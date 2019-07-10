---
title: Aggiungere impostazioni VPN per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione VPN usando le impostazioni di configurazione della rete privata virtuale (VPN), inclusi i dettagli della connessione, i metodi di autenticazione e lo split tunneling nelle impostazioni di base; le impostazioni VPN personalizzate con l'identificatore e le coppie chiave-valore; le impostazioni VPN per app che includono gli URL Safari e VPN su richiesta con SSID o domini di ricerca DNS; le impostazioni del proxy per includere uno script di configurazione, un indirizzo IP o FQDN e una porta TCP nei dispositivi che eseguono iOS in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1eee827ace5dae92b485a250e6e4e0b9b426fbe6
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713195"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune

Microsoft Intune include molte impostazioni VPN che possono essere distribuite ai dispositivi iOS. Queste impostazioni vengono usate per creare e configurare le connessioni VPN nella rete dell'organizzazione. Questo articolo descrive queste impostazioni. Alcune impostazioni sono disponibili solo per alcuni client VPN, ad esempio Citrix, Zscaler e altri.

## <a name="connection-type"></a>Tipo di connessione

Selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: applicabile all'app [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 4.0.5x e versioni precedenti.
- **Cisco AnyConnect**: applicabile all'app [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 4.0.7x e versioni successive.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: applicabile all'app F5 Access 2.1 e versioni precedenti.
- **F5 Access**: applicabile all'app F5 Access 3.0 e versioni successive.
- **Palo Alto Networks GlobalProtect (Legacy)** : applicabile all'app Palo Alto Networks GlobalProtect 4.1 e versioni precedenti.
- **Palo Alto Networks GlobalProtect**: applicabile all'app Palo Alto Networks GlobalProtect 5.0 e versioni successive.
- **Pulse Secure**
- **Cisco (IPSec)**
- **VPN Citrix**
- **Citrix SSO**
- **Zscaler**: per usare l'accesso condizionale oppure consentire agli utenti di ignorare la schermata di accesso di Zscaler, è necessario integrare Zscaler Private Access (ZPA) con il proprio account Azure AD. Per informazioni dettagliate, vedere la [documentazione di Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **VPN personalizzata**

