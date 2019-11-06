---
title: Trasferire localmente app per Windows e Windows Phone
titleSuffix: Microsoft Intune
description: Informazioni su come firmare le app line-of-business in modo da poter usare Intune per distribuirle.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7500000f8a34120e69c27ce01a6cfdb85f447abe
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414708"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Firmare le app line-of-business per poterle distribuire nei dispositivi Windows con Intune

L'amministratore di Intune ha la possibilità di distribuire app line-of-business (LOB) universali in dispositivi Windows 8.1 Desktop o Windows 10 Desktop e Mobile, inclusa l'app Portale aziendale. Per distribuire le app APPX in dispositivi Windows 8.1 Desktop o Windows 10 Desktop e Mobile, è possibile usare un certificato di firma codice di un'autorità di certificazione pubblica già considerata attendibile dai dispositivi Windows oppure usare la propria autorità di certificazione.

 > [!NOTE]
 > Windows 8.1 Desktop richiede un criterio enterprise per abilitare il sideload o l'uso delle chiavi di sideload (abilitate automaticamente per i dispositivi aggiunti a un dominio). Per altre informazioni, vedere i [requisiti del sideload in Windows 8](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Sideload in Windows 10

In Windows 10 il sideload è diverso rispetto alle versioni precedenti di Windows:

- È possibile sbloccare un dispositivo per il sideload usando un criterio enterprise. Intune offre un criterio di configurazione del dispositivo denominato "installazione di app attendibile". L'impostazione del criterio su <allow> è tutto ciò che serve ai dispositivi che già considerano attendibile il certificato usato per firmare l'app APPX.

- I certificati Symantec Phone e le chiavi della licenza per la funzionalità di sideload non sono obbligatori. Tuttavia, se un'autorità di certificazione locale non è disponibile, può essere necessario ottenere un certificato di firma del codice da un'autorità di certificazione pubblica. Per altre informazioni, vedere l'[introduzione alla firma del codice](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Firma del codice dell'app

Il primo passaggio è firmare il codice del pacchetto APPX. Per i dettagli, vedere l'articolo sulla [firma del pacchetto dell'app con SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Caricare l'app

