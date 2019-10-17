---
title: Végpontvédelem hozzáadása macOS rendszeren az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: macOS rendszerű eszközökön használjon forgalomirányítót annak meghatározására, hogy honnan lehet alkalmazásokat telepíteni, beleértve a Mac App Store áruházat is. Engedélyezzen vagy konfiguráljon tűzfalat is egyes alkalmazások engedélyezésére, alkalmazások tiltására, rejtett üzemmód használatára vagy akár bizonyos bejövő kapcsolattípusok tiltására a Microsoft Intune használatával.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 358a396e762f1f20051abadfc2f3df80f37ca8c8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502295"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>MacOS Endpoint Protection-beállítások az Intune-ban  

Ez a cikk a macOS-t futtató eszközökhöz konfigurálható Endpoint Protection-beállításokat ismerteti. Ezeket a beállításokat macOS-eszköz konfigurációs profiljának használatával konfigurálhatja [az Intune](endpoint-protection-configure.md) -ban.  

## <a name="gatekeeper"></a>Forgalomirányító  

- **Ezen helyekről letöltött alkalmazások engedélyezése**  
  Korlátozza az eszköz által elindítható alkalmazásokat attól függően, hogy az alkalmazások Honnan tölthetők le. A cél az, hogy megvédje az eszközöket a kártevők ellen, és csak a megbízható forrásból származó alkalmazásokat engedélyezze.  

  - **Nincs konfigurálva**  
  - **Mac App Store**  
  - **Mac App Store és ismert fejlesztők**  
  - **Bárhonnan**  

  **Alapértelmezett**: nincs konfigurálva  

- **A felhasználó felülbírálhatja a forgalomirányítót**  
  Megakadályozza, hogy a felhasználók felülbírálják a forgalomirányító beállítását, és megakadályozza, hogy a felhasználók egy alkalmazás telepítésére rákattintanak. Ha engedélyezve van, akkor a felhasználók bármilyen alkalmazást telepíteni tudnak, ha a Ctrl billentyűt lenyomva rákattintanak.  
 
  - **Nincs konfigurálva** – a felhasználók vezérelhetik az alkalmazások telepítését.  
  - **Letiltás** – megakadályozza, hogy a felhasználók ne használják a vezérlőt – kattintson az alkalmazások telepítéséhez.  

  **Alapértelmezett**: nincs konfigurálva  

## <a name="firewall"></a>Tűzfal  

A tűzfalat inkább a kapcsolatok alkalmazásonkénti, nem pedig portonkénti korlátozására használja. Az alkalmazásonkénti beállítások használatával könnyebben kihasználhatók a tűzfal védelmének előnyei. Segít annak megelőzésében is, hogy nem kívánt alkalmazások átvegyék a megbízható alkalmazások számára nyitott portok irányítását.  

**Általános**
- **Tűzfal**  
  Engedélyezze a tűzfalat annak konfigurálásához, hogy a rendszer hogyan kezelje a bejövő kapcsolatokat a környezetben.  
  - **Nincs konfigurálva**  
  - **Engedélyezése**  

  **Alapértelmezett**: nincs konfigurálva  

- **Bejövő kapcsolatok**  
  Letiltja az összes bejövő kapcsolatot, kivéve az alapszintű internetes szolgáltatásokhoz szükséges kapcsolatokat, például a DHCP-t, a Bonjour-t és az IPSec-t. Ez a funkció a megosztási szolgáltatásokat, például a fájlmegosztást és a képernyőmegosztást is letiltja. Ha megosztási szolgáltatásokat használ, hagyja ezt a beállítást a *Nincs konfigurálva* értéken.  
  - **Nincs konfigurálva**  
  - **Tiltás**  

  **Alapértelmezett**: nincs konfigurálva  

