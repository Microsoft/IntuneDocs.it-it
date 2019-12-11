---
title: Scenario guidato - Desktop moderno gestito da cloud
titleSuffix: Microsoft Intune
description: Informazioni sullo scenario guidato per l'installazione e configurazione di un desktop moderno di base dal portale di gestione dei dispositivi per Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74164578"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Scenario guidato - Desktop moderno gestito da cloud

Il desktop moderno è la piattaforma di produttività all'avanguardia per gli Information Worker. Office 365 ProPlus e Windows 10 sono i componenti principali del desktop moderno insieme alle baseline di sicurezza più recenti per Windows 10 e Microsoft Defender Advanced Threat Protection. 

La gestione del desktop moderno dal cloud offre l'ulteriore vantaggio di azioni remote estese a Internet. La gestione cloud usa i criteri di gestione dei dispositivi mobili di Windows predefiniti e rimuove le dipendenze dai Criteri di gruppo di Active Directory locali. 

Se si vuole valutare un desktop moderno gestito dal cloud nella propria organizzazione, questo scenario guidato predefinisce tutte le configurazioni necessarie per una distribuzione di base. In questo scenario guidato verrà creato un ambiente sicuro in cui è possibile provare le funzionalità di gestione dei dispositivi di Intune. 

## <a name="prerequisites"></a>Prerequisiti
- [Impostare l'autorità MDM su Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) - L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.
- Minimo M365 E3 (o M365 E5 per una sicurezza ottimale)
- Dispositivo Windows 10 1903 (registrato con Windows Autopilot per la migliore esperienza utente finale)
- Autorizzazioni di amministratore di Intune necessarie per completare questo scenario guidato:
  - Configurazione del dispositivo: Lettura, Creazione, Eliminazione, Assegnazione e Aggiornamento
  - Programmi di registrazione: lettura del dispositivo, lettura del profilo, creazione del profilo, assegnazione del profilo, eliminazione del profilo
  - App per dispositivi mobili: Lettura, Creazione, Eliminazione, Assegnazione e Aggiornamento
  - Organizzazione: Lettura e Aggiornamento
  - Baseline di sicurezza: Lettura, Creazione, Eliminazione, Assegnazione e Aggiornamento
  - Se di criteri: Lettura, Creazione, Eliminazione, Assegnazione e Aggiornamento

## <a name="step-1---introduction"></a>Passaggio 1 - Introduzione

Questo scenario guidato prevede la configurazione di un utente di test, la registrazione di un dispositivo in Intune e la distribuzione del dispositivo con le impostazioni consigliate di Intune, nonché Windows 10 e Office ProPlus. Se si sceglie di [abilitare questa protezione in Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune), il dispositivo verrà configurato anche per Microsoft Defender Advanced Threat Protection. L'utente configurato e il dispositivo da registrare verranno aggiunti a un nuovo gruppo di sicurezza e verranno configurati con le impostazioni consigliate per la sicurezza e la produttività. 

### <a name="what-you-will-need-to-continue"></a>Cosa serve per continuare

In questo scenario guidato è necessario fornire il dispositivo di test e l'utente di test. Assicurarsi di completare le attività seguenti:
- Configurare un account utente di test in Azure Active Directory.
- Creare un dispositivo di test che esegue Windows 10 versione 1903 o versione successiva.
- (Facoltativo) [Registrare il dispositivo di test in Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices).
- (Facoltativo) Abilitare le [informazioni personalizzate distintive dell'azienda nella pagina di accesso di Azure Active Directory dell'organizzazione](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Passaggio 2 - Utente

Scegliere un utente da configurare nel dispositivo. Questa persona sarà l'utente primario del dispositivo.

Se si vogliono aggiungere altri utenti o dispositivi a questa configurazione, è sufficiente aggiungere gli utenti e i dispositivi ai gruppi di sicurezza AAD generati dalla procedura guidata. A differenza di altri scenari guidati, non è necessario eseguire la procedura guidata più di una volta, poiché la configurazione non è personalizzabile. È sufficiente aggiungere altri utenti e dispositivi ai gruppi AAD creati. Al termine della procedura guidata, sarà possibile visualizzare il gruppo generato con i criteri consigliati distribuiti. 

## <a name="step-3---device"></a>Passaggio 3 - Dispositivo

Verificare che nel dispositivo sia in esecuzione Windows 10, versione 1903 o successiva.  L'utente primario dovrà configurare il dispositivo al momento della ricezione. Sono disponibili due opzioni di configurazione per l'utente. 

### <a name="option-a--windows-autopilot"></a>Opzione A - Windows Autopilot
Windows Autopilot consente di automatizzare la configurazione dei nuovi dispositivi, in modo che gli utenti possano procedere senza assistenza IT. Se il dispositivo è già registrato in Windows Autopilot, selezionarlo in base al numero di serie. Per altre informazioni sull'uso di Windows Autopilot, vedere [Registrare il dispositivo in Windows Autopilot (facoltativo)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Opzione B - Registrazione manuale del dispositivo
Gli utenti possono configurare e registrare manualmente i nuovi dispositivi nella gestione dei dispositivi mobili. Al termine di questo scenario, reimpostare il dispositivo e fornire all'utente primario le istruzioni di registrazione per i dispositivi Windows. Per altre informazioni, vedere [Per aggiungere un dispositivo Windows 10 ad Azure AD in fase di completamento dell'installazione](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Passaggio 4 - Verifica e creazione

Il passaggio finale consente di esaminare un riepilogo delle impostazioni configurate. Dopo aver verificato le scelte, fare clic su **Distribuisci** per completare lo scenario guidato. Una volta completato lo scenario guidato, viene visualizzata una tabella di risorse. È possibile modificare queste risorse in un secondo momento, ma quando si esce dalla visualizzazione di riepilogo la tabella non verrà salvata.

> [!IMPORTANT]
> Una volta completato lo scenario guidato, verrà visualizzato un riepilogo. È possibile modificare le risorse elencate nel riepilogo in un secondo momento, ma la tabella che visualizza queste risorse non verrà salvata.

### <a name="verification"></a>Verifica
1. Verificare che sia assegnato l'ambito utente MDM
    - Assicurarsi che [Ambito utente MDM](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) sia:
        - Impostato su **Tutti** per l'app **Microsoft Intune** o,
        - Impostato su **In parte**. Inoltre, aggiungere il gruppo di utenti creato da questo scenario guidato.
2. Verificare che l'utente selezionato sia in grado di aggiungere dispositivi ad Azure Active Directory.
    - Verificare che l'aggiunta ad AAD sia:
        - Impostata su **Tutti** o
        - Impostata su **In parte**. Aggiungere anche il gruppo di utenti creato da questo scenario guidato.
3. Seguire i passaggi appropriati nel dispositivo per aggiungerlo ad Azure AD in base a quanto segue:
    - Con Autopilot. Per altre informazioni, vedere [Modalità definita dall'utente di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Senza Autopilot: Per altre informazioni, vedere [Per aggiungere un dispositivo Windows 10 ad Azure AD in fase di completamento dell'installazione](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>Cosa accade quando si fa clic su Distribuisci?
L'utente e il dispositivo verranno aggiunti ai nuovi gruppi di sicurezza. Verranno anche configurati con le impostazioni consigliate di Intune per la sicurezza e la produttività nell'ambiente aziendale o dell'istituto di istruzione. Dopo che l'utente ha aggiunto il dispositivo ad Azure AD, al dispositivo verranno aggiunte ulteriori app e impostazioni. Per altre informazioni su queste configurazioni aggiuntive, vedere [Avvio rapido: Registrare il dispositivo Windows 10](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Informazioni aggiuntive

### <a name="register-device-with-windows-autopilot-optional"></a>Registrare il dispositivo in Windows Autopilot (facoltativo)

Facoltativamente, è possibile scegliere di usare un dispositivo Autopilot registrato. Per Autopilot, questo scenario guidato assegnerà un profilo di distribuzione Autopilot e un profilo della pagina dello stato della registrazione. Il profilo di distribuzione Autopilot verrà configurato come segue:
- Modalità definita dall'utente, ovvero con richiesta all'utente finale di immettere il nome utente e la password durante l'installazione di Windows.
- Aggiunta ad Azure AD.
- Personalizzare l'installazione di Windows:
  - Nascondere la schermata relativa alle condizioni di licenza software Microsoft
  - Nascondere le impostazioni di privacy 
  - Creare il profilo locale dell'utente senza privilegi di amministratore locale
  - Nascondere le opzioni Cambia account nella pagina di accesso aziendale

La pagina relativa allo stato della registrazione verrà configurata in modo da essere abilitata solo per i dispositivi Autopilot e non verrà bloccata in attesa dell'installazione di tutte le app.

Lo scenario guidato prevede anche l'assegnazione dell'utente al dispositivo Autopilot selezionato per un'esperienza di installazione personalizzata.

#### <a name="post-requisites"></a>Post-requisiti
Dopo che l'utente ha aggiunto il dispositivo ad Azure Active Directory, al dispositivo verranno applicate le configurazioni seguenti:
1. Office 365 ProPlus verrà installato automaticamente nel computer gestito dal cloud. Include applicazioni note, ovvero Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype for Business e Word. È possibile usare queste applicazioni per connettersi ai servizi di Office 365, ad esempio SharePoint Online, Exchange Online e Skype for Business Online. Office 365 ProPlus viene aggiornato regolarmente con nuove funzionalità, a differenza delle versioni non in abbonamento di Office. Per un elenco delle nuove funzionalità, vedere Novità di Office 365.
2. Le baseline di sicurezza di Windows verranno installate nel PC gestito dal cloud. Se è stato configurato Microsoft Defender Advanced Threat Protection, nello scenario guidato verranno configurate anche le impostazioni di base per Defender. Defender Advanced Threat Protection rende disponibile un nuovo livello di protezione post-violazione nello stack di sicurezza di Windows 10. Grazie a una combinazione di tecnologia client integrata in Windows 10 e un servizio cloud affidabile, consentirà di rilevare le minacce che hanno superato altre difese. 

## <a name="next-steps"></a>Passaggi successivi

- Se si usa Microsoft Defender Advanced Threat Detection, creare [criteri di conformità di Intune](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) per richiedere l'analisi delle minacce di Defender per ottenere la conformità.
- Creare [criteri di accesso condizionale basato sul dispositivo](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) per bloccare l'accesso se il dispositivo non risulta conforme a Intune.
