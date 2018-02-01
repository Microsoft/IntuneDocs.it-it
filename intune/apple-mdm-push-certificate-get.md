---
title: Ottenere un certificato push MDM di Apple
titlesuffix: Azure portal
description: Informazioni sulla procedura per ottenere un certificato push MDM di Apple per gestire i dispositivi iOS con Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8fca2a1f32cd15752758802ee6ae44b8ae33b696
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="get-an-apple-mdm-push-certificate"></a>Ottenere un certificato push MDM di Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad, iPhone e computer Mac e offre agli utenti l'accesso alla posta elettronica e alle app aziendali. Per consentire a Intune di gestire dispositivi iOS e Mac, è necessario un certificato Push MDM. Dopo aver aggiunto il certificato a Intune, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi. È anche possibile configurare la gestione dei dispositivi iOS di proprietà dell'azienda usando Apple Device Enrollment Program o registrare i dispositivi con Apple Configurator. Per altre informazioni sulle opzioni di registrazione, vedere [Scegliere come registrare i dispositivi iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Passaggi per ottenere il certificato
Nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** **Certificato push MDM Apple** e quindi seguire questa procedura nel portale di Azure.

**Passaggio 1. Scaricare la richiesta di firma del certificato di Intune necessaria per creare un certificato push MDM di Apple.**<br>
Selezionare **Scarica CSR** per scaricare e salvare il file di richiesta in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

  ![Screenshot che illustra la schermata Configura il certificato push MDM con l'opzione Push MDM non impostata.](./media/create-mdm-push-certificate.png)

**Passaggio 2: Creare un certificato push MDM di Apple.**<br>
Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Accedere con l'ID Apple aziendale e fare clic su **Crea un certificato**. Selezionare **Scegli file**, individuare il file di richiesta di firma del certificato e scegliere **Invia**. Nella pagina di conferma scegliere **Download** per scaricare il file del certificato (con estensione PEM), quindi salvare il file in locale.

> [!NOTE]
> Il certificato è associato all'ID Apple usato per crearlo. La procedura consigliata è usare un ID Apple aziendale per attività di gestione. Non usare mai un ID Apple personale.

**Passaggio 3: Immettere l'ID Apple usato per creare il certificato push MDM di Apple.**<br>
Annotare questo ID per averlo a disposizione quando è necessario rinnovare il certificato.

**Passaggio 4: Passare al certificato push MDM di Apple da caricare.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push Intune può registrare e gestire i dispositivi Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Rinnovare il certificato push MDM Apple
Il certificato push MDM Apple è valido un anno e deve essere rinnovato annualmente per poter continuare la gestione dei dispositivi iOS e macOS. Se il certificato è scaduto, non è possibile contattare i dispositivi Apple registrati.

Il certificato è associato all'ID Apple usato per crearlo. Rinnovare il certificato push MDM con lo stesso ID Apple usato per crearlo.

1. Nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi scegliere **Certificato push MDM Apple**.
2. Scegliere **Scarica CSR** per scaricare e salvare il file di richiesta in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.
3. Trovare il certificato da rinnovare e selezionare **Rinnova**.
4. Nella schermata **Renew Push Certificate** (Rinnova certificato push) immettere una descrizione per identificare il certificato in futuro, selezionare **Scegli file** per trovare il nuovo file di richiesta e scegliere **Carica**.
   > [!TIP]
   > Un certificato può essere identificato dal relativo UID. Esaminare l'**ID oggetto** nei dettagli del certificato per individuare la parte GUID dell'UID. In alternativa, in un dispositivo iOS registrato, scegliere **Impostazioni** > **Generali** > **Gestione** **dispositivo** > **Profilo di gestione** > **Altri dettagli** > **Profilo di gestione**. La seconda voce, **Argomento**, contiene il GUID univoco che è possibile abbinare al certificato nel portale dei certificati push Apple.
 
6. Nella schermata **Conferma** selezionare **Scarica** e salvare il file PEM localmente.
7. Nel portale di Azure selezionare l'icona Sfoglia del **certificato push MDM Apple**, selezionare il file PEM scaricato da Apple e scegliere **Carica**.

Il certificato push MDM Apple viene visualizzato come **Attivo** e sarà valido 365 giorni.
