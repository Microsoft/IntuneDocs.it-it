---
title: Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo Windows in Intune? | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/8/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3a2daebdb781ce99aa103e7717ffa1b0297cb3a
ms.openlocfilehash: 840d985fd2c4771831f722cdff214026a383f606


---


# Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo Windows in Intune?

Quando si installa l'app Portale aziendale e la si usa per registrare un dispositivo Windows o Windows Phone, si abilita l'amministratore IT per la gestione del dispositivo in modo da proteggere i dati dell'azienda o dell'istituto di istruzione, come descritto di seguito per i dispositivi precedenti a Windows 10. Per informazioni sui dispositivi Windows 10, vedere [questa pagina](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## Che cosa avviene a tutti i dispositivi Windows dopo l'iscrizione?
Quando si registra il dispositivo Windows o Windows Phone in Intune, è possibile:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro

-   Ottenere le app aziendali dal sito Web del portale aziendale (per Windows 7 e Vista, è possibile ottenere app aziendali solo dal sito Web del portale aziendale)

-   Configurare automaticamente l'account di posta elettronica aziendale o dell'istituto di istruzione

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato

Quando si registra un dispositivo, vengono concesse all'amministratore IT le autorizzazioni per eseguire le operazioni seguenti:

-   Ripristinare le impostazioni predefinite del dispositivo. Questa operazione è utile se il dispositivo viene smarrito o rubato.

-   Rimuovere tutti i dati correlati alla società e le app aziendali installate. Impostazioni e dati personali non vengono rimossi.

-   L'amministratore IT può eseguire un inventario di tutti i software installati nel computer, compresi quelli installati personalmente dall'utente.

-   Può essere necessario impostare una password o un PIN, che bloccherà il dispositivo, ripristinerà le impostazioni predefinite o eliminerà i dati dopo troppi tentativi di accesso con password errata.

-   Può essere necessaria la crittografia dei dati nel dispositivo, che consente di proteggere i dati se il dispositivo viene smarrito o rubato.

-   Richiedere di accettare i termini e le condizioni.

-   L'amministratore IT può applicare i criteri del computer. Ad esempio, potrebbe essere necessario impostare una password o un PIN che bloccherà il computer o eliminerà tutti i dati dal disco rigido del computer dopo troppi tentativi di accesso con password errata.

-   Disabilitare la scheda SD.

## Che cosa accade a tutti i PC Windows dopo l'iscrizione?

-  Verrà installato software nel computer per consentire all'amministratore IT di gestire il computer e all'utente di accedere alle risorse della società, come app e informazioni sul supporto. L'amministratore IT può aggiornare automaticamente il software.

-  Intune Endpoint Protection può essere installato nel computer. Questo software controlla la presenza di virus e malware.

-  L'amministratore IT può eseguire un inventario di tutti i software installati nel computer, compresi quelli installati personalmente dall'utente.

-  È possibile richiedere di accettare i termini e le condizioni.

-  L'amministratore IT può raccogliere o eliminare dati dal disco rigido del computer. L'amministratore IT può inoltre eliminare l'intero disco rigido.

-  L'amministratore IT può installare applicazioni e aggiornamenti nel computer.

-  L'amministratore IT può applicare i criteri del computer. Ad esempio, può essere necessario impostare una password o un PIN che bloccherà il computer o eliminerà tutti i dati dal disco rigido del computer dopo troppi tentativi di accesso con password errata.


## Che cosa accade ogni otto ore dopo la registrazione del dispositivo?
Ogni otto ore circa, i dispositivi registrati eseguono le operazioni seguenti:

-   Download degli aggiornamenti di criteri o app resi disponibili dall'amministratore IT.

-   Invio degli aggiornamenti dell'inventario hardware.

-   Invio degli aggiornamenti dell'inventario delle app aziendali.

Per la procedura di registrazione, vedere [Registrare il dispositivo Windows in Intune](enroll-your-device-in-intune-windows.md). Per informazioni sui dettagli del dispositivo visibili all'amministratore IT, vedere [Quali sono i dettagli visibili all'amministratore IT quando si registra il dispositivo in Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

Per informazioni, contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

### Vedere anche
[Uso del dispositivo Windows con Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO4-->


