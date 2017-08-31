---
title: Configurare i criteri di aggiornamento per iOS
titleSuffix: Intune on Azure
description: "Configurare i criteri di aggiornamento per iOS per forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione."
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: d4af2d58ec21c54362cf451eac1a33b2088885d5
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2017
---
# <a name="configure-ios-update-policies"></a>Configurare i criteri di aggiornamento per iOS
I criteri di aggiornamento per iOS consentono di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. È possibile configurare i giorni e gli orari in cui non si vuole che i dispositivi installino l'aggiornamento.

## <a name="configure-the-ios-update-policy"></a>Configurare i criteri di aggiornamento per iOS
1. Passare al pannello Intune nel portale di Azure.
2. Nel pannello **Intune** scegliere **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.
4. Nel pannello dei criteri scegliere **Crea** e quindi immettere un nome e una descrizione per il criterio.
5. Selezionare **Impostazioni** > **Configura** e specificare nel dettaglio quando non verrà forzata l'installazione dell'aggiornamento più recente nei dispositivi iOS.
6. Scegliere **OK** per salvare la configurazione. Si torna al pannello **Crea criteri di aggiornamento**. Scegliere **Crea** per creare i criteri e salvare le impostazioni.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei criteri di aggiornamento per iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Assegnare un criterio di aggiornamento per iOS agli utenti
Per assegnare un criterio di aggiornamento per iOS agli utenti, scegliere un criterio configurato. I criteri esistenti sono disponibili nel pannello **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.
1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i Gruppi di sicurezza Azure Active Directory e assegnarli ai criteri.
2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD. Scegliere **Seleziona** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità per l'aggiornamento.

## <a name="change-the-restricted-days-for-the-policy"></a>Modificare i giorni con restrizioni per il criterio
1. Nel pannello **Aggiornamenti software** scegliere **Criteri di aggiornamento per iOS**.
2. Selezionare il criterio di aggiornamento per iOS che si vuole aggiornare.
3. Selezionare **Proprietà** e aggiornare le informazioni sui giorni con restrizioni.
