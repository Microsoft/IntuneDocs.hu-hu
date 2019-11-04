---
title: Felhasználók hozzáadása és engedélyek megadása
titleSuffix: Microsoft Intune
description: A helyszíni felhasználók szinkronizálása az Azure AD-vel és rendszergazdai jogosultság megadása az Intune-előfizetéshez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5b469c759ac34a6d8de09163534a580346e48a1
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415028"
---
# <a name="add-users-and-grant-administrative-permission-to-intune"></a>Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz

A rendszergazdák jogosultak közvetlenül felvenni az új felhasználókat, vagy szinkronizálni a felhasználókat a helyszíni Active Directoryból. Ha felvették a felhasználókat a szolgáltatásba, regisztrálhatják az eszközeiket, és elérhetik a vállalati erőforrásokat. További jogosultságokat is adhat a felhasználóknak, többek között *globális rendszergazdai* és *szolgáltatásadminisztrátori* engedélyeket.

## <a name="add-users-to-intune"></a>Felhasználók hozzáadása az Intune-hoz

Az Intune-előfizetéshez manuálisan is hozzáadhat felhasználókat a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com) vagy a [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). A rendszergazda módosíthatja a felhasználói fiókokat az Intune-licencek hozzárendeléséhez. A licenceket a Microsoft 365 felügyeleti központban vagy az Intune-Azure Portal is hozzárendelheti. A Microsoft 365 felügyeleti központ használatával kapcsolatos további információkért lásd: [felhasználók hozzáadása egyénileg vagy tömegesen a Microsoft 365 felügyeleti központban](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-microsoft-365-admin-center"></a>Intune-felhasználók hozzáadása a Microsoft 365 felügyeleti központban

1. Jelentkezzen be [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) globális rendszergazdai vagy felhasználói felügyeleti rendszergazdai fiókkal.
2. Az Office 365 menüjében válassza a **Rendszergazda** elemet.
3. A Felügyeleti központban válassza a **Felhasználó hozzáadása** elemet.

   ![Képernyőkép a Felhasználó hozzáadása szakaszról](./media/users-add/office-add-user.png)

4. Adja meg a következő felhasználói adatokat:
   - **Utónév**
   - **Vezetéknév**
   - **Megjelenítendő név**
   - **Felhasználói név** – A szolgáltatás eléréséhez használt és az Azure Active Directoryban tárolt egyszerű felhasználónév (UPN)
   - **Hely**
   - **Kapcsolattartási adatok** (nem kötelező)
   - **Jelszó** –automatikus létrehozás vagy adja meg

     ![Képernyőkép az új felhasználó szakaszról](./media/users-add/office-add-user-details.png)

5. Rendeljen hozzá egy Intune-licencet. Válassza a **Terméklicencek** lehetőséget, és válassza ki a terméklicencet. Szükség van egy Intune-ra is vonatkozó licencre.
6. Válassza a **Hozzáadás** gombot az új felhasználó létrehozásához.

### <a name="add-intune-users-in-the-azure-portal"></a>Intune-felhasználók felvétele az Azure Portalon

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **Felhasználók** > **Minden felhasználó** lehetőséget.
3. A Felügyeleti központban válassza az **Új felhasználó** elemet.
   ![Képernyőkép az Új felhasználó hozzáadása elemről](./media/users-add/intune-add-user.png)
4. Adja meg a következő felhasználói adatokat:
   - **Név**
   - **Felhasználónév** – Az új név az Azure Active Directory portálon ![Képernyőkép a név és a felhasználónév hozzáadásáról](./media/users-add/intune-add-user-info.png) Válassza az **OK** gombot a folytatáshoz.
5. Szükség esetén a következő felhasználói tulajdonságokat is megadhatja:
   - **Profil** – Munkahelyi adatok, többek között a **Beosztás megnevezése** és a **Részleg**
   - **Csoportok** – Válasszon a felhasználó által felehető csoportokat
   - **Címtár szerepkör** – Rendszergazdai jogosultságok adása a felhasználónak (többek között szolgáltatásadminisztrátor szerepkör az Intune-hoz).

   Az új felhasználó Intune-hoz adásához válassza a **Létrehozás** gombot.
6. Válassza a **Profil** lehetőséget, majd válasszon egy **Felhasználási helyet** az új felhasználónak. A felhasználási hely megadása szükséges, mielőtt az új felhasználóhoz hozzárendelhetne egy Intune-licencet. A folytatáshoz válassza a **Mentés** gombot.
    ![A felhasználási hely képernyőképe](./media/users-add/intune-add-user-loc.png)
7. Intune-licenc felhasználóhoz rendeléséhez válassza a **Licencek** lehetőséget, majd a **Hozzárendelés** elemet. Az eszközök regisztrálásához és a vállalati erőforrások eléréséhez Intune-licenc szükséges. Válassza a **Termékek** lehetőséget, válassza ki a licenctípust, aztán a **Kiválasztás** lehetőséget, majd a **Hozzárendelés** elemet.

## <a name="grant-admin-permissions"></a>Rendszergazdai jogosultságok megadása

Javasoljuk, hogy a felhasználók Intune-előfizetéshez történő hozzáadása után biztosítson néhány felhasználó számára rendszergazdai engedélyt.  Rendszergazdai jogosultságokat az alábbi lépéseket követve adhat:

### <a name="give-admin-permissions-in-office-365"></a>Rendszergazdai jogosultságok biztosítása az Office 365-ben

1. Jelentkezzen be a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) globális rendszergazdai fiókkal.
2. Az Office 365 menüjében válassza a **Rendszergazda** elemet.
3. A Felügyeleti központban válassza az **Aktív felhasználók** lehetőséget, majd válassza ki azt a felhasználót, akinek rendszergazdai jogosultságot szeretne adni.

