---
title: Android-eszközök automatikus regisztrálása a Samsung Knox Mobile beléptetésével
titleSuffix: Microsoft Intune
description: Útmutató az Android-eszközök a Samsung KME-vel történő regisztrálásához
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f290370dd6ec05677a7073d9ca3edd854c9aa5e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505586"
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


Az eszközök azonosítóinak (sorozatszámok és IMEI-EK) listáját a rendszer automatikusan hozzáadja a Knox-portálhoz, amikor a Knox üzembe helyezési programban részt vevő, jóváhagyott viszonteladóknak vásárol eszközöket.


## <a name="prerequisites"></a>Előfeltételek

Ha regisztrálni szeretne eszközöket az Intune-ban a KME-vel, először a cégét kell regisztrálnia a Samsung Knox portálon. Ehhez kövesse az alábbi lépéseket:
1. Győződjön [meg arról, hogy a KME elérhető az Ön országában vagy régiójában](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): a KME több mint 55 országban/régióban érhető el. Győződjön meg arról, hogy a központi telepítés országa/régiója támogatott.

2. [Támogatott eszközök](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): A KME Android-eszközregisztráció esetén a minimum Knox 2.4-es, Android vállalati regisztráció esetén pedig a minimum Knox 2.8-as verziójú Samsung-eszközökön érhető el.

