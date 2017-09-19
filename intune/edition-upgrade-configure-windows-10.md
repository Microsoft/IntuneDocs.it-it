---
title: Configurare gli aggiornamenti edizione di Windows 10 con Intune
titlesuffix: Azure portal
description: Informazioni sull'uso di Intune per aggiornare a un'edizione diversa i dispositivi Windows 10 gestiti."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 40c3ca0207ed81af3212ad2ea04598654cab7198
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Come configurare gli aggiornamenti edizione di Windows 10 in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le informazioni in questo argomento per imparare a configurare un profilo di aggiornamento edizione di Windows 10. Questo profilo consente di aggiornare automaticamente a un'altra edizione i dispositivi che eseguono una delle seguenti versioni di Windows 10:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobile


Sono supportati i seguenti percorsi di aggiornamento:

- Da Windows 10 Pro a Windows 10 Enterprise
- Da Windows 10 Home a Windows 10 Education
- Da Windows 10 Mobile a Windows 10 Mobile Enterprise
- Da Windows 10 Holographic Pro a Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:

- Un codice Product Key valido per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. Si possono usare codici Multiple Activation Key (MAK) oppure del server di gestione delle chiavi o un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
- I dispositivi Windows 10 a cui vengono assegnati i criteri devono essere registrati in Microsoft Intune. Non è possibile usare criteri di aggiornamento dell'edizione con PC che eseguono il software client per PC di Intune.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di aggiornamento dell'edizione.
5. Dall'elenco a discesa **Piattaforma** scegliere **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Aggiornamento edizione**.
7. Nel pannello **Aggiornamento edizione** configurare le impostazioni seguenti:
    - **Edizione da cui eseguire l'aggiornamento**: dall'elenco a discesa selezionare la versione Windows 10 che si desidera aggiornare sui dispositivi.
    - **Edizione a cui eseguire l'aggiornamento**: nell'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
    - **Codice Product Key**: specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Windows 10 Desktop di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificarlo in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
    - **File di licenza**: scegliere **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione Windows Holographic o Windows 10 Mobile in base alla quale si vogliono aggiornare i dispositivi di destinazione.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

>[!NOTE]
>Se si rimuove l'assegnazione dei criteri in seguito, la versione di Windows nel dispositivo non viene ripristinata e continua a funzionare normalmente.

