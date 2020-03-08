---
title: Újdonságok a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Az Azure-beli Intune-portál újdonságai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb34a67539e1c2ed181189589aa3fc5b0e86fa97
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78893162"
---
# <a name="whats-new-in-microsoft-intune"></a>Újdonságok a Microsoft Intune-ban

Megtudhatja, milyen Újdonságok vannak a Microsoft Intune hetente. Megtalálhatja a [fontos megjegyzéseket](#notices), a [korábbi kiadásokat](whats-new-archive.md)és az [Intune szolgáltatás frissítéseinek kiadásával](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)kapcsolatos információkat is. 

> [!Note]
> A [havi frissítés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) akár három napot is igénybe vehet, és a következő sorrendben fog megjelenni:
>
> - 1\. nap: Ázsia és a Csendes-óceáni térség (APAC)
> - 2\. nap: Európa, Közel-Kelet, Afrika (EMEA)
> - 3\. nap: Észak-Amerika
> - 4\. nap +: az Intune a Government számára
>
> Egyes funkciók bevezetése több hetet igénybe vehet, így előfordulhat, hogy nem elérhetők a felhasználók számára az első héten.
>
> A kiadásban a közelgő funkciók listáját a [fejlesztés lapon](in-development.md) találja.

**RSS-hírcsatorna**: értesítést kap az oldal frissítésekor, ha a következő URL-címet másolja, és beillesztette a hírcsatorna-olvasóba: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-march-2-2020"></a>2020. március 2. hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="microsoft-endpoint-manager-tenant-attach-device-sync-and-device-actions---6317104-cm3555758--"></a>Microsoft Endpoint Manager-bérlő csatolása: eszköz-szinkronizálás és eszközök műveletei<!-- 6317104, CM3555758-->
A Microsoft Endpoint Manager egyetlen konzolon egyesíti a Configuration Manager és az Intune-t. Az 2002,2-Configuration Manager es Technical Preview verziótól kezdődően a Configuration Manager-eszközöket feltöltheti a Cloud Service-be, és műveleteket végezhet rajtuk a felügyeleti központban. További információ: [Configuration Manager Technical preview 2002,2-es verziójának szolgáltatásai](https://docs.microsoft.com/configmgr/core/get-started/2020/technical-preview-2002-2#bkmk_attach).

A frissítés telepítése előtt tekintse át a [Configuration Manager Technical Preview-cikket](https://docs.microsoft.com/configmgr/core/get-started/technical-preview) . Ez a cikk az általános követelményeket és korlátozásokat ismerteti a technikai előzetes verzió használatára, a verziók közötti frissítésre és a visszajelzések megadására vonatkozóan.

#### <a name="bulk-remote-actions--4576882--"></a>Tömeges távoli műveletek<!--4576882-->
Mostantól tömeges parancsokat is kiadhat a következő távoli műveletekhez: újraindítás, átnevezés, Autopilot alaphelyzetbe állítása, törlés és törlés. Az új tömeges műveletek megtekintéséhez lépjen a [Microsoft Endpoint Manager felügyeleti központ](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközök** > **minden eszköz** > **tömeges műveletek**.

#### <a name="all-devices-list-improved-search-sort-and-filter--6179023--"></a>Minden eszköz lista Továbbfejlesztett keresés, rendezés és szűrés<!--6179023-->
A minden eszköz lista javult a jobb teljesítmény, a keresés, a rendezés és a szűrés érdekében.

<!-- ########################## -->
## <a name="week-of-february-24-2020"></a>2020. február 24-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>a macOS Céges portál felhasználói élményének fejlesztése<!-- 5568987 -->
Javítottuk a macOS-eszközök regisztrálási élményét és a Mac Céges portál alkalmazást. A következőt fogja látni:
- Jobb Microsoft automatikus **frissítési** élmény a regisztráció során, amely biztosítja, hogy a felhasználók a céges portál legújabb verziójával rendelkezzenek.
- Továbbfejlesztett megfelelőség-ellenőrzési lépés a regisztráció során.
- A másolt incidensek azonosítóinak támogatása, így a felhasználók gyorsabban küldhetnek hibákat az eszközeiről a céges támogatási csapatnak.

A regisztrációval és a Mac Céges portál alkalmazással kapcsolatos további információkért lásd: [MacOS-eszköz regisztrálása a céges portál alkalmazás használatával](/intune-user-help/enroll-your-device-in-intune-macos-cp). 

#### <a name="app-protection-policies-for-better-mobile-now-supports-ios-and-ipados---6224512----"></a>Az App Protection-szabályzatok a Better Mobile-hoz már támogatja az iOS-és iPadOS<!-- 6224512  -->

2019 októberében az Intune app Protection-szabályzat hozzáadta a Microsoft Threat Defense-partnereinktől származó adatok használatát. Ezzel a frissítéssel mostantól egy alkalmazás-védelmi szabályzattal blokkolhatja, vagy szelektíven törölheti a felhasználókat a vállalati adatok alapján, az iOS-és iPadOS jobb mobil használatával.  További információ: [a Mobile Threat Defense-alkalmazás védelmi szabályzatának létrehozása az Intune](../protect/mtd-app-protection-policy.md)-nal.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="exports-from-the-all-devices-list--now-in-zipped-csv-format--6343117--"></a>Exportálás a minden eszköz listából most tömörített CSV-formátumban<!--6343117-->
Az **eszközökről** > az **összes eszköz** lapon lévő exportálás már tömörített CSV-formátumban van.


<!-- ########################## -->
## <a name="week-of-february-17-2020-2002-service-release"></a>Február 17-i hét, 2020 (2002-es kiadás)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424618---"></a>Microsoft Defender Advanced Threat Protection (ATP) alkalmazás macOS rendszerhez<!-- 5424618 -->
Az Intune segítségével egyszerűen üzembe helyezheti a macOS rendszerhez készült Microsoft Defender Advanced Threat Protection (ATP) alkalmazást a felügyelt Mac-eszközökön. További információ: a [Microsoft DEFENDER ATP hozzáadása MacOS-eszközökhöz Microsoft Intune](~/apps/apps-advanced-threat-protection-macos.md) és a [Microsoft Defender komplex veszélyforrások elleni védelem Mac rendszerhez](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac).  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111----"></a>A hálózati hozzáférés-vezérlés (NAC) engedélyezése a Cisco AnyConnect VPN-sel iOS-eszközökön<!-- 4860111  -->
IOS-eszközökön létrehozhat egy VPN-profilt, és különböző kapcsolattípust használhat, beleértve a Cisco AnyConnect-t (az**eszköz konfigurációjának** > **profiljait** , > **profil létrehozása** > **iOS** for platform > **VPN** a profil típusa > **Cisco AnyConnect** for kapcsolattípus). 

Engedélyezheti a hálózati hozzáférés-vezérlést (NAC) a Cisco AnyConnect használatával. A szolgáltatás használata:

1. A [Cisco Identity Services Engine rendszergazdai útmutatójában](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)a Cisco Identity Services Engine (ISE) az Azure-ban való konfigurálásához kövesse az **Microsoft Intune konfigurálása Mdm-kiszolgálóként** című témakör lépéseit.
2. Az Intune-eszköz konfigurációs profiljában válassza a **hálózati Access Control engedélyezése (NAC)** beállítást.

Az összes rendelkezésre álló VPN-beállítás megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS-eszközökön](../configuration/vpn-settings-ios.md)című témakört.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765----"></a>Sorozatszám az Apple MDM push-tanúsítvány oldalán<!--5947765  -->
Az Apple MDM push-tanúsítvány lapja most megjeleníti a sorozatszámot. A sorozatszám szükséges ahhoz, hogy újra hozzáférhessen az Apple MDM push-tanúsítványhoz, ha a tanúsítvány létrehozásához használt Apple ID azonosítóhoz való hozzáférés elvész. A sorozatszám megjelenítéséhez nyissa meg az **eszközök** > **iOS** > **iOS-regisztráció** > az **Apple Mdm push-tanúsítvány**lehetőséget.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689----"></a>Új frissítési ütemterv beállítások az operációs rendszer frissítéseinek beléptetéséhez a beléptetett iOS/iPadOS-eszközökön<!--5879689  -->
Az iOS/iPadOS operációs rendszer frissítéseinek ütemezésekor a következő lehetőségek közül választhat. Ez az Apple Business Manager vagy az Apple School Manager regisztrációs típusait használó eszközökre vonatkozik.
- Frissítés a következő bejelentkezéskor
- Frissítés az ütemezett idő alatt
- Frissítés az ütemezett időkereten kívül

Az utóbbi két lehetőség esetében több időablakot is létrehozhat.

Az új beállítások megjelenítéséhez nyissa meg a MEM >- **eszközök** > **iOS** **- > frissítési szabályzatok iOS/iPadOS > a** **profil létrehozása**lehetőséget.

#### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689----"></a>Válassza ki, hogy mely iOS-/iPadOS-frissítéseket szeretné leküldeni a regisztrált eszközökre<!--5879689  -->
Kiválaszthat egy adott iOS/iPadOS-frissítést (kivéve a legújabb frissítést) az Apple Business Manager vagy az Apple School Manager használatával beléptetett eszközökre való leküldéshez. Az ilyen eszközöknek rendelkeznie kell egy olyan eszköz-konfigurációs házirenddel, amely bizonyos számú nap elteltével késlelteti a szoftverfrissítés láthatóságát. Ennek a funkciónak a megtekintéséhez nyissa meg a MEM >- **eszközök** ** > ios** -es > **frissítési szabályzatok iOS/iPadOS > a** **profil létrehozása**lehetőséget.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="improved-intune-reporting-experience---3791418-----"></a>Továbbfejlesztett Intune jelentéskészítési élmény<!-- 3791418   -->
Az Intune mostantól továbbfejlesztett jelentéskészítési lehetőségeket kínál, beleértve az új jelentési típusokat, a jobb jelentési szervezetet, a célzottabb nézeteket, a jobb jelentési funkciókat, valamint a több konzisztens és kellő időben megjelenő adatát. A jelentéskészítési élmény a nyilvános előzetes verzióról a GA-ra (általánosan elérhető) vált. Emellett a GA-kiadás a honosítási támogatást, a hibajavításokat, a tervezési javításokat és az eszközök megfelelőségi adatainak a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)lévő csempén való összegzését is biztosítja. 

Az új Jelentéstípusok a következőkre összpontosítanak:
- **Működés** – a negatív állapotú friss rekordokat biztosít. 
- **Szervezet** – a teljes állapot szélesebb körű összegzését biztosítja.
- **Előzmények** – mintákat és trendeket biztosít egy adott időszakra vonatkozóan.
- **Specialist** – lehetővé teszi, hogy a nyers adatait használja saját egyéni jelentéseinek létrehozásához.

Az új jelentések első halmaza az eszköz megfelelőségére koncentrál. További információ: [Blog Microsoft Intune jelentési keretrendszer](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) és [Intune-jelentések](~/fundamentals/reports.md).

#### <a name="consolidated-the-location-of-security-baselines-in-the-ui---6177074-----"></a>A biztonsági alapkonfigurációk helyének konszolidálása a felhasználói felületen<!-- 6177074   -->
A biztonsági alapkonfigurációk [megkereséséhez](../protect/security-baselines.md) szükséges elérési utakat összevontuk a Microsoft Endpoint Manager felügyeleti központban a *biztonsági* ALAPKONFIGURÁCIÓk több felhasználói felületi helyről való eltávolításával. A biztonsági alapkonfigurációk megkereséséhez használja a következő elérési utat: **Endpoint security** > **biztonsági**alapkonfigurációk.

#### <a name="expanded-support-for-imported-pkcs-certificates---6044197-wnready---"></a>Az importált PKCS-tanúsítványok kibővített támogatása<!-- 6044197 WNReady -->
Bővítettük az [importált PKCS-tanúsítványok](../protect/certificates-imported-pfx-configure.md#supported-platforms) használatának támogatását az *Android Enterprise teljes körűen felügyelt eszközök*támogatásához. A PFX-tanúsítványok importálása általában az S/MIME titkosítási forgatókönyvek esetében használatos, ahol minden eszközön szükség van egy felhasználó titkosítási tanúsítványára, hogy az e-mail visszafejtése megtörténjen.

A PFX-tanúsítványok importálása a következő platformokon támogatott:
- Android – eszköz rendszergazdája
- Android Enterprise – teljes körűen felügyelt
- Android Enterprise-Work profil
- iOS
- Mac
- Windows 10

#### <a name="view-the-endpoint-security-configuration-for-devices---6206460----"></a>Az eszközök Endpoint Security-konfigurációjának megtekintése<!-- 6206460  -->
Frissítettük a lehetőség nevét a Microsoft Endpoint Manager felügyeleti központban, amely az [adott eszközre érvényes Endpoint Security-konfigurációk](../protect/security-baselines-monitor.md#view-endpoint-security-configurations-per-device)megtekintését teszi elérhetővé. A rendszer átnevezi a **végpontok biztonsági konfigurációját** , mert a biztonsági alapterveken kívül létrehozott további házirendeket is megjeleníti. Korábban a beállítás neve *biztonsági*alapkonfiguráció. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="intune-roles-user-interface-changes-coming--5801612-----"></a>Az Intune-szerepkörök felhasználói felületének módosításai elérkeznek<!--5801612   -->
A [Microsoft Endpoint Manager felügyeleti központ](https://go.microsoft.com/fwlink/?linkid=2109431) felhasználói felületének > **bérlői adminisztrációs** > **szerepkörei** sokkal jobb és intuitív kialakítást biztosítanak. Ez a felhasználói élmény ugyanazokat a beállításokat és adatokat tartalmazza, amelyeket most használ, de az új felület egy varázsló-szerű folyamatot alkalmaz.

<!-- ########################## -->
## <a name="week-of-february-17-2020"></a>2020. február 17-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="microsofts-new-office-app---5859926---"></a>Microsoft új Office-alkalmazás<!-- 5859926 -->
A Microsoft új Office-alkalmazásának letöltése és használata általánosan elérhető. Az Office-alkalmazás egy összevont felhasználói felület, amelyben a felhasználók egyetlen alkalmazáson belül dolgozhatnak a Word, az Excel és a PowerPoint használatával. Az alkalmazást megcélozhatja egy alkalmazás-védelmi szabályzattal, hogy biztosítsa, hogy az elérni kívánt információ védve legyen.

További információ: [az Intune app Protection-szabályzatok engedélyezése az Office Mobile Preview alkalmazással](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-how-to-enable-intune-app-protection-policies-with/ba-p/1045493).


<!-- ########################## -->

## <a name="week-of-february-10-2020"></a>2020. február 10-i hét

### <a name="windows-7-ends-extended-support--3042987---"></a>A Windows 7 kiterjesztett támogatást ér véget<!--3042987 -->
A Windows 7 2020 január 14-én elérte a kiterjesztett támogatás végét. Az Intune elavult támogatást biztosít a Windows 7 rendszert futtató eszközökhöz. A számítógép védelmének biztosítására szolgáló technikai segítségnyújtás és automatikus frissítés már nem érhető el. Frissítsen a Windows 10-es verzióra. További információ: [change blog post](https://aka.ms/Windows7_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>A Microsoft Edge 77-es és újabb verziói a Windows 10-es eszközökön<!-- 5843584 -->
Az Intune mostantól támogatja a Microsoft Edge 77-es és újabb verziójának eltávolítását a Windows 10-es eszközökön. További információ: a [Microsoft Edge for Windows 10 hozzáadása a Microsoft Intunehoz](~/apps/apps-windows-edge.md).

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Képernyő eltávolítva Céges portál, Android munkahelyi profil regisztrációja<!--6103987 -->
A **Mi a következő lépés?** a képernyőn el lett távolítva az Android munkahelyi profil beléptetési folyamata céges portál a felhasználói élmény egyszerűsítése érdekében. A frissített Android munkahelyi profil regisztrálási folyamatának megtekintéséhez nyissa meg az [androidos munkahelyi Profil regisztrálása](/intune-user-help/enroll-device-android-work-profile) című témakört.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>Céges portál alkalmazás teljesítményének növelése<!-- 6178652 -->
A Céges portál alkalmazás frissítve lett, hogy támogassa a ARM64 processzorokat használó eszközök jobb teljesítményét, például a Surface Pro X. korábban, az Céges portál emulált ARM32 módban működött. A 10.4.7080.0 és újabb verziókban a Céges portál alkalmazás natív módon van lefordítva a ARM64. További információ a Céges portál alkalmazásról: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>2020. január 27-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Intune-támogatás a Microsoft Edge 77-es verziójának további, a macOS-hez készült telepítési csatornájának telepítéséhez<!-- 5983950  -->
Microsoft Intune mostantól támogatja a további **stabil** üzembe helyezési csatornát a MacOS-hez készült Microsoft Edge alkalmazáshoz. A **stabil** csatorna az ajánlott csatorna, amellyel a Microsoft Edge nagyvállalati környezetben is üzembe helyezhető. Hat hetente frissül, és minden kiadás a **Beta** Channel szolgáltatással kapcsolatos fejlesztési funkciókat tartalmaz. A **stabil** és a **bétaverziós** csatornákon kívül az Intune egy **fejlesztői** csatornát is támogat. A nyilvános előzetes verzió a Microsoft Edge 77-es és újabb verzióihoz készült stabil és fejlesztői csatornákat kínál a macOS rendszerhez. Alapértelmezés szerint a böngésző automatikus frissítései be vannak kapcsolva. További információ: [Microsoft Edge hozzáadása MacOS-eszközökhöz Microsoft Intune használatával](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Intune Managed Browser kivonása<!--5728447 -->
A Intune Managed Browser megszűnik. Használja a Microsoft Edge-t a védett Intune-böngésző felhasználói felületéhez. További információkért lásd a "[művelet végrehajtása: a Microsoft Edge használata a védett Intune-böngészővel](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)" című szakaszt az alábbi [hirdetményekben](~/fundamentals/whats-new.md#notices) .

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>2020. január 20. (2001 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Felhasználói élmény változása alkalmazások Intune-beli hozzáadásakor<!-- 4705829   -->
Az alkalmazásoknak az Intune-on keresztül történő hozzáadásakor új felhasználói élmény jelenik meg. Ez a felhasználói élmény ugyanazokat a beállításokat és adatokat tartalmazza, amelyeket korábban már használt, de az új felhasználói felület a varázslóhoz hasonló folyamatot követ, mielőtt hozzáad egy alkalmazást az Intune-hoz. Ez az új felület egy felülvizsgálati oldalt is biztosít az alkalmazás hozzáadása előtt. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **alkalmazások** > **minden alkalmazás** lehetőséget, > a **Hozzáadás**elemet. További információt az [Alkalmazások hozzáadása a Microsoft Intune-hoz](~/apps/apps-add.md) című cikkben talál.

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Win32-alkalmazások újraindításának megkövetelése <!-- 5622282   -->
A sikeres telepítés után a Win32-alkalmazások újraindítására lehet szükség. Azt is megadhatja, hogy az újraindítás előtt mennyi idő elteltével (a türelmi időszakot) kell megadnia.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Felhasználói élmény változása az alkalmazások Intune-beli konfigurálásakor<!-- 4207990   -->
Az alkalmazás-konfigurációs szabályzatok Intune-ban való létrehozásakor új felhasználói élmény jelenik meg. Ez a felhasználói élmény ugyanazokat a beállításokat és adatokat tartalmazza, amelyeket korábban már használt, de az új felhasználói élmény egy varázsló-szerű folyamatot követ, mielőtt hozzáad egy szabályzatot az Intune-hoz. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **alkalmazások** > **alkalmazás-konfigurációs házirendek** > **Hozzáadás**elemet. További információ: [Microsoft Intune alkalmazás-konfigurációs szabályzatai](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Intune-támogatás a Windows 10-es telepítési csatornájának további Microsoft Edge-hez<!-- 5861774 -->
Microsoft Intune mostantól támogatja a további **stabil** üzembe helyezési csatornát a Microsoft Edge-hez (77-es és újabb verzió) a Windows 10 alkalmazáshoz. A **stabil** csatorna az ajánlott csatorna, amellyel a Microsoft Edge a Windows 10 rendszerhez széles körben üzembe helyezhető a vállalati környezetekben. Ez a csatorna hat hetente frissül, és minden kiadás, amely a **Beta** -csatornával kapcsolatos fejlesztési funkciókat tartalmaz. A **stabil** és a **bétaverziós** csatornákon kívül az Intune egy **fejlesztői** csatornát is támogat. További információ: [Microsoft Edge for Windows 10 – Alkalmazásbeállítások konfigurálása](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Továbbfejlesztett felhasználói felületi élmény az Exchange ActiveSync helyszíni összekötő felhasználói felületének konfigurálásakor<!-- 5695492   -->
Frissítettük az [Exchange ActiveSync helyszíni összekötő konfigurálásának](../protect/exchange-connector-install.md)élményét. A frissített felhasználói felület egyetlen ablaktáblát használ a helyszíni összekötők adatainak konfigurálásához, szerkesztéséhez és összefoglalásához. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Automatikus proxybeállítások hozzáadása Wi-Fi profilokhoz androidos vállalati munkahelyi profilokhoz<!-- 4490822   -->
Az Android Enterprise munkahelyi profil eszközein Wi-Fi profilok hozhatók létre. Ha a Wi-Fi Enterprise-típust választja, megadhatja a Wi-Fi-hálózaton használt bővíthető hitelesítési protokoll (EAP) típusát is.

Ha a vállalat típusát választja, megadhatja az automatikus proxybeállításokat is, beleértve a proxykiszolgáló URL-címét, például a `proxy.contoso.com`.

A konfigurálható aktuális Wi-Fi beállítások megjelenítéséhez nyissa meg a [Wi-Fi beállítások hozzáadása az Android Enterprise és az Android kioszkot futtató eszközökhöz Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md#work-profile-only).

A következőkre vonatkozik:
- Androidos vállalati munkahelyi profil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Android-regisztrációk letiltása az eszköz gyártója által<!--5197392  -->
Az eszközök regisztrálása az eszköz gyártójától függően tiltható le. Ez az Android-eszköz rendszergazdája és az Android Enterprise Work Profiles eszközökre vonatkozik. A regisztrációs korlátozások megjelenítéséhez nyissa meg a [Microsoft Endpoint Manager felügyeleti Központját](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközök** > a **regisztrációs korlátozásokat**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Az iOS/iPadOS regisztrációs típus létrehozása felhasználói felületének fejlesztései<!-- 6055005 -->
Az iOS/iPadOS felhasználói regisztrációja esetén a **regisztrációs típus létrehozása profil** **Beállítások** oldalát a rendszer egyszerűbbé tette, hogy javítsa a **regisztrációs típus** megválasztásának folyamatát, miközben megtartja ugyanazt a funkciót. Az új felhasználói felület megjelenítéséhez nyissa meg a [Microsoft Endpoint Manager felügyeleti Központját](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközök** > **ios** > **iOS-regisztráció** > **regisztrációs típusok** > **profil létrehozása** > **Beállítások** lapon. További információ: [felhasználói beléptetési profil létrehozása az Intune-ban](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Új információ az eszköz részleteiben<!-- 4471759 5604099  -->
A következő információk mostantól az eszközök **Áttekintés** lapján érhetők el:
- Memória kapacitása (a fizikai memória mennyisége az eszközön)
- Tárolási kapacitás (az eszközön található fizikai tárterület mennyisége) 
- CPU-architektúra

#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>iOS-megkerülés Aktiválási zár távoli művelet átnevezve Aktiválási zár letiltására <!--5904591  -->
A távoli művelet **megkerülése aktiválási zár** át lett nevezve a **aktiválási zár letiltására**. További információ: iOS- [aktiválási zár letiltása az Intune](../remote-actions/device-activation-lock-bypass.md)-nal.

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Windows 10 funkció-frissítési üzembe helyezés támogatása az Autopilot-eszközökhöz<!-- 5948137   -->
Az Intune mostantól támogatja az Autopilot regisztrált eszközök célzását a [Windows 10-es funkcióinak frissítésével](../protect/windows-update-for-business-configure.md#windows-10-feature-updates).

A Windows 10 szolgáltatás frissítési házirendjei nem alkalmazhatók az Autopilot-ből a Box Experience (OOBE) alkalmazásban, és csak az első Windows Update vizsgálatra érvényesek, miután egy eszköz befejezte az üzembe helyezést (ez általában egy nap).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>A Windows Autopilot üzembe helyezési jelentései (előzetes verzió) <!-- 3856172   -->
Egy új jelentés a Windows Autopilot szolgáltatáson keresztül üzembe helyezett összes eszközt részletezi. További információ: [Autopilot Deployment Report](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Új Intune beépített szerepkör Endpoint Security Manager<!--4253397   -->
Új Intune beépített szerepkör érhető el: a Endpoint Security Manager. Ez az új szerepkör lehetővé teszi a rendszergazdák számára, hogy teljes hozzáférést biztosítson az Intune-beli Endpoint Manager-csomóponthoz, és készen álljanak a többi területre való A szerepkör a "biztonsági rendszergazda" szerepkör kiterjesztése az Azure AD-ből. Ha jelenleg csak a globális rendszergazdák szerepkörrel rendelkezik, akkor nincs szükség módosításra. Ha szerepköröket használ, és szeretné, hogy a végponti Security Manager milyen részletességgel rendelkezik, akkor rendelje hozzá ezt a szerepkört, ha elérhetővé válik. A beépített szerepkörökről további információt a [szerepköralapú hozzáférés-vezérlés](role-based-access-control.md)című témakörben talál.

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>2020. január 6-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>S/MIME-támogatás az iOS-hez készült Microsoft Outlookhoz<!-- 2669398 -->
Az Intune támogatja az iOS-eszközökön az iOS rendszerhez használható S/MIME-aláírási és titkosítási tanúsítványok kézbesítését. További információ: [érzékenység címkézése és védelme az Outlookban az iOS és az Android rendszerhez](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Win32-alkalmazás tartalmának gyorsítótárazása a Microsoft csatlakoztatott gyorsítótár-kiszolgálóval<!-- 6030314 -->
Telepítheti a Microsoft csatlakoztatott gyorsítótár-kiszolgálót a Configuration Manager terjesztési pontokra az Intune Win32-alkalmazás tartalmának gyorsítótárazásához. További információ: a [Microsoft csatlakoztatott gyorsítótára Configuration Manager – az Intune Win32-alkalmazások támogatása](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>A Windows 10 felügyeleti sablonok (ADMX) profiljai mostantól támogatják a hatókör címkéit <!--5137390 -->
Mostantól a felügyeleti sablon profiljaihoz (ADMX) is hozzárendelhet hatókör-címkéket. Ehhez nyissa meg az **Intune** > **eszközök** > **konfigurációs profilok** > Válassza ki a felügyeleti sablonok profilt a lista > **Tulajdonságok** > **hatókör címkék**listájában. A hatókör címkével kapcsolatos további információkért lásd a [hatókör címkék társítása más objektumokhoz](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects)című témakört.

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>2019. december 30-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Személyes helyreállítási kulcs beolvasása a MEM titkosított macOS-eszközökről<!-- 4851745 -->
A végfelhasználók a saját helyreállítási kulcsát (FileVault-kulcs) az iOS Céges portál alkalmazás használatával kérhetik le. A személyes helyreállítási kulccsal rendelkező eszközt regisztrálni kell az Intune-ban, és az Intune-on keresztül kell titkosítani a FileVault-mel. Az iOS Céges portál alkalmazás használatával a végfelhasználók a titkosított macOS-eszközre a **helyreállítási kulcs beolvasása**lehetőségre kattintva lekérhetik a személyes helyreállítási kulcsot. A helyreállítási kulcsot az Intune-ból is lekérheti, ha kijelöli az **eszközök** > *a titkosított és regisztrált macOS-eszközt > a* **helyreállítási kulcs beolvasása**lehetőségre. További információ a FileVault: FileVault- [titkosítás MacOS rendszerhez](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>iOS-és iPadOS-felhasználó által licencelt VPP-alkalmazások<!-- 5619268 -->
A felhasználók által beléptetett iOS-és iPadOS-eszközök esetében a végfelhasználók többé nem fognak megjelenni az újonnan létrehozott, elérhetővé vált VPP-alkalmazásokkal. A végfelhasználók azonban továbbra is láthatják az összes felhasználó által licencelt VPP-alkalmazást a Céges portálon belül. További információ a VPP-alkalmazásokról: [Apple Volume Purchase program által vásárolt iOS-és MacOS-alkalmazások kezelése Microsoft Intune használatával](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>2019. december 23-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Figyelje meg, hogy a Windows 10 1703 (RS2) nem támogatott <!-- 5026679 -->
Az 2018. október 9-én kezdődően a Windows 10 1703 (RS2) a Microsoft platform-támogatását kiváltotta a Home, a Pro és a Pro for workstations kiadásban. A Windows 10-es nagyvállalati és oktatási kiadásaiban a Windows 10 1703 (RS2) 2019. október 8-án kikerült a platform-támogatásból. 2019. december 26-án a Windows Céges portál alkalmazás minimális verzióját fogjuk frissíteni a Windows 10 1709 (RS3) verzióra. A 1709 előtti verziót futtató számítógépek többé nem kapják meg az alkalmazás frissített verzióit a Microsoft Store. Korábban már tájékoztatták ezt a változást azokról az ügyfelekről, akik a Windows 10 régebbi verzióit kezelik az üzenetközpont használatával. További információ: a [Windows életciklusának](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)Adatlapja.

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>2019. december 16-i hét

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Felügyeleti sablonok frissítései a Windows 10-es eszközökhöz <!-- 5941568 -->

A Microsoft Edge, az Office és a Windows beállításainak vezérléséhez és kezeléséhez a Microsoft Intune ADMX-sablonjait használhatja. Az Intune-beli Felügyeleti sablonok a következő házirend-beállítással kapcsolatos frissítéseket hozta létre:

- A Microsoft Edge 78-es és 79-es verziójának támogatása.
- A tartalmazza a [Felügyeleti sablonok fájljaiban (ADMX/ADML) és az Office-testreszabási eszközben az office 365 ProPlus, az office 2019 és az office 2016-hez](https://www.microsoft.com/download/details.aspx?id=49030)készült 2019-es ADMX-fájlokat.

Az Intune-beli ADMX-sablonokkal kapcsolatos további információkért lásd: [Windows 10 sablonok használata a csoportházirend-beállítások konfigurálásához a Microsoft Intuneban](../configuration/administrative-templates-windows.md).

A következőkre vonatkozik:

- Windows 10 és újabb

## <a name="week-of-december-9-2019-1912-service-release"></a>December 9. és 2019. hét (1912 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrálás a Microsoft Edge-be felügyelt böngészési forgatókönyvek esetén<!-- 5173762 -->
Ahogy közeledünk a Intune Managed Browser kivonulásához, az alkalmazás-védelmi szabályzatok módosultak, hogy leegyszerűsítse a felhasználók az Edge-re való áthelyezéséhez szükséges lépéseket. Frissítettük az alkalmazás-védelmi házirend beállítását, amely **korlátozza a webes tartalom átvitelét más alkalmazásokkal** , hogy az a következők egyike legyen:

- Bármely alkalmazás
- Intune Managed Browser
- Microsoft Edge
- Nem felügyelt böngésző 

Ha kiválasztja a **Microsoft Edge**lehetőséget, a végfelhasználók a feltételes hozzáférési üzenetküldést fogják látni, hogy a Microsoft Edge szükséges a felügyelt böngészési forgatókönyvekhez. A rendszer arra kéri, hogy töltse le és jelentkezzen be a Microsoft Edge-be a HRE-fiókjával, ha még nem tette volna meg.  Ez azzal egyenértékű, hogy a MAM-kompatibilis alkalmazásokat az alkalmazás konfigurációs beállításával megcélozta, `com.microsoft.intune.useEdge` **igaz**értékre van állítva. A **házirend által felügyelt böngészőket** használó meglévő alkalmazás-védelmi szabályzatok mostantól **Intune Managed Browser** lesznek kiválasztva, és a viselkedésben nem fog megjelenni a változás. Ez azt jelenti, hogy a felhasználók láthatják, hogy az üzenetküldés a Microsoft Edge használatára van beállítva, ha a **useEdge** -alkalmazás konfigurációjának beállítása **true (igaz**). Javasoljuk, hogy a felügyelt böngészési forgatókönyveket használó ügyfelek az alkalmazás-védelmi szabályzatokat a **webes tartalmak más alkalmazásokkal való átadásának korlátozásával** használják, hogy a felhasználók lássák a Microsoft Edge-re való áttérésre vonatkozó megfelelő útmutatást, függetlenül attól, hogy az alkalmazás milyen alkalmazásokat indít el. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz<!-- 2576686  -->
Az Intune app Protection-szabályzatok (alkalmazás) Android-és iOS-eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Kiválaszthat egy lehetőséget (engedélyezheti, letilthatja a szervezeti adatforrásokat vagy letilthatja) annak megadásához, hogy a rendszer hogyan jelenítse meg a szervezeti fiókok értesítéseit a kiválasztott alkalmazás Ehhez a szolgáltatáshoz az alkalmazások támogatására van szükség, és előfordulhat, hogy az összes alkalmazás-kompatibilis alkalmazás esetében nem érhető el. Az iOS-es verzió 4.15.0 (vagy újabb) és az Outlook for Android 4.83.0 (vagy újabb) támogatja ezt a beállítást. A beállítás a konzolon érhető el, de a funkció a 2019. december 16. után lép érvénybe. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](../apps/app-protection-policy.md).

#### <a name="microsoft-app-icons-update--4677605----"></a>Microsoft-alkalmazás ikonjainak frissítése<!--4677605  -->
Az alkalmazás-védelmi házirendek és az alkalmazás-konfigurációs házirendek alkalmazás-célcsoportok ablaktábláján a Microsoft-alkalmazásokhoz használt ikonok frissültek.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Jóváhagyott billentyűzetek használatának megkövetelése Androidon<!--4761794  -->
Az alkalmazás védelmi szabályzatának részeként megadhatja a [**jóváhagyott billentyűzetek**](../apps/app-protection-policy-settings-android.md#data-protection) beállítását, amelyekkel felügyelheti, hogy mely Android-billentyűzetek használhatók a felügyelt Android-alkalmazásokkal. Amikor a felhasználó megnyitja a felügyelt alkalmazást, és még nem használ jóváhagyott billentyűzetet az alkalmazáshoz, a rendszer felszólítja, hogy váltson az eszközén már telepített jóváhagyott billentyűzetekre. Ha szükséges, a rendszer egy hivatkozást használ a jóváhagyott billentyűzet letöltésére a Google Play Áruházról, melyeket telepítheti és beállíthatja. A felhasználó csak akkor szerkesztheti a szöveges mezőket egy felügyelt alkalmazásban, ha az aktív billentyűzet nem a jóváhagyott billentyűzetek egyike.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Az iOS-, iPadOS-és macOS-eszközökön futó alkalmazásokhoz és webhelyekhez készült egyszeri bejelentkezések frissítése<!-- 4999578  -->
Az Intune több egyszeri bejelentkezési (SSO) beállítást adott hozzá az iOS-, iPadOS-és macOS-eszközökhöz. Mostantól konfigurálhatja a szervezete vagy az Ön személyazonossága szolgáltatója által írt átirányítási SSO-alkalmazások bővítményeit is. Ezekkel a beállításokkal zökkenőmentes egyszeri bejelentkezést állíthat be a modern hitelesítési módszereket (például OAuth és egy SAML2) használó alkalmazásokhoz és webhelyekhez. 

Ezek az új beállítások az egyszeri bejelentkezéses alkalmazás-bővítmények és az Apple beépített Kerberos-bővítménye (**eszközök** > **eszköz konfigurációja** > **profilok** > **create Profile** > **iOS/iPadOS** vagy **MacOS** a platform típusa > **eszköz funkciók** a profil típusa). 

A konfigurálható egyszeri bejelentkezéses alkalmazások teljes beállításainak megjelenítéséhez nyissa [meg az SSO](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) -t iOS-en és [SSO-on MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)rendszeren.

A következőkre vonatkozik:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Frissítettük az iOS-és iPadOS-eszközök két eszközre vonatkozó korlátozási beállításait a működésük kijavítani<!-- 5701352    -->
IOS-eszközökön létrehozhat olyan eszköz-korlátozási profilokat, amelyek **engedélyezik a hálózaton** KÍVÜLi PKI-frissítéseket, és BLOKKOLJA az USB-korlátozásos **üzemmódot** (**eszközök** > **eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** platform > **eszközre vonatkozó korlátozások** a profil típusa esetén). A jelen kiadás előtt a felhasználói felület beállításai és leírásai helytelenek voltak, és a rendszer kijavította azokat. Ettől a kiadástól kezdve a beállítások a következők:

**Nyilvános PKI-frissítések letiltása**: a **Letiltás** megakadályozza, hogy a felhasználók csak akkor fogadják a szoftverfrissítéseket, ha az eszköz csatlakoztatva van a számítógéphez. **Nincs konfigurálva** (alapértelmezett): lehetővé teszi, hogy az eszköz a számítógépekhez való csatlakozás nélkül kapjon szoftverfrissítéseket.
- Korábban ez a beállítás **lehetővé teszi**, hogy a következőképpen konfigurálja azt: Allow (Engedélyezés), amellyel a felhasználók az eszközök számítógéphez való csatlakoztatása nélkül kapják meg a szoftverfrissítéseket.
**USB-tartozékok engedélyezése, ha az eszköz zárolva van**: az **Engedélyezés** lehetővé teszi, hogy az USB-tartozékok egy órán keresztül zárolt eszközzel legyenek kicserélve. **Nincs konfigurálva** (az alapértelmezett) nem FRISSÍTI az USB-korlátozott üzemmódot az eszközön, és az USB-tartozékok le lesznek tiltva az adatoknak az eszközről történő átvitele esetén, ha egy órán keresztül zárolva van.
- Korábban ez a beállítás lehetővé teszi a következő konfigurálását: **Letiltás** a felügyelt eszközökön lévő USB-korlátozott mód letiltásához.

A konfigurálható beállítással kapcsolatos további információkért tekintse meg az [iOS-és iPadOS-eszközök beállításait, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

Ez a funkció az alábbiakra vonatkozik:

- Operációs rendszer/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686  -->
   > [!NOTE]
   > Ez a szolgáltatás késleltetve lett, de hamarosan megjelent.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>A tanúsítvány hitelesítő adatainak a felügyelt tárolóban való konfigurálásának tiltása a felhasználók számára az Android Enterprise-eszközök tulajdonosi eszközein<!-- 3311998 -->
Az androidos vállalati eszközök tulajdonosi eszközein beállíthat egy új beállítást, amely letiltja a felhasználók számára a tanúsítvány hitelesítő adatainak konfigurálását a felügyelt tárolóban (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **Android enterprise** for platform > **eszköz tulajdonosa csak > eszközök korlátozásai** > **felhasználók + fiókok**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="protected-wipe-action-now-available--51150000---"></a>A védett törlési művelet már elérhető<!--51150000 -->
Most lehetősége van arra, hogy az eszköz törlése műveletet használja az eszköz védett törlésének elvégzéséhez. A védett törlések megegyeznek a normál törlésekkel, azzal a kivétellel, hogy az eszköz kikapcsolásával nem lehet kikerülni őket. A védett adatok törlésével a rendszer addig próbálkozik az eszköz alaphelyzetbe állításával. Bizonyos konfigurációk esetében ez a művelet nem tudja újraindítani az eszközt. További információ: eszközök kivonása [vagy törlése](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Az eszköz áttekintő oldalához hozzáadott eszköz Ethernet MAC-címe<!--5562275 -->
Most már megtekintheti az eszköz Ethernet MAC-címeit az eszköz adatai oldalon (**eszközök** > **minden eszköz** > válasszon egy eszközt > **Áttekintés**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Továbbfejlesztett élmény egy megosztott eszközön, ha az eszközön alapuló feltételes hozzáférési szabályzatok engedélyezve vannak<!-- 1734096  -->
Továbbfejlesztettük a felhasználói élményt egy olyan megosztott eszközön, amely az eszközön alapuló feltételes hozzáférési házirendet célozza meg, ha ellenőrzi a felhasználó legújabb megfelelőségi értékelését a szabályzat érvényesítése során. További információkért tekintse meg a következő áttekintő cikkeket:
- [Az Azure áttekintése feltételes hozzáféréshez](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Intune-eszközök megfelelőségének áttekintése](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Tanúsítványokat tartalmazó eszközök kiépítése PKCS-tanúsítványok használatával<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Mostantól PKCS-alapú tanúsítvány-profilok használatával tanúsítványokat állíthat ki az Android for Work, iOS/iPadOS és Windows rendszerű *eszközökhöz* , ha a Wi-Fi-hez és a VPN-hez hasonló profilokhoz van társítva. Korábban ez a három platform csak a felhasználó-alapú tanúsítványokat támogatta, az eszköz-alapú támogatás pedig macOS-re korlátozódik.

> [!NOTE]
> A PKCS-tanúsítványok profiljai nem támogatottak a Wi-Fi profilokkal. Ehelyett használjon SCEP-tanúsítvány-profilokat, ha [EAP-típust](../configuration/wi-fi-settings-windows.md#enterprise-profile)használ.

Ha eszköz alapú tanúsítványt szeretne használni a támogatott platformok [PKCS-tanúsítványának létrehozása](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) közben, válassza a **Beállítások**lehetőséget. Ekkor megjelenik a **tanúsítvány típusának**beállítása, amely támogatja az eszköz vagy a felhasználó beállításait.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Központi naplók<!--5603185, 5697164 -->
Az új központosított naplózási szolgáltatás mostantól egyetlen oldalra gyűjti a naplókat az összes kategóriához. A naplók szűrésével lekérheti a keresett adatkérést. A naplók megtekintéséhez lépjen a **bérlői adminisztráció** > **naplók**elemre. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>A naplózási tevékenység részleteiben szereplő hatóköri címke adatai<!--5763534 -->
A naplózási tevékenység részletei mostantól tartalmazzák a hatókör címkével kapcsolatos információkat (a hatókör címkéit támogató Intune-objektumok esetében). További információ a naplókról: [események nyomon követésére és figyelésére szolgáló naplók használata](monitor-audit-logs.md).

<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019. december 2. hét

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Új Microsoft-végpont Configuration Manager közös felügyelet licencelése<!--5027281-->
A frissítési garanciával rendelkező ügyfelek a Windows 10 rendszerű számítógépeken az Intune közös felügyeletét anélkül érhetik el, hogy további Intune-licencet kellene vásárolnia a közös felügyelethez. Configuration Manager Az ügyfeleknek már nem kell egyéni Intune-/EMS-licenceket rendelniük a végfelhasználók számára a Windows 10 közös felügyeletéhez.
- A Configuration Manager által felügyelt és a közös felügyeletbe beléptetett eszközök szinte ugyanazok a jogosultságok, mint az Intune önálló MDM felügyelt számítógépei. Az alaphelyzetbe állítást követően azonban nem lehet újra kiépíteni az Autopilot használatával.
- Az Intune-ba beléptetett Windows 10-es eszközök más módon teljes Intune-licencet igényelnek.
- A más platformokon lévő eszközök továbbra is teljes Intune-licenceket igényelnek.

További információ: [licencelési feltételek](https://www.microsoft.com/en-us/Licensing/product-licensing/products).

<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>November 18. és 2019. hét (1911 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Felhasználói felület frissítése az alkalmazásadatok szelektív törléséhez<!-- 4102028 -->
Frissült az alkalmazásadatok szelektív törlésére szolgáló felhasználói felület az Intune-ban. A felhasználói felület változásai a következők:
- Egyszerűsített felhasználói felület, amely egyetlen ablaktáblán belül tömörített varázsló-stílusú formátumot használ.
- A létrehozási folyamatra vonatkozó frissítés, amely tartalmazza a hozzárendeléseket.
- A tulajdonságok megtekintésekor beállított összes dolog összefoglaló lapja új házirend létrehozása vagy egy tulajdonság szerkesztésekor. Emellett a tulajdonságok szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemek listáját jeleníti meg.

További tájékoztatást a [Csak vállalati adatok törlése az Intune által felügyelt alkalmazásokból](~/apps/apps-selective-wipe.md) című cikkben talál.

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS és iPadOS harmadik féltől származó billentyűzet-támogatás<!-- 4922950 -->
Március 2019-án bejelentettük a "harmadik féltől származó billentyűzetek" című iOS-es app Protection-házirend támogatásának eltávolítását. A szolgáltatás az iOS-és a iPadOS-támogatással is visszatér az Intune-hoz. A beállítás engedélyezéséhez látogasson el egy új vagy meglévő iOS/iPadOS adatvédelmi szabályzat **Adatvédelem** lapjára, és keresse meg a **harmadik féltől származó billentyűzetek** beállítást a **adatátvitel**alatt.

Ennek a házirend-beállításnak a viselkedése némileg eltér az előző implementációtól. Az SDK-t és újabb verziót használó többidentitásos alkalmazásokban az alkalmazás-védelmi szabályzatok által a **blokkolásra**konfigurált beállítások alapján a végfelhasználók nem tudnak harmadik féltől származó billentyűzeteket használni a szervezetük és a személyes fiókjaik 12.0.16. A 12.0.12 és korábbi SDK-verziókat használó alkalmazások továbbra is mutatják a blogbejegyzés címében ismertetett viselkedést, [ismert probléma: a harmadik féltől származó billentyűzetek nincsenek letiltva az iOS-ben személyes fiókokhoz](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása<!-- 4061739  --> 
A [JAMF által felügyelt MacOS-eszközökre](../protect/conditional-access-integrate-jamf.md)vonatkozó konkrét felhasználói csoportokat is megcélozhat. Ez lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket az Intune kezel. Ha már használja a JAMF-integrációt, a rendszer alapértelmezés szerint minden felhasználót megcéloz az integrációra.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Új Exchange ActiveSync-beállítások az e-mail-eszköz konfigurációs profiljának létrehozásakor iOS-eszközökön<!-- 4892824   --> 
IOS-/iPadOS-eszközökön konfigurálhatja az e-mailek kapcsolatát egy eszköz konfigurációs profiljában (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/IPadOS** a platform > **e-mail-** profil típusa). 

Új Exchange ActiveSync-beállítások érhetők el, beleértve a következőket:
- **Szinkronizálni kívánt Exchange-információk**: válassza ki a naptár, a névjegyek, a emlékeztetők, a megjegyzések és az e-mailek szinkronizálására szolgáló Exchange-szolgáltatásokat.
- A **szinkronizálási beállítások módosításának engedélyezése a felhasználók**számára: engedélyezheti (vagy letilthatja) a felhasználók számára ezen szolgáltatások szinkronizálási beállításainak módosítását az eszközön.  

A beállítással kapcsolatos további információkért nyissa meg az [iOS-eszközök e-mail profiljának beállításait az Intune-ban](../configuration/email-settings-ios.md). 

A következőkre vonatkozik:

- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Személyes Google-fiókok hozzáadásának megakadályozása az Android Enterprise rendszerű, teljes körűen felügyelt és dedikált eszközök számára<!-- 5353228   -->
Az Android Enterprise teljes körűen felügyelt és dedikált eszközökön van egy új beállítás, amely megakadályozza, hogy a felhasználók személyes Google-fiókokat hozzanak létre (az eszköz**konfigurációjának** > **profiljait** , > **profil létrehozása** > **Android Enterprise** for platform > **eszköz tulajdonosa csak > eszközök korlátozásait** a profil típusa > **felhasználók és fiókok beállításai** > **személyes Google-fiókok**).

A konfigurálható beállítások megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

A következőkre vonatkozik:

- Android Enterprise teljes körűen felügyelt eszközök
- Androidos vállalati dedikált eszközök

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>A Siri-parancsok beállításának kiszolgálóoldali naplózása el lesz távolítva az iOS/iPadOS-eszköz korlátozási profiljában <!-- 5468501   -->
IOS-és iPadOS-eszközökön **a Siri-parancsok kiszolgálóoldali naplózása** el lesz távolítva a Microsoft Endpoint Manager felügyeleti konzolról (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **eszközre vonatkozó korlátozások** a profil típusa > **beépített alkalmazások**). 

Ez a beállítás nincs hatással az eszközökre. Ha el szeretné távolítani a beállítást a meglévő profilok közül, nyissa meg a profilt, végezze el a kívánt módosításokat, majd mentse a profilt. A rendszer frissíti a profilt, és törli a beállítást az eszközökről.

Az összes konfigurálható beállítás megjelenítéséhez tekintse meg az [iOS-és iPadOS-eszközök beállításait, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

A következőkre vonatkozik:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 szolgáltatás frissítései (nyilvános előzetes verzió)<!-- 2384877 -->
Most már telepítheti a [Windows 10-es szolgáltatások frissítéseit](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) a Windows 10-es eszközökre. A Windows 10-es szolgáltatások frissítései egy új szoftverfrissítési házirend, amely a Windows 10 azon verzióját állítja be, amelyre telepíteni szeretné az eszközöket, és megmarad. Ezt az új házirend-típust használhatja a meglévő Windows 10-es frissítési gyűrűkkel együtt.

Azok az eszközök, amelyek megkapják a Windows 10-es szolgáltatások frissítési szabályzatát, telepítik a Windows megadott verzióját, majd az adott verzióban maradnak, amíg a házirendet nem szerkesztik vagy nem távolítják el. A Windows újabb verzióját futtató eszközök továbbra is a jelenlegi verzióban maradnak. A Windows adott verziójában tárolt eszközök továbbra is telepíthetik az adott verzió minőségi és biztonsági frissítéseit a Windows 10-es frissítési gyűrűkből.

Ez az új típusú házirend a bérlők számára ezen a héten kezdődik. Ha ez a szabályzat még nem érhető el a bérlő számára, hamarosan elérhető lesz.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Az plist-fájlokban lévő legfontosabb információk hozzáadása és módosítása macOS-alkalmazásokhoz<!-- 4736278 -->
MacOS-eszközökön mostantól létrehozhat egy olyan eszköz-konfigurációs profilt, amely feltölt egy alkalmazáshoz vagy az eszközhöz társított (. plist) egy tulajdonságlapot (az**eszközök** > a **konfigurációs profilokat** , > **hozza létre** a profilt > **MacOS** - **t a platform > a** profil típusa).

Csak néhány alkalmazás támogatja a felügyelt beállításokat, és előfordulhat, hogy ezek az alkalmazások nem teszik lehetővé az összes beállítás kezelését. Ügyeljen arra, hogy töltsön fel egy olyan tulajdonságlap-fájlt, amely az eszköz csatornájának beállításait konfigurálja, nem pedig a felhasználói csatorna beállításait.

A szolgáltatással kapcsolatos további információkért lásd: [Tulajdonságok listájának hozzáadása MacOS-eszközökhöz Microsoft Intune használatával](../configuration/preference-file-settings-macos.md).

A következőkre vonatkozik:

- 10,7 és újabb rendszerű macOS-eszközök

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Az Autopilot-eszközökhöz tartozó eszköznév értékének szerkesztése<!-- 2640074 -->
Az Azure AD-hez csatlakoztatott Autopilot-eszközök eszköznév értéke szerkeszthető.  További információ: az [Autopilot-eszköz attribútumainak szerkesztése](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Az Autopilot-eszközökhöz tartozó címke értékének szerkesztése<!-- 4816775   -->
Az Autopilot-eszközöknél szerkesztheti a csoport címke értékét. További információ: az [Autopilot-eszköz attribútumainak szerkesztése](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="updated-support-experience---5012398---"></a>Frissített támogatási élmény<!-- 5012398 -->

A mai naptól kezdve az Intune-nal való [Súgó és támogatás megszerzésére](get-support.md) szolgáló, frissített és egyszerűsített konzolon alapuló élmény a bérlők számára érhető el. Ha ez az új felület még nem érhető el, hamarosan elérhető lesz.

Továbbfejlesztettük a konzolon belüli keresést és visszajelzést a gyakori problémákkal kapcsolatban, valamint az ügyfélszolgálattal való kapcsolatfelvételhez használt munkafolyamatot. A támogatási problémák megnyitásakor a rendszer valós idejű becsléseket fog kapni a visszahívási vagy e-mail-válaszhoz, és a Premier és az egységes támogatással rendelkező ügyfelek egyszerűen meghatározhatják a probléma súlyosságát, így gyorsabban kaphatnak támogatást.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Továbbfejlesztett Intune jelentéskészítési felület (nyilvános előzetes verzió) <!-- 3791418 -->
Az Intune mostantól továbbfejlesztett jelentéskészítési lehetőségeket kínál, beleértve az új jelentési típusokat, a jobb jelentési szervezetet, a célzottabb nézeteket, a jobb jelentési funkciókat, valamint a több konzisztens és kellő időben megjelenő adatát. Az új Jelentéstípusok a következőkre összpontosítanak:
- **Működés** – a negatív állapotú friss rekordokat biztosít. 
- **Szervezet** – a teljes állapot szélesebb körű összegzését biztosítja.
- **Előzmények** – mintákat és trendeket biztosít egy adott időszakra vonatkozóan.
- **Specialist** – lehetővé teszi, hogy a nyers adatait használja saját egyéni jelentéseinek létrehozásához.

Az új jelentések első halmaza az eszköz megfelelőségére koncentrál. További információ: [Blog Microsoft Intune jelentési keretrendszer](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) és [Intune-jelentések](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Ismétlődő egyéni vagy beépített szerepkörök <!-- 1081938   -->
Mostantól a beépített és az egyéni szerepkörök is másolhatók. További információ: [szerepkör másolása](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Új engedélyek az iskolai rendszergazdai szerepkörhöz <!-- 5621805  -->  
Két új engedély, **profil** -és **szinkronizáló eszköz**lett hozzáadva az iskolai rendszergazda szerepkörhöz > **engedélyek** > **beléptetési programok**. A szinkronizálási profil engedély lehetővé teszi a rendszergazdák számára a Windows Autopilot-eszközök szinkronizálását. A profil kiosztása engedély lehetővé teszi a felhasználó által kezdeményezett Apple beléptetési profilok törlését. Emellett engedélyt ad az Autopilot-eszközök hozzárendeléseinek és az Autopilot-alapú üzembe helyezési profilok hozzárendelésének kezelésére is. Az összes iskolai rendszergazda/csoport rendszergazdai engedély listájáért lásd: [csoport adminisztrátorok kiosztása](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Biztonság

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker-kulcs elforgatása<!-- 2564951  -->
Az Intune-eszköz művelettel távolról [elforgathatja a BitLocker helyreállítási kulcsait](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) a Windows 1909-es vagy újabb verzióját futtató felügyelt eszközökön. Ahhoz, hogy a helyreállítási kulcsok el legyenek forgatva, az eszközöket úgy kell konfigurálni, hogy támogassák a helyreállítási kulcs elforgatását.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>A dedikált eszközök regisztrációjának frissítései a SCEP-eszközök telepítésének támogatásához <!-- 5198878  -->
Az Intune mostantól támogatja a SCEP telepítését az Android Enterprise dedikált eszközökön a Wi-Fi profilok tanúsítvány alapú eléréséhez. A Microsoft Intune alkalmazásnak jelen kell lennie az eszközön a működéshez való üzembe helyezéshez. Ennek eredményeképpen frissítettük az androidos vállalati dedikált eszközök beléptetési élményét. Az új regisztrációk továbbra is ugyanúgy kezdődnek (QR, NFC, Zero Touch vagy Device Identifier), de most egy olyan lépéssel kell rendelkezniük, amely megköveteli, hogy a felhasználók telepítse az Intune-alkalmazást. A meglévő eszközök elkezdik automatikusan telepíteni az alkalmazást a folyamatos üzembe helyezéshez.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Intune-naplók a vállalatok közötti együttműködéshez<!--5670211 -->
A vállalatok közötti (B2B) együttműködés lehetővé teszi, hogy biztonságosan megossza a vállalat alkalmazásait és szolgáltatásait a vendég felhasználókkal bármely más szervezettől, miközben a saját vállalati adatok felett tartja a felügyeletet. Az Intune mostantól támogatja a B2B vendég felhasználói számára a naplókat. Ha például a vendég felhasználó változtatásokat hajt végre, az Intune a naplók segítségével rögzítheti ezeket az eseményeket. További információ: [Mi a vendég felhasználói hozzáférés a Azure Active Directory B2B-ben?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>November 11-i hét, 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Továbbfejlesztett macOS-regisztrációs élmény Céges portál <!-- 5074349  -->  
A macOS-regisztrálási élmény Céges portál egyszerűbb regisztrációs folyamattal rendelkezik, amely szorosabban igazodik a Céges portál iOS-es regisztrálási élményhez. Az eszköz felhasználói mostantól a következőket látják:  

* Egy fényesebb felhasználói felület.  
* Továbbfejlesztett regisztrációs ellenőrzőlista.  
* Az eszközök regisztrálásával kapcsolatos tudnivalók.  
* Továbbfejlesztett hibaelhárítási beállítások.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>A Windows Céges portál alkalmazásból indított webalkalmazások<!-- 5030972 -->
A végfelhasználók mostantól közvetlenül a Windows Céges portál alkalmazásból is elindíthatják a webalkalmazásokat. A végfelhasználók kiválaszthatják a webalkalmazást, majd kiválaszthatják a **Megnyitás böngészőben**lehetőséget. A közzétett webes URL-cím közvetlenül egy böngészőben nyílik meg. Ez a funkció a következő héten lesz bevezetve. A Web Apps szolgáltatással kapcsolatos további információkért lásd: [webalkalmazások hozzáadása Microsoft Intunehoz](~/apps/web-app.md).  

#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Új hozzárendelési típus oszlop a Windows 10-es Céges portál <!-- 5459950  -->
A Céges portál > **telepített alkalmazások** > **hozzárendelés típusa** oszlop átnevezve lett a **szervezet**számára.  Az oszlop alatt a felhasználók **Igen** vagy nem értékkel látják, hogy az alkalmazás a szervezet által kötelező vagy **nem** kötelezően elérhetővé válik. Ezek a módosítások azért történtek, mert az eszköz felhasználói zavarosak voltak az elérhető alkalmazások fogalmával kapcsolatban. A felhasználók további információkat találhatnak az alkalmazások telepítéséről Céges portálről az [alkalmazás telepítése és megosztása eszközön](/intune-user-help/install-apps-cpapp-windows). A Céges portál alkalmazásnak a felhasználók számára történő konfigurálásával kapcsolatos további információkért lásd: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019. november 4. hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>A biztonsági alapkonfigurációkat a Microsoft Azure Government támogatja<!-- 4062552 -->

A *Microsoft Azure Government* futtatott Intune-példányok mostantól [biztonsági](../protect/security-baselines.md) alapkonfigurációkat használhatnak a felhasználók és eszközök védelméhez és védelméhez.

## <a name="whats-new-archive"></a>Újdonságok archívuma
Az előző hónapok esetében tekintse meg az Újdonságok [archívumát](whats-new-archive.md).

## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]


