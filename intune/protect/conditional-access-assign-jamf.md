---
title: Eszközmegfelelési szabályzat Jamf-eszközökhöz
titleSuffix: Microsoft Intune
description: A JAMF által felügyelt eszközök biztonságossá tételéhez használja a Microsoft Intune megfelelőségi szabályzatokat Azure Active Directory feltételes hozzáféréssel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: 93265c2491058afde7168134075bed77031b9311
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/18/2019
ms.locfileid: "74161593"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro által felügyelt Mac számítógépek megfelelőségének kikényszerítése

Ha [integrálja a JAMF Pro-t az Intune](conditional-access-integrate-jamf.md)-nal, a feltételes hozzáférési szabályzatok segítségével kényszerítheti a Mac-eszközök megfelelőségét a szervezeti követelményeknek megfelelően.  Ez a cikk a következő feladatokhoz nyújt segítséget:  

- Feltételes hozzáférési szabályzatok létrehozása.
- Konfigurálja a JAMF Pro-t, hogy a Intune Céges portál alkalmazást a JAMF-mel kezelt eszközökre telepítse.
- Konfigurálja az eszközöket az Azure AD-ben való regisztrálásra, amikor az eszköz felhasználója bejelentkezik a Céges portál alkalmazásba, amely a JAMF önkiszolgáló alkalmazásból indul el. Az eszköz regisztrálása létrehoz egy identitást az Azure AD-ben, amely lehetővé teszi, hogy a feltételes hozzáférési szabályzatok alapján kiértékelje az eszközt a vállalati erőforrásokhoz való hozzáféréshez.  
 
A cikkben ismertetett eljárásokhoz az Intune és a JAMF Pro konzolokhoz is hozzá kell férni.

## <a name="set-up-device-compliance-policies-in-intune"></a>Eszközmegfelelőségi szabályzatok beállítása az Intune-ban

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **megfelelőségi szabályzatok**lehetőséget. Ha korábban létrehozott házirendet használ, válassza ki ezt a házirendet a konzolon, majd folytassa az eljárás következő lépésével. Új szabályzat létrehozásához válassza a **házirend létrehozása** lehetőséget, majd adja meg a szabályzat részleteit a **MacOS** *platformmal* . Konfigurálja a nem megfelelőség *beállításait* és *műveleteit* a szervezeti követelmények teljesítéséhez, majd válassza a **Létrehozás** lehetőséget a szabályzat mentéséhez.

3. A házirendek *Áttekintés* ablaktáblán válassza a **hozzárendelések**lehetőséget. Az elérhető beállítások segítségével konfigurálhatja, hogy mely Azure Active Directory (Azure AD) felhasználók és biztonsági csoportok kapják meg ezt a házirendet. A JAMF és az Intune közötti integráció nem támogatja az erőforráscsoportok megkeresésére vonatkozó megfelelőségi szabályzatot.

4. A **Mentés**gombra kattintva a házirend a felhasználók számára települ.  

Az Ön által telepített házirendek a hozzárendelt felhasználók által használt eszközöket célozzák meg. Az eszközök megfelelőségét a rendszer kiértékeli. A megfelelő eszközök megfelelőként vannak megjelölve az Azure AD-ben az "*eszköz megfelelőként való megjelölésének megkövetelése*" beállítással.  

> [!NOTE]
> A megfelelőség érdekében az Intune teljes lemeztitkosítást követel meg.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>A macOS-hez készült Vállalati portál alkalmazás üzembe helyezése a Jamf Pro szolgáltatásban

Hozzon létre egy szabályzatot a JAMF Pro-ban a Intune Céges portál telepítéséhez. Ez a szabályzat telepíti a vállalati portál alkalmazást, hogy az elérhető legyen a JAMF önkiszolgáló szolgáltatásban. A szabályzat létrehozása előtt hozza létre a szabályzatot a JAMF Pro-ban a felhasználók számára az eszközök Azure AD-vel való regisztrálásához.  

Az alábbi eljárás végrehajtásához hozzáférésre van szüksége egy macOS-eszközhöz és a JAMF Pro portálhoz. 

### <a name="to-deploy-the-company-portal-app"></a>A vállalati portál alkalmazás üzembe helyezése  

