---
title: Aggiornare Office 365 usando modelli amministrativi in Microsoft Intune - Azure | Microsoft Docs
description: Usare modelli amministrativi in Microsoft Intune per aggiornare le app di Office 365 alla versione più recente e scegliere la frequenza con cui Office controlla la disponibilità degli aggiornamenti. Vedere le chiavi del Registro di sistema del dispositivo aggiornate quando viene applicato un criterio di Intune a Office Update.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ebbc22c5452c99439d34813509b5652daef1f0
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548096"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Usare le impostazioni Canale di aggiornamento e Versione di destinazione per aggiornare Office 365 con i modelli amministrativi di Microsoft Intune

In Intune è possibile usare [modelli di Windows 10 per configurare le impostazioni di criteri di gruppo](administrative-templates-windows.md). Questo articolo illustra come aggiornare Office 365 usando un modello amministrativo in Intune. L'articolo include anche materiale sussidiario per verificare l'applicazione corretta dei criteri. Queste informazioni sono utili anche per la risoluzione dei problemi.

In questo scenario viene creato un modello amministrativo in Intune che aggiorna Office 365 nei dispositivi.

Per altre informazioni sui modelli amministrativi, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di criteri di gruppo](administrative-templates-windows.md).

Si applica a:

- Windows 10 e versioni successive
- Office 365

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi di [abilitare Aggiornamenti automatici di Office365 ProPlus](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) per le app di Office. È possibile eseguire questa operazione usando i criteri di gruppo o il modello ADMX di Office 2016 di Intune:

