---
title: Configurare le impostazioni proxy per il connettore di Intune per Active Directory
description: Viene illustrato come configurare il connettore di Intune per Active Directory per l'uso dei server proxy locali esistenti.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 529bf4cbf3658d492776afc0433926d85535b1f8
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723359"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Usare i server proxy locali esistenti

Questo articolo illustra come configurare il connettore di Intune per Active Directory per l'uso dei server proxy in uscita. L'articolo è destinato ai clienti con ambienti di rete in cui sono presenti proxy.

Per altre informazioni sul funzionamento dei connettori, vedere [Informazioni sui connettori di Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Ignorare i proxy in uscita

I connettori hanno componenti del sistema operativo sottostanti che effettuano richieste in uscita. Questi componenti cercano automaticamente di individuare un server proxy nella rete usando WPAD (Web Proxy Auto-Discovery).

I componenti del sistema operativo provano a individuare un server proxy eseguendo una ricerca DNS per wpad.domainsuffix. Se la ricerca restituisce il DNS, viene quindi inviata una richiesta HTTP all'indirizzo IP per wpad.dat. Questa richiesta diventa lo script di configurazione proxy nell'ambiente. Il connettore usa questo script per selezionare un server proxy in uscita. Il traffico del connettore potrebbe tuttavia non riuscire ancora a passare perché sono necessarie altre impostazioni di configurazione nel proxy.

È possibile configurare il connettore in modo che ignori il proxy locale, per garantire che usi la connettività diretta ai servizi di Azure. Se consentito dai criteri di rete, questo approccio è consigliato, perché implica una configurazione in meno da gestire.

Per disabilitare l'uso del proxy in uscita per il connettore, modificare il file C:\Programmi\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config e aggiungere l'indirizzo e la porta del proxy nella sezione indicata nell'esempio di codice seguente:

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

Per assicurarsi che anche il servizio Connector Updater ignori il proxy, apportare una modifica simile al file C:\Programmi\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

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

Assicurarsi di creare copie dei file originali nel caso sia necessario ripristinare i file config predefiniti.

Dopo che i file di configurazione sono stati modificati, è necessario riavviare il servizio connettore di Intune. 

1. Aprire **services.msc**.
2. Individuare e selezionare **Servizio Connettore ODJ di Intune**.
3. Selezionare **Riavvia**.

![Screenshot del riavvio del servizio](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Passaggi successivi

[Gestire i dispositivi](../remote-actions/device-management.md)