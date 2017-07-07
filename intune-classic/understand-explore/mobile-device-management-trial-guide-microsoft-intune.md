---
title: Valutare la gestione dei dispositivi mobili in Microsoft Intune
description: Valutare la gestione dei dispositivi mobili nella versione di valutazione gratuita di Intune.
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: adef9335d8f199e8dec56e92eb1fda8c180ac6ce
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>Valutare la gestione dei dispositivi mobili in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questa guida di valutazione illustra il funzionamento della gestione dei dispositivi mobili in Intune. Si apprenderà come:
- Registrare un dispositivo da gestire in Intune.
- Creare gruppi per organizzare utenti e dispositivi.
- Creare criteri di gestione dei dispositivi e distribuirli ai gruppi.
- Pubblicare un'app e consentire agli utenti con dispositivi registrati di installarla.
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>Presupposti
In questa guida si presuppone che la versione gratuita venga usata soltanto a scopo di valutazione. Si presuppone inoltre che, quando si esegue la sottoscrizione, si inizi con un ambiente "pulito".

Per facilitare l'utilizzo della versione di valutazione, viene impostato un ambiente molto semplice che usa esclusivamente Intune e presuppone che quest'ultimo sia l'autorità di gestione di dispositivi mobili. Nel corso della guida, tuttavia, verranno forniti collegamenti a contenuti tecnici, da usare per uno studio più approfondito.

Con la versione di valutazione è possibile eseguire le stesse operazioni consentite da una versione in abbonamento. L'unica differenza è che la versione di valutazione è limitata a 100 account utente.

## <a name="whats-not-covered"></a>Argomenti non trattati
|Se si è interessati a quanto segue |Leggere |
|------------------------|----------|
|Gestione dei dispositivi mobili in un ambiente non di test | [Guida introduttiva di Intune](/intune/setup-steps) |
|Gestione dei dispositivi mobili con Intune e System Center Configuration Manager | [Gestione ibrida dei dispositivi mobili](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management) |

Rispetto alla guida di valutazione, le guide sopra indicate sono più lunghe e approfondite. Illustrano infatti la configurazione di Intune negli ambienti di produzione e spiegano numerosi punti critici che è necessario prendere in considerazione.

Per acquisire rapidamente familiarità con Intune, è consigliabile iniziare dalla guida di valutazione e quindi passare alle altre guide.

