---
title: A Microsoft Store for Business VPP-alkalmazásainak kezelése
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan szinkronizálhatja az alkalmazásokat az Intune-ban a Microsoft Store for Business használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: a58136fc9e973963fbfe12efd03f92b5b8a01f9f
ms.sourcegitcommit: ec22a186a9cfa489a8490698e387624e480892d8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/13/2019
ms.locfileid: "71302523"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Mennyiségi programban vásárolt alkalmazások felügyelete a Microsoft Store for Business és a Microsoft Intune használatával

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A [Vállalati Microsoft Áruház](https://www.microsoft.com/business-store) az a hely, ahol alkalmazásokat vásárolhat a szervezete számára egyenként vagy mennyiségi program keretében. Az áruházat a Microsoft Intune-nal összekapcsolva a mennyiségi programban vásárolt alkalmazásokat az Azure Portalról kezelheti. Példa:
* Szinkronizálhatja az áruházból az Intune-nal megvásárolt (vagy ingyenes) alkalmazások listáját.
* A szinkronizált alkalmazások megjelennek az Intune felügyeleti konzolján; ezen alkalmazásokat a többi alkalmazáshoz hasonlóan oszthatja ki.
* Az alkalmazások online és offline licenccel rendelkező verziója is szinkronizálva van az Intune-nal. Az alkalmazások neve "online" vagy "offline" értékkel lesz hozzáfűzve a portálon.
* Az Intune felügyeleti konzolján nyomon követheti a szabad és a használatban lévő licencek számát.
* Ha nincs elegendő elérhető licenc, az Intune letiltja az alkalmazások kiosztását és telepítését.
* A Vállalati Microsoft Áruház által kezelt alkalmazások automatikusan visszavonják a licenceket, amikor egy felhasználó elhagyja a vállalatot, vagy amikor a rendszergazda eltávolítja a felhasználót és a felhasználói eszközöket.

## <a name="before-you-start"></a>Előkészületek

Mielőtt elkezdené a Vállalati Microsoft Áruházból származó alkalmazások szinkronizálását és hozzárendelését, tekintse át a következő információkat:

- Állítsa be az Intune-t a szervezet mobileszköz-kezelő szolgáltatójaként.
- Rendelkeznie kell fiókkal a Vállalati Microsoft Áruházban.
- Miután összekapcsolta a Vállalati Microsoft Áruház-fiókját az Intune-nal, később nem választhat hozzá másik fiókot.
- Az áruházban vásárolt alkalmazások manuálisan nem vehetők fel és nem törölhetők az Intune-ban. Az alkalmazások csak a Vállalati Microsoft Áruházzal szinkronizálhatók.
- A Vállalati Microsoft Áruházban vásárolt online és offline licencelt alkalmazásokat az Intune portál egyaránt szinkronizálja. Ezeket az alkalmazásokat eszközcsoportok vagy felhasználói csoportok számára telepítheti. 
- Az online alkalmazástelepítéseket az áruház felügyeli.
- Az Intune az ingyenes offline alkalmazásokat is szinkronizálja. Ezeket az alkalmazásokat az Intune, és nem az Áruház telepíti.
- Az eszközök akkor használhatják ezt a lehetőséget, ha csatlakoztatva vannak az Active Directory Domain Services szolgáltatáshoz vagy egy munkahelyhez.
- A regisztrált eszközöknek a Windows 10 1511-es vagy újabb verzióját kell használniuk.

Emellett a kapcsolódó készletek és a Vállalati Microsoft Áruházból szinkronizált offline licencelt alkalmazások mostantól egyetlen alkalmazásbejegyzésben jelennek meg a felhasználói felületen. A különálló csomagok üzembe helyezési adatait szintén egyetlen bejegyzésben összesítjük. Ha meg szeretné tekinteni a kapcsolódó készleteket az Azure Portalon, válassza az **Ügyfélalkalmazások** panel **Alkalmazáslicencek** lehetőségét.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>A Vállalati Microsoft Áruházbeli fiók összekapcsolása az Intune-nal
Mielőtt engedélyezné a szinkronizálást az Intune-konzolon, konfigurálnia kell az áruházbeli fiókját az Intune használatára felügyeleti eszközként:
1. Ügyeljen arra, hogy az Intune-ba való bejelentkezéshez használt bérlői fiókkal jelentkezzen be a [vállalati Microsoft Storeba](https://www.microsoft.com/business-store) .
2. A vállalati áruházban válassza a **kezelés** lapot, válassza a **Beállítások**lehetőséget, majd kattintson a **terjesztés** fülre.
3. Ha nem kifejezetten mobileszköz-felügyeleti eszközként **Microsoft Intune** érhető el, válassza a **felügyeleti eszköz hozzáadása** lehetőséget **Microsoft Intune**hozzáadásához. Ha nincs **Microsoft Intune** aktiválva a mobileszköz-kezelő eszközként, kattintson az **aktiválás** elemre **Microsoft Intune**gombra. Vegye figyelembe, hogy **Microsoft Intune-regisztráció**helyett aktiválni kell **Microsoft Intune** .

> [!NOTE]
> Korábban csak egyetlen felügyeleti eszközt társíthatott a Vállalati Microsoft Áruházhoz az alkalmazások hozzárendeléséhez. Mostantól több felügyeleti eszközzel is megteheti ezt (például az Intune-nal és a Configuration Managerrel). 

Most már folytathatja a műveletet, és beállíthatja a szinkronizálást az Intune-konzolon.

## <a name="configure-synchronization"></a>A szinkronizálás konfigurálása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
1. Az **Ügyfélalkalmazások** panelen válassza a **Beállítás** > **Vállalati Microsoft Áruház** lehetőséget.
2. Kattintson az **Engedélyezés** lehetőségre.
3. Ha még nem tette meg, kattintson a Vállalati Microsoft Áruházban való regisztrálás hivatkozására, és a fent leírtaknak megfelelően társítsa a fiókját.
5. A **Nyelv** legördülő listából válassza ki, hogy milyen nyelven jelenjenek meg a Vállalati Microsoft Áruházból származó alkalmazások az Azure Portalon. Az alkalmazások a megjelenítés nyelvétől függetlenül a végfelhasználó nyelvén lesznek telepítve (ha elérhető).
6. Kattintson a **Szinkronizálás** lehetőségre a Microsoft Áruházból megvásárolt alkalmazások Intune-ba való felvételéhez.

## <a name="synchronize-apps"></a>Az alkalmazások szinkronizálása

1. Az **Ügyfélalkalmazások** panelen válassza a **Beállítás** > **Vállalati Microsoft Áruház** lehetőséget.
2. Kattintson a **Szinkronizálás** lehetőségre a Microsoft Áruházból megvásárolt alkalmazások Intune-ba való felvételéhez.

> [!NOTE]
> A titkosított alkalmazáscsomag által kezelt alkalmazások jelenleg nem támogatottak, és nem lesznek szinkronizálva az Intune-nal.

## <a name="assign-apps"></a>Alkalmazások hozzárendelése

Az Áruházból származó alkalmazásokat ugyanúgy rendelheti hozzá, mint a többi Intune-alkalmazást. További információ: [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal). 

Az offline alkalmazások célcsoportjai lehetnek felhasználói csoportok, eszközcsoportok, valamit felhasználókat és eszközöket egyaránt tartalmazó csoportok.
Az offline alkalmazások telepíthetők egy eszköz adott felhasználója vagy az összes felhasználója számára. 


A Vállalati Microsoft Áruházból származó alkalmazások hozzárendelésekor az alkalmazást telepítő minden felhasználó egy-egy licencet használ fel. Ha felhasználja egy kiosztott alkalmazás összes elérhető licencét, akkor nem oszthat ki több példányt. Válasszon a következő lehetőségek közül:
* Távolítsa el az alkalmazást néhány eszközről.
* Szűkítse le az aktuális hozzárendelés hatókörét annyi felhasználóra, ahány elérhető licenccel rendelkezik.
* Vásároljon további példányokat az alkalmazásból a Vállalati Microsoft Áruházban.

## <a name="remove-apps"></a>Alkalmazások eltávolítása

A Microsoft Store Vállalatoknak szolgáltatásból szinkronizált alkalmazás eltávolításához be kell jelentkeznie a Microsoft Store Vállalatoknak szolgáltatásba, és vissza kell térítenie az alkalmazás árát. A folyamat ugyanaz, függetlenül attól, hogy az alkalmazás ingyenes-e. Az ingyenes alkalmazások esetében az áruház $0-es visszatérítést biztosít. Az alábbi példa egy ingyenes alkalmazásra vonatkozó visszatérítést mutat be. 

![Képernyőkép az alkalmazás eltávolításának részleteiről](./media/microsoft-store-for-business-01.png)

> [!NOTE]
> Az alkalmazások privát tárolóban való láthatóságának eltávolítása nem fogja tudni megőrizni az Intune-t az alkalmazás szinkronizálásával. Az alkalmazás teljes eltávolításához vissza kell térítenie az alkalmazást.

## <a name="next-steps"></a>További lépések

- [Mennyiségi programban vásárolt alkalmazások és könyvek kezelése a Microsoft Intune-nal](vpp-apps.md)
