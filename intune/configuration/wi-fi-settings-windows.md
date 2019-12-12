---
title: Wi-Fi-beállítások Windows 10-es eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Wi-Fi-konfigurációs profil hozzáadása vagy létrehozása a Wi-Fi-beállítások használatával Windows 10 és újabb rendszerű eszközökön a Microsoft Intune-ban. Konfigurálhat alapszintű vagy nagyvállalati szintű beállításokat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68601d8ccf06cebf668c75857d23536e2c9e6553
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503519"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Wi-Fi-beállítások hozzáadása Windows 10 és újabb rendszerű eszközökhöz az Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti a Windows 10-es vagy újabb eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, az előmegosztott kulcsok használatát és egyebeket.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic-profile"></a>Alapszintű profil

- **Wi-Fi típusa**: válassza az **Alapszintű** lehetőséget. 

- **Wi-Fi neve (SSID)** : A szolgáltatáskészlet-azonosító rövidítése. Ez az érték a valódi neve a vezeték nélküli hálózatnak, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **kapcsolatnevet** látják, amikor kiválasztják a kapcsolatot.

- **Kapcsolat neve**: Adja meg a Wi-Fi-kapcsolat felhasználóbarát nevét. Az ide beírt szöveg a felhasználók számára megjelenő név, amikor a rendelkezésre álló kapcsolatokat böngészik az eszközeiken.

- **Hatótávolságon belül automatikus csatlakozás**: Ha **Igen** értékre van állítva, akkor az eszközök automatikusan csatlakoznak, amikor ennek a hálózatnak a hatótávolságán belül vannak. Ha a beállítás **Nem**, akkor az eszközök nem csatlakoznak automatikusan.

  - **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz**: Ha az eszközök egy előnyben részesített hálózat hatókörében vannak, akkor **Igen** beállítás mellett azt fogják használni. Válassza a **Nem** beállítást, hogy az ebben a konfigurációs profilban lévő Wi-Fi-hálózatot használják.

    Tegyük fel, hogy létrehozott egy **ContosoCorp** nevű Wi-Fi-hálózatot, és a **ContosoCorp** hálózatot használja ebben a konfigurációs profilban. Elérhető távolságban van egy **ContosoGuest** nevű Wi-Fi-hálózat is. Azt szeretné, hogy ha céges eszközei hatókörön belül vannak, automatikusan a **ContosoCorphoz** csatlakozzanak. Ebben az esetben állítsa a **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz** tulajdonságot **Nem** értékre.

  - **Csatlakozás ehhez a hálózathoz akkor is, ha nem küld SSID-t**: Válassza az **Igen** beállítást a konfigurációs profilhoz, hogy akkor is automatikusan csatlakozzon a hálózatához, amikor a hálózat rejtett (tehát nem küldi szét nyilvánosan az SSID-ját). Válassza a **Nem** beállítást, ha nem szeretné, hogy ez a konfigurációs profil a rejtett hálózathoz csatlakozzon.

- **Mért kapcsolathoz megadott korlát**: A rendszergazdák kiválaszthatják, hogy történjen a hálózati forgalom mérése. Alkalmazások ezt követően ennek a beállításnak az alapján módosíthatják a hálózati forgalommal kapcsolatos viselkedésüket. A választható lehetőségek:

  - **Nem korlátozott**: alapértelmezett. A rendszer nem méri a kapcsolatot, és nincs korlátozva a forgalom.
  - **Rögzített**: Ezt a lehetőséget használja, ha a hálózathoz rögzített hálózati forgalomkorlát van beállítva. A korlát elérése után a hálózati hozzáférés le van tiltva.
  - **Változó**: Ezt a lehetőséget használja, ha a hálózati forgalom számlázása bájtonként (bájtonkénti költség) történik.

