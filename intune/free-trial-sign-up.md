---
title: Iscriversi per una versione di valutazione gratuita di Microsoft Intune valida 30 giorni
titleSuffix: Azure portal
description: Come iscriversi per una versione di valutazione gratuita di Intune valida 30 giorni.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 3b4d6528acd42a84c7d87968874d36199b661a90
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune


Questo articolo descrive la procedura di iscrizione a una versione di valutazione di Intune autonomo per il portale di Azure.

1. Visitare la pagina di [iscrizione a Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) e compilare il modulo per richiedere una sottoscrizione di valutazione.
* Se si dispone già di un account aziendale o dell'istituto di istruzione e si vuole usare tale account per la versione di valutazione di Intune, seguire [queste istruzioni di iscrizione](/intune/account-sign-up).

* Se per la maggior parte delle operazioni IT e degli utenti viene usata una lingua diversa dalla propria, è necessario selezionare la lingua in **Where's your company located?** (Dov'è situata la tua azienda?).

2. Al termine del processo di registrazione, l'utente riceve un messaggio con le informazioni del nuovo account. <br/> ![Immagine delle informazioni sull'account](./media/2-end-of-sign-up-process.png) <br/>A questo punto, se si fa clic su **You're ready to go** (Pronto per procedere), si passa all'interfaccia di amministrazione di Office 365, in cui è possibile aggiungere utenti all'ambiente di test. <br/><br/>Tuttavia, se si desidera accedere direttamente al portale di Intune di Azure, aprire una nuova finestra del browser e digitare **https://portal.azure.com** nella barra degli indirizzi. Verrà visualizzata la pagina di accesso ad Azure, a cui è possibile accedere tramite le credenziali assegnate. Usare questo indirizzo per accedere alla versione di valutazione di Intune. <br/> ![Immagine della pagina di accesso al portale di Azure](./media/azure-portal-signin.png)

Al primo accesso al portale di Intune di Azure, Intune potrebbe non essere visibile nel dashboard di Azure. Per aggiungere il servizio Intune al dashboard di Azure:
1. Scegliere **Altri servizi >** nell'elenco dei servizi di Azure a sinistra del dashboard e immettere **Intune** nella casella di ricerca.
2. Scegliere **Intune** nell'elenco e selezionare la stella per aggiungere il servizio all'elenco dei servizi.<br/> ![Immagine della selezione di Intune dall'elenco dei servizi](./media/azure-add-intune1.png)
3. Scegliere quindi **Intune** nell'elenco dei servizi per aprire il dashboard di Intune.

Quando si esegue l'iscrizione per una versione di valutazione, all'indirizzo di posta elettronica specificato in fase di iscrizione verrà anche inviato un messaggio contenente le informazioni sul proprio account. Questo messaggio conferma che la versione di valutazione è attiva.



## <a name="keeping-the-admin-experiences-straight"></a>Esperienze diverse per l'amministrazione


Per il portale di Intune di Azure sono disponibili tre portali:
- Il dashboard di Intune in Azure ([portal.azure.com](https://portal.azure.com)) in cui è possibile esplorare le [funzionalità di Intune nel portale di Azure](what-is-intune.md).
- L'interfaccia di amministrazione di Office 365 ([portal.office.com](https://portal.office.com)) in cui è possibile aggiungere e gestire gli utenti se non si usa Azure Active Directory a tale scopo. È anche possibile gestire altri aspetti del proprio account, incluse la fatturazione e il supporto tecnico.
- La console di amministrazione di Intune ([manage.microsoft.com](https://manage.microsoft.com)) in cui è possibile esplorare le funzionalità che non sono ancora state aggiunte ad Azure.

In genere le operazioni vengono eseguite nel dashboard di Intune, illustrato di seguito. Questa console consente infatti di impostare e gestire i gruppi, i criteri, i dispositivi e le app.

È possibile passare alla console di amministrazione di Intune dal dashboard scegliendo **Portale classico** nella parte superiore del dashboard.

Per tornare al portale di Intune di Azure, immettere https://portal.azure.com nella barra degli indirizzi del browser e quindi scegliere di nuovo **Intune** nell'elenco dei servizi.

 ![Immagine del dashboard di Intune](./media/intune-azure-dashboard.png)


L'interfaccia di amministrazione di Office 365, illustrata di seguito, viene usata per aggiungere e gestire gli utenti e per altri aspetti dell'account, inclusi la fatturazione e il supporto.

![Immagine dell'interfaccia di amministrazione di Office 365](./media/office-admin-center.png)

Per passare dall'interfaccia di amministrazione di Office 365 al dashboard di Intune, immettere https://portal.azure.com nella barra degli indirizzi del browser. Scegliere **Intune** nell'elenco dei servizi.

Per tornare all'interfaccia di amministrazione di Office 365 da Intune, immettere https://portal.office.com nella barra degli indirizzi del browser. Se è già stato effettuato l'accesso in Intune, si passerà direttamente all'interfaccia di amministrazione di Office 365.

## <a name="next-steps"></a>Passaggi successivi

### <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure
Altre informazioni su [Intune nel portale di Azure](what-is-intune.md)

### <a name="integration-with-other-products"></a>Integrazione con altri prodotti
Per altre informazioni sull'uso degli account utente di Azure Active Directory con Intune, vedere:
- [Identity requirements](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview) (Requisiti di identità)
- [Determinare i requisiti di sincronizzazione delle directory](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Determinare i requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Altre informazioni sull'uso di [Intune con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
