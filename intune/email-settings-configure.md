---
title: E-mail-beállítások konfigurálása a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: E-mail-profilt hozhat létre a Microsoft Intune-ban, majd üzembe helyezheti ezt a profilt Android Enterprise-, iOS- és Windows-eszközökön. E-mail-profil használatával olyan gyakori e-mail-beállítások konfigurálhatók, mint a levelezési kiszolgáló, és az Ön által felügyelt eszközökön a vállalati levelezéshez való csatlakozáshoz használt hitelesítési módszer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a534aef3cdb989376dc1c148abedfb4f4e4f78b
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71162886"
---
# <a name="add-email-settings-to-devices-using-intune"></a>E-mail-beállítások hozzáadása az Intune-t használó eszközökhöz

A Microsoft Intune különböző e-mail-beállításokat tartalmaz, amelyeket alkalmazhat a vállalati eszközökön. A rendszergazda e-mail-profilokat hoz létre a levelezési kiszolgálóhoz való kapcsolódáshoz, például az Office 365-hez és a Gmailhez. A végfelhasználók ezután összekapcsolják, hitelesítik és szinkronizálják a szervezeti e-mail-fiókjaikat a mobileszközökön. E-mail-profil létrehozásával és üzembe helyezésével ellenőrizheti, hogy a beállítások szabványosak-e számos eszközön. Ezáltal a helyes e-mail-beállításokat nem ismerő végfelhasználóktól érkező támogatási hívások száma is csökkenthető.

E-mail-profilok segítségével a következő eszközökön konfigurálhatók a beépített e-mail-beállítások:

- Android Samsung Knox Standard (4.0-s és újabb verziók)
- Vállalati Android
- iOS 8.0 és újabb verziók
- Windows Phone 8.1 és újabb verziók
- Windows 10 (asztali rendszer) és Windows 10 Mobile

Ez a cikk azt mutatja be, hogyan hozható létre e-mail-profil a Microsoft Intune-ban. Az egyes platformok különleges beállításaira mutató hivatkozásokat is tartalmaz.

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. A megfelelő házirend neve például az **összes Windows-eszköz e-mail-beállításai**.
    - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza ki az eszközök platformját. A választható lehetőségek:

        - **Android** (csak Samsung Android Knox Standard esetén)
        - **Vállalati Android**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 és újabb**

    - **Profil típusa**: Válassza az **e-mail**lehetőséget.

4. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Válassza ki a platformot a részletes beállításokhoz:

    - [Android Samsung Knox standard-beállítások](email-settings-android.md)
    - [Androidos vállalati beállítások](email-settings-android-enterprise.md)
    - [iOS-/iPadOS-beállítások](email-settings-ios.md)
    - [Windows Phone 8.1-beállítások](email-settings-windows-phone-8-1.md)
    - [Windows 10-beállítások](email-settings-windows-10.md)

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

