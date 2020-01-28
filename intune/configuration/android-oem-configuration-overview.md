---
title: A OEMConfig használata androidos vállalati eszközökön Microsoft Intune-Azure-ban | Microsoft Docs
description: Az OEMConfig használatával az Android Enterprise rendszert futtató eszközöket a Microsoft Intune segítségével kezelheti és használhatja. Tekintse meg az összes lépést, beleértve az áttekintést, az előfeltételek, a konfigurációs profil létrehozása az Intune-ban című témakört, és tekintse meg a támogatott OEMConfig-alkalmazások listáját.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b5a0b152b6090da1831ac6d7b707c10ec466ce7
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754592"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Androidos nagyvállalati eszközök használata és kezelése a OEMConfig-ben Microsoft Intune

A Microsoft Intune a OEMConfig használatával adhat hozzá, hozhat létre és szabhat testre OEM-specifikus beállításokat az androidos vállalati eszközökhöz. A OEMConfig általában az Intune-ban nem beépített beállítások konfigurálására szolgálnak. Az eredeti berendezésgyártó (OEM) különböző beállításokat tartalmaz. Az elérhető beállítások attól függnek, hogy az OEM milyen tartalmakat tartalmaz a OEMConfig alkalmazásban.

Ez a funkció az alábbiakra vonatkozik:  

- Vállalati Android

Ez a cikk a OEMConfig ismerteti, felsorolja az előfeltételeket, bemutatja, hogyan hozhat létre konfigurációs profilt, és listázza a támogatott OEMConfig-alkalmazásokat az Intune-ban.

## <a name="overview"></a>Overview

