---
title: Adatok törlése az App Protection-szabályzat feltételes indítási műveleteivel
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan törölheti az adatok szelektív törlését az alkalmazás-védelmi szabályzat feltételes indítási műveleteivel Microsoft Intuneban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0425b6a3f2c82f6ad2119286c8697f0eb0fc2f82
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513906"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Adatok szelektív törlése az App Protection-szabályzat feltételes indítási műveleteivel az Intune-ban

Az Intune alkalmazásvédelmi szabályzatainak használatával olyan beállításokat konfigurálhat, amelyek megakadályozzák, hogy a felhasználók hozzáférjenek egy vállalati alkalmazáshoz vagy fiókhoz. Ezek a vállalat által meghatározott adatáttelepítési és hozzáférési követelményekre vonatkozó beállítások például a feltört eszközök vagy a minimális operációsrendszer-verzió kezelésére.
 
Ezekkel a beállításokkal egyértelműen megadható az összes vállalati adat törlése a felhasználó eszközéről mint a nem megfelelőség esetén végrehajtandó művelet. Bizonyos beállításokhoz több művelet is konfigurálható, például a hozzáférés tiltása és az adatok törlése bizonyos megadott értékek alapján.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Alkalmazás-védelmi szabályzat létrehozása feltételes indítási műveletek használatával

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **alkalmazás-védelmi szabályzatok**lehetőséget.
3. Kattintson a **házirend létrehozása** elemre, és válassza ki az eszköz platformját a szabályzathoz. 
4. Kattintson a **Kötelező beállítások konfigurálása** lehetőségre a szabályzathoz konfigurálható beállítások listájának megjelenítéséhez. 
5. A Settings (beállítások) ablaktáblán lefelé görgetve megtekintheti a **feltételes indítás** nevű szakaszt egy szerkeszthető táblával.

    ![Képernyőkép az Intune alkalmazásvédelmi hozzáférési műveleteiről](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

6. Válasszon egy **Beállítást**, és adjon meg egy **Értéket**, amelynek a felhasználónak meg kell felelnie ahhoz, hogy bejelentkezhessen a vállalati alkalmazásába. 
7. Válassza ki a **Műveletet**, amelyet akkor kell végrehajtani, ha a felhasználó nem felel meg a követelményeknek. Bizonyos esetekben egy beállításhoz több művelet is megadható. További információt az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md) című cikkben talál.

## <a name="policy-settings"></a>Szabályzatbeállítások 

Az alkalmazásvédelmi szabályzatbeállítások táblázata a **Beállítás**, **Érték** és **Művelet** oszlopokból áll.

### <a name="ios-policy-settings"></a>iOS-es szabályzatbeállítások
Az iOS/iPadOS esetében a következő beállításokhoz tartozó műveleteket konfigurálhatja a **legördülő menü** használatával:
- PIN-kód-megadási kísérletek maximális száma
- Offline türelmi időszak
- Függetlenített/feltört eszközök
- Operációs rendszer minimális verziója
- Alkalmazás minimális verziója
- SDK minimális verziója
- Eszközmodell(ek)
- Az eszköz maximálisan engedélyezett veszélyforrása

