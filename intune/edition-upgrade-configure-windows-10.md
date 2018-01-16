---
title: Configurare gli aggiornamenti edizione di Windows 10 con Intune
titlesuffix: Azure portal
description: Informazioni sull'uso di Intune per aggiornare a un'edizione diversa i dispositivi Windows 10 gestiti."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b4e1fc203633a9624ce748ab1f36374c5322e3f7
ms.sourcegitcommit: 061dab899e3fbc59b0128e2b4fbdf8ebf80afddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Come configurare gli aggiornamenti edizione di Windows 10 in Microsoft Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le informazioni in questo articolo per imparare a configurare un profilo di aggiornamento dell'edizione di Windows 10. Questo profilo consente di aggiornare automaticamente a un'altra edizione i dispositivi che eseguono Windows 10. 

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:

- Un codice Product Key valido per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. Si possono usare codici Multiple Activation Key (MAK) oppure del server di gestione delle chiavi o un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
- I dispositivi Windows 10 a cui vengono assegnati i criteri devono essere registrati in Microsoft Intune. Non è possibile usare criteri di aggiornamento dell'edizione con PC che eseguono il software client per PC di Intune.

## <a name="supported-upgrade-paths-for-the-windows-10-edition-upgrade-profile"></a>Percorsi di aggiornamento supportati per il profilo di aggiornamento di Windows 10
L'elenco seguente include i percorsi di aggiornamento supportati per il profilo di aggiornamento di Windows 10. L'edizione di Windows 10 da aggiornare è indicata in grassetto seguita dall'elenco delle edizioni supportate da cui è possibile eseguire l'aggiornamento:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N**    
- Windows 10 Pro N
- Windows 10 Pro Education N
- Windows 10 Cloud N
- Windows 10 Enterprise N
- Windows 10 Core N
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N**
- Windows 10 Pro N
- Windows 10 Cloud N
- Windows 10 Core N
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N**
- Windows 10 Cloud N
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N**
- Windows 10 Pro N
- Windows 10 Cloud N
- Windows 10 Core N

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile

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

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo
1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di aggiornamento dell'edizione.
5. Dall'elenco a discesa **Piattaforma** scegliere **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Aggiornamento edizione**.
7. Nel pannello **Aggiornamento edizione** configurare le impostazioni seguenti:
    - **Edizione a cui eseguire l'aggiornamento**: nell'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
    - **Codice Product Key**: specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Windows 10 Desktop di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificarlo in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
    - **File di licenza**: scegliere **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione di Windows Holographic o Windows 10 Mobile a cui si vogliono aggiornare i dispositivi di destinazione.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

>[!NOTE]
>Se si rimuove l'assegnazione dei criteri in seguito, la versione di Windows nel dispositivo non viene ripristinata e continua a funzionare normalmente.

