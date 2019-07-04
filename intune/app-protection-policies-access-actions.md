---
title: Alkalmazás alkalmazásvédelmi szabályzat feltételes indítási műveletekről használatával adatok törlése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy a Microsoft Intune app protection szabályzat feltételes indítási műveletekről használata az adatok szelektív törlése.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65115f6520122cd4b3429411db67052481984617
ms.sourcegitcommit: cb4e71cd48311ea693001979ee59f621237a6e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67558444"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Az Intune app protection szabályzat feltételes indítási műveletekről használata az adatok szelektív törlése

Az Intune alkalmazásvédelmi szabályzatainak használatával olyan beállításokat konfigurálhat, amelyek megakadályozzák, hogy a felhasználók hozzáférjenek egy vállalati alkalmazáshoz vagy fiókhoz. Ezek a vállalat által meghatározott adatáttelepítési és hozzáférési követelményekre vonatkozó beállítások például a feltört eszközök vagy a minimális operációsrendszer-verzió kezelésére.
 
Ezekkel a beállításokkal egyértelműen megadható az összes vállalati adat törlése a felhasználó eszközéről mint a nem megfelelőség esetén végrehajtandó művelet. Bizonyos beállításokhoz több művelet is konfigurálható, például a hozzáférés tiltása és az adatok törlése bizonyos megadott értékek alapján.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Hozzon létre egy alkalmazásvédelmi szabályzatot használja a feltételes indítási műveletekről

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lehetőséget.
4. Kattintson a **Szabályzat hozzáadása** lehetőségre (a meglévő szabályzatok is módosíthatók). 
5. Kattintson a **Kötelező beállítások konfigurálása** lehetőségre a szabályzathoz konfigurálható beállítások listájának megjelenítéséhez. 
6. A Görgetés lefelé a beállítások ablaktáblában, látni fogja a szakaszig **feltételes indítási** egy szerkeszthető táblával.

    ![Képernyőkép az Intune alkalmazásvédelmi hozzáférési műveleteiről](./media/apps-selective-wipe-access-actions01.png)

7. Válasszon egy **Beállítást**, és adjon meg egy **Értéket**, amelynek a felhasználónak meg kell felelnie ahhoz, hogy bejelentkezhessen a vállalati alkalmazásába. 
8. Válassza ki a **Műveletet**, amelyet akkor kell végrehajtani, ha a felhasználó nem felel meg a követelményeknek. Bizonyos esetekben egy beállításhoz több művelet is megadható. További információt az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md) című cikkben talál.

>[!NOTE]
> Az **Eszközmodell(ek) vagy Eszközgyártó(k)** beállítás használatához gépelje be a modellazonosítók pontosvesszővel tagolt felsorolását. Több értéket tartalmazó felsorolásban kerülje a szóközöket. Ezekben az értékekben nincsenek megkülönböztetve a kis- és a nagybetűk. 

## <a name="policy-settings"></a>Szabályzatbeállítások 

Az alkalmazásvédelmi szabályzatbeállítások táblázata a **Beállítás**, **Érték** és **Művelet** oszlopokból áll.

### <a name="ios-policy-settings"></a>iOS-es szabályzatbeállítások
iOS rendszeren a következő beállításokhoz konfigurálhat műveleteket a **Beállítások** legördülő lista használatával:
- PIN-kód-megadási kísérletek maximális száma
- Offline türelmi időszak
- Függetlenített/feltört eszközök
- Operációs rendszer minimális verziója
- Alkalmazás minimális verziója
- SDK minimális verziója
- Eszközmodell(ek)

Az **Eszközmodell(ek)** beállítás használatához adjon meg egy iOS-modellazonosítókat tartalmazó, pontosvesszővel tagolt listát. Az iOS-modellazonosítót a [HockeyApp támogatási dokumentációjának](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) Eszköztípus oszlopában találja.<br>
Példabemenet: *iPhone5,2; iPhone5,3*

A végfelhasználói eszközökön az Intune-ügyfél az Intune-ban az Application Protection-szabályzatokhoz megadott eszközmodellsztringek egyszerű egyeztetése alapján végez műveleteket. Az egyeztetés teljes mértékben az eszköz által jelentett értéktől függ. Az informatikai rendszergazda számára ajánlatos ellenőrizni, hogy a szándéknak megfelelő viselkedés történik-e, ennek a beállításnak kölönféle eszközgyártókon és modelleken alapuló, kisméretű felhasználói csoportot célzó tesztelésével. Az alapértelmezett érték a **Nincs konfigurálva**.<br>
Állítsa be a következő műveletek egyikét: 
- Megadottak engedélyezése (nem megadottak tiltása)
- Megadottak engedélyezése (nem megadottak törlése)

**Mi történik, ha az informatikai rendszergazda az ugyanazokra az alkalmazásokra és azonos Intune-felhasználóra célzott szabályzatok között bemenetként a iOS-modellazonosítók egy másik listáját adja meg?**<br>
Ha két alkalmazásvédelmi szabályzat konfigurált értékei között ütközés van, az Intune általában a legkorlátozóbb megközelítést alkalmazza. Ezért a célzott Intune-felhasználó által megnyitott alkalmazásnak leküldött, eredményül kapott szabályzat az *A szabályzatban* és a *B szabályzatban* listázott iOS-modellazonosító(k) metszete lesz, ugyanarra az alkalmazás/felhasználó kombinációra célozva. Ha például az *A szabályzat* meghatározza az „iPhone5,2; iPhone5,3” szabályt, míg a *B szabályzat* az „iPhone5,3” szabályt az *A szabályzat* és a *B szabályzat* által is megcélzott Intune-felhasználó számára az eredményül kapott szabályzat az „iPhone5,3” lesz. 

