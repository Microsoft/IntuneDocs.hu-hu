---
title: MacOS kernel-bővítmények eszköz profiljának létrehozása a Microsoft Intune-Azure-ban | Microsoft Docs
titleSuffix: ''
description: Adjon hozzá vagy hozzon létre egy macOS-eszköz profilt, majd konfigurálja a kernel-bővítményeket a felhasználó felülbírálásának engedélyezéséhez, a csoport azonosítójának hozzáadásához, valamint egy köteg és csoport azonosítójának Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: abcd7b96de8f5f3984c2d4407abaf11b7b6b7e4f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492485"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>MacOS kernel-bővítmények hozzáadása az Intune-ban

MacOS-eszközökön a kernel szintjén adhat hozzá szolgáltatásokat. Ezek a szolgáltatások az operációs rendszer azon részeihez férnek hozzá, amelyekhez a normál programok nem férhetnek hozzá. Előfordulhat, hogy a szervezete olyan konkrét igényekkel vagy követelményekkel rendelkezik, amelyek nem érhetők el egy alkalmazásban, az eszköz funkciójában stb. 

Ha olyan kernel-bővítményeket szeretne hozzáadni, amelyek mindig engedélyezve vannak az eszközökön való betöltéshez, adja hozzá a "kernel Extensions" (KEXT) kifejezést Microsoft Intune, majd telepítse ezeket a bővítményeket az eszközeire.

Például van egy víruskeresési program, amely kártékony tartalmat keres az eszközön. A víruskereső program kernel-bővítményét az Intune-ban engedélyezett kernel-bővítményként adhatja hozzá. Ezután "rendelje hozzá" a bővítményt a macOS-eszközökhöz.

Ezzel a funkcióval a rendszergazdák a kernel-bővítmények felülbírálását, a csoport azonosítóinak hozzáadását és az Intune-ban megadott kernel-bővítmények hozzáadását engedélyezhetik a felhasználóknak.

Ez a funkció az alábbiakra vonatkozik:

- macOS 10.13.2 és újabb verziók

A funkció használatához az eszközöknek a következőket kell tartalmazniuk:

- Regisztrálva van az Intune-ban az Apple Készülékregisztrációs program (DEP) használatával. A [MacOS-eszközök automatikus regisztrálása](../enrollment/device-enrollment-program-enroll-macos.md) további információkat tartalmaz.

  VAGY

- Regisztrálva van az Intune-ban a "felhasználó által jóváhagyott beléptetéssel" (Apple term). [Felkészülés a kernel-bővítmények a MacOS magas Sierra-ben való változásaira](https://support.apple.com/en-us/HT208019) (az Apple webhelyének megnyitása) további információkat tartalmaz.

Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a funkciókat egy profilhoz, leküldheti vagy telepítheti a profilt macOS-eszközökre a szervezetben.

Ez a cikk bemutatja, hogyan hozhat létre az Intune-ban kernel-bővítményeket használó eszköz-konfigurációs profilt.

> [!TIP]
> További információ a kernel-bővítményekről: [kernel-bővítmény áttekintése](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (az Apple webhelyének megnyitása).

## <a name="what-you-need-to-know"></a>Amit még tudnia kell

- Aláíratlan örökölt kernel-bővítmények is hozzáadhatók.
- Ügyeljen arra, hogy a rendszermag-bővítmény helyes csapat-azonosítóját és a köteg AZONOSÍTÓját adja meg. Az Intune nem ellenőrzi a beírt értékeket. Ha helytelen adatokat ad meg, a bővítmény nem fog működni az eszközön.

> [!NOTE]
> Az Apple közzétette az összes szoftver aláírásával és notarization kapcsolatos információkat. MacOS 10.14.5 és újabb rendszereken az Intune-on keresztül üzembe helyezett kernel-bővítményeknek nem kell megfelelniük az Apple notarization-szabályzatának.
>
> A notarization szabályzattal, valamint a frissítésekkel és a változásokkal kapcsolatos további információkért tekintse meg a következő forrásokat:
>
> - [Notarizing az alkalmazást a terjesztés előtt (az](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) Apple webhelyén nyílik meg) 
> - [Felkészülés a kernel-bővítmények változásaira a MacOS High Sierra-ben](https://support.apple.com/en-us/HT208019) (az Apple webhelyén nyílik meg)

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza a **MacOS** lehetőséget
    - **Profil típusa**: válassza a **bővítmények**lehetőséget.
    - **Beállítások**: adja meg a konfigurálni kívánt beállításokat. Az összes beállítás listáját és a teendőket lásd:

        - [macOS](kernel-extensions-settings-macos.md)

4. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a listában. Ügyeljen arra, hogy [hozzárendelje a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](../device-profile-monitor.md).

## <a name="next-steps"></a>További lépések

A profil létrehozása után készen áll a hozzárendelésre. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](../device-profile-monitor.md).
