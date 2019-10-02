---
title: Dati inviati da Jamf Pro a Intune
titleSuffix: Microsoft Intune
description: Esaminare l'elenco di dati inviati da Jamf Pro a Microsoft Intune quando si integra Jamf Pro per gestire i computer Mac con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce9a92a9fffad13c6723504735b1b1cb9442f61f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721461"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dati inviati da Jamf Pro a Intune

Quando si usa [Jamf Pro](https://www.jamf.com) per gestire i computer Mac degli utenti finali con Intune, Jamf Pro acquisisce informazioni sull'inventario per i dispositivi macOS gestiti 

## <a name="data"></a>Dati  
e fornisce le informazioni seguenti a Intune:  

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
* Nome dispositivo
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
* Totale RAM
* UDID
* Indirizzo di posta elettronica dell'utente

È possibile rimuovere un dispositivo gestito da Jamf dalla console di Intune selezionando **Elimina** nella vista **Tutti i dispositivi**. L'eliminazione in blocco dei dispositivi può essere abilitata selezionando più dispositivi e facendo clic su **Elimina**.

## <a name="next-steps"></a>Passaggi successivi
Ottenere informazioni su come [rimuovere un dispositivo gestito da Jamf nella documentazione di Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Per altre informazioni, è anche possibile registrare un ticket di supporto presso il [supporto Jamf](https://www.jamf.com/support/). 

