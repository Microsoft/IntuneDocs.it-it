---
title: Amministrare dispositivi in remoto in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare i ruoli richiesti per l'uso di TeamViewer, come installare TeamViewer Connector e le procedure dettagliate per l'amministrazione remota dei dispositivi usando Microsoft Intune nel portale di Azure
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 60d9398b80a30adee194470ac4e5c6c1efc0bd4c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744636"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Usare TeamViewer per l'amministrazione remota dei dispositivi di Intune

È possibile amministrare in remoto i dispositivi gestiti da Intune mediante [TeamViewer](https://www.teamviewer.com). TeamViewer è un programma di terze parti da acquistare separatamente. In questo argomento viene illustrato come configurare TeamViewer in Intune per l'amministrazione in remoto di un dispositivo. 

## <a name="prerequisites"></a>Prerequisiti

- Usare un dispositivo supportato. I dispositivi Android, Windows, iOS e macOS gestiti da Intune supportano l'amministrazione remota. TeamViewer potrebbe non supportare Windows Holographic (HoloLens), Windows Team (Surface Hub) o Windows 10 S. Per informazioni sul supporto, vedere [TeamViewer](https://www.teamviewer.com) per eventuali aggiornamenti.

- L'amministratore di Intune nel portale di Azure deve avere i seguenti [ruoli di Intune](role-based-access-control.md):  

    - **Update Remote Assistance** (Aggiorna assistenza remota): consente agli amministratori di modificare le impostazioni di TeamViewer Connector.
    - **Request Remote Assistance** (Richiedi assistenza remota): consente agli amministratori di avviare una nuova sessione di assistenza remota per qualsiasi utente. Gli utenti con questo ruolo non sono limitati da nessun ruolo di Intune in un determinato ambito. Anche i gruppi di utenti o dispositivi ai quali è assegnato un ruolo di Intune in un determinato ambito possono richiedere assistenza remota. 

- Account di [TeamViewer](https://www.teamviewer.com) con le credenziali di accesso

Usando TeamViewer si consente a TeamViewer Connector per Intune di creare sessioni di TeamViewer, leggere i dati di Active Directory e salvare il token di accesso dell'account TeamViewer.

## <a name="configure-the-teamviewer-connector"></a>Configurare TeamViewer Connector

Per offrire assistenza remota ai dispositivi, è necessario configurare TeamViewer Connector per Intune, eseguendo la procedura seguente:

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** e cercare **Microsoft Intune**.
2. In **Microsoft Intune** selezionare **Dispositivi**, quindi selezionare **TeamViewer Connector**.
3. Selezionare **Connetti**, quindi accettare il Contratto di licenza.
4. Scegliere **Accedere a TeamViewer per l'autorizzazione**.
5. Verrà visualizzata una pagina Web del sito di TeamViewer. Immettere le credenziali della licenza di TeamViewer e fare clic su **Accedi**.

## <a name="remotely-administer-a-device"></a>Amministrare un dispositivo in remoto

Dopo la configurazione di Connector è possibile iniziare ad amministrare un dispositivo in remoto. Effettuare i seguenti passaggi: 

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** e cercare **Microsoft Intune**.
2. In **Microsoft Intune** selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
3. Nell'elenco selezionare il dispositivo che si vuole amministrare in remoto. Nelle proprietà del dispositivo selezionare **Nuova sessione di assistenza remota**.
4. Dopo la connessione di Intune al servizio TeamViewer, verranno visualizzate alcune informazioni sul dispositivo. Scegliere **Connetti** per avviare la sessione remota.

![Usare TeamViewer per amministrare in remoto un dispositivo Android - Esempio](./media/android-teamviewer.png)

Quando si avvia una sessione remota, un utente finale vede un flag di notifica sull'icona dell'app Portale aziendale nel dispositivo in uso. All'apertura dell'app viene visualizzata un'altra notifica. L'utente può quindi accettare la richiesta di assistenza remota.

In TeamViewer è possibile completare una serie di azioni sul dispositivo, inclusa l'acquisizione del controllo del dispositivo. Per informazioni complete sulle operazioni possibili, vedere il [materiale sussidiario per TeamViewer](https://www.teamviewer.com/support/documents/).

Al termine chiudere la finestra di TeamViewer.