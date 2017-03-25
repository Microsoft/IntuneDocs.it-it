---
title: Ottenere un certificato push MDM di Apple
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sulla procedura per ottenere un certificato push MDM di Apple per gestire i dispositivi iOS con Intune.'
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 82585886bb053d5b6b5981f61d0337fc6feffea4
ms.openlocfilehash: b26d66d557e084b5b328aec2222c50c2db254bf7
ms.lasthandoff: 03/14/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Ottenere un certificato push MDM di Apple

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad, iPhone e computer Mac e offre agli utenti l'accesso alla posta elettronica e alle app aziendali. Per consentire a Intune di gestire dispositivi iOS e Mac, è necessario un certificato Push MDM. Dopo aver aggiunto il certificato a Intune, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi. È anche possibile configurare la gestione dei dispositivi iOS di proprietà dell'azienda usando Apple Device Enrollment Program o registrare i dispositivi con Apple Configurator. Per altre informazioni sulle opzioni di registrazione, vedere [Scegliere come registrare i dispositivi iOS](https://docs.microsoft.com/intune-azure/enroll-devices/choose-ios-enrollment-method).

## <a name="steps-to-get-your-certificate"></a>Passaggi per ottenere il certificato
Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registra i dispositivi** > **Registrazione Apple** **Certificato push MDM Apple** e quindi seguire i passaggi numerati nel portale di Azure, come illustrato di seguito.

**Passaggio 1. Scaricare la richiesta di firma del certificato di Intune necessaria per creare un certificato push MDM di Apple.**<br>
Selezionare **Scarica CSR** per scaricare e salvare il file con estensione csr in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

**Passaggio 2: Creare un certificato push MDM di Apple.**<br>
Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Accedere con il proprio ID Apple aziendale per creare il certificato push usando il file con estensione csr. Dopo aver scelto **Upload** (Carica) nel portale Apple Push Certificates si riceverà un file con estensione json. Usare questo file per il certificato push. Completare il download e tornare al portale Apple Push Certificates per i certificati per server di terze parti e quindi fare clic su **Scarica**. Scaricare il certificato push (file con estensione pem) e salvare il file in locale.
Nota

**Passaggio 3: Immettere l'ID Apple usato per creare il certificato push MDM di Apple.**

**Passaggio 4: Passare al certificato push MDM di Apple da caricare.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati.

