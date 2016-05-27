---
# required metadata

title: Risolvere i problemi relativi ai criteri | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Risolvere i problemi relativi ai criteri in Microsoft Intune

Di seguito sono elencati alcuni problemi che potrebbero emergere dalla configurazione dei criteri di Microsoft Intune e indicazioni per la risoluzione di questi problemi.

Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md) per trovare altri modi per ottenere assistenza.


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

## Intervalli di aggiornamento dei criteri
I criteri vengono aggiornati a intervalli regolari. In generale, i criteri dovrebbero essere registrati nei dispositivi entro 15 minuti dall'applicazione di una modifica. Ecco altri dettagli sugli intervalli regolari per l'aggiornamento dei criteri:

-   **Dispositivo Windows registrato per MDM**: viene generato da un'attività pianificata alle 15.00 ora locale sul dispositivo e si verifica ogni giorno.

-   **Windows Phone**: i criteri vengono aggiornati ogni 8 ore. Può essere imposto da un aggiornamento nel Portale aziendale, in **Impostazioni**.

-   **iOS**: i criteri vengono aggiornati una volta al giorno con un intervallo di tempo casuale. Può essere imposto anche aprendo il Portale aziendale, selezionando il dispositivo e facendo clic su **Sincronizza**.

-   **Android**: i criteri vengono aggiornati una volta al giorno con un intervallo di tempo casuale. Può essere imposto anche aprendo il Portale aziendale, selezionando il dispositivo e facendo clic su **Sincronizza**.

## Errori relativi a criteri di Microsoft Intune in policyplatform.log
Per i dispositivi Windows non MDM, gli errori dei criteri nel file policyplatform.log potrebbero derivare da impostazioni non predefinite nel Controllo dell'account utente di Windows sul dispositivo. Alcune impostazioni non predefinite del Controllo dell'account utente possono influire sulle installazioni client di Microsoft Intune e sull'esecuzione dei criteri.

### Per risolvere i problemi relativi al Controllo dell'account utente

1.  Ritirare il computer come descritto in [Retire devices from Microsoft Intune management](/intune/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune)..

2.  Attendere 20 minuti che il software client venga rimosso.

    > [!NOTE]
    > Non provare a rimuovere il client da Programmi e funzionalità.

3.  Nel menu Start digitare **Controllo account utente** per aprire le impostazioni di Controllo dell'account utente.

4.  Spostare il dispositivo di scorrimento di notifica sull'impostazione predefinita.

## Errore 0x87D1FDE8 per il dispositivo KNOX
**Problema**: dopo la creazione e la distribuzione di un profilo di posta elettronica di Exchange Active Sync per Samsung KNOX per vari dispositivi Android, viene restituito l'errore **0x87D1FDE8** o **correzione non riuscita** in Proprietà dispositivo &gt; scheda Criteri.

Verificare la configurazione del profilo EAS per Samsung KNOX e i criteri di origine. L'opzione di sincronizzazione Samsung Notes non è più supportata e non dovrebbe essere selezionata nel profilo. Assicurarsi che i dispositivi abbiano avuto un tempo sufficiente per elaborare i criteri, fino a 24 ore.

## Avviso: Il salvataggio delle regole di accesso in Exchange non è riuscito
**Problema**: viene visualizzato l'avviso **Il salvataggio delle regole di accesso in Exchange non è riuscito**  nella console di amministrazione.

Se sono stati creati criteri nell'area di lavoro Criteri di Exchange locale con la console di amministrazione ma si usa Office 365, le impostazioni dei criteri configurate non vengono applicate da Intune. Si noti l'origine dei criteri nell'avviso.  Nell'area di lavoro Criteri di Exchange locale eliminare le regole precedenti, in quanto si tratta di regole generali di Exchange in Intune per Exchange locale e non sono rilevanti per Office 365, quindi creare nuovi criteri per Office 365.

## ERRORE: Impossibile ottenere il valore dal computer, 0x80041013
Può verificarsi se l'ora nel sistema locale è fuori sincronia di 5 minuti o più. Se l'ora nel computer locale non è sincronizzata, le transazioni sicure avranno esito negativo perché i timestamp non saranno validi.

Per risolvere questo problema, allineare l'ora del sistema locale il più possibile all'ora o all'ora impostata nei controller di dominio sulla rete.

## Non è possibile modificare i criteri di sicurezza per vari dispositivi MDM
I dispositivi Windows Phone e Windows RT non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta dopo averli configurati. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8 che poi si tenta di ridurre a 4. I criteri più restrittivi sono già stati applicati al dispositivo.

A seconda della piattaforma del dispositivo, se si vogliono modificare i criteri a un valore meno sicuro può essere necessario reimpostare i criteri di sicurezza.
Ad esempio, in Windows RT, sul desktop scorrere verso destra per aprire la barra **Accessi** e fare clic su **Impostazioni** &gt; **Pannello di controllo**.  Selezionare l'applet **Account utente** .
Nella parte inferiore del menu di navigazione a sinistra è disponibile un collegamento **Reimposta criteri di sicurezza** . Selezionare tale collegamento e quindi fare clic sul pulsante **Reimposta criteri** .
È possibile che altri dispositivi MDM, ad esempio Android, Windows Phone 8.1 e versione successiva e iOS, debbano essere ritirati e registrati nuovamente al servizio per consentire all'utente di applicare criteri meno restrittivi.

## I dispositivi Android non impongono modifiche ai criteri di sicurezza senza l'accettazione dell'utente finale
Android MDM non consente al servizio di forzare le modifiche dei criteri iniziali sui dispositivi, diversamente da altre piattaforme. Questa condizione è dovuta a funzionalità di Android e non è correlata al servizio Intune. I dispositivi Android richiederanno all'utente finale, tramite la finestra di notifica, di modificare i criteri correlati (ad esempio password, crittografia e così via).  L'utente finale deve rispondere alla richiesta e, dopo l'accettazione, i criteri vengono applicati.

## Non è possibile creare criteri o registrare client se il nome della società contiene caratteri speciali
**Problema:** non è possibile creare criteri o registrare client.

**Risoluzione:** nell'[interfaccia di amministrazione di Office 365](https://portal.office.com/) rimuovere i caratteri speciali dal nome della società e salvare le informazioni aziendali.

### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


<!--HONumber=May16_HO1-->


