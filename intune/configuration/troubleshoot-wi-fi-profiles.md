---
title: A Wi-Fi-eszköz profil naplóinak hibakeresése és áttekintése a Microsoft Intune-Azure-ban | Microsoft Docs
description: A Wi-Fi-eszközök konfigurációs profiljaival kapcsolatos problémák megismerése és hibaelhárítása az Android, iOS és Windows rendszerű eszközökön Microsoft Intuneban. Tekintse át a naplókat, és tekintse meg a gyakori problémákat és a lehetséges megoldásokat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c33ab3c72d6e76b44fec85ce40dc2d6510a294bc
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207128"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>A Wi-Fi-eszköz konfigurációs profiljainak hibáinak megoldása Microsoft Intune

Az Intune-ban olyan eszköz-konfigurációs profilokat hozhat létre, amelyek tartalmazzák a WiFi-hálózathoz tartozó kapcsolatbeállításokat. Ezekkel a beállításokkal csatlakoztathatók a felhasználók Android-, iOS-és Windows-eszközei a szervezeti hálózathoz.

Ez a cikk azt mutatja be, hogy a Wi-Fi profil hogyan néz ki, ha az eszközre való sikeres alkalmazásra vonatkozik. Emellett a naplózási információkat, a gyakori problémákat és egyebeket is tartalmaz. Ez a cikk segítséget nyújt a Wi-Fi profilok hibakeresésében.

