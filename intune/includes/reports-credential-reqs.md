<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Az Azure AD-beli és az Intune-beli hitelesítő adatokra vonatkozó követelmények

A hitelesítés és az engedélyezés az Azure AD-beli hitelesítő adatokon és az Intune szerepköralapú hozzáférés-vezérlésén (RBAC) alapul. Alapértelmezés szerint a bérlő valamennyi globális rendszergazdája és Intune-beli szolgáltatás-rendszergazdája hozzáféréssel rendelkezik az adattárházhoz. Az Intune-szerepkörök használatával azáltal biztosíthat több felhasználónak is hozzáférést, hogy hozzáférést ad nekik az **Intune-adattárház** erőforráshoz.

Az Intune-adattárházhoz való hozzáférésre (beleértve az API-t is) vonatkozó követelmények a következők:

  -  A felhasználónak a következők egyikének kell lennie:
      -  Azure AD-beli globális rendszergazda
      -  Intune-beli szolgáltatás-rendszergazda
      -  Felhasználó szerepköralapú hozzáféréssel az **Intune-adattárház** erőforráshoz
      -  Felhasználó nélküli hitelesítés [csak alkalmazásalapú hitelesítés](../data-warehouse-app-only-auth.md) 
