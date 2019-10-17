---
title: macOS-eszköz Céges portálon való regisztrálása az Intune-ban | Microsoft Docs
description: A cikk azt mutatja be, hogyan regisztrálhatók macOS-eszközök az Intune-ban a Céges portál alkalmazással
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee725d118353e18924858569ac861992d19f839a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506188"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>A macOS-eszköz Céges portál alkalmazással való regisztrálása az Intune-ban

Regisztrálja macOS-eszközét az Intune Céges portál alkalmazással, hogy biztonságos hozzáférést kapjon vállalata levelezéséhez, fájljaihoz és alkalmazásaihoz.

A vállalatok gyakran megkövetelik az eszközök felügyelet alá vonását, mielőtt engedélyeznék azok hozzáférését a védett adatokhoz. A már felügyelt eszközökre a vállalat szabályzatokat és alkalmazásokat küldhet le a mobileszköz-felügyeleti szolgáltatón keresztül. Ahhoz, hogy eszközéről folyamatosan hozzáférjen a munkahelyi vagy iskolai információkhoz, eszközét a szabályzatbeállításoknak megfelelően kell konfigurálnia.  

Ez a cikk azt írja le, hogyan segít a macOS-hez készült Intune Céges portál alkalmazás az eszközök vállalati követelményeknek megfelelő regisztrálásában, konfigurálásában és karbantartásában.  
</br>
> [!VIDEO https://www.youtube.com/embed/Pa2pfhwq_yk?rel=0]

## <a name="what-to-expect-from-the-company-portal-app"></a>Ami a Céges portál alkalmazástól elvárható

Első beállítása során az alkalmazás megköveteli, hogy hitelesítse magát vállalatánál. Ez után tájékoztatja az összes szükséges eszközbeállításról. A vállalatok gyakran megadják például a jelszavak minimális vagy maximális karakterszámát, és ezt Önnek be kell tartania.    

Eszköze regisztrálása után a Céges portál alkalmazás folyamatosan gondoskodik az eszköz védelméről. Ha például nem megbízható forrásból telepít valamit, az alkalmazás riasztást küld Önnek, és olykor meg is vonja a vállalati adatokhoz való hozzáférést. A vállalatok gyakran használnak ilyen alkalmazásvédelmi szabályzatokat, amelyek többnyire megkövetelik a nem megbízható alkalmazások eltávolítását a hozzáférés visszaadása előtt.

Ha a regisztráció után a vállalat új biztonsági követelményt, például többtényezős hitelesítést vezet be, a Céges portál alkalmazás értesíti Önt. Lehetősége lesz módosítani beállításait, hogy továbbra is dolgozhasson az eszközéről.  

További információk a regisztrációval kapcsolatban: [Mi történik a Céges portál alkalmazás telepítésekor és az eszköz regisztrálásakor?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Eszköz felügyelet alá vonása  
A macOS 10,12-es vagy újabb verzióját futtató macOS-eszközök regisztrálásához kövesse az alábbi lépéseket.   


1. A Céges portál webhelyének eléréséhez nyisson új ablakot a __Safariban__, és lépjen a https://portal.manage.microsoft.com URL-címre.  

2. Jelentkezzen be a Céges portál webhelyére munkahelyi vagy iskolai fiókjával.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Kattintson az oldal bal felső sarkában lévő **Menü** > **Eszközök** lehetőségre.  

4. Az __Eszközök__ oldalon vagy a felügyelt eszközök listája, vagy egy szalagcím látható. Hogy mi jelenik meg, az attól függ, hogy rendelkezik-e már felügyelt eszközzel. 
    * A felsoroltak között nem szereplő eszköz hozzáadásához válassza az **Ide koppintva tudathatja velünk, melyik eszközt használja, vagy új eszközt adhat meg.** feliratú szalagcímet.
    * Ha nem rendelkezik eszközekkel, a szalagcím beolvasása: **nem rendelkezik felügyelt eszközökkel. Ezt a gombra koppintva veheti fel.** Az eszköz hozzáadásához kattintson a szalagcímre.  

     ![Képernyőkép az Eszközök oldalról, a kattintás helyét kiemelő piros téglalappal bekeretezett szalagcímmel.](./media/CP-enroll-MACOS-1808.png)  
5. Hajtsa végre az alábbi lépések közül a Céges portálon éppen megjelenő üzenetnek megfelelőt.  
    * Ha először ad hozzá egy eszközt, akkor a rendszer felkéri, hogy töltse le a Céges portál alkalmazást az eszközére. A folytatásához kattintson a **Letöltés** lehetőségre.  

         ![Példa képernyőkép a macOS-es Céges portál alkalmazás letöltését kérő képernyőről. A felhasználó választhat, hogy a bal alsó, kék Letöltés gombra, vagy a jobb alsó, szürke Mégse gombra kattint a párbeszédablakban.](./media/CP-enroll-download-macOS-1808.png)  

    * Ha már rendelkezik felügyelt macOS-eszközzel, akkor a jelenleg felügyelt macOS-eszközei listája jelenik meg egy párbeszédablakban. **Az eszközöm nincs a listán** > **Letöltés** lehetőség választásával töltse le a Céges portál alkalmazást az éppen hozzáadott eszközre.  

         ![Példa képernyőkép a macOS-es Céges portál alkalmazás letöltését kérő képernyőről. A felhasználó választhatja *Az eszközöm nincs a listán* lehetőséget, vagy egy eszközt az oldal közepéről. A párbeszédablak bal alsó sarkában megjelenik egy kék Letöltés gomb, a jobb alsó sarokban pedig egy szürke Mégse gomb](./media/cp-mac-os-device-isnt-here-1808.png)  

6. Eszköze ellenőrzi, hogy a **CompanyPortal.pkg** telepítőfájl megnyitása biztonságos-e. Miután ez befejeződött, nyissa meg a telepítőt, és végezze el a telepítést.  

7. Amikor a telepítés véget ér, lépjen a **Kezdőpanelre**, majd nyissa meg a **Céges portált**.  

8. MacOS-eszköze párbeszédablakban kér megerősítést a Céges portál alkalmazás megnyitásához. Kattintson a **Megnyitás** gombra.  

   > [!TIP]
   > Az Intune-nak hozzá kell férnie a számítógépéhez, enélkül nem tud meggyőződni arról, hogy elég biztonságos-e az eszköz a vállalat erőforrásainak eléréséhez. Ha a számítógép elutasítja a Céges portál alkalmazás megnyitását, [kapcsolja ki a forgalomirányítót](https://support.apple.com/HT202491). Ez után nyissa meg az alkalmazást.

9. A Céges portál alkalmazás első megjelenő képernyője felszólítja, hogy **jelentkezzen be**. Használja ugyanazt a munkahelyi vagy iskolai fiókot, amellyel a Céges portál webhelyre jelentkezett be.

10. A Céges portál megerősíti a fiókadatokat, majd megjeleníti az **Eszközregisztráció** és az **Eszközmegfelelőség** állapotát. Sárga háromszögek hívják fel a figyelmet a macOS-eszköz iskolai vagy munkahelyi használatának biztonságossá tételéhez szükséges lépéseket. A regisztráció megkezdéséhez kattintson az **Indítás** lehetőségre. 

11. Ha a rendszer kéri, írja be a számítógép bejelentkezési adatait.  

Az eszköz felügyeleti regisztrálása eltarthat néhány percig. Ezalatt végezhet egyéb műveleteket az eszközén. A vállalati hozzáférés beállításának befejezése után megjelenő üzenet a folyamat lezárásáról tájékoztatja.  

## <a name="unverified-profiles"></a>Ellenőrizetlen profilok
A macOS-eszköz telepített mobileszköz-kezelési (MDM-) profiljainak megtekintésekor előfordulhat, hogy egyes profilok **Ellenőrizetlen** állapotot jeleznek. Amíg a **Felügyeleti profil** **Ellenőrzött** állapotot jelez, nincs ok az aggodalomra.  

A felügyeleti profil határozza meg az MDM-csatorna kapcsolatát. Amíg a felügyeleti profil ellenőrizve van, a többi, ezen a csatornán keresztül a gépre érkező profil a felügyeleti profil biztonság tulajdonságait örökli.

Mivel ezeket a profilokat nem kell egyenként ellenőrizni, gyorsabban létrejönnek és eljutnak az eszközökre. 

## <a name="updating-the-company-portal-app"></a>A Céges portál alkalmazás frissítése

A Céges portál alkalmazás frissítése bármely más Office-alkalmazáséhoz hasonlóan a Microsoft AutoUpdate for Mac használatával történik. További tudnivalók a [macOS rendszerhez készült Microsoft-alkalmazások frissítéséről](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>További lépések  
További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához. A kapcsolatfelvételi adatait megtalálja a [Munkahelyi portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  


