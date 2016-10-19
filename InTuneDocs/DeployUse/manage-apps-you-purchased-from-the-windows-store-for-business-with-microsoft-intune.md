---
title: Gestire Windows Store per le app aziendali | Microsoft Intune
description: Connettere Microsoft Intune a Windows Store per le aziende se si vuole gestire e distribuire app acquistate con Volume Purchase Program dalla console di Intune
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 8eee27e0c24e353143ce2014b65dc91af2c04843


---

# Gestire le app acquistate in Windows Store per le aziende con Microsoft Intune
In [Windows Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dalla console di Intune le app acquistate con Volume Purchase Program. Ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile distribuirle come qualsiasi altra app.
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune.
* Intune blocca la distribuzione e l'installazione di app se non sono disponibili licenze sufficienti.

## Prima di iniziare
Prima di iniziare la sincronizzazione e la distribuzione di app da Windows Store per le aziende, leggere attentamente le informazioni seguenti:
* È necessario configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione. Per altre informazioni, vedere [Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md).
* È necessario ottenere un account registrandosi in Windows Store per le aziende.
* Dopo che un account di Windows Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
* Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune. ma possono solo essere sincronizzate con Windows Store per le aziende.
* Intune sincronizza solo le app concesse in licenza online e acquistate da Windows Store per le aziende.
* Per usare questa funzionalità i dispositivi devono essere aggiunti a Servizi di dominio Active Directory o all'area di lavoro.
* I dispositivi registrati devono usare la versione 1511 di Windows 10.

## Associare l'account Windows Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere **Microsoft Intune**.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## Configurare la sincronizzazione

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
2. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili** e quindi fare clic su **Windows Store per le aziende**.
3. Nella pagina **Windows Store per le aziende** eseguire le operazioni seguenti:
 * Se non è già stato fatto, fare clic sul collegamento per registrarsi a Windows Store per le aziende.
 * Dopo aver effettuato la registrazione, fare clic su **Configura sincronizzazione**.
4. Nella finestra di dialogo **Configura sincronizzazione app di Windows Store for Business** selezionare **Abilita sincronizzazione di Windows Store for Business**.
5. Nell'elenco a discesa **Lingua** selezionare la lingua in cui visualizzare le app scaricate da Windows Store per le aziende nella console di Intune. Indipendentemente dalla lingua in cui sono visualizzate, verranno installate nella lingua dell'utente finale, quando disponibile.
6. Fare clic su **OK**.

## Sincronizzare le app

1. Nella pagina **Windows Store per le aziende** scegliere **Sincronizza** per sincronizzare le app acquistate dallo Store con Intune.
2. Nell'area di lavoro **App** scegliere **Software gestito** > **Software in licenza** per visualizzare le app disponibili e verificare che le app acquistate siano state importate correttamente. Le app in questo nodo vengono visualizzate con il numero totale di licenze possedute e con il numero di licenze ancora disponibili.

## Distribuire le app

Le app scaricate dallo Store vengono distribuite allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Quando si distribuisce un'app di Windows Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app distribuita, non sarà possibile distribuire altre copie. Scegliere una delle azioni seguenti:
* Disinstallare l'app da alcuni dispositivi.
* Ridurre l'ambito della distribuzione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze.
* Acquistare più copie dell'app da Windows Store per le aziende.

> [!Important]
> Le app distribuite sono disponibili solo per l'utente che ha originariamente registrato il dispositivo. Gli altri utenti non possono accedere all'app.


### Vedere anche
[Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO4-->


