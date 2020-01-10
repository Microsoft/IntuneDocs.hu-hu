---
title: A Céges portál alkalmazás telepítése Windows rendszerhez | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 28e64b9a860ca7c3265fe17401292cc1a508da7e
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858862"
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>Mi történik a Vállalati portál alkalmazás telepítésekor és a Windows-eszköz Intune-beli regisztrálásakor?

Amikor a Céges portál alkalmazást telepíti, majd egy Windows- vagy Windows Phone-eszközt regisztrál vele, azzal lehetővé teszi, hogy a cég informatikai támogató szolgálata felügyelje az eszközt, és így biztonságban tartsa a cég vagy az intézmény adatait. Ebben a témakörben a Windows 10-nél korábbi rendszerű eszközökről esik szó. A Windows 10-eszközök esetében lásd[kapcsolódó témakör](about-cp-app-for-windows-10.md).  

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>Mi történik minden Windows-eszközzel a regisztrálás után?
Ha Windows- vagy Windows Phone-eszközét regisztrálja az Intune-ban, a következőkre nyílik lehetősége:

- Elérheti a vállalat hálózatát, a saját levelezését és a munkájához szükséges fájlokat.

- Letöltheti a vállalati alkalmazásokat a Vállalati portálról weboldaláról. (__Megjegyzés__: Windows 7 és Windows Vista esetében kizárólag a Céges portál webhelyről tölthet le vállalati alkalmazásokat.)

- Automatikusan konfigurálhatja vállalati vagy iskolai e-mail-fiókját.

- Ha elveszíti vagy ellopják a telefonját, visszaállíthatja a gyári beállításait.

Egy eszköz regisztrálásával jogosultságot ad a cég informatikai támogató szolgálatának a következő műveletek elvégzésére:

- Az eszköz visszaállítása az alapértelmezett gyári beállításokra. Az eszköz elvesztésekor vagy ellopásakor bizonyulhat hasznosnak.

- Csak a munkahelyi fájlok és munkahelyi alkalmazások eltávolítása. *A személyes adatai és beállításai nem törlődnek.*

- A cég informatikai támogató szolgálata leltárt készíthet az eszközre telepített szoftverekről, ideértve az Ön által telepített szoftvereket is.

- Követelményeket határozhat meg az eszközön, például a jelszó vagy PIN-kód használatát a vállalati adatok védelme érdekében. A cég informatikai támogatási szolgálata korlátozhatja, hogy hányszor lehet helytelen jelszót megadni, és kizárhatja a felhasználót az eszközről, ha túl sokszor próbálkozott.

- Megkövetelheti az eszközön tárolt adatok titkosítását a céges adatok védelme érdekében az eszköz elvesztése vagy ellopása esetén.

- Ehhez el kell fogadnia a használati feltételeket.

- Megakadályozhatja, hogy felvételt készíthessen a vállalattal kapcsolatos adatokról.

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>Mi történik minden Windows rendszerű számítógéppel a regisztrálás után?

- Olyan szoftverek települnek a számítógépre, amelyek lehetővé teszik a cég informatikai támogatási szolgálata számára a számítógép felügyeletét, Önnek pedig a különböző vállalati erőforrások, például alkalmazások és támogatási információk elérését. A cég informatikai támogatási szolgálata automatikusan frissítheti ezeket a szoftvereket.

- Lehetséges, hogy az Intune Endpoint Protection is települ a számítógépre. Ez egy vírusok és kártevő szoftverek elleni védelmi alkalmazás.

- A cég informatikai támogatási szolgálata adatokat gyűjthet a számítógép merevlemezéről, illetve adatokat törölhet róla.

- A cég informatikai támogatási szolgálata alkalmazásokat és frissítéseket telepíthet a számítógépre.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>Mi történik az eszköz regisztrálása után nyolcóránként?

A regisztrált eszközök megközelítőleg nyolcóránként elvégzik a következőket:

- A cég informatikai támogatási szolgálata által elérhetővé tett szabályzatok és alkalmazásfrissítések letöltése.

- A hardverleltár változásainak elküldése.

- A vállalati alkalmazások leltárában bekövetkezett változások elküldése.

Ha kérdése van, lépjen kapcsolatba a cég informatikai támogatási szolgálatával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
