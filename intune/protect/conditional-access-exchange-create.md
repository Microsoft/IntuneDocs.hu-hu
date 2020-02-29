---
title: Exchange feltételes hozzáférési szabályzat létrehozása
titleSuffix: Microsoft Intune
description: Feltételes hozzáférés konfigurálása a helyszíni Exchange-hez és az örökölt dedikált Exchange Online-hoz az Intune-ban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6650c091917ea265783044efd78b19a7e032e6a7
ms.sourcegitcommit: 5511b4f2b8a3383176a7afe2a22ad5a8d42caf7b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169297"
---
# <a name="configure-exchange-on-premises-access-for-intune"></a>Helyszíni Exchange-hozzáférés konfigurálása az Intune-hoz

Ez a cikk bemutatja, hogyan konfigurálhatja a feltételes hozzáférést a helyszíni Exchange-hez az eszközök megfelelősége alapján.

Ha dedikált Exchange Online-környezettel rendelkezik, és szeretné tudni, hogy az új vagy az örökölt konfiguráció tartozik-e hozzá, lépjen kapcsolatba a fiókkezelővel. A helyszíni Exchange-hez vagy az örökölt dedikált Exchange Online-környezethez való e-mail-hozzáférés szabályozásához konfigurálja a feltételes hozzáférést a helyszíni Exchange-hez az Intune-ban.

## <a name="before-you-begin"></a>Előkészületek

A feltételes hozzáférés konfigurálása előtt ellenőrizze, hogy a következő konfigurációk léteznek-e:

- Exchange-verziója: **exchange 2010 SP1 vagy újabb**. Az Exchange-kiszolgáló ügyfél-hozzáférési kiszolgálótömbje (CAS) nem támogatott.

- Telepítette és használja az [Exchange ActiveSync helyszíni Exchange Connectort](exchange-connector-install.md), amely az Intune-t a helyszíni Exchange-hez köti.

    >[!IMPORTANT]  
    >Az Intune egy előfizetésben több helyszíni Exchange-összekötőt is támogat.  A helyszíni Exchange Connector azonban egyetlen Intune-bérlőre vonatkozik, és más Bérlővel nem használható.  Ha a cég egynél több helyszíni Exchange-összekötővel rendelkezik, minden Exchange-szervezet részére külön összekötőt építhet ki.

- A helyszíni Exchange-szervezet összekötője bármely gépen telepíthető, feltéve, hogy a gép kommunikálni tud az Exchange-kiszolgálóval.

- Ez az összekötő támogatja az **Exchange CAS-környezetet**. Az Intune támogatja az összekötők közvetlen telepítését az Exchange CAS-kiszolgálóra. Azt javasoljuk, hogy külön számítógépre telepítse azt, mert az összekötő további terhelést helyez el a kiszolgálón. Az összekötőt úgy kell konfigurálni, hogy az kommunikáljon az Exchange CAS-kiszolgálók valamelyikével.

- Az **Exchange ActiveSync** tanúsítványalapú hitelesítéssel vagy felhasználó által megadott hitelesítő adatokkal konfigurálandó.

- Ha a feltételes hozzáférési szabályzatok konfigurálva vannak és egy felhasználóhoz vannak rendelve, mielőtt egy felhasználó csatlakozni tud az e-mailhez, az általa használt **eszköznek** a következőnek kell lennie:
  - **Regisztrálva** van az Intune-ban, vagy olyan számítógép, amely csatlakoztatva van egy tartományhoz.
  - **Regisztrálva van az Azure Active Directoryban**. Ezenkívül az ügyfél Exchange ActiveSync-azonosítójának regisztrálva kell lennie az Azure Active Directoryban.

- Az Azure AD eszközregisztrációs szolgáltatása (DRS) automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azok az ügyfelek, akik már telepítették az ADFS-eszköz regisztrációs szolgáltatását, nem látják a regisztrált eszközöket a helyszíni Active Directoryban. **Ez nem érvényes a Windows rendszerű számítógépekre és a Windows Phone-eszközökre**.

- **Meg kell felelnie** az eszközre telepített összes megfelelőségi szabályzatnak.

- Ha az eszköz nem felel meg a feltételes hozzáférési beállításoknak, a felhasználó a következő üzenetek egyikével jelenik meg a bejelentkezéskor:
  - Ha az eszköz nincs regisztrálva az Intune-ban, vagy nincs regisztrálva a Azure Active Directoryban, egy üzenet jelenik meg, amely bemutatja, hogyan kell telepíteni a Céges portál alkalmazást, regisztrálni az eszközt és aktiválni az e-mailt. Ez a folyamat hozzárendeli az eszköz Exchange ActiveSync-azonosítóját is az Azure Active Directoryban lévő eszközrekordhoz.
  - Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely a felhasználót a Intune Céges portál webhelyére vagy a Céges portál alkalmazásra irányítja. A vállalati portálról információt talál a problémáról és annak megoldásáról.

