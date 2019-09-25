---
title: Android-alkalmazások alkalmazásvédelmi szabályzatokkal
description: Ez a témakör azt ismerteti, hogy milyen hatással vannak az alkalmazásokra az alkalmazásvédelmi szabályzatok.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7e4a1081c76e1d41b84a7fadc84e93a221007c4
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "71238428"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Ez a témakör az alkalmazásvédelmi szabályzatokkal védett alkalmazások felhasználói élményét ismerteti. Az alkalmazásvédelmi szabályzatokat csak akkor alkalmazza a rendszer, amikor az alkalmazásokat munkahelyi környezetben használják: például amikor egy munkahelyi fiókkal fér hozzá az alkalmazásokhoz, vagy a vállalata a OneDrive vállalati verzióban tárolt fájlokhoz fér hozzá.

## <a name="access-apps"></a>Alkalmazások elérése

Androidos eszközökön minden alkalmazásvédelmi szabályzathoz rendelt alkalmazás esetén szükség van a Céges portál alkalmazásra.

Azokon az eszközökön, amelyek nincsenek regisztrálva az Intune-ban, az eszközre telepíteni kell a Munkahelyi portál alkalmazást. A felhasználónak azonban nem kell elindítania a Céges portál alkalmazást, illetve nem kell bejelentkeznie az alkalmazásba ahhoz, hogy használhassa az alkalmazásvédelmi szabályzatok által felügyelt alkalmazásokat.

A Munkahelyi portál alkalmazás biztonságos helyet tesz elérhetővé az Intune számára, ahol a szolgáltatás megoszthatja az adatokat. A Céges portál alkalmazás ezért az összes alkalmazásvédelmi szabályzat alá vont alkalmazás esetében követelmény, még akkor is, ha maga az eszköz nincs regisztrálva az Intune-ban.


## <a name="use-apps-with-multi-identity-support"></a>A többszörös identitást támogató alkalmazások használata

Az alkalmazásvédelmi szabályzatokat a rendszer csak a munkahelyi használat esetén alkalmazza. Ez azt jelenti, hogy az alkalmazás eltérő módon működhet, attól függően, hogy munkahelyi vagy személyes célokra használják.

Például a munkahelyi adatok elérésekor a felhasználónak PIN-kódot kell megadnia. Az **Outlook alkalmazás** esetében a felhasználónak az alkalmazás indításakor kell megadnia a PIN-kódot. A **OneDrive alkalmazás** esetében a felhasználónak a munkahelyi fiók beírásakor kell megadnia a PIN-kódot. A Microsoft **Word**, a **PowerPoint** és az **Excel** esetében a felhasználónak akkor kell megadnia a PIN-kódot, ha a vállalat OneDrive vállalati helyén tárolt dokumentumhoz szeretne hozzáférni.

## <a name="manage-user-accounts-on-the-device"></a>Felhasználói fiókok kezelése az eszközön

A többszörös identitású alkalmazások lehetővé teszik, hogy a felhasználók több fiókot is hozzáadjanak.  Az Intune APP csak egy felügyelt fiókot támogat.  Az Intune APP a felügyelt fiókok számát azonban nem korlátozza.

Ha felügyelt fiók van jelen az alkalmazásban:
* Ha a felhasználó egy második felügyelt fiókot próbál hozzáadni, akkor meg kell adnia, hogy mely felügyelt fiókot szeretné használni.  A másik fiók el lesz távolítva.
* Ha a rendszergazda egy második meglévő fiókhoz ad hozzá szabályzatot, a felhasználónak ki kell választania, hogy mely felügyelt fiókot szeretné használni.  A másik fiók el lesz távolítva.

A következő példák részletesen bemutatják, hogy a rendszer hogyan kezeli a további felhasználói fiókokat.

Az A felhasználó két vállalatnak dolgozik: az **X vállalatnak** és az **Y vállalatnak**. Az A felhasználó munkahelyi fiókkal rendelkezik mindként vállalatnál, és mindkettő az Intune-t használja alkalmazásvédelmi szabályzatok telepítéséhez. Az **X vállalat** telepít elsőként alkalmazásvédelmi szabályzatokat, **megelőzve** az **Y vállalatot**. Az **X vállalathoz** tartozó fiók megkapja az alkalmazásvédelmi szabályzatot, de az Y vállalat fiókja nem. Ha azt szeretné, hogy az alkalmazásvédelmi szabályzatok az Y vállalathoz tartozó fiókot kezeljék, akkor el kell távolítania az X vállalathoz tartozó fiókot, és hozzá kell adnia az Y vállalathoz tartozó fiókot.
### <a name="add-a-second-account"></a>Második fiók hozzáadása
#### <a name="android"></a>Android
Android-eszközön blokkoló üzenet jelenhet meg, amely ismerteti a meglévő fiók eltávolításának és új fiók felvételének lépéseit.  A meglévő fiók eltávolításához válassza a **Beállítások &gt;Általános &gt; Alkalmazáskezelő &gt;Munkahelyi portál** lehetőséget, majd itt az **Adatok törlése** lehetőséget.

![Képernyőfelvétel a hibaüzenetről és a fiók eltávolítására vonatkozó utasításokról](./media/Android_SwitchUser.png)

## <a name="view-media-files-with-the-azure-information-protection-app"></a>Médiafájlok megtekintése az Azure Information Protection alkalmazással
A vállalati AV-, PDF- és képfájlok Android-eszközökön való megtekintéséhez használja az [Azure Information Protection alkalmazást](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (amelyet korábban Rights Management-megosztóalkalmazásnak neveztünk).

Ezt az alkalmazást a Google Play Áruházból töltheti le.  

A rendszer a következő fájltípusokat támogatja:

* **Hang** AAC LC, it-AACv1 (AAC +), AACv2 (bővített AAC +), AAC-címkézés (bővített, alacsony késleltetésű AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, OGG Vorbis, PCM/WAVE
* **Videóinak** H. 263, H. 264 AVC, MPEG-4 SP, VP8
* **Kép:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg
* **Dokumentumok** PDF PPDF


|**pfile**|
|----|
|A pfile egy általános „burkoló” formátum a védett fájlokhoz, amelyben a titkosított tartalom és az Azure Information Protection-licencek is megtalálhatók. Ez bármilyen fájltípus védelmére használható.|

## <a name="next-steps"></a>További lépések
[Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](end-user-mam-apps-ios.md)
