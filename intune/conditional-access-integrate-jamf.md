---
title: "Integrare Jamf Pro con Intune per la conformità"
titlesuffix: Azure portal
description: "Usare i criteri di conformità per proteggere i dispositivi gestiti da Jamf."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b37ffd23f8cf8764ba457b0803dfc308cf1c071
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrare Jamf Pro con Intune per la conformità

|Si applica a: Intune nel Portale di Azure |
|--|
|Serve documentazione su Intune nel portale classico? [Fare clic qui](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Attualmente in anteprima privata|
|--|
|Le funzionalità descritte in questo argomento sono disponibili solo ai clienti attualmente registrati per l'anteprima privata. Questo messaggio verrò rimosso dopo il rilascio per tutti i clienti.|
| |

Le organizzazioni che usano [Jamf Pro](https://www.jamf.com) per gestire i computer Mac degli utenti finali possono adottare i criteri di conformità di Microsoft Intune e l'accesso condizionale di Azure Active Directory per garantire la conformità dei dispositivi presenti nell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Per configurare l'accesso condizionale con Jamf Pro, è necessario quanto segue:

- Accesso all'anteprima privata di Intune per l'accesso condizionale a macOS
- Jamf Pro 10.1.0 o versione successiva
- [App Portale aziendale per macOS](https://aka.ms/macoscompanyportal)
- Dispositivi macOS con OS X 10.11 Yosemite o versioni successive

## <a name="connecting-intune-to-jamf-pro"></a>Connessione di Intune a Jamf Pro

Per connettere Intune a Jamf Pro, è possibile:

1. Creare una nuova applicazione in Azure
2. Abilitare Intune per l'integrazione con Jamf Pro
3. Configurare l'accesso condizionale in Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Creare una nuova applicazione in Azure Active Directory

1. Aprire **Azure Active Directory** > **Registrazione dell'applicazione**.
2. Fare clic su **Registrazione nuova applicazione**.
3. In **Nome visualizzato** specificare un nome, ad esempio **Accesso condizionale Jamf**.
4. Selezionare **App Web/API**.
5. Specificare l'**URL di accesso** per Jamf Pro.
6. Fare clic su **Crea applicazione**.
7. Salvare l'**ID applicazione** appena creato e quindi aprire **Tutte le impostazioni** > **Chiavi** per creare una nuova chiave dell'applicazione. Salvare la chiave dell'applicazione.

  > [!NOTE]
  > La chiave dell'applicazione viene visualizzata solo una volta durante questo processo. Assicurarsi quindi di salvarla in una posizione da cui sia possibile recuperarla facilmente.

8. Passare a **Tutte le impostazioni** > **Accesso API** > **Autorizzazioni necessarie** ed eliminare tutte le autorizzazioni.

  > [!NOTE]
  > Aggiungere un nuova autorizzazione richiesta. È possibile che l'applicazione funzioni correttamente solo se è dotata dell'unica l'autorizzazione richiesta.

9.  Selezionare **API di Microsoft Intune** e fare clic su **Seleziona**.
10. Scegliere **Send device attributes to Microsoft Intune** (Invia gli attributi dei dispositivi a Microsoft Intune) e fare clic su **Seleziona**.
11. Fare clic sul pulsante **Concedi autorizzazioni** dopo aver salvato le autorizzazioni necessarie per l'applicazione.

  > [!NOTE]
  > Se la chiave dell'applicazione scade, è necessario creare una nuova chiave dell'applicazione in Microsoft Azure e quindi aggiornare i dati di accesso condizionale in Jamf Pro. Per evitare interruzioni del servizio, Azure consente di mantenere attive sia la chiave precedente sia la nuova chiave.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Abilitare Intune per l'integrazione con Jamf Pro

1. Nel portale di Microsoft Azure, aprire **Microsoft Intune** > **Conformità del dispositivo** > **Connettore per la conformità per Jamf**.
2. Abilitare il connettore per la conformità per Jamf incollando l'ID dell'applicazione nel campo **Jamf Azure Active Directory App ID** (ID app di Azure Active Directory per Jamf).
3. Fare clic su **Save**.

## <a name="configure-conditional-access-in-jamf-pro"></a>Configurare l'accesso condizionale in Jamf Pro

1. In Jamf Pro passare a **Gestione globale** > **Accesso condizionale**. Fare clic sul pulsante **Modifica** nella scheda **Microsoft**.
2. Selezionare la casella di controllo **Enable Conditional Access with Microsoft** (Abilita accesso condizionale con Microsoft).
3. Fornire le informazioni necessarie sul tenant di Azure, tra cui **Percorso**, **Nome di dominio**e **ID applicazione**, oltre alla **Chiave applicazione** salvata nei passaggi precedenti.
4. Fare clic su **Save**. Jamf Pro testerà le impostazioni e ne verificherà la correttezza.

## <a name="information-shared-from-jamf-pro-to-intune"></a>Informazioni condivise da Jamf Pro in Intune

Jamf Pro acquisisce informazioni di inventario sui dispositivi macOS gestiti e fornisce le informazioni seguenti a Intune:

* ID Azure AD del dispositivo
* Stato di inventario JAMF (stato di inventario di un computer che ha eseguito l'archiviazione con Jamf Pro nelle ultime 24 ore)
* Versione sistema operativo
* ID Azure AD dell'utente
* File crittografati (FileVault 2)
* Stato del gatekeeper
* Password: numero minimo di set di caratteri
* Scadenza password (giorni)
* Tipo di password: semplice, alfanumerica o sconosciuta
* Accesso automatico non consentito
* Lunghezza del passcode richiesta
* Password: numero di password precedenti per evitarne il riutilizzo
* Protezione dell'integrità del sistema
* Ora dell'ultima archiviazione
* Tipo di architettura
* Slot di memoria RAM disponibili
* Capacità della batteria
* ROM di avvio
* Velocità del bus
* Dimensione cache (%):
* Nome periferica
* Aggiunta al dominio
* ID Jamf
* Indirizzo MAC
* Marca
* Modello
* Identificatore del modello
* Velocità della scheda di interfaccia di rete
* Numero di core
* Numero di processori
* Sistema operativo
* Piattaforma
* Velocità processore
* Tipo di processore
* Indirizzo MAC secondario
* Numero di serie
* Versione SMC
* RAM totale
* UDID
* Indirizzo di posta elettronica dell'utente

## <a name="next-steps"></a>Passaggi successivi

- [Applicare criteri di conformità a dispositivi gestiti da Jamf](conditional-access-assign-jamf.md)