Az Intune Wi-Fi profiljaival kapcsolatos további információkért lásd: Wi-Fi- [Beállítások hozzáadása és használata az eszközökön](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Előkészületek

A jelen cikkben szereplő példák az Intune-profilok SCEP tanúsítvány-hitelesítését használják. Azt is feltételezi, hogy a megbízható gyökér-és SCEP profilok megfelelően működnek az eszközön.

## <a name="android"></a>Android:

Ebben a szakaszban bemutatjuk a végfelhasználói élményt a konfigurációs profilok Android-eszközön való telepítésekor.

### <a name="end-user-experience-example"></a>Végfelhasználói élmény – példa

Ez a forgatókönyv egy Nokia 6,1-es eszközt használ. A Wi-Fi profil telepítésének megkezdése előtt telepítse a megbízható gyökér-és SCEP-profilokat.

1. A végfelhasználók értesítést kapnak a megbízható legfelső szintű tanúsítvány profiljának telepítéséhez:

    > [!div class="mx-imgBorder"]
    > ![minta Céges portál alkalmazás-értesítés Androidon a megbízható főtanúsítvány-profil telepítéséhez](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. A következő értesítés kéri a SCEP-tanúsítvány profiljának telepítését:

    > [!div class="mx-imgBorder"]
    > ![minta Céges portál alkalmazás-értesítés Androidon a SCEP-tanúsítvány profiljának telepítéséhez](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Ha egy eszköz rendszergazdája által felügyelt Android-eszközt használ, több tanúsítvány is szerepelhet. A tanúsítvány-profil visszavonása vagy eltávolítása után a tanúsítvány marad az eszközön. Ebben az esetben válassza ki a legújabb tanúsítványt. Ez általában a listában látható utolsó tanúsítvány.
    >
    > Ez a helyzet az Android Enterprise és a Samsung Knox rendszerű eszközökön nem fordul elő. További információ: [androidos munkahelyi profilú eszközök kezelése](../enrollment/android-enterprise-overview.md) és [SCEP-és PKCS-tanúsítványok eltávolítása](../protect/remove-certificates.md#android-knox-devices).

3. Ezután a felhasználók értesítést kapnak a Wi-Fi profil telepítéséhez:

    > [!div class="mx-imgBorder"]
    > ![minta Céges portál alkalmazás-értesítés Androidon a SCEP-tanúsítvány profiljának telepítéséhez](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Ha elkészült, a Wi-Fi-kapcsolat mentett hálózatként jelenik meg:

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi-kapcsolat mentett hálózatként jelenik meg](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Céges portál alkalmazás naplófájljainak áttekintése

Az Androidon a **Omadmlog. log** fájl a Wi-Fi profil tevékenységeit az eszközre való telepítéskor részletezi. Lehet, hogy legfeljebb öt Omadmlog naplófájl van. Ügyeljen arra, hogy a legutóbbi szinkronizálás időbélyegét kapja meg, mivel a kapcsolódó naplóbejegyzések megtalálásához segítséget nyújt.

A következő példában a [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) használatával olvassa be a naplókat, és keressen rá a "wifimgr" kifejezésre:

> [!div class="mx-imgBorder"]
> ![Wi-Fi-kapcsolat mentett hálózatként jelenik meg](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

A következő napló a keresési eredményeket jeleníti meg, és a Wi-Fi profil sikeres alkalmazását mutatja:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Miután telepítette a Wi-Fi profilt az eszközön, a **felügyeleti profilban**látható:

> [!div class="mx-imgBorder"]
> ![felügyeleti profil iOS-eszközön](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Wi-Fi-kapcsolat Wi-Fi-hálózatként jelenik meg iOS-eszközön](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Az iOS-konzol és az eszközök naplófájljainak áttekintése

IOS-eszközökön a Céges portál-alkalmazás naplója nem tartalmazza a Wi-Fi profilokkal kapcsolatos információkat. A Wi-Fi profilok telepítési adatainak megtekintéséhez használja a konzol/eszköz naplókat:

1. Az iOS-eszköz csatlakoztatása Mac-hez. Válassza az **alkalmazások** > **segédprogramok**lehetőséget, és nyissa meg a konzol alkalmazást.
2. A **művelet**területen jelölje be az **információs üzenetek belefoglalása** és a **hibakeresési üzenetek belefoglalása**jelölőnégyzetet:

    > [!div class="mx-imgBorder"]
    > ![tartalmazza a tájékoztató üzeneteket, és hibakeresési üzeneteket is tartalmazhatnak az iOS-konzol alkalmazásban](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Hozza létre újra a forgatókönyvet, és mentse a naplókat szövegfájlba:

    1. Válassza ki az összes üzenetet az aktuális képernyőn: **szerkesztés** > az **összes kijelölése elemre**.
    2. Az üzenetek másolása: > **Másolás** **szerkesztése** .
    3. Illessze be a naplózási adatnaplót egy szövegszerkesztőbe, és mentse a fájlt.

4. A mentett naplófájlban keresse meg a részletes információkat. A profil sikeres telepítésekor a kimenet a következő naplóhoz hasonlóan néz ki:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Miután telepítette a Wi-Fi profilt az eszközön, lépjen a **beállítások** > **fiókok** > **hozzáférés munkahelyi vagy iskolai**rendszerhez elemre. Válassza ki a fiókját > **info**:

> [!div class="mx-imgBorder"]
> ![hozzáférés munkahelyi vagy iskolai rendszerhez, és válassza a Windows-eszköz információi](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

A **Microsoft által felügyelt területeken**a **WiFi** a következőket jeleníti meg:

> [!div class="mx-imgBorder"]
> ![a Microsoft által felügyelt területeken tekintse meg, hogy a WiFi szerepel-e a Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

A Wi-Fi kapcsolat megtekintéséhez lépjen a **beállítások** > **hálózati & Internet**  > **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![Windows rendszeren a Wi-Fi-kapcsolat ismert hálózatként jelenik meg a beállításokban](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Eseménynapló-naplók áttekintése

Windows-eszközökön a Wi-Fi profilokkal kapcsolatos részletek a Eseménynaplóban vannak naplózva:

1. Nyissa meg a **Eseménynapló** alkalmazást.
2. A **nézet** menüben válassza az **elemzési és hibakeresési naplók megjelenítése**lehetőséget.
3. **Az alkalmazások és szolgáltatások naplói** kibontása > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**

Az alábbi naplókhoz hasonló kimenet:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Gyakori problémák

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>1. probléma: a Wi-Fi profil nincs központilag telepítve az eszközön

- Ellenőrizze, hogy a Wi-Fi profil a megfelelő csoporthoz van-e rendelve:

    1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **konfigurációs profilok**lehetőséget.
    2. Válassza ki a profilt >- **hozzárendeléseket**. Győződjön meg arról, hogy a kiválasztott csoportok helyesek.
    3. A Endpoint Managerben válassza a **Hibaelhárítás + támogatás**lehetőséget. Tekintse át a **hozzárendelések** adatait.

- A Endpoint Managerben válassza a **Hibaelhárítás + támogatás**lehetőséget. Ellenőrizze, hogy az eszköz képes-e szinkronizálni az Intune-nal az **utolsó bejelentkezés** időpontjának ellenőrzésével.

- Ha a Wi-Fi-profil a megbízható gyökér-és SCEP profilokhoz van csatolva, ellenőrizze, hogy mindkét profil telepítve van-e az eszközön. A Wi-Fi profil ezen profiloktól függ.

- A Windows 10 és újabb rendszerű eszközökön tekintse át a MDM diagnosztikai információs naplóját:

  1. Lépjen a **beállítások** > **fiókok** > **hozzáférés munkahelyi vagy iskolai rendszerhez elemre**.
  2. Válassza ki a munkahelyi vagy iskolai fiókját > **adatokat**.
  3. A **Beállítások** lap alján válassza a **jelentés létrehozása**lehetőséget.
  4. Megnyílik egy ablak, amely megjeleníti a naplófájlok elérési útját. Válassza az **Exportálás**lehetőséget.
  5. Nyissa meg a `\Users\Public\Documents\MDMDiagnostics` elérési utat, és tekintse meg a jelentést:

      > [!div class="mx-imgBorder"]
      > ![minta MDM diagnosztikai információk, amelyek a Wi-Fi profilok konfigurációját jelenítik meg a Windows 10-es eszközökön](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > További információ: [Mdm-hibák diagnosztizálása a Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)rendszerben.

- Ha androidos eszközökön nincsenek telepítve a megbízható gyökér-és SCEP-profilok az eszközön, a következő bejegyzés jelenik meg a Céges portál alkalmazás Omadmlog fájljában:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Ha a megbízható gyökér-és SCEP-profilok az Android-eszközön vannak és megfelelőek, előfordulhat, hogy a Wi-Fi profil nem található az eszközön. Ez a probléma akkor fordul elő, ha a Céges portál alkalmazás **CertificateSelector** -szolgáltatója nem talál olyan tanúsítványt, amely megfelel a megadott feltételeknek. Az adott feltétel a tanúsítványsablon vagy a SCEP-profilban lehet.

    Ha nem található a megfelelő tanúsítvány, az eszközön lévő tanúsítványok nincsenek telepítve. A Wi-Fi profil nem érvényes, mert nem rendelkezik a megfelelő tanúsítvánnyal. Ebben az esetben a következő bejegyzést látja a Céges portál alkalmazás Omadmlog fájljában:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    Az alábbi minta naplóban láthatók azok a tanúsítványok, amelyeket a rendszer kizár, mert a rendszer **Kibővített kulcshasználat** (EKU) feltételeket adott meg. Az eszközhöz rendelt tanúsítványok azonban nem rendelkeznek ezzel az EKU-vel:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    A következő minta azt mutatja be, hogy a SCEP-profil a **bármely célra szolgáló** EKU-t tartalmazza. Ez azonban nem szerepel a hitelesítésszolgáltató (CA) tanúsítvány-sablonjában. A probléma megoldásához adja hozzá a **bármely célra** lehetőséget a tanúsítványsablon számára. Vagy távolítsa el a **bármilyen célra** lehetőséget a SCEP-profilból.

    > [!div class="mx-imgBorder"]
    > ![az Androidon, adjon hozzá valamilyen célt a tanúsítványsablon számára a hitelesítésszolgáltatónál](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![Androidon, adjon hozzá bármilyen célt az Intune-ban az SCEP-tanúsítvány konfigurációs profiljához](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Győződjön meg arról, hogy a teljes tanúsítványlánc összes szükséges tanúsítványa az Android-eszközön található. Ellenkező esetben a Wi-Fi profil nem telepíthető az eszközre. További információ: [hiányzó köztes](https://developer.android.com/training/articles/security-ssl#MissingCa) hitelesítésszolgáltató (az Android webhely megnyitása).
  - A Omadmlog szűrésével kereshet olyan információkat, mint például a Wi-Fi profilban használt tanúsítvány, valamint a profil sikeres alkalmazása.

    Például a [CMTrace](https://docs.microsoft.com/sccm/core/support/cmtrace) használatával olvassa be a naplókat. A "wifimgr" szűréséhez használja a keresési karakterláncot:

    > [!div class="mx-imgBorder"]
    > ![szűrő CMTrace az Android-eszközökön található WiFiMgr-konfigurációs profilok kereséséhez](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    A kimenet a következő naplóhoz hasonlóan néz ki:

    > [!div class="mx-imgBorder"]
    > ![minta CMTrace, amely a WiFi Intune konfigurációs profilt mutatja az eszközökön való sikeres alkalmazásakor](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Ha a naplóban hiba jelenik meg, másolja a hiba időbélyegét, és szűrje a napló szűrését. Ezután használja a "keresés" lehetőséget az időbélyegző használatával, hogy megtudja, mi történt a hiba előtt.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>2. probléma: a Wi-Fi profil telepítve van az eszközön, de az eszköz nem tud csatlakozni a hálózathoz

Ezt a problémát általában az Intune-on kívüli személy okozta. A következő feladatok segítenek megérteni és elhárítani a kapcsolódási problémákat:

- Manuálisan kapcsolódjon a hálózathoz a Wi-Fi-profilban megegyező feltételekkel rendelkező tanúsítvány használatával.

  Ha csatlakozni tud, tekintse meg a tanúsítvány tulajdonságait a manuális kapcsolatban. Ezután frissítse az Intune Wi-Fi-profilját ugyanazzal a tanúsítvány-tulajdonságokkal.
- A kapcsolódási hibák általában a RADIUS-kiszolgáló naplójában vannak naplózva. Például meg kell jelenítenie, hogy az eszköz megpróbált-e kapcsolódni a Wi-Fi profilhoz.

## <a name="need-more-help"></a>További segítségre van szüksége

- Használja az [Intune felhasználói fórumait](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) , vagy [kérjen támogatást a Microsofttól](../fundamentals/get-support.md).

- A Microsoft Intune Wi-Fi profiljaival kapcsolatos további információkért tekintse meg a következő cikkeket:

  - Wi-Fi-beállítások hozzáadása [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md)és [Windows 10 és újabb](wi-fi-settings-windows.md)rendszerű eszközökhöz.
  - [Támogatási tipp – a NDES konfigurálása a SCEP-tanúsítványok telepítéséhez az Intune-ban](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Az [SCEP-tanúsítvány profiljának üzembe helyezése](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) és a [NDES-konfiguráció](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)hibáinak megoldása.

- A legfrissebb hírek, információk és technikai tippekért tekintse meg a hivatalos blogokat:
  - [Microsoft Intune támogatási csapat blogja](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Microsoft nagyvállalati mobilitási és biztonsági blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>További lépések

[A profilok figyelése](device-profile-monitor.md).
