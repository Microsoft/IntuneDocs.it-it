---
title: Limitare l'accesso alle reti con Cisco ISE | Microsoft Intune
description: Utilizzare ISE Cisco con Intune in modo che i dispositivi vengano registrati in Intune e siano conformi ai relativi criteri prima di accedere a Wi-Fi e VPN controllati da Cisco ISE.
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 78945498a951e7b897164ae6f33c4e87d521ca5b


---

# Uso di Cisco ISE con Microsoft Intune
L'integrazione di Intune con Cisco ISE consente di creare criteri di rete nell'ambiente ISE usando lo stato di conformità e registrazione dei dispositivi di Intune. Questi criteri possono essere usati per verificare che l'accesso alla rete aziendale sia limitato ai dispositivi gestiti da Intune e conformi ai criteri di Intune. 

## Configurazione

Per abilitare l'integrazione, non è necessario eseguire installazioni nel tenant di Intune. Sarà necessario concedere al server Cisco ISE l'autorizzazione ad accedere al tenant di Intune e, al termine di questa operazione, il resto dell'installazione viene eseguita nel server Cisco ISE. Questo articolo illustra come concedere al server ISE le autorizzazioni necessarie per accedere al tenant di Intune. 

### Passaggio 1: Gestire i certificati
1. Nella console di Azure Active Directory (AAD) esportare il certificato. 

    #### Internet Explorer 11
        
    a. Eseguire Internet Explorer come amministratore e accedere alla console di AAD.
  
    b. Scegliere l'icona del lucchetto nella barra degli indirizzi e quindi **Visualizza certificati**
    
    c. Nella scheda **Dettagli** delle proprietà del certificato scegliere **Copia su file**.

    d. Nella pagina iniziale **dell'Esportazione guidata certificati** fare clic su **Avanti**. 

    e. Nella pagina **Formato di file di esportazione** lasciare l'impostazione predefinita, **Binario codificato DER x.509 (. CER)**, e scegliere **Avanti**.  

    f. Nella pagina **File da esportare** scegliere **Sfoglia** per selezionare un percorso in cui salvare il file e specificare un nome di file. Anche se apparentemente si sta selezionando un file da esportare, in realtà si assegna un nome al file in cui verrà salvato il certificato esportato. Scegliere **Avanti** &gt; **Fine**.

    #### Safari
    
    a. Accedere alla console di AAD.

    b. Scegliere l'icona del blocco &gt;  **Ulteriori informazioni**.
    
    c. Scegliere **Visualizza certificato** &gt; **Dettagli**.

    d. Scegliere il certificato, quindi **Esporta**.  


> [!IMPORTANT]
> Controllare la data di scadenza del certificato, poiché sarà necessario esportare e importare un nuovo certificato quando questo scade.

    

2. Dall'interno della console ISE importare il certificato di Intune, ovvero il file esportato, nell'archivio dei **certificati attendibili**.
3. Nella console ISE passare a **Amministrazione** > **Certificati** > **Certificati di sistema**.
4. Selezionare il certificato ISE, quindi scegliere **Esporta**.
5. Modificare il certificato esportato in un editor di testo:
 - Eliminare ** -----BEGIN CERTIFICATE-----**
 - Eliminare ** -----END CERTIFICATE-----**
 - Verificare che tutto il testo sia una singola riga

### Passaggio 2: Creare un'app per ISE nel tenant di AAD
1. Nella console di Azure Active Directory (AAD) scegliere **Applicazioni** > **Aggiungi applicazione** > **Aggiungi un'applicazione che l'organizzazione sta sviluppando**.
2. Specificare un nome e un URL per l'app. L'URL può essere il sito Web aziendale.
3. Scaricare il manifesto dell'app (file JSON).
4. Modificare il file JSON del manifesto. Nell'impostazione **keyCredentials** indicare il testo del certificato modificato del passaggio 1 come valore dell'impostazione.
5. Salvare il file senza modificarne il nome.
6. Specificare per l'app le autorizzazioni per l'API Microsoft Graph e Microsoft Intune.
    1. Per Microsoft Graph, scegliere gli elementi seguenti
        - **Autorizzazioni per l'applicazione**: Lettura dati directory
        - **Autorizzazioni delegate**: 
            - Accedi ai dati di un altro utente in qualsiasi momento
          - Effettua l'accesso utente
   2. Per l'API Microsoft Intune, in **Autorizzazioni applicazione** scegliere **Get device state and compliance from Intune** (Ottieni stato del dispositivo e conformità da Intune).

