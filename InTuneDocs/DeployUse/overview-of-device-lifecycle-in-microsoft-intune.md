---
title: Panoramica del ciclo di vita del software MDM | Microsoft Intune
description: Informazioni su come Intune consente di gestire i dispositivi per tutto il loro ciclo di vita dalla registrazione e dalla configurazione al ritiro finale.
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 5140c4943be630ea8e48f80f7e6b590d223beac1
ms.openlocfilehash: 751025aa71ef41564100ea57ac0d1fe60619e214


---

# Panoramica del ciclo di vita di gestione dei dispositivi mobili (MDM)

Tutti i dispositivi gestiti hanno ciò che viene definito un *ciclo di vita*. Intune può essere utile per gestire il ciclo di vita del dispositivo dalla registrazione al ritiro del dispositivo stesso quando non è più necessario:

![Ciclo di vita del dispositivo](./media/device-lifecycle.png "the Intune device lifecycle")

## Registrazione
Le odierne strategie di gestione dei dispositivi mobili (MDM) riguardano una vasta gamma di telefoni, tablet e PC (iOS, Android, Windows e Mac OS X). Se è necessario essere in grado di gestire il dispositivo, come nel caso dei dispositivi aziendali, il primo passaggio consiste nella [registrazione del dispositivo](enroll-devices-in-microsoft-intune.md). È anche possibile gestire i PC Windows registrandoli con Intune (MDM) oppure [installando il software client Intune](manage-windows-pcs-with-microsoft-intune.md).

## Configura
La registrazione dei dispositivi costituisce il primo passaggio. Per poter usufruire di tutte le offerte di Intune e verificare che i dispositivi siano protetti e conformi agli standard aziendali, è possibile scegliere tra una vasta gamma di **criteri** che consentono di configurare quasi ogni aspetto correlato al funzionamento dei dispositivi gestiti. Gli utenti devono, ad esempio, usare una password per i dispositivi che contengono dati aziendali? È possibile impostare questo requisito. È disponibile una Wi-Fi aziendale? È possibile configurarla automaticamente. Di seguito sono descritti i tipi di opzioni di configurazione disponibili:

- [**Criteri di configurazione**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md): questi criteri consentono di configurare il funzionamento delle caratteristiche e delle funzionalità dei dispositivi gestiti. Ad esempio, può essere necessario usare una password in Windows Phone o disabilitare l'uso della fotocamera su iPhone.
- [**Criteri di accesso alle risorse aziendali**](enable-access-to-company-resources-with-microsoft-intune.md) : quando si consente agli utenti di accedere ai dati aziendali da un dispositivo personale, possono presentarsi alcune problematiche. Ad esempio, come è possibile garantire che tutti i dispositivi che devono accedere alla posta elettronica aziendale siano configurati correttamente? Come è possibile garantire che gli utenti possano accedere alla rete aziendale con una connessione VPN senza dover conoscere le impostazioni complesse che ne stanno alla base? Con Intune è possibile ridurre queste problematiche configurando automaticamente i dispositivi gestiti per l'accesso alle risorse aziendali comuni.
- [**Criteri di gestione di PC Windows (con il software client di Intune)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md): mentre la registrazione dei PC Windows con Intune fornisce la maggior parte delle funzionalità di gestione dei dispositivi, Intune continua a supportare la gestione dei PC Windows con il software client di Intune. Per altre informazioni su alcune delle attività che è possibile eseguire con i PC, iniziare da qui.

## Protezione
Al giorno d'oggi, la protezione dei dispositivi da accessi non autorizzati è una delle attività più importanti da eseguire. Oltre agli elementi descritti nel passaggio **Configurazione** del ciclo di vita del dispositivo, Intune fornisce altre funzionalità che consentono di proteggere i dispositivi gestiti da accessi non autorizzati o attacchi dannosi:
- [**Autenticazione a più fattori**](protect-windows-devices-with-multi-factor-authentication.md): l'aggiunta di un ulteriore livello di autenticazione agli accessi dell'utente contribuisce a rendere i dispositivi ancora più sicuri. I dispositivi Windows, Windows Phone e Windows Mobile offrono l'autenticazione a più fattori che richiede un secondo livello di autenticazione, ad esempio una telefonata o un messaggio di testo prima che gli utenti possono accedere.
- [**Impostazioni di Microsoft Passport**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md): Microsoft Passport è un metodo di accesso alternativo che consente agli utenti di usare un *movimento*, ad esempio un'impronta digitale, o Windows Hello per accedere senza dover immettere una password.
- [**Criteri per proteggere i PC Windows (con il software client di Intune)**](policies-to-protect-windows-pcs-in-microsoft-intune.md): quando si gestiscono PC Windows mediante il software client di Intune, sono disponibili criteri che consentono di controllare le impostazioni per la protezione dell'endpoint, gli aggiornamenti software e Windows Firewall nei PC gestiti.

## Ritiro
Quando un dispositivo viene smarrito o rubato, è necessario sostituirlo. Oppure quando gli utenti si spostano in un altro posto è in genere il caso di [ritirare o cancellare](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) il dispositivo. Esistono diversi modi per eseguire questa operazione dal ripristino del dispositivo, alla rimozione dalla gestione o alla cancellazione dei dati aziendali che contiene.



<!--HONumber=Jul16_HO2-->


