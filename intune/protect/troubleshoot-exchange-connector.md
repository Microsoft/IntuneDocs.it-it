---
title: Risolvere i problemi di Exchange Connector
titleSuffix: Microsoft Intune
description: Risoluzione dei problemi correlati a Intune On-Premises Exchange Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508851"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Risolvere i problemi di Intune Exchange Connector

Questo argomento descrive come risolvere i problemi relativi a Intune Exchange Connector.

## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare la risoluzione dei problemi relativi a Exchange Connector in Intune, raccogliere alcune informazioni di base in modo da lavorare su solide fondamenta. Questo approccio può essere utile per comprendere meglio la natura del problema e risolverlo più rapidamente.

- Verificare che il processo soddisfi i requisiti di installazione. Vedere [Configurare Intune Exchange Connector locale](exchange-connector-install.md).
- Verificare che l'account disponga delle autorizzazioni di amministratore di Exchange e Intune.
- Si noti il testo del messaggio di errore completo e esatto, i dettagli e la posizione in cui viene visualizzato il messaggio.
- Determinare quando è stato avviato il problema: 
  - Si sta configurando il connettore per la prima volta? 
  - Il connettore funziona correttamente e quindi ha esito negativo?
  - Se funzionava, quali modifiche sono state apportate nell'ambiente di Intune, in ambiente Exchange o nel computer in cui è in esecuzione il software connettore?
- Che cos'è l'autorità MDM? Se è System Center Configuration Manager, quale versione di Configuration Manager si usa?
- Quale versione di Exchange si usa?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Usare PowerShell per ottenere più dati sui problemi relativi a Exchange Connector

- Per ottenere un elenco di tutti i dispositivi mobili per una cassetta postale, usare `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Per ottenere un elenco di indirizzi SMTP per una cassetta postale, utilizzare `Get-Mailbox -Identity user | select emailaddresses | fl`
- Per ottenere informazioni dettagliate sullo stato di accesso di un dispositivo, usare `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>Verificare la configurazione del connettore

Esaminare i [requisiti di Exchange Connector locali](exchange-connector-install.md#intune-exchange-connector-requirements) per assicurarsi che l'ambiente e il connettore siano configurati correttamente. 

### <a name="general-considerations-for-the-connector"></a>Considerazioni generali sul connettore

- Verificare che il firewall e i server proxy consentano la comunicazione tra il server che ospita Intune Exchange Connector e il servizio Intune.

- Il computer che ospita Intune Exchange Connector e il server Accesso client di Exchange (CAS) devono essere aggiunti a un dominio e nella stessa LAN. Assicurarsi che vengano aggiunte le autorizzazioni necessarie per l'account usato da Intune Exchange Connector.

- L'account di notifica viene usato per recuperare le impostazioni di *individuazione automatica* . Per altre informazioni su Autodisover in Exchange, vedere [servizio di individuazione automatica in Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- Intune Exchange Connector invia una richiesta all'URL di EWS usando le credenziali dell'account di notifica per inviare i messaggi di posta elettronica di notifica con il collegamento *Get Started* (per la registrazione in Intune). L'uso del collegamento *Get Started* per la registrazione è un requisito per i dispositivi Android non-Knox. In caso contrario, questi dispositivi verranno bloccati dall'accesso condizionale.

### <a name="common-issues-for-connector-configurations"></a>Problemi comuni per le configurazioni del connettore

- **Autorizzazioni dell'account**: nella finestra di dialogo di Microsoft Intune Exchange Connector assicurarsi di avere specificato un account utente con le autorizzazioni appropriate per eseguire i [cmdlet di Windows PowerShell Exchange richiesti](exchange-connector-install.md#exchange-cmdlet-requirements).
- **Messaggi di posta elettronica di notifica**: Abilita le notifiche e specifica un account di notifica.
- **Sincronizzazione del server Accesso client**: quando si configura Exchange Connector, specificare un CAS con la latenza di rete più bassa possibile per il server che ospita Exchange Connector. La latenza di comunicazione tra il server Accesso client ed Exchange Connector può determinare ritardi nell'individuazione dei dispositivi, specialmente quando si usa Exchange Online dedicato.
- **Pianificazione della sincronizzazione**: un utente con un dispositivo appena registrato potrebbe riscontrare ritardi e ottenere l'accesso solo dopo il completamento della sincronizzazione di Exchange Connector con il server Accesso client di Exchange. Una sincronizzazione completa viene eseguita una volta al giorno, mentre una sincronizzazione delta (rapida) viene eseguita più volte al giorno. È possibile [forzare manualmente una sincronizzazione rapida o una sincronizzazione completa](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) per ridurre al minimo i ritardi.

## <a name="next-steps"></a>Passaggi successivi
Gli articoli seguenti consentono di risolvere i problemi comuni e gli errori specifici:

- [Risolvere i problemi comuni per Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md).
- [Risolvere gli errori comuni per Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Richiedere assistenza dal supporto tecnico o dalla community di Intune:

- Vedere [ottenere supporto](../fundamentals/get-support.md) per usare la console di Intune per risolvere il problema o per aprire un caso di supporto con Microsoft. 
- Pubblicare il problema nei [forum Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
