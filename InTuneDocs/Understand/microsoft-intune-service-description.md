---
title: Descrizione del servizio | Microsoft Intune
description: "Intune è un servizio basato su cloud che consente di gestire i PC Windows e i dispositivi mobili iOS, Mac OS X, Android e Windows."
keywords: 
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: e3694f80d6148abbce004bb0c7143bf394b313d9


---

# Descrizione del servizio Microsoft Intune

Microsoft Intune è un servizio basato su cloud che consente di gestire i PC Windows e i dispositivi mobili iOS, Mac OS X, Android e Windows. Intune consente inoltre di proteggere i dati e le applicazioni aziendali. È possibile usare Intune singolarmente oppure è possibile integrarlo con System Center Configuration Manager per aumentare le funzionalità di gestione. 

Microsoft offre l'onboarding benefit di Intune per i servizi idonei nei piani idonei. L'onboarding benefit consente di collaborare in remoto con gli esperti Microsoft per preparare l'ambiente Intune. Per altre informazioni, vedere [Processo di onboarding benefit di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=619281).

È possibile iniziare a usare Intune con una versione di valutazione gratuita di 30 giorni che include 100 licenze utente. Per avviare la versione di valutazione gratuita, [fare clic qui per visitare la pagina di registrazione a Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Se l'organizzazione dispone di un Enterprise Agreement o di un Contratto multilicenza equivalente, contattare il proprio rappresentante Microsoft per configurare la versione di valutazione gratuita.

> [!NOTE]
> Se l'organizzazione dispone di un account aziendale o dell'istituto di istruzione di Microsoft Online Services e si prevede di continuare a usare la sottoscrizione di Intune nell'ambiente di produzione alla scadenza del periodo di valutazione, fare clic sull'opzione **Accedi** nella pagina ed eseguire l'autenticazione usando l'account dell'amministratore globale dell'organizzazione. Questa operazione consente infatti di collegare la versione di valutazione di Intune all'account aziendale o dell'istituto di istruzione.

Per un elenco di impostazioni configurabili nei dispositivi mobili, vedere:

-   [Funzionalità di gestione dei dispositivi registrati di Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune) 

-   [Gestione di dispositivi mobili ibridi con System Center Configuration Manager e Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx) 

Per informazioni su System Center Configuration Manager, vedere [Documentazione per System Center Configuration Manager](https://technet.microsoft.com/library/mt346023.aspx).

## Informazioni sull'impatto degli aggiornamenti del servizio Intune
Poiché Intune è un servizio online, Microsoft può aggiornarlo a intervalli regolari.

Usare le informazioni in questo argomento per comprendere la frequenza di questi aggiornamenti del servizio e la notifica avanzata che viene fornita all'utente quando un aggiornamento può avere effetto sull'uso del servizio.

Per informazioni sulle modifiche apportate al servizio Intune, vedere [Novità di Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune). Nel [blog di Microsoft Intune](http://blogs.technet.com/b/microsoftintune/) vengono anche illustrate le modifiche apportate al servizio e vengono offerti suggerimenti utili che consentono di ottenere notevoli vantaggi da Intune. 

Importanti aggiornamenti di servizio vengono comunicati anche nel Centro messaggi del [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx). Se si installa l'[app mobile Amministrazione di Office 365](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) complementare è possibile ricevere notifiche sul dispositivo mobile.

> [!NOTE]
> È possibile monitorare lo stato del servizio Intune nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx). Scegliere **Integrità dei servizi** nel riquadro a sinistra.  

Ecco i tipi di comunicazioni che Microsoft invia sul servizio di Intune:
-   Per consentire la pianificazione per le modifiche del servizio, viene inviata una notifica almeno da 30 a 90 giorni prima dell'aggiornamento del servizio, a seconda dell'impatto della modifica. Tramite canali di comunicazione integrati nel prodotto, ad esempio gli avvisi in bacheca. Queste modifiche possono prevedere:
* Aggiornamenti che possono avere impatti normativi o di conformità
* Modifiche all'esperienza utente, all'interfaccia utente e ai flussi di lavoro
* API nuove o modificate: si riceve una notifica che indica la necessità di eseguire un test per garantire la compatibilità delle app personalizzate
* Modifiche ai requisiti di sistema, ad esempio per la versione minima del browser richiesta
* Aggiornamenti che richiedono l'intervento dell'utente per abilitare una funzionalità o per evitare interruzioni della funzionalità.
-   Con l'aggiornamento mensile del servizio Microsoft offre informazioni sulle nuove funzionalità, nuove funzionalità e miglioramenti alle funzionalità esistenti. In genere, Microsoft rilascia gli aggiornamenti del servizio nella metà di ogni mese. Gli aggiornamenti sono descritti in [Novità di Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune).
-   In caso di chiusura del servizio Intune, verrebbe inviata una notifica con un anticipo di 12 mesi.

## Scegliere una soluzione di gestione adatta alle esigenze della propria azienda
È possibile configurare Intune in vari modi per gestire e consentire di proteggere i computer e i dispositivi mobili della società (definiti semplicemente **dispositivi** in questo documento).

-   **Configurazione autonoma di Intune.** Per gestire i dispositivi della propria organizzazione, usare la console di amministrazione basata sul Web in Intune. Intune può essere usato senza alcuna infrastruttura IT, ma se si usa Intune con Servizi di dominio Active Directory, è possibile usare con Intune gli account utente di dominio gestiti con Servizi di dominio.

-   **Intune con System Center Configuration Manager.** Per gestire computer e dispositivi mobili nell'azienda, usare la console di gestione di Configuration Manager. Questa configurazione consente di gestire tutti i dispositivi dell'organizzazione tramite un'unica console, la console di amministrazione di Configuration Manager. Configuration Manager supporta un grandissimo numero di dispositivi mobili, server e computer. Per altre informazioni, vedere [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx) (Gestione ibrida di dispositivi mobili con System Center Configuration Manager e Microsoft Intune).  Per altre informazioni sulla scelta dell'approccio più adatto per l'utente, vedere [Choose between Microsoft Intune standalone and hybrid mobile device management with System Center Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx) (Scegliere tra la gestione di dispositivi mobili di Microsoft Intune autonoma e ibrida con System Center Configuration Manager). 


## Altre informazioni su Intune
Per altre informazioni su Intune, usare queste risorse:

-   Il [Centro protezione di Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) offre informazioni sulle procedure relative alla sicurezza, alla privacy e alla conformità di Intune e descrive alcune delle certificazioni di Intune.

-   [Funzionalità di gestione dei dispositivi registrati di Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune) 

### Vedere anche
[Microsoft Intune](https://docs.microsoft.com/intune/)
[Libreria della documentazione di System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Novità di Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Sep16_HO4-->


