---
title: "A Vállalati portál alkalmazás üzeneteinek ismertetése a végfelhasználókkal | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 40f2ead80326a451dfd59a4969191009dc35deef


---

# A Vállalati portál alkalmazás üzeneteinek ismertetése a végfelhasználókkal

A következő információk kizárólag Android 6.0-s és újabb rendszerű eszközökre vonatkoznak. Az eszközregisztrálási folyamat során a végfelhasználóknak két üzenet jelenik meg:

- Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)
- Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)

A következők bekezdésekben erről a két üzenetről tudhat meg többet, valamint olyan ismereteket szerezhet róluk, amelyeket megoszthat végfelhasználóival.

## Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)

### Az üzenet szövege és megjelenésének helye
Az üzenet szövege a következő: **Allow Company Portal to make and manage phone calls?** (Engedélyezi, hogy a Vállalati portál alkalmazás telefonhívásokat indítson és kezeljen?). Akkor jelenik meg, amikor a felhasználó első alkalommal bejelentkezik a Vállalati portál alkalmazásba, és megkezdi az eszköz regisztrálását.

### Az üzenet jelentése
Az üzenet arra kéri a felhasználót, hogy engedélyezze eszköze telefonszámának és IMEI-számának elküldését az Intune szolgáltatásba, és engedélyezze, hogy azok megjelenjenek a felügyeleti konzol Hardver lapján.

> [!NOTE]
> **A Munkahelyi portál alkalmazás soha nem indít telefonhívásokat, és nem is kezeli azokat.** Az üzenet szövegét a Google szabja meg, és nem módosítható.

A **Hardver** lap megnyitásához válassza a **Csoportok** > **Minden mobileszköz** > **Eszközök** lehetőséget. Jelölje ki a felhasználó eszközét, majd válassza a **Tulajdonságok megjelenítése** > **Hardver** lehetőséget.

### Ez történik, ha a felhasználó engedélyezi vagy nem engedélyezi a hozzáférést
Ha a felhasználó engedélyezi a hozzáférést, az eszköz telefonszáma és IMEI-száma megjelenik a felügyeleti konzol Hardver lapján.

Ha a felhasználó nem engedélyezi a hozzáférést, attól továbbra is használhatja a Vállalati portál alkalmazást, és regisztrálhatja az eszközeit, de azok telefonszáma és IMEI-száma nem jelenik meg a felügyeleti konzol Hardver lapján. Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését.

Ha a felhasználó engedélyezi a hozzáférést, de később megtagadja azt, az üzenet újból megjelenik, amikor a felhasználó a regisztrálást követően először bejelentkezik a Vállalati portál alkalmazásba.</br></br>Amennyiben a felhasználó később ismét engedélyezni szeretné a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Telefon** lapon teheti ezt meg.

### További információ biztosítása a felhasználónak
5. lépés a következőben: [Android-eszköz regisztrálása az Intune-ban](/Intune/EndUser/enroll-your-device-in-intune-android)

## Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)

### Az üzenet szövege és megjelenésének helye
Az üzenet szövege a következő: **Allow Company Portal to access photos, media, and files on your device?** (Engedélyezi a Vállalati portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?). Akkor jelenik meg, ha a felhasználó az **Adatok elküldése** elemre koppintva adatnaplókat küld a rendszergazdának.

### Az üzenet jelentése
Az üzenet arra kéri a felhasználót, hogy engedélyezze, hogy eszköze adatnaplókat írjon az eszköz SD-kártyájára, és engedélyezze, hogy a rendszer ezeket a naplókat USB-kábel segítségével más helyre másolja.   

> [!NOTE]
> **A Munkahelyi portál alkalmazás sohasem próbál hozzáférni a felhasználó fényképeihez, médiatartalmaihoz és fájljaihoz.** Az üzenet szövegét a Google szabja meg, és nem módosítható.

### Ez történik, ha a felhasználó engedélyezi vagy nem engedélyezi a hozzáférést
Ha a felhasználó engedélyezi a hozzáférést, a rendszer az SD-kártyára másolja a naplókat.

Ha a felhasználó nem engedélyezi a hozzáférést, akkor is elküldheti az adatnaplókat, ám azok nem másolhatók az SD-kártyára.

Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését. Ha a felhasználó engedélyezi a hozzáférést, de később megtagadja, az üzenet újból megjelenik, amikor a felhasználó a legközelebb megpróbálja elküldeni a naplókat. Amennyiben a felhasználó később ismét engedélyezni szeretné a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Tárterület** lapon teheti ezt meg.

### További információ biztosítása a felhasználónak
[Diagnosztikai adatok naplófájljainak elküldése e-mailben a rendszergazdának](/Intune/EndUser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)


### További információ
[Mit kell tudniuk a végfelhasználóknak az Intune használatáról?](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)



<!--HONumber=Jul16_HO1-->


