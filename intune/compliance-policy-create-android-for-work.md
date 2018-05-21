---
title: Creare criteri di conformità per Android for Work in Microsoft Intune - Azure | Microsoft Docs
description: Creare o configurare i criteri di conformità per i dispositivi Android for Work in Microsoft Intune. Scegliere di consentire i dispositivi jailbroken, impostare il livello di minaccia accettabile, verificare la presenza di Google Play, immettere la versione minima e massima del sistema operativo, scegliere i requisiti delle password e consentire il sideload delle applicazioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d438aa7416b1629af7ab2b899afa06720e2b49
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Aggiungere i criteri di conformità per i dispositivi Android for Work in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità di un dispositivo Android for Work in Intune specificano le regole e le impostazioni che questi dispositivi devono soddisfare per essere considerati conformi. Questi criteri con accesso condizionale possono essere usati per consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi vengono creati per le piattaforme nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

--------------------------

|**impostazione di criteri**| **Android for Work** |
| --- | --- |
| **Configurazione di PIN o password** |  In quarantena |
| **Crittografia dispositivo** |  In quarantena |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione) |
| **Profilo di posta elettronica** | Non applicabile |
| **Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |
| **Attestazione dell'integrità di Windows** |Non applicabile |

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)+

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Se all'utente si applica un criterio di accesso condizionale, il dispositivo viene bloccato.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Per **Piattaforma** selezionare **Android for Work**. Scegliere **Impostazioni Configura** e immettere le impostazioni **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, fare clic su **OK** e su **Crea**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **Dispositivi rooted**: se si abilita questa impostazione, i dispositivi jailbroken vengono considerati non conformi.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Scegliere il livello di minaccia massimo consentito:
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
- **Google Play Services è configurato**: richiede che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati.
- **Provider di sicurezza aggiornato**: richiede un provider di sicurezza aggiornato che può proteggere un dispositivo dalle vulnerabilità note.
- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato**
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

#### <a name="threat-scan-on-apps"></a>Analisi delle minacce nelle app

Nei dispositivi con profili di lavoro (Android for Work) l'impostazione **Analisi delle minacce nelle app** è disponibile come impostazione dei criteri di configurazione. Gli amministratori possono abilitare l'impostazione per un dispositivo.

Se l'organizzazione usa i profili di lavoro Android, è possibile abilitare **Analisi delle minacce nelle app** per i dispositivi registrati. Stabilire un profilo del dispositivo e richiedere l'impostazione di sicurezza del sistema. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Intune](device-restrictions-android-for-work.md).

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella nella regola, l'accesso alle risorse aziendali viene bloccato e all'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata per poter consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password dell'utente.
- **Tipo di password richiesto**: scegliere se una password deve contenere solo caratteri numerici oppure una combinazione di numeri e altri caratteri. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Almeno numerico**
  - **Complessa numerica**
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password recenti che non è possibile riutilizzare. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sul dispositivo mobile**: non è necessario configurare questa impostazione poiché i dispositivi Android for Work applicano la crittografia.

### <a name="device-security"></a>Sicurezza del dispositivo

- **Blocca app da origini sconosciute**: non è necessario configurare questa impostazione perché i dispositivi Android for Work limitano sempre l'installazione da origini sconosciute.
- **Integrità del runtime dell'app Portale aziendale**: consente di verificare che nell'app Portale aziendale sia stato installato l'ambiente di runtime predefinito, che l'app sia firmata correttamente, non sia in modalità debug e sia stata installata da un'origine nota.
- **Blocca il debug USB nel dispositivo**: non è necessario configurare questa impostazione perché l'esecuzione del debug USB è già stata disabilitata nei dispositivi Android for Work.
- **Livello minimo di patch di protezione**: selezionare il livello di patch di sicurezza meno recente consentito per un dispositivo. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere immessa nel formato `YYYY-MM-DD`.

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)
