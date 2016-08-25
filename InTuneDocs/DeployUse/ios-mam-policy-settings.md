---
title: "Az iOS MAM-szabályzat beállításai | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5a445f06d6c2328f7689468ca4d68a969af1e825
ms.openlocfilehash: b3df4b35dbe2710157b88a4e7fdba9734f8b998b


---

#  iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása
Az alábbiakban ismertetett szabályzatbeállítások az Azure-portál **Beállítások** paneljén [konfigurálhatók](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) a MAM-szabályzatokhoz.

A szabályzatbeállításoknak két kategóriájuk van, az adatáthelyezési beállítások és a hozzáférési beállítások.

##  Adatáthelyezési beállítások
A **szabályzattal felügyelt alkalmazások** kifejezés azon alkalmazásokra utal, amelyekhez MAM-szabályzatot állítottak be.

- **iTunes- és iCloud-alapú biztonsági mentés tiltása:** az **Igen** gombbal letilthatja, a **Nem** gombbal engedélyezheti a vállalati adatok biztonsági mentését a szabályzattal felügyelt alkalmazásokban.

  **Alapértelmezett érték = Igen**

- **Az alkalmazás átadhat adatokat más alkalmazásoknak:** Valamelyik beállítás kiválasztásával jelezze, hogy mely alkalmazások fogadhassanak adatokat a szabályzat által felügyelt alkalmazásoktól:
  - **Házirend által felügyelt alkalmazások**: adatátvitel engedélyezése csak MAM-szabályzattal ellátott alkalmazásokba.
  - **Minden alkalmazás**: bármely alkalmazásba engedélyezett az adatok átvitele
  - **Nincs**: az adatátvitel egyetlen alkalmazásba sem engedélyezett, ideértve a szabályzat által felügyelt többi alkalmazást is.

  A **Házirend által felügyelt alkalmazások** vagy a **Nincs** beállítás alkalmazása esetén le lesz tiltva az iOS 9 rendszernek az a funkciója, amely lehetővé teszi, hogy a Spotlight-keresés adatokat keressen az alkalmazásokon belül.

  **Alapértelmezett érték = Házirend által felügyelt alkalmazások**

- **Az alkalmazás fogadhat adatokat más alkalmazásokból:** azon alkalmazások körét határozza meg, amelyek adatokat adhatnak át a szabályzat által felügyelt alkalmazásoknak:
  -  **Házirend által felügyelt alkalmazások**: az adatátvitel csak más szabályzat által felügyelt alkalmazásokból engedélyezett.
  -  **Minden alkalmazás**: az adatátvitel minden alkalmazásból engedélyezve van.
  -  **Nincs**: az adatátvitel minden alkalmazásból tiltva van.

  **Alapértelmezett érték = Minden alkalmazás**

- **A Mentés másként művelet letiltása:** Az **Igen** gombot választva letilthatja a Mentés másként funkció használatát bármely olyan alkalmazásban, amelyet ez a szabályzat felügyel. A **Nem** gombot választva engedélyezheti a Mentés másként funkció használatát.

  **Alapértelmezett érték = Igen**

- **Kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal:** Megadhatja, milyen esetekben korlátozza a kivágási, másolási és beillesztési műveleteket. A következő lehetőségek közül választhat:
  -   **Letiltva**: A kivágási, másolási és beillesztési műveletek tiltása a szabályzattal felügyelt alkalmazások között.
  -   **Szabályzattal felügyelt alkalmazások**: A kivágási, másolási és beillesztési műveletek elvégzése csak a szabályzattal felügyelt alkalmazások körében engedélyezett.
  -   **Szabályzattal felügyelt alkalmazások beillesztési lehetőséggel**: A kivágási vagy másolási művelet engedélyezett a szabályzattal felügyelt alkalmazások körében. A bármelyik alkalmazásból kivágott vagy másolt adatok beilleszthetők ebbe az alkalmazásba.
  - **Bármely alkalmazás**: az alkalmazások közötti kivágási, másolási és beillesztési műveletekre nem vonatkoznak korlátozások.

  **Alapértelmezett érték = Házirend által felügyelt alkalmazások beillesztési lehetőséggel**

