---
title: "A Microsoft Intune próbaverziójának elindítása és az iOS PIN-kódokra vonatkozó szabályzatának alkalmazása | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7f3985b10ac9612c8c1efc4756eb25cdcf29b023
ms.openlocfilehash: 6787d0c35621b2bc94bfe376dfd1669e9dfe46db


---

# A Microsoft Intune próbaverziójának elindítása és az iOS PIN-kódokra vonatkozó szabályzatának alkalmazása
Ezek a részletes útmutatók segítenek az Intune próbaverziójának beállításában és PIN-házirend konfigurálásában az iOS-eszközökhöz. Az Intune értékelésével kapcsolatos további kipróbálható általános feladatok listáját a [Common Microsoft Intune evaluation tasks](common-microsoft-intune-evaluation-tasks.md) (A Microsoft Intune értékelésével kapcsolatos általános feladatok) című témakörben tekintheti meg.



## A feladat előfeltételeinek áttekintése

-   Windows rendszerű számítógép, amelyen Internet Explorer található – adminisztratív feladatokhoz

-   iOS 7.1-es vagy újabb verzió a felhasználói házirend érvényesítésének teszteléséhez

-   Telefon a hitelesítéséhez próbafeliratkozás során

## Ingyenes Intune-próbafiók létrehozása
> [!NOTE]
> Ha már rendelkezik Intune-előfizetéssel, hagyja ki ezt a szakaszt, és folytassa a következő szakasszal.

