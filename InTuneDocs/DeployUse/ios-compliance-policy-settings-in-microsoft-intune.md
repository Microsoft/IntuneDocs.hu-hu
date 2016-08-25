---
# required metadata

title: Megfelelőségi szabályzat beállításai iOS-eszközökhöz | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Megfelelőségi szabályzat beállításai iOS-eszközökhöz a Microsoft Intune-ban

A jelen témakörben leírt szabályzati beállítások  iOS 6 vagy újabb verziójú futó eszközökre vonatkoznak.

Ha más platformokra vonatkozó információkat keres, válassza az alábbiak egyikét:
> [!div class="op_single_selector"]
- [Megfelelőségi szabályzat beállításai Android-eszközökhöz](android-compliance-policy-settings-in-microsoft-intune.md)
- [Megfelelőségi szabályzat beállításai Windows-eszközökhöz](windows-compliance-policy-settings-in-microsoft-intune.md)

## A rendszer biztonsági beállításai
### Jelszó
- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához:**    Ha azt szeretné, hogy a felhasználók kötelesek legyenek jelszót megadni az eszköz eléréséhez, válassza az **Igen** lehetőséget. A jelszót használó iOS-eszközöket titkosítja a rendszer.

- **Egyszerű jelszavak engedélyezése:**    Ha engedélyezni szeretné, hogy a felhasználók használhassanak olyan egyszerű jelszavakat, mint az **1234** vagy az **1111**, válassza az **Igen** lehetőséget.

-  **Jelszó minimális hossza:** meghatározza a felhasználók jelszavában szereplő számjegyek vagy karakterek minimális számát.
- **Megkövetelt jelszótípus:** Meghatározza, hogy a felhasználóknak **alfanumerikus** vagy **numerikus** jelszót kell-e létrehozniuk.

- **Karakterkészletek minimális száma:** Ha a **Megkövetelt jelszótípus** **alfanumerikus**, ez a beállítás határozza meg a jelszóban használandó karakterkészletek minimális számát. A négy karakterkészlet a következő:
  -   Kisbetűk
  -   Nagybetűk
  -   Szimbólumok
  -   Számok

  Ha nagyobb értékre állítja ezt a beállítást, a felhasználóknak összetettebb jelszavakat kell létrehozniuk.

  Az iOS-eszközök esetében ez a beállítás a jelszóban használandó különleges karakterek (például: **!**, **#**, **&amp;**) minimális számára utal.
- **Jelszó kérése ennyi perc inaktivitás után**: arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát.

- **Jelszó érvényessége (napokban):** Válassza ki, hány nap elteltével járjon le a felhasználó jelszava, ami után újat kell létrehoznia.

- **Korábbi jelszavak megjegyzése:** Ezt a beállítást a **Korábbi jelszavak újbóli használatának tiltása** beállítással használva korlátozhatja, hogy a felhasználó korábban már használt jelszavakat hozzon létre.

- **Korábbi jelszavak újbóli használatának tiltása:** Ha a **Korábbi jelszavak megjegyzése** beállítás be van jelölve, adja meg, hogy az utolsó hány korábbi jelszót ne lehessen ismét használni.

- **Jelszó kérése, amikor az eszköz visszatér inaktív állapotból:** Ezt a beállítást a **Jelszó kérése ennyi perc inaktivitás után** beállítással együtt kell használni. A rendszer megkéri a végfelhasználót egy jelszó beírására a **Jelszó kérése ennyi perc inaktivitás után** beállításban megadott ideig inaktív eszköz eléréséhez.

### E-mail profil
- **Csak az Intune által felügyelt e-mail fiók használható:** ha **Igen** értékre állítja a beállítást, az eszköznek az eszközre telepített megfelelő e-mail-fiókot kell használnia. Az eszköz a következő esetekben számít nem megfelelőnek:
  - Az e-mail-profilt ugyanarra a felhasználói csoportra kell telepíteni, amelyet a megfelelőségi szabályzat is céloz, ellenkező esetben a felhasználó eszköze nem megfelelőnek fog számítani.
  - Ha a felhasználó olyan e-mail-fiókot állított be az eszközön, amely egyezik az eszközre telepített Intune-e-mail-fiókkal, a rendszer nem megfelelőként jelenti az eszközt. Az Intune nem írhatja felül a felhasználó által létesített profilt, így nem kezelheti. A megfelelőség biztosítása érdekében a felhasználónak el kell távolítania a meglévő e-mail beállításokat, hogy az Intune telepíthesse a felügyelt levelezési profilt.


- **Az Intune-ban felügyelni kívánt levelezési profil:**
     Ha a **Csak az Intune által felügyelt e-mail fiók használható** beállítás be van jelölve, kattintson a **Kiválasztás** elemre az Intune levelezési profil kiválasztásához. A levelezési profilnak megtalálhatónak kell lennie az eszközön.

     A levelezési profilokról a [Hozzáférés engedélyezése a vállalati e-mailekhez a Microsoft Intune e-mail profiljaival](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) című témakörben talál további információt.

## Eszközállapot-beállítások

- **Az eszköz nem lehet függetlenített vagy feltört eszköz:** Ha bekapcsolja ezt a beállítást, a rendszer nem megfelelőként fogja értékelni a feltört eszközöket.

##  Eszköztulajdonságok
- **Az operációs rendszer szükséges minimális verziója:** Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként fog szerepelni.
Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ezt követően pedig hozzáférhet a vállalati erőforrásokhoz.

- **Maximálisan engedélyezett operációsrendszer-verzió:** Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb fut, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva, és a felhasználónak kapcsolatba kell lépnie az informatikai rendszergazdával. Az eszköz csak akkor használható a vállalati erőforrások eléréséhez, ha a szabályt úgy módosítják, hogy engedélyezze az operációs rendszer verzióját.


<!--HONumber=Jun16_HO2-->


