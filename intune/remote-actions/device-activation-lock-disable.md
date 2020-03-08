---
title: IOS/iPadOS Aktiválási zár mellőzése az Intune-nal
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan lehet az Intune használatával megkerülni az iOS/iPadOS Aktiválási zár a zárolt eszközök eléréséhez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a322788dba092f44af2f0664fe810f8392b9f56
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855983"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>A felügyelt iOS-/iPadOS-eszközök Aktiválási zár letiltása az Intune-nal


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Microsoft Intune segítségével felügyelheti az iOS/iPadOS Aktiválási zárt, amely az iOS/iPadOS 8,0 és újabb rendszerű eszközök Find My iPhone alkalmazásának egyik funkciója. Ha a felhasználó megnyitja a Find My iPhone alkalmazást egy eszközön, az aktiválási zár automatikusan engedélyezve lesz. Az engedélyezése után meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni a következők bármelyikét:

- A Find My iPhone alkalmazás kikapcsolása
- Az eszköz alaphelyzetbe állítása
- Az eszköz újraaktiválása

## <a name="how-activation-lock-affects-you"></a>Az aktiválási zár hatásai

Míg a Aktiválási zár segít az iOS/iPadOS eszközök biztonságossá tételében, és javítja az elveszett vagy ellopott eszközök helyreállításának esélyét, ez a funkció számos kihívást is jelenthet Ön, mint rendszergazda számára. Például:

- Egy felhasználó beállítja az aktiválási zárat egy eszközön. A felhasználó később elhagyja a céget és visszaszolgáltatja az eszközt. A felhasználó Apple ID azonosítója és jelszava nélkül semmilyen módon nem lehet újraaktiválni az eszközt.
- Szüksége van egy jelentésre az összes eszközről, amelyen engedélyezve van az aktiválási zár.
- Néhány eszközt másik részleghez szeretne rendelni a szervezetben egy eszközfrissítés során. Csak azokat az eszközöket lehet újból hozzárendelni, amelyeken nincs engedélyezve az aktiválási zár.

A problémák megoldásához az Apple bemutatta Aktiválási zár iOS/iPadOS 7,1-es letiltását. A Aktiválási zár letiltása lehetővé teszi, hogy a felhasználó Apple ID azonosítója és jelszava nélkül távolítsa el az Aktiválási zár a felügyelt eszközökről. A felügyelt eszközök létre tudnak hozni egy eszközspecifikus aktiválásizár-áthidaló kódot, mely az Apple aktiválási kiszolgálóján van tárolva.

>[!TIP]
>Az iOS/iPadOS eszközök felügyelt módja lehetővé teszi, hogy az Apple konfigurátor használatával zárolja az eszközt, és bizonyos üzleti célokra korlátozza a funkcionalitást. A felügyelt mód csak vállalati tulajdonú eszközökhöz használható.

Az aktiválási zárról további információt az [Apple webhelyén](https://support.apple.com/HT201365) olvashat.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Az aktiválási zár kezelése az Intune-nal
Az Intune az iOS/iPadOS 8,0-es vagy újabb verzióját futtató felügyelt eszközök Aktiválási zár állapotát kérheti le. Csak felügyelt eszközök esetén az Intune lekérheti a letiltási Aktiválási zár kódot, és közvetlenül kiállíthatja azt az eszközön. Ha törölték az eszköz adatait, üres felhasználónévvel és a kódot jelszóként használva közvetlenül hozzáférhet az eszközhöz.

**Az aktiválási zárnak az Intune-nal történő felügyelete a következő üzleti előnyökkel jár:**

- A felhasználó élvezheti a Find My iPhone alkalmazás biztonsági előnyeit.
- Lehetővé teheti, hogy a felhasználó annak tudatában végezhesse a munkáját, hogy az eszközt ki lehet vonni vagy fel lehet oldani a zárolását, ha a használatának módosítására van szükség.

## <a name="before-you-start"></a>Előkészületek
Az eszközök Aktiválási zár letiltásához a következő utasításokat követve engedélyeznie kell azt:

1. Az [eszköz korlátozási beállításainak konfigurálása](../configuration/device-restrictions-configure.md)című témakörben leírtak alapján konfigurálhatja az iOS/iPadOS Intune-eszköz korlátozási profilját.
2. Az [iOS/iPadOS eszköz korlátozási beállításainál](../configuration/device-restrictions-ios.md)az **általános** beállítások területen engedélyezze a **aktiválási zár**lehetőséget.
3. Mentse a profilt, majd [rendelje](../configuration/device-profile-assign.md) hozzá azokhoz az eszközökhöz, amelyeken a letiltási aktiválási zár szeretné kezelni.


## <a name="how-to-use-disable-activation-lock"></a>A Disable Aktiválási zár használata

>[!IMPORTANT]
>Miután letiltotta a Aktiválási zár az eszközön, ha a Find My iPhone alkalmazás elindult, automatikusan új Aktiválási zár lesz alkalmazva. Ezért **csak akkor kövesse ezt az eljárást, ha az eszköz a birtokában van**.

Az Intune **Disable aktiválási zár** távoli eszköz művelettel a felhasználó Apple ID azonosítója és jelszava nélkül távolítsa el a aktiválási zár egy IOS/iPadOS-eszközről. Miután letiltotta a Aktiválási zár, az eszköz újra bekapcsol Aktiválási zár a Find My iPhone alkalmazás indításakor. Ha fizikai hozzáféréssel rendelkezik az eszközhöz, tiltsa le a Aktiválási zár.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Az **Intune** panelen válassza az **Eszközök** lehetőséget.
4. Az **Eszközök** panelen válassza a **Minden eszköz** lehetőséget.
5. A felügyelt eszközök listájában válassza a Aktiválási zár eszköz távoli **letiltása** műveletet.
6. Nyissa meg az eszköz "hardver" szakaszát, majd másolja a **aktiválási zár megkerülő kód** értékét a **feltételes hozzáférés lehetőségre**.

    >[!NOTE]
    >Az eszköz összes adatának törlése előtt másolja ki a megkerülési kódot. Ha az eszközbeállításokat a kód kimásolása előtt állítja vissza, a kód el lesz távolítva az Azure-ból.

7. Nyissa meg az eszköz **Áttekintés** paneljét, majd válassza az **Összes adat törlése** lehetőséget.
8. Az eszköz alaphelyzetbe állítása után meg kell adnia az *Apple-azonosítót* és a *jelszót*. Hagyja üresen az *Azonosító* mezőt, majd adja meg az **aktiválásizár-megkerülő kódot** a *jelszóhoz*. Ezzel eltávolítja a fiókot az eszközről. 


## <a name="next-steps"></a>További lépések

A zárolásfeloldási kérés állapotát az **Eszközök kezelése** munkaterhelésben az eszköz részleteit megjelenítő oldalon ellenőrizheti.
