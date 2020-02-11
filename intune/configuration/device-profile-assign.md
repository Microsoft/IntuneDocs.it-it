---
title: Assegnare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Usare l'interfaccia di amministrazione di Microsoft Endpoint Manager per assegnare criteri e profili di dispositivo a utenti e dispositivi. Informazioni su come escludere gruppi da un'assegnazione di profilo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b61c333f41054194b44c7517e508fe1ef6d28d4
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812378"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Assegnare profili utente e profili di dispositivo in Microsoft Intune

Dopo aver creato un profilo, completo di tutte le impostazioni specificate, il passaggio successivo consiste nel distribuire o "assegnare" il profilo ai gruppi di utenti o di dispositivi di Azure Active Directory (Azure AD). Con l'assegnazione, gli utenti e i dispositivi ricevono il profilo e vengono applicate le impostazioni specificate.

Questo articolo illustra come assegnare un profilo e include alcune informazioni sull'uso dei tag di ambito nei profili.

> [!NOTE]  
> Quando un profilo viene rimosso o non è più assegnato a un dispositivo, si possono verificare situazioni diverse, a seconda delle impostazioni presenti nel profilo. Le impostazioni si basano sui provider di servizi di configurazione (CSP) e ogni CSP può gestire la rimozione del profilo in modo diverso. Ad esempio, un'impostazione potrebbe mantenere il valore esistente e non tornare a un valore predefinito. Il comportamento è controllato da ogni CSP nel sistema operativo. Per un elenco di CSP di Windows, vedere il [riferimento sui provider di servizi di configurazione (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).
>
> Per modificare un'impostazione e usare un valore diverso, creare un nuovo profilo, configurare l'impostazione su **Non configurato** e assegnare il profilo. Dopo l'applicazione al dispositivo, gli utenti devono essere in grado di modificare l'impostazione scegliendo il valore preferito.
>
> Quando si configurano queste impostazioni, è consigliabile distribuirle a un gruppo pilota. Per altre indicazioni sull'implementazione, vedere le [istruzioni per la creazione di un piano di implementazione](../fundamentals/planning-guide-rollout-plan.md).

## <a name="before-you-begin"></a>Prima di iniziare

