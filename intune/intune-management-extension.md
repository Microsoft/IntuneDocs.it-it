---
title: Gestire gli script di PowerShell in Microsoft Intune per i dispositivi Windows 10
titlesuffix: ''
description: Informazioni su come caricare script di PowerShell in Microsoft Intune per l'esecuzione in dispositivi Windows 10.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c501292126200baa88e06e30b6226e5c5021b8ec
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2018
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10
L'estensione di gestione di Intune consente di caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione di gestione integra le funzionalità di gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice passare a una gestione moderna.

## <a name="moving-to-modern-management"></a>Passare alla gestione moderna
I computer destinati agli utenti finali stanno attraversando una fase di trasformazione digitale. Le attività IT tradizionali e classiche si occupano di piattaforme su singoli dispositivi, di dispositivi di proprietà dell'azienda, di utenti che lavorano in ufficio e di una serie di processi reattivi manuali. Un'area di lavoro moderna, tuttavia, prevede piattaforme su più dispositivi, di proprietà dell'utente finale e dell'azienda, consente di lavorare ovunque ci si trovi e mette a disposizione processi IT automatizzati e proattivi. 

I servizi MDM, ad esempio Microsoft Intune, gestiscono i dispositivi Windows 10 tramite il protocollo MDM. Il client di gestione predefinito in Windows 10 è in grado di comunicare con Intune per eseguire attività di gestione aziendale, promuovendo l'adozione di metodi di gestione moderni nei dispositivi Windows 10. Possono tuttavia rivelarsi necessarie alcune funzionalità, ad esempio la configurazione avanzata dei dispositivi, la risoluzione dei problemi e la gestione di app Win32 legacy, attualmente non disponibili tra le funzioni di gestione MDM di Windows 10. Per avere tali funzionalità, è possibile eseguire il client software Intune nei dispositivi Windows 10. Di conseguenza, non si è in grado di usare le nuove funzionalità offerte dalla gestione MDM di Windows 10. [Esaminare le differenze tra il client software Intune e la funzione di gestione MDM di Windows 10](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

L'estensione di gestione di Intune integra le funzionalità di gestione MDM disponibili in Windows 10. È possibile creare script di PowerShell da eseguire nei dispositivi Windows 10 per ottenere le funzionalità necessarie. È ad esempio possibile creare uno script di PowerShell che consenta di installare un'app Win32 legacy nei dispositivi Windows 10, caricare lo script in Intune, assegnarlo a un gruppo di Azure Active Directory (AD) ed eseguirlo nei dispositivi Windows 10. È quindi possibile monitorare lo stato dell'esecuzione dello script nei dispositivi Windows 10 dall'inizio alla fine.

## <a name="prerequisites"></a>Prerequisiti
L'estensione di gestione di Intune ha i prerequisiti seguenti:
- I dispositivi devono essere stati aggiunti ad Azure AD
- I dispositivi devono eseguire Windows 10 versione 1607 o successiva

## <a name="create-a-powershell-script-policy"></a>Creare un criterio di script di PowerShell 
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Script di PowerShell**.
5. Nel riquadro **Script di PowerShell** scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi uno script di PowerShell** immettere un **Nome** e una **Descrizione** per lo script di PowerShell.
7. In **Percorso dello script** cercare e selezionare lo script di PowerShell. Lo script deve avere dimensioni inferiori a 10 KB (ASCII) o a 5 KB (Unicode).
8. Scegliere **Configura** e quindi scegliere se eseguire lo script con le credenziali dell'utente del dispositivo (**Sì**) o nel contesto di sistema (**No**). Per impostazione predefinita, lo script viene eseguito nel contesto di sistema. Selezionare **Sì**, a meno che non sia necessario eseguire lo script nel contesto di sistema. 
  ![Riquadro Script di PowerShell](./media/mgmt-extension-add-script.png)
9. Scegliere se lo script deve essere firmato da un autore attendibile (**Sì**). Per impostazione predefinita, non è necessario che lo script sia firmato. 
10. Fare clic su **OK** e quindi fare clic su **Crea** per salvare lo script.

## <a name="assign-a-powershell-script-policy"></a>Assegnare un criterio di script di PowerShell
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Script di PowerShell**.
5. Nel riquadro **Script di PowerShell** selezionare lo script da assegnare e quindi scegliere **Gestisci** > **Assegnazioni**.
  ![Riquadro Script di PowerShell](./media/mgmt-extension-assignments.png)
 
6. Scegliere **Seleziona gruppi** per elencare i gruppi di Azure AD disponibili. 
7. Selezionare uno o più gruppi che contengono gli utenti con i dispositivi che riceveranno lo script e quindi fare clic su **Seleziona** per assegnare i criteri ai gruppi selezionati.

L'estensione di gestione di Intune effettua la sincronizzazione con Intune una volta ogni ora. Dopo aver assegnato il criterio ai gruppi di Azure AD, lo script di PowerShell viene eseguito e vengono visualizzati i risultati dell'esecuzione. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Monitorare lo stato di esecuzione degli script di PowerShell
È possibile monitorare lo stato dell'esecuzione degli script di PowerShell per utenti e dispositivi nel portale di Azure.
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Script di PowerShell**.
5. Nel riquadro **Script di PowerShell** selezionare lo script da monitorare e quindi scegliere **Monitoraggio** e uno dei report seguenti:
   - **Stato del dispositivo**
   - **Stato utente**
