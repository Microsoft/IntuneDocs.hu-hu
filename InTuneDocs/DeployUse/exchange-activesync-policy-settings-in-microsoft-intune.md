---
title: "Exchange ActiveSync házirend-beállítások | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: 7ab9c5f283f65c82e1713d29923fa16a6a542352


---

# Exchange ActiveSync házirend-beállítások a Microsoft Intune-ban
A Microsoft Intune **Exchange ActiveSync**-házirendjének használatával megadhatók azok a beállítások, amelyekkel az Exchange ActiveSync által kezelt eszközök szolgáltatásai és funkciói széles körben vezérelhetővé válnak.


## Jelszóbeállítások

|Beállítás neve|Részletek
|----------------|
|**Jelszó szükséges a mobileszközök feloldásához**|Meghatározza, hogy az eszközöket jelszóval kell-e zárolni.<br>(A Windows RT rendszerű eszközökre nem vonatkozik.)|
|**Kötelező jelszótípus**|A megkövetelt jelszótípust határozza meg, például hogy a jelszó csak számokat, vagy számokat és betűket is tartalmazzon.|
|**Jelszó minimális hossza**|A jelszóban használandó karakterek minimális számát határozza meg.|
|**Egyszerű jelszavak engedélyezése**|Egyszerű jelszó például a „0000” és az „1234”.|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|A helyes jelszó megadására tett engedélyezett próbálkozások száma az eszköz törlése előtt.|
|**Jelszó lejárata (nap)**|Ennyi nap elteltével kell megváltoztatni az eszköz jelszavát.
|**Jelszóelőzmények megjegyzése**|Megadja, hogy használhatók-e a korábban már használt jelszavak.|
|**Korábbi jelszavak megjegyzése** – **Korábbi jelszavak újbóli használatának tiltása**|Meghatározza, hogy hány jelszóra visszamenőleg nem használható egy már korábban használt jelszó.|
|**Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót**|Meghatározza, hogy az eszköznek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.

## Titkosítási beállítások

|Beállítás neve|Részletek|
|----------------|
|**Titkosítás megkövetelése mobileszközön**<sup>1</sup>|Ha az eszköz támogatja a titkosítást, titkosítani kell a rajta lévő adatokat.<br>A Windows Phone 8-telefonokon ezt **Igen**értékre kell állítani.<br /><br />Az iOS-eszközök titkosításának engedélyezéséhez **A mobileszközök zárolásának feloldásához jelszó szükséges**beállítást engedélyezni kell.|
|**Titkosítás megkövetelése tárolókártyákon**|A külső tárhelyen, például egy SD-kártyán tárolt adatok titkosítása szükséges (a támogatott eszközökön).
<sup>1</sup> További információk a Windows 8.1 rendszerű eszközökhöz

-   A Windows 8.1 rendszerű eszközökön a titkosítás kényszerítéséhez minden egyes eszközön telepíteni kell a következőt: [2014. decemberi MDM-ügyfélfrissítés Windows rendszerre](http://support.microsoft.com/kb/3013816) .

-   Ha engedélyezi ezt a beállítást a Windows 8.1 rendszerű eszközökön, az eszköz valamennyi felhasználójának rendelkeznie kell Microsoft-fiókkal.

-   A titkosítás működéséhez az eszköznek teljesítenie kell a Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) hardvertanúsítvány követelményeit.

-   Amikor kényszeríti az eszközön a titkosítást, a Microsoft-fiókkal rendelkező felhasználók részéről a helyreállítási kulcs csak a OneDrive-fiókjukból érhető el. Ez a kulcs nem állítható vissza egy felhasználó nevében.

## E-mail beállítások

|Beállítás neve|Részletek
|----------------|
|**Az e-mail mellékletek letöltésének engedélyezése a felhasználók számára**|Megadja, hogy le lehet-e tölteni az e-mail mellékleteket az eszközre.|
|**E-mail szinkronizálási időszak**|Válassza ki, hogy hány napnyi beérkezett e-mail szinkronizálódjon az eszközzel.
|**Engedélyezze az Exchange ActiveSync-beállításokat nem teljes mértékben támogató eszközök szinkronizálását az Exchange kiszolgálóval**|A beállítással megadható, hogy engedélyezi-e az Exchange kiszolgálóhoz a hozzáférést az Exchange ActiveSync-beállításokat csak részben vagy egyáltalán nem támogató eszközök számára.

## Webböngésző beállításai

|Beállítás neve|Részletek
|----------------|-
|**Webböngésző használatának engedélyezése**|A beállítás meghatározza, hogy használható-e az eszközön a webböngésző.<br>(Windows RT vagy Windows Phone esetén nem érhető el.)

## Hardverbeállítások

|Beállítás neve|Részletek
|----------------|
|**Kamera használatának engedélyezése**|A beállítás meghatározza, hogy használható-e az eszközön a kamera.<br>(Windows RT vagy Windows Phone esetén nem érhető el.)



### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