### <a name="support-for-mobile-devices"></a>A mobileszközök támogatása

- **Windows Phone-telefon 8,1-es és újabb verziók** – feltételes hozzáférési szabályzat létrehozása: [feltételes hozzáférési házirendek létrehozása](../protect/create-conditional-access-intune.md)
- **Natív e-mail alkalmazás iOS/iPadOS** – feltételes hozzáférési szabályzat létrehozása: [feltételes hozzáférési házirendek létrehozása](../protect/create-conditional-access-intune.md)
- **EAS levelezési ügyfélprogramok, mint például a Gmail az Android 4-es vagy újabb verzióiban** – feltételes hozzáférési szabályzat létrehozásával kapcsolatban lásd a [feltételes hozzáférési házirendek létrehozása](../protect/create-conditional-access-intune.md) című témakört.

- **EAS levelezési ügyfélprogramok androidos munkahelyi Profilos eszközökön** – az androidos munkahelyi profil eszközein csak a *Gmail* és *a Nine work for Android Enterprise* támogatott. Az androidos munkahelyi profilokkal végzett feltételes hozzáféréshez telepítenie kell egy e-mail-profilt a *Gmail* vagy a *Nine work for Android Enterprise* alkalmazáshoz, és ezeket az alkalmazásokat kötelező telepítésként is telepítenie kell. Az alkalmazás üzembe helyezését követően beállíthatja az eszközön alapuló feltételes hozzáférést.

