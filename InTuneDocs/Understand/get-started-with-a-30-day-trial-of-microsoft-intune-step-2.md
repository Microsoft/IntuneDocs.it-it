---
title: Aggiungere utenti per una valutazione di 30 giorni di Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cb729533107d511fa0cc863ec6ab842e7624982
ms.openlocfilehash: 15e641f4f5f60c4a3eb3a7b09cab8cb9ef788cba


---

# Aggiungere utenti per una valutazione di 30 giorni di Microsoft Intune
Dopo aver configurato l'account, usare la procedura guidata **Nuovi utenti** per aggiungere singoli account utente a Intune, oppure la procedura guidata **Aggiungi utenti in blocco** per aggiungere gli utenti in blocco (vedere le istruzioni in questa sezione).  Prima di iniziare, è importante comprendere come vengono gestiti gli account amministratore in Intune.

Un amministratore tenant usa l'interfaccia di amministrazione di Office 365 per aggiungere gli utenti al **gruppo Utenti** di Microsoft Intune. L'aggiunta di utenti al  **gruppo Utenti** assegna le licenze della sottoscrizione a Intune agli utenti e consente di visualizzare gli utenti nella console di amministrazione di Microsoft Intune.

Gli account amministratore per Intune non vengono creati nell'interfaccia di amministrazione di Office 365, come avviene per i normali account utente. Diversamente, agli utenti vengono assegnati diritti amministrativi di accesso in sola lettura o accesso completo usando la console di amministrazione nell'area di lavoro **Amministrazione** in **Administration Management** (Gestione amministratori). Gli amministratori del servizio a cui è assegnato l'accesso in sola lettura non possono modificare le impostazioni di Intune, ma possono visualizzare i dati ed eseguire i report. Gli amministratori del servizio con accesso completo dispongono di tutti i diritti amministrativi.

La console di amministrazione di Intune può essere usata per visualizzare le informazioni sull'amministratore tenant, ma non per creare gli amministratori tenant. Per impostazione predefinita, il proprietario della sottoscrizione diventa un amministratore tenant del servizio Microsoft Intune e ha l'accesso completo sia all'interfaccia di amministrazione di Office 365 che alla console di amministrazione di Intune. È consigliabile creare almeno un altro account di amministratore tenant usando l'interfaccia di amministrazione di Office 365 per delegare le attività e per essere certi di non restare bloccati senza accesso all'account amministratore del servizio Intune se si dimentica la password.

## Aggiungere singoli account utente
Usare i passaggi seguenti per creare altri account utente nel tenant di valutazione. Ricordare che ogni account utente aggiunto viene considerato come un'unità nel computo delle 100 licenze disponibili nella versione di valutazione gratuita di Intune.

1.  Nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkID=787455) scegliere **Aggiungi utenti** &gt; **Nuovo**&gt; **Utente** per avviare la procedura guidata **Nuovi utenti**.

2.  Nella pagina **Dettagli** completare i campi richiesti.

3.  Nella pagina **Impostazioni** impostare la **località** per l'utente.

4.  Nella pagina **Gruppo** fare clic su **Avanti** per accettare il valore predefinito e assegnare una licenza per Intune all'account utente.

5.  Nella pagina **Posta elettronica** specificare fino a cinque indirizzi di posta elettronica a cui verrà inviata una notifica contenente il nome utente e la password temporanea creata per l'account. Separare più indirizzi di posta elettronica con punti e virgola (;). Al termine, fare clic su **Crea** per aggiungere l'utente alla sottoscrizione.

6.  Nel **risultati** pagina, è possibile visualizzare il nuovo nome account e la relativa password temporanea. Intune crea automaticamente la password temporanea.

7.  Quando il nuovo utente viene visualizzato nell'interfaccia di amministrazione di Office 365, verificare che sia stato creato correttamente:

    1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Amministrazione** &gt; **Portale aziendale**, quindi scorrere fino alla parte inferiore della schermata. Copiare l'URL indicato nel **Portale aziendale di Intune**.

    2.  Aprire una nuova finestra del browser in modalità di privacy (in Internet Explorer scegliere **Strumenti** &gt; **InPrivate Browsing**) oppure aprire una nuova finestra in un altro dispositivo e accedere all'URL copiato nel passaggio precedente. Quando gli utenti accedono per la prima volta, devono specificare una nuova password per l'account.

## Aggiungi utenti in blocco
Per aggiungere utenti in blocco a Intune, usare la procedura guidata **Aggiunta utenti in blocco** per caricare un file con valori separati da virgola (csv) contenente i dati utente. I collegamenti nella procedura guidata consentono di scaricare un modello vuoto e un file CSV di esempio. La prima riga del file CSV deve contenere, nell'ordine corretto, tutte le etichette di colonna per i dati utente. Quindi, per ciascun utente nel file CSV è necessario includere il **nome utente** (ad esempio **bob@contoso.com**) e un **nome visualizzato** (ad esempio **Bob Kelly**).

1.  Nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkID=787455) scegliere **Utenti** &gt; **Nuovo**.

2.  Fare clic su **Aggiungi in blocco** per avviare la procedura guidata Aggiunta utenti in blocco.

3.  Nella pagina **Seleziona file** fare clic su **Sfoglia** per specificare un file con estensione csv esistente nel computer e caricarlo. È anche possibile scaricare un file CSV di esempio o un file modello vuoto usando i collegamenti nella procedura guidata.

4.  Nella pagina **Verifica** esaminare i risultati e fare clic su **Visualizza** per visualizzare altri dettagli.

5.  Nella pagina **Impostazioni** verificare che lo stato di accesso sia **Consentito** e impostare il **percorso**. Queste impostazioni si applicano a tutti gli account utente aggiunti dal file CSV.

6.  Nella pagina **Gruppo** fare clic su **Avanti** per accettare il valore predefinito e assegnare una licenza per Intune a tutti gli account utente aggiunti dal file CSV. Per impostazione predefinita, la casella di controllo è selezionata e viene assegnata una licenza per Intune a ogni account.

7.  Nella pagina **Posta elettronica** specificare fino a cinque indirizzi di posta elettronica a cui verrà inviata una notifica contenente i nomi utente e le password temporanee create da Intune per ogni account. Separare più indirizzi di posta elettronica con punti e virgola (;). Fare clic su **Crea** per aggiungere gli utenti alla sottoscrizione.

8.  Nella pagina **Risultati** è possibile visualizzare il nome account e la password temporanea per ciascun account utente.

Ogni account utente importato a questo punto viene visualizzato nel nodo **Utenti** dell'interfaccia di amministrazione di Office 365. Quando i nuovi utenti accedono per la prima volta, devono specificare una nuova password per l'account utente.

### Passaggi successivi
A questo punto, il passaggio 2 della procedura di *valutazione di Microsoft Intune* è stato completato.

>[!div class="step-by-step"]

>[&larr; **Iscriversi per una valutazione**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**Creare gruppi** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


