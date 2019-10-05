---
title: Aggiungere gruppi per organizzare utenti e dispositivi
titleSuffix: Microsoft Intune
description: Aggiungere gruppi per organizzare utenti e dispositivi in base a posizione geografica, reparto o caratteristiche hardware.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7477d8c6325d801d575f2fee66dc9cbee363ce61
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726492"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Aggiungere gruppi per organizzare utenti e dispositivi
Intune usa i gruppi di Azure Active Directory (AD) per gestire dispositivi e utenti. Gli amministratori di Intune possono impostare i gruppi in base alle esigenze dell'organizzazione. Creare gruppi per organizzare utenti o dispositivi in base alla posizione geografica, reparto o caratteristiche hardware. Usare i gruppi per gestire operazioni su larga scala. Ad esempio, è possibile impostare i criteri per molti utenti o distribuire le app a un set di dispositivi.

È possibile aggiungere i tipi di gruppi seguenti:
- **Gruppi assegnati**: aggiungere manualmente utenti o dispositivi a un gruppo statico
- **Gruppi dinamici**: (con Azure Active Directory Premium) consente di creare dinamicamente gruppi di utenti o di dispositivi con regole semplici o avanzate

## <a name="add-a-new-group"></a>Aggiungere un nuovo gruppo

Usare la procedura seguente per creare un nuovo gruppo.
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Gruppi** e quindi scegliere **Nuovo gruppo** nel riquadro **Tutti i gruppi**.
   ![Screenshot del portale di Azure in cui è selezionato Nuovo gruppo](./media/groups-add/groups-add-new.png)
4. Per **Tipo gruppo** selezionare una delle opzioni seguenti:
    - **Sicurezza**: I gruppi di sicurezza sono un'ottima risorsa per il popolamento dei gruppi di utenti. Dato che i gruppi di sicurezza definiscono chi ha accesso a quali risorse, tali gruppi possono essere convertiti perfettamente in gruppi di utenti di Intune. I gruppi di sicurezza sincronizzati da Active Directory ad Azure Active Directory oppure creati direttamente in Azure Active Directory con l'interfaccia di amministrazione di Microsoft 365 o il portale di Azure sono disponibili per l'uso quando si creano gruppi di utenti in Intune.
    - **Office 365**

5. Inserire un **Nome** e una **Descrizione** per il nuovo gruppo. Queste proprietà vengono visualizzate solo nel portale di gestione e non vengono visualizzate agli utenti.

6. Scegliere **Tipo di appartenenza**:
   - **Assegnato** per creare un gruppo con l'assegnazione manuale di membri. Per altre informazioni, vedere [Azure AD assigned groups](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) (Gruppi assegnati di Azure AD).
   - **Utente dinamico** per creare un gruppo di utenti definito con una **query dinamica**.
   - **Dispositivo dinamico** per creare un gruppo di dispositivi definito con una **query dinamica**.

   ![Screenshot delle proprietà dei gruppi di Intune](./media/groups-add/groups-add-properties.png)

   Azure AD consente di creare gruppi dinamici basati su regole che definiscono l'appartenenza. Informazioni su come [creare gruppi dinamici basati su attributi](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. È possibile selezionare **Abilitare le funzionalità di Office** per concedere ai membri del gruppo utenti accesso alle app di Office 365 condivise. Altre informazioni sui [gruppi di Office 365](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Scegliere **Crea** per aggiungere il nuovo gruppo.

## <a name="groups-and-policies"></a>Gruppi e criteri

Quando si creano gruppi, tenere conto del modo in cui verranno applicati i [criteri](../protect/device-compliance-get-started.md). Ad esempio, si possono applicare criteri specifici dei sistemi operativi dei dispositivi e criteri specifici per ruoli diversi nell'organizzazione o per differenti unità organizzative già definiti in Active Directory. Potrebbe essere utile avere gruppi di dispositivi separati per iOS, Android e Windows, oltre a un gruppo di utenti per ogni ruolo dell'organizzazione.

Sarà probabilmente anche utile creare criteri predefiniti applicabili a tutti i gruppi e i dispositivi, per stabilire i requisiti di conformità di base dell'organizzazione. Sarà quindi possibile creare criteri più specifici per categorie più ampie di utenti e dispositivi, ad esempio criteri di posta elettronica per ogni sistema operativo per i dispositivi.



## <a name="see-also"></a>Vedere anche
- [Gestire l'accesso alle risorse tramite i gruppi di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Gruppi di Intune classici nel portale di Azure](groups-get-started.md)