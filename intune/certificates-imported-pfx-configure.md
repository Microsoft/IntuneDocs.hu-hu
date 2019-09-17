---
title: Importált PFX-tanúsítványok használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: Az importált nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványok használata Microsoft Intuneekkel, beleértve a tanúsítványok importálását, a tanúsítványsablon konfigurálását, az Intune importált PFX tanúsítvány-összekötő telepítését és az importált PKCS létrehozását A tanúsítvány profilja.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18d01692f8c42b67605c223f59e13b1e5197a8db
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "71017941"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Importált PKCS-tanúsítványok konfigurálása és használata az Intune-nal

A Microsoft Intune támogatja az importált nyilvános kulcsú (PKCS) tanúsítványok használatát, amelyet gyakran használnak az S/MIME titkosításhoz az e-mail-profilokkal. Az Intune egyes e-mail-profiljai támogatják az S/MIME engedélyezését, ahol meghatározható az S/MIME aláíró tanúsítványa és az S/MIME titkosítási tanúsítvány.

Az S/MIME titkosítás kihívást jelent, mivel az e-mailek egy adott tanúsítvánnyal vannak titkosítva. A tanúsítvány titkos kulcsát kell használnia, amely a levelezést az eszközön titkosítja, hogy visszafejthető legyen. A titkosítási tanúsítványok megújítása rendszeresen megtörténik, ami azt jelenti, hogy az összes eszközön szükség lehet a titkosítási előzményekre, így biztosíthatja a régebbi e-mailek olvasását.  Mivel ugyanazt a tanúsítványt kell használni az eszközök között, nem lehet [SCEP](certificates-scep-configure.md) -vagy [PKCS](certficates-pfx-configure.md) -tanúsítvány-profilokat használni erre a célra, mivel ezek a tanúsítványok kézbesítési mechanizmusai eszközönként egyedi tanúsítványokat szolgáltatnak. 

