---
title: Aggiungere impostazioni VPN per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione VPN usando le impostazioni di configurazione della rete privata virtuale (VPN), inclusi i dettagli della connessione, i metodi di autenticazione e lo split tunneling nelle impostazioni di base; le impostazioni VPN personalizzate con l'identificatore e le coppie chiave-valore; le impostazioni VPN per app che includono gli URL Safari e VPN su richiesta con SSID o domini di ricerca DNS; le impostazioni del proxy per includere uno script di configurazione, un indirizzo IP o FQDN e una porta TCP nei dispositivi che eseguono iOS in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b794ec40d05358ddd1aa3179c2f4060b2cd6fe1d
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236510"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune

Microsoft Intune include molte impostazioni VPN che possono essere distribuite ai dispositivi iOS. Queste impostazioni vengono usate per creare e configurare le connessioni VPN nella rete dell'organizzazione. Questo articolo descrive queste impostazioni. Alcune impostazioni sono disponibili solo per alcuni client VPN, ad esempio Citrix, Zscaler e altri.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

Le impostazioni visualizzate nell'elenco seguente sono determinate dal tipo di connessione VPN scelto.  

- **Nome connessione**: questo nome viene visualizzato dagli utenti finali quando cercano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Nome dominio personalizzato** (solo Zscaler): precompilare il campo di accesso dell'app Zscaler con il dominio a cui appartengono i propri utenti. Ad esempio, se un nome utente è `Joe@contoso.net`, il dominio `contoso.net` viene visualizzato nel campo in modo statico quando si apre l'app. Se non si specifica un nome di dominio, verrà usata la parte del dominio del nome dell'entità utente in Azure Active Directory.
- **Indirizzo IP o FQDN**: indirizzo IP o nome di dominio completo (FQDN) del server VPN a cui si connettono i dispositivi. Ad esempio, immettere `192.168.1.1` o `vpn.contoso.com`.
- **Nome cloud organizzazione** (solo Zscaler): specificare il nome del cloud in cui viene eseguito il provisioning dell'organizzazione. Il nome è presente nell'URL usato per accedere a Zscaler.  
- **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. 
  - **Certificati**: in **Certificato di autenticazione** selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. In [Configurare i certificati](certificates-configure.md) sono disponibili alcune indicazioni sui profili di certificato.
  - **Nome utente e password**: gli utenti finali devono immettere un nome utente e una password per accedere al server VPN.  

    > [!NOTE]
    > Se nome utente e password vengono usati come metodo di autenticazione per la VPN IPSec Cisco, devono fornire SharedSecret tramite un profilo personalizzato di Apple Configurator.
  
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **Cisco Legacy AnyConnect**: applicabile all'app [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 4.0.5x e versioni precedenti.
  - **Cisco AnyConnect**: applicabile all'app [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 4.0.7x e versioni successive.
  - **SonicWall Mobile Connect**
  - **F5 Access Legacy**: applicabile all'app F5 Access 2.1 e versioni precedenti.
  - **F5 Access**: applicabile all'app F5 Access 3.0 e versioni successive.
  - **Palo Alto Networks GlobalProtect (Legacy)**: applicabile all'app Palo Alto Networks GlobalProtect 4.1 e versioni precedenti.
  - **Palo Alto Networks GlobalProtect**: applicabile all'app Palo Alto Networks GlobalProtect 5.0 e versioni successive.
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **VPN Citrix**
  - **Citrix SSO**
  - **Zscaler**: richiede l'integrazione di Zscaler Private Access (ZPA) con il proprio account Azure AD. Per informazioni dettagliate, vedere la [documentazione di Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **VPN personalizzata**    

    > [!NOTE]
    > Cisco, Citrix, F5 e Palo Alto hanno annunciato che i client legacy non funzionano in iOS 12. È necessario eseguire la migrazione alle nuove app appena possibile. Per altre informazioni, vedere il [blog del team di supporto di Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **URL esclusi** (solo Zscaler): quando si è connessi alla rete VPN di Zscaler, gli URL elencati sono accessibili dall'esterno del cloud di Zscaler. 

- **Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

- **Abilita il controllo accesso alla rete**: questa impostazione è un segnaposto per i client VPN, ad esempio Citrix, per consentire a un ID dispositivo di essere incluso nel profilo VPN per l'uso con il controllo di accesso alla rete. Quando si sceglie **Accetto**, l'ID dispositivo viene incluso nel profilo VPN. Attualmente non esistono client VPN o soluzioni partner per il controllo di accesso alla rete che supportano questo nuovo ID, pertanto i dispositivi potranno connettersi alla rete VPN indipendentemente dallo stato di conformità. Questo documento verrà aggiornato quando i nostri partner aggiungeranno il supporto per l'ID.

  Informazioni importanti:  

  - Quando questa impostazione è abilitata, la rete VPN viene disconnessa ogni 24 ore.
  - L'ID dispositivo fa parte del profilo, ma non può essere visualizzato in Intune o nel profilo. Questo ID non viene archiviato né condiviso da Microsoft. Una volta supportato dai partner VPN, il client VPN, ad esempio Citrix SSO, può ottenere l'ID ed eseguire query in Intune per confermare che il dispositivo sia registrato e se il profilo VPN sia conforme o non conforme.
  - Per rimuovere questa informazione, creare nuovamente il profilo e non selezionare **Accetto**. Riassegnare quindi il profilo.

## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata** come tipo di connessione, configurare le impostazioni riportate di seguito. Queste impostazioni sono visibili anche per le connessioni Zscaler e Citrix.

- **Identificatore VPN**: identificatore per l'app VPN in uso, specificato dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata dell'organizzazione**: aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere specificati dal provider VPN.

## <a name="automatic-vpn-settings"></a>Impostazioni VPN automatico

- **VPN per app**: abilita la rete VPN per singole app. Consente l'attivazione automatica della connessione VPN all'apertura di alcune app. È anche possibile associare le app a questo profilo VPN. Per altre informazioni, vedere le [istruzioni per configurare la VPN per app per iOS](vpn-setting-configure-per-app.md).
  - **Tipo di provider**: è disponibile solo per Pulse Secure e VPN personalizzata.
  - Quando si usano i profili **VPN per app** iOS con Pulse Secure o una VPN personalizzata, scegliere il tunneling a livello di app (proxy delle app) o il tunneling a livello di pacchetto (tunnel di pacchetti). Impostare il valore **ProviderType** su **app-proxy** per il tunneling di livello app e su **packet-tunnel** per il tunneling di livello pacchetto. Se non si conosce il valore da usare, vedere la documentazione del provider VPN.
  - **URL Safari che attiveranno questa connessione VPN**: aggiungere uno o più URL del sito Web. Quando questi URL vengono visitati con il browser Safari nel dispositivo, viene stabilita automaticamente la connessione alla VPN.

- **VPN su richiesta**: configurare le regole condizionali che controllano l'avvio della connessione VPN. Ad esempio, creare una condizione per cui la connessione VPN viene usata solo quando un dispositivo non è connesso a una rete Wi-Fi aziendale. Oppure, creare una condizione per cui, se un dispositivo non può accedere a un dominio di ricerca DNS specificato, la connessione VPN non viene avviata.

  - **SSID o domini di ricerca DNS**: selezionare se la condizione usa o meno **SSID** della rete wireless o **Domini di ricerca DNS**. Scegliere **Aggiungi** per configurare uno o più SSID o domini di ricerca.
  - **Probe della stringa dell'URL**: facoltativo. Immettere un URL che viene usato dalla regola come test. Se il dispositivo con questo profilo accede a tale URL senza reindirizzamento, la connessione VPN viene avviata. Il dispositivo si connette quindi all'URL di destinazione. L'utente non visualizza il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi che la rete VPN possa connettersi a un sito prima di connettere il dispositivo all'URL di destinazione tramite VPN.
  - **Azione del dominio**: scegliere una delle opzioni seguenti:
    - Connetti se necessario
    - Non connettere mai
  - **Azione**: scegliere una delle opzioni seguenti:
    - Connessione
    - Valuta la connessione
    - Ignora
    - Disconnessione

## <a name="proxy-settings"></a>Impostazioni proxy

Se si usa un proxy, configurare le impostazioni seguenti. Le impostazioni del proxy non sono disponibili per le connessioni VPN Zscaler.  

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.
- **Indirizzo**: immettere l'indirizzo IP del nome host completo del server proxy.
- **Numero di porta**: immettere il numero di porta associato al server proxy.

## <a name="next-step"></a>Passaggio successivo
[Creare profili VPN in Intune](vpn-settings-configure.md)  
