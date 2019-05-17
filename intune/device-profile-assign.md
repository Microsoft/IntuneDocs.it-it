---
title: Assegnare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Usare il portale di Azure per assegnare profili e criteri di dispositivo a utenti e dispositivi. Informazioni su come escludere gruppi da un'assegnazione di profilo in Microsoft Intune.
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
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570507"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Assegnare profili utente e profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dopo aver creato un profilo, completo di tutte le impostazioni specificate, il passaggio successivo consiste nel distribuire o "assegnare" il profilo ai gruppi di utenti o di dispositivi di Azure Active Directory (Azure AD). Con l'assegnazione, gli utenti e i dispositivi ricevono il profilo e vengono applicate le impostazioni specificate.

Questo articolo illustra come assegnare un profilo e include alcune informazioni sull'uso dei tag di ambito nei profili.

## <a name="assign-a-device-profile"></a>Assegnare un profilo di dispositivo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili**. Vengono elencati tutti i profili.
3. Selezionare il profilo che si vuole assegnare e quindi selezionare **Assegnazioni**.
4. Scegliere **Includi** o **Escludi**, quindi selezionare i gruppi da includere o escludere. Quando si selezionano i gruppi, si sceglie un gruppo di Azure AD. Per selezionare più gruppi, tenere premuto **CTRL** e selezionare i gruppi.

    ![Screenshot delle opzioni per includere o escludere i gruppi da un'assegnazione di profilo](./media/group-include-exclude.png)

5. **Salvare** le modifiche.

### <a name="evaluate-how-many-users-are-targeted"></a>Valutare il numero di utenti interessati

Quando si assegna il profilo, è anche possibile usare la funzionalità **Valuta** per calcolare il numero di utenti interessati. Questa funzionalità calcola gli utenti, non i dispositivi.

1. In Intune selezionare **Configurazione del dispositivo** > **Profili**.
2. Selezionare un profilo e quindi **Assegnazioni** > **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti interessati da questo profilo.

Se il pulsante **Valuta** è disattivato, verificare che il profilo sia assegnato a uno o più gruppi.


## <a name="use-scope-tags"></a>Usare i tag di ambito

Durante la creazione o l'aggiornamento di un profilo è anche possibile aggiungervi tag di ambito.

I **tag di ambito** sono un metodo molto efficiente per assegnare e filtrare criteri a gruppi specifici, ad esempio il reparto Risorse umane o i dipendenti di una filiale. Per altre informazioni, vedere [Use RBAC and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

## <a name="exclude-groups-from-a-profile-assignment"></a>Escludere gruppi da un'assegnazione di profilo

I profili di configurazione dei dispositivi Intune consentono di escludere gruppi dall'assegnazione dei criteri. Ad esempio, è possibile assegnare un profilo di dispositivo al gruppo **Tutti gli utenti aziendali**, ma escludere i membri del gruppo **Dirigenti**.

Quando si escludono gruppi, solo utenti o solo gruppi di dispositivi (non una combinazione di gruppi) da un'assegnazione, Intune non considera le relazioni utente-dispositivo. L'inclusione di gruppi di utenti mentre si escludono gruppi di dispositivi può non restituire i risultati previsti. Se si usano gruppi misti o esistono altri conflitti, l'inclusione ha la precedenza sull'esclusione.

Ad esempio, si vuole assegnare un profilo di dispositivo a tutti i dispositivi dell'organizzazione, ad eccezione dei dispositivi in modalità tutto schermo. Si include il gruppo **Tutti gli utenti**, ma si esclude il gruppo **Tutti i dispositivi**. In questo caso, tutti gli utenti e i relativi dispositivi ottengono i criteri, anche se il dispositivo dell'utente è nel gruppo **Tutti i dispositivi**.

L'esclusione valuta solo i membri diretti del gruppo. Non include i dispositivi associati a un utente. Tuttavia i dispositivi che non hanno un utente non ottengono i criteri. Questo accade perché i dispositivi non hanno alcuna relazione con il gruppo **Tutti gli utenti**.

Se si includono **tutti i dispositivi** ma si escludono **tutti gli utenti**, tutti i dispositivi ricevono i criteri. In questo caso, lo scopo è l'esclusione dei dispositivi ai quali è associato un utente in base a questi criteri. Tuttavia i dispositivi non vengono esclusi, perché l'esclusione confronta solo i membri diretti del gruppo.

## <a name="next-steps"></a>Passaggi successivi

Per indicazioni sul monitoraggio dei profili e dei dispositivi in cui sono in esecuzione i profili, vedere [Monitorare i profili di dispositivo](device-profile-monitor.md).