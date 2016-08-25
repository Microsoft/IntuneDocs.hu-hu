---
# required metadata

title: Az Exchange Online-hoz és az új dedikált Exchange Online-hoz való e-mail hozzáférés korlátozása | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az Exchange Online-hoz és az új dedikált Exchange Online-hoz való e-mail hozzáférés korlátozása

Ha dedikált Exchange Online-környezettel rendelkezik, és szeretné tudni, hogy az új vagy az örökölt konfiguráció tartozik-e hozzá, lépjen kapcsolatba a fiókkezelővel.

Az Exchange Online-hoz vagy az új dedikált Exchange Online-környezethez való e-mail-hozzáférés konfigurálásához az Intune-ban konfiguráljon feltételes hozzáférést az Exchange Online-hoz.
Ha szeretné jobban megismerni a feltételes hozzáférés működését, olvassa el [Az e-mailek és az O365-szolgáltatások elérésének korlátozása](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) című cikket.

>[!IMPORTANT]
>A modern hitelesítést használó alkalmazásokat működtető számítógépek és Windows 10 Mobile rendszerű eszközök esetében a feltételes hozzáférés jelenleg nem érhető el az összes Intune-ügyfél számára. Ha már használja ezeket a funkciókat, nincs teendője. Továbbra is használhatja őket.

>Ha nem hozott létre feltételes hozzáférési szabályzatokat a modern hitelesítést használó alkalmazásokat működtető számítógépekhez vagy Windows 10 Mobile rendszerű eszközökhöz, kérelmet kell küldenie.  A [Microsoft Connect webhelyen](http://go.microsoft.com/fwlink/?LinkId=761472) részletes tájékoztatást talál az ismert problémákról, valamint a funkció elérésének módjáról.

**Mielőtt** konfigurálja a feltételes hozzáférést, meg kell felelnie a következő előfeltételeknek:

-   Rendelkeznie kell egy olyan **Office 365-előfizetéssel, amely tartalmazza az Exchange Online-t (például E3)**, és a felhasználóknak licenccel kell rendelkezniük az Exchange Online-hoz.

-  Fontolja meg a választható **Microsoft Intune szolgáltatások közötti összekötő** beállítását, amely az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-t a Microsoft Exchange Online-hoz csatlakoztatja, és segít Önnek az eszközinformációk kezelésében az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] konzolján keresztül. Feltételes házirendek vagy feltételes hozzáférési házirendek használatához nincs szükség az összekötő használatára, szükség van rá azonban az olyan jelentések futtatásához, amelyek segítenek a feltételes hozzáférés hatásának vizsgálatában.

   > [!NOTE] Ne konfigurálja a szolgáltatások közötti összekötőt, ha feltételes hozzáférést szeretne használni az Exchange Online-hoz és a helyszíni Exchange-hez is.

   Az összekötő konfigurálásának ismertetését lásd: [Intune szolgáltatások közötti összekötő](intune-service-to-service-exchange-connector.md).

Amikor feltételes hozzáférési szabályzatokat konfigurál és rendel hozzá felhasználókhoz, a felhasználók csak akkor csatlakozhatnak az e-mail fiókjukhoz, ha a használt **eszköz**:

-   **Regisztrálva** van az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal vagy egy tartományhoz csatlakozó számítógép.

-  **Regisztrálva van az Azure Active Directoryban**. Ez automatikusan megtörténik, amikor az eszköz regisztrálva van az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal. Ezenkívül az ügyfél Exchange ActiveSync-azonosítójának regisztrálva kell lennie az Azure Active Directoryban.

  Az AAD DRS szolgáltatás automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azok az ügyfelek, akik már telepítették az ADFS eszközregisztrációs szolgáltatását, nem fogják látni a regisztrált eszközöket a helyszíni Active Directoryban.

-   **Megfelel** az eszközre telepített minden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] megfelelőségi szabályzatnak, vagy tartományhoz van csatlakoztatva egy helyszíni tartományban.

Ha a feltételes hozzáférési szabályzat valamelyik feltétele nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:

- Ha az eszköz nincs regisztrálva az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ban vagy az Azure Active Directoryban, megjelenik egy üzenet, amely leírja, hogyan kell telepíteni a Vállalati portál alkalmazást, regisztrálni az eszközt és aktiválni az e-mailt. Ez a folyamat hozzárendeli az eszköz Exchange ActiveSync-azonosítóját is az Azure Active Directoryban lévő rekordhoz.

