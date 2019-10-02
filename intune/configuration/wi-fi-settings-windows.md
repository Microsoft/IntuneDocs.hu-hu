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
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 666e39aa427a10e54ea63b5fc133766335ac09c7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730379"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Wi-Fi-beállítások hozzáadása Windows 10 és újabb rendszerű eszközökhöz az Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti a Windows 10-es vagy újabb eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, az előmegosztott kulcsok használatát és egyebeket.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic-profile"></a>Alapszintű profil

- **Wi-Fi típusa**: Válassza a **Basic** (Egyszerű) lehetőséget. 

- **Wi-Fi-név (SSID)** : A szolgáltatáskészlet-azonosító rövid értéke. Ez az érték a valódi neve a vezeték nélküli hálózatnak, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **kapcsolatnevet** látják, amikor kiválasztják a kapcsolatot.

- **Kapcsolatok neve**: Adja meg a Wi-Fi kapcsolat felhasználóbarát nevét. Az ide beírt szöveg a felhasználók számára megjelenő név, amikor a rendelkezésre álló kapcsolatokat böngészik az eszközeiken.

- **Automatikus csatlakozás a tartományon belül**: Ha **Igen**, az eszközök automatikusan csatlakoznak, amikor a hálózat tartományában vannak. Ha a beállítás **Nem**, akkor az eszközök nem csatlakoznak automatikusan.

  - **Csatlakozás több előnyben részesített hálózathoz, ha elérhető**: Ha az eszközök egy előnyben részesített hálózat hatótávolságán belül vannak, válassza az **Igen** lehetőséget az előnyben részesített hálózat használatához. Válassza a **Nem** beállítást, hogy az ebben a konfigurációs profilban lévő Wi-Fi-hálózatot használják.

    Tegyük fel, hogy létrehozott egy **ContosoCorp** nevű Wi-Fi-hálózatot, és a **ContosoCorp** hálózatot használja ebben a konfigurációs profilban. Elérhető távolságban van egy **ContosoGuest** nevű Wi-Fi-hálózat is. Azt szeretné, hogy ha céges eszközei hatókörön belül vannak, automatikusan a **ContosoCorphoz** csatlakozzanak. Ebben az esetben állítsa a **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz** tulajdonságot **Nem** értékre.

  - **Csatlakozás ehhez a hálózathoz, még akkor is, ha nem sugározza az SSID**-t: Válassza az **Igen** lehetőséget a konfigurációs profilhoz, hogy automatikusan csatlakozhasson a hálózathoz, még akkor is, ha a hálózat el van rejtve (vagyis az SSID-t nem a nyilvános szórásra). Válassza a **Nem** beállítást, ha nem szeretné, hogy ez a konfigurációs profil a rejtett hálózathoz csatlakozzon.

- **Mért kapcsolatok korlátja**: A rendszergazda megadhatja a hálózat forgalmának mérését. Alkalmazások ezt követően ennek a beállításnak az alapján módosíthatják a hálózati forgalommal kapcsolatos viselkedésüket. A választható lehetőségek:

  - Nem **korlátozott**: Default (Alapértelmezett): A rendszer nem méri a kapcsolatot, és nincs korlátozva a forgalom.
  - **Kijavítva**: Akkor használja ezt a beállítást, ha a hálózat rögzített korláttal van konfigurálva a hálózati forgalomhoz. A korlát elérése után a hálózati hozzáférés le van tiltva.
  - **Változó**: Akkor használja ezt a beállítást, ha a hálózati forgalom díja bájt (költség/bájt).

