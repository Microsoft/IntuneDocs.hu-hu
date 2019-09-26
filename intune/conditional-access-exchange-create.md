---
title: Exchange feltételes hozzáférési szabályzat létrehozása
titleSuffix: Microsoft Intune
description: Feltételes hozzáférés konfigurálása a helyszíni Exchange-hez és az örökölt dedikált Exchange Online-hoz az Intune-ban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: stama
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b53f3dc338f543468984df362b22f6b88ee5c53
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304061"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Feltételes hozzáférési szabályzat létrehozása a helyszíni Exchange-hez és az örökölt dedikált Exchange Online-hoz

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk bemutatja, hogyan konfigurálhatja a feltételes hozzáférést a helyszíni Exchange-hez az eszközök megfelelősége alapján.

Ha dedikált Exchange Online-környezettel rendelkezik, és szeretné tudni, hogy az új vagy az örökölt konfiguráció tartozik-e hozzá, lépjen kapcsolatba a fiókkezelővel. A helyszíni Exchange-hez vagy az örökölt dedikált Exchange Online-környezethez való e-mail-hozzáférés szabályozásához konfigurálja a feltételes hozzáférést a helyszíni Exchange-hez az Intune-ban.

## <a name="before-you-begin"></a>Előkészületek

A feltételes hozzáférés konfigurálása előtt ellenőrizze, hogy a következő konfigurációk léteznek-e:

- Exchange-verziója: **exchange 2010 SP1 vagy újabb**. Az Exchange-kiszolgáló ügyfél-hozzáférési kiszolgálótömbje (CAS) nem támogatott.

- Telepítette és használja a [Exchange Active Sync helyszíni Exchange Connectort](exchange-connector-install.md), amely összeköti az Intune-t a helyszíni Exchange-hez.

    >[!IMPORTANT]  
    >Az Intune egy előfizetésben több helyszíni Exchange-összekötőt is támogat.  A helyszíni Exchange Connector azonban egyetlen Intune-bérlőre vonatkozik, és más Bérlővel nem használható.  Ha a cége egynél több helyszíni Exchange-összekötővel rendelkezik, minden Exchange-szervezet részére külön összekötőt építhet ki.

- A helyszíni Exchange-szervezet összekötője bármely gépen telepíthető, feltéve, hogy a gép kommunikálni tud az Exchange-kiszolgálóval.

- Ez az összekötő támogatja az **Exchange CAS-környezetet**. Az Intune lehetővé teszi, hogy közvetlenül az Exchange CAS-kiszolgálóra telepítse az összekötőt, de javasoljuk, hogy az összekötő további betöltése miatt telepítse azt egy külön számítógépre. Az összekötőt úgy kell konfigurálni, hogy az kommunikáljon az Exchange CAS-kiszolgálók valamelyikével.

- Az **Exchange ActiveSync** tanúsítványalapú hitelesítéssel vagy felhasználó által megadott hitelesítő adatokkal konfigurálandó.

- Ha a feltételes hozzáférési szabályzatok konfigurálva vannak és egy felhasználóhoz vannak rendelve, mielőtt egy felhasználó csatlakozni tud az e-mailhez, az általa használt **eszköznek** a következőnek kell lennie:
  - **Regisztrálva** van az Intune-ban, vagy olyan számítógép, amely csatlakoztatva van egy tartományhoz.
  - **Regisztrálva van az Azure Active Directoryban**. Ezenkívül az ügyfél Exchange ActiveSync-azonosítójának regisztrálva kell lennie az Azure Active Directoryban.

- Az Azure AD eszközregisztrációs szolgáltatása (DRS) automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azok az ügyfelek, akik már telepítették az ADFS-eszköz regisztrációs szolgáltatását, nem látják a regisztrált eszközöket a helyszíni Active Directoryban. **Ez nem érvényes a Windows rendszerű számítógépekre és a Windows Phone-eszközökre**.

- **Meg kell felelnie** az eszközre telepített összes megfelelőségi szabályzatnak.

- Ha az eszköz nem felel meg a feltételes hozzáférési beállításoknak, a felhasználó a következő üzenetek egyikével jelenik meg a bejelentkezéskor:
  - Ha az eszköz nincs regisztrálva az Intune-ban, vagy nincs regisztrálva a Azure Active Directoryban, egy üzenet jelenik meg, amely bemutatja, hogyan kell telepíteni a Céges portál alkalmazást, regisztrálni az eszközt és aktiválni az e-mailt. Ez a folyamat hozzárendeli az eszköz Exchange ActiveSync-azonosítóját is az Azure Active Directoryban lévő eszközrekordhoz.
  - Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely a felhasználót a Intune Céges portál webhelyre vagy a Céges portál alkalmazásba irányítja, ahol információt talál a problémáról és annak megoldásáról.

### <a name="support-for-mobile-devices"></a>A mobileszközök támogatása

- Windows Phone 8.1 és újabb verziók
- Natív e-mail alkalmazás iOS rendszerű eszközökön.
- EAS levelezési ügyfélprogramok, mint például a Gmail az Android 4-es vagy újabb verzióiban.
- EAS levelezési ügyfélprogramok **androidos munkahelyi profil eszközei:** A **munkahelyi profilban** csak a **Gmail** és a **Nine work for Android Enterprise** használható androidos munkahelyi Profilos eszközökön. Az androidos munkahelyi profilokkal végzett feltételes hozzáféréshez telepítenie kell egy e-mail-profilt a Gmail vagy a Nine work for Android Enterprise alkalmazáshoz, és ezeket az alkalmazásokat kötelező telepítésként is telepítenie kell.

