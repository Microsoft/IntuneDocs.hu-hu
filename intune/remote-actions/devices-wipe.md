---
title: Eszközök kivonása vagy összes adatuk törlése a Microsoft Intune használatával – Azure | Microsoft Docs
description: A Windows Intune-nal kivonhat Android rendszerű, androidos munkahelyi profilt használó, iOS, macOS vagy Windows rendszerű eszközöket, vagy törölheti azok összes adatát. Törölheti is az eszközt az Azure Active Directoryból.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc50d275a3d3e6a613640e96b363ce7608da81
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508566"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Eszközök eltávolítása összes adatuk törlésével, az eszköz kivonásával vagy regisztrációja manuális törlésével

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A **Kivonás** vagy az **Összes adat törlése** művelettel eltávolíthatja az eszközt az Intune-ból, ha az eszközre már nincs szükség, azt egy megváltozott célra használják, vagy ha elveszett. A felhasználók egy távoli parancsot is kiadhatnak a Intune Céges portál az Intune-ban regisztrált eszközökre.

> [!NOTE]
> Mielőtt eltávolítana egy felhasználót az Azure Active Directoryból (Azure AD), adjon ki egy **Kivonás** vagy egy **Összes adat törlése** parancsot az adott felhasználóhoz rendelt összes eszközre. Ha felügyelt eszközzel rendelkező felhasználókat távolít el az Azure AD-ból, akkor az Intune már nem fogja tudni törölni ezeknek az eszközöknek az összes adatát, vagy kivonni az eszközöket.

## <a name="wipe"></a>Törlés

Az **Összes adat törlése** művelet visszaállítja az eszközön az alapértelmezett gyári beállításokat. A felhasználói adatok attól függően maradnak meg, hogy bejelölte-e a **Regisztrációs állapot és felhasználói fiók megtartása** jelölőnégyzetet. Ellenkező esetben a rendszer eltávolítja az összes adatértéket, alkalmazást és beállítást.

|Az Összes adat törlése művelet|**Regisztrációs állapot és felhasználói fiók megtartása**|Eltávolítva az Intune kezelése alól|Description|
|:-------------:|:------------:|:------------:|------------|
|**Törlés**| Nincs bejelölve | Igen | Törli az összes felhasználói fiókot, adatot, MDM-szabályzatot és beállítást. Visszaállítja az operációs rendszert az alapértelmezett állapotra és beállításokra.|
|**Törlés**| Bejelölve | Nem | Törli az összes MDM-szabályzatot. Megtartja a felhasználói fiókokat és az adatokat. Visszaállítja a felhasználói beállításokat az alapértelmezett értékre. Visszaállítja az operációs rendszert az alapértelmezett állapotra és beállításokra.|


> [!NOTE]
> A törlési művelet nem érhető el a felhasználó beléptetésével regisztrált iOS-eszközökön.

A **Regisztrációs állapot és felhasználói fiók megtartása** lehetőség csak a Windows 10 1709-es vagy újabb verziók esetében érhető el.

A rendszer újra alkalmazza az MDM-szabályzatokat az eszköz következő Intune-csatlakozásakor.

Az összes adat törlését akkor érdemes használni, ha szeretne alaphelyzetbe állítani egy adott eszközt, mielőtt új felhasználónak adná, illetve abban az esetben, ha az eszközt elveszítették vagy ellopták. Az **Összes adat törlése** műveletet körültekintően használja. Az eszközön tárolt adatok a művelet után nem állíthatók vissza.

