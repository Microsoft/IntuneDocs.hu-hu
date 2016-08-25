---
title: "Az Android MAM-szabályzat beállításai | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5a445f06d6c2328f7689468ca4d68a969af1e825
ms.openlocfilehash: 3f43dc871dc0b0a81a6d0b05376a1254957fc35b


---

# Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban
Az alábbiakban ismertetett szabályzatbeállítások az Azure-portál **Beállítások** paneljén [konfigurálhatók](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) a MAM-szabályzatokhoz.
A szabályzatbeállításoknak két kategóriájuk van, az adatáthelyezési beállítások és a hozzáférési beállítások.

##  Adatáthelyezési beállítások
A **szabályzattal felügyelt alkalmazások** kifejezés azon alkalmazásokra utal, amelyekhez MAM-szabályzatot állítottak be.
- **Android-alapú biztonsági mentések tiltása:** Az **Igen** gombbal letilthatja, a **Nem** gombbal engedélyezheti a vállalati adatok biztonsági mentését a szabályzattal felügyelt alkalmazásokban.

  **Alapértelmezett érték = Igen**
- **Az alkalmazás átadhat adatokat más alkalmazásoknak:** Valamelyik beállítás kiválasztásával jelezze, hogy melyik alkalmazások fogadhassanak vállalati adatokat a szabályzattal felügyelt alkalmazásoktól:
  -   **Szabályzattal felügyelt alkalmazások**: Adatátvitel engedélyezése csak MAM-szabályzattal ellátott alkalmazásokba.
  -   **Minden alkalmazás**: Minden alkalmazásba engedélyezett az adatok átvitele.
  -   **Nincs**: Minden alkalmazásba tiltott az adatátvitel.

  **Alapértelmezett érték = Szabályzattal felügyelt alkalmazások**
- **Az alkalmazás fogadhat adatokat más alkalmazásokból:** Azon alkalmazások körét határozza meg, amelyek adatokat adhatnak át a szabályzattal felügyelt alkalmazásoknak:
  -   **Szabályzattal felügyelt alkalmazások**: Az adatátvitel csak más szabályzattal felügyelt alkalmazásokból engedélyezett.
  -   **Minden alkalmazás**: Az adatátvitel minden alkalmazásból engedélyezett.
  -   **Nincs**: Az adatátvitel minden alkalmazásból tiltva van.

      **Alapértelmezett érték = Minden alkalmazás**

-   **A Mentés másként művelet letiltása:** Az **Igen** gombot választva letilthatja a Mentés másként funkció használatát bármely olyan alkalmazásban, amelyet ez a szabályzat felügyel. A **Nem** gombot választva engedélyezheti a Mentés másként funkció használatát.

  **Alapértelmezett érték = Igen**
- **Kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal:** Megadhatja, milyen esetekben korlátozza a kivágási, másolási és beillesztési műveleteket. A következő lehetőségek közül választhat:
  -   **Letiltva**: A kivágási, másolási és beillesztési műveletek tiltása a szabályzattal felügyelt alkalmazások között.
  -   **Szabályzattal felügyelt alkalmazások**: A kivágási, másolási és beillesztési műveletek elvégzése csak a szabályzattal felügyelt alkalmazások körében engedélyezett.
  -   **Szabályzattal felügyelt alkalmazások beillesztési lehetőséggel**: A kivágási vagy másolási művelet engedélyezett a szabályzattal felügyelt alkalmazások körében. A bármelyik alkalmazásból kivágott vagy másolt adatok beilleszthetők ebbe az alkalmazásba.
  -   **Bármely alkalmazás**: Az alkalmazások közötti kivágási, másolási és beillesztési műveletek nem korlátozottak.

    **Alapértelmezett érték = Szabályzattal felügyelt alkalmazások beillesztési lehetőséggel**
-   **A Managed Browser (felügyelt böngésző) alkalmazásban megjelenítendő webes tartalom korlátozása:** Ha engedélyezve van ez a beállítás, az alkalmazásban szereplő esetleges hivatkozások a kezelt böngészőben fognak megnyílni.

  Az Intune-ban nem regisztrált eszközök esetében a szabályzattal felügyelt alkalmazásokban a webhivatkozások a mobilalkalmazás-felügyeleti szabályzat használatakor kizárólag a Managed Browser alkalmazásban nyílnak meg.

  Ha az Intune-t használja az eszközök kezeléséhez, olvassa el [Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban](manage-internet-access-using-managed-browser-policies.md) című témakört.

    **Alapértelmezett érték = Igen**
