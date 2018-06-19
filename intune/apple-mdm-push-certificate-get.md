---
title: Ottenere un certificato push MDM di Apple
titlesuffix: Microsoft Intune
description: Informazioni sulla procedura per ottenere un certificato push MDM di Apple per gestire i dispositivi iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28eb86a1924dc72df4c77cc3f8a05aacd61e0fbd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025672"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Ottenere un certificato push MDM di Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad, iPhone e computer Mac e offre agli utenti l'accesso alla posta elettronica e alle app aziendali. Per consentire a Intune di gestire dispositivi iOS e macOS, è necessario un certificato push Apple MDM. Dopo aver aggiunto il certificato a Intune, gli utenti possono registrare i propri dispositivi usando:

- L'app Portale aziendale.

- I metodi di registrazione in blocco Apple, come Device Enrollment Program, Apple School Manager o Apple Configurator.

Per altre informazioni sulle opzioni di registrazione, vedere [Scegliere come registrare i dispositivi iOS](enrollment-method-choose-ios.md).

Quando un certificato push scade, è necessario rinnovarlo. Per il rinnovo, assicurarsi di usare lo stesso ID Apple usato per la creazione del certificato push.


## <a name="steps-to-get-your-certificate"></a>Passaggi per ottenere il certificato
Nel [portale di Azure](https://portal.azure.com) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Certificato push MDM Apple** e quindi seguire questa procedura nel [portale di Azure](https://portal.azure.com).

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Passaggio 1. Concedere a Microsoft l'autorizzazione per l'invio di informazioni sugli utenti e i dispositivi ad Apple
Selezionare **Accetto.** per concedere a Microsoft l'autorizzazione per l'invio di dati ad Apple.

![Schermata Configura il certificato push MDM con l'opzione Push MDM non impostata.](./media/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>Passaggio 2: Scaricare la richiesta di firma del certificato di Intune necessaria per creare un certificato push MDM di Apple
Selezionare **Scarica CSR** per scaricare e salvare il file di richiesta in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

  ### <a name="step-3-create-an-apple-mdm-push-certificate"></a>Passaggio 3. Creare un certificato push MDM di Apple
Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Accedere con l'ID Apple aziendale e fare clic su **Crea un certificato**. Selezionare **Scegli file**, individuare il file di richiesta di firma del certificato e scegliere **Invia**. Nella pagina di conferma scegliere **Download** per scaricare il file del certificato (con estensione PEM), quindi salvare il file in locale.

> [!NOTE]
> Il certificato è associato all'ID Apple usato per crearlo. Come procedura consigliata, usare un ID Apple aziendale per le attività di gestione e verificare che la cassetta postale sia monitorata da più di una persona come una lista di distribuzione. Non usare mai un ID Apple personale.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>Passaggio 4. Immettere l'ID Apple usato per creare il certificato push MDM di Apple
Annotare questo ID per averlo a disposizione quando è necessario rinnovare il certificato.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>Passaggio 5. Passare al certificato push MDM di Apple da caricare
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push Intune può registrare e gestire i dispositivi Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Rinnovare il certificato push MDM Apple
Il certificato push MDM Apple è valido un anno e deve essere rinnovato annualmente per poter continuare la gestione dei dispositivi iOS e macOS. Se il certificato è scaduto, non è possibile contattare i dispositivi Apple registrati.

Il certificato è associato all'ID Apple usato per crearlo. Rinnovare il certificato push MDM con lo stesso ID Apple usato per crearlo.

1. Nel [portale di Azure](https://portal.azure.com) scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi scegliere il riquadro **Certificato push MDM Apple** nell'area dei dettagli.
2. Scegliere **Scarica CSR** per scaricare e salvare il file di richiesta in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.
3. Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Trovare il certificato da rinnovare e selezionare **Rinnova**.
4. Nella schermata **Rinnova il certificato push MDM** immettere una descrizione per identificare il certificato in futuro, selezionare **Scegli file** per trovare il nuovo file di richiesta scaricato e scegliere **Carica**.
   > [!TIP]
   > Un certificato può essere identificato dal relativo UID. Esaminare l'**ID oggetto** nei dettagli del certificato per individuare la parte GUID dell'UID. In alternativa, in un dispositivo iOS registrato, scegliere **Impostazioni** > **Generali** > **Gestione** **dispositivo** > **Profilo di gestione** > **Altri dettagli** > **Profilo di gestione**. La seconda voce, **Argomento**, contiene il GUID univoco che è possibile abbinare al certificato nel portale dei certificati push Apple.
 
6. Nella schermata **Conferma** selezionare **Scarica** e salvare il file PEM localmente.
7. Nel [portale di Azure](https://portal.azure.com) selezionare l'icona Sfoglia per **Certificato push MDM Apple**, selezionare il file PEM scaricato da Apple e scegliere **Carica**.

Il certificato push MDM Apple viene visualizzato come **Attivo** e sarà valido 365 giorni.
