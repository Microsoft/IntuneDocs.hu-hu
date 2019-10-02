---
title: Titkosítási jelentés a Microsoft Intune titkosított eszközeihez
titleSuffix: Microsoft Intune
description: Megtekintheti az iOS-vagy Windows-eszközök titkosítási állapotát, valamint a FileVault és a BitLocker helyreállítási kulcsait a Microsoft Intune-portálon keresztül érheti el.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c123de600d91f2ba44f9ae728d7f21c8adebed25
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732379"
---
# <a name="monitor-device-encryption-with-intune"></a>Az eszközök titkosításának figyelése az Intune-nal   

A Microsoft Intune titkosítási jelentés központi hely az eszköz titkosítási állapotának részleteinek megtekintéséhez és az eszköz helyreállítási kulcsainak kezeléséhez szükséges beállítások megkereséséhez. A rendelkezésre álló helyreállítási kulcs beállításai a megtekintett eszköz típusától függenek.  

A jelentés megkereséséhez jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és lépjen az **eszköz konfigurálása**elemre, majd a *figyelés*területen válassza a **titkosítási jelentés**elemet.  

## <a name="view-encryption-details"></a>Titkosítási adatok megtekintése  

A titkosítási jelentés a felügyelt támogatott eszközök általános részleteit jeleníti meg. A következő szakaszokban részletesen ismertetjük az Intune által a jelentésben bemutatott információk részleteit.  
 
### <a name="prerequisites"></a>Előfeltételek:  

A titkosítási jelentés támogatja a jelentéskészítést a következő operációsrendszer-verziókat futtató eszközökön:  
- macOS 10,13 vagy újabb verzió  
- Windows 1607 vagy újabb verzió  

### <a name="report-details"></a>Jelentés részletei  

