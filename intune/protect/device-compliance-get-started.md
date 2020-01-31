---
title: Eszközmegfelelőségi szabályzatok az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: 'Első lépések: eszközök megfelelőségi házirendjeinek használata, az állapot és a súlyossági szintek áttekintése, a türelmi időszakban állapot, a feltételes hozzáférés használata és a hozzárendelt házirend nélküli eszközök kezelése.'
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a56d8f7aface3628ba5bc8985128ebb49c9cf404
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812166"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Szabályok beállítása az eszközökön a szervezet erőforrásaihoz való hozzáférés engedélyezéséhez az Intune használatával

Számos mobileszköz-kezelési (MDM) megoldás segíti a szervezeti adatvédelmet azáltal, hogy a felhasználóknak és az eszközöknek bizonyos követelmények teljesítését igénylik. Az Intune-ban ezt a funkciót "megfelelőségi szabályzatoknak" nevezzük. A megfelelőségi szabályzatok határozzák meg azokat a szabályokat és beállításokat, amelyeknek a felhasználóknak és az eszközöknek meg kell felelniük a követelményeknek. A feltételes hozzáféréssel együtt a rendszergazdák letilthatják azokat a felhasználókat és eszközöket, amelyek nem felelnek meg a szabályoknak.

Az Intune-rendszergazdák például a következőket tehetik meg:

- A végfelhasználók jelszó használatával érik el a mobileszközök szervezeti információit
- Az eszköz nem sérült vagy feltört
- Az eszközön az operációs rendszer minimális vagy maximális verziója
- Az eszköz, amelynek a helye, vagy fenyegetési szinten kell lennie

Ezt a funkciót használhatja a szervezet eszközeinek megfelelőségi állapotának figyelésére is.

> [!IMPORTANT]
> Az Intune az eszköz összes megfelelőségi értékeléséhez az eszköz beadási ütemtervét követi. A [házirend-és profil-frissítési ciklusok](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) a becsült frissítési időpontokat listázza.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Az eszközök megfelelőségi szabályzatai működnek az Azure AD-vel

Az Intune Azure Active Directory (AD) [feltételes hozzáférést](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) használ (megnyílik egy másik docs webhelye) a megfelelőség kikényszerítés érdekében. Ha egy eszköz regisztrálva van az Intune-ban, elindul az Azure AD regisztrációs folyamata, és az eszköz adatai frissülnek az Azure AD-ben. Az egyik legfontosabb információ az eszköz megfelelőségi állapota. Ezt a megfelelőségi állapotot a feltételes hozzáférési szabályzatok használják az e-mailekhez és más szervezeti erőforrásokhoz való hozzáférés blokkolására vagy engedélyezésére.

- [Mi az Eszközkezelés a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/device-management-introduction) , hogy miért és hogyan történik az eszközök regisztrálása az Azure ad-ben.

- A [feltételes hozzáférés és a](conditional-access.md) [feltételes hozzáférés használatának gyakori módjai](conditional-access-intune-common-ways-use.md) ezt a funkciót írják le, mivel az Intune-nal kapcsolatosak.

## <a name="ways-to-use-device-compliance-policies"></a>Eszközmegfelelőségi szabályzatok használatának módjai

### <a name="with-conditional-access"></a>Feltételes hozzáféréssel

A házirend-szabályoknak megfelelő eszközökhöz hozzáférést biztosíthat a levelezéshez és más szervezeti erőforrásokhoz. Ha az eszközök nem felelnek meg a szabályzati szabályoknak, akkor nem kapnak hozzáférést a szervezeti erőforrásokhoz. Ez a feltételes hozzáférés.

### <a name="without-conditional-access"></a>Feltételes hozzáférés nélkül

Az eszköz megfelelőségi szabályzatait feltételes hozzáférés nélkül is használhatja. A megfelelőségi szabályzatok önálló használata esetén a megcélzott eszközöket megfelelőségi állapotuk szerint értékeli ki és jelenti a rendszer. Lekérhet például egy jelentést arról, hogy hány eszköz titkosítása nem történik meg, vagy hogy mely eszközök legyenek a börtöntől töröttek vagy feltörtek. Ha a megfelelőségi szabályzatokat feltételes hozzáférés nélkül használja, a szervezeti erőforrásokhoz nincs hozzáférés-korlátozás.

## <a name="ways-to-deploy-device-compliance-policies"></a>Az eszközmegfelelőségi szabályzatok üzembe helyezésének módjai

Az eszközmegfelelőségi szabályzatokat felhasználói csoportokban lévő felhasználók, illetve eszközcsoportokban lévő eszközök számára helyezheti üzembe. Amikor felhasználók számára telepít megfelelőségi szabályzatot, a rendszer az összes felhasználói eszköz megfelelőségét ellenőrzi. A Windows 10 1803-as vagy újabb verziójával rendelkező eszközökön javasolt az eszközcsoportokba történő üzembe helyezés, *ha* az elsődleges felhasználó nem regisztrálta az eszközt. Ebben a forgatókönyvben az eszközcsoportok használata segít a megfelelőségi jelentések elkészítésében.

