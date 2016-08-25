---
title: "A mobileszköz-kezelési életciklus áttekintése | Microsoft Intune"
description: "Ismerje meg, hogyan segíti az Intune az eszközök kezelését a teljes életciklusuk alatt a regisztrációtól a beállításon át a végső kivonásig."
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 5140c4943be630ea8e48f80f7e6b590d223beac1
ms.openlocfilehash: 751025aa71ef41564100ea57ac0d1fe60619e214


---

# A mobileszköz-kezelés (MDM) életciklusának áttekintése

Minden Ön által kezelt eszköz rendelkezik úgynevezett *életciklussal*. Az Intune segíthet ennek az életciklusnak a kezelésében a regisztrációtól az eszköz kivonásáig, amikor már nincs rá szükség:

![Az eszközök életciklusa](./media/device-lifecycle.png "the Intune device lifecycle")

## Regisztrálás
A mai mobileszköz-kezelési (MDM) stratégiák számos különböző telefont, táblagépet és számítógépet kezelnek (iOS, Android, Windows és Mac OS X). Ha szüksége van az eszköz kezelhetőségére, ami általában a vállalati tulajdonú eszközök esetében fordul elő, akkor az első lépés az [eszközregisztráció beállítása](enroll-devices-in-microsoft-intune.md). Windows rendszerű számítógépeket is kezelhet, ha regisztrálja őket az Intune-ban (MDM), vagy [telepíti az Intune ügyfélszoftverét](manage-windows-pcs-with-microsoft-intune.md).

## Konfigurálás
Az eszközök regisztrálása csak az első lépés. Az Intune teljes kínálatának kihasználásához, valamint az eszközök biztonságosságának és a vállalati előírásoknak való megfelelőségének biztosításához számos **szabályzat** közül választhat, amelyekkel a felügyelt eszközök működésének szinte minden szempontját konfigurálhatja. Szeretné például, hogy a felhasználók jelszót használjanak a vállalati adatokhoz hozzáférő eszközökhöz? A jelszó használata kötelezővé tehető. Használ vállalati Wi-Fi-t? Ha igen, automatikusan konfigurálhatja. Az elérhető konfigurációs lehetőségek a következők:

- [**Konfigurációs szabályzatok**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) – Ezekkel a szabályzatokkal beállíthatja a felügyelt eszközök szolgáltatásainak és funkcióinak működését. Előírhatja például jelszó használatát a Windows Phone rendszerű eszközökön, vagy letilthatja a kamera használatát az iPhone-okon.
- [**Vállalati erőforrás-hozzáférési szabályzatok**](enable-access-to-company-resources-with-microsoft-intune.md) – Ha engedélyezi a felhasználóknak a munkájukhoz kapcsolódó anyagok elérését a saját eszközükről, ez több megoldandó feladatot is teremthet. Például hogyan gondoskodik az olyan eszközök megfelelő beállításáról, amelyeknek hozzá kell férniük a vállalati levelezéshez? Hogyan biztosíthatja, hogy felhasználók hozzáférhessenek a vállalati hálózathoz VPN-kapcsolaton keresztül anélkül, hogy ismerniük kellene az ehhez szükséges, gyakran bonyolult beállításokat? Az Intune segítségével úgy csökkentheti ezt a terhet, hogy automatikusan konfigurálja a felügyelt eszközök közös vállalati erőforrásokhoz való hozzáférését.
- [**Windows rendszerű számítógépek felügyeleti szabályzatai**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) – A Windows rendszerű számítógépek Intune-nal történő regisztrálásával juthat hozzá a legtöbb eszközfelügyeleti lehetőséghez, emellett az Intune továbbra is támogatja a Windows rendszerű számítógépek felügyeletét az Intune ügyfélszoftverrel. Ha tájékoztatásra van szüksége a számítógépekkel végrehajtható feladatokról, kezdje itt.

## Védelem
A modern informatikai világban az eszközök jogosulatlan hozzáférés elleni védelme az egyik legfontosabb feladat. Az eszközök életciklusának **Konfigurálás** lépésében az Intune további olyan funkciókat kínál, amelyek segítenek megvédeni a felügyelt eszközöket az illetéktelen hozzáféréstől és a rosszindulatú támadásoktól:
- [**Többtényezős hitelesítés**](protect-windows-devices-with-multi-factor-authentication.md) – Egy további hitelesítési réteggel egészíti ki a felhasználók bejelentkezését, ami még biztonságosabbá teszi az eszközöket. A Windows, a Windows Phone és a Windows Mobile rendszerű eszközök olyan többtényezős hitelesítést tartalmaznak, amely egy második hitelesítési szint teljesítését igényli – például telefonhívást vagy SMS-t – ahhoz, hogy a felhasználók hozzáférést kapjanak.
- [**Microsoft Passport-beállítások**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) – A Microsoft Passport egy alternatív bejelentkezési módszer, amellyel a felhasználók *kézmozdulat*, például egy ujjlenyomattal vagy a Windows Hello funkcióval, jelszó nélkül jelentkeznek be.
- [**Szabályzatok a Windows rendszerű számítógépek védelméhez (az Intune ügyfélszoftverrel)**](policies-to-protect-windows-pcs-in-microsoft-intune.md) – Amikor az Intune ügyfélszoftverrel kezeli a Windows rendszerű számítógépeket, olyan szabályzatok közül választhat, amelyekkel megadhatja az Endpoint Protection, a szoftverfrissítések és a Windows tűzfal beállításait a felügyelt számítógépeken.

## Kivonás
Az eszközök elvesztése, ellopása vagy szükségessé váló cseréje esetén, vagy ha a felhasználók más helyre vagy beosztásba kerülnek, az adott eszközt [ki kell vonni vagy törölni kell a tartalmát](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Ezt többféleképpen is megteheti, például alaphelyzetbe állíthatja az eszközt, megszüntetheti a felügyeletét vagy törölheti az eszközön található vállalati adatokat.



<!--HONumber=Jul16_HO2-->


