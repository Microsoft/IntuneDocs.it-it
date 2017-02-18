---
title: Connessioni VPN | Documentazione Microsoft
description: Usare i profili VPN per distribuire le impostazioni VPN agli utenti e ai dispositivi dell&quot;organizzazione.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0154e3bfeac0457de57257045e3e7ce833325bce
ms.openlocfilehash: a462bcfa107bf1a37ea4e84bc3d88d0dd81f9fc8


---

# <a name="vpn-connections-in-microsoft-intune"></a>Connessioni VPN in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un *profilo di connessione VPN* per stabilire una connessione con il server VPN. Usare i *profili VPN* in Microsoft Intune per distribuire le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.

Si supponga, ad esempio, di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Creare un profilo VPN contenente le impostazioni necessarie per connettersi alla rete aziendale e quindi distribuire tale profilo a tutti gli utenti che usano dispositivi iOS. Gli utenti visualizzano la connessione VPN nell'elenco delle reti disponibili e possono connettersi con la massima facilità.

I profili VPN consentono di configurare i tipi di dispositivo seguenti:

* Dispositivi che eseguono Android 4 e versioni successive
* Dispositivi Android for Work
* Dispositivi che eseguono iOS 8.0 e versione successiva
* Dispositivi che eseguono Mac OS X 10.9 e versioni successive
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Dispositivi che eseguono Windows Phone 8.1 e versioni successive
* Dispositivi che eseguono Windows 10 Desktop e Mobile

Le opzioni di configurazione del profilo VPN variano a seconda del tipo di dispositivo selezionato.

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

Intune supporta la creazione di profili VPN che usano i tipi di connessione seguenti:


Tipo di connessione |iOS e Mac OS X  |Android e Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop e Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Sì |Sì   |No    |No  |No    | Sì, (URI OMA, solo dispositivi mobili)|     
Cisco (IPsec)|sì |Sì   |No  |No  |No | No|
Citrix|sì |Sì (solo Android)   |No  |No  |No | No|
Pulse Secure|Sì  |Sì |Sì   |Sì  |Sì| Sì|        
F5 Edge Client|Sì |Sì |Sì |Sì  |   Sì |  Sì|   
Dell SonicWALL Mobile Connect|Sì |Sì |Sì |Sì |Sì |Sì|         
VPN CheckPoint Mobile|Sì |Sì |Sì |Sì|Sì|Sì|
Microsoft SSL (SSTP)|No |No |No |No|No|VPNv1 URI OMA*|
Microsoft Automatico|No |No |No |No|Sì (URI OMA)|sì|
IKEv2|Profilo personalizzato iOS|No |No |No|Sì (URI OMA)|sì|
PPTP|Profilo personalizzato iOS|No |No |No|No|Sì|
L2TP|Profilo personalizzato iOS|No |No |No|Sì (URI OMA)|sì|

\* Senza impostazioni aggiuntive che sono altrimenti disponibili per Windows 10.

> [!IMPORTANT]
> Prima di usare i profili VPN distribuiti in un dispositivo, è necessario installare l'app VPN applicabile per il profilo È possibile usare le informazioni fornite nell'argomento [Distribuire le app con Microsoft Intune](deploy-apps-in-microsoft-intune.md) per distribuire l'app applicabile usando Intune.  

 Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Configurazioni personalizzate per i profili VPN](create-custom-vpn-profiles.md).     

## <a name="methods-of-securing-vpn-profiles"></a>Metodi per la protezione dei profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante uno dei due metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PFX creato precedentemente in Intune. Questo metodo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene distribuito nel computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere il documento relativo alla [protezione dell'accesso alle risorse con i profili certificato](secure-resource-access-with-certificate-profiles.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.

## <a name="create-a-vpn-profile"></a>Creare un profilo VPN

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** > **Aggiungi criterio**.
2. Selezionare un modello per il nuovo criterio espandendo il tipo di dispositivo pertinente e quindi scegliere il profilo VPN per il dispositivo:
    * **Profilo VPN (Android 4 e versioni successive)**
    * **Profilo VPN (Android for Work)**
    * **Profilo VPN (iOS 8.0 e versioni successive)**
    * **Profilo VPN (Mac OS X 10.9 e versioni successive)**
    * **Profilo VPN (Windows 8.1 e versioni successive)**
    * **Profilo VPN (Windows Phone 8.1 e versioni successive)**
    * **Profilo VPN (Windows 10 Desktop e Mobile e versioni successive)**

 È possibile creare e distribuire soltanto criteri personalizzati dei profili VPN. Le impostazioni consigliate non sono disponibili.

