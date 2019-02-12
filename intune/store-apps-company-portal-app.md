---
title: Aggiungere manualmente l'app Portale aziendale di Windows 10
titleSuffix: Microsoft Intune
description: Informazioni su come il personale dell'azienda può aggiungere manualmente l'app Portale aziendale di Windows 10 nei propri PC da Microsoft Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6f148c98c31f53626d78a91aacedb4c92571109
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851650"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Aggiungere manualmente l'app Portale aziendale di Windows 10 usando Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per gestire dispositivi e installare app, gli utenti possono installare l'app Portale aziendale da Microsoft Store. Se per le specifiche esigenze aziendali è richiesta l'assegnazione dell'app Portale aziendale, è comunque possibile assegnare manualmente l'app Portale aziendale di Windows 10 direttamente da Intune, anche se Intune non è integrato con Windows Store per le aziende.

 > [!NOTE]
 > Per l'opzione descritta in questo articolo è necessario che gli aggiornamenti manuali siano assegnati ogni volta che viene rilasciato un aggiornamento dell'app.

## <a name="configure-settings-to-show-offline-apps"></a>Configurare le impostazioni per visualizzare le app offline
1. Accedere a [Microsoft Store per le aziende](https://www.microsoft.com/business-store) con l'account amministratore.
2. Selezionare la scheda **Manage** (Gestisci) nella parte superiore della finestra.
3. Nel riquadro di sinistra selezionare **Impostazioni**.
4. Impostare **Show offline apps** (Mostra app offline) in **Shopping experience** (Esperienza di acquisto) su **On** (Attivo).  
    Saranno visualizzate le app con licenza offline.

## <a name="download-the-offline-company-portal-app"></a>Scaricare l'app Portale aziendale offline
1. Cercare e selezionare l'app **Portale aziendale**.
2. Impostare il **Tipo di licenza** su **Offline**.
3. Selezionare **Scarica l'app** per acquisire e aggiungere l'app Portale aziendale offline all'inventario.
4. Selezionare **Gestisci** nella pagina dell'app **Portale aziendale**.
5. Selezionare **Windows 10 all devices** (Windows 10 (tutti i dispositivi)) come **Piattaforma**, quindi scegliere un valore appropriato per **Versione minima**, **Architettura** e **Download app metadata**. 
6. Fare clic su **Download** per salvare il file nel computer locale.

    ![Sono selezionati dispositivi Windows 10 la cui architettura corrisponde a X86](./media/Win10CP-all-devices.png)

7. Scaricare tutti i pacchetti in "Framework richiesti" selezionando **Download**.  
    Questa azione deve essere completata per le architetture x86, x64 e ARM, per un totale di 12 pacchetti.
8. Prima di caricare l'app Portale aziendale in Intune, creare una cartella (ad esempio, C:\Company Portal) con i pacchetti strutturati nel modo seguente:
   - Inserire il pacchetto dell'app Portale aziendale in C:\Company Portal. Creare anche una sottocartella *Dependencies* in questo percorso.  

     ![Cartella Dependencies salvata con il file APPXBUN](./media/Win10CP-Dependencies-save.png)

   - Inserire i pacchetti delle dipendenze nella cartella *Dependencies*. 

     > [!NOTE]
     > Se le dipendenze non vengono inserite nel formato corretto, Intune non riconoscerà e caricherà i file durante il caricamento del pacchetto. Il caricamento non verrà quindi eseguito e verrà visualizzato un errore.

9. Nel portale di Azure in Microsoft Intune caricare l'app Portale aziendale come nuova app. 
10. Assegnare l'app Portale aziendale come app obbligatoria agli utenti di destinazione selezionati.  

Per altre informazioni su come Intune gestisce le dipendenze per le app universali, vedere [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Distribuzione di un appxbundle con dipendenze tramite MDM di Microsoft Intune).  

## <a name="frequently-asked-questions"></a>Domande frequenti 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Come aggiornare l'app Portale aziendale nei dispositivi degli utenti se hanno già installato le app precedenti dallo Store?
Se gli utenti hanno già installato le app Portale aziendale di Windows 8.1 o Windows Phone 8.1 da Microsoft Store, queste dovrebbero essere aggiornate automaticamente all'ultima versione senza alcun intervento da parte dell'amministratore o dell'utente. Se l'aggiornamento non viene eseguito, chiedere agli utenti di controllare se hanno abilitato gli aggiornamenti automatici per le app dello Store nei dispositivi.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare l'assegnazione dell'app Portale aziendale di Windows 8.1 impostando l'azione di assegnazione su **Disinstalla**. Dopo aver selezionato questa impostazione, è possibile assegnare l'app Portale aziendale di Windows 10 usando una delle opzioni descritte in precedenza.  

Se è necessario trasferire localmente l'app e si è assegnata l'app Portale aziendale di Windows 8.1 senza firmarla con il certificato Symantec, completare l'aggiornamento seguendo i passaggi riportati nella sezione precedente di questo articolo.

Se è necessario trasferire localmente l'app e si è firmata e assegnata l'app Portale aziendale di Windows 8.1 con il certificato di firma codice Symantec, seguire la procedura descritta nella prossima sezione.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 firmata e trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare l'assegnazione esistente dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 impostando l'azione di assegnazione su **Disinstalla**. Dopo aver selezionato questa impostazione, è possibile assegnare l'app Portale aziendale di Windows 10 normalmente.  

In caso contrario, è necessario aggiornare e firmare l'app Portale aziendale di Windows 10 per assicurarsi che il percorso di aggiornamento venga rispettato.  

Se l'app Portale aziendale di Windows 10 viene firmata e assegnata in questo modo, sarà necessario ripetere questa procedura per ogni nuovo aggiornamento dell'app disponibile nello Store. L'app non viene aggiornata automaticamente in caso di aggiornamento dello Store.  

Ecco come firmare e assegnare l'app in questo modo:

1. Scaricare lo [script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10](https://aka.ms/win10cpscript).  
    Per l'esecuzione di questo script è necessario che sia installato Windows 10 SDK nel computer host. [Scaricare Windows SDK per Windows 10](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Scaricare l'app Portale aziendale di Windows 10 da Microsoft Store per le aziende, come descritto in precedenza.  
3. Per firmare l'app Portale aziendale di Windows 10, eseguire lo script con i parametri di input riportati nel dettaglio nell'intestazione, come descritto nella tabella seguente.  
    Non è necessario passare le dipendenze allo script. Le dipendenze sono necessarie solo quando l'app viene caricata nella console di amministrazione di Intune.

| Parametro |  Descrizione  |
|---|---|
| InputWin10AppxBundle  |  Percorso del file appxbundle di origine. |
| OutputWin10AppxBundle | Percorso di output per il file appxbundle firmato. 
| Win81Appx  | Percorso del file con estensione appx dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1. |
| PfxFilePath  |  Percorso del file (con estensione pfx) del certificato di firma codice di Symantec Enterprise Mobile.  |
| PfxPassword  | Password del certificato di firma codice di Symantec Enterprise Mobile. |
| PublisherId | ID editore dell'azienda. Se assente, viene usato il campo Subject del certificato di firma codice mobile aziendale Symantec. |
| SdkPath | Percorso della cartella radice di Windows 10 SDK. Questo argomento è facoltativo e l'impostazione predefinita è ${env:ProgramFiles(x86)}\Windows Kits\10.  |

Al termine dell'esecuzione, lo script genera la versione firmata dell'app Portale aziendale di Windows 10. È quindi possibile assegnare la versione firmata dell'app come app line-of-business (LOB) tramite Intune, in modo da aggiornare le versioni attualmente assegnate alla nuova app.  

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)

