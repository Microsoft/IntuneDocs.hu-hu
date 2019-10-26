---
title: Windows Holographic rendszerű eszközök használata a Microsoft Intune-nal – Azure | Microsoft Docs
description: Windows Holographic for Business és HoloLens rendszerű eszközökön sokféle feladatot felügyelhet és végrehajthat a Microsoft Intune használatával, egyebek között konfigurálhatja a Céges portált, létrehozhat megfelelőségi szabályzatokat, testre szabhat OMA-URI-beállításokat, üzembe helyezhet alkalmazásokat, csoportokba sorolhat eszközöket, profilokat hozhat létre, eszközöket korlátozhat, szoftverfrissítéseket engedélyezhet, beállíthat használati feltételeket, konfigurálhatja a VPN- és Wi-Fi-beállításokat és használhatja a Vállalati Windows Hellót.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 585a2f17-106b-4f02-adf7-05f08a92dbc1
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e648d2eff8fd95cd3c995e9cce1bd0c9dfff32da
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889522"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Különböző Eszközkezelő funkciók kezelése és használata Windows holografikus és HoloLens eszközökön az Intune-nal

A Microsoft Intune számos olyan szolgáltatást biztosít, amelyek segítenek a Windows Holographic for Business rendszert futtató eszközök, például a [Microsoft HoloLens](https://docs.microsoft.com/hololens/) felügyeletében. Az Intune használatával ellenőrizhető, hogy az eszközök megfelelnek-e a szervezeti szabályoknak, és az eszközök testreszabása is elvégezhető VPN- vagy Wi-Fi-profilok hozzáadásával. Egy másik fontos funkció az eszközök kioszkként való használata és egy bizonyos alkalmazás vagy alkalmazáskészlet futtatása.

A cikkben ismertetett feladatok segítséget nyújtanak a Windows Holographic for Business rendszert futtató eszközök felügyeletében, testreszabásában és védelmében, beleértve a szoftverfrissítések telepítését és a Vállalati Windows Hello használatát.

A Windows Holographic rendszerű eszközök Intune-nal való használatához hozzon létre egy kiadásfrissítési profilt. Ez a frissítési profil frissíti az eszközöket a Windows Holographic rendszerről a Windows Holographic for Business rendszerre. A Microsoft HoloLens esetében a frissítéshez szükséges licenc beszerzéséhez megvásárolhatja a Commercial Suite-ot is. További információt [A Windows Holographic operációs rendszert futtató eszközök frissítése a Windows Holographic for Business verzióra](../configuration/holographic-upgrade.md) című témakörben talál.

## <a name="azure-active-directory"></a>Azure Active Directory

Az Azure Active Directory (AD) segítségével könnyedén kezelheti és vezérelheti a Windows Holographic for Business rendszerű eszközeit. Az Intune és az Azure AD használatával: 

- **[Eszközök csatlakoztatása a Azure Active Directoryhoz](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)** : a Azure Active Directory (ad) szolgáltatásban felveheti a munkahelyi Windows 10-es eszközeit, beleértve a Windows holografikus for Business rendszert futtató eszközöket is. Ez a funkció lehetővé teszi, hogy az Azure AD vezérelje az eszközt. Ez segít biztosítani, hogy a felhasználói olyan eszközökről érjék el a vállalati erőforrásokat, amelyek megfelelnek a vállalat biztonsági és megfelelőségi szabványainak.

  [Az Azure ad-beli eszközkezelés](https://docs.microsoft.com/azure/active-directory/devices/overview) további részleteket tartalmaz.

- **[Csoportos regisztráció Windows-eszközök esetében](../enrollment/windows-bulk-enroll.md)** : Egyszerre nagy számú új windowsos eszközt is csatlakoztathat az Azure Active Directoryhoz és az Intune-hoz. Ezt a szolgáltatást csoportos regisztrációnak hívják, és kiépítési csomagokat használ. Ezek a csomagok összekötik a Windows Holographic for Business rendszerű eszközöket az Azure AD-bérlővel, és regisztrálják őket az Intune-ban.

## <a name="company-portal"></a>Céges portál
**[A Céges portál alkalmazás konfigurálása](../apps/company-portal-app.md)**

Az Intune a Céges port alkalmazást biztosítja a felhasználók részére, ahol egyebek között hozzáférhetnek a vállalat adataihoz, eszközöket regisztrálhatnak, alkalmazásokat telepíthetnek és kapcsolatba léphetnek az IT-részleggel. A Céges portál alkalmazás testre szabható a Windows Holographic for Bussines rendszerű eszközökhöz.

A Céges portál alkalmazással a következő műveleteket is futtathatja:

- [Eszköz eltávolítása az Intune-ból](/intune-user-help/unenroll-your-device-from-intune-windows) a Gépház alkalmazás vagy a Céges portál alkalmazás használatával
- [Eszköz átnevezése](/intune-user-help/rename-your-device-cpapp)
- [Alkalmazások telepítése](/intune-user-help/install-apps-cpapp-windows) az eszközön
- [Eszközök manuális szinkronizálása](/intune-user-help/sync-your-device-manually-windows) a Gépház alkalmazásból vagy a Céges portál alkalmazásból

## <a name="compliance-policy"></a>Megfelelőségi szabályzat
**[Eszközmegfelelőségi szabályzat létrehozása](../protect/compliance-policy-create-windows.md)**

A megfelelőségi szabályzatok olyan szabályok és beállítások, amelyeknek az eszközöknek eleget kell tenniük, hogy megfelelőnek minősüljenek. Ezeket a szabályzatokat feltételes hozzáféréssel használva blokkolhatja a vállalati erőforrásokhoz való hozzáférést a nem megfelelő eszközökhöz. Az Intune-ban létrehozhat a Windows Holographic for Business rendszerű eszközök hozzáférését engedélyező vagy tiltó megfelelőségi szabályzatokat is. Létrehozhat például olyan szabályzatot, amely megköveteli a Bitlocker engedélyezését.

Lásd még: **[Első lépések a megfelelőségi szabályzatokkal](../protect/device-compliance-get-started.md)** .

## <a name="deploy-and-manage-apps"></a>Alkalmazások központi telepítése és kezelése
**[Alkalmazások hozzáadása az Intune-hoz](../apps/apps-add.md)**

Az Intune használatával alkalmazásokat adhat hozzá a Windows Holographic for Business rendszerű eszközeihez. Alkalmazások telepítésére több mód is van, többek között:

- [Microsoft Áruházbeli alkalmazások hozzáadása](../apps/store-apps-windows.md)
- [Saját készítésű alkalmazások hozzáadása](../apps/lob-apps-windows.md)
- [Alkalmazások hozzárendelése csoportokhoz](../apps/apps-deploy.md)

A Microsoft Intune-nal univerzális Windows-alkalmazások telepíthetők a Windows Holographic for Business rendszert futtató Microsoft HoloLens-eszközökre. Az alkalmazáscsomagok közvetlenül feltölthetők az Intune Azure Portalon, vagy üzembe helyezhetők a Microsoft Store Vállalatoknak áruházból. A kapcsolódó témakörökről az alábbi cikkek nyújtanak bővebb információt:
- Üzletági alkalmazások telepítéséről az Intune Azure Portalon: [Windowsos üzletági alkalmazások hozzáadása a Microsoft Intune-hoz](../apps/lob-apps-windows.md).

    > [!NOTE]
    > Az Intune legfeljebb 8 GB csomagméretet engedélyez. Ez a csomagméret csak az Intune-ba feltöltött üzletági alkalmazásokhoz érhető el.

- Alkalmazások telepítéséről a Microsoft Store Vállalatoknak áruházból: [A Microsoft Store Vállalatoknak áruházban vásárolt alkalmazások kezelése a Microsoft Intune-nal](../apps/windows-store-for-business.md). 
- Alkalmazások kezeléséről a Microsoft Intune-nal: [Alkalmazáskezelés a Microsoft Intune-ban](../apps/app-management.md).
- A Microsoft HoloLensre készülő alkalmazások fejlesztéséről: [Vegyes valóság alkalmazások a Microsoft HoloLenshez](https://www.microsoft.com/hololens/apps). 

> [!NOTE]
> A Windows 10 Holographic for Business 1607 rendszerű HoloLens-eszközök nem támogatják a Microsoft Store Vállalatoknak áruházból származó, online licencelt alkalmazásokat. További információ: [Alkalmazások telepítése a HoloLens-re](/hololens/holographic-store-apps).

## <a name="device-actions"></a>Eszközműveletek
Az Intune rendelkezik néhány olyan beépített funkcióval, amelyek használatával a rendszergazdák különböző műveleteket végezhetnek lokálisan az eszközön, vagy távoli eléréssel az Intune-ban az Azure Portalról. A saját tulajdonban lévő, Intune-ban regisztrált eszközeikre a felhasználók is kiadhatnak egy távoli parancsot az Intune céges portálon keresztül.

Windows Holographic for Business rendszert futtató eszközök használata esetén a következő műveletek végezhetők: 

- **[Összes adat törlése:](../remote-actions/devices-wipe.md#wipe)** Az **Összes adat törlése** művelet eltávolítja az eszközt az Intune-ból, és visszaállítja az eszköz gyári alapértelmezett beállításait. Ezt a műveletet akkor érdemes használni, mielőtt az eszközt egy új felhasználónak adják, vagy ha az eszköz elveszett, vagy ellopták.

- **[Kivonás:](../remote-actions/devices-wipe.md#retire)** A **Kivonás** művelet eltávolítja az eszközt az Intune-ból. Az Intune által hozzárendelt felügyelt alkalmazások adait, beállításokat és e-mail-profilokat is eltávolítja. A felhasználó személyes adatai az eszközön maradnak.

- **[Eszköz szinkronizálása a legfrissebb szabályzatok és műveletek hozzáadásához](../remote-actions/device-sync.md)** : A **Szinkronizálás** művelettel kényszeríteni lehet az eszközt, hogy azonnal csatlakozzon az Intune-hoz. Bejelentkezéskor az eszköz azonnal fogadja az hozzárendelt összes függőben lévő műveletet vagy szabályzatot. Ez a funkció segíthet ellenőrizni a vonatkozó szabályzatokat és elhárítani a hibákat anélkül, hogy ki kellene várni a következő ütemezett bejelentkezést.

**[A Microsoft Intune-eszközfelügyelet ismertetése](../remote-actions/device-management.md)**  című cikkből további részleteket is megtudhat az Azure Portal használatával történő eszközkezelésről. 

## <a name="device-categories-and-groups"></a>Eszközkategóriák és csoportok
**[Eszközök csoportokba sorolása](../enrollment/device-group-mapping.md)**

Az Intune használatával eszközkategóriákat hozhat létre, hogy azok alapján automatikusan hozzáadja az eszközöket az olyan csoportokhoz, mint az Értékesítés, Könyvelés, Emberi erőforrások stb. A cél a Windows Holographic for Business rendszerű eszközök felügyeletének megkönnyítése.

## <a name="device-configuration-profiles"></a>Eszközkonfigurációs profilok 
**[Első lépések a konfigurációs profilokkal](../configuration/device-profiles.md) és [saját profil létrehozása](../configuration/device-profile-create.md)**

Az Intune olyan beállításokat és funkciókat kínál, amelyeket Ön engedélyezhet vagy letilthat a vállalatához tartozó különböző eszközökön. Ezek a beállítások és funkciók profilok használatával kezelhetők. Létrehozhat például olyan profilt, amely a Cortanát engedélyezi vagy a Windows Defender SmartScreent használja a Windows Holographic for Business rendszerű eszközein.

Profiljaiban OMA-URI használatával testre szabhat néhány beállítást, létrehozhat eszközkorlátozásokat és konfigurálhatja a virtuális magánhálózatokat (VPN) és a Wi-Fit.

### <a name="custom-device-settingsconfigurationcustom-settings-windows-holographicmd"></a>[Egyéni eszközbeállítások](../configuration/custom-settings-windows-holographic.md)

Az OMA-URI (Open Mobile Alliance Uniform Resource Identifier) konfigurálásához egyéni profilt hozhat létre az Intune-ban. Az OMA-URI beállítások használatával a Windows Holographic for Business rendszerű eszközök olyan funkcióit szabályozhatja, mint a VPN engedélyezése vagy a frissítések keresése a Microsoft Update szolgáltatásban.

### <a name="configure-kiosk-modeconfigurationkiosk-settings-holographicmd"></a>[Teljes képernyős mód konfigurálása](../configuration/kiosk-settings-holographic.md)

Az Intune-ban elérhető megosztott vagy vendégszámítógép funkciókkal konfigurálhatja a Windows Holographic for Business eszközöket teljes képernyős módban való futtatásra. Ezek az eszközök futtathatnak egyetlen alkalmazást (egyalkalmazásos kioszkmód) vagy több alkalmazást (többalkalmazásos kioszkmód).

### <a name="device-restrictionsconfigurationdevice-restrictions-windows-holographicmd"></a>[Eszközkorlátozások](../configuration/device-restrictions-windows-holographic.md)

Az eszközkorlátozásokkal többek között az eszközök olyan beállításai és funkciói szabályozhatók, mint a jelszó megkövetelése, alkalmazások telepítése a [Microsoft Áruházból](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) vagy a Bluetooth engedélyezése. Ezek a korlátozások egy Intune-profilban jönnek létre. Ez a profil több Windows Holographic for Business rendszerű eszközön is alkalmazható.

### <a name="configure-vpnconfigurationvpn-settings-configuremd"></a>[VPN konfigurálása](../configuration/vpn-settings-configure.md)

A virtuális magánhálózatok (VPN) segítségével biztonságos távoli hozzáférést biztosíthat felhasználóinak a vállalati hálózathoz. Az Intune-ban létrehozhat a Windows Holographic for Business rendszerű eszközeire vonatkozó beállításokat tartalmazó VPN-profilt. Létrehozhat például egy VPN-profilt, hogy minden Windows Holographic for Business rendszerű eszköz Citrix VPN-t használjon kapcsolattípusként.

### <a name="configure-wi-ficonfigurationwi-fi-settings-configuremd"></a>[Wi-Fi konfigurálása](../configuration/wi-fi-settings-configure.md)

Az Intune-ban Wi-Fi-profilt is létrehozhat, amellyel vezeték nélküli hálózati beállításokat rendel a Windows Holographic for Business rendszerű eszközeihez. Wi-Fi-profil hozzárendelésekor a végfelhasználók a hálózat konfigurálása nélkül kapnak vállalati hálózati hozzáférést. Létrehozhat például egy Wi-Fi hálózatot külön a Windows Holographic for Business rendszerű eszközöknek.

## <a name="shared-multi-user-devices"></a>Többfelhasználós megosztott eszközök
[Megosztott eszközök](../configuration/shared-user-device-settings-windows-holographic.md)

A Windows holografikus for Business rendszert futtató eszközök, például a Microsoft HoloLens több felhasználóval is rendelkezhetnek. Az Intune olyan beállításokat tartalmaz, amelyek a megosztott eszközök különböző funkcióit vezérlik, például az energiagazdálkodást, a helyi tárterületet és a fiókok kezelését. A konfigurációs profilok a különböző operációs rendszerekkel rendelkező eszközökre is alkalmazhatók. Például az eszközök csoport rendelkezhet olyan eszközökkel, amelyek RS2 és RS3 futtatnak ugyanabban a csoportban.

## <a name="software-updates"></a>Szoftverfrissítések
**[Szoftverfrissítések kezelése](../protect/windows-update-for-business-configure.md)**

Az Intune tartalmaz egy frissítési körök nevű funkciót a Windows 10-es eszközökhöz. A frissítési körökhöz tartozik a frissítések telepítési módját meghatározó beállítások egy csoportja. Létrehozhat például egy karbantartási időszakot a frissítések telepítésére vagy eldöntheti, hogy kíván-e újraindítást a frissítések telepítése után. Egy frissítési kör több Windows Holographic for Business rendszerű eszközre is alkalmazható.

## <a name="terms-and-conditions"></a>használati feltételei
**[A vállalati felhasználói hozzáférési használati feltételek megadása](../enrollment/terms-and-conditions-create.md)**

Megkövetelheti, hogy a felhasználók csak a használati feltételek elfogadása után regisztrálhassák eszközeiket és érhessék el a céges alkalmazásokat, köztük a levelezést. Az Intune-ban megadhatja, hogy hogyan jelenjenek meg a használati feltételek a Céges portálon és ezeket a használati feltételeket hozzá is rendelheti a Windows Holographic for Business rendszerű eszközökhöz.

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello
**[A Vállalati Windows Hello használata](../protect/windows-hello.md)**

A Vállalati Windows Hello egy alternatív bejelentkezési módszer, amely egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett. A Vállalati Windows Hellóval Windows Holographic for Business rendszerű eszközei PIN-kóddal jelentkezhetnek be, amelynek minimális hosszát Ön állítja be.