-   Ha az eszköz nem felel meg a megfelelőségi szabályzat előírásainak, egy üzenet jelenik meg, amely a végfelhasználót az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] vállalati portál webhelyére vagy a Vállalati portál alkalmazásba irányítja, ahol a felhasználó további információt talál a problémáról és annak megoldásáról.


Az alábbi ábra az Exchange Online feltételes hozzáférési szabályzatai által használt folyamatot szemlélteti.

![Az eszközök hozzáférésének engedélyezését vagy letiltását meghatározó döntési pontokat bemutató ábra](../media/ConditionalAccess8-1.png)

## A mobileszközök támogatása
Korlátozhatja az Exchange Online e-mailjeinek az **Outlook** alkalmazásból és a **modern hitelesítést használó más alkalmazásokból** történő elérését:

- Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0-s és újabb verziók
- iOS 7.1-es és újabb verziók
- Windows Phone 8.1 és újabb verziók

 A **modern hitelesítéssel** Active Directory Authentication Library-alapú (ADAL-alapú) bejelentkezés biztosítható a Microsoft Office-ügyfelekhez.

> -   Az ADAL-alapú hitelesítéssel az Office-ügyfelek végezhetnek böngészőalapú hitelesítést (más néven passzív hitelesítést).  A hitelesítéshez a felhasználó egy bejelentkezési weblapra van átirányítva. Ez az új bejelentkezési módszer nagyobb biztonságot tesz lehetővé, például a **többtényezős hitelesítéssel** és a **tanúsítványalapú hitelesítéssel**. A korszerű hitelesítés működéséről ebben a [cikkben](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) olvashat további információkat.


A következő platformokon korlátozhatja az Exchange e-mail fiókok elérését a beépített **Exchange ActiveSync levelezési ügyfélről**:

- Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0-s és újabb verziók

- iOS 7.1-es és újabb verziók

- Windows Phone 8.1 és újabb verziók

## Számítógépek támogatása

Az asztali Office-alkalmazásokat futtató számítógépekhez beállíthatja az **Exchange Online** és a **SharePoint Online** feltételes hozzáférését, ha a számítógépek megfelelnek az alábbi követelményeknek:

-   A számítógépen Windows 7.0 vagy Windows 8.1 operációs rendszernek kell futnia.

-   A számítógépnek tartományhoz kell csatlakoznia, vagy meg kell felelnie a megfelelőségi szabályzat előírásainak.

    A megfelelőség biztosításához a számítógépet regisztrálni kell az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ban, és meg kell felelnie a szabályzatoknak.

    Tartományhoz csatlakozó számítógépek esetén be kell állítani az [eszköz automatikus regisztrációját](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) az Azure Active Directoryban.

-   Az [Office 365 modern hitelesítésének engedélyezve kell lennie](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), és a számítógépre telepíteni kell az Office legújabb frissítéseit.

    A modern hitelesítéssel Active Directory Authentication Library-alapú (ADAL-alapú) bejelentkezés biztosítható az Office 2013 Windows-ügyfelein, és jobb biztonságot kínál, többek között a **többtényezős hitelesítéssel** és a **tanúsítványalapú hitelesítéssel**.

