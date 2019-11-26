---
title: Risoluzione dei problemi di registrazione dei dispositivi iOS in Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggerimenti per la risoluzione di alcuni dei problemi più comuni quando si registrano i dispositivi iOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e71ae2d2bcee22040c256ea711edd22b1d1fc80a
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199281"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Risolvere i problemi di registrazione dei dispositivi iOS in Microsoft Intune

Questo articolo aiuta gli amministratori di Intune a comprendere e risolvere i problemi durante la registrazione dei dispositivi iOS in Intune.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare la risoluzione dei problemi, è importante raccogliere alcune informazioni di base. Queste informazioni possono essere utili per comprendere meglio il problema e ridurre il tempo necessario per trovare una soluzione.

Raccogliere le seguenti informazioni sul problema:

- Qual è il messaggio di errore esatto?
- Dove viene visualizzato il messaggio di errore?
- Quando è iniziato il problema? La registrazione è già stata elaborata?
- Quale piattaforma (Android, iOS, Windows) presenta il problema?
- Quanti utenti sono interessati? Tutti gli utenti sono interessati o solo alcuni?
- Quanti dispositivi sono interessati? Tutti i dispositivi sono interessati o solo alcuni?
- Che cos'è l'autorità MDM? Se è System Center Configuration Manager, quale versione di Configuration Manager si sta usando?
- Come viene eseguita la registrazione? BYOD (Bring Your Own Device) o Apple Device Enrollment Program (DEP) con i profili di registrazione?

## <a name="error-messages"></a>Messaggi di errore

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Installazione profilo non riuscita. Si è verificato un errore di rete.

**Motivo:** Si è verificato un problema non specificato con iOS nel dispositivo.

#### <a name="resolution"></a>Soluzione

