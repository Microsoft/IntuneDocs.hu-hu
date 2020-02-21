---
title: Interaktív forgatókönyv – a Microsoft Edge for Mobile üzembe helyezése
titleSuffix: Microsoft Intune
description: Ismerje meg a Microsoft Edge for Mobile üzembe helyezésének interaktív forgatókönyvét a Microsoft 365 Eszközkezelő portálról.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afb8f431ae301fe74f420c11205a7ed2637434b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514625"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Interaktív forgatókönyv – a Microsoft Edge for Mobile üzembe helyezése 

Ennek az [interaktív forgatókönyvnek](~/fundamentals/guided-scenarios-overview.md)a követésével a Microsoft Edge alkalmazást hozzárendelheti a felhasználókhoz iOS/IPadOS vagy Android rendszerű eszközökön a szervezetében. Az alkalmazás hozzárendelésével lehetővé teheti, hogy a felhasználók zökkenőmentesen böngésszék a tartalmat a vállalati eszközeik használatával. 

A Microsoft Edge lehetővé teszi a felhasználók számára, hogy a beépített funkciókkal, amelyek segítségével összevonhatja, rendezheti és kezelheti a munkahelyi tartalmakat. Az iOS/iPadOS és az Android rendszerű eszközök azon felhasználói, akik a Microsoft Edge alkalmazásban lévő vállalati Azure AD-fiókkal jelentkeznek be, megkeresik a böngészőben előre betöltött böngészőt a munkahelyi **Kedvencek** és a definiált webhely-szűrők használatával.

> [!NOTE]
> Ha letiltotta a felhasználók számára az iOS/iPadOS vagy Android rendszerű eszközök regisztrálását, akkor ez a forgatókönyv nem engedélyezi a regisztrációt, és a felhasználóknak maguknak kell telepíteniük az Edge-t.
Az Intune-szabályzatok által engedélyezett Microsoft Edge Enterprise-funkciók a következők: 

- **Kettős identitás** – a felhasználók egy munkahelyi fiókot és egy személyes fiókot is hozzáadhatnak a böngészéshez. A két identitás között teljes elkülönítés áll fenn, amely hasonló az Office 365 és az Outlook architektúrájának és felhasználói felületéhez. Az Intune-rendszergazdák a munkahelyi fiókon belül megadhatják a védett böngészési élmény kívánt szabályzatait. 
- **Intune app Protection-házirend-integráció** – a rendszergazdák mostantól megcélozhatja az alkalmazás-védelmi szabályzatokat a Microsoft Edge számára, beleértve a kivágási, másolási és beillesztési műveleteket, a képernyőfelvételek megakadályozását, valamint annak biztosítását, hogy a felhasználó által kijelölt hivatkozások csak más kezelt alkalmazásokban legyenek
- **Azure alkalmazásproxy-integráció** – a rendszergazdák vezérelhetik az SaaS-alkalmazásokhoz és a webalkalmazásokhoz való hozzáférést, így biztosítva, hogy a böngészőalapú alkalmazások csak a biztonságos Microsoft Edge böngészőben fussanak, legyen szó a vállalati hálózatról vagy az internetről való csatlakozásról. 
- A **felügyelt kedvencek és a Kezdőlap parancsikonjai** – a könnyű hozzáférés érdekében a rendszergazdák megadhatják, hogy az URL-címek megjelenjenek a Kedvencek területen, amikor a végfelhasználók a vállalati környezetben vannak. A rendszergazdák megadhatnak egy Kezdőlap parancsikont, amely az elsődleges hivatkozásként jelenik meg, amikor a vállalati felhasználó új lapot nyit meg, vagy egy új lapot a Microsoft Edge-ben.

## <a name="prerequisites"></a>Előfeltételek

