---
title: Aggiungere impostazioni personalizzate per dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per dispositivi Android per creare un profilo Wi-Fi con una chiave precondivisa, creare un profilo VPN per app o consentire e bloccare app per dispositivi Samsung Knox Standard in Microsoft Intune
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa105cc96cd0fa7d8c6beb32cdb80b7782d9828c
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2018
---
# <a name="custom-settings-for-android-devices---intune"></a>Impostazioni personalizzate per dispositivi Android - Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I profili personalizzati usano impostazioni Open Mobile Alliance Uniform Resource Identifier (URI-OMA) per configurare funzionalità diverse nei dispositivi Android. Tali impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità del dispositivo.

L'uso di un profilo personalizzato consente di configurare e assegnare le impostazioni Android seguenti. Tali impostazioni non sono predefinite nei criteri di Intune:

- [Creare un profilo Wi-Fi con una chiave precondivisa](/intune/wi-fi-profile-shared-key)
- [Creare un profilo VPN per ogni app](/intune/android-pulse-secure-per-app-vpn)
- [Consentire e bloccare app per dispositivi Samsung Know Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Solo le impostazioni elencate in precedenza possono essere configurate da questo tipo di profilo. I dispositivi Android non espongono un elenco completo di impostazioni URI OMA configurabili. Se si vogliono visualizzare altre impostazioni, chiedere più impostazioni nel [sito Uservoice di Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Impostazioni del profilo personalizzate per dispositivi Android

1. Accedere al [portale di Azure](https://portal.azure.com). 
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Creare un profilo personalizzato usando la piattaforma Android. La procedura è illustrata in [Configurare impostazioni dispositivo personalizzate in Microsoft Intune](custom-settings-configure.md).
4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi** e **Aggiungi riga**.
5. Immettere le seguenti proprietà:

  - **Nome**: immettere un nome univoco per l'impostazione URI OMA in modo da poterla individuare facilmente.
  - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
  - **Tipo di dati**: immettere il tipo di dati da usare per l'impostazione URI OMA. Scegliere tra **Stringa**, **Stringa (XML)**, **Data e ora**, **Intero**, **Virgola mobile** o **Booleano**.
  - **URI-OMA**: immettere l'impostazione URI OMA di preferenza.
  - **Valore**: immettere il valore da associare all'impostazione URI OMA immessa.

6. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver completato le impostazioni, il profilo viene creato e visualizzato nell'elenco. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
