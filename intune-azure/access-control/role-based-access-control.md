---
title: Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: Informazioni su come il Controllo degli accessi in base al ruolo consente di controllare chi può eseguire azioni e apportare modifiche."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: e60edd86289e0fca2aa03660d8ce782e373c0236
ms.lasthandoff: 03/15/2017


---

# <a name="intune-roles-rbac-for-microsoft-intune"></a>Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

In altre parole, i **ruoli** di Intune (Controllo degli accessi in base al ruolo) consentono di eseguire varie azioni su Intune e a chi si applicano queste azioni. È possibile usare i ruoli predefiniti che coprono alcuni scenari comuni in Intune oppure creare ruoli personalizzati.

Un ruolo è definito da:

- **Definizione**: il nome di un ruolo e le autorizzazioni che il ruolo configura.
- **Membri**: l'utente o il gruppo di utenti a cui verranno assegnate queste autorizzazioni.
- **Ambito**: gli utenti o i dispositivi in grado di gestire una specifica persona (membro).
- **Assegnazione**: il ruolo viene assegnato quando sono stati configurati la definizione, i membri e l'ambito.

## <a name="built-in-roles"></a>Ruoli predefiniti

I seguenti ruoli sono predefiniti in Intune ed è possibile personalizzarli o assegnarli ai gruppi senza ulteriore configurazione.

- **Amministratore di Intune**: dispone di autorizzazioni complete per tutte le operazioni in Intune.
- **Application Manager**: consente di gestire e distribuire applicazioni e profili.
- **Configuration Policy Manager**: consente di gestire e distribuire i profili e le impostazioni.
- **Operatore helpdesk**: consente di eseguire attività in remoto e visualizzare le informazioni su utenti e dispositivi.
- **Operatore sola lettura**: visualizza le informazioni nel portale di Intune senza la possibilità di apportare modifiche.


## <a name="custom-roles"></a>Ruoli personalizzati

Se nessuno dei ruoli predefiniti è adatto alle proprie esigenze, è possibile creare un ruolo personalizzato scegliendo impostazioni che includono molte funzionalità di Intune. È possibile esaminare un elenco di impostazioni disponibili più avanti in questo argomento.

### <a name="example"></a>Esempio

Si assume un amministratore IT che sarà responsabile della distribuzione e della gestione delle app agli utenti nella sede a Londra. Gli utenti sono inclusi in un gruppo di Azure Active Directory denominato **Londra**. Si vuole impedire all'amministratore IT di distribuire le app agli utenti in un altro ufficio. Eseguire le operazioni seguenti:

- Assegnare il ruolo **Application Manager** predefinito con le proprietà seguenti:
    - **Membri**: selezionare un gruppo che include l'amministratore IT responsabile della distribuzione delle app
    - **Ambito**: selezionare il gruppo **Londra** di Azure Active Directory.

    >[!IMPORTANT]
    >Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
    >- **Amministratore globale AAD**
    >- **Amministratore del servizio di Intune**

