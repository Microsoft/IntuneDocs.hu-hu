---
title: "Csomagcsalád nevének (PFN) megkeresése az alkalmazásonkénti VPN-ekhez | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager:
- ALIAS
ms.date: 05/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
translationtype: Human Translation
ms.sourcegitcommit: e32cbcd54220cf36d6770ee16897d27e1d2d71db
ms.openlocfilehash: 21bc0bcaf64cf67eea2ca30b933c314c4c3e6dae


---

# Csomagcsalád nevének (PFN) megkeresése az alkalmazásonkénti VPN-ekhez

Ahhoz, hogy egy alkalmazásonkénti VPN-t konfigurálni tudjon, két lehetősége is van a PFN megkeresésére.

## Egy Windows 10 rendszerű számítógépre telepített alkalmazás PFN-jének megkeresése 

Ha már telepítve van egy Windows 10 rendszerű számítógépre az az alkalmazás, amellyel dolgozik, a [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell-parancsmag használatával is beolvashatja a PFN-t.

A Get-AppxPackage szintaxisa a következő:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> Megjegyzés: Előfordulhat, hogy a PFN lekéréséhez rendszergazdaként kell futtatnia a PowerShellt.

Ha például a számítógépre telepített összes univerzális alkalmazásra vonatkozó adatot szeretné lekérni, használja a `Get-AppxPackage` parancsot.

Ha olyan alkalmazás adatait szeretné lekérni, amelynek tudja a nevét vagy a név egy részét, használja a `Get-AppxPackage *<app_name>` parancsot. Felhívjuk figyelemét a helyettesítő karakter használatára. Ez különösen akkor hasznos, ha nem tudja biztosan az alkalmazás teljes nevét. A OneNote adatainak lekéréséhez például használja a `Get-AppxPackage *OneNote` parancsot.


A OneNote-ra vonatkozóan lekért adatok a következők:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## A PFN megkeresése, ha az alkalmazás nincs telepítve a számítógépre

1.  Nyissa meg a https://www.microsoft.com/hu-hu/store/apps webhelyet.
2.  Írja be az alkalmazás nevét a keresősávba. A jelen példában keressen rá a OneNote-ra.
3.  Kattintson az alkalmazásra mutató hivatkozásra. Figyelje meg, hogy az elért URL-cím végén egy több betűből álló betűsor található. A példánkban az URL-cím a következőképpen néz ki:
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Egy másik lapon illessze be a következő URL-t `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, majd cserélje az `<app id>` azonosítót a https://www.microsoft.com/hu-hu/store/apps webhelyről származó alkalmazásazonosítóra – vagyis a 3. lépésben elért URL-cím végén található betűsorra. Ebben a példában, a OneNote esetében a következő URL-t kell beillesztenie: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Az Edge böngészőben megjelennek a kívánt adatok; az Internet Explorerben kattintson a **Megnyitás** parancsra az adatok megtekintéséhez. A PFN értéke az első sorban található. A jelen példában az eredmények a következők:
 

`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`




<!--HONumber=Jun16_HO4-->


