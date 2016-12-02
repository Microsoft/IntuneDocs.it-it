---
title: Dispositivi mobili e browser supportati | Microsoft Intune
description: Dispositivi mobili e computer supportati da Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>Dispositivi mobili e computer supportati

È possibile registrare e successivamente gestire i tipi di dispositivo seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

La registrazione dei dispositivi offre le [funzionalità descritte di seguito](/Intune/get-started/choose-how-to-manage-devices).

In alternativa, è possibile gestire i PC Windows con il software client PC Intune. Il software client per PC di Intune supporta Windows 7 e versione successiva, ad eccezione di Windows 10 Home. La gestione dei PC con il software client offre [queste funzionalità](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

I clienti con Enterprise Management Suite possono anche usare Azure Active Directory (Azure AD) per registrare i dispositivi Windows 10.

## <a name="microsoft-intune-supported-web-browsers"></a>Browser Web supportati da Microsoft Intune

Per le svariate attività amministrative è necessario usare uno dei siti Web di amministrazione seguenti.

- [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Console di amministrazione di Microsoft Intune](https://admin.manage.microsoft.com/)

> [!Note]
> Microsoft Edge e i browser per dispositivi mobili non sono supportati per la console di amministrazione perché non supportano [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La console di Intune entro un certo periodo lascerà l'esperienza Silverlight. Infine, tutte le funzionalità di gestione delle applicazioni e dei dispositivi mobili di Intune saranno [disponibili nel nuovo portale di Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

|Funzionalità di Intune |Browser supportati|
|---------|---------|
|Console di amministrazione di Intune     |  Internet Explorer 10 o versione successiva<br /><br />Google Chrome (versioni precedenti alla versione 42)<br /><br />Mozilla Firefox con Silverlight abilitato<br /><br />**Nota:** Microsoft Edge e i browser per dispositivi mobili non sono supportati per la console di amministrazione.                      
|Portale di amministrazione di Office 365     |Tutti i browser, inclusi i browser per dispositivi mobili e i browser gestiti  |
|Sito Web del portale aziendale     |**Nei dispositivi mobili:** usare il Web browser predefinito per ogni piattaforma supportata   <br /><br />**Nei PC Windows:** Internet Explorer 10 o versione successiva oppure Microsoft Edge<br /><br />**In Mac OS X 10.9 o versioni successive:** Apple Safari    |

> [!Note]
> Microsoft Edge e i browser per dispositivi mobili non sono supportati per la console di amministrazione perché non supportano [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La console di Intune entro un certo periodo lascerà l'esperienza Silverlight. Infine, tutte le funzionalità di gestione delle applicazioni e dei dispositivi mobili di Intune saranno [disponibili nel nuovo portale di Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**L'amministratore tenant usa questo portale per gestire la propria sottoscrizione**, incluse le seguenti attività, quando il proprio ruolo di amministratore lo consente:

- Gestire gli account utente per la sottoscrizione e configurare la sincronizzazione delle directory da Active Directory locale.
- Gestire gruppi di utenti, denominati gruppi di sicurezza.
- Assegnare licenze agli utenti per usare Intune.
- Configurare il nome di dominio da usare con la sottoscrizione. Il nome di dominio definisce l'account con cui gli utenti effettuano l'accesso.
- Gestire la fatturazione e i dettagli di acquisto della propria sottoscrizione, incluso il numero di licenze disponibili o la quantità di spazio di archiviazione cloud usabile.
- Trovare collegamenti per visualizzare lo stato del servizio Intune.
- Gli amministratori tenant possono accedere al portale di Office 365 per gestire la sottoscrizione anche se all'account usato non è assegnata una licenza di Intune.
- Qualsiasi utente che dispone di una licenza per Intune ma non è un amministratore può usare il portale per ripristinare la password del proprio account e modificare il proprio profilo.
- Per accedere al portale di Office 365, lo stato di accesso dell'account deve essere **Consentito**. Questo stato non equivale a ricevere una licenza per la sottoscrizione. Per impostazione predefinita, tutti gli account utente hanno lo stato **Consentito**.


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Console di amministrazione di Microsoft Intune](https://manage.microsoft.com/)

**L'amministratore del servizio usa questo portale per gestire le operazioni quotidiane** tra cui:

- Impostare i criteri per computer e dispositivi mobili.
- Caricare e distribuire software come app e aggiornamenti software.
- Gestire Endpoint Protection nei computer.
- Visualizzare lo stato dei dispositivi ed eseguire report.
- Accedere a questo portale. Per accedere al portale è necessario avere le autorizzazioni di amministratore del servizio o essere un amministratore tenant con il ruolo Amministratore globale.


Solo gli utenti con autorizzazioni di amministratore del servizio o di amministratore tenant con il ruolo Amministratore globale possono accedere al portale. Per accedere alla console di amministrazione, è necessario che l'account abbia una licenza per l'uso di Intune e lo stato di accesso **Consentito**.



<!--HONumber=Nov16_HO4-->


