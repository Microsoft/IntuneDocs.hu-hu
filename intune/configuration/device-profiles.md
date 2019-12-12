---
title: Az eszköz szolgáltatásai és beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: A különböző Microsoft Intune-eszközök profiljainak áttekintése. A szolgáltatások, korlátozások, e-mailek, Wi-Fi, VPN, oktatás, tanúsítványok, a Windows 10, a BitLocker és a Microsoft Defender, a Windows Information Protection, a felügyeleti sablonok és az egyéni eszközök konfigurációs beállításainak frissítése a Azure Portal. Ezen profilok használatával felügyelheti és védetté teheti a vállalat adatait és eszközeit.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b74cdf29999bccdefaa94c84673b9ea89c335537
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74694947"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Szolgáltatások és beállítások alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Microsoft Intune olyan beállításokat és funkciókat kínál, amelyeket Ön engedélyezhet vagy tilthat le a vállalatához tartozó különböző eszközökön. Ezek a beállítások és funkciók hozzáadódnak a "konfigurációs profilokhoz". Létrehozhat profilokat különböző eszközökhöz és különböző platformokhoz, például iOS-, Android-és Windows-rendszerekhez is. Ezután az Intune-nal alkalmazza vagy "rendelje hozzá" a profilt az eszközökhöz.

A mobileszköz-kezelési (MDM) megoldás részeként ezeket a konfigurációs profilokat használhatja a különböző feladatok elvégzéséhez. Néhány példa profilok használatára:

- Windows 10-es eszközökön használjon az Internet Explorerben ActiveX-vezérlőket blokkoló profilt tartalmazó sablont.
- IOS-és macOS-eszközökön engedélyezze a felhasználók számára a AirPrint-nyomtatók használatát a szervezetben.
- A Bluetooth-hozzáférés engedélyezése vagy letiltása az eszközön.
- Hozzon létre egy Wi-Fi-vagy VPN-profilt, amely különböző eszközöket biztosít a vállalati hálózathoz való hozzáféréshez.
- Szoftverfrissítések kezelése, beleértve a telepítésük időpontját is.
- Futtathat egy Android-eszközt dedikált kioszk-eszközként, amely futtathat egy alkalmazást, vagy futtathat számos alkalmazást.

Ez a cikk áttekintést nyújt a létrehozott profilok különböző típusairól. Ezekkel a profilokkal engedélyezheti vagy megtilthatja az eszközök egyes funkcióinak használatát.

## <a name="administrative-templates"></a>Felügyeleti sablonok

A [Felügyeleti sablonok](administrative-templates-windows.md) több száz beállítást tartalmaznak, amelyek az Internet Explorer, a OneDrive, a távoli asztal, a Word, az Excel és más Office-programok számára konfigurálhatók.

Ezek a sablonok a Csoportházirendhez hasonló beállítások egyszerűsített nézetét biztosítják a rendszergazdáknak, de 100%-os felhő-alapúak.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

## <a name="certificates"></a>Tanúsítványok

A [tanúsítványok](../protect/certificates-configure.md) az eszközökhöz rendelt megbízható, SCEP és PKCS tanúsítványokat konfigurálják. Ezek a tanúsítványok a Wi-Fi-, VPN-és e-mail-profilokat hitelesítik.

Ez a funkció a következőket támogatja: 

- Android:
- Vállalati Android
- iOS/iPadOS
- macOS
- WVPN-profilokdows Phone 8.1
- Windows 8.1
- Windows 10 és újabb

## <a name="custom-profile"></a>Egyéni profil

Az [Egyéni beállítások](custom-settings-configure.md) lehetővé teszik a rendszergazdák számára az Intune-ba nem beépített eszközbeállítások hozzárendelését. Az androidos eszközökön OMA-URI értékeket adhat meg. iOS-eszközökön importálható egy, az Apple Configuratorban létrehozott konfigurációs fájl.

Ez a funkció a következőket támogatja:

- Android:
- Vállalati Android
- iOS/iPadOS
- macOS
- WVPN-profilokdows Phone 8.1

## <a name="delivery-optimization"></a>Teljesítésoptimalizálás

A [kézbesítés optimalizálása](delivery-optimization-windows.md) jobb élményt nyújt a szoftverfrissítések kézbesítéséhez. Ezek a beállítások a **szoftverfrissítések** > **Windows 10-es frissítési kör** beállításait használják.

