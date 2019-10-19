---
title: Codici di errore e di stato in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di errori, codici di stato, descrizioni e soluzioni quando si usano dispositivi gestiti MDM, ottenere l'accesso a risorse aziendali, errori nei dispositivi iOS ed errori di risposta OMA in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17a8ebfcad2bcf485771f26184377aeb2c4bf4e1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509798"
---
# <a name="common-error-codes-and-descriptions-in-microsoft-intune"></a>Codici di errore comuni e descrizioni in Microsoft Intune

In questo articolo sono elencati gli errori più comuni, i codici di stato, le descrizioni e le soluzioni possibili durante l'accesso alle risorse dell'organizzazione. Usare queste informazioni per facilitare la risoluzione dei problemi di accesso quando si usa Microsoft Intune.

Se è necessaria assistenza, vedere [Come ottenere supporto per Microsoft Intune](../get-support.md).

## <a name="status-codes-for-mdm-managed-windows-devices"></a>Codici di stato per dispositivi Windows gestiti da MDM

|Codice di stato|Messaggio di errore|Operazioni da eseguire|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Installazione in corso||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|In attesa del contenuto||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|Recupero del contenuto|Causa probabile: Lo stato del processo 30 indica che il download utente di un'app non è riuscito.<br /><br />Le cause probabili potrebbero essere:<br /><br />Il dispositivo ha perso la connettività Internet mentre il download era in corso.<br /><br />Il certificato emesso per il dispositivo al momento della registrazione potrebbe essere scaduto.<br /><br />Attenuazione:<br /><br />Avviare le applicazioni aziendali dal Pannello di controllo sul dispositivo per verificare che il certificato del dispositivo non sia scaduto. Se scaduto, sarà necessario registrare nuovamente il dispositivo.<br /><br />Verificare che il dispositivo sia connesso a Internet e provare a richiedere nuovamente l'applicazione.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Download del contenuto completato||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Installazione in corso||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Si è verificato un errore di installazione|L'installazione dell'app non è riuscita dopo il download.<br /><br />Il certificato di firma del codice con cui è stata firmata l'app non è presente nel dispositivo.<br /><br />Una dipendenza del framework da cui dipende l'applicazione non è stata trovata nel dispositivo.<br /><br />Assicurarsi che il certificato di firma del codice con cui è stata firmata l'applicazione sia presente nel dispositivo e verificare con l'amministratore che tale certificato sia destinato a tutti i dispositivi Windows RT registrati nell'organizzazione.<br /><br />Nel caso in cui l'errore di installazione sia dovuto a una dipendenza del framework mancante, l'amministratore dovrà pubblicare nuovamente l'applicazione assemblando il framework insieme al pacchetto dell'applicazione.<br /><br />Il pacchetto dell'applicazione scaricato non è un pacchetto valido, potrebbe essere danneggiato o potrebbe non essere compatibile con la versione del sistema operativo del dispositivo.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Installazione riuscita||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Disinstallazione in corso||
|90 (APP_CI_ENFORCEMENT_ERROR)|Si è verificato un errore di disinstallazione||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Disinstallazione completata||
|110 (APP_CI_ENFORCEMENT_ERROR)|Mancata corrispondenza hash del contenuto||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK / chiave di trasferimento locale non abilitata||
|130 (APP_CI_ENFORCEMENT_ERROR)|Installazione della licenza MSADP non riuscita||
|Nessuno stato (APP_CI_ENFORCEMENT_UNKNOWN)|n/d|Lo stato è attualmente sconosciuto.|

## <a name="company-resource-access-common-errors"></a>Accesso alle risorse aziendali (errori comuni)

