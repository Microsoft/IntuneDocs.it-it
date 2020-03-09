---
title: Visualizzare i dettagli del dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare i dettagli relativi al dispositivo, inclusi i sistemi operativi, lo spazio di archiviazione, il produttore e il modello. Ottenere un elenco delle app installate, controllare i criteri di conformità e configurare TeamViewer con Microsoft Intune in Azure. Simile alla visualizzazione dell'inventario dei dispositivi gestiti.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df814abf9cdff3eb4d9fbac8183618461b590adb
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781924"
---
# <a name="see-device-details-in-intune"></a>Visualizzare i dettagli del dispositivo in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La funzionalità **Dispositivi** offre ulteriori dettagli sui dispositivi gestiti, inclusi i componenti hardware e le app installate.

Questo articolo illustra come visualizzare tutti i dispositivi e le relative proprietà nel portale di Azure.

## <a name="view-the-device-details"></a>Visualizzare i dettagli del dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **Dispositivi** > **Tutti i dispositivi** > selezionare uno dei dispositivi elencati per aprirne i dettagli:

   - **Panoramica** visualizza il nome del dispositivo ed elenca alcune delle proprietà chiave, ad esempio se è un dispositivo Bring Your Own Device (BYOD), quando è stato registrato e altro ancora. È possibile eseguire le seguenti attività sul dispositivo:
      - [Ritira](devices-wipe.md#retire)
      - [Cancellazione](devices-wipe.md#wipe)
      - [Eliminazione](devices-wipe.md#delete-devices-from-the-intune-portal)
      - [Blocco remoto](device-remote-lock.md)
      - [Sincronizzazione](device-sync.md)
      - [Reimposta passcode](device-passcode-reset.md)
      - [Riavvia](device-restart.md) (solo Windows)
      - [Fresh Start](device-fresh-start.md) (solo Windows)
      - [Reimpostazione di Autopilot]() (solo Windows)
      - [Analisi veloce](../configuration/device-restrictions-windows-10.md) (solo Windows 10)
      - [Analisi completa](../configuration/device-restrictions-windows-10.md) (solo Windows 10)
       - [Rinominare il dispositivo](device-rename.md)
      - Avviare una sessione di assistenza remota
   - Usare **Proprietà** per assegnare una [categoria del dispositivo creata](../enrollment/device-group-mapping.md) e modificare la proprietà del dispositivo scegliendo dispositivo personale o dispositivo aziendale.
   - **Hardware** include vari dettagli sul dispositivo, ad esempio l'ID del dispositivo, il sistema operativo e la versione, lo spazio di archiviazione e così via.
   - **App individuate** visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune con relativa versione. Per altre informazioni, vedere [App individuate da Intune](../apps/app-discovered-apps.md).
   - **Conformità del dispositivo** elenca tutti i criteri di conformità assegnati e indica se il dispositivo è conforme o non conforme.
   - **Configurazione del dispositivo** riporta tutti i criteri di configurazione assegnati al dispositivo e indica se il criterio è riuscito o meno.

## <a name="hardware-device-details"></a>Dettagli dispositivo hardware
A seconda del gestore telefonico usato dai dispositivi, è possibile che non vengano raccolti tuti i dettagli

> [!Note]  
> L'inventario hardware e software viene aggiornato nel servizio Intune ogni 7 giorni.

|Dettagli|Descrizione|Piattaforma| 
|--------------|----------------------|----|  
|Name|Nome del dispositivo.|Windows, iOS|
|Nome di gestione|Nome del dispositivo usato solo nella console. Se si modifica questo nome, il nome del dispositivo non viene modificato.|Windows, iOS|
|UDID|Identificatore univoco del dispositivo.|Windows, iOS|
|ID dispositivo di Intune|GUID che identifica in modo univoco il dispositivo.|Windows, iOS|
|Numero di serie|Numero di serie del dispositivo assegnato dal produttore.|Windows, iOS|
|Dispositivo condiviso|Se **Sì** il dispositivo è condiviso da più utenti.|Windows, iOS|
|Registrazione approvata dall'utente|Se **Sì** il dispositivo include la registrazione approvata dall'utente, che consente agli amministratori di gestire alcune impostazioni di sicurezza nel dispositivo stesso.|Windows, iOS|
|Sistema operativo|Sistema operativo presente nel dispositivo.|Windows, iOS|
|Versione del sistema operativo|Versione del sistema operativo installato nel dispositivo.|Windows, iOS|
|Lingua del sistema operativo|Lingua impostata per il sistema operativo nel dispositivo.|Windows, iOS|
|Numero build|Numero di build del sistema operativo.|Android|
|Livello di patch di protezione|Livello della patch di protezione per il dispositivo.|Android|
|Spazio di archiviazione totale|Spazio di archiviazione totale nel dispositivo (in gigabyte).|Windows, iOS|
|Spazio di archiviazione disponibile|Spazio di archiviazione non usato nel dispositivo (in gigabyte).|Windows, iOS|
|IMEI|Identificativo IMEI (International Mobile Equipment Identity) del dispositivo.|Windows, iOS/iPadOS, Android|
|MEID|Identificativo di apparecchiatura mobile del dispositivo.|Windows, iOS/iPadOS, Android|
|Produttore|Produttore del dispositivo.|Windows, iOS/iPadOS, Android|
|Modello|Modello del dispositivo.|Windows, iOS/iPadOS, Android|
|Numero di telefono|Numero di telefono assegnato al dispositivo.|Windows, iOS/iPadOS, Android*|
|Gestore telefonico del sottoscrittore|Vettore wireless del dispositivo.|Windows, iOS/iPadOS, Android|
|Tecnologia cellulare|Sistema di radiotelefonia usato dal dispositivo.|Windows, iOS/iPadOS, Android|
|MAC Wi-Fi|Indirizzo MAC (Media Access Control) del dispositivo.|Windows, iOS/iPadOS, Android|
|ICCID|Identificatore Integrated Circuit Card Identifier, numero di identificazione univoco di una scheda SIM.|Windows, iOS/iPadOS, Android|
|Data registrazione|Data e ora in cui il dispositivo è stato registrato in Intune.|Windows, iOS/iPadOS, Android|
|Ultimo contatto|Data e ora dell'ultimo collegamento del dispositivo a Intune.|Windows, iOS/iPadOS, Android|
|Codice di bypass del blocco attivazione|Codice che può essere usato per disabilitare il blocco attivazione.|iOS|
|Registrato con AAD|Se **Sì** il dispositivo è registrato con Azure Active Directory.|Windows, iOS/iPadOS, Android|
|Registrato in Intune|Se **Sì** il dispositivo è registrato in Intune.|Windows, iOS/iPadOS, Android|
|Conformità|Stato di conformità del dispositivo.|Windows, iOS/iPadOS, Android|
|Attivato da EAS|Se **Sì** il dispositivo è sincronizzato con una cassetta postale di Exchange.|Windows, iOS/iPadOS, Android|
|ID di attivazione EAS|Identificatore Exchange ActiveSync del dispositivo.|Windows, iOS/iPadOS, Android|
|Sotto la supervisione|Se **Sì** gli amministratori dispongono di controllo avanzato sul dispositivo.|Windows, iOS/iPadOS, Android|
|Crittografato|Se **Sì** i dati archiviati nel dispositivo sono crittografati.|Windows, iOS/iPadOS, Android|

> [!Note]  
> Il numero di telefono non è incluso nell'inventario dei dispositivi Android Enterprise dedicati o completamente gestiti.

## <a name="next-steps"></a>Passaggi successivi
Vedere le altre operazioni possibili per [gestire i dispositivi](device-management.md) con Intune.