-   Állítsa be az ADFS-jogcímszabályokat a nem modern hitelesítési protokollok blokkolására. Lépésenkénti útmutatás: 3. forgatókönyv – [Az O365-höz való hozzáférés teljes letiltása a böngészőalapú alkalmazások kivételével](https://technet.microsoft.com/library/dn592182.aspx).

## Feltételes hozzáférés konfigurálása
### 1. lépés: Megfelelőségi szabályzat konfigurálása és telepítése
[Hozza létre](create-a-device-compliance-policy-in-microsoft-intune.md) és [telepítse](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) a megfelelőségi szabályzatot azon felhasználói csoportok számára, amelyekre érvényes lesz a feltételes hozzáférési szabályzat is.


> [!IMPORTANT] Ha nem állított be megfelelőségi szabályzatot, akkor az eszközök megfelelőnek minősülnek, és engedélyezve lesz az Exchange-hez való hozzáférésük.

### 2. lépés: A feltételes hozzáférési szabályzat hatásának értékelése
A feltételes hozzáférési szabályzat konfigurálása után a **Mobileszközkészlet-jelentések** használatával azonosíthatja azokat az eszközöket, amelyek Exchange-hozzáférése le van tiltva.

Ehhez konfiguráljon kapcsolatot a(z) [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] és az Exchange között a [Microsoft Intune szolgáltatások közötti összekötő](intune-service-to-service-exchange-connector.md) használatával.
1.  Keresse meg a **Jelentések -> Mobileszközkészlet-jelentések** területet.
![Képernyőfelvétel a Mobileszközkészlet-jelentés oldalról](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  A jelentés paramétereiben válassza ki az értékelni kívánt [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-csoportot és szükség esetén azon eszközplatformokat, amelyekre alkalmazza a szabályzatot.
3.  A szervezet igényeinek megfelelő feltételek kiválasztása után válassza a **Jelentés megtekintése** lehetőséget.
A Jelentésmegjelenítő egy új ablakban nyílik meg.
![Képernyőfelvétel egy mobileszközkészlet-jelentésről](../media/IntuneSA2cViewReport.PNG)

A jelentés futtatása után vizsgálja meg a következő négy oszlopot annak meghatározásához, hogy a felhasználók le lesznek-e tiltva:

-   **Kezelési csatorna** – Jelzi, hogy az eszközt az Intune, az Exchange ActiveSync vagy mindkettő kezeli.

-   **Az AAD-ben regisztrált** – Jelzi, hogy az eszköz regisztrálva van-e az Azure Active Directoryban (vagyis munkahelyi csatlakoztatással).

-   **Megfelelő** – Jelzi, hogy az eszköz megfelel-e a telepített megfelelőségi házirendeknek.

-   **Exchange ActiveSync-azonosító** – Az iOS- és Android-eszközök Exchange ActiveSync-azonosítójának társítva kell lennie az Azure Active Directoryban található eszközregisztrációs rekorddal. Ez akkor történik meg, amikor a felhasználó a **Levelezés aktiválása** hivatkozásra kattint a karanténba helyezett e-mailben.

    > [!NOTE] Windows Phone-telefonok esetén ebben az oszlopban mindig szerepel valamilyen érték.

A célcsoporthoz tartozó eszközök Exchange-hozzáférése le lesz tiltva, ha az oszlop értékei nem egyeznek a következő táblázatban lévő értékekkel:

--------------------------
|Kezelési csatorna|Az AAD-ben regisztrált|Compliant (Megfelelő)|Exchange ActiveSync-azonosító|Eredményművelet|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**A Microsoft Intune és az Exchange ActiveSync kezeli**|Igen|Igen|Érték jelenik meg|Az e-mail hozzáférés engedélyezett|
|Bármely más érték|Nem|Nem|Nem jelenik meg érték|Az e-mail hozzáférés le van tiltva|
----------------------
Exportálhatja a jelentés tartalmát, és az **E-mail cím** oszlop segítségével értesítheti a felhasználókat arról, hogy le lesznek tiltva.

### 3. lépés: Felhasználói csoportok konfigurálása a feltételes hozzáférési szabályzathoz
A feltételes hozzáférési szabályzatokkal a felhasználók különböző Azure Active Directory biztonsági csoportjai célozhatók meg. Ezenkívül meghatározott felhasználói csoportok mentesíthetők is a szabályzat alól.  Amikor egy felhasználóra házirend vonatkozik, az általa használt összes eszköznek megfelelőnek kell lennie az e-mailek eléréséhez.

Ezeket a csoportokat az **Office 365 Felügyeleti központban**vagy az **Intune-fiókportálon**konfigurálhatja.

Minden házirendben két csoporttípust adhat meg:

-   **Megcélzott csoportok** – Azon felhasználói csoportok, amelyekre a szabályzat érvényes.

-   **Kivétel alá eső csoportok** – Azon felhasználói csoportok, amelyek mentesülnek a házirend alól (választható)

Ha egy felhasználó mindkét csoportban szerepel, mentesül a házirend alól.

Csak a feltételes hozzáférési szabályzat által célzott csoportokat értékeli ki a rendszer.

### 4. lépés: A feltételes hozzáférési szabályzat konfigurálása

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) válassza a **Házirend** > **Feltételes hozzáférés** > **Exchange Online-szabályzat** elemet.
![Képernyőfelvétel az Exchange Online feltétes hozzáférési szabályzatának oldaláról](../media/IntuneSA5dExchangeOnlinePolicy.png)

2.  Az **Exchange Online-szabályzat** lapon válassza a **Feltételes hozzáférési házirend engedélyezése Exchange Online-hoz**lehetőséget.

    > [!NOTE] Amennyiben nem állított be megfelelőségi szabályzatot, a rendszer megfelelőnek tekinti az eszközöket.
    >
    > A megfelelőségi állapottól függetlenül a szabályzat által megcélzott összes felhasználónak regisztrálnia kell az eszközét a következővel: [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  Az **Alkalmazás-hozzáférés** beállításnál két módszer közül választhat annak megadásához, hogy a szabályzat melyik platformokra lesz érvényes a modern hitelesítést használó alkalmazások esetében. A támogatott platformok a következők: Android, iOS, Windows és Windows Phone.

    -   **Összes platform**

        Ha ezt a beállítást szeretné használni, az **Exchange Online** elérésére használt összes eszköznek regisztrálva kell lennie az Intune-ban, és meg kell felelnie a szabályzatoknak.  Bármely, **modern hitelesítést** használó ügyfélalkalmazás a feltételes hozzáférési szabályzat hatálya alá tartozik, ha pedig az adott platformot az Intune jelenleg nem támogatja, az **Exchange Online** elérése le lesz tiltva.
        >[!TIP]
           Lehet, hogy nem látja ezt a beállítást, ha még nem használ feltételes hozzáférést a számítógépekhez.  Használja helyette az **Adott platformok** beállítást. A feltételes hozzáférés a számítógépek esetében jelenleg nem áll rendelkezésre az összes Intune-ügyfél számára.   A [Microsoft Connect webhelyen](http://go.microsoft.com/fwlink/?LinkId=761472) részletes tájékoztatást talál az ismert problémákról, valamint a funkció elérésének módjáról.

    -   **Megadott platformok**

         Minden, a **modern hitelesítést** használó ügyfélalkalmazás a feltételes hozzáférési szabályzat hatálya alá tartozik a kiválasztott eszközplatformokon.

4.  Az **Exchange ActiveSync-alkalmazások** beállításnál megadhatja a nem megfelelő eszközök Exchange Online-hozzáférésének letiltását. Azt is kiválaszthatja, hogy engedélyezi vagy letiltja az e-mailek elérését, amikor az eszköz nem támogatott platformmal működik. A támogatott platformok a következők: Android, iOS, Windows és Windows Phone.


5.  A **Megcélzott csoportok**területen válassza ki azon felhasználók Active Directory biztonsági csoportjait, akikre érvényes a házirend. Az összes felhasználót vagy a felhasználói csoportok egy kiválasztott listáját is megadhatja.
![Képernyőfelvétel az Exchange Online feltételes hozzáférési szabályzatának oldaláról, valamint a megcélzott és a kivétel alá eső csoportok beállításairól](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE] A **Megcélzott csoportok** listán lévő felhasználók esetében az Intune-szabályzatok leváltják az Exchange-szabályokat és -szabályzatokat.
    >
    > Az Exchange csak a következő esetekben érvényesíti az engedélyezési, blokkolási és karanténba helyezési Exchange-szabályokat és az Exchange-szabályzatokat:
    >
    > -   A felhasználó nem rendelkezik Intune-licenccel.
    > -   A felhasználó rendelkezik Intune-licenccel, de egy, a feltételes hozzáférési házirendben megcélzott biztonsági csoportnak sem tagja.

6.  A **Kivétel alá eső csoportok**területen válassza ki azon felhasználók Active Directory biztonsági csoportjait, akikre nem érvényes a házirend. Ha egy felhasználó a megcélzott és a mentesített csoportban is szerepel, mentes a házirend alól.

7.  Ha elkészült, válassza a **Mentés** elemet.

-   Nem kell telepítenie a feltételes hozzáférési házirendet, azonnal érvénybe lép.

-   Miután egy felhasználó e-mail fiókot hoz létre, azonnal letiltja az eszközt.

-   Ha egy letiltott felhasználó regisztrálja az eszközt az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ban, a rendszer 2 percen belül feloldja az e-mail elérés letiltását.

-   Ha a felhasználó megszünteti az eszköz regisztrációját, a rendszer körülbelül 6 óra múlva letiltja az e-maileket.

**Ha szeretne arra vonatkozó példákat megtekinteni, hogy hogyan konfigurálhat feltételes hozzáférési szabályzatot az eszközök hozzáférésének korlátozásához, olvassa el [az e-mail-hozzáférés korlátozását bemutató példák](restrict-email-access-example-scenarios.md) leírását.**

## A megfelelőség és a feltételes hozzáférési házirendek megfigyelése

#### Az Exchange szolgáltatásból kitiltott eszközök megtekintése

Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] irányítópultján kattintson **Az Exchange szolgáltatásból kitiltott eszközök** csempére a letiltott eszközök számát és további információkat megjelenítő hivatkozások megtekintéséhez.
![Képernyőfelvétel az Intune irányítópultjáról és azokról az eszközökről, amelyek Exchange-hozzáférése le van tiltva](../media/IntuneSA6BlockedDevices.PNG)

## További lépések
[A SharePoint Online-hoz való hozzáférés korlátozása](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[A Skype Vállalati online verzióhoz való hozzáférés korlátozása](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


