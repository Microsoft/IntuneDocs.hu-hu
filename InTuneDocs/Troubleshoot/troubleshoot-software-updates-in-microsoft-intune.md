---
# required metadata

title: Szoftverfrissítésekkel kapcsolatos hibák elhárítása | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A Microsoft Intune szoftverfrissítéseinek hibaelhárítása
Az ebben a részben ismertetett információk segítséget nyújtanak a Microsoft Intune szoftverfrissítéseivel kapcsolatban felmerülő problémák megoldásához.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben talál további részleteket a segítségkéréshez.

A következő táblázat a **frissítési ügynök** hibakódjait sorolja fel. Ha nem talál meg egy adott hibakódot a táblázatban, lásd: [A Windows Update ügynök eredménykódjai](http://go.microsoft.com/fwlink/?LinkID=221542).

|Hibakód|Szimbolikus név|További információ|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|Az ügynök sikeresen leállt.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|A művelet sikeresen befejeződött, de a frissítések alkalmazása során hibák jelentkeztek.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Egy visszahívás későbbi megszakításra lett megjelölve, mert a művelet megszakítására vonatkozó kérést a visszahívás futtatása közben küldték.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|A frissítés telepítésének befejezéséhez a rendszert újra kell indítani.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|A telepíteni kívánt frissítés már telepítve van a rendszeren.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|Az eltávolítani kívánt frissítés nincs telepítve a rendszeren.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|A frissítés telepítése folyamatban van.|
|**0x80cf0001**|OM_E_NO_SERVICE|Az ügynök nem tudja biztosítani a szolgáltatást.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|Meghaladta a szolgáltatás maximális kapacitását.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|Egy azonosító nem található.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|Az objektumot nem lehet inicializálni.|
|**0x80cf0007**|OM_E_INVALIDINDEX|Egy gyűjtemény indexe nem érvényes.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|A lekérdezett elem kulcsa nem található.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Ütköző művelet volt folyamatban. Egyes műveleteket, például több telepítést nem lehet egyidejűleg elvégezni.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|A műveletet megszakították.|
|**0x80cf000C**|OM_E_NOOP|Nem volt szükség műveletre.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|Az ügynök nem találta meg a szükséges információkat a frissítés XML-adataiban.|
|**0x80cf000E**|OM_E_XML_INVALID|Az ügynök érvénytelen információkat talált a frissítés XML-adataiban.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|A rendszer körkörös frissítési kapcsolatokat észlelt a metaadatokban.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|A frissítési kapcsolatok túl mélyen vannak beágyazva ahhoz, hogy ki lehessen értékelni őket.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|A rendszer érvénytelen frissítési kapcsolatot talált.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|A rendszer érvénytelen beállításazonosítót olvasott be.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|A művelet ismétlődő elemet próbált hozzáadni egy listához.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|A hívó nem tudja telepíteni a telepítéshez kért frissítéseket.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|A művelet úgy próbálta elvégezni a telepítést, hogy egy másik telepítés is folyamatban volt, vagy függőben volt a rendszer kötelező újraindítása.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|A műveletet nem lett végrehajtva, mert nincs alkalmazható frissítés.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|A művelet sikertelen, mert egy szükséges felhasználói jogkivonat hiányzik.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|A kizárólagos frissítések nem telepíthetők más frissítésekkel egyszerre.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Nincs megadva egy házirendérték.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Egy frissítés érvénytelen metaadatot tartalmaz.|
|**0x80cf001E**|OM_E_SERVICE_STOP|A műveletet nem lehetett befejezni, mert a szolgáltatás vagy a rendszer leállt.|
|**0x80cf001F**|OM_E_NO_CONNECTION|A műveletet nem sikerült befejezni, mert a hálózati kapcsolat nem volt elérhető.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|A műveletet nem sikerült befejezni, mert nincs bejelentkezett interaktív felhasználó.|
|**0x80cf0021**|OM_E_TIME_OUT|A műveletet időtúllépés miatt nem sikerült befejezni.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|A művelet az összes frissítésnél sikertelen.|
|**0x80cf0024**|OM_E_NO_UPDATE|Nincsenek frissítések.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|A csoportházirend-beállítások megakadályozták a Windows Update elérését.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|A frissítés típusa érvénytelen.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|A frissítés nem távolítható el, mert a kérés nem WSUS-kiszolgálótól származik.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|Előfordulhat, hogy a keresés nem talált meg minden frissítést, vagy a rendszeren egy licenc nélküli alkalmazás található.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Nem sikerült telepíteni egy különbségtömörítéses frissítést, mert szükség volt a forrásra.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Nem sikerült telepíteni egy teljes fájlos frissítést, mert szükség volt a forrásra.|
|**0x80cf002E**|OM_E_WU_DISABLED|Egy nem felügyelt kiszolgálóhoz való hozzáférés nem engedélyezett.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|A műveletet nem sikerült befejezni, mert a **DisableWindowsUpdateAccess** házirend van érvényben.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|A proxylista formátuma érvénytelen.|
|**0x80cf0031**|OM_E_INVALID_FILE|A fájl formátuma nem megfelelő.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|A keresési feltételek karakterlánca érvénytelen.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|A frissítést nem sikerült letölteni.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|A rendszer nem dolgozta fel a frissítést.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|Az objektum aktuális állapota nem engedélyezi a műveletet.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|A művelet nem támogatott.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|A letöltött fájl tartalma váratlan típusú.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|A kiszolgáló túl sokszor kérte az ügynököt újraszinkronizálásra.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|A WUA felhasználói felülete nem támogatott.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Ezt a műveletet csak rendszergazdák hajthatják végre számítógépenkénti frissítéseken.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|Egy nem támogatott hatókörű keresést kíséreltek meg.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|Az URL-cím nem mutat fájlra.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|A kért művelet nem támogatott.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Az adatok a tartományon kívül esnek.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Az adat érvénytelen verziót tartalmaz.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|A keresés befejeződött, de néhány frissítés észlelése nem sikerült.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|A letöltési hívás befejeződött, de néhány frissítés letöltése nem sikerült.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|A telepítési hívás befejeződött, de néhány frissítés telepítése nem sikerült.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|A Windows Update gyorsítótára üres, mert nem lett inicializálva.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|A kiszolgáló nem támogatja a kategóriára vonatkozó keresést. Helyette teljes katalógusban végzett keresést kell elindítani.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Hiba történt a szolgáltatással való engedélyezés során.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|A végpontnak nincs útvonala vagy hálózati kapcsolata.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|A fogadott adatok nem felelnek meg az adategyezmény követelményeinek.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|Az URL-cím érvénytelen.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|Nem sikerült betölteni az NWS futásidejű modult.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|A proxy hitelesítési sémája nem támogatott.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|A kért szolgáltatástulajdonság nem érhető el.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|A végpontszolgáltató beépülő modulja online frissítést igényel.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|A kért szolgáltatásvégpont URL-címe nem érhető el.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|Megszakadt a kapcsolat a szolgáltatásvégponttal.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|A művelet nem érvényes, mert a protokoll-kapcsolattartó állapota érvénytelen.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|Egy művelet olyan okokból szakadt meg, amelyeket nem lehet egy másik hibakóddal leírni.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Előfordulhat, hogy a keresés nem talált meg néhány frissítést, mert a Windows Installer verziója 3.1-esnél régebbi.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Előfordulhat, hogy a keresés nem talált meg néhány frissítést, mert a Windows Installer nincsen konfigurálva.|
|**0x80cf1003**|OM_E_MSP_DISABLED|Előfordulhat, hogy a keresés nem talált meg néhány frissítést, mert a házirend letiltotta a Windows Installer javítását.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Egy frissítés alkalmazása sikertelen volt, mert az alkalmazás felhasználónként van telepítve.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Egy távoli frissítéskezelőre vonatkozó kérést nem lehetett teljesíteni, mert nem érhető el távoli folyamat.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Egy távoli frissítéskezelőre vonatkozó kérést nem lehetett teljesíteni, mert a kezelő csak helyi műveletekhez használható.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Nem sikerült létrehozni egy távoli frissítéskezelőt, mert már létezik egy.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|A kezelő nem tudott teljesíteni egy frissítés telepítésére (eltávolítására) vonatkozó kérést, mert a frissítés nem támogatja a telepítést (eltávolítást).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Egy műveletet nem sikerült befejezni, mert nem megfelelő kezelő van megadva.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Egy kezelői műveletet nem sikerült befejezni, mert a frissítés érvénytelen metaadatot tartalmaz.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Egy műveletet nem sikerült befejezni, mert a telepítő túllépte az időkorlátot. Ellenőrizze, hogy egy felhasználói beavatkozást igénylő frissítés telepítése megkapta-e a jóváhagyást. Ebben az esetben vizsgálja felül a frissítés telepítési paramétereit, hogy a telepítése csendes legyen.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Egy frissítéskezelő által végzett műveletet megszakítottak.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Egy műveletet nem sikerült végrehajtani, mert a kezelőspecifikus metaadatok érvénytelenek.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|A telepítőnek nem sikerült telepítenie (eltávolítania) egy vagy több frissítést.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|A frissítéskezelő nem telepítette a frissítést, mert azt újra le kell tölteni.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|A frissítéskezelő nem tudott értesítést küldeni a telepítési (eltávolítási) művelet állapotáról.|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|A frissítés újraindítás utáni művelete még folyamatban van.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|A frissítés újraindítás utáni műveletének eredményét nem sikerült meghatározni.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|A frissítés váratlan állapotba került az újraindítás utáni művelet befejezését követően.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|Az operációs rendszer karbantartási csomagját frissíteni kell a frissítés letöltése vagy telepítése előtt.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Egy visszahívás-telepítő hibával tért vissza.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|Az egyéni telepítő aláírása nem egyezik a frissítés által igényelt aláírással.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|A telepítő nem támogatja a telepítés konfigurációját.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|A telepítés céljaként megadott munkamenet érvénytelen.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Frissítéskezelői hiba, amelyet más OM_E_UH_&#42; kód nem jelez.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|A felhasználói felület nem jeleníthető meg olyan módban, amely nem alkalmas a felhasználói felület megjelenítésére. Előfordulhat, hogy a Windows Update-ügyfelek felhasználóifelület-moduljai nincsenek telepítve.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Nem támogatott verzió a WU-ügyfél felhasználói felületének exportált funkcióinál.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Olyan felhasználóifelület-hiba történt, amelyet más OM_E_AUCLIENT_&#42; hibakód nem jelez.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Ugyanaz, mint a **SOAPCLIENT_SOAPFAULT**. A SOAP-ügyfél egy **OM_E_PT_SOAP_&#42;** hibakódtípusú hiba miatt nem tudta végrehajtani a műveletet.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Ugyanaz, mint a **SOAPCLIENT_PARSEFAULT_ERROR**.  A SOAP-ügyfél nem tudott elemezni egy SOAP-hibát.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Ugyanaz, mint a **SOAPCLIENT_PARSE_ERROR**.  A SOAP-ügyfél nem tudta elemezni a kiszolgáló válaszát.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Ugyanaz, mint a **SOAP_E_VERSION_MISMATCH**. A SOAP-ügyfél ismeretlen névteret talált a SOAP-borítékhoz.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Ugyanaz, mint a **SOAP_E_MUST_UNDERSTAND**. A SOAP-ügyfél nem tudott értelmezni egy fejlécet.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Ugyanaz, mint a **SOAP_E_CLIENT**. A SOAP-ügyfél azt jelezte, hogy az üzenet hibás formátumú. Javítsa ki, majd küldje el újra.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Ugyanaz, mint a **SOAP_E_SERVER**. A SOAP-üzenetet kiszolgálóhiba miatt nem sikerült feldolgozni. Küldje újra később.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|A kiszolgálóval való adatváltások száma meghaladta a maximálisan megengedettet.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|Az inicializálás sikertelen, mert az objektum már inicializálva van.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|A számítógép neve nem határozható meg.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|A kiszolgálótól érkezett válasz azt jelzi, hogy a kiszolgálót módosították vagy érvénytelen volt a cookie. Frissítse a belső gyorsítótárat, és próbálkozzon újra.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Ugyanaz, mint a **400-as HTTP-állapot**. A kiszolgáló nem tudta feldolgozni a kérést, mert a szintaxis érvénytelen.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Ugyanaz, mint a **401-es HTTP-állapot**. A kért erőforráshoz felhasználói hitelesítés szükséges.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Ugyanaz, mint a **403-as HTTP-állapot**. A kiszolgáló megértette a kérést, de visszautasította a végrehajtását.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Ugyanaz, mint a **404-es HTTP-állapot**. A kiszolgáló nem találja a kért egységes erőforrás-azonosítót (URI).|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Ugyanaz, mint a **405-ös HTTP-állapot**. A HTTP-metódus nem engedélyezett.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Ugyanaz, mint a **407-es HTTP-állapot**. Proxyhitelesítés szükséges.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Ugyanaz, mint a **408-as HTTP-állapot**. A kiszolgálón időtúllépés történt a kérésre való várakozásnál.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Ugyanaz, mint a **409-es HTTP-állapot**. A kérés nem lett végrehajtva az erőforrás aktuális állapotával való ütközés miatt.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Ugyanaz, mint a **410-es HTTP-állapot**. A kért erőforrás már nem érhető el a kiszolgálón.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Ugyanaz, mint az **500-as HTTP-állapot**. A kiszolgáló belső hibája megakadályozta a kérés teljesítését.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Ugyanaz, mint az **500-as HTTP-állapot**. A kiszolgáló nem támogatja a kérés teljesítéséhez szükséges funkciót.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Ugyanaz, mint az **502-es HTTP-állapot**. Az átjáróként vagy proxyként működő kiszolgáló a kérés teljesítése közben érvénytelen választ kapott az elért felsőbb szintű kiszolgálótól.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Ugyanaz, mint az **503-as HTTP-állapot**. A szolgáltatás átmenetileg túlterhelt.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Ugyanaz, mint az **503-as HTTP-állapot**. A kérés túllépte az időkorlátot az átjáróra való várakozás közben.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Ugyanaz, mint az **505-ös HTTP-állapot**. A kiszolgáló nem támogatja a HTTP protokoll a kéréshez használt verzióját.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|A művelet sikertelen, mert a fájl helye megváltozott. Frissítse a belső állapotot, és küldje el újból.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|A kiszolgáló üres hitelesítőinformáció-listát adott vissza.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|Az ügynök nem tudott létrehozni érvényes hitelesítési cookie-kat.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Egy konfigurációs tulajdonság értéke hibás volt.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Egy konfigurációs tulajdonság értéke hiányzik.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|A HTTP-kérést nem lehetett teljesíteni, és az ok nem felelt meg a **OM_E_PT_HTTP_&#42;** hibakódok egyikének sem.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Ugyanaz, mint az **ERROR_WINHTTP_NAME_NOT_RESOLVED**. A proxy- vagy célkiszolgáló neve nem oldható fel.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|A külső .cab fájl feldolgozása hibákkal fejeződött be.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|A külső kabinetfájl-feldolgozó inicializálása nem fejeződött be.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|A metaadatfájl formátuma nem érvényes.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|A külső kabinetfájl-feldolgozó érvénytelen metaadatokat talált.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Nem sikerült kibontani a fájlkivonatot egy külső .cab fájlból.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Egy külső .cab fájlt nem sikerült kibontani.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|A külső kabinetfájl-feldolgozó nem tudta lekérni a fájlhelyeket.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Olyan kommunikációs hiba fordult elő, amelyet más **OM_E_PT_&#42;** hibakód nem jelez.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Egy letöltéskezelői műveletet nem sikerült befejezni, mert a kért fájlnak nincs URL-címe.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Egy letöltéskezelői műveletet nem sikerült befejezni, mert a fájlkivonat nem ismerhető fel.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Egy letöltéskezelői műveletet nem sikerült befejezni, mert a fájlmetaadatok ismeretlen kivonatoló algoritmust kértek.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Egy letöltéskezelői műveletet nem sikerült befejezni, mert a hálózati kapcsolat nem volt elérhető.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|A frissítés nem töltődött le.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|Egy letöltéskezelői művelet nem sikerült, mert a letöltéskezelő nem tudott csatlakozni a háttérben futó intelligens átviteli szolgáltatáshoz (BITS).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|Egy letöltéskezelői művelet nem sikerült, mert meghatározatlan átviteli hiba történt a háttérben futó intelligens átviteli szolgáltatásban (BITS).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|Egy letöltést újra kell indítani, mert a letöltési forrás helye megváltozott.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|Egy letöltést újra kell indítani, mert a frissítési tartalom egy új verzióban megváltozott.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Olyan letöltéskezelői hiba történt, amelyet más **OM_E_DM_&#42;** hibakód nem jelez.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|Érvénytelen eseménytartalom lett megadva.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|Az eseménytartalom elküldött mérete érvénytelen.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|A szolgáltatás nincsen regisztrálva.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|Egy művelet nem sikerült, mert az ügynök leállása folyamatban van.|
|**0x80cf8001**|OM_E_DS_INUSE|Egy művelet nem sikerült, mert az adattár használatban volt.|
|**0x80cf8002**|OM_E_DS_INVALID|Nem egyezik az adattár jelenlegi és várt állapota.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|Az adattárból hiányzik egy táblázat.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|Az adattár nem várt oszlopokkal rendelkező táblázatot tartalmaz.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|Egy táblázatot nem sikerült megnyitni, mert a táblázat nincs az adattárban.|
|**0x80cf8006**|OM_E_DS_BADVERSION|Nem egyezik az adattár jelenlegi és várt verziója.|
|**0x80cf8007**|OM_E_DS_NODATA|A kért információ nem található az adattárban.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|Hiányoznak az adattárhoz szükséges információk, vagy az adattárban null értékű egy olyan táblázatoszlop, amelyben a null érték nem megengedett.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|Hiányoznak az adattárhoz szükséges információk, vagy az adattárban hiányzó licencfeltételekre, fájlra, honosított tulajdonságra vagy csatolt sorra vonatkozó hivatkozás van.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|A rendszer nem dolgozta fel a frissítést, mert nem ismerte fel a frissítéskezelőjét.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|A frissítés nem lett törölve, mert egy vagy több szolgáltatás még mindig hivatkozik rá.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|Az adattárszakaszt nem sikerült zárolni a rendelkezésre álló időn belül.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|A sor nem lett hozzáadva, mert egy létező sornak ugyanaz az elsődleges kulcsa.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Az adattárat nem sikerült inicializálni, mert egy másik folyamat zárolta.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|Az adattár számára nem engedélyezett a COM-regisztráció a jelenlegi folyamatban.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Egy művelet nem tudott létrehozni egy adattárobjektumot egy másik folyamatban.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|A kiszolgáló ugyanazt a frissítést küldte az ügyfélnek két különböző verzióazonosítóval.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Egy műveletet nem sikerült befejezni, mert a szolgáltatás nem található az adattárban.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Egy műveletet nem sikerült befejezni, mert a szolgáltatás regisztrációja lejárt.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|A frissítés elrejtésére vonatkozó kérelmet elutasította a rendszer, mivel az vagy egy kötelező frissítés, vagy határidővel telepítették.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|Egy táblázat nem zárult be, mert nincs a munkamenethez társítva.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|Egy táblázat nem zárult be, mert nincs a munkamenethez társítva.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|A szolgáltatás eltávolítására vagy regisztrációjának megszüntetésére irányuló kérést a rendszer elutasította, mert az egy beépített szolgáltatás, vagy mert az automatikus frissítések nem térhetnek vissza egy másik szolgáltatásra.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|A rendszer elutasította a kérést, mert a művelet nem engedélyezett.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|Az aktuális adattár sémája nem egyezik egy biztonsági másolatként tárolt XML-dokumentumban lévő táblázat sémájával.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|Az adattár a munkamenet alaphelyzetbe állítását igényli. Szabadítsa fel a munkamenetet, és próbálkozzon újból egy új munkamenettel.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|Egy adattárműveletet nem sikerült befejezni, mert megszemélyesített identitással kérték.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Olyan adattárhiba történt, amelyet más **OM_E_DS_&#42;** hibakód nem jelez.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Az Automatikus frissítések szolgáltatás nem tudta kiszolgálni a beérkező kéréseket.|
|**0x80cfA004**|OM_E_AU_PAUSED|Az Automatikus frissítések szolgáltatás nem tudta feldolgozni a beérkező kéréseket, mert szüneteltették.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Nincs felügyelet nélküli szolgáltatás regisztrálva az Automatikus frissítések szolgáltatással.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Az Automatikus frissítések szolgáltatással regisztrált alapértelmezett szolgáltatás a keresés közben módosult.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Az Automatikus frissítések szolgáltatás már felkérte a felhasználót az újraindításra.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Olyan, automatikus frissítésekkel kapcsolatos hiba fordult elő, amelyet más **OM_E_AU &#42;** hibakód nem jelez.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert egy kifejezés nem volt felismerhető.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert egy kifejezés érvénytelen volt.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert egy kifejezés nem megfelelő számú metaadat-csomópontot tartalmaz.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert a szerializált kifejezésadatok verziója érvénytelen.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|A kifejezéskiértékelőt nem sikerült inicializálni.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert egy attribútum érvénytelen.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Egy kifejezéskiértékelői műveletet nem sikerült befejezni, mert a számítógép fürtállapota nem határozható meg.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Olyan kifejezéskiértékelői hiba történt, amelyet más **OM_E_EE_&#42;** hibakód nem jelez.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|Az esemény gyorsítótárfájlja sérült.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Nem sikerült elemezni az XML-t az esemény névterének leírójában.|
|**0x80cfF003**|OM_E_INVALID_EVENT|Érvénytelen az XML az esemény névterének leírójában.|
|**0x80cfF004**|OM_E_SERVER_BUSY|A kiszolgáló elutasított egy eseményt, mert elfoglalt volt.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Olyan jelentéskészítői hiba történt, amelyet más hibakód nem jelez.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|A telepítés nem sikerült, mert függőben van a rendszer kötelező újraindítása.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|A letöltést megszakították.|

## A nagyszámú felülírt frissítéssel rendelkező Windows 7 rendszerű számítógépek nem küldenek jelentéseket a Microsoft Intune konzolnak
**Probléma**: Olyan helyzet állhat elő, amelyben a Microsoft Intune-ügyfelek az alábbi jelenségek közül egyet vagy többet tapasztalnak:
- Az ügyfelek váratlanul leállítják a jelentésküldést a Microsoft felügyeleti konzolnak.  
- Az ügyfeleken magas fokú processzorhasználatot tapasztalható.
- Az Intune portálon keresztül telepített alkalmazások telepítése lassan megy végbe. 
- A Microsoft Intune Center a következő hibát váltja ki: *Hiba történt a számítógép frissítése közben. Észlelt hiba kódja: 0x800705b4*.
- Az Intune felügyeleti konzol > Csoportok > Minden eszköz menüpont alatti állapotmezőben a következő látható: *A számítógépen telepített ügynökök legalább egyike hibát jelzett. Lehetséges, hogy a számítógépről rendelkezésre álló információk pontatlanok vagy elavultak*.

Ezt a problémát az okozhatja, ha a felülírt frissítéseket (vagyis azokat a frissítéseket, amelyeket más frissítések már leváltottak) a felhasználó hosszabb időtartamon át nem utasította el. Bizonyos folyamatok (például az alkalmazások telepítése) során a Windows sorban ellenőrzi az összes felülírt frissítést, hogy helyesen leképezhesse a korábbi és új frissítéseket. Amennyiben a felülírt frissítések listája túl hosszúvá válik, az ellenőrzési feladat az elvégzéséhez szükséges magas processzorterhelés és idő következtében magas fokú processzorhasználathoz vezethet. Ez a probléma főként a Windows 7 rendszerű ügyfeleket érinti, mivel ehhez a rendszerhez érhetők el nagy számban felülírt frissítések. A Windows 8 és az újabb operációs rendszerekhez nem tartozik ilyen sok felülírt frissítés, ezért ezeknél nem fordul elő olyan gyakran a probléma.

**Megoldás**: A probléma megoldásához kövesse az alábbi lépéseket:
1. Jelentkezzen be az [Intune felügyeleti konzolba](https://manage.microsoft.com).
2. Válassza a **Frissítések** > **Minden frissítés** lehetőséget.
3. A felső eszköztár szűrője segítségével szűrje meg a találatokat a felülírt frissítésekre.
4. Utasítsa el a Windows 7 rendszerre vagy az alkalmazásokra (például a Microsoft Office-ra) vonatkozó, az érintett ügyfeleken telepített összes felülírt frissítést. 
5. Indítsa újra az érintett ügyfeleket.

Ha Windows 7 rendszert használ, ezenfelül ellenőrizze, hogy telepítette-e a következő frissítést:[3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265).

### További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.



<!--HONumber=Jun16_HO1-->


