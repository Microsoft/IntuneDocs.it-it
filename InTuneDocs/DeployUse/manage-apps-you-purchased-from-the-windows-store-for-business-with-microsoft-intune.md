---
# required metadata

title: Gestire le app acquistate in Windows Store per le aziende| Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gestire le app acquistate in Windows Store per le aziende con Microsoft Intune
In [Windows Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dalla console di Intune le app acquistate con Volume Purchase Program, ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile distribuirle come qualsiasi altra app
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune
* Intune blocca la distribuzione e l'installazione di app se non sono disponibili licenze sufficienti

## Prima di iniziare
Prima di iniziare la sincronizzazione e la distribuzione di app da Windows Store per le aziende, leggere attentamente le informazioni seguenti:
* È necessario configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione. Per altre informazioni, vedere [Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md).
* È necessario aver ottenuto un account dopo aver effettuato la registrazione in Windows Store per le aziende.
* Dopo che un account di Windows Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
* Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune ma possono solo essere sincronizzate con Windows Store per le aziende.
* Intune sincronizza solo le app concesse in licenza online e acquistate da Windows Store per le aziende.
* Per usare questa funzionalità i dispositivi devono essere aggiunti a un dominio di Active Directory o alla rete aziendale.
* I dispositivi registrati devono usare la versione 1511 di Windows 10.

## Associare l'account Windows Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere Microsoft Intune.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## Configurare la sincronizzazione

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Amministrazione**.
2. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili** e quindi fare clic su **Store for Business**.
3. Nella pagina **Windows Store per le aziende** eseguire le operazioni seguenti:
* Se non è già stato fatto, fare clic sul collegamento per registrarsi a Windows Store per le aziende
* Dopo aver effettuato la registrazione, fare clic su **Configura sincronizzazione**
4. Nella finestra di dialogo **Configura sincronizzazione app di Windows Store for Business** selezionare **Abilita sincronizzazione di Windows Store for Business**.
5. Nell'elenco a discesa **Lingua** selezionare la lingua in cui visualizzare le app scaricate da Windows Store per le aziende nella console di Intune. Indipendentemente dalla lingua in cui sono visualizzate, verranno installate nella lingua dell'utente finale, quando disponibile.
6. Fare clic su **OK**.

## Sincronizzare le app

1. Nella pagina **Windows Store per le aziende** fare clic su **Sincronizza** per sincronizzare le app acquistate dallo Store con Intune.
2. Nell'area di lavoro **App** fare clic su **Software gestito** > **Software in licenza** per visualizzare le app disponibili e verificare che le app acquistate siano state importate correttamente.
Le app in questo nodo vengono visualizzate con il numero totale di licenze possedute e con il numero di licenze ancora disponibili.

## Distribuire le app

Le app scaricate dallo Store vengono distribuite allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Quando si distribuisce un'app di Windows Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app distribuita, non sarà possibile distribuire altre copie e sarà necessario eseguire una delle operazioni seguenti:
* Disinstallare l'app da alcuni dispositivi
* Ridurre l'ambito della distribuzione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze
* Acquistare più copie dell'app da Windows Store per le aziende


### Vedere anche
[Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)




<!--HONumber=May16_HO2-->