#### <a name="to-set-up-conditional-access-for-android-work-profile-devices"></a>Feltételes hozzáférés beállítása androidos munkahelyi profilú eszközökhöz

  1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. **Szükség**szerint telepítse a Gmail vagy a Nine Work alkalmazást.

  3. Válassza az **eszközök** > **konfigurációs profilok** > **profil létrehozása**lehetőséget, adja meg a profil **nevét** és **leírását** .

  4. Válassza az **Android Enterprise** lehetőséget a **platformon**, majd válassza az **e-mail** lehetőséget a **Profil típusa**mezőben.

  5. Adja meg az [e-mail profil beállításait](https://docs.microsoft.com/intune/configuration/email-settings-android-enterprise#android-enterprise).

  6. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

  7. Az e-mail profil létrehozása után [rendelje hozzá a csoportokhoz](https://docs.microsoft.com/intune/device-profile-assign).

  8. Az [eszközön alapuló feltételes hozzáférés](https://docs.microsoft.com/intune/protect/conditional-access-intune-common-ways-use#device-based-conditional-access)beállítása.

> [!NOTE]
> A Microsoft Outlook for Android és az iOS/iPadOS nem támogatott a helyszíni Exchange-összekötőn keresztül. Ha szeretné kihasználni Azure Active Directory feltételes hozzáférési szabályzatokat, és Intune App Protection szabályzatokat az iOS/iPadOS és az Android rendszerhez a helyszíni postaládákhoz, tekintse meg a [hibrid modern hitelesítés használata az Outlookban iOS/iPadOS és Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)rendszerhez című témakört.

### <a name="support-for-pcs"></a>Számítógépek támogatása

A natív **posta** alkalmazás a Windows 8,1-es és újabb verzióiban (ha a Mdm-be az Intune-nal regisztrálták)

## <a name="configure-exchange-on-premises-access"></a>A helyszíni Exchange-hozzáférés konfigurálása

Mielőtt az alábbi eljárást használja a helyszíni Exchange-hozzáférés beállításához, telepítenie és konfigurálnia kell legalább egy Intune helyszíni Exchange [Connectort](exchange-connector-install.md) a helyszíni Exchange-hez.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Lépjen a **bérlői felügyelet** > **Exchange-hozzáférés**elemre, majd válassza **a helyszíni Exchange-hozzáférés**lehetőséget.

3. A helyszíni Exchange- **hozzáférés** panel **Igen** elemét választva engedélyezheti a helyszíni *Exchange-hozzáférés-vezérlést*.

   > [!div class="mx-imgBorder"]
   > ![példa a helyszíni Exchange-hozzáférés képernyőre](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. A **hozzárendelés**területen válassza **a csoportok kiválasztása a belefoglaláshoz**lehetőséget, majd válasszon ki egy vagy több csoportot a hozzáférés konfigurálásához.

   A kiválasztott csoportok tagjai a feltételes hozzáférési szabályzattal rendelkeznek a helyszíni Exchange-hozzáféréshez. A szabályzatot fogadó felhasználóknak regisztrálniuk kell az eszközeiket az Intune-ban, és meg kell felelniük a megfelelőségi profiloknak ahhoz, hogy hozzáférhessenek a helyszíni Exchange-hez.

   > [!div class="mx-imgBorder"]
   > ![válassza ki a csoportokat](./media/conditional-access-exchange-create/select-groups.png)

5. A csoportok kizárásához válassza a **kizárni kívánt csoportok kiválasztása**lehetőséget, majd válasszon ki egy vagy több olyan csoportot, amely mentesül az eszközök regisztrálására és a megfelelőségi profiloknak való megfelelésre a helyszíni Exchange elérése előtt.

   Válassza a **Mentés** lehetőséget a konfiguráció mentéséhez, és térjen vissza az **Exchange-hozzáférés** ablaktáblára.

6. Ezután konfigurálja a helyszíni Intune Exchange Connector beállításait. A konzolon válassza a **bérlői felügyelet** > **exchange-hozzáférés**> **Exchange ActiveSync helyszíni összekötő** lehetőséget, majd válassza ki a konfigurálni kívánt Exchange-szervezet összekötőjét.

7. **Felhasználói értesítések**esetén válassza a **Szerkesztés** lehetőséget a **szervezet szerkesztése** munkafolyamat megnyitásához, ahol módosíthatja a *felhasználói értesítési* üzenetet.

   > [!div class="mx-imgBorder"]
   > ![például képernyőkép a szervezeti munkafolyamat szerkesztése az értesítésekhez](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   Módosítsa a felhasználóknak küldött alapértelmezett e-mail-üzenetet, ha az eszköz nem megfelelő, és szeretné elérni a helyszíni Exchange-t. Az üzenetsablon egy jelölőnyelvet használ. Azt is megtekintheti, hogy az üzenet hogyan néz ki a beírt módon

   Válassza a **felülvizsgálat + mentés**lehetőséget, majd **mentse** a módosításokat a helyszíni Exchange-hozzáférés konfigurálásának befejezéséhez.

   > [!TIP]
   > A jelölőnyelvekről ez a [Wikipedia-cikk](https://en.wikipedia.org/wiki/Markup_language) nyújt tájékoztatást.

8. Ezután válassza a **speciális Exchange ActiveSync hozzáférési beállítások** elemet a *speciális Exchange ActiveSync hozzáférési beállítások* munkafolyamatának megnyitásához, ahol az eszköz-hozzáférési szabályokat konfigurálja.

   > [!div class="mx-imgBorder"]
   > ![a speciális beállításokhoz tartozó szervezeti munkafolyamat szerkesztése című képernyőképet](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - A nem **felügyelt eszközök hozzáféréséhez**állítsa be a globális alapértelmezett szabályt a hozzáféréshez a feltételes hozzáférés vagy más szabályok által nem érintett eszközökről:

     - **Hozzáférés engedélyezése** – az összes eszköz azonnal hozzáférhet a helyszíni Exchange-hez. Azok az eszközök, amelyek az előző eljárásban megadott csoportokba tartozó felhasználókhoz tartoznak, le vannak tiltva, ha később kiértékelik azokat, amelyek nem felelnek meg a megfelelő szabályzatoknak, vagy nincsenek regisztrálva az Intune-ban.

     - **Hozzáférés letiltása** és **karanténba helyezése** – az összes eszköz azonnal le lesz tiltva a helyszíni Exchange-hez való hozzáféréshez. Azok az eszközök, amelyek az előző eljárás részeként konfigurált csoportokban lévő felhasználókhoz tartoznak, hozzáférhetnek az Intune-ban az eszköz regisztrálása után, és megfelelőnek értékelik azokat.

       A Samsung Knox standard-t *nem* futtató Android-eszközök nem támogatják ezt a beállítást, és mindig le vannak tiltva.

   - Az **eszközök platformjának kivételei**esetében válassza a **Hozzáadás**lehetőséget, majd adja meg a környezetéhez szükséges adatokat.

      Ha a nem **felügyelt eszköz hozzáférésének** beállítása **blokkolva**értékre van állítva, a regisztrált és megfelelő eszközök akkor is engedélyezettek, ha a platform kivételt okoz.  

9. A módosítások mentéséhez kattintson **az OK gombra** .

10. Válassza a **felülvizsgálat + mentés**lehetőséget, **majd mentse az Exchange** feltételes hozzáférési szabályzatát.

## <a name="next-steps"></a>További lépések

Ezután hozzon létre egy megfelelőségi szabályzatot, és rendelje hozzá a felhasználókhoz az Intune-nal a mobileszközök kiértékeléséhez lásd: [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md).

[A helyszíni Intune Exchange Connector hibaelhárítása Microsoft Intune](https://support.microsoft.com/help/4471887)