- **Alkalmazásadatok titkosítása:** Válassza az **Igen** lehetőséget a titkosítás engedélyezéséhez. Amikor engedélyezve van ez a beállítás, a mobilalkalmazás-felügyeleti szabályzattal társított alkalmazások esetén a titkosításról a Microsoft gondoskodik. A rendszer szinkron módon titkosítja az adatokat a fájlok írási és olvasási műveletei során. Az eszköz tárhelyén található tartalom mindig titkosított marad.
  >[!NOTE]
  >A titkosítási módszerre nem érvényes a FIPS 140-2 típusú tanúsítvány

  **Alapértelmezett érték = Igen**

- **Névjegy-szinkronizálás letiltása:** Válassza az **Igen** lehetőséget, ha nem szeretné, hogy a rendszer szinkronizálja a névjegyadatokat az eszköz natív címjegyzék-alkalmazásával. Ha a **Nem** lehetőséget választja, az alkalmazás az eszköz natív címjegyzék-alkalmazásába menti a névjegyadatokat.<br/>Ha szelektív törléssel távolítja el a vállalati adatokat, a rendszer törli az alkalmazásból közvetlenül a natív címjegyzékbe szinkronizált névjegyeket. A natív címjegyzékből egy másik külső forrásba szinkronizált névjegyek nem törölhetők. Ez jelenleg csak a **Microsoft Outlook** alkalmazásra érvényes.

  **Alapértelmezett érték = Igen**

##  A hozzáférési szabályzatok beállításai Android rendszeren
A **szabályzattal felügyelt alkalmazások** kifejezés azon alkalmazásokra utal, amelyekhez MAM-szabályzatot állítottak be.

- **PIN-kód megkövetelése a hozzáféréshez:** Ha szeretné, hogy a szabályzattal felügyelt alkalmazások használatához PIN-kód megadása legyen szükséges, válassza az **Igen** lehetőséget. Ha a felhasználó első alkalommal futtatja az alkalmazást munkahelyi környezetben, a rendszer a kód beállítására kéri.

 **Alapértelmezett érték = Igen**

 -  **Egyszerű PIN-kód engedélyezése:** Azt határozza meg, hogy a felhasználó használhat-e egyszerű PIN-kódokat (például 1234 vagy 1111). **Alapértelmezett érték = Igen**.
 - **PIN-kód hossza:** Azt határozza meg, hogy a PIN-kódoknak legalább hány számjegyet kell tartalmazniuk. **Alapértelmezett érték = 4**
 - **Próbálkozások száma a PIN kód alaphelyzetbe állítása előtt:** Itt beállíthatja, hogy hányszor tehessen kísérletet a felhasználó a PIN-kód megadására, mielőtt a rendszer a PIN-kód alaphelyzetbe állítását kérné. **A beállításnak nincs alapértelmezett értéke.**
- **Vállalati hitelesítő adatok szükségesek a hozzáféréshez:** Az **Igen** lehetőséget választva a rendszer a számokból álló PIN-kód helyett vállalati hitelesítő adatokat kér az alkalmazás eléréséhez.  Az **Igen** érték megadásával a rendszer felülírja a PIN-kóddal vagy az ujjlenyomatos azonosítással kapcsolatos követelményeket.  A rendszer a vállalati hitelesítő adatok megadását fogja kérni a felhasználótól.

  **Alapértelmezett érték = Nem**
- **A felügyelt alkalmazások futásának letiltása a függetlenített vagy feltört eszközökön:** Válassza az **Igen** lehetőséget, ha le szeretné tiltani az alkalmazások futását a függetlenített vagy feltört eszközökön. A felhasználó továbbra is használhatja az alkalmazásokat személyes feladatokhoz, de a munkavégzéshez másik eszközt kell használnia.

  **Alapértelmezett érték = Igen**
- **Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)**-   **Időtúllépés:** ennyi idő elteltével kerül sor újra az alkalmazás hozzáférési követelményeinek ismételt ellenőrzésére (percben).
  -   **Offline türelmi időszak**: ennyi idő elteltével kerül sor újra az alkalmazás hozzáférési követelményeinek ismételt ellenőrzésére (percben), ha az eszköz offline állapotban van.

    **Alapértelmezett érték = 30 perces időkorlát és 720 perces offline türelmi időszak**

-   **Offline időszak az alkalmazásadatok törlése előtt (nap):** ha egy eszköz már bizonyos ideje offline állapotban van, a rendszer törölheti róla a vállalati adatokat.  A szabályzatbeállítások paneljén adhatja meg, hány napig lehet az eszköz offline állapotban, mielőtt a rendszer eltávolítaná róla a vállalati adatokat. **Tipp:** A 0 érték megadása kikapcsolja ezt a beállítást.

  **Alapértelmezett érték = 90 nap**
- **Képernyőfelvétel és az Android Assistant alkalmazás tiltása (Android 6 Marshmallow vagy újabb):** Válassza az **Igen** lehetőséget a képernyőfelvétel-készítés és az eszköz **Android Assistant**-funkcióinak letiltásához az alkalmazás használatakor.



<!--HONumber=Jun16_HO4-->


