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
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 322d6f1e23464f1f75cc79346d839a9ccdbd7bc7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504638"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 8,1 beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és ismerteti a Windows 8,1-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja az egyszerű jelszavak letiltásához, az operációs rendszer minimális és maximális verziójának beállításához, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- WVPN-profilokdows Phone 8.1
- Windows 8.1 és újabb

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza a **Windows Phone-telefon 8,1** vagy **a Windows 8,1 és újabb**lehetőséget.

## <a name="device-properties"></a>Eszköztulajdonságok

- Az **operációs rendszer szükséges minimális**verziója: adja meg a minimálisan engedélyezett verziót. Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximálisan engedélyezett operációsrendszer-verzió**: adja meg a maximálisan engedélyezett verziót. Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg meg nem változtatja a szabályt az operációs rendszer verziójának engedélyezéséhez.

Windows 8.1-es számítógépek esetén például a visszaadott verzió a **3**-as. Ha az operációs rendszer verziójának szabálya Windows 8,1 for Windows, akkor az eszköz akkor is nem megfelelőként lesz jelezve, ha az eszközön Windows 8,1 van.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez.
- **Egyszerű jelszavak**: Ha nem szeretné engedélyezni, hogy a felhasználók olyan egyszerű jelszavakat használhassanak, mint az **1234** vagy az **1111**, válassza a **Tiltás** lehetőséget. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó minimális hossza**: Meghatározhatja a jelszóban szereplő számjegyek vagy karakterek minimális számát.

  Windows rendszerű, Microsoft-fiókon keresztül elért eszközök esetén a megfelelőségi szabályzat nem lesz helyesen kiértékelve:
  - Ha a jelszó minimális hossza nyolc karakternél nagyobb
  - Vagy ha a karakterkészletek minimális száma kettőnél több

- **Jelszó típusa**: Megadható, hogy a jelszó csak **számjegy** karaktereket vagy számjegy és más (**Alfanumerikus**) karaktereket vegyesen tartalmazzon.
  
  - **Jelszavak nem alfanumerikus karaktereinek száma:** Ha a **Megkövetelt jelszótípus** **alfanumerikus**, ez a beállítás határozza meg a jelszóban használandó karakterkészletek minimális számát. A négy karakterkészlet a következő:
    - Kisbetűk
    - Nagybetűk
    - Szimbólumok
    - Számok

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk. A Microsoft-fiókhoz hozzáférő eszközök esetén a megfelelőségi szabályzat kiértékelése nem megfelelő:

    - Ha a jelszó minimális hossza nyolc karakternél nagyobb
    - Vagy ha a karakterkészletek minimális száma meghaladja a kettőt

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : Válassza ki, hány nap elteltével járjon le a jelszó, ami után újat kell létrehoznia.
- Az **újrafelhasználást megakadályozó korábbi jelszavak száma**: megadhatja, hogy hány korábban használt jelszót ne lehessen használni.

### <a name="encryption"></a>Encryption

- **Titkosítás megkövetelése mobileszközön:** : **Megkövetelhető**, hogy az eszközök csak titkosítás használata esetén csatlakozhassanak az adattároló erőforrásokhoz.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 10-es és újabb rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows.md) .