A beállítások megadása és a profil létrehozása után a profil megjelenik a profilok listájában. A következő lépés a [profil hozzárendelése egyes csoportokhoz](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>E-mail-profil eltávolítása

Az e-mail-profilok felhasználói csoportok helyett eszközcsoportokhoz vannak hozzárendelve. Az e-mail-profilokat az eszközről többféle módon lehet eltávolítani, még akkor is, ha az eszközön csak egy e-mail-profil található:

- **1. lehetőség**: Nyissa meg az e-mail profilt (**eszköz-konfigurációs** > **profilok**), és válassza a **hozzárendelések**lehetőséget. A **Belefoglalás** lapon jelennek meg a profilhoz rendelt csoportok. Kattintson a jobb gombbal a csoportra, majd válassza az **Eltávolítás** lehetőséget. Ne felejtse el **menteni** a módosításokat.

- **2. lehetőség**: [Az eszköz törlése vagy](devices-wipe.md)kivonása. A következő műveletekkel az összes adatot és beállítást, vagy azok egy részét is eltávolíthatja.

## <a name="secure-email-access"></a>Biztonságos e-mail-hozzáférés

Az e-mail-profilok biztonsága az alábbi módszerekkel fokozható:

- **Tanúsítványok**: Az e-mail-profil létrehozásakor ki kell választania egy korábban az Intune-ban létrehozott tanúsítványsablont. Ez a tanúsítvány identitástanúsítványként is ismert. Ez hajtja végre a hitelesítést egy megbízható tanúsítványprofillal vagy főtanúsítvánnyal, így ellenőrizve, hogy a felhasználó eszközének csatlakoztatása engedélyezve van-e. A megbízható tanúsítvány az e-mail-kapcsolatot hitelesítő számítógéphez van rendelve. Ez a számítógép általában a natív levelezési kiszolgáló.

  A tanúsítványprofiloknak az Intune-ban történő létrehozásáról és használatáról a következő dokumentumban olvashat bővebben: [Tanúsítványok konfigurálása az Intune-nal](certificates-configure.md).

- **Felhasználónév és jelszó**: A végfelhasználó hitelesíti magát a natív levelezési kiszolgálón a Felhasználónév és a jelszó megadásával. A jelszó nem szerepel az e-mail-profilban. Így a végfelhasználó az e-mailekhez való csatlakozáskor megadja a jelszót.

## <a name="how-intune-handles-existing-email-accounts"></a>Hogyan kezeli az Intune a meglévő e-mail-fiókokat?

Ha a felhasználó már konfigurált e-mail-fiókot, az e-mail-profil a platformtól függően, másként lesz hozzárendelve.

- **iOS**: A rendszer az állomásnév és az e-mail-cím alapján egy már meglévő e-mail-profilt észlel. Az ugyanezeket az adatokat tartalmazó e-mail-profil megakadályozza az Intune-profil hozzárendelését. Ebben az esetben a Céges portál alkalmazás értesíti a felhasználót, hogy nem felel meg a felhasználónak, és felszólítja a felhasználót, hogy manuálisan távolítsa el a konfigurált profilt. A forgatókönyv megelőzése érdekében kérje meg a végfelhasználókat, hogy regisztráljanak az e-mail-profil telepítése *előtt* , amely lehetővé teszi az Intune számára a profil beállítását.

- **Windows:** A rendszer az állomásnév és az e-mail-cím alapján egy már meglévő e-mail-profilt észlel. Az Intune felülírja a végfelhasználó által létrehozott meglévő e-mail-profilt.

- **Android Samsung Knox standard**: A rendszer az e-mail-cím alapján egy már meglévő e-mail-profilt észlel, és felülírja az Intune-profillal. Az Android nem használ állomásnevet a profil azonosításához. Ne hozzon létre több e-mail-profilt ugyanazt az e-mail-címet több állomáson használva. A profilok felülírják egymást.

- **Androidos munkahelyi profilok**: Az Intune két androidos munkahelyi e-mail-profilt biztosít: egyet a Gmail-alkalmazáshoz, egyet pedig a Nine Work alkalmazáshoz. Ezek az alkalmazások a Google Play áruházból érhetők el, és telepíthetők az eszköz munkahelyi profiljába. Ezek az alkalmazások nem hoznak létre ismétlődő profilokat. Mindkét alkalmazás támogatja az Exchange-kapcsolatokat. E-mail-kapcsolat használatához helyezze üzembe ezeknek az levelezőalkalmazásoknak az egyikét a felhasználók eszközén. Ezután hozza létre és helyezze üzembe a megfelelő e-mail-profilt. Lehetséges, hogy egyes e-mail-alkalmazások, például a Nine Work, nem ingyenesek. Olvassa el az alkalmazás licencelési információit, vagy kérdés esetén lépjen kapcsolatba az alkalmazás kibocsátójával.

## <a name="changes-to-assigned-email-profiles"></a>Hozzárendelt e-mail-profilok módosításai

Ha egy már hozzárendelt e-mail-profilt módosít, a végfelhasználókat a rendszer arra kérheti, hogy fogadják el az e-mail-beállítások újrakonfigurálását.

## <a name="next-steps"></a>További lépések

A létrehozott profil egyelőre semmit sem csinál. Ezután [rendelje hozzá a profilt bizonyos eszközökhöz](device-profile-assign.md).
