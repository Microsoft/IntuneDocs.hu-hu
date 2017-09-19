---
title: "Az iOS-es Osztályterem alkalmazás Intune-beállításai"
titlesuffix: Azure portal
description: "A cikk tájékoztatást nyújt az Intune azon beállításairól, amelyekkel szabályozhatók az Osztályterem alkalmazás beállításai az iOS-eszközökön."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f31ad2226052b4a681bc79e366e7d1def01c3cc4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Az iOS-beli Osztályterem alkalmazás Intune-beállításainak konfigurálása

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Bevezetés
Az [Osztályterem](https://itunes.apple.com/app/id1085319084) egy olyan alkalmazás, amely lehetővé teszi az oktatóknak a tanulási folyamat és a diákok eszközeinek irányítását az osztályteremben. Az alkalmazás használatával egy oktató például:

- Megnyithat alkalmazásokat a diákok eszközein
- Zárolhatja az iPad képernyőjét és feloldhatja annak zárolását
- Megtekintheti egy diák iPadjének képernyőjét
- Egy könyvjelzőre vagy egy könyv adott fejezetére léptetheti a diákok iPadjeit
- Megjelenítheti egy diák iPad-képernyőjét az Apple TV-n

Használja az Intune iOS **Oktatás** eszközprofilját és ennek a témakörnek az információit az Osztályterem alkalmazásnak és azoknak az eszközöknek a beállításához, amelyeken használni fogja azt.

## <a name="before-you-start"></a>Előkészületek

A beállítások konfigurálása előtt vegye figyelembe a következőket:

- Az oktatók és a diákok iPadjeinek regisztrálva kell lenniük az Intune-ban
- Győződjön meg arról, hogy az oktató eszközén telepítve van az [Apple Osztályterem](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) alkalmazás. Telepítheti az alkalmazást manuálisan, vagy használhatja az [Intune-alkalmazáskezelést](app-management.md).
- Tanúsítványokat kell konfigurálnia az oktatói és a diákeszközök közötti kapcsolat hitelesítéséhez (lásd a 2. lépést)
- A tanári és a hallgatói iPadeknek azonos Wi-Fi hálózaton kell lenniük, és a Bluetooth használatának engedélyezése is szükséges
- Az Osztályterem alkalmazás iOS 9.3 vagy újabb operációs rendszerű felügyelt iPadeken működik
- Ebben a kiadásban az Intune az 1:1-es forgatókönyv kezelését támogatja, amelynek esetén minden diák saját dedikált iPad készülékkel rendelkezik


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>1. lépés – Importálja az iskolai adatokat az Azure Active Directoryba

A Microsoft School Data Sync (SDS) használatával importálja az iskolai adatokat egy meglévő hallgatói információs rendszerből (Student Information System, SIS) az Azure Active Directoryba (Azure AD).
Az SDS szinkronizálja a SIS adatait, és tárolja azokat az Azure AD-ben. Az Azure AD egy Microsoft felügyeleti rendszer, amely segítséget nyújt a felhasználók és eszközök rendezéséhez. Ezeket az adatokat felhasználhatja a diákok és a tanórák kezeléséhez. További információk az [SDS üzembe helyezésével](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) kapcsolatban.

### <a name="how-to-import-data-using-sds"></a>Adatok importálása az SDS használatával

Az SDS-be a következő módszerek valamelyikével importálhat adatokat:

- [CSV-fájlok](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – Vesszővel tagolt (.csv) fájlok manuális exportálása és összeállítása
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – Egy SIS-szolgáltató, amely egyszerűsíti a szinkronizálást az Azure AD-vel
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) – Egy közvetlenül az Azure AD-vel szinkronizáló identitáskezelési megoldás
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) – Ebbe a CSV-formátumba exportálhat, és konvertálhatja az Azure AD-vel való szinkronizáláshoz

### <a name="find-out-more"></a>További tudnivalók

