---
title: Connessioni Wi-Fi | Microsoft Intune
description: Usare i profili Wi-Fi per consentire agli utenti di connettersi alle reti Wi-Fi.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 27ba29f57bba1f3807c4b593ecac8c0af0851962
ms.openlocfilehash: 7b49b7d9b6054f7d153359c1ee1b6cf5875fba32


---

# Configurare i dispositivi per connettersi alle reti Wi-Fi aziendali

Usare i profili Wi-Fi in di Microsoft Intune per distribuire le impostazioni di rete wireless agli utenti e ai dispositivi dell'organizzazione. Quando si distribuisce un profilo Wi-Fi, gli utenti hanno accesso alla rete Wi-Fi aziendale senza doverla configurare.

Si immagini, ad esempio, di installare una nuova rete Wi-Fi denominata **Contoso Wi-Fi** e di voler configurare tutti i dispositivi iOS in modo che si connettano alla rete. Questa è la procedura:

![Riepilogo del processo del profilo Wi-Fi](..\media\wi-fi-process-diagram.png) 

1.   Creare un profilo Wi-Fi che contiene le impostazioni necessarie per connettersi alla rete wireless **Contoso Wi-Fi**.

2.   Distribuire il profilo al gruppo di utenti con dispositivi iOS.

3.   Gli utenti visualizzeranno la nuova rete **Contoso Wi-Fi** nell'elenco delle reti wireless e potranno facilmente connettersi a tale rete.


## Come creare un profilo Wi-Fi

È possibile distribuire i profili Wi-Fi nelle piattaforme seguenti:

-   Android 4.0 e versioni successive

-   Android for Work   

-   iOS 8.0 e versioni successive

-   Mac OS X 10.9 e versioni successive

