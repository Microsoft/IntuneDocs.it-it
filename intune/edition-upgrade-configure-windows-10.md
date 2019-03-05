---
title: Eseguire l'aggiornamento o usare la modalità S nei dispositivi Windows 10 - Microsoft Intune - Azure | Microsoft Docs
description: Usare Microsoft Intune per aggiornare i dispositivi Windows 10 a un'edizione diversa oppure abilitare la modalità S. Gli amministratori possono usare un profilo di configurazione del dispositivo per eseguire l'aggiornamento di Windows 10 Professional a Windows 10 Enterprise e abilitare o disattivare la modalità S. Vedere i percorsi di aggiornamento supportati per Windows 10 Pro, edizioni N, Education, Cloud, Enterprise, Core, Holographic e Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26a8718247142ef2ed3f509dc185207b1e99e82f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233322"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Aggiornare le edizioni Windows 10 o abilitare la modalità S nei dispositivi con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Come parte della soluzione di gestione di dispositivi mobili (MDM), può essere necessario aggiornare i dispositivi Windows 10. Ad esempio, aggiornare i dispositivi Windows 10 Professional a Windows 10 Enterprise. Potrebbe anche risultare necessario abilitare la modalità S per i dispositivi mobili in modo che i dispositivi eseguano app solo da Microsoft Store.

La [modalità S di Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) è stata progettata per garantire sicurezza e prestazioni elevate. Se i propri dispositivi eseguono solo app di Microsoft Store, è possibile utilizzare la modalità S per garantire la loro protezione. Se i dispositivi usano app che non sono disponibili in Microsoft Store, disattivare la modalità S. La disattivazione della modalità S è irreversibile. Una volta disattivata, la modalità S non potrà più essere riattivata in Windows 10.

Questa funzionalità si applica a:

- Windows 10 e versioni successive
- Windows 10 1809 o versione successiva per la modalità S
- Windows Holographic for Business

Queste funzionalità sono disponibili in Intune e possono essere configurate dall'amministratore. Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, è possibile eseguire il push o distribuire il profilo nei dispositivi Windows 10 nell'organizzazione. Quando si distribuisce il profilo, Intune aggiorna automaticamente i dispositivi o abilita la modalità S.

Questo articolo elenca i percorsi di aggiornamento supportati e illustra come creare il profilo di configurazione del dispositivo. È anche possibile visualizzare tutte le impostazioni disponibili per l'aggiornamento e la modalità S per [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Se in seguito si rimuove l'assegnazione dei criteri, la versione di Windows nel dispositivo non viene ripristinata. Il dispositivo continua a funzionare normalmente.

## <a name="prerequisites"></a>Prerequisiti

Prima di aggiornare i dispositivi, assicurarsi di avere i prerequisiti seguenti:

- Un codice Product Key valido per installare la versione di Windows aggiornata in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. È possibile usare codici ad attivazione multipla o chiavi del server di gestione delle chiavi.
- Per le edizioni Windows 10 Mobile e Windows 10 Holographic è possibile usare un file di licenza Microsoft. Il file di licenza include le informazioni di licenza per installare la versione aggiornata in tutti i dispositivi a cui sono destinati i criteri.
- I dispositivi Windows 10 a cui vengono assegnati i criteri vengono registrati in Microsoft Intune. Non è possibile usare i criteri di aggiornamento dell'edizione con i PC che eseguono il software client per PC di Intune.

## <a name="supported-upgrade-paths"></a>Percorsi di aggiornamento supportati

La tabella seguente riporta i percorsi di aggiornamento supportati per il profilo di aggiornamento di Windows 10.

| Eseguire l'aggiornamento da | Eseguire l'aggiornamento a |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N | Windows 10 Education N <br/>Windows 10 Enterprise N <br/>Windows 10 Pro Education N | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N | Windows 10 Education N |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N | Windows 10 Education N <br/>Windows 10 Enterprise N <br/>Windows 10 Pro N <br/>Windows 10 Pro Education N | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N | Windows 10 Education N | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N | Windows 10 Education N <br/>Windows 10 Enterprise N <br/>Windows 10 Pro Education N | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo. Ad esempio, immettere `Windows 10 edition upgrade profile` o `Windows 10 switch off S mode`.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare la piattaforma:  

        - **Windows 10 e versioni successive**

    - **Tipo di profilo**: selezionare **Aggiornamento edizione**.
    - **Impostazioni**: immettere le impostazioni da configurare. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere:

        - [Aggiornamento a Windows 10 e modalità S](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Selezionare **OK** > **Crea** per salvare le modifiche. 

Il profilo viene creato e visualizzato nell'elenco. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Visualizzare le impostazioni di aggiornamento e della modalità S per i dispositivi [Windows 10](edition-upgrade-windows-settings.md) e [Windows Holographic for Business](holographic-upgrade.md).