### <a name="wiping-a-device"></a>Eszköz összes adatának törlése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.
4. Válassza ki az eszköz nevét, amelyen az összes adatot törölni szeretné.
5. Az eszköz nevét megjelenítő panelen válassza az **Összes adat törlése** lehetőséget.
6. A Windows 10 1709-es vagy újabb verziója esetén rendelkezésre áll a **Regisztrációs állapot és felhasználói fiók megtartása** lehetőség is. 
    
    |Meg lesz őrizve az összes adat törlése során |Nem őrződik meg|
    | -------------|------------|
    |Az eszközhöz társított felhasználói fiókok|Felhasználói fájlok|
    |A gép állapota \(tartományhoz való csatlakozás, Azure AD-csatlakoztatás)| A felhasználók által telepített alkalmazások \(áruházbeli és Win32-alkalmazások)|
    |Mobileszköz-felügyeleti (MDM-) regisztráció|Nem alapértelmezett eszközbeállítások|
    |Az eredeti berendezésgyártók által telepített alkalmazások \(áruházbeli és Win32-alkalmazások)||
    |Felhasználói profil||
    |A felhasználói profilon kívüli felhasználói adatok||
    |Felhasználói automatikus bejelentkezés|| 
    
         
7. Az összes adat törlésének megerősítéséhez válassza az **Igen** lehetőséget.

Ha az eszköz be van kapcsolva és csatlakoztatva van, az **Összes adat törlése** műveletnek az összes eszköztípusra való propagálása kevesebb mint 15 percet vesz igénybe.

## <a name="retire"></a>Kivonás

