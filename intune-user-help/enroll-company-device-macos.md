---
title: A szervezet által biztosított macOS-eszköz regisztrálása a felügyeletben | Microsoft Docs
description: Leírja, hogyan regisztrálhat egy olyan macOS-eszközt az Intune-ban, amelyet a szervezet megvásárolt és biztosít.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c20ad54f71eb44f69638eacd4ae1c3796771896
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314657"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>A szervezet által biztosított macOS-eszköz regisztrálása a felügyeletben

Ismerje meg, hogyan kezelheti az új macOS-eszközt az Intune-ban.  

A munkahelye vagy iskolája által biztosított eszközök gyakran előre vannak konfigurálva, mielőtt megkapta őket. A szervezet ezeket az előre konfigurált beállításokat a bekapcsolás és az első bejelentkezés után elküldi az eszközre. Miután az eszköz befejezte a telepítést, hozzáférést kap a munkahelyi vagy iskolai erőforrásokhoz.

A kezelés megkezdéséhez kapcsolja be az eszközt, és jelentkezzen be a munkahelyi vagy iskolai hitelesítő adataival. A cikk további részében azokat a lépéseket és képernyőket mutatjuk be, amelyeket a beállítási Asszisztensen keresztül láthat.

## <a name="what-is-apple-dep"></a>Mi az Apple DEP?

