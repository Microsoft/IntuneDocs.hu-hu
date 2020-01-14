---
title: Windows 10-es eszközök csoportos regisztrálása
titleSuffix: Microsoft Intune
description: Csoportos regisztrációs csomag létrehozása a Microsoft Intune-hoz
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: spshumwa
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cbdd99dfb7b42677048b4f214e7de537db0edda
ms.sourcegitcommit: 5db0769274d788a1218dca3ad90d8649927becb4
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925823"
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windowsos eszközök csoportos regisztrálása

A rendszergazda nagy számú új windowsos eszközt csatlakoztathat az Azure Active Directoryhoz és az Intune-hoz. Ha az Azure AD-bérlőhöz csoportosan szeretne eszközöket regisztrálni, először a Windows Configuration Designer (WCD) alkalmazással létre kell hoznia egy kiépítési csomagot. Ha a kiépítési csomagokat céges tulajdonban lévő eszközökre alkalmazza, az eszközök az Azure AD-bérlőhöz lesznek csatlakoztatva, és regisztrálódnak az Intune-felügyeletben. A csomag alkalmazása után készen áll az Azure AD-felhasználók bejelentkezésére.

Az Azure AD-felhasználók általános jogú felhasználók ezeken az eszközökön, és megkapják a hozzájuk rendelt Intune-szabályzatokat és a kötelező alkalmazásokat. Az Intune-nal a Windows csoportos regisztráció használatával beléptetett Windows-eszközök a Céges portál alkalmazást használhatják az elérhető alkalmazások telepítéséhez. 

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windowsos eszközök csoportos regisztrációjának előfeltételei

