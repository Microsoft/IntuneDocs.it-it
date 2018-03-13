---
title: Come aggiungere app di Windows Store a Microsoft Intune
titleSuffix: 
description: Informazioni sull'aggiunta di app Windows Store a Microsoft Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 815f780ef9f04870f19e75481ed74f0a1c3601f3
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Come aggiungere app di Windows Store a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. I passaggi seguenti consentono di aggiungere un'app Windows Store a Microsoft Intune.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**.
5. Scegliere **Aggiungi** sopra l'elenco.
6. Selezionare **Windows** nei tipi di **App Store** disponibili nell'elenco.
7. Scegliere **Informazioni sull'app** per configurare le informazioni sull'app.
8. Nel pannello **Informazioni sull'app** configurare le informazioni sull'app seguenti. A seconda dell'app scelta, alcuni dei valori in questo riquadro possono essere compilati automaticamente:
    - **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare. 
    - **Categoria** (facoltativo): selezionare una o più categorie di app oppure una categoria creata. L'aggiunta di queste informazioni consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che contiene informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che contiene informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio **Reparto risorse umane** (facoltativo).
    - **Note**: immettere tutte le note da associare a questa app (facoltativo).
    - **Carica l'icona**: Caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata con l'app quando gli utenti visitano il portale aziendale.
1. Fare clic su **OK** dopo aver immesso tutte le informazioni sull'app necessarie.
2. Fare clic su **Aggiungi** nel pannello **Aggiungi app**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

## <a name="manually-assign-windows-10-company-portal-app"></a>Assegnare manualmente l'app Portale aziendale di Windows 10
Gli utenti finali possono installare l'app Portale aziendale da Microsoft Store per gestire dispositivi e installare app. Se tuttavia per le specifiche esigenze aziendali è richiesta l'assegnazione dell'app Portale aziendale, è possibile assegnare manualmente l'app Portale aziendale di Windows 10 direttamente da Intune, anche se Intune non è integrato con Microsoft Store per le aziende.

 > [!NOTE]
 > Se si sceglie questa opzione, sarà necessario assegnare manualmente gli aggiornamenti ogni volta che viene rilasciato un aggiornamento dell'app.

