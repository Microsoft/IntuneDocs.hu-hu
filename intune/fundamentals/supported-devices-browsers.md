---
title: A Microsoft Intune által támogatott operációs rendszerek és böngészők
titleSuffix: ''
description: Felsorolja az Intune-eszközkezelés támogatott eszköz platformját és böngészőit
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d2777f2caabc24a457fc407b3e47facb1f6fc3c
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314617"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Az Intune-ban támogatott operációs rendszerek és böngészők

A Microsoft Intune beállítása előtt tekintse át a támogatott operációs rendszereket és böngészőket.

Az Intune az eszközön való telepítésével kapcsolatos segítségért lásd: a [felügyelt eszközök használata a munkavégzéshez és az](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) [Intune hálózati sávszélesség-használathoz](network-bandwidth-use.md).

A konfigurációs szolgáltató támogatásával kapcsolatos további információkért látogasson el a konfigurációs szolgáltatói [referenciára](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="intune-supported-operating-systems"></a>Intune által támogatott operációs rendszerek

A következő operációs rendszereket futtató eszközöket kezelheti:

[!INCLUDE [mdm-supported-devices](../../intune-classic/includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Támogatott Samsung Knox standard-eszközök

A MDM-regisztrációt megakadályozó Knox-aktiválási hibák elkerülése érdekében az Céges portál alkalmazás csak akkor kísérli meg a Samsung Knox-aktiválást a MDM-regisztráció során, ha az eszköz megjelenik a [támogatott Knox-eszközök listáján](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Azok az eszközök, amelyek nem támogatják a Samsung Knox-aktiválást, szabványos Android-eszközökként regisztrálhatnak. Előfordulhat, hogy egy Samsung-eszköz bizonyos modelljei támogatják a Knox-t, míg mások nem. A Samsung-eszközök megvásárlása és üzembe helyezése előtt ellenőrizze, hogy a Knox kompatibilis-e az eszköz viszonteladóval.

> [!NOTE]
> Előfordulhat, hogy a Samsung Knox-eszközök regisztrálásához engedélyeznie kell a [Samsung-kiszolgálókhoz való hozzáférést](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

Az alábbi Samsung-eszközök listája nem támogatja a Knox-t. Natív Android-eszközként vannak regisztrálva az Androidhoz készült Céges portál alkalmazásban:

| **Eszköz neve** | **Eszközök modelljeinek száma** |
| --- | --- |
| Galaxy Avant | SM – G386T |
| Galaxy Core 2/Core 2 Duó | SM – G355H<br>SM – G355M |
| Galaxy Core Lite | SM – G3588V |
| Galaxy Core Prime | SM – G360H |
| Galaxy Core LTE | SM – G386F<br>SM – G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM – G7200 |
| Galaxy Grand neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM – G531H |
| Galaxy J Max | SM – T285YD |
| Galaxy J1 | SM – J100H<br>SM – J100M<br>SM – J100ML |
| Galaxy J1 Ace | SM – J110F<br>SM – J110H |
| Galaxy J1 mini | SM – J105M |
| Galaxy J2/J2 Pro | SM – J200H<br>SM – J210F |
| Galaxy J3 | SM – J320F<br>SM – J320FN<br>SM – J320H<br>SM – J320M |
| Galaxis K nagyítása | SM – C115 |
| Galaxy Light | SGH – T399N |
| 3\. Megjegyzés: Galaxy | SM – N9002<br>SM – N9009 |
| Galaxy Megjegyzés 7/Megjegyzés 7 duó | SM – N930S<br>SM – N9300<br>SM – N930F<br>SM – N930T<br>SM – N9300<br>SM – N930F<br>SM – N930S<br>SM – N930T |
| Galaxy Megjegyzés 10,1 3G | SM – P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxis S3 mini | SM – G730A<br>SM – G730V |
| Galaxis S3 neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM – S975L |
| Galaxy S4 neo | SM – G318ML |
| Galaxy S5 | SM – G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0 @ no__t-0 | SM – T280<br>SM – T285 |
| Galaxy Tab 3 7 @ no__t-0/Tab 3 Lite 7 @ no__t-1 | SM – T116<br>SM – T210<br>SM – T211 |
| Galaxy Tab 3 8.0 @ no__t-0 | SM – T311 |
| Galaxy Tab 3 10.1 @ no__t-0 | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy trend 2 Lite | SM – G318H |
| Galaxy V Plus | SM – G318HZ |
| Galaxy Young 2 Duó | SM – G130BU |


### <a name="windows-pc-software-client"></a>Windows rendszerű számítógép ügyfélszoftvere

Az [Intune-ügyfélszoftverek](../manage-windows-pcs-with-microsoft-intune.md) a Windows rendszerű számítógépekre is telepíthetők és telepíthetők alternatív regisztrációs módszerként. Ez a funkció csak a klasszikus Intune-portálon érhető el. Az Intune-ügyfélszoftver használatával a Windows 7 és újabb rendszerű számítógépeket kezelheti a Windows 10 Home Edition kivételével.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune által támogatott böngészők

A különböző felügyeleti feladatok elvégzéséhez a következő felügyeleti webhelyek egyikét kell használnia.

- [Microsoft 365 felügyeleti központ](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portalra](https://portal.azure.com/)

Ezek a portálok a következő böngészőkkel támogatottak:
- Microsoft Edge (legújabb verzió)
- Microsoft Internet Explorer 11
- Safari (csak a legújabb verzió, csak Mac)
- Chrome (legújabb verzió)
- Firefox (legújabb verzió)




### <a name="intune-classic-portal"></a>Klasszikus Intune-portál

A klasszikus Intune-portált csak az Intune PC szoftverrel rendelkező ügyfélszoftverrel regisztrált eszközök kezelésére használjuk (https://manage.microsoft.com). A klasszikus Intune-portálon a Silverlight böngésző támogatására van szükség.

A következő Silverlight-böngészők támogatják az Intune-konzolt:
- Internet Explorer 10 vagy újabb
- Google Chrome (42-es verziónál korábbi verziók)
- Mozilla Firefox – Silverlight engedélyezve (56-es verziónál korábbi verziók)

> [!Note]
> A Microsoft Edge és a Mobile böngészők nem támogatottak a klasszikus Intune-portálon, mert nem támogatják a [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx)szoftvert.

Csak a szolgáltatás-rendszergazdai jogosultságokkal rendelkező felhasználók és a globális rendszergazdai szerepkörrel rendelkező bérlői rendszergazdák jelentkezhetnek be a portálra. A felügyeleti konzol eléréséhez a fióknak rendelkeznie kell az Intune használatához szükséges licenccel, illetve **engedélyezett**bejelentkezési állapottal.
