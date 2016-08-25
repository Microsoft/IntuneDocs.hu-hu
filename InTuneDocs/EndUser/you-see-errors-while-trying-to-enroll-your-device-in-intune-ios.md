---
title: "Hibába ütközik, amikor megpróbálja regisztrálni az iOS-es eszközt az Intune-ban | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
ROBOTS: noindex
ms.reviewer: esmich
ms.suite: ems
ms.sourcegitcommit: 39e810466d3a98789f0f1338f68d2be80d757d39
ms.openlocfilehash: 21305aa10caecdcc6f2d22f305d47f74a5b3f3ba


---


# Hibába ütközik, amikor megpróbálja regisztrálni az iOS-es eszközt az Intune-ban

A következő táblázat azon hibákat tartalmazza, amelyeket az iOS-es eszközök Intune-ban történő regisztrálásakor láthat. Küldje el ezt a hivatkozást a rendszergazdának. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

|Hibaüzenet|Probléma|Miről tájékoztassa a rendszergazdát?|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|DeviceCapReached|Már túl sok mobileszközt regisztrált.|A felhasználónak el kell távolítania az aktuálisan regisztrált mobileszközeit a Vállalati portálról, mielőtt másikat regisztrálhatna. Kövesse a meglévő eszköz típusára vonatkozó utasításokat: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios), [Windows](unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Probléma akadt azzal a tanúsítvánnyal, amely lehetővé teszi a mobileszköz és a vállalat hálózata közötti kommunikációt.<br /><br />Lépjen kapcsolatba az informatikai rendszergazdákkal, és mondja el nekik, hogy az **APNSCertificateNotValid** üzenetet kapta a mobileszköz regisztrálása során, és kérje meg őket, hogy nézzék meg a jelen táblázatban lévő megoldást.|Az Apple Push Notification (APN) szolgáltatás révén elérhetők a beléptetett iOS-eszközök. Ha nem lettek végrehajtva az APN-tanúsítvány beszerzésének lépései, vagy ha az APN-tanúsítvány lejárt, a beléptetési kísérletek ezzel az üzenettel hiúsulnak meg.<br /><br />A felhasználók konfigurálásához olvassa el [Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) című szakaszt, valamint a [felhasználók és eszközök rendszerezésével](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5) kapcsolatos tudnivalókat.|
|AccountNotOnboarded|Probléma akadt azzal a tanúsítvánnyal, amely lehetővé teszi a mobileszköz és a vállalat hálózata közötti kommunikációt.<br /><br />Lépjen kapcsolatba az informatikai rendszergazdákkal, és mondja el nekik, hogy az **APNSNotOnboarded** üzenetet kapta a mobileszköz regisztrálása során, és kérje meg őket, hogy nézzék meg a jelen táblázatban lévő megoldást.|Az Apple Push Notification (APN) szolgáltatás révén elérhetők a beléptetett iOS-eszközök. Ha nem lettek végrehajtva az APN-tanúsítvány beszerzésének lépései, vagy ha az APN-tanúsítvány lejárt, a beléptetési kísérletek ezzel az üzenettel hiúsulnak meg.<br /><br />További információért lásd: [Az iOS és Mac rendszerek felügyeletének előkészítése a Microsoft Intune-ban](/Intune/Deployuse/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Lehet, hogy nem iOS-eszközzel próbált meg regisztrálni. A regisztrálni próbált mobileszköz nem támogatott.<br /><br />Győződjön meg róla, hogy az eszköz 7.1-es vagy újabb iOS-verziót futtat.<br /><br />Lépjen kapcsolatba az informatikai rendszergazdákkal, és mondja el nekik, hogy a **DeviceTypeNotSupported** üzenetet kapta a mobileszköz regisztrálása során, és kérje meg őket, hogy nézzék meg a jelen táblázatban lévő megoldást.|Győződjön meg róla, hogy a felhasználó eszköze 7.1-es vagy újabb iOS-verziót futtat.|
|UserLicenseTypeInvalid|Nem tudja regisztrálni a mobileszközt, mert a felhasználói fiók még nem tagja egy szükséges felhasználói csoportnak.<br /><br />Lépjen kapcsolatba az informatikai rendszergazdákkal, és mondja el nekik, hogy a **UserLicenseTypeInvalid** üzenetet kapta a mobileszköz regisztrálása során, és kérje meg őket, hogy nézzék meg a jelen táblázatban lévő megoldást.|Mielőtt a felhasználók regisztrálhatnák az eszközeiket, a megfelelő felhasználói csoport tagjának kell lenniük. Ez az üzenet azt jelenti, hogy nem rendelkeznek a megfelelő licenctípussal a meghatározott mobileszköz-kezelő szolgáltatóhoz. Ha például az Intune lett mobileszköz-kezelő szolgáltatóként meghatározva, és System Center 2012 R2 Configuration Manager-licencet használnak, ezt a hibaüzenetet látják.<br /><br />Tekintse meg az alábbiakat a további információkért:<br /><br />Olvassa el [Az iOS kezelésének beállítása a Microsoft Intune-nal](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) című szakaszt, illetve a felhasználók konfigurálásával („Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz”)(/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3), valamint a [felhasználók és eszközök rendszerezésével](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5) kapcsolatos tudnivalókat.|
|MdmAuthorityNotDefined|Az informatikai rendszergazdának konfigurálnia kell a vállalatban lévő mobileszközök felügyeletének módját.<br /><br />Lépjen kapcsolatba az informatikai rendszergazdákkal, és mondja el nekik, hogy az **MdmAuthorityNotDefined** üzenetet kapta a mobileszköz regisztrálása során, és kérje meg őket, hogy nézzék meg a jelen táblázatban lévő megoldást.|A mobileszköz-kezelő szolgáltató nincs megadva az Intune-ban.<br /><br />Tekintse meg az 1. elemet [Az első lépések a Microsoft Intune 30 napos próbaverziójában](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) „6. lépés: Mobileszközök regisztrálása és alkalmazások telepítése” szakaszában.|

### További információ
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)


<!--HONumber=Jun16_HO2-->


