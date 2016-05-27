---
# required metadata

title: Regole di accesso Exchange per dispositivi mobili gestiti con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Regole di accesso Exchange per dispositivi mobili
Le regole di accesso Exchange per i dispositivi mobili determinano il livello di accesso a Exchange per tali dispositivi. Queste impostazioni interessano tutti i dispositivi mobili, inclusi quelli non registrati in Microsoft Intune. È possibile iniziare definendo una **Regola predefinita** che verrà applicata a tutti i dispositivi mobili a cui non è applicata una regola personalizzata. Nella tabella seguente vengono descritti i livelli di accesso gestiti da Exchange ActiveSync:

|Livello di accesso|Descrizione|
|----------------|---------------|
|**Consentire a tutti i dispositivi mobili di accedere a Exchange, se non diversamente specificato da una regola personalizzata**|Nello stato di *accesso consentito* i dispositivi mobili sono in grado di eseguire la sincronizzazione con Exchange ActiveSync e di connettersi al server Exchange per recuperare la posta elettronica e modificare le informazioni di Calendario, Contatti, Attività e Note. Questo stato rimane attivo finché il dispositivo è conforme al **Criterio di protezione del dispositivo mobile di Intune** configurato, a meno che l'utente o il dispositivo mobile specifico sia stato bloccato dall'amministratore di Exchange.|
|**Impedire a tutti i dispositivi mobili di accedere a Exchange, se non diversamente specificato da una regola personalizzata**|Nello stato di *accesso bloccato* i dispositivi mobili sono bloccati e non sono autorizzati a connettersi al server di Exchange. I dispositivi ricevono l'errore HTTP 403 Forbidden. L'utente riceverà un messaggio di posta elettronica dal server Exchange in cui si informa che al dispositivo mobile è stato bloccato l'accesso alla cassetta postale. Questo messaggio non può essere sul dispositivo mobile bloccato. Per fare in modo che gli utenti con dispositivi bloccati ricevano le istruzioni, è possibile aggiungere a questo messaggio un testo personalizzato usando l'attività **Imposta notifica utente**.|
|**Mettere in quarantena tutti i dispositivi mobili, in modo da poter prendere una decisione su ciascun singolo dispositivo mobile in un secondo momento, se non diversamente specificato da una regola personalizzata**|Quando viene messo in quarantena, il dispositivo mobile può comunque connettersi al server Exchange, ma dispone di accesso limitato ai dati. L'utente può aggiungere contenuto alle proprie cartelle Calendario, Contatti, Attività e Note, ma il server non consentirà al dispositivo di recuperare contenuto dalla cassetta postale dell'utente. L'utente riceverà un messaggio di posta elettronica che indica che il dispositivo mobile è stato messo in quarantena. Il messaggio viene ricevuto nel dispositivo e nella cassetta postale dell'utente. Per aggiungere a questo messaggio testo personalizzato per fornire istruzioni agli utenti con dispositivi messi in quarantena, è possibile usare l'attività **Imposta notifica utente** .|

Una strategia di accesso è una combinazione di una **Regola predefinita** e di **Regole personalizzate** che si applicano a tutti i dispositivi mobili connessi a Exchange. Nella tabella seguente sono elencate alcune strategie di accesso di esempio.

|Strategia di accesso|Descrizione|
|-------------------|---------------|
|Elenco Consenti|È possibile usare un *elenco Consenti* per concedere l'accesso a un elenco di dispositivi noti e limitare l'accesso per tutti gli altri. A tale scopo, è necessario creare regole personalizzate in modo che i dispositivi specifici desiderati siano autorizzati ad accedere alle cassette postali degli utenti. Non appena si crea tale regola, è necessario impostare la regola di accesso predefinita in modo da bloccare o mettere in quarantena tutti gli altri dispositivi. Per aggiungere un nuovo dispositivo all'elenco Consenti, creare una nuova regola personalizzata.|
|Elenco Blocca|È possibile usare un *elenco Blocca* per concedere l'accesso a tutti i dispositivi per impostazione predefinita, bloccandolo solo per i dispositivi che non devono accedere all'organizzazione. Per creare un elenco Blocca, è necessario creare regole personalizzate per bloccare i dispositivi che non devono essere sincronizzati con le cassette postali dell'organizzazione. La regola predefinita deve essere impostata in modo da consentire l'accesso a tutti i dispositivi che non siano esplicitamente bloccati dalle regole esistenti. Per aggiungere un nuovo dispositivo o un insieme di dispositivi all'elenco Blocca, creare una nuova regola personalizzata.|
|Uso combinato di elenchi Consenti e Blocca|Oltre a creare elenchi Consenti e Blocca, è possibile mettere in quarantena nuovi dispositivi mobili quando vengono introdotti nell'organizzazione durante la valutazione. Se ad esempio si dispone di un elenco Blocca per i dispositivi mobili non consentiti e di un elenco Consenti per i dispositivi mobili consentiti nell'organizzazione, è possibile impostare la regola predefinita su Quarantena. Tutti gli altri dispositivi verranno automaticamente messi in quarantena. Ciò consente di rilevare i nuovi dispositivi quando vengono introdotti nell'organizzazione, nonché decidere se aggiungerli all'elenco Consenti o Blocca.|
Nella procedura riportata di seguito viene descritto come creare una regola personalizzata.

## Creare una regola di accesso predefinita

1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) &gt; **Criteri** &gt; **Regole di accesso a Exchange per dispositivi mobili**.

2.  Nell'elenco **Regola predefinita** selezionare la regola di accesso da applicare a tutti i dispositivi mobili a cui non si applica una regola o un'esenzione personale. Scegliere **Salva**.

Nella procedura riportata di seguito viene descritto come creare una regola personalizzata.

## Creare una regola di accesso personalizzata

1. Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) &gt; **Criteri** &gt; **Regole di accesso a Exchange per dispositivi mobili**.

2.  Nell'elenco **Regole personalizzate** fare clic su **Aggiungi regola** e creare una regola personalizzata. Scegliere **Salva**.


<!--HONumber=May16_HO1-->


