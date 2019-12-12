---
title: A Symantec és a Microsoft Intune közötti integráció beállítása
titleSuffix: Microsoft Intune
description: A Symantec Endpoint Protection Mobile beállítása a Microsoft Intune-ban a mobileszközök a vállalati erőforrásokhoz való hozzáférésének kezeléséhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6c28b222307ee20e3198033ef6aa4af3d756e7e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72681323"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>A Symantec Endpoint Protection Mobile és az Intune közötti integráció beállítása

A Symantec Endpoint Protection Mobile (SEP Mobile) és az Intune közötti integráció beállításához kövesse az alábbi lépéseket. Az egyszeri bejelentkezés lehetőségéhez a SEP Mobile-alkalmazásokat hozzá kell adni az Azure AD-hez.

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="before-you-begin"></a>Előkészületek

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Az Intune és a SEP Mobile integrálásához használt Azure AD-fiók

- A SEP Mobile alapvető beállítási folyamatának megkezdése előtt ellenőrizze, hogy megfelelően konfigurálta-e az Azure AD-fiókot a [Symantec Endpoint Protection Mobile Management-konzolon](https://aad.skycure.com).
- Az integráció végrehajtásához az Azure AD-fióknak globális rendszergazdai fióknak kell lennie.
### <a name="network-setup"></a>Hálózati beállítás

Ha meg szeretne győződni róla, hogy a hálózata megfelelően van beállítva a SEP Mobile-integrációhoz, tekintse meg a [hálózati konfiguráció beállításáról szóló](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016) Symantec-cikket.

### <a name="full-integration-vs-read-only"></a>Teljes integráció vagy csak olvasható

A SEP Mobile kétféleképpen integrálható az Intune-nal:

- Az **írásvédett integráció (alapszintű beállítás)** csak kiolvassa az Azure Active Directoryból az eszközöket, és betölti őket a Symantec Endpoint Protection Mobile Management-konzolba.
<br>
  - Ha az **Eszközök állapotának és kockázatának jelentése az Intune-nak** és **A biztonsági incidensek jelentése az Intune-nak** jelölőnégyzetek nincsenek bejelölve a Symantec Endpoint Protection Mobile Management-konzolon, az integráció írásvédett, ezért nem fogja módosítani az eszközök megfelelőségi állapotát az Intune-ban.
<br></br>
- A **teljes integráció** lehetővé teszi, hogy a SEP Mobile jelentse az eszközökkel kapcsolatos kockázatokat és a biztonsági incidensek részleteit az Intune-nak, amely kétirányú kommunikációt alakít ki a két felhőszolgáltatás között.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Hogyan használja az Azure AD és az Intune a SEP Mobile-alkalmazásokat?

- **iOS-es alkalmazás:** A végfelhasználók iOS-es alkalmazással jelentkezhetnek be az Azure AD-ba.

- **Androidos alkalmazás:** A végfelhasználók androidos alkalmazással jelentkezhetnek be az Azure AD-ba.

- **Felügyeleti alkalmazás:** Ez a SEP Mobile több-bérlős Azure AD-alkalmazása, amely lehetővé teszi a szolgáltatásközi kommunikációt az Intune-nal.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Írásvédett integráció beállítása az Intune és a SEP Mobile között

> [!IMPORTANT]
> A SEP Mobile-adminisztrátor hitelesítő adatainak egy olyan e-mail-fiókot kell tartalmaznia, amely egy érvényes felhasználóhoz tartozik az Azure Active Directoryban. Ellenkező esetben nem fog tudni bejelentkezni. A SEP Mobile az Azure Active Directoryval hitelesíti egyszeri bejelentkezéshez (SSO) az adminisztrátort.

1. Nyissa meg a [Symantec Endpoint Protection Mobile Management-konzolt](https://aad.skycure.com).

2. Adja meg a **SEP Mobile rendszergazdai hitelesítő adatait**, és válassza a **Folytatás** lehetőséget.

3. A **Beállítások**lap **Intune-integráció** területén válassza az **Alapszintű beállítás** lehetőséget.

4. A **iOS-alkalmazás** elem mellett válassza a **Hozzáadás az Active Directoryhoz** lehetőséget.

    ![A Symantec Endpoint Protection Mobile Management konzol képe](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

5. Amikor megnyílik a bejelentkezési oldal, adja meg Intune-os hitelesítő adatait, majd válassza az **Elfogadom** lehetőséget.

    ![Kép az iOS-alkalmazás Intune-bejelentkezési képernyőjéről](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

6. Miután hozzáadta az alkalmazást az Azure AD-hoz, megjelenik egy erről szóló értesítés.

    ![Kép az iOS-alkalmazás sikeres hozzáadását jelző képernyőről](./media/skycure-mtd-connector-integration/symantec-portal-basic-added.png)

7. Ismételje meg ezeket a lépéseket a **SEP Mobile Android** és **Management** alkalmazásokhoz.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Azure AD-biztonsági csoport hozzáadása a SEP Mobile-hoz

Hozzá kell adnia egy olyan biztonsági csoportot, amelynek tagja az összes SEP Mobile-t futtató eszköz.

- Adja meg és jelölje ki az összes SEP Mobile-t futtató eszközöket tartalmazó biztonsági csoportot, majd mentse a módosításokat.

    ![Kép a SEP Mobile felhasználói csoportjairól](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

A SEP Mobile a Mobile Threat Defense szolgáltatást futtató eszközöket az Azure AD biztonsági csoportjaival szinkronizálja.

![Biztonsági csoport konfigurációjának képe a SEP Mobile Management konzolon](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Teljes integráció beállítása az Intune és a SEP Mobile között

### <a name="retrieve-the-directory-id-in-azure-ad"></a>A címtár-azonosító lekérése az Azure AD-ből

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).

2. Írja be az „Active Directory” kifejezést a keresőmezőbe, majd válassza az **Azure Active Directory** lehetőséget.

3. Válassza a **Tulajdonságok** lehetőséget.

4. A **címtár-azonosító** mellett válassza a másolás ikont, majd illessze be az azonosítót egy biztonságos helyre. Erre egy későbbi lépésben szüksége lesz.

    ![Kép a címtár-azonosítóról az Azure Portalon](./media/skycure-mtd-connector-integration/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Választható) Hozzon létre egy dedikált biztonsági csoportot azon eszközök számára, amelyek SEP Mobile-alkalmazásokat szeretnének futtatni
1. Az [Azure Portal](https://portal.azure.com) **Kezelés** területén válassza a **Felhasználók és csoportok**, majd a **Minden csoport** lehetőséget.

2. Kattintson a **Hozzáadás** gombra. Írjon be egy **csoportnevet**. A **Tagság típusa** területen válassza a **Hozzárendelt** lehetőséget.

3. A **Tagok** panelen jelölje ki a csoport tagjait, majd kattintson a **Kiválasztás** gombra.

4. A **Csoport** panelen válassza a **Létrehozás** lehetőséget.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>A Symantec Endpoint Protection Mobile és az Intune közötti integráció beállítása

1. Nyissa meg a [Symantec Endpoint Protection Mobile Management-konzolt](https://aad.skycure.com).

2. Adja meg a **SEP Mobile rendszergazdai hitelesítő adatait**, és válassza a **Folytatás** lehetőséget.

3. Lépjen a **Beállítások** > **Integrációk** > **Intune** > **EMM-integráció kiválasztása** szakaszra.

4. A **címtár-azonosító** mezőbe illessze be az előző szakaszban az Azure Active Directoryból kimásolt címtár-azonosítót, majd mentse a beállításokat.

    ![Kép a címtár-azonosítóról a SEP Mobile portálon](./media/skycure-mtd-connector-integration/symantec-portal-directory-ID.png)

5. Lépjen a **Beállítások** > **Integrációk** > **Intune** > **Alapszintű beállítás** szakaszra.

6. A **iOS-alkalmazás** elem mellett válassza a **Hozzáadás az Active Directoryhoz** lehetőséget.

    ![Kép az iOS-alkalmazás az Active Directoryhoz való hozzáadásáról](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

7. Jelentkezzen be a címtárat kezelő Office 365-fiók Azure Active Directory-hitelesítő adataival.

8. Válassza az **Elfogadás** gombot a SEP Mobile iOS-alkalmazás az Azure Active Directoryhoz való hozzáadásához.

    ![Kép az Elfogadás gombról](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

9. Végezze el ugyanezt az eljárást az **Androidos alkalmazással** és a **Felügyeleti alkalmazással** is.

10. Válassza ki az összes olyan felhasználói csoportot, amely SEP Mobile-alkalmazásokat szeretne futtatni, például a korábban létrehozott biztonsági csoportot.

    ![Kép a SEP Mobile felhasználói csoportjairól](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

11. A SEP Mobile szinkronizálja a kijelölt csoportok eszközeit, és megkezdi az adatok jelentését az Intune felé. Ezeket az adatokat a Teljes integráció szakaszban tekintheti meg. Lépjen a **Beállítások** > **Integrációk** > **Intune** > **Teljes integráció** szakaszra.

     ![Kép a teljes SEP Mobile-integráció befejezéséről](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>További lépések

[SEP Mobile-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