> [!Note]
> Un profilo VPN per i dispositivi Android for Work abilita una connessione VPN solo per le app installate nel profilo di lavoro del dispositivo.
>
> Alcuni tipi di connessione VPN supportano la funzione VPN per app per i dispositivi Android for Work per i dispositivi di lavoro e per l'abilitazione della funzione VPN per app per le app distribuite tramite Intune.  

3. Usare la tabella seguente per configurare le impostazioni del profilo VPN:

Nome impostazione  |Altre informazioni  
---------|---------
**Nome**     |Immettere un nome univoco per il profilo VPN che consenta di identificarlo nella console di Intune.         
**Descrizione**     |Fornire una descrizione di carattere generale sul profilo VPN e altre informazioni rilevanti per consentirne l'individuazione.         
**Nome connessione VPN (visualizzato agli utenti)**     |Specificare un nome per il profilo VPN. Si tratta del nome visualizzato agli utenti nell'elenco delle connessioni VPN disponibili nei dispositivi.         
**Tipo di connessione**     |  Selezionare uno dei tipi di connessione seguenti da usare nel profilo VPN: **Cisco AnyConnect** (non disponibile per Windows 8.1 o Windows Phone 8.1), **Pulse Secure**, **Citrix**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **VPN CheckPoint Mobile**.
**Descrizione server VPN**     | Specificare una descrizione per il server VPN a cui si connetteranno i dispositivi. Esempio: **Server VPN di Contoso**. Se il tipo di connessione è **F5 Edge Client**, usare il campo **Elenco server** per specificare un elenco di descrizioni e indirizzi IP di server.
**Indirizzo IP o FQDN server**    |Specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.  Se il tipo di connessione è **F5 Edge Client**, usare il campo **Elenco server** per specificare un elenco di descrizioni e indirizzi IP di server.         |         
**Elenco server**     |Fare clic su **Aggiungi** per aggiungere un nuovo server VPN da usare per la connessione VPN. È inoltre possibile specificare il server predefinito per la connessione. Questa opzione viene visualizzata solo quando il tipo di connessione è **F5 Edge Client**.         
**Invia tutto il traffico di rete tramite la connessione VPN**     |Se si seleziona questa opzione, tutto il traffico di rete verrà inviato tramite la connessione VPN. Se non si seleziona questa opzione, il client negozierà in modo dinamico le route per lo split tunneling al momento della connessione al server VPN di terze parti. Solo le connessioni alla rete aziendale vengono inviate tramite un tunnel VPN. Il tunneling VPN non viene usato quando si esegue la connessione alle risorse su Internet.
**Metodo di autenticazione**| Selezionare il metodo di autenticazione usato dalla connessione VPN: **Certificati** oppure **Nome utente e password**. L'impostazione **Nome utente e password** non è disponibile per il tipo di connessione Cisco AnyConnect. L'opzione **Metodo di autenticazione** non è disponibile per Windows 8.1.
**Memorizza le credenziali utente a ogni accesso**|selezionare questa opzione per garantire che le credenziali utente vengano memorizzate in modo che l'utente non debba immetterle ogni volta che viene stabilita una connessione.
**Selezionare un certificato client per l'autenticazione client (certificato di identità)**|Selezionare il certificato SCEP client creato in precedenza e che verrà usato per autenticare la connessione VPN. Per altre informazioni su come usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con profili di certificato) Questa opzione viene visualizzata solo quando il metodo di autenticazione è **Certificati**.
**Ruolo**| Specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso. Questa opzione viene visualizzata solo quando il tipo di connessione è **Pulse Secure** o **Citrix**.
**Area di autenticazione**|Specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure o Citrix. Questa opzione viene visualizzata solo quando il tipo di connessione è **Pulse Secure** o **Citrix**.
**Gruppo o dominio di accesso**|Specificare il nome del gruppo di accesso o di dominio a cui connettersi. Questa opzione viene visualizzata solo quando il tipo di connessione è **Dell SonicWALL Mobile Connect**.
**Impronta digitale**|Specificare una stringa, ad esempio "Codice impronta digitale Contoso", che verrà usata per verificare l'attendibilità del server VPN. È possibile inviare un'impronta digitale al client per indicargli di considerare attendibile qualsiasi server che presenta la stessa impronta digitale durante la connessione. Se il dispositivo non ha ancora l'impronta digitale, richiederà all'utente di considerare attendibile il server VPN usato per la connessione durante la visualizzazione dell'impronta digitale. L'utente verifica manualmente l'impronta digitale e sceglie **Attendibilità** per connettersi. Questa opzione viene visualizzata solo quando il tipo di connessione è **VPN CheckPoint Mobile**.
**Per VPN app**|Selezionare questa opzione se si vuole associare questa connessione VPN a un'app iOS o Mac OS X in modo da aprire la connessione quando si esegue l'app. Quando si distribuisce il software, è possibile associare il profilo VPN a un'app. Per altre informazioni vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**VPN su richiesta**|È possibile impostare la connessione VPN su richiesta per i dispositivi iOS 8.0 e versione successiva. In [Connessione VPN su richiesta per dispositivi iOS](#on-demand-vpn-for-ios-devices) vengono fornite istruzioni per la configurazione.
**Rileva automaticamente impostazioni proxy** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
**Usa script di configurazione automatica** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, specificare se si desidera usare uno script di configurazione automatica per definire le impostazioni e quindi specificare l'URL del file contenente le impostazioni. Per altre informazioni, vedere la documentazione di Windows Server.
**Usa server proxy** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, selezionare questa opzione e quindi specificare il numero di porta e l'indirizzo del server proxy. Per altre informazioni, vedere la documentazione di Windows Server.
**Disabilita le impostazioni del proxy per gli indirizzi locali** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.
**XML personalizzato** (solo per Windows 8.1 e Windows Phone 8.1 e versioni successive)|Specificare i comandi XML personalizzati per la configurazione della connessione VPN. Esempio per **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Esempio per **VPN CheckPoint Mobile**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Esempio per **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Esempio per **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Per altre informazioni su come scrivere comandi XML personalizzati, fare riferimento alla documentazione della VPN fornita dai diversi produttori.
**Elenco di ricerca suffissi DNS** (solo per Windows Phone 8.1)|Specificare un solo suffisso DNS per ogni riga. Ogni suffisso DNS specificato verrà cercato al momento della connessione a un sito Web mediante un nome breve. Ad esempio, specificare i suffissi DNS **domain1.contoso.com** e **domain2.contoso.com** e visitare l'URL **http://mywebsite**: verranno cercati gli URL **http://mywebsite.domain1.contoso.com** e **http://mywebsite.domain2.contoso.com**.
**Disabilita VPN quando il dispositivo è connesso alla rete Wi-Fi aziendale** (solo per Windows Phone 8.1)|Selezionare questa opzione per specificare che la connessione VPN non verrà usata quando il dispositivo è connesso alla rete Wi-Fi aziendale.
**Disabilita VPN quando il dispositivo è connesso alla rete Wi-Fi domestica** (solo per Windows Phone 8.1)|Selezionare questa opzione per specificare che la connessione VPN non verrà usata quando il dispositivo è connesso a una rete Wi-Fi domestica.

