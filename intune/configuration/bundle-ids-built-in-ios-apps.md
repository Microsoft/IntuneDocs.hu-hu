---
title: iOS/iPadOS Bundle-azonosítók a Microsoft Intune-Azure beépített alkalmazásaihoz | Microsoft Docs
titleSuffix: ''
description: Tekintse meg a beépített iOS-és iPadOS-alkalmazások köteg-azonosítóinak listáját. Ezekkel a köteg-azonosítókkal explicit módon engedélyezheti az alkalmazások számára az eszközök konfigurációs profiljaiban és házirendjeiben Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10c6ea8e3afd7bb1f5a583c0088c72fc155cb0f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513299"
---
# <a name="bundle-ids-for-built-in-ios-and-ipados-apps-you-can-use-in-intune"></a>Az Intune-ban használható beépített iOS-és iPadOS-alkalmazások köteg-azonosítói

Ha iOS/iPadOS eszközökön konfigurálja a szolgáltatásokat, a beépített alkalmazásokat is hozzáadhatja az iOS/iPadOS eszközökhöz. Ez a cikk néhány gyakori beépített iOS/iPadOS-alkalmazás köteg-azonosítóit sorolja fel. Ha más alkalmazás csomagazonosítóját szeretné megismerni, lépjen kapcsolatba a szoftver gyártójával. Tekintse meg az Apple [iOS/iPadOS Bundle-azonosítóinak](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web) listáját (az Apple webhelyének megnyitása).

## <a name="bundle-ids"></a>Köteg-azonosítók

| Csomagazonosító                   | Alkalmazásnév     | Publisher |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Alkalmazásáruház    | Apple     |
| com.apple.calculator        | Számológép   | Apple     |
| com.apple.mobilecal         | Naptár     | Apple     |
| com.apple.camera            | Fényképezőgép       | Apple     |
| com.apple.mobiletimer       | Óra        | Apple     |
| com. Apple. clips             | Klipek        | Apple     |
| com.apple.compass           | Iránytű      | Apple     |
| com.apple.MobileAddressBook | Névjegyek     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Fájlok        | Apple     |
| com.apple.mobileme.fmf1     | Barátok keresése | Apple     |
| com.apple.mobileme.fmip1    | iPhone keresése  | Apple     |
| com.apple.gamecenter        | Game Center  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Állapot       | Apple     |
| com.apple.Home              | Otthoni         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes-kapcsolat | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Térképek         | Apple     |
| com. Apple. mérték           | Kategória      | Apple     |
| com.apple.MobileSMS         | Üzenetek     | Apple     |
| com.apple.Music             | Zene        | Apple     |
| com.apple.news              | Hírek         | Apple     |
| com.apple.mobilenotes       | Megjegyzések        | Apple     |
| com.apple.Numbers           | Számok      | Apple     |
| com.apple.Pages             | Pages        | Apple     |
| com.apple.mobilephone       | Telefon        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotók       | Apple     |
| com.apple.podcasts          | Podcastok     | Apple     |
| com.apple.reminders         | Emlékeztetők    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Beállítások     | Apple     |
| com. Apple. Shortcuts         | Billentyűparancsok    | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Részvények       | Apple     |
| com.apple.tips              | Tippek         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | Videók       | Apple     |
| com.apple.VoiceMemos        | Hangjegyzetek   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Időjárás      | Apple     |

## <a name="next-steps"></a>További lépések

Ezekkel a köteg-azonosítókkal konfigurálhatja az [eszköz funkcióit](ios-device-features-settings.md) , és [engedélyezheti vagy korlátozhatja](device-restrictions-ios.md) az iOS/iPadOS eszközök egyes beállításait.
