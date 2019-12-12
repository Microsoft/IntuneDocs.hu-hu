---
title: Hálózati hozzáférés-vezérlés integrálása a Microsoft Intune-nal – Azure | Microsoft Docs
description: A hálózati hozzáférés-vezérlési (NAC) megoldások az Intune-beli eszközök regisztrációját és megfelelőségét ellenőrzik. A NAC bizonyos viselkedéseket tartalmaz, és feltételes hozzáféréssel működik. Tekintse meg az előkészítés lépéseit, valamint a partneri megoldásokat.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b2083a493fd723c649bdfe2b709dbaa4c0ec663
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810279"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Hálózati hozzáférés-vezérlés (NAC) integrálása az Intune-nal

Az Intune hálózati hozzáférés-vezérlő partnerekkel integráltan segít a szervezetek céges adatainak védelmében, amikor egy eszköz helyszíni erőforrásokhoz kísérel meg hozzáférni.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Hogyan védi az Intune és a NAC-megoldások együttese a szervezeti erőforrásokat?

A NAC-megoldások feladata az eszközregisztráció és a megfelelőségi állapot ellenőrzése az Intune-nál, hogy döntést hozhasson a hozzáférésről. Ha az eszköz még nincs regisztrálva, vagy regisztrálva van, de nem felel meg az Intune eszközmegfelelőségi szabályzatának, akkor az eszközt vissza kell irányítani az Intune-ra a regisztráció végrehajtásához, vagy az eszközmegfelelőség ellenőrzése céljából.

### <a name="example"></a>Példa

Regisztrált és az Intune-nál megfelelőnek minősülő eszköz számára a NAC-megoldás engedélyezni fogja a vállalati erőforrásokhoz való hozzáférést. Engedélyezhető vagy letiltható például a felhasználók számára a vállalati Wi-Fi vagy VPN-erőforrásokhoz való hozzáférés.

## <a name="feature-behaviors"></a>Funkciók működési módjai

Azon eszközök, amelyek aktív szinkronizálást végeznek az Intune-nal, nem léphetnek **Megfelelő** / **Nem megfelelő** állapotból **Nem szinkronizált** (vagy **Ismeretlen**) állapotba. Az **Ismeretlen** állapot megfordul azon újonnan regisztrált eszközök számára, amelyek még nem estek át megfelelőségi ellenőrzésen.

Azon eszközök esetében, melyek erőforrásokhoz való hozzáférése le van tiltva, az ezt letiltó szolgáltatásnak minden felhasználót át kell irányítania a [felügyeleti portálra](https://portal.manage.microsoft.com) annak meghatározása érdekében, hogy az eszköz miért van letiltva.  Ha a felhasználók megnyitják az oldalt, az eszközeik megfelelőségét a rendszer szinkron módon újraértékeli.

## <a name="nac-and-conditional-access"></a>NAC és feltételes hozzáférés

A NAC feltételes hozzáféréssel működik a hozzáférés-vezérlési döntések biztosításához. További információ: a [feltételes hozzáférés használatának gyakori módjai az Intune](conditional-access-intune-common-ways-use.md)-ban.

## <a name="how-the-nac-integration-works"></a>Az integrált hálózati hozzáférés-vezérlés működése

A követező listában megtalálhatja annak áttekintését, hogyan működik az integrált hálózati hozzáférés-vezérlés az Intune-nal való integráció esetén. Az első három (1-3.) lépés az előkészítési folyamatot mutatja be. A NAC-megoldás Intune-nal való integrálása után a 4.–9. lépés a folyamatos működést ismerteti.

![A NAC és az Intune közötti együttműködés fogalmi képe](./media/network-access-control-integrate/ca-intune-common-ways-2.png)

1. Partnertől származó NAC-megoldás regisztrációja az Azure Active Directoryban (AAD), és delegált engedélyek megadása az Intune NAC API számára.
2. Partnertől származó NAC-megoldás konfigurálása a megfelelő beállításokkal, beleértve az Intune-felderítési URL-címet.
3. Partnertől származó NAC-megoldás konfigurálása a tanúsítványalapú hitelesítéshez.
4. A felhasználó csatlakozik a vállalati Wi-Fi-hozzáférési ponthoz, vagy VPN kapcsolatot kezdeményez.
5. A partneri NAC-megoldás az Intune-nak továbbítja az eszközinformációkat, és lekérdezi az Intune-tól az eszköz regisztrációját és megfelelőségi állapotát.
6. Ha az eszköz nem minősül megfelelőnek, vagy nincs regisztrálva, akkor a partnertől származó NAC-megoldás az eszköz regisztrálására vagy megfelelőségének biztosítására utasítja a felhasználót.
7. Az eszköz adott esetben megkísérli újból ellenőrizni saját megfelelőségi és regisztrációs állapotát.
8. Ha az eszköz már regisztrálva van és megfelel, a NAC-partnermegoldás megkapja az állapotát az Intune-tól.
9. Sikeresen létrejön a kapcsolat, amelyen keresztül az eszköz hozzáfér a vállalati erőforrásokhoz.

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>Az iOS-eszközökön használt NAC használata a VPN-hez  

- A NAC a következő VPN-kiszolgálókon érhető el anélkül, hogy engedélyezze a NAC-t a VPN-profilban:

  - NAC a Cisco örökölt AnyConnect
  - F5-hozzáférés örökölt
  - Citrix VPN

- A NAC Citrix SSO és F5 hozzáférés esetén is elérhető. A NAC engedélyezése Citrix SSO esetén:

  - A Citrix Gateway 12.0.59 vagy újabb verzióját használja.  
  - A felhasználóknak Citrix SSO 1.1.6 vagy újabb verzióval kell rendelkezniük.
  - [Integrálja a NetScaler](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) -t a NAC Intune-nal a Citrix termék dokumentációjában leírtak szerint.
  - A VPN-profilban válassza az **alapbeállítások** > a **hálózati Access Control (NAC) engedélyezése** > válassza **az Elfogadom lehetőséget.**

  Biztonsági okokból a VPN-kapcsolat 24 óránként le van választva. A VPN-t azonnal újra lehet kapcsolni.

- A NAC engedélyezése F5-hozzáféréshez:

  - Használja az F5 BIG-IP 13.1.1.5. A BIG-IP 14 nem támogatott.
  - A BIG-IP integrálása az Intune-nal a NAC-hoz. Az [áttekintő: az APM konfigurálása eszköz-testhelyzeti ellenőrzésekhez végpont-felügyeleti rendszerekkel](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 útmutató a lépéseket tartalmazza.
  - A VPN-profilban válassza az **alapbeállítások** > a **hálózati Access Control (NAC) engedélyezése** > válassza **az Elfogadom lehetőséget.**

  Biztonsági okokból a VPN-kapcsolat 24 óránként le van választva. A VPN-t azonnal újra lehet kapcsolni.

- A hálózati hozzáférés-vezérlés nem támogatott a következő VPN-ügyfél esetében iOS rendszeren:
  - Cisco AnyConnect

Partnereinkkel dolgozunk, hogy kiszabadítson egy NAC-megoldást ezekre az újabb ügyfelekre. Ha a megoldások készen állnak, a cikk további információkkal fog frissülni.

## <a name="next-steps"></a>További lépések

- [A Cisco ISE integrálása az Intune-nal](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [A Citrix NetScaler integrálása az Intune-nal](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Az F5 BIG-IP Access Policy Manager integrálása az Intune-nal](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-13-0-0/6.html)
- [A HP Aruba ClearPass integrálása az Intune-nal](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Squadra Security Removable Media Manager integrálása az Intune-nal](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
