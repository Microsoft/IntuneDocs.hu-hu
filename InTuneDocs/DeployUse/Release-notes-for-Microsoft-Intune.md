---
title: "A Microsoft Intune kibocsátási megjegyzései | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 1906f14568484ebbf23ac7c4350964fb2d5d508f


---

# A Microsoft Intune kibocsátási megjegyzései
A Microsoft Intune egy integrált, felhőalapú ügyfél-felügyeleti megoldás, amely az eszközöket, jelentéseket és a Windows a legújabb verziójára történő frissítést lehetővé tevő licenceket biztosít, valamint megkönnyíti a számítógépek naprakészen tartását és védelmét. Ezenkívül az Intune lehetővé teszi a hálózathoz csatlakoztatott mobileszközök kezelését az Exchange ActiveSync szolgáltatással vagy közvetlenül az Intune-ban. Az alábbi kibocsátási megjegyzések a Microsoft Intune-nal kapcsolatos fontos információkat és ismert problémákat ismertetik.


## Az Android-felhasználók nem tudnak e-mailt küldeni, ha az Exchange Online-hoz feltételes hozzáférést megvalósították

Az eszközükön Samsung Android 5.1.1-es vagy újabb rendszert futtató felhasználók nem tudnak e-mailt küldeni, ha az Exchange Online-hoz feltételes hozzáférés van konfigurálva. A Samsung elismerte, hogy a hiba az Android 5.1.1-es és újabb rendszerek beépített e-mail-ügyfélprogramjában van, és jelenleg vizsgálja a javítás lehetőségét.

**1. megkerülő megoldás:** Javasolja a végfelhasználóknak, hogy használják az Androidhoz készült Outlook alkalmazást.

**2. megkerülő megoldás:** Ahhoz, hogy az érintett felhasználók e-mail-üzeneteket küldhessenek, hajtsa végre ezeket a lépéseket:

1. Az érintett felhasználót vegye fel egy olyan biztonsági csoportba, amely az Exchange Online feltételes hozzáférési szabályzatának „kivétel alá eső csoportok” részébe tartozik.
2. Engedélyezze a felhasználó számára, hogy szinkronizálja az e-mailjeit a beépített e-mail-ügyfélprogrammal.
3. Távolítsa el az érintett felhasználót a kivétel alá eső csoportból, majd győződjön meg arról, hogy a felhasználó már tud e-mailt küldeni.

A Microsoft továbbra is szorosan együttműködik a Samsunggal a javítás vagy a további megkerülő megoldások kidolgozásában.



## Az iOS és az Android rendszer esetében előfordulhat, hogy csoportváltás alkalmával sikertelen lesz az erőforrás-hozzáférési profilok módosítása
**Probléma:** Ha csoportváltás hatására másik e-mail-profil vagy SCEP-erőforrás-hozzáférési profil lép életbe, akkor előfordulhat, hogy a profilok ütköznek, és működésük hibás lesz. Tegyük fel például, hogy van egy e-mail-profilja, amely a helyszíni Exchange-kiszolgálóra mutat, és az „A” csoportot célozza. Létrehoz egy új e-mail-profilt, amely az Exchange Online-ra mutat, és a „B” csoportot célozza. Ha az „A” csoportból a „B” csoportba helyez át felhasználókat, akkor az eszközök megőrzik a helyszíni Exchange e-mail profilt, és megkísérlik a „B” csoportot célzó Exchange Online e-mail-profil telepítését.

Ezen a ponton a következők egyike történik: 
* Ha az „A” és a „B” profil azonos, akkor az eszköz elutasítja a „B” e-mail-profilt, mert a „B” e-mail-profil már tartalmazza az „A” e-mail-profilt.
* Ha az „A” e-mail-profil eltér a „B” e-mail-profiltól, akkor, amint azt a fenti példa is említi, az eszköznek két e-mail-profilja lesz.

**Megjegyzés:** az e-mail-profilok egymástól való megkülönböztetéséhez a rendszer ellenőrzi a felhasználónévhez használt állomásnevet és attribútumot.

Az erőforrás-hozzáférési profilt (az e-mail-profilt) a rendszer egyik esetben sem távolítja el az eszközről, nehogy véletlenül megszűnjön a felhasználó hozzáférése az e-mailhez, vagy törlődjön az ügyfél SCEP-tanúsítványa.

**Megkerülő megoldás:** Nincs.

