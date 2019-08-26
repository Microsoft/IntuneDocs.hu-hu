---
title: Eszközkorlátozási beállítások Windows 10 rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Tekintse meg az összes beállítás listáját, valamint a Windows 10 és újabb rendszerű eszközökön az eszközök korlátozásának létrehozásához szükséges leírást. Ezekkel a beállításokkal konfigurálhatja a képernyőképeket, a jelszavakra vonatkozó követelményeket, a kioszk beállításait, az áruházbeli alkalmazásokat, a Microsoft Edge böngészőt, a Windows Defendert, a felhőhöz való hozzáférést, a Start menüt és egyebeket Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b3fd474e938e2e85a0a08951a9e3f154d980411
ms.sourcegitcommit: b64869b4be357c0741ec01b1a2f0bae13efce937
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69998948"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows 10 (és újabb) eszközbeállítások az Intune-t használó szolgáltatások engedélyezéséhez vagy korlátozásához

Ez a cikk felsorolja és leírja a Windows 10 és újabb rendszerű eszközökön szabályozható különböző beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, testreszabhatja a zárolási képernyőt, és használhatja a Windows Defendert.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a Windows 10-es eszközökhöz vannak rendelve vagy telepítve.

> [!Note]
> Nem minden beállítás érhető el a Windows összes kiadásában. A támogatott kiadások megtekintéséhez tekintse meg a [házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) -kriptográfiai (másik Microsoft-webhely megnyitása) című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Alkalmazásáruház

Ezek a beállítások a [ApplicationManagement házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **App Store** (csak mobil): **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára az alkalmazás-áruház elérését a mobileszközökön. **Letiltja** az alkalmazás-áruház használatát.
- **Az áruházból származó alkalmazások automatikus frissítése**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a Microsoft Store telepített alkalmazások automatikusan frissüljenek. A **Letiltás** megakadályozza a frissítések automatikus telepítését.
- **Megbízható alkalmazás telepítése**: Válassza ki, hogy a nem Microsoft Store alkalmazásokat lehet-e telepíteni, más néven közvetlen telepítési. A közvetlen telepítési telepíti, majd futtatja vagy teszteli az Microsoft Store által nem tanúsított alkalmazást. Például egy olyan alkalmazás, amely csak a vállalaton belül található. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett értékének használata.
  - **Letiltás**: Megakadályozza a közvetlen telepítési. Nem Microsoft Store alkalmazások nem telepíthetők.
  - **Engedélyezés**: Engedélyezi a közvetlen telepítési. Nem Microsoft Store alkalmazások is telepíthetők.
- **Fejlesztői zárolás feloldása**: Engedélyezze a Windows fejlesztői beállításait, például lehetővé teszi a közvetlenül telepített alkalmazások módosítását a végfelhasználók számára. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett értékének használata.
  - **Letiltás**: A fejlesztői üzemmód és a közvetlen telepítési alkalmazások megakadályozása.
  - **Engedélyezés**: Lehetővé teszi a fejlesztői üzemmód és a közvetlen telepítési alkalmazások használatát.

  Az [eszköz fejlesztésének engedélyezése](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) további információt tartalmaz a szolgáltatással kapcsolatban.

- **Megosztott felhasználói alkalmazásadatok**: Az **Engedélyezés** elemre kattintva megoszthatja az alkalmazásadatok különböző felhasználók között ugyanazon az eszközön és az alkalmazás más példányaival. **Nincs konfigurálva** (alapértelmezés) megakadályozza az adatmegosztást más felhasználókkal és ugyanazon alkalmazás más példányaival.
- **Csak privát áruház használata**: Az alkalmazások csak privát áruházból tölthetők le, és nem tölthetők le a nyilvános áruházból, beleértve a kiskereskedelmi katalógust is. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások letöltését egy privát áruházból és egy nyilvános áruházból.
- **Áruházból származó alkalmazások indítása**: A **Letiltás** letiltja az eszközön előre telepített vagy a Microsoft Store letöltött összes alkalmazást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások megnyitását.
- **Alkalmazásadatok telepítése a**rendszerköteten: A **blokk** leállítja az alkalmazások számára az eszköz rendszerkötetén tárolt adatok tárolását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások számára a rendszerlemez kötetén tárolt adattárolást.
- **Alkalmazások telepítése a**rendszermeghajtón: A **Letiltás** megakadályozza, hogy az alkalmazások a rendszermeghajtón telepítsenek az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások telepítését a rendszermeghajtón.
- **Játék DVR** (csak asztali verzió): A **Letiltás** letiltja a Windows-játékok rögzítését és a szórást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a játékok rögzítését és közvetítését.
- **Csak áruházból származó alkalmazások**: Ez a beállítás határozza meg a felhasználói élményt, ha a felhasználók a Microsoft Storetól eltérő helyekről telepítik az alkalmazásokat. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Lehetővé teszi, hogy a végfelhasználók a Microsoft Storetól eltérő helyekről telepítsenek alkalmazásokat, beleértve az egyéb házirend-beállításokban definiált alkalmazásokat is.  
  - **Bárhol**: Kikapcsolja az alkalmazások javaslatait, és lehetővé teszi, hogy a felhasználók tetszőleges helyről telepítsenek alkalmazásokat.  
  - **Csak tárolás**: Kényszeríti a végfelhasználókat, hogy csak az Microsoft Store telepítsenek alkalmazásokat.
  - **Javaslatok**: Ha a Microsoft Store elérhető webhelyről telepít egy alkalmazást, a felhasználók egy üzenetet látnak, amely azt javasolja, hogy töltse le az áruházból.  
  - **Előnyben részesített tároló**: Figyelmezteti a felhasználókat, ha a Microsoft Storetól eltérő helyekről telepítik az alkalmazásokat.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- A **telepítés felhasználói ellenőrzése**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), Windows Installer megakadályozhatja, hogy a felhasználók a rendszergazdák számára fenntartott telepítési beállításokat módosítsák, például a fájlok telepítéséhez a címtárat. A **Letiltás** lehetővé teszi a felhasználók számára, hogy megváltoztassák ezeket a telepítési beállításokat, és néhány Windows Installer biztonsági funkciót kihagynak.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Alkalmazások telepítése emelt szintű jogosultságokkal**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), akkor a rendszer az aktuális felhasználó engedélyeit alkalmazza, amikor olyan programokat telepít, amelyeket a rendszergazda nem telepít vagy kínál. Ha a rendszerre telepít bármely programot, a **letiltja** a Windows Installert a emelt szintű engedélyek használatára. Ezek a jogosultságok minden programra kiterjeszthetők.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Indítási alkalmazások**: Adja meg azoknak az alkalmazásoknak a listáját, amelyeket a felhasználó az eszközre való bejelentkezés után megnyithat. Ügyeljen arra, hogy a Windows-alkalmazások PFN-neveinek pontosvesszővel tagolt listáját használja. Ahhoz, hogy ez a szabályzat működjön, a Windows-alkalmazásokban a jegyzékfájlnak indítási feladatot kell használnia.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

Ezek a beállítások a [kapcsolódási házirendet](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) és a [Wi-Fi házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) -kriptográfiai szolgáltatókat használják, amelyek a támogatott Windows-kiadásokat is felsorolják.

