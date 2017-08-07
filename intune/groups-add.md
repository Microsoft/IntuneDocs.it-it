---
title: Impostare restrizioni di registrazione in Intune
titleSuffix: Intune on Azure
description: Limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2c9d10e4e2a1d2a745b9e327bf9a8a9cd99e5ce4
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2017
---
# <a name="add-groups-in-intune"></a>Aggiungere gruppi in Intune
Intune usa i gruppi di Azure Active Directory (AD) per gestire dispositivi e utenti. Gli amministratori di Intune possono impostare i gruppi in base alle esigenze dell'organizzazione. Creare gruppi per organizzare utenti o dispositivi in base alla posizione geografica, reparto o caratteristiche hardware. Usare i gruppi per gestire operazioni su larga scala. Ad esempio, è possibile impostare i criteri per molti utenti o distribuire le app a un set di dispositivi.

Questo argomento illustra come aggiungere gruppi per l'uso in Intune.

È possibile aggiungere i tipi di gruppi seguenti:
- **Gruppi assegnati**: aggiungere manualmente utenti o dispositivi a un gruppo statico
- **Gruppi dinamici**: (Azure Active Directory Premium) consente di creare dinamicamente utenti o gruppi di dispositivi con regole semplici o avanzate

## <a name="add-a-new-group"></a>Aggiungere un nuovo gruppo

Usare la procedura seguente per creare un nuovo gruppo.
1. Nel portale di Intune, passare a **Gruppi** e quindi scegliere **Nuovo gruppo** nel pannello **Tutti i gruppi**.
  ![Schermata del portale di Intune in cui è selezionato Nuovo gruppo](./media/groups-add-new.png)
2. Specificare il **nome** e la **descrizione** del nuovo gruppo. Queste proprietà vengono visualizzate solo nel portale di Intune e non vengono visualizzate agli utenti.

3. Scegliere **Tipo di appartenenza**:
  - **Assegnato** per creare un gruppo con l'assegnazione manuale di membri. Per altre informazioni, vedere [Azure AD assigned groups](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) (Gruppi assegnati di Azure AD).
  - **Utente dinamico** per creare un gruppo di utenti definito con una **query dinamica**.
  - **Dispositivo dinamico** per creare un gruppo di dispositivi definito con una **query dinamica**.

  ![Schermata delle proprietà del gruppo di Intune con Nome, Descrizione, Tipo di appartenenza, Abilitare le funzioni di Office e Membri](./media/groups-add-properties.png)

  Azure AD consente di creare gruppi dinamici basati su regole che definiscono l'appartenenza. Informazioni su come [creare gruppi dinamici basati su attributi](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

4. È possibile selezionare **Abilitare le funzionalità di Office** per concedere ai membri del gruppo utenti accesso alle app di Office 365 condivise.
5. Scegliere **Crea** per aggiungere il nuovo gruppo.

## <a name="see-also"></a>Vedere anche
[Gestire l'accesso alle risorse con i gruppi di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
[Intune classic groups in the Azure portal](groups-get-started.md) (Gruppi di Intune classici nel portale di Azure)