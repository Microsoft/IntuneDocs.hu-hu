---
title: "Windowsos eszközök védelme többtényezős hitelesítéssel | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2023d7bc1d35b423a216ece195cdca9a6a542446
ms.openlocfilehash: 15e546b93c2a3aff551efa36ac80ff212ada5812


---

# Protect Windows devices with multi-factor authentication
A Microsoft Intune többtényezős hitelesítés (MFA) alkalmazásával segíti elő a vállalati erőforrások védelmét. Az MFA hitelesítés a felhasználónevek és jelszavak mellett olyan hitelesítési tényezőket is igényel, mint például a szöveges hitelesítés. Az Intune a többtényezős hitelesítés használatát a Windows 8.1 vagy későbbi verziójú, a Windows Phone 8.1, illetve a Windows 10 rendszerű asztali és mobileszközök regisztrálása során támogatja. 

## Az ADFS Multi-Factor Authentication helyszíni infrastruktúra-követelményei
A többtényezős hitelesítés beállításához az alábbiakra van szükség:

-   **Egy Active Directory-tartomány, amelyhez az ADFS-kiszolgáló csatlakozik.**

-   **A Multi-Factor Authentication szolgáltatáshoz beállított ADFS-kiszolgáló.** ADFS-kiszolgálóként beállított, Windows Server 2012 R2 rendszerű kiszolgáló. További információkért lásd: [Secure cloud and on-premises resources using Azure Multi-Factor Authentication Server with Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/) (A felhőalapú és helyszíni erőforrások védelme a Windows Server 2012 R2 Active Directory összevonási szolgáltatásokkal használt Azure Multi-Factor Authentication alkalmazásával)

A fent felsorolt kiszolgálók mindegyikének meg kell felelnie a [Rendszerkövetelmények és telepítési információk a Windows Server 2012 R2-höz](http://technet.microsoft.com/library/dn303418.aspx)című témakörben megadott rendszerkövetelményeknek.

#### Többtényezős hitelesítés az Intune-ban
Ha vállalata helyszíni informatikai infrastruktúrát használ, amelynek az Active Directory-tartományában be van állítva az Active Directory összevonási szolgáltatások (ADFS), beállíthatja a Multi-Factor Authentication szolgáltatást az összevonási kiszolgálón, majd engedélyezheti azt az Intune-ban történő regisztráláshoz. Az MFA szolgáltatásnak az Intune-beli konfigurálásával engedélyezi, hogy a felhasználók egyszer, a regisztráció során hitelesítsék magukat, majd ezt követően úgy férhessenek hozzá a vállalati erőforrásokhoz, hogy az MFA hitelesítési folyamatot nem kell minden alkalommal megismételniük.

>[!NOTE]
>Az MFA hitelesítés felhasználói vagy csoportszinten követelhető meg az ADFS-kiszolgálón.  

#### Többtényezős hitelesítés az Intune nélkül
Ha beállítja az MFA használatát az összevonási kiszolgálón, de nem engedélyezi az MFA használatát az Intune-beléptetéshez, a felhasználóknak minden olyan alkalommal használniuk kell a többtényezős hitelesítést, amikor vállalati erőforrásokhoz férnek hozzá (nem csak a regisztrációnál).

Az Azure Active Directory MFA használható arra is, hogy a többtényezős hitelesítés minden alkalommal, felhasználónkénti alapon kötelező legyen, amikor a felhasználók vállalati erőforrásokhoz férnek hozzá. Az Azure Active Directory Multi-Factor Authentication egy felhőalapú szolgáltatás, amelyhez nincs szükség helyszíni informatikai infrastruktúrára. Az Azure Active Directory MFA hitelesítés beállításáról a [Bevezetés a felhőalapú Azure Multi-Factor Authentication használatába](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/) című témakörben tájékozódhat.

## Többtényezős hitelesítés megkövetelése az Active Directory összevonási szolgáltatásokban windowsos eszközök regisztrálásakor
A Multi-Factor Authentication engedélyezéséről az ADFS-ben a [Kockázatkezelés további többtényezős hitelesítéssel érzékeny alkalmazások esetén](http://technet.microsoft.com/library/dn280949.aspx)című bemutatóban tájékozódhat.

## Többtényezős hitelesítésű eszközregisztráció beállítása az Intune-ban
>[!Important]  
>Mielőtt kötelezővé tenné a többtényezős hitelesítés használatát a windowsos eszközök Intune-beli regisztrálásához, engedélyezze ezt a hitelesítési módot az Azure AD-bérlőn vagy a helyszíni környezetben. Ellenkező esetben a felhasználók hibaüzenetet kapnak, amikor Windows rendszerű eszközüket próbálják regisztrálni, illetve amikor megpróbálják csatlakoztatni eszközüket az Azure Active Directoryhoz, amennyiben az Azure AD-hoz való csatlakozáskori automatikus regisztráció be van állítva.

1.  Az Intune felügyeleti konzolon kattintson a **Rendszergazda** &gt; **Mobileszköz-kezelés** &gt; **Többtényezős hitelesítés** elemre.

2.  Kattintson **A többtényezős hitelesítés konfigurálása**, majd a **Többtényezős hitelesítés engedélyezése** elemre.




<!--HONumber=Jun16_HO4-->


