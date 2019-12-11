---
title: Configurare le impostazioni di posta elettronica in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Creare un profilo di posta elettronica in Microsoft Intune e distribuire questo profilo nei dispositivi Windows, iOS e Android Enterprise. Usare un profilo di posta elettronica per configurare le impostazioni di posta elettronica comuni, tra cui un server di posta elettronica e il metodo di autenticazione per la connessione alla posta elettronica aziendale nei dispositivi gestiti.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 110db564dce5ad68d3c2a26b85e60ecbe99e7335
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059420"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Aggiungere impostazioni di posta elettronica ai dispositivi con Intune

Microsoft Intune include impostazioni di posta elettronica diverse che è possibile distribuire nei dispositivi dell'organizzazione. Un amministratore IT crea profili di posta elettronica con impostazioni specifiche per la connessione a un server di posta, ad esempio Office 365 e Gmail. Gli utenti finali quindi si connettono, eseguono l'autenticazione e sincronizzano gli account di posta elettronica dell'organizzazione nei dispositivi mobili. Creando e distribuendo un profilo di posta elettronica, è possibile assicurarsi che le impostazioni siano standard in più dispositivi e ridurre così le chiamate al supporto da parte degli utenti finali che non conoscono le impostazioni di posta elettronica corrette.

È possibile usare i profili di posta elettronica per configurare le impostazioni di posta elettronica predefinite per i dispositivi seguenti:

- Android Samsung Knox Standard 4.0 e versioni successive
- Android Enterprise
- iOS 8.0 e versioni successive
- Windows Phone 8.1 e versioni successive
- Windows 10 (Desktop) e Windows 10 Mobile

Questo articolo illustra come creare un profilo di posta elettronica in Microsoft Intune e include i collegamenti alle diverse piattaforme per impostazioni più specifiche.

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **Impostazioni di posta elettronica per tutti i dispositivi Windows**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:

        - **Android** (solo Samsung Android Knox Standard)
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 e versioni successive**

    - **Tipo di profilo**: Selezionare **Posta elettronica**.

4. Le impostazioni configurabili variano in base alla piattaforma scelta. Scegliere la piattaforma per le impostazioni dettagliate:

    - [Impostazioni Android Samsung Knox Standard](../email-settings-android.md)
    - [Impostazioni Android Enterprise](../email-settings-android-enterprise.md)
    - [Impostazioni di iOS/iPadOS](email-settings-ios.md)
    - [Impostazioni Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 10](email-settings-windows-10.md)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Dopo aver immesso le impostazioni e creato il profilo, il profilo viene visualizzato nell'elenco dei profili. Ora [assegnare il profilo ad alcuni gruppi](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Rimuovere un profilo di posta elettronica

I profili di posta elettronica vengono assegnati ai gruppi di dispositivi, non ai gruppi di utenti. Esistono diversi modi di rimuovere un profilo di posta elettronica da un dispositivo, anche quando è disponibile un solo profilo di posta elettronica nel dispositivo:

- **Opzione 1**: Aprire il profilo di posta elettronica (**Dispositivi** > **Profili di configurazione** > selezionare il profilo) e scegliere **Assegnazioni**. Nella scheda **Includi** sono visualizzati i gruppi assegnati al profilo. Fare clic con il pulsante destro del mouse sul gruppo > **Rimuovi**. Assicurarsi di **salvare** le modifiche.

- **Opzione 2**: [cancellare o ritirare il dispositivo](../remote-actions/devices-wipe.md). È possibile usare queste azioni per rimuovere completamente o in modo selettivo dati e impostazioni.

## <a name="secure-email-access"></a>Proteggere l'accesso alla posta elettronica

È possibile proteggere i profili di posta elettronica usando le opzioni seguenti:

- **Certificati**: quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo certificato è noto come certificato di identità. Esegue l'autenticazione in base a un profilo certificato attendibile o a un certificato radice per verificare che il dispositivo di un utente sia autorizzato a connettersi. Il certificato attendibile viene assegnato al computer che autentica la connessione alla posta elettronica. Questo computer è in genere il server di posta nativo.

  Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Intune](../protect/certificates-configure.md).

- **Nome utente e password**: l'utente esegue l'autenticazione al server di posta nativo immettendo nome utente e password. La password non esiste nel profilo di posta elettronica, quindi l'utente finale immette la password quando si connette alla posta elettronica.

## <a name="how-intune-handles-existing-email-accounts"></a>In che modo Intune gestisce gli account di posta elettronica esistenti

Se l'utente ha già configurato un account di posta elettronica, il profilo di posta elettronica viene assegnato in modo diverso, a seconda della piattaforma.

- **iOS**: Un profilo di posta elettronica duplicato esistente viene individuato in base al nome host e all'indirizzo di posta elettronica. Il profilo di posta elettronica duplicato blocca l'assegnazione di un profilo di Intune. In questo caso l'app Portale aziendale notifica all'utente finale che esiste un problema di conformità e richiede quindi di rimuovere il profilo. Per evitare questo scenario, indicare agli utenti finali di eseguire la registrazione *prima* di installare un profilo di posta elettronica e di consentire a Intune di impostarlo.

- **Windows:** Un profilo di posta elettronica duplicato esistente viene individuato in base al nome host e all'indirizzo di posta elettronica. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente finale.

- **Android Samsung Knox Standard**: Un profilo di posta elettronica duplicato esistente viene individuato in base all'indirizzo di posta elettronica e viene sovrascritto con il profilo di Intune. Android non usa il nome host per identificare il profilo. Non creare più profili di posta elettronica usando lo stesso indirizzo di posta elettronica in host diversi. I profili si sovrascrivono a vicenda.

- **Profili di lavoro Android**: Intune offre due profili di posta elettronica di lavoro Android, uno per l'app Gmail e uno per l'app Nine Work. Queste app sono disponibili in Google Play Store e vengono installate nel profilo di lavoro del dispositivo. Queste app non creano profili duplicati. Entrambe le app supportano le connessioni a Exchange. Per usare la connettività di posta elettronica, distribuire una di queste app di posta elettronica nei dispositivi degli utenti, quindi creare e distribuire il profilo di posta elettronica appropriato. Le app di posta elettronica, ad esempio Nine Work, potrebbero non essere gratuite. Rivedere i dettagli relativi alla licenza dell'app o contattare l'azienda produttrice per richiedere informazioni.

## <a name="changes-to-assigned-email-profiles"></a>Modifiche ai profili di posta elettronica assegnati

Se si apportano modifiche a un profilo di posta elettronica assegnato in precedenza, è possibile che un messaggio richieda agli utenti finali di approvare la riconfigurazione delle impostazioni di posta elettronica.

## <a name="next-steps"></a>Passaggi successivi

Dopo che il profilo è stato creato, non è ancora operativo. È ora necessario [assegnare il profilo](../device-profile-assign.md).
