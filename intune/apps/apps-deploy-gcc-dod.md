---
title: Alkalmazások GCC magas és DoD környezetekhez
titleSuffix: Microsoft Intune
description: Ismerkedjen meg a GCC magas és DoD környezeteket érintő alkalmazásokkal Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d414899b6146afbe2c5ac119193fe0e59aa719b
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939973"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Alkalmazások üzembe helyezése az Intune-nal a GCC magas és DoD környezetekben 

A bérlői rendszergazdák a Microsoft Intune használhatják alkalmazások kiosztását a munkahelyükön. A munkaerő a vállalat alkalmazottja, az alkalmazások felhasználói. Számos különböző típusú alkalmazás telepíthető az Intune-ból a GCC magas vagy DoD környezetekben. Ha a rendszergazdának fel kell töltenie és terjesztenie kell egy olyan Windows-alkalmazást, amely egy egyéni készítésű, harmadik féltől származó gyártó által létrehozott, vagy a [Microsoft Store for Business](https://businessstore.microsoft.com/store)szolgáltatásból letöltött offline alkalmazás, akkor a rendszergazda dönthet úgy, hogy terjesszen üzletági [alkalmazásként](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Kereskedelmi környezetekben a bérlői rendszergazda szinkronizálhatja az üzletét az Intune-nal, azonban a GCC magas és a DoD környezetek esetében ez a szolgáltatás nem érhető el. Ebben a helyzetben a rendszergazdáknak közvetlenül az Intune-ba való feltöltéssel kell központilag telepíteniük az alkalmazást.  

## <a name="add-line-of-business-apps-using-intune"></a>Üzletági alkalmazások hozzáadása az Intune-nal 

Ha olyan üzletági alkalmazást szeretne hozzáadni, amely egy GCC magas vagy DoD környezethez készült, az Intune használatával követheti a [Windows LOB alkalmazás](lob-apps-windows.md) utasításait. Dönthet úgy, hogy először a vállalati Microsoft Store telepíti a Céges portál. Ha úgy dönt, hogy a Céges portál használja, akkor manuálisan telepítheti és telepítheti a Céges portál. További információ: [a Microsoft Intune céges portál alkalmazás konfigurálása](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Offline alkalmazások terjesztése a vállalati áruházból az Intune használatával  

Ha [le kell töltenie egy offline licenccel rendelkező alkalmazást](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) a vállalati Microsoft Storeból, kövesse az alábbi lépéseket az alkalmazás letöltéséhez: 

1. Jelentkezzen be a [vállalati áruházba](https://businessstore.microsoft.com/).
2. Válassza a **kezelés** > **Beállítások**lehetőséget.
3. A **vásárlási élmény**területen állítsa az **Offline alkalmazások megjelenítése a következőre** :.

Ha az alkalmazások vásárlásakor offline verzió érhető el, dönthet úgy, hogy a licenc típusát offline értékre módosítja. Az alkalmazás beszerzése után felügyelheti azt a  >  termékek **kezelése**a [vállalati áruházban](https://businessstore.microsoft.com/) **& szolgáltatások** lehetőség választásával. Emellett letöltheti az alkalmazást és annak függőségeit is. Ezt követően a letöltött alkalmazást (és annak függőségeit) is telepítheti a felhasználók számára az Intune használatával.  

## <a name="syncing-intune-to-the-store-for-business"></a>Az Intune szinkronizálása a vállalati áruházba 

Kereskedelmi (nem kormányzati) környezetben a rendszergazda szinkronizálhatja az Intune-t a vállalati Microsoft Store. Ez a kormányzati környezetekben nem érhető el. Az Intune kereskedelmi környezetekben és a kormányzati környezetek Intune-ban való különbségével kapcsolatos részletekért lásd: [Enterprise Mobility + Security az Egyesült Államok kormányzati szolgálatának leírása](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Ha az Intune-t az áruházbeli vállalati fiókhoz szeretné szinkronizálni, tekintse meg [a Microsoft Store for Business szolgáltatásban vásárolt alkalmazások kezelése a Microsoft Intune](windows-store-for-business.md)segítségével című témakört.  

## <a name="compliance"></a>Megfelelőség 

Tekintse át az alkalmazások adatvédelmi és megfelelőségi nyilatkozatait, és hasonlítsa össze azokat a szervezet megfelelőségi, biztonsági és adatvédelmi követelményeivel, amikor kiértékeli ezeknek a szolgáltatásoknak a megfelelő használatát.   

## <a name="next-steps"></a>További lépések

Az alkalmazások telepítésével és hozzárendelésével kapcsolatos további tudnivalókért lásd: [alkalmazások társítása csoportokhoz Microsoft Intune használatával](apps-deploy.md).

 