- **Vezeték nélküli biztonság típusa**: Adja meg a hálózatán az eszközök hitelesítésére használt biztonsági protokollt. Az alábbi lehetőségek állnak rendelkezésére:
  - **Nyitott (nincs hitelesítés)** : Csak akkor válassza ezt a lehetőséget, ha a hálózat nem védett.
  - **WPA/WPA2 (személyes)** : Egy biztonságosabb beállítás, amelyet gyakran hasznának Wi-Fi-csatlakozáshoz. A további biztonság érdekében előre megosztott kulcsot vagy hálózati kulcsot is megadhat.

    - **Előre megosztott kulcs** (PSK): nem kötelező. Akkor jelenik meg, ha a **WPA/WPA2 (személyes)** biztonsági típust választja. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként. 8–64 karakter közötti hosszúságú sztringet adjon meg. Ha a jelszó vagy a hálózati kulcs 64 karakterből áll, akkor hexadecimális karakteret adjon meg.

      > [!NOTE]
      > A Wi-Fi-profil mentésekor a PSK megadott értéke nem jelenik meg biztonsági okokból. Az előre megosztott kulcs vízjele továbbra is **Nincs konfigurálva** értéket mutat annak ellenére, hogy a PSK el van mentve a profilban. A PSK módosításához adjon meg egy új kulcsot, majd mentse a profilt. Ha a PSK mentésekor szerkeszti a szabályzatot, a PSK-t pedig üresen hagyja, továbbra is a meglévő PSK lesz használatban.
      > [!IMPORTANT]
      > A PSK ugyanaz, mint az összes olyan eszközön, amelyre a profilt célozza. Ha a kulcs biztonsága sérül, bármely eszköz használhatja a Wi-Fi hálózathoz való csatlakozáshoz. A jogosulatlan hozzáférés elkerüléséhez tartsa biztonságos PSKs.

- **Vállalati proxybeállítások**: Válassza ki a vállalatán belül használni kívánt proxybeállításokat. A választható lehetőségek:
  - **Nincs**: Semmilyen proxybeállítás nincs konfigurálva.
  - **Manuálisan konfigurált**: Adja meg a **proxykiszolgáló IP-címét** és **portszámát**.
  - **Automatikusan konfigurált**: Adja meg egy proxy automatikus konfigurációs (PAC) szkriptjének URL-címét. Például írja be a következőt: `http://proxy.contoso.com/proxy.pac`.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="enterprise-profile"></a>Vállalati profil

- **Wi-Fi típusa**: Válassza a **Vállalati** elemet.

- **Wi-Fi neve (SSID)** : A szolgáltatáskészlet-azonosító rövidítése. Ez az érték a valódi neve a vezeték nélküli hálózatnak, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **kapcsolatnevet** látják, amikor kiválasztják a kapcsolatot.

- **Kapcsolat neve**: Adja meg a Wi-Fi-kapcsolat felhasználóbarát nevét. Az ide beírt szöveg a felhasználók számára megjelenő név, amikor a rendelkezésre álló kapcsolatokat böngészik az eszközeiken.

- **Hatótávolságon belül automatikus csatlakozás**: Ha **Igen** értékre van állítva, akkor az eszközök automatikusan csatlakoznak, amikor ennek a hálózatnak a hatótávolságán belül vannak. Ha a beállítás **Nem**, akkor az eszközök nem csatlakoznak automatikusan.
  - **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz**: Ha az eszközök egy előnyben részesített hálózat hatókörében vannak, akkor **Igen** beállítás mellett azt fogják használni. Válassza a **Nem** beállítást, hogy az ebben a konfigurációs profilban lévő Wi-Fi-hálózatot használják.

    Tegyük fel, hogy létrehozott egy **ContosoCorp** nevű Wi-Fi-hálózatot, és a **ContosoCorp** hálózatot használja ebben a konfigurációs profilban. Elérhető távolságban van egy **ContosoGuest** nevű Wi-Fi-hálózat is. Azt szeretné, hogy ha céges eszközei hatókörön belül vannak, automatikusan a **ContosoCorphoz** csatlakozzanak. Ebben az esetben állítsa a **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz** tulajdonságot **Nem** értékre.

  - **Csatlakozás ehhez a hálózathoz akkor is, ha nem küld SSID-t**: Válassza az **Igen** beállítást a konfigurációs profilhoz, hogy akkor is automatikusan csatlakozzon a hálózatához, amikor a hálózat rejtett (tehát nem küldi szét nyilvánosan az SSID-ját). Válassza a **Nem** beállítást, ha nem szeretné, hogy ez a konfigurációs profil a rejtett hálózathoz csatlakozzon.

