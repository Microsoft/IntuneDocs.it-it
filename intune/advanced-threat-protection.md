---
title: Usare Windows Defender ATP in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su come abilitare Windows Defender Advanced Threat Protection (ATP) in uno scenario end-to-end che include l'attivazione di ATP in Intune e in Windows Defender Security Center (portale ATP), l'onboarding dei dispositivi con un profilo di configurazione ATP, la creazione di criteri di conformità dei dispositivi Intune, la creazione di un criterio di accesso condizionale di Azure e il monitoraggio della conformità dei dispositivi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99d848fb1efea2ea2d557ab8d4f19881705ec991
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744670"
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>Abilitare Windows Defender ATP con l'accesso condizionale in Intune

Windows Defender Advanced Threat Protection (ATP) e Microsoft Intune interagiscono tra loro per impedire violazioni della sicurezza e limitare l'impatto delle violazioni all'interno di un'organizzazione.

Questa funzionalità si applica ai dispositivi Windows 10.

Supponiamo ad esempio che qualcuno invii a un utente dell'organizzazione un allegato di Word con codice dannoso incorporato. L'utente apre l'allegato e abilita il contenuto. Viene così avviato un attacco con privilegi elevati, che assegna a un utente malintenzionato che opera da un computer remoto diritti di amministratore sul dispositivo della vittima. L'utente malintenzionato accede quindi in remoto agli altri dispositivi dell'utente.

Questa violazione della sicurezza può avere ripercussioni sull'intera organizzazione.

Windows Defender ATP può risolvere gli eventi legati alla sicurezza come questo scenario. Windows Defender Security Center (la console ATP) segnala i dispositivi come "ad alto rischio" e include un report dettagliato delle attività sospette. Nel nostro esempio Windows Defender ATP rileva che il dispositivo ha eseguito codice anomalo, ha sperimentato un'elevazione dei privilegi, ha inserito codice dannoso e ha eseguito un comando sospetto da shell remota. Windows Defender ATP offre quindi alcune opzioni per ridurre la minaccia.

Tramite Intune è possibile creare criteri di conformità che determinano un livello di rischio accettabile. Se un dispositivo supera questo livello, diventa non conforme. Quando a questi criteri si aggiunge l'accesso condizionale di Azure Active Directory (AD), all'utente viene impedito l'accesso alle risorse aziendali.

Questo articolo illustra come:

- Abilitare Intune in ATP e ATP in Intune. Queste attività creano una connessione da servizio a servizio fra Intune e Windows Defender ATP. Questa connessione consente a Windows Defender ATP di scrivere il livello di rischio del computer per i dispositivi Intune.
- Creare i criteri di conformità in Intune.
- Abilitare l'accesso condizionale in Azure Active Directory (AD) sui dispositivi in base al relativo livello di minaccia.

## <a name="prerequisites"></a>Prerequisiti

Per usare ATP con Intune, verificare che gli elementi seguenti siano configurati e pronti per l'uso:

- Tenant con licenza per Enterprise Mobility + Security E5 e Windows E5 (o Microsoft 365 Enterprise E5)
- Ambiente Microsoft Intune, con dispositivi Windows 10 [gestiti da Intune](windows-enroll.md) che siano anche aggiunti ad Azure AD
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) e accesso a Windows Defender Security Center (portale ATP)

## <a name="enable-windows-defender-atp-in-intune"></a>Abilitare Windows Defender ATP in Intune

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Conformità del dispositivo** > **Windows Defender ATP** > **Apri Windows Defender Security Center**.

    ![Selezionare per aprire Windows Defender Security Center](./media/atp-device-compliance-open-windows-defender.png)

4. In **Windows Defender Security Center**:
    1. Selezionare **Settings** (Impostazioni)  > **Advanced features** (Funzionalità avanzate).
    2. Per **Microsoft Intune connection** (Connessione Microsoft Intune) selezionare **On** (Attivata):

        ![Abilitare la connessione a Intune](./media/atp-security-center-intune-toggle.png)

    3. Selezionare **Save preferences** (Salva preferenze).

5. Tornare a Intune, **Conformità del dispositivo** > **Windows Defender ATP**. Impostare **Connetti i dispositivi Windows con versione 10.0.15063 e successiva a Windows Defender ATP** su **Attivato**.
6. Selezionare **Salva**.

Questa procedura viene in genere eseguita una volta sola. Se quindi ATP è già abilitato nella risorsa di Intune, non è necessario ripeterla.

## <a name="onboard-devices-using-a-configuration-profile"></a>Eseguire l'onboarding dei dispositivi tramite un profilo di configurazione

Windows Defender include un pacchetto di configurazione per l'onboarding che viene installato nei dispositivi. Una volta installato, il pacchetto comunica con i [servizi Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) per analizzare i file, rilevare le minacce e segnalare il rischio a Windows Defender ATP. Tramite Intune è possibile creare un profilo di configurazione che usa questo pacchetto di configurazione, quindi assegnare il profilo ai dispositivi di cui si sta eseguendo l'onboarding per la prima volta.

Una volta eseguito l'onboarding di un dispositivo con il pacchetto di configurazione, non è necessario ripetere l'operazione. In genere questa attività viene eseguita una volta sola.

È possibile eseguire l'onboarding dei dispositivi anche usando un [criterio di gruppo o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

Le procedure seguenti mostrano come eseguire l'onboarding tramite Intune.

#### <a name="download-configuration-package"></a>Scaricare il pacchetto di configurazione

