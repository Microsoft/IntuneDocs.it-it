---
title: Dati inviati da Intune a Google
titleSuffix: Microsoft Intune
description: Elenco di dati inviati da Intune a Google.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bb205472c4407dab6ff990e33737a8bd8b24a010
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188646"
---
# <a name="data-intune-sends-to-google"></a>Dati inviati da Intune a Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando la gestione dei dispositivi aziendali Android è abilitata in un dispositivo, Microsoft Intune stabilisce una connessione con Google e condivide informazioni sull'utente e il dispositivo con Google. Per consentire a Microsoft Intune di stabilire una connessione è necessario creare un account di Google.

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


Per interrompere l'uso della gestione dispositivi aziendali Android con Microsoft Intune ed eliminare i dati è necessario disabilitare la gestione dispositivi aziendali Android di Microsoft Intune ed eliminare l'account Google. Per informazioni sulla gestione account, vedere l'account Google.


