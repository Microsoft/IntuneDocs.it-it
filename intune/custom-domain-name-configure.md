---
title: Configurare un nome di dominio personalizzato
titlesuffix: Microsoft Intune
description: Aggiungere un nome di dominio personalizzato per la sottoscrizione di Microsoft Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: a4227399eb5cf1d2cc2e265215eccb2c05d73ac5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181497"
---
# <a name="configure-a-custom-domain-name"></a>Configurare un nome di dominio personalizzato

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Questo argomento descrive agli amministratori come creare un CNAME DNS per semplificare e personalizzare l'esperienza di accesso usando Microsoft Intune.

Quando l'organizzazione si iscrive a un servizio Microsoft basato su cloud come Intune, l'utente riceve un nome di dominio iniziale ospitato in Azure Active Directory (AD) simile a **dominio.onmicrosoft.com**. In questo esempio **dominio** è il nome scelto al momento dell'iscrizione. **onmicrosoft.com** è il suffisso assegnato agli account che si aggiungono alla sottoscrizione. Per accedere a Intune, è possibile configurare il dominio personalizzato dell'organizzazione invece del nome di dominio fornito con la sottoscrizione.

Prima di creare account utente oppure sincronizzare gli account dall'istanza locale di Active Directory, è consigliabile decidere se usare solo il dominio .onmicrosoft.com oppure aggiungere uno o più nomi di dominio personalizzati. Per semplificare la gestione utenti, configurare un dominio personalizzato prima di aggiungere gli utenti. In questo modo, gli utenti eseguono l'accesso con le credenziali usate per accedere alle altre risorse del dominio.

Quando si sottoscrive un servizio cloud Microsoft, l'istanza del servizio ottenuta è un [tenant di Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) di Microsoft, che fornisce identità e servizi di directory per il servizio cloud. Poiché le attività necessarie per configurare Intune in modo da usare il nome di dominio personalizzato aziendale sono le stesse che per altri tenant Azure Active Directory, è possibile usare le informazioni e le procedure disponibili in [Aggiungere il dominio personalizzato usando il portale di Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Per altre informazioni sui domini personalizzati, vedere [Panoramica concettuale dei nomi di dominio personalizzati in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Non è possibile rinominare o rimuovere il nome di dominio onmicrosoft.com iniziale. È possibile aggiungere, verificare o rimuovere i nomi di dominio personalizzati usati con Intune in modo che l'identità aziendale risulti chiara.

## <a name="to-add-and-verify-your-custom-domain"></a>Per aggiungere e verificare il dominio personalizzato

1. Passare al [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) e accedere con l'account amministratore.

2. Nel riquadro di spostamento scegliere **Impostazioni** &gt; **Domini**.

3. Scegliere **Aggiungi dominio** e digitare il nome di dominio personalizzato. Selezionare **Avanti**.
   ![Screenshot dell'interfaccia di amministrazione di Office 365 con selezione di Impostazioni > Domini e aggiunta di un nuovo nome di dominio](./media/domain-custom-add.png)
4. Verrà visualizzata la finestra di dialogo **Verifica dominio** con i valori necessari per creare il record TXT nel provider di hosting DNS.
    - **Utenti di GoDaddy**: il portale di gestione di Office 365 reindirizza l'utente alla pagina di accesso di GoDaddy. Dopo l'immissione delle credenziali e l'accettazione dell'accordo di autorizzazione alla modifica del dominio, il record TXT viene creato automaticamente. In alternativa è possibile [creare il record TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Utenti di Register.com**: seguire le [istruzioni dettagliate](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) per creare il record TXT.

I passaggi per aggiungere e verificare un dominio personalizzato possono essere anche [eseguiti in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Altre informazioni sono disponibili in [Informazioni sul dominio onmicrosoft.com iniziale in Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)
