---
title: Introduzione a Microsoft Intune
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
author: Lindavr
robots: noindex,nofollow
---
# Introduzione a Microsoft Intune
![](../Image/Nav-Icons/WIT_Tile_W_OverviewHighlight.png)[![](../Image/Nav-Icons/WIT_Tile_W_GetStarted.png)](https://technet.microsoft.com/library/dn646953.aspx/?WT.mc_id=IntuneGS20150801)[![](../Image/Nav-Icons/WIT_Tile_W_EnrollDevices.png)](https://technet.microsoft.com/library/dn646962.aspx/?WT.mc_id=IntuneEnroll20150801)[![](../Image/Nav-Icons/WIT_Tile_W_ManageDevices.png)](https://technet.microsoft.com/library/mt313202.aspx/?WT.mc_id=IntuneConfig20150801)[![](../Image/Nav-Icons/WIT_Tile_W_ManageApps.png)](https://technet.microsoft.com/library/dn646965.aspx/?WT.mc_id=IntuneDeploy20150801)[![](../Image/Nav-Icons/WIT_Tile_W_ProtectResources.png)](https://technet.microsoft.com/library/mt313203.aspx/?WT.mc_id=IntuneProtect20150801)[![](../Image/Nav-Icons/WIT_Tile_W_RetireData.png)](https://technet.microsoft.com/library/mt313204.aspx/?WT.mc_id=IntuneRetire20150801)[![](../Image/Nav-Icons/WIT_Tile_W_TechnicalReference.png)](https://technet.microsoft.com/library/mt282239.aspx/?WT.mc_id=IntuneTR20150801)[![](../Image/Nav-Icons/WIT_Tile_W_Troubleshooting.png)](https://technet.microsoft.com/library/mt345521.aspx)
![](../Image/Nav-Icons/WIT_Tile_Bar_Overview.png)

[!INCLUDE[wit_nextref](../Token/wit_nextref_md.md)] è un servizio basato su cloud che consente di gestire i dispositivi mobili, i PC e le app garantendo la produttività agli utenti e, allo stesso tempo, la protezione delle informazioni aziendali.

La gestione dei dispositivi mobili (MDM) e la gestione dei PC Windows rappresentano il fondamento di un reparto IT moderno. I lavoratori, il personale e gli studenti sono sempre più connessi e orientati alla mobilità. Il successo dipende dalla disponibilità di informazioni dove servono e dalla certezza che siano protette. È necessario distribuire le app, proteggere i dispositivi, assicurare che gli aggiornamenti siano applicati ed eseguire il provisioning della posta elettronica più rapidamente che mai, proteggendo al tempo stesso le informazioni aziendali.

## Modi diversi per gestire i dispositivi con Microsoft Intune
Sono disponibili diversi modi per usare Intune:

-   **Soluzione autonoma per la gestione dei dispositivi**. Come servizio basato su cloud, consente di gestire i dispositivi e proteggere i dati aziendali senza ulteriori costi per l'infrastruttura di rete.

    Intune può gestire i dispositivi iOS, Android, Mac OS X e Windows Phone, nonché dispositivi Windows RT e Windows 8.1 e Windows 10 come dispositivi mobili. Se con [!INCLUDE[wit_nextref](../Token/wit_nextref_md.md)] si cerca una soluzione Mobile Device Management (MDM), leggere [Funzionalità di gestione dei dispositivi mobili in Microsoft Intune](https://technet.microsoft.com/library/dn600287.aspx).

    È possibile installare il software client di [!INCLUDE[wit_nextref](../Token/wit_nextref_md.md)] nei PC Windows per consentire la gestione. In un computer gestito è possibile distribuire app e aggiornamenti software, gestire Endpoint Protection e Windows Firewall, fornire assistenza remota e molto altro. Vedere [l'elenco completo di funzionalità di gestione del computer](http://technet.microsoft.com/library/dn646975.aspx).

    Intune può essere usato anche per [distribuire e gestire le app](https://technet.microsoft.com/library/dn646965.aspx). La gestione delle app consente di evitare che i dati vengano condivisi all'esterno dell'azienda limitando azioni come le operazioni taglia, copia e incolla e i salvataggi tra app gestite da Intune e app personali. Questa protezione dei dati è incorporata direttamente in molte app per dispositivi mobili Microsoft, ma è possibile [estendere la protezione dei dati alle app line-of-business con Intune App Wrapping Tool](https://technet.microsoft.com/library/dn878026.aspx). Con [Intune Managed Browser](https://technet.microsoft.com/library/dn878029.aspx)è possibile impostare anche una visualizzazione dei contenuti sicura. Per proteggere ulteriormente le informazioni aziendali, è possibile [cancellare selettivamente le app gestite e i dati correlati](https://technet.microsoft.com/library/mt313204.aspx) nei dispositivi non registrati, non più conformi oppure smarriti, rubati o ritirati.

-   **Estensione cloud di Microsoft System Center 2012 Configuration Manager**. Se si usa già Configuration Manager per gestire i dispositivi locali e si cerca una soluzione per gestire molti dei dispositivi mobili moderni, è possibile [usare Intune come estensione di System Center 2012 Configuration Manager](https://technet.microsoft.com/library/dn957912.aspx#BKMK_HybridOfferings). Due dei principali vantaggi di questa opzione riguardano l'esperienza di gestione unificata per i dispositivi mobili e locali e la scalabilità. Questa implementazione ibrida di Intune consente di gestire più di 50.000 dispositivi.

-   **Parte della sottoscrizione a Microsoft Office 365**. Se si ha una sottoscrizione commerciale a Office 365, è possibile usare [le funzionalità di gestione dei dispositivi mobili di Intune predefinite in Office 365](https://technet.microsoft.com/library/dn957912.aspx#MDMOfferings). Questa opzione non è completa come quella della versione autonoma di Intune o della combinazione tra Intune e Configuration Manager, tuttavia consente di gestire i dispositivi iOS, Android e Windows Phone, creare criteri di sicurezza, limitare l'accesso alla posta elettronica e ai documenti di Office 365 nei dispositivi gestiti e usare la cancellazione selettiva per rimuovere Office 365 dai dispositivi gestiti.

-   **Parte di Microsoft Enterprise Mobility Suite**. La mobilità e il cloud sono fenomeni destinati a espandersi. Intune è un componente essenziale di [Microsoft Enterprise Mobility Suite (EMS)](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx%20), un set di servizi basati su cloud che fornisce il rilevamento delle minacce, la gestione dell'identità collegata alla protezione dei dati e la gestione dei dispositivi, offerti dalla versione autonoma di Intune.

## Requisiti per la configurazione di Intune
Sebbene Intune sia un servizio, e quindi elimina molti dei costi dell'infrastruttura, potrebbero essere richiesti comunque alcuni [requisiti di configurazione di rete](https://technet.microsoft.com/library/dn646950.aspx). Ad esempio, il firewall potrebbe bloccare per impostazione predefinita alcune delle porte di rete necessarie a [!INCLUDE[wit_nextref](../Token/wit_nextref_md.md)].  Inoltre, se si vogliono sincronizzare i dati da Exchange Server, potrebbe essere necessario applicare delle eccezioni al firewall.

Altre operazioni per [preparare la distribuzione di Intune](https://technet.microsoft.com/library/dn646966.aspx) includono:

-   configurare un portale aziendale affinché gli utenti possano registrare i dispositivi mobili in modo che vengano gestiti da Intune

-   comprendere l'uso della larghezza di banda previsto

-   decidere se usare il nome di dominio **onmicrosoft.com** predefinito o un nome di dominio di cui si è proprietari

## Vedere anche
[Guida alle considerazioni sulla progettazione per la gestione dei dispositivi mobili](https://technet.microsoft.com/en-us/library/mt143180.aspx)
[Documentazione di Microsoft Intune](../Topic/Documentation-for-Microsoft-Intune.md)



<!--HONumber=Mar16_HO3-->