Az S/MIME Intune-nal való használatával kapcsolatos további információkért az [s/MIME használatával titkosítsa az e-maileket](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Követelmények

Az importált PKCS-tanúsítványok Intune-nal való használatához a következő infrastruktúrára lesz szüksége:

- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**:  
  Minden Intune-bérlő támogatja az összekötő egyetlen példányát. Ezt az összekötőt telepítheti ugyanarra a kiszolgálóra, mint az Microsoft Intune Certificate Connector példánya.

  Ez az összekötő kezeli az Intune-ba importált PFX-fájlok kéréseit egy adott felhasználó számára az S/MIME e-mail-titkosításhoz.  

  Ez az összekötő automatikusan képes frissíteni magát, ha új verziók válnak elérhetővé. A frissítési képesség használatához meg kell győződnie arról, hogy a tűzfalak nyitva vannak, amelyek lehetővé teszik, hogy az összekötő kapcsolatba lépjen a **AutoUpdate.msappproxy.net** a **443**-es porton.  

  További információ az összekötő által elért összes hálózati végpontról: az [Intune hálózati konfigurációjának követelményei és sávszélessége](https://docs.microsoft.com/intune/network-bandwidth-use).


- **Windows Server**:  
  A PFX tanúsítvány-összekötőt a Windows Server használatával futtathatja Microsoft Intunehoz.  Az összekötő az Intune-ba importált tanúsítványok kéréseinek feldolgozására szolgál.

  Az Intune támogatja a *Microsoft Intune tanúsítvány-összekötő* telepítését ugyanarra a kiszolgálóra, mint a *pfx tanúsítvány-összekötőt a Microsoft Intunehoz*.

  Az összekötő támogatásához a kiszolgálónak a .NET 4,6-keretrendszer vagy újabb verziójának kell futnia. Ha a .NET 4,6-keretrendszer nincs telepítve az összekötő telepítésének megkezdése után, az összekötő telepítése automatikusan megtörténik.

- **Visual Studio 2015 vagy újabb** verzió (nem kötelező): A Visual Studióval felépítheti a segítő PowerShell-modult a PFX-tanúsítványok Microsoft Intuneba importálására szolgáló parancsmagokkal. A segítő PowerShell-parancsmagok beszerzéséhez lásd: [PFXImport PowerShell-projekt a githubban](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Működés

Ha az Intune-nal egy **importált pfx-tanúsítványt** telepít egy felhasználóhoz, az eszközön kívül két összetevőt is le kell játszani: 

- **Intune szolgáltatás**: Titkosított állapotban tárolja a PFX-tanúsítványokat, és kezeli a tanúsítvány központi telepítését a felhasználói eszközön.  A tanúsítvány titkos kulcsait védő jelszavakat a rendszer a hardveres biztonsági modul (HSM) vagy a Windows-titkosítás használatával a feltöltés előtt titkosítja, így biztosítva, hogy az Intune bármikor ne férhessen hozzá a titkos kulcshoz.
- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**: Amikor egy eszköz az Intune-ba importált PFX-tanúsítványt kér, a titkosított jelszót, a tanúsítványt és az eszköz nyilvános kulcsát az összekötőnek küldik el.  Az összekötő visszafejti a jelszót a helyszíni titkos kulccsal, majd újratitkosítja a jelszót (és minden plist-profilt, ha iOS-et használ) az eszköz kulcsával, mielőtt elküldené a tanúsítványt az Intune-nak.  Az Intune ezután továbbítja a tanúsítványt az eszköznek, és az eszköz visszafejti azt az eszköz titkos kulcsával, és telepítheti a tanúsítványt.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>A PFX tanúsítvány-összekötő letöltése, telepítése és konfigurálása Microsoft Intune

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -portálon válassza az **eszközök konfigurálása** > **tanúsítvány-összekötők** > **Hozzáadás** lehetőséget.

   ![PFX tanúsítvány-összekötő Microsoft Intune letöltéshez](media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. Kövesse az útmutatást, hogy letöltse a *pfx tanúsítvány-összekötőt a Microsoft Intune* egy olyan helyre, amely elérhető a kiszolgálóról, amelyen az összekötőt telepíteni fogja.
3. A letöltés befejezése után jelentkezzen be a kiszolgálóra, és futtassa a telepítőt (PfxCertificateConnectorBootstrapper. exe).  
   - Ha elfogadja az alapértelmezett telepítési helyet, az összekötő a következőre `Program Files\Microsoft Intune\PFXCertificateConnector`települ:.
   - Az összekötő-szolgáltatás a helyi rendszerfiók alatt fut. Ha egy proxyra van szükség az internet-hozzáféréshez, ellenőrizze, hogy a helyi szolgáltatásfiók hozzáférhet-e a proxy beállításaihoz a kiszolgálón.

4. A Microsoft Intune-hoz készült PFX tanúsítvány-összekötő telepítés után megnyitja a **Regisztráció** lapot. Az Intune-hoz való kapcsolódás engedélyezéséhez **Jelentkezzen be**, és adjon meg egy globális Azure-rendszergazdai vagy Intune-rendszergazdai engedélyekkel rendelkező fiókot.

   > [!WARNING]
   > Alapértelmezés szerint a Windows Server **IE fokozott biztonsági beállításai** beállítás értéke **, amely az** Office 365-be való bejelentkezéssel kapcsolatos problémákat okozhat.

5. Zárja be az ablakot.
6. Az Intune-portálon térjen vissza az **eszköz konfigurációja** > **tanúsítvány-összekötők**elemre. Néhány pillanat múlva zöld pipa jelenik meg, és a **kapcsolatok állapota** **aktív**. Az összekötő-kiszolgáló mostantól képes kommunikálni az Intune-nal.

## <a name="import-pfx-certificates-to-intune"></a>PFX-tanúsítványok importálása az Intune-ba

A [Microsoft Graph](https://docs.microsoft.com/graph) használatával importálhatja a felhasználók pfx-tanúsítványait az Intune-ba. A [GitHub segítő PFXImport PowerShell-projektje](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) olyan parancsmagokat biztosít, amelyek megkönnyítik a műveletek elvégzését.

Ha inkább a Graph használatával szeretné használni saját egyéni megoldását, használja a [userPFXCertificate erőforrástípust](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>"PFXImport PowerShell Project"-parancsmagok létrehozása

A PowerShell-parancsmagok használatához saját maga hozza létre a projektet a Visual Studióval. A folyamat egyenesen előre, míg a kiszolgálón futtatható, javasoljuk, hogy futtassa azt a munkaállomáson.  

1. Nyissa meg az [Intune-erőforrás-hozzáférés](https://github.com/microsoft/Intune-Resource-Access) tárház gyökerét a githubon, majd töltse le vagy klónozással a tárházat a git használatával a gépre.

   ![GitHub Letöltés gomb](media/certificates-imported-pfx-configure/github-download.png)

2. Nyissa meg a projektet a Visual Studióval a **PFXImportPS. SLN**fájl használatával. `.\Intune-Resource-Access-develop\src\PFXImportPowershell\`
3. A felső részen váltson **hibakeresésről** **kiadásra**.
4. Nyissa meg a **Build** elemet, és válassza a **PFXImportPS létrehozása**lehetőséget. Néhány pillanat elteltével megjelenik a **Létrehozás sikeres** megerősítése a Visual Studio bal alsó sarkában.

   ![Visual Studio-Build lehetőség](media/certificates-imported-pfx-configure/vs-build-release.png)

5. A létrehozási folyamat létrehoz egy új mappát a PowerShell-modullal `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Ezt a **kiadási** mappát fogja használni a következő lépésekhez.

### <a name="create-the-encryption-public-key"></a>A titkosítás nyilvános kulcsának létrehozása

PFX-tanúsítványokat és titkos kulcsokat importálhat az Intune-ba. A titkos kulcs védelmét biztosító jelszó a helyszínen tárolt nyilvános kulccsal van titkosítva. A nyilvános/titkos kulcspár létrehozásához és tárolásához használhatja a Windows-titkosítást, a hardveres biztonsági modult vagy más típusú titkosítást is.  A használt titkosítási típustól függően a nyilvános/titkos kulcspár a biztonsági mentéshez fájlformátum formátumban is exportálható.

A PowerShell-modul módszereket biztosít a kulcsok Windows-titkosítással történő létrehozására. Emellett más eszközöket is használhat a kulcsok létrehozásához.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>A titkosítási kulcs létrehozása Windows-kriptográfia használatával

1. Másolja a Visual Studio által létrehozott *kiadási* mappát arra a kiszolgálóra, amelyre a **pfx tanúsítvány-összekötőt telepítette Microsoft Intunehoz**. Ez a mappa tartalmazza a PowerShell-modult.  
2. A kiszolgálón nyissa meg a *PowerShellt* rendszergazdaként, majd navigáljon a PowerShell-modult tartalmazó *kiadási* mappához.
3. A modul importálásához futtassa a `Import-Module .\IntunePfxImport.psd1` parancsot a modul importálásához.
4. Következő, Futtatás`Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > A PFX-tanúsítványok importálásakor a használt szolgáltatót újra ki kell választani. Használhatja a **Microsoft szoftveres kulcstároló-szolgáltatót**, bár más szolgáltató használata is támogatott. A kulcs neve is megjelenik példaként, és használhat más nevet is.  

   Ha azt tervezi, hogy importálja a tanúsítványt a munkaállomásról, exportálhatja a kulcsot egy fájlba a következő paranccsal:`Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   A titkos kulcsot importálni kell azon a kiszolgálón, amelyen a PFX tanúsítvány-összekötő fut Microsoft Intune, hogy az importált PFX-tanúsítványok sikeresen feldolgozhatók legyenek.  

#### <a name="to-use-a-hardware-security-module-hsm"></a>Hardveres biztonsági modul (HSM) használata  

A hardveres biztonsági modult (HSM) használhatja a nyilvános/titkos kulcspár létrehozásához és tárolásához. További információ: HSM-szolgáltató dokumentációja.

### <a name="import-pfx-certificates"></a>PFX-tanúsítványok importálása 

A következő folyamat a PowerShell-parancsmagokat használja példaként a PFX-tanúsítványok importálásához. A követelményektől függően különböző beállításokat választhat.

A lehetőségek a következők:  
- Felhasználási cél (a tanúsítványokat egy címke alapján csoportosítja):  
  - kiosztva
  - Smimeencryption tanúsítványhoz tartozó
  - Smimesigning tanúsítványhoz tartozó


- Kitöltési séma:  
  - PKCS1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

Válassza ki azt a kulcstároló-szolgáltatót, amely megfelel a kulcs létrehozásához használt szolgáltatónak.

#### <a name="to-import-the-pfx-certificate"></a>A PFX-tanúsítvány importálása  

1. Exportálja a tanúsítványokat bármely hitelesítésszolgáltatótól (CA) a szolgáltató dokumentációjának követésével.  A Microsoft Active Directory tanúsítványszolgáltatás esetében [ezt a parancsfájlt](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b)használhatja.   
2. A kiszolgálón nyissa meg a *PowerShellt* rendszergazdaként, majd navigáljon a PowerShell-modult tartalmazó *kiadási* mappához.
3. A modul importálásához futtassa a következőt`Import-Module .\IntunePfxImport.psd1`  
4. Az Intune Graph-ban való hitelesítéshez futtassa a következőt`$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Mivel a hitelesítés a gráfon fut, engedélyeket kell biztosítania a AppID. Ha első alkalommal használta ezt a segédprogramot, *globális rendszergazdai jogosultsággal* kell rendelkeznie. A PowerShell-parancsmagok ugyanazt a AppID használják, mint a [PowerShell Intune-mintákkal](https://github.com/microsoftgraph/powershell-intune-samples).   
5. A futtatásával `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`alakítsa át a biztonságos sztringbe importálandó összes pfx-fájl jelszavát.  
6. **UserPFXCertificate** objektum létrehozásához futtassa a parancsot.`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   Például:`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > Ha az összekötőt futtató kiszolgálótól eltérő rendszerből importálja a tanúsítványt, akkor a következő parancsot kell használnia, amely tartalmazza a kulcsfájl elérési útját:`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. A **UserPFXCertificate** objektum importálása az Intune-ba a futtatásával`Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. A tanúsítvány importálásának ellenőrzéséhez futtassa a következőt`Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UsertList "<UserUPN>"`

További információ az egyéb elérhető parancsokról: a [PFXImport PowerShell-projekt](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)információs fájlja a githubon.

## <a name="create-a-pkcs-imported-certificate-profile"></a>Importált PKCS-tanúsítványprofil létrehozása

A tanúsítványok Intune-ba importálása után hozzon létre egy **Importált PKCS-tanúsítvány** profilt, és rendelje hozzá Azure Active Directory-csoportokhoz.

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -portálon az **eszköz-konfigurációs** > **profilok** > **profil létrehozása**elemet kell létrehozni.
2. Adja meg a következő tulajdonságokat:

   - **Név** a profil számára
   - Igény szerint hozzáadhat egy leírást
   - **Platform**, amelyen telepíteni kell a profilt
   - A **Profiltípust** állítsa **Importált PKCS-tanúsítványra**

3. Nyissa meg a **Beállítások** lapot, és adja meg a következő tulajdonságokat:

   - **Felhasználási cél**: Itt adhatja meg a profilhoz importált tanúsítványok kívánt célját. A rendszergazdák különböző felhasználási célokra importálnak tanúsítványokat (például hitelesítés, S/MIME-aláírás vagy S/MIME-titkosítás). A tanúsítványprofilban kijelölt felhasználási cél alapján lesznek párosítva a megfelelő importált tanúsítványok. A felhasználási cél az importált tanúsítványok együttes csoportosítása, és nem garantálja, hogy az adott címkével importált tanúsítványok megfelelnek a kívánt célnak.  
   - **Tanúsítvány érvényességi időtartama**: Hacsak nem módosították az érvényességi időszakot a tanúsítványsablon esetében, ez a beállítás alapértelmezés szerint egy év.  
   - **Kulcstároló-szolgáltató (KSP)** : Windows esetén válassza ki a kulcsok tárolásának helyét az eszközön.  

4. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.
5. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](device-profile-assign.md).



