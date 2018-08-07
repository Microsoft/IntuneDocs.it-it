---
title: Impostazioni relative alla modalità tutto schermo per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo. Include la personalizzazione del menu Start, l'aggiunta di app, la barra della applicazioni e la configurazione di un Web browser. Configurare anche i dispositivi Windows Holographic for Business per l'esecuzione di più app in modalità tutto schermo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f10e7bb7a2e7c5e1d0e8b27517a62454e8bd630
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321802"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Impostazioni relative alla modalità tutto schermo per Windows 10 e versioni successive in Intune

I profili di modalità tutto schermo vengono usati per configurare i dispositivi Windows 10 per l'esecuzione di una o più app. Quando si crea un profilo di modalità tutto schermo è anche possibile scegliere se verrà visualizzato un menu Start, se verrà installato un Web browser e altro ancora.

## <a name="kiosk-settings"></a>Impostazioni della modalità tutto schermo

1. Selezionare **Aggiungi** per creare un ambiente di modalità tutto schermo.
2. Immettere il **nome di una configurazione di modalità tutto schermo**. Questo nome identifica un gruppo di applicazioni, il layout di queste app nel menu Start e gli utenti assegnati a questa configurazione di modalità tutto schermo.
3. Selezionare la **modalità tutto schermo**. La **modalità tutto schermo** identifica il tipo di modalità tutto schermo supportata dal criterio. Le opzioni includono:

    - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo.
    - **App singola per chiosco multimediale a schermo intero**: il profilo abilita il dispositivo per l'esecuzione come singolo account utente e lo blocca su un'unica app UWP (Universal Windows Platform). Pertanto, quando l'utente accede, viene avviata un'app specifica. Questa modalità impedisce anche all'utente di aprire nuove app o modificare l'app in esecuzione.
    - **Più app in modalità tutto schermo**: il profilo abilita il dispositivo per l'esecuzione di più app UWP (Universal Windows Platform) o app Win32. È anche possibile assegnare app diverse ad account utente diversi. Solo le app aggiunte sono disponibili agli utenti. Il vantaggio di avere più app in modalità tutto schermo, o un dispositivo predefinito per uno scopo, consiste nel garantire un'esperienza semplice, consentendo di accedere solo alle app necessarie e rimuovendo dalla visualizzazione le app non necessarie.

#### <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero
Immettere le impostazioni seguenti:

- **Identificatore dell'app UWP (Universal Windows Platform)**: Immettere l'**ID modello utente applicazione (AUMID, Application User Model ID)** dell'app in modalità tutto schermo. Oppure selezionare un'app gestita esistente aggiunta tramite [App per dispositivi mobili](apps-add.md).

    Vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata).

- **Tipo di account utente**: le opzioni disponibili sono le seguenti.

  - **Accesso automatico**: per i chioschi multimediali in ambienti pubblici con accesso automatico abilitato, è necessario usare un utente con privilegi minimi, ad esempio l'account utente standard locale. Per configurare un account Azure Active Directory (AD) per la modalità tutto schermo, usare il formato `AzureAD\user@contoso.com`.
  - **Account utente locale**: immettere l'account utente locale (per il dispositivo) o l'account di accesso di Azure AD associato all'app in modalità tutto schermo. Per gli account aggiunti ai domini di Azure AD, immettere l'account nel formato `domain\username@tenant.org`.

#### <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo
Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire. 

In [Più app in modalità tutto schermo](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) si usa una configurazione per chiosco multimediale che elenca le app consentite e altre impostazioni.

Immettere le impostazioni seguenti:

