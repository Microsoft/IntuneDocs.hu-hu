---
title: Az androidos vállalati munkahelyi profilok eszközeinek kezelése Microsoft Intune
titleSuffix: ''
description: A Microsoft Intune felügyeli az Android vállalati munkahelyi profilok eszközeit, így további felügyeleti lehetőségeket és adatvédelmet biztosíthat, amikor a felhasználók személyes Android-eszközeiket használják a munkahelyen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6941b3b79dd690c9861c8efead7f525e56e2b350
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415418"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Androidos munkahelyi profilos eszközök kezelése az Intune-nal

Az Android Enterprise olyan regisztrációs lehetőségeket kínál, amelyek a legnaprakészebb és biztonságos funkciókat biztosítanak a felhasználóknak. Az androidos vállalati munkahelyi profil beléptetése lehetővé teszi olyan szolgáltatások és szolgáltatások készletét, amelyek elkülönítik a személyes alkalmazásokat és a munkahelyi alkalmazásokat és adatokból származó adatokból álló szolgáltatásokat. Emellett további felügyeleti lehetőségeket és adatvédelmet is biztosít, amikor a felhasználók személyes Android-eszközeiket használják a munkahelyen. 

## <a name="supported-devices"></a>Támogatott eszközök

Az Android Enterprise Management képességei az újabb Android operációs rendszerek részét képező funkciókra támaszkodnak. Az Android Enterprise-t nem támogató eszközök esetében a hagyományos androidos felügyelet továbbra is elérhető marad. További információt az [Android Enterprise-követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)című témakörben talál.

## <a name="onboarding"></a>Bevezetés