A **Kivonás** művelet eltávolítja a felügyelt alkalmazásadatokat (ha vannak ilyenek), a beállításokat és az eszközhöz az Intune használatával hozzárendelt e-mail-profilokat. Az eszközt a rendszer eltávolítja az Intune-ból. Ez akkor történik meg, amikor az eszköz legközelebb bejelentkezik és megkapja a távoli **Kivonás** műveletet. Az eszköz addig is megjelenik az Intune-ban, amíg az eszköz be nem jelentkezik. Ha azonnal el szeretné távolítani az elavult eszközöket, használja helyette a [delete műveletet](devices-wipe.md#delete-devices-from-the-intune-portal) .

A **Kivonás** meghagyja az eszközön a felhasználó személyes adatait.  

Az alábbi táblázatok ismertetik, hogy milyen adatokat távolít el a rendszer, és hogy az eszközön maradó adatokra milyen hatással van a **Kivonás** művelet a céges adatok eltávolítása után.

### <a name="ios"></a>iOS

|Adattípus|iOS|
|-------------|-------|
|Vállalati alkalmazások és az Intune által telepített egyéb vonatkozó adatok|**Céges portál használatával telepített alkalmazások:** A felügyeleti profilba rögzített alkalmazások esetében az összes alkalmazásadatok és az alkalmazások el lesznek távolítva. Ezek az alkalmazások tartalmazzák az App Store-ból eredetileg telepített alkalmazásokat és a később vállalati alkalmazásokként kezelt alkalmazásokat. <br /><br /> **A Mobile App Management szolgáltatást használó Microsoft-alkalmazások és az App Store áruházból lettek telepítve:** A Céges portál által nem felügyelt alkalmazások esetén a rendszer eltávolítja az alkalmazás helyi tárolójában lévő, a Mobile Application Management (MAM) titkosítással védett vállalati alkalmazásadatok szolgáltatásait. Az alkalmazáson kívüli MAM-titkosítás által védett adatforgalom titkosítva és használhatatlan marad, de nem törlődik. A személyes alkalmazásadatok és az alkalmazások nem törlődnek.|
|Beállítások|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|
|Wi-Fi és VPN profilbeállításai|Eltávolítva.|
|Tanúsítvány profilbeállításai|A tanúsítványok törlődnek és visszavonásra kerülnek.|
|Kezelőügynök|Törlődik a felügyeleti profil.|
|E-mail|Törlődnek az Intune-on keresztül telepített e-mail-profilok. Törlődnek az eszközön gyorsítótárazott e-mailek.|
|Az Azure AD elhagyása|Törlődik az Azure AD rekord.|

### <a name="android"></a>Android:

|Adattípus|Android:|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Webhivatkozások|Eltávolítva.|Eltávolítva.|
|Nem felügyelt Google Play-alkalmazások|A telepített alkalmazások és azok adatai megmaradnak. <br /> <br />A rendszer eltávolítja az alkalmazás helyi tárolójában lévő, a Mobile Application Management (MAM) titkosítással védett vállalati alkalmazás-beállításokat. Az alkalmazáson kívüli MAM-titkosítás által védett adatforgalom titkosítva és használhatatlan marad, de nem törlődik. |A telepített alkalmazások és azok adatai megmaradnak. <br /> <br />A rendszer eltávolítja az alkalmazás helyi tárolójában lévő, a Mobile Application Management (MAM) titkosítással védett vállalati alkalmazás-beállításokat. Az alkalmazáson kívüli MAM-titkosítás által védett adatforgalom titkosítva és használhatatlan marad, de nem törlődik.|
|Nem felügyelt üzletági alkalmazások|A telepített alkalmazások és azok adatai megmaradnak.|Az alkalmazások el lesznek távolítva, és az alkalmazás helyi adatai is törlődnek. Az alkalmazáson kívüli adatok (például amelyek az SD-kártyán vannak) nem fognak törlődni.|
|Felügyelt Google Play-alkalmazások|Az alkalmazásadatok törlődnek. Az alkalmazások nem törlődnek. Az alkalmazáson kívüli (például az SD-kártyán lévő), Mobile Application Management- (MAM)-titkosítás által védett adatok titkosítva és használhatatlan állapotban maradnak, de a rendszer nem távolítja el azokat.|Az alkalmazásadatok törlődnek. Az alkalmazások nem törlődnek. Az alkalmazáson kívül (például az SD-kártyán lévő), MAM-titkosítás által védett adatok titkosítva maradnak, de a rendszer nem távolítja el azokat.|
|Felügyelt üzletági alkalmazások|Az alkalmazásadatok törlődnek. Az alkalmazások nem törlődnek. Az alkalmazáson kívül (például az SD-kártyán lévő), MAM-titkosítás által védett adatok titkosítva maradnak, és használhatatlanok lesznek, de a rendszer nem távolítja el azokat.|Az alkalmazásadatok törlődnek. Az alkalmazások nem törlődnek. Az alkalmazáson kívül (például az SD-kártyán lévő), MAM-titkosítás által védett adatok titkosítva maradnak, és használhatatlanok lesznek, de a rendszer nem távolítja el azokat.|
|Beállítások|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|
|Wi-Fi és VPN profilbeállításai|Eltávolítva.|Eltávolítva.|
|Tanúsítvány profilbeállításai|A tanúsítványok visszavonódnak, de nem törlődnek.|A tanúsítványok törlődnek és visszavonásra kerülnek.|
|Kezelőügynök|Visszavonódik az eszköz-rendszergazdai jogosultság.|Visszavonódik az eszköz-rendszergazdai jogosultság.|
|E-mail|Nem alkalmazható (az androidos eszközök nem támogatják az e-mail-profilokat)|Törlődnek az Intune-on keresztül telepített e-mail-profilok. Törlődnek az eszközön gyorsítótárazott e-mailek.|
|Az Azure AD elhagyása|Törlődik az Azure AD rekord.|Törlődik az Azure AD rekord.|

### <a name="android-work-profile"></a>Androidos munkahelyi profil

Az androidos munkahelyi profillal rendelkező eszközökről a céges adatok eltávolítása a munkahelyi profilban lévő összes adatot, alkalmazást és beállítást eltávolítja. Az eszköz kikerült az Intune felügyeletéből. Az androidos munkahelyi profilok esetében a kivonás nem támogatott.

### <a name="android-enterprise-kiosk-devices"></a>Vállalati androidos kioszkeszközök

Az összes adat törlése csak kioszkeszközökön lehetséges. Androidos kioszkeszközöket nem lehet kivonni.


### <a name="macos"></a>macOS

|Adattípus|macOS|
|-------------|-------|
|Beállítások|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|
|Wi-Fi és VPN profilbeállításai|Eltávolítva.|
|Tanúsítvány profilbeállításai|A rendszer az MDM-mel telepített tanúsítványokat eltávolítja és visszavonja.|
|Kezelőügynök|Törlődik a felügyeleti profil.|
|Outlook|Ha a feltételes hozzáférés engedélyezve van, az eszköz nem kap új e-mailt.|
|Az Azure AD elhagyása|Törlődik az Azure AD rekord.|

### <a name="windows"></a>Windows

|Adattípus|Windows 8.1 (MDM) és Windows RT 8.1|Windows RT|Windows Phone 8.1 és Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Vállalati alkalmazások és az Intune által telepített egyéb vonatkozó adatok|Az EFS által védett fájloknál a kulcsok visszavonódnak. A felhasználó nem tudja megnyitni a fájlokat.|A vállalati alkalmazásokat a rendszer nem távolítja el.|Törlődnek az eredetileg a Céges portálon keresztül telepített alkalmazások. Törlődnek a vállalati alkalmazásadatok.|Törlődnek az alkalmazások. A közvetlen telepítési kulcsokat a rendszer eltávolítja.<br>A Windows 10 1703-as (alkotói frissítés) és újabb verzióinál a rendszer az Office 365 ProPlus alkalmazásokat nem távolítja el. Az Intune felügyeleti bővítmény telepített Win32-alkalmazásai nem lesznek eltávolítva a nem regisztrált eszközökön. A rendszergazdák kihasználhatják a hozzárendelések kizárását, hogy a Win32-alkalmazások ne BYOD eszközöket.|
|Beállítások|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|Az Intune-szabályzat által konfigurált beállítások érvényüket vesztik. A felhasználók megváltoztathatják a beállításokat.|
|Wi-Fi és VPN profilbeállításai|Eltávolítva.|Eltávolítva.|Not supported.|Eltávolítva.|
|Tanúsítvány profilbeállításai|A tanúsítványok törlődnek és visszavonásra kerülnek.|A tanúsítványok törlődnek és visszavonásra kerülnek.|Not supported.|A tanúsítványok törlődnek és visszavonásra kerülnek.|
|E-mail|Eltávolítja az EFS-kompatibilis e-maileket. Ez magában foglalja a Windows Posta alkalmazásában található e-maileket és mellékleteket.|Not supported.|Törlődnek az Intune-on keresztül telepített e-mail-profilok. Törlődnek az eszközön gyorsítótárazott e-mailek.|Eltávolítja az EFS-kompatibilis e-maileket. Ez magában foglalja a Windows Posta alkalmazásában található e-maileket és mellékleteket. A rendszer eltávolítja az Intune által telepített e-mail-fiókokat.|
|Az Azure AD elhagyása|Nem.|Nem.|Törlődik az Azure AD rekord.|Törlődik az Azure AD rekord.|

> [!NOTE]
> Az Azure AD-hez a kezdeti beállítás (OOBE) során csatlakozó Windows 10-es eszközök esetén a kivonás parancs eltávolítja az összes Azure AD-fiókot az eszközről. Kövesse a [számítógép csökkentett módban való beindításának](https://support.microsoft.com/en-us/help/12376/windows-10-start-your-pc-in-safe-mode) lépéseit helyi rendszergazdaként való bejelentkezéshez és a felhasználó helyi adataihoz való hozzáférés visszaszerzéséhez. 

### <a name="retire"></a>Kivonás

1. Jelentkezzen be az [Intune-ba az Azure Portalon](https://aka.ms/intuneportal).
2. Az **Eszközök** panelen válassza a **Minden eszköz** lehetőséget.
3. Válassza ki a kivonni kívánt eszköz nevét.
4. Az eszköz nevét megjelenítő panelen válassza a **Kivonás** lehetőséget. Válassza az **Igen** lehetőséget a megerősítéshez.

Ha az eszköz be van kapcsolva és csatlakoztatva van, a **Kivonás** műveletnek az összes eszköztípusra való propagálása kevesebb mint 15 percet vesz igénybe.

## <a name="delete-devices-from-the-intune-portal"></a>Eszközök törlése az Intune-portálról

Ha el szeretne távolítani eszközöket az Intune-portálról, ezt megteheti az adott eszközpanelen. Az eszköz következő bejelentkezésekor minden céges adat el lesz távolítva.

1. Jelentkezzen be az [Intune-ba az Azure Portalon](https://aka.ms/intuneportal).
2. Válassza az **Eszközök** > **Minden eszköz** > a törölni kívánt eszközök > **Törlés** lehetőséget.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Eszközök automatikus törlése törlési szabályok alkalmazásával
Az Intune konfigurálható úgy, hogy automatikusan törölje az inaktívnak, elavultnak vagy nem válaszolónak látszó eszközöket. Ezek a törlési szabályok folyamatosan figyelik az eszközleltárt, hogy az eszközrekordok naprakészek maradjanak. Az így törölt eszközök törlődnek az Intune-felügyeletből.
1. Jelentkezzen be az [Intune-ba az Azure Portalon](https://aka.ms/intuneportal).
2. Válassza az **Eszközök** > **Eszköztörlési szabályok** > **Igen** lehetőséget.
3. A **sok napig nem bejelentkezett eszközök törlése** mezőbe írjon be egy 30 és 270 közötti számot.
4. Válassza a **Mentés** elemet.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eszközök törlése az Azure Active Directory portálról

Előfordulhat, hogy eszközöket kell törölnie az Azure AD-ből kommunikációs problémák vagy hiányzó eszközök miatt. A **Törlés** művelettel eltávolíthatók az Azure Portalról az olyan eszköz rekordjai, amelyekről tudja, hogy nem érhetők el, és nem valószínű, hogy újra kommunikálni fognak az Azure-ral. A **Törlés** művelet nem távolítja el az eszközt a felügyelet alól.

1. Jelentkezzen be az [Azure Active Directoryba az Azure Portalon](https://aka.ms/accessaad) a rendszergazdai hitelesítő adataival. A [Microsoft 365 felügyeleti központba](https://admin.microsoft.com)is bejelentkezhet. Válassza a menüben a **Felügyeleti központok** > **Azure AD** menüpontot.
2. Ha még nem rendelkezik Azure-előfizetéssel, hozzon létre egyet. Ha díjköteles fiókkal rendelkezik, ennek elvégzéséhez nem szükséges hitelkártya vagy díjrendezés (válassza a **Register your free Azure Active Directory** előfizetési hivatkozást).
3. Válassza az **Azure Active Directory** lehetőséget, majd válassza ki a vállalatot.
4. Válassza a **Felhasználók** fület.
5. Válassza ki azt a felhasználót, aki a törölni kívánt eszközhöz van társítva.
6. Válassza az **Eszközök** lehetőséget.
7. Szükség szerint távolítsa el az eszközöket. Eltávolíthat például olyan eszközöket, amelyeket már nem használnak vagy pontatlan definíciókkal rendelkeznek.

## <a name="retire-an-apple-dep-device-from-intune"></a>Apple DEP-eszközök kivonása az Intune-ból

Ha szeretne teljesen kivonni egy Apple DEP-eszközt az Intune általi felügyeletből, kövesse az alábbi lépéseket:

1. Jelentkezzen be az [Intune-ba az Azure Portalon](https://aka.ms/intuneportal).
2. Válassza az **Eszközök** > **Minden eszköz** > a törölni kívánt eszköz > **Kivonás** lehetőséget.
![Kivonás képernyőképe](./media/devices-wipe/retire.png)
3. Látogasson el a [deploy.apple.com](http://deploy.apple.com) webhelyre, és keressen rá az eszközre a sorozatszáma alapján.
4. A **Hozzárendelve** menüben válassza a **Nincs hozzárendelés** elemet.

5. Válassza az **Újbóli hozzárendelés** lehetőséget.

    ![Képernyőkép az újbóli hozzárendelésről az Apple esetében](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Új kezdés

Alkalmazható a Windows 10-es eszközökre. További információ az [új kezdésről](device-fresh-start.md).

## <a name="next-steps"></a>További lépések

Ha szeretne egy törölt eszközt újból regisztrálni, olvassa el a [Regisztrációs lehetőségek](../enrollment/enrollment-options.md) szakaszt.

