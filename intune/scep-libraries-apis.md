---
title: API-k használata külső hitelesítésszolgáltatók regisztrálásához – Microsoft Intune – Azure | Microsoft Docs
description: Felveheti vagy integrálhatja a külső hitelesítésszolgáltatókhoz (CA) készült SCEP GitHub megoldást SCEP-tanúsítványok kibocsátásához a Microsoft Intune-ban lévő eszközökhöz. Ez a megoldás Java és C# API-kat tartalmaz, amelyek érvényesítést végeznek, sikeres és sikertelen üzeneteket küldenek az Intune-nak, és SSL szoftvercsatornát használnak az Intune-nal folytatott kommunikációhoz. Az SCEP CA konfigurációjának teszteléséhez szükséges lépések is áttekintők.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5278b631d581c892f68e8ba08c2bc7893cd3782a
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321668"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>API-k használata az SCEP külső tanúsítványszolgáltatóinak Intune-ba való felvételére

A Microsoft Intune-ban felvehet külső hitelesítésszolgáltatókat (CA-kat), és végrehajthatja ezekkel a CA-kkal a tanúsítványok kibocsátását és érvényesítését az Egyszerű tanúsítványigénylési protokoll (SCEP) használatával. Ennek a funkciónak az áttekintése és az Intune-beli rendszergazdai feladatok leírása a [Külső tanúsítványszolgáltató felvétele](certificate-authority-add-scep-overview.md) szakaszban olvasható.

Van néhány fejlesztői feladat is, amelyek a Microsoft által a GitHub.com webhelyen közzétett nyílt forráskódú könyvtárat használnak. A könyvtár egy olyan API-t tartalmaz, amely:

- Ellenőrzi az Intune által dinamikusan létrehozott SCEP-jelszót
- Értesíti az Intune-t az SCEP-kérelmeket küldött eszközökön létrehozott tanúsítványokról

Ezzel az API-val a külső SCEP-kiszolgáló integrálódik az MDM-eszközök Intune SCEP-felügyeleti megoldásával. A könyvtár aspektusokat kivonatol a felhasználóktól, például a hitelesítést, a szolgáltatás helyét és az ODATA Service API-t.

## <a name="scep-management-solution"></a>SCEP-felügyeleti megoldás

![Harmadik fél hitelesítésszolgáltató SCEP-jének együttműködése a Microsoft Intune-nal](./media/scep-certificate-vendor-integration.png)

Az Intune-ben a rendszergazdák SCEP-profilokat hoznak létre, majd hozzárendelik ezeket az MDM-eszközökhöz. Az SCEP-profilok paramétereket tartalmaznak, mint például az alábbiak:

- A SCEP-kiszolgáló URL-címe
- A hitelesítésszolgáltató megbízható főtanúsítványa
- Tanúsítványattribútumok és egyebek

Az Intune-ba bejelentkező eszközökhöz a rendszer hozzárendeli az SCEP-profilt, és ezekkel a paraméterekkel konfigurálja. Az Intune létrehoz egy dinamikusan generált SCEP-jelszót, majd hozzárendeli az eszközhöz.

Ez a jelszó tartalmazza az eszköz által az SCEP-kiszolgáló számára kibocsátott tanúsítvány-aláírási kérelemhez (CSR) várt paraméterek részleteit. A jelszó az ellenőrző kérdés lejárati időpontját is tartalmazza. Az Intune titkosítja az információt, aláírja a titkosított blobot, majd becsomagolja ezeket az adatokat az SCEP-jelszóba.

Az SCEP-kiszolgálóhoz kapcsolódó, tanúsítványt kérő eszközök ekkor ezt az SCEP-jelszót adják meg. A jelszónak át kell mennie az SCEP-kiszolgálón az érvényesítésen, hogy az tanúsítványt bocsásson ki az eszköz részére. Az SCEP-jelszó érvényesítésekor a következő ellenőrzések történnek:

- Ellenőrzi a titkosított blob aláírását
- Ellenőrzi, hogy az ellenőrző kérdés nem járt-e le
- Ellenőrzi, hogy a profil továbbra is az eszközt célozza-e
- Ellenőrzi, hogy az eszköz által kért tanúsítvány tulajdonságai a CSR-ben egyeznek-e a várt értékekkel

Az SCEP-felügyeleti megoldás jelentéskészítést is tartalmaz. A rendszergazda információt kérhet le az SCEP-profil központi telepítési állapotára és az eszközökhöz kibocsátott tanúsítványokra vonatkozóan.

## <a name="integrate-with-intune"></a>Integrálás az Intune-nal