- [További információ a helyszíni iskolai adatok az Azure AD-vel való szinkronizálásának teljes folyamatáról](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [További információ a Microsoft School Data Sync-kel kapcsolatban](https://sds.microsoft.com/)
- [További tudnivalók az Azure Active Directorybeli licencelésről](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>2. lépés – Egy iOS-es Oktatás profil létrehozása és hozzárendelése az Intune-ban

### <a name="configure-general-settings"></a>Általános beállítások konfigurálása

1. Jelentkezzen be az Azure Portalra.
2. Válassza a **További szolgáltatások** > **Figyelés + felügyelet** > **Intune** lehetőséget.
3.  Az **Intune** panelen válassza az **Eszközök konfigurálása** lehetőséget.
4.  Az **Eszközkonfiguráció** panelen válassza a **Felügyelet** > **Profilok** lehetőséget.
5.  A profilok paneljén válassza a **Profil létrehozása** lehetőséget.
6.  A **Profil létrehozása** panelen töltse ki az iOS-es oktatási profil **Név** és **Leírás** mezőjét.
7.  A **Platform** legördülő listájában válassza az **iOS** lehetőséget.
8.  A **Profil típusa** legördülő listában válassza az **Oktatás** lehetőséget.
9.  Válassza a **Beállítások** > **Konfigurálás** lehetőséget.


Ezután tanúsítványokra lesz szüksége az oktató és a diákok iPadjei közötti megbízhatósági kapcsolat létrehozásához. A tanúsítványok az eszközök közötti kapcsolatok felhasználónevek és jelszavak megadása nélküli, zökkenőmentes és csendes hitelesítéséhez használatosak.

>[!IMPORTANT]
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
- **Tanúsítvány érvényességi időtartama** – Adja meg a tanúsítvány lejáratáig hátralévő időt.
A megadott tanúsítványsablonban meghatározott érvényességi időszaknál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet beállíthat értékként, öt évet azonban nem. Az értéknek emellett a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál is kevesebbnek kell lennie.

Miután befejezte a tanúsítványok konfigurálását, kattintson az **OK** gombra.

### <a name="configure-student-certificates"></a>Diáktanúsítványok konfigurálása

1.  Az **Oktatás** panelen válassza a **Diáktanúsítványok** lehetőséget.
2.  A **Diáktanúsítványok** panelen a **Tanulóieszköz-tanúsítványok típusa** listából válassza az **1:1** lehetőséget.

#### <a name="configure-student-root-certificate"></a>Tanulói főtanúsítvány konfigurálása

A **Tanulói főtanúsítvány** területen a Tallózás gombra kattintva válassza ki a tanulói főtanúsítvány .cer (DER vagy Base64-kódolású) vagy .P7b (a teljes tanúsítványlánccal vagy anélkül) kiterjesztésű fájlját.

#### <a name="configure-student-pkcs12-certificate"></a>Tanulói PKCS#12-tanúsítvány konfigurálása

Az **Tanulói PKCS#12-tanúsítvány** területen konfigurálja a következő értékeket:

- **Tulajdonosnév formátuma** – Az Intune automatikusan előtaggal egészíti ki a tanúsítvány köznapi nevét. Ez az oktatói tanúsítványoknál **leader** (vezető), illetve **member** (tag) a diáktanúsítványok esetében.
- **Hitelesítésszolgáltató:** Olyan vállalati hitelesítésszolgáltató (CA), amelyen a Windows Server 2008 R2 vagy újabb rendszer Enterprise kiadása fut. Az önálló hitelesítésszolgáltató nem támogatott. 
- **Hitelesítésszolgáltató neve** – Adja meg a hitelesítésszolgáltatója nevét.
- **Tanúsítványsablon neve** – Válassza ki annak a tanúsítványsablonnak a nevét, amely hozzá van adva egy kiállító hitelesítésszolgáltatóhoz. 
- **Megújítási küszöb (%)** – Adja meg, hogy az eszköz a tanúsítvány élettartamának hány százalékos hátralévő idejénél igényelje a tanúsítvány megújítását.
- **Tanúsítvány érvényességi időtartama** – Adja meg a tanúsítvány lejáratáig hátralévő időt.
A megadott tanúsítványsablonban meghatározott érvényességi időszaknál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet beállíthat értékként, öt évet azonban nem. Az értéknek emellett a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál is kevesebbnek kell lennie.

Miután befejezte a tanúsítványok konfigurálását, kattintson az **OK** gombra.

## <a name="finish-up"></a>Befejezés

1.  Az **Oktatás** panelen kattintson az OK gombra.
2.  A **Profil létrehozása** panelen válassza a **Létrehozás** lehetőséget.
    
Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó panelen.

Rendelje hozzá a profilt az iskolai adatok az Azure AD-vel való szinkronizálásakor létrehozott osztálytermi csoportokban található tanulói eszközökhöz (lásd: [Eszközprofilok hozzárendelése](device-profile-assign.md)).

## <a name="next-steps"></a>További lépések

Az oktatók az Osztályterem alkalmazás használatakor most már teljes hozzáféréssel rendelkeznek a diákok eszközeihez.

Az Osztályterem alkalmazással kapcsolatos további tudnivalókért lásd az [Osztályterem alkalmazás súgóját](https://help.apple.com/classroom/ipad/2.0/) az Apple webhelyén.

Ha szeretne megosztott iPad eszközöket konfigurálni a diákoknak, olvassa el [Az Intune oktatási beállításainak konfigurálása megosztott iPad eszközökhöz](education-settings-configure-ios-shared.md) szakaszt.
