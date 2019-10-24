---
title: A Mobile Threat Defense-összekötő engedélyezése a nem regisztrált eszközökhöz
titleSuffix: Microsoft Intune
description: Engedélyezze a Mobile Threat Defense-összekötőt Microsoft Intune a nem regisztrált eszközökhöz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63079757ee3610d825601921da1d33aa94f851b6
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72795306"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban a nem regisztrált eszközökön

A Mobile Threat Defense (MTD) telepítésekor beállította a fenyegetések besorolására szolgáló szabályzatot a Mobile Threat Defense-partner konzolon, és létrehozta az alkalmazás-védelmi szabályzatot az Intune-ban. Ha már konfigurálta az Intune-összekötőt a MTD-partner konzolon, most már engedélyezheti a MTD-MTD kapcsolatát.

> [!NOTE] 
> Ez a cikk az alkalmazás-védelmi házirendeket támogató összes Mobile Threat Defense-partnerre vonatkozik: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>Az MTD-összekötő engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

2. Az **Intune-irányítópulton** válassza az **Eszközmegfelelőség**, majd a **Beállítás** szakaszban a **Mobile Threat Defense** elemet.

3. A **Mobile Threat Defense** panelen válassza a **Hozzáadás** elemet.

4. A legördülő listában jelölje ki a saját MTD-megoldását mint **Beállítani kívánt Mobile Threat Defense-összekötőt**.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.

## <a name="mtd-toggle-options"></a>Az MTD kapcsolós megoldásai

A cég igényei alapján eldöntheti, hogy az MTD mely kapcsolós beállításait kell engedélyeznie. További részletek:

**Az alkalmazás védelmi házirendjének beállításai**
- Az **4,1-es vagy újabb verziójú Android-eszközök csatlakoztatásával *\<MTD partner neve >* for app Protection Policy kiértékelés**: Ha engedélyezi ezt a beállítást, az eszköz veszélyforrások szintjének szabályát használó alkalmazás-védelmi szabályzatok kiértékelik az eszközöket, beleértve a az összekötőből származó adatok.
- Az **iOS-eszközök 8,0-es vagy újabb verziójának összekapcsolása az alkalmazás-védelmi szabályzat kiértékeléséhez használt *\<MTD partner neve >***  Ez az összekötő.

**Közös megosztott beállítások**
- **Partner ennyi nap után nem válaszol**: az Intune ennyi napnyi tétlenség után feltételezi, hogy a partner a kapcsolat megszakadása miatt nem válaszol. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.

> [!NOTE] 
> Ha engedélyezi a Mobile Threat Defense-kapcsolatot az Intune-nal, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden olyan MTD-alkalmazás, amelyet integrál, beleértve a [DEFENDER ATP](advanced-threat-protection.md) -t vagy bármely további [MTD-partnert](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre. **Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.**
> 
> Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz: 
> - Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy a MTD-partnerekkel való kommunikáció előtt rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.  
> - Semmilyen más felhőalapú alkalmazásra vagy erőforrásra nincs hatással.  
> - Nem különböznek a MTD kezeléséhez, illetve az App Protection CA megköveteléséhez létrehozott feltételes hozzáférési házirendekkel.
> - Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.  
>
> A klasszikus feltételes hozzáférési szabályzatok az [Azure](https://portal.azure.com/#home)-ban való megtekintéséhez lépjen a **Azure Active Directory**  > **feltételes hozzáférés**  > **klasszikus házirendek**elemre.

## <a name="next-steps"></a>További lépések

- [Mobile Threat Defense-(MTD-) alkalmazás-védelmi szabályzat létrehozása az Intune-](~/protect/mtd-app-protection-policy.md)nal.