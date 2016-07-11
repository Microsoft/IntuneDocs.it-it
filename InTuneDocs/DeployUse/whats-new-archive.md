---
title: "Archivio novità | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 051d06afb0f29f2a97c1f06dc1102138e5f2be8f


---


## Settembre 2015
### Aggiornamenti per la gestione di dispositivi mobili e app
**Tutte le funzionalità di gestione iOS per Intune ora supportano iOS 9** Per informazioni dettagliate sulle funzionalità di gestione di iOS 9, vedere [questo post di blog](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Nuovi criteri di configurazione di app per dispositivi mobili per iOS** Usare i nuovi criteri di configurazione di app per dispositivi mobili per specificare automaticamente le impostazioni che possono essere utili a un'app per iOS quando viene eseguita. Ad esempio, è possibile specificare una porta di rete o un nome utente. Per informazioni dettagliate, vedere [Configurare le app con i criteri di configurazione delle app per dispositivi mobili in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Gestione di app semplificata per gli utenti di iOS 9**
 In questa versione è possibile fare in modo che le app già distribuite vengano gestite da Intune per gli utenti di iOS 9. Per le versioni precedenti di iOS, quando si distribuisce un'app e sul dispositivo è già installata una versione non gestita dell'applicazione, è necessario chiedere all'utente di disinstallare manualmente l'app prima che sia possibile installare le app gestite con Intune.

 Tuttavia, a partire da questa release di Intune, è possibile richiedere agli utenti dei dispositivi iOS 9 di consentire che Intune si occupi della gestione dell'app e applichi tutti i criteri di gestione delle applicazioni mobili pertinenti.

 **Gestione di Windows 10** Usare i nuovi [criteri di configurazione generale di Windows 10](https://technet.microsoft.com/library/mt404697.aspx) per configurare password, dispositivi, browser e altre impostazioni per i dispositivi registrati che eseguono Windows 10 e Windows 10 Mobile.

 **Creare e distribuire app a dispositivi Windows 10 registrati** Un nuovo tipo di programma di installazione software, Windows Installer tramite MDM (&#42;.msi), consente di creare e distribuire le app di Windows Installer nei dispositivi registrati che eseguono Windows 10. Per informazioni dettagliate, vedere [Introduzione alla distribuzione dell'app in Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

**iOS**
* Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso del Portale aziendale per migliorare prodotti e servizi Microsoft. Gli utenti finali possono disattivare la raccolta dati tramite l'impostazione Dati sull'utilizzo del dispositivo. Gli amministratori invece non hanno controllo sulla raccolta dati e non possono modificare la selezione dell'utente relativa a questa impostazione.
* Supporto per la risoluzione a schermo intero in iPhone 6 e 6 Plus
* Correzioni dei bug per migliorare la sicurezza

### Novità della documentazione di Intune - Settembre 2015
**Nuovi argomenti**

|Nome|Dettagli|
|----|--------|
|[Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Si tratta di nuovi criteri di configurazione che consentono di gestire le impostazioni e le funzionalità dei dispositivi che eseguono Windows 10 e Windows 10 Mobile.
| [Configurare le app con i criteri di configurazione delle app mobili in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Si tratta di nuovi tipi di criteri che consentono di specificare automaticamente le impostazioni che possono essere necessarie quando l'utente esegue un'app iOS. |

**Argomenti aggiornati**

|Nome|Dettagli|
|----|-------|
|[Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Aggiornato per includere le informazioni più recenti che consentono di comprendere e creare i criteri.|

## Agosto 2015
### Aggiornamenti per la gestione di dispositivi mobili e app
* I**Termini e condizioni** per la registrazione di Intune e l'accesso aziendale ora vengono [gestiti tramite i criteri](https://technet.microsoft.com/library/mt405893.aspx). È possibile usare diversi tipi di termini e condizioni per soddisfare specifici requisiti per i gruppi di utenti. Ad esempio, è possibile distribuire termini e condizioni in lingue diverse ai gruppi di utenti definiti geograficamente. È anche possibile [modificare i termini e le condizioni](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) e specificare se aumentare i numeri di versione richiedendo agli utenti di accettare i nuovi termini e condizioni per poter usare il Portale aziendale.
* **Diversi criteri di Intune sono stati rinominati** per renderli più uniformi all'interno del prodotto e per semplificarne l'individuazione. Per un elenco di tutti i criteri di Intune disponibili, vedere [Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* I **profili certificati PKCS #12 (PFX)** sono disponibili per Android 4.0 o versioni successive e per Windows 10 (Desktop e Mobile) e versioni successive. L'uso di .PFX non richiede un server NDES. Per altre informazioni su come usare i profili certificato PFX, vedere [Abilitare l'accesso alle risorse aziendali usando i profili certificato con Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx).
* Le impostazioni **Limiti aziendali per Windows 10 Desktop e Mobile** abilitano impostazioni VPN granulari, come descritto in [Consentire agli utenti di connettersi al proprio lavoro tramite profili VPN con Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx).
* **L'app OneDrive per Android ora supporta più identità**. Questo e altri criteri di gestione delle app mobili sono descritti nell' [elenco di applicazioni Microsoft che è possibile gestire](https://technet.microsoft.com/library/dn708489.aspx).
* **Bypass del blocco attivazione iOS**. Se i dispositivi iOS di proprietà dell'azienda sono protetti dal blocco attivazione, è necessario immettere l'ID e la password Apple dell'utente per formattare o riattivare il dispositivo. Questo può costituire un problema se gli utenti lasciano la società e restituiscono un dispositivo aziendale senza aver prima disattivato Blocco attivazione. Per risolvere questo problema, si può usare [Bypass del blocco attivazione di Intune](https://technet.microsoft.com/library/mt414176.aspx).

### Accesso condizionale per i PC
Ora è possibile configurare i criteri di accesso condizionale per i PC. Questi criteri consentono alle app desktop di Office di accedere ai servizi di Exchange Online e SharePoint Online.
Per abilitare i criteri di accesso condizionale per i PC, è necessario che questi ultimi siano aggiunti a un dominio oppure che siano conformi.
* Vedere la sezione **Guida introduttiva** in [ Gestire l'accesso alla posta elettronica e a SharePoint con Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx) per un elenco completo di requisiti per abilitare l'accesso condizionale per i PC.
* Vedere [ Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) per le opzioni che è possibile impostare per abilitare l'accesso condizionale per l'accesso alla posta elettronica.
* Vedere [Gestire l'accesso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) per le opzioni che è possibile impostare per abilitare l'accesso condizionale per SharePoint Online.

### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

**Android**

Se il dispositivo non è ancora stato registrato per la gestione, dopo aver eseguito l'accesso gli utenti visualizzeranno le istruzioni di registrazione.

### Novità nella documentazione di Intune -- Agosto 2015
**Nuovi argomenti**

|Titolo|Dettagli|
|-----|-------|
|[Proteggere i dispositivi iOS con il bypass di Blocco attivazione per Microsoft Intune](https://technet.microsoft.com/library/mt414176.aspx)|Informazioni su come usare Intune per ignorare il blocco attivazione iOS quando un utente lascia l'azienda e restituisce un dispositivo bloccato.|

**Argomenti aggiornati**

|Titolo|Dettagli|
|-----|-------|
|[App Microsoft che è possibile usare con i criteri di gestione delle applicazioni mobili di Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx)|Aggiornato con le ultime informazioni sulle app che è possibile gestire con i criteri di gestione delle applicazioni mobili.
|[Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Aggiornato con i criteri più recenti aggiunti a Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jun16_HO4-->


