---
title: Eszközkorlátozási beállítások Android rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Megtekintheti az összes olyan androidos eszközbeállítást, amelyet vezérelhet és korlátozhat a Microsoft Intune-ban. Ezekkel a beállításokkal vezérelheti a jelszavakat, a Google Playhez való hozzáférést, az alkalmazások engedélyezését vagy letiltását, a böngészőbeállításokat, az alkalmazások blokkolását, a Google-felhőbe való biztonsági mentéseket, valamint az üzenetkezelés, a hang, az adatroaming, a Wi-Fi és a Bluetooth beállításait.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1eac5b7959232fe747dd8ba87546269ff7a95af
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730775"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Android-és Samsung Knox standard-eszközök korlátozási beállításainak listája az Intune-ban

A cikk bemutatja a Microsoft Intune összes olyan eszközkorlátozásokra vonatkozó beállítását, melyek konfigurálhatók Android rendszerű eszközökhöz.

>[!TIP]
>Ha a kívánt beállítások nem elérhetőek, lehet, hogy konfigurálni tudja az eszközöket egy [egyéni profil](../custom-settings-android.md) használatával.

## <a name="general"></a>Általános

- **Kamera**: A kamera elérésének megakadályozásához válassza a **Letiltás** lehetőséget. A **nincs konfigurálva** beállítás lehetővé teszi az eszköz kamerájának elérését.
- **Másolás és beillesztés (csak Samsung Knox esetén)** : A másolás és beillesztés megtiltásához válassza a **Letiltás** lehetőséget. A **nincs konfigurálva** beállítás lehetővé teszi a másolási és beillesztési függvények használatát az eszközön.
- **Vágólap megosztása az alkalmazások között (csak Samsung Knox esetén)** : A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a vágólapon keresztül másolja és illessze be az alkalmazások között. **Nincs konfigurálva** , lehetővé teszi az alkalmazások közötti másolást és beillesztést a vágólap használatával.
- **Diagnosztikai adatok beküldése (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget, ha le szeretné állítani, hogy a felhasználó diagnosztikai adatok elküldését az eszközről. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára az adatküldést.
- **Törlés (csak Samsung Knox esetén)** : Lehetővé teszi a felhasználó számára, hogy [törlési](../remote-actions/devices-wipe.md) műveletet futtasson az eszközön.
- Földrajzi hely **(csak Samsung Knox)** : A **Letiltás** elem kiválasztásával letilthatja az eszközt a hely adatainak használatával. A **nincs konfigurálva** beállítás lehetővé teszi az eszköz számára a helyadatok használatát.
- Kikapcsolás **(csak Samsung Knox esetén)** : A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználó kikapcsolja az eszközt. Ha ez a beállítás le van tiltva, az eszköz nem állítható be, és nem működik a **sikertelen bejelentkezések száma** . A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó kikapcsolja az eszközt.
- **Képernyőfelvétel (csak Samsung Knox esetén)** : A képernyőképek megtiltásához válassza a **Letiltás** lehetőséget. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó képként rögzítse a képernyőn látható tartalmat.
- **Hangsegéd (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget az S Voice szolgáltatás letiltásához. A **nincs konfigurálva** beállítás lehetővé teszi az S hang szolgáltatás és az alkalmazás használatát az eszközön. Ez a beállítás nem vonatkozik a Bixby vagy a hangvezérelt Segédre olyan kisegítő lehetőségek esetén, amelyek felolvassák a képernyő tartalmát.
- **YouTube (csak Samsung Knox esetén)** : A **Letiltás** gombra kattintva megakadályozhatja, hogy a felhasználók a YouTube-alkalmazást használják. A **nincs konfigurálva** beállítás lehetővé teszi a YouTube alkalmazás használatát az eszközön.
- **Megosztott eszközök (csak Samsung Knox esetén)** : Felügyelt Samsung Knox standard-eszköz konfigurálása megosztottként. Ha az **Engedélyezés**értékre van állítva, a végfelhasználók Azure ad-beli hitelesítő adataikkal jelentkezhetnek be és ki az eszközön. Az eszköz felügyelt marad, függetlenül attól, hogy használatban van-e vagy sem.</br>SCEP-tanúsítvány profil használata esetén ez a funkció lehetővé teszi, hogy a végfelhasználók ugyanazzal az alkalmazásokkal közösen használják az eszközt az összes felhasználó számára. Azonban minden felhasználónak saját SCEP felhasználói tanúsítványa van. A felhasználói kijelentkezéskor az összes alkalmazásadat törlődik. Ez a szolgáltatás csak az üzletági alkalmazásokra érvényes. </br>A **nincs konfigurálva beállítás** megakadályozza, hogy a végfelhasználók az Azure ad-beli hitelesítő adataik használatával bejelentkezzenek az eszközön lévő céges portál alkalmazásba.
- **Dátum-és időmódosítások letiltása (Samsung Knox)** : A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználó módosítsa a dátum-és időbeállításokat az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára a dátum-és időbeállítások módosítását.

## <a name="password"></a>Windows 10

- **Jelszó**: **Kérje** meg a végfelhasználót, hogy adjon meg egy jelszót az eszköz eléréséhez. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználók jelszó megadása nélkül férhessenek hozzá az eszközhöz.

    > [!NOTE]
    > A Samsung Knox-eszközök automatikusan megkövetelnek egy 4 számjegyű PIN-kódot az MDM-regisztráció során. Előfordulhat, hogy a natív Android-eszközök automatikusan PIN-kódot igényelnek, hogy megfeleljenek a feltételes hozzáférésnek.

- **Jelszó minimális hossza**: Adja meg a jelszó minimális hosszát, amelyet a felhasználónak meg kell adnia (4 és 16 karakter között).
- **A képernyőfelvételek legfeljebb ennyi perc inaktivitás**után: Adja meg az eszközön a képernyő zárolása előtt legfeljebb ennyi perc inaktivitás engedélyezett számát. Az eszközön a végfelhasználó nem adhat meg a profilban konfigurált időnél nagyobb értéket. A végfelhasználó kisebb értéket azonban megadhat. Ha például a profilban 15 perc van megadva, a végfelhasználó beállíthat 5 percet. 30 perces értéket azonban már nem adhat meg. 
- **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg, hogy hány sikertelen bejelentkezés után kerüljön sor az eszköz törlésére.
- **Jelszó érvényessége (napokban)** : Adja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát.
- **Szükséges jelszó típusa**: Adja meg a jelszó bonyolultsági szintjét, valamint azt, hogy használható-e biometrikus eszköz. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Legalább számok**
  - **Komplex numerikus**: Ismétlődő vagy egymást követő számok (például "1111" vagy "1234") nem engedélyezettek. <sup>1</sup>
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Megakadályozza, hogy a végfelhasználó a korábban használt jelszót hozzon létre.
- **Ujjlenyomat feloldása (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget, hogy ne használjon ujjlenyomatot az eszköz zárolásának feloldásához. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó számára az eszközzárolás ujjlenyomattal történő használatával.
- **Smart Lock és más megbízhatósági ügynökök**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy Smart lock vagy más megbízhatósági ügynökök módosítsák a zárolási képernyő beállításait (Samsung Knox standard 5.0 +). Ez a telefonos funkció – más néven megbízhatósági ügynök – lehetővé teszi az eszköz zárolási képernyőjének jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van. Ez a funkció például akkor használható, ha az eszköz egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy ha egy NFC-címkéhez van kapcsolva. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.
- **Titkosítás**: Válassza a **szükséges** lehetőséget, hogy az eszközön lévő fájlok titkosítva legyenek. Nem minden eszköz támogatja a titkosítást. A funkció használatához a következőket is használhatja: 
  1. **Jelszó** megadása **kötelező**.
  2. Adja meg a **kötelező jelszó típusát** **legalább numerikus**értékre.
  3. Állítsa be a **jelszó minimális hosszát** legalább 4 értékre a beállítás megfelelőségének megfelelő jelentéséhez.

  > [!NOTE]
  > Ha kényszerítve van egy titkosítási szabályzat, a Samsung Knox-eszközökön a felhasználónak be kell állítania egy 6 karakterből álló összetett jelszót eszközjelszóként.

<sup>1</sup> a beállítás eszközökhöz rendelése előtt frissítse a céges portál alkalmazást az eszközök legújabb verziójára.

Ha a **kötelező jelszó típust** a **numerikus összetett**értékre állítja, majd hozzárendeli egy olyan eszközhöz, amely az Android 5,0-nál korábbi verzióját futtatja, akkor a következő viselkedés vonatkozik rá:

- Ha a Céges portál alkalmazás a 1704-nál korábbi verziót futtat, akkor a rendszer nem alkalmaz PIN-kódot az eszközön, és egy hibaüzenet jelenik meg a Azure Portal.
- Ha a Céges portál alkalmazás 1704-es vagy későbbi verzióját futtatja, csak egyszerű PIN-kód alkalmazható. Az Android 5,0-nál korábbi verziói nem támogatják ezt a beállítást. Nem jelenik meg hiba a Azure Portalban.

## <a name="google-play-store"></a>Google Play Áruház

- **Google Play áruház (csak Samsung Knox esetén)** : A **blokkolás** gombra kattintva megakadályozhatja, hogy a felhasználók a Google Play áruházat használják. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára a Google Play áruház elérését az eszközön.

## <a name="restricted-apps"></a>Korlátozott alkalmazások

Ezekkel a beállításokkal engedélyezheti vagy megakadályozhatja az adott alkalmazások használatát az eszközön. Ez a funkció Android-és Samsung Knox standard-eszközökön támogatott:

- **Tiltott alkalmazások**: Az Intune által nem felügyelt alkalmazások listája, amelyeket nem kíván telepíteni az eszközre. Ha egy felhasználó a listából telepít egy alkalmazást, az Intune értesítést kap.
- **Jóváhagyott alkalmazások**: Azoknak az alkalmazásoknak a listája, amelyeket a felhasználók telepíthetnek. A megfelelőség érdekében a felhasználók nem telepíthetnek más alkalmazásokat. Az Intune által kezelt alkalmazások automatikusan engedélyezettek.

Ha alkalmazást szeretne hozzáadni a listához, a következőket teheti:

- **Adja hozzá** a kívánt alkalmazás Google Play áruház URL-címét. Például az Androidhoz készült Microsoft Távoli asztal alkalmazás hozzáadásához írja be a következőt: `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Az alkalmazás URL-címének megkereséséhez nyissa meg a [Google Play áruházat](https://play.google.com/store/apps), és keressen rá az alkalmazásra. Keressen például a `Microsoft Remote Desktop Play Store` vagy `Microsoft Planner`a kifejezésre. Válassza ki az alkalmazást, és másolja az URL-címet.
- Importáljon egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a <*alkalmazás URL-címét*>, <*alkalmazás neve*>, <*app Publisher*> formátumban. Vagy **exportáljon** egy meglévő listát, amely tartalmazza a korlátozott alkalmazások listáját ugyanabban a formátumban.

> [!IMPORTANT]
> A korlátozott alkalmazás-beállításokat használó eszközöket felhasználói csoportokhoz kell rendelni.

## <a name="browser"></a>Browser

- **Webböngésző (csak Samsung Knox esetén)** : A **Letiltás** elem kiválasztásával megakadályozhatja, hogy az alapértelmezett böngésző ne legyen használatban az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi az eszköz alapértelmezett webböngészőjének használatát.
- **Automatikus kitöltés (csak Samsung Knox esetén)** : A **Letiltás** elemre kattintva megakadályozhatja a szöveg automatikus kitöltését a böngészőben. A **nincs konfigurálva** beállítás lehetővé teszi a webböngésző automatikus kitöltés funkciójának használatát.
- **Cookie-k (csak Samsung Knox esetén)** : Válassza ki, hogyan szeretné kezelni a cookie-kat az eszköz webhelyeiről. A választható lehetőségek:
  - Allow
  - Az összes cookie letiltása
  - Cookie-k engedélyezése a felkeresett webhelyekről
  - Cookie-k engedélyezése a jelenlegi webhelyről
- **JavaScript (csak Samsung Knox esetén)** : A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a webböngésző Java-parancsfájlokat futtasson. A **nincs konfigurálva** beállítás lehetővé teszi, hogy az eszköz webböngészője Java-parancsfájlokat futtasson.
- **Előugró ablakok (csak Samsung Knox esetén)** : Kattintson a **Letiltás** elemre a böngészőben megjelenő előugró ablakok elkerüléséhez. A **nincs konfigurálva** beállítás lehetővé teszi az előugró ablakok használatát a böngészőben.

## <a name="allow-or-block-apps"></a>Alkalmazások engedélyezése és letiltása

Ezekkel a beállításokkal engedélyezheti, letilthatja vagy elrejtheti az egyes alkalmazásokat a Samsung Knox standard-eszközökön. A rejtett alkalmazások nem nyithatók meg és nem futtathatók a felhasználó számára.

A választható lehetőségek:

- **Telepíthető alkalmazások (csak Samsung Knox Standard esetén)**
- **Nem indítható alkalmazások (csak Samsung Knox Standard esetén)**
- **Felhasználó elől elrejtett alkalmazások (csak Samsung Knox Standard esetén)**

Az egyes beállításokhoz adja hozzá az alkalmazások listáját. A választható lehetőségek:

- **Alkalmazások hozzáadása csomag neve szerint**: Elsősorban üzletági alkalmazások esetében használatos. Adja meg az alkalmazás nevét, majd az alkalmazáscsomag nevét.
- **Alkalmazások hozzáadása URL-cím szerint**: Adja meg az alkalmazás nevét és URL-címét a Google Play áruházban.
- **Áruházbeli alkalmazás hozzáadása**: Válasszon ki egy alkalmazást az Intune-ban kezelt alkalmazások meglévő listájából.

## <a name="cloud-and-storage"></a>Felhő és tárolás

- **Google Backup (csak Samsung Knox esetén)** : A **Letiltás** elemre kattintva megakadályozhatja, hogy az eszköz szinkronizáljon a Google Backup szolgáltatással. A **nincs konfigurálva** beállítás lehetővé teszi a Google Backup használatát.
- **Google-fiók automatikus szinkronizálása (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget a Google-fiók automatikus szinkronizálási funkciójának megtiltásához az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a Google-fiók beállításainak automatikus szinkronizálását.
- **Cserélhető tárolók (csak Samsung Knox esetén)** : A **Letiltás** elem kiválasztásával megakadályozhatja, hogy az eszköz cserélhető tárolót használjon. A **nincs konfigurálva** beállítás lehetővé teszi, hogy az eszköz cserélhető tárolót használjon, például egy SD-kártyát.
- **A Storage-kártyák titkosítása (csak Samsung Knox esetén)** : A **kötelező** kikényszeríti a memóriakártyák titkosítását. A **nincs konfigurálva** beállítás lehetővé teszi a titkosítatlan tárolóhelyek használatát. Nem minden eszköz támogatja a memóriakártyák titkosítását. A megerősítéshez forduljon az eszköz gyártójához.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

- **Adatroaming (csak Samsung Knox esetén)** : A **Letiltás** elemre kattintva megakadályozhatja az adatroamingot a mobil hálózaton. **Nincs konfigurálva** engedélyezi az adatroaming használatát, ha az eszköz mobilhálózati.
- **SMS-és MMS-üzenetkezelés (csak Samsung Knox esetén)** : A **Letiltás** elemre kattintva megakadályozhatja a szöveges üzenetküldést az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi az SMS-és MMS-üzenetek használatát az eszközön.
- **Hangtárcsázás (csak Samsung Knox esetén)** : A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a hangtárcsázás funkciót használják az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a hangtárcsázást az eszközön.
- **Hangroaming (csak Samsung Knox esetén)** : A **Letiltás** elemre kattintva megakadályozhatja a hangroaming használatát a mobil hálózaton. A **nincs konfigurálva** beállítás lehetővé teszi a hangroaming használatát, ha az eszköz mobil hálózaton van.
- **Bluetooth (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget a Bluetooth eszközön való használatának megakadályozásához. A **nincs konfigurálva** beállítás engedélyezi a Bluetooth használatát az eszközön.
- **NFC (csak Samsung Knox esetén)** : A kis hatótávolságú kommunikáció (NFC) technológiájának leállításához válassza a **Letiltás** lehetőséget. A **nincs konfigurálva** beállítás lehetővé teszi a kis hatótávolságú kommunikációt használó műveletek használatát a támogatott eszközökön.
- **Wi-Fi (csak Samsung Knox esetén)** : Válassza a **Letiltás** lehetőséget, hogy megakadályozza a Wi-Fi használatát az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi az eszköz Wi-Fi funkcióinak használatát.
- **Wi-Fi-kötés (csak Samsung Knox esetén)** : A **blokkolás** gombra kattintva megakadályozhatja, hogy a Wi-Fi megkötést használjon az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a Wi-Fi-kötés használatát az eszközön.

## <a name="kiosk"></a>Kioszkmód

A kioszkmód csak a Samsung Knox Standard eszközökre, és csak az Intune-nal felügyelt alkalmazásokra vonatkozik.

- Adja meg azokat az alkalmazásokat, amelyeket futtatni szeretne, amikor az eszköz kioszk módban van. A teljes képernyős módban csak a felvenni kívánt alkalmazások futnak; a nem hozzáadott alkalmazások nem futnak. Az előre telepített böngészők nem futtathatók alkalmazásként, ha az eszköz kioszk módban van. Ha böngészőre van szüksége, fontolja meg a [Felügyelt böngésző](../apps/app-configuration-managed-browser.md) használatát.

  Az alkalmazás beállításai:

  - **Alkalmazások hozzáadása csomag neve szerint**: Elsősorban üzletági alkalmazások esetében használatos. Adja meg az alkalmazás nevét, majd az alkalmazáscsomag nevét.
  - **Alkalmazások hozzáadása URL-cím szerint**: Adja meg az alkalmazás nevét és URL-címét a Google Play áruházban.
  - **Áruházbeli alkalmazás hozzáadása**: Válasszon ki egy alkalmazást az Intune-ban kezelt alkalmazások meglévő listájából.

- **Képernyő alvó gombja**: Kattintson a **Letiltás** gombra a képernyő alvó állapotának megelőzésére vagy elrejtéséhez. A **nincs konfigurálva** beállítás engedélyezi a képernyő alvó állapotba lépését az eszközön.
- **Hangerő gombok**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználó állítsa be a kötetet a hangerő-szabályozó gombok letiltásával. A **nincs konfigurálva** beállítás lehetővé teszi a hangerő gomb használatát az eszközön.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](../device-profile-monitor.md).

Az [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) és a [Windows 10 rendszerű](kiosk-settings.md) eszközökhöz kioszk-profilokat is létrehozhat.
