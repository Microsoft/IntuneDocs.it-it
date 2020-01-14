---
title: Scenario guidato - Proteggi le app di Office per dispositivi mobili
titleSuffix: Microsoft Intune
description: Informazioni sullo scenario guidato per la distribuzione di app per dispositivi mobili Microsoft Office sicure dal portale di gestione dei dispositivi per Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3399cf006543c0a3554c4c6ec812554462d74231
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691813"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Scenario guidato - Proteggi le app di Office per dispositivi mobili 

Seguendo questo scenario guidato nel portale di gestione dei dispositivi, è possibile abilitare la protezione delle app di Intune di base nei dispositivi iOS e Android.

La protezione delle app abilitata applicherà le azioni seguenti: 
- Crittografare i file di lavoro.
- Richiedere un PIN per accedere ai file di lavoro.
- Richiedere la reimpostazione del PIN dopo cinque tentativi non riusciti.
- Impedire il backup dei file di lavoro nei servizi di backup di iTunes, iCloud o Android.  
- Imporre il salvataggio dei file di lavoro solo in OneDrive o SharePoint.
- Impedire alle app protette di caricare file di lavoro nei dispositivi jailbroken o rooted.
- Impedire l'accesso ai file di lavoro se il dispositivo rimane offline per 720 minuti.
- Rimuovere i file di lavoro se il dispositivo rimane offline per 90 giorni. 

## <a name="background"></a>Informazioni di base

Le app per dispositivi mobili di Office e Microsoft Edge per dispositivi mobili supportano la doppia identità. La doppia identità consente alle app di gestire i file di lavoro separatamente dai file personali. 

