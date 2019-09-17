---
title: A Jamf Pro integrálása a Microsoft Intune-nal a megfelelőség érdekében
titleSuffix: Microsoft Intune
description: A JAMF által felügyelt eszközök biztonságossá tételéhez használja a Microsoft Intune megfelelőségi szabályzatokat Azure Active Directory feltételes hozzáféréssel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012512"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>A Jamf Pro integrálása az Intune-nal a megfelelőség érdekében

Érintett kiadások: Intune az Azure Portalon

Ha a szervezete a [JAMF Pro](https://www.jamf.com) -t használja a végfelhasználói Mac gépek felügyeletéhez, Microsoft Intune megfelelőségi szabályzatokat Azure Active Directory feltételes hozzáféréssel, hogy biztosítsa, hogy a szervezetben lévő eszközök megfeleljenek.

## <a name="prerequisites"></a>Előfeltételek

A JAMF Pro-val való feltételes hozzáférés konfigurálásához a következőkre van szükség:

- A Jamf Pro 10.1.0-ás vagy későbbi verziója
- [macOS-hez készült Céges portál alkalmazás](https://aka.ms/macoscompanyportal)
- OS X 10.11-es vagy későbbi Yosemite verzióval rendelkező macOS-alapú eszközök

## <a name="connect-intune-to-jamf-pro"></a>Az Intune és a JAMF Pro összekötése

Az Intune és a JAMF Pro összekötése:

1. Hozzon létre egy új alkalmazást az Azure-ban.
2. A JAMF Pro-val való integráció engedélyezése az Intune-nal.
3. Feltételes hozzáférés konfigurálása a JAMF Pro-ban.

## <a name="create-an-application-in-azure-active-directory"></a>Alkalmazás létrehozása Azure Active Directory

1. A [Azure Portal](https://portal.azure.com)válassza a **Azure Active Directory** > **alkalmazás-regisztrációk**, majd az **új regisztráció**lehetőséget. 

2. Az **alkalmazás regisztrálása** lapon a következő részleteket kell megadnia:
   - A **név** szakaszban adjon meg egy értelmes alkalmazásnév nevet, például **JAMF feltételes hozzáférés**.
   - A **támogatott fióktípus** szakaszban válassza a fiókok lehetőséget **bármely szervezeti címtárban**. 
   - Az **átirányítási URI**esetében hagyja meg az alapértelmezett webes beállítást, majd adja meg a JAMF Pro-példány URL-címét.  

3. Válassza a **regisztráció** lehetőséget az alkalmazás létrehozásához és az új alkalmazás **Áttekintés** lapjának megnyitásához.  

4. Az alkalmazás **áttekintése** lapon másolja az **alkalmazás (ügyfél) azonosító** értékét, és jegyezze fel későbbi használatra. Ezt az értéket későbbi eljárásokban kell megadnia.  

5. Válassza a **tanúsítványok & a titkok** elemet a **kezelés**alatt. Válassza az **új ügyfél titka** gombot. Adjon meg egy értéket a **Leírás**mezőben, válassza a **lejárat** lehetőséget, majd válassza a **Hozzáadás**elemet.

   > [!IMPORTANT]  
   > Mielőtt elhagyja ezt a lapot, másolja ki az ügyfél titkos kulcsának értékét, és jegyezze fel későbbi használatra. Erre az értékre szüksége lesz a későbbi eljárásokban. Ez az érték nem érhető el újra az alkalmazás regisztrációjának újbóli létrehozása nélkül.  

6. Válassza az **API-engedélyek** elemet a **kezelés**alatt. Válassza ki a meglévő engedélyeket, majd válassza az **engedély eltávolítása** lehetőséget az engedélyek törléséhez. Az összes meglévő engedély eltávolítására akkor van szükség, amikor új engedélyt ad hozzá, és az alkalmazás csak akkor működik, ha az egyetlen szükséges engedéllyel rendelkezik.  

7. Új engedély hozzárendeléséhez válassza az **engedély hozzáadása**lehetőséget. Az **API-engedélyek kérése** lapon válassza az **Intune**lehetőséget, majd válassza az **alkalmazás engedélyei**lehetőséget. Jelölje be a csak a **update_device_attributes**jelölőnégyzetet.  

   Válassza a **Hozzáadás engedély** lehetőséget a konfiguráció mentéséhez.  

8. Az **API-engedélyek** lapon válassza a **rendszergazdai jóváhagyás megadása a Microsoft számára**lehetőséget, majd válassza az **Igen**lehetőséget.  

   Befejeződött az alkalmazás regisztrációs folyamata az Azure AD-ben.


    > [!NOTE]
    > Ha az ügyfél titkos kulcsa lejár, létre kell hoznia egy új ügyfél-titkos kulcsot az Azure-ban, majd frissítenie kell a feltételes hozzáférési adatot a JAMF Pro-ban. Az Azure lehetővé teszi, hogy a régi titok és az új kulcs aktív legyen a szolgáltatás megszakadásának megelőzése érdekében.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Az Intune engedélyezése a Jamf Pro-val történő integrációra

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, és lépjen **Microsoft Intune** > **eszköz megfelelőségi** > **partnere eszközének felügyeletéhez**.

2. Engedélyezze a megfelelőségi összekötőt a JAMF az előző eljárás során mentett alkalmazás-azonosító beillesztésével az **Jamf Azure Active Directory alkalmazás-azonosító** mezőjébe.

3. Kattintson a **Mentés** gombra.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>A Microsoft Intune-integráció konfigurálása a Jamf Pro szolgáltatásban

1. A Jamf Pro oldalán nyissa meg a **Globális felügyelet** > **Feltételes hozzáférés** lehetőséget. Kattintson a **Szerkesztés** gombra a **MacOS Intune-integráció** lapon.

2. Jelölje be az Intune- **integráció engedélyezése MacOS-hez**jelölőnégyzetet.

3. Adja meg az Azure-bérlőre vonatkozó szükséges információkat, beleértve a **helyet**, a **tartománynevet**, az **alkalmazás azonosítóját**, valamint az alkalmazás Azure ad-ben történő létrehozásakor mentett *ügyfél titkos kulcs* értékét.  

4. Kattintson a **Mentés** gombra. A JAMF Pro teszteli a beállításokat, és ellenőrzi a sikerességet.

## <a name="set-up-compliance-policies-and-register-devices"></a>Megfelelőségi szabályzatok beállítása és eszközök regisztrálása

Miután konfigurálta az Intune és a JAMF közötti integrációt, a [JAMF által felügyelt eszközökre vonatkozó megfelelőségi szabályzatokat kell alkalmaznia](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>A JAMF Pro és az Intune leválasztása 

Ha már nem használja a JAMF Pro-t a szervezeten belüli Mac-EK felügyeletéhez, és szeretné, hogy a felhasználók az Intune-nal felügyelhetők legyenek, el kell távolítania a kapcsolatot a JAMF Pro és az Intune között. A JAMF Pro konzol használatával távolítsa el a kapcsolatokat. 

1. A JAMF Pro-ban lépjen a **globális felügyelet** > **feltételes hozzáférés**elemre. A **MacOS Intune-integráció** lapon válassza a **Szerkesztés**lehetőséget.
2. Törölje az **Intune-integráció engedélyezése MacOS-hez** jelölőnégyzet jelölését.
3. Kattintson a **Mentés** gombra. A JAMF Pro elküldi a konfigurációt az Intune-nak, és az integráció leáll.
4. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba. Lépjen a **Microsoft Intune** > **eszköz megfelelőségi** > **partnere eszközének felügyeletéhez** , és ellenőrizze, hogy az állapot most **megszakadt**-e. 

   > [!NOTE]
   > A szervezet Mac-eszközei a konzolján látható (3 hónap) időpontban lesznek eltávolítva. 

## <a name="next-steps"></a>További lépések

- [Megfelelőségi szabályzatok alkalmazása Jamf által felügyelt eszközökön](conditional-access-assign-jamf.md)
- [A JAMF által küldött adatokat az Intune-nak küldi](data-jamf-sends-to-intune.md)
