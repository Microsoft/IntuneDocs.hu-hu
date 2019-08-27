---
title: Magán-és nyilvános kulcsú tanúsítványok használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: Nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványok hozzáadása vagy létrehozása Microsoft Intuneekkel, beleértve a főtanúsítvány exportálásának lépéseit, a tanúsítványsablon konfigurálását, a letöltést és az Intune Certificate Connector (NDES) telepítését, valamint az eszköz létrehozását konfigurációs profil, és hozzon létre egy PKCS-tanúsítvány profilt az Azure-ban és a hitelesítésszolgáltatóban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cda32e72956e5998d5ebc8d8bed2baea39951ec
ms.sourcegitcommit: 58a22f1b4a3fffffb1f7da228f470b3b0774fc42
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/26/2019
ms.locfileid: "70021805"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>PKCS-tanúsítványok konfigurálása és használata az Intune-nal

Az Intune támogatja a magán-és nyilvános kulcspár-(PKCS-) tanúsítványok használatát. Ez a cikk segítséget nyújt a szükséges infrastruktúra, például a helyszíni tanúsítvány-összekötők konfigurálásához, a PKCS-tanúsítvány exportálásához, majd a tanúsítvány hozzáadásához az Intune-eszköz konfigurációs profiljához.

A Microsoft Intune beépített beállításokat tartalmaz a PKCS-tanúsítványok használatára a szervezet erőforrásaihoz való hozzáféréshez és hitelesítéshez. A tanúsítványok hitelesítése és biztonságos hozzáférés a vállalati erőforrásokhoz, például VPN-hez vagy WiFi-hálózathoz. Ezeket a beállításokat az Intune-ban az eszköz konfigurációs profiljait használó eszközökre kell telepíteni.


## <a name="requirements"></a>Követelmények

A PKCS-tanúsítványok Intune-nal való használatához a következő infrastruktúrára lesz szüksége:

