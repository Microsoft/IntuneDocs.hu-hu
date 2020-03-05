---
title: Importált PFX-tanúsítványok használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: Az importált nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványait Microsoft Intune használatával használhatja. Importálja a tanúsítványokat, konfigurálja a tanúsítványsablonokat, telepítse az Intune-ba importált PFX-tanúsítvány-összekötőt, és hozzon létre egy importált PKCS-tanúsítvány profilt.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda; rimarram
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d31093f4765969d97f3d57f4b41eaa5ef98daaf1
ms.sourcegitcommit: b4502dc09b82985265299968a11158f5898b56e0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78287577"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Importált PKCS-tanúsítványok konfigurálása és használata az Intune-nal

A Microsoft Intune támogatja az importált nyilvános kulcsú (PKCS) tanúsítványok használatát, amelyet gyakran használnak az S/MIME titkosításhoz az e-mail-profilokkal. Az Intune egyes e-mail-profiljai támogatják az S/MIME engedélyezését, ahol meghatározható az S/MIME aláíró tanúsítványa és az S/MIME titkosítási tanúsítvány.

Az S/MIME titkosítás kihívást jelent, mivel az e-mailek egy adott tanúsítvánnyal vannak titkosítva:

- A tanúsítvány titkos kulcsát kell használnia, amely a levelezést az eszközön titkosítja, hogy visszafejthető legyen.
- Az eszközön lévő tanúsítvány lejárta előtt új tanúsítványt kell importálnia, hogy az eszközök továbbra is visszafejtsék az új e-maileket. A tanúsítványok megújítása nem támogatott.
- A titkosítási tanúsítványok megújítása rendszeresen megtörténik, ami azt jelenti, hogy a korábbi tanúsítványokat továbbra is meg kell őrizni az eszközökön, hogy a régebbi e-mailek továbbra is visszafejtve legyenek.  

Mivel ugyanazt a tanúsítványt kell használni az eszközök között, nem lehet [SCEP](certificates-scep-configure.md) -vagy [PKCS](certficates-pfx-configure.md) -tanúsítvány-profilokat használni erre a célra, mivel ezek a tanúsítványok kézbesítési mechanizmusai eszközönként egyedi tanúsítványokat szolgáltatnak.

Az S/MIME Intune-nal való használatával kapcsolatos további információkért az [s/MIME használatával titkosítsa az e-maileket](certificates-s-mime-encryption-sign.md).

## <a name="supported-platforms"></a>Támogatott platformok

Az Intune támogatja a PFX-tanúsítványok importálását a következő platformokon:

- Android – eszköz rendszergazdája
- Android Enterprise – teljes körűen felügyelt
- Android Enterprise-Work profil
- iOS
- Mac
- Windows 10

## <a name="requirements"></a>Követelmények

Az importált PKCS-tanúsítványok Intune-nal való használatához a következő infrastruktúrára lesz szüksége:

- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**:

  Minden Intune-bérlő támogatja az összekötő egyetlen példányát. Ezt az összekötőt telepítheti ugyanarra a kiszolgálóra, mint az Microsoft Intune Certificate Connector példánya.

  Ez az összekötő kezeli az Intune-ba importált PFX-fájlok kéréseit egy adott felhasználó számára az S/MIME e-mail-titkosításhoz.

  Ez az összekötő automatikusan képes frissíteni magát, ha új verziók válnak elérhetővé. A frissítési képesség használatához meg kell győződnie arról, hogy a tűzfalak nyitva vannak, amelyek lehetővé teszik, hogy az összekötő kapcsolatba lépjen a **AutoUpdate.msappproxy.net** a **443**-es porton.

  További információ: [Microsoft Intune hálózati végpontok és az](../fundamentals/intune-endpoints.md) [Intune hálózati konfigurációs követelményei és sávszélessége](../fundamentals/network-bandwidth-use.md).