1. MacOS-eszközön töltse le, de ne telepítse a [MacOS rendszerhez készült céges portál alkalmazás](https://go.microsoft.com/fwlink/?linkid=862280)aktuális verzióját. Csak az alkalmazás egy példányát kell használnia, hogy feltöltse az alkalmazást a JAMF Pro-ba.  

2. Nyissa meg a JAMF Pro-t, és válassza a **Számítógép-kezelés** > **csomagokat**.

3. Hozzon létre egy új csomagot a macOS rendszerhez készült Céges portál alkalmazással, majd válassza a **Mentés**lehetőséget.

4. Nyissa meg a **Számítógépek** > **Szabályzatok** oldalt, majd kattintson az **Új** elemre.

5. Az **Általános** tartalom használatával konfigurálja a szabályzat beállításait. A következő beállításokat kell használnia:
   - Eseményindító: válassza a **Regisztráció kész** és az **Ismétlődő bejelentkezés** beállítást.
   - Végrehajtás gyakorisága: válassza a **Számítógépenként egyszer** beállítást.

6. Válassza ki a **Csomagok** tartalmat, és kattintson a **Konfigurálás** elemre.

7. A **Hozzáadás** elemre kattintva válassza ki a csomagot a Céges portál alkalmazással.

8. Válassza a **telepítés** lehetőséget a **művelet** előugró menüből.
9. Konfigurálja a csomag beállításait.

10. Válassza ki a **hatókör** lapot annak megadásához, hogy mely számítógépeken kell telepíteni a céges portál alkalmazást. Válassza a **Mentés** lehetőséget. A házirend hatókörön belüli eszközökön fut, amikor a kiválasztott aktiválás következő lépése a számítógépen történik, és az **általános** adattartalomban szereplő feltételek teljesülnek.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Szabályzat létrehozása a Jamf Pro szolgáltatásban a felhasználók eszközének Azure Active Directoryban való regisztrálásához  

Miután [telepítette a](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) MacOS rendszerhez készült céges portál a JAMF Pro önkiszolgáló szolgáltatással, létrehozhatja a JAMF Pro-szabályzatot, amely a felhasználó eszközét regisztrálja az Azure ad-ben. 

Az eszközök regisztrálásához az eszköz felhasználójának manuálisan kell kiválasztania a Intune Céges portál alkalmazást a JAMF önkiszolgáló szolgáltatáson belül. Javasoljuk, hogy e-mailben, JAMF Pro-értesítéseken vagy bármely más, a szervezet által használt módon [lépjen kapcsolatba a végfelhasználókkal](../fundamentals/end-user-educate.md) a művelet befejezéséhez, hogy az eszközök regisztrálva legyenek. 

> [!WARNING]
> A Céges portál alkalmazás manuális elindítása (például az alkalmazások vagy a letöltések mappából) nem regisztrálja az eszközt. Ha az eszköz felhasználója manuálisan indítja el a Céges portál, akkor megjelenik egy figyelmeztetés, **"AccountNotOnboarded"** .

### <a name="to-create-the-registration-policy"></a>A regisztrációs szabályzat létrehozása  

1. A JAMF Pro-ban lépjen a **számítógépek** > **házirendek**elemre, majd hozzon létre egy új szabályzatot az eszközök regisztrálásához.

2. Konfigurálja a **Microsoft Intune-integráció** tartalmat, beleértve az eseményindítót és a végrehajtás gyakoriságát is.

3. Válassza a **hatókör** fület, majd a házirend hatókörét az összes megcélzott eszközre.

4. Válassza az **önkiszolgáló** fület, hogy a szabályzat elérhető legyen a JAMF önkiszolgáló szolgáltatásban. Adja hozzá a szabályzatot az **Eszközmegfelelőség** kategóriához. Kattintson a **Mentés**gombra.

## <a name="validate-intune-and-jamf-integration"></a>Az Intune és a JAMF integrációjának ellenőrzése  

A JAMF Pro konzollal ellenőrizze, hogy a JAMF Pro és a Microsoft Intune közötti kommunikáció sikeres-e. 

- A JAMF Pro-ban lépjen a **beállítások** > **globális felügyelet** > **Microsoft Intune integráció**, majd a **teszt**elemre.

    A konzolon megjelenik egy üzenet, amely a kapcsolatok sikerességét vagy hibáját jelzi.  

Ha a JAMF Pro konzolon nem sikerül a kapcsolatok tesztelése, tekintse át a JAMF konfigurációját. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Jamf által felügyelt eszköz eltávolítása az Intune-ból

JAMF által felügyelt eszköz eltávolításához nyissa meg a Microsoft Endpoint Manager felügyeleti központot, és válassza az **eszközök** > **minden eszköz**lehetőséget, válassza ki az eszközt, majd válassza a **Törlés**lehetőséget.  Az eszközök csoportos törlésére is van lehetőség: jelöljön ki több eszközt, és kattintson a **Törlés** elemre.

A [JAMF által felügyelt eszközök JAMF Pro docs-beli eltávolításával](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)kapcsolatos információk. További segítségért a támogatási jegyet is [JAMF-támogatással](https://www.jamf.com/support/) teheti meg. 

## <a name="next-steps"></a>További lépések

- [Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Ismerkedés a feltételes hozzáféréssel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
