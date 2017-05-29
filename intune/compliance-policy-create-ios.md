---
title: "Come creare un criterio di conformità per iOS"
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle modalità di creazione dei criteri di conformità per i dispositivi iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 423c6058c8a2803e62a90f309f4b9c9ad62f9ede
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune-azure-preview"></a>Come creare i criteri di conformità per i dispositivi iOS nell'anteprima di Intune in Azure


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

I criteri di conformità vengono creati per ogni piattaforma.  È possibile creare i criteri di conformità nel portale di Azure. Per altre informazioni sui criteri di conformità consultare l'argomento [What is a device compliance](device-compliance.md)(Che cos'è la conformità dei dispositivi). Per altre informazioni sui prerequisiti che è necessario soddisfare prima di creare i criteri di conformità, consultare l'argomento [Get started with device compliance](device-compliance-get-started.md) (Introduzione alla conformità dei dispositivi).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

-------------------------------


| **Impostazione di criteri** | **iOS 8.0 e versioni successive** |
| --- | --- |
| **Configurazione di PIN o password** | Corretto |   
| **Crittografia dispositivo** | Corretto (impostando il PIN) |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione)
| **Profilo di posta elettronica** | In quarantena |
|**Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |  
| **Attestazione dell'integrità di Windows** | Non applicabile |  
----------------------------


**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creare i criteri di conformità nel portale di Azure

1. Dal pannello **Intune** scegliere **Imposta la conformità dei dispositivi**. In **Gestisci** scegliere **All device compliance policies** (Tutti i criteri di conformità dei dispositivi) e scegliere **Crea**.
2. Digitare un nome e una descrizione, quindi scegliere la piattaforma a cui si desidera applicare questi criteri.
3. Scegliere i **Requisiti per la conformità** per specificarvi le impostazioni **Sicurezza**, **Integrità del dispositivo** e **Proprietà del dispositivo** e, al termine, scegliere **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono reperibili nel pannello **Criteri di conformità**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.
2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD.  Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

Il criterio è stato applicato agli utenti.  I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per consentire a un utente di immettere una password per poter accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.
- **Consenti password semplici**: impostare questa opzione su **Sì** per consentire all'utente di creare una password semplice come **1234** o **1111**.
- **Lunghezza minima password**: specifica il numero minimo di cifre o caratteri per la password.
- **Tipo di password richiesto:** specificare se l'utente deve creare una password di tipo **Alfanumerico** o **Numerico**.
- **Numero minimo di set di caratteri:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, usare questa impostazione per specificare il numero minimo di set di caratteri che la password deve avere. I quattro set di caratteri sono:
  - Lettere minuscole
  - Lettere maiuscole
  - Simboli
  - Numeri

Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

Per i dispositivi iOS, questa impostazione si riferisce al numero di caratteri speciali (ad esempio **!** , **#** , **&amp;** ) che è necessario includere nella password.

- **Minuti di inattività prima che venga richiesta la password**: specifica il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Ricorda cronologia password**: usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.
- **Impedisci riutilizzo delle password precedenti**: se l'opzione **Ricorda cronologia password** è selezionata, specifica il numero di password usate in precedenza che non è possibile usare di nuovo.
- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**: questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### <a name="email-profile"></a>Profilo di posta elettronica

- **L'account di posta elettronica deve essere gestito da Intune**: se questa opzione è impostata su **Sì**, il dispositivo deve usare il profilo di posta elettronica distribuito al dispositivo stesso. Il dispositivo è considerato non conforme nelle seguenti situazioni:
  - Il profilo di posta elettronica viene distribuito a un gruppo di utenti diverso dal gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo con provisioning dell'utente, quindi non può gestirlo. Per garantire la conformità, l'utente deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.
- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune**: se è stata selezionata l'impostazione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per specificare il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere presente nel dispositivo.

Per dettagli sul profilo di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Impostazioni dello stato dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted**: se si abilita questa impostazione, i dispositivi jailbroken non risultano conformi.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->

