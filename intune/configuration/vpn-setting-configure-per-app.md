---
title: Alkalmazásonkénti VPN beállítása iOS eszközökhöz az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: A cikk útmutatást nyújt az előfeltételek áttekintéséhez, csoport létrehozásához a virtuális magánhálózat (VPN) felhasználói számára, az SCEP-tanúsítványprofil hozzáadásához, az alkalmazásonkénti VPN-profil beállításához és alkalmazások VPN-profilhoz történő hozzáadásához iOS-eszközök esetében a Microsoft Intune-ban. Továbbá a VPN-kapcsolat eszközön történő ellenőrzéséhez szükséges lépéseket is bemutatja.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40abb2adda9602adc372f0c2b6ee9c17fbf5cb87
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730495"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>App virtual private Network (VPN) beállítása iOS-eszközökhöz az Intune-ban

Microsoft Intune az alkalmazáshoz hozzárendelt virtuális magánhálózatok (VPN) hozhatók létre és használhatók. Ezt a funkciót "app VPN"-ként nevezzük. Kiválaszthatja azokat a felügyelt alkalmazásokat, amelyek használhatják a VPN-t az Intune által felügyelt eszközökön. Az alkalmazáson belüli VPN-EK használatakor a végfelhasználók automatikusan csatlakoznak a VPN-en keresztül, és hozzáférést kapnak a szervezeti erőforrásokhoz, például a dokumentumokhoz.

Ez a funkció az alábbiakra vonatkozik:

- iOS 9-es és újabb verziók

A VPN-szolgáltató dokumentációjában megtekintheti, hogy a VPN támogatja-e az alkalmazáson belüli VPN-t.

Ebből a cikkből megtudhatja, hogyan hozhat létre egy alkalmazáson belüli VPN-profilt, és hogyan rendelheti hozzá a profilt az alkalmazásaihoz. Ezekkel a lépésekkel zökkenőmentes, alkalmazáson belüli VPN-élményt hozhat létre a végfelhasználók számára. Az App VPN-t támogató legtöbb VPN esetén a felhasználó megnyit egy alkalmazást, és automatikusan csatlakozik a VPN-hez.

Egyes VPN-EK lehetővé teszik a Felhasználónév és jelszó hitelesítését az alkalmazáson belüli VPN-sel. Azt jelenti, hogy a felhasználóknak felhasználónevet és jelszót kell megadniuk a VPN-hez való csatlakozáshoz.

## <a name="per-app-vpn-with-zscaler"></a>Alkalmazáson belüli VPN és Zscaler