|Codice di stato|Codice di errore esadecimale|Messaggio di errore|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|Richiesta CRP MDM non trovata|
|-2016281102|0x87D1FDF2|URL NDES non trovato|
|-2016281103|0x87D1FDF1|Informazioni sul certificato CRP MDM non trovate|
|-2016281104|0x87D1FDF0|Informazioni sul certificato CI MDM non trovate|
|-2016281105|0x87D1FDEF|Valutazione della regola non riuscita|
|-2016281106|0x87D1FDEE|Non applicabile perché persa durante la risoluzione dei conflitti|
|-2016281107|0x87D1FDED|Origine di individuazione impostazione non supportata|
|-2016281108|0x87D1FDEC|Impostazione di riferimento non trovata in CI|
|-2016281109|0x87D1FDEB|Conversione tipo di dati non riuscita|
|-2016281110|0x87D1FDEA|Parametro non valido per impostazione CIM|
|-2016281111|0x87D1FDE9|Non applicabile per questo dispositivo|
|-2016281112|0x87D1FDE8|Correzione non riuscita|
|-2016330905|0x87D13B67|Stato app sconosciuto|
|-2016330906|0x87D13B66|L'app è gestita, ma è stata rimossa dall'utente|
|-2016330907|0x87D13B65|Il dispositivo sta riscattando il codice di riscatto|
|-2016330908|0x87D13B64|Installazione app non riuscita|
|-2016330909|0x87D13B63|L'utente ha rifiutato l'offerta di aggiornamento dell'app|
|-2016330910|0x87D13B62|L'utente ha rifiutato l'offerta di installazione dell'app|
|-2016330911|0x87D13B61|L'utente ha installato l'app prima dell'installazione dell'app gestita|
|-2016330912|0x87D13B60|L'app viene pianificata per l'installazione, ma è necessario un codice di riscatto per completare la transazione|
|-2016341109|0x87D1138B|Il dispositivo iOS ha riscontrato un errore|
|-2016341110|0x87D1138A|Il dispositivo iOS ha rifiutato il comando a causa del formato non corretto|
|-2016341111|0x87D11389|Il dispositivo iOS ha restituito uno stato Inattivo imprevisto|
|-2016341112|0x87D11388|Il dispositivo iOS è attualmente occupato|

## <a name="errors-returned-by-ios-devices"></a>Errori restituiti da dispositivi iOS

### <a name="company-portal-errors"></a>Errori nel Portale aziendale

|Testo dell'errore nel Portale aziendale|Codice di stato HTTP|Altre informazioni sull'errore|
|---|---|---|
|__Problema interno del server__ <br>Non è stato possibile contattarci a causa di un problema interno del server. Riprovare e quindi contattare l'amministratore IT se il problema persiste.|Errore 500|Questo errore è probabilmente causato da un problema nel servizio Intune. Il problema deve essere risolto sul lato del servizio Intune ed è probabile che non sia causato da problemi sul lato del cliente.|
|__Temporaneamente non disponibile__ <br>Non è stato possibile contattarci perché il servizio non è temporaneamente disponibile. Riprovare e quindi contattare l'amministratore IT se il problema persiste.|Errore 503|L'errore è probabilmente causato da un problema temporaneo del servizio Intune, ad esempio se è in corso la manutenzione del servizio. Il problema deve essere risolto sul lato del servizio Intune ed è probabile che non sia causato da problemi sul lato del cliente.|
|__Non è possibile connettersi al server__ <br>Non è stato possibile contattarci. Riprovare e quindi contattare l'amministratore IT se il problema persiste.|Non associato a un codice di stato HTTP|Non è stato possibile stabilire una connessione protetta al server, probabilmente a causa di un problema SSL con i certificati in uso. Questo problema potrebbe dipendere da configurazioni del cliente non conformi ai requisiti di Apple per ATS (App Transport Security).|
|__Si è verificato un errore__ <br>Non è stato possibile caricare il client del portale aziendale. Riprovare e quindi contattare l'amministratore IT se il problema persiste.|Errore 400|Qualsiasi errore con codice di stato HTTP nel gruppo 400 che non ha un messaggio di errore più specifico visualizzerà questo messaggio. Si tratta di un errore sul lato del client che si verifica nell'app Portale aziendale per iOS.|
|__Non è stato possibile raggiungere il server__ <br>Non è stato possibile contattarci. Riprovare e quindi contattare l'amministratore IT se il problema persiste.|Errore 500|Qualsiasi errore con codice di stato HTTP nel gruppo 500 che non ha un messaggio di errore più specifico visualizzerà questo messaggio. Si tratta di un errore sul lato del servizio che si verifica nel servizio Intune.|

### <a name="service-errors"></a>Errori del servizio

