---
title: "Megfelelőségi szabályzat beállításai Android-eszközökhöz | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: e736d688032dd2ddee5be9edf2a33d5e7ba5257b
ms.openlocfilehash: dd3369cf59ea972f1ecc4953881ddbbede9a99c8


---


# Megfelelőségi szabályzat beállításai Android-eszközökhöz a Microsoft Intune-ban

A jelen témakörben leírt szabályzati beállítások az Android 4.0-s és újabb verzióival, illetve a Samsung KNOX 4.0-s és újabb verzióival futó eszközökre vonatkoznak.

Ha más platformokra vonatkozó információkat keres, válassza az alábbiak egyikét:
> [!div class="op_single_selector"]
- [Megfelelőségi szabályzat beállításai iOS-eszközökhöz](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Megfelelőségi szabályzat beállításai Windows-eszközökhöz](windows-compliance-policy-settings-in-microsoft-intune.md)

## A rendszer biztonsági beállításai
### Jelszó
- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához:** Ha azt szeretné, hogy a felhasználók kötelesek legyenek jelszót megadni az eszköz eléréséhez, válassza az **Igen** lehetőséget.

-  **Jelszó minimális hossza:** meghatározza a felhasználók jelszavában szereplő számjegyek vagy karakterek minimális számát.

- **Jelszó erőssége:** a beállítás bekapcsolása esetén konfigurálhatja az Android-eszközök jelszókövetelményeit. A következő lehetőségek közül választhat:
  -   **Alacsony biztonságú biometrikus**
  - **Kötelező**
  -   **Legalább számok**
  -   **Legalább betűk**
  -   **Legalább alfanumerikus karakterek**
  -   **Alfanumerikus karakterek és szimbólumok**

- **Jelszó kérése ennyi perc inaktivitás után:** arra a tétlenségi időre vonatkozik, amin belül a felhasználónak újra meg kell adnia a jelszavát.

- **Jelszó érvényessége (napokban):** Válassza ki, hány nap elteltével járjon le a felhasználó jelszava, ami után újat kell létrehoznia.

- **Korábbi jelszavak megjegyzése:** Ezt a beállítást a **Korábbi jelszavak újbóli használatának tiltása** beállítással használva korlátozhatja, hogy a felhasználó korábban már használt jelszavakat hozzon létre.

- **Korábbi jelszavak újbóli használatának tiltása:** Ha a **Korábbi jelszavak megjegyzése** beállítás be van jelölve, adja meg, hogy az utolsó hány korábbi jelszót ne lehessen ismét használni.

- **Jelszó kérése, amikor az eszköz visszatér inaktív állapotból:** Ezt a beállítást a **Jelszó kérése ennyi perc inaktivitás után** beállítással együtt kell használni. A rendszer jelszó beírását kéri a végfelhasználótól a **Jelszó kérése ennyi perc inaktivitás után** beállításban megadott ideig inaktív eszköz eléréséhez.

### Titkosítás
- **Titkosítás megkövetelése mobileszközön:** Állítsa ezt a beállítást **Igen** értékre, ha szeretné előírni, hogy az eszközök csak titkosítás használata esetén csatlakozhassanak az erőforrásokhoz. Az eszközök **A mobileszközök zárolásának feloldásához jelszó szükséges** beállítás konfigurálásával titkosíthatók.

## Eszközállapot-beállítások

- **Az eszköz nem lehet függetlenített vagy feltört eszköz:** Ha bekapcsolja ezt a beállítást, a rendszer nem megfelelőként fogja értékelni a feltört eszközöket.

## Eszköztulajdonság-beállítások
- **Az operációs rendszer szükséges minimális verziója:** Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként fog szerepelni.
  Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ezt követően pedig hozzáférhet a vállalati erőforrásokhoz.

- **Maximálisan engedélyezett operációsrendszer-verzió:** Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb fut, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva, és a felhasználónak kapcsolatba kell lépnie az informatikai rendszergazdával. Az eszköz csak akkor használható a vállalati erőforrások eléréséhez, ha a szabályt úgy módosítják, hogy engedélyezze az operációs rendszer verzióját.



<!--HONumber=Jul16_HO1-->


