---
title: Használatieset-forgatókönyvek követelményeinek meghatározása
titleSuffix: Microsoft Intune
description: Ez a cikk segít az Intune használatieset- valamint alhasználatieset-követelményeinek meghatározásában a Microsoft Intune csak felhőalapú megvalósítása esetében.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a03a92f715496b3c647a12bb99457d151ead54a3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514931"
---
# <a name="determine-use-case-scenario-requirements"></a>Használatieset-forgatókönyvek követelményeinek meghatározása

Ebben a szakaszban meghatározza az összes használati eset minden egyes munkahelyi csoportjára vonatkozó követelményeket. Ez a folyamat segít abban, hogy jobban felkészülhessen az Intune telepítésével kapcsolatos más területeken, például az architektúra és tervezés, az előkészítés és bevezetés terén. Mindemellett az Intune üzembe helyezési projektjével kapcsolatos lehetséges hiányosságokat és kihívásokat is segít azonosítani.

Előfordulhat, hogy egyes használati esetekre és alárendelt használati esetekre vonatkozóan más követelmények, társított munkahelyi csoportok és mobileszköz-platformok léteznek. A céges használati esetre vonatkozó követelmények megkövetelhetik például az eszközök korlátozóbb eszközbeállításokkal, például 6 karakterből álló PIN-kód vagy letiltott felhőalapú biztonsági mentés, történő regisztrálását az Intune-ban. A „saját eszközök használata ” (BYOD) használati eset lehet, hogy kevésbé korlátozó, és lehetővé teszi a 4 karakterből álló PIN-kód és felhőalapú biztonsági mentés használatát.

Az is elképzelhető, hogy a céges használatieset-forgatókönyvekhez olyan munkahelyi csoportokkal rendelkezik, amelyekre eltérő követelmények vonatkoznak (például a PIN-kód beállításait, Wi-Fi vagy VPN-profilt, az alkalmazásokat illetően). Az is elképzelhető, hogy a követelményeket a mobileszköz-platform képességei határozzák meg (például ujjlenyomat-olvasó, e-mail-profil).

Itt található néhány példa a munkahelyi használatieset-forgatókönyvek követelményeire, amelyekben az egyes használatieset- és alhasználatieset-forgatókönyvekre, munkahelyi csoportra és mobileszköz-platformra különböző követelmények vonatkoznak. A következő táblázatot is felhasználhatja munkahelye használatieset-követelményeinek megadásához:

| **Használati esetek** | **Használati alesetek** | **Csoportok** | **Eszközplatformok** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Vállalati | Infomunkás | HR, Pénzügy | iOS/iPadOS | Biztonságos e-mail, eszközbeállítások, profilok, alkalmazások |                                                          
| Vállalati | Vezetők | HR, Pénzügy | iOS/iPadOS | Biztonságos e-mail, eszközbeállítások, profilok, alkalmazások |                                                         
| Vállalati | Kioszkmód | Kereskedelem | Android: | Eszközbeállítások, profilok, alkalmazások |
| BYOD | Infomunkás | Marketing, értékesítés | iOS/iPadOS | Biztonságos e-mail, eszközbeállítások, profilok, alkalmazások |                                                         
| BYOD | Vezetők | Marketing, értékesítés | iOS/iPadOS | Biztonságos e-mail, eszközbeállítások, profilok, alkalmazások |

[Letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), hogy beírja a cég használatieset- és alhasználatieset-követelményeit.


## <a name="examples-of-requirements"></a>Példák a követelményekre

Íme néhány további példa, amelyek használhatók a „Követelmények” oszlopban:

- **Biztonságos e-mail**
  - Feltételes hozzáférés az Exchange Online-hoz/helyszíni
  - Az Outlook alkalmazás adatvédelmi szabályzatai

- **Eszközbeállítások**
  - PIN-kód beállítása 4 vagy 6 karakterrel
  - Felhőbeli biztonsági mentés korlátozása

- **Profilok**
  - Wi-Fi
  - VPN
  - E-mail (Windows 10 mobil verzió)

- **Alkalmazások**
  - Az Office 365 és az alkalmazás adatvédelmi szabályzatai
  - Üzletági (LOB) alkalmazásvédelmi szabályzatok

## <a name="next-steps"></a>További lépések

A következő szakaszban az [Intune bevezetési tervének összeállításáról](planning-guide-rollout-plan.md) található információ.