4. A **Szerepkörök** oszlopban válassza a **Szerkesztés** lehetőséget.

    ![Képernyőkép a Rendszergazdai felhasználóról](./media/users-add/office-assign-roles-open.png)

5. Az elérhető szerepkörök listájából válassza ki a hozzárendelni kívánt rendszergazdai jogosultságot.
![Képernyőkép a szerepkörök hozzárendeléséről](./media/users-add/office-assign-roles.png)
6. Válassza a **Mentés** elemet.

### <a name="give-admin-permissions-in-the-azure-portal"></a>Rendszergazdai jogosultságok megadása az Azure Portalon

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com) egy globális rendszergazdai fiókkal.
2. Az Azure Portalon válassza a **Felhasználó** lehetőséget, majd válassza ki azt a felhasználót, akinek rendszergazdai jogosultságot szeretne adni.
3. Válassza a **Címtárbeli szerepkör** elemet, majd pedig a kívánt jogosultságot.
  ![Képernyőkép a Címtárszerepkörről](./media/users-add/add-intune-directory-role.png)
4. Válassza a **Mentés** elemet.

### <a name="types-of-administrators"></a>Rendszergazdatípusok

Rendeljen hozzá egy vagy több rendszergazdai jogosultságot a felhasználókhoz. Ezek az engedélyek definiálják a felügyeleti hatókört a felhasználók és az általuk kezelhető feladatokra vonatkozóan. A Microsoft különböző felhőszolgáltatásai ugyanazokat a rendszergazdai jogosultságokat használják, azonban előfordulhat, hogy egyes szolgáltatások nem támogatnak bizonyos jogosultságokat. A Azure Portal és a Microsoft 365 felügyeleti központ is korlátozott rendszergazdai szerepköröket listáz, amelyeket nem az Intune használ. Az Intune-beli rendszergazdai jogosultságok az alábbiak lehetnek:

- **Globális rendszergazda** – (Office 365 és Intune) Az Intune összes rendszergazdai funkciójához hozzáfér. Alapértelmezés szerint az Intune-ra feliratkozik személy globális rendszergazda lesz. A globális rendszergazdák az egyetlen rendszergazda, akik más rendszergazdai szerepköröket rendelhetnek hozzá. A szervezetben egynél több globális rendszergazda is működhet. Javasoljuk, hogy a kockázat minimalizálása érdekében ne adja meg túl sok személynek ezt a szerepkört.
- **Jelszókezelő** – (Office 365 és Intune) Átállítja a jelszavakat, kezeli a szolgáltatáskéréseket, illetve figyeli a szolgáltatás állapotát. A jelszókezelők kizárólag a felhasználók jelszavának átállítására jogosultak.
- **Szolgáltatásadminisztrátor** – (Office 365 és Intune) Benyújtja a támogatási kéréseket a Microsoftnak, és jogosult megtekinteni a szolgáltatás irányítópultját és üzenetközpontját. Ezekhez kizárólag „csak olvasási” hozzáféréssel rendelkeznek, csak a támogatási jegyeket nyithatják meg és olvashatják el.
- **Számlázási adminisztrátor** – (Office 365 és Intune) Lebonyolítja a vásárlásokat, kezeli az előfizetéseket és a támogatási jegyeket, valamint figyeli a szolgáltatás állapotát.
- **Felhasználókezelő rendszergazda** – (Office 365 és Intune) Visszaállítja a jelszavakat, figyeli a szolgáltatás állapotát, hozzáadja és törli a felhasználói fiókokat, valamint kezeli a szolgáltatáskéréseket. A felhasználókezelő rendszergazda nem törölheti a globális rendszergazdákat, nem hozhat létre más rendszergazdai szerepköröket, és nem állíthatja át más rendszergazdák jelszavát.
- **Intune-szolgáltatásadminisztrátor** – A **címtárbeli szerepkör** biztosítására vonatkozó jogosultságot kivéve az Intune-beli globális rendszergazdai jogosultságok mindegyikével rendelkezik.

