---
title: Introduzione agli utenti
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e711f32ebd77a83b17e6db468f8cb23a409c8d31
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="get-started-with-users"></a>Introduzione agli utenti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Azure Active Directory gestisce i gruppi di oggetti (quali dispositivi e app) e i gruppi di utenti dell'organizzazione. È possibile raggruppare utenti o dispositivi anziché gestire singolarmente ogni dispositivo. Con questo approccio è possibile assegnare facilmente app e impostazioni a un numero elevato di utenti e dispositivi.

## <a name="how-do-i-create-a-user"></a>Come si crea un utente?

1. Accedere al [portale di Azure](https://portal.azure.com).
2. In **Cerca risorse** cercare **Utenti e gruppi**.
3. Aprire il pannello **Utenti e gruppi**, selezionare **Tutti gli utenti**, quindi selezionare **Aggiungi**.
4. Immettere i dettagli dell'utente, ad esempio **Nome** e **Nome utente**. La parte del nome utente con il nome di dominio deve corrispondere al nome di dominio predefinito iniziale "contoso.onmicrosoft.com" o a un nome di dominio verificato e non federato, ad esempio "contoso.com".
5. In **Gruppi** scegliere il gruppo di test al quale aggiungere l'utente.
6. Salvare la password dell'utente generata automaticamente e necessaria per l'accesso a un dispositivo di test. È necessario comunicare questa password agli utenti, che potranno sostituirla con una password normale facile da ricordare.
7. Nel pannello **Utente** selezionare **Crea**.

## <a name="assigning-licenses-to-users"></a>Assegnazione di licenze agli utenti

Dopo aver creato un utente è necessario usare il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) per assegnare una licenza di Intune a tale utente. Senza una licenza l'utente non può registrare il dispositivo nella gestione.

1. Accedere al [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con le stesse credenziali usate per accedere a Intune.
2. Selezionare **Utenti** > **Utenti attivi**, quindi selezionare l'utente creato in precedenza.
3. Attendere qualche istante per il caricamento delle informazioni dell'utente. Dopo il caricamento selezionare **Modifica** nel pannello **Licenze** dell'utente.
4. Assegnare un **Percorso** all'utente, quindi impostare Intune su **On** (Attivato).

 > [!NOTE]
 > Questa operazione usa una delle licenze per l'utente. Se si usa l'ambiente in tempo reale è possibile disattivare l'uso di licenza in un secondo momento per riassegnarla a un utente reale.

5. Selezionare **Salva**.
