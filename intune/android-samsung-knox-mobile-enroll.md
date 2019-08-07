---
title: Samsung Knox mobileszköz beléptetési használata Android-eszközök automatikus regisztrálása
titleSuffix: Microsoft Intune
description: Útmutató az Android-eszközök a Samsung KME-vel történő regisztrálásához
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94c92f70844594fd8524f2e49c537f1afaadaf96
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783197"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Eszközök automatikus regisztrációja a Samsung Knox Mobile Enrollmenttel

Ez a témakör segít beállítani az Intune-t támogatott Android-eszközök a Samsung Knox Mobile Enrollmenttel (KME-vel) történő regisztrációjához. Az Intune a Samsung Knox Mobile Enrollmenttel (KME-vel) való használatával nagy mennyiségű céges tulajdonú Android-eszközt regisztrálhat, amikor a végfelhasználók először bekapcsolják az eszközüket, és egy Wi-Fi- vagy mobilhálózathoz csatlakoznak. A Knox Deployment App használatával az eszközök Bluetooth vagy NFC segítségével is regisztrálhatók.

Ha engedélyezni szeretné a Samsung KME-vel történő Intune-regisztrációt, az Intune és a Samsung Knox portálját is használnia kell, ebben a sorrendben:

1. A Knox portálján:
    1. [Hozzon létre egy MDM-profilt](#create-mdm-profile)
    2. [Adjon hozzá eszközöket](#add-devices)
    3. [Rendeljen hozzá MDM-profilokat az eszközökhöz](#assign-an-mdm-profile-to-devices)
2. A Knox portálon [konfigurálja a végfelhasználói bejelentkezést](#configure-how-end-users-sign-in).
3. [Terjessze az eszközöket](#distribute-devices).


A rendszer automatikusan hozzáadja az eszközazonosítókat (a sorozatszámokat és az IMEI-ket) a Knox portálhoz, amikor a Knox Deployment Programban részt vevő hivatalos viszonteladóktól vásárol eszközöket.


## <a name="prerequisites"></a>Előfeltételek

Ha regisztrálni szeretne eszközöket az Intune-ban a KME-vel, először a cégét kell regisztrálnia a Samsung Knox portálon. Ehhez kövesse az alábbi lépéseket:
1. Győződjön [meg arról, hogy a KME elérhető az Ön országában vagy régiójában](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): A KME több mint 55 országban/régióban érhető el. Győződjön meg arról, hogy a központi telepítés országa/régiója támogatott.

2. [Támogatott eszközök](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): A KME minden Samsung-eszközön elérhető, legalább Knox 2,4 for Android-regisztrációval, és legalább Knox 2,8 az Android Enterprise-regisztrációhoz.

3. [Hálózati követelmények](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Győződjön meg arról, hogy a szükséges tűzfal-és hálózati hozzáférési szabályok engedélyezve vannak a hálózaton.

4. [Regisztráljon egy Samsung](https://www2.samsungknox.com/en/user/register)-fiókra: Samsung-fiókra van szükség a KME regisztrálásához és engedélyezéséhez, valamint az összes Knox-beli nagyvállalati jogosultság egyetlen helyen történő kezeléséhez.

5. Regisztráció áttekintése: Miután elvégezte és elküldte a profilt, a Samsung végrehajtja az alkalmazás áttekintését, és vagy azonnal jóváhagyja, vagy egy függőben lévő felülvizsgálati állapotba helyezi a további követést. A fiók jóváhagyása után továbbhaladhat a következő lépésekre.

## <a name="create-mdm-profile"></a>MDM-profil létrehozása

Miután sikeresen regisztrálta a cégét, az alábbi adatokkal létrehozhat egy Microsoft Intune-os MDM-profilt a Knox portálon. A Knox portálon Android-és Android Enterprise-eszközökhöz egyaránt létrehozhat MDM-profilokat. 

### <a name="for-android-enterprise"></a>Android Enterprise számára

| MDM-profil – mezők| Kötelező? | értékek | 
|-------------------|-----------|-------| 
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt. 
|Profilnév       | Igen       |Adjon meg egy profilnevet. 
|Leírás        | Nem        |Adjon meg egy leírást a profilhoz. 
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme_deviceowner 
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Igen | A lehetőség kiválasztásával Android Enterprise-ként regisztrálhatja az eszközt. 
|Támogatott mobileszköz-kezelés      | Igen       |Microsoft Intune 
|A rendszeralkalmazások engedélyezettek maradnak | Nem | A lehetőség kiválasztásával biztosíthatja, hogy az összes alkalmazás engedélyezve legyen, és elérhető legyen a profilhoz. Ha ez a beállítás nincs bejelölve, csak nagyon korlátozott számú rendszeralkalmazás jelenik meg az eszköz alkalmazástálcáján. Az olyan alkalmazások, mint például az e-mail-alkalmazás, rejtve maradnak. 
|Egyéni JSON        | Nem        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Adja meg az Intune beléptetési token sztringjét"}. Ismerje meg, a [Beléptetési profil létrehozásának](android-kiosk-enroll.md) folyamatát. 
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt. 

### <a name="for-android"></a>Android rendszerhez

Részletes útmutatásért tekintse meg a [Samsung Knox profil telepítése varázsló](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) utasításait.

| MDM-profil – mezők| Kötelező? | értékek |
|-------------------|-----------|-------|
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt.
|Profilnév       | Igen       |Adjon meg egy profilnevet.
|leírás        | Nem        |Adjon meg egy leírást a profilhoz.
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Nem | Android esetén hagyja üresen a beállítást. A beállítás csak Android Enterprise esetén érvényes.
|A telepítővarázsló kihagyása  | Nem        |Válassza ezt a beállítást, ha ki szeretné hagyni a szabványos eszközbeállítási lépéseket a végfelhasználó nevében.
|Regisztráció megszakításának engedélyezése a végfelhasználó számára | Nem | Válassza ezt a beállítást, ha engedélyezni szeretné a felhasználók számára, hogy megszakítsák a KME-t.
|Egyéni JSON        | Nem        |Hagyja üresen a mezőt.
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt.
Knox-licenc társítása a profilhoz | Nem | Hagyja üresen a beállítást. A KME-vel történő Intune-regisztrációhoz nincs szükség Knox-licencre.

## <a name="add-devices"></a>Eszközök felvétele

Ha MDM-profilokat szeretne hozzárendelni az eszközökhöz, a támogatott Samsung Knox-eszközöket hozzá kell adnia a Knox portálhoz az alábbi módszerek egyikével:
- **A Samsung által jóváhagyott viszonteladó (k) használata:** Ezt a módszert akkor használja, ha az egyik Samsung által jóváhagyott viszonteladótól vásárol eszközöket. Ha jóváhagyja, a viszonteladók automatikusan feltölthetnek eszközöket. [A viszonteladók hozzáadásáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **A Knox üzembehelyezési alkalmazás (KDA) használata:** Akkor használja ezt a módszert, ha olyan meglévő eszközöket használ, amelyeket a KME használatával kell regisztrálni. Ezzel a módszerrel Bluetooth vagy NFC használatával adhat hozzá eszközöket a Knox portálhoz. [A KDA használatáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>MDM-profil hozzárendelése az eszközökhöz
A regisztráció előtt a Knox portálon hozzá kell rendelnie egy MDM-profilt a hozzáadott eszközökhöz. [Az eszközkonfigurációról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>A végfelhasználói bejelentkezés konfigurálása

Az Intune-ba androidos KME-vel beléptetett eszközök esetében a következőképp konfigurálhatja a végfelhasználói bejelentkezést:

- **Felhasználónév-társítás nélkül:** A Knox-portál **eszköz részletei**területén hagyja üresen a **felhasználói azonosító** és a **jelszó** mezőket a hozzáadott eszközökhöz. Így a végfelhasználónak az Intune-regisztráció során nevet és jelszót is meg kell adnia.

- **Felhasználónévvel társítva:** A Knox-portál **eszköz részletei**területén adjon meg egy **felhasználói azonosítót** (például egy felhasználónevet a hozzárendelt felhasználóhoz vagy egy [eszköz](https://docs.microsoft.com/intune/device-enrollment-manager-enroll) beléptetési kezelői fiókhoz) a hozzáadott eszközökhöz. Így a végfelhasználó felhasználó neve előre ki lesz töltve, az Intune-regisztráció során pedig neki egy jelszót kell megadnia.

> [!NOTE]
>
>A felhasználó-hozzárendelés csak Android-eszközök beléptetésére vonatkozik. Ha meghatároz egy felhasználó-hozzárendelést, csak a hozzárendelt felhasználó regisztrálhatja az eszközt a KME-vel. Ez az eszköz gyári alaphelyzetbe állítása után is így marad. Ha nem határoz meg felhasználó-hozzárendelést a Knox portálon, bármely, érvényes Intune-licenccel rendelkező felhasználó regisztrálhatja az eszközt a KME-vel.
>

## <a name="distribute-devices"></a>Eszközök terjesztése

Az MDM-profil létrehozása és hozzárendelése, a felhasználónév társítása és az eszközök vállalati tulajdonúként való azonosítása után megkezdheti az eszközök terjesztését a felhasználók között.

További segítségre van szüksége? Tekintse meg a teljes [Knox mobileszköz-regisztrációs felhasználói útmutatót](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Gyakori kérdések

- **Eszköz tulajdonosának támogatása:** Az Intune az eszközök csak kioszk módban való regisztrálását támogatja az Android Enterprise használatával. Egyéb Android Enterprise eszköztulajdonosi módok támogatására is sor kerül, amint elérhetővé válnak az Intune-ban.

- **A munkahelyi profil nem támogatott:** A KME a vállalati eszközök regisztrálási módszere és az Android munkahelyi profilban regisztrált eszközök biztosítják, hogy a munkahelyi és a személyes adatmennyiség külön legyen a személyes eszközökön. Tehát eszközök regisztrálása a munkahelyi profilba KME használatával nem támogatjuk az Intune-ban.

- **Gyári beállítások visszaállítása az Android Enterprise-ba való regisztráláshoz:** Ha a már beállított eszközöket kell beállítani, az eszközöknek gyári beállításokra van szükségük az Android Enterprise-ban való regisztráláskor.

- **Frissítések a Google Play-fiók használatával:** A Google Play-fiók nem szükséges az eszköz Microsoft Intune való regisztrálásához. Az Intune Céges portál alkalmazás jövőbeli frissítései azonban ezt kötelezővé tehetik. A Google Eszköztulajdonos-regisztrációhoz nem szükséges Google Play-fiók.

- **A "password" mezőt a rendszer figyelmen kívül hagyja:** Ha a Knox-portálon a **jelszó** mező fel van töltve az **eszköz részletei** között, a Intune céges portál alkalmazás figyelmen kívül hagyja az Android-regisztráció során. A végfelhasználónak meg kell adnia egy jelszót az eszközön az eszközregisztráció befejezéséhez.


## <a name="getting-support"></a>Támogatás igénybevétele
További információ [a Samsung KME támogatásáról](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


