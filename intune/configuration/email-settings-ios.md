---
title: Az iOS-eszközök e-mail-beállításainak konfigurálása a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az összes olyan e-mail-beállítást, amelyet konfigurálhat és hozzáadhat az iOS-eszközökhöz a Microsoft Intuneban, beleértve az Exchange-kiszolgálók használatát és az attribútumok Azure Active Directoryból való beszerzését. Emellett engedélyezheti az SSL használatát, hitelesítheti a tanúsítványokkal vagy felhasználónévvel/jelszóval rendelkező felhasználókat, és az iOS-eszközökön szinkronizálhatja az e-maileket a Microsoft Intune eszköz konfigurációs profiljaival.
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
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Az iOS-eszközök e-mail beállításainak hozzáadása a Microsoft Intune

Microsoft Intune az e-mail-kiszolgálóhoz való kapcsolódáshoz hozzon létre és konfiguráljon e-mailt, válassza ki a felhasználók hitelesítésének módját, az S/MIME titkosítást és egyebeket.

Ez a cikk felsorolja és leírja az iOS rendszerű eszközökön elérhető összes e-mail-beállítást. Létrehozhat egy eszköz-konfigurációs profilt, amellyel leküldheti vagy telepítheti ezeket az e-mail-beállításokat iOS-eszközeire.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](../email-settings-configure.md).

> [!NOTE]
> Ezek a beállítások minden regisztrációs típushoz elérhetők. A regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Exchange ActiveSync-fiók beállításai

- **E-mail-kiszolgáló**: Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (AAD) lekért attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: A nevet, például `user1` vagy `user1@contoso.com` kéri le.
  - **Elsődleges SMTP-cím**: E-mail-cím formátumban kéri le a nevet, például `user1@contoso.com`
  - **SAM-fiók neve**: Tartomány szükséges hozzá, például `domain\user1`. Ezt is adja meg:  
    - **Felhasználói tartománynév forrása**: Válassza az **AAD** (Azure Active Directory) vagy az **Egyéni** lehetőséget.
      - **HRE**: az attribútumok lekérése az Azure ad-ből. Ezt is adja meg:
        - **Felhasználói tartománynév attribútuma a HRE-ből**: válassza a felhasználó **teljes tartománynevét** (`contoso.com`) vagy a **NetBIOS-név** (`contoso`) attribútumának beolvasását.

      - **Egyéni**: az attribútumok beolvasása egy egyéni tartománynévből. Ezt is adja meg:
        - **Használandó egyéni tartománynév**: adjon meg egy értéket, amelyet az Intune a tartománynévhez használ, például `contoso.com` vagy `contoso`.

- **E-mail-cím attribútuma az AAD-ből**: Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím. A választható lehetőségek:
  - **Egyszerű felhasználónév**: használja a teljes egyszerű nevet e-mail-címként, például `user1@contoso.com` vagy `user1`.
  - **Elsődleges SMTP-címe**: használja az elsődleges SMTP-címeket, hogy bejelentkezzen az Exchange-be, például `user1@contoso.com`.
- **Hitelesítési módszer**: válassza ki, hogyan szeretné hitelesíteni a felhasználókat az e-mail-kiszolgálón. A választható lehetőségek:
  - **Tanúsítvány**: válasszon ki egy, az Exchange-kapcsolatok hitelesítéséhez korábban létrehozott SCEP-vagy PKCS-tanúsítvány-profilt. Ez a beállítás biztosítja a legbiztonságosabb és zökkenőmentes felhasználói élményt.
  - **Felhasználónév és jelszó**: a rendszer a felhasználókat kéri a Felhasználónév és a jelszó megadására.
  - **Származtatott hitelesítő adatok**: a felhasználó intelligens kártyáján származtatott tanúsítvány használata. További információ: [származtatott hitelesítő adatok használata Microsoft Intuneban](../protect/derived-credentials.md).

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

## <a name="exchange-activesync-profile-configuration"></a>Exchange ActiveSync-profil konfigurálása

> [!IMPORTANT]
> Ezen beállítások konfigurálásakor a rendszer egy új profilt helyez üzembe az eszközön, még akkor is, ha a meglévő e-mail-profil frissül, hogy tartalmazza ezeket a beállításokat. A rendszer felszólítja a felhasználókat az Exchange ActiveSync-fiók jelszavának megadására. Ezek a beállítások a jelszó megadásakor lépnek érvénybe.

