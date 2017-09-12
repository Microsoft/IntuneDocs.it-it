---
title: "Come creare un criterio di conformità per Android"
titleSuffix: Azure portal
description: "Informazioni sulle modalità di creazione dei criteri di conformità per i dispositivi Android.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 64e16233a9acb021c0a50b32f3eb750125eb0638
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune"></a>Come creare i criteri di conformità per i dispositivi Android in Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I criteri di conformità dei dispositivi vengono creati per ogni piattaforma dal portale di Intune in Azure. 

- Per altre informazioni sui criteri di conformità consultare l'argomento [What is a device compliance](device-compliance.md)(Che cos'è la conformità dei dispositivi).
- Per altre informazioni sui prerequisiti che è necessario soddisfare prima di creare i criteri di conformità, consultare l'argomento [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

## <a name="to-create-a-device-compliance-policy"></a>Per creare i criteri di conformità dei dispositivi

1. Dal pannello **Intune** scegliere **Imposta la conformità dei dispositivi**. In **Gestione** scegliere **Tutti i criteri di conformità del dispositivo** e quindi **Crea**.
2. Digitare un nome e una descrizione, quindi scegliere la piattaforma a cui si desidera applicare questi criteri.
3. Scegliere i **Requisiti per la conformità** per specificare le impostazioni **Sicurezza**, **Integrità del dispositivo** e **Proprietà del dispositivo**. Al termine, scegliere **OK**.

<!-- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.-->

## <a name="to-assign-user-groups"></a>Per assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono reperibili nel pannello **Criteri di conformità**.

1. Selezionare il criterio e scegliere **Assegnazione**. Si apre il pannello da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.
2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD. Qui è possibile trovare i gruppi di sicurezza in Azure Active Directory.  È possibile selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Seleziona**. Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

Il criterio è stato applicato agli utenti.  I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

<!---##  Compliance policy settings--->

## <a name="device-health-and-security-settings"></a>Impostazioni di integrità e sicurezza dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted**: se si abilita questa impostazione, i dispositivi jailbroken verranno valutati come non conformi.
- **Richiedi che i dispositivi impediscano l'installazione di app da origini sconosciute (Android 4.0 o versione successiva)**: per bloccare i dispositivi che hanno le opzioni **Sicurezza**>; **Origini sconosciute** abilitate sul dispositivo, abilitare questa impostazione e impostarla su **Sì**.

### <a name="important"></a>Importante

Le applicazioni di cui si esegue il sideload richiedono l'abilitazione dell'impostazione **Origini sconosciute**. Imporre questo criterio di conformità solo se non si esegue il sideload di app Android nei dispositivi.

- **Richiedi la disabilitazione del debug USB (Android 4.2 o versione successiva)**: questa impostazione indica se è necessario rilevare o meno l'abilitazione del debug USB nel dispositivo.
- **Richiedi l'abilitazione dell'opzione "Cerca minacce per la sicurezza nel dispositivo" nei dispositivi (Android 4.2-4.4)**: questa impostazione specifica che la funzionalità **Verifica app** è abilitata nel dispositivo.
- **Livello minimo di patch di protezione per Android (Android 6.0 o versione successiva)**: usare questa impostazione per specificare il livello minimo di patch per Android. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere specificata nel formato: AAAA-MM-GG.
- **Richiedi l'abilitazione della protezione dalle minacce per il dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Selezionare il livello di minaccia più alto consentito tra uno dei seguenti:
  - **Nessuno (protetto)**: questo è il livello più sicuro e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello per il dispositivo, questo sarà considerato come non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questo è il livello meno sicuro. Questa impostazione abilita tutti i livelli di rischio. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

Per altre informazioni dettagliate, vedere [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy).

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Lunghezza minima password**: specifica il numero minimo di cifre o caratteri per la password dell&#39;utente.
- **Qualità password:** questa impostazione rileva se i requisiti di password specificati sono configurati nel dispositivo. Abilitare questa impostazione per richiedere agli utenti di impostare determinati requisiti di password per i dispositivi Android. È possibile scegliere tra:
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Alfanumerico con simboli**
- **Minuti di inattività prima che venga richiesta la password**: specifica il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Ricorda cronologia password**: usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.
- **Impedisci riutilizzo delle password precedenti**: se l'opzione **Ricorda cronologia password** è selezionata, specifica il numero di password usate in precedenza che non è possibile usare di nuovo.
- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sul dispositivo mobile**: impostare questa opzione su **Sì** per richiedere che i dispositivi vengano crittografati per la connessione alle risorse. I dispositivi vengono crittografati se si sceglie l'impostazione **Richiedi una password per sbloccare i dispositivi mobili**.

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo per poter accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata per consentire la versione del sistema operativo, non è possibile usare il dispositivo per accedere alle risorse aziendali.

## <a name="how-non-compliant-settings-work-with-conditional-access-policies"></a>In che modo interagiscono le impostazioni di non conformità con i criteri di accesso condizionale?

La tabella seguente descrive il modo in cui vengono gestite le impostazioni di non conformità quando i criteri di conformità vengono usati insieme ai criteri di accesso condizionale.

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

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)+

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:+

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
