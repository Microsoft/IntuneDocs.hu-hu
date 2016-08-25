---
# required metadata

title: Újdonságok – archívum | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


## 2015. szeptember
### Mobileszköz- és alkalmazásfelügyeleti frissítések
**Mostantól az Intune összes iOS-felügyeleti szolgáltatása támogatja az iOS 9 rendszert**
Az iOS 9-felügyeleti képességekkel kapcsolatos részletekről [ebben a blogbejegyzésben](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx) olvashat..

**Új mobilalkalmazás-konfigurációs házirend az iOS rendszerhez**
Az új mobilalkalmazás-konfigurációs házirenddel automatikusan adhat meg olyan beállításokat, amelyekre az iOS-alkalmazásoknak szükségük lehet a futtatásukkor. Megadhat például egy hálózati portot vagy egy felhasználónevet. Részletekért lásd: [Alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban](https://technet.microsoft.com/library/mt481447.aspx)..

**Egyszerűbb alkalmazásfelügyelet iOS 9-felhasználóknak**
 Ebben a kiadásban a már telepített alkalmazásokat iOS 9-felhasználók esetén az Intune felügyelete alá helyezheti. Ha az iOS korábbi verziói esetén telepít egy alkalmazást, és az alkalmazás nem felügyelt verziója már telepítve van az eszközön, továbbra is meg kell kérnie a felhasználót, hogy kézzel távolítsa el az alkalmazást, mielőtt az Intune telepítené a felügyelt alkalmazást.

 Az Intune jelen kiadásával kezdődően azonban arra kérheti az iOS 9-eszközök felhasználóit, hogy engedélyezzék az Intune számára az alkalmazás felügyeletének átvételét és a megfelelő mobilalkalmazás-felügyeleti szabályzatok alkalmazását.

 **A Windows 10 felügyelete** Az új [általános Windows 10-es konfigurációs házirend](https://technet.microsoft.com/library/mt404697.aspx) használatával konfigurálhatja a Windows 10 vagy Windows 10 Mobile rendszert futtató, regisztrált eszközök jelszó-, eszköz-, böngésző- és más beállításait.

 **Alkalmazások létrehozása és telepítése regisztrált Windows 10-eszközökre** A Windows Installer mobileszköz-felügyelettel (*.msi) új szoftvertelepítő-típussal Windows Installer-alkalmazásokat hozhat létre és telepíthet a Windows 10-et futtató regisztrált eszközökre. A részletekért lásd: [Az alkalmazások telepítésének első lépései a Microsoft Intune-ban](https://technet.microsoft.com/library/dn646955.aspx)..

### A Microsoft vállalati portál alkalmazásainak módosításai és frissítései
Ebben a kiadásban a következő módosítások lettek bevezetve a vállalati portál alkalmazásaival kapcsolatban:

**iOS**
* A Microsoft termék- és szolgáltatásfejlesztési célból automatikus módszerekkel név nélküli adatokat gyűjt a vállalati portál teljesítményéről és használatáról. A végfelhasználók bármikor kikapcsolhatják az adatok gyűjtését eszközük használati adatokra vonatkozó beállításával, rendszergazdák azonban nem szabályozhatják az adatgyűjtést, és nem módosíthatják e beállítás végfelhasználói szakaszát.
* A teljes képernyős felbontás támogatása az iPhone 6 és 6 Plus eszközön
* Correction de bogues pour améliorer la sécurité

### Újdonságok az Intune-ban – 2015. szeptember
**Új témakörök**

|Név|Részletek|
|----|--------|
|[A Windows 10 konfigurációs házirendjének beállításai a Microsoft Intune-ban](https://technet.microsoft.com/library/mt404697.aspx)|Ez egy olyan új konfigurációs házirend, amellyel kezelheti a beállításokat és a funkciókat a Windows 10-et és Windows 10 Mobile-t futtató eszközökön.
| [Alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban](https://technet.microsoft.com/library/mt481447.aspx)|Ez egy olyan új házirendtípus, amellyel automatikusan megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy iOS-alkalmazást futtat. |

**Frissített témakörök**

|Név|Részletek|
|----|-------|
|[Házirendek használata a számítógépek és mobileszközök kezeléséhez a Microsoft Intune-nal](https://technet.microsoft.com/library/dn743712.aspx)|A frissítés eredményeképpen tartalmazza a legújabb információkat, amelyek segítenek a házirendek megértésében és létrehozásában.|

## 2015. augusztus
### Mobileszköz- és alkalmazásfelügyeleti frissítések
* Az Intune-regisztráció és a vállalati hozzáférés**használati feltételei** [már házirendek használatával kezelhetők](https://technet.microsoft.com/library/mt405893.aspx). Az egyes felhasználói csoportok eltérő igényeinek kielégítéséhez különböző feltételkészleteket hozhat létre. A földrajzi elhelyezkedés alapján definiált felhasználói csoportok számára például különböző nyelveken teheti elérhetővé a használati feltételeket. A [használati feltételeket módosíthatja](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) is, és megadhatja, hogy a hogy a verziószámok növekedjenek-e, valamint megkövetelheti a felhasználóktól az új feltételek elfogadását, mielőtt megkezdenék a vállalati portál használatát.
* **Számos Intune-házirendet átneveztünk** a termékben való egységes megjelenés és a könnyebb keresés érdekében. Az összes elérhető Intune-házirend listájáért lásd: [Házirendek használata a számítógépek és mobileszközök kezeléséhez a Microsoft Intune-nal](https://technet.microsoft.com/library/dn743712.aspx)..
* **PKCS #12 (. PFX) tanúsítványprofilok** érhetők el az Android 4.0 vagy újabb, illetve a Windows 10 vagy újabb (asztali és mobil-) rendszerhez. A .PFX használatához nincs szükség NDES-kiszolgálóra. A .PFX tanúsítványprofilok létrehozásával kapcsolatban lásd: [Vállalati erőforrások elérésének lehetővé tétele a Microsoft Intune tanúsítványprofiljaival](http://technet.microsoft.com/library/dn818904.aspx)
* **A Windows 10 asztali és mobil verziójának vállalati határbeállításai** lehetővé teszik a részletes VPN-beállítások használatát a következő témakörben leírtak szerint: [Segítség a felhasználóknak a munkájukhoz való csatlakozásban VPN-profilok használatával a Microsoft Intune-nal](https://technet.microsoft.com/library/dn818905.aspx)
* **Az androidos OneDrive alkalmazás már támogatja a többszörös identitás használatát**. Erről és a mobilalkalmazás-felügyeleti házirendekkel kapcsolatos egyéb frissítésekről a [felügyelhető Microsoft-alkalmazások listájában tájékozódhat](https://technet.microsoft.com/library/dn708489.aspx)..
* **iOS-alapú aktiválási zár megkerülése**. Ha a céges iOS-eszközök aktiválási zárral vannak védve, egy adott eszköz törléséhez vagy újraaktiválásához először meg kell adni a felhasználó Apple ID azonosítóját és jelszavát. Ez kihívást jelenthet, ha a felhasználók elhagyják a vállalatot és az aktiválási zár kikapcsolása nélkül szolgáltatják vissza a céges eszközöket. A probléma megoldásához használhatja az [aktiválási zár megkerülését az Intune-ban](https://technet.microsoft.com/library/mt414176.aspx).

### Feltételes hozzáférés a PC-ken
Már PC-ken is konfigurálhat feltételes hozzáférési szabályzatokat. Ez lehetővé teszi az Office asztali alkalmazásai számára az Exchange Online és a SharePoint online szolgáltatás elérését.
Csak olyan PC-n engedélyezhetők a feltételes hozzáférési szabályzatok, amely tartományhoz van csatlakoztatva, vagy alkalmas a csatlakoztatásra.
* [Az e-mailek és a SharePoint hozzáférésének kezelése a Microsoft Intune használatával](http://technet.microsoft.com/library/dn818907).aspx) témakör **Első lépések** szakaszában megtalálható minden, a számítógépek feltételes hozzáférésének engedélyezésére vonatkozó követelmény.
* Az e-mail-hozzáférés esetén a feltételes hozzáférést engedélyező beállításokkal kapcsolatban lásd: [E-mail-hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705841.aspx).
* A SharePoint Online feltételes hozzáférését engedélyező beállításokkal kapcsolatban lásd: [A SharePoint Online-hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705844.aspx).

### A Microsoft vállalati portál alkalmazásainak módosításai és frissítései
Ebben a kiadásban a következő módosítások lettek bevezetve a vállalati portál alkalmazásaival kapcsolatban:

**Android**

Azon felhasználók számára, akik még nem regisztrálták eszközüket, a bejelentkezés után megjelennek az eszközregisztrációs utasítások.

### Újdonságok az Intune dokumentációjában -- 2015. augusztus
**Új témakörök**

|Cím|Részletek|
|-----|-------|
|[Az iOS-eszközök védelme a Microsoft Intune-hoz készült aktiválásizár-megkerüléssel](https://technet.microsoft.com/library/mt414176.aspx)|Annak ismertetése, hogy az Intune használatával miként kerülhető meg az iOS-alapú aktiválás zárolás, ha egy felhasználó kilép a cégtől, és egy zárolt eszközt ad vissza.|

**Frissített témakörök**

|Cím|Részletek|
|-----|-------|
|[A Microsoft Intune mobilalkalmazás-kezelési házirendekkel használható Microsoft-alkalmazások](https://technet.microsoft.com/library/dn708489.aspx)|Frissített információk a mobilalkalmazás-felügyeleti házirendekkel kezelhető alkalmazásokról.
|[Házirendek használata a számítógépek és mobileszközök kezeléséhez a Microsoft Intune-nal](http://technet.microsoft.com/library/dn743712.aspx)|Frissítve az Intune-hoz hozzáadott legújabb házirendekkel.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->


<!--HONumber=May16_HO1-->


