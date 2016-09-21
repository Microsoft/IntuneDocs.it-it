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
ms.sourcegitcommit: 952cfa4f23f8ba080ce53f6785baceb8a0a367c6
ms.openlocfilehash: ce8fa172c68fed7a1398cd5b1263ac970b87559b


---

# Panoramica di Intune App SDK
Intune App SDK è disponibile per la piattaforma iOS e Android e abilita le funzionalità di gestione di app per dispositivi mobili con Microsoft Intune. Un altro obiettivo è quello di ridurre la quantità di modifiche al codice necessarie per lo sviluppatore. La maggior parte delle funzionalità SDK possono infatti essere abilitate senza modificare il comportamento dell'app. Per un'esperienza avanzata per utenti finali e amministratori IT, è possibile usare le API per personalizzare il comportamento dell'app per le funzionalità che richiedono la partecipazione dell'app. Dopo avere abilitato l'app, gli amministratori IT possono distribuire i criteri alle app gestite da Intune e sfruttare queste funzionalità per proteggere i dati aziendali.

## Funzionalità comuni

### Controllare la capacità degli utenti di spostare documenti aziendali
Gli amministratori IT possono controllare lo spostamento di file di documenti aziendali nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisce alle app di backup dei file di eseguire il backup dei dati aziendali nel cloud.

### Configurare le restrizioni per gli Appunti
Gli amministratori IT possono configurare il comportamento degli Appunti nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisca agli utenti finali di usare gli Appunti per tagliare/copiare da un'app gestita da Intune e incollare in un'app non gestita.

### Configurare le restrizioni per l'acquisizione dello schermo
Gli amministratori IT possono impedire agli utenti di acquisire la schermata se è visualizzata un'app gestita da Intune. L'applicazione di questa restrizione impedisce l'acquisizione e la divulgazione di contenuti aziendali riservati. Questa funzionalità è disponibile solo per i dispositivi Android.

### Applicare la crittografia ai dati salvati
Gli amministratori IT possono applicare un criterio che assicura che i dati salvati nel dispositivo dall'app siano crittografati.

### Cancellare i dati aziendali da remoto
Gli amministratori IT possono cancellare i dati aziendali da un'app gestita da Intune quando viene annullata la registrazione del dispositivo in Microsoft Intune. Questa funzionalità è basata sull'identità ed elimina solo i file correlati all'identità aziendale dell'utente finale. A questo scopo, la funzionalità richiede la partecipazione dell'app. L'app può specificare l'identità per cui è necessario cancellare i dati sulla base delle impostazioni utente. Se nell'applicazione non sono presenti queste impostazioni utente specifiche, il comportamento predefinito prevede la cancellazione della directory dell'applicazione e l'invio di una notifica all'utente finale relativa alla rimozione dell'accesso alle risorse aziendali.

### Imporre l'uso di un browser gestito
Gli amministratori IT possono imporre l'uso di un browser gestito quando vengono aperti collegamenti dalle app gestite da Intune. L'uso di un browser gestito da Microsoft Intune contribuisce a garantire che i collegamenti visualizzati nei messaggi di posta elettronica (che si trovano in un client di posta elettronica gestito da Intune) restino all'interno del dominio delle app gestite da Intune.

### Applicare un criterio PIN
Gli amministratori IT possono applicare un criterio PIN quando viene avviata un'app gestita da Intune. Questo criterio consente di verificare che gli utenti finali che hanno registrato i propri dispositivi in Microsoft Intune siano le stesse persone che stanno avviando le app. Quando gli utenti finali configurano il PIN, Intune App SDK usa Azure Active Directory per verificare le credenziali degli utenti finali rispetto alle credenziali di registrazione del dispositivo.

### Richiedere agli utenti di immettere le credenziali prima di avviare le app
Gli amministratori IT possono richiedere agli utenti finali di immettere le proprie credenziali per avviare un'app gestita da Intune. Intune App SDK usa Azure Active Directory per fornire un'esperienza Single Sign-On, in cui le credenziali vengono immesse una sola volta e riutilizzate per gli accessi successivi. È supportata anche l'autenticazione di soluzioni di gestione delle identità [federate con Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### Verificare la conformità e l'integrità dei dispositivi
Gli amministratori IT possono controllare l'integrità del dispositivo e la sua conformità ai criteri aziendali prima che gli utenti finali accedano alle app gestite da Intune. Nella piattaforma iOS questo criterio controlla se il dispositivo è jailbroken. Nella piattaforma Android questo criterio controlla se il dispositivo è rooted.

## Funzionalità in anteprima
Microsoft Intune App SDK include diverse funzionalità in "anteprima". È possibile iniziare l'integrazione con le API in anteprima, ma solo a scopo di test. Si noti che queste anteprime sono aggiuntive e non sostitutive rispetto agli scenari esistenti.

### Supporto di più identità di Microsoft Intune App SDK
Il supporto di più identità è una funzionalità che permette la coesistenza di account gestiti tramite criteri (aziendali) e account non gestiti (personali) in una singola app.

### Esempio di scenario multi-identità
Molti utenti configurano account di posta elettronica sia personali che aziendali nell'app Outlook per iOS e Android. Quando un utente accede ai dati nel proprio account aziendale, l'amministratore IT deve accertarsi che venga applicata la gestione dei criteri MAM. Quando invece un utente accede a un account di posta elettronica personale, questi dati devono esulare dal controllo dell'amministratore IT. Microsoft Intune raggiunge questo obiettivo applicando i criteri di gestione solo all'account aziendale nell'applicazione. Questa funzionalità multi-identità contribuisce a risolvere il problema della protezione dei dati che le organizzazioni devono affrontare in presenza di dispositivi e app che supportano account personali e aziendali.

### Come supportare più identità
Le API in anteprima consentono di specificare un nome dell'entità utente (UPN) con specifiche operazioni sui dati, ad esempio le operazioni relative agli Appunti e ai file. Microsoft Intune App SDK usa il nome UPN per individuare la corrispondenza con la chiamata eseguita all'UPN usato per registrare il dispositivo nel servizio Microsoft Intune. Se i nomi UPN corrispondono, la chiamata viene considerata come una chiamata di "dati aziendali" e i dati vengono protetti; se invece non corrispondono, la chiamata viene considerata come una chiamata di "dati personali" e i dati non vengono protetti.

### Gestione di app senza registrazione del dispositivo
Molti utenti con dispositivi personali vogliono visualizzare e usare i dati aziendali senza registrare il dispositivo personale con un prodotto di gestione di dispositivi mobili (MDM). Dato che la registrazione MDM richiede il controllo globale del dispositivo, gli utenti sono riluttanti a fornire tale controllo globale sui propri dispositivi personali all'azienda.

La gestione delle app senza la registrazione del dispositivo consente al servizio Microsoft Intune di distribuire i criteri MAM a un'app in modo diretto, senza basarsi su un canale MDM. Eliminata la necessità di un canale MDM, non è necessaria la registrazione MDM.




<!--HONumber=Sep16_HO2-->


