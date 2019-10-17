---
title: A Microsoft Intune által támogatott operációs rendszerek és böngészők
titleSuffix: ''
description: Az Intune-eszközkezelés által támogatott eszközplatformok és böngészők listája
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9fec08511303c15a7197014fd80834d95948191
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504884"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Az Intune-ban támogatott operációs rendszerek és böngészők

A Microsoft Intune beállítása előtt tekintse át a támogatott operációs rendszereket és böngészőket.

Az Intune az eszközön való telepítésével kapcsolatos segítségért lásd: a [felügyelt eszközök használata a munkavégzéshez és az](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) [Intune hálózati sávszélesség-használathoz](network-bandwidth-use.md).

A konfigurációs szolgáltató támogatásával kapcsolatos további információkért látogasson el a konfigurációs szolgáltatói [referenciára](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="intune-supported-operating-systems"></a>Az Intune által támogatott operációs rendszerek

Az alábbi operációs rendszereket használó eszközöket kezelheti:

[!INCLUDE [mdm-supported-devices](../../intune-classic/includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Támogatott Samsung Knox Standard-eszközök

Az MDM-regisztrálást megakadályozó Knox-aktiválási hibák elkerülése érdekében az MDM-regisztráció során a Céges portál alkalmazás csak akkor kísérli meg a Samsung Knox-aktiválást, ha az eszköz szerepel a [támogatott Knox-eszközök listáján](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Azokat az eszközöket, melyek nem támogatják a Samsung Knox-aktiválást, szabványos Android-eszközként regisztrálja a rendszer. Előfordulhat, hogy egy Samsung eszköz néhány modellje támogatja a Knox platformot, míg mások nem. Samsung-eszközök vásárlása és üzembe helyezése előtt egyeztesse az eszköz viszonteladójával, hogy az eszköz kompatibilis-e a KNOX-szal.

> [!NOTE]
> Előfordulhat, hogy a Samsung Knox-eszközök regisztrálásához [engedélyeznie kell a Samsung kiszolgálóinak elérését](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

Az alábbi Samsung-modellek nem támogatják a Knoxot. Ezeket az Androidhoz készült Céges portál alkalmazás natív Android-eszközként regisztrálja:

| **Eszköz neve** | **Eszköz modellszáma** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="windows-pc-software-client"></a>Windowsos számítógépeken futó szoftveres ügyfél

A windowsos számítógépekre a regisztráció alternatívájaként telepítheti az [Intune szoftveres ügyfelet](../manage-windows-pcs-with-microsoft-intune.md) is. Ez a funkció csak a klasszikus Intune-portálon érhető el. Az Intune szoftveres ügyfele segítségével a Windows 7 és újabb rendszerű számítógépeket felügyelheti (kivéve a Windows 10 Home verziót).

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Az Intune által támogatott webböngészők

A különféle felügyeleti tevékenységek elvégzésére a következő két felügyeleti webhely valamelyikét kell használnia.

- [Microsoft 365 felügyeleti központ](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portal](https://portal.azure.com/)

Ezeken a portálokon jelenleg a következő böngészők támogatottak:
- Microsoft Edge (legújabb verzió)
- Microsoft Internet Explorer 11
- Safari (csak Mac, legújabb verzió)
- Chrome (legújabb verzió)
- Firefox (legújabb verzió)




### <a name="intune-classic-portal"></a>Klasszikus Intune-portál

A klasszikus Intune-portált csak az Intune PC szoftverrel rendelkező ügyfélszoftverrel regisztrált eszközök kezelésére használjuk (https://manage.microsoft.com). A klasszikus Intune-portálhoz a böngésző Silverlight-támogatása szükséges.

A klasszikus Intune-portál a következő Silverlight-kompatibilis böngészőkkel használható:
- Internet Explorer 10 vagy újabb
- Google Chrome (42-es vagy korábbi verziók)
- Mozilla Firefox – Silverlight engedélyezve (56-es verziónál korábbi verziók)

> [!Note]
> A Microsoft Edge és a mobilböngészők a klasszikus Intune-portálhoz való használata nem támogatott, mivel nem támogatják a [Microsoft Silverlightot](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

A portálra szolgáltatás-rendszergazdák, valamint globális rendszergazda szerepkörrel rendelkező bérlői rendszergazdák jelentkezhetnek be. A felügyeleti konzol eléréséhez a fióknak az Intune használatához szükséges licenccel, illetve **Engedélyezett** bejelentkezési állapottal kell rendelkeznie.
