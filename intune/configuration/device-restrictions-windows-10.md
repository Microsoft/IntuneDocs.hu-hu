---
title: Eszközkorlátozási beállítások Windows 10 rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Tekintse meg az összes beállítás listáját, valamint a Windows 10 és újabb rendszerű eszközökön az eszközök korlátozásának létrehozásához szükséges leírást. Ezekkel a beállításokkal konfigurálhatja a képernyőképeket, a jelszavakra vonatkozó követelményeket, a kioszk beállításait, az áruházbeli alkalmazásokat, a Microsoft Edge böngészőt, a Microsoft Defendert, a felhőhöz való hozzáférést, a Start menüt és egyebeket Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fb025e6b698eba3deeabbda788fcd990a19105f
ms.sourcegitcommit: b752acefec077c719e169e665c955adb944e85c6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781175"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows 10 (és újabb) eszközbeállítások az Intune-t használó szolgáltatások engedélyezéséhez vagy korlátozásához

Ez a cikk felsorolja és leírja a Windows 10 és újabb rendszerű eszközökön szabályozható különböző beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, testreszabhatja a zárolási képernyőt, és használhatja a Microsoft Defendert.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a Windows 10-es eszközökhöz vannak rendelve vagy telepítve.

> [!Note]
> Nem minden beállítás érhető el a Windows összes kiadásában. A támogatott kiadások megtekintéséhez tekintse meg a [házirend-kriptográfiai](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (másik Microsoft-webhely megnyitása) című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Alkalmazásáruház

Ezek a beállítások a [ApplicationManagement házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **App Store** (csak mobil): **nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára az alkalmazás-áruház elérését a mobileszközökön. **Letiltja** az alkalmazás-áruház használatát.
- Az **áruházból származó alkalmazások automatikus frissítése**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a rendszer automatikusan frissítse az alkalmazásokat a Microsoft Storeról. A **Letiltás** megakadályozza a frissítések automatikus telepítését.
- **Megbízható alkalmazás telepítése**: válassza ki, hogy a nem Microsoft Store alkalmazásokat lehet-e telepíteni, más néven közvetlen telepítési. A közvetlen telepítési telepíti, majd futtatja vagy teszteli az Microsoft Store által nem tanúsított alkalmazást. Például egy olyan alkalmazás, amely csak a vállalaton belül található. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): az operációs rendszer alapértelmezését használja.
  - **Letiltás**: megakadályozza a közvetlen telepítési. Nem Microsoft Store alkalmazások nem telepíthetők.
  - **Engedélyezés**: engedélyezi a közvetlen telepítési. Nem Microsoft Store alkalmazások is telepíthetők.
- **Fejlesztői zárolás feloldása**: engedélyezi a Windows fejlesztői beállításait, például lehetővé teszi a közvetlenül telepített alkalmazások módosítását a végfelhasználók számára. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): az operációs rendszer alapértelmezését használja.
  - **Letiltás**: meggátolja a fejlesztői üzemmódot és a közvetlen telepítési alkalmazásokat.
  - **Engedélyezés**: lehetővé teszi a fejlesztői üzemmód és a közvetlen telepítési alkalmazások használatát.

  Az [eszköz fejlesztésének engedélyezése](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) további információt tartalmaz a szolgáltatással kapcsolatban.

- **Megosztott felhasználói alkalmazásadatok**: válassza az **Engedélyezés lehetőséget** az alkalmazásadatok különböző felhasználók közötti megosztásához ugyanazon az eszközön és az alkalmazás más példányai között. **Nincs konfigurálva** (az alapértelmezett) megakadályozza az adatmegosztást más felhasználókkal és ugyanazon alkalmazás más példányaival.
- **Csak privát áruház használata**: **az** alkalmazások csak privát áruházból tölthetők le, és nem tölthetők le a nyilvános áruházból, beleértve a kiskereskedelmi katalógust is. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások letöltését egy privát áruházból és egy nyilvános áruházból.
- **Áruházból származó alkalmazások indítása**: a **Letiltás** letiltja az eszközön előre telepített vagy a Microsoft Store letöltött összes alkalmazást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások megnyitását.
- **Alkalmazásadatok telepítése a rendszerköteten**: a **blokk** leállítja az alkalmazások adattárolását az eszköz rendszerkötetén. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások számára a rendszerlemez kötetén tárolt adattárolást.
- **Alkalmazások telepítése a rendszermeghajtón**: a **Letiltás** megakadályozza, hogy az alkalmazások a rendszermeghajtón telepítsenek az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazások telepítését a rendszermeghajtón.
- **Játék DVR** (csak asztali verzió): a **Letiltás** letiltja a Windows-játékok rögzítését és a szórást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a játékok rögzítését és közvetítését.
- **Csak áruházbeli alkalmazások**: Ez a beállítás határozza meg azt a felhasználói élményt, amikor a felhasználók a Microsoft Storetól eltérő helyekről telepítik az alkalmazásokat. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): lehetővé teszi, hogy a végfelhasználók alkalmazásokat telepítsenek a Microsoft Storetól eltérő helyekről, beleértve a más házirend-beállításokban definiált alkalmazásokat is.  
  - **Bárhol**: kikapcsolja az alkalmazások javaslatait, és lehetővé teszi, hogy a felhasználók tetszőleges helyről telepítsenek alkalmazásokat.  
  - **Csak tárolás**: kényszeríti a végfelhasználókat, hogy csak az Microsoft Store telepítsenek alkalmazásokat.
  - **Javaslatok**: ha a Microsoft Storeban elérhető webről telepít egy alkalmazást, a felhasználók egy, az áruházból letöltött üzenetet látnak.  
  - **Előnyben részesített tároló**: figyelmezteti a felhasználókat, ha a Microsoft Storetól eltérő helyekről telepítik az alkalmazásokat.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Felhasználói vezérlés a telepítésekben**: Ha **nincs konfigurálva** (alapértelmezett), Windows Installer megakadályozhatja, hogy a felhasználók a rendszergazdák számára fenntartott telepítési beállításokat módosíthassák, például a fájlok telepítéséhez a címtárat. A **Letiltás** lehetővé teszi a felhasználók számára, hogy megváltoztassák ezeket a telepítési beállításokat, és néhány Windows Installer biztonsági funkciót kihagynak.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Alkalmazások telepítése emelt szintű jogosultságokkal**: Ha a **nincs konfigurálva** értékre van állítva, a rendszer az aktuális felhasználó engedélyeit alkalmazza, amikor olyan programokat telepít, amelyeket a rendszergazda nem telepít vagy biztosít. Ha a rendszerre telepít bármely programot, a **letiltja** a Windows Installert a emelt szintű engedélyek használatára. Ezek a jogosultságok minden programra kiterjeszthetők.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Indítási alkalmazások**: Itt adhatja meg, hogy mely alkalmazások számára kell megnyílni, miután egy felhasználó bejelentkezik az eszközre. Ügyeljen arra, hogy a Windows-alkalmazások PFN-neveinek pontosvesszővel tagolt listáját használja. Ahhoz, hogy ez a szabályzat működjön, a Windows-alkalmazásokban a jegyzékfájlnak indítási feladatot kell használnia.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

Ezek a beállítások a [kapcsolódási házirendet](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) és a [Wi-Fi házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) -kriptográfiai szolgáltatókat használják, amelyek a támogatott Windows-kiadásokat is felsorolják.

- [Wi-Fi házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Mobil adatcsatorna**: válassza ki, hogy a végfelhasználók használhatnak-e olyan adatforrásokat, mint például a webes böngészés, ha a hálózathoz csatlakozik. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): az operációs rendszer alapértelmezését használja, ami engedélyezheti a mobil adatcsatornát. A végfelhasználók kikapcsolhatják a felhasználókat.
  - **Letiltás**: ne engedélyezze a mobil adatcsatornát. A végfelhasználók nem kapcsolhatják be.
  - **Engedélyezés (nem szerkeszthető)** : engedélyezi a mobil adatcsatornát. A végfelhasználók nem kapcsolhatják ki.

- **Adatroaming**: a **blokk** megakadályozza a mobil adatroaming használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hálózatok közötti barangolást az adatok elérésekor.
- **VPN a mobil hálózaton keresztül**: a **Letiltás** megakadályozza, hogy az eszköz hozzáférjen a VPN-kapcsolatokhoz, amikor a hálózathoz csatlakozik. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a VPN számára bármilyen kapcsolat használatát, beleértve a mobilt is.
- **VPN-barangolás a mobilhálózat felett**: a **Letiltás** megakadályozza, hogy az eszköz hozzáférjen a VPN-kapcsolatokhoz a mobil hálózaton való barangoláskor. **Nincs konfigurálva** (az alapértelmezett) engedélyezi a VPN-kapcsolatokat barangolás közben.
- **Csatlakoztatott eszközök szolgáltatás**: a **Letiltás** letiltja a csatlakoztatott eszközök platform (CDP) összetevőjét. A CDP lehetővé teszi a felderítést és a kapcsolódást más eszközökhöz (Bluetooth/LAN-on vagy a felhőben) a távoli alkalmazások indításához, a távoli üzenetküldéshez, a távoli alkalmazás-munkamenetekhez és más, az eszközök közötti élményekhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a csatlakoztatott eszközök szolgáltatást, amely lehetővé teszi a felderítést és a csatlakozást más Bluetooth-eszközökhöz.
- **NFC**: **letiltja** a kis hatótávolságú kommunikáció (NFC) képességeit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az NFC-funkciók engedélyezését és konfigurálását az eszközön.
- **Wi-Fi**: a **blokk** megakadályozza, hogy a felhasználók a Wi-Fi-kapcsolatokat használják az eszközön, és engedélyezzék, konfigurálja és használják azokat. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Wi-Fi-kapcsolatokat.
- **Automatikus csatlakozás Wi-Fi elérési**pontokhoz **: megakadályozza** , hogy az eszközök automatikusan csatlakozzanak a Wi-Fi elérési pontokhoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszközök automatikusan csatlakozzanak az ingyenes Wi-Fi elérési pontokhoz, és automatikusan elfogadják a kapcsolat használati feltételeit.
- A **Wi-Fi manuális konfigurálása**: a **blokk** megakadályozza, hogy az eszközök csatlakozzanak a Mdm-kiszolgálón kívüli Wi-Fi-hálózathoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára a saját Wi-Fi-kapcsolataik hálózati SSID-azonosítóinak hozzáadását és konfigurálását.
- **Wi-Fi-vizsgálat időköze**: Itt adhatja meg, hogy az eszközök milyen gyakran keressenek Wi-Fi-hálózatokat. Adjon meg 1 (leggyakoribb) és 500 (a legkevésbé gyakori) értéket. Az alapértelmezett érték `0` (nulla).

### <a name="bluetooth"></a>Bluetooth

