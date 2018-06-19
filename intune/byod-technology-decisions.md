---
title: Decisioni in merito alla tecnologia per BYOD con EMS
description: Principali decisioni in merito alla tecnologia da prendere per l'abilitazione di BYOD e la protezione dei dati aziendali con Microsoft Enterprise Mobility + Security.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.openlocfilehash: 7fb86ae8d3163e14581ee495004b74f684d30cec
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31832768"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Decisioni in merito alla tecnologia per l'abilitazione di BYOD con Microsoft Enterprise Mobility + Security (EMS)

Durante l'elaborazione della strategia per consentire ai dipendenti di lavorare in remoto con i dispositivi personali (BYOD), è necessario prendere decisioni chiave per gli scenari di abilitazione di BYOD e per le modalità di protezione dei dati aziendali. Fortunatamente, EMS offre tutte le funzionalità necessarie in un set di soluzioni completo.  

In questo argomento viene esaminato il caso d'uso semplice di abilitazione di BYOD per l'accesso alla posta elettronica aziendale. Si porrà particolarmente attenzione sulla necessità o meno di gestire l'intero dispositivo o solo le applicazioni, entrambe scelte del tutto valide.

## <a name="assumptions"></a>Presupposti
* Conoscenze di base di Azure Active Directory e Microsoft Intune
* Account di posta elettronica ospitati in Exchange Online

## <a name="common-reasons-to-manage-the-device-mdm"></a>Motivi comuni per scegliere la gestione dei dispositivi (MDM)
È possibile richiedere facilmente agli utenti di registrare i propri dispositivi nella gestione dei dispositivi tramite la distribuzione di criteri di [accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) in Exchange Online. L'elenco seguente include i motivi validi per optare per la gestione dei dispositivi personali:

**WiFi/VPN**: se gli utenti necessitano di un profilo di connettività aziendale per la produttività, è possibile configurarlo facilmente.

**Applicazioni**: se gli utenti hanno l'esigenza di ricevere un set di app nel dispositivo tramite push, è possibile gestire facilmente il recapito. Sono incluse le applicazioni che potrebbero essere richieste dall'azienda per motivi di sicurezza, ad esempio un'app Mobile Threat Defense.

**Conformità**: alcune organizzazioni devono conformarsi alle normative o ad altri criteri che prescrivono controlli MDM specifici. Ad esempio, è necessaria una soluzione MDM per crittografare l'intero dispositivo o per generare un report di tutte le app nel dispositivo.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Motivi comuni per scegliere di gestire solo le app (MAM)
La scelta di soluzioni MAM senza MDM è molto comune per le organizzazioni che supportano BYOD. È possibile richiedere agli utenti di accedere alla posta elettronica da Outlook Mobile (che supporta le protezioni MAM) tramite la distribuzione di criteri di accesso condizionale in Exchange Online. L'elenco seguente include i motivi validi per optare solo per la gestione delle app nei dispositivi personali:

**Esperienza utente**: la registrazione MDM include molti messaggi di avviso (applicati dalla piattaforma) che spesso portano l'utente a decidere di non usare affatto la posta elettronica dal dispositivo personale. MAM genera molti meno avvisi per gli utenti, che ricevono semplicemente un messaggio popup una sola volta per segnalare che sono attive protezioni MAM.

**Conformità**: alcune organizzazioni devono rispettare criteri che richiedono meno funzionalità di gestione nei dispositivi personali. Ad esempio, MAM consente solo di rimuovere i dati aziendali dalle app, diversamente da MDM che consente la rimozione di tutti i dati dal dispositivo.

![Immagine di confronto della gestione dei dispositivi e delle app nei dispositivi mobili](./media/byod-app-device-mgmt.png)

Altre informazioni sui [cicli di vita della gestione dei dispositivi e della gestione delle app](introduction-device-app-lifecycles.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Confronto delle funzionalità MDM e MAM
Come già accennato, con l'accesso condizionale è possibile richiedere a un utente di registrare il dispositivo o di usare un'app gestita come Outlook Mobile. In entrambi i casi possono essere applicate molte altre condizioni, tra cui:

* Utente che tenta l'accesso
* Posizione attendibile o non attendibile
*   Livello di rischio di accesso
* Piattaforma per i dispositivi

Molte organizzazioni spesso sono ancora preoccupate per rischi specifici.  La tabella seguente elenca le preoccupazioni più comuni e le soluzioni offerte da MDM e MAM.

| Preoccupazione   |   MDM  |   MAM  |
|------------|--------|--------|
|Accesso ai dati non autorizzato | Richiedere l'appartenenza a gruppi | Richiedere l'appartenenza a gruppi |
|Accesso ai dati non autorizzato | Richiedere la registrazione dei dispositivi | Richiedere app protette |
|Accesso ai dati non autorizzato | Richiedere posizioni specifiche | Richiedere posizioni specifiche |
| | | |
|Account utente compromessi| Richiedi MFA | Richiedi MFA|
|Account utente compromessi | Bloccare gli utenti ad alto rischio | Bloccare gli utenti ad alto rischio |
|Account utente compromessi | PIN per i dispositivi | PIN per le app |
| | | |
| App o dispositivo compromesso | Richiedere un dispositivo conforme | Controllo jailbreak all'avvio dell'app |
| App o dispositivo compromesso | Crittografare i dati del dispositivo | Crittografa dati app |
| | | |
|Dispositivo perso o rubato | Rimuovere tutti i dati del dispositivo | Rimuovere tutti i dati delle app|
| | | |
| Condivisione accidentale dei dati o salvataggio dei dati in posizioni non protette | Limitare i backup dei dati del dispositivo | Limitare le operazioni Taglia/Copia/Incolla|
| Condivisione accidentale dei dati o salvataggio dei dati in posizioni non protette | Limitare le operazioni Salva con nome | Limitare le operazioni Salva con nome |
|Condivisione accidentale dei dati o salvataggio dei dati in posizioni non protette | Disabilita stampa | n/d|

## <a name="next-steps"></a>Passaggi successivi
A questo punto è necessario decidere se si intende abilitare BYOD nell'organizzazione con un'implementazione incentrata sulla gestione dei dispositivi, sulla gestione delle app o su una combinazione di questi due aspetti. La scelta del tipo di implementazione è libera, grazie alla possibilità di fare affidamento sulle funzionalità di identità e di sicurezza comunque disponibili in Azure AD.  

Usare la [Guida alla pianificazione](planning-guide.md) di Intune per definire il livello successivo della pianificazione.