Az Android Enterprise Work Profile-eszközök regisztrálása előtt végre kell hajtania néhány bevezetési lépést. Ezek a lépések kapcsolatot létesít az Intune-bérlő és a felügyelt Google Play között. További információ: [az Android Enterprise Work profiling-eszközök regisztrálásának engedélyezése](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Munkahelyi profilok kezelése

Ha az Intune-nal felügyel egy androidos vállalati munkahelyi profilt, a teljes eszközt nem kezeli. A felügyeleti funkciók csak az eszközön a regisztráció során létrehozott munkahelyi profilra vonatkoznak. Minden olyan alkalmazás, amelyet az Intune-nal helyez üzembe az eszközön, a munkahelyi profilba települ. A munkahelyi profilban megjelenő alkalmazásikonok elkülönülnek az eszközön található személyes alkalmazásoktól. A vállalati Android hatókörén kívül eső összes Android-alkalmazás és adat személyes marad az eszközön, és a végfelhasználó felügyelete alá tartozik. Az eszköz személyes részén a felhasználók bármilyen alkalmazást telepíthetnek. A rendszergazdák a munkahelyi profil hatókörébe tartozó alkalmazásokat és műveleteket felügyelhetik és figyelhetik.

Az Intune az androidos munkahelyi profilos eszközökön konfigurálható, beépített általános beállítások széles választékát kínálja. További információt az [Androidos munkahelyi profilos eszközökre vonatkozó szabályzatbeállítások](../protect/compliance-policy-create-android-for-work.md) című témakörben talál.

## <a name="app-publishing-and-distribution"></a>Alkalmazások közzététele és terjesztése

A felügyelt Google Play az androidos Nagyvállalati alkalmazások terjesztésének és felügyeletének szerves részét képezi. A munkahelyi profilban az Android Enterprise munkahelyi profil eszközeire telepített alkalmazások a felügyelt Google Play szolgáltatásból származnak. A Play áruházban található alkalmazások felügyeletéhez és üzembe helyezéséhez a Google-felügyeletre kijelölt céges rendszergazdai hitelesítő adatokkal kell bejelentkezni a Google Play webhelyére. Az androidos vállalati telepítéshez tartozó alkalmazások jóváhagyását követően az eszközök munkahelyi profiljaiban is megjelenhetnek. Ezek az alkalmazások az Intune-konzolra szinkronizálódnak, ahol ezután telepíthetők és felügyelhetők az Intune-nal. A cége által fejlesztett üzletági (LOB) alkalmazásokat közzé kell tenni a Felügyelt Google Play szolgáltatásban a Google androidos alkalmazás-közzétételi konzoljával. Az üzletági alkalmazásokat az androidos alkalmazás-közzétételi konzolon kell konfigurálni a szervezethez való hozzáférés korlátozásához.

Az alkalmazások felhasználói beavatkozás nélkül telepíthetők, és az sem szükséges, hogy a felhasználó engedélyezze az **ismeretlen forrásból történő telepítést**. A választható vagy elérhető alkalmazások tallózásához és telepítéséhez a felhasználók a Play for Work áruházat használhatják az eszközükön. További információ: [alkalmazások kiosztása androidos vállalati munkahelyi Profilos eszközökhöz az Intune](../apps/apps-add-android-for-work.md)-nal.

## <a name="app-configuration"></a>Alkalmazáskonfiguráció

Az Android Enterprise infrastruktúrát biztosít az alkalmazások konfigurációs értékeinek üzembe helyezéséhez az azokat támogató alkalmazásokhoz. A munkahelyi alkalmazások konfigurációs értékeinek megadásával biztosíthatja, hogy az alkalmazások megfelelően legyenek beállítva, amikor a felhasználók először indítják el őket. Az alkalmazáskonfiguráció támogatásához az alkalmazásfejlesztőknek úgy kell létrehozniuk az Android-alkalmazásaikat, hogy azok támogassák a felügyelt konfigurációs értékek használatát. Ilyen esetben az Intune-nal adhatja meg és alkalmazhatja ezeket a konfigurációs beállításokat. További információt az [Alkalmazáskonfigurációs szabályzatok hozzáadása kezelt Android-eszközökhöz](../apps/app-configuration-policies-use-android.md) című témakörben talál.

## <a name="email-configuration"></a>E-mail-konfiguráció

Az Android Enterprise nem biztosít alapértelmezett e-mail alkalmazást vagy natív e-mail-profilt, például az iOS/iPadOS által megadott objektumot. Ehelyett e-mail-konfigurációk adhatók meg az alkalmazáskonfigurációs beállítások használatával az olyan levelezőalkalmazásokhoz, amelyek támogatják ezt. A Gmail és a Nine Work két Exchange ActiveSync (EAS) ügyfélalkalmazás a Play Áruházban, amelyek támogatják az Android Enterprise-alkalmazás konfigurációját.

Az Intune konfigurációsablonokat biztosít a Gmail és a Nine Work alkalmazáshoz, ha azok munkahelyi alkalmazásként vannak felügyelve. Az alkalmazáskonfigurációs profilokat támogató más levelezőalkalmazások mobilalkalmazás-konfigurációs szabályzatokkal konfigurálhatók.

Ha Exchange ActiveSync feltételes hozzáférést használ az Android Enterprise Work Profile eszközhöz, érdemes lehet a Gmail vagy a Nine Work e-mail alkalmazást használni. Szintén támogatott az Android rendszerhez készült Microsoft Outlook alkalmazás, illetve bármely olyan levelezőalkalmazás, amely modern ADAL-hitelesítést használ. További információt [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](../configuration/email-settings-configure.md) című témakörben talál.

## <a name="app-protection-policies"></a>Alkalmazásvédelmi szabályzatok

Az érvényben lévő alkalmazásvédelmi szabályzatokat a munkahelyi és a személyes profil egyaránt teljes mértékben támogatja. Az üzletági alkalmazásokat a https://play.google.com/apps/publish címen elérhető androidos alkalmazás-közzétételi konzolon teheti közzé. Ez a konzol tartalmaz egy beállítást, amellyel az alkalmazások privátként jelölhetők meg a szervezet számára. További információ: [eszköz megfelelőségi szabályzatának hozzáadása az Android Enterprise Work Profile-eszközökhöz az Intune-ban](../protect/compliance-policy-create-android-for-work.md). Az alkalmazásvédelmi szabályzatok létrehozásáról általános információ: [Mik azok az alkalmazásvédelmi szabályzatok?](../apps/app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN-profilok

A VPN-támogatás az Android VPN-profilokhoz hasonlít. Ugyanezek a VPN-szolgáltatók és alapszintű konfigurációs beállítások érhetők el az Android Enterprise Managementhez két különbséggel:

- **Munkahelyi profil hatókörű VPN** – A VPN-kapcsolatok a munkahelyi profilban üzembe helyezett alkalmazásokra vannak korlátozva. Csak az androidos betöltésének által felügyelt alkalmazások használhatják a VPN-kapcsolatokat. Az eszközön lévő saját alkalmazások nem használhatnak felügyelt VPN-kapcsolatot. További információt az [Android Enterprise VPN-beállítások](../configuration/vpn-settings-android-enterprise.md)című témakörben talál.

- **Alkalmazásspecifikus VPN** – Az alkalmazásspecifikus VPN akkor konfigurálható az Intune-ban, ha a VPN-szolgáltató támogatja:
  - alkalmazásspecifikus VPN konfigurációja
  - az alkalmazáson belüli VPN konfigurálásának lehetősége az Android Enterprise app Configuration profil használatával.
  További információt az [Alkalmazásonkénti VPN-profil létrehozása androidos eszközökhöz egyéni Microsoft Intune-profillal](../configuration/android-pulse-secure-per-app-vpn.md) című témakörben talál.

## <a name="certificate-profiles"></a>Tanúsítványprofilok

Az androidos felügyelethez elérhető, az Android vállalati munkahelyi profil eszközein elérhető konfigurációs beállítások is elérhetők. Az Android Enterprise továbbfejlesztett tanúsítványkezelő API-kat biztosít. A kibővített tanúsítványkezelés a következő funkciókat tartalmazza:

- Biztosítja, hogy a tanúsítványok telepítése csendes módban és a felhasználó számára zökkenőmentesen történjen.
- Biztosítja a telepített tanúsítványok eltávolítását, amikor az eszközöket kivonják az Intune-ból, és törlik a munkahelyi profilt.
- Továbbfejlesztett üzenetküldést biztosít, amely tájékoztatja a felhasználókat arról, hogy az informatikai részleg telepítette és konfigurálta a tanúsítványt a felügyeleti szolgáltatáson keresztül.

További információt az [Eszközök tanúsítványprofiljainak konfigurálása a Microsoft Intune-ban](../protect/certificates-configure.md) című témakörben talál.

## <a name="wi-fi-profiles"></a>Wi-Fi profilok

Az Android Enterprise által felügyelt Wi-Fi profilok törlődnek, ha az eszközt kivonják az Intune-ból, és törlik a munkahelyi profilt. További információt [A Wi-Fi-beállítások konfigurálása a Microsoft Intune-ban](../configuration/wi-fi-settings-configure.md) című témakörben talál.

## <a name="next-steps"></a>További lépések
- [Androidos eszközök regisztrálása](android-enroll.md)
- [Alkalmazások kiosztása androidos vállalati munkahelyi Profilos eszközökhöz az Intune-nal](../apps/apps-add-android-for-work.md)
