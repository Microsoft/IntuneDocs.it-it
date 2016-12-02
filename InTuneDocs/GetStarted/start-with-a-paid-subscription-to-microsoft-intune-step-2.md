---
title: Configurare un nome di dominio personalizzato | Microsoft Intune
description: Aggiungere un nome di dominio personalizzato per la sottoscrizione di Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 9fe78bca15ffee1e5e0e7e3758ff70b6bc92b619


---


# <a name="configure-a-custom-domain-name"></a>Configurare un nome di dominio personalizzato

Quando l'organizzazione si iscrive a un servizio Microsoft basato su cloud come Intune, l'utente riceve un nome di dominio iniziale ospitato in Azure Active Directory (AD) simile al seguente: **dominio.onmicrosoft.com**. In questo esempio, **dominio** è il nome scelto al momento dell'iscrizione e **onmicrosoft.com** è il suffisso assegnato agli account che si aggiungono alla sottoscrizione. Quando l'azienda dispone di un dominio personalizzato, è possibile configurare la propria istanza di Intune in modo da usare quel dominio anziché quello fornito con la sottoscrizione.

Prima di creare account utente oppure sincronizzare gli account dall'istanza locale di Active Directory, è consigliabile decidere se usare solo il dominio .onmicrosoft.com oppure aggiungere uno o più nomi di dominio personalizzati. La configurazione di un dominio personalizzato prima dell'aggiunta degli utenti può contribuire a semplificare la gestione delle identità per la sottoscrizione consentendo agli utenti di effettuare l'accesso con le stesse credenziali che usano per accedere ad altre risorse di dominio.

Quando si sottoscrive un servizio cloud Microsoft, l'istanza del servizio ottenuta è un [tenant di Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) di Microsoft, che fornisce identità e servizi di directory per il servizio cloud. Poiché le attività necessarie per configurare Intune in modo da usare il nome di dominio personalizzato aziendale sono le stesse che per altri tenant Azure Active Directory, è possibile usare le informazioni e le procedure disponibili in [Aggiungere un nome di dominio personalizzato ad Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Per altre informazioni sull'uso del dominio personalizzato con un servizio basato su cloud Microsoft, vedere [Panoramica concettuale dei nomi di dominio personalizzati in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Non è possibile rinominare o rimuovere il nome di dominio iniziale. È tuttavia possibile aggiungere, verificare o rimuovere i propri nomi di dominio personalizzati da usare con Intune. Ciò è utile se si vuole mantenere l'identità del proprio business.

## <a name="to-add-and-verify-your-custom-domain"></a>Per aggiungere e verificare il dominio personalizzato

1. Passare al [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) e accedere con l'account amministratore.

2. Nel riquadro di spostamento scegliere **Impostazioni** &gt; **Domini**.

3. Scegliere **Aggiungi dominio** e digitare il nome di dominio personalizzato.

4. Verrà visualizzata la finestra di dialogo **Verifica dominio** con i valori necessari per creare il record TXT nel provider di hosting DNS.
    - **Utenti di GoDaddy**: il portale di gestione di Office 365 reindirizza l'utente alla pagina di accesso di GoDaddy. Dopo l'immissione delle credenziali e l'accettazione dell'accordo di autorizzazione alla modifica del dominio, il record TXT viene creato automaticamente. In alternativa è possibile [creare il record TXT](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US).
    - **Utenti di Register.com**: seguire le [istruzioni dettagliate](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) per creare il record TXT.

    > [!TIP]
    > Assicurarsi di creare un alias DNS (CNAME) per la [registrazione dei dispositivi Windows](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) durante le modifiche al provider di hosting DNS.

I passaggi per aggiungere e verificare un dominio personalizzato possono in alternativa essere [eseguiti in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/).

In uno scenario di cloud ibrido, dopo l'aggiunta del nome di dominio personalizzato e la verifica dell'appartenenza di quest'ultimo all'organizzazione, è possibile continuare a gestire gli account utente di Active Directory locale, quindi sincronizzare il dominio con Azure AD.

## <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Per sincronizzare gli utenti locali con Azure AD##

1. [Aggiungere il suffisso UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) per il dominio personalizzato in Active Directory locale.
2. Impostare il nuovo suffisso UPN per gli utenti locali da importare.
3. Eseguire la [sincronizzazione di Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) per integrare gli utenti locali con Azure AD.
4. Dopo la sincronizzazione delle informazioni degli account utente è possibile assegnare licenze di Microsoft Intune usando il [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx).

### <a name="see-also"></a>Vedere anche

[Informazioni sul dominio onmicrosoft.com iniziale in Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)
### <a name="next-steps"></a>Passaggi successivi
A questo punto, il passaggio 2 della *Guida introduttiva a Intune* è stato completato.

>[!div class="step-by-step"]

>[&larr; **Accedere a Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Aggiungere utenti a Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Nov16_HO4-->


