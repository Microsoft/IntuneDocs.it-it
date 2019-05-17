---
title: Impostazioni di conformità di Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Android Enterprise in Microsoft Intune. Impostare le regole delle password, scegliere una versione minima o massima del sistema operativo, creare restrizioni per app specifiche, impedire il riutilizzo della password e così via.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16db0acab84a1095c40e9a92648c75c2581187cd
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423561"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Android Enterprise in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per contrassegnare i dispositivi rooted (Jailbroken) come non conformi, impostare un livello di rischio consentito, abilitare Protezione di Google Play e così via.

Questa funzionalità si applica a:

- Android Enterprise

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma** selezionare **Android Enterprise**.

## <a name="device-health"></a>Device health

- **Dispositivi rooted**: scegliere **Blocca** per contrassegnare i dispositivi rooted (jailbroken) come non conformi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Per usare questa impostazione, scegliere il livello di minaccia consentito:
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

### <a name="google-play-protect"></a>Protezione di Google Play

- **Google Play Services è configurata**: **richiede** che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Provider di sicurezza aggiornato**: **richiede** un provider di sicurezza aggiornato in grado di proteggere un dispositivo dalle vulnerabilità note. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Attestazione del dispositivo SafetyNet**: immettere il livello di [attestazione di SafetyNet](https://developer.android.com/training/safetynet/attestation.html) che deve essere raggiunto. Le opzioni disponibili sono:
  - **Non configurato** (impostazione predefinita): l'impostazione non viene tenuta in considerazione per la valutazione della conformità.
  - **Verifica l'integrità di base**
  - **Verifica l'integrità di base e i dispositivi certificati**

> [!NOTE]
> Nei dispositivi Android Enterprise **Analisi delle minacce nelle app** è un criterio di configurazione del dispositivo. Usando i criteri di configurazione, gli amministratori possono abilitare l'impostazione in un dispositivo. Vedere [Impostazioni relative alle restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi accedere alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella nella regola, l'accesso alle risorse aziendali viene bloccato e all'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata in modo da consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Questa impostazione viene applicata a livello di dispositivo. Se è sufficiente richiedere una password a livello di profilo di lavoro, usare i criteri di configurazione. Vedere [Impostazioni di configurazione dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password dell'utente.
- **Tipo di password richiesto**: scegliere se una password deve essere composta solo da caratteri numerici oppure da una combinazione di numeri e altri caratteri. Le opzioni disponibili sono:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Almeno numerico** (impostazione predefinita)
  - **Complessa numerica**
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password recenti che non è possibile riutilizzare. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. 

  Non è necessario configurare questa impostazione poiché i dispositivi Android Enterprise applicano la crittografia.

### <a name="device-security"></a>Sicurezza del dispositivo

- **Blocca app da origini sconosciute**: scegliere di **bloccare** i dispositivi con origini abilitate in "Security > Unknown Sources" (Sicurezza > Origini sconosciute) (supportato da Android 4.0 ad Android 7.x, non supportato da Android 8.0 e versioni successive). Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

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

Selezionare **OK** > **Crea** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Android](compliance-policy-create-android.md).
