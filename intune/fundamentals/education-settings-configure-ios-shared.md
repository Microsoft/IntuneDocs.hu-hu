---
title: Az iOS-es Osztályterem alkalmazás megosztott eszközeire vonatkozó Intune-beállítások
titleSuffix: Microsoft Intune
description: Tájékoztatás az Intune azon beállításairól, amelyekkel szabályozhatók az Osztályterem alkalmazás beállításai az iOS-eszközökön.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0edfd9b8ee8b45952d9c22d5365d09d125ea7710
ms.sourcegitcommit: 78faf608510fbaca09bc410d63df1aa5254dee45
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74784255"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>Az Intune oktatási beállításainak konfigurálása megosztott iPad eszközökhöz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

> [!NOTE]
> Az Intune jelenleg nem támogatja az osztályterem alkalmazás konfigurálását. Ez a cikk csak az Intune-ban meglévő iOS-es oktatási profilokkal rendelkező felhasználókra érvényes.

Az Intune támogatja az iOS-es Osztályterem alkalmazást, amely lehetővé teszi az oktatóknak a tanulási folyamat és a diákok eszközeinek irányítását az osztályteremben. Az Osztályterem alkalmazás mellett az Apple támogatja a diákok iPad eszközeinek olyan konfigurációját, amely egyetlen eszköz több diák általi használatát teszi lehetővé. Ebből a dokumentumból megtudhatja, hogy ezt hogyan valósíthatja meg az Intune-nal.

További információ a dedikált (egyszemélyes használatban lévő) iPad eszközök Osztályterem alkalmazással való konfigurációjáról: [Az iOS-beli Osztályterem alkalmazás Intune-beállításainak konfigurálása](education-settings-configure-ios.md).

## <a name="before-you-start"></a>Előkészületek

A megosztott iPad használatának előfeltételei:

