---
title: Mac regisztrálása a Intune Céges portál | Microsoft Docs
description: Ismerje meg, hogyan regisztrálhat Mac-et az Intune-ban a Céges portál alkalmazással.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098133"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>MacOS-eszköz regisztrálása a Céges portál alkalmazás használatával  

A macOS-eszköz regisztrálása a Intune Céges portál alkalmazással biztonságos hozzáférést biztosít a munkahelyi vagy iskolai e-mailekhez, fájlokhoz és alkalmazásokhoz.

A szervezetek általában az eszköz regisztrálásához szükségesek ahhoz, hogy hozzáférjenek a tulajdonosi adataihoz. Az eszköz regisztrálása után a rendszer *felügyeli*. A szervezet a mobileszköz-felügyeleti (MDM-) szolgáltatón (például az Intune-on) keresztül rendelhet szabályzatokat és alkalmazásokat az eszközhöz. Az eszközön a munkahelyi vagy iskolai adatok folyamatos eléréséhez úgy kell beállítania az eszközt, hogy az megfeleljen a szervezet házirend-beállításainak.  

Ez a cikk azt ismerteti, hogyan használható a macOS rendszerhez készült Céges portál alkalmazás az eszköz regisztrálására, konfigurálására és karbantartására, hogy megfeleljen a szervezet igényeinek.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Ami a Céges portál alkalmazástól elvárható

A kezdeti beállítás során a Céges portál alkalmazásnak be kell jelentkeznie, és hitelesítenie kell magát a szervezetében. A Céges portál ezután tájékoztatja a szervezet követelményeinek teljesítéséhez konfigurálni kívánt eszközökről. A vállalatok gyakran megadják például a jelszavak minimális vagy maximális karakterszámát, és ezt Önnek be kell tartania.    

Az eszköz regisztrálása után a Céges portál mindig ellenőrzi, hogy az eszköz védett-e a szervezet követelményeinek megfelelően. Ha például egy alkalmazást nem megbízható forrásból telepít, Céges portál riasztást küld, és a szervezet erőforrásaihoz való hozzáférést is korlátozhatja. Ilyenek például az alkalmazás-védelmi szabályzatok. A hozzáférés helyreállításához valószínűleg el kell távolítania a nem megbízható alkalmazást. 

Ha a regisztrációt követően a szervezet új biztonsági követelményt (például többtényezős hitelesítést) érvényesít, Céges portál értesíti Önt. Lehetősége lesz módosítani beállításait, hogy továbbra is dolgozhasson az eszközéről.  

