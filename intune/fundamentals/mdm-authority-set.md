---
title: Impostare l'autorità di gestione dei dispositivi mobili
titleSuffix: Microsoft Intune
description: Impostare l'autorità di gestione dei dispositivi mobili in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b611b2307b7b4f7e789e7db9d070e4b6b3f1350c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514490"
---
# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#set-mdm-authority-to-intune).

- **Co-gestione di Intune**: integrazione della soluzione cloud di Intune con Configuration Manager per dispositivi Windows 10. Intune viene configurato tramite la console di Configuration Manager. [Configurare la registrazione automatica dei dispositivi in Intune](https://docs.microsoft.com/configmgr/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Microsoft 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Microsoft 365.

- **Coesistenza di Office 365 MDM** È possibile attivare e usare sia MDM per Office 365 che Intune simultaneamente nel tenant e impostare l'autorità di gestione su Intune o MDM per Office 365 per ogni utente per determinare quale servizio verrà usato per gestire i dispositivi mobili. L'autorità di gestione dell'utente è definita in base alla licenza assegnata all'utente. Per altre informazioni, vedere [ Coesistenza di Microsoft Intune con MDM per Office 365](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

Se l'autorità MDM non è stata ancora impostata, seguire questa procedura.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare l'intestazione arancione per aprire l’impostazione **Autorità di gestione dei dispositivi mobili**. L'intestazione arancione viene visualizzata solo se l'autorità MDM non è stata ancora impostata.
2. In **Autorità di gestione dei dispositivi mobili** scegliere una delle opzioni seguenti per l'autorità MDM:
   - **Autorità MDM Intune**
   - **Nessuno**

   ![Immagine della schermata di impostazione dell’autorità di gestione dei dispositivi mobili di Intune](./media/mdm-authority-set/set-mdm-auth.png)

   Un messaggio indica che l'autorità MDM è stata impostata su Intune.

### <a name="workflow-of-intune-administration-ui"></a>Flusso di lavoro dell'interfaccia utente di amministrazione di Intune
Quando è abilitata la gestione dei dispositivi Android o Apple, Intune invia informazioni sul dispositivo e sull'utente da integrare con i servizi di terze parti per la gestione dei rispettivi dispositivi.

Gli scenari con il consenso alla condivisione dei dati vengono inclusi se:
- Si abilitano i profili di lavoro Android.
- Si abilitano e caricano i certificati per le notifiche push MDM Apple.
- Si abilita uno dei servizi Apple, ad esempio Device Enrollment Program, School Manager o Volume Purchasing Program.

In ogni caso, il consenso è strettamente correlato all'esecuzione di un servizio di gestione dei dispositivi mobili. Ad esempio, verificare che l'amministratore IT abbia autorizzato la registrazione di dispositivi Google o Apple. La documentazione da consultare per sapere quali informazioni vengono condivise quando vengono pubblicati i nuovi flussi di lavoro è disponibile nelle posizioni seguenti:
- [Dati inviati da Intune a Google](https://aka.ms/Data-intune-sends-to-google)
- [Dati inviati da Intune ad Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Considerazioni principali
Dopo il passaggio alla nuova autorità MDM, è probabile che vi sia un tempo di transizione (fino a otto ore) prima dell'archiviazione del dispositivo e della sua sincronizzazione con il servizio. È necessario configurare le impostazioni nella nuova autorità MDM per garantire che i dispositivi registrati continuino a essere gestiti e protetti dopo la modifica. 
- I dispositivi devono connettersi con il servizio dopo la modifica, in modo che le impostazioni dalla nuova autorità MDM (versione autonoma di Intune) sostituiscano le impostazioni esistenti nel dispositivo.
- Dopo aver cambiato l'autorità MDM, alcune impostazioni di base dell'autorità MDM precedente, come ad esempio i profili, rimarranno nel dispositivo per un massimo di sette giorni o fino a quando il dispositivo stesso non si connetterà al servizio per la prima volta. È consigliabile configurare le app e le impostazioni (criteri, profili, app e così via) nella nuova autorità MDM appena possibile e distribuire le impostazioni ai gruppi di utenti in cui sono presenti utenti che hanno già dispositivi registrati. Non appena un dispositivo si connette al servizio dopo che l'autorità MDM è stata cambiata, riceve le nuove impostazioni dall'autorità MDM impedendo che vi siano vuoti nella gestione e protezione.
- Per i dispositivi senza utenti associati (generalmente con il Device Enrollment Program per dispositivi iOS/iPadOS o con scenari di registrazione in blocco) non viene eseguita la migrazione alla nuova autorità MDM. Per tali dispositivi è necessario chiamare il supporto tecnico per chiedere assistenza nel passaggio alla nuova autorità MDM.

## <a name="change-mdm-authority-to-office-365"></a>Cambiare l'autorità MDM in Office 365

Per attivare la gestione dei dispositivi mobili di Office 365 (o per abilitare la coesistenza di MDM nel servizio Intune Service esistente), passare a [https://protection.office.com](https://protection.office.com), scegliere **Prevenzione della perdita di dati** > **Criteri di sicurezza dei dispositivi** > **Visualizza l'elenco dei dispositivi gestiti** > **Inizia**.

Per altre informazioni, vedere [Configurare Gestione di dispositivi mobili in Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Se si vuole che gli utenti finali siano gestiti solo con Office 365 MDM, rimuovere qualsiasi licenza di Intune e/o EMS assegnata dopo l'attivazione di Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non verrà rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.

## <a name="remove-mdm-authority"></a>Rimuovere l'autorità MDM

Non è possibile reimpostare l'autorità MDM su Sconosciuto. L'autorità MDM è usata dal servizio per determinare il portale di registrazione a cui fanno riferimento i dispositivi (Microsoft Intune o Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Conseguenze della modifica dell'autorità MDM

- Quando il servizio Intune rileva che l'autorità MDM di un tenant è cambiata, invia un messaggio di notifica a tutti i dispositivi registrati perché eseguano l'archiviazione e la sincronizzazione con il servizio (questa notifica è al di fuori delle normali archiviazioni pianificate). Di conseguenza, dopo la modifica dell'autorità MDM per il tenant da Intune autonomo, tutti i dispositivi accesi e online si connetteranno al servizio, riceveranno la nuova autorità MDM e da quel momento saranno gestiti dall'autorità MDM. Non ci sono interruzioni per la gestione e protezione di questi dispositivi.
- Anche se i dispositivi sono accesi e online durante (o immediatamente dopo) la modifica nell'autorità MDM, ci sarà un ritardo massimo di otto ore (a seconda del momento della successiva archiviazione periodica pianificata) prima che i dispositivi siano registrati per il servizio con la nuova autorità MDM.    

  > [!IMPORTANT]    
  > Tra il momento in cui si cambia l'autorità MDM e quello in cui viene caricato il certificato rinnovato del servizio APN per la nuova autorità, le nuove registrazioni e le nuove sincronizzazioni di dispositivi iOS/iPadOS hanno esito negativo. Pertanto è importante analizzare e caricare il certificato APN per la nuova autorità al più presto dopo la modifica nell'autorità MDM.

- Gli utenti possono passare rapidamente alla nuova autorità MDM avviando manualmente un'archiviazione dal dispositivo al servizio. Gli utenti possono eseguire facilmente questa modifica usando l'app Portale aziendale e avviando un controllo di conformità del dispositivo.
- Per verificare che tutto funzioni correttamente dopo che i dispositivi sono stati archiviati e sincronizzati con il servizio dopo la modifica dell'autorità MDM, cercare i dispositivi nella nuova autorità MDM.
- Quando un dispositivo è offline durante la modifica nell'autorità MDM e quando il dispositivo viene archiviato nel servizio si ha una situazione intermedia. Per garantire che il dispositivo rimanga protetto e funzionale durante questo periodo, i profili seguenti rimangono nel dispositivo per un massimo di sette giorni o fino a quando il dispositivo non si connette con la nuova autorità MDM e riceve le nuove impostazioni che sovrascrivono quelle esistenti:
  - Profilo di posta elettronica
  - Profilo VPN
  - Profilo certificato
  - Profilo Wi-Fi
  - Profili di configurazione
- Dopo il passaggio alla nuova autorità MDM, i dati di conformità nella console di amministrazione di Microsoft Intune possono richiedere fino a una settimana per un reporting preciso. Tuttavia, gli stati di conformità in Azure Active Directory e nel dispositivo sono accurati. Il dispositivo, quindi, è comunque protetto.
- Verificare che le nuove impostazioni che devono sovrascrivere quelle esistenti abbiano lo stesso nome delle precedenti per garantire che le impostazioni precedenti vengano sovrascritte. In caso contrario, i dispositivi potrebbero finire con criteri e profili ridondanti.    

  > [!TIP]    
  > Come procedura consigliata è necessario creare tutte le impostazioni di gestione e le configurazioni, nonché le distribuzioni, subito dopo aver completato la modifica dell'autorità MDM. Questo contribuisce a garantire la protezione e la gestione attiva dei dispositivi durante il periodo intermedio.

- Dopo aver modificato l'autorità MDM, eseguire la procedura seguente per verificare che i nuovi dispositivi siano registrati correttamente con la nuova autorità:   
  - Registrare un nuovo dispositivo
  - Assicurarsi che il dispositivo appena registrato sia visualizzato nell'autorità MDM.
  - Eseguire un'azione, ad esempio il blocco remoto, dalla console di amministrazione al dispositivo. Se l'azione ha esito positivo, il dispositivo è gestito dalla nuova autorità MDM.
- Nel caso di problemi con dispositivi specifici, è possibile annullare e ripetere la registrazione dei dispositivi in modo che siano connessi alla nuova autorità e gestiti il più rapidamente possibile.

## <a name="next-steps"></a>Passaggi successivi

Con il set di autorità MDM, è possibile iniziare la [registrazione dei dispositivi](../enrollment/device-enrollment.md).
