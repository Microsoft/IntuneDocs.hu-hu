---
title: Felhasználók által is látható Céges portál-üzenetek az eszközökön
titleSuffix: Microsoft Intune
description: A cikk azokat az üzeneteket ismerteti, amelyeket a végfelhasználók láthatnak a Céges portálon.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57467d3d073666c1c22ac0a412f68a258d5b3d75
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414073"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>A Vállalati portál alkalmazás üzeneteinek ismertetése a végfelhasználókkal

> [!NOTE]
> Az alábbi információk csak az Android 6.0 + és az iOS 10 + rendszerű eszközökre vonatkoznak.

A cikk azokat az alkalmazásüzeneteket ismerteti, amelyeket a végfelhasználók láthatnak a Céges portálon. Az alkalmazásüzenetek általában a regisztrációs folyamat különféle szakaszaiban jelennek meg. A cikk bemutatja, hol jelennek meg az üzenetek, milyen konkrét jelentésük van, és hogy mi történik, ha a felhasználók nem adnak hozzáférést. Ezen kívül megtudhatja, hogyan érdemes az üzeneteket ismertetni a felhasználók számára.

- __Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)__
- __Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)__

> [!NOTE]
> A szolgáltatás által gyűjtött adatokat semmilyen okból nem adjuk át harmadik félnek.

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)

### <a name="where-it-appears"></a>Megjelenési helye

Az **Allow Company Portal to make and manage phone calls?** (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?) üzenet akkor jelenik meg, amikor az eszköz regisztrációja során a felhasználók a **Regisztráció** elemre koppintanak a Vállalati portál alkalmazásban.

### <a name="what-it-means"></a>Jelentés

Megerősítő válasszal a felhasználó engedélyezi, hogy az eszköz telefonszámát és IMEI-számát elküldje a rendszer az Intune szolgáltatásnak. Ezek az információk a felügyeleti konzol __Hardver__ lapján jelennek meg.

> [!NOTE]
> **A Munkahelyi portál alkalmazás soha nem indít telefonhívásokat, és nem is kezeli azokat.** Az üzenet szövegét a Google szabja meg, és nem módosítható.

A **Hardver** lap megnyitásához válassza a **Csoportok** > **Minden mobileszköz** > **Eszközök** lehetőséget. Jelölje ki a felhasználó eszközét, és válassza a **Tulajdonságok megjelenítése** > **Hardver** lehetőséget.

### <a name="what-happens-if-users-deny-access"></a>Mi történik, ha a felhasználók nem engedélyezik a hozzáférést

Ha a felhasználó nem engedélyezi a hozzáférést, attól továbbra is használhatja a Vállalati portál alkalmazást, és regisztrálhatja az eszközeit. Az eszköz telefonszáma és IMEI-száma azonban ebben az esetben nem jelenik meg a felügyeleti konzol __Hardver__ lapján. Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését.

Ha a felhasználó engedélyezi a hozzáférést, de később megtagadja azt, az üzenet újból megjelenik, amikor a felhasználó a regisztrálást követően először bejelentkezik a Vállalati portál alkalmazásba.

Amennyiben a felhasználók később ismét engedélyezni szeretnék a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Telefon** lapon tehetik ezt meg.

### <a name="how-to-explain-this-to-your-users"></a>A felhasználók tájékoztatásának módja

További információért ajánlja a felhasználóknak az [Android-eszközök regisztrálása az Intune-ban](/intune-user-help/enroll-device-android-company-portal) című témakört.

## <a name="allow-company-portal-to-access-your-contacts"></a>Engedélyezi, hogy a Vállalati Portál hozzáférjen a névjegyekhez?

### <a name="where-it-appears"></a>Megjelenési helye

Az **Allow Company Portal to access your contacts?** (Engedélyezi, hogy a Munkahelyi portál alkalmazás hozzáférjen a névjegyekhez?) üzenet akkor jelenik meg, amikor az eszköz regisztrációja során a felhasználók a **Regisztráció** elemre koppintanak a Vállalati portál alkalmazásban.

### <a name="what-it-means"></a>Jelentés

Megerősítő válasszal a felhasználó engedélyezi az Intune számára, hogy létrehozza munkahelyi fiókjukat és kezelje az eszköz felhasználójához regisztrált Active Directory-identitást.

> [!NOTE]
> **A Microsoft soha nem fér hozzá a névjegyeihez!** Az üzenet szövegét a Google szabja meg, és nem módosítható.

### <a name="what-happens-if-users-deny-access"></a>Mi történik, ha a felhasználók nem engedélyezik a hozzáférést

Ha a felhasználó tiltja a hozzáférést, az eszköz nem regisztrál az Intune-ban és nem felügyelhető. Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését.

Ha a felhasználó engedélyezi a hozzáférést, de később megtagadja azt, az üzenet újból megjelenik, amikor a felhasználó a regisztrálást követően először bejelentkezik a Vállalati portál alkalmazásba.

Amennyiben a felhasználók később ismét engedélyezni szeretnék a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Telefon** lapon tehetik ezt meg.

### <a name="how-to-explain-this-to-your-users"></a>A felhasználók tájékoztatásának módja

További információért ajánlja a felhasználóknak az [Android-eszközök regisztrálása az Intune-ban](/intune-user-help/enroll-device-android-company-portal) című témakört.  

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)

### <a name="where-it-appears"></a>Megjelenési helye

