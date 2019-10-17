---
title: Mit jelent az eszközök regisztrálása a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: Útmutató iOS, Android és Windows rendszerű eszközök regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb9aa6349a88f226c063703d6cb035b3c89636fd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503251"
---
# <a name="what-is-device-enrollment"></a>Mi az eszközregisztrálás?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune lehetővé teszi a dolgozók eszközeinek és alkalmazásainak, illetve a céges adatokhoz való hozzáférésük kezelését. Ezen mobileszköz-kezelés (MDM) használatához az eszközöket először regisztrálni kell az Intune szolgáltatásban. Ha egy eszköz regisztrálva van, egy MDM-tanúsítványt ad ki. Ez a tanúsítvány az Intune szolgáltatással való kommunikációra szolgál.

Amint az alábbi táblázatokban látható, a dolgozók eszközeit többféleképpen is lehet regisztrálni. Az egyes módszerek az eszköz tulajdonosától (személyes vagy céges), az eszköztípustól (iOS, Windows, Android) és a felügyeleti követelményektől (alaphelyzetbe állítások, affinitás, zárolás) függ.

Alapértelmezés szerint platformtól függetlenül minden eszköz regisztrációja engedélyezett az Intune-ban. Viszont [korlátozhatja az eszközöket platform szerint](enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="ios-enrollment-methods"></a>iOS-eszközök regisztrálási módszerei

| **Módszer** | **Alaphelyzetbe állítás szükséges** | [**Felhasználói affinitás**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Zárolás** | **Részletek** |
|:---:|:---:|:---:|:---:|:---:|
| | A regisztráció során az eszközök összes adata törölve lesz. | Minden eszközt egy felhasználóhoz társítja.| Ha igen, a felhasználók nem tudják törölni az eszközök regisztrációját. | |
|**[BYOD](#bring-your-own-device)** | Nem| Igen | Nem | [További információ](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Nem |Nem |Nem | [További információ](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| Igen | Nem kötelező megadni | Nem kötelező megadni|[További információ](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Igen | Nem kötelező megadni | Nem| [További információ](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Nem | Nem | Nem|[További információ](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS-eszközök regisztrálási módszerei
| **Módszer** |  **Alaphelyzetbe állítás szükséges** |  **Felhasználói affinitás** | **Zárolás** | **Részletek**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nem| Igen | Nem | [További információ](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nem |Nem |Nem  | [További információ](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| Igen | Nem kötelező megadni | Nem kötelező megadni|[További információ](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Windows-eszközök regisztrálási módszerei

| **Módszer** | **Alaphelyzetbe állítás szükséges** | **Felhasználói affinitás** | **Zárolás** | **Részletek**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nem | Igen | Nem | [További információ](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nem |Nem |Nem |[További információ](device-enrollment-manager-enroll.md)|
|**Automatikus regisztráció** | Nem |Igen |Nem | [További információ](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Igen |Igen |Nem | [További információ](enrollment-autopilot.md)
|**Csoportos regisztráció** |Nem |Nem |Nem | [További információ](windows-bulk-enroll.md) |
|**Közös felügyelet** |Nem |Igen |Nem | [További információ](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |Nem |Igen |Nem | [További információ](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Android-eszközök regisztrálási módszerei

| **Személyes** | **Regisztrációs módszerek** | **Alaphelyzetbe állítás szükséges** | **Felhasználói affinitás** | **Zárolás** | **Részletek**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android-eszköz rendszergazdája**|**Felhasználó által kezdeményezett Céges portál** | Nem | Igen | Nem | [További információ](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Androidos vállalati munkahelyi profil**|**Felhasználó által kezdeményezett Céges portál**| Nem | Igen | Nem | [További információ](android-work-profile-enroll.md)|


| **Vállalati** | **Regisztrációs módszerek** | **Alaphelyzetbe állítás szükséges** | **Felhasználói affinitás** | **Zárolás** | **Részletek**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android-eszköz rendszergazdája**|**[DEM](#device-enrollment-manager) céges portál használatával kezdeményezve**| Nem | Nem | Nem |[További információ](device-enrollment-manager-enroll.md)|
|**Android-eszköz rendszergazdája**|**(Előre deklarált IMEI vagy SN) Felhasználó által kezdeményezett Céges portál**| Nem | Igen | Nem | [További információ](./../corporate-identifiers-add.md)|
|**Android-eszköz rendszergazdája a zebra Mobility Extensions bővítménnyel**|**Céges portál használatával kezdeményezett felhasználó vagy [DEM](#device-enrollment-manager)**| Nem | Igen, ha a felhasználó kezdeményezte, nem, ha a [DEM](#device-enrollment-manager) kezdeményezte | Nem | [További információ](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise dedikált**|**NFC, token, QR-kód, nulla érintés**| Igen | Nem | Konfigurálható házirenden keresztül | [További információ](android-kiosk-enroll.md)|
|**Android Enterprise teljes körűen felügyelt**|**NFC, token, QR-kód, nulla érintés**| Igen | Igen | Konfigurálható házirenden keresztül | [További információ](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Saját eszközök használata (Bring Your Own Device)
Saját eszközök használata (BYOD) személyes tulajdonú telefonok, tabletták és számítógépek. A BYOD-eszközök regisztrálásához a felhasználók telepítik és futtatják a Céges portál alkalmazást. A program lehetővé teszi, hogy a felhasználók elérhessék a vállalati erőforrásokat, például az e-mailt.

## <a name="corporate-owned-device"></a>Céges eszköz
A [céges eszközök (COD)](corporate-identifiers-add.md) közé tartoznak a szervezet tulajdonában lévő és a dolgozóknak kiosztott telefonok, táblagépek és számítógépek. A céges eszközök (COD) regisztrációja olyan forgatókönyveket támogat, mint például az automatikus regisztráció, a megosztott eszközök vagy az előre engedélyezett regisztrációs követelmények. A céges eszközök regisztrálásának egy rendszergazdák és menedzserek által gyakran használt módja a készülékregisztráció-kezelő (DEM) alkalmazása. Az iOS-eszközök közvetlenül regisztrálhatók a Készülékregisztrációs program (DEP) Apple által biztosított eszközeivel. Az IMEI-számmal rendelkező eszközök is azonosíthatók és megcímkézve vállalati tulajdonban.

### <a name="device-enrollment-manager"></a>Készülékregisztráció-kezelő
Az eszközregisztráció-kezelő (DEM) egy speciális felhasználói fiók, amely több vállalati tulajdonú eszköz regisztrációjára és felügyeletére szolgál. A kezelők tudják telepíteni a Vállalati portált és regisztrálni számos, felhasználó nélküli eszközt. Az ilyen típusú eszközök például POS- vagy segédprogram-alkalmazásokhoz megfelelőek, de nem alkalmasak olyan felhasználók számára, akik hozzá szeretnének férni a levelezésükhöz vagy a vállalati erőforrásokhoz. További információ a [DEM](device-enrollment-manager-enroll.md) módszerről.

### <a name="apple-device-enrollment-program"></a>Apple Készülékregisztrációs program
Az Apple Készülékregisztrációs program (DEP) kezelése lehetővé teszi, hogy a "hálózaton keresztül" házirendet hozzon létre és telepítsen a DEP által megvásárolt és felügyelt iOS-és macOS-eszközökre. Az eszköz regisztrálása akkor történik meg, amikor a felhasználók első alkalommal bekapcsolják az eszközt, és futtatják a beállítási asszisztenst. Ez a módszer támogatja az iOS Supervised (Felügyelt) üzemmódját, amely lehetővé teszi konkrét funkciók beállítását az eszközön.

További információ az iOS-eszközök regisztrálásáról a DEP keretében:

- [Az iOS-eszközök regisztrálási módjának kiválasztása](ios-enroll.md)
- [iOS-eszközök regisztrálása a Készülékregisztrációs program segítségével](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
Az Apple Configurator segítségével a rendszergazdák a beállítási asszisztens használatával USB-kapcsolaton keresztül manuálisan előkészíthetnek minden vállalat által birtokolt eszközt. A rendszergazda létrehoz egy regisztrációs profilt, és exportálja azt az Apple Configuratorba. Amikor a felhasználók megkapják az eszközeiket, a rendszer felszólítja, hogy futtassa a beállítási asszisztenst az eszköz regisztrálásához. Ez a módszer támogatja az **iOS Supervised** (Felügyelt) üzemmódját, amely lehetővé teszi a következő funkciókat:
- Zárolt regisztráció
- Teljes képernyős mód és más speciális konfigurációk és korlátozások

További információk az eszközöknek az Apple Configurator és Beállítási asszisztens segítségével történő regisztrálásáról:

- [Az iOS-eszközök regisztrálási módjának kiválasztása](ios-enroll.md)
- [iOS-eszközök regisztrálása az Apple Configurator és a Beállítási asszisztens használatával](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
A közvetlen regisztrációhoz a rendszergazdának a regisztrációs házirend létrehozásához és az Apple Configuratorba való exportálásához manuálisan kell regisztrálnia minden eszközt. Az USB-csatlakozású, vállalati tulajdonú eszközök regisztrálása közvetlenül történik, az összes adat törlésére nincs szükség. Az eszközök kezelése felhasználó nélküli eszközökként történik. Nincsenek zárolva vagy felügyelve, és nem támogatják a feltételes hozzáférést, a jailbreak észlelését vagy a mobileszközök felügyeletét.

További információ az iOS-eszközök regisztrációjáról:

- [Az iOS-eszközök regisztrálási módjának kiválasztása](ios-enroll.md)
- [iOS-eszközök regisztrálása a Configurator és közvetlen regisztráció használatával](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Mobileszköz karbantartása az MDM-tanúsítvány lejárta után

Az MDM-tanúsítvány automatikusan megújul, amikor a mobileszköz kommunikál az Intune szolgáltatással. Ha a mobileszközök törölve lettek, vagy bizonyos ideig nem tudnak kommunikálni az Intune szolgáltatással, a MDM-tanúsítvány nincs megújítva. Az eszköz az MDM-tanúsítvány lejárta után 180 nappal törlődik az Azure Portalról.
