---
title: Mennyiségi programban vásárolt iOS/iPadOS-e-könyvek kezelése
titleSuffix: Microsoft Intune
description: Az iOS-áruházból mennyiségi programban vásárolt könyvek szinkronizálása az Intune-nal, majd használatuk felügyelete és nyomon követése.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff2ed62695bad781b7b55ac590e9b97490ba2416
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216080"
---
# <a name="how-to-manage-iosipados-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Mennyiségi vásárlási program keretében vásárolt iOS/iPadOS-e-könyvek kezelése Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Apple Volume Purchase Program (VPP) keretében a vállalat felhasználói közt elosztani kívánt könyvekhez több licencet is vásárolhat. Az üzleti és az oktatási áruházakból vásárolt könyveket oszthatja el.

A Microsoft Intune segít a program keretében vásárolt könyvek szinkronizálásában, kezelésében és hozzárendelésében. Importálhatja az áruházból a licencadatokat, és nyomon követheti a felhasznált licencek számát.

A könyvek kezelésének eljárásai hasonlók a [VPP-alkalmazások kezeléséhez](../vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Mennyiségi programban vásárolt könyvek kezelése iOS-eszközökön
Az iOS/iPadOS-könyvekhez több licencet is vásárolhat a [Apple Volume Purchase program for Business](https://www.apple.com/business/vpp/) vagy az [oktatási Apple Volume Purchase program](https://volume.itunes.apple.com/us/store). Ez az eljárás magában fogalja Apple VPP-fiók beállítását az Apple webhelyén, és az Apple VPP-token feltöltését az Intune-ba.  Ezután szinkronizálhatja a mennyiségi vásárlás adatait az Intune-nal, és nyomon követheti a mennyiségi programban vásárolt könyvek használatát.

## <a name="before-you-start"></a>Előkészületek
Mielőtt hozzálát, szerezzen be VPP-tokent az Apple-től, és töltse fel az Intune-fiókjába. Egyéb rendelkezések:

* Ha korábban VPP-tokent használt egy másik termékkel, egy újat kell létrehoznia az Intune használatához.
* A tokenek egy évig érvényesek.
* Alapértelmezés szerint az Intune naponta kétszer szinkronizál az Apple VPP szolgáltatással. Manuális szinkronizálás bármikor kezdeményezhető.
* Miután a VPP-tokent az Intune-ba importálta, ne importálja ugyanezt a tokent egy másik eszközfelügyeleti megoldásba. Ez a licenc-hozzárendelések és a felhasználói rekordok elvesztését eredményezheti.
* Mielőtt az iOS/iPadOS-könyveket az Intune-nal kezdené használni, távolítsa el a más mobileszköz-felügyeleti (MDM) szállítókkal létrehozott meglévő VPP-felhasználói fiókokat. Az Intune biztonsági okokból nem szinkronizálja ezeket a felhasználói fiókokat az Intune-ba. Az Intune csak az Intune által létrehozott adatokat szinkronizálja az Apple VPP szolgáltatásból.
* Csak olyan eszközhöz rendelhet hozzá könyvet, amelyen telepítve van a beépített iBooks alkalmazás. Ha nincs, akkor a felhasználónak újra kell telepítenie az alkalmazást, hogy el tudják olvasni a könyvet. Az Intune jelenleg nem használható eltávolított beépített alkalmazások újratelepítésére.
* Csak az Apple Volume Purchase Program webhelyéről rendelhet hozzá könyveket. A házon belül létrehozott könyveket nem töltheti fel és rendelheti hozzá.
* Jelenleg nem rendelhet hozzá könyveket a felhasználói kategóriákhoz ugyanúgy, ahogyan az alkalmazásokat.
* A könyv hozzárendelése után nem igényelhet vissza licencet.
* Amikor egy arra jogosult eszközzel rendelkező felhasználó először próbál VPP-könyvet telepíteni, először csatlakoznia kell az Apple Volume Purchase programhoz. A felügyelt Apple-azonosítókkal rendelkező biztonsági csoportokhoz is hozzárendelhet licenceket. Ha ezt teszi, akkor a könyvek telepítésekor a rendszer nem kéri a felhasználóktól az Apple-azonosítót.
* Az eszközöket felhasználói affinitással kell regisztrálni, mivel az e-könyvek csak felhasználói csoportokhoz rendelhetők.   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP-token beszerzése és feltöltése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **Apple VPP-tokenek**elemet.
3. A VPP-tokenek panel listájában kattintson a **Létrehozás** elemre.
5. Az **Új VPP-token** panelen adja meg az alábbi adatokat:
    - **VPP-jogkivonatfájl** – Ha még nem tette meg, iratkozzon fel a Volume Purchase Program for Business vagy a Volume Purchase Program for Education programra. Ezután töltse le a fiókjához tartozó Apple VPP-tokent, és itt jelölje ki.
    - **Apple ID** – Adja meg a mennyiségi vásárlási programhoz kapcsolódó fiók Apple ID-ját.
    - **VPP-fiók típusa** –A következő lehetőségek közül választhat: **Üzlet** és **Oktatás**.
5. Ha végzett, kattintson a **Létrehozás** gombra.

A token a jogkivonatok panel listájában jelenik meg.


Az Apple által tárolt adatok bármikor szinkronizálhatók az Intune-nal a **Szinkronizálás** lehetőség kiválasztásával.

## <a name="to-assign-a-volume-purchased-app"></a>Mennyiségi programban vásárolt alkalmazás hozzárendelése

1. Válassza az **alkalmazások** > **eBooks** > **az összes ebook**elemet.
2. A könyvlista paneljén válassza ki a hozzárendelni kívánt könyvet, és válassza a **...** > **Csoportok hozzárendelése** lehetőséget.
3. A <*könyv neve*> – **Hozzárendelt csoportok** panelen válassza a **Felügyelet** > **Hozzárendelt csoportok** lehetőséget.
4. Válassza a **Hozzárendelt csoportok**, majd a **Csoportok kiválasztása** panelt, és jelölje ki azon Azure AD felhasználói csoportokat, amelyekhez hozzá szeretné rendelni a könyvet. Az eszközcsoportok jelenleg nem támogatottak.
Válassza az **Elérhető** vagy a **Kötelező** hozzárendelési műveletet. 
5. Ha elkészült, válassza a **Mentés** elemet.

## <a name="next-steps"></a>További lépések

Lásd [az alkalmazások figyelésével](apps-monitor.md) foglalkozó útmutatót, amely segítséget nyújt a könyvhozzárendelések figyeléséhez.






