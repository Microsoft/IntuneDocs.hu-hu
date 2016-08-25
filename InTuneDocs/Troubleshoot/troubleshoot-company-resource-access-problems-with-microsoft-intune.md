---
title: "Munkahelyi erőforrás-hozzáférési problémák megoldása | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c22ddd554928b394e14742b8ba7d583d390d1c44
ms.openlocfilehash: ed14e92d48a2604d16ceee8b844ae5cc0c45f051


---

# Munkahelyi erőforrás-hozzáférési problémák megoldása a Microsoft Intune-nal
A témakörben található információkkal háríthatja el a problémákat, amikor egy Microsoft Intune-művelet hibakódot ad vissza.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben talál további részleteket a segítségkéréshez.

## Az MDM által felügyelt Windows-eszközök állapotkódjai

|Állapotkód|Hibaüzenet|Mi a teendő|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Telepítés folyamatban||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|Tartalomra vár||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|Tartalom lekérése|Valószínű ok: A 30-as feladatállapot azt jelzi, hogy egy alkalmazás felhasználói letöltése meghiúsult.<br /><br />Ennek valószínű okai a következők lehetnek:<br /><br />Az eszköz internetkapcsolata megszakadt a letöltési folyamat során.<br /><br />Lehet, hogy a regisztráció során az eszköz számára kiadott tanúsítvány lejárt.<br /><br />Kezelés:<br /><br />Indítsa el a Vállalati alkalmazások alkalmazást a Vezérlőpultról az eszközön annak ellenőrzéséhez, hogy az eszköz tanúsítványa nem járt-e le. Ha lejárt, akkor újra regisztrálnia kell az eszközt.<br /><br />Ellenőrizze, hogy az eszköz csatlakozik-e az internethez, és próbálja meg ismét igényelni az alkalmazást.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|A tartalom letöltése befejeződött||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Telepítés folyamatban||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Telepítés ​Hiba történt|Az alkalmazás telepítése sikertelen a letöltés után.<br /><br />Az alkalmazás aláírásához használt kódaláírási tanúsítvány nincs jelen az eszközön.<br /><br />Nincs az eszközre telepítve egy keretrendszerbeli függőség, amely szükséges az alkalmazás működéséhez.<br /><br />Ellenőrizze, hogy az alkalmazás aláírásához használt kódaláírási tanúsítvány megtalálható-e az eszközön, és kérjen megerősítést a rendszergazdától, hogy ez a tanúsítvány érvényes az összes regisztrált vállalati Windows RT-eszközre.<br /><br />Ha a telepítési hibát hiányzó keretrendszerbeli függőség okozta, a rendszergazdának újra közzé kell tennie az alkalmazást, a keretrendszert az alkalmazáscsomagba foglalva.<br /><br />A letöltött alkalmazáscsomag nem érvényes csomag. Lehet, hogy sérült, vagy nem kompatibilis az eszközön lévő operációs rendszer verziójával.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|A telepítés sikeres||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Eltávolítás folyamatban||
|90 (APP_CI_ENFORCEMENT_ERROR)|Eltávolítási hiba történt||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Az eltávolítás sikeres||
|110 (APP_CI_ENFORCEMENT_ERROR)|A tartalomkivonat nem egyezik||
|120 (APP_CI_ENFORCEMENT_ERROR)|Az SLK / közvetlen telepítés nem engedélyezett||
|130 (APP_CI_ENFORCEMENT_ERROR)|Az MSADP licenc telepítése meghiúsult||
|Nincs állapot (APP_CI_ENFORCEMENT_UNKNOWN)|nem áll rendelkezésre|Az állapot jelenleg ismeretlen.|

## Vállalati erőforrások elérése (gyakori hibák)

