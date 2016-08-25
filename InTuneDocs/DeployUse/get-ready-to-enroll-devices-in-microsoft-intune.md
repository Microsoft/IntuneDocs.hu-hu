---
title: "Felkészülés az eszközök regisztrálására | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 71077d9f86a53cc66536928e4799fa4b1a51cdf0
ms.openlocfilehash: 86d3b7894eca70454fa82393c4d06eab5a99246f


---

# Felkészülés az eszközök regisztrálására a Microsoft Intune-ban
Ha szeretné lehetővé tenni, hogy alkalmazottai regisztrálhassák mobileszközeiket (például [Android](set-up-android-management-with-microsoft-intune.md), [iOS és Mac](set-up-ios-and-mac-management-with-microsoft-intune.md) rendszerű eszközeiket, [Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md) rendszerű eszközeiket és [Windows rendszerű számítógépeiket](set-up-windows-device-management-with-microsoft-intune.md)), engedélyeznie kell az eszközregisztrációt. A regisztráció engedélyezéséhez először be kell állítania egy mobileszköz-kezelő szolgáltatót, konfigurálnia kell az Intune Vállalati portált, ki kell osztania licenceket, és engedélyeznie kell a regisztrációt az adott eszközplatform számára.

## A mobileszköz-kezelő szolgáltató beállítása
A mobileszköz-felügyeleti szolgáltató határozza meg azt a felügyeleti szolgáltatást, amely az eszközök kezelésére jogosult. MDM-szolgáltató lehet például az Intune önmagában, illetve az Intune-nal bővített Configuration Manager. Ha a Configuration Manager van beállítva felügyeleti szolgáltatóként, nem használhat más szolgáltatást a mobileszközök felügyeletére.

>[!IMPORTANT]
> Alaposan fontolja meg, hogy a mobileszközöket csak az Intune használatával (online szolgáltatás), vagy a System Center Configuration Managerbe integrált Intune-nal szeretné-e kezelni (helyszíni szoftveres megoldás online szolgáltatással együtt). A mobileszköz-kezelő szolgáltató beállítása után a szolgáltató nem módosítható.



