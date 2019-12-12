---
title: A Jamf Pro integrálása a Microsoft Intune-nal a megfelelőség érdekében
titleSuffix: Microsoft Intune
description: A JAMF által felügyelt eszközök integrálásához és védelméhez Azure Active Directory feltételes hozzáféréssel Microsoft Intune megfelelőségi szabályzatokat használhat.
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
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01dae8f6c90155e649211ab226cf24eeade29b42
ms.sourcegitcommit: f5108039f0ade52e95ea3ac1da1aa16d02224af3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/09/2019
ms.locfileid: "74946682"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>A Jamf Pro integrálása az Intune-nal a megfelelőség érdekében

Ha a szervezete a [JAMF Pro](https://www.jamf.com) -t használja a MacOS-eszközök kezeléséhez, Microsoft Intune megfelelőségi szabályzatokat használhat Azure Active Directory (Azure ad) feltételes hozzáféréssel annak biztosításához, hogy a szervezetben lévő eszközök megfeleljenek a vállalati erőforrásokhoz való hozzáféréshez. Ez a cikk segítséget nyújt a JAMF-integráció konfigurálásához az Intune-nal.

Ha a JAMF Pro integrálva van az Intune-nal, az Azure AD-n keresztül szinkronizálhatja a macOS-eszközök leltári adatait az Intune használatával. Az Intune megfelelőségi motorja ezután elemzi a leltári adatkészletet a jelentések létrehozásához. Az Intune elemzése az eszköz felhasználójának Azure AD-identitásával kapcsolatos intelligenciával együtt a kényszerítést a feltételes hozzáférés használatával hajtja. A feltételes hozzáférési szabályzatoknak megfelelő eszközök hozzáférést kaphatnak a védett vállalati erőforrásokhoz.

Az integráció konfigurálása után [konfigurálja a JAMF és az Intune-t úgy, hogy](conditional-access-assign-jamf.md) a JAMF által felügyelt eszközökön feltételes hozzáféréssel kényszerítse ki a megfelelőséget.

## <a name="prerequisites"></a>Előfeltételek

### <a name="products-and-services"></a>Termékek és szolgáltatások

A JAMF Pro-val való feltételes hozzáférés konfigurálásához a következőkre van szükség:

- A Jamf Pro 10.1.0-ás vagy későbbi verziója
- [macOS-hez készült Céges portál alkalmazás](https://aka.ms/macoscompanyportal)
- macOS-eszközök OS X 10,12 Yosemite vagy újabb verzióval

### <a name="network-ports"></a>Hálózati portok

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
A következő portoknak elérhetőknek kell lenniük a JAMF és az Intune megfelelő integrálásához:

- **Intune**: 443-es port
- **Apple**: portok 2195, 2196 és 5223 (leküldéses értesítések az Intune-ba)
- **JAMF**: 80-es és 5223-es portok

Ahhoz, hogy a APNS megfelelően működjön a hálózaton, engedélyeznie kell a kimenő kapcsolatokat is a következőhöz:

- az Apple 17.0.0.0/8 blokkolja a 5223-es és a 443-es TCP-portokat az összes ügyfél-hálózatról.
- a JAMF Pro-kiszolgálók 2195-es és 2196-es portjai.  

További információt ezekről a portokról a következő cikkekben talál:

- [Az Intune hálózati konfigurációs követelményei és sávszélessége](../fundamentals/network-bandwidth-use.md).
- A JAMF Pro által a jamf.com-on [használt hálózati portok](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) .
- Az [Apple Software Products által használt TCP-és UDP-portok](https://support.apple.com/HT202944) a support.Apple.com-on

## <a name="connect-intune-to-jamf-pro"></a>Az Intune és a JAMF Pro összekötése

Az Intune és a JAMF Pro összekötése:

1. Hozzon létre egy új alkalmazást az Azure-ban.
2. A JAMF Pro-val való integráció engedélyezése az Intune-nal.
3. Feltételes hozzáférés konfigurálása a JAMF Pro-ban.

### <a name="create-an-application-in-azure-active-directory"></a>Alkalmazás létrehozása az Azure Active Directoryban

1. A [Azure Portal](https://portal.azure.com)lépjen a **Azure Active Directory** > alkalmazás- **regisztrációk**elemre, majd válassza az **új regisztráció**lehetőséget.

2. Az **alkalmazás regisztrálása** lapon a következő részleteket kell megadnia:

   - A **név** szakaszban adjon meg egy értelmes alkalmazásnév nevet, például **JAMF feltételes hozzáférés**.
   - A **támogatott fióktípus** szakaszban válassza a fiókok lehetőséget **bármely szervezeti címtárban**.
   - Az **átirányítási URI**esetében hagyja meg az alapértelmezett webes beállítást, majd adja meg a JAMF Pro-példány URL-címét.

3. Válassza a **regisztráció** lehetőséget az alkalmazás létrehozásához és az új alkalmazás **Áttekintés** lapjának megnyitásához.

4. Az alkalmazás **áttekintése** lapon másolja az **alkalmazás (ügyfél) azonosító** értékét, és jegyezze fel későbbi használatra. Ezt az értéket későbbi eljárásokban kell megadnia.

5. Válassza a **tanúsítványok & a titkok** elemet a **kezelés**alatt. Válassza az **új ügyfél titka** gombot. Adjon meg egy értéket a **Leírás**mezőben, válassza a **lejárat** lehetőséget, majd válassza a **Hozzáadás**elemet.

   > [!IMPORTANT]
   > Mielőtt elhagyja ezt a lapot, másolja ki az ügyfél titkos kulcsának értékét, és jegyezze fel későbbi használatra. Erre az értékre szüksége lesz a későbbi eljárásokban. Ez az érték nem érhető el újra az alkalmazás regisztrációjának újbóli létrehozása nélkül.

6. Válassza az **API-engedélyek** lehetőséget a **Kezelés** területen. 

7. Az API-engedélyek lapon válassza az **engedély hozzáadása** lehetőséget új engedély hozzáadásához. Az **API-engedélyek kérése** lapon válassza az **Intune**lehetőséget, majd válassza az **alkalmazás engedélyei**lehetőséget. Jelölje be a csak **update_device_attributes**jelölőnégyzetet.

8. Várjon néhány percet, hogy az új engedély érvénybe léphet. Ezután válassza a **rendszergazdai jóváhagyás megadása lehetőséget a _bérlő >\<ához_** . Hitelesítse a fiókját az új ablakban, és az utasításokat követve adja meg az alkalmazás elérését.  

9. Előfordulhat, hogy néhány percet várnia kell, hogy a rendszergazdai engedély érvénybe lép.

10. A lap tetején található **frissítés** gombra kattintva frissítse a lapot. Győződjön meg arról, hogy a **update_device_attributes** engedélyhez rendszergazdai jóváhagyás lett megadva. 

11. Távolítsa el a rendszergazda beleegyezését a **felhasználó. olvasás** engedéllyel. ehhez kattintson a **...** menüre, és válassza a **rendszergazdai beleegyezés visszavonása**lehetőséget.

12. Emellett el kell távolítania a **User. Read** engedélyt. Válassza a **...** menüt **felhasználó szerint. olvassa el** , majd válassza az **Eltávolítás engedélyt**. 

8. Az alkalmazás sikeres regisztrálását követően az API-engedélyek csak egy **update_device_attributes** nevű engedélyt tartalmazhatnak, és a következőképpen kell megjelenniük:

   ![Sikeres engedélyek](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Befejeződött az alkalmazás regisztrációs folyamata az Azure AD-ben.

    > [!NOTE]
    > Ha az ügyfél titkos kulcsa lejár, létre kell hoznia egy új ügyfél-titkos kulcsot az Azure-ban, majd frissítenie kell a feltételes hozzáférési adatot a JAMF Pro-ban. Az Azure lehetővé teszi, hogy a régi titok és az új kulcs aktív legyen a szolgáltatás megszakadásának megelőzése érdekében.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Az Intune engedélyezése a Jamf Pro-val történő integrációra

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** lehetőséget > **partner-eszközök kezelése**lehetőségre.

3. Engedélyezze a *megfelelőségi összekötőt a JAMF* , ha beillesztette az előző eljárás során mentett alkalmazás azonosítóját az **Azure Active Directory alkalmazás azonosítójának megadása a JAMF** mezőben.

4. Válassza a **Mentés** lehetőséget.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>A Microsoft Intune-integráció konfigurálása a Jamf Pro szolgáltatásban

1. Aktiválja a JAMF Pro-konzolon található kapcsolatokat:

   1. Nyissa meg a JAMF Pro konzolt, és navigáljon a **globális felügyelet** > a **feltételes hozzáférés**elemre. Kattintson a **Szerkesztés** gombra a **MacOS Intune-integráció** lapon.
   2. Jelölje be az Intune- **integráció engedélyezése MacOS-hez**jelölőnégyzetet.
   3. Adja meg az Azure-bérlőre vonatkozó szükséges információkat, beleértve a **helyet**, a **tartománynevet**, az **alkalmazás azonosítóját**, valamint az alkalmazás Azure ad-ben történő létrehozásakor mentett *ügyfél titkos kulcs* értékét.
   4. Válassza a **Mentés** lehetőséget. A JAMF Pro teszteli a beállításokat, és ellenőrzi a sikerességet.

   Térjen vissza az Intune-beli **partner** -eszközkezelés lapra a konfiguráció befejezéséhez.

2. Az Intune-ban nyissa meg a **partneri eszközök kezelése** lapot. Az **összekötő beállításai** területen adja meg a hozzárendelési csoportokat:

   - Válassza a **Belefoglalás** lehetőséget, és adja meg, hogy mely felhasználói csoportok számára kívánja használni a MacOS-regisztrációt a JAMF.
   - A **kizárás** használatával válassza ki azokat a felhasználókat, akik nem tudnak regisztrálni a JAMF, hanem közvetlenül az Intune-ban regisztrálják a Mac-et.

   A felülbírálások *kizárása* , ami azt jelenti, hogy a mindkét csoportban lévő összes eszköz ki van zárva a JAMF- *ből, és*az Intune-nal való regisztrálásra van leképezve.

   >[!NOTE]
   > A felhasználói csoportok belefoglalásának és kizárásának módszere befolyásolja a felhasználó regisztrációs élményét. Bármely olyan Mac-felhasználó, amely már regisztrálva van a JAMF vagy az Intune-ban, és a másik MDM való regisztrálásra irányul, meg kell adnia az eszköz regisztrációját, majd újra regisztrálnia kell az új MDM az eszköz megfelelő működésének felügyelete előtt.

3. A **kiértékelés** lehetőség kiválasztásával meghatározhatja, hogy hány eszköz lesz regisztrálva az JAMF-ben a csoport beállításai alapján.

4. Válassza a **Mentés** lehetőséget, ha készen áll a konfiguráció alkalmazására.

5. A folytatáshoz a JAMF-t kell használnia [a Mac-céges portál telepítéséhez](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) , hogy a felhasználók regisztrálni tudják az eszközeiket az Intune-ban.

## <a name="set-up-compliance-policies-and-register-devices"></a>Megfelelőségi szabályzatok beállítása és eszközök regisztrálása

Miután konfigurálta az Intune és a JAMF közötti integrációt, a [JAMF által felügyelt eszközökre vonatkozó megfelelőségi szabályzatokat kell alkalmaznia](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>A JAMF Pro és az Intune leválasztása

Ha már nem használja a JAMF Pro-t a szervezeten belüli Mac-EK felügyeletéhez, és szeretné, hogy a felhasználók az Intune-nal felügyelhetők legyenek, el kell távolítania a kapcsolatot a JAMF Pro és az Intune között. A JAMF Pro konzol használatával távolítsa el a kapcsolatokat.

1. A JAMF Pro-ban lépjen a **globális felügyelet** > **feltételes hozzáférés**elemre. A **MacOS Intune-integráció** lapon válassza a **Szerkesztés**lehetőséget.

2. Törölje az **Intune-integráció engedélyezése MacOS-hez** jelölőnégyzet jelölését.

3. Válassza a **Mentés** lehetőséget. A JAMF Pro elküldi a konfigurációt az Intune-nak, és az integráció leáll.

4. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Válassza a **bérlői felügyelet** > **Összekötők és jogkivonatok** lehetőséget > **partneri eszközök kezelése** lehetőségre, és ellenőrizze, hogy az állapot most **leállt**-e.

   > [!NOTE]
   > A szervezet Mac-eszközei a konzolján látható (3 hónap) időpontban lesznek eltávolítva.

## <a name="next-steps"></a>További lépések

- [Megfelelőségi szabályzatok alkalmazása Jamf által felügyelt eszközökön](conditional-access-assign-jamf.md)
- [A JAMF által küldött adatokat az Intune-nak küldi](data-jamf-sends-to-intune.md)
