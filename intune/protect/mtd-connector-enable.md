---
title: A Mobile Threat Defense-összekötő engedélyezése a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: A Mobile Threat Defense (MTD) partner és a Microsoft Intune közötti összekötő engedélyezése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f917167baecc643e045610e86e582957e535978
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810284"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban

> [!NOTE] 
> Ez a témakör minden Mobile Threat Defense-partnerre vonatkozik.

A Mobile Threat Defense (MTD) beállítása során konfigurált egy, az MTD-partnerkonzolra vonatkozó fenyegetésosztályozási szabályzatot, és létrehozta az eszközmegfelelőségi szabályzatot az Intune-ban. Ha már konfigurálta az Intune-összekötőt a MTD-partner konzolon, most már engedélyezheti a MTD-MTD kapcsolatát.

Amikor új alkalmazást integrál az Intune Mobile Threat Defense-be, és engedélyezi az Intune-nal való kapcsolatot, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden olyan MTD-alkalmazás, amelyet integrál, beleértve a [DEFENDER ATP](advanced-threat-protection.md) -t vagy bármely további [MTD-partnert](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre. Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.

Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz: 

- Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy a MTD-partnerekkel való kommunikáció előtt rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.  
- Semmilyen más felhőalapú alkalmazásra vagy erőforrásra nincs hatással.  
- Nem különböznek a MTD kezeléséhez esetlegesen létrehozott feltételes hozzáférési házirendektől.
- Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.  

A klasszikus feltételes hozzáférési szabályzatok az [Azure](https://portal.azure.com/#home)-ban való megtekintéséhez lépjen a **Azure Active Directory**  > **feltételes hozzáférés**  > **klasszikus házirendek**elemre.


## <a name="to-enable-the-mobile-threat-defense-connector"></a>A Mobile Threat Defense-összekötő engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

4. Az **Intune-irányítópulton** válassza az **Eszközmegfelelőség**, majd a **Beállítás** szakaszban a **Mobile Threat Defense** elemet.

5. A **Mobile Threat Defense** panelen válassza a **Hozzáadás** elemet.

6. A legördülő listában jelölje ki a saját MTD-megoldását mint **Beállítani kívánt Mobile Threat Defense-összekötőt**.

    ![Az MTD beállítása az Azure-beli Intune-portálon](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense – váltási beállítások

Eldöntheti, hogy a szervezet igényeinek megfelelően melyik Mobile Threat Defense-kapcsolót kell engedélyeznie. További részletek:

**MDM megfelelőségi szabályzatának beállításai**
- \* * Az Android 4.1 + rendszerű eszközök csatlakoztatása a *\<MTD partner neve > * * *: Ha engedélyezi ezt a beállítást, az Android 4.1 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
- \* * IOS 8.0 + rendszerű eszközök csatlakoztatása *\<MTD partner neve > * * *: Ha engedélyezi ezt a beállítást, az iOS 8.0 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
- **Alkalmazásszinkronizálás engedélyezése iOS-eszközök számára**: Engedélyezi a Mobile Threat Defense-partner számára, hogy iOS-alkalmazások metaadatait kérje le az Intune-ból fenyegetéselemzés céljából.
- **Nem támogatott operációsrendszer-verziók blokkolása**: a legalacsonyabb támogatott verziónál régebbi rendszerű eszközök blokkolva lesznek.

**Az alkalmazás védelmi házirendjének beállításai**
- Az **4,1-es vagy újabb verziójú Android-eszközök csatlakoztatásával *\<MTD partner neve >* for app Protection Policy kiértékelés**: Ha engedélyezi ezt a beállítást, az eszköz veszélyforrások szintjének szabályát használó alkalmazás-védelmi szabályzatok kiértékelik az eszközöket, beleértve a az összekötőből származó adatok.
- Az **iOS-eszközök 8,0-es vagy újabb verziójának összekapcsolása az alkalmazás-védelmi szabályzat kiértékeléséhez használt *\<MTD partner neve >***  Ez az összekötő.

Ha többet szeretne megtudni a Mobile Threat Defense-összekötők használatáról Intune App Protection szabályzat kiértékeléséhez, tekintse meg a [Mobile Threat Defense beállítása a nem regisztrált eszközökhöz](~/protect/mtd-enable-unenrolled-devices.md)című témakört.

**Közös megosztott beállítások**
- **Partner ennyi nap után nem válaszol**: az Intune ennyi napnyi tétlenség után feltételezi, hogy a partner a kapcsolat megszakadása miatt nem válaszol. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!IMPORTANT] 
> Ha lehetséges, javasoljuk, hogy az eszköz megfelelőségének és a feltételes hozzáférési szabályzat szabályainak létrehozása előtt vegye fel és rendelje hozzá a MTD-alkalmazásokat. Ez segít biztosítani, hogy a MTD alkalmazás készen álljon, és elérhető legyen a végfelhasználók számára az e-mailekhez vagy más vállalati erőforrásokhoz való hozzáféréshez.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.
