---
title: Az iOS-eszközök e-mail-beállításainak konfigurálása a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az összes olyan e-mail-beállítást, amelyet konfigurálhat és hozzáadhat az iOS-eszközökhöz a Microsoft Intuneban, beleértve az Exchange-kiszolgálók használatát és az attribútumok Azure Active Directoryból való beszerzését. Emellett engedélyezheti az SSL használatát, hitelesítheti a tanúsítványokkal vagy felhasználónévvel/jelszóval rendelkező felhasználókat, és az iOS-eszközökön szinkronizálhatja az e-maileket a Microsoft Intune eszköz konfigurációs profiljaival.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cbf9c29a1e694726b1b42f7072eea859f812751
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593798"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Az iOS-eszközök e-mail beállításainak hozzáadása a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune az e-mail-kiszolgálóhoz való kapcsolódáshoz hozzon létre és konfiguráljon e-mailt, válassza ki a felhasználók hitelesítésének módját, az S/MIME titkosítást és egyebeket.

Ez a cikk felsorolja és leírja az iOS rendszerű eszközökön elérhető összes e-mail-beállítást. Létrehozhat egy eszköz-konfigurációs profilt, amellyel leküldheti vagy telepítheti ezeket az e-mail-beállításokat iOS-eszközeire.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](../email-settings-configure.md).

> [!NOTE]
> Ezek a beállítások minden regisztrációs típushoz elérhetők. A regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](../ios-enroll.md).

## <a name="email-settings"></a>E-mail beállítások

- **E-mail-kiszolgáló**: Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (AAD) lekért attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: A nevet, például `user1` vagy `user1@contoso.com` kéri le.
  - **Elsődleges SMTP-cím**: E-mail-cím formátumban kéri le a nevet, például `user1@contoso.com`
  - **SAM-fiók neve**: Tartomány szükséges hozzá, például `domain\user1`.

    Ezt is adja meg:  
    - **Felhasználói tartománynév forrása**: Válassza az **AAD** (Azure Active Directory) vagy az **Egyéni** lehetőséget.

      Ha azt választja, hogy az attribútumokat az **AAD-ből** kéri le, adja meg ezt is:
      - **Felhasználói tartománynév attribútuma az AAD-ból**: Választhatja a felhasználóhoz tartozó **Teljes tartománynév** vagy a **NetBIOS-név** attribútum lehetőséget

      Ha az **Egyéni** attribútumot választja, adja meg a következőt:
      - **Használandó egyéni tartománynév**: Adja meg az Intune által a tartománynévhez használt értéket, például `contoso.com` vagy `contoso`

- **E-mail-cím attribútuma az AAD-ből**: Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím. Az **Egyszerű felhasználónév** (`user1@contoso.com` vagy `user1`) lehetőség kiválasztásával az egyszerű felhasználónevet e-mail-címként használhatja. Az Exchange-kiszolgálóra való bejelentkezéshez válassza az **Elsődleges SMTP-cím** (`user1@contoso.com`) lehetőséget.
- **Hitelesítési módszer**: válassza ki a **felhasználónevet és a jelszót**, a **tanúsítványokat**vagy a **származtatott hitelesítő adatokat** az e-mail-profil által használt hitelesítési módszerként. Az Azure-alapú többtényezős hitelesítés nincs támogatva.
  - Ha a **Tanúsítvány** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát, amelyet az Exchange-kapcsolat hitelesítésére kíván használni.
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

