---
title: Come proteggere il dispositivo Android con la crittografia | Microsoft Docs
description: Proteggere il dispositivo Android
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
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
ms.openlocfilehash: cea43f2bf3b13bf0463e1dedd6c20a1587336d5b
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
ms.locfileid: "30754995"
---
# <a name="how-to-protect-your-android-device-using-encryption"></a>Come proteggere il dispositivo Android usando la crittografia

Quando si crittografa un dispositivo, si esegue il wrapping delle informazioni in esso contenute in un livello di codice protettivo che impedisce l'accesso agli utenti non autorizzati. Come passo aggiuntivo per assicurarsi che le informazioni siano protette, l'organizzazione richiede di crittografare il dispositivo Android prima di accedere a file, posta elettronica o dati aziendali.

> [!Note]
> Alcuni dispositivi Android, inclusi alcuni modelli realizzati da Huawei e tutti i dispositivi Vivo e OPPO, non possono essere crittografati. Per altre informazioni, vedere [qui](your-device-appears-encrypted-but-cp-says-otherwise-android.md).

Un telefono di cui si annulla la registrazione rimarrà crittografato.

1.  Assicurarsi che per il dispositivo sia stato impostato un PIN o una password per il blocco dello schermo.

2.  In **Impostazioni** scegliere **Sicurezza** > **Esegui crittografia dispositivo**.
    In alcuni telefoni è necessario fare clic su **Memoria** > **Crittografia memoria** o **Memoria** > **Schermata di blocco e sicurezza** > **Altre impostazioni di sicurezza** per trovare l'opzione "Crittografia".

3.  Seguire le istruzioni visualizzate. Durante la crittografia il dispositivo potrebbe essere riavviato più volte.

### <a name="what-to-do-if-you-have-issues"></a>Operazioni da eseguire in caso di problemi
**Problema**: il dispositivo è già stato crittografato e si verifica uno dei problemi seguenti:

- Il pulsante di crittografia è disabilitato.
- Un messaggio informa che è necessario crittografare il dispositivo.
- Si verificano errori quando si prova a usare l'app Portale aziendale.

**Possibili soluzioni**

- Verificare che il dispositivo sia carico e collegato.
- Assicurarsi di aver impostato un PIN o una password nel dispositivo.
- Se il PIN o la password sono già impostati nel dispositivo, provare i passaggi seguenti che il personale del supporto potrebbe richiedere per rendere più sicuro il dispositivo. I nomi dei menu visualizzati potrebbero essere leggermente diversi da quelli riportati nelle procedure, a seconda del tipo di dispositivo Android in uso.

    1. Passare a **Impostazioni** > **Schermata di blocco e sicurezza** > **Blocco schermo**. Confermare il PIN o la password corrente.

    2. In **Selezione blocco schermo** scegliere il tipo di blocco schermo da usare. 

    3. Dopo aver scelto il blocco dello schermo, tornare a **Schermata di blocco e sicurezza** e selezionare **Avvio protetto**. 
    
    4. Nella schermata di **avvio protetto** toccare **Richiedi PIN per avviare il dispositivo**, quindi toccare **Continua**.

    5. Scegliere un PIN, ad esempio quello immesso in precedenza, e toccare **Conferma PIN**.

    6. Aprire l'app Portale aziendale, selezionare il dispositivo e toccare **Controlla conformità**.

Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.
