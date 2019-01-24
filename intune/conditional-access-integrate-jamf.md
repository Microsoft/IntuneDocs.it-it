---
title: Integrare Jamf Pro con Microsoft Intune per la conformità | Microsoft Intune
description: Usare i criteri di conformità dei dispositivi Microsoft Intune con l'accesso condizionale di Azure Active Directory per proteggere i dispositivi gestiti Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 971dc851714045a8a3b60dfe8ff6c6acc4419294
ms.sourcegitcommit: 7c41f42d6e398ed46aa602ec8aaa4f39aaf92772
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54325016"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrare Jamf Pro con Intune per la conformità

Si applica a: Intune nel portale di Azure

Le organizzazioni che usano [Jamf Pro](https://www.jamf.com) per gestire i computer Mac degli utenti finali possono adottare i criteri di conformità di Microsoft Intune e l'accesso condizionale di Azure Active Directory per garantire la conformità dei dispositivi presenti nell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Per configurare l'accesso condizionale con Jamf Pro, è necessario quanto segue:

- Jamf Pro 10.1.0 o versione successiva
- [App Portale aziendale per macOS](https://aka.ms/macoscompanyportal)
- Dispositivi macOS con OS X 10.11 Yosemite o versioni successive

## <a name="connecting-intune-to-jamf-pro"></a>Connessione di Intune a Jamf Pro

Per connettere Intune a Jamf Pro, è possibile:

1. Creare una nuova applicazione in Azure
2. Abilitare Intune per l'integrazione con Jamf Pro
3. Configurare l'accesso condizionale in Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Creare un’applicazione in Azure Active Directory

1. Nel [portale di Azure](https://portal.azure.com) passare ad **Azure Active Directory** > **Registrazioni app**.
2. Selezionare **+Registrazione nuova applicazione**.
3. In **Nome visualizzato** specificare un nome, ad esempio **Accesso condizionale Jamf**.
4. Selezionare **App Web/API**.
5. Specificare l'**URL di accesso** usando l'URL dell'istanza Jamf Pro.
6. Selezionare **Crea**. Viene creata l'applicazione e i relativi dettagli vengono visualizzati nel portale.
7. Salvare una copia dell’**ID applicazione** per la nuova applicazione. Questo ID verrà specificato in una procedura successiva. Selezionare quindi **Impostazioni** e passare ad **Accesso all'API** > **Chiavi**.
8. Nel riquadro *Chiavi* specificare una **descrizione** e l’intervallo di attesa prima della **scadenza**, quindi selezionare **Salva** per generare la chiave dell’applicazione (valore).

   > [!IMPORTANT]
   > La chiave dell'applicazione viene visualizzata solo una volta durante questo processo. Assicurarsi quindi di salvarla in una posizione da cui sia possibile recuperarla facilmente.

8. Nel riquadro *Impostazioni* dell’app passare ad **Accesso all’API** > **Autorizzazioni necessarie**. Selezionare tutte le autorizzazioni esistenti e quindi fare clic su **Elimina** ed eliminare tutte le autorizzazioni. È necessario eliminare le autorizzazioni esistenti quando si aggiunge una nuova autorizzazione. L’applicazione funziona solo se è presente un’unica autorizzazione.  
9. Per assegnare una nuova autorizzazione, selezionare **+Aggiungi** > **Seleziona API** > **API Microsoft Intune**, quindi fare clic su **Seleziona**.
10. Nel riquadro *Abilita accesso* selezionare **Invia attributi dispositivo a Microsoft Intune**, fare clic su **Seleziona**, quindi su **Chiudi**.
11. Nel riquadro *Autorizzazioni necessarie* selezionare **Concedi autorizzazioni**, quindi **Sì** per applicare le autorizzazioni necessarie all’applicazione.

    > [!NOTE]
    > Se la chiave dell'applicazione scade, è necessario creare una nuova chiave dell'applicazione in Microsoft Azure e quindi aggiornare i dati di accesso condizionale in Jamf Pro. Per evitare interruzioni del servizio, Azure consente di mantenere attive sia la chiave precedente sia la nuova chiave.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Abilitare Intune per l'integrazione con Jamf Pro

1. Nel [portale di Azure](https://portal.azure.com) passare a **Microsoft Intune** > **Conformità del dispositivo** > **Gestione dei dispositivi partner**.
2. Abilitare il connettore per la conformità per Jamf incollando l'ID dell'applicazione salvato durante la procedura precedente nel campo **Jamf Azure Active Directory App ID** (ID app di Azure Active Directory per Jamf).
3. Selezionare **Salva**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurare l'integrazione di Microsoft Intune in Jamf Pro

1. In Jamf Pro passare a **Gestione globale** > **Accesso condizionale**. Fare clic sul pulsante **Modifica** nella scheda **Microsoft Intune Integration** (Integrazione Microsoft Intune).
2. Selezionare la casella di controllo **Abilita integrazione con Microsoft Intune**.
3. Fornire le informazioni necessarie sul tenant di Azure, tra cui **Percorso**, **Nome di dominio**e **ID applicazione**, oltre alla **Chiave applicazione** salvata nei passaggi precedenti.
4. Selezionare **Salva**. Jamf Pro testerà le impostazioni e ne verificherà la correttezza.

## <a name="set-up-compliance-policies-and-register-devices"></a>Impostare i criteri di conformità e registrare i dispositivi

Dopo aver configurato l'integrazione tra Intune e Jamf, è necessario [applicare i criteri di conformità per i dispositivi gestiti da Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Passaggi successivi

- [Applicare criteri di conformità a dispositivi gestiti da Jamf](conditional-access-assign-jamf.md)
- [Dati inviati da Jamf a Intune](data-jamf-sends-to-intune.md)
