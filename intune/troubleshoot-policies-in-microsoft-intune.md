---
title: Risoluzione dei problemi dei criteri in Microsoft Intune - Azure | Microsoft Docs
description: Problemi comuni e soluzioni per l'uso dei criteri in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d656dcc8c3abcf3a4b0a9c6aacbc42eb896289f
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096503"
---
# <a name="troubleshoot-policies-in-intune"></a>Risolvere i problemi relativi ai criteri in Intune

Se si verificano problemi durante la distribuzione e la gestione di criteri Intune, iniziare da qui. Questo articolo descrive alcuni problemi comuni riscontrabili e le possibili soluzioni.

## <a name="general-issues"></a>Problemi generali

### <a name="was-a-deployed-policy-applied-to-the-device"></a>È stato applicato un criterio distribuito al dispositivo?
**Problema:** non si è sicuri se un criterio è stato applicato correttamente.

In Intune > **Dispositivi** > **Tutti i dispositivi** > selezionare il dispositivo > **Configurazione del dispositivo**. Per ogni dispositivo sono elencati i relativi criteri. Ogni criterio ha uno **Stato**. Lo stato è ciò che si ottiene quando tutti i criteri applicati al dispositivo, nonché le restrizioni e i requisiti di hardware e del sistema operativo, vengono considerati insieme. Gli stati possibili sono:

- **Conforme**: il dispositivo ha ricevuto i criteri e segnala al servizio di essere conforme all'impostazione.

- **Non applicabile**: l'impostazione dei criteri non è applicabile. Ad esempio, è possibile che le impostazioni di posta elettronica per i dispositivi iOS non si applichino a un dispositivo Android.

- **In sospeso**: i criteri sono stati inviati al dispositivo, ma il servizio non ha ricevuto informazioni relative allo stato. Ad esempio, la crittografia in Android richiede l'abilitazione da parte dell'utente e può quindi comparire come in sospeso.

> [!NOTE]
> Quando due criteri con livelli di restrizione diversi vengono applicati allo stesso dispositivo o utente, viene applicato il criterio più restrittivo.

## <a name="issues-with-enrolled-devices"></a>Problemi con i dispositivi registrati

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Avviso: Il salvataggio delle regole di accesso in Exchange non è riuscito
**Problema**: viene visualizzato l'avviso **Il salvataggio delle regole di accesso in Exchange non è riuscito**  nella console di amministrazione.

Se sono stati creati criteri nell'area di lavoro Criteri di Exchange locale con la console di amministrazione ma si usa Office 365, le impostazioni dei criteri configurate non vengono applicate da Intune. Si noti l'origine dei criteri nell'avviso.  Nell'area di lavoro Criteri di Exchange locale eliminare le regole precedenti. Le regole precedenti sono regole generali di Exchange in Intune per Exchange locale e non sono rilevanti per Office 365, quindi creare nuovi criteri per Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Non è possibile modificare i criteri di sicurezza per vari dispositivi registrati
I dispositivi Windows Phone non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta dopo averli configurati. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8 che poi si tenta di ridurre a 4. I criteri più restrittivi sono già stati applicati al dispositivo.

A seconda della piattaforma del dispositivo, se si vogliono modificare i criteri a un valore meno sicuro può essere necessario reimpostare i criteri di sicurezza.

Ad esempio, in Windows, sul desktop scorrere verso destra per aprire la barra **Accessi**. Scegliere **Impostazioni** > **Pannello di controllo** e selezionare **Account utente**. A sinistra, selezionare il collegamento **Reimposta criteri di sicurezza** e scegliere **Reimposta criteri**.

È possibile che altri dispositivi MDM, ad esempio dispositivi Android, Windows Phone 8.1 e versione successiva e iOS, debbano essere ritirati e registrati nuovamente nel servizio per applicare criteri meno restrittivi.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problemi con i PC che eseguono il client software di Intune

Si applica al portale classico.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errori relativi a criteri di Microsoft Intune in policyplatform.log
Per i PC Windows gestiti con il client software di Intune, gli errori dei criteri nel file policyplatform.log possono derivare da impostazioni non predefinite nel Controllo dell'account utente di Windows sul dispositivo. Alcune impostazioni non predefinite del Controllo dell'account utente possono influire sulle installazioni client di Microsoft Intune e sull'esecuzione dei criteri.

#### <a name="resolve-uac-issues"></a>Risolvere i problemi relativi al Controllo dell'account utente

1. Ritirare il computer. Vedere [Rimuovere i dispositivi](devices-wipe.md).

2. Attendere 20 minuti che il software client venga rimosso.

    > [!NOTE]
    > Non provare a rimuovere il client da Programmi e funzionalità.

3. Nel menu Start digitare **Controllo account utente** per aprire le impostazioni di Controllo dell'account utente.

4. Spostare il dispositivo di scorrimento di notifica sull'impostazione predefinita.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERRORE: Impossibile ottenere il valore dal computer, 0x80041013
Si verifica se l'ora nel sistema locale è fuori sincronia di 5 minuti o più. Se l'ora nel computer locale non è sincronizzata, le transazioni sicure avranno esito negativo perché i timestamp non saranno validi.

Per risolvere questo problema, allineare l'ora del sistema locale il più possibile all'ora o all'ora impostata nei controller di dominio sulla rete.

### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto tecnico Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).
