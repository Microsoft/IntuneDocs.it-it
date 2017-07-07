---
title: Aggiungere app per i PC Windows che eseguono il software client di Intune
description: Usare le informazioni in questo argomento per scoprire come aggiungere app a Intune prima di distribuirle.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: faf52c4166298d981532ee61c158f4a705c5a3da
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Aggiungere app per i PC Windows che eseguono il software client di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare le informazioni in questo argomento per informazioni su come aggiungere app a Intune prima di distribuirle.

> [!IMPORTANT]
> Le informazioni fornite in questo argomento semplificano l'aggiunta di app nei PC Windows gestiti usando il software client di Intune. Per aggiungere app per computer Windows e altri dispositivi mobili registrati, vedere [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

Per installare le app nei PC, è necessario che possano essere installate in modalità invisibile, senza l'intervento dell'utente. In caso contrario, l'installazione avrà esito negativo.


## <a name="add-the-app"></a>Aggiungere l'app
Usare l'Autore del software Intune per configurare le proprietà dell'app e caricarla nello spazio di archiviazione cloud usando la procedura seguente:

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App** &gt; **Aggiungi app** per avviare l'autore del software Intune.

    > [!TIP]
    > Per avviare questa funzionalità, può essere necessario immettere il nome utente e la password di Intune.

2.  Nella pagina **Installazione software** dell'autore, in **Selezionare il modo in cui questo software viene fornito ai dispositivi**, scegliere **Programma di installazione software** e quindi specificare quanto segue:

    - **Selezionare il tipo di file del programma di installazione software**. Indica il tipo di software da distribuire. Per un PC Windows scegliere **Windows Installer**.
    - **Specificare il percorso dei file di installazione software**. Immettere il percorso dei file di installazione o scegliere **Sfoglia** per selezionare il percorso da un elenco.
    - **Includi sottocartelle e file aggiuntivi dalla stessa cartella**. Alcuni programmi software che usano Windows Installer richiedono file di supporto. Tali file devono trovarsi nella stessa cartella dei file di installazione. Selezionare questa opzione se si vogliono distribuire anche i file di supporto.

    Ad esempio, se si vuole pubblicare un'app denominata Application.msi su Intune, la pagina avrà un aspetto simile al seguente: ![Pagina di installazione del software dell'autore](./media/publisher-for-pc.png)

   Questo tipo di installazione usa parte dello spazio di archiviazione cloud.

3.  Nella pagina **Descrizione software** configurare gli elementi seguenti.

    > [!NOTE]
    > In base al file del programma di installazione in uso, è possibile che alcuni valori siano stati immessi automaticamente o che non vengano visualizzati.

    - **Autore**. Immettere il nome dell'autore dell'app.
    - **Nome**. Immettere il nome dell'app che verrà visualizzato nel portale aziendale.<br />Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**. Immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **URL per le informazioni software** (facoltativo). Immettere l'URL di un sito Web che include informazioni sull'app. L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy** (facoltativo). Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app. L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Categoria** (facoltativo). Selezionare una delle categorie predefinite dell'app. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Icona** (facoltativo). Caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.

4.  Nella pagina **Requisiti** selezionare i requisiti che devono essere soddisfatti prima di poter installare l'app. È possibile scegliere tra:

    - **Architettura**. Indicare se l'app può essere installata in sistemi operativi a 32 bit o a 64 bit oppure in entrambi.
    - **Sistema operativo**. Selezionare il sistema operativo minimo in cui è possibile installare l'app.

5.  Nella pagina **Regole di rilevamento** è possibile configurare le regole per rilevare se l'app in fase di configurazione è già installata in un PC. In alternativa, è possibile usare le regole di rilevamento predefinite per sovrascrivere automaticamente eventuali versioni dell'app installate in precedenza. Questa opzione è per Windows Installer (solo file con estensione exe).

    È possibile configurare le regole seguenti:
    - **File esistente**. Specificare il percorso per il file da rilevare. È possibile cercare in **%ProgramFiles%** (per eseguire ricerche in **Programmi**\&lt;percorso&gt; e **Programmi (x86)**\&lt;percorso&gt;) nel PC o **%SystemDrive%** (per eseguire ricerche nell'unità radice del PC, in genere C).
    - **Codice prodotto MSI esistente**. Fare clic su **Sfoglia** per scegliere il file di Windows Installer (con estensione msi) da rilevare.
    - **Chiave del Registro di sistema esistente**. Specificare una chiave del Registro di sistema che inizia con **HKEY_LOCAL_MACHINE\**. Vengono eseguite ricerche nei percorso del Registro di sistema a 32 bit e a 64 bit. Se la chiave specificata esiste in uno dei due percorsi, la regola di rilevamento sarà soddisfatta.

    Se l'app soddisfa una delle regole configurate, non verrà installata.

6.  Solo per il tipo di file **Windows Installer** (con estensione msi ed exe): nella pagina **Argomenti della riga di comando** indicare se si vuole specificare argomenti facoltativi della riga di comando per il programma di installazione.
    I parametri seguenti vengono aggiunti automaticamente da Intune:
    - Per i file EXE, viene aggiunto il parametro **/install**.
    - Per i file MSI, viene aggiunto il parametro **/quiet**.
    Si noti che queste opzioni funzioneranno solo se l'autore del pacchetto dell'app ha abilitato le funzionalità corrispondenti.

7.  Solo per il tipo di file **Windows Installer** (solo con estensione exe): nella pagina **Codici restituiti** è possibile aggiungere nuovi codici di errore che vengono interpretati da Intune quando l'app viene installata in un PC Windows gestito.

    Per impostazione predefinita, Intune usa i codici restituiti standard del settore per segnalare un'installazione corretta o non riuscita di un pacchetto di app: **0** (Operazione riuscita) o **3010** (Operazione completata con riavvio). È anche possibile aggiungere codici restituiti personalizzati all'elenco. Se si specifica un elenco di codici restituiti e l'installazione dell'app restituisce un codice non incluso nell'elenco, questa situazione verrà interpretata come un errore.

8.  Nella pagina **Riepilogo** verificare le informazioni specificate. Al termine, scegliere **Carica**.

9. Scegliere **Chiudi** per completare la procedura.

L'app viene visualizzata nel nodo **App** dell'area di lavoro **App**.

## <a name="next-steps"></a>Passaggi successivi

Il passaggio successivo alla creazione di un'app è la distribuzione. Per altre informazioni, vedere [Distribuire le app con Microsoft Intune](deploy-apps.md).

Per altre informazioni sui suggerimenti e trucchi per distribuire il software in PC Windows, vedere il post di blog [Support Tip: Best Practices for Intune Software Distribution to PC’s](https://blogs.technet.microsoft.com/intunesupport/2016/06/13/support-tip-best-practices-for-intune-software-distribution-to-pcs/) (Suggerimento per il supporto: procedure consigliate per la distribuzione del software Intune nei PC).
