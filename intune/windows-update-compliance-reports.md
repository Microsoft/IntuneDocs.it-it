---
title: Usare i report di conformità degli aggiornamenti per gli aggiornamenti di Windows in Microsoft Intune | Microsoft Docs
description: Usare Conformità aggiornamenti di Operation Management Suite per visualizzare i dati dei report per gli aggiornamenti di Windows distribuiti con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2b236d01cb5ffcf5a26e71ac0a9b65bb586dcb1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039658"
---
# <a name="intune-compliance-reports-for-updates"></a>Report di conformità di Intune per gli aggiornamenti
Quando si usa Intune per distribuire aggiornamenti di Windows in dispositivi Windows 10, è possibile visualizzare i dettagli sulla conformità degli aggiornamenti tramite Intune o una soluzione gratuita denominata *Conformità aggiornamenti*, che fa parte di Microsoft Operations Management Suite.

## <a name="use-intune"></a>Usare Intune
Per esaminare un report sui criteri sullo stato di distribuzione per gli anelli di aggiornamento di Windows 10 configurati: 
1. Accedere al [portale di Azure](https://portal.azure.com/).
2. Scegliere **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Aggiornamenti software** > **Panoramica**. Vengono visualizzate informazioni generali sullo stato di tutti gli anelli di aggiornamento assegnati.
4. Aprire uno dei report seguenti:  

   **Per tutti gli anelli di distribuzione**:
   1. In **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**
   2. Nella sezione **Monitoraggio** scegliere **Stato di distribuzione per ogni anello di aggiornamento**.  

   **Per anelli di distribuzione specifici**:  

   1. In **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10** scegliere l'anello di distribuzione da rivedere.  
   2. Nella sezione **Monitoraggio** scegliere uno dei report seguenti per visualizzare informazioni dettagliate sull'anello di aggiornamento:  
      - **Stato del dispositivo**  
      - **Stato utente**  

## <a name="use-update-compliance"></a>Usare Conformità aggiornamenti
È possibile monitorare le implementazioni degli aggiornamenti di Windows 10 usando [Conformità aggiornamenti](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), una soluzione Windows Analytics. Conformità aggiornamenti viene fornito tramite il portale di Azure ed è disponibile gratuitamente per i dispositivi che ne soddisfano i [prerequisiti](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Quando si usa questa soluzione, è possibile distribuire un ID commerciale in uno qualsiasi dei dispositivi Windows 10 gestiti da Intune per cui si vuole creare report di conformità degli aggiornamenti.  

Nella console di Intune è possibile usare le impostazioni OMA-URI di un criterio personalizzato per configurare l'ID commerciale. Per informazioni dettagliate, vedere [Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

Il percorso OMA-URI (con distinzione tra maiuscole e minuscole) per configurare l'ID commerciale è: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

È ad esempio possibile usare i valori seguenti in **Aggiungi o modifica impostazione URI OMA**:
- **Nome dell'impostazione**: ID commerciale di Windows Analytics
- **Descrizione dell'impostazione**: configurazione dell'ID commerciale per le soluzioni Windows Analytics
- **OMA-URI** (con distinzione tra maiuscole e minuscole): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Tipo di dati**: Stringa
- **Valore**: \<usare il GUID mostrato nella scheda Telemetria di Windows nell'area di lavoro OMS>
 
> [!NOTE]  
> Per altre informazioni su MS DM Server, vedere [DMClient configuration service provider (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp) (Provider di servizi di configurazione per DMClient).

## <a name="next-steps"></a>Passaggi successivi
[Gestire gli aggiornamenti software in Intune](windows-update-for-business-configure.md)

