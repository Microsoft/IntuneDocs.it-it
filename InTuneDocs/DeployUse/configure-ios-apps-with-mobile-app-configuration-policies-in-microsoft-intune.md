---
# required metadata

title: Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune
Usare i criteri di configurazione delle app mobili in Microsoft Intune per specificare le impostazioni che potrebbero essere richieste quando l'utente esegue un'app. Ad esempio, un'app potrebbe richiedere all'utente di specificare:

-   Numero di porta personalizzato per l'esecuzione

-   Impostazione della lingua

-   Impostazioni di sicurezza

-   Impostazioni di personalizzazione, ad esempio il logo aziendale

Se queste impostazioni vengono immesse in modo non corretto dall'utente, si può avere un aumento del carico dell'help desk rallentando inoltre l'adozione di nuove app.

I criteri di configurazione delle app mobili permettono di evitare questi problemi consentendo di distribuire tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e l'utente non deve intraprendere alcuna azione.

Questi criteri non vengono distribuiti direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi distribuita. Le impostazioni dei criteri vengono usate ogni volta che l'app ne esegue la ricerca (in genere, alla prima esecuzione).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 7.1 e versioni successive e supporta i tipi di installazione di app seguenti:
> 
> -   **App iOS gestita dall'App Store**
> -   **Pacchetto app per iOS**
> 
> Per altre informazioni sui tipi di installazione delle app, vedere [Distribuire app con Microsoft Intune](deploy-apps.md).

## Configurare un criterio di configurazione delle app mobili

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Nell'elenco dei criteri espandere **iOS**, fare clic su **Configurazione delle app per dispositivi mobili**, quindi fare clic su **Crea criterio**.

    > [!TIP]
    > È possibile configurare solo le impostazioni personalizzate per questo tipo di criterio. Le impostazioni consigliate non sono disponibili.

3.  Nella sezione **Generale** della pagina **Crea criterio** specificare un nome e una descrizione facoltativa per il criterio di configurazione delle app mobili.

4.  Nella sezione **Criterio di configurazione delle app per dispositivi mobili** della pagina immettere o incollare un elenco di proprietà XML contenente le impostazioni di configurazione delle app desiderate.

    > [!TIP]
    > Per altre informazioni sugli elenchi di proprietà XML, vedere l'articolo relativo agli [elenchi di proprietà XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) nella libreria degli sviluppatori iOS.
    > 
    > Il formato dell'elenco di proprietà XML varia a seconda dell'app da configurare. Per altre informazioni sul formato esatto da usare, contattare il fornitore dell'app.
    > 
    > Intune supporta i tipi di dati seguenti in un elenco di proprietà:
    > 
    > &lt;integer&gt;
    > &lt;real&gt;
    > &lt;stringa&gt;
    > &lt;matrice&gt;
    > &lt;dict&gt;
    > &lt;true /&gt; o &lt;false /&gt;
    > 
    > Per altre informazioni sui tipi di dati, vedere l'articolo relativo agli [elenchi di proprietà](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) nella libreria degli sviluppatori iOS.
    >
        > Intune supporta anche i tipi di token seguenti nell'elenco di proprietà:
    >    
    > \{\{userprincipalname\}\} - (Esempio: **John@contoso.com**)
    > \{\{mail\}\} - (Esempio: **John@contoso.com**)
    > \{\{partialupn\}\} - (Esempio: **John**)
    > \{\{accountid\}\} - (Esempio: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
    > \{\{deviceid\}\} - (Esempio: **b9841cd9-9843-405f-be28-b2265c59ef97**)
    > \{\{userid\}\} - (Esempio: **3ec2c00f-b125-4519-acf0-302ac3761822**)
    > \{\{username\}\} - (Esempio: **John Doe**)
    > \{\{serialnumber\}\} - (Esempio: **F4KN99ZUG5V2**) per i dispositivi iOS
    > \{\{serialnumberlast4digits\}\} - (Esempio: **G5V2**) per i dispositivi iOS
>
> I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.




5.  Fare clic su **Convalida** per verificare che il formato della proprietà XML immessa sia valido.

    > [!IMPORTANT]
    > Quando si fa clic su **Convalida**, Intune verifica che il file XML aggiunto sia in un formato valido. Non verifica che l'elenco di proprietà XML funzionerà con l'app a cui è associato.

6.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio verrà visualizzato nel nodo **Criteri di configurazione** .

## Associare un criterio di configurazione delle app mobili a un'app
Dopo aver creato un criterio di configurazione delle app mobili, è necessario associarlo all'app iOS a cui si vogliono applicare le impostazioni del criterio di configurazione.

A tale scopo, seguire i passaggi per creare una distribuzione di app in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) e [Distribuire app con Microsoft Intune](deploy-apps-in-microsoft-intune.md) . Quando viene visualizzata la pagina **Configurazione delle app per dispositivi mobili** della procedura guidata, selezionare il criterio che si vuole associare all'app dall'elenco a discesa **Criterio di configurazione dell'app**.

Continuare quindi a distribuire e monitorare la distribuzione dell'app come di consueto.

Quando l'app distribuita viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app mobili.

> [!TIP]
> Se uno o più criteri di configurazione delle app sono in conflitto, nessun criterio viene applicato e il conflitto viene riportato nel **Dashboard** della console di amministrazione di Intune.

## Formato di esempio per file XML di configurazione delle app per dispositivi mobili

Quando si crea un file di configurazione delle app per dispositivi mobili, è possibile specificare uno o più dei seguenti valori usando questo formato:

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




<!--HONumber=May16_HO1-->


