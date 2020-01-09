---
title: Szerezze be a macOS-eszköz helyreállítási kulcsát a Intune Céges portál webhelyről
description: Megtekintheti egy regisztrált, felügyelt macOS-eszköz helyreállítási kulcsát.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44026c379a763db2cc43912e4ef09ae542fbe7db
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75653995"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>A macOS-eszköz helyreállítási kulcsának beolvasása

Használja a Céges portál webhelyét a zárolt macOS-eszköz helyreállítási kulcsának beszerzéséhez. Ha elfelejti az eszköz jelszavát, bejelentkezhet a Céges portál egy másik eszközről a kulcs lekéréséhez.  

## <a name="get-recovery-key-from-company-portal-website"></a>Helyreállítási kulcs beolvasása Céges portál webhelyről

Ez a beállítás a szervezet által a FileVault használatával titkosított eszközökhöz érhető el. Nem érhető el a személyes titkosítású eszközökhöz.

1. Bármely eszközön jelentkezzen be a [céges portál webhelyére](https://portal.manage.microsoft.com) , és válassza a menü gomb > **eszközök** **menüpontot** .  
2. Válassza ki a titkosított macOS-eszközt.  
3. Válassza a **helyreállítási kulcs beolvasása**elemet.  

    ![Képernyőkép a Céges portál webhelyéről, kiemelve a helyreállítási kulcs beolvasása szakaszt.](./media/1907-recovery2-cpweb-intune.PNG)  

4. Ekkor megjelenik a helyreállítási kulcs.

    ![Képernyőkép a Céges portál webhelyről, amely a helyreállítási kulcsot mutatja.](./media/1907-recovery-cpweb-intune.PNG)  

    Biztonsági okokból a kulcs öt perc múlva eltűnik. A kulcs ismételt megjelenítéséhez válassza a **helyreállítási kulcs beolvasása**elemet.

Ha a kulcs nem található, de az eszköz megfelelően titkosított, forduljon a szervezet ügyfélszolgálatához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>Helyreállítási kulcs beolvasása Céges portál iOS-alkalmazásból

A személyes helyreállítási kulcs (FileVault-kulcs) az iOS rendszerhez készült Céges portál alkalmazással kérhető le. A személyes helyreállítási kulccsal rendelkező eszközt regisztrálni kell az Intune-ban, és az Intune-on keresztül kell titkosítani a FileVault-mel. Ez a beállítás nem érhető el a személyes titkosítású eszközökhöz. 

A Céges portál alkalmazás használatával megnyithatja a Safari webes nézetét, és lekérheti a személyes helyreállítási kulcsot. 

1. Nyissa meg Céges portál.
2. Kattintson a **helyreállítási kulcs beolvasása**elemre.

    ![Képernyőkép a Céges portál iOS-alkalmazásról, amely a helyreállítási kulcsot mutatja](./media/get-recovery-key-cpweb-02.png)  

A Céges portál webhely a Safari webes nézetében nyílik meg, és megjeleníti a kulcsot. 

## <a name="it-pro-support"></a>IT Pro-támogatás

Ha informatikai támogató személy, és a macOS-eszközök FileVault-titkosítását szeretné konfigurálni és felügyelni, tekintse meg az [eszközök titkosításának használata az Intune](/intune/protect/encrypt-devices)-nal című témakört.

## <a name="next-steps"></a>További lépések

Ismerje meg, mit tehet a Céges portál webhelyén. Lásd: [a Intune céges portál webhely használata](using-the-intune-company-portal-website.md) a műveletek listájához.  

További segítségre van szüksége? Lépjen kapcsolatba az informatikai támogatási személlyel. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
