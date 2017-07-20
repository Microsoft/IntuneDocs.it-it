---
title: Come usare i criteri di configurazione delle app di Intune per iOS
titleSuffix: Intune on Azure
description: Informazioni su come usare i criteri di configurazione delle app per fornire i dati di configurazione a un'app iOS in esecuzione."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 112f60ff208c27825ddd0f4c812535b255894333
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Come usare i criteri di configurazione delle app di Microsoft Intune per iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un'app iOS. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

-   Un numero di porta personalizzato.

-   Impostazioni della lingua.

-   Impostazioni di sicurezza.

-   Impostazioni di personalizzazione, ad esempio il logo aziendale.

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app permettono di evitare questi problemi consentendo di assegnare tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri vengono usate ogni volta che l'app ne esegue la ricerca (in genere, alla prima esecuzione).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [How to add an app to Microsoft Intune](apps-add.md) (Come aggiungere un'app a Microsoft Intune).

## <a name="create-an-app-configuration-policy"></a>Creare criteri di configurazione delle app

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1.  Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **Criteri di configurazione dell'app**.

2.  Nel pannello dell'elenco dei criteri scegliere **Aggiungi**.

3.  Nel pannello **Aggiungi i criteri di configurazione** specificare un nome e una descrizione facoltativa per i criteri di configurazione dell'app.
4.  Scegliere **App associata** e nel pannello **App associata** selezionare l'app gestita a cui si desidera applicare la configurazione.
5.  Nel pannello **Aggiungi i criteri di configurazione** scegliere **Impostazioni di configurazione** e nel pannello Impostazioni di configurazione scegliere come si desidera specificare i valori XML che costituiscono il profilo di configurazione:
    - **Immettere i dati XML**: immettere o incollare un elenco di proprietà XML che contiene le impostazioni di configurazione dell'app desiderata. Il formato dell'elenco di proprietà XML varia a seconda dell'app da configurare. Per altre informazioni sul formato esatto da usare, contattare il fornitore dell'app.
    Intune verifica che il file XML aggiunto sia in un formato valido. Non verifica che l'elenco di proprietà XML funzioni con l'app a cui è associato.
    Per altre informazioni sugli elenchi di proprietà XML, vedere l'articolo relativo agli [elenchi di proprietà XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) nella libreria degli sviluppatori iOS.
    - **Usa progettazione configurazione**: consente di specificare coppie chiave-valore XML direttamente nel portale.
8. Al termine, tornare al pannello **Aggiungi i criteri di configurazione** e premere **Crea**.

Il criterio verrà creato e visualizzato nel pannello dell'elenco dei criteri.

Procedere quindi ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente le app.

Quando l'app assegnata viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app.

> [!TIP]
> Se uno o più criteri di configurazione delle app sono in conflitto, non verrà applicato alcun criterio.

## <a name="create-a-mam-targeted-configuration-policy"></a>Creare un criterio di configurazione MAM di destinazione
La configurazione destinata a MAM consente a un'app di ricevere i dati di configurazione tramite Intune App SDK. Il proprietario o lo sviluppatore dell'applicazione deve comunicare ai clienti Intune il formato e le varianti di tali dati. Gli amministratori di Intune possono indirizzare e distribuire i dati di configurazione tramite la console Azure di Intune. I dati della configurazione MAM di destinazione possono essere forniti mediante il servizio MAM alle applicazioni che supportano MAM-WE. Ad esempio, [Intune Managed Browser](https://docs.microsoft.com/intune/app-configuration-managed-browser) ha un elenco di URL consentiti o bloccati. I dati di configurazione dell'applicazione vengono inviati tramite il servizio MAM direttamente all'app invece che tramite il canale MDM. I [criteri di configurazione delle app MDM](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#create-an-app-configuration-policy) sono la soluzione nativa da MDM. La differenza principale rispetto alla configurazione MAM di destinazione è che il dispositivo in cui l'app è in esecuzione non deve essere registrato in MDM. La configurazione MAM di destinazione è disponibile in iOS e Android. Per iOS, è necessario che l'app abbia integrato Intune APP SDK per iOS (v 7.0.1) e faccia parte delle impostazioni di configurazione delle app. La procedura per la creazione di un criterio di configurazione MAM di destinazione è la seguente: 

1. Accedere al **portale Azure**.

2. Scegliere **Intune > App per dispositivi mobili - Criteri di configurazione dell'app**.

3. Nel pannello **Criteri di configurazione dell'app** scegliere **Aggiungi**.

4. Immettere **Nome** e **Descrizione** facoltativa per le impostazioni di configurazione dell'app, quindi scegliere **Non registrato in Intune**.

5. Scegliere **Selezionare le app richieste** e quindi scegliere le app per le piattaforme desiderate nel pannello **App di destinazione**. <br>
**Nota:** per le app line-of-business selezionare **Altre app**. Immettere l'ID del pacchetto per l'applicazione.

6. Scegliere **OK** per tornare al pannello **Aggiungi la configurazione dell'app**.

7. Scegliere **Definisci la configurazione**. Nel pannello **Configurazione** definire le coppie di chiavi e valori per specificare le configurazioni.

8. Al termine, scegliere **OK**.

9. Nel pannello **Aggiungi la configurazione dell'app** scegliere **Crea**.

La nuova configurazione verrà creata e visualizzata nel pannello Configurazione dell'app.

Procedere quindi ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente le app.

Quando l'app assegnata (integrata con Intune APP SDK) viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione MAM di destinazione. Nell'app assegnata deve essere integrata la versione supportata di Intune APP SDK. Per altre informazioni sui requisiti di sviluppo delle app per l'uso dei criteri di configurazione MAM di destinazione, vedere [Guida all'integrazione di Intune APP SDK per iOS](https://docs.microsoft.com/intune/app-sdk-ios).

Per altre informazioni sulle funzionalità dell'API Graph rispetto ai valori di configurazione MAM di destinazione, vedere [Configurazione MAM di destinazione di riferimento per l'API Graph](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="information-about-the-xml-file-format"></a>Informazioni sul formato di file XML

Intune supporta i tipi di dati seguenti in un elenco di proprietà:

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; o &lt;false /&gt;

Per altre informazioni sui tipi di dati, vedere l'articolo relativo agli [elenchi di proprietà](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) nella libreria degli sviluppatori iOS.

Intune supporta anche i tipi di token seguenti nell'elenco di proprietà:
- \{\{userprincipalname\}\} - (esempio: **John@contoso.com**)
- \{\{mail\}\} - (esempio: **John@contoso.com**)
- \{\{partialupn\}\} - (esempio: **Luca**)
- \{\{accountid\}\} - (esempio: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (esempio: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (esempio: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (esempio: **Luca Udinesi**)
- \{\{serialnumber\}\} - (esempio: **F4KN99ZUG5V2**) per dispositivi iOS
- \{\{serialnumberlast4digits\}\} - (esempio: **G5V2**) per dispositivi iOS

I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.

## <a name="example-format-for-an-app-configuration-xml-file"></a>Formato di esempio per file XML di configurazione delle app

Quando si crea un file di configurazione di app, è possibile specificare uno o più dei seguenti valori usando questo formato:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```
