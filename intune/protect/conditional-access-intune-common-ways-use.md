---
title: Feltételes hozzáférési forgatókönyvek
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan használják az Intune feltételes hozzáférését az eszköz-és az alkalmazás-alapú feltételes hozzáféréshez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9795ca8a585fd926cc269d493760b37aa7666eb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74051962"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Mik a feltételes hozzáférés az Intune-nal való használatának gyakori módjai?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Az Intune-ban kétféle feltételes hozzáférés létezik: eszközalapú és alkalmazásalapú feltételes hozzáférés. A feltételes hozzáférés megfelelőségének a szervezetben való engedélyezéséhez konfigurálnia kell a kapcsolódó megfelelőségi szabályzatokat. A feltételes hozzáférést általában olyan dolgokhoz használják, mint az Exchange-hez való hozzáférés engedélyezése vagy letiltása, a hálózathoz való hozzáférés szabályozása vagy a Mobile Threat Defense megoldással való integráció.
 
A cikkben található információk segítségével megismerheti, hogyan használható az Intune mobileszköz *-megfelelőségi* képességei és az Intune Mobile *Application* Management (MAM) képességei. 

> [!NOTE]
> A feltételes hozzáférés egy prémium szintű Azure Active Directory-licenc részét képező Azure Active Directory képesség. Az Intune ezt a lehetőséget mobileszköz-megfelelőségi és mobilalkalmazás-felügyeleti megoldások hozzáadásával bővíti tovább. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

## <a name="device-based-conditional-access"></a>Eszköz alapú feltételes hozzáférés

