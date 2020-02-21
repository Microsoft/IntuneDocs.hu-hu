---
title: Az eszközök műveleteinek Microsoft Intune – Azure | Microsoft Docs
description: Segítség kérése az eszköz működésével kapcsolatos hibák elhárításához.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 545f287e8b7ee82e2008f239171b22e01714b8c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514744"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Eszközök műveleteinek hibáinak megoldása az Intune-ban

A Microsoft Intune számos olyan műveletet tartalmaz, amelyek segítségével felügyelheti az eszközöket. Ez a cikk az eszközök műveleteinek megoldásához segítséget nyújtó gyakori kérdésekre ad választ.

## <a name="disable-activation-lock-action"></a>Aktiválási zár művelet letiltása

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Rákattintottam a "letiltás Aktiválási zár" műveletet a portálon, de semmi nem történt az eszközön.
Ez a várt érték. A letiltási Aktiválási zár művelet megkezdése után az Intune egy frissített kódot kér az Apple-től. Ha az eszköz a Aktiválási zár képernyőn látható, manuálisan írja be a kódot a PIN-kód mezőbe. Ez a kód 15 napig érvényes, ezért ügyeljen rá, hogy a törlés előtt kattintson a műveletre, és másolja a kódot.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-iosipados-device"></a>Miért nem látom a Letiltás Aktiválási zár kódot az iOS/iPadOS eszköz hardver áttekintés paneljén?
A legvalószínűbb ok a következők:
- A kód lejárt, és törölve lett a szolgáltatásból.
- Az eszköz nem felügyeli az eszköz korlátozási szabályzatát, hogy engedélyezze Aktiválási zár.

A kódot a Graph Explorerben a következő lekérdezéssel tekintheti meg:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-iosipados-device"></a>Miért szürke a Letiltás Aktiválási zár művelet az iOS/iPadOS eszközön?
A legvalószínűbb ok a következők: 
- A kód lejárt, és törölve lett a szolgáltatásból.
- Az eszköz nem felügyeli az eszköz korlátozási szabályzatát, hogy engedélyezze Aktiválási zár.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>A letiltási Aktiválási zár kódja kis-és nagybetűket?
Nem. És nem kell megadnia a kötőjeleket.

## <a name="remove-devices-action"></a>Eszközök eltávolítása művelet

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Hogyan eldönteni, ki kezdte kivonni/törölni a kivonást?
A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)lépjen a **bérlői felügyelet** > a **naplók** > ellenőrizze a **kezdeményezett oszlop alapján** .
Ha nem lát bejegyzést, a legvalószínűbb, hogy kezdeményezte a műveletet az eszköz felhasználója. Valószínűleg használták a Céges portál alkalmazást vagy a portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Miért nem távolította el az alkalmazást a kivonást követően?
Mivel nem tekintették felügyelt alkalmazásnak. Ebben a kontextusban egy felügyelt alkalmazás az Intune szolgáltatással telepített alkalmazás. Ez a következő teendőket foglalja magában:
- Az alkalmazás központi telepítése kötelező
- Az alkalmazás elérhetőként lett telepítve, majd a végfelhasználó telepíti a Céges portál alkalmazásból.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Miért van szürkén kitörölve az androidos vállalati munkahelyi Profilos eszközökön?
Ez az elvárt működés. A Google nem engedélyezi a munkahelyi Profilos eszközök gyári alaphelyzetbe állítását a MDM-szolgáltatótól.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Miért tudok újra bejelentkezni az Office-alkalmazásokba az eszköz kivonása után?
Mivel az eszköz kivonása nem vonja vissza a hozzáférési jogkivonatokat. A feltételes hozzáférési szabályzatok segítségével csökkentheti ezt a feltételt.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Hogyan figyelhető meg a kivonási/törlési művelet a kibocsátás után?
A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)lépjen a **bérlői felügyelet** > **naplók**elemre.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>A törlési műveletek miért nem a határozatlan idejű függőben jelenjenek meg?
Az eszközök az Alaphelyzetbe állítás elindítása előtt nem jelentik vissza az állapotukat az Intune szolgáltatásnak. Így a művelet függőként jelenik meg. Ha megerősítette a művelet sikerességét, törölje az eszközt a szolgáltatásból.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Mi történik, ha elindítok egy kivonást vagy adattörlést egy offline eszközön vagy olyan eszközön, amely még nem kommunikált a szolgáltatással?
Az eszköz kivonási **/törlési** állapotban marad mindaddig, amíg az Mdm-tanúsítvány le nem jár. Az MDM-tanúsítvány egy évig tart a regisztrációtól, és minden évben automatikusan megújítható. Ha az eszköz a MDM-tanúsítvány lejárata előtt jelentkezik be, a rendszer kivonja vagy törli. Ha az eszköz nem kerül be a MDM-tanúsítvány lejárta előtt, akkor nem fog tudni bejelentkezni a szolgáltatásba. 180 nappal az MDM-tanúsítvány lejárta után a rendszer automatikusan eltávolítja az eszközt a Azure Portal.


