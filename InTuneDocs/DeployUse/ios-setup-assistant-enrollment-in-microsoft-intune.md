---
title: "iOS-eszközök Beállítási asszisztenssel végzett regisztrációja a Microsoft Intune-nal | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f3637e79e7b6f93820e775932653c41879f369fe
ms.openlocfilehash: b9cb10ccb26d4f61d63fb2dc6c18be48cc0a3182


---

# iOS-eszközök regisztrálása az Apple Configurator és a Beállítási asszisztens segítségével
Az Intune támogatja a vállalat által birtokolt iOS-eszközök Mac számítógépen futó [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eszköz segítségével történő regisztrálását. Ez a folyamat gyári alaphelyzetbe állítja az eszközt, és felkészíti azt a Beállítási asszisztens az eszköz új felhasználója által a vállalati szabályzatok előtelepítése mellett történő futtatására.


## iOS-eszközök Beállítási asszisztenssel végzett regisztrációja a Microsoft Intune-nal
Az Apple Configuratorrel gyári alaphelyzetbe állíthatja az iOS-eszközöket, és felkészítheti őket a beállításhoz az új felhasználó számára.  Ehhez a módszerhez az iOS-eszközt USB-kapcsolaton keresztül egy Mac számítógéphez kell csatlakoztatni a vállalati regisztráció beállítása érdekében. A módszer emellett feltételezi, hogy Ön az Apple Configurator 2.0 verziót használja. Az iOS-eszközre alkalmazott szabályzatnak általában *felhasználói affinitást* kell tartalmaznia az Intune Vállalati portál alkalmazás használatának engedélyezése érdekében.

**Előfeltételek**
* Fizikai hozzáférés iOS-eszközökhöz – Az eszközök konfigurálását jelszóvédelem nélkül kell megszüntetni (a gyári beállítások visszaállítása)
* Az eszközök sorozatszáma – [Az Apple-termékekhez tartozó sorozatszámok kikeresése](https://support.apple.com/en-us/HT204308)
* USB csatlakozókábelek
* Az [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)-s verzióját futtató Mac számítógép


1.  **Mobileszköz-csoport létrehozása** (nem kötelező) Ha vállalatának mobileszköz-csoportokra van szüksége az eszközök kezeléséhez, hozza létre ezeket a csoportokat. [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Profil létrehozása az eszközökhöz** Az eszközökre alkalmazott beállításokat egy eszközregisztrációs profil határozza meg. Ha még nem tette meg, az Apple Configurator eszközzel regisztrált iOS-eszközökhöz hozzon létre egy eszközregisztrációs profilt.

    ###### Profil létrehozása

    1.  A [Microsoft Intune felügyeleti konzolon](http://manage.microsoft.com) ugorjon a **Házirend** &gt; **Céges eszközök** elemre, és válassza a **Hozzáadás...** elemet.

    ![Eszközbeléptetési profil létrehozása](../media/pol-sa-corp-enroll.png)

    2.  Adja meg az eszközprofilok részleteit:

        -   **Név** – Az eszközregisztrációs profil neve. (A felhasználók számára nem látható)

        -   **Leírás** – Az eszközregisztrációs profil leírása. (A felhasználók számára nem látható)

        -   **Regisztráció részletei** – Meghatározza az eszközök regisztrációjának módját.

            -   **Rákérdezés a felhasználói affinitásra** – Az eszköz összekapcsolható egy felhasználóval a kezdeti beállítás során, majd az eszköznek engedélyezhető, hogy a felhasználó nevében hozzáférjen a vállalati adatokhoz és e-mailekhez. A Beállítási asszisztens legtöbb forgatókönyvéhez használja a **Rákérdezés a felhasználói affinitásra** lehetőséget.
            Ez a mód több forgatókönyvet is támogat:

                -   **A vállalat által birtokolt személyes eszköz** – A „Saját eszköz kiválasztása” (CYOD) hasonló a privát vagy személyes eszközökhöz, de a rendszergazda rendelkezik néhány jogosultsággal, például engedélyezett számára az eszköz törlése, alaphelyzetbe állítása, felügyelete és regisztrációjának törlése. Az eszköz felhasználója is telepíthet alkalmazásokat, és rendelkezik a legtöbb olyan eszközhasználati jogosultsággal, amelyek nem ütköznek a kezelési házirendbe és a rendszer nem blokkolja őket.

                -   **Eszközregisztráció-kezelő fiók** – Az eszközt egy speciális Intune rendszergazda fiók regisztrálja. A fiók kezelhető privát fiókként, de csak a regisztrációkezelő hitelesítő adataival rendelkező felhasználó telepíthet alkalmazásokat, vagy törölheti, állíthatja alaphelyzetbe, felügyelheti az eszközt, illetve csak ő törölheti a regisztrációját. A közös fiókon keresztül, számos felhasználó által közösen használt eszközök regisztrációjával kapcsolatos információkért lásd: [Vállalati tulajdonban lévő eszközök regisztrálása a Microsoft Intune-ban az Eszközregisztráció-kezelővel](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

            -   **Nincs megadva a felhasználói affinitás** – Az eszköz nem kapcsolódik felhasználóhoz. Ezt a kapcsolatot olyan eszközök esetén alkalmazza, amelyek a helyi felhasználói adatok nélkül hajtanak végre feladatokat. A felhasználói kapcsolatot igénylő alkalmazások le vannak tiltva, vagy nem fognak működni.

        -   **Előzetes eszközcsoport-hozzárendelés** – Minden, ezzel a profillal telepített eszköz kezdetben ehhez a csoporthoz fog tartozni. A regisztrálás után új csoportba sorolhatja az eszközöket.

        >[!Important]
        >A csoport-hozzárendelések az Intune-ból az Azure Active Directory-ba lesznek áthelyezve. [További információ](http://go.microsoft.com/fwlink/?LinkID=787064)

          -  **Device Enrollment Program** – Az Apple Device Enrollment Program (DEP) nem használható a Beállítási asszisztenssel végzett regisztrációhoz. Ellenőrizze, hogy a váltógomb **ki** értékre van-e állítva.

    3.  Profil hozzáadásához válassza a **Profil mentése** lehetőséget.

3.  **iOS-eszközök regisztrálása a telepítősegéddel** A [Microsoft Intune felügyeleti konzolon](http://manage.microsoft.com) válassza a **Csoportok** &gt; **Minden eszköz** &gt; **Minden céges eszköz** &gt; **Minden eszköz**, majd az **Eszközök hozzáadása...** lehetőséget. Két módon adhat hozzá eszközöket:

    ![Eszközök felvétele párbeszédablak](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Sorozatszámokat tartalmazó CSV-fájl feltöltése** – Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv), amelyben maximum 5000 eszköz szerepel. A csv-fájl mérete nem haladja meg az 5 MB-ot.

        |||
        |-|-|
        |&lt;1. sorozatszám&gt;|&lt;1. eszköz részletei&gt;|
        |&lt;2. sorozatszám&gt;|&lt;2. eszköz részletei&gt;|
        Ez a .csv- fájl egy szövegszerkesztőben megtekintve így jelenik meg:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Eszközadatok kézi hozzáadása** – Adja meg legfeljebb öt eszköz sorozatszámát és eszközadatait

    > [!NOTE]
    > Ha a később el kell távolítania vállalati tulajdonú eszközöket az Intune kezeléséből, az eszköz regisztrációjának letiltásához el kell távolítania az eszköz gyári számát az Intune-ból az **Előre regisztrált vállalati eszközök** elemcsoportban található **iOS-sorozatszám szerint** eszközcsoportot használva.  Ha az Intune vész-helyreállítási folyamatot hajt végre a sorozatszámok eltávolítása közben vagy az akörüli időszakban, győződjön meg arról, hogy a csoportban csak az aktív eszközök sorozatszámai szerepelnek.

    Kattintson a **Tovább** gombra.

4.  **Regisztrálni kívánt eszközök kiválasztása** Ellenőrizze a regisztrálni kívánt eszközöket. A már regisztrált vagy más módszerrel már regisztrált sorozatszámok nem importálhatók. A folytatáshoz válassza a **Tovább** gombot.

5.  **Profil hozzárendelése** Adja meg a hozzáadott eszközökhöz hozzárendelendő profilt az elérhető profilok listájából, tekintse át a **Regisztrációs profil részleteit**, és válassza a **Befejezés** gombot. A manuálisan hozzáadott eszközök bármilyen regisztrációs profilhoz hozzárendelhetők.

6.  **Exportálja az iOS-eszközökre telepítendő profilt** A [Microsoft Intune felügyeleti konzolon](http://manage.microsoft.com) válassza a **Házirend** &gt; **Munkahelyi eszközök regisztrációja** lehetőséget, majd válassza ki a mobileszközökre telepítendő eszközprofilt. Kattintson az **Exportálás...** lehetőségre a tálcán. Másolja ki és mentse el a **Profil URL-címét**. A címet később fel kell töltenie az Apple Configurator eszközbe az iOS-eszközök által használt Intune profil meghatározásához.
    Az Apple Configurator 2 támogatásához módosítania kell a 2.0-s profil URL-címét. Cserélje le ezt:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    a

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Az itt következő eljárás keretében az Apple Configurator segítségével feltölti a profil URL-címét az Apple DEP szolgáltatásába, ezzel meghatározza az iOS-eszközök által használandó Intune-profilt.



7.  **Az eszköz előkészítése az Apple Configuratorral** Az iOS-eszközök csatlakoznak a Mac számítógéphez, és regisztrálva vannak mobileszköz-kezelésre.

    1.  A Mac-számítógépen nyissa meg az **Apple Configurator 2** eszközt. A menüsávban válassza az **Apple Configurator 2**, majd a **Beállítások** elemet.

         > [!WARNING]
         > Az eszközökön vissza kell állítani a gyári beállításokat a regisztrációs folyamat során. Ajánlott eljárásként állítsa vissza az eszközt, és kapcsolja be. Ajánlott eljárás, hogy az eszközön legalább az **üdvözlőképernyőnek** kell megjelennie az eszköz csatlakoztatásakor.

    2. Válassza a Beállítások panel **Servers** (Kiszolgálók) elemét, majd az MDM Server wizard (MDM-kiszolgáló varázsló) elindításához válassza a bal oldali panel alatt található „+” szimbólumot. Kattintson a **Tovább** gombra.

    3. Töltse ki a **Name** (Név) és az **Enrollment URL** (Regisztrációs URL-cím) mezőket az MDM-kiszolgálóra vonatkozóan a fenti 6. pontnál szereplő adatok alapján. Az Enrollment URL (Regisztrációs URL-cím) mezőnél adja meg az Intune-ból exportált regisztrációs profil URL-címét. Kattintson a **Tovább** gombra.  

       Ha az Apple TV-re vonatkozó megbízhatóságiprofil-követelményekkel kapcsolatos figyelmeztetést kap, nyugodtan hagyja figyelmen kívül a **Trust Profile** (Megbízhatósági profil) beállítást a szürke X gombot választva. Ezenfelül a kapcsolattanúsítványokra (Anchor certificate) vonatkozó figyelmeztetést is figyelmen kívül hagyhatja. Válassza a **Next** (Tovább) gombokat a varázsló befejezéséig.

    4.  A **Servers** (Kiszolgálók) panelen válassza az új kiszolgálóprofil mellett található „Edit” (Szerkesztés) elemet. Ellenőrizze, hogy az Enrollment URL (Regisztrációs URL-cím) értéke pontosan egyezik-e az Intune-ból exportált URL-címmel. Ha nem, írja be újra az eredeti URL-címet, majd az Intune-ból exportált regisztrációs profil mentéséhez kattintson a **Save** (Mentés) gombra.

    5.  Az iOS-mobileszközöket csatlakoztassa az Apple számítógéphez egy USB-adapterrel.

        > [!WARNING]
        > Az eszközökön vissza kell állítani a gyári beállításokat a regisztrációs folyamat során. Ajánlott eljárásként állítsa vissza az eszközt, és kapcsolja be. Jó gyakorlat, ha a Beállítási asszisztens indításakor az eszközön az **üdvözlőképernyő** látható.

    6.  Válassza a **Prepare** (Előkészítés) lehetőséget. A **Prepare iOS Device** (iOS-eszköz előkészítése) panelen válassza a **Manual** (Manuális) elemet, majd a **Next** (Tovább) gombot.

    7. Az **Enroll in MDM Server** (Regisztrálás MDM-kiszolgálón) panelen válassza ki a létrehozott kiszolgáló nevét, majd válassza a **Next** (Tovább) gombot.

    8. A **Supervise Devices** (Eszközök felügyelete) panelen válassza ki a felügyelet szintjét, majd válassza a **Next** (Tovább) gombot.

    9. A **Create an Organization** (Szervezet létrehozása) panelen válassza ki a **szervezetet** vagy hozzon létre új szervezetet, majd válassza a **Next** (Tovább) gombot.

    10. A **Configure iOS Setup Assistant** (iOS-alapú Beállítási asszisztens konfigurálása) panelen válassza ki a felhasználó számára megjelenő lépéseket, majd válassza a **Prepare** (Előkészítés) gombot. Ha a rendszer kéri, végezzen hitelesítést a megbízhatósági beállítások frissítése érdekében.  

    11. Az iOS-eszköz előkészítésének befejezésekor leválaszthatja az USB-kábelt.  

8.  **Eszközök terjesztése** Az eszközök most már készen állnak a vállalati regisztrációra. Kapcsolja ki az eszközöket, és ossza ki őket a felhasználóknak. Az eszköz bekapcsolásakor elindul a Beállítási asszisztens.



### További információ
[Felkészülés az eszközök regisztrálására](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


