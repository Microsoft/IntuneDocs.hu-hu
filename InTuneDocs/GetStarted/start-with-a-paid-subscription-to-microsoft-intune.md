---
# required metadata

title: Az Intune rövid kezdési útmutatója | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Az Intune rövid kezdési útmutatója
A rövid kezdési útmutató végigvezeti Önt a Microsoft Intune fizetős előfizetésének beállításához szükséges lépéseken, hogy gyorsan és könnyen elkezdhesse a szervezetében használt mobileszközök és Windows rendszerű számítógépek kezelését. A lépéseket követheti sorrendben, vagy kihagyhatja azokat, amelyek nem érvényesek a környezetére vagy nem kapcsolódnak az üzleti igényeihez.

>[!NOTE]
>Ez a cikk az Intune különálló szolgáltatásként történő beállításával foglalkozik. Ha a számítógépek és a kiszolgálók kezelésére jelenleg a Microsoft System Center Configuration Managert használja, akkor a [Configuration Managert kiegészítheti a mobileszközök kezelésével](https://technet.microsoft.com/library/jj884158.aspx) úgy, hogy összekapcsolja az Intune-t és a Configuration Managert egy hibrid MDM-telepítésben.

A jelen rövid kezdési útmutatóban található lépések nagy része megegyezik az [Intune próbaverziójára vonatkozó útmutatóban](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) ismertetett lépésekkel. A próbaidőszak lejárta után azonban, valamint amikor készen áll a mobileszközök kezelésére, számos további követelménynek is eleget kell tennie. Ezek az aktuális hálózati infrastruktúrától és az üzleti igényektől függnek, amelyek például a következők lehetnek:

-   A helyi Active Directory-fiókok szinkronizálása az Intune szolgáltatással és az Azure Active Directory-val

-   A nyilvános tartományok és a DNS-szolgáltatás rekordjainak frissítése a tartományregisztrálónál

-   Az Intune-funkciók testreszabása üzemi használatra

>[!TIP]
>Ha legalább 150 licencet vásárolt a Microsoft Intune-hoz egy erre jogosult csomagban, használhatja a FastTrack Center juttatást, azt a szolgáltatást, amelyben a Microsoft szakértőivel együtt készítheti fel környezetét az Intune használatára. Lásd: [A Microsoft Intune szolgáltatási juttatás leírása](https://technet.microsoft.com/library/mt228265.aspx)..


## Előkészületek
Ezt az útmutatót akkor használhatja, ha a szolgáltatás fizetős verziójára fizet elő, és készen áll az Intune telepítésére, valamint a meglévő hálózati infrastruktúra módosítására. Ez a belső és külső DNS-rekordok létrehozásától vagy frissítésétől egészen a meglévő Active Directory felhasználói fiókoknak az Azure Active Directory-ba történő szinkronizálásáig terjedhet. Az Intune mobileszköz-felügyeleti funkcióinak bármilyen kombinációja mellett dönt is, gondosan meg kell terveznie, hogy az Intune hogyan működjön együtt a meglévő hálózati összetevőkkel és szolgáltatásokkal. Az alábbi szempontokra különösen nagy hangsúlyt fektessen:

-   **A felhasználói identitás kezelése**: A legtöbb közép- és nagyvállalat esetében az Intune-felhasználók identitását úgy kezelheti a leghatékonyabban és legkényelmesebben, hogy az Azure Active Directory segítségével összekapcsolja a meglévő címtárszolgáltatásokat az Intune-nal. Ez különösen akkor célszerű, ha egyéb felhőalapú Microsoft-szolgáltatásokat, például Office 365-öt vagy Exchange Online-t is használ. A helyi Active Directory és az Azure Active Directory összekapcsolása, valamint az egyszeri bejelentkezéses felhasználói hitelesítés beállítása gyorsan és egyszerűen elvégezhető a meglévő felhasználói fiókok [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) eszközzel történő szinkronizálásával.

-   **A DNS érintettsége**: Ha saját tartománynevét szeretné használni az Intune szolgáltatás első előfizetésekor létrehozott alapértelmezett onmicrosoft.com tartomány helyett, akkor néhány nyilvános DNS-rekordot frissítenie kell. A DNS-rekordok frissítése azért szükséges, hogy a mobileszközök megtalálhassák az Intune szolgáltatást, és annak ellenőrzéséhez, hogy az előfizetés megfelelően működik, és kezeli a szervezet által használt összes eszközt.

## A következőkre lesz szüksége
Készen áll a kezdésre? Ahhoz, hogy megkezdhesse az Intune fizetős verziójának használatát, a következőkre lesz szüksége:

### Egy Silverlight-kompatibilis webböngészővel rendelkező eszköz
Erre az Intune felügyeleti konzoljának elérésére lesz szüksége, ahol kezelheti az eszközöket, az alkalmazásokat és a szabályzatokat. A webböngészőt kell használnia a webes vállalati portál elérésére is, ha nem mobileszközről éri el a Vállalati portál alkalmazást. A művelet egyszerűsítéséhez használja az Intune-felügyelethez használt ugyanazon böngésző adatvédelmi üzemmóddal kapcsolatos beállítását (az Internet Explorerben például válassza az **Eszközök** &gt; **InPrivate-böngészés** lehetőséget).).

>[!TIP]
>Ezen követelmény miatt a Microsoft Edge böngésző nem támogatott az Intune felügyeleti konzoljának eléréséhez.


### Mobileszközök tanúsítványai
Ha az iOS- vagy a Windows Phone-eszközöket az Intune-szolgáltatással fogja felügyelni, a tanúsítványok lekéréséhez tanúsítványokra és fiókokra lesz szüksége. Android-eszközök kezeléséhez nincs szükség külön tanúsítványokra.

- A **Windows Phone 8.1** azon felhasználói számára, akik az Áruházból telepítik a Vállalati portál alkalmazást, nem szükséges tanúsítvány. [Symantec kódaláíró tanúsítvány](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do) szükséges azonban a **Windows Phone 8.0** esetén, vagy ha a Vállalati portál alkalmazást az Intune szolgáltatással kívánja Windows Phone 8.1-eszközre telepíteni.

>[!NOTE]
>Ez a rövid útmutató azt feltételezi, hogy az Ön felhasználói az Áruházból származó Vállalati portál alkalmazást Windows Phone 8.1 vagy újabb rendszerű eszközön telepítik. A Windows Phone 8.0 támogatásával kapcsolatos információkat lásd: [Windows Phone 8.0 rendszerű telefonok Microsoft Intune-beli felügyeletének beállítása](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)..

- A **Windows rendszerű számítógép** vagy a **Windows RT rendszerű eszközök** esetében nincs tanúsítványra vonatkozó követelmény, amikor eszközként regisztrálja a Windows rendszerű számítógépeket vagy a [Microsoft Intune Windows rendszerű számítógépügyfelét telepíti](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)..

- Az **iOS** vagy a **Mac OS X** rendszerű eszközökhöz Apple Push Notification szolgáltatásbeli tanúsítványt kell igényelnie az Apple-től [Az iOS kezelésének beállítása a Microsoft Intune-nal](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) témakör 3. lépésében leírtak szerint..

### További lépések
Itt az ideje, hogy megismerkedjen az Intune rövid kezdési útmutatójával!

>[!div class="step-by-step"]
[**Bejelentkezés az Intune-ba** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)


<!--HONumber=May16_HO1-->