Assicurarsi di avere il ruolo appropriato per assegnare i profili. Per altre informazioni, vedere [Controllo degli accessi in base al ruolo (RBAC) con Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Assegnare un profilo di dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione**. Vengono elencati tutti i profili.
3. Selezionare il profilo che si vuole assegnare e quindi selezionare **Assegnazioni**.
4. Scegliere **Includi** o **Escludi**, quindi selezionare i gruppi da includere o escludere. Quando si selezionano i gruppi, si sceglie un gruppo di Azure AD. Per selezionare più gruppi, tenere premuto **CTRL** e selezionare i gruppi.

    ![Screenshot delle opzioni per includere o escludere i gruppi da un'assegnazione di profilo](./media/device-profile-assign/group-include-exclude.png)

5. **Salvare** le modifiche.

### <a name="evaluate-how-many-users-are-targeted"></a>Valutare il numero di utenti interessati

Quando si assegna il profilo, è anche possibile usare la funzionalità **Valuta** per calcolare il numero di utenti interessati. Questa funzionalità calcola gli utenti, non i dispositivi.

1. Nell'interfaccia di amministrazione selezionare **Dispositivi** > **Profili di configurazione**.
2. Selezionare un profilo e quindi **Assegnazioni** > **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti interessati da questo profilo.

Se il pulsante **Valuta** è disattivato, verificare che il profilo sia assegnato a uno o più gruppi.

## <a name="use-scope-tags-or-applicability-rules"></a>Usare i tag di ambito o le regole di applicabilità

Durante la creazione o l'aggiornamento di un profilo è anche possibile aggiungere tag di ambito e regole di applicabilità.

I **tag di ambito** sono un ottimo modo per filtrare i profili in base a gruppi specifici, ad esempio `US-NC IT Team` o `JohnGlenn_ITDepartment`. Per altre informazioni, vedere [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

Nei dispositivi Windows 10 è possibile aggiungere **regole di applicabilità**, in modo che il profilo venga applicato solo a una versione specifica del sistema operativo o a un'edizione specifica di Windows. Per altre informazioni, vedere [Regole di applicabilità](device-profile-create.md#applicability-rules).

## <a name="user-groups-vs-device-groups"></a>Gruppi di utenti e gruppi di dispositivi

Molti utenti vogliono sapere quando usare i gruppi di utenti e quando usare i gruppi di dispositivi. La risposta dipende dall'obiettivo dell'utente. Ecco alcune indicazioni per iniziare.

### <a name="device-groups"></a>Gruppi di dispositivi

Se si vogliono applicare impostazioni in un dispositivo, indipendentemente dall'utente che esegue l'accesso, assegnare i profili a un gruppo di dispositivi. Le impostazioni applicate ai gruppi di dispositivi si riferiscono sempre al dispositivo e non all'utente.

Ad esempio:

- I gruppi di dispositivi sono utili per gestire i dispositivi che non hanno un utente dedicato. Si hanno ad esempio dispositivi che stampano ticket, analizzano l'inventario, vengono condivisi da dipendenti che lavorano a turni, sono assegnati a un magazzino specifico e così via. Inserire questi dispositivi in un gruppo di dispositivi e assegnare i profili a questo gruppo di dispositivi.

- Si crea un [profilo di Intune DFCI (Device Firmware Configuration Interface, Interfaccia di configurazione del firmware del dispositivo](device-firmware-configuration-interface-windows.md)) che aggiorna le impostazioni nel BIOS. Si configura ad esempio questo profilo per disabilitare la fotocamera del dispositivo o bloccare le opzioni di avvio per impedire agli utenti di avviare un altro sistema operativo. Questo profilo è uno scenario valido da assegnare a un gruppo di dispositivi.

- In alcuni dispositivi Windows specifici è sempre necessario controllare alcune impostazioni Microsoft Edge, indipendentemente dall'utente che usa il dispositivo. Si vuole ad esempio bloccare tutti i download, limitare tutti i cookie alla sessione di esplorazione corrente ed eliminare la cronologia esplorazioni. Per questo scenario, inserire questi dispositivi Windows specifici in un gruppo di dispositivi. Creare quindi un [modello amministrativo in Intune](administrative-templates-windows.md), aggiungere queste impostazioni dispositivo e assegnare questo profilo al gruppo di dispositivi.

Per riepilogare, usare i gruppi di dispositivi quando non è importante chi esegue l'accesso o se qualcuno ha eseguito l'accesso al dispositivo. Si vuole che le impostazioni accompagnino sempre il dispositivo.

### <a name="user-groups"></a>Gruppi di utenti

Le impostazioni del profilo applicate ai gruppi di utenti si abbinano all'utente e lo accompagnano quando esegue l'accesso ai diversi dispositivi. È normale che gli utenti abbiano molti dispositivi, ad esempio un dispositivo Surface Pro per il lavoro e un dispositivo iOS per uso personale. È normale che un utente acceda alla posta elettronica e ad altre risorse dell'organizzazione da questi dispositivi.

Ad esempio:

- Si vuole inserire un'icona Help Desk in tutti i dispositivi di tutti gli utenti. In questo scenario inserire questi utenti in un gruppo di utenti e assegnare il profilo dell'icona Help Desk a questo gruppo di utenti.
- Un utente riceve un nuovo dispositivo di proprietà dell'organizzazione. L'utente accede al dispositivo usando il proprio account di dominio. Il dispositivo viene registrato automaticamente in Azure AD e gestito automaticamente da Intune. Questo profilo è uno scenario valido da assegnare a un gruppo di utenti.
- Ogni volta che un utente accede a un dispositivo, si vogliono controllare le funzionalità nelle app, ad esempio OneDrive oppure Office. In questo scenario assegnare le impostazioni del profilo di OneDrive o Office a un gruppo di utenti.

  Si vuole ad esempio bloccare i controlli ActiveX non attendibili nelle app di Office. È possibile creare un [modello amministrativo in Intune](administrative-templates-windows.md), configurare questa impostazione e assegnare questo profilo al gruppo di utenti.

Per riepilogare, usare i gruppi di utenti quando si vuole che le impostazioni siano applicate sempre all'utente, indipendentemente dal dispositivo usato.

## <a name="exclude-groups-from-a-profile-assignment"></a>Escludere gruppi da un'assegnazione di profilo

I profili di configurazione dei dispositivi Intune consentono di includere ed escludere gruppi dall'assegnazione del profilo.

Come procedura consigliata, creare e assegnare profili specifici per i gruppi di utenti e creare e assegnare profili diversi specificamente per i gruppi di dispositivi. Per altre informazioni sui gruppi, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](../fundamentals/groups-add.md).

Quando si assegnano i profili, usare la tabella seguente per includere ed escludere i gruppi. Un segno di spunta indica che l'assegnazione è supportata.

![Opzioni supportate per includere o escludere gruppi da un'assegnazione di profilo](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Informazioni importanti

- L'esclusione ha la precedenza sull'inclusione negli scenari seguenti, relativi a gruppi dello stesso tipo:

  - Inclusione di gruppi utenti ed esclusione di gruppi utenti
  - Inclusione di gruppi di dispositivi ed esclusione di gruppi di dispositivi

  Ad esempio si assegna un profilo di dispositivo al gruppo di utenti **Tutti gli utenti aziendali**, ma si escludono i membri del gruppo **Dirigenti**. Poiché entrambi i gruppi sono gruppi di utenti, il profilo interessa **Tutti gli utenti aziendali** ad eccezione dei **Dirigenti**.

- Intune non valuta le relazioni di gruppi di utenti e dispositivi. Se si assegnano profili a gruppi misti, i risultati potrebbero non essere quelli voluti o previsti.

  Si supponga, ad esempio, di assegnare un profilo di dispositivo al gruppo utenti **Tutti gli utenti**, escludendo però il gruppo di dispositivi **Tutti i dispositivi personali**. In questa assegnazione del profilo a un gruppo misto il gruppo **Tutti gli utenti** è interessato dal profilo. L'esclusione non viene applicata.

  Non è quindi consigliabile assegnare profili a gruppi misti.

## <a name="next-steps"></a>Passaggi successivi

Per indicazioni sul monitoraggio dei profili e dei dispositivi in cui sono in esecuzione i profili, vedere [Monitorare i profili di dispositivo](device-profile-monitor.md).
