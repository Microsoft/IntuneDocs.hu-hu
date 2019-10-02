---
title: Mit tehetek Microsoft Intune a vállalatom számára?
titleSuffix: ''
description: Gyakori üzleti problémák Microsoft Intune segít a megoldásban.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 845eb22522895e04f6ec4f46eda7a817e27a830c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731839"
---
# <a name="what-can-intune-do-for-my-company"></a>Hogyan válhat az Intune a cégem előnyére?
A Microsoft Intune egy felhőalapú nagyvállalati mobileszköz-felügyeleti (EMM) szolgáltatás, amely segítséget nyújt a munkatársak hatékonyságának fenntartásához a vállalati adatok védelmének megőrzése mellett.

Az Intune-nal a következőkre nyílik lehetősége:

- Felügyelheti a munkatársak által a vállalati adatok elérésére használt mobileszközöket.
- Felügyelheti a munkatársak által használt alkalmazásokat.
- Megóvhatja vállalati adatokat, szabályozva azt, ahogyan a munkatársak elérik és megosztják őket.
- Gondoskodhat arról, hogy az eszközök és az alkalmazások megfeleljenek a vállalat biztonsági követelményeinek.

## <a name="common-business-problems-that-intune-helps-solve"></a>Az Intune segítségével megoldható gyakori üzleti problémák

* [A helyszíni e-mailek és adatok védelme a mobileszközökről történő biztonságos hozzáférés lehetővé tételéhez](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Az Office 365 e-mailjeinek és adatainak védelme a mobileszközökről történő biztonságos hozzáférés lehetővé tételéhez](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Vállalati tulajdonú telefonok kiadása az informatikai dolgozóknak](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [„Saját eszközök használata” (BYOD) vagy „személyes eszközök” program ajánlása az összes dolgozónak](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Az Office 365 nem felügyelt nyilvános kioszkból történő biztonságos elérésének engedélyezése a dolgozók számára](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Korlátozott használatú megosztott táblagépek kiadása adott feladattal foglalkozó dolgozóknak](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Gyorsútmutatók

Tisztában vagyunk azzal, hogy a mobileszközök kezelésének megkezdése bonyolult lehet. A vállalat nevében számos különböző döntést kell meghoznia. A következő rövid útmutatók segítségével elsajátíthatja az Intune-t, és elvégezheti a gyakori feladatok elvégzését a minimális időtartamra.

A rövid útmutatókat a lap bal oldalán található **Tartalomjegyzék használatával** követheti.

- [Próbálja ki ingyenesen az Intune alkalmazást](free-trial-sign-up.md) – Az Intune tesztkörnyezetben történő kipróbálásához hozzon létre egy ingyenes előfizetést.    
- [Felhasználó létrehozása](quickstart-create-user.md) – A felhasználók Intune-ba való felvételével engedélyezheti nekik, hogy mobileszközről is elérjék a céges erőforrásokat.
- [Hozzon létre egy csoportot](quickstart-create-group.md) – a felhasználókat csoportokba rendezve könnyebben kezelheti a hozzájuk tartozó szabályzatokat és alkalmazásokat.
- [Automatikus regisztráció beállítása](../enrollment/quickstart-setup-auto-enrollment.md) – az Intune beállítása az eszközök automatikus regisztrálására, amikor adott felhasználók bejelentkeznek a Windows 10-es eszközökre.
- [Az eszköz regisztrálása](../enrollment/quickstart-enroll-windows-device.md) – vegye fel az Intune-felhasználó szerepkörét, és regisztrálja eszközét az Intune-ban. Ezután térjen vissza az Intune-hoz, és ellenőrizze, hogy az eszköz regisztrálása sikeresen megtörtént-e.
- [Eszközmegfelelőségi szabályzat létrehozása](../protect/quickstart-set-password-length-android.md) – Létrehozhat egy megfelelőségi szabályzatot egy eszközhöz, és hozzárendelhet egy csoportot a szabályzathoz.
- [Értesítések küldése a nem megfelelő eszközökre](../protect/quickstart-send-notification.md) – értesítés küldése e-mailben a nem megfelelő eszközökkel rendelkező munkatársaknak a megfelelőségi szabályzat létrehozásával és hozzárendelésével.
- [Alkalmazás hozzáadása és hozzárendelése](../apps/quickstart-add-assign-app.md) – Hozzáadhat és hozzárendelhet egy alkalmazást a cég alkalmazottaihoz.
- [Alkalmazásvédelmi szabályzat létrehozása és hozzárendelése](../apps/quickstart-create-assign-app-policy.md) – Létrehozhat és hozzárendelhet egy alkalmazásvédelmi szabályzatot egy ügyfélalkalmazáshoz a végfelhasználó eszközén.
- [Egyéni szerepkör létrehozása és hozzárendelése](create-custom-role.md) – Létrehozhat és hozzárendelhet egy specifikus engedélyeket biztosító egyéni szerepkört a biztonsági műveleti részleg számára. 
- [E-mail-profil létrehozása iOS-eszközökhöz](../configuration/quickstart-email-profile.md) – Létrehozhat egy e-mail-profilt iOS-eszközökhöz.

## <a name="prerequisites"></a>Előfeltételek

A Kezdés előtt aktiválnia kell egy Intune-beli rendszergazdai és bérlői fiókot. [Az Intune ingyenes](free-trial-sign-up.md), tesztkörnyezetben történő kipróbálásához hozzon létre egy ingyenes előfizetést. A jelenlegi előfizetők is elvégezhetik ezeket a tevékenységeket az élő bérlőn. Ezek az első lépéseket bemutató cikkek feltételezik, hogy tesztelési eszközökön dolgozik.

Az Első lépések útmutató összes feladatának elvégzéséhez az is szükséges, hogy Ön a cég globális rendszergazdája legyen.

## <a name="intune-architecture"></a>Az Intune architektúrája

Az Intune az Enterprise Mobility + Security (EMS) megoldás mobileszköz- és mobilalkalmazás-felügyeletért felelős összetevője. Szorosan együttműködik más EMS-összetevőkkel, így az identitáskezelés és a hozzáférés-vezérlés terén az Azure Active Directoryval (Azure AD), valamint az adatvédelem terén az Azure Information Protectionnel. Ha az Office 365-mel használja, a munkaerőt minden eszközén hatékonyabbá teheti, miközben a szervezet adatainak védelmét is lehetővé teszi.

![A Microsoft Intune magas szintű architekturális diagramja](./media/get-started-evaluation/intunearchitecture.svg)

## <a name="next-steps"></a>További lépések

[Az Azure használatának első lépései](tutorial-walkthrough-intune-portal.md) – Ebből a gyakorlatból megismerkedhet az Azure Portal felépítésével, és megtudhatja, hogyan módosíthatja a megjelenő oldalt.

## <a name="learn-more"></a>További információ

- [Mi az az Intune?](what-is-intune.md)
- [Mi az az Azure Portal?](what-is-intune.md)
- [Eszközök és alkalmazások életciklusa](device-lifecycle.md)
