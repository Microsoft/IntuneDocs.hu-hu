---
title: Intune-regisztráció beállítása androidos vállalati dedikált eszközökhöz
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan regisztrálhat androidos vállalati dedikált eszközöket az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 118cd6e1d2506e5eb8d35ff8a27cc70f33a26697
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71304642"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Androidos vállalati dedikált eszközök Intune-regisztrációjának beállítása

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Android Enterprise támogatja a vállalat által birtokolt, egyetlen használatú, kioszk stílusú eszközöket a dedikált eszközökhöz beállított megoldással. Az ilyen eszközöknek egyetlen rendeltetése van, például digitális aláírás, jegynyomtatás vagy leltárkezelés, hogy csak néhányat említsünk. A rendszergazdák alkalmazások és webes hivatkozások egy adott körére korlátozzák az eszköz használatát. Ez azt is megakadályozza, hogy a felhasználók más alkalmazásokat adjanak az eszközhöz, vagy más műveleteket hajtsanak végre rajta.

Az Intune segítségével alkalmazásokat és beállításokat telepíthet az androidos vállalati dedikált eszközökre. Az Android Enterprise-ról az [Android Enterprise-követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)című témakörben olvashat részletesebben.

Az ezen a módon felügyelt eszközök felhasználói fiók nélkül vannak regisztrálva az Intune-ban, és egyetlen végfelhasználóhoz sincsenek hozzárendelve. Nem rendeltetésük olyan személyes használatra szánt, vagy sok felhasználóspecifikus adatot igénylő alkalmazások futtatása, mint az Outlook vagy a Gmail.

## <a name="device-requirements"></a>Eszközkövetelmények

Az eszközöknek meg kell felelniük az alábbi követelményeknek, amelyeket androidos vállalati dedikált eszközként kell kezelni:

- Android 5.1 vagy újabb operációs rendszer.
- Az eszközökön olyan Android-disztribúciónak kell futnia, amely kapcsolódni tud a Google Mobile Services (GMS) szolgáltatáshoz. Az eszközöknek el kell érniük a GMS-t, és képesnek kell lenniük a GMS-hez való kapcsolódásra.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Androidos vállalati dedikált eszközök felügyeletének beállítása

Az Android Enterprise dedikált eszközök felügyeletének beállításához kövesse az alábbi lépéseket:

