---
title: Regisztrációs korlátozások beállítása a Microsoft Intune-ban
titleSuffix: ''
description: Regisztráció korlátozása platform alapján és eszközregisztrálási korlát beállítása az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9215dc0d814b4269c239595183e024ebb073455
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/31/2019
ms.locfileid: "71302125"
---
# <a name="set-enrollment-restrictions"></a>Regisztrációs korlátozások beállítása

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune-rendszergazdaként létrehozhat és kezelhet olyan regisztrációs korlátozásokat, amelyek meghatározzák, hogy mely eszközök regisztrálhatók a felügyeletbe az Intune-nal, beleértve a következőket:
- eszközök száma
- az operációs rendszerek és verziók több korlátozást is létrehozhatnak, és különböző felhasználói csoportokra alkalmazhatják őket. Az egyes korlátozásokhoz [prioritássorrendet](#change-enrollment-restriction-priority) állíthat be.

>[!NOTE]
>A regisztrációs korlátozások nem biztonsági funkciók. A feltört eszközök más tulajdonságokat állíthatnak magukról. Ezek a korlátozások a nem rosszindulatú felhasználók esetén jelentenek észszerű erőfeszítést igénylő akadályt.

Többek között az alábbi regisztrációs korlátozásokat hozhatja létre:

- Regisztrált eszközök maximális száma.
- Regisztrációra alkalmas eszközplatformok:
  - Android-eszköz rendszergazdája
  - Androidos vállalati munkahelyi profil
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Platform operációsrendszer-verziója iOS, Android rendszerű eszköz rendszergazdája, Android Enterprise Work profil, Windows és Windows Mobile rendszerű eszközökhöz. (Csak a Windows 10-es verziók használhatók. Hagyja üresen, ha a Windows 8.1 engedélyezett.)
  - Minimális verzió.
  - Maximális verzió.
- Személyes tulajdonú eszközök korlátozása (iOS, Android rendszerű eszköz rendszergazdája, Android Enterprise Work profil, macOS, Windows és Windows Mobile).

## <a name="default-restrictions"></a>Alapértelmezett korlátozások

A rendszer tartalmaz alapértelmezett korlátozásokat mind az eszköztípusra, mind az eszközszámra vonatkozóan. Módosíthatja az alapértelmezések beállításait. Az alapértelmezett korlátozások minden felhasználós és felhasználó nélküli regisztrációra vonatkoznak. Felülbírálhatja ezeket az alapértelmezéseket új, magasabb prioritású korlátozások létrehozásával.

## <a name="create-a-device-type-restriction"></a>Eszköz típusú korlátozás létrehozása

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások** lehetőséget, írja be az **Intune** keresési kifejezést, majd válassza az **Intune** lehetőséget.
3. Válassza az **eszközök** > beléptetése**regisztrációs korlátozásokat** > **korlátozó** > **eszköz típusának**korlátozásának létrehozása lehetőséget.
    ![Eszköz típusú korlátozás létrehozásához használható képernyő-sapka](media/enrollment-restrictions-set/create-device-type-restriction.png)
4. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
5. A **tovább** gombra kattintva nyissa meg a **platform beállításai** lapot.
6. A **platform**területen válassza az **Engedélyezés** lehetőséget azokhoz a platformokhoz, amelyekre engedélyezni szeretné ezt a korlátozást.
    ![Képernyő-sapka a platform beállításainak kiválasztásához](media/enrollment-restrictions-set/choose-platform-settings.png)
7. A **verziók**területen válassza ki azokat a minimális és maximális verziókat, amelyeknek az engedélyezett platformokat támogatni szeretné. A verzióra vonatkozó korlátozások csak a Céges portál regisztrált eszközökre vonatkoznak.
     Támogatott verzióformátumok többek között az alábbiak:
    - Az Android-eszköz rendszergazdája és az Android Enterprise munkahelyi profil támogatja a főverzió. alverzió. Rev. Build használatát.
    - Az iOS a főverzió.alverzió.változat formátumot támogatja. Az operációs rendszer verziójának korlátozásai nem vonatkoznak a Készülékregisztrációs programban, az Apple School Manager programban vagy az Apple Configurator alkalmazással regisztrált Apple-eszközökre.
    - A Windows a főverzió.alverzió.változat.build formátumot támogatja, csak Windows 10 esetén.
    > [!Note]
    > A Windows 10 nem adja meg a Build számát a regisztráció során, így például ha a 10.0.17134.100-ben belép, és az eszköz 10.0.17134.174, a rendszer letiltja a regisztráció során.

8. A **személyes tulajdonú**területen válassza az **Engedélyezés lehetőséget** a saját tulajdonú eszközökként engedélyezni kívánt platformok számára.
9. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
10. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra lesz érvényes, amelyekhez hozzárendelte azt. Ha egy korlátozást egyetlen csoporthoz sem rendel hozzá, akkor az adott korlátozásnak semmilyen hatása nem lesz. Válassza a **Kiválasztás** elemet. 
    ![Képernyő-sapka a platform beállításainak kiválasztásához](media/enrollment-restrictions-set/select-groups.png)
11. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
12. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
13. Az új korlátozások az alapértelmezett korlátozásnál eggyel magasabb prioritással jönnek létre. Igény esetén [módosíthatja a prioritást](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Eszköz korlátozási korlátozásának létrehozása

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások** lehetőséget, írja be az **Intune** keresési kifejezést, majd válassza az **Intune** lehetőséget.
3. Válassza az **eszközök** > beléptetése**regisztrációjának korlátozásai** > korlátozási**eszköz**korlátozásának**létrehozása** > lehetőséget.
    ![Az eszközök korlátozására vonatkozó korlátozás létrehozásához használható képernyő sapka](media/enrollment-restrictions-set/create-device-limit-restriction.png)
4. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
5. A **tovább** gombra kattintva nyissa meg az **eszköz korlátozása** lapot.
6. Az eszközök **korlátja**beállításnál válassza ki a felhasználó által regisztrálható eszközök maximális számát.
    ![Az eszköz korlátjának kiválasztására szolgáló képernyő sapka](media/enrollment-restrictions-set/choose-device-limit.png)
7. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
8. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra lesz érvényes, amelyekhez hozzárendelte azt. Ha egy korlátozást egyetlen csoporthoz sem rendel hozzá, akkor az adott korlátozásnak semmilyen hatása nem lesz. Válassza a **Kiválasztás** elemet. 
    ![A csoportok kiválasztására szolgáló képernyő-sapka](media/enrollment-restrictions-set/select-groups-device-limit.png)
11. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
12. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
13. Az új korlátozások az alapértelmezett korlátozásnál eggyel magasabb prioritással jönnek létre. Igény esetén [módosíthatja a prioritást](#change-enrollment-restriction-priority).

BYOD regisztrációk során a felhasználóknak megjelenik egy értesítés, értesíti, ha a regisztrált eszközök maximális számát. IOS rendszeren például:

![Az iOS-eszközön megjelenő limitértesítés](./media/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Az eszközök korlátozására vonatkozó korlátozások nem vonatkoznak a következő Windows-beléptetési típusokra:
> - Közösen felügyelt regisztrációk
> - GPO-regisztrációk
> - Azure Active Directory csatlakoztatott regisztrációk
> - Összekapcsolt regisztrációk tömeges Azure Active Directory
> - Autopilot-regisztrációk
> - Eszközök tanúsítványigénylési kezelőjének regisztrációja
>
> A rendszer nem kényszeríti ki az eszközre vonatkozó korlátozásokat a beléptetési típusok esetében, mert azok megosztott eszközök.
> A beléptetési típusokra vonatkozó rögzített korlátokat [a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings)állíthatja be.


## <a name="change-enrollment-restrictions"></a>Regisztrációs korlátozások módosítása

A regisztrációs korlátozás beállításait az alábbi lépésekkel módosíthatja. Ezek a korlátozások nem érintik azokat az eszközöket, amelyek már regisztrálva vannak. Ez a funkció nem alkalmas az [Intune PC-ügynök](manage-windows-pcs-with-microsoft-intune.md) használatával regisztrált eszközök letiltásához.

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások** lehetőséget, írja be az **Intune** keresési kifejezést, majd válassza az **Intune** lehetőséget.
3. Válassza az **eszközök** > regisztrálása**regisztrációs korlátozások** lehetőséget > Válassza ki azt a korlátozást, amelyet módosítani szeretne > **tulajdonságainál**.
4. Válassza a **Szerkesztés** lehetőséget a módosítani kívánt beállítások mellett.
5. A **Szerkesztés** lapon végezze el a kívánt módosításokat, és folytassa a **felülvizsgálat + mentés** lapra, majd válassza a **Mentés**lehetőséget.


## <a name="blocking-personal-android-devices"></a>Személyes Android-eszközök letiltása
- Ha letiltja a személyes tulajdonú Android-eszközök regisztrációját, a személyes tulajdonú Android Enterprise Work profiling-eszközök továbbra is regisztrálhatnak.
- Alapértelmezés szerint az androidos vállalati munkahelyi profil eszközeinek beállításai megegyeznek az Android-eszközök rendszergazdai eszközeinek beállításaival. Miután módosította az androidos vállalati munkahelyi profilt vagy az Android-eszköz rendszergazdai beállításait, már nem ez a helyzet.
- Ha letiltja a személyes Android vállalati munkahelyi profil regisztrálását, csak a vállalat által birtokolt Android-eszközök regisztrálhatók androidos vállalati munkahelyi profilokkal.

## <a name="blocking-personal-windows-devices"></a>Személyes Windows-eszközök letiltása
Ha letiltja a személyes tulajdonban lévő windowsos eszközök regisztrációját, az Intune ellenőrzi, hogy minden új Windows-regisztrációs kérelem vállalati regisztrációként lett-e engedélyezve. A jogosulatlan regisztrációk le lesznek tiltva.

Windows vállalati regisztrációnak minősülnek az alábbi módszerek:
- A felhasználó [készülékregisztráció-kezelői fiókot]( device-enrollment-manager-enroll.md) használ a regisztráláshoz.
- Az eszközregisztráció a [Windows Autopilot](enrollment-autopilot.md) használatával történik.
- Az eszköz regisztrálva van a Windows Autopilot szolgáltatásban, de a Windows beállításai nem csak MDM-regisztrációt igényelnek.
- Az eszköz IMEI-száma szerepel az **Eszközregisztráció** >  **[Vállalati eszközazonosítók](corporate-identifiers-add.md)** listán. (Windows Phone 8.1-hez nem támogatott)
- Az eszközregisztráció [tömeges kiépítési csomagban](windows-bulk-enroll.md) történik.
- Az eszköz regisztrál a csoportházirend-objektumon keresztül, vagy [automatikus regisztrációt a SCCM-ből a közös felügyelethez](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
A következő regisztrációk az Intune-ban vállalatiként vannak megjelölve. De mivel nem biztosítanak az Intune-rendszergazda eszközönkénti felügyeletet, a rendszer letiltja a következőket:
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [Azure Active Directory-csatlakozás a Windows beállítása során](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [Azure Active Directory-csatlakozás a Windows beállításaiból](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Az alábbi személyes regisztrációs módszerek is le lesznek tiltva:
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [munkahelyi fiók hozzáadása a Windows-beállításokból](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- [Csak MDM-regisztráció]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) lehetősége a Windows-beállításokból.

\* Ha az AutoPilottal regisztrált, ezek nincsenek letiltva.


## <a name="change-enrollment-restriction-priority"></a>A regisztrációs korlátozások prioritásának módosítása

A prioritást akkor használja a rendszer, ha egy felhasználó több olyan csoportnak is a tagja, amelyhez korlátozások vannak hozzárendelve. A felhasználókra a rendszer egyedül a vonatkozó csoportok legmagasabb prioritású korlátozását alkalmazza. Tegyük fel például, hogy Attila tagja az A csoportnak, melyhez egy 5-ös prioritású korlátozás van hozzárendelve, illetve tagja a B csoportnak is, melyhez egy 2-es prioritású korlátozás van hozzárendelve. Ez esetben Attilára csak a 2-es prioritású korlátozást alkalmazza a rendszer.

Az Ön által létrehozott korlátozások az alapértelmezettnél eggyel magasabb prioritást kapnak.

Az eszközregisztráció tartalmaz alapértelmezett korlátozásokat mind az eszköztípusra, mind az eszközszámra vonatkozóan. Ez a két korlátozás az összes felhasználóra érvényes, hacsak felül nem bírálják őket magasabb prioritású korlátozások.

Az összes egyéni korlátozás prioritását módosíthatja.

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások** lehetőséget, írja be az **Intune** keresési kifejezést, majd válassza az **Intune** lehetőséget.
3. Válassza az **Eszközök regisztrálása** > **Regisztrációs korlátozások** lehetőséget.
4. Vigye az egérmutatót a korlátozás fölé a prioritáslistában.
5. A három függőleges pontot alkotó ikon használatával húzza a prioritást a lista megfelelő helyére.
