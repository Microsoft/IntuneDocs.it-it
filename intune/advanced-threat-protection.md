---
title: Usare Microsoft Defender ATP in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su come abilitare Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) in uno scenario end-to-end che include l'attivazione di Microsoft Defender ATP in Intune e in Microsoft Defender Security Center, l'onboarding dei dispositivi con un profilo di configurazione di Microsoft Defender ATP, la creazione di criteri di conformità dei dispositivi Intune, la creazione di un criterio di accesso condizionale di Azure e il monitoraggio della conformità dei dispositivi.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 069658bdd231be96d7f9fbe23de1b4e38fdc5a9e
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885155"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Applicare la conformità per Microsoft Defender ATP con l'accesso condizionale in Intune  

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) e Microsoft Intune interagiscono tra loro per impedire violazioni della sicurezza e limitare l'impatto delle violazioni all'interno di un'organizzazione.

Questa funzionalità si applica a: Dispositivi Windows 10

Supponiamo ad esempio che qualcuno invii a un utente dell'organizzazione un allegato di Word con codice dannoso incorporato. L'utente apre l'allegato e abilita il contenuto. Viene così avviato un attacco con privilegi elevati, che assegna a un utente malintenzionato che opera da un computer remoto diritti di amministratore sul dispositivo della vittima. L'utente malintenzionato accede quindi in remoto agli altri dispositivi dell'utente.

Questa violazione della sicurezza può avere ripercussioni sull'intera organizzazione.

Microsoft Defender ATP può risolvere gli eventi legati alla sicurezza come questo scenario. Microsoft Defender Security Center segnala i dispositivi come "ad alto rischio" e include un report dettagliato delle attività sospette. In questo esempio Microsoft Defender ATP rileva che il dispositivo ha eseguito codice anomalo, ha sperimentato un'elevazione dei privilegi per un processo, ha inserito codice dannoso e ha eseguito un comando sospetto da shell remota. Microsoft Defender ATP offre quindi alcune opzioni per ridurre la minaccia.

Tramite Intune è possibile creare criteri di conformità che determinano un livello di rischio accettabile. Se un dispositivo supera questo livello, diventa non conforme. Quando a questi criteri si aggiunge l'accesso condizionale di Azure Active Directory (AD), all'utente viene impedito l'accesso alle risorse aziendali.

Questo articolo illustra come:

- Abilitare Intune in Microsoft Defender Security Center e abilitare Microsoft Defender ATP in Intune. Queste attività creano una connessione da servizio a servizio fra Intune e Microsoft Defender ATP. Questa connessione consente a Microsoft Defender ATP di scrivere il livello di rischio del computer per i dispositivi Intune.
- Creare i criteri di conformità in Intune.
- Abilitare l'accesso condizionale in Azure Active Directory (AD) sui dispositivi in base al relativo livello di minaccia.

## <a name="prerequisites"></a>Prerequisiti

Per usare Microsoft Defender ATP con Intune, verificare che gli elementi seguenti siano configurati e pronti per l'uso:

- Tenant con licenza per Enterprise Mobility + Security E3 e Windows E5 (o Microsoft 365 Enterprise E5)
- Ambiente Microsoft Intune, con dispositivi Windows 10 [gestiti da Intune](windows-enroll.md) che siano anche aggiunti ad Azure AD
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) e accesso a Microsoft Defender Security Center (portale ATP)

