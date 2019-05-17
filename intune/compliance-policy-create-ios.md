---
title: Impostazioni di conformità di iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi iOS in Microsoft Intune. Richiedere un indirizzo di posta elettronica, controllare dispositivi jailbroken o rooted, impostare la versione minima e massima del sistema consentita, impostare le restrizioni relative alla password, inclusa la lunghezza della password e il periodo di inattività del dispositivo, creare restrizioni per le app e così via.
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
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ec071622a2e0d49068864f8bfb47954f54c8ba4
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423612"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di iOS per contrassegnare un dispositivo come conforme o non conforme in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi iOS in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per richiedere un indirizzo di posta elettronica, contrassegnare i dispositivi rooted (Jailbroken) come non conformi, impostare un livello di rischio consentito, impostare la scadenza delle password e così via.

Questa funzionalità si applica a:

- iOS

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma**, selezionare **iOS**.

## <a name="email"></a>Posta elettronica

- **Rendi obbligatorio un profilo di posta elettronica gestito nei dispositivi mobili**: quando si imposta **Richiedi**, i dispositivi che non hanno un profilo di posta elettronica gestito da Intune non sono considerati conformi. Un dispositivo potrebbe non avere un profilo di posta elettronica gestito quando non viene specificato correttamente come destinazione oppure se l'utente ha configurato manualmente l'account di posta elettronica nel dispositivo. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  Il dispositivo è considerato non conforme nelle situazioni seguenti:

  - Il profilo di posta elettronica viene assegnato a un gruppo di utenti diverso rispetto al gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo configurato dall'utente e non può gestirlo. Per assicurare la conformità, l'utente finale deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.

- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune:**: se è stata selezionata l'impostazione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per immettere il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere esistente nel dispositivo.

Per informazioni dettagliate sui profili di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Dispositivi jailbroken**: scegliere **Blocca** per contrassegnare i dispositivi rooted (jailbroken) come non conformi. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo** (iOS 8.0 e versioni successive): usare questa impostazione per considerare la valutazione del rischio come condizione di conformità. Se si sceglie **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità. Per usare questa impostazione, scegliere il livello di minaccia consentito:
  - **Protetto**: questa opzione è la più sicura e indica che il dispositivo non può subire alcuna minaccia. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato non conforme.
  - **Alta**: questa opzione è la meno sicura, perché consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo** (iOS 8.0 e versioni successive): quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse dell'organizzazione.
- **Versione massima del sistema operativo** (iOS 8.0 e versioni successive): quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché una regola non viene modificata in modo da consentire la versione del sistema operativo.
- **Versione minima della build del sistema operativo** (iOS 8.0 e versioni successive): quando Apple pubblica gli aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build minimo consentito nel dispositivo.
- **Versione massima della build del sistema operativo** (iOS 8.0 e versioni successive): quando Apple pubblica gli aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build massimo consentito nel dispositivo.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

> [!NOTE]
> Dopo l'applicazione di criteri di conformità o di configurazione a un dispositivo iOS, agli utenti viene richiesto ogni 15 minuti di impostare un passcode. Tale richiesta viene visualizzata finché non viene impostato un passcode.

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Tipo di password richiesto**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).
- **Numero di caratteri non alfanumerici nella password**: immettere il numero minimo di caratteri speciali, ad esempio `&`, `#`, `%`, `!` e così via, che devono essere inclusi nella password.

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

### <a name="device-security"></a>Sicurezza del dispositivo

- **App con restrizioni**: è possibile creare restrizioni per le app aggiungendo i relativi ID bundle ai criteri. Se in un dispositivo è installata l'app, il dispositivo verrà contrassegnato come non conforme.

  - **Nome app**: immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle.
  - **ID bundle dell'app**: immettere l'identificatore univoco del bundle assegnato dal provider dell'app. Per trovare l'ID bundle, vedere [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (Come trovare l'ID bundle per app iOS). Si aprirà un altro sito Web Microsoft.  

Selezionare **OK** > **Crea** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi macOS](compliance-policy-create-mac-os.md).
