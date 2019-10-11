---
title: Impostazioni di conformità di Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Android Enterprise in Microsoft Intune. Impostare le regole delle password, scegliere una versione minima o massima del sistema operativo, creare restrizioni per app specifiche, impedire il riutilizzo della password e così via.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7d38d5c71b06587b593eef46eca46f3d32f1349
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733101"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Android Enterprise in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per contrassegnare i dispositivi rooted (Jailbroken) come non conformi, impostare un livello di rischio consentito, abilitare Protezione di Google Play e così via.

Questa funzionalità si applica a:

- Android Enterprise

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

> [!IMPORTANT]
> I criteri di conformità applicano anche dispositivi dedicati a Android Enterprise. Se un criterio di conformità viene assegnato a un dispositivo dedicato, il dispositivo può essere visualizzato come **non conforme**. L'accesso condizionale e l'applicazione della conformità non sono disponibili nei dispositivi dedicati. Assicurarsi di completare qualsiasi attività o operazione per garantire che i dispositivi dedicati siano conformi con i criteri assegnati.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma** selezionare **Android Enterprise**.

## <a name="device-owner"></a>Proprietario del dispositivo

### <a name="device-health"></a>Integrità del dispositivo

- **Richiedi che il dispositivo si trovi al**massimo al livello di minaccia del dispositivo: selezionare il livello di minaccia massimo consentito per il dispositivo valutato dal [servizio Mobile Threat Defense](mobile-threat-defense.md). I dispositivi che superano questo livello di minaccia vengono contrassegnati come non conformi. Per usare questa impostazione, scegliere il livello di minaccia consentito:

  - **Non configurato** (impostazione predefinita): questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
  
> [!NOTE] 
> I provider di Mobile Threat Defense (MTD) seguenti supportano le distribuzioni del proprietario di dispositivi Android Enterprise usando la configurazione dell'app:
> - Better Mobile 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Rivolgersi al provider MTD per la configurazione esatta necessaria per supportare le piattaforme del proprietario di dispositivi Android Enterprise in Intune. Questo elenco viene aggiornato perché i MTD parters supportano gli scenari per i proprietari di dispositivi Android Enterprise. 

#### <a name="google-play-protect"></a>Protezione di Google Play

- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato** (impostazione predefinita): l'impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

### <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può aggiornare il dispositivo e quindi accedere alle risorse dell'organizzazione.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

