---
title: Installare le app di Office 365 nei dispositivi mobili usando Intune
titlesuffix: Azure portal
description: "Informazioni su come usare Intune per renderne più semplice l'installazione delle app di Office 365 nei dispositivi Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f1958e4a0fb5aeba3225ee7ea5fae1e7fb39db3
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>Come assegnare le app di Office 365 ProPlus 2016 ai dispositivi Windows 10 con Microsoft Intune

Questo tipo di app semplifica l'assegnazione delle app Office 365 ProPlus 2016 ai dispositivi gestiti che eseguono Windows 10. È anche possibile installare app per il client per desktop di Microsoft Project Online e Microsoft Visio Pro for Office 365 se si è proprietari delle relative licenze. Le app desiderate vengono visualizzate come unica voce nell'elenco delle app nella console di Intune.


## <a name="before-you-start"></a>Prima di iniziare

>[!IMPORTANT]
>Questo metodo di installazione di Office è supportato solo se non sono installate altre versioni di Microsoft Office nel dispositivo.

- È necessario che i dispositivi in cui vengono distribuite le app eseguano Windows 10 Creators Update o versioni successive.
- Intune supporta l'aggiunta di app di Office solo da Office 365 ProPlus 2016 Suite.
- Se sono aperte app di Office quando Intune installa l'insieme di app, è possibile che gli utenti finali perdano i dati dei file non salvati.
- Questo metodo di installazione non è supportato nei dispositivi Windows 10 S.
- Intune non consente di installare le app desktop di Office 365 da Windows Store (note come app Office Centennial) in un dispositivo a cui sono già state distribuite app di Office 365 con Intune. Se si installa questa configurazione, si potrebbero verificare perdite o danneggiamenti dei dati.


## <a name="get-started"></a>Introduzione

1.  Accedere al portale Azure.
2.  Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3.  Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4.  Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5.  In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6.  Nel pannello **Aggiungi app** scegliere **Office 365 ProPlus Suite (Windows 10)**.

## <a name="configure-the-app-suite"></a>Configurare la suite di app

In questo passaggio scegliere le app di Office che si vuole assegnare ai dispositivi.

1.  Nel pannello **Aggiungi app** scegliere **Configure App Suite** (Configura suite di app).
2.  Nel pannello **Configure App Suite** (Configura suite di app) scegliere le app di Office standard da assegnare ai dispositivi. È anche possibile installare app per il client per desktop di Microsoft Project Online e Microsoft Visio Pro for Office 365 se si è proprietari delle relative licenze.
3.  Al termine, fare clic su **OK**.

>[!IMPORTANT]
> Dopo aver creato la suite di app, non è possibile modificarne le proprietà. Per configurare proprietà diverse, eliminare la suite di app e crearne una nuova.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app

In questo passaggio specificare le informazioni sulla suite di app. Queste informazioni consentono di identificarla in Intune e permettono agli utenti di trovarla nell'app Portale aziendale.

1.  Nel pannello **Aggiungi app** scegliere **App Suite Information** (Informazioni sulla suite di app).
2.  Nel pannello **App Suite Information** (Informazioni sulla suite di app) specificare le informazioni seguenti: 
    - **Suite Name** (Nome suite): immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Suite Description** (Descrizione suite): immettere una descrizione per la suite di app. Ad esempio, è possibile elencare le app selezionate da includere.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata. L'uso delle categorie consente agli utenti di trovare più facilmente la suite di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza la suite di app in primo piano nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Carica icona**: caricare un'icona visualizzata con l'app dagli utenti nel portale aziendale.
3.  Al termine, fare clic su **OK**.

## <a name="configure-app-settings"></a>Configurare le impostazioni dell'app

In questo passaggio configurare le opzioni di installazione per la suite di app. Le impostazioni si applicano a tutte le app aggiunte alla suite.

