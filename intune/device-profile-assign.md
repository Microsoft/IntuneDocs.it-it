---
title: Come assegnare i profili di dispositivo con Intune
titleSuffix: Intune on Azure
description: Dopo aver creato un profilo di dispositivo con Intune, usare questo argomento per informazioni su come assegnarlo ai dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf6bd6cb301491c031e382236eee509e17f08383
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2017
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>Come assegnare i profili di dispositivo con Microsoft Intune

## <a name="assign-a-device-profile"></a>Assegnare un profilo di dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
1. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
2. Nell'elenco del pannello dei profili selezionare il profilo che si desidera gestire, quindi, nel pannello **Report** <*nome profilo*>  scegliere **Gestisci** > **Assegnazioni**.
3. Nel pannello successivo, scegliere **Includi** per includere i gruppi o **Escludi** per escludere i gruppi, quindi scegliere **Seleziona gruppi**.
![Includere ed escludere gruppi da un'assegnazione di profilo.](./media/group-include-exclude.png)
4. Nel pannello **Seleziona gruppi** scegliere i gruppi di Azure AD che si vuole includere o escludere dall'assegnazione. Per selezionare più gruppi, è possibile tenere premuto il tasto **CTRL**.
4. Al termine, nel pannello **Selezionare i gruppi** scegliere **Seleziona**.



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>Come escludere gruppi da un'assegnazione di profilo di dispositivo

I profili di configurazione dei dispositivi Intune consentono di escludere gruppi dall'assegnazione dei criteri. Ad esempio, è possibile assegnare un profilo di dispositivo per il gruppo **Tutti gli utenti aziendali**, ma escludere tutti i membri del gruppo **Dirigenti**.

Quando si escludono gruppi da un'assegnazione, escludere solo utenti o gruppi di dispositivi, non usare una combinazione di gruppi. Intune non tiene conto di nessun utente associato al dispositivo quando esclude i gruppi. L'inclusione di gruppi di utenti mentre si escludono i gruppi di dispositivi molto probabilmente non dà i risultati necessari. Nel caso in cui vengano usati gruppi misti o esistono altri conflitti, l'inclusione ha la precedenza sull'esclusione.

Ad esempio, si vuole assegnare un profilo di dispositivo a tutti i dispositivi dell'organizzazione, ad eccezione dei dispositivi in modalità tutto schermo. Si include il gruppo **Tutti gli utenti**, ma si esclude il gruppo **Tutti i dispositivi**.

In questo caso, tutti gli utenti e i dispositivi ottengono i criteri, anche se il dispositivo dell'utente è parte del gruppo **Tutti i dispositivi**. 

L'esclusione valuta solo i membri diretti del gruppo e non include i dispositivi che sono associati a un utente. Tuttavia, i dispositivi che non hanno utenti non ottengono i criteri perché non hanno alcuna associazione con il gruppo **Tutti gli utenti**. 

Se si includono **tutti i dispositivi**, ma si escludono **tutti gli utenti**, tutti i dispositivi ricevano i criteri. In questo caso, lo scopo è di escludere i dispositivi che hanno un utente associato da questi criteri. Tuttavia, ciò non avviene perché la funzionalità di esclusione confronta solo i membri diretti del gruppo. 

>[!Tip]
>Le esclusioni non sono attualmente disponibili per l'assegnazione di app o di criteri di conformità. Per escludere membri da un'assegnazione, è possibile usare i tipi di assegnazione Disponibile e Non applicabile. Ad esempio, si assegna un'app al gruppo **Tutti gli utenti aziendali** con il tipo **Disponibile** e al gruppo **Dirigenti** con il tipo **Non applicabile**. L'app viene assegnata a tutti gli utenti *tranne* agli utenti del gruppo **Dirigenti**. Se si assegna l'app al gruppo **Tutti gli utenti aziendali** con il tipo **Necessario**, gli utenti del gruppo **Dirigenti** non vengono esclusi.
 
    
## <a name="next-steps"></a>Passaggi successivi
Per informazioni sul monitoraggio delle assegnazioni dei profili di dispositivo vedere [Come monitorare i profili di dispositivo](device-profile-monitor.md).