Az Intune a beépített megfelelőségi szabályzatok egy készletét is tartalmazza. A következő beépített szabályzatok az Intune-ban regisztrált összes eszközön kiértékelésre kerülnek:

- **Hozzárendelt megfelelőségi szabályzattal nem rendelkező eszköz megjelölése mint**: Ehhez a tulajdonsághoz két érték tartozik:

  - **Megfelelő** (*alapértelmezett*): biztonsági szolgáltatás kikapcsolva
  - **Nem megfelelő**: biztonsági szolgáltatás bekapcsolva

  Ha egy eszközhöz nincs hozzárendelve megfelelőségi szabályzat, az eszköz alapértelmezés szerint megfelelőnek minősül. Ha a feltételes hozzáférést megfelelőségi szabályzatokkal használja, javasoljuk, hogy az alapértelmezett beállítást **ne megfelelőre**módosítsa. Ha egy végfelhasználó nem felel meg a szabályzatnak, a [céges portál alkalmazás](../apps/company-portal-app.md) a `No compliance policies have been assigned`t jeleníti meg.


> [!NOTE]
> Az iOS-eszközök továbbfejlesztett jailbreak-észlelése átmenetileg le lett tiltva az Intune-ban.

- **Továbbfejlesztett jailbreak-észlelés**: Ha engedélyezve van, ez a beállítás az iOS-eszközök gyakrabban való bejelentkezését okozza az Intune-ban. A tulajdonság engedélyezésekor a rendszer igénybe veszi az eszköz helyalapú szolgáltatásait, mely hatással van az akkumulátorhasználatra. Az Intune nem tárolja a felhasználói hely adatterületét.

  Ennek a beállításnak az engedélyezésekor az eszközöknek meg kell felelnie a következőknek:
  - Engedélyezze a Location Services szolgáltatást az operációs rendszer szintjén.
  - A helymeghatározási szolgáltatások használatának engedélyezése a vállalati portál számára.
  - Jailbreakelés állapotának kiértékelése és jelentése az Intune-nak legalább 72 óránként. Máskülönben az eszköz „nem megfelelő” állapotúként lesz megjelölve. A kiértékelés a Céges portál alkalmazás megnyitásával vagy az eszköz 500 méteres vagy újabb fizikai mozgatásával aktiválódik. Ha az eszköz 72 órán belül nem helyezi át a 500 métert, a felhasználónak meg kell nyitnia a Céges portál alkalmazást a kibővített Jail Break kiértékeléséhez.

- **Megfelelőségi állapot érvényességi időtartama (nap)** : Adja meg azt az időszakot, amelyben az eszközöknek jelenteniük kell az állapotukat minden fogadott megfelelőségi szabályzat vonatkozásában. A rendszer nem megfelelőként kezeli azokat az eszközöket, melyek ebben az időszakban nem adják vissza állapotukat. Az alapértelmezett érték 30 nap.

