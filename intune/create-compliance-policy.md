---
title: Criteri di conformità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni introduttive sull'utilizzo dei criteri di conformità, panoramica dei livelli di stato e gravità, uso dello stato Periodo di tolleranza, utilizzo dell'accesso condizionale, gestione dei dispositivi senza un criterio assegnato e differenze di conformità tra il portale di Azure e il portale classico in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0aa98774f25bf290391225c6ccae56a3859c22
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570416"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Creare criteri di conformità in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità dei dispositivi sono una funzionalità fondamentale quando si usa Intune per proteggere le risorse dell'organizzazione. In Intune è possibile creare regole e impostazioni che i dispositivi devono soddisfare per essere considerati conformi, ad esempio la versione minima del sistema operativo. Se il dispositivo non è conforme, è possibile bloccare l'accesso ai dati e alle risorse tramite l'[accesso condizionale](conditional-access.md).

È anche possibile eseguire azioni specifiche in caso di mancata conformità, ad esempio inviare una notifica tramite posta elettronica all'utente. Per una panoramica degli effetti dei criteri di conformità e delle modalità di utilizzo, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md).

Questo articolo:

- Illustra i prerequisiti e i passaggi da eseguire per creare criteri di conformità.
- Illustra come assegnare i criteri ai gruppi di utenti e di dispositivi.
- Descrive altre funzionalità, tra cui i tag di ambito per "filtrare" i criteri e le operazioni che è possibile eseguire sui dispositivi non conformi.
- Elenca la frequenza dei cicli di aggiornamento quando i dispositivi ricevono aggiornamenti dei criteri.

## <a name="before-you-begin"></a>Prima di iniziare

Per usare criteri di conformità del dispositivo, attenersi a quanto segue:

- Uso delle sottoscrizioni seguenti:

  - Intune
  - Se si usa l'accesso condizionale è necessario Azure Active Directory (AD) Premium. La pagina [Prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) spiega cosa si ottiene con le diverse edizioni. Azure AD non è necessario per la conformità di Intune.

- Uso di una piattaforma supportata:

  - Android
  - Android Enterprise
  - iOS
  - macOS (anteprima)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Registrazione dei dispositivi in Intune (necessaria per visualizzarne lo stato di conformità)

- Registrazione dei dispositivi per un solo utente o senza un utente primario. Non sono supportati dispositivi registrati per più utenti.

## <a name="create-the-policy"></a>Creare i criteri

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Conformità del dispositivo**. Sono disponibili le seguenti opzioni:

    - **Panoramica**: mostra un riepilogo e il numero di dispositivi conformi, non valutati e così via. Elenca anche i criteri e le singole impostazioni dei criteri. Per informazioni utili, vedere [Monitorare i criteri di conformità dei dispositivi di Intune](compliance-policy-monitor.md).
    - **Gestione**: consente di creare criteri per i dispositivi, inviare [notifiche](quickstart-send-notification.md) ai dispositivi non conformi e abilitare la [limitazione della rete](use-network-locations.md).
    - **Monitoraggio**: consente di controllare lo stato di conformità dei dispositivi, a livello di impostazione e di criterio. Per altre informazioni, vedere [Monitorare i criteri di conformità dei dispositivi di Intune](compliance-policy-monitor.md). Consente anche di visualizzare i log e di controllare lo stato dell'agente delle minacce dei dispositivi.
    - **Configurazione**: consente di usare i [criteri di conformità predefiniti](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), abilitare [Windows Defender Advanced Threat Protection (ATP)](advanced-threat-protection.md) aggiungere un [connettore di Mobile Threat Defense](mobile-threat-defense.md) e usare [Jamf](conditional-access-integrate-jamf.md).

3. Selezionare **Criteri** > **Crea criterio**. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di criterio è **Dispositivi iOS jailbroken di Marco non conformi**.
    - **Description**: immettere una descrizione del criterio. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

    - **Impostazioni**: gli articoli seguenti elencano e descrivono le impostazioni per ogni piattaforma:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1, Windows 8.1 versioni successive](compliance-policy-create-windows-8-1.md)
        - [Windows 10 e versioni successive](compliance-policy-create-windows.md)

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche. Il criterio viene creato e visualizzato nell'elenco. Assegnare quindi il criterio ai gruppi.

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Una volta creato un criterio, il passaggio successivo consiste nell'assegnarlo ai propri gruppi:

1. Scegliere un criterio precedentemente creato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e quindi **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e quindi scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. Verrà eseguita la valutazione della conformità dei dispositivi usati dagli utenti a cui il criterio è destinato.

### <a name="evaluate-how-many-users-are-targeted"></a>Valutare il numero di utenti interessati

Quando si assegna il criterio, è anche possibile usare la funzionalità **Valuta** per calcolare il numero di utenti interessati. Questa funzionalità calcola gli utenti, non i dispositivi.

1. In Intune selezionare **Conformità del dispositivo** > **Criteri**.
2. Selezionare un criterio e quindi **Assegnazioni** > **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti interessati da questo criterio.

Se il pulsante **Valuta** è disattivato, verificare che il criterio sia assegnato a uno o più gruppi.

## <a name="actions-for-noncompliance"></a>Azioni per la mancata conformità

