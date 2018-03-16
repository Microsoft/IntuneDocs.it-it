---
title: Dati inviati da Intune a Google
titlesuffix: Azure portal
description: Elenco di dati inviati da Intune a Google.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d5f8c71115b8c3ee761fbc8d303f87e8aaabd5e1
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="data-intune-sends-to-google"></a>Dati inviati da Intune a Google

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando la gestione dei dispositivi Android è abilitata in un dispositivo, Microsoft Intune stabilisce una connessione con Google e condivide informazioni sull'utente e il dispositivo con Google. Per consentire a Microsoft Intune di stabilire una connessione è necessario creare un account di Google.

Nella tabella seguente sono elencati i dati che Microsoft Intune invia a Google quando la gestione dei dispositivi è abilitata in un dispositivo:


| Dati inviati a Google | Dettagli | Utilizzato per | Esempio |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Ha origine in Google al momento dell'associazione dell'account Gmail a Intune. | Identificatore principale usato per le comunicazioni tra Intune e Google.  Queste comunicazioni includono l'impostazione di criteri, la gestione dei dispositivi e l'associazione/annullamento dell'associazione di Android Enterprise con Intune. | Identificatore univoco, formato di esempio: LC04eik8a6 |
| Policy Body (Insieme di criteri) | Viene originato in Intune quando si salva una nuova app o nuovi criteri di configurazione | Applicazione dei criteri ai dispositivi. | Raccolta di tutte le impostazioni configurate per un'applicazione o per i criteri di configurazione. Può contenere informazioni sui clienti, se visualizzate come parte dei criteri, ad esempio nomi di rete, nomi delle applicazioni e impostazioni specifiche dell'app. |
| Dati del dispositivo | Gli scenari dei dispositivi per Profilo di lavoro hanno come punto di partenza la registrazione in Intune. Gli scenari dei dispositivi per Dispositivo gestito hanno come punto di partenza la registrazione in Google. | I dati del dispositivo vengono scambiati tra Intune e Google per diverse operazioni quali l'applicazione di criteri, la gestione del dispositivo e operazioni di creazione report generiche. | **Identificatore univoco che rappresenta il nome di dispositivo.** Esempio: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Identificatore univoco che rappresenta il nome utente.** Esempio: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Stato dispositivo.** Esempi: Attivo, Disabilitato, Provisioning in corso.<br>**Stati di conformità.** Esempi: impostazione non supportata, app richieste mancanti<br>**Informazioni software.** Esempi: versioni del software e livello delle patch.<br>**Network Info (Info rete).** Esempi: IMEI, MEID, WifiMacAddress<br>**Impostazioni del dispositivo.** Esempi: informazioni sui livelli di crittografia e se il dispositivo accetta le app sconosciute.<br> Vedere di seguito un esempio di messaggio JSON. |
| newPassword | Origine in Intune. | Reimpostazione del passcode del dispositivo. | Stringa che rappresenta la nuova password. |
| Utente di Google | Google | Gestione del profilo di lavoro per gli scenari Profilo di lavoro (BYOD). | Identificatore univoco che rappresenta l'account Gmail collegato. Esempio: 114223373813435875042 |
| Dati applicazione | Originati in Intune durante il salvataggio dei criteri dell'applicazione. |  | Stringa del nome dell'applicazione. Esempio: app:com.microsoft.windowsintune.companyportal |
| Account Enterprise Service | Originato in Google su richiesta di Intune. | Usato per l'autenticazione tra Intune e Google per le transazioni relative al cliente. | È costituito da varie parti:<br> **Id organizzazione**: documentato in precedenza.<br>**UPN**: nome dell'entità utente generato, usato nell'autenticazione per conto del cliente.<br>Esempio: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Chiave**: BLOB con codifica Base64 usato nelle richieste di autenticazione e archiviato con crittografia nel servizio. Il BLOB ha il seguente aspetto:<br> Identificatore univoco che rappresenta la chiave dell'utente.<br>Esempio: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**Esempio di dati del dispositivo**

Di seguito è riportato un messaggio del dispositivo JSON di esempio da Google:



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

Per interrompere l'uso della gestione dispositivi Android con Microsoft Intune ed eliminare i dati è necessario disabilitare la gestione dispositivi Android di Microsoft Intune ed eliminare l'account Google. Per informazioni sulla gestione account, vedere l'account Google.


