---
title: Raccogliere informazioni operative tramite i report | Documentazione Microsoft
description: Creare e gestire report su software, hardware e licenze software dell&quot;organizzazione.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 3400a49feaca9ef34bcffcc176bc496310d4c357



---

# <a name="understand-microsoft-intune-operations-by-using-reports"></a>Comprendere le operazioni di Microsoft Intune con l'uso dei report

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare le informazioni contenute in questo argomento per creare e gestire report di Microsoft Intune che forniscano informazioni su software, hardware e licenze software disponibili nell'organizzazione.

## <a name="using-reports"></a>Utilizzo dei report
I report di Intune forniscono informazioni su software, hardware e licenze software dell'organizzazione. I report contribuiscono a definire le esigenze correnti e a prevedere la spesa futura. Nell'area di lavoro **Report** vengono forniti gli strumenti per creare e gestire i report. 

### <a name="report-types"></a>Tipi di report

|Tipo di report|Descrizione|
|---------------|---------------|
|**Report aggiornamenti**|Consente di visualizzare gli aggiornamenti software completati nei computer dell'organizzazione. Vengono inoltre visualizzati gli aggiornamenti non riusciti, in sospeso o necessari. Per altre informazioni sugli aggiornamenti software, vedere [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Report software rilevato**|Consente di visualizzare i prodotti software completati installati nei computer dell'organizzazione. Incluse le versioni del software. È possibile filtrare le informazioni visualizzate in base all'editore e alla categoria del software. È possibile espandere gli aggiornamenti nell'elenco per visualizzare maggiori dettagli, ad esempio i computer in cui un aggiornamento è installato, scegliendo la freccia direzionale accanto alla voce dell'elenco.<br /><br />Quando si ritirano i computer o se ne modifica l'appartenenza al gruppo in Intune, possono essere necessari diversi minuti prima che le modifiche siano visibili nel report software rilevato. Dopo aver disattivato i computer o averne modificato l'appartenenza al gruppo, attendere alcuni minuti prima di eseguire un report software rilevato che includa quei computer, in modo da ottenere dati il più accurati possibile dell'inventario software.|
|**Report inventario computer**|Visualizza le informazioni sui computer gestiti nell'organizzazione. Usare questo report per pianificare gli acquisti di hardware e per risalire all'hardware necessario per gli utenti nell'organizzazione. Per altre informazioni sull'uso di computer gestiti, vedere [Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Report inventario dispositivi mobili**|Visualizza le informazioni sui dispositivi mobili nell'organizzazione. È possibile filtrare le informazioni visualizzate in base ai gruppi, se il dispositivo è jailbroken o rooted e in base al sistema operativo.|
|**Report acquisto licenza**|Visualizza i titoli di tutto il software concesso in licenza ai gruppi di licenze selezionati, in base ai rispettivi contratti di licenza. Se le informazioni sulle licenze software non sono state aggiornate per più di 24 ore, vengono aggiornate quando si crea un report licenze. Il report licenze non è una prova di conformità contrattuale né un calcolo esatto dei titoli di software usati. ma solo uno strumento che agevola le decisioni aziendali relative alle licenze. Intune potrebbe non rilevare alcuni prodotti che possono avere un Contratto multilicenza Microsoft. I filtri disponibili sono:<br /><br />**Tutti i contratti** consente di visualizzare tutti i prodotti con contratto di licenza gestiti da Intune.<br /><br />**Contratti multilicenza** per visualizzare solo i prodotti software del Centro servizi per contratti multilicenza.<br /><br />**Altri contratti di licenza software** per visualizzare i contratti software gestiti al di fuori del Centro servizi per contratti multilicenza.|
|**Report installazione licenza**|Consente di confrontare il software installato nei computer dell'organizzazione con la copertura dei contratti di licenza corrente in base al Centro servizi per contratti multilicenza. I filtri includono:<br /><br />**Tutti i contratti** consente di visualizzare tutti i prodotti con contratto di licenza gestiti da Intune.<br /><br />**Contratti multilicenza** per visualizzare solo i prodotti software del Centro servizi per contratti multilicenza.<br /><br />**Altri contratti di licenza software** per visualizzare i contratti software gestiti al di fuori del Centro servizi per contratti multilicenza.|
|**Report relativi ai termini e alle condizioni**|Indica se gli utenti hanno accettato i termini e le condizioni distribuiti e quale versione è stata accettata. È possibile specificare fino a 10 utenti di cui mostrare l'accettazione di tutti i termini e le condizioni distribuiti o mostrare lo stato di accettazione di specifici termini distribuiti.|
|**Report App non conformi**|Mostra le informazioni sugli utenti che hanno installato app presenti negli elenchi di app conformi e non conformi. Usare questo report per individuare gli utenti e i dispositivi non conformi con i criteri della società relativi alle app.|
|**Report di conformità certificato**|Indica quali sono i certificati rilasciati a utenti e dispositivi tramite SCEP o PKCS #12 (.PFX). Usare questo report per individuare i certificati rilasciati, scaduti e revocati.|
|**Report cronologia dispositivo**|Visualizza un log cronologico di azioni di disattivazione, cancellazione ed eliminazione. Usare questo report per vedere chi ha avviato le azioni sui dispositivi in passato.|
|**Report di attestazione dell'integrità**|Indica l'integrità dei dispositivi mobili.|
|**Report sull'hardware Mac OS X**|Visualizza i dettagli sull'hardware per tutti i dispositivi Mac OS X registrati nei gruppi selezionati. Per informazioni sull'inventario hardware raccolto da questi dispositivi, vedere [Informazioni sui dispositivi con inventario in Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Report sul software Mac OS X**|Visualizza il software installato in tutti i dispositivi Mac OS X nei gruppi selezionati. Nel report sono elencati il nome del software (come ID bundle), il nome abbreviato (o descrittivo), la versione e il numero di dispositivi in cui è installato il software.|

#### <a name="to-create-a-report"></a>Per creare un report

1.  Nella console di amministrazione di Intune scegliere **Report**. Scegliere quindi il tipo di report che si vuole generare, come descritto nella tabella precedente.

2.  Nella pagina **Crea nuovo report** accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report software rilevato solo il software pubblicato da Microsoft.

3.  Scegliere **Visualizza report** per aprire il report in una nuova finestra.

Per ordinare il report in base a una delle colonne visualizzate, scegliere l'intestazione di colonna. Inoltre, alcuni report consentono di espandere gli elementi dell'elenco per visualizzare maggiori dettagli.

## <a name="more-report-actions"></a>Ulteriori azioni report
Inoltre, i report supportano le seguenti operazioni:

|Azione|Altre informazioni|
|----------|--------------------|
|**Stampa**|In un report aperto scegliere l'icona di stampa e seguire le istruzioni.|
|**Export**|In un report aperto scegliere l'icona di esportazione e seguire le istruzioni. È possibile esportare un report in formato HTML o con valori separati da virgola (CSV).|
|**Salva**|Nella pagina **Crea nuovo report** ogni utente può salvare fino a 100 report. Configurare i parametri del report in base ai propri requisiti e quindi scegliere **Salva**o **Salva con nome** se si vuole usare un altro nome.|
|**Carica**|Nella pagina **Crea nuovo report** scegliere **Carica** per recuperare i gruppi di parametri report precedentemente salvati.|
|**Eliminazione**|Nell'area di lavoro **Report** selezionare il tipo di report desiderato e scegliere **Carica**. Quindi, nell'elenco dei report, scegliere l'icona di eliminazione (x) accanto al report.|

### <a name="see-also"></a>Vedere anche
[Monitoraggio e report con Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