### <a name="how-to-create-a-custom-role"></a>Come creare un ruolo personalizzato

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Intune roles** (Ruoli di Intune).
![Carico di lavoro di Controllo dell'accesso](./media/axxess-control.png)
1. Nel pannello **Ruoli** del carico di lavoro di **Controllo dell'accesso** scegliere **Aggiungi personalizzato**.
2. Nel pannello **Aggiungi un ruolo personalizzato** immettere un nome e una descrizione per il nuovo ruolo e quindi fare clic su **Autorizzazioni**.
3. Nel pannello **Autorizzazioni** scegliere le autorizzazioni da usare con questo ruolo. È utile usare l'elenco di riferimento alle impostazioni di ruoli personalizzati più avanti in questo argomento.
4. Al termine, fare clic su **OK**.
5. Nel pannello **Aggiungi ruolo personalizzato** fare clic su **Crea**.

Il nuovo ruolo viene visualizzato nell'elenco del pannello **Ruoli**.

## <a name="how-to-assign-a-role"></a>Come assegnare un ruolo

1. Nel pannello **Ruoli** del carico di lavoro di **Controllo dell'accesso** scegliere il ruolo predefinito o personalizzato da assegnare.
2. Nel pannello <*Nome ruolo*>- **Proprietà** scegliere **Gestisci** > **Assegnazioni**.
    >[!TIP]
    >In questo pannello è anche possibile modificare o eliminare i ruoli esistenti.
3. Nel pannello successivo scegliere **Assegna**.
4. Nel pannello **Assegnazioni di ruolo** immettere un **nome** e una **descrizione** facoltativa per l'assegnazione e quindi scegliere le operazioni seguenti:
    - **Membri**: selezionare un gruppo contenente l'utente a cui si vuole assegnare le autorizzazioni.
    - **Ambito**: selezionare un gruppo contenente gli utenti che il membro indicato in precedenza è autorizzato a gestire.
5. Al termine, fare clic su **OK**.

La nuova assegnazione viene visualizzata nell'elenco di assegnazioni.

## <a name="custom-role-settings-reference"></a>Riferimento alle impostazioni di ruoli personalizzati

Quando si crea un ruolo personalizzato, è possibile configurare una o più delle impostazioni seguenti:

### <a name="device-configurations"></a>Configurazioni del dispositivo

|||
|-|-|
|**Assegna**|Assegnare i profili di dispositivo ai gruppi.|
|**Crea**|Creare i profili di dispositivo.|
|**Eliminazione**|Eliminare i profili di dispositivo.|
|**Leggi**|Leggere i profili di dispositivo e le relative proprietà.|
|**Aggiorna**|Aggiornare i profili di dispositivo esistenti.|

### <a name="managed-apps"></a>App gestite

|||
|-|-|
|**Assegna**|Assegnare le app gestite ai gruppi.|
|**Crea**|Aggiungere nuove app gestite in Intune.|
|**Eliminazione**|Eliminare le app gestite.|
|**Leggi**|Leggere le app gestite e le relative proprietà.|
|**Aggiorna**|Aggiornare le app gestite esistenti.|
|**Cancellazione**|Cancellare le app gestite dai dispositivi.|

### <a name="managed-devices"></a>Dispositivi gestiti

|||
|-|-|
|**Eliminazione**|Eliminare i dispositivi gestiti da Intune.|
|**Leggi**|Visualizzare informazioni sui dispositivi gestiti nel portale di Intune.|
|**Aggiorna**|Aggiornare le informazioni sui dispositivi gestiti.|

### <a name="mobile-apps"></a>App per dispositivi mobili

|||
|-|-|
|**Assegna**|Assegnare le app per dispositivi mobili ai gruppi.|
|**Crea**|Aggiungere nuove app per dispositivi mobili in Intune.|
|**Eliminazione**|Eliminare le app per dispositivi mobili.|
|**Leggi**|Leggere le app per dispositivi mobili e le relative proprietà.|
|**Aggiorna**|Aggiornare le app per dispositivi mobili.|

### <a name="organization"></a>Organizzazione

|||
|-|-|
|**Leggi**|Leggere le impostazioni relative ai tenant.|
|**Aggiorna**|Aggiornare le impostazioni relative ai tenant.|

### <a name="remote-tasks"></a>Attività remote

|||
|-|-|
|**Eseguire il bypass del blocco attivazione**|Rimuove il blocco attivazione dai dispositivi iOS senza richiedere Apple ID e password dell'utente. |
|**Disabilita la modalità di dispositivo perso**|Disabilitare la modalità di dispositivo perso. Questa modalità consente di specificare un messaggio e un numero di telefono che verranno visualizzati nella schermata di blocco del dispositivo.|
|**Abilita la modalità di dispositivo perso**|Abilitare la modalità di dispositivo perso. Questa modalità consente di specificare un messaggio e un numero di telefono che verranno visualizzati nella schermata di blocco del dispositivo.|
|**Individua il dispositivo**|-|
|**Riavvia il dispositivo**|Causa il riavvio del dispositivo.|
|**Blocco remoto**|Blocca un dispositivo. Per sbloccarlo, il proprietario del dispositivo deve usare il passcode.|
|**Reimposta passcode**|Genera un nuovo passcode per il dispositivo che verrà visualizzato nel pannello Panoramica di <device name>.|
|**Ritira**|Rimuove solo i dati aziendali gestiti da Intune. Non rimuove dal dispositivo i dati personali.|
|**Cancellazione**|Ripristina le impostazioni predefinite del dispositivo.|



### <a name="telecom-expenses"></a>Spese per telecomunicazioni

|||
|-|-|
|**Leggi**|Leggere le impostazioni del servizio di gestione delle spese per telecomunicazioni (TEM).|
|**Aggiorna**|Aggiornare le impostazioni del servizio di gestione delle spese per telecomunicazioni (TEM).|

### <a name="terms-and-conditions"></a>Termini e condizioni

|||
|-|-|
|**Assegna**|Assegnare i termini e le condizioni ai gruppi.|
|**Crea**|Creare le impostazioni relative ai termini e alle condizioni.|
|**Eliminazione**|Eliminare le impostazioni relative ai termini e alle condizioni.|
|**Leggi**|Leggere le impostazioni relative ai termini e alle condizioni nel portale di Intune.|
|**Aggiorna**|Aggiornare le impostazioni relative ai termini e alle condizioni.|
