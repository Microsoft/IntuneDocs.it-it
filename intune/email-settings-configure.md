---
title: Configurare le impostazioni di posta elettronica in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Creare un profilo di posta elettronica in Microsoft Intune e distribuire questo profilo nei dispositivi Windows, iOS e Android Enterprise. Usare un profilo di posta elettronica per configurare le impostazioni di posta elettronica comuni, tra cui un server di posta elettronica e il metodo di autenticazione per la connessione alla posta elettronica aziendale nei dispositivi gestiti.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 33a7593adcab7df76020b8bfe520cf6cbd3c6455
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186155"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Aggiungere impostazioni di posta elettronica ai dispositivi con Intune

Microsoft Intune include impostazioni di posta elettronica diverse che è possibile distribuire nei dispositivi dell'organizzazione. Un amministratore IT può creare profili di posta elettronica con impostazioni specifiche per la connessione a un server di posta, ad esempio Office 365 e Gmail. Gli utenti quindi si connettono, eseguono l'autenticazione e sincronizzano gli account di posta elettronica aziendali nei dispositivi mobili. Creando e distribuendo un profilo di posta elettronica, è possibile verificare che le impostazioni siano standard in più dispositivi e ridurre così le chiamate al supporto da parte degli utenti finali che non conoscono le impostazioni di posta elettronica corrette.

È possibile usare i profili di posta elettronica per configurare le impostazioni di posta elettronica predefinite per i dispositivi seguenti:

- Android Samsung Knox Standard 4.0 e versioni successive
- Dispositivi del profilo di lavoro Android
- iOS 8.0 e versioni successive
- Windows Phone 8.1 e versioni successive
- Windows 10 (Desktop) e Windows 10 Mobile

Questo articolo illustra come creare un profilo di posta elettronica in Microsoft Intune e include i collegamenti alle diverse piattaforme per impostazioni più specifiche.

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Specificare un **nome** e una **descrizione** per il profilo di posta elettronica.
4. Scegliere la **piattaforma** dall'elenco a discesa. Le opzioni disponibili sono:

    - **Android** (solo Samsung Android Knox Standard)
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**

5. Nell'elenco a discesa dei tipi di **profilo** scegliere **Posta elettronica**.
6. Le impostazioni che è possibile configurare potrebbero essere diverse per ogni piattaforma. Per le impostazioni specifiche, scegliere la piattaforma:

    - [Impostazioni del profilo di lavoro Android e di Samsung Knox Standard](email-settings-android.md)
    - [Impostazioni iOS](email-settings-ios.md)
    - [Impostazioni Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 10](email-settings-windows-10.md)

Dopo aver immesso le impostazioni e creato il profilo, il profilo viene visualizzato nell'elenco dei profili. Ora [assegnare il profilo ad alcuni gruppi](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Rimuovere un profilo di posta elettronica

I profili di posta elettronica vengono assegnati ai gruppi di dispositivi, non ai gruppi di utenti. Esistono diversi modi di rimuovere un profilo di posta elettronica da un dispositivo, anche quando è disponibile un solo profilo di posta elettronica nel dispositivo:

- **Opzione 1**: aprire il profilo di posta elettronica (**Configurazione del dispositivo** > **Profili**) e scegliere **Assegnazioni**. Nella scheda **Includi** sono visualizzati i gruppi assegnati al profilo. Fare clic con il pulsante destro del mouse sul gruppo > **Rimuovi**. Assicurarsi di **salvare** le modifiche.

- **Opzione 2**: [Cancellare o ritirare il dispositivo](devices-wipe.md). È possibile usare queste azioni per rimuovere completamente o in modo selettivo dati e impostazioni.

## <a name="secure-email-access"></a>Proteggere l'accesso alla posta elettronica

È possibile proteggere i profili di posta elettronica usando le opzioni seguenti:

- **Certificati**: quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo certificato è noto come certificato di identità. Esegue l'autenticazione in base a un profilo certificato attendibile o a un certificato radice per verificare che il dispositivo di un utente sia autorizzato a connettersi. Il certificato attendibile viene assegnato al computer che autentica la connessione alla posta elettronica. Questo computer è in genere il server di posta nativo.

  Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Intune](certificates-configure.md).

- **Nome utente e password**: l'utente esegue l'autenticazione al server di posta nativo immettendo nome utente e password. La password non esiste nel profilo di posta elettronica, quindi l'utente deve immettere la password quando si connette alla posta elettronica.

## <a name="how-intune-handles-existing-email-accounts"></a>In che modo Intune gestisce gli account di posta elettronica esistenti

Se l'utente ha già configurato un account di posta elettronica, il profilo di posta elettronica viene assegnato in modo diverso, a seconda della piattaforma.

- **iOS**: un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Il profilo di posta elettronica duplicato blocca l'assegnazione di un profilo di Intune. In questo caso l'app Portale aziendale notifica all'utente che esiste un problema di conformità e richiede quindi di rimuovere il profilo. Per evitare questo scenario, dire agli utenti di eseguire la registrazione *prima* di installare un profilo di posta elettronica e di consentire a Intune di impostarlo.

- **Windows:** un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.

- **Android Samsung Knox Standard**: un profilo di posta elettronica esistente duplicato viene rilevato sulla base dell'indirizzo di posta elettronica e viene sovrascritto con il profilo di Intune. Android non usa il nome host per identificare il profilo. Non creare più profili di posta elettronica usando lo stesso indirizzo di posta elettronica in host diversi. I profili si sovrascriveranno a vicenda.

- **Profili di lavoro Android**: Intune offre due profili di posta elettronica di lavoro Android, uno per l'app Gmail e uno per l'app Nine Work. Queste app sono disponibili in Google Play Store e vengono installate nel profilo di lavoro del dispositivo. Queste app non creeranno profili duplicati. Entrambe le app supportano le connessioni a Exchange. Per usare la connettività di posta elettronica, distribuire una di queste app di posta elettronica nei dispositivi degli utenti, quindi creare e distribuire il profilo di posta elettronica appropriato. Le app di posta elettronica, ad esempio Nine Work, potrebbero non essere gratuite. Rivedere i dettagli relativi alla licenza dell'app o contattare l'azienda produttrice per richiedere informazioni.

## <a name="changes-to-assigned-email-profiles"></a>Modifiche ai profili di posta elettronica assegnati

Se si apportano modifiche a un profilo di posta elettronica assegnato in precedenza, è possibile che un messaggio richieda agli utenti finali di approvare la riconfigurazione delle impostazioni di posta elettronica.

## <a name="next-steps"></a>Passaggi successivi
Dopo che il profilo è stato creato, non è ancora operativo. Ora [assegnare il profilo ad alcuni dispositivi](device-profile-assign.md).