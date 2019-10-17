---
title: Vállalati Windows Hello-beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az Identity Protection-profilban található összes PIN-kód, biometrikus és hamisítás elleni beállítás listáját, és konfigurálja a Windows Hello for Business szolgáltatást a Windows 10-es eszközökön Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: f49ea9e1e59fadcb90a773e362ec3ef41e25ab63
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502224"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Windows 10 eszközbeállítások a vállalati Windows Hello engedélyezéséhez az Intune-ban

Ez a cikk felsorolja és ismerteti a Windows Hello for Business beállításait, amelyekkel szabályozható a Windows 10-es eszközök használata az Intune-ban. Intune-rendszergazdaként konfigurálhatja és hozzárendelheti ezeket a beállításokat a Windows 10-es eszközökhöz a mobileszköz-felügyeleti (MDM) megoldás részeként. 

Ezekről a beállításokról további információt a Windows Hello [for Business-házirend beállításainak konfigurálása](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)című témakörben talál a Windows Hello dokumentációjában.


Ha többet szeretne megtudni a vállalati Windows Hello-profilokról az Intune-ban, tekintse meg az [Identity Protection konfigurálása](identity-protection-configure.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy konfigurációs profilt](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello
- **A vállalati Windows Hello konfigurálása**:
  - **Nincs konfigurálva** – válassza ezt a beállítást, ha nem szeretné használni az Intune-t a vállalati Windows Hello beállításainak szabályozására. A Windows 10-eszközökön meglévő Vállalati Windows Hello-beállítások nem módosulnak. A panelen a többi beállítás nem elérhető.

  - **Letiltva** – ha nem szeretné a vállalati Windows Hello-t használni, válassza ezt a beállítást. Ezt követően a képernyőn a többi beállítás nem lesz elérhető.
  - **Engedélyezve** – ezt a beállítást akkor válassza, ha a vállalati Windows Hello beállításait szeretné konfigurálni.  
  
  **Alapértelmezett**: nincs konfigurálva

  Ha az Engedélyezve értékre *van*állítva, a következő beállítások érhetők el:

  - **PIN-kód minimális hossza**  
    Az eszközökhöz tartozó PIN-kód minimális hosszának megadása a bejelentkezés biztonságossá tételéhez. A Windows-eszköz alapértelmezett értéke hat karakter, de ez a beállítás legalább négy 127 karaktert kényszerítheti ki. 

    **Alapértelmezett**: *nincs konfigurálva*

  - **PIN-kód maximális hossza**  
  A bejelentkezés biztonságossá tételéhez a PIN-kód maximális hosszát határozza meg az eszközök számára. A Windows-eszköz alapértelmezett értéke hat karakter, de ez a beállítás legalább négy 127 karaktert kényszerítheti ki.  

    **Alapértelmezett**: *nincs konfigurálva*  

  - **Kisbetűk a PIN-kódban**  
    Erősebb PIN-kód kikényszeríthető úgy, hogy a végfelhasználók a kisbetűket is megkövetelik. A választható lehetőségek:

    - **Nem engedélyezett** – a felhasználók nem használhatnak kisbetűket a PIN-kódban. Ez a viselkedés akkor is előfordulhat, ha a beállítás nincs konfigurálva.
    - **Engedélyezett** – lehetővé teszi, hogy a felhasználók kisbetűs karaktereket használjanak a PIN-kódban, de ez nem kötelező.
    - **Kötelező** – a felhasználóknak legalább egy kisbetűt tartalmazniuk kell a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

  - **Nagybetűk a PIN-kódban**  
    Erősebb PIN-kód kikényszeríthető úgy, hogy a végfelhasználók nagybetűvel rendelkeznek. A választható lehetőségek:

    - **Nem engedélyezett** – a felhasználók nem használhatnak nagybetűket a PIN-kódban. Ez a viselkedés akkor is előfordulhat, ha a beállítás nincs konfigurálva.
    - **Engedélyezett** – lehetővé teszi, hogy a felhasználók nagybetűket használjanak a PIN-kódban, de ez nem kötelező.
    - **Kötelező** – a felhasználóknak legalább egy nagybetűt tartalmazniuk kell a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

  - **Speciális karakterek a PIN-kódban**  
    Erősebb PIN-kód kikényszeríthető úgy, hogy a végfelhasználók speciális karaktereket is megkövetelnek. A speciális karakterek a következők: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  

    A választható lehetőségek:
    - **Nem engedélyezett** – a felhasználók nem használhatnak speciális karaktereket a PIN-kódban. Ez a viselkedés akkor is előfordulhat, ha a beállítás nincs konfigurálva.
    - **Engedélyezett** – lehetővé teszi, hogy a felhasználók nagybetűket használjanak a PIN-kódban, de ez nem kötelező.
    - **Kötelező** – a felhasználóknak legalább egy nagybetűt tartalmazniuk kell a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

    **Alapértelmezett**: nem engedélyezett

  - **PIN-kód lejárata (nap)**  
    A PIN-kódhoz célszerű lejárati időt megadni, amelynek eltelte után a felhasználóknak módosítaniuk kell a PIN-kódot. A Windows-eszközök alapértelmezett értékei 41 nap.

    **Alapértelmezett**: nincs konfigurálva

  - **PIN-előzmények megjegyzése**  
    Korlátozza a korábban használt PIN-kódok ismételt használatát. A Windows-eszközök alapértelmezett értéke az utolsó öt PIN-kód újbóli használatának megakadályozása.  

    **Alapértelmezett**: nincs konfigurálva  

  - **PIN-kód helyreállításának engedélyezése**@no__t – 1  
    Lehetővé teszi a felhasználó számára a vállalati Windows Hello PIN-kód helyreállítási szolgáltatás használatát. 
    
    - **Engedélyezve** – a PIN-kód helyreállítási titkát a rendszer az eszközön tárolja, és szükség esetén a felhasználó módosíthatja a PIN-kódját.  
    - **Letiltva** – a helyreállítási titok nem jön létre vagy nem tárolódik.

    **Alapértelmezett**: nincs konfigurálva

  - **Platformmegbízhatósági modul (TPM)**   használata  
    A TPM lapka használata további adatbiztonsági réteget biztosít.  

    - Csak az elérhető TPM modullal rendelkező eszközök telepíthetik a vállalati Windows Hello **szolgáltatást** .
    - **Nincs konfigurálva** – az eszközök először a TPM használatára tesznek kísérletet. Ha az nem érhető el, használhatnak szoftveralapú titkosítást.
    
    **Alapértelmezett**: nincs konfigurálva

  - **Biometrikus hitelesítés engedélyezése**  
     Lehetővé teszi a biometrikus hitelesítést, például az arcfelismerést vagy az ujjlenyomat használatát a PIN-kód alternatívájaként a Vállalati Windows Hello szolgáltatásban. A felhasználóknak ekkor is be kell állítaniuk egy PIN-kódot arra az esetre, ha a biometrikus hitelesítés nem sikerül. A következő lehetőségek közül választhat:

    - **Engedélyezés** – a vállalati Windows Hello lehetővé teszi a biometrikus hitelesítést.
    - **Nincs konfigurálva** – a Windows Hello for Business megakadályozza a biometrikus hitelesítést (minden fióktípus esetében).

    **Alapértelmezett**: nincs konfigurálva

  - **Fokozott hamisítás elleni javítás használata, ha elérhető**  
    Konfigurálható, hogy a Windows Hello hamisításszűrési funkcióit használják-e az azt támogató eszközök (például egy valós arc helyett egy arcról készült fénykép észlelése).  
    - **Engedélyezés** – a Windows megköveteli, hogy a rendszer minden felhasználó számára az arc-funkciók elleni hamisítást használja a támogatott esetekben.
    - **Nincs konfigurálva** – a Windows tiszteletben tartja a hamisítási konfigurációkat az eszközön.

    **Alapértelmezett**: nincs konfigurálva

  - **Tanúsítvány helyszíni erőforrásokhoz**  

    - **Engedélyezés** – lehetővé teszi, hogy a vállalati Windows Hello tanúsítványokat használjon a helyszíni erőforrásokhoz való hitelesítéshez.
    - **Nincs konfigurálva** – megakadályozza, hogy a vállalati Windows Hello tanúsítványokat használjon a helyszíni erőforrásokhoz való hitelesítéshez. Az eszközök Ehelyett a *kulcs-megbízhatósági kapcsolat helyi hitelesítésének*alapértelmezett viselkedését használják. További információ: [felhasználói tanúsítvány helyszíni hitelesítéshez](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) a Windows Hello dokumentációjában.  

  **Alapértelmezett**: nincs konfigurálva

- **Bejelentkezéshez használható biztonsági kulcsok használata**  
  Ez a beállítás a Windows 10 1903-es vagy újabb verzióját futtató eszközökön érhető el. A használatával felügyelheti a Windows Hello biztonsági kulcsainak használatát a bejelentkezéshez.  

  - **Engedélyezve** – a felhasználók a Windows Hello biztonsági kulcsot bejelentkezési hitelesítő adatként használhatják a szabályzattal megcélzó számítógépeken. 
  - **Letiltva** – a biztonsági kulcsok le vannak tiltva, és a felhasználók nem használhatják őket a számítógépekbe való bejelentkezéshez.   

  **Alapértelmezett**: nincs konfigurálva

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../configuration/device-profile-assign.md), és [kövesse nyomon az állapotát](../configuration/device-profile-monitor.md).
