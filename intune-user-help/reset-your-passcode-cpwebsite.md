---
title: Új PIN-kód kérése a Céges portál webhelyén | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 690fb81350c0c264677c6c75b8942e9cdcd4e8f0
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163363"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Az eszköz jelszavának alaphelyzetbe állítása a Vállalati portál webhelyén

Ha elveszíti egy eszköz PIN-kódját vagy jelszavát, a [Céges portál webhelyen](https://portal.manage.microsoft.com) kérhet újat. 

Előfordulhat, hogy a PIN-kód alaphelyzetbe állítása beállítás nem jelenik meg a vállalat által regisztrált eszköz esetében. Ebben az esetben kérje meg a cég informatikai támogatási szolgálatát, hogy állítsa alaphelyzetbe.  

A PIN-kód alaphelyzetbe állítása nem érhető el az Android 7,0 és újabb rendszerű eszközökön. Ha elfelejti a PIN-kódját az egyik eszközön, vissza kell állítania a gyári beállításokra.  

## <a name="reset-your-passcode"></a>A jelszó alaphelyzetbe állítása

1. Nyissa meg a [Céges portál webhelyét](https://portal.manage.microsoft.com), és válassza a __Menü__ gomb >__Eszközök__ lehetőséget.  

2. Válassza ki azt az eszközt, amelynek a jelszavát alaphelyzetbe kell állítani.  

    ![Az eszközök lap képernyőképe, amelyen két csempe azonosítatlan, általános névvel ellátott eszközök láthatók. A szürke szalagcím közvetlenül az eszközök alatt található, és felszólítja a felhasználót, hogy azonosítsa az Ön által használt eszközt, vagy újat adjon hozzá.](./media/rename-reset-device-step2-1808.png) 

3. Válassza a **Jelszó alaphelyzetbe állítása** lehetőséget. Ha a jelszó lehetőség nem jelenik meg az oldal tetején, válassza az **Egyéb (…)**  > **Jelszó alaphelyzetbe állítása** lehetőséget.   

   ![A kiválasztott eszköz adatai a Céges portál webhelyén, felül az Átnevezés, az Eltávolítás, az Eszköz alaphelyzetbe állítása, a Jelszó alaphelyzetbe állítása és a Távoli zárolás lehetőségekre mutató hivatkozásokkal. ](./media/rename-reset-device-1808.png)   

    ![Képernyőkép a további ikonról, amely piros nyíllal van kiemelve.](./media/rename-reset-device-step3-more-1808.png)  

4. Ha a program arra kéri, kattintson a **Kijelentkezés** gombra. Újabb kérés esetén jelentkezzen be ismét. Jelentkezzen be ismét a Céges portál webhelyre öt percen belül, vagy Céges portál nem állítja vissza az eszköz PIN-kódját.  

   > [!NOTE]
   > A személyazonossága megerősítéséhez újra be kell jelentkeznie. Ennek a beállításnak az a célja, hogy megakadályozza a jelszó alaphelyzetbe állítására vonatkozó rosszindulatú kísérleteket.

   ![A képernyőképeken a Céges portál kijelentkezésre való felszólítása látható. A felhasználó a Kijelentkezés és a Mégse gombokat használhatja.](./media/iwp-reset-passcode-popup-1808.png)

5. Ekkor egy üzenet jelenik meg, hogy az eszköz meglévő jelszava el lesz távolítva. A jóváhagyáshoz kattintson a **Jelszó alaphelyzetbe állítása** lehetőségre.  
    > [!WARNING]
    > A jelszó alaphelyzetbe állítása után bárki, akinek fizikai hozzáférése van az eszközhöz, hozzáférhet az eszközön tárolt legtöbb személyes és céges adathoz. Ha az eszköz jelenleg nincs az ön birtokában, ne állítsa alaphelyzetbe a jelszót.  

   ![A képernyőképen a jelszó alaphelyzetbe állítására vonatkozó második üzenet látható. Tartalmaz egy hivatkozást, amely a dokumentációban az új jelszó beállítására vonatkozó részre mutat, és egyéni gombokat, amelyekkel alaphelyzetbe állíthatja a jelszót, és megszakíthatja a műveletet.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Ha iOS-eszközön állítja alaphelyzetbe a jelszót, a meglévő jelszó el lesz távolítva. Windows-vagy Android-eszközök esetén ideiglenes PIN-kódot kell kiadni az eszköz zárolásának feloldásához és egy új PIN-kód beállításához. 

   > [!NOTE]
   > A Windows és Android rendszerű eszközökhöz tartozó ideiglenes jelszó a Céges portálon, az eszközadatokat tartalmazó lapon található. Az egyes operációs rendszerek jelszóbeállításaihoz tekintse meg az [Új jelszó beállítása](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) szakaszt.  
   
7. Nyissa meg a **Beállítások** oldalt az eszközén, és módosítsa az ideiglenes jelszót. 

8. Ekkor egy zászló jelenik meg a Céges portál webhelyének jobb felső részén. Kattintson az üzenetre, és erősítse meg, hogy a jelszó alaphelyzetbe állítása sikerült.  

## <a name="set-up-a-new-passcode"></a>Új jelszó beállítása  

Ez a szakasz a jelszó alaphelyzetbe állítását és az ideiglenes jelszó viselkedését ismerteti az egyes eszközplatformokon.  

**Android**: Eltávolítja a meglévő jelszót, és egy betűkből és számokból álló ideiglenes jelszót hoz létre.

**iOS**: Eltávolítja a meglévő jelszót, és nem hoz létre ideiglenes jelszót. Ha a Touch ID-t használja az eszköz megnyitásához vagy a vásárláshoz, azt újra be kell állítania.  

**Windows 10 Mobile**: Eltávolítja a meglévő jelszót, és egy betűkből és számokból álló ideiglenes jelszót hoz létre. A beállítás után a Windows Hello arcfelismerő rendszer továbbra is működni fog az eszközön.

**Windows Phone 8.1**: Eltávolítja a meglévő jelszót, és egy számokból álló ideiglenes jelszót hoz létre.  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