## Ha olyan Windows 8.1 rendszerű eszközt regisztrál, amelyet proxykiszolgálónak kell hitelesítenie, a regisztrálási folyamat a hiba okának feltüntetése nélkül sikertelen lesz.
**Probléma:** Ha Windows 8.1 rendszerű eszközt regisztrál, és az eszközt proxykiszolgálónak kell hitelesítenie a regisztráció során, a regisztráció sikertelen lesz, ha az eszközön nincsenek gyorsítótárazva a proxykiszolgáló hitelesítő adatait. Ha a proxykiszolgáló hitelesítő adatai nincsenek gyorsítótárazva az eszközön, a regisztrálási folyamatnak meg kell várnia, hogy a felhasználó megadja a hitelesítő adatokat. A proxykiszolgáló hitelesítő adatait kérő felület azonban nem jelenik meg a regisztrálás során. Ennek eredményeként a regisztrációs folyamat során a proxykiszolgáló nem tudja hitelesíteni az eszközt, és a hiba oka nem jelenik meg a felhasználó számára.

**Megkerülő megoldás:** Ha az a hálózat, amelyen regisztrálni kíván egy Windows 8.1 rendszerű eszközt, hitelesített proxykiszolgáló használatát igényli, akkor a proxykiszolgáló hitelesítő adatait az eszköz regisztrálása előtt be kell állítani, és menteni kell. Hitelesítő adatok konfigurálása és mentése a Windows 8.1 rendszerű eszközökön:

1.  A Windows 8.1 rendszerű eszközön nyissa meg az **Internet Explorert**.

2.  Ha a rendszer kéri, adja meg a proxykiszolgáló hitelesítő adatait, majd válassza a **Jegyezze meg a hitelesítő adataimat**lehetőséget.

3.  Regisztrálja az eszközt.

## A Windows Phone 8.1 rendszerű eszközök nem regisztrálhatók a Microsoft Intune-ban, ha az eszközhitelesítés engedélyezve van az AD FS-ben
**Probléma:** A Windows Phone 8.1-eszközök regisztrálása sikertelen lesz, ha az opcionális eszközhitelesítési beállítás engedélyezve van a globális hitelesítési házirend részeként az Active Directory összevonási szolgáltatásokban (AD FS).

**Megkerülő megoldás:** Tiltsa le az eszközhitelesítést az AD FS-kiszolgálón az **Enable device authentication** (Eszközhitelesítés engedélyezése) lehetőség kiválasztásával az **Edit Global Authentication Policy**(Globális hitelesítési házirend szerkesztése) beállításban. További információ: [Hitelesítési házirendek konfigurálása](http://technet.microsoft.com/library/dn486781.aspx)


## A Microsoft Intune App Wrapping Tool for Android nem rendelkezik beépített eltávolítási funkcióval
**Probléma:** A **Microsoft Andorid rendszerhez készült alkalmazásburkoló eszköze** nem tartalmaz olyan beépített funkciót, amellyel eltávolítható.

**Megkerülő megoldás:** Keresse meg az eszköz telepítési helyét, és törölje a könyvtárat. Az alapértelmezett telepítési hely a következő: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. További információk az alkalmazásburkoló eszközről: [Android-alkalmazások előkészítése az alkalmazásburkoló eszközzel való kezeléshez](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## A Távsegítség nem érhető el a Windows 8 vagy Windows 8.1 rendszerű számítógépeken
**Probléma:** Ebben a kiadásban a Távsegítség funkció nem érhető el a Windows 8 vagy Windows 8.1 rendszert futtató számítógépeken.

**Megkerülő megoldás:** Nincs.

## Előfordul, hogy az automatikusan hozzáadott címzettek nem kapják meg a riasztási értesítéseket.
**Probléma:** A riasztási értesítéshez automatikusan hozzáadott címzettek nem mindig kapják meg az értesítést.

**Megkerülő megoldás:** Annak érdekében, hogy a címzettek megkapják az értesítési üzeneteket, manuálisan adja hozzá a címzetteket a riasztási értesítésekhez.

## Nyelvi támogatás az Azure Betekintő portálon
Az Azure Betekintő portál új platformra épül, és a következő nyelveket támogatja: angol, cseh, francia, holland, japán, kínai (egyszerűsített), kínai (hagyományos), koreai, lengyel, magyar, német, olasz, orosz, portugál (brazíliai), portugál (portugáliai), spanyol, svéd, török.

Az Intune felügyeleti konzol és a végfelhasználói mobilélmények az Azure Betekintő portál által támogatott nyelveken kívül a következő nyelveket támogatják: dán, finn, görög, norvég és román.



<!--HONumber=Jun16_HO4-->