1. A mobileszközök kezelésének előkészítését a [**Microsoft Intune** mint mobileszköz-felügyeleti (MDM) szolgáltató megadása](mdm-authority-set.md) című témakör ismerteti. Ezt elég egyszer beállítani, amikor először állítja be az Intune-t a mobileszközök felügyeletére.
2. [Kapcsolódjon az Intune-bérlői fiókhoz a felügyelt Google Play-fiókkal](connect-intune-android-enterprise.md).
3. [Regisztrációs profil létrehozása](#create-an-enrollment-profile).
4. [Eszközcsoport létrehozása](#create-a-device-group).
5. [A dedikált eszközök regisztrálása](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Beléptetési profil létrehozása

> [!NOTE]
> Ha egy jogkivonat lejárt, a hozzá társított profil nem jelenik meg az **eszközök beléptetése** > **Android-regisztráció** > **vállalat által birtokolt dedikált eszközök**területen. Az aktív és az inaktív tokenekhez kapcsolódó összes profil megjelenítéséhez kattintson a **Filter (szűrő** ) elemre, és jelölje be az "aktív" és az "inaktív" házirend-állapotok jelölőnégyzeteit. 

Létre kell hoznia egy regisztrációs profilt, hogy regisztrálni tudja a dedikált eszközöket. A profil a létrehozásakor ad egy regisztrációs jogkivonatot (véletlenszerű karakterlánc) és egy QR-kódot. Az eszköz Android operációs rendszerének és verziójától függően a jogkivonat vagy a QR-kód segítségével [regisztrálhat a dedikált eszközt](#enroll-the-dedicated-devices).

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza az **eszközök beléptetése** > **Android-regisztráció** > **vállalat által birtokolt dedikált eszközök**elemet.
2. Válassza a **Létrehozás** lehetőséget, és töltse ki a kötelező mezőket.
    - **Név**: Írjon be egy nevet, amelyet a profil dinamikus eszközcsoport-csoporthoz való hozzárendeléséhez fog használni.
    - **Jogkivonat lejárati dátuma**: A jogkivonat lejárati dátuma. A Google legfeljebb 90 napos érvényességi időszakot engedélyez.
3. Válassza a **Létrehozás** elemet a profil mentéséhez.

### <a name="create-a-device-group"></a>Eszközcsoport létrehozása

A cél lehet alkalmazás, és hozzárendelt vagy dinamikus eszközcsoportokra vonatkozó szabályzat is. A dinamikus AAD-eszközcsoportokat a következő lépesekkel konfigurálhatja úgy, hogy automatikusan felvegyék a megadott regisztrációs profillal regisztrált eszközöket:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza a **csoportok** > **minden** > csoport**új csoport**lehetőséget.
2. A **Csoport** panelen töltse ki a kötelező mezőket az alábbiak szerint:
    - **Csoport típusa**: Biztonság
    - **Csoport neve**: Írjon be egy intuitív nevet (például Factory 1 eszköz)
    - **Tagság típusa**: Dinamikus eszköz
3. Válassza a **Dinamikus lekérdezés hozzáadása** lehetőséget.
4. A **Dinamikus tagsági szabályok** panelen töltse ki a mezőket az alábbiak szerint:
    - **Dinamikus tagsági szabály hozzáadása**: Egyszerű szabály
    - **Eszközök hozzáadásának helye**: enrollmentProfileName
    - A középső mezőben válassza az **Egyezés** (Match) lehetőséget.
    - Az utolsó mezőben adja meg a korábban létrehozott regisztrációs profilt.
    A dinamikus tagságra vonatkozó szabályokról bővebben lásd [az AAD-csoportok dinamikus tagsági szabályait](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership) ismertető témakört. 
5. Válassza a **Lekérdezés hozzáadása** > **Létrehozás** lehetőséget.

### <a name="replace-or-remove-tokens"></a>Jogkivonatok cseréje vagy eltávolítása

- **Token cseréje**: Létrehozhat egy új tokent vagy QR-kódot, ha az egyik közeljövőben lejár a lecserélés token használatával.
- **Jogkivonat visszavonása**: A jogkivonat/QR-kód azonnal lejár. Ettől kezdve a jogkivonat/QR-kód többé nem használható. Ez a lehetőség a következő esetekben lehet hasznos:
  - a jogkivonat/QR-kód véletlenül meg lett osztva egy jogosulatlan féllel
  - minden regisztráció befejeződött, és a jogkivonatra/QR-kódra többé nincs szükség

Egy jogkivonat/QR-kód cseréje vagy visszavonása a már regisztrált eszközöket nem érinti.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza az **eszközök beléptetése** > **Android-regisztrációk** > **saját tulajdonú dedikált eszközök**elemet.
2. Válassza ki a profilt, amellyel dolgozni kíván.
3. Válassza a **Jogkivonat** lehetőséget.
4. A jogkivonat cseréjéhez válassza a **Jogkivonat cseréje** lehetőséget.
5. A jogkivonat visszavonásához válassza a **Jogkivonat visszavonása** lehetőséget.

## <a name="enroll-the-dedicated-devices"></a>A dedikált eszközök regisztrálása

Most már [regisztrálhat dedikált eszközeit](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Alkalmazások kezelése androidos vállalati dedikált eszközökön

Az androidos vállalati dedikált eszközökön csak a [kötelező](apps-deploy.md#assign-an-app) hozzárendelési típussal rendelkező alkalmazások telepíthetők. Az alkalmazások a felügyelt Google Play áruházból telepíthetők, ugyanúgy, mint az Android Enterprise Work Profile eszközei.

Az alkalmazások automatikusan frissítve lesznek a felügyelt eszközökön, amikor az alkalmazás fejlesztője frissítést tesz közzé a Google Playben.

Az Android Enterprise dedikált eszközökről származó alkalmazások eltávolításához a következők egyikét teheti:
- Törölje az alkalmazástelepítés Kötelező értékét.
- Hozzon létre központi eltávolítást az alkalmazáshoz.

## <a name="next-steps"></a>További lépések
- [Android-alkalmazások telepítése](apps-deploy.md)
- [Androidos konfigurációs szabályzatok hozzáadása](device-profiles.md)
