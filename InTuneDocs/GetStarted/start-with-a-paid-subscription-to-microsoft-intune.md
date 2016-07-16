---
title: Guida introduttiva a Intune | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: ca0ca74357b59d9cc6fbf4ec7eb237dff972c411


---


# Guida introduttiva a Intune
Questa guida introduttiva illustra la procedura di configurazione di una sottoscrizione a pagamento di Microsoft Intune per iniziare a gestire in modo rapido e semplice i dispositivi mobili e i PC Windows usati dall'organizzazione. È possibile seguire tutti i passaggi nell'ordine o ignorare quelli che non si applicano a un ambiente specifico o alle esigenze aziendali.

>[!NOTE]
>Questo articolo è incentrato sulla configurazione di Intune come un servizio autonomo. Se invece si sta usando Microsoft System Center Configuration Manager per gestire computer e server, è possibile [estendere Configuration Manager per gestire i dispositivi mobili](https://technet.microsoft.com/library/jj884158.aspx) connettendo Intune a Configuration Manager in una distribuzione ibrida del software MDM per la gestione anche di dispositivi mobili.

La procedura descritta in questa guida introduttiva condivide molti passaggi presenti nella [guida di valutazione di Intune](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune). Tuttavia, dopo la valutazione e quando tutto è pronto per iniziare a gestire i dispositivi mobili, è necessario soddisfare alcuni requisiti aggiuntivi. Questi requisiti variano a seconda dei requisiti di business e infrastruttura di rete attuali tra cui:

-   Sincronizzazione degli account Active Directory locali con Intune e Azure Active Directory

-   Aggiornamento dei record del dominio pubblico e dei servizi DNS con il registrar

-   Personalizzazione delle funzionalità di Intune per l'uso in produzione

>[!TIP]
>Se si acquistano almeno 150 licenze per Microsoft Intune in un piano idoneo, è possibile utilizzare "FastTrack Center Benefit", un servizio mediante il quale gli specialisti Microsoft collaborano con gli utenti per preparare l’ambiente per Intune. Vedere [FastTrack Center Benefit per Intune](https://technet.microsoft.com/library/mt228265.aspx).


## Prima di iniziare
Questa guida è utile nel momento in cui si avvia una sottoscrizione a pagamento e quando è possibile distribuire Intune nonché apportare modifiche all'infrastruttura di rete esistente. Si va dalle semplici operazioni di aggiunta o aggiornamento dei record DNS interni ed esterni fino alla sincronizzazione degli account utente Active Directory con Azure Active Directory. Indipendentemente dalla combinazione scelta di funzionalità di gestione di Intune dei dispositivi mobili, è necessario pianificare attentamente l'interazione di Intune con i componenti e i servizi di rete esistenti. In particolare, è necessario controllare gli aspetti seguenti:

-   **Gestione dell'identità utente**: per la maggior parte delle organizzazioni di medie e grandi dimensioni, la connessione dei servizi di directory esistenti a Intune tramite Azure Active Directory costituisce la soluzione migliore e più conveniente per gestire l'identità utente con Intune. Questo vale in particolare se si usano già altri servizi cloud Microsoft, come Office 365 o Exchange Online. La sincronizzazione degli account utente esistenti con [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) consente di connettere in modo semplice e rapido l'istanza locale di Active Directory ad Azure Active Directory e di configurare un'esperienza di autenticazione Single Sign-On per gli utenti.

-   **Impatto sul DNS**: se si desidera usare il proprio nome di dominio anziché il dominio onmicrosoft.com predefinito ottenuto al momento della registrazione a Intune, saranno necessari alcuni aggiornamenti dei record DNS pubblici. Gli aggiornamenti dei record DNS sono necessari per consentire ai dispositivi mobili di individuare il servizio di Intune e garantire il corretto funzionamento di quello di gestione relativo alla propria sottoscrizione per la gestione di tutti i dispositivi in uso da parte dell'organizzazione.

## Tenere a portata di mano gli elementi seguenti
Per iniziare Quando si inizia a usare la sottoscrizione a pagamento di Intune sono necessari gli elementi seguenti:

### Un dispositivo con web browser abilitato per Silverlight
Questo dispositivo sarà necessario per accedere alla console di amministrazione di Intune in cui gestire i dispositivi, le applicazioni e i criteri. Sarà necessario anche un web browser per accedere al portale aziendale basato sul Web quando non si esegue l'accesso all'app Portale aziendale da un dispositivo mobile. Per semplificare l'operazione, è possibile usare l'impostazione della "modalità di privacy" nello stesso browser usato per l'amministrazione di Intune. Ad esempio, in Internet Explorer è possibile fare clic su **Strumenti**&gt;**InPrivate Browsing**.

>[!TIP]
>A causa di questo requisito, il browser Microsoft Edge non è supportato per accedere alla console di amministrazione di Intune.


### Certificati per i dispositivi mobili
Se si intende gestire dispositivi iOS o Windows Phone con Intune, sono necessari certificati e account per recuperare tali certificati. Per gestire i dispositivi Android non sono necessari certificati aggiuntivi.

- Non è necessario alcun certificato per gli utenti di **Windows Phone 8.1** che installano l'app Portale aziendale dallo Store. È richiesto tuttavia un [certificato di firma codice Symantec](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do) per **Windows Phone 8.0** o per usare Intune con lo scopo di distribuire l'app Portale aziendale in dispositivi Windows Phone 8.1.

>[!NOTE]
>Questa guida introduttiva presuppone che gli utenti scarichino l'app Portale aziendale dallo Store in un dispositivo Windows Phone 8.1 o versioni successive. Per informazioni sul supporto di Windows Phone 8.0, vedere [Configurare la gestione del dispositivo per Windows Phone 8.0](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).

- Non sono previsti requisiti di certificato per **PC Windows** o **dispositivi Windows RT** durante la registrazione dei PC Windows come dispositivi o [l'installazione del client di PC Windows per Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).

- Per i dispositivi **iOS** o **Mac OS X** è necessario richiedere un certificato Apple Push Notification Service di Apple, come descritto nel passaggio 3 di [Configurare la gestione dei dispositivi iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

### Passaggi successivi
È ora di iniziare con la guida introduttiva di Intune!

>[!div class="step-by-step"]
[**Accedere a Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jun16_HO4-->


