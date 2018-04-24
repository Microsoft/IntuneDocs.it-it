---
title: Scegliere come registrare i dispositivi iOS in Intune
titlesuffix: Microsoft Intune
description: Impostare la registrazione dei dispositivi iOS in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01523dc4c887214794d4600219ce0b77549b4734
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-ios-devices-in-intune"></a>Registrare i dispositivi iOS in Intune

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad e iPhone e offre agli utenti l'accesso alla posta elettronica e alle app aziendali.

Come amministratore di Intune, è possibile abilitare la registrazione per i dispositivi iOS. È possibile consentire agli utenti di registrare dispositivi di proprietà personale, tramite la registrazione di tipo "bring your own device" (BYOD). È anche possibile abilitare la registrazione di dispositivi di proprietà dell'azienda.

## <a name="prerequisites-for-ios-enrollment"></a>Prerequisiti per la registrazione iOS
Prima di abilitare i dispositivi iOS, completare i passaggi seguenti:
- [Configurare Intune](setup-steps.md): questi passaggi consentono di impostare l'infrastruttura Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).
- [Ottenere un certificato push MDM di Apple](apple-mdm-push-certificate-get.md): Apple richiede un certificato per abilitare la gestione dei dispositivi iOS e macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivi iOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali per la gestione di Intune, una funzionalità nota come BYOD (Bring Your Own Device, Usa dispositivo personale). Dopo aver completato i prerequisiti e assegnato le licenze, gli utenti possono scaricare l'app Portale aziendale Intune dall'App Store e seguire le istruzioni di registrazione nell'app.

## <a name="company-owned-ios-devices"></a>Dispositivi macOS di proprietà dell'azienda
Per le organizzazioni che acquistano dispositivi per i propri utenti, Intune supporta i seguenti metodi di registrazione dei dispositivi iOS di proprietà dell'azienda:

- Device Enrollment Program (DEP) di Apple
- Apple School Manager
- Registrazione con Assistente configurazione e Apple Configurator
- Registrazione diretta con Apple Configurator

È anche possibile registrare i dispositivi iOS di proprietà dell'azienda con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programma di registrazione dispositivi
Le organizzazioni possono ora acquistare i dispositivi iOS tramite Device Enrollment Program (DEP) di Apple. DEP consente di distribuire un profilo di registrazione in modalità wireless per portare i dispositivi nella gestione. Altre informazioni su [Device Enrollment Program](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager è un programma di acquisto e registrazione dei dispositivi per le scuole. Analogamente a DEP, consente di distribuire un profilo per registrare i dispositivi nella gestione. Altre informazioni su [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
È possibile registrare i dispositivi iOS con Apple Configurator in esecuzione su un computer Mac. Per preparare i dispositivi, connetterli tramite USB e installare un profilo di registrazione. È possibile registrare i dispositivi con Apple Configurator in due modi:
- Registrazione di Assistente configurazione: ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.
- Registrazione diretta: non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi senza affinità utente.

Altre informazioni sulla [Registrazione con Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Usare il portale aziendale nei dispositivi registrati con il programma di registrazione dispositivi o Apple Configurator

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo che gli utenti ricevono i dispositivi, devono eseguire alcuni passaggi supplementari per completare l'Assistente configurazione e installare l'app del portale aziendale.

L'affinità utente è necessaria per supportare quanto segue:
  - App per la gestione di applicazioni mobili (MAM)
  - Accesso condizionale ai dati aziendali e della posta elettronica
  - App Portale aziendale

**Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente**
1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. Durante la configurazione, agli utenti viene chiesto di fornire le credenziali. Devono usare le credenziali (nome personale univoco o UPN) associate alla propria sottoscrizione in Intune.

2. Durante la configurazione, agli utenti viene chiesto di fornire un ID Apple. Devono specificare l'ID Apple, per consentire al dispositivo di installare il portale aziendale. Possono inoltre specificare l'ID dal menu delle impostazioni di iOS al termine dell'installazione.

3. Al termine dell'installazione, il dispositivo iOS deve installare l'app del portale aziendale dall'App Store.

4. A questo punto l'utente può accedere al portale aziendale con l'UPN usato durante la configurazione del dispositivo.

5. Dopo l'accesso, viene chiesto di registrare il dispositivo. Il primo passaggio consiste nell'identificazione del dispositivo. L'app visualizza un elenco di dispositivi iOS già registrati dall'azienda e assegnati all'account di Intune dell'utente. L'utente deve scegliere il dispositivo corrispondente.

   Se il dispositivo non è registrato dall'azienda, è necessario selezionare **nuovo dispositivo** per continuare con il flusso di registrazione standard.

6. Nella schermata successiva l'utente deve confermare il numero di serie del nuovo dispositivo. L'utente può toccare il collegamento **confermare il numero di serie** per avviare le istruzioni per l'uso dell'app Impostazioni per verificare il numero di serie. Deve quindi immettere gli ultimi quattro caratteri del numero di serie nell'app del portale aziendale.

   Questo passaggio verifica che il dispositivo sia il dispositivo aziendale registrato in Intune. Se il numero di serie sul dispositivo non corrisponde, è stato selezionato il dispositivo errato. L'utente deve tornare alla schermata precedente e selezionare un dispositivo diverso.

7. Dopo aver verificato il numero di serie, l'app del portale aziendale reindirizza al sito Web del portale aziendale per completare la registrazione. A questo punto, il sito Web chiede all'utente di tornare all'app.

8. La registrazione è stata completata. L'utente può ora usare il dispositivo con il set completo di funzionalità.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Informazioni sui dispositivi gestiti di proprietà dell'azienda senza affinità utente

Nei dispositivi configurati senza affinità utente il portale aziendale non è supportato e non si dovrebbe installare l'app. Il Portale aziendale è progettato per gli utenti che hanno credenziali aziendali e richiedono l'accesso a risorse aziendali personalizzate, ad esempio la posta elettronica. I dispositivi registrati senza affinità utente non sono pensati per l'accesso utente dedicato. Chioschi multimediali, POS o dispositivi di utilità condivisi sono casi d'uso tipici per i dispositivi registrati senza affinità utente.

Se è necessaria l'affinità utente, assicurarsi che nel profilo di registrazione del dispositivo sia selezionata l'opzione **Affinità utente** prima di registrare il dispositivo. Per modificare lo stato di affinità in un dispositivo è necessario ritirare il dispositivo e quindi registrarlo nuovamente.

