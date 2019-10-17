---
title: Infrastruktúra konfigurálása a SCEP-tanúsítvány-profilok támogatásához a Microsoft Intune-Azure használatával | Microsoft Docs
description: Ha a SCEP-t a Microsoft Intuneban szeretné használni, konfigurálja a helyszíni AD-tartományt, hozzon létre egy hitelesítésszolgáltatót, állítsa be a NDES-kiszolgálót, és telepítse az Intune tanúsítvány-összekötőt.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82177e475c6f5a637aba9f053e64986dcd9bdadf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502552"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Infrastruktúra konfigurálása az Intune-nal való SCEP támogatásához  
  
Az Intune a Egyszerű tanúsítványigénylési protokoll (SCEP) használatát támogatja az [alkalmazások és a vállalati erőforrások kapcsolatainak hitelesítéséhez](certificates-configure.md). A SCEP a hitelesítésszolgáltató (CA) tanúsítványát használja a tanúsítvány-aláírási kérelem (CSR) üzenetváltásának biztonságossá tételéhez. Ha az infrastruktúra támogatja a SCEP-t, az Intune *SCEP-tanúsítvány* -profiljaival (az Intune-ban) használhatja a tanúsítványokat az eszközökre. Active Directory tanúsítványszolgáltatás hitelesítésszolgáltató használata esetén a Microsoft Intune Tanúsítvány-összekötő a SCEP-tanúsítványok Intune-nal való használatához szükséges. [Harmadik féltől származó hitelesítésszolgáltatók](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)használata esetén nincs szükség az összekötőre.  

A cikkben található információk segítségével úgy konfigurálhatja az infrastruktúrát, hogy támogassa a SCEP a Active Directory tanúsítványszolgáltatás használatakor. Az infrastruktúra konfigurálása után [SCEP-tanúsítványokat hozhat létre és telepíthet](certificates-profile-scep.md) az Intune-nal.  

