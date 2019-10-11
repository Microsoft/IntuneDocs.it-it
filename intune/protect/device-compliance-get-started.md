---
title: Criteri di conformità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni introduttive sull'uso dei criteri di conformità, panoramica dei livelli di stato e gravità, uso dello stato Periodo di tolleranza, uso dell'accesso condizionale, gestione dei dispositivi senza un criterio assegnato e differenze di conformità tra il portale di Azure e il portale classico in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a743bb3b2003b1dbdf8088aca19bce898c8e40a8
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721422"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Impostare regole sui dispositivi per consentire l'accesso alle risorse dell'organizzazione tramite Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Molte soluzioni di gestione di dispositivi mobili (MDM, Mobile Device Management) consentono di proteggere i dati dell'organizzazione richiedendo agli utenti e ai dispositivi di soddisfare alcuni requisiti. In Intune, questa funzionalità è detta "criteri di conformità". I criteri di conformità definiscono le regole e le impostazioni che gli utenti e i dispositivi devono soddisfare per adeguarsi ai criteri stessi. Combinando questi criteri con l'accesso condizionale gli amministratori possono bloccare gli utenti e i dispositivi che non rispettano le regole.

Un amministratore di Intune può, ad esempio, richiedere:

- L'uso di una password da parte degli utenti finali per accedere ai dati dell'organizzazione nei dispositivi mobili
- L'uso di un dispositivo non manomesso con jailbreak e senza accesso root
- Una versione massima o minima del sistema operativo per il dispositivo
- Un livello di minaccia del dispositivo corrispondente o inferiore a un certo livello

Si può usare questa funzionalità anche per monitorare lo stato di conformità dei dispositivi dell'organizzazione.

> [!IMPORTANT]
> Intune segue la pianificazione in base alla quale il dispositivo contatta il servizio per tutte le valutazioni di conformità sul dispositivo. [Cicli di aggiornamento di criteri e profili](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) elenca i tempi di aggiornamento stimati.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Funzionamento dei criteri di conformità del dispositivo con Azure AD

Intune usa l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) di Azure Active Directory (AD) (apre un altro sito Web di documenti) per applicare la conformità. Al momento della registrazione di un dispositivo in Intune, viene avviato il processo di registrazione di Azure AD e le informazioni sul dispositivo vengono aggiornate in Azure AD. Un'informazione chiave è lo stato di conformità del dispositivo. Questo stato di conformità viene usato dai criteri di accesso condizionale per bloccare o consentire l'accesso alla posta elettronica e ad altre risorse dell'organizzazione.

