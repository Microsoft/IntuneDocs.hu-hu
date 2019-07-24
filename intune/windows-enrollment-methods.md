---
title: Intune-regisztrációs módszerek Windows-eszközökhöz
titleSuffix: Microsoft Intune
description: Ismerkedjen meg a Windows-eszközök Intune-ban való regisztrálásának különböző módjaival
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 4a0df4f32513eb37bd7396d8e6249f9c6e71a4e4
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884184"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Intune-regisztrációs módszerek Windows-eszközökhöz

Az eszközök Intune-beli kezeléséhez először regisztrálni kell az eszközöket az Intune szolgáltatásban. A személyes tulajdonban lévő és a vállalat tulajdonában lévő eszközök egyaránt regisztrálhatók az Intune-felügyeletre. 

Az Intune-ban regisztrált eszközök két módon szerezhetők be:
- A felhasználók saját maguk is regisztrálhatják Windows rendszerű számítógépeiket 
- A rendszergazdák úgy konfigurálhatják a házirendeket, hogy felhasználói beavatkozás nélkül kényszerítsék az automatikus regisztrációt

## <a name="user-self-enrollment-in-intune"></a>Felhasználói regisztráció az Intune-ban

A felhasználók a következő módszerek bármelyikével regisztrálhatják saját Windows-eszközét:

- [Saját eszköz használata (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): A felhasználók a személyes tulajdonban lévő eszközeiket a **munkahelyi és iskolai** fióknak az  eszköz beállításaiból való összekapcsolására való kiválasztásával regisztrálhatják. Ez a folyamat:
  - Regisztrálja az eszközt a Azure Active Directory, hogy hozzáférjen a vállalati erőforrásokhoz, például az e-mailekhez.
  - Regisztrálja az eszközt az Intune-ban személyes tulajdonú eszközként (BYOD).
Ha egy rendszergazda konfigurálta az automatikus regisztrációt (az Azure AD Premium-előfizetésekkel érhető el), a felhasználónak csak egyszer kell megadnia a hitelesítő adatokat. Ellenkező esetben a regisztrációhoz külön regisztrálni kell a MDM, és újra meg kell adniuk a hitelesítő adataikat.  
- A **Mdm csak** a beléptetés lehetővé teszi, hogy a felhasználók meglévő munkacsoportot, Active Directory vagy Azure Active Directory-csatlakozó számítógépet regisztráljanak az Intune-ban. A felhasználók a meglévő Windows rendszerű számítógép beállításaitól regisztrálhatnak. Ez a módszer nem ajánlott, mert nem regisztrálja az eszközt Azure Active Directoryba. Emellett megakadályozza az olyan funkciók használatát, mint a feltételes hozzáférés.
- [Azure Active Directory (Azure ad) csatlakozás](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) – összekapcsolja az eszközt a Azure Active Directory, és lehetővé teszi, hogy a felhasználók Azure ad-beli hitelesítő adataikkal jelentkezzenek be a Windowsba. Ha engedélyezve van az automatikus regisztráció, a rendszer automatikusan regisztrálja az eszközt az Intune-ban. Az automatikus regisztrálás előnye a felhasználó egylépéses folyamata. Ellenkező esetben a regisztrációhoz külön regisztrálni kell a MDM, és újra meg kell adniuk a hitelesítő adataikat. A felhasználók a kezdeti Windows OOBE vagy a beállítások alapján regisztrálhatják ezt a módot. Az eszköz vállalati tulajdonú eszközként van megjelölve az Intune-ban.
- [Autopilot](enrollment-autopilot.md) – automatizálja az Azure ad Joint, és regisztrálja az új vállalati tulajdonú eszközöket az Intune-ban. Ez a módszer leegyszerűsíti a beépített felhasználói élményt, és nem kell egyéni operációsrendszer-lemezképeket alkalmaznia az eszközökre. Ha a rendszergazdák az Intune-t használják az Autopilot-eszközök felügyeletére, akkor a regisztráció után kezelhetik a szabályzatokat, a profilokat, az alkalmazásokat és egyebeket.  A robotpilóta-telepítés négyféle típusú: [Saját üzembe helyezési mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (kioszkok, digitális aláírások vagy megosztott eszközök), [felhasználó által vezérelt mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (hagyományos felhasználók számára), [fehér kesztyű] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) lehetővé teszi a partnerek vagy az informatikai munkatársak számára a Windows 10 rendszerű számítógépek előzetes kiépítését, hogy az teljes mértékben konfigurálva legyen, és készen álljon a szolgáltatásra [Autopilot for meglévő eszközök] (https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) lehetővé teszi a Windows 10 legújabb verziójának egyszerű telepítését a meglévő eszközökre.

## <a name="administrator-based-enrollment-in-intune"></a>Rendszergazdai alapú regisztráció az Intune-ban

A rendszergazdák a következő regisztrációs módszereket állíthatják be, amelyek nem igényelnek felhasználói beavatkozást:

- A [hibrid Azure ad JOIN](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) lehetővé teszi, hogy a rendszergazdák a hibrid Azure ad-hez csatlakoztatott eszközöket automatikusan regisztrálják Active Directory csoportházirendet. 
- [Configuration Manager a közös felügyelet](https://docs.microsoft.com/sccm/comanage/overview) lehetővé teszi, hogy a rendszergazdák az Intune és a Configuration Manager kettős előnyeinek beszerzésével regisztrálják meglévő Configuration Manager felügyelt eszközeiket az Intune-ban. 
- [Eszköz](device-enrollment-manager-enroll.md) beléptetési kezelője A (DEM) egy speciális szolgáltatásfiók. A DEM-fiókok rendelkeznek olyan engedélyekkel, amelyek lehetővé teszik a jogosult felhasználók számára több vállalati tulajdonú eszköz regisztrálását és kezelését. Az ilyen típusú eszközök például POS- vagy segédprogram-alkalmazásokhoz megfelelőek, de nem alkalmasak olyan felhasználók számára, akik hozzá szeretnének férni a levelezésükhöz vagy a vállalati erőforrásokhoz. Ez a módszer nem teszi lehetővé olyan szolgáltatások használatát, mint például a feltételes hozzáférés. 
- A [tömeges regisztrálás](windows-bulk-enroll.md) lehetővé teszi, hogy egy adott felhasználó nagy számú új vállalati tulajdonú eszközt csatlakoztasson Azure Active Directory és az Intune-hoz. Létre kell hoznia egy kiépítési csomagot a Windows Configuration Designer (WCD) alkalmazással. Ezután a kezdeti Windows OOBE-élmény vagy a meglévő Windows rendszerű számítógépek USB-adathordozójának használatával telepítheti a kiépítési csomagot, hogy automatikusan regisztrálja az eszközöket az Intune-ban. Ez a metódus nem engedélyezi a feltételes hozzáférés használatát. 
- A [Windows IoT alapvető eszközeinek](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) beléptetése a Windows IoT alapirányítópultján történik az eszköz előkészítéséhez, majd a Windows Configuration Designer használatával kiépítési csomag létrehozásához. Ezután az SD-kártya adathordozójának használata a kezdeti rendszerindítás során telepíti a kiépítési csomagot, hogy automatikusan regisztrálja az eszközöket az Intune-ban.

## <a name="next-steps"></a>További lépések

[Ismerje meg a Windows beléptetési módszereinek képességeit](enrollment-method-capab.md)
