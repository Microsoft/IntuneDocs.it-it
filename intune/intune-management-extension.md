---
title: Aggiungere gli script di PowerShell in Microsoft Intune per i dispositivi Windows 10 - Azure | Microsoft Docs
description: Aggiungere script di PowerShell, assegnare il criterio di script ai gruppi di Azure Active Directory, usare i report per monitorare gli script e ottenere informazioni sui passaggi necessari per eliminare gli script aggiunti ai dispositivi Windows 10 in Microsoft Intune. Vedere anche alcuni problemi e risoluzioni comuni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 063a5cbbe18efc5c406c9dc7f2fa40d614b2e48a
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860963"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10

Usare l'estensione di gestione di Intune per caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione di gestione migliora la gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice passare a una gestione moderna.

## <a name="moving-to-modern-management"></a>Passare alla gestione moderna

I computer destinati agli utenti finali stanno attraversando una fase di trasformazione digitale. Le attività IT tradizionali e classiche si occupano di piattaforme su singoli dispositivi, di dispositivi di proprietà dell'azienda, di utenti che lavorano in ufficio e di una serie di processi reattivi manuali. Un'area di lavoro moderna usa più piattaforme di proprietà dell'utente e dell'azienda, consente di lavorare ovunque ci si trovi e mette a disposizione processi IT automatizzati e proattivi.

I servizi MDM, ad esempio Microsoft Intune, possono gestire dispositivi mobili e desktop che eseguono Windows 10. Il client di gestione predefinito in Windows 10 comunica con Intune per eseguire attività di gestione aziendale. Possono rivelarsi necessarie alcune attività, ad esempio la configurazione avanzata dei dispositivi, la risoluzione dei problemi e la gestione di app Win32 legacy, attualmente non disponibili tra le funzioni di gestione MDM di Windows 10. Per avere tali funzionalità, è possibile eseguire il client software Intune nei dispositivi Windows 10. [Confrontare la gestione dei PC Windows come computer o come dispositivi mobili](pc-management-comparison.md) è un'utile risorsa.

L'estensione di gestione di Intune integra le funzionalità di gestione MDM disponibili in Windows 10. È possibile creare script di PowerShell da eseguire nei dispositivi Windows 10. È ad esempio possibile creare uno script di PowerShell che consenta di installare un'app Win32 legacy, caricare lo script in Intune, assegnarlo a un gruppo di Azure Active Directory (AD) ed eseguirlo. È quindi possibile monitorare lo stato dell'esecuzione dello script dall'inizio alla fine.

## <a name="prerequisites"></a>Prerequisiti

L'estensione di gestione di Intune ha i prerequisiti seguenti:

- I dispositivi devono essere stati aggiunti ad Azure AD e [registrati automaticamente](windows-enroll.md#enable-windows-10-automatic-enrollment). L'estensione di gestione di Intune supporta i dispositivi Windows registrati aggiunti ad Azure AD, aggiunti al dominio nella soluzione ibrida e con cogestione. Non sono supportati i dispositivi registrati in oggetti Criteri di gruppo.
- I dispositivi devono eseguire Windows 10 versione 1607 o successiva.
- L'agente dell'estensione di gestione di Intune viene installato quando uno script di PowerShell o un'app Win32 viene distribuita in un gruppo di sicurezza dispositivi o utente.

## <a name="create-a-powershell-script-policy"></a>Creare un criterio di script di PowerShell 

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** > filtrare per **Intune** > selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi**.
3. Immettere un **nome** e una **descrizione** per lo script di PowerShell. In **Percorso dello script** selezionare lo script di PowerShell. Lo script deve avere dimensioni inferiori a 200 KB (ASCII) o a 100 KB (Unicode).
4. Scegliere **Configura**. Quindi scegliere di eseguire lo script con le credenziali dell'utente del dispositivo (**Sì**) o nel contesto di sistema (**No**). Per impostazione predefinita, lo script viene eseguito nel contesto di sistema. Selezionare **Sì**, a meno che non sia necessario eseguire lo script nel contesto di sistema. 
  ![Riquadro Script di PowerShell](./media/mgmt-extension-add-script.png)
5. Scegliere se lo script deve essere firmato da un autore attendibile (**Sì**). Per impostazione predefinita, non è necessario che lo script sia firmato. 
6. Selezionare **OK** e quindi **Crea** per salvare lo script.

## <a name="assign-a-powershell-script-policy"></a>Assegnare un criterio di script di PowerShell

1. In **Script di PowerShell** selezionare lo script da assegnare e quindi scegliere **Gestisci** > **Assegnazioni**.

    ![Riquadro Aggiungi uno script di PowerShell](./media/mgmt-extension-assignments.png)

2. Scegliere **Seleziona gruppi** per elencare i gruppi di Azure AD disponibili. 
3. Selezionare uno o più gruppi che includono gli utenti i cui dispositivi ricevono lo script. Fare clic su **Seleziona** per assegnare il criterio ai gruppi selezionati.

> [!NOTE]
> - Gli script di PowerShell non possono essere applicati a gruppi di computer.
> - Gli utenti finali non devono eseguire l'accesso al dispositivo per eseguire gli script di PowerShell.
> - Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi di Azure AD.

Il client dell'estensione di gestione di Intune effettua il controllo con Intune una volta ogni ora. Dopo aver assegnato il criterio ai gruppi di Azure AD, lo script di PowerShell viene eseguito e vengono visualizzati i risultati dell'esecuzione.

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

## <a name="common-issues-and-resolutions"></a>Problemi e risoluzioni comuni

Gli script di PowerShell non vengono eseguiti a ogni accesso. Vengono eseguiti solo dopo i riavvii di sistema o se viene riavviato il servizio **Microsoft Intune Management Extension**. Il client dell'estensione di gestione di Intune una volta ogni ora verifica la presenza di modifiche nello script o nei criteri di Intune.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: L'estensione di gestione di Intune non viene scaricata

**Risoluzioni possibili**:

- Assicurarsi che i dispositivi siano registrati automaticamente in Azure AD. Per verificarlo, nel dispositivo: 

  1. Passare a **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**.
  2. Selezionare l'account aggiunto > **Informazioni**.
  3. In **Advanced Diagnostic Report** (Report di diagnostica avanzata) selezionare **Crea report**.
  4. Aprire `MDMDiagReport` in un Web browser e passare alla sezione **Enrolled configuration sources** (Origini di configurazione registrate).
  5. Cercare la proprietà **MDMDeviceWithAAD**. Se questa proprietà non esiste, il dispositivo non è registrato automaticamente.

    [Abilitare la registrazione automatica di Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) include i passaggi necessari.

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problema: Gli script di PowerShell non vengono eseguiti

**Risoluzioni possibili**:

- Verificare che l'estensione di gestione di Intune sia stata scaricata in `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Gli script non vengono eseguiti in Surface Hub.
- Verificare la presenza di errori nei log `\ProgramData\Microsoft\IntuneManagementExtension\Logs`.
- Per eventuali problemi di autorizzazione, assicurarsi che le proprietà dello script di PowerShell siano impostate su `Run this script using the logged on credentials`. Verificare anche che l'utente connesso abbia le autorizzazioni appropriate per eseguire lo script.
- Per isolare i problemi di scripting, eseguire uno script di esempio. Creare ad esempio la directory `C:\Scripts` e assegnare a ognuno il controllo completo. Eseguire lo script seguente:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Se l'esecuzione ha esito positivo, verrà creato output.txt che includerà il testo "Script worked".

- Per testare l'esecuzione degli script senza Intune, eseguire gli script nel contesto di sistema usando lo [strumento psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) in locale:

  `psexec -i -s`

## <a name="next-steps"></a>Passaggi successivi

[Monitorare](device-profile-monitor.md) e [risolvere i problemi](device-profile-troubleshoot.md) relativi ai profili.