![Nel modello amministrativo di Intune selezionare Abilita aggiornamenti automatici per Office](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Impostare il canale di aggiornamento nel modello amministrativo di Intune

1. Nel [modello amministrativo di Intune](administrative-templates-windows.md#create-a-template) passare all'impostazione **Canale di aggiornamento** e immettere il canale desiderato. Ad esempio, scegliere `Semi-Annual Channel`:

    ![Nel modello amministrativo di Intune impostare Canale di aggiornamento per Office](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > È consigliabile eseguire l'aggiornamento con maggiore frequenza. L'aggiornamento semestrale è usato solo come esempio.

2. Assicurarsi di [assegnare i criteri](device-profile-assign.md) ai dispositivi Windows 10. Per testare i criteri, è anche possibile sincronizzarli:

    - [Sincronizzare i criteri in Intune](../remote-actions/device-sync.md)
    - [Sincronizzare manualmente i criteri nel dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Controllare le chiavi del Registro di sistema di Intune

Dopo aver assegnato i criteri e dopo la sincronizzazione del dispositivo, è possibile verificare l'applicazione dei criteri:

1. Nel dispositivo aprire l'app **Editor del Registro di sistema**.
2. Passare al percorso dei criteri di Intune: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > `<Provider ID>` nella chiave del Registro di sistema viene modificato. Per trovare l'ID provider per il dispositivo, aprire l'app **Editor del Registro di sistema** e passare a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. Viene visualizzato l'ID provider.

    Quando i criteri vengono applicati, vengono visualizzate le chiavi del Registro di sistema seguenti:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    Esaminando l'esempio seguente è possibile notare che `L_UpdateBranch` ha un valore simile a `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`. Questo valore indica che è impostato su Canale semestrale:

    ![Esempio di chiave del Registro di sistema L_Updatebranch del modello amministrativo](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > In [Gestire Office 365 ProPlus con Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) è disponibile un elenco dei valori con il relativo significato. I valori del registro sono basati sul canale di distribuzione selezionato:
    >
    >- Canale mensile                - value="Current"
    >- Canale mensile (mirato)     - value="Current"
    >- Canale semestrale            - value="Current"
    >- Canale semestrale (mirato) - value="FirstReleaseDeferred"
    >- Circuito Insider veloce                   - value="InsiderFast"

A questo punto, i criteri di Intune vengono applicati correttamente al dispositivo.

## <a name="check-the-office-registry-keys"></a>Controllare le chiavi del Registro di sistema di Office

1. Nel dispositivo aprire l'app **Editor del Registro di sistema**.
2. Passare al percorso dei criteri di Office: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Vengono visualizzate le chiavi del Registro di sistema seguenti:

    - `UpdateChannel`: chiave dinamica che cambia, a seconda delle impostazioni configurate.
    - `CDNBaseUrl`: impostato quando Office 365 viene installato nel dispositivo.

3. Osservare il valore `UpdateChannel`. Il valore indica la frequenza di aggiornamento di Office. In [Gestire Office 365 ProPlus con Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) è disponibile un elenco dei valori con la relativa impostazione.

    Esaminando l'esempio seguente si noti che `UpdateChannel` è impostato su `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, ovvero **mensile**:

    ![Esempio di chiave del Registro di sistema Office UpdateChannel del modello amministrativo](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Questo esempio indica che i criteri non sono ancora applicati poiché l'impostazione è ancora **mensile** anziché **semestrale**.

Questa chiave del Registro di sistema viene aggiornata al momento dell'esecuzione di **Utilità di pianificazione** > **Aggiornamenti automatici di Office 2.0** o quando un utente accede al dispositivo. Per verificare, aprire l'attività **Aggiornamenti automatici di Office 2.0** > **Trigger**. A seconda dei trigger, l'aggiornamento della chiave del Registro di sistema `UpdateChannel` può richiedere un giorno o più.

## <a name="force-office-automatic-updates-to-run"></a>Forzare l'esecuzione degli aggiornamenti automatici di Office

Per testare i criteri, è possibile forzare le impostazioni dei criteri nel dispositivo. Per aggiornare il registro, eseguire i passaggi seguenti. Come sempre, prestare attenzione quando si aggiorna il registro.

1. Cancellare la chiave del Registro di sistema:

    1. Passare a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Fare doppio clic sulla chiave `UpdateDetectionLastRunTime`, eliminare i dati del valore > **OK**.

2. Eseguire l'attività degli aggiornamenti automatici di Office:

    1. Aprire l'app **Utilità di pianificazione** nel dispositivo.
    2. Espandere **Libreria Utilità di pianificazione** > **Microsoft** > **Office**.
    3. Selezionare **Aggiornamenti automatici di Office 2.0** > **Esegui**:

        ![Aprire l'Utilità di pianificazione ed eseguire gli aggiornamenti automatici di Office](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Attendere il completamento dell'attività, che può richiedere alcuni minuti.

3. Nell'app **Editor del Registro** passare a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Controllare il valore `UpdateChannel`.

    Dovrebbe essere aggiornato con il valore impostato nei criteri. In questo esempio il valore dovrebbe essere impostato su `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

A questo punto, il canale di aggiornamento di Office è stato modificato correttamente nel dispositivo. È possibile aprire un'app di Office 365 per un utente che riceve questo aggiornamento per verificare lo stato.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Forza la sincronizzazione di Office per aggiornare le informazioni dell'account  

Se si vuole eseguire altre operazioni, è possibile forzare l'aggiornamento alla versione più recente di Office. I passaggi seguenti devono essere eseguiti solo per conferma o se è necessario che i dispositivi ottengano rapidamente l'aggiornamento alla versione più recente dal canale. In caso contrario, consentire a Office di eseguire automaticamente l'aggiornamento.

### <a name="step-1-force-the-office-version-to-update"></a>Passaggio 1: Forzare l'aggiornamento della versione di Office

1. Verificare che la versione di Office supporti il canale di aggiornamento scelto. In [Cronologia degli aggiornamenti per Office 365 ProPlus](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) è disponibile un elenco dei numeri di build che supportano i diversi canali di aggiornamento.

2. Nel [modello amministrativo di Intune](administrative-templates-windows.md#create-a-template) passare all'impostazione **Versione di destinazione** e immettere la versione desiderata.

    L'impostazione **Versione di destinazione** è simile all'impostazione seguente:

    ![Nel modello amministrativo di Intune impostare Versione di destinazione per Office](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Assicurarsi di assegnare il criterio.
> - Se si modifica un criterio esistente, le modifiche verranno applicate a tutti gli utenti assegnati.
> - Se si sta testando questa funzionalità, è consigliabile creare un criterio di test e assegnare il criterio a un gruppo di utenti di test.

### <a name="step-2-check-the-office-version"></a>Passaggio 2: Controllare la versione di Office

Provare a usare questi passaggi per testare i criteri prima di distribuirli a tutti gli utenti.

1. Nell'app **Editor del Registro di sistema** passare a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. Osservare il valore `L_UpdateTargetVersion`. Dopo aver applicato i criteri, il valore viene impostato sulla versione specificata, ad esempio `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    A questo punto, i criteri di Intune vengono applicati correttamente al dispositivo.

3. È quindi possibile forzare l'aggiornamento di Office. Aprire un'app di Office, ad esempio Excel. Scegliere di eseguire ora l'aggiornamento (possibilmente nel menu **Account**).

    L'aggiornamento richiede diversi minuti. È possibile verificare che Office tenti di ottenere la versione specificata:

      1. Nel dispositivo passare a `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Aprire il file `VersionDescriptor.xml` e passare alla sezione `<Version>`. La versione disponibile deve corrispondere a quella specificata nei criteri di Intune, ad esempio:

          ![Controllare la sezione Version nel file XML descrittore di versione di Office](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. Dopo l'installazione dell'aggiornamento, l'app di Office dovrebbe visualizzare la nuova versione (ad esempio, nel menu **Account**)

## <a name="next-steps"></a>Passaggi successivi

[Aggiornare i valori del canale per i client Office 365](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[Panoramica del servizio di criteri del cloud di Office per Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Usare i modelli di Windows 10 per configurare le impostazioni di criteri di gruppo (modelli ADMX) in Microsoft Intune](administrative-templates-windows.md)