1. Per evitare la perdita di dati nei passaggi seguenti (il ripristino di iOS Elimina tutti i dati nel dispositivo), assicurarsi di eseguire il backup dei dati.
2. Impostare il dispositivo in modalità di ripristino e quindi ripristinarlo. Assicurarsi di configurarlo come nuovo dispositivo. Per ulteriori informazioni su come ripristinare i dispositivi iOS, vedere [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Registrare nuovamente il dispositivo.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Installazione profilo non riuscita. Non è stato possibile stabilire una connessione al server.

**Motivo:** Il tenant di Intune è configurato per consentire solo i dispositivi di proprietà dell'azienda. 

#### <a name="resolution"></a>Soluzione
1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare Intune e quindi selezionare **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **restrizioni sul tipo di dispositivo**selezionare la restrizione che si vuole impostare > **Proprietà** > **selezionare le piattaforme** > selezionare **Consenti** per **iOS**, quindi fare clic su **OK**.
5. Selezionare **Configura piattaforme**, selezionare **Consenti** per i dispositivi iOS di proprietà personale, quindi fare clic su **OK**.
6. Registrare nuovamente il dispositivo.

**Motivo:** I record CNAME necessari in DNS non esistono.

#### <a name="resolution"></a>Soluzione
Creare record di risorse DNS CNAME per il dominio aziendale. Ad esempio, se il dominio della società è contoso.com, creare un record CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com.

Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record di registrazione CNAME, agli utenti viene richiesto di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

Se è presente più di un dominio verificato, creare un record CNAME per ogni dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

|TYPE|Nome host|Punta a|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Hr|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hr|

Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

> [!NOTE]
> La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non è stato propagato.

**Motivo:** Si registra un dispositivo registrato in precedenza con un account utente diverso e l'utente precedente non è stato rimosso in modo appropriato da Intune.

#### <a name="resolution"></a>Soluzione
1. Annulla l'installazione del profilo corrente.
2. Aprire [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) in Safari.
3. Registrare nuovamente il dispositivo.

> [!NOTE]
> Se la registrazione non riesce ancora, rimuovere i cookie in Safari (non bloccare i cookie), quindi registrare nuovamente il dispositivo.

**Motivo:** Il dispositivo è già registrato con un altro provider MDM.

#### <a name="resolution"></a>Soluzione
1. Aprire **Impostazioni** nel dispositivo iOS, passare a **Generale > Gestione dispositivi**.
2. Rimuovere qualsiasi profilo di gestione esistente.
3. Registrare nuovamente il dispositivo.

**Motivo:** L'utente che sta provando a registrare il dispositivo non dispone di una licenza di Microsoft Intune.

#### <a name="resolution"></a>Soluzione
1. Passare all'interfaccia di [amministrazione di Office 365](https://portal.office.com/adminportal/home#/homepage), quindi scegliere **utenti > utenti attivi**.
2. Selezionare l'account utente a cui si vuole assegnare una licenza utente di Intune e quindi scegliere **Licenze di prodotto > Modifica**.
3. Passare alla posizione **on** per la licenza che si desidera assegnare all'utente e quindi scegliere **Salva**.
4. Registrare nuovamente il dispositivo.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Questo servizio non è supportato. Nessun criterio di registrazione.

**Motivo**: un certificato push MDM Apple non è configurato in Intune o il certificato non è valido. 

#### <a name="resolution"></a>Soluzione

- Se il certificato push MDM non è configurato, seguire i passaggi in [ottenere un certificato push MDM Apple](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Se il certificato push MDM non è valido, attenersi alla procedura descritta in [rinnovo del certificato push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Portale aziendale temporaneamente non disponibile. Si è verificato un problema nell'app Portale aziendale. Se il problema persiste, contattare l'amministratore del sistema.

**Motivo:** L'app Portale aziendale non è aggiornata o è danneggiata.

#### <a name="resolution"></a>Soluzione
1. Rimuovere l'app Portale aziendale dal dispositivo.
2. Scaricare e installare l'app **Portale aziendale Microsoft Intune** da **App Store**.
3. Registrare nuovamente il dispositivo.
 > [!NOTE]
    > Questo errore può verificarsi anche se l'utente tenta di registrare più dispositivi rispetto alla configurazione della registrazione del dispositivo. Seguire i passaggi di risoluzione per il **limite di dispositivo raggiunto** di seguito se questa procedura non risolve il problema.

### <a name="device-cap-reached"></a>Numero massimo dispositivi raggiunto

**Motivo:** L'utente tenta di registrare più dispositivi rispetto al limite di registrazione del dispositivo.

#### <a name="resolution"></a>Soluzione
1. Aprire il [portale di amministrazione di Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) > **dispositivi** > **tutti i dispositivi**e verificare il numero di dispositivi registrati dall'utente.
    > [!NOTE]
    > È anche necessario avere l'accesso utente interessato al portale per gli [utenti di Intune](https://portal.manage.microsoft.com/) e controllare i dispositivi registrati. Potrebbero essere presenti dispositivi che vengono visualizzati nel [portale](https://portal.manage.microsoft.com/) per gli utenti di Intune ma non nel [portale di amministrazione di Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). tali dispositivi vengono conteggiati anche per il limite di registrazione del dispositivo.
2. Passare ad **amministrazione** > **gestione dei dispositivi mobili** > **regole di registrazione** > verificare il limite di registrazione del dispositivo. Per impostazione predefinita, il limite è impostato su 15. 
3. Se il numero di dispositivi registrati ha raggiunto il limite, rimuovere i dispositivi non necessari o aumentare il limite di registrazione del dispositivo. Poiché ogni dispositivo registrato usa una licenza di Intune, è consigliabile rimuovere sempre i dispositivi non necessari.
4. Registrare nuovamente il dispositivo.

### <a name="workplace-join-failed"></a>Workplace Join non riuscito

**Motivo:** L'app Portale aziendale non è aggiornata o è danneggiata.  

#### <a name="resolution"></a>Soluzione
1. Rimuovere l'app Portale aziendale dal dispositivo.
2. Scaricare e installare l'app **Portale aziendale Microsoft Intune** da **App Store**.
3. Registrare nuovamente il dispositivo.

### <a name="user-license-type-invalid"></a>Tipo di licenza utente non valido

**Motivo:** L'utente che sta provando a registrare il dispositivo non dispone di una licenza di Intune valida.

#### <a name="resolution"></a>Soluzione
1. Passare all'interfaccia di [amministrazione di Microsoft 365](https://portal.office.com/adminportal/home#/homepage), quindi scegliere **utenti** > **utenti attivi**.
2. Selezionare l'account utente interessato > **licenze prodotto** > **modifica**.
3. Verificare che all'utente sia assegnata una licenza di Intune valida.
4. Registrare nuovamente il dispositivo.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nome utente non riconosciuto. Questo account utente non è autorizzato a utilizzare Microsoft Intune. Se si ritiene di aver ricevuto questo messaggio in errore, contattare l'amministratore di sistema.

**Motivo:** L'utente che sta provando a registrare il dispositivo non dispone di una licenza di Intune valida.

1. Passare all'interfaccia di [amministrazione di Microsoft 365](https://portal.office.com/adminportal/home#/homepage), quindi scegliere **utenti** > **utenti attivi**.
2. Selezionare l'account utente interessato, quindi scegliere **licenze prodotto** > **modifica**.
3. Verificare che all'utente sia assegnata una licenza di Intune valida.
4. Registrare nuovamente il dispositivo.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Installazione profilo non riuscita. Il nuovo payload MDM non corrisponde al payload precedente.

**Motivo:** Un profilo di gestione è già installato nel dispositivo.

#### <a name="resolution"></a>Soluzione

1. Aprire **Impostazioni** nel dispositivo iOS > **generale** > la **gestione dei dispositivi**.
2. Toccare il profilo di gestione esistente e toccare **Rimuovi Gestione**.
3. Registrare nuovamente il dispositivo.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Motivo:** Il certificato Apple Push Notification Service (APNs) è mancante, non valido o scaduto.

#### <a name="resolution"></a>Soluzione
Verificare che in Intune sia stato aggiunto un certificato APNs valido. Per altre informazioni, vedere [Configurare la gestione dei dispositivi iOS e Mac](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Motivo:** Si è verificato un problema con il certificato del servizio Apple Push Notification (APNs) configurato in Intune.

#### <a name="resolution"></a>Soluzione
Rinnovare il certificato APNs e quindi eseguire di nuovo la registrazione del dispositivo.

> [!IMPORTANT]
> Assicurarsi di rinnovare il certificato APNs. Non sostituire il certificato APNs. Se si sostituisce il certificato, è necessario registrare di nuovo tutti i dispositivi iOS in Intune. 

- Per rinnovare il certificato APNs in Intune autonomo, vedere [rinnovare il certificato push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Per rinnovare il certificato APNs in Intune Hybrid con Configuration Manager, vedere [configurare la gestione di dispositivi ibridi iOS con System Center Configuration Manager e Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- Per rinnovare il certificato APNs in Office 365, vedere [creare un certificato APNs per dispositivi iOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>Connessione XPC_TYPE_ERROR non valida

Quando si attiva un dispositivo gestito da DEP a cui viene assegnato un profilo di registrazione, la registrazione ha esito negativo e viene visualizzato il messaggio di errore seguente:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Motivo:** Si è verificato un problema di connessione tra il dispositivo e il servizio DEP di Apple.

#### <a name="resolution"></a>Soluzione
Risolvere il problema di connessione oppure usare una connessione di rete diversa per registrare il dispositivo. Se il problema persiste, potrebbe essere necessario contattare Apple.


## <a name="other-issues"></a>Altri problemi

### <a name="dep-enrollment-doesnt-start"></a>La registrazione DEP non viene avviata
Quando si attiva un dispositivo gestito da DEP a cui viene assegnato un profilo di registrazione, il processo di registrazione di Intune non viene avviato.

**Motivo:** Il profilo di registrazione viene creato prima che il token DEP venga caricato in Intune.

#### <a name="resolution"></a>Soluzione

1. Modificare il profilo di registrazione. È possibile apportare qualsiasi modifica al profilo. Lo scopo è aggiornare l'ora di modifica del profilo.
2. Sincronizzare i dispositivi gestiti da DEP: aprire il portale di Intune > **amministratore** > **gestione dei dispositivi mobili** > **iOS** > **Device Enrollment Program** **Sincronizza ora** > . Viene inviata una richiesta di sincronizzazione ad Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>Registrazione DEP bloccata all'accesso dell'utente
Quando si attiva un dispositivo gestito da DEP a cui viene assegnato un profilo di registrazione, il programma di installazione iniziale si inserisce dopo aver immesso le credenziali.

**Motivo:** Multi-factor authentication è abilitato. Attualmente, l'autenticazione a più fattori non funziona durante la registrazione nei dispositivi DEP.

#### <a name="resolution"></a>Soluzione
Disabilitare l'autenticazione a più fattori e quindi eseguire di nuovo la registrazione del dispositivo.

## <a name="next-steps"></a>Passaggi successivi

- [Risolvere i problemi di registrazione dei dispositivi in Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Porre una domanda nel forum di Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulta il Blog del team di supporto di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consulta il Blog di Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
