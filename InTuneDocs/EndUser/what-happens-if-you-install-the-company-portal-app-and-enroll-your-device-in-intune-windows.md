---
title: "Mi történik a Vállalati portál alkalmazás telepítésekor és az eszköz Intune-beli regisztrálásakor? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ms.reviewer: priyar
ms.suite: ems
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: e2da1f39d0cfe05bb0ea1c149c91e5ff82312c01


---


# Mi történik a Vállalati portál alkalmazás telepítésekor és az eszköz Intune-beli regisztrálásakor?

Ha szeretné megtudni, hogy mi történik a Vállalati portál alkalmazás telepítésekor és az eszköznek az Intune-beli regisztrálásakor, kattintson az eszközének megfelelő hivatkozásra a fenti „A cikk tartalma” részben. Windows 10-eszközökkel kapcsolatos információkért nyissa meg [ezt az oldalt](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## Windows 8.1 és Windows RT
Miután telepítette a Vállalati portál alkalmazást, és annak használatával regisztrálta a Windows 8.1 Enterprise, Windows 8.1 Professional vagy Windows RT rendszerű eszközét az Intune-ban, lehetősége nyílik a következőkre:

-   Elérheti a vállalat hálózatát, a saját levelezését és a munkájához szükséges fájlokat

-   Letöltheti a vállalati alkalmazásokat a vállalati portálról

-   Automatikusan konfigurálhatja vállalati e-mail fiókját

-   Ha elveszíti a telefonját, visszaállíthatja a gyári beállításait

A regisztrálás lépéseit lásd: [Windows-eszköz regisztrálása az Intune-ban](enroll-your-device-in-intune-windows.md). A [Milyen adatokhoz jut hozzá a rendszergazda, ha regisztrálom az eszközömet az Intune-ban?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) című szakaszból megtudhatja, hogy a rendszergazda mit láthat az eszközén.

Számítógép hozzáadásakor:

-   Olyan szoftverek települnek a számítógépre, amelyek lehetővé teszik a rendszergazda számára a számítógép felügyeletét, Önnek pedig a különböző vállalati erőforrások, például alkalmazások és támogatási információk elérését. A rendszergazda automatikusan frissítheti ezeket a szoftvereket.

-   Lehetséges, hogy az Intune Endpoint Protection is települ a számítógépre. Ez egy vírusok és kártevő szoftverek elleni védelmi alkalmazás.

-   Az IT rendszergazda leltárt készíthet a számítógépre telepített szoftverekről, ideértve az Ön által személyes használatra telepített szoftvereket is.

-   Elképzelhető, hogy el kell fogadnia a vonatkozó használati feltételeket.

-   A IT rendszergazda adatokat gyűjthet a számítógép merevlemezéről, illetve adatokat törölhet róla. Az IT rendszergazda akár a merevlemez teljes tartalmát is törölheti.

-   Az IT rendszergazda alkalmazásokat és frissítéseket telepíthet a számítógépre.

-   Az IT rendszergazda házirendeket léptethet életbe a számítógépen. Lehetséges például, hogy jelszót vagy PIN-kódot kell beállítania a számítógépen; ebből fakadóan kizárhatja magát a számítógépről, vagy letörölheti az összes adatot a számítógép merevlemezéről, ha túlságosan sokszor adja meg hibásan a jelszót.

## Windows Phone 8.1 és Windows Phone 8
Miután telepítette a Vállalati portál alkalmazást, és annak használatával regisztrálta a Windows Phone 8.1-es vagy Windows Phone 8-as eszközét az Intune-ban, lehetősége nyílik a következőkre:

-   Elérheti a vállalat hálózatát, a saját levelezését és a munkájához szükséges fájlokat

-   Letöltheti a vállalati alkalmazásokat a vállalati portálról

-   Automatikusan konfigurálhatja vállalati e-mail fiókját

-   Ha elveszíti a telefonját, visszaállíthatja a gyári beállításait

A regisztrálás lépéseit lásd: [Windows-eszköz regisztrálása az Intune-ban](enroll-your-device-in-intune-windows.md). A [Milyen adatokhoz jut hozzá a rendszergazda, ha regisztrálom az eszközömet az Intune-ban?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) című szakaszból megtudhatja, hogy a rendszergazda mit láthat az eszközén.

Windows Phone-alapú eszköz hozzáadásakor jogosultságot ad az IT rendszergazdának az eszköz elérésére. A következőkre nyílik lehetőség:

-   Az eszköz visszaállítása az alapértelmezett gyári beállításokra. Az eszköz elvesztésekor vagy ellopásakor bizonyulhat hasznosnak.

-   Az összes céges adat és telepített munkahelyi alkalmazás eltávolítása. A saját adatok és beállítások nem törlődnek.

-   Jelszó vagy PIN-kód megadásának kényszerítése az eszközön, így túl sok helytelen jelszó megadásakor a rendszer kizárhatja az eszközről, vagy visszaállíthatja az eszközön a gyári alapbeállításokat, amely az adatok törlését is magával vonhatja.

-   Az eszközön található összes adat titkosításának kikényszerítése. Hozzájárul az adatok védelméhez az eszköz elvesztésekor és ellopásakor.

-   Ehhez el kell fogadnia a használati feltételeket.

-   Az SD-kártya letiltása.

-   Az eszközön található alkalmazások frissítéseinek telepítése. Ez csak a frissítésekre vonatkozik. Az IT rendszergazda nem kényszerítheti ki új alkalmazások telepítését az eszközre, de Ön a kívánsága szerint telepítheti a vállalati portálon elérhető alkalmazásokat.

-   Az eszköz a vállalati portálhoz való hozzáadása után körülbelül 8 óránként a következőket hajtja végre:

    -   Az IT rendszergazda által elérhetővé tett házirendek és alkalmazásfrissítések letöltése.

    -   A hardverleltár változásainak elküldése.

    -   A vállalati alkalmazások leltárában bekövetkezett változások elküldése.

## Windows 7 és Vista
Miután telepítette a Vállalati portál alkalmazást, és annak használatával regisztrálta a Windows 7-es vagy Windows Vista rendszerű eszközét az Intune-ban, lehetősége nyílik a következőkre:

-   Elérheti a vállalat hálózatát, a saját levelezését és a munkájához szükséges fájlokat

-   Letöltheti a vállalati alkalmazásokat a vállalati portálról

-   Automatikusan konfigurálhatja vállalati e-mail fiókját

-   Ha elveszíti a telefonját, visszaállíthatja a gyári beállításait

A [Milyen adatokhoz jut hozzá a rendszergazda, ha regisztrálom az eszközömet az Intune-ban?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) című szakaszból megtudhatja, hogy a rendszergazda mit láthat az eszközén.

Számítógép hozzáadásakor:

-   Olyan szoftverek települnek a számítógépre, amelyek lehetővé teszik a rendszergazda számára a számítógép felügyeletét, Önnek pedig a különböző vállalati erőforrások, például alkalmazások és támogatási információk elérését. A rendszergazda automatikusan frissítheti ezeket a szoftvereket.

-   Lehetséges, hogy az Intune Endpoint Protection is települ a számítógépre. Ez egy vírusok és kártevő szoftverek elleni védelmi alkalmazás.

-   Az IT rendszergazda leltárt készíthet a számítógépre telepített szoftverekről, ideértve az Ön által személyes használatra telepített szoftvereket is.

-   Elképzelhető, hogy el kell fogadnia a vonatkozó használati feltételeket.

-   A IT rendszergazda adatokat gyűjthet a számítógép merevlemezéről, illetve adatokat törölhet róla. Az IT rendszergazda akár a merevlemez teljes tartalmát is törölheti.

-   Az IT rendszergazda alkalmazásokat és frissítéseket telepíthet a számítógépre.

-   Az IT rendszergazda házirendeket léptethet életbe a számítógépen. Lehetséges például, hogy jelszót vagy PIN-kódot kell beállítania a számítógépen; ebből fakadóan kizárhatja magát a számítógépről, vagy letörölheti az összes adatot a számítógép merevlemezéről, ha túlságosan sokszor adja meg hibásan a jelszót.

Ha kérdése van, lépjen kapcsolatba a rendszergazdával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

### További információ
[Windows-eszköz használata az Intune-nal](using-your-windows-device-with-intune.md)



<!--HONumber=Jun16_HO4-->


