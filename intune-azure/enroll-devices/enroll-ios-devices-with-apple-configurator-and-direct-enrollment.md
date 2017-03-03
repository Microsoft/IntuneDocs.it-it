---
title: Registrare i dispositivi iOS con Apple Configurator e registrazione diretta
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni su come usare lo strumento Apple Configurator per registrare i dispositivi iOS di proprietà dell&quot;azienda con la registrazione diretta."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b464a07e701797d39b7f9f50d1854a9a2682ac8e
ms.openlocfilehash: 3208e964f2676ebcc1e54e29f039c4965c20238f
ms.lasthandoff: 03/01/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>Registrare i dispositivi iOS con Apple Configurator e registrazione diretta 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) in esecuzione in un computer Mac. Questo processo non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi con **nessuna affinità utente** e richiede la connessione USB del dispositivo iOS a un computer Mac per configurare la registrazione aziendale.

>[!NOTE]
>Questo metodo di registrazione non può essere usato con il metodo del [manager di registrazione dispositivi](enroll-devices-using-device-enrollment-manager.md).

Durante la registrazione diretta dei dispositivi iOS, è possibile registrare un dispositivo senza acquisire il numero di serie del dispositivo. È anche possibile denominare il dispositivo per scopi di identificazione prima che Intune acquisisca il nome del dispositivo durante la registrazione. L'app Portale aziendale non è supportata per i dispositivi con registrazione diretta. In queste istruzioni si presuppone l'uso di Apple Configurator 2.0 in un computer Mac.

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).


## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di configurare la registrazione di dispositivi iOS:

- [Configurare i domini](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità MDM](set-mdm-authority.md)
- [Creare i gruppi](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurare il Portale aziendale](/intune-azure/manage-apps/company-portal-app)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](get-an-apple-mdm-push-certificate.md)
- Assicurarsi di avere accesso fisico ai dispositivi iOS
- Ottenere i numeri di serie dei dispositivi (vedere [Come trovare il numero di serie di un prodotto Apple](https://support.apple.com//HT204308))
- Avere a disposizione i cavi di connessione USB
- Assicurarsi di disporre di un computer Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Creare un profilo di Apple Configurator per i dispositivi

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. La procedura seguente mostra come creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Registrazione Apple**.

3. In **Gestisci le impostazioni di registrazione di Apple Configurator** selezionare **Profili AC**.

4. Nel pannello **Profili di registrazione di Apple Configurator** selezionare **Crea**.

5. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.

6. Per **Affinità utente** scegliere **Registra senza affinità utente** per accertarsi che il dispositivo non sia associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

7. Selezionare **Crea** per salvare il profilo.

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Esportare il profilo come file con estensione mobileconfig per i dispositivi iOS

1. Nel pannello **Esporta il profilo** scaricare il profilo di registrazione in [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) per inviarlo direttamente come profilo di gestione a un dispositivo iOS connesso. Non è necessario alcun ripristino delle impostazioni predefinite.

2. Preparare il dispositivo con Apple Configurator usando la procedura seguente.

   a. In un computer Mac aprire Apple Configurator 2.0.

   b. Connettere il dispositivo iOS al computer Mac con un cavo USB. Chiudere Photos, iTunes e altre app che vengono aperte quando viene rilevato il dispositivo.

   c. In Apple Configurator selezionare il dispositivo iOS connesso e scegliere **Aggiungi**. Nell'elenco a discesa vengono visualizzate le opzioni che possono essere aggiunte al dispositivo. Scegliere **Profili**.

   d. Usare il selettore file per selezionare il file con estensione mobileconfig esportato da Intune e scegliere **Aggiungi**. Il profilo viene aggiunto al dispositivo. Se per il dispositivo è indicato Supervisione non eseguita, l'installazione richiederà l'accettazione sul dispositivo.

3. Usare la procedura seguente per installare il profilo nel dispositivo iOS. Il dispositivo deve aver già completato l'Assistente configurazione ed essere pronto per l'uso. Se la registrazione comporta distribuzioni dell'app, il dispositivo deve avere un ID Apple configurato perché le distribuzioni di app richiederanno l'accesso all'App Store con un ID Apple.

   a. Sbloccare il dispositivo iOS.

   b. Nella finestra di dialogo **Installa profilo** del **profilo di gestione** scegliere **Installa**.

   c. Indicare il passcode del dispositivo o l'ID Apple, se necessario.

   d. Accettare l'**avviso** e scegliere **Installa**.

   e. Accettare l'**avviso remoto** e scegliere **Attendibile**.

   f. Quando la casella **Profilo installato** conferma che il profilo è Installato, scegliere **Fine**.

4. Nel dispositivo iOS aprire la finestra **Impostazioni** e passare a **Generale**  >  **Gestione dei dispositivi**  >  **Profilo di gestione**. Verificare che l'installazione del profilo è inclusa nell'elenco e controllare le restrizioni dei criteri iOS e le app installate. La visualizzazione delle restrizioni dei criteri e delle app nel dispositivo può impiegare fino a 10 minuti.

5. Distribuire i dispositivi. Il dispositivo iOS viene ora registrato con Intune e gestito.