Ezeket a beállításokat a beépített szabályzatok segítségével figyelheti. Az Intune az eszköz platformtól függően különböző időközönként [frissíti vagy ellenőrzi a frissítéseket](create-compliance-policy.md#refresh-cycle-times) . A [Microsoft Intune eszköz-szabályzatokkal és-profilokkal kapcsolatos gyakori kérdések, problémák és megoldások](../configuration/device-profile-troubleshoot.md) jó erőforrás.

A megfelelőségi jelentések praktikus módot nyújtanak az eszközök állapotának ellenőrzésére. A [megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md) némi útmutatást tartalmaz.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Nem megfelelőség és feltételes hozzáférés a különböző platformokon

A következő táblázat ismerteti, hogyan történik a nem megfelelő beállítások kezelése, ha a megfelelőségi szabályzatot feltételes hozzáférési szabályzattal együtt használják.

---------------------------

|**Szabályzat-beállítás**| **Platform** |
| --- | ----|
| **PIN-kód vagy jelszó konfigurálása** | - **Android 4,0 és újabb verziók**: karanténba helyezve<br>- **Samsung Knox Standard 4,0 és újabb verziók**: karanténba helyezve<br>- **Android Enterprise**: karanténba helyezve  <br>  <br>- **iOS 8,0 és újabb verziók**: szervizelt<br>- **macOS 10,11 és újabb verziók**: szervizelt  <br>  <br>- **Windows 8,1 és újabb verziók**: szervizelt<br>- **Windows Phone-telefon 8,1 és újabb verziók**: szervizelt|
| **Eszköztitkosítás** | - **Android 4,0 és újabb verziók**: karanténba helyezve<br>- **Samsung Knox Standard 4,0 és újabb verziók**: karanténba helyezve<br>- **Android Enterprise**: karanténba helyezve<br><br>- **iOS 8,0 és újabb verziók**: szervizelés (PIN-kód beállításával)<br>- **macOS 10,11 és újabb verziók**: szervizelés (PIN-kód beállításával)<br><br>- **Windows 8,1 és újabb verziók**: nem alkalmazható<br>- **Windows Phone-telefon 8,1 és újabb verziók**: szervizelt |
| **Jailbreakelt vagy rootolt eszköz** | - **Android 4,0 és újabb verziók**: karanténba helyezve (nem beállítás)<br>- **Samsung Knox Standard 4,0 és újabb verziók**: karanténba helyezve (nem beállítás)<br>- **Android Enterprise**: karanténba helyezve (nem beállítás)<br><br>- **iOS 8,0 és újabb verziók**: karanténba helyezve (nem beállítás)<br>- **macOS 10,11 és újabb verziók**: nem alkalmazható<br><br>- **Windows 8,1 és újabb verziók**: nem alkalmazható<br>- **Windows Phone-telefon 8,1 és újabb verziók**: nem alkalmazható |
| **E-mail profil** | - **Android 4,0 és újabb verziók**: nem alkalmazható<br>- **Samsung Knox Standard 4,0 és újabb verziók**: nem alkalmazható<br>- **Android Enterprise**: nem alkalmazható<br><br>- **iOS 8,0 és újabb verziók**: karanténba helyezve<br>- **macOS 10,11 és újabb verziók**: karanténba helyezve<br><br>- **Windows 8,1 és újabb verziók**: nem alkalmazható<br>- **Windows Phone-telefon 8,1 és újabb verziók**: nem alkalmazható |
| **Operációs rendszer minimális verziója** | - **Android 4,0 és újabb verziók**: karanténba helyezve<br>- **Samsung Knox Standard 4,0 és újabb verziók**: karanténba helyezve<br>- **Android Enterprise**: karanténba helyezve<br><br>- **iOS 8,0 és újabb verziók**: karanténba helyezve<br>- **macOS 10,11 és újabb verziók**: karanténba helyezve<br><br>- **Windows 8,1 és újabb verziók**: karanténba helyezve<br>- **Windows Phone-telefon 8,1 és újabb verziók**: karanténba helyezve |
| **Operációs rendszer maximális verziója** | - **Android 4,0 és újabb verziók**: karanténba helyezve<br>- **Samsung Knox Standard 4,0 és újabb verziók**: karanténba helyezve<br>- **Android Enterprise**: karanténba helyezve<br><br>- **iOS 8,0 és újabb verziók**: karanténba helyezve<br>- **macOS 10,11 és újabb verziók**: karanténba helyezve<br><br>- **Windows 8,1 és újabb verziók**: karanténba helyezve<br>- **Windows Phone-telefon 8,1 és újabb verziók**: karanténba helyezve |
| **Windows-állapotigazolás** | - **Android 4,0 és újabb verziók**: nem alkalmazható<br>- **Samsung Knox Standard 4,0 és újabb verziók**: nem alkalmazható<br>- **Android Enterprise**: nem alkalmazható<br><br>- **iOS 8,0 és újabb verziók**: nem alkalmazható<br>- **macOS 10,11 és újabb verziók**: nem alkalmazható<br><br>- **Windows 10 és Windows 10 Mobile**: karanténba helyezve<br>- **Windows 8,1 és újabb verziók**: karanténba helyezve<br>- **Windows Phone-telefon 8,1 és újabb verziók**: nem alkalmazható |

---------------------------

**Szervizelés**: az eszköz operációs rendszere kikényszeríti a megfelelőséget. Például a felhasználó köteles lesz PIN-kódot beállítani.

**Karanténba helyezve**: az eszköz operációs rendszere nem kényszeríti ki a megfelelőséget. Az Android és az Android rendszerű vállalati eszközök például nem kényszerítik a felhasználót az eszköz titkosítására. Ha az eszköz nem megfelelő, a következő műveletekre kerül sor:

- Ha a felhasználóra vonatkozó feltételes hozzáférési szabályzat érvényes, az eszköz le lesz tiltva.
- A Céges portál alkalmazás értesíti a felhasználót a megfelelőségi problémákról.

## <a name="next-steps"></a>További lépések

- [Hozzon létre egy szabályzatot](create-compliance-policy.md) , és tekintse meg az előfeltételeket.
- Tekintse meg a különböző eszközök platformjának megfelelőségi beállításait:

  - [Android--](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS--](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 és újabb](compliance-policy-create-windows-8-1.md)
  - [Windows 10 és újabb](compliance-policy-create-windows.md)

- A [házirend entitásokra](../reports-ref-policy.md) vonatkozó információk az Intune-adattárház házirend entitásait ismertetik.
