---
title: Vantaggi di Intune App SDK
description: "Intune App SDK è disponibile per la piattaforma iOS e Android e abilita le funzionalità di gestione di app per dispositivi mobili con Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8a9b0c398c4b6dd46823ceaaefd68ee193ab4502
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="intune-app-sdk-overview"></a>Panoramica di Intune App SDK
Intune App SDK, disponibile per iOS e Android, consente di abilitare le app per i criteri di protezione delle app di Intune. Mira a ridurre al minimo la quantità di modifiche del codice richieste da uno sviluppatore di app. La maggior parte delle funzionalità dell'SDK possono infatti essere abilitate senza modificare il comportamento dell'app. Per un'esperienza avanzata per utenti finali e amministratori IT, è possibile usare le API per personalizzare il comportamento dell'app per le funzionalità che richiedono la partecipazione dell'app.

Dopo avere abilitato l'app per i criteri di protezione delle app, gli amministratori IT possono distribuire questi criteri per proteggere i dati aziendali all'interno dell'app.

## <a name="app-protection-features"></a>Funzionalità di protezione delle app

Di seguito sono disponibili alcuni esempi delle funzionalità di protezione delle app che possono essere abilitate con l'SDK.

### <a name="control-users-ability-to-move-corporate-files"></a>Controllare la capacità degli utenti di spostare file aziendali
Gli amministratori IT possono controllare dove possono essere spostati i dati aziendali o dell'istituto di istruzione nell'app. Ad esempio, è possibile distribuire un criterio che impedisce all'app di eseguire il backup dei dati aziendali nel cloud.

### <a name="configure-clipboard-restrictions"></a>Configurare le restrizioni per gli Appunti
Gli amministratori IT possono configurare il comportamento degli Appunti nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio per impedire agli utenti finali di tagliare o copiare dati dall'app per incollarli in un'app personale non gestita.

### <a name="enforce-encryption-on-saved-data"></a>Applicare la crittografia ai dati salvati
Gli amministratori IT possono applicare un criterio che assicura che i dati salvati nel dispositivo dall'app siano crittografati.

### <a name="remotely-wipe-corporate-data"></a>Cancellare i dati aziendali da remoto
Gli amministratori IT possono cancellare i dati aziendali da remoto mediante un'app gestita da Intune. Questa funzionalità è basata sull'identità ed elimina solo i file associati all'identità aziendale dell'utente finale. A questo scopo, la funzionalità richiede la partecipazione dell'app. L'app può specificare l'identità per cui è necessario cancellare i dati sulla base delle impostazioni utente. Se nell'applicazione non sono presenti queste impostazioni utente specifiche, il comportamento predefinito prevede la cancellazione della directory dell'applicazione e l'invio di una notifica all'utente finale relativa alla rimozione dell'accesso.

### <a name="enforce-the-use-of-a-managed-browser"></a>Imporre l'uso di un browser gestito
Gli amministratori IT possono imporre l'apertura dei collegamenti Web nell'app con l'[app Intune Managed Browser](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies). In questo modo, si garantisce che i collegamenti visualizzati in un ambiente aziendale si trovino all'interno del dominio delle app gestite da Intune.

### <a name="enforce-a-pin-policy"></a>Applicare un criterio PIN
Gli amministratori IT possono richiedere all'utente finale di immettere un PIN prima di accedere ai dati aziendali nell'app. In questo modo, si garantisce che la persona che usa l'app sia la stessa che inizialmente ha eseguito l'accesso con un account aziendale o dell'istituto di istruzione. Quando gli utenti finali configurano il PIN, Intune App SDK usa Azure Active Directory per verificare le credenziali degli utenti finali rispetto all'account di Intune registrato.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>Richiedere agli utenti di accedere all'app con l'account aziendale o dell'istituto di istruzione
Gli amministratori IT possono richiedere agli utenti di accedere all'app con il proprio account aziendale o dell'istituto di istruzione. Intune App SDK usa Azure Active Directory per fornire un'esperienza Single Sign-On, in cui le credenziali vengono immesse una sola volta e riutilizzate per gli accessi successivi. È supportata anche l'autenticazione di soluzioni di gestione delle identità federate con Azure Active Directory.

### <a name="check-device-health-and-compliance"></a>Verificare la conformità e l'integrità dei dispositivi
Gli amministratori IT possono controllare l'integrità del dispositivo e la sua conformità ai criteri di Intune prima che gli utenti finali accedano all'app. In iOS questo criterio controlla se il dispositivo è jailbroken. In Android questo criterio controlla se il dispositivo è rooted.

### <a name="multi-identity-support"></a>Supporto di più identità
Il supporto di più identità è una funzionalità dell'SDK che permette la coesistenza di account gestiti tramite criteri (aziendali) e account non gestiti (personali) in una singola app.

Ad esempio, molti utenti configurano account di posta elettronica sia personali che aziendali nelle app di Office per dispositivi mobili per iOS e Android. Quando un utente accede ai dati con il proprio account aziendale, l'amministratore IT deve essere certo che vengano applicati i criteri di protezione delle app. Quando invece un utente accede a un account di posta elettronica personale, questi dati devono esulare dal controllo dell'amministratore IT. Intune App SDK consente di ottenere questo risultato applicando i criteri di protezione delle app **solo** all'identità aziendale nell'app.

Questa funzionalità per il supporto di più identità contribuisce a risolvere il problema della protezione dei dati che le organizzazioni devono affrontare in presenza di app dello store che supportano sia account personali che aziendali.
 
### <a name="app-protection-without-device-enrollment"></a>Protezione delle app senza registrazione del dispositivo

>[!IMPORTANT]
>La protezione delle app di Intune senza registrazione del dispositivo non è attualmente disponibile con Intune App SDK per Android. È disponibile con gli strumenti per il wrapping delle app di Intune, l'SDK per iOS, il componente Xamarin per l'SDK e il plug-in Cordova per l'SDK.


Molti utenti con dispositivi personali vogliono accedere ai dati aziendali senza registrare il dispositivo personale in un provider di gestione di dispositivi mobili (MDM). Dato che la registrazione in una soluzione MDM richiede il controllo globale del dispositivo, gli utenti sono spesso riluttanti a fornire tale controllo all'azienda per i propri dispositivi personali.

La protezione delle app senza la registrazione del dispositivo consente al servizio Microsoft Intune di distribuire i criteri di protezione delle app a un'app in modo diretto, senza basarsi su un canale di gestione dei dispositivi.
