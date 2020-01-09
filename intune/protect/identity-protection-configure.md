---
title: PIN-kód használata a Windows 10-es eszközökre való bejelentkezéshez Microsoft Intune-Azure használatával | Microsoft Docs
description: A Windows Hello for Business használatával lehetővé teheti a felhasználók számára, hogy PIN-kódot, ujjlenyomatot és egyebeket használva jelentkezzenek be az eszközökre. Hozzon létre egy Identity Protection konfigurációs profilt az Intune-ban a Windows 10-es eszközökhöz ezekkel a beállításokkal, és rendelje hozzá a profilt a felhasználói csoportokhoz és az eszközök csoportjaihoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f5d3a232cab25c60189132732a0ea3f347c74a
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683799"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>A Windows Hello for Business használata Windows 10-es eszközökön Microsoft Intune

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

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

3. Adja meg a következő tulajdonságokat:

   - **Név**: Adja meg az új profil leíró nevét.
   - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
   - **Platform**: válassza **a Windows 10 és újabb**lehetőséget. A Vállalati Windows Hello csak a Windows 10 vagy újabb rendszerű eszközökön támogatott.
   - **Profil típusa**: válassza az **Identity Protection**elemet.

4. A *vállalati Windows Hello* panelen konfigurálja a következő beállításokat:

   - **A vállalati Windows Hello konfigurálása**: válassza ki, hogyan szeretné konfigurálni a vállalati Windows Hello-t:

     - **Nincs konfigurálva** (alapértelmezett): a [vállalati Windows Hello szolgáltatásra vonatkozó rendelkezések](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) az eszközön. Ha csak felhasználókhoz rendel hozzá identitásvédelmi profilokat, az eszközkörnyezet alapértelmezett beállítása a **Nem konfigurált** lesz.

     - **Letiltva**: Ha nem szeretné a vállalati Windows Hello-t használni, válassza ezt a lehetőséget. Ez a beállítás letiltja a vállalati Windows Hello-et minden felhasználó számára.

     - **Engedélyezve**: válassza [ezt a lehetőséget a vállalati](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)Windows Hello beállításainak kiépítéséhez és konfigurálásához az Intune-ban. Adja meg a konfigurálni kívánt beállításokat. Az összes beállítás listáját és azok leírását lásd: – [Windows 10 eszközbeállítások a vállalati Windows Hello engedélyezéséhez](identity-protection-windows-settings.md).

   - **Bejelentkezéshez használható biztonsági kulcsok használata**: a Windows Hello biztonsági kulcs engedélyezése bejelentkezési hitelesítő adatként a bérlő összes számítógépe számára.

     - **Engedélyezés**
     - **Nincs konfigurálva** (alapértelmezett)

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listájában. Ezután [rendelje hozzá](../configuration/device-profile-assign.md) ezt a profilt a felhasználókhoz és az eszközökhöz, hogy megfeleljen az igényeinek.

> [!IMPORTANT]
> Annak engedélyezéséhez, hogy több felhasználó legyen kiépítve egy eszközre, a vállalati Windows Hello-szabályzatot alkalmazza az eszközökre. Ha a házirend csak a felhasználókra vonatkozik, csak egy felhasználó lehet kiépítve egy eszközre.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>További lépések

- Tekintse meg az összes [beállítás listáját, és hogy mit csinálnak](identity-protection-windows-settings.md).
- [Rendelje hozzá a profilt](../configuration/device-profile-assign.md), és [kövesse nyomon az állapotát](../configuration/device-profile-monitor.md).
