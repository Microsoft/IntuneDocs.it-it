---
title: Creare criteri di conformità per i dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Creare o configurare i criteri di conformità per i dispositivi Android in Microsoft Intune. Scegliere di consentire i dispositivi jailbroken, impostare il livello di minaccia accettabile, verificare la presenza di Google Play, immettere la versione minima e massima del sistema operativo, scegliere i requisiti delle password e consentire il sideload delle applicazioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2277da45ad1404269571f36dec0c16443409b39f
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744704"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Aggiungere i criteri di conformità per i dispositivi Android in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità di un dispositivo Android in Intune specificano le regole e le impostazioni che i dispositivi Android devono soddisfare per essere considerati conformi. Questi criteri con accesso condizionale possono essere usati per consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi vengono creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

--------------------

|**Impostazione di criteri**| **Android 4.0 e versioni successive, Samsung Knox Standard 4.0 e versioni successive** |
| --- | ----|
| **Configurazione di PIN o password** |  In quarantena |
| **Crittografia dispositivo** | In quarantena |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione) |
| **Profilo di posta elettronica** | Non applicabile |
| **Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** |   In quarantena |
| **Attestazione dell'integrità di Windows** | Non applicabile |

--------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Per **Piattaforma**, selezionare **Android**. Scegliere **Impostazioni Configura** e immettere le impostazioni **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, fare clic su **OK** e su **Crea**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Dispositivi rooted**: se si abilita questa impostazione, i dispositivi jailbroken vengono considerati non conformi.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Scegliere il livello di minaccia massimo consentito:
  - **Protetto**: questa opzione è la più sicura, perché il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce esistenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura e consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
- **Google Play Services è configurato**: richiede che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati.
- **Provider di sicurezza aggiornato**: richiede un provider di sicurezza aggiornato che può proteggere un dispositivo dalle vulnerabilità note.
- **Analisi delle minacce nelle app**: richiede l'abilitazione della funzionalità **Verifica app** Android.

  > [!NOTE]
  > Nella piattaforma Android legacy, questa funzionalità è un'impostazione di conformità. Intune consente solo di verificare se questa impostazione è abilitata a livello di dispositivo. Nei dispositivi con profili di lavoro (Android for Work), questa impostazione è disponibile come impostazione dei criteri di configurazione. Ciò consente agli amministratori di abilitare l'impostazione per un dispositivo.

  Se l'organizzazione usa i profili di lavoro Android, è possibile abilitare **Analisi delle minacce nelle app** per i dispositivi registrati. Stabilire un profilo del dispositivo e richiedere l'impostazione di sicurezza del sistema. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Intune](device-restrictions-android-for-work.md).

- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato**
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata per poter consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password dell'utente.
- **Tipo di password richiesto**: scegliere se una password deve avere solo caratteri numerici oppure una combinazione di numeri e altri caratteri. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti (ad esempio, "1111" o "1234") non sono consentiti.
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, l'utente deve crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password recenti che non è possibile riutilizzare. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo** (Android 4.0 e versioni successive o KNOX 4.0 e versioni successive): scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi. I dispositivi vengono crittografati se si sceglie l'impostazione **Richiedi una password per sbloccare i dispositivi mobili**.

### <a name="device-security"></a>Sicurezza del dispositivo

- **Blocca app da origini sconosciute**: scegliere di bloccare i dispositivi con le origini abilitate in "Sicurezza > Unknown Sources (Origini sconosciute)" (Android 4.0 - Android 7.x. Non supportato da Android 8.0 e versioni successive). Per trasferire localmente le app, devono essere consentite le origini sconosciute. Se non si trasferiscono localmente le app Android, abilitare questi criteri di conformità.

  > [!IMPORTANT]
  > Le applicazioni trasferite localmente richiedono l'abilitazione dell'impostazione **Blocca app da origini sconosciute**. Imporre questo criterio di conformità solo se non si esegue il sideload di app Android nei dispositivi.

- **Integrità del runtime dell'app Portale aziendale**: consente di verificare che nell'app Portale aziendale sia stato installato l'ambiente di runtime predefinito, che l'app sia firmata correttamente, non sia in modalità debug e sia stata installata da un'origine nota.
- **Blocca il debug USB nel dispositivo** (Android 4.2 o versione successiva): scegliere di impedire ai dispositivi di usare la funzionalità di debug USB.
- **Livello minimo di patch di protezione** (Android 6.0 o versione successiva): selezionare il livello di patch di sicurezza meno recente consentito per un dispositivo. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere immessa nel formato `YYYY-MM-DD`.

## <a name="locations"></a>Percorsi

Nei criteri eseguire la scelta da percorsi esistenti. Se non si ha ancora una posizione, vedere l'articolo che spiega come [usare i percorsi (isolamento rete) in Intune](use-network-locations.md) per conoscere alcune linee guida.

1. Scegliere **Seleziona percorsi**.
2. Selezionare il percorso nell'elenco e scegliere **Seleziona**.
3. **Salvare** il criterio.
4. Selezionare **Azioni per la mancata conformità**. L'azione predefinita contrassegna immediatamente il dispositivo come non conforme. Questa azione viene applicata quando si seleziona almeno un percorso e se il dispositivo non è connesso ai percorsi selezionati.

  È possibile modificare questa azione per aggiornare la pianificazione quando il dispositivo è contrassegnato come non conforme, ad esempio dopo un giorno. È anche possibile configurare una seconda azione che invia un messaggio di posta elettronica all'utente quando il dispositivo non è più compatibile con i percorsi.

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)