1. In [Windows Defender Security Center](https://securitycenter.windows.com) selezionare **Settings** (Impostazioni)  > **Onboarding**.
2. Immettere le impostazioni seguenti:
  - **Sistema operativo**: Windows 10
  - **Onboard a machine** (Onboarding di un computer)  > **Deployment method** (Metodo di distribuzione): Gestione dispositivi mobili / Microsoft Intune
3. Selezionare **Download package** (Scarica pacchetto) e salvare il file **WindowsDefenderATPOnboardingPackage.zip**. Estrarre il file.

Questo file ZIP include **WindowsDefenderATP.onboarding**, che servirà nei passaggi successivi.

#### <a name="create-the-atp-configuration-profile"></a>Creare il profilo di configurazione ATP

Questo profilo usa il pacchetto di onboarding scaricato nella procedura precedente.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **nome** e una **descrizione**.
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. In **Tipo di profilo** selezionare **Windows Defender ATP (Windows 10 Desktop)**.
6. Configurare le impostazioni:

  - **Onboarding del pacchetto di configurazione**: individuare e selezionare il file **WindowsDefenderATP.onboarding** scaricato. Questo file abilita un'impostazione che consente ai dispositivi di inviare segnalazioni al servizio Windows Defender ATP.
  - **Condivisione di esempi per tutti i file**: consente di raccogliere gli esempi e di condividerli con Windows Defender ATP. Ad esempio, se viene rilevato un file sospetto, è possibile inviarlo a Windows Defender ATP per un'analisi approfondita.
  - **Accelera la frequenza di creazione di report di telemetria**: abilitare questa impostazione per i dispositivi ad alto rischio, in modo che la telemetra venga segnalata più frequentemente al servizio Windows Defender ATP.
  - **Offboarding del pacchetto di configurazione**: se si vuole rimuovere o eseguire l'offload del monitoraggio di Windows Defender ATP, è possibile scaricare un pacchetto di offload in [Windows Defender Security Center](https://securitycenter.windows.com) e aggiungerlo. In caso contrario, ignorare questa proprietà.

    Per informazioni più dettagliate su queste impostazioni di Windows Defender ATP, vedere [Onboard Windows 10 machines using System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) (Eseguire l'onboarding di computer Windows 10 tramite System Center Configuration Manager).

7. Scegliere **OK** e **Crea** per salvare le modifiche e creare il profilo.

## <a name="create-the-compliance-policy"></a>Creare i criteri di conformità
I criteri di conformità determinano un livello di rischio accettabile per un dispositivo.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
3. Immettere un **nome** e una **descrizione**.
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. Nelle impostazioni di **Windows Defender ATP** impostare **Richiedi che il dispositivo si trovi al massimo al punteggio di rischio del computer** sul livello preferito:

  - **Cancella**: questo livello è il più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.
  - **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. I dispositivi con un livello di minaccia medio o alto non sono conformi.
  - **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
  - **Alto**: questo livello è il meno sicuro e consente tutti i livelli di minaccia. Sono quindi considerati conformi i dispositivi con un livello di minaccia alto, medio o basso.

6. Scegliere **OK** e **Crea** per salvare le modifiche e creare i criteri.

## <a name="assign-the-policy"></a>Assegnare i criteri

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Conformità del dispositivo** > **Criteri**> selezionare i criteri di conformità di Windows Defender ATP.
3. Selezionare **Assegnazioni**.
4. Includere o escludere i gruppi di Azure AD per assegnare loro i criteri.
5. Per distribuire i criteri ai gruppi, scegliere **Salva**. I dispositivi degli utenti a cui sono destinati i criteri vengono valutati per la conformità.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Creare un criterio di accesso condizionale di Azure AD
Il criterio di accesso condizionale blocca l'accesso alle risorse *se* il dispositivo non è conforme. Se quindi un dispositivo supera il livello di minaccia, è possibile bloccare l'accesso alle risorse aziendali, come SharePoint o Exchange Online.

1. Nel [portale di Azure](https://portal.azure.com) aprire **Azure Active Directory** > **Accesso condizionale** > **Nuovo criterio**.
2. Immettere un **nome** per il criterio e selezionare **Utenti e gruppi**. Usare l'opzione Includi o Escludi per aggiungere i gruppi per il criterio e selezionare **Fatto**.
3. Selezionare **App cloud** e scegliere le app da proteggere. Ad esempio, scegliere **Seleziona le app** e quindi selezionare **Office 365 SharePoint Online**e **Office 365 Exchange Online**.

    Selezionare **Fatto** per salvare le modifiche.

4. Selezionare **Condizioni** > **App client** per applicare il criterio alle app e ai browser. Ad esempio, selezionare **Sì** e quindi abilitare **Browser** e **App per dispositivi mobili e client desktop**.

    Selezionare **Fatto** per salvare le modifiche.

5. Selezionare **Concedi** per applicare l'accesso condizionale basato sulla conformità del dispositivo. Ad esempio, selezionare **Concedi accesso** > **Richiedi che i dispositivi siano contrassegnati come conformi**.

    Scegliere **OK** per salvare le modifiche.

6. Selezionare **Abilita criterio** e quindi **Crea** per salvare le modifiche.

L'articolo [Che cos'è l'accesso condizionale?](conditional-access.md) offre altre informazioni utili.

## <a name="monitor-device-compliance"></a>Monitorare la conformità dei dispositivi
A questo punto occorre monitorare lo stato dei dispositivi in cui sono applicati i criteri di conformità di Windows Defender ATP.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Conformità del dispositivo** > **Conformità dei criteri**.
3. Trovare il proprio criterio di Windows Defender ATP nell'elenco e verificare quali dispositivi sono conformi o non conformi.

## <a name="more-good-stuff"></a>Altre informazioni utili
[Accesso condizionale di Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Dashboard dei rischi di Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md)  
[Accesso condizionale in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)