---
title: A OEMConfig használata androidos vállalati eszközökön Microsoft Intune-Azure-ban | Microsoft Docs
description: Az OEMConfig használatával az Android Enterprise rendszert futtató eszközöket a Microsoft Intune segítségével kezelheti és használhatja. Tekintse meg az összes lépést, beleértve az áttekintést, az előfeltételek, a konfigurációs profil létrehozása az Intune-ban című témakört, és tekintse meg a támogatott OEMConfig-alkalmazások listáját.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c46caf4d1c9f9a32a7f324fc5e1734dbe8043bd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730959"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Androidos nagyvállalati eszközök használata és kezelése a OEMConfig-ben Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Microsoft Intune a OEMConfig használatával adhat hozzá, hozhat létre és szabhat testre OEM-specifikus beállításokat az androidos vállalati eszközökhöz. A OEMConfig általában az Intune-ban nem beépített beállítások konfigurálására szolgálnak. Az eredeti berendezésgyártó (OEM) különböző beállításokat tartalmaz. Az elérhető beállítások attól függnek, hogy az OEM milyen tartalmakat tartalmaz a OEMConfig alkalmazásban.

Ez a funkció az alábbiakra vonatkozik:  

- Vállalati Android

Ez a cikk a OEMConfig ismerteti, felsorolja az előfeltételeket, bemutatja, hogyan hozhat létre konfigurációs profilt, és listázza a támogatott OEMConfig-alkalmazásokat az Intune-ban.

## <a name="overview"></a>Áttekintés

