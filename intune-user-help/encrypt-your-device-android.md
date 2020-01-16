---
title: Crittografare il dispositivo Android per Intune | Microsoft Docs
description: Procedura per attivare la crittografia dei dispositivi Android quando richiesto da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 2774a4f4c571b8a965c9ec47376a671df2dbf006
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856683"
---
# <a name="encrypting-your-android-device"></a>Crittografia del dispositivo Android

La crittografia del dispositivo protegge i file e le cartelle da accessi non autorizzati se il dispositivo viene smarrito o rubato. Dopo aver acceso la crittografia del dispositivo, solo gli utenti con la password o il pin corretti saranno in grado di accedere al dispositivo. 

Prima di poter accedere alle risorse scolastiche o di lavoro, è possibile che l'organizzazione richieda la crittografia del dispositivo Android. Alcuni dispositivi Android più recenti sono crittografati per impostazione predefinita.  

## <a name="turn-on-encryption"></a>Attivare la crittografia

Se Portale aziendale o l'app Microsoft Intune richiede di crittografare il dispositivo, completare i passaggi seguenti. 

> [!Note]
> Alcuni dispositivi Android da Huawei, vivo e OPPO non possono essere crittografati. Per altre informazioni, vedere [qui](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Impostare un blocco dello schermo del dispositivo.  
    a. Passare a **Impostazioni** > **Schermata di blocco e sicurezza** > **Tipo di blocco**.  
    b. Selezionare **pin**, **password**o **schema**.  
    c. Seguire le istruzioni visualizzate per configurare il blocco dello schermo.  

2. Tornare alla **schermata di blocco e alla sicurezza** e selezionare **avvio protetto**.
3. Scegliere **Richiedi PIN quando il dispositivo si attiva** > **OK**.
4. Immettere il PIN per confermare e crittografare il dispositivo.
5. Aprire l'app Portale aziendale o Microsoft Intune.
    * Utenti dell'app Portale aziendale: selezionare il dispositivo e toccare **Controlla le impostazioni del dispositivo**. 
    * Microsoft Intune utenti: è necessario attendere che la pagina venga aggiornata, ma, in questo caso, lo stato della crittografia deve essere modificato in conforme.  

I dispositivi che eseguono Android 4,4 e versioni precedenti potrebbero non avere l'opzione di **avvio protetto** . In tal caso, completare la procedura seguente per crittografare il dispositivo.

1. Passare a **impostazioni** > **sicurezza** > **Crittografa dispositivo**. Le etichette sullo schermo variano tra i dispositivi Android. Se l'opzione **Encrypt Device** non è visibile, archiviare:
    * **Archiviazione** > **crittografia di archiviazione**
    * **Archiviazione** > **schermata di blocco e sicurezza** > **altre impostazioni di sicurezza** 

2. Seguire le istruzioni visualizzate. Durante la crittografia il dispositivo potrebbe essere riavviato più volte.
3. Aprire l'app Portale aziendale o Microsoft Intune.
    * Utenti dell'app Portale aziendale: selezionare il dispositivo e toccare **Controlla le impostazioni del dispositivo**.  
    * Microsoft Intune utenti: è necessario attendere che la pagina venga aggiornata, ma, in questo caso, lo stato della crittografia deve essere modificato in conforme.

## <a name="troubleshoot"></a>Risoluzione dei problemi  
**Problema**: il dispositivo è già stato crittografato e

- Il pulsante di crittografia è disabilitato.
- Un messaggio informa che è necessario crittografare il dispositivo.
- Si verificano errori durante il tentativo di usare l'app Portale aziendale o Microsoft Intune.

**Possibili soluzioni**

- Verificare che il dispositivo sia carico e collegato.  
- Assicurarsi di aver impostato un PIN o una password nel dispositivo.  

Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.  
