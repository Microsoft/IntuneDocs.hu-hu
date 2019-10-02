---
title: Hová kerültek az Intune-funkciók az Azure-ban?
titleSuffix: Microsoft Intune
description: A Microsoft Intune-funkciók megkeresése az Azure Portalon.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f74ed8586bcfca21ea7434ec1c6ad045c8bc1bbd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731647"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Hová kerültek az Intune-funkciók az Azure-ban?
Az Intune Azure Portalra való költöztetésekor éltünk a lehetőséggel, és logikusabban rendeztünk el néhány feladatot. Minden ilyen előrelépés azzal jár, hogy meg kell tanulni az új elrendezést. Ez az útmutató azoknak készült, akik jól ismerik a klasszikus Intune-portált, és szeretnék megtudni, hogyan végezhetik el a feladatokat az Azure Portalbeli Intune-ban. Ha a cikk nem tartalmazza az Ön által keresett információt, írja meg a lap alján hozzászólásban, hogy pótolhassuk.
## <a name="quick-reference-guide"></a>Rövid összefoglaló útmutató

|Funkció |Elérési útvonal a klasszikus portálon|Elérési útvonal az Azure Portalbeli Intune-ban|
|------------|---------------|---------------|
|Készülékregisztrációs program (DEP) [csak iOS rendszeren]|Felügyelet > Mobileszköz-kezelés > iOS > Készülékregisztrációs program|[Eszközregisztráció > Apple-regisztráció > Regisztrációs program tokenje](#where-did-apple-dep-go) |
|Készülékregisztrációs program (DEP) [csak iOS rendszeren]| Felügyelet > Mobileszköz-kezelés > iOS és macOS > Készülékregisztrációs program |[Eszközregisztráció > Apple-regisztráció > Regisztrációs program sorozatszámai](#where-did-apple-dep-go) |
|Beléptetési szabályok |Felügyelet > Mobileszköz-kezelés > Regisztrációs szabályok|[Eszközregisztráció > Regisztrációs korlátozások](#where-did-enrollment-rules-go) |
|Csoportok iOS-sorozatszám szerint |Csoportok > Minden eszköz > Előre regisztrált vállalati eszközök > iOS-sorozatszám szerint|[Eszközregisztráció > Apple-regisztráció > Regisztrációs program sorozatszámai](#where-did-corporate-pre-enrolled-devices-go) |
|Csoportok iOS-sorozatszám szerint |Csoportok > Minden eszköz > Előre regisztrált vállalati eszközök > iOS-sorozatszám szerint| [Eszközregisztráció > Apple-regisztráció > AC-sorozatszámok](#where-did-corporate-pre-enrolled-devices-go)|
|Csoportok IMEI szerint (minden platform)| Csoportok > Minden eszköz > Előre regisztrált vállalati eszközök > IMEI szerint (minden platform) | [Eszközregisztráció > Céges készülékazonosítók](#by-imei-all-platforms)|
| Vállalati eszközregisztrációs profil| Szabályzat > Vállalati eszközök regisztrációja | [Eszközregisztráció > Apple-regisztráció > Regisztrációs programprofilok](#where-did-corporate-pre-enrolled-devices-go) |
| Vállalati eszközregisztrációs profil | Szabályzat > Vállalati eszközök regisztrációja | [Eszközregisztráció > Apple-regisztráció > AC-profilok](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | Felügyelet > Mobileszköz-kezelés > Android for Work | Eszközregisztráció > Android eszközök beléptetése |
| Feltételek és kikötések | Szabályzatok > Használati feltételek | Eszközregisztráció > Használati feltételek |
A céges portál beállításai|Felügyelet > Céges portál|**Kezelés** > Mobilalkalmazások<br> **Telepítő** > A Céges portál védjegyezése


## <a name="where-do-i-manage-groups"></a>Hol lehet a csoportokat kezelni?
Az Azure Portalbeli Intune az [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) segítségével kezeli a csoportokat.

## <a name="where-did-enrollment-rules-go"></a>Hová tűntek a regisztrációs szabályok?
A klasszikus portálon be lehetett állítani a modern windowsos és macOS-es, valamint mobileszközök MDM-regisztrációjára vonatkozó szabályokat.

![Klasszikus mobileszköz-regisztrációs szabályok képe](./media/ui-changes/01-classic-rules.png)

Ezek a szabályok kivétel nélkül vonatkoztak az Intune-fiók összes felhasználójára. A Azure Portalban ezek a szabályok két különböző típusú házirendben jelennek meg: Az eszközök típusának korlátozásai és az eszközökre vonatkozó korlátozások korlátozása.

![Azure-os mobileszköz-regisztrációs korlátozások képe](./media/ui-changes/02-azure-enroll-restrictions.png)

Az eszközök száma szerinti alapértelmezett korlátozás megfelel a klasszikus portálon a Regisztrált eszközök maximális száma szabálynak.

![Azure-os eszközszám-korlátozások képe](./media/ui-changes/03-azure-device-limit.png)

Az eszköztípus szerinti alapértelmezett korlátozás megfelel a klasszikus portálon a platformkorlátozási szabálynak.

![Azure-os eszköztípus-korlátozások képe](./media/ui-changes/04-azure-platform-restrictions.png)

A személyes tulajdonú eszközök letiltásának vagy engedélyezésének képességét az eszköztípus szerinti korlátozások platformkonfigurációjában lehet kezelni.

![Azure-os személyes eszközletiltási beállítások képe](./media/ui-changes/05-azure-personal-block.png)

A további korlátozási képességek csak az Azure Portalon érhetők el.

## <a name="where-did-my-conditional-access-policies-go"></a>Hová mennek a feltételes hozzáférési szabályzatok?
Miután a bérlő áttelepítette a Azure Portal, a bérlő feltételes hozzáférési házirendjei továbbra is érvényben vannak. Megtekinteni vagy módosítani viszont nem tudja őket az Intune-ból az Azure Portalon.

Ha szeretné megtekinteni és módosítani a feltételes hozzáférési szabályzatokat a Azure Portalból, el kell távolítania a régi szabályzatokat a klasszikus portálról. Ez után újra létrehozhatja azokat az Azure Portalon. A feltételes hozzáférési szabályzatok áttelepítésével kapcsolatos további információkért lásd: [klasszikus szabályzatok áttelepítése az Azure Portalon](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration). 

## <a name="where-did-my-compliance-policies-go"></a>Mi történt a megfelelőségi szabályzataimmal?
Miután a bérlője migrál az Azure Portalra, a bérlő megfelelőségi szabályzatai továbbra is érvényesülnek. Megtekinteni vagy módosítani viszont nem tudja őket az Intune-ból az Azure Portalon.

Ha meg kívánja tekinteni vagy módosítani szeretné a megfelelőségi szabályzatokat az Azure Portalon, akkor el kell távolítania a régi szabályzatokat a klasszikus portálról. Ez után újra létrehozhatja azokat az Azure Portalon. További információk az eszközmegfelelőségi szabályzatokról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](../protect/device-compliance-get-started.md). 

## <a name="where-did-apple-dep-go"></a>Hová tűnt az Apple DEP?
A klasszikus portálon az Intune-t integrálni lehetett az Apple készülékregisztrációs programjával, és manuálisan szinkronizálást kérni az Apple szolgáltatásával:

![Klasszikus DEP-token képe](./media/ui-changes/06-classic-dep-token.png)

Az Azure Portalon ugyanazokkal a lépésekkel lehet beállítani az Apple DEP-et, mint a klasszikus Intune-ban:

![Azure-os DEP-token képe](./media/ui-changes/07-azure-dep-token.png)

A klasszikus portál **Szinkronizálás** lehetősége azonban a sorozatszám-kezelési munkafolyamatba került, hiszen a manuális szinkronizálás eredménye is ott jelenik meg:

![Azure-os DEP-szinkronizálás képe](./media/ui-changes/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Hová tűntek az előre regisztrált vállalati eszközök?
### <a name="by-ios-serial-number"></a>iOS-sorozatszám szerint
A klasszikus portálon az iOS-es eszközöket az Apple készülékregisztrációs programjával (DEP) és az Apple Configurator eszközzel lehet regisztrálni. Mindkét módszerrel lehetséges a sorozatszám-alapú előzetes regisztráció, és mindkettőhöz speciális Céges eszközregisztrációs profilokat kell kiosztani. A regisztráció előtt a regisztrációs profilok kiosztását a **Előre regisztrált vállalati eszközök iOS-sorozatszám szerint** eszközcsoporttal lehet kezelni:

![Klasszikus Apple-sorozatszámok képe](./media/ui-changes/09-classic-apple-serials.png)

Az Apple DEP-pel és a Configurator eszközzel végzett regisztrációk sorozatszámai közös listán jelennek meg. A téves profilkiosztások (DEP-profil AC-sorozatszámhoz vagy fordítva) számának csökkentése érdekében az Azure Portalon két listába osztottuk szét a sorozatszámokat:

**DEP-sorozatszámok**
![Azure-os DEP-sorozatszámok képe](./media/ui-changes/10-azure-dep-serials.png)

**Apple Configurator-sorozatszámok**
![Azure-os Apple Configurator-sorozatszámok képe](./media/ui-changes/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>IMEI-szám szerint (minden platform)

A klasszikus portálon előzetesen meg lehet adni azoknak az eszközöknek a sorozatszámát, amelyeket az Intune-regisztráció alkalmával céges tulajdonúként kell megjelölni:

![Klasszikus IMEI-számlista képe](./media/ui-changes/12-classic-corp-imei.png)

Az Azure Portalon ugyanezeket az IMEI-számokat a Céges készülékazonosítók listába kell feltölteni vesszőkkel tagolt (CSV) fájlként. Az új portálon nem lehet manuálisan bevinni az IMEI-számokat:

![Azure-os IMEI-számlista képe](./media/ui-changes/13-azure-corp-imei.png)

Az Azure-beli Intune fel van készítve az IMEI mellett másféle azonosítók kezelésére is, de jelenleg csak az IMEI-számokat lehet előzetesen bevinni.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Hová tűntek a céges eszközregisztrációs profilok?
Ha az Apple DEP program keretében vagy az Apple Configurator eszközzel iOS-es eszközöket szeretne regisztrálni, meg kell adnia az eszköznek kiosztandó céges eszközregisztrációs profilt. A klasszikus portálon ezeknek a profiloknak a létrehozása és kezelése egyetlen listában történt:

![Klasszikus eszközregisztrációs profilok képe](./media/ui-changes/14-classic-corp-profiles.png)

Ebben a listában láthatók az Apple DEP programmal használható (**DEP On** – DEP engedélyezve) és a csak az Apple Configurator eszközzel használható (**DEP Off** – DEP letiltva) profilok.

A két profiltípus keveredésének és az ebből fakadó téves profilkiosztásoknak (DEP-profil AC-sorozatszámhoz vagy fordítva) az elkerülése érdekében elkülönítettük (az Apple készülékregisztrációs programját és az Apple School Managert is támogató) DEP-profilok, illetve az Apple Configurator-profilok létrehozását és kezelését:

**DEP-profilok**
![Azure-os DEP-profilok képe](./media/ui-changes/15-azure-dep-profiles.png)

**Apple Configurator-profilok**
![Azure-os Apple Configurator-profilok képe](./media/ui-changes/16-azure-ac-profiles.png)
