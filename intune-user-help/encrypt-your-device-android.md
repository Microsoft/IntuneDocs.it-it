---
title: Come proteggere il dispositivo Android con la crittografia | Microsoft Docs
description: Proteggere il dispositivo Android
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 8ba85e15fb55a4de1b2f1db53bc5b9962de84394
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-protect-your-android-device-using-encryption"></a>Come proteggere il dispositivo Android usando la crittografia

Quando si crittografa un dispositivo, si esegue il wrapping delle informazioni in esso contenute in un livello di codice protettivo che impedisce l'accesso agli utenti non autorizzati. Come passo aggiuntivo per assicurarsi che le informazioni siano protette, l'organizzazione richiede di crittografare il dispositivo Android prima di accedere a file, posta elettronica o dati aziendali.

> [!Note]
> Potrebbe essere necessario impostare un PIN o una password prima di crittografare il dispositivo, se richiesto dall'amministratore IT.

Un telefono di cui si annulla la registrazione rimarrà crittografato.

1.  Assicurarsi che per il dispositivo sia stato impostato un PIN o una password per il blocco dello schermo.

2.  In **Impostazioni** scegliere **Sicurezza** &gt; **Crittografa dispositivo**.
    In alcuni telefoni è necessario fare clic su **Memoria** &gt; **Crittografia memoria** o **Memoria** &gt; **Schermata di blocco e Sicurezza** &gt; **Altre impostazioni di sicurezza** per trovare l'opzione "Crittografia".

3.  Seguire le istruzioni visualizzate. Durante la crittografia il dispositivo potrebbe essere riavviato più volte.

> [!Note]
> Alcuni dispositivi Android non possono essere crittografati. Per altre informazioni, vedere [qui](your-device-appears-encrypted-but-cp-says-otherwise-android.md).

### <a name="what-to-do-if-you-have-issues"></a>Operazioni da eseguire in caso di problemi
**Problema**: il dispositivo è già stato crittografato e si verifica uno dei problemi seguenti:

- Il pulsante di crittografia è disabilitato.
- Un messaggio informa che è necessario crittografare il dispositivo.
- Si verificano errori quando si prova a usare l'app Portale aziendale.

**Possibili soluzioni**

- Verificare che il dispositivo sia carico e collegato.
- Assicurarsi di aver impostato un PIN o una password nel dispositivo.
- Se il PIN o la password sono già impostati nel dispositivo, provare i passaggi seguenti che l'amministratore IT potrebbe richiedere per rendere più sicuro il dispositivo. I nomi dei menu visualizzati potrebbero essere leggermente diversi da quelli riportati nelle procedure, a seconda del tipo di dispositivo Android in uso.

    1. Toccare **Impostazioni** > **Sicurezza** > **Blocco schermo**. Confermare il PIN o la password corrente.

    2. In **Selezione blocco schermo** scegliere il tipo di blocco schermo da usare.

    3. Nella schermata di **avvio protetto** toccare **Richiedi PIN per avviare il dispositivo**, quindi toccare **Continua**.

    4. Scegliere un PIN, ad esempio quello immesso in precedenza, e toccare **Conferma PIN**.

    5. Aprire l'app Portale aziendale, selezionare il dispositivo e toccare **Controlla conformità**.

Serve ancora assistenza? Contattare l'amministratore IT (accedere al [sito Web del portale aziendale](http://portal.manage.microsoft.com) per informazioni sui contatti) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.
