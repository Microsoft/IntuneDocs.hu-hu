---
title: iOS-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az iOS-eszközök megfelelőségének beállításakor használható összes beállítást Microsoft Intuneban. E-mail-cím, a feltört eszközök bejelölése, az engedélyezett minimális és maximális operációs rendszer beállítása, a jelszó korlátozásának beállítása, beleértve a jelszó hosszát és az eszköz inaktivitását, az alkalmazások korlátozását stb.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9bcfed67eda96bb4d79317bcc69d21a5f8197bc
ms.sourcegitcommit: 2b905913840d4133a7964fe4f54a58ea6e421e12
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2020
ms.locfileid: "77074631"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>iOS-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

Ez a cikk felsorolja és leírja az iOS-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal megkövetelheti, hogy az e-mailek, a feltört (feltört) eszközök nem megfelelőek legyenek, beállíthatja az engedélyezett veszélyforrásokat, beállíthatja a jelszavakat, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- iOS
- iPadOS

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza az **iOS/iPadOS**lehetőséget.

## <a name="email"></a>E-mail

- **Felügyelt e-mail-profillal rendelkező mobileszközök megkövetelése**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – az Intune által felügyelt e-mail-profillal nem rendelkező eszközök nem megfelelőnek minősülnek. Egy eszköz nem rendelkezhet felügyelt e-mail-profillal, ha nem megfelelően van megcélozva, vagy ha a felhasználó manuálisan állítja be az e-mail-fiókot az eszközön.

  Az eszköz nem megfelelőnek minősül a következő helyzetekben:  
  - Az e-mail-profil egy másik felhasználói csoporthoz van rendelve, mint a megfelelőségi szabályzat által megcélozott felhasználói csoport.
  - A felhasználó már beállított egy olyan e-mail fiókot az eszközön, amely megfelel az eszközre telepített Intune e-mail profilnak. Az Intune nem írhatja felül a felhasználó által konfigurált profilt, és az Intune nem tudja kezelni azt. A megfelelőség érdekében a felhasználónak el kell távolítania a meglévő e-mail-beállításokat. Ezt követően az Intune képes lesz a felügyelt e-mail-profil telepítésére.  

A levelezési profilokkal kapcsolatos további információkért lásd: a [vállalati levelezéshez való hozzáférés konfigurálása e-mail-profilok használatával az Intune-](../configuration/email-settings-configure.md)nal.

## <a name="device-health"></a>Eszköz állapota

- Feltört **eszközök**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Blokkolt** feltört (feltört) eszközök nem megfelelőként való megjelölése.  

- **Az eszköznek a veszélyforrások szintjén vagy alatt kell lennie** *(iOS 8,0 és újabb)* :  
  Ezzel a beállítással a kockázatértékelés feltételként tekintheti meg a kockázat értékelését. Az engedélyezett veszélyforrások szintjének kiválasztása:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Biztonságos** – ez a legbiztonságosabb beállítás, ami azt jelenti, hogy az eszközhöz nem tartozhat fenyegetés. Ha az eszköz bármilyen szintű fenyegetést észlel, azt a rendszer nem megfelelőként értékeli.
  - **Alacsony** – az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes** – az eszköz abban az esetben minősül megfelelőnek, ha az eszközön lévő fenyegetések alacsony vagy közepes szintűek. Ha az eszköz magas szintű fenyegetéseket észlel, azt a rendszer nem megfelelőként határozza meg.
  - **Magas** – ez a legkevésbé biztonságos beállítás, mivel az összes veszélyforrást engedélyezi. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

## <a name="device-properties"></a>Eszköztulajdonságok

### <a name="operating-system-version"></a>Operációs rendszer verziója  

- **Operációs rendszer minimális verziója** *(iOS 8,0 és újabb)* :  
  Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. Ezután hozzáférhetnek a szervezeti erőforrásokhoz.

