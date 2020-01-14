---
title: Aggiungere gruppi per organizzare utenti e dispositivi
titleSuffix: Microsoft Intune
description: Aggiungere gruppi per organizzare utenti e dispositivi in base a posizione geografica, reparto o caratteristiche hardware.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe37ac412d01d3032685a0e66827d20e13b0db64
ms.sourcegitcommit: 42183c87b137710b8529049f8710d47127e99900
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75303066"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Aggiungere gruppi per organizzare utenti e dispositivi

Intune usa i gruppi di Azure Active Directory (Azure AD) per gestire dispositivi e utenti. Gli amministratori di Intune possono impostare i gruppi in base alle esigenze dell'organizzazione. Creare gruppi per organizzare utenti o dispositivi in base alla posizione geografica, reparto o caratteristiche hardware. Usare i gruppi per gestire operazioni su larga scala. Ad esempio, è possibile impostare i criteri per più utenti o distribuire le app a un set di dispositivi.

È possibile aggiungere i tipi di gruppi seguenti:

- **Gruppi assegnati**: aggiungere manualmente utenti o dispositivi a un gruppo statico. 
- **Gruppi dinamici** (richiede Azure AD Premium): aggiungere automaticamente utenti o dispositivi a gruppi di utenti o di dispositivi in base a un'espressione creata.

  Ad esempio, quando un utente viene aggiunto con il titolo Manager, l'utente viene aggiunto automaticamente a un gruppo di utenti **Tutti i manager**. In alternativa, quando un dispositivo ha il tipo di sistema operativo del dispositivo iOS, il dispositivo viene aggiunto automaticamente a un gruppo di dispositivi **Tutti i dispositivi**.

## <a name="add-a-new-group"></a>Aggiungere un nuovo gruppo

Usare la procedura seguente per creare un nuovo gruppo.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Gruppi** > **Nuovo gruppo**:

   ![Screenshot del portale di Azure in cui è selezionato Nuovo gruppo](./media/groups-add/groups-add-new.png)

3. In **Tipo gruppo** selezionare una delle opzioni seguenti:

    - **Sicurezza**: i gruppi di sicurezza definiscono gli utenti che possono accedere alle risorse e sono consigliati per i gruppi in Intune. Ad esempio, è possibile creare gruppi per gli utenti, come **Tutti i dipendenti di Charlotte** o **Tutti i lavoratori remoti**. In alternativa, è possibile creare gruppi per i dispositivi, ad esempio **Tutti i dispositivi iOS** o **Tutti i dispositivi Windows 10 Student**.

        > [!TIP]
        > Gli utenti e i gruppi creati possono essere visualizzati anche nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com), nell'interfaccia di amministrazione di Azure Active Directory e in [Microsoft Intune nel portale di Azure](https://go.microsoft.com/fwlink/?linkid=2090973). Nel tenant dell'organizzazione è possibile creare e gestire i gruppi in tutte queste aree.
        >
        > Se il ruolo primario è la gestione dei dispositivi, è consigliabile usare l'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: Questi gruppi sono progettati per controllare l'accesso e condividere le risorse di Office 365. Ad esempio, è possibile creare un gruppo di Office 365 per condividere una casella di posta in arrivo o un calendario di Outlook. Per altre informazioni, vedere [Informazioni su Gruppi di Office 365](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Immettere un **Nome gruppo** e una **Descrizione gruppo** per il nuovo gruppo. Immettere informazioni specifiche che consentano agli altri utenti di individuare la funzione del gruppo.

    Ad esempio, immettere **Tutti i dispositivi Windows 10 Student** per nome gruppo e **Tutti i dispositivi Windows 10 usati dagli studenti in Contoso delle classi superiori 9-12** per la descrizione del gruppo.

5. Immettere il **Tipo di appartenenza**. Le opzioni disponibili sono:

    - **Assegnato**: Gli amministratori assegnano e rimuovono manualmente gli utenti o i dispositivi in questo gruppo.
    - **Utente dinamico**: Gli amministratori creano le regole di appartenenza per aggiungere e rimuovere automaticamente i membri.
    - **Dispositivo dinamico**: Gli amministratori creano le regole di gruppo dinamico per aggiungere e rimuovere automaticamente i dispositivi.

        ![Screenshot delle proprietà dei gruppi di Intune](./media/groups-add/groups-add-properties.png)

    Per altre informazioni su questi tipi di appartenenza e sulla creazione di espressioni dinamiche, vedere:

    - [Creare un gruppo di base e aggiungere membri con Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Regole di appartenenza dinamica per i gruppi in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Nell'interfaccia di amministrazione, quando si creano utenti o gruppi, è possibile che non venga visualizzato **Azure Active Directory**. Ciononostante, viene usato Azure Active Directory.

6. Scegliere **Crea** per aggiungere il nuovo gruppo. Il gruppo viene visualizzato nell'elenco.

> [!TIP]
> Prendere in considerazione alcuni degli altri gruppi di utenti e dispositivi dinamici che è possibile creare, ad esempio:
>
> - Tutti gli studenti di Contoso High School
> - Tutti i dispositivi Android Enterprise
> - Tutti i dispositivi iOS 11 e versioni precedenti
> - Marketing
> - Risorse umane
> - Tutti i dipendenti di Charlotte
> - Tutti i dipendenti di WA

## <a name="groups-and-policies"></a>Gruppi e criteri

L'accesso alle risorse dell'organizzazione è controllato dagli utenti e dai gruppi creati.

Quando si creano gruppi, considerare la modalità di applicazione dei [criteri di conformità](../protect/device-compliance-get-started.md) e dei [profili di configurazione](../configuration/device-profiles.md). Ad esempio, è possibile avere:

- Criteri specifici del sistema operativo di un dispositivo.
- Criteri specifici dei diversi ruoli all'interno dell'organizzazione.
- Criteri specifici delle unità organizzative definite in Active Directory.

Per creare i requisiti di conformità di base dell'organizzazione, è possibile creare un criterio predefinito che si applica a tutti i gruppi e dispositivi. Creare quindi criteri più specifici per categorie più ampie di utenti e dispositivi, ad esempio criteri di posta elettronica per ogni sistema operativo per i dispositivi.

Per raccomandazioni e materiale sussidiario sui profili di configurazione, vedere [Assegnare i criteri a gruppi di utenti o gruppi di dispositivi](../configuration/device-profile-assign.md#user-groups-vs-device-groups) e [Raccomandazioni sui profili](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Vedere anche

- [Controllo degli accessi in base al ruolo con Microsoft Intune](role-based-access-control.md)
- [Gestire l'accesso alle risorse con i gruppi di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