- **Vezeték nélküli biztonság típusa**: Adja meg a hálózaton lévő eszközök hitelesítéséhez használt biztonsági protokollt. A lehetőségek a következők:
  - **Megnyitás (nincs hitelesítés)** : Csak akkor használja ezt a beállítást, ha a hálózat nem biztonságos.
  - **WPA/WPA2-Personal**: Egy biztonságosabb megoldás, amelyet általában a Wi-Fi-kapcsolathoz használ a rendszer. A további biztonság érdekében előre megosztott kulcsot vagy hálózati kulcsot is megadhat.

    - **Előmegosztott kulcs** (PSK): Nem kötelező. Akkor jelenik meg, ha a **WPA/WPA2 (személyes)** biztonsági típust választja. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként. 8–64 karakter közötti hosszúságú sztringet adjon meg. Ha a jelszó vagy a hálózati kulcs 64 karakterből áll, akkor hexadecimális karakteret adjon meg.

      > [!NOTE]
      > A Wi-Fi-profil mentésekor a PSK megadott értéke nem jelenik meg biztonsági okokból. Az előre megosztott kulcs vízjele továbbra is **Nincs konfigurálva** értéket mutat annak ellenére, hogy a PSK el van mentve a profilban. A PSK módosításához adjon meg egy új kulcsot, majd mentse a profilt. Ha a PSK mentésekor szerkeszti a szabályzatot, a PSK-t pedig üresen hagyja, továbbra is a meglévő PSK lesz használatban.
      > [!IMPORTANT]
      > A PSK ugyanaz, mint az összes olyan eszközön, amelyre a profilt célozza. Ha a kulcs biztonsága sérül, bármely eszköz használhatja a Wi-Fi hálózathoz való csatlakozáshoz. A jogosulatlan hozzáférés elkerüléséhez tartsa biztonságos PSKs.

- **Vállalati proxybeállítások**: Válassza ki a szervezeten belüli proxybeállítások használatát. A választható lehetőségek:
  - **Nincs**: Nincsenek proxybeállítások konfigurálva.
  - **Manuális konfigurálás**: Adja meg a **proxykiszolgáló IP** -címe és **portszámát**.
  - **Automatikus konfigurálás**: Adja meg a proxy automatikus konfigurációs (PAC) parancsfájlra mutató URL-címet. Például írja be a következőt: `http://proxy.contoso.com/proxy.pac`.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="enterprise-profile"></a>Vállalati profil

- **Wi-Fi típusa**: Válassza a **vállalat**lehetőséget.

- **Wi-Fi-név (SSID)** : A szolgáltatáskészlet-azonosító rövid értéke. Ez az érték a valódi neve a vezeték nélküli hálózatnak, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **kapcsolatnevet** látják, amikor kiválasztják a kapcsolatot.

- **Kapcsolatok neve**: Adja meg a Wi-Fi kapcsolat felhasználóbarát nevét. Az ide beírt szöveg a felhasználók számára megjelenő név, amikor a rendelkezésre álló kapcsolatokat böngészik az eszközeiken.

- **Automatikus csatlakozás a tartományon belül**: Ha **Igen**, az eszközök automatikusan csatlakoznak, amikor a hálózat tartományában vannak. Ha a beállítás **Nem**, akkor az eszközök nem csatlakoznak automatikusan.
  - **Csatlakozás több előnyben részesített hálózathoz, ha elérhető**: Ha az eszközök egy előnyben részesített hálózat hatótávolságán belül vannak, válassza az **Igen** lehetőséget az előnyben részesített hálózat használatához. Válassza a **Nem** beállítást, hogy az ebben a konfigurációs profilban lévő Wi-Fi-hálózatot használják.

    Tegyük fel, hogy létrehozott egy **ContosoCorp** nevű Wi-Fi-hálózatot, és a **ContosoCorp** hálózatot használja ebben a konfigurációs profilban. Elérhető távolságban van egy **ContosoGuest** nevű Wi-Fi-hálózat is. Azt szeretné, hogy ha céges eszközei hatókörön belül vannak, automatikusan a **ContosoCorphoz** csatlakozzanak. Ebben az esetben állítsa a **Lehetőség szerint csatlakozás egy előnyben részesített hálózathoz** tulajdonságot **Nem** értékre.

  - **Csatlakozás ehhez a hálózathoz, még akkor is, ha nem sugározza az SSID**-t: Válassza az **Igen** lehetőséget a konfigurációs profilhoz, hogy automatikusan csatlakozhasson a hálózathoz, még akkor is, ha a hálózat el van rejtve (vagyis az SSID-t nem a nyilvános szórásra). Válassza a **Nem** beállítást, ha nem szeretné, hogy ez a konfigurációs profil a rejtett hálózathoz csatlakozzon.