- [Wi-Fi házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Mobil adatcsatorna**: Válassza ki, hogy a végfelhasználók használhatnak-e olyan adatforrásokat, mint például a webes böngészés, ha egy mobil hálózathoz csatlakoznak. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az alapértelmezett operációs rendszert használja, amely lehetővé teszi a mobil adatcsatorna használatát. A végfelhasználók kikapcsolhatják a felhasználókat.
  - **Letiltás**: Ne engedélyezze a mobil adatcsatornát. A végfelhasználók nem kapcsolhatják be.
  - **Engedélyezés (nem szerkeszthető)** : Engedélyezi a mobil adatcsatorna használatát. A végfelhasználók nem kapcsolhatják ki.

- **Adatroaming**: A **blokk** megakadályozza a mobil adatroaming használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hálózatok közötti barangolást az adatok elérésekor.
- **VPN a mobil hálózaton keresztül**: A **Letiltás** megakadályozza, hogy az eszköz hozzáférjen a VPN-kapcsolatokhoz, amikor a hálózathoz csatlakozik. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a VPN számára bármilyen kapcsolat használatát, beleértve a mobilt is.
- **VPN-barangolás a mobil hálózaton**: A **Letiltás** megakadályozza, hogy az eszköz hozzáférjen a VPN-kapcsolatokhoz a mobil hálózaton való barangolás során. **Nincs konfigurálva** (alapértelmezés) engedélyezi a VPN-kapcsolatokat barangolás közben.
- **Csatlakoztatott eszközök szolgáltatás**: A **Letiltás** letiltja a csatlakoztatott eszközök platform (CDP) összetevőjét. A CDP lehetővé teszi a felderítést és a kapcsolódást más eszközökhöz (Bluetooth/LAN-on vagy a felhőben) a távoli alkalmazások indításához, a távoli üzenetküldéshez, a távoli alkalmazás-munkamenetekhez és más, az eszközök közötti élményekhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a csatlakoztatott eszközök szolgáltatást, amely lehetővé teszi a felderítést és a csatlakozást más Bluetooth-eszközökhöz.
- **NFC**: A **blokk** megakadályozza a kis hatótávolságú kommunikáció (NFC) képességeit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak az NFC-funkciók engedélyezését és konfigurálását az eszközön.
- **Wi-Fi**: A **Letiltás** megakadályozza, hogy a felhasználók a Wi-Fi-kapcsolatokat az eszközön használják és engedélyezze, konfigurálja és használja. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Wi-Fi-kapcsolatokat.
- **Automatikus csatlakozás Wi-Fi elérési**pontokhoz: A **Letiltás** megakadályozza, hogy az eszközök automatikusan csatlakozzanak a Wi-Fi elérési pontokhoz. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az eszközök automatikusan csatlakozzanak az ingyenes Wi-Fi elérési pontokhoz, és automatikusan elfogadják a kapcsolat használati feltételeit.
- **Wi-Fi manuális konfigurálása**: A **Letiltás** megakadályozza, hogy az eszközök CSATLAKOZZANAK a Mdm-kiszolgáló által telepített hálózatokon kívüli Wi-Fi-hez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára saját Wi-Fi-kapcsolataik hálózati SSID-azonosítóinak hozzáadását és konfigurálását.
- **Wi-Fi-ellenőrzési időköz**: Adja meg, hogy az eszközök milyen gyakran keressenek Wi-Fi-hálózatokat. Adjon meg 1 (leggyakoribb) és 500 (a legkevésbé gyakori) értéket. Az `0` alapértelmezett érték (nulla).

### <a name="bluetooth"></a>Bluetooth

Ezek a beállítások a [Bluetooth Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Bluetooth**: A **Letiltás** megakadályozza a felhasználók számára a Bluetooth engedélyezését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Bluetooth használatát az eszközön.
- **Bluetooth**-felderíthetőség: A **Letiltás** megakadályozza, hogy az eszköz felderíthető legyen más Bluetooth-kompatibilis eszközökön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi más Bluetooth-kompatibilis eszközök, például a Headsetek számára az eszköz felderítését.
- **Bluetooth**-előpárosítás: A **blokk** megakadályozza, hogy a megadott Bluetooth-eszközök automatikusan párosítva legyenek a gazdagép eszközzel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az automatikus párosítást a gazdagép eszközzel.
- **Bluetooth-hirdetés**: A **Letiltás** megakadályozza, hogy az eszköz Bluetooth-hirdetéseket küldjön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszköz számára a Bluetooth-hirdetmények küldését.
- **Bluetooth-engedélyezett szolgáltatások**: **Adja** meg az engedélyezett Bluetooth-szolgáltatások és-profilok listáját hexadecimális karakterláncként, `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`például:.

  A [ServicesAllowedList használati útmutatója](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) további információkat tartalmaz a szolgáltatás listájáról.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cloud-and-storage"></a>Felhő és tárolás

Ezek a beállítások a [fiókok házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Microsoft-fiók**: A **Letiltás** megakadályozza, hogy a végfelhasználók Microsoft-fiók társítsák az eszközzel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi Microsoft-fiók hozzáadását és használatát.
- **Nem Microsoft-fiók**: A **Letiltás** megakadályozza, hogy a végfelhasználók nem Microsoft-fiókokat adjanak hozzá a felhasználói felület használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a Microsoft-fiókhoz nem társított e-mail-fiókok hozzáadását.
- **Microsoft-fiók beállítások szinkronizálása**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz és az alkalmazás beállításai egy Microsoft-fiókhoz legyenek szinkronizálva az eszközök között. A **Letiltás** megakadályozza a szinkronizálást.
- **Microsoft-fiók bejelentkezési segédje**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a végfelhasználók elindíthatják és leállíthatják a **Microsoft-fiók bejelentkezési segédje** (wlidsvc) szolgáltatását. Ez az operációsrendszer-szolgáltatás lehetővé teszi, hogy a felhasználók bejelentkezzenek a Microsoft-fiókba. A **Letiltás** beállítás meggátolja a végfelhasználók számára a Microsoft bejelentkezési segéd szolgáltatás (wlidsvc) szabályozását.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cloud-printer"></a>Felhőbeli nyomtató

Ezek a beállítások a [EnterpriseCloudPrint házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Nyomtató felderítésének URL-címe**: Adja meg a felhőalapú nyomtatók keresésének URL-címét. Például írja be a következőt: `https://cloudprinterdiscovery.contoso.com`.
- A **nyomtató hozzáférési szolgáltatójának URL-címe**: Adja meg a hitelesítési végpont URL-címét az OAuth-tokenek lekéréséhez. Például írja be a következőt: `https://azuretenant.contoso.com/adfs`.
- **Azure Native Client app GUID**: Adja meg egy olyan ügyfélalkalmazás GUID azonosítóját, amely számára engedélyezett a OAuth jogkivonatok beolvasása a OAuth. Például írja be a következőt: `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **Nyomtatási szolgáltatás erőforrás-URI-ja**: Adja meg a Azure Portalban konfigurált nyomtatási szolgáltatás OAuth erőforrás-URI-JÁT. Például írja be a következőt: `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **A lekérdezni kívánt nyomtatók maximális**száma: Adja meg a lekérdezni kívánt nyomtatók maximális számát. Az alapértelmezett érték: `20`.
- **Nyomtató-felderítési szolgáltatás erőforrás-URI-ja**: Adja meg a OAuth-erőforrás URI-JÁT a Azure Portal konfigurált nyomtató-felderítési szolgáltatáshoz. Például írja be a következőt: `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> A [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)beállítása után megadhatja ezeket a beállításokat, majd üzembe helyezheti a Windows-eszközökön.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="control-panel-and-settings"></a>Vezérlőpult és Gépház

- **Beállítások alkalmazás**: A **Letiltás** megakadályozza, hogy a végfelhasználók hozzáférhessenek a Windows Settings alkalmazáshoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megnyissák a beállítások alkalmazást az eszközön.
  - **System**: A **Letiltás** megakadályozza a hozzáférést a beállítások alkalmazás rendszerterületéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
    - **Energiagazdálkodási és alvási beállítások módosítása** (csak asztali verzió): A **Letiltás** megakadályozza, hogy a végfelhasználók módosíthassák az eszköz energiagazdálkodási és alvási beállításait. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az energiagazdálkodási beállítások módosítását.
  - **Eszközök**: A **Letiltás** megakadályozza az eszközön a beállítások alkalmazás eszközök területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Hálózati Internet**: A **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás hálózati & internetes területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Személyre szabás**: A **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás személyre szabott területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Alkalmazások**: A **Letiltás** megakadályozza a hozzáférést az eszköz beállítások alkalmazásának alkalmazások területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Fiókok**: A **Letiltás** megakadályozza a hozzáférést az eszköz beállítások alkalmazásának fiókok területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Idő és nyelv**: A **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás Time & Language területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
    - **Rendszeridő módosítása**: A **Letiltás** megakadályozza, hogy a végfelhasználók módosíthassák a dátum-és időbeállításokat az eszközön. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.
    - **Területi beállítások módosítása** (csak asztali verzió): A **Letiltás** megakadályozza, hogy a végfelhasználók módosíthassák a régió beállításait az eszközön. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.
    - **Nyelvi beállítások módosítása (csak asztali verzió)** : A **Letiltás** megakadályozza a végfelhasználók számára az eszköz nyelvi beállításainak módosítását. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.

      [Beállítások házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Játék**: A **Letiltás** megakadályozza a hozzáférését az eszközön található beállítások alkalmazás játék területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Egyszerű hozzáférés**: A **blokk** megakadályozza az eszközön a beállítások alkalmazás egyszerű hozzáférés területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Adatvédelem**: A **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás adatvédelmi területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Frissítés és biztonság**: A **Letiltás** megakadályozza az eszközön a beállítások alkalmazás frissítés & biztonsági területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="display"></a>Megjelenítés

Ezek a beállítások a [megjelenítési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

A GDI DPI-méretezés lehetővé teszi, hogy a DPI-t nem támogató alkalmazások a figyelő DPI-vel legyenek tisztában.

- **A GDI-méretezés bekapcsolása az alkalmazásokhoz**: **Adja hozzá** azokat az örökölt alkalmazásokat, amelyeken be szeretné kapcsolni a GDI dpi-méretezést. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés be van kapcsolva a listában szereplő összes örökölt alkalmazáshoz.

- **A GDI-méretezés kikapcsolása az alkalmazásokhoz**: **Adja hozzá** azokat az örökölt alkalmazásokat, amelyeket a GDI DPI-méretezés ki szeretne kapcsolni. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés ki van kapcsolva a listában szereplő összes örökölt alkalmazás esetében.

Egy. csv -fájlt is importálhat az alkalmazások listájával.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="general"></a>Általános

Ezek a beállítások az [élmény házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)-t használják; amely a támogatott Windows-kiadásokat is felsorolja. 

- **Képernyőfelvétel** (csak mobil): A **Letiltás** megakadályozza, hogy a végfelhasználók képernyőfelvételeket készítsenek az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Másolás és beillesztés (csak mobil)** : A **Letiltás** megakadályozza, hogy a végfelhasználók az eszközön lévő alkalmazások közötti másolást és beillesztést használják. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Regisztráció manuális**törlése: A **Letiltás** megakadályozza a végfelhasználók számára a munkahelyi fiók törlését az eszköz munkahelyi Vezérlőpultjának használatával. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.

  Ez a házirend-beállítás nem vonatkozik arra az esetre, ha a számítógép Azure AD-hez csatlakozik, és engedélyezve van az automatikus regisztráció.

- **Főtanúsítvány manuális telepítése** (csak mobil): A **Letiltás** megakadályozza a végfelhasználók számára a főtanúsítványok és a KÖZTes Cap-tanúsítványok manuális telepítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kamera**: A **Letiltás** megakadályozza, hogy a végfelhasználók a kamerát használják az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **OneDrive fájl szinkronizálása**: A **Letiltás** megakadályozza, hogy a végfelhasználók szinkronizálják a fájlokat a OneDrive az eszközről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Cserélhető tároló**: A **Letiltás** megakadályozza, hogy a végfelhasználók külső tárolóeszközöket használjanak, például SD-kártyákat az eszközzel. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- Földrajzi hely: A **Letiltás** megakadályozza, hogy a végfelhasználók bekapcsolják a Location Servicest az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Internetkapcsolat megosztása**: A **blokk** megakadályozza az internetkapcsolat megosztását az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Telefon**alaphelyzetbe állítása: A **Letiltás** megakadályozza, hogy a végfelhasználók törölje vagy visszaállítsa a gyári beállítások visszaállítását az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **USB-kapcsolat**: A **blokk** megakadályozza a külső tárolóeszközök elérését az eszközön található USB-kapcsolaton keresztül. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót. Ez a beállítás nem érinti az USB-töltést.
- **Lopásgátló üzemmód** (csak mobil): A **Letiltás** megakadályozza, hogy a végfelhasználók lopásgátló üzemmódot válasszanak az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Cortana**: Tiltsa le a Cortana hangsegédet az eszközön. Ha a Cortana ki van kapcsolva, a felhasználók továbbra is kereshetik az eszközön található elemeket. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Cortana.
- **Hangrögzítés** (csak mobil): A **Letiltás** megakadályozza a végfelhasználók számára az eszköz hangrögzítőjét az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások hangfelvételét.
- **Eszköz nevének módosítása** (csak mobil): A **Letiltás** megakadályozza a végfelhasználók számára az eszköz nevének módosítását. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kiépítési csomagok hozzáadása**: A **Letiltás** megakadályozza, hogy a futásidejű konfigurációs ügynök kiépítési csomagokat telepítsen az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kiépítési csomagok eltávolítása**: A **Letiltás** megakadályozza, hogy a futásidejű konfigurációs ügynök eltávolítja a kiépítési csomagokat az eszközről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Eszköz felderítése**: A **Letiltás** megakadályozza, hogy az eszköz más eszközök által is felderíthető legyen. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Feladat kapcsolója** (csak mobil): A **Letiltás** megakadályozza a feladat váltását az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **SIM-kártya hiba párbeszédpanelje** (csak mobil): A hibaüzenetek megjelenítésének **letiltása** az eszközön, ha a rendszer nem észlel SIM-kártyát. **Nincs konfigurálva** (alapértelmezés) megjeleníti a hibaüzeneteket.
- **Szabadkézi munkaterület**: Válassza ki, hogy a felhasználó hogyan fér hozzá a tinta munkaterülethez. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Bekapcsolja a tinta munkaterületet, és a felhasználó használhatja a zárolási képernyő felett.
  - **Zárolási képernyőn**Letiltva: A tinta munkaterület engedélyezve van, és a funkció be van kapcsolva. A felhasználó azonban nem fér hozzá a zárolási képernyő felett.
  - Letiltva: A szabadkézi munkaterülethez való hozzáférés le van tiltva. A szolgáltatás ki van kapcsolva.

  [WindowsInkWorkspace házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Automatikus újratelepítés**: Válassza az **Engedélyezés lehetőséget** , hogy a rendszergazdai jogosultságokkal rendelkező felhasználók az eszköz zárolási képernyőjén a **CTRL + Win + R billentyűkombinációval** törölhetik az összes felhasználói és beállítást. A rendszer automatikusan újrakonfigurálja az eszközt, és újból regisztrálja őket a felügyeletbe. **Nincs konfigurálva** (alapértelmezés) megakadályozza ezt a funkciót.
- **A hálózathoz való csatlakozás megkövetelése a felhasználók számára az eszköz telepítése során**: Válassza a **szükséges** lehetőséget, hogy az eszköz csatlakozzon a hálózathoz, mielőtt továbblép a hálózat lapra a Windows telepítése során. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy a hálózat oldalára lépjenek, még akkor is, ha nem csatlakozik hálózathoz.

  A beállítás az eszköz legközelebb törlésével vagy alaphelyzetbe állításával válik hatályossá. A többi Intune-konfigurációhoz hasonlóan az eszközt az Intune-nak kell regisztrálnia és kezelnie a konfigurációs beállítások fogadásához. Ha azonban regisztrálva van, és a házirendeket fogad, akkor az eszköz alaphelyzetbe állítása a következő Windows-telepítéskor kényszeríti a beállítást.

- **Közvetlen memória-hozzáférés**: A **blokk** megakadályozza a közvetlen memória-hozzáférés (DMA) használatát az összes melegen csatlakoztatható PCI-porton, amíg a felhasználó be nem jelentkezik a Windowsba. **Engedélyezve** (alapértelmezés) lehetővé teszi a hozzáférést a DMA-hoz, még akkor is, ha a felhasználó nincs bejelentkezve.

  CSP [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Folyamatok leállítása a Feladatkezelő eszközből**: Ez a beállítás határozza meg, hogy a nem rendszergazdák használhatják-e a Feladatkezelőt a feladatok befejezéséhez. A **Letiltás** megakadályozza, hogy az általános jogú felhasználók (nem rendszergazdák) a Feladatkezelő segítségével fejezzenek be egy folyamatot vagy feladatot az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az általános jogú felhasználók számára, hogy egy folyamatot vagy feladatot a Feladatkezelő használatával fejezzenek ki.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="locked-screen-experience"></a>Zárolási képernyő felülete

- **Műveletközpont értesítései (csak mobil)** : A **Letiltás** megakadályozza a Műveletközpont értesítéseinek megjelenítését az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválaszthatják, hogy mely alkalmazások jelenjenek meg értesítések a zárolási képernyőn.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **Zárolt képernyős kép URL-címe (csak asztali verzió)** : Adja meg egy olyan kép URL-címét JPG, JPEG vagy PNG formátumban, amelyet a Windows zárolási képernyőjének háttérképe használ. Például írja be a következőt: `https://contoso.com/image.png`. Ez a beállítás zárolja a rendszerképet, és ezt követően nem módosítható.
- **Felhasználó által konfigurálható képernyő-időkorlát (csak mobil)** : **Lehetővé** teszi, hogy a felhasználók konfigurálja a képernyő időkorlátját. **Nincs konfigurálva** (alapértelmezés) nem adja meg a felhasználóknak ezt a lehetőséget.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **Cortana zárolt képernyőn** (csak asztali verzió): A **Letiltás** megakadályozza, hogy a felhasználók a Cortana használják, amikor az eszköz a zárolási képernyőn található. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Cortana való interakciót.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Bejelentési értesítések zárolt képernyőn**: **Letiltja** a bejelentési értesítések elrejtését az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket az értesítéseket.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Képernyő időkorlátja (csak mobil)** : Állítsa be azt az időtartamot (másodpercben), amelyet a képernyő zárolása a képernyő kikapcsolásakor kikapcsol. A támogatott értékek a 11-1800. Adja meg `300` például, hogy ezt az időkorlátot 5 percre állítsa be.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="messaging"></a>Üzenetkezelési

Ezek a beállítások az [üzenetküldési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Üzenet-szinkronizálás (csak mobil)** : A **Letiltás** letiltja a szöveges üzenetek biztonsági mentését és visszaállítását, valamint az üzenetek Windows-eszközök közötti szinkronizálását. A Letiltás segít elkerülni a szervezet vezérlőn kívüli kiszolgálókon tárolt adatok tárolását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók megváltoztassák ezeket a beállításokat, és szinkronizálják az üzeneteiket.
- **MMS (csak mobil)** : A **Letiltás** letiltja az MMS-küldési és-fogadási funkciókat az eszközön. A vállalatok esetében ezzel a szabályzattal letilthatja az MMS-eszközöket az eszközökön a naplózási vagy felügyeleti követelmények részeként. **Nincs konfigurálva** (alapértelmezés) engedélyezi az MMS küldését és fogadását.
- **RCS (csak mobil)** : A **Letiltás** letiltja az eszközön a RCS-küldési és-fogadási funkciókat. A vállalatok esetében ezzel a szabályzattal tilthatja le a RCS az eszközökön a naplózási vagy felügyeleti követelmények részeként. **Nincs konfigurálva** (alapértelmezés) engedélyezi a RCS küldését és fogadását.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="microsoft-edge-browser"></a>Microsoft Edge böngésző

Ezek a beállítások a [böngésző házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

### <a name="use-microsoft-edge-kiosk-mode"></a>A Microsoft Edge kioszk mód használata

Az elérhető beállítások a választott lehetőségtől függően változnak. A választható lehetőségek:

- **Nem** (alapértelmezett): A Microsoft Edge nem kioszk módban fut. A Microsoft Edge összes beállítását módosíthatja és konfigurálhatja.
- **Digitális/interaktív aláírások (egyetlen alkalmazás kioszkja)** : A Microsoft Edge-beállítások a digitális/interaktív aláíráshoz a Microsoft Edge kioszk módban csak a Windows 10 single-app kioszkok esetében használhatók. Ezzel a beállítással megnyithatja a teljes URL-címet, és csak az adott webhelyen lévő tartalmat jelenítheti meg. A [digitális jelek beállítása](https://docs.microsoft.com/windows/configuration/setup-digital-signage) a szolgáltatással kapcsolatos további információkat tartalmaz.
- **InPrivate nyilvános böngészés (egyetlen alkalmazás kioszkja)** : Azokat a Microsoft Edge-beállításokat szűri, amelyek az InPrivate nyilvános böngészéshez használhatók a Microsoft Edge kioszk módban a Windows 10 single-app kioszkokban való használathoz. A Microsoft Edge többoldalas verzióját futtatja.
- **Normál mód (többalkalmazásos kioszk)** : A Microsoft Edge-beállítások normál, a Microsoft Edge-kioszk üzemmódra érvényes beállításait szűri. A Microsoft Edge teljes verzióját futtatja minden böngészési funkcióval.
- **Nyilvános böngészés (többalkalmazásos kioszk)** : A Windows 10-es többalkalmazásos kioszkon nyilvános tallózásra alkalmazható Microsoft Edge-beállítások szűrése.  Futtatja a Microsoft Edge multi-Tab verzióját.

> [!TIP]
> A beállításokkal kapcsolatos további információkért lásd a [Microsoft Edge kioszk mód konfigurációs típusait](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Ez az eszköz-korlátozási profil közvetlenül kapcsolódik a [Windows kioszk beállításainak](kiosk-settings-windows.md)használatával létrehozott kioszk-profilhoz. Összefoglalás:

1. Hozza létre a [Windows kioszk beállítási](kiosk-settings-windows.md) profilt az eszköz teljes képernyős módban való futtatásához. Válassza ki a Microsoft Edge alkalmazást, és állítsa be a Microsoft Edge kioszk üzemmódot a kioszk profilban.
2. Hozza létre a jelen cikkben ismertetett eszköz-korlátozási profilt, és konfigurálja a Microsoft Edge-ben engedélyezett bizonyos szolgáltatásokat és beállításokat. Ügyeljen arra, hogy ugyanazt a Microsoft Edge kioszk Mode-típust válassza, mint a kioszk-profilban ([Windows kioszk beállításai](kiosk-settings-windows.md)). 

    A teljes [képernyős mód beállításai](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) egy nagyszerű erőforrás.

> [!IMPORTANT] 
> Győződjön meg arról, hogy a Microsoft Edge-profilt ugyanahhoz az eszközhöz rendeli hozzá, mint a kioszk-profilt ([Windows kioszk beállításai](kiosk-settings-windows.md)).

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Kezdési élmény

- **A Microsoft Edge elindítása**: Válassza ki, hogy mely lapok nyílnak meg a Microsoft Edge indításakor. A választható lehetőségek:
  - **Egyéni kezdő lapok**: Adja meg a kezdő lapokat, `http://www.contoso.com`például:. A Microsoft Edge betölti a beírt kezdő lapokat.
  - **Új lap lapja**: A Microsoft Edge betöltése bármi bekerül az **új lap URL-címének** beállításaiba.
  - **Utolsó munkamenet lapja**: A Microsoft Edge betölti az utolsó munkamenet lapot.
  - **Kezdőlapok a helyi alkalmazás beállításaiban**: A Microsoft Edge az operációs rendszer által meghatározott alapértelmezett kezdőlaptal kezdődik.

- **Kezdő lapok módosításának engedélyezése a felhasználó számára**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók számára a kezdőlapok módosítását. A rendszergazdák a `EdgeHomepageUrls` segítségével megadhatják a felhasználók által alapértelmezés szerint megjelenő kezdő lapokat a Microsoft Edge megnyitásakor. **Nem** blokkolja a felhasználók a kezdőlapok módosítását.
- **Webes tartalom engedélyezése az új lapon**lapon: Ha az **Igen** értékre van állítva (alapértelmezett), a Microsoft Edge megnyitja az **új lap URL-címében** megadott URL-címet. Ha az **új lap URL-címe** üres, a Microsoft Edge megnyitja az új lap lapot a Microsoft Edge beállításaiban. A felhasználók módosíthatják azt. Ha a **nem**értékre van állítva, a Microsoft Edge új lapot nyit meg egy üres oldallal. A felhasználók nem változtathatják meg.
- **Új lap URL-címe**: Adja meg az új lap lapon megnyitható URL-címet. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.

- **Kezdőlap gomb**: Válassza ki, hogy mi történjen a Kezdőlap gomb kiválasztásakor. A választható lehetőségek:
  - **Kezdő lapok**: Megnyitja a kiválasztott lehetőséget a **Microsoft Edge elindítása** a beállítással
  - **Új lap lapja**: Megnyitja az **új lap URL-címe** beállításban megadott URL-címet.
  - **Kezdőlap gomb URL-címe**: Adja meg a megnyitni kívánt URL-címet. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.
  - **Kezdőlap gomb elrejtése**: Elrejti a Kezdőlap gombot
- **A Kezdőlap gomb módosításának engedélyezése a felhasználók**számára: **Igen** , lehetővé teszi a felhasználók számára a Kezdőlap gomb módosítását. A felhasználó módosításai felülbírálják a rendszergazdai beállításokat a Home (Kezdőlap) gombra. **Nem** (alapértelmezés) megakadályozza, hogy a felhasználók megváltoztassák, hogyan konfigurálta a rendszergazda a Kezdőlap gombot.
- **Első futtatási élmény megjelenítése lap (csak mobil)** : **Igen** (alapértelmezés) megjeleníti a Microsoft Edge első használat bemutatása lapját. A Microsoft Edge első futtatásakor a bevezető oldal **nem** jelenik meg. Ez a funkció lehetővé teszi, hogy a vállalatok, például a nulla kibocsátási konfigurációkba beléptetett szervezetek regisztrálva legyenek ezen a lapon.
- **Első futtatási élmény URL-listájának helye** (Csak Windows 10 Mobile esetén): Adja meg azt az URL-címet, amely az első futtatási oldal URL-címét tartalmazó XML-fájlra mutat. Például írja be a következőt: `https://www.contoso.com/sites.xml`.

- **Böngésző frissítése üresjárati idő után**: Adja meg az üresjárati percek számát, amíg a böngésző frissül, 0-1440 percen belül. Az `5` alapértelmezett érték perc. Ha a `0` (nulla) értékre van állítva, a böngésző üresjárat után nem frissül.

  Ez a beállítás csak akkor érhető el, ha [InPrivate nyilvános böngészés (Egyalkalmazásos kioszk)](#use-microsoft-edge-kiosk-mode)fut.

- **Előugró ablakok engedélyezése** (csak asztali verzió): **Igen** (alapértelmezés) lehetővé teszi az előugró ablakok használatát a böngészőben. **Nem** akadályozza meg az előugró ablakokat a böngészőben.
- **Intranetes forgalom küldése az Internet Explorernek** (Csak asztali verzió): **Igen** , lehetővé teszi a felhasználók számára az intranetes webhelyek megnyitását az Internet Explorerben a Microsoft Edge helyett. Ez a beállítás a visszamenőleges kompatibilitáshoz szükséges. **Nem** (alapértelmezés) lehetővé teszi a felhasználók számára a Microsoft Edge használatát.
- **Vállalati üzemmód helyének listázási helye** (Csak asztali verzió): Adja meg azt az URL-címet, amely a vállalati módban megnyitott webhelyek listáját tartalmazó XML-fájlra mutat. A felhasználók nem változtathatják meg a listát. Például írja be a következőt: `https://www.contoso.com/sites.xml`.
- **Üzenet a helyek Internet Explorerben való megnyitásakor**: Ezzel a beállítással konfigurálhatja a Microsoft Edge-t, hogy megjelenjen egy értesítés, mielőtt egy webhely megnyílik az Internet Explorer 11 böngészőben. A választható lehetőségek:
  - **Ne jelenjen**meg az üzenet: Az operációs rendszer alapértelmezett viselkedése használatos, amely nem jeleníti meg az üzenetet.
  - **A webhely megnyitására szolgáló üzenet megjelenítése az Internet Explorer 11 böngészőben**: Az üzenet megjelenítése az IE-helyek megnyitásakor. A helyek megnyitva az IE-ben. 
  - A **Microsoft Edge-helyek megnyitására szolgáló lehetőséggel rendelkező üzenet megjelenítése**: Az üzenet megjelenítése a helyek Edge-beli megnyitásakor. Az üzenet tartalmaz egy **lépést a Microsoft Edge-** hivatkozásban, hogy a felhasználók az IE helyett a Microsoft Edge-et is kiválaszthatják.

  > [!IMPORTANT]
  > Ehhez a beállításhoz a **vállalati üzemmód helyének listázási helye** beállítást kell használnia, az intranetes adatforgalom **küldése az Internet Explorerhez** vagy mindkét beállításhoz.

- **Microsoft kompatibilitási lista engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft kompatibilitási listájának használatát. **Nem** akadályozza meg a Microsoft-kompatibilitási listát a Microsoft Edge-ben. A Microsoft ezen listája segíti a Microsoft Edge számára az ismert kompatibilitási problémákkal rendelkező helyek megfelelő megjelenítését.
- Előtöltési **kezdőlapok és új lap**lap: **Igen** (alapértelmezés) az operációs rendszer alapértelmezett viselkedését használja, amely a lapok betöltését is okozhatja. Az előre betöltéssel csökkentheti a Microsoft Edge elindításának idejét és az új lapok betöltését. A **nem** akadályozza meg, hogy a Microsoft Edge ne legyenek előre betöltve a kezdőlapok és az új lapok.
- **Kezdőlapok és új lap megnyitása**: **Igen** (alapértelmezés) az operációs rendszer alapértelmezett viselkedését használja, amely a lapok előindítására is használható. Az előzetes indítás segít a Microsoft Edge teljesítményében, és minimálisra csökkenti a Microsoft Edge elindításához szükséges időt. **Nem** akadályozza meg, hogy a Microsoft Edge előre elindítsa a kezdőlapokat és az új lapokat.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="favorites-and-search"></a>Kedvencek és keresés

- **Kedvencek sáv megjelenítése**: Válassza ki, hogy mi történjen a Microsoft Edge-lapok Kedvencek sávján. A választható lehetőségek:
  - **A kezdő és az új**lapokon: Megjeleníti a Kedvencek sávot a Microsoft Edge indításakor, valamint az összes lap lapjain. A végfelhasználók módosíthatják ezt a beállítást.
  - **Minden oldalon**: Megjeleníti a Kedvencek sávot az összes oldalon. A végfelhasználók nem változtathatják meg ezt a beállítást.
  - **Rejtett**: Elrejti a Kedvencek sávot az összes oldalon. A végfelhasználók nem változtathatják meg ezt a beállítást.
- **Kedvencek módosításának engedélyezése**: **Igen** (alapértelmezés) az alapértelmezett operációs rendszert használja, amely lehetővé teszi a felhasználók számára a lista módosítását. A **nem** teszi lehetővé a végfelhasználók számára a kedvencek listájának hozzáadását, importálását, rendezését és szerkesztését.
  - **Kedvencek listája**: Adja meg az URL-címek listáját a Kedvencek fájlhoz. Adja `http://contoso.com/favorites.html`meg például a következőt:.
- **Kedvencek szinkronizálása a Microsoft böngészők között** (Csak asztali verzió): **Igen** kényszeríti a Windowst, hogy szinkronizálja a kedvenceket az Internet Explorer és a Microsoft Edge között. A Kedvencek között a hozzáadások, a törlések, a módosítások és a megrendelési módosítások megoszthatók a böngészők között.  **Nem** (alapértelmezés) az alapértelmezett operációs rendszert használja, amely lehetővé teheti a felhasználóknak a Kedvencek szinkronizálását a böngészők között.
- **Alapértelmezett keresőmotor**: Válassza ki az alapértelmezett keresőmotort az eszközön. A végfelhasználók ezt az értéket bármikor módosíthatják. A választható lehetőségek:
  - Keresőmotor az ügyfél Microsoft Edge-beállításaiban
  - Bing
  - Google
  - Yahoo
  - Egyéni érték: A **OpenSearch XML URL-címe**mezőben adjon meg egy HTTPS URL-címet, amely tartalmazza a keresőmotor rövid nevét és URL-címét (minimum). Például írja be a következőt: `https://www.contoso.com/opensearch.xml`.
- **Keresési javaslatok megjelenítése**: **Igen** (alapértelmezés) lehetővé teszi, hogy a keresőmotor a címsorban beírt keresési kifejezésekkel jelezze a helyeket. **Nem** akadályozza meg ezt a funkciót.
- **A keresőmotor módosításának engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi, hogy a felhasználók új keresőmotorokat adjanak hozzá, vagy megváltoztassák az alapértelmezett keresőmotort a Microsoft Edge-ben. A **nem** gombra kattintva megakadályozhatja, hogy a felhasználók testreszabják a keresőmotort.

  Ez a beállítás csak akkor érhető el, ha [normál módban fut (több alkalmazásból álló kioszk)](#use-microsoft-edge-kiosk-mode).

Válassza ki **OK** a módosítások mentéséhez.

### <a name="privacy-and-security"></a>Adatvédelem és biztonság

- **InPrivate-böngészés engedélyezése**: **Igen** (alapértelmezés) engedélyezi a InPrivate-böngészést a Microsoft Edge-ben. Az összes InPrivate-fül bezárása után a Microsoft Edge törli a böngészési adatait az eszközről. **Nem** akadályozza meg, hogy a végfelhasználók InPrivate-böngészési munkameneteket nyissanak meg.
- **Böngészési előzmények mentése**: **Igen** (alapértelmezett) a böngészési előzmények mentésének engedélyezése a Microsoft Edge-ben. **Nem** akadályozza meg a böngészési előzmények mentését.
- **Böngészési adatvesztés törlése** kilépéskor (csak asztali verzió): **Igen** – törli az előzményeket és a böngészési adatokat, amikor a felhasználó kilép a Microsoft Edge-ből. **Nem** (alapértelmezés) az operációs rendszer alapértelmezését használja, amely gyorsítótárazhatja a böngészési adatfájlokat.
- **A böngésző beállításainak szinkronizálása a felhasználó eszközei között**: Válassza ki, hogyan szeretné szinkronizálni a böngésző beállításait az eszközök között. A választható lehetőségek:
  - **Engedélyezés**: A Microsoft Edge böngésző beállításainak szinkronizálásának engedélyezése a felhasználó eszközei között
  - **Felhasználói felülbírálás letiltása és engedélyezése**: A Microsoft Edge böngésző beállításainak szinkronizálásának letiltása a felhasználó eszközei között. A felhasználók felülbírálhatja ezt a beállítást.
  - **Letiltás**: A Microsoft Edge böngésző beállításainak szinkronizálásának tiltása a felhasználók eszközei között. A felhasználók nem írhatják felül ezt a beállítást.

Ha a "felhasználói felülbírálás tiltása és engedélyezése" lehetőség van kiválasztva, a felhasználó felülbírálhatja a rendszergazda megjelölését.

- A **Password Manager engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára a Password Manager automatikus használatát, amely lehetővé teszi a felhasználók számára a jelszavak mentését és kezelését az eszközön. **Nem** akadályozza meg a Microsoft Edge használatát a Password Manager használatával.
- **Cookie-k**: Válassza ki, hogy a cookie-k hogyan legyenek kezelve a böngészőben. A választható lehetőségek:
  - **Engedélyezés**: A cookie-k tárolása az eszközön történik.
  - **Az összes cookie blokkolása**: A cookie-k nem tárolódnak az eszközön.
  - **Csak a harmadik féltől származó cookie-k letiltása**: A harmadik féltől származó vagy partneri cookie-k nem tárolódnak az eszközön.
- **Automatikus kitöltés engedélyezése az űrlapokon**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy módosítsák a böngésző automatikus kiegészítési beállításait, és automatikusan feltöltsék az űrlapmezők tartalmát. **Nem** tiltja le az automatikus kitöltés funkciót a Microsoft Edge-ben.
- **Nem nyomon követett fejlécek küldése**: **Igen** , a nyomkövetési adatokat kérő webhelyeken nem követhető fejlécek küldése (ajánlott). **Nem** (alapértelmezés) nem küld fejléceket, amelyek lehetővé teszik a webhelyek számára a felhasználó nyomon követését. A felhasználó beállítható.
- **WebRTC localhost IP-cím megjelenítése**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók localhost IP-címének megjelenítését, amikor telefonhívásokat végez a protokoll használatával. A **nem** akadályozza meg, hogy a felhasználók localhost IP-címe megjelenjen. 
- **Élő csempe**-adatgyűjtés engedélyezése: **Igen** (alapértelmezés) lehetővé teszi, hogy a Microsoft Edge adatokat gyűjtsön a Start menübe rögzített élő csempéről. **Nem** akadályozza meg az adatok gyűjtését, ami korlátozott felhasználói élményt biztosíthat a felhasználóknak.
- A **felhasználó felülbírálhatja a tanúsítvány hibáit**: **Igen** (alapértelmezés) lehetővé teszi, hogy a felhasználók hozzáférhessenek SSL/Transport Layer Security (SSL/TLS) hibákat tartalmazó webhelyekhez. **Nem** (fokozott biztonság esetén ajánlott) megakadályozza, hogy a felhasználók SSL-vagy TLS-hibákkal férhessenek hozzá a webhelyekhez.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="additional"></a>Továbbiak

- **Microsoft Edge böngésző engedélyezése** (csak mobil): **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge webböngésző használatát a mobileszközön. **Nem** akadályozza meg a Microsoft Edge használatát az eszközön. Ha a **nem**lehetőséget választja, a többi egyéni beállítás csak az asztalra vonatkozik.
- **Címsor legördülő menüjének engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára, hogy megjelenítse a címsor legördülő listáját a javaslatok listájával. A **nem** állítja le a Microsoft Edge-t a legördülő listában szereplő javaslatok listájának megjelenítéséhez a beíráskor. Ha a **nem**értékre van állítva, akkor:
  - A Microsoft Edge és a Microsoft-szolgáltatások közötti hálózati sávszélesség csökkentése.
  - Tiltsa le a **Keresés és a webhely javaslatainak** beírása a Microsoft Edge-> beállításainál.
- **Teljes képernyős mód engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára a teljes képernyős mód használatát, amely csak a webes tartalmat jeleníti meg, és elrejti a Microsoft Edge felhasználói felületét. A teljes képernyős mód **nem** akadályozza meg a Microsoft Edge-ben.
- **Az about Flags lap engedélyezése**: **Igen** (alapértelmezés) az alapértelmezett operációs rendszert használja, amely lehetővé teheti `about:flags` az oldal elérését. A `about:flags` lap lehetővé teszi a felhasználók számára a fejlesztői beállítások módosítását és a kísérleti funkciók engedélyezését. **Nem** akadályozza meg, hogy a végfelhasználók hozzáférjenek az `about:flags` oldalhoz a Microsoft Edge-ben.
- **Fejlesztői eszközök engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy alapértelmezés szerint a weblapok létrehozásához és hibakereséséhez az F12 fejlesztői eszközöket használják. **Nem** akadályozza meg, hogy a végfelhasználók az F12 fejlesztői eszközöket használják.
- **JavaScript engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a parancsfájlok (például a JavaScript) futtatását a Microsoft Edge böngészőben. **Nem** akadályozza meg, hogy a böngészőben a Java-parancsfájlok fussanak.
- A **felhasználók**a bővítményeket telepíthetik: **Igen** (alapértelmezés) lehetővé teszi a végfelhasználók számára a Microsoft Edge-bővítmények telepítését az eszközön. **Nem** akadályozza meg a telepítést.
- **Fejlesztői bővítmények közvetlen telepítési engedélyezése**: **Igen** (alapértelmezés) az alapértelmezett operációs rendszert használja, amely lehetővé teszi a közvetlen telepítési. A közvetlen telepítési telepíti és futtatja a nem ellenőrzött bővítményeket. **Nem** akadályozza meg, hogy a Microsoft Edge a közvetlen telepítési a **Load Extensions** szolgáltatást használja. Nem akadályozza meg, hogy a közvetlen telepítési bővítmények más módon, például a PowerShell használatával legyenek használva.
- **Szükséges bővítmények**: Válassza ki, hogy mely bővítményeket szeretné kikapcsolni a végfelhasználók számára a Microsoft Edge-ben. Adja meg a csomag családjának nevét, majd kattintson a **Hozzáadás**gombra. [A csomaghoz tartozó családi név (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) megkeresése néhány útmutatást tartalmaz.

  Importálhat egy CSV-fájlt is, amely tartalmazza a csomag családjának nevét. Vagy **exportálja** a megadott csomagbeli család nevét.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="network-proxy"></a>Hálózati proxy

Ezek a beállítások a [NetworkProxy házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Proxybeállítások automatikus észlelése**: A **Letiltás** letiltja, hogy az eszköz automatikusan észlelje a proxy automatikus konfigurációs (PAC) parancsfájlját. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót. Ha engedélyezve van, az eszköz megpróbálja megkeresni egy PAC-szkript elérési útját.
- **Proxy parancsfájl használata**: A proxykiszolgáló konfigurálásához válassza az **Engedélyezés lehetőséget** a PAC-szkript elérési útjának megadásához. **Nincs konfigurálva** (alapértelmezés) nem teszi lehetővé a PAC-szkriptek URL-címének megadását.
  - **Telepítési parancsfájl URL-címe**: Adja meg a proxykiszolgáló konfigurálásához használni kívánt PAC-parancsfájl URL-címét.
- **Manuális proxykiszolgáló használata**: Válassza az **Engedélyezés lehetőséget** a proxykiszolgáló nevének vagy IP-címének és TCP-portszámának manuális megadásához. **Nincs konfigurálva** (alapértelmezés) nem teszi lehetővé a proxykiszolgáló adatainak manuális megadását.
  - **Címe**: Adja meg a proxykiszolgáló nevét vagy IP-címét.
  - **Portszám**: Adja meg a proxykiszolgáló portszámát.
  - **Proxy**-kivételek: Adja meg azokat az URL-címeket, amelyeknek nem kell a proxykiszolgálót használniuk. Az egyes címeket pontosvesszővel választhatja el egymástól.
  - **Proxykiszolgáló kihagyása helyi címen**: **Nincs konfigurálva** (alapértelmezés) megakadályozza a proxykiszolgáló használatát az intraneten lévő helyi címekhez. **Engedélyezi** a proxykiszolgáló használatát a helyi címekhez.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="password"></a>Windows 10

Ezek a beállítások a [DeviceLock házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Jelszó**: **Kérje** meg a végfelhasználót, hogy adjon meg egy jelszót az eszköz eléréséhez. **Nincs konfigurálva** (alapértelmezés) jelszó nélkül teszi lehetővé az eszköz hozzáférését. Csak a helyi fiókokra vonatkozik. A tartományi fiókhoz tartozó jelszavakat Active Directory (AD) és az Azure AD is konfigurálja.

  - **Szükséges jelszó típusa**: Válassza ki a jelszó típusát. A választható lehetőségek:
    - **Nincs konfigurálva**: A jelszó tartalmazhat számokat és betűket.
    - **Numerikus**: A jelszónak csak számnak kell lennie.
    - **Alfanumerikus karakterek**: A jelszónak számokból és betűkből álló kombinációnak kell lennie.
  - **Jelszó minimális hossza**: Adja meg a minimálisan szükséges számot vagy karaktereket a 4-16-ból. Írja be például, `6` hogy legalább hat karaktert kell megadnia a jelszó hosszában.
  
    > [!IMPORTANT]
    > Ha a jelszóra vonatkozó követelményt egy Windows asztalon módosítják, a felhasználók a következő bejelentkezéskor jelentkeznek, ahogy az az eszköz tétlenről aktív állapotba kerül. A követelménynek megfelelő jelszóval rendelkező felhasználókat a rendszer továbbra is megkéri a jelszavuk módosítására.
    
  - **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg az eszköz törlése előtt engedélyezett hitelesítési hibák számát, akár 11-ig. A beírt érvényes szám a kiadástól függ. A [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) listázza a támogatott értékeket. `0`(nulla) letilthatja az eszköz törlési funkcióját.

    Ez a beállítás a kiadástól függően más hatással is van. A beállítás részletes ismertetését lásd: [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **A képernyőfelvételek legfeljebb ennyi perc inaktivitás**után: Adja meg, hogy az eszköznek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.
  - **Jelszó érvényessége (napokban)** : Adja meg az időtartamot napokban, amikor az eszköz jelszavát módosítani kell, a 1-365-ból. Adja meg `90` például a következőt:, hogy 90 nap után lejárja a jelszót.
  - **Korábbi jelszavak újbóli használatának tiltása**: Adja meg a korábban nem használható jelszavak számát 1-24-től. Írja be `5` például, hogy a felhasználók nem állíthatnak be új jelszót a jelenlegi jelszavuk vagy az előző négy jelszavuk bármelyike számára.
  - **Jelszó kérése, ha az eszköz visszatér az inaktív állapotból** (Mobil és holografikus): Válassza a **szükséges** lehetőséget, hogy a felhasználóknak meg kell adniuk egy jelszót az eszköz zárolásának feloldásához. **Nincs konfigurálva** (alapértelmezés) nem igényel PIN-kódot vagy jelszót, amikor az eszköz visszatér inaktív állapotból.
  - **Egyszerű jelszavak**: Állítsa a **Letiltás** értékre, így a `1234` felhasználók nem hozhatnak létre egyszerű jelszavakat, például vagy. `1111` Állítsa be úgy, hogy **ne legyen konfigurálva** (alapértelmezett), hogy `1234` a felhasználók jelszavakat hozzanak létre (például vagy `1111`). Ez a beállítás a Windows-képjelszavak használatát is engedélyezi vagy letiltja.
- **Automatikus titkosítás a AADJ során**: A **blokk** megakadályozza a BitLocker-eszközök automatikus titkosítását, ha az eszköz az első használatra készült, amikor az eszköz csatlakoztatva van az Azure ad-hez. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezett alapértékét használja, amely lehetővé teheti a titkosítást. További információ a [BitLocker-eszközök titkosításáról](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- A **Federal Information Processing standard (FIPS) szabályzata**: Az **Engedélyezés** a Federal Information Processing standard (FIPS) szabályzatot használja, amely a titkosításhoz, kivonatoláshoz és aláíráshoz az Egyesült Államok kormányzati szabványa. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezett alapértékét használja, amely nem használ FIPS-t.

  [Kriptográfia/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello-eszköz hitelesítése**: Windows Hello Companion-eszköz (például telefon, fitness-sáv vagy IoT-eszköz) használatának **engedélyezése** a felhasználók számára Windows 10 rendszerű számítógépre való bejelentkezéshez. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezését használja, ami megakadályozhatja a Windows Hello Companion-eszközök hitelesítését a Windowsban.

  [Hitelesítés/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Webes bejelentkezés**: Lehetővé teszi a Windows bejelentkezési támogatását a nem ADFS (Active Directory összevonási szolgáltatások (AD FS)) összevont szolgáltatók számára, például Security Assertion Markup Language (SAML). Az SAML olyan biztonságos jogkivonatokat használ, amelyek egy egyszeri bejelentkezési (SSO) élményt biztosítanak a webböngészőknek. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett értékeit használja az eszközön.
  - **Engedélyezve**: A webes hitelesítőadat-szolgáltató engedélyezve van a bejelentkezéshez.
  - Letiltva: A webes hitelesítőadat-szolgáltató le van tiltva a bejelentkezéshez.

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Előnyben részesített Azure ad-bérlői tartomány**: Adjon meg egy meglévő tartománynevet az Azure AD-szervezetben. Ha a tartomány felhasználói bejelentkeznek, nem kell beírniuk a tartománynevet. Például írja be a következőt: `contoso.com`. A `contoso.com` tartományban lévő felhasználók bejelentkezhetnek a felhasználó nevével, `abby`például a `abby@contoso.com`helyett.

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="per-app-privacy-exceptions"></a>Alkalmazásonkénti adatvédelmi kivételek

Olyan alkalmazásokat adhat hozzá, amelyeknek az "alapértelmezett adatvédelem" beállítástól eltérő adatvédelmi viselkedéssel kell rendelkeznie.

- **Csomag neve**: Alkalmazáscsomag-család neve.
- **Alkalmazás neve**: Az alkalmazás neve.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: Annak megadása, hogy az alkalmazás elérheti-e a felhasználónevet, a képet és az egyéb kapcsolattartási adatokat.
- **Háttérben futó alkalmazások**: Annak megadása, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: Annak megadása, hogy az alkalmazás elérheti-e a naptárat.
- **Meghívási előzmények**: Annak megadása, hogy az alkalmazás hozzáférhet-e a hívási előzményekhez.
- **Kamera**: Annak megadása, hogy az alkalmazás elérheti-e a kamerát.
- **Névjegyek**: Annak megadása, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **E-mail cím**: Annak megadása, hogy az alkalmazás hozzáférhessen-e e-mailekhez, és küldje el.
- **Hely**: Annak megadása, hogy az alkalmazás hozzáférhet-e a hely adataihoz.
- **Üzenetküldés**: Azt határozza meg, hogy az alkalmazás képes-e szöveges vagy MMS-üzenetek olvasására vagy elküldésére.
- **Mikrofon**: Annak megadása, hogy az alkalmazás használhatja-e a mikrofont.
- **Mozgás**: Annak megadása, hogy az alkalmazás hozzáférhet-e az eszköz mozgási adataihoz.
- **Értesítések**: Annak megadása, hogy az alkalmazás hozzáférhet-e az értesítésekhez.
- **Telefon**: Annak megadása, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Rádiók**: Egyes alkalmazások rádiókat (például Bluetooth) használnak az eszközön az eszközök küldéséhez és fogadásához, valamint a rádiók be-és kikapcsolásához. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: Annak megadása, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: Válassza ki, hogy az alkalmazás használhat-e megbízható eszközöket. A megbízható eszközök a már csatlakoztatott hardverek vagy az eszközhöz tartozó hardverek. Használjon például TV-ket, kivetítőket és így tovább, mint a megbízható eszközök.
- **Visszajelzés és diagnosztika**: Annak megadása, hogy az alkalmazás hozzáférhet-e a diagnosztikai adatokhoz.
- **Szinkronizálás eszközökkel**: Válassza ki, hogy az alkalmazás képes-e automatikusan megosztani és szinkronizálni az adatokat olyan vezeték nélküli eszközökkel, amelyek nem kifejezetten párosítva vannak az eszközzel.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="personalization"></a>Személyre szabás

Ezek a beállítások a [megszemélyesítési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Asztali háttérkép URL-címe (csak asztali verzió)** : Adja meg egy. jpg,. jpeg vagy. png formátumú kép URL-címét, amelyet a Windows asztali háttérképként kíván használni. A felhasználók nem módosíthatják a képet. Például írja be a következőt: `https://contoso.com/logo.png`.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="printer"></a>Nyomtató

- **Nyomtatók**: A hozzáadott helyi nyomtatók listája.
- **Alapértelmezett nyomtató**: Állítsa be az alapértelmezett nyomtatót.
- **Felhasználói hozzáférés új nyomtatók hozzáadásához**: Helyi nyomtatók használatának engedélyezése vagy letiltása.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="privacy"></a>Személyes adatok védelme

Ezek a beállítások az [adatvédelmi házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Bevitel személyre szabása**: A **Letiltás** megakadályozza a hang használatát a diktáláshoz, valamint a Cortana és más, a Microsoft felhőalapú beszédfelismerést használó alkalmazásokkal való kommunikációhoz. A szolgáltatás le van tiltva, és a felhasználók a beállítások használatával nem engedélyezhetik online beszédfelismerést. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a választást. Ha engedélyezi ezeket a szolgáltatásokat, a Microsoft hangadatokat gyűjthet a szolgáltatás fejlesztéséhez.
- **A párosítási és adatvédelmi felhasználói beleegyezési kérések automatikus elfogadása**: Válassza az **Engedélyezés lehetőséget** , hogy a Windows automatikusan fogadja a párosítási és adatvédelmi engedélyekkel kapcsolatos üzeneteket az alkalmazások futtatásakor. **Nincs konfigurálva** (alapértelmezés) megakadályozza a párosítási és adatvédelmi felhasználói beleegyezési ablak automatikus elfogadását az alkalmazások megnyitásakor.
- **Felhasználói tevékenységek közzététele**: A **blokk** megakadályozza a tevékenységek hírcsatornájában a közelmúltban használt erőforrások közös használatát és felderítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót, így az alkalmazások közzétehetik a végfelhasználói tevékenységeket.
- **Csak helyi tevékenységek**: A **blokk** megakadályozza, hogy a feladat-átkapcsolásban csak a helyi tevékenységen alapuló megosztott és a legutóbb használt erőforrások felderítése legyen elérhető. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.

Beállíthatja, hogy az eszközön található összes alkalmazás hozzáférhessen. A kivételeket az alkalmazáson belüli **adatvédelmi kivételek**használatával is meghatározhatja az alkalmazások alapján.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: Annak megadása, hogy az alkalmazás elérheti-e a felhasználónevet, a képet és az egyéb kapcsolattartási adatokat.
- **Háttérben futó alkalmazások**: Annak megadása, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: Annak megadása, hogy az alkalmazás elérheti-e a naptárat.
- **Meghívási előzmények**: Annak megadása, hogy az alkalmazás hozzáférhet-e a hívási előzményekhez.
- **Kamera**: Annak megadása, hogy az alkalmazás elérheti-e a kamerát.
- **Névjegyek**: Annak megadása, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **E-mail cím**: Annak megadása, hogy az alkalmazás hozzáférhessen-e e-mailekhez, és küldje el.
- **Hely**: Annak megadása, hogy az alkalmazás hozzáférhet-e a hely adataihoz.
- **Üzenetküldés**: Azt határozza meg, hogy az alkalmazás képes-e szöveges vagy MMS-üzenetek olvasására vagy elküldésére.
- **Mikrofon**: Annak megadása, hogy az alkalmazás használhatja-e a mikrofont.
- **Mozgás**: Annak megadása, hogy az alkalmazás hozzáférhet-e az eszköz mozgási adataihoz.
- **Értesítések**: Annak megadása, hogy az alkalmazás hozzáférhet-e az értesítésekhez.
- **Telefon**: Annak megadása, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Rádiók**: Egyes alkalmazások rádiókat (például Bluetooth) használnak az eszközön az eszközök küldéséhez és fogadásához, valamint a rádiók be-és kikapcsolásához. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: Annak megadása, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: Válassza ki, hogy az alkalmazás használhat-e megbízható eszközöket. A megbízható eszközök a már csatlakoztatott hardverek vagy az eszközhöz tartozó hardverek. Használjon például TV-ket, kivetítőket és így tovább, mint a megbízható eszközök.
- **Visszajelzés és diagnosztika**: Válassza ki, hogy az alkalmazás képes-e a diagnosztikai adatok elérésére.
- **Szinkronizálás eszközökkel** – Megadhatja, hogy az alkalmazás oszthat-e meg és szinkronizálhat-e adatokat automatikusan olyan vezeték nélküli eszközökkel, amelyek nincsenek kifejezetten párosítva az adott PC-vel, táblagéppel vagy telefonnal.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="projection"></a>Kivetítés

Ezek a beállítások a [WirelessDisplay házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Felhasználói bevitel vezeték nélküli kijelzők fogadói**: A **Letiltás** megakadályozza a felhasználók vezeték nélküli megjelenítési fogadók általi bevitelét. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a vezeték nélküli kijelző billentyűzetet, egeret, tollat és érintéses bevitelt küldjön a forrás eszközre.
- **Kivetítés erre a számítógépre**: A **Letiltás** megakadályozza, hogy más eszközök megtalálják az eszközt a kivetítéshez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz felderíthető legyen, és képes legyen a projekt a zárolási képernyő feletti eszközre.
- **PIN-kód kérése a párosításhoz**: Válassza a **kötelező** lehetőséget a kivetítési eszközhöz való csatlakozáskor a PIN-kód megadásához. **Nincs konfigurálva** (az alapértelmezett) nem igényel PIN-kódot az eszköz kivetítési eszközhöz való párosításához.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="reporting-and-telemetry"></a>Jelentéskészítés és telemetria

- **Használati adatok megosztása**: Válassza ki az elküldött diagnosztikai adatmennyiséget. A választható lehetőségek:
  - **Nincs konfigurálva**: Nincsenek megosztott adathalmazok.
  - **Biztonság**: A Windows biztonságosabbá tételéhez szükséges információk, beleértve a csatlakoztatott felhasználói élményre és telemetria, valamint a kártevő szoftvereket eltávolító eszközre és a Windows Defenderre vonatkozó adatokat.
  - Alapszintű: Alapszintű eszköz adatai, beleértve a minőségi adatokat, az alkalmazások kompatibilitását, az alkalmazások használati adatait és a biztonsági szintről származó adatokat.
  - **Bővített**: További elemzések, többek között a következők: hogyan használják a Windows, a Windows Server, a System Center és az alkalmazásokat, hogyan hajtják végre, a speciális megbízhatósági adatok, valamint az adatok mind az alapszintű, mind a biztonsági szinten.
  - **Teljes**: A problémák azonosításához és javításához szükséges összes adat, valamint a biztonsági, alapszintű és továbbfejlesztett szintekből származó adatok.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Microsoft Edge-böngészési adatgyűjtés küldése Microsoft 365 Analyticsnek**: A szolgáltatás használatához állítsa a **használati adatok megosztása** beállítást a **bővített** vagy a **teljes**értékre. Ez a szolgáltatás azt szabályozza, hogy a Microsoft Edge milyen adatokat küldjön a vállalati eszközök Microsoft 365 elemzéséhez egy konfigurált kereskedelmi AZONOSÍTÓval. A választható lehetőségek:
  - **Nincs konfigurálva**: Az operációs rendszer alapértelmezett értékének használata, amely nem küldi el a böngészési előzményeket.
  - **Csak intranetes adatküldési szolgáltatás**: Lehetővé teszi a rendszergazda számára az intranetes adatelőzmények küldését
  - **Csak az internetes**adatküldés: Lehetővé teszi a rendszergazda számára az internetes adatelőzmények küldését
  - **Intranetes és internetes**adatküldés: Lehetővé teszi a rendszergazda számára az intranetes és az internetes adatelőzmények küldését

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Telemetria proxykiszolgáló**: Adja meg egy proxykiszolgáló teljes tartománynevét (FQDN) vagy IP-címét a csatlakoztatott felhasználói élmények és telemetria-kérések továbbításához SSL (SSL) kapcsolat használatával. a következő formátumban: *kiszolgáló*:*port*. Ha a nevesített proxy nem sikerül, vagy ha a házirend engedélyezésekor nem adta meg a proxyt, a rendszer nem küldi el a csatlakoztatott felhasználói élményt és telemetria, és a helyi eszközön marad.

  Példák a formátumra:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="search"></a>Keresés

Ezek a beállítások a [keresési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)-t használják, amely a támogatott Windows-kiadásokat is felsorolja. 

- **Biztonságos Keresés (csak mobil)** : Annak szabályozása, hogy a Cortana hogyan szűri a felnőtt tartalmat a keresési eredmények között. A választható lehetőségek:
  - **Felhasználó által definiált**: Saját beállítások kiválasztásának engedélyezése a végfelhasználók számára.
  - **Szigorú**: A felnőtt tartalmak legmagasabb szintű szűrése.
  - **Mérsékelt**: Mérsékelt szűrés a felnőtt tartalommal szemben. Az érvényes keresési eredmények nem szűrhetők.
- **Webes találatok megjelenítése a keresésben**: Ha a **blokkolás**értékre van állítva, a felhasználók nem kereshetnek, és a webes találatok nem jelennek meg a keresésben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a webes keresést, és az eredmények megjelennek az eszközön.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="start"></a>Start

Ezek a beállítások a [Start Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.  

- **Start menü elrendezése**: Felülbírálja az alapértelmezett indítási elrendezést, és testreszabhatja a Start menüt az asztali eszközökön. Töltsön fel egy XML-fájlt, amely tartalmazza a testreszabásokat, beleértve az alkalmazások listájának sorrendjét és egyebeket. A felhasználók nem változtathatják meg a Start menü megadott elrendezését.
- **Webhelyek rögzítése a Start menüben**: Képek importálása a Microsoft Edge-ből, amelyek hivatkozásként jelennek meg a Windows Start menüjében asztali eszközökhöz.
- **Alkalmazások feloldja a tálcán**: A **Letiltás** megakadályozza, hogy a felhasználók kioldják az alkalmazásokat a tálcáról. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók kibontsák az alkalmazásokat a tálcáról.
- **Gyors**felhasználóváltás: A **Letiltás** megakadályozza a bejelentkezett felhasználók közötti váltást a kijelentkezés nélkül. **Nincs konfigurálva** (alapértelmezés) megjeleníti a felhasználói csempén a **kapcsoló felhasználóját** .
- **Leggyakrabban használt alkalmazások**: A **blokk** elrejti a leggyakrabban használt alkalmazásokat a Start menüben. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezés) a leggyakrabban használt alkalmazásokat jeleníti meg.
- **Nemrég hozzáadott alkalmazások**: A **blokk** elrejti a nemrég hozzáadott alkalmazásokat a Start menüben. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezés) megjeleníti a legutóbb hozzáadott alkalmazásokat a Start menüben.
- **Kezdőképernyő mód**: Válassza ki a kezdőképernyő megjelenítésének módját. A választható lehetőségek:
  - **Felhasználó által definiált**: Nem kényszeríti az indítás méretét. A felhasználók megadhatják a méretet.
  - **Teljes képernyő**: Az indítás teljes képernyős méretének kényszerítése.
  - **Nem teljes képernyő**: Az indítás nem teljes képernyős méretének kényszerítése.
- **A legutóbb megnyitott elemek a Jump List menükben**: A legutóbbi Jump List menük elrejtése a Start menüben és a tálcán. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezés) megjeleníti a legutóbb megnyitott elemeket a jumplists-ben.
- **Alkalmazások listája**: Válassza ki, hogyan jelenjenek meg az összes alkalmazás listája. A választható lehetőségek:
  - **Felhasználó által definiált**: Nincs kényszerített beállítás. A felhasználók kiválaszthatják, hogyan jelenjenek meg az alkalmazások listája az eszközön.
  - **Összecsukás**: Az összes alkalmazás listájának elrejtése
  - **A beállítások alkalmazás összecsukása és letiltása**: Az összes alkalmazás listájának elrejtése és a beállítások alkalmazás **Start menüjében szereplő alkalmazások listájának** letiltása.
  - **Eltávolítja és letiltja a beállítások alkalmazást**: Az alkalmazások listájának elrejtése, az összes alkalmazás eltávolítása gomb és az alkalmazások listájának letiltása a **Start menüben** a beállítások alkalmazásban.
- **Főkapcsoló gomb**: A **Letiltás** elrejti a főkapcsoló gombot a Start menüben. **Nincs konfigurálva** (alapértelmezés) megjeleníti a főkapcsoló gombot.
- **Felhasználói csempe**: A **blokk** elrejti a felhasználói csempét a Start menüben. **Nincs konfigurálva** (alapértelmezés) megjeleníti a felhasználói csempét, és beállítja a következő beállításokat is:
  - **Zárolás**: A **Letiltás** elrejti a **zárolási** lehetőséget a Start menü felhasználói csempén. **Nincs konfigurálva** (alapértelmezés) megjeleníti a **zárolási** beállítást.
  - **Kijelentkezés**: A **Letiltás** elrejti a kijelentkezési lehetőséget a Start menü felhasználói csempéje alatt. **Nincs konfigurálva** (alapértelmezés) megjeleníti a kijelentkezési lehetőséget.
- **Leállítás**: A **Letiltás** elrejti a **frissítést, és** leállítja és **leállítja** a beállításokat a Start menü főkapcsoló gombján. **Nincs konfigurálva** (alapértelmezés) ezeket a beállításokat jeleníti meg.
- **Alvó állapot**: Az **alvó állapot** elrejtésének **letiltása** a Start menü főkapcsoló gombján látható. **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Hibernálás**: **Letiltja** a **hibernálás** beállítás elrejtését a Start menü főkapcsoló gombján. **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Fiók váltása**: A **blokk** elrejti a **kapcsoló fiókját** , amely a Start menü felhasználói csempéjét mutatja. **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Újraindítási beállítások**:  **Blokkolja** a Start menü főkapcsoló gombján a **frissítés és újraindítás** és **Újraindítás** beállítások elrejtését. **Nincs konfigurálva** (alapértelmezés) ezeket a beállításokat jeleníti meg.
- **Dokumentumok a Start menüben**: A dokumentumok mappa elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Letöltések a Start menüben**: A letöltések mappa elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Fájlkezelő a Start menüben**: A Windows Start menüjében található fájlkezelő elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Otthoni csoport a Start menüben**: Az otthoni csoport parancsikonjának elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Zene a Start menüben**: A zene mappa elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Hálózat a Start menüben**: Bejövő hálózati forgalom elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Személyes mappa a Start menüben**: Személyes mappa elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Képek a Start menüben**: A Windows Start menüjében található képek mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Beállítások a Start menüben**: A beállítások parancsikon elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.
- **Videók a Start menüben**: A videók mappájának elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs kényszerített beállítás. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: A parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: Megjelenik a parancsikon, és letiltja a beállítást a beállítások alkalmazásban.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen a Microsoft Edge-hez**: A **kötelező** kikapcsolja a Windows Defender SmartScreen szolgáltatást, és megakadályozza, hogy a felhasználók bekapcsolják azt. **Nincs konfigurálva** (alapértelmezés) bekapcsolja a SmartScreen szolgáltatást. Segít megvédeni a felhasználókat az esetleges fenyegetésektől, és megakadályozhatja a felhasználók számára a kikapcsolást.

  A Microsoft Edge a Windows Defender SmartScreen (bekapcsolva) használatával gondoskodik a felhasználók számára a lehetséges adatlopó csalások és a kártevő szoftverek elleni védelemről.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Rosszindulatú hely elérése**: A **Letiltás** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Windows Defender SmartScreen szűrő figyelmeztetéseit, és blokkolja azokat a helyre. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók figyelmen kívül hagyják a figyelmeztetéseket, és folytassa a webhelyet.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- Nem **ellenőrzött fájlok letöltése**: A **Letiltás** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Windows Defender SmartScreen szűrő figyelmeztetéseit, és blokkolja a nem ellenőrzött fájlok letöltését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók figyelmen kívül hagyják a figyelmeztetéseket, és folytatják a nem ellenőrzött fájlok letöltését.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-spotlight"></a>Windows Reflektorfény

Ezek a beállítások az [Experience Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Windows reflektorfény**: A **Letiltás** kikapcsolja a Windows reflektorfényt a zárolási képernyőn, a Windows-tippeken, a Microsoft fogyasztói szolgáltatásain és egyéb kapcsolódó funkciókon. Ha a cél az, hogy csökkentse a hálózati forgalmat az eszközökről,állítsa ezt a blokkra. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows reflektorfény funkcióinak használatát, és a végfelhasználók is vezérelhetik. Ha engedélyezve van, a következő beállításokat is engedélyezheti vagy letilthatja:

  - **Windows reflektorfény a zárolási képernyőn**: A **Letiltás** megakadályozza a Windows reflektorfényben az eszköz zárolási képernyőjén található információk megjelenítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
  - **Harmadik féltől származó javaslatok a Windows reflektorfényben**: A **Letiltás** megakadályozza, hogy a Windows reflektorfény ne a Microsoft által közzétett tartalmat javasoljon. **Nincs konfigurálva** az (alapértelmezett) lehetővé teszi az alkalmazások és tartalmak a partner szoftvergyártók számára való használatát a Windows reflektorfényben, például a zárolási képernyő Spotlight, a javasolt alkalmazások a Start menüben és a Windows-tippek.
  - **Fogyasztói funkciók**: A **Block** kikapcsolja a jellemzően csak a fogyasztóknak szóló tapasztalatokat, például az indítási javaslatokat, a tagsági értesítéseket, az alkalmazások telepítés utáni telepítését és a csempék átirányítását. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.
  - **Windows-tippek**: A **Letiltás** letiltja a Windows-előugró ablakokra vonatkozó tippeket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows-tippek megjelenítését.
  - **Windows reflektorfény a műveleti központban**: A **blokk** megakadályozza a Windows reflektorfény értesítéseinek megjelenítését a műveleti központban. **Nincs konfigurálva** (alapértelmezés) a műveleti központban olyan értesítéseket jeleníthet meg, amelyek az alkalmazásokat és szolgáltatásokat javasolva segítik a felhasználókat a Windowsban.
  - **Windows reflektorfény személyre szabása**: A **Letiltás** megakadályozza, hogy a Windows a diagnosztikai adatok használatával testreszabott felhasználói élményt nyújtson. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a Microsoft diagnosztikai információkkal lássa el személyre szabott javaslatokat, tippeket és ajánlatokat a Windows személyre szabásához a felhasználó igényei szerint.
  - **Windows üdvözlőprogram-élmény**: A **Letiltás** kikapcsolja a Windows reflektorfény Windows üdvözlőprogramjának funkcióját. A Windows üdvözlőprogramja nem jelenik meg, ha a Windows és az alkalmazásai frissítései és változásai vannak. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows üdvözlőprogram használatát, amely az új vagy frissített funkciókkal kapcsolatos felhasználói adatokat jeleníti meg.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-defender-antivirus"></a>Windows Defender víruskereső

Ezek a beállítások a [Defender Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Valós idejű figyelés**: Az **Engedélyezés** beállítás meggátolja a kártevők, kémprogramok és más nemkívánatos szoftverek valós idejű vizsgálatát. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Viselkedés figyelése**: Az **Engedélyezés** beállítás megadásával megakadályozható, hogy a Defender gyanús tevékenységekre utaló ismert mintákat keressen az eszközökön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows Defender viselkedésének figyelését.
- **Hálózatvizsgáló rendszer (NIS)** : A NIS segítségével megvédheti az eszközöket a hálózati alapú biztonsági rések ellen. A Microsoft Endpoint Protection-központból származó ismert sebezhető pontok mintázatai alapján segít észlelni és blokkolni a rosszindulatú hálózati forgalmat.
- **Az összes Letöltés ellenőrzése**: Meghatározza, hogy a Defender az internetről letöltött összes fájlt megvizsgálja-e.
- **A Microsoft webböngészőkben betöltött parancsfájlok vizsgálata**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Defender számára az Internet Explorerben használt parancsfájlok vizsgálatát. Az **Engedélyezés** megakadályozza a vizsgálat megkeresését.
- **Végfelhasználói hozzáférés a defenderhez**: A **blokk** elrejti a Windows Defender felhasználói felületét a végfelhasználók számára. A Windows Defender összes értesítése is le van tiltva. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználói hozzáférést a Windows Defender felhasználói felületéhez. Módosítás esetén a beállítás a felhasználó számítógépének következő újraindításakor lép érvénybe.
- **Aláírás-frissítési időköz (óra)** : Adja meg azt az időközt, amellyel a Defender az új aláírási fájlokat ellenőrzi 0-24-ból. A választható lehetőségek:

  - **Nincs konfigurálva** alapértelmezett
  - Ne legyen bejelölve: A Defender nem keres új aláírási fájlokat.
  - **1-24**: `1` minden órában ellenőrzi, `2` ellenőrzi a két óránként `24` , naponta ellenőrzi, és így tovább.
- **Fájl-és program-tevékenység figyelése**: Engedélyezi a Defender számára az eszközökön zajló a fájl- és programtevékenységet.
- **Karanténba helyezett kártevők törlése előtti napok**: Továbbra is nyomon követheti a megoldott kártevő szoftvereket a megadott számú napon, így manuálisan is megtekintheti a korábban érintett eszközöket. Ha a napok számát **0-ra**állítja, a kártevő a karantén mappában marad, és a rendszer nem távolítja el automatikusan. Ha a értékre van állítva, a rendszer 90 napig tárolja a karanténba helyezett elemeket, majd eltávolítja azt `90`.
- **CPU-használati korlát a vizsgálat során**: Korlátozza a megvizsgálható PROCESSZORok mennyiségét **1** és **100**között.
- **Archív fájlok vizsgálata**: Az **Engedélyezés** megakadályozza a Defender számára az archivált fájlok, például a zip-vagy a cab-fájlok vizsgálatát. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a keresést.
- **Bejövő üzenetek ellenőrzése**: Az **Engedélyezés** lehetővé teszi, hogy a Defender az eszközre érkező e-maileket vizsgálja. **Nincs konfigurálva** (alapértelmezés) megakadályozza az e-mailek vizsgálatát.
- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**: Az **Engedélyezés** beállítás meggátolja a cserélhető meghajtók teljes vizsgálatát. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Defender számára a cserélhető meghajtók, például az USB-stickek vizsgálatát.
- **Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat során**: Az **Engedélyezés** lehetővé teszi a Defender számára a csatlakoztatott hálózati meghajtókon lévő fájlok vizsgálatát. **Nincs konfigurálva** (alapértelmezés) megakadályozza a teljes vizsgálatot. Ha a meghajtón található fájlok írásvédettek, a Defender nem tudja eltávolítani a bennük talált kártevőket.
- **Hálózati mappákból megnyitott fájlok vizsgálata**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Defender számára a megosztott hálózati meghajtókon lévő fájlok, például az UNC elérési útról elérhető fájlok vizsgálatát. Az **Engedélyezés** megakadályozza a vizsgálat megkeresését. Ha a meghajtón található fájlok írásvédettek, a Defender nem tudja eltávolítani a bennük talált kártevőket.
- **Felhőbeli védelem**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az Microsoft Active Protection Service adatokat kapjon a kezelt eszközökről származó kártevők tevékenységéről. Letiltja a funkciót.
- A felhasználók megkérdezése a **minta beküldése előtt**: Azt szabályozza, hogy a rendszer automatikusan elküldje-e a Microsoftnak a további elemzést igénylő potenciálisan kártékony fájlokat. A választható lehetőségek:
  - **Nincs konfigurálva**
  - **Mindig legyen kérdés**
  - **Rákérdezés a személyes adatok elküldése előtt**
  - **Soha ne küldjön adatküldést**
  - **Az összes üzenet küldése a kérés nélkül**: Az adatküldés automatikusan történik

- **A napi gyors vizsgálat elvégzésének ideje**: Válassza ki az órát a napi gyors vizsgálat futtatásához. A **nem konfigurált** napi vizsgálat nem fut. Ha további testreszabásra van szüksége, konfigurálja a **Rendszervizsgálat típusát** a beállítás elvégzéséhez.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **A végrehajtandó rendszervizsgálat típusa**: Rendszervizsgálatot ütemezhet, beleértve a vizsgálat szintjét, valamint az ellenőrzés futtatásának napját és időpontját. A választható lehetőségek:
  - **Nincs konfigurálva**: Nem ütemezhet rendszervizsgálatot az eszközön. A végfelhasználók szükség szerint manuálisan futtathatják a vizsgálatokat, vagy az eszközeiket szeretnék.
  - **Letiltás**: Letiltja az eszközön a rendszer vizsgálatát. Akkor válassza ezt a lehetőséget, ha olyan partner víruskereső megoldást használ, amely az eszközöket vizsgálja.
  - **Gyors vizsgálat**: Olyan gyakori helyekre hasonlít, ahol a kártevők regisztrálva lehetnek, például a beállításkulcsok és az ismert Windows-indítási mappák.
    - **Ütemezett nap**: Válassza ki a napot a vizsgálat futtatásához.
    - **Ütemezett időpont**: Válassza ki az órát a vizsgálat futtatásához.
  - **Teljes vizsgálat**: Megtekinti azokat a közös helyeket, amelyeken kártevők regisztrálhatók, valamint az eszköz összes fájlját és mappáját is megvizsgálja.
    - **Ütemezett nap**: Válassza ki a napot a vizsgálat futtatásához.
    - **Ütemezett időpont**: Válassza ki az órát a vizsgálat futtatásához.

  Ez a beállítás ütközhet a **napi gyors vizsgálati** beállítások végrehajtásához szükséges idővel. Néhány javaslat:

  - Napi gyors vizsgálat futtatásához állítsa be az **időt a napi gyors vizsgálati** beállítás végrehajtásához.
  - Napi gyors vizsgálat és teljes ellenőrzés futtatása hetente, majd az **idő beállítása napi gyors vizsgálat végrehajtásához**. A **Rendszervizsgálat típusának** beállítása a teljes vizsgálathoz a nap és az idő alapján.
  - Ne konfigurálja az időt a gyors vizsgálathoz beállított rendszervizsgálati **típussal** egyidejűleg a **napi gyors vizsgálat végrehajtásához** . Ezek a beállítások ütközést okozhatnak, és előfordulhat, hogy a vizsgálat nem fut.
  - Ha keddenként szeretne gyors vizsgálatot futtatni, konfigurálja a **Rendszervizsgálat típusát** a beállítás elvégzéséhez.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Vélhetően nemkívánatos alkalmazások észlelése**: Válassza ki a védelmi szintet, ha a Windows vélhetően nemkívánatos alkalmazásokat észlel. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A Windows Defender vélhetően nemkívánatos alkalmazások elleni védelme le van tiltva.
  - **Letiltás**: A Windows Defender észleli a vélhetően nemkívánatos alkalmazásokat, és a rendszer letiltja az észlelt elemeket. Ezek az elemek az előzményekben más fenyegetésekkel együtt jelennek meg.
  - **Naplózás**: A Windows Defender észleli a vélhetően nemkívánatos alkalmazásokat, de nem igényel műveletet. Áttekintheti a Windows Defender által az alkalmazásokkal kapcsolatos információkat. Keressen például a Windows Defender által a Eseménynaplóban létrehozott eseményeket.

  A vélhetően nemkívánatos alkalmazásokról további információt a vélhetően [nemkívánatos alkalmazások észlelése és blokkolása](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)című témakörben talál.

- **Észlelt kártevő-fenyegetésekkel kapcsolatos műveletek**: Válassza ki azokat a műveleteket, amelyeket a Defender az észlelt veszélyforrások szintjén elvégez: alacsony, közepes, magas és súlyos. Ha ez nem lehetséges, a Windows Defender a legjobb lehetőséget választja a fenyegetés szervizelésének biztosítására. A választható lehetőségek:
  - **Tisztítás**
  - **Karantén**
  - **Eltávolítás**
  - **Engedélyezés**
  - **Felhasználó által definiált**
  - **Tiltás**

Válassza ki **OK** a módosítások mentéséhez.

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender víruskereső – kizárások

- A vizsgálatokból **és a valós idejű védelemből kizárandó fájlok és mappák**: A kívánt fájlok és mappák – például **C:\Elérési_út** vagy **%ProgramFiles%\Elérési_út\fájlnév.exe** – felvétele a kivételek listájára. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a fájlokat és mappákat.
- A vizsgálatokból **és a valós idejű védelemből kizárandó**fájlkiterjesztések: Vegye fel a kívánt fájlkiterjesztéseket – például **jpg** vagy **txt** – a kivételek listájára. Az ilyen kiterjesztésű fájlok nem szerepelnek a valós idejű vagy ütemezett vizsgálatok során.
- A vizsgálatokból **és a valós idejű védelemből kizárandó folyamatok**: Vegye fel a kívánt típusú folyamatokat – **.exe**, **.com** vagy **.scr** – a kivételek listájára. Ezek a folyamatok nem tartoznak valós idejű vagy ütemezett vizsgálatokba.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="next-steps"></a>További lépések

További technikai részleteket az egyes beállításokról és a Windows támogatott kiadásairól a [Windows 10 szabályzatkonfigurációs szolgáltatói referenciájában](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) talál.
