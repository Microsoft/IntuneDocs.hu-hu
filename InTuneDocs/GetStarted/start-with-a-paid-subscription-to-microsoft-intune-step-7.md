---
title: "A vállalati portál testreszabása | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 45f574a975c94338c4543c0cdbc3aef549030601


---


# A vállalati portál testreszabása
A felhasználók a vállalati portálon ([!INCLUDE[wit_iwportal_1](../includes/wit_iwportal_1_md.md)]) elérhetik a vállalati adatokat, és olyan gyakori feladatokat hajthatnak végre, mint például az eszközök regisztrálása, az alkalmazások telepítése és az informatikai támogatási információk megtekintése.

> [!TIP]
> A vállalati portál testreszabása a vállalati portál webhelyére és a vállalati portál alkalmazásaira egyaránt hatással van.

A vállalati portál testreszabásával ismerős és könnyen használható környezetet teremthet felhasználóinak. Ehhez jelentkezzen be a [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) bérlői vagy szolgáltatás-rendszergazdaként, válassza a **Felügyelet** &gt; **Vállalati portál** lehetőséget, és konfigurálja a Vállalati portál beállításait.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## Vállalat kapcsolattartási adatai és adatvédelmi nyilatkozata
A vállalat neve a Vállalati portál címeként jelenik meg. A kapcsolattartási adatokat és részleteket a felhasználók a Vállalati portál IT-csoport elérhetősége képernyőjén tekinthetik meg. Az adatvédelmi nyilatkozat az Adatvédelem hivatkozásra kattintva jeleníthető meg.

|Mező neve|Maximális hossz|További információ|
    |----------|------------------------|----------------|
    |A cég neve|40|Ez a név a Vállalati portál címeként jelenik meg.|
    |IT-részleg kapcsolattartójának a neve|40|Ez a név az **IT-csoport elérhetősége** lapon jelenik meg.|
    |IT-részleg telefonszáma|20|Ez a telefonszám az **IT-csoport elérhetősége** lapon jelenik meg.|
    |IT-részleg e-mail címe|40|Ez a cím az **IT-csoport elérhetősége** lapon jelenik meg. Meg kell adnia egy érvényes e-mail-címet az **alias@tartománynév.com** formátumban.|
    |További információ|120|Az **IT-csoport elérhetősége** lapon jelenik meg.|
    |Vállalat adatvédelmi nyilatkozatának URL-címe:|79|Itt adhatja meg vállalatának adatvédelmi nyilatkozatát, amely akkor jelenik meg, ha a felhasználó a Vállalati portál adatvédelmi hivatkozásaira kattint. Érvényes URL-címet kell megadnia, a következő formátumban: https://www.contoso.com.|

## Támogatási kapcsolattartók
A támogatási webhely a Vállalati portálon jelenik meg, és lehetővé teszi a felhasználók számára az online támogatás elérését.

|Mező neve|Maximális hossz|További információ|
    |----------|------------------------|----------------|
    |Támogatási webhely URL-címe|150|Ha rendelkezik saját felhasználóinak szánt támogatási webhellyel, ide írja be az URL-címét. Az URL-címet a https://www.contoso.com formátumban kell megadni. Ha nem ad meg URL-címet, semmi sem jelenik meg a támogatási webhelyről a Vállalati portál **IT-csoport elérhetősége** lapján.|
    |Webhely neve|40|Ez a név a támogatási webhely URL-címének rövid neveként jelenik meg. Ha a támogatási webhelyhez csak URL-címet ad meg, de egyszerű nevet nem, akkor **Az IT-csoport weboldalának megnyitása** felirat jelenik meg a Vállalati portál **IT-csoport elérhetősége** lapján.|

## Vállalati arculat szerinti testreszabás
A Vállalati portál testre szabható a vállalat emblémájának és nevének, valamint a téma színének és a háttérnek a megadásával.

|Mező neve|További információ|
    |----------|----------------|
    |Téma színe|A Vállalati portálra alkalmazni kívánt témaszín kiválasztása.|
    |Cég emblémájának megjelenítése|Ha engedélyezi ezt a beállítást, feltöltheti a Vállalati portálon megjeleníteni kívánt vállalati emblémát. Két emblémát tölthet fel: az egyik akkor jelenik meg, ha a Vállalati portál háttérszíne fehér, a másik pedig akkor, ha a Vállalati portál a témának megfelelő háttérszínnel jelenik meg. Mindkét emblémának egy .png vagy .jpg formátumú fájlnak kell lennie, melyek felbontása legfeljebb 400 x 100 képpont, mérete pedig legfeljebb 750 KB lehet.|
    |Háttér választása a [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] Vállalati portál alkalmazás számára|Ez a beállítás csak a [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] Vállalati portál alkalmazás hátterére van hatással.|


A módosítások mentése után a felügyeleti konzol **Vállalati portál** lapjának alján található hivatkozásokra kattintva megtekintheti a Vállalati portál webhelyét. Ezek a hivatkozások nem módosíthatók. A felhasználók bejelentkezésekor ezek a hivatkozások a Vállalati portálon megjelenítik az Ön előfizetéseit.

### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések* útmutató 7. lépését.
>[!div class="step-by-step"]

>[&larr; **Házirendek és alkalmazások létrehozása**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Eszközök regisztrálása** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Jun16_HO4-->


