---
title: Configure Email settings for iOS devices in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the email settings you can configure and add to iOS devices in Microsoft Intune, including using Exchange servers, and getting attributes from Azure Active Directory. You can also enable SSL, authenticate users with certificates or username/password, and synchronize email on iOS devices using device configuration profiles in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390820"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Add e-mail settings for iOS devices in Microsoft Intune

In Microsoft Intune, you can create and configure email to connect to an email server, choose how users authenticate, use S/MIME for encryption, and more.

This article lists and describes all the email settings available for devices running iOS. You can create a device configuration profile to push or deploy these email settings to your iOS devices.

## <a name="before-you-begin"></a>Előkészületek

[Create a device configuration profile](../email-settings-configure.md).

> [!NOTE]
> These settings are available for all enrollment types. For more information on the enrollment types, see [iOS enrollment](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Exchange ActiveSync account settings

- **E-mail-kiszolgáló**: Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (AAD) lekért attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: A nevet, például `user1` vagy `user1@contoso.com` kéri le.
  - **Elsődleges SMTP-cím**: E-mail-cím formátumban kéri le a nevet, például `user1@contoso.com`
  - **SAM-fiók neve**: Tartomány szükséges hozzá, például `domain\user1`. Ezt is adja meg:  
    - **Felhasználói tartománynév forrása**: Válassza az **AAD** (Azure Active Directory) vagy az **Egyéni** lehetőséget.
      - **AAD**: Get the attributes from Azure AD. Ezt is adja meg:
        - **User domain name attribute from AAD**: Choose to get the **Full domain name** (`contoso.com`) or the **NetBIOS name** (`contoso`) attribute of the user.

      - **Custom**: Get the attributes from a custom domain name. Ezt is adja meg:
        - **Custom domain name to use**: Enter a value that Intune uses for the domain name, such as `contoso.com` or `contoso`.

- **E-mail-cím attribútuma az AAD-ből**: Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím. A választható lehetőségek:
  - **User principal name**: Use the full principal name as the email address, such as `user1@contoso.com` or `user1`.
  - **Primary SMTP address**: Use the primary SMTP address to sign in to Exchange, such as `user1@contoso.com`.
- **Authentication method**: Choose how users to authenticate to the email server. A választható lehetőségek:
  - **Certificate**: Select a client SCEP or PKCS certificate profile you previously created to authenticate the Exchange connection. This option provides the most secure and seamless experience for your users.
  - **Username and Password**: Users are prompted to enter their user name and password.
  - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > Az Azure-alapú többtényezős hitelesítés nincs támogatva.
  
- **SSL**: **Engedélyezheti** az SSL-kommunikáció használatát e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikáció során.
- **OAuth**: **Engedélyezheti** az Open Authorization (OAuth) használatát e-mailek küldésekor és fogadásakor, valamint az Exchange-dzsel való kommunikáció során. Ha az OAuth-kiszolgáló tanúsítványalapú hitelesítést használ, válassza a **Tanúsítvány** lehetőséget **hitelesítési módszernek**, és foglalja bele a tanúsítványt a profilba. Ellenkező esetben válassza a **Felhasználónév és jelszó** lehetőséget a **hitelesítési módszerhez**. OAuth használata esetén ügyeljen a következőkre:

  - A profil a felhasználóknak való elérhetővé tétele előtt ellenőrizze, hogy a levelezőszolgáltatása támogatja-e az OAuthot. Az Office 365 Exchange Online támogatja az OAuthot. A helyszíni Exchange és egyéb partneri vagy külső megoldások nem feltétlenül támogatják az OAuthot. A helyszíni Exchange konfigurálható modern hitelesítéshez (ehhez tekintse meg a [Hibrid modern hitelesítés bejelentése a helyszíni Exchange-hez](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) című blogbejegyzést).

    Ha az e-mail-profil OAuth-hitelesítést használ, amelyet a levelezőszolgáltató azonban nem támogat, a **Jelszó újbóli megadása** lehetőség nm lesz elérhető. Így például semmi nem történik, ha a felhasználó a **Jelszó újbóli megadása** lehetőséget választja az Apple eszközbeállításaiban.

  - Az OAuth engedélyezése esetén a végfelhasználók különböző „modern hitelesítési” bejelentkezési felületeket láthatnak, amelyek támogatják a többtényezős hitelesítést (MFA). 

  - Egyes szervezetek letilthatják a végfelhasználóknak az[önkiszolgáló alkalmazás-hozzáférést](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Ebben a forgatókönyvben a modern hitelesítéses bejelentkezés sikertelen lehet mindaddig, amíg a rendszergazda létre nem hozza az „iOS Accounts” vállalati alkalmazást, és hozzáférést nem ad a felhasználóknak hozzá az Azure AD-ben.

    Az alapértelmezett művelet az alkalmazás hozzáadása az [alkalmazás-hozzáférési panel](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **Alkalmazás hozzáadása** funkciójával, **üzleti jóváhagyás nélkül**. További információ: [felhasználók hozzárendelése alkalmazásokhoz](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Az OAuth engedélyezésekor a következők történnek:  
  > 1. A már célzott eszközök új profilt kapnak.
  > 2. A rendszer újra kéri a végfelhasználók hitelesítő adatainak megadását.

## <a name="exchange-activesync-profile-configuration"></a>Exchange ActiveSync profile configuration

> [!IMPORTANT]
> Configuring these settings deploys a new profile to the device, even when an existing email profile is updated to include these settings. Users are prompted to enter their Exchange ActiveSync account password. These settings take affect when the password is entered.

- **Exchange data to sync**: When using Exchange ActiveSync, choose the Exchange services that are synced on the device: Calendar, Contacts, Reminders, Notes, and Email. A választható lehetőségek:
  - **All data** (default): Sync is enabled for all services.
  - **Email only**: Sync is enabled for Email only. Sync is disabled for the other services.
  - **Calendar only**: Sync is enabled for Calendar only. Sync is disabled for the other services.
  - **Calendar and Contacts only**: Sync is enabled for Calendar and Contacts only. Sync is disabled for the other services.
  - **Contacts only**: Sync is enabled for Contacts only. Sync is disabled for the other services.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

- **Allow users to change sync settings**: Choose if users can change the Exchange ActiveSync settings for the Exchange services on the device: Calendar, Contacts, Reminders, Notes, and Email. A választható lehetőségek:

  - **Yes** (default): Users can change the sync behavior of all services. Choosing **Yes** allows changes to *all* services.
  - **No**: Users can't change the sync settings of all the services. Choosing **No** blocks changes to *all* services.

  > [!TIP]
  > If you configured the **Exchange data to sync** setting to sync only some services, we recommend selecting **No** for this setting. Choosing **No** prevents users from changing the Exchange service that's synced.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

## <a name="exchange-activesync-email-settings"></a>Exchange ActiveSync email settings

- **S/MIME**: S/MIME uses email certificates that provide extra security to your email communications by signing, encrypting, and decrypting. When you use S/MIME with an email message, you confirm the authenticity of the sender, and the integrity and confidentiality of the message.

  A választható lehetőségek:

  - **Disable S/MIME** (default): Doesn't use an S/MIME email certificate to sign, encrypt, or decrypt emails.
  - **Enable S/MIME**: Allows users to sign and/or encrypt email in the iOS native mail application. Ezt is adja meg:

    - **S/MIME signing enabled**: **Disable** (default) doesn't allow users to digitally sign the message. **Enable** allows users to digitally sign outgoing email for the account you entered. Signing helps users who receive messages be certain that the message came from the specific sender, and not from someone pretending to be the sender.
      - **Allow user to change setting**: **Enable** allows users to change the signing options. **Disable** (default) prevents users from changing the signing, and forces users to use the signing you configured.
      - **Signing certificate type**: Your options:
        - **Not configured**: Intune doesn't update or change this setting.
        - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
        - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificates**: Select an existing PKCS or SCEP certificate profile that's used for signing email messages.
      - **Allow user to change setting**: **Enable** allows users to change the signing certificate. **Disable** (default) prevents users from changing the signing certificate, and forces users to use the certificate you configured.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 and newer
        - iPadOS 12 and newer

    - **Encrypt by default**: **Enable** encrypts all messages as the default behavior. **Disable** (default) doesn't encrypt all messages as the default behavior.
      - **Allow user to change setting**: **Enable** allows users to change the default encryption behavior. **Disable** prevents users from changing the encryption default behavior, and forces users to use the encryption you configured.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 and newer
        - iPadOS 12 and newer

    - **Force per-message encryption**: Per-message encryption allows users to choose which emails are encrypted before being sent.

      **Enable** shows the per-message encryption option when creating a new email. Users can then choose to opt-in or opt-out of per-message encryption. If the **Encrypt by default** setting is also enabled, enabling per-message encryption allows users to opt out of encryption per message.

      **Disable** (default) prevents the per-message encryption option from showing. If the **Encrypt by default** setting is also disabled, enabling per-message encryption allows users to opt in to encryption per message.

      - **Encryption certificate type**: Your options:
        - **Not configured**: Intune doesn't update or change this setting.
        - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
        - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificates**: Select an existing PKCS or SCEP certificate profile that's used for signing email messages.
      - **Allow user to change setting**: **Enable** allow users to change the encryption certificate. **Disable** (default) prevents users from changing the encryption certificate, and forces users to use the certificate you configured.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 and newer
        - iPadOS 12 and newer

- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket. Vagy válassza a **Korlátlan** lehetőséget az összes elérhető e-mail szinkronizálása.
- **Allow messages to be moved to other email accounts**: **Enable** (default) allows users to move email messages between different accounts the users configured on their devices.
- **Allow email to be sent from third-party applications**: **Enable** (default) allows users to select this profile as the default account for sending email. Engedélyezi a külső alkalmazásoknak az e-mailek natív levelezőalkalmazásban történő megnyitását, például fájlok e-mailhez való csatolásakor.
- **Synchronize recently used email addresses**: **Enable** (default) allows users to synchronize the list of email addresses that have been recently used on the device with the server.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Next, [assign the profile](../device-profile-assign.md) and [monitor its status](../device-profile-monitor.md).

Configure email settings on [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md), and [Windows Phone 8.1](email-settings-windows-phone-8-1.md) devices.