- **Active Directory tartomány**:  
  Az ebben a szakaszban felsorolt összes kiszolgálónak csatlakoznia kell a Active Directory tartományhoz.

  A Active Directory tartományi szolgáltatások (AD DS) telepítésével és konfigurálásával kapcsolatos további információkért lásd: [AD DS tervezés és tervezés](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Hitelesítésszolgáltató**:  
   Vállalati hitelesítésszolgáltató (CA).

  A Active Directory tanúsítványszolgáltatások (AD CS) telepítésével és konfigurálásával kapcsolatos információkért tekintse meg a következő témakört: [Active Directory tanúsítványszolgáltatások lépésenkénti útmutatója](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > Az Intune követelményei szerint az AD CS-t vállalati hitelesítésszolgáltatóval, és nem önálló hitelesítésszolgáltatóval kell futtatni.

- **Ügyfél**:  
  A vállalati HITELESÍTÉSSZOLGÁLTATÓhoz való kapcsolódáshoz.

- **Főtanúsítvány**:  
  Vállalati hitelesítésszolgáltatótól származó főtanúsítvány exportált másolata.

- **Microsoft Intune tanúsítvány-összekötő** (más néven az *NDES Certificate Connector*):  
  Az Intune-portálon válassza az **eszközök konfigurációs** > **tanúsítvány összekötők** > **Hozzáadás**lehetőséget, majd kövesse a *lépéseket az összekötő PKCS #12 telepítéséhez*. Az **NDESConnectorSetup. exe**tanúsítvány-összekötő telepítőjének letöltéséhez használja a portál letöltési hivatkozását.  

  Az Intune-ban az összekötő legfeljebb 100 példánya támogatott a bérlőn, és mindegyik példány külön Windows-kiszolgálón található. Az összekötő egy példányát telepítheti ugyanarra a kiszolgálóra, mint a PFX tanúsítvány-összekötő példánya Microsoft Intune. Ha több összekötőt használ, az összekötő-infrastruktúra támogatja a magas rendelkezésre állást és a terheléselosztást, mivel bármely elérhető összekötő-példány feldolgozhatja a PKCS-tanúsítványkérelmek kérelmeit. 

  Ez az összekötő a hitelesítéshez vagy az S/MIME e-mailek aláírásához használt PKCS-tanúsítványkérelmek feldolgozását végzi.

  A Microsoft Intune Tanúsítvány-összekötő támogatja a Federal Information Processing standard (FIPS) üzemmódot is. A FIPS nem szükséges, de ha engedélyezve van, akkor lehetőség van tanúsítványok kibocsátására és visszavonására.

- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**:  
  Ha az S/MIME e-mailek titkosítását tervezi használni, az Intune-portálon töltheti le az *importált pfx*-tanúsítványokhoz tartozó összekötőt.  Nyissa meg az **eszköz konfigurációs** > **tanúsítvány** > -összekötők**Hozzáadás**lehetőséget, és kövesse a *lépéseket az importált pfx-tanúsítványokhoz tartozó összekötő telepítéséhez*. Az **PfxCertificateConnectorBootstrapper. exe**telepítőjének letöltéséhez használja a portál letöltési hivatkozását. 

  Minden Intune-bérlő támogatja az összekötő egyetlen példányát. Ezt az összekötőt telepítheti ugyanarra a kiszolgálóra, mint az Microsoft Intune Certificate Connector példánya.

  Ez az összekötő kezeli az Intune-ba importált PFX-fájlok kéréseit egy adott felhasználó számára az S/MIME e-mail-titkosításhoz.  

  Ez az összekötő automatikusan képes frissíteni magát, ha új verziók válnak elérhetővé. A frissítési képesség használatához a következőket kell tennie:
  - Telepítse az importált PFX tanúsítvány-összekötőt Microsoft Intune a kiszolgálón.  
  - A fontos frissítések automatikus fogadásához győződjön meg arról, hogy a tűzfalak nyitva vannak, amelyek lehetővé teszik, hogy az összekötő kapcsolatba lépjen a **443**-es port **AutoUpdate.msappproxy.net** .   

  További információ az összekötő által elérhető összes hálózati végpontról: [Microsoft Intune tanúsítvány-összekötő](intune-endpoints.md#microsoft-intune-certificate-connector).

- **Windows Server**:  
  Windows-kiszolgálót használ a gazdagéphez:

  - Microsoft Intune Tanúsítvány-összekötő – hitelesítéshez és S/MIME e-mail aláírási forgatókönyvekhez
  - PFX tanúsítvány-összekötő a Microsoft Intunehoz – S/MIME e-mail titkosítási forgatókönyvek esetén.

  Mindkét összekötőt (*Microsoft Intune tanúsítvány-összekötő* és *pfx tanúsítvány*-összekötőt) is telepítheti ugyanarra a kiszolgálóra.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Főtanúsítvány exportálása a vállalati hitelesítésszolgáltatótól

VPN-, WiFi-vagy más erőforrásokkal rendelkező eszköz hitelesítéséhez az eszköznek szüksége van egy gyökérszintű vagy köztes HITELESÍTÉSSZOLGÁLTATÓI tanúsítványra. Az alábbi lépések ismertetik a szükséges tanúsítvány beszerzését a vállalati hitelesítésszolgáltatótól.

**Parancssor használata**:  
1. Jelentkezzen be a legfelső szintű hitelesítésszolgáltató kiszolgálóra rendszergazdai fiókkal.
 
2. Nyissa meg a **Start** > **Run**parancsot, majd írja be a **cmd** parancsot a parancssor megnyitásához. 
    
3. A legfelső szintű tanúsítvány *ca_name. cer*nevű fájlként való exportálásához a **Certutil-CA. CERT ca_name. cer** fájlt kell megadni.



## <a name="configure-certificate-templates-on-the-ca"></a>Tanúsítványsablonok konfigurálása a HITELESÍTÉSSZOLGÁLTATÓN

1. Jelentkezzen be a vállalati hitelesítésszolgáltatóhoz egy rendszergazdai jogosultságokkal rendelkező fiókkal.
2. Nyissa meg a **Hitelesítésszolgáltató** konzolt, majd kattintson a jobb gombbal a **Tanúsítványsablonok** elemre, és válassza a **Kezelés** lehetőséget.
3. Keresse meg a **Felhasználó** tanúsítványsablont, kattintson rá a jobb gombbal, majd válassza a **Sablon megkettőzése** lehetőséget. Ekkor megnyílik az **Új sablon tulajdonságai** terület.

    > [!NOTE]
    > S/MIME e-mail-aláírás és titkosítás esetén sok rendszergazda külön tanúsítványt használ az aláíráshoz és a titkosításhoz. Ha a Microsoft Active Directory Tanúsítványszolgáltatást használja, akkor használhatja az **Exchange Signature Only** (csak Exchange-aláírás) sablont S/MIME e-mail-aláírási tanúsítványokhoz, és az **Exchange User** (Exchange felhasználó) sablont S/MIME titkosítási tanúsítványokhoz.  Ha harmadik féltől származó hitelesítésszolgáltatót használ, javasoljuk, hogy tekintse át az aláírási és titkosítási sablonok beállításához szükséges útmutatást.

4. A **Kompatibilitás** lapon:

    - Állítsa a **Hitelesítésszolgáltató** beállítást **Windows Server 2008 R2** értékre.
    - Állítsa a **Tanúsítvány kezdeményezettje** beállítást **Windows 7 / Server 2008 R2** értékre.

5. Állítsa be az **Általános** lapon a **Sablon megjelenítendő neve** beállítást egy aktuális névre.

    > [!WARNING]
    > A **Sablon neve** alapértelmezés szerint ugyanaz, mint a **Sablon megjelenítendő neve**, *szóköz nélkül*. Jegyezze fel a sablon nevét, mert később szüksége lesz rá.

6. A **Kérelmek kezelése** lapon válassza **A titkos kulcs exportálható** beállítást.
7. A **Titkosítás** lapon ellenőrizze, hogy a **Minimális kulcshossz** értéke 2048.
8. A **Tulajdonos neve** lapon válassza a **Kérelemben megadva** lehetőséget.
9. A **Bővítmények** lapon ellenőrizze, hogy az **Alkalmazásszabályzatok** területen láthatók-e a következő elemek: Titkosított fájlrendszer, Biztonságos e-mail, Ügyfél-hitelesítés.

    > [!IMPORTANT]
    > iOS-tanúsítványsablonok esetén a **Kiterjesztések** lapon frissítse a **Kulcshasználat** beállítást, és ügyeljen rá, hogy **Az aláírás igazolja az eredetet** jelölőnégyzet ne legyen bejelölve.

10. A **Biztonság** lapon vegye fel annak a kiszolgálónak a fiókját, amelyen telepíti a Microsoft Intune Tanúsítvány-összekötőt. Adja meg a fiók számára az **Olvasás** és **Beléptetés** engedélyeket.
11. A tanúsítvány mentéséhez válassza ki az **Alkalmaz** > **OK** elemet. Zárja be a **Tanúsítvány-sablonok konzolt**.
12. A **Hitelesítésszolgáltató** konzolon kattintson a jobb gombbal a **Tanúsítványsablonok** > **Új** > **Kiállítandó tanúsítványsablon** elemre. Válassza ki az iménti lépésekben létrehozott sablont. Kattintson az **OK** gombra.
13. Ahhoz, hogy a kiszolgáló kezelhesse a regisztrált eszközök és felhasználók tanúsítványait, kövesse az alábbi lépéseket:

    1. Kattintson a jobb gombbal a hitelesítésszolgáltatóra, majd kattintson a **Tulajdonságok** elemre.
    2. A biztonság lapon vegye fel annak a kiszolgálónak a fiókját, amelyen az összekötőket (**Microsoft Intune Tanúsítvány-összekötő** vagy **Microsoft Intune-hoz készült PFX tanúsítvány-összekötő**) futtatja. 
    3. A fiók számára adja meg a **Tanúsítványok kiadása és kezelése** és a **Tanúsítványkérés** engedélyeket.

14. Jelentkezzen ki a vállalati hitelesítésszolgáltatóból.

## <a name="download-install-and-configure-the-certificate-connectors"></a>A tanúsítvány-összekötők letöltése, telepítése és konfigurálása

### <a name="microsoft-intune-certificate-connector"></a>A Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> A Microsoft Intune Tanúsítvány-összekötő nem telepíthető a kiállító hitelesítésszolgáltatóra (CA), hanem külön Windows Serverre kell telepíteni.  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz konfigurációja** > **tanúsítvány-összekötők** > **Hozzáadás**lehetőséget.
3. Töltse le és mentse az összekötő-fájlt egy olyan helyre, amely a-összekötő telepítéséhez használt kiszolgálóról érhető el.

    ![Microsoft Intune Tanúsítvány-összekötő Letöltés](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. A letöltés befejezése után jelentkezzen be a kiszolgálóra. Ha ez megvan:

    1. Győződjön meg róla, hogy telepítve van-e a .NET keretrendszer 4.5 vagy újabb verziója, mivel arra szüksége van az NDES tanúsítvány-összekötőjének. A .NET 4.5-keretrendszer automatikusan részen a Windows Server 2012 R2 és újabb verzióknak.
    2. Futtassa a telepítőprogramot (NDESConnectorSetup.exe), és fogadja el az alapértelmezett helyet. A telepítő az összekötőt a `\Program Files\Microsoft Intune\NDESConnectorUI` helyen telepíti. A Telepítőbeállítás oldalon válassza a **PFX terjesztése**, lehetőséget. Folytassa és fejezze be a telepítést.
    3. Az összekötő-szolgáltatás alapértelmezés szerint a helyi rendszerfiók alatt fut. Ha az Internet eléréséhez proxy szükséges, akkor győződjön meg arról, hogy a helyi szolgáltatásfiók hozzáfér a proxy-beállításokhoz a kiszolgálón.

5. A Microsoft Intune Tanúsítvány-összekötő megnyitja a **beléptetés** lapot. Az Intune-hoz való kapcsolódás engedélyezéséhez válassza a **Bejelentkezés** lehetőséget, és adjon meg egy globális rendszergazdai engedélyekkel rendelkező fiókot.
6. Javasoljuk, hogy a **Speciális** lapon hagyja kijelölve az **E számítógép SYSTEM fiókjának a használata (alapértelmezett)** beállítást.
7. **Alkalmaz** > **Bezárás**
8. Térjen vissza az Intune-portálra (**Intune** > -**eszköz konfigurációs** > **tanúsítvány**-összekötők). Néhány pillanat múlva megjelenik egy zöld pipa jel, és a **kapcsolatok állapota** **aktív**. Az összekötő kiszolgáló mostantól kapcsolatba tud lépni az Intune-nal.
9. Ha a hálózati környezetben van webproxyja, további konfigurációkra lehet szükség az összekötő működésének engedélyezéséhez. További információ: a [meglévő helyszíni proxykiszolgálók használata](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) az Azure Active Directory dokumentációjában.

> [!NOTE]  
> A Microsoft Intune Tanúsítvány-összekötő a TLS 1,2-et támogatja. Ha a TLS 1,2 telepítve van az összekötőt futtató kiszolgálón, az összekötő a TLS 1,2-et használja. Ellenkező esetben a TLS 1,1 használatos. Az eszközök és a kiszolgáló közötti hitelesítéshez jelenleg a TLS 1.1 van használatban.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>A Microsoft Intune-hoz készült PFX tanúsítvány-összekötő

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza ki az **eszköz konfigurációja** > **tanúsítvány** > -összekötők**hozzáadása** elemet.
3. Töltse le és mentse a Microsoft Intune-hoz készült PFX tanúsítvány-összekötőt. Mentse egy olyan helyre, amely elérhető a kiszolgálóról, amelyre az összekötő telepítve lesz.
4. A letöltés befejezése után jelentkezzen be a kiszolgálóra. Ha ez megvan:

    1. Győződjön meg róla, hogy telepítve van-e a .NET keretrendszer 4.6 vagy újabb verziója, mivel arra szüksége van a Microsoft Intune-hoz készült PFX tanúsítvány-összekötőnek. Ha a .NET 4.6 keretrendszer nincs telepítve, akkor a telepítő automatikusan telepíti.
    2. Futtassa a telepítőt (PfxCertificateConnectorBootstrapper. exe), és fogadja el az alapértelmezett helyet, amely telepíti `Program Files\Microsoft Intune\PFXCertificateConnector`az összekötőt a következőre:.
    3. Az összekötő-szolgáltatás a helyi rendszerfiók alatt fut. Ha proxy szükséges az Internet eléréséhez, akkor győződjön meg arról, hogy a helyi szolgáltatásfiók hozzáfér a proxy-beállításokhoz a kiszolgálón.

5. A Microsoft Intune-hoz készült PFX tanúsítvány-összekötő telepítés után megnyitja a **Regisztráció** lapot. Az Intune-hoz való kapcsolódás engedélyezéséhez **Jelentkezzen be**, és adjon meg egy globális Azure-rendszergazdai vagy Intune-rendszergazdai engedélyekkel rendelkező fiókot.
6. Zárja be az ablakot.
7. Térjen vissza a Azure Portalhoz (**Intune** > -**eszköz konfigurációs** > **tanúsítvány**-összekötők). Néhány pillanat múlva megjelenik egy zöld pipa jel, és a **kapcsolatok állapota** **aktív**. Az összekötő kiszolgáló mostantól kapcsolatba tud lépni az Intune-nal.

## <a name="create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozása

1. Az [Azure Portalon](https://portal.azure.com) lépjen az **Intune** > **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** menüponthoz.
    ![Navigáljon az Intune-hoz, és hozzon létre egy új profilt egy megbízható tanúsítványhoz](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Adja meg a következő tulajdonságokat:

    - **Név** a profil számára
    - Igény szerint hozzáadhat egy leírást
    - **Platform**, amelyen telepíteni kell a profilt
    - A **Profiltípust** állítsa **Megbízható tanúsítványra**

3. Nyissa meg a **Beállítások** lapot, és adja meg a korábban exportált hitelesítésszolgáltatói főtanúsítvány .cer fájlját.

   > [!NOTE]
   > A **2. lépésben**kiválasztott platformtól függően előfordulhat, hogy nem rendelkezik a tanúsítvány **célhelyének** kiválasztására szolgáló lehetőséggel.

   ![Profil létrehozása és megbízható tanúsítvány feltöltése](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.
5. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>PKCS-tanúsítványprofil létrehozása

1. Az [Azure Portalon](https://portal.azure.com) lépjen az **Intune** > **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** menüponthoz.
2. Adja meg a következő tulajdonságokat:

    - **Név** a profil számára
    - Igény szerint hozzáadhat egy leírást
    - **Platform**, amelyen telepíteni kell a profilt
    - A **Profiltípust** állítsa **PKCS-tanúsítványra**

3. Nyissa meg a **Beállítások** lapot, és adja meg a következő tulajdonságokat:

    - **Megújítási küszöb (%)** : Ajánlott érték: 20%.
    - **Tanúsítvány érvényességi időtartama**: Ha nem módosította a tanúsítványsablont, akkor ez a beállítás egy évig állítható be.
    - **Kulcstároló-szolgáltató (KSP)** : Windows esetén válassza ki a kulcsok tárolásának helyét az eszközön.
    - **Hitelesítésszolgáltató**: Megjeleníti a vállalati HITELESÍTÉSSZOLGÁLTATÓ belső teljes tartománynevét (FQDN).
    - **Hitelesítésszolgáltató neve**: Felsorolja a vállalati HITELESÍTÉSSZOLGÁLTATÓ nevét, például a "contoso hitelesítésszolgáltató" nevet.
    - **Tanúsítványsablon neve**: A korábban létrehozott sablon neve. Emlékeztető: a **Sablon neve** alapértelmezés szerint ugyanaz, mint a **Sablon megjelenítendő neve**, *szóköz nélkül*.
    - **Tulajdonos nevének formátuma**: Ha ez a beállítás nem kötelező, adja meg a **köznapi nevet** .
    - **Tulajdonos alternatív neve**: Ha ez a beállítás nem kötelező, adja meg az egyszerű felhasználónév **(UPN)** beállítást.

4. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.
5. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](device-profile-assign.md).

   > [!NOTE]
   > Az androidos vállalati profillal rendelkező eszközökön a PKCS-tanúsítvány profil használatával telepített tanúsítványok nem láthatók az eszközön. A tanúsítvány sikeres központi telepítésének megerősítéséhez ellenőrizze a profil állapotát az Intune-konzolon.

## <a name="create-a-pkcs-imported-certificate-profile"></a>Importált PKCS-tanúsítványprofil létrehozása

A korábban kiadott tanúsítványokat importálhatja egy adott felhasználóhoz bármely, az Intune-ban lévő HITELESÍTÉSSZOLGÁLTATÓTÓL. Az importált tanúsítványok a felhasználó által regisztrált valamennyi eszközre telepítve lesznek. A leggyakrabban S/MIME e-mail-titkosításhoz importálnak meglévő PFX-tanúsítványokat az Intune-ba. Egy felhasználónak számos tanúsítványa lehet az e-mailek titkosítására. Ezen tanúsítványok titkos kulcsainak a felhasználó összes eszközén meg kell lenniük, hogy fel tudják oldani a korábban titkosított e-mailek titkosítását.

A tanúsítványok Intune-ba való importálásához használhatja [a GitHubon rendelkezésre álló PowerShell-parancsmagokat](https://github.com/Microsoft/Intune-Resource-Access).

A tanúsítványok Intune-ba importálása után hozzon létre egy **Importált PKCS-tanúsítvány** profilt, és rendelje hozzá Azure Active Directory-csoportokhoz.

1. Az [Azure Portalon](https://portal.azure.com) lépjen az **Intune** > **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** menüponthoz.
2. Adja meg a következő tulajdonságokat:

    - **Név** a profil számára
    - Igény szerint hozzáadhat egy leírást
    - **Platform**, amelyen telepíteni kell a profilt
    - A **Profiltípust** állítsa **Importált PKCS-tanúsítványra**

3. Nyissa meg a **Beállítások** lapot, és adja meg a következő tulajdonságokat:

    - **Felhasználási cél**: A profilhoz importált tanúsítványok rendeltetési célja. Előfordulhat, hogy egy rendszergazda más célra (például hitelesítésre, S/MIME-aláírásra vagy S/MIME-titkosításra) szánt tanúsítványokat importált. A tanúsítványprofilban kijelölt felhasználási cél alapján lesznek párosítva a megfelelő importált tanúsítványok.
    - **Tanúsítvány érvényességi időtartama**: Ha nem módosította a tanúsítványsablont, akkor ez a beállítás egy évig állítható be.
    - **Kulcstároló-szolgáltató (KSP)** : Windows esetén válassza ki a kulcsok tárolásának helyét az eszközön.

4. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.
5. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](device-profile-assign.md).

## <a name="whats-new-for-connectors"></a>Az összekötők újdonságai
A két tanúsítvány-összekötő frissítései rendszeresen jelennek meg. Amikor frissítünk egy összekötőt, itt olvashat a változásokról. 

A *pfx-tanúsítványok összekötője Microsoft Intune* [támogatja az automatikus frissítéseket](#requirements), az *Intune tanúsítvány-összekötő* pedig manuálisan frissül.

### <a name="may-17-2019"></a>Május 17., 2019  
- **PFX-tanúsítványok összekötője Microsoft Intune-Version 6.1905.0.404**  
  Változások ebben a kiadásban:  
  - Kijavítva a probléma, hogy a meglévő PFX-tanúsítványok továbbra is újra fel lesznek dolgozva, ami miatt az összekötő leállítja az új kérések feldolgozását. 

### <a name="may-6-2019"></a>2019. május 6.  
- **PFX-tanúsítványok összekötője Microsoft Intune-Version 6.1905.0.402**  
  Változások ebben a kiadásban:  
  - Az összekötő lekérdezési időköze 5 perctől 30 másodpercre van csökkentve.
 
### <a name="april-2-2019"></a>2019. április 2.  
- **Intune tanúsítvány-összekötő – verzió 6.1904.1.0**  
  Változások ebben a kiadásban:  
  - Kijavított egy hibát, amely miatt előfordulhat, hogy az összekötő nem tud regisztrálni az Intune-ba, miután bejelentkezett az összekötőbe egy globális rendszergazdai fiókkal.  
  - A tanúsítvány visszavonására vonatkozó megbízhatósági javításokat tartalmaz.  
  - Teljesítménnyel kapcsolatos javításokat tartalmaz, amelyekkel növelheti a PKCS-tanúsítványkérelmek feldolgozásának gyors módját.  

- **PFX-tanúsítványok összekötője Microsoft Intune-Version 6.1904.0.401**
  > [!NOTE]  
  > A PFX-összekötő ezen verziójának automatikus frissítése 2019 április 11-én nem érhető el.  

  Változások ebben a kiadásban:  
  - Kijavított egy hibát, amely miatt előfordulhat, hogy az összekötő nem tud regisztrálni az Intune-ba, miután bejelentkezett az összekötőbe egy globális rendszergazdai fiókkal.  


## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

[Használjon SCEP](certificates-scep-configure.md)-tanúsítványokat, vagy [adjon ki PKCS-tanúsítványokat egy Digicert PKI Manager](certificates-digicert-configure.md)webszolgáltatásból.


