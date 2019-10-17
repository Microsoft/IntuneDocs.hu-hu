---
title: Mobileszköz-felügyeleti szolgáltató megadása
titleSuffix: Microsoft Intune
description: Mobileszköz-felügyeleti szolgáltató beállítása az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19d02694ab5e53dc43e0861c6a427a044bf50648
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502636"
---
# <a name="set-the-mobile-device-management-authority"></a>Mobileszköz-felügyeleti szolgáltató megadása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A mobileszköz-felügyeleti (MDM-) szolgáltató beállítása szabja meg, hogy miként kezelheti mobileszközeit. Ahhoz, hogy a felhasználók felügyeletre tudják regisztrálni eszközeiket, a rendszergazdának be kell állítania egy MDM-szolgáltatót.

A lehetséges konfigurációk a következők:

- **Önálló Intune** – kizárólag felhőalapú felügyelet használata, amelyet az Azure Portal segítségével konfigurálhat. Az Intune-ban elérhető összes lehetőség a rendelkezésére áll. [MDM-szolgáltató beállítása az Intune-konzolon](#set-mdm-authority-to-intune).

- **Intune közös felügyelet** – az Intune felhőalapú megoldásának integrációja System Center Configuration Manager Windows 10-es eszközökhöz. Az Intune-t a Configuration Manager konzolja segítségével konfigurálhatja. Az [eszközök automatikus regisztrálásának konfigurálása az Intune-ban](https://docs.microsoft.com/sccm/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

    > [!Important]
    >Az új hibrid MDM-ügyfelek bevezetése elavult. További információ: [áttérés hibrid mobileszköz-kezelésről az Intune-ra az Azure-](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) blogbejegyzésben.

- **Mobileszköz-felügyelet az Office 365 használatával** – Az Office 365 és az Intune felhőalapú megoldásának integrációja. Az Intune-t a Microsoft 365 felügyeleti központból konfigurálhatja. Az önálló Intune-nal elérhető funkciók egy részét tartalmazza. A MDM-szolgáltató beállítása Microsoft 365 felügyeleti központban.

- **Office 365 Mdm együttes létezése** Az Office 365 és az Intune MDM is aktiválhatja és használhatja egyszerre a bérlőn, és a felügyeleti szolgáltatót úgy állíthatja be, hogy az Intune-t vagy a MDM-t az Office 365-hoz az egyes felhasználók számára a mobileszközök felügyeletére szolgáló szolgáltatás megadásához. A felhasználó felügyeleti szolgáltatója a felhasználóhoz rendelt licenc alapján van definiálva. További információ: [Microsoft Intune együttes létezése a Mdm for Office 365](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)

## <a name="set-mdm-authority-to-intune"></a>Az Intune beállítása MDM-szolgáltatóként

Ha még nem állította be az MDM-szolgáltatót, kövesse az alábbi lépéseket. A SCCM való váltásról lásd: [hibrid Mdm-felhasználók és-eszközök migrálása önálló Intune-ba](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

1. A [Azure Portal Intune-](https://aka.ms/intuneportal)ban válassza ki a narancssárga szalagcímet a **mobileszköz-kezelő szolgáltató** beállításának megnyitásához. A narancssárga szalagcím csak akkor jelenik meg, ha még nem állított be az MDM-szolgáltatót.
2. A **Mobileszköz-kezelő szolgáltató** szakaszban válassza ki az alábbiak közül a kívánt MDM-szolgáltatót:
   - **Intune MDM-szolgáltató**
   - **Nincsenek**

   ![Képernyőkép az Intune mobileszköz-kezelő szolgáltató beállítására szolgáló képernyőjéről](./media/mdm-authority-set/set-mdm-auth.png)

   Egy üzenet jelzi, hogy az Intune-t sikeresen beállította mobileszköz-kezelő szolgáltatónak.

### <a name="workflow-of-intune-administration-ui"></a>Az Intune-felügyelet felhasználói felületének munkafolyamata
Engedélyezett Android- vagy Apple-eszközkezelés esetén az Intune eszköz- és felhasználóadatok küldésével végzi el az eszközök kezeléséhez szükséges integrációt a külső szolgáltatásokkal.

Néhány új helyzet, amelyben az adatok megosztásához a rendszer jóváhagyást kér:
- Az androidos munkahelyi profilok engedélyezése.
- Apple MDM leküldéses tanúsítványok engedélyezése és feltöltése.
- Olyan Apple-szolgáltatások engedélyezése, mint a Készülékregisztrációs program, a School Manager és a mennyiségi vásárlási program (VPP).

Ezekben az esetekben a jóváhagyás szigorúan csak egy mobileszköz-felügyeleti szolgáltatás futtatásához kapcsolódik, például annak megerősítéséhez, hogy egy rendszergazda engedélyezte a Google- vagy Apple-eszközök regisztrálását. Az új munkafolyamatok indulásakor megosztott adatokról szóló dokumentáció az alábbi helyeken érhető el:
- [Az Intune által a Google-nek küldött adatok](https://aka.ms/Data-intune-sends-to-google)
- [Az Intune által az Apple-nek küldött adatok](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Fontos szempontok
Az új MDM-szolgáltatóra való váltás után, az eszköz bejelentkezése és a szolgáltatóval való szinkronizálása előtt valószínűleg egy átmeneti időszak következik, amely akár 8 órán át is tarthat. Konfigurálnia kell az új (hibrid) MDM-szolgáltató beállításait, hogy továbbra is gondoskodhasson a regisztrált eszközök felügyeletéről és védelméről a módosítás után. 
- Az eszközöknek csatlakozniuk kell a szolgáltatáshoz a váltás után annak érdekében, hogy az új MDM-szolgáltató (az Intune önálló verziója) lecserélhesse az eszköz meglévő beállításait.
- Az MDM-szolgáltató módosítása után az előző MDM-szolgáltató (az Intune önálló verziója) egyes alapszintű beállításai (például a profilok) akár 7 napig, vagy az eszköz a szolgáltatáshoz való első csatlakozásáig az eszközön maradhatnak. Javasoljuk, hogy az új hibrid MDM-szolgáltatóban a lehető leghamarabb konfigurálja az alkalmazásokat és a beállításokat (a szabályzatokat, a profilokat, az alkalmazásokat és egyebeket), és alkalmazza a beállításokat azokra a felhasználói csoportokra, amelyek a meglévő regisztrált eszközökkel rendelkező felhasználókat tartalmazzák. Amint egy eszköz csatlakozik a szolgáltatáshoz az MDM-szolgáltató váltása után, megkapja az új MDM-szolgáltató beállításait, és meggátolja a felügyeleti és a védelmi hiányosságokat.
- Ha ugyanazok az eszközkategóriák megtalálhatóak mind az Intune-ban, mind pedig Configuration Managerben, akkor az új MDM-szolgáltatóra váltás után az eszközökre vonatkozó eszközkategória-hozzárendelések nem lesznek áthozva. Ha továbbra is használni szeretné az eszközkategóriákat, akkor azokat manuálisan kell hozzáadnia a megfelelő gyűjteményekhez azt követően, hogy az új MDM-szolgáltatóra váltás megtörtént, és az eszközök megjelennek a Configuration Manager konzolján.
- Azok az eszközök, amelyek nem rendelkeznek hozzárendelt felhasználókkal (általában az iOS Készülékregisztrációs programja vagy csoportos regisztrálási folyamatok esetén), nem migrálhatók az új MDM-szolgáltatóba. Ezeknek az eszközöknek az új MDM-szolgáltatóba való áthelyezéséhez az ügyfélszolgálat segítségét kell kérnie.

## <a name="change-mdm-authority-to-office-365"></a>Az Office 365 beállítása mobileszköz-felügyeleti szolgáltatóként

Az Office 365 MDM aktiválásához (vagy a MDM párhuzamos létezésének engedélyezéséhez a meglévő Intune-szolgáltatáson kívül) lépjen a [https://protection.office.com](https://protection.office.com)elemre, válassza az **adatveszteség-megelőzés** > **eszköz biztonsági házirendek** > **megtekintését a felügyelt eszközök listáján**@no_ _T-7 –**első lépések**.

További információ: [Mobileszköz-felügyelet (MDM) beállítása az Office 365-ben](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Ha azt szeretné, hogy a végfelhasználókat egyedül az Office 365 MDM felügyelje, akkor az Office 365 MDM aktiválása után távolítson el minden hozzárendelt Intune- és/vagy EMS-licencet.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Mobileszköz karbantartása az MDM-tanúsítvány lejárta után

Az MDM-tanúsítvány automatikusan megújul, amikor a mobileszköz kommunikál az Intune szolgáltatással. Ha egy mobileszköznek törlik a tartalmát, vagy az eszköz egy bizonyos időn át nem kommunikál az Intune szolgáltatással, akkor az MDM-tanúsítvány nem újul meg. Az eszköz az MDM-tanúsítvány lejárta után 180 nappal törlődik az Azure Portalról.

## <a name="remove-mdm-authority"></a>Mobileszköz-felügyeleti szolgáltató eltávolítása

A mobileszköz-felügyeleti szolgáltató nem állítható vissza Ismeretlenre. A szolgáltatás a MDM-szolgáltatót használja annak meghatározására, hogy mely portálon regisztrált eszközök jelentenek jelentést (Microsoft Intune vagy Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Amire a mobileszköz-felügyeleti szolgáltató módosítása után számítani kell

- Amikor az Intune észleli, hogy egy bérlő MDM-szolgáltatója módosult, értesítést küld az összes regisztrált eszköznek, hogy jelentkezzenek be és szinkronizáljanak a szolgáltatással (ez az értesítés nem tartozik a rendszeresen ütemezett bejelentkezések közé). Emiatt miután az Intune önálló verziójáról hibridre módosítja a bérlő MDM-szolgáltatóját, az összes bekapcsolt és online eszköz csatlakozik a szolgáltatáshoz, az új MDM-szolgáltató hatásköre alá kerül, és a továbbiakban a hibrid szolgáltatás kezelése alá tartozik. Az eszközök kezelése és védelme megszakítás nélkül fennmarad.
- Az MDM-szolgáltató módosítása során (vagy röviddel utána) bekapcsolt és online állapotban lévő eszközök esetében akár 8 órás késés várható (a következő ütemezett rendszeres bejelentkezés idejétől függően), mielőtt az eszközök regisztrációja befejeződne az új MDM-szolgáltató szolgáltatása alatt.    

  > [!IMPORTANT]    
  > Az MDM-szolgáltató módosítása és a megújított APNs-tanúsítvány az új szolgáltatóra való feltöltése között az iOS-eszközök új eszközregisztrációi és -bejelentkezései sikertelenek lesznek. Ezért különösen fontos, hogy az MDM-szolgáltató módosítása után a lehető leghamarabb tekintse át és töltse fel az APNs-tanúsítványt az új szolgáltatóba.

- A felhasználók gyorsan átválthatnak az új MDM-szolgáltatóra, ha manuálisan bejelentkeznek az eszközről a szolgáltatásba. Ezt könnyen megtehetik a Céges portál alkalmazásból, ha elindítanak egy eszközmegfelelőségi ellenőrzést.
- Ha ellenőrizni szeretné, hogy az MDM-szolgáltató módosítása után megfelelően működik-e minden a bejelentkezett és a szolgáltatással szinkronizált eszközök esetében, keresse meg az eszközöket a Configuration Manager konzolban. A korábban az Intune által kezelt eszközök mostantól kezelt eszközökként jelennek meg a Configuration Manager konzolban.    
- Az MDM-szolgáltató váltásakor, valamint az eszköz szolgáltatásba való bejelentkezésekor az eszköz ideiglenesen offline állapotba kerül. Annak érdekében, hogy az eszköz az ideiglenes időszak alatt is védelem alatt álljon és megfelelően működjön, az alábbi profilok az eszközön maradnak legfeljebb 7 napig (vagy addig, amíg az eszköz nem csatlakozik az új MDM-szolgáltatóhoz és kapja meg a meglévő beállításokat felülíró új beállításokat):
  - E-mail-profil
  - VPN-profil
  - Tanúsítványprofil
  - Wi-Fi profil
  - Konfigurációs profilok
- Az új MDM-szolgáltatóra való váltás után a Microsoft Intune felügyeleti konzol megfelelőségi adatainak akár egy hétre is szükségük lehet, hogy pontosan jelenjenek meg. Az Azure Active Directory és az eszköz megfelelőségi állapotai azonban pontosak maradnak, az eszköz így továbbra is védelem alatt áll.
- Ügyeljen rá, hogy a meglévő beállításokat felülírandó új beállítások ugyanazzal a névvel rendelkezzenek, mint a korábbiak. Így az új beállítások biztosan felülírják a korábbiakat. Ellenkező esetben előfordulhat, hogy az eszközökön felesleges profilok és szabályzatok maradnak.    

  > [!TIP]    
  > Ajánlott eljárásként érdemes létrehozni minden kezelési beállítást, konfigurációt és példányt nem sokkal az MDM-szolgáltató módosítása után. Ezzel biztosíthatja, hogy az eszközök az ideiglenes időszak alatt is védelem és kezelés alatt álljanak.

- Az MDM-szolgáltató módosítása után végezze el az alábbi lépéseket az új eszközök sikeres regisztrációjának ellenőrzéséhez:   
  - Új eszköz regisztrációja
  - Ellenőrizze, hogy az újonnan regisztrált eszköz megjelenik-e a Configuration Manager konzolban.
  - Végezzen el egy, az eszközre vonatkozó műveletet (például távoli zárolást) a felügyeleti konzolban. Ha a művelet sikeres, az eszközt már az új MDM-szolgáltató kezeli.
- Ha problémába ütközik bizonyos eszközökkel, szüntesse meg azok regisztrációját, majd regisztrálja őket újra, így azok csatlakozni tudnak az új szolgáltatóhoz, és a lehető leggyorsabban újra kezelés alatt állhatnak.

## <a name="next-steps"></a>További lépések

A mobileszköz-felügyeleti szolgáltató beállítása után megkezdheti az [eszközök regisztrálását](../enrollment/device-enrollment.md).
