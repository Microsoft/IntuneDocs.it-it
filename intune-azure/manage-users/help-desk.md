---
title: Portale del Supporto tecnico per la risoluzione dei problemi | Microsoft Docs
titleSuffix: Intune Azure preview
description: Il personale del supporto tecnico usa il portale per risolvere i problemi tecnici degli utenti
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 4916b66e1f2eeabb42401645dbece28dad28eb19
ms.contentlocale: it-it
ms.lasthandoff: 04/26/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Assistere gli utenti con il portale per la risoluzione dei problemi in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Il portale per la risoluzione dei problemi consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare utenti e dispositivi e di eseguire attività per la risoluzione dei problemi tecnici di Intune.

## <a name="add-help-desk-operators"></a>Aggiungere operatori del supporto tecnico
Un amministratore di Intune può assegnare agli utenti l'autorizzazione di operatore del supporto tecnico. Gli utenti del supporto tecnico potranno quindi visualizzare il portale di Intune, ma non visualizzare o eseguire attività amministrative esterne al carico di lavoro di risoluzione dei problemi.

1. Accedere come amministratore di Intune al [portale di Azure](https:portal.azure.com), selezionare **More Services** (Altri servizi) > **Monitoring + Management** (Monitoraggio e gestione)  > **Intune**.
2. Nel pannello di navigazione a sinistra, selezionare **Ruoli di Intune**.
3. Nel carico di lavoro **Ruoli di Intune** selezionare **Help Desk Operator** (Operatore del supporto tecnico), quindi selezionare **Assegna**.
4. Digitare un **Nome dell'assegnazione** (obbligatorio), una **Descrizione dell'assegnazione** (facoltativa), quindi assegnare **Membri (gruppi)** e **Ambito (gruppi)**.
5. Ora i membri appartenenti al ruolo Operatore del supporto tecnico possono usare il portale per la risoluzione dei problemi.

Per altre informazioni sui ruoli di Intune, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo)](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control).

## <a name="access-the-troubleshooting-portal"></a>Accedere al portale per la risoluzione dei problemi

Il personale del supporto tecnico e gli amministratori di Intune possono accedere al portale per la risoluzione dei problemi in due modi:
- Nel [portale di Azure](https://portal.azure.com) selezionare **More Services** (Altri servizi)  > **Monitoring + Management** (Monitoraggio e gestione) > **Intune**, quindi nel pannello di navigazione a sinistra selezionare **Troubleshoot** (Risoluzione dei problemi). Nel pannello di navigazione a sinistra sono visibili altri carichi di lavoro, che tuttavia non sono disponibili.

![Screenshot del carico di lavoro Intune Troubleshoot (Risoluzione dei problemi di Intune) con il collegamento Seleziona utente](media/help-desk-user.png)
- Aprire [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) in un Web browser. È visibile solo il portale per la risoluzione dei problemi.

## <a name="use-the-troubleshooting-portal"></a>Usare il portale per la risoluzione dei problemi

Nel portale per la risoluzione dei problemi è possibile scegliere **Seleziona utente** per visualizzare le informazioni relative a un utente. Le informazioni utente sono utili per definire lo stato corrente degli utenti e dei loro dispositivi. Il portale per la risoluzione dei problemi visualizza i seguenti dettagli per gli utenti e i dispositivi di Intune:
- Informazioni sull'account utente
- Appartenenza dell'utente a gruppi
- Dettagli dispositivo

Gli utenti del servizio tecnico possono anche eseguire attività remote sui dispositivi, quali **Blocco remoto**.

