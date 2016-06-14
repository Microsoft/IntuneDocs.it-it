---
# required metadata

title: Connessioni VPN | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Connessioni VPN in Microsoft Intune
 È possibile usare le reti private virtuali (VPN) per offrire agli utenti accesso remoto sicuro alla rete aziendale. Gli utenti remoti possono lavorare come se il dispositivo fosse fisicamente connesso alla rete. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i **profili VPN** in Microsoft Intune per distribuire le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alle risorse nella rete aziendale.

Ad esempio, si supponga di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Creare un profilo VPN contenente le impostazioni necessarie per connettersi alla rete aziendale, quindi distribuire questo profilo a tutti gli utenti con dispositivi iOS. Gli utenti visualizzano la connessione VPN nell'elenco delle reti disponibili e possono connettersi con la massima facilità.

È possibile configurare con profili VPN i seguenti tipi di dispositivo:

* Dispositivi che eseguono Android 4 e versioni successive
* Dispositivi che eseguono iOS 7.1 e versioni successive
* Dispositivi che eseguono Mac OS X 10.9 e versioni successive
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Dispositivi che eseguono Windows Phone 8.1 e versioni successive
* Dispositivi che eseguono Windows 10 Desktop e Mobile.

Le opzioni di configurazione del profilo VPN variano a seconda del tipo di dispositivo selezionato.

## Tipi di connessione VPN

Intune supporta la creazione di profili VPN che usano i tipi di connessione seguenti:




Tipo di connessione |iOS e Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1  |Windows 10 Desktop e Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|------------|
Cisco AnyConnect|Sì |Sì   |No    |     No    |No  |No    | Sì, (URI OMA, solo dispositivi mobili)|     
Pulse Secure|Sì  |Sì |Sì   |No  |Sì  |Sì| Sì|        
F5 Edge Client|Sì |Sì |Sì |No  |Sì  |   Sì |  Sì|   
Dell SonicWALL Mobile Connect|Sì |Sì |Sì |No  |Sì |Sì |Sì|         
VPN CheckPoint Mobile|Sì |Sì |Sì |Sì |Sì|Sì|Sì|
Microsoft SSL (SSTP)|No |No |No |No |No|No|No|
Microsoft Automatico|No |No |No |No |No|No|sì|
IKEv2|No |No |No |No |No|No|sì|
PPTP|No |No |No |No |No|No|sì|
L2TP|No |No |No |No |No|No|sì|


> [!IMPORTANT] Prima di usare i profili VPN distribuiti in un dispositivo, è necessario installare l'app VPN applicabile per il profilo È possibile usare le informazioni nell'argomento [Distribuire le app in dispositivi mobili in Microsoft Intune](deploy-apps-in-microsoft-intune.md) per distribuire l'app applicabile tramite Intune.  

 Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Custom configurations for VPN profiles (Configurazioni personalizzate per i profili VPN)](custom-configurations-for-vpn-profiles.md).     

## Come vengono protetti i profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Per proteggere queste connessioni, si usa in genere uno dei due metodi seguenti:

### Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PFX creato in precedenza in Intune.

Questo profilo, noto come certificato di identità, viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o certificato radice) creato per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene distribuito nel computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con i profili certificato).

### Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve fornire nome utente e password.

## Creare un profilo VPN

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri > Aggiungi criterio**.
2. Selezionare un modello per il nuovo criterio espandendo il tipo di dispositivo interessato, quindi scegliere il profilo VPN per il dispositivo:
    * **Profilo VPN (Android 4 e versioni successive)**
    * **Profilo VPN (iOS 7.1 e versioni successive)**
    * **Profilo VPN (Mac OS X 10.9 e versioni successive)**
    * **Profilo VPN (Windows 8.1 e versioni successive)**
    * **Profilo VPN (Windows Phone 8.1 e versioni successive)**
    * **Profilo VPN (Windows 10 Desktop e Mobile e versioni successive)**

    È possibile solo creare e distribuire criteri personalizzati dei profili VPN. Le impostazioni consigliate non sono disponibili.

3. Usare la tabella seguente per configurare le impostazioni del profilo VPN:

Nome impostazione  |Altre informazioni  
---------|---------
**Nome**     |Immettere un nome univoco per il profilo VPN che consenta di identificarlo nella console di Intune.         
**Descrizione**     |Fornire una descrizione di carattere generale sul profilo VPN e altre informazioni rilevanti per consentirne l'individuazione.         
**Nome connessione VPN (visualizzato agli utenti)**     |Specificare un nome per il profilo VPN. Si tratta del nome visualizzato agli utenti nell'elenco delle connessioni VPN disponibili nei dispositivi.         
**Tipo di connessione**     |  Selezionare uno dei seguenti tipi di connessione da usare nel profilo VPN: **Cisco AnyConnect** (non disponibile per Windows 8.1 o Windows Phone 8.1), **Pulse Secure**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **VPN CheckPoint Mobile**
**Descrizione server VPN**     | Specificare una descrizione per il server VPN a cui si connetteranno i dispositivi. **Esempio:** Server VPN di Contoso Se il tipo di connessione è **F5 Edge Client**, usare il campo **Elenco server** per specificare un elenco di descrizioni e indirizzi IP di server.
**Indirizzo IP o FQDN del server**    |Specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. **Esempi:** 192.168.1.1, vpn.contoso.com.  Se il tipo di connessione è **F5 Edge Client**, usare il campo **Elenco server** per specificare un elenco di descrizioni e indirizzi IP di server.         |         
**Elenco server**     |Fare clic su **Aggiungi** per aggiungere un nuovo server VPN da usare per la connessione VPN. È anche possibile specificare il server da impostare come predefinito per la connessione. Questa opzione viene visualizzata solo quando il tipo di connessione è **F5 Edge Client**.         
**Invia tutto il traffico di rete tramite la connessione VPN**     |Se si seleziona questa opzione, tutto il traffico di rete verrà inviato tramite la connessione VPN. Se non si seleziona questa opzione, il client negozierà in modo dinamico le route per lo split tunneling al momento della connessione al server VPN di terze parti. Solo le connessioni alla rete aziendale vengono inviate tramite un tunnel VPN. Il tunneling VPN non viene usato quando si esegue la connessione alle risorse su Internet.
**Metodo di autenticazione**| Selezionare il metodo di autenticazione usato dalla connessione VPN: **Certificati** oppure **Nome utente e password**. L'impostazione Nome utente e password non è disponibile quando il tipo di connessione è Cisco AnyConnect. L'opzione **Metodo di autenticazione** non è disponibile per Windows 8.1.
**Memorizza le credenziali utente a ogni accesso**|selezionare questa opzione per garantire che le credenziali utente vengano memorizzate in modo che l'utente non debba immetterle ogni volta che viene stabilita una connessione.
**Selezionare un certificato client per l'autenticazione client (certificato di identità)**|Selezionare il certificato SCEP client creato in precedenza che verrà usato per autenticare la connessione VPN. Per altre informazioni su come usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con profili di certificato) Questa opzione viene visualizzata solo quando il metodo di autenticazione è **Certificati**.
**Ruolo**| Specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le impostazioni personali e le opzioni, oltre ad abilitare o disabilitare alcune funzionalità di accesso. Questa opzione viene visualizzata solo quando il tipo di connessione è **Pulse Secure**.
**Area di autenticazione**|Specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure. Questa opzione viene visualizzata solo quando il tipo di connessione è **Pulse Secure**.
**Gruppo o dominio di accesso**|Specificare il nome del gruppo di accesso o di dominio a cui connettersi. Questa opzione viene visualizzata solo quando il tipo di connessione è **Dell SonicWALL Mobile Connect**.
**Impronta digitale**|Specificare una stringa, ad esempio "Codice impronta digitale Contoso", che verrà usata per verificare l'attendibilitàò del server VPN. Un'impronta digitale può essere inviata al client in modo da informarlo che può considerare attendibile un server che presenta la stessa impronta digitale durante la connessione. Se il dispositivo non ha ancora l'impronta digitale, verrà richiesto all'utente di considerare attendibile il server VPN a cui si sta connettendo e verrà visualizzata l'impronta digitale. L'utente verifica manualmente l'impronta digitale e sceglie **Attendibilità** per connettersi. Questa opzione viene visualizzata solo quando il tipo di connessione è **VPN CheckPoint Mobile**.
**Per VPN app**|Selezionare questa opzione se si vuole associare questa connessione VPN a un'app Mac OS X in modo da aprire la connessione quando si esegue l'app. Quando si distribuisce il software, è possibile associare il profilo VPN a un'app. Per altre informazioni, vedere [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Distribuire app in Microsoft Intune)
**Rileva automaticamente impostazioni proxy** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, specificare se si vuole che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
**Usa script di configurazione automatica** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, specificare se si vuole usare uno script di configurazione automatica per definire le impostazioni e quindi specificare l'URL del file contenente le impostazioni. Per altre informazioni, vedere la documentazione di Windows Server.
**Usa server proxy** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, selezionare questa opzione, quindi specificare il numero di porta e l'indirizzo del server proxy. Per altre informazioni, vedere la documentazione di Windows Server.
**Disabilita le impostazioni del proxy per gli indirizzi locali** (solo per iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.
**XML personalizzato** (solo per Windows 8.1 e Windows Phone 8.1 e versioni successive)|Consente di specificare i comandi XML personalizzati che consentono di configurare la connessione VPN. Esempi. Per **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Per **VPN CheckPoint Mobile**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Per **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Per **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Per altre informazioni su come scrivere comandi XML personalizzati, fare riferimento alla documentazione della VPN fornita dai singoli produttori.
**Elenco di ricerca suffissi DNS** (solo per Windows Phone 8.1)|Specificare un solo suffisso DNS per ogni riga. Per cercare ogni suffisso DNS specificato durante la connessione a un sito Web verrà usato un nome breve. Ad esempio, specificare i suffissi DNS **domain1.contoso.com** e **domain2.contoso.com**, visitare l'URL **http://mywebsite** e la ricerca verrà eseguita negli URL **http://mywebsite.domain1.contoso.com** e **http://mywebsite.domain2.contoso.com**.
**Disabilita VPN quando il dispositivo è connesso alla rete Wi-Fi aziendale** (solo per Windows Phone 8.1)|Specifica che la connessione VPN non verrà usata quando il dispositivo è connesso alla rete Wi-Fi aziendale.
**Disabilita VPN quando il dispositivo è connesso alla rete Wi-Fi domestica** (solo per Windows Phone 8.1)|Specifica che la connessione VPN non verrà usata quando il dispositivo è connesso a una rete Wi-Fi domestica.

Per i dispositivi Windows 10 Desktop e Mobile sono disponibili anche le impostazioni seguenti:

Nome impostazione  |Altre informazioni  
---------|---------
**Regole del traffico di rete**| Impostare i protocolli e gli intervalli di porte e indirizzi locali e remoti che verranno abilitati per la connessione VPN. Se non si crea una regola del traffico di rete, verranno abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo aver creato una regola, solo i protocolli, le porte e gli intervalli di indirizzi specificati in tale regola o nelle regole aggiuntive verranno usati dalla connessione VPN.
**Route**|Specifica le route che verranno usate dalla connessione VPN.
**Server DNS**| Specifica i server DNS che vengono usati dalla connessione VPN una volta stabilita la connessione.         
**App associate**     | È possibile fornire un elenco di app che useranno automaticamente la connessione VPN. Il tipo di app determinerà l'identificatore dell'app. Per le app universali specificare il nome della famiglia di pacchetti e per le app desktop specificare il percorso dell'app.          


> [!IMPORTANT] È consigliabile proteggere tutti gli elenchi delle app compilate da usare per la configurazione della VPN per app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco della VPN per app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

Di seguito è riportato un esempio di quando è possibile usare le impostazioni dei limiti aziendali. Se si vuole abilitare la connessione VPN solo per il desktop remoto, si creerà una regola del traffico di rete che consente il traffico per il numero di protocollo 27 sulla porta esterna 3996. Nessun altro tipo di traffico userà la connessione VPN.

Definire le route nei limiti aziendali è utile quando il tipo di connessione VPN non consente di definire il modo in cui viene gestito il traffico nello split tunneling. In tal caso, usare **Route** per elencare le route che useranno la connessione VPN.

È possibile limitare l'uso della connessione VPN dei dispositivi Windows 10 a specifiche app creando un'impostazione URI OMA personalizzata.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi scegliere **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**, selezionare uno o più gruppi a cui si vuole distribuire il criterio, quindi scegliere **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuirlo**, scegliere **Annulla**.


Al termine della distribuzione, il nome della connessione VPN specificato verrà visualizzato nell'elenco delle connessioni VPN nel dispositivo.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.

### Vedere anche
[Custom configurations for VPN profiles (Configurazioni personalizzate per i profili VPN)](Custom-configurations-for-VPN-profiles.md)
[Per-app VPN for Android Pulse Secure (VPN per app per Pulse Secure per Android)](per-app-vpn-for-android-pulse-secure.md)


<!--HONumber=May16_HO5-->