Successivamente, è necessario caricare il file APPX firmato. Per maggiori dettagli, vedere [Aggiungere un'app line-of-business per Windows a Microsoft Intune](lob-apps-windows.md).

Se si distribuisce l'app come richiesto agli utenti o ai dispositivi, l'app Portale aziendale Intune non è necessaria. Tuttavia, se si distribuisce l'app come disponibile per gli utenti, gli utenti potranno usare l'app Portale aziendale dal Microsoft Store pubblico, usare l'app Portale aziendale dal Microsoft Store privato per le aziende oppure firmare e distribuire manualmente l'app Portale aziendale Intune.

### <a name="upload-the-code-signing-certificate"></a>Caricare il certificato di firma codice

Se il dispositivo Windows 10 non considera attendibile l'autorità di certificazione, dopo aver firmato il pacchetto APPX e averlo caricato nel servizio Intune, è necessario caricare il certificato di firma codice nel portale di Intune:

1. Fare clic su App client
2. Fare clic su Certificati Windows Enterprise
3. Scegliere "Selezionare un file" in Certificato di firma codice
4. Selezionare il file CER e fare clic su Carica

A questo punto, qualsiasi dispositivo Windows 10 Desktop e Mobile con una distribuzione APPX eseguita dal servizio Intune scaricherà automaticamente il certificato enterprise corrispondente e sarà possibile avviare l'applicazione dopo l'installazione.

Intune distribuisce solo il file CER più recente che è stato caricato. Se più file APPX sono stati creati da altri sviluppatori che non sono associati alla propria organizzazione, sarà necessario richiedere agli sviluppatori i file APPX non firmati in modo da firmarli con il proprio certificato oppure fare in modo che gli sviluppatori abbiano il certificato di firma codice usato dall'organizzazione.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Come rinnovare il certificato di firma codice aziendale Symantec

Il certificato usato per la distribuzione delle app per dispositivi mobili di Windows Phone 8.1 è stato sospeso il 28 febbraio 2019 e non è più disponibile per il rinnovo da Symantec. Se si esegue la distribuzione in Windows 10 Mobile, è possibile continuare a usare i certificati di firma codice di Symantec Desktop Enterprise seguendo le istruzioni per il [sideload in Windows 10](app-sideload-windows.md#windows-10-sideloading).

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Come installare il certificato aggiornato per le app line-of-business (LOB)

Windows Phone 8.1

Il servizio Intune non è più in grado di distribuire le app LOB per questa piattaforma dopo la scadenza del certificato di firma codice di Symantec Mobile Enterprise. Sarà comunque possibile il sideload dei file XAP/APPX senza firma usando una scheda SD o scaricando il file nel dispositivo. Per altre informazioni, vedere la [procedura di installazione dei file XAP in Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 Desktop/Windows 10 Desktop e Mobile

Se il periodo di certificazione è scaduto, è possibile che i file APPX non vengano avviati. È necessario ottenere un nuovo file CER e seguire le istruzioni per firmare il codice per ogni file APPX distribuito e ricaricare tutti i file APPX e il file CER aggiornato nella sezione Certificati Windows Enterprise del portale di Intune

## <a name="manually-deploy-windows-10-company-portal-app"></a>Distribuire manualmente l'app Portale aziendale di Windows 10

Se non si vuole concedere l'accesso al Microsoft Store, è possibile distribuire manualmente l'app Portale aziendale di Windows 10 direttamente da Intune, anche se non si è integrato Intune con Microsoft Store per le aziende. In alternativa, se Intune è integrato, è possibile distribuire l'app Portale aziendale seguendo la [procedura di distribuzione delle app con Microsoft Store per le aziende](store-apps-windows.md).

 > [!NOTE]
 > Se si sceglie questa opzione, sarà necessario distribuire manualmente gli aggiornamenti ogni volta che verrà rilasciato un aggiornamento dell'app.

1. Accedere al proprio account di [Microsoft Store per le aziende](https://www.microsoft.com/business-store) e acquisire la versione con **licenza offline** dell'app Portale aziendale.  
2. Dopo aver acquisito l'app, selezionarla nella pagina **Inventario**.  
3. Selezionare **Windows 10 all devices** (Windows 10 - tutti i dispositivi) come **Piattaforma**, quindi specificare l'opzione di **Architettura** appropriata ed eseguire il download. Per questa app non è necessario un file di licenza di app.
   ![Immagine dei dettagli del pacchetto di Windows 10 X86 per il download](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Scaricare tutti i pacchetti inclusi in "Framework richiesti". Questa operazione deve essere eseguita per le architetture x86, x64 e ARM, per un totale di 9 pacchetti, come illustrato di seguito.

   ![Immagine dei file di dipendenza da scaricare ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Prima di caricare l'app Portale aziendale in Intune, creare una cartella (ad esempio, C:&#92;Company Portal) con i pacchetti strutturati nel modo seguente:
   1. Inserire il pacchetto dell'app Portale aziendale in C:\Company Portal. Creare anche una sottocartella Dependencies in questa posizione.  
      ![Immagine della cartella Dependencies salvata con il file APPXBUN](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Inserire i nove pacchetti delle dipendenze nella cartella Dependencies.  
      Se le dipendenze non vengono inserite in questo formato, Intune non sarà in grado di riconoscerle e caricarle durante il caricamento del pacchetto. Pertanto questa operazione avrà esito negativo e restituirà l'errore seguente.  
      ![Messaggio di errore: è necessario specificare la dipendenza delle app di Windows.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Tornare a Intune e caricare l'app Portale aziendale come una nuova app. Distribuirla come app necessaria al gruppo di utenti di destinazione desiderato.  

Per altre informazioni sul modo in cui Intune gestisce le dipendenze per le app universali, vedere [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Distribuzione di un appxbundle con dipendenze tramite MDM di Microsoft Intune).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Come aggiornare l'app Portale aziendale sui dispositivi degli utenti se hanno già installato le app precedenti dallo Store?

Se gli utenti hanno già installato le app Portale aziendale di Windows 8.1 o Windows Phone 8.1 dallo Store, queste dovrebbero essere aggiornate automaticamente alla nuova versione senza alcun intervento da parte dell'amministratore o dell'utente. Se l'aggiornamento non viene eseguito, chiedere agli utenti di controllare se hanno abilitato gli aggiornamenti automatici per le app dello Store sui dispositivi.

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 trasferita localmente all'app Portale aziendale di Windows 10?

Il percorso di migrazione consigliato consiste nell'eliminare la distribuzione dell'app Portale aziendale di Windows 8.1 impostando l'azione di distribuzione su "Disinstalla". Al termine di questa operazione, l'app Portale aziendale di Windows 10 può essere distribuita usando una delle opzioni precedenti.  

Se è necessario trasferire localmente l'app e si è distribuita l'app Portale aziendale di Windows 8.1 senza firmarla con il certificato Symantec, per completare l'aggiornamento seguire i passaggi riportati nella sezione relativa alla distribuzione diretta tramite Intune.

Se è necessario trasferire localmente l'app e si è firmata e distribuita l'app Portale aziendale di Windows 8.1 con il certificato di firma codice Symantec, seguire i passaggi illustrati nella sezione seguente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 firmata e trasferita localmente all'app Portale aziendale di Windows 10?

Il percorso di migrazione consigliato consiste nell'eliminare la distribuzione esistente dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 impostando l'azione di distribuzione su "Disinstalla". Al termine di questa operazione, l'app Portale aziendale di Windows 10 può essere distribuita normalmente.  

In caso contrario, è necessario aggiornare e firmare l'app Portale aziendale di Windows 10 per assicurarsi che il percorso di aggiornamento venga rispettato.  

Se l'app Portale aziendale di Windows 10 viene firmata e distribuita in questo modo, sarà necessario ripetere questa procedura per ogni nuovo aggiornamento dell'app disponibile nello Store. L'app non verrà aggiornata automaticamente in caso di aggiornamento dello Store.  

Ecco come firmare e distribuire l'app in questo modo:

1. Scaricare lo script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10 dall'indirizzo [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Per l'esecuzione di questo script è necessario che sia installato Windows 10 SDK nel computer host. Per scaricare Windows SDK per Windows 10, visitare [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Scaricare l'app Portale aziendale di Windows 10 da Microsoft Store per le aziende, come descritto in precedenza.  
3. Eseguire lo script per firmare l'app Portale aziendale di Windows 10 con i parametri di input riportati nell'intestazione (descritti nella tabella seguente). Non è necessario passare le dipendenze allo script. Le dipendenze sono necessarie solo quando l'app viene caricata nella console di amministrazione di Intune.

|       Parametro       |                                                                    Descrizione                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Percorso in cui si trova il file appxbundle di origine.                                              |
| OutputWin10AppxBundle |                                                  Percorso di output per il file appxbundle firmato.                                                  |
|       Win81Appx       |                          Percorso in cui si trova il file (con estensione appx) dell'app Portale aziendale per Windows 8.1 o Windows Phone 8.1.                           |
|      PfxFilePath      |                                   Percorso del file (con estensione pfx) del certificato di firma codice di Symantec Enterprise Mobile.                                    |
|      PfxPassword      |                                     Password del certificato di firma codice di Symantec Enterprise Mobile.                                      |
|      PublisherId      |      ID editore dell'azienda. Se assente, viene usato il campo 'Subject' del certificato di firma codice mobile aziendale Symantec .       |
|        SdkPath        | Percorso della cartella radice di Windows 10 SDK. Questo argomento è facoltativo e l'impostazione predefinita è ${env:ProgramFiles(x86)}\Windows Kits\10. |

Al termine dell'esecuzione, lo script genererà la versione firmata dell'app Portale aziendale di Windows 10. Sarà quindi possibile distribuire la versione firmata dell'app come app line-of-business tramite Intune, in modo da aggiornare le versioni attualmente distribuite alla nuova app.  