### <a name="android-policy-settings"></a>Android-szabályzat beállításai

Android rendszeren a következő beállításokhoz konfigurálhat műveleteket a **Beállítások** legördülő lista használatával:
- PIN-kód-megadási kísérletek maximális száma
- Offline türelmi időszak
- Függetlenített/feltört eszközök
- Operációs rendszer minimális verziója
- Alkalmazás minimális verziója
- Minimális javításverzió
- Eszközgyártó(k)
- SafetyNet eszközigazolás
- Alkalmazások fenyegetettségvizsgálata

Az **Eszközgyártó(k)** beállítás használatához gépelje be az Android-gyártók pontosvesszővel tagolt felsorolását. Az eszköz Android-gyártóját az eszközbeállításokban találja meg.<br>
Példabemenet: *Gyártó A; B gyártója* 

>[!NOTE]
> Ezek az eszközök Intune-beli jelentett néhány gyakori gyártó, és bemenetként is használható: Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

A végfelhasználói eszközökön az Intune-ügyfél az Intune-ban az Application Protection-szabályzatokhoz megadott eszközmodellsztringek egyszerű egyeztetése alapján végez műveleteket. Az egyeztetés teljes mértékben az eszköz által jelentett értéktől függ. Az informatikai rendszergazda számára ajánlatos ellenőrizni, hogy a szándéknak megfelelő viselkedés történik-e, ennek a beállításnak kölönféle eszközgyártókon és modelleken alapuló, kisméretű felhasználói csoportot célzó tesztelésével. Az alapértelmezett érték a **Nincs konfigurálva**.<br>
Állítsa be a következő műveletek egyikét: 
- Megadottak engedélyezése (nem megadottak tiltása)
- Megadottak engedélyezése (nem megadottak törlése)

**Mi történik, ha az informatikai rendszergazda az ugyanazokra az alkalmazásokra és azonos Intune-felhasználóra célzott szabályzatok között bemenetként az Android-gyártók egy másik listáját adja meg?**<br>
Ha két alkalmazásvédelmi szabályzat konfigurált értékei között ütközés van, az Intune általában a legkorlátozóbb megközelítést alkalmazza. Ezért a célzott Intune-felhasználó által megnyitott alkalmazásnak leküldött, eredményül kapott szabályzat az *A szabályzatban* és a *B szabályzatban* listázott Android-gyártók metszete lesz, ugyanarra az alkalmazás/felhasználó kombinációra célozva. Ha például az *A szabályzat* meghatározza az „Google; Samsung” szabályt, míg a *B szabályzat* a „Google” szabályt, az *A szabályzat* és a *B szabályzat* által is megcélzott Intune-felhasználó számára az eredményül kapott szabályzat a „Google” lesz. 

### <a name="additional-settings-and-actions"></a>További beállítások és műveletek 

A táblázat néhány sora alapértelmezés szerint ki lesz töltve az **Offline türelmi időszak** és a **PIN-kód-megadási kísérletek maximális száma** beállítások konfigurációjával, ha a **PIN-kód megkövetelése a hozzáféréshez** beállítás **Igen** értékre van beállítva.
 
A beállítások konfigurálásához válasszon egy beállítást a **Beállítás** oszlop alatti legördülő listából. A beállítás kiválasztása után szerkeszthetővé válik az **Érték** oszlop alatti szövegmező, ha kötelező megadni egy értéket. Használhatóvá válik a **Művelet** oszlop alatti legördülő lista is, amely a beállításhoz tartozó feltételesen végrehajtható műveleteket tartalmazza. 

A következő lista a leggyakoribb műveleteket sorolja fel:
- **Hozzáférés letiltása** – Letiltja a végfelhasználó hozzáférését a vállalati alkalmazáshoz.
- **Összes adat törlése** – Az összes vállalati adat törlése a végfelhasználó eszközéről.
- **Figyelmeztetés** – Figyelmeztető üzenetet jelenít meg a végfelhasználó számára.

Bizonyos beállítások, például az **Operációs rendszer minimális verziója**, a különféle verziószámok alapján minden lehetséges műveletet végrehajtásához konfigurálhatók. 

![Képernyőkép a app protection hozzáférési műveletek – minimális operációsrendszer-verzió](./media/apps-selective-wipe-access-actions05.png)

Ha egy beállítás teljesen konfigurálva van, akkor a sor megjelenik a csak olvasható nézetben, de bármikor módosítható. Ezen kívül megjelenik egy sor, amelyben új érték választható ki a **Beállítás** oszlopban. Azok a már konfigurált beállítások, amelyekhez nem adható meg több művelet, nem lesznek kiválaszthatók a legördülő listában.

## <a name="next-steps"></a>További lépések

Az Intune alkalmazásvédelmi szabályzatairól a következő helyeken tájékozódhat bővebben:
- [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md)
- [iOS-eszközök alkalmazásvédelmi szabályzatainak beállításai](app-protection-policy-settings-ios.md)
- [Android-eszközök alkalmazásvédelmi szabályzatainak beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) 