A OEMConfig szabályzatok az [alkalmazás-konfigurációs házirendhez](../apps/app-configuration-policies-overview.md)hasonló speciális típusú eszköz-konfigurációs házirend. A OEMConfig egy, a Google által meghatározott szabvány, amely az alkalmazások konfigurációját használja az Androidon az eszközök beállításainak az OEM-ek által írt alkalmazásokba való küldéséhez (eredeti berendezésgyártó). Ez a szabvány lehetővé teszi, hogy a számítógépgyártók és a EMMs (nagyvállalati mobilitási felügyelet) szabványosított módon hozzanak létre és támogassák az OEM-specifikus szolgáltatásokat. [További információ a OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

A EMMs, például az Intune, az OEM-specifikus funkciók támogatását manuálisan is kiépítheti, miután a számítógépgyártó bevezette őket. Ez a megközelítés ismétlődő erőfeszítéseket és lassú bevezetést eredményez.

A OEMConfig esetében az OEM egy olyan sémát hoz létre, amely az OEM-specifikus felügyeleti funkciókat definiálja. Az OEM beágyazza a sémát egy alkalmazásba, majd ezt az alkalmazást a Google Play webhelyen helyezi el. Az az alkalmazásból beolvassa a sémát, és elérhetővé teszi a sémát a az a-ben lévő, a (az A konzol lehetővé teszi az Intune-rendszergazdák számára a séma beállításainak konfigurálását.

Ha a OEMConfig-alkalmazás egy eszközre települ, a a (z) a (z) és a (z) és a (z) által felügyelt, az Az eszközök beállításait a OEMConfig alkalmazás hajtja végre, nem pedig az MDM-ügynök által készített,

Ha az OEM hozzáadja és javítja a felügyeleti funkciókat, az OEM az alkalmazást a Google Play áruházban is frissíti. Rendszergazdaként ezeket az új szolgáltatásokat és frissítéseket (beleértve a javításokat is) úgy érheti el, hogy a EMMs-re való várakozás nélkül is felveszi ezeket a frissítéseket.

> [!TIP]
> A OEMConfig csak olyan eszközökkel használható, amelyek támogatják ezt a funkciót, és rendelkeznek egy megfelelő OEMConfig-alkalmazással. További részletekért forduljon az OEM-hez.

## <a name="before-you-begin"></a>Előkészületek

A OEMConfig használatakor vegye figyelembe a következő információkat:

- Az Intune elérhetővé teszi a OEMConfig alkalmazás sémáját, hogy beállítsa. Az Intune nem ellenőrzi vagy nem módosítja az alkalmazás által biztosított sémát. Így ha a séma helytelen, vagy pontatlan adatmennyiséggel rendelkezik, ezeket az adatait a rendszer továbbra is elküldi az eszközöknek. Ha olyan problémát talál, amely a sémából származik, forduljon az OEM-hez útmutatásért.
- Az Intune nem befolyásolja vagy szabályozza az alkalmazás sémájának tartalmát. Az Intune például nem rendelkezik a karakterláncok, a nyelv, az engedélyezett műveletek és így tovább. Javasoljuk, hogy az eszközök OEMConfig való kezelésével kapcsolatos további információkért vegye fel a kapcsolatot az OEM-mel.
- A számítógépgyártók bármikor frissíthetik a támogatott szolgáltatásokat és sémákat, és új alkalmazást tölthetnek fel a Google Play áruházba. Az Intune mindig szinkronizálja a OEMConfig alkalmazás legújabb verzióját a Google Play áruházból. Az Intune nem tartja karban a séma vagy az alkalmazás régebbi verzióit. Ha a verziószáma ütközik, javasoljuk, hogy további információért forduljon az OEM-hez.
- Rendeljen egy OEMConfig-profilt egy eszközhöz. Ha ugyanahhoz az eszközhöz több profil is hozzá van rendelve, akkor inkonzisztens viselkedést tapasztalhat. A OEMConfig-modell csak egyetlen házirendet támogat eszközönként.

## <a name="prerequisites"></a>Előfeltételek

A OEMConfig eszközön való használatához győződjön meg arról, hogy rendelkezik a következő követelményekkel:

- Az Intune-ban regisztrált androidos vállalati eszköz.
- Az OEM által készített OEMConfig-alkalmazás, amelyet a Google Play áruházba töltöttek fel. Ha nem a Google Play áruházban van, további információért forduljon az OEM-hez.
- Az Intune rendszergazdája szerepköralapú hozzáférés-vezérlési (RBAC) engedélyekkel rendelkezik a mobileszközök és az **eszközök konfigurálásához**, valamint az **Android for Work** **alkalmazásban**az "olvasás" engedélyre. Ezek az engedélyek azért szükségesek, mert a OEMConfig-profilok felügyelt alkalmazás-konfigurációkat használnak az eszközök konfigurációjának kezeléséhez.

## <a name="prepare-the-oemconfig-app"></a>A OEMConfig alkalmazás előkészítése

Győződjön meg arról, hogy az eszköz támogatja a OEMConfig, a megfelelő OEMConfig-alkalmazást adja hozzá az Intune-hoz, és az alkalmazás telepítve van az eszközön. Ehhez az információhoz forduljon az OEM-hez.

> [!TIP] 
> A OEMConfig-alkalmazások az OEM-re jellemzőek. Egy Zebra Technologies-eszközre telepített Sony OEMConfig-alkalmazás például nem csinál semmit.

1. Szerezze be a OEMConfig alkalmazást a felügyelt Google Play Áruház. [Felügyelt Google Play-alkalmazások hozzáadása Android Enterprise-eszközökhöz](../apps/apps-add-android-for-work.md) a lépések felsorolása.
2. Egyes számítógépgyártók előre telepített OEMConfig-alkalmazással is eldönthetik az eszközök szállítását. Ha az alkalmazás nincs előtelepítve, az Intune használatával [adhatja hozzá és helyezheti üzembe az alkalmazást az eszközökön](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>OEMConfig-profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Platform**: válassza az **Android Enterprise**lehetőséget.
    - **Profil típusa**: válassza a **OEMConfig**lehetőséget.

4. Válassza a **Létrehozás** lehetőséget.
5. Az **alapvető beállítások**területen adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **OEMConfig-alkalmazás**: válassza **az OEMConfig-alkalmazás kiválasztása**lehetőséget.

6. A **társított alkalmazásban**válasszon ki egy korábban hozzáadott meglévő OEMConfig-alkalmazást > **válassza a lehetőséget**. Ügyeljen arra, hogy a megfelelő OEMConfig-alkalmazást válassza ki azokhoz az eszközökhöz, amelyekre a szabályzatot hozzárendeli.

    Ha nem látja a felsorolt alkalmazásokat, akkor állítsa be a felügyelt Google Play áruházat, és szerezze be az alkalmazásokat a felügyelt Google Play áruházból. [Felügyelt Google Play-alkalmazások hozzáadása Android Enterprise-eszközökhöz](../apps/apps-add-android-for-work.md) a lépések felsorolása.

    > [!IMPORTANT]
    > Ha egy OEMConfig-alkalmazást adott hozzá, és szinkronizálta azt a Google Play-be, de nem szerepel a **társított alkalmazásban**, akkor előfordulhat, hogy kapcsolatba kell lépnie az Intune-nal az alkalmazás bevezetéséhez. Lásd: [új alkalmazás hozzáadása](#supported-oemconfig-apps) (ebben a cikkben).

7. Válassza a **Tovább** elemet.
8. A **beállítások konfigurálása**területen válassza ki a **Configuration Designer** vagy a **JSON-szerkesztőt**:

    > [!TIP]
    > Olvassa el az OEM dokumentációját, és győződjön meg róla, hogy helyesen konfigurálja a tulajdonságokat. Ezeket az alkalmazás-tulajdonságokat az OEM, nem pedig az Intune tartalmazza. Az Intune minimálisan ellenőrzi a tulajdonságokat, vagy a beírt értéket. Ha például megadja `abcd` portszámot, a profil a-as értékre lesz mentve, és a rendszer az Ön által konfigurált értékeket telepíti az eszközökre. Ügyeljen arra, hogy a helyes adatokat adja meg.

    - **Configuration Designer**: Ha bejelöli ezt a beállítást, az alkalmazás sémáján belül elérhető tulajdonságok is megjelennek a konfiguráláshoz.

      - A Configuration Designer helyi menüi azt jelzik, hogy több lehetőség is rendelkezésre áll. A helyi menü például lehetővé teheti a beállítások hozzáadását, törlését és átrendezését. Ezeket a beállításokat a SZÁMÍTÓGÉPGYÁRTÓ is tartalmazza. Olvassa el az OEM-alkalmazás dokumentációját, amelyből megtudhatja, hogyan kell használni ezeket a beállításokat a profilok létrehozásához.

      - Számos beállításhoz az OEM által megadott alapértelmezett értékek tartoznak. Ha meg szeretné tekinteni, hogy van-e alapértelmezett érték, vigye a kurzort a beállítás melletti információs ikonra. Az elemleírás az adott beállítás alapértelmezett értékeit (ha alkalmazható) és az OEM által biztosított további részleteket jeleníti meg.

      - A **Törlés** gombra kattintva törölheti a beállításokat a profilból. Ha egy beállítás nincs a profilban, az eszköz értéke nem változik a profil alkalmazása után.

      - Ha üres (nem konfigurált) köteget hoz létre a Configuration Designerben, a rendszer törli a JSON-szerkesztőre való áttéréskor.

    - **JSON-szerkesztő**: Ha ezt a beállítást választja, megnyílik egy JSON-szerkesztő, amely az alkalmazásban beágyazott teljes konfigurációs séma sablonját nyitja meg. A szerkesztőben szabja testre a sablont a különböző beállítások értékeivel. Ha a **Configuration Designer** használatával módosítja az értékeket, a JSON-szerkesztő felülírja a sablont a Configuration Designer értékével.

      - Ha meglévő profilt frissít, a JSON-szerkesztő megjeleníti azokat a beállításokat, amelyek utoljára mentve lettek a profillal.

      - A OEMConfig sémái nagyok és összetettebbek lehetnek. Ha egy másik szerkesztő használatával szeretné frissíteni ezeket a beállításokat, válassza a **JSON-sablon letöltése** gombot. Az Ön által választott szerkesztővel adhatja hozzá a konfigurációs értékeket a sablonhoz. Ezután másolja és illessze be a frissített JSON-t a **JSON-szerkesztő** tulajdonságba.

      - A JSON-szerkesztő segítségével biztonsági másolatot készíthet a konfigurációról. Miután konfigurálta a beállításokat, ezzel a funkcióval lekérheti a JSON-beállításokat az értékekkel. Másolja és illessze be a JSON-fájlt egy fájlba, és mentse. Most már van egy biztonságimásolat-fájlja.

    A Configuration Designerben végrehajtott módosítások a JSON-szerkesztőben is automatikusan megtörténik. Hasonlóképpen, a JSON-szerkesztőben végrehajtott módosítások automatikusan a Configuration Designerben történnek. Ha a bemenet érvénytelen értékeket tartalmaz, nem válthat a Configuration Designer és a JSON-szerkesztő között, amíg ki nem javítja a problémákat.

9. Válassza a **Tovább** elemet.
10. A **hatókör címkék** (nem kötelező) területen rendeljen hozzá egy címkét a profil adott informatikai csoportokra való szűréséhez, például `US-NC IT Team` vagy `JohnGlenn_ITDepartment`. A hatókör-címkékkel kapcsolatos további információkért lásd: [a RBAC és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

    Válassza a **Tovább** elemet.

11. A **hozzárendelések**területen válassza ki azokat a felhasználókat vagy csoportokat, akik megkapják a profilt. Rendeljen hozzá egy profilt az egyes eszközökhöz. A OEMConfig-modell csak egy házirendet támogat eszközönként.

    A profilok hozzárendelésével kapcsolatos további információkért lásd: [felhasználói és eszköz-profilok társítása](device-profile-assign.md).

    Válassza a **Tovább** elemet.

12. A **felülvizsgálat + létrehozás**lapon tekintse át a beállításokat. A **Létrehozás**gombra kattintva a rendszer menti a módosításokat, és hozzárendeli a profilt. A szabályzat a profilok listában is megjelenik.

Amikor az eszköz legközelebb megkeresi a konfigurációs frissítéseket, a rendszer a OEMConfig alkalmazásra alkalmazza a beállított SZÁMÍTÓGÉPGYÁRTÓi beállításokat.

> [!NOTE]
> A OEMConfig standard jelenleg nem tartalmazza az állapotjelentések bejelentését. A profilok alapértelmezés szerint **függő** állapotot jelenítenek meg.

## <a name="supported-oemconfig-apps"></a>Támogatott OEMConfig-alkalmazások

A standard szintű alkalmazásokhoz képest a OEMConfig-alkalmazások kibővítik a Google által az összetettebb sémák támogatásához biztosított felügyelt konfigurációkra vonatkozó jogosultságokat. Az Intune jelenleg a következő OEMConfig-alkalmazásokat támogatja:

-----------------

| OEM | Csomagazonosító | OEM-dokumentáció (ha elérhető) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. kpu | [A Knox szolgáltatás beépülő moduljának rendszergazdai útmutatója](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra-technológiák | com. zebra. oemconfig. Common | [A zebra OEMConfig áttekintése](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [A Datalogic OEMConfig felhasználói dokumentációja](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisedeviceconfig |  |
| Spectralink – vonalkódok | com. Spectralink. vonalkód. szolgáltatás |  |
| Spectralink – gombok | com. Spectralink. Buttons |  |
| Spectralink – eszköz | com. Spectralink. slnkdevicesettings  |  |
| Spectralink – naplózás | com. Spectralink. slnklogger |  |
| Spectralink - VQO | com. Spectralink. slnkvqo |  |

-----------------

Ha létezik egy OEMConfig-alkalmazás az eszközhöz, de nem szerepel a fenti táblázatban, vagy nem jelenik meg az Intune-konzolon, akkor az e-mail-`IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> A OEMConfig-alkalmazásokat az Intune-nak kell bejelentkeznie ahhoz, hogy OEMConfig-profilokkal lehessen konfigurálni őket. Az alkalmazások támogatása után nem kell felvennie a kapcsolatot a Microsofttal a bérlőben való beállításával kapcsolatban. Csak kövesse az ezen az oldalon található utasításokat.

## <a name="next-steps"></a>További lépések

[A profil állapotának figyelése](device-profile-monitor.md).