A Zscaler Private Access (ZPA) integrálható a Azure Active Directory (Azure AD) szolgáltatással a hitelesítéshez. A ZPA használatakor nincs szükség a [megbízható tanúsítvány](#create-a-trusted-certificate-profile) -vagy [SCEP-vagy PKCS-tanúsítványok](#create-a-scep-or-pkcs-certificate-profile) profiljaira (ez a cikk ismerteti). Ha a Zscaler beállított felhasználónkénti VPN-profillal rendelkezik, akkor a társított alkalmazások egyikének megnyitása nem kapcsolódik automatikusan a ZPA. Ehelyett a felhasználónak először be kell jelentkeznie a Zscaler alkalmazásba. Ezt követően a távoli hozzáférés a társított alkalmazásokra korlátozódik.

## <a name="prerequisites-for-per-app-vpn"></a>Az alkalmazásonkénti VPN-re vonatkozó előfeltételek

> [!IMPORTANT]
> A VPN-szállító más követelményekkel rendelkezhet az alkalmazáson belüli VPN-hez, például adott hardverhez vagy licenceléshez. Mindenképp ellenőrizze a vonatkozó dokumentációt, és gondoskodjon a követelményeknek való megfelelésről, mielőtt alkalmazásonkénti VPN-t állítana be az Intune-ban.

A VPN-kiszolgáló által identitása igazolásához bemutatott tanúsítványt az eszköznek kérdés nélkül el kell fogadnia. A tanúsítvány automatikus jóváhagyásának megerősítéséhez hozzon létre egy megbízható tanúsítványsablont, amely tartalmazza a hitelesítésszolgáltató (CA) által kiadott legfelső szintű tanúsítványt a VPN-kiszolgáló számára. 

### <a name="export-the-certificate-and-add-the-ca"></a>A tanúsítvány exportálása és a HITELESÍTÉSSZOLGÁLTATÓ hozzáadása

1. A VPN-kiszolgálón nyissa meg a felügyeleti konzolt.
2. Ellenőrizze, hogy a VPN-kiszolgáló tanúsítványalapú hitelesítést használ-e. 
3. Exportálja a megbízható főtanúsítvány fájlját. Ez .cer kiterjesztéssel rendelkezik, és megbízható tanúsítványprofilok létrehozásakor hozzá kell adnia.
4. Adja hozzá a VPN-kiszolgálón való hitelesítéshez használt tanúsítványt kiállító hitelesítésszolgáltató nevét.

    Ha az eszköz által megjelenített HITELESÍTÉSSZOLGÁLTATÓ megfelel a VPN-kiszolgáló megbízható HITELESÍTÉSSZOLGÁLTATÓI listájában található HITELESÍTÉSSZOLGÁLTATÓnak, akkor a VPN-kiszolgáló sikeresen hitelesíti az eszközt.

## <a name="create-a-group-for-your-vpn-users"></a>Csoport létrehozása VPN-felhasználók számára

Hozzon létre vagy válasszon ki egy meglévő csoportot Azure Active Directory (Azure AD) azon felhasználók vagy eszközök számára, amelyek app VPN-t használnak. Új csoport létrehozásához tekintse [meg a csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../fundamentals/groups-add.md)című témakört.

## <a name="create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozása

Importálja az Intune-ban létrehozott profilba a VPN-kiszolgáló a CA által kiadott legfelső szintű tanúsítványát. A megbízható tanúsítványprofil arra utasítja az iOS-eszközt, hogy tekintse automatikusan megbízhatónak a VPN-kiszolgáló által bemutatott CA-t.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:
    - **Name**
    - **Leírás**
    - **Platform**: Válassza az **iOS**lehetőséget.
    - **Profil típusa**: Válassza a **megbízható tanúsítvány**lehetőséget.
4. Válassza ki a mappa ikont, és keresse meg a VPN-felügyeleti konzolról exportált VPN-tanúsítványt (. cer fájlt). 
5. Kattintson **az OK** > **Létrehozás**gombra.

    ![Megbízható tanúsítvány profil létrehozása iOS-eszközökhöz a Microsoft Intuneban](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>SCEP-vagy PKCS-tanúsítvány profiljának létrehozása

A megbízható főtanúsítvány-profil lehetővé teszi, hogy az eszköz automatikusan megbízzon a VPN-kiszolgálón. A SCEP vagy a PKCS tanúsítvány hitelesítő adatokat biztosít az iOS VPN-ügyféltől a VPN-kiszolgáló felé. A tanúsítvány lehetővé teszi az eszköz beavatkozás nélküli hitelesítését Felhasználónév és jelszó kérése nélkül. 

Az ügyfél-hitelesítési tanúsítvány konfigurálásához és hozzárendeléséhez tekintse meg az alábbi cikkek egyikét:

- [Infrastruktúra konfigurálása az Intune-nal való SCEP támogatásához](../protect/certificates-scep-configure.md)
- [PKCS-tanúsítványok konfigurálása és kezelése az Intune-nal](../protect/certficates-pfx-configure.md)

Ügyeljen arra, hogy konfigurálja a tanúsítványt az ügyfél-hitelesítéshez. Ezt közvetlenül is megadhatja a SCEP-tanúsítvány profiljaiban (**Kibővített kulcshasználat** lista > **ügyfél-hitelesítés**). A PKCS beállításnál állítsa be az ügyfél-hitelesítést a hitelesítésszolgáltató (CA) tanúsítvány sablonjában.

![Hozzon létre egy SCEP-tanúsítványsablont a Microsoft Intuneban, beleértve a tulajdonos nevének formátumát, a kulcshasználat, a kibővített kulcshasználat és egyebeket.](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Alkalmazásonkénti VPN-profil létrehozása

A VPN-profil tartalmazza a SCEP vagy a PKCS-tanúsítványt az ügyfél hitelesítő adataival, a VPN-kapcsolati információkkal és az alkalmazáson belüli VPN-jelzővel, amely lehetővé teszi az iOS-alkalmazás által használt alkalmazások közötti VPN-szolgáltatást.

1. Az **Intune**-ban válassza az **eszköz konfigurációs** > **profilok** > **profil létrehozása**lehetőséget. 
2. Adja meg a következő tulajdonságokat: 
    - **Name**
    - **Leírás**
    - **Platform**: Válassza az **iOS**lehetőséget.
    - **Profil típusa**: Válassza a **VPN**lehetőséget.
3. A **kapcsolat típusa**területen válassza ki a VPN-ügyfélalkalmazás elemet.
4. Válassza az **Alapszintű VPN** lehetőséget. az [iOS-es VPN-beállítások](vpn-settings-ios.md) listája és az összes beállítás leírása. Az alkalmazáson belüli VPN használatakor ügyeljen rá, hogy a következő tulajdonságokat adja meg a listával: 
    
    - **Hitelesítési módszer**: Válassza a **tanúsítványok**lehetőséget. 
    - **Hitelesítési tanúsítvány**: Válasszon ki egy meglévő SCEP vagy PKCS-tanúsítványt > **az OK gombra**.      
    - **Megosztott bújtatás**: A **Letiltás** lehetőség kiválasztásával kényszerítheti az összes FORGALMAT a VPN-alagút használatára, amikor a VPN-kapcsolat aktív. 

      ![Egy alkalmazáson belüli VPN-profilban adja meg a kapcsolat, az IP-cím vagy a teljes tartománynév, a hitelesítési módszer és a felosztott bújtatás Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    További információt a további beállításokról az [iOS VPN-beállítások](vpn-settings-ios.md)című témakörben talál.

5. Válassza > kiazautomatikus > VPN-**alapú VPN-** típus automatikus VPN-típusát

    ![Az Intune-ban állítsa be az automatikus VPN-t az alkalmazáson belüli VPN-re iOS-eszközökön](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Kattintson az **OK** > **OK** > **Létrehozás**gombra.

## <a name="associate-an-app-with-the-vpn-profile"></a>Alkalmazás társítása a VPN-profillal

Miután hozzáadta a VPN-profilt, társítsa az alkalmazást és a Microsoft Azure Active Directory-csoportot a profillal.

1. Az **Intune-ban** válassza az **Ügyfélalkalmazások** > **Alkalmazások** elemet.
2. Válasszon ki egy alkalmazást a listáról > > hozzárendelések**hozzáadása csoportot**.
3. A **hozzárendelés típusa**mezőben válassza a **kötelező** vagy **a regisztrált eszközök számára elérhető**lehetőséget.
4. Jelölje be a belefoglalt **csoportok** > kiválasztása lehetőséget > Válassza ki a [létrehozott](#create-a-group-for-your-vpn-users) csoportot (ebben a cikkben) > **válassza ki**.
5. A **VPN**-EK területen válassza ki a [létrehozott](#create-a-per-app-vpn-profile) app VPN-profilt (ebben a cikkben).

    ![Alkalmazás társítása az alkalmazáson belüli VPN-profilhoz Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. Kattintson **az OK** > **Mentés**gombra.

Az alkalmazás és a profil közötti társítás el lesz távolítva az eszköz következő beadásakor, ha az alábbi feltételek mindegyike teljesül:

- Az alkalmazás meg lett jelölve kötelező telepítéshez.
- A profil és az alkalmazás ugyanazt a csoportot célozza.
- Az alkalmazásonkénti VPN-konfigurációt eltávolítja az alkalmazás-hozzárendelésből.

Egy alkalmazás és egy profil közötti társítás mindaddig fennáll, amíg a felhasználó újra nem kéri a Céges portált, ha az alábbi feltételek mindegyike teljesül:

- Az alkalmazás meg lett jelölve választható telepítéshez.
- A profil és az alkalmazás ugyanazt a csoportot célozza.
- A végfelhasználó kért alkalmazást a Céges portál, amely az alkalmazás és a profil telepítését végzi az eszközön.
- Módosítja az alkalmazásonkénti VPN-konfigurációt, illetve eltávolítja az alkalmazás-hozzárendelésből.

## <a name="verify-the-connection-on-the-ios-device"></a>A kapcsolat ellenőrzése az iOS-eszközön

Az alkalmazásonkénti VPN beállítását és az alkalmazáshoz való társítását követően ellenőrizze, hogy az internetkapcsolat megfelelően működik-e az eszközről.

### <a name="before-you-attempt-to-connect"></a>Mielőtt megpróbálna kapcsolódni

- Győződjön meg arról, hogy az összes fent említett szabályzatot ugyanarra a csoportra telepíti. Ellenkező esetben az alkalmazáson belüli VPN-élmény nem fog működni.
- Ha a Pulse Secure VPN-alkalmazást vagy egy egyéni VPN-ügyfélalkalmazás használatát használja, dönthet úgy, hogy az alkalmazás-réteg vagy a csomagszűrő bújtatást használja. A **Szolgáltatótípus** értékét az alkalmazásrétegbeli alagútkezeléshez állítsa az **alkalmazásproxy** lehetőségre, a csomagrétegbeli alagútkezeléshez pedig állítsa a **csomagalagút** lehetőségre. Ellenőrizze a VPN-szolgáltató dokumentációját, és győződjön meg róla, hogy a megfelelő értéket használja.

### <a name="connect-using-the-per-app-vpn"></a>Alkalmazásonkénti VPN-en keresztüli csatlakozás

A VPN kiválasztása vagy a hitelesítő adatok megadása nélküli csatlakozással ellenőrizze a beavatkozás nélküli működést. A beavatkozás nélküli működés azt jelenti, hogy:

- Az eszköz nem kéri a VPN-kiszolgáló megbízhatóságának megadását. Vagyis a felhasználó nem látja a **dinamikus megbízhatóság** párbeszédpanelt.
- A felhasználónak nem kell beírnia a hitelesítő adatokat.
- A felhasználó eszköze akkor csatlakozik a VPN-hez, amikor a felhasználó megnyitja az egyik társított alkalmazást.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>További lépések

- Az iOS-es beállítások ellenőrzéséhez lásd: [iOS-eszközökre vonatkozó VPN-beállítások a Microsoft Intune-ban](vpn-settings-ios.md).
- A VPN-beállításokkal és az Intune-nal kapcsolatos további tudnivalókért lásd: [VPN-beállítások konfigurálása Microsoft Intuneban](vpn-settings-configure.md).
