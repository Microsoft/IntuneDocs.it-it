---
title: Registrare i dispositivi usando un account del manager di registrazione dispositivi
titlesuffix: Microsoft Intune
description: Usare l'account del manager di registrazione dispositivi per registrare i dispositivi in Intune. "
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
ms.custom: intune-azure
ms.openlocfilehash: 1d3e01cdbc7c9e30034e83e9609c0df5f031c18a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184914"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Registrare i dispositivi usando un account del manager di registrazione dispositivi

È possibile registrare fino a 1.000 dispositivi mobili con un singolo account di Azure Active Directory usando un account di manager di registrazione dispositivi. Il manager di registrazione dispositivi è un'autorizzazione di Intune che può essere applicata a un account utente AAD e consente all'utente di registrare fino a 1.000 dispositivi. Un account di manager di registrazione dispositivi è utile per gli scenari in cui i dispositivi vengono registrati e preparati prima di essere distribuiti agli utenti.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitazioni dei dispositivi registrati con un account del manager di registrazione dispositivi

Gli account utente di tipo manager di registrazione dispositivi e i dispositivi registrati con un account di tale tipo presentano le seguenti limitazioni:

  - La cancellazione non può essere eseguita dal portale aziendale. La cancellazione di un dispositivo registrato da un account di manager di registrazione dispositivi può essere eseguita da Intune nel portale di Azure.
  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.
  - Gli account utente di manager di registrazione dispositivi non possono usare le app Volume Purchase Program (VPP) di Apple con licenze utente VPP Apple poiché è necessario un ID Apple per utente per la gestione delle app.
  - I dispositivi possono installare le app VPP se sono dotati delle licenze dispositivo VPP Apple.
  - I dispositivi sono bloccati per l'accesso condizionale ad eccezione di Windows 10 1803+


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