Ezek a beállítások a [Bluetooth Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Bluetooth**: **letiltja** a felhasználók számára a Bluetooth engedélyezését. **Nincs konfigurálva** (alapértelmezett) engedélyezi a Bluetooth használatát az eszközön.
- **Bluetooth-felderíthetőség**: a **blokk** megakadályozza, hogy az eszköz felderíthető legyen más Bluetooth-kompatibilis eszközökön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a más Bluetooth-kompatibilis eszközök, például a Headsetek számára az eszköz felderítését.
- **Bluetooth-előpárosítás**: a **blokk** megakadályozza, hogy a megadott Bluetooth-eszközök automatikusan párosítva legyenek a gazdagép eszközzel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az automatikus párosítást a gazdagép eszközzel.
- **Bluetooth-hirdetés**: a **blokk** megakadályozza, hogy az eszköz Bluetooth-hirdetéseket küldjön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszköz számára a Bluetooth-hirdetmények küldését.
- **Bluetooth-engedélyezett szolgáltatások**: az engedélyezett Bluetooth-szolgáltatások és-profilok listáját hexadecimális karakterláncként **adja hozzá** , például `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  A [ServicesAllowedList használati útmutatója](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) további információkat tartalmaz a szolgáltatás listájáról.

## <a name="cloud-and-storage"></a>Felhő és tárolás

Ezek a beállítások a [fiókok házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Microsoft-fiók**: a **Letiltás** megakadályozza, hogy a végfelhasználók Microsoft-fiók társítsák az eszközzel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi Microsoft-fiók hozzáadását és használatát.
- **Nem Microsoft-fiók**: a **Letiltás** megakadályozza, hogy a végfelhasználók nem Microsoft-fiókokat adjanak hozzá a felhasználói felület használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a Microsoft-fiókhoz nem társított e-mail-fiókok hozzáadását.
- **Microsoft-fiók beállításainak szinkronizálása**: **nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a rendszer az eszközök közötti szinkronizáláshoz társítsa a Microsoft-fiók eszköz-és Alkalmazásbeállítások. A **Letiltás** megakadályozza a szinkronizálást.
- **Microsoft-fiók bejelentkezési segédje**: Ha a **nincs konfigurálva** értékre van állítva, a végfelhasználók elindíthatják és leállíthatják a **Microsoft-fiók bejelentkezési segédje** (wlidsvc) szolgáltatását. Ez az operációsrendszer-szolgáltatás lehetővé teszi, hogy a felhasználók bejelentkezzenek a Microsoft-fiókba. A **Letiltás** beállítás meggátolja a végfelhasználók számára a Microsoft bejelentkezési segéd szolgáltatás (wlidsvc) szabályozását.

## <a name="cloud-printer"></a>Felhőbeli nyomtató

Ezek a beállítások a [EnterpriseCloudPrint házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Nyomtató-felderítési URL-cím**: adja meg a Felhőbeli nyomtatók keresésének URL-címét. Például írja be a következőt: `https://cloudprinterdiscovery.contoso.com`.
- **Nyomtató hozzáférési szolgáltatójának URL-címe**: adja meg a hitelesítési végpont URL-címét az OAuth-tokenek lekéréséhez. Például írja be a következőt: `https://azuretenant.contoso.com/adfs`.
- **Natív Azure-ügyfélalkalmazás GUID-azonosítója**: adja meg egy olyan ügyfélalkalmazás GUID azonosítóját, amely a OAuth származó OAuth-tokenek beolvasására jogosult. Például írja be a következőt: `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **Nyomtatási szolgáltatás erőforrás-URI-ja**: adja meg a Azure Portalban konfigurált nyomtatási szolgáltatás OAuth erőforrás-URI-ját. Például írja be a következőt: `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Lekérdezhető nyomtatók maximális**száma: adja meg a lekérdezni kívánt nyomtatók maximális számát. Az alapértelmezett érték `20`.
- **Nyomtató-felderítési szolgáltatás erőforrás-URI-ja**: adja meg a OAuth-erőforrás URI-ját a Azure Portal konfigurált nyomtató-felderítési szolgáltatáshoz. Például írja be a következőt: `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> A [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)beállítása után megadhatja ezeket a beállításokat, majd üzembe helyezheti a Windows-eszközökön.

## <a name="control-panel-and-settings"></a>Vezérlőpult és Gépház

- **Settings alkalmazás**: a **Letiltás** megakadályozza, hogy a végfelhasználók hozzáférhessenek a Windows beállítások alkalmazáshoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a beállítások alkalmazás megnyitását az eszközön.
  - **System**: a **Block** megakadályozza a hozzáférést a beállítások alkalmazás rendszerterületéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
    - **Energiagazdálkodási és alvási beállítások módosítása** (csak asztali verzióban): a **blokk** megakadályozza, hogy a végfelhasználók megváltoztassák az eszköz energiagazdálkodási és alvási beállításait. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az energiagazdálkodási beállítások módosítását.
  - **Eszközök**: a **Letiltás** megakadályozza az eszközön a beállítások alkalmazás eszközök területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Hálózati Internet**: a **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás hálózati & Internet területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Személyre szabás**: a **Letiltás** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás személyre szabott területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Alkalmazások**: a **Letiltás** megakadályozza az eszközön a beállítások alkalmazás alkalmazások területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Fiókok**: a **Letiltás** megakadályozza az eszközön lévő beállítások alkalmazás fiókok területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Idő és nyelv**: a **Letiltás** megakadályozza az eszközön lévő beállítások alkalmazás idő& nyelvi területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
    - **Rendszeridő módosítása**: a **blokk** megakadályozza, hogy a végfelhasználók módosíthassák a dátum-és időbeállításokat az eszközön. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.
    - **Területi beállítások módosítása** (csak asztali verzióban): a **blokk** megakadályozza, hogy a végfelhasználók módosíthassák a régió beállításait az eszközön. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.
    - **Nyelvi beállítások módosítása (csak asztali**verzióban): a **blokk** megakadályozza, hogy a végfelhasználók módosíthassák a nyelvi beállításokat az eszközön. A **nincs konfigurálva** beállítás megadása esetén a felhasználók módosíthatják ezeket a beállításokat.

      [Beállítások házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Gaming**: a **Block** megakadályozza a hozzáférést az eszközön lévő beállítások alkalmazás játék területéhez. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Könnyű hozzáférés**: a **blokk** megakadályozza az eszközön a beállítások alkalmazás egyszerű hozzáférés területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Adatvédelem**: a **Letiltás** megakadályozza az eszközön lévő beállítások alkalmazás adatvédelmi területének elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.
  - **Frissítés és biztonság**: a **Letiltás** megakadályozza a hozzáférést a settings alkalmazás Update & Security területéhez az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.

## <a name="display"></a>Megjelenítés

Ezek a beállítások a [megjelenítési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

A GDI DPI-méretezés lehetővé teszi, hogy a DPI-t nem támogató alkalmazások a figyelő DPI-vel legyenek tisztában.

- A **GDI-méretezés bekapcsolása az alkalmazásokhoz**: **adja hozzá** azokat az örökölt alkalmazásokat, AMELYeken a GDI DPI-méretezés be van kapcsolva. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés be van kapcsolva a listában szereplő összes örökölt alkalmazáshoz.

- A **GDI-méretezés kikapcsolása az alkalmazásokhoz**: **adja hozzá** azokat az örökölt alkalmazásokat, amelyeket a GDI DPI-méretezés ki szeretne kapcsolni. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés ki van kapcsolva a listában szereplő összes örökölt alkalmazás esetében.

Egy. csv-fájlt is **importálhat** az alkalmazások listájával.

## <a name="general"></a>Általános

Ezek a beállítások az [élmény házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)-t használják; amely a támogatott Windows-kiadásokat is felsorolja. 

- **Képernyőfelvétel** (csak mobileszköz esetén): a **blokk** megakadályozza, hogy a végfelhasználók képernyőképeket kapjanak az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Másolás és beillesztés (csak mobileszköz esetén)** : a **blokk** megakadályozza, hogy a végfelhasználók az eszközön lévő alkalmazások között másolást és beillesztést használjanak. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Regisztráció manuális**törlése: a **blokk** megakadályozza a végfelhasználók számára a munkahelyi fiók törlését az eszköz munkahelyi Vezérlőpultjának használatával. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.

  Ez a házirend-beállítás nem vonatkozik arra az esetre, ha a számítógép Azure AD-hez csatlakozik, és engedélyezve van az automatikus regisztráció.

- **Főtanúsítvány manuális telepítése** (csak mobileszköz esetén): a **Letiltás** megakadályozza a végfelhasználók számára a főtanúsítványok és a köztes Cap-tanúsítványok manuális telepítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kamera**: a **Letiltás** megakadályozza, hogy a végfelhasználók a kamerát használják az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.

  [Kamera CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-camera)

- **OneDrive fájl szinkronizálása**: a **Letiltás** megakadályozza, hogy a végfelhasználók szinkronizálják a fájlokat az eszközről a OneDrive. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Cserélhető tároló**: a **blokk** megakadályozza, hogy a végfelhasználók külső tárolóeszközöket használjanak, például SD-kártyákat az eszközzel. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- Földrajzi **hely: a** **Letiltás** megakadályozza, hogy a végfelhasználók bekapcsolják a Location Servicest az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Internetkapcsolat**megosztása: a **blokk** megakadályozza az internetkapcsolat megosztását az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Telefon alaphelyzetbe állítása**: a **blokk** megakadályozza, hogy a végfelhasználók törölve legyenek, vagy a gyári beállítások visszaállítása az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **USB-kapcsolat**: a **blokk** megakadályozza a külső tárolóeszközök elérését az eszközön található USB-kapcsolaton keresztül. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót. Ez a beállítás nem érinti az USB-töltést.
- **Lopásgátló üzemmód** (csak mobil): a **Letiltás** megakadályozza, hogy a végfelhasználók lopásgátló üzemmódot válasszanak az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Cortana**: letiltja a Cortana hangsegéd **letiltását** az eszközön. Ha a Cortana ki van kapcsolva, a felhasználók továbbra is kereshetik az eszközön található elemeket. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Cortana.
- **Hangrögzítés** (csak mobileszköz esetén): a **blokk** megakadályozza, hogy a végfelhasználók az eszközön lévő Hangrögzítőt használják. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hangrögzítést az alkalmazásokhoz.
- **Eszköz nevének módosítása** (csak mobileszköz esetén): a **blokk** megakadályozza, hogy a végfelhasználók módosíthassák az eszköz nevét. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kiépítési csomagok hozzáadása**: a **Letiltás** megakadályozza, hogy a futásidejű konfigurációs ügynök üzembe helyezési csomagokat telepítsen az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Kiépítési csomagok eltávolítása**: a **blokk** megakadályozza, hogy a futásidejű konfigurációs ügynök eltávolítja az eszközről a kiépítési csomagokat. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Eszköz felderítése**: a **Letiltás** megakadályozza, hogy az eszköz felderítse a többi eszközt. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **Feladat-kapcsoló** (csak mobil): a **Letiltás** megakadályozza a feladat váltását az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
- **SIM-kártya hiba párbeszédpanele** (csak mobil): **letiltja** a hibaüzeneteket az eszközön, ha a rendszer nem észlel SIM-kártyát. **Nincs konfigurálva** (az alapértelmezett) megjeleníti a hibaüzeneteket.
- **Tinta munkaterület**: válassza ki, hogy a felhasználó hogyan fér hozzá a tinta munkaterülethez. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): bekapcsolja a tinta munkaterületet, és a felhasználó a zárolási képernyő feletti használatra jogosult.
  - **Letiltva a zárolási képernyőn**: a tinta munkaterület engedélyezve van, és a funkció be van kapcsolva. A felhasználó azonban nem fér hozzá a zárolási képernyő felett.
  - **Letiltva**: a szabadkézi munkaterülethez való hozzáférés le van tiltva. A szolgáltatás ki van kapcsolva.

  [WindowsInkWorkspace házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Automatikus újratelepítés**: válassza az **Engedélyezés lehetőséget** , hogy a rendszergazdai jogosultságokkal rendelkező felhasználók az eszköz zárolási képernyőjén a **CTRL + Win + R billentyűkombinációval** törölhetik az összes felhasználói adatforrást és beállítást. A rendszer automatikusan újrakonfigurálja az eszközt, és újból regisztrálja őket a felügyeletbe. **Nincs konfigurálva** (alapértelmezés) megakadályozza ezt a funkciót.
- A hálózathoz való **Csatlakozás megkövetelése a felhasználók számára az eszköz telepítése során**: válassza a **szükséges** lehetőséget, hogy az eszköz csatlakozzon a hálózathoz, mielőtt továbblép a hálózat lapra a Windows telepítője során. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy a hálózat oldalára lépjenek, még akkor is, ha nem csatlakozik hálózathoz.

  A beállítás az eszköz legközelebb törlésével vagy alaphelyzetbe állításával válik hatályossá. A többi Intune-konfigurációhoz hasonlóan az eszközt az Intune-nak kell regisztrálnia és kezelnie a konfigurációs beállítások fogadásához. Ha azonban regisztrálva van, és a házirendeket fogad, akkor az eszköz alaphelyzetbe állítása a következő Windows-telepítéskor kényszeríti a beállítást.

  [TenantLockdown CSP](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp)

- **Közvetlen memória-hozzáférés**: a **blokk** megakadályozza a közvetlen memória-hozzáférés (DMA) használatát az összes melegen csatlakoztatható PCI-porton, amíg a felhasználó be nem jelentkezik a Windowsba. **Engedélyezve** (alapértelmezés) engedélyezi a hozzáférést a DMA-hoz, még akkor is, ha a felhasználó nincs bejelentkezve.

  [DataProtection/AllowDirectMemoryAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Folyamatok leállítása a Feladatkezelő eszközből**: Ez a beállítás határozza meg, hogy a nem rendszergazdák használhatják-e a Feladatkezelőt a feladatok befejezéséhez. A **Letiltás** megakadályozza, hogy az általános jogú felhasználók (nem rendszergazdák) a Feladatkezelő segítségével fejezzenek be egy folyamatot vagy feladatot az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a normál felhasználók egy folyamatot vagy feladatot fejezzenek be a Feladatkezelő használatával.

## <a name="locked-screen-experience"></a>Zárolási képernyő felülete

- **Műveletközpont értesítései (csak mobil)** : a **Letiltás** megakadályozza a Műveletközpont értesítéseinek megjelenítését az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválasszák, hogy mely alkalmazások jelenjenek meg értesítések a zárolási képernyőn.

  [AboveLock/AllowActionCenterNotifications CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#AboveLock_AllowActionCenterNotifications)

- **Zárolt képernyő kép URL-címe (csak asztali verzió)** : adja meg a Windows zárolási képernyőjének hátterében használt jpg, JPEG vagy PNG formátumú kép URL-címét. Például írja be a következőt: `https://contoso.com/image.png`. Ez a beállítás zárolja a rendszerképet, és ezt követően nem módosítható.
- **Felhasználó által konfigurálható képernyő-időkorlát (csak mobil)** : **engedélyezi, hogy** a felhasználók konfigurálja a képernyő időkorlátját. **Nincs konfigurálva** (az alapértelmezett) nem adja meg a felhasználóknak ezt a lehetőséget.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana zárolt képernyőn** (csak asztali verzióban): a **blokk** megakadályozza, hogy a felhasználók a Cortana használhassák, amikor az eszköz a zárolási képernyőn található. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Cortana való interakciót.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Bejelentési értesítések zárolt képernyőn**: **letiltja** a bejelentési értesítések elrejtését az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket az értesítéseket.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Képernyő időkorlátja (csak mobil)** : állítsa be a képernyő zárolásának időtartamát (másodpercben) a képernyő kikapcsolásához. A támogatott értékek a 11-1800. Adja meg például a `300` értéket az időtúllépés 5 percre való beállításához.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_ScreenTimeoutWhileLocked)

