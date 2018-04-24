---
title: Creare criteri di conformità per i dispositivi iOS in Microsoft Intune- Azure | Microsoft Docs
description: Creare criteri di conformità per i dispositivi in Microsoft Intune per consentire ai dispositivi iOS di connettersi a un account di posta elettronica, controllare dispositivi jailbroken, verificare il sistema operativo minimo e massimo e impostare le restrizioni relative alle password, ad esempio la lunghezza e il periodo di inattività del dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 887f45cdc79aa5e45de3e8a1df5d12665d2ed8ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Aggiungere criteri di conformità per i dispositivi iOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità per i dispositivi iOS in Intune specificano le regole e le impostazioni che i dispositivi iOS devono soddisfare per essere conformi. Tramite i criteri di conformità del dispositivo con accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi possono essere creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e i prerequisiti da rispettare per creare criteri di conformità, vedere [Introduzione ai criteri di conformità](device-compliance-get-started.md).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

| **Impostazione di criteri** | **iOS 8.0 e versioni successive** |
| --- | --- |
| **Configurazione di PIN o password** | Corretto |
| **Crittografia dispositivo** | Corretto (impostando il PIN) |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione)
| **Profilo di posta elettronica** | In quarantena |
|**Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |
| **Attestazione dell'integrità di Windows** | Non applicabile |

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creare i criteri di conformità nel portale di Azure

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
4. Immettere un nome e una descrizione e scegliere la piattaforma a cui applicare questi criteri.
5. Scegliere **Impostazioni** per immettere le impostazioni **Posta elettronica**, **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, scegliere **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono disponibili nel riquadro **Conformità del dispositivo - Criteri**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i **gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.
2. Scegliere **Gruppi selezionati** per aprire il riquadro che consente di visualizzare i gruppi di sicurezza di Azure AD.  Se si sceglie **Salva** il criterio verrà distribuito agli utenti.

Il criterio è stato applicato agli utenti.  I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

<!---## Compliance policy settings--->

## <a name="email"></a>Posta elettronica

- **L'account di posta elettronica deve essere gestito da Intune**: se questa opzione è impostata su **Sì**, il dispositivo deve usare il profilo di posta elettronica distribuito al dispositivo stesso. Il dispositivo è considerato non conforme nelle seguenti situazioni:
  - Il profilo di posta elettronica viene distribuito a un gruppo di utenti diverso dal gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo con provisioning dell'utente, quindi non può gestirlo. Per garantire la conformità, l'utente deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.
- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune**: se è stata selezionata l'impostazione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per specificare il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere presente nel dispositivo.

Per dettagli sul profilo di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Dispositivi jailbroken**: se si abilita questa impostazione, i dispositivi jailbroken non sono conformi.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: scegliere il livello di minaccia massimo oltre il quale i dispositivi vengono contrassegnati come non conformi. Ad esempio, se si imposta il livello di minaccia su **Medio**, i dispositivi con un livello medio, basso o protetto sono conformi. I dispositivi con un livello di minaccia alto non sono conformi.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene quindi richiesto di contattare l'amministratore IT. Finché la regola non viene modificata in modo da consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

> [!NOTE]
> Dopo l'applicazione di criteri di conformità o di configurazione a un dispositivo iOS, agli utenti viene richiesto ogni 15 minuti di impostare un passcode. Tale richiesta viene visualizzata finché non viene impostato un passcode.

- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per consentire a un utente di immettere una password per poter accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.
- **Password semplici**: impostare questa opzione su **Sì** per consentire la creazione di password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Tipo di password richiesto**: specificare se è necessario creare una password di tipo **Alfanumerico** o **Numerico**.
- **Numero di caratteri non alfanumerici nella password**: immettere il numero minimo di simboli o caratteri speciali (&, #, %, ! e così via), che è necessario includere nella password.

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
