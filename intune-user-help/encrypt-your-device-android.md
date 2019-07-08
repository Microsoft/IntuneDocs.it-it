---
title: Crittografare il dispositivo Android per Intune | Microsoft Docs
description: Procedura per attivare la crittografia del dispositivo Android quando richiesti da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545250"
---
# <a name="encrypting-your-android-device"></a>Crittografia del dispositivo Android

La crittografia del dispositivo consente di proteggere file e cartelle da accesso non autorizzato se il dispositivo viene smarrito o rubato. Dopo avere attivato la crittografia del dispositivo, solo gli utenti con la password corrette o il pin sarà in grado di accedere al dispositivo. 

Prima di poter accedere alle risorse aziendali o dell'istituto di istruzione, l'organizzazione potrebbe essere necessario crittografare il dispositivo Android. Alcuni dispositivi Android più recenti vengono crittografati per impostazione predefinita, out-of-the-box.  

## <a name="turn-on-encryption"></a>Attivare la crittografia

Se l'App portale aziendale o dell'app di Microsoft Intune richiede di crittografare il dispositivo, completare i passaggi seguenti. 

> [!Note]
> Alcuni dispositivi Android da Huawei Vivo e OPPO non possono essere crittografate. Per altre informazioni, vedere [qui](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Impostare un blocco dello schermo del dispositivo.  
    a. Passare a **Impostazioni** > **Schermata di blocco e sicurezza** > **Tipo di blocco**.  
    b. Selezionare uno **PIN**, **Password**, o **Pattern**.  
    c. Seguire le istruzioni visualizzate per configurare il blocco dello schermo.  

2. Tornare alla **schermata di blocco e sicurezza** e selezionare **Secure startup**.
3. Scegli **Richiedi PIN quando si attiva dispositivo** > **OK**.
4. Immettere il PIN per confermare e crittografare il dispositivo.
5. Aprire l'app portale aziendale o Microsoft Intune.
    * Utenti del portale aziendale: selezionare il dispositivo e toccare **Controlla le impostazioni del dispositivo**. 
    * Gli utenti di Microsoft Intune: sarà necessario attendere gli aggiornamenti di pagina, ma in questo caso, il tuo stato di crittografia deve cambiare a conforme.  

Dispositivi che eseguono Android 4.4 e versioni precedenti potrebbero non avere le **Secure startup** opzione. In tal caso, completare la procedura seguente per crittografare il dispositivo.

1. Passare a **le impostazioni** > **sicurezza** > **crittografia dispositivo**. Etichette visualizzate variano tra i dispositivi Android. Se non viene visualizzato il **Esegui crittografia dispositivo** opzione, l'archiviazione:
    * **Archiviazione** > **crittografia di archiviazione**
    * **Archiviazione** > **schermata di blocco e sicurezza** > **altre impostazioni di sicurezza** 

2. Seguire le istruzioni visualizzate. Durante la crittografia il dispositivo potrebbe essere riavviato più volte.
3. Aprire l'app portale aziendale o Microsoft Intune.
    * Utenti del portale aziendale: selezionare il dispositivo e toccare **Controlla le impostazioni del dispositivo**.  
    * Gli utenti di Microsoft Intune: sarà necessario attendere gli aggiornamenti di pagina, ma in questo caso, il tuo stato di crittografia deve cambiare a conforme.

## <a name="troubleshoot"></a>Risoluzione dei problemi  
**Problema**: già stato crittografato il dispositivo e

- Il pulsante di crittografia è disabilitato.
- Un messaggio informa che è necessario crittografare il dispositivo.
- Si verificano errori durante il tentativo di usare l'app portale aziendale o Microsoft Intune.

**Possibili soluzioni**

- Verificare che il dispositivo sia carico e collegato.  
- Assicurarsi di aver impostato un PIN o una password nel dispositivo.  

Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.  