- **Szinkronizálni kívánt Exchange-információk**: az Exchange ActiveSync használata esetén válassza ki az eszközön szinkronizált Exchange-szolgáltatásokat: naptár, névjegyek, emlékeztetők, megjegyzések és e-mailek. A választható lehetőségek:
  - **Minden adatérték** (alapértelmezett): a szinkronizálás minden szolgáltatás esetében engedélyezve van.
  - **Csak e-mail-cím**: a szinkronizálás csak az e-mailek esetében engedélyezett. A többi szolgáltatás szinkronizálása le van tiltva.
  - **Csak naptár**: a szinkronizálás csak a naptár esetében engedélyezett. A többi szolgáltatás szinkronizálása le van tiltva.
  - **Csak naptár és névjegyek**: a szinkronizálás csak naptár és névjegyek esetében engedélyezett. A többi szolgáltatás szinkronizálása le van tiltva.
  - **Csak névjegyek**: a szinkronizálás csak a névjegyek esetében engedélyezett. A többi szolgáltatás szinkronizálása le van tiltva.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók

- A **szinkronizálási beállítások módosításának engedélyezése a felhasználók**számára: válassza ki, hogy a felhasználók módosíthatják-e az Exchange-szolgáltatások Exchange ActiveSync-beállításait az eszközön: naptár, névjegyek, emlékeztetők, megjegyzések és e-mailek. A választható lehetőségek:

  - **Igen** (alapértelmezett): a felhasználók módosíthatják az összes szolgáltatás szinkronizálási viselkedését. Ha az **Igen** lehetőséget választja, az *összes* szolgáltatás módosítható.
  - **Nem**: a felhasználók nem változtathatják meg az összes szolgáltatás szinkronizálási beállításait. A **nem** blokkolja az *összes* szolgáltatás módosításait.

  > [!TIP]
  > Ha úgy konfigurálta az **Exchange-adatszinkronizálási** beállítást, hogy csak bizonyos szolgáltatásokat szinkronizáljon, javasoljuk, hogy válassza a **nem** lehetőséget ehhez a beállításhoz. A **nem** beállítás megadásával megakadályozható, hogy a felhasználók módosítsák a szinkronizált Exchange-szolgáltatást.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók

## <a name="exchange-activesync-email-settings"></a>Exchange ActiveSync e-mail beállítások

