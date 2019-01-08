---
title: Esercitazione - Usare Autopilot per registrare i dispositivi in Intune
titleSuffix: Microsoft Intune
description: In questa esercitazione si vedrà come configurare Windows Autopilot per registrare i dispositivi in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 087f890f84c9bc0ff0c46f129ef84b8a268c738e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187736"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Esercitazione: usare Autopilot per registrare i dispositivi Windows in Intune
Windows Autopilot semplifica la registrazione dei dispositivi. Con Microsoft Intune e Autopilot è possibile assegnare i nuovi dispositivi agli utenti finali senza la necessità di compilare, gestire e applicare immagini del sistema operativo personalizzate. 

In questa esercitazione si apprenderà come:
> [!div class="checklist"]
> * Aggiungere dispositivi a Intune
> * Creare un gruppo di dispositivi Autopilot
> * Creare un profilo di distribuzione Autopilot
> * Assegnare il profilo di distribuzione Autopilot al gruppo di dispositivi
> * Distribuire i dispositivi Windows agli utenti

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

Per una panoramica di vantaggi, scenari e prerequisiti di Autopilot, vedere [Panoramica di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Prerequisiti
- [Configurare la registrazione automatica di Windows](quickstart-setup-auto-enrollment.md)
- [sottoscrizione di Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Aggiungere dispositivi

Il primo passaggio nella configurazione di Windows Autopilot consiste nell'aggiungere i dispositivi Windows in Intune. A tale scopo, è sufficiente creare un file CSV e importarlo in Intune.

1. In qualsiasi editor di testo, creare un elenco di valori delimitati da virgole (CSV) che identificano i dispositivi Windows. Usare il seguente formato:
    
    *numero-di-serie*, *id-prodotto-windows*, *hash-hardware*, *id-ordine-facoltativo*
    
    I primi tre elementi sono obbligatori, ma l'ID dell'ordine è facoltativo.

2. Salvare il file CSV.

3. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > **Importa**.

    ![Screenshot dei dispositivi di Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

4. In **Aggiungi dispositivi di Windows AutoPilot** individuare e selezionare il file CSV salvato.

    ![Screenshot dell'aggiunta dei dispositivi di Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

5. Scegliere **Importa** per avviare l'importazione delle informazioni sui dispositivi. L'importazione può richiedere alcuni minuti.

4. Al termine dell'importazione scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > **Windows AutoPilot** > **Sincronizza**. Viene visualizzato un messaggio che informa che è in corso la sincronizzazione. Il processo potrebbe richiedere alcuni minuti, a seconda di quanti dispositivi devono essere sincronizzati.

5. Aggiornare la vista per visualizzare i nuovi dispositivi.

## <a name="create-an-autopilot-device-group"></a>Creare un gruppo di dispositivi Autopilot

Successivamente, verrà creato un gruppo di dispositivi in cui verranno inseriti i dispositivi di Autopilot appena caricati.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo**:
    1. In **Tipo gruppo** scegliere **sicurezza**.
    2. Per **Nome gruppo** immettere *Gruppo Autopilot*. Per **Descrizione gruppo** immettere *Gruppo di test per dispositivi Autopilot*.
    3. In **Tipo di appartenenza** scegliere **Assegnato**.
3. Nel riquadro **Gruppo** scegliere **Membri** e aggiungere i dispositivi Autopilot al gruppo. I dispositivi Autopilot che non sono ancora registrati sono dispositivi il cui nome è uguale al numero di serie del dispositivo stesso.
4. Scegliere **Crea**.  

## <a name="create-an-autopilot-deployment-profile"></a>Creare un profilo di distribuzione Autopilot

Dopo aver creato un gruppo di dispositivi, è necessario creare un profilo di distribuzione in modo che sia possibile configurare i dispositivi Autopilot.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo**.
2. Per **Nome** immettere *Profilo Autopilot*. Per **Descrizione** immettere *Profilo di test per dispositivi Autopilot*.
3. Impostare **Converti tutti i dispositivi interessati in Autopilot** su **Sì**. Questa impostazione garantisce che tutti i dispositivi nell'elenco vengano registrati per il servizio di distribuzione Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore.
4. In **Modalità di distribuzione** scegliere **Definita dall'utente**. I dispositivi con questo profilo sono associati all'utente che esegue la registrazione del dispositivo. Le credenziali dell'utente sono necessarie per effettuare la registrazione del dispositivo.
5. Nella casella **Join to Azure AD as** (Connetti ad Azure AD come) scegliere **Aggiunto ad Azure AD**.
6. Scegliere **Configurazione guidata**, configurare le opzioni seguenti e lasciare le altre impostate sui valori predefiniti, quindi scegliere **Salva**:
    - **Contratto di licenza con l'utente finale**: **Nascondi**
    - **impostazioni privacy**: **Mostra**
    - **Tipo di account utente**: **Standard**

6. Scegliere **Crea** per creare il profilo. Il profilo di distribuzione di Autopilot è ora disponibile per l'assegnazione ai dispositivi.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Assegnare un profilo di distribuzione di Autopilot a un gruppo di dispositivi

Dopo aver creato il profilo di distribuzione, lo si assegnerà al gruppo di dispositivi.
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > scegliere un profilo.
2. Nel pannello del profilo specifico, scegliere **Assegnazioni**. 
3. Scegliere **Selezione gruppi**, nel pannello **Selezione gruppi** scegliere **Gruppo Autopilot** e quindi scegliere **Seleziona**.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

È ora possibile distribuire i dispositivi Windows agli utenti. Quando effettuano l'accesso per la prima volta, il sistema Autopilot registra e configura automaticamente i dispositivi. 

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se non si vogliono più usare dispositivi Autopilot, è possibile eliminarli.

1. Se i dispositivi sono registrati in Intune, è necessario prima [eliminarli dal portale di Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi**.

3. In **Dispositivi di Windows AutoPilot** scegliere i dispositivi che si vuole eliminare e quindi scegliere **Elimina**.

4. Confermare l'eliminazione scegliendo **Sì**. L'eliminazione può richiedere alcuni minuti.

## <a name="next-steps"></a>Passaggi successivi

Sono disponibili ulteriori informazioni sulle altre opzioni disponibili per Windows Autopilot.

> [!div class="nextstepaction"]
> [Articolo approfondito sulla registrazione con Autopilot](enrollment-autopilot.md)