- Az [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) és a [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617) telepítése.
- A diákok [felügyelt Apple ID-jának](http://help.apple.com/schoolmanager/#/tes78b477c81) konfigurálása az Apple School Manager telepítése során. [További tudnivalók a felügyelt Apple ID-król](https://support.apple.com/HT205918).
- Egy regisztrációs profil létrehozása az Apple School Managerből szinkronizált eszközök sorozatszámaihoz.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>1\. lépés – Importálja az iskolai adatokat az Azure Active Directoryba

A Microsoft School Data Sync (SDS) használatával importálja az iskolai adatokat egy meglévő hallgatói információs rendszerből (Student Information System, SIS) az Azure Active Directoryba (Azure AD).
Az SDS szinkronizálja a SIS adatait, és tárolja azokat az Azure AD-ben. Az Azure AD egy Microsoft felügyeleti rendszer, amely segítséget nyújt a felhasználók és eszközök rendezéséhez. Ezeket az adatokat felhasználhatja a diákok és a tanórák kezeléséhez. További információk az [SDS üzembe helyezésével](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) kapcsolatban.

### <a name="how-to-import-data-using-sds"></a>Adatok importálása az SDS használatával

Az SDS-be a következő módszerek valamelyikével importálhat adatokat:

- [CSV-fájlok](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – Vesszővel tagolt (.csv) fájlok manuális exportálása és összeállítása
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – Egy SIS-szolgáltató, amely egyszerűsíti a szinkronizálást az Azure AD-vel
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) – Ebbe a CSV-formátumba exportálhat, és konvertálhatja az Azure AD-vel való szinkronizáláshoz

### <a name="find-out-more"></a>További tudnivalók

- [További információ a helyszíni iskolai adatok az Azure AD-vel való szinkronizálásának teljes folyamatáról](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [További információ a Microsoft School Data Sync-kel kapcsolatban](https://sds.microsoft.com/)
- [További tudnivalók az Azure Active Directorybeli licencelésről](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>2\. lépés – Egy iOS-es Oktatás profil létrehozása és hozzárendelése az Intune-ban

### <a name="configure-general-settings"></a>Általános beállítások konfigurálása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
2. Az **Eszközkonfiguráció** panel **Kezelés** területén válassza a **Profilok** lehetőséget.
5. A profilok paneljén válassza a **Profil létrehozása** lehetőséget.
6. A **Profil létrehozása** panelen adja meg az iOS-es oktatási profil **Nevét** és **Leírását**.
7. A **Platform** legördülő listájában válassza az **iOS** lehetőséget.
8. A **Profil típusa** legördülő listában válassza az **Oktatás** lehetőséget.
9. Válassza a **Beállítások** > **Konfigurálás** lehetőséget.

Ezután tanúsítványokra lesz szüksége az oktató és a diákok iPadjei közötti megbízhatósági kapcsolat létrehozásához. A tanúsítványok az eszközök közötti kapcsolatok felhasználónevek és jelszavak megadása nélküli, zökkenőmentes és csendes hitelesítéséhez használatosak.

>[!Important]
>A használt oktatói és diáktanúsítványokat különböző hitelesítésszolgáltatóknak (CA) kell kiállítaniuk. Létre kell hoznia két új alárendelt hitelesítésszolgáltatót a meglévő tanúsítvány-infrastruktúrához kapcsolódva: egyet az oktatók és egyet a diákok számára.

Az iOS oktatási profiljai csak a PFX-tanúsítványokat támogatják. Az SCEP-tanúsítványok nem támogatottak.

A létrehozott tanúsítványoknak támogatniuk kell a kiszolgálói hitelesítést is a felhasználó hitelesítése mellett.

### <a name="configure-teacher-certificates"></a>Oktatói tanúsítványok konfigurálása

Az **Oktatás** panelen válassza a **Oktatói tanúsítványok** lehetőséget.

#### <a name="configure-teacher-root-certificate"></a>Oktatói főtanúsítvány konfigurálása

Az **Oktatói főtanúsítvány** területen a Tallózás gombra kattintva válassza ki az oktatói főtanúsítvány .cer (DER vagy Base64-kódolású) vagy .P7b (a teljes tanúsítványlánccal vagy anélkül) kiterjesztésű fájlját.

#### <a name="configure-teacher-pkcs12-certificate"></a>Oktatói PKCS#12 tanúsítvány konfigurálása

Az **Oktatói PKCS#12-tanúsítvány** területen konfigurálja a következő értékeket:

- **Tulajdonosnév formátuma** – Az Intune automatikusan előtaggal egészíti ki a tanúsítvány köznapi nevét. Ez az oktatói tanúsítványoknál **leader** (vezető), illetve **member** (tag) a diáktanúsítványok esetében.
- **Hitelesítésszolgáltató:** Olyan vállalati hitelesítésszolgáltató (CA), amelyen a Windows Server 2008 R2 vagy újabb rendszer Enterprise kiadása fut. Az önálló hitelesítésszolgáltató nem támogatott.
- **Hitelesítésszolgáltató neve** – Adja meg a hitelesítésszolgáltatója nevét.
- **Tanúsítványsablon neve** – Válassza ki annak a tanúsítványsablonnak a nevét, amely hozzá van adva egy kiállító hitelesítésszolgáltatóhoz.
- **Megújítási küszöb (%)** – Adja meg, hogy az eszköz a tanúsítvány élettartamának hány százalékos hátralévő idejénél igényelje a tanúsítvány megújítását.
- **Tanúsítvány érvényességi időtartama** – Adja meg a tanúsítvány lejáratáig hátralévő időt. A megadott tanúsítványsablonban meghatározott érvényességi időszaknál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet beállíthat értékként, öt évet azonban nem. Az értéknek emellett a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál is kevesebbnek kell lennie.

Miután befejezte az oktatói tanúsítványok konfigurálását, kattintson az **OK** gombra.

### <a name="configure-student-certificates"></a>Diáktanúsítványok konfigurálása

1. Az **Oktatás** panelen válassza a **Diáktanúsítványok** lehetőséget.
2. A **Diáktanúsítványok** panelen a **Tanulóieszköz-tanúsítványok típusa** listából válassza a **Megosztott iPad** lehetőséget.

#### <a name="configure-student-root-certificate"></a>Tanulói főtanúsítvány konfigurálása

Az **Eszköz főtanúsítványa** területen a Tallózás gombra kattintva válassza ki a tanulói főtanúsítvány .cer (DER vagy Base64-kódolású) vagy .P7b (a teljes tanúsítványlánccal vagy anélkül) kiterjesztésű fájlját.

#### <a name="configure-device-pkcs12-certificate"></a>Az eszköz PKCS#12-tanúsítványának konfigurálása

Az **Tanulói PKCS#12-tanúsítvány** területen konfigurálja a következő értékeket:

- **Tulajdonosnév formátuma** – Az Intune automatikusan előtaggal egészíti ki a tanúsítvány köznapi nevét. Ez az oktatói tanúsítványoknál leader (vezető), az eszköztanúsítványok esetében pedig member (tag).
- **Hitelesítésszolgáltató:** Olyan vállalati hitelesítésszolgáltató (CA), amelyen a Windows Server 2008 R2 vagy újabb rendszer Enterprise kiadása fut. Az önálló hitelesítésszolgáltató nem támogatott.
- **Hitelesítésszolgáltató neve** – Adja meg a hitelesítésszolgáltatója nevét.
- **Tanúsítványsablon neve** – Válassza ki annak a tanúsítványsablonnak a nevét, amely hozzá van adva egy kiállító hitelesítésszolgáltatóhoz.
- **Megújítási küszöb (%)** – Adja meg, hogy az eszköz a tanúsítvány élettartamának hány százalékos hátralévő idejénél igényelje a tanúsítvány megújítását.
- **Tanúsítvány érvényességi időtartama** – Adja meg a tanúsítvány lejáratáig hátralévő időt. A megadott tanúsítványsablonban meghatározott érvényességi időszaknál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet beállíthat értékként, öt évet azonban nem. Az értéknek emellett a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál is kevesebbnek kell lennie.

Miután befejezte a tanúsítványok konfigurálását, kattintson az **OK** gombra.

### <a name="complete-certificate-setup"></a>A tanúsítvány telepítésének befejezése

1. Az **Oktatás** panelen kattintson az **OK** gombra.
2. A **Profil létrehozása** panelen válassza a **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó panelen.

## <a name="step-3---create-a-device-category"></a>3\. lépés – eszközkategória létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközregisztráció** lehetőséget.
4. Az **Eszközregisztráció – Áttekintés** panelen válassza az **Eszközkategóriák** elemet.
5. Az **Eszközregisztráció – Eszközkategóriák** panelen válassza a **Létrehozás** lehetőséget.
6. Az **Eszközkategória létrehozása** panelen adja meg a kategória **Nevét** és **Leírását**.
7. A **Eszközkategória létrehozása** panelen válassza a **Létrehozás** lehetőséget.

Az eszközkategória ekkor létrejön a **Regisztráció – Eszközkategóriák** panelen.

## <a name="step-4--create-a-dynamic-group"></a>4\. lépés – dinamikus csoport létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Csoportok** lehetőséget.
4. A **Felhasználók és csoportok – Minden csoport** panelen válassza az **Új csoport** lehetőséget.
5. A **Csoport** panelen válasszon **Csoporttípust**, majd adja meg a csoport **Nevét** és **Leírását**.
6. A **Tagság típusa** legördülő listából válassza a **Dinamikus eszköz** lehetőséget.
7. A tagsági szabályok létrehozásához válassza a **Dinamikus eszköztagság** lehetőséget.
8. A **Dinamikus tagsági szabályok** panelen tegye a következőket:
1. Az **Eszközök hozzáadásának helye** legördülő menüben válassza a **deviceCategory** lehetőséget.
2. Válassza az **Egyenlő** lehetőséget.
3. Írja be az üres szövegdobozba a létrehozott eszközkategória nevét.
9. A **Dinamikus tagsági szabályok** panelen válassza a **Lekérdezés hozzáadása** lehetőséget.
10. A **Csoport** panelen válassza a **Létrehozás** lehetőséget.

A dinamikus csoport ekkor létrejön a **Felhasználók és csoportok – Minden csoport** panelen.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>5\. lépés – eszközök hozzárendelése egy kategóriához (kocsik)

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközök** lehetőséget.
4. Az **Eszközök** panelen válassza a **Minden eszköz** lehetőséget.
5. Az **Eszközök – Minden eszköz** panelen válasszon ki egy eszközt.
6. Az eszközök paneljén válassza a **Tulajdonságok** lehetőséget.
7. Az eszköz Tulajdonságok panelén adja meg az eszközkategóriát az **Eszközkategória** szövegdobozban.
8. Az eszközök paneljén válassza a **Mentés** lehetőséget.

Az eszköz mostantól hozzá van rendelve az eszközkategóriához. Ismételje meg ezt a folyamatot minden olyan eszközre, amelyet hozzá szeretne rendelni a létrehozott eszközkategóriához.

## <a name="step-6--create-classroom-profiles"></a>6\. lépés – Osztályterem-profilok létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
4. Az **Eszközkonfiguráció** panelen válassza a **Felügyelet** > **Kocsiprofilok** lehetőséget.
5. A profilok paneljén válassza a **Profil létrehozása** lehetőséget.
6. A **Hozzárendelés létrehozása** panelen adjon meg egy **Nevet** és egy **Leírást**.
7. A csoportok kocsiprofillal való társításához válassza az **Osztályok kiválasztása** > **Konfigurálás** lehetőséget.
8. Válassza ki a kocsiprofilhoz hozzáadni kívánt osztályokat, majd kattintson a **Kijelölés** lehetőségre. 
9. A csoportok kocsiprofillal való társításához válassza az **Kocsik kiválasztása** > **Konfigurálás** lehetőséget.
10. Válassza ki a kocsiprofilban alkalmazni kívánt csoportokat, majd kattintson a **Kijelölés** lehetőségre.
11. A kocsiprofil mentéséhez a **Hozzárendelés létrehozása** panelen válassza a **Mentés** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó panelen.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>7\. lépés – a kocsiprofil hozzárendelése az osztályokhoz

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
4. Az **Eszközkonfiguráció** panelen válassza a **Figyelés** > **Hozzárendelés állapota** lehetőséget.
5. A **Hozzárendelés állapota** panelen jelölje ki a létrehozott **kocsiprofilt**.
6. A **Kocsiprofil** panelen válassza a **Hozzárendelések** lehetőséget, majd a **Belefoglalás** területen a **Válassza ki a befoglalandó csoportokat** lehetőséget.
7. Válassza ki a kocsiprofil célosztályait (ne válasszon ki csoportokat), majd kattintson a **Kijelölés** lehetőségre. 
8. Ha elkészült, válassza a **Mentés** elemet.

A hozzárendelés ekkor befejeződik, az Intune pedig üzembe helyezi az Osztályterem profilját a céleszközökön az osztályterem-hozzárendelés alapján.

## <a name="next-steps"></a>További lépések

A diákok mostantól megoszthatják egymás között az eszközöket, és bármelyik iPadet használhatják az osztályteremben, bejelentkezhetnek saját PIN-kódjukkal, és személyre szabhatják az eszközöket saját tartalmaikkal. A megosztott iPadekről további információt az [Apple webhelyén](https://www.apple.com/education/it/) találhat.
