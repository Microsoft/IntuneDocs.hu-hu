---
title: Eszközmegfelelési szabályzat Jamf-eszközökhöz
titleSuffix: Microsoft Intune
description: A JAMF által felügyelt eszközök biztonságossá tételéhez használja a Microsoft Intune megfelelőségi szabályzatokat Azure Active Directory feltételes hozzáféréssel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d23e725db965a249522f7f8fa89f8bb27bc24fd8
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680009"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro által felügyelt Mac számítógépek megfelelőségének kikényszerítése

Érintett kiadások: Intune az Azure Portalon

A Azure Active Directory és az Microsoft Intune feltételes hozzáférési szabályzatai biztosítják, hogy a végfelhasználók megfeleljenek a szervezeti követelményeknek. Ezeket a szabályzatokat a [Jamf Pro által felügyelt](conditional-access-integrate-jamf.md) Mac számítógépekre is alkalmazhatja. Ennek megvalósításához az Intune és a Jamf Pro konzolhoz egyaránt hozzáférésre van szüksége.

## <a name="set-up-device-compliance-policies-in-intune"></a>Eszközmegfelelőségi szabályzatok beállítása az Intune-ban

1. Nyissa meg a Microsoft Azure-t, majd az **Intune** > **Eszközmegfelelőség** > **Szabályzatok** oldalt. A macOS-re vonatkozó szabályzatokat is létrehozhat, többek között a nem megfelelő felhasználóknak és csoportoknak szóló műveletek (például figyelmeztető e-mailek küldése) kiválasztásával.
2. Válassza ki a szabályzatot > hozzárendeléseket. Belefoglalhat vagy kizárhat Azure Active Directory (AD) biztonsági csoportokat.
3. Válassza a kiválasztott csoportok lehetőséget az Azure AD biztonsági csoportok megjelenítéséhez. Válassza ki azokat a felhasználói csoportokat, amelyekre alkalmazni szeretné a szabályzatot > válassza a mentés lehetőséget a szabályzat felhasználók számára történő telepítéséhez.

A szabályzatot alkalmazta a felhasználókra. A szabályzat által megadott felhasználók által használt eszközök megfelelőségét a rendszer kiértékeli, és compliantfor jelöli meg az "eszköz megfelelőként való megjelölésének megkövetelése" beállítást Azure Active Directoryban.

> [!Note]
> A megfelelőség érdekében az Intune teljes lemeztitkosítást követel meg.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>A macOS-hez készült Vállalati portál alkalmazás üzembe helyezése a Jamf Pro szolgáltatásban

Az alábbi eljárást követve háttérbeli telepítésként kell üzembe helyeznie a macOS-hez készült Céges portál alkalmazást a Jamf Pro szolgáltatásban:

1. A macOS-eszközön töltse le a [macOS-hez készült céges portál alkalmazás](https://go.microsoft.com/fwlink/?linkid=862280) jelenlegi verzióját. Ne telepítse azt. Az alkalmazás egy másolatára van szükség a Jamf Pro szolgáltatásba való feltöltésre.
2. Nyissa meg a Jamf Pro szolgáltatást, majd a **Számítógép-kezelés** > **Csomagok** oldalt.
3. Hozzon létre egy új csomagot a macOS-hez készült Céges portál alkalmazással, majd kattintson a **Mentés** elemre.
4. Nyissa meg a **Számítógépek** > **Szabályzatok** oldalt, majd kattintson az **Új** elemre.
5. Az **Általános** tartalom használatával konfigurálja a szabályzat beállításait. A következő beállításokat kell használnia:
   - Eseményindító: válassza a **Regisztráció kész** és az **Ismétlődő bejelentkezés** beállítást.
   - Végrehajtás gyakorisága: válassza a **Számítógépenként egyszer** beállítást.
6. Válassza ki a **Csomagok** tartalmat, és kattintson a **Konfigurálás** elemre.
7. A **Hozzáadás** elemre kattintva válassza ki a csomagot a Céges portál alkalmazással.
8. A felugró **Művelet** menüből válassza ki a **Telepítés** lehetőséget.
9. Konfigurálja a csomag beállításait.
10. Kattintson a **Hatókör** lapra annak meghatározásához, hogy mely számítógépeken kell telepíteni a Céges portál alkalmazást. Kattintson a **Save** (Mentés) gombra. Legközelebb, amikor a megadott eseményindító kiváltódik a számítógépen, és megfelel az **Általános** tartalomban szereplő feltételeknek, a szabályzat lefut a hatókörbe bevont eszközökön.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Szabályzat létrehozása a Jamf Pro szolgáltatásban a felhasználók eszközének Azure Active Directoryban való regisztrálásához

> [!NOTE]
> A következő lépések előtt [üzembe kell helyeznie a macOS-eszközökhöz készült Céges portált](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro).  

Ahhoz, hogy az eszközt Jamf Pro által kezelt eszközként regisztrálhassák az Azure AD szolgáltatásban, a végfelhasználóknak a Jamf Self Service oldalról kell megnyitniuk a Céges portál alkalmazást. Ez egy művelet végrehajtását fogja igényelni a végfelhasználók részéről. Javasoljuk, hogy [lépjen kapcsolatba a végfelhasználókkal](end-user-educate.md) e-mailben, Jamf Pro-értesítésben vagy más módon, és kérje meg őket, hogy kattintsanak a gombra a Jamf Self Service szolgáltatásban.

> [!WARNING]
> Az eszközregisztráció sikeres megkezdéséhez a Céges portál alkalmazást mindenképpen a Jamf Self Service szolgáltatásból kell indítani. <br><br>A Céges portál alkalmazás manuális – például az alkalmazások vagy a letöltések mappájából való – indítása esetén az eszköz nem lesz regisztrálva. Ha egy végfelhasználó manuálisan indítja a Céges portál alkalmazást, az „AccountNotOnboarded” figyelmeztetést fogja látni.

1. A Jamf Pro oldalán nyissa meg a **Számítógépek** > **Szabályzatok** oldalt, és hozzon létre egy új eszközregisztrációs szabályzatot.
2. Konfigurálja a **Microsoft Intune-integráció** tartalmat, beleértve az eseményindítót és a végrehajtás gyakoriságát is.
3. A **Hatókör** lapra kattintva terjessze ki a szabályzat hatókörét az összes megcélzott eszközre.
4. A **Self Service** lapra kattintva tegye elérhetővé a szabályzatot a Jamf Self Service szolgáltatásban. Adja hozzá a szabályzatot az **Eszközmegfelelőség** kategóriához. Kattintson a **Save** (Mentés) gombra.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Jamf által felügyelt eszköz eltávolítása az Intune-ból

A Jamf által felügyelt eszközöknek az Intune-konzolról történő eltávolításához a **Minden eszköz** nézetben kattintson a **Törlés** elemre. Az eszközök csoportos törlésére is van lehetőség: jelöljön ki több eszközt, és kattintson a **Törlés** elemre.

[A Jamf által felügyelt eszköz eltávolításáról a Jamf Pro dokumentációjában](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information) olvashat részletesebben. Ha további segítségre van szüksége, támogatási jegyet is küldhet a [Jamf támogatási szolgálatának](https://www.jamf.com/support/). 

## <a name="next-steps"></a>További lépések

- [Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Ismerkedés a feltételes hozzáféréssel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