|Codice di stato|Codice di errore esadecimale|Messaggio di errore|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Errore interno|
|-2016299112|0x87D1B798|Errore interno|
|-2016300111|0x87D1B3B1|36001: (errore interno)|
|-2016300112|0x87D1B3B0|36000: Cellulare già configurato|
|-2016301110|0x87D1AFCA|35002: Più tipi di carattere in un payload singolo|
|-2016301111|0x87D1AFC9|35001: Installazione del tipo di carattere non riuscita|
|-2016301112|0x87D1AFC8|35000: Dati del tipo di carattere non validi|
|-2016302109|0x87D1ABE3|34003: Nome entità Kerberos non valido|
|-2016302110|0x87D1ABE2|34002: Nome entità Kerberos mancante|
|-2016302111|0x87D1ABE1|34001: Modello di corrispondenza URL non valido|
|-2016302112|0x87D1ABE0|34000: Modello di corrispondenza ID app non valido|
|-2016304112|0x87D1A410|32000: Troppe app|
|-2016305111|0x87D1A029|31001: Impossibile applicare le impostazioni|
|-2016305112|0x87D1A028|31000: Impossibile applicare le credenziali|
|-2016306111|0x87D19C41|30001: Timeout|
|-2016306112|0x87D19C40|30000: Autenticazione non riuscita|
|-2016307109|0x87D1985B|29003: Dati certificato non corretti|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000: Dispositivo non supervisionato|
|-2016308110|0x87D19472|28002: Impossibile impostare lo sfondo|
|-2016308111|0x87D19471|28001: Immagine sfondo non corretta|
|-2016308112|0x87D19470|28000: Elemento sconosciuto|
|-2016310111|0x87D18CA1|26001 Crittografia di livello file non supportata|
|-2016310112|0x87D18CA0|26000: Crittografia di livello blocco non supportata|
|-2016311110|0x87D188BA|25002: Impossibile rimuovere|
|-2016311111|0x87D188B9|25001: Impossibile installare|
|-2016311112|0x87D188B8|25000: Profilo non corretto|
|-2016312109|0x87D184D3|24003: Profilo finale non corretto|
|-2016312110|0x87D184D2|24002: Payload identità non corretto|
|-2016312111|0x87D184D1|24001: Impossibile firmare il dizionario degli attributi|
|-2016312112|0x87D184D0|24000: Impossibile creare il dizionario degli attributi|
|-2016313110|0x87D180EA|23002: Certificato server non valido|
|-2016313111|0x87D180E9|23001: Risposta del server non corretta|
|-2016313112|0x87D180E8|23000: Identità non corretta|
|-2016314099|0x87D17D0D|22013: Risposta operazione PKI non valida|
|-2016314100|0x87D17D0C|22012: Impossibile archiviare il certificato CA|
|-2016314101|0x87D17D0B|22011: Impossibile generare CSR|
|-2016314102|0x87D17D0A|22010: Impossibile archiviare l'identità temporanea|
|-2016314103|0x87D17D09|22009: Impossibile creare l'identità temporanea|
|-2016314104|0x87D17D08|22008: Impossibile creare l'identità|
|-2016314105|0x87D17D07|22007: Certificato firmato non valido|
|-2016314106|0x87D17D06|22006: CACaps non sufficienti|
|-2016314107|0x87D17D05|22005: Errore di rete|
|-2016314108|0x87D17D04|22004: Configurazione dei certificati non supportata|
|-2016314109|0x87D17D03|22003: RAResponse non valida|
|-2016314110|0x87D17D02|22002: CAResponse non valida|
|-2016314111|0x87D17D01|22001: Impossibile generare la coppia di chiavi|
|-2016314112|0x87D17D00|22000: Utilizzo della chiave non valido|
|-2016315105|0x87D1791F|21007: Impossibile verificare l'account|
|-2016315106|0x87D1791E|21006: Impossibile decrittografare il certificato|
|-2016315107|0x87D1791D|21005: account non univoco (il profilo di posta elettronica esiste già nel dispositivo)|
|-2016315108|0x87D1791C|21004: Impossibile creare l'account|
|-2016315109|0x87D1791B|21003: Nessun nome host|
|-2016315110|0x87D1791A|21002: Impossibile conformarsi con il criterio di crittografia dal server|
|-2016315111|0x87D17919|21001: Impossibile conformarsi con il criterio dal server|
|-2016315112|0x87D17918|21000: Impossibile ottenere il criterio dal server|
|-2016316110|0x87D17532|20002: Account non univoco|
|-2016316111|0x87D17531|20001: Nessun nome host|
|-2016316112|0x87D17530|20000: Impossibile creare l'account|
|-2016317110|0x87D1714A|19002: Account non univoco|
|-2016317111|0x87D17149|19001: Nessun nome host|
|-2016317112|0x87D17148|19000: Impossibile creare l'account|
|-2016318110|0x87D16D62|18002: Credenziali non valide|
|-2016318111|0x87D16D61|18001: Host non raggiungibile|
|-2016318112|0x87D16D60|18000: Errore sconosciuto|
|-2016319110|0x87D1697A|17002: Account non univoco|
|-2016319111|0x87D16979|17001: Nessun nome host|
|-2016319112|0x87D16978|17000: Impossibile creare l'account|
|-2016320110|0x87D16592|16002: Account non univoco|
|-2016320111|0x87D16591|16001: Nessun nome host|
|-2016320112|0x87D16590|16000: Impossibile creare la sottoscrizione|
|-2016321109|0x87D161AB|15003: Certificato non valido|
|-2016321110|0x87D161AA|15002: Impossibile bloccare la configurazione di rete|
|-2016321111|0x87D161A9|15001: Impossibile rimuovere VPN|
|-2016321112|0x87D161A8|15000: Impossibile installare VPN|
|-2016322110|0x87D15DC2|14002: Configurazione cloud già esistente|
|-2016322111|0x87D15DC1|14001: Dispositivo bloccato|
|-2016322112|0x87D15DC0|14000: Campo non valido|
|-2016323107|0x87D159DD|13005: Impossibile configurare il proxy|
|-2016323108|0x87D159DC|13004: Impossibile configurare EAP|
|-2016323109|0x87D159DB|13003: Impossibile creare la configurazione Wi-Fi|
|-2016323110|0x87D159DA|13002: Password richiesta|
|-2016323111|0x87D159D9|13001: Nome utente richiesto|
|-2016323112|0x87D159D8|13000: Impossibile installare|
|-2016324070|0x87D1561A|12042: Codice impostazioni locali sconosciuto|
|-2016324071|0x87D15619|12041: Codice lingua sconosciuto|
|-2016324072|0x87D15618|12040: Accesso allo store iTunes obbligatorio|
|-2016324073|0x87D15617|12039: (non utilizzato)|
|-2016324074|0x87D15616|12038: App non gestita|
|-2016324075|0x87D15615|12037: Codice riscatto non valido|
|-2016324076|0x87D15614|12036: Impossibile rimuovere l'app nello stato corrente|
|-2016324077|0x87D15613|12035: App non acquistabile|
|-2016324078|0x87D15612|12034: L'URL non è HTTPS|
|-2016324079|0x87D15611|12033: Manifesto non valido|
|-2016324080|0x87D15610|12032: Numero eccessivo di app nel manifesto|
|-2016324081|0x87D1560F|12031: Installazione app disabilitata|
|-2016324082|0x87D1560E|12030: URL non valido|
|-2016324083|0x87D1560D|12029: App non gestita|
|-2016324084|0x87D1560C|12028: Non in attesa di riscatto|
|-2016324085|0x87D1560B|12027: Non è un'app|
|-2016324086|0x87D1560A|12026: App già in coda|
|-2016324087|0x87D15609|12025: App già installata|
|-2016324088|0x87D15608|12024: Impossibile convalidare il manifesto dell'app|
|-2016324089|0x87D15607|12023: Impossibile convalidare l'ID dell'app|
|-2016324090|0x87D15606|12022: Argomento non valido|
|-2016324091|0x87D15605|12021: Tipo di richiesta non valido|
|-2016324092|0x87D15604|12020: Non autorizzato dal server|
|-2016324093|0x87D15603|12019: Impossibile copiare la chiave segreta del deposito|
|-2016324094|0x87D15602|12018: Impossibile copiare i dati del contenitore del deposito|
|-2016324095|0x87D15601|12017: Impossibile creare il contenitore del deposito|
|-2016324096|0x87D15600|12016: Identità mancante|
|-2016324097|0x87D155FF|12015: Impossibile ottenere il token push|
|-2016324098|0x87D155FE|12014: Profilo di provisioning non gestito|
|-2016324099|0x87D155FD|12013: Profilo non gestito|
|-2016324100|0x87D155FC|12012: Mancata corrispondenza della sostituzione MDM|
|-2016324101|0x87D155FB|12011: Configurazione MDM non valida|
|-2016324102|0x87D155FA|12010: Errore di incoerenza interno|
|-2016324103|0x87D155F9|12009: Profilo di sostituzione non valido|
|-2016324104|0x87D155F8|12008: Formato della richiesta non valido|
|-2016324105|0x87D155F7|12007: Non autorizzato|
|-2016324106|0x87D155F6|12006: Reindirizzamento rifiutato|
|-2016324107|0x87D155F5|12005: Impossibile trovare il certificato|
|-2016324108|0x87D155F4|12004: Certificato push non valido|
|-2016324109|0x87D155F3|12003: Risposta alla richiesta non valida|
|-2016324110|0x87D155F2|12002: Impossibile archiviare|
|-2016324111|0x87D155F1|12001: Istanze MDM multiple|
|-2016324112|0x87D155F0|12000: Diritti di accesso non validi|
|-2016325111|0x87D15209|11001: APN personalizzato già installato|
|-2016325112|0x87D15208|11000: Impossibile installare VPN|
|-2016326111|0x87D14E21|10001: Firmatario non valido|
|-2016326112|0x87D14E20|10000: Impossibile installare le impostazioni definite|
|-2016327106|0x87D14A3E|9006: Il certificato non è un'identità|
|-2016327107|0x87D14A3D|9005: Formato del certificato non valido|
|-2016327108|0x87D14A3C|9004: Impossibile archiviare il certificato root|
|-2016327109|0x87D14A3B|9003: Impossibile archiviare i dati WAPI|
|-2016327110|0x87D14A3A|9002: Impossibile archiviare il certificato|
|-2016327111|0x87D14A39|9001: Troppi certificati in un payload|
|-2016327112|0x87D14A38|9000: Password non valida|
|-2016328112|0x87D14650|8000: Impossibile installare Web Clip|
|-2016329105|0x87D1426F|7007: Account SMTP non configurato correttamente|
|-2016329106|0x87D1426E|7006: Account POP non configurato correttamente|
|-2016329107|0x87D1426D|7005: Account IMAP non configurato correttamente|
|-2016329108|0x87D1426C|7004: Certificato SMIME non valido|
|-2016329109|0x87D1426B|7003: Certificato SMIME non trovato|
|-2016329110|0x87D1426A|7002: Durante la convalida si è verificato un errore sconosciuto|
|-2016329111|0x87D14269|7001: Credenziali non valide|
|-2016329112|0x87D14268|7000: Host non raggiungibile|
|-2016330110|0x87D13E82|6002: Impossibile creare la query|
|-2016330111|0x87D13E81|6001: Stringa vuota|
|-2016330112|0x87D13E80|6000: Errore di sistema keychain|
|-2016331097|0x87D13AA7|5015: Impossibile impostare il periodo di prova|
|-2016331098|0x87D13AA6|5014: Impossibile impostare il passcode|
|-2016331099|0x87D13AA5|5013: Impossibile cancellare il passcode|
|-2016331100|0x87D13AA4|5012: (non utilizzato)|
|-2016331101||5011: Passcode non corretto|
|-2016331102||5010: Dispositivo bloccato|
|-2016331103|0x87D13AA4|5009: (non utilizzato)|
|-2016331104|0x87D13AA0|5008: Passcode troppo recente|
|-2016331105|0x87D13A9F|5007: Passcode scaduto|
|-2016331106|0x87D13AA3|5006: Il passcode richiede caratteri alfabetici|
|-2016331107|0x87D13A9D|5005: Il passcode richiede un numero|
|-2016331108|0x87D13A9C|5004: Il passcode contiene caratteri crescenti decrescenti|
|-2016331109|0x87D13A9B|5003: Il passcode contiene caratteri ripetuti|
|-2016331110|0x87D13A9A|5002: Numero di caratteri complessi insufficiente|
|-2016331111|0x87D13A99|5001: Numero di caratteri univoci insufficiente|
|-2016331112|0x87D13A98|5000: Passcode troppo breve|
|-2016332093|0x87D136C3|4019: Più payload di blocco app|
|-2016332094|0x87D136C2|4018: Più payload APN o Cellulare|
|-2016332095|0x87D136C1|4017: Più payload HTTPProxy globali|
|-2016332096|0x87D136C0|4016: (Errore interno)|
|-2016332097|0x87D136BF|4015: Il profilo di sostituzione non contiene un payload MDM|
|-2016332098|0x87D136BE|4014: Nessuna identità del dispositivo disponibile|
|-2016332099|0x87D136BD|4013: Aggiornamento non riuscito|
|-2016332100|0x87D136BC|4012: Profilo non aggiornabile|
|-2016332101|0x87D136BB|4011: Il profilo finale non è un profilo di configurazione|
|-2016332102|0x87D136BA|4010: Il profilo aggiornato non ha lo stesso identificatore|
|-2016332103|0x87D136B9|4009: Dispositivo bloccato|
|-2016332104|0x87D136B8|4008: Mancata corrispondenza dei certificati|
|-2016332105|0x87D136B7|4007: Formato file non riconosciuto|
|-2016332106|0x87D136B6|4006: La data di rimozione del profilo è scaduta|
|-2016332107|0x87D136B5|4005: Passcode non conforme|
|-2016332108|0x87D136B4|4004: Installazione annullata dall'utente|
|-2016332109|0x87D136B3|4003: Profilo non in coda per l'installazione|
|-2016332110|0x87D136B2|4002: UUID duplicato|
|-2016332111|0x87D136B1|4001: Errore di installazione|
|-2016332112|0x87D136B0|4000: Impossibile analizzare il profilo|
|-2016333111|0x87D132C9|3001: Senso di confronto di valori non coerente (errore interno)|
|-2016333112|0x87D132C8|3000: Senso di limitazione non coerente (errore interno)|
|-2016334108|0x87D12EE4|2004: Valore campo non supportato|
|-2016334109|0x87D12EE3|2003: Tipo di dati nel campo non corretti|
|-2016334110|0x87D12EE2|2002: Campo richiesto mancante|
|-2016334111|0x87D12EE1|2001: Versione payload non supportata|
|-2016334112|0x87D12EE0|2000: Formato payload non valido|
|-2016335102|0x87D12B02|1010: Valore campo non supportato|
|-2016335103|0x87D12B01|1009: Errore di installazione del profilo|
|-2016335104|0x87D12B00|1008: Identificatori di payload non univoci|
|-2016335105|0x87D12AFF|1007: UUID non univoci|
|-2016335106|0x87D12AFE|1006: Impossibile decrittografare|
|-2016335107|0x87D12AFD|1005: Profilo vuoto|
|-2016335108|0x87D12AFC|1004: Firma non corretta|
|-2016335109|0x87D12AFB|1003: Tipo di dati nel campo non corretti|
|-2016335110|0x87D12AFA|1002: Campo richiesto mancante|
|-2016335111|0x87D12AF9|1001: Versione profilo non supportata|
|-2016335112|0x87D12AF8|1000: Formato profilo non valido|

