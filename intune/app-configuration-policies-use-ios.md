---
title: Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti | Microsoft Docs
titlesuffix: Azure portal
description: Informazioni su come usare i criteri di configurazione delle app per specificare i dati di configurazione per un'app iOS in fase di esecuzione.
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a39b2d120a804d32b93b7a240af246327514b1b7
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app iOS. Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [How to add an app to Microsoft Intune](apps-add.md) (Come aggiungere un'app a Microsoft Intune).

## <a name="create-an-app-configuration-policy"></a>Creare criteri di configurazione delle app

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** + **Intune**.
3. Scegliere il carico di lavoro delle **app per dispositivi mobili**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome**<br>
      Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**<br>
      Descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**<br>
      Scegliere **Dispositivi gestiti**.
6. Selezionare **iOS** per **Piattaforma**.
7.  Scegliere **App associata**. Nel pannello **App associata** scegliere l'app gestita alla quale applicare la configurazione.
8.  Nel pannello **Aggiungi i criteri di configurazione** scegliere **Impostazioni di configurazione**.
9. Selezionare **Formato delle impostazioni di configurazione**. Selezionare una delle opzioni seguenti:
    - **[Usa progettazione configurazione](#Use-the-configuration-designer)**
    - **[Immettere i dati XML](#enter-xml-data)**
10. Scegliere **OK** e quindi **Aggiungi**.

## <a name="use-configuration-designer"></a>Usare Progettazione configurazione

È possibile usare la finestra di progettazione della configurazione per le app disponibili in dispositivi registrati o non registrati in Intune. La finestra di progettazione consente di configurare chiavi e valori di configurazione specifici. È anche necessario specificare il tipo di dati per ogni valore. Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

### <a name="add-a-setting"></a>Aggiungere un'impostazione

1. Per ogni chiave e valore nella configurazione, impostare:
   - **Chiave di configurazione**<br>
     Chiave che identifica in modo univoco la configurazione specifica delle impostazioni.
   - **Tipo di valore**<br>
     Il tipo di dati del valore di configurazione. I tipi includono Integer, Real, String o Boolean.
   - **Valore di configurazione**<br>
     Il valore per la configurazione.
2. Scegliere **OK** per specificare le impostazioni di configurazione.

### <a name="delete-a-setting"></a>Eliminare un'impostazione

1. Scegliere i puntini di sospensione (**...**) accanto all'impostazione.
2. Selezionare **Elimina**.

I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.

## <a name="enter-xml-data"></a>Immettere i dati XML

È possibile digitare o incollare un elenco di proprietà XML contenente le impostazioni di configurazione dell'app per i dispositivi registrati in Intune. Il formato dell'elenco di proprietà XML varia a seconda dell'app da configurare. Per altre informazioni sul formato esatto da usare, contattare il fornitore dell'app.

Intune convalida il formato XML. Tuttavia Intune non verifica se l'elenco di proprietà XML (PList) funziona con l'app di destinazione.

Per altre informazioni sugli elenchi di proprietà XML:

  -  Leggere [Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -  Vedere [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Informazioni sugli elenchi di proprietà XML) nella libreria per gli sviluppatori iOS.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Formato di esempio per file XML di configurazione delle app

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
### <a name="supported-xml-plist-data-types"></a>Tipi di dati supportati nell'elenco di proprietà XML

Intune supporta i tipi di dati seguenti in un elenco di proprietà:

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; o &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>Token usati nell'elenco di proprietà

Intune supporta anche i tipi di token seguenti nell'elenco di proprietà:
- \{\{userprincipalname\}\}, ad esempio **John@contoso.com**
- \{\{mail\}\}, ad esempio **John@contoso.com**
- \{\{partialupn\}\}, ad esempio **John**
- \{\{accountid\}\}, ad esempio **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}, ad esempio **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}, ad esempio **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}, ad esempio **John Doe**
- \{\{serialnumber\}\}, ad esempio **F4KN99ZUG5V2** (per dispositivi iOS)
- \{\{serialnumberlast4digits\}\}, ad esempio **G5V2** (per dispositivi iOS)

## <a name="next-steps"></a>Passaggi successivi

Procedere ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente l'app.