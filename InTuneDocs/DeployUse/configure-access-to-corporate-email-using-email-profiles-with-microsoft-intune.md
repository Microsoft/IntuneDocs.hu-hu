---
title: "Vállalati levelezéshez való hozzáférés konfigurálása e-mail-profilokkal | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8a3df01e9c02af7c43cdadc6d202bc6d74a000da
ms.openlocfilehash: d0fa235b7b25fe71a4e3b4b0bf68cd2db31b1f18


---

# Vállalati levelezéshez való hozzáférés konfigurálása e-mail profilokkal a Microsoft Intune-ban
Sok mobilplatform *natív* e-mail-ügyfélprogramot tartalmaz, amely az operációs rendszer részét képezi.  Ezek közül egyes ügyfélprogramok e-mail-profilok használatával konfigurálhatók, az ebben a témakörben ismertetett módon.

Ha még erősebb adatveszteség-megelőzési intézkedéseket szeretne foganatosítani, válassza a [feltételes hozzáférést](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), amely a felhasználó postaládájához szabályozza a hozzáférést, bármilyen levelezőprogramot is használjon (beleértve a natív levelezőprogramokat).

Az e-mail-profil beállításainak segítségével konfigurálhatók az e-mail-hozzáférési beállítások a mobileszközökön futó konkrét e-mail-ügyfélprogramok számára.   A legtöbb mobilplatform *natív* e-mail-ügyfélprogramot tartalmaz, amely az operációs rendszer részét képezi.  A támogatott platformokon a natív e-mail-ügyfélprogramok úgy konfigurálhatók a Microsoft Intune segítségével, hogy a felhasználók saját eszközeiken telepítés nélkül hozzáférhessenek a vállalati e-mailjeikhez.  

A rendszergazdák vagy a felhasználók alternatív e-mail-ügyfélprogramokat is telepíthetnek, például a Microsoft Outlook alkalmazás Android vagy iOS rendszerhez készült változatát.  Előfordulhat, hogy ezek az e-mail-ügyfélprogramok nem támogatják az e-mail-profilokat, és nem konfigurálhatók a Microsoft Intune e-mail-profilok használatával.  

A következő eszköztípusokon konfigurálható a natív e-mail-ügyfélprogram e-mail-profilok segítségével:
-   Windows Phone 8 és újabb verziók
-   Windows 10 asztali verzió, Windows 10 Mobile és újabb verziók
-   iOS 7.1-es és újabb verziók
-   Samsung KNOX Standard (4.0-s és újabb verzió)


Azon kívül, hogy beállít egy e-mail-fiókot, a szinkronizálási beállításokat is megadhatja az eszközön, mint például a szinkronizálni kívánt e-mailek mennyiségét, és eszköztípustól függően a szinkronizálni kívánt tartalmakat is.

## Az e-mail-profilok biztonságossá tétele
Az e-mail-profilok az alábbi két módszer egyikével tehetők biztonságossá:

### Tanúsítványok
Az e-mail-profil létrehozásakor válassza ki a korábban az Intune-ban már létrehozott tanúsítványprofilt. Ez identitástanúsítványként is ismert. Ezt hitelesíti a rendszer egy megbízható tanúsítványprofilhoz (vagy főtanúsítványhoz) képest, hogy ellenőrizze a felhasználó eszközének a csatlakozásra való jogosultságát. A megbízható tanúsítvány az e-mail-kapcsolatot hitelesítő számítógépre van telepítve. Ez általában a natív levelezési kiszolgáló.

További információt a tanúsítványprofilok Intune-ban történő létrehozásáról és használatáról [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md) című témakörben találhat.

### Felhasználónév és jelszó
A felhasználó a natív levelezési kiszolgálón felhasználónév és jelszó megadásával hitelesíti magát.

A jelszó nem szerepel az e-mail profilban, így a felhasználónak ezt minden alkalommal meg kell adnia, amikor az e-mail szolgáltatáshoz csatlakozik.

### E-mail profil létrehozása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfigurálja a következő házirendtípusok egyikét:

    -   **A Samsung KNOX szabvány (4.0 és újabb) e-mail profilja**

    -   **E-mail profil (iOS 7.1 és újabb)**

    -   **E-mail profil (Windows Phone 8 és újabb)**

    -   **E-mail profil (Windows 10 és újabb asztali és mobil rendszerek)**

    Csak egyéni e-mail profilházirendet hozhat létre és telepíthet. Ajánlott beállítások nem állnak rendelkezésre.

