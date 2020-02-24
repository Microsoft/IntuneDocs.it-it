---
title: Registrare i dispositivi iOS/iPadOS in Intune
titleSuffix: Microsoft Intune
description: Impostare la registrazione dei dispositivi iOS/iPadOS in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d5aeb17084ea0bb76429b1fa15c9de5855220ab
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415287"
---
# <a name="enroll-iosipados-devices-in-intune"></a>Registrare i dispositivi iOS/iPadOS in Intune

Intune abilita la gestione di dispositivi mobili (MDM, Mobile Device Management) di iPad e iPhone per offrire agli utenti accesso sicuro a posta elettronica, dati e app aziendali.

Come amministratore di Intune, è possibile configurare la registrazione dei dispositivi iOS/iPadOS e iPadOS per accedere alle risorse aziendali. È possibile consentire agli utenti di registrare dispositivi di proprietà personale tramite la registrazione di tipo BYOD (Bring Your Own Device). È anche possibile configurare la registrazione di dispositivi di proprietà dell'azienda.

## <a name="prerequisites-for-iosipados-enrollment"></a>Prerequisiti per la registrazione iOS/iPadOS

Prima di abilitare i dispositivi iOS/iPadOS, completare i passaggi seguenti:

- [Verificare che il dispositivo sia idoneo per la registrazione dei dispositivi Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurare Intune](../fundamentals/setup-steps.md): questi passaggi consentono di impostare l'infrastruttura Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](../fundamentals/mdm-authority-set.md).
- [Ottenere un certificato push MDM di Apple](apple-mdm-push-certificate-get.md): Apple richiede un certificato per abilitare la gestione dei dispositivi iOS/iPadOS e macOS.

## <a name="user-owned-iosipados-and-ipados-devices-byod"></a>Dispositivi iOS/iPadOS e iPadOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali per la gestione di Intune, una funzionalità nota come BYOD (Bring Your Own Device, Usa dispositivo personale). Sono disponibili tre opzioni di registrazione degli utenti:
- I criteri di protezione delle app offrono l'esperienza BYOD più semplice con una gestione solo a livello di app. Tuttavia, se si vuole proteggere anche il dispositivo con un PIN complesso di 6 cifre, è possibile usare questi criteri insieme alla registrazione utente.
- La registrazione dispositivi può essere considerata la registrazione BYOD tipica. Offre agli amministratori un'ampia gamma di opzioni di gestione.
- La registrazione utente è un processo di registrazione più semplificato che offre agli amministratori un subset di opzioni di gestione dei dispositivi. Questa funzionalità è attualmente disponibile in anteprima. 

Dopo aver completato i prerequisiti e assegnato le licenze utente, gli utenti possono scaricare l'app Portale aziendale Intune da App Store e seguire le istruzioni di registrazione nell'app. È possibile personalizzare l'informativa sulla privacy del portale aziendale nei dispositivi iOS/iPadOS come descritto nella sezione relativa alla [personalizzazione dell'informativa sulla privacy](../apps/company-portal-app.md#privacy-statement-customization).

## <a name="company-owned-iosipados-devices"></a>Dispositivi iOS/iPadOS di proprietà dell'azienda

Per le organizzazioni che acquistano dispositivi per i propri utenti, Intune supporta i seguenti metodi di registrazione dei dispositivi iOS/iPadOS di proprietà dell'azienda:

- Device Enrollment Program (DEP) di Apple
- Apple School Manager
- Registrazione con Assistente configurazione e Apple Configurator
- Registrazione diretta con Apple Configurator

È anche possibile registrare i dispositivi iOS/iPadOS di proprietà dell'azienda con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programma di registrazione dispositivi

Le organizzazioni possono ora acquistare i dispositivi iOS/iPadOS con Device Enrollment Program (DEP) di Apple. DEP consente di distribuire un profilo di registrazione in modalità wireless per portare i dispositivi nella gestione. Per altre informazioni, vedere [Device Enrollment Program](device-enrollment-program-enroll-ios.md).

## <a name="user-enrollment"></a>Registrazione utenti
La registrazione utente offre agli amministratori un subset di opzioni di gestione semplificato rispetto ad altri metodi di registrazione. Per altre informazioni, vedere [Azioni e opzioni supportate per la registrazione utente](ios-user-enrollment-supported-actions.md) e [Configurare la registrazione utente iOS/iPadOS e iPadOS](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Apple School Manager

Apple School Manager è un programma di acquisto e registrazione dei dispositivi per le scuole. Analogamente a DEP, consente di distribuire un profilo per registrare i dispositivi nella gestione. Altre informazioni su [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

È possibile registrare i dispositivi iOS/iPadOS con Apple Configurator in esecuzione su un computer Mac. Per preparare i dispositivi, connetterli tramite USB e installare un profilo di registrazione. È possibile registrare i dispositivi con Apple Configurator in due modi:

- Registrazione di Assistente configurazione: cancella il dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.
- Registrazione diretta: non cancella il dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi senza affinità utente.

Altre informazioni sulla [Registrazione con Apple Configurator](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Usare il portale aziendale nei dispositivi registrati con il programma di registrazione dispositivi o Apple Configurator

I dispositivi configurati con affinità utente possono installare ed eseguire l'app Portale aziendale per scaricare le app e gestire i dispositivi. Dopo che gli utenti ricevono i dispositivi, devono eseguire alcuni passaggi supplementari per completare l'Assistente configurazione e installare l'app del portale aziendale.

L'affinità utente è necessaria per supportare quanto segue:

- App per la gestione di applicazioni mobili (MAM)
- Accesso condizionale ai dati aziendali e alla posta elettronica
- App Portale aziendale

### <a name="how-users-enroll-corporate-owned-iosipados-devices-with-user-affinity"></a>Come registrare i dispositivi iOS/iPadOS di proprietà dell'azienda con l'affinità utente

1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione.
2. Dopo il completamento della configurazione viene chiesto agli utenti di specificare un ID Apple. Gli utenti devono specificare l'ID Apple per consentire al dispositivo di installare l'app Portale aziendale.
3. Il dispositivo iOS/iPadOS installa automaticamente l'app Portale aziendale da App Store.
4. Gli utenti devono avviare l'app Portale aziendale e accedere con le credenziali (quali il nome personale univoco o UPN) associate all'abbonamento in Intune.
5. Dopo aver effettuato l'accesso, la registrazione è completa. Ora gli utenti possono usare il dispositivo con il set completo di funzionalità.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Informazioni sui dispositivi gestiti di proprietà dell'azienda senza affinità utente

Nei dispositivi configurati senza affinità utente il portale aziendale non è supportato e non si dovrebbe installare l'app. Il Portale aziendale è progettato per gli utenti che hanno credenziali aziendali e richiedono l'accesso a risorse aziendali personalizzate, ad esempio la posta elettronica. I dispositivi registrati senza affinità utente non prevedono l'accesso utente dedicato. Chioschi multimediali, POS o dispositivi di utilità condivisi sono casi d'uso tipici per i dispositivi registrati senza affinità utente.

Se è necessaria l'affinità utente, assicurarsi che nel profilo di registrazione del dispositivo sia selezionata l'opzione **Affinità utente** prima di registrare il dispositivo. Per modificare lo stato di affinità in un dispositivo è necessario ritirare il dispositivo e quindi registrarlo nuovamente.

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi di registrazione dei dispositivi iOS/iPadOS in Microsoft Intune](https://support.microsoft.com/help/4039809)
