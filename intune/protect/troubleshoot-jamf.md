---
title: JAMF Pro-integráció hibaelhárítása Microsoft Intune
titleSuffix: Microsoft Intune
description: Javaslatok a JAMF Pro Mac-eszközökre való integrálásával kapcsolatos leggyakoribb problémák elhárításához Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817556"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>A JAMF Pro és a Microsoft Intune integrációjának megoldása

Ez a cikk az Intune-rendszergazdáknak segít megérteni és elhárítani a JAMF Pro for macOS és az Intune integrálásával kapcsolatos problémákat.

> [!TIP]  
> A cikkben szereplő információk nagy része eredetileg a hibaelhárítás során jelent meg, [Amikor integrálja a JAMF-t](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) a support.microsoft.com-on lévő Microsoft Intuneval.

## <a name="prerequisites"></a>Előfeltételek

A hibaelhárítás megkezdése előtt gyűjtsön össze néhány alapvető információt a probléma tisztázásához és a megoldás megtalálásához szükséges idő csökkentéséhez. Ha például egy JAMF-Intune integrációval kapcsolatos problémába ütközik, mindig ellenőrizze, hogy az előfeltételek teljesültek-e. A hibaelhárítás megkezdése előtt tekintse át a következő szempontokat:

- Tekintse át a [JAMF Pro és az Intune integrálásához](conditional-access-integrate-jamf.md#prerequisites)szükséges előfeltételeket.
- Minden felhasználónak rendelkeznie kell Microsoft Intune és a Microsoft HRE Premium P1 licenccel 
- Rendelkeznie kell egy olyan felhasználói fiókkal, amely Microsoft Intune integrációs engedélyekkel rendelkezik a JAMF Pro konzolon.
- Olyan felhasználói fiókkal kell rendelkeznie, amely globális rendszergazdai engedélyekkel rendelkezik az Azure-ban.


Az Intune-nal való JAMF Pro-integráció kivizsgálása során vegye figyelembe a következő információkat: 
- Pontosan milyen hibaüzenet jelenik meg?
- Hol található a hibaüzenet?
- Mikor indult el a probléma?  Működött a JAMF Pro integrációja az Intune-nal?
- Hány felhasználót érint a rendszer? Az összes érintett felhasználó vagy csak néhány?
- Hány eszközt érint a rendszer? Minden eszköz érintett vagy csak néhány?
 

## <a name="common-problems"></a>Gyakori problémák 

Az alábbi információk segítséget nyújtanak az eszközök gyakori problémáinak azonosításában és megoldásában az Intune és a JAMF Pro-integráció beállítása után.  

| Probléma   | További információ                  |
|-----------------|--------------------------|
| **Az eszközök nem válaszoló vannak megjelölve a JAMF Pro-ban**  | [Az eszközök nem tudnak bejelentkezni a JAMF Pro vagy az Azure AD használatával](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **A Mac-eszközök akkor jelentkeznek, ha az alkalmazások megnyitásakor nem sikerül regisztrálni a kulcstartót**  | A [rendszer megkéri a felhasználókat a jelszavuk megadására, hogy lehetővé tegyék az alkalmazások számára az Azure ad-regisztrációt](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **Nem sikerült regisztrálni az eszközöket**  | A következő okokat lehet alkalmazni: <br> 1\. **@no__t – 1** [ ***OK*** – a JAMF Pro alkalmazás az Azure-ban helytelen engedélyekkel rendelkezik](#cause-1) <br> **@no__t – 1** [ ***OK 2*** – probléma van a *JAMF natív MacOS-összekötővel* az Azure ad-ben](#cause-2) <br> **@no__t – 1** [ ***OK 3*** – a felhasználónak nincs érvényes Intune-vagy JAMF-licence](#cause-3) <br> **@no__t – 1** [ ***OK 4*** – a felhasználó nem használja a JAMF önkiszolgáló szolgáltatást a céges portál alkalmazás elindításához](#cause-4) <br> **@no__t – 1** [ ***OK 5*** – az Intune-integráció ki van kapcsolva](#cause-5) <br> **@no__t – 1** [ ***OK 6*** – az eszköz korábban regisztrálva van az Intune-ban, vagy a felhasználó többször próbálta regisztrálni az eszközt](#cause-6) <br> **@no__t – 1** [ ***OK 7*** – a JamfAAD a felhasználók kulcstartójában hozzáférést kér a "Microsoft Workplace JOIN kulcshoz"](#cause-7) |
|  **A Mac-eszköz megfelel az Intune-ban, de nem megfelelő az Azure-ban** | [Eszközök regisztrálásával kapcsolatos problémák](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Ismétlődő bejegyzések jelennek meg az Intune-konzolon a JAMF használatával beléptetett Mac-eszközökhöz** | [Több regisztráció ugyanarra az eszközre](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **A megfelelőségi szabályzat nem tudja kiértékelni az eszközt** | [Házirend céljaként szolgáló eszközök csoportjai](#compliance-policy-fails-to-evaluate-the-device) |
| **Nem sikerült beolvasni Microsoft Graph API hozzáférési jogkivonatát** | A következő okokat lehet alkalmazni: <br> @no__t – 0[engedély a JAMF Pro-alkalmazáshoz az Azure-ban](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> @no__t – 0[lejárt licenc a JAMF vagy az Intune](#a-license-required-for-jamf-intune-integration-has-expired) -hoz <br> a **-** [portok nincsenek megnyitva](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Az eszközök nem válaszoló vannak megjelölve a JAMF Pro-ban  

**OK**: A JAMF Pro által nem *válaszoló* eszközök gyakori okai a következők:

- Az eszköz nem tud bejelentkezni a JAMF Pro-val.  
  A JAMF Pro 15 percenként várja az eszközök beadását. Az eszközök nem válaszolnak a JAMF, amikor egy 24 órás időszakban nem tudnak bejelentkezni.  

- Az eszköz nem tud bejelentkezni az Azure AD-be.  
  Az Azure AD-be való sikeres regisztrációt követően a macOS-eszközök Azure-tokent kapnak:
  - Ez a jogkivonat 12 óránként frissül.   
  - Ha a jogkivonat frissítése 24 órán keresztül nem sikerül, a JAMF Pro nem válaszol az eszközre.  
  - Ha az Azure-token lejár, a rendszer felszólítja a felhasználókat, hogy jelentkezzenek be az Azure-ba új jogkivonat beszerzéséhez. Az Azure-hozzáférés frissítési jogkivonata hét naponként jön létre.

**Felbontás**  
Ha egy eszköz nem *válaszol* a JAMF Pro által, az eszköz regisztrált felhasználójának be kell jelentkeznie, hogy javítsa a nem válaszoló állapotot. Annak a felhasználónak kell lennie, aki a munkahelyi fiókkal csatlakozott, mert az Intune identitása a bejelentkezési kulcstartóban van.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>A Mac-eszközök rákérdeznek a kulcstartó bejelentkezésére az alkalmazások megnyitásakor  

Miután konfigurálta az Intune-t és a JAMF Pro-integrációt, és üzembe helyezi a feltételes hozzáférési szabályzatokat, a JAMF Pro által felügyelt eszközök felhasználói megkérik a jelszót, amikor megnyitnak Microsoft Office 365 alkalmazást, például a csapatokat, az Outlookot és más Azure AD-hitelesítés. 

Például egy, az alábbi példához hasonló szöveget tartalmazó üzenet jelenik meg a Microsoft Teams megnyitásakor:

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**OK**: Ezeket az utasításokat a JAMF Pro hozza létre minden olyan alkalmazáshoz, amely Azure AD-regisztrációt igényel. 

**Megoldás**@no__t – 1  
Ha a rendszer kéri, a felhasználónak meg kell adnia az eszköz jelszavát az Azure AD-be való bejelentkezéshez. A lehetőségek a következők:
- **Megtagadás** – ne jelentkezzen be, és ne használja az alkalmazást.
- **Engedélyezés** – egyszeri bejelentkezés. Amikor az alkalmazás legközelebb megnyílik, megkéri a bejelentkezést.
- **Mindig engedélyezett** – a bejelentkezési hitelesítő adatok gyorsítótárazva lesznek az alkalmazáshoz. Amikor az alkalmazás legközelebb megnyílik, nem kéri a bejelentkezést.  

Ha a *mindig engedélyezi* , hogy egy alkalmazás csak a jövőbeli bejelentkezéshez hagyja jóvá az alkalmazást. További alkalmazások esetén a rendszer a hitelesítést is kéri, amíg a *mindig engedélyezett*értékre van állítva. Egy alkalmazás gyorsítótárazott hitelesítő adatait nem használhatja másik alkalmazás.  

### <a name="devices-fail-to-register"></a>Nem sikerült regisztrálni az eszközöket  

Számos gyakori oka van annak, hogy a Mac-eszközök nem regisztrálhatnak.  

#### <a name="cause-1"></a>OK: 1  

**Az Azure-beli JAMF Pro Enterprise-alkalmazás nem rendelkezik megfelelő engedéllyel, vagy egynél több engedéllyel rendelkezik**  

  Amikor létrehoz egy alkalmazást az Azure-ban, el kell távolítania az összes alapértelmezett API-engedélyt, majd hozzá kell rendelnie az Intune-t a *update_device_attributes*-hez. 

  **Felbontás**  
  Tekintse át és ha szükséges, javítsa ki az Azure AD-ben létrehozott JAMF alkalmazás engedélyeit. Tekintse meg az [Azure ad-beli JAMF alkalmazás létrehozásának](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory)eljárását. 

#### <a name="cause-2"></a>OK 2  

**Az **JAMF natív MacOS-összekötő** alkalmazás nem lett létrehozva az Azure ad-bérlőben, vagy az összekötő beleegyezett abba, hogy olyan fiók írta alá, amely nem rendelkezik globális rendszergazdai jogokkal**  

  **Felbontás**  
  Tekintse meg a *MacOS Intune-integráció konfigurálása* című szakaszt a [Microsoft Intune integrációja](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) a docs.JAMF.com-ben című témakörben. 

#### <a name="cause-3"></a>3\. ok

**A felhasználónak nincs érvényes Intune-vagy JAMF-licence**  

  Az érvényes licenc hiánya a következő hibához vezethet, ami azt jelzi, hogy a JAMF-licenc lejárt:  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Felbontás**
  - JAMF-licenc: Kérje a JAMF segítségét a JAMF új licencének beszerzéséhez.  
  - Intune-licenc: Rendelje hozzá a felhasználót egy érvényes licenchez, vagy forduljon a Microsofthoz vagy a partnerhez az aktuális licenc beszerzésével kapcsolatos információkért.

#### <a name="cause-4"></a>4\. ok  

**A felhasználó nem használja a *JAMF önkiszolgáló szolgáltatást* a céges portál alkalmazás elindításához**

Ahhoz, hogy egy eszköz sikeresen regisztrálja és regisztrálja az Intune-t a JAMF-on keresztül, a felhasználónak a JAMF önkiszolgáló eszköz használatával kell megnyitnia a Intune Céges portál. Ha a felhasználó manuálisan nyitja meg a vállalati portált, az eszköz regisztrál és regisztrál a JAMF-kapcsolat nélkül.  

Annak megállapításához, hogy az eszköz regisztrálása és regisztrálása milyen szolgáltatást használ, tekintse meg a Céges portál alkalmazást az eszközön. A JAMF-on keresztüli regisztráláskor értesítést kell kapnia az önkiszolgáló alkalmazás megnyitásához a módosítások elvégzéséhez.

A Céges portál alkalmazásban előfordulhat, hogy a felhasználó **`Not registered`** , és az alábbi példához hasonló bejegyzés jelenhet meg a céges portál naplókban:  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Felbontás**  
A regisztrációs forrás módosítása az Intune-ból a JAMF:
1. [A MacOS-eszköz regisztrációjának törlése az Intune-ból](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Az Intune-ból nem teljesen eltávolított eszközökre vonatkozó további szövődmények elkerüléséhez lásd: [*6. ok*](#cause-6) az okok listájában.  

2. Az eszközön a JAMF önkiszolgáló elemre kattintva nyissa meg a Céges portál alkalmazást, majd regisztrálja az eszközt az Intune-nal. Ehhez a feladathoz a [JAMF használatával kell telepítenie a MacOS-hez készült céges portál alkalmazást](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro), és létre kell hoznia [egy szabályzatot a JAMF Pro-ban, amely regisztrálja a felhasználók eszközét az Azure ad-ben](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. Amikor megnyílik a portál, megjelenik az első képernyő, amely felszólítja, hogy jelentkezzen be. Munkahelyi vagy iskolai fiók használata  

4. A Céges portál megerősíti a fiókadatok adatait, és megjeleníti az eszközök regisztrálását és az eszközök megfelelőségi állapotát. Sárga háromszögek hívják fel a figyelmet a macOS-eszköz iskolai vagy munkahelyi használatának biztonságossá tételéhez szükséges lépéseket. Kattintson a BEGIN (Kezdés) gombra a regisztráció megkezdéséhez.  

5. Ha a rendszer kéri, írja be a számítógép bejelentkezési adatait.  
     
Az eszköz felügyeleti regisztrálása eltarthat néhány percig. Ezalatt végezhet egyéb műveleteket az eszközén. A vállalati hozzáférés beállításának befejezése után megjelenő üzenet a folyamat lezárásáról tájékoztatja.

#### <a name="cause-5"></a>5\. ok  

**Az Intune-integráció ki van kapcsolva**

Ha az Intune-integráció ki van kapcsolva, a felhasználók egy előugró ablakot kapnak a Céges portál a következő üzenettel, amikor megpróbálnak regisztrálni egy eszközt:  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

A JAMF Pro-kiszolgáló egy impulzust küld az Intune-kiszolgálókra, ha az integráció ki van kapcsolva, amely tájékoztatja az Intune-t, hogy az integráció le van tiltva. 

**Felbontás**  
Engedélyezze újra az Intune-integrációt a JAMF Pro-n belül. Lásd: [Microsoft Intune integráció konfigurálása a JAMF Pro-ban](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>6. ok  

**Az eszköz korábban regisztrálva van az Intune-ban, vagy a felhasználó többször próbálta regisztrálni az eszközt**

Ha egy eszköz regisztrációja megszűnik a JAMF-ból, de nem távolítja el megfelelően az Intune-ból, vagy több regisztrációs kísérlet történik, előfordulhat, hogy a portálon ugyanaz az eszköz több példánya is megjelenik. Ennek hatására a JAMF-regisztráció sikertelen lesz.

**Felbontás**  
1. A Mac számítógépen indítsa el a **terminált**.
2. Futtassa a **sudo JAMF removemdmprofile**.
3. Futtassa a **sudo JAMF removeFramework**.
4. A JAMF Pro-kiszolgálón törölje a számítógép leltározási rekordját.
5. Törölje az eszközt a AzureAD-ből.
6. Ha létezik, törölje a következő fájlokat az eszközön:
   - /Library/Application Support-támogatás/com. microsoft. CompanyPortal. UserContext. info
   - /Library/Application Support-támogatás/com. microsoft. CompanyPortal
   - /Library/Application Support-támogatás/com. jamfsoftware. selfservice. Mac
   - /Library/Saved-alkalmazás
   - State/com. jamfsoftware. selfservice. Mac. savedState
   - /Library/Saved alkalmazás állapota/com. microsoft. CompanyPortal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/cookie-k/com. microsoft. CompanyPortal. binarycookies
   - /Users/<username>/Library/cookie-k/com. JAMF. Management. jamfAAD. binarycookies
   - com. microsoft. CompanyPortal
   - com. microsoft. CompanyPortal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft munkamenet-átviteli kulcs (nyilvános és titkos kulcsok)
   - Microsoft Workplace Join kulcs (nyilvános és titkos kulcsok)
7. Távolítson el bármit a *Microsoftra*, *Intune*-ra vagy *céges portálra*hivatkozó eszköz kulcstartóján, beleértve a DeviceLogin.microsoft.com tanúsítványokat is. Távolítsa el a *JAMF* -hivatkozásokat, kivéve a nyilvános és a titkos kulcs JAMF. 
   > [!IMPORTANT]  
   > A nyilvános és a titkos kulcs eltávolítása megszakítja az eszközök regisztrálását.

8. Törölje a következő bejegyzések bármelyikét:  
   - Típusú Alkalmazás jelszava; Fiók: com. microsoft. workplacejoin. ujjlenyomat
   - Típusú Alkalmazás jelszava; Fiók: com. microsoft. workplacejoin. registeredUserPrincipalName
   - Típusú Tanúsítvány Kiállító: MS-Organization-Access
   - Típusú Identitás-beállítások; Név (ADFS STS URL-címe, ha van): https://adfs\<DNSName>.com/adfs/ls
   - Típusú Identitás-beállítások; Név: @no__t – 0
   - Típusú Identitás-beállítások; Név: @no__t – 0  
9. Indítsa újra a Mac-eszközt.
10. Céges portál eltávolítása az eszközről.
11. Nyissa meg a portal.manage.microsoft.com, és törölje a Mac-eszköz összes példányát. Várjon legalább 30 percet, mielőtt a következő lépéshez ugorjon.
12. Regisztrálja újra az eszközt a JAMF Pro-ban.
13. Nyissa meg újra az önkiszolgáló szolgáltatást, és indítsa el a regisztrációs szabályzatot.


#### <a name="cause-7"></a>7\. ok  

**A JamfAAD a "Microsoft Workplace Join Key" hozzáférést kéri a felhasználók kulcstartójában**

A regisztráció során a macOS-eszköz felhasználója a következő üzenetet kapja, amely lehetővé teszi a JamfAAD hozzáférését a kulcstartóból: 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Felbontás**  
Az eszköz Azure AD-vel való sikeres regisztrálásához a JAMF-nek a felhasználónak meg kell adnia a fiók jelszavát, és az **Engedélyezés**lehetőséget kell választania.

Ez a kérelem hasonló a Mac-eszközökre vonatkozó kérelemhez, amely a jelen cikk korábbi részében a [kulcstartó bejelentkezését kéri](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app).  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>A Mac-eszköz megfelel az Intune-ban, de nem megfelelő az Azure-ban  

**OK**: Az alábbi feltételek azt okozhatják, hogy az eszköz megfelelőként jelenjen meg az Intune-ban, de nem felel meg az Azure-ban:  
- Az eszköz nincs megfelelően regisztrálva.  
- Az eszköz többször is regisztrálva van a szükséges tisztítás nélkül.

**Felbontás**  
A probléma megoldásához kövesse az *eszközök*6. [*okának*](#cause-6) feloldását a cikk korábbi részében. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Ismétlődő bejegyzések jelennek meg az Intune-konzolon a JAMF használatával beléptetett Mac-eszközökhöz  
 
**OK**: Egy eszköz többször van regisztrálva az Intune-ban, általában az Intune-ból való eltávolítás után.  

Ha eltávolítanak egy eszközt az Intune-ból, és JAMF a Pro-integrációt, egyes adatok lemaradnak, ami egymást követő regisztrációkat eredményezhet ismétlődő bejegyzések létrehozásához.  

**Felbontás**  
A probléma megoldásához kövesse az *eszközök*6. [*okának*](#cause-6) feloldását a cikk korábbi részében. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>A megfelelőségi szabályzat nem tudja kiértékelni az eszközt  

**OK**: A JAMF és az Intune közötti integráció nem támogatja az erőforráscsoportok megkeresésére vonatkozó megfelelőségi szabályzatot. 

**Felbontás**  
A felhasználói csoportokhoz hozzárendelni kívánt macOS-eszközök megfelelőségi szabályzatának módosítása. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Nem sikerült beolvasni Microsoft Graph API hozzáférési jogkivonatát

A következő hibaüzenetet kapja:

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

A hiba forrása a következő okok egyike lehet: 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Probléma van a JAMF Pro alkalmazással az Azure-ban

A JAMF Pro-alkalmazás Azure-ban való regisztrálásakor a következő feltételek egyike történt:  
- Az alkalmazás egynél több engedélyt kapott.
- A **rendszergazdai jóváhagyás megadása *@no__t – 2your vállalati >***  beállítás nem lett kiválasztva.  

**Felbontás**  
Tekintse meg a cikk korábbi, 1. okának feloldását az [eszközök regisztrálásához](#devices-fail-to-register).

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>A JAMF-Intune-integrációhoz szükséges licenc lejárt

**Feloldási**: Tekintse meg a 3. ok feloldását az [eszközök nem regisztrálhatnak](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>A szükséges portok nincsenek megnyitva a hálózaton

**Feloldási**: Tekintse át a hálózati portok információit a JAMF Pro Intune-nal való integrálásának [előfeltételei](conditional-access-integrate-jamf.md#prerequisites) között.


## <a name="next-steps"></a>További lépések
További információ a [JAMF Pro és az Intune integrálásáról](conditional-access-integrate-jamf.md)