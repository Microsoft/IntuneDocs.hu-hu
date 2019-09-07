---
title: Microsoft Intune bérlő állapota lap
titleSuffix: Microsoft Intune
description: Az Intune-bérlő állapota lapon megtekintheti a bérlő fontos adatait az Intune-portál elhagyása nélkül
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b55623dec2a89df700da8c0adb1c64e7e754043f
ms.sourcegitcommit: e477e399cba673a2a9e1fa342e8303ed993801eb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70738898"
---
# <a name="use-the-intune-tenant-status-page"></a>Az Intune-bérlő állapotának használata lap
A Microsoft Intune bérlő állapota lap egy központi központ, ahol a bérlő aktuális és fontos adatait tekintheti meg. A részletek tartalmazzák a licencek rendelkezésre állását és használatát, az összekötő állapotát, valamint az Intune szolgáltatással kapcsolatos fontos kommunikációt.  

Az irányítópult megtekintéséhez jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, majd válassza a **bérlő állapota**lehetőséget.  A *bérlő állapota* a **Súgó és támogatás**területen jelenik meg.  

Az oldal három lapra van osztva:

## <a name="tenant-details"></a>Bérlő részletei
A bérlői adatok áttekintést nyújtanak a bérlőről. Megtekintheti a bérlő nevét és helyét, a MDM-szolgáltatót és a bérlői szolgáltatás kiadási számát. A szolgáltatás kiadásának száma egy hivatkozás, amely megnyitja az *Újdonságok az Intune-ban* című cikket a Microsoft docs webhelyen. Az *Újdonságok*az Intune szolgáltatás legújabb szolgáltatásairól és frissítéseiről olvashatók.  

Ezen a lapon a rendelkezésre álló licencekre vonatkozó alapvető információkat és a felhasználókhoz rendelt mennyiségeket is megtalálhatja. Az eszközökhöz tartozó licencek nem jelennek meg.

## <a name="connector-status"></a>Összekötő állapota
Az összekötő állapota egy egyablakos hely az Intune összes elérhető összekötője állapotának áttekintéséhez.  

Az összekötők a következők:
- **Külső szolgáltatásokhoz konfigurált kapcsolatok**. Például a *Apple Volume Purchase program* szolgáltatás vagy a *Windows Autopilot* szolgáltatás.  Az ilyen típusú összekötő állapota a legutóbbi sikeres szinkronizálási időponton alapul.
- A külső, nem felügyelt szolgáltatásokhoz, például az *Apple Push Notification Services* (APNS) tanúsítványokhoz való **kapcsolódáshoz szükséges tanúsítványok vagy hitelesítő adatok**. Az ilyen típusú összekötő állapota a tanúsítvány vagy a hitelesítő adat lejárati időbélyegzője alapján történik.  

Amikor megnyitja az *összekötő állapota* lapot, a nem kifogástalan állapotú összekötők a lista tetején jelennek meg. A következő a figyelmeztetéseket tartalmazó összekötők, majd az egészséges összekötők listája. A még nem konfigurált összekötők *nem engedélyezettek*az utolsóként.

Ha több, mint egyetlen összekötő egyetlen típusból áll, az állapot az összes azonos összekötő összefoglalása. Az egyes összekötők legalább kifogástalan állapota a csoport állapotának megfelelően van használatban.  

**Összekötő állapota:**
- **Sérült**
  - A tanúsítvány vagy a hitelesítő adat Lejárt
  - A legutóbbi szinkronizálás három nappal ezelőtt történt
- **Figyelmeztetés**
  - A tanúsítvány vagy a hitelesítő adat érvényessége hét napon belül lejár
  - A legutóbbi szinkronizálás több mint egy nappal ezelőtt történt
- **Kifogástalan**
  - A tanúsítvány vagy a hitelesítő adat nem jár le a következő hét napon belül
  - A legutóbbi szinkronizálás kevesebb mint egy nappal ezelőtt történt  

