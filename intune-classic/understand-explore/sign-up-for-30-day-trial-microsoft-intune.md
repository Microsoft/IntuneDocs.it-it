---
title: Iscriversi per una versione di valutazione gratuita di Microsoft Intune valida 30 giorni
description: Iscriversi per ottenere una versione di valutazione gratuita di Microsoft Intune valida 30 giorni.
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ffa07d5e36abc8686cedd600123494180c286011
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo articolo illustra come iscriversi per ottenere una versione di valutazione di Intune. Tale versione viene quindi preparata per l'uso con alcuni utenti, in modo che sia possibile seguire la guida di valutazione associata per comprendere il modo in cui Intune gestisce i dispositivi mobili. <!---or app data when devices are not enrolled in Intune.--->

>[!Note]
> A partire da dicembre 2016, Microsoft Intune verrà spostato nel portale di Azure e alcune iscrizioni per la versione di valutazione gratuita saranno in Intune nel portale di Azure e alcune in Intune classico. Se la versione di valutazione in uso è disponibile nel portale di Azure, il [contenuto relativo a Intune nella versione di anteprima del portale di Azure](/intune/what-is-intune) risulterà più utile dopo aver completato i passaggi descritti in questo articolo.

## <a name="assumptions"></a>Presupposti
Nella sezione relativa all'iscrizione e nella guida di valutazione si presuppone che la versione gratuita venga usata soltanto a scopo di valutazione. Si presuppone inoltre che, quando si esegue la sottoscrizione, si inizi con un ambiente "pulito".

Per facilitare l'utilizzo della versione di valutazione, viene impostato un ambiente molto semplice che usa esclusivamente Intune e presuppone che quest'ultimo sia l'unico metodo di gestione dei dispositivi (noto anche come autorità di gestione dei dispositivi mobili). Nel corso della guida, tuttavia, verranno forniti collegamenti a contenuti tecnici, da usare per uno studio più approfondito.

Con la versione di valutazione è possibile eseguire le stesse operazioni consentite da una versione in abbonamento. L'unica differenza è che la versione di valutazione è limitata a 100 account utente.

## <a name="sign-up-for-your-trial"></a>Iscriversi per la versione di valutazione gratuita
Visitare la pagina di [iscrizione a Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) e compilare il modulo per richiedere una sottoscrizione di valutazione.

Se si dispone già di un account aziendale o dell'istituto di istruzione e si vuole usare tale account per la versione di valutazione di Intune, seguire [queste istruzioni di iscrizione](/intune/account-sign-up). Questo articolo e la guida di valutazione, tuttavia, presuppongono che non venga usato questo tipo di account.

> [!TIP]
> Se per la maggior parte delle operazioni IT viene usata una lingua diversa dalla propria, è necessario specificare per la versione di valutazione le impostazioni locali appropriate, così da poter eseguire il test delle prestazioni.

### <a name="post-sign-up-considerations"></a>Considerazioni successive all'iscrizione
Quando si esegue l'iscrizione per una versione di valutazione, all'indirizzo di posta elettronica specificato in fase di iscrizione verrà inviato un messaggio contenente le informazioni sul proprio account. Questo messaggio conferma che la versione di valutazione è attiva.

Dopo aver completato il processo di iscrizione, si verrà indirizzati a una pagina usata per aggiungere utenti e assegnare loro licenze tramite l'interfaccia di amministrazione di Office 365. Al successivo accesso a **Intune classico** (https://manage.microsoft.com), l'utente verrà automaticamente indirizzato alla console di amministrazione di Intune.

Se la versione di valutazione è nel **portale di Azure**, passare a https://portal.azure.com e accedere con le credenziali di valutazione di Intune.

## <a name="add-users"></a>Aggiungere utenti
Prima di passare dall'interfaccia di amministrazione di Office 365 a Intune, è necessario aggiungere alcuni utenti all'account di valutazione.

