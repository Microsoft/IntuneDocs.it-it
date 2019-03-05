---
title: Introduzione alla gestione degli utenti
titlesuffix: Microsoft Intune
description: Aggiungere un utente a Intune e assegnargli una licenza per consentire l'accesso alle risorse aziendali nei dispositivi mobili.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c401110799202bd0c8aafc62bfda6d8827247be
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57234760"
---
# <a name="get-started-managing-users"></a>Introduzione alla gestione degli utenti

In ogni organizzazione lavorano molte persone diverse. Per ogni persona che usa i dati aziendali è necessario un utente per gestire l'accesso ai dati in Intune.

## <a name="how-do-i-create-a-user"></a>Come si crea un utente?

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Dopo aver aperto il riquadro **Microsoft Intune**, selezionare **Utenti**. Nella pagina **Tutti gli utenti** selezionare **+ Nuovo utente**.
4. Immettere i dettagli dell'utente, ad esempio **Nome** e **Nome utente**. La parte del nome di dominio del nome utente deve corrispondere a uno dei domini seguenti:
    - nome di dominio predefinito iniziale "contoso.onmicrosoft.com";
    - nome di dominio verificato non federato, ad esempio "contoso.com".
5. In **Gruppi** scegliere [un gruppo](get-started-groups.md) al quale aggiungere l'utente.
6. Salvare la password utente generata automaticamente, necessaria per l'accesso a un dispositivo di test. È necessario comunicare questa password agli utenti, che potranno sostituirla con una password normale facile da ricordare.
7. Nel riquadro **Utente** selezionare **Crea**.

## <a name="assigning-licenses-to-users"></a>Assegnazione di licenze agli utenti

Dopo aver creato un utente è necessario usare il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) per assegnare una licenza di Intune a tale utente. Senza una licenza l'utente non può registrare il dispositivo nella gestione.

1. Accedere al [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con le stesse credenziali usate per accedere a Intune.
2. Selezionare **Utenti** > **Utenti attivi**, quindi selezionare l'utente creato in precedenza.
3. Attendere qualche istante per il caricamento delle informazioni dell'utente. Dopo il caricamento selezionare **Modifica** nel pannello **Licenze** dell'utente.
4. Assegnare un **Percorso** all'utente, quindi impostare Intune su **On** (Attivato).

   > [!NOTE]
   > Questa operazione usa una delle licenze per l'utente. Se si usa l'ambiente in tempo reale è possibile disattivare l'uso di licenza in un secondo momento per riassegnarla a un utente reale.

5. Selezionare **Salva**.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione ai gruppi](get-started-groups.md): illustra come organizzare gli utenti in gruppi per semplificare la gestione dei criteri e delle app a cui possono accedere.
