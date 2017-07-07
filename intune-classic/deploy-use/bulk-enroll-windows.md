---
title: "Windows 10-es eszközök csoportos regisztrálása"
description: "Csoportos regisztrációs csomag létrehozása a Microsoft Intune-hoz"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0053e37a-f26e-452f-9524-5039a635b52e
ms.reviewer: damionw
ms.custom: intune-classic
ms.openlocfilehash: ab52ba70403da5192cd3539dfd6d1e64bd79268c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windowsos eszközök csoportos regisztrálása

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

A rendszergazda nagy számú új windowsos eszközt csatlakoztathat az Azure Active Directoryhoz és az Intune-hoz. Ha az Azure AD-bérlőhöz csoportosan szeretne eszközöket regisztrálni, először a Windows Configuration Designer (WCD) alkalmazással létre kell hoznia egy kiépítési csomagot. Ha a kiépítési csomagokat céges tulajdonban lévő eszközökre alkalmazza, az eszközök az Azure AD-bérlőhöz lesznek csatlakoztatva, és regisztrálódnak az Intune-felügyeletben. A csomag alkalmazása után az Azure AD-felhasználók bejelentkezhetnek az eszközökre.

Az Azure AD-felhasználók általános jogú felhasználók ezeken az eszközökön, és megkapják a hozzájuk rendelt Intune-szabályzatokat és a kötelező alkalmazásokat. Az önkiszolgáló és a Céges portált használó forgatókönyvek jelenleg nem támogatottak.

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windowsos eszközök csoportos regisztrációjának előfeltételei

Windowsos eszközök csoportos regisztrálásához az alábbiak szükségesek:

- A Windows 10 alkotói frissítését vagy újabb verziót futtató eszközök
- [Windowsos eszközök automatikus regisztrációja](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Kiépítési csomag létrehozása

1. Töltse le a [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) alkalmazást a Windows Áruházból.
![A Windows Configuration Designer alkalmazás áruházbeli képernyőképei és ismertetője](../media/bulk-enroll-store.png)

2. Nyissa meg a **Windows Configuration Designer** alkalmazást, és válassza a **Provision desktop devices** (Asztali eszközök kiépítése) elemet.
![Képernyőkép a Provision desktop services elem kiválasztásáról a Windows Configuration Designerben](../media/bulk-enroll-select.png)

3. Megnyílik egy **New project** (Új projekt) ablak, ahol az alábbiakat kell megadnia:
  - **Name** (Név) – A projekt neve
  - **Project folder** (Projektmappa) – A projekt mentési helye
  - **Description** (Leírás) – A projekt leírása (nem kötelező) ![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-name.png)

4.  Adjon meg egyedi neveket az eszközök számára. A névben szerepelhet sorozatszám (%%SERIAL%%) vagy véletlenszerű karaktersorozat. Megadhat továbbá termékkulcsot arra az esetre, ha másik Windows-kiadásra vált, konfigurálhatja az eszközt közös használatra, és eltávolíthatja az előre telepített szoftvereket.<BR>
![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-device.png)

5.  Lehetőség van arra is, hogy beállítsa, mely Wi-Fi-hálózathoz csatlakozzanak az eszközök az első indításkor.  Ha ez nincs megadva, az eszköz első indításakor vezetékes hálózati kapcsolatra lesz szükség.
![Képernyőkép a Wi-Fi engedélyezéséről, a hálózati SSID és a hálózattípus konfigurálásáról a Windows Configuration Designerben](../media/bulk-enroll-network.png)

6.  Válassza az **Enroll in Azure AD** (Regisztrálás az Azure AD-ban) lehetőséget, adja meg a **Bulk Token Expiry** (Csoportos jogkivonat lejárati ideje) értékét, majd válassza a **Get Bulk Token** (Csoportos jogkivonat beszerzése) elemet.
![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-account.png)

7. A csoportos jogkivonat beszerzéséhez meg kell adnia az Azure AD-beli hitelesítő adatait.
![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-cred.png)

8.  Ha a **Bulk Token** (Csoportos jogkivonat) sikeresen letöltődött, kattintson a **Next** (Tovább) gombra.

9. Az **Add applications** elemmel alkalmazásokat, az **Add certificates** elemmel tanúsítványokat vehet fel az eszközökre. A megadott alkalmazások és tanúsítványok telepítve lesznek az eszközön.

10. Igény esetén a kiépítési csomagot jelszóval is védheti.  Kattintson a **Létrehozás** gombra.
![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-create.png)

## <a name="provision-devices"></a>Eszközök üzembe helyezése

1. Keresse meg a kiépítési csomagot abban a mappában, amelyet az alkalmazásban a **Project folder** mezőben megadott.

2. Válassza ki azt a módszert, amellyel a kiépítési csomagot alkalmazni szeretné az eszközre.  A kiépítési csomagot az alábbi módszerekkel lehet eszközre alkalmazni:
 - Másolja a kiépítési csomagot USB-meghajtóra, majd csatlakoztassa az USB-meghajtót a csoportosan regisztrálni kívánt eszközhöz, majd a kezdeti beállításnál alkalmazza a csomagot.
 - Másolja a kiépítési csomagot egy hálózati meghajtóra, majd a kezdeti beállításnál alkalmazza a csomagot a csoportosan regisztrálni kívánt eszközre.

 A kiépítési csomag használatának részletes leírását megtalálja a [Kiépítési csomag alkalmazása](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package) című témakörben.

3. A csomag alkalmazása után az eszköz 1 percen belül automatikusan újraindul.
 ![Képernyőkép a név, a projektmappa és a leírás megadásáról a Windows Configuration Designerben](../media/bulk-enroll-add.png)

4. Az újraindítás után az eszköz automatikusan csatlakozik az Azure Active Directoryhoz, és regisztrálódik a Microsoft Intune-ban.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windowsos eszközök csoportos regisztrálásával kapcsolatos hibaelhárítás

A kiépítés alapvetően új windowsos eszközök esetében használható. Kiépítési hibák esetén szükség lehet a gyári beállítások visszaállítására, vagy az eszköz rendszerindító lemezképből való helyreállítására. Az alábbi példák egyes kiépítési hibákhoz adnak magyarázatot:

- Ha egy kiépítési csomaggal olyan Active Directory-tartományhoz vagy Azure Active Directory-bérlőhöz próbál csatlakozni, amely nem hoz létre helyi fiókot, akkor az eszköz elérhetetlenné válhat, ha a tartományhoz való csatlakozás hálózati hiba miatt meghiúsul.
- A kiépítési csomag szkriptjei rendszerkörnyezetben futnak, és bármilyen módosítást képesek elvégezni az eszköz fájlrendszerén és konfigurációján. Egy rosszindulatú vagy hibás szkript azt eredményezheti, hogy az eszközt csak a rendszerkép alaphelyzetbe állításával vagy a gyári beállítások visszaállításával lehet helyreállítani.
