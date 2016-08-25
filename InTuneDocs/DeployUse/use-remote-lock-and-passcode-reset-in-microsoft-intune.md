---
title: "Távoli zárolás és jelszó alaphelyzetbe állítása | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
translationtype: Human Translation
ms.sourcegitcommit: 6d9b79a09eef2546d78a19e061ba5cc3f24f645c
ms.openlocfilehash: 34379881b8299a2e3f9886b14b6d83e9dfe83373

---
# Az adatok védelme távoli zárolással és jelszó alaphelyzetbe állításával
A Microsoft Intune egyaránt biztosít távoli zárolásra és a jelszavak alaphelyzetbe állítására szolgáló képességeket.

## Eszköz távoli zárolása
Ha egy felhasználó elveszíti az eszközét, távolról zárolhatja azt. Az alábbi táblázatban áttekintheti, hogy hogyan működik a távoli zárolás az egyes mobilplatformokon.

|Platform|Távoli zárolás|
|------------|---------------|
|iOS|Támogatott|
|Android|Támogatott|
|Windows 10 mobil verzió|Támogatott|
|Windows Phone 8 és Windows Phone 8.1|Támogatott|
|Windows RT 8.1 és Windows RT|Támogatott, ha az eszköz aktuális felhasználója megegyezik az eszközt beléptető felhasználóval.|
|Windows 8.1|Támogatott, ha az eszköz aktuális felhasználója megegyezik az eszközt beléptető felhasználóval.|


### Mobileszköz zárolása távolról az Intune-konzollal

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) kattintson a **Csoportok** &gt; **Minden eszköz** &gt; **Minden mobileszköz** elemre.

2.  Kattintson a **Minden közvetlenül felügyelt eszköz** elemre az Intune-ban regisztrált eszközök megjelenítéséhez, vagy kattintson a **Minden Exchange ActiveSync által kezelt eszköz** elemre.

    > [!TIP]
    > Az eszközt akár a felhasználó alapján is megtalálhatja. Válassza a **Minden felhasználó** lehetőséget. A felhasználó Tulajdonságok lapján kattintson az **Eszközök** elemre, majd a törölni kívánt mobileszköz nevére.

3.  A listában kattintson a zárolni kívánt eszközre vagy eszközökre. A tálcán kattintson a **Távoli feladatok** elemre, és válassza a **Távoli zárolás** lehetőséget.

## Eszköz PIN-kódjának alaphelyzetbe állítása
Ha egy felhasználó elfelejti a PIN-kódját, segítségként eltávolíthatja a PIN-kódot az eszközről, vagy új ideiglenes PIN-kódot kényszeríthet az eszközre. Az alábbi táblázatban áttekintheti, hogy hogyan működik a PIN-kód cseréje az egyes mobilplatformokon.

|Platform|PIN-kód alaphelyzetbe állítása|
|------------|------------------|
|iOS|Csak a PIN-kód eszközről való törlése támogatott. Nem lehet új ideiglenes PIN-kódot létrehozni.|
|Android|Támogatott, és ideiglenes PIN-kód jön létre.|
|Windows 10 mobil verzió|Támogatott|
|Windows Phone 8 és Windows Phone 8.1|Támogatott|
|Windows RT 8.1 és Windows RT|Nem támogatott|
|Windows 8.1|Nem támogatott|

### Jelszó alaphelyzetbe állítása

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) kattintson a **Csoportok** &gt; **Minden eszköz** &gt; **Minden mobileszköz** elemre.

2.  Kattintson a **Minden közvetlenül felügyelt eszköz** elemre az Intune-ban regisztrált eszközök megjelenítéséhez, vagy kattintson a **Minden Exchange ActiveSync által kezelt eszköz** elemre.

    > [!TIP]
    > Az eszközt akár a felhasználó alapján is megtalálhatja. Kattintson a **Minden felhasználó** elemre. A felhasználó Tulajdonságok lapján kattintson az **Eszközök** elemre, majd a törölni kívánt mobileszköz nevére.

3.  A listában kattintson a zárolni kívánt eszközre vagy eszközökre. A tálcán kattintson a **Távoli feladatok** elemre, és válassza a **Jelszó alaphelyzetbe állítása** lehetőséget.


### További információ
[Eszköz kivonása](retire-devices-from-microsoft-intune-management.md)
[Windows szelektív törlés az eszközadatok felügyeletéhez](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Jun16_HO4-->


