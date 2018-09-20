---
title: Registrare automaticamente i dispositivi Android usando Knox Mobile Enrollment di Samsung
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android usando Samsung Knox Mobile Enrollment
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f1fbe688705940d3e8038affb84268fbaf113e3
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313065"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Registrare automaticamente i dispositivi Android usando Knox Mobile Enrollment di Samsung

Questo argomento consente di configurare Intune per registrare i dispositivi Android supportati usando Samsung Knox Mobile Enrollment (KME). Usando Intune con Samsung KME, è possibile registrare un numero elevato di dispositivi Android aziendali quando gli utenti finali attivano i dispositivi per la prima volta e si connettono a una rete WiFi o cellulare. I dispositivi possono anche essere registrati usando Bluetooth o NFC quando si usa l'app Knox Deployment.

Per abilitare la registrazione di Intune con Samsung KME, si usano entrambi i portali di Intune e di Samsung Knox in quest'ordine:

1. Nel portale di Knox:
    1. [Creare un profilo MDM](#create-mdm-profile)
    2. [Aggiungere dispositivi](#add-devices)
    3. [Assegnare un profilo MDM ai dispositivi](#assign-an-mdm-profile-to-devices)
2. Nel portale di Knox [configurare l'accesso degli utenti finali](#configure-how-end-users-sign-in).
3. [Distribuire i dispositivi](#distribute-devices).


Un elenco di identificatori di dispositivo (numeri di serie e IMEI) viene automaticamente aggiunto al portale di Knox quando si acquistano dispositivi da rivenditori autorizzati che partecipano a Knox Deployment Program.


## <a name="prerequisites"></a>Prerequisiti

Per la registrazione in Intune con KME, è prima necessario registrare la società nel portale di Samsung Knox seguendo questa procedura:
1.  [Verificare che KME sia disponibile nella propria area](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME è disponibile in più di 55 paesi. Assicurarsi che il proprio paese di distribuzione sia supportato.

2.  [Dispositivi supportati](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME è disponibile in tutti i dispositivi Samsung che eseguono Knox 2.4 o versione successiva.

3.  [Requisiti di rete](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): verificare che le regole di accesso alla rete e del firewall necessarie siano consentite nella rete.

4.  [Registrare un account Samsung](https://www2.samsungknox.com/en/user/register): è necessario un account Samsung per registrare e abilitare KME e per gestire tutti i diritti Knox Enterprise in un'unica posizione.

5.  Verifica della registrazione: dopo che il profilo è stato completato e inviato, Samsung esegue una verifica dell'applicazione e la approva immediatamente o ne imposta lo stato di verifica in sospeso che richiede ulteriori attività di completamento. Dopo che l'account è stato approvato, è possibile continuare con i passaggi successivi.

## <a name="create-mdm-profile"></a>Creare il profilo MDM

Quando la società viene registrata correttamente, è possibile creare il profilo MDM per Microsoft Intune nel portale di Knox usando le informazioni seguenti. Per indicazioni dettagliate, vedere le istruzioni in [Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) (Configurazione guidata del profilo Samsung Knox).

| Campi del profilo MDM| Necessaria? | Valori |
|-------------------|-----------|-------|
|MDM Server URI (URI server MDM)     | No        |Lasciarlo vuoto.
|Nome profilo       | Sì       |Immettere il nome profilo preferito.
|description        | No        |Immettere la descrizione del profilo.
|MDM Agent APK (APK agente MDM)      | Sì       |https://aka.ms/intune_kme
|Skip Setup wizard (Ignora configurazione guidata)  | No        |Scegliere questa opzione per ignorare i prompt della procedura di configurazione dei dispositivi standard per conto dell'utente finale.
|Allow End User to Cancel Enrollment (Consenti all'utente finale di annullare la registrazione) | No | Scegliere questa opzione per consentire agli utenti di annullare KME.
|Custom JSON (JSON personalizzato)        | No        |Lasciarlo vuoto.
| EULAs, Terms of Service & User Agreements (Condizioni di licenza, condizioni d'uso e contratti di licenza)| No | Scegliere questa opzione per visualizzare i contratti relativi a Knox per l'accettazione utente.
Associate a Knox license with this profile (Associa una licenza Knox a questo profilo) | No | Lasciare questa opzione deselezionata. Per la registrazione in Intune con KME non è necessaria una licenza Knox.

## <a name="add-devices"></a>Aggiungere dispositivi

Per assegnare i profili MDM ai dispositivi, i dispositivi Samsung Knox supportati devono essere aggiunti al portale di Knox usando uno dei metodi seguenti:
- **Uso di rivenditori approvati da Samsung:** usare questo metodo se si acquistano i dispositivi da uno dei rivenditori approvati da Samsung. I rivenditori possono caricare automaticamente i dispositivi una volta approvati. [Per informazioni su come aggiungere i rivenditori, vedere il manuale dell'utente sulla registrazione di Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Uso dell'app Knox Deployment:** usare questo metodo se è necessario registrare dispositivi esistenti con KME. È possibile usare Bluetooth o NFC per aggiungere i dispositivi al portale di Knox con questo metodo. [Per informazioni sull'uso dell'app Knox Deployment, vedere il manuale dell'utente sulla registrazione di Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Assegnare un profilo MDM ai dispositivi
È necessario assegnare un profilo MDM ai dispositivi aggiunti nel portale di Knox per poterli registrare. [Per informazioni sulla configurazione dei dispositivi, vedere il manuale dell'utente sulla registrazione di Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurare la modalità di accesso degli utenti finali

Per i dispositivi registrati in Intune con KME, è possibile configurare la modalità di accesso degli utenti finali come segue:

- **Senza associazione del nome utente:** nel portale di Knox, in **Device details** (Dettagli dispositivo) lasciare vuoti i campi **User ID** (ID utente) e **Password** per i dispositivi aggiunti. In questo modo l'utente finale dovrà immettere sia il nome utente che la password durante la registrazione in Intune.

- **Con associazione del nome utente:** nel portale di Knox, in **Device details** (Dettagli dispositivo) immettere un **ID utente** (ad esempio un nome utente per l'utente assegnato o un account [Manager di registrazione dispositivi](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)) per i dispositivi aggiunti. In questo modo il nome utente verrà prepopolato e l'utente finale dovrà immettere una password durante la registrazione in Intune.

> [!NOTE]
>
>Quando l'associazione utente è definita, solo gli utenti associati possono registrare il dispositivo con KME. Ciò vale anche dopo una cancellazione con ripristino delle impostazioni predefinite del dispositivo. Quando non sono definite associazioni utente nel portale di Knox, qualsiasi utente con una licenza di Intune valida può registrare il dispositivo con KME.
>

## <a name="distribute-devices"></a>Distribuire i dispositivi

Dopo avere creato e assegnato un profilo MDM, avere associato un nome utente e identificato i dispositivi come di proprietà dell'azienda in Intune, è possibile distribuire i dispositivi agli utenti.

Serve ancora assistenza? Vedere il [manuale dell'utente di Knox Mobile Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Domande frequenti
- **Account Google Play:** l'account Google Play non è necessario per registrare il dispositivo in Microsoft Intune, ma i futuri aggiornamenti dell'app Portale aziendale Intune potrebbero richiedere un account Google Play nel dispositivo.

- **Modalità proprietario del dispositivo di Google:** la registrazione in modalità proprietario del dispositivo di Google con KME non è supportata in questa anteprima. Questo scenario è attualmente sottoposto ad analisi.

- **Il campo "Password" viene ignorato:** se il campo **password** viene popolato in **Device details** (Dettagli dispositivo) nel portale di Knox, viene ignorato dall'app Portale aziendale Intune. L'utente finale deve immettere una password nel dispositivo per completare la registrazione del dispositivo.

- **"Registrazione di Android Enterprise:** KME non supporta la registrazione di Android Enterprise.

## <a name="getting-support"></a>Richiesta di assistenza
Sono disponibili altre informazioni su come [ottenere assistenza per Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


