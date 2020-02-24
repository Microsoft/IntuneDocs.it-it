---
title: Trovare l'utente primario di un dispositivo Microsoft Intune.
titleSuffix: ''
description: Trovare l'utente primario (o l'affinità utente-dispositivo) di un dispositivo Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbafca746c43dada6281ffbfe1e34f01afa8ab91
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413686"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Trovare l'utente primario di un dispositivo Intune

Utente primario, o Affinità utente-dispositivo, è una proprietà di ogni dispositivo Intune. A un dispositivo Intune può essere assegnato da zero a un utente primario. Quando non è assegnato alcun utente primario, il dispositivo è detto "dispositivo condiviso".

## <a name="how-to-find-a-devices-primary-user"></a>Come trovare l'utente primario di un dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Scegliere **Dispositivi** e selezionare un dispositivo.
3. Nella pagina **Panoramica** scegliere **See more** (Altre informazioni) per visualizzare l'utente primario.

## <a name="what-is-the-primary-user"></a>Che cos'è l'utente primario?
La proprietà utente primario viene usata per eseguire il mapping di un utente con licenza di Intune ai propri dispositivi nelle posizioni seguenti:
- L'app Portale aziendale.
- Il sito Web dell'utente finale.
- Esperienze dei professionisti IT, come le pagine per la risoluzione dei problemi nel portale di Azure. Queste pagine mappano gli account utente ai dispositivi usando l'utente primario.    

### <a name="company-portal-app"></a>App Portale aziendale
L'app Portale aziendale presuppone che l'account utente connesso al portale aziendale sia l'utente primario del dispositivo. Se come utente primario è stato assegnato un altro utente, nel portale aziendale viene visualizzato un avviso simile al seguente:

"Il dispositivo è già assegnato a un altro utente nell'organizzazione. Contattare il servizio di supporto della società per informazioni su come diventare l'utente primario del dispositivo. È possibile continuare a usare l'app Portale aziendale, ma le funzionalità saranno limitate".

Se a un dispositivo Intune non è assegnato un utente primario, l'app Portale aziendale lo rileva come dispositivo condiviso. I dispositivi condivisi sono visivamente identificabili grazie all'etichetta "condiviso" visualizzata sul riquadro del dispositivo. In questa modalità è possibile continuare a usare l'app Portale aziendale per richiedere e installare le app disponibili. Le azioni self-service (reimpostazione/ridenominazione/ritiro) non sono però disponibili.  

Per essere visualizzate nell'app Portale aziendale su dispositivi condivisi, le app disponibili devono essere assegnate a un gruppo di utenti. Vengono installate nel contesto del sistema o nel contesto utente, in base al modo in cui sono state configurate dall'amministratore IT. Per altre informazioni sul contesto dell'app, vedere [Installare le app nei dispositivi Windows 10](../apps/apps-windows-10-app-deploy.md). Per usare questa funzionalità è necessaria l'app Portale aziendale versione 10.3.4651.0 o successive.


## <a name="who-is-assigned-as-the-primary-user"></a>Chi viene assegnato come utente primario?
Intune aggiunge automaticamente l'utente primario ai dispositivi durante o subito dopo la registrazione. Il metodo di registrazione determina il momento in cui l'utente primario viene aggiunto a un dispositivo.

| Piattaforma | Metodo di registrazione | Utente primario assegnato | Momento dell'assegnazione |
| ---- | ---- | ---- | ---- |
| Windows | Aggiunta di un account aziendale o dell'istituto di istruzione (definito dall'utente) | Utente che effettua la registrazione | Durante la registrazione |   
| Windows | Accesso a un'app moderna (definito dall'utente) | Utente che effettua la registrazione | Durante la registrazione | 
| Windows | Solo registrazione in MDM (definito dall'utente) | Utente che effettua la registrazione | Durante la registrazione | 
| Windows | Aggiunta ad Azure AD (configurazione guidata) | Utente che effettua la registrazione | Durante la registrazione | 
| Windows | Aggiunta ad Azure AD (configurazione guidata Autopilot) | Utente che effettua la registrazione | Durante la registrazione | 
| Windows | Solo registrazione in MDM | Utente che effettua la registrazione | Durante la registrazione | 
| Windows | Aggiunta ad AAD ibrida + oggetto Criteri di gruppo registrazione automatica | Primo utente ad accedere a Windows | Quando il primo utente esegue l'accesso a Windows| 
| Windows | Co-gestione | Primo utente ad accedere a Windows | Quando il primo utente esegue l'accesso a Windows | 
| Windows | Aggiunta ad Azure AD (token di registrazione in blocco) | Nessuno | Non applicabile | 
| Windows | Aggiunta ad Azure AD (modalità di distribuzione automatica Autopilot) | Nessuno | Non applicabile | 
| Multipiattaforma | Registrazione guidata dall'utente con l'app Portale aziendale | Utente che effettua la registrazione | Durante la registrazione |
| Multipiattaforma | Manager di registrazione dispositivi (DEM) | Utente DEM che effettua la registrazione | Durante la registrazione |
| iOS/iPadOS, macOS | Registrazione dispositivi automatica Apple (DEP con affinità utente) | Utente che effettua la registrazione | Durante la registrazione |
| iOS/iPadOS, macOS | Registrazione dispositivi automatica Apple (DEP senza affinità utente) | Nessuno | Non applicabile |
| Android | Dispositivi dedicati Android di proprietà dell'azienda | Nessuno | Non applicabile |

## <a name="primary-user-and-azure-ad-device-owner"></a>Utente primario e proprietario del dispositivo di Azure AD
In alcuni casi l'utente primario di Intune può essere diverso dalla proprietà **Proprietario** del dispositivo di Azure AD (visualizzabile in **Dispositivi** > **Dispositivi di Azure AD**). Il proprietario del dispositivo di Azure AD viene aggiunto durante la registrazione del dispositivo in Azure Active Directory.

## <a name="next-steps"></a>Passaggi successivi
[Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md)
