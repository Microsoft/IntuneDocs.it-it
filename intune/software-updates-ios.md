---
title: Configurare i criteri di aggiornamento per iOS in Microsoft Intune
titlesuffix: 
description: "Configurare i criteri di aggiornamento per iOS per forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 6ba354fb3b39544f09363651abfd9e1a5c0f6154
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurare i criteri di aggiornamento per iOS in Microsoft Intune
I criteri di aggiornamento per iOS consentono di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. È possibile configurare i giorni e gli orari in cui non si vuole che i dispositivi installino l'aggiornamento.

## <a name="configure-the-ios-update-policy"></a>Configurare i criteri di aggiornamento per iOS
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
2. Nel riquadro **Intune** scegliere **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.
4. Nel riquadro dei criteri scegliere **Crea** e quindi immettere un nome e una descrizione per il criterio.
5. Selezionare **Impostazioni** > **Configura** e specificare nel dettaglio quando non viene forzata l'installazione dell'aggiornamento più recente nei dispositivi iOS.
6. Scegliere **OK** per salvare la configurazione. Si torna al riquadro **Crea criteri di aggiornamento**. Scegliere **Crea** per creare i criteri e salvare le impostazioni.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei criteri di aggiornamento per iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Assegnare un criterio di aggiornamento per iOS agli utenti
Per assegnare un criterio di aggiornamento per iOS agli utenti, scegliere un criterio configurato. I criteri esistenti sono disponibili nel riquadro **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.
1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il riquadro in cui è possibile selezionare i gruppi di sicurezza di Azure Active Directory e assegnarli ai criteri.
2. Scegliere **Gruppi selezionati** per aprire il riquadro che consente di visualizzare i gruppi di sicurezza di Azure AD.
3. Scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità degli aggiornamenti.

## <a name="change-the-restricted-days-for-the-policy"></a>Modificare i giorni con restrizioni per il criterio
1. Nel riquadro **Aggiornamenti software** scegliere **Criteri di aggiornamento per iOS**.
2. Selezionare il criterio di aggiornamento per iOS che si vuole aggiornare.
3. Selezionare **Proprietà** > **Impostazioni** per aggiornare le informazioni sui giorni con restrizioni.

## <a name="monitor-ios-devices-with-older-ios-versions"></a>Monitorare dispositivi iOS con versioni iOS precedenti
<!-- 1352223 -->
Il report **Dispositivi iOS non aggiornati** è disponibile dal riquadro **Aggiornamenti software** > **Criteri di aggiornamento per iOS**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento per iOS e che non possono essere aggiornati. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente.