- **A Managed Browser (felügyelt böngésző) alkalmazásban megjelenítendő webes tartalom korlátozása:** ha engedélyezve van ez a beállítás, az alkalmazásban esetleg szereplő hivatkozások a kezelt böngészőben fognak megnyílni.

  A mobilalkalmazás-felügyeleti szabályzat használata esetén az Intune-ban nem regisztrált eszközökön kizárólag a Managed Browser alkalmazásban nyílnak meg a webhivatkozások a szabályzat által felügyelt alkalmazásokban.

  Ha az Intune-t használja az eszközök felügyeletére, olvassa el [Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban](manage-internet-access-using-managed-browser-policies.md) című témakört.

    **Alapértelmezett érték = Igen**

- **Alkalmazás adatainak titkosítása:** Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] valamely mobilalkalmazás-felügyeleti szabályzatához társított alkalmazások esetén az adatok titkosítása az iOS által biztosított eszközszintű titkosítással történik. Ha PIN-kódra van szükség, az adattitkosítás a mobilalkalmazás-felügyeleti szabályzatban megadott beállítások szerint történik. Az Apple dokumentációjában leírtaknak megfelelően [az iOS 7 által használt modulokra érvényes a FIPS 140-2 tanúsítvány](http://support.apple.com/en-us/HT202739).

  A szabályzat-beállításokban megadhatja a PIN-kód titkosítási értékét.  Ezek az értékek meghatározzák, hogy mikor titkosítsa a rendszer az adatokat. Az alábbi lehetőségek állnak rendelkezésére:
  - **Ha az eszköz zárolva van:** a rendszer a szabályzathoz társított összes alkalmazásadatot titkosítja az eszköz zárolt állapotában.
  -   **Ha az eszköz zárolva van (kivéve a megnyitott fájlokat):** a rendszer a szabályzathoz társított összes alkalmazásadatot titkosítja az eszköz zárolt állapotában, az alkalmazásban aktuálisan megnyitott fájlok adatait kivéve.
  -   **Az eszköz újraindítása után:** a rendszer az eszköz újraindításakor a szabályzathoz társított összes alkalmazásadatot titkosítja, amíg fel nem oldják a zárolást az eszközön.
  -   **Eszközbeállítások használata:** a rendszer az eszköz alapértelmezett beállításai alapján titkosítja az alkalmazásadatokat.
  Ha engedélyezi ezt a beállítást, a végfelhasználónak PIN-kódot kell beállítania és használnia az eszköz eléréséhez.  Ha nincs beállítva PIN-kód, nem indulnak el az alkalmazások. A végfelhasználó üzenetben értesül arról, hogy a vállalat követelményei szerint PIN-kód beállítása szükséges az adott alkalmazás eléréséhez.

  **Alapértelmezett érték = A titkosítási beállítás nincs megadva**
- **Névjegy-szinkronizálás letiltása:** Válassza az **Igen** lehetőséget, ha nem szeretné, hogy a rendszer szinkronizálja a névjegyadatokat az eszköz natív címjegyzék-alkalmazásával. Ha a **Nem** lehetőséget választja, az alkalmazás az eszköz natív címjegyzék-alkalmazásába menti a névjegyadatokat.

  Ha szelektív törléssel távolítja el a vállalati adatokat, a rendszer törli az alkalmazásból közvetlenül a natív címjegyzékbe szinkronizált névjegyeket. A natív címjegyzékből egy másik külső forrásba szinkronizált névjegyek nem törölhetők. Ez jelenleg csak a **Microsoft Outlook** alkalmazásra érvényes.

  **Alapértelmezett érték = Igen**
##  A hozzáférési szabályzatok beállításai iOS rendszeren
A **szabályzattal felügyelt alkalmazások** kifejezés azon alkalmazásokra utal, amelyekhez MAM-szabályzatot állítottak be.
- **PIN-kód megkövetelése a hozzáféréshez:** Ha azt szeretné, hogy a szabályzattal felügyelt alkalmazások használatához PIN-kód megadása legyen szükséges, válassza az **Igen** lehetőséget. Ha a felhasználó első alkalommal futtatja az alkalmazást munkahelyi környezetben, a rendszer a kód beállítására kéri.

  **Alapértelmezett érték = Igen**
    -  **Egyszerű PIN-kód engedélyezése:** Azt határozza meg, hogy a felhasználó használhat-e egyszerű PIN-kódokat (például 1234 vagy 1111). **Alapértelmezett érték = Igen**.
    - **PIN-kód hossza:** Azt határozza meg, hogy a PIN-kódoknak legalább hány számjegyet kell tartalmazniuk. **Alapértelmezett érték = 4**
    - **Próbálkozások száma a PIN kód alaphelyzetbe állítása előtt:** Itt beállíthatja, hogy hányszor tehessen kísérletet a felhasználó a PIN-kód megadására, mielőtt a rendszer a PIN-kód alaphelyzetbe állítását kérné.
  **A beállításnak nincs alapértelmezett értéke**.

  - **Ujjlenyomat kérése PIN-kód helyett (iOS 8.0 és újabb)**: válassza az **Igen** lehetőséget, ha szeretné, hogy a rendszer számokból álló PIN-kód helyett ujjlenyomat-azonosítót kérjen az alkalmazás eléréséhez.
Az iOS-eszközökön engedélyezheti a felhasználóknak, hogy számjegyes PIN-kód helyett ujjlenyomattal azonosítsák magukat. Ha a végfelhasználó a munkahelyi fiókjával próbál hozzáférni az alkalmazáshoz, a rendszer a PIN-kód megadása helyett ujjlenyomat-azonosítót fog kérni.

    **Alapértelmezett érték = Igen**
- **Vállalati hitelesítő adatok szükségesek a hozzáféréshez:** ha az **Igen** gombot választja, a rendszer a számokból álló a PIN-kód helyett a vállalati hitelesítő adatokat kéri az alkalmazás eléréséhez. **Az Igen érték megadásával a rendszer felülírja a PIN-kóddal vagy az ujjlenyomatos azonosítással kapcsolatos követelményeket.** A rendszer a vállalati hitelesítő adatok megadását fogja kérni a felhasználótól.

  **Alapértelmezett érték = Nem**
- **A felügyelt alkalmazások futásának letiltása a függetlenített vagy feltört eszközökön:** Válassza az **Igen** lehetőséget, ha le szeretné tiltani az alkalmazások futását a függetlenített vagy feltört eszközökön. A felhasználó továbbra is használhatja az alkalmazásokat személyes feladatokhoz, de a munkavégzéshez másik eszközt kell használnia.

  **Alapértelmezett érték = Igen**
- **Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)**|-   **Időtúllépés:** ennyi idő elteltével kerül sor újra az alkalmazás hozzáférési követelményeinek ismételt ellenőrzésére (percben).
  -   **Offline türelmi időszak**: ennyi idő elteltével kerül sor újra az alkalmazás hozzáférési követelményeinek ismételt ellenőrzésére (percben), ha az eszköz offline állapotban van.

  **Alapértelmezett érték = 30 perces időkorlát és 720 perces offline türelmi időszak**
  - **Offline időszak az alkalmazásadatok törlése előtt (nap):** ha egy eszköz már bizonyos ideje offline állapotban van, a rendszer törölheti róla a vállalati adatokat.  A szabályzatbeállítások paneljén adhatja meg, hány napig lehet az eszköz offline állapotban, mielőtt a rendszer eltávolítaná róla a vállalati adatokat. **A 0 érték megadása kikapcsolja ezt a beállítást**.

  **Alapértelmezett érték = 90 nap**



<!--HONumber=Jun16_HO4-->


