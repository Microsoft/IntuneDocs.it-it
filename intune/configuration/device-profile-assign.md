---
title: Assegnare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Usare il portale di Azure per assegnare profili e criteri di dispositivo a utenti e dispositivi. Informazioni su come escludere gruppi da un'assegnazione di profilo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2019
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
ms.openlocfilehash: a19515e859f5e78f7611bbd10088aea5f7c44650
ms.sourcegitcommit: f12bd2ce10b6241715bae2d2857f33c474287166
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72892626"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Assegnare profili utente e profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Dopo aver creato un profilo, completo di tutte le impostazioni specificate, il passaggio successivo consiste nel distribuire o "assegnare" il profilo ai gruppi di utenti o di dispositivi di Azure Active Directory (Azure AD). Con l'assegnazione, gli utenti e i dispositivi ricevono il profilo e vengono applicate le impostazioni specificate.

Questo articolo illustra come assegnare un profilo e include alcune informazioni sull'uso dei tag di ambito nei profili.

> [!NOTE]  
> Quando un criterio viene rimosso o non è più assegnato a un dispositivo, l'impostazione potrebbe mantenere il valore esistente. L'impostazione non ripristina un valore predefinito. Per impostare un valore diverso, creare un nuovo criterio e assegnarlo.

## <a name="before-you-begin"></a>Prima di iniziare

Assicurarsi di avere il ruolo appropriato per assegnare i criteri. Per altre informazioni, vedere [Controllo degli accessi in base al ruolo (RBAC) con Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Assegnare un profilo di dispositivo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili**. Vengono elencati tutti i profili.
3. Selezionare il profilo che si vuole assegnare e quindi selezionare **Assegnazioni**.
4. Scegliere **Includi** o **Escludi**, quindi selezionare i gruppi da includere o escludere. Quando si selezionano i gruppi, si sceglie un gruppo di Azure AD. Per selezionare più gruppi, tenere premuto **CTRL** e selezionare i gruppi.

    ![Screenshot delle opzioni per includere o escludere i gruppi da un'assegnazione di profilo](./media/device-profile-assign/group-include-exclude.png)

5. **Salvare** le modifiche.

### <a name="evaluate-how-many-users-are-targeted"></a>Valutare il numero di utenti interessati

Quando si assegna il profilo, è anche possibile usare la funzionalità **Valuta** per calcolare il numero di utenti interessati. Questa funzionalità calcola gli utenti, non i dispositivi.

1. In Intune selezionare **Configurazione del dispositivo** > **Profili**.
2. Selezionare un profilo e quindi **Assegnazioni** > **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti interessati da questo profilo.

Se il pulsante **Valuta** è disattivato, verificare che il profilo sia assegnato a uno o più gruppi.

## <a name="use-scope-tags-or-applicability-rules"></a>Usare i tag di ambito o le regole di applicabilità

Durante la creazione o l'aggiornamento di un profilo è anche possibile aggiungere tag di ambito e regole di applicabilità.

I **tag di ambito** sono un metodo molto efficiente per assegnare e filtrare criteri a gruppi specifici, ad esempio il reparto Risorse umane o i dipendenti di una filiale. Per altre informazioni, vedere [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

Nei dispositivi Windows 10 è possibile aggiungere **regole di applicabilità**, in modo che il profilo venga applicato solo a una versione specifica del sistema operativo o a un'edizione specifica di Windows. Per altre informazioni, vedere [Regole di applicabilità](device-profile-create.md#applicability-rules).

## <a name="exclude-groups-from-a-profile-assignment"></a>Escludere gruppi da un'assegnazione di profilo

I profili di configurazione dei dispositivi Intune consentono di includere ed escludere gruppi dall'assegnazione di criteri.

Come procedura consigliata, creare e assegnare criteri specifici per i gruppi utenti e creare e assegnare criteri diversi specificamente per i gruppi di dispositivi. Per altre informazioni sui gruppi, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](../fundamentals/groups-add.md).

Quando si assegnano i criteri includendo ed escludendo gruppi, usare la tabella seguente. Un segno di spunta indica che l'assegnazione è supportata.

![Opzioni supportate per includere o escludere gruppi da un'assegnazione di profilo](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Informazioni importanti

- L'esclusione ha la precedenza sull'inclusione negli scenari seguenti, relativi a gruppi dello stesso tipo:

  - Inclusione di gruppi utenti ed esclusione di gruppi utenti
  - Inclusione di gruppi di dispositivi ed esclusione di gruppi di dispositivi

  Ad esempio si assegna un profilo di dispositivo al gruppo di utenti **Tutti gli utenti aziendali**, ma si escludono i membri del gruppo **Dirigenti**. Poiché entrambi i gruppi sono gruppi utenti, i criteri interessano **tutti gli utenti aziendali** ad eccezione dei **dirigenti**.

- Intune non valuta le relazioni di gruppi di utenti e dispositivi. Se si assegnano criteri a gruppi misti, i risultati potrebbero non essere quelli voluti o previsti.

  Si supponga, ad esempio, di assegnare un profilo di dispositivo al gruppo utenti **Tutti gli utenti**, escludendo però il gruppo di dispositivi **Tutti i dispositivi personali**. In questa assegnazione di criteri di gruppo misto il gruppo **Tutti gli utenti** è interessato dai criteri. L'esclusione non viene applicata.

  Non è quindi consigliabile assegnare criteri a gruppi misti.

## <a name="next-steps"></a>Passaggi successivi

Per indicazioni sul monitoraggio dei profili e dei dispositivi in cui sono in esecuzione i profili, vedere [Monitorare i profili di dispositivo](device-profile-monitor.md).
