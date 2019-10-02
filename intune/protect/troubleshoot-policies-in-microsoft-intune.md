---
title: Hibaelhárítás az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Tekintse meg a beépített hibaelhárítási funkció használatát ismertető témakört, és olvassa el a gyakori problémákat és problémákat, valamint a megfelelőségi szabályzatok és konfigurációs profilok használatakor Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2afdd358af19c28ff18e4e6e65839d7e314996b1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731527"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Szabályzatok és profilok és az Intune hibáinak megoldása

Microsoft Intune tartalmaz néhány beépített hibaelhárítási funkciót. Ezekkel a szolgáltatásokkal elháríthatja a környezetben a megfelelőségi szabályzatokat és a konfigurációs profilokat.

Ez a cikk néhány gyakori hibaelhárítási módszert sorol fel, és ismerteti az esetlegesen felmerülő problémákat.

## <a name="check-tenant-status"></a>Bérlői állapot keresése
Ellenőrizze a [bérlő állapotát](../fundamentals/tenant-status.md) , és ellenőrizze, hogy az előfizetés aktív-e. Megtekintheti azokat az aktív incidenseket és tanácsadókat is, amelyek hatással lehetnek a szabályzatra vagy a profil telepítésére.

## <a name="use-built-in-troubleshooting"></a>Beépített hibaelhárítás használata

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ban válassza a **hibakeresés**elemet:

    ![Az Intune-ban lépjen a Súgó és támogatás elemre, és válassza a hibakeresés lehetőséget.](./media/troubleshoot-policies-in-microsoft-intune/help-and-support-troubleshoot.png)

2. Válassza a **felhasználó kiválasztása** lehetőséget > Válassza ki azt a felhasználót, aki a probléma > **válassza a lehetőséget**.
3. Győződjön meg arról, hogy az **Intune-licenc** és- **fiók állapota** mind a zöld ellenőrzések megjelenítése:

    ![Az Intune-ban válassza ki a felhasználót, és erősítse meg a fiók állapotát és az Intune-licenc megjelenítése zöld ellenőrzési jelek az állapothoz](./media/troubleshoot-policies-in-microsoft-intune/account-status-intune-license-show-green.png)

    **Hasznos hivatkozások**:

    - [Licencek kiosztása, hogy a felhasználók regisztrálhatják az eszközöket](../fundamentals/licenses-assign.md)
    - [Felhasználók hozzáadása az Intune-hoz](../fundamentals/users-add.md)

