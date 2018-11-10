---
title: Configurare la registrazione di Intune per i dispositivi aggiunti ad Active Directory ibrido usando Windows Autopilot
titleSuffix: Microsoft Intune
description: Usare Windows Autopilot per registrare i dispositivi aggiunti ad Active Directory ibrido in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 120478644743619dbcfc5e8e36806a1109924331
ms.sourcegitcommit: 222881461a81a93b3843c2ac86a7c24a180158d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2018
ms.locfileid: "50972775"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Distribuire dispositivi aggiunti ad Azure AD ibrido usando Intune e Windows Autopilot (anteprima)
È possibile usare Intune e Windows Autopilot per configurare i dispositivi aggiunti ad Active Directory ibrido. A tale scopo, eseguire i passaggi seguenti.

> [!NOTE]
> Questa funzionalità verrà implementata nella base di utenti nei prossimi giorni. Di conseguenza, sarà possibile seguire questa procedura solo dopo l'implementazione nel proprio account.

## <a name="prerequisites"></a>Prerequisiti

- Configurare i [dispositivi aggiunti ad Azure Active Directory ibrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains).
    - Assicurarsi di [verificare la registrazione usando il cmdlet Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

I dispositivi da registrare devono anche:
- Eseguire Windows 10 con l'[aggiornamento di ottobre 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Avere accesso a Internet.
- Avere accesso ad Active Directory (la connessione VPN non è supportata).
- Eseguire la Configurazione guidata.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurare la registrazione automatica di Windows 10

1. Accedere al [portale di Azure](https://portal.azure.com) e selezionare **Azure Active Directory**.

   ![Schermata del portale di Azure](./media/auto-enroll-azure-main.png)

2. Selezionare **Servizi Mobility (MDM e MAM)**.

   ![Schermata del portale di Azure](./media/auto-enroll-mdm.png)

3. Selezionare **Microsoft Intune**.

   ![Schermata del portale di Azure](./media/auto-enroll-intune.png)

4. Assicurarsi che gli utenti che distribuiscono dispositivi aggiunti ad Azure Active Directory con Intune e Windows siano membri di un gruppo incluso nell'**ambito utente MDM**.

   ![Schermata del portale di Azure](./media/auto-enroll-scope.png)

5. Usare i valori predefiniti per gli URL seguenti:
    - **URL delle condizioni per l'uso di MDM**
    - **URL individuazione MDM**
    - **URL conformità MDM**
6. Scegliere **Salva**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentare il limite di account computer nell'unità organizzativa

Intune Connector per Active Directory crea computer di registrazione Autopilot nel dominio Active Directory locale. Il computer che ospita Intune Connector deve avere l'autorizzazione per la creazione di oggetti computer all'interno del dominio. 

In alcuni domini ai computer non viene assegnata l'autorizzazione per la creazione di computer. Oppure gli amministratori non vogliono aumentare il limite di account computer a livello di dominio. In questi casi, le autorizzazioni possono essere delegate all'unità organizzativa in cui vengono creati i dispositivi aggiunti ad Azure AD ibrido.

L'unità organizzativa a cui viene assegnata l'autorizzazione per la creazione di computer deve corrispondere a:
- l'unità organizzativa specificata nel profilo di aggiunta al dominio
- oppure, se non è selezionato alcun profilo, al nome di dominio del computer per il dominio.

1. Aprire **Utenti e computer di Active Directory** (DSA.msc).

2. Fare clic con il pulsante destro del mouse sull'unità organizzativa che verrà usata per creare i computer aggiunti ad Azure AD ibrido > **Delega controllo**.

    ![Schermata di delega del controllo](media/windows-autopilot-hybrid/delegate-control.png)

3. Nella procedura guidata **Delegation of Control** (Delega del controllo) scegliere **Avanti** > **Aggiungi...** > **Tipi di oggetto**.

4. Nella finestra di dialogo **Tipi di oggetto** selezionare **Computer** e quindi scegliere **OK**.

    ![Schermata di delega del controllo](media/windows-autopilot-hybrid/object-types-computers.png)

5. Nella finestra di dialogo **Seleziona utenti, computer o gruppi** nella casella **Immettere i nomi degli oggetti da selezionare** immettere il nome del computer in cui è installato Connector.

    ![Schermata di delega del controllo](media/windows-autopilot-hybrid/enter-object-names.png)

6. Scegliere **Controlla nomi** per controllare il valore immesso, quindi scegliere **OK** > **Avanti**.

7. Scegliere **Create a custom task to delegate** (Crea un'attività personalizzata da delegare)  > **Avanti**.

8. Scegliere **Only the following objects in the folder** (Solo gli oggetti seguenti nella cartella) e quindi selezionare le opzioni seguenti:
    - **Oggetti computer**
    - **Crea gli oggetti selezionati in questa cartella**
    - **Elimina gli oggetti selezionati in questa cartella**

    ![Schermata di delega del controllo](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Scegliere **Avanti**.

10. In **Autorizzazioni** selezionare **Controllo completo** (verranno selezionate tutte le altre opzioni) > **Avanti** > **Fine**.

    ![Schermata di delega del controllo](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Installare Intune Connector

Intune Connector per Active Directory deve essere installato in un computer che esegue Windows Server 2016 che ha accesso a Internet e ad Active Directory. Per aumentare la scalabilità e la disponibilità o per supportare più domini di Active Directory, è possibile installare più connettori nell'ambiente. È consigliabile installare il connettore in un server che non esegue altri connettori Intune.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Intune Connector per Active Directory (anteprima)** > **Aggiungi un connettore**. 
2. Seguire le istruzioni per scaricare il connettore.
3. Aprire il file di installazione del connettore scaricato per installare il connettore (ODJConnectorBootstrapper.exe).
4. Al termine dell'installazione, scegliere **Configura**.
5. Scegliere **Accedi**.
6. Immettere le credenziali del ruolo Amministratore globale o Amministratore di Intune dell'utente.
8. Passare a **Registrazione del dispositivo** > **Registrazione Windows** > **Intune Connector per Active Directory (anteprima)** e verificare che lo stato della connessione sia **Attivo**.

### <a name="configure-web-proxy-settings"></a>Configurare le impostazioni del proxy Web

Se nell'ambiente di rete è presente un proxy Web, attenersi alle istruzioni indicate in [Usare server proxy locali esistenti](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) per garantire il corretto funzionamento di Intune Connector per Active Directory.


## <a name="create-a-device-group"></a>Creare un gruppo di dispositivi
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo**:
    1. In **Tipo gruppo** scegliere **sicurezza**.
    2. Immettere un **Nome gruppo** e una **Descrizione gruppo**.
    3. Scegliere un **Tipo di appartenenza**.
3. Se nel passaggio precedente si è scelto **Dispositivi dinamici** come **Tipo di appartenenza**, nella scheda **Gruppo** scegliere **Membri dispositivo dinamico** e digitare uno dei codici seguenti nella casella **Regola avanzata**.
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot, digitare `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot con un ID ordine specifico, digitare `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot con un ID ordine d'acquisto specifico, digitare `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Dopo aver aggiunto il codice **Regola avanzata** scegliere **Salva**.
5. Scegliere **Crea**.  

## <a name="register-your-autopilot-devices"></a>Registrare i dispositivi di Autopilot

Scegliere uno dei modi seguenti per registrare i dispositivi di Autopilot:

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrare i dispositivi di Autopilot che sono già registrati

1. Creare un profilo di distribuzione di Autopilot con l'opzione **Converti tutti i dispositivi interessati in Autopilot** impostata su **Sì**. 
2. Assegnare il profilo a un gruppo che contiene i membri che si vuole registrare automaticamente in Autopilot.

Per altre informazioni, vedere [Creare un profilo di distribuzione Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrare i dispositivi di Autopilot che non sono registrati

Se i dispositivi non sono ancora registrati, è possibile registrarli. Per altre informazioni, vedere [Aggiungere dispositivi](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrare i dispositivi da un OEM

Quando vengono acquistati nuovi dispositivi, alcuni OEM possono registrare i dispositivi per l'utente. Per altre informazioni, vedere la [pagina di Windows Autopilot](http://aka.ms/WindowsAutopilot).

Quando vengono registrati i dispositivi di Autopilot (prima che vengano registrati in Intune), i dispositivi sono visibili in tre posizioni (con i numeri di serie impostati come nomi):
- Il pannello Dispositivi di Windows AutoPilot in Intune nel portale di Azure (**Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi**).
- Pannello Dispositivi di Azure AD in Intune nel portale di Azure (**Dispositivi** > **Dispositivi di Azure AD**).
- Pannello Tutti i dispositivi di AAD in Azure Active Directory nel portale di Azure (**Dispositivi** > **Tutti i dispositivi**).

Dopo la registrazione dei dispositivi di Autopilot, i dispositivi sono visibili in quattro posizioni:
- Pannello Dispositivi di Windows AutoPilot in Intune nel portale di Azure (**Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi**).
- Pannello Dispositivi di Azure AD in Intune nel portale di Azure (**Dispositivi** > **Dispositivi di Azure AD**).
- Pannello Tutti i dispositivi di AAD in Azure Active Directory nel portale di Azure (**Dispositivi** > **Tutti i dispositivi**).
- Pannello Tutti i dispositivi in Intune nel portale di Azure (**Dispositivi** > **Tutti i dispositivi**).

Dopo la registrazione dei dispositivi di Autopilot, i nomi dei dispositivi vengono modificati nel nome host del dispositivo. Per impostazione predefinita, il nome inizia con "DESKTOP-".




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Creare e assegnare un profilo di distribuzione AutoPilot
I profili di distribuzione AutoPilot vengono usati per configurare i dispositivi AutoPilot.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo**.
2. Specificare un **Nome** e una **Descrizione** facoltativa.
3. In **Modalità di distribuzione** scegliere **Definita dall'utente**.
4. Nella casella **Join to Azure AD as** (Aggiungi ad Azure AD come) scegliere **Aggiunto ad Azure AD ibrido (anteprima)**.
5. Scegliere **Configurazione guidata**, configurare le opzioni in base alle proprie esigenze e scegliere **Salva**.
6. Scegliere **Crea** per creare il profilo. 
7. Nel pannello del profilo scegliere **Assegnazioni**.
8. Scegliere **Selezione gruppi** > nel pannello **Selezione gruppi** scegliere il gruppo di dispositivi > **Seleziona**.

Il passaggio dello stato del profilo del dispositivo da **Non assegnato** ad **Assegnazione** e infine ad **Assegnato** richiede circa 15 minuti.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Attivare la pagina dello stato della registrazione (facoltativo)

1.  In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Enrollment Status Page (Preview)** (Pagina stato registrazione (anteprima)).
2.  Nel pannello **Enrollment Status Page** (Pagina stato registrazione) scegliere **Predefinito** > **Impostazioni**.
3.  Per **Show app and profile installation progress** (Visualizza stato di avanzamento installazione app e profilo), scegliere **Sì**.
4. Configurare le altre opzioni in base alle proprie esigenze.
5.  Scegliere **Salva**.

## <a name="create-and-assign-a-domain-join-profile"></a>Creare e assegnare un profilo di aggiunta al dominio

1. In **Microsoft Intune** scegliere **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le seguenti proprietà:
   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Descrizione:** immettere una descrizione per il profilo.
   - **Piattaforma**: scegliere **Windows 10 e versioni successive**.
   - **Tipo profilo**: scegliere **Aggiunta a un dominio (anteprima)**.
3.  Scegliere **Impostazioni** e specificare un **Prefisso nome computer**, **Nome di dominio** e **Unità organizzativa** (facoltativo). 
4. Scegliere **OK** > **Crea**. Il profilo viene creato e quindi visualizzato nell'elenco.
5. Per assegnare il profilo, seguire i passaggi indicati in [Assegnare un profilo di dispositivo](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato Windows AutoPilot, scoprire come gestire i dispositivi. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).