### <a name="system-security"></a>Protezione del sistema

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Questa impostazione viene applicata a livello di dispositivo. Se è sufficiente richiedere una password a livello di profilo di lavoro, usare i criteri di configurazione. Vedere [Impostazioni di configurazione dei dispositivi Android Enterprise](../configuration/device-restrictions-android-for-work.md).

  - **Tipo di password richiesto**: scegliere se una password deve essere composta solo da caratteri numerici oppure da una combinazione di numeri e altri caratteri. Le opzioni disponibili sono:
    - **Impostazione predefinita del dispositivo**: per valutare la conformità delle password, assicurarsi di selezionare un livello di attendibilità diverso da quello **predefinito del dispositivo**.  
    - **Password obbligatoria, nessuna restrizione**
    - **Biometria vulnerabile**: [biometrica complessa rispetto alla vulnerabile](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (apre il sito Web di Android)
    - **Numerica** (impostazione predefinita): la password contiene solo numeri, ad esempio `123456789`. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
    - **Complessa numerica**: i numeri consecutivi o ripetuti (ad esempio, "1111" o "1234") non sono consentiti. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
    - **Alfabetica**: è obbligatorio utilizzare le lettere dell'alfabeto. Numeri e simboli non sono richiesti. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
    - **Alfanumerica**: include lettere maiuscole, lettere minuscole e caratteri numerici. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
    - **Alfanumerico con simboli**: include lettere maiuscole, lettere minuscole, caratteri numerici, segni di punteggiatura e simboli. Specificare anche:

      - **Lunghezza minima password**: immettere la lunghezza minima per la password che deve essere compresa tra da 4 e 16 caratteri.
      - **Numero di caratteri richiesti**: immettere il numero di caratteri deve contenere la password, compreso tra 0 e 16 caratteri.
      - **Numero di caratteri minuscoli obbligatori**: immettere il numero di caratteri minuscoli compreso tra 0 e 16 che la password deve contenere.
      - **Numero di caratteri maiuscoli obbligatori**: immettere il numero di caratteri maiuscoli compreso tra 0 e 16 che la password deve contenere.
      - **Numero di caratteri diversi da lettere obbligatori**: immettere il numero di caratteri (diversi dalle lettere dell'alfabeto) compreso tra 0 e 16 caratteri che la password deve contenere.
      - **Numero di caratteri numerici obbligatori**: immettere il numero di caratteri numerici (`1`, `2`, `3` e così via) compreso tra 0 e 16 caratteri che la password deve contenere.
      - **Numero di caratteri di tipo simbolo obbligatori**: immettere il numero di caratteri di tipo simbolo (`&`, `#`, `%` e così via) compreso tra 0 e 16 caratteri che la password deve contenere.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Numero di giorni rimanenti prima della scadenza della password**: immettere il numero di giorni che devono trascorrere tra 1 e 365 prima che sia necessario modificare la password del dispositivo. Ad esempio, per modificare la password dopo 60 giorni, immettere `60`. Quando la password scade, agli utenti viene chiesto di creare una nuova password.
- **Numero di password obbligatorie prima che un utente possa riutilizzare una password**: immettere il numero di password recenti tra 1 e 24 che non può essere riutilizzato. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Non è necessario configurare questa impostazione poiché i dispositivi Android Enterprise applicano la crittografia.

## <a name="work-profile"></a>Profilo di lavoro

### <a name="device-health"></a>Device health

- **Dispositivi rooted**: scegliere **Blocca** per contrassegnare i dispositivi rooted (jailbroken) come non conformi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Richiedi che il dispositivo si trovi al**massimo al livello di minaccia del dispositivo: selezionare il livello di minaccia massimo consentito per il dispositivo valutato dal [servizio Mobile Threat Defense](mobile-threat-defense.md). I dispositivi che superano questo livello di minaccia vengono contrassegnati come non conformi. Per usare questa impostazione, scegliere il livello di minaccia consentito:

  - **Non configurato** (impostazione predefinita): questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

#### <a name="google-play-protect"></a>Protezione di Google Play

- **Google Play Services è configurata**: **richiede** che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Provider di sicurezza aggiornato**: **richiede** un provider di sicurezza aggiornato in grado di proteggere un dispositivo dalle vulnerabilità note. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato** (impostazione predefinita): l'impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

> [!NOTE]
> Nei dispositivi Android Enterprise **Analisi delle minacce nelle app** è un criterio di configurazione del dispositivo. Usando i criteri di configurazione, gli amministratori possono abilitare l'impostazione in un dispositivo. Vedere [Impostazioni relative alle restrizioni dei dispositivi Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può aggiornare il dispositivo e quindi accedere alle risorse dell'organizzazione.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

### <a name="system-security"></a>Protezione del sistema

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Questa impostazione viene applicata a livello di dispositivo. Se è sufficiente richiedere una password a livello di profilo di lavoro, usare i criteri di configurazione. Vedere [Impostazioni di configurazione dei dispositivi Android Enterprise](../configuration/device-restrictions-android-for-work.md).
- **Tipo di password richiesto**: scegliere se una password deve essere composta solo da caratteri numerici oppure da una combinazione di numeri e altri caratteri. Le opzioni disponibili sono:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Almeno numerico** (impostazione predefinita): immettere la **lunghezza minima della password** che un utente deve immettere (da 4 a 16 caratteri).
  - **Complessa numerica** (impostazione predefinita): immettere la **lunghezza minima della password** che un utente deve immettere (da 4 a 16 caratteri).
  - **Almeno alfabetico**: immettere la **lunghezza minima della password** che un utente deve immettere (da 4 a 16 caratteri).
  - **Almeno alfanumerico**: immettere la **lunghezza minima della password** che un utente deve immettere (da 4 a 16 caratteri).
  - **Almeno alfanumerico con simboli**: immettere la **lunghezza minima della password** che un utente deve immettere (da 4 a 16 caratteri).

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Numero di giorni rimanenti prima della scadenza della password**: selezionare il numero di giorni prima della scadenza della password. Alla scadenza, l'utente finale dovrà creare una nuova password.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password recenti che non è possibile riutilizzare. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

#### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. 

  Non è necessario configurare questa impostazione poiché i dispositivi Android Enterprise applicano la crittografia.

#### <a name="device-security"></a>Sicurezza del dispositivo

- **Blocca app da origini sconosciute**: scegliere di **bloccare** i dispositivi con origini abilitate in **Sicurezza** > **Origini sconosciute** (supportato da Android 4.0 ad Android 7.x, non supportato da Android 8.0 e versioni successive). Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Per trasferire localmente le app, devono essere consentite le origini sconosciute. Se non si esegue il sideload di app Android, abilitare questi criteri di conformità impostando questa funzionalità su **Blocca**.

  > [!IMPORTANT]
  > Le applicazioni trasferite localmente richiedono l'abilitazione dell'impostazione **Blocca app da origini sconosciute**. Imporre questi criteri di conformità solo se non si esegue il sideload di app Android nei dispositivi.

  Non è necessario configurare questa impostazione poiché i dispositivi Android Enterprise impediscono sempre l'installazione da origini sconosciute.

- **Integrità del runtime dell'app Portale aziendale**: scegliere **Richiedi** per confermare che l'app Portale aziendale soddisfa tutti i requisiti seguenti:

  - Ha l'ambiente di runtime predefinito installato
  - È firmata correttamente
  - Non è in modalità di debug
  - È installata da un'origine nota

  Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

- **Blocca il debug USB nel dispositivo**: scegliere **Blocca** per impedire ai dispositivi di usare la funzionalità di debug USB. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Non è necessario configurare questa impostazione perché il debug USB è già disabilitato nei dispositivi Android Enterprise.

- **Livello minimo di patch di protezione**: selezionare il livello di patch di sicurezza meno recente consentito per un dispositivo. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere immessa nel formato *AAAA-MM-GG*.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Android](compliance-policy-create-android.md).