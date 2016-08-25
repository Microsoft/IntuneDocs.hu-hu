---
title: "A Microsoft Passport beállításainak szabályozása az eszközökön | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: bdf7dfda3814ad6c6c00f5c133027175a95fb5e2


---

# A Microsoft Passport beállításainak szabályozása az eszközökön a Microsoft Intune-nal
A Microsoft Intune lehetővé teszi az integrációt a **Microsoft Passport for Work** nevű alternatív bejelentkezési módszerrel, amely Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.

A Passport lehetővé teszi jelszó helyett **felhasználói kézmozdulatok** használatát a bejelentkezéshez. A felhasználói hitelesítési mód lehet egy egyszerű PIN-kód, biometrikus hitelesítés, mint például a Windows Hello, vagy egy külső eszköz, például egy ujjlenyomat-olvasó.

Az Intune két módon integrálható a Passport for Workkel:

-   Intune-szabályzatokkal szabályozható, hogy a felhasználók mely hitelesítési módokkal jelentkezhetnek be, és melyekkel nem

-   A hitelesítési tanúsítványokat tárolhatja a Passport for Work kulcstároló-szolgáltatójában. További információkért lásd: [Az erőforrások biztonságos elérése a Microsoft Intune tanúsítványprofiljai segítségével](secure-resource-access-with-certificate-profiles.md).

## Passport for Work-házirend létrehozása

1.  A Passport for Work alábbi oldalának megnyitásához a [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Felügyelet** &gt; **Mobileszköz-kezelés** &gt; **Windows** &gt; **Passport for Work** lehetőségre.

    ![Passport for Work oldal](../media/passport.png)

2.  Válasszon egyet az alábbi beállítások közül:
    - **A Passport for Work letiltása a regisztrált eszközökön** – Válassza ezt a beállítást, ha Windows 10 eszközökön nem kívánja használni a Passport for Work lehetőséget. A képernyőn az összes többi beállítás le van tiltva.
    - **A Passport for Work engedélyezése a regisztrált eszközökön** – Válassza ezt a beállítást, ha a Passport for Work beállításait minden Windows 10 eszközön konfigurálni kívánja.
    - **Nincs konfigurálva** – Válassza ezt a beállítást, ha nem kívánja az Intune-nal vezérelni a Passport beállításait. A Windows 10 eszközökön meglévő Passport for Work-beállítások nem módosulnak. A képernyőn az összes többi beállítás le van tiltva.
3.  Ha **A Passport for Work engedélyezése a regisztrált eszközökön** lehetőséget választotta, akkor konfigurálja a szükséges beállításokat. A rendszer az összes regisztrált Windows 10 és Windows 10 Mobile eszközre alkalmazni fogja őket.
3.  Amikor végzett, kattintson a **Mentés** gombra.

## Passport for Work oldal: PIN-beállítások

  
- **PIN-kód minimális hosszának megkövetelése**/**PIN-kód maximális hosszának megkövetelése** – eszközök beállítása a megadott minimális és maximális hosszúságú PIN-kód használatára, a biztonságos bejelentkezés érdekében. A PIN-kód alapértelmezett hossza 6 karakter, de előírható, hogy legalább 4 karakterből kell állnia. A PIN-kód legfeljebb 127 karakter hosszú lehet.
- **Kisbetűk használatának megkövetelése a PIN-kódban**/**Nagybetűk használatának megkövetelése a PIN-kódban**/**Speciális karakterek megkövetelése a PIN-kódban** – Erősebb PIN-kód is használata is előírható, kis- és nagybetűk, illetve speciális karakterek PIN-kódon belüli használatának megkövetelésével. A következő lehetőségek közül választhat:
    - **Engedélyezett** – A felhasználók használhatják a karaktertípust a PIN-kódjukban, de ez nem kötelező.
    - **Kötelező** – A felhasználóknak a karaktertípusból legalább egyet használniuk kell a PIN-kódjukban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.
    - **Nem engedélyezett** (alapértelmezett) – A felhasználók ezeket a karaktertípusokat nem használhatják a PIN-kódjukban (ez történik akkor is, ha a beállítás nincs konfigurálva).
    > [!TIP]
    > [!TIP] A speciális karakterek a következők: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **PIN-kód lejárata (nap)** – A PIN-kódhoz célszerű lejárati időt megadni, amelynek eltelte után a végfelhasználóknak módosítaniuk kell a PIN-kódot. Az alapértelmezett érték 41 nap. 
- **PIN-előzmények megjegyzése** – Ezzel a beállítással korlátozható a korábban használt PIN-kódok ismételt használata. Alapértelmezés szerint az 5 legutóbb használt PIN-kód nem használható újra.


## Passport for Work: Egyéb beállítások

- **Platformmegbízhatósági modul (TPM) használata** – Platformmegbízhatósági modul (TPM) lapka használata további adatbiztonsági réteget biztosít.<br>Válasszon egyet az alábbi lehetőségek közül:
    - **Kötelező** (alapértelmezett) – a Passport for Work csak az elérhető TPM modullal rendelkező eszközökön építhető ki.
    - **Elsődleges** – az eszközök először a TPM használatára tesznek kísérletet. Ha az nem érhető el, használhatnak szoftveralapú titkosítást.
- **Biometrikus hitelesítés engedélyezése** – A PIN-kód helyett biometrikus hitelesítés, például arcfelismerés vagy ujjlenyomat használatának engedélyezése a Passport for Work szolgáltatásban. A felhasználóknak ekkor is be kell állítaniuk egy PIN-kódot arra az esetre, ha a biometrikus hitelesítés nem sikerül. A következő lehetőségek közül választhat:
    - **Igen** – A Passport for Work engedélyezi a biometrikus hitelesítést.
    - **Nem** – A Passport for Work meggátolja a biometrikus hitelesítést (minden fióktípus esetében).
- **Kibővített hamisításszűrés használata, ha elérhető** – konfigurálható, hogy a Windows Hello hamisításszűrési funkcióit használják-e az azt támogató eszközök (például egy valós arc helyett egy arcról készült fénykép észlelése).<br>Ha **Igen** értékre van állítva, a Windows minden felhasználótól megköveteli a kibővített hamisításszűrés alkalmazását arcfelismerés esetén, ha az támogatott.
- **Remote Passport használata** – Ha a beállítás az **Igen** értékre van beállítva, a felhasználók egy Remote Passport-eszközt használhatnak hordozható társeszközként az asztali hitelesítéshez. Az asztali gépnek csatlakoztatva kell lennie az Azure Active Directoryhoz, és a társeszköznek rendelkeznie kell a Passport for Work PIN-kódjával.

## További információ
A Microsoft Passporttal kapcsolatos további információkért olvassa el a Windows 10 dokumentációjában található [útmutatót](https://technet.microsoft.com/library/mt589441.aspx).





<!--HONumber=Jun16_HO4-->