A titkosítási jelentés panel megjeleníti az eszközök magas szintű részleteivel kezelt eszközök listáját. Kiválaszthat egy eszközt a listából a részletezéshez, és további részleteket jeleníthet meg az eszközök [eszköz titkosítása állapot](#device-encryption-status) ablaktáblán.  

- **Eszköznév** – az eszköz neve.  
- **Operációs rendszer** – az eszköz platformja, például Windows vagy MacOS.  
- **Operációs rendszer verziója** – a Windows vagy MacOS verziója az eszközön.  
- **TPM-verzió** *(Csak a Windows 10 rendszerre vonatkozik)* – a Windows 10-es eszközön lévő PLATFORMMEGBÍZHATÓSÁGI modul (TPM) lapka verziója.  
- **Titkosítási készültség** – az eszközök kiértékelése a megfelelő titkosítási technológiák, például a BitLocker vagy a FileVault titkosítás támogatásához. Az eszközök azonosítása a következőképpen történik:  
  - **Kész**: Az eszköz MDM házirenddel titkosítható, amelyhez az eszköznek az alábbi követelményeknek kell megfelelnie:  
    
    **MacOS-eszközök esetén**:  
    - MacOS 10,13 vagy újabb verzió  
    
    **Windows 10-es eszközök esetén**:  
    - Az 1703-es vagy újabb verzió, az *üzleti*, a *vállalati*, az *oktatási*vagy a 1809-es vagy újabb verziójának verziója  
    - Az eszközön TPM-lapka szükséges  
    
    További információ: a Windows dokumentációjában található [BitLocker konfigurációs szolgáltató (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) .  

  - **Nem áll készen**: Az eszköz nem rendelkezik teljes titkosítási képességekkel, de továbbra is támogatja a titkosítást. Előfordulhat például, hogy egy Windows-eszközt manuálisan, egy felhasználó vagy egy olyan Csoportházirend használatával titkosít, amely lehetővé teszi a titkosítást TPM nélkül.
  - **Nem alkalmazható**: Nincs elegendő információ az eszköz besorolásához.  

- **Titkosítási állapot** – azt határozza meg, hogy az operációsrendszer-meghajtó titkosítva van-e.  

- **Egyszerű felhasználónév** – az eszköz elsődleges felhasználója.  

### <a name="device-encryption-status"></a>Eszköz titkosítási állapota  

Amikor kijelöl egy eszközt a titkosítási jelentésből, az Intune megjeleníti az **eszköz titkosítási állapota** ablaktáblát. Az ablaktábla a következő adatokat tartalmazza:  

- **Eszköz neve** – a megtekintett eszköz neve.  

- **Titkosítási készültség** – az eszközök kiértékelése felkészültséget nyújt a titkosítás támogatásához a Mdm szabályzaton keresztül.  
  
  Példa: Ha egy Windows 10-es eszköz készültsége *nem áll készen*, akkor is támogatja a titkosítást. Ahhoz, hogy a *kész* megjelölés megtörténjen, a Windows 10-es ESZKÖZnek TPM-lapka kell lennie. A titkosítás támogatásához TPM-chipek nem szükségesek. (További információ: *titkosítási készültség* az előző szakaszban.)  

- **Titkosítási állapot** – azt határozza meg, hogy az operációsrendszer-meghajtó titkosítva van-e. Akár 24 óráig is eltarthat, amíg az Intune jelentést tud készíteni az eszköz titkosítási állapotáról vagy az adott állapot változásáról. Ez az idő magában foglalja az operációs rendszer titkosításának idejét, valamint azt, hogy az eszköz Mikor jelentsen vissza az Intune-nak.  

  A FileVault titkosítási állapot jelentésének felgyorsításához, mielőtt az eszköz bejelentkezik, a felhasználók a titkosítás befejeződése után szinkronizálják az eszközeiket.  

- **Profilok** – az eszközre érvényes, az eszközhöz tartozó *konfigurációs* profilok listája, és a következő értékekkel vannak konfigurálva:  

  - macOS:
    - Profil típusa = *Endpoint Protection*  
    - Beállítások > FileVault > FileVault = *enable*

  - Windows 10:
    - Profil típusa = *Endpoint Protection*  
    - Beállítások > Windows-titkosítási > eszközök titkosítása = *kötelező*  

  A profilok listáját használva azonosíthatja az egyes házirendeket, hogy a *profil állapotának összegzése* problémákat jelez-e.  

- **Profil állapotának összegzése** – az eszközre érvényes profilok összegzése. Az összefoglalás a legkevésbé kedvező feltételt jelöli a megfelelő profilok között. Ha például a különböző profilok közül csak egy jelenik meg, akkor a *profil állapota összefoglaló* *hibaüzenetet*jelenít meg.  
  
  Az állapot további részleteinek megtekintéséhez nyissa meg az **Intune** > -**eszköz konfigurációs** > **profiljait**, és válassza ki a profilt. Szükség esetén kiválaszthatja az **eszköz állapotát** , majd kiválaszthat egy eszközt.  

- **Állapotadatok** – részletes információk az eszköz titkosítási állapotáról.  

  > [!IMPORTANT]  
  > Windows 10-es eszközök esetén az Intune csak a *Windows 10 április 2019* -es vagy újabb verzióját futtató eszközök *állapotának adatait* jeleníti meg.  
  
  Ebben a mezőben az egyes észlelt hibákra vonatkozó információk láthatók. Ezekkel az információkkal megtudhatja, hogy az eszköz miért nem áll készen a titkosításra.  

  Az alábbi példák az Intune által jelentett állapot részleteire mutatnak:  
  
  **MacOS**:
  - A helyreállítási kulcsot még nem sikerült lekérdezni és tárolni. Legvalószínűbb, hogy az eszköz nem lett zárolva, vagy nincs bejelölve.  
 
    *Úgy Ez az eredmény nem feltétlenül jelent hibát, hanem ideiglenes állapotot, amelynek oka az lehet, hogy az eszközön a titkosítási kérelem elküldése előtt be kell állítani a helyreállítási kulcsokra vonatkozó letéti időt. Ez az állapot azt is jelezheti, hogy az eszköz zárolva marad, vagy az Intune-nal nem ellenőrizte az utóbbi időben. Végül, mivel a FileVault titkosítás nem indul el, amíg egy eszköz be nem töltődik (töltés), lehetséges, hogy a felhasználó olyan eszköz helyreállítási kulcsát kapja, amely még nincs titkosítva*.  

  - A felhasználó késlelteti a titkosítást, vagy jelenleg a titkosítás folyamatban van.  
 
    *Úgy Vagy a felhasználó még nem jelentkezett be a titkosítási kérelem kézhezvétele után, ami szükséges ahhoz, hogy a FileVault titkosítsa az eszközt, vagy ha a felhasználó manuálisan visszafejti az eszközt. Az Intune nem tudja megakadályozni, hogy a felhasználó visszafejtse eszközét.*  

  - Az eszköz már titkosítva van. A folytatáshoz az eszköz felhasználójának vissza kell fejtenie az eszközt.  
 
    *Úgy Az Intune nem tudja beállítani a FileVault olyan eszközön, amely már titkosítva van. Ehelyett a felhasználónak manuálisan kell visszafejtenie az eszközét, mielőtt az eszköz-konfigurációs szabályzattal és az Intune*-nal tudja felügyelni. 
 
  - A FileVault a felhasználónak jóvá kell hagynia a felügyeleti profilt MacOS Catalina és újabb verziókban.  
 
    *Úgy A MacOS 10,15-as (Catalina) verziótól kezdődően a felhasználó által jóváhagyott regisztrációs beállítások azt a követelményt eredményezhetik, hogy a felhasználók manuálisan hagyják jóvá a FileVault titkosítást. További információ: [felhasználó által jóváhagyott regisztráció](../enrollment/macos-enroll.md) az Intune-ban –* dokumentáció.  

  - Ismeretlen.  

    *Úgy Ismeretlen állapot esetén az egyik lehetséges ok az, hogy az eszköz zárolva van, és az Intune nem tudja elindítani a letéti vagy titkosítási folyamatot. Az eszköz zárolása után a folyamat továbbra*is folytatódhat.  

  **Windows 10**:  
  - A BitLocker-házirend felhasználói beleegyezik, hogy elindítsa a BitLocker meghajtótitkosítás varázslót az operációsrendszer-kötet titkosításának megkezdéséhez, de a felhasználó nem járult hozzá.  
  
  - Az operációsrendszer-kötet titkosítási metódusa nem felel meg a BitLocker-házirendnek.  
  
  - A BitLocker-szabályzathoz TPM-védő szükséges az operációs rendszer kötetének védelme érdekében, de a TPM nincs használatban.  
  
  - A BitLocker-házirendhez csak TPM-védelem szükséges az operációsrendszer-kötethez, de a TPM védelme nincs használatban.  
  
  - A BitLocker-házirendhez a TPM + PIN-kód védelem szükséges az operációsrendszer-kötethez, de nincs használatban TPM + PIN-védő.  
  
  - A BitLocker-házirendhez a TPM + indítókulcs-védelem szükséges az operációs rendszer kötetén, de a TPM + indítókulcs-védő nincs használatban.  
  
  - A BitLocker-házirendhez a TPM + PIN + indítókulcs-védelem szükséges az operációsrendszer-köteten, de a TPM + PIN + indítókulcs-védő nincs használatban.  
  
  - Az operációsrendszer-kötet nem védett.  
  
  - A helyreállítási kulcs biztonsági mentése nem sikerült.  
  
  - A rögzített meghajtók nem védettek.  
  
  - A rögzített meghajtó titkosítási metódusa nem felel meg a BitLocker-házirendnek.  
  
  - A meghajtók titkosításához a BitLocker-házirendnek vagy a felhasználónak rendszergazdaként kell bejelentkeznie, vagy ha az eszköz csatlakozik az Azure AD-hez, a AllowStandardUserEncryption házirendet 1-re kell állítani.  
  
  - Nincs konfigurálva a Windows helyreállítási környezet (WinRE).  
  
  - A TPM nem érhető el a BitLocker számára, mert nincs jelen, a beállításjegyzékben nem érhető el, vagy az operációs rendszer cserélhető meghajtón található.  
  
  - A TPM nem áll készen a BitLocker használatára.  
  
  - A hálózat nem érhető el, amely a helyreállítási kulcs biztonsági mentéséhez szükséges.  

## <a name="export-report-details"></a>Jelentés adatainak exportálása 
A titkosítási jelentés panel megtekintése közben kiválaszthatja az **Exportálás** lehetőséget *. csv* -fájl letöltéséhez a jelentés részleteiről.  Ez a jelentés a *titkosítási jelentés* panel magas szintű adatait és az *eszköz titkosítási állapotának* részleteit tartalmazza minden egyes felügyelt eszközön.   
 
  
![Exportálás részletei](./media/encryption-monitor/export.png) 
 
Ez a jelentés az eszközök csoportjaiban felmerülő problémák azonosításában is felhasználható. Például használhatja a jelentést azon macOS-eszközök listájának azonosítására, amelyeket az összes jelentés *FileVault már engedélyeztek a felhasználó*, amely azokat az eszközöket jelöli, amelyeket manuálisan kell visszafejteni, mielőtt az Intune felügyelni tudja a FileVault beállításait.  
 
## <a name="filevault-recovery-keys"></a>FileVault helyreállítási kulcsok   
Amikor az Intune először titkosít egy macOS-eszközt a FileVault-mel, létrejön egy személyes helyreállítási kulcs. A titkosítás után az eszköz egyetlen alkalommal jeleníti meg a személyes kulcsot a végfelhasználó számára.  
 
A felügyelt eszközök esetében az Intune a személyes helyreállítási kulcs egy másolatát is letétbe helyezheti. A kulcsok letétbe való bekapcsolása lehetővé teszi az Intune-rendszergazdák számára, hogy a kulcsokat az eszközök védelmére, valamint az elveszett vagy elforgatott személyes helyreállítási kulcsok helyreállítására.  
 
Az Intune több lehetőséget is támogat a személyes helyreállítási kulcsok elforgatására és helyreállítására. A kulcsok elforgatásának egyik oka az, hogy ha az aktuális személyes kulcs elveszett vagy veszélyben van.  
 
> [!IMPORTANT]  
>  Azokat az eszközöket, amelyeket a felhasználók titkosítottak, és nem az Intune, nem kezelhetik az Intune-nal. Ez azt jelenti, hogy az Intune nem tudja kiutalni ezeknek az eszközöknek a személyes helyreállítását, és nem kezeli a helyreállítási kulcs rotációját.  Mielőtt az Intune felügyelni tudja az eszköz FileVault és helyreállítási kulcsait, a felhasználónak vissza kell fejtenie az eszközét, majd engedélyeznie kell az Intune-nak az eszköz titkosítását.  

### <a name="rotate-recovery-keys"></a>Helyreállítási kulcsok elforgatása  

- **Automatikus elforgatás**: Rendszergazdaként beállíthatja a személyes helyreállítási kulcs FileVault beállítását, hogy az új helyreállítási kulcs rendszeres időközönként automatikusan létrejöjjön.  Ha egy eszközhöz új kulcs jön létre, a kulcs nem jelenik meg a felhasználó számára. Ehelyett a felhasználónak rendszergazda vagy a vállalati portál alkalmazás használatával kell lekérnie a kulcsot.  

- **Manuális elforgatás**: Rendszergazdaként megtekintheti az Intune-nal kezelt és a FileVault-mel titkosított eszközök adatait. Ezután dönthet úgy, hogy manuálisan elforgatja a vállalati eszközök helyreállítási kulcsát. A személyes eszközökhöz nem lehet elforgatni a helyreállítási kulcsokat.  

  Helyreállítási kulcs elforgatása: 
  1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, lépjen az **eszközök** pontra, majd a kezelés területen válassza a **minden eszköz**lehetőséget.  
  2. Az eszközök listájából válassza ki a titkosított eszközt, amelyre el szeretné forgatni a kulcsát. Ezután a Figyelés területen válassza a **helyreállítási kulcsok**elemet.  
  3. A helyreállítási kulcsok ablaktáblán válassza a **FileVault-helyreállítási kulcs**elforgatása lehetőséget.  
  
     Amikor az eszköz legközelebb bejelentkezik az Intune-ba, a rendszer elforgatja a személyes kulcsot. Ha szükséges, az új kulcsot a végfelhasználó szerzi be a vállalati portálon keresztül. 


### <a name="recover-recovery-keys"></a>Helyreállítási kulcsok helyreállítása  
- **Rendszergazda**: A rendszergazdák nem tekinthetik meg a FileVault-mel titkosított eszközök személyes helyreállítási kulcsait.  

- **Végfelhasználó**: A végfelhasználók a Céges portál webhelyet bármely eszközről megtekinthetik a felügyelt eszközök aktuális személyes helyreállítási kulcsát. A Céges portál alkalmazásból nem tekinthetők meg helyreállítási kulcsok.  

 
  Helyreállítási kulcs megtekintése:  
  1. Jelentkezzen be a *Intune céges portál* webhelyére bármely eszközről.  
  2. A portálon lépjen az **eszközök** elemre, és válassza ki a FileVault-mel titkosított MacOS-eszközt.  
  3. Válassza a **helyreállítási kulcs**beolvasása elemet. Megjelenik az aktuális helyreállítási kulcs.  
 

## <a name="bitlocker-recovery-keys"></a>BitLocker helyreállítási kulcsok  

Az Intune hozzáférést biztosít a BitLockerhez készült Azure AD panelhez, így megtekintheti a BitLocker-kulcsok azonosítóit és a Windows 10-es eszközök helyreállítási kulcsait az Intune-portálon belülről.  Az eszköznek elérhetőnek kell lennie az Azure AD-ben. 
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, lépjen az **eszközök** pontra, majd a *kezelés*területen válassza a **minden eszköz**lehetőséget.  

2. Válasszon ki egy eszközt a listából, majd a *figyelés*területen válassza a **helyreállítási kulcsok**elemet.  
  
Ha a kulcsok elérhetők az Azure AD-ben, a következő információk érhetők el:
- BitLocker-kulcs azonosítója  
- BitLocker helyreállítási kulcs  
- Meghajtó típusa  

Ha a kulcsok nem szerepelnek az Azure AD-ben, az Intune az *eszközhöz nem talált BitLocker-kulcsot*fog megjeleníteni.  

A BitLocker információi a [BitLocker konfigurációs](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) szolgáltató (CSP) használatával szerezhetők be. A BitLocker CSP támogatott a Windows 10 1703-es és újabb verzióiban, valamint a Windows 10 Pro 1809-es és újabb verzióiban.  

## <a name="next-steps"></a>További lépések  

Hozzon létre egy [eszköz megfelelőségi](compliance-policy-create-windows.md) szabályzatát.
