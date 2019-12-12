---
title: Az Android Enterprise Microsoft Launcher konfigurálása az Intune-nal
titleSuffix: ''
description: Intune-konfigurációs szabályzatok használata a Microsoft Launcher használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc2e2ce7e19933accdb1063ccacf99fa3f54b09
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563955"
---
# <a name="configure-microsoft-launcher"></a>A Microsoft Launcher konfigurálása

A Microsoft Launcher egy Android-alkalmazás, amely lehetővé teszi, hogy a felhasználók személyre szabják a telefont, útközben is megmaradnak, és a telefonról a saját számítógépükre is átvihetik a munkát. 

Az Android Enterprise teljes körűen felügyelt eszközökön a feladatindító lehetővé teszi a vállalati IT-rendszergazdák számára a felügyelt eszközök kezdőlapjának testreszabását a tapéta, az alkalmazások és az ikon pozíciójának kiválasztásával. Ez egységesíti az összes felügyelt Android-eszköz megjelenését és működését különböző OEM-eszközökön és rendszerverziókban. 

## <a name="how-to-configure-the-microsoft-managed-home-screen-app"></a>A Microsoft Managed Home Screen alkalmazás konfigurálása 

Navigáljon a [Microsoft Endpoint Manager felügyeleti központjához](https://go.microsoft.com/fwlink/?linkid=2109431) , és válassza az **alkalmazások** > **alkalmazás-konfigurációs házirendek**elemet. Adja meg az **Android** rendszerű **felügyelt eszközökhöz** tartozó konfigurációs szabályzatot, és válassza a **Microsoft Launcher** lehetőséget a társított alkalmazásként. Kattintson a **konfigurációs beállítások** elemre a különböző elérhető felügyelt kezdőképernyő-beállítások konfigurálásához. 

## <a name="choosing-a-configuration-settings-format"></a>Konfigurációs beállítások formátumának kiválasztása 

A felügyelt kezdőképernyő konfigurációs beállításainak definiálására két módszer használható: 

- A **Configuration Designer** lehetővé teszi, hogy a beállításokat egy könnyen használható kezelőfelülettel konfigurálja, amely lehetővé teszi a szolgáltatások be-és kikapcsolását, valamint az értékek beállítását. Ebben a metódusban van néhány letiltott konfigurációs kulcs a BundleArray értékkel. Ezeket a konfigurációs kulcsokat csak a JSON-adatokat megadásával lehet konfigurálni. 

- A **JSON-adatai** lehetővé teszik az összes lehetséges konfigurációs kulcs megadását JSON-parancsfájl használatával. 

Ha a **Configuration Designer**használatával ad hozzá tulajdonságokat, automatikusan átalakíthatja ezeket a TULAJDONSÁGOKAT a JSON formátumba úgy, hogy KIVÁLASZTJA a **JSON-adatok megadása** lehetőséget a **konfigurációs beállítások formátuma** legördülő listából az alábbi ábrán látható módon.

   ![Konfigurációs beállítások formátuma – a Configuration Designer használata](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>A Configuration Designer használata

A Configuration Designer lehetővé teszi az előre megadott beállítások és a hozzájuk tartozó értékek kiválasztását.

   ![Konfigurációs beállítások formátuma – JSON-adatbevitel](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

A következő táblázat felsorolja a Microsoft Launcher elérhető konfigurációs kulcsait, az értékek típusát, az alapértelmezett értékeket és a leírásokat. A leírás a kiválasztott értékek alapján biztosítja a várt eszköz viselkedését. A Configuration Designerben letiltott konfigurációs kulcsok nem szerepelnek a táblázatban.

|    Konfigurációs kulcs    |    Érték típusa    |    Alapértelmezett érték    |    Description     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Regisztráció típusa    |    Sztring     |    Alapértelmezett    |    Lehetővé teszi a beléptetési típus beállítását, amelyre a szabályzat vonatkozik. Az **alapértelmezett** érték jelenleg a **CorporateOwnedBuisnessOnly**-ra hivatkozik. Jelenleg nincsenek más támogatott regisztrációs típusok.        JSON-kulcs neve: management_mode_key        |
|    Kezdőképernyő alkalmazás megrendelésének felhasználói módosítása engedélyezve    |    Logikai    |    Igaz    |    Lehetővé teszi annak megadását, hogy a végfelhasználó módosíthatja-e a **kezdőképernyő-alkalmazás megrendelésének** beállításait.<ul><li>Ha **igaz**értékre van állítva, a házirendben definiált alkalmazási sorrend csak a kezdeti telepítéshez lesz érvényesítve. Ezt követően a szabályzatot nem kényszeríti ki a felhasználó által esetlegesen végrehajtott módosítások tiszteletben tartására.</li><li>Ha **hamis**értékre van állítva, a rendszer minden egyes szinkronizáláskor érvényesíti az alkalmazás sorrendjét.</li></ul><br>**Megjegyzés:** A kezdőképernyő-alkalmazás sorrendje csak a JSON-szerkesztő használatával konfigurálható.<br><br>JSON-kulcs neve:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Rácsvonal méretének beállítása    |    Sztring    |    Automatikus    |    Lehetővé teszi az alkalmazások rácsos méretének megadását a kezdőképernyőn pozícionálva. Az alkalmazás sorainak és oszlopainak számát a következő formátumban állíthatja be a rácsvonalak méretének meghatározásához: `columns;rows`. Ha a rács méretét határozza meg, a kezdőképernyő egy sorában megjelenő alkalmazások maximális száma lesz a beállított sorok száma, és a kezdőképernyő egyik oszlopában megjelenő alkalmazások maximális száma a beállított oszlopok száma.<br><br>        JSON-kulcs neve:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Eszköz háttérképének beállítása    |    Sztring    |    Null    |    Lehetővé teszi, hogy tetszőleges háttérképet állítson be a háttérképként beállítani kívánt rendszerkép URL-címének megadásával.<br><br>JSON-kulcs neve:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Az eszköz tapétájának felhasználói módosításának beállítása engedélyezett    |    Logikai    |    Igaz    |    Lehetővé teszi annak megadását, hogy a végfelhasználó módosíthatja-e az eszköz háttérképének beállítása beállítást.<ul><li>Ha **igaz**értékre van állítva, a rendszer a szabályzat háttérképét csak a kezdeti telepítéshez kényszeríti ki. Ezt követően a szabályzatot nem kényszeríti ki a felhasználó által esetlegesen végrehajtott módosítások tiszteletben tartására.</li><li>Ha **hamis**értékre van állítva, a rendszer minden szinkronizáláskor kikényszeríti a hátteret.</li></ul><br>JSON-kulcs neve:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Hírcsatorna engedélyezése    |    Logikai    |    Igaz    |    Lehetővé teszi, hogy az eszközön engedélyezze az indító hírcsatornát, amikor a felhasználó a kezdőképernyő jobb oldalán található.<ul><li>Ha **igaz**értékre van állítva, a hírcsatorna engedélyezve lesz.</li><li>Ha **hamis**értékre van állítva, a hírcsatorna le lesz tiltva.</li></ul><br>JSON-kulcs neve:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    A hírcsatorna lehetővé teszi a felhasználói módosítás engedélyezését    |    Logikai    |    Igaz    |     Lehetővé teszi annak megadását, hogy a végfelhasználó módosíthatja-e a **hírcsatorna engedélyezésének** beállítását.<ul><li>Ha **igaz**értékre van állítva, a rendszer csak a kezdeti telepítéshez kényszeríti ki a hírcsatornát. Ezt követően a szabályzatot nem kényszeríti ki a felhasználó által esetlegesen végrehajtott módosítások tiszteletben tartására.</li><li>Ha **hamis**értékre van állítva, a rendszer minden szinkronizáláskor kikényszeríti a hírcsatornát.</li></ul><br>JSON-kulcs neve:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>JSON-adatbevitel

Adja meg a JSON-adatbevitelt a Microsoft Launcher összes elérhető beállításának konfigurálásához, valamint a **Configuration Designerben**letiltott beállításokhoz az alább látható módon.

   ![Configuration Designer – JSON-adatbázis](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

A Configuration Designer táblában (fent) található konfigurálható beállítások listáján kívül az alábbi táblázat azokat a konfigurációs kulcsokat tartalmazza, amelyeket csak JSON-adatokkal lehet konfigurálni.

|    Konfigurációs kulcs    |    Érték típusa    |    Alapértelmezett érték    |    Description     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Engedélyezett alkalmazások beállítása<br>JSON-kulcs:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Lásd: [engedélyezett alkalmazások beállítása](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    Lehetővé teszi a kezdőképernyőn látható alkalmazások készletének megadását az eszközön telepített alkalmazások közül. Az alkalmazásokat megadhatja a láthatóvá tenni kívánt alkalmazások alkalmazáscsomag-nevének megadásával, például `com.android.settings` a kezdőképernyőn elérhetővé tenné a beállításokat. Az engedélyezett alkalmazások listája már telepítve van az eszközön, hogy láthatóvá váljon a kezdőképernyőn.<p>Tulajdonságok:<ul><li>**Csomag:** Az alkalmazáscsomag neve</li><li>**Osztály:** Az alkalmazás tevékenysége, amely egy adott alkalmazás oldalára vonatkozik. Ha ez az érték üres, az alapértelmezett alkalmazás lapot fogja használni.</li></ul>      |
|    Kezdőképernyő-alkalmazás sorrendje<br>JSON-kulcs: `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Lásd: [kezdőképernyő app Order](configure-microsoft-launcher.md#home-screen-app-order)      |    Lehetővé teszi az alkalmazás megrendelésének megadását a kezdőképernyőn.<p>Tulajdonságok:<br><ul><li>**Írja be a következőt:** Az egyetlen támogatott típus `application`.</li><li>**Pozíció:** Az alkalmazás ikonjának tárolóhelye a kezdőképernyőn. Ekkor elindul az 1. pozíció a bal felső sarokban, és balról jobbra, felülről lefelé haladva.</li><li>**Csomag:** Az alkalmazáscsomag neve.</li><li>**Osztály:** Az alkalmazás tevékenysége, amely egy adott alkalmazás oldalára vonatkozik. Ha ez az érték üres, az alapértelmezett alkalmazás lap lesz használatban.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Engedélyezett alkalmazások beállítása

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>Kezdőképernyő-alkalmazás sorrendje

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

A következő példa egy JSON-szkriptet tartalmaz, amely tartalmazza az összes elérhető konfigurációs kulcsot:

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>További lépések

- Az Android Enterprise teljes körűen felügyelt eszközökkel kapcsolatos további információkért lásd: [az Android Enterprise Intune-regisztrációjának beállítása teljes mértékben](../enrollment/android-fully-managed-enroll.md)felügyelt eszközök.