Per i dispositivi Windows 10 Desktop e Mobile sono disponibili anche le impostazioni seguenti:

Nome impostazione  |Altre informazioni  
---------|---------
**Regole del traffico di rete**|Selezionare i protocolli, le porte e gli intervalli di indirizzi locali e remoti che verranno abilitati per la connessione VPN. Se non si crea una regola del traffico di rete, verranno abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo la creazione di una regola, la connessione VPN userà soltanto i protocolli, le porte e gli intervalli di indirizzi specificati in tale regola.
**Route**|Selezionare le route che verranno usate dalla connessione VPN.
**Server DNS**| Selezionare i server DNS che verranno usati dalla connessione VPN una volta stabilita la connessione.         
**App associate**|Fornire un elenco di app che useranno automaticamente la connessione VPN. Il tipo di app determinerà l'identificatore dell'app. Per un'app universale, specificare il nome della famiglia di pacchetti. Per un'app desktop, specificare il percorso file dell'app.          


> [!IMPORTANT]
> È consigliabile proteggere tutti gli elenchi delle app compilate da usare per la configurazione della VPN per app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco della VPN per app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

Di seguito è riportata una situazione di esempio in cui è possibile usare le impostazioni dei limiti aziendali. Se si vuole abilitare la connessione VPN solo per il desktop remoto, creare una regola del traffico di rete che consente il traffico per il numero di protocollo 27 sulla porta esterna 3996. Nessun altro tipo di traffico userà la connessione VPN.

Definire le route nei limiti aziendali è utile quando il tipo di connessione VPN non consente di definire il modo in cui viene gestito il traffico nello split tunneling. In tal caso, usare **Route** per elencare le route che useranno la connessione VPN.