1.  Windows rendszerű számítógépen kattintson a jobb gombbal az **Internet Explorer** (IE) elemre, és válassza az **InPrivate-böngészés** lehetőséget.

    ![InPrivate-böngészés indítása](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  Lépjen az [Intune feliratkozási portálra](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1), adja meg a kért információkat, és kattintson a **Tovább** gombra.

    ![Fiók regisztrálása](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  Adjon meg egy felhasználói azonosítót és egy jelszót a rendszergazdai fiókhoz, és kattintson a **Tovább** gombra. Ezzel az azonosítóval fog bejelentkezni az Intune-portálra a rendszergazdai feladatok elvégzéséhez.

    ![Azonosító létrehozása](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  Adja meg a mobiltelefonszámát, és kattintson az **SMS-t kérek** gombra a szám érvényesítéséhez.

    ![Adatok ellenőrzése](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  Mentse el a képernyőn megjelenő információkat, majd kattintson a **Készen áll...** gombra.

    ![Készen áll](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## Tesztfelhasználó létrehozása

1.  Windows rendszerű számítógépen kattintson a **Start** gomba a felhasználófelügyeleti lapra lépéshez.

    ![Lépjen a felhasználókezelési oldalra.](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  Felhasználó hozzáadásához kattintson a **+** gombra.

    ![Felhasználó hozzáadása](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  Az **Új felhasználói fiók létrehozása** lapon:

    1.  Adja meg a tesztfelhasználó információit.

    2.  Válassza a **Jelszó beírása** lehetőséget.

    3.  Törölje az **Ennek a személynek a következő bejelentkezéskor módosítania kell a jelszavát** jelölőnégyzet bejelölését.

    4.  Kattintson a **Létrehozás** gombra.

    ![Új felhasználói fiók létrehozása](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  A felhasználó létrehozásának megerősítési oldalán kattintson a **Bezárás** gombra.

    ![A felhasználó létrehozásának megerősítési oldala](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  Kattintson a **Frissítés** gombra a létrehozott tesztfelhasználó megtekintéséhez.

    ![Eseménymegerősítés](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## iOS PIN-kódokra vonatkozó házirend konfigurálása a tesztfelhasználó számára

1.  Windows rendszerű számítógépen állítsa be az Intune-t mobileszköz-kezelő szolgáltatóként:

    1.  Lépjen az [Intune felügyeleti konzoljára](http://manage.microsoft.com/), jelentkezzen be a rendszergazdai fiókjával, és kattintson a **Mobileszközök kezelésének megkezdése** gombra. Megnyílik a mobileszköz-kezelő szolgáltató oldala.

        ![Az Intune-konzol használatának megkezdése](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  Kattintson a **Mobileszköz-kezelő szolgáltató megadása** hivatkozásra.

        ![Mobileszköz-felügyeleti szolgáltató megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  Engedélyezze az iOS-eszközök regisztrációját. Ez a folyamat megbízható tanúsítványt állít be az Apple Push Notification szolgáltatás (APNs) és az Intune-előfizetés között.

    1.  Kattintson **Az iOS és a Mac OS X platform engedélyezése** gombra.

        ![iOS- és Mac OS X-regisztráció engedélyezése](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  Kattintson **Az APNs-tanúsítványkérelem letöltése** gombra.

        ![Az APNs-tanúsítvány letöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  Adjon meg egy fájlnevet és egy helyet a tanúsítvány-aláírási kérelem számára, majd kattintson a **Mentés** parancsra. Ebben a fájlban található az Intune-előfizetés által őrzött titkos kulcsnak megfelelő nyilvános kulcs.

        ![Tanúsítvány-aláírási kérés megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  Kattintson az **Apple Push Certificates portálra** új lap megnyitásához.

        ![Lépjen az APNs-tanúsítványok oldalára.](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Adja meg az Apple ID-t és a jelszót, és kattintson a **Sign in** (Bejelentkezés) gombra. Ez az azonosító az iOS-eszközön alkalmazások az iOS App Store áruházból való beszerzéséhez használt azonosító lehet.

        ![Jelentkezzen be az Apple Push Certificates Portal webhelyre.](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  Kattintson a **Create a Certificate** (Tanúsítvány létrehozása) gombra.

        ![APNs-tanúsítvány létrehozása](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Olvassa el az Apple felhasználási feltételeit, jelölje be a jelölőnégyzetet, és kattintson az **Accept** (Elfogadás) gombra.

        ![A feltételek elfogadása](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  Kattintson a **Tallózás** gombra.

        ![Nyissa meg a mappát, ahová menteni szeretné a tanúsítványt.](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. Válassza ki a korábban mentett CSR-fájlt, és kattintson az **Open** (Megnyitás) gombra.

        ![A tanúsítvány megnyitása](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. Kattintson az **Upload** (Feltöltés) gombra.

        ![A tanúsítvány feltöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. Ha a rendszer rákérdez a JSON-fájl letöltésére, kattintson a **Save as** (Mentés másként) gombra.

        ![A JSON-fájl mentése](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. Adjon meg egy helyet a JSON-fájl számára, majd kattintson a **Save** (Mentés) parancsra.

        ![A JSON-fájl mentési helyének megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        Ha az oldala nem irányítja át automatikusan néhány másodpercen belül, kattintson a **Cancel** (Mégse) gombra.

        ![Vonja vissza a Mégse gombbal, ha az oldal nem irányítja át](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. Az újonnan létrehozott tanúsítványfájl lekéréséhez kattintson a **Download** (Letöltés) gombra.

        ![A tanúsítvány letöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. Ha a rendszer rákérdez a PEM-fájl letöltésére, kattintson a **Save as** (Mentés másként) gombra.

        ![A PEM-fájl letöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. Adjon meg egy helyet a PEM-fájl számára, majd kattintson a **Save** (Mentés) parancsra.

        ![A PEM-fájl mentése](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Térjen vissza az Intune felügyeleti konzoljára, és kattintson **Az APNs-tanúsítvány feltöltése** gombra.

        ![Az APNs-tanúsítvány feltöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Adja meg az Apple ID-t, és kattintson a **Tallózás** gombra.

        ![Az Apple ID megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. Válassza ki a nemrég mentett PEM-fájlt, és kattintson a **Megnyitás** gombra.

        ![A PEM-fájl megnyitása](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. A befejezéshez kattintson a **Feltöltés**.

        ![A PEM-fájl feltöltése](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        Az APNs-tanúsítvány most már konfigurálva van.

        ![Az APNs-tanúsítványkonfiguráció kész](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  Tesztfelhasználói csoport létrehozása a házirendek célzásához:

    1.  A bal oldali panelen kattintson a **Csoportok** elemre.

        ![A Csoportok menü megnyitása](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  A jobb szélen kattintson a **Csoport létrehozása** elemre.

        ![Csoport létrehozása](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  Adjon meg egy csoportnevet, válassza a **Minden felhasználó** elemet szülőcsoportként, és kattintson a **Tovább** gombra.

        ![A Minden felhasználó szülőcsoportnak való kiválasztása](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  A **Csoporttagság kezdése a következővel:** mezőben válassza **A szülőcsoport összes felhasználója** elemet, és kattintson a **Befejezés** gombra.

        ![Csoporttagság kezdése a szülőcsoporttal](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  Hozzon létre egy iOS PIN-kódokra vonatkozó házirendet és célozza meg azzal a tesztfelhasználói csoportot:

    1.  A bal oldali panelen kattintson a **Házirend** elemre.

        ![Házirend munkaterület megnyitása](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  A jobb szélen kattintson a **Házirend hozzáadása** elemre.

        ![Házirend hozzáadása](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  Bontsa ki az iOS csomópontot, válassza az **Általános konfiguráció** sort, és kattintson a **Házirend létrehozása** elemre.

        ![Általános konfigurációs házirend létrehozása iOS-eszközökhöz](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  Adjon meg egy nevet a házirend számára, kapcsolja be **A mobileszközök zárolásának feloldásához jelszó szükséges** beállítást, és állítsa a **Jelszó minimális hossza** beállítást **4** értékre.

        ![Jelszóbeállítások megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  Kattintson az **Igen** gombra a házirend telepítéséhez.

        ![Házirend telepítése](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  Kattintson a korábban létrehozott felhasználói csoportra, kattintson a **Hozzáadás** gombra, és kattintson az **OK** gombra.

        ![Házirend csoportjának kiválasztása](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        Most egy olyan, iOS PIN-kódokra vonatkozó házirenddel rendelkezik, amely a tesztfelhasználói csoportot célozza.

        ![Házirend beállítása kész](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## Annak ellenőrzése, hogy a házirend ki van-e kényszerítve az iOS-eszközökön

1.  Egy iPad készüléken indítsa el az iOS App Store áruházat, telepítse az ingyenes **Microsoft Intune Munkahelyi portál** alkalmazást, majd nyissa meg azt.

    ![A Vállalati portál telepítése](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  Adja meg a tesztfelhasználói fiók nevét és jelszavát, és koppintson a **Bejelentkezés** gombra.

    ![Hitelesítő adatok megadása](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  Koppintson a **Regisztrálás** gombra az eszköz Intune-ban való regisztrálásának megkezdéséhez.

    ![Regisztráció megkezdése](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  A **Profil telepítése** képernyőn koppintson a **Telepítés** gombra.

    ![Profil telepítése](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  A **Profil telepítése** párbeszédpanelen koppintson a **Telepítés** gombra.

    ![Profil telepítésének folytatása](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  A **Figyelmeztetés** képernyőn koppintson a **Telepítés** gombra.

    ![Figyelmeztető üzenet elfogadása](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  A **Távoli felügyelet** párbeszédpanelen koppintson a **Megbízhatóság** gombra.

    ![Távfelügyelet megbízhatóságának beállítása](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  A felügyeleti profil telepítésének befejezésekor koppintson a **Kész** gombra. A regisztrálás kész.

    ![Regisztráció kész](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. A regisztrálás befejezésekor koppintson az **OK** gombra, és zárja be a Munkahelyi portál alkalmazást.

    ![Az OK gomb megérintése a Vállalati portál alkalmazás bezárásához](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. Amikor a rendszer PIN-kód konfigurálását kéri be, koppintson a **Folytatás** gombra.

    ![PIN-kód beállítására felszólító kérés elfogadása](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. Írja be a PIN-kódját, koppintson a **Folytatás** gombra, írja be ismét a PIN-kódját, és koppintson a **Mentés** gombra.

    ![PIN-kód beállítása](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. Nyomja meg a bekapcsológombot az iPad zárolásához, csúsztassa el a zárolás feloldásához, és láthatja, hogy most be kell írnia a PIN-kódot az eszköz feloldásához.

### További információ
[Útmutató az Intune próbaverziójához](get-started-with-a-30-day-trial-of-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