|Állapotkód|Hexadecimális hibakód|Hibaüzenet|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|Nem található az MDM CRP-kérés|
|-2016281102|0x87D1FDF2|Nem található az NDES URL-címe|
|-2016281103|0x87D1FDF1|Nem találhatóak az MDM CRP-tanúsítvány adatai|
|-2016281104|0x87D1FDF0|Nem találhatóak az MDM CI-tanúsítvány adatai|
|-2016281105|0x87D1FDEF|A szabály értékelése sikertelen|
|-2016281106|0x87D1FDEE|Nem használható, mert ütközésfeloldás közben elveszett|
|-2016281107|0x87D1FDED|Nem támogatott beállításfelderítési forrás|
|-2016281108|0x87D1FDEC|A hivatkozott beállítás nem található a CI-ben|
|-2016281109|0x87D1FDEB|Az adattípus átalakítása sikertelen|
|-2016281110|0x87D1FDEA|Érvénytelen paraméter a CIM-beállításhoz|
|-2016281111|0x87D1FDE9|Nem alkalmazható erre az eszközre|
|-2016281112|0x87D1FDE8|A javítás sikertelen|
|-2016330905|0x87D13B67|Az alkalmazás állapota ismeretlen|
|-2016330906|0x87D13B66|Az alkalmazás felügyelt alkalmazás, de a felhasználó eltávolította|
|-2016330907|0x87D13B65|Az eszköz az érvényesítési kódot váltja be|
|-2016330908|0x87D13B64|Az alkalmazás telepítése sikertelen|
|-2016330909|0x87D13B63|A felhasználó visszautasította az alkalmazás frissítésére vonatkozó ajánlatot|
|-2016330910|0x87D13B62|A felhasználó visszautasította az alkalmazás telepítésére vonatkozó ajánlatot|
|-2016330911|0x87D13B61|A felhasználó telepítette az alkalmazást, mielőtt a felügyelt alkalmazástelepítés elindulhatott volna|
|-2016330912|0x87D13B60|Az alkalmazás telepítésre van ütemezve, de a tranzakció elvégzéséhez érvényesítési kódra van szüksége|
|-2016341109|0x87D1138B|Az iOS-eszköz hibát adott vissza|
|-2016341110|0x87D1138A|Az iOS-eszköz helytelen formátum miatt elutasította a parancsot|
|-2016341111|0x87D11389|Az iOS-eszköz váratlan üresjárati állapotot adott vissza|
|-2016341112|0x87D11388|Az iOS-eszköz jelenleg elfoglalt|

## iOS-eszközök által visszaadott hibák

