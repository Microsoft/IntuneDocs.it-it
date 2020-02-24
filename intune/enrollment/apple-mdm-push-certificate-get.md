---
title: Ottenere un certificato push MDM Apple per Intune
titleSuffix: ''
description: Ottenere un certificato push MDM Apple per gestire i dispositivi iOS/iPadOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 673f63194b46ca7e4dbf1206d363cbe70c6e6098
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414435"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Ottenere un certificato push MDM di Apple

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Per consentire a Intune di gestire dispositivi iOS/iPadOS e macOS, è necessario un certificato push Apple MDM. Dopo aver aggiunto il certificato a Intune, gli utenti possono registrare i propri dispositivi usando:

- L'app Portale aziendale.

- I metodi di registrazione in blocco Apple, come Device Enrollment Program, Apple School Manager o Apple Configurator.

Per altre informazioni sulle opzioni di registrazione, vedere [Scegliere come registrare i dispositivi iOS/iPadOS](ios-enroll.md).

Quando un certificato push scade, è necessario rinnovarlo. Per il rinnovo, assicurarsi di usare lo stesso ID Apple usato per la creazione del certificato push.


## <a name="steps-to-get-your-certificate"></a>Passaggi per ottenere il certificato
Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Dispositivi** > **Registra i dispositivi** > **Registrazione Apple** > **Certificato push MDM Apple** e quindi seguire questa procedura.

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Passaggio 1. Concedere a Microsoft l'autorizzazione per l'invio di informazioni sugli utenti e i dispositivi ad Apple
Selezionare **Accetto.** per concedere a Microsoft l'autorizzazione per l'invio di dati ad Apple.

![Schermata Configura il certificato push MDM con l'opzione Push MDM non impostata.](./media/apple-mdm-push-certificate-get/create-mdm-push-certificate.png)

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
Il certificato push MDM Apple è valido un anno e deve essere rinnovato annualmente per poter continuare la gestione dei dispositivi iOS/iPadOS e macOS. Se il certificato è scaduto, non è possibile contattare i dispositivi Apple registrati.

Il certificato è associato all'ID Apple usato per crearlo. Rinnovare il certificato push MDM con lo stesso ID Apple usato per crearlo.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Dispositivi** > **Registra i dispositivi** > **Registrazione Apple** > **Certificato push MDM Apple**.
2. Scegliere **Scarica CSR** per scaricare e salvare il file di richiesta in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.
3. Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Trovare il certificato da rinnovare e selezionare **Rinnova**.
4. Nella schermata **Rinnova il certificato push MDM** immettere una descrizione per identificare il certificato in futuro, selezionare **Scegli file** per trovare il nuovo file di richiesta scaricato e scegliere **Carica**.
   > [!TIP]
   > Un certificato può essere identificato dal relativo UID. Esaminare l'**ID oggetto** nei dettagli del certificato per individuare la parte GUID dell'UID. In alternativa, in un dispositivo iOS/iPadOS registrato scegliere **Impostazioni** > **Generali** > **Gestione** **dispositivo** > **Profilo di gestione** > **Altri dettagli** > **Profilo di gestione**. La seconda voce, **Argomento**, contiene il GUID univoco che è possibile abbinare al certificato nel portale dei certificati push Apple.
 
6. Nella schermata **Conferma** selezionare **Scarica** e salvare il file PEM localmente.
7. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare l'icona Sfoglia per **Certificato push MDM Apple**, selezionare il file con estensione PEM scaricato da Apple e scegliere **Carica**.

Il certificato push MDM Apple viene visualizzato come **Attivo** e sarà valido 365 giorni.
