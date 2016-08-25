---
title: "A mobileszközök regisztrálásának módjai | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
translationtype: Human Translation
ms.sourcegitcommit: f1dc713099c982d6e32c87b814dd3f55b1656eda
ms.openlocfilehash: 5668a4d8a6cce15446201926b03d71ede174a299


---

# A mobileszközök regisztrálásának módjai

A mobileszköz regisztrálása az a folyamat, amely az okostelefonokat, a táblagépeket és a számítógépeket a menedzsment részévi teszi a Microsoft Intune segítségével. Rendszergazdaként el kell döntenie, hogy hogyan érdemes regisztrálni az eszközeit az alábbi szempontok alapján:

 -  Tulajdonjog (személyi vagy vállalati tulajdonban lévő eszköz)
 -  Használat (megosztott vagy személyes)
 -  Platform (iOS, Android, Windows Phone, Windows-számítógép, Mac számítógép) – Beléptetési módszer szerint kiválasztva

Az alábbi kérdésekre adott válaszaiból megtudhatja, hogy melyik regisztrációs módszer felel meg a legjobban az Ön által kezelt eszközöknek.

## **Az alkalmazottak saját eszközeiket használják, vagy a szervezet biztosítja nekik ezeket az eszközöket?**

  A **felhasználói tulajdonban lévő eszközök** vagy más néven „saját eszközök” (BYOD) regisztrációjával a felhasználók regisztrálhatják eszközeiket az egyes vállalati erőforrások – például a levelezés, a vállalati alkalmazások, a vállalati adatok és a támogatás – eléréséhez. A **vállalati tulajdonban lévő eszközöket** (COD) a vállalat biztosítja az alkalmazottak számára az üzleti igények alapján.
  > [!div class="button"]
  [BYOD-regisztráció >](#byod-device-enrollment)   [COD-regisztráció >](#cod-device-enrollment)

### BYOD-eszközök regisztrálása

A BYOD-regisztráció megköveteli a felhasználóktól az Intune Vállalati portál alkalmazásának telepítését a saját eszközeiken. Ezután indíthatják el az alkalmazást, és regisztrálhatnak a munkahelyi vagy iskolai fiókjuk hitelesítő adataival. Feltéve, hogy az Intune talál licencet az ilyen hitelesítő adatokhoz, a rendszer hozzáadja az eszközt az Intune felügyeleti konzoljához. Ezután az eszközre az Intune házirendje érvényes, amely biztosítja a hozzáférést a vállalati erőforrásokhoz.

**Eszköz típusának kiválasztása:**
> [!div class="button"]
[Android](..deploy-use/set-up-android-management-with-microsoft-intune) [iOS és Mac](..deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile és Windows Phone](..deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows rendszerű számítógépek](..deploy-use/set-up-windows-device-management-with-microsoft-intune)


### COD-eszközök regisztrálása

A vállalati tulajdonban lévő eszközöket (COD) regisztrálni lehet meghatározott felhasználók támogatására, vagy sok felhasználó közötti megosztásra.  A **megosztott eszközökhöz** több felhasználó is hozzáfér, és általában nem használhatók levelezésre. Ilyenek például a kioszkmódban működő, vagy a feladatközpontú, egy helyen tárolt, közös használatú eszközök. Az ajánlott regisztrációs módszer az eszköz platformjától függ. Az egyéni felhasználókkal rendelkező **dedikált eszközök** egyszerre nyomon követendő vállalati eszközök és személyes eszközök, amelyről a felhasználók elérhetik e-mail postafiókjukat és adataikat. Az ajánlott regisztrációs módszer az eszköz platformjától függ. [Következő kérdés...](Are your company-owned devices shared or do they have dedicated users?)

## **A vállalati tulajdonban lévő eszközök megosztott eszközök, vagy dedikált felhasználókkal rendelkeznek?**

> [!div class="button"]
[Megosztott >](#Shared-company-owned-devices)   [Dedikált >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)


### Vállalat tulajdonban lévő megosztott eszközök

Ezekhez az eszközökhöz több felhasználó is hozzáfér, és általában nem használhatók levelezésre. Ilyenek például a kioszkmódban működő, vagy a feladatközpontú, egy helyen tárolt, közös használatú eszközök. Az ajánlott regisztrációs módszer az eszköz platformjától függ.

  - **Windows- és Android-eszközök** – A *készülékregisztráció-kezelő* egy olyan Intune-fiók, amelyen több megosztott eszközt is regisztrálhat a Vállalati portál alkalmazással.
  > [!div class="button"]
  [Windows >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#shared-ios-device-enrollment)

### Megosztott iOS-eszközök regisztrálása

A megosztott, vállalati tulajdonban lévő iOS-es eszközök regisztrációjának előnyben részesített módja az eszközök megvásárlási és kezelési módjától függ:

  - **Az Apple Készülékregisztrációs programja (Device Enrollment Program – DEP)** – A DEP-pel vásárolt vagy kezelt iOS-eszközökre regisztrációs profil telepíthető. Amikor a felhasználók először kapcsolják be az eszközt, az letölti a DEP-profilt és regisztrálja az eszközt
  - **Az Apple Configurator Mac számítógépen (Mac)** – Az Apple Configurator egy Mac-számítógépekre tervezett Apple-alkalmazás. Az iOS-eszközeit egy USB-kábellel csatlakoztathatja a Mac-számítógéphez, majd feltelepítheti rájuk a regisztrációs profilt. Ha az eszközöket a gyári beállítások visszaállításával szeretné regisztrálni, használja a Beállítási asszisztenssel való regisztrációt. Ha nem szeretné a gyári beállításokat visszaállítani az eszközökön, használja Közvetlen regisztrációt.
  - **Egyik sem** – Ha nem tudja vagy nem kívánja az Apple DEP- vagy az Apple Configurator-regisztrációt használni, használja az Intune készülékregisztráció-kezelőjét (Device Enrollment Manager – DEM).

  **Válassza az alábbi lehetőséget::**
    > [!div class="button"]
     [DEP-regisztráció >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Mac >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Közvetlen regisztráció >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)  

  > [!div class="button"]
    [DEP-regisztráció >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Egyéni felhasználók** – Az egyéni félhasználókkal rendelkező vállalati tulajdonban lévő eszközök egyszerre nyomon követendő vállalati eszközök és személyes eszközök, amelyről a felhasználók elérhetik e-mail postafiókjukat és adataikat. Az ajánlott regisztrációs módszer az eszköz platformjától függ.

  - **Windows- és Android-eszközök** – A vállalati eszközök IMEI-számainak importálásával vállalati eszközként jelölheti meg őket az Intune-ban. A felhasználók ezután személyes eszközként regisztrálhatják az eszközeiket a Vállalati portál telepítésével, így hozzáférhetnek az olyan vállalati erőforrásokhoz, mint a levelezés, a vállalati alkalmazások és az adatok.
  > [!div class="button"]
  [Megjelölés IMEI-számokkal >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS-eszközök** – A megosztott iOS-eszközök háromféleképpen kezelhetők.  **Hogyan regisztrálja a megosztott iOS-eszközöket?**

    - **Az Apple Készülékregisztrációs programja (Device Enrollment Program – DEP)** – A DEP-pel vásárolt vagy kezelt iOS-eszközökre regisztrációs profil telepíthető. Amikor a felhasználók először kapcsolják be az eszközt, az letölti a DEP-profilt és annak megfelelően regisztrálja az eszközt.
    > [!div class="button"]
    [DEP-regisztráció](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Az Apple Configurator Mac számítógépen** – Az Apple Configurator egy Mac-számítógépekre tervezett Apple-alkalmazás. Az iOS-eszközeit egy USB-kábellel csatlakoztathatja a Mac-számítógéphez, majd feltelepítheti rájuk a regisztrációs profilt. Ha az eszközöket a gyári beállítások visszaállításával szeretné regisztrálni, használja a Beállítási asszisztenssel való regisztrációt.

    Ha nem szeretné a gyári beállításokat visszaállítani az eszközökön, használja Közvetlen regisztrációt.
    Ha az eszközöket a gyári beállítások visszaállításával szeretné regisztrálni, használja a Beállítási asszisztenssel való regisztrációt.
    > [!div class="button"][iOS Setup Assistant enrollment](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS direct enrollment](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Egyik sem** – Ha nem tudja vagy nem kívánja az Apple DEP- vagy az Apple Configurator-regisztrációt használni, a vállalati eszközök IMEI-számának importálásával vállalati eszközként jelölheti meg az eszközöket az Intune-ban. A felhasználók ezután személyes eszközként regisztrálhatják az eszközeiket a Vállalati portál telepítésével, így hozzáférhetnek az olyan vállalati erőforrásokhoz, mint a levelezés, a vállalati alkalmazások és az adatok.
    > [!div class="button"][Tag devices with IMEI numbers](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Jun16_HO5-->