## <a name="enable-microsoft-defender-atp-in-intune"></a>Abilitare Microsoft Defender ATP in Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Microsoft Defender ATP** e quindi, sotto a *Impostazioni del connettore*, selezionare **Aprire Microsoft Defender Security Center**.

    ![Selezionare per aprire Microsoft Defender Security Center](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. In **Microsoft Defender Security Center**:
    1. Selezionare **Settings** (Impostazioni)  > **Advanced features** (Funzionalità avanzate).
    2. Per **Microsoft Intune connection** (Connessione Microsoft Intune) selezionare **On** (Attivata):

        ![Abilitare la connessione a Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Selezionare **Save preferences** (Salva preferenze).

4. Tornare a Intune, **Conformità del dispositivo** > **Microsoft Defender ATP**. Impostare **Connetti i dispositivi Windows con versione 10.0.15063 e successiva a Microsoft Defender ATP** su **Attivato**.
5. Selezionare **Salva**.

Questa procedura viene in genere eseguita una volta sola. Quindi, se Microsoft Defender ATP è già abilitato nella risorsa di Intune, non è necessario ripeterla.

## <a name="onboard-devices-using-a-configuration-profile"></a>Eseguire l'onboarding dei dispositivi tramite un profilo di configurazione

Quando un utente finale si registra in Intune, è possibile eseguire il push di diverse impostazioni nel dispositivo usando un profilo di configurazione. Questo vale anche per Microsoft Defender ATP.

Microsoft Defender ATP include un pacchetto di configurazione dell'onboarding che comunica con i [servizi Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) per analizzare i file, rilevare le minacce e segnalare il rischio a Microsoft Defender ATP.

Quando si esegue l'onboarding, Intune ottiene un pacchetto di configurazione generato automaticamente da Microsoft Defender ATP. Intune esegue il push del pacchetto di configurazione nel dispositivo quando invia il profilo di configurazione al dispositivo, che consente a Microsoft Defender ATP di monitorare il dispositivo per individuare le minacce.

Una volta eseguito l'onboarding di un dispositivo con il pacchetto di configurazione, non è necessario ripetere l'operazione. È possibile eseguire l'onboarding dei dispositivi anche usando un [criterio di gruppo o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-configuration-profile"></a>Creare il profilo di configurazione

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **nome** e una **descrizione**.
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. In **Tipo di profilo** selezionare **Microsoft Defender ATP (Windows 10 Desktop)** .
6. Configurare le impostazioni:

    - **Tipo del pacchetto di configurazione client di Microsoft Defender ATP**: selezionare **Onboarding** per aggiungere il pacchetto di configurazione al profilo. Selezionare **Offboarding** per rimuovere il pacchetto di configurazione dal profilo.
  
    > [!NOTE]  
    > Se è stata stabilita correttamente una connessione a Microsoft Defender ATP, Intune esegue automaticamente l'**onboarding** del profilo di configurazione e l'impostazione **Tipo del pacchetto di configurazione client di Microsoft Defender ATP** non sarà disponibile.
  
    - **Condivisione di esempi per tutti i file**: **Abilita** consente di raccogliere gli esempi e di condividerli con Microsoft Defender ATP. Ad esempio, se viene rilevato un file sospetto, è possibile inviarlo a Microsoft Defender ATP per un'analisi approfondita. **Non configurato** non condivide alcun esempio con Microsoft Defender ATP.
    - **Accelera la frequenza di creazione di report di telemetria**: **abilitare** questa impostazione per i dispositivi ad alto rischio, in modo che i dati di telemetria vengano segnalati più frequentemente al servizio Microsoft Defender ATP.

    Per informazioni più dettagliate su queste impostazioni di Microsoft Defender ATP, vedere [Eseguire l'onboarding di computer Windows 10 tramite System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm).

7. Scegliere **OK** e **Crea** per salvare le modifiche e creare il profilo.

## <a name="create-the-compliance-policy"></a>Creare i criteri di conformità
I criteri di conformità determinano un livello di rischio accettabile per un dispositivo.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
3. Immettere un **nome** e una **descrizione**.
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. Nelle impostazioni di **Microsoft Defender ATP** impostare **Richiedi che il dispositivo si trovi al massimo al punteggio di rischio del computer** sul livello preferito. Le classificazioni dei livelli delle minacce vengono [determinate da Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Cancella**: questo livello è il più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme. Per gli utenti di Microsoft Defender ATP il valore è *Sicuro*.
   - **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. I dispositivi con un livello di minaccia medio o alto non sono conformi.
   - **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
   - **Alto**: questo livello è il meno sicuro e consente tutti i livelli di minaccia. Sono quindi considerati conformi i dispositivi con un livello di minaccia alto, medio o basso.

6. Scegliere **OK** e **Crea** per salvare le modifiche e creare i criteri.

## <a name="assign-the-policy"></a>Assegnare i criteri

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Criteri**> selezionare i criteri di conformità di Microsoft Defender ATP.
3. Selezionare **Assegnazioni**.
4. Includere o escludere i gruppi di Azure AD per assegnare loro i criteri.
5. Per distribuire i criteri ai gruppi, scegliere **Salva**. I dispositivi degli utenti a cui sono destinati i criteri vengono valutati per la conformità.

## <a name="create-a-conditional-access-policy"></a>Creare criteri di accesso condizionale
I criteri di accesso condizionale bloccano l'accesso alle risorse *se* il dispositivo non è conforme. Se quindi un dispositivo supera il livello di minaccia, è possibile bloccare l'accesso alle risorse aziendali, come SharePoint o Exchange Online.  

> [!TIP]  
> L'accesso condizionale è una tecnologia di Azure Active Directory (Azure AD). Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo accessibile da *Azure AD*.  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionare **Accesso condizionale** > **Nuovi criteri**.
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
A questo punto occorre monitorare lo stato dei dispositivi in cui sono applicati i criteri di conformità di Microsoft Defender ATP.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Conformità dei criteri**.
3. Trovare il proprio criterio di Microsoft Defender ATP nell'elenco e verificare quali dispositivi sono conformi o non conformi.

## <a name="more-good-stuff"></a>Altre informazioni utili
[Accesso condizionale di Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Dashboard dei rischi di Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md)  
[Accesso condizionale in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)