- [Az Mdm-szolgáltató beállítása az Intune](mdm-authority-set.md#set-mdm-authority-to-intune) -ra – a mobileszköz-kezelési (Mdm) szolgáltatói beállítás határozza meg az eszközök felügyeletének módját. Ahhoz, hogy a felhasználók felügyeletre tudják regisztrálni eszközeiket, a rendszergazdának be kell állítania egy MDM-szolgáltatót.
- Intune-rendszergazdai engedélyek szükségesek:
    - Felügyelt alkalmazások olvasási, létrehozási, törlési és hozzárendelési engedélyek
    - Mobile apps – olvasási, létrehozási és hozzárendelési engedélyek
    - A házirend beállítja az olvasási, létrehozási és hozzárendelési engedélyeket
    - Szervezet olvasási, frissítési engedélye

## <a name="step-1---introduction"></a>1\. lépés – bevezetés

A **Microsoft Edge for Mobile interaktív forgatókönyv üzembe helyezését** követve a Microsoft Edge alapszintű üzembe helyezését fogja beállítani az iOS/iPadOS és az Android-felhasználók kiválasztott csoportja számára. Ez a telepítés a **kettős identitást** és a **felügyelt kedvenceket, valamint a Kezdőlap parancsikonjait**fogja megvalósítani. Emellett a kiválasztott felhasználók által beléptetett eszközök automatikusan az Intune által telepített Microsoft Edge alkalmazást fogják telepíteni. Ez az automatikus telepítés minden felhasználó által vezérelt regisztrációs típuson bekövetkezik, többek között a következők: 
- iOS/iPadOS-regisztráció a Céges portál alkalmazáson keresztül 
- iOS/iPadOS felhasználó-affinitási regisztráció az Apple Business Manageren keresztül 
- Régi Android-regisztráció a Céges portál alkalmazáson keresztül 

Ez az interaktív forgatókönyv automatikusan lehetővé teszi, hogy a **MyApps** megjelenjenek a Microsoft Edge-Kedvencek között, és konfigurálja a böngészőt az Intune céges portál alkalmazáshoz beállított arculattal. 

### <a name="what-you-will-need-to-continue"></a>A folytatáshoz szükséges művelet
A felhasználók számára szükséges munkahelyi kedvenceket és a webböngészéshez szükséges szűrőket kérjük. A folytatás előtt győződjön meg arról, hogy a következő feladatokat hajtja végre:

- Felhasználók hozzáadása az Azure AD-csoportokhoz. További információkért lásd: [alapszintű csoport létrehozása és Tagok hozzáadása Azure Active Directory használatával](https://go.microsoft.com/fwlink/?linkid=2102458).
- IOS-/iPadOS-vagy Android-eszközök regisztrálása az Intune-ban. További információ: [eszközök beléptetése](https://go.microsoft.com/fwlink/?linkid=2102547).
- A Microsoft Edge-ben hozzáadandó munkahelyi kedvencek listájának összegyűjtése.
- A Microsoft Edge-ben érvényesíteni kívánt webhely-szűrők listájának összegyűjtése.

## <a name="step-2---basics"></a>2\. lépés – alapismeretek

Ebben a lépésben meg kell adnia az új Microsoft Edge-szabályzatok nevét és leírását. Ezek a házirendek később is szerepelhetnek, ha módosítania kell a hozzárendeléseket és a konfigurációkat. Az interaktív forgatókönyv a Microsoft Edge iOS/iPadOS alkalmazást is hozzáadja az iOS-és iPadOS-eszközökhöz, valamint egy Microsoft Edge Android-alkalmazást az Android-eszközökhöz. Emellett ez a lépés az alkalmazások konfigurációs szabályzatait is létrehozza.

## <a name="step-3---configuration"></a>3\. lépés – konfiguráció

Ebben a lépésben az interaktív forgatókönyv úgy konfigurálja a Microsoft Edge-t, hogy megjelenítse az Intune-on keresztül a felhasználókhoz rendelt összes más alkalmazást, és ugyanazt a arculatot használja, mint a Microsoft Intune Céges portál alkalmazás. A Microsoft Edge **-t a Kezdőlap helyi URL-címével**, a **felügyelt könyvjelzők**listájával és a **letiltott URL-címek**listájával is konfigurálhatja. A **Kezdőlap parancsikonjának URL-címe** az első ikonként jelenik meg a felhasználók számára a keresősáv alatt, amikor új lapot nyitnak meg a Microsoft Edge-ben az eszközön. A **felügyelt könyvjelzők** a felhasználók kedvenc URL-címeinek listája, amelyek a Microsoft Edge munkahelyi környezetben való használata esetén érhetők el. A **letiltott URL-címek** azokat a helyeket határozzák meg, amelyeket a felhasználók a munkahelyi környezetben blokkoltak. Minden más hely engedélyezve lesz. 

## <a name="step-4---assignments"></a>4\. lépés – hozzárendelések

Ebben a lépésben kiválaszthatja azokat a felhasználói csoportokat, amelyeket fel szeretne venni, hogy a Microsoft Edge Mobile be legyen állítva a működésre. A Microsoft Edge a felhasználók által beléptetett iOS-/iPadOS-és Android-eszközökön is telepítve lesz.

## <a name="step-5---review--create"></a>5\. lépés – felülvizsgálat + létrehozás

Az utolsó lépés lehetővé teszi a konfigurált beállítások összefoglalásának áttekintését. Miután áttekintette a beállításokat, kattintson a **Létrehozás** gombra az interaktív forgatókönyv befejezéséhez. 

> [!NOTE]
> Az Edge akár 12 órát is igénybe vehet a konfiguráció fogadásához. További információ: [Microsoft Intune alkalmazás-konfigurációs szabályzatai](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Az interaktív forgatókönyv befejezését követően megjelenik egy Összegzés. Az összegzésben felsorolt erőforrásokat módosíthatja, azonban a osztályalapú megjelenítő tábla nem lesz mentve.

## <a name="next-steps"></a>További lépések

- A Microsoft Edge használatának biztonsága az Intune app Protection-házirendek integrálásának beállításával. További információ: [Application Protection-szabályzatok a Microsoft Edge-hez](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Ha rendelkezik intranetes helyekkel, tekintse meg a hozzáférés védelme az Azure Application proxy-integrációval című webhelyet. További információ: [Application proxy-beállítások konfigurálása a Microsoft Edge-hez](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