- Az **s/MIME**: s/MIME olyan e-mail-tanúsítványokat használ, amelyek további biztonságot nyújtanak az e-mail-kommunikációhoz aláírással, titkosítással és visszafejtéssel. Ha e-mail-üzenettel használja az S/MIME-t, erősítse meg a küldő hitelességét, valamint az üzenet sértetlenségét és titkosságát.

  A választható lehetőségek:

  - **S/MIME letiltása** (alapértelmezett): nem használ s/MIME e-mail tanúsítványokat az e-mailek aláírásához, titkosításához és visszafejtéséhez.
  - **S/MIME engedélyezése**: lehetővé teszi a felhasználóknak az e-mailek aláírását és/vagy titkosítását az iOS Native mail alkalmazásban. Ezt is adja meg:

    - **S/MIME-aláírás engedélyezve**: a **Letiltás** (alapértelmezett) nem teszi lehetővé a felhasználók számára az üzenet digitális aláírását. Az **Engedélyezés** beállítás megadása esetén a felhasználók digitálisan aláírják a kimenő e-maileket a megadott fiókhoz. Az aláírás segítségével az üzenetek fogadására jogosult felhasználók biztosak lehetnek abban, hogy az üzenet az adott feladótól származik, és nem a feladótól érkező személynek.
      - A **felhasználó módosíthatja a beállítást**: az **Engedélyezés** beállítás megadásával engedélyezhető a felhasználók számára az aláírási beállítások módosítása. **Letiltás** (alapértelmezett) megakadályozza, hogy a felhasználók megváltoztassák az aláírást, és kényszerítse a felhasználókat, hogy a konfigurált aláírást használják.
      - **Aláíró tanúsítvány típusa**: az Ön beállításai:
        - **Nincs konfigurálva**: az Intune nem frissíti vagy nem módosítja ezt a beállítást.
        - **Nincs**: rendszergazdaként nem kényszeríti ki egy adott tanúsítvány megadását. Válassza ezt a lehetőséget, hogy a felhasználók kiválaszthatják a saját tanúsítványát.
        - **Származtatott hitelesítő adatok**: a felhasználó intelligens kártyáján származtatott tanúsítvány használata. További információ: [származtatott hitelesítő adatok használata Microsoft Intuneban](../protect/derived-credentials.md).
        - **Tanúsítványok**: válasszon ki egy meglévő PKCS-vagy SCEP-tanúsítványt, amelyet az e-mail üzenetek aláírásához használ.
      - A felhasználó módosíthatja a beállítást: az **Engedélyezés** **beállítás megadásával**engedélyezhető a felhasználók számára az aláíró tanúsítvány módosítása. **Letiltás** (alapértelmezett) megakadályozza, hogy a felhasználók megváltoztassák az aláíró tanúsítványt, és kényszerítse a felhasználókat a konfigurált tanúsítvány használatára.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 és újabb verziók
        - iPadOS 12 és újabb

    - **Titkosítás alapértelmezés**szerint: az **Engedélyezés** az összes üzenetet titkosítja alapértelmezett viselkedésként. **Letiltás** (alapértelmezés) – az összes üzenet titkosítása alapértelmezett viselkedésként nem történik meg.
      - A felhasználó módosíthatja a beállítást: az **Engedélyezés** **beállítás megadásával**engedélyezhető a felhasználók számára az alapértelmezett titkosítási viselkedés módosítása. A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók megváltoztassák a titkosítás alapértelmezett viselkedését, és kényszerítse a felhasználókat a konfigurált titkosítás használatára.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 és újabb verziók
        - iPadOS 12 és újabb

    - Az üzenetek titkosításának **kényszerítése**: az üzenetek titkosítása lehetővé teszi a felhasználók számára, hogy a küldés előtt kiválasszák a titkosított e-maileket.

      Az **Engedélyezés** beállítás megjeleníti az üzeneten belüli titkosítási lehetőséget, amikor új e-mailt hoz létre. A felhasználók ezután dönthetnek úgy, hogy kiválaszthatják az üzenetek titkosítását, vagy letiltják azt. Ha a **titkosítás alapértelmezés szerint** beállítás is engedélyezve van, az üzenetek titkosításának engedélyezése lehetővé teszi a felhasználók számára, hogy üzenetként letiltsák a titkosítást.

      **Letiltás** (alapértelmezett) megakadályozza, hogy az üzeneten belüli titkosítási beállítás látható legyen. Ha a **titkosítás alapértelmezés** szerint beállítás le van tiltva, az üzenetek titkosításának engedélyezése lehetővé teszi a felhasználók számára, hogy üzenetként engedélyezzék a titkosítást.

      - **Titkosítási tanúsítvány típusa**: az Ön beállításai:
        - **Nincs konfigurálva**: az Intune nem frissíti vagy nem módosítja ezt a beállítást.
        - **Nincs**: rendszergazdaként nem kényszeríti ki egy adott tanúsítvány megadását. Válassza ezt a lehetőséget, hogy a felhasználók kiválaszthatják a saját tanúsítványát.
        - **Származtatott hitelesítő adatok**: a felhasználó intelligens kártyáján származtatott tanúsítvány használata. További információ: [származtatott hitelesítő adatok használata Microsoft Intuneban](../protect/derived-credentials.md).
        - **Tanúsítványok**: válasszon ki egy meglévő PKCS-vagy SCEP-tanúsítványt, amelyet az e-mail üzenetek aláírásához használ.
      - A **felhasználó módosíthatja a beállítást**: **lehetővé teszi a** felhasználók számára a titkosítási tanúsítvány módosítását. **Letiltás** (alapértelmezett) megakadályozza, hogy a felhasználók megváltoztassák a titkosítási tanúsítványt, és kényszerítse a felhasználókat a konfigurált tanúsítvány használatára.

        Ez a funkció az alábbiakra vonatkozik:  
        - iOS 12 és újabb verziók
        - iPadOS 12 és újabb

- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket. Vagy válassza a **Korlátlan** lehetőséget az összes elérhető e-mail szinkronizálása.
- **Üzenetek más e-mail-fiókba**való áthelyezésének engedélyezése: az **Engedélyezés** (alapértelmezés) lehetővé teszi a felhasználóknak, hogy az eszközökön konfigurált felhasználóktól eltérő fiókokba helyezzenek el e-mail-üzeneteket.
- E **-mailek küldésének engedélyezése harmadik féltől származó alkalmazásokból**: az **Engedélyezés** (alapértelmezett) lehetővé teszi, hogy a felhasználók a profilt alapértelmezett fiókként válasszanak e-mailek küldéséhez. Engedélyezi a külső alkalmazásoknak az e-mailek natív levelezőalkalmazásban történő megnyitását, például fájlok e-mailhez való csatolásakor.
- **Legutóbb használt e-mail-címek szinkronizálása**: az **Engedélyezés** (alapértelmezett) lehetővé teszi a felhasználók számára, hogy szinkronizálják az eszközön a kiszolgálón nemrég használt e-mail-címek listáját.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](../device-profile-monitor.md).

Az e-mail-beállítások konfigurálása az [Android](../email-settings-android.md), az [Android Enterprise](../email-settings-android-enterprise.md), a [Windows 10](email-settings-windows-10.md)és a [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md) rendszerű eszközökön.
