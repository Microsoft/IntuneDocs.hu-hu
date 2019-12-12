---
title:
- CIKK CÍME | SZOLGÁLTATÁS NEVE
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: 0a5e90c6bc6b352f4d7a0fc0ae22c65110563461
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "68354410"
---
# <a name="metadata-and-markdown-template"></a>Metaadat- és markdown-sablon

Ez a docs.ms sablon példákat tartalmaz a markdown szintaxisra, valamint a metaadatok beállítására vonatkozó útmutatást. Az egyes EM próbaadattárak gyökérkönyvtárában érhető el (például: ~/Azure-RMSDocs-pr /template.md), és markdown-fájlként kell olvasni, [a közzétett változatban](https://stage.docs.microsoft.com/en-us/rights-management/template) azonban megtekintheti, hogy a markdown-példák hogyan jelennek meg.

Markdown-fájl létrehozásakor másolja a sablont egy új fájlba, töltse ki a metaadatokat az alábbiakban megadottak szerint, állítsa be a fenti H1 címsort a cikk címére, és törölje a tartalmat. 


## <a name="metadata"></a>Metaadatok 

A teljes metaadatblokk a fentiekben található kötelező és opcionális mezőkre bontva; további részletekért lásd: [OPS metaadatok – áttekintés](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data). Néhány kulcsfontosságú megjegyzés:

- A kettőspont (:) és a metaadatelem értéke között szóköznek **kell** lennie.
- Ha az opcionális metaadatelem nem rendelkezik értékkel, tegye megjegyzésbe az elemet egy # karakterrel (ne hagyja üresen, és ne használja az „na” karakterláncot); ha értéket ad egy korábban megjegyzésbe helyezett elemhez, törölje a # karaktert.
- Az értékben (például a címben) szereplő kettőspontok megtörik a metaadat-elemzőt. Használja helyettük az &#58; HTML-kódot (például: „cím: Azure Rights Management&#58; az alapok | Azure RMS”).
- **title**: Ez a cím jelenik meg a keresőmotorok találatai között. A cím végén egy függőleges vonalnak (|) kell szerepelnie, amelyet a szolgáltatás neve követ (lásd fentebb). A címnek nem kell megegyeznie (és valószínűleg jobb is, ha nem egyezik meg) a H1 címsorban lévő címmel. Nagyjából 65 karakter hosszú legyen (beleértve a | SZOLGÁLTATÁS NEVÉT)
- **author**, **manager**, **reviewer**: Az author mező a szerző **Github-felhasználónevét** tartalmazza, ne pedig az aliasát.  A manager és a reviewer mezőben azonban aliasnak kell szerepelnie. Az ms.reviewer a cikkhez vagy szolgáltatáshoz társított PM nevét adja meg.
- **ms.assetid**: Ez a CAPS-cikk GUID azonosítója. Új Markdown-fájl létrehozásakor szerezze be a [https://www.guidgenerator.com](https://www.guidgenerator.com)GUID azonosítóját. 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: Ezeknek az elemeknek a lehetséges értékei [itt](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default) találhatóak.

## <a name="basic-markdown-and-gfm"></a>Alapvető markdown és GFM

Minden alapvető és Github-flavored markdown támogatva van. Ezekkel kapcsolatos további információért lásd:

- [Alapvető markdown-szintaxis](https://daringfireball.net/projects/markdown/syntax)
- [Github-stílusú markdown (GFM) – dokumentáció](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Címsorok

Első és második szintű címsorokra fent láthatók példák. 

A témakörben **csak egy** első szintű címsor lehet, amely az oldalon belüli címként jelenik meg.  

A második szintű címsorok hozzák létre az oldalon belüli tartalomjegyzéket, amely „A cikk tartalma” részben jelenik meg az oldalon belüli cím alatt.

### <a name="third-level-heading"></a>Harmadik szintű címsor
#### <a name="fourth-level-heading"></a>Negyedik szintű címsor
##### <a name="fifth-level-heading"></a>Ötödik szintű címsor
###### <a name="sixth-level-heading"></a>Hatodik szintű címsor

## <a name="text-styling"></a>Szövegformázás

*Dőlt* 

**Félkövér** 

~~Áthúzott~~



## <a name="links"></a>Links

Az egyazon adattárban lévő markdown-fájlra való hivatkozáshoz használjon [relatív hivatkozásokat](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Például: [Mi az az Azure Rights Management?](./understand-explore/what-is-azure-rights-management.md)

Az egyazon markdown-fájlban lévő címsorra való hivatkozáshoz tekintse meg a közzétett cikk forrását, keresse meg a címsor azonosítóját (például `id="blockquote"`), és a # + azonosító kombináció segítségével hozza létre a hivatkozást (például `#blockquote`).

- Például: [Idézetblokkok](#blockquote)

Az egyazon adattárban lévő címsorra való hivatkozáshoz használjon relatív hivatkozást és hashtaggel történő hivatkozást.

- Például: [az aláírási folyamat műszaki áttekintése](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Külső fájlra hivatkozáshoz használja hivatkozásként a teljes URL-címet.

- Például: [Github](http://www.github.com)

Ha a markdown-fájlban egy URL-cím jelenik meg, akkor az egy kattintható hivatkozássá alakul.

- Példa: http://www.github.com

## <a name="lists"></a>Listák

### <a name="ordered-lists"></a>Rendezett listák

1. Ez 
1. Itt
1. Egy
1. Rendezett
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Rendezett lista egy beágyazott listával

1. Ez
1. pedig
1. egy
1. beágyazott
    1. Josephine Scarlett
    1. Plum professzor
1. rendezett
1. lista


### <a name="unordered-lists"></a>Rendezetlen listák

- Ez
- itt
- egy
- listajeles
- lista


#### <a name="unordered-list-with-an-embedded-lists"></a>Rendezetlen lista beágyazott listákkal

- Ez 
- listajeles 
- lista
  - Patricia Peacock
  - John Green
- tartalmazza  
- más
    1. Mustard ezredes
    1. Mrs. White
- listákat is


## <a name="horizontal-rule"></a>Vízszintes vonal

---

## <a name="tables"></a>A táblázatok

| A táblázatok        | Nagyon           | Hasznosak  |
| ------------- |:-------------:| -----:|
| a 3. oszlop      | jobbra van igazítva | $1600 |
| a 2. oszlop      | középre van igazítva      |   $12 |
| az 1. oszlop alapértelmezés szerint | balra van igazítva     |    $1 |


## <a name="code"></a>Kód

### <a name="codeblock"></a>Kódblokk

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Beágyazott kód

Ez egy példa a következőre: `in-line code`.

## <a name="blockquotes"></a>Idézetblokkok

> Az aszály immár tízmillió éve tartott, és a félelmetes gyíkok uralma már régen véget ért. Itt az Egyenlítőn, azon a kontinensen, amelyet egy nap majd Afrikának neveznek, a túlélésért folyó harc egyre kegyetlenebbé vált, ám a győztes még a láthatáron sem volt. Ezen a sivár, felperzselt vidéken csak az apró termetű, fürge vagy harcias teremtmények maradhattak életben vagy remélhették a túlélést.

## <a name="images"></a>Képek

### <a name="static-image"></a>Statikus kép

![ez az alternatív szöveg](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Csatolt kép

[![alternatív szöveg a hivatkozott képhez](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>Animált gif

![animált gif](./media/hololens.gif)

## <a name="alerts"></a>Alerts

### <a name="note"></a>Megjegyzés

> [!NOTE]
> Ez MEGJEGYZÉS

### <a name="warning"></a>Figyelmeztetés

> [!WARNING]
> Ez FIGYELMEZTETÉS

### <a name="tip"></a>Tipp

> [!TIP]
> Ez TIPP

### <a name="important"></a>Fontos

> [!IMPORTANT]
> Ez FONTOS

## <a name="videos"></a>Videók

### <a name="channel-9"></a>9-es csatorna

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms kiterjesztések

### <a name="button"></a>Gomb

> [!div class="button"]
[gombok hivatkozásai](/rights-management)

### <a name="selector"></a>Szelektor

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>Lépésről lépésre

>[!div class="step-by-step"]
[Előző](https://www.example.com)
[Következő](https://www.example.com)