Nell'interfaccia di amministrazione di Office 365 è possibile aggiungere utenti, sia singolarmente che in blocco, caricando un file con estensione csv. Per impostare la versione di valutazione verranno eseguite entrambe le operazioni. Nell'ambiente di produzione, tuttavia, è probabilmente preferibile usare gli account utente di Azure Active Directory. Per altre informazioni, vedere le sezioni [Guida introduttiva](/intune/users-permissions-add) e [Passaggi successivi](#next-steps) di questo articolo.

### <a name="add-an-individual-user"></a>Aggiungere un singolo utente
1. Scegliere una delle due opzioni per l'aggiunta di un utente per aprire un modulo che consente di creare un utente. Sono obbligatori soltanto gli elementi contrassegnati da un asterisco (\*).
![Immagine delle opzioni del pulsante Aggiungi utente](./media/sign-up/add-user.png)


2.  Quando si aggiunge un utente, come ultimo passaggio è necessario inviare a tale utente un messaggio di posta elettronica con la password temporanea di Intune. Ai fini di questa versione di valutazione, usare il proprio indirizzo di posta elettronica aziendale, così da ricevere le informazioni di accesso e visualizzare il messaggio che verrà inviato agli utenti. È quindi possibile usare queste identità utente per registrare i dispositivi di test.<br/>

 ![Immagine del passaggio finale di Aggiungi utente](./media/sign-up/new-user-2.png)

3. Se, dopo aver creato un utente, si vuole assegnargli un ruolo, è possibile modificare il ruolo nell'interfaccia di amministrazione di Office 365 selezionando il nome utente dall'elenco degli utenti e quindi scegliendo **Modifica** nella riga Ruolo. Viene visualizzato l'elenco dei ruoli da cui selezionare quello da assegnare all'utente.

 ![Immagine delle opzioni del ruolo utente](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>Importare più utenti
1. La procedura guidata per l'importazione di più utenti è disponibile nell'elenco **More** (Altro).

 ![Immagine dell'opzione per aggiungere più utenti](./media/sign-up/add-multiple-users.png)

2. Per impostare più facilmente il file con estensione CSV, è possibile scaricare un file modello da popolare con i dati degli utenti. Scaricare il file con estensione csv contenente le intestazioni e le informazioni utente di esempio per visualizzare esattamente il tipo di dati richiesto per ciascun campo.

 ![Immagine del primo passaggio nella procedura guidata di registrazione in blocco](./media/sign-up/bulk-enroll-step-1.png)


3. Dopo aver creato e salvato il file con estensione csv, scegliere **Sfoglia** per selezionare il file. Verificare e scegliere **Avanti**. Gli utenti verranno caricati e aggiunti all'elenco di utenti attivi.

> [!NOTE]
> Gli utenti non vengono visualizzati in Intune fino a quando non hanno registrato un dispositivo da gestire.

A questo punto, è necessario passare a Intune per iniziare a gestire gli utenti, i loro dispositivi e le loro applicazioni.

## <a name="keeping-the-admin-experiences-straight"></a>Esperienze diverse per l'amministrazione
### <a name="classic-intune"></a>Intune classico
Per Intune classico verranno usati due portali:
- L'interfaccia di amministrazione di Office 365 ([portal.office.com](https://portal.office.com))
- La console di amministrazione di Intune ([manage.microsoft.com](https://manage.microsoft.com))

In genere le operazioni vengono eseguite nella console di amministrazione di Intune, illustrata di seguito. Questa console consente infatti di impostare e gestire i gruppi, i criteri, i dispositivi e le app.

![Immagine della console di amministrazione di Intune](./media/sign-up/intune-admin-console.png)

Per aggiungere e gestire gli utenti e per altri aspetti dell'account, inclusi la fatturazione e il supporto, viene tuttavia usata l'interfaccia di amministrazione di Office 365, illustrata di seguito.

![Immagine dell'interfaccia di amministrazione di Office 365](./media/sign-up/office-admin-center.png)

È possibile passare dall'interfaccia di amministrazione di Office 365 alla console di amministrazione di Intune. Le interfacce di amministrazione si trovano sotto l'ultimo elemento nel riquadro si spostamento a sinistra. Scegliere **Intune** per aprire la console di amministrazione di Intune in una nuova scheda.

![Immagine del collegamento alla console di amministrazione di Intune](./media/sign-up/link-to-intune.png)

Per passare da Intune all'interfaccia di amministrazione di Office 365 Admin, scegliere l'attività **Aggiungi utenti** nella pagina Panoramica gruppi.

![Immagine del collegamento all'interfaccia di amministrazione di Office 365](./media/sign-up/task-add-users.png)

### <a name="intune-on-azure"></a>Intune in Azure
Per Intune in Azure verranno usati tre portali:
- L'interfaccia di amministrazione di Office 365 ([portal.office.com](https://portal.office.com))
- Il dashboard di Intune in Azure ([portal.azure.com](https://portal.azure.com))
- La console di amministrazione di Intune classico ([manage.microsoft.com](https://manage.microsoft.com))

Al primo accesso a Intune in Azure, potrebbe non essere visibile nel dashboard di Azure. Per aggiungere il servizio Intune al dashboard di Azure:
1. Scegliere **Altri servizi >** nell'elenco dei servizi di Azure a sinistra del dashboard e immettere Intune nella casella di ricerca.
2. Scegliere **Intune** nell'elenco e selezionare la stella per aggiungere il servizio all'elenco dei servizi.<br/> ![Immagine della selezione di Intune dall'elenco dei servizi](./media/sign-up/azure-add-intune1.png)
3. Scegliere **Intune** nell'elenco dei servizi per aprire il dashboard di Intune.

In genere le operazioni vengono eseguite nel dashboard di Intune, illustrato di seguito. Questa console consente infatti di impostare e gestire i gruppi, i criteri, i dispositivi e le app. È possibile passare alla console di amministrazione di Intune classico dal dashboard scegliendo il riquadro **Apri il portale classico di Intune**. Per tornare all'anteprima di Intune in Azure, immettere https://portal.azure.com nella barra degli indirizzi del browser e quindi scegliere di nuovo **Intune** nell'elenco dei servizi.

 ![Immagine del dashboard di Intune](./media/sign-up/intune-azure-dashboard.png)


Per aggiungere e gestire gli utenti e per altri aspetti dell'account, inclusi la fatturazione e il supporto, viene tuttavia usata l'interfaccia di amministrazione di Office 365, illustrata di seguito.

![Immagine dell'interfaccia di amministrazione di Office 365](./media/sign-up/office-admin-center.png)

Per passare dall'interfaccia di amministrazione di Office 365 al dashboard di Intune, immettere https://portal.azure.com nella barra degli indirizzi del browser. Scegliere **Intune** nell'elenco dei servizi.

Per tornare all'interfaccia di amministrazione di Office 365 da Intune, immettere https://portal.office.com nella barra degli indirizzi del browser. Se è già stato effettuato l'accesso in Intune, si passerà direttamente all'interfaccia di amministrazione di Office 365.

## <a name="next-steps"></a>Passaggi successivi
### <a name="classic-intune"></a>Intune classico
Scenario di valutazione: [Valutare la gestione dei dispositivi mobili in Microsoft Intune](mobile-device-management-trial-guide-microsoft-intune.md)

### <a name="intune-on-azure"></a>Intune in Azure
Altre informazioni su [Intune in Azure](/intune/what-is-intune)

### <a name="integration-with-other-products"></a>Integrazione con altri prodotti
Per altre informazioni sull'uso degli account utente di Azure Active Directory con Intune, vedere:
- [Identity requirements](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview) (Requisiti di identità)
- [Determinare i requisiti di sincronizzazione delle directory](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Determinare i requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Altre informazioni sull'uso di [Intune con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
