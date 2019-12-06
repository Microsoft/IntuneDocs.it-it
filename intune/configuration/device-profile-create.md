---
title: Creare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare un profilo di configurazione del dispositivo in Microsoft Intune. Selezionare il tipo di piattaforma, configurare le impostazioni e aggiungere un tag di ambito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c4c995322234a4a2486d8e6c5e9efd88f78dd63
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390878"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creare un profilo di dispositivo in Microsoft Intune

I profili di dispositivo consentono di aggiungere e configurare impostazioni e quindi di eseguire il push di queste impostazioni nei dispositivi dell'organizzazione. Per informazioni più dettagliate e procedure, vedere [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](device-profiles.md).

Questo articolo:

- Elenca i passaggi da eseguire per creare un profilo.
- Illustra come aggiungere un tag di ambito per "filtrare" il profilo.
- Descrive le regole di applicabilità nei dispositivi Windows 10 e illustra come creare una regola.
- Elenca la frequenza dei cicli di aggiornamento quando i dispositivi ricevono i profili e i relativi aggiornamenti.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione**. Sono disponibili le seguenti opzioni:

    - **Panoramica**: elenca lo stato dei profili e offre dettagli aggiuntivi sui profili assegnati a utenti e dispositivi.
    - **Gestione**: consente di creare profili di dispositivo, caricare [script di PowerShell](../apps/intune-management-extension.md) personalizzati da eseguire all'interno del profilo e di aggiungere piani dati ai dispositivi che usano [eSIM](esim-device-configuration.md).
    - **Monitoraggio**: consente di verificare lo stato di un profilo e le operazioni riuscite e non riuscite, nonché di visualizzare i log per i profili.
    - **Configurazione**: aggiungere un'autorità di certificazione SCEP o PFX o abilitare [Gestione delle spese per telecomunicazioni](telecom-expenses-monitor.md) nel profilo.

