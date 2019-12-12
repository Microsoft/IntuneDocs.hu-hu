---
title: Újdonságok a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Az Azure-beli Intune-portál újdonságai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/09/2019
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
ms.openlocfilehash: 77cf4745262346ec2f8bfb5d4d7e67e1ee5c5e07
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000380"
---
# <a name="whats-new-in-microsoft-intune"></a>Újdonságok a Microsoft Intune-ban

Heti összesítésben olvashat a Microsoft Intune újdonságairól. Megtalálhatja a [fontos megjegyzéseket](#notices), a [korábbi kiadásokat](whats-new-archive.md)és az [Intune szolgáltatás frissítéseinek kiadásával](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)kapcsolatos információkat is.

> [!Note]
> A [havi frissítés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) akár három napot is igénybe vehet, és a következő sorrendben fog megjelenni:
>
> - 1\. nap: Ázsia és a Csendes-óceáni térség (APAC)
> - 2\. nap: Európa, Közel-Kelet, Afrika (EMEA)
> - 3\. nap: Észak-Amerika
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
## <a name="week-of-december-9-2019"></a>2019. december 9-i hét

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrálás a Microsoft Edge-be felügyelt böngészési forgatókönyvek esetén<!-- 5173762 -->

Ahogy közeledünk a Intune Managed Browser kivonulásához, az alkalmazás-védelmi szabályzatok módosultak, hogy leegyszerűsítse a felhasználók az Edge-re való áthelyezéséhez szükséges lépéseket. Frissítettük az alkalmazás-védelmi házirend beállítását, amely **korlátozza a webes tartalom átvitelét más alkalmazásokkal** , hogy az a következők egyike legyen:

- Bármely alkalmazás
- Intune Managed Browser
- Microsoft Edge
- Nem felügyelt böngésző 

Ha kiválasztja a **Microsoft Edge**lehetőséget, a végfelhasználók a feltételes hozzáférési üzenetküldést fogják látni, hogy a Microsoft Edge szükséges a felügyelt böngészési forgatókönyvekhez. A rendszer arra kéri, hogy töltse le és jelentkezzen be a Microsoft Edge-be a HRE-fiókjával, ha még nem tette volna meg.  Ez azzal egyenértékű, hogy a MAM-kompatibilis alkalmazásokat az alkalmazás konfigurációs beállításával megcélozta, `com.microsoft.intune.useEdge` **igaz**értékre van állítva. A **házirend által felügyelt böngészőket** használó meglévő alkalmazás-védelmi szabályzatok mostantól **Intune Managed Browser** lesznek kiválasztva, és a viselkedésben nem fog megjelenni a változás. Ez azt jelenti, hogy a felhasználók láthatják, hogy az üzenetküldés a Microsoft Edge használatára van beállítva, ha a **useEdge** -alkalmazás konfigurációjának beállítása **true (igaz**). Javasoljuk, hogy a felügyelt böngészési forgatókönyveket használó ügyfelek az alkalmazás-védelmi szabályzatokat a **webes tartalmak más alkalmazásokkal való átadásának korlátozásával** használják, hogy a felhasználók lássák a Microsoft Edge-re való áttérésre vonatkozó megfelelő útmutatást, függetlenül attól, hogy az alkalmazás milyen alkalmazásokat indít el. 

<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019. december 2. hét

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Új Microsoft-végpont Configuration Manager közös felügyelet licencelése<!--5027281-->
Mostantól elérhető egy új licenc, amely lehetővé Configuration Manager teszi a frissítési garanciával rendelkező ügyfelek számára, hogy a Windows 10 rendszerű számítógépeken az Intune-nal közös felügyeletet igényeljen anélkül, hogy további Intune-licencet kellene vásárolnia a közös felügyelet Az ügyfeleknek már nem kell egyéni Intune-/EMS-licenceket rendelniük a végfelhasználók számára a Windows 10 közös felügyeletéhez.
- A Configuration Manager által felügyelt és a közös felügyeletbe beléptetett eszközök szinte ugyanazok a jogosultságok, mint az Intune önálló MDM felügyelt számítógépei. Az alaphelyzetbe állítást követően azonban nem lehet újra kiépíteni az Autopilot használatával.
- Az Intune-ba beléptetett Windows 10-es eszközök más módon teljes Intune-licencet igényelnek.
- A más platformokon lévő eszközök továbbra is teljes Intune-licenceket igényelnek.

További információ: [licencelési feltételek](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>November 18. és 2019. hét (1911 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="smime-support-with-microsoft-outlook-for-ios---2669398-idready---"></a>S/MIME-támogatás az iOS-hez készült Microsoft Outlookkal<!-- 2669398 idready -->

   > [!NOTE]
   > Ez a szolgáltatás késleltetve lett, de hamarosan megjelent.

Az Intune támogatja az iOS-eszközökön az iOS rendszerhez használható S/MIME-aláírási és titkosítási tanúsítványok kézbesítését. További információ: az [S/MIME konfigurálása az Outlookhoz az iOS rendszerhez](~/apps/app-configuration-policies-outlook-smime.md).

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Felhasználói felület frissítése az alkalmazásadatok szelektív törléséhez<!-- 4102028 -->
Frissült az alkalmazásadatok szelektív törlésére szolgáló felhasználói felület az Intune-ban. A felhasználói felület változásai a következők:
- Egyszerűsített felhasználói felület, amely egyetlen ablaktáblán belül tömörített varázsló-stílusú formátumot használ.
- A létrehozási folyamatra vonatkozó frissítés, amely tartalmazza a hozzárendeléseket.
- A tulajdonságok megtekintésekor beállított összes dolog összefoglaló lapja új házirend létrehozása vagy egy tulajdonság szerkesztésekor. Emellett a tulajdonságok szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemek listáját jeleníti meg.

További tájékoztatást a [Csak vállalati adatok törlése az Intune által felügyelt alkalmazásokból](~/apps/apps-selective-wipe.md) című cikkben talál.

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS és iPadOS harmadik féltől származó billentyűzet-támogatás<!-- 4922950 -->
2019 márciusában bejelentettük a "harmadik féltől származó billentyűzetek" beállításra vonatkozó iOS-es alkalmazás-védelmi házirend támogatásának eltávolítását. A szolgáltatás az iOS-és a iPadOS-támogatással is visszatér az Intune-hoz. A beállítás engedélyezéséhez látogasson el egy új vagy meglévő iOS/iPadOS adatvédelmi szabályzat **Adatvédelem** lapjára, és keresse meg a **harmadik féltől származó billentyűzetek** beállítást a **adatátvitel**alatt.

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

A következőre érvényes
- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Személyes Google-fiókok hozzáadásának megakadályozása az Android Enterprise rendszerű, teljes körűen felügyelt és dedikált eszközök számára<!-- 5353228   -->
Az Android Enterprise teljes körűen felügyelt és dedikált eszközökön van egy új beállítás, amely megakadályozza, hogy a felhasználók személyes Google-fiókokat hozzanak létre (az eszköz**konfigurációjának** > **profiljait** , > **profil létrehozása** > **Android Enterprise** for platform > **eszköz tulajdonosa csak > eszközök korlátozásait** a profil típusa > **felhasználók és fiókok beállításai** > **személyes Google-fiókok**).

A konfigurálható beállítások megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

A következőre érvényes
- Android Enterprise teljes körűen felügyelt eszközök
- Androidos vállalati dedikált eszközök

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>A Siri-parancsok beállításának kiszolgálóoldali naplózása el lesz távolítva az iOS/iPadOS-eszköz korlátozási profiljában <!-- 5468501   -->
IOS-és iPadOS-eszközökön **a Siri-parancsok kiszolgálóoldali naplózása** el lesz távolítva a Microsoft Endpoint Manager felügyeleti konzolról (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **eszközre vonatkozó korlátozások** a profil típusa > **beépített alkalmazások**). 

Ez a beállítás nincs hatással az eszközökre. Ha el szeretné távolítani a beállítást a meglévő profilok közül, nyissa meg a profilt, végezze el a kívánt módosításokat, majd mentse a profilt. A rendszer frissíti a profilt, és törli a beállítást az eszközökről.

Az összes konfigurálható beállítás megjelenítéséhez tekintse meg az [iOS-és iPadOS-eszközök beállításait, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

A következőre érvényes
- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 szolgáltatás frissítései (nyilvános előzetes verzió)<!-- 2384877 -->
Most már telepítheti a [Windows 10-es szolgáltatások frissítéseit](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) a Windows 10-es eszközökre. A Windows 10-es szolgáltatások frissítései egy új szoftverfrissítési házirend, amely a Windows 10 azon verzióját állítja be, amelyre telepíteni szeretné az eszközöket, és megmarad. Ezt az új házirend-típust használhatja a meglévő Windows 10-es frissítési gyűrűkkel együtt.

Azok az eszközök, amelyek megkapják a Windows 10-es szolgáltatások frissítési szabályzatát, telepítik a Windows megadott verzióját, majd az adott verzióban maradnak, amíg a házirendet nem szerkesztik vagy nem távolítják el. A Windows újabb verzióját futtató eszközök továbbra is a jelenlegi verzióban maradnak. A Windows adott verziójában tárolt eszközök továbbra is telepíthetik az adott verzió minőségi és biztonsági frissítéseit a Windows 10-es frissítési gyűrűkből.

Ez az új típusú házirend a bérlők számára ezen a héten kezdődik. Ha ez a szabályzat még nem érhető el a bérlő számára, hamarosan elérhető lesz.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Az plist-fájlokban lévő legfontosabb információk hozzáadása és módosítása macOS-alkalmazásokhoz<!-- 4736278 -->
MacOS-eszközökön mostantól létrehozhat egy olyan eszköz-konfigurációs profilt, amely feltölt egy alkalmazáshoz vagy az eszközhöz társított (. plist) egy tulajdonságlapot (az**eszközök** > a **konfigurációs profilokat** , > **hozza létre** a profilt > **MacOS** - **t a platform > a** profil típusa).

Csak néhány alkalmazás támogatja a felügyelt beállításokat, és előfordulhat, hogy ezek az alkalmazások nem teszik lehetővé az összes beállítás kezelését. Ügyeljen arra, hogy töltsön fel egy olyan tulajdonságlap-fájlt, amely az eszköz csatornájának beállításait konfigurálja, nem pedig a felhasználói csatorna beállításait.

A szolgáltatással kapcsolatos további információkért lásd: [Tulajdonságok listájának hozzáadása MacOS-eszközökhöz Microsoft Intune használatával](../configuration/preference-file-settings-macos.md).

A következőre érvényes
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

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>Továbbfejlesztett macOS-regisztrációs élmény Céges portál <!-- 5074349 WNready -->  
A macOS-regisztrálási élmény Céges portál egyszerűbb regisztrációs folyamattal rendelkezik, amely szorosabban igazodik a Céges portál iOS-es regisztrálási élményhez. Az eszköz felhasználói mostantól a következőket látják:  

* Egy fényesebb felhasználói felület.  
* Továbbfejlesztett regisztrációs ellenőrzőlista.  
* Az eszközök regisztrálásával kapcsolatos tudnivalók.  
* Továbbfejlesztett hibaelhárítási beállítások.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>A Windows Céges portál alkalmazásból indított webalkalmazások<!-- 5030972 -->
A végfelhasználók mostantól közvetlenül a Windows Céges portál alkalmazásból is elindíthatják a webalkalmazásokat. A végfelhasználók kiválaszthatják a webalkalmazást, majd kiválaszthatják a **Megnyitás böngészőben**lehetőséget. A közzétett webes URL-cím közvetlenül egy böngészőben nyílik meg. Ez a funkció a következő héten lesz bevezetve. A Web Apps szolgáltatással kapcsolatos további információkért lásd: [webalkalmazások hozzáadása Microsoft Intunehoz](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>Új hozzárendelési típus oszlop a Windows 10-es Céges portál <!-- 5459950 WNready -->
A Céges portál > **telepített alkalmazások** > **hozzárendelés típusa** oszlop átnevezve lett a **szervezet**számára.  Az oszlop alatt a felhasználók **Igen** vagy nem értékkel látják, hogy az alkalmazás a szervezet által kötelező vagy **nem** kötelezően elérhetővé válik. Ezek a módosítások azért történtek, mert az eszköz felhasználói zavarosak voltak az elérhető alkalmazások fogalmával kapcsolatban. A felhasználók további információkat találhatnak az alkalmazások telepítéséről Céges portálről az [alkalmazás telepítése és megosztása eszközön](/intune-user-help/install-apps-cpapp-windows). A Céges portál alkalmazásnak a felhasználók számára történő konfigurálásával kapcsolatos további információkért lásd: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019. november 4. hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>A biztonsági alapkonfigurációkat a Microsoft Azure Government támogatja<!-- 4062552 -->

A *Microsoft Azure Government* futtatott Intune-példányok mostantól [biztonsági](../protect/security-baselines.md) alapkonfigurációkat használhatnak a felhasználók és eszközök védelméhez és védelméhez.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>2019. október 28-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Továbbfejlesztett ellenőrzőlista-kialakítás az androidos Céges portál alkalmazásban<!-- 5550857 -->  
Az Androidhoz készült Céges portál alkalmazásban található beállítási ellenőrzőlista egy könnyű kialakítással és új ikonokkal frissült. A módosítások összhangban vannak az iOS rendszerhez készült Céges portál alkalmazás legújabb frissítéseivel. A változások párhuzamos összehasonlítását lásd: Újdonságok az [alkalmazás felhasználói felületén](whats-new-app-ui.md). A frissített regisztrációs lépések megtekintéséhez tekintse meg az androidos [munkahelyi Profil regisztrálása](/intune-user-help/enroll-device-android-work-profile) és [az Android-eszköz regisztrálása](/intune-user-help/enroll-device-android-company-portal)című témakört.  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Win32-alkalmazások Windows 10 S üzemmódú eszközökön<!-- 3747604 --> 
Win32-alkalmazásokat telepíthet és futtathat Windows 10 S üzemmódú felügyelt eszközökön. Ehhez a Windows Defender Application Control (WDAC) PowerShell-eszközeivel létrehozhat egy vagy több kiegészítő szabályzatot az S üzemmódhoz. Írja alá a kiegészítő szabályzatokat az Eszközkezelő-aláírási portálon, majd töltse fel és terjessze a szabályzatokat az Intune-on keresztül. Az Intune-ban ezt a képességet az **ügyfélalkalmazások** > **Windows 10 S kiegészítő házirendek**lehetőség kiválasztásával találja meg. További információ: Win32- [alkalmazások engedélyezése az S Mode-eszközökön](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Win32-alkalmazás rendelkezésre állásának beállítása dátum és idő alapján<!-- 3510685 -->
Rendszergazdaként beállíthatja a szükséges Win32-alkalmazások kezdési és határidő-idejét. A kezdési időpontban az Intune felügyeleti bővítmény elindítja az alkalmazás tartalmának letöltését és gyorsítótárazását. Az alkalmazás a határidő lejártakor lesz telepítve. Az elérhető alkalmazások esetében a kezdési idő akkor fog megjelenni, amikor az alkalmazás látható Céges portálban. További információ: az [Intune win32 app Management](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Eszköz újraindításának megkövetelése türelmi időszak alapján a Win32-alkalmazás telepítése után<!-- 3136567 -->
Megkövetelheti, hogy az eszköznek újra kell indítania a Win32-alkalmazások sikeres telepítése után. További információ: [win32 app Management – alkalmazás telepítésének részletei](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Sötét mód iOS-Céges portál<!-- 4911422 -->
A sötét mód elérhető az iOS-Céges portál számára. A felhasználók letölthetik a vállalati alkalmazásokat, kezelhetik az eszközeiket, és az eszköz beállításai alapján választhatják ki a kívánt színsémát. Az iOS-Céges portál automatikusan meg fogja egyezni a végfelhasználói eszközbeállítások sötét vagy világos módban. További információ: [sötét mód bevezetése Microsoft Intune céges portál iOS rendszerhez](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). További információ az iOS Céges portálről: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android Céges portál kényszerített alkalmazás minimális verziója<!-- 2378776 -->
Az alkalmazás-védelmi házirend **minimális céges portál verziójának** beállításával megadhatja a végfelhasználói eszközön kényszerített céges portál adott minimálisan meghatározott verzióját. Ez a feltételes indítási beállítás lehetővé teszi a **hozzáférés letiltását**, az **adatok törlését**vagy a **Figyelmeztetés** lehetséges műveleteit, ha az érték nem teljesül. Az érték lehetséges formátuma a *[Major] mintázatot követi. [ Minor]* , *[főverzió]. [ Alverzió]. [Build]* vagy *[főverzió]. [ Alverzió]. [Build]. [Változat]* .

Ha be van állítva a **minimális céges portál verziószáma** , az hatással lesz minden olyan végfelhasználóra, aki a céges portál 5.0.4560.0 és a céges portál jövőbeli verzióit lekéri. Ez a beállítás nem lesz hatással a felhasználók olyan Céges portál verzióját használó felhasználóra, amely régebbi, mint a szolgáltatás által kiadott verzió. Az alkalmazás automatikus frissítéseit az eszközön használó végfelhasználók valószínűleg nem fogják látni a szolgáltatásból származó párbeszédpaneleket, mivel azok valószínűleg a legújabb Céges portál-verziót fogják használni. Ez a beállítás csak a regisztrált és a nem regisztrált eszközökön futó alkalmazás-védelemmel rendelkező Android. További információ: [Android-alkalmazás védelmi szabályzatának beállításai – feltételes indítás](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Eszközkezelés Microsoft 365

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>A végpont biztonsági csomópontjának bemutatása Microsoft 365-eszközkezelés<!-- 5630102 -->

A **végponti biztonsági** csomópont mostantól általánosan elérhető Microsoft 365 Eszközkezelő Specialist munkaterületen a https://devicemanagement.microsoft.com , amely a végpontok biztonságossá tételeit csoportosítja, például:

- Biztonsági alapkonfigurációk: előre konfigurált beállítások csoportja, amely segítséget nyújt a Microsoft által javasolt, ismert beállítások és alapértelmezett értékek alkalmazásához.

- Biztonsági feladatok: kihasználhatja a Microsoft Defender ATPs Threat and sebezhetőségi felügyeletét (TVM), és az Intune-nal javíthatja a végpontok gyengeségeit.

- Microsoft Defender ATP: integrált Microsoft Defender komplex veszélyforrások elleni védelem (ATP) a biztonsági rések megelőzése érdekében.

Ezek a beállítások továbbra is elérhetők lesznek a többi érintett csomóponttól, például az eszközöktől, és az aktuálisan konfigurált állapot ugyanaz lesz, függetlenül attól, hogy hol férhet hozzá és engedélyezheti ezeket a funkciókat.

További információ ezekről a fejlesztésekről: [Intune-ügyfél sikerének blogbejegyzése](https://aka.ms/Endpoint_security_node) a Microsoft Tech Community webhelyén.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Az Intune támogatja az iOS 11 és újabb verziókat<!-- 4665324  -->

Az Intune-regisztráció és a Céges portál mostantól támogatja az iOS 11-es és újabb verzióit. A régebbi verziók nem támogatottak.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge alapterve (előzetes verzió)<!--  3787164  -->

Bővítettük a [Microsoft Edge-beállítások biztonsági alapkonfigurációjának](../protect/security-baseline-settings-edge.md)előzetes verzióját. 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>2019. október 21-i hét (1910 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Eszközkezelés Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Továbbfejlesztett adminisztrációs élmény az Microsoft 365-eszközök felügyeletében<!-- 5551239 -->

Mostantól általánosan elérhető a frissített és áramvonalas felügyeleti felület a Microsoft 365 Eszközkezelő Specialist munkaterületen a [https://devicemanagement.microsoft.com on ](https://devicemanagement.microsoft.com), beleértve a következőket:

- **Frissített navigáció**: egy egyszerűsített, első szintű navigációt talál, amely logikailag csoportosítja a szolgáltatásokat.
- **Új platform szűrők**: egyetlen platformot választhat ki, amely csak a kiválasztott platformhoz tartozó szabályzatokat és alkalmazásokat jeleníti meg az eszközök és alkalmazások oldalain.
- **Új Kezdőlap**: gyorsan megtekintheti a szolgáltatás állapotát, a bérlőt, a híreket stb. az új kezdőlapon.

További információ ezekről a fejlesztésekről: [Enterprise Mobility + Security blogbejegyzés](https://go.microsoft.com/fwlink/?linkid=2109094) a Microsoft technikai Közösség webhelyén.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Mobile Threat Defense-alkalmazások hozzáadása a nem regisztrált eszközökhöz<!-- 3005337 -->
Létrehozhat egy Intune app Protection-szabályzatot, amely letilthatja vagy szelektíven törölheti a felhasználók vállalati adatait az eszköz állapota alapján. Az eszköz állapota a kiválasztott Mobile Threat Defense-(MTD-) megoldás használatával van meghatározva. Ez a funkció ma már az Intune-ban regisztrált eszközökön van, eszköz-megfelelőségi beállításként. Ezzel az új funkcióval kiterjesztjük a fenyegetések észlelését egy Mobile Threat Defense-gyártótól a nem regisztrált eszközökön való működéshez. Android rendszeren a szolgáltatáshoz a legújabb Céges portál van szükség az eszközön. IOS rendszeren ez a funkció akkor használható, ha az alkalmazások integrálják a legújabb Intune SDK-t (v 12.0.15 +). Frissítjük az Újdonságok témakört, amikor az első alkalmazás elfogadja a legújabb Intune SDK-t. A fennmaradó alkalmazások folyamatosan elérhetővé válnak. További információ: [a Mobile Threat Defense-alkalmazás védelmi szabályzatának létrehozása az Intune](~/protect/mtd-app-protection-policy.md)-nal.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Új eszköz belső vezérlőprogram-konfigurációs felületének profilja a Windows 10 és újabb rendszerű eszközökhöz (nyilvános előzetes verzió)<!-- 2266073  -->

Windows 10 és újabb rendszereken létrehozhat egy eszköz-konfigurációs profilt a beállítások és szolgáltatások vezérléséhez (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Windows 10 és újabb verziók** a platformhoz). Ebben a frissítésben egy új, az eszköz belső vezérlőprogram-konfigurációs felületének profilja van, amely lehetővé teszi az Intune számára az UEFI-(BIOS-) beállítások kezelését.

A szolgáltatással kapcsolatos további információkért lásd: [DFCI-profilok használata Windows-eszközökön Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

A következőre érvényes
- Windows 10 RS5 (1809) és újabb támogatott belső vezérlőprogram

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Váltás csak a regisztrációs állapot megjelenítése lapra a beépített felhasználói felülettel (OOBE) kiépített eszközökön<!--3959566-->
Most úgy is dönthet, hogy csak az Autopilot OOBE által kiépített eszközök regisztrációs állapot lapját jeleníti meg.

Az új váltógomb megjelenítéséhez válassza az **Intune** > **eszközök beléptetése** > **Windows-regisztráció** > **regisztráció állapota lapot** > **profil létrehozása** > **Beállítások** > **csak az eszközön a beépített felhasználói felülettel (OOBE) kiépített eszközök megjelenítése**lehetőséget.


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>2019. október 14-i hét

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz<!-- 3041956   -->
Az Android Enterprise munkahelyi profil, dedikált és teljes körűen felügyelt eszközökön elérhető alkalmazások telepítésének megtekintheti az alkalmazások telepítési állapotát, valamint a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](~/apps/app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](~/enrollment/android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>A Microsoft Edge 77-es és újabb verziói a Windows 10 és a macOS rendszerhez (nyilvános előzetes verzió)<!-- 3872025, 4678761  -->
A Microsoft Edge 77-es és újabb verziói elérhetők lesznek a Windows 10 és macOS rendszerű számítógépeken való üzembe helyezéshez. 

A nyilvános előzetes verzió a Windows 10 **fejlesztési** és **bétaverziós** csatornáit, valamint a MacOS-hez készült **bétaverziót** kínálja. A központi telepítés csak angol (EN) nyelven érhető el, de a végfelhasználók a **beállítások** > **nyelvek**területen módosíthatják a böngésző megjelenítési nyelvét. A Microsoft Edge egy, a rendszerkörnyezetben és hasonló architektúrákban telepített Win32-alkalmazás (x86-OS és x64-es OS-es x64-es alkalmazás). Emellett a böngésző automatikus frissítései alapértelmezés szerint be vannak **kapcsolva** , és a Microsoft Edge nem távolítható el. További információ: a [Microsoft Edge for Windows 10 hozzáadása a Microsoft Intune](~/apps/apps-windows-edge.md) és a [Microsoft Edge dokumentációhoz](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Az App Protection felhasználói felületének és az iOS-alkalmazások kiépítési felhasználói felületének frissítése<!-- 4102027, 4102029   -->
Az alkalmazás-védelmi szabályzatok létrehozásához és szerkesztéséhez, valamint az iOS-alkalmazások létesítési profiljaihoz az Intune-ban frissült a felhasználói felület. A felhasználói felület változásai a következők:
- Egyszerűsített felhasználói felület, amely egy, egy panelen belül tömörített varázsló-stílusú formátumot használ. 
- A létrehozási folyamatra vonatkozó frissítés, amely tartalmazza a hozzárendeléseket.
- A tulajdonságok megtekintésekor beállított összes dolog összefoglaló lapja új házirend létrehozása vagy egy tulajdonság szerkesztésekor. Emellett a tulajdonságok szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemek listáját jeleníti meg.

További információ: [az alkalmazás-védelmi szabályzatok létrehozása és kiosztása](~/apps/app-protection-policies.md) és [az iOS-alkalmazások létesítési profiljainak használata](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Az Intune interaktív forgatókönyvei<!-- 4850318, 4831296, 3610611  -->
Az Intune-nal olyan interaktív forgatókönyvek érhetők el, amelyek segítséget nyújtanak egy adott feladat vagy feladatok elvégzéséhez az Intune-ban. Az interaktív forgatókönyvek egy teljes körű használati esethez igazított lépések (munkafolyamat) testreszabott sorozata. A gyakori forgatókönyvek a rendszergazda, a felhasználó vagy az eszköz által a szervezeten belül játszott szerepkör alapján vannak meghatározva. Ezek a munkafolyamatok általában gondosan előkészített profilok, beállítások, alkalmazások és biztonsági vezérlők gyűjteményét igénylik a legjobb felhasználói élmény és biztonság érdekében. Az új interaktív forgatókönyvek a következők:
- [A Microsoft Edge for Mobile üzembe helyezése](~/fundamentals/guided-scenarios-edge.md)
- [Biztonságos Microsoft Office Mobile apps](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Felhőben felügyelt modern asztal](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

További információ: az [Intune interaktív forgatókönyvek áttekintése](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>További elérhető az alkalmazás konfigurációs változója<!-- 4969237   -->
Alkalmazás-konfigurációs házirend létrehozásakor a konfigurációs beállítások részeként felveheti a `AAD Device ID` konfigurációs változót. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs házirendek** > **Hozzáadás**elemet. Adja meg a konfigurációs szabályzat adatait, és válassza a **konfigurációs beállítások** lehetőséget a **konfigurációs beállítások** panel megtekintéséhez. További információ: [alkalmazás-konfigurációs házirendek a felügyelt Android Enterprise-eszközökhöz – a Configuration Designer használata](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Házirend-készletek nevű felügyeleti objektumok csoportjainak létrehozása<!-- 3762880  -->
A házirend-készletek lehetővé teszik, hogy a már meglévő felügyeleti entitásokra mutató hivatkozásokat hozzon létre, amelyeket egyetlen fogalmi egységként kell azonosítani, megcélozni és figyelni. A házirend-készletek nem helyettesítik a meglévő fogalmakat vagy objektumokat. Továbbra is hozzárendelhet egyedi objektumokat az Intune-ban, és egy házirend-készlet részeként egyedi objektumokat is hivatkozhat. Ezért az egyes objektumok módosításai a házirend-készletben is megjelennek.  Az Intune-ban a **házirend-készletek** > **Létrehozás** gombra kattintva hozhat létre új házirend-készletet. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Felhasználói felület frissítése a Windows 10-es frissítési gyűrűk létrehozásához és szerkesztéséhez<!-- 4099089         -->
Frissítettük az Intune [-hoz készült Windows 10-es frissítési körök létrehozására és szerkesztésére](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) szolgáló felhasználói felületet. A felhasználói felület változásai a következők:  
- A varázsló-stílusú formátum egyetlen konzolos panelre van tömörítve, amely az előzőekben látható, az Update Rings konfigurálásakor korábban látott panelre mutat.   
- A felülvizsgált munkafolyamat hozzárendeléseket tartalmaz, mielőtt befejezi a gyűrű kezdeti konfigurációját.
- Egy összefoglaló lap, amellyel áttekintheti az összes olyan konfigurációt, amelyeket az új frissítési kör mentése és telepítése előtt használhat. Egy frissítési kör szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriáján belül beállított elemek listáját jeleníti meg.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Felhasználói felület frissítése iOS szoftverfrissítési szabályzat létrehozásához és szerkesztéséhez<!-- 4099090       --> 
Frissítettük az Intune-hoz készült iOS-szoftverfrissítési szabályzatok [létrehozásához](../protect/software-updates-ios.md#configure-the-policy) és [SZERKESZTÉSÉHEZ](../protect/software-updates-ios.md#edit-a-policy) szükséges felhasználói felületet.  A felhasználói felület változásai a következők:  
- A varázsló-stílusú formátum egyetlen konzolos panelre van tömörítve, amely a korábban a frissítési szabályzatok konfigurálásakor megtekintett panel terjeszkedésével foglalkozik.   
- A módosított munkafolyamat hozzárendeléseket tartalmaz, mielőtt befejezi a szabályzat kezdeti konfigurációját.
- Egy összefoglaló lap, amellyel áttekintheti az összes olyan konfigurációt, amelyeket az új szabályzat mentése és telepítése előtt használhat. A szabályzatok szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriáján belül beállított elemek listáját jeleníti meg.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Az újraindítási beállítások el lesznek távolítva a Windows Update gyűrűkből<!--  4464404   WNReady   -->
Amint azt korábban bejelentettük, az Intune Windows 10-es frissítési gyűrűk mostantól [támogatják a határidőkhöz tartozó beállításokat](../protect/windows-update-settings.md) , és a továbbiakban nem támogatják az *újraindítást*. A *felvállalt újraindítási* beállítások már nem érhetők el, ha az Intune-ban konfigurálja vagy kezeli a frissítési köröket.  

Ez a módosítás a legújabb [Windows-karbantartási változásokkal](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) és a Windows 10 1903 vagy újabb rendszerű eszközökön is igazodik, és a *határidők* felülírják a *felvállalt újraindítási*konfigurációkat.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Az ismeretlen forrásból származó alkalmazások telepítésének megakadályozása az Android Enterprise Work profiling-eszközökön<!-- 4760025   -->
Az Android Enterprise Work Profile eszközein a felhasználók soha nem telepíthetnek ismeretlen forrásból származó alkalmazásokat. Ebben a frissítésben van egy új beállítás – megakadályozza, hogy **az alkalmazások telepítése ismeretlen forrásból történjen a személyes profilban**. Alapértelmezés szerint ez a beállítás megakadályozza, hogy a felhasználók az ismeretlen forrásból származó alkalmazásokat az eszköz személyes profiljába töltsenak be.

A konfigurálható beállítás megjelenítéséhez nyissa meg az [Android Enterprise Device Settings lehetőséget az Intune-nal való funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-android-for-work.md).

A következőre érvényes
- Androidos vállalati munkahelyi profil

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Globális HTTP-proxy létrehozása androidos vállalati eszköz tulajdonosi eszközein<!-- 4816339   -->
Az Android Enterprise rendszerű eszközökön konfigurálhat egy globális HTTP-proxyt, hogy megfeleljen a szervezete webböngészési szabványainak (az**eszköz konfigurációjának** > **profiljai** > **profil létrehozása** > **Android Enterprise** for platform > **eszköz tulajdonosa > eszköz korlátozásai** a profil típusa > a **kapcsolat**). A konfigurálást követően az összes HTTP-forgalom ezt a proxyt fogja használni.

A szolgáltatás konfigurálásához és az összes konfigurált beállítás megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

A következőre érvényes
- Androidos vállalati eszköz tulajdonosa

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Az Automatikus csatlakozás beállítás el lesz távolítva a Wi-Fi profilokban az Android-eszköz rendszergazdája és az Android Enterprise<!-- 5021055   -->
Az Android-eszköz rendszergazdája és az Android Enterprise rendszerű eszközökön létrehozhat egy Wi-Fi profilt különböző beállítások konfigurálásához (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Android-eszköz rendszergazdája** vagy **Android Enterprise** for platform > **Wi-Fi** profil típusa). Ebben a frissítésben a **kapcsolat automatikus** beállítása el lesz távolítva, mivel az [Android nem támogatja](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Ha ezt a beállítást egy Wi-Fi profilban használja, előfordulhat, hogy észrevette, hogy a **Csatlakozás automatikusan** nem működik. Semmilyen műveletet nem kell elvégeznie, de vegye figyelembe, hogy ez a beállítás el lesz távolítva az Intune felhasználói felületén.

Az aktuális beállítások megtekintéséhez lépjen az [Android Wi-Fi beállítások](../configuration/wi-fi-settings-android.md) vagy az [Android Enterprise Wi-Fi beállítások](../configuration/wi-fi-settings-android-enterprise.md)elemre.

A következőre érvényes
- Android-eszköz rendszergazdája 
- Vállalati Android


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Új eszköz konfigurációs beállításai felügyelt iOS-és iPadOS-eszközökhöz<!-- 5199328   -->
Az iOS-és iPadOS-eszközökön létrehozhat egy profilt, amellyel korlátozhatja az eszközök funkcióit és beállításait (az**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **eszközre vonatkozó korlátozások** a profil típusa esetén). Ebben a frissítésben új beállítások vezérelhetők: 
- Hozzáférés hálózati meghajtóhoz a Files alkalmazásban  
- Hozzáférés USB-meghajtóhoz a Files alkalmazásban 
- Wi-Fi mindig be van kapcsolva 

A beállítások megtekintéséhez lépjen az iOS- [eszközbeállítások elemre az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-ios.md).

A következőre érvényes
- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Itt adhatja meg, hogy az operációs rendszer mely operációsrendszer-verzióit regisztrálja munkahelyi profillal vagy az eszközök rendszergazdai regisztrálásával<!-- 4350697   -->
Az Intune-eszközök típusának korlátozásai segítségével megadhatja, hogy mely felhasználói eszközök fogják használni az Android Enterprise munkahelyi profil regisztrációját vagy az Android-eszközök rendszergazdai regisztrációját.  További információkért lásd a [regisztrációs korlátozások beállítása](../enrollment/enrollment-restrictions-set.md)című témakört.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Új korlátozások a Windows-eszközök átnevezéséhez<!-- 3478938  -->
Egy Windows-eszköz átnevezése során új szabályokat kell követnie:
- legfeljebb 15 karakter (63 bájtnál kisebbnek vagy azzal egyenlőnek kell lennie, a záró NULL értékkel nem együtt)
- Nem null vagy üres karakterlánc
- Engedélyezett ASCII: betűk (a-z, A-Z), számok (0-9) és kötőjelek
- Engedélyezett Unicode: karakter > = 0x80, érvényes UTF8-nak kell lennie, az IDN-leképezhető (azaz a RtlIdnToNameprepUnicode sikeresek, lásd: RFC 3492)
- A nevek nem tartalmazhatnak csak számokat
- Nincs szóköz a névben
- Nem engedélyezett karakterek: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

 További információ: [eszköz átnevezése az Intune-ban](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Új Android-jelentés az eszközök áttekintése oldalon<!-- 4924364 -->
Az eszközök áttekintése oldal új jelentése megjeleníti, hogy hány Android-eszköz van regisztrálva az egyes eszközkezelés megoldásokban. Ez a diagram a munkahelyi profilt, a teljes körűen felügyelt, a dedikált és az eszköz-rendszergazda által beléptetett eszközök számát mutatja. A jelentés megtekintéséhez válassza az **Intune** > **eszközök** > **Áttekintés**elemet.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>PKCS-tanúsítványok macOS rendszerhez<!-- 1333650       -->
Mostantól [HASZNÁLHAT PKCS-tanúsítványokat MacOS használatával](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). A PKCS-tanúsítványt a macOS-profil típusaként kiválaszthatja, és olyan felhasználói és eszköz-tanúsítványokat telepíthet, amelyek [testreszabott tulajdonosi és tulajdonosi alternatív név mezőket](../protect/certficates-pfx-configure.md#subject-name-format-for-macos)tartalmazhatnak.  

A macOS-hez készült PKCS-tanúsítvány egy új beállítást is támogat, _lehetővé téve az összes alkalmazás elérését_. Ezzel a beállítással engedélyezheti, hogy az összes társított alkalmazás hozzáférhessen a tanúsítvány titkos kulcsához.  A beállítással kapcsolatos további információkért tekintse meg az Apple dokumentációját https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf címen.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Származtatott hitelesítő adatok a tanúsítványokkal rendelkező iOS-mobileszközök kiépítéséhez<!--  1736036, 1736037, 1772050, 2777333         -->  
Az Intune támogatja a [származtatott hitelesítő adatok](../protect/derived-credentials.md) hitelesítési módszerként való használatát, valamint az S/MIME-aláírást és az iOS-eszközök titkosítását. A származtatott hitelesítő adatok a *nemzeti szabványügyi és Technológiai Intézet (NIST) 800-157* standard implementációja, amely tanúsítványokat helyez üzembe az eszközökön.  

A származtatott hitelesítő adatok a személyes személyazonosság-ellenőrzés (PIV) vagy a Common Card (CAC) kártya (például intelligens kártya) használatára támaszkodnak. Ahhoz, hogy egy származtatott hitelesítő adatot kapjon a mobileszköz számára, a felhasználók a Céges portál alkalmazásban kezdődnek, és egy, a használt szolgáltatóra jellemző regisztrációs munkafolyamatot követnek.  Az összes szolgáltatóval közösen az intelligens kártyát kell használni a számítógépen a származtatott hitelesítőadat-szolgáltatón való hitelesítéshez. Ez a szolgáltató ezután kibocsátja a tanúsítványt a felhasználó intelligens kártyáján található eszközre.  

Az Intune a következő származtatott hitelesítőadat-szolgáltatókat támogatja:
- DISA fajtatiszta
- Entrust Datacard
- Közbenjárni

Származtatott hitelesítő adatokat használ a VPN-, Wi-Fi-és e-mail-alapú eszköz-konfigurációs profilok hitelesítési módszere. Ezeket az alkalmazás-hitelesítéshez, valamint az S/MIME-aláíráshoz és a titkosításhoz is használhatja.  

További információ a standardról: [származtatott PIV hitelesítő adatok](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) a www.nccoe.nist.gov címen.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>A Graph API használatával adja meg a helyszíni egyszerű felhasználónevet változóként a SCEP-tanúsítványok számára.<!--  5437939        -->  
Az [Intune-Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)használatakor megadhatja a onPremisesUserPrincipalName változóként a tulajdonos alternatív NEVEKÉNT (San) a SCEP-tanúsítványokhoz.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>2019. szeptember 23-i hét

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>iOS-felhasználók regisztrációja az előzetes verzióban<!-- 4817900 -->
Az Apple iOS 13,1 kiadásában a felhasználók beléptetése, valamint az iOS-eszközökhöz készült egyszerűsített felügyelet új formája szerepel. A személyes tulajdonú eszközök esetében az eszközök beléptetése vagy az automatikus eszközök beléptetése (korábban Készülékregisztrációs program) helyett is felhasználható. Az Intune előzetes verziója a következő lépésekkel támogatja a szolgáltatáskészlet támogatását:

- Felhasználói csoportokba való felhasználói regisztráció megcélzása.
- Lehetővé teszi a végfelhasználók számára, hogy az eszközük regisztrálásakor a könnyebb felhasználói regisztráció vagy erősebb eszközök beléptetése között választhatnak.

Az iOS 13,1-es verziójától kezdődően a 9/24/2019-es verziótól kezdve a frissítések minden ügyfelünk számára elérhetők lesznek, és a következő hét végére várhatóan befejeződtek.
A következőre érvényes

iOS 13,1 és újabb verziók

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune-támogatás a iPadOS és az iOS 13,1-eszközökhöz<!--5439574-->
Az Intune mostantól támogatja a iPadOS és az iOS 13,1-eszközök kezelését is. További információkat [ebben a blogban](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094) talál.

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>2019. szeptember 16-i hét (1909 szolgáltatás kiadása)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Alkalmazáskezelés 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Felügyelt Google Play Private LOB-alkalmazások<!-- 1464182  -->
Az Intune mostantól lehetővé teszi a rendszergazdák számára, hogy privát Android LOB-alkalmazásokat tegyenek közzé a Google Play szolgáltatásban az Intune-konzolon beágyazott iframe használatával.  Korábban a rendszergazdák számára szükséges, hogy a LOB-alkalmazásokat közvetlenül a Google Play közzétételi konzolján tegye közzé, amely több lépést igényelt, és időigényes volt. Ez az új funkció lehetővé teszi a LOB-alkalmazások egyszerű közzétételét a lépések minimális készletével anélkül, hogy az Intune-konzolt el kellene hagynia.  A rendszergazdáknak többé nem kell manuálisan regisztrálniuk a Google-fejlesztőként, és a továbbiakban nem kell fizetniük a Google $25 regisztrációs díját.  A felügyelt Google Play szolgáltatást használó androidos vállalati felügyeleti forgatókönyvek bármelyike kihasználhatja ezt a funkciót (munkahelyi profil, dedikált, teljes körűen felügyelt és nem regisztrált eszközök). Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**elemet. Ezután válassza a **felügyelt Google Play** lehetőséget az **alkalmazás típusa** listából. A felügyelt Google Play-alkalmazásokkal kapcsolatos további információkért lásd: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](../apps/apps-add-android-for-work.md)-nal.

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows Céges portál-élmény<!-- 1473353, 3598357 -->
A Windows Céges portál frissítése folyamatban van. Az alkalmazások lapon több szűrőt is használhat a Windows Céges portálon belül. Az eszköz részletes felhasználói felülete is frissül. Ezen frissítések minden ügyfelünk számára folyamatban vagyunk, és a következő hét végére várhatóan elvégezhető.

#### <a name="macos-support-for-web-apps---3174427---"></a>macOS-támogatás webes alkalmazásokhoz<!-- 3174427 -->
Webalkalmazások, amelyek lehetővé teszik a webes URL-címekhez való parancsikonok hozzáadását a Dockon a macOS Céges portál használatával. A végfelhasználók a macOS Céges portál webalkalmazáshoz tartozó alkalmazás részletei lapon érhetik el a **telepítési** műveletet. A **Webhivatkozás** alkalmazás típusával kapcsolatos további információkért lásd: [alkalmazások hozzáadása a Microsoft Intunehez](../apps/apps-add.md) és [webalkalmazások hozzáadása Microsoft Intunehoz](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>a macOS-alkalmazások macOS-támogatása<!-- 3173501  -->
az Apple Business Managerrel megvásárolt macOS-alkalmazások a konzolon jelennek meg, amikor az Apple VPP-tokenek szinkronizálva vannak az Intune-ban. Az Intune-konzollal rendelhet hozzá, vonhat vissza és rendelhet hozzá eszközöket és felhasználó-alapú licenceket a csoportokhoz. A Microsoft Intune segítségével kezelheti a vállalat által a cégnél való használatra megvásárolt VPP-alkalmazásokat:

- Licencinformációk jelentése az App Store-ból.
- A felhasznált licencek számának nyilvántartása.
- Segít megelőzni az alkalmazás több példányának telepítését, mint amennyit Ön birtokol.

Az Intune-nal és a VPP-vel kapcsolatos további információkért lásd: [mennyiségi programban vásárolt alkalmazások és könyvek kezelése Microsoft Intuneokkal](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Felügyelt Google Play iframe-támogatás<!-- 2871756  -->
Az Intune mostantól támogatást nyújt a webhivatkozások hozzáadásához és kezeléséhez közvetlenül az Intune-konzolon a felügyelt Google Play iframe használatával.  Ez lehetővé teszi, hogy a rendszergazdák elküldjék az URL-címet és az ikont, majd ezeket a hivatkozásokat a normál Android-alkalmazásokhoz hasonló eszközökre telepítse. A felügyelt Google Play szolgáltatást használó androidos vállalati felügyeleti forgatókönyvek bármelyike kihasználhatja ezt a funkciót (munkahelyi profil, dedikált, teljes körűen felügyelt és nem regisztrált eszközök). Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**elemet. Ezután válassza a **felügyelt Google Play** lehetőséget az **alkalmazás típusa** listából. A felügyelt Google Play-alkalmazásokkal kapcsolatos további információkért lásd: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](../apps/apps-add-android-for-work.md)-nal.

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Android LOB-alkalmazások csendes telepítése a zebra-eszközökön<!-- 4252734  -->
Ha az androidos üzletági (LOB) alkalmazásokat a [Zebra-eszközökre](../configuration/android-zebra-mx-overview.md)telepíti, és nem kéri a LOB-alkalmazás letöltését és telepítését, akkor az alkalmazást csendesen is telepítheti. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**elemet. Az **Alkalmazás hozzáadása** panelen válassza az **Üzletági alkalmazás** lehetőséget. További információ: [androidos üzletági alkalmazás hozzáadása a Microsoft Intunehoz](../apps/lob-apps-android.md).

Jelenleg a LOB-alkalmazás letöltése után a rendszer **letölti a sikerről** szóló értesítést a felhasználó eszközén. Az értesítés csak akkor törölhető, ha az értesítési árnyékban az **összes törlése** elemre koppint. Ez az értesítési probléma egy közelgő kiadásban fog megjelenni, és a telepítés teljesen csendes marad, és nem jelenik meg vizuális mutató.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Az Intune-alkalmazások Graph API műveleteinek olvasása és írása<!-- 5031704  -->
Az alkalmazások az Intune-Graph API az olvasási és írási műveletekkel is meghívhatják az alkalmazás identitása felhasználói hitelesítő adatok nélkül. További információ az Intune-hoz készült Microsoft Graph API eléréséről: az [Intune használata a Microsoft Graphban](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Az iOS-hez készült Intune app SDK védett adatmegosztása és titkosítása<!-- 3586942  -->
Az iOS-hez készült Intune app SDK 256 bites titkosítási kulcsokat használ, ha az adatvédelmi szabályzatok lehetővé teszik a titkosítást. Minden alkalmazásnak rendelkeznie kell egy SDK-verzió 8.1.1 a védett adatmegosztás engedélyezéséhez.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Az iOS rendszerhez készült IKEv2 VPN-profilok támogatása<!-- 1943438   -->
Ebben a frissítésben VPN-profilokat hozhat létre az iOS natív VPN-ügyfél számára a IKEv2 protokoll használatával. A IKEv2 új kapcsolattípus az **eszköz konfigurációja** > **profiljaiban** > **profil létrehozása** > **iOS** for platform > **VPN** a profil típusa > **kapcsolattípus**.

Ezek a VPN-profilok a natív VPN-ügyfelet konfigurálja, így a rendszer nem telepíti a VPN-ügyfélszoftvert, és nem küldi azokat a felügyelt eszközökre Ehhez a szolgáltatáshoz regisztrálni kell az eszközöket az Intune-ban (MDM-regisztráció).

Az aktuálisan konfigurálható VPN-beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS-eszközökön](../configuration/vpn-settings-ios.md)című témakört.

A következőre érvényes
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>A regisztrációs típus megjeleníti az eszközök funkcióit, az eszközök korlátozásait és a bővítményi profilokat az iOS-és macOS-beállításokhoz.<!-- 4886161   -->

Az Intune-ban létrehozhat profilokat az iOS-és macOS-eszközökhöz (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **iOS** vagy **MacOS** platform > **eszköz funkciói**, **eszköz-korlátozások**vagy **bővítmények** a profil típusa esetén). 

Ebben a frissítésben az Intune-portálon elérhető beállítások a beléptetési típus szerint vannak kategorizálva:

- iOS
  - Felhasználói regisztráció
  - Eszközök beléptetése
  - Automatikus eszközök beléptetése (felügyelt)
  - Minden regisztrációs típus

- macOS
  - Felhasználó által jóváhagyott
  - Eszközök beléptetése
  - Automatikus eszközök beléptetése
  - Minden regisztrációs típus

A következőre érvényes
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>A teljes képernyős módban futó, felügyelt iOS-eszközök új hang-vezérlési beállításai<!-- 4892835   -->
Az Intune-ban házirendeket hozhat létre a felügyelt iOS-eszközök kioszkként való futtatásához, vagy dedikált eszközként (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** platformon > **eszköz-korlátozások** a profil típusa > **kioszk**).

Ebben a frissítésben új beállítások vezérelhetők:
- **Hangvezérlés**: lehetővé teszi a hangvezérelt vezérlést az eszközön kioszk módban.
- A **hangvezérlés módosítása**: lehetővé teszi a felhasználók számára, hogy kioszk módban módosítsák az eszköz hangvezérlési beállítását.

Az aktuális beállítások megjelenítéséhez nyissa meg az [iOS kioszk beállításait](../configuration/device-restrictions-ios.md#kiosk).

A következőre érvényes
- iOS 13,0 és újabb verziók

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Egyszeri bejelentkezés használata az iOS-és macOS-eszközökön futó alkalmazásokhoz és webhelyekhez<!-- 4893175   -->
Ebben a frissítésben az iOS-és macOS-eszközökre vonatkozó új egyszeri bejelentkezési beállítások vannak (az**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** vagy **MacOS** a platform > **eszköz funkciói** a profil típusa).

Ezekkel a beállításokkal konfigurálhatja az egyszeri bejelentkezési élményt, különösen a Kerberos-hitelesítést használó alkalmazásokhoz és webhelyekhez. Választhat egy általános hitelesítő adatok egyszeri bejelentkezési alkalmazás-bővítménye és az Apple beépített Kerberos-bővítménye közül.

Az eszköz aktuálisan konfigurálható szolgáltatásainak megtekintéséhez nyissa meg az [iOS-eszközök funkcióit](../configuration/ios-device-features-settings.md) és a [MacOS-eszközök funkcióit](../configuration/macos-device-features-settings.md).

A következőre érvényes
- iOS 13,0 és újabb verziók
- macOS 10,15 és újabb verziók

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Tartományok hozzárendelése macOS-10.15 és-eszközökön futó alkalmazásokhoz<!-- 4898079   -->
MacOS-eszközökön különböző funkciókat konfigurálhat, és leküldheti ezeket a funkciókat az eszközökre egy házirend használatával (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **MacOS** platformon > **eszköz funkciói** a profil típusa). Ebben a frissítésben tartományokat rendelhet az alkalmazásaihoz. Ez a szolgáltatás segít megosztani a hitelesítő adatokat az alkalmazással kapcsolatos webhelyekkel, és használható az Apple egyszeri bejelentkezési bővítménnyel, az univerzális hivatkozásokkal és a jelszavak automatikus kitöltésével. 

Az aktuálisan konfigurálható szolgáltatások megjelenítéséhez nyissa meg a [MacOS-eszköz szolgáltatás beállításait az Intune-ban](../configuration/macos-device-features-settings.md).

A következőre érvényes
- macOS 10,15 és újabb verziók

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Az iOS-es felügyelt eszközökön lévő alkalmazások megjelenítéséhez vagy elrejtéséhez használja az iTunes alkalmazás-áruház URL-címe "iTunes" és "alkalmazások" elemét.<!-- 4928474   --> 
Az Intune-ban szabályzatokat hozhat létre a felügyelt iOS-eszközökön lévő alkalmazások megjelenítéséhez vagy elrejtéséhez (az**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** platformon > **eszközre vonatkozó korlátozások** a profil típusa > az **alkalmazások megjelenítése vagy elrejtése**). 

Megadhatja az iTunes App Store-beli URL-címét, például `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. Ebben a frissítésben a `apps` és a `itunes` is használható az URL-címben, például:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

További információ ezekről a beállításokról: [alkalmazások megjelenítése vagy elrejtése](../configuration/device-restrictions-ios.md#show-or-hide-apps).

A következőre érvényes
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>A Windows 10-es megfelelőségi szabályzat jelszavának típusa világosabb és egyező CSP<!-- 5138985 -->
Windows 10 rendszerű eszközökön létrehozhat olyan megfelelőségi szabályzatot, amely bizonyos jelszó-szolgáltatásokat igényel (**eszköz megfelelőségi** > **szabályzatok** , > a platform > **rendszerbiztonsága** > a **Windows 10-es és újabb** **házirendek létrehozása** ). Ebben a frissítésben:
- A **jelszó típusú** értékek világosabbak, és frissülnek, hogy megfeleljenek a [DEVICELOCK/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)-nek.
- A **jelszó lejárati ideje (nap)** beállítás frissült, így az 1-730 napos értékek is megengedettek. 

A Windows 10 megfelelőségi beállításaival kapcsolatos további információkért lásd: [Windows 10 és újabb beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez](../protect/compliance-policy-create-windows.md). 

A következőre érvényes
- Windows 10 és újabb

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Frissített felhasználói felület a Microsoft Exchange helyszíni hozzáférésének konfigurálásához<!-- 4092920 -->  
Frissítettük a konzolt, ahol a [Microsoft Exchange helyszíni hozzáférését konfigurálja](../protect/conditional-access-exchange-create.md). A helyszíni Exchange-hozzáférés összes konfigurációja már elérhető a konzol ugyanazon paneljén, ahol *engedélyezheti a helyszíni Exchange-hozzáférés-vezérlést*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Alkalmazás-widgetek a kezdőképernyőn való hozzáadásának engedélyezése vagy korlátozása Android Enterprise Work profiling-eszközökön<!-- 1109650  --> 
Az Android Enterprise rendszerű eszközökön a munkahelyi profil funkcióit (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Android enterprise** for platform > **munkahelyi profil csak > eszköz korlátozásai** ). Ebben a frissítésben engedélyezheti a felhasználóknak, hogy a munkahelyi profil alkalmazásai által közzétett widgeteket adjanak az eszköz kezdőlapjára.

A konfigurálható beállítások megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

A következőre érvényes
- Androidos vállalati munkahelyi profil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Az új bérlők alapértelmezetten az Android-eszközök rendszergazdájának felügyeletével lesznek elérhetők<!-- 4869790   -->
Az Android rendszerű eszközök rendszergazdai képességeit az Android Enterprise váltja fel. Ezért javasoljuk, hogy az Android Enterprise új regisztrációkat használjon. Egy későbbi frissítés során az új bérlőknek a következő előfeltételeket kell végrehajtaniuk az Android-regisztrációban az eszköz rendszergazdai felügyeletének használatához: Nyissa meg az **Intune** > **eszközök regisztrációja** > **Android-regisztráció** > **személyes és vállalati tulajdonú eszközök az eszköz rendszergazdai jogosultságával** > az **eszköz rendszergazdája az eszközök**felügyeletéhez lehetőséget.

A meglévő bérlők semmilyen változást nem fognak tapasztalni a környezetében.

További információ az Android-eszközök rendszergazdájáról az Intune-ban: [Android-eszközök rendszergazdai regisztrációja](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>A profilhoz társított DEP-eszközök listája<!-- 5012045 idmiss -->
Most már megtekintheti a profilhoz társított Apple automatizált Készülékregisztrációs program (DEP) eszközök lapozható listáját. A listában bármelyik oldalról kereshet. A lista megjelenítéséhez nyissa meg az **Intune** > **eszközök beléptetése** > az **Apple-regisztráció** > a **beléptetési program jogkivonatait** > Válassza ki a tokent > **profilok** > válasszon egy profilt > **hozzárendelt eszközöket** (a **figyelő**alatt).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Eszközkezelés

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>További Android teljes körűen felügyelt támogatás<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Az Android teljes körűen felügyelt eszközeihez a következő támogatást adtuk hozzá:

- A teljes körűen felügyelt Android-tanúsítványok SCEP tanúsítványokat biztosítanak az eszköz tulajdonosként felügyelt eszközökön. A SCEP-tanúsítványok már támogatottak a munkahelyi profil eszközein.  Az SCEP-tanúsítványokkal a következőket teheti: <!-- 5227935 -->
    - SCEP-profil létrehozása az Android Enterprise DO szakaszban
    - SCEP-tanúsítványok csatolása Wi-Fi-profil hitelesítéshez
    - SCEP-tanúsítványok csatolása a VPN-profilokhoz hitelesítéshez
    - SCEP-tanúsítványok csatolása e-mail-profilokhoz a hitelesítéshez (AppConfig keresztül)
- A rendszeralkalmazások az Android Enterprise rendszerű eszközökön támogatottak. Az Intune-ban adjon hozzá egy androidos nagyvállalati rendszeralkalmazást, és válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**lehetőséget. Az **alkalmazás típusa** listában válassza az **Android Enterprise System app**elemet. További információ: [androidos nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz](../apps/apps-ae-system.md). <!-- 4062195 -->
- Az **eszközök megfelelősége** > az **Android Enterprise** > **eszköz tulajdonosa**, létrehozhat egy megfelelőségi szabályzatot, amely beállítja a Google biztonság igazolási szintjét.   <!-- 4631425 -->
- Az Android Enterprise teljes körűen felügyelt eszközökön a Mobile Threat Defense-szolgáltatók támogatottak. Az **eszközök megfelelősége** > az **Android Enterprise** > **eszköz tulajdonosa**lehetőség van egy elfogadható veszélyforrási szint kiválasztására. <!-- 4631440 --> Az [Android vállalati beállítások az eszközök megfelelő vagy nem megfelelőként való megjelölésére az Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) -ban az aktuális beállítások szerepelnek.
- Az Android Enterprise teljes körűen felügyelt eszközökön a Microsoft Launcher alkalmazás mostantól az alkalmazás-konfigurációs szabályzatok segítségével konfigurálható, hogy lehetővé váljon a teljes körűen felügyelt eszközön a szabványosított végfelhasználói élmény. Az Android-eszköz személyre szabásához használhatja a Microsoft Launcher alkalmazást. Az alkalmazással Microsoft-fiók vagy munkahelyi/iskolai fiókkal is elérheti a naptárt, a dokumentumokat és a legutóbbi tevékenységeket a személyre szabott hírcsatornában. <!-- 5334044 -->

Ezzel a frissítéssel örömmel jelentjük be, hogy az Android Enterprise teljes körűen felügyelt Intune-támogatás már általánosan elérhető.

A következőre érvényes

- Android Enterprise teljes körűen felügyelt eszközök

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Egyéni értesítések küldése egyetlen eszközre<!-- 4928910 -->
Most már kijelölhet egyetlen eszközt, majd egy távoli eszköz művelettel [Egyéni értesítéseket küldhet csak erre az eszközre](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>A törlés és a PIN-kód átállítása művelet nem érhető el a felhasználói regisztráció használatával beléptetett iOS-eszközökön<!-- 4950491 -->
A felhasználó beléptetése új típusú Apple-eszközök beléptetése. Ha felhasználói beléptetést használó eszközöket regisztrál, a törlés és a jelszó-visszaállítás távoli műveletei nem lesznek elérhetők az ilyen eszközökön.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune-támogatás iOS 13-és macOS-eszközökhöz<!-- 4665317 -->
Az Intune mostantól támogatja az iOS 13 és macOS Catalina eszközök felügyeletét.
További információkért lásd az [iOS 13 és a iPadOS Microsoft Intune támogatását ismertető blogbejegyzést](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Eszköz biztonsága

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>BitLocker-támogatás az ügyfél által vezérelt helyreállítási jelszó elforgatásához<!--  3444125 -->
Az Intune-Endpoint Protection beállítások segítségével konfigurálhatja az [ügyfél által vezérelt helyreállítási jelszavakat](../protect/endpoint-protection-windows-10.md#windows-encryption) a Bitlockerhez a Windows 1909-es vagy újabb verzióját futtató eszközökön.

Ez a beállítás egy, az operációsrendszer-meghajtó helyreállítása után (a Csizmadia vagy a WinRE használatával) és a helyreállítási jelszó zárolásának feloldása után kezdeményezi az ügyfél által vezérelt helyreállítási jelszó frissítését egy rögzített adatmeghajtón. Ez a beállítás frissíti a használt helyreállítási jelszót, és a köteten található egyéb nem használt jelszavak változatlanok maradnak. További információ: a BitLocker CSP dokumentációja a [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Illetéktelen védelem a Windows Defender Víruskeresőben<!-- 4705448        -->
Az Intune használatával kezelheti a Windows Defender víruskereső *illetéktelen hozzáférést biztosító védelmét* . Az [illetéktelen hozzáférést biztosító védelem beállítását](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) a Microsoft Defender Security Center csoportjában találja, ha a Windows 10-es végpontok védelméhez eszköz-konfigurációs profilokat használ. Beállíthatja, hogy az illetéktelen hozzáférést *engedélyező* védelem bekapcsolja a Temper Protection-korlátozásokat, *Letiltva* a kikapcsolását, vagy beállíthatja, hogy a rendszer*ne* állítsa be az eszközök aktuális konfigurációját.  

További információ az illetéktelen hozzáférést biztosító védelemről: a [biztonsági beállítások módosításának megakadályozása](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) a Windows dokumentációjában.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Mostantól általánosan elérhető a Windows Defender-tűzfal speciális beállításai<!--  5317392       -->  
A [Windows Defender egyéni tűzfalszabályok az Endpoint Protection számára](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), amelyet az eszköz konfigurációs profiljának részeként konfigurál, a szolgáltatás nem nyilvános előzetes verzióban érhető el, és általánosan elérhető (GA).  Ezekkel a szabályokkal megadhatja a bejövő és kimenő viselkedést az alkalmazásokhoz, a hálózati címekhez és a portokhoz. Ezek a szabályok júliusban lettek közzétéve nyilvános előzetes verzióként. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>A hatókör-címkék mostantól támogatják a Használati szabályzatok használati feltételeit<!-- 2358863 idmiss -->
Mostantól hozzárendelheti a [hatókörhöz tartozó címkéket](scope-tags.md) a használati szabályzatokhoz. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **feltételek és kikötések** > válasszon egy elemet a listáról > **Tulajdonságok** > **hatókör címkék** > válasszon hatókör címkét.

## <a name="week-of-september-9-2019"></a>2019. szeptember 9. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Microsoft Intune alkalmazás frissítései<!-- 4997846 -->
Az Android rendszerhez készült Microsoft Intune alkalmazás a következő továbbfejlesztett funkciókkal bővült:
- Frissítve és javította az elrendezést, hogy a legfontosabb műveleteknél a legalsó szintű Navigálás szerepeljen.
- Hozzáadott egy további oldalt, amely megjeleníti a felhasználó profilját.
- Az alkalmazásban a felhasználó számára elérhető végrehajtható értesítések megjelenítése, például az eszköz beállításainak frissítése szükséges.
- Az egyéni leküldéses értesítések megjelenítése, az alkalmazás igazítása az iOS és Android rendszerhez készült Céges portál alkalmazásban nemrégiben hozzáadott támogatással. További információt [az egyéni értesítések küldése az Intune-ban](../remote-actions/custom-notifications.md)című témakörben talál.

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál<!-- 4394993 -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön. További információ: [a Intune céges portál alkalmazás konfigurálása](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>2019. szeptember 2. hét

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune felhasználói felület frissítése – bérlői állapot irányítópultja<!-- 5273210  -->
A bérlői állapot irányítópultjának felhasználói felülete frissítve lett az Azure felhasználói felületi stílusokkal való összehangoláshoz. További információ: [bérlői állapot](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>2019. augusztus 26. hét

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>A Microsoft Edge-beállítások konfigurálása a Windows 10 és újabb rendszerhez készült felügyeleti sablonok használatával<!-- 5228061 -->

Windows 10 és újabb rendszerű eszközökön felügyeleti sablonokat hozhat létre az Intune csoportházirend-beállításainak konfigurálásához. Ebben a frissítésben olyan beállításokat adhat meg, amelyek a Microsoft Edge 77-es vagy újabb verziójára vonatkoznak.

A felügyeleti sablonokkal kapcsolatos további információkért lásd: [Windows 10 sablonok használata a csoportházirend-beállítások konfigurálásához az Intune-ban](../configuration/administrative-templates-windows.md).

A következőre érvényes

- Windows 10 és újabb (Windows RS4 +)

## <a name="week-of-august-12-2019-1908-service-release"></a>2019. augusztus 12-i hét (1908 szolgáltatás kiadása)

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>IOS-alkalmazások eltávolítási viselkedésének szabályozása az eszköz regisztrációjának törlése során<!-- 3504144   -->
A rendszergazdák kezelhetik, hogy egy alkalmazás el lett-e távolítva vagy meg van-e őrizni az eszközön, ha az eszköz regisztrálva van a felhasználó vagy az eszköz csoport szintjén. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Üzleti alkalmazások kategorizálása Microsoft Store<!-- 3926922 -->
A vállalati alkalmazások Microsoft Store kategorizálható. Ehhez válassza az **Intune** > **ügyfélalkalmazások** > **alkalmazások** lehetőséget, > válassza ki a Microsoft Store for Business App > **alkalmazás adatai** > **kategóriát**. A legördülő menüben rendeljen hozzá egy kategóriát.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Testreszabott értesítések Microsoft Intune alkalmazás felhasználói számára<!-- 4843354  -->
Az Androidhoz készült Microsoft Intune alkalmazás mostantól támogatja az egyéni leküldéses értesítések megjelenítését, valamint az iOS és Android rendszerhez készült Céges portál alkalmazásokban nemrégiben hozzáadott támogatással való összehangolását. További információt [az egyéni értesítések küldése az Intune-ban](../remote-actions/custom-notifications.md)című témakörben talál.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Új funkciók androidos vállalati dedikált eszközökhöz többalkalmazásos módban<!-- 3755304 3041943 3041946   -->

Az Intune-ban a funkciók és a beállítások az androidos vállalati dedikált eszközökön (**eszköz-konfiguráció** > **profilok** ) teljes képernyős környezetben vezérelhetők, > **profilokat hozhat létre** > **Android Enterprise** for platform > **eszköz tulajdonosa, az eszközre vonatkozó korlátozások** a profil típusa esetén).

Ebben a frissítésben a következő szolgáltatások lesznek hozzáadva:

- **Dedikált eszközök** **többalkalmazásos** > : a **virtuális Kezdőlap gomb** megnyomásával megjeleníthető az eszközön, vagy a képernyőn lebegve, hogy a felhasználók áthelyezhetik azt.
- **Dedikált eszközök** **többalkalmazásos** > : a **zseblámpa-hozzáférés** lehetővé teszi a felhasználók számára a zseblámpa használatát. 
- **Dedikált eszközök** > **multi-app**: a **Media Volume Control** lehetővé teszi a felhasználóknak, hogy az eszköz adathordozó-kötetét egy csúszka használatával szabályozzák. 
- **Dedikált eszközök** > **többalkalmazásos**: **képernyővédő engedélyezése**, egyéni rendszerkép feltöltése és a képernyővédő megjelenítésének vezérlése.

Az aktuális beállítások megtekintéséhez lépjen az [Android Enterprise Device Settings elemre az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

A következőre érvényes

- Androidos vállalati dedikált eszközök

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Új alkalmazás-és konfigurációs profilok Android Enterprise teljes körűen felügyelt eszközökhöz<!-- 3574215 3574238 3574235 3574232   -->
A profilok használatával olyan beállításokat konfigurálhat, amelyek a VPN-, e-mail-és Wi-Fi-beállításokat alkalmazzák az androidos vállalati eszköz tulajdonos (teljes mértékben felügyelt) eszközeire. Ebben a frissítésben a következőket teheti:

- Alkalmazás- [konfigurációs szabályzatok](../apps/app-configuration-policies-use-android.md) használatával telepítheti az Outlook, a Gmail és a Nine Work e-mail-beállításait.
- A [megbízható főtanúsítványok beállításainak](../protect/certificates-configure.md)üzembe helyezéséhez használjon eszköz-konfigurációs profilokat.
- A VPN-és [Wi-Fi-](../configuration/wi-fi-settings-android-enterprise.md) beállítások üzembe helyezéséhez használjon eszköz [-](../configuration/vpn-settings-android-enterprise.md) konfigurációs profilokat.

> [!IMPORTANT]
> Ezzel a funkcióval a felhasználók a VPN-, Wi-Fi-és e-mail-profilokhoz tartozó felhasználónevével és jelszavával hitelesítik magukat. A tanúsítvány alapú hitelesítés jelenleg nem érhető el.

A következőre érvényes  
- Androidos vállalati eszköz tulajdonosa (teljes mértékben felügyelt)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>A macOS-eszközökre való bejelentkezéskor megnyíló alkalmazások, fájlok, dokumentumok és mappák szabályozása<!--3914202   -->
A macOS-eszközökön engedélyezheti és konfigurálhatja a szolgáltatásokat (az**eszköz konfigurációjának** > **profiljait** , > **profilt hozhat létre** > **MacOS** platformon > **eszköz-funkciók** a profil típusa esetén). 

Ebben a frissítésben új bejelentkezési elemek beállításával szabályozhatja, hogy mely alkalmazások, fájlok, dokumentumok és mappák nyílnak meg, amikor a felhasználó bejelentkezik a regisztrált eszközre. 

Az aktuális beállítások megtekintéséhez válassza a [MacOS-eszköz szolgáltatás beállításai az Intune-ban](../configuration/macos-device-features-settings.md)lehetőséget.

A következőre érvényes  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>A határidők lecserélik a Windows Update gyűrűk lefoglalt újraindítási beállításait<!-- 4464404        -->
A legutóbbi Windows- [karbantartási változások](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)összehangolásához az Intune Windows 10-es frissítési gyűrűk mostantól [támogatják a határidők beállításait](../protect/windows-update-settings.md). A *határidők* határozzák meg, hogy egy eszköz Mikor telepítse a szolgáltatást és a biztonsági frissítéseket.  A Windows 10 1903-es vagy újabb verzióját futtató eszközökön a *határidők* felülírják a *felvállalt újraindítási*konfigurációkat.  A jövőben a *határidők* felülírják a Windows 10 korábbi verzióiban a megjelenő *újraindítást* is.  

Ha nem konfigurálja a *határidőket*, az eszközök továbbra is használják a kapcsolódó *Újraindítási* beállításokat, azonban az Intune a későbbi frissítésekben nem fogja támogatni a felvállalt újraindítási beállítások támogatását.  

Tervezze meg a *határidők* használatát a Windows 10-es eszközökön. A *határidők* beállításainak megadása után módosíthatja az Intune-konfigurációkat, hogy a rendszer ne konfigurálja a folyamatban lévő *újraindítást* . Ha a nincs konfigurálva értékre van állítva, az Intune leállítja a beállítások kezelését az eszközökön, de nem távolítja el a beállítás utolsó konfigurációját az eszközről. Ezért a *felvállalt újraindításhoz* beállított utolsó konfigurációk aktív állapotban maradnak, és csak az Intune-tól eltérő módon módosítják ezeket a beállításokat. Később, amikor az eszközök Windows-verziója megváltozik, vagy ha a *határidőkhöz* tartozó Intune-támogatás a Windows rendszerű eszközökre bővül, az eszköz a már meglévő új beállításokat fogja használni.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Több Microsoft Intune tanúsítvány-összekötő támogatása<!--   4704642      -->
Az Intune mostantól támogatja több Microsoft Intune tanúsítvány-összekötő telepítését és használatát [a PKCS-műveletekhez](../protect/certficates-pfx-configure.md). Ez a változás támogatja a terheléselosztást és az összekötő magas rendelkezésre állását. Minden összekötő-példány feldolgozhatja a tanúsítványkérelmek az Intune-ból.  Ha az egyik összekötő nem érhető el, a többi összekötő továbbra is feldolgozza a kérelmeket.

Több összekötő használatához nincs szükség az összekötő szoftver legújabb verziójára való frissítésre.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Új beállítások és meglévő beállítások módosítása az iOS-és macOS-eszközök funkcióinak korlátozásához<!-- 4867699 4867709   -->
Létrehozhat olyan profilokat, amelyekkel korlátozhatja az iOS és macOS rendszerű eszközök beállításait (az**eszköz konfigurációjának** > **profiljai** > **profil létrehozása** > **iOS** vagy **MacOS** a platform típusa > **eszköz korlátozásai**). Ez a frissítés a következő funkciókat tartalmazza:

- A **macos** > **eszköz korlátozásai** > a **felhő és a tárolás**szolgáltatásban az új **handoff** beállítással letilthatja a felhasználók számára a munkát egy MacOS-eszközön, és folytathatja a munkát egy másik MacOS vagy iOS rendszerű eszközön.

  Ha szeretné megtekinteni az aktuális beállításokat, lépjen a [MacOS eszközbeállítások lehetőségre, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-macos.md).

- Az **iOS** > **eszköz korlátozásai**esetében néhány változás van:

  - **Beépített alkalmazások** > **Keresés az iPhone-ban (csak felügyelt eszköz esetén)** : új beállítás, amely letiltja ezt a funkciót a Find My app szolgáltatásban. 
  - **Beépített alkalmazások** > a **barátok megkeresése (csak felügyelt eszköz esetén)** : új beállítás, amely letiltja ezt a funkciót a Find My app szolgáltatásban. 
  - Wi-Fi állapot **vezeték nélküli** > **módosítása (csak felügyelt eszköz esetén)** : új beállítás, amely megakadályozza, hogy a felhasználók bekapcsolják vagy kikapcsolják a Wi-Fi-t az eszközön.
  - **Billentyűzet és szótár** > **QuickPath (csak felügyelt eszköz esetén)** : új beállítás, amely letiltja a QuickPath funkciót.
  - **Felhő és tárolás**: a **tevékenység folytatását** a rendszer átnevezi a **handoff**.

  Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

A következőre érvényes  
- macOS 10,15 és újabb verziók
- iOS 13 és újabb verziók

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Néhány nem felügyelt iOS-eszközre vonatkozó korlátozás csak az iOS 13,0-es kiadással lesz felügyelve<!-- 4867809   -->
Ebben a frissítésben egyes beállítások csak a felügyelt eszközökre vonatkoznak az iOS 13,0 kiadással. Ha ezek a beállítások az iOS 13,0-es kiadás előtt konfigurálhatók és nem felügyelt eszközökhöz vannak hozzárendelve, a rendszer továbbra is alkalmazza a beállításokat a nem felügyelt eszközökre. Az eszközök az iOS 13,0-re való frissítés után is érvényben maradnak. Ezek a korlátozások el lesznek távolítva a nem felügyelt eszközökön, amelyek biztonsági mentése és visszaállítása megtörtént.

Ezek a beállítások a következők:

- Alkalmazás-áruház, dokumentumok megtekintése, játékok
  - Alkalmazás-áruház
  - Explicit iTunes, zene, podcast vagy Hírek tartalma
  - Game Center ismerősök hozzáadása
  - Több résztvevős játék
- Beépített alkalmazások
  - Fényképezőgép
    - FaceTime
  - Safari
    - Automatikus kitöltés
- Felhő és tárolás
  - Biztonsági mentés az iCloudba
  - ICloud-dokumentumok szinkronizálásának letiltása
  - ICloud-kulcstartó szinkronizálásának letiltása

Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

A következőre érvényes  
- iOS 13,0 és újabb verziók

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Továbbfejlesztett eszköz állapota macOS FileVault titkosításhoz<!-- 4944983         -->
A macOS rendszerű eszközökön a FileVault titkosításhoz több [eszköz állapotüzenetek](../protect/encryption-monitor.md#device-encryption-status) is frissültek.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>A jelentések egyes Windows Defender víruskereső-keresési beállításai sikertelen állapotot mutatnak<!-- 5119229 -->
Az Intune-ban házirendeket hozhat létre a Windows Defender víruskereső használatával a Windows 10 rendszerű eszközök vizsgálatához (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **windows 10 és újabb verziók** a platform > **eszközre vonatkozó korlátozások** a profil típusa > **Windows Defender Antivirus**). A jelentéskészítés elvégzéséhez szükséges **napi gyors vizsgálat** és **rendszervizsgálati** idő a sikertelen állapotot jelzi, ha valójában sikeres állapotot jelent. 

Ebben a frissítésben ez a viselkedés kijavítva van. Így a **napi gyors vizsgálat** és a **rendszervizsgálatok elvégzéséhez szükséges** idő a sikeres ellenőrzések sikerességi állapotát jeleníti meg, és sikertelen állapotot jelez, ha a beállítások nem lesznek alkalmazva.

A Windows Defender víruskereső beállításaival kapcsolatos további információkért lásd: [Windows 10 (és újabb) eszközbeállítások, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="default-scope-tags---3702875----"></a>Alapértelmezett hatókör-Címkék<!-- 3702875  -->
Mostantól elérhető egy új beépített alapértelmezett hatóköri címke. A hatóköri címkéket támogató összes nem címkézett Intune-objektum automatikusan hozzá lesz rendelve az alapértelmezett hatókör-címkéhez. Az **alapértelmezett** hatókör címkét a rendszer hozzáadja az összes meglévő szerepkör-hozzárendeléshez a paritásnak a rendszergazdai felülettel való fenntartásához. Ha nem szeretné, hogy a rendszergazda az alapértelmezett hatókör címkével lássa el az Intune-objektumokat, távolítsa el az alapértelmezett hatóköri címkét a szerepkör-hozzárendelésből. Ez a funkció hasonló a System Center Configuration Manager biztonsági hatókörök szolgáltatásához. További információ: a [RBAC és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android beléptetési eszköz rendszergazdai támogatása<!-- 4869749   -->
Az Android-eszköz rendszergazdai beléptetési lehetősége hozzá lett adva az Android-eszközök regisztrálási lapjához (**Intune** > **eszközök regisztrációja** > **Android-regisztráció**). Az Android-eszközök rendszergazdája alapértelmezés szerint továbbra is engedélyezve lesz az összes bérlő esetében.  További információ: Android- [eszközök rendszergazdai regisztrációja](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>További képernyők kihagyása a beállítási Asszisztensben <!--4877451  -->
Készülékregisztrációs program profilokat is beállíthat, hogy kihagyja a következő beállítási asszisztens képernyőket:
- iOS rendszerhez
    - Megjelenését
    - Expressz nyelv
    - Előnyben részesített nyelv
    - Eszközről az eszközre való Migrálás
- MacOS esetén
    - Képernyő időpontja
    - Touch ID beállítása

A beállítási asszisztens testreszabásával kapcsolatos további információkért lásd: [Apple beléptetési profil létrehozása iOS rendszerhez](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) és [Apple regisztrációs profil létrehozása MacOS rendszerhez ](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Felhasználói oszlop hozzáadása az Autopilot-eszköz CSV-feltöltési folyamatához<!-- 3823054 -->
Mostantól hozzáadhat egy felhasználói oszlopot az Autopilot-eszközökhöz tartozó CSV-feltöltéshez. Ez lehetővé teszi a felhasználók tömeges hozzárendelését a CSV importálásakor. További információ: [Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Eszközkezelés

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Az eszköz automatikus törlési időkorlátjának beállítása 30 nap alatt<!--4231059  -->
Megadhatja az automatikus eszköz tisztítási időkorlátját, amely az utolsó bejelentkezés után 30 nap (az előző korlát helyett a 90 nap). Ehhez nyissa meg az **Intune** > - **eszközök** > a **telepítő** > **eszköz tisztítása szabályokat**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Az Android-eszköz hardveres oldalán található szám összeállítása<!-- 4461910   -->
Minden Android-eszköz hardver lapján megjelenik egy új bejegyzés, amely tartalmazza az eszköz operációs rendszerének Build-számát. További információ: [az eszköz adatainak megtekintése az Intune-ban](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Hét augusztus 5-ig, 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>A zebra Technologies egy támogatott OEM OEMConfig az androidos vállalati eszközökön<!-- 4843713 -->

Az Intune-ban létrehozhat eszköz-konfigurációs profilokat, és beállításokat alkalmazhat az androidos vállalati eszközökre a OEMConfig használatával (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **Android Enterprise** for platform > **OEMConfig** ).

Ebben a frissítésben a zebra Technologies a OEMConfig által támogatott eredeti berendezésgyártó (OEM). További információ a OEMConfig-ről: [androidos vállalati eszközök használata és kezelése a OEMConfig](../configuration/android-oem-configuration-overview.md)-mel.

A következőre érvényes  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>2019. július 22-i hét (1907 szolgáltatás kiadása)

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Felhasználók és csoportok testreszabott értesítései<!-- 16766574          -->
Egyéni leküldéses értesítések küldése a Céges portál alkalmazásból az Intune-nal felügyelt iOS-és Android-eszközökön lévő felhasználóknak. Ezek a mobil leküldéses értesítések nagyon testreszabhatók ingyenes szöveggel, és bármilyen célra használhatók. A szervezet különböző felhasználói csoportjaira is megcélozhatja őket. További információ: [Egyéni értesítések](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>A Google eszköz házirend-vezérlő alkalmazás<!-- 3041950  -->
A felügyelt kezdőképernyő alkalmazás mostantól hozzáférést biztosít a Google androidos eszköz házirend-alkalmazásához. A felügyelt kezdőképernyő alkalmazás egy egyéni indító, amelyet az Intune-ban regisztrált eszközökhöz az Android Enterprise (AE) dedikált eszközként használnak többalkalmazásos kioszk mód használatával. Elérheti az Android-eszköz házirend-alkalmazását, vagy megtekintheti a felhasználókat az Android-eszközök házirend-alkalmazásához, támogatási és hibakeresési célból. Ez az indítási képesség akkor érhető el, amikor az eszköz regisztrálja és zárolja a felügyelt kezdőképernyőn. A funkció használatához nincs szükség további telepítésekre.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Az Outlook védelmi beállításai iOS és Android rendszerű eszközökhöz<!-- 3212619 -->
Mostantól az iOS és az Android rendszerhez készült általános alkalmazások és adatvédelem konfigurációs beállításait is konfigurálhatja az egyszerű Intune rendszergazdai vezérlőkkel az eszközök regisztrálása nélkül. Az alkalmazás általános beállításainak megadása a rendszergazdák számára lehetővé teszi, hogy az Outlookot az iOS és az Android rendszerhez a regisztrált eszközökön is kezelhesse. Az Outlook-beállításokkal kapcsolatos további információkért lásd: [az Outlook telepítése iOS-és Android-alkalmazásokhoz konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Az "alkalmazhatósági szabályok" használata Windows 10-es eszközök konfigurációs profiljainak létrehozásakor <!-- 2549910 eeready   idstaged -->

A Windows 10-es eszközök konfigurációs profiljait (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **Windows 10-es** platform > **alkalmazhatósági szabályok**) létrehozásához. Ebben a frissítésben létrehozhat egy **alkalmazhatósági szabályt** , hogy a profil csak egy adott kiadásra vagy adott verzióra vonatkozzon. Létrehozhat például egy olyan profilt, amely lehetővé teszi egyes BitLocker-beállítások használatát. A profil hozzáadása után alkalmazzon egy alkalmazhatósági szabályt, hogy a profil csak a Windows 10 Enterprise rendszert futtató eszközökre vonatkozzon.

Alkalmazhatósági szabály hozzáadásához lásd: [alkalmazhatósági szabályok](../configuration/device-profile-create.md#applicability-rules).

A Windows 10 és újabb verziókra vonatkozik

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>A jogkivonatok használata az eszközre jellemző információk hozzáadásához az egyéni profilokban iOS-és macOS-eszközökhöz<!-- 3330008  -->
Az iOS-és macOS-eszközökön az egyéni profilok használatával konfigurálhatja az Intune-ban nem beépített beállításokat és szolgáltatásokat (az**eszköz konfigurációjának** > **profiljai** > **profil létrehozása** > **iOS** vagy **MacOS** a platformhoz > **Egyéni** profil típusa). Ebben a frissítésben jogkivonatokat adhat hozzá a `.mobileconfig` fájlokhoz az eszközre vonatkozó információk hozzáadásához. Például hozzáadhat `Serial Number: {{serialnumber}}` a konfigurációs fájlhoz az eszköz sorozatszámának megjelenítéséhez.

Egyéni profil létrehozásához tekintse meg az [Egyéni iOS-beállítások](../configuration/custom-settings-ios.md) vagy a MacOS-es [Egyéni beállítások](../configuration/custom-settings-macos.md)című témakört.

A következőre érvényes
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Új Configuration Designer az Android Enterprise-hoz készült OEMConfig-profil létrehozásakor<!-- 3712769   -->
Az Intune-ban létrehozhat egy OEMConfig-alkalmazást használó eszköz-konfigurációs profilt (az eszköz konfigurációjának > profiljait, > profilt hozhat létre > Android Enterprise platformon > OEMConfig). Ha ezt teszi, a rendszer egy JSON-szerkesztőt nyit meg a sablon és az értékek módosításával. 

Ez a frissítés egy továbbfejlesztett felhasználói élményt biztosító konfigurációs tervezőt tartalmaz, amely az alkalmazásban beágyazott részleteket jeleníti meg, beleértve a címeket, a leírásokat és egyebeket. A JSON-szerkesztő továbbra is elérhető, és a Configuration Designerben végrehajtott módosításokat jeleníti meg.

Az aktuális beállítások megtekintéséhez válassza az [androidos vállalati eszközök használata és kezelése a OEMConfig](../configuration/android-oem-configuration-overview.md)-mel című témakört.

A következőkre vonatkozik: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Frissített felhasználói felület a Windows Hello konfigurálásához<!-- 4089576            -->
Frissítettük a konzolt, amelyben az [Intune-t a vállalati Windows Hello használatára konfigurálja](../protect/windows-hello.md). A konfigurációs beállítások mostantól a konzol ugyanazon paneljén érhetők el, ahol engedélyezheti a Windows Hello használatát.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Az Intune PowerShell SDK, amely a Microsoft Graphon keresztül támogatja az Intune API-t, a 6.1907.1.0 verzióra frissült. Az SDK mostantól a következőket támogatja:
- Együttműködik Azure Automationokkal.
- A csak az alkalmazásra vonatkozó hitelesítési olvasási műveleteket támogatja. 
- Támogatja a rövid rövidített neveket aliasként.
- Megfelel a PowerShell elnevezési konvencióinak. Pontosabban a `Connect-MSGraph` parancsmag `PSCredential` paraméterét átnevezték `Credential`re.
- A `Invoke-MSGraphRequest` parancsmag használata esetén a `Content-Type` fejléc értékének manuális megadását támogatja.

További információ: [POWERSHELL SDK Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Regisztrációs korlátozások frissítései<!-- 2871968 -->
Az új bérlők regisztrálási korlátozásai frissültek, így az androidos vállalati munkahelyi profilok alapértelmezés szerint engedélyezve vannak. A meglévő bérlők semmilyen változást nem fognak tapasztalni. Az androidos vállalati munkahelyi profilok használatához továbbra is [össze kell kapcsolnia Intune-fiókját a felügyelt Google Play-fiókkal](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Felhasználói felületi frissítések az Apple-regisztrációhoz és a regisztrációs korlátozásokhoz<!--4089575, 4089579  -->
A következő folyamatok mindegyike egy varázsló stílusú felhasználói felületet használ:
- Apple-eszközök beléptetése. További információ: iOS- [eszközök automatikus regisztrálása az Apple Készülékregisztrációs program](../enrollment/device-enrollment-program-enroll-ios.md).
- Regisztráció korlátozásának létrehozása. További információkért lásd a [regisztrációs korlátozások beállítása](../enrollment/enrollment-restrictions-set.md)című témakört.

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>A vállalati eszközök azonosítóinak előzetes konfigurációjának kezeléséhez Android Q-eszközökhöz<!-- 4711509  idmiss -->
Az Android Q (v10)-ben a Google eltávolítja a MDM-ügynököket a örökölt felügyelt (eszköz-rendszergazda) Android-eszközökön az eszköz-azonosító információk összegyűjtéséhez.  Az Intune olyan funkcióval rendelkezik, amely lehetővé teszi a rendszergazdák számára, hogy [előre konfigurálják az eszközök sorozatszámait vagy IMEI-listáját](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) , hogy automatikusan címkével lássa el ezeket az eszközöket a vállalat tulajdonában. Ez a funkció nem működik az eszköz rendszergazdája által felügyelt Android Q-eszközökön.  Függetlenül attól, hogy az eszköz sorozatszáma vagy IMEI-je fel van-e töltve, a rendszer mindig személyesnek tekinti az Intune-regisztráció során.  A regisztráció után manuálisan is átválthatja a vállalati tulajdont.  Ez csak az új regisztrációkat érinti, és a meglévő regisztrált eszközöket nem érinti.  A munkahelyi profillal felügyelt Android-eszközöket ez a változás nem érinti, és továbbra is működik, ahogy ma.  Emellett az eszköz-rendszergazdaként regisztrált Android Q-eszközök nem tudnak a sorozatszámot vagy IMEI-t jelenteni az Intune-konzolon az eszköz tulajdonságaiként.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Az androidos vállalati regisztrációk (munkahelyi profil, dedikált eszközök és teljes körűen felügyelt eszközök) ikonjai módosultak.<!-- 4977730 -->
Az Android Enterprise beléptetési profilok ikonjai módosultak. Az új ikonok megjelenítéséhez nyissa meg az **Intune** > **beléptetés** > **Android-regisztráció** > a **beléptetési profilok**területen.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows diagnosztikai adatgyűjtés módosítása<!-- 4113859 -->
A diagnosztikai adatgyűjtés alapértelmezett értéke megváltozott a Windows 10 1903-es vagy újabb verzióját futtató eszközökön. A Windows 10 1903-től kezdődően a diagnosztikai adatgyűjtés alapértelmezés szerint engedélyezve van. A Windows diagnosztikai adatok fontos műszaki adatok a Windows-eszközökről az eszközről, valamint a Windows és a kapcsolódó szoftverek működésének módjáról. További információ: [Windows diagnosztikai adatok konfigurálása a szervezetben](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Az Autopilot-eszközök is a "teljes" telemetria vannak kiválasztva, kivéve, ha az Autopilot-profilban nincs más beállítva a [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Eszközkezelés

#### <a name="improve-device-location---3855417----"></a>Az eszköz helyének javítása<!-- 3855417  -->
Az eszköz **megkeresése** művelettel nagyíthatja az eszköz pontos koordinátáit. Az elveszett iOS-eszközök megkeresésével kapcsolatos további információkért lásd: [elveszett iOS-eszközök megkeresése](../remote-actions/device-locate.md).

### <a name="device-security"></a>Eszköz biztonsága

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Speciális beállítások a Windows Defender-tűzfalhoz (nyilvános előzetes verzió)<!--  1311949     -->  
Az Intune használatával kezelheti az egyéni tűzfalszabályok az Endpoint Protection [eszköz konfigurációs profiljának részeként](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) a Windows 10 rendszerben. A szabályok megadhatják a bejövő és kimenő viselkedést az alkalmazásokhoz, a hálózati címekhez és a portokhoz. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Frissített felhasználói felület a biztonsági alapkonfigurációk kezeléséhez<!-- 4091125     -->
A biztonsági alaptervek [létrehozásához és szerkesztéséhez](../protect/security-baselines.md#create-the-profile) az Intune-konzolon frissítettük az élményt. A módosítások a következők:

Egyszerűbb varázsló-stílusú formátum, amely egyetlen panelre van tömörítve. egy panelen belül. Ez az új kialakítás a panel terjeszkedésével foglalkozik, amely megköveteli, hogy az informatikai szakemberek több különálló ablaktáblán is megvizsgálják a részletezést.  
Mostantól a létrehozási és szerkesztési élmény részeként is létrehozhat hozzárendeléseket, ahelyett, hogy később vissza kellene térnie az alaptervek hozzárendeléséhez. Az új alapkonfiguráció létrehozása előtt megtekintheti a beállítások összegzését, és egy meglévőt is szerkeszthet. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok egy kategóriájában beállított elemek listáját jeleníti meg.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019. július 15-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Felügyelt kezdőképernyő és felügyelt beállítások ikonjai<!-- 4918107 -->
Frissült a felügyelt kezdőképernyő alkalmazás ikonja és a **felügyelt beállítások** ikon. A felügyelt kezdőképernyő alkalmazást csak az Intune-ban regisztrált eszközök használják az Android Enterprise (AE) dedikált eszközként, és több alkalmazásból álló kioszk módban futnak. A felügyelt kezdőképernyő alkalmazással kapcsolatos további információkért lásd: [az Android Enterprise rendszerhez készült Microsoft Managed Home Screen alkalmazás konfigurálása](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Androidos eszközök házirendje androidos vállalati dedikált eszközökön<!-- 4918136 -->
Az Android-eszközök házirendje alkalmazást a felügyelt kezdőképernyő alkalmazás hibakeresési képernyőjéről érheti el. A felügyelt kezdőképernyő alkalmazást csak az Intune-ban regisztrált eszközök használják az Android Enterprise (AE) dedikált eszközként, és több alkalmazásból álló kioszk módban futnak. További információ: [az Android Enterprise rendszerhez készült Microsoft Managed Home Screen alkalmazás konfigurálása](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>iOS-Céges portál frissítései<!-- 3902931 -->
Az iOS app Management-kérések vállalatának neve lecseréli az aktuális "i.manage.microsoft.com" szöveget. A felhasználók például a "i.manage.microsoft.com" helyett a cég nevét fogják látni, ha a felhasználók iOS-alkalmazást próbálnak telepíteni a Céges portálról, vagy amikor a felhasználók engedélyezik az alkalmazás felügyeletét. Ezt a rendszer a következő néhány nap során minden ügyfélnek bevezeti.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>FileVault kezelése macOS rendszerhez<!--  3858502 + 4557986 + 1210104  -->
Az Intune segítségével [kezelheti a MacOS-eszközök FileVault-titkosítását](../protect/encrypt-devices.md). Az eszközök titkosításához az Endpoint Protection-eszköz konfigurációs profilját kell használnia.

A FileVault-támogatás magában foglalja a titkosítatlan eszközök titkosítását, az eszközök személyes helyreállítási kulcsának letétjét, a személyes titkosítási kulcsok automatikus vagy manuális elforgatását, valamint a vállalati eszközök legfontosabb lekérését. A végfelhasználók a Céges portál webhelyet is használhatják a titkosított eszközök személyes helyreállítási kulcsának beszerzéséhez.

Kibővítettük a titkosítási jelentést is, hogy a BitLocker melletti [FileVault kapcsolatos információk](../protect/encryption-monitor.md) is szerepeljenek, így egyetlen helyen tekintheti meg az összes eszköz titkosítási részleteit.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>A Windows Autopilot alaphelyzetbe állítása eltávolítja az eszköz elsődleges felhasználóját<!-- 4156123 -->
Ha az Autopilot alaphelyzetbe állítását egy eszközön használja, az eszköz elsődleges felhasználója el lesz távolítva. A következő felhasználó, aki az Alaphelyzetbe állítás után bejelentkezik, elsődleges felhasználóként lesz beállítva. A szolgáltatás a következő néhány nap során minden ügyfelünk számára elérhetővé válik.

## <a name="week-of-july-8-2019"></a>2019. július 8. hét

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Új Office-, Windows-és OneDrive-beállítások a Windows 10 felügyeleti sablonokban <!-- 3510695 -->

Az Intune-ban olyan felügyeleti sablonokat hozhat létre, amelyek a helyszíni csoportházirend-kezelést (**eszközkezelés** >  profilokat > a profil létrehozásához > **Windows 10-es és újabb verziókat** **hozhatnak létre** a platform > **felügyeleti sablon** a profil típusa esetén).

Ez a frissítés több Office-, Windows-és OneDrive-beállítást is tartalmaz, amelyeket hozzáadhat a sablonokhoz. Ezekkel az új beállításokkal mostantól konfigurálhatja a 2500-es, 100%-os beállításokat.

A szolgáltatással kapcsolatos további tudnivalókért tekintse meg a csoportházirend [-beállítások konfigurálása az Intune-ban című témakört a Windows 10-es sablonok használatával](../configuration/administrative-templates-windows.md).

A Windows 10 és újabb verziókra vonatkozik

## <a name="week-of-july-1-2019"></a>2019. július 1. hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>HRE és alkalmazás androidos vállalati eszközökön<!-- 3574267 -->
Teljes körűen felügyelt Android Enterprise-eszközök bevezetésével a felhasználók most már regisztrálva lesznek Azure Active Directory (HRE) az új vagy gyári visszaállítási eszköz kezdeti beállítása során. A teljes körűen felügyelt eszközhöz korábban a telepítés befejeződése után a felhasználónak manuálisan kell elindítania a Microsoft Intune alkalmazást a HRE-regisztráció elindításához. Most, amikor a felhasználó a kezdeti beállítás után az eszköz kezdőlapján landol, az eszköz regisztrálása és regisztrálása is megtörténik.

A HRE-frissítések mellett az Intune app Protection-szabályzatok (alkalmazás) mostantól teljes körűen felügyelt Android Enterprise-eszközökön is támogatottak. Ez a funkció az üzembe helyezés során elérhetővé válik. További információ: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](../apps/apps-add-android-for-work.md)-nal.

## <a name="week-of-june-24-2019-1906-service-release"></a>2019. június 24-i hét (1906 szolgáltatás kiadása)

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Annak konfigurálása, hogy melyik böngésző számára engedélyezett a szervezeti adatkapcsolat<!-- 3145939 -->
Az Android és iOS rendszerű eszközökön elérhető Intune App Protection szabályzatok mostantól lehetővé teszik, hogy az Intune Managed Browser vagy a Microsoft Edge alkalmazáson kívül egy adott böngészőre is átvigye a szervezeti webhivatkozásokat.  További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Minden alkalmazás lap az online/offline Microsoft Store for Business Apps szolgáltatást azonosítja<!--4089647 -->
A **minden alkalmazás** oldalon elérhetők az Microsoft Store for Business (MSFB) alkalmazások online vagy offline alkalmazásként való azonosítására szolgáló címkék is. Minden MSFB-alkalmazás már tartalmaz egy utótagot **online** vagy **offline állapotba**. Az alkalmazás részletei lap a **licenc típusát** is tartalmazza, és **támogatja az eszközök környezetének telepítését** (csak offline licenccel rendelkező alkalmazások) kapcsolatos információk.

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Céges portál alkalmazás a Windows megosztott eszközökön<!--4393553 -->
A felhasználók mostantól hozzáférhetnek a Céges portál alkalmazáshoz a Windows megosztott eszközökön. A végfelhasználók egy **megosztott** címkét fognak látni az eszköz csempén. Ez a Windows Céges portál alkalmazás 10.3.45609.0 és újabb verziójára vonatkozik.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Az összes telepített alkalmazás megtekintése új Céges portál weboldalról<!-- 4224326 -->
A Céges portál webhely új **telepített alkalmazások** lapja felsorolja a felhasználó eszközeire telepített összes felügyelt alkalmazást (mindkettő szükséges és elérhető). A hozzárendelés típusa mellett a felhasználók láthatják az alkalmazás közzétevőjét, a közzététel dátumát és a jelenlegi telepítési állapotot. Ha még nem tette meg a felhasználók számára szükséges vagy elérhető alkalmazásokat, egy üzenet jelenik meg arról, hogy nincs telepítve vállalati alkalmazás. Ha szeretné megtekinteni az új lapot a weben, lépjen a [céges portál webhelyére](https://portal.manage.microsoft.com) , és kattintson a **telepített alkalmazások**elemre.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>Az új nézet lehetővé teszi, hogy az alkalmazások felhasználói lássák az eszközre telepített összes felügyelt alkalmazást.<!-- 2352913 -->  
A Windows Céges portál alkalmazás mostantól felsorolja a felhasználó eszközére telepített összes felügyelt alkalmazást (mindkettő kötelező és elérhető). A felhasználók láthatják a megkísérelt és függőben lévő alkalmazás-telepítéseket, valamint a jelenlegi állapotukat is. Ha még nem tette meg a felhasználók számára a szükséges vagy elérhető alkalmazásokat, megjelenik egy üzenet, amely arról tájékoztatja, hogy nincsenek telepítve a vállalati alkalmazások. Az új nézet megjelenítéséhez nyissa meg a Céges portál navigációs ablaktáblát, és válassza az **alkalmazások** > **telepített alkalmazások**elemet.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Kernel-bővítmények beállításainak konfigurálása macOS-eszközökön<!-- 2043024 -->
MacOS-eszközökön létrehozhat egy eszköz konfigurációs profilt (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > a **MacOS** for platform kiválasztása). Ez a frissítés olyan új beállításokat tartalmaz, amelyek lehetővé teszik a kernel-bővítmények konfigurálását és használatát az eszközökön. Hozzáadhat konkrét bővítményeket, vagy engedélyezheti az összes bővítményt egy adott partnertől vagy fejlesztőtől.

További információ erről a szolgáltatásról: a [kernel-bővítmények áttekintése](../configuration/kernel-extensions-overview-macos.md) és a [kernel-bővítmény beállításai](../configuration/kernel-extensions-settings-macos.md).

A következőkre vonatkozik: macOS 10.13.2 és újabb verziók

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>A csak áruházból származó alkalmazások Windows 10-es eszközökön való beállítása további konfigurációs beállításokat tartalmaz<!-- 2697002 -->
Ha Windows-eszközökhöz hoz létre egy eszköz-korlátozási profilt, a **csak az áruházból származó alkalmazásokat** használhatja, így a felhasználók csak a Windows App Store áruházból telepítik az alkalmazásokat (az**eszköz konfigurációjának** > **profiljai** > profil **létrehozása** > **Windows 10 és újabb verziók** a platform > **eszköz korlátozásai** ). Ebben a frissítésben ez a beállítás ki van bővítve a további beállítások támogatásához.

Az új beállítás megjelenítéséhez nyissa meg a [Windows 10 (és újabb) eszközbeállítások beállításait a szolgáltatások engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-windows-10.md#app-store).

A Windows 10 és újabb verziókra vonatkozik

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Több Zebra Mobility Extensions-eszköz profiljának üzembe helyezése egy eszközön, azonos felhasználói csoporton vagy azonos eszközök csoporton<!-- 4089955 -->
Az Intune-ban az eszköz konfigurációs profiljában a zebra Mobility Extensions (MX) segítségével testre szabhatja az Intune-ba nem beépített Zebra-eszközök beállításait. Jelenleg egyetlen eszközre is telepíthet egyetlen profilt. Ebben a frissítésben több profilt is üzembe helyezhet:
- Ugyanazon felhasználói csoport
- Ugyanazok az eszközök csoport
- Egyetlen eszköz

Az MX használata az Intune-ban című témakörben Microsoft Intune bemutatja, hogyan használhatók a zebra- [eszközök a zebra Mobility Extensions bővítménnyel](../configuration/android-zebra-mx-overview.md) .

A következőkre vonatkozik: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Egyes kioszk-beállítások iOS-eszközökön a "letiltás" értékkel vannak beállítva, az "engedélyezés" kifejezés helyett<!-- 4404075  -->
Ha iOS-eszközökön hoz létre egy eszköz-korlátozási profilt (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** for platform > **eszközök korlátozásai** a profil típusaként > **kioszkban**), beállíthatja az **automatikus zárolást**, a **csengetés kapcsolóját**, a **képernyő elforgatását**, a **képernyő alvó gombját**és a **hangerő gombokat**.

Ebben a frissítésben az értékek **blokkolva** vannak (blokkolja a funkciót), és **nincs konfigurálva** (engedélyezi a funkciót). A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait a funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-ios.md#kiosk).

A következőre vonatkozik: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>A jelszó-hitelesítéshez használja a Face ID-t iOS-eszközökön<!-- 4490704 -->
IOS-eszközökhöz tartozó eszköz-korlátozási profil létrehozásakor ujjlenyomatot használhat a jelszóhoz. Ebben a frissítésben az ujjlenyomat jelszavának beállításai is lehetővé teszik az Arcfelismerés (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** platformon > **eszközre vonatkozó korlátozások** a profil típusa > **Password**). Ennek eredményeképpen a következő beállítások változtak:

- Az **ujjlenyomat feloldása** most érintse meg az **azonosító és a Face ID feloldása**lehetőséget.
- Az **ujjlenyomat módosítása (csak felügyelt** eszköz esetén) most érintse meg az **azonosító és a Face ID módosítását (csak felügyelt**eszköz esetén).

A Face ID az iOS 11,0-es és újabb verzióiban érhető el. A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md#password).

A következőre vonatkozik: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>A játékok és az App Store-szolgáltatások iOS-eszközökön való korlátozása mostantól a minősítési régiótól függ<!-- 4593948 -->
IOS-eszközökön engedélyezheti vagy korlátozhatja a játékokhoz, az App Store-hoz és a dokumentumok megtekintéséhez kapcsolódó funkciókat (az**eszköz konfigurációs** > **profiljait** , > **profilt hozhat létre** > **iOS** platformon > **eszköz-korlátozásokat** a profil típusaként > **App Store, a doc Viewing, a Gaming**). Kiválaszthatja a minősítési régiót is, például a Egyesült Államok.

Ebben a frissítésben az **alkalmazások** szolgáltatás egy gyermek **minősítési régióba**kerül, és a **minősítési régiótól**függ. A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

A következőre vonatkozik: iOS

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows Autopilot-támogatás hibrid Azure AD-csatlakozáshoz<!-- 4809146-->
A meglévő eszközökhöz készült Windows Autopilot mostantól támogatja a hibrid Azure AD-csatlakozást (a meglévő Azure AD-csatlakozás támogatása mellett). A Windows 10 1809-es vagy újabb verziójára vonatkozik. További információ: [a Windows Autopilot a meglévő eszközökhöz](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Eszközkezelés

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Tekintse meg az androidos eszközök biztonsági javítási szintjét<!-- 4461911 -->
Most már megtekintheti az Android-eszközök biztonsági javítási szintjét. Ehhez válassza az **Intune** > **eszközök** > **minden eszköz** lehetőséget, > válasszon egy eszközt > **hardver**.
A javítási szint az **operációs rendszer** szakaszban szerepel.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Hatókör-címkék társítása egy biztonsági csoportban lévő összes felügyelt eszközhöz<!-- 3173810 -->
Mostantól hozzárendelheti a hatókörhöz tartozó címkéket egy biztonsági csoporthoz, és a biztonsági csoportban lévő összes eszköz hozzá lesz rendelve a hatókörhöz tartozó címkékhez is. Az ezekben a csoportokban lévő összes eszköz hozzá lesz rendelve a hatókör címkéhez is. Az ezzel a szolgáltatással beállított hatókör-címkék felülírják az aktuális eszköz hatóköre címkék folyamatával beállított hatóköri címkéket. További információ: [a RBAC és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

### <a name="device-security"></a>Eszköz biztonsága

#### <a name="use-keyword-search-with-security-baselines------"></a>Kulcsszavas keresés használata biztonsági alaptervekkel<!--  -->
A [biztonsági](../protect/security-baselines.md#create-the-profile)alapkonfigurációk létrehozásakor vagy szerkesztésekor megadhat kulcsszavakat az új *keresési* sávban a keresési feltételeket tartalmazó elérhető csoportok szűréséhez.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>A biztonsági alapkonfigurációk szolgáltatás mostantól általánosan elérhető<!-- 3785395 -->
A **biztonsági** alapkonfigurációk szolgáltatás előzetes verzióban érhető el, és mostantól általánosan elérhető (GA).  Ez azt jelenti, hogy a szolgáltatás készen áll az éles környezetben való használatra. Az egyes alapkonfigurációk azonban előzetes verzióban is megmaradhatnak, és a saját ütemezésük alapján kiértékelik és kiadhatják a GA-nak.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>A MDM biztonsági alapkonfiguráció sablonja már általánosan elérhető<!-- 3794072, 4217151,  3534649 -->
A MDM biztonsági alapkonfiguráció sablonja ki lett helyezve az előzetes verzióra, és már általánosan elérhető (GA). A GA-sablon a 2019-as **Mdm biztonsági**alapkonfigurációként van azonosítva.  Ez egy új sablon, és nem az előzetes verzióról való frissítés.  Új sablonként át kell tekintenie a [benne található beállításokat](../protect/security-baseline-settings-mdm.md), majd új profilokat kell létrehoznia a sablon üzembe helyezéséhez az eszközön. Más biztonsági alapkonfigurációk is megmaradhatnak az előzetes verzióban. Az elérhető alapkonfigurációk listáját itt tekintheti meg: [elérhető biztonsági](../protect/security-baselines.md#available-security-baselines)alapkonfigurációk.  

Az új sablon mellett a *május 2019 sablon Mdm biztonsági alapterve* a következő két beállítást tartalmazza, amelyeket nemrégiben jelentettünk be a fejlesztési cikkben:  
- Zárolás fent: az alkalmazások hangvezérelt aktiválása zárolt képernyőről  
- DeviceGuard: a virtualizálás-alapú biztonság (VBS) használata az eszközök következő újraindításakor.  

A *május 2019-es Mdm biztonsági* alapkonfiguráció több új beállítás hozzáadását is magában foglalja, mások eltávolítását, valamint egy beállítás alapértelmezett értékének egy változatát. Az előzetes verzióról a GA-re való változások részletes listáját az **új sablon**változásai című részben tekintheti meg.

#### <a name="security-baseline-versioning---3194322---"></a>Biztonsági alapterv verziószámozása<!-- 3194322 -->
Az Intune biztonsági alapkonfigurációi támogatják a verziószámozást. Ha ezzel a támogatással az egyes biztonsági alapkonfigurációk új verziói jelennek meg, akkor a meglévő biztonsági alapkonfigurációkat úgy frissítheti, hogy az új alapterv újbóli létrehozása és üzembe helyezése nélkül is felhasználható legyen. Emellett az Intune-konzolon megtekintheti az egyes alapbeállításokkal kapcsolatos információkat, például az alapkonfigurációt használó egyedi profilok számát, a profilok által használt különböző alapkonfigurációkat, valamint az adott biztonság legújabb kiadását. az alapterv volt.  További információ: **biztonsági alaptervek**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>A bejelentkezési beállításhoz tartozó biztonsági kulcsok használata áthelyezve<!-- 4501151 -->
A **bejelentkezéshez használt** "Identity Protection" nevű eszköz konfigurációs beállítása már nem található a *Windows Hello for Business konfigurálásának*albeállításaként. Ez most egy legfelső szintű beállítás, amely mindig elérhető, még akkor is, ha nem engedélyezi a vállalati Windows Hello használatát. További információ: [Identity Protection](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Új engedélyek a hozzárendelt csoport rendszergazdái számára<!-- 4504437   -->
Az Intune beépített iskolai rendszergazdai szerepköre mostantól rendelkezik a felügyelt alkalmazások létrehozására, olvasására, frissítésére és törlésére (szifilisz) vonatkozó engedélyekkel. Ez a frissítés azt jelenti, hogy ha Intune for Education-beli csoport-rendszergazdaként van társítva, mostantól létrehozhatja, megtekintheti, frissítheti és törölheti az iOS-MDM Push-tanúsítvány, az iOS MDM-kiszolgálói tokeneket, valamint az iOS VPP-tokeneket az [összes meglévő engedélyével](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)együtt. A fenti műveletek elvégzéséhez nyissa meg a **bérlői beállítások** > **iOS-eszközök felügyeletét**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Az alkalmazások a Graph API használatával felhasználói hitelesítő adatok nélkül hívhatják meg az olvasási műveleteket<!-- 4655885 -->
Az alkalmazások felhasználói hitelesítő adatok nélkül hívhatják meg az Intune-Graph API olvasási műveleteit az alkalmazás identitásával. További információ az Intune-hoz készült Microsoft Graph API eléréséről: az [Intune használata a Microsoft Graphban](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Hatókör-címkék alkalmazása Microsoft Store vállalati alkalmazásokhoz<!-- 4392555 -->
Mostantól alkalmazhat hatókör-címkéket Microsoft Store vállalati alkalmazásokhoz. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

## <a name="week-of-june-17-2019"></a>2019. június 17-i hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune alkalmazás új funkciói
Új funkciókkal bővült az Androidhoz készült Microsoft Intune alkalmazás (előzetes verzió). A teljes körűen felügyelt Android-eszközök felhasználói mostantól a következőket tehetik:  

* Megtekintheti és kezelheti az Intune Céges portál vagy Microsoft Intune alkalmazással regisztrált eszközöket.
* Segítségért forduljon a szervezethez.
* Küldjön visszajelzést a Microsoftnak.
* Megtekintheti a feltételeket és kikötéseket, ha azokat a szervezete állítja be.

## <a name="week-of-june-10-2019"></a>2019. június 10-i hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>A GitHubon elérhető Intune SDK-integrációt bemutató új minta alkalmazások<!-- 2653471 -->
A msintuneappsdk GitHub-fiók új, az iOS (Swift), az Android, a Xamarin. iOS, a Xamarin Forms és a Xamarin. Android alkalmazásokhoz készült példákkal bővült. Ezeknek az alkalmazásoknak a célja, hogy kiegészítsék meglévő dokumentációját, és bemutatjuk, hogyan integrálhatja az Intune APP SDK-t a saját Mobile Apps szolgáltatásba. Ha olyan alkalmazás fejlesztője van, amelynek további Intune SDK-útmutatásra van szüksége, tekintse meg a következő csatolt mintákat:
- [Csevegés](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) – natív iOS (Swift) azonnali üzenetküldési alkalmazás, amely a Azure Active Directory Authentication Library (ADAL) protokollt használja a felügyelt hitelesítéshez.
- [TASKER](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) – a ADAL-t a felügyelt hitelesítéshez használó natív androidos Todo-lista alkalmazás.
- [TASKER](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) – Xamarin. Android Todo-lista alkalmazás, amely ADAL használ a felügyelt hitelesítéshez, ez a tárház a Xamarin. Forms alkalmazást is tartalmazza.
- [Xamarin. iOS minta alkalmazás](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – A barebones Xamarin. iOS minta alkalmazás.

## <a name="week-of-may-27-2019"></a>Május 27., 2019. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Az Android-eszközökön feltehetően ártalmas alkalmazások jelentése<!-- 4223162 -->
Az Intune mostantól további jelentéskészítési információkat biztosít az Android-eszközökön található potenciálisan ártalmas alkalmazásokról. 

## <a name="week-of-may-20-2019"></a>2019. május 20. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="windows-company-portal-app---3316993---"></a>Windowsos Munkahelyi portál alkalmazás<!-- 3316993 -->
A Windows Céges portál alkalmazás mostantól egy új lap címkével ellátott **eszközeit**fogja tartalmazni. Az **eszközök** lap megjeleníti a végfelhasználók összes regisztrált eszközét. Ha a 10.3.4291.0 vagy újabb verziót használja, a felhasználók ezt a változást fogják látni a Céges portálban. További információ a Céges portál konfigurálásáról: [Microsoft Intune céges portál alkalmazás konfigurálása](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Az Autopilot-eszköz Rendeléskód attribútumának neve a csoport címkére módosult <!-- 4659453 -->

Ahhoz, hogy intuitívabb legyen, a **Rendeléskód** -attribútum neve az Autopilot-eszközökön **csoport címkére**módosult. Ha a CSV-t használja az Autopilot-eszköz adatainak feltöltésére, akkor a Group címkét oszlop fejlécként kell használni, a Rendeléskód nem.  

## <a name="week-of-may-13-2019-1905-service-release"></a>Május 13-i hét, 2019 (1905 szolgáltatás kiadása)

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Az Intune-szabályzatok frissítik a hitelesítési módszert és Céges portál alkalmazás telepítését<!-- 1927359  -->
A beállítási Asszisztensen keresztül már regisztrált eszközökön az Apple vállalati eszközök egyik regisztrációs módszerén keresztül az Intune többé nem fogja támogatni a Céges portál, ha az App Store-ból végfelhasználók manuálisan telepítik. Ez a módosítás csak akkor érvényes, ha a regisztráció során az Apple beállítási asszisztenssel végzi a hitelesítést. Ez a módosítás csak az alábbi módon beléptetett iOS-eszközökre vonatkozik:  
* Apple konfigurátor

* Apple Business Manager

* Apple School Manager

* Apple Készülékregisztrációs program (DEP)

Ha a felhasználók telepítik a Céges portál alkalmazást az App Store áruházból, majd megpróbálják regisztrálni ezeket az eszközöket, hibaüzenetet kapnak. Ezeket az eszközöket a rendszer csak akkor fogja használni, ha a regisztráció során az Intune automatikusan leküldte a Céges portál. Az Intune-ban lévő beléptetési profilok a Azure Portal frissülni fognak, így megadhatja, hogyan történjen az eszközök hitelesítése, és ha megkapják a Céges portál alkalmazást. Ha azt szeretné, hogy a DEP-eszköz felhasználói rendelkezzenek a Céges portál, meg kell adnia a beállításait egy beléptetési profilban. 

Emellett az iOS-Céges portálban az **eszköz azonosítása** képernyő is törlődik. Ezért a rendszergazdáknak, akik engedélyezni szeretnék a feltételes hozzáférést, vagy vállalati alkalmazásokat kell telepíteniük, frissíteniük kell a DEP regisztrációs profilt. Ez a követelmény csak akkor érvényes, ha a DEP-regisztráció a beállítási asszisztenssel van hitelesítve. Ebben az esetben a Céges portált az eszközre kell leküldeni. Ehhez válassza az **Intune** > **eszközök beléptetése** > az **Apple-regisztráció** > a **beléptetési program jogkivonatok** lehetőséget > Válassza ki a tokent > **profilok** > válasszon egy profilt > **Tulajdonságok** > a **telepítési céges portál** beállítása **Igen**értékre.

Ha a Céges portál a már regisztrált DEP-eszközökön szeretné telepíteni, akkor az Intune-ban > ügyfélalkalmazások elemre kell kattintania, és felügyelt alkalmazásként kell leküldeni az alkalmazás-konfigurációs házirendekkel. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Annak konfigurálása, hogy a végfelhasználók hogyan frissíthetnek egy üzletági (LOB) alkalmazást egy alkalmazás-védelmi házirend használatával<!-- 3568384 -->
Most már beállíthatja, hogy a végfelhasználók hol szerezhetik be az üzletági (LOB) alkalmazások frissített verzióját. A végfelhasználók láthatják ezt a szolgáltatást a **minimális app Version** feltételes indítási párbeszédpanelen, amely arra kéri a végfelhasználókat, hogy frissítsen az üzletági alkalmazás minimális verziójára. Ezeket a frissítés részleteit a LOB-alkalmazás védelmi házirendjének (alkalmazás) részeként kell megadnia. Ez a funkció iOS és Android rendszereken érhető el. IOS rendszeren ez a funkció megköveteli, hogy az alkalmazás integrálva legyen (vagy becsomagolva a burkoló eszköz használatával) az iOS-hez készült Intune SDK-val. 10.0.7 vagy újabb. Androidon a szolgáltatáshoz a legújabb Céges portál szükséges. Annak konfigurálásához, hogy a végfelhasználó hogyan frissítsen egy LOB-alkalmazást, az alkalmazásnak szüksége van egy felügyelt alkalmazás konfigurációs szabályzatára, amelyet a kulcsával `com.microsoft.intune.myappstore`. Az elküldés érték határozza meg, hogy a végfelhasználó melyik tárolóban tölti le az alkalmazást. Ha az alkalmazás a Céges portálon keresztül lett telepítve, az értéknek `CompanyPortal`nak kell lennie. Bármely más áruház esetében teljes URL-címet kell megadnia.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune felügyeleti bővítmény PowerShell-parancsfájlok<!-- 3734186  -->
Konfigurálhatja a PowerShell-parancsfájlokat úgy, hogy az eszközön a felhasználó rendszergazdai jogosultságával fussanak. További információ: PowerShell- [parancsfájlok használata a Windows 10-es eszközökön az Intune-ban](../apps/intune-management-extension.md) és a [win32 app managementben](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Androidos vállalati alkalmazások kezelése<!-- 4459905 -->
Annak érdekében, hogy a rendszergazdák könnyebben konfigurálják és használják az Android Enterprise managementet, az Intune automatikusan négy általános androidos vállalati alkalmazást ad hozzá az Intune felügyeleti konzolhoz. A négy androidos vállalati alkalmazás a következő alkalmazások:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – az Android Enterprise teljes körűen felügyelt forgatókönyvekhez használható.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – segít bejelentkezni a fiókjába, ha kétfaktoros ellenőrzést használ.
- **[Intune céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – az alkalmazás-és az Android Enterprise Work-profil forgatókönyvek esetében használatos.
- [Felügyelt kezdőképernyő](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – az Android Enterprise dedikált/kioszk forgatókönyvek esetében használható.

Korábban a rendszergazdáknak manuálisan kell megkeresniük és jóváhagynia ezeket az alkalmazásokat a [felügyelt Google Play áruházban](https://play.google.com/store/apps) a telepítés részeként. Ez a módosítás eltávolítja ezeket a korábban kézi lépéseket, így egyszerűbbé és gyorsabbá teszi az ügyfelek számára az Android Enterprise Management használatát.

A rendszergazdák láthatják, hogy ezek a négy alkalmazás automatikusan hozzá lesz adva az Intune-alkalmazások listájához, amikor először csatlakoznak az Intune-bérlőhöz a felügyelt Google Play szolgáltatáshoz. További információ: [az Intune-fiók összekötése a felügyelt Google Play-fiókkal](../enrollment/connect-intune-android-enterprise.md). Azok a bérlők, akik már csatlakoztak a bérlőhöz, vagy akik már használják az Android Enterprise-t, nincs szükség a rendszergazdákra. A következő négy alkalmazás automatikusan megjelenik a május 2019 szolgáltatás bevezetésének befejezését követő 7 napon belül.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>A PFX tanúsítvány-összekötő frissítése a Microsoft Intune<!-- 1533038 -->
Kiadott egy frissítést a [pfx tanúsítvány-összekötőhöz Microsoft Intune számára](../protect/certficates-pfx-configure.md#whats-new-for-connectors) , amely egy olyan hibával foglalkozik, amelyben a meglévő pfx-tanúsítványok továbbra is újrafeldolgozásra kerülnek, ami miatt az összekötő leállítja az új kérések feldolgozását.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Intune-beli biztonsági feladatok a Defender ATP-ben (nyilvános előzetes verzió)<!-- 3208597 -->
A nyilvános előzetes verzióban az Intune használatával kezelheti a [Microsoft Defender komplex veszélyforrások elleni védelem (ATP) biztonsági feladatait](../protect/atp-manage-vulnerabilities.md). Ez az ATP-integráció és a kockázati alapú megközelítés a végponti biztonsági rések és helytelen konfigurációk felderítéséhez, rangsorolásához és javításához, valamint a felderítés és a hibák enyhítése közötti idő csökkentéséhez.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>TPM-chipkészlet keresése Windows 10-es eszköz megfelelőségi szabályzatában<!-- 3617671   idstaged-->
Számos Windows 10 és újabb rendszerű eszköz rendelkezik platformmegbízhatósági modul (TPM) chipsettel. Ez a frissítés egy új megfelelőségi beállítást tartalmaz, amely ellenőrzi a TPM-lapka verzióját az eszközön.

A [Windows 10-es és újabb megfelelőségi szabályzatok beállításai](../protect/compliance-policy-create-windows.md#device-security) ezt a beállítást ismertetik.

A Windows 10 és újabb verziókra vonatkozik

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Annak megakadályozása, hogy a végfelhasználók módosíthassák a személyes hozzáférési pontokat, és tiltsa le a Siri Server naplózását iOS-eszközökön<!-- 4097904   -->  
Az iOS-eszközön létre kell hoznia egy eszköz-korlátozási profilt (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS** platformon > **eszközre vonatkozó korlátozások** a profil típusa esetén). Ez a frissítés olyan új beállításokat is tartalmaz, amelyeket konfigurálhat:

- **Beépített alkalmazások**: kiszolgálóoldali naplózás a Siri-parancsokhoz
- **Vezeték nélküli**: a személyes hozzáférési pont felhasználói módosítása (csak felügyelt eszköz esetén)

Ezeknek a beállításoknak a megtekintéséhez nyissa meg az iOS és a [vezeték nélküli beállítások](../configuration/device-restrictions-ios.md#wireless)iOS-hez című [beépített alkalmazás beállításait](../configuration/device-restrictions-ios.md#built-in-apps) .

A következőkre vonatkozik: iOS 12,2 és újabb

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Új osztályterem alkalmazás-eszköz korlátozási beállításai macOS-eszközökhöz<!-- 4097905   --> 
A macOS-eszközökhöz létrehozhat eszköz-konfigurációs profilokat (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **MacOS** platformon > **eszközre vonatkozó korlátozások** a profil típusa esetén). Ez a frissítés magában foglalja az új osztályterem alkalmazás beállításait, a képernyőképek blokkolásának lehetőségét, valamint az iCloud Photo Library letiltásának lehetőségét.

Ha szeretné megtekinteni az aktuális beállításokat, lépjen a [MacOS eszközbeállítások lehetőségre, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-macos.md).

A következőkre vonatkozik: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Az App Store-beállítások eléréséhez használt iOS-jelszó átnevezve<!-- 4557891  -->
Az **App Store-hoz való hozzáféréshez szükséges jelszót** a rendszer átnevezi, hogy **megkövetelje az iTunes Store-beli jelszót az összes vásárláshoz** (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **iOS** platformon > **eszköz-korlátozások** a profil típusa > **App Store, a doc Viewing és a Gaming**).

Az elérhető beállítások megjelenítéséhez nyissa meg az [App Store, a doc Viewing, a Gaming iOS beállításait](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

A következőre vonatkozik: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender komplex veszélyforrások elleni védelem alapterve (előzetes verzió)<!--  3754134 -->
Bővítettük a [Microsoft Defender komplex veszélyforrások elleni védelemhez](../protect/security-baseline-settings-defender-atp.md) tartozó biztonsági alapkonfiguráció előzetes verzióját. Ez az alapterv akkor érhető el, ha a környezet megfelel a [Microsoft Defender komplex veszélyforrások elleni védelem](../protect/advanced-threat-protection.md#prerequisites)használatának előfeltételeinek.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>A Windows-regisztráció állapota lap (ESP) már általánosan elérhető<!-- 3605348 -->
A regisztráció állapota lap már nem előzetes verzió. További információ: [regisztráció állapotának beállítása lap](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune felhasználói felület frissítése – Autopilot beléptetési profil létrehozása<!-- 4593669 -->
Az Autopilot-beléptetési profil létrehozásához szükséges felhasználói felület frissítve lett az Azure felhasználói felületi stílusokkal való összehangolás érdekében. További információt az Autopilot- [beléptetési profil létrehozása](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)című témakörben talál. A továbbítást követően további Intune-forgatókönyvek is frissülnek az új felhasználói felületi stílusba.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Az Autopilot alaphelyzetbe állításának engedélyezése az összes Windows-eszközön<!-- 4225665 -->
Az Autopilot alaphelyzetbe állítása mostantól minden Windows-eszközön működik, még azok is, amelyek nincsenek konfigurálva a regisztrációs állapot lap használatára. Ha a regisztráció állapotát jelző lap nem lett konfigurálva az eszközre a kezdeti eszközök beléptetése során, az eszköz a bejelentkezés után egyenesen az asztalra kerül. Akár nyolc órát is igénybe vehet, és az Intune-ban megfelelőnek tűnik. További információ: [eszközök alaphelyzetbe állítása a távoli Windows Autopilot alaphelyzetbe állításával](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Az összes eszköz keresésekor nem szükséges pontos IMEI-formátum<!--30407680 -->
A **minden eszköz**keresésekor nem szükséges szóközöket bevenni az IMEI-számba.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Az eszközök az Apple Portalon való törlése az Intune-portálon jelenik meg<!--2489996 -->
Ha egy eszközt törölnek az Apple Készülékregisztrációs program vagy az Apple Business Manager portálról, az eszköz automatikusan törlődik az Intune-ból a következő szinkronizálás során.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>A regisztráció állapota lap most nyomon követi a Win32-alkalmazásokat<!-- 2714451 -->
Ez csak a Windows 10 1903-es vagy újabb verzióját futtató eszközökre vonatkozik. További információ: [regisztráció állapotának beállítása lap](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Eszközkezelés

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Eszközök tömeges visszaállítása és törlése a Graph API használatával<!-- 3295288 -->
Most visszaállíthatja és törölheti a több mint 100 eszközt a Graph API használatával.

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>A titkosítási jelentés kívül esik a nyilvános előzetes verzióban<!-- 4587546      -->
A [BitLocker és az eszközök titkosítására vonatkozó jelentés](../protect/encryption-monitor.md) már általánosan elérhető, és már nem része a nyilvános előzetes verziónak.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Az Outlook-aláírás és a biometrikus beállítások iOS és Android rendszerű eszközökhöz<!-- 4050557 -->
Mostantól megadhatja, hogy az alapértelmezett aláírás engedélyezve van-e az Outlookban iOS-és Android-eszközökön. Emellett dönthet úgy is, hogy lehetővé teszi a felhasználók számára, hogy megváltoztassák a biometrikus beállításokat az Outlookban az iOS-ben.

## <a name="week-of-may-6-2019"></a>Május 6-i hét, 2019

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Hálózati Access Control (NAC) támogatása az iOS-eszközökre vonatkozó F5-hozzáféréshez<!-- 4500808 -->

F5 kiadott egy frissítést a BIG-IP 13-hez, amely lehetővé teszi, hogy a nagyvállalati funkciók F5-ös verzióhoz hozzáférjenek az Intune-ban A szolgáltatás használata:

- A BIG-IP frissítése a 13.1.1.5 frissítéséhez. A BIG-IP 14 nem támogatott.
- A BIG-IP integrálása az Intune-nal a NAC-hoz. Az [Áttekintés lépései: az APM konfigurálása eszköz-testtartási ellenőrzésekhez végpont-felügyeleti rendszerekkel](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Jelölje be a **hálózati Access Control (NAC) engedélyezése** beállítást a VPN-profilban az Intune-ban.

Az elérhető beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS-eszközökön](../configuration/vpn-settings-ios.md)című témakört.

A következőre vonatkozik: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>A PFX tanúsítvány-összekötő frissítése a Microsoft Intune<!-- doc-vso 1521237  -->  
Kiadott egy frissítést a [pfx tanúsítvány-összekötőhöz a Microsoft Intune számára](../protect/certficates-pfx-configure.md#whats-new-for-connectors) , amely 5 perctől 30 másodpercre lecsökken a lekérdezési időköz.




## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