3.  A következő táblázat segítségével konfigurálja az e-mail-profil beállításait:
    |Beállítás neve|További információ|
    |----------------|-----------------------------------------------------------------------------|
    |**Név**|Az e-mail-profil egyedi neve.|
    |**Leírás**|A profil azonosítását megkönnyítő leírás.|
    |**Gazdagép**|Annak a vállalati kiszolgálónak az állomásneve, amelyen a natív e-mail-szolgáltatást fut.|
    |**Fióknév**|Az e-mail-fiók megjelenítendő neve. Ez fog megjelenni a felhasználók eszközein.|
    |**Felhasználónév**|Az e-mail-fiókhoz tartozó felhasználónév megszerzésének módja: Helyszíni Exchange-kiszolgáló esetén válassza a **Felhasználónév**, Office 365 esetén pedig az **Egyszerű felhasználónév** lehetőséget.|
    |**E-mail cím**|A felhasználóhoz tartozó e-mail-cím előállításának módja az egyes eszközökön. Ha az elsődleges SMTP-cím használatával kíván bejelentkezni az Exchange-be, válassza az **Elsődleges SMTP-cím** lehetőséget; ha e-mail-címként a teljes egyszerű felhasználónevet kívánja használni, válassza az **Egyszerű felhasználónév** lehetőséget.|
    |**Hitelesítési módszer** (Samsung KNOX és iOS)|Az e-mail-profil által használandó hitelesítési módszernek válassza a **Felhasználónév és jelszó** vagy a **Tanúsítványok** lehetőséget.|
    |**Válasszon ki egy, az ügyfél-hitelesítéshez használandó ügyféltanúsítványt (identitástanúsítványt)** (Samsung KNOX és iOS)|Válassza ki az ügyfél korábban létrehozott SCEP tanúsítványát, amelyet az Exchange-kapcsolat hitelesítésére kíván használni. További információt a tanúsítványprofilok Intune-ban történő használatáról [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md) című témakörben találhat.<br /><br />Ez a beállítás csak akkor látható, ha a hitelesítési módszer a **Tanúsítványok**.|
    |**S/MIME használata** (Samsung KNOX és iOS)|Kimenő e-mailek küldése S/MIME titkosítással.|
    |**Aláíró tanúsítvány** (Samsung KNOX és iOS)|Válassza ki a kimenő e-mailek aláírására használt aláíró tanúsítványt.<br /><br />Ez a lehetőség csak akkor jelenik meg, ha az **S/MIME használata** lehetőséget választotta.|
    |**E-mailek szinkronizálása ennyi napra visszamenőleg**|Ennyi napra visszamenőleg kívánja szinkronizálni az e-maileket; az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.|
    |**Szinkronizálás ütemezése** (Samsung KNOX, Windows Phone 8 és újabb verziók, Windows 10)|Válassza ki, hogy az eszközök milyen ütemezés szerint szinkronizálják az adatokat az Exchange Server kiszolgálóról. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.|
    |**SSL használata**|Biztonságos szoftvercsatornás (SSL) kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange Server kiszolgálóval való kommunikációhoz. <br /><br />A Samsung KNOX 4.0-s vagy újabb verzióját futtató eszközök számára exportálja az Exchange Server SSL-tanúsítványát, és telepítse az Intune-ban androidos megbízható tanúsítványprofilként. Az Intune nem támogatja a hozzáférést ehhez a tanúsítványhoz, ha ez más módon telepítve van az Exchange Serverre.|
    |**Szinkronizálni kívánt tartalom típusa**|Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat.| 
    |**Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** (csak iOS esetén)|A felhasználók kiválaszthatják ezt a profilt alapértelmezett e-mail-küldési fiókként, és engedélyezett a külső alkalmazások számára az e-mailek natív e-mail alkalmazásban történő megnyitása, például fájlok e-mailhez való csatolásához.|

    > [!IMPORTANT]
    > Ha már telepített egy e-mail-profilt, de szeretné megváltoztatni az **állomás** vagy az **E-mail cím** beállítás értékét, akkor törölje a meglévő e-mail-profilt, majd hozzon létre egy újat a kívánt értékekkel.

4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## A szabályzat telepítése

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése**lehetőségre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A szabályzat telepítése** – Válasszon ki egy vagy több olyan csoportot, amelynek telepíteni kívánja a szabályzatot, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.

A **Házirend** munkaterület **Áttekintés** lapján található állapotösszegzés és riasztások segítségével azonosíthatók a szabályzattal kapcsolatos, figyelmet igénylő problémák. Ezen felül egy állapotösszegzés megjelenik az Irányítópult munkaterületen is.

> [!NOTE]
> Ha egy eszközről ki szeretne törölni egy e-mail profilt, módosítsa a telepítését, és távolítson el minden olyan csoportot, amelyeknek tagja az eszköz.





<!--HONumber=Jun16_HO4-->


