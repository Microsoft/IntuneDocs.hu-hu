---
title: Kapcsolja össze Intune-fiókját a felügyelt Google Play-fiókkal.
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan csatlakozhat Intune-fiókjához a felügyelt Google Play-fiókkal.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 581d88e49391bc874625e9c84318c039706b0c1b
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124826"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Az Intune-fiók összekötése a felügyelt Google Play-fiókkal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Android [Enterprise munkahelyi profil](android-work-profile-enroll.md), az [Android Enterprise teljes körű](android-fully-managed-enroll.md)felügyelet és az [Android Enterprise dedikált eszközök](android-kiosk-enroll.md)támogatásához az Intune bérlői fiókját a felügyelt Google Play-fiókhoz kell kapcsolni.  

Ahhoz, hogy egyszerűbb legyen az Android Enterprise Management konfigurálása és használata, a Google Play-hez való csatlakozáskor az Intune automatikusan négy általános androidos vállalati alkalmazást fog hozzáadni az Intune felügyeleti konzolhoz. A négy androidos vállalati alkalmazás a következő:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – az Android Enterprise teljes körűen felügyelt forgatókönyvekhez használható.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – segít bejelentkezni a fiókjába, ha kétfaktoros ellenőrzést használ.
- **[Intune céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – az alkalmazás-és az Android Enterprise Work-profil forgatókönyvek esetében használatos.
- [Felügyelt kezdőképernyő](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – az Android Enterprise dedikált/kioszk forgatókönyvek esetében használható.

> [!NOTE]
> A Google- és a Microsoft-tartományok közötti interakció miatt ennél a lépésnél előfordulhat, hogy módosítania kell a böngésző beállításait.  Ügyeljen rá, hogy a „portal.azure.com” és a „play.google.com” tartomány azonos biztonsági zónában legyen található a böngészőben.

1. Ha még nem tette meg, készítse elő a mobileszköz-kezelést úgy, hogy a  [Microsoft Intune](../fundamentals/mdm-authority-set.md) -t állítja be a mobileszköz-kezelő **szolgáltatóként**.
2. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **android** > **Android-regisztráció** > **felügyelt Google Play**lehetőséget.  Ha egyéni Intune-rendszergazdai szerepkört használ, akkor ennek eléréséhez szervezeti olvasási és frissítési engedély szükséges.
   
   ![Vállalati Android regisztrációs képernyő](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Az **Elfogadom** lehetőség választásával engedélyezze a Microsoftnak a [felhasználó- és eszközadatok Google-nak való elküldését](../protect/data-intune-sends-to-google.md). 
   
4. Válassza a **Google elindítása az azonnali csatlakozáshoz** lehetőséget. Ezzel megnyitja a Felügyelt Google Play webhelyet. A webhely egy új lapon nyílik meg a böngészőben.
  
5. A Google bejelentkezési oldalán adja meg azt a Google-fiókot, amely a bérlő összes androidos vállalati felügyeleti feladatához társítva lesz. Ezt a Google-fiókot osztják meg a vállalati rendszergazdák az alkalmazások Google Play konzolon való felügyeletéhez és közzétételéhez. Meglévő Google-fiókot is használhat, illetve újat is létrehozhat. A választott fiók nem lehet G Suite-tartományhoz rendelve.
    
    > [!Note]
    > Ha a Microsoft Edge böngészőt használja, akkor a Google-fiókjába való bejelentkezéshez kattintson a jobb felső sarokban lévő **Bejelentkezés** lehetőségre.

6. Az **Organization name** (Szervezet neve) mezőben adja meg a vállalat nevét. Az **Enterprise mobility management (EMM) provider** (Nagyvállalati mobileszköz-felügyeleti (EMM-) szolgáltató) mezőben a **Microsoft Intune** értéknek kell megjelennie.

7. Fogadja el az Android-szerződést, majd válassza a **Jóváhagyás** gombot. Megtörténik a kérelem feldolgozása.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Az androidos vállalati rendszergazdai fiók leválasztása

Kikapcsolhatja az Android vállalati regisztrációját és felügyeletét. Ehhez először ki kell vonnia a regisztrált androidos vállalati eszközöket, beleértve a munkahelyi Profilos eszközöket, a dedikált eszközöket és a teljes körűen felügyelt eszközöket. Ezután az Intune felügyeleti konzolján válassza a **Leválasztás** lehetőséget az összes regisztrált Android vállalati munkahelyi profil eszköz, a dedikált eszközök és a teljes körűen felügyelt eszközök regisztrációból való eltávolításához. Ezzel eltávolítja a felügyelt Google Play-fiók és az Intune közötti kapcsolatot is.

1. Intune-rendszergazdaként jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **Android** > **Android-regisztráció** > **felügyelt Google Play** > **Leválasztás**lehetőséget.
3. Válassza az **Igen** választ az összes vállalati androidos eszköz leválasztásához és az Intune-beli regisztrációjuk megszüntetéséhez.

## <a name="next-steps"></a>További lépések

Miután kapcsolódott a felügyelt Google Play-fiókhoz, beállíthatja az [androidos vállalati munkahelyi Profilos eszközöket](android-work-profile-enroll.md), beállíthatja az androidos [vállalati dedikált eszközöket](android-kiosk-enroll.md) , és [beállíthatja az androidos nagyvállalati szintű felügyelt eszközöket](android-fully-managed-enroll.md)