7. Scegliere **Visualizza endpoint** e copiare i valori seguenti per l'uso nella configurazione delle impostazioni ISE:

|Valore nel portale di Azure Active Directory|Campo corrispondente nel portale ISE|
|-------------------|---------------------------------|
|Endpoint API di Microsoft Azure AD Graph|URL individuazione automatica|
|Endpoint del token OAuth 2.0|URL emittente di token|
|Aggiornare il codice con l'ID client|ID client|


### Passaggio 3: Configurare le impostazioni ISE 
2. Nella console di amministrazione ISE indicare questi valori: 
  - **Tipo di server**: Mobile Device Manager
  - **Tipo di autenticazione**: OAuth, credenziali del client
  - **Individuazione automatica**: sì
  - **URL individuazione automatica**: immettere il valore del passaggio 1
  - **ID client**: immettere il valore del passaggio 1
  - **URL emittente di token**: immettere il valore del passaggio 1



## Informazioni condivise tra il tenant di Intune e il server Cisco ISE
Questa tabella elenca le informazioni condivise tra il tenant di Intune e il server Cisco ISE per i dispositivi gestiti da Intune.

|Proprietà|  Descrizione|
|---------------|------------------------------------------------------------|
|complianceState|   True o False (stringa) che indica se il dispositivo è conforme o non conforme.|
|IsManaged| True o False che indica se il client è gestito o meno da Intune.|
|macAddress|Indirizzo Mac del dispositivo.|
|serialNumber|Numero di serie del dispositivo. Si applica solo ai dispositivi iOS.|
|imei|Il numero IMEI (15 cifre decimali: 14 cifre più un numero di controllo) o IMEISV (16 cifre) include informazioni su origine, modello e numero di serie del dispositivo. La struttura del numero IMEI/SV è specificata in 3GPP TS 23.003. Si applica solo ai dispositivi con schede SIM.|
|udid|Identificatore univoco del dispositivo, una sequenza di 40 lettere e numeri specifica per dispositivi iOS.|
|meid|Identificativo di apparecchiatura mobile, un numero univoco globale che identifica un componente fisico della stazione mobile CDMA. Il formato del numero è definito dal report 3GPP2 S. R0048 ma in pratica può essere considerato un IMEI con cifre esadecimali. Un MEID ha una lunghezza di 56 bit (14 cifre esadecimali). È costituito da tre campi, inclusi un codice regionale (RR) di 8 bit, un codice di produttore di 24 bit e un numero di serie di 24 bit assegnato dal produttore.| 
|osVersion| Versione del sistema operativo del dispositivo.
|modello|Modello del dispositivo.
|manufacturer|Produttore del dispositivo.
|azureDeviceId| L'ID del dispositivo dopo l'aggiunta dell'area di lavoro in Azure Active Directory. Sarà un guid vuoto per i dispositivi non aggiunti.|
|lastContactTimeUtc|Data e ora in cui il dispositivo ha eseguito l'ultima archiviazione con il servizio di gestione di Intune. 


## Esperienza utente

Quando un utente tenta di accedere alle risorse usando un dispositivo non registrato, riceve una richiesta simile a quella riportata di seguito:

![Esempio di richiesta di registrazione](../media/cisco-ise-user-iphone.png)

Quando l'utente sceglie di eseguire la registrazione, viene reindirizzato al processo di registrazione di Intune. L'esperienza di registrazione in Intune è illustrata negli argomenti seguenti:

- [Registrare il dispositivo Android in Intune](/intune/end-user/enroll-your-device-in-Intune-android)</br>
- [Registrare il dispositivo iOS in Intune](/intune/end-user/enroll-your-device-in-intune-ios)</br>
- [Registrare il dispositivo Mac OS X in Intune](/intune/end-user/enroll-your-device-in-intune-mac-os-x)</br>
- [Registrare il dispositivo Windows in Intune](/intune/end-user/enroll-your-device-in-intune-windows)</br> 

È anche disponibile un [set scaricabile di istruzioni per la registrazione](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) che consente di creare indicazioni personalizzate per l'esperienza utente.


### Vedere anche

[Cisco Identity Services Engine Administrator Guide, Release 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)




<!--HONumber=Jun16_HO4-->


