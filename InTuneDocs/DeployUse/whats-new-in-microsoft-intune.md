---
# required metadata

title: Novità | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novità di Microsoft Intune

## Aprile 2016
Tutte queste funzionalità sono supportate anche per i clienti ibridi (Configuration Manager con Intune).
### Gestione delle app
- **Conformità utente MAM.**
È ora possibile visualizzare lo [stato](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) dei criteri di gestione delle applicazioni per ogni utente del tenant Azure Active Directory (AAD). Sono inclusi:
   - Dispositivi
   - App sul dispositivo

   Valori di stato:

   **Archiviato**: indica che il criterio è stato distribuito all'utente, l'app è stata usata nel contesto di lavoro e ha ricevuto correttamente i criteri.

    **Non archiviato**: indica che il criterio è stato distribuito all'utente, ma da quel momento l'app non è mai stata usata nel contesto di lavoro.


- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (Android).**
È disponibile una nuova impostazione per la [gestione delle applicazioni per dispositivi mobili](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi Android. Quando l'impostazione è abilitata, le applicazioni di destinazione non possono più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, le applicazioni di destinazione possono salvare i contatti nella rubrica nativa. Quando [si cancella un dispositivo o un'app da remoto](wipe-managed-company-app-data-with-Microsoft-Intune.md), tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata inizialmente dall'applicazione Outlook sui dispositivi Android.

### Gestione dei dispositivi
- **Identificazione del numero di telefono per i dispositivi aziendali.** I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, per esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con **** mostrando solo le ultime 4 cifre.


### Aggiornamenti del Portale aziendale
**App del Portale aziendale Android**
Gli utenti che non hanno registrato il loro dispositivo in Intune e che non hanno il certificato corretto installato non potranno accedere all'app del Portale aziendale Android e vedranno il messaggio “Non è possibile accedere. Manca un certificato necessario per il dispositivo.” Il messaggio include il collegamento “Risoluzione del problema” che gli utenti possono usare per vedere le istruzioni per l'installazione del certificato. Per i passaggi che gli utenti finali devono eseguire per risolvere il problema, vedere [Manca un certificato necessario per il dispositivo](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**App del portale aziendale iOS**
È stato aggiunto il supporto per l'azione di scorrimento per aggiornare il contenuto sulla schermata home, che include le app e i dispositivi elencati e le informazioni di contatto IT. L'azione di scorrimento per l'aggiornamento non controlla la conformità o le informazioni sui criteri, cosa che si può fare selezionando il riquadro per il dispositivo corrente e toccando il pulsante **Sincronizza**.

**App del Portale aziendale di Windows 10 Mobile e Windows Phone 8.1**
Durante l'installazione delle applicazioni line of business ora gli utenti finali vedranno un'esperienza di installazione delle app migliorata. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo manualmente per velocizzare l'installazione delle app](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sito Web del portale aziendale**
Durante l'installazione delle app line of business, gli utenti di Windows 10 Mobile e Windows Phone 8.1 vedranno ora i seguenti stati nuovi, che forniscono maggiori dettagli sullo stato della loro installazione:

* **In attesa della sincronizzazione del dispositivo**: l'utente ha toccato “Installa” e il dispositivo ora tenta di sincronizzarsi con l'infrastruttura Intune. La sincronizzazione è necessaria per poter completare l'installazione. Il messaggio "In attesa della sincronizzazione del dispositivo" è anche un collegamento che gli utenti possono toccare per vedere le [istruzioni](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) per sincronizzare manualmente il dispositivo con Intune, se il processo di sincronizzazione impiega troppo tempo o si blocca.
* **Download in corso**: la richiesta di download dell'utente è in fase di elaborazione e il dispositivo sta scaricando e installando l'app.

Prima dell'aggiunta di questi stati, gli utenti potevano essere confusi se l'installazione di un'app impiegava molto tempo, poiché vedevano solo lo stato "Installazione in corso", che poteva rimanere visualizzata sullo schermo per ore. Grazie all'aggiunta dei nuovi stati gli utenti, invece di chiamare il supporto, possono ora toccare il collegamento "In attesa della sincronizzazione del dispositivo" e seguire le istruzioni per forzare la ripresa del processo di sincronizzazione.

### Sviluppi futuri

**Modifiche agli account dei manager di registrazione dispositivi.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app del Portale aziendale. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.  Intune inoltre deprecherà l'uso degli account manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi.  Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile.

Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)..


## Versioni precedenti di Intune
Per vedere cosa è stato rilasciato in Intune negli ultimi sei mesi, leggere l'articolo [Versioni precedenti di Intune](previous-intune-releases.md).



### Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)


<!--HONumber=May16_HO1-->