> [!NOTE]
> Az Android és az iOS rendszerhez készült Microsoft Outlook nem támogatott a helyszíni Exchange-összekötőn keresztül. Ha szeretné kihasználni Azure Active Directory feltételes hozzáférési szabályzatokat, és Intune App Protection szabályzatokat az iOS-hez és az Androidhoz készült Outlook használatával a helyszíni postaládákhoz, tekintse meg a [hibrid modern hitelesítés használata az Outlookban iOS és Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) rendszerhez című témakört. . 

### <a name="support-for-pcs"></a>Számítógépek támogatása

A natív **posta** alkalmazás a Windows 8,1-es és újabb verzióiban (ha a Mdm-be az Intune-nal regisztrálták)

## <a name="configure-exchange-on-premises-access"></a>A helyszíni Exchange-hozzáférés konfigurálása

Mielőtt az alábbi eljárást használja a helyszíni Exchange-hozzáférés beállításához, telepítenie és konfigurálnia kell legalább egy Intune helyszíni Exchange [Connectort](exchange-connector-install.md) a helyszíni Exchange-hez.

1. Bejelentkezés az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba

2. Lépjen az **Exchange-hozzáférés**elemre, majd válassza **a helyszíni Exchange-hozzáférés**lehetőséget. 

3. A helyszíni Exchange- **hozzáférés** panel **Igen** elemét választva engedélyezheti a helyszíni *Exchange-hozzáférés-vezérlést*.

4. A **hozzárendelés**területen válassza **a csoportok kiválasztása a belefoglaláshoz**lehetőséget, majd válasszon ki egy vagy több csoportot a hozzáférés konfigurálásához. 

   A kiválasztott csoportok tagjai a feltételes hozzáférési szabályzattal rendelkeznek a helyszíni Exchange-hozzáféréshez. A szabályzatot fogadó felhasználóknak regisztrálniuk kell az eszközeiket az Intune-ban, és meg kell felelniük a megfelelőségi profiloknak ahhoz, hogy hozzáférhessenek a helyszíni Exchange-hez.

5. A csoportok kizárásához válassza a **kizárni kívánt csoportok kiválasztása**lehetőséget, majd válasszon ki egy vagy több olyan csoportot, amely mentesül az eszközök regisztrálására vonatkozó követelmények alól, és a helyszíni Exchange-hez való hozzáférés előtt meg kell felelnie a megfelelőségi profiloknak. 

6. Ezután konfigurálja a helyszíni Intune Exchange Connector beállításait.  Az **Exchange-hozzáférés ablaktáblán**válassza az **Exchange ActiveSync helyszíni összekötő** lehetőséget, majd válassza ki a konfigurálni kívánt Exchange-szervezet összekötőjét.

7. A **Beállítások**területen válassza a **felhasználói értesítések** lehetőséget a felhasználóknak küldött alapértelmezett e-mail-üzenet módosításához, ha az eszköz nem megfelelő, és szeretné elérni a helyszíni Exchange-t. Az üzenetsablon egy jelölőnyelvet használ.  Amint beírja az üzenetet, azt is követheti, hogy mit fog látni a címzett.
   > [!TIP]
   > A jelölőnyelvekről ez a [Wikipedia-cikk](https://en.wikipedia.org/wiki/Markup_language) nyújt tájékoztatást.
 
   A módosítások mentéséhez kattintson **az OK gombra** , hogy elvégezze a helyszíni Exchange-hozzáférés konfigurálását.

8. Ezután válassza a **speciális Exchange Active Sync hozzáférési beállítások** elemet a *speciális Exchange ActiveSync hozzáférési beállítások* panel megnyitásához, ahol az eszköz-hozzáférési szabályokat konfigurálhatja:  

   - A nem **felügyelt eszközök hozzáféréséhez**állítsa be a globális alapértelmezett szabályt a hozzáféréshez a feltételes hozzáférés vagy más szabályok által nem érintett eszközökről:

     - **Hozzáférés engedélyezése** – az összes eszköz azonnal hozzáférhet a helyszíni Exchange-hez. Azok az eszközök, amelyek az előző eljárásban megadott csoportokba tartozó felhasználókhoz tartoznak, le vannak tiltva, ha később kiértékelik azokat, amelyek nem felelnek meg a megfelelő szabályzatoknak, vagy nincsenek regisztrálva az Intune-ban.

     - **Hozzáférés letiltása** és **karanténba helyezése** – az összes eszköz azonnal le lesz tiltva a helyszíni Exchange-hez való hozzáféréshez. Azok az eszközök, amelyek az előző eljárás részeként konfigurált csoportokban lévő felhasználókhoz tartoznak, hozzáférhetnek az Intune-ban az eszköz regisztrálása után, és megfelelőnek értékelik azokat. 

       A Samsung Knox standard-t *nem* futtató Android-eszközök nem támogatják ezt a beállítást, és mindig le vannak tiltva.

   -  Az **eszközök platformjának kivételei**esetében válassza a **Hozzáadás**lehetőséget, majd adja meg a környezethez szükséges platform részleteit. 
   
      Ha a nem **felügyelt eszköz hozzáférésének** beállítása **blokkolva**értékre van állítva, a regisztrált és megfelelő eszközök akkor is engedélyezettek, ha a platform kivételt okoz.  
   
   A módosítások mentéséhez kattintson **az OK gombra** .

9. Válassza a **Mentés** lehetőséget az Exchange feltételes hozzáférési szabályzatának mentéséhez.

Ezután hozzon létre egy megfelelőségi szabályzatot, és rendelje hozzá a felhasználókhoz az Intune-nal a mobileszközök kiértékeléséhez lásd: [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md).

## <a name="see-also"></a>Lásd még:

[A helyszíni Intune Exchange Connector hibaelhárítása Microsoft Intune](https://support.microsoft.com/help/4471887)
