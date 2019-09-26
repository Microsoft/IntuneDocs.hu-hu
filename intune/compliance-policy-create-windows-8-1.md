---
title: Windows 8,1 megfelelőségi beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg a Windows 8,1 és Windows Phone-telefon 8,1 rendszerű eszközök megfelelőségének beállításakor használható beállítások listáját Microsoft Intuneban. Győződjön meg arról, hogy megfelel a minimális és a maximális operációs rendszernek, a jelszó korlátozásának és hosszának beállítása, a titkosítás engedélyezése az adattárolásban és egyebek.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57a860edd99bfbbd41ff7df8fd98d0343f4f5ba6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304116"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 8,1 beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk felsorolja és ismerteti a Windows 8,1-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja az egyszerű jelszavak letiltásához, az operációs rendszer minimális és maximális verziójának beállításához, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- Windows Phone 8.1
- Windows 8.1 és újabb

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza a **Windows Phone-telefon 8,1** vagy **a Windows 8,1 és újabb**lehetőséget.

## <a name="device-properties"></a>Eszköztulajdonságok

- Az **operációs rendszer minimuma szükséges**: Adja meg a minimálisan engedélyezett verziót. Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximálisan engedélyezett operációsrendszer-verzió**: Adja meg a maximálisan engedélyezett verziót. Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak ekkor az informatikai rendszergazdához kell fordulnia. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg meg nem változtatja a szabályt az operációs rendszer verziójának engedélyezéséhez.

Windows 8.1-es számítógépek esetén például a visszaadott verzió a **3**-as. Ha az operációs rendszer verziójának szabálya Windows 8,1 for Windows, akkor az eszköz akkor is nem megfelelőként lesz jelezve, ha az eszközön Windows 8,1 van.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Windows 10

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: A **felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.
- **Egyszerű jelszavak**: A **Letiltás** beállítás megadása esetén a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó minimális hossza**: Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.

  Windows rendszerű, Microsoft-fiókon keresztül elért eszközök esetén a megfelelőségi szabályzat nem lesz helyesen kiértékelve:
  - Ha a jelszó minimális hossza nyolc karakternél nagyobb
  - Vagy ha a karakterkészletek minimális száma kettőnél több

- **Jelszó típusa**: Válassza ki, hogy a jelszó csak **numerikus** karakterekből álljon-e, vagy számokból és más karakterből (**alfanumerikus**) kell állnia.
  
  - **Nem alfanumerikus karakterek száma a jelszóban**: Ha a **Jelszó kötelező** típusa **Alfanumerikus**, ez a beállítás határozza meg a jelszóban szereplő karakterkészletek minimális számát. A négy karakterkészlet a következő:
    - Kisbetűk
    - Nagybetűk
    - Szimbólumok
    - Számok

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk. A Microsoft-fiókhoz hozzáférő eszközök esetén a megfelelőségi szabályzat kiértékelése nem megfelelő:

    - Ha a jelszó minimális hossza nyolc karakternél nagyobb
    - Vagy ha a karakterkészletek minimális száma meghaladja a kettőt

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : Válassza ki, hogy hány nap elteltével járjon le a jelszó, és egy újat kell létrehoznia.
- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**: Adja meg a nem használható korábban használt jelszavak számát.

### <a name="encryption"></a>Encryption

- **Titkosítás megkövetelése mobileszközön**: Az eszköz titkosításának **megkövetelése** az adattárolási erőforrásokhoz való kapcsolódáshoz.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 10-es és újabb rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows.md) .