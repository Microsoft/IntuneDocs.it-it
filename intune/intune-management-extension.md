---
title: Aggiungere script di PowerShell ai dispositivi Windows 10 in Microsoft Intune | Microsoft Docs
description: Creare ed eseguire script di PowerShell, assegnare i criteri di script ai gruppi di Azure Active Directory, usare i report per monitorare gli script e ottenere informazioni sui passaggi necessari per eliminare gli script aggiunti ai dispositivi Windows 10 in Microsoft Intune. Vedere anche alcuni problemi e risoluzioni comuni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66a23b75913f6465064a988bd8f2ba9c2b4c36d6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514140"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Usare gli script di PowerShell nei dispositivi Windows 10 in Intune

Usare l'estensione di gestione di Microsoft Intune per caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione di gestione migliora la gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice passare a una gestione moderna.

Questa funzionalità si applica a:

- Windows 10 e versioni successive

## <a name="move-to-modern-management"></a>Passare alla gestione moderna

I computer destinati agli utenti finali stanno attraversando una fase di trasformazione digitale. Le attività IT tradizionali e classiche si occupano di singole piattaforme di dispositivi, dispositivi di proprietà dell'azienda, utenti che lavorano in ufficio e diversi processi IT reattivi manuali. Un'area di lavoro moderna usa più piattaforme di proprietà dell'utente e dell'azienda, consente di lavorare ovunque ci si trovi e mette a disposizione processi IT automatizzati e proattivi.

I servizi MDM, ad esempio Microsoft Intune, possono gestire dispositivi mobili e desktop che eseguono Windows 10. Il client di gestione predefinito in Windows 10 comunica con Intune per eseguire attività di gestione aziendale. Potrebbe essere necessario eseguire alcune attività come la configurazione avanzata dei dispositivi e la risoluzione dei problemi. Per la gestione delle app Win32, è possibile usare la funzionalità di [gestione delle app Win32](apps-win32-app-management.md) nei dispositivi Windows 10.

L'estensione di gestione di Intune integra le funzionalità di gestione MDM disponibili in Windows 10. È possibile creare script di PowerShell da eseguire nei dispositivi Windows 10. È ad esempio possibile creare uno script di PowerShell che esegue le configurazioni avanzate dei dispositivi, carica lo script in Intune, lo assegna a un gruppo di Azure Active Directory (AD) e lo esegue. È quindi possibile monitorare lo stato dell'esecuzione dello script dall'inizio alla fine.

## <a name="prerequisites"></a>Prerequisiti

L'estensione di gestione di Intune ha i prerequisiti seguenti:

- I dispositivi devono essere aggiunti o registrati in Azure AD e Azure AD e Intune devono essere configurati per la [registrazione automatica](quickstart-setup-auto-enrollment.md). L'estensione di gestione di Intune supporta i dispositivi Windows registrati e cogestiti, aggiunti ad Azure AD e aggiunti al dominio di Azure AD ibrido.
- I dispositivi devono eseguire Windows 10 versione 1607 o successiva.
- L'agente dell'estensione di gestione di Intune viene installato quando uno script di PowerShell o un'app Win32 viene distribuita in un gruppo di sicurezza dispositivi o utente.

## <a name="create-a-script-policy"></a>Creare criteri di script 

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi**.
3. Immettere le proprietà seguenti:
    - **Nome**: immettere un nome per lo script di PowerShell. 
    - **Description**: immettere una descrizione per lo script di PowerShell. Questa impostazione è facoltativa ma consigliata. 
    - **Percorso dello script**: passare allo script di PowerShell. Lo script deve avere dimensioni inferiori a 200 KB (ASCII).
