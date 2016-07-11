---
title: Comprendere le operazioni con l'uso dei report | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 06/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.sourcegitcommit: 617f1cd42de49f0c8675bd450591a390af674e73
ms.openlocfilehash: b8af36cef1bcb9077d0ab611a14fb88c0f458ece


---

# Comprendere le operazioni di Microsoft Intune con l'uso dei report
Usare le informazioni contenute in questo argomento per creare e gestire report di Microsoft Intune che forniscano informazioni su software, hardware e licenze software disponibili nell'organizzazione.

## Utilizzo dei report
I report di Intune forniscono informazioni su software, hardware e licenze software dell'organizzazione. I report contribuiscono a definire le esigenze correnti e a prevedere la spesa futura. Nell'area di lavoro **Report** vengono forniti gli strumenti per creare e gestire i report. Per altre informazioni sui report, vedere [Comprendere le operazioni di Microsoft Intune con l'uso dei report](understand-microsoft-intune-operations-by-using-reports.md).

### Tipi di report

|Tipo di report|Descrizione|
|---------------|---------------|
|**Report aggiornamenti**|Vengono visualizzati gli aggiornamenti software effettuati nei computer dell'organizzazione, oltre agli aggiornamenti non riusciti, in sospeso o necessari. Per altre informazioni sugli aggiornamenti software, vedere [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Report software rilevato**|Visualizza il software installato nei computer dell'organizzazione e include le versioni del software. È possibile filtrare le informazioni visualizzate in base all'editore e alla categoria del software. È possibile espandere gli aggiornamenti nell'elenco per visualizzare maggiori dettagli, ad esempio i computer in cui gli aggiornamenti sono installati, facendo clic sulla freccia direzionale accanto alla voce dell'elenco.<br /><br />Quando si ritirano i computer o se ne modifica l'appartenenza al gruppo in Intune, possono essere necessari diversi minuti prima che le modifiche siano visibili nel report software rilevato. Dopo aver disattivato i computer o averne modificato l'appartenenza al gruppo, attendere alcuni minuti prima di eseguire un report software rilevato che includa quei computer, in modo da ottenere dati il più accurati possibile dell'inventario software.|
|**Report inventario computer**|Visualizza le informazioni sui computer gestiti nell'organizzazione. Usare questo report per pianificare gli acquisti di hardware e per risalire all'hardware necessario per gli utenti nell'organizzazione. Per altre informazioni sull'uso di computer gestiti, vedere [Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Report inventario dispositivi mobili**|Visualizza le informazioni sui dispositivi mobili nell'organizzazione. È possibile filtrare le informazioni visualizzate in base ai gruppi, se il dispositivo è jailbroken o rooted e in base al sistema operativo.|
|**Report acquisto licenza**|Visualizza i titoli di tutto il software concesso in licenza ai gruppi di licenze selezionati, in base ai rispettivi contratti di licenza. Se le informazioni sulle licenze software non sono state aggiornate per più di 24 ore, vengono aggiornate quando si crea un report licenze. Il report licenze non è una prova di conformità contrattuale né un calcolo esatto dei titoli di software usati. ma solo uno strumento che agevola le decisioni aziendali relative alle licenze. Intune potrebbe non rilevare alcuni prodotti che possono avere un Contratto multilicenza Microsoft. I filtri disponibili sono:<br /><br />**Tutti i contratti** consente di visualizzare tutti i prodotti con contratto di licenza gestiti da Intune.<br /><br />**Contratti multilicenza** per visualizzare solo i prodotti software del Centro servizi per contratti multilicenza.<br /><br />**Altri contratti di licenza software** per visualizzare i contratti software gestiti al di fuori del Centro servizi per contratti multilicenza.|
|**Report installazione licenza**|Confrontare il software installato nei computer dell'organizzazione con l'attuale copertura del contratto di licenza secondo il Centro servizi per contratti multilicenza. I filtri includono:<br /><br />**Tutti i contratti** consente di visualizzare tutti i prodotti con contratto di licenza gestiti da Intune.<br /><br />**Contratti multilicenza** per visualizzare solo i prodotti software del Centro servizi per contratti multilicenza.<br /><br />**Altri contratti di licenza software** per visualizzare i contratti software gestiti al di fuori del Centro servizi per contratti multilicenza.|
|**Report termini e condizioni**|Indica se gli utenti hanno accettato i termini e le condizioni distribuiti e quale versione è stata accettata. È possibile specificare fino a 10 utenti di cui mostrare l'accettazione di tutti i termini e le condizioni distribuiti o mostrare lo stato di accettazione di termini e condizioni distribuiti specifici.|
|**Report app non conformi**|Mostra le informazioni sugli utenti che hanno installato app presenti negli elenchi di app conformi e non conformi. Usare questo report per individuare gli utenti e i dispositivi non conformi con i criteri della società relativi alle app.|
|**Report conformità certificato**|Indica quali sono i certificati rilasciati a utenti e dispositivi tramite SCEP o PKCS #12 (.PFX). Usare questo report per individuare i certificati rilasciati, scaduti e revocati.|
|**Report cronologia dispositivo**|Visualizza un log cronologico di azioni di disattivazione, cancellazione ed eliminazione. Usare questo report per vedere chi ha avviato le azioni sui dispositivi in passato.|
|**Report di attestazione dell'integrità**|Indica l'integrità dei dispositivi mobili.|
|**Report sull'hardware Mac OS X**|Visualizza i dettagli sull'hardware per tutti i dispositivi Mac OS X registrati nei gruppi selezionati. Per informazioni sull'inventario hardware raccolto da questi dispositivi, vedere [Informazioni sui dispositivi con inventario in Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Report sul software Mac OS X**|Visualizza il software installato in tutti i dispositivi Mac OS X nei gruppi selezionati. Nel report sono elencati il nome del software (come ID bundle), il nome abbreviato (o descrittivo), la versione e il numero di dispositivi in cui è installato il software.|

#### Per creare un report

1.  Nella console di amministrazione di Intune fare clic su **Report**e quindi fare clic sul tipo di report da generare, descritto nella tabella in alto.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report software rilevato solo il software pubblicato da Microsoft.

3.  Fare clic su **Visualizza report** per aprire il report in una nuova finestra.

Per ordinare il report in base a una delle colonne visualizzate, fare clic sull'intestazione di colonna. Inoltre, alcuni report consentono di espandere gli elementi dell'elenco per visualizzare maggiori dettagli.

## Ulteriori azioni report
Inoltre, i report supportano le seguenti operazioni:

|Azione|Altre informazioni|
|----------|--------------------|
|**Stampa**|In un report aperto fare clic sull'icona di stampa e seguire le istruzioni.|
|**Export**|In un report aperto fare clic sull'icona di esportazione e seguire le istruzioni. È possibile esportare un report in formato HTML o con valori separati da virgola (CSV).|
|**Salva**|Nella pagina **Crea nuovo report** ogni utente può salvare fino a 100 report. Configurare i parametri del report in base ai propri requisiti e quindi fare clic su **Salva**o **Salva con nome** se si desidera usare un altro nome.|
|**Carica**|Nella pagina **Crea nuovo report** fare clic su **Carica** per recuperare i gruppi di parametri report precedentemente salvati.|
|**Eliminazione**|Nell'area di lavoro **Report** selezionare il tipo di report desiderato, fare clic su **Carica**e quindi, nell'elenco di report, fare clic sull'icona di eliminazione (x) accanto al report.|

### Vedere anche
[Monitoraggio e report con Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)




<!--HONumber=Jun16_HO3-->


