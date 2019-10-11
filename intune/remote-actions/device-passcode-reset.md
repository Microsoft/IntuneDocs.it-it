---
title: Reimpostare i passcode dei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Rimuovere o reimpostare il passcode tramite l'azione di rimozione del passcode nei dispositivi gestiti o monitorati con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34aea5256ebb7d6577b4e77054dcca63d47bf317
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728585"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Reimpostare o rimuovere il passcode di un dispositivo in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo documento illustra sia la reimpostazione del passcode a livello di dispositivo sia la reimpostazione del passcode del profilo di lavoro nei dispositivi Android Enterprise, chiamati in precedenza dispositivi Android for Work o AfW. È importante tenere presente questa distinzione, perché i requisiti per le due procedure possono variare. Una reimpostazione del passcode a livello di dispositivo reimposta il passcode per l'intero dispositivo. Una reimpostazione del passcode del profilo lavoro reimposta il passcode solo per il profilo di lavoro dell'utente nei dispositivi Android Enterprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Piattaforme supportate per la reimpostazione del passcode a livello di dispositivo

| Piattaforma | Supportata |
| ---- | ---- |
| Dispositivi Android versione 6.x o precedenti | Sì |
| Dispositivi aziendali Android in modalità tutto schermo | Sì |
| Dispositivi iOS | Sì |
| Dispositivi iOS registrati con la registrazione utenti | No |
| Dispositivi Android registrati con un profilo di lavoro | No |
| Dispositivi Android versione 7.0 o successive | No |
| macOS | No |
| Windows | No |

Per i dispositivi Android, questo significa che la reimpostazione del passcode a livello di dispositivo è supportata solo nei dispositivi che eseguono la versione 6.x o precedenti oppure nei dispositivi Android Enterprise in modalità tutto schermo. Questo avviene perché Google ha eliminato il supporto per la reimpostazione di passcode/password di un dispositivo Android 7 all'interno di app concesse da un amministratore di dispositivi e il vincolo si estende a tutti i fornitori di software MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Piattaforme supportate per la reimpostazione del passcode del profilo di lavoro di Android Enterprise

| Piattaforma | Supportata |
| ---- | ---- |
| Dispositivi Android Enterprise registrati con un profilo di lavoro e che eseguono la versione 8.0 o successive | Sì |
| Dispositivi Android Enterprise registrati con un profilo di lavoro e che eseguono la versione 7.x o precedenti | No |
| Dispositivi Android che eseguono la versione 7.x o precedenti | No |

Per creare un nuovo passcode del profilo di lavoro, usare l'azione di Reimposta passcode. Questa azione richiede una reimpostazione del passcode e crea un nuovo passcode temporaneo riservato al profilo di lavoro. 

## <a name="reset-a-passcode"></a>Reimpostare un passcode


1. Accedere al [portale di Azure](https://portal.azure.com) con uno dei ruoli seguenti: Amministratore globale di Azure Active Directory, amministratore del servizio Intune per Azure Active Directory, operatore del supporto tecnico o amministratore dei ruoli.
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo e scegliere **...Altre informazioni**. Quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="reset-android-work-profile-passcodes"></a>Reimpostare i passcode dei profili di lavoro Android

I dispositivi Android Enterprise supportati registrati con un profilo di lavoro ricevono una nuova password per lo sblocco del profilo gestito o una richiesta di profilo gestito per l'utente finale.

Nei dispositivi Android Enterprise che eseguono la versione 8. x o successive, e registrati con un profilo di lavoro, gli utenti finali vengono avvisati di attivare la reimpostazione del passcode non appena la registrazione viene completata. La notifica viene visualizzata se la password di un profilo di lavoro è necessaria e impostata. Dopo l'immissione del passcode, la notifica viene chiusa.


## <a name="remove-ios-passcodes"></a>Rimuovere i passcode iOS

Anziché reimpostati, i passcode vengono rimossi dai dispositivi iOS. Se è impostato un criterio di conformità passcode, il dispositivo richiede all'utente di definire un nuovo passcode nelle impostazioni.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** in **Dispositivi**.
