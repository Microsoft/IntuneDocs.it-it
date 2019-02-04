---
title: Impostazioni relative all'ottimizzazione recapito per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare la modalità di recapito degli aggiornamenti software ai dispositivi tramite i servizi cloud di ottimizzazione recapito disponibili per i dispositivi con Windows 10 e versioni successive. In Intune, creare un profilo di configurazione del dispositivo per installare gli aggiornamenti da Internet. Vedere anche come sostituire gli anelli di aggiornamento esistenti con un profilo di ottimizzazione recapito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831548"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Impostazioni di ottimizzazione recapito per Windows 10 (e versioni successive) in Microsoft Intune

> [!NOTE]
> Le impostazioni **Aggiornamenti software - Anelli di aggiornamento di Windows 10** vengono sostituite dalle impostazioni di **Ottimizzazione recapito**. È possibile modificare gli anelli di aggiornamento esistenti in modo da usare le impostazioni di **Ottimizzazione recapito**. La sezione [Passare anelli di aggiornamento esistenti all'ottimizzazione recapito](#move-existing-update-rings-to-delivery-optimization) (in questo articolo) elenca i passaggi. 


Questa funzionalità si applica alla piattaforma seguente:

- Windows 10 e versioni successive

Questo articolo elenca e descrive tutte le impostazioni di ottimizzazione recapito che è possibile configurare per i dispositivi Windows 10. Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo e quindi assegnate o distribuite ai dispositivi con Microsoft Intune.

[Ottimizzazione recapito per gli aggiornamenti](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) è una risorsa eccellente per ottenere informazioni sull'ottimizzazione del recapito in Windows 10.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.

2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.

3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare la piattaforma:  

        - **Windows 10 e versioni successive**

    - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.
    - **Impostazioni**: scegliere come si vogliono scaricare gli aggiornamenti. Le opzioni disponibili sono: 

        - **Non configurata**: gli utenti finali aggiornano i propri dispositivi usando il metodo prescelto, che può essere usare **Windows Update** o le impostazioni di **Ottimizzazione recapito** disponibili con il sistema operativo.
        - **Solo HTTP, senza peering**: ottenere gli aggiornamenti solo da Internet. Non è consentito ottenere aggiornamenti da altri computer nella rete (operazione nota come peering o peer-to-peer).
        - **HTTP misto con peering nella stessa NAT**: ottenere gli aggiornamenti da Internet e da altri computer nella rete. 
        - **HTTP misto con peering in un gruppo privato**: Il peering si verifica per i dispositivi nello stesso sito di Active Directory (se presente) o nello stesso dominio. Quando questa opzione è selezionata, il peering attraversa gli indirizzi IP di NAT (Network Address Translation).
        - **HTTP misto con peering Internet**: ottenere gli aggiornamenti da Internet e da altri computer nella rete.
        - **Modalità di download semplice senza peering**: ottenere gli aggiornamenti da Internet, direttamente dal proprietario dell'aggiornamento, ad esempio Microsoft. Non vengono contattati i servizi cloud di ottimizzazione recapito.
        - **Modalità Bypass**: usare BITS (Background Intelligent Transfer Service) per ottenere gli aggiornamenti. Non usare ottimizzazione recapito.

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Passare anelli di aggiornamento esistenti all'ottimizzazione recapito

Le impostazioni **Aggiornamenti software - Anelli di aggiornamento di Windows 10** vengono sostituite dalle impostazioni di **Ottimizzazione recapito**. Gli anelli di aggiornamento esistenti possono essere facilmente modificati per usare le impostazioni di **Ottimizzazione recapito**. Passaggi:

1. Creare un profilo di configurazione di ottimizzazione recapito:

    1. In Intune selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
    2. Immettere le proprietà seguenti:

        - **Nome**: immettere un nome descrittivo per il nuovo profilo.
        - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
        - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
        - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.
        - **Impostazioni**: Per **Modalità di download con ottimizzazione recapito**, scegliere la stessa modalità usata dall'anello di aggiornamento software esistente. Le opzioni disponibili sono:
            - **Non configurato**
            - **Solo HTTP, senza peering**
            - **HTTP misto con peering nella stessa NAT**
            - **HTTP misto con peering in un gruppo privato**
            - **HTTP misto con peering Internet**
            - **Modalità di download semplice senza peering**
            - **Modalità Bypass**

2. Assegnare questo nuovo profilo agli stessi dispositivi e utenti dell'anello di aggiornamento software esistente. La procedura è descritta in [Assegnare un profilo di dispositivo](device-profile-assign.md).

3. Annullare la configurazione dell'anello di aggiornamento software esistente:
    1. In Intune, passare ad **Aggiornamenti software** > Anelli di aggiornamento di Windows 10.
    2. Selezionare l'anello di aggiornamento nell'elenco.
    3. Nelle impostazioni specificare **Non configurata** per **Modalità di download con ottimizzazione recapito**.
    4. **OK** > **Salva** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
