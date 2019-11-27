---
title: A Mobile Threat Defense-összekötő engedélyezése a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: A Mobile Threat Defense (MTD) partner és a Microsoft Intune közötti összekötő engedélyezése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
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
ms.openlocfilehash: b8243ae4014660a76c6327afd9c970ce8a9eae58
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478836"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban

A Mobile Threat Defense (MTD) telepítésekor beállította a fenyegetések besorolására szolgáló szabályzatot a Mobile Threat Defense-partner konzolon, és Ön hozta létre az eszköz megfelelőségi szabályzatát az Intune-ban. Ha már konfigurálta az Intune-összekötőt a MTD-partner konzolon, most már engedélyezheti a MTD-MTD kapcsolatát.

> [!NOTE]
> Ez a témakör minden Mobile Threat Defense-partnerre vonatkozik.

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz

Amikor új alkalmazást integrál az Intune Mobile Threat Defense-be, és engedélyezi az Intune-nal való kapcsolatot, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden olyan MTD-alkalmazás, amelyet integrál, beleértve a [DEFENDER ATP](advanced-threat-protection.md) -t vagy bármely további [MTD-partnert](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre. Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.

Ha a klasszikus szabályzatot törli, törölnie kell a létrehozásért felelős Intune-nal, majd újra be kell állítania a kapcsolatát. Ez a folyamat újra létrehozza a klasszikus szabályzatot. Nem támogatott a klasszikus szabályzatok áttelepítése MTD-alkalmazásokhoz az új házirend-típusra a feltételes hozzáféréshez.

Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz:

- Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy a MTD-partnerekkel való kommunikáció előtt rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.

- Semmilyen más felhőalapú alkalmazásra vagy erőforrásra nincs hatással.

- Nem különböznek a MTD kezeléséhez esetlegesen létrehozott feltételes hozzáférési házirendektől.

- Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.

A klasszikus feltételes hozzáférési szabályzatok az [Azure](https://portal.azure.com/#home)-ban való megtekintéséhez lépjen a **Azure Active Directory** > **feltételes hozzáférés** > **klasszikus házirendek**elemre.

## <a name="to-enable-the-mobile-threat-defense-connector"></a>A Mobile Threat Defense-összekötő engedélyezése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **Mobile Threat Defense**lehetőséget.

3. A **Mobile Threat Defense** panelen válassza a **Hozzáadás**lehetőséget.

4. A **Mobile Threat Defense-összekötő telepítéséhez**válassza ki a MTD-megoldást a legördülő listából.

5. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.  Az alábbi képen például a Symantec Endpoint Protection elérhető lehetőségei láthatók:

   ![Az MTD beállítása az Azure-beli Intune-portálon](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense – váltási beállítások

A cég igényei alapján eldöntheti, hogy az MTD mely kapcsolós beállításait kell engedélyeznie. Az összes Mobile Thread Defense-partner nem támogatja az alábbi lehetőségek egyikét sem:

**MDM megfelelőségi szabályzatának beállításai**

- Az Android rendszerű **eszközök _\<támogatott verziókhoz_ való csatlakoztatása > _\<MTD partner neve >_** : Ha engedélyezi ezt a beállítást, az Android 4.1 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.

- Az **iOS-eszközök verziójának csatlakoztatása _\<támogatott verziók >_ _\<MTD partner neve >_** : Ha engedélyezi ezt a beállítást, az iOS 8.0 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.

- **Alkalmazásszinkronizálás engedélyezése iOS-eszközök számára**: Engedélyezi a Mobile Threat Defense-partner számára, hogy iOS-alkalmazások metaadatait kérje le az Intune-ból fenyegetéselemzés céljából.

- **Nem támogatott operációsrendszer-verziók blokkolása**: a legalacsonyabb támogatott verziónál régebbi rendszerű eszközök blokkolva lesznek.

**Az alkalmazás védelmi házirendjének beállításai**

- Az  ***\<támogatott verziókhoz* tartozó Android-eszközök csatlakoztatása > *\<MTD partner neve >* for app Protection Policy kiértékelés**: Ha engedélyezi ezt a beállítást, az eszköz veszélyforrások szintjének szabályát használó alkalmazás-védelmi szabályzatok kiértékelik az adott összekötőből származó adatokkal rendelkező eszközöket.

- Az **iOS-eszközök verziójának Összekapcsolása *\<támogatott verziók >* *\<MTD partner neve >* az alkalmazás-védelmi házirend kiértékeléséhez**: Ha engedélyezi ezt a beállítást, az eszköz veszélyforrása szintű szabályt használó alkalmazás-védelmi házirendek kiértékelik az adott összekötőből származó adatokkal rendelkező eszközöket.

Ha többet szeretne megtudni a Mobile Threat Defense-összekötők használatáról Intune App Protection szabályzat kiértékeléséhez, tekintse meg a [Mobile Threat Defense beállítása a nem regisztrált eszközökhöz](~/protect/mtd-enable-unenrolled-devices.md)című témakört.

**Közös megosztott beállítások**

- **Partner ennyi nap után nem válaszol**: az Intune ennyi napnyi tétlenség után feltételezi, hogy a partner a kapcsolat megszakadása miatt nem válaszol. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!IMPORTANT]
> Ha lehetséges, javasoljuk, hogy az eszköz megfelelőségének és a feltételes hozzáférési szabályzat szabályainak létrehozása előtt vegye fel és rendelje hozzá a MTD-alkalmazásokat. Ez segít biztosítani, hogy a MTD alkalmazás készen álljon, és elérhető legyen a végfelhasználók számára az e-mailekhez vagy más vállalati erőforrásokhoz való hozzáféréshez.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.

## <a name="next-steps"></a>További lépések

- [Mobile Threat Defense-(MTD-) alkalmazás-védelmi szabályzat létrehozása az Intune-](~/protect/mtd-app-protection-policy.md)nal.