A Microsoft Intune-előfizetés létrehozásához használt fiók globális rendszergazdai fiók. A napi felügyeleti feladatok elvégzéséhez nem ajánlott globális rendszergazdai jogosultságokat használni. Noha a rendszergazda licenc nélkül is elérheti az Intune-t az Azure Portalon, bizonyos felügyeleti feladatokat, például az Exchange szolgáltatás összekötőjének beállítását csak Intune-licenc birtokában végezhet el.

A Microsoft 365 felügyeleti központhoz való hozzáféréshez a fióknak **engedélyezett bejelentkezési** készlettel kell rendelkeznie. Az Azure Portalon a **Profil** szakaszban a **Nem** értékre állítsa a **Bejelentkezés blokkolása** beállítást. Ez az állapot nem ugyanaz, mint amikor a fióknak licence van az előfizetéshez. Alapértelmezés szerint az összes felhasználói fiók **Engedélyezett** állapotú. A rendszergazdai jogosultságokkal nem rendelkező felhasználók az Intune-jelszavak alaphelyzetbe állításához a Microsoft 365 felügyeleti központot használhatják.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz

A címtár-szinkronizálás konfigurálásával importálhatja a helyi Active Directoryban lévő felhasználói fiókokat a Microsoft Azure Active Directory (Azure AD) szolgáltatásba (ide tartoznak az Intune-felhasználók is). A helyi Active Directory szolgáltatás Azure Active Directory-alapú szolgáltatásokkal való összekapcsolásával jóval egyszerűbbé válik az identitásfelügyelet. Az egyszeri bejelentkezési funkciók konfigurálásával ismerőssé és könnyebbé teheti a felhasználók számára a hitelesítést. Ha egy [Azure AD-bérlőt](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) egyszerre több szolgáltatáshoz is társít, a korábban már szinkronizált felhasználói fiókok is elérhetővé válnak az összes felhőalapú szolgáltatásban.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Helyi felhasználók szinkronizálása az Azure AD szolgáltatással

A felhasználói fiókoknak az Azure AD-val való szinkronizálásához kizárólag az [Azure AD Connect varázslóra](https://www.microsoft.com/download/details.aspx?id=47594) van szüksége. Az Azure AD Connect varázsló egyszerűsített és irányított kezelőfelülettel segíti a helyszíni identitási infrastruktúrának a felhőhöz történő csatlakoztatását. Válassza ki a topológiát és a vonatkozó igényeket (egyetlen vagy több címtár, jelszókivonatok szinkronizálása, átmenő hitelesítés vagy összevonás). A varázsló telepíti és konfigurálja a kapcsolat működéséhez szükséges az összes összetevőt. Ilyen összetevők többek között: a szinkronizálási szolgáltatások, az Active Directory összevonási szolgáltatások (AD FS) és az Azure AD PowerShell modul.

> [!TIP]
> A Azure AD Connect olyan funkciókat foglal magában, amelyek korábban a következőképpen lettek feloldva: Azure AD-szinkronizáló. További információ a [címtár-integrációról](https://technet.microsoft.com/library/jj573653.aspx). További tudnivalók a helyi címtárban lévő felhasználói fiókok Azure AD-vel való szinkronizálásáról: [Similarities between Active Directory and Azure AD](https://technet.microsoft.com/library/dn518177.aspx) (Az Active Directory és az Azure AD közötti hasonlóságok).
