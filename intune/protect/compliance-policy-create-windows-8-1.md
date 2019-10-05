---
title: Impostazioni di conformità di Windows 8.1 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Windows 8.1 e Windows Phone 8.1 in Microsoft Intune. Verificare la conformità nella versione minima e massima del sistema operativo, impostare le restrizioni relative alla password e la lunghezza, abilitare la crittografia nell'archiviazione dati e così via.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f37fbd4cf2cc67e8e102ae5bdd4647e0073aa2da
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733023"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Windows 8.1 per contrassegnare un dispositivo come conforme o non conforme in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Windows 8.1 in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per bloccare le password semplice, impostare una versione minima e massima del sistema operativo e così via.

Questa funzionalità si applica a:

- Windows Phone 8.1
- Windows 8.1 e versioni successive

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma** selezionare **Windows Phone 8.1** o **Windows 8.1 e versioni successive**.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: immettere la versione minima consentita. Quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.
- **Versione massima consentita del sistema operativo**: immettere la versione massima consentita. quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene richiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse aziendali finché non viene modificata la regola per consentire la versione del sistema operativo.

I PC Windows 8.1 restituiscono la versione **3**. Se la regola della versione del sistema operativo è impostata su Windows 8.1 per Windows, il dispositivo risulta non conforme anche se il sistema operativo installato è Windows 8.1.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.

  Per i dispositivi che eseguono Windows e prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida:
  - Se la lunghezza minima della password è maggiore di otto caratteri
  - Oppure, se il numero minimo di set di caratteri è maggiore di due

- **Tipo di password**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).
  
  - **Numero di caratteri non alfanumerici nella password:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, questa impostazione specifica il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
    - Lettere minuscole
    - Lettere maiuscole
    - Simboli
    - Numeri

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa. Per i dispositivi che prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida:

    - Se la lunghezza minima della password è maggiore di otto caratteri
    - Oppure, se il numero minimo di set di caratteri è maggiore di due

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)** : selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sui dispositivi mobili**: **richiedere** la crittografia del dispositivo per la connessione alle risorse di archiviazione dati.

Selezionare **OK** > **Crea** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](compliance-policy-create-windows.md).