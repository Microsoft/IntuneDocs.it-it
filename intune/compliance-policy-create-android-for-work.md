---
title: Creare criteri di conformità per Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Creare o configurare criteri di conformità Microsoft Intune per dispositivi Android Enterprise o di profili di lavoro. Scegliere di consentire i dispositivi jailbroken, impostare il livello di minaccia accettabile, verificare la presenza di Google Play, immettere la versione minima e massima del sistema operativo, scegliere i requisiti delle password e consentire il sideload delle applicazioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: aab8208865fb072170a670d1da25e7f02448c38f
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642864"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>Aggiungere criteri di conformità per dispositivi Android Enterprise in Intune

I criteri di conformità dei dispositivi sono una funzionalità fondamentale quando si usa Intune per proteggere le risorse dell'organizzazione. In Intune è possibile creare regole e impostazioni che i dispositivi devono soddisfare per essere considerati conformi, ad esempio la lunghezza della password. Se il dispositivo non è conforme, è possibile bloccare l'accesso ai dati e alle risorse tramite l'[accesso condizionale](conditional-access.md). 

È anche possibile ottenere report per i dispositivi e, in caso di mancata conformità, eseguire azioni specifiche, ad esempio inviare una notifica tramite posta elettronica all'utente. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

Questo articolo elenca le impostazioni che è possibile usare all'interno di criteri di conformità per dispositivi che eseguono Android Enterprise.

## <a name="non-compliance-and-conditional-access"></a>Mancata conformità e accesso condizionale

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

--------------------------

|**impostazione di criteri**| **Profilo Android Enterprise** |
| --- | --- |
| **Configurazione di PIN o password** |  In quarantena |
| **Crittografia dispositivo** |  In quarantena |
| **Dispositivo jailbroken o rooted** | In quarantena (non è un'impostazione) |
| **Profilo di posta elettronica** | Non applicabile |
| **Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |
| **Attestazione dell'integrità di Windows** |Non applicabile |

**Con correzione** = il sistema operativo del dispositivo impone la conformità. Ad esempio, l'utente è obbligato a impostare un PIN.

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. ad esempio, l'utente di dispositivi Android non è obbligato a crittografare il dispositivo. Se il dispositivo non è conforme, vengono eseguite le azioni seguenti:

  - Se all'utente si applica un criterio di accesso condizionale, il dispositivo viene bloccato.
  - Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Per **Piattaforma** selezionare **Android Enterprise**. 
5. Scegliere **Impostazioni Configura**. Immettere le impostazioni **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema** come descritto in questo articolo.

## <a name="device-health"></a>Integrità del dispositivo

- **Dispositivi rooted**: scegliere **Blocca** per contrassegnare i dispositivi rooted (jailbroken) come non conformi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Per usare questa impostazione, scegliere il livello di minaccia consentito:
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alto**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
- **Google Play Services è configurato**: **richiede** che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Provider di sicurezza aggiornato**: **richiede** un provider di sicurezza aggiornato che può proteggere un dispositivo dalle vulnerabilità note. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato** (impostazione predefinita): l'impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

#### <a name="threat-scan-on-apps"></a>Analisi delle minacce nelle app

Nei dispositivi Android Enterprise, l'impostazione **Analisi delle minacce nelle app** è un criterio di configurazione. Vedere [Impostazioni relative alle restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella nella regola, l'accesso alle risorse aziendali viene bloccato e all'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata in modo da consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password per poter accedere al dispositivo. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Questa impostazione viene applicata a livello di dispositivo. Se è sufficiente richiedere una password a livello di profilo di lavoro, usare i criteri di configurazione. Vedere [Impostazioni di configurazione dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri che deve avere la password dell'utente.
- **Tipo di password richiesto**: scegliere se una password deve essere composta solo da caratteri numerici oppure da una combinazione di numeri e altri caratteri. Le opzioni disponibili sono:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Almeno numerico** (impostazione predefinita)
  - **Complessa numerica**
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere nuovamente la password. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Scadenza password (giorni)**: selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.
- **Numero di password precedenti di cui impedire il riutilizzo**: immettere il numero di password recenti che non è possibile riutilizzare. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. 

  Non è necessario configurare questa impostazione poiché i dispositivi del profilo di lavoro Android applicano la crittografia.

### <a name="device-security"></a>Sicurezza del dispositivo

- **Blocca app da origini sconosciute**: scegliere di **bloccare** i dispositivi con origini abilitate in "Sicurezza > Origini sconosciute" (supportato da Android 4.0 ad Android 7.x, non supportato da Android 8.0 e versioni successive). Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Per trasferire localmente le app, devono essere consentite le origini sconosciute. Se non si esegue il sideload di app Android, abilitare questi criteri di conformità impostando questa funzionalità su **Blocca**. 

  > [!IMPORTANT]
  > Le applicazioni trasferite localmente richiedono l'abilitazione dell'impostazione **Blocca app da origini sconosciute**. Imporre questi criteri di conformità solo se non si esegue il sideload di app Android nei dispositivi.

  Non è necessario configurare questa impostazione poiché i dispositivi del profilo di lavoro Android limitano sempre l'installazione da origini sconosciute.

- **Integrità del runtime dell'app Portale aziendale**: scegliere **Rendi obbligatorio** per confermare che l'app Portale aziendale soddisfa tutti i requisiti seguenti:

  - Ha l'ambiente di runtime predefinito installato
  - È firmata correttamente
  - Non è in modalità di debug
  - È installata da un'origine nota

  Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

- **Blocca il debug USB nel dispositivo**: scegliere **Blocca** per impedire ai dispositivi di usare la funzionalità di debug USB. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Non è necessario configurare questa impostazione perché il debug USB è già disabilitato nei dispositivi del profilo di lavoro Android.

- **Livello minimo di patch di protezione**: selezionare il livello di patch di sicurezza meno recente consentito per un dispositivo. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere immessa nel formato *AAAA-MM-GG*.

Al termine, selezionare **OK** > **OK** per salvare le modifiche.

## <a name="actions-for-noncompliance"></a>Azioni per la mancata conformità

Selezionare **Azioni per la mancata conformità**. L'azione predefinita contrassegna immediatamente il dispositivo come non conforme.

Se il dispositivo è contrassegnato come non conforme, è possibile modificare la pianificazione, ad esempio dopo un giorno. È anche possibile configurare una seconda azione con cui inviare un messaggio di posta elettronica all'utente se il dispositivo risulta non conforme.

[Aggiungere azioni per dispositivi non conformi](actions-for-noncompliance.md) offre altre informazioni, tra cui come creare un messaggio di posta elettronica di notifica per gli utenti.

## <a name="scope-tags"></a>Tag di ambito

I tag di ambito sono un metodo molto efficiente per assegnare criteri a gruppi specifici, ad esempio ai reparti Vendite, Ufficio tecnico, Risorse umane e così via. È possibile aggiungere tag di ambito a criteri di conformità. Vedere [Usare i tag di ambito per filtrare i criteri](scope-tags.md). 

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Dopo aver creato un criterio, questo non esegue alcuna operazione finché non viene assegnato. Per assegnare il criterio: 

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

Il criterio è stato applicato agli utenti. Verrà eseguita la valutazione della conformità dei dispositivi usati dagli utenti a cui il criterio è destinato.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)  
[Impostazioni dei criteri di conformità per Android](compliance-policy-create-android.md)
