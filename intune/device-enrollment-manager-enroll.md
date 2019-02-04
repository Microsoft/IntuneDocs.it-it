---
title: Registrare i dispositivi usando un account del manager di registrazione dispositivi
titlesuffix: Microsoft Intune
description: Usare l'account del manager di registrazione dispositivi per registrare i dispositivi in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: be348840df2e1d7864b0c1c57efbb7abcb698392
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199388"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Registrare i dispositivi in Intune usando un account del manager di registrazione dispositivi

È possibile registrare fino a 1.000 dispositivi mobili con un singolo account di Azure Active Directory usando un account di manager di registrazione dispositivi. Il manager di registrazione dispositivi è un'autorizzazione di Intune che può essere applicata a un account utente AAD e consente all'utente di registrare fino a 1.000 dispositivi. Un account di manager di registrazione dispositivi è utile per gli scenari in cui i dispositivi vengono registrati e preparati prima di essere distribuiti agli utenti.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitazioni dei dispositivi registrati con un account del manager di registrazione dispositivi

Gli account utente di tipo manager di registrazione dispositivi e i dispositivi registrati con un account di tale tipo presentano le seguenti limitazioni:

  - La cancellazione non può essere eseguita dal portale aziendale. La cancellazione di un dispositivo registrato da un account di manager di registrazione dispositivi può essere eseguita da Intune nel portale di Azure.
  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.
  - Gli account utente di manager di registrazione dispositivi non possono usare le app Volume Purchase Program (VPP) di Apple con licenze utente VPP Apple poiché è necessario un ID Apple per utente per la gestione delle app.
  - I dispositivi possono installare le app VPP se sono dotati delle licenze dispositivo VPP Apple.
  - I dispositivi sono bloccati per l'accesso condizionale ad eccezione di Windows 10 1803+
  - Ogni dispositivo registrato con un account manager di registrazione dispositivi deve avere la propria licenza dispositivo Intune.


## <a name="add-a-device-enrollment-manager"></a>Aggiungere un manager di registrazione dispositivi

1.  Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Manager di registrazione dispositivi**.

2.  Selezionare **Aggiungi**.

3.  Nel pannello **Aggiungi utente** immettere un nome entità utente per l'utente manager di registrazione dispositivi, quindi selezionare **Aggiungi**. L'utente manager di registrazione dispositivi viene aggiunto all'elenco di utenti manager di registrazione dispositivi.

## <a name="permissions-for-dem"></a>Autorizzazioni per il manager di registrazione dispositivi

I ruoli di Azure AD Amministratore globale o Amministratore del servizio Intune sono necessari per
- assegnare un'autorizzazione di manager di registrazione dispositivi a un account utente di Azure AD
- visualizzare tutti gli utenti manager di registrazione dispositivi

Se un utente non ha il ruolo Amministratore globale o Amministratore del servizio Intune, ma ha le di autorizzazioni di lettura abilitate per il ruolo Manager di registrazione dispositivi, può visualizzare solo gli utenti manager di registrazione dispositivi che ha creato.


## <a name="remove-device-enrollment-manager-permissions"></a>Rimuovere le autorizzazioni di manager di registrazione dispositivi

La rimozione di un manager di registrazione dispositivi non influisce sui dispositivi registrati.

**Per rimuovere un manager di registrazione dispositivi**

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** e quindi scegliere **Manager di registrazione dispositivi**.
2. Nel pannello **Manager di registrazione dispositivi** selezionare l'utente manager di registrazione dispositivi e selezionare **Elimina**.

