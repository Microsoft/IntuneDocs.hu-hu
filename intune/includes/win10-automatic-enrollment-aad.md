---
ms.openlocfilehash: 748141dc494e28f25a09039a7a500411af76ace7
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2020
ms.locfileid: "76037610"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10-es eszközök automatikus regisztrációjának engedélyezése

Az automatikus regisztrálással a felhasználók Windows 10-es eszközeiket regisztrálhatják az Intune-ban. A regisztráláshoz a felhasználónak a személyes tulajdonú eszközén hozzá kell adnia a munkahelyi fiókját, vagy a céges tulajdonban lévő eszközt csatlakoztatnia kell az Azure Active Directoryhoz. A háttérben az eszköz regisztrálja magát, és csatlakozik az Azure Active Directoryhoz. A regisztrációt követően az eszközt az Intune felügyeli.

**Előfeltételek**

- Azure Active Directory Premium-előfizetés ([próba-előfizetés](https://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-előfizetés

### <a name="configure-automatic-mdm-enrollment"></a>Az automatikus MDM-regisztráció konfigurálása

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com), majd válassza az **Azure Active Directory** elemet.

   ![Az Azure Portal képernyőképe](../enrollment/media/windows-enroll/auto-enroll-azure-main.png)

2. Válassza a **Mobilitás (MDM és MAM)** elemet.

   ![Az Azure Portal képernyőképe](../enrollment/media/windows-enroll/auto-enroll-mdm.png)

3. Válassza a **Microsoft Intune** elemet.

   ![Az Azure Portal képernyőképe](../enrollment/media/windows-enroll/auto-enroll-intune.png)

4. Konfigurálja az **MDM-felhasználói hatókört**. Adja meg, hogy mely felhasználók eszközeit felügyelje a Microsoft Intune. Ezeket a Windows 10 rendszerű eszközöket a rendszer automatikusan regisztrálni tudja a Microsoft Intune-felügyeletbe.

   - **Nincs** – Automatikus MDM-regisztráció letiltva
   - **Néhány** – Kiválaszthatja a **csoportokat**, melyek automatikusan regisztrálhatják Windows 10-es eszközeiket
   - **Mind** – Minden felhasználó automatikusan regisztrálhatja Windows 10-es eszközeit

      > [!IMPORTANT]
      > A BYOD-eszközök esetében a MAM felhasználói hatókör elsőbbséget élvez, ha a MAM felhasználói hatóköre és a MDM felhasználói hatóköre (az automatikus MDM-regisztráció) minden felhasználó számára engedélyezve van (vagy ugyanazokat a felhasználói csoportokat). Az eszköz a Windows Information Protection (folyamatban lévő) házirendeket fogja használni (ha konfigurálta őket) ahelyett, hogy MDM a regisztrálást.
      >
      > A vállalati eszközök esetében a MDM felhasználói hatóköre elsőbbséget élvez, ha mindkét hatókör engedélyezve van. Az eszközök bekerülnek a MDM.

   > [!NOTE]
   > A MDM felhasználói hatókörét olyan Azure AD-csoportra kell beállítani, amely felhasználói objektumokat tartalmaz.

   ![Az Azure Portal képernyőképe](../enrollment/media/windows-enroll/auto-enroll-scope.png)

5. A következő URL-címekhez használja az alapértelmezett értékeket:
    - **MDM használati feltételeinek URL-címe**
    - **MDM-felderítési URL-cím**
    - **MDM megfelelőségi URL-címe**

6. Válassza a **Mentés** lehetőséget.

Alapértelmezés szerint a kétfaktoros hitelesítés nincs engedélyezve a szolgáltatáshoz. Ezzel együtt azonban az eszköz regisztrálásához ajánlatos kétfaktoros hitelesítést használni. A kétfaktoros hitelesítés engedélyezéséhez konfigurálnia kell egy kétfaktoros hitelesítési szolgáltatót az Azure AD-ban, a felhasználói fiókokat pedig többtényezős hitelesítéshez kell konfigurálnia. További információt az [Azure Multi-Factor Authentication-kiszolgáló – első lépések](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud) című témakörben talál.
