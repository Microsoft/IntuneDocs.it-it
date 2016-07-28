---
title: Nomi di dominio per Microsoft Intune | Microsoft Intune
description: aggiunta del nome di dominio per Intune
keywords: 
author: andredm7
manager: swadhwa
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32723f5b2c92073dda43a0b1f36a48ded0e13ba3
ms.openlocfilehash: 2adbe1e4a92af5302550a8b78069bc49d725dbc3


---



# Nomi di dominio personalizzati con Microsoft Intune

I passaggi per aggiungere e verificare un dominio personalizzato possono in alternativa essere [eseguiti in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/).

Quando l'organizzazione si iscrive a un servizio Microsoft basato su cloud come Intune, l'utente riceve un nome di dominio iniziale simile al seguente: **dominio.onmicrosoft.com**. In questo esempio, **dominio** è il nome scelto al momento dell'iscrizione e **onmicrosoft.com** è il suffisso assegnato agli account che si aggiungono alla sottoscrizione.

Non è possibile rinominare o rimuovere il nome di dominio iniziale. È tuttavia possibile aggiungere, verificare o rimuovere i propri nomi di dominio personalizzati da usare con Intune. Ciò è utile se si vuole mantenere l'identità del proprio business.

## Per aggiungere e verificare il dominio personalizzato 

1. Passare al [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) e accedere con l'account amministratore.
    > [!IMPORTANT]
    > Leggere l'annuncio     [Unione del portale per gli account di Intune e del portale di gestione di Office 365](https://docs.microsoft.com/en-us/intune/deploy-use/account-portal-merged-with-Office-365) per altre informazioni sulla modalità di gestione di utenti, gruppi e domini di Microsoft Intune.
2. Nel riquadro di spostamento scegliere **Impostazioni** &gt; **Domini**.
3. Scegliere **Aggiungi dominio** e digitare il nome di dominio personalizzato.
4. Verrà visualizzata la finestra di dialogo **Verifica dominio** con i valori necessari per creare il record TXT nel provider di hosting DNS.
    - **Utenti di GoDaddy**: il portale di gestione di Office 365 reindirizza l'utente alla pagina di accesso di GoDaddy. Dopo l'immissione delle credenziali e l'accettazione dell'accordo di autorizzazione alla modifica del dominio, il record TXT viene creato automaticamente. In alternativa è possibile [creare il record TXT](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US).
    - **Utenti di Register.com**: seguire le [istruzioni dettagliate](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) per creare il record TXT.

    > [!TIP] 
    > Assicurarsi di creare un alias DNS (CNAME) per la [registrazione dei dispositivi Windows](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) durante le modifiche al provider di hosting DNS.

In uno scenario di cloud ibrido, dopo l'aggiunta del nome di dominio personalizzato e la verifica dell'appartenenza di quest'ultimo all'organizzazione, è possibile continuare a gestire gli account utente di Active Directory locale, quindi sincronizzare il dominio con Azure AD.

## Per sincronizzare gli utenti locali con Azure AD##

1. [Aggiungere il suffisso UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) per il dominio personalizzato in Active Directory locale.
2. Impostare il nuovo suffisso UPN per gli utenti locali da importare.
3. Eseguire la [sincronizzazione di Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) per integrare gli utenti locali con Azure AD.
4. Dopo la sincronizzazione delle informazioni degli account utente è possibile assegnare licenze di Microsoft Intune usando il [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx).

### Vedere anche

[Informazioni sul dominio onmicrosoft.com iniziale in Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