- **S/MIME**: az **s/MIME engedélyezése** lehetővé teszi, hogy a felhasználók aláírják és/vagy titkosítsák az e-maileket az iOS natív posta alkalmazásban. 

  Ha e-mail-üzenettel használja az S/MIME-t, erősítse meg a küldő hitelességét, valamint az üzenet sértetlenségét és titkosságát.

  - **S/MIME-aláírás engedélyezve**: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók digitálisan aláírják a kimenő e-maileket a megadott fiókhoz. Az aláírás segítségével az üzenetek fogadására jogosult felhasználók biztosak lehetnek abban, hogy az üzenet az adott feladótól származik, és nem a feladótól érkező személynek. A **Letiltás** nem teszi lehetővé a felhasználók számára az üzenet digitális aláírását.
    - **Beállítás módosításának engedélyezése a felhasználó**számára: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók megváltoztassák az S/MIME-aláírás viselkedését. A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók módosítsák a konfigurált S/MIME-aláírási beállítást. Az iOS 12 és újabb verziókban érhető el.

  - **S/MIME-aláírási tanúsítvány**: válasszon ki egy meglévő PKCS-vagy SCEP-tanúsítványt, amelyet az e-mail üzenetek aláírásához használ.
    - **Beállítások módosításának engedélyezése a felhasználó**számára: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók megváltoztassák az aláíró tanúsítványt. A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók megváltoztassák az aláíró tanúsítványt, és kényszerítse a felhasználókat a konfigurált tanúsítvány használatára. Az iOS 12 és újabb verziókban érhető el.

  - **Titkosítás alapértelmezés**szerint: az **Engedélyezés** az összes üzenetet titkosítja alapértelmezett viselkedésként. A **Letiltás** beállítás megadása esetén az összes üzenet nem titkosítható alapértelmezett viselkedésként.
    - **Beállítás módosításának engedélyezése a felhasználó**számára: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók megváltoztassák az alapértelmezett titkosítási viselkedést. A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók megváltoztassák a titkosítás alapértelmezett viselkedését, és kényszerítse a felhasználókat, hogy használják a konfigurált Az iOS 12 és újabb verziókban érhető el.

  - Az üzenetek titkosításának **kényszerítése**: az üzenetek titkosítása lehetővé teszi a felhasználók számára, hogy a küldés előtt kiválasszák a titkosított e-maileket. Ha új e-mailt hoz létre, válassza az **Engedélyezés** lehetőséget az üzeneten belüli titkosítási beállítás megjelenítéséhez. A felhasználók ezután dönthetnek úgy, hogy az üzenetek titkosítását letiltják vagy letiltják. A **Letiltás** beállítás megadásával megakadályozható, hogy az üzenet titkosítása lehetőség látható legyen.

    Ha a **titkosítás alapértelmezés** szerint beállítás engedélyezve van, az üzenetek titkosításának engedélyezése lehetővé teszi a felhasználók számára, hogy üzenetként letiltsák a titkosítást. Ha a **titkosítás alapértelmezés** szerint beállítás le van tiltva, az üzenetsor-titkosítás engedélyezése lehetővé teszi a felhasználók számára, hogy üzenetként engedélyezzék a titkosítást.

  - **S/MIME titkosítási tanúsítvány**: válassza ki az e-mail-üzenetek titkosításához használt meglévő PKCS-vagy SCEP-tanúsítványsablont.
    - **Beállítás módosításának engedélyezése a felhasználó**számára: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók megváltoztassák a titkosítási tanúsítványt. A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók módosítsák a titkosítási tanúsítványt, és a felhasználók a konfigurált tanúsítvány használatára kényszerítik a felhasználókat. Az iOS 12 és újabb verziókban érhető el.
- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket. Vagy válassza a **Korlátlan** lehetőséget az összes elérhető e-mail szinkronizálása.
- **Üzenetek más e-mail-fiókba való áthelyezésének engedélyezése**: **Engedélyezés** után lehetővé teszi a felhasználóknak az e-mailek áthelyezését az eszközön konfigurált más fiókokba.
- **E-mailek küldésének engedélyezése külső gyártótól származó alkalmazásokból**: **Engedélyezés** után a felhasználók kiválaszthatják alapértelmezett e-mail-küldési fiókként ezt a profilt. Engedélyezi a külső alkalmazásoknak az e-mailek natív levelezőalkalmazásban történő megnyitását, például fájlok e-mailhez való csatolásakor.
- **Legutóbb használt e-mail-címek szinkronizálása**: **Engedélyezés** után a felhasználók szinkronizálni tudják az eszközön legutóbb használt e-mail-címek listáját a kiszolgálóval.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](../device-profile-monitor.md).

Az e-mail-beállítások konfigurálása az [Android](../email-settings-android.md), az [Android Enterprise](../email-settings-android-enterprise.md), a [Windows 10](email-settings-windows-10.md)és a [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md) rendszerű eszközökön.