## <a name="messaging"></a>Üzenetkezelési

Ezek a beállítások az [üzenetküldési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging)-t használják; amely a támogatott Windows-kiadásokat is felsorolja.

- **Üzenet-szinkronizálás (csak mobil)** : a **Letiltás** letiltja a szöveges üzenetek biztonsági mentését és visszaállítását, valamint az üzenetek Windows-eszközök közötti szinkronizálását. A Letiltás segít elkerülni a szervezet vezérlőn kívüli kiszolgálókon tárolt adatok tárolását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók megváltoztassák ezeket a beállításokat, és szinkronizálják az üzeneteiket.
- **MMS (csak mobil)** : a **LETILTÁS** letiltja az MMS-küldési és-fogadási funkciót az eszközön. A vállalatok esetében ezzel a szabályzattal letilthatja az MMS-eszközöket az eszközökön a naplózási vagy felügyeleti követelmények részeként. **Nincs konfigurálva** (alapértelmezés) engedélyezi az MMS küldését és fogadását.
- **RCS (csak mobil)** : a **Letiltás** letiltja a kommunikációs szolgáltatások (RCS) a küldési és fogadási funkcióit az eszközön. A vállalatok esetében ezzel a szabályzattal tilthatja le a RCS az eszközökön a naplózási vagy felügyeleti követelmények részeként. **Nincs konfigurálva** (alapértelmezés) engedélyezi a RCS küldését és fogadását.

## <a name="microsoft-edge-browser"></a>Microsoft Edge böngésző

