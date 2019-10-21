---
title: Assegnare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Usare il portale di Azure per assegnare profili e criteri di dispositivo a utenti e dispositivi. Informazioni su come escludere gruppi da un'assegnazione di profilo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db1f0944a6725d1f361ea20c972d8ffa8f5d9035
ms.sourcegitcommit: a50a1ca123ecc2c5ac129f112f73838748f56476
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237219"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Assegnare profili utente e profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Dopo aver creato un profilo, completo di tutte le impostazioni specificate, il passaggio successivo consiste nel distribuire o "assegnare" il profilo ai gruppi di utenti o di dispositivi di Azure Active Directory (Azure AD). Con l'assegnazione, gli utenti e i dispositivi ricevono il profilo e vengono applicate le impostazioni specificate.

Questo articolo illustra come assegnare un profilo e include alcune informazioni sull'uso dei tag di ambito nei profili.

> [!NOTE]  
> Quando un criterio viene rimosso o non è più assegnato a un dispositivo, l'impostazione potrebbe mantenere il valore esistente. L'impostazione non ripristina un valore predefinito. Per impostare un valore diverso, creare un nuovo criterio e assegnarlo.

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

I profili di configurazione dei dispositivi Intune consentono di escludere gruppi dall'assegnazione dei criteri.

Intune non esamina le relazioni da utente a gruppo di dispositivi. L'inclusione di gruppi di utenti mentre si escludono gruppi di dispositivi può non restituire i risultati previsti. Negli scenari da gruppo di utenti a gruppo di utenti e da gruppo di dispositivi a gruppo di dispositivi l'esclusione ha la precedenza sull'inclusione.

Ad esempio si assegna un profilo di dispositivo al gruppo di utenti **Tutti gli utenti aziendali**, ma si escludono i membri del gruppo **Dirigenti**. Poiché entrambi i gruppi sono gruppi di utenti, tutti i membri del gruppo **Dirigenti** sono esclusi dal criterio, anche se sono membri del gruppo di inclusione **Tutti gli utenti aziendali**.

L'inclusione ha la precedenza sull'esclusione quando si usano gruppi misti, ad esempio da gruppo di utenti a gruppo di dispositivi o da gruppo di dispositivi a gruppo di utenti.

Si supponga di voler assegnare un profilo di dispositivo a tutti gli utenti dell'organizzazione, ad eccezione dei dispositivi in modalità tutto schermo. Si include il gruppo **Tutti gli utenti**, ma si esclude il gruppo **Tutti i dispositivi**. In questo caso, tutti gli utenti e i relativi dispositivi ottengono i criteri, anche se il dispositivo dell'utente è nel gruppo **Tutti i dispositivi**.

L'esclusione valuta solo i membri diretti del gruppo. Non include i dispositivi associati a un utente. Tuttavia i dispositivi che non hanno un utente non ottengono i criteri. Questo accade perché i dispositivi senza utente non hanno alcuna relazione con il gruppo **Tutti gli utenti**.

Se si includono **tutti i dispositivi** ma si escludono **tutti gli utenti**, tutti i dispositivi ricevono i criteri. In questo caso, lo scopo è l'esclusione dei dispositivi ai quali è associato un utente in base a questi criteri. Tuttavia i dispositivi non vengono esclusi, perché l'esclusione confronta solo i membri diretti del gruppo.

## <a name="next-steps"></a>Passaggi successivi

Per indicazioni sul monitoraggio dei profili e dei dispositivi in cui sono in esecuzione i profili, vedere [Monitorare i profili di dispositivo](device-profile-monitor.md).