4. Scegliere **Configura** e immettere le proprietà seguenti:
    - **Esegui lo script con le credenziali dell'utente connesso**: selezionare **Sì** per eseguire lo script con le credenziali dell'utente nel dispositivo. Scegliere **No** (impostazione predefinita) per eseguire lo script nel contesto di sistema. Molti amministratori scelgono **Sì**. Se è necessario eseguire lo script nel contesto di sistema, scegliere **No**.
    - **Imponi il controllo della firma degli script**: selezionare **Sì** se lo script deve essere firmato da un autore attendibile. Selezionare **No** (impostazione predefinita) se non è necessario che lo script sia firmato. 
    - **Esegui lo script in un host di PowerShell a 64 bit**: selezionare **Sì** per eseguire lo script in un host di PowerShell a 64 bit in un'architettura client a 64 bit. Selezionare **No** (impostazione predefinita) per eseguire lo script in un host di PowerShell a 32 bit.

      Quando si imposta l'opzione su **Sì** o **No**, fare riferimento alla tabella seguente per il comportamento dei criteri nuovi ed esistenti:

      | Esegui lo script in un host di PowerShell a 64 bit | Architettura client | Nuovo script di PowerShell | Script dei criteri di PowerShell esistente |
      | --- | --- | --- | --- | 
      | No | 32 bit  | Host di PowerShell a 32 bit supportato | L'esecuzione avviene solo nell'host di PowerShell a 32 bit, che funziona su architetture a 32 bit e a 64 bit. |
      | Sì | 64 bit | Lo script viene eseguito nell'host di PowerShell a 64 bit per le architetture a 64 bit. Quando l'esecuzione avviene su piattaforme a 32 bit, lo script viene eseguito in un host di PowerShell a 32 bit. | Lo script viene eseguito in un host a 32 bit. Se questa impostazione viene modificata con l'opzione a 64 bit, lo script viene aperto (non eseguito) in un host di PowerShell a 64 bit e vengono visualizzati i risultati. Quando l'esecuzione avviene su piattaforme a 32 bit, lo script viene eseguito in un host di PowerShell a 32 bit. |

    ![Aggiungere e usare script di PowerShell in Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Selezionare **OK** > **Crea** per salvare lo script.

## <a name="assign-the-policy"></a>Assegnare i criteri

1. In **Script di PowerShell** selezionare lo script da assegnare e quindi scegliere **Gestisci** > **Assegnazioni**.

    ![Assegnare o distribuire lo script di PowerShell a gruppi di dispositivi in Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Scegliere **Seleziona gruppi** per elencare i gruppi di Azure AD disponibili. 
3. Selezionare uno o più gruppi che includono gli utenti i cui dispositivi ricevono lo script. Fare clic su **Seleziona** per assegnare il criterio ai gruppi selezionati.

> [!NOTE]
> - Gli utenti finali non devono eseguire l'accesso al dispositivo per eseguire gli script di PowerShell.
> - Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi di Azure AD.
> - Gli script di PowerShell in Intune possono essere destinati ai gruppi sicurezza utente di Azure AD.

Il client dell'estensione di gestione di Intune effettua il controllo una volta ogni ora e dopo ogni riavvio con Intune per verificare la presenza di nuovi script o di modifiche. Dopo aver assegnato il criterio ai gruppi di Azure AD, lo script di PowerShell viene eseguito e vengono visualizzati i risultati dell'esecuzione. Dopo essere stato eseguito, lo script non viene eseguito di nuovo a meno che non venga apportata una modifica allo script o ai criteri.

## <a name="monitor-run-status"></a>Monitorare lo stato di esecuzione

È possibile monitorare lo stato dell'esecuzione degli script di PowerShell per utenti e dispositivi nel portale di Azure.

In **Script di PowerShell** selezionare lo script da monitorare, scegliere **Monitoraggio** e quindi uno dei report seguenti:

- **Stato del dispositivo**
- **Stato utente**

## <a name="troubleshoot-scripts"></a>Risolvere i problemi relativi agli script

I log dell'agente nel computer client si trovano in genere in `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. È possibile usare [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) per visualizzare questi file di log. 

![Screenshot di log dell'agente cmtrace di esempio in Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Eliminare uno script

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

#### <a name="issue-powershell-scripts-do-not-run"></a>Problema: Gli script di PowerShell non vengono eseguiti

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