A könyvtár Intune SCEP-vel való integrációjához rendelkezésre álló kód letölthető a [Microsoft/Intune-Resource-Access GitHub-adattárból](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

A könyvtár és a termékek integrálásához a következő lépéseket kell követnie. A lépések követéséhez szükség van a GitHub-adattárakkal végzett munkára és a Visual Studio alkalmazásban megoldások és projektek létrehozására vonatkozó ismeretekre.

1. Regisztráljon az adattárból érkező értesítések fogadásához
2. Az adattár klónozása vagy letöltése
3. Lépjen a szükséges könyvtár-implementációra a `\src\CsrValidation` mappában (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. Hozza létre a könyvtárat a README fájlban található utasítások alapján
5. Foglalja bele a könyvtárat abba a projektbe, amelyik felépíti az SCEP-kiszolgálóját
6. Hajtsa végre a következő feladatokat a SCEP-kiszolgálón:

    - Engedélyezze a rendszergazdának az [Azure-alkalmazásazonosító, az Azure-alkalmazáskulcs és a bérlőazonosító](#onboard-scep-server-in-azure) konfigurálását (ebben a cikkben), melyeket a könyvtár a hitelesítéshez fog használni. A rendszergazdáknak engedélyeznie kell az Azure-alkalmazáskulcs frissítését.
    - Azonosítsa az Intune által létrehozott SCEP-jelszót magukban foglaló SCEP-kérelmeket
    - Használja a **Kérelem érvényesítése API** könyvtárat az Intune által létrehozott SCEP-jelszavak érvényesítésére
    - Használja az erőforrástár-értesítési API-kat az Intune értesítésére azokról az SCEP-kérelmekhez kibocsátott tanúsítványokról, amelyek rendelkeznek az Intune által létrehozott SCEP-jelszavakkal. Értesítse az Intune-t azokról a hibákról is, amelyek ezeknek az SCEP-kérelmeknek a feldolgozásakor keletkezhetnek.
    - Győződjön meg róla, hogy a kiszolgáló elegendő információt naplóz ahhoz, hogy segítse a rendszergazdákat a hibaelhárításban

7. Hajtsa végre az [integráció tesztelését](#integration-testing) (eben a cikkben), és oldja meg a problémákat
8. Adjon írott útmutatót az ügyfeleknek, amely ismereti az alábbiakat:

    - Hogyan kell a SCEP-kiszolgálót előkészíteni a Microsoft Azure Portalon
    - Hogyan szerezhetik be az erőforrástár konfigurálásához szükséges Azure-alkalmazásazonosítót és az Azure-alkalmazáskulcsot

### <a name="onboard-scep-server-in-azure"></a>Az SCEP-kiszolgáló előkészítése az Azure-ban

Az Intune-ban való hitelesítéshez az SCEP-kiszolgálónak szüksége van egy Azure-alkalmazásazonosítóra, egy Azure-alkalmazáskulcsra és egy bérlőazonosítóra. A SCEP-kiszolgálónak jogosultságra is szüksége van az Intune API eléréséhez.

Ezeknek az adatoknak a lekéréséhez az SCEP-kiszolgáló rendszergazdája bejelentkezik az Azure Portalra, regisztrálja az alkalmazást, engedélyezi az alkalmazásnak a **Microsoft Intune API\SCEP ellenőrző kérdés érvényesítését**, létrehoz az alkalmazáshoz egy kulcsot, majd letölti az alkalmazásazonosítót, a kulcsot és a bérlőazonosítót.

Az alkalmazások regisztrálására és az azonosítók és kulcsok beszerzésére vonatkozó útmutatót lásd: [Az Azure Active Directory-alkalmazás és -erőforrások elérésére képes egyszerű szolgáltatás létrehozása a portál használatával](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>Java-kódtár API

A Java-kódtár Maven-projektként van implementálva, amely lekéri a függőségeit a létrehozásakor. Az API a `com.microsoft.intune.scepvalidation` névtérben van implementálva az `IntuneScepServiceClient` osztály által.

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient osztály

Az `IntuneScepServiceClient` osztály tartalmazza az SCEP szolgáltatás által az SCEP-jelszavak érvényesítésére, az Intune létrehozott tanúsítványokról történő értesítésére és a hibák listázására használt metódusokat.

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient konstruktor

Aláírás:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Leírás:

Példányosít és konfigurál egy `IntuneScepServiceClient` objektumot.

Paraméterek:

    - configProperties: Ügyfél-konfigurációs adatokat tartalmazó tulajdonságok objektum

A konfigurációnak a következő tulajdonságokat kell tartalmaznia:

    - AAD_APP_ID=„Az előkészítési folyamat során beszerzett Azure-alkalmazásazonosító”
    - AAD_APP_KEY=„Az előkészítési folyamat során beszerzett Azure-alkalmazáskulcs”
    - TENANT=„Az előkészítési folyamat során beszerzett bérlőazonosító”
    - PROVIDER_NAME_AND_VERSION =„A termék- és a verzió azonosításához használt információk”

Jelzések:

    - IllegalArgumentException Akkor jelzi a program, ha a konstruktor végrehajtása megfelelő tulajdonságobjektum nélkül történik.

> [!IMPORTANT]
> Legjobb példányosítani ennek az osztálynak egy példányát, és többszörös SCEP-kérelmek feldolgozására használni. Ezzel csökkenti a terhelést, mivel gyorsítótárazza a hitelesítési biztonsági jogkivonatokat és a szolgálatatás helyére vonatkozó adatokat.

**Biztonsági megjegyzések**  
A SCEP-kiszolgáló végrehajtójának védenie kell a konfigurációs tulajdonságokban állandó tárolásra megadott adatokat illetéktelen módosítás és felfedés ellen. Javasoljuk, hogy az adatok védelmére használjon megfelelő hozzáférés-vezérlési listákat és titkosítást.

##### <a name="validaterequest-method"></a>ValidateRequest metódus

Aláírás:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Leírás:

SCEP-tanúsítványkérelem érvényesítése.

Paraméterek:

    - transactionId Az SCEP-tranzakció azonosítója
    - certificateRequest DER kódolású PKCS #10 tanúsítványkérelem, sztringként kódolva Base64 kódolással

Jelzések:

    - IllegalArgumentException Ezt a jelzést érvénytelen paraméterrel történő hívás esetén kapja
    - IntuneScepServiceException jelzést kap, ha nem bizonyul érvényesnek a tanúsítványkérelem
    - Exception jelzést kap, ha kivételhiba történik

> [!IMPORTANT]
> Az ezáltal metódus által okozott kivételeket a kiszolgálónak naplóznia kell. Vegye figyelembe, hogy az `IntuneScepServiceException` tulajdonságok részletes információt tartalmaznak azzal kapcsolatban, hogy miért volt sikertelen a tanúsítványkérelem érvényesítése.

**Biztonsági megjegyzések**  

  - Ha ez a metódus kivételt jelez, a SCEP-kiszolgáló **nem** bocsáthat ki tanúsítványt az ügyfél számára.
  - Az SCEP-ügyféltanúsítványkérelem érvényesítési hibái az Intune-infrastruktúrával kapcsolatos problémára utalhatnak. Vagy azt is jelezhetik, hogy egy támadó próbál meg tanúsítványt kérni.

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification metódus

Aláírás:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Leírás:

Értesíti az Intune-t, hogy az SCEP-kérelem feldolgozásának részeként létrejött egy tanúsítvány.

Paraméterek:

    - transactionId Az SCEP-tranzakció azonosítója
    - certificateRequest DER kódolású PKCS #10 tanúsítványkérelem, sztringként kódolva Base64 kódolással
    - certThumprint A telepített tanúsítvány ujjlenyomata
    - certSerialNumber A telepített tanúsítvány sorozatszáma
    - certExpirationDate A telepített tanúsítvány lejárati dátuma. A dátum-idő karakterláncot webes UTC időként kell formázni (ÉÉÉÉ-HH-NNTmm:ss.sssTZD) ISO 8601.
    - certIssuingAuthority A tanúsítványt kiállító hitelesítésszolgáltató neve

Jelzések:

    - IllegalArgumentException Ezt a jelzést érvénytelen paraméterrel történő hívás esetén kapja
    - IntuneScepServiceException jelzést kap, ha nem bizonyul érvényesnek a tanúsítványkérelem
    - Exception jelzést kap, ha kivételhiba történik

> [!IMPORTANT]
> Az ezáltal metódus által okozott kivételeket a kiszolgálónak naplóznia kell. Vegye figyelembe, hogy az `IntuneScepServiceException` tulajdonságok részletes információt tartalmaznak azzal kapcsolatban, hogy miért volt sikertelen a tanúsítványkérelem érvényesítése.

**Biztonsági megjegyzések**

  - Ha ez a metódus kivételt jelez, a SCEP-kiszolgáló **nem** bocsáthat ki tanúsítványt az ügyfél számára.
  - Az SCEP-ügyféltanúsítványkérelem érvényesítési hibái az Intune-infrastruktúrával kapcsolatos problémára utalhatnak. Vagy azt is jelezhetik, hogy egy támadó próbál meg tanúsítványt kérni.

##### <a name="sendfailurenotification-method"></a>SendFailureNotification metódus

Aláírás:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Leírás:

Értesíti az Intune-t, hogy hiba történt egy SCEP-kérelem feldolgozása közben. Ez a metódus nem hívható meg az ezen osztály metódusai által kiváltott kivételekre.

Paraméterek:

    - transactionId Az SCEP-tranzakció azonosítója
    - certificateRequest DER kódolású PKCS #10 tanúsítványkérelem, sztringként kódolva Base64 kódolással
    - hResult A felmerült hibát legpontosabban leíró Win32-hibakód. Lásd: [Win32-hibakódok](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription A hiba leírása megtalálva

Jelzések:

    - IllegalArgumentException Ezt a jelzést érvénytelen paraméterrel történő hívás esetén kapja
    - IntuneScepServiceException jelzést kap, ha nem bizonyul érvényesnek a tanúsítványkérelem
    - Exception jelzést kap, ha kivételhiba történik

> [!IMPORTANT]
> Az ezáltal metódus által okozott kivételeket a kiszolgálónak naplóznia kell. Vegye figyelembe, hogy az `IntuneScepServiceException` tulajdonságok részletes információt tartalmaznak azzal kapcsolatban, hogy miért volt sikertelen a tanúsítványkérelem érvényesítése.

**Biztonsági megjegyzések**

  - Ha ez a metódus kivételt jelez, a SCEP-kiszolgáló **nem** bocsáthat ki tanúsítványt az ügyfél számára.
  - Az SCEP-ügyféltanúsítványkérelem érvényesítési hibái az Intune-infrastruktúrával kapcsolatos problémára utalhatnak. Vagy azt is jelezhetik, hogy egy támadó próbál meg tanúsítványt kérni.

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory metódus

Aláírás:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Leírás:

Ennek a metódusnak a segítségével tájékoztathatja az ügyfelet arról, hogy a meghatározott SSL-szoftvercsatornát kell használnia (az alapértelmezett helyett) az Intune-nal folytatott kommunikáció során.

Paraméterek:

    - factory Az az SSL-szoftvercsatorna, amelyet az ügyfélnek HTTPS-kérésekhez kell használnia

Jelzések:

    - IllegalArgumentException Ezt a jelzést érvénytelen paraméterrel történő hívás esetén kapja

> [!NOTE]
> Az SSL-szoftvercsatornát szükség esetén az osztály többi metódusainak végrehajtása előtt kell beállítani.

## <a name="integration-testing"></a>Integrációtesztelés

A megoldása és az Intune megfelelő integrációjának ellenőrzése és tesztelése elengedhetetlen. A következő a lépések áttekintését tartalmazza:

1. Állítson be egy [Intune-próbafiókot](account-sign-up.md).
2. Készítse elő az [SCEP-kiszolgálót a Microsoft Azure Portalon](#onboard-scep-server-in-azure) (ebben a cikkben).
3. [Konfigurálja az SCEP-kiszolgálót](certificates-scep-configure.md) az SCEP-kiszolgáló előkészítésekor létrehozott azonosítókkal és kulcsok megadásával.
4. [Eszközök regisztrálása](device-enrollment.md) [a forgatókönyv-tesztelési mátrix](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv) forgatókönyveinek teszteléséhez.
5. [Hozzon létre egy megbízható főtanúsítvány-profilt](certificates-scep-configure.md) a tesztelési hitelesítésszolgáltatóhoz.
6. Hozzon létre SCEP-profilokat a [forgatókönyv-tesztelési mátrixban](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv) felsorolt forgatókönyvek teszteléséhez.
7. [Rendelje hozzá a profilokat](device-profile-assign.md) azokhoz a felhasználókhoz, akik regisztrálták az eszközeiket.
8. Várja meg az eszközök és az Intune szinkronizálásának befejeződését. Vagy [szinkronizálja az eszközöket manuálisan](device-sync.md).
9. Győződjön meg róla, hogy megtörtént a megbízható főtanúsítvány és az SCEP-[profilok központi telepítése az eszközökön](device-profile-monitor.md).
10. Győződjön meg róla, hogy a megbízható főtanúsítvány telepítve van minden eszközön.
11. Győződjön meg róla, hogy a hozzárendelt profilok SCEP-tanúsítványai telepítve vannak minden eszközön.
12. Győződjön meg róla, hogy a telepített tanúsítványok tulajdonságai megfelelnek az SCEP-profilban megadott tulajdonságoknak.
13. Győződjön meg róla, hogy a kiadott tanúsítványok megfelelően szerepelnek az Intune-konzolon

## <a name="see-also"></a>Lásd még:

- [Külső hitelesítésszolgáltató felvételének áttekintése](certificate-authority-add-scep-overview.md)
- [Az Intune telepítése](setup-steps.md)
- [Eszközök regisztrálása](device-enrollment.md)
- [SCEP-tanúsítványprofilok konfigurálása](certificates-scep-configure.md#create-a-scep-certificate-profile) (a Microsoft NDES-kiszolgáló\Összekötő beállítás ebben a forgatókönyvben nem használt)