![Immagine dei dati aziendali rispetto ai dati personali](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

I [criteri di protezione delle app di Intune](~/apps/app-protection-policy.md) consentono di proteggere i file di lavoro nei dispositivi registrati in Intune. I criteri di protezione delle app possono essere usati anche nei dispositivi di proprietà dei dipendenti non registrati per la gestione in Intune. In questo caso, anche se il dispositivo non viene gestito dall'azienda, è comunque necessario assicurarsi che i file e le risorse di lavoro siano protetti.

È possibile usare i criteri di protezione delle app per impedire agli utenti di salvare i file di lavoro in posizioni non protette. È anche possibile limitare lo spostamento dei dati ad altre app non protette dai criteri di protezione delle app. Le impostazioni dei criteri di protezione delle app includono:
- Criteri di rilocazione dei dati, ad esempio **Salva copie dei dati dell'organizzazione** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso per richiedere un PIN semplice per l'accesso e per bloccare l'esecuzione delle app gestite nei dispositivi jailbroken o rooted.

L'accesso condizionale basato su app e la gestione delle app client consentono di aggiungere un livello di sicurezza, garantendo che solo le app client che supportano i criteri di protezione delle app di Intune possano accedere a Exchange Online e agli altri servizi di Office 365.

Consentendo solo all'app Microsoft Outlook di accedere a Exchange Online, è possibile bloccare le app di posta elettronica predefinite in iOS e Android. È inoltre possibile impedire di accedere a SharePoint Online alle app a cui non sono applicati criteri di protezione delle app di Intune.

In questo esempio, l'amministratore ha applicato criteri di protezione delle app all'app Outlook, seguiti da una regola di accesso condizionale che aggiunge l'app Outlook a un elenco approvato di app che possono essere usate per l'accesso alla posta elettronica aziendale.

![Flusso del processo di accesso condizionale dell'app Outlook](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Prerequisiti

Saranno necessarie le autorizzazioni di amministrazione di Intune seguenti:

   - App gestite: Lettura, Creazione, Eliminazione e Assegnazione
   - Set di criteri: Lettura, Creazione e Assegnazione
   - Organizzazione: Lettura

## <a name="step-1---introduction"></a>Passaggio 1 - Introduzione

Seguendo lo scenario guidato di **Protezione app di Intune** si eviteranno condivisioni o perdite dei dati all'esterno dell'organizzazione. 

Gli utenti iOS e Android assegnati devono immettere un PIN ogni volta che aprono un'app di Office. Dopo 5 tentativi di immissione del PIN non riusciti, gli utenti devono reimpostare il PIN. Se è già richiesto un PIN del dispositivo, questa impostazione non avrà effetto sugli utenti.

### <a name="what-you-will-need-to-continue"></a>Cosa serve per continuare

Verranno fornite informazioni sulle app richieste dagli utenti e sugli elementi necessari per accedervi. Assicurarsi di avere a portata di mano le informazioni seguenti:
- Elenco delle app di Office approvate per l'uso aziendale.
- Eventuali requisiti di PIN per l'avvio di app approvate su dispositivi non gestiti.

## <a name="step-2---basics"></a>Passaggio 2 - Informazioni di base

In questo passaggio è necessario immettere un **Prefisso** e una **Descrizione** per i nuovi criteri di protezione delle app. Quando si aggiunge il **Prefisso**, i dettagli relativi alle risorse create dallo scenario guidato verranno aggiornati. Questi dettagli semplificheranno la ricerca dei criteri in un secondo momento se è necessario modificare le assegnazioni e la configurazione. 

> [!TIP]
> Valutare la possibilità di prendere nota delle risorse che verranno create, in modo da potervi fare riferimento in un secondo momento.

## <a name="step-3---apps"></a>Passaggio 3 - App

Per iniziare, questo scenario guidato consente di pre-selezionare le app per dispositivi mobili seguenti per la protezione nei dispositivi iOS e Android:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Questo scenario guidato configurerà anche queste app per l'apertura dei collegamenti Web in Microsoft Edge in modo da garantire che i siti di lavoro vengano aperti in un browser protetto.

Modificare l'elenco delle app gestite da criteri che si vuole proteggere. Aggiungere o rimuovere app da questo elenco. 

Dopo aver selezionato le app fare clic su **Avanti**.

## <a name="step-4---configuration"></a>Passaggio 4 - Configurazione

In questo passaggio è necessario configurare i requisiti per l'accesso e la condivisione di file e messaggi di posta elettronica aziendali in queste app. Per impostazione predefinita, gli utenti possono salvare i dati negli account OneDrive e SharePoint dell'organizzazione.

| Impostazione | Descrizione | Valore predefinito |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Tipo di PIN | I PIN numerici sono costituiti solo da numeri. I passcode sono costituiti da caratteri alfanumerici e caratteri speciali.  In iOS/iPadOS per configurare il tipo di passcode, è necessario che l'app disponga di Intune SDK versione 7.1.12 o successiva. Per il tipo numerico non sono previste restrizioni di versione di Intune SDK. | Numerico |
| Selezionare la lunghezza minima del PIN | specificare il numero minimo di cifre in una sequenza di PIN. | 6 |
| Controlla di nuovo i requisiti di accesso dopo (minuti di inattività) | Se l'app gestita da criteri è inattiva per un periodo superiore al numero di minuti di inattività specificato, l'app richiederà che i requisiti di accesso (ad esempio PIN e impostazioni di avvio condizionale) vengano ricontrollati dopo l'avvio dell'app. | 30 |
| Stampa dei dati dell'organizzazione | Se viene impostato il blocco, l'app non può stampare i dati protetti. | Blocca |
| Open policy-managed app links in unmanaged browsers (Apri i collegamenti delle app gestite da criteri nei browser non gestiti) | Se viene impostato il blocco, i collegamenti delle app gestite da criteri devono essere aperti in un browser gestito. | Blocca |
| Copia i dati in app non gestite | Se viene impostato il blocco, i dati gestiti rimarranno nelle app gestite. | Consenti |

## <a name="step-5---assignments"></a>Passaggio 5 - Assegnazioni

In questo passaggio è possibile scegliere i gruppi di utenti che si vuole includere per assicurarsi che abbiano accesso ai dati aziendali. La protezione delle app viene assegnata agli utenti e non ai dispositivi, quindi i dati aziendali saranno sicuri indipendentemente dal dispositivo usato e dal relativo stato di registrazione.

Gli utenti a cui non sono assegnati criteri di protezione delle app e impostazioni di accesso condizionale potranno salvare i dati dal profilo aziendale nelle app personali e nello spazio di archiviazione locale non gestito nei dispositivi mobili. Potrebbero anche connettersi a servizi dati aziendali, come Microsoft Exchange, con le app personali.

## <a name="step-6---review--create"></a>Passaggio 6 - Verifica e creazione

Il passaggio finale consente di esaminare un riepilogo delle impostazioni configurate. Dopo aver verificato le scelte, fare clic su **Crea** per completare lo scenario guidato. Una volta completato lo scenario guidato, viene visualizzata una tabella di risorse. È possibile modificare queste risorse in un secondo momento, ma quando si esce dalla visualizzazione di riepilogo la tabella non verrà salvata.

> [!IMPORTANT]
> Una volta completato lo scenario guidato, verrà visualizzato un riepilogo. È possibile modificare le risorse elencate nel riepilogo in un secondo momento, ma la tabella che visualizza queste risorse non verrà salvata.
## <a name="next-steps"></a>Passaggi successivi

- Migliorare la sicurezza dei file di lavoro assegnando agli utenti un criterio di accesso condizionale basato su app per proteggere i servizi cloud dall'invio di file di lavoro ad app non protette. Per altre informazioni, vedere [Configurare criteri di accesso condizionale basato su app con Intune](~/protect/app-based-conditional-access-intune-create.md).

