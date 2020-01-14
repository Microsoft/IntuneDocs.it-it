---
title: Configurare l'integrazione di Wandera Mobile Threat Protection con Intune
titleSuffix: Intune on Azure
description: Come configurare la soluzione Wandera Mobile Threat Protection con Microsoft Intune per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e565f40aac2a2b97f547a5b68a70a887d9e820ae
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207469"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integrare Wandera Mobile Threat Protection con Intune  

Seguire questa procedura per integrare la soluzione Wandera Mobile Threat Defense con Intune.  

> [!NOTE]
> Questo fornitore di Mobile Threat Defense non è supportato per i dispositivi non registrati.

## <a name="before-you-begin"></a>Prima di iniziare  

Prima di iniziare il processo di integrazione di Wandera con Intune, verificare che si siano soddisfatti i prerequisiti seguenti:
- Sottoscrizione di Microsoft Intune  
- Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:  
  - Accesso e lettura del profilo utente  
  - Accesso alla directory come utente connesso  
  - Lettura dati directory  
  - Invio di informazioni sul dispositivo a Intune  

- Sottoscrizione Wandera:
  - Uno o più account Wandera con licenza per EMM Connect  
  - Un account con privilegi di super amministratore in Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorizzazione per l'app Wandera Mobile Threat Defense  

Processo di autorizzazione per l'app Wandera Mobile Threat Defense:  
- Consentire al servizio Wandera Mobile Threat Defense di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.  
- Wandera esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.  
- Consentire al portale di amministrazione di Wandera RADAR di usare Azure AD Single Sign On (SSO).  
- Consentire all'app Wandera Mobile Threat Defense di eseguire l'accesso con Azure AD SSO.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Configurare l'integrazione di Wandera Mobile Threat Defense  
La configurazione di *EMM Connect* per Wandera richiede un processo di configurazione una tantum da eseguire sia nella console di Wandera che in quella di Intune. Il processo di configurazione richiede circa 15 minuti. È possibile completare la configurazione senza coordinarsi con l'account tecnico o il rappresentante del supporto tecnico di Wandera.  

