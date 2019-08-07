---
title: Aggiungere Endpoint Protection su macOS in Microsoft Intune - Azure | Documenti Microsoft
description: Nei dispositivi macOS utilizzare il gatekeeper per determinare dove è possibile installare le app, incluso il Mac App Store. Inoltre, abilitare o configurare un firewall per autorizzare app specifiche, bloccare app specifiche, utilizzare la modalità mascheramento e persino bloccare determinati tipi di connessioni in ingresso con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4aa0c47f0aa099ff469eb31b212f387836ad69b
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2019
ms.locfileid: "68756517"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Impostazioni di Endpoint Protection per macOS in Intune  

Questo articolo illustra le impostazioni di Endpoint Protection configurabili per i dispositivi che eseguono macOS. Queste impostazioni vengono configurate usando un profilo di configurazione del dispositivo macOS per [Endpoint Protection](endpoint-protection-configure.md) in Intune.  

## <a name="gatekeeper"></a>Gatekeeper  

- **Consenti le app scaricate da queste posizioni**  
  Limitare le app che possono essere avviate da un dispositivo, a seconda della posizione in cui sono state scaricate le app. L'obiettivo è proteggere i dispositivi da malware e consentire solo le app da origini attendibili.  

  - **Non configurato**  
  - **Mac App Store**  
  - **Mac App Store e sviluppatori identificati**  
  - **Ovunque**  

  **Impostazione predefinita**: Non configurato  

- **L'utente può eseguire l'override di Gatekeeper**  
  Impedisce agli utenti di eseguire l'override dell'impostazione Gatekeeper e usare CTRL+clic per installare un'app. Quando è abilitata, gli utenti possono usare Clic+CTRL per installare qualsiasi app.  
 
  - **Non configurato** : gli utenti possono controllare-fare clic per installare le app.  
  - **Blocca** : impedisce agli utenti di usare il controllo-fare clic per installare le app.  

  **Impostazione predefinita**: Non configurato  

## <a name="firewall"></a>Firewall  

Usare il firewall per controllare le connessioni per ogni singola applicazione, anziché per ogni porta. L'uso delle impostazioni in base alle singole applicazione rende più facile sfruttare i vantaggi di protezione mediante firewall. Contribuisce, inoltre, a impedire che app indesiderate assumano il controllo delle porte di rete aperte per app legittime.  

**Generalee**
- **Firewall**  
  Abilitare il firewall per configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.  
  - **Non configurato**  
  - **Attiva**  

  **Impostazione predefinita**: Non configurato  

- **Connessioni in ingresso**  
  Bloccare tutte le connessioni in ingresso tranne le connessioni necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa opzione blocca anche tutti i servizi di condivisione, ad esempio Condivisione file e Condivisione schermo. Se si utilizzano servizi di condivisione, mantenere questa impostazione come *Non configurato*.  
  - **Non configurato**  
  - **Bloccato**  

  **Impostazione predefinita**: Non configurato  

**Consentire o bloccare le connessioni in ingresso per app specifiche.**  

  - **App consentite**  
    Selezionare le app che sono esplicitamente autorizzate a ricevere connessioni in ingresso.  

  - **App bloccate**  
    Selezionare le app che devono bloccare le connessioni in ingresso.  

  - **Modalità mascheramento**  
    Abilitare questa modalità per impedire che il computer risponde alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate. Le richieste impreviste, ad esempio le richieste ICMP (ping), vengono ignorate.  
    - **Non configurato**  
    - **Attiva**  

    **Impostazione predefinita**: Non configurato  

## <a name="filevault"></a>FileVault  
Per ulteriori informazioni sulle impostazioni di Apple FileVault, vedere [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) nel contenuto Apple Developer. 

- **FileVault**  
  È possibile *abilitare* la crittografia dei dischi completa usando XTS-AES 128 con FileVault nei dispositivi che eseguono MacOS 10,13 e versioni successive.  
  - **Non configurato**  
  - **Attiva**  

  **Impostazione predefinita**: Non configurato  

  - **Tipo di chiave di ripristino**  
    Per i dispositivi vengono create chiavi di ripristino della *chiave personale* . Configurare le impostazioni seguenti per la chiave personale.  

    - **Percorso della chiave di ripristino personale** : specificare un messaggio breve per l'utente che spiega come e dove è possibile recuperare la chiave di ripristino personale. Questo testo viene inserito nel messaggio visualizzato dall'utente nella schermata di accesso quando viene richiesto di immettere la chiave di ripristino personale se una password viene dimenticata.  
      
    - **Rotazione della chiave di ripristino personale** : specificare la frequenza con cui viene ruotata la chiave di ripristino personale per un dispositivo. È possibile selezionare il valore predefinito di **non configurato**o un valore da **1** a **12** mesi.  

  - **Disattiva richiesta alla disconnessione**  
    Impedire all'utente di richiedere l'abilitazione di FileVault al momento della disconnessione.  Quando l'impostazione è abilitata, la richiesta di disconnessione viene disabilitata e all'utente viene richiesto di eseguire l'accesso.  
    - **Non configurato**  
    - **Abilita** -Disabilita la richiesta di disconnessione.

    **Impostazione predefinita**: Non configurato  

     > [!IMPORTANT]  
     > Si è verificato un problema noto quando l'impostazione **Disattiva richiesta alla disconnessione** è impostata su *Abilita*. Quando è impostato su *Abilita*, l'impostazione per il **numero di volte consentito a bypass** deve essere impostata su un valore e non deve essere impostata come *non*configurata. Se impostato su *non configurato*, il profilo ha esito negativo nel dispositivo. In questo scenario il dispositivo segnala che si tratta di un **Riepilogo dello stato del profilo** come **errore** senza ulteriori dettagli.
     > 
     > Quando la **richiesta di disabilitazione alla disconnessione** è impostata su *non configurato*, il **numero di volte consentito per il bypass** non può essere *configurato* o avere un valore.  
     > 
     > Il problema verrà risolto in un aggiornamento futuro. 

  - **Numero di volte in cui è consentito eseguire il bypass**  
  Impostare il numero di volte in cui un utente può ignorare le richieste di abilitazione di FileVault prima che FileVault sia necessario per l'accesso dell'utente.  

    - **Non configurato** : la crittografia del dispositivo è obbligatoria prima che il successivo accesso sia consentito.  
    - da **1** a **10** : consente a un utente di ignorare la richiesta da 1 a 10 volte prima di richiedere la crittografia nel dispositivo.  
    - **Nessun limite, sempre richiesta** . all'utente viene richiesto di abilitare FileVault, ma la crittografia non è mai necessaria.  
 
    **Impostazione predefinita**: Non configurato  