|Állapotkód|Hexadecimális hibakód|Hibaüzenet|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Belső hiba|
|-2016299112|0x87D1B798|Belső hiba|
|-2016300111|0x87D1B3B1|36001:(belső hiba)|
|-2016300112|0x87D1B3B0|36000:A mobiltelefon már konfigurálva van|
|-2016301110|0x87D1AFCA|35002:Több betűtípus található a hasznos adatban|
|-2016301111|0x87D1AFC9|35001:A betűtípus-telepítés sikertelen|
|-2016301112|0x87D1AFC8|35000:Érvénytelen betűtípusadatok|
|-2016302109|0x87D1ABE3|34003:A Kerberos egyszerű neve érvénytelen|
|-2016302110|0x87D1ABE2|34002:A Kerberos egyszerű neve hiányzik|
|-2016302111|0x87D1ABE1|34001:Érvénytelen az URL-egyeztetési minta|
|-2016302112|0x87D1ABE0|34000:Érvénytelen alkalmazásazonosító-egyeztetési minta|
|-2016304112|0x87D1A410|32000:Túl sok alkalmazás|
|-2016305111|0x87D1A029|31001:A beállítások nem alkalmazhatók|
|-2016305112|0x87D1A028|31000:A hitelesítő adat nem alkalmazható|
|-2016306111|0x87D19C41|30001:Időtúllépés|
|-2016306112|0x87D19C40|30000:A hitelesítés sikertelen|
|-2016307109|0x87D1985B|29003:Helytelen tanúsítványadatok|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000:Az eszköz nincs felügyelve|
|-2016308110|0x87D19472|28002:Nem állítható be háttérkép|
|-2016308111|0x87D19471|28001:Helytelen háttérkép|
|-2016308112|0x87D19470|28000:Ismeretlen elem|
|-2016310111|0x87D18CA1|26001:A fájlszintű titkosítás nem támogatott|
|-2016310112|0x87D18CA0|26000:A blokkszintű titkosítás nem támogatott|
|-2016311110|0x87D188BA|25002:Nem távolítható el|
|-2016311111|0x87D188B9|25001:Nem telepíthető|
|-2016311112|0x87D188B8|25000:Helytelen profil|
|-2016312109|0x87D184D3|24003:Helytelen végső profil|
|-2016312110|0x87D184D2|24002:Helytelen identitásra vonatkozó hasznos adat|
|-2016312111|0x87D184D1|24001:Nem írható alá az attribútumszótár|
|-2016312112|0x87D184D0|24000:Nem hozható létre attribútumszótár|
|-2016313110|0x87D180EA|23002:Érvénytelen kiszolgálótanúsítvány|
|-2016313111|0x87D180E9|23001:Helytelen kiszolgálóválasz|
|-2016313112|0x87D180E8|23000:Helytelen identitás|
|-2016314099|0x87D17D0D|22013:Érvénytelen PKI műveleti válasz|
|-2016314100|0x87D17D0C|22012:Nem tárolható hitelesítésszolgáltatói tanúsítvány|
|-2016314101|0x87D17D0B|22011:Nem hozható létre CSR|
|-2016314102|0x87D17D0A|22010:Nem tárolható ideiglenes identitás|
|-2016314103|0x87D17D09|22009:Nem hozható létre ideiglenes identitás|
|-2016314104|0x87D17D08|22008:Nem hozható létre identitás|
|-2016314105|0x87D17D07|22007:Érvénytelen aláírt tanúsítvány|
|-2016314106|0x87D17D06|22006:Nincs elegendő CA-kapacitás|
|-2016314107|0x87D17D05|22005:Hálózati hiba|
|-2016314108|0x87D17D04|22004:Nem támogatott tanúsítványkonfiguráció|
|-2016314109|0x87D17D03|22003:Érvénytelen a regisztrációszolgáltatótól érkezett válasz|
|-2016314110|0x87D17D02|22002:Érvénytelen a hitelesítésszolgáltatótól érkezett válasz|
|-2016314111|0x87D17D01|22001:Nem hozható létre kulcspár|
|-2016314112|0x87D17D00|22000: Érvénytelen kulcshasználat|
|-2016315105|0x87D1791F|21007:A fiók nem ellenőrizhető|
|-2016315106|0x87D1791E|21006:Nem fejthető vissza a tanúsítvány|
|-2016315107|0x87D1791D|21005:A fiók nem egyedi|
|-2016315108|0x87D1791C|21004:A fiók nem hozható létre|
|-2016315109|0x87D1791B|21003:Nincs állomásnév|
|-2016315110|0x87D1791A|21002:Nem tartható be a kiszolgáló titkosítási házirendje|
|-2016315111|0x87D17919|21001:Nem tartható be a kiszolgáló házirendje|
|-2016315112|0x87D17918|21000:Nem kérhető le a házirend a kiszolgálóról|
|-2016316110|0x87D17532|20002:A fiók nem egyedi|
|-2016316111|0x87D17531|20001:Nincs állomásnév|
|-2016316112|0x87D17530|20000:A fiók nem hozható létre|
|-2016317110|0x87D1714A|19002:A fiók nem egyedi|
|-2016317111|0x87D17149|19001:Nincs állomásnév|
|-2016317112|0x87D17148|19000:A fiók nem hozható létre|
|-2016318110|0x87D16D62|18002:Érvénytelen hitelesítő adatok|
|-2016318111|0x87D16D61|18001:Az állomás nem érhető el|
|-2016318112|0x87D16D60|18000:Ismeretlen hiba|
|-2016319110|0x87D1697A|17002:A fiók nem egyedi|
|-2016319111|0x87D16979|17001:Nincs állomásnév|
|-2016319112|0x87D16978|17000:A fiók nem hozható létre|
|-2016320110|0x87D16592|16002:A fiók nem egyedi|
|-2016320111|0x87D16591|16001:Nincs állomásnév|
|-2016320112|0x87D16590|16000:Nem hozható létre előfizetés|
|-2016321109|0x87D161AB|15003:Érvénytelen tanúsítvány|
|-2016321110|0x87D161AA|15002:Nem zárolható a hálózati konfiguráció|
|-2016321111|0x87D161A9|15001:Nem távolítható el a VPN|
|-2016321112|0x87D161A8|15000:Nem telepíthető a VPN|
|-2016322110|0x87D15DC2|14002:A felhőkonfiguráció már létezik|
|-2016322111|0x87D15DC1|14001:Eszköz zárolva|
|-2016322112|0x87D15DC0|14000:Érvénytelen mező|
|-2016323107|0x87D159DD|13005:Nem állítható be proxy|
|-2016323108|0x87D159DC|13004:Nem állítható be EAP|
|-2016323109|0x87D159DB|13003:Nem hozható létre WiFi-konfiguráció|
|-2016323110|0x87D159DA|13002:Jelszóra van szükség|
|-2016323111|0x87D159D9|13001:Felhasználónévre van szükség|
|-2016323112|0x87D159D8|13000:Nem telepíthető|
|-2016324070|0x87D1561A|12042:Ismeretlen területibeállítás-kód|
|-2016324071|0x87D15619|12041:Ismeretlen nyelvi kód|
|-2016324072|0x87D15618|12040:Be kell jelentkezni az iTunes áruházba|
|-2016324073|0x87D15617|12039:(nincs használatban)|
|-2016324074|0x87D15616|12038:Az alkalmazás nincs felügyelve|
|-2016324075|0x87D15615|12037:Érvénytelen érvényesítési kód|
|-2016324076|0x87D15614|12036:Nem távolítható el az alkalmazás a jelenlegi állapotban|
|-2016324077|0x87D15613|12035:Az alkalmazás nem vásárolható meg|
|-2016324078|0x87D15612|12034:Az URL nem HTTPS|
|-2016324079|0x87D15611|12033:Érvénytelen jegyzék|
|-2016324080|0x87D15610|12032:Túl sok alkalmazás a jegyzékben|
|-2016324081|0x87D1560F|12031:Az alkalmazás telepítése le van tiltva|
|-2016324082|0x87D1560E|12030:Érvénytelen URL|
|-2016324083|0x87D1560D|12029:Az alkalmazás nincs felügyelve|
|-2016324084|0x87D1560C|12028:Nem várakozik beváltásra|
|-2016324085|0x87D1560B|12027:Nem alkalmazás|
|-2016324086|0x87D1560A|12026:Az alkalmazás már sorban áll|
|-2016324087|0x87D15609|12025:Az alkalmazás már telepítve van|
|-2016324088|0x87D15608|12024:Az alkalmazás jegyzéke nem érvényesíthető|
|-2016324089|0x87D15607|12023:Az alkalmazás azonosítója nem érvényesíthető|
|-2016324090|0x87D15606|12022:Érvénytelen témakör|
|-2016324091|0x87D15605|12021:Érvénytelen kérelemtípus|
|-2016324092|0x87D15604|12020:A kiszolgáló nem jogosította fel|
|-2016324093|0x87D15603|12019:Nem másolható a letéti titkos kulcs|
|-2016324094|0x87D15602|12018:A kulcsletét adatai nem másolhatók|
|-2016324095|0x87D15601|12017:Nem hozható létre kulcsletét|
|-2016324096|0x87D15600|12016:Hiányzó identitás|
|-2016324097|0x87D155FF|12015:Nem szerezhető be leküldéses token|
|-2016324098|0x87D155FE|12014:A létesítési profil nincs felügyelve|
|-2016324099|0x87D155FD|12013:Nem felügyelt profil|
|-2016324100|0x87D155FC|12012:A csere MDM nem egyezik|
|-2016324101|0x87D155FB|12011:Érvénytelen MDM-konfiguráció|
|-2016324102|0x87D155FA|12010:Belső konzisztenciahiba|
|-2016324103|0x87D155F9|12009:Érvénytelen csereprofil|
|-2016324104|0x87D155F8|12008:Rossz formátumú kérelem|
|-2016324105|0x87D155F7|12007:Nem engedélyezett|
|-2016324106|0x87D155F6|12006:Az átirányítás elutasítva|
|-2016324107|0x87D155F5|12005:Nem található tanúsítvány|
|-2016324108|0x87D155F4|12004:Érvénytelen leküldéses tanúsítvány|
|-2016324109|0x87D155F3|12003:Érvénytelen válasz a kérdésre|
|-2016324110|0x87D155F2|12002:Nem adható be|
|-2016324111|0x87D155F1|12001:Több MDM-példány található|
|-2016324112|0x87D155F0|12000:Érvénytelen hozzáférési jogosultságok|
|-2016325111|0x87D15209|11001:Már telepítve van egyéni APN|
|-2016325112|0x87D15208|11000:Nem telepíthető az APN|
|-2016326111|0x87D14E21|10001:Érvénytelen aláíró|
|-2016326112|0x87D14E20|10000:Nem telepíthetők alapértelmezett beállítások|
|-2016327106|0x87D14A3E|9006:A tanúsítvány nem identitás|
|-2016327107|0x87D14A3D|9005:A tanúsítvány helytelen formátumú|
|-2016327108|0x87D14A3C|9004:Nem tárolható a főtanúsítvány|
|-2016327109|0x87D14A3B|9003:Nem tárolhatók WAPI-adatok|
|-2016327110|0x87D14A3A|9002:Nem tárolható a tanúsítvány|
|-2016327111|0x87D14A39|9001:Túl sok tanúsítvány található a hasznos adatok között|
|-2016327112|0x87D14A38|9000:Érvénytelen jelszó|
|-2016328112|0x87D14650|8000:Nem telepíthető a webklip|
|-2016329105|0x87D1426F|7007:Az SMTP-fiók helytelenül van konfigurálva|
|-2016329106|0x87D1426E|7006:A POP-fiók helytelenül van konfigurálva|
|-2016329107|0x87D1426D|7005:Az IMAP-fiók helytelenül van konfigurálva|
|-2016329108|0x87D1426C|7004:Az SMIME-tanúsítvány helytelen|
|-2016329109|0x87D1426B|7003:Az SMIME-tanúsítvány nem található|
|-2016329110|0x87D1426A|7002:Ismeretlen hiba történt az érvényesítés során|
|-2016329111|0x87D14269|7001:Érvénytelen hitelesítő adatok|
|-2016329112|0x87D14268|7000:Az állomás nem érhető el|
|-2016330110|0x87D13E82|6002:Nem hozható létre a lekérdezés|
|-2016330111|0x87D13E81|6001:Üres karakterlánc|
|-2016330112|0x87D13E80|6000:Hiba a kulcskarikarendszerben|
|-2016331097|0x87D13AA7|5015:Nem állítható be türelmi időszak|
|-2016331098|0x87D13AA6|5014:Nem állítható be PIN-kód|
|-2016331099|0x87D13AA5|5013:A PIN-kód nem törölhető|
|-2016331100|0x87D13AA4|5012:(nincs használatban)|
|-2016331101||5011:Hibás PIN-kód|
|-2016331102||5010:Eszköz zárolva|
|-2016331103|0x87D13AA4|5009:(nincs használatban)|
|-2016331104|0x87D13AA0|5008:A PIN-kód túl friss|
|-2016331105|0x87D13A9F|5007:A PIN-kód lejárt|
|-2016331106|0x87D13AA3|5006:A PIN-kódnak betűkből kell állnia|
|-2016331107|0x87D13A9D|5005:A PIN-kódnak számjegyekből kell állnia|
|-2016331108|0x87D13A9C|5004:A PIN-kód növekvő/csökkenő karaktereket tartalmaz|
|-2016331109|0x87D13A9B|5003:A PIN-kód ismétlődő karaktereket tartalmaz|
|-2016331110|0x87D13A9A|5002:Túl kevés az összetett karakter|
|-2016331111|0x87D13A99|5001:Túl kevés az egyedi karakter|
|-2016331112|0x87D13A98|5000:A PIN-kód túl rövid|
|-2016332093|0x87D136C3|4019:Több alkalmazászárolási hasznos adat található|
|-2016332094|0x87D136C2|4018:Több APN-re vagy mobileszközre vonatkozó hasznos adat található|
|-2016332095|0x87D136C1|4017:Több globális HTTP-proxy hasznos adat található|
|-2016332096|0x87D136C0|4016:(Belső hiba)|
|-2016332097|0x87D136BF|4015:A csereprofil nem tartalmaz az MDM-re vonatkozó hasznos adatot|
|-2016332098|0x87D136BE|4014:Nem érhető el az eszközidentitás|
|-2016332099|0x87D136BD|4013:A frissítés sikertelen|
|-2016332100|0x87D136BC|4012:A profil nem frissíthető|
|-2016332101|0x87D136BB|4011:A végső profil nem konfigurációs profil|
|-2016332102|0x87D136BA|4010:A frissített profil azonosítója nem ugyanaz|
|-2016332103|0x87D136B9|4009:Eszköz zárolva|
|-2016332104|0x87D136B8|4008:Nem egyező tanúsítványok|
|-2016332105|0x87D136B7|4007:Ismeretlen fájlformátum|
|-2016332106|0x87D136B6|4006:A profil eltávolításának dátuma a múltban van|
|-2016332107|0x87D136B5|4005:A PIN-kód nem felel meg|
|-2016332108|0x87D136B4|4004:A felhasználó megszakította a telepítést|
|-2016332109|0x87D136B3|4003:A profil nincs a telepítési várólistán|
|-2016332110|0x87D136B2|4002:Ismétlődő UUID|
|-2016332111|0x87D136B1|4001:Telepítési hiba|
|-2016332112|0x87D136B0|4000:A profil nem elemezhető|
|-2016333111|0x87D132C9|3001:Inkonzisztens érték-összehasonlítási logika (belső hiba)|
|-2016333112|0x87D132C8|3000:Inkonzisztens korlátozási logika (belső hiba)|
|-2016334108|0x87D12EE4|2004:Nem támogatott mezőérték|
|-2016334109|0x87D12EE3|2003:Helytelen adattípus a mezőben|
|-2016334110|0x87D12EE2|2002:Hiányzik egy kötelező mező|
|-2016334111|0x87D12EE1|2001:Nem támogatott a hasznos adat verziója|
|-2016334112|0x87D12EE0|2000:Helytelen formátumú hasznos adat|
|-2016335102|0x87D12B02|1010:Nem támogatott mezőérték|
|-2016335103|0x87D12B01|1009:Profiltelepítési hiba|
|-2016335104|0x87D12B00|1008:Nem egyediek a hasznos adatok azonosítói|
|-2016335105|0x87D12AFF|1007:Nem egyedi UUID-k|
|-2016335106|0x87D12AFE|1006:Nem fejthető vissza|
|-2016335107|0x87D12AFD|1005:Üres profil|
|-2016335108|0x87D12AFC|1004:Helytelen aláírás|
|-2016335109|0x87D12AFB|1003:Helytelen adattípus a mezőben|
|-2016335110|0x87D12AFA|1002:Hiányzik egy kötelező mező|
|-2016335111|0x87D12AF9|1001:Nem támogatott profilverzió|
|-2016335112|0x87D12AF8|1000:Hibás formátumú profil|

