---
title: PIN-kód használata a Windows 10-es eszközökre való bejelentkezéshez Microsoft Intune-Azure használatával | Microsoft Docs
description: A Windows Hello for Business használatával lehetővé teheti a felhasználók számára, hogy PIN-kódot, ujjlenyomatot és egyebeket használva jelentkezzenek be az eszközökre. Hozzon létre egy Identity Protection konfigurációs profilt az Intune-ban a Windows 10-es eszközökhöz ezekkel a beállításokkal, és rendelje hozzá a profilt a felhasználói csoportokhoz és az eszközök csoportjaihoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d81396dda2cbd8129d9bbcae961435b99946d74
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729243"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>A Windows Hello for Business használata Windows 10-es eszközökön Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A vállalati Windows Hello szolgáltatás a jelszavak, intelligens kártyák és virtuális intelligens kártyák cseréjével a Windows-eszközökre való bejelentkezéshez használható módszer. Az Intune beépített beállításokat tartalmaz, amelyek segítségével a rendszergazdák konfigurálhatják és használhatják a vállalati Windows Hello-t. Például a következő beállításokkal végezheti el a használatát:

- A vállalati Windows Hello engedélyezése az eszközök és a felhasználók számára
- Az eszköz PIN-követelményeinek beállítása, beleértve a PIN-kód minimális vagy maximális hosszát
- Kézmozdulatok, például ujjlenyomatok engedélyezése, hogy a felhasználók (vagy nem használhatják) bejelentkezhetnek az eszközökre

Ez a funkció a következő rendszerű eszközökre vonatkozik:

- Windows 10 és újabb
- Windows 10 mobil verzió
- Windows Holographic for Business

Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a szolgáltatásokat egy profilhoz, leküldheti vagy telepítheti ezeket a beállításokat a szervezetében lévő felhasználói és eszközök csoportjaira.

Ez a cikk bemutatja, hogyan hozhat létre egy eszköz-konfigurációs profilt. Az összes beállítás listáját és azok leírását lásd: [Windows 10 eszközbeállítások a vállalati Windows Hello engedélyezéséhez](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Az eszköz profiljának létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adjon meg egy leíró nevet az új profilhoz.
    - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza **a Windows 10 és újabb**lehetőséget. A Vállalati Windows Hello csak a Windows 10 vagy újabb rendszerű eszközökön támogatott.
    - **Profil típusa**: Válassza az **Identity Protection**elemet.
    - **A vállalati Windows Hello konfigurálása**: Válassza ki, hogyan szeretné konfigurálni a vállalati Windows Hello-t. A választható lehetőségek:

        - **Nincs konfigurálva**: A [vállalati Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) kiépítését az eszközön. Ha csak felhasználókhoz rendel hozzá identitásvédelmi profilokat, az eszközkörnyezet alapértelmezett beállítása a **Nem konfigurált** lesz.
        - Letiltva: Ha nem szeretné a vállalati Windows Hello-t használni, válassza ezt a lehetőséget. Ez a beállítás letiltja a vállalati Windows Hello-et minden felhasználó számára.
        - **Engedélyezve**: Válassza [ezt a lehetőséget a vállalati](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)Windows Hello beállításainak kiépítéséhez és konfigurálásához az Intune-ban. Adja meg a konfigurálni kívánt beállításokat. Az összes beállítás listáját és a teendőket lásd:

            - [Windows 10 eszközbeállítások a vállalati Windows Hello engedélyezéséhez](identity-protection-windows-settings.md)

4. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listájában. Ezután [rendelje hozzá](../configuration/device-profile-assign.md) ezt a profilt a felhasználókhoz és az eszközökhöz, hogy megfeleljen az igényeinek.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>További lépések

- Tekintse meg az összes [beállítás listáját, és hogy mit csinálnak](identity-protection-windows-settings.md).
- [Rendelje hozzá a profilt](../configuration/device-profile-assign.md), és [kövesse nyomon az állapotát](../configuration/device-profile-monitor.md).
