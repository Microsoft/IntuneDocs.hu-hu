---
title: Androidos vállalati munkahelyi Profilos eszközök regisztrálása az Intune-ban
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan regisztrálhat androidos vállalati munkahelyi profilokat használó eszközöket az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4339f98ed133c3426faee8bd4b18024fd2648606
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503346"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Vállalati androidos munkahelyi profilos eszközök regisztrálásának beállítása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune segítségével alkalmazásokat és beállításokat telepíthet az Android Enterprise munkahelyi Profilos eszközökre, így biztosítva, hogy a munkahelyi és a személyes adatok elkülönítve legyenek. Az Android Enterprise-ról az [Android Enterprise-követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)című témakörben olvashat részletesebben.

Az androidos vállalati munkahelyi profilok felügyeletének beállításához kövesse az alábbi lépéseket:

1. Az [Intune-bérlői fiókját az Android Enterprise-fiókjával is összekapcsolhatjuk](connect-intune-android-enterprise.md).
2. Az androidos vállalati munkahelyi profil regisztrálási beállításainak megadása. Az androidos vállalati munkahelyi profilok [csak bizonyos Android-eszközökön támogatottak](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Az Android Enterprise Work-profilokat támogató bármely eszköz támogatja az Android-eszközök rendszergazdai felügyeletét is. Az Intune segítségével megadhatja, hogy az androidos vállalati munkahelyi profilokat támogató eszközöket a [regisztrációs korlátozásokon](enrollment-restrictions-set.md)belül kell kezelni.
    - **Blokkolás**: minden Android-eszköz, beleértve az Android Enterprise Work-profilokat támogató eszközöket, az Android-eszköz rendszergazdai eszközeként lesz regisztrálva, kivéve, ha az Android-eszközök rendszergazdai regisztrációja is le van tiltva. 
    - **Engedélyezés (alapértelmezett beállítás)** : az Android Enterprise munkahelyi profilokat támogató összes eszköz androidos vállalati munkahelyi Profilos eszközökként van regisztrálva. Az androidos vállalati munkahelyi profilokat nem támogató androidos eszközök regisztrálása Android-eszköz rendszergazdai eszközeként történik, kivéve, ha az Android-eszközök rendszergazdai regisztrációja le van tiltva. 
> [!NOTE]
> Az alapértelmezett beállítás az új bérlők esetében a **2019-as** számú. Az összes korábbi bérlő nem fogja tudni módosítani a regisztrációs korlátozásokat, és látni fogja azokat a szabályzatokat, amelyeket a regisztrációs korlátozásokban beállítottak. Az olyan korábbi bérlők esetében, amelyekhez még nem történt meg a regisztrációs korlátozás, az androidos vállalati munkahelyi profilok esetében is az alapértelmezett érték lesz a **blokkolás** .

3. [A felhasználók tájékoztatása arról, hogy miképpen regisztrálhatják az eszközeiket](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Ha androidos vállalati munkahelyi profilokkal szeretné regisztrálni az eszközöket, de ezek az eszközök már regisztrálva lettek az Android-eszköz rendszergazdájával, akkor ezeket az eszközöket először törölni kell, majd újra kell regisztrálni őket.
> [!NOTE]
> Rendszergazdaként ezt távolról is elvégezheti **a** kivonási függvénnyel. Ez a függvény a műveletek menüben található, miután kiválasztotta az eszközt a **minden eszköz** panelen.

Ha az androidos vállalati munkahelyi profil eszközeit egy [eszköz-beléptetési kezelői](device-enrollment-manager-enroll.md) fiókkal regisztrálja, akkor a fiókhoz legfeljebb 10 eszköz regisztrálható.

További információ: [Az Intune által a Google-nek küldött adatok](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Következő lépések az androidos vállalati munkahelyi profilokhoz
- [Androidos vállalati munkahelyi profilbeli alkalmazások telepítése](../apps/apps-add-android-for-work.md)
- [Androidos vállalati munkahelyi profil konfigurációs házirendjeinek hozzáadása](../configuration/device-profiles.md)

## <a name="see-also"></a>További információ

[Androidos vállalati eszközök konfigurálása és hibaelhárítása Microsoft Intune](https://support.microsoft.com/help/4476974)
