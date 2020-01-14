---
title: Usare i report di Conformità aggiornamenti per gli aggiornamenti di Windows in Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare Conformità aggiornamenti di Operation Management Suite per visualizzare i dati dei report per gli aggiornamenti di Windows distribuiti con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1e493e0d2d562c0f69454d1999e82b528c724a2
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731280"
---
# <a name="intune-compliance-reports-for-updates"></a>Report di conformità di Intune per gli aggiornamenti

Quando si usa Intune per distribuire aggiornamenti di Windows in dispositivi Windows 10, è possibile visualizzare i dettagli sulla conformità degli aggiornamenti tramite Intune o una soluzione gratuita denominata *Conformità aggiornamenti*, che fa parte di Microsoft Operations Management Suite.

## <a name="use-intune"></a>Usare Intune

Per esaminare un report sui criteri sullo stato di distribuzione per gli anelli di aggiornamento di Windows 10 configurati:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Panoramica** > **Stato dell'aggiornamento software**. Vengono visualizzate informazioni generali sullo stato di tutti gli anelli di aggiornamento assegnati.

3. Per visualizzare ulteriori dettagli, selezionare **Monitoraggio**. Quindi, in **Aggiornamenti software** selezionare **Stato di distribuzione per ogni anello di aggiornamento** e scegliere l'anello di distribuzione da rivedere.

   Nella sezione **Monitoraggio** scegliere uno dei report seguenti per visualizzare informazioni dettagliate sull'anello di aggiornamento:

   - **Stato del dispositivo**: visualizza lo stato di configurazione del dispositivo. Per informazioni dettagliate, vedere [Aggiornare deviceConfigurationDeviceStatus]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **Stato dell'utente**: visualizza il nome utente, lo stato e la data dell'ultimo report. Per informazioni dettagliate, vedere [Visualizzare deviceConfigurationUserStatus](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **Stato di aggiornamento dell'utente finale**: visualizza lo stato di aggiornamento del dispositivo Windows. Per informazioni dettagliate, vedere [windowsUpdateState](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Usare Conformità aggiornamenti

È possibile monitorare le implementazioni degli aggiornamenti di Windows 10 usando [Conformità aggiornamenti](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), una soluzione Windows Analytics. Conformità aggiornamenti viene fornito tramite il portale di Azure ed è disponibile gratuitamente per i dispositivi che ne soddisfano i [prerequisiti](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Quando si usa questa soluzione, è possibile distribuire un ID commerciale in uno qualsiasi dei dispositivi Windows 10 gestiti da Intune per cui si vuole creare report di conformità degli aggiornamenti.  

In Intune usare le impostazioni OMA-URI di un criterio personalizzato per configurare l'ID commerciale. Vedere [Usare le impostazioni personalizzate per dispositivi Windows 10 in Intune](../configuration/custom-settings-windows-10.md).

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
