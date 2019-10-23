---
title: Configurare un nome di dominio personalizzato
titleSuffix: Microsoft Intune
description: Aggiungere un nome di dominio personalizzato per la sottoscrizione di Microsoft Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e8d0a38d385e034b948b96a96df2189666362a9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505450"
---
# <a name="configure-a-custom-domain-name"></a>Configurare un nome di dominio personalizzato

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Questo argomento descrive agli amministratori come creare un CNAME DNS per semplificare e personalizzare l'esperienza di accesso usando Microsoft Intune.

Quando l'organizzazione si iscrive a un servizio Microsoft basato su cloud come Intune, l'utente riceve un nome di dominio iniziale ospitato in Azure Active Directory (AD) simile a **dominio.onmicrosoft.com**. In questo esempio **dominio** è il nome scelto al momento dell'iscrizione. **onmicrosoft.com** è il suffisso assegnato agli account che si aggiungono alla sottoscrizione. Per accedere a Intune, è possibile configurare il dominio personalizzato dell'organizzazione invece del nome di dominio fornito con la sottoscrizione.

Prima di creare account utente oppure sincronizzare gli account dall'istanza locale di Active Directory, è consigliabile decidere se usare solo il dominio .onmicrosoft.com oppure aggiungere uno o più nomi di dominio personalizzati. Per semplificare la gestione utenti, configurare un dominio personalizzato prima di aggiungere gli utenti. Configurando un dominio personalizzato, gli utenti possono eseguire l'accesso con le credenziali usate per accedere ad altre risorse del dominio.

Quando si sottoscrive un servizio cloud Microsoft, l'istanza del servizio ottenuta è un [tenant di Azure AD](https://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) di Microsoft, che fornisce identità e servizi di directory per il servizio cloud. Poiché le attività necessarie per configurare Intune in modo da usare il nome di dominio personalizzato aziendale sono le stesse che per altri tenant Azure Active Directory, è possibile usare le informazioni e le procedure disponibili in [Aggiungere un nome di dominio personalizzato ad Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Per altre informazioni sui domini personalizzati, vedere [Panoramica concettuale dei nomi di dominio personalizzati in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Non è possibile rinominare o rimuovere il nome di dominio onmicrosoft.com iniziale. È possibile aggiungere, verificare o rimuovere i nomi di dominio personalizzati usati con Intune in modo che l'identità aziendale risulti chiara.

## <a name="to-add-and-verify-your-custom-domain"></a>Per aggiungere e verificare il dominio personalizzato

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/) e accedere all'account amministratore.

2. Nel riquadro di spostamento scegliere **Impostazioni** &gt; **Domini**.

3. Scegliere **Aggiungi dominio** e digitare il nome di dominio personalizzato. Selezionare **Avanti**.
   ![Screenshot dell'interfaccia di amministrazione di Microsoft 365 con selezione di Impostazioni > Domini e aggiunta di un nuovo nome di dominio](./media/custom-domain-name-configure/domain-custom-add.png)
4. Verrà visualizzata la finestra di dialogo **Verifica dominio** con i valori necessari per creare il record TXT nel provider di hosting DNS.
    - **Utenti di GoDaddy**: l'interfaccia di amministrazione di Microsoft 365 reindirizza gli utenti alla pagina di accesso di GoDaddy. Dopo l'immissione delle credenziali e l'accettazione dell'accordo di autorizzazione alla modifica del dominio, il record TXT viene creato automaticamente. In alternativa è possibile [creare il record TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Utenti di Register.com**: seguire le [istruzioni dettagliate](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) per creare il record TXT.
5. [Potrebbe essere necessario creare record DNS aggiuntivi per le registrazioni di Intune](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium).

I passaggi per aggiungere e verificare un dominio personalizzato possono essere anche [eseguiti in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Altre informazioni sono disponibili in [Informazioni sul dominio onmicrosoft.com iniziale in Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

Creare un DNS CNAME che reindirizza la registrazione a server Intune per avere altre informazioni su come [semplificare la registrazione W senza Azure AD Premium](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium).
