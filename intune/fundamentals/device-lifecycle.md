---
title: A Microsoft Intune mobileszköz-kezelési életciklusának áttekintése
description: Ismerje meg, hogyan segíti az Intune az eszközök kezelését a teljes életciklusuk alatt a regisztrációtól a beállításon át a végső kivonásig.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 414476389a36cdfafd9169d449ea11adf6e68efd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731703"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>A Microsoft Intune mobileszköz-kezelési életciklusának áttekintése

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Valamennyi Ön által kezelt eszköz rendelkezik *életciklussal*. Az Intune segít ennek az életciklusnak a kezelésében a regisztrációtól a beállításon és védelmen át egészen az eszköz kivonásáig, amikor már nincs rá szükség.

![Az eszközök életciklusa](./media/device-lifecycle/device-lifecycle.png "Az eszközök életciklusa az Intune-ban")

## <a name="enroll"></a>Regisztrálás
A mai mobileszköz-kezelési (MDM) stratégiák számos különböző telefont, táblagépet és számítógépet kezelnek (iOS, Android, Windows és Mac OS X). Ha szükség van az eszköz felügyeletére – és a vállalati tulajdonú eszközök esetében általában ez a helyzet –, akkor az első lépés [beállítani az eszköz regisztrációját](../enrollment/device-enrollment.md). Windows rendszerű számítógépeket is kezelhet, ha regisztrálja azokat az Intune-ban (MDM), vagy [telepíti az Intune ügyfélszoftverét](../manage-windows-pcs-with-microsoft-intune.md).

## <a name="configure"></a>Konfigurálás
Az eszközök regisztrálása csak az első lépés. Az Intune teljes funkcionalitásának kihasználásához, valamint az eszközök biztonságosságának és a vállalati előírásoknak való megfelelőségének biztosításához számos szabályzat közül választhat. Ezek segítségével a felügyelt eszközök működésének szinte minden vetületét meghatározhatja. Szeretné például, hogy a felhasználóknak jelszót kelljen megadniuk a vállalati adatokat tartalmazó eszközök használatához? A jelszó használata kötelezővé tehető. Rendelkezik vállalati Wi-Fi eléréssel? Ha igen, automatikusan konfigurálhatja. Az elérhető konfigurációs lehetőségek a következők:

- [**Eszköz konfigurációja**](../configuration/device-profiles.md). Ezekkel a szabályzatokkal beállíthatja a felügyelt eszközök szolgáltatásainak és funkcióinak működését. Előírhatja például jelszó használatát a Windows Phone-telefonokon, vagy letilthatja a kamera használatát az iPhone-okon.
- [**Vállalati erőforrás-hozzáférés**](../configuration/device-profiles.md). Ha engedélyezi a felhasználóknak a munkájukhoz kapcsolódó anyagok elérését a saját, személyes eszközükről, ez több megoldandó feladatot is teremthet. Például hogyan gondoskodik az olyan eszközök megfelelő beállításáról, amelyeknek hozzá kell férniük a vállalati levelezéshez? Hogyan biztosítja a hozzáférést a vállalati hálózathoz VPN-kapcsolaton keresztül anélkül, hogy bonyolult beállításokat kellene elvégezniük a felhasználóknak? Az Intune segítségével úgy csökkentheti ezt a terhet, hogy automatikusan konfigurálja a felügyelt eszközök közös vállalati erőforrásokhoz való hozzáférését.
- [**Windows rendszerű számítógépek felügyeleti szabályzatai (Intune ügyfélszoftverrel)** ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Jóllehet a legszéleskörűbb eszközfelügyeleti lehetőségeket az nyújtja, ha a Windows rendszerű számítógépeket regisztrálja az Intune-ban, az Intune továbbra is támogatja a Windows rendszerű számítógépek felügyeletét az Intune ügyfélszoftverrel. Ha információt szeretne azzal kapcsolatban, milyen feladatokat hajthat végre a számítógépekkel, kezdje itt.

## <a name="protect"></a>védelme
A modern informatikai világban az eszközök jogosulatlan hozzáférés elleni védelme az egyik legfontosabb feladat. Az eszközök életciklusának **Konfigurálás** lépésében található lehetőségek mellett az Intune további olyan funkciókat kínál, amelyek segítenek megvédeni a felügyelt eszközöket az illetéktelen hozzáféréstől és a rosszindulatú támadásoktól:
- [**Többtényezős hitelesítés**](../enrollment/multi-factor-authentication.md). Ez a megoldás még biztonságosabbá teszi az eszközöket azzal, hogy a felhasználók bejelentkezési folyamatába egy további hitelesítési réteget iktat. Számos eszköz támogatja a többtényezős hitelesítést, azaz előírja egy második hitelesítési szint teljesítését is – például telefonhívást vagy SMS-t – ahhoz, hogy a felhasználók hozzáférést kapjanak.
- [**Vállalati Windows Hello-beállítások**](../protect/windows-hello.md). A Vállalati Windows Hello egy alternatív bejelentkezési módszer, mellyel a felhasználók *mozdulatok* segítségével, például ujjlenyomattal vagy a Windows Hello funkcióval jelentkezhetnek be anélkül, hogy jelszót kellene megadniuk.
- [**Szabályzatok a Windows rendszerű számítógépek védelméhez (Intune ügyfélszoftverrel)** ](../policies-to-protect-windows-pcs-in-microsoft-intune.md). A Windows rendszerű számítógépek Intune ügyfélszoftverrel való felügyelete esetén olyan szabályzatok állnak rendelkezésre, amelyekkel meghatározhatja az Endpoint Protection, a szoftverfrissítések és a Windows tűzfal beállításait a felügyelt számítógépeken.

## <a name="retire"></a>Kivonás
Az eszközök elvesztése, ellopása vagy lecserélése esetén, illetve ha a felhasználók más helyre vagy beosztásba kerülnek, az adott eszközt általában [ki kell vonni vagy törölni kell a tartalmát](../remote-actions/device-management.md). Ezt többféleképpen is megteheti, például alaphelyzetbe állíthatja az eszközt vagy megszüntetheti a felügyeletét és törölheti az eszközön található vállalati adatokat.

## <a name="next-steps"></a>További lépések

- Tudnivalók a [Microsoft Intune eszközök kezeléséről](../remote-actions/device-management.md)