- **Mért kapcsolatok korlátja**: A rendszergazda megadhatja a hálózat forgalmának mérését. Alkalmazások ezt követően ennek a beállításnak az alapján módosíthatják a hálózati forgalommal kapcsolatos viselkedésüket. A választható lehetőségek:

  - Nem **korlátozott**: Default (Alapértelmezett): A rendszer nem méri a kapcsolatot, és nincs korlátozva a forgalom.
  - **Kijavítva**: Akkor használja ezt a beállítást, ha a hálózat rögzített korláttal van konfigurálva a hálózati forgalomhoz. A korlát elérése után a hálózati hozzáférés le van tiltva.
  - **Változó**: Akkor használja ezt a beállítást, ha a hálózati forgalom ára bájtban van számolva.

- **Egyszeri bejelentkezés (SSO)** : Lehetővé teszi az egyszeri bejelentkezés (SSO) konfigurálását, ahol a hitelesítő adatok megoszthatók a számítógép és a Wi-Fi hálózati bejelentkezés során. A lehetőségek a következők:
  - **Letiltás**: Letiltja az egyszeri bejelentkezés működését. A felhasználónak külön kell hitelesítenie magát a hálózaton.
  - **Engedélyezés, mielőtt a felhasználó bejelentkezik az eszközre**: Az egyszeri bejelentkezéssel hitelesítheti a hálózatot közvetlenül a felhasználó bejelentkezési folyamata előtt.
  - **Engedélyezés, miután a felhasználó bejelentkezik az eszközre**: A felhasználó bejelentkezési folyamatának befejeződése után azonnal hitelesítse magát a hálózatban az SSO használatával.
  - **Időtúllépés előtti hitelesítés maximális ideje**: Adja meg azt a maximális időtartamot másodpercben, ameddig a hálózatra való hitelesítés előtt várni kell, hogy a rendszer 1-120 másodperc múlva.
  - **További hitelesítő adatok kérésének engedélyezése a Windows számára a felhasználóknak**: Ha az **Igen** lehetőséget választja, a Windows rendszer további hitelesítő adatok megadását kéri a felhasználótól, ha a hitelesítési módszer szükséges. A **Nem** beállítás elrejti ezeket a kéréseket.

- **Páros főkulcs gyorsítótárazásának engedélyezése**: Válassza az **Igen** lehetőséget a hitelesítéshez használt főkulcsok gyorsítótárazásához. Ez a gyorsítótárazás általában gyorsabb hálózati hitelesítést tesz lehetővé. A **Nem** beállítással megkövetelheti a hitelesítési kézfogást a Wi-Fi-hálózathoz való minden kapcsolódáskor.

  - **A FŐkulcsok maximális ideje a gyorsítótárban tárolódik**: Adja meg, hogy hány perc elteltével páros a rendszer a gyorsítótárban, 5-1440 percen belül.
  - **A gyorsítótárban tárolt PMKs maximális száma**: Adja meg a gyorsítótárban tárolt kulcsok számát 1-255-ból.

- **Előzetes hitelesítés engedélyezése**: Az előhitelesítés lehetővé teszi, hogy a profil a csatlakozás előtt a hálózat összes hozzáférési pontjára hitelesítse a profilt. Ha a felhasználók illetve az eszközök mozognak a hozzáférési pontok között, az előhitelesítés meggyorsítja az újracsatlakozást. **Igen** beállítással a profil a hálózat összes hatótávolságon belüli hozzáférési pontján hitelesíti magát. **Nem** beállítással a felhasználónak vagy eszköznek minden hozzáférési ponton külön kell hitelesítenie.

  - **Előhitelesítési kísérletek maximális száma**: Adja meg az előhitelesítésre való próbálkozások számát a 1-16-ból.