3. Selezionare **Crea profilo**. Immettere le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di profilo è **Profilo di posta elettronica WP per l'intera azienda**.
   - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

   - **Tipo di profilo**: selezionare il tipo di impostazioni da creare. L'elenco visualizzato dipende dalla **piattaforma** scelta.
   - **Impostazioni**: Gli articoli seguenti descrivono le impostazioni per ogni tipo di profilo:

       - [Modelli amministrativi](administrative-templates-windows.md)
       - [Personalizzato](../custom-settings-configure.md)
       - [Ottimizzazione recapito](../delivery-optimization-windows.md)
       - [Funzionalità dei dispositivi](../device-features-configure.md)
       - [Restrizioni dei dispositivi](device-restrictions-configure.md)
       - [Aggiornamento dell'edizione e cambio di modalità](edition-upgrade-configure-windows-10.md)
       - [Istruzione](education-settings-configure.md)
       - [Posta elettronica](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Protezione dell'identità](../protect/identity-protection-configure.md)  
       - [Modalità tutto schermo](kiosk-settings.md)
       - [Certificato PKCS](../protect/certficates-pfx-configure.md)
       - [Certificato importato PKCS](../protect/certificates-imported-pfx-configure.md)
       - [File delle preferenze](preference-file-settings-macos.md)
       - [Certificato SCEP](../protect/certificates-scep-configure.md)
       - [Certificato attendibile](../protect/certificates-configure.md)
       - [Criteri di aggiornamento](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     Se ad esempio si seleziona come piattaforma **iOS/iPadOS**, le opzioni del tipo di profilo sono simili a quelle del profilo seguente:

     ![Creare un profilo iOS in Intune](./media/device-profile-create/create-device-profile.png)

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche. Il profilo viene creato e visualizzato nell'elenco.

## <a name="scope-tags"></a>Tag di ambito

Dopo aver aggiunto le impostazioni, si può anche aggiungere un tag di ambito al profilo. I tag di ambito assegnano e filtrano criteri a gruppi specifici, ad esempio il reparto Risorse umane o i dipendenti di una filiale.

Per altre informazioni sui tag di ambito e le relative procedure, vedere [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

### <a name="add-a-scope-tag"></a>Aggiungere un tag di ambito

1. Selezionare **Ambito (tag)** .
2. Selezionare **Aggiungi** per creare un nuovo tag di ambito. Oppure selezionare un tag di ambito esistente dall'elenco.
3. Selezionare **OK** per salvare le modifiche.

## <a name="applicability-rules"></a>Regole di applicabilità

Si applica a:

- Windows 10 e versioni successive

Le regole di applicabilità consentono agli amministratori di fare riferimento a dispositivi in un gruppo che soddisfano criteri specifici. Ad esempio, si crea un profilo di restrizioni del dispositivo che si applica al gruppo **Tutti i dispositivi Windows 10**. Si vuole che il profilo venga assegnato solo ai dispositivi che eseguono Windows 10 Enterprise.

Per eseguire questa attività, creare una **regola di applicabilità**. Queste regole sono utili per gli scenari seguenti:

- Si usa Windows 10 Education (EDU). Nel Bellows College, l'obiettivo è raggiungere tutti i dispositivi Windows 10 EDU con versioni comprese tra RS3 e RS4.
- In Contoso si vuole raggiungere tutti gli utenti del reparto Risorse umane, ma solo i dispositivi con Windows 10 Professional o Enterprise.

Per affrontare questi scenari, è necessario:

- Creare un gruppo di dispositivi che include tutti i dispositivi del Bellows College. Nel profilo aggiungere una regola di applicabilità che viene implementata se la versione minima del sistema operativo è `16299` e la versione massima è `17134`. Assegnare questo profilo al gruppo di dispositivi del Bellows College.

  Quando viene assegnato, il profilo viene applicato ai dispositivi con una versione compresa tra la versione minima e la versione massima specificate. Per i dispositivi la cui versione non è inclusa tra le versioni minima e massima specificate, lo stato visualizzato è **Non applicabile**.

- Creare un gruppo di utenti che include tutti gli utenti del reparto Risorse umane (HR) di Contoso. Nel profilo aggiungere una regola di applicabilità che seleziona i dispositivi che eseguono Windows 10 Professional o Enterprise. Assegnare questo profilo al gruppo di utenti HR.

  Quando viene assegnato, il profilo si applica ai dispositivi che eseguono Windows 10 Professional o Enterprise. Per i dispositivi che non eseguono queste edizioni, lo stato visualizzato è **Non applicabile**.

- Se sono presenti due profili con le stesse impostazioni esatte, viene applicato il profilo che non include una regola di applicabilità. 

  Ad esempio, ProfileA è destinato al gruppo dispositivi Windows 10, abilita BitLocker e non ha una regola di applicabilità. ProfileB è destinato allo stesso gruppo di dispositivi Windows 10, abilita BitLocker e ha una regola di applicabilità per cui il profilo viene applicato solo a Windows 10 Enterprise.

  Quando sono assegnati entrambi i profili viene applicato ProfileA, perché non ha una regola di applicabilità. 

Quando si assegna il profilo ai gruppi, le regole di applicabilità fanno da filtro e si applicano solo i dispositivi che soddisfano i criteri.

### <a name="add-a-rule"></a>Aggiungere una regola

1. Selezionare **Regole di applicabilità**. È possibile scegliere le impostazioni **Regola**, **Proprietà** e **Edizione del sistema operativo**:

    ![Aggiungere una regola di applicabilità a un profilo di configurazione del dispositivo in Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. In **Regola** scegliere se si vuole includere o escludere utenti o gruppi. Le opzioni disponibili sono:

    - **Assegna un profilo se**: include utenti o gruppi che soddisfano i criteri immessi.
    - **Non assegnare un profilo se**: esclude utenti o gruppi che soddisfano i criteri immessi.

3. In **Proprietà** scegliere il filtro. Le opzioni disponibili sono: 

    - **Edizione del sistema operativo**: nell'elenco selezionare le edizioni di Windows 10 che si vuole includere (o escludere) nella regola.
    - **Versione del sistema operativo**: immettere i numeri di versione **Min** e **Max** di Windows 10 che si vuole includere (o escludere) nella regola. Entrambi i valori sono obbligatori.

      Ad esempio è possibile immettere `10.0.16299.0` (RS3 o 1709) per la versione minima e `10.0.17134.0` (RS4 o 1803) per la versione massima. In alternativa è possibile adottare una granularità maggiore e immettere `10.0.16299.001` per la versione minima e `10.0.17134.319` per la versione massima.

4. Selezionare **Aggiungi** per salvare le modifiche.

## <a name="refresh-cycle-times"></a>Frequenza dei cicli di aggiornamento

Intune usa cicli di aggiornamento diversi per verificare la disponibilità di aggiornamenti per i profili di configurazione. Se il dispositivo è stato registrato di recente, il controllo viene eseguito con maggiore frequenza. [Cicli di aggiornamento di criteri e profili](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) elenca i tempi di aggiornamento stimati.

Gli utenti possono aprire in qualsiasi momento l'app Portale aziendale e sincronizzare il dispositivo per controllare immediatamente la disponibilità di aggiornamenti del profilo.

## <a name="recommendations"></a>Indicazioni

Durante la creazione dei profili, tenere presenti le indicazioni seguenti:

- Assegnare un nome ai criteri in modo da sapere quali sono e qual è la loro funzione. Tutti i [criteri di conformità](../protect/create-compliance-policy.md) e i [profili di configurazione](../configuration/device-profile-create.md) hanno una proprietà **Descrizione** facoltativa. In **Descrizione** immettere informazioni specifiche che consentano agli altri utenti di individuare la funzione dei criteri.

  Di seguito alcuni esempi di profilo di configurazione:

  **Nome profilo**: Modello amministrativo: profilo di configurazione OneDrive per tutti gli utenti di Windows 10  
  **Descrizione profilo**: Profilo del modello amministrativo di OneDrive che include le impostazioni minime e di base per tutti gli utenti di Windows 10. Creato da user@contoso.com per impedire agli utenti di condividere i dati dell'organizzazione con account OneDrive personali.

  **Nome profilo**: Profilo VPN per tutti gli utenti iOS  
  **Descrizione profilo**: Profilo VPN che include le impostazioni minime e di base per tutti gli utenti iOS per connettersi alla VPN Contoso. Creato da user@contoso.com in modo che gli utenti eseguano automaticamente l'autenticazione alla VPN, anziché richiedere loro nome utente e password.

- Creare il profilo in base all'attività, ad esempio configurare le impostazioni di Microsoft Edge, abilitare le impostazioni antivirus di Microsoft Defender, bloccare i dispositivi iOS jailbroken e così via.

- Creare profili che si applicano a gruppi specifici, ad esempio marketing, vendite, amministratori IT o in base alla posizione o al sistema dell'istituto di istruzione.

- Separare i criteri utente dai criteri del dispositivo.

  Ad esempio [Modelli amministrativi in Intune](administrative-templates-windows.md) contiene centinaia di impostazioni ADMX. Questo modello indica se le impostazioni si applicano a utenti o dispositivi. Quando si creano modelli amministrativi, assegnare le impostazioni degli utenti a un gruppo di utenti e assegnare le impostazioni dei dispositivi a un gruppo di dispositivi.

  Nell'immagine seguente viene illustrato un esempio di impostazione che può essere applicata agli utenti e/o ai dispositivi:

  ![Modello amministrativo di Intune applicato a utenti e dispositivi](./media/device-profile-create/setting-applies-to-user-and-device.png)

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
