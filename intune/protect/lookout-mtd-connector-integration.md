---
title: Configurare l'integrazione di Lookout con Microsoft Intune
titleSuffix: Microsoft Intune
description: Informazioni sull'integrazione di Intune con Lookout Mobile Endpoint Security come soluzione Mobile Threat Defense per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4661b151493eb68cc6f71a5a77bd023ac27b826
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810215"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Configurare l'integrazione di Lookout Mobile Endpoint Security con Intune
Con un ambiente che soddisfi i [prerequisiti](lookout-mobile-threat-defense-connector.md#prerequisites), è possibile integrare Lookout Mobile Endpoint Security con Intune. Le informazioni contenute in questo articolo illustrano nel dettaglio come predisporre l'integrazione e configurare impostazioni importanti in Lookout per l'uso con Intune.  

> [!IMPORTANT]
> Un tenant esistente di Lookout Mobile Endpoint Security non ancora associato al tenant di Azure AD non può essere usato per l'integrazione con Azure AD e Intune. Contattare il supporto di Lookout per creare un nuovo tenant di Lookout Mobile Endpoint Security. Usare il nuovo tenant per caricare gli utenti di Azure AD.

## <a name="collect-azure-ad-information"></a>Raccogliere le informazioni di Azure AD  
Per integrare Lookout con Intune occorre associare il tenant di Lookout Mobility Endpoint Security alla sottoscrizione di Azure Active Directory (AD).

Per abilitare la sottoscrizione di Lookout Mobile Endpoint Security con Intune, è necessario fornire le informazioni seguenti al servizio di supporto di Lookout (enterprisesupport@lookout.com):  

- **ID directory del tenant di Azure AD**  

- **ID oggetto di gruppo di Azure AD** per il gruppo con accesso **completo** alla console di Lookout Mobile Endpoint Security (MES).  
  Occorre creare questo gruppo di utenti in Azure AD per contenere gli utenti che hanno *accesso completo* alla **console di Lookout**. Gli utenti devono essere membri di questo gruppo o del gruppo facoltativo con *accesso con restrizioni* per poter accedere alla console di Lookout. 

- **ID oggetto di gruppo di Azure AD** per il gruppo con accesso **con restrizioni** alla console di Lookout MES *(gruppo facoltativo)* . 
  Occorre creare questo gruppo di utenti in Azure AD per contenere gli utenti che non devono avere accesso a diversi moduli di configurazione e registrazione della console di Lookout. Questi utenti hanno invece accesso in sola lettura al modulo **Criteri di sicurezza** della console di Lookout. Gli utenti devono essere membri di questo gruppo facoltativo o del gruppo obbligatorio con *accesso completo* per poter accedere alla console di Lookout.

 > [!TIP] 
 > Per altri dettagli sulle autorizzazioni, leggere [questo articolo](https://personal.support.lookout.com/hc/articles/114094105653) nel sito Web di Lookout.

### <a name="collect-information-from-azure-ad"></a>Raccogliere informazioni da Azure AD 

1. Accedere al [portale di Azure](https://portal.azure.com) con un account di amministratore globale.

2. Passare ad **Azure Active Directory** > **Proprietà** e individuare il proprio **ID directory**. Usare il pulsante *Copia* per copiare l'ID directory e quindi salvarlo in un file di testo.

   ![Proprietà di Azure AD](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Trovare quindi l'ID di gruppo di Azure AD per gli account usati per concedere agli utenti di Azure AD l'accesso alla console di Lookout. Il primo gruppo è per l'*accesso completo*, mentre il secondo è per l'*accesso con restrizioni* ed è facoltativo. Per ottenere l'*ID oggetto*, per ogni account:  
   1. Passare ad **Azure Active Directory** > **Gruppi** per aprire il riquadro *Gruppi - Tutti i gruppi*.  

   2. Selezionare il gruppo creato per l'*accesso completo* per aprire il relativo riquadro *Panoramica*.  

   3. Usare il pulsante *Copia* per copiare l'ID oggetto e quindi salvarlo in un file di testo.  

   4. Ripetere la procedura per il gruppo con *accesso con restrizioni*, se usato.  

      ![ID oggetto di gruppo di Azure AD](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Dopo aver raccolto queste informazioni, contattare il supporto di Lookout all'indirizzo di posta elettronica enterprisesupport@lookout.com. Il servizio di supporto tecnico di Lookout collaborerà con il contatto principale dell'utente per eseguire l'onboarding della sottoscrizione e per creare l'account aziendale per Lookout, usando le informazioni fornite.  

## <a name="configure-your-lookout-subscription"></a>Configurare la sottoscrizione di Lookout  

I passaggi seguenti vengono eseguiti nella console di amministrazione di Lookout Enterprise e consentiranno una connessione al servizio Lookout per i dispositivi registrati di Intune (tramite la conformità del dispositivo) **e** i dispositivi non registrati (tramite i criteri di protezione delle app).

Dopo aver creato l'account aziendale per Lookout, il servizio di supporto tecnico di Lookout invia un messaggio di posta elettronica al contatto principale dell'azienda con un collegamento all'URL di accesso: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Accesso iniziale  
Al primo accesso alla console di Lookout MES viene visualizzata una pagina di consenso (https://aad.lookout.com/les?action=consent) ). Se si è amministratori globali di Azure AD, accedere e selezionare **Accept** (Accetto). Per gli accessi successivi non è necessario che l'utente abbia questo livello di privilegi per Azure AD. 

 Viene visualizzata una pagina per richiedere il consenso. Scegliere **Accept** (Accetto) per completare la registrazione. 
   ![Screenshot della pagina di primo accesso della console di Lookout](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Dopo aver accettato e fornito il consenso, si viene reindirizzati alla console di Lookout.

Completata la fase di accesso iniziale e consenso, gli utenti che accedono da https://aad.lookout.com vengono reindirizzati alla console MES. Se il consenso non è stato ancora concesso, tutti i tentativi di accesso generano un errore di accesso non valido.

### <a name="configure-the-intune-connector"></a>Configurare Intune Connector  
La procedura seguente presuppone che sia stato precedentemente creato un gruppo di utenti in Azure AD per testare la distribuzione di Lookout. È consigliabile iniziare con un piccolo gruppo di utenti per consentire agli amministratori di Lookout e Intune di familiarizzare con le integrazioni dei prodotti. Sarà poi possibile estendere la registrazione ad altri gruppi di utenti.

1. Accedere alla [console di Lookout MES](https://aad.lookout.com) e passare a **System** (Sistema) > **Connectors** (Connettori), quindi selezionare **Add Connector** (Aggiungi connettore).  Selezionare **Intune**.

   ![Immagine della console di Lookout con l'opzione Intune nella scheda dei connettori](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. Nel riquadro *Microsoft Intune* selezionare **Connection Settings** (Impostazioni di connessione) e quindi in **Heartbeat Frequency** specificare la frequenza di heartbeat in minuti. 

   ![Immagine della scheda delle impostazioni di connessione con la frequenza di heartbeat configurata](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Selezionare **Enrollment Management** (Gestione registrazione), quindi in **Use the following Azure AD security groups to identify devices that should be enrolled in Lookout for Work** (Usa i gruppi di sicurezza di Azure AD seguenti per identificare i dispositivi da registrare in Lookout for Work) specificare il *nome gruppo* di un gruppo di Azure AD da usare con Lookout, quindi selezionare **Save changes** (Salva modifiche).

    ![screenshot della pagina di registrazione di Intune Connector](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Informazioni sui gruppi usati**:
   - È consigliabile iniziare con un gruppo di sicurezza Azure AD contenente un numero limitato di utenti per testare l'integrazione di Lookout.
   - Per il **nome del gruppo** viene fatta distinzione tra maiuscole e minuscole, come indicato nella pagina **Proprietà** del gruppo di sicurezza nel portale di Azure.  
   - I gruppi specificati per **Enrollment Management** (Gestione registrazione) definiscono il gruppo di utenti i cui dispositivi verranno registrati con Lookout. Quando un utente è in un gruppo di registrazione, i suoi dispositivi in Azure AD vengono registrati e sono idonei per l'attivazione in Lookout MES. La prima volta che un utente apre l'applicazione *Lookout for Work* in un dispositivo supportato, gli viene chiesto di attivarla.

4. Selezionare **State Sync** (Sincronizzazione stato) e verificare che sia *device status* (stato dispositivo) che *threat status* (stato minacce) siano impostati su **On** (Attivato).  Entrambi gli stati sono necessari per il corretto funzionamento dell'integrazione di Lookout e Intune.  

5. Selezionare **Error Management** (Gestione errori), specificare l'indirizzo di posta elettronica a cui inviare i report sugli errori e quindi selezionare **Save changes** (Salva modifiche).
 
   ![screenshot della pagina di gestione degli errori di Intune Connector](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Selezionare **Create connector** (Crea connettore) per completare la configurazione del connettore. Quando si è soddisfatti dei risultati, è possibile estendere la registrazione ad altri gruppi di utenti.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Configurare Intune per usare Lookout come provider di Mobile Threat Defense
Dopo aver configurato Lookout MES, è necessario impostare una connessione a [Lookout in Intune](https://docs.microsoft.com/en-us/intune/protect/mtd-connector-enable).  

## <a name="additional-settings-in-the-lookout-mes-console"></a>Impostazioni aggiuntive nella console di Lookout MES
Di seguito sono illustrate alcune impostazioni aggiuntive che possono essere configurate nella console di Lookout MES.  

### <a name="configure-enrollment-settings"></a>Configurare le impostazioni di registrazione
Nella console di Lookout MES selezionare **System** (Sistema) > **Manage Enrollment** (Gestisci registrazione) > **Enrollment settings** (Impostazioni di registrazione).  

- In **Disconnected Status** (Stato disconnesso) specificare il numero di giorni che deve trascorrere prima che un dispositivo non connesso venga contrassegnato come disconnesso.  

  I dispositivi disconnessi sono considerati non conformi. L'accesso alle applicazioni aziendali tramite questi dispositivi in base ai criteri di accesso condizionale di Intune è bloccato. È possibile specificare un valore compreso tra 1 e 90 giorni.

  ![Impostazioni di registrazione di Lookout per il modulo di sistema](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Configurare le notifiche tramite posta elettronica
Per ricevere avvisi relativi alle minacce tramite posta elettronica, accedere alla [console di Lookout MES](https://aad.lookout.com) con l'account utente che deve ricevere le notifiche.  

- Passare a **Preferences** (Preferenze), impostare le notifiche che si vuole ricevere su **ON** (Attivato) e quindi scegliere **Save** (Salva) per salvare le modifiche.  

- Se non si vogliono più ricevere notifiche tramite posta elettronica, impostare le notifiche su **OFF** (Disattivato) e salvare le modifiche.

  ![Screenshot della pagina delle preferenze con l'account utente visualizzato](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)

## <a name="configure-threat-classifications"></a>Configurare la classificazione delle minacce  
Lookout Mobile Endpoint Security usa vari tipi di classificazione per le minacce ai dispositivi mobili. Alle classificazioni delle minacce di Lookout sono associati livelli di rischio predefiniti. I livelli di rischio possono essere modificati in qualsiasi momento per adattarli ai requisiti aziendali.

Per informazioni sulle classificazioni dei livelli di minaccia e su come gestire i livelli di rischio associati, vedere le [informazioni di riferimento sulle minacce di Lookout](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> I livelli di rischio rappresentano un aspetto importante di Mobile Endpoint Security perché l'integrazione con Intune calcola la conformità dei dispositivi in base a questi livelli di rischio in fase di esecuzione.  
> 
> In altre parole, l'amministratore di Intune imposta una regola nei criteri per identificare un dispositivo come non conforme se presenta una minaccia attiva con un livello minimo di rischio: **alto**, **medio** o **basso**. Il calcolo della conformità dei dispositivi in Intune dipende direttamente dai criteri di classificazione delle minacce in Lookout Mobile Endpoint Security.  

## <a name="monitor-enrollment"></a>Monitorare la registrazione
Al termine della configurazione, Lookout Mobile Endpoint Security inizia a eseguire il polling di Azure AD per individuare i dispositivi corrispondenti ai gruppi di registrazione specificati.  È possibile trovare informazioni sui dispositivi registrati passando a **Devices** (Dispositivi) nella console di Lookout MES.  
- Lo stato iniziale dei dispositivi è *pending* (in sospeso).  
- Lo stato del dispositivo viene aggiornato dopo l'installazione, l'apertura e l'attivazione nel dispositivo dell'app *Lookout for Work*.

Per informazioni dettagliate su come distribuire l'app *Lookout for Work* nel dispositivo, vedere [Aggiungere e assegnare app Mobile Threat Defense (MTD) con Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Passaggi successivi

- [Configurare app Lookout per i dispositivi registrati](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Configurare app Lookout per i dispositivi non registrati](~/protect/mtd-add-apps-unenrolled-devices.md)
