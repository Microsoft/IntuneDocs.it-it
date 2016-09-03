---
title: Risolvere i problemi relativi ai criteri | Microsoft Intune
description: Risolvere i problemi di configurazione dei criteri.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1f133d31311706365888cf33ceb4c4412deec333
ms.openlocfilehash: a8afc681b8b12e1e760dea3f784e4beac4697242


---

# Risolvere i problemi relativi ai criteri in Microsoft Intune

Se si verificano problemi durante la distribuzione e la gestione di criteri con Intune, iniziare da qui. Questo argomento descrive alcuni problemi comuni e le relative soluzioni.

## I criteri si applicano al dispositivo?
**Problema:** non è chiaro se determinati criteri si applichino a un dispositivo o se un dispositivo si comporti in modo opposto a quanto definito dai criteri.

Controllare le informazioni sui criteri disponibili per ogni dispositivo per comprendere l'impatto dei criteri su un dispositivo specifico.

Nella console di amministrazione di Intune, per ogni dispositivo è disponibile una scheda di criteri in **Proprietà dispositivo**. Se la scheda non è presente, è possibile che il dispositivo sia ancora in corso di registrazione o che non abbia criteri applicati. Ogni criterio dispone di un **previsto valore** e **stato**. Il valore previsto è quello che si intende ottenere quando si assegnano i criteri. Lo stato è ciò che effettivamente si ottiene quando tutti i criteri applicati al dispositivo, nonché le restrizioni e requisiti di hardware e del sistema operativo, vengono considerati insieme. Gli stati possibili sono:

-   **Conforme**: il dispositivo ha ricevuto i criteri e segnala al servizio di essere conforme all'impostazione.

-   **Non applicabile**: l'impostazione dei criteri non è applicabile. Ad esempio, è possibile che le impostazioni di posta elettronica per i dispositivi iOS non si applichino a un dispositivo Android.

-   **In sospeso**: i criteri sono stati inviati al dispositivo, ma il servizio non ha ricevuto informazioni relative allo stato. Ad esempio, la crittografia in Android richiede l'abilitazione da parte dell'utente e può quindi essere in sospeso.

Nella schermata seguente è possibile visualizzare due chiari esempi:

-   **Consentire password semplici** è impostato su **Sì**, come illustrato nella colonna **del valore previsto** ma lo **stato** è **non applicabile**. Infatti, le password semplici non sono supportate per i dispositivi Android.

-   Analogamente, l'elemento dei criteri espanso **Impostazioni posta elettronica per i dispositivi iOS** non viene applicato al dispositivo, dal momento che si tratta di un dispositivo Android.

![Criteri dei dispositivi Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Tenere presente che quando due criteri con livelli di restrizione diversi vengono applicati allo stesso dispositivo o utente, viene di fatto applicato il criterio più restrittivo.

## Errori relativi a criteri di Microsoft Intune in policyplatform.log
Per i dispositivi Windows non MDM, gli errori dei criteri nel file policyplatform.log potrebbero derivare da impostazioni non predefinite nel Controllo dell'account utente di Windows sul dispositivo. Alcune impostazioni non predefinite del Controllo dell'account utente possono influire sulle installazioni client di Microsoft Intune e sull'esecuzione dei criteri.

### Per risolvere i problemi relativi al Controllo dell'account utente

1.  Ritirare il computer come descritto in [Retire devices from Microsoft Intune management](/intune/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune).

2.  Attendere 20 minuti che il software client venga rimosso.

    > [!NOTE]
    > Non provare a rimuovere il client da Programmi e funzionalità.

3.  Nel menu Start digitare **Controllo account utente** per aprire le impostazioni di Controllo dell'account utente.

4.  Spostare il dispositivo di scorrimento di notifica sull'impostazione predefinita.


## Avviso: Il salvataggio delle regole di accesso in Exchange non è riuscito
**Problema**: viene visualizzato l'avviso **Il salvataggio delle regole di accesso in Exchange non è riuscito**  nella console di amministrazione.

Se sono stati creati criteri nell'area di lavoro Criteri di Exchange locale con la console di amministrazione ma si usa Office 365, le impostazioni dei criteri configurate non vengono applicate da Intune. Si noti l'origine dei criteri nell'avviso.  Nell'area di lavoro Criteri di Exchange locale eliminare le regole precedenti, in quanto si tratta di regole generali di Exchange in Intune per Exchange locale e non sono rilevanti per Office 365, quindi creare nuovi criteri per Office 365.

## ERRORE: Impossibile ottenere il valore dal computer, 0x80041013
Può verificarsi se l'ora nel sistema locale è fuori sincronia di 5 minuti o più. Se l'ora nel computer locale non è sincronizzata, le transazioni sicure avranno esito negativo perché i timestamp non saranno validi.

Per risolvere questo problema, allineare l'ora del sistema locale il più possibile all'ora o all'ora impostata nei controller di dominio sulla rete.

## Non è possibile modificare i criteri di sicurezza per vari dispositivi MDM
I dispositivi Windows Phone e Windows RT non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta dopo averli configurati. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8 che poi si tenta di ridurre a 4. I criteri più restrittivi sono già stati applicati al dispositivo.

A seconda della piattaforma del dispositivo, se si vogliono modificare i criteri a un valore meno sicuro può essere necessario reimpostare i criteri di sicurezza.
Ad esempio, in Windows RT, sul desktop scorrere verso destra per aprire la barra **Accessi** e scegliere **Impostazioni** &gt; **Pannello di controllo**.  Selezionare l'applet **Account utente** .
Nella parte inferiore del menu di navigazione a sinistra è disponibile un collegamento **Reimposta criteri di sicurezza** . Selezionare tale collegamento e scegliere il pulsante **Reimposta criteri**.
È possibile che altri dispositivi MDM, ad esempio Android, Windows Phone 8.1 e versione successiva e iOS, debbano essere ritirati e registrati nuovamente al servizio per consentire all'utente di applicare criteri meno restrittivi.

## Non è possibile creare criteri o registrare client se il nome della società contiene caratteri speciali
**Problema:** non è possibile creare criteri o registrare client.

**Risoluzione:** nell'[interfaccia di amministrazione di Office 365](https://portal.office.com/) rimuovere i caratteri speciali dal nome della società e salvare le informazioni aziendali.

### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO4-->