**Adott alkalmazások bejövő kapcsolatainak engedélyezése vagy letiltása.**  

  - **Engedélyezett alkalmazások**  
    Válassza ki azokat az alkalmazásokat, amelyek számára kifejezetten engedélyezett a bejövő kapcsolatok fogadása.  

  - **Blokkolt alkalmazások**  
    Válassza ki azokat az alkalmazásokat, amelyeknek le kell tiltaniuk a bejövő kapcsolatokat.  

  - **Rejtett üzemmód**  
    Ha meg szeretné akadályozni, hogy a számítógép válaszoljon a Szondázási kérelmekre, engedélyezze a rejtett üzemmódot. Az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre. Az olyan váratlan kérelmeket, mint az ICMP (ping), a rendszer figyelmen kívül hagyja.  
    - **Nincs konfigurálva**  
    - **Engedélyezése**  

    **Alapértelmezett**: nincs konfigurálva  

## <a name="filevault"></a>FileVault  
Az Apple FileVault beállításaival kapcsolatos további információkért lásd: [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) az Apple fejlesztői tartalomban. 

> [!IMPORTANT]  
> A macOS 10,15-es verziótól kezdve a FileVault-konfigurációhoz a felhasználó által jóváhagyott MDM-regisztráció szükséges. 

- **FileVault**  
  A XTS-AES 128 és újabb rendszerű 10,13 eszközökön a FileVault használatával *engedélyezheti* a teljes lemezes titkosítást.  
  - **Nincs konfigurálva**  
  - **Engedélyezése**  

  **Alapértelmezett**: nincs konfigurálva  

  - **Helyreállítási kulcs típusa**  
    A rendszer létrehozza a *személyes kulcs* helyreállítási kulcsait az eszközökhöz. Adja meg a következő beállításokat a személyes kulcshoz.  

    - **Személyes helyreállítási kulcs helye** – egy rövid üzenetet adhat meg a felhasználónak, amely elmagyarázza, hogyan és hol kérheti le személyes helyreállítási kulcsát. Ezt a szöveget szúrja be a felhasználó által a bejelentkezési képernyőn megjelenő üzenetbe, amikor a rendszer kéri, hogy adja meg a személyes helyreállítási kulcsot, ha elfelejtik a jelszót.  
      
    - **Személyes helyreállítási kulcs elforgatása** – Itt adhatja meg, hogy az eszköz személyes helyreállítási kulcsa milyen gyakran legyen elforgatva. Kiválaszthatja a **nincs konfigurálva**beállítás alapértelmezett értékét, vagy **1** és **12** hónap közötti értéket is megadhat.  

  - **Figyelmeztetés letiltása a kijelentkezéskor**  
    Megakadályozza, hogy a rendszer felszólítsa a felhasználót, hogy engedélyezze a FileVault a kijelentkezéskor.  Ha a Letiltás értékre van állítva, a rendszer letiltja a kijelentkezéskor megjelenő kérést, és a felhasználó bejelentkezik.  
    - **Nincs konfigurálva**  
    - **Letiltás** – tiltsa le a kijelentkezéskor megjelenő üzenetet.

    **Alapértelmezett**: nincs konfigurálva  

  - **Megkerülő időpontok száma**  
  Állítsa be, hogy a felhasználó hányszor hagyhatja figyelmen kívül a kéréseket, hogy engedélyezze a FileVault, mielőtt FileVault a felhasználónak a bejelentkezéshez. 

    - **Nincs konfigurálva** – az eszközön a következő bejelentkezés engedélyezése előtt titkosítás szükséges.  
    - **1** – **10** – lehetővé teszi, hogy a felhasználó 1 – 10 alkalommal figyelmen kívül hagyja a kérést, mielőtt titkosítást kellene megadnia az eszközön.  
    - **Nincs korlát, mindig Rákérdezés** – a rendszer felszólítja a felhasználót, hogy engedélyezze a FileVault, de a titkosítás soha nem szükséges.  
 
    **Alapértelmezett**: *változó* – ha a *Letiltás letiltása* a kijelentkezéskor beállítás nincs **konfigurálva**értékre van állítva, akkor ez a beállítás alapértelmezés szerint **nincs konfigurálva**. Ha a *kijelentkezéskor a Letiltás* lehetőség van letiltva értékre van **állítva, akkor**a beállítás alapértelmezett értéke **1** , a **nem konfigurált** érték pedig nem.

Az Intune-nal történő FileVault kapcsolatos további információkért lásd: [FileVault helyreállítási kulcsok](encryption-monitor.md#filevault-recovery-keys).