Az **Allow Company Portal to access photos, media, and files on your device?** (Engedélyezi a Vállalati portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?) üzenet akkor jelenik meg, ha a felhasználó az **Adatok elküldése** elemre koppintva naplókat küld a rendszergazdának.

### <a name="what-it-means"></a>Jelentés

Megerősítő válasszal a felhasználó engedélyezi, hogy eszköze adatnaplókat írjon az eszköz SD-kártyájára.Megerősítő válasszal a felhasználó engedélyezi, hogy eszköze adatnaplókat írjon az eszköz SD-kártyájára. Azt is engedélyezi továbbá, hogy a rendszer ezeket a naplókat USB-kábel segítségével más helyre másolja.   

> [!NOTE]
> **A Munkahelyi portál alkalmazás sohasem próbál hozzáférni a felhasználó fényképeihez, médiatartalmaihoz és fájljaihoz.** Az üzenet szövegét a Google szabja meg, és nem módosítható.

### <a name="what-happens-if-users-deny-access"></a>Mi történik, ha a felhasználók nem engedélyezik a hozzáférést

Ha a felhasználó nem engedélyezi a hozzáférést, e-mailben akkor is elküldheti az adatnaplókat, ám azok nem másolhatók az SD-kártyára.

Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését. Ha a felhasználó engedélyezi a hozzáférést, de később megtagadja, az üzenet újból megjelenik, amikor a felhasználó a legközelebb megpróbálja elküldeni a naplókat. Amennyiben azonban a felhasználók később ismét engedélyezni szeretnék a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Tárterület** lapon tehetik ezt meg.


### <a name="how-to-explain-this-to-your-users"></a>A felhasználók tájékoztatásának módja

Ajánlja a felhasználóknak a [Naplók elküldése a rendszergazdának e-mailben](/intune-user-help/send-logs-to-your-it-admin-by-email-android) című témakört. 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>A céges ügyfélszolgálatnak hozzáférést kell nyújtania Önnek a céges erőforrásokhoz

### <a name="where-it-appears"></a>Megjelenési helye

Ha nem adta hozzá a Céges portált az **Engedélyezett alkalmazások** vagy a **Mentesített alkalmazások** listájához, és egy felhasználó megpróbál bejelentkezni, a bejelentkezés meghiúsul. Az alábbi üzenet jelenik meg:

> **A céges ügyfélszolgálatnak hozzáférést kell nyújtania Önnek a céges erőforrásokhoz**  
> A cége a Windows Információvédelem szabályzataival védi az eszközt. A céges ügyfélszolgálatnak biztosítania kell, hogy engedélyezze a Céges portálnak a hozzáférést ezekhez az erőforrásokhoz.

### <a name="what-it-means"></a>Jelentés

Adja hozzá a Céges portál az **engedélyezett alkalmazások** vagy a **mentesített alkalmazások** listájához a Windows Information Protection (folyamatban lévő) alkalmazás-védelmi házirendben. További információ: [A Windows Információvédelem (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése az Intune használatával](../apps/windows-information-protection-policy-create.md).

## <a name="approve-a-ios-company-app-line-of-business-app-on-your-ios-device"></a>IOS-es vállalati alkalmazás jóváhagyása (üzletági alkalmazás) iOS-eszközön 

### <a name="where-it-appears"></a>Megjelenési helye

a szervezet által fejlesztett, az App Store-ban nem elérhető iOS-alkalmazásokat az eszköz alapértelmezés szerint nem megbízhatónak minősíti. Ha a Céges portál használatával telepíti az alkalmazásokat, és elindítja az alkalmazást, a következő üzenet jelenik meg:

![iOS-alkalmazás üzenete – nem megbízható nagyvállalati fejlesztő](./media/end-user-company-portal-messages/end-user-company-portal-messages-01.png)

### <a name="what-it-means"></a>Jelentés

Ez az üzenet azt jelenti, hogy módosítania kell az iOS-eszköz beállításait a vállalat által az iOS-eszközön fejlesztett alkalmazások jóváhagyásához és telepítéséhez.

Ha az alkalmazásokat a Céges portál használatával telepíti, és elindítja az alkalmazást, az alábbi lépéseket követve jóváhagyhatja az alkalmazást a letöltés után:

1. A telepített vállalati alkalmazások (üzletági alkalmazások) indításakor a "nem megbízható nagyvállalati fejlesztő" üzenet jelenik meg. <br>
   Nyomja meg a **Mégse**gombot.
2. Navigáljon a **beállítások** > **általános** > **eszközök kezelése**elemre.

   ![iOS-eszköz felhasználói felülete – eszközkezelés](./media/end-user-company-portal-messages/end-user-company-portal-messages-02.png)

3. Válassza a **felügyeleti profil** > **vállalati alkalmazás**lehetőséget.
4. Válassza ki a fejlesztő nevét.
5. Kattintson a **megbízhatóság _fejlesztő neve_** gombra.
6. Erősítse meg az alkalmazást úgy, hogy kijelöli a **megbízhatóság** lehetőséget az alkalmazás telepítése előugró üzenetben.

   ![iOS-eszköz felhasználói felülete – megbízhatósági alkalmazás üzenete](./media/end-user-company-portal-messages/end-user-company-portal-messages-03.png)

    Képesnek kell lennie a vállalati alkalmazás indítására és használatára.


## <a name="see-also"></a>További információ
[Mit kell tudniuk a végfelhasználóknak az Intune használatáról?](end-user-educate.md)
