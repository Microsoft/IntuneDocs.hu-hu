---
title: Regisztrációs korlátozások beállítása a Microsoft Intuneban
titleSuffix: ''
description: Korlátozza a beléptetést a platformon, és állítsa be az eszközök regisztrálási korlátját az Intune-ban.
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
ms.openlocfilehash: d96cd3e6496bbfde35a666bfcf4a1f6427e45173
ms.sourcegitcommit: 11ae6a37527ef5b3ac042743950254f3ef559c53
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72280251"
---
# <a name="set-enrollment-restrictions"></a>Regisztrációs korlátozások beállítása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune-rendszergazdaként létrehozhat és kezelhet olyan regisztrációs korlátozásokat, amelyek meghatározzák, hogy mely eszközök regisztrálhatók a felügyeletbe az Intune-nal, beleértve a következőket:
- eszközök száma
- az operációs rendszerek és verziók több korlátozást is létrehozhatnak, és különböző felhasználói csoportokra alkalmazhatják őket. Megadhatja a különböző korlátozásokhoz tartozó [prioritási sorrendet](#change-enrollment-restriction-priority) .

>[!NOTE]
>A regisztrációs korlátozások nem biztonsági funkciók. A feltört eszközök megadhatják a karakterét. Ezek a korlátozások a nem rosszindulatú felhasználók számára ajánlott akadályok.

A létrehozható konkrét regisztrációs korlátozások a következők lehetnek:

- A regisztrált eszközök maximális száma.
- A regisztrálni kívánt eszközök platformja:
  - Android-eszköz rendszergazdája
  - Androidos vállalati munkahelyi profil
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Platform operációsrendszer-verziója iOS, Android rendszerű eszköz rendszergazdája, Android Enterprise Work profil, Windows és Windows Mobile rendszerű eszközökhöz. (Csak a Windows 10 verziói használhatók. Ha a Windows 8,1 engedélyezve van, hagyja üresen.)
  - Minimális verzió.
  - Maximális verzió.
- Személyes tulajdonú eszközök korlátozása (iOS, Android rendszerű eszköz rendszergazdája, Android Enterprise Work profil, macOS, Windows és Windows Mobile).

## <a name="default-restrictions"></a>Alapértelmezett korlátozások

Az alapértelmezett korlátozásokat a rendszer automatikusan megadja mindkét eszköz típusa és az eszközök korlátozására vonatkozó regisztrációs korlátozásokhoz. Módosíthatja az alapértelmezett beállítások beállításait. Az alapértelmezett korlátozások az összes felhasználóra és felhasználóra vonatkozó regisztrációra érvényesek. Ezeket az alapértelmezett értékeket felülbírálhatja, ha új korlátozásokat hoz létre magasabb prioritásokkal.

## <a name="create-a-device-type-restriction"></a>Eszköz típusú korlátozás létrehozása

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások**lehetőséget, keresse meg az **Intune**-t, majd válassza az **Intune**lehetőséget.
3. Válassza az **eszközök beléptetése** > **regisztrációs korlátozások** > **Létrehozás korlátozás** > **típusú eszköz korlátozását**.
    ![Screen sapka az eszköz típusú korlátozás létrehozásához @ no__t-1
4. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
5. A **tovább** gombra kattintva nyissa meg a **platform beállításai** lapot.
6. A **platform**területen válassza az **Engedélyezés** lehetőséget azokhoz a platformokhoz, amelyekre engedélyezni szeretné ezt a korlátozást.
    ![Screen sapka a platform beállításainak kiválasztásához @ no__t-1
7. A **verziók**területen válassza ki azokat a minimális és maximális verziókat, amelyeknek az engedélyezett platformokat támogatni szeretné. A verzióra vonatkozó korlátozások csak a Céges portál regisztrált eszközökre vonatkoznak.
     A támogatott verziók a következők:
    - Az Android-eszköz rendszergazdája és az Android Enterprise munkahelyi profil támogatja a főverzió. alverzió. Rev. Build használatát.
    - az iOS támogatja a főverzió. alverzió. Rev. Az operációs rendszer verziói nem vonatkoznak a Készülékregisztrációs program, az Apple School Manager vagy az Apple konfigurátor alkalmazással regisztrált Apple-eszközökre.
    - A Windows csak a Windows 10-es főverzió. alverzió. Build. Rev-et támogatja.
    > [!Note]
    > A Windows 10 nem adja meg a beléptetés során a Rev számot, így például ha a 10.0.17134.100-ben belép, és az eszköz 10.0.17134.174, a rendszer letiltja a regisztráció során.

8. A **személyes tulajdonú**területen válassza az **Engedélyezés lehetőséget** a saját tulajdonú eszközökként engedélyezni kívánt platformok számára.
9. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
10. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra vonatkozik, amelyekhez hozzá van rendelve. Ha nem rendel hozzá korlátozást legalább egy csoporthoz, nem lesz hatása. Ezután válassza a **kiválasztás**lehetőséget. 
    ![Screen sapka a platform beállításainak kiválasztásához @ no__t-1
11. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
12. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
13. Az új korlátozás az alapértelmezettnél magasabb prioritással jön létre. [Módosíthatja a prioritást](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Eszköz korlátozási korlátozásának létrehozása

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások**lehetőséget, keresse meg az **Intune**-t, majd válassza az **Intune**lehetőséget.
3. Válassza az **eszközök beléptetése** > **regisztrációs korlátozások** > **Létrehozás korlátozás** > **eszköz**korlátozásának korlátozását.
    ![Screen sapka az eszközök korlátozására vonatkozó korlátozás létrehozásához @ no__t-1
4. Az **alapvető beállítások** lapon adja meg a korlátozás **nevét** és **leírását**(nem kötelező).
5. A **tovább** gombra kattintva nyissa meg az **eszköz korlátozása** lapot.
6. Az eszközök **korlátja**beállításnál válassza ki a felhasználó által regisztrálható eszközök maximális számát.
    ![Screen sapka az eszköz korlátjának kiválasztásához @ no__t-1
7. A **tovább** gombra kattintva nyissa meg a **hozzárendelések** lapot.
8. Válassza ki a **felvenni kívánt csoportokat** , majd a keresőmező segítségével keresse meg azokat a csoportokat, amelyeket ebbe a korlátozásba kíván foglalni. A korlátozás csak azokra a csoportokra vonatkozik, amelyekhez hozzá van rendelve. Ha nem rendel hozzá korlátozást legalább egy csoporthoz, nem lesz hatása. Ezután válassza a **kiválasztás**lehetőséget. 
    ![Screen sapka a csoportok kiválasztásához @ no__t-1
11. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.
12. Válassza a **Létrehozás** lehetőséget a korlátozás létrehozásához.
13. Az új korlátozás az alapértelmezettnél magasabb prioritással jön létre. [Módosíthatja a prioritást](#change-enrollment-restriction-priority).

A BYOD-regisztráció során a felhasználók értesítést kapnak arról, hogy mikor teljesítik a regisztrált eszközök maximális számát. IOS rendszeren például:

![iOS-eszközök korlátozására vonatkozó értesítés](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

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

A regisztrációs korlátozás beállításait az alábbi lépésekkel módosíthatja. Ezek a korlátozások nem érintik azokat az eszközöket, amelyek már regisztrálva vannak. Az [INTUNE PC-ügynökkel](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) regisztrált eszközök nem tiltható le ezzel a szolgáltatással.

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások**lehetőséget, keresse meg az **Intune**-t, majd válassza az **Intune**lehetőséget.
3. Válassza ki az **eszközök beléptetése** > **regisztrációs korlátozásokat** > Válassza ki a módosítani kívánt korlátozást > **tulajdonságokat**.
4. Válassza a **Szerkesztés** lehetőséget a módosítani kívánt beállítások mellett.
5. A **Szerkesztés** lapon végezze el a kívánt módosításokat, és folytassa a **felülvizsgálat + mentés** lapra, majd válassza a **Mentés**lehetőséget.


## <a name="blocking-personal-android-devices"></a>Személyes Android-eszközök blokkolása
- Ha letiltja a személyes tulajdonú Android-eszközök regisztrációját, a személyes tulajdonú Android Enterprise Work profiling-eszközök továbbra is regisztrálhatnak.
- Alapértelmezés szerint az androidos vállalati munkahelyi profil eszközeinek beállításai megegyeznek az Android-eszközök rendszergazdai eszközeinek beállításaival. Miután módosította az androidos vállalati munkahelyi profilt vagy az Android-eszköz rendszergazdai beállításait, már nem ez a helyzet.
- Ha letiltja a személyes Android vállalati munkahelyi profil regisztrálását, csak a vállalat által birtokolt Android-eszközök regisztrálhatók androidos vállalati munkahelyi profilokkal.

## <a name="blocking-personal-windows-devices"></a>Személyes Windows-eszközök blokkolása
Ha letiltja a személyes tulajdonban lévő Windows-eszközök regisztrációját, az Intune ellenőrzi, hogy minden új Windows-beléptetési kérelem engedélyezve lett-e vállalati beléptetésként. A jogosulatlan regisztrációk le lesznek tiltva.

A következő módszerek érvényesek a Windows vállalati beléptetésének engedélyezéseként:
- A beléptetés felhasználója egy [eszköz tanúsítványigénylési kezelőjének fiókját]( device-enrollment-manager-enroll.md)használja.
- Az eszköz regisztrál a [Windows Autopilot](enrollment-autopilot.md)szolgáltatásban.
- Az eszköz regisztrálva van a Windows Autopilot szolgáltatásban, de a Windows beállításai nem csak MDM-regisztrációt igényelnek.
- Az eszköz IMEI-száma az **eszközök beléptetése** >  **[vállalati eszköz azonosítói](corporate-identifiers-add.md)** között szerepel. (Windows Phone-telefon 8,1 esetén nem támogatott.)
- Az eszköz regisztrál egy [tömeges kiépítési csomagon](windows-bulk-enroll.md)keresztül.
- Az eszköz regisztrál a csoportházirend-objektumon keresztül, vagy [automatikus regisztrációt a SCCM-ből a közös felügyelethez](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
A következő regisztrációk az Intune-ban vállalatiként vannak megjelölve. De mivel nem biztosítanak az Intune-rendszergazda eszközönkénti felügyeletet, a rendszer letiltja a következőket:
- [Automatikus Mdm](windows-enroll.md#enable-windows-10-automatic-enrollment) -regisztráció [Azure Active Directory csatlakoztatáskor a Windows telepítő](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Automatikus Mdm](windows-enroll.md#enable-windows-10-automatic-enrollment) -regisztráció [Azure Active Directory Windows-beállításokkal való csatlakozással](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
A következő személyes regisztrációs módszerek is blokkolva lesznek:
- [Automatikus Mdm-regisztráció](windows-enroll.md#enable-windows-10-automatic-enrollment) a [munkahelyi fiók hozzáadása a Windows-beállítások](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)@no__t – 2.
- A [Mdm csak]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) a Windows beállításai közül választhat.

@no__t – 0 ezek nem lesznek letiltva, ha az Autopilot regisztrálva van.


## <a name="change-enrollment-restriction-priority"></a>Regisztráció korlátozási prioritásának módosítása

A rendszer akkor használja a prioritást, ha egy felhasználó több, korlátozás alá tartozó csoportban található. A felhasználók csak a legmagasabb prioritású korlátozáshoz vannak rendelve, amely a csoporthoz tartozik. Joe például az A csoport, amely a Priority 5 korlátozásokhoz van rendelve, valamint a B csoportba a 2. prioritáshoz rendelt korlátozásokat is. Joe csak a 2. prioritásra vonatkozó korlátozásoknak van kitéve.

Ha korlátozást hoz létre, az alapértelmezés szerint közvetlenül a listára kerül.

Az eszközök beléptetése alapértelmezett korlátozásokat tartalmaz az eszközök és az eszközök korlátozására vonatkozóan. Ez a két korlátozás az összes felhasználóra érvényes, kivéve ha azok felülbírálják a magasabb prioritású korlátozásokat.

Módosíthatja a nem alapértelmezett korlátozások prioritását.

1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások**lehetőséget, keresse meg az **Intune**-t, majd válassza az **Intune**lehetőséget.
3. Válassza az **eszközök beléptetése**@no__t – 1**regisztrációs korlátozásokat**.
4. Vigye az egérmutatót a prioritási lista korlátozására.
5. A három függőleges pont használatával húzza a prioritást a lista kívánt helyére.