4. Az **eszközök**területen keresse meg a problémával rendelkező eszközt. Tekintse át a különböző oszlopokat:

    - **Felügyelt**: Ahhoz, hogy egy eszköz megfelelőségi vagy konfigurációs szabályzatokat kapjon, ennek a tulajdonságnak **Mdm** vagy **EAS/Mdm**kell mutatnia.

        - Ha a **felügyelt** nem **Mdm** vagy **EAS/Mdm**értékre van állítva, akkor az eszköz nincs regisztrálva. Nem kap megfelelőségi vagy konfigurációs szabályzatot, amíg a regisztrációja be nem fejeződik.

        - Az alkalmazás-védelmi szabályzatok (mobileszköz-kezelés) nem igénylik az eszközök regisztrálását. További információ: az [alkalmazás-védelmi szabályzatok létrehozása és kiosztása](../apps/app-protection-policies.md).

    - **Azure ad-csatlakozás típusa**: **Munkahelyre** vagy **AzureAD**kell beállítani.
 
        - Ha ez az oszlop nincs **regisztrálva**, lehet, hogy probléma van a regisztrációval. Az eszköz regisztrációjának törlése és újbóli regisztrálása általában feloldja ezt az állapotot.

    - **Intune-kompatibilis**: **Igen értékűnek**kell lennie. Ha **nem** látható, a megfelelőségi szabályzatokkal kapcsolatos probléma merülhet fel, vagy az eszköz nem csatlakozik az Intune szolgáltatáshoz. Előfordulhat például, hogy az eszköz ki van kapcsolva, vagy nem rendelkezik hálózati kapcsolatban. Végül az eszköz nem megfelelővé válik, valószínűleg 30 nap után.

        További információ: [Bevezetés az eszközök megfelelőségi házirendjeibe](../protect/device-compliance-get-started.md).

    - **Azure ad-kompatibilis**: **Igen értékűnek**kell lennie. Ha **nem** látható, a megfelelőségi szabályzatokkal kapcsolatos probléma merülhet fel, vagy az eszköz nem csatlakozik az Intune szolgáltatáshoz. Előfordulhat például, hogy az eszköz ki van kapcsolva, vagy nem rendelkezik hálózati kapcsolatban. Végül az eszköz nem megfelelővé válik, valószínűleg 30 nap után.

        További információ: [Bevezetés az eszközök megfelelőségi házirendjeibe](../protect/device-compliance-get-started.md).

    - **Utolsó beadás**: A legutóbbi dátumnak és időpontnak kell lennie. Alapértelmezés szerint az Intune-eszközök 8 óránként kerülnek beadásra.

        - Ha a **legutóbbi bejelentkezés** 24 óránál hosszabb, lehet, hogy probléma van az eszközzel. Olyan eszköz, amely nem tud bejelentkezni, nem tudja fogadni a szabályzatokat az Intune-ból.

        - A bejelentkezés kényszerítése:
            - Az Android-eszközön nyissa meg az Céges portál alkalmazás > **eszközök** > válassza ki az eszközt a listából > az **eszközbeállítások ellenõrzése**lehetőséget.
            - Az iOS-eszközön nyissa meg a vállalati portál alkalmazást > **eszközök** > válassza ki az eszközt a listából > a **Beállítások ellenőrzését**.

        - Windows-eszközön nyissa meg a **Beállítások** > **fiókok** > **hozzáférés munkahelyi vagy iskolai** > Válassza ki a fiókot vagy a Mdm beléptetési > az **adatok** > **szinkronizálása**lehetőséget.

    - Válassza ki az eszközt a házirend-specifikus információk megjelenítéséhez.

        Az **eszköz megfelelősége** az eszközhöz rendelt megfelelőségi szabályzatok állapotát mutatja.

        Az **eszköz konfigurációja** megjeleníti az eszközhöz rendelt konfigurációs házirendek állapotait.

        Ha a várt szabályzatok nem jelennek meg az **eszköz megfelelősége** vagy az **eszköz konfigurációja**területen, akkor a házirendek nem megfelelően vannak megcélozva. Nyissa meg a szabályzatot, és rendelje hozzá a szabályzatot ehhez a felhasználóhoz vagy eszközhöz.

        **Szabályzat állapota**:

        - **Nem alkalmazható**: Ez a szabályzat nem támogatott ezen a platformon. Az iOS-házirendek például nem működnek az Android rendszeren. A Samsung KNOX-szabályzatok nem működnek Windows-eszközökön.
        - **Ütközés**: Létezik egy meglévő beállítás az eszközön, amelyet az Intune nem tud felülbírálni. Másik lehetőségként két házirendet is üzembe helyezett ugyanazzal a beállítással különböző értékek használatával.
        - **Függőben**: Az eszköz nem ellenőrizte az Intune-t a szabályzat beszerzéséhez. Vagy az eszköz fogadta a szabályzatot, de nem jelentette az állapotot az Intune-nak.
        - **Hibák**: A [Vállalati erőforrás-hozzáférési problémák elhárításával kapcsolatos](../fundamentals/troubleshoot-company-resource-access-problems.md)hibákat és lehetséges megoldásokat kereshet.

        **Hasznos hivatkozások**: 

        - [Eszközök megfelelőségi házirendjeinek központi telepítésének módjai](../protect/device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
        - [Eszközmegfelelőségi szabályzatok figyelése](../protect/compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Nem biztos benne, hogy a profil megfelelően van-e alkalmazva

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszközök** > **minden eszköz** lehetőséget > Válassza ki az eszköz > **eszköz konfigurációját**. 

    Minden eszköz felsorolja a profilokat. Minden profil rendelkezik **állapottal**. Az állapot akkor érvényes, ha az összes hozzárendelt profil, beleértve a hardvert és az operációs rendszer korlátozásait és követelményeit együttesen veszi figyelembe. A lehetséges állapotok a következők:

    - **Megfelel**a következőket: Az eszköz megkapta a profilt és a jelentéseket az Intune-nak, amely megfelel a beállításnak.

    - **Nem alkalmazható**: A profil beállítása nem alkalmazható. Az iOS-eszközök e-mail-beállításai például nem alkalmazhatók Android-eszközre.

    - **Függőben**: A rendszer elküldje a profilt az eszközre, de nem jelentett állapotot az Intune-nak. Például az Android rendszeren csak akkor működik a titkosítás, ha a felhasználó engedélyezi, ezért függőben lehet.

**Hasznos hivatkozás**: [Konfigurációs eszközök profiljainak figyelése](../configuration/device-profile-monitor.md)

> [!NOTE]
> Ha két különböző korlátozási szintű szabályzat vonatkozik egy eszközre vagy felhasználóra, akkor a gyakorlatban a szigorúbb szabályzat lesz érvényes.

## <a name="policy-troubleshooting-resources"></a>Házirend-hibaelhárítási erőforrások

- [Az eszközökön nem alkalmazott iOS-vagy Android-házirendek hibaelhárítása](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (másik Microsoft-webhely megnyitása)
- A [Windows 10 Intune-szabályzat hibáinak elhárítása](https://blogs.technet.microsoft.com/configmgrdogs/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (blog megnyitása)
- [A Windows 10 rendszerhez készült CSP egyéni beállításainak megoldása](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (másik Microsoft-webhely megnyitása)
- [Windows 10 csoportházirend vs INTUNE Mdm szabályzat](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (másik Microsoft-webhely megnyitása)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Riasztás Sikertelen volt a hozzáférési szabályok mentése az Exchange szolgáltatásba

**Probléma**: A felügyeleti konzolon az Exchange-re vonatkozó **hozzáférési szabályok mentése sikertelen volt** .

Ha szabályzatokat hoz létre a helyszíni Exchange-házirend munkaterületen (felügyeleti konzol), de az Office 365-et használja, akkor az Intune nem kényszeríti ki a konfigurált házirend-beállításokat. A riasztásban jegyezze fel a házirend forrását. A helyszíni Exchange-szabályzat munkaterületen törölje az örökölt szabályokat. Az örökölt szabályok az Intune-ban a helyszíni Exchange-en belüli globális Exchange-szabályok, és nem vonatkoznak az Office 365-re. Ezután hozzon létre új szabályzatot az Office 365-hez.

Előfordulhat, hogy [az Intune helyszíni Exchange Connector](../protect/troubleshoot-exchange-connector.md) a megfelelő erőforrást fogja elhárítani.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Nem lehet módosítani a regisztrált eszközökhöz tartozó biztonsági házirendeket

Windows Phone-telefon az eszközök nem teszik lehetővé, hogy a MDM vagy EAS-vel beállított biztonsági házirendek a biztonságuk után csökkentsék a biztonságot. Például beállíthatja, hogy a **jelszó minimális száma** 8 legyen, majd próbálja meg csökkenteni a 4 értékre. Az eszközre szigorúbb házirend vonatkozik.

Előfordulhat, hogy a Windows 10-es eszközök nem távolítják el a biztonsági házirendeket a szabályzat hozzárendelésének megszüntetésekor (az üzemelő példány leállítása). Előfordulhat, hogy el kell hagynia a hozzárendelt szabályzatot, majd vissza kell állítania a biztonsági beállításokat az alapértelmezett értékekre.

Ha a házirendet kevésbé biztonságos értékre szeretné módosítani, előfordulhat, hogy alaphelyzetbe kell állítania a biztonsági szabályzatokat.

Például a Windows 8,1-ben az asztalon, a jobb oldalon a **varázsok** sáv megnyitásához. Válassza a **Beállítások** > **Vezérlőpult** > **felhasználói fiókok**elemet. A bal oldalon válassza a **Biztonsági szabályzatok alaphelyzetbe állítása** hivatkozást, majd válassza a **Szabályzatok alaphelyzetbe állítása** lehetőséget.

Előfordulhat, hogy más platformokon (például Android, iOS vagy Windows Phone-telefon 8,1) ki kell vonni a rendszert, és újból regisztrálni kell, hogy kevésbé szigorú házirendet alkalmazzon.

Előfordulhat, hogy az [eszközök regisztrálásának hibája](../enrollment/troubleshoot-device-enrollment-in-intune.md) jó erőforrás.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>Az Intune szoftveres ügyfélprogramot használó számítógépek – klasszikus portál

> [!NOTE]
> Ez a szakasz a klasszikus portálra vonatkozik. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Microsoft Intune-házirendekkel kapcsolatos hibák a policyplatform.log fájlban

Az Intune-ügyfélszoftverrel felügyelt Windows rendszerű számítógépeken előfordulhat, `policyplatform.log` hogy a fájlban lévő házirend-hibák a Windows felhasználói fiókok felügyelete (UAC) nem alapértelmezett beállításaiból származnak az eszközön. Néhány nem alapértelmezett UAC-beállítás hatással lehet a Microsoft Intune ügyféltelepítéseire és a házirendek érvénybe léptetésére.

#### <a name="resolve-uac-issues"></a>UAC-problémák megoldása

1. Vonja ki a számítógépet. Lásd: [Eszközök eltávolítása](../remote-actions/devices-wipe.md).

2. Várjon 20 percet az ügyfélszoftver eltávolításáig.

    > [!NOTE]
    > Ne próbálja meg eltávolítani az ügyfelet a Programok és szolgáltatások területről.

3. A Start menüben írja be az **UAC** parancsot a felhasználói fiókok vezérlési beállításainak megnyitásához.

4. Helyezze át az értesítési csúszkát az alapértelmezett értékre.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>HIBA Nem lehet beolvasni az értéket a számítógépről, 0x80041013

Ez akkor fordulhat elő, ha a helyi rendszeren lévő idő legalább öt perccel eltér a szinkronizált értéktől. Ha a helyi számítógépen lévő idő nincs szinkronban, a biztonságos tranzakciók sikertelenek, mert az időbélyegek érvénytelenek.

A probléma megoldásához állítsa be a helyi rendszeridőt a lehető legrövidebb idő alatt az internetes idő értékre. Vagy állítsa be a hálózatban lévő tartományvezérlőkön beállított időpontra.

## <a name="next-steps"></a>További lépések

[Az e-mail-profilokkal kapcsolatos gyakori problémák és megoldások](../configuration/troubleshoot-email-profiles-in-microsoft-intune.md)

Kérjen [támogatási segítséget](../fundamentals/get-support.md)a Microsofttól, vagy használja a [közösségi fórumokat](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