- **Windows Server**:

  A PFX tanúsítvány-összekötőt a Windows Server használatával futtathatja Microsoft Intunehoz.  Az összekötő az Intune-ba importált tanúsítványok kéréseinek feldolgozására szolgál.
  
  Az összekötőhöz a felügyelt eszközökhöz tartozó, az [eszköz végpontjának tartalma](https://docs.microsoft.com/intune/fundamentals/intune-endpoints#access-for-managed-devices)alapján megegyező portokhoz kell hozzáférni.

  Az Intune támogatja a *Microsoft Intune tanúsítvány-összekötő* telepítését ugyanarra a kiszolgálóra, mint a *pfx tanúsítvány-összekötőt a Microsoft Intunehoz*.

  Az összekötő támogatásához a kiszolgálónak a .NET 4,6-keretrendszer vagy újabb verziójának kell futnia. Ha a .NET 4,6-keretrendszer nincs telepítve az összekötő telepítésének megkezdése után, az összekötő telepítése automatikusan megtörténik.

- **Visual Studio 2015 vagy újabb** (nem kötelező):

  A Visual Studióval felépítheti a segítő PowerShell-modult a PFX-tanúsítványok Microsoft Intuneba importálására szolgáló parancsmagokkal. A segítő PowerShell-parancsmagok beszerzéséhez lásd: [PFXImport PowerShell-projekt a githubban](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Működés

Ha az Intune-nal egy **importált pfx-tanúsítványt** telepít egy felhasználóhoz, az eszközön kívül két összetevőt is le kell játszani:

- **Intune szolgáltatás**: a pfx-tanúsítványokat titkosított állapotban tárolja, és kezeli a tanúsítvány központi telepítését a felhasználói eszközön.  A tanúsítvány titkos kulcsait védő jelszavak titkosítása a hardveres biztonsági modul (HSM) vagy a Windows-titkosítás használatával történik, így biztosítva, hogy az Intune bármikor ne férhessen hozzá a titkos kulcshoz.

- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**: Ha egy eszköz az Intune-ba importált pfx-tanúsítványt kér, a titkosított jelszót, a tanúsítványt és az eszköz nyilvános kulcsát elküldi az összekötőnek.  Az összekötő visszafejti a jelszót a helyszíni titkos kulccsal, majd újratitkosítja a jelszót (és minden plist-profilt, ha iOS-et használ) az eszköz kulcsával, mielőtt elküldené a tanúsítványt az Intune-nak.  Az Intune ezután továbbítja a tanúsítványt az eszköznek, és az eszköz visszafejti azt az eszköz titkos kulcsával, és telepítheti a tanúsítványt.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>A PFX tanúsítvány-összekötő letöltése, telepítése és konfigurálása Microsoft Intune

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **tanúsítvány-összekötők** > **Hozzáadás**lehetőséget.

   ![PFX tanúsítvány-összekötő Microsoft Intune letöltéshez](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

3. Kövesse az útmutatást, hogy letöltse a *pfx tanúsítvány-összekötőt a Microsoft Intune* egy olyan helyre, amely elérhető a kiszolgálóról, amelyen az összekötőt telepíteni fogja.

4. A letöltés befejezése után jelentkezzen be a kiszolgálóra, és futtassa a telepítőt (PfxCertificateConnectorBootstrapper. exe).  
   - Ha elfogadja az alapértelmezett telepítési helyet, az összekötő telepíti a `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - Az összekötő-szolgáltatás a helyi rendszerfiók alatt fut. Ha egy proxyra van szükség az internet-hozzáféréshez, ellenőrizze, hogy a helyi szolgáltatásfiók hozzáférhet-e a proxy beállításaihoz a kiszolgálón.

5. A Microsoft Intune-hoz készült PFX tanúsítvány-összekötő telepítés után megnyitja a **Regisztráció** lapot. Az Intune-hoz való kapcsolódás engedélyezéséhez **Jelentkezzen be**, és adjon meg egy globális Azure-rendszergazdai vagy Intune-rendszergazdai engedélyekkel rendelkező fiókot.

   > [!WARNING]
   > Alapértelmezés szerint a Windows Server **IE fokozott biztonsági beállításai** beállítás értéke **, amely az** Office 365-be való bejelentkezéssel kapcsolatos problémákat okozhat.

6. Zárja be az ablakot.

7. A Microsoft Endpoint Manager felügyeleti központban térjen vissza a **bérlői adminisztráció** > **Összekötők és tokenek** > **tanúsítvány-összekötők**elemre. Néhány pillanat múlva megjelenik egy zöld pipa, és a kapcsolatok állapota frissül. Az összekötő-kiszolgáló mostantól képes kommunikálni az Intune-nal.

## <a name="import-pfx-certificates-to-intune"></a>PFX-tanúsítványok importálása az Intune-ba

A [Microsoft Graph](https://docs.microsoft.com/graph) használatával importálhatja a felhasználók pfx-tanúsítványait az Intune-ba. A [GitHub segítő PFXImport PowerShell-projektje](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) olyan parancsmagokat biztosít, amelyek megkönnyítik a műveletek elvégzését.

Ha inkább a Graph használatával szeretné használni saját egyéni megoldását, használja a [userPFXCertificate erőforrástípust](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>"PFXImport PowerShell Project"-parancsmagok létrehozása

A PowerShell-parancsmagok használatához saját maga hozza létre a projektet a Visual Studióval. A folyamat egyenesen előre, míg a kiszolgálón futtatható, javasoljuk, hogy futtassa azt a munkaállomáson.  

1. Nyissa meg az [Intune-erőforrás-hozzáférés](https://github.com/microsoft/Intune-Resource-Access) tárház gyökerét a githubon, majd töltse le vagy klónozással a tárházat a git használatával a gépre.

   ![GitHub Letöltés gomb](./media/certificates-imported-pfx-configure/github-download.png)

2. Lépjen a `.\Intune-Resource-Access-develop\src\PFXImportPowershell\`ra, és nyissa meg a projektet a Visual Studióval a **PFXImportPS. SLN**fájl használatával.

3. A felső részen váltson **hibakeresésről** **kiadásra**.

4. Nyissa meg a **Build** elemet, és válassza a **PFXImportPS létrehozása**lehetőséget. Néhány pillanat elteltével megjelenik a **Létrehozás sikeres** megerősítése a Visual Studio bal alsó sarkában.

   ![Visual Studio-Build lehetőség](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. A létrehozási folyamat egy új mappát hoz létre a PowerShell-modullal `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Ezt a **kiadási** mappát fogja használni a következő lépésekhez.

### <a name="create-the-encryption-public-key"></a>A titkosítás nyilvános kulcsának létrehozása

PFX-tanúsítványokat és titkos kulcsokat importálhat az Intune-ba. A titkos kulcs védelmét biztosító jelszó a helyszínen tárolt nyilvános kulccsal van titkosítva. A nyilvános/titkos kulcspár létrehozásához és tárolásához használhatja a Windows-titkosítást, a hardveres biztonsági modult vagy más típusú titkosítást is.  A használt titkosítási típustól függően a nyilvános/titkos kulcspár a biztonsági mentéshez fájlformátum formátumban is exportálható.

A PowerShell-modul módszereket biztosít a kulcsok Windows-titkosítással történő létrehozására. Emellett más eszközöket is használhat a kulcsok létrehozásához.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>A titkosítási kulcs létrehozása Windows-kriptográfia használatával

1. Másolja a Visual Studio által létrehozott *kiadási* mappát arra a kiszolgálóra, amelyre a **pfx tanúsítvány-összekötőt telepítette Microsoft Intunehoz**. Ez a mappa tartalmazza a PowerShell-modult.

2. A kiszolgálón nyissa meg a *PowerShellt* rendszergazdaként, majd navigáljon a PowerShell-modult tartalmazó *kiadási* mappához.

3. A modul importálásához futtassa `Import-Module .\IntunePfxImport.psd1` a modul importálásához.

4. Következő lépésként futtassa `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]
   > A PFX-tanúsítványok importálásakor a használt szolgáltatót újra ki kell választani. Használhatja a **Microsoft szoftveres kulcstároló-szolgáltatót**, bár más szolgáltató használata is támogatott. A kulcs neve is megjelenik példaként, és használhat más nevet is.

   Ha azt tervezi, hogy a munkaállomásról importálja a tanúsítványt, akkor a következő paranccsal exportálhatja a kulcsot egy fájlba: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path\Filename.PFX>"`

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
  - oaepSha256
  - oaepSha384
  - oaepSha512

Válassza ki azt a kulcstároló-szolgáltatót, amely megfelel a kulcs létrehozásához használt szolgáltatónak.

#### <a name="to-import-the-pfx-certificate"></a>A PFX-tanúsítvány importálása  

1. Exportálja a tanúsítványokat bármely hitelesítésszolgáltatótól (CA) a szolgáltató dokumentációjának követésével.  A Microsoft Active Directory tanúsítványszolgáltatás esetében [ezt a parancsfájlt](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b)használhatja.

2. A kiszolgálón nyissa meg a *PowerShellt* rendszergazdaként, majd navigáljon a PowerShell-modult tartalmazó *kiadási* mappához.

3. A modul importálásához futtassa `Import-Module .\IntunePfxImport.psd1`

4. Az Intune Graph-ban való hitelesítéshez futtassa `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Mivel a hitelesítés a gráfon fut, engedélyeket kell biztosítania a AppID. Ha első alkalommal használta ezt a segédprogramot, *globális rendszergazdai jogosultsággal* kell rendelkeznie. A PowerShell-parancsmagok ugyanazt a AppID használják, mint a [PowerShell Intune-mintákkal](https://github.com/microsoftgraph/powershell-intune-samples).

5. Konvertálja a jelszót minden PFX-fájlhoz, amelyet importál egy biztonságos karakterláncba `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`futtatásával.

6. **UserPFXCertificate** objektum létrehozásához futtassa `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>"`

   Például így: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption"`

   > [!NOTE]
   > Ha az összekötőt futtató kiszolgálótól eltérő rendszerből importálja a tanúsítványt, akkor a következő parancsot kell használnia, amely tartalmazza a kulcsfájl elérési útját: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. A **UserPFXCertificate** objektum importálása az Intune-ba `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject` futtatásával

8. A tanúsítvány érvényesítéséhez futtassa a következőt `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`

További információ az egyéb elérhető parancsokról: a [PFXImport PowerShell-projekt](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)információs fájlja a githubon.

## <a name="create-a-pkcs-imported-certificate-profile"></a>Importált PKCS-tanúsítványprofil létrehozása

A tanúsítványok Intune-ba importálása után hozzon létre egy **Importált PKCS-tanúsítvány** profilt, és rendelje hozzá Azure Active Directory-csoportokhoz.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profil** > **létrehozási profil**lehetőséget.

3. Adja meg a következő tulajdonságokat:

   - **Név** a profil számára
   - Igény szerint hozzáadhat egy leírást
   - **Platform**, amelyen telepíteni kell a profilt
   - A **Profiltípust** állítsa **Importált PKCS-tanúsítványra**

4. Válassza a **Beállítások**lehetőséget, és adja meg a következő tulajdonságokat:

   - **Felhasználási cél**: Itt adhatja meg a profilhoz importált tanúsítványok kívánt célját. A rendszergazdák más felhasználási célokra is importálhatók tanúsítványokat (például S/MIME-aláírás vagy S/MIME-titkosítás). A tanúsítványprofilban kijelölt felhasználási cél alapján lesznek párosítva a megfelelő importált tanúsítványok. A felhasználási cél az importált tanúsítványok együttes csoportosítása, és nem garantálja, hogy az adott címkével importált tanúsítványok megfelelnek a kívánt célnak.  
   - **Tanúsítvány érvényességi időtartama**: Ha az érvényességi időszak nem módosult a tanúsítványsablon esetében, ez a beállítás alapértelmezés szerint egy év.
   - **Kulcstároló-szolgáltató (KSP)** : Windows rendszer esetén válasszon helyet a kulcsok tárolására az eszközön.

5. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.

## <a name="support-for-third-party-partners"></a>Harmadik féltől származó partnerek támogatása

A következő partnerek olyan támogatott módszereket vagy eszközöket biztosítanak, amelyekkel PFX-tanúsítványokat importálhat az Intune-ba.

### <a name="digicert"></a>DigiCert
Ha a DigiCert PKI platform szolgáltatást használja, az **Intune S/MIME-tanúsítványok DigiCert importálási eszköze** segítségével importálhatja a pfx-tanúsítványokat az Intune-ba. Az eszköz használata lecseréli a [pfx-tanúsítványok importálása az Intune](#import-pfx-certificates-to-intune) -ba című szakaszban ismertetett utasításokat a jelen cikk korábbi részében leírtak szerint.

Ha többet szeretne megtudni a DigiCert importálási eszközről, beleértve az eszköz beszerzésének módját, tekintse meg a https://knowledge.digicert.com/tutorials/microsoft-intune.html a DigiCert Tudásbázisban.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Az új eszköz profiljának [kiosztása](../configuration/device-profile-assign.md) .