- **Mért kapcsolathoz megadott korlát**: A rendszergazdák kiválaszthatják, hogy történjen a hálózati forgalom mérése. Alkalmazások ezt követően ennek a beállításnak az alapján módosíthatják a hálózati forgalommal kapcsolatos viselkedésüket. A választható lehetőségek:

  - **Nem korlátozott**: alapértelmezett. A rendszer nem méri a kapcsolatot, és nincs korlátozva a forgalom.
  - **Rögzített**: Ezt a lehetőséget használja, ha a hálózathoz rögzített hálózati forgalomkorlát van beállítva. A korlát elérése után a hálózati hozzáférés le van tiltva.
  - **Változó**: Ezt a lehetőséget használja, ha a hálózati forgalom számlázása bájtonként történik.

- **Egyszeri bejelentkezés (SSO)** : Lehetővé teszi az egyszeri bejelentkezés (SSO) konfigurálását. Ekkor ugyanazok a hitelesítő adatok szolgálnak a számítógépre és a Wi-Fi-hálózatba való bejelentkezésre. Az alábbi lehetőségek állnak rendelkezésére:
  - **Letiltás** Letiltja az SSO viselkedést. A felhasználónak külön kell hitelesítenie magát a hálózaton.
  - **Engedélyezés mielőtt a felhasználó bejelentkezik az eszközre**: Az SSO használata a hálózaton való hitelesítésre közvetlenül a felhasználói bejelentkezés előtt.
  - **Engedélyezés miután a felhasználó bejelentkezik az eszközre**: Az SSO használata a hálózaton való hitelesítésre közvetlenül azután, hogy a felhasználói bejelentkezés befejeződik.
  - **A hitelesítésre rendelkezésre álló időkorlát**: Adja meg másodpercben a maximális várakozási időt (1 és 120 másodperc között) a hálózatban történő hitelesítés előtt.
  - **A Windows további hitelesítő adatokat kérhet a felhasználótól**: **Igen** beállítással a Windows rendszer további hitelesítő adatokat kérhet a felhasználótól, ha a hitelesítési módszer ezt megköveteli. A **Nem** beállítás elrejti ezeket a kéréseket.

- **Páros főkulcs (PMK) gyorsítótárazásának engedélyezése**: Állítsa **Igen** értékre a hitelesítéshez használt PMK gyorsítótárazásához. Ez a gyorsítótárazás általában gyorsabb hálózati hitelesítést tesz lehetővé. A **Nem** beállítással megkövetelheti a hitelesítési kézfogást a Wi-Fi-hálózathoz való minden kapcsolódáskor.

  - **PMK megőrzésének maximális időtartama a gyorsítótárban**: Adja meg a percek számát (5 és 1440 között), amíg a páros főkulcs (PMK) tárolva lesz a gyorsítótárban.
  - **A gyorsítótárban tárolt PMK-k maximális száma**: Adja meg a gyorsítótárban tárolt kulcsok számát 1 és 255 között.

- **Előhitelesítés engedélyezése**: Előhitelesítéssel a profil a hozzá tartozó hálózat összes hozzáférési pontján hitelesítheti magát csatlakozás előtt. Ha a felhasználók illetve az eszközök mozognak a hozzáférési pontok között, az előhitelesítés meggyorsítja az újracsatlakozást. **Igen** beállítással a profil a hálózat összes hatótávolságon belüli hozzáférési pontján hitelesíti magát. **Nem** beállítással a felhasználónak vagy eszköznek minden hozzáférési ponton külön kell hitelesítenie.

  - **Előhitelesítési kísérletek maximális száma**: Adja meg az előhitelesítési próbálkozások számát 1 és 16 között.

