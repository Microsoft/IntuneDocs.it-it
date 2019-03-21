---
title: Che cosa avviene quando si installa l'app Portale aziendale per Android
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d8af8b01de3b9782f487e29a9f993ceaf32aac6
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55838156"
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-android-device-in-intune"></a>Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo Android in Intune?

Se l'organizzazione richiede di installare l'app Portale aziendale di Intune sul dispositivo Android, è legittimo chiedersi perché. In questo articolo vengono descritti lo scopo e le funzionalità dell'applicazione&mdash;e in che modo protegge i dati di lavoro e scolastici che si consultano e memorizzano nel dispositivo.

## <a name="gets-your-device-managed"></a>Attiva la gestione del dispositivo
L'app Portale aziendale consente di gestire, o *registrare*, il dispositivo nel sistema di gestione dei dispositivi della propria organizzazione. Prima di autorizzare la connessione alla rete dell'organizzazione, l'istituto di istruzione o l'azienda desidera accertarsi che il dispositivo sia sicuro e affidabile. Per poter accedere alle risorse aziendali o dell'istituto di istruzione, il dispositivo dovrà soddisfare i criteri di sicurezza definiti per i dispositivi dell'organizzazione. 

Il supporto tecnico dell'azienda o l'amministratore IT configura tali criteri nel sistema di gestione dei dispositivi aziendali. Quando si registra il dispositivo, i criteri vengono inviati. 

Esempi di alcuni dei criteri che l'organizzazione potrebbe richiedere:
* Configurazione di una password o di un PIN
* Limitare l'accesso dopo un determinato numero di tentativi di accesso
* Garantire che il dispositivo non sia jailbroken o rooted
* Installazione delle app necessarie per il lavoro

L'app Portale aziendale guida ogni passaggio della registrazione e configura le impostazioni del dispositivo in modo da soddisfare i requisiti dell'organizzazione. In alcuni casi, l'app emetterà un avviso o una richiesta prima di apportare modifiche.

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>Consente di accedere alle app aziendali e dell'istituto di istruzione, ai file di lavoro e alla posta elettronica
Per la registrazione, l'app Portale aziendale richiede la connessione al proprio account aziendale o dell'istituto di istruzione. Dopo l'autenticazione, sarà possibile accedere alla posta elettronica aziendale e alla rete, ai file e alle app della propria organizzazione. 

Le organizzazioni a volte richiedono di installare app di lavoro o di sicurezza, ad esempio Microsoft Office o Mobile Threat Defense. Queste app richieste dall'organizzazione o rese disponibili da essa sono presenti nell'app Portale aziendale.

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>Consente di ripristinare in remoto un dispositivo smarrito o rubato (se il dispositivo supporta la procedura)
Se un dispositivo viene smarrito o rubato, è possibile accedere al sito Web o all'app Portale aziendale da un altro dispositivo e ripristinare le impostazioni di fabbrica sul telefono. Questa funzionalità è utile se il dispositivo smarrito contiene dati di lavoro proprietari che non devono essere resi disponibili ad altri. Poiché il dispositivo è registrato nel servizio di gestione, il supporto tecnico dell'azienda o l'amministratore IT può reimpostarlo.  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>Avvisa della presenza di aggiornamenti dei criteri e dei requisiti
Ogni otto ore l'app Portale aziendale si sincronizza con il provider di gestione dei dispositivi mobili dell'organizzazione. Se si desidera eseguire un controllo più frequente, il supporto tecnico aziendale o l'utente può avviare una sincronizzazione manuale. Durante l'operazione di controllo, l'app:  
* Scarica tutti gli aggiornamenti dei criteri o dell'app resi disponibili dal supporto tecnico dell'azienda.  
* Invia gli aggiornamenti dell'inventario hardware. Questi aggiornamenti non contengono informazioni personali.  
* Invia gli aggiornamenti dell'inventario delle app aziendali. Questi aggiornamenti non contengono informazioni personali.  

Se il dispositivo smette di essere sincronizzato con i requisiti dell'organizzazione, l'app Portale aziendale avviserà l'utente. L'app segnala il problema e i passaggi da eseguire per risolvere il problema. L'accesso alle risorse di lavoro o dell'istituto di istruzione potrebbe essere sospeso in attesa che il dispositivo soddisfi di nuovo i requisiti. Nell'app Portale aziendale questo stato è indicato come *Non conforme*. 

## <a name="permits-company-support-access-to-your-device"></a>Consente di accedere al supporto aziendale per il dispositivo
Quando si registra il dispositivo nell'app Portale aziendale, al supporto tecnico dell'azienda o all'amministratore IT viene concesso l'accesso al dispositivo per motivi limitati e significativi. Gli utenti possono:  

* Ripristinare le impostazioni predefinite dal produttore del dispositivo. Come indicato in precedenza, l'utente può reimpostare personalmente il dispositivo. Tuttavia, se l'utente non riesce ad accedere immediatamente all'app Portale aziendale, l'azienda può reimpostare il dispositivo per conto dell'utente.  

* Rimuovere tutti i dati correlati alla società. L'organizzazione può rimuovere i dati aziendali dal dispositivo se l'utente lascia l'azienda o se il dispositivo diventa non gestito. I dati personali e le impostazioni dell'utente non vengono rimossi e rimangono nel dispositivo.  

* Impostare i requisiti per il dispositivo, ad esempio richiedere una password o un PIN. In questo caso, tramite le notifiche dell'app si verrà informati che il dispositivo non è conforme. Il supporto tecnico aziendale può anche limitare il numero di volte che è possibile immettere una password non corretta nel dispositivo. Troppi tentativi di immettere una password errata potrebbero comportare il blocco del dispositivo.  

* Richiedere di accettare i termini e le condizioni.  

* Disabilitare la fotocamera. Lo scopo di questo criterio è evitare che informazioni proprietarie vengano fotografate, nonché rimuovere elementi di distrazione negli istituti di istruzione. Le scuole potrebbero disabilitare le fotocamere digitali nei dispositivi in aula affinché gli studenti non possano condividere i contenuti delle verifiche.  

* Imporre la crittografia di tutti i dati del dispositivo. Se il dispositivo viene smarrito o rubato, questo criterio consente di proteggere i dati al suo interno. Permette inoltre di proteggere i dati che vengono condivisi tra i dispositivi e le app.  

Serve assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.
