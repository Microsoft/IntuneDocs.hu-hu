---
title: Adatok törlése az App Protection-szabályzat feltételes indítási műveleteivel
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan törölheti az adatok szelektív törlését az alkalmazás-védelmi szabályzat feltételes indítási műveleteivel Microsoft Intuneban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/24/2019
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
ms.openlocfilehash: 882c542d6a1d981b9924bb33eee40f03b41689f7
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999476"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Adatok szelektív törlése az App Protection-szabályzat feltételes indítási műveleteivel az Intune-ban

Az Intune alkalmazásvédelmi szabályzatainak használatával olyan beállításokat konfigurálhat, amelyek megakadályozzák, hogy a felhasználók hozzáférjenek egy vállalati alkalmazáshoz vagy fiókhoz. Ezek a vállalat által meghatározott adatáttelepítési és hozzáférési követelményekre vonatkozó beállítások például a feltört eszközök vagy a minimális operációsrendszer-verzió kezelésére.
 
Ezekkel a beállításokkal egyértelműen megadható az összes vállalati adat törlése a felhasználó eszközéről mint a nem megfelelőség esetén végrehajtandó művelet. Bizonyos beállításokhoz több művelet is konfigurálható, például a hozzáférés tiltása és az adatok törlése bizonyos megadott értékek alapján.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Alkalmazás-védelmi szabályzat létrehozása feltételes indítási műveletek használatával

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lehetőséget.
4. Kattintson a **Szabályzat hozzáadása** lehetőségre (a meglévő szabályzatok is módosíthatók). 
5. Kattintson a **Kötelező beállítások konfigurálása** lehetőségre a szabályzathoz konfigurálható beállítások listájának megjelenítéséhez. 
6. A Settings (beállítások) ablaktáblán lefelé görgetve megtekintheti a **feltételes indítás** nevű szakaszt egy szerkeszthető táblával.

    ![Képernyőkép az Intune alkalmazásvédelmi hozzáférési műveleteiről](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

7. Válasszon egy **Beállítást**, és adjon meg egy **Értéket**, amelynek a felhasználónak meg kell felelnie ahhoz, hogy bejelentkezhessen a vállalati alkalmazásába. 
8. Válassza ki a **Műveletet**, amelyet akkor kell végrehajtani, ha a felhasználó nem felel meg a követelményeknek. Bizonyos esetekben egy beállításhoz több művelet is megadható. További információt az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md) című cikkben talál.

>[!NOTE]
> Az **eszköz modell (ek) vagy az eszköz gyártó (k)** beállításainak használatához adja meg az eszköz modell-azonosítóinak (iOS) vagy az eszközök gyártóinak (Android) pontosvesszővel tagolt listáját. Több értéket tartalmazó felsorolásban kerülje a szóközöket. Ezekben az értékekben nincsenek megkülönböztetve a kis- és a nagybetűk. 

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
- Az eszköz maximálisan engedélyezett veszélyforrása

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
- Biztonság-eszköz igazolása
- Veszélyforrások vizsgálatának megkövetelése az alkalmazásokban
- Minimális Céges portál verzió
- Az eszköz maximálisan engedélyezett veszélyforrása

A **minimális céges portál verzió**használatával megadhatja a végfelhasználói eszközön kényszerített céges portál adott minimálisan meghatározott verzióját. Ez a feltételes indítási beállítás lehetővé teszi az értékek megadását a **hozzáférés letiltásához**, az **adatok törléséhez**és a **Figyelmeztetés** lehetséges műveletekhez, ha az egyes értékek nem teljesülnek. Az érték lehetséges formátuma a *[Major] mintázatot követi. [ Minor]* , *[főverzió]. [ Alverzió]. [Build]* vagy *[főverzió]. [ Alverzió]. [Build]. [Változat]* . Mivel előfordulhat, hogy egyes végfelhasználók nem részesítik előnyben az alkalmazások kényszerített frissítését a helyszínen, a "figyelmeztetés" beállítás ideális lehet a beállítás konfigurálásakor. Az Google Play Áruház jó munkát végez, amely csak az alkalmazások frissítéseinek különbözeti bájtjait küldi el, de ez továbbra is nagy mennyiségű adat lehet, amelyet a felhasználó esetleg nem szeretne használni, ha a frissítéskor adatokat használ. A frissítés kényszerítése és a frissített alkalmazások letöltése nem várt adatforgalmi díjat eredményezhet a frissítéskor. Ha be van állítva a **minimális céges portál verziószáma** , az hatással lesz minden olyan végfelhasználóra, aki beolvassa a céges portál és a céges portál jövőbeli verzióinak 5.0.4560.0 verzióját. Ez a beállítás nem lesz hatással a felhasználók olyan Céges portál verzióját használó felhasználóra, amely régebbi, mint a szolgáltatás által kiadott verzió. Az alkalmazás automatikus frissítéseit az eszközön használó végfelhasználók valószínűleg nem fogják látni a szolgáltatásból származó párbeszédpaneleket, mivel azok valószínűleg a legújabb Céges portál-verziót fogják használni. Ez a beállítás csak a regisztrált és a nem regisztrált eszközökön futó alkalmazás-védelemmel rendelkező Android.

Az **Eszközgyártó(k)** beállítás használatához gépelje be az Android-gyártók pontosvesszővel tagolt felsorolását. Az eszköz Android-gyártóját az eszközbeállításokban találja meg.<br>
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
- [iOS-eszközök alkalmazásvédelmi szabályzatainak beállításai](app-protection-policy-settings-ios.md)
- [Android-eszközök alkalmazásvédelmi szabályzatainak beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) 
