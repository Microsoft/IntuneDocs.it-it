---
title: Creare criteri di conformità per i dispositivi iOS in Microsoft Intune- Azure | Microsoft Docs
description: Creare o configurare criteri di conformità per i dispositivi in Microsoft Intune per consentire ai dispositivi iOS di connettersi a un account di posta elettronica, controllare dispositivi jailbroken, verificare il sistema operativo minimo e massimo e impostare le restrizioni relative alle password, ad esempio la lunghezza e il periodo di inattività del dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ee08c77fe085ad0f238d63481dd682ea15aa5ce
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313086"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Aggiungere criteri di conformità per i dispositivi iOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità per i dispositivi iOS in Intune specificano le regole e le impostazioni che i dispositivi iOS devono soddisfare per essere conformi. Tramite i criteri di conformità del dispositivo con accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi possono essere creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

---------------------------

| **Impostazione di criteri** | **iOS 8.0 e versioni successive** |
| --- | --- |
| **Configurazione di PIN o password** | Corretto |
| **Crittografia dispositivo** | Corretto (impostando il PIN) |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione)
| **Profilo di posta elettronica** | In quarantena |
|**Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |
| **Attestazione dell'integrità di Windows** | Non applicabile |

---------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Per **Piattaforma**, selezionare **iOS**. Scegliere **Impostazioni Configura** e immettere le impostazioni **Posta elettronica**, **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, fare clic su **OK** e su **Crea**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>Posta elettronica

- **Rendi obbligatorio un profilo di posta elettronica gestito nei dispositivi mobili**: se si imposta questa opzione su Rendi obbligatorio, i dispositivi che non hanno un profilo di posta elettronica gestito da Intune non sono considerati conformi. Un dispositivo potrebbe non avere un profilo di posta elettronica gestito quando non viene specificato correttamente come destinazione oppure se l'utente ha configurato manualmente l'account di posta elettronica nel dispositivo.

  Il dispositivo è considerato non conforme nelle seguenti situazioni:
  - Il profilo di posta elettronica viene distribuito a un gruppo di utenti diverso dal gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo con provisioning dell'utente, quindi non può gestirlo. Per garantire la conformità, l'utente deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.

- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune**: se è stata selezionata l'impostazione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per specificare il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere presente nel dispositivo.

Per dettagli sul profilo di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Dispositivi jailbroken**: se si abilita questa impostazione, i dispositivi jailbroken non sono conformi.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo** (iOS 8.0 e versioni successive): scegliere il livello di minaccia massimo oltre il quale i dispositivi vengono contrassegnati come non conformi. I dispositivi che superano questo livello di minaccia vengono contrassegnati come non conformi:
  - **Protetto**: questa opzione è la più sicura, perché il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce esistenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura e consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene quindi richiesto di contattare l'amministratore IT. Finché la regola non viene modificata in modo da consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

> [!NOTE]
> Dopo l'applicazione di criteri di conformità o di configurazione a un dispositivo iOS, agli utenti viene richiesto ogni 15 minuti di impostare un passcode. Tale richiesta viene visualizzata finché non viene impostato un passcode.

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Tipo di password richiesto**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).
- **Numero di caratteri non alfanumerici nella password**: immettere il numero minimo di simboli o caratteri speciali (&, #, %, ! e così via), che è necessario includere nella password.

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

### <a name="restricted-applications"></a>Applicazioni con restrizioni 
È possibile creare restrizioni per le app aggiungendo i relativi ID bundle ai criteri. Quindi, se in un dispositivo è installata l'app, il dispositivo verrà contrassegnato come non conforme. 
- **Nome app**: immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle. 
- **ID bundle dell'app**: immettere l'identificatore univoco del bundle assegnato dal provider dell'app. Per reperire l'ID bundle, vedere le [indicazioni su come trovare l'ID bundle per un'app iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).  

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)