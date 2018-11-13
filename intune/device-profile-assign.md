---
title: Assegnare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Usare il portale di Azure per assegnare profili e criteri di dispositivo a utenti e dispositivi. Informazioni su come escludere i gruppi da un'assegnazione di profilo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 439c89f7b0158111f63d2d8327291c2b5a5c1e38
ms.sourcegitcommit: cfce9318b5b5a3005929be6eab632038a12379c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51298072"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Assegnare profili utente e profili di dispositivo in Microsoft Intune

Dopo aver creato un profilo è possibile assegnarlo ai gruppi di Azure Active Directory (Azure AD).

## <a name="assign-a-device-profile"></a>Assegnare un profilo di dispositivo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** e cercare **Microsoft Intune**.
2. In **Microsoft Intune** selezionare **Configurazione del dispositivo** e quindi **Profili**.
3. Nell'elenco di profili selezionare il profilo che si vuole assegnare e quindi scegliere **Assegnazioni**.
4. Scegliere **Includi** o **Escludi** e quindi selezionare i gruppi.  

    ![Screenshot delle opzioni per includere o escludere i gruppi da un'assegnazione di profilo](./media/group-include-exclude.png)

5. Quando si selezionano i gruppi, si sceglie un gruppo di Azure AD. Per selezionare più gruppi, tenere premuto **CTRL**.
6. Al termine, selezionare **Salva**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Escludere gruppi da un'assegnazione di profilo

I profili di configurazione dei dispositivi Intune consentono di escludere gruppi dall'assegnazione dei criteri. Ad esempio è possibile assegnare un profilo di dispositivo al gruppo **Tutti gli utenti aziendali**, ma escludere tutti i membri del gruppo **Dirigenti**.

Quando si escludono gruppi da un'assegnazione, si escludono solo utenti o si escludono solo gruppi di dispositivi (non una combinazione di gruppi), Intune non considera nessuna relazione utente-dispositivo. L'inclusione di gruppi di utenti mentre si escludono gruppi di dispositivi può non restituire i risultati previsti. Se si usano gruppi misti o esistono altri conflitti, l'inclusione ha la precedenza sull'esclusione.

Ad esempio, si vuole assegnare un profilo di dispositivo a tutti i dispositivi dell'organizzazione, ad eccezione dei dispositivi in modalità tutto schermo. Si include il gruppo **Tutti gli utenti**, ma si esclude il gruppo **Tutti i dispositivi**. In questo caso, tutti gli utenti e i dispositivi ottengono i criteri, anche se il dispositivo dell'utente è parte del gruppo **Tutti i dispositivi**.

L'esclusione valuta solo i membri diretti dei gruppi e non include i dispositivi associati a un utente. Tuttavia i dispositivi che non hanno un utente non ottengono i criteri. Questo si verifica perché i dispositivi non hanno nessuna relazione con il gruppo **Tutti gli utenti**.

Se si includono **tutti i dispositivi** ma si escludono **tutti gli utenti**, tutti i dispositivi ricevono i criteri. In questo caso, lo scopo è l'esclusione dei dispositivi ai quali è associato un utente in base a questi criteri. Tuttavia i dispositivi non vengono esclusi, perché l'esclusione confronta solo i membri diretti del gruppo.

## <a name="next-steps"></a>Passaggi successivi
Per informazioni sul monitoraggio delle assegnazioni dei profili di dispositivo, vedere [Come monitorare i profili di dispositivo](device-profile-monitor.md).
