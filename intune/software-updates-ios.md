---
title: Configurare i criteri di aggiornamento software per iOS in Microsoft Intune
titlesuffix: ''
description: Configurare i criteri di aggiornamento per iOS per forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 58727a501d6a8ec14e964094eac9fcd6eb3868da
ms.sourcegitcommit: c3ae3c3dc46b62d9191813d25a196874ba4927be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurare i criteri di aggiornamento per iOS in Microsoft Intune

I criteri di aggiornamento software consentono di forzare l'installazione automatica dell'aggiornamento del sistema operativo più recente disponibile nei dispositivi iOS che eseguono iOS 10.3 e versioni successive con supervisione. Questa funzionalità è disponibile solo per i dispositivi con supervisione. È possibile configurare i giorni e gli orari in cui non si vuole che i dispositivi installino l'aggiornamento. 

Quando il dispositivo si collega al servizio, se è disponibile un aggiornamento e al di fuori di un intervallo di tempo dotato di restrizioni, ogni 8 ore il dispositivo tenterà di scaricare e installare l'aggiornamento del sistema operativo più recente. Non è necessario alcun intervento dell'utente per aggiornare il dispositivo. Il criterio potrebbe non impedire a un utente di aggiornare il sistema operativo.

## <a name="configure-the-ios-update-policy"></a>Configurare i criteri di aggiornamento per iOS
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.
4. Nel riquadro dei criteri scegliere **Crea** e quindi immettere un nome e una descrizione per il criterio.
5. Selezionare **Impostazioni** > **Configura** e specificare nel dettaglio quando non viene forzata l'installazione dell'aggiornamento più recente nei dispositivi iOS. È possibile configurare giorni della settimana, fuso orario, ora di inizio e ora di fine.
6. Scegliere **OK** per salvare la configurazione. Si torna al riquadro **Crea criteri di aggiornamento**. Scegliere **Crea** per creare i criteri e salvare le impostazioni.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei criteri di aggiornamento per iOS. La gestione di dispositivi mobili di Apple non consente di forzare l'installazione dell'aggiornamento sul dispositivo entro una determinata ora o data. 

## <a name="change-the-restricted-times-for-the-policy"></a>Modificare gli intervalli di tempo dotati di restrizioni per il criterio

1.  Nel pannello **Aggiornamenti software** scegliere **Criteri di aggiornamento per iOS**.
2.  Selezionare il criterio di aggiornamento per iOS che si vuole aggiornare.
3.  Selezionare **Proprietà** e aggiornare le informazioni sugli intervalli di tempo dotati di restrizioni.
4.  Scegliere i giorni della settimana
5.  Fuso orario nel quale verrà applicato il criterio
6.  Ora di inizio e fine per le ore disattivate

## <a name="assign-an-ios-update-policy-to-users"></a>Assegnare un criterio di aggiornamento per iOS agli utenti

Per assegnare un criterio di aggiornamento per iOS agli utenti, scegliere un criterio configurato. I criteri esistenti sono disponibili nel riquadro **Aggiornamenti software** > **Criteri di aggiornamento per iOS**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il riquadro in cui è possibile selezionare i gruppi di sicurezza di Azure Active Directory e assegnarli ai criteri.
2. Scegliere **Gruppi selezionati** per aprire il riquadro che consente di visualizzare i gruppi di sicurezza di Azure AD. Determinare chi ha accesso al criterio assegnando i gruppi da includere ed escludere.
3. Scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità degli aggiornamenti. Questo criterio supporta anche i dispositivi senza utente.

## <a name="monitor-ios-device-installation-failures"></a>Monitorare gli errori di installazione nei dispositivi iOS
<!-- 1352223 -->
Il report **Installation failures for iOS devices** (Errori di installazione per dispositivi iOS) è disponibile nel riquadro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento per iOS e che nonostante il tentativo di aggiornamento non è stato possibile aggiornare. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. I dispositivi integri e aggiornati non verranno visualizzati nell'elenco. Un dispositivo è aggiornato se possiede l'ultimo aggiornamento che è in grado di supportare.