1. Accedere al proprio account di [Microsoft Store per le aziende](https://www.microsoft.com/business-store) e acquisire la versione con **licenza offline** dell'app Portale aziendale.  
2. Dopo aver acquisito l'app, selezionarla nella pagina **Inventario**.  
3. Selezionare **Windows 10 all devices** (Windows 10 - tutti i dispositivi) come **Piattaforma**, quindi specificare l'opzione di **Architettura** appropriata ed eseguire il download. Per questa app non è necessario un file di licenza di app.

    ![Immagine dei dettagli del pacchetto per Windows 10 (tutti i dispositivi) e l'architettura x86](./media/Win10CP-all-devices.png)

4. Scaricare tutti i pacchetti inclusi in "Framework richiesti". Questa operazione deve essere eseguita per le architetture x86, x64 e ARM, per un totale di 9 pacchetti, come illustrato di seguito.

    ![Immagine dei file di dipendenza da scaricare](./media/Win10CP-dependent-files.png)

5. Prima di caricare l'app Portale aziendale in Intune, creare una cartella (ad esempio, C:&#92;Company Portal) con i pacchetti strutturati nel modo seguente:
  - Inserire il pacchetto dell'app Portale aziendale in C:\Company Portal. Creare anche una sottocartella Dependencies in questa posizione.  
  
    ![Immagine della cartella Dependencies salvata con il file APPXBUN](./media/Win10CP-Dependencies-save.png)

  - Inserire i nove pacchetti delle dipendenze nella cartella Dependencies. Se le dipendenze non vengono inserite in questo formato, Intune non sarà in grado di riconoscerle e caricarle durante il caricamento del pacchetto. Pertanto questa operazione avrà esito negativo con l'errore seguente: 

      ![Nella cartella dell'applicazione non è presente la dipendenza delle app Windows per questo programma di installazione software. È possibile continuare a creare e ad assegnare questa applicazione, ma non sarà possibile eseguirla fino a quando non diventa disponibile la dipendenza delle app Windows mancante.](./media/Win10CP-error-message.png)

6. Tornare a Intune e caricare l'app Portale aziendale come una nuova app. Assegnarla come app necessaria al gruppo di utenti di destinazione desiderato.  

Per altre informazioni sul modo in cui Intune gestisce le dipendenze per le app universali, vedere [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Distribuzione di un appxbundle con dipendenze tramite MDM di Microsoft Intune).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Come aggiornare l'app Portale aziendale sui dispositivi degli utenti se hanno già installato le app precedenti dallo Store?
Se gli utenti hanno già installato le app Portale aziendale di Windows 8.1 o Windows Phone 8.1 dallo Store, queste dovrebbero essere aggiornate automaticamente alla nuova versione senza alcun intervento da parte dell'amministratore o dell'utente. Se l'aggiornamento non viene eseguito, chiedere agli utenti di controllare se hanno abilitato gli aggiornamenti automatici per le app dello Store sui dispositivi.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare l'assegnazione dell'app Portale aziendale di Windows 8.1 impostando l'azione di assegnazione su "Disinstalla". Dopo aver impostato questa azione, l'app Portale aziendale di Windows 10 può essere assegnata usando una delle opzioni precedenti.  

Se è necessario trasferire localmente l'app e si è assegnata l'app Portale aziendale di Windows 8.1 senza firmarla con il certificato Symantec, per completare l'aggiornamento seguire i passaggi riportati nella sezione precedente per l'assegnazione diretta tramite Intune.

Se è necessario trasferire localmente l'app e si è firmata e assegnata l'app Portale aziendale di Windows 8.1 con il certificato di firma codice Symantec, seguire i passaggi illustrati nella sezione seguente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 firmata e trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare l'assegnazione esistente dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 impostando l'azione di assegnazione su "Disinstalla". Dopo aver impostato questa azione, l'app Portale aziendale di Windows 10 può essere assegnata normalmente.  

In caso contrario, è necessario aggiornare e firmare l'app Portale aziendale di Windows 10 per assicurarsi che il percorso di aggiornamento venga rispettato.  

Se l'app Portale aziendale di Windows 10 viene firmata e assegnata in questo modo, sarà necessario ripetere questa procedura per ogni nuovo aggiornamento dell'app disponibile nello Store. L'app non verrà aggiornata automaticamente in caso di aggiornamento dello Store.  

Ecco come firmare e assegnare l'app in questo modo:

1. Scaricare lo script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10 dall'indirizzo [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Per l'esecuzione di questo script è necessario che sia installato Windows 10 SDK nel computer host. Per scaricare Windows 10 SDK, visitare [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Scaricare l'app Portale aziendale di Windows 10 da Microsoft Store per le aziende, come descritto in precedenza.  
3. Eseguire lo script per firmare l'app Portale aziendale di Windows 10 con i parametri di input riportati nell'intestazione (descritti nella tabella seguente). Non è necessario passare le dipendenze allo script. Le dipendenze sono necessarie solo quando l'app viene caricata nella console di amministrazione di Intune.

|Parametro | Descrizione|
| ------------- | ------------- |
|InputWin10AppxBundle |Percorso in cui si trova il file appxbundle di origine. |
|OutputWin10AppxBundle |Percorso di output per il file appxbundle firmato.  Win81Appx: percorso in cui si trova il file (con estensione appx) dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1.|
|PfxFilePath |Percorso del file (con estensione pfx) del certificato di firma codice di Symantec Enterprise Mobile. |
|PfxPassword| Password del certificato di firma codice di Symantec Enterprise Mobile. |
|PublisherId |ID editore dell'azienda. Se assente, viene usato il campo 'Subject' del certificato di firma codice mobile aziendale Symantec .|
|SdkPath | Percorso della cartella radice di Windows 10 SDK. Questo argomento è facoltativo e l'impostazione predefinita è ${env:ProgramFiles(x86)}\Windows Kits\10.|
Al termine dell'esecuzione, lo script genererà la versione firmata dell'app Portale aziendale di Windows 10. Sarà quindi possibile assegnare la versione firmata dell'app come app line-of-business tramite Intune, in modo da aggiornare le versioni attualmente assegnate alla nuova app.  
