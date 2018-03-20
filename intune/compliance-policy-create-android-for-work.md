---
title: "Creare criteri di conformità per Android for Work"
titleSuffix: Microsoft Intune
description: "Creare criteri di conformità per i dispositivi Android for Work in Microsoft Intune in modo da poter specificare i requisiti che un dispositivo deve soddisfare per essere conforme."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ca31d4c83ccc6b786933080b96f66953cf1a108
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Come creare i criteri di conformità per i dispositivi Android for Work in Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I criteri di conformità di un dispositivo Android for Work in Intune specificano le regole e le impostazioni che i dispositivi Android for Work devono soddisfare per essere considerati conformi. È possibile usare questi criteri con accesso condizionale per consentire o bloccare l'accesso alle risorse aziendali, oltre che ottenere report per dispositivi e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi vengono creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e i prerequisiti che è necessario soddisfare prima di creare i criteri di conformità, vedere [Introduzione ai criteri conformità](device-compliance-get-started.md).

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

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creare i criteri di conformità nel portale di Azure

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
1. Dal riquadro **Intune** scegliere **Conformità del dispositivo**. In **Gestisci** scegliere **Criteri** e quindi **Crea criterio**.
2. Digitare un nome e una descrizione, quindi scegliere la piattaforma a cui si desidera applicare questi criteri.
3. Scegliere **Impostazioni Configura** per specificare le impostazioni **Sicurezza del sistema**, **Integrità del dispositivo** e **Proprietà dispositivo**. Al termine, scegliere **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono disponibili nel riquadro **Conformità del dispositivo - Criteri**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il riquadro da cui è possibile selezionare i **gruppi di sicurezza di Azure Active Directory** e assegnarli ai criteri.
2. Scegliere **Gruppi selezionati** per aprire il riquadro che consente di visualizzare i gruppi di sicurezza di Azure AD.  Se si sceglie **Salva** il criterio verrà distribuito agli utenti.

Il criterio è stato applicato agli utenti.  I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri per la password.
- **Qualità password**: questa impostazione rileva se i requisiti di password specificati sono configurati nel dispositivo. Abilitare questa impostazione per richiedere agli utenti la configurazione di determinati requisiti di password per i dispositivi Android. È possibile scegliere tra:
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Alfanumerico con simboli**
- **Minuti di inattività prima che venga richiesta la password**: specificare il tempo di inattività prima che l'utente debba immettere nuovamente la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, l&#39;utente dovrà crearne una nuova.
- **Ricorda cronologia password**: usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.
- **Impedisci riutilizzo delle password precedenti**: se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile usare di nuovo.
- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**: usare questa impostazione con l'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.


### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sul dispositivo mobile**: non è necessario configurare questa impostazione poiché i dispositivi Android for Work applicano la crittografia.


## <a name="device-health-and-security-settings"></a>Impostazioni di integrità e sicurezza dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted**: se si abilita questa impostazione, i dispositivi jailbroken vengono considerati non conformi.
- **Richiedi che i dispositivi impediscano l'installazione di app da origini sconosciute**: non è necessario configurare questa impostazione poiché i dispositivi Android for Work impediscono sempre l'installazione da origini sconosciute.
- **Richiedi la disabilitazione del debug USB**: non è necessario configurare questa impostazione poiché il debug USB è già disabilitato nei dispositivi Android for Work.
- **Livello minimo di patch di protezione per Android**: usare questa impostazione per specificare il livello minimo di patch per Android. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere specificata nel formato: AAAA-MM-GG.
- **Richiedi l'abilitazione della protezione dalle minacce per il dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Selezionare il livello di minaccia massimo consentito tra uno dei seguenti:
  - **Nessuno (protetto)**: questo è il livello più sicuro e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sonio di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato non conforme.
  - **Alta**: questo è il livello meno sicuro. L'opzione consente praticamente tutti i livelli di minaccia e può essere utile se si usa la soluzione soltanto per la creazione di report.

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
