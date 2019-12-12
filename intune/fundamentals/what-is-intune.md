---
title: Mi az Microsoft Intune – Azure | Microsoft Docs
description: Ismerje meg, hogyan Microsoft Intune a Enterprise Mobility + Security megoldás mobileszköz-kezelési (MDM-) és Mobile App Management (MAM) összetevője, és hogyan segít a vállalati adatvédelemben.
keywords: Mi az az Intune?
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3c03c67a99b78804c999250f8d1148a4b3d1d97
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504764"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune az eszközök MDM és MAM-szolgáltatója

A Microsoft Intune egy felhőalapú szolgáltatás, amely a mobileszköz-felügyeletre (MDM) és a mobileszköz-felügyeletre (MAM) koncentrál. Az Intune megtalálható a Microsoft [Enterprise Mobility + Security (EMS) csomagjában](https://www.microsoft.com/microsoft-365/enterprise-mobility-security), és lehetővé teszi a felhasználók számára a hatékony munkavégzést a szervezet adatai védelmének megőrzése mellett. Integrálható más szolgáltatásokkal, többek között a Microsoft 365 és az Azure Active Directory (Azure AD), amelyekkel szabályozhatja, hogy ki férhet hozzá, és hogy mire van hozzáférésük, és Azure Information Protection az adatvédelem érdekében. Ha Microsoft 365 használatával használja, lehetővé teheti, hogy a munkaerő minden eszközén hatékony legyen, miközben gondoskodik a szervezet adatainak védelméről.

![Kép az Intune architektúrájáról](./media/what-is-intune/intunearch_sm.png)

Az Intune architektúráját szemléltető diagramot [nagyobb méretben](./media/what-is-intune/intunearchitecture.svg) is megnézheti.

Az Intune-nal a következőkre nyílik lehetősége:

- Az Intune-nal a 100%-os felhőt kell választania, vagy a Configuration Manager és az Intune-nal együtt kell [felügyelni](https://docs.microsoft.com/sccm/comanage/overview) .
- Szabályok beállítása és beállítások konfigurálása a személyes és a szervezet tulajdonában lévő eszközökön az adateléréshez és a hálózatokhoz.
- Alkalmazások üzembe helyezése és hitelesítése a helyszíni és a mobil eszközökön.
- Gondoskodjon a vállalati adatok biztonságáról a felhasználók hozzáférésének és megosztásának módjának szabályozásával.
- Győződjön meg arról, hogy az eszközök és alkalmazások megfelelnek a biztonsági követelményeknek.

## <a name="manage-devices"></a>Kezelje az eszközöket

Az Intune-ban az eszközöket az Ön számára legmegfelelőbb megközelítéssel kezelheti. A szervezet tulajdonában lévő eszközök esetében teljes hozzáférésre lehet szükség az eszközökön, beleértve a beállításokat, a funkciókat és a biztonságot. Ebben a megközelítésben az eszközök és a felhasználók az Intune-ban regisztrálva vannak. A regisztrációt követően a szabályok és beállítások az Intune-ban konfigurált szabályzatokon keresztül kapják meg a szabályokat és a beállításokat. Beállíthatja például a jelszó-és PIN-követelmények, a VPN-kapcsolat létrehozását, a fenyegetések elleni védelem beállítását és egyebeket.

A személyes eszközökhöz vagy a saját eszközökhöz (BYOD) a felhasználók nem dönthetnek arról, hogy a szervezet rendszergazdái teljes körű felügyeletet biztosítanak. Ebben a megközelítésben adja meg a felhasználók beállításait. Például a felhasználók [regisztrálhatják](../enrollment/device-enrollment.md) eszközeiket, ha teljes hozzáférést szeretnének a szervezeti erőforrásokhoz. Vagy ha ezek a felhasználók csak az e-mailekhez vagy a Microsoft Teams szolgáltatáshoz szeretnének hozzáférni, akkor használja ezeket az alkalmazásokat a multi-Factor Authentication (MFA) szolgáltatást igénylő alkalmazás-védelmi házirendekkel.

Az eszközök Intune-beli regisztrálásakor és kezelésekor a rendszergazdák a következőket tehetik:

- Megtekintheti a regisztrált eszközök listáját, és leltárt kaphat a szervezeti erőforrásokhoz hozzáférő eszközökről.
- Konfigurálja az eszközöket úgy, hogy azok megfeleljenek a biztonsági és az egészségvédelmi szabványoknak. Például valószínűleg le szeretné tiltani a feltört eszközöket.
- Tanúsítványok leküldése az eszközökre, így a felhasználók könnyedén hozzáférhetnek a Wi-Fi-hálózathoz, vagy használhatnak VPN-t a hálózathoz való csatlakozáshoz.
- Tekintse meg a megfelelő és nem megfelelő felhasználók és eszközök jelentéseit.
- Ha egy eszköz elvesztése, ellopása vagy használata már nem történik meg, távolítsa el a szervezeti adategységeket.

**Online erőforrások**:

- [Mi az eszközregisztrálás?](../enrollment/device-enrollment.md)

- [Szolgáltatások és beállítások alkalmazása az eszközön az eszközök profiljainak használatával](../configuration/device-profiles.md)

- [Eszközök védelme a Microsoft Intune-nal](../protect/device-protect.md)

## <a name="manage-apps"></a>Alkalmazások kezelése

Az Intune-ban a mobileszköz-felügyelet (MAM) úgy van kialakítva, hogy az alkalmazás szintjén, beleértve az egyéni alkalmazásokat és az áruházbeli alkalmazásokat is. Az alkalmazások felügyelete a szervezet tulajdonában lévő eszközökön és a személyes eszközökön is használható.

Ha az alkalmazásokat az Intune-ban felügyelik, a rendszergazdák a következőket végezhetik el:

- Mobil alkalmazások hozzáadása és kiosztása felhasználói csoportokhoz és eszközökhöz, beleértve az adott csoportokban lévő felhasználókat, az adott csoportokban található eszközöket és egyebeket.
- Beállíthatja, hogy az alkalmazások a megadott beállításokkal induljon el vagy fussanak, és frissítse a már meglévő alkalmazásokat az eszközön.
- Tekintse meg a jelentéseket, amelyeken az alkalmazások használatban vannak, és kövesse nyomon a használatot.
- Szelektív törléssel csak a szervezet adatait távolíthatja el az alkalmazásokból.

Az Intune a Mobile App Security szolgáltatással való ellátásának egyik módja az **[alkalmazás-védelmi szabályzatok](../apps/app-protection-policy.md)** használata. Alkalmazás-védelmi szabályzatok:

- Az Azure AD Identity használatával elkülönítheti a szervezeti adatok személyes adatokból való elkülönítését. A személyes adatok elkülöníthetők a szervezeti informatikai szakismeretektől. A szervezet hitelesítő adataival elért adatok további biztonsági védelmet kapnak.
- A felhasználók által elvégezhető műveletek (például másolás és beillesztés, mentés és megtekintés) korlátozásával biztonságosabbá teheti a személyes eszközök hozzáférését.
- Az Intune-ban regisztrált eszközökön hozhatók létre és helyezhetők üzembe, egy másik MDM-szolgáltatásban regisztrálva vannak, vagy nem regisztrálhatók semmilyen MDM szolgáltatásban. A regisztrált eszközökön az App Protection-szabályzatok további védelmi réteget adhatnak hozzá.

Például egy felhasználó bejelentkezik egy eszközre a szervezeti hitelesítő adataival. A szervezeti identitásuk lehetővé teszi a személyes identitásnak megtagadott adatok elérését. A szervezeti adathasználatot illetően az alkalmazás védelmi házirendjei vezérlik az adatmentést és-megosztást. Ha a felhasználók személyes identitással jelentkeznek be, akkor az azonos védelem nem alkalmazható. Ily módon felügyelheti a szervezeti adatokat, míg a végfelhasználók a személyes adataik felett kezelhetik az irányítást és az adatvédelmet.

Emellett az Intune-t az EMS egyéb szolgáltatásaival is használhatja. Ez a funkció az operációs rendszer és az alkalmazások számára elérhetővé teszi az Ön szervezete számára a mobil alkalmazások biztonságát. Az EMS-szel kezelt alkalmazások hozzáférhetnek a mobil alkalmazások és adatvédelmi funkciók szélesebb köréhez.

![Az alkalmazásfelügyelet adatvédelmi szintjeit bemutató ábra](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>Megfelelőség és feltételes hozzáférés

Az Intune az Azure AD-vel együttműködve a hozzáférés-vezérlési forgatókönyvek széles választékát teszi elérhetővé. Például megkövetelheti, hogy a mobileszközök megfeleljenek az Intune-ban definiált szervezeti szabványoknak, mielőtt hozzáférnek a hálózati erőforrásokhoz, például e-mailekhez vagy SharePointhoz. Hasonlóképpen leállíthatja a szolgáltatásokat, hogy azok csak a mobileszközök adott készletén legyenek elérhetők. Zárolhatja például az Exchange Online-t, hogy az csak az Outlook vagy az Outlook Mobile használatával legyen elérhető.

**Online erőforrások**:

- [Szabályok beállítása az eszközökön a szervezet erőforrásaihoz való hozzáférés engedélyezéséhez](../protect/device-compliance-get-started.md)

- [A feltételes hozzáférés használatának gyakori módjai az Intune-nal](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Az Intune beszerzése

Az Intune elérhető:

- Önálló [Azure-szolgáltatásként](https://go.microsoft.com/fwlink/?linkid=2090973)
- [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) és [Microsoft 365 Government](https://www.microsoft.com/microsoft-365/government) része
- A [mobileszköz-kezelés az Office 365-ben](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22), amely néhány korlátozott Intune-funkciót tartalmaz

Az Intune számos ágazatban használatos, beleértve a [kormányzatot](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), az [oktatást](https://www.microsoft.com/en-us/education/intune), a [kioszkot vagy a dedikált eszközt](../configuration/kiosk-settings.md) a gyártáshoz és a kereskedelemhez.

## <a name="next-steps"></a>További lépések

- Olvassa el az [Intune által feloldható gyakori üzleti problémákat](https://docs.microsoft.com/intune/common-scenarios).
- Kezdje egy [30 napos Intune-próbaverzióval](free-trial-sign-up.md).
- Tervezze meg az [Intune-ba való áttelepítést](migration-guide.md).
- Az ingyenes próbaverzió vagy előfizetés használatával lépjen be a gyors üzembe helyezési útmutatóba [: hozzon létre egy e-mail-eszköz profilt az iOS-hez](../configuration/quickstart-email-profile.md).