- A Windows 10 alkotói frissítését (1703-as build) vagy újabb verziót futtató eszközök
- [Windowsos eszközök automatikus regisztrációja](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Kiépítési csomag létrehozása

1. Töltse le a [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) alkalmazást a Microsoft Áruházból.
   ![Képernyőkép a Windows Configuration Designer alkalmazás-áruházról](./media/windows-bulk-enroll/bulk-enroll-store.png)

2. Nyissa meg a **Windows Configuration Designer** alkalmazást, és válassza a **Provision desktop devices** (Asztali eszközök kiépítése) elemet.
   ![Képernyőkép a Provision desktop services elem kiválasztásáról a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-select.png)

3. Megnyílik egy **New project** (Új projekt) ablak, ahol az alábbi adatokat kell megadnia:
   - **Név** – A projekt neve
   - **Project folder** (Projektmappa) – A projekt mentési helye
   - **Description** (Leírás) – A projekt leírása (nem kötelező) ![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-name.png)

4. Adjon meg egyedi neveket az eszközök számára. A nevek tartalmazhatnak sorozatszámot (% SERIAL%) vagy véletlenszerűen beállított karakterek. Lehetőség van termékkulcs megadására is, ha frissíti a Windows-kiadást, megosztott használatra konfigurálja az eszközt, és eltávolítja az előre telepített szoftvert.
   
   ![Képernyőkép a név és a termékkulcs megadásáról a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-device.png)

5. Lehetőség van arra is, hogy beállítsa, mely Wi-Fi-hálózathoz csatlakozzanak az eszközök az első indításkor.  Ha nincsenek konfigurálva a hálózati eszközök, az eszköz első indításakor vezetékes hálózati kapcsolatra lesz szükség.
   ![Képernyőkép a Wi-Fi engedélyezéséről, a hálózati SSID és a hálózattípus konfigurálásáról a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-network.png)

6. Válassza az **Enroll in Azure AD** (Regisztrálás az Azure AD-ban) lehetőséget, adja meg a **Bulk Token Expiry** (Csoportos jogkivonat lejárati ideje) értékét, majd válassza a **Get Bulk Token** (Csoportos jogkivonat beszerzése) elemet.
   ![Képernyőkép a fiókkezelésről a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-account.png)

7. A csoportos jogkivonat beszerzéséhez meg kell adnia az Azure AD-beli hitelesítő adatait.
   ![Képernyőkép a Windows Configuration Designerbe való bejelentkezésről](./media/windows-bulk-enroll/bulk-enroll-cred.png)

8. Ha a **Bulk Token** (Csoportos jogkivonat) sikeresen letöltődött, kattintson a **Next** (Tovább) gombra.

9. Az **Add applications** elemmel alkalmazásokat, az **Add certificates** elemmel tanúsítványokat vehet fel az eszközökre. A megadott alkalmazások és tanúsítványok telepítve lesznek az eszközön.

10. Igény esetén a kiépítési csomagot jelszóval is védheti.  Kattintson a **Létrehozás**gombra.
    ![Képernyőkép a csomagvédelemről a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-create.png)

## <a name="provision-devices"></a>Eszközök üzembe helyezése

1. Keresse meg a kiépítési csomagot abban a mappában, amelyet az alkalmazásban a **Project folder** mezőben megadott.

2. Válassza ki azt a módszert, amellyel a kiépítési csomagot alkalmazni szeretné az eszközre.  A kiépítési csomagot az alábbi módszerekkel lehet eszközre alkalmazni:
   - Másolja a kiépítési csomagot USB-meghajtóra, majd csatlakoztassa az USB-meghajtót a csoportosan regisztrálni kívánt eszközhöz, majd a kezdeti beállításnál alkalmazza a csomagot.
   - Helyezze el a kiépítési csomagot egy hálózati mappába, és alkalmazza azt a kezdeti beállítás után

   A kiépítési csomag használatának részletes leírását megtalálja a [Kiépítési csomag alkalmazása](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package) című témakörben.

3. A csomag alkalmazása után az eszköz egy percen belül automatikusan újraindul.
   ![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](./media/windows-bulk-enroll/bulk-enroll-add.png)

4. Az újraindítás után az eszköz automatikusan csatlakozik az Azure Active Directoryhoz, és regisztrálódik a Microsoft Intune-ban.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windowsos eszközök csoportos regisztrálásával kapcsolatos hibaelhárítás

### <a name="provisioning-issues"></a>Kiépítéssel kapcsolatos problémák
A kiépítés alapvetően új windowsos eszközök esetében használható. Kiépítési hibák esetén szükség lehet az összes adat törlésére, vagy az eszköz rendszerindító lemezképből való helyreállítására. Az alábbi példák egyes kiépítési hibákhoz adnak magyarázatot:

- Ha egy kiépítési csomaggal olyan Active Directory-tartományhoz vagy Azure Active Directory-bérlőhöz próbál csatlakozni, amely nem hoz létre helyi fiókot, akkor az eszköz elérhetetlenné válhat, ha a tartományhoz való csatlakozás hálózati hiba miatt meghiúsul.
- A kiépítési csomag által futtatott parancsfájlok rendszerkörnyezetben futnak. A parancsfájlok tetszőleges módosításokat képesek végrehajtani az eszköz fájlrendszerében és konfigurációiban. Egy rosszindulatú vagy hibás szkript azt eredményezheti, hogy az eszközt csak a rendszerkép alaphelyzetbe állításával vagy az összes adat törlésével lehet helyreállítani.

A csomagban található beállítások sikerességét vagy hibáját a **kiépítési diagnosztika – szolgáltató** rendszergazdai bejelentkezés eseménynaplóban tekintheti meg.

### <a name="bulk-enrollment-with-wi-fi"></a>Csoportos regisztrálás Wi-Fivel 

Ha nem nyitott hálózatot használ, az [eszköz szintű tanúsítványokat](../protect/certificates-configure.md) kell használnia a kapcsolatok elindításához. A tömegesen beléptetett eszközök nem használhatók a felhasználó által megrendelt tanúsítványokhoz a hálózati hozzáféréshez. 

### <a name="conditional-access"></a>Conditional Access
A feltételes hozzáférés nem érhető el a csoportos regisztráció használatával beléptetett Windows-eszközökhöz.
