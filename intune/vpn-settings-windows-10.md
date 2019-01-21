---
title: Impostazioni VPN di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su tutte le impostazioni VPN disponibili in Microsoft Intune, sulla loro funzione e sulle operazioni eseguite, incluse le regole di traffico, l'accesso condizionale e le impostazioni DNS e proxy per i dispositivi Windows 10 e i dispositivi Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 9c41fc39b5d2dc644fae91d6b02171681453ab1c
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203400"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Impostazioni dei dispositivi Windows 10 e Windows Holographic per l'aggiunta di connessioni VPN con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile aggiungere e configurare connessioni VPN per i dispositivi tramite Microsoft Intune. Questo articolo illustra le impostazioni e le funzionalità comunemente usate per creare reti private virtuali (VPN). Queste impostazioni e funzionalità VPN vengono usate nei profili di configurazione del dispositivo di Intune di cui viene eseguito il push o la distribuzione nei dispositivi. 

Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, tra cui l'uso di un fornitore VPN, l'abilitazione della funzione Sempre online, l'uso del DNS, l'aggiunta di un proxy e altre ancora.

Queste impostazioni si applicano ai dispositivi che eseguono:

- Windows 10
- Windows Holographic for Business

A seconda delle impostazioni selezionate, è possibile che non tutti i valori siano configurabili.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo VPN](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi. Quando si aggiunge un server, si immettono le informazioni seguenti:
  - **Descrizione**: immettere un nome descrittivo per il server, ad esempio **Server VPN Contoso**
  - **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi, ad esempio **192.168.1.1** o **vpn.contoso.com**
  - **Server predefinito**: abilita il server come server predefinito usato dai dispositivi per stabilire la connessione. Impostare un solo server come server predefinito.
  - **Importa**: selezionare un file che include un elenco di server separati da virgole nel formato: descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i server nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file con valori delimitati da virgole (CSV).

- **Registrazione di indirizzi IP con DNS interno**: selezionare **Abilita** per configurare il profilo VPN di Windows 10 in modo da registrare dinamicamente gli indirizzi IP assegnati all'interfaccia VPN con il DNS interno. Selezionare **Disabilita** per non registrare in modo dinamico gli indirizzi IP.

- **Tipo di connessione**: Selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatico**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Quando si sceglie un tipo di connessione VPN, potrebbe essere richieste anche le impostazioni seguenti:  
    - **Sempre online**: scegliere **Abilita** per connettersi automaticamente alla connessione VPN quando si verificano gli eventi seguenti: 
      - Gli utenti accedono ai propri dispositivi
      - La rete del dispositivo cambia
      - Lo schermo del dispositivo si riattiva dopo essere stato disattivato 

    - **Metodo di autenticazione**: specificare come si vuole eseguire l'autenticazione degli utenti nel server VPN. L'uso dei **certificati** offre funzionalità avanzate, ad esempio un'esperienza completamente automatica, VPN su richiesta e VPN per singole app.
    - **Ricorda le credenziali a ogni accesso**: memorizza nella cache le credenziali di autenticazione.
    - **XML personalizzato**: immettere i comandi XML personalizzati per la configurazione della connessione VPN.
    - **XML EAP**: immettere i comandi XML EAP per la configurazione della connessione VPN

#### <a name="pulse-secure-example"></a>Esempio di Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Esempio di F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Esempio di SonicWALL Mobile Connect
**Gruppo o dominio di accesso**: questa proprietà non può essere impostata nel profilo VPN. Mobile Connect analizza questo valore quando nome utente e dominio vengono immessi nel formato `username@domain` o `DOMAIN\username`.

Esempio:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Esempio di VPN CheckPoint Mobile

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Scrittura di XML personalizzato
Per altre informazioni su come scrivere comandi XML personalizzati, vedere la documentazione della VPN fornita dai diversi produttori.

Per altre informazioni sulla creazione di XML EAP personalizzato, vedere [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration) (Configurazione EAP).

## <a name="apps-and-traffic-rules"></a>App e regole del traffico

- **Associa WIP o app a questa VPN**: abilitare questa opzione se si vuole che la connessione VPN venga usata solo da alcune app. Le opzioni disponibili sono:

  - **Associa WIP a questa connessione**: immettere un **dominio WIP per la connessione**
  - **Associa le app a questa connessione**: selezionare **Limita la connessione VPN a queste app** e quindi aggiungere le **app associate**. Le app immesse usano automaticamente la connessione VPN. Il tipo di app determina l'identificatore dell'app. Per un'app universale, immettere il nome della famiglia di pacchetti. Per un'app desktop, immettere il percorso del file dell'app.
  >[!IMPORTANT]
  >È consigliabile proteggere tutti gli elenchi di app creati per le reti VPN per singole app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco delle app della VPN per singole app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

- **Regole del traffico di rete per questa connessione VPN**: selezionare i protocolli, oltre alle porte e agli intervalli di indirizzi locali e remoti, abilitati per la connessione VPN. Se non si crea una regola di traffico di rete, vengono abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo la creazione di una regola, la connessione VPN usa soltanto i protocolli, le porte e gli intervalli di indirizzi immessi nella regola.

## <a name="conditional-access"></a>Accesso condizionale

- **Accesso condizionale per questa connessione VPN**: abilita il flusso di conformità dei dispositivi dal client. Se questa impostazione è abilitata, il client VPN comunica con Azure Active Directory (AD) per ottenere un certificato da usare per l'autenticazione. La rete VPN deve essere impostata per usare l'autenticazione basata su certificato e il server VPN deve considerare attendibile il server restituito da Azure AD.

- **Accesso Single Sign-On (SSO) con il certificato alternativo**: per la conformità del dispositivo, usare un certificato diverso dal certificato di autenticazione VPN per l'autenticazione Kerberos. Immettere il certificato con le impostazioni seguenti:

  - **Nome**: nome per l'utilizzo chiavi avanzato (EKU)
  - **Identificatore oggetto**: ID oggetto per EKU
  - **Hash dell'emittente**: identificazione personale per il certificato SSO

## <a name="dns-settings"></a>Impostazioni DNS

- **Elenco di ricerca dei suffissi DNS**: in **Suffissi DNS** immettere un suffisso DNS e fare clic su **Aggiungi**. È possibile aggiungere più suffissi.

  Quando si usano i suffissi DNS, è possibile cercare una risorsa di rete usando il relativo nome breve anziché il nome di dominio completo (FQDN). Quando si esegue la ricerca usando il nome breve, il suffisso viene determinato automaticamente dal server DNS. Ad esempio, `utah.contoso.com` è nell'elenco di suffissi DNS. Si effettua il ping di `DEV-comp`. In questo scenario viene risolto in `DEV-comp.utah.contoso.com`.

  I suffissi DNS vengono risolti nell'ordine indicato e l'ordine può essere modificato. Ad esempio, `colorado.contoso.com` e `utah.contoso.com` sono nell'elenco di suffissi DNS ed entrambi hanno una risorsa denominata `DEV-comp`. Poiché `colorado.contoso.com` è elencato per primo, viene risolto come `DEV-comp.colorado.contoso.com`.
  
  Per modificare l'ordine, fare clic sui puntini a sinistra del suffisso DNS e quindi trascinare il suffisso nella parte superiore:

  ![Selezionare i tre puntini e fare clic e trascinare per spostare il suffisso DNS](./media/vpn-settings-windows10-move-dns-suffix.png)

- **Regole della tabella dei criteri di risoluzione dei nomi**: le regole della tabella dei criteri di risoluzione dei nomi definiscono il modo in cui DNS risolve i nomi quando è connesso alla VPN. Dopo che è stata stabilita la connessione VPN, scegliere i server DNS usati dalla connessione.

  È possibile aggiungere alla tabella regole che includono il dominio, il server DNS, il proxy e altri dettagli per la risoluzione del dominio immesso. La connessione VPN usa queste regole quando gli utenti si connettono ai domini immessi.

  Selezionare **Aggiungi** per aggiungere una nuova regola. Per ogni server, immettere:

  - **Dominio**: immettere il nome di dominio completo (FQDN) o un suffisso DNS per applicare la regola. È anche possibile immettere un punto (.) all'inizio per un suffisso DNS. Ad esempio, immettere `contoso.com` o `.allcontososubdomains.com`.
  - **Server DNS**: immettere l'indirizzo IP o il server DNS che risolve il dominio. Ad esempio, immettere `10.0.0.3` o `vpn.contoso.com`.
  - **Proxy**: immettere il server proxy Web che risolve il dominio. Immettere ad esempio `http://proxy.com`.
  - **Connetti automaticamente**: con l'impostazione **Abilitata**, il dispositivo si connette automaticamente alla rete VPN quando un dispositivo si connette a un dominio immesso, ad esempio `contoso.com`. con l'impostazione **Non configurata** (predefinita), il dispositivo non si connette automaticamente alla VPN.
  - **Persistente**: con l'impostazione **Abilitata**, la regola rimane nella tabella dei criteri di risoluzione dei nomi finché non viene rimossa manualmente dal dispositivo, anche dopo la disconnessione della VPN. Con l'impostazione **Non configurata** (predefinita), le regole NRPT nel profilo VPN vengono rimosse dal dispositivo quando la VPN si disconnette.

## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per configurare il server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, che include il file di configurazione.
- **Indirizzo**: immettere l'indirizzo del server proxy, ad esempio un indirizzo IP o `vpn.contoso.com`
- **Numero porta**: immettere il numero della porta TCP usato dal server proxy
- **Ignora proxy per indirizzi locali**: se non si vuole usare un server proxy per gli indirizzi locali, scegliere Abilita. Questa impostazione si applica se il server VPN richiede un server proxy per la connessione.

## <a name="split-tunneling"></a>Split tunneling

- **Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.
- **Route di split tunneling per questa connessione VPN**: consente di aggiungere route facoltative per provider VPN di terze parti. Immettere un prefisso di destinazione e una dimensione per ogni connessione.

## <a name="trusted-network-detection"></a>Rilevamento della rete attendibile

**Suffissi DNS delle reti attendibili**: quando gli utenti sono già connessi a una rete attendibile, è possibile impedire ai dispositivi di connettersi automaticamente ad altre connessioni VPN.

In **Suffissi DNS** immettere un suffisso DNS che si vuole considerare attendibile, come contoso.com, e scegliere **Aggiungi**. È possibile aggiungere un numero illimitato di suffissi.

Se un utente è connesso a un suffisso DNS nell'elenco, non verrà connesso automaticamente a un'altra connessione VPN. L'utente continua a usare l'elenco attendibile di suffissi DNS immesso. La rete attendibile viene ancora usata, anche se sono impostate eventuali attivazioni automatiche.

Ad esempio, se l'utente è già connesso a un suffisso DNS attendibile, le attivazioni automatiche vengono ignorate. Nello specifico, i suffissi DNS nell'elenco annullano tutte le altre attivazioni automatiche di connessione, tra cui:

- Sempre online
- Trigger basato su app
- Attivazione automatica del DNS

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni VPN nei dispositivi [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md) e [macOS](vpn-settings-macos.md).