- **Aggiungi un'app di Win32**: un'app Win32 è un'app desktop tradizionale. Compilare i campi **Nome dell'app** e **Identificatore**. Il campo **Identificatore** deve contenere il nome del percorso completo del file eseguibile, relativo al dispositivo.
- **Aggiungi app gestite**: selezionare un'app gestita esistente aggiunta tramite [App per dispositivi mobili in Intune](apps-add.md).
- **Aggiungi un'app in base all'ID modello utente applicazione**: immettere l'[ID modello utente dell'applicazione](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (app UWP).
- **Barra delle applicazioni**: scegliere di **abilitare** (visualizzare) la barra delle applicazioni o di mantenerlo **non configurata** (nascosta) nel chiosco multimediale.
- **Layout del menu Start**: immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Leggere [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) per conoscere alcune linee guida e XML di esempio.

  In [Creare un chiosco multimediale Windows 10 che esegue più app](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) sono disponibili altri dettagli sull'uso e la creazione di file XML.

- **Tipo di account utente**: aggiungere uno o più account utente autorizzati a usare le app aggiunte. Quando l'account esegue l'accesso, sono disponibili solo le app definite nella configurazione. L'account può essere locale per il dispositivo o un account di accesso di Azure AD associato all'app in modalità tutto schermo.

    Per i chioschi multimediali in ambienti pubblici con accesso automatico abilitato, è necessario usare un tipo di utente con privilegi minimi, ad esempio l'account utente standard locale. Per configurare un account Azure Active Directory (AD) per la modalità tutto schermo, usare il formato `domain\user@tenant.com`.

## <a name="kiosk-web-browser-settings"></a>Impostazioni del Web browser in modalità tutto schermo

Queste impostazioni controllano un'app Web browser in modalità tutto schermo. Assicurarsi di avere distribuito un'app Web browser ai dispositivi in modalità tutto schermo usando [App per dispositivi mobili](apps-add.md).

1. Immettere le impostazioni seguenti:

    - **URL della home page predefinita**: immettere l'URL predefinito che verrà aperto dal browser in modalità tutto schermo all'apertura o al riavvio del browser.

    - **Pulsante Pagina iniziale**: visualizza (**Consenti**) o nasconde (**Non configurato**) il pulsante Pagina iniziale del browser in modalità tutto schermo. Per impostazione predefinita, il pulsante è Non configurato.

    - **Pulsante di spostamento**: visualizza (**Consenti**) o nasconde (**Non configurato**) i pulsanti Avanti e Indietro. Per impostazione predefinita, i pulsanti di spostamento sono Non configurati.

    - **Pulsante Termina sessione**: visualizza (**Consenti**) o nasconde (**Non configurato**) il pulsante Termina sessione. Quando visualizzato, l'utente seleziona il pulsante e l'app chiede conferma della chiusura della sessione. Se confermata, il browser cancella tutti i dati di esplorazione (cookie, cache e così via) e torna all'URL predefinito. Per impostazione predefinita, il pulsante è Non configurato. 

    - **Aggiorna il browser quando un utente supera il limite relativo al tempo di inattività**: specificare il numero di minuti di inattività della sessione prima del riavvio del browser in modalità tutto schermo con uno stato aggiornato. Il valore è un numero intero da 1 a 1440 minuti. Per impostazione predefinita, il valore è vuoto, ovvero non è indicato alcun timeout di inattività.

    - **Siti Web bloccati**: elenco di URL di siti Web bloccati (con supporto di caratteri jolly). Usare questa impostazione per impedire al browser di aprire siti specifici. È anche possibile **importare** un file con estensione csv contenente un elenco. Oppure creare un file con estensione csv (**Esporta**) contenente i siti aggiunti.

    - **Eccezioni per i siti Web**: elenco di eccezioni agli URL di siti Web bloccati (con supporto di caratteri jolly). Usare questa impostazione per consentire al browser di aprire siti specifici. Queste eccezioni sono un subset degli URL bloccati. Se un URL è presente nell'elenco dei siti Web bloccati e nell'elenco delle eccezioni dei siti Web, viene applicata l'eccezione.

    È anche possibile **importare** un file con estensione csv contenente un elenco. Oppure creare un file con estensione csv (**Esporta**) contenente i siti aggiunti.

2. Selezionare **OK** per salvare le modifiche.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

È possibile configurare i dispositivi Windows Holographic for Business per l'esecuzione di una o più app in modalità tutto schermo. 

#### <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero
Immettere le impostazioni seguenti:

- **Identificatore dell'app UWP (Universal Windows Platform)**: Immettere l'**ID modello utente applicazione (AUMID, Application User Model ID)** dell'app in modalità tutto schermo. Oppure selezionare un'app gestita esistente aggiunta tramite [App per dispositivi mobili](apps-add.md).

    Vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.

- **Tipo di account utente**: selezionare **Account utente locale** per immettere l'account utente locale (per il dispositivo) oppure un accesso con account Microsoft associato all'app in modalità tutto schermo. I tipi di account utente con **accesso automatico** non sono supportati in Windows Holographic for Business.

#### <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo
Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire.

Immettere le impostazioni seguenti:

- **Aggiungi app gestite**: selezionare un'app gestita esistente aggiunta tramite [App per dispositivi mobili in Intune](apps-add.md).
- **Aggiungi un'app in base all'ID modello utente applicazione**: immettere l'[ID modello utente dell'applicazione](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (app UWP).
- **Layout del menu Start**: immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) offre alcune indicazioni e include un file XML specifico per i dispositivi Windows Holographic for Business.
- **Tipo di account utente**: aggiungere uno o più account utente autorizzati a usare le app aggiunte. Le opzioni supportate includono: 
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Utenti di Azure AD**: richiede credenziali utente per l'accesso al dispositivo. Usare il formato `domain\user@tenant.com`.
  - **Account utente locale**: richiede credenziali utente per l'accesso al dispositivo. 

Quando l'account esegue l'accesso, sono disponibili solo le app definite nella configurazione.

## <a name="next-steps"></a>Passaggi successivi
[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