Amikor kiválaszt egy összekötőt a listából, a portál az adott összekötőhöz kapcsolódó portált jeleníti meg. Az összekötők lapon megtekintheti a korábban konfigurált összekötők állapotát, vagy megadhatja az adott típusú új összekötő hozzáadásához vagy létrehozásához szükséges beállításokat.

Ha például a **VPP lejárati dátum** összekötőt választja, megnyílik az **iOS Volume-purchased program-jogkivonatok** lap, ahol megtekintheti az összekötő további részleteit. Létrehozhat egy új konfigurációt is, vagy szerkesztheti és kijavíthatja a meglévő problémákat.

## <a name="service-health-dashboard"></a>Szolgáltatás állapotának irányítópultja  
A szolgáltatás állapota irányítópulton megtekintheti a bérlőt befolyásoló *szolgáltatási incidensek* részleteit, valamint az *Intune-híreket* , amelyek a frissítésekkel és a tervezett módosításokkal kapcsolatos információkat biztosítanak.

### <a name="intune-service-health"></a>Intune Service Health
Tekintse meg az aktív incidensek és az ADVISOROK részleteit anélkül, hogy a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com)található Microsoft 365 Service Health irányítópultra vagy az üzenetközpont-ra kellene navigálnia. Csak a bérlőt érintő incidensek jelennek meg.  

Ha kijelöl egy eseményt, az incidens részletei közvetlenül a bérlő állapota lapon jelennek meg. A korábbi tanácsadók és incidensek megtekintéséhez válassza a **korábbi incidensek/tanácsadók**megtekintése lehetőséget. Megnyílik a Microsoft 365 felügyeleti központ, és megtekintheti a bérlőnek az elmúlt 30 napban megadott tanácsadókat és incidenseket.  

Az *Intune-Service Health*adatainak megtekintéséhez a fióknak a Azure Active Directory vagy a Microsoft 365 felügyeleti központban kell lennie a **globális rendszergazdai** vagy **szolgáltatás-rendszergazdai** szerepkörrel. Az engedélyek hozzárendeléséhez jelentkezzen be a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) globális rendszergazdai engedélyekkel. Válassza a **felhasználók > az aktív felhasználók**lehetőséget, majd válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza a szerepkörök **szerkesztése** lehetőséget, válassza a *szolgáltatás-rendszergazda* vagy a *globális rendszergazda*lehetőséget, majd **mentse** a szerkesztést az engedélyek hozzárendeléséhez.  

A Microsoft 365 felügyeleti központban csak az Intune-Service Health kommunikációs beállításait állíthatja be.

### <a name="intune-news"></a>Intune-Hírek  
Tekintse meg az Intune szolgáltatás csapatának tájékoztató jellegű kommunikációját anélkül, hogy az Office Message Centerre kellene navigálnia. A kommunikáció olyan módosításokat tartalmaz, amelyek nemrég történtek az Intune szolgáltatásban, vagy amelyek a bérlői úton történnek.  

Alapértelmezés szerint a 10 legutóbbi és aktív üzenet látható. A régebbi üzenetek megtekintéséhez kattintson a **korábbi üzenetek** megjelenítése elemre az *üzenetközpont* megnyitásához a Microsoft 365 felügyeleti központban.  

Az Intune-Hírek információinak megtekintéséhez a fióknak a Azure Active Directory vagy az **üzenetsor-olvasó** **szerepkörrel** kell **rendelkeznie a Microsoft 365** felügyeleti központban.  Az engedély hozzárendeléséhez jelentkezzen be a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) rendszergazdai engedélyekkel. Válassza a **felhasználók > az aktív felhasználók**lehetőséget, majd válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza a *szerepkörök* **szerkesztése** lehetőséget, válassza a *csapatok kommunikációs rendszergazdája*lehetőséget, majd **mentse** a szerkesztést az engedélyek hozzárendeléséhez.  

A Microsoft 365 felügyeleti központban csak az Intune-Hírek kommunikációs beállításait állíthatja be.
