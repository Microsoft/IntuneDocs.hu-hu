---
title: Android-eszköz regisztrációjának törlése az Intune-ból | Microsoft Docs
description: Android-eszköz eltávolítása Intune Céges portál
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f2e9313cf2a4d639096f783b895596fc2535649
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163551"
---
# <a name="unenroll-your-android-device-from-management"></a>Android-eszköz regisztrációjának törlése  

Regisztrált Android-eszköz eltávolítása a szervezet által felügyelt eszközök közül. Ez a cikk azt ismerteti, hogyan távolíthatja el az eszközt a Céges portál alkalmazásból. Miután eltávolította az eszközt:  

* Az eszköz nem fogja tudni elérni a szervezet védett adatait és erőforrásait.
* Az eszköz nem fog megjelenni a Céges portálon.
* Nem telepíthet alkalmazásokat a Céges portálról.
* Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.  

> [!NOTE]
> A vállalati tulajdonban lévő eszközt nem lehet törölni vagy eltávolítani a Microsoft Intune alkalmazásból. Az eszköz regisztrálása az eszköz kezdeti beállítása során történt, és regisztrálni kell a szervezet erőforrásaihoz való hozzáféréshez.  

1. A Céges portálon koppintson a jobb felső sarokban található három függőleges pontra. Megnyílik a műveletmenü.

   ![Képernyőkép az Android Céges portál alkalmazásról, a jobb felső sarokban megnyíló művelet menüvel. A „Saját profil” és a „beállítások” lehetőség alatt harmadikként megjelenik az új „céges portál eltávolítása” lehetőség is, alatta a „használati feltételek”, a „súgó és visszajelzés” és végül a „névjegy”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Koppintson a **Céges portál eltávolítása** elemre.  

3. Megjelenik egy üzenet, amely tájékoztatja arról, mi történik, ha törli az eszköz regisztrációját. Koppintson az **OK** lehetőségre annak megerősítéséhez, hogy eltávolítja az eszközt a Céges portálról.

   ![Az új "céges portál eltávolítása" lehetőség kiválasztását követően elérhető képernyőkép a művelet menüből.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Céges portál alkalmazás által összegyűjtött adatok eltávolítása  

Az Android-eszközhöz készült Céges portál alkalmazás által az eszközön tárolt adatok törlésének módja a következő:

- Az alkalmazásadatok törléséhez koppintson az **alkalmazások** > **[*alkalmazás neve*]**  > **adattörlés elemre**.
- Törölje a következő mappát: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>A Céges portál alkalmazás eltávolítása

Céges portál egy Eszközkezelő alkalmazás. Nem távolítható el, amíg nem törli az eszköz regisztrációját a felügyelet alól. Miután ezt megtette, koppintson a Céges portál alkalmazás ikonjára, és tartsa nyomva addig, amíg az **Eltávolítás** lehetőség meg nem jelenik. Koppintson az **Eltávolítás** lehetőségre az alkalmazás eszközről való eltávolításához.  

Vagy koppintson a **beállítások** > **alkalmazások** > **céges portál** > **Eltávolítás**elemre.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Az Céges portál alkalmazás eltávolítása eszköz-rendszergazdaként

Utolsó megoldásként eltávolíthatja az alkalmazást az eszközről az eszköz rendszergazdájaként.  

Ha a vállalat tulajdonában álló eszközről van szó, a szervezetnek szüksége lehet arra, hogy a Céges portál mindig az eszközön legyen. Ha eltávolítja, akkor a védett vállalati erőforrásokhoz, például e-mailekhez, alkalmazásokhoz, Wi-Fi-hez vagy VPN-hez férhet hozzá, amíg újra nem telepíti az alkalmazást. További információ a szükséges alkalmazások telepítéséről, frissítéséről és eltávolításáról: [Alkalmazások hozzáadása Microsoft Intunehoz](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune).

A következőképpen tilthatja le a Céges portál eszközt rendszergazdaként. Az egyes beállítások tényleges nevei eltérőek lehetnek az Android-eszközön.  

**1. lehetőség**:  

1. Válassza a **beállítások** > **biztonsági** > **további biztonsági beállítások** > **eszköz-rendszergazdák**elemet.  
2. Törölje a **céges portál** kijelölését.  

**2. lehetőség**:

1. Válassza a **beállítások** > **zárolási képernyő és biztonság** > **egyéb biztonsági beállítások** > **eszköz rendszergazdai alkalmazások**elemet.
2. Törölje a **céges portál** kijelölését.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
