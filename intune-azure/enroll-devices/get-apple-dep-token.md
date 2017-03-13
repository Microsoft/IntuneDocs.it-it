---
title: Ottenere un certificato DEP Apple per Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: istruzioni per la configurazione e il caricamento di un certificato push MDM, un prerequisito per la gestione dei dispositivi Apple in Intune. '
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>Ottenere un certificato DEP di Apple

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Per registrare i dispositivi iOS di proprietà dell'azienda con Device Enrollment Program (DEP) di Apple, è necessario un token DEP di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano al programma DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per gestire i dispositivi iOS di proprietà dell'azienda con DEP, le organizzazioni devono aderire al programma DEP di Apple e acquisire i dispositivi attraverso il programma. I dettagli del processo sono disponibili all'indirizzo: https://deploy.apple.com. I vantaggi del programma includono la configurazione dei dispositivi senza intervento dell'utente e senza dover connettere ogni dispositivo a un computer tramite un cavo USB.

> [!NOTE]
> Questa nota si applica solo ai clienti Intune che hanno eseguito la migrazione dalla console di amministrazione di Intune al portale di Azure. Se un token DEP Apple è stato eliminato dalla console di amministrazione di Intune durante il periodo di migrazione, è possibile che sia stato ripristinato nel proprio account di Intune. In questo caso è sufficiente eliminare il token DEP dal portale di Azure.

## <a name="steps-to-get-the-apple-dep-certificate"></a>Passaggi per ottenere il certificato DEP Apple
Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registra i dispositivi** > **Token DEP Apple**, quindi seguire i passaggi numerati nel portale di Azure, illustrati di seguito.

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token DEP Apple.**<br>
Selezionare **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

**Passaggio 2: Scaricare un token DEP Apple dal sito Web Apple appropriato.**<br>
Selezionare [Creare un token DEP tramite i programmi di distribuzione Apple](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale. Lo stesso ID Apple dovrà essere usato per rinnovare il token DEP.

   a.  Nel [portale del programma di registrazione dispositivi](https://deploy.apple.com) passare a **Programma di registrazione dispositivi** &gt; **Gestisci server** e fare clic sull'opzione **Aggiungi server MDM**.

   b.  Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.

   c.  Si apre la finestra di dialogo **Aggiungi &lt;NomeServer&gt;**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.

   d.  La finestra di dialogo **Aggiungi &lt;Nome Server&gt;** include un collegamento al **Token del server**. Scaricare il file token del server (con estensione p7m) nel computer e fare clic su **Fine**.

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**Passaggio 3: Immettere l'ID Apple usato per creare il token DEP Apple. Questo ID può essere usato per rinnovare il token.**

**Passaggio 4: Passare al token DEP Apple da caricare. Intune eseguirà automaticamente la sincronizzazione con l'account DEP.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati.

