---
title: Registrare un dispositivo iOS fornito dall'organizzazione per la gestione. | Microsoft Docs
description: Informazioni su come registrare in Intune un dispositivo iOS acquistato e fornito dall'organizzazione
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e5ce83d20958f3ba4c818e49b0c226e07851d03
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506217"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>Registrare il dispositivo iOS fornito dall'organizzazione per la gestione

Informazioni su come rendere il nuovo dispositivo iOS gestito da Intune.  

I dispositivi iOS che vengono forniti dall'azienda o dall'istituto di istruzione sono spesso preconfigurati. L'organizzazione invierà le impostazioni preconfigurate al dispositivo la prima volta che viene acceso e che l'utente esegue l'accesso. Al termine della configurazione del dispositivo, si otterrà l'accesso alle risorse aziendali o dell'istituto di istruzione.  

Per avviare la configurazione, accendere il dispositivo e accedere con le credenziali aziendali o dell'istituto di istruzione. Il resto di questo articolo descrive i passaggi e le schermate visualizzati durante l'utilizzo dell'Assistente configurazione.

## <a name="what-is-apple-dep"></a>Che cos'è il programma DEP di Apple?

L'organizzazione potrebbe avere acquistato i propri dispositivi tramite un *Apple Device Enrollment Program* (DEP). Il programma DEP di Apple consente alle organizzazioni di acquistare grandi quantità di dispositivi iOS o macOS. Le organizzazioni possono quindi configurare e gestire tali dispositivi all'interno del provider di gestione dei dispositivi mobili preferito, ad esempio Intune. Gli amministratori che desiderano avere altre informazioni sul programma DEP di Apple possono vedere [Registrare automaticamente i dispositivi nel programma Device Enrollment Program di Apple](/intune/enrollment/device-enrollment-program-enroll-ios).

## <a name="set-up-your-ios-device"></a>Configurare il dispositivo iOS

Se si usa un dispositivo iOS personale invece di un dispositivo fornito dall'organizzazione, seguire questa procedura per i [dispositivi personali e BYOD](enroll-your-device-in-intune-ios.md).  

1. Accendere il dispositivo iOS.
2. Dopo avere selezionato la **lingua**, connettere il dispositivo al Wi-Fi.
3. Nella schermata **Set up iOS device** (Configura dispositivo iOS) scegliere:
   - **Set up as new device** (Configura come nuovo dispositivo)
   - **Restore from iCloud Backup** (Ripristina da backup iCloud)
   - **Restore from iTunes Backup** (Ripristina da backup iTunes)

4. Dopo la connessione al Wi-Fi, verrà visualizzata la schermata **Configuration** (Configurazione) contenente il messaggio **[Your Company] will automatically configure your device** ([Società] configurerà automaticamente il dispositivo).

   **Configuration allows [Your Company] to manage this device over the air (La configurazione consente a [società] di gestire il dispositivo in modalità wireless). An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely (Un amministratore può consentire di configurare gli account di posta elettronica e di rete, installare e configurare le app e gestire le impostazioni in modalità remota). An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device** (Un amministratore può disattivare le funzionalità, installare e rimuovere app, monitorare e limitare il traffico Internet e cancellare in remoto il dispositivo).

   **Configuration is provided by: [Your Company's] iOS Team [Address]** (La configurazione è specificata da: team iOS [società]).

5. Eseguire l'accesso con l'ID Apple. L'accesso consente di installare l'app Portale aziendale e il profilo di gestione che consentono all'azienda di concedere l'accesso alle risorse, come la posta elettronica e le app.
6. Accettare **termini e condizioni** e decidere se inviare le informazioni di diagnostica a Apple.
7. Dopo avere completato la registrazione, il dispositivo potrebbe chiedere di eseguire altre azioni, Alcune di queste operazioni potrebbero essere l'immissione della password per l'accesso alla posta elettronica e l'impostazione di un passcode.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
