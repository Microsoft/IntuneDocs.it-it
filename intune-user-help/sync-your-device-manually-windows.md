---
title: Sincronizzare manualmente il dispositivo Windows | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328ec3111aae5f8363f2743d423a56eafc47d765
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546262"
---
# <a name="sync-your-windows-device-manually"></a>Sincronizzare il dispositivo Windows manualmente

Quando la velocità di installazione di un'app non è quella prevista, avviare una sincronizzazione manuale del dispositivo. Le sincronizzazioni manuali forzano la connessione del dispositivo a Intune per trovare gli aggiornamenti e le comunicazioni più recenti. La velocità di installazione può aumentare dopo avere completato la sincronizzazione del dispositivo.

Intune supporta la sincronizzazione manuale dall'app Portale aziendale, dalla barra delle applicazioni o dal menu Start del desktop e dall'app Impostazioni del dispositivo. La funzionalità dell'app Portale aziendale è supportata nei dispositivi Windows 10 che eseguono Creators Update (1703) o versione successiva. 

Tutti i dispositivi Windows possono essere sincronizzati dall'app Impostazioni del dispositivo, inclusi:

* [Windows 10 Desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>Eseguire la sincronizzazione diretta dall'app Portale aziendale per Windows
Completare questi passaggi per sincronizzare manualmente qualsiasi dispositivo Windows 10 che esegue l'aggiornamento Creators Update (versione 1703) o versione successiva.

1. Aprire l'app Portale aziendale nel dispositivo.

2. Selezionare **Impostazioni** > **Sincronizza**.

    ![Screenshot della home page dell'app Portale aziendale, con Impostazioni evidenziato](./media/RS1_homePage_settings_04.png)  
    
    ![Screenshot della pagina Impostazioni dell'app Portale aziendale, con il pulsante Sincronizza evidenziato](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>Eseguire la sincronizzazione dalla barra delle applicazioni o dal menu Start del dispositivo   

È anche possibile accedere al controllo della sincronizzazione all'esterno dell'app, dal desktop del dispositivo. È utile se l'app è stata aggiunta direttamente alla barra delle applicazioni o al menu Start e si vuole eseguire rapidamente la sincronizzazione.  

1. Trovare l'icona dell'app Portale aziendale nel menu Start o nella barra delle applicazioni.  
2. Fare clic con il pulsante destro del mouse sull'icona dell'app per visualizzare il menu (detto anche jump list).  

    ![Screenshot della barra delle applicazioni di Windows nel desktop di un dispositivo. L'icona dell'app Portale aziendale è stata selezionata per visualizzare un menu con le opzioni "Pin to taskbar" (Aggiungi alla barra delle applicazioni), "Chiudi finestra" e "Sincronizza il dispositivo".](./media/sync-device-from-start-menu-1807.png)  

3. Scegliere **Sincronizza il dispositivo**. Viene aperta la pagina **Impostazioni** dell'app Portale aziendale e inizia la sincronizzazione.  

## <a name="sync-from-settings-app"></a>Eseguire la sincronizzazione dall'app Impostazioni 
Completare questi passaggi per sincronizzare manualmente i dispositivi Microsoft HoloLens, Windows 10 desktop, Windows 10 Mobile o Windows Phone 8.1 dall'app Impostazioni.  

### <a name="windows-10-desktop"></a>Windows 10 Desktop
1. Nel dispositivo selezionare **Start** > **Impostazioni**.

2. Selezionare **Account**.

    ![Scelta di Account nella pagina Impostazioni](./media/win10pc-sync-2-settings-accounts.png)  

3. Esistono più versioni di Windows 10 per desktop. Confrontare la schermata con gli screenshot seguenti per determinare quale procedura seguire. 

    * Se nella schermata è visualizzato **Accedi all'azienda o all'istituto di istruzione**, vedere la procedura illustrata in [Accesso all'azienda o all'istituto di istruzione](#access-work-or-school-steps).

    ![Opzione Accedi all'azienda o all'istituto di istruzione nell'app Impostazioni](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * Se nella schermata è visualizzato **Accesso società**, vedere la procedura illustrata in [Accesso società](#work-access-steps).  

    ![Scelta di Accesso società come tipo di account](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>Procedura di accesso all'azienda o all'istituto di istruzione

1. Fare clic su **Accedi all'azienda o all'istituto di istruzione**.

    ![Screenshot che illustra l'opzione Accedi all'azienda o all'istituto di istruzione](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. Selezionare l'account con l'icona a forma di valigetta. Se questo account non è visualizzato, è possibile che la società abbia configurato diversamente le impostazioni. Fare invece clic sull'account con il logo Microsoft.

     ![Scegliere il nome dell'account accanto a Sincronia file o al logo Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Fare clic su **Info**. 

4. Fare clic su **Sincronizza**. 

#### <a name="work-access-steps"></a>Procedura di accesso società

1. Fare clic su **Accesso società**.

    ![Scelta di Accesso società come tipo di account](./media/win10pc-sync-3-work-access.png)

2. In **Registrati per la gestione dispositivi** selezionare il nome della società.

    ![Scelta del nome della società per la gestione dei dispositivi](./media/win10pc-sync-4-tap-com-name.png)

3. Fare clic su **Sincronizza**. Il pulsante rimane disabilitato finché non viene completata la sincronizzazione.

    ![Scelta del pulsante Sincronizza](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. Nel dispositivo accedere a **Tutte le app** > **Impostazioni** > **Account**.

       ![Scelta di Account nella schermata Impostazioni](./media/win10m-sync-1-settings-accounts.png)

   2. Selezionare **Accesso società**.

       ![Scelta di Accesso società come tipo di account](./media/win10m-sync-2-work-access.png)

   3. In **Registrati per la gestione dispositivi** selezionare il nome della società.

       ![Scelta del nome della società per la gestione dei dispositivi](./media/win10m-sync-3-tap-comp-name.png)

   4. Selezionare l'icona **Sincronizza**. Il pulsante rimane disabilitato finché non viene completata la sincronizzazione.

       ![Scelta dell'icona Sincronizza.](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
Queste istruzioni si applicano ai dispositivi HoloLens che eseguono l'Aggiornamento dell'anniversario di Windows 10 (noto anche come RS1). 
1. Aprire l'app Impostazioni del dispositivo.  

2. Selezionare **Account** > **Accesso società**.  
    ![Screenshot dell'app Impostazioni di HoloLens, con il collegamento Account evidenziato](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3. Selezionare l'account connesso > **Sincronizza**.  ![Screenshot dell'app Impostazioni di HoloLens, con il pulsante Sincronizza evidenziato](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. Accedere a **Tutte le app** > **Impostazioni** > **azienda**.

    ![Elenco di impostazioni](./media/wp81-1-sync-settings-workplace.png)

2. Selezionare il nome della propria società.

    ![Scelta del nome della società per l'account aziendale](./media/wp81-2-sync-tap-compname.png)

3. Selezionare l'icona **Sincronizza**.

    ![Scelta dell'icona Sincronizza.](./media/wp81-3-sync-tap-sync-button.png)

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