További információk a regisztrációval kapcsolatban: [Mi történik a Céges portál alkalmazás telepítésekor és az eszköz regisztrálásakor?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>MacOS-eszköz felügyeletének beolvasása  
A következő lépésekkel regisztrálja macOS-eszközét a szervezetében. Az eszközön macOS 10,12 vagy újabb rendszernek kell futnia.   

> [!NOTE]
> A folyamat során előfordulhat, hogy a rendszer arra kéri, hogy Céges portál a kulcstartóban tárolt bizalmas információk használatára. Ezek a kérések az Apple Security részét képezik. A kérdés beírásakor írja be a bejelentkezési kulcstartó jelszavát, és válassza a **mindig Engedélyezés lehetőséget**. Ha megnyomja az **ENTER** billentyűt vagy a **visszatérést** a billentyűzeten, a kérés Ehelyett az **Engedélyezés lehetőséget**választja, ami további kéréseket eredményezhet.  

### <a name="install-company-portal-app"></a>Céges portál alkalmazás telepítése  
1. Nyissa meg a [Mac-regisztrációt](https://go.microsoft.com/fwlink/?linkid=853070).  
2. A rendszer letölti a Céges portál Installer. pkg fájlt. Nyissa meg a telepítőt, és folytassa a lépéseket. 
3. Fogadja el a szoftverlicenc-szerződést. 
4. Adja meg az eszköz jelszavát vagy a regisztrált ujjlenyomatot a szoftver telepítéséhez.  
5. Nyissa meg Céges portál. 

> [!IMPORTANT]
> Előfordulhat, hogy a Microsoft AutoUpdate megnyitotta a Microsoft-szoftverek frissítését. Az összes frissítés telepítése után nyissa meg a Céges portál alkalmazást. A legjobb telepítési élmény érdekében telepítse a Microsoft AutoUpdate és a Céges portál legújabb verzióit.  


### <a name="enroll-your-mac"></a>Mac-regisztráció  


1. Jelentkezzen be Céges portálra munkahelyi vagy iskolai fiókjával.  
2. Az alkalmazás megnyitásakor válassza az **Indítás**lehetőséget.  
3. Tekintse át, hogy a cége [mit láthat és mit nem láthat](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) a regisztrált eszközön. Ezután válassza a **Continue** (Folytatás) gombot.  
4. A **felügyeleti profil telepítése** képernyőn válassza a **profil letöltése**lehetőséget.   

    ![Példa a Céges portálre, a felügyeleti profil telepítése képernyőre, és a "profil letöltése" gombra.](./media/install-mgmt-profile-mac-1911.PNG)   
5. Ekkor megnyílik az eszköz rendszerbeállításai. Válassza a **telepítés** lehetőséget, majd válassza a **telepítés** újra lehetőséget. Ha a rendszer kéri, adja meg az eszköz jelszavát.  

    ![Példa a macOS rendszer beállításairól, a telepítési kérésről, a "telepítés" gombra.](./media/system-preference-install-1911.PNG)  
6. A profil telepítése után a rendszer a **felügyeleti profilban** megjelenik a profilok listájában.  

   ![Példa a macOS rendszer beállításai, profilok képernyő, a telepített felügyeleti profil kiemelése képernyőképre.](./media/system-preference-verify-1911.PNG)   
7. Vissza Céges portál.   
8. Előfordulhat, hogy a szervezetnek frissítenie kell az eszköz beállításait. Ha elkészült a beállítások frissítésével, válassza a **Beállítások ellenőrzése**lehetőséget.  

    ![Példa a Céges portál képernyőképére, az eszközbeállítások képernyő frissítésére, és a "beállítások ellenõrzése" gombra.](./media/update-settings-mac-1911.PNG)  
9. Ha a telepítés befejeződött, válassza a **kész**gombot.  


 ## <a name="troubleshooting-and-feedback"></a>Hibaelhárítás és visszajelzés   

Ha a regisztráció során problémákba ütközik, lépjen a **súgó** > **diagnosztikai jelentés küldése** elemre, hogy jelentse a problémát a Microsoft-alkalmazások fejlesztőinek. Ezek az információk segítenek az alkalmazás tökéletesítésében. Ezeket az információkat is felhasználhatják a probléma megoldásához, ha az informatikai támogatási személy a segítségére jut.  

Miután bejelentette a problémát a Microsoftnak, elküldheti a felhasználói élmény részleteit az informatikai támogatási személynek. Válassza ki az **e-mailek adatait**. Írja be, hogy mit tapasztalt az e-mail törzsében. A támogatási személy e-mail-címének megkereséséhez nyissa meg a Céges portál alkalmazás > **Névjegy**lehetőséget. Vagy keresse meg a [céges portál webhelyet](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Emellett a Microsoft Intune Céges portál csapata szívesen hallja a visszajelzését. Lépjen a **súgó** > **visszajelzés küldése** gombra a gondolatok és ötletek megosztásához.  

## <a name="unverified-profiles"></a>Ellenőrizetlen profilok  
Ha megtekinti a telepített mobileszköz-kezelési (MDM) profilokat a **Rendszerbeállítások** > a **profilok**között, egyes profilok nem ellenőrzött állapotot jelezhetnek. Ha a felügyeleti profil ellenőrzött állapotot mutat, nem kell foglalkoznia.  

A felügyeleti profil határozza meg az MDM-csatorna kapcsolatát. Ha a felügyeleti profil ellenőrzése megtörtént, az adott csatornán keresztül a gépre küldött egyéb profilok öröklik a felügyeleti profil biztonsági sajátosságait.  

## <a name="updating-the-company-portal-app"></a>A Céges portál alkalmazás frissítése

A Céges portál alkalmazás frissítése ugyanúgy történik, mint bármely más Office-alkalmazáshoz a macOS rendszerhez készült Microsoft autoupdaten keresztül. Tudjon meg többet a [MacOS-hez készült Microsoft-alkalmazások frissítéséről](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>További lépések  
További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  