- **EAP-típus**: Válassza ki a bővíthető hitelesítési protokoll (EAP) típusát a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **Védett EAP** (PEAP)

    **EAP-TLS, EAP-TTLS és PEAP további beállításai**:
    
    > [!NOTE]
    > EAP-típusok használata esetén jelenleg csak az SCEP-tanúsítványprofilok támogatottak. A PKCS-tanúsítványprofilok nem támogatottak. Amikor egy felhasználótól tanúsítvány megadását kérik, mindenképpen SCEP-tanúsítványt kell választani.

    - **Kiszolgáló megbízhatósága**  

      **Kiszolgálótanúsítvány-kiszolgálók nevei**: Az **EAP-TLS**, **EAP-TTLS**vagy **PEAP** EAP-típusokkal használható. Adjon meg egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti a dinamikus megbízhatósági párbeszédpanelt, amely megjelenik a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.  

      **Kiszolgáló-ellenőrzés**főtanúsítványa: Az **EAP-TLS**, **EAP-TTLS**vagy **PEAP** EAP-típusokkal használható. Válassza ki a kapcsolat hitelesítéséhez használni kívánt megbízható főtanúsítvány-profilt.  

      **Személyazonosság védelme (külső identitás)** : **PEAP** EAP-típussal használható. Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg tetszőleges érték lehet. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.  

    - **Ügyfél-hitelesítés**

      Ügyféltanúsítvány **az ügyfél-hitelesítéshez (identitás-tanúsítvány)** : Az **EAP-TLS EAP-** típussal használható. Válassza ki a kapcsolat hitelesítéséhez használni kívánt tanúsítványprofilt.

      **Hitelesítési módszer**: Az **EAP-TTLS EAP-** típussal használható. Válassza ki a kapcsolat hitelesítési módszerét:  

      - **Tanúsítványok**: Válassza ki azt az ügyféltanúsítványt, amely a kiszolgálónak bemutatott identitás-tanúsítvány.
      - **Felhasználónév és jelszó**: Adjon meg egy **nem EAP-módszer (belső identitás)** módszert a hitelesítéshez. A választható lehetőségek:

        - **Titkosítatlan jelszó (PAP)**
        - **Kérdés-kézfogás (CHAP)**
        - **Microsoft CHAP (MS-CHAP)**
        - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      **Személyazonosság védelme (külső identitás)** : Az **EAP-TTLS EAP-** típussal használható. Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg tetszőleges érték lehet. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

- **Vállalati proxybeállítások**: Válassza ki a szervezeten belüli proxybeállítások használatát. A választható lehetőségek:
  - **Nincs**: Nincsenek proxybeállítások konfigurálva.
  - **Manuális konfigurálás**: Adja meg a **proxykiszolgáló IP** -címe és **portszámát**.
  - **Automatikus konfigurálás**: Adja meg a proxy automatikus konfigurációs (PAC) parancsfájlra mutató URL-címet. Például írja be a következőt: `http://proxy.contoso.com/proxy.pac`.

- **A Wi-Fi profil kényszerítése a Federal Information Processing standard (FIPS) szabványnak megfelelően**: Az FIPS 140-2 szabványnak megfelelő érvényesítéskor válassza az **Igen** lehetőséget. Ennek a szabványnak a betartása kötelező az összes Egyesült Államokbeli Szövetségi kormányzati szerv részére, ahol titkosításon alapuló biztonsági rendszereket használnak a digitálisan tárolt bizalmas, de nem titkos minősítésű információk tárolására. Válassza a **Nem** lehetőséget, ha nem szeretne FIPS-megfelelőséget.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="use-an-imported-settings-file"></a>Importált beállításfájl használata

Az Intune-ban nem elérhető összes beállításhoz exportálhatja a Wi-Fi-beállításokat egy másik windowsos eszközből. Az exportálás az összes beállítást tartalmazó XML-fájlt hoz létre. Ez után importálja ezt a fájlt az Intune-ba, és használja Wi-Fi-profilként. Lásd: [Wi-Fi-beállítások exportálása és importálása Windows rendszerű eszközökhöz](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

- A [Windows 8.1](wi-fi-settings-import-windows-8-1.md) rendszerhez rendelkezésre álló beállítások megtekintése.
- [Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi platformot is.
