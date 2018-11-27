---
title: Eseguire l'aggiornamento o usare la modalità S sui dispositivi Windows 10 con Microsoft Intune - Azure | Microsoft Docs
description: Creare un profilo dispositivo in Microsoft Intune per aggiornare i dispositivi Windows 10 alle edizioni più recenti. Ad esempio, è possibile eseguire l'aggiornamento da Windows 10 Professional a Windows 10 Enterprise. Usando il profilo di configurazione è anche possibile attivare o disattivare la modalità S. Vedere anche i percorsi di aggiornamento supportati per Windows 10 Pro, edizioni N, Education, Cloud, Enterprise, Core, Holographic e Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eb44647e50e406b9ef5052c576660c9b7eebf6dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189759"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Usare un profilo di configurazione per aggiornare Windows 10, o disattivare la modalità S in Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurare un profilo di aggiornamento in Intune per aggiornare automaticamente a un'altra edizione i dispositivi che eseguono Windows 10. Vedere anche i percorsi di aggiornamento supportati.

## <a name="before-you-begin"></a>Prima di iniziare
Prima di aggiornare i dispositivi alla versione più recente, è necessario soddisfare i prerequisiti seguenti:

- Un codice Product Key valido per installare la versione di Windows aggiornata in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. È possibile usare codici ad attivazione multipla o chiavi del server di gestione delle chiavi. Per le edizioni Windows 10 Mobile e Windows 10 Holographic si può usare un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri.
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


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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

## <a name="upgrade-the-edition"></a>Aggiornare l'edizione

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **Nome** e una **Descrizione** per il profilo. Ad esempio, immettere un nome come `Windows 10 edition upgrade`
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. Per **Tipo di profilo** selezionare **Aggiornamento edizione**.
6. Nelle proprietà **Aggiornamento edizione** immettere le impostazioni seguenti:

   - **Edizione a cui eseguire l'aggiornamento**: selezionare l'edizione Windows 10 a cui si esegue l'aggiornamento. I dispositivi a cui è destinato questo criterio vengono aggiornati all'edizione che scelta.
   - **Codice Product Key**: immettere il codice product key ricevuto da Microsoft. Dopo aver creato il criterio con il codice Product Key, la chiave non può essere aggiornata e viene nascosta per motivi di sicurezza. Per modificare il codice Product Key, immettere nuovamente l'intero codice.
   - **File di licenza**: per l'edizione **Windows 10 Holographic for Business** o **Windows 10 Mobile**, scegliere **Sfoglia** per selezionare il file di licenza ricevuto da Microsoft. Il file di licenza include le informazioni di licenza delle edizioni a cui si stanno aggiornando i dispositivi specificati.

7. Selezionare **OK** per salvare le modifiche. Selezionare **Crea** per creare il profilo.

## <a name="switch-out-of-s-mode"></a>Disattivare la modalità S

La [modalità S di Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) è stata progettata per garantire sicurezza e prestazioni elevate. Se i propri dispositivi eseguono solo app di Microsoft Store, è possibile utilizzare la modalità S per garantire la loro protezione. Se i propri dispositivi richiedono app che non sono disponibili in Microsoft Store, disattivare la modalità S. La disattivazione della modalità S è irreversibile. Una volta disattivata, la modalità S non potrà più essere riattivata in Windows 10.

I passaggi seguenti illustrano come creare un profilo che controlli la modalità S nei dispositivi di Windows 10 (1809 o versione successiva).

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **Nome** e una **Descrizione** per il profilo. Ad esempio, immettere un nome come `Windows 10 switch off S mode`
4. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
5. Per **Tipo di profilo** selezionare **Aggiornamento edizione**.
6. Selezionare **Cambio di modalità (Windows Insider)** e impostare la proprietà **Switch out of S mode** (Disattiva la modalità S). Le opzioni disponibili sono:

    - **Nessuna configurazione**: un dispositivo in modalità S rimane in modalità S. Un utente finale può disattivare la modalità S sul dispositivo.
    - **Mantieni in modalità S**: impedisce all'utente finale di poter disattivare la modalità S sul dispositivo.
    - **Switch** (Cambia): disattiva la modalità S sul dispositivo.

7. Selezionare **OK** per salvare le modifiche. Selezionare **Crea** per creare il profilo.

Il profilo viene creato e visualizzato tra i profili.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare questo profilo](device-profile-assign.md) ai gruppi.

>[!NOTE]
>Se in seguito si rimuove l'assegnazione dei criteri, la versione di Windows nel dispositivo non viene ripristinata e continua a funzionare normalmente.