## <a name="reset-passcode-action"></a>Jelszó alaphelyzetbe állítása művelet

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>A PIN-kód alaphelyzetbe állítása művelet miért szürkén jelenik meg az Android-eszköz adminisztrátorának regisztrált eszközén?
A váltságdíjat elleni küzdelem érdekében a Google eltávolította a PIN-kód alaphelyzetbe állítása funkciót az eszköz felügyeleti API-ban (az Android 7,0-es vagy újabb verziójára vonatkozik).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Miért kapok "nem támogatott" üzenetet, amikor új PIN-kódot ad ki az Android 8,0-es vagy újabb munkahelyi profilhoz regisztrált eszközre?
Mivel az alaphelyzetbe állítási jogkivonat nincs aktiválva az eszközön. Az alaphelyzetbe állítási jogkivonat aktiválása:
1. A konfigurációs szabályzatban munkahelyi profilhoz tartozó PIN-kódot kell megadnia.
2. A végfelhasználónak meg kell adnia egy megfelelő munkahelyi profilhoz tartozó PIN-kódot.
3. A felhasználónak el kell fogadnia a másodlagos kérést, hogy engedélyezze a PIN-kód alaphelyzetbe állítását.
A lépések elvégzése után többé nem kell megkapnia ezt a választ.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-iosipados-device-when-i-issue-the-remove-passcode-action"></a>Miért kérik új PIN-kód beállítását az iOS/iPadOS eszközön a PIN-kód eltávolítása művelet kiadása során?
Mivel az egyik megfelelőségi szabályzathoz PIN-kód szükséges.


## <a name="wipe-action"></a>Az Összes adat törlése művelet

### <a name="i-cant-restart-a-windows-10-device-after-using-the-wipe-action"></a>Nem tudok újraindítani egy Windows 10-es eszközt a törlési művelet használata után
Ennek oka az, hogy a válassza ki az **eszközt, és továbbra is törli a törlést, még akkor is, ha az eszközök elvesztik a teljesítményt. Ha ezt a beállítást választja, vegye figyelembe, hogy előfordulhat, hogy a Windows 10 rendszerű eszközök újraindulnak.** Windows 10 rendszerű eszközön.

Ez akkor fordulhat elő, ha a Windows telepítése jelentős sérülést okoz, amely megakadályozza az operációs rendszer újratelepítését. Ebben az esetben a folyamat meghiúsul, és a [Windows helyreállítási környezetben]( https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)elhagyja a rendszert.

### <a name="i-cant-restart-a-bitlocker-encrypted-device-after-using-the-wipe-action"></a>A törlési művelet használata után nem lehet újraindítani a BitLocker által titkosított eszközt
Ennek oka az, hogy a válassza ki az **eszközt, és továbbra is törli a törlést, még akkor is, ha az eszközök elvesztik a teljesítményt. Ha ezt a beállítást választja, vegye figyelembe, hogy előfordulhat, hogy a Windows 10 rendszerű eszközök újraindulnak.** lehetőség egy BitLocker-titkosítású eszközön.

A probléma megoldásához a rendszerindító adathordozó használatával telepítse újra a Windows 10 rendszert az eszközön.


## <a name="next-steps"></a>További lépések

Kérjen [támogatási segítséget a Microsofttól](../fundamentals/get-support.md), vagy használja a [közösségi fórumokat](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