1.  A [Microsoft Intune felügyeleti konzoljában](http://manage.microsoft.com) válassza a **Felügyelet** &gt; **Mobileszköz-kezelés** lehetőséget.

2.  A **Feladatok** listában kattintson a **Mobileszköz-kezelő szolgáltatás beállítása**elemre. Megnyílik az **MDM szolgáltatás beállítása** párbeszédpanel.

    ![Az MDM-szolgáltató megadása párbeszédpanel](../media/intune-mdm-authority.png)

3.  Az Intune annak megerősítését kéri, hogy be szeretné állítani MDM-szolgáltatóként. Ha az Intune-t szeretné használni a mobileszközök kezeléséhez, jelölje be a jelölőnégyzetet, majd kattintson az **Igen** lehetőségre.

## Az Intune Vállalati portál konfigurálása

A felhasználók az Intune Vállalati portálon érhetik el a vállalati adatokat, és olyan gyakori feladatokat hajthatnak végre, mint például az eszközök regisztrálása, az alkalmazások telepítése és az informatikai támogatási információk megtekintése.

> [!TIP]
> A vállalati portál testreszabása a vállalati portál webhelyére és a vállalati portál alkalmazásaira egyaránt hatással van.

A vállalati portál testreszabásával ismerős és könnyen használható környezetet teremthet felhasználóinak. Ehhez jelentkezzen be a [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) bérlői vagy szolgáltatás-rendszergazdaként, válassza a **Felügyelet** &gt; **Vállalati portál** lehetőséget, és konfigurálja a Vállalati portál beállításait.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

#### Vállalat kapcsolattartási adatai és adatvédelmi nyilatkozata

A vállalat neve a Vállalati portál címeként jelenik meg. A kapcsolattartási adatokat és részleteket a felhasználók a Vállalati portál IT-csoport elérhetősége képernyőjén tekinthetik meg. Az adatvédelmi nyilatkozat az Adatvédelem hivatkozásra kattintva jeleníthető meg.

|Mező neve|Maximális hossz|További információ|
    |----------|------------------------|----------------|
    |A cég neve|40|Ez a név a Vállalati portál címeként jelenik meg.|
    |IT-részleg kapcsolattartójának a neve|40|Ez a név az **IT-csoport elérhetősége** lapon jelenik meg.|
    |IT-részleg telefonszáma|20|Ez a telefonszám az **IT-csoport elérhetősége** lapon jelenik meg.|
    |IT-részleg e-mail címe|40|Ez a cím az **IT-csoport elérhetősége** lapon jelenik meg. Meg kell adnia egy érvényes e-mail-címet az **alias@tartománynév.com** formátumban.|
    |További információ|120|Az **IT-csoport elérhetősége** lapon jelenik meg.|
    |Vállalat adatvédelmi nyilatkozatának URL-címe:|79|Itt adhatja meg vállalatának adatvédelmi nyilatkozatát, amely akkor jelenik meg, ha a felhasználó a Vállalati portál adatvédelmi hivatkozásaira kattint. Érvényes URL-címet kell megadnia, a következő formátumban: https://www.contoso.com.|

#### Támogatási kapcsolattartók
A támogatási webhely a Vállalati portálon jelenik meg, és lehetővé teszi a felhasználók számára az online támogatás elérését.

|Mező neve|Maximális hossz|További információ|
    |----------|------------------------|----------------|
    |Támogatási webhely URL-címe|150|Ha rendelkezik saját felhasználóinak szánt támogatási webhellyel, ide írja be az URL-címét. Az URL-címet a https://www.contoso.com formátumban kell megadni. Ha nem ad meg URL-címet, semmi sem jelenik meg a támogatási webhelyről a Vállalati portál **IT-csoport elérhetősége** lapján.|
    |Webhely neve|40|Ez a név a támogatási webhely URL-címének rövid neveként jelenik meg. Ha a támogatási webhelyhez csak URL-címet ad meg, de egyszerű nevet nem, akkor **Az IT-csoport weboldalának megnyitása** felirat jelenik meg a Vállalati portál **IT-csoport elérhetősége** lapján.|


#### Vállalati arculat szerinti testreszabás

A Vállalati portál testre szabható a vállalat emblémájának és nevének, valamint a téma színének és a háttérnek a megadásával.

|Mező neve|További információ|
    |----------|----------------|
    |Téma színe|A Vállalati portálra alkalmazni kívánt témaszín kiválasztása.|
    |Cég emblémájának megjelenítése|Ha engedélyezi ezt a beállítást, feltöltheti a Vállalati portálon megjeleníteni kívánt vállalati emblémát. Két emblémát tölthet fel: az egyik akkor jelenik meg, ha a Vállalati portál háttérszíne fehér, a másik pedig akkor, ha a Vállalati portál a témának megfelelő háttérszínnel jelenik meg. Mindkét emblémának egy .png vagy .jpg formátumú fájlnak kell lennie, melyek felbontása legfeljebb 400 x 100 képpont, mérete pedig legfeljebb 750 KB lehet.|
    |Háttér választása a [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] Vállalati portál alkalmazás számára|Ez a beállítás csak a [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] Vállalati portál alkalmazás hátterére van hatással.|


A módosítások mentése után a felügyeleti konzol **Vállalati portál** lapjának alján található hivatkozásokra kattintva megtekintheti a Vállalati portál webhelyét. Ezek a hivatkozások nem módosíthatók. A felhasználók bejelentkezésekor ezek a hivatkozások a Vállalati portálon megjelenítik az Ön előfizetéseit.

## Intune felhasználói licenc hozzárendelése

Az **Office 365 felügyeleti portáljának** használatával a felhőalapú felhasználók és licencek manuálisan hozzáadhatók, illetve hozzárendelhetők a felhőalapú felhasználói fiókokhoz és a helyszíni Active Directoryból az Azure AD-be szinkronizált fiókokhoz is.

1.  Jelentkezzen be az [Office 365 felügyeleti portálján](https://portal.office.com/Admin/Default.aspx) bérlői rendszergazdai hitelesítő adataival.

2.  Válassza ki azt a felhasználói fiókot, amelyhez Intune felhasználói licencet kíván hozzárendelni, és a felhasználói fiók tulajdonságainál jelölje be a **Microsoft Intune** jelölőnégyzetet.

3.  A felhasználói fiók ezzel bekerül a Microsoft Intune felhasználói csoportba, amely engedélyt ad a felhasználónak a szolgáltatás használatára és eszközeinek felügyeletre való regisztrálására.

## Eszközkezelés beállítása
A mobileszköz-kezelő szolgáltató beállítása után meg kell adnia az eszközkezelési beállításokat a szervezet által támogatni kívánt operációs rendszerekhez. Az eszközkezelés beállításához szükséges lépések az operációs rendszertől függően változhatnak. Android operációs rendszer esetén például semmit sem kell megadnia az Intune felügyeleti konzolon. Windows- és iOS-eszközökön azonban a felügyelet engedélyezéséhez megbízhatósági kapcsolatot kell beállítani az eszközök és az Intune között.

> [!div class="op_single_selector"]
- [Androidos eszközök Microsoft Intune-beli kezelésének beállítása](set-up-android-management-with-microsoft-intune.md)
- [Az iOS kezelésének beállítása a Microsoft Intune-nal](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Windows Phone-telefonok Microsoft Intune-beli kezelésének beállítása](set-up-windows-phone-management-with-microsoft-intune.md)
- [Windowsos eszközök Microsoft Intune-beli kezelésének beállítása](set-up-windows-device-management-with-microsoft-intune.md)

További lehetőségek:
 - Több eszköz regisztrálásához használja a [készülékregisztráció-kezelői fiókot](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
 - A [Vállalati tulajdonban lévő eszközök megadása IMEI-számokkal](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) című témakör az eszközök regisztrálásához, illetve a szabályzatok célzásához nyújt segítséget.



<!--HONumber=Jun16_HO4-->


