---
title: "Rendszergazdai fiókok, weblapok és engedélyek a Microsoft Intune-ban | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: a8d9cf5d36107c54b97d2b5a5250645dc735a8da


---

# Rendszergazdai fiókok, weboldalak és engedélyek a Microsoft Intune-ban

A Microsoft Intune beállítása előtt olvassa el ezt a témakört, valamint a [Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md) című témakörben felsorolt követelmények listáját.

Az Intune felügyeletéhez a következőket fogja használni:
- Két különböző típusú rendszergazdai fiók
- További jogosultságokkal rendelkező felhasználói fiókok
- Két webalapú felügyeleti konzol/portál, amelyek hozzáférést biztosítanak a rendszergazdák számára azokhoz az elemekhez, amelyeket felügyelniük kell.

Az alábbiakban ezen fiókokról és portálokról esik szó.

## Az Intune rendszergazdai fiókjai és speciális engedélyekkel rendelkező felhasználói fiókjai

Az alábbiakban találja az Intune által használt fiókokat és engedélyeket.

### Bérlői rendszergazda
|Jogosultsági szintek|További információ|
|--------------------------|-------------------------|
|A bérlői rendszergazdák egy rendszergazdai szerepkörrel rendelkeznek, amely meghatározza az adott felhasználó felügyeleti hatókörét és az általa kezelhető feladatokat.<br /><br />A Microsoft különböző felhőszolgáltatásai ugyanazokat a rendszergazdai szerepköröket használják, azonban előfordulhat, hogy egyes szolgáltatások nem támogatnak bizonyos szerepköröket.<br /><br /> A Microsoft Intune a következő szerepköröket használja:<br /><br />- Globális rendszergazda<br />- Számlázási rendszergazda<br />- Jelszókezelő<br />- Szolgáltatás-rendszergazda<br />- Felhasználókezelő rendszergazda|A Microsoft Intune-előfizetés létrehozásához használt fiók alapértelmezés szerint egy bérlői rendszergazda, aki megkapja a globális rendszergazdai szerepkört.<br /></br>  Bérlői rendszergazdaként a [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] segítségével kezelheti [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-előfizetését, valamint kijelölheti a bérlő rendszergazdákat a(z) [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] felületén.<br /><br />A globális rendszergazdai szerepkörrel rendelkező bérlői rendszergazdákkal hozzáférhet a [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]hoz, és kijelölheti az első szolgáltatás-rendszergazdát. A napi felügyeleti feladatok elvégzéséhez nem ajánlott bérlői rendszergazdát alkalmazni. A bérlői rendszergazdának nincs szüksége [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licencre a [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]hoz való hozzáféréshez.<br /><br />A bérlői rendszergazda a Microsoft felhőszolgáltatásaiban általánosan használt fogalom. Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ra való előfizetéskor a szolgáltatás a Microsoft Azure AD bérlője lesz. Lásd az Azure AD-bérlőről szóló részt a következő cikkben: [Mi az az Azure AD címtár?](http://technet.microsoft.com/library/jj573650.aspx)|


### Szolgáltatás-rendszergazda
|Jogosultsági szintek|További információ|
|--------------------------|-------------------------|
|A szolgáltatás-rendszergazdák a következő jogosultságok egyikével rendelkeznek:<br /><br />**Teljes hozzáférés**: A [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] minden területéhez korlátlan hozzáférést biztosít. Más szolgáltatás-rendszergazdákat is hozzáadhat és kezelhet.<br /><br />**Olvasási hozzáférés**: A [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] minden területéhez olvasási engedélyt biztosít. A csak olvasási hozzáféréssel rendelkező szolgáltatás-rendszergazdák nem módosíthatják az adatokat, de futtathatnak jelentéseket.<br /><br />**Segélyszolgálat – Csoportok csomópont**: csak a segélyszolgálati forgatókönyvekhez gyakran kapcsolódó feladatokhoz biztosít engedélyeket a szolgáltatás rendszergazdája számára. Az engedélyeknek ezzel a halmazával kapcsolatos további információkért lásd: [Az Intune-konzolnézetek testreszabása a rendszergazdai szerepköröknek megfelelően](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] szolgáltatás alapértelmezés szerint nem jelöl ki szolgáltatás-rendszergazdát. Ehelyett egy globális rendszergazdai szerepkörrel rendelkező bérlői rendszergazda használatával kell kijelölnie az első szolgáltatás-rendszergazdát az előfizetéshez. </br></br> Szolgáltatás-rendszergazdaként az [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]on végezheti el a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] napi feladatait.<br /><br />A szolgáltatás-rendszergazdákat a felügyeleti konzolon lehet kijelölni. A szolgáltatás-rendszergazdáknak rendelkezniük kell [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenccel ahhoz, hogy a fiók hozzáférhessen a felügyeleti konzolhoz.|



### Eszközregisztráció-kezelők
|Jogosultsági szintek|További információ|
|--------------------------|-------------------------|
|Az eszközregisztráció-kezelők normál felhasználói fiókok, melyek rendelkeznek az ötnél több eszköz regisztrálásához szükséges további engedélyekkel.|Alapértelmezés szerint minden [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-felhasználó legfeljebb öt eszközt regisztrálhat. Megadhatja azonban az eszközregisztráció-kezelői engedélyt egy felhasználói fióknak, majd ezzel a fiókkal regisztrálhat nagy mennyiségű vállalati eszközt. Ez akkor hasznos, ha előfordulhat, hogy az eszközöket csak ideiglenesen rendelik hozzá a felhasználókhoz, vagy kioszkmódban működnek, amelyben a felhasználók eszközökhöz való társítása nem szükséges.|


## Az Intune felügyeleti webhelyei
 A különböző rendszergazdai feladatok elvégzéséhez a következő felügyeleti webhelyek szükségesek. Ezeket a [támogatott böngészőkkel](supported-web-browsers.md) érheti el.

- [Office 365 portál](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune felügyeleti konzol](https://admin.manage.microsoft.com/)

### [Office 365 portál](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Bérlői rendszergazdaként ezen a portálon kezelheti előfizetését**, beleértve a következő feladatokat, ha a rendszergazdai szerepköre lehetővé teszi őket:

- Az előfizetéshez tartozó felhasználói fiókok kezelése és a helyszíni Active Directoryból való címtár-szinkronizálás beállítása.
- A felhasználók biztonsági csoport nevű csoportjainak kezelése.
- Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatához szükséges licencek kiosztása a felhasználók számára.
- Az előfizetéshez használt tartománynév beállítása. A tartománynév határozza meg a fiókot, amellyel a felhasználók bejelentkeznek.
- Az előfizetés és a vásárlások adatainak kezelése, beleértve a birtokolt licencek számát, illetve a felhasználható felhőbeli tárhely mennyiségét.
- Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] szolgáltatás állapotának megtekintésére szolgáló hivatkozások használata.
- Bérlői rendszergazdaként az Office 365 portálra bejelentkezve kezelheti az előfizetést, akkor is, ha a fiókjához nincs hozzárendelve a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatához szükséges licenc.
- Az Intune-licenccel rendelkező, ugyanakkor nem rendszergazdai felhasználók e portál segítségével állíthatják alaphelyzetbe a fiókjelszavukat, illetve módosíthatják a profiljukat.
- Az Office 365 portál eléréséhez a fióknak **Engedélyezett** bejelentkezési állapotúnak kell lennie. Ez az állapot nem ugyanaz, mint amikor a fióknak licence van az előfizetéshez. Alapértelmezés szerint az összes felhasználói fiók **Engedélyezett** állapotú.


### [Microsoft Intune felügyeleti konzol](https://admin.manage.microsoft.com/)

**Szolgáltatás-rendszergazdaként ezen a portálon kezelhetők a napi tevékenységek**, beleértve az alábbiakat:

- Számítógépekre és mobileszközökre vonatkozó házirendek beállítása.
- Szoftverek, például szoftverfrissítések és alkalmazások feltöltése és telepítése.
- A számítógépeken futó [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection szolgáltatás kezelése.
- Eszközállapot megtekintése és jelentések futtatása.
- Jelentkezzen be a portálra. A portálra szolgáltatás-rendszergazdák, valamint globális rendszergazda szerepkörrel rendelkező bérlői rendszergazdák jelentkezhetnek be.


A portálra szolgáltatás-rendszergazdák, valamint globális rendszergazda szerepkörrel rendelkező bérlői rendszergazdák jelentkezhetnek be. A felügyeleti konzol eléréséhez a fióknak az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatához szükséges licenccel, illetve **Engedélyezett** bejelentkezési állapottal kell rendelkeznie.

További információ a [felhasználók előfizetéshez való hozzáadásával](start-with-a-paid-subscription-to-microsoft-intune-step-3.md) és az [előfizetési licencek hozzárendelésével kapcsolatban](start-with-a-paid-subscription-to-microsoft-intune-step-4.md).

 ### További információ
 [Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


