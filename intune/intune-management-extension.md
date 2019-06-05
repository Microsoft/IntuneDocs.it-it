---
title: Aggiungere script di PowerShell ai dispositivi Windows 10 in Microsoft Intune | Microsoft Docs
description: Creare ed eseguire script di PowerShell, assegnare i criteri di script ai gruppi di Azure Active Directory, usare i report per monitorare gli script e ottenere informazioni sui passaggi necessari per eliminare gli script aggiunti ai dispositivi Windows 10 in Microsoft Intune. Vedere anche alcuni problemi e risoluzioni comuni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f17bdf21db61616f88cef4d257fbcd28d941dae8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373463"
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

L'estensione di gestione di Intune ha i prerequisiti seguenti. Dopo che questi prerequisiti sono soddisfatti, l'estensione di gestione di Intune viene installata automaticamente quando uno script di PowerShell o un'app Win32 viene assegnata all'utente o al dispositivo.

- Dispositivi che eseguono Windows 10 versione 1607 o successiva. Se il dispositivo viene registrato tramite la [registrazione automatica in blocco](windows-bulk-enroll.md), i dispositivi devono eseguire Windows 10 versione 1703 o successiva. L'estensione di gestione di Intune non è supportata in Windows 10 in modalità S, perché la modalità S non consente l'esecuzione di app non dello Store. 
  
- Dispositivi aggiunti ad Azure Active Directory (AD), tra cui:
  
  - Aggiunti ad Azure AD ibrido: Dispositivi aggiunti ad Azure Active Directory (AD) e anche ad Active Directory (AD) locale. Per informazioni aggiuntive, vedere [Pianificare l'implementazione dell'aggiunta ad Azure Active Directory ibrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).

- Dispositivi registrati in Intune, tra cui:

  - Dispositivi registrati in un oggetto Criteri di gruppo (GPO). Per informazioni aggiuntive, vedere [Enroll a Windows 10 device automatically using Group Policy](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) (Registrare un dispositivo Windows 10 automaticamente tramite Criteri di gruppo).
  
  - Dispositivi registrati in Intune manualmente, ovvero quando:
  
    - L'utente esegue l'accesso al dispositivo usando un account utente locale e quindi aggiunge manualmente il dispositivo ad Azure AD (e la registrazione automatica in Intune è abilitata in Azure AD).
    
    Oppure
    
    - L'utente esegue l'accesso al dispositivo usando il proprio account Azure AD e quindi esegue la registrazione in Intune.

  - Dispositivi con co-gestione che usano Configuration Manager e Intune. Per informazioni aggiuntive, vedere [Informazioni sulla co-gestione](https://docs.microsoft.com/sccm/comanage/overview).

## <a name="create-a-script-policy"></a>Creare criteri di script 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
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

> [!NOTE]
> Lo script di PowerShell viene eseguito con privilegi di amministratore (per impostazione predefinita) quando è impostato sul contesto utente e l'utente finale del dispositivo dispone di privilegi amministrativi.

## <a name="assign-the-policy"></a>Assegnare i criteri

1. In **Script di PowerShell** selezionare lo script da assegnare e quindi scegliere **Gestisci** > **Assegnazioni**.

    ![Assegnare o distribuire lo script di PowerShell a gruppi di dispositivi in Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Scegliere **Seleziona gruppi** per elencare i gruppi di Azure AD disponibili. 
3. Selezionare uno o più gruppi che includono gli utenti i cui dispositivi ricevono lo script. Fare clic su **Seleziona** per assegnare il criterio ai gruppi selezionati.

> [!NOTE]
> - Gli utenti finali non devono eseguire l'accesso al dispositivo per eseguire gli script di PowerShell.
> - Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi di Azure AD o ai gruppi di sicurezza degli utenti di Azure AD.

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

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: L'estensione di gestione di Intune non viene scaricata

**Risoluzioni possibili**:

- Il dispositivo non è stato aggiunto ad Azure AD. Verificare che i dispositivi soddisfino i [prerequisiti](#prerequisites) (elencati in questo articolo). 
- Nessuna app Win32 o script di PowerShell è assegnato ai gruppi ai quali appartiene l'utente o dispositivo.
- Il dispositivo non è in grado di eseguire il check-in con il servizio Intune perché non è disponibile l'accesso a Internet, l'accesso a Windows Push Notification Services (WNS) e così via.
- Il dispositivo è in modalità S. L'estensione di gestione di Intune non è supportata nei dispositivi in esecuzione in modalità S. 

Per vedere se il dispositivo è registrato automaticamente, è possibile:

  1. Passare a **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**.
  2. Selezionare l'account aggiunto > **Informazioni**.
  3. In **Advanced Diagnostic Report** (Report di diagnostica avanzata) selezionare **Crea report**.
  4. Aprire `MDMDiagReport` in un Web browser.
  5. Cercare la proprietà **MDMDeviceWithAAD**. Se la proprietà esiste, il dispositivo è registrato automaticamente. Se la proprietà non esiste, il dispositivo non è registrato automaticamente.

[Abilitare la registrazione automatica di Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) include la procedura per configurare la registrazione automatica in Intune.

#### <a name="issue-powershell-scripts-do-not-run"></a>Problema: Gli script di PowerShell non vengono eseguiti

**Risoluzioni possibili**:

- Gli script di PowerShell non vengono eseguiti a ogni accesso. Vengono eseguiti:

  - Quando lo script viene assegnato a un dispositivo
  - Se si modifica lo script, lo si carica e lo si assegna a un utente o un dispositivo
  
    > [!TIP]
    > L'**estensione di gestione di Microsoft Intune** è un servizio che viene eseguito sul dispositivo esattamente come qualsiasi altro servizio elencato nell'app Servizi (services.msc). Dopo il riavvio di un dispositivo è possibile che anche questo servizio venga riavviato e verifichi la presenza di eventuali script PowerShell assegnati con il servizio Intune. Se il servizio **estensione di gestione di Microsoft Intune** è impostato su Manuale, potrebbe non essere riavviato dopo il riavvio del dispositivo.

- Il client dell'estensione di gestione di Intune verifica ogni ora la presenza di modifiche nello script o nei criteri di Intune.
- Verificare che l'estensione di gestione di Intune sia stata scaricata in `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Gli script non vengono eseguiti in Surface Hub o in Windows 10 in modalità S.
- Verificare la presenza di eventuali errori nei log. Vedere [Risolvere i problemi relativi agli script](#troubleshoot-scripts) in questo articolo.
- Per eventuali problemi di autorizzazione, assicurarsi che le proprietà dello script di PowerShell siano impostate su `Run this script using the logged on credentials`. Verificare anche che l'utente connesso abbia le autorizzazioni appropriate per eseguire lo script.

- Per isolare i problemi di scripting seguire questa procedura:

  - Esaminare la configurazione di esecuzione di PowerShell nei dispositivi. Per informazioni aggiuntive, vedere [Criteri di esecuzione di PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6).
  - Eseguire uno script di esempio con l'estensione di gestione di Intune. Creare ad esempio la directory `C:\Scripts` e assegnare a ognuno il controllo completo. Eseguire lo script seguente:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Se l'esecuzione ha esito positivo, verrà creato output.txt che includerà il testo "Script worked".

  - Per testare l'esecuzione degli script senza Intune, eseguire gli script nell'account di sistema usando lo [strumento psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) in locale:

    `psexec -i -s`

## <a name="next-steps"></a>Passaggi successivi

[Monitorare](device-profile-monitor.md) e [risolvere i problemi](device-profile-troubleshoot.md) relativi ai profili.
