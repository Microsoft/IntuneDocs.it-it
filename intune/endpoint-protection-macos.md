---
title: Aggiungere Endpoint Protection su macOS in Microsoft Intune - Azure | Documenti Microsoft
description: Nei dispositivi macOS utilizzare il gatekeeper per determinare dove è possibile installare le app, incluso il Mac App Store. Inoltre, abilitare o configurare un firewall per autorizzare app specifiche, bloccare app specifiche, utilizzare la modalità mascheramento e persino bloccare determinati tipi di connessioni in ingresso con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e050d188d4508225ef384fbf557e7724efacab18
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047728"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Impostazioni di Endpoint Protection per macOS in Intune

Questo articolo illustra le impostazioni di Endpoint Protection configurabili per i dispositivi che eseguono macOS. Le impostazioni includono le impostazioni del gatekeeper e del firewall in questi dispositivi e possono essere configurate con un profilo del dispositivo in Microsoft Intune.

## <a name="gatekeeper"></a>Gatekeeper

- **Consenti le app scaricate da queste posizioni**: limitare le app a seconda di dove le app vengono scaricate. L'obiettivo è proteggere i dispositivi da malware e autorizzare solo le app provenienti da origini attendibili. È possibile consentire le origini seguenti: 
  - **Mac App Store**
  - **Mac App Store e sviluppatori identificati**
  - **Ovunque**

- **L'utente può eseguire l'override di Gatekeeper**: impedisce agli utenti di eseguire l'override dell'impostazione Gatekeeper e usare Clic+CTRL per installare un'app. Quando è abilitata, gli utenti possono usare Clic+CTRL per installare qualsiasi app.

## <a name="firewall"></a>Firewall

Usare il firewall per controllare le connessioni per ogni singola applicazione, anziché per ogni porta. L'uso delle impostazioni in base alle singole applicazione rende più facile sfruttare i vantaggi di protezione mediante firewall. Contribuisce, inoltre, a impedire che app indesiderate assumano il controllo delle porte di rete aperte per app legittime.

- **È possibile usare il firewall per proteggere i dispositivi dall'accesso di rete non autorizzato tramite il controllo delle connessioni in base alle singole app.**
  - **Firewall**: abilitare il firewall per configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.
  - **Connessioni in ingresso**: bloccare tutte le connessioni in ingresso tranne le connessioni necessarie per i servizi Internet base, ad esempio DHCP, Bonjour e IPSec. Questa opzione blocca anche tutti i servizi di condivisione, ad esempio Condivisione file e Condivisione schermo. Se si utilizzano servizi di condivisione, mantenere questa impostazione come **Non configurato**.

- **È possibile consentire o bloccare le connessioni in ingresso per app specifiche**
  - **App consentite**: selezionare le app che sono esplicitamente autorizzate a ricevere connessioni in ingresso.
  - **App bloccate**: selezionare le app che devono bloccare le connessioni in ingresso.
  - **Modalità mascheramento**: abilitare questa modalità per impedire che il computer risponde alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate. Le richieste impreviste, ad esempio le richieste ICMP (ping), vengono ignorate.
