---
title: Az iOS-alkalmazások közötti adatátvitel kezelése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan használhatja a Microsoft Intune mobilalkalmazás-kezelési házirendjeit az alkalmazások közötti adatátvitel kezeléséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db583b1fc89edf72f329a605cc86363593eaaa9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497912"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban

A vállalati adatai védelme érdekében korlátozza a fájlátvitelt csak a felügyelt alkalmazásokra. Az iOS-alkalmazásokat az alábbi módokon felügyelheti:

- Munkahelyi vagy iskolai fiókok szervezeti adatainak védelme az alkalmazások alkalmazás-védelmi szabályzatának konfigurálásával. a szabályzat által *felügyelt alkalmazásokat*hívjuk.  [Az Intune által kezelt alkalmazásvédelmi szabályzattal védhető alkalmazások listája](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Az alkalmazásokat az iOS-eszközök felügyeletén keresztül telepítheti és kezelheti, ehhez pedig egy mobileszköz-kezelési (MDM) megoldásban kell regisztrálnia az eszközöket. Az üzembe helyezett alkalmazások házirend által *felügyelt alkalmazások* vagy más, iOS által felügyelt alkalmazások lehetnek.

A regisztrált iOS-eszközök **megnyitási felügyeleti** funkciója korlátozhatja az iOS által felügyelt alkalmazások közötti fájlátvitelt. Állítsa be a *megnyitási felügyeleti* korlátozásokat a konfigurációs beállításokban, majd telepítse őket a Mdm-megoldás használatával.  Amikor egy felhasználó telepíti az üzembe helyezett alkalmazást, a rendszer alkalmazza a megadott korlátozásokat.

## <a name="use-app-protection-with-ios-apps"></a>Az App Protection használata iOS-alkalmazásokkal
Az iOS- **es Open-in Management** szolgáltatással az alábbi módokon biztosíthatja a vállalati adatainak védelmét az alkalmazás-védelmi házirendek használatával:

- **Egyetlen Mdm-megoldás által nem kezelt eszközök:** Az alkalmazás védelmi házirendjének beállításait beállíthatja úgy, hogy az adatmegosztást más alkalmazásokkal is megtekintse *megnyitási* vagy *megosztási bővítmények*használatával.  Ehhez konfigurálja a **szervezeti adatküldés más alkalmazásra** beállítást a szabályzat által **felügyelt alkalmazások számára a Megnyitás/megosztás szűrési** értékkel.  A *házirend által felügyelt alkalmazás* *megnyitási és megosztási* viselkedése csak más *szabályzat által felügyelt alkalmazásokat* jelenít meg megosztási lehetőségként. 

- Az **Mdm-megoldások által felügyelt eszközök**: az Intune-ban vagy harmadik féltől származó Mdm-megoldásokban regisztrált eszközökön az alkalmazások közötti adatmegosztás az alkalmazás-védelmi szabályzatokkal és a Mdm által központilag telepített egyéb felügyelt iOS-alkalmazásokkal az Intune app Policy és az iOS **Open a felügyeleti** szolgáltatásban. Annak biztosításához, hogy a MDM-megoldással telepített alkalmazások is társítva legyenek az Intune app Protection-szabályzatokhoz, konfigurálja a felhasználói UPN-beállítást a következő szakaszban leírtak szerint, [konfigurálja a felhasználói UPN-beállítást](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Annak megadásához, hogy hogyan kívánja engedélyezni a más alkalmazásoknak való adatátvitelt, engedélyezze a **szervezeti adatok más alkalmazásokba való küldését** , majd válassza ki az előnyben részesített megosztási szintet. Annak megadásához, hogy az alkalmazások hogyan fogadhatnak más alkalmazásokból származó adatfogadást, engedélyezze a **más alkalmazásokból érkező adatok fogadását** , majd válassza ki az adatok fogadásának kívánt szintjét. Az alkalmazásadatok fogadására és megosztására vonatkozó további információért lásd az [Adatáthelyezési beállítások](app-protection-policy-settings-ios.md#data-protection) szakaszt.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Az egyszerű felhasználónév beállításának konfigurálása a Microsoft Intune-hoz vagy külső EMM-megoldáshoz
A felhasználó UPN-beállításának konfigurálása az Intune által felügyelt eszközökön, vagy egy harmadik féltől származó, a regisztrált felhasználói fiók azonosítására **szolgáló más** gyártótól származó Az UPN-konfiguráció az Intune-ból üzembe helyezett alkalmazás-védelmi házirendekkel működik. Az alábbi eljárás az UPN-beállítás és az eredményül kapott felhasználói élmény konfigurálásának általános folyamata:

1. Az [Azure Portalon](https://portal.azure.com) [hozzon létre és osszon ki alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-nek. A vállalati igényeknek megfelelően konfigurálja a szabályzat beállításait, majd válassza ki azokat az iOS-es alkalmazásokat, amelyekre ennek a szabályzatnak kell vonatkoznia.

2. Telepítse az Intune-ban vagy a külső MDM-megoldáson keresztül felügyelni kívánt alkalmazásokat és e-mail-profilt az alábbi általánosított lépések segítségével. Ezt a folyamatot az 1. *példa*is tárgyalja.

3. Telepítse az alkalmazást a következő alkalmazás-konfigurációs beállításokkal a felügyelt eszközre:

      **kulcs** = IntuneMAMUPN, **érték** =  @ no__t-3

      Példa: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Az Intune-ban az alkalmazás-konfigurációs házirend beléptetési típusát **felügyelt eszközökre**kell beállítani.
     > Emellett az alkalmazást telepíteni kell a Intune Céges portálról (ha az elérhetőként van beállítva), vagy az eszköznek megfelelően leküldve. 

4. Telepítse a regisztrált eszközökre a **Megnyitási engedélyek felügyelete** szabályzatot a az Intune vagy külső MDM-szolgáltató segítségével.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>1\. példa: A rendszergazda teendői az Intune- vagy a külső MDM-konzolon

1. Nyissa meg az Intune vagy a külső MDM-szolgáltató felügyeleti konzolját. Nyissa meg a konzolnak azt a szakaszát, ahol a regisztrált iOS-eszközökre érvényes alkalmazáskonfigurációs beállításokat adja meg.

2. Az alkalmazások konfigurációjának megadására szolgáló szakaszban adja meg a következő beállítást:

   **kulcs** = IntuneMAMUPN, **érték** =  @ no__t-3

   A kulcs-érték pár pontos szintaxisa függ a külső MDM-szolgáltatótól. A következő táblázat példákat mutat be a harmadik féltől származó MDM-szolgáltatókra, valamint a kulcs/érték párokhoz megadott pontos értékekre.

   |Külső MDM-szolgáltató| Konfigurációs kulcs | Érték típusa | Konfigurációs érték|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Sztring | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Sztring | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Sztring | ${userUPN} **vagy** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | Sztring | $ {User. userPrincipalName} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Sztring | %upn% |

> [!NOTE]  
> Az iOS rendszerhez készült Outlook alkalmazás esetén, ha az alkalmazás-konfigurációs szabályzatot "a Configuration Designer használata" beállítással telepíti, a IntuneMAMUPN konfigurációs kulcsát a rendszer automatikusan beállítja a háttérben a házirendhez. További részletek az [iOS-és Android-alkalmazások konfigurációs házirendje – általános alkalmazás-konfiguráció – az új Outlook for iOS és az Android alkalmazás konfigurációs szabályzata –](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481)gyakori kérdések 


### <a name="example-2-end-user-experience"></a>2\. példa: A végfelhasználó teendői

Házirend *által* felügyelt alkalmazás megosztása *más ALKALMAZÁSOKKAL az operációs rendszer megosztásával*

1. A felhasználók megnyitják a Microsoft OneDrive alkalmazást egy regisztrált iOS-eszközön, és bejelentkeznek a munkahelyi fiókjába.  A felhasználó által megadott fióknak meg kell egyeznie a Microsoft OneDrive alkalmazás konfigurációs beállításaiban megadott fiók UPN-fiókjával.

2. Bejelentkezés után a rendszergazda által konfigurált Alkalmazásbeállítások a Microsoft OneDrive felhasználói fiókjára vonatkoznak.  Ez magában foglalja a **szervezeti adatküldés más alkalmazásoknak** beállítását a **szabályzat által felügyelt alkalmazások számára az operációs rendszer megosztási** értékével.

3. A felhasználó előzetesen megtekint egy munkahelyi fájlt, és az iOS-es felügyelt alkalmazásba való megnyitással próbálkozik.  

4. Az adatátvitel sikeresen megtörtént, és az adatok mostantól az iOS által felügyelt alkalmazásban is megtalálhatók a **nyílt felügyelettel** .  Az Intune-alkalmazás nem alkalmazható olyan alkalmazásokra, amelyek nem *házirend által felügyelt alkalmazások*.

Az iOS által felügyelt alkalmazások *megosztása* *egy házirend által* felügyelt alkalmazásba *a bejövő szervezeti adatokkal*

1. A felhasználók egy felügyelt e-mail-profillal megnyitják a natív e-maileket egy regisztrált iOS-eszközön.  

1. A felhasználó megnyit egy munkahelyi dokumentum mellékletét a natív levelezésből a Microsoft Wordbe.

1. A Word alkalmazás indításakor a következő két élmény egyike fordul elő:
   1. Az Intune-alkalmazás az alábbiak szerint védi az adatvédelmet:
      - A felhasználó bejelentkezett a munkahelyi fiókjába, amely megfelel a Microsoft Word alkalmazás alkalmazás-konfigurációs beállításaiban megadott fiók UPN-nek. 
      - A rendszergazda által konfigurált alkalmazás beállításai a Microsoft Word felhasználói fiókjára vonatkoznak.  Ide tartozik a **más alkalmazásoktól érkező adatok fogadásának** beállítása a **minden alkalmazásra a bejövő szervezeti** adatértékkel.
      - Az adatátvitel sikeres lesz, és a dokumentum a munkahelyi identitással van címkézve az alkalmazásban.  Az Intune-alkalmazás védi a dokumentum felhasználói műveleteit.
   1. Az Intune-alkalmazás **nem** védi az adatvédelmet, ha:
      - A felhasználó **nem** jelentkezett be a munkahelyi fiókjába.
      - A rendszergazda által konfigurált beállítások **nem** lesznek alkalmazva a Microsoft Wordre, mert a felhasználó nincs bejelentkezve.
      - Az adatátvitel sikeres lesz, és a dokumentum **nem** az alkalmazásban található munkahelyi identitással van megjelölve.  Az Intune-alkalmazás nem védi a dokumentum felhasználói műveleteit, mert **az nem aktív** .

    > [!NOTE]
    > A felhasználók hozzáadhatnak és használhatnak személyes fiókjaikat a Word használatával. Az alkalmazás-védelmi szabályzatok nem érvényesek, ha a felhasználó a Word alkalmazást a munkahelyi környezeten kívül használja. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Külső EMM-megoldásban megadott UPN-beállítás ellenőrzése

A felhasználói UPN-beállítás konfigurálása után ellenőrizze, hogy az iOS-alkalmazás képes-e az Intune app Protection-szabályzat fogadására és betartására.

Az **alkalmazás PIN-kódjának megkövetelése** házirend-beállítás például egyszerűen tesztelhető. Ha a házirend-beállítás értéke **kötelező**, a felhasználónak meg kell jelennie a PIN-kód beállításához vagy megadásához, mielőtt hozzá tudnak férni a vállalati információkhoz.

Először [hozzon létre és osszon ki egy alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-alkalmazásnak. Az alkalmazás-védelmi szabályzat tesztelésével kapcsolatos további információkért lásd: az [alkalmazás-védelmi házirendek érvényesítése](app-protection-policies-validate.md).


## <a name="see-also"></a>További információ
[Mi az Intune alkalmazásvédelmi szabályzat?](app-protection-policy.md)
