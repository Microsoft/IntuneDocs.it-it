---
title: Ottenere un certificato push MDM di Apple| Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: informazioni sulla procedura per ottenere un certificato push MDM di Apple per gestire i dispositivi iOS con Intune.'
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c0884ded1c8c55bb1b7968e483864b42f5bd6bde


---

# <a name="get-an-apple-mdm-push-certificate"></a>Ottenere un certificato push MDM di Apple 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune consente la gestione dei dispositivi mobili (MDM) iPad, iPhone e Mac OS X e offre agli utenti accesso alla posta elettronica e alle app aziendali. Affinché Intune gestisca i dispositivi iOS e Mac, è necessario un dispositivo Apple Push Notification Service. Dopo aver aggiunto il certificato a Intune, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi. In alternativa, è possibile configurare la gestione dei dispositivi iOS di proprietà dell'azienda.

**Per ottenere un certificato push MDM:**<br>

Nel portale di Azure scegliere **Altri servizi**, immettere **Intune** nella casella di testo e quindi scegliere **Altro** > **Intune**. Nel pannello Intune scegliere **Registra i dispositivi** > **Certificato push MDM Apple**, quindi seguire i passaggi numerati nel portale di Azure, illustrati di seguito.

**Passaggio 1. Scaricare la richiesta di firma del certificato di Intune necessaria per creare un certificato push MDM di Apple.**<br>
Selezionare **Scarica CSR** per scaricare e salvare il file con estensione csr in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

**Passaggio 2: Creare un certificato push MDM di Apple.**<br>
Selezionare **Crea il certificato push MDM** per passare al portale Apple Push Certificates. Accedere con il proprio ID Apple aziendale per creare il certificato push usando il file con estensione csr. Dopo aver scelto **Upload** (Carica) nel portale Apple Push Certificates si riceverà un file con estensione json. Usare questo file per il certificato push. Completare il download e tornare al portale Apple Push Certificates per i certificati per server di terze parti e quindi fare clic su **Scarica**. Scaricare il certificato push (file con estensione pem) e salvare il file in locale.
Nota

**Passaggio 3: Immettere l'ID Apple usato per creare il certificato push MDM di Apple.**

**Passaggio 4: Passare al certificato push MDM di Apple da caricare.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati.



<!--HONumber=Feb17_HO1-->