È possibile limitare ad app specifiche l'uso della connessione VPN nei dispositivi Windows 10 creando un'impostazione OMA-URI personalizzata.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri**.

### <a name="on-demand-vpn-for-ios-devices"></a>Connessione VPN su richiesta per dispositivi iOS
È possibile configurare la connessione VPN su richiesta per i dispositivi iOS 8.0 e versioni successive.

> [!NOTE]
>  
> Non è possibile usare la connessione VPN per app e VPN su richiesta nello stesso criterio.

1. Nella pagina di configurazione dei criteri, trovare **Regole su richiesta per questa connessione VPN**. Le colonne sono denominate **Corrispondenza**, la condizione verificata dalle regole, e **Azione**, l'azione che il criterio attiverà quando la condizione verrà soddisfatta.
2. Scegliere **Aggiungi** per creare una regola. Nella regola è possibile impostare due tipi di corrispondenze. È possibile configurare solo uno di questi tipi per ogni regola.
  - **SSID**, che fanno riferimento alle reti wireless.
  - **Domini di ricerca DNS**, che sono...  È possibile usare nomi di dominio completo, ad esempio *team. corp.contoso.com*, oppure usare domini quali *contoso.com*, che è equivalente all'uso di * *.contoso.com*.
3. Facoltativo: specificare un probe della stringa dell'URL, ovvero un URL che viene usato come test. Se il dispositivo in cui è installato il profilo è in grado di accedere a tale URL senza il reindirizzamento, verrà stabilita la connessione VPN e il dispositivo si connetterà all'URL di destinazione. L'utente non visualizzerà il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi la capacità della rete VPN di connettersi a un sito, prima di connettere il dispositivo all'URL di destinazione tramite VPN.
4. Scegliere una delle azioni seguenti:
  - **Connessione**
  - **Valuta la connessione**, che presenta tre impostazioni. a. **Azione del dominio**: scegliere **Connetti se necessario** o **Non connettere mai**
    . b. **Elenco di domini separati da virgole**: configurarla solo se si sceglie **Azione del dominio** **Connetti se necessario**
    . c. **Probe della stringa dell'URL necessario**: un URL HTTP o HTTPS (consigliato), ad esempio *https://vpntestprobe.contoso.com*. La regola verificherà se esiste una risposta da questo indirizzo. In caso contrario e se **Azione del dominio** è **Connetti se necessario**, la connessione VPN verrà attivata.
     > [!TIP]
     >
     >Un esempio di quando è possibile usare questa azione riguarda il fatto che alcuni siti della rete aziendale richiedono una connessione alla rete aziendale diretta o VPN, mentre altri no. Se si elencano i domini in **Elenco di domini separati da virgole** *corp.contoso.com*, è possibile scegliere **Connetti se necessario** e quindi elencare siti specifici nella rete che può richiedere una connessione VPN, ad esempio *sharepoint.corp.contoso.com*. La regola controllerà quindi se *vpntestprobe.contoso.com* può essere raggiunto. Se non è possibile, la connessione VPN verrà attivata per il sito di SharePoint.
  - **Ignorato**: questo non comporta alcuna modifica nella connettività VPN. Se la connessione VPN è stabilita, lasciarla invariata. In caso contrario, non stabilirla. Ad esempio, è possibile che si disponga di una regola che si connette alla rete VPN per tutti i siti Web aziendali interni, ma si vuole che uno di quei siti interni sia accessibile solo quando il dispositivo è attualmente connesso alla rete aziendale. In tal caso, è consigliabile creare una regola che ignori tale sito.
  - **Disconnetti**: disconnettere i dispositivi dalla rete VPN quando le condizioni vengono soddisfatte. Ad esempio, è possibile elencare le reti wireless aziendali nel campo **SSID** e creare una regola che consente di disconnettere i dispositivi dalla rete VPN quando si connettono a una di tali reti.

Le regole specifiche del dominio vengono valutate prima delle regole di tutti i domini.


## <a name="deploy-the-policy"></a>Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   Per distribuire il criterio, selezionare uno o più gruppi a cui lo si vuole distribuire e quindi scegliere **Aggiungi** &gt; **OK**.

    -   Per chiudere la finestra di dialogo senza distribuirlo, scegliere **Annulla**.


Al termine della distribuzione, il nome della connessione VPN specificato verrà visualizzato nell'elenco delle connessioni VPN sui dispositivi.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.



<!--HONumber=Feb17_HO1-->