Az Intune és a Azure Active Directory együttműködve gondoskodhat arról, hogy csak a felügyelt és megfelelő eszközök férhessenek hozzá az e-mailekhez, az Office 365-szolgáltatásokhoz, a szolgáltatott szoftverekhez (SaaS) és [a helyszíni alkalmazásokhoz](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Emellett beállíthat egy házirendet a Azure Active Directoryban, hogy csak az Intune-ban regisztrált, tartományhoz csatlakoztatott számítógépeket vagy mobil eszközöket engedélyezze az Office 365-szolgáltatások eléréséhez.

Az Intune biztosítja az eszközök megfelelőségi állapotát értékelő eszközmegfelelőségi szabályzatokat. A megfelelőségi állapotot a rendszer a Azure Active Directory, amely a Azure Active Directoryban létrehozott feltételes hozzáférési szabályzat kikényszeríti a vállalati erőforrásokhoz való hozzáféréskor.

Az Exchange Online-hoz és más Office 365-termékekhez készült eszköz-alapú feltételes hozzáférési szabályzatok a [Azure Portalon](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)keresztül konfigurálhatók.  

- További információ [: a felügyelt eszközök megkövetelése feltételes hozzáféréssel a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices).

- További információ az [Intune eszközmegfelelőségéről](device-compliance-get-started.md).

- További információ a [Azure Active Directory-beli feltételes hozzáféréssel rendelkező támogatott böngészőkről](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers).

> [!NOTE]
> Ha Android-eszközökön engedélyezi az eszközökön alapuló hozzáférést a SharePoint Online-hoz vagy a böngészőalapú hozzáférést az Exchange Online-hoz, a felhasználóknak engedélyeznie kell a **böngészőalapú hozzáférés engedélyezése** beállítást a regisztrált eszközön a következőképpen:
> 1. Nyissa meg a **Vállalati portál alkalmazást**.
> 2. Nyissa meg a **Beállítások** lapot a három ponttal (...) vagy a hardveres menügombbal.
> 3. Kattintson a **Böngészőalapú hozzáférés engedélyezése** gombra. 
> 4. A Chrome böngészőben jelentkezzen ki az Office 365-ből, majd indítsa újra a Chrome-ot.

### <a name="conditional-access-based-on-network-access-control"></a>Hálózati hozzáférés-vezérlésen alapuló feltételes hozzáférés

Az Intune integrálható olyan partnerekkel, mint például a Cisco ISE, az Aruba Clear Pass és a Citrix NetScaler, hogy az Intune-regisztráció és az eszköz megfelelőségi állapota alapján biztosítson hozzáférés-vezérlést.

A felhasználók számára engedélyezheti vagy megtagadhatja a hozzáférést a vállalati Wi-Fi-vagy VPN-erőforrásokhoz, attól függően, hogy a használt eszköz felügyelt és megfelel-e az Intune-eszközök megfelelőségi házirendjeinek.

- További tudnivalókért lásd: [Hálózati hozzáférés-vezérlés (NAC) integrációja az Intune-nal](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Eszközkockázaton alapuló feltételes hozzáférés

Az Intune partneri megállapodást kötött a Mobile Threat Defense forgalmazóival. Ez a szolgáltatás biztonsági megoldást nyújt a mobileszközöket veszélyeztető kártevők, trójai vírusok és egyéb fenyegetések észleléséhez.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Hogyan működik az Intune és a Mobile Threat Defense integrációja?

Ha a mobileszközök telepítve vannak a Mobile Threat Defense-ügynökkel, az ügynök visszaküldi a megfelelőségi állapotot az Intune jelentéskészítési szolgáltatásának, ha a rendszer fenyegetést talál magának a mobileszközön.

Az Intune és a Mobile Threat Defense integrációja az eszköz kockázatán alapuló feltételes hozzáférési döntések során játszik szerepet.

- További tudnivalók: [Intune Mobile Threat Defense](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Feltételes hozzáférés Windows rendszerű számítógépeken

Az asztali számítógépeken ken beállítható feltételes hozzáférés a mobileszközökhöz hasonló lehetőségeket biztosít. Ez a szakasz a feltételes hozzáférés Intune által felügyelt Windows rendszerű gépeken alkalmazható módjait tekinti át.

#### <a name="corporate-owned"></a>Céges tulajdonú eszközök

- Helyszíni **ad-tartományhoz csatlakoztatva:** Ezt a lehetőséget általában olyan szervezetek használják, amelyek ésszerűen kényelmesek ahhoz, hogy a számítógépeket az AD-csoportok házirendjein vagy a System Center Configuration Manageron keresztül kezelhesse.

- **Azure ad-tartományhoz csatlakoztatott és Intune-felügyelet:** Ez a forgatókönyv olyan szervezeteknek szól, amelyeknek először a felhőt szeretnék használni (azaz elsősorban a Cloud Services használatát, amelynek célja a helyszíni infrastruktúra használatának csökkentése) vagy csak felhőalapú (nincs helyszíni infrastruktúra). Az Azure AD-csatlakozás hibrid környezetben jól működik, és lehetővé teszi a Felhőbeli és a helyszíni alkalmazások és erőforrások elérését. Az eszköz csatlakozik az Azure AD-hez, és regisztrálva lesz az Intune-ban, amely feltételes hozzáférési feltételekként használható a vállalati erőforrások eléréséhez.

- **Ad-tartományhoz csatlakoztatott és System Center Configuration Manager:** Az aktuális ág esetében System Center Configuration Manager olyan feltételes hozzáférési képességeket biztosít, amelyek a tartományhoz csatlakoztatott SZÁMÍTÓGÉPeken kívül a meghatározott megfelelőségi feltételeket is kiértékelik:

  - Titkosították-e a számítógépet?

  - A kártevő szoftver telepítve van? Frissítették az eszközt?

  - Jailbreakelték vagy rootolták az eszközt?

#### <a name="bring-your-own-device-byod"></a>Saját eszközök használata (Bring Your Own Device, BYOD)

- **Munkahelyi csatlakozás és Intune-felügyelet:** A felhasználók ebben az esetben a saját eszközeiket csatlakoztatva érhetik el a céges erőforrásokat és szolgáltatásokat. A munkahelyi csatlakoztatás és az eszközök regisztrálása az Intune MDM az eszköz szintű házirendek fogadásához, amelyek egy másik lehetőség a feltételes hozzáférési feltételek kiértékelésére.

További információ a [Azure Active Directory eszköz-kezeléséről](https://docs.microsoft.com/azure/active-directory/devices/overview).

## <a name="app-based-conditional-access"></a>Alkalmazásalapú feltételes hozzáférés

Az Intune és az Azure Active Directory együtt biztosítja, hogy csak felügyelt alkalmazások férhessenek hozzá a céges e-mailekhez vagy más Office 365-szolgáltatásokhoz.

- További tudnivalók: [Alkalmazásalapú feltételes hozzáférés az Intune-nal](app-based-conditional-access-intune.md).

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Intune feltételes hozzáférés helyszíni Exchange-hez

A feltételes hozzáférés használatával az eszközfelügyeleti szabályzatok és az eszközregisztráció állapota alapján engedélyezhető, illetve tiltható a hozzáférés a **helyszíni Exchange-hez**. A feltételes hozzáférés és az eszközmegfelelőségi szabályzat együttes alkalmazásával elérheti, hogy csak megfelelő eszközök férhessenek hozzá a helyszíni Exchange-hez.

A részletesebb vezérléshez speciális feltételes hozzáférési beállításokat is megadhat, például:

- Egyes platformok engedélyezése vagy letiltása.

- Az Intune által nem felügyelt eszközök azonnali letiltása.

Az eszközmegfelelőségi és feltételes hozzáférési szabályzatok alkalmazása esetén a rendszer ellenőrzi a helyszíni Exchange elérésére használt összes eszköz megfelelőségét.

Ha az eszközök nem felelnek meg a megadott feltételeknek, a rendszer végigvezeti a végfelhasználót az eszköz regisztrálásának lépésein az eszköz nem megfelelővé tételével kapcsolatos probléma megoldásához.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>A feltételes hozzáférés működése helyszíni Exchange esetén

A helyszíni Exchange feltételes hozzáférése eltérő módon működik, mint az Azure feltételes hozzáférés-alapú szabályzatai. Az Intune Exchange helyszíni összekötőt az Exchange Serverrel való közvetlen kommunikációra kell telepíteni. Az Intune Exchange Connector lekéri az Exchange-kiszolgálón lévő összes Exchange Active Sync- (EAS-) rekordot, amelyeket az Intune átvesz, és megfeleltet az Intune-eszközrekordoknak. Ezek a rekordok az Intune által regisztrált és felismert eszközöknek felelnek meg. A folyamat engedélyezi vagy tiltja a hozzáférést az e-mailekhez.

Ha az EAS-rekord új, és nem ismeri az Intune-t, az Intune olyan parancsmagot ad ki, amely az Exchange-kiszolgálót az e-mailek elérésének blokkolására utasítja. A folyamat működésével kapcsolatos további részletek:

![Folyamatábra: Feltételes hozzáférés helyszíni Exchange esetén](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. A felhasználó megkísérel hozzáférni a helyszíni Exchange 2010 SP1-es vagy későbbi verziójában tárolt céges e-mailekhez.

2. Ha az eszközt nem az Intune felügyeli, a rendszer letiltja az e-mailek elérését. Az Intune blokk-értesítést küld az EAS-ügyfélnek.

3. Az EAS megkapja a blokk értesítését, áthelyezi az eszközt a karanténba, és elküldi a karanténba helyezett e-mailt, amely hivatkozásokat tartalmaz, így a felhasználók regisztrálhatják eszközeiket.

4. A munkahelyi csatlakozás létrejöttével megtörténik az első lépés ahhoz, hogy az eszköz az Intune felügyelete alá kerüljön.

5. A rendszer regisztrálja az eszközt az Intune-ban.

6. Az Intune egy eszközrekordba képezi le az EAS-rekordot, és menti az eszközmegfelelőségi állapotot.

7. Az eszközök Azure AD-beli regisztrációjának folyamata során a rendszer regisztrálja az EAS-es ügyfél-azonosítót, ami kapcsolatot létesít az Intune-eszközrekord és az EAS-es ügyfél-azonosító között.

8. Az eszközök Azure AD-beli regisztrációja menti az eszköz állapotadatait.

9. Ha a felhasználó teljesíti a feltételes hozzáférési szabályzatokat, az Intune az Intune Exchange Connector segítségével ad ki egy parancsmagot, amely lehetővé teszi a postaláda szinkronizálását.

10. Az Exchange-kiszolgáló elküldi az értesítést az EAS-ügyfélhez, hogy a felhasználó hozzáférhessen az e-mailjeihez.


#### <a name="whats-the-intune-role"></a>Mi az Intune szerepe?

Az Intune kiértékeli és felügyeli az eszköz állapotát.

#### <a name="whats-the-exchange-server-role"></a>Mi az Exchange-kiszolgáló szerepe?

Az Exchange Server API-t és infrastruktúrát biztosít az eszközök karanténba helyezéséhez.

> [!IMPORTANT]
> Ne feledje, hogy az eszközt használó felhasználónak megfelelőségi profillal és Intune-licenccel kell rendelkeznie, hogy az eszköz megfelelőségét kiértékelje. Amennyiben a felhasználóra nem vonatkozik megfelelőségi szabályzat, a rendszer megfelelőként kezeli az eszközt, és egyáltalán nem korlátozza a hozzáférést.

## <a name="next-steps"></a>További lépések

[Feltételes hozzáférés konfigurálása Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Alkalmazás-alapú feltételes hozzáférési szabályzatok beállítása](app-based-conditional-access-intune-create.md)

[Helyszíni Exchange Connector telepítése az Intune-nal](exchange-connector-install.md).

[Feltételes hozzáférési szabályzat létrehozása a helyszíni Exchange-hez](conditional-access-exchange-create.md)