Az **eszköz-modell (ek)** beállítás használatához adja meg az iOS/iPadOS modell-azonosítók pontosvesszővel elválasztott listáját. Ezek az értékek nem tesznek különbséget a kis-és nagybetűk között. Az "eszköz modell (ek)" bemenethez tartozó Intune-jelentéskészítésen kívül az iOS/iPadOS modell azonosítóját a [HockeyApp támogatási dokumentációjának](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) eszköz típusa oszlopában vagy a [harmadik fél GitHub-tárházában](https://gist.github.com/adamawolf/3048717)találhatja meg.<br>
Példabemenet: *iPhone5,2; iPhone5,3*

A végfelhasználói eszközökön az Intune-ügyfél az Intune-ban az Application Protection-szabályzatokhoz megadott eszközmodellsztringek egyszerű egyeztetése alapján végez műveleteket. Az egyeztetés teljes mértékben az eszköz által jelentett értéktől függ. Az informatikai rendszergazda számára ajánlatos ellenőrizni, hogy a szándéknak megfelelő viselkedés történik-e, ennek a beállításnak kölönféle eszközgyártókon és modelleken alapuló, kisméretű felhasználói csoportot célzó tesztelésével. Az alapértelmezett érték a **Nincs konfigurálva**.<br>
Állítsa be a következő műveletek egyikét: 
- Megadottak engedélyezése (nem megadottak tiltása)
- Megadottak engedélyezése (nem megadottak törlése)

**Mi történik, ha a rendszergazda bekapcsolja az iOS/iPadOS modell-azonosító (k) egy másik listáját az azonos Intune-felhasználóhoz tartozó házirendek között?**<br>
Ha két alkalmazásvédelmi szabályzat konfigurált értékei között ütközés van, az Intune általában a legkorlátozóbb megközelítést alkalmazza. Így a célként megadott Intune-felhasználó által a megnevezett alkalmazásnak küldött eredő házirend az *a szabályzatban* szereplő iOS/iPadOS-modell-azonosító (k), valamint a *B* házirend ugyanazon alkalmazás-és felhasználói kombinációra irányul. Ha például az *A szabályzat* meghatározza az „iPhone5,2; iPhone5,3” szabályt, míg a *B szabályzat* az „iPhone5,3” szabályt az *A szabályzat* és a *B szabályzat* által is megcélzott Intune-felhasználó számára az eredményül kapott szabályzat az „iPhone5,3” lesz. 

### <a name="android-policy-settings"></a>Android-szabályzat beállításai

Android rendszeren a következő beállításokhoz konfigurálhat műveleteket a **Beállítások** legördülő lista használatával:
- PIN-kód-megadási kísérletek maximális száma
- Offline türelmi időszak
- Függetlenített/feltört eszközök
- Operációs rendszer minimális verziója
- Alkalmazás minimális verziója
- Minimális javításverzió
- Eszközgyártó(k)
- Biztonság-eszköz igazolása
- Veszélyforrások vizsgálatának megkövetelése az alkalmazásokban
- Minimális Céges portál verzió
- Az eszköz maximálisan engedélyezett veszélyforrása

A **minimális céges portál verzió**használatával megadhatja a végfelhasználói eszközön kényszerített céges portál adott minimálisan meghatározott verzióját. Ez a feltételes indítási beállítás lehetővé teszi az értékek megadását a **hozzáférés letiltásához**, az **adatok törléséhez**és a **Figyelmeztetés** lehetséges műveletekhez, ha az egyes értékek nem teljesülnek. Az érték lehetséges formátumai a *[Major] mintát követik. [ Minor]* , *[főverzió]. [ Alverzió]. [Build]* vagy *[főverzió]. [ Alverzió]. [Build]. [Változat]* . Mivel előfordulhat, hogy egyes végfelhasználók nem részesítik előnyben az alkalmazások kényszerített frissítését a helyszínen, a "figyelmeztetés" beállítás ideális lehet a beállítás konfigurálásakor. Az Google Play Áruház jó munkát végez, amely csak az alkalmazások frissítéseinek különbözeti bájtjait küldi el, de ez továbbra is nagy mennyiségű adat lehet, amelyet a felhasználó esetleg nem szeretne használni, ha a frissítéskor adatokat használ. A frissítés kényszerítése és a frissített alkalmazások letöltése nem várt adatforgalmi díjat eredményezhet a frissítéskor. Ha be van állítva a **minimális céges portál verziószáma** , az hatással lesz minden olyan végfelhasználóra, aki beolvassa a céges portál és a céges portál jövőbeli verzióinak 5.0.4560.0 verzióját. Ez a beállítás nem lesz hatással a felhasználók olyan Céges portál verzióját használó felhasználóra, amely régebbi, mint a szolgáltatás által kiadott verzió. Az alkalmazás automatikus frissítéseit az eszközön használó végfelhasználók valószínűleg nem fogják látni a szolgáltatásból származó párbeszédpaneleket, mivel azok valószínűleg a legújabb Céges portál-verziót fogják használni. Ez a beállítás csak a regisztrált és a nem regisztrált eszközökön futó alkalmazás-védelemmel rendelkező Android.

Az **Eszközgyártó(k)** beállítás használatához gépelje be az Android-gyártók pontosvesszővel tagolt felsorolását. Ezek az értékek nem tesznek különbséget a kis-és nagybetűk között. Az Intune-jelentéskészítés mellett az eszközök androidos gyártóját is megtalálhatja az eszköz beállításai között. <br>
Példabemenet: *A gyártó;B gyártó* 

>[!NOTE]
> A következők az Intune-t használó eszközökhöz gyakran megadott gyártók, és bemenetként használhatók: Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

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

![Képernyőkép az App Protection-hozzáférési műveletekről – minimális operációsrendszer-verzió](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

Ha egy beállítás teljesen konfigurálva van, akkor a sor megjelenik a csak olvasható nézetben, de bármikor módosítható. Ezen kívül megjelenik egy sor, amelyben új érték választható ki a **Beállítás** oszlopban. Azok a már konfigurált beállítások, amelyekhez nem adható meg több művelet, nem lesznek kiválaszthatók a legördülő listában.

## <a name="next-steps"></a>További lépések

Az Intune alkalmazásvédelmi szabályzatairól a következő helyeken tájékozódhat bővebben:
- [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md)
- [iOS/iPadOS-alkalmazás védelmi házirendjének beállításai](app-protection-policy-settings-ios.md)
- [Android-eszközök alkalmazásvédelmi szabályzatainak beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) 