### <a name="enable-support-for-wandera-in-intune"></a>Abilitare il supporto per Wandera in Intune

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Mobile Threat Defense** > **Aggiungi**.
3. Nella pagina **Aggiungi un connettore** selezionare **Wandera** nel menu a discesa. Selezionare quindi **Crea**.  
4. Nel riquadro Mobile Threat Defense, selezionare il connettore MTD **Wandera** nell'elenco dei connettori per aprire il riquadro *Modifica il connettore*. Selezionare **Apri la console dell'amministratore di Wandera MTD** per aprire [RADAR](https://radar.wandera.com/login), la console di amministrazione di Wandera e accedere. 
5. Nella console di Wandera passare a **Settings** > **EMM Integration** (Impostazioni, Integrazione EMM) e selezionare la scheda **EMM Connect**. Usare l'elenco a discesa *EMM Vendor* (Fornitore EMM) e selezionare *Microsoft Intune*.

   ![Selezionare Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

6. Selezionare **Grant permissions** (Concedi autorizzazioni) per aprire una connessione al portale di Intune. Accedere usando le credenziali di amministratore di Intune, selezionare la casella di controllo e quindi **Accetta** per accettare la richiesta di autorizzazioni.  

   ![Accettare le autorizzazioni](./media/wandera-mtd-connector-integration/permissions.png) 

7. Wandera completa la connessione e torna alla console di amministrazione RADAR. Ripetere il processo per **concedere** l'accesso per altre configurazioni, in base alle esigenze.  

   ![Integrazioni e autorizzazioni](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

8. Ancora nella console RADAR, copiare il nome del gruppo **SyncOnly** visualizzato sotto **EMM Label** (Etichetta EMM). Questo nome verrà usato per configurare un gruppo in Intune per la sincronizzazione con Wandera.

   ![Gruppo di sincronizzazione](./media/wandera-mtd-connector-integration/sync-group-name.png) 

9. Tornare alla console di [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e modificare il connettore MTD Wandera. **Attivare** gli interruttori disponibili e quindi **salvare** la configurazione.  

   ![Abilitare Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune e Wandera sono ora connessi.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configurare le applicazioni e il gruppo di sincronizzazione di Wandera  
Per distribuire Wandera verranno aggiunte le app per dispositivi mobili Wandera per le piattaforme usate (iOS e Android) in Intune e le app verranno poi assegnate a un gruppo specifico per la sincronizzazione: il gruppo *SyncOnly*. 

Le sezioni e le procedure seguenti descriveranno in modo guidato questo processo.

Per altre informazioni su questo processo da Wandera, accedere alla console [RADAR](https://radar.wandera.com/login) di Wandera. Passare a **Settings** > **EMM Integration** (Impostazioni, Integrazione EMM), selezionare la scheda **App Push** (Push app) e quindi selezionare **Microsoft Intune**. La scheda App Push (Push app) viene aggiornata con istruzioni specifiche per Intune.  

### <a name="add-the-wandera-apps"></a>Aggiungere le app Wandera  
Creare app client in Intune per distribuire l'app Wandera nei dispositivi Android e iOS. Vedere [Aggiungere app MTD](mtd-apps-ios-app-configuration-policy-add-assign.md) per le procedure e i dettagli personalizzati specifici per le app Wandera.  

Dopo aver creato le app tornare qui per creare il gruppo di sincronizzazione e assegnare le app.

### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Creare il gruppo di sincronizzazione e assegnare le app

1. Ottenere il nome del gruppo **SyncOnly** visualizzato in **EMM Label** (Etichetta EMM) dall'interno della console RADAR di Wandera. È possibile che questo nome sia stato salvato nel passaggio 7 durante l'[abilitazione del supporto per Wandera in Intune](#enable-support-for-wandera-in-intune). Usare questo nome come nome del gruppo in Intune per la sincronizzazione di Wandera.  

2. Nell'interfaccia di amministrazione di Endpoint Manager passare a **Gruppi** e selezionare **Nuovo gruppo**. Specificare le informazioni seguenti per configurare il gruppo di sincronizzazione per l'uso da Wandera:
   - **Tipo di gruppo**: **Security**
   - **Nome gruppo**: specificare il nome del gruppo **SyncOnly** recuperato dalla console di amministrazione RADAR di Wandera.

   ![configurare il gruppo di sincronizzazione](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Selezionare **Membri** e assegnare i gruppi che includono i dispositivi Android e iOS che si vuole usare con Wandera.

4. Selezionare **Crea** per salvare il gruppo.

Per altre informazioni, vedere [Distribuire le app](../apps/apps-deploy.md).

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Assegnare le app Wandera al gruppo di sincronizzazione  
Ripetere la procedura seguente per l'app Wandera creata per iOS e Android.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** e selezionare l'app Wandera.
3. Selezionare **Assegnazioni** e quindi **Aggiungi gruppo**.  
4. Nel riquadro **Aggiungi gruppo** selezionare *Obbligatorio* in *Tipo di assegnazione*.
5. Selezionare **Gruppi inclusi** e quindi **Selezionare i gruppi da includere**. Specificare il gruppo creato per la sincronizzazione di Wandera e quindi fare clic su **Seleziona** > **OK** > **OK**. Selezionare **Salva** per completare l'assegnazione del gruppo. 

## <a name="next-steps"></a>Passaggi successivi  
Ora che è stata configurata l'integrazione, è possibile iniziare a configurare i criteri, configurare l'accesso condizionale avanzato e visualizzare i report nella console di amministrazione di Wandera. Per altre informazioni sulla gestione e configurazione di Wandera, vedere la [guida introduttiva al centro di supporto](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) nella documentazione di Wandera. 
