---
title: Az eszközhöz hiányzik egy tanúsítvány | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 9ac79311881b2f245cbdedcb6c9ac9763ba7cbf3
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857149"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>A szervezet által igényelt hiányzó tanúsítvány telepítése  

Ha az eszköz nincs regisztrálva az Intune-ban, és hiányzik egy szükséges tanúsítvány, nem fog tudni bejelentkezni a Céges portál alkalmazásba. Amikor megpróbál bejelentkezni, a következő üzenet jelenik meg:

![képernyőfelvétel-hibaüzenet-hiányzó-tanúsítványról](./media/andr-cert_install-1-cert_missing.png)

Két lehetőség közül választhat, ha le szeretné tölteni a szükséges tanúsítványt, és az eszköz regisztrálva lesz. 

- Böngésző-hozzáférés engedélyezése Céges portál alkalmazásban.
- Azonosítsa a hiányzó tanúsítványt a vállalat vagy az iskola SZÁMÍTÓGÉPén. Ezután keressen rá az interneten a hiányzó tanúsítvány letöltéséhez. 

Végezze el a böngészőalapú hozzáférés engedélyezésének lépéseit. Ezt követően, ha továbbra sem tudja regisztrálni az eszközt, kövesse az interneten található tanúsítvány megkereséséhez szükséges lépéseket. 

## <a name="enable-browser-access"></a>Böngészőalapú hozzáférés engedélyezése
A böngésző elérésének engedélyezéséhez hajtsa végre a következő lépéseket. A hozzáférés engedélyezése után Céges portál telepíti a megfelelő tanúsítványt, és folytatja a regisztrálást.    

1. A Céges portál alkalmazásban lépjen a jobb oldali sarokba, és válassza ki a menüt.  
2. Válassza a **Beállítások** lehetőséget.  
3. A **böngésző-hozzáférés engedélyezése lehetőség** mellett válassza az **Engedélyezés**lehetőséget.  
4. Az eszköz rendszergazdája képernyőn válassza az **aktiválás**lehetőséget. 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>A hiányzó tanúsítvány azonosítása és letöltése webes kereséssel
A következő lépések végrehajtásával manuálisan azonosíthatja és telepítheti a tanúsítványt az eszközön.  

1. Nyissa meg egy számítógépen az Internet Explorert. Ha nincs erre a célra használható számítógépe, forduljon a cég informatikai támogató szolgálatához. A cég informatikai támogató szolgálatának elérhetőségét a [Céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja.

2. Lépjen a [Céges portál webhelyére](https://go.microsoft.com/fwlink/?linkid=2010980), és jelentkezzen be a munkahelyi vagy iskolai fiókjával.

3. A böngésző címsorának jobb szélén válassza az alábbi képernyőképen látható, lakat alakú szimbólumot.

    ![képernyőfelvétel-internet-explorer-címsor-lakat-szimbólum](./media/andr-missing-cert-ie-padlock-symbol.png)

    Ha nem látja a lakat alakú szimbólumot, ne lépjen tovább, hanem forduljon a cég informatikai támogató szolgálatához. A lakat azt jelenti, hogy biztonságosan jelentkezett be, ezért ha nem látja a szimbólumot, nem javasolt a továbblépés.

4. Válassza a **Tanúsítványok megtekintése** elemet.

    ![képernyőfelvétel-internet-explorer-tanúsítvány-megtekeintése-gomb-webhely-azonosítási-párbeszédpanelén](./media/andr-missg-cert-ie-view-cert-button.png)

5. Válassza a **tanúsítvány elérési útja** fület, majd azonosítsa a tanúsítványt, amelyet az internetről kell lekérnie. A szükséges tanúsítvány neve ugyanazon a helyen lesz, mint az előbbi képernyőfelvételen kiemelt tanúsítványé.

6. Ha keresőmotort, például Binget vagy Google-t használ, keressen rá az előző szakaszban azonosított hiányzó tanúsítvány nevére. A tanúsítvány különböző „kiterjesztésekkel” rendelkezhet, például „.crt”, „.pem” stb.

7. Töltse le a főtanúsítványt a webhelyről.

8. Miután a tanúsítvány letöltése befejeződött, húzza le az értesítéseket fentről, és koppintson a tanúsítvány nevére az értesítések listájában.

4. Az alábbi képernyőképen látható **Name the Certificate** (A tanúsítvány elnevezése) párbeszédpanelben fogadja el az alapértelmezett tanúsítványnevet.

5. Győződjön meg arról, hogy **Credential Use** (Hitelesítő adatok használata) beállítás értéke **Used for VPN and apps** (VPN-hez és az alkalmazásokhoz használt), és koppintson az **OK** gombra.

    ![képernyőkép-tanúsítványnevet-mutató-képernyő](./media/andr-missing-cert-cert-name.png)

6. Zárja be a Céges portál alkalmazást.

7. Nyissa ismét meg a Céges portál alkalmazást. Ekkor már be kell, hogy tudjon jelentkezni a Céges portál alkalmazásba. Ha segítségre van szüksége, lépjen kapcsolatba a cég informatikai támogató szolgálatával.

Ha ugyanazt a „Hiányzó tanúsítvány” üzenetet látja, mint amelyik fentebb is látható, és már követte a fenti lépéseket, akkor valószínűleg egy másik tanúsítvány is van, amelyet a cég informatikai támogató szolgálatának segítségével telepíteni kell. Kérje a cég informatikai támogató szolgálatának segítségét a [Céges portál webhelyen](https://go.microsoft.com/fwlink/?linkid=2010980) található elérhetőségeken.

## <a name="next-steps"></a>További lépések  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
