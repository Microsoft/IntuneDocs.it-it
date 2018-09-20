---
title: Visualizzare i dettagli del dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare i dettagli relativi al dispositivo, inclusi i sistemi operativi, lo spazio di archiviazione, il produttore e il modello. Ottenere un elenco delle app installate, controllare i criteri di conformità e configurare TeamViewer con Microsoft Intune in Azure. Simile alla visualizzazione dell'inventario dei dispositivi gestiti.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a658182800f480f27097e078f28adc95c35aa3ea
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313179"
---
# <a name="see-device-details-in-intune"></a>Visualizzare i dettagli del dispositivo in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La funzionalità **Dispositivi** offre ulteriori dettagli sui dispositivi gestiti, inclusi i componenti hardware e le app installate.

Questo articolo illustra come visualizzare tutti i dispositivi e le relative proprietà nel portale di Azure.

## <a name="view-the-device-details"></a>Visualizzare i dettagli del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** > **Tutti i dispositivi** > selezionare uno dei dispositivi elencati per aprirne i dettagli:

   - **Panoramica** mostra il nome del dispositivo ed elenca alcune delle sue proprietà chiave, ad esempio se è un dispositivo Bring Your Own Device (BYOD), quando è stato registrato e altro ancora. Sul dispositivo si possono eseguire le azioni seguenti:
      - [Ritira](devices-wipe.md#retire)
        - [Cancellazione](devices-wipe.md#wipe)
        - [Blocco remoto](device-remote-lock.md)
        - [Sincronizzare il dispositivo](device-sync.md)
        - [Reimposta passcode](device-passcode-reset.md)
        - [Riavvia](device-restart.md) (solo Windows)
        - [Fresh Start](device-fresh-start.md) (solo Windows)
     - Avviare una sessione di assistenza remota
   - Usare **Proprietà** per assegnare una [categoria del dispositivo creata](device-group-mapping.md) e modificare la proprietà del dispositivo scegliendo dispositivo personale o dispositivo aziendale.
   - **Hardware** include molte informazioni sul dispositivo, come l'ID del dispositivo, il sistema operativo e la versione, lo spazio di archiviazione, il modello e il produttore, le impostazioni di accesso condizionale e altro.
   - **App individuate** visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune con relativa versione. È anche possibile **esportare** l'elenco di app in un file CSV.
   - **Conformità del dispositivo** elenca tutti i criteri di conformità assegnati e indica se il dispositivo è conforme o non conforme.
   - **Configurazione del dispositivo** riporta tutti i criteri di configurazione assegnati al dispositivo e indica se il criterio è riuscito o meno.

Intune raccoglie un elenco di app solo nei dispositivi di proprietà dell'azienda. Le app non vengono controllate nei dispositivi personali. Per i PC Windows 10, solo le app moderne vengono elencate per i dispositivi di proprietà dell'azienda. Intune non raccoglie informazioni sulle app Win32 nel dispositivo. A seconda del gestore telefonico usato dai dispositivi, è possibile che non tutte le app vengano raccolte.

|Piattaforma|Per i dispositivi di proprietà personale|Per i dispositivi di proprietà dell'azienda|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 senza il client di Configuration Manager|Solo le app gestite|Solo le app gestite|
|Windows 8.1 senza il client di Configuration Manager|Solo le app gestite|Solo le app gestite|  
|Windows Phone 8|Solo le app gestite|Solo le app gestite|  
|Windows RT|Solo le app gestite|Solo le app gestite|  
|iOS|Solo le app gestite|Tutte le app installate nel dispositivo|
|macOS|Tutte le app installate nel dispositivo|Tutte le app installate nel dispositivo|  
|Android|Solo le app gestite|Tutte le app installate nel dispositivo|  

## <a name="hardware-device-details"></a>Dettagli dispositivo hardware

### <a name="windows-and-ios-device-details"></a>Dettagli dispositivo Windows e iOS:
|Dettagli|Descrizione|  
|--------------|----------------------|  
|Name|Nome del dispositivo.|
|Nome di gestione|Nome del dispositivo usato solo nella console. Se si modifica questo nome, il nome del dispositivo non viene modificato.|
|UDID|Identificatore univoco del dispositivo.|
|ID dispositivo di Intune|GUID che identifica in modo univoco il dispositivo.|
|Numero di serie|Numero di serie del dispositivo assegnato dal produttore.|
|Dispositivo condiviso|Se **Sì** il dispositivo è condiviso da più utenti.|
|Registrazione approvata dall'utente|Se **Sì** il dispositivo include la registrazione approvata dall'utente, che consente agli amministratori di gestire alcune impostazioni di sicurezza nel dispositivo stesso.|
|Sistema operativo|Sistema operativo presente nel dispositivo.|
|Versione del sistema operativo|Versione del sistema operativo del dispositivo.|
|Lingua del sistema operativo|Lingua impostata per il sistema operativo nel dispositivo.|
|Spazio di archiviazione totale|Spazio di archiviazione totale nel dispositivo (in gigabyte).|
|Spazio di archiviazione disponibile|Spazio di archiviazione non usato nel dispositivo (in gigabyte).|


### <a name="windows-ios-and-macos-device-details"></a>Dettagli del dispositivo per Windows, iOS e macOS
|Dettagli|Descrizione|  
|--------------|----------------------|  
|IMEI|Identificativo IMEI (International Mobile Equipment Identity) del dispositivo.|
|MEID|Identificativo di apparecchiatura mobile del dispositivo.|
|Produttore|Produttore del dispositivo.|
|Modello|Modello del dispositivo.|
|Numero di telefono|Numero di telefono assegnato al dispositivo.|
|Gestore telefonico del sottoscrittore|Vettore wireless del dispositivo.|
|Tecnologia cellulare|Sistema di radiotelefonia usato dal dispositivo.|
|MAC Wi-Fi|Indirizzo MAC (Media Access Control) del dispositivo.|
|ICCID|Identificatore Integrated Circuit Card Identifier, numero di identificazione univoco di una scheda SIM.|
|Data registrazione|Data e ora in cui il dispositivo è stato registrato in Intune.|
|Ultimo contatto|Data e ora dell'ultimo collegamento del dispositivo a Intune.|
|Codice di bypass del blocco attivazione|Codice che può essere usato per ignorare il blocco attivazione.|
|Registrato con AAD|Se **Sì** il dispositivo è registrato con Azure Active Directory.|
|Conformità|Stato di conformità del dispositivo.|
|Attivato da EAS|Se **Sì** il dispositivo è sincronizzato con una cassetta postale di Exchange.|
|ID di attivazione EAS|Identificatore Exchange ActiveSync del dispositivo.|
|Sotto la supervisione|Se **Sì** gli amministratori dispongono di controllo avanzato sul dispositivo.|
|Crittografato|Se **Sì** i dati archiviati nel dispositivo sono crittografati.|



## <a name="next-steps"></a>Passaggi successivi
Vedere le altre operazioni possibili per [gestire i dispositivi](device-management.md) con Intune.