Ezekkel a beállításokkal szabályozhatja, hogy a rendszer hogyan töltse le a szoftverfrissítéseket a szervezet eszközeire. Megadhatja például, hogy a felhasználók megkapják a saját frissítéseiket, vagy egy eszköz profiljában a kézbesítési optimalizálás Cloud Services használatával frissítéseket szerezzenek be.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

## <a name="device-features"></a>Eszközfunkciók

Az [eszköz szolgáltatásai](device-features-configure.md) vezérlik az iOS-és MacOS-eszközök funkcióit, például a AirPrint, az értesítéseket és a zárolási képernyő üzeneteit.

Ez a funkció a következőket támogatja:

- iOS/iPadOS
- macOS

## <a name="device-firmware-configuration-interface"></a>Eszköz belső vezérlőprogram-konfigurációs felülete

Az [eszköz belső vezérlőprogram-konfigurációs felülete](device-firmware-configuration-interface-windows.md) (DFCI) lehetővé teszi a rendszergazdák számára az UEFI (BIOS) beállítások engedélyezését vagy letiltását az Intune használatával. Ezekkel a beállításokkal fokozhatja a biztonságot a belső vezérlőprogram szintjén, ami általában rugalmasabb a kártékony támadásokkal szemben.

Ez a funkció a következőket támogatja:

- Windows 10 1809 és újabb verziók a támogatott belső vezérlőprogram-on

## <a name="device-restrictions"></a>Eszközkorlátozások

Az [eszközkorlátozásokkal](device-restrictions-configure.md) kezelhető a biztonság, a hardver, az adatmegosztás és az eszközök több beállítása. Létrehozható például egy olyan eszközkorlátozási profil, amely megakadályozza, hogy az iOS-eszközök felhasználói használják az eszköz kameráját. 

Ez a funkció a következőket támogatja:

- Android:
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 és újabb
- Windows 10 Team

## <a name="edition-upgrade"></a>Kiadásfrissítés

A [Windows 10 kiadásfrissítések](edition-upgrade-configure-windows-10.md) lehetővé teszi a Windows 10 egyes verzióit futtató eszközök újabb kiadásra történő automatikus frissítését.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

## <a name="education"></a>Oktatás

