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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1263df126b371780b3c5c14ae619f0cb7c83d475
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415305"
---
# <a name="set-enrollment-restrictions"></a>Regisztrációs korlátozások beállítása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune-rendszergazdaként létrehozhat és kezelhet olyan regisztrációs korlátozásokat, amelyek meghatározzák, hogy mely eszközök regisztrálhatók a felügyeletbe az Intune-nal, beleértve a következőket:
- Az eszközök száma.
- Operációs rendszerek és verziók.

Több korlátozást is létrehozhat, melyeket alkalmazhat különféle felhasználói csoportokra. Az egyes korlátozásokhoz [prioritássorrendet](#change-enrollment-restriction-priority) állíthat be.

>[!NOTE]
>A regisztrációs korlátozások nem biztonsági funkciók. A feltört eszközök más tulajdonságokat állíthatnak magukról. Ezek a korlátozások a nem rosszindulatú felhasználók esetén jelentenek észszerű erőfeszítést igénylő akadályt.

Többek között az alábbi regisztrációs korlátozásokat hozhatja létre:

- Regisztrált eszközök maximális száma.
- Regisztrációra alkalmas eszközplatformok:
  - Android-eszköz rendszergazdája
  - Androidos vállalati munkahelyi profil
  - iOS/iPadOS
  - macOS
  - Windows
  - Windows Mobile
- Platform operációsrendszer-verziója iOS/iPadOS, Android-eszköz rendszergazdája, Android Enterprise Work profil, Windows és Windows Mobile rendszerhez. (Csak a Windows 10-es verziók használhatók. Hagyja üresen, ha a Windows 8.1 engedélyezett.)
  - Minimális verzió.
  - Maximális verzió.
- [Személyes tulajdonú eszközök](device-enrollment.md#bring-your-own-device) korlátozása (iOS, Android rendszerű eszköz rendszergazdája, Android Enterprise Work profil, MacOS, Windows és Windows Mobile).

## <a name="default-restrictions"></a>Alapértelmezett korlátozások

A rendszer tartalmaz alapértelmezett korlátozásokat mind az eszköztípusra, mind az eszközszámra vonatkozóan. Módosíthatja az alapértelmezések beállításait. Az alapértelmezett korlátozások minden felhasználós és felhasználó nélküli regisztrációra vonatkoznak. Felülbírálhatja ezeket az alapértelmezéseket új, magasabb prioritású korlátozások létrehozásával.

## <a name="create-a-device-type-restriction"></a>Eszköz típusú korlátozás létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager Felügyeleti Központba](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközökre** > a **regisztrálási korlátozásokat** > a **korlátozás** > az **eszköz típusának**korlátozására.
2. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
3. A **tovább** gombra kattintva nyissa meg a **platform beállításai** lapot.
4. A **platform**területen válassza az **Engedélyezés** lehetőséget azokhoz a platformokhoz, amelyekre engedélyezni szeretné ezt a korlátozást.
    ![képernyő sapka a platform beállításainak kiválasztásához](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. A **verziók**területen válassza ki azokat a minimális és maximális verziókat, amelyeknek az engedélyezett platformokat támogatni szeretné. A verzióra vonatkozó korlátozások csak a Céges portál regisztrált eszközökre vonatkoznak.
     Támogatott verzióformátumok többek között az alábbiak:
    - Az Android-eszköz rendszergazdája és az Android Enterprise munkahelyi profil támogatja a főverzió. alverzió. Rev. Build használatát.
    - az iOS/iPadOS a főverzió. alverzió. Rev-et támogatja. Az operációs rendszer verziói nem vonatkoznak a Készülékregisztrációs program, az Apple School Manager vagy az Apple konfigurátor alkalmazással regisztrált Apple-eszközökre.
    - A Windows csak a Windows 10-es főverzió. alverzió. Build. Rev-et támogatja.
    
    > [!IMPORTANT]
    > Az Android Enterprise (munkahelyi profil) és az Android-eszközök felügyeleti platformja a következő viselkedéssel rendelkezik:
    > - Ha mindkét platform engedélyezett ugyanahhoz a csoporthoz, akkor a felhasználók munkahelyi profillal lesznek regisztrálva, ha az eszközük támogatja azt, ellenkező esetben a rendszer a következőt regisztrálja: DA. 
    > - Ha mindkét platform engedélyezett a csoport számára, és az adott és nem átfedésben lévő verziókra is finomítva van, akkor a felhasználók megkapják az operációsrendszer-verzióhoz meghatározott beléptetési folyamatot. 
    > - Ha mindkét platform engedélyezve van, de ugyanazon verziók esetében le van tiltva, akkor a blokkolt verzióval rendelkező eszközökön lévő felhasználók le lesznek tiltva az androidos eszköz rendszergazdai regisztrálási folyamatán, majd letiltják a regisztrációt, és a rendszer kéri a kijelentkezést. 
    >
    > Érdemes megjegyezni, hogy a munkahelyi profil vagy az eszköz rendszergazdai regisztrációja sem fog működni, kivéve, ha a megfelelő információt az Android-regisztráció során befejezték. 
    
   > [!Note]
   > A Windows 10 nem adja meg a beléptetés során a Rev számot, így például ha a 10.0.17134.100-ben belép, és az eszköz 10.0.17134.174, a rendszer letiltja a regisztráció során.

6. A **személyes tulajdonú**területen válassza az **Engedélyezés lehetőséget** a saját tulajdonú eszközökként engedélyezni kívánt platformok számára.
7. Az **eszköz gyártója**területen adja meg a blokkolni kívánt gyártók vesszővel tagolt listáját.
8. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
9. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra lesz érvényes, amelyekhez hozzárendelte azt. Ha egy korlátozást egyetlen csoporthoz sem rendel hozzá, akkor az adott korlátozásnak semmilyen hatása nem lesz. Válassza a **Kiválasztás** elemet. 
    ![képernyő sapka a platform beállításainak kiválasztásához](./media/enrollment-restrictions-set/select-groups.png)
10. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
11. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
12. Az új korlátozások az alapértelmezett korlátozásnál eggyel magasabb prioritással jönnek létre. Igény esetén [módosíthatja a prioritást](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Eszköz korlátozási korlátozásának létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager Felügyeleti Központba](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközökre** > a **regisztrálási korlátozásokat** > a korlátozás > az eszközök korlátozására vonatkozó **korlátozás** **létrehozásához** .
2. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
3. A **tovább** gombra kattintva nyissa meg az **eszköz korlátozása** lapot.
4. Az eszközök **korlátja**beállításnál válassza ki a felhasználó által regisztrálható eszközök maximális számát.
    ![képernyő sapka az eszköz korlátjának kiválasztásához](./media/enrollment-restrictions-set/choose-device-limit.png)
5. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
6. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra lesz érvényes, amelyekhez hozzárendelte azt. Ha egy korlátozást egyetlen csoporthoz sem rendel hozzá, akkor az adott korlátozásnak semmilyen hatása nem lesz. Válassza a **Kiválasztás** elemet. 
    ![képernyő sapka a csoportok kiválasztásához](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
8. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
9. Az új korlátozások az alapértelmezett korlátozásnál eggyel magasabb prioritással jönnek létre. Igény esetén [módosíthatja a prioritást](#change-enrollment-restriction-priority).

BYOD regisztrációk során a felhasználóknak megjelenik egy értesítés, értesíti, ha a regisztrált eszközök maximális számát. IOS rendszeren például:

![Az iOS-eszközön megjelenő limitértesítés](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

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

A regisztrációs korlátozás beállításait az alábbi lépésekkel módosíthatja. Ezek a korlátozások nem érintik azokat az eszközöket, amelyek már regisztrálva vannak. Ez a funkció nem alkalmas az [Intune PC-ügynök](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) használatával regisztrált eszközök letiltásához.

1. Jelentkezzen be a [Microsoft Endpoint Manager Felügyeleti Központba](https://go.microsoft.com/fwlink/?linkid=2109431) > **eszközökre** > a **regisztrálási korlátozásokat** > Válassza ki azt a korlátozást, amelyet módosítani szeretne > **tulajdonságainál**.
2. Válassza a **Szerkesztés** lehetőséget a módosítani kívánt beállítások mellett.
3. A **Szerkesztés** lapon végezze el a kívánt módosításokat, és folytassa a **felülvizsgálat + mentés** lapra, majd válassza a **Mentés**lehetőséget.


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
- Az eszköz a csoportházirend-objektumon keresztül regisztrálja, vagy az [Configuration Managerból való automatikus regisztrációt a közös felügyelethez](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1).
 
A következő regisztrációk az Intune-ban vállalatiként vannak megjelölve. De mivel nem biztosítanak az Intune-rendszergazda eszközönkénti felügyeletet, a rendszer letiltja a következőket:
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [Azure Active Directory-csatlakozás a Windows beállítása során](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [Azure Active Directory-csatlakozás a Windows beállításaiból](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Az alábbi személyes regisztrációs módszerek is le lesznek tiltva:
- [Automatikus MDM-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) és [munkahelyi fiók hozzáadása a Windows-beállításokból](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- [Csak MDM-regisztráció]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) lehetősége a Windows-beállításokból.

\* Ha az AutoPilottal regisztrált, ezek nincsenek letiltva.


## <a name="blocking-personal-iosipados-devices"></a>Személyes iOS-/iPadOS-eszközök blokkolása
Alapértelmezés szerint az Intune a személyes tulajdonú iOS/iPadOS-eszközöket sorolja fel. Ahhoz, hogy a vállalat tulajdonában legyen besorolva, az iOS/iPadOS-eszköznek az alábbi feltételek egyikét kell teljesítenie:
- Sorozatszámmal vagy IMEI-számmal regisztrálva.
- Regisztrálva van az automatikus eszközök regisztrációjának használatával (korábban Készülékregisztrációs program)


## <a name="change-enrollment-restriction-priority"></a>A regisztrációs korlátozások prioritásának módosítása

A prioritást akkor használja a rendszer, ha egy felhasználó több olyan csoportnak is a tagja, amelyhez korlátozások vannak hozzárendelve. A felhasználókra a rendszer egyedül a vonatkozó csoportok legmagasabb prioritású korlátozását alkalmazza. Tegyük fel például, hogy Attila tagja az A csoportnak, melyhez egy 5-ös prioritású korlátozás van hozzárendelve, illetve tagja a B csoportnak is, melyhez egy 2-es prioritású korlátozás van hozzárendelve. Ez esetben Attilára csak a 2-es prioritású korlátozást alkalmazza a rendszer.

Az Ön által létrehozott korlátozások az alapértelmezettnél eggyel magasabb prioritást kapnak.

Az eszközregisztráció tartalmaz alapértelmezett korlátozásokat mind az eszköztípusra, mind az eszközszámra vonatkozóan. Ez a két korlátozás az összes felhasználóra érvényes, hacsak felül nem bírálják őket magasabb prioritású korlátozások.

Az összes egyéni korlátozás prioritását módosíthatja.

1. Jelentkezzen be az Azure Portalra.
2. Válassza a **További szolgáltatások** lehetőséget, írja be az **Intune** keresési kifejezést, majd válassza az **Intune** lehetőséget.
3. Válassza az **Eszközök regisztrálása** > **Regisztrációs korlátozások** lehetőséget.
4. Vigye az egérmutatót a korlátozás fölé a prioritáslistában.
5. A három függőleges pontot alkotó ikon használatával húzza a prioritást a lista megfelelő helyére.
