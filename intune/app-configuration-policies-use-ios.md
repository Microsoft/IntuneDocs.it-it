---
title: Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti
titlesuffix: Microsoft Intune
description: Informazioni su come usare i criteri di configurazione delle app per specificare i dati di configurazione per un'app iOS in fase di esecuzione.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3e81b52f10bb94d90d5f66ca5aee13daaf4941e
ms.sourcegitcommit: cefa84efd3003fa5a0ef0c2dce6206a6a411a1ec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35232234"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare impostazioni di configurazione personalizzate per un'app iOS. Queste impostazioni di configurazione consentono di personalizzare un'app in base alle indicazioni dei fornitori. È necessario ottenere queste impostazioni di configurazione (chiavi e valori) dal fornitore dell'app. Per configurare l'app, specificare le impostazioni come chiavi e valori oppure come file XML contenente le chiavi e valori. Inoltre, questi criteri di configurazione non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri di configurazione vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

Dopo aver aggiunto un criterio di configurazione dell'app, è possibile impostare le assegnazioni per i criteri di configurazione dell'app. Quando si impostano le assegnazioni per i criteri, è possibile scegliere di includere ed escludere i gruppi di utenti ai quali vengono applicati i criteri. Quando si sceglie di includere uno o più gruppi, è possibile selezionare i gruppi specifici da includere o selezionare i gruppi predefiniti. I gruppi predefiniti includono **Tutti gli utenti**, **Tutti i dispositivi**, e **Tutti gli utenti + Tutti i dispositivi**. 

>[!NOTE]
>Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console con le ottimizzazioni predefinite. È consigliabile usare questi gruppi per scegliere tutti gli utenti e tutti i dispositivi invece dei gruppi 'Tutti gli utenti' o 'Tutti i dispositivi' che potrebbero essere stati creati manualmente.

Dopo aver selezionato i gruppi inclusi per i criteri di configurazione dell'applicazione, è anche possibile scegliere i gruppi specifici da escludere. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [How to add an app to Microsoft Intune](apps-add.md) (Come aggiungere un'app a Microsoft Intune).

## <a name="create-an-app-configuration-policy"></a>Creare criteri di configurazione delle app

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Scegliere il carico di lavoro delle **app per dispositivi mobili**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome** - Nome del profilo che viene visualizzato nel portale di Azure.
    - **Descrizione** - Descrizione del profilo che viene visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**: scegliere **Dispositivi gestiti**.
6. Selezionare **iOS** per **Piattaforma**.
7.  Scegliere **App associata**. Nel riquadro **App associata** scegliere l'app gestita alla quale applicare la configurazione e selezionare **OK**.
8.  Nel riquadro **Aggiungi i criteri di configurazione** scegliere **Impostazioni di configurazione**.
9. Selezionare **Formato delle impostazioni di configurazione**. Selezionare una delle opzioni seguenti per aggiungere informazioni XML:
    - **Usare la finestra di progettazione della configurazione**
    - **Immettere i dati XML**<br></br>
    Per informazioni dettagliate sull'uso della finestra di progettazione della configurazione, vedere [Usare Progettazione configurazione](#use-configuration-designer). Per informazioni dettagliate sull'immissione di dati XML, vedere [Immettere i dati XML](#enter-xml-data). 
10. Dopo aver aggiunto le informazioni XML, scegliere **OK**, quindi scegliere **Aggiungi** per aggiungere i criteri di configurazione. Viene visualizzato il riquadro di panoramica dei criteri di configurazione.
11. Selezionare **Assegnazioni** per visualizzare le opzioni di inclusione ed esclusione. 

    ![Screenshot della scheda Includi in Assegnazioni](./media/app-config-policy01.png)
12. Selezionare **Tutti gli utenti** nella scheda **Includi**.

    ![Screenshot delle assegnazioni dei criteri - opzione di elenco a discesa Tutti gli utenti](./media/app-config-policy02.png)
13. Selezionare la scheda **Escludi**. 
14. Fare clic su **Selezionare i gruppi da escludere** per visualizzare il riquadro correlato.

    ![Screenshot delle assegnazioni dei criteri - Pannello Selezionare i gruppi da escludere](./media/app-config-policy03.png)
15. Scegliere i gruppi da escludere e quindi fare clic su **Seleziona**.

    >[!NOTE]
    >Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, tale gruppo risulterà preselezionato e non potrà essere modificato per gli altri tipi di assegnazione di inclusione. Di conseguenza, tale gruppo non potrà essere usato come gruppo escluso.
16. Fare clic su **Save**.

## <a name="use-configuration-designer"></a>Usare Progettazione configurazione

Microsoft Intune fornisce impostazioni di configurazione univoche per un'app. È possibile usare la finestra di progettazione della configurazione per le app disponibili in dispositivi registrati o non registrati in Microsoft Intune. La finestra di progettazione consente di configurare chiavi e valori di configurazione specifici utili per creare il codice XML sottostante. È anche necessario specificare il tipo di dati per ogni valore. Queste impostazioni vengono fornite automaticamente alle app al momento dell'installazione.

### <a name="add-a-setting"></a>Aggiungere un'impostazione

1. Per ogni chiave e valore nella configurazione, impostare:
   - **Chiave di configurazione** - Chiave che identifica in modo univoco la configurazione specifica delle impostazioni.
   - **Tipo di valore** - Il tipo di dati del valore di configurazione. I tipi includono Integer, Real, String o Boolean.
   - **Valore di configurazione** - Valore per la configurazione.
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

Procedere con l'[assegnazione](apps-deploy.md) e il [monitoraggio](apps-monitor.md) dell'app.
