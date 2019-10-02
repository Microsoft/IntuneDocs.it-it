---
title: Usare Intune per risolvere le vulnerabilità rilevate da Microsoft Defender ATP - Azure | Microsoft Docs
description: Informazioni su come gestire le attività di sicurezza da Threat & Vulnerability Management, un componente di Microsoft Defender Advanced Threat Protection (ATP) disponibile dalla console di Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69f214b4fd3f3b7767e719c0f68f19e178a8e29c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723008"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Usare Intune per risolvere le vulnerabilità identificate da Microsoft Defender ATP  

Quando si integra Intune con Microsoft Defender Advanced Threat Protection (ATP), è possibile sfruttare i vantaggi di Threat & Vulnerability Management (TVM) di ATP e usare Intune per risolvere le vulnerabilità dell'endpoint identificate da TVM. Questa integrazione aggiunge un approccio basato sui rischi per l'individuazione e la classificazione delle vulnerabilità che consente di migliorare il tempo di risposta per la loro risoluzione nell'ambiente in uso.  

[Threat & Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) fa parte di [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).  

## <a name="how-integration-works"></a>Funzionamento dell'integrazione  

Dopo aver connesso Intune a Microsoft Defender Advanced Threat Protection, ATP riceve i dettagli delle minacce e delle vulnerabilità dai dispositivi gestiti.  

Nella console di Microsoft Defender Security Center gli amministratori della sicurezza ATP esaminano i dati sulle vulnerabilità dell'endpoint. Con un solo clic del mouse gli amministratori creano quindi attività di sicurezza che contrassegnano i dispositivi vulnerabili per la correzione. Le attività di sicurezza vengono passate immediatamente alla console di Intune dove gli amministratori di Intune possono visualizzarle. L'attività di sicurezza identifica il tipo di vulnerabilità, la priorità, lo stato e i passaggi da eseguire per risolvere la vulnerabilità. L'amministratore di Intune sceglie se accettare o rifiutare l'attività.  

Quando un'attività viene accettata, l'amministratore di Intune cerca di risolvere la vulnerabilità tramite Intune, facendo riferimento alle indicazioni fornite nell'ambito dell'attività di sicurezza.  

Le azioni comuni per la correzione includono:  

- **Blocco** dell'esecuzione di un'applicazione  
- **Distribuzione** di un aggiornamento del sistema operativo per ridurre la vulnerabilità.  
- **Modifica** di un valore del Registro di sistema.  
- **Disabilitazione** o **abilitazione** di una configurazione per influire sulla vulnerabilità.  
- **Richiesta di attenzione** per avvisare l'amministratore della minaccia quando non ci sono raccomandazioni appropriate da fornire.  

Ecco un flusso di lavoro di esempio:

- All'interno di Microsoft Defender ATP, viene rilevata una vulnerabilità per un'app denominata Contoso Media Player v4 e un amministratore crea un'attività di sicurezza per aggiornare l'app. Il lettore Contoso Media Player è un'app non gestita che è stata distribuita con Intune.  

  Questa attività di sicurezza viene visualizzata nella console di Intune con stato In sospeso:  
  ![Visualizzare l'elenco delle attività di sicurezza nella console di Intune](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- L'amministratore di Intune seleziona l'attività di sicurezza per visualizzare i dettagli relativi all'attività.  L'amministratore seleziona quindi **Accetta**, che aggiorna lo stato in Intune e in ATP in *Accettato*.  
  ![Accettare o rifiutare un'attività di sicurezza](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- L'amministratore risolve quindi la vulnerabilità basandosi sulle indicazioni fornite.  Le indicazioni variano a seconda del tipo di correzione richiesta. Quando sono disponibili, le indicazioni per la correzione includono collegamenti che aprono riquadri pertinenti per le configurazioni in Intune. 

  Poiché il lettore multimediale in questo esempio non è un'app gestita, Intune può fornire solo istruzioni di testo. Se l'app è gestita, Intune potrebbe fornire istruzioni per scaricare una versione aggiornata e un collegamento per aprire la distribuzione per l'app, in modo che i file aggiornati possano essere aggiunti alla distribuzione. 

- Al termine della correzione, l'amministratore di Intune apre l'attività di sicurezza e seleziona **Completa attività**.  Lo stato di correzione viene aggiornato per Intune e in ATP, dove gli amministratori della sicurezza confermano lo stato rivisto per la vulnerabilità.  

## <a name="prerequisites"></a>Prerequisiti  

**Sottoscrizioni**:  

- Microsoft Intune  
- Microsoft Defender Advanced Threat Protection ([registrarsi per una versione di prova gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink))  

**Configurazioni di Intune per ATP**:  

- Configurare una connessione da servizio a servizio con Microsoft Defender ATP.  
- Distribuire un criterio di conformità del dispositivo con un tipo di profilo **Microsoft Defender ATP (Windows 10 Desktop)** per i dispositivi per cui ATP ha valutato la presenza di un rischio.

  Per informazioni su come configurare Intune per usare ATP, vedere [Applicare la conformità per Microsoft Defender ATP con l'accesso condizionale in Intune](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune).  

## <a name="work-with-security-tasks"></a>Gestire le attività di sicurezza  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a **Sicurezza dei dispositivi** > **Attività di sicurezza**.  
2. Selezionare un'attività dall'elenco per aprire una finestra di risorse che visualizza dettagli aggiuntivi per l'attività di sicurezza.  
3. Mentre si visualizza la finestra di risorse dell'attività di sicurezza, è possibile selezionare altri collegamenti:  
   - APP GESTITE: visualizzare l'app vulnerabile. Quando la vulnerabilità si applica a più app, si vedrà un elenco di app filtrato.  
   - DISPOSITIVI: visualizzare un elenco dei *dispositivi vulnerabili*, da cui è possibile collegarsi a una voce con maggiori dettagli per la vulnerabilità in tale dispositivo.  
   - RICHIEDENTE: usare il collegamento per inviare un messaggio e-mail all'amministratore che ha inviato l'attività di sicurezza.  
   - NOTE: leggere i messaggi personalizzati inviati dal richiedente all'apertura dell'attività di sicurezza.  
4. Selezionare **Accetta** o **Rifiuta** per inviare notifiche ad ATP per l'azione pianificata. Quando si accetta o si rifiuta un'attività, è possibile inoltrare note, che vengono inviate ad ATP.  

5. Dopo aver accettato un'attività, riaprire l'attività di sicurezza (se chiusa) e seguire i dettagli della correzione per risolvere la vulnerabilità.  Le istruzioni fornite da ATP nei dettagli dell'attività di sicurezza variano a seconda della vulnerabilità interessata.  

   Quando è possibile, le istruzioni di correzione includono collegamenti che aprono gli oggetti di configurazione pertinenti nella console di Intune.  

6. Dopo aver completato la procedura di correzione, aprire l'attività di sicurezza e selezionare **Completa attività**.  Questa azione aggiorna lo stato dell'attività di sicurezza in Intune e in ATP.  

Dopo che la correzione ha esito positivo, il punteggio di esposizione al rischio in ATP può calare, in base alle nuove informazioni provenienti dai dispositivi sottoposti a correzione. 

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni su Intune e [Microsoft Defender ATP](advanced-threat-protection.md)  
Rivedere [Mobile Threat Defense](mobile-threat-defense.md) di Intune  
Rivedere il [dashboard di Threat & Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) in Microsoft Defender ATP
