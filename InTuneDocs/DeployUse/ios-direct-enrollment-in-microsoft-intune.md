---
title: "iOS-eszközök közvetlen regisztrációja | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1b942c7e09e59de59e3e406b84a21a712c0e973a
ms.openlocfilehash: 8fea0f7f87972bc643bbb20348095e05f701287e


---

# iOS-eszközök közvetlen regisztrálása az Apple Configurator használatával
Az Intune támogatja a vállalat által birtokolt iOS-eszközök Mac számítógépen futó [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eszköz segítségével történő regisztrálását. Ez a folyamat nem állítja gyári alaphelyzetbe az eszközt, és az eszközt előre definiált szabályzattal regisztrálja. Ez a módszer azokon az eszközökön használható, amelyeken **Nincs megadva felhasználói affinitás**. A módszer használatához az iOS-eszközt USB-kapcsolaton egy Mac géphez kell csatlakoztatni a vállalati regisztráció beállítása érdekében. A vállalati portál alkalmazás nem támogatott a közvetlen módon regisztrált eszközökön. Ez az útmutató feltételezi, hogy az Apple Configurator 2.0 verzióját használja egy Mac-gépen.

1.  **Profil létrehozása az eszközökhöz** Az eszközökre alkalmazott beállításokat egy eszközregisztrációs profil határozza meg. Ha még nem tette meg, az Apple Configurator eszközzel regisztrált iOS-eszközökhöz hozzon létre egy eszközregisztrációs profilt.

    #### Profil létrehozása

    1.  A [Microsoft Intune felügyeleti konzolon](http://manage.microsoft.com) ugorjon a **Házirend** &gt; **Munkahelyi eszközök regisztrációja** elemre, majd válassza a **Hozzáadás...** lehetőséget.

        ![Eszközbeléptetési profil létrehozása oldal](../media/pol-sa-corp-enroll.png)

    2.  Adja meg az eszközprofilok részleteit:

        -   **Név** – Az eszközregisztrációs profil neve. A felhasználók számára nem látható.

        -   **Leírás** – Az eszközregisztrációs profil leírása. A felhasználók számára nem látható.

        -   **Felhasználói kapcsolat** – Meghatározza az eszközök regisztrációjának módját. A közvetlen regisztrációhoz válassza a **Nincs felhasználói affinitás**lehetőséget.

        -   **Előzetes eszközcsoport-hozzárendelés** – Minden, ezzel a profillal telepített eszköz kezdetben ehhez a csoporthoz fog tartozni. A regisztrálás után új csoportba sorolhatja az eszközöket.

        >[!Important]
        >A csoport-hozzárendelések az Intune-ból az Azure Active Directory-ba kerülnek át. [További információ](http://go.microsoft.com/fwlink/?LinkID=787064)
    3.  Profil hozzáadásához válassza a **Profil mentése** lehetőséget.

5.  **A profil exportálása .mobileconfig fájlként, iOS-eszközökre telepítéshez** Válassza ki a létrehozott eszközprofilt. Kattintson az **Exportálás...** lehetőségre a tálcán. Válassza a **Profil letöltése** elemet, és mentse a letöltött .mobileconfig fájlt.

6.  **A fájl átvitele** Másolja a letöltött .mobileconfig fájlt egy Mac számítógépre.
    > [!NOTE]
    > A regisztrációs profil URL-címe az exportálástól számított két hétig érvényes. Két hét után új regisztrációs profil URL-címet kell exportálnia az iOS-eszközök Beállítási asszisztenssel végzett regisztrálásához.
7.  **Az eszköz előkészítése az Apple Configuratorral** Az iOS-eszközök csatlakoznak a Mac számítógéphez, és regisztrálva vannak mobileszköz-kezelésre.

    1.  A Mac számítógépen indítsa el az **Apple Configurator 2.0-t**.

    2.  Csatlakoztassa az iOS-eszközt a Mac számítógéphez egy USB-kábellel. Zárja be a **Fotók**, az **iTunes** és más alkalmazásokat, amelyek nyitva voltak az eszköz észlelésekor.

    3.  Az Apple Configuratorban kattintson egyszer a csatlakoztatott iOS-eszközre, majd válassza az **Add** (Hozzáadás) gombot. Az eszközhöz adható lehetőségek a legördülő listában jelennek meg. Válassza a **Profilok** lehetőséget.

    4.  A fájlkiválasztóval válassza ki az Intune-ból exportált .mobileconfig fájlt, majd válassza az **Add** (Hozzáadás) gombot. Ezzel a profil hozzá lesz adva az eszközhöz.  Ha az eszköz **Felügyeletlen**, a telepítéshez az eszköz elfogadására van szükség.

8.  **A profil telepítése** Most már készen áll a profil iOS-eszközre telepítésére. Az eszköz elvileg elvégezte a Beállítási asszisztens lépéseit, és készen áll a használatra.  Ha a regisztrációba alkalmazástelepítések tartoznak, az eszközhöz be kell állítani egy Apple ID-t, mert az alkalmazástelepítésekhez Apple ID-vel kell bejelentkezni az Apple Store áruházba.

    ###### Profilelfogadás felügyeletlen iOS-eszközök esetében

    1.  Oldja fel az iOS-eszköz zárolását.

    2.  A **Felügyeleti profil** **Profil telepítése** párbeszédpanelén koppintson a **Telepítés** gombra.

    3.  Adja meg az **Eszköz PIN-kódját** vagy az **Apple ID-t**, ha szükséges.

    4.  Fogadja el a **Figyelmeztetést**, és koppintson a **Telepítés** gombra.

    5.  Fogadja el a **Távoli figyelmeztetést**, és koppintson a **Megbízhatóság** gombra.

    6.  Amikor a **Profil telepítve** mező megerősíti, hogy a profil **Telepítve** van, válassza a **Kész** gombot.

9. **A profil ellenőrzése**
    Az iOS-eszközön indítsa el a **Beállítások** alkalmazást, majd válassza az **Általános** &gt; **Eszközfelügyelet** &gt; ** Felügyeleti profil** &gt;  lehetőséget, és ellenőrizze, hogy a profiltelepítés szerepel-e a listán, valamint ellenőrizze az iOS-házirend korlátozásait és a telepített alkalmazásokat. A házirend-korlátozások és alkalmazások megjelenítése az eszközön akár 10 percet is igénybe vehet.

10. **Eszközök terjesztése** Az iOS-eszköz most már felügyelt, és regisztrálva van az Intune-ban.


### Lásd még:
[Felkészülés az eszközök regisztrálására](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


