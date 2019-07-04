---
title: Registrare i dispositivi iOS in Intune
titleSuffix: Microsoft Intune
description: Impostare la registrazione dei dispositivi iOS in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d94f2bd9237e92b22b9d73e4f7777dc0faf3f0fe
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529616"
---
# <a name="enroll-ios-devices-in-intune"></a>Registrare i dispositivi iOS in Intune

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad e iPhone e offre agli utenti l'accesso alla posta elettronica e alle app aziendali.

Come amministratore di Intune, è possibile abilitare la registrazione per i dispositivi iOS. È possibile consentire agli utenti di registrare dispositivi di proprietà personale mediante la registrazione di tipo BYOD (Bring Your Own Device). È anche possibile abilitare la registrazione di dispositivi di proprietà dell'azienda.

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
- Registrazione di Assistente configurazione: cancella il dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.
- Registrazione diretta: non cancella il dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi senza affinità utente.

Altre informazioni sulla [Registrazione con Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Usare il portale aziendale nei dispositivi registrati con il programma di registrazione dispositivi o Apple Configurator

I dispositivi configurati con affinità utente possono installare ed eseguire l'app Portale aziendale per scaricare le app e gestire i dispositivi. Dopo che gli utenti ricevono i dispositivi, devono eseguire alcuni passaggi supplementari per completare l'Assistente configurazione e installare l'app del portale aziendale.

L'affinità utente è necessaria per supportare quanto segue:
  - App per la gestione di applicazioni mobili (MAM)
  - Accesso condizionale ai dati aziendali e alla posta elettronica
  - App Portale aziendale

**Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente**
1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. 
2. Dopo il completamento della configurazione viene chiesto agli utenti di specificare un ID Apple. Gli utenti devono specificare l'ID Apple per consentire al dispositivo di installare l'app Portale aziendale. 
3. Il dispositivo iOS installa automaticamente l'app Portale aziendale da App Store.
4. Gli utenti devono avviare l'app Portale aziendale e accedere con le credenziali (quali il nome personale univoco o UPN) associate all'abbonamento in Intune. 
5. Dopo aver effettuato l'accesso, la registrazione è completa. Ora gli utenti possono usare il dispositivo con il set completo di funzionalità.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Informazioni sui dispositivi gestiti di proprietà dell'azienda senza affinità utente

Nei dispositivi configurati senza affinità utente il portale aziendale non è supportato e non si dovrebbe installare l'app. Il Portale aziendale è progettato per gli utenti che hanno credenziali aziendali e richiedono l'accesso a risorse aziendali personalizzate, ad esempio la posta elettronica. I dispositivi registrati senza affinità utente non prevedono l'accesso utente dedicato. Chioschi multimediali, POS o dispositivi di utilità condivisi sono casi d'uso tipici per i dispositivi registrati senza affinità utente.

Se è necessaria l'affinità utente, assicurarsi che nel profilo di registrazione del dispositivo sia selezionata l'opzione **Affinità utente** prima di registrare il dispositivo. Per modificare lo stato di affinità in un dispositivo è necessario ritirare il dispositivo e quindi registrarlo nuovamente.

## <a name="see-also"></a>Vedere anche

[Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809) (Risoluzione dei problemi di registrazione dei dispositivi iOS in Microsoft Intune)
