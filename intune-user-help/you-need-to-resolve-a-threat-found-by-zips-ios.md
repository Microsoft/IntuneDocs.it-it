---
title: Risoluzione delle minacce rilevate da Zimperium zIPS in iOS | Microsoft Docs
description: Informazioni su come risolvere le minacce rilevate nel dispositivo iOS.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: eaccd9c0-cd46-48e2-8675-4c022c74f672
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6affa9f3577d71ba8e0794454987860f183446ad
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841158"
---
# <a name="resolve-a-threat-found-by-zimperium-zips"></a>Risolvere una minaccia rilevata da Zimperium zIPS

Zimperium zIPS è un servizio Mobile Threat Defender che identifica le potenziali minacce nei dispositivi iOS. Le minacce vengono segnalate all'app Portale aziendale e sono indicate come problemi di non conformità non risolti. Se il dispositivo viene identificato come non conforme, si potrebbe non essere in grado di:

* Connettersi alla posta elettronica aziendale
* Connettersi al Wi-Fi aziendale
* Connettersi a SharePoint Online
* Sincronizzare i file aziendali con OneDrive
* Accedere alle app aziendali

Questo articolo descrive come riconoscere gli avvisi di minaccia di Zimperium zIPS e le azioni da intraprendere per risolverli. 

## <a name="troubleshoot-virus-or-security-threat"></a>Risolvere un virus o una minaccia per la sicurezza  
Al rilevamento di un virus o una minaccia per la sicurezza, Zimperium zIPS applica restrizioni in base ai criteri di accesso dell'organizzazione. I criteri di accesso aziendali possono impedire l'accesso dal dispositivo alla rete, alle app e alla posta elettronica aziendali.  

Zimperium zIPS chiederà all'utente di intervenire per ottenere di nuovo l'accesso. Selezionare la minaccia e seguire le istruzioni disponibili all'interno dell'app per risolvere il problema.

Poiché l'app è integrata con il provider di gestione di dispositivi mobili aziendale, un avviso relativo all'accesso con restrizioni sarà visualizzato anche nell'app Portale aziendale. L'avviso indica di aprire Zimperium zIPS per risolvere il virus o la minaccia per la sicurezza.  

  ![Screenshot di esempio della pagina del dispositivo nel portale aziendale con l'avviso di Zimperium zIPS.](./media/CP-lookout-virus-banner-1808.png)  
  
## <a name="troubleshoot-an-app-threat"></a>Risolvere una minaccia app

Se si installa un'app che viene vista come una minaccia per il dispositivo, si riceverà una notifica all'interno di Zimperium zIPS. Se l'app interessata rimane nel dispositivo, non sarà possibile accedere alle risorse aziendali.  

Per risolvere il problema, selezionare l'app dall'elenco di minacce in Zimperium zIPS. Seguire quindi le istruzioni visualizzate sullo schermo per rimuovere e disinstallare l'app.  

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).   
