---
title: Proxybeállítások konfigurálása a Active Directory Intune-összekötőhöz
description: Ismerteti, hogyan konfigurálható az Intune-összekötő a Active Directory számára a meglévő helyszíni proxykiszolgálók használata esetén.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11537902e8306d753d6c3e144e0ac15f90ab3b51
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503288"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Meglévő helyszíni proxykiszolgálók használata

Ez a cikk azt ismerteti, hogyan konfigurálható az Intune-összekötő a Active Directory számára a kimenő proxykiszolgálók használatához. Olyan hálózati környezetű ügyfelek számára készült, amelyek meglévő proxykkal rendelkeznek.

További információ az összekötők működéséről: az [Azure ad Application proxy-összekötők ismertetése](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Kimenő proxyk megkerülése

Az összekötők olyan operációsrendszer-összetevőkkel rendelkeznek, amelyek kimenő kérelmeket hajtanak végre. Ezek az összetevők automatikusan megpróbálnak megkeresni egy proxykiszolgálót a hálózaton a webproxy automatikus felderítése (WPAD) használatával.

Az operációs rendszer összetevői a WPAD. domainsuffix DNS-címkeresés végrehajtásával kísérlik meg a proxykiszolgáló megkeresését. Ha a keresés a DNS-ben oldódik fel, akkor a WPAD. dat IP-címére kell HTTP-kérelmet készíteni. Ez a kérelem a proxy konfigurációs parancsfájlja lesz a környezetben. Az összekötő ezt a parancsfájlt használja a kimenő proxykiszolgáló kiválasztásához. Előfordulhat azonban, hogy az összekötői forgalom továbbra sem halad át a proxyn szükséges további konfigurációs beállítások miatt.

Az összekötőt úgy is beállíthatja, hogy megkerülje a helyszíni proxyt, hogy az az Azure-szolgáltatásokhoz közvetlen kapcsolatot használjon. Ezt a megközelítést javasoljuk, ha a hálózati házirend lehetővé teszi a számára, mert az azt jelenti, hogy egy kisebb konfigurációt kell fenntartania.

Az összekötőhöz tartozó kimenő proxyk használatának letiltásához szerkessze a: \Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config fájlt, és adja hozzá a proxy címe és a proxy portját a következő példában látható szakaszban:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Annak biztosítása érdekében, hogy a Connector Updater szolgáltatás a proxyt is megkerüljék, hasonló változást kell végeznie a C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Készítsen másolatot az eredeti fájlokról, ha az alapértelmezett. config fájlokra kell visszaállítania.

A konfigurációs fájlok módosítása után újra kell indítania az Intune Connector szolgáltatást. 

1. Nyissa meg a **Services. msc fájlt**.
2. Keresse meg és válassza ki az **Intune ODJConnector szolgáltatást**.
3. Válassza az **Újraindítás**lehetőséget.

![Képernyőfelvétel a szolgáltatás újraindításáról](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>További lépések

[Az eszközök kezelése](../remote-actions/device-management.md)