> [!TIP]  
> Az Intune a [nyilvános kulcsú titkosítási szabványok #12 tanúsítványok](certficates-pfx-configure.md)használatát is támogatja.  


## <a name="prerequisites-for-using-scep-for-certificates"></a>A tanúsítványok SCEP használatának előfeltételei  
A folytatás előtt győződjön meg arról, hogy [létrehozta és telepítette a *megbízható* ](certificates-configure.md#export-the-trusted-root-ca-certificate) SCEP a tanúsítvány-profilokat használó eszközökön. A SCEP tanúsítvány-profilok közvetlenül hivatkoznak arra a megbízható tanúsítvány-profilra, amelyet az eszközök megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvánnyal való kiosztására használ.  

### <a name="servers-and-server-roles"></a>Kiszolgálók és kiszolgálói szerepkörök  
A következő helyszíni infrastruktúrának olyan kiszolgálókon kell futnia, amelyek tartományhoz csatlakoznak a Active Directoryhoz, a webalkalmazás-proxy kiszolgáló kivételével.  
- **Hitelesítésszolgáltató** – használjon olyan Microsoft Active Directory tanúsítványszolgáltatások vállalati HITELESÍTÉSSZOLGÁLTATÓT (CA), amely a Windows Server 2008 R2 Service Pack 1 vagy újabb verziójának Enterprise kiadásán fut. A használt Windows Server-verziónak a Microsoft által támogatottnak kell maradnia. Az önálló hitelesítésszolgáltató nem támogatott. További információ: [a hitelesítésszolgáltató telepítése](https://technet.microsoft.com/library/jj125375.aspx). Ha a HITELESÍTÉSSZOLGÁLTATÓ a Windows Server 2008 R2 SP1 verziót futtatja, [a gyorsjavítást a KB2483564-ből kell telepítenie](https://support.microsoft.com/kb/2483564/).  

- **NDES kiszolgálói szerepkör** – a Windows Server 2012 R2 vagy újabb verzióban konfigurálnia kell egy hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) kiszolgálói szerepkörét. A cikk későbbi részében végigvezeti Önt a [NDES telepítésének](#set-up-ndes)lépésein.  

  - A NDES-t futtató kiszolgálónak tartományhoz kell csatlakoznia, és a vállalati HITELESÍTÉSSZOLGÁLTATÓval megegyező erdőben kell lennie.  
  - Nem használhatja a vállalati HITELESÍTÉSSZOLGÁLTATÓT futtató kiszolgálóra telepített NDES.  
  - A Microsoft Intune tanúsítvány-összekötőt ugyanarra a kiszolgálóra kell telepíteni, amelyen a NDES fut.  

  További információ a NDES: [hálózati eszközök tanúsítványigénylési szolgáltatásának útmutatója](https://technet.microsoft.com/library/hh831498.aspx) a Windows Server dokumentációjában, valamint [egy házirend modul használata a hálózati eszközök tanúsítványigénylési szolgáltatásával](https://technet.microsoft.com/library/dn473016.aspx).  

- **Microsoft Intune tanúsítvány-összekötő** – a Microsoft INTUNE tanúsítvány-összekötő a SCEP-tanúsítványok Intune-nal való használatához szükséges. Ez a cikk végigvezeti [az összekötő telepítésének](#install-the-intune-certificate-connector)lépésein.  

  Az összekötő támogatja a Federal Information Processing standard (FIPS) üzemmódot. Az FIPS nem kötelező, de ha engedélyezve van, a tanúsítványok kiállítása és visszavonása is megadható.  
  - Az összekötőnek a NDES kiszolgálói szerepkörrel megegyező kiszolgálón kell futnia, amely egy Windows Server 2012 R2 vagy újabb rendszert futtató kiszolgáló.  
  - A .NET 4,5 keretrendszert az összekötő igényli, és a Windows Server 2012 R2 rendszer automatikusan tartalmazza.  
  - Az Internet Explorer fokozott biztonsági beállításait [le kell tiltani azon a kiszolgálón, amelyen a NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) és a Microsoft Intune tanúsítvány-összekötő fut.  

A következő helyszíni infrastruktúra nem kötelező:  
  Annak engedélyezéséhez, hogy az interneten lévő eszközök tanúsítványokat kérjenek, közzé kell tennie a NDES URL-címét a vállalati hálózaton kívül. Használhatja az Azure AD Application Proxy, a webalkalmazás-proxy kiszolgálót vagy egy másik fordított proxyt is.
  
- **Azure ad Application proxy** (nem kötelező) – a dedikált webalkalmazás-proxy (WAP) kiszolgáló helyett az Azure ad Application proxy használatával teheti közzé a NDES URL-címét az interneten. Ez lehetővé teszi, hogy az intranetes és az internetes eszközök is megkapják a tanúsítványokat. További információért lásd [a helyszíni alkalmazások biztonságos távoli elérésével](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) kapcsolatos témakört. 

- **Webalkalmazás-proxykiszolgáló** (nem kötelező) – Windows Server 2012 R2 vagy újabb rendszert futtató kiszolgáló használata webalkalmazás-proxy (WAP) kiszolgálóként a NDES URL-címének közzétételéhez az interneten.  Ez lehetővé teszi, hogy az intranetes és az internetes eszközök is megkapják a tanúsítványokat.

  A WAP-ot futtató kiszolgálón [telepíteni kell egy frissítést](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ahhoz, hogy az támogassa az NDES által használt hosszú URL-eket. Ez a frissítés megtalálható a [2014. decemberi kumulatív frissítésben](https://support.microsoft.com/kb/3013769), illetve önállóan a [KB3011135-as jelű frissítésként](https://support.microsoft.com/kb/3011135).  

  A WAP-kiszolgálónak rendelkeznie kell egy SSL-tanúsítvánnyal, amely megegyezik a külső ügyfelek számára közzétett névvel, és meg kell bíznia a NDES szolgáltatást futtató számítógépen használt SSL-tanúsítványban. Ezek a tanúsítványok lehetővé teszik a WAP-kiszolgáló számára az SSL-kapcsolat megszüntetését az ügyfelektől, és új SSL-kapcsolat létrehozását a NDES szolgáltatáshoz.  

  További információ: [Tanúsítványok tervezése a WAP-hoz](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) és [Általános adatok a WAP-kiszolgálókról](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Fiókok   
- **NDES-szolgáltatásfiók** – a NDES beállítása előtt azonosítson egy tartományi felhasználói fiókot, amelyet NDES-szolgáltatásfiókként kíván használni. Ezt a fiókot akkor kell megadnia, amikor sablonokat állít be a kiállító HITELESÍTÉSSZOLGÁLTATÓhoz a NDES konfigurálása előtt.  

  Ennek a fióknak a következő jogosultságokkal kell rendelkeznie a NDES üzemeltető kiszolgálón:  
  - **Helyi bejelentkezés**  
  - **Szolgáltatásként való bejelentkezés**  
  - **Bejelentkezés batch-feladatokként**  

  További információ: [tartományi felhasználói fiók létrehozása NDES-szolgáltatásfiókként való](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account)használatra. 
- **Hozzáférés a NDES szolgáltatást futtató számítógéphez** – szüksége lesz egy tartományi felhasználói fiókra, amely jogosult a Windows Server-szerepkörök telepítésére és konfigurálására azon a kiszolgálón, amelyre a NDES telepíti.  

- **Hozzáférés a hitelesítésszolgáltatóhoz** – szüksége lesz egy olyan tartományi felhasználói fiókra, amely jogosultságokkal rendelkezik a hitelesítésszolgáltató kezeléséhez.  

### <a name="network-requirements"></a>A hálózatra vonatkozó követelmények

Javasoljuk, hogy a NDES szolgáltatást fordított proxyn keresztül tegye közzé, például az [Azure ad alkalmazásproxy, a Web Access proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)vagy egy harmadik féltől származó proxy használatával. Ha nem fordított proxyt használ, engedélyezze a TCP-forgalmat a 443-as porton az interneten lévő összes gazdagépről és IP-címről a NDES szolgáltatásba.  

A NDES szolgáltatás és a környezetben található összes támogató infrastruktúra közötti kommunikációhoz szükséges összes port és protokoll engedélyezése. Például a NDES szolgáltatást futtató számítógépnek kommunikálnia kell a HITELESÍTÉSSZOLGÁLTATÓval, a DNS-kiszolgálókkal, a tartományvezérlőkkel és a környezetében lévő más szolgáltatásokkal vagy kiszolgálókkal, például a Configuration Manager.

### <a name="certificates-and-templates"></a>Tanúsítványok és sablonok

A SCEP használatakor a következő tanúsítványokat és sablonokat használja a rendszer.

|Objektum    |Details    |
|----------|-----------|
|**SCEP tanúsítványsablon**         |Az eszközök SCEP-kéréseinek fullfil használt, a kiállító HITELESÍTÉSSZOLGÁLTATÓhoz konfigurálni kívánt sablon. |
|**Ügyfél-hitelesítési tanúsítvány** |A kiállító HITELESÍTÉSSZOLGÁLTATÓtól vagy nyilvános HITELESÍTÉSSZOLGÁLTATÓTÓL kérelmezve.<br /> Ezt a tanúsítványt a NDES szolgáltatást futtató számítógépre kell telepíteni, amelyet az Intune Certificate Connector használ.<br /> Ha a tanúsítvány *ügyfél* -és *kiszolgáló-hitelesítési* kulcshasználat (**Kibővített kulcshasználat**) van BEÁLLÍTVA a tanúsítvány kiállításához használt hitelesítésszolgáltatói sablonban. Ezt követően ugyanazt a tanúsítványt használhatja a kiszolgáló-és ügyfél-hitelesítéshez is. |
|**Kiszolgálói hitelesítési tanúsítvány** |A kiállító HITELESÍTÉSSZOLGÁLTATÓtól vagy a nyilvános HITELESÍTÉSSZOLGÁLTATÓTÓL kért webkiszolgáló-tanúsítvány.<br /> Ezt az SSL-tanúsítványt a NDES üzemeltető számítógépen telepíti és köti össze az IIS-ben.<br />Ha a tanúsítvány *ügyfél* -és *kiszolgáló-hitelesítési* kulcshasználat (**Kibővített kulcshasználat**) van BEÁLLÍTVA a tanúsítvány kiállításához használt hitelesítésszolgáltatói sablonban. Ezt követően ugyanazt a tanúsítványt használhatja a kiszolgáló-és ügyfél-hitelesítéshez is. |
|**Megbízható legfelső szintű hitelesítésszolgáltató tanúsítványa**       |SCEP-tanúsítvány használatához az eszközöknek megbízható legfelső szintű hitelesítésszolgáltatót (CA) kell megbízniuk. A megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítványnak a felhasználók és eszközök számára való kiépítéséhez használjon egy *megbízható tanúsítványsablont* az Intune-ban. <br/><br/> **@no__t – 1**  Az operációs rendszer platformján egyetlen megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítványt használjon, és társítsa a tanúsítványt a létrehozott összes megbízható tanúsítvány profiljához. <br /><br /> **@no__t – 1**  Szükség esetén további megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítványokat is használhat. Előfordulhat például, hogy további tanúsítványokat használ arra, hogy megbízhatóságot biztosítson egy olyan HITELESÍTÉSSZOLGÁLTATÓ számára, amely aláírja a kiszolgálói hitelesítési tanúsítványokat a Wi-Fi hozzáférési pontjai számára. További megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítványok létrehozása a hitelesítésszolgáltatók kibocsátásához.  Győződjön meg arról, hogy az Intune-ban létrehozott SCEP-tanúsítvány profiljában meg kell adnia a kiállító HITELESÍTÉSSZOLGÁLTATÓ megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI profilját.<br/><br/> A megbízható tanúsítvány profiljával kapcsolatos információkért lásd: [a megbízható legfelső szintű hitelesítésszolgáltatói tanúsítvány exportálása](certificates-configure.md#export-the-trusted-root-ca-certificate) és [megbízható tanúsítvány-profilok létrehozása](certificates-configure.md#create-trusted-certificate-profiles) a *tanúsítványok használata a hitelesítéshez az Intune-ban*. |

## <a name="configure-the-certification-authority"></a>A hitelesítésszolgáltató konfigurálása

A következő fejezetekben a következőkre lesz szüksége:
- Konfigurálja és tegye közzé a NDES szükséges sablont. 
- Állítsa be a tanúsítvány visszavonásához szükséges engedélyeket. 

A következő részekben a Windows Server 2012 R2 vagy újabb, valamint a Active Directory tanúsítványszolgáltatás (AD CS) ismerete szükséges.  

### <a name="access-your-issuing-ca"></a>A kiállító HITELESÍTÉSSZOLGÁLTATÓ elérése

1. Jelentkezzen be a kiállító HITELESÍTÉSSZOLGÁLTATÓba egy olyan tartományi fiókkal, amely elegendő jogosultsággal rendelkezik a HITELESÍTÉSSZOLGÁLTATÓ kezeléséhez.  
2. Nyissa meg a Microsoft Management Console (MMC) hitelesítésszolgáltatót. **Futtassa** a "certsrv. msc" parancsot, vagy a **Kiszolgálókezelőben**kattintson az **eszközök**, majd a **hitelesítésszolgáltató**elemre.
3. Válassza a **Tanúsítványsablonok** csomópontot, majd kattintson a **művelet**@no__t – 2**kezelés**elemre.

### <a name="create-the-scep-certificate-template"></a>A SCEP-tanúsítványsablon létrehozása

1. Hozzon létre egy v2-tanúsítványsablont (Windows 2003 kompatibilitással) SCEP-tanúsítványsablonként való használatra. A következőket teheti:  
   - Új egyéni sablon létrehozásához használja a *Tanúsítványsablonok* beépülő modult.  
   - Másoljon egy meglévő sablont (például a felhasználói sablont), majd frissítse a példányt NDES-sablonként való használatra.
 
2. Konfigurálja a következő beállításokat a sablon megadott lapjain:
   - **Általános**:
     - Törölje **a tanúsítvány közzététele Active Directoryban**jelölőnégyzet jelölését.
     - Adjon meg egy felhasználóbarát **sablon megjelenítendő nevét** , hogy később azonosítani tudja ezt a sablont.  

   - **Tulajdonos neve**:  
     - Válassza **a kérelemben a kínálat**lehetőséget. A biztonságot a NDES Intune házirend-modulja kényszeríti ki.  

     ![Sablon, a tulajdonos nevének megadására szolgáló lap](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)
   - **Bővítmények**:  
     - Győződjön meg arról, hogy **az alkalmazás-házirendek leírása tartalmazza az** **ügyfél-hitelesítést**.  
       > [!IMPORTANT]  
       > Csak a szükséges alkalmazás-házirendeket adja hozzá. A kiválasztott elemekkel kapcsolatban kérje ki a biztonsági rendszergazda véleményét is.
 
     - IOS-és macOS-tanúsítványsablonok esetén szerkessze a **kulcshasználat** is, és győződjön meg arról, hogy az **aláírás az eredet igazolása** nincs kiválasztva.

     ![Sablon, a bővítményeket tartalmazó lap](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Biztonság**:  
     - Adja hozzá a **NDES szolgáltatásfiókot**. Ennek a fióknak **olvasási** és beléptetési **engedélyre** van szüksége ehhez a sablonhoz.

     - További fiókok hozzáadása az Intune-rendszergazdák számára, akik SCEP-profilokat fognak létrehozni. Ezeknek a fiókoknak **olvasási** engedéllyel kell rendelkezniük a sablonhoz ahhoz, hogy a rendszergazdák megkeressék ezt a SABLONT a SCEP-profilok létrehozása során.  

     ![Sablon, a biztonsági beállításokat tartalmazó lap](./media/certificates-scep-configure/scep-ndes-security.jpg)  

   - **Kérelmek feldolgozása**:  
      Az alábbi képen egy példa látható. A konfiguráció eltérő lehet.  

     ![Sablon, a kérelmek kezelésére szolgáló lap](./media/certificates-scep-configure/scep-ndes-request-handling.png) 

   - **Kiállítási követelmények**:  
     Az alábbi képen egy példa látható. A konfiguráció eltérő lehet.  

     ![Sablon, a tanúsítvány kiállításának feltételeit tartalmazó lap](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)  

3. Mentse a tanúsítványsablont.  

### <a name="create-the-client-certificate-template"></a>Az ügyféltanúsítvány-sablon létrehozása

Az Intune tanúsítvány-összekötőhöz az ügyfél- *hitelesítés* Kibővített kulcshasználat és a tulajdonos neve értéknek kell megegyeznie annak a GÉPNEK a teljes tartománynevével, amelyen az összekötő telepítve van. A következő tulajdonságokkal rendelkező sablon szükséges:

- A **bővítmények** > **alkalmazás-házirendnek** tartalmaznia kell az **ügyfél-hitelesítést**
- **A kérelemben szereplő** **tulajdonos neve** > .

Ha már van olyan sablonja, amely tartalmazza ezeket a tulajdonságokat, újra felhasználhatja, vagy létrehozhat egy új sablont a meglévő példányok másolásával vagy egyéni sablon létrehozásával.

### <a name="create-the-server-certificate-template"></a>A kiszolgálói tanúsítvány sablonjának létrehozása

A felügyelt eszközök és az IIS közötti kommunikáció a NDES-kiszolgálón HTTPS protokollt használ, amelyhez tanúsítvány használata szükséges. Ezt a tanúsítványt a **webkiszolgáló** -tanúsítvány sablonnal is kiállíthatja. Ha inkább egy dedikált sablonnal szeretne rendelkezni, a következő tulajdonságokkal kell rendelkeznie:

- **Bővítmények** >  az**alkalmazás-szabályzatoknak** **kiszolgálói hitelesítést** kell tartalmazniuk
- **A kérelemben szereplő** **tulajdonos neve** > .

> [!NOTE]  
> Ha olyan tanúsítvánnyal rendelkezik, amely megfelel az ügyfél és a kiszolgálói tanúsítvány sablonjainak, egyetlen tanúsítványt is használhat az IIS-hez és az Intune tanúsítvány-összekötőhöz.

### <a name="grant-permissions-for-certificate-revocation"></a>Engedélyek megadása a tanúsítvány visszavonásához

Ahhoz, hogy az Intune vissza tudja vonni azokat a tanúsítványokat, amelyekre már nincs szükség, engedélyeket kell biztosítania a hitelesítésszolgáltató számára. 

Az Intune tanúsítvány-összekötőn használhatja a NDES-kiszolgáló **rendszerfiókját** vagy egy adott fiókot, például a **NDES-szolgáltatásfiókot**.

1. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal a hitelesítésszolgáltató nevére, és válassza a **Tulajdonságok**lehetőséget.
2. A **Biztonság** lapon kattintson a **Hozzáadás**gombra.
3. **Tanúsítványok kiállításának és kezelésének** engedélyezése engedély:
   - Ha úgy dönt, hogy a NDES-kiszolgáló **rendszerfiókját**használja, adja meg az engedélyeket a NDES-kiszolgálónak.
   - Ha a **NDES-szolgáltatásfiók**használatát választja, adja meg a fiók engedélyeit.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Tanúsítványsablon érvényességi időtartamának módosítása

A tanúsítványsablon érvényességi időtartamának módosítása nem kötelező.  

[A SCEP-tanúsítványsablon létrehozása](#create-the-scep-certificate-template)után szerkesztheti a sablont az **érvényességi időszak** áttekintéséhez az **általános** lapon.  

Alapértelmezés szerint az Intune a sablonban konfigurált értéket használja. A HITELESÍTÉSSZOLGÁLTATÓT azonban úgy is beállíthatja, hogy a kérelmező más értéket adjon meg, és ez az érték az Intune-konzolon belülről is megadható.  

> [!IMPORTANT]  
> IOS és macOS esetén mindig a sablonban beállított értéket használja.  

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Az Intune-konzolon megadható érték konfigurálása  
1. Futtassa a hitelesítésszolgáltatón a következő parancsokat:  
   -**Certutil-setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  
   @no__t – 0**net stop certsvc**  
   @no__t – 0**hálózati indítási certsvc**  

2. Tegye közzé a Hitelesítésszolgáltató beépülő modullal a tanúsítványsablont a vállalati hitelesítésszolgáltatón. Válassza a **Tanúsítványsablonok** csomópontot, válassza a **művelet**@no__t – 2**új** > **Tanúsítványsablon**lehetőséget, majd válassza ki az előző szakaszban létrehozott tanúsítványsablont.  

3. Ellenőrizze, hogy a sablon közzé van-e téve a **Tanúsítványsablonok** mappában.  

## <a name="set-up-ndes"></a>NDES beállítása  
Az alábbi eljárások segítségével konfigurálhatja a hálózati eszközök tanúsítványigénylési szolgáltatását (NDES) az Intune-nal való használatra. További információ a NDES: [hálózati eszközök tanúsítványigénylési szolgáltatásának útmutatója](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).  

### <a name="install-the-ndes-service"></a>A NDES szolgáltatás telepítése  
1. A NDES szolgáltatást futtató kiszolgálón jelentkezzen be **vállalati rendszergazdaként**, majd használja a [szerepkörök és szolgáltatások hozzáadása varázslót](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) a NDES telepítéséhez:

   1. A varázslóban válassza az **Active Directory tanúsítványszolgáltatások** lehetőséget az AD CS szerepkör-szolgáltatások eléréséhez. Válassza a **hálózati eszközök tanúsítványigénylési szolgáltatása**lehetőséget, törölje a **hitelesítésszolgáltató**jelölőnégyzet jelölését, majd fejezze be a varázslót.  

      > [!TIP]  
      > A **telepítési folyamat**területen ne válassza a **Bezárás**lehetőséget. Ehelyett válassza **Az Active Directory tanúsítványszolgáltatások beállítása a célkiszolgálón** hivatkozást. Megnyílik az **Active Directory tanúsítványszolgáltatások konfigurálása** varázsló, amelyet a jelen cikk következő eljárásához használ, *konfigurálja a NDES szolgáltatást*. Ha megnyílt Az Active Directory tanúsítványszolgáltatások beállítása varázsló, bezárhatja a Szerepkörök és szolgáltatások hozzáadása varázslót.  

   2. Az NDES kiszolgálóhoz való hozzáadásakor a varázsló az IIS-t is telepíti. Győződjön meg arról, hogy az IIS a következő konfigurációkkal rendelkezik:  

      - **Webkiszolgáló** > **Biztonság** > **Kérelemszűrés**  
      - **Webkiszolgáló** > **Alkalmazásfejlesztés** > **ASP.NET 3.5**  

        Az ASP.NET 3.5 telepítése telepíti a .NET-keretrendszer 3.5-öt is. A .NET-keretrendszer 3.5 telepítésekor a **.NET-keretrendszer 3.5** alapszolgáltatásai mellett telepítse a **HTTP-aktiválás**szolgáltatást is.  
      - **Webkiszolgáló** > **Alkalmazásfejlesztés** > **ASP.NET 4.5**  

        Az ASP.NET 4.5 telepítése telepíti a .NET-keretrendszer 4.5-öt is. A .NET-keretrendszer 4.5 telepítésekor a **.NET-keretrendszer 4.5** alapszolgáltatásai mellett telepítse az **ASP.NET 4.5** és a **WCF-szolgáltatások** > **HTTP-aktiválás** szolgáltatást is.  

      - **Felügyeleti eszközök** > **Kompatibilitás az IIS 6 kezelésével** > **Kompatibilitás az IIS 6 metabázisával**  
      - **Felügyeleti eszközök** > **Kompatibilitás az IIS 6 kezelésével** > **IIS 6 WMI kompatibilitási mód**  
      - Vegye fel a kiszolgálón az NDES szolgáltatásfiókot a helyi **IIS_IUSR** csoport tagjaként.  

2. A NDES szolgáltatást futtató számítógépen futtassa a következő parancsot egy rendszergazda jogú parancssorban. A következő parancs a NDES-szolgáltatásfiók egyszerű szolgáltatásnevet állítja be:  

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`
   
   Ha például a NDES szolgáltatást futtató számítógép neve **kiszolgalo01**, a tartománya **contoso.com**, a szolgáltatásfiók pedig **ndesszolgaltatas**, használja a következőt:  

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>A NDES szolgáltatás konfigurálása  

1. Az NDES szolgáltatást futtató számítógépen nyissa meg az **Active Directory tanúsítványszolgáltatások konfigurálása** varázslót, majd hajtsa végre a következő frissítéseket:  

   > [!TIP]  
   > Ha folytatja az utolsó eljárást, és rákattintott a **Active Directory tanúsítványszolgáltatások konfigurálása a célkiszolgálón** hivatkozásra, a varázslónak már nyitva kell lennie. Ellenkező esetben nyissa meg a Kiszolgálókezelőt az Active Directory tanúsítványszolgáltatások telepítés utáni konfigurációjának eléréséhez.  

   - A **szerepkör-szolgáltatások**területen válassza a **hálózati eszközök tanúsítványigénylési szolgáltatása**lehetőséget.
   - A **NDES szolgáltatásban**válassza a NDES szolgáltatásfiókot.
   - A **NDES hitelesítésszolgáltatójában**kattintson a **kiválasztás**elemre, majd válassza ki azt a kiállító hitelesítésszolgáltatót, amelyben a tanúsítványsablont konfigurálta.
   - A **Titkosítás a Hálózati eszközök tanúsítványigénylési szolgáltatása esetén** területen adja meg a kulcshosszt a vállalati követelményeknek megfelelően.
   - A **Megerősítés** területen válassza a **Konfigurálás** lehetőséget a varázsló befejezéséhez.

2. A varázsló befejezése után frissítse a következő beállításkulcsot a NDES szolgáltatást futtató számítógépen:  
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`  

   A kulcs frissítéséhez azonosítsa a Tanúsítványsablonok **célját** (a **kérelmek kezelésére** szolgáló lapon található). Ezután frissítse a beállításjegyzék megfelelő bejegyzését úgy, hogy lecseréli a meglévő adatait a tanúsítványsablon nevére (nem a sablon megjelenített nevére), amelyet [a tanúsítványsablon létrehozásakor](#create-the-scep-certificate-template)adott meg.  

   A következő táblázat a tanúsítványsablon-céloknak megfelelő beállításjegyzék-értékeket mutatja:
   
   |Tanúsítványsablon célja (a Kérelmek kezelése lapon)|Szerkesztendő beállításazonosító|Az SCEP-profil Intune felügyeleti konzolban látható értéke|
   |------------------------|-------------------------|---|
   |Aláírás               |SignatureTemplate        |Digitális aláírás |
   |Encryption              |EncryptionTemplate       |Kulcstitkosítás  |
   |Aláírás és titkosítás|GeneralPurposeTemplate   |Kulcstitkosítás<br/>Digitális aláírás |  

   Ha például a tanúsítványsablon célja **Titkosítás**, akkor az **EncryptionTemplate** azonosító értékét kell a tanúsítványsablon nevére cserélnie.  

3. Konfigurálja az IIS-kérelmek szűrését az NDES szolgáltatás által fogadott hosszú URL-címek (lekérdezések) támogatásához az IIS-ben.
   1. Az IIS-kezelőben válassza az **alapértelmezett**webhely  > **kérések szűrése** >  a**szolgáltatás beállításainak szerkesztése** lehetőséget a **kérelmek szűrési beállításainak szerkesztése** lap megnyitásához.  

   2. Adja meg a következő beállításokat:  
      - **URL-cím maximális hossza (bájt)** = 65534  
      - **Lekérdezési karakterlánc maximális száma (bájt)** = 65534  
   3. A konfiguráció mentéséhez és az IIS-kezelő bezárásához kattintson **az OK gombra** .  
   4. Ellenőrizze ezt a konfigurációt a következő beállításkulcs megtekintésével annak megerősítéséhez, hogy a megadott értékek szerepelnek-e:  

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`    

      A következő értékek DWORD-bejegyzésként vannak beállítva:  
      - Név: **MaxFieldLength**, decimális **65534**  
      - Név: **MaxRequestBytes**, decimális **65534**  
4. Indítsa újra a NDES szolgáltatást futtató kiszolgálót. Ne használja az **IISReset**; a iireset nem teljesíti a szükséges módosításokat.  

5. Keresse meg a *http://* Server_FQDN */certsrv/MSCEP/MSCEP.dll*. Az alábbi képhez hasonló NDES-oldalnak kell megjelennie:  

   ![NDES teszt](./media/certificates-scep-configure/scep-ndes-url.png)
  
   Ha a webcímen a **503 szolgáltatás nem érhető el**, ellenőrizze a számítógépek eseménynaplóját. Ez a hiba általában akkor fordul elő, ha az alkalmazáskészletet leállítja a [NDES-szolgáltatásfiók hiányzó engedélye](#accounts)miatt.  
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Tanúsítványok telepítése és kötése a NDES üzemeltető kiszolgálón  
> [!TIP]  
> A következő eljárásban egyetlen tanúsítványt is használhat a *kiszolgálói hitelesítéshez* és az ügyfél- *hitelesítéshez* , ha a tanúsítvány úgy van konfigurálva, hogy mindkét használat feltételeinek megfeleljen. Az egyes használatokra vonatkozó feltételeket az alábbi eljárás 1. és 3. lépésében ismertetjük.  

1. Igényeljen **kiszolgálói hitelesítési** tanúsítványt a belső hitelesítésszolgáltatótól vagy a nyilvános hitelesítésszolgáltatótól, majd telepítse a tanúsítványt a kiszolgálóra.  

   Ha a kiszolgáló külső és belső nevet használ egyetlen hálózati címnek, akkor a kiszolgálói hitelesítési tanúsítványnak rendelkeznie kell a következővel:  

   - A **tulajdonos neve** külső nyilvános kiszolgáló nevével.
   - Egy **tulajdonos alternatív neve** , amely tartalmazza a belső kiszolgáló nevét.  

2. A kiszolgálói hitelesítési tanúsítvány kötése az IIS-ben:  
  
   1. A kiszolgálói hitelesítési tanúsítvány telepítése után nyissa meg az **IIS-kezelőt**, és válassza ki az **alapértelmezett**webhelyet. Válassza a **Műveletek** panelen található **Kötések** elemet.  
   1. Válassza a **Hozzáadás** lehetőséget, adja meg a **Típus** beállításnál a **https**értéket, és győződjön meg róla, hogy a port **443** értékre van állítva.  
   1. Az **SSL-tanúsítvány**beállításnál adja meg a kiszolgálóhitelesítő tanúsítványt.  
 
3. Kérelmezzen a belső vagy a nyilvános hitelesítésszolgáltatótól egy **ügyfél-hitelesítő** tanúsítványt, és telepítse az NDES-kiszolgálón.  

   Az ügyfél-hitelesítő tanúsítványnak az alábbi tulajdonságokkal kell rendelkeznie:  
   - **Kibővített kulcshasználat**: ennek az értéknek tartalmaznia kell az **ügyfél-hitelesítést**.  
   - **Tulajdonos neve**: az értéknek meg kell egyeznie annak a kiszolgálónak a DNS-nevével, amelyre a tanúsítványt telepíti (a NDES-kiszolgáló).  

4. A NDES szolgáltatást futtató kiszolgáló most már készen áll az Intune tanúsítvány-összekötő támogatására.  

## <a name="install-the-intune-certificate-connector"></a>Az Intune tanúsítvány-összekötő telepítése  
A Microsoft Intune Tanúsítvány-összekötő a NDES szolgáltatást futtató kiszolgálóra települ. Nem támogatott a NDES vagy az Intune tanúsítvány-összekötő használata ugyanazon a kiszolgálón, mint a kiállító hitelesítésszolgáltató (CA).  

A tanúsítvány-összekötő telepítése:  
1. Jelentkezzen be az [Intune-portálra](https://aka.ms/intuneportal) egy olyan fiókkal, amely rendelkezik Intune-jogokkal.  

2. Válassza az **Eszközkonfiguráció** > **Hitelesítésszolgáltató** > **Hozzáadás** lehetőséget.  

3. Töltse le és mentse a SCEP-fájlhoz tartozó összekötőt. Mentse egy olyan helyre, amely elérhető a kiszolgálóról, amelyre az összekötő telepítve lesz.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. A letöltés befejezése után lépjen arra a kiszolgálóra, amely a Hálózati eszközök tanúsítványigénylési szolgáltatása (NDES) szerepkört üzemelteti. Ha ez megvan:  

   1. Ellenőrizze, hogy telepítve van-e a .NET 4,5-keretrendszer, ahogy azt az Intune tanúsítvány-összekötője megköveteli. A .NET 4,5-keretrendszer automatikusan megtalálható a Windows Server 2012 R2 és újabb verziókban.  
   2. Futtassa a telepítőprogramot (**NDESConnectorSetup.exe**). A telepítő telepíti a NDES és az IIS-tanúsítvány regisztrációs pontjának (CRP) webszolgáltatásának irányelvmodul-modulját is. A *melynek neve certificateregistrationsvc*-alapú CRP-webszolgáltatás alkalmazásként fut az IIS-ben.  

      - Ha önálló Intune-hoz telepíti az NDES-t, akkor a CRP szolgáltatás automatikusan települ a tanúsítvány-összekötővel együtt. 
      - Az Intune és a Configuration Manager használatával a tanúsítvány regisztrációs pontját Configuration Manager helyrendszer-szerepkörként kell telepíteni.  
5. Amikor a rendszer kéri a tanúsítvány-összekötő ügyféltanúsítványt, válassza a **kiválasztás**lehetőséget, majd válassza ki a NDES-kiszolgálóra telepített **ügyfél-hitelesítési** tanúsítványt a [telepítés és a tanúsítványok kötésének lépésein #3 ](#install-and-bind-certificates-on-the-server-that-hosts-ndes)a jelen cikk korábbi részében NDES futtató kiszolgáló.  

   Miután kiválasztotta az ügyfél-hitelesítési tanúsítványt, a rendszer visszaküldi az **ügyféltanúsítványt Microsoft Intune tanúsítvány-összekötő** Surface-re. Bár a kiválasztott tanúsítvány nem látható, kattintson a **tovább** gombra a tanúsítvány tulajdonságainak megtekintéséhez. Válassza a **Tovább**, majd a **Telepítés** lehetőséget.

6. Ha a varázsló befejeződött, még mielőtt bezárná, válassza a **Launch the Certificate Connector UI** (Certificate Connector felhasználói felületének indítása) lehetőséget.  

   Ha a tanúsítvány-összekötő felhasználói felületének elindítása előtt bezárta a varázslót, akkor a következő parancs futtatásával újra megnyithatja: *< install_Path > \NDESConnectorUI\NDESConnectorUI.exe*

7. A **Certificate Connector** (Tanúsítvány-összekötő) felhasználói felületén:  
   1. Válassza a **Bejelentkezés** gombot, és írja be az Intune szolgáltatás rendszergazdai hitelesítő adatait, vagy egy bérlői rendszergazda globális felügyeleti engedéllyel rendelkező hitelesítő adatait.  
   2. A használt fióknak érvényes Intune-licencet kell rendelnie.  
   3. A bejelentkezést követően az Intune tanúsítvány-összekötő letölt egy tanúsítványt az Intune-ból. Ezzel történik az összekötő és az Intune közti hitelesítés. Ha a használt fiók nem rendelkezik Intune-licenccel, az összekötő (NDESConnectorUI. exe) nem tudja lekérni a tanúsítványt az Intune-ból.  

      Ha munkahelye proxykiszolgálót használ, és a proxy használata szükséges ahhoz, hogy az NDES-kiszolgáló hozzáférjen az internethez, válassza a **Proxykiszolgáló használata** lehetőséget. Ezután a csatlakozáshoz adja meg a proxykiszolgáló nevét, portját és a fiókhoz tartozó hitelesítő adatokat.  

    4. Váltson a **Speciális** lapra, majd adja meg egy olyan fiók hitelesítő adatait, amely rendelkezik **Tanúsítványok kiállítása és kezelése** engedéllyel a vállalati hitelesítésszolgáltatónál. Válassza az **Alkalmaz** gombot a módosítások alkalmazásához.  

    5. Bezárhatja a tanúsítvány-összekötő felhasználói felületét.  

8. Nyisson meg egy parancssort, írja be a **services.msc** nevet, majd nyomja le az **Enter** billentyűt. Kattintson jobb egérgombbal az **Intune Connector Service** > **Újraindítás** lehetőségre.


A szolgáltatás futásának ellenőrzéséhez nyisson meg egy böngészőt, és írja be az alábbi URL-t. **403** -es hibát ad vissza: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`  

> [!NOTE]  
> Az Intune Certificate Connector a TLS 1,2-et támogatja. Ha az összekötőt futtató kiszolgáló támogatja a TLS 1,2-et, akkor a rendszer a TLS 1,2-et használja. Amennyiben a kiszolgáló nem támogatja a TLS 1.2 verziót, a TLS 1.1 lesz használva. Az eszközök és a kiszolgáló közötti hitelesítéshez jelenleg a TLS 1.1 van használatban.

## <a name="next-steps"></a>További lépések

[SCEP-tanúsítványprofil létrehozása](certificates-profile-scep.md)  
[Az Intune tanúsítvány-összekötővel kapcsolatos problémák elhárítása](troubleshoot-certificate-connector-events.md)