A OEMConfig szabályzatok az [alkalmazás-konfigurációs házirendhez](../apps/app-configuration-policies-overview.md)hasonló speciális típusú eszköz-konfigurációs házirend. A OEMConfig egy, a Google által meghatározott szabvány, amely az alkalmazások konfigurációját használja az Androidban az eszközök beállításainak az OEM-ek által írt alkalmazásokba való küldéséhez (eredeti berendezésgyártó). Ez a szabvány lehetővé teszi, hogy a számítógépgyártók és a EMMs (nagyvállalati mobilitási felügyelet) szabványosított módon hozzanak létre és támogassák az OEM-specifikus szolgáltatásokat. [További információ a OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

A EMMs, például az Intune, az OEM-specifikus funkciók támogatását manuálisan is kiépítheti, miután a számítógépgyártó bevezette őket. Ez a megközelítés ismétlődő erőfeszítéseket és lassú bevezetést eredményez.

A OEMConfig esetében az OEM egy olyan sémát hoz létre, amely az OEM-specifikus felügyeleti funkciókat definiálja. Az OEM beágyazza a sémát egy alkalmazásba, majd ezt az alkalmazást a Google Play webhelyen helyezi el. Az az alkalmazásból beolvassa a sémát, és elérhetővé teszi a sémát a az a-ben lévő, a (az A konzol lehetővé teszi az Intune-rendszergazdák számára a séma beállításainak konfigurálását.

Amikor a OEMConfig alkalmazást telepíti egy eszközre, az a következő beállításokkal kezeli az eszközt: Az eszköz beállításait a OEMConfig alkalmazás hajtja végre, nem pedig az MDM-ügynök által készített,

Ha az OEM hozzáadja és javítja a felügyeleti funkciókat, az OEM az alkalmazást a Google Play áruházban is frissíti. Rendszergazdaként ezeket az új szolgáltatásokat és frissítéseket (beleértve a javításokat is) úgy érheti el, hogy a EMMs-re való várakozás nélkül is felveszi ezeket a frissítéseket.

> [!TIP]
> A OEMConfig csak olyan eszközökkel használható, amelyek támogatják ezt a funkciót, és rendelkeznek egy megfelelő OEMConfig-alkalmazással. További részletekért forduljon az OEM-hez.

## <a name="before-you-begin"></a>Előkészületek

A OEMConfig használatakor vegye figyelembe a következő információkat:

- Az Intune elérhetővé teszi a OEMConfig alkalmazás sémáját, hogy beállítsa. Az Intune nem ellenőrzi vagy nem módosítja az alkalmazás által biztosított sémát. Így ha a séma helytelen, vagy pontatlan adatmennyiséggel rendelkezik, ezeket az adatait a rendszer továbbra is elküldi az eszközöknek. Ha olyan problémát talál, amely a sémából származik, forduljon az OEM-hez útmutatásért.
- Az Intune nem befolyásolja vagy szabályozza az alkalmazás sémájának tartalmát. Az Intune például nem rendelkezik a karakterláncok, a nyelv, az engedélyezett műveletek és így tovább. Javasoljuk, hogy vegye fel a kapcsolatot az OEM-vel az eszközök OEMConfig-vel való kezelésével kapcsolatos részletekért és ajánlott eljárásokhoz.
- A számítógépgyártók bármikor frissíthetik a támogatott szolgáltatásokat és sémákat, és új alkalmazást tölthetnek fel a Google Play áruházba. Az Intune mindig szinkronizálja a OEMConfig alkalmazás legújabb verzióját a Google Play áruházból. Az Intune nem tartja karban a séma vagy az alkalmazás régebbi verzióit. Ha a verziószáma ütközik, javasoljuk, hogy további információért forduljon az OEM-hez.
- Rendeljen egy OEMConfig-profilt egy eszközhöz. Ha ugyanahhoz az eszközhöz több profil is hozzá van rendelve, akkor inkonzisztens viselkedést tapasztalhat. A OEMConfig-modell csak egyetlen házirendet támogat eszközönként.

## <a name="prerequisites"></a>Előfeltételek

A OEMConfig eszközön való használatához győződjön meg arról, hogy rendelkezik a következő követelményekkel:

- Az Intune-ban regisztrált androidos vállalati eszköz.
- Az OEM által készített OEMConfig-alkalmazás, amelyet a Google Play áruházba töltöttek fel. Ha nem a Google Play áruházban van, további információért forduljon az OEM-hez.
- Az Intune rendszergazdája szerepköralapú hozzáférés-vezérlési (RBAC) engedélyekkel rendelkezik a **Mobile apps** és a **DeviceConfigurations**számára. Ezek az engedélyek azért szükségesek, mert a OEMConfig-profilok felügyelt alkalmazás-konfigurációkat használnak az eszközök konfigurációjának kezeléséhez.

## <a name="prepare-the-oemconfig-app"></a>A OEMConfig alkalmazás előkészítése

Győződjön meg arról, hogy az eszköz támogatja a OEMConfig, a megfelelő OEMConfig-alkalmazást adja hozzá az Intune-hoz, és az alkalmazás telepítve van az eszközön. Ehhez az információhoz forduljon az OEM-hez.

> [!TIP] 
> A OEMConfig-alkalmazások az OEM-re jellemzőek. Egy Zebra Technologies-eszközre telepített Sony OEMConfig-alkalmazás például nem csinál semmit.

1. Szerezze be a OEMConfig alkalmazást a felügyelt Google Play Áruház. [Felügyelt Google Play-alkalmazások hozzáadása Android Enterprise-eszközökhöz](../apps/apps-add-android-for-work.md) a lépések felsorolása.
2. Egyes számítógépgyártók előre telepített OEMConfig-alkalmazással is eldönthetik az eszközök szállítását. Ha az alkalmazás nincs előtelepítve, az Intune használatával [adhatja hozzá és helyezheti üzembe az alkalmazást az eszközökön](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>OEMConfig-profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adjon meg egy leíró nevet az új profilhoz.
    - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza az **Android Enterprise**lehetőséget.
    - **Profil típusa**: Válassza a **OEMConfig**lehetőséget.

4. Válassza a **társított alkalmazás**lehetőséget, válassza ki a korábban hozzáadott meglévő OEMConfig-alkalmazást > **OK gombra**. Ügyeljen arra, hogy a megfelelő OEMConfig-alkalmazást válassza ki azokhoz az eszközökhöz, amelyekre a szabályzatot hozzárendeli.

    Ha nem látja a felsorolt alkalmazásokat, akkor állítsa be a felügyelt Google Play áruházat, és szerezze be az alkalmazásokat a felügyelt Google Play áruházból. [Felügyelt Google Play-alkalmazások hozzáadása Android Enterprise-eszközökhöz](../apps/apps-add-android-for-work.md) a lépések felsorolása.

    > [!IMPORTANT]
    > Ha egy OEMConfig-alkalmazást adott hozzá, és szinkronizálta azt a Google Play-be, de nem szerepel a **társított alkalmazásban**, akkor előfordulhat, hogy kapcsolatba kell lépnie az Intune-nal az alkalmazás bevezetéséhez. Lásd: [új alkalmazás hozzáadása](#supported-oemconfig-apps) (ebben a cikkben).

5. A **beállítások konfigurálása**a alkalmazásban területen válassza a **Configuration Designer** vagy a **JSON-szerkesztő**használatát:

    > [!TIP]
    > Olvassa el az OEM dokumentációját, és győződjön meg róla, hogy helyesen konfigurálja a tulajdonságokat. Ezeket az alkalmazás-tulajdonságokat az OEM, nem pedig az Intune tartalmazza. Az Intune minimálisan ellenőrzi a tulajdonságokat, vagy a beírt értéket. Ha például egy portszámot ad `abcd` meg, a profil a-ként lesz mentve, és az eszközön a konfigurált értékekkel lesz telepítve. Ügyeljen arra, hogy a helyes adatokat adja meg.

    - **Konfigurációs tervező**: Ha ezt a beállítást választja, az alkalmazás sémáján belül elérhető tulajdonságok is megjelennek a konfiguráláshoz.

      - A Configuration Designer helyi menüi azt jelzik, hogy több lehetőség is rendelkezésre áll. A helyi menü például lehetővé teheti a beállítások hozzáadását, törlését és átrendezését. Ezeket a beállításokat a SZÁMÍTÓGÉPGYÁRTÓ is tartalmazza. Olvassa el az OEM-alkalmazás dokumentációját, amelyből megtudhatja, hogyan kell használni ezeket a beállításokat a profilok létrehozásához.

      - Számos beállításhoz az OEM által megadott alapértelmezett értékek tartoznak. Ha meg szeretné tekinteni, hogy van-e alapértelmezett érték, vigye a kurzort a beállítás melletti információs ikonra. Az elemleírás az adott beállítás alapértelmezett értékeit (ha alkalmazható) és az OEM által biztosított további részleteket jeleníti meg.

      - A **Törlés** gombra kattintva törölheti a beállításokat a profilból. Ha egy beállítás nincs a profilban, az eszköz értéke nem változik a profil alkalmazása után.
        
      - Ha üres (nem konfigurált) köteget hoz létre a Configuration Designerben, a rendszer törli a JSON-szerkesztőre való áttéréskor.

    - **JSON-szerkesztő**: Ha ezt a beállítást választja, a rendszer egy JSON-szerkesztőt nyit meg az alkalmazásban beágyazott teljes konfigurációs sémához tartozó sablonnal. A szerkesztőben szabja testre a sablont a különböző beállítások értékeivel. Ha a **Configuration Designer** használatával módosítja az értékeket, a JSON-szerkesztő felülírja a sablont a Configuration Designer értékével.
    
      - Ha meglévő profilt frissít, a JSON-szerkesztő megjeleníti azokat a beállításokat, amelyek utoljára mentve lettek a profillal.

      - A OEMConfig sémái nagyok és összetettebbek lehetnek. Ha egy másik szerkesztő használatával szeretné frissíteni ezeket a beállításokat, válassza a **JSON-sablon letöltése** gombot. Az Ön által választott szerkesztővel adhatja hozzá a konfigurációs értékeket a sablonhoz. Ezután másolja és illessze be a frissített JSON-t a **JSON-szerkesztő** tulajdonságba.

      - A JSON-szerkesztő segítségével biztonsági másolatot készíthet a konfigurációról. Miután konfigurálta a beállításokat, ezzel a funkcióval lekérheti a JSON-beállításokat az értékekkel. Másolja és illessze be a JSON-fájlt egy fájlba, és mentse. Most már van egy biztonságimásolat-fájlja.

    A Configuration Designerben végrehajtott módosítások a JSON-szerkesztőben is automatikusan megtörténik. Hasonlóképpen, a JSON-szerkesztőben végrehajtott módosítások automatikusan a Configuration Designerben történnek. Ha a bemenet érvénytelen értékeket tartalmaz, nem válthat a Configuration Designer és a JSON-szerkesztő között, amíg ki nem javítja a problémákat.

6. A módosítások mentéséhez kattintson **az OK** > **Hozzáadás** gombra. Ekkor létrejön a szabályzat, és megjelenik a listában.

Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

 > [!NOTE]
 > Rendeljen hozzá egy profilt az egyes eszközökhöz. A OEMConfig-modell csak egy házirendet támogat eszközönként.

Amikor az eszköz legközelebb megkeresi a konfigurációs frissítéseket, a rendszer a OEMConfig alkalmazásra alkalmazza a beállított SZÁMÍTÓGÉPGYÁRTÓi beállításokat.

> [!NOTE]
> A OEMConfig standard jelenleg nem tartalmazza az állapotjelentések bejelentését. A profilok alapértelmezés szerint **függő** állapotot jelenítenek meg.

## <a name="supported-oemconfig-apps"></a>Támogatott OEMConfig-alkalmazások

A standard szintű alkalmazásokhoz képest a OEMConfig-alkalmazások kibővítik a Google által az összetettebb sémák támogatásához biztosított felügyelt konfigurációkra vonatkozó jogosultságokat. Az Intune jelenleg a következő OEMConfig-alkalmazásokat támogatja:

-----------------

| OEM | Csomagazonosító | OEM-dokumentáció (ha elérhető) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [A Knox szolgáltatás beépülő moduljának rendszergazdai útmutatója](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Zebra-technológiák | com. zebra. oemconfig. Common | [A zebra OEMConfig áttekintése](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [A Datalogic OEMConfig felhasználói dokumentációja](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |

-----------------

Ha létezik egy OEMConfig-alkalmazás az eszközhöz, de nem szerepel a fenti táblázatban, vagy nem jelenik meg az Intune-konzolon, küldjön `IntuneOEMConfig@microsoft.com`e-mailt.

> [!NOTE]
> A OEMConfig-alkalmazásokat az Intune-nak kell bejelentkeznie ahhoz, hogy OEMConfig-profilokkal lehessen konfigurálni őket. Az alkalmazások támogatása után nem kell felvennie a kapcsolatot a Microsofttal a bérlőben való beállításával kapcsolatban. Csak kövesse az ezen az oldalon található utasításokat.

## <a name="next-steps"></a>További lépések

- [Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