> [!NOTE]
> Cisco, Citrix, F5 e Palo Alto hanno annunciato che i client legacy non funzionano in iOS 12. È necessario eseguire la migrazione alle nuove app appena possibile. Per altre informazioni, vedere il [blog del team di supporto di Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

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

- **URL esclusi** (solo Zscaler): quando si è connessi alla rete VPN di Zscaler, gli URL elencati sono accessibili dall'esterno del cloud di Zscaler. 

- **Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

- **Identificatore VPN** (VPN personalizzata, Zscaler e Citrix): identificatore per l'app VPN in uso, specificato dal provider VPN.
  - **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata dell'organizzazione**: aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere specificati dal provider VPN.

- **Abilita il controllo accesso alla rete** (Citrix SSO, F5 Access): quando si sceglie **Accetto**, l'ID del dispositivo viene incluso nel profilo VPN. Questo ID può essere usato per l'autenticazione della rete VPN per consentire o impedire l'accesso alla rete.

  **Quando si usa F5 Access**, assicurarsi di:

  - Confermare che si sta usando F5 BIG-IP 13.1.1.5. BIG-IP 14 non è supportata.
  - Integrare BIG-IP con Intune per NAC. Vedere [Overview: Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) della Guida di F5.
  - Abilitare il controllo accesso alla rete nel profilo VPN.

  **Quando si usa Citrix SSO con Gateway**, assicurarsi di:

  - Verificare che sia in uso Citrix Gateway 12.0.59 o versione successiva.
  - Verificare che gli utenti abbiano Citrix SSO 1.1.6 o versione successiva installato nei dispositivi.
  - Integrare Citrix Gateway con Intune per NAC. Vedere la guida alla distribuzione di Citrix [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) (Integrazione di Microsoft Intune/Enterprise Mobility Suite con NetScaler - scenario LDAP+OTP).
  - Abilitare il controllo accesso alla rete nel profilo VPN.

  **Informazioni importanti**:  

  - Quando il controllo accesso alla rete è abilitato, la rete VPN viene disconnessa ogni 24 ore. La VPN può essere riconnessa immediatamente.
  - L'ID del dispositivo fa parte del profilo, ma non viene visualizzato in Intune. Questo ID non viene archiviato né condiviso da Microsoft.

  Quando l'ID del dispositivo è supportato dai partner VPN, il client VPN, ad esempio Citrix SSO, è in grado di ottenere l'ID. Quindi, può inviare una query a Intune per verificare se il dispositivo è registrato e se il profilo VPN è conforme o meno.

  - Per rimuovere questa informazione, creare nuovamente il profilo e non selezionare **Accetto**. Riassegnare quindi il profilo.

## <a name="automatic-vpn-settings"></a>Impostazioni VPN automatico

- **VPN per app**: abilita la rete VPN per singole app. Consente l'attivazione automatica della connessione VPN all'apertura di alcune app. È anche possibile associare le app a questo profilo VPN. Per altre informazioni, vedere le [istruzioni per configurare la VPN per app per iOS](vpn-setting-configure-per-app.md).
  - **Tipo di provider**: è disponibile solo per Pulse Secure e VPN personalizzata.
  - Quando si usano i profili **VPN per app** iOS con Pulse Secure o una VPN personalizzata, scegliere il tunneling a livello di app (proxy delle app) o il tunneling a livello di pacchetto (tunnel di pacchetti). Impostare il valore **ProviderType** su **app-proxy** per il tunneling di livello app e su **packet-tunnel** per il tunneling di livello pacchetto. Se non si conosce il valore da usare, vedere la documentazione del provider VPN.
  - **URL Safari che attiveranno questa connessione VPN**: aggiungere uno o più URL del sito Web. Quando questi URL vengono visitati con il browser Safari nel dispositivo, viene stabilita automaticamente la connessione alla VPN.

- **VPN su richiesta**: configurare le regole condizionali che controllano l'avvio della connessione VPN. Ad esempio, creare una condizione per cui la connessione VPN viene usata solo quando un dispositivo non è connesso a una rete Wi-Fi aziendale. In alternativa, creare una nuova condizione. Ad esempio, se un dispositivo non può accedere a un dominio di ricerca DNS specificato, la connessione VPN non viene avviata.

  - **SSID o domini di ricerca DNS**: selezionare se la condizione usa o meno **SSID** della rete wireless o **Domini di ricerca DNS**. Scegliere **Aggiungi** per configurare uno o più SSID o domini di ricerca.
  - **Probe della stringa dell'URL**: facoltativo. Immettere un URL che viene usato dalla regola come test. Se il dispositivo con questo profilo accede a tale URL senza reindirizzamento, la connessione VPN viene avviata. Il dispositivo si connette quindi all'URL di destinazione. L'utente non visualizza il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi che la rete VPN possa connettersi a un sito prima di connettere il dispositivo all'URL di destinazione tramite VPN.
  - **Azione del dominio**: scegliere una delle opzioni seguenti:
    - Connetti se necessario
    - Non connettere mai
  - **Azione**: scegliere una delle opzioni seguenti:
    - Connessione
    - Valuta la connessione
    - Ignora
    - Disconnetti

## <a name="proxy-settings"></a>Impostazioni proxy

Se si usa un proxy, configurare le impostazioni seguenti. Le impostazioni del proxy non sono disponibili per le connessioni VPN Zscaler.  

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.
- **Indirizzo**: immettere l'indirizzo IP del nome host completo del server proxy.
- **Numero di porta**: immettere il numero di porta associato al server proxy.

## <a name="next-step"></a>Passaggio successivo
[Creare profili VPN in Intune](vpn-settings-configure.md)  
