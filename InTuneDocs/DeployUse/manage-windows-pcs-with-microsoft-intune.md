---
# required metadata

title: Windows rendszerű számítógépek felügyelete | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Windows rendszerű számítógépek felügyelete a Microsoft Intune-nal
Az eszközök regisztrálása mellett az Intune a támogatott operációs rendszereket futtató, Windows rendszerű számítógépek felügyeletét is lehetővé teszi a Windows rendszerhez készült Intune ügyfélszoftver segítségével. A számítógépes ügyfél futtatásának hardver- és szoftverkövetelményei minimálisak. Jóformán minden, Windows 7 vagy annál későbbi verziót futtató rendszer támogatott.  Az ügyfélszoftver könnyedén telepíthető tartományhoz csatlakoztatott (legyen az bármilyen tartomány) és tartományhoz nem csatlakoztatott számítógépeken is.

Az Intune a Windows rendszerű számítógépek felügyeletéhez a Windows Server Active Directory tartományi szolgáltatások (AD DS) és csoportházirend-objektumok (GPO-k) által alkalmazottakhoz hasonló szabályzatokat használ. Ha Active Directory-tartományhoz csatlakoztatott számítógépeket felügyel az Intune segítségével, akkor [győződjön meg róla, hogy az Intune-szabályzatok nem ütköznek a szervezet csoportházirend-objektumaival](resolve-gpo-and-microsoft-intune-policy-conflicts.md).

> [!NOTE]
> A Microsoft Intune önálló szolgáltatásként az alábbi funkciókat nyújtja a számítógépek felügyeletéhez. A Windows 8.1 rendszert futtató eszközöket kezelheti az Intune-ügyfélprogrammal, vagy mobileszközként is regisztrálhatja őket. Az alábbi információ az Intune-ügyfélprogramot futtató számítógépekre érvényes.

## Az Intune számítógép-felügyelet követelményei

**Hardver**:
Az Intune-ügyfél a következő minimális hardverkövetelményekkel telepíthető:

|Követelmény|További információ|
|---------------|--------------------|
|Hálózat|Az ügyfél használatához a számítógépnek internetkapcsolattal kell rendelkeznie.|
|Processzor és memória|A processzorra és a RAM-ra vonatkozó követelményeket a számítógép operációs rendszere határozza meg.|
|Lemezterület|200 MB szabad lemezterület az ügyfélszoftver telepítése előtt.|

**Szoftver**:
Az Intune-ügyfél a következő minimális szoftverkövetelményekkel telepíthető:

|Követelmény|További információ|
|---------------|--------------------|
|Rendszergazdai engedélyek|Az ügyfélszoftvert telepítő fióknak helyi rendszergazdai engedélyekkel kell rendelkeznie a számítógépen.|
|Windows Installer 3.1|A számítógépnek legalább a Windows Installer 3.1-es verziójával kell rendelkeznie.<br /><br />A Windows Installer verziójának megtekintése egy számítógépen:<br /><br />– A számítógépen kattintson a jobb gombbal a **%windir%\System32\msiexec.exe** fájlra, majd a **Tulajdonságok** menüpontra..<br /><br />A Windows Installer legújabb verzióját letöltheti a Microsoft Developer Network webhelyen található [Windows Installer újraterjeszthető csomagok](http://go.microsoft.com/fwlink/?LinkID=234258) oldalról.|
|Nem kompatibilis ügyfélszoftver eltávolítása|Az Intune-ügyfélszoftver telepítése előtt el kell távolítania minden Configuration Manager-, illetve System Management Server-ügyfélszoftvert az adott számítógépről.|

## Az Intune-számítógépügyfél telepítése
Ha az Intune segítségével szeretne Windows rendszerű számítógépeket felügyelni, először telepítenie kell az ügyfelet. Az ügyfélszoftver akkor telepíthető, ha a számítógépet regisztrálta az Intune szolgáltatással végzett felügyelethez a következő módszerek valamelyikével:

-   Megteheti, hogy [manuálisan telepíti a Microsoft Intune-ügyfélszoftvert](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). Ennél a telepítési típusnál a rendszergazda letölti az Intune-ügyfélszoftvert, és manuálisan telepíti minden egyes számítógépen.

    Az Intune-ügyfélszoftver letöltéséhez nyissa meg az Intune felügyeleti konzolját, és töltse le az ügyfélszoftvercsomagot az Ügyfélszoftver letöltése területen. Az ügyfélszoftver telepítése után az Intune automatikusan telepíti a számítógép kezeléséhez szükséges további szoftvereket.

-   A letöltött fájlokkal azt is megteheti, hogy manuálisan telepíti az Intune-ügyfelet a [tartományhoz csatlakoztatott számítógépekre az Active Directory csoportházirend-objektumaival](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)..

-   [A felhasználók saját maguk is regisztrálhatják számítógépeiket](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers) az Intune vállalati portálon. Ekkor minden egyes regisztrált számítógép automatikusan kapcsolódik ahhoz a felhasználói fiókhoz, amellyel az Intune-ügyfélszoftvert telepítették.

-   Végső módszerként egy [operációsrendszer-telepítés](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image) részeként is telepítheti az Intune-ügyfélszoftvert..

## Számítógép-felügyelet az Intune-számítógépügyféllel
Miután telepítette az Intune-ügyfelet, az ügyfélszoftver különböző számítógép-felügyeleti képességeket telepít, például [alkalmazásfelügyeletet](deploy-apps-in-microsoft-intune.md), Endpoint Protection védelmet, hardver- és szoftverleltárt, (távsegítségre vonatkozó kéréseken keresztüli) távvezérlést, szoftverfrissítéseket és a megfelelőségi beállítások jelentéseit.

A számítógépügyfél által engedélyezett számítógép-felügyeleti feladatok némelyikét Intune-házirendekkel lehet elvégezni, például a következőket:

-   A [Windows tűzfal beállításainak](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) konfigurálása a felügyelt számítógépeken.

-   [Szoftverfrissítési beállítások](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) konfigurálása felügyelt számítógépeken a szükséges szoftverfrissítések ellenőrzéséhez és letöltéséhez.

-   Felügyelt számítógépek védelmének elősegítése lehetséges fenyegetésekkel és rosszindulatú szoftverekkel szemben [valós idejű megfigyeléssel és az Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) kezelésével.

Az Intune-ügyfélügynök által különálló számítógépeken helyileg elvégzett műveleteken túl az Intune felügyeleti konzolján egyéb [általános számítógép-felügyeleti feladatokat](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) is elvégezhet azokon a Windows rendszerű számítógépeken, amelyekre az ügyfél telepítve van. Például:

-   Felügyelt számítógépek hardver- és szoftverleltárjára vonatkozó információk megtekintése

-   Számítógépek távoli újraindítása

-   Számítógépek kivonása az ügyfélszoftver eltávolításához és kivételükhöz az Intune-felügyelet alól

-   Felhasználók hozzákapcsolása adott felügyelt számítógépekhez

-   Válasz távsegítségre vonatkozó kérésre

Az Intune-ügyfélügynök általában a háttérben fut, és ritkán van csak szükség felhasználói beavatkozásra vagy hibaelhárításra. Ha azonban szüksége van segítségre a számítógép-felügyeleti problémák elhárításához, több olyan [forrásanyag is elérhető, amelyek segítséget nyújthatnak](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)..


<!--HONumber=May16_HO1-->


