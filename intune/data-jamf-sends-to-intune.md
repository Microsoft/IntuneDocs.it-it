---
title: Dati inviati da JAMF Pro a Intune | Microsoft Intune
description: Elenco di dati che Jamf Pro Invia a Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5b58a92ed59d4485f06370672d8c335ff2fffcc7
ms.sourcegitcommit: 7c41f42d6e398ed46aa602ec8aaa4f39aaf92772
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327926"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dati inviati da Jamf Pro a Intune

Quando si usa [Jamf Pro](https://www.jamf.com) per gestire i computer Mac degli utenti finali con Intune, Jamf Pro acquisisce informazioni sull'inventario per i dispositivi macOS gestiti e fornisce le informazioni seguenti a Intune:

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


È possibile rimuovere un dispositivo gestito da Jamf dalla console di Intune selezionando **Elimina** nella vista **Tutti i dispositivi**. L'eliminazione in blocco dei dispositivi può essere abilitata selezionando più dispositivi e facendo clic su **Elimina**.

Ottenere informazioni su come [rimuovere un dispositivo gestito da Jamf nella documentazione di Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Per altre informazioni, è anche possibile registrare un ticket di supporto presso il [supporto Jamf](https://www.jamf.com/support/). 