- **Maximális operációsrendszer-verzió** *(iOS 8,0 és újabb)* :  
  Ha egy eszköz a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg egy szabály nem változik, hogy az operációs rendszer verziója engedélyezve legyen.

- **Operációsrendszer-Build minimális verziója** *(iOS 8,0 és újabb)* :  
  Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ez a funkció használatával adja meg a minimális megengedett buildszám az eszközön.

- **Operációsrendszer-Build maximális verziója** *(iOS 8,0 és újabb)* :  
  Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ez a funkció használatával adja meg a maximális megengedett buildszám az eszközön.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Windows 10

> [!NOTE]
> Miután megfelelőségi vagy konfigurációs szabályzatot alkalmazott egy iOS-eszközre, a felhasználóktól 15 percenként egy PIN-kódot kér a rendszer. A kérések mindaddig megjelennek, amíg a felhasználó meg nem ad egy PIN-kódot. Ha az iOS-eszközhöz PIN-kód van beállítva, a titkosítási folyamat automatikusan elindul. Az eszköz mindaddig titkosítva marad, amíg le nem tiltja a PIN-kódot.

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.  
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. A jelszót használó iOS-eszközöket titkosítja a rendszer.

- **Egyszerű jelszavak**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a felhasználók létrehozhatnak olyan egyszerű jelszavakat, mint a **1234** vagy a **1111**.
  - **Letiltás** – a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**. 

- **Jelszó minimális hossza**:  
  Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.  

- **Szükséges jelszó típusa**:  
  Válassza ki, hogy a jelszó csak **numerikus** karakterekből álljon-e, vagy számokból és más karakterből (**alfanumerikus**) kell állnia.

- **Nem alfanumerikus karakterek száma a jelszóban**:  
  Adja meg a speciális karakterek minimális számát (például `&`, `#`, `%`, `!`stb.), amelynek a jelszónak kell lennie. 

  Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk.

- **Jelszó kérése a képernyő zárolása után legfeljebb perccel** *(iOS 8,0 és újabb)* :  
  Adja meg, hogy a képernyő után milyen gyorsan legyen zárolva, mielőtt a felhasználónak jelszót kell megadnia az eszköz eléréséhez. A lehetőségek közé tartozik a *nem konfigurált*, *azonnal*és *1 perc* és *4 óra*közötti alapértelmezett érték.

- **A képernyőfelvételek legfeljebb ennyi perc inaktivitás**után:  
  Adja meg azt az üresjárati időt, ameddig az eszköz zárolja a képernyőt. A beállítások közé tartozik az alapértelmezett *nincs konfigurálva*, *azonnal*, és *1 perc* és *15 perc*között.

- **Jelszó érvényessége (napokban)** :  
  Válassza ki, hogy hány nap elteltével járjon le a jelszó, és egy újat kell létrehoznia. 

- Az **újrafelhasználást megakadályozó korábbi jelszavak száma** *(iOS 8,0 és újabb)* :   
  Adja meg a nem használható korábban használt jelszavak számát.

### <a name="device-security"></a>Eszközbiztonság

- **Korlátozott alkalmazások**:  
  Alkalmazásokat úgy korlátozhat, hogy kötegazonosítójukat hozzáadja a szabályzathoz. Ha egy eszközön telepítve van az alkalmazás, az eszköz nem megfelelőként van megjelölve.

  - **Alkalmazás neve** – adjon meg egy felhasználóbarát nevet, amely segít a csomag azonosítójának azonosításában.
  - Alkalmazáscsomag **azonosítója** – adja meg az alkalmazás-szolgáltató által hozzárendelt egyedi köteg azonosítóját. A csomag AZONOSÍTÓjának megkereséséhez lásd: [az iOS-alkalmazáshoz tartozó csomag azonosítójának megkeresése](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (egy másik Microsoft-webhely megnyitása).  

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Lásd: [MacOS-eszközök megfelelőségi szabályzatának beállításai](compliance-policy-create-mac-os.md) .