Az [Oktatási beállítások – Windows 10](education-settings-configure.md) segítségével konfigurálhatja a [Windows Vizsga alkalmazás](https://education.microsoft.com/gettrained/win10takeatest) beállításait. A beállítások konfigurálásakor az eszközön a vizsga befejezéséig nem futhat másik alkalmazás.

Az [Oktatási beállítások – iOS](../fundamentals/education-settings-configure-ios-shared.md) az iOS-es Osztályterem alkalmazás segítségével lehetővé teszi az oktatási folyamat és a diákok eszközeinek irányítását az osztályteremben. Az iPad eszközöket úgy is konfigurálhatja, hogy sok diák megoszthat egyetlen eszközt.

## <a name="email"></a>E-mail

Az [e-mail-beállítások](email-settings-configure.md) az Exchange ActiveSync e-mail beállításait az eszközökön létrehozzák, hozzárendelik és figyelik. Az e-mail-profilok segítenek a konzisztencia, a támogatási hívások csökkentése és a végfelhasználók számára a személyes eszközökön a vállalati e-mailek elérésében, a szükséges beállítások megadása nélkül. 

Ez a funkció a következőket támogatja: 

- Android:
- Vállalati Android
- iOS/iPadOS
- WVPN-profilokdows Phone 8.1
- Windows 10 és újabb

## <a name="endpoint-protection"></a>Endpoint Protection

[A Windows 10-es Endpoint Protection-beállításai](../protect/endpoint-protection-windows-10.md) a BitLocker és a Microsoft Defender beállításainak konfigurálását végzik a Windows 10-es eszközökön.

A Microsoft Defender komplex veszélyforrások elleni védelem (WDATP) a Microsoft Intune használatával történő bevezetéséhez lásd: [végpontok konfigurálása mobileszköz-kezelési (Mdm) eszközökkel](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm).

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

## <a name="esim-cellular---public-preview"></a>eSIM-kártya – Nyilvános előzetes verzió

a [eSIM celluláris profilok](esim-device-configuration.md) lehetővé teszi, hogy a rendszergazdák a felügyelt eszközökön konfiguráljanak mobil adatcsomagokat az internetre és az adatelérésre. Miután beolvasta az aktiválási kódokat a mobil üzemeltetőjétől, az Intune használatával importálja ezeket az aktiválási kódokat, majd hozzárendelheti a eSIM-kompatibilis eszközökhöz.

Ez a funkció a következőket támogatja:

- Windows 10 őszi alkotói frissítés, vagy későbbi verzió

## <a name="extensions"></a>Bővítmények

A [kernel-bővítmények](kernel-extensions-overview-macos.md) lehetővé teszik a rendszergazdák számára, hogy a MacOS-eszközökön a kernel szintjén szolgáltatásokat és programokat adjanak hozzá. Konfigurálja ezeket a beállításokat egy adott fejlesztőtől vagy partnertől származó összes bővítmény megbízhatóságához, vagy engedélyezze a megadott kernel-bővítményeket.

Ez a funkció a következőket támogatja:

- macOS

## <a name="identity-protection"></a>Identity protection

Az [Identity protection](../protect/identity-protection-configure.md) vezérli a vállalati Windows Hello felületet Windows 10 vagy Windows 10 Mobile rendszerű eszközökön. Ezeknek a beállításoknak a konfigurálásával teheti elérhetővé a vállalati Windows Hellót a felhasználók és eszközök számára, és így adhatja meg az eszközök PIN-kódjaira és a kézmozdulatokra vonatkozó követelményeket.  

Ez a funkció a következőket támogatja:  

- Windows 10 és újabb
- Windows Holographic for Business  

## <a name="kiosk"></a>Kioszkmód

A teljes [képernyős beállítások](kiosk-settings.md) profil egy eszköz futtatására, illetve számos alkalmazás futtatására van konfigurálva. A teljes képernyőn más funkciókat, többek között start menüt és webböngészőt is testre szabhat.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

A kioszk beállításai az [Android](device-restrictions-android.md#kiosk), az [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)és az [iOS](device-restrictions-ios.md#kiosk)rendszerű eszközök korlátozásai is elérhetők.

## <a name="oemconfig"></a>OEMConfig

A [OEMConfig](android-oem-configuration-overview.md) olyan szabvány, amely lehetővé teszi az OEM-ek (eredeti berendezésgyártók) és a EMMs (nagyvállalati mobilitási felügyelet) számára, hogy szabványosított módon hozzon létre és támogassa az Android Enterprise-eszközökön. A OEMConfig használatával az OEM létrehoz egy sémát, amely a SZÁMÍTÓGÉPGYÁRTÓ által meghatározott felügyeleti funkciókat definiálja, és beágyazza azt a Google Play szolgáltatásba feltöltött alkalmazásba. Az Intune beolvassa a sémát az alkalmazásból, lehetővé teszi az Intune-rendszergazdák számára a séma beállításainak konfigurálását.

Ez a funkció a következőket támogatja:

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>PowerShell-parancsprogramok

A [Windows 10-es eszközökön futó PowerShell-parancsfájlok](../apps/intune-management-extension.md) az Intune felügyeleti bővítmény használatával töltik fel a PowerShell-parancsfájlokat az Intune-ban, majd ezeket a parancsfájlokat futtatják az eszközökön. Azt is láthatja, hogy mire van szükség a bővítmény használatához, az Intune-hoz való hozzáadásához és egyéb fontos információkhoz.


Ez a funkció a következőket támogatja:

- Windows 10 és újabb
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>Többfelhasználós megosztott eszköz

A [Windows 10](shared-user-device-settings-windows.md) és [a Windows holografikus for Business](shared-user-device-settings-windows-holographic.md) magában foglalja az eszközök több felhasználóval, más néven megosztott eszközökkel vagy megosztott számítógépekkel való felügyeletének beállításait. Amikor egy felhasználó bejelentkezik az eszközre, kiválaszthatja, hogy a felhasználó módosíthatja-e az alvó üzemmód beállításait, vagy mentheti a fájlokat az eszközön. Egy másik példában a tárhely mentéséhez létrehozhat egy profilt, amely törli az inaktív hitelesítő adatokat a Windows HoloLens-eszközökről.

Ezek a megosztott többfelhasználós eszközbeállítások lehetővé teszik, hogy a rendszergazda vezérelje az eszköz egyes funkcióit, és kezelje ezeket a megosztott eszközöket az Intune-nal.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb
- Windows Holographic for Business

## <a name="update-policies"></a>Frissítési szabályzatok

Az [iOS-es frissítési szabályzatok](../protect/software-updates-ios.md) az iOS-eszközökön telepítendő szoftverfrissítésekre vonatkozó iOS-es szabályzatok létrehozását és hozzárendelését mutatják be. A telepítés állapotát is áttekintheti.

A Windows-eszközök frissítési házirendjeivel kapcsolatban lásd: [kézbesítési optimalizálás](delivery-optimization-windows.md). 

Ez a funkció a következőket támogatja:

- iOS/iPadOS

## <a name="vpn"></a>VPN

A [VPN-beállítások](vpn-settings-configure.md) használatával a VPN-profilokat a vállalati felhasználókhoz és eszközökhöz rendelheti hozzá, így azok könnyen és biztonságosan kapcsolódhatnak a hálózathoz. 

A virtuális magánhálózatok (VPN) biztonságos távoli hozzáférést biztosítanak a felhasználóknak a vállalati hálózathoz. Az eszközök egy VPN-csatlakozási profil használatával kezdeményeznek kapcsolatot a VPN-kiszolgálóval. 

Ez a funkció a következőket támogatja: 

- Android:
- Vállalati Android
- iOS/iPadOS
- macOS
- WVPN-profilokdows Phone 8.1
- Windows 8.1
- Windows 10 és újabb

## <a name="wi-fi"></a>Wi-Fi

A [Wi-Fi-beállítások](wi-fi-settings-configure.md) a vezeték nélküli hálózat beállításait rendeli hozzá felhasználókhoz és eszközökhöz. A Wi-Fi-profil hozzárendelése után a felhasználók anélkül is hozzáférhetnek a céges Wi-Fihez, hogy ők maguk konfigurálnák azt. 

Ez a funkció a következőket támogatja: 

- Android:
- Vállalati Android
- iOS/iPadOS
- macOS
- Windows 8.1 (csak importálás)
- Windows 10 és újabb

## <a name="windows-information-protection-profile"></a>Windows információvédelem profil

A [Windows Információvédelem](../protect/windows-information-protection-configure.md) úgy segít védekezni az adatszivárgások ellen, hogy mindeközben nem avatkozik bele az alkalmazottak munkavégzésébe. Emellett segít a vállalati alkalmazások és az adatszivárgások elleni védelemben a vállalati tulajdonú eszközökön és az alkalmazottak által a munkahelyen használt személyes eszközökön a véletlen adatszivárgások ellen. A Windows Information Protection használata nem igényli a környezet vagy más alkalmazások módosítását.

Ez a funkció a következőket támogatja:

- Windows 10 és újabb

## <a name="zebra-mobility-extensions-mx"></a>Zebra mobilitási bővítmények (MX)

A [Zebra Mobility Extensions (MX)](android-zebra-mx-overview.md) lehetővé teszi a rendszergazdák számára a zebra-eszközök használatát és felügyeletét az Intune-ban. StageNow-profilokat hozhat létre a beállításokkal, majd az Intune használatával rendelheti hozzá és helyezheti üzembe ezeket a profilokat a zebra-eszközökön. A [StageNow-naplók és gyakori problémák](android-zebra-mx-logs-troubleshoot.md) egy nagyszerű erőforrás a profilok hibakereséséhez, és néhány lehetséges probléma a StageNow használatakor.

Ez a funkció a következőket támogatja:

- Android (mobilitási bővítmények)

## <a name="manage-and-troubleshoot"></a>Felügyelet és hibaelhárítás

[A profilok kezelésével](device-profile-monitor.md) ellenőrizheti az eszközök állapotát és a hozzárendelt profilokat. Az ütközéseket kiváltó beállítások, valamint az ezeket a beállításokat tartalmazó profilok megtekintésével is segítheti a problémák megoldását. A [gyakori problémák és megoldások](device-profile-troubleshoot.md) segítenek a rendszergazdáknak a profilok működésében. Leírja, hogy mi történik egy profil törlésekor, mi okozza az értesítések küldését az eszközökre, és így tovább.

## <a name="next-steps"></a>További lépések

Válassza ki a platformot, és kezdje el.