- **EAP típusa**: Válassza ki az EAP protokoll biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használni kívánt típusát. A választható lehetőségek:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **Védett EAP** (PEAP)

    **EAP-TLS, EAP-TTLS és PEAP további beállításai**:
    
    > [!NOTE]
    > EAP-típusok használata esetén jelenleg csak az SCEP-tanúsítványprofilok támogatottak. A PKCS-tanúsítványprofilok nem támogatottak. Amikor egy felhasználótól tanúsítvány megadását kérik, mindenképpen SCEP-tanúsítványt kell választani.

    - **Kiszolgáló megbízhatósága**  

      **Tanúsítvány-kiszolgálók nevei**: **EAP-TLS**, **EAP-TTLS** vagy **PEAP** EAP-típusokkal használható. Adjon meg egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti a dinamikus megbízhatósági párbeszédpanelt, amely megjelenik a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.  

      **Gyökértanúsítvány kiszolgálóhitelesítéshez**: **EAP-TLS**, **EAP-TTLS** vagy **PEAP** EAP-típusokkal használható. Válassza ki a kapcsolat hitelesítéséhez használni kívánt megbízható főtanúsítvány-profilt.  

      **Identitásadatok védelme (külső identitás)** : **PEAP** EAP-típussal használható. Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg tetszőleges érték lehet. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.  

    - **Ügyfél-hitelesítés**

      **Ügyfél-hitelesítéshez használandó ügyféltanúsítvány (identitástanúsítvány)** : **EAP-TLS** EAP-típussal használható. Válassza ki a kapcsolat hitelesítéséhez használni kívánt tanúsítványprofilt.

      **Hitelesítési módszer**: **EAP-TTLS** EAP-típussal használható. Válassza ki a kapcsolat hitelesítési módszerét:  

      - **Tanúsítványok**: Válassza ki a kiszolgálónak az identitás tanúsítványaként benyújtott ügyféltanúsítványt.
      - **Felhasználónév és jelszó**: Adjon meg egy **nem-EAP módszert (belső identitás)** a hitelesítéshez. A választható lehetőségek:

        - **Titkosítatlan jelszó (PAP)**
        - **Kérdés-kézfogás (CHAP)**
        - **Microsoft CHAP (MS-CHAP)**
        - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      **Identitásadatok védelme (külső identitás)** : **EAP-TTLS** EAP-típussal használható. Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg tetszőleges érték lehet. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

- **Vállalati proxybeállítások**: Válassza ki a vállalatán belül használni kívánt proxybeállításokat. A választható lehetőségek:
  - **Nincs**: Semmilyen proxybeállítás nincs konfigurálva.
  - **Manuálisan konfigurált**: Adja meg a **proxykiszolgáló IP-címét** és **portszámát**.
  - **Automatikusan konfigurált**: Adja meg egy proxy automatikus konfigurációs (PAC) parancsprogramjának URL-címét. Például írja be a következőt: `http://proxy.contoso.com/proxy.pac`.

- **A Wi-Fi-profil Federal Information Processing Standard (FIPS) szabványnak való megfelelésének a kényszerítése**: Válassza az **Igen** lehetőséget, ha a FIPS 140-2 szabvány szerinti érvényességet ellenőrzi. Ennek a szabványnak a betartása kötelező az összes Egyesült Államokbeli Szövetségi kormányzati szerv részére, ahol titkosításon alapuló biztonsági rendszereket használnak a digitálisan tárolt bizalmas, de nem titkos minősítésű információk tárolására. Válassza a **Nem** lehetőséget, ha nem szeretne FIPS-megfelelőséget.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="use-an-imported-settings-file"></a>Importált beállításfájl használata

Az Intune-ban nem elérhető összes beállításhoz exportálhatja a Wi-Fi-beállításokat egy másik windowsos eszközből. Az exportálás az összes beállítást tartalmazó XML-fájlt hoz létre. Ez után importálja ezt a fájlt az Intune-ba, és használja Wi-Fi-profilként. Lásd: [Wi-Fi-beállítások exportálása és importálása Windows rendszerű eszközökhöz](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További forrásanyagok

- A [Windows 8.1](wi-fi-settings-import-windows-8-1.md) rendszerhez rendelkezésre álló beállítások megtekintése.
- [Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi platformot is.
