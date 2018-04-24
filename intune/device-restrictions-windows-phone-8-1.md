---
title: Eszközkorlátozásokra vonatkozó beállítások a Microsoft Intune-ban Windows Phone 8.1 esetén
titleSuffix: ''
description: Az Intune azon beállításainak ismertetése, amelyekkel szabályozhatók az eszközbeállítások, illetve a funkciók köre a Windows Phone 8.1 rendszerű eszközökön.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1bebb5915a7adeb13fd95b73587bca0171bebd83
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>A Windows Phone 8.1 eszközkorlátozásokra vonatkozó beállításai a Microsoft Intune-ban

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A cikk bemutatja a Microsoft Intune olyan eszközkorlátozásokra vonatkozó beállításait, melyek konfigurálhatók Windows Phone 8.1 rendszerű eszközökhöz.


## <a name="general"></a>Általános

-   **Kamera** – Engedélyezi vagy letiltja az eszköz kamerájának használatát.
-   **Másolás és beillesztés** – Engedélyezi vagy letiltja az eszközök másolási és beillesztési funkciójának használatát.
-   **Cserélhető tároló** – Cserélhető tárolók (például SD-kártyák) használatának engedélyezése az eszközön.
-   **Földrajzi hely** – Engedélyezi az eszköz számára a helyadatok használatát.
-   **Microsoft-fiók** – Engedélyezi vagy letiltja a felhasználó számára egy Microsoft-fiók összekapcsolását az eszközzel.
-   **Képernyőfelvétel** – A képernyőtartalom képfájlban történő rögzítésének engedélyezése a felhasználó számára.
-   **Diagnosztikai adatok beküldése** – Engedélyezése esetén az eszköz diagnosztikai adatokat küld a Microsoftnak.
-   **Egyéni e-mail fiókok szinkronizálása** – Nem Microsoft e-mail-fiókokhoz való kapcsolódás engedélyezése az eszköz számára.

## <a name="password"></a>Jelszó

-   **Jelszó** – Megköveteli a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez.
    -   **Megkövetelt jelszótípus** – Meghatározza a megkövetelt jelszótípust, például hogy a jelszó számokat és betűket, vagy csak számokat tartalmazhat.
    -   **Jelszó minimális hossza** – A jelszóban használandó karakterek minimális számát határozza meg.
    -   **Egyszerű jelszavak** – Engedélyezi az egyszerű jelszavak (mint például a „0000” vagy az „1234”) használatát.
    -   **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat** – Meghatározza, hogy a felhasználó hányszor adhat meg helytelen jelszót, mielőtt a rendszer törölné az eszközt.
    -   **Képernyőzárolás legfeljebb ennyi perc inaktivitás után** – Meghatározza, hogy az eszköznek mennyi ideig kell tétlennek lennie a képernyő automatikus zárolása előtt.
    -   **Jelszó érvényessége (napokban)** – Meghatározza, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát.
    -   **Korábbi jelszavak újbóli használatának tiltása** – Meghatározza, hogy a rendszer hány korábban használt jelszót jegyezzen meg.
-   **Titkosítás** – Kötelezővé teszi az adatok titkosítását a támogatott mobileszközökön.

## <a name="app-store"></a>Alkalmazásáruház

-   **Alkalmazásáruház** – Lehetővé teszi a felhasználók számára az alkalmazásáruház elérését az eszközről.

## <a name="restricted-apps"></a>Korlátozott alkalmazások

A korlátozott alkalmazások listájában a következő listák valamelyikét konfigurálhatja:

A **Tiltott alkalmazások** listája – Azokat a nem az Intune által kezelt alkalmazásokat tartalmazza, amelyek telepítése és futtatása nincs engedélyezve a felhasználók számára.
Az **Engedélyezett alkalmazások** listája – Azokat az alkalmazásokat tartalmazza, amelyek telepítése engedélyezett a felhasználók számára. Az Intune által kezelt alkalmazások automatikusan engedélyezettek.

A lista konfigurálásához kattintson a **Hozzáadás** gombra, adja meg a kívánt nevet, igény szerint az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Az alkalmazás áruházbeli URL-címének megadása

Ha meg szeretné adni egy alkalmazás URL-címét az engedélyezett vagy letiltott alkalmazások listájában, használja a következő formátumot:

A [Windows Phone Áruház](https://www.microsoft.com/store/apps/windows-phone) lapon keressen rá a használni kívánt alkalmazásra.

Nyissa meg az alkalmazás lapját, és másolja az URL-címet a vágólapra. Ezt a címet az engedélyezett és a tiltott alkalmazások listájában egyaránt használhatja URL-címként.

Például: Keressen rá az áruházban a Skype alkalmazásra. Az Ön által használt URL-cím a következő: **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>További beállítások

Az **Importálás** gombra kattintva feltöltheti a listát egy CSV-fájlból, mely a következő formátumú: <*alkalmazás URL-címe*>, <*alkalmazás neve*>, <<app publisher>>. Az **Exportálás** gombra kattintva pedig létrehozhat egy CSV-fájlt, amely ugyanebben a formátumban tartalmazza a korlátozott alkalmazások listáját.


## <a name="browser"></a>Böngésző

-   **Webböngésző** – Engedélyezi vagy letiltja az eszköz beépített webböngészőjét.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

-   **Wi-Fi** – Az eszköz Wi-Fi funkciójának engedélyezése vagy letiltása.
-   **Wi-Fi-alapú internetmegosztás** – Engedélyezi az eszköz Wi-Fi-alapú internetmegosztási funkciójának használatát.
-   **Automatikus csatlakozás Wi-Fi elérési pontokhoz** – Engedélyezi az eszközön az ingyenes Wi-Fi elérési pontokhoz történő automatikus csatlakozást és a vonatkozó használati feltételek automatikus elfogadását.
-   **Wi-Fi elérési pont jelentése** – Információt küld a Wi-Fi kapcsolatokról a közeli kapcsolatok felderítésének elősegítése érdekében.
-   **NFC** – Engedélyezi vagy letiltja azokat a műveleteket, amelyek kis hatótávolságú kommunikációt használnak az azt támogató eszközökön.
-   **Bluetooth** – Az eszköz Bluetooth funkciójának engedélyezése vagy letiltása.
