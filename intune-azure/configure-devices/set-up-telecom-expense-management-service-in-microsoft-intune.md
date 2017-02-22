---
title: Configurare un servizio di gestione delle spese per telecomunicazioni | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: configurare il servizio di gestione delle spese per telecomunicazioni Saaswedo per l&quot;integrazione con Intune.'
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Impostare un servizio di gestione delle spese per telecomunicazioni nell'anteprima di Intune in Azure
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune è integrato con la soluzione di gestione delle spese per telecomunicazioni Datalert dello sviluppatore software di terze parti Saaswedo. Datalert è un software di gestione delle spese per telecomunicazioni in tempo reale, che consente di gestire il consumo dei dati per le telecomunicazioni e di evitare eccedenze impreviste e costose relative a dati e roaming per i dispositivi gestiti da Intune. L'integrazione di Intune con Datalert consente di impostare centralmente, monitorare e limitare il consumo dei dati, sia nazionale che in roaming, tramite avvisi automatizzati generati ogni volta che i limiti superano le soglie definite. È possibile configurare il servizio per applicare azioni diverse a utenti individuali o gruppi di utenti finali, inclusa la disabilitazione del roaming, in caso di superamento della soglia. I report che forniscono il consumo dei dati e le informazioni di monitoraggio sono disponibili dalla console di gestione Datalert.

Prima di poter usare il servizio Datalert con Intune, è necessario configurare le impostazioni nella console di Datalert e in Intune. La connessione deve essere attivata per il servizio Datalert e per Intune. Se è abilitato il lato Datalert della connessione, ma non il lato Intune, Intune riceve la comunicazione, ma la ignora.

>[!NOTE]
>Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) per l'attivazione e il supporto Datalert per le licenze software necessarie.

## <a name="supported-platforms"></a>Piattaforme supportate

- Samsung KNOX
- iOS 8.0 e versioni successive

## <a name="prerequisites"></a>Prerequisiti

- Disporre di una sottoscrizione a Microsoft Intune.
- Disporre di una sottoscrizione al servizio di gestione delle spese per telecomunicazioni Datalert.

## <a name="list-of-telecom-expense-management-providers"></a>Elenco di provider di gestione delle spese per telecomunicazioni

Intune attualmente si integra con i provider di gestione delle spese per telecomunicazioni seguenti:

[Servizio di gestione delle spese per telecomunicazioni Saaswedo Datalert](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>Configurare Intune per lavorare con il servizio Datalert

 

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Installazione** > **Gestione delle spese per telecomunicazioni**.
2. In **Gestione delle spese per telecomunicazioni**selezionare **Stato connessione**.

3. Selezionare **Elenco di provider di servizi di gestione delle spese per telecomunicazioni** e quindi selezionare il provider nell'elenco visualizzato. Verrà visualizzata una pagina specifica del provider. Per Saaswedo, si aprirà la pagina Datalert. Per acquistare una sottoscrizione, è necessario lavorare con Saaswedo Datalert.

4. Nella console di gestione **Datalert**:

    a. Andare alla scheda **Impostazioni** e quindi alla sezione **MDM configuration** (Configurazione di MDM).

    b. Selezionare **Sblocca** per poter immettere le impostazioni nella pagina.

    c. Per **Server MDM** (MDM del server) scegliere **Microsoft Intune**.

    d. Per **ID tenant** immettere l'ID tenant di Intune e selezionare il pulsante **Connessione**. Quando si seleziona **Connessione**, il servizio Datalert esegue un controllo con Intune per garantire che non siano presenti connessioni Datalert preesistenti con Intune. Dopo alcuni secondi, viene visualizzata una pagina di accesso Microsoft, seguita dalla pagina di autenticazione Datalert per Azure.

    e. Nella pagina di autenticazione Microsoft selezionare **Accetta**. Si viene reindirizzati a una pagina di ringraziamento Datalert, che si chiude dopo pochi secondi. Datalert convalida la connessione e visualizza segni di spunta verdi accanto all'elenco di elementi convalidati. Se la convalida ha esito negativo, viene visualizzato un messaggio in rosso. In questo caso, contattare il supporto Datalert per assistenza.

5. Attendere alcuni minuti, quindi andare al portale di Azure e verificare che lo stato della connessione venga visualizzato come **Attivo**. 

    >[!NOTE]
    >Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

6. Tornare alla console di gestione Datalert e configurare le righe di dati:

    a. Andare alla scheda **Impostazioni**.

    b. Andare alla procedura guidata **Installazione** e seguire i passaggi descritti.



Il servizio Datalert è ora attivo e avvia il monitoraggio del consumo dei dati e la disattivazione di dati cellulare e roaming sui dispositivi che superano i limiti di utilizzo configurati.

## <a name="turning-off-the-datalert-service"></a>Disattivazione del servizio Datalert

Se si disabilita il servizio Datalert nel portale di Azure:

- Tutte le azioni che sono state applicate ai dispositivi, a causa di precedenti violazioni dei limiti di utilizzo, vengono annullate.
- Agli utenti non vengono più impediti l'accesso ai dati e il roaming.
- Intune riceve ancora i segnali provenienti dal servizio, ma li ignora.

**Per disattivare il servizio**

1. Nel pannello **Gestione delle spese per telecomunicazioni** nel portale di Azure selezionare **Disabilita**.

2. Selezionare **Salva**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visualizzazione del consumo dei dati e dei report di roaming

A questo punto, il reporting del consumo dei dati è disponibile solo nella console di gestione Datalert di Saaswedo.



<!--HONumber=Feb17_HO2-->