## <a name="oma-response-codes"></a>Codici di risposta OMA

|Codice di stato|Codice di errore esadecimale|Messaggio di errore|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): accesso certificato negato|
|-2016344009|0x87D10837|(1403): certificato non trovato|
|-2016344010|0x87D10836|DCMO(1402): operazione non riuscita|
|-2016344011|0x87D10835|DCMO(1401): l'utente ha scelto di non accettare l'operazione, quando richiesto|
|-2016344012|0x87D10834|DCMO(1400): errore client|
|-2016344108|0x87D107D4|DCMO(1204): la funzionalità di dispositivo è disabilitata e l'utente dispone dell'autorizzazione per riabilitarla|
|-2016344109|0x87D107D3|DCMO(1203): la funzionalità di dispositivo è disabilitata e l'utente non dispone dell'autorizzazione per riabilitarla|
|-2016344110|0x87D107D2|DCMO(1202): l'abilitazione è stata eseguita correttamente, ma la funzionalità di dispositivo è attualmente scollegata|
|-2016344111|0xF3FB4D95|DCMO(1201): l'abilitazione è stata eseguita correttamente e la funzionalità di dispositivo è attualmente collegata|
|-2016344112|0x87D107D0|DCMO(1200): operazione completata correttamente|
|-2016345595|0x87D10205|Syncml(517): la risposta a un comando atomico è troppo lunga per essere contenuta in un solo messaggio.|
|-2016345596|0x87D10204|Syncml(516): il comando era incluso in un elemento atomico non riuscito. Il rollback di questo comando non è stato eseguito correttamente.|
|-2016345598|0x87D10202|Syncml(514): il comando SyncML non è stato completato correttamente poiché l'operazione è stata annullata prima dell'elaborazione del comando.|
|-2016345599|0x87D10201|Syncml(513): il destinatario non supporta o rifiuta di supportare la versione specificata del protocollo di sincronizzazione SyncML usato nel messaggio di richiesta SyncML.|
|-2016345600|0x87D10200|Syncml(512): si è verificato un errore dell'applicazione durante la sessione di sincronizzazione.|
|-2016345601|0x87D101FF|Syncml(511): si è verificato un errore grave nel server durante l'elaborazione della richiesta.|
|-2016345602|0x87D101FE|Syncml(510): si è verificato un errore durante l'elaborazione della richiesta. L'errore è correlato a un guasto nell'archivio dati del destinatario.|
|-2016345603|0x87D101FD|Syncml(509): riservato per un uso futuro.|
|-2016345604|0x87D101FC|Syncml(508): si è verificato un errore che richiede un aggiornamento dello stato di sincronizzazione corrente tra client e server.|
|-2016345605|0x87D101FB|Syncml(507): l'errore ha impedito il completamento di tutti i comandi SyncML all'interno di un tipo di elemento atomico.|
|-2016345606|0x87D101FA|Syncml(506): si è verificato un errore dell'applicazione durante l'elaborazione della richiesta.|
|-2016345607|0x87D101F9|Syncml(505): il destinatario non supporta o rifiuta di supportare la versione specificata di DTD SyncML usato nel messaggio SyncML della richiesta.|
|-2016345608|=0x87D101F8|Syncml(504): il destinatario, che agisce come gateway o proxy, non ha ricevuto una risposta tempestiva dal destinatario upstream specificato dall'URI (ad esempio, HTTP, FTP, LDAP) o da altri destinatari ausiliari (ad esempio, DNS), per il quale è richiesto l'accesso per il completamento della richiesta.|
|-2016345609|0x87D101F7|Syncml(503): il destinatario non è attualmente in grado di gestire la richiesta a causa di un sovraccarico temporaneo o a operazioni di manutenzione del destinatario.|
|-2016345610|0x87D101F6|Syncml(502): il destinatario, che agisce come gateway o proxy, ha ricevuto una risposta non valida dal destinatario upstream al quale si è connesso durante il tentativo di completare la richiesta.|
|-2016345611|0x87D101F5|Syncml(501): il destinatario non supporta il comando richiesto per completare la richiesta.|
|-2016345612|0x87D101F4|Syncml(500): si è verificata una condizione imprevista che ha impedito al destinatario di completare la richiesta|
|-2016345684|0x87D101AC|Syncml(428): spostamento non riuscito|
|-2016345685|0x87D101AB|Syncml(427): non è possibile eliminare il padre poiché contiene elementi figlio.|
|-2016345686|0x87D101AA|Syncml(426): elemento parziale non accettato.|
|-2016345687|0x87D101A9|Syncml(425): il comando richiesto non è riuscito perché il mittente non dispone di autorizzazioni di controllo dell'accesso (ACL) per il destinatario.|
|-2016345688|0x87D101A8|Syncml(424): l'oggetto in blocchi è stato ricevuto, ma le dimensioni dell'oggetto non corrispondono a quelle dichiarate nel primo blocco.|
|-2016345689|0x87D101A7|Syncml(423): il comando richiesto non è riuscito perché l'elemento con eliminazione reversibile nel server figurava precedentemente come eliminato definitivamente.|
|-2016345690|0x87D101A6|Syncml(422): il comando richiesto non è riuscito nel server perché lo script CGI in LocURI era formato in modo errato.|
|-2016345691|0x87D101A5|Syncml(421): il comando richiesto non è riuscito nel server perché la grammatica di ricerca specificata non era nota.|
|-2016345692|0x87D101A4|Syncml(420): il destinatario non dispone di ulteriore spazio di archiviazione per i dati di sincronizzazione rimanenti.|
|-2016345693|0x87D101A3|Syncml(419): la richiesta client ha creato un conflitto risolto dal comando server dominante.|
|-2016345694|0x87D101A2|Syncml(418): il comando Put o Add richiesto non è riuscito perché la destinazione esiste già.|
|-2016345695|0x87D101A1|Syncml(417): la richiesta non è riuscita. L'iniziatore deve riprovare in un secondo momento.|
|-2016345696|0x87D101A0|Syncml(416): la richiesta non è riuscita perché le dimensioni in byte specificate nella richiesta erano troppo elevate.|
|-2016345697|0x87D1019F|Syncml(415): tipo o formato del supporto non supportato.|
|-2016345698|0x87D1019E|Syncml(414): il comando richiesto non è riuscito perché l'URI di destinazione era troppo lungo per le capacità di elaborazione del destinatario.|
|-2016345699|0x87D1019D|Syncml(413): il destinatario rifiuta di eseguire il comando richiesto perché l'elemento richiesto è eccessivo rispetto alle capacità di elaborazione del destinatario.|
|-2016345700|0x87D1019C|Syncml(412): il comando richiesto non è riuscito nel destinatario perché era incompleto o formato in modo errato.|
|-2016345701|0x87D1019B|Syncml(411): il comando richiesto deve essere accompagnato da informazioni sulle dimensioni in byte o sulla lunghezza nel tipo di elemento Meta.|
|-2016345702|0x87D1019A|Syncml(410): la destinazione richiesta non si trova più nel destinatario e non è disponibile alcun URI di inoltro.|
|-2016345703|0x87D10199|Syncml(409): la richiesta non è riuscita a causa di un conflitto di aggiornamenti tra le versioni client e server dei dati.|
|-2016345704|0x87D10198|Syncml(408): non è stato ricevuto un messaggio previsto nel periodo di tempo specificato.|
|-2016345705|0x87D10197|Syncml(407): il comando richiesto non è riuscito perché l'iniziatore deve fornire l'autenticazione necessaria.|
|-2016345706|0x87D10196|Syncml(406): il comando richiesto non è riuscito perché una funzione facoltativa della richiesta non è supportata.|
|-2016345707|0x87D10195|Syncml(405): il comando richiesto non è consentito nella destinazione.|
|-2016345708|0x87D10194|Syncml(404): la destinazione richiesta non è stata trovata.|
|-2016345709|0x87D10193|Syncml(403): il comando richiesto non è riuscito, ma è stato compreso dal destinatario.|
|-2016345710|0x87D10192|Syncml(402): il comando richiesto non è riuscito perché è necessario il pagamento corretto.|
|-2016345711|0x87D10191|Syncml(401): il comando richiesto non è riuscito perché il richiedente deve fornire l'autenticazione necessaria.|
|-2016345712|0x87D10190|Syncml(400): il comando richiesto non è riuscito a causa di una sintassi errata del comando.|
|-2016345807|0x87D10131|Syncml(305): la destinazione richiesta deve essere accessibile dall'URI del proxy specificato.|
|-2016345808|0x87D10130|Syncml (304): il comando richiesto SyncML non è stato eseguito nella destinazione.|
|-2016345809|0x87D1012F|Syncml(303): la destinazione richiesta non è stata rilevata in un altro URI.|
|-2016345810|0x87D1012E|Syncml(302): la destinazione richiesta è stata spostata temporaneamente in un URI diverso.|
|-2016345811|0x87D1012D|Syncml(301): la destinazione richiesta dispone di un nuovo URI.|
|-2016345812|0x87D1012C|Syncml(300): la destinazione richiesta è una delle diverse alternative disponibili.|
|-2016345896|0x87D100D8|Syncml(216): un comando era incluso in un elemento atomico non riuscito. Il rollback di questo comando è stato eseguito correttamente.|
|-2016345897|0x87D100D7|Syncml(215): un comando non è stato eseguito a causa dell'interazione con l'utente, che ha scelto di non accettare l'opzione.|
|-2016345898|0x87D100D6|Syncml(214): operazione annullata. Il comando SyncML è stato completato correttamente, ma nessun altro comando verrà elaborato all'interno della sessione.|
|-2016345899|0x87D100D5|Syncml(213): elemento in blocchi accettato e memorizzato nel buffer.|
|-2016345900|0x87D100D4|Syncml(212): autenticazione accettata. Non è necessaria alcuna ulteriore autenticazione per il resto della sessione di sincronizzazione. Questo codice di risposta è utilizzabile solo in risposta a una richiesta in cui sono state fornite le credenziali.|
|-2016345901|0x87D100D3|Syncml(211): elemento non eliminato. Elemento richiesto non trovato. È possibile che sia stato eliminato in precedenza.|
|-2016345902|0x87D100D2|Syncml(210): eliminazione senza archiviazione. La risposta indica che i dati richiesti sono stati eliminati, ma che non sono stati archiviati prima dell'eliminazione perché questa funzionalità facoltativa non era supportata dall'implementazione.|
|-2016345903|0x87D100D1|Conflitto risolto con duplicato. La risposta indica che la richiesta ha creato un conflitto di aggiornamento; che è stato risolto con una duplicazione dei dati del client, creati nel database del server. La risposta include l'URI di destinazione del duplicato nell'elemento dello stato. Inoltre, nel caso di una sincronizzazione bidirezionale, un comando Add viene restituito con la definizione di dati duplicati.|
|-2016345904|0x87D100D0|Conflitto risolto con il comando del client "vincente". La risposta indica che si è verificato un conflitto di aggiornamento che è stato risolto dal comando del client vincente.|
|-2016345905|0x87D100CF|Conflitto risolto con l'unione. La risposta indica che la richiesta ha creato un conflitto che è stato risolto con un'operazione di unione delle istanze del client e server dei dati. La risposta include gli URL di origine e di destinazione nell'elemento dello stato. Inoltre, un comando Replace viene restituito con i dati uniti.|
|-2016345906|0x87D100CE|La risposta indica che solo una parte del comando è stata completata. Se il resto del comando può essere completato successivamente, al completamento deve essere creato un altro codice di stato richiesta di completamento appropriato.|
|-2016345907|0x87D100CD|L'origine deve aggiornare il relativo contenuto. Il creatore della richiesta ha indicato che il contenuto deve essere sincronizzato per ottenere una versione aggiornata.|
|-2016345908|0x87D100CC|La richiesta è stata completata, ma non viene restituito alcun dato. Il codice di risposta viene restituito in risposta a un'operazione Get anche quando la destinazione non presenta alcun contenuto.|
|-2016345909|0x87D100CB|Risposta non autorevole. La risposta alla richiesta è fornita da un'entità diversa da quella di destinazione. La risposta deve essere restituita solo se la richiesta sarebbe stata restituita in un codice di risposta 200 dalla destinazione autorevole.|
|-2016345910|0x87D100CA|Accettata per l'elaborazione. La richiesta per avviare un'esecuzione remota di un'applicazione o segnalare che un utente o un'applicazione è stata eseguita correttamente.|
|-2016345911|0x87D100C9|È stato aggiunto l'elemento richiesto.|
|-2016345912|0x87D100C8|Il comando SyncML è stato completato correttamente.|
|-2016346011|0x87D10065|Il comando specificato SyncML è in fase di esecuzione ma non è stato ancora completato.|

## <a name="next-steps"></a>Passaggi successivi

Contattare il supporto tecnico di Microsoft per [ottenere supporto per Microsoft Intune](../get-support.md).
