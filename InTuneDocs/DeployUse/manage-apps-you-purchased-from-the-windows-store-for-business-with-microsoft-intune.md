---
title: "A Vállalati Windows Áruházban vásárolt alkalmazások kezelése | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: b6e2f0ec13caa9616b72a2fa225e77fe43a4755c


---

# A Vállalati Windows Áruházban vásárolt alkalmazások kezelése a Microsoft Intune-nal
A [Vállalati Windows Áruház](https://www.microsoft.com/business-store) az a hely, ahol alkalmazásokat vásárolhat a szervezete számára egyenként vagy nagyobb mennyiségben. Ha összekapcsolja az áruházat a Microsoft Intune-nal, a mennyiségi programban vásárolt alkalmazásokat az Intune-konzolról kezelheti, például:
* Szinkronizálhatja az áruházban vásárolt alkalmazások listáját az Intune-nal.
* A szinkronizált alkalmazások megjelennek az Intune felügyeleti konzolon, és a többi alkalmazáshoz hasonlóan telepítheti őket.
* Az Intune felügyeleti konzolon nyomon követheti, hogy hány licenc érhető el, és hány van használatban.
* Ha nincs elegendő elérhető licenc, az Intune letiltja az alkalmazások központi telepítését és telepítését.

## Előkészületek
Mielőtt elkezdi a Vállalati Windows Áruházból származó alkalmazások szinkronizálását és telepítését, tekintse át a következő információkat:
* Az Intune-t kell beállítania mobileszköz-kezelő szolgáltatóként a szervezetben. További tudnivalók: [Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](get-ready-to-enroll-devices-in-microsoft-intune.md).
* Rendelkeznie kell fiókkal a Vállalati Windows Áruházban.
* Miután összekapcsolta a Vállalati Windows Áruház-fiókját az Intune-nal, később nem választhat hozzá másik fiókot.
* Az áruházból beszerzett alkalmazások nem vehetők fel és nem törölhetők manuálisan az Intune-ban. Az alkalmazások csak a Vállalati Windows Áruházzal szinkronizálhatók.
* Az Intune csak a Vállalati Windows Áruházban vásárolt, online licenccel rendelkező alkalmazásokat szinkronizálja.
* Az eszközök akkor használhatják ezt a funkciót, ha csatlakoztak az Active Directory-tartományhoz vagy a munkahelyhez.
* A regisztrált eszközöknek a Windows 10 1511-es verzióját kell használniuk.

## A Vállalati Windows Áruház-fiók összekapcsolása az Intune-nal
Mielőtt engedélyezné a szinkronizálást az Intune-konzolon, konfigurálnia kell az áruházbeli fiókját az Intune használatára felügyeleti eszközként:
1. Ügyeljen arra, hogy a Vállalati Áruházba való bejelentkezéshez ugyanazt a bérlőt használja, mint az Intune-ba való bejelentkezéshez.
2. A Vállalati Áruházban válassza a **Beállítások** > **Felügyeleti eszközök** lehetőséget.
3. A Felügyeleti eszközök lapon válassza a **Felügyeleti eszköz hozzáadása** lehetőséget, és adja meg a Microsoft Intune-t.

Most már folytathatja a műveletet, és beállíthatja a szinkronizálást az Intune-konzolon.

## A szinkronizálás konfigurálása

1. A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Felügyelet** elemre.
2. A **Felügyelet** munkaterületen bontsa ki a **Mobileszköz-kezelés** elemet, majd kattintson a **Vállalati Áruház** elemre.
3. A **Vállalati Windows Áruház** lapon hajtsa végre a következő műveletet:
* Ha még nem tette meg, kattintson a Vállalati Windows Áruház regisztrálási hivatkozására.
* Miután regisztrálta magát, kattintson a **Szinkronizálás konfigurálása** elemre.
4. **A Vállalati Windows Áruházzal való alkalmazásszinkronizálás konfigurálása** párbeszédpanelen válassza a **Vállalati Windows Áruházzal való szinkronizálás engedélyezése** lehetőséget.
5. A **Nyelv** legördülő listán válassza ki azt a nyelvet, amelyet a Vállalati Windows Áruházból származó alkalmazásoknak az Intune-konzolon való megjelenítéséhez kíván használni. Az alkalmazások a végfelhasználó nyelvén lesznek telepítve (ha ez elérhető), függetlenül a megjelenítéshez választott nyelvtől.
6. Kattintson az **OK**gombra.

## Az alkalmazások szinkronizálása

1. A **Vállalati Windows Áruház** lapon kattintson a **Szinkronizálás** elemre az áruházban vásárolt alkalmazásoknak az Intune-nal való szinkronizálásához.
2. Az **Alkalmazások** munkaterületen kattintson a **Felügyelt szoftver** > **Licencelt szoftverek** elemre az elérhető alkalmazások megtekintéséhez és a megvásárolt alkalmazások helyes importálásának ellenőrzéséhez.
Az ebben a csomópontban található alkalmazásoknál megjelenik az Ön tulajdonában lévő összes licenc száma, valamint az elérhető licencek száma.

## Alkalmazások telepítése

Az Áruházból származó alkalmazásokat ugyanúgy telepítheti, mint a többi Intune-alkalmazást. További információk: [Alkalmazások telepítése a Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md).
A Vállalati Windows Áruházból származó alkalmazások központi telepítésekor az alkalmazást telepítő minden felhasználóhoz meg kell adnia egy-egy licencet. Ha felhasználja egy telepített alkalmazás minden elérhető licencét, már nem telepíthet több példányt, és a végre kell hajtania a következő műveletek valamelyikét:
* Távolítsa el az alkalmazást néhány eszközről.
* Csökkentse az aktuális telepítés hatókörét annyi felhasználóra, ahány licenccel rendelkezik.
* Vásárolja meg az alkalmazás további példányait a Vállalati Windows Áruházban.


### További információ
[Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md)





<!--HONumber=Jun16_HO4-->