Per i dispositivi che non soddisfano i criteri di conformità, è possibile aggiungere una sequenza di azioni da applicare automaticamente. Se il dispositivo è contrassegnato come non conforme, è possibile modificare la pianificazione, ad esempio dopo un giorno. È anche possibile configurare una seconda azione con cui inviare un messaggio di posta elettronica all'utente se il dispositivo risulta non conforme.

[Aggiungere azioni per dispositivi non conformi](actions-for-noncompliance.md) offre altre informazioni, tra cui come creare un messaggio di posta elettronica di notifica per gli utenti.

Si supponga, ad esempio, di usare la funzionalità Percorsi e di aggiungere un percorso in un criterio di conformità. L'azione predefinita per la mancata conformità viene applicata quando si seleziona almeno un percorso. Se il dispositivo non è connesso ai percorsi selezionati, viene immediatamente considerato non conforme. È possibile concedere agli utenti un periodo di tolleranza, ad esempio un giorno.

## <a name="scope-tags"></a>Tag di ambito

I tag di ambito sono un metodo molto efficiente per assegnare e filtrare criteri a gruppi specifici, ad esempio ai reparti Vendite o Risorse umane, ai dipendenti di una filiale e così via. Dopo aver aggiunto le impostazioni, si può anche aggiungere un tag di ambito ai criteri di conformità. Per altre informazioni, vedere [Filtrare i criteri con tag di ambito](scope-tags.md).

## <a name="refresh-cycle-times"></a>Frequenza dei cicli di aggiornamento

Durante il controllo della conformità, Intune usa lo stesso ciclo di aggiornamento dei profili di configurazione. In genere, la frequenza è la seguente:

| Piattaforma | Ciclo di aggiornamento|
| --- | --- |
| iOS | Ogni 6 ore |
| macOS | Ogni 6 ore |
| Android | Ogni 8 ore |
| PC Windows 10 registrati come dispositivi | Ogni 8 ore |
| Windows Phone | Ogni 8 ore |
| Windows 8.1 | Ogni 8 ore |

Se il dispositivo è stato registrato di recente, il controllo della conformità viene eseguito con maggiore frequenza:

| Piattaforma | Frequenza |
| --- | --- |
| iOS | Ogni 15 minuti per 6 ore e quindi ogni 6 ore |  
| macOS | Ogni 15 minuti per 6 ore e quindi ogni 6 ore | 
| Android | Ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| PC Windows 10 registrati come dispositivi | Ogni 3 minuti per 30 minuti e quindi ogni 8 ore | 
| Windows Phone | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| Windows 8.1 | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 

Gli utenti possono aprire in qualsiasi momento l'app Portale aziendale e sincronizzare il dispositivo in modo che controlli immediatamente la disponibilità di un criterio.

### <a name="assign-an-ingraceperiod-status"></a>Assegnare uno stato InGracePeriod

Lo stato InGracePeriod è un valore dei criteri di conformità. Questo valore è determinato dalla combinazione del periodo di tolleranza del dispositivo e dello stato effettivo del dispositivo per tale criterio di conformità.

In particolare, se un dispositivo presenta uno stato NonCompliant per un criterio di conformità assegnato e:

- al dispositivo non è stato assegnato alcun periodo di tolleranza, quindi il valore assegnato per il criterio di conformità è NonCompliant
- il dispositivo ha un periodo di tolleranza scaduto, quindi il valore assegnato per il criterio di conformità è NonCompliant
- il dispositivo ha un periodo di tolleranza futuro, quindi il valore assegnato per il criterio di conformità è InGracePeriod

Nella tabella seguente sono riassunte le varie situazioni:

|Stato di conformità attuale|Valore del periodo di tolleranza assegnato|Stato di conformità effettivo|
|---------|---------|---------|
|NonCompliant |Nessun periodo di tolleranza assegnato |NonCompliant |
|NonCompliant |Data trascorsa|NonCompliant|
|NonCompliant |Data futura|InGracePeriod|

Per altre informazioni sul monitoraggio dei criteri di conformità dei dispositivi, vedere [Monitorare i criteri di conformità dei dispositivi di Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Assegnare uno stato dei criteri di conformità risultante

Se un dispositivo ha più criteri di conformità e il dispositivo presenta stati di conformità diversi per due o più dei criteri di conformità assegnati, verrà assegnato un unico stato di conformità risultante. Questa assegnazione si basa su un livello di gravità concettuale assegnato a ogni stato di conformità. I livelli di gravità di ogni stato di conformità sono i seguenti:

|Stato  |Gravità  |
|---------|---------|
|Sconosciuto     |1|
|NotApplicable     |2|
|Conforme|3|
|InGracePeriod|4|
|NonCompliant|5|
|Errore|6|

Quando un dispositivo ha più criteri di conformità, viene assegnato il livello di gravità massimo di tutti i criteri per quel dispositivo.

Ad esempio, un dispositivo ha tre criteri di conformità: uno con stato Sconosciuto (gravità = 1), uno con stato Conforme (gravità = 3) e uno con stato Periodo di tolleranza (gravità = 4). Lo stato Periodo di tolleranza ha il livello di gravità più alto. Tutti e tre i criteri hanno quindi lo stato di conformità Periodo di tolleranza.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare i criteri](compliance-policy-monitor.md).