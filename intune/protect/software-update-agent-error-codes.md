---
title: Errori di aggiornamento software e relative descrizioni in Microsoft Intune - Azure | Microsoft Docs
description: Elenco dei codici di errore dell'agente di aggiornamento software in Microsoft Intune, completo di codice errore, nome simbolico e descrizione dell'errore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bf6a4b92a913b2ef359466ac3a5239bb9387994
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735909"
---
# <a name="software-update-agent-error-codes-and-descriptions-in-microsoft-intune"></a>Codici di errore dell'agente di aggiornamento software e descrizioni in Microsoft Intune

La tabella seguente elenca i codici di errore dell'**agente di aggiornamento** di Intune. Se non si trova un codice di errore specifico in questa tabella, vedere l'[elenco dei codici di errore di Windows Update](https://support.microsoft.com/help/938205/windows-update-error-code-list).

|Codice errore|Nome simbolico|Altre informazioni|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|L'agente è stato interrotto correttamente.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|L'operazione è stata completata correttamente, ma si sono verificati errori durante l'applicazione degli aggiornamenti.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Una richiamata è stata contrassegnata per la disconnessione successiva, perché la richiesta di disconnessione dell'operazione si è verificata mentre la richiamata era in esecuzione.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|Per completare l'installazione dell'aggiornamento, è necessario riavviare il sistema.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|L'aggiornamento da installare è già installato nel sistema.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|L'aggiornamento da rimuovere non è installato nel sistema.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|L'installazione dell'aggiornamento è in corso.|
|**0x80cf0001**|OM_E_NO_SERVICE|L'agente non è stato in grado di fornire il servizio.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|È stata superata la capacità massima del servizio.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|Impossibile trovare un ID.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|Impossibile inizializzare l'oggetto.|
|**0x80cf0007**|OM_E_INVALIDINDEX|L'indice di una raccolta non è valido.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|Impossibile trovare la chiave per l'elemento oggetto della query.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Era in corso un'operazione in conflitto. Alcune operazioni, ad esempio le installazioni multiple, non possono essere eseguite contemporaneamente.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|L'operazione è stata annullata.|
|**0x80cf000C**|OM_E_NOOP|Nessuna operazione è stata necessaria.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|L'agente non è stato in grado di trovare le informazioni richieste nei dati XML dell'aggiornamento.|
|**0x80cf000E**|OM_E_XML_INVALID|L'agente ha trovato informazioni non valide nei dati XML dell'aggiornamento.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Nei metadati sono state rilevate relazioni circolari di aggiornamento.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|Le relazioni di aggiornamento erano eccessivamente nidificate per la valutazione.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|È stata trovata una relazione di aggiornamento non valida.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|È stato letto un valore del Registro di sistema non valido.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|L'operazione ha tentato di aggiungere un elemento duplicato a un elenco.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|Il chiamante non è in grado di installare gli aggiornamenti necessari per l'installazione.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|L'operazione ha tentato di effettuare l'installazione mentre un'altra installazione era in corso o il sistema era in attesa di riavvio del sistema obbligatorio.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|L'operazione non è stata eseguita perché non sono presenti aggiornamenti applicabili.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|L'operazione non è riuscita perché un token utente necessario risulta mancante.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|Impossibile installare un aggiornamento esclusivo simultaneamente con altri aggiornamenti.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Non è stato impostato un valore del criterio.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Un aggiornamento contiene metadati non validi.|
|**0x80cf001E**|OM_E_SERVICE_STOP|Impossibile completare l'operazione. Il servizio o il sistema erano in fase di arresto.|
|**0x80cf001F**|OM_E_NO_CONNECTION|Impossibile completare l'operazione. La connessione di rete non era disponibile.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|Impossibile completare l'operazione. Nessun utente interattivo è connesso.|
|**0x80cf0021**|OM_E_TIME_OUT|Impossibile completare l'operazione. Tempo scaduto.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|Operazione non riuscita per tutti gli aggiornamenti.|
|**0x80cf0024**|OM_E_NO_UPDATE|Non sono disponibili aggiornamenti.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|Le impostazioni dei Criteri di gruppo hanno impedito l'accesso a Windows Update.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|Il tipo di aggiornamento non è valido.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|Impossibile disinstallare l'aggiornamento. La richiesta non proviene da un server WSUS.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|La ricerca potrebbe aver ignorato alcuni aggiornamenti o potrebbe essere presente un'applicazione senza licenza nel sistema.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Impossibile installare un aggiornamento con compressione delta. È richiesto il codice sorgente.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Impossibile installare un aggiornamento di file completo. È richiesto il codice sorgente.|
|**0x80cf002E**|OM_E_WU_DISABLED|Non è consentito l'accesso a un server non gestito.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|Non è stato possibile completare l'operazione perché è stato impostato il criterio **DisableWindowsUpdateAccess**.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|Il formato di elenco del proxy non è valido.|
|**0x80cf0031**|OM_E_INVALID_FILE|Il formato del file non è corretto.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|La stringa di criteri di ricerca non è valida.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|Impossibile scaricare l'aggiornamento.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|L'aggiornamento non è stato elaborato.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|Lo stato corrente dell'oggetto non ha consentito l'operazione.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|L'operazione non è supportata.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|Il file scaricato ha un tipo di contenuto imprevisto.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|Il server ha richiesto all'agente di effettuare nuovamente la sincronizzazione troppe volte.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|Nessun supporto disponibile per l'interfaccia utente dell'Agente di Windows Update.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Solo gli amministratori possono eseguire questa operazione sugli aggiornamenti per computer.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|È stata tentata una ricerca con un ambito non supportato.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|L'URL non fa riferimento a un file.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|L'operazione richiesta non è supportata.|
|**0x80cf0049**|OM_E_OUTOFRANGE|I dati non rientrano nell'intervallo.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|I dati contengono una versione non valida.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|La chiamata di ricerca è stata completata, ma non è stato possibile rilevare alcuni aggiornamenti.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|La chiamata di ricerca è stata completata, ma non è stato possibile scaricare alcuni aggiornamenti.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|La chiamata di installazione è stata completata, ma non è stato possibile installare alcuni aggiornamenti.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|La cache di Windows Update è vuota perché non è stata inizializzata.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|Il server non supporta la ricerca specifica di categorie. È necessario eseguire la ricerca nel catalogo completo.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Si è verificato un problema di autorizzazione con il servizio.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|Non è disponibile alcun percorso o connettività di rete verso l'endpoint.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|I dati ricevuti non soddisfano le aspettative del contratto dati.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|L'URL non è valido.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|Impossibile caricare runtime NWS.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|Lo schema di autenticazione proxy non è supportato.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|La proprietà del servizio richiesto non è disponibile.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|Il plug-in del provider dell'endpoint richiede un aggiornamento in linea.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|Nessun URL disponibile per l'endpoint del servizio richiesto.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|La connessione all'endpoint del servizio è stata terminata.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|L'operazione non è valida perché lo stato del talker di protocollo non è appropriato.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|Un'operazione non è riuscita a causa di motivi non spiegati da un altro codice errore.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|La ricerca potrebbe aver ignorato alcuni aggiornamenti perché Windows Installer è una versione precedente alla versione 3.1.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|La ricerca potrebbe aver ignorato alcuni aggiornamenti poiché Windows Installer non è configurato.|
|**0x80cf1003**|OM_E_MSP_DISABLED|La ricerca potrebbe aver ignorato alcuni aggiornamenti perché il criterio ha disabilitato l'applicazione delle patch di Windows Installer.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Impossibile applicare un aggiornamento perché l'applicazione è installata per utente.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Impossibile completare una richiesta per un gestore di aggiornamento remoto. Nessun processo remoto disponibile.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Impossibile completare una richiesta per un gestore di aggiornamento remoto. Il gestore è solo locale.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Impossibile creare un gestore di aggiornamento remoto perché ne esiste già uno.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|Impossibile completare una richiesta per l'installazione (disinstallazione) di un aggiornamento da parte del gestore. L'aggiornamento non supporta l'installazione (disinstallazione).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Impossibile completare un'operazione. È stato specificato un gestore non corretto.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Impossibile completare un'operazione del gestore. L'aggiornamento contiene metadati non validi.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Non è possibile completare un'operazione. Il programma di installazione ha superato il limite di tempo. Controllare se un aggiornamento che richiede l'intervento dell'utente è stato approvato per la distribuzione. In questo caso, è necessario rivedere i parametri di installazione dell'aggiornamento, in modo che possa essere installato automaticamente.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Un'operazione in esecuzione mediante il gestore degli aggiornamenti è stata annullata.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Impossibile completare un'operazione. I metadati specifici del gestore non sono validi.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|Il programma di installazione non è stato in grado di installare (disinstallare) uno o più aggiornamenti.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|Il gestore degli aggiornamenti non ha installato l'aggiornamento perché è necessario scaricarlo nuovamente.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|Il gestore degli aggiornamenti non è stato in grado di inviare la notifica dello stato dell'installazione (disinstallazione) dell'operazione.|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|L'operazione di post-riavvio per l'aggiornamento è ancora in corso.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|Impossibile determinare il risultato dell'operazione di post-riavvio per l'aggiornamento.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|Stato dell'aggiornamento imprevisto in seguito al completamento dell'operazione post-riavvio.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|Lo stack di manutenzione del sistema operativo deve essere aggiornato prima che venga scaricato o installato questo aggiornamento.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Un programma di installazione di chiamata ha richiamato con un errore.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|La firma del programma di installazione personalizzato non corrisponde alla firma richiesta dall'aggiornamento.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|La configurazione dell'installazione non è supportata dal programma di installazione.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|La sessione di destinazione dell'installazione non è valida.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Un errore del gestore degli aggiornamenti non è coperto da un altro codice OM_E_UH_&#42;.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|Impossibile visualizzare l'interfaccia utente in modalità non interfaccia utente. I moduli di interfaccia utente del client di Windows Update potrebbero non essere installati.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Le funzioni esportate dell'interfaccia utente di questa versione del client di Windows Update non sono supportate.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Si è verificato un errore dell'interfaccia utente non coperto da un altro codice errore OM_E_AUCLIENT_&#42;.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Uguale a **SOAPCLIENT_SOAPFAULT**. Client SOAP non riuscito. Si è verificato un errore SOAP con codice errore di tipo **OM_E_PT_SOAP_&#42;** .|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Uguale a **SOAPCLIENT_PARSEFAULT_ERROR**.  Il client SOAP non è stato in grado di analizzare un errore SOAP.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Uguale a **SOAPCLIENT_PARSE_ERROR**.  Il client SOAP non è stato in grado di analizzare la risposta del server.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Uguale a **SOAP_E_VERSION_MISMATCH**. Il client SOAP ha trovato uno spazio dei nomi non riconoscibile per la envelope SOAP.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Uguale a **SOAP_E_MUST_UNDERSTAND**. Il client SOAP non è stato in grado di interpretare un'intestazione.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Uguale a **SOAP_E_CLIENT**. Il client SOAP ha rilevato che il messaggio non era valido. Correggere prima di inviare di nuovo.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Uguale a **SOAP_E_SERVER**. Non è stato possibile elaborare il messaggio SOAP a causa di un errore del server. Inviare di nuovo in un secondo momento.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|Il numero di round trip al server ha superato il limite massimo.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|Inizializzazione non riuscita. L'oggetto è già stato inizializzato.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|Non è stato possibile determinare il nome del computer.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|La risposta del server indica che il server è stato modificato o che il cookie non era valido. Aggiornare la cache interna e riprovare.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Uguale allo **stato HTTP 400**. Il server non è stato in grado di elaborare la richiesta perché la sintassi non è valida.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Uguale allo **stato HTTP 401**. La risorsa richiesta prevede l'autenticazione degli utenti.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Uguale allo **stato HTTP 403**. Il server è in grado di riconoscere la richiesta, ma non di soddisfarla.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Uguale allo **stato HTTP 404**. Il server non è in grado di trovare l'URI (Uniform Resource Identifier) richiesto.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Uguale allo **stato HTTP 405**. Il metodo HTTP non è consentito.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Uguale allo **stato HTTP 407**. È richiesta l'autenticazione proxy.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Uguale allo **stato HTTP 408**. Timeout del server durante l'attesa della richiesta.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Uguale allo **stato HTTP 409**. La richiesta non è stata completata a causa di un conflitto con lo stato corrente della risorsa.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Uguale allo **stato HTTP 410**. La risorsa richiesta non è più disponibile sul server.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Uguale allo **stato HTTP 500**. Un errore interno del server ha impedito di soddisfare la richiesta.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Uguale allo **stato HTTP 500**. Il server non supporta la funzionalità necessaria per soddisfare la richiesta.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Uguale allo **stato HTTP 502**. Operando come gateway o proxy, il server ha ricevuto una risposta non valida dal server padre a cui si effettua l'accesso nel tentativo di soddisfare la richiesta.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Uguale allo **stato HTTP 503**. Il servizio è momentaneamente sovraccarico.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Uguale allo **stato HTTP 503**. Richiesta scaduta in attesa di un gateway.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Uguale allo **stato HTTP 505**. Il server non supporta la versione del protocollo HTTP usata per la richiesta.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|L'operazione non è stata completata a causa della modifica del percorso dei file. Aggiornare lo stato interno e inviare di nuovo.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|Il server ha restituito un elenco di informazioni di autenticazione vuoto.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|L'agente non è stato in grado di creare cookie di autenticazione validi.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Valore di una proprietà di configurazione errato.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Valore di una proprietà di configurazione mancante.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|Impossibile completare la richiesta HTTP. Il motivo non corrisponde a nessun codice errore **OM_E_PT_HTTP_&#42;** .|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Uguale a **ERROR_WINHTTP_NAME_NOT_RESOLVED**. Impossibile risolvere il nome del server proxy o del server di destinazione.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|L'elaborazione del file CAB esterno è stata completata con alcuni errori.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|L'inizializzazione dell'elaboratore CAB esterno non è stata completata.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|Il formato di un file di metadati non è valido.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|L'elaboratore cab esterno ha trovato metadati non validi.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Impossibile estrarre il digest file da un file in formato CAB esterno.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Impossibile decomprimere un file in formato CAB esterno.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|L'elaboratore cab esterno non è stato in grado di ottenere le posizioni dei file.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Si è verificato un errore di comunicazione non coperto da un altro codice errore **OM_E_PT_&#42;** .|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Impossibile completare un'operazione di download manager. Il file richiesto non dispone di un URL.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Impossibile completare un'operazione di download manager. Il digest file non è stato riconosciuto.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Impossibile completare un'operazione di download manager. I metadati dei file hanno richiesto un algoritmo hash non riconosciuto.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Impossibile completare un'operazione di download manager. La connessione di rete non era disponibile.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|L'aggiornamento non è stato scaricato.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|Un'operazione di download manager non è stata completata perché download manager non è stato in grado di connettersi al servizio trasferimento intelligente in background (BITS).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|Un'operazione di download manager non riuscita perché si è verificato un errore di trasferimento non specificato del servizio trasferimento intelligente in background (BITS).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|È necessario riavviare un download perché la sua posizione di origine è stata modificata.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|È necessario riavviare un download poiché il contenuto dell'aggiornamento è stato modificato in una nuova versione.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Si è verificato un errore di download manager non coperto da un altro codice errore **OM_E_DM_&#42;**|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|È stato specificato un payload dell'evento non valido.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|La dimensione del payload dell'evento inviato non è valida.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|Il servizio non è registrato.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|Un'operazione non è stata completata perché l'agente verrà arrestato.|
|**0x80cf8001**|OM_E_DS_INUSE|Un'operazione non è stata completata perché l'archivio dati era in uso.|
|**0x80cf8002**|OM_E_DS_INVALID|Gli stati corrente e previsto dell'archivio dati non corrispondono.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|L'archivio dati presenta una tabella mancante.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|L'archivio dati contiene una tabella con colonne impreviste.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|Impossibile aprire una tabella perché non è presente nell'archivio dati.|
|**0x80cf8006**|OM_E_DS_BADVERSION|Le versioni corrente e prevista dell'archivio dati non corrispondono.|
|**0x80cf8007**|OM_E_DS_NODATA|Le informazioni richieste non sono presenti nell'archivio dati.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|L'archivio dati presenta informazioni mancanti o ha un valore null in una colonna della tabella che richiede un valore diverso da null.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|L'archivio dati presenta informazioni necessarie mancanti o contiene un riferimento a condizioni di licenza, file, proprietà localizzata o riga collegata mancanti.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|L'aggiornamento non è stato elaborato perché il relativo gestore di aggiornamento non è stato riconosciuto.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|L'aggiornamento non è stato eliminato perché uno o più servizi fanno ancora riferimento ad esso.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|Non è stato possibile bloccare la sezione dell'archivio dati entro il tempo massimo consentito.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|La riga non è stata aggiunta perché una riga esistente contiene la stessa chiave primaria.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Impossibile inizializzare l'archivio dati perché è stato bloccato da un altro processo.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|Impossibile registrare l'archivio dati con COM nel processo corrente.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Un'operazione non è stata in grado di creare un oggetto archivio dati in un altro processo.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|Il server ha inviato lo stesso aggiornamento al client con due ID di versioni diverse.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Non è possibile completare un'operazione, perché il servizio non è presente nell'archivio dati.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Non è possibile completare un'operazione, perché la registrazione del servizio è scaduta.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|Una richiesta di nascondere un aggiornamento è stata rifiutata perché è un aggiornamento obbligatorio o perché è stato distribuito con una scadenza.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|Una tabella non è stata chiusa perché non è associata alla sessione.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|Una tabella non è stata chiusa perché non è associata alla sessione.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|La richiesta di rimuovere il servizio o annullare la sua registrazione è stata rifiutata perché il servizio è integrato o perché Aggiornamenti automatici non è in grado di usare un altro servizio.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|La richiesta è stata rifiutata perché l'operazione non è consentita.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|Lo schema dell'archivio dati corrente e lo schema di una tabella in un documento XML di backup non corrispondono.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|L'archivio dati richiede un ripristino della sessione. Rilasciare la sessione e riprovare con una nuova sessione.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|Impossibile completare un'operazione dell'archivio dati poiché è stata richiesta con un'identità rappresentata.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Si è verificato un errore dell'archivio dati che non è coperto da un altro codice **OM_E_DS_&#42;** .|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Aggiornamenti automatici non è stato in grado di servire le richieste in arrivo.|
|**0x80cfA004**|OM_E_AU_PAUSED|Aggiornamenti automatici non è stato in grado di elaborare le richieste in ingresso perché era stato sospeso.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Nessun servizio non gestito è registrato con Aggiornamenti automatici.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Il servizio predefinito registrato con Aggiornamenti automatici è stato modificato durante la ricerca.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Aggiornamenti automatici ha già richiesto all'utente di riavviare il computer.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Si è verificato un errore di Aggiornamenti automatici non coperto da un altro codice **OM_E_AU &#42;** .|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Non è stato possibile completare un'operazione dell'analizzatore di espressioni perché un'espressione non è stata riconosciuta.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Non è stato possibile completare un'operazione dell'analizzatore di espressioni perché un'espressione non era valida.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Non è stato possibile completare un'operazione dell'analizzatore di espressioni, perché un'espressione contiene un numero errato di nodi di metadati.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Non è possibile completare un'operazione dell'analizzatore di espressioni perché la versione dei dati serializzati dell'espressione non è valida.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|Impossibile inizializzare l'analizzatore di espressioni.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Non è stato possibile completare un'operazione dell'analizzatore di espressioni perché un attributo non è valido.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Non è possibile completare un'operazione dell'analizzatore di espressioni, poiché non è possibile determinare lo stato del cluster del computer.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Si è verificato un errore dell'analizzatore di espressioni non coperto da un altro codice di errore **OM_E_EE_&#42;** .|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|Il file della cache eventi non era corretto.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Non è stato possibile analizzare il codice XML nel descrittore dello spazio dei nomi dell'evento.|
|**0x80cfF003**|OM_E_INVALID_EVENT|Il codice XML nel descrittore dello spazio dei nomi dell'evento non è valido.|
|**0x80cfF004**|OM_E_SERVER_BUSY|Il server ha rifiutato un evento perché è occupato.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Si è verificato un errore nel report non coperto da un altro codice errore.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|Installazione non riuscita perché vi è un riavvio obbligatorio in sospeso.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|Il download è stato annullato.|