3. [Hálózati követelmények](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Győződjön meg róla, hogy engedélyezte a megfelelő, tűzfallal és hálózati hozzáféréssel kapcsolatos szabályokat a hálózatán.

4. [Samsung-fiók regisztrálása](https://www2.samsungknox.com/en/user/register): A KME engedélyezéséhez és a regisztrációhoz, valamint a Knox Enterprise-jogosultságok egyetlen helyen történő kezeléséhez egy Samsung-fiókra van szüksége.

5. Regisztráció áttekintése: miután elvégezte és elküldte a profilt, a Samsung áttekinti az alkalmazást, és vagy azonnal jóváhagyja, vagy egy függőben lévő felülvizsgálati állapotba helyezi a további követés érdekében. A fiók jóváhagyása után további lépéseket is végrehajthat.

## <a name="create-mdm-profile"></a>MDM-profil létrehozása

Miután sikeresen regisztrálta a cégét, az alábbi adatokkal létrehozhat egy Microsoft Intune-os MDM-profilt a Knox portálon. A Knox portálon Android-és Android Enterprise-eszközökhöz egyaránt létrehozhat MDM-profilokat. 

### <a name="for-android-enterprise"></a>Android Enterprise számára

| MDM-profil – mezők| Kötelező? | Értékek | 
|-------------------|-----------|-------| 
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt. 
|Profilnév       | Igen       |Adjon meg egy profilnevet. 
|Description        | Nem        |Adjon meg egy leírást a profilhoz. 
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme_deviceowner 
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Igen | A lehetőség kiválasztásával Android Enterprise-ként regisztrálhatja az eszközt. 
|Támogatott mobileszköz-kezelés      | Igen       |Microsoft Intune 
|A rendszeralkalmazások engedélyezettek maradnak | Nem | A lehetőség kiválasztásával biztosíthatja, hogy az összes alkalmazás engedélyezve legyen, és elérhető legyen a profilhoz. Ha ez a beállítás nincs bejelölve, a rendszer csak a rendszeralkalmazások egy korlátozott készletét jeleníti meg az eszköz alkalmazások tálcáján. Az olyan alkalmazások, mint például az e-mail-alkalmazás, rejtve maradnak. 
|Egyéni JSON        | Nem        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Enter Intune enrollment token string"}. Ismerje meg, a [Beléptetési profil létrehozásának](android-kiosk-enroll.md) folyamatát. 
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt. 

### <a name="for-android"></a>Android rendszerhez

Részletes útmutatásért tekintse meg a [Samsung Knox profil telepítése varázsló](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) utasításait.

| MDM-profil – mezők| Kötelező? | Értékek |
|-------------------|-----------|-------|
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt.
|Profilnév       | Igen       |Adjon meg egy profilnevet.
|leírás        | Nem        |Adjon meg egy leírást a profilhoz.
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Nem | Android esetén hagyja üresen a beállítást. Ez a beállítás csak az Android Enterprise rendszerre érvényes.
|A telepítővarázsló kihagyása  | Nem        |Válassza ezt a lehetőséget, ha ki szeretné hagyni a végfelhasználó számára a szabványos eszköz telepítési kéréseit.
|Regisztráció megszakításának engedélyezése a végfelhasználó számára | Nem | Válassza ezt a beállítást, ha engedélyezni szeretné a felhasználók számára, hogy megszakítsák a KME-t.
|Egyéni JSON        | Nem        |Hagyja üresen a mezőt.
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt.
Knox-licenc társítása a profilhoz | Nem | Hagyja üresen a beállítást. Az Intune-ba való regisztráláshoz nem szükséges Knox-licenc.

## <a name="add-devices"></a>Eszközök felvétele

Ha MDM-profilokat szeretne hozzárendelni az eszközökhöz, a támogatott Samsung Knox-eszközöket hozzá kell adnia a Knox portálhoz az alábbi módszerek egyikével:
- **A Samsung által jóváhagyott viszonteladó (k) használata:** Ezt a módszert akkor használja, ha az egyik Samsung által jóváhagyott viszonteladótól vásárolja meg az eszközöket. Ha jóváhagyja, a viszonteladók automatikusan feltölthetnek eszközöket. [A viszonteladók hozzáadásáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **A Knox Deployment App (KDA) segítségével:** Használja ezt a módszert, ha a meglévő eszközeit szeretné regisztrálni a KME-vel. Ezzel a módszerrel Bluetooth vagy NFC használatával adhat hozzá eszközöket a Knox portálhoz. [A KDA használatáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>MDM-profil hozzárendelése az eszközökhöz
A regisztráció előtt a Knox portálon hozzá kell rendelnie egy MDM-profilt a hozzáadott eszközökhöz. [Az eszközkonfigurációról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>A végfelhasználói bejelentkezés konfigurálása

Az Intune-ba androidos KME-vel beléptetett eszközök esetében a következőképp konfigurálhatja a végfelhasználói bejelentkezést:

- **Felhasználónév-hozzárendelés nélkül:** A Knox portál **Eszközadatok** területén hagyja üresen a hozzáadott eszközök **Felhasználóazonosító** és a **Jelszó** mezőit. Ehhez a beállításhoz a felhasználónak a felhasználónevet és a jelszót is meg kell adnia az Intune-ba való regisztráláskor.

- **Felhasználónév-hozzárendeléssel:** A Knox portál **Eszközadatok** területén adjon meg egy **Felhasználóazonosítót** (például a hozzárendelt felhasználó vagy a [Készülékregisztráció-kezelő](device-enrollment-manager-enroll.md) fiókjának felhasználónevét) a hozzáadott eszközöknek. Ez a beállítás előre feltölti a felhasználónevet, és megköveteli a végfelhasználótól, hogy jelszót adjon meg az Intune-ba való regisztráláskor.

> [!NOTE]
>
>A felhasználói társítás csak az Android-eszközök rendszergazdai regisztrálására vonatkozik. Ha meghatároz egy felhasználó-hozzárendelést, csak a hozzárendelt felhasználó regisztrálhatja az eszközt a KME-vel. Ez az eszköz gyári alaphelyzetbe állítása után is így marad. Ha nem határoz meg felhasználó-hozzárendelést a Knox portálon, bármely, érvényes Intune-licenccel rendelkező felhasználó regisztrálhatja az eszközt a KME-vel.
>Az Android Enterprise teljes körűen felügyelt eszközök esetében akkor is, ha a felhasználói társítás definiálva van, nem lesz továbbítva az eszköznek vagy nem köti az eszközt a felhasználóhoz.
>

## <a name="distribute-devices"></a>Eszközök terjesztése

Az MDM-profil létrehozása és hozzárendelése, a felhasználónév társítása és az eszközök vállalati tulajdonúként való azonosítása után megkezdheti az eszközök terjesztését a felhasználók között.

További segítségre van szüksége? Tekintse meg a teljes [KME felhasználói útmutatót](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Gyakori kérdések

- **Eszköz tulajdonosának támogatása:** - **eszköz tulajdonosának támogatása:** az Intune támogatja a dedikált és teljes mértékben felügyelt eszközök regisztrálását a KME-portál használatával. Egyéb Android Enterprise eszköztulajdonosi módok támogatására is sor kerül, amint elérhetővé válnak az Intune-ban.

- A **munkahelyi profil nem támogatott:** A KME a vállalati eszközök regisztrálási módszere és az Android munkahelyi profilban regisztrált eszközök biztosítják, hogy a munkahelyi és a személyes adatmennyiség külön legyen a személyes eszközökön. Így az eszközök a KME használatával történő beléptetése nem támogatott forgatókönyv az Intune-ban.

- **Gyári beállítások visszaállítása az Android Enterprise-regisztrációhoz:** A már beállított eszközök újrahasznosításakor az eszközön vissza kell állítani a gyári beállításokat az eszköz Android Enterprise-regisztrációja előtt.

- **Frissítések a Google Play-fiók használatával:** Nincs szükség Google Play-fiókra az eszköz Microsoft Intune való regisztrálásához. Az androidos eszközök rendszergazdai regisztrációja esetén azonban előfordulhat, hogy a Intune Céges portál alkalmazás jövőbeli frissítéseihez Google Play-fiókra lehet szükség az eszközön. Nincs szükség Google Play-fiókra a Google-eszköz tulajdonosának való regisztráláskor.

- **A "password" mezőt a rendszer figyelmen kívül hagyja:** Ha a Knox-portálon a **jelszó** mező fel van töltve az **eszköz részletei** között, a Intune céges portál alkalmazás figyelmen kívül hagyja az Android-regisztráció során. A végfelhasználónak meg kell adnia egy jelszót az eszközön az eszközregisztráció befejezéséhez.


## <a name="getting-support"></a>Támogatás igénybevétele
További információ [a Samsung KME támogatásáról](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