Ezek a beállítások a [böngésző házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

### <a name="use-microsoft-edge-kiosk-mode"></a>A Microsoft Edge kioszk mód használata

Az elérhető beállítások a választott lehetőségtől függően változnak. A választható lehetőségek:

- **Nem** (alapértelmezett): a Microsoft Edge nem kioszk módban fut. A Microsoft Edge összes beállítását módosíthatja és konfigurálhatja.
- **Digitális/interaktív aláírások (Egyalkalmazásos kioszkok)** : a Microsoft Edge azon beállításainak szűrése, amelyek a digitális/interaktív aláírások Microsoft Edge kioszk módban használhatók csak a Windows 10 single-app kioszkok esetében. Ezzel a beállítással megnyithatja a teljes URL-címet, és csak az adott webhelyen lévő tartalmat jelenítheti meg. A [digitális jelek beállítása](https://docs.microsoft.com/windows/configuration/setup-digital-signage) a szolgáltatással kapcsolatos további információkat tartalmaz.
- **InPrivate nyilvános böngészés (Egyalkalmazásos kioszk)** : a Microsoft Edge azon beállításainak szűrése, amelyek az InPrivate nyilvános böngészéshez használhatók a Microsoft Edge kioszk módban a Windows 10 single-app kioszkokon. A Microsoft Edge többoldalas verzióját futtatja.
- **Normál mód (többalkalmazásos kioszk)** : a Microsoft Edge-beállítások normál, a Microsoft Edge kioszk üzemmódra érvényes beállításait szűri. A Microsoft Edge teljes verzióját futtatja minden böngészési funkcióval.
- **Nyilvános böngészés (többalkalmazásos kioszk)** : szűri a Microsoft Edge azon beállításait, amelyek a Windows 10 többalkalmazásos kioszkban való nyilvános böngészésre alkalmazhatók.  Futtatja a Microsoft Edge multi-Tab verzióját.

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

- **A Microsoft Edge elindítása**: válassza ki, hogy mely lapok nyílnak meg a Microsoft Edge indításakor. A választható lehetőségek:
  - **Egyéni kezdőlapok**: adja meg a kezdő lapokat, például `http://www.contoso.com`. A Microsoft Edge betölti a beírt kezdő lapokat.
  - **Új lap lapja**: a Microsoft Edge betöltése bármi bekerül az **új lap URL-címének** beállítására.
  - **Utolsó munkamenet lapja**: a Microsoft Edge betölti az utolsó munkamenet lapot.
  - Kezdőlapok **a helyi alkalmazás beállításaiban**: a Microsoft Edge az operációs rendszer által meghatározott alapértelmezett kezdőlaptal kezdődik.

- **Kezdőlapok módosításának engedélyezése a felhasználó**számára: **Igen** (alapértelmezés) lehetővé teszi a felhasználók számára a kezdőlapok módosítását. A rendszergazdák a `EdgeHomepageUrls` segítségével megadhatják a kezdő lapokat, amelyeket a felhasználók alapértelmezés szerint látnak a Microsoft Edge megnyitásakor. **Nem** blokkolja a felhasználók a kezdőlapok módosítását.
- **Webtartalom engedélyezése az új lapon**lapon: Ha az **Igen** értékre van állítva, a Microsoft Edge megnyitja az **új lap URL-címében** megadott URL-címet. Ha az **új lap URL-címe** üres, a Microsoft Edge megnyitja az új lap lapot a Microsoft Edge beállításaiban. A felhasználók módosíthatják azt. Ha a **nem**értékre van állítva, a Microsoft Edge új lapot nyit meg egy üres oldallal. A felhasználók nem változtathatják meg.
- **Új lap URL-címe**: Itt adhatja meg az új lap lapon megnyitható URL-címet. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.

- **Kezdőlap gomb**: válassza ki, hogy mi történjen a Kezdőlap gomb kiválasztásakor. A választható lehetőségek:
  - **Kezdőlapok**: megnyitja a kiválasztott lehetőséget a **Microsoft Edge** -beli elindítása a beállítással
  - **Új lap**lap: megnyitja az **új lap URL-címében** megadott URL-címet.
  - **Kezdőlap gomb URL-címe**: adja meg a megnyitni kívánt URL-címet. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.
  - **Kezdőlap gomb elrejtése**: elrejti a Kezdőlap gombot
- A **Kezdőlap gomb módosításának engedélyezése a felhasználók**számára: **Igen** , lehetővé teszi a felhasználók számára a Kezdőlap gomb módosítását. A felhasználó módosításai felülbírálják a rendszergazdai beállításokat a Home (Kezdőlap) gombra. **Nem** (alapértelmezett) megakadályozza, hogy a felhasználók megváltoztassák, hogyan konfigurálta a rendszergazda a Kezdőlap gombot.
- **Első futtatási élmény megjelenítése lap (csak mobil)** : **Igen** (alapértelmezés) a Microsoft Edge első használat bemutatása lapján látható. A Microsoft Edge első futtatásakor a bevezető oldal **nem** jelenik meg. Ez a funkció lehetővé teszi, hogy a vállalatok, például a nulla kibocsátási konfigurációkba beléptetett szervezetek regisztrálva legyenek ezen a lapon.
- **Első futtatási élmény URL-listájának helye** (csak Windows 10 Mobile esetén): adja meg azt az URL-címet, amely az első futtatási oldal URL-címét tartalmazó XML-fájlra mutat. Például írja be a következőt: `https://www.contoso.com/sites.xml`.

- **Böngésző frissítése üresjárati idő után**: adja meg az üresjárati percek számát, amíg a böngésző frissül, 0-1440 percen belül. Az alapértelmezett érték `5` perc. Ha `0` (nulla) értékre van állítva, a böngésző üresjárat után nem frissül.

  Ez a beállítás csak akkor érhető el, ha [InPrivate nyilvános böngészés (Egyalkalmazásos kioszk)](#use-microsoft-edge-kiosk-mode)fut.

- **Előugró ablakok engedélyezése** (csak asztali verzió): **Igen** (alapértelmezés) lehetővé teszi az előugró ablakok használatát a böngészőben. **Nem** akadályozza meg az előugró ablakokat a böngészőben.
- **Intranetes forgalom küldése az Internet Explorerhez** (csak asztali verzió): **Igen** , lehetővé teszi, hogy a felhasználók a Microsoft Edge helyett az Internet Explorerben nyissák meg az intranetes webhelyeket Ez a beállítás a visszamenőleges kompatibilitáshoz szükséges. **Nem** (alapértelmezett): a felhasználók a Microsoft Edge használatát teszik lehetővé.
- **Vállalati üzemmód helyének listázási helye** (csak asztali verzió): adja meg az URL-címet, amely a vállalati módban megnyitott webhelyek listáját tartalmazó XML-fájlra mutat. A felhasználók nem változtathatják meg a listát. Például írja be a következőt: `https://www.contoso.com/sites.xml`.
- **Üzenet a helyek Internet Explorerben való megnyitásakor**: ezzel a beállítással konfigurálhatja a Microsoft Edge-t, hogy megjelenjen egy értesítés, mielőtt egy webhely megnyílik az Internet Explorer 11 alkalmazásban. A választható lehetőségek:
  - **Ne jelenjen meg üzenet**: az operációs rendszer alapértelmezett viselkedését használja, amely nem jelenít meg üzenetet.
  - Az **Internet Explorer 11 böngészőben megnyitott üzenet megjelenítése**: megjeleníti az üzenetet, amikor a webhelyeket nyitják meg az IE-ben. A helyek megnyitva az IE-ben. 
  - A **Microsoft Edge-helyek megnyitására szolgáló lehetőséggel rendelkező üzenet megjelenítése**: az üzenet megjelenítése a helyek Microsoft Edge-ben való megnyitásakor. Az üzenet tartalmaz egy **lépést a Microsoft Edge-** hivatkozásban, hogy a felhasználók az IE helyett a Microsoft Edge-et is kiválaszthatják.

  > [!IMPORTANT]
  > Ehhez a beállításhoz a **vállalati üzemmód helyének listázási helye** beállítást kell használnia, az **intranetes adatforgalom küldése az Internet Explorerhez** vagy mindkét beállításhoz.

- **Microsoft kompatibilitási lista engedélyezése**: az **Igen** (alapértelmezett) beállítás lehetővé teszi a Microsoft kompatibilitási listájának használatát. **Nem** akadályozza meg a Microsoft-kompatibilitási listát a Microsoft Edge-ben. A Microsoft ezen listája segíti a Microsoft Edge számára az ismert kompatibilitási problémákkal rendelkező helyek megfelelő megjelenítését.
- Előtöltési **kezdőlapok és új lap lap**: az **Igen** (alapértelmezett) az operációs rendszer alapértelmezett viselkedését használja, amely lehet, hogy előállítja a lapokat. Az előre betöltéssel csökkentheti a Microsoft Edge elindításának idejét és az új lapok betöltését. A **nem** akadályozza meg, hogy a Microsoft Edge ne legyenek előre betöltve a kezdőlapok és az új lapok.
- A **kezdőlapok és az új lap megnyitása**: az **Igen** (alapértelmezett) az operációs rendszer alapértelmezett viselkedését használja, amely a lapok előindítására is használható. Az előzetes indítás segít a Microsoft Edge teljesítményében, és minimálisra csökkenti a Microsoft Edge elindításához szükséges időt. **Nem** akadályozza meg, hogy a Microsoft Edge előre elindítsa a kezdőlapokat és az új lapokat.

### <a name="favorites-and-search"></a>Kedvencek és keresés

- **Kedvencek sáv megjelenítése**: válassza ki, hogy mi történik a Microsoft Edge-lapokon a Kedvencek sávhoz. A választható lehetőségek:
  - **A Start és az új lap lapokon**: a Kedvencek sáv megjelenítése a Microsoft Edge indításakor és az összes lapon. A végfelhasználók módosíthatják ezt a beállítást.
  - **Minden oldalon**: a Kedvencek sáv megjelenítése az összes oldalon. A végfelhasználók nem változtathatják meg ezt a beállítást.
  - **Rejtett**: elrejti a Kedvencek sávot az összes oldalon. A végfelhasználók nem változtathatják meg ezt a beállítást.
- A **Kedvencek módosításának engedélyezése**: az **Igen** (alapértelmezett) az operációs rendszer alapértelmezését használja, amely lehetővé teszi a felhasználók számára a lista módosítását. A **nem** teszi lehetővé a végfelhasználók számára a kedvencek listájának hozzáadását, importálását, rendezését és szerkesztését.
  - **Kedvencek listája**: adja meg a Kedvencek fájl URL-címeinek listáját. Adja meg például `http://contoso.com/favorites.html`.
- **Kedvencek szinkronizálása a Microsoft-böngészők között** (csak asztali verzió): **Igen** kényszeríti a Windowst a Kedvencek szinkronizálására az Internet Explorer és a Microsoft Edge között. A Kedvencek között a hozzáadások, a törlések, a módosítások és a megrendelési módosítások megoszthatók a böngészők között.  **Nem** (alapértelmezett) az operációs rendszer alapértelmezését használja, amely lehetővé teheti a felhasználóknak a Kedvencek szinkronizálását a böngészők között.
- **Alapértelmezett keresőmotor**: válassza ki az alapértelmezett keresőmotort az eszközön. A végfelhasználók ezt az értéket bármikor módosíthatják. A választható lehetőségek:
  - Keresőmotor az ügyfél Microsoft Edge-beállításaiban
  - Bing
  - Google
  - Yahoo
  - Egyéni érték: a **OpenSearch XML URL-címében**adjon meg egy HTTPS URL-címet, amely tartalmazza a keresőmotor rövid nevét és URL-címét (minimum). Például írja be a következőt: `https://www.contoso.com/opensearch.xml`.
- **Keresési javaslatok megjelenítése**: **Igen** (alapértelmezés) lehetővé teszi, hogy a keresőmotor a címsorban keresési kifejezések beírásakor javasoljon helyeket. **Nem** akadályozza meg ezt a funkciót.
- **Keresőmotor-változások engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi, hogy a felhasználók új keresőmotorokat adjanak hozzá, vagy megváltoztassák az alapértelmezett keresőmotort a Microsoft Edge-ben. A **nem** gombra kattintva megakadályozhatja, hogy a felhasználók testreszabják a keresőmotort.

  Ez a beállítás csak akkor érhető el, ha [normál módban fut (több alkalmazásból álló kioszk)](#use-microsoft-edge-kiosk-mode).

### <a name="privacy-and-security"></a>Adatvédelem és biztonság

- **InPrivate-böngészés engedélyezése**: az **Igen** (alapértelmezés) lehetővé teszi az InPrivate-böngészést a Microsoft Edge-ben. Az összes InPrivate-fül bezárása után a Microsoft Edge törli a böngészési adatait az eszközről. **Nem** akadályozza meg, hogy a végfelhasználók InPrivate-böngészési munkameneteket nyissanak meg.
- **Böngészési előzmények mentése**: **Igen** (alapértelmezés) lehetővé teszi a böngészési előzmények mentését a Microsoft Edge-ben. **Nem** akadályozza meg a böngészési előzmények mentését.
- **Böngészési adatokat kihagyhatja a kilépéskor** (csak asztali verzióban): **Igen** törli az előzményeket és a böngészési adatokat, amikor a felhasználó kilép a Microsoft Edge-ből. A **nem** (alapértelmezett) az operációs rendszer alapértelmezett beállítását használja, amely gyorsítótárazhatja a böngészési adatfájlokat.
- **Böngésző beállításainak szinkronizálása a felhasználók eszközei között**: válassza ki, hogyan szeretné szinkronizálni a böngésző beállításait az eszközök között. A választható lehetőségek:
  - **Engedélyezés**: a Microsoft Edge böngésző beállításainak szinkronizálásának engedélyezése a felhasználó eszközei között
  - **Felhasználói felülbírálás letiltása és engedélyezése**: a Microsoft Edge böngésző beállításainak szinkronizálásának letiltása a felhasználó eszközei között. A felhasználók felülbírálhatja ezt a beállítást.
  - **Letiltás**: a Microsoft Edge böngésző beállításainak szinkronizálásának letiltása a felhasználók eszközei között. A felhasználók nem írhatják felül ezt a beállítást.

Ha a "felhasználói felülbírálás tiltása és engedélyezése" lehetőség van kiválasztva, a felhasználó felülbírálhatja a rendszergazda megjelölését.

- A **Password Manager engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára a Password Manager automatikus használatát, amely lehetővé teszi a felhasználók számára a jelszavak mentését és kezelését az eszközön. **Nem** akadályozza meg a Microsoft Edge használatát a Password Manager használatával.
- **Cookie-k**: válassza ki, hogyan történjen a cookie-k kezelése a böngészőben. A választható lehetőségek:
  - **Engedélyezés**: a cookie-k tárolása az eszközön történik.
  - Az **összes cookie blokkolása**: a cookie-k nem tárolódnak az eszközön.
  - **Csak a harmadik féltől származó cookie-k letiltása**: a harmadik féltől származó vagy partneri cookie-k nem tárolódnak az eszközön.
- **Automatikus kitöltés engedélyezése az űrlapokon**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy módosítsák a böngésző automatikus kiegészítési beállításait, és automatikusan feltöltsék az űrlapmezőket. **Nem** tiltja le az automatikus kitöltés funkciót a Microsoft Edge-ben.
- Nem **nyomon követhető fejlécek küldése**: **Igen** – a nyomkövetési adatokat kérő webhelyeken nem követhető fejlécek küldése (ajánlott). **Nem** (alapértelmezett) nem küld fejléceket, amelyek lehetővé teszik a webhelyek számára a felhasználó nyomon követését. A felhasználó beállítható.
- A **WebRTC localhost IP-címének megjelenítése**: **Igen** (alapértelmezés) lehetővé teszi a felhasználók localhost IP-címének megjelenítését, amikor telefonhívásokat végez a protokoll használatával. A **nem** akadályozza meg, hogy a felhasználók localhost IP-címe megjelenjen. 
- **Élő csempe adatgyűjtésének engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára a Start menübe rögzített élő csempék adatainak gyűjtését. **Nem** akadályozza meg az adatok gyűjtését, ami korlátozott felhasználói élményt biztosíthat a felhasználóknak.
- A **felhasználó felülbírálhatja a tanúsítvány hibáit**: az **Igen** (alapértelmezett) lehetővé teszi, hogy a felhasználók hozzáférhessenek SSL/TRANSPORT Layer Security (SSL/TLS) hibákat tartalmazó webhelyekhez. **Nem** (a fokozott biztonsághoz ajánlott) megakadályozza, hogy a felhasználók SSL-vagy TLS-hibákkal férhessenek hozzá a webhelyekhez.

### <a name="additional"></a>További

- **Microsoft Edge böngésző engedélyezése** (csak mobil): **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge webböngésző használatát a mobileszközön. **Nem** akadályozza meg a Microsoft Edge használatát az eszközön. Ha a **nem**lehetőséget választja, a többi egyéni beállítás csak az asztalra vonatkozik.
- **Címsor legördülő menüjének engedélyezése**: **Igen** (alapértelmezés) lehetővé teszi a Microsoft Edge számára, hogy megjelenjen a címsor legördülő lista a javaslatok listájával. A **nem** állítja le a Microsoft Edge-t a legördülő listában szereplő javaslatok listájának megjelenítéséhez a beíráskor. Ha a **nem**értékre van állítva, akkor:
  - A Microsoft Edge és a Microsoft-szolgáltatások közötti hálózati sávszélesség csökkentése.
  - Tiltsa le a **Keresés és a webhely javaslatainak beírása** a Microsoft Edge-> beállításainál.
- **Teljes képernyős mód engedélyezése**: az **Igen** (alapértelmezett) lehetővé teszi a Microsoft Edge számára, hogy teljes képernyős módot használjon, amely csak a webes tartalmat jeleníti meg, és elrejti a Microsoft Edge felhasználói felületet. A teljes képernyős mód **nem** akadályozza meg a Microsoft Edge-ben.
- Az **About Flags lap engedélyezése**: az **Igen** (alapértelmezett) az operációs rendszer alapértelmezését használja, ami engedélyezheti a `about:flags` oldal elérését. A `about:flags` lap lehetővé teszi a felhasználóknak a fejlesztői beállítások módosítását és a kísérleti funkciók engedélyezését. **Nem** akadályozza meg, hogy a végfelhasználók hozzáférhessenek a `about:flags` lapjához a Microsoft Edge-ben.
- **Fejlesztői eszközök engedélyezése**: az **Igen** (alapértelmezett) lehetővé teszi, hogy a felhasználók az F12 fejlesztői eszközöket használják a weblapok létrehozásához és hibakereséséhez alapértelmezés szerint. **Nem** akadályozza meg, hogy a végfelhasználók az F12 fejlesztői eszközöket használják.
- **JavaScript engedélyezése**: az **Igen** (alapértelmezett) lehetővé teszi a parancsfájlok (például a JavaScript) futtatását a Microsoft Edge böngészőben. **Nem** akadályozza meg, hogy a böngészőben a Java-parancsfájlok fussanak.
- A **felhasználók telepíthetik a bővítményeket**: **Igen** (alapértelmezés) lehetővé teszi a végfelhasználók számára a Microsoft Edge-bővítmények telepítését az eszközön. **Nem** akadályozza meg a telepítést.
- **Fejlesztői bővítmények közvetlen telepítési engedélyezése**: az **Igen** (alapértelmezett) az operációs rendszer alapértelmezését használja, amely lehetővé teheti a közvetlen telepítési. A közvetlen telepítési telepíti és futtatja a nem ellenőrzött bővítményeket. **Nem** akadályozza meg, hogy a Microsoft Edge a közvetlen telepítési a **Load Extensions** szolgáltatást használja. Nem akadályozza meg, hogy a közvetlen telepítési bővítmények más módon, például a PowerShell használatával legyenek használva.
- **Szükséges bővítmények**: válassza ki, hogy mely bővítményeket nem lehet kikapcsolni a végfelhasználók számára a Microsoft Edge-ben. Adja meg a csomag családjának nevét, majd kattintson a **Hozzáadás**gombra. [A csomaghoz tartozó családi név (PFN) megkeresése](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) néhány útmutatást tartalmaz.

  **Importálhat** egy CSV-fájlt is, amely tartalmazza a csomag családjának nevét. Vagy **exportálja** a megadott csomagbeli család nevét.

## <a name="network-proxy"></a>Hálózati proxy

Ezek a beállítások a [NetworkProxy házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Proxybeállítások automatikus észlelése**: a **Letiltás** letiltja az eszköz számára a proxy automatikus konfigurációs (PAC) parancsfájljának automatikus észlelését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót. Ha engedélyezve van, az eszköz megpróbálja megkeresni egy PAC-szkript elérési útját.
- **Proxy parancsfájl használata**: az **Engedélyezés** gombra kattintva MEGadhatja a PAC-parancsfájl elérési útját a proxykiszolgáló konfigurálásához. **Nincs konfigurálva** (alapértelmezés) nem teszi lehetővé a PAC-szkriptek URL-címének megadását.
  - **Telepítési parancsfájl URL-címe**: adja meg a proxykiszolgáló konfigurálásához használni kívánt PAC-parancsfájl URL-címét.
- **Manuális proxykiszolgáló használata**: válassza az **Engedélyezés lehetőséget** a proxykiszolgáló nevének vagy IP-címének és TCP-portszámának manuális megadásához. **Nincs konfigurálva** (alapértelmezés) nem teszi lehetővé a proxykiszolgáló adatainak manuális megadását.
  - **Cím**: adja meg a proxykiszolgáló nevét vagy IP-címét.
  - **Portszám**: adja meg a proxykiszolgáló portszámát.
  - **Proxy-kivételek**: adjon meg olyan URL-címeket, amelyek nem használhatják a proxykiszolgálót. Az egyes címeket pontosvesszővel választhatja el egymástól.
  - **Proxykiszolgáló kihagyása helyi cím esetén**: **nincs konfigurálva** (alapértelmezés) megakadályozza a proxykiszolgáló használatát az intraneten lévő helyi címekhez. **Engedélyezi** a proxykiszolgáló használatát a helyi címekhez.

## <a name="password"></a>Jelszó

Ezek a beállítások a [DeviceLock házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Password (jelszó**): **megköveteli** a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez. **Nincs konfigurálva** (alapértelmezés) jelszó nélkül teszi lehetővé az eszköz elérését. Csak a helyi fiókokra vonatkozik. A tartományi fiókhoz tartozó jelszavakat Active Directory (AD) és az Azure AD is konfigurálja.

  - **Szükséges jelszó típusa**: válassza ki a jelszó típusát. A választható lehetőségek:
    - **Nincs konfigurálva**: a jelszó tartalmazhat számokat és betűket.
    - **Numerikus**: a jelszó csak számokból hívható meg.
    - **Alfanumerikus**: a jelszónak számokból és betűkből álló kombinációnak kell lennie.
  - **Jelszó minimális hossza**: Itt adhatja meg a minimálisan szükséges számot vagy karaktereket (4-16). Adja meg például a `6` értéket, ha legalább hat karaktert szeretne megadni a jelszó hosszában.
  
    > [!IMPORTANT]
    > Ha a jelszóra vonatkozó követelményt egy Windows asztalon módosítják, a felhasználók a következő bejelentkezéskor jelentkeznek, ahogy az az eszköz tétlenről aktív állapotba kerül. A követelménynek megfelelő jelszóval rendelkező felhasználókat a rendszer továbbra is megkéri a jelszavuk módosítására.
    
  - **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Itt adhatja meg az eszköz törlése előtt engedélyezett hitelesítési hibák számát, akár 11-re is. A beírt érvényes szám a kiadástól függ. A [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) listázza a támogatott értékeket. `0` (nulla) letilthatja az eszköz törlési funkcióját.

    Ez a beállítás a kiadástól függően más hatással is van. A beállítás részletes ismertetését lásd: [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - A **Képernyő zárolása legfeljebb ennyi perc inaktivitás**után: adja meg, hogy az eszköznek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.
  - **Jelszó érvényessége (napokban)** : adja meg az időtartamot napokban, amikor az eszköz jelszavát módosítani kell, a 1-365-ból. Írja be például, hogy `90`, hogy a jelszót 90 nap után lejárja.
  - **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg a korábban nem használható jelszavak számát 1-24-ről. Írja be például, hogy `5`, hogy a felhasználók nem állíthatnak be új jelszót a jelenlegi jelszavuk vagy az előző négy jelszavuk bármelyike számára.
  - **Jelszó kérése, ha az eszköz visszatér az inaktív állapotból** (mobil és holografikus): válassza a **szükséges** lehetőséget, hogy a felhasználóknak jelszót kell megadniuk az eszköz zárolásának feloldásához. **Nincs konfigurálva** (az alapértelmezett) nem igényel PIN-kódot vagy jelszót, amikor az eszköz visszatér inaktív állapotból.
  - **Egyszerű jelszavak**: a **Letiltás** beállítás megadásával a felhasználók nem hozhatnak létre egyszerű jelszavakat, például `1234` vagy `1111`. Állítsa be úgy, hogy **ne legyen konfigurálva** (alapértelmezett), hogy a felhasználók jelszavakat hozzanak létre, például `1234` vagy `1111`. Ez a beállítás a Windows-képjelszavak használatát is engedélyezi vagy letiltja.
- **Automatikus titkosítás a AADJ során**: a **blokk** megakadályozza a BitLocker-eszközök automatikus titkosítását az eszköz első használatra való előkészítésekor, amikor az eszköz csatlakozik az Azure ad-hez. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezett alapértékét használja, amely lehetővé teszi a titkosítást. További információ a [BitLocker-eszközök titkosításáról](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Biztonság/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Federal Information Processing standard (FIPS) szabályzat**: az **Engedélyezés** a Federal Information Processing standard (FIPS) szabályzatot használja, amely az Egyesült államokbeli kormányzati szabvány a titkosításhoz, a kivonatoláshoz és az aláíráshoz. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezett alapértékét használja, amely nem használ FIPS-t.

  [Kriptográfia/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello eszköz hitelesítése**: **lehetővé teszi** a felhasználóknak a Windows Hello Companion-eszközök, például a telefon, a fitness-sáv vagy a IoT-eszköz használatát a Windows 10 rendszerű számítógépekre való bejelentkezéshez. **Nincs konfigurálva** (alapértelmezés) az operációs rendszer alapértelmezését használja, ami megakadályozhatja, hogy a Windows Hello Companion-eszközök a Windows rendszerrel hitelesítsék magukat.

  [Hitelesítés/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Webes bejelentkezés**: lehetővé teszi a Windows bejelentkezési támogatását a nem ADFS (Active Directory összevonási szolgáltatások (AD FS)) összevont szolgáltatóknál, például Security ASSERTION MARKUP Language (SAML). Az SAML olyan biztonságos jogkivonatokat használ, amelyek egy egyszeri bejelentkezési (SSO) élményt biztosítanak a webböngészőknek. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): az operációs rendszer alapértelmezett beállításait használja az eszközön.
  - **Engedélyezve**: a webes hitelesítőadat-szolgáltató engedélyezve van a bejelentkezéshez.
  - **Letiltva**: a webes hitelesítőadat-szolgáltató le van tiltva a bejelentkezéshez.

  [Hitelesítés/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Előnyben részesített Azure ad-bérlői tartomány**: adjon meg egy meglévő tartománynevet az Azure ad-szervezetben. Ha a tartomány felhasználói bejelentkeznek, nem kell beírniuk a tartománynevet. Például írja be a következőt: `contoso.com`. A `contoso.com` tartományba tartozó felhasználók a saját felhasználónevével (például `abby`) jelentkezhetnek be `abby@contoso.com`helyett.

  [Hitelesítés/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Alkalmazásonkénti adatvédelmi kivételek

Olyan alkalmazásokat adhat hozzá, amelyeknek az "alapértelmezett adatvédelem" beállítástól eltérő adatvédelmi viselkedéssel kell rendelkeznie.

- **Csomag neve: alkalmazáscsomag**-család neve.
- **Alkalmazás neve**: az alkalmazás neve.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: megadhatja, hogy az alkalmazás elérheti-e a felhasználónevet, a képet és a kapcsolattartási adatokat.
- **Háttérbeli alkalmazások**: megadhatja, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: annak megadása, hogy az alkalmazás elérheti-e a naptárat.
- **Híváslista**: megadhatja, hogy az alkalmazás elérheti-e a hívások előzményeit.
- **Kamera**: határozza meg, hogy az alkalmazás elérheti-e a kamerát.
- **Névjegyek**: megadhatja, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **E-mail**: megadhatja, hogy az alkalmazás hozzáférhessen-e e-mailekhez.
- **Hely**: határozza meg, hogy az alkalmazás hozzáférhet-e a hely adataihoz.
- **Üzenetküldés**: megadhatja, hogy az alkalmazás képes-e SZÖVEGES vagy MMS-üzenetek olvasására és küldésére.
- **Mikrofon**: határozza meg, hogy az alkalmazás használhatja-e a mikrofont.
- **Mozgás**: megadhatja, hogy az alkalmazás hozzáférhet-e az eszköz mozgási adataihoz.
- **Értesítések**: megadhatja, hogy az alkalmazás hozzáférhet-e az értesítésekhez.
- **Telefon**: határozza meg, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Rádiók**: egyes alkalmazások rádiókat (például Bluetooth) használnak az eszközön az eszközök küldéséhez és fogadásához, valamint a rádiók be-és kikapcsolásához. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: megadhatja, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: válassza ki, hogy az alkalmazás használhat-e megbízható eszközöket. A megbízható eszközök a már csatlakoztatott hardverek vagy az eszközhöz tartozó hardverek. Használjon például TV-ket, kivetítőket és így tovább, mint a megbízható eszközök.
- **Visszajelzés és diagnosztika**: megadhatja, hogy az alkalmazás hozzáférhet-e a diagnosztikai adatokhoz.
- **Szinkronizálás eszközökkel**: válassza ki, hogy az alkalmazás képes-e automatikusan megosztani és szinkronizálni az adatokat olyan vezeték nélküli eszközökkel, amelyek nem kifejezetten párosítva vannak az eszközzel.

## <a name="personalization"></a>Személyre szabás

Ezek a beállítások a [megszemélyesítési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Asztali háttérkép URL-címe (csak asztali**verzióban): adja meg a Windows asztali háttérképként használni kívánt. jpg,. jpeg vagy. png formátumú kép URL-címét. A felhasználók nem módosíthatják a képet. Például írja be a következőt: `https://contoso.com/logo.png`.

## <a name="printer"></a>Nyomtató

- **Nyomtatók**: a hozzáadott helyi nyomtatók listája.
- **Alapértelmezett nyomtató**: állítsa be az alapértelmezett nyomtatót.
- **Felhasználói hozzáférés új nyomtatók hozzáadásához**: engedélyezi vagy letiltja a helyi nyomtatók használatát.

## <a name="privacy"></a>Személyes adatok védelme

Ezek a beállítások az [adatvédelmi házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Bevitel személyre szabása**: a **Letiltás** megakadályozza a hang használatát a diktáláshoz, valamint a Cortana és más, a Microsoft felhőalapú beszédfelismerést használó alkalmazásokkal való kommunikációhoz. A szolgáltatás le van tiltva, és a felhasználók a beállítások használatával nem engedélyezhetik online beszédfelismerést. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a választást. Ha engedélyezi ezeket a szolgáltatásokat, a Microsoft hangadatokat gyűjthet a szolgáltatás fejlesztéséhez.
- **A párosítási és adatvédelmi felhasználói beleegyezési kérések automatikus elfogadása**: válassza az **Engedélyezés lehetőséget** , hogy a Windows automatikusan fogadja a párosítási és adatvédelmi hozzájárulási üzeneteket az alkalmazások futtatásakor. **Nincs konfigurálva** (alapértelmezés) megakadályozza a párosítási és adatvédelmi felhasználói beleegyezési ablak automatikus elfogadását az alkalmazások megnyitásakor.
- **Felhasználói tevékenységek közzététele**: a **blokk** megakadályozza a tevékenységek hírcsatornájában a legutóbb használt erőforrások közös élményét és felderítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót, így az alkalmazások közzé tehetik a végfelhasználói tevékenységeket.
- **Csak helyi tevékenységek**: a **blokk** megakadályozza, hogy a csak a helyi tevékenységeken alapuló, a feladat-visszakapcsolásban lévő, a közelmúltban felhasznált erőforrások felderítését, valamint a feladat **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.

Beállíthatja, hogy az eszközön található összes alkalmazás hozzáférhessen. A kivételeket az alkalmazáson belüli **adatvédelmi kivételek**használatával is meghatározhatja az alkalmazások alapján.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: megadhatja, hogy az alkalmazás elérheti-e a felhasználónevet, a képet és a kapcsolattartási adatokat.
- **Háttérbeli alkalmazások**: megadhatja, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: annak megadása, hogy az alkalmazás elérheti-e a naptárat.
- **Híváslista**: megadhatja, hogy az alkalmazás elérheti-e a hívások előzményeit.
- **Kamera**: határozza meg, hogy az alkalmazás elérheti-e a kamerát.
- **Névjegyek**: megadhatja, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **E-mail**: megadhatja, hogy az alkalmazás hozzáférhessen-e e-mailekhez.
- **Hely**: határozza meg, hogy az alkalmazás hozzáférhet-e a hely adataihoz.
- **Üzenetküldés**: megadhatja, hogy az alkalmazás képes-e SZÖVEGES vagy MMS-üzenetek olvasására és küldésére.
- **Mikrofon**: határozza meg, hogy az alkalmazás használhatja-e a mikrofont.
- **Mozgás**: megadhatja, hogy az alkalmazás hozzáférhet-e az eszköz mozgási adataihoz.
- **Értesítések**: megadhatja, hogy az alkalmazás hozzáférhet-e az értesítésekhez.
- **Telefon**: határozza meg, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Rádiók**: egyes alkalmazások rádiókat (például Bluetooth) használnak az eszközön az eszközök küldéséhez és fogadásához, valamint a rádiók be-és kikapcsolásához. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: megadhatja, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: válassza ki, hogy az alkalmazás használhat-e megbízható eszközöket. A megbízható eszközök a már csatlakoztatott hardverek vagy az eszközhöz tartozó hardverek. Használjon például TV-ket, kivetítőket és így tovább, mint a megbízható eszközök.
- **Visszajelzés és diagnosztika**: válassza ki, hogy az alkalmazás képes-e hozzáférni a diagnosztikai adatokhoz.
- **Szinkronizálás eszközökkel** – Megadhatja, hogy az alkalmazás oszthat-e meg és szinkronizálhat-e adatokat automatikusan olyan vezeték nélküli eszközökkel, amelyek nincsenek kifejezetten párosítva az adott PC-vel, táblagéppel vagy telefonnal.

## <a name="projection"></a>Kivetítés

Ezek a beállítások a [WirelessDisplay házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Vezeték nélküli Display fogadók felhasználói bevitele**: a **Letiltás** megakadályozza a vezeték nélküli megjelenítési fogadók felhasználói bevitelét. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a vezeték nélküli kijelző számára a billentyűzet, egér, toll és érintéses adatok küldését a forrás eszközre.
- **Vetítés erre a számítógépre**: a **Letiltás** megakadályozza, hogy más eszközök megtalálják az eszközt a kivetítéshez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz felderíthető legyen, és képes legyen a projekt a zárolási képernyő feletti eszközre.
- **PIN-kód megkövetelése párosításhoz**: válassza a **szükséges** lehetőséget, hogy a rendszer mindig PIN-kódot kérjen a kivetítési eszközhöz való csatlakozáskor. **Nincs konfigurálva** (az alapértelmezett) nem igényel PIN-kódot az eszköz kivetítési eszközhöz való párosításához.

## <a name="reporting-and-telemetry"></a>Jelentéskészítés és telemetria

- **Használati adatok megosztása**: válassza ki az elküldött diagnosztikai adatok szintjét. A választható lehetőségek:
  - **Nincs konfigurálva**: a rendszer nem osztja meg az adatmegosztást.
  - **Biztonság**: a Windows biztonságosabbá tételéhez szükséges információk, beleértve a csatlakoztatott felhasználói élményre és telemetria, valamint a kártevő szoftver-eltávolítási eszközre és a Microsoft defenderre vonatkozó adatokat.
  - **Alapszintű**: alapszintű eszköz adatai, beleértve a minőséggel kapcsolatos adatokat, az alkalmazások kompatibilitását, az alkalmazás használati adatait és a biztonsági szintről származó adatokat.
  - **Bővített**: további elemzések, többek között a következők: hogyan használhatók a Windows, a Windows Server, a System Center és az alkalmazások, hogyan működnek, és milyen speciális megbízhatósági adatok, valamint az alapszintű és a biztonsági szintek adatai.
  - **Teljes**: minden olyan adat, amely a problémák azonosításához és javításához, valamint a biztonsági, alapszintű és továbbfejlesztett szintekről származó adatokhoz szükséges.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Microsoft Edge-böngészési adatok küldése Microsoft 365 Analyticsnek**: a szolgáltatás használatához a **használati adatok megosztásának** megadásával **bővíteni** vagy **megtelt**értékre kell állítani. Ez a szolgáltatás azt szabályozza, hogy a Microsoft Edge milyen adatokat küldjön a vállalati eszközök Microsoft 365 elemzéséhez egy konfigurált kereskedelmi AZONOSÍTÓval. A választható lehetőségek:
  - **Nincs konfigurálva**: az operációs rendszer alapértelmezését használja, amely nem küldi el a böngészési előzményeket.
  - **Csak intranetes adatküldés**: lehetővé teszi a rendszergazda számára az intranetes adatelőzmények küldését.
  - **Csak internetes adatküldés**: lehetővé teszi, hogy a rendszergazda internetes adatelőzményeket küldjön
  - **Intranetes és internetes adatküldés**: lehetővé teszi a rendszergazda számára az intranetes és az internetes adatelőzmények küldését

  [Böngésző/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Telemetria proxykiszolgáló**: adja meg egy proxykiszolgáló teljes tartománynevét (FQDN) vagy IP-címét a csatlakoztatott felhasználói élmények és telemetria-kérések továbbításához SSL (SSL) kapcsolat használatával. a következő formátumban: *kiszolgáló*:*port*. Ha a nevesített proxy nem sikerül, vagy ha a házirend engedélyezésekor nem adta meg a proxyt, a rendszer nem küldi el a csatlakoztatott felhasználói élményt és telemetria, és a helyi eszközön marad.

  Példák a formátumra:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

A módosítások mentéséhez válassza az **OK** gombot.

## <a name="search"></a>Keresés

Ezek a beállítások a [keresési házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)-t használják, amely a támogatott Windows-kiadásokat is felsorolja. 

- **Biztonságos Keresés (csak mobil)** : annak szabályozása, hogy a Cortana hogyan szűri a felnőtt tartalmat a keresési eredmények között. A választható lehetőségek:
  - **Felhasználó által definiált**: a végfelhasználók választhatják ki a saját beállításait.
  - **Szigorú**: a legmagasabb szintű szűrés a felnőtt tartalmakon.
  - **Mérsékelt**: mérsékelt szűrés a felnőtt tartalommal szemben. Az érvényes keresési eredmények nem szűrhetők.
- **Webes találatok megjelenítése a keresésben**: Ha a **blokk**értékre van állítva, a felhasználók nem kereshetnek, és a webes eredmények nem jelennek meg a keresésben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a webes keresést, és az eredmények megjelennek az eszközön.

## <a name="start"></a>Indítás

Ezek a beállítások a [Start Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.  

- **Start menü elrendezése**: az alapértelmezett indítási elrendezés felülbírálása és a Start menü testreszabása asztali eszközökön. Töltsön fel egy XML-fájlt, amely tartalmazza a testreszabásokat, beleértve az alkalmazások listájának sorrendjét és egyebeket. A felhasználók nem változtathatják meg a Start menü megadott elrendezését.
- **Webhelyek rögzítése a Start menüben**: képek importálása a Microsoft Edge-ből, amelyek hivatkozásként jelennek meg a Windows Start menüjében asztali eszközökhöz.
- **Alkalmazások rögzítésének feloldása a tálcán**: a Letiltás megakadályozza, hogy a felhasználók **kioldják** az alkalmazásokat a tálcáról. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az alkalmazások rögzítését a tálcáról.
- **Gyors felhasználói váltás**: a **Letiltás** megakadályozza, hogy a rendszer kijelentkezés nélkül, egyidejűleg bejelentkezett felhasználók között váltson át. **Nincs konfigurálva** (alapértelmezés) megjeleníti a felhasználói csempén a **kapcsoló felhasználóját** .
- **Leggyakrabban használt alkalmazások**: a **blokk** elrejti a leggyakrabban használt alkalmazásokat a Start menüben. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezés) a leggyakrabban használt alkalmazásokat jeleníti meg.
- **Nemrég hozzáadott alkalmazások**: **blokkolja** a nemrég hozzáadott alkalmazások elrejtését a Start menüben. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezés) megjeleníti a legutóbb hozzáadott alkalmazásokat a Start menüben.
- Kezdőképernyő **mód**: válassza ki, hogyan jelenjen meg a kezdőképernyő. A választható lehetőségek:
  - **Felhasználó által definiált**: nem kényszeríti az indítás méretét. A felhasználók megadhatják a méretet.
  - **Teljes képernyő**: az indítás teljes teljes méretét kényszeríti.
  - **Nem teljes képernyő**: az indítás nélküli méret kényszerítése.
- A **legutóbb megnyitott elemek a Jump List menükben**: **letiltja** a legutóbbi Jump List lista elrejtése a Start menüben és a tálcán. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezett) a legutóbb megnyitott elemeket mutatja a jumplists-ben.
- Alkalmazások **listája**: válassza ki, hogyan jelenjenek meg a minden alkalmazás lista. A választható lehetőségek:
  - **Felhasználó által definiált**: nincs beállítás kényszerítve. A felhasználók kiválaszthatják, hogyan jelenjenek meg az alkalmazások listája az eszközön.
  - **Összecsukás**: az összes alkalmazás listájának elrejtése.
  - **Összecsukhatja és letilthatja a beállítások alkalmazást**: az összes alkalmazás listájának elrejtése és a beállítások alkalmazás **Start menüjében szereplő alkalmazások listájának** letiltása.
  - **Eltávolítja és letiltja a beállítások alkalmazást**: az összes alkalmazás listájának elrejtése, az összes alkalmazás eltávolítása gomb, valamint a beállítások alkalmazás **Start menüjében szereplő alkalmazások listájának** letiltása.
- **Főkapcsoló gomb**: a **Letiltás** elrejti a főkapcsoló gombot a Start menüben. **Nincs konfigurálva** (alapértelmezett) a főkapcsoló gombot jeleníti meg.
- **Felhasználói csempe**: a **blokk** elrejti a felhasználói csempét a Start menüben. **Nincs konfigurálva** (alapértelmezett) a felhasználói csempét jeleníti meg, és az alábbi beállításokat is megadja:
  - **Zárolás**: a **blokk** elrejti a **zárolási** lehetőséget a Start menü felhasználói csempén. **Nincs konfigurálva** (alapértelmezett) a **zárolási** beállítást mutatja.
  - **Kijelentkezés**: a **blokk** elrejti a kijelentkezési **lehetőséget a** Start menü felhasználói csempén. **Nincs konfigurálva** (alapértelmezés) megjeleníti a **kijelentkezési** lehetőséget.
- **Leállítás**: a Start menü főkapcsoló gombján a **Letiltás** elrejti a **frissítést, és** leállítja és **leállítja** a beállításokat. **Nincs konfigurálva** (alapértelmezés) ezeket a beállításokat jeleníti meg.
- **Alvó állapot**: a **Letiltás megakadályozza** , hogy a Start menü főkapcsoló gombján megjelenítse az **alvó üzemmódot** . **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Hibernált állapot**: a Start menü főkapcsoló gombján a **Letiltás** elrejti a **hibernálási** beállítást. **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Fiók váltása**: a **blokk** elrejti a **kapcsoló fiókot** a Start menü felhasználói csempén. **Nincs konfigurálva** (alapértelmezés) Ez a beállítás jelenik meg.
- **Újraindítási beállítások**: a **Letiltás** a Start menü főkapcsoló gombjára kattintva elrejti a **frissítési és** újraindítási és **Újraindítási** beállításokat. **Nincs konfigurálva** (alapértelmezés) ezeket a beállításokat jeleníti meg.
- **Dokumentumok a Start**menüben: a Windows Start menüjének dokumentumok mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Letöltések a Start**menüben: a Windows Start menü letöltések mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Fájlkezelő a Start**menüben: a Windows Start menüjében található fájlkezelő elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Otthoni csoport a Start**menüben: az otthoni csoport parancsikonjának elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Zene a Start**menüben: a Windows Start menü zene mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Hálózat a Start**menüben: bejövő hálózati forgalom elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Személyes mappa a Start**menüben: személyes mappa elrejtése vagy megjelenítése a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Képek a Start**menüben: a Windows Start menüjében található képek mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Beállítások a Start**menüben: elrejtheti vagy megjelenítheti a beállítások parancsikont a Windows Start menüjében. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.
- **Videók a Start**menüben: a Windows Start menüjében található videók mappájának elrejtése vagy megjelenítése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a rendszer nem kényszeríti a beállítást. A felhasználók a parancsikon megjelenítéséhez vagy elrejtéséhez választanak.
  - **Elrejtés**: a parancsikon rejtett, és letiltja a beállítást a beállítások alkalmazásban.
  - **Megjelenítés**: a parancsikon megjelenik, és letiltja a beállítást a beállítások alkalmazásban.

## <a name="microsoft-defender-smart-screen"></a>Microsoft Defender intelligens képernyő

- **SmartScreen a Microsoft Edge-hez**: a **kötelező** kikapcsolja a Microsoft Defender SmartScreen szolgáltatást, és megakadályozza, hogy a felhasználók bekapcsolják azt. **Nincs konfigurálva** (alapértelmezett) bekapcsolja a SmartScreen szolgáltatást. Segít megvédeni a felhasználókat az esetleges fenyegetésektől, és megakadályozhatja a felhasználók számára a kikapcsolást.

  A Microsoft Edge a Microsoft Defender SmartScreen (bekapcsolt) használatával gondoskodik a felhasználók számára az esetleges adatlopó csalások és kártevő szoftverek elleni védelemről.

  [Böngésző/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Rosszindulatú hely elérése**: a **Letiltás** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Microsoft Defender SmartScreen szűrő figyelmeztetéseit, és blokkolja azokat a helyről. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy figyelmen kívül hagyják a figyelmeztetéseket, és folytassa a webhelyet.

  [Böngésző/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- Nem **ellenőrzött fájlok letöltése**: a **Letiltás** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Microsoft Defender SmartScreen szűrő figyelmeztetéseit, és letiltja a nem ellenőrzött fájlok letöltését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók figyelmen kívül hagyják a figyelmeztetéseket, és folytassa a nem ellenőrzött fájlok letöltését.

  [Böngésző/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows Reflektorfény

Ezek a beállítások az [Experience Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Windows Spotlight**: a **Letiltás** kikapcsolja a Windows reflektorfényt a zárolási képernyőn, a Windows-tippeket, a Microsoft fogyasztói funkcióit és az egyéb kapcsolódó funkciókat. Ha a cél az, hogy csökkentse a hálózati forgalmat az eszközökről, állítsa ezt a **blokkra**. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows reflektorfény funkcióinak használatát, és a végfelhasználók is vezérelhetik. Ha engedélyezve van, a következő beállításokat is engedélyezheti vagy letilthatja:

  - **Windows reflektorfény a zárolási képernyőn**: a **Letiltás** megakadályozza a Windows reflektorfényben az eszköz zárolási képernyőjén található információk megjelenítését. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt a funkciót.
  - **Harmadik féltől származó javaslatok a Windows reflektorfényben**: a **Letiltás** megakadályozza a Windows Reflektorfényben a nem a Microsoft által közzétett tartalmakat. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az alkalmazás-és tartalmi javaslatok használatát a Windows reflektorfényben lévő partnerek szoftvergyártói számára, például a zárolási képernyő Spotlight, a javasolt alkalmazások a Start menüben és a Windows-tippek.
  - **Fogyasztói funkciók**: a **Letiltás** kikapcsolja az általában csak a fogyasztóknak szóló tapasztalatokat, például az indítási javaslatokat, a tagsági értesítéseket, az alkalmazások telepítés utáni telepítését és a csempék átirányítását. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.
  - **Windows-tippek**: a **Letiltás** letiltja az előugró ablakokra vonatkozó tippeket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows-tippek megjelenítését.
  - **Windows reflektorfény a műveletközpontben**: a **Letiltás** megakadályozza a Windows reflektorfény értesítéseinek megjelenítését a műveleti központban. **Nincs konfigurálva** (alapértelmezés) a műveleti központban olyan értesítéseket jeleníthet meg, amelyek az alkalmazásokat és szolgáltatásokat javasolva segítik a felhasználókat a Windowsban.
  - **Windows reflektorfény személyre szabása**: a **Letiltás** megakadályozza, hogy a Windows a diagnosztikai adatok használatával testreszabott felhasználói élményt nyújtson. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Microsoft számára a diagnosztikai adatgyűjtés használatát, hogy személyre szabott ajánlásokat, tippeket és ajánlatokat biztosítson a felhasználók igényeinek kielégítésére.
  - **Windows üdvözlőprogram-élmény**: a **Letiltás** kikapcsolja a Windows reflektorfény Windows üdvözlőprogramjának funkcióját. A Windows üdvözlőprogramja nem jelenik meg, ha a Windows és az alkalmazásai frissítései és változásai vannak. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Windows üdvözlőprogram használatát, amely az új vagy frissített funkciókkal kapcsolatos felhasználói adatokat jeleníti meg.

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender víruskereső

Ezek a beállítások a [Defender Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)-t használják, amely a támogatott Windows-kiadásokat is felsorolja.

- **Valós idejű figyelés**: az **Engedélyezés** bekapcsolja a kártevők, kémprogramok és más nemkívánatos szoftverek valós idejű vizsgálatát. A felhasználók nem kapcsolhatják ki. 

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja ezt a funkciót, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **Viselkedés figyelése**: **engedélyezze** a működés közbeni figyelést, és ellenőrzi, hogy vannak-e gyanús tevékenységekre utaló ismert mintázatok az eszközökön. A felhasználók nem kapcsolhatják ki a viselkedés figyelését. 

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja a viselkedés figyelését, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowBehaviorMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **Hálózatvizsgáló rendszer (NIS)** : a NIS segítségével megvédheti az eszközöket a hálózati alapú biztonsági rések ellen. A Microsoft Endpoint Protection-központból származó ismert sebezhető pontok mintázatai alapján segít észlelni és blokkolni a rosszindulatú hálózati forgalmat.

  A hálózati védelem bekapcsolása és a hálózati blokkolás **engedélyezése** . A felhasználók nem kapcsolhatják ki. Ha ez a beállítás engedélyezve van, a felhasználók nem tudnak csatlakozni az ismert biztonsági rések eléréséhez.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja a NIS-t, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **Összes Letöltés ellenőrzése**: **engedélyezze** a beállítás bekapcsolása beállítást, és a Defender az internetről letöltött összes fájlt megvizsgálja. A felhasználók nem kapcsolhatják ki ezt a beállítást. 

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja ezt a beállítást, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowIOAVProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **A Microsoft webböngészőkben betöltött parancsfájlok vizsgálata**: **engedélyezze** a Defender számára az Internet Explorerben használt parancsfájlok vizsgálatát. A felhasználók nem kapcsolhatják ki ezt a beállítást. 

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja ezt a beállítást, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowScriptScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Végfelhasználói hozzáférés a defenderhez**: a **blokk** elrejti a Microsoft Defender felhasználói felületét a végfelhasználók számára. A Microsoft Defender összes értesítése is le van tiltva.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha letiltja a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer lehetővé teszi a felhasználóknak a Microsoft Defender felhasználói felületének felhasználói hozzáférését, és lehetővé teszik a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  Módosítás esetén a beállítás a felhasználó számítógépének következő újraindításakor lép érvénybe.

  [Defender/AllowUserUIAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **Biztonsági intelligencia frissítési időköze (órában)** : adja meg azt az időközt, amelyet a Defender az új biztonsági intelligenciát keres, 0-24-ból. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): a frissítések keresése 8 óránként.
  - Ne legyen **pipa**: a Defender nem keres új biztonsági intelligenciával kapcsolatos frissítéseket.
  - **1-24**: a `1` óránként ellenőrzi az ellenőrzést, `2` ellenőrzi, hogy naponta, `24`-e az ellenőrzések és így tovább.
  
  [Defender/SignatureUpdateInterval CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- A **fájl-és program-tevékenység figyelése**: engedélyezi a Defender számára a fájl-és program-tevékenységek figyelését az eszközökön. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): az összes fájl figyelése
  - **Figyelés letiltva**
  - **Az összes fájl figyelése**
  - **Csak a bejövő fájlok figyelése**
  - **Csak a kimenő fájlok figyelése**

  [Defender/RealTimeScanDirection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **Karanténba helyezett kártevők törlése előtt**: a megoldott kártevő szoftverek nyomon követése a megadott napok számával, így manuálisan is ellenőrizhetők a korábban érintett eszközök. Ha a `0`napok számát állítja be, a kártevő a karantén mappában marad, és a rendszer nem távolítja el automatikusan. Ha `90`re van állítva, a karanténba helyezett elemek a rendszeren 90 napig tárolódnak, majd el lesznek távolítva.

  [Defender/DaysToRetainCleanedMalware CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **CPU-használat korlátozása vizsgálat során**: korlátozza a megvizsgálható CPU mennyiségét, `0`tól `100`ig.
- **Archív fájlok vizsgálata**: **engedélyezze** a Defender bekapcsolását, hogy az archivált fájlokat, például zip-vagy cab-fájlokat vizsgálja. A felhasználók nem kapcsolhatják ki ezt a beállítást.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja ezt a vizsgálatot, és lehetővé teszi a felhasználók számára a módosítást.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowArchiveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **Beérkező levelek ellenőrzése**: **engedélyezheti** , hogy a Defender az eszközre érkező e-mail-üzeneteket vizsgálja. Ha engedélyezve van, a motor elemzi a postaládát és a levelezési fájlokat, hogy elemezze a levél törzsét és a mellékleteket. A. pst (Outlook), a. dbx, a. MBX, a MIME (Outlook Express) és a BinHex (Mac) formátumok is beolvashatók.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer kikapcsolja ezt a vizsgálatot, és lehetővé teszi a felhasználók számára a módosítást.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowEmailScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**: a teljes vizsgálat során a bekapcsolja a Defender cserélhető meghajtókon való vizsgálatának **bekapcsolását** . A felhasználók nem kapcsolhatják ki ezt a beállítást.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer lehetővé teszi a Defender számára a cserélhető meghajtók, például az USB-stickek vizsgálatát, és lehetővé teszi a felhasználók számára a beállítás módosítását.

  A gyors vizsgálat során előfordulhat, hogy a cserélhető meghajtók továbbra is megtekinthetők.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowFullScanRemovableDriveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **Leképezett hálózati meghajtók ellenőrzése teljes vizsgálat során**: az engedélyezés a Defender által leképezett hálózati meghajtókon lévő fájlok vizsgálatát is **lehetővé teszi** . Ha a meghajtón található fájlok írásvédettek, a Defender nem tudja eltávolítani a bennük talált kártevőket. A felhasználók nem kapcsolhatják ki ezt a beállítást.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer bekapcsolja ezt a funkciót, és lehetővé teszi a felhasználók számára a módosítását.

  A gyors vizsgálat során a csatlakoztatott hálózati meghajtók továbbra is megtekinthetők.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowFullScanOnMappedNetworkDrives CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **Hálózati mappákból megnyitott fájlok vizsgálata**: az engedélyezés a (z) **lehetővé teszi** , hogy a Defender megvizsgálja a hálózati mappákból vagy megosztott hálózati meghajtókról megnyitott fájlokat, például az UNC elérési útról elérhető fájlokat. A felhasználók nem kapcsolhatják ki ezt a beállítást. Ha a meghajtón található fájlok írásvédettek, a Defender nem tudja eltávolítani a bennük talált kártevőket.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer megvizsgálja a hálózati mappákból megnyitott fájlokat, és lehetővé teszi a felhasználók számára a módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowScanningNetworkFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **Cloud Protection**: **az** Microsoft Active Protection Service bekapcsolja az eszközt, hogy a felügyelt eszközökről információkat kapjon a kártevők tevékenységéről. A felhasználók nem változtathatják meg ezt a beállítást. 

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), az Intune nem érinti ezt a beállítást. Ha engedélyezi a beállítást, majd visszavált a **nincs konfigurálva**értékre, akkor az Intune a beállítást a korábban konfigurált állapotban hagyja. Alapértelmezés szerint az operációs rendszer lehetővé teszi az Microsoft Active Protection Service számára az információk fogadását, és lehetővé teszi a felhasználók számára a beállítás módosítását.

  Az Intune nem kapcsolja ki ezt a funkciót. A letiltásához használjon egyéni URI-t.

  [Defender/AllowCloudProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- A **felhasználók megkérdezése a minta beküldése előtt**: meghatározza, hogy a rendszer automatikusan elküldje-e a további elemzést igénylő potenciálisan kártékony fájlokat a Microsoftnak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): biztonságos minták automatikus küldése.
  - **Mindig legyen kérdés**
  - **Rákérdezés a személyes adatok elküldése előtt**
  - **Soha ne küldjön adatküldést**
  - Az **összes üzenet küldése az értesítés nélkül**: az adatküldés automatikusan megtörténik.

  [Defender/SubmitSamplesConsent CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **Napi gyors vizsgálat elvégzésének ideje**: válassza ki az órát a napi gyors vizsgálat futtatásához. A **nem konfigurált** napi vizsgálat nem fut. Ha további testreszabásra van szüksége, konfigurálja a **Rendszervizsgálat típusát a beállítás elvégzéséhez** .

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- A **végrehajtandó rendszervizsgálat típusa**: rendszervizsgálatot ütemezhet, beleértve a vizsgálat szintjét, valamint az ellenőrzés futtatásának napját és időpontját. A választható lehetőségek:
  - **Nincs konfigurálva**: a rendszer nem ütemezhet rendszervizsgálatot az eszközön. A végfelhasználók szükség szerint manuálisan futtathatják a vizsgálatokat, vagy az eszközeiket szeretnék.
  - **Letiltás**: letiltja az eszközön a rendszer vizsgálatát. Akkor válassza ezt a lehetőséget, ha olyan partner víruskereső megoldást használ, amely az eszközöket vizsgálja.
  - **Gyors vizsgálat**: megtekinti azokat a közös helyeket, amelyeken kártevők regisztrálhatók, például beállításkulcsok és ismert Windows indítási mappák.
    - **Ütemezett nap**: válassza ki a napot a vizsgálat futtatásához.
    - **Ütemezett időpont**: válassza ki az órát a vizsgálat futtatásához.
  - **Teljes vizsgálat**: megtekinti azokat a közös helyeket, amelyeken kártevők regisztrálhatók, valamint az eszközön található összes fájl és mappa is megvizsgálható.
    - **Ütemezett nap**: válassza ki a napot a vizsgálat futtatásához.
    - **Ütemezett időpont**: válassza ki az órát a vizsgálat futtatásához.

  > [!TIP]
  > Ez a beállítás ütközhet a **napi gyors vizsgálati beállítások végrehajtásához szükséges idővel** . Néhány javaslat:  
  >
  > - Ha napi gyors vizsgálatot kíván ütemezni, és hetente teljes vizsgálatot szeretne, akkor:
  >   1. Állítsa be az **időt a gyors vizsgálat napi beállításának elvégzéséhez** .
  >   2. A teljes vizsgálat **elvégzéséhez konfigurálja a rendszervizsgálat típusát** .
  > 
  > - Ha csak egy gyors vizsgálatot szeretne naponta (teljes vizsgálat nélkül), használja a következőt: **Time (napi gyors vizsgálat** vagy **rendszervizsgálati típus**) végrehajtása. Ha például a gyors vizsgálatot minden kedden 6 ÓRAKOR szeretné futtatni, konfigurálja a **Rendszervizsgálat típusát a beállítás végrehajtásához** .
  > 
  > - Ne konfigurálja az időt a **gyors vizsgálathoz**beállított **rendszervizsgálati típussal** egyidejűleg a **napi gyors vizsgálat végrehajtásához** . Ezek a beállítások ütközést okozhatnak, és előfordulhat, hogy a vizsgálat nem fut.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Vélhetően nemkívánatos alkalmazások észlelése**: válassza ki a védelem szintjét, ha a Windows vélhetően nemkívánatos alkalmazásokat észlel. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a Microsoft Defender vélhetően nemkívánatos alkalmazások elleni védelme le van tiltva.
  - **Letiltás**: a Microsoft Defender észleli a vélhetően nemkívánatos alkalmazásokat, és a rendszer letiltja az észlelt elemeket. Ezek az elemek az előzményekben más fenyegetésekkel együtt jelennek meg.
  - **Naplózás**: a Microsoft Defender vélhetően nemkívánatos alkalmazásokat észlel, de nem hajt végre műveletet. Áttekintheti a Microsoft Defender által az alkalmazásokkal kapcsolatos információkat. Keressen például a Microsoft Defender által a Eseménynaplóban létrehozott eseményekre.

  A vélhetően nemkívánatos alkalmazásokról további információt a [vélhetően nemkívánatos alkalmazások észlelése és blokkolása](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)című témakörben talál.

  [Defender/PUAProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **Észlelt kártevő-fenyegetésekkel kapcsolatos műveletek**: válassza ki, hogyan szeretné kezelni a kártevő-szálakat. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a Microsoft Defender számára a legjobb lehetőség kiválasztását. Ha az **Engedélyezés**lehetőségre van beállítva, válassza ki azokat a műveleteket, amelyeket az észlelt fenyegetési szinteknél el szeretne végezni: alacsony, közepes, magas és súlyos. A választható lehetőségek:
  
  - **Tisztítás**
  - **Karantén**
  - **Eltávolítás**
  - **Engedélyezés**
  - **Felhasználó által definiált**
  - **Tiltás**

  Ha a művelet nem lehetséges, a Microsoft Defender a legjobb lehetőséget választja a fenyegetés szervizelésének biztosítására. 

  [Defender/ThreatSeverityDefaultAction CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="microsoft-defender-antivirus-exclusions"></a>Microsoft Defender Antivirus-kizárások

- A vizsgálatokból **és a valós idejű védelemből kizárandó fájlok és mappák**: egy vagy több fájlt és mappát (például **\ elérésiút** vagy **%ProgramFiles%\Path\filename.exe** ) hoz létre a kizárások listájához. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a fájlokat és mappákat.
- A vizsgálatokból **és a valós idejű védelemből kizárandó**fájlkiterjesztések: adjon hozzá egy vagy több fájlkiterjesztés, például **jpg** vagy **txt** elemet a kizárások listájához. Az ilyen kiterjesztésű fájlok nem szerepelnek a valós idejű vagy ütemezett vizsgálatok során.
- A vizsgálatokból **és a valós idejű védelemből kizárandó folyamatok**: adjon hozzá egy vagy több **. exe**, **. com**vagy **. scr** típusú folyamatot a kizárások listájához. Ezek a folyamatok nem tartoznak valós idejű vagy ütemezett vizsgálatokba.

## <a name="next-steps"></a>További lépések

További technikai részleteket az egyes beállításokról és a Windows támogatott kiadásairól a [Windows 10 szabályzatkonfigurációs szolgáltatói referenciájában](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) talál.
