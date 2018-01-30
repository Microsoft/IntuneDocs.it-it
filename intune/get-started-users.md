---
title: Introduzione agli utenti
titlesuffix: Azure portal
description: Aggiungere un utente a Intune per consentirgli di accedere alle risorse aziendali dai dispositivi mobili.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 297a9244bac8e45e14e1d22cadee9088c87f34a3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="get-started-with-managing-users"></a>Introduzione alla gestione degli utenti

In ogni organizzazione lavorano molte persone diverse. Per ogni persona che usa i dati aziendali è necessario un utente per gestire l'accesso ai dati in Intune.

## <a name="how-do-i-create-a-user"></a>Come si crea un utente?

1. Accedere al [portale di Azure](https://portal.azure.com).
2. In **Cerca risorse** cercare **Intune**.
3. Dopo aver aperto il pannello **Microsoft Intune**, selezionare **Utenti**. Nella pagina **Tutti gli utenti** selezionare **+ Nuovo utente**.
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

## <a name="next-steps"></a>Passaggi successivi

[Introduzione ai gruppi](get-started-groups.md): illustra come organizzare gli utenti in gruppi per semplificare la gestione dei criteri e delle app a cui possono accedere.
