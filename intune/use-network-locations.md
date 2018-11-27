---
title: Associare dispositivi Android in base al percorso di rete in Microsoft Intune - Azure | Microsoft Docs
description: Creare o configurare percorsi di rete in Microsoft Intune per dispositivi Android. È possibile contrassegnare un dispositivo come non conforme in base al percorso di rete del dispositivo stesso. Se il dispositivo viene spostato al di fuori del percorso di rete, è possibile bloccare l'accesso alle risorse aziendali.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 619976887a7c523933a9e74233779d188baa2cc1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183673"
---
# <a name="use-locations-network-fence-in-intune"></a>Usare i percorsi (isolamento di rete) in Intune

Può essere necessario bloccare l'accesso a una rete aziendale, se un dispositivo lascia un percorso. Questa funzionalità è offerta dalla funzione **Percorsi** in Intune. 

È possibile creare criteri di conformità basati sul percorso di rete. Questa funzionalità è nota anche con il nome di isolamento di rete. Questi criteri consentono di assicurarsi che, per essere ritenuti conformi, i dispositivi siano collegati a una rete aziendale. È possibile usare questi criteri insieme a criteri di accesso condizionale, in modo che i dispositivi abbiano accesso a risorse aziendali *solo* se sono connessi alla rete aziendale. Se il dispositivo non è connesso alla rete aziendale, il dispositivo non è più conforme e perde l'accesso alle risorse aziendali.

Considerare lo scenario seguente:

In una struttura di produzione, alcuni dipendenti usano dispositivi Android. Un dipendente porta il dispositivo Android all'esterno della struttura o dell'impianto. Per impedire un accesso non autorizzato, è possibile:

1. Creare un percorso con un intervallo IPv4 denominato **Reparto di produzione**.
2. Creare criteri di conformità che richiedano che i dispositivi siano connessi alla rete aziendale e assegnare tali criteri.
3. Se il dispositivo viene spostato all'esterno dell'impianto di produzione, viene considerato non conforme e non ha accesso alle risorse aziendali.

Inoltre, è possibile aggiungere [azioni per la mancata conformità](#configure-the-actions-for-noncompliance). Quando il dispositivo torna in sede e all'interno del percorso di rete, otterrà di nuovo l'accesso alle risorse aziendali.

## <a name="prerequisites"></a>Prerequisiti

Per creare criteri di conformità basati sul percorso:

- Creare un percorso di rete con intervalli di rete IPv4 per il server gateway,per il server DHCP e/o per il server DNS a cui si connettono i dispositivi
- Creare criteri di conformità che usino questi percorsi e definiscano l'azione da eseguire quando un dispositivo non è più connesso al percorso di rete
- Dispositivi Android 6.0 e versioni successive, con l'app Portale aziendale aggiornata

## <a name="create-a-location"></a>Creare un percorso

1. In Intune selezionare **Conformità del dispositivo** > **Percorsi** > **Crea**.

2. Immettere le seguenti proprietà:  

   - Obbligatorio. Immettere un **Nome** per il percorso, ad esempio **Reparto di produzione** o **Edificio 44 protetto**.
   - Facoltativo. Immettere un **Intervallo IPv4** con la notazione CIDR (Classless Interdomain Routing), ad esempio `aaa.bbb.ccc.ddd/n`.
   - Facoltativo. Immettere l'indirizzo **Gateway IPv4**, ad esempio `aaa.bbb.ccc.ddd`.
   - Facoltativo. Immettere l'indirizzo **Server DHCP IPv4**, ad esempio `aaa.bbb.ccc.ddd`.
   - Facoltativo. Immettere un elenco di indirizzi **Server DNS IPv4**. Questa impostazione usa la funzione di **corrispondenza di subset**. Se i server DNS IPv4 del dispositivo sono subset dei valori definiti, il dispositivo viene considerato ALL'INTERNO del limite di isolamento. Assicurarsi di immettere un solo indirizzo per ogni riga, ad esempio:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Facoltativo. Immettere un elenco di **Suffissi DNS**. Questa impostazione usa la funzione di **corrispondenza di subset**. Se i suffissi DNS del dispositivo sono subset dei valori definiti, il dispositivo viene considerato ALL'INTERNO del limite di isolamento. Assicurarsi di immettere un solo nome di dominio in ogni riga, ad esempio:  
     `contoso.com`  
     `contoso.org`

3. **Salvare** le modifiche.

## <a name="create-the-location-compliance-policy"></a>Creare i criteri di conformità di percorso

Quando si creano i criteri di conformità, selezionare **Android** come **Piattaforma**. In **Percorsi** è possibile scegliere uno o più dei percorsi di rete aggiunti. Questi percorsi fanno parte dell'isolamento di rete che si sta creando per i dispositivi.

[Creare criteri di conformità basati sul percorso di rete](compliance-policy-create-android.md#locations) offre materiale sussidiario.

## <a name="configure-the-actions-for-noncompliance"></a>Configurare le azioni per la non conformità

Dopo la creazione dei criteri di conformità, al dispositivo si applica l'azione predefinita per la mancata conformità. È possibile aggiungere altre azioni, ad esempio aggiungere un'azione che invia un messaggio di posta elettronica all'utente quando il dispositivo non è più conforme ai percorsi.

[Aggiungere azioni per la mancata conformità](actions-for-noncompliance.md) offre materiale sussidiario.

## <a name="company-portal-app"></a>App Portale aziendale

Quando il dispositivo è connesso ai percorsi corretti, viene visualizzato come conforme nell'app Portale aziendale. Quando il dispositivo non è connesso a uno dei percorsi corretti, viene visualizzato come non conforme.

## <a name="next-steps"></a>Passaggi successivi
[Monitorare i criteri di conformità dei dispositivi](compliance-policy-monitor.md)  
[Introduzione ai criteri di conformità](device-compliance-get-started.md)