1.  Nel pannello **Aggiungi app** scegliere **App Suite Settings** (Impostazioni suite di app).
2.  Nel pannello **App Suite Settings** (Impostazioni suite di app) specificare le informazioni seguenti: 
    - **Versione di Office**: scegliere se assegnare la versione a 32 bit o a 64 bit di Office. La versione a 32 bit può essere installata su dispositivi a 32 bit e a 64 bit, mentre la versione a 64 bit può essere installata solo su dispositivi a 64 bit.
    - **Canale di aggiornamento**: scegliere la modalità di aggiornamento di Office nei dispositivi. Per informazioni sui diversi canali di aggiornamento, vedere Panoramica dei canali di aggiornamento per Office 365 ProPlus. È possibile scegliere tra: 
        - **Current** (Corrente)
        - **Deferred** (Rinviato)
        - **First Release Current** (Prima versione corrente)
        - **First Release Deferred** (Prima versione rinviata)
    - **Automatically accept the app end user license agreement** (Accetta automaticamente il contratto di licenza con l'utente finale): selezionare questa opzione se non si richiede agli utenti finali di accettare il contratto di licenza. Intune accetterà automaticamente il contratto.
    - **Use shared computer activation** (Usa attivazione di computer condivisi): l'attivazione di computer condivisi viene usata quando più utenti condividono un computer. Per altre informazioni, vedere Panoramica dell'attivazione di computer condivisi per Office 365 ProPlus.
    - **Lingue**: Office viene installato automaticamente in tutte le lingue supportate installate con Windows nel dispositivo dell'utente finale. Selezionare questa opzione se si vuole installare lingue aggiuntive con la suite di app.

>[!IMPORTANT]
> Dopo aver creato la suite di app, non è possibile modificarne le proprietà. Per configurare proprietà diverse, eliminare la suite di app e crearne una nuova.

## <a name="finish-up"></a>Terminare

Al termine, nel pannello **Aggiungi app** scegliere **Salva**. L'app creata viene visualizzata nell'elenco di app.

## <a name="error-codes-when-installing-the-app-suite"></a>Codici di errore durante l'installazione della suite di app

La tabella seguente elenca i codici di errore comuni che possono essere visualizzati e il relativo significato.

### <a name="status-for-office-csp"></a>Stato di Office CSP: 

||||
|-|-|-|
|Stato|Fase|Descrizione|
|1460 (ERROR_TIMEOUT)|Download|Non è stato possibile scaricare lo strumento di distribuzione di Office|    
|13 (ERROR_INVALID_DATA)|-|Impossibile verificare la firma dello strumento di distribuzione di Office scaricato| 
|Codice di errore da CertVerifyCertificateChainPolicy|-|Controllo del certificato non riuscito per lo strumento di distribuzione di Office scaricato|    
|997|WIP|Installazione| 
|0|Dopo l'installazione|Installazione completata|    
|1603 (ERROR_INSTALL_FAILURE)|-|Non sono stati eseguiti tutti i controlli dei prerequisiti, ad esempio:<br>- SxS (È stata tentata l'installazione con la versione MSI 2016 installata)<br>- versione non corrispondente<br>- ecc.|     
|0x8000ffff (E_UNEXPECTED)|-|È stata tentata la disinstallazione senza Office a portata di clic disponibile nel computer.|    
|17002|-|Non è stato possibile completare lo scenario (installazione). Motivi possibili:<br>- Installazione annullata dall'utente<br>- Installazione annullata da un'altra installazione<br>- Spazio su disco insufficiente durante l'installazione<br>- ID lingua sconosciuto| 
|17004|-|SKU sconosciuti|   


### <a name="office-deployment-tool-error-codes"></a>Codici di errore dello strumento di distribuzione di Office

|||||
|-|-|-|-|
|Scenario|Codice restituito|Interfaccia utente|Nota| 
|Disinstallazione senza installazione A porta di clic attiva|-2147418113, 0x8000ffff o 2147549183|Codice di errore: 30088-1008<br>Codice di errore: 30125-1011 (404)|Strumento di distribuzione di Office| 
|Installazione con la versione MSI installata|1603|-|Strumento di distribuzione di Office| 
|Installazione annullata dall'utente o da un'altra installazione|17002|-|A portata di clic| 
|Tentativo di installazione della versione a 64 bit in un dispositivo in cui è installata la versione a 32 bit.|1603|-|Codice restituito dello strumento di distribuzione di Office| 
|Tentativo di installazione di un codice SKU sconosciuto (caso d'uso non legittimo per Office CSP poiché devono essere passati solo i codici SKU validi)|17004|-|A portata di clic| 
|Mancanza di spazio|17002|-|A portata di clic| 
|Il client a portata di clic non è stato avvisato (imprevisto)|17000|-|A portata di clic| 
|Il client a portata di clic non è stato inserito in coda (imprevisto)|17001|-|A portata di clic| 

## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare le app ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).