---
title: Aggiungere gli script di PowerShell in Microsoft Intune per i dispositivi Windows 10 - Azure | Microsoft Docs
description: Aggiungere script di PowerShell, assegnare il criterio di script ai gruppi di Azure Active Directory, usare i report per monitorare gli script e ottenere informazioni sui passaggi necessari per eliminare gli script aggiunti ai dispositivi Windows 10 in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2c4fb7000d808d860494d2af572c821b42fa6d5c
ms.sourcegitcommit: 77a1047f5d93c1924e5c9ea243454532881be031
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52579184"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10
L'estensione di gestione di Intune consente di caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione di gestione integra le funzionalità di gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice passare a una gestione moderna.

## <a name="moving-to-modern-management"></a>Passare alla gestione moderna
I computer destinati agli utenti finali stanno attraversando una fase di trasformazione digitale. Le attività IT tradizionali e classiche si occupano di piattaforme su singoli dispositivi, di dispositivi di proprietà dell'azienda, di utenti che lavorano in ufficio e di una serie di processi reattivi manuali. Un'area di lavoro moderna, tuttavia, prevede piattaforme su più dispositivi, di proprietà dell'utente finale e dell'azienda, consente di lavorare ovunque ci si trovi e mette a disposizione processi IT automatizzati e proattivi. 

I servizi MDM, ad esempio Microsoft Intune, gestiscono i dispositivi Windows 10 tramite il protocollo MDM. Il client di gestione predefinito in Windows 10 è in grado di comunicare con Intune per eseguire attività di gestione aziendale, promuovendo l'adozione di metodi di gestione moderni nei dispositivi Windows 10. Possono tuttavia rivelarsi necessarie alcune funzionalità, ad esempio la configurazione avanzata dei dispositivi, che non sono disponibili tra le funzioni MDM incorporate di Windows 10.

L'estensione di gestione di Intune integra le funzionalità di gestione MDM disponibili in Windows 10. È possibile creare script di PowerShell da eseguire nei dispositivi Windows 10 per ottenere le funzionalità necessarie. È possibile creare uno script di PowerShell che consenta di configurare le impostazioni personalizzate, caricare lo script in Intune, assegnarlo a un gruppo di Azure Active Directory (AD) ed eseguirlo nei dispositivi Windows 10. Lo script può essere monitorato per valutarne lo stato di esecuzione nei dispositivi Windows 10 dall'inizio alla fine.

## <a name="prerequisites"></a>Prerequisiti
L'estensione di gestione di Intune ha i prerequisiti seguenti:
- I dispositivi devono essere stati aggiunti ad Azure AD. L'estensione di gestione di Intune supporta i dispositivi Windows registrati aggiunti ad Azure Active Directory, aggiunti al dominio nella soluzione ibrida e con cogestione.
- I dispositivi devono eseguire Windows 10 versione 1607 o successiva.
- La registrazione automatica al software MDM deve essere [abilitata in Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) e i dispositivi devono eseguire la registrazione automatica in Intune.

## <a name="create-a-powershell-script-policy"></a>Creare un criterio di script di PowerShell 
1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi**.
4. Immettere un **nome** e una **descrizione** per lo script di PowerShell. In **Percorso dello script** selezionare lo script di PowerShell. Le dimensioni dello script non devono superare i 200 KB (ASCII) o i 100 KB (Unicode).
5. Scegliere **Configura**. Quindi scegliere di eseguire lo script con le credenziali dell'utente del dispositivo (**Sì**) o nel contesto di sistema (**No**). Per impostazione predefinita, lo script viene eseguito nel contesto di sistema. Selezionare **Sì**, a meno che non sia necessario eseguire lo script nel contesto di sistema. 
  ![Riquadro Script di PowerShell](./media/mgmt-extension-add-script.png)
6. Scegliere se lo script deve essere firmato da un autore attendibile (**Sì**). Per impostazione predefinita, non è necessario che lo script sia firmato. 
7. Selezionare **OK** e quindi **Crea** per salvare lo script.

## <a name="assign-a-powershell-script-policy"></a>Assegnare un criterio di script di PowerShell
1. In **Script di PowerShell** selezionare lo script da assegnare e quindi scegliere **Gestisci** > **Assegnazioni**.
  ![Riquadro Script di PowerShell](./media/mgmt-extension-assignments.png)
 
2. Scegliere **Seleziona gruppi** per elencare i gruppi di Azure AD disponibili. 
3. Selezionare uno o più gruppi contenenti gli utenti i cui dispositivi ricevono lo script. Fare clic su **Seleziona** per assegnare il criterio ai gruppi selezionati.

> [!NOTE]
> - Gli utenti finali non devono eseguire l'accesso al dispositivo per eseguire gli script di PowerShell. 
> - Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi AAD.

L'estensione di gestione di Intune effettua la sincronizzazione con Intune una volta ogni ora. Dopo aver assegnato il criterio ai gruppi di Azure AD, lo script di PowerShell viene eseguito e vengono visualizzati i risultati dell'esecuzione. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Monitorare lo stato di esecuzione degli script di PowerShell
È possibile monitorare lo stato dell'esecuzione degli script di PowerShell per utenti e dispositivi nel portale di Azure.

In **Script di PowerShell** selezionare lo script da monitorare, scegliere **Monitoraggio** e quindi uno dei report seguenti:
   - **Stato del dispositivo**
   - **Stato utente**

## <a name="troubleshoot-powershell-scripts"></a>Risolvere i problemi degli script di PowerShell

I log dell'agente nel computer client si trovano in genere in `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. È possibile usare [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) per visualizzare questi file di log. 

![Screenshot dei log dell'agente](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Eliminare uno script di PowerShell
In **Script di PowerShell** fare clic con il pulsante destro del mouse sullo script e selezionare **Elimina**.