## OMA-válaszkódok

|Állapotkód|Hexadecimális hibakód|Hibaüzenet|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): A tanúsítványhoz való hozzáférés megtagadva|
|-2016344009|0x87D10837|(1403): A tanúsítvány nem található|
|-2016344010|0x87D10836|DCMO(1402): A művelet meghiúsult|
|-2016344011|0x87D10835|DCMO(1401): A felhasználó nem fogadta el a műveletet, amikor a program erre rákérdezett|
|-2016344012|0x87D10834|DCMO(1400): Ügyfélhiba|
|-2016344108|0x87D107D4|DCMO(1204): Az eszközképesség le van tiltva, és a felhasználó újra engedélyezheti|
|-2016344109|0x87D107D3|DCMO(1203): Az eszközképesség le van tiltva, és a felhasználó nem engedélyezheti újra|
|-2016344110|0x87D107D2|DCMO(1202): Az engedélyezési művelet sikeresen végbement, de az eszközképesség jelenleg le van választva|
|-2016344111|0xF3FB4D95|DCMO(1201): Az engedélyezési művelet sikeresen végbement, és az eszközképesség jelenleg csatlakoztatva van|
|-2016344112|0x87D107D0|DCMO(1200): A művelet sikeresen végbement|
|-2016345595|0x87D10205|Syncml(517): Egy atomi parancsra adott válasz túl nagy volt ahhoz, hogy elférjen egyetlen üzenetben.|
|-2016345596|0x87D10204|Syncml(516): A parancs egy atomi elemen belül volt, és az atomi elem végrehajtása nem sikerült. A parancs visszaállítása sikertelen.|
|-2016345598|0x87D10202|Syncml(514): A SyncML parancs nem fejeződött be sikeresen, mert a műveletet már a parancs feldolgozása előtt megszakították.|
|-2016345599|0x87D10201|Syncml(513): A címzett nem támogatja vagy elutasítja a SyncML szinkronizálási protokoll megadott verzióját, amelyet a kérés SyncML-üzenetében használtak.|
|-2016345600|0x87D10200|Syncml(512): Alkalmazáshiba történt a szinkronizálási munkamenetben.|
|-2016345601|0x87D101FF|Syncml(511): Súlyos hiba történt a kiszolgálón a kérés feldolgozása közben.|
|-2016345602|0x87D101FE|Syncml(510): Hiba történt a kérés feldolgozása során. A hiba a címzett adattár hibájára vezethető vissza.|
|-2016345603|0x87D101FD|Syncml(509): Jövőbeli használatra fenntartva.|
|-2016345604|0x87D101FC|Syncml(508): Olyan hiba történt, amely az ügyfél és a kiszolgáló jelenlegi szinkronizálási állapotának frissítését teszi szükségessé.|
|-2016345605|0x87D101FB|Syncml(507): A hiba miatt minden atomi elemtípuson belüli SyncML-parancs meghiúsul.|
|-2016345606|0x87D101FA|Syncml(506): Alkalmazáshiba történt a kérés feldolgozása során.|
|-2016345607|0x87D101F9|Syncml(505): A címzett nem támogatja vagy elutasítja a SyncML DTD megadott verzióját, amelyet a kérés SyncML-üzenetében használtak.|
|-2016345608|=0x87D101F8|Syncml(504): A címzett, miközben átjáróként vagy proxyként működött, nem kapott időben választ az URI (pl. HTTP, FTP, LDAP) által meghatározott felsőbb rétegbeli címzettől, illetve valamely egyéb címzettől (pl. DNS), amelyet a kérés teljesítéséhez el kellett érnie.|
|-2016345609|0x87D101F7|Syncml(503): A címzett jelenleg nem tudja kezelni a kérést, mert átmenetileg túl van terhelve vagy karbantartást végeznek rajta.|
|-2016345610|0x87D101F6|Syncml(502): A címzett, miközben átjáróként vagy proxyként működött, érvénytelen választ kapott a felsőbb rétegbeli címzettől, amelyhez a kérés teljesítésére tett kísérlet során kapcsolódott.|
|-2016345611|0x87D101F5|Syncml(501): A címzett nem támogatja a kérés teljesítéséhez szükséges parancsot.|
|-2016345612|0x87D101F4|Syncml(500): A címzett nem várt állapotot észlelt, amely megakadályozta a kérés teljesítését|
|-2016345684|0x87D101AC|Syncml(428): Az áthelyezés nem sikerült|
|-2016345685|0x87D101AB|Syncml(427): A szülő nem törölhető, mert gyermekeket tartalmaz.|
|-2016345686|0x87D101AA|Syncml(426): A részleges elem visszautasítva.|
|-2016345687|0x87D101A9|Syncml(425): A kért parancs meghiúsult, mert a küldő nem rendelkezik megfelelő hozzáférés-vezérlési engedélyekkel (ACL) a címzetthez.|
|-2016345688|0x87D101A8|Syncml(424): A darabolt objektum beérkezett, de a fogadott objektum mérete nem egyezik az első darabban deklarált mérettel.|
|-2016345689|0x87D101A7|Syncml(423): A kért parancs meghiúsult, mert a törlésre kijelölt elemet korábban véglegesen törölték a kiszolgálóról.|
|-2016345690|0x87D101A6|Syncml(422): A kért parancs meghiúsult a kiszolgálón, mert a LocURI CGI-parancsainak formátuma nem volt megfelelő.|
|-2016345691|0x87D101A5|Syncml(421): A kért parancs meghiúsult a kiszolgálón, mert a megadott keresési szintaxis ismeretlen volt.|
|-2016345692|0x87D101A4|Syncml(420): A címzetten nincs több tárhely a hátralévő szinkronizálási adatok számára.|
|-2016345693|0x87D101A3|Syncml(419): Az ügyfélkérés ütközést eredményezett, amelyből a kiszolgálói parancs került ki nyertesen.|
|-2016345694|0x87D101A2|Syncml(418): A kért Put vagy Add parancs meghiúsult, mert a cél már létezik.|
|-2016345695|0x87D101A1|Syncml(417): A kérés meghiúsult, és a kérés kezdeményezőjének később újra kell próbálkoznia.|
|-2016345696|0x87D101A0|Syncml(416): A kérés meghiúsult, mert a kérésben megadott bájtméret túl nagy.|
|-2016345697|0x87D1019F|Syncml(415): Nem támogatott adathordozó-típus vagy formátum.|
|-2016345698|0x87D1019E|Syncml(414): A kért parancs meghiúsult, mert a célként megadott URI túl hosszú, és a címzett nem képes vagy nem hajlandó feldolgozni.|
|-2016345699|0x87D1019D|Syncml(413): A címzett elutasította a kért parancs végrehajtását, mert a kért elem nagyobb, mint amit a címzett képes vagy hajlandó feldolgozni.|
|-2016345700|0x87D1019C|Syncml(412): A kért parancs meghiúsult a címzettnél, mert hiányos vagy hibás formátumú volt.|
|-2016345701|0x87D1019B|Syncml(411): A kért parancshoz meg kell adni a bájtméretet vagy a hosszra vonatkozó információt a Meta elemtípusban.|
|-2016345702|0x87D1019A|Syncml(410): A kért cél már nem található a címzetten, és nincs ismert továbbító URI.|
|-2016345703|0x87D10199|Syncml(409): A kérés meghiúsult, mert frissítési ütközés történt az adatok ügyfélen és kiszolgálón tárolt verziói között.|
|-2016345704|0x87D10198|Syncml(408): Egy várt üzenet nem érkezett meg a szükséges időszakon belül.|
|-2016345705|0x87D10197|Syncml(407): A kért parancs meghiúsult, mert a kezdeményezőnek megfelelő hitelesítő adatokat kell megadnia.|
|-2016345706|0x87D10196|Syncml(406): A kért parancs meghiúsult, mert a kérés egyik választható szolgáltatása nem támogatott.|
|-2016345707|0x87D10195|Syncml(405): A kért parancs nincs engedélyezve a célhelyen.|
|-2016345708|0x87D10194|Syncml(404): A kért célhely nem található.|
|-2016345709|0x87D10193|Syncml(403): A kért parancs meghiúsult, de a címzett képes volt értelmezni.|
|-2016345710|0x87D10192|Syncml(402): A kért parancs meghiúsult, mert megfelelő fizetésre van szükség.|
|-2016345711|0x87D10191|Syncml(401): A kért parancs meghiúsult, mert a kérelmezőnek megfelelő hitelesítő adatokat kell megadnia.|
|-2016345712|0x87D10190|Syncml(400): A kért parancsot nem lehetett végrehajtani, mert hibás szintaxist tartalmazott.|
|-2016345807|0x87D10131|Syncml(305): A kért célhelyet a megadott proxy URI használatával kell elérni.|
|-2016345808|0x87D10130|Syncml(304):A kért SyncML-parancs végrehajtása nem történt meg a célon.|
|-2016345809|0x87D1012F|Syncml(303): A kért célhelyhez másik URI tartozik.|
|-2016345810|0x87D1012E|Syncml(302): A kért célhelyhez ideiglenesen másik URI tartozik.|
|-2016345811|0x87D1012D|Syncml(301): A kért célhelyhez új URI tartozik.|
|-2016345812|0x87D1012C|Syncml(300): A kért célhely több kért alternatíva egyike.|
|-2016345896|0x87D100D8|Syncml(216): Egy parancs egy atomi elemen belül volt, és az atomi elem végrehajtása nem sikerült. A parancs visszaállítása sikeres.|
|-2016345897|0x87D100D7|Syncml(215): Egy parancs végrehajtása nem történt meg, mivel a felhasználói beavatkozás során a felhasználó nem fogadta el a lehetőséget.|
|-2016345898|0x87D100D6|Syncml(214): A művelet megszakadt. A SyncML-parancs sikeresen befejeződött, további parancsok azonban nem lesznek végrehajtva a munkamenetben.|
|-2016345899|0x87D100D5|Syncml(213): A darabolt elem elfogadva és pufferelve.|
|-2016345900|0x87D100D4|Syncml(212): Hitelesítés elfogadva. További hitelesítés nem szükséges a szinkronizációs munkamenet hátralévő részére. A válaszkód csak olyan kérésekre alkalmazható válaszként, amelyekben a hitelesítő adatok meg lettek adva.|
|-2016345901|0x87D100D3|Syncml(211): Az elem nem lett törölve. A kért elem nem található. Valószínűleg korábban törölve lett.|
|-2016345902|0x87D100D2|Syncml(210): Törlés archiválás nélkül. A válasz azt jelzi, hogy a kért adat sikeresen törölve lett, azonban a törlés előtt nem lett archiválva, mivel a telepítés ezt az OPCIONÁLIS szolgáltatást nem támogatta.|
|-2016345903|0x87D100D1|Az ütközés duplikálással feloldva. A válasz azt jelzi, hogy a kérés egy frissítési ütközést eredményezett, amelyet a rendszer az ügyfél adatainak a kiszolgáló adatbázisába történő duplikálásával oldott fel. A válasz a duplikált elem cél URI azonosítóját is tartalmazza az Állapot elemben. Továbbá kétirányú szinkronizáció esetén egy Add parancs is elérhető a duplikált adatdefinícióival.|
|-2016345904|0x87D100D0|Az ütközés az ügyfél parancsának „győzelmével” feloldva. A válasz azt jelzi, hogy frissítési ütközés lépett fel, amelyből az ügyfélparancs került ki nyertesen.|
|-2016345905|0x87D100CF|Az ütközés egyesítéssel feloldva. A válasz azt jelzi, hogy a kérés egy ütközést eredményezett, amelyet a rendszer az ügyfél- és a kiszolgálói adatpéldányok egyesítésével oldott fel. A válasz a cél és a forrás URL-címét egyaránt tartalmazza az Állapot elemben. Továbbá a rendszer egy Replace parancsot is visszaadott az egyesített adatokkal.|
|-2016345906|0x87D100CE|A válasz azt jelzi, hogy a parancsnak csak egy része lett végrehajtva. Ha a parancs fennmaradó része később végrehajtható, a végrehajtás alkalmával egy másik megfelelő befejezési kérésállapotkódot KELL létrehozni.|
|-2016345907|0x87D100CD|A forrásnak frissítenie KELL a tartalmát. A parancs kezdeményezőjét tájékoztatja, hogy a tartalmat szinkronizálnia KELL, hogy naprakész verzióval rendelkezzen.|
|-2016345908|0x87D100CC|A kérés sikeresen végre lett hajtva, azonban adatot nem ad vissza. Ez a válaszkód az eredmény abban az esetben is, ha a Get parancs céljának nincs tartalma.|
|-2016345909|0x87D100CB|Nem mérvadó válasz. A kérésre egy, a célzottól eltérő entitás válaszol. A rendszer csak akkor adja vissza ezt a választ, ha a kérés 200-as válaszkódot eredményezett volna a mérvadó céltól.|
|-2016345910|0x87D100CA|Elfogadva feldolgozásra. A valamely alkalmazás távoli végrehajtásának futtatását vagy egy felhasználó vagy alkalmazás riasztását célzó kérés sikeresen végre lett hajtva.|
|-2016345911|0x87D100C9|A kért elem hozzá lett adva.|
|-2016345912|0x87D100C8|A SyncML-parancs sikeresen végrehajtva.|
|-2016346011|0x87D10065|A megadott SyncML-parancs végrehajtása folyamatban van, de még nem fejeződött be.|

### További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.



<!--HONumber=Jun16_HO4-->


