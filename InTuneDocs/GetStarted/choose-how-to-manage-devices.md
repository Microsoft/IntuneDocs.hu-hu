---
title: "Az eszközkezelés módjának kiválasztása | Microsoft Intune"
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: c9b34408e4af34dafc700d016304a6d29c2e8585


---

# Az eszközkezelés módjának kiválasztása
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] segítségével számos különböző eszközt kezelhet úgy, hogy *regisztrálja* őket a szolgáltatásban. A felhasználók ezt követően számos különböző műveletet végezhetnek el a *vállalati portál* segítségével: regisztrálhatják az alkalmazásokat, válogathatnak az alkalmazások közül, telepíthetik őket, ellenőrizhetik, hogy megfelel-e az eszközük a vállalat szabályzatainak, és az informatikai támogatási munkatársakhoz fordulhatnak.

## A mobileszközök kezelésének módjai
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a következő eszközplatformokat képes kezelni:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tipp</h5>
  <p>Ha korábban regisztrált olyan eszközöket, amelyeken az iOS-nak a támogatottnál korábbi verziója fut, azok regisztrálva maradnak. Azonban minden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-verzió dokumentációjában ellenőrizze, hogy az adott iOS-verziót támogatja-e a funkció.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] képes a felhasználók eszközeinek (közkeletű nevén a „saját behozott eszközök” (BYOD)) kezelésére. A vállalat tulajdonában lévő eszközök kezelésére is alkalmas, beleértve az olyan helyzeteket is, amikor a vállalat a választható eszközök listáját bocsátja a felhasználók rendelkezésére (közkeletű nevén „saját eszköz kiválasztása” vagy CYOD).

### Az eszközök regisztrálása felügyeletre
A mobileszköz-operációs rendszert (iOS, Android, Windows Phone) használó eszközöket mindig regisztrálni kell. Az eszközök regisztrálásának módja azonban függ a vállalat igényeitől:

|Beléptetés típusa|BYOD|CYOD|Megosztott eszköz kezelő fiókkal|Megosztott eszköz felhasználói fiók nélkül|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Leírás**|Személyes eszköz regisztrálva a Microsoft Intune segítségével|Vállalat által birtokolt eszköz egyetlen felhasználó számára|Vállalat által birtokolt, kezelői fiókkal kezelt, sok felhasználó között megosztott eszköz|Vállalati által birtokolt, felhasználó nélküli, sok felhasználó által használt eszköz.|
|**Az eszköz felhasználója**|Tulajdonos|Hozzárendelt felhasználó|Nincs felhasználóspecifikus fiók|Nincs adott felhasználó|
|**Regisztrációt végzi**|Tulajdonos|Rendszergazda|Eszközkezelő|Bárki|
|**Regisztráció törlését végzi**|Tulajdonos vagy a rendszergazda|Rendszergazda|Rendszergazda|Rendszergazda|
|**Alaphelyzetbe állíthatja**|Tulajdonos vagy a rendszergazda|Rendszergazda|Rendszergazda|Rendszergazda|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tipp</h5>
  <p>Az eszközök regisztrálásával elérhető lehetőségek teljes listájáért lásd: [Mobileszköz-kezelési képességek](mobile-device-management-capabilities-in-microsoft-intune.md).</p>
</div>



## A Windows rendszerű számítógépek kezelésének módjai
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] képes Windows Vista és újabb rendszerű Windows-számítógépek kezelésére az Intune-számítógépügyféllel. A Windows-számítógépek esetében eldöntheti azonban, hogy regisztrálja őket, vagy telepíti az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-számítógépügyfelet. Az utóbbi olyan lehetőségeket is kínál, amelyek az eszközök regisztrálása esetén nem érhetők el. A legtöbb esetben azonban célszerű regisztrálni a Windows-eszközöket az Intune-ban, ez ugyanis több funkciót biztosít, mint a számítógépes ügyfél.

Akkor fontolja meg az Intune-számítógépügyfél használatát, ha a következők a céljai:
<ul>
<li>A Microsoft Intune-számítógépügyfél által nyújtott funkciók használata a Windows-számítógépek felügyelete céljából.</li>
<li>Olyan Windows-számítógép kezelése, amelyen a regisztrációt nem támogató operációs rendszer fut.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tipp</h5>
  <p>A támogatott Windows-számítógépeken futó Intune-számítógépügyfél által nyújtott funkciók teljes listáját lásd: [A Windows-számítógépek felügyeletére szolgáló képességek](windows-pc-management-capabilities-in-microsoft-intune.md).</p>
</div>

## Felügyelet az Exchange ActiveSync segítségével
Az Exchange ActiveSync segítségével is felügyelheti az eszközöket. Ehhez telepítenie kell az intézményi összekötőt, vagy a beépített Service to Service összekötővel kell kapcsolódnia az Exchange Serverhez.

A helyszíni összekötő telepítésére vonatkozó hardver- és a szoftverkövetelményekről [A helyszíni összekötőre vonatkozó követelmények](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connect) című témakörben olvashat.

További információk az On-Premises Connector vagy a Service to Service Connector összekötőnek az Exchange-dzsel történő használatáról: [Mobileszköz-kezelés az Exchange ActiveSync és a Microsoft Intune használatával](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## További lépések
Az előzőekben megismert néhány funkciót, amelyeket akkor használhat, ha regisztrálja eszközét a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal. Következő lépésként [regisztrálja eszközeit](/intune/deploy-use/enroll-devices-in-microsoft-intune). Az eszközök regisztrálását követően élhet az előnyökkel, amelyeket az ebben a témakörben tárgyalt funkciók biztosítanak. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Jun16_HO4-->


