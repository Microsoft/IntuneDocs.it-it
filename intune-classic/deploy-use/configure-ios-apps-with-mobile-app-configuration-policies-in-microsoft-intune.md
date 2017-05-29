---
title: Usare i criteri di configurazione delle app per dispositivi mobili iOS | Documentazione Microsoft
description: Usare i criteri di configurazione delle app mobili in Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un&quot;app iOS.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 48f31fa1a883abc2bba372c3aaffb1f998d33c00
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare i criteri di configurazione delle app mobili in Microsoft Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un'app iOS. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

-   Un numero di porta personalizzato.

-   Impostazioni della lingua.

-   Impostazioni di sicurezza.

-   Impostazioni di personalizzazione, ad esempio il logo aziendale.

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app mobili permettono di evitare questi problemi consentendo di distribuire tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Questi criteri non vengono distribuiti direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi distribuita. Le impostazioni dei criteri vengono usate ogni volta che l'app ne esegue la ricerca (in genere, alla prima esecuzione).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [Distribuire le app con Microsoft Intune](deploy-apps.md)

## <a name="configure-a-mobile-app-configuration-policy"></a>Configurare un criterio di configurazione delle app mobili

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Nell'elenco dei criteri espandere **iOS**, scegliere **Configurazione delle app per dispositivi mobili** e quindi scegliere **Crea criterio**.

    > [!TIP]
    > Per questo tipo di criterio è possibile configurare solo le impostazioni personalizzate. Le impostazioni consigliate non sono disponibili.

3.  Nella sezione **Generale** della pagina **Crea criterio** specificare un nome e una descrizione facoltativa per il criterio di configurazione delle app mobili.

4.  Nella casella della sezione **Criterio di configurazione delle app per dispositivi mobili** della pagina immettere o incollare un elenco di proprietà XML contenente le impostazioni di configurazione delle app desiderate. Il formato dell'elenco di proprietà XML varia a seconda dell'app da configurare. Per altre informazioni sul formato esatto da usare, contattare il fornitore dell'app.

    > [!TIP]
    > Per altre informazioni sugli elenchi di proprietà XML, vedere l'articolo relativo agli [elenchi di proprietà XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) nella libreria degli sviluppatori iOS.

5.  Fare clic su **Convalida** per verificare che il formato dell'elenco di proprietà XML immesso sia valido.

    > [!IMPORTANT]
    > Quando si fa clic su **Convalida**, Intune verifica che il file XML aggiunto sia in un formato valido. Non verifica che l'elenco di proprietà XML funzioni con l'app a cui è associato.

6.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio verrà visualizzato nel nodo **Criteri di configurazione** .

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

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>Associare un criterio di configurazione delle app mobili a un'app
Dopo aver creato un criterio di configurazione delle app mobili, è necessario associarlo all'app iOS a cui si vogliono applicare le impostazioni del criterio di configurazione.

A tale scopo, seguire i passaggi per la creazione di una distribuzione di app in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) e [Distribuire app con Microsoft Intune](deploy-apps-in-microsoft-intune.md). Quando viene visualizzata la pagina **Configurazione delle app per dispositivi mobili** della procedura guidata, selezionare il criterio che si vuole associare all'app dall'elenco a discesa **Criterio di configurazione dell'app**.

Continuare quindi a distribuire e monitorare la distribuzione dell'app come di consueto.

Quando l'app distribuita viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app mobili.

> [!TIP]
> Se uno o più criteri di configurazione delle app mobili sono in conflitto, non verrà applicato alcun criterio. Il conflitto verrà segnalato nel **Dashboard** della console di amministrazione di Intune.

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>Formato di esempio per file XML di configurazione di app per dispositivi mobili

Quando si crea un file di configurazione di app per dispositivi mobili, è possibile specificare uno o più dei seguenti valori usando questo formato:

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

