---
# required metadata

title: Mobileszköz-kezelés az Exchange ActiveSync és a Microsoft Intune használatával | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Mobileszköz-kezelés az Exchange ActiveSync és a Microsoft Intune használatával
Ahhoz, hogy a Microsoft Intune közvetlenül tudja felügyelni a mobileszközöket, a felhasználóknak regisztrálniuk kell az eszközöket az Intune-ban. A felhasználók által nem beléptetett mobileszközökhöz az Exchange-összekötő segítségével engedélyezheti az Exchange ActiveSync-felügyeletet. Az eszközök helyszíni Exchange-kiszolgálókon, illetve Microsoft Office 365-ben, a felhőben üzemeltetett Exchange esetén is felügyelhetők.

## Mobileszközökre vonatkozó Exchange-hozzáférési szabályok ##

Az Exchange használatához olyan szabálykészletre van szükség, amely meghatározza, hogy mi történik akkor, amikor a mobileszközök csatlakozni próbálnak az Exchange ActiveSynchez. Ezeket a szabályokat az Intune felügyeleti konzol kezeli.

[Mobileszközökre vonatkozó Exchange-hozzáférési szabályok](exchange-access-rules-for-mobile-devices.md)

## Az Exchange Connector telepítése
Az Exchange Connector lehetővé teszi az Exchange-telepítésnek az Intune-konzolon történő kezelését. Először telepítenie és konfigurálnia kell a megfelelő Intune-Exchange összekötőt. Válassza ki a megfelelő lehetőséget annak alapján, hogy helyszíni vagy felhőalapú szolgáltatásként üzemeltetett Exchange-kiszolgálót használ:

-   [Az Intune-összekötő telepítése helyszíni Exchange-hez](intune-on-premises-exchange-connector.md)
-   [Szolgáltatások közötti Intune-összekötő konfigurálása szolgáltatott Exchange-hez](intune-service-to-service-exchange-connector.md)

## Exchange-felügyelet alatt álló mobileszközök szabályzatának alkalmazása
A szabályzatbeállítások az Intune konzolon alkalmazhatók, lásd: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Az Exchange ActiveSync-szabályzat beállításainak és az egyes mobileszközök által támogatott funkciók listáját [az Exchange ActiveSync-ügyfelek összehasonlító táblázatában](http://go.microsoft.com/fwlink/?LinkId=247270) találja..

> [!NOTE]
> Az Intune Microsoft Exchange-környezethez való csatlakozását követően minden Intune-nal felügyelt felhasználó EAS-házirendje visszaáll a Microsoft Exchange-kiszolgáló aktuális alapértelmezett házirendjére, kivéve, ha az Intune-ban specifikusabb házirend lett meghatározva.

## Vállalati adatok törlése mobileszközökről
Végül [az EAS által felügyelt mobileszközökön tárolt vállalati adatokat törölheti](wipe-for-exchange-managed-mobile-devices.md), ha már nincsenek használatban, illetve ha elvesztették vagy ellopták az eszközt.


<!--HONumber=May16_HO1-->


