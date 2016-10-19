---
title: Vantaggi di Intune App SDK | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 74120a8228a5851cb8f8dda1a324d1f9119befaf
ms.openlocfilehash: 3abc6ad9fcf0acdf9ecd61b39f056f770a2a0e3c


---

# Panoramica di Intune App SDK
Intune App SDK è disponibile per la piattaforma iOS e Android e abilita le funzionalità di gestione di app per dispositivi mobili con Microsoft Intune. Mira a ridurre al minimo la quantità di modifiche del codice richieste da uno sviluppatore di app. La maggior parte delle funzionalità dell'SDK possono infatti essere abilitate senza modificare il comportamento dell'app. Per un'esperienza avanzata per utenti finali e amministratori IT, è possibile usare le API per personalizzare il comportamento dell'app per le funzionalità che richiedono la partecipazione dell'app. 

Dopo avere abilitato l'app, gli amministratori IT possono distribuire i criteri alle app gestite da Intune e sfruttare queste funzionalità per proteggere i dati aziendali.

## Funzionalità comuni

### Controllare la capacità degli utenti di spostare documenti aziendali
Gli amministratori IT possono controllare lo spostamento di file di documenti aziendali nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisce alle app di backup dei file di eseguire il backup dei dati aziendali nel cloud.

### Configurare le restrizioni per gli Appunti
Gli amministratori IT possono configurare il comportamento degli Appunti nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisca agli utenti finali di usare gli Appunti per tagliare/copiare da un'app gestita da Intune e incollare in un'app personale non gestita.

### Applicare la crittografia ai dati salvati
Gli amministratori IT possono applicare un criterio che assicura che i dati salvati nel dispositivo dall'app siano crittografati.

### Cancellare i dati aziendali da remoto
Gli amministratori IT possono cancellare i dati aziendali da remoto mediante un'app gestita da Intune. Questa funzionalità è basata sull'identità ed elimina solo i file associati all'identità aziendale dell'utente finale. A questo scopo, la funzionalità richiede la partecipazione dell'app. L'app può specificare l'identità per cui è necessario cancellare i dati sulla base delle impostazioni utente. Se nell'applicazione non sono presenti queste impostazioni utente specifiche, il comportamento predefinito prevede la cancellazione della directory dell'applicazione e l'invio di una notifica all'utente finale relativa alla rimozione dell'accesso.

### Imporre l'uso di un browser gestito
Gli amministratori IT possono imporre l'uso di un'app browser gestita da Intune quando vengono aperti collegamenti dalle app gestite da Intune. In questo modo, si garantisce che i collegamenti visualizzati in un ambiente aziendale si trovino all'interno del dominio delle app gestite da Intune.

### Applicare un criterio PIN
Gli amministratori IT possono applicare un criterio PIN quando viene avviata un'app gestita da Intune. In questo modo, si garantisce che l'utente che avvia l'app sia lo stesso che inizialmente ha eseguito l'accesso con un account aziendale o dell'istituto di istruzione registrato. Quando gli utenti finali configurano il PIN, Intune App SDK usa Azure Active Directory per verificare le credenziali degli utenti finali rispetto all'account di Intune registrato.

### Richiedere agli utenti di immettere le credenziali prima di avviare le app
Gli amministratori IT possono richiedere agli utenti finali di immettere le proprie credenziali per avviare un'app gestita da Intune. Intune App SDK usa Azure Active Directory per fornire un'esperienza Single Sign-On, in cui le credenziali vengono immesse una sola volta e riutilizzate per gli accessi successivi. È supportata anche l'autenticazione di soluzioni di gestione delle identità [federate con Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### Verificare la conformità e l'integrità dei dispositivi
Gli amministratori IT possono controllare l'integrità del dispositivo e la sua conformità ai criteri aziendali prima che gli utenti finali accedano alle app gestite da Intune. Nella piattaforma iOS questo criterio controlla se il dispositivo è jailbroken. Nella piattaforma Android questo criterio controlla se il dispositivo è rooted.

### Supporto di più identità SDK
Il supporto di più identità è una funzionalità che permette la coesistenza di account gestiti tramite criteri (aziendali) e account non gestiti (personali) in una singola app.

Ad esempio, molti utenti configurano account di posta elettronica sia personali che aziendali nell'app Outlook per iOS e Android. Quando un utente accede ai dati nel proprio account aziendale, l'amministratore IT deve accertarsi che venga applicata la gestione dei criteri MAM. Quando invece un utente accede a un account di posta elettronica personale, questi dati devono esulare dal controllo dell'amministratore IT. Microsoft Intune raggiunge questo obiettivo applicando i criteri di gestione solo all'account aziendale nell'applicazione. Questa funzionalità multi-identità contribuisce a risolvere il problema della protezione dei dati che le organizzazioni devono affrontare in presenza di dispositivi e app che supportano account personali e aziendali.

* **Supporto di più identità**: le API di Microsoft Intune App SDK consentono di specificare un nome dell'entità utente (UPN) con specifiche operazioni sui dati, ad esempio le operazioni relative agli Appunti e ai file. L'SDK usa il nome UPN per individuare la corrispondenza con la chiamata eseguita all'UPN usato per registrare il dispositivo nel servizio Microsoft Intune. Se i nomi UPN corrispondono, la chiamata viene considerata come una chiamata di "dati aziendali" e i dati vengono protetti; se invece non corrispondono, la chiamata viene considerata come una chiamata di "dati personali" e i dati non vengono protetti.

### Gestione di app senza registrazione del dispositivo

>[!IMPORTANT]
>La gestione di app mobili di Intune senza registrazione del dispositivo è attualmente disponibile solo con Intune App SDK per iOS. 


Molti utenti con dispositivi personali vogliono visualizzare e usare i dati aziendali senza registrare il dispositivo personale con un prodotto di gestione di dispositivi mobili (MDM). Dato che la registrazione MDM richiede il controllo globale del dispositivo, gli utenti sono riluttanti a fornire tale controllo globale sui propri dispositivi personali all'azienda.

La gestione delle app senza la registrazione del dispositivo consente al servizio Microsoft Intune di distribuire i criteri MAM a un'app in modo diretto, senza basarsi su un canale MDM. Eliminata la necessità di un canale MDM, non è necessaria la registrazione MDM.



<!--HONumber=Sep16_HO4-->