## <a name="prerequisites-for-this-evaluation"></a>Prerequisiti per la versione di valutazione
- Internet Explorer 10 o versione successiva
- Un dispositivo da usare per testare la modalità di registrazione e di gestione dei dispositivi degli utenti Intune tramite il portale aziendale. In questa guida vengono usati un iPad e un telefono Android.
- Per gestire l'iPad o altri dispositivi iOS, è necessario un [certificato del servizio Apple Push Notification](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).
- Una [sottoscrizione di valutazione di Intune](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili
Il primo passaggio da eseguire per gestire i dispositivi mobili con Intune è l'impostazione dell'**autorità di gestione dei dispositivi mobili (MDM)**.

Se si usa la versione autonoma di Intune, come si presuppone per questa versione di valutazione, o se si usa Intune come parte di una sottoscrizione Enterprise Mobility + Security (EMS), è necessario impostare Intune in modo che sia l'autorità di gestione dei dispositivi mobili. In altri termini, Intune viene definito come servizio usato per la gestione dei dispositivi mobili all'interno dell'organizzazione.

I clienti che intendono usare Intune con System Center Configuration Manager per la gestione dei dispositivi mobili devono decidere se usare Intune o Configuration Manager come autorità di gestione dei dispositivi mobili. Negli ambienti di produzione si tratta di una decisione molto importante: una volta eseguita l'impostazione, infatti, è molto difficile modificarla. In ogni caso, quest'ultima operazione esula dall'ambito della guida di valutazione. Per altre informazioni sulle implicazioni dell'impostazione di Intune o di Configuration Manager come autorità di gestione dei dispositivi mobili, vedere [Choose between standalone Intune and hybrid mobile device management](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) (Scegliere tra la versione autonoma di Intune e la gestione ibrida dei dispositivi mobili).

Intune verrà impostato come autorità di gestione dei dispositivi mobili per la versione di valutazione. Questa scelta non avrà effetti sull'ambiente di produzione, a meno che non si decida di usare la versione di valutazione per tale ambiente.

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Amministrazione**&gt;**Gestione dispositivi mobili**.
2. Nell'elenco **Attività** scegliere **Set MDM Authority** (Imposta autorità MDM). Verrà visualizzata la finestra di dialogo **Imposta autorità MDM**.
3. Intune richiede di confermare che si vuole usare Intune come autorità di gestione dei dispositivi mobili. Selezionare la casella di controllo e quindi scegliere **Sì** per usare Intune per la gestione dei dispositivi mobili.

## <a name="enroll-your-test-devices-into-intune"></a>Registrare dispositivi di test in Intune

In questa guida vengono registrati un telefono Android e un iPad Apple. Al termine della sezione, vengono comunque forniti collegamenti per [altre informazioni sulla registrazione dei dispositivi in Intune](#Learn-more-about-device-enrollment).
### <a name="android"></a>Android
Installare l'app **Portale aziendale di Intune** di Microsoft Corporation disponibile in [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) e accedere con le [credenziali utente create](sign-up-for-30-day-trial-microsoft-intune.md#add-users) al momento dell'iscrizione per questa versione di valutazione gratuita.

### <a name="ios"></a>iOS
Per consentire agli utenti di registrare dispositivi iOS, è necessario impostare Intune per la gestione di tali dispositivi.

1. **Ottenere una richiesta di firma del certificato**<br/>
Accedere a Intune con l'account amministratore e passare ad **Amministrazione** > **Gestione dispositivi mobili** > **iOS e Mac OS X** > **Carica un certificato APN** e quindi scegliere **Scarica richiesta di certificato APN**. Salvare il file della richiesta di firma del certificato (estensione csr) in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.
2.  **Ottenere un certificato di Apple Push Notification Service**<BR/>
Visitare il [portale Apple Push Certificates](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2) e accedere con il proprio ID Apple per creare il certificato APN usando il file con estensione csr. Dopo aver scelto **Upload on Apple's Push Certificate Portal** (Carica nel portale Apple Push Certificates), si riceverà un file con estensione json che non può essere usato per il servizio APN. Completare il download e tornare al portale Apple Push Certificates per i certificati per server di terze parti e quindi fare clic su **Scarica**.<br/>
Scaricare il certificato APN (con estensione pem) e salvare il file in locale. Questo ID Apple dovrà essere usato in futuro per rinnovare il certificato APN.
3.  **Aggiungere il certificato APN a Intune**<BR/>
Nella console di amministrazione di Microsoft Intune passare ad **Amministrazione** > **Gestione dispositivi mobili** > **iOS e Mac OS X** > **Carica un certificato APN** e quindi scegliere **Carica il certificato APN**. Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi immettere l'ID Apple. Con il certificato APN, Intune può registrare e gestire i dispositivi iOS effettuando il push dei criteri nei dispositivi mobili registrati.
4.  **Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali.**<br/>
Per istruzioni sulla registrazione da parte degli utenti finali, vedere [Registrare il dispositivo iOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) e [Registrare il dispositivo Mac OS X in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos). Il processo di registrazione indica agli utenti cosa possono aspettarsi e i dati visibili o meno agli amministratori IT nei propri dispositivi.


### <a name="learn-more-about-device-enrollment"></a>Ulteriori informazioni sulla registrazione dei dispositivi

Intune supporta le piattaforme per dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

I requisiti per l'abilitazione della gestione dei dispositivi dipendono dalla piattaforma che si intende gestire.
- I dispositivi mobili **Android** consentono agli utenti di [effettuare la registrazione tramite l'app Portale aziendale](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune) disponibile da Google Play. Non sono richieste ulteriori operazioni di configurazione in Intune.
- [Requisiti di impostazione per **iOS e Mac OS X**](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)

- [Requisiti di impostazione per **Windows Phone**](/intune-classic/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).






## <a name="next-steps"></a>Passaggi successivi
[Creare gruppi per organizzare utenti e dispositivi](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)