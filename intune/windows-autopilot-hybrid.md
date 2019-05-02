---
title: Registrazione dei dispositivi aggiunti ad Azure AD - Windows Autopilot
titleSuffix: ''
description: Usare Windows Autopilot per registrare dispositivi aggiunti ad Azure Active Directory ibrido in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ab718cd087757211ad4e84cbba39808cf9de7d3
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515509"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot-preview"></a>Distribuire dispositivi aggiunti ad Azure AD ibrido usando Intune e Windows Autopilot (anteprima)
È possibile usare Intune e Windows Autopilot per configurare i dispositivi aggiunti ad Azure Active Directory ibrido. A tale scopo, eseguire i passaggi descritti in questo articolo.

## <a name="prerequisites"></a>Prerequisiti

Configurare correttamente i [dispositivi aggiunti ad Azure AD ibrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Assicurarsi di [verificare la registrazione del dispositivo]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) usando il cmdlet Get-MsolDevice.

I dispositivi da registrare devono anche:
- Eseguire Windows 10 con l'[aggiornamento di ottobre 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Avere accesso a Internet.
- Avere accesso ad Active Directory (la connessione VPN non è supportata).
- Eseguire la Configurazione guidata.
- Essere in grado di effettuare il ping del controller di dominio del dominio cui si sta tentando di aggiungere il dispositivo.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurare la registrazione automatica di Windows 10

1. Accedere al [portale di Azure](https://portal.azure.com) e nel riquadro a sinistra selezionare **Azure Active Directory**.

   ![Portale di Azure](./media/auto-enroll-azure-main.png)

1. Selezionare **Servizi Mobility (MDM e MAM)**.

   ![Riquadro Azure Active Directory](./media/auto-enroll-mdm.png)

1. Selezionare **Microsoft Intune**.

   ![Riquadro Servizi Mobility (MDM e MAM)](./media/auto-enroll-intune.png)

1. Assicurarsi che gli utenti che distribuiscono dispositivi aggiunti ad Azure Active Directory mediante Intune e Windows siano membri di un gruppo incluso nell'**ambito utente MDM**.

   ![Riquadro Configura di Servizi Mobility (MDM e MAM)](./media/auto-enroll-scope.png)

1. Usare i valori predefiniti nelle caselle **URL delle condizioni per l'utilizzo di MDM**, **URL individuazione MDM** e **URL conformità MDM**, quindi selezionare **Salva**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentare il limite di account computer nell'unità organizzativa

Intune Connector per Active Directory crea computer registrati in Autopilot nel dominio Active Directory locale. Il computer che ospita Intune Connector deve avere l'autorizzazione per la creazione di oggetti computer all'interno del dominio. 

In alcuni domini ai computer non viene assegnata l'autorizzazione per la creazione di computer. Sui domini è anche impostato un limite predefinito (pari a 10) che si applica a tutti gli utenti e i computer a cui non sono stati delegati i diritti di creazione di oggetti computer. I diritti devono pertanto essere delegati ai computer che ospitano Intune Connector nell'unità organizzativa in cui vengono creati i dispositivi aggiunti ad Azure AD ibrido.

L'unità organizzativa a cui vengono assegnate le autorizzazioni per la creazione di computer deve corrispondere a:
- L'unità organizzativa specificata nel profilo Aggiunta a un dominio.
- Se non è selezionato alcun profilo, il nome di dominio del computer per il dominio.

1. Aprire **Utenti e computer di Active Directory (DSA.msc)**.

1. Fare clic con il pulsante destro del mouse sull'unità organizzativa che verrà usata per creare i computer aggiunti ad Azure AD ibrido, quindi selezionare **Delega controllo**.

    ![Comando Delega controllo](media/windows-autopilot-hybrid/delegate-control.png)

1. Nella procedura **Delega guidata del controllo** scegliere **Avanti** > **Aggiungi** > **Tipi di oggetto**.

1. Nella finestra di dialogo **Tipi di oggetto** selezionare la casella di controllo **Computer**, quindi fare clic su **OK**.

    ![Riquadro Tipi di oggetto](media/windows-autopilot-hybrid/object-types-computers.png)

1. Nel riquadro **Seleziona utenti, computer o gruppi** nella casella **Immettere i nomi degli oggetti da selezionare** immettere il nome del computer in cui è installato Connector.

    ![Riquadro Seleziona utenti, computer o gruppi](media/windows-autopilot-hybrid/enter-object-names.png)

1. Selezionare **Controlla nomi** per convalidare la voce, selezionare **OK** e quindi selezionare **Avanti**.

1. Selezionare **Crea un'attività personalizzata per eseguire la delega** > **Avanti**.

1. Selezionare la casella di controllo **Solo i seguenti oggetti contenuti nella cartella**, quindi selezionare le caselle di controllo **Oggetto computer**, **Crea gli oggetti selezionati in questa cartella** e **Elimina gli oggetti selezionati in questa cartella**.

    ![Riquadro Tipo di oggetti Active Directory](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Selezionare **Avanti**.

1. In **Autorizzazioni** selezionare la casella di controllo **Controllo completo**.  
    Questa azione consente di selezionare tutte le altre opzioni.

    ![Riquadro Autorizzazioni](media/windows-autopilot-hybrid/full-control.png)

1. Selezionare **Avanti** e quindi selezionare **Fine**.

## <a name="install-the-intune-connector"></a>Installare Intune Connector

Il connettore di Intune per Active Directory deve essere installato in un computer che esegue Windows Server 2016 o versioni successive. Il computer deve anche avere accesso a Internet e al servizio Active Directory. Per aumentare la scalabilità e la disponibilità o per supportare più domini di Active Directory, è possibile installare più connettori nell'ambiente. È consigliabile installare il connettore in un server che non esegue altri connettori di Intune.

1. Assicurarsi di avere installato e configurato un Language Pack, come descritto in [Requisiti di lingua connettore Intune (anteprima)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. In [Intune](https://aka.ms/intuneportal) selezionare **Registrazione del dispositivo** > **Registrazione Windows** > **Connettore di Intune per Active Directory (anteprima)** > **Aggiungi un connettore**. 
3. Seguire le istruzioni per scaricare il connettore.
4. Aprire il file di installazione del connettore scaricato *ODJConnectorBootstrapper.exe* per installare il connettore.
5. Al termine dell'installazione selezionare **Configura**.
6. Selezionare **Accedi**.
7. Immettere le credenziali utente del ruolo Amministratore globale o Amministratore di Intune.  
   All'account utente deve essere assegnata una licenza di Intune.
8. Passare a **Registrazione del dispositivo** > **Registrazione Windows** > **Connettore di Intune per Active Directory (anteprima)** e verificare che lo stato della connessione sia **Attivo**.

> [!NOTE]
> Dopo l'accesso, la visualizzazione del connettore in [Intune](https://aka.ms/intuneportal) può richiedere qualche minuto. Il connettore viene visualizzato solo se può comunicare correttamente con il servizio Intune.

### <a name="configure-web-proxy-settings"></a>Configurare le impostazioni del proxy Web

Se nell'ambiente di rete è presente un proxy Web, vedere [Usare server proxy locali esistenti](autopilot-hybrid-connector-proxy.md) per garantire il corretto funzionamento del connettore di Intune per Active Directory.


## <a name="create-a-device-group"></a>Creare un gruppo di dispositivi
1. In [Intune](https://aka.ms/intuneportal) selezionare **Gruppi** > **Nuovo gruppo**.

1. Nel riquadro **Gruppo** seguire questa procedura:

    a. In **Tipo gruppo** selezionare **Sicurezza**.

    b. Immettere un **Nome gruppo** e una **Descrizione gruppo**.

    c. Selezionare un **Tipo di appartenenza**.

1. Se come tipo di appartenenza è stato scelto **Dispositivi dinamici**, nel riquadro **Gruppo** selezionare **Membri dispositivo dinamico** e quindi nella casella **Regola avanzata** eseguire una delle operazioni seguenti:
    - Per creare un gruppo che includa tutti i dispositivi Autopilot, digitare `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Per creare un gruppo che includa tutti i dispositivi Autopilot con un ID ordine specifico, digitare `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`.
    - Per creare un gruppo che includa tutti i dispositivi Autopilot con un ID ordine di acquisto specifico, digitare `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Selezionare **Salva**.

1. Selezionare **Crea**.  

## <a name="register-your-autopilot-devices"></a>Registrare i dispositivi di Autopilot

Selezionare uno dei modi seguenti per registrare i dispositivi di Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrare i dispositivi di Autopilot che sono già registrati

1. Creare un profilo di distribuzione di Autopilot con l'opzione **Converti tutti i dispositivi interessati in Autopilot** impostata su **Sì**. 
2. Assegnare il profilo a un gruppo contenente i membri da registrare automaticamente in Autopilot.

Per altre informazioni, vedere [Creare un profilo di distribuzione Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrare i dispositivi di Autopilot che non sono registrati

Se i dispositivi non sono ancora registrati, è possibile registrarli. Per altre informazioni, vedere [Aggiungere dispositivi](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrare i dispositivi da un OEM

Quando vengono acquistati nuovi dispositivi, alcuni OEM possono registrare i dispositivi per l'utente. Per altre informazioni, vedere la [pagina di Windows Autopilot](http://aka.ms/WindowsAutopilot).

Quando i dispositivi di Autopilot vengono *registrati* (prima che vengano registrati in Intune), sono visibili in tre posizioni (con i numeri di serie impostati come nomi):
- Il riquadro **Dispositivi di Autopilot** in Intune nel portale di Azure. Selezionare **Registrazione dispositivi** > **Registrazione Windows** > **Dispositivo**.
- Il riquadro **Dispositivi di Azure AD** in Intune nel portale di Azure. Selezionare **Dispositivi** > **Dispositivi di Azure AD**.
- Per visualizzare il riquadro **Tutti dispositivi** in Azure Active Directory nel portale di Azure selezionare **Dispositivi** > **Tutti i dispositivi**.

Dopo la *registrazione* i dispositivi di Autopilot vengono visualizzati in quattro posizioni:
- Il riquadro **Dispositivi di Autopilot** in Intune nel portale di Azure. Selezionare **Registrazione dispositivi** > **Registrazione Windows** > **Dispositivo**.
- Il riquadro **Dispositivi di Azure AD** in Intune nel portale di Azure. Selezionare **Dispositivi** > **Dispositivi di Azure AD**.
- Il riquadro **Tutti i dispositivi** in Azure Active Directory nel portale di Azure. Selezionare **Dispositivi** > **Tutti i dispositivi**.
- Il riquadro **Tutti i dispositivi** in Intune nel portale di Azure. Selezionare **Dispositivi** > **Tutti i dispositivi**.

Dopo la registrazione dei dispositivi di Autopilot, i nomi dei dispositivi diventano il nome host del dispositivo. Per impostazione predefinita, il nome host inizia con *DESKTOP-*.


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Creare e assegnare un profilo di distribuzione AutoPilot
I profili di distribuzione AutoPilot vengono usati per configurare i dispositivi AutoPilot.

1. In [Intune](https://aka.ms/intuneportal) selezionare **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo**.
1. Digitare un **Nome** e una **Descrizione** facoltativa.
1. In **Modalità di distribuzione** scegliere **Definita dall'utente**.
1. Nella casella **Aggiungi ad Azure AD come** scegliere **Aggiunto ad Azure AD ibrido (anteprima)**.
1. Selezionare **Configurazione guidata**, configurare le opzioni in base alle esigenze e selezionare **Salva**.
1. Selezionare **Crea** per creare il profilo. 
1. Nel riquadro del profilo selezionare **Assegnazioni**.
1. Selezionare **Seleziona gruppi**.
1. Nel riquadro **Seleziona gruppi** selezionare il gruppo di dispositivi e fare clic su **Seleziona**.

Il passaggio dello stato del profilo del dispositivo da *Non assegnato* ad *Assegnazione* e infine ad *Assegnato* richiede circa 15 minuti.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Facoltativo) Attivare la pagina dello stato della registrazione

1. In [Intune](https://aka.ms/intuneportal) selezionare **Registrazione del dispositivo** > **Registrazione Windows** > **Pagina relativa allo stato della registrazione (anteprima)**.
1. Nel riquadro **Pagina relativa allo stato della registrazione** selezionare **Predefinito** > **Impostazioni**.
1. Nella casella **Mostra lo stato dell'installazione di profili e applicazioni** scegliere **Sì**.
1. Configurare le altre opzioni in base alle proprie esigenze.
1. Selezionare **Salva**.

## <a name="create-and-assign-a-domain-join-profile"></a>Creare e assegnare un profilo di aggiunta al dominio

1. In [Intune](https://aka.ms/intuneportal) selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
1. Immettere le proprietà seguenti:
   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Description**: Immettere una descrizione del profilo.
   - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
   - **Tipo di profilo**: selezionare **Aggiunta a un dominio (anteprima)**.
1. Selezionare **Impostazioni** e specificare **Prefisso nome computer**, **Nome di dominio** e **Unità organizzativa** (facoltativo) nel [formato DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Selezionare **OK** > **Crea**.  
    Il profilo viene creato e visualizzato nell'elenco.
1. Per assegnare il profilo, seguire i passaggi indicati in [Assegnare un profilo di dispositivo](device-profile-assign.md#assign-a-device-profile). 

> [!NOTE]
> Le funzionalità di denominazione per Windows Autopilot per l'aggiunta ad Azure AD ibrido non supportano le variabili, ad esempio %SERIAL%, e supportano solo i prefissi per il nome del computer.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato Windows AutoPilot, scoprire come gestire i dispositivi. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).
