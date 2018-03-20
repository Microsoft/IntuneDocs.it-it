---
title: Aggiungere manualmente l'app Portale aziendale di Windows 10
titleSuffix: Microsoft Intune
description: Informazioni su come aggiungere manualmente l'app Portale aziendale di Windows 10.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06ed9395d06e2d64edcedcaadfe819ad03f1d495
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Aggiungere manualmente l'app Portale aziendale di Windows 10 usando Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Gli utenti finali possono installare l'app Portale aziendale da Microsoft Store per gestire dispositivi e installare app. Se tuttavia per le specifiche esigenze aziendali è richiesta l'assegnazione dell'app Portale aziendale, è possibile assegnare manualmente l'app Portale aziendale di Windows 10 direttamente da Intune, anche se Intune non è integrato con Microsoft Store per le aziende.

 > [!NOTE]
 > Se si sceglie questa opzione, sarà necessario assegnare manualmente gli aggiornamenti ogni volta che viene rilasciato un aggiornamento dell'app.

## <a name="configure-settings-to-show-offline-apps"></a>Configurare le impostazioni per visualizzare le app offline
1. Passare a [Microsoft Store per le aziende](https://www.microsoft.com/business-store) e assicurarsi di aver eseguito l'accesso con l'account di amministratore.
2. Selezionare la scheda **Manage** (Gestisci) nella parte superiore della finestra.
3. Selezionare **Settings** (Impostazioni) nella colonna di spostamento a sinistra.
4. Impostare **Show offline apps** (Mostra app offline) nella sezione **Shopping experience** (Esperienza di acquisto) su **On** (Attivo). Le app offline con licenza verranno visualizzate in Microsoft Store per le aziende.

## <a name="download-the-offline-company-portal-app"></a>Scaricare l'app Portale aziendale offline
1. Cercare e selezionare l'app **Portale aziendale**.
2. Impostare il **Tipo di licenza** su **Offline**.
3. Fare clic su **Scarica l'app** per acquisire e aggiungere l'app Portale aziendale offline all'inventario.
4. Fare clic su **Gestisci** nella pagina dell'app **Portale aziendale**.
5. Selezionare **Windows 10 Tutti i dispositivi** come **Piattaforma**, quindi selezionare la **Versione minima** appropriata, **Architettura** e scaricare i valori dei metadati dell'app**. 
6. Fare clic su **Download** per salvare il file nel computer locale.

    ![Immagine dei dettagli del pacchetto per Windows 10 (tutti i dispositivi) e l'architettura x86](./media/Win10CP-all-devices.png)

7. Scaricare tutti i pacchetti inclusi in "Framework richiesti". Questa operazione deve essere eseguita per le architetture x86, x64 e ARM, per un totale di 12 pacchetti.
8. Prima di caricare l'app Portale aziendale in Intune, creare una cartella (ad esempio, C:&#92;Company Portal) con i pacchetti strutturati nel modo seguente:
  - Inserire il pacchetto dell'app Portale aziendale in C:\Company Portal. Creare anche una sottocartella Dependencies in questa posizione.  

    ![Immagine della cartella Dependencies salvata con il file APPXBUN](./media/Win10CP-Dependencies-save.png)

  - Inserire i pacchetti delle dipendenze nella cartella *Dependencies*. 

     > [!NOTE]
     > Se le dipendenze non vengono inserite nel formato corretto, Intune non sarà in grado di riconoscere e caricare i file durante il caricamento del pacchetto. Pertanto il caricamento non verrà eseguito e verrà visualizzato un errore.

9. Tornare a Microsoft Intune nel portale di Azure.
10. Caricare l'app Portale aziendale come nuova app. Assegnarla come app necessaria al gruppo di utenti di destinazione desiderato.  

Per altre informazioni sul modo in cui Intune gestisce le dipendenze per le app universali, vedere [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Distribuzione di un appxbundle con dipendenze tramite MDM di Microsoft Intune).  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Come aggiornare l'app Portale aziendale sui dispositivi degli utenti se hanno già installato le app precedenti dallo Store?
Se gli utenti hanno già installato le app Portale aziendale di Windows 8.1 o Windows Phone 8.1 dallo Store, queste dovrebbero essere aggiornate automaticamente alla nuova versione senza alcun intervento da parte dell'amministratore o dell'utente. Se l'aggiornamento non viene eseguito, chiedere agli utenti di controllare se hanno abilitato gli aggiornamenti automatici per le app dello Store sui dispositivi.   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare l'assegnazione dell'app Portale aziendale di Windows 8.1 impostando l'azione di assegnazione su "Disinstalla". Dopo aver impostato questa azione, l'app Portale aziendale di Windows 10 può essere assegnata usando una delle opzioni precedenti.  

Se è necessario trasferire localmente l'app e si è assegnata l'app Portale aziendale di Windows 8.1 senza firmarla con il certificato Symantec, per completare l'aggiornamento seguire i passaggi riportati nella sezione precedente per l'assegnazione diretta tramite Intune.

Se è necessario trasferire localmente l'app e si è firmata e assegnata l'app Portale aziendale di Windows 8.1 con il certificato di firma codice Symantec, seguire i passaggi illustrati nella sezione seguente.  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 firmata e trasferita localmente all'app Portale aziendale di Windows 10?
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

## <a name="next-steps"></a>Passaggi successivi

- [Come assegnare app ai gruppi](apps-deploy.md)

