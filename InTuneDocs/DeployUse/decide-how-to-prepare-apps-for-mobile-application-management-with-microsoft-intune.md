---
# required metadata

title: Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal
Az Intune alkalmazásburkoló eszközével vagy az Intune App SDK-val engedélyezheti, hogy az alkalmazások mobilalkalmazás-kezelési házirendeket használjanak. Az alábbi információkkal többet megtudhat erről a két módszerről és arról, mikor érdemes használni azokat.

## Intune alkalmazásburkoló eszköz
Az alkalmazásburkoló eszköz főleg belső üzletági (LOB) alkalmazásokhoz készült. Az eszköz egy parancssori alkalmazás, amely egy burkolót hoz létre az alkalmazás körül, amely azután lehetővé teszi az alkalmazás Intune mobilalkalmazás-kezelési házirend általi kezelését. Nincs szüksége a forráskódra az eszköz használatához, de aláíró hitelesítő adatokra igen.  Az aláíró hitelesítő adatokról további információért lásd: [Intune blog](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx). Az alkalmazásburkoló eszköz dokumentációja az [Android alkalmazásburkoló eszköz](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) és az [iOS alkalmazásburkoló eszköz](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) című cikkekben található.

Az alkalmazásburkoló eszköz nem támogatja az App vagy Play Store alkalmazásait és azon szolgáltatásokat, amelyek a fejlesztési idő integrációját igénylik (lásd a következő szolgáltatás-összehasonlító táblázatot).

Az alkalmazásburkoló eszközt kell használnia az SDK helyett, ha az alkalmazás már meg lett írva, vagy ha a forráskód nem érhető el.

## Intune App SDK
Az App SDK főleg olyan ügyfeleknek lett kialakítva, akik az App vagy Play Store áruházakból származó alkalmazásokkal rendelkeznek, és az Intune-nal szeretnék kezelni az alkalmazásokat. De bármely alkalmazás kihasználhatja az SDK integrálásának előnyeit akkor is, ha azok üzletági alkalmazások.

További információk az SDK-ról: [Áttekintés](/intune/develop/intune-app-sdk). Az SDK használatának megkezdéséhez olvassa el a [Bevezetés a Microsoft Intune App SDK használatába](/intune/develop/intune-app-sdk-get-started) című szakaszt.

## Szolgáltatások összehasonlítása
Ez a táblázat az App SDK-hoz és az alkalmazásburkoló eszközhöz használható beállításokat sorolja fel.

> [!NOTE] Az alkalmazásburkoló használható a különálló Intune-nal és a Configuration Managerrel kombinált Intune-nal is.

|Szolgáltatás|App SDK|Alkalmazásburkoló eszköz|
|-----------|---------------------|-----------|
|A vállalat által kezelt böngészőben megjelenő webtartalom korlátozása|X|X|
|Android-, iTunes- vagy iCloud-biztonságimentések megakadályozása|X|X|
|Más alkalmazásokból való adatátvitel engedélyezése az alkalmazásnak|X|X|
|Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak|X|X|
|Kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal|X|X|
|Egyszerű PIN-kód szükséges a hozzáféréshez|X|X|
|Az alkalmazások beépített PIN-kódjának lecserélése Intune PIN-kóddal|X||
|A PIN-kód alaphelyzetbe állítása előtti kísérletek számának megadása|X|X|
|Ujjlenyomat kérése PIN-kód helyett (csak iOS)<br></br>**Megjegyzés:** Csak MAM-környezetekben érhető el.|X||
|Vállalati hitelesítő adatok szükségesek a hozzáféréshez|X|X|
|A felügyelt alkalmazások futtatásának tiltása jailbreakelt vagy rootolt eszközökön|X|X|
|Alkalmazásadatok titkosítása|X|X|
|A hozzáférési követelmények ismételt ellenőrzése a megadott számú percek után|X|X|
|Az offline türelmi időszak megadása|X|X|
|Képernyőrögzítés letiltása (csak Android esetén)|X|X|
|Teljes törlés|X|X|
|Szelektív törlés <br></br>**Megjegyzés:** iOS esetén a felügyeleti profil törlésekor az alkalmazást is törli.|X||
|A „Mentés másként” művelet letiltása |X||
|Többszörös identitás támogatása|X||

### További információ
[Android alkalmazásburkoló eszköz](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS alkalmazásburkoló eszköz](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Alkalmazások előkészítése a mobilalkalmazás-felügyeletre az SDK segítségével](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=Jun16_HO1-->


