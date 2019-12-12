---
title: Windows 8,1 megfelelőségi beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg a Windows 8,1 és Windows Phone-telefon 8,1 rendszerű eszközök megfelelőségének beállításakor használható beállítások listáját Microsoft Intuneban. Győződjön meg arról, hogy megfelel a minimális és a maximális operációs rendszernek, a jelszó korlátozásának és hosszának beállítása, a titkosítás engedélyezése az adattárolásban és egyebek.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813210"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 8,1 beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

Ez a cikk felsorolja és ismerteti a Windows 8,1-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja az egyszerű jelszavak letiltásához, az operációs rendszer minimális és maximális verziójának beállításához, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- WVPN-profilokdows Phone 8.1
- Windows 8.1 és újabb

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza a **Windows Phone-telefon 8,1** vagy **a Windows 8,1 és újabb**lehetőséget.

## <a name="device-properties"></a>Eszköztulajdonságok

### <a name="operating-system-version"></a>Operációs rendszer verziója

**Windows Phone 8,1 és újabb verziók**
- **Mobileszközök minimális operációsrendszer-verziója**:  
  Adja meg a minimálisan engedélyezett verziót. Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. Az eszköz a felhasználó dönthet úgy, hogy frissíti az eszközét, majd hozzáférést kap a vállalati erőforrásokhoz.

- **Mobileszközök maximális operációsrendszer-verziója**:  
  Adja meg a maximálisan engedélyezett verziót. Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. Az eszköz felhasználójának kapcsolatba kell lépnie a rendszergazdával. Az eszköz nem fér hozzá a szervezeti erőforrásokhoz, amíg egy szabály nem változik, hogy az operációs rendszer verziója engedélyezve legyen.

**Windows 8.1 és újabb**
- **Operációs rendszer minimális verziója**:  
  Adja meg a minimálisan engedélyezett verziót. Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. Az eszköz a felhasználó dönthet úgy, hogy frissíti az eszközét, majd hozzáférést kap a vállalati erőforrásokhoz.

- **Maximális operációsrendszer-verzió**:  
  Adja meg a maximálisan engedélyezett verziót. Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. Az eszköz felhasználójának kapcsolatba kell lépnie a rendszergazdával. Az eszköz nem fér hozzá a szervezeti erőforrásokhoz, amíg egy szabály nem változik, hogy az operációs rendszer verziója engedélyezve legyen.

Windows 8.1-es számítógépek esetén például a visszaadott verzió a **3**-as. Ha az operációs rendszer verziójának szabálya Windows 8,1 for Windows, akkor az eszköz akkor is nem megfelelőként lesz jelezve, ha az eszközön Windows 8,1 van.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.

- **Egyszerű jelszavak**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a felhasználók létrehozhatnak olyan egyszerű jelszavakat, mint a **1234** vagy a **1111**.
  - **Letiltás** – a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**.  

- **Jelszó minimális hossza**:  
  Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.

  A Windows rendszerű és a Microsoft-fiókt futtató eszközök esetén a megfelelőségi házirend kiértékelése nem megfelelő, ha a következő feltételek valamelyike teljesül:  
  - A jelszó minimális hossza nagyobb, mint nyolc karakter.
  - A karakterkészletek minimális száma meghaladja a kettőt

- **Jelszó típusa**:  
  Válassza ki, hogy a jelszó csak **numerikus** karakterekből álljon-e, vagy számokból és más karakterből (**alfanumerikus**) kell állnia.

  Ha *alfanumerikus*értékre van állítva, a következő beállítás érhető el.  

  - **Nem alfanumerikus karakterek száma a jelszóban**:  
    Ha a *jelszó típusa* **alfanumerikus**, adja meg a jelszóban szereplő karakterkészletek minimális számát. A beállítások **0** – **4** készletet tartalmaznak, amelyek alapértelmezett értéke **1**.
    
    A négy karakterkészlet a következő:
    - Kisbetűk
    - Nagybetűk
    - Szimbólumok
    - Számok

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk. A Microsoft-fiókkal elért eszközök esetén a megfelelőségi szabályzat nem lesz megfelelően kiértékelve, ha a következő feltételek valamelyike teljesül:

    - A jelszó minimális hossza nagyobb, mint nyolc karakter.
    - A karakterkészletek minimális száma meghaladja a kettőt

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**:  
  Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.

- **Jelszó érvényessége (napokban)** :  
  Válassza ki, hogy hány nap elteltével járjon le a jelszó, és a felhasználóknak újat kell létrehozniuk.

- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**:  
  Adja meg a nem használható korábban használt jelszavak számát.

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**:  
  - **Nincs konfigurálva** (*alapértelmezett*)
  - **Kötelező** – az adattárolást az eszközökön *titkosítani kell.*


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 10-es és újabb rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows.md) .