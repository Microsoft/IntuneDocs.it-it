---
title: Come usare i criteri di configurazione delle app di Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare i criteri di configurazione delle app per fornire i dati di configurazione a un&quot;app iOS in esecuzione.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 82af84bc3e31317023a2f8f7089431b1dbcaed52
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-use-microsoft-intune-app-configuration-policies"></a>Come usare i criteri di configurazione delle app di Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un'app iOS. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

-   Un numero di porta personalizzato.

-   Impostazioni della lingua.

-   Impostazioni di sicurezza.

-   Impostazioni di personalizzazione, ad esempio il logo aziendale.

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app permettono di evitare questi problemi consentendo di assegnare tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi distribuita. Le impostazioni dei criteri vengono usate ogni volta che l'app ne esegue la ricerca (in genere, alla prima esecuzione).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [How to add an app to Microsoft Intune](/intune-azure/manage-apps/add-apps) (Come aggiungere un'app a Microsoft Intune).

## <a name="create-an-app-configuration-policy"></a>Creare criteri di configurazione delle app

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
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

Procedere quindi ad [assegnare](deploy-apps.md) e [monitorare](monitor-apps.md) normalmente le app.

Quando l'app assegnata viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app.

> [!TIP]
> Se uno o più criteri di configurazione delle app sono in conflitto, non verrà applicato alcun criterio.

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

