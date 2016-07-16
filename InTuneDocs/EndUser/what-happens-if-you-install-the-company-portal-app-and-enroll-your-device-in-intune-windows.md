---
title: Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune? | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: e2da1f39d0cfe05bb0ea1c149c91e5ff82312c01


---


# Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune?

Per informazioni su cosa accade quando si installa l'app Portale aziendale e si registra il dispositivo, usare il collegamento visualizzato nella sezione "Contenuto dell'articolo" per il dispositivo in uso. Per informazioni sui dispositivi Windows 10, vedere [questa pagina](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## Windows 8.1 e Windows RT
Quando si installa l'app Portale aziendale e si registra il proprio dispositivo Windows 8.1 Enterprise o Professional o Windows RT in Intune, è possibile usare tale app per:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro

-   Ottenere app aziendali dal Portale aziendale

-   Configurare automaticamente l'account di posta elettronica aziendale

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato

Per la procedura di registrazione, vedere [Registrare il dispositivo Windows in Intune](enroll-your-device-in-intune-windows.md). Per informazioni sui dettagli del dispositivo visibili all'amministratore IT, vedere [Quali sono i dettagli visibili all'amministratore IT quando si registra il dispositivo in Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

Quando si aggiunge un computer:

-   Verrà installato software nel computer per consentire all'amministratore IT di gestire il computer e all'utente di accedere alle risorse della società, come app e informazioni sul supporto. L'amministratore IT può aggiornare automaticamente il software.

-   Intune Endpoint Protection può essere installato nel computer. Questo software controlla la presenza di virus e malware.

-   L'amministratore IT può eseguire un inventario di tutti i software installati nel computer, compresi quelli installati personalmente dall'utente.

-   È possibile richiedere di accettare i termini e le condizioni.

-   L'amministratore IT può raccogliere o eliminare dati dal disco rigido del computer. L'amministratore IT può inoltre eliminare l'intero disco rigido.

-   L'amministratore IT può installare applicazioni e aggiornamenti nel computer.

-   L'amministratore IT può applicare i criteri del computer. Ad esempio, potrebbe essere necessario impostare una password o un PIN che bloccherà il computer o eliminerà tutti i dati dal disco rigido del computer dopo troppi tentativi di accesso con password errata.

## Windows Phone 8.1 e Windows Phone 8
Quando si installa l'app Portale aziendale e si registra il proprio dispositivo Windows Phone 8.1 o Windows Phone 8 in Intune, è possibile usare tale app per:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro

-   Ottenere app aziendali dal Portale aziendale

-   Configurare automaticamente l'account di posta elettronica aziendale

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato

Per la procedura di registrazione, vedere [Registrare il dispositivo Windows in Intune](enroll-your-device-in-intune-windows.md). Per informazioni sui dettagli del dispositivo visibili all'amministratore IT, vedere [Quali sono i dettagli visibili all'amministratore IT quando si registra il dispositivo in Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

Quando si aggiunge il dispositivo Windows Phone, vengono concesse all'amministratore IT le autorizzazioni per accedere al dispositivo. Tali autorizzazioni consentono di:

-   Ripristinare le impostazioni predefinite del dispositivo. Questa operazione è utile se il dispositivo viene smarrito o rubato.

-   Rimuovere tutti i dati correlati alla società e le app aziendali installate. Impostazioni e dati personali non vengono rimossi.

-   Potrebbe essere necessario impostare una password o un PIN, che bloccherà il dispositivo, ripristinerà le impostazioni predefinite o eliminerà i dati dopo troppi tentativi di accesso con password errata.

-   Forzare la crittografia di tutti i dati nel dispositivo. Questa operazione consente di proteggere i dati se il dispositivo viene smarrito o rubato.

-   Richiedere di accettare i termini e le condizioni.

-   Disabilitare la scheda SD.

-   Installare gli aggiornamenti delle app sul dispositivo. Questo si applica solo agli aggiornamenti. L'amministratore IT non può forzare l'installazione di nuove app nel dispositivo, ma l'utente può scegliere di installare le app presenti nel portale aziendale.

-   Dopo aver aggiunto il dispositivo al portale dell'azienda, ogni 8 ore circa verranno eseguite le operazioni seguenti:

    -   Download degli aggiornamenti di criteri o app resi disponibili dall'amministratore IT.

    -   Invio degli aggiornamenti dell'inventario hardware.

    -   Invio degli aggiornamenti dell'inventario delle app aziendali.

## Windows 7 e Vista
Quando si installa l'app Portale aziendale e si registra il proprio dispositivo Windows 7 o Vista in Intune, è possibile usare tale app per:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro

-   Ottenere app aziendali dal Portale aziendale

-   Configurare automaticamente l'account di posta elettronica aziendale

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato

Per informazioni sui dettagli del dispositivo visibili all'amministratore IT, vedere [Quali sono i dettagli visibili all'amministratore IT quando si registra il dispositivo in Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

Quando si aggiunge un computer:

-   Verrà installato software nel computer per consentire all'amministratore IT di gestire il computer e all'utente di accedere alle risorse della società, come app e informazioni sul supporto. L'amministratore IT può aggiornare automaticamente il software.

-   Intune Endpoint Protection può essere installato nel computer. Questo software controlla la presenza di virus e malware.

-   L'amministratore IT può eseguire un inventario di tutti i software installati nel computer, compresi quelli installati personalmente dall'utente.

-   È possibile richiedere di accettare i termini e le condizioni.

-   L'amministratore IT può raccogliere o eliminare dati dal disco rigido del computer. L'amministratore IT può inoltre eliminare l'intero disco rigido.

-   L'amministratore IT può installare applicazioni e aggiornamenti nel computer.

-   L'amministratore IT può applicare i criteri del computer. Ad esempio, potrebbe essere necessario impostare una password o un PIN che bloccherà il computer o eliminerà tutti i dati dal disco rigido del computer dopo troppi tentativi di accesso con password errata.

Per informazioni, contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

### Vedere anche
[Uso del dispositivo Windows con Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Jun16_HO4-->


