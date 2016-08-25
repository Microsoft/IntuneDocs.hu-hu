---
title: "iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: a1b2fb7f2938939725465a18efb594dda91d16bd


---

# iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban
A Microsoft Intune mobilalkalmazás-konfigurációs házirendjeivel automatikusan megadhatja az olyan beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy alkalmazást futtat. Egy alkalmazás kérheti a felhasználótól például a következők megadását:

-   Egy egyéni portszám a futtatáskor

-   Nyelvi beállítások

-   Biztonsági beállítások

-   Márkajelzési beállítások, például a vállalat logója

Ha ezeket a beállításokat a felhasználó helytelenül adja meg, az növelheti az ügyfélszolgálatra nehezedő terheket, és lelassíthatja az új alkalmazások bevezetését.

A mobilalkalmazás-konfigurációs házirendek segítséget nyújthatnak ezeknek a problémáknak a megoldásában azáltal, hogy lehetővé teszik ezeknek a beállításoknak a telepítését a felhasználók számára a házirendben még az alkalmazás futtatása előtt. A beállítások megadása ezek után automatikusan történik, és nincs szükség felhasználói beavatkozásra.

Nem kell telepítenie ezeket a házirendeket közvetlenül a felhasználók és eszközök számára. Ehelyett a házirendet társítani kell egy alkalmazáshoz, majd telepíteni kell az alkalmazást. A házirend-beállítások akkor lesznek felhasználva, amikor egy alkalmazás keresi azokat (általában az első futtatáskor).

> [!TIP]
> Ez a házirendtípus jelenleg csak az iOS 7.1-es és újabb verzióit futtató eszközökön érhető el, és a következő alkalmazástelepítés-típusokat támogatja:
> 
> -   **Felügyelt iOS-alkalmazás az App Store-ból**
> -   **Alkalmazáscsomag az iOS számára**
> 
> Az alkalmazástelepítés-típusokról bővebben a következő témakörben olvashat: [Alkalmazások telepítése a Microsoft Intune-ban](deploy-apps.md).

## Mobilalkalmazás-konfigurációs házirend konfigurálása

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Házirend** &gt; **Áttekintés** &gt; **Házirend hozzáadása** elemre.

2.  A házirendek listájában bontsa ki az **iOS**csomópontot, kattintson a **Mobilalkalmazás konfigurálása**lehetőségre, majd a **Házirend létrehozása**elemre.

    > [!TIP]
    > Ehhez a házirendtípushoz csak egyéni beállításokat lehet megadni. Ajánlott beállítások nem állnak rendelkezésre.

3.  A **Házirend létrehozása** lap **Általános** részében adja meg a mobilalkalmazás-konfigurációs házirend nevét és opcionális leírását.

4.  Az oldal **Mobilalkalmazás-konfigurációs házirend** részében írja vagy illessze be a mezőbe a kívánt alkalmazáskonfigurációs beállításokat tartalmazó XML-tulajdonságlistát.

    > [!TIP]
    > Az XML-tulajdonságlistákkal kapcsolatos további információért tekintse meg az iOS Developer Library [Understanding XML Property Lists ](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Az XML-tulajdonságlisták ismertetése) című témakörét.
    > 
    > Az XML-tulajdonságlista formátuma a konfigurálni kívánt alkalmazás függvényében eltérő. A használandó formátummal kapcsolatban forduljon az alkalmazás szállítójához.
    > 
    > Az Intune a következő adattípusokat támogatja a tulajdonságlistákban:
    > 
    > &lt;integer&gt;
    > &lt;real&gt;
    > &lt;string&gt;
    > &lt;array&gt;
    > &lt;dict&gt;
    > &lt;true /&gt; vagy &lt;false /&gt;
    > 
    > Az adattípusokkal kapcsolatban további információt az iOS Developer Library [About Property List](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) (Tulajdonságlisták) című témakörében talál.
    >
        > Ezenkívül az Intune a következő tokentípusokat támogatja a tulajdonságlistában:
    >    
    > \{\{userprincipalname\}\} - (példa: **John@contoso.com**) \{\{mail\}\} - (példa: **John@contoso.com**) \{\{partialupn\}\} - (példa: **John**) \{\{accountid\}\} - (példa: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**) \{\{deviceid\}\} - (példa: **b9841cd9-9843-405f-be28-b2265c59ef97**) \{\{userid\}\} - (példa: **3ec2c00f-b125-4519-acf0-302ac3761822**) \{\{username\}\} - (példa: **John Doe**) \{\{serialnumber\}\} - (példa: **F4KN99ZUG5V2**) iOS-eszközök esetében \{\{serialnumberlast4digits\}\} - (példa: **G5V2**) iOS-eszközök esetében
>
> A \{\{ és \}\} karaktereket csak a tokentípusok használják, ezek más célokra nem használhatók.




5.  Annak ellenőrzéséhez, hogy a megadott XML tulajdonságlista-formátuma érvényes-e, kattintson az **Ellenőrzés** lehetőségre.

    > [!IMPORTANT]
    > Amikor az **Ellenőrzés**lehetőségre kattint, az Intune ellenőrzi, hogy érvényes-e a megadott XML formátuma. Azt nem ellenőrzi, hogy az XML-tulajdonságlista működni fog-e az alkalmazással, amelyhez társítva van.

6.  Amikor elkészült, kattintson a **Házirend mentése**gombra.

Az új szabályzat megjelenik a **Konfigurációs szabályzatok** csomópontban.

## Mobilalkalmazás-konfigurációs házirend társítása egy alkalmazáshoz
A mobilalkalmazás-konfigurációs házirendet a létrehozást követően társítani kell ahhoz az iOS-alkalmazáshoz, amelyre a konfigurációs házirend beállításait alkalmazni kívánja.

Ehhez kövesse az alkalmazástelepítés létrehozásának lépéseit, amelyeket a következő témakörök ismertetnek: [Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md), illetve [Alkalmazások telepítése a Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md). Amikor eléri a varázsló **Mobilalkalmazás-konfiguráció** oldalát, az **Alkalmazáskonfigurációs házirend** legördülő listából válassza ki az alkalmazáshoz társítani kívánt házirendet.

Ezután a megszokott módon haladjon tovább az alkalmazás telepítésével és a telepítés nyomon követésével.

Amikor a telepített alkalmazást futtatják egy eszközön, akkor az a mobilalkalmazás-konfigurációs házirendben megadott beállításokkal fog futni.

> [!TIP]
> Ha egy vagy több mobilalkalmazás-konfigurációs szabályzatnál ütközés lép fel, a rendszer egyik szabályzatot sem tartatja be, az ütközésről pedig jelentés készül az Intune felügyeleti konzoljának **Irányítópult** területén.

## Mobilalkalmazás-konfigurációs XML-fájl példaformátuma

Mobilalkalmazás-konfigurációs fájl létrehozásakor a következő értékek közül egyet vagy többet adhat meg ebben a formátumban:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```





<!--HONumber=Jun16_HO4-->