Előfordulhat, hogy a szervezete az *Apple Készülékregisztrációs program* (DEP) nevű eszközön vásárolta meg az eszközöket. Az Apple DEP lehetővé teszi, hogy a szervezetek nagy mennyiségű iOS-vagy macOS-eszközt vásárolnak. A szervezetek ezután konfigurálhatják és kezelhetik az eszközöket az előnyben részesített mobileszköz-kezelő szolgáltatón belül, például az Intune-ban. Ha Ön rendszergazda, és további információra van szüksége az Apple DEP szolgáltatásról, olvassa el [a MacOS-eszközök automatikus regisztrálása az apple Készülékregisztrációs programban](https://docs.microsoft.com/intune/enrollment/device-enrollment-program-enroll-macos)című témakört.  

## <a name="get-your-device-managed"></a>Eszköz felügyeletének beolvasása

A macOS-eszköz felügyeletbe való regisztrálásához hajtsa végre az alábbi lépéseket. Ha saját eszközt használ, és nem egy szervezet által biztosított eszközt, kövesse a [személyes és a saját eszközök](enroll-your-device-in-intune-macos-cp.md)használatára vonatkozó lépéseket.  

1. A macOS-eszköz bekapcsolása.
2. Válassza ki az országot vagy régiót, majd kattintson a **Folytatás**gombra.  

   ![Képernyőfelvétel a macOS-eszközök beállítási asszisztensének üdvözlőképernyő képernyőjéről, amely megjeleníti a választható nyelvek listáját.](./media/macos-dep-welcome-1808.png)
3. Válassza ki a billentyűzet elrendezését. A listában egy vagy több lehetőség látható a kiválasztott ország/régió alapján. Az összes elrendezési beállítás megjelenítéséhez, a kiválasztott országtól/régiótól függetlenül, kattintson az **összes megjelenítése**elemre. Ha elkészült, kattintson a **Continue (folytatás) gombra.**  

   ![Képernyőkép a macOS-eszköz beállítási asszisztensének billentyűzetkiosztási képernyőjéről, amely megjeleníti a választható billentyűzetek listáját, az összes megjelenítése jelölőnégyzetet, valamint a vissza és a folytatás gombot.](./media/macos-dep-keyboard-1808.png)  
4. Válassza ki a Wi-Fi hálózatot. A telepítés folytatásához internetkapcsolat szükséges. Ha nem látja a hálózatot, vagy ha vezetékes hálózaton keresztül szeretne csatlakozni, kattintson az **egyéb hálózati beállítások**elemre. Ha elkészült, kattintson a **Continue (folytatás**) gombra.  

   ![Képernyőfelvétel a macOS-eszközök beállítási Asszisztenséről válassza ki a Wi-Fi hálózat képernyőjét, amely megjeleníti a választható hálózatok listáját. Egy másik hálózati beállítások gomb, vissza gomb és Folytatás gomb is látható.](./media/macos-dep-wifi-1808.png)  
5. Miután csatlakozott a Wi-Fi-hez, megjelenik a **távfelügyelet** képernyő. A távfelügyelet lehetővé teszi, hogy a szervezet rendszergazdája távolról konfigurálja az eszközt a vállalat által igényelt fiókokkal, beállításokkal, alkalmazásokkal és hálózatokkal. Az eszköz felügyeletének megismeréséhez olvassa el a távfelügyelet magyarázatát. Ezután kattintson a **Continue** (Folytatás) gombra.  

   ![Képernyőkép a macOS-eszköz beállítási asszisztensének távfelügyeleti képernyőjéről, a távoli felügyeletet magyarázó szöveggel, valamint a további információkat tartalmazó dokumentációra mutató hivatkozással. A vissza gombot és a folytatás gombot is megjeleníti.](./media/macos-dep-remote-management-1-1808.png)  
6. Ha a rendszer kéri, jelentkezzen be munkahelyi vagy iskolai fiókjával. A hitelesítés után az eszköz egy felügyeleti profilt fog telepíteni. A profil konfigurálja és engedélyezi a szervezet erőforrásaihoz való hozzáférést.  
7. Olvassa el az Apple-adatok & adatvédelmi ikonját, hogy később azonosítani tudja a személyes adatok gyűjtését. Ezután kattintson a **Continue** (Folytatás) gombra.  

   ![Képernyőfelvétel a macOS-eszközök beállítási asszisztensi & adatvédelmi képernyőjéről, amely két személyből álló illusztrációt mutat be, és leírja, hogy az Apple milyen személyes adatokat használ. A vissza és a folytatás gombot is megjeleníti.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Az eszköz regisztrálását követően további lépéseket is végrehajthat. A megjelenő lépések attól függnek, hogy a szervezet hogyan szabta testre a telepítési folyamatot. Ehhez a következőket kell tennie:
    * Bejelentkezés Apple-fiókba
    * A feltételek és Kikötések elfogadása
    * Számítógépfiók létrehozása
    * Az expressz telepítés
    * A Mac beállítása

## <a name="get-the-company-portal-app"></a>A Céges portál alkalmazás beszerzése

Töltse le a macOS rendszerhez készült Intune Céges portál alkalmazást az eszközön. Az alkalmazás lehetővé teszi az eszköz felügyeletét, szinkronizálását, hozzáadását és eltávolítását, valamint az alkalmazások telepítését. Ezek a lépések azt is ismertetik, hogyan lehet regisztrálni az eszközt a Céges portál.

1. A macOS-eszközön nyissa meg a következőt: [https://portal.manage.microsoft.com/EnrollmentRedirect.aspx](https://portal.manage.microsoft.com/EnrollmentRedirect.aspx).
2. Jelentkezzen be a Céges portál webhelyére munkahelyi vagy iskolai fiókjával. 
3. Kattintson **az alkalmazás** letöltése gombra a MacOS céges portál telepítőjének letöltéséhez.
4. Ha a rendszer kéri, nyissa meg a. pkg fájlt, és fejezze be a telepítési lépéseket.
5. Nyissa meg a Céges portál alkalmazást, és jelentkezzen be munkahelyi vagy iskolai fiókjával.
6. Keresse meg az eszközt, és kattintson a **regisztráció**elemre.
7. Kattintson a **folytatás** > **kész**lehetőségre. Az eszköznek most meg kell jelennie a Céges portál alkalmazásban vállalati és megfelelő eszközként.

Továbbra is segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához. A kapcsolattartási adatokat a [céges portál webhelyén találja](https://go.microsoft.com/fwlink/?linkid=2010980).