Per i dispositivi che eseguono Windows 8.1 o Windows 10 Desktop o Mobile, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file. Per informazioni dettagliate, vedere [Esportare o impostare un profilo di configurazione Wi-Fi per i dispositivi Windows](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Selezionare uno dei seguenti tipi di criteri, quindi fare clic su **Crea criterio**:

    -   Profilo Wi-Fi (Android 4 e versioni successive)

    -   Profilo Wi-Fi (Android for Work)

    -   Profilo Wi-Fi (iOS 8.0 e versioni successive)

    -   Profilo Wi-Fi (Mac OS X 10.9 e versioni successive)
    
    
    Non esistono impostazioni consigliate per questo tipo di criteri. È necessario creare un criterio personalizzato.

3.  Specificare un nome e una descrizione per il profilo.

4. Specificare i valori delle **connessioni di rete**.
 - **SSID (Service Set Identifier)**: gli utenti visualizzano il nome di rete, non l'identificatore SSID.
 - **Connetti quando la rete non sta trasmettendo il nome (SSID)**: selezionare questa opzione per consentire ai dispositivi di connettersi alla rete quando non è visibile nell'elenco delle reti (perché è nascosta e non sta trasmettendo il nome).
 
5. Configurare le **Impostazioni di sicurezza** per la piattaforma selezionata. Le impostazioni disponibili dipendono dai tipi di sicurezza selezionati e sono descritte in [Impostazioni di sicurezza](#security-settings).

6. (Solo iOS e MAC OS X) Configurare le **impostazioni proxy**

    |Nome impostazione|Altre informazioni|Usare quando:|
    |----------------|-------------------|-------------|
    |**Impostazioni proxy per questa connessione Wi-Fi**|Scegliere il tipo di impostazioni proxy:<br /><br />-   **Nessuno** (valore predefinito)<br />-   **Manuale**: consente di specificare manualmente l'URL e il numero di porta del server proxy.<br />-   **Automatico**: consente di usare un file di configurazione per configurare il server proxy.|Sempre|
    |**Indirizzo server proxy** e **Numero porta**|Specificare l'URL e il numero di porta del server proxy.|**Impostazioni proxy per questa connessione Wi-Fi** è impostato su **Manuale**.|
    |**URL server proxy**|Specificare l'URL del file contenente le impostazioni del server proxy.|**Impostazioni proxy per questa connessione Wi-Fi** è impostato su **Automatico**.|

7.  Salvare il profilo Wi-Fi

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri**. Per informazioni sulla distribuzione del profilo, vedere **Passaggi successivi**.

## Esportare o impostare un profilo di configurazione Wi-Fi per i dispositivi Windows
 
Per i dispositivi che eseguono Windows 8.1 o Windows 10 Desktop o Mobile, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file. 

### Esportare un profilo Wi-Fi
In Windows è possibile usare l'utilità **netsh wlan** per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. In un computer Windows in cui è già installato il profilo Wi-Fi necessario, attenersi alla procedura seguente.

1.  Creare una cartella locale per i profili Wi-Fi esportati, ad esempio c:\WiFi

2.  Aprire un prompt dei comandi come amministratore.

3.  Eseguire il comando `netsh wlan show profiles` e prendere nota del nome del profilo da esportare.  In questo esempio, il nome del profilo è *WiFiName*.

4.  Eseguire questo comando: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Verrà creato un file di profilo Wi-Fi denominato "Wi-Fi-WiFiName.xml" nella cartella di destinazione.

### Importare un profilo Wi-Fi
Usare **Criteri di importazione Wi-Fi di Windows** per importare un set di impostazioni Wi-Fi che è quindi possibile distribuire ai gruppi di utenti o dispositivi necessari.


1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare un criterio di tipo **Windows** &gt; **Importazione Wi-Fi (Windows 8.1 e versioni successive)**.

    Questo criterio può essere applicato ai dispositivi desktop e mobili con Windows 8.1 e Windows 10.

    È possibile solo creare e distribuire criteri di importazione Wi-Fi di Windows *personalizzati*. Le impostazioni consigliate non sono disponibili.

3.  Specificare i valori generali seguenti in Criteri di importazione Wi-Fi di Windows:

    |Nome impostazione|Altre informazioni|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il profilo Wi-Fi per identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione del profilo Wi-Fi e altre informazioni rilevanti per consentirne l'individuazione.|

4.  Specificare i valori seguenti in **Profilo Wi-Fi personalizzato**:

    |Nome impostazione|Altre informazioni|
    |----------------|--------------------|
    |**File del profilo di configurazione**|Fare clic su **Importa** per selezionare il file XML contenente le impostazioni del profilo Wi-Fi da importare in Intune.|
    |**Nome del profilo di configurazione personalizzato (visualizzato agli utenti)**|Visualizza il nome del profilo di configurazione Wi-Fi come verrà visualizzato dagli utenti sul dispositivo.|
    |**Dettagli del profilo di configurazione**|Visualizza il codice XML per il profilo di configurazione selezionato.|

5.  Al termine, fare clic su **Salva criterio**.

6.  Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## Distribuire il profilo

Un profilo è un tipo di criterio, pertanto per distribuirlo è possibile usare l'area di lavoro Criteri.

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: selezionare uno o più gruppi in cui si vuole distribuire il criterio, quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, fare clic su **Annulla**.


Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.

## Impostazioni di sicurezza
Queste tabelle contengono dettagli per le impostazioni di sicurezza disponibili per i profili Wi-Fi Android, iOS e Mac OS X. 

### Impostazioni di sicurezza per i dispositivi Android

  |Nome impostazione|Altre informazioni|Usare quando:|
|----------------|--------------------|-------------|
|**Tipo di sicurezza**|Selezionare il protocollo di sicurezza per la rete wireless:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Nessuna autenticazione (aperto)** se la rete non è protetta.|Sempre|
|**Tipo EAP**|Scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Viene selezionato il tipo di sicurezza **WPA-Enterprise/WPA2-Enterprise**.|
|**Selezionare i certificati radice per la convalida server**|Fare clic su **Seleziona**, quindi scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. **Importante:** per la creazione del profilo del certificato radice attendibile, vedere [Proteggere l'accesso alle risorse con i profili certificato](secure-resource-access-with-certificate-profiles.md).|Viene selezionato qualsiasi **Tipo EAP** .|
|**Metodo di autenticazione**|Selezionare il metodo di autenticazione per la connessione:<br /><br />-   **Certificati** per specificare il certificato client<br />-   **Nome utente e password** per specificare un metodo diverso per l'autenticazione|**Tipo EAP** è impostato su **PEAP** o **EAP-TTLS**.|
|**Selezionare un metodo non EAP per l'autenticazione (identità interna)**|Selezionare la modalità di autenticazione della connessione:<br /><br />-   **Nessuno**<br />-   **Password Authentication Protocol (PAP)**<br />-   **Challenge Handshake Authentication Protocol (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP versione 2 (MS-CHAP v2)**<br /><br />Le opzioni disponibili dipendono dal tipo EAP selezionato.| **Metodo di autenticazione** è impostato su **Nome utente e password**.|
|**Abilita privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|**Tipo EAP** è impostato su **PEAP** o **EAP-TTLS**.|
|**Selezionare un certificato client per l'autenticazione client (certificato di identità)**|Fare clic su **Seleziona**, quindi scegliere il profilo certificato SCEP usato per autenticare la connessione. **Importante:** per la creazione del profilo certificato SCEP, vedere [Proteggere l'accesso alle risorse con i profili certificato](secure-resource-access-with-certificate-profiles.md).|Il tipo di sicurezza è **WPA-Enterprise/WPA2-Enterprise** e viene selezionato qualsiasi **Tipo EAP**.|

### Impostazioni di sicurezza per i dispositivi iOS e Mac OS X

  |Nome impostazione|Altre informazioni|Usare quando:|
|----------------|--------------------|-------------|
|**Tipo di sicurezza**|Selezionare il protocollo di sicurezza di rete wireless:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Nessuna autenticazione (aperto)** se la rete non è protetta.|Sempre|
|**Tipo EAP**|Scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-FAST**<br />-   **LEAP**<br />-   **EAP-SIM**|Viene selezionato il tipo di sicurezza **WPA-Enterprise/WPA2-Enterprise**.|
|**Nomi di certificati del server attendibili**|Selezionare il profilo del certificato radice attendibile usato per autenticare la connessione. **Importante:** per la creazione del profilo del certificato radice attendibile, vedere [Proteggere l'accesso alle risorse con i profili certificato](secure-resource-access-with-certificate-profiles.md).|Viene selezionato un tipo EAP, ovvero **EAP-TLS**, **PEAP**, **EAP-TTLS** o **EAP-FAST**.|
|**Usa Protected Access Credential (PAC)**|Selezionare questa opzione per usare credenziali di accesso protetto per stabilire un tunnel autenticato tra il client e il server di autenticazione. Se presente, verrà usato un file PAC esistente.|**Tipo EAP** è impostato su **EAP-FAST**.|
|**Esegui provisioning di PAC**|Consente di eseguire il provisioning del file PAC nei dispositivi.<br /><br />Quando viene usata questa opzione, è possibile anche selezionare **Esegui provisioning anonimo di PAC** per garantire che il provisioning del file PAC venga eseguito senza effettuare l'autenticazione del server.|Viene selezionato**Usa Protected Access Credential (PAC)** .|
|**Metodo di autenticazione**|Selezionare il metodo di autenticazione usato per la connessione:<br /><br /><ul><li>**Certificati** per specificare il certificato client</li><li>**Nome utente e password** per specificare uno dei seguenti metodi non EAP per l'autenticazione (noto anche come identità interna):<br /><br /><ul><li>**Nessuno**</li><li>**Password Authentication Protocol (PAP)**</li><li>**Challenge Handshake Authentication Protocol (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP versione 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|**Tipo EAP** è impostato su **PEAP** o **EAP-TTLS**.|
|**Selezionare un certificato client per l'autenticazione client (certificato di identità)**|Selezionare il profilo certificato SCEP usato per autenticare la connessione. **Importante:** per la creazione del profilo certificato SCEP, vedere [Proteggere l'accesso alle risorse con i profili certificato](secure-resource-access-with-certificate-profiles.md).|Il tipo di sicurezza viene impostato su **WPA-Enterprise/WPA2-Enterprise** e **Tipo EAP** viene impostato su **EAP-TLS**, **PEAP** o **EAP-TTLS**.|
|**Abilita privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore.<br /><br />Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|**Tipo EAP** è impostato su **PEAP**, **EAP-TTLS** o **EAP-FAST**.|


### Vedere anche
Per informazioni sulla creazione di un profilo Wi-Fi con una chiave precondivisa, vedere [Pre-shared key Wi-Fi profile (Profilo Wi-Fi con chiave precondivisa)](pre-shared-key-wi-fi-profile.md)



<!--HONumber=Oct16_HO2-->


