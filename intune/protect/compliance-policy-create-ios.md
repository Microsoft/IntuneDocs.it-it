---
title: Impostazioni di conformità di iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi iOS in Microsoft Intune. Richiedere un indirizzo di posta elettronica, controllare dispositivi jailbroken o rooted, impostare la versione minima e massima del sistema consentita, impostare le restrizioni relative alla password, inclusa la lunghezza della password e il periodo di inattività del dispositivo, creare restrizioni per le app e così via.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b83b764af415349b287df2a09f9b4c355734c28
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810245"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di iOS per contrassegnare un dispositivo come conforme o non conforme in Intune

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi iOS in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per richiedere un indirizzo di posta elettronica, contrassegnare i dispositivi rooted (Jailbroken) come non conformi, impostare un livello di rischio consentito, impostare la scadenza delle password e così via.

Questa funzionalità si applica a:

- iOS
- iPados

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma**, selezionare **iOS/iPadOS**.

## <a name="email"></a>Posta elettronica

- **Rendi obbligatorio un profilo di posta elettronica gestito nei dispositivi mobili**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Rendi obbligatorio**: i dispositivi che non hanno un profilo di posta elettronica gestito da Intune non sono considerati conformi. Un dispositivo potrebbe non avere un profilo di posta elettronica gestito quando non viene specificato correttamente come destinazione oppure se l'utente ha configurato manualmente l'account di posta elettronica nel dispositivo.

  Il dispositivo è considerato non conforme nelle situazioni seguenti:  
  - Il profilo di posta elettronica viene assegnato a un gruppo di utenti diverso rispetto al gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo configurato dall'utente e non può gestirlo. Per assicurare la conformità, l'utente finale deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.  

Per informazioni dettagliate sui profili di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Intune](../configuration/email-settings-configure.md).

## <a name="device-health"></a>Integrità del dispositivo

- **Dispositivi jailbroken**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Blocca**: contrassegnare i dispositivi rooted (jailbroken) come non conformi.  

- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo** *(iOS 8.0 e versioni successive)* :  
  Usare questa impostazione per eseguire la valutazione dei rischi come condizione per la conformità. Scegliere il livello di minaccia consentito:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato non conforme.
  - **Alto**: questa opzione è la meno sicura poiché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

## <a name="device-properties"></a>Proprietà dispositivo

### <a name="operating-system-version"></a>Versione del sistema operativo  

- **Sistema operativo minimo richiesto** *(iOS 8,0 e versioni successive)* :  
  Quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse dell'organizzazione.

- **Versione massima del sistema operativo consentita** *(iOS 8,0 e versioni successive)* :  
  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella della regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché una regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Versione minima build del sistema operativo** *(iOS 8,0 e versioni successive)* :  
  quando Apple pubblica aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build minimo consentito nel dispositivo.

- **Versione massima build del sistema operativo** *(iOS 8,0 e versioni successive)* :  
  quando Apple pubblica aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build massimo consentito nel dispositivo.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

> [!NOTE]
> Dopo l'applicazione di criteri di conformità o di configurazione a un dispositivo iOS, agli utenti viene richiesto ogni 15 minuti di impostare un passcode. Tale richiesta viene visualizzata finché non viene impostato un passcode. Quando viene impostato un codice per il dispositivo iOS, viene avviato automaticamente il processo di crittografia. Il dispositivo resta crittografato fino a quando non viene disabilitato il codice.

- **Richiedi una password per sbloccare i dispositivi mobili**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.  
  - **Rendi obbligatorio**: gli utenti devono immettere una password prima di accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.

- **Password semplici**:  
  - **Non configurato** (*impostazione predefinita*): gli utenti possono creare password semplici, ad esempio **1234** o **1111**.
  - **Blocca**: impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. 

- **Lunghezza minima password**:  
  immettere il numero minimo di cifre o caratteri che la password deve avere.  

- **Tipo di password richiesto**:  
  scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).

- **Numero di caratteri non alfanumerici nella password**:  
  immettere il numero minimo di caratteri speciali, ad esempio `&`, `#`, `%`, `!` e così via, che è necessario includere nella password. 

  Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** *(iOS 8.0 e versioni successive)* :  
  Specificare il momento in cui la schermata è bloccata prima che un utente debba immettere una password per accedere al dispositivo. Le opzioni includono il valore predefinito *non configurato*, *immediatamente*e da *1 minuto* a *4 ore*.

- **Numero massimo di minuti di inattività fino al blocco dello schermo**:  
  Immettere il tempo di inattività prima che il dispositivo blocchi la schermata. Le opzioni includono il valore predefinito *non configurato*, *immediatamente*e da *1 minuto* a *15 minuti*.

- **Scadenza password (giorni)** :  
  selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password. 

- **Numero di password precedenti di cui impedire il riutilizzo**  *(iOS 8.0 e versioni successive)* :   
  immettere il numero di password usate in precedenza che non è possibile usare.

### <a name="device-security"></a>Sicurezza del dispositivo

- **App con restrizioni**:  
  È possibile creare restrizioni per le app aggiungendo i relativi ID bundle ai criteri. Se in un dispositivo è installata l'app, il dispositivo verrà contrassegnato come non conforme.

  - **Nome app**: immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle.
  - **ID bundle dell'app**: immettere l'identificatore univoco del bundle assegnato dal provider dell'app. Per trovare l'ID bundle, vedere [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (Come trovare l'ID bundle per app iOS). Si aprirà un altro sito Web Microsoft.  

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi macOS](compliance-policy-create-mac-os.md).
