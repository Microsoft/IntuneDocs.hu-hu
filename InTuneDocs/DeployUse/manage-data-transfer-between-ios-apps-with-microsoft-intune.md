---
title: "iOS-alkalmazások közti adatátvitel felügyelete | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 002ebec14a089754849024916590b787431c7efe
ms.openlocfilehash: fce0081fc1ecb92acf539a2d69f0493fb30ee418


---

# iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-nal
## IOS-alkalmazások felügyelete
A vállalati adatok védelmébe tartozik annak biztosítása, hogy csak a vállalat által felügyelt alkalmazásokkal lehessen fájlokat átvinni.  Az iOS-alkalmazásokat az alábbi módokon felügyelheti:

-   Vállalati adatvesztés megakadályozása MAM-szabályzatok konfigurálásával az alkalmazások számára. Az ilyen alkalmazásokat **szabályzattal felügyelt** alkalmazásoknak nevezzük.

-   Az **MDM-csatornán** keresztül is telepíthet és felügyelhet alkalmazásokat.  Ehhez az eszközöket az MDM-megoldásba kell regisztrálni. Ezek **házirenddel felügyelt** alkalmazások vagy más felügyelt alkalmazások is lehetnek.

Az iOS-eszközök **Megnyitási engedélyek felügyelete** szolgáltatásával a fájlátvitel az **MDM-csatornával** telepített alkalmazásokra korlátozható. A Megnyitási engedélyek felügyeletének korlátozásai a konfiguráció beállításaiban adhatók meg, és a mobileszköz-kezelési megoldás használatával telepíthetők.  Amikor a felhasználó telepíti a központilag telepített alkalmazást, a rendszer alkalmazza a beállított korlátozásokat.
##  MAM használata iOS-alkalmazásokban
A mobilalkalmazás-felügyeleti (MAM-) szabályzatok az iOS **Megnyitási engedélyek felügyelete** szolgáltatásával együtt használhatók a vállalati adatok védelméhez, a következő módokon:

-   **Alkalmazottak tulajdonában lévő, mobileszköz-kezelési megoldás által nem kezelt eszközök:** a mobilalkalmazás-kezelési megoldás szabályzati beállításait beállíthatja a következőre: **Az alkalmazás átadhat adatokat házirend által felügyelt alkalmazásoknak**. Ha a végfelhasználó nem házirenddel felügyelt alkalmazásban nyit meg egy védett fájlt, a fájl nem olvasható.

-   **Az Intune által felügyelt eszközök:** az Intune-ban regisztrált eszközök esetén a MAM-szabályzatokkal rendelkező és az Intune használatával telepített egyéb felügyelt iOS-alkalmazások közötti adatátvitel automatikusan engedélyezett. A MAM-szabályzatokkal rendelkező alkalmazások közötti adatátvitel engedélyezéséhez aktiválja **Az alkalmazás átadhat adatokat szabályzat által felügyelt alkalmazásoknak** beállítást. Az Intune-nal telepített alkalmazások között a **Megnyitási engedélyek felügyelete** funkcióval vezérelhető az adatátvitel.   

-   **Külső MDM-megoldás által felügyelt eszközök:** Az adatátvitel a felügyelt alkalmazásokra korlátozható az IOS **Megnyitási engedélyek felügyelete** funkciójával.
Annak biztosításához, hogy a harmadik féltől származó MDM megoldás segítségével központilag telepített alkalmazások is társítva legyenek az Intune-ban beállított MAM-szabályzatokhoz, konfigurálnia kell a felhasználói UPN-beállítást, [A felhasználói UPN-beállítás konfigurálása](#configure-user-upn-setting) című cikkben ismertetett lépések szerint.  Ha az alkalmazásokat a felhasználói UPN-beállítással telepítik, akkor a MAM-szabályzatok érvénybe lépnek az alkalmazásra vonatkozóan, amikor a végfelhasználó a munkahelyi fiókjával jelentkezik be.

> [!IMPORTANT]
> A felhasználói UPN-beállításra csak a külső MDM által felügyelt eszközökre telepített alkalmazások esetén van szükség.  Az Intune-nal felügyelt eszközök esetén erre a beállításra nincs szükség.

## A felhasználói UPN-beállítás konfigurálása
Erre a konfigurációra külső MDM-megoldás által felügyelt eszközök esetén van szükség. Az alább leírt eljárás egy általános módszer az UPN-beállítás és az eredményül kapott végfelhasználói élmény megvalósításához:


1.  Az Azure-portálon [konfiguráljon mobilalkalmazás-felügyeleti szabályzatot](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) iOS platformra. A vállalati igényeknek megfelelően konfigurálja a szabályzat beállításait, majd válassza ki az alkalmazásokat, amelyeknek ezzel a szabályzattal kell rendelkezniük.

2.  A felügyelni kívánt alkalmazásokat és az e-mail profilt telepítse **saját külső MDM-megoldásával** a 3. és 4. lépésekben leírt beállítások használatával.

3.  Az alkalmazást a következő alkalmazáskonfigurációs beállításokkal telepítse: key=IntuneMAMUPN, Value=<felhasznalo@vallalat.com> [példa: ‘IntuneMAMUPN’, ‘janos@microsoft.com’]

4.  Telepítse a Megnyitási engedélyek felügyelete házirendet a regisztrált eszközökre.

### Végfelhasználói élmény példája

1.  A végfelhasználó telepíti a Microsoft Word alkalmazást az eszközre.

2.  A végfelhasználó elindítja a felügyelt natív levelezőalkalmazást az e-mailjei eléréséhez.

3.  A végfelhasználó megpróbál megnyitni egy dokumentumot egy natív e-mailből a Microsoft Word programban.

4.  A Word elindulásakor a rendszer felkéri a végfelhasználót, hogy jelentkezzen be a munkahelyi fiókjával.  Ennek a végfelhasználó által, kérésre megadott munkahelyi fióknak meg kell egyeznie a Microsoft Word alkalmazás számára az alkalmazás konfigurációs beállításaiban megadott fiókkal.

    > [!NOTE]
    > A végfelhasználó más személyes fiókokat is hozzáadhat a Wordhöz személyes munkájának elvégzéséhez, és a MAM-szabályzatok nem vonatkoznak rá a Word alkalmazás személyes használatakor.

5.  Amikor a bejelentkezés sikeres, az alkalmazás házirend-beállításai érvénybe lépnek a Word alkalmazásnál.

6.  Mostantól az adatátvitel sikeres lesz, és a dokumentum vállalati identitásként van megjelölve az alkalmazásban. Ezenkívül a rendszer munkahelyi környezetben kezeli az adatokat, és ennek megfelelően alkalmazza a szabályzatbeállításokat.

### További információ
[Alkalmazásadatok védelme mobilalkalmazás-kezelési szabályzatokkal a Microsoft Intune segítségével](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