- Per sapere perché e in che modo i dispositivi vengono registrati in Azure AD, vedere [Informazioni sulla gestione dei dispositivi in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

- Gli articoli [Che cos'è l'accesso condizionale?](conditional-access.md) e [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](conditional-access-intune-common-ways-use.md) descrivono questa funzionalità in relazione a Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Modi per usare i criteri di conformità del dispositivo

### <a name="with-conditional-access"></a>Con l'accesso condizionale

Ai dispositivi conformi alle regole dei criteri è possibile consentire l'accesso alla posta elettronica e ad altre risorse dell'organizzazione. Se non sono conformi alle regole dei criteri, i dispositivi non ottengono l'accesso alle risorse dell'organizzazione. Questo è l'accesso condizionale.

### <a name="without-conditional-access"></a>Senza l'accesso condizionale

È anche possibile usare i criteri di conformità dei dispositivi senza accesso condizionale. In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Può ad esempio essere utile ottenere un report del numero dei dispositivi non crittografati o dei dispositivi manomessi con jailbreak o con accesso root. Quando si usano criteri di conformità senza l'accesso condizionale non vengono applicate limitazioni per l'accesso alle risorse dell'organizzazione.

## <a name="ways-to-deploy-device-compliance-policies"></a>Modi per distribuire i criteri di conformità dei dispositivi

È possibile distribuire i criteri di conformità a utenti in gruppi di utenti o a dispositivi in gruppi di dispositivi. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata su tutti i dispositivi dell'utente. In Windows 10 versione 1803 e nei dispositivi più recenti è consigliabile eseguire la distribuzione ai gruppi di dispositivi *se* l'utente primario non ha registrato il dispositivo. L'uso di gruppi di dispositivi in questo scenario è utile per la creazione di report di conformità.

Intune include anche un set di impostazioni dei criteri di conformità predefiniti. I criteri predefiniti seguenti vengono valutati in tutti i dispositivi registrati in Intune:

- **Contrassegna i dispositivi senza criteri di conformità assegnati come**: questa proprietà ha due valori:

  - **Conforme** (impostazione predefinita): la funzione di sicurezza è disattivata
  - **Non conforme**: la funzione di sicurezza è attiva

  Per impostazione predefinita, un dispositivo a cui non è stato assegnato un criterio di conformità è considerato conforme. Se si usa l'accesso condizionale con i criteri di conformità, è consigliabile cambiare l'impostazione in **Non conforme**. Se un utente finale non è conforme perché non è stato assegnato alcun criterio, nell'[app Portale aziendale](../apps/company-portal-app.md) viene visualizzato `No compliance policies have been assigned`.

- **Rilevamento ottimizzato per jailbreak**: se abilitata, questa impostazione attiva un'archiviazione più frequente dei dispositivi iOS con Intune. L'abilitazione di questa proprietà usa i servizi di posizione del dispositivo e influisce sull'utilizzo della batteria. I dati relativi alla posizione dell'utente non vengono archiviati da Intune.

  Per l'abilitazione di questa impostazione è necessario che:
  - Nei dispositivi siano abilitati i servizi di posizione a livello di sistema operativo.
  - I dispositivi consentano al portale aziendale di usare servizi di posizione.
  - I dispositivi valutino e segnalino il proprio stato jailbreak a Intune almeno una volta ogni 72 ore. In caso contrario, il dispositivo è contrassegnato come non conforme. La valutazione viene attivata aprendo l'app Portale aziendale o spostando fisicamente il dispositivo di almeno 500 metri. Se il dispositivo non si sposta di 500 metri entro 72 ore, l'utente deve aprire l'app Portale aziendale per la valutazione avanzata dello stato jailbreak.

- **Periodo di validità dello stato di conformità (giorni)** : immettere il periodo di tempo in cui i dispositivi devono segnalare lo stato per tutti i criteri di conformità ricevuti. I dispositivi che non restituiscono lo stato entro il periodo indicato vengono considerati non conformi. Il valore predefinito è 30 giorni.

È possibile usare i criteri predefiniti per monitorare queste impostazioni. Intune inoltre [aggiorna o verifica la presenza di aggiornamenti](create-compliance-policy.md#refresh-cycle-times) a diversi intervalli, a seconda della piattaforma del dispositivo. Per altre informazioni, vedere [Domande e problemi comuni e soluzioni per i criteri e i profili dei dispositivi in Microsoft Intune](../configuration/device-profile-troubleshoot.md).

I report di conformità sono un ottimo modo per controllare lo stato dei dispositivi. Per altre indicazioni, vedere [Monitorare i criteri di conformità](compliance-policy-monitor.md).

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Mancata conformità e accesso condizionale sulle diverse piattaforme

La tabella seguente descrive come vengono gestite le impostazioni non conformi quando si usano criteri di conformità con criteri di accesso condizionale.

---------------------------

|**Impostazione di criteri**| **Piattaforma** |
| --- | ----|
| **Configurazione di PIN o password** | - **Android 4.0 e versioni successive**: In quarantena</br>- **Samsung KNOX Standard 4.0 e versioni successive**: In quarantena</br>- **Android Enterprise**: In quarantena</br></br>- **iOS 8.0 e versioni successive**: Corretto</br>- **macOS 10.11 e versioni successive**: Corretto</br></br>- **Windows 8.1 e versioni successive**: Corretto</br>- **Windows Phone 8.1 e versioni successive**: Corretto|
| **Crittografia dispositivo** | - **Android 4.0 e versioni successive**: In quarantena</br>- **Samsung KNOX Standard 4.0 e versioni successive**: In quarantena</br>- **Android Enterprise**: In quarantena</br></br>- **iOS 8.0 e versioni successive**: Corretto (impostando il PIN)</br>- **macOS 10.11 e versioni successive**: Corretto (impostando il PIN)</br></br>- **Windows 8.1 e versioni successive**: Non applicabile</br>- **Windows Phone 8.1 e versioni successive**: Corretto |
| **Dispositivo jailbroken o rooted** | - **Android 4.0 e versioni successive**: In quarantena (non è un'impostazione)</br>- **Samsung KNOX Standard 4.0 e versioni successive**: In quarantena (non è un'impostazione)</br>- **Android Enterprise**: In quarantena (non è un'impostazione)</br></br>- **iOS 8.0 e versioni successive**: In quarantena (non è un'impostazione)</br>- **macOS 10.11 e versioni successive**: Non applicabile</br></br>- **Windows 8.1 e versioni successive**: Non applicabile</br>- **Windows Phone 8.1 e versioni successive**: Non applicabile |
| **Profilo di posta elettronica** | - **Android 4.0 e versioni successive**: Non applicabile</br>- **Samsung KNOX Standard 4.0 e versioni successive**: Non applicabile</br>- **Android Enterprise**: Non applicabile</br></br>- **iOS 8.0 e versioni successive**: In quarantena</br>- **macOS 10.11 e versioni successive**: In quarantena</br></br>- **Windows 8.1 e versioni successive**: Non applicabile</br>- **Windows Phone 8.1 e versioni successive**: Non applicabile |
| **Versione minima del sistema operativo** | - **Android 4.0 e versioni successive**: In quarantena</br>- **Samsung KNOX Standard 4.0 e versioni successive**: In quarantena</br>- **Android Enterprise**: In quarantena</br></br>- **iOS 8.0 e versioni successive**: In quarantena</br>- **macOS 10.11 e versioni successive**: In quarantena</br></br>- **Windows 8.1 e versioni successive**: In quarantena</br>- **Windows Phone 8.1 e versioni successive**: In quarantena |
| **Versione massima del sistema operativo** | - **Android 4.0 e versioni successive**: In quarantena</br>- **Samsung KNOX Standard 4.0 e versioni successive**: In quarantena</br>- **Android Enterprise**: In quarantena</br></br>- **iOS 8.0 e versioni successive**: In quarantena</br>- **macOS 10.11 e versioni successive**: In quarantena</br></br>- **Windows 8.1 e versioni successive**: In quarantena</br>- **Windows Phone 8.1 e versioni successive**: In quarantena |
| **Attestazione dell'integrità di Windows** | - **Android 4.0 e versioni successive**: Non applicabile</br>- **Samsung KNOX Standard 4.0 e versioni successive**: Non applicabile</br>- **Android Enterprise**: Non applicabile</br></br>- **iOS 8.0 e versioni successive**: Non applicabile</br>- **macOS 10.11 e versioni successive**: Non applicabile</br></br>- **Windows 10 e Windows 10 Mobile**: In quarantena</br>- **Windows 8.1 e versioni successive**: In quarantena</br>- **Windows Phone 8.1 e versioni successive**: Non applicabile |

---------------------------

**Con correzione**: il sistema operativo del dispositivo impone la conformità. Ad esempio, l'utente è obbligato a impostare un PIN.

**In quarantena**: il sistema operativo del dispositivo non impone la conformità. Ad esempio, l'utente di dispositivi Android e Android Enterprise non è obbligato a crittografare il dispositivo. Se il dispositivo non è conforme, vengono eseguite le azioni seguenti:

- Se all'utente si applica un criterio di accesso condizionale, il dispositivo viene bloccato.
- L'app Portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="azure-classic-portal-vs-azure-portal"></a>Differenze tra portale di Azure classico e Portale di Azure

La differenza principale rispetto all'uso dei criteri di conformità dei dispositivi nel portale di Azure:

- Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata
- Nel portale di Azure classico un criterio di conformità è comune a tutte le piattaforme supportate

<!--- - In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

- In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

I criteri di conformità dei dispositivi creati nel [portale classico](https://manage.microsoft.com) non compaiono nel [portale di Azure](https://portal.azure.com). Tali criteri sono tuttavia destinati agli utenti e gestibili tramite il portale di classico.

Per usare le funzionalità relative alla conformità dei dispositivi nel portale di Azure, è necessario creare nuovi criteri di conformità dei dispositivi nel portale stesso. Se si assegna un criterio di conformità dei dispositivi nel portale di Azure a un utente al quale è assegnato un criterio di conformità dei dispositivi anche dal portale classico, i criteri di conformità dei dispositivi dal portale di Azure avranno la precedenza rispetto a quelli creati nel portale classico.

## <a name="next-steps"></a>Passaggi successivi

- [Creare un criterio](create-compliance-policy.md) e visualizzare i prerequisiti.
- Vedere le impostazioni di conformità per le diverse piattaforme per dispositivi:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows 10 e versioni successive](compliance-policy-create-windows.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows 8.1 e Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- Per informazioni sulle entità del criterio Data warehouse di Intune, vedere [Informazioni di riferimento per le entità della categoria Policy](../reports-ref-policy.md).