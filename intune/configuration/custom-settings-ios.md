---
title: Egyéni beállítások hozzáadása iOS-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Exportálhat iOS-beállításokat az Apple Configuratorből vagy az Apple Profile Managerből, majd a Microsoft Intune-ba importálhatja őket. Ezek a beállítások egyéni beállításokat és szolgáltatásokat hozhatnak létre, használhatnak és vezérelhetik az iOS-eszközökön. Ez az egyéni profil ezután hozzárendelhető vagy kiosztható a szervezet iOS-eszközei számára kiindulási alap vagy szabvány létrehozása érdekében.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ef61292086fb9781c2924ef31271e7f36d99ab2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730883"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Egyéni beállítások használata iOS-eszközökhöz a Microsoft Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre az iOS-eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

iOS-eszközök használatakor kétféleképpen lehet egyéni beállításokat juttatni az Intune-ba:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Ezekkel az eszközökkel exportálhatja a beállításokat egy konfigurációs profilba. Az Intune-ban importálja ezt a fájlt, majd hozzárendeli a profilt az iOS-felhasználókhoz és -eszközökhöz. A hozzárendelés után a rendszer elosztja a beállításokat. Emellett az iOS rendszerhez készült alapkonfigurációt vagy standardot is létrehozzák a szervezetben.

Ez a cikk útmutatást nyújt az Apple konfigurátor és az Apple-profil kezelőjének használatáról, valamint ismerteti a konfigurálható tulajdonságokat is.

## <a name="before-you-begin"></a>Előkészületek

[Hozza létre a profilt](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Amit még tudnia kell

- Ha az **Apple konfigurátor** használatával hozza létre a konfigurációs profilt, ügyeljen arra, hogy az exportált beállítások kompatibilisek legyenek az iOS-verzióval az eszközökön. A nem kompatibilis beállításokból fakadó problémák megoldásával kapcsolatos információkat az [Apple Developer](https://developer.apple.com/) webhelyről letölthető **Configuration Profile Reference** és **Mobile Device Management Protocol Reference** című (angol nyelvű) útmutatókban talál.

- Az **Apple Profile Manager** használatakor:

  - Engedélyezze a [mobileszköz-felügyeletet](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) a Profile Managerben.
  - Adja hozzá az [iOS-eszközöket](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) a Profile Managerben.
  - Miután hozzáadott egy eszközt a Profile Managerben, lépjen a **Könyvtár** > **Eszközök** részhez > válassza ki az eszközt > válassza a **Beállítások** lehetőséget. Adja meg az általános beállításokat az eszközhöz.

    Töltse le és mentse ezt a fájlt. A fájlt az Intune-profilban adja majd meg.

  - Ügyeljen arra, hogy az Apple profil Managerből exportált beállítások kompatibilisek legyenek az iOS-verzióval az eszközökön. A nem kompatibilis beállításokból fakadó problémák megoldásával kapcsolatos információkat az [Apple Developer](https://developer.apple.com/) webhelyről letölthető **Configuration Profile Reference** és **Mobile Device Management Protocol Reference** című (angol nyelvű) útmutatókban talál.

## <a name="custom-configuration-profile-settings"></a>Egyéni konfigurációs profil beállításai

- **Egyéni konfigurációs profil neve**: Adja meg a szabályzat nevét. Ez a név megjelenik az eszközön, valamint az Intune állapotában.
- **Konfigurációs profil fájlja**: Keresse meg a létrehozott konfigurációs profilt az Apple konfigurátor vagy az Apple Profile Manager használatával. Az importált fájl megjelenik a **Fájl tartalma** területen.

  Az egyéni konfigurációs fájlokhoz is hozzáadhat eszköz-jogkivonatokat. Az eszköz-jogkivonatok az eszközre vonatkozó információk hozzáadására szolgálnak. A sorozatszám megjelenítéséhez például írja be `{{serialnumber}}`a következőt:. Az eszközön a szöveg hasonló `123456789ABC` módon jelenik meg, amely minden eszköz esetében egyedi. A változók beírásakor ügyeljen arra, hogy kapcsos zárójeleket `{{ }}`használjon. Az [alkalmazás-konfigurációs tokenek](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) tartalmazzák a használható változók listáját. Használhatja a `deviceid` vagy bármely más eszközre jellemző értéket is.

  > [!NOTE]
  > A rendszer nem érvényesíti a változókat a felhasználói felületen, és megkülönbözteti a kis-és nagybetűket. Ennek eredményeképpen előfordulhat, hogy a profilok helytelen bevitelsel lettek mentve. Ha például a `{{deviceid}}`helyett a értéket `{{DeviceID}}` adja meg, akkor az eszköz egyedi azonosítója helyett a literál sztring jelenik meg. Ügyeljen arra, hogy a helyes adatokat adja meg.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat macOS-eszközökön](custom-settings-macos.md). 
