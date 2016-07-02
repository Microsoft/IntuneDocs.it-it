---
title: Pianificare i gruppi di utenti e dispositivi | Microsoft Intune
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 82ab2dbfada6c0745195da149d5f0dc1948ceb92
ms.openlocfilehash: e89d8384532b994d810649fc07c698237e2f3cec


---

# Pianificare i gruppi di utenti e dispositivi
I gruppi in Intune offrono una grande flessibilità per la gestione di utenti e dispositivi. È possibile impostare i gruppi in base alle esigenze dell'organizzazione in riferimento a:

- posizione geografica
- reparto
- caratteristiche hardware
- sistema operativo
- proprietà del dispositivo da parte dell'utente o della società


## Funzionamento dei gruppi di Intune


La visualizzazione predefinita del nodo Gruppi nella console di amministrazione di Intune è la seguente:

![Schermata della visualizzazione predefinita del nodo Gruppi nella console di Intune](/intune/media/Intune_Planning_Groups_Default_small.png)

I criteri vengono distribuiti nei gruppi, quindi la gerarchia dei gruppi rappresenta una delle più importanti considerazioni sulla progettazione. È anche importante sapere che un gruppo padre non può essere modificato dopo aver creato il gruppo, quindi la struttura del gruppo è di vitale importanza dal momento in cui si inizia a usare il servizio Intune. Di seguito vengono descritte alcune delle procedure consigliate per la progettazione di una gerarchia di gruppi in base alle proprie esigenze organizzative.

## Ruoli di appartenenza a gruppi

1. Un gruppo può contenere utenti o dispositivi, ma non entrambi.

    * **Gruppi di dispositivi:** sono inclusi computer e dispositivi mobili. Prima di aggiungere un computer a un gruppo, deve essere registrato. Prima di aggiungere un dispositivo mobile a un gruppo, l'ambiente deve essere configurato per supportare i dispositivi mobili e i dispositivi devono essere registrati o individuati con Exchange ActiveSync.

    * **Gruppi di utenti:** un gruppo può contenere utenti dai gruppi di sicurezza, ossia gruppi sincronizzati da Active Directory. Se non si usa la sincronizzazione di Active Directory, è possibile creare manualmente questi gruppi.

2. Un dispositivo o un utente può appartenere a più gruppi.

3. Un gruppo può includere ed escludere i membri in base alle seguenti regole di appartenenza:

    * **Criteri di appartenenza:** si tratta di regole dinamiche che Intune esegue per includere o escludere i membri. Questi criteri usano i **gruppi di sicurezza** e altre informazioni sincronizzate da Active Directory (AD) locale. Quando il gruppo di sicurezza o i dati vengono modificati, l'appartenenza al gruppo cambia quando viene sincronizzata con AD.

    * **Appartenenza diretta:** si tratta di regole statiche che consentono di aggiungere o escludere i membri in modo esplicito. L'elenco di appartenenza è statico.

4. Per creare gruppi di utenti o di dispositivi che includono utenti o computer, non è necessario usare Servizi di dominio Active Directory. Per consentire l'aggiunta di dispositivi mobili nei gruppi di dispositivi, è tuttavia necessario configurare l'ambiente in uso in modo che supporti i dispositivi mobili.

    Inoltre, i dispositivi devono essere rilevati e aggiunti a Intune.

## Regole di relazione dei gruppi

1. Ogni gruppo creato deve avere un gruppo padre, che non può più essere modificato dopo essere stato creato.

2. Quando si aggiungono utenti o dispositivi a un gruppo figlio:

    * I gruppi figlio sono sempre sottoinsiemi del gruppo padre.

    * I nuovi membri aggiunti a un gruppo figlio vengono aggiunti automaticamente al relativo gruppo padre.

    * Non è possibile aggiungere un membro a un gruppo figlio quando tale membro viene escluso dal gruppo padre.

3. L'appartenenza di un gruppo padre definisce la possibile appartenenza del gruppo figlio.

4. Quando si elimina un gruppo padre, vengono eliminati tutti i gruppi figlio.

5. È possibile distribuire i contenuti e i criteri a un gruppo padre escludendo la distribuzione ai gruppi figlio.

6. È possibile aggiungere un utente o un dispositivo specifico a un gruppo figlio che non è membro del gruppo padre. In tal caso, il nuovo membro del gruppo verrà aggiunto al gruppo padre.

    Tuttavia, non è possibile aggiungere un membro a un gruppo figlio escluso dal gruppo padre.

7. L'appartenenza ai gruppi è ricorsiva. Ad esempio:

    * **Pat** è un membro di un solo gruppo, il gruppo di sicurezza **Utenti portatile** .

    * Il gruppo **Utenti laptop** è un membro del gruppo di sicurezza **Utenti approvati** .

    * Viene creato un gruppo in Intune che usa una query di appartenenza dinamica che include i membri del gruppo **Utenti approvati**. Il risultato è che il gruppo utenti di Intune include **Pat**.

> [!TIP]
> Quando si creano gruppi, considerare la modalità di applicazione dei criteri. Ad esempio, si potrebbe disporre di criteri specifici per i sistemi operativi per dispositivi e i criteri specifici per ruoli diversi all'interno dell'organizzazione o nelle unità organizzative che sono già state definite nell’Active Directory. Alcuni considerano utile disporre di gruppi di dispositivi specifici di Windows, iOS e Android, nonché gruppi di utenti per ogni ruolo dell'organizzazione.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Gruppi predefiniti
Intune fornisce nove gruppi predefiniti che non è possibile modificare o eliminare: <!--maybe a screen shot would be best?-->

-   **Tutti gli utenti**
    -   Utenti non raggruppati
-   **Tutti i dispositivi**
    -   Tutti i computer
    -   Tutti i dispositivi mobili
        -   Tutti i dispositivi gestiti direttamente
        -   Tutti i dispositivi gestiti da Exchange ActiveSync
    -   Tutti i dispositivi di proprietà dell'azienda
    -   Dispositivi non raggruppati

> [!NOTE]
> È fondamentale la *semplicità*. Se l'organizzazione non ha esigenze specifiche come quelle descritte di seguito, mantenere la struttura e i criteri del gruppo predefiniti renderà il servizio più gestibile a lungo termine. La manutenzione risulterà più semplice se è possibile gestire gli utenti in modo uniforme con una minima differenziazione per gruppo, in modo da dover gestire un numero inferiore di criteri.


### Tutti gli utenti e i dispositivi nella propria organizzazione
Definire un gruppo padre per tutti gli utenti e i dispositivi nell'organizzazione, perché è probabile che ci saranno criteri applicabili a tutti. A questo scopo, è possibile usare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** in Intune. I sottogruppi che consentono di organizzare i dispositivi in base alle specifiche, ad esempio un gruppo per i dispositivi BYOD e uno per i dispositivi di proprietà dell'azienda (CO), possono essere elementi figlio dei gruppi padre **Tutti gli utenti** e **Tutti i dispositivi**.

## Personalizzazione dei gruppi per l'organizzazione

### Dispositivi BYOD e di proprietà aziendale
Se l'organizzazione consente ai dipendenti di usare i propri dispositivi durante il lavoro (BYOD), fornisce i dispositivi di proprietà dell'azienda (CO) o consente una combinazione di entrambi gli scenari, si consiglia di applicare criteri basati su queste due categorie di dispositivi.

Nel caso di dispositivi BYOD o di una combinazione dei due scenari, assicurarsi di pianificare i criteri che non violano le normative locali in materia di privacy. Creare un gruppo padre per tutti gli utenti che porteranno i propri dispositivi. Questo gruppo può quindi essere usato per applicare i criteri che sono applicabili a tutti gli utenti in questa categoria.

![Schermata della creazione di un gruppo padre BYOD](/intune/media/Intune_Planning_Groups_BYOD_small.png)

Analogamente, è possibile creare un gruppo per gli utenti CO dell'organizzazione:

![Schermata di gruppi di utenti di pari livello per BYOD e CO](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Gruppi per aree geografiche
Se l'organizzazione necessita di criteri per aree specifiche, è possibile creare gruppi in base all'area geografica. È possibile basare tali criteri sui gruppi regionali già creati in Active Directory (AD) e sincronizzarli in Azure AD. È anche possibile crearli direttamente in Azure AD.

Questi screenshot mostrano come creare gruppi di Intune in base ai gruppi sincronizzati da AD locale. In questi esempi si presuppone che esista un gruppo di sicurezza di AD denominato **Gruppo utenti USA**.

1. Prima di tutto, fornire le informazioni generali.

![Schermata dell'area Modifica gruppo](/intune/media/Intune_Planning_Groups_AD_General_small.png)

In Criteri di appartenenza, selezionare **Gruppo utenti USA**, sincronizzato da AD, come gruppo di sicurezza da usare nelle regole di appartenenza.

![Finestra di dialogo Modifica gruppo](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

Verificare i dati e quindi fare clic su **Fine** per completare la creazione del gruppo.

![Finestra di dialogo Modifica gruppo](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

Nel nostro esempio, abbiamo creato anche un gruppo Medio Oriente e Asia, MEA.

> [!NOTE]
> Se l'appartenenza al gruppo non viene popolata in base all'appartenenza ai gruppi di sicurezza, controllare di avere licenze Intune assegnate a tali membri.

### Gruppi per hardware specifico
Se l'organizzazione necessita di criteri applicabili a tipi di hardware specifici, è possibile creare gruppi in base a questo requisito. È possibile basare i criteri su gruppi specifici già creati in AD locale e sincronizzarli in Azure AD. È anche possibile crearli direttamente in Azure AD. In questo esempio, **Gruppo utenti USA** viene usato come gruppo padre del gruppo **Utenti di portatili**.

![Finestra di dialogo Seleziona gruppo di sicurezza](/intune/media/Intune_Planning_Groups_Laptop_small.png)

A questo punto, la gerarchia di gruppi dovrebbe essere visualizzata come illustrato di seguito. Come si può vedere, ora ci sono membri all'interno del gruppo Intune **Laptop Users**. Tutti i criteri applicati a questo gruppo verranno ora applicati agli utenti di portatili BYOD dall'area degli Stati Uniti.

![Visualizzazione del gruppo Utenti portatili](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Gruppi per sistemi operativi specifici
Se l'organizzazione necessita di criteri applicabili a sistemi operativi specifici, ad esempio Android, iOS o Windows, è possibile creare gruppi in base a questo requisito. Come negli esempi precedenti, è possibile basare i criteri su gruppi specifici per il sistema operativo già creati in AD locale e sincronizzarli in Azure AD. È anche possibile crearli direttamente in Azure AD.

Seguendo lo stesso metodo degli esempi precedenti, è possibile creare gruppi in base agli utenti <!--devices?--> usando piattaforme del sistema operativo specifiche.

> [!NOTE]
> Se gli utenti usano più piattaforme mobili/sistemi operativi e non hanno un metodo automatico per classificare gli utenti come utenti di Android, utenti di iOS o utenti di Windows, è possibile applicare i criteri a livello di dispositivo, consentendo una maggiore flessibilità nell'applicazione di criteri specifici del sistema operativo.
>
> Non è possibile eseguire il provisioning dei gruppi in modo dinamico in base al sistema operativo del dispositivo. Eseguire questa operazione usando i gruppi di sicurezza di AD o AAD.

![Visualizzare il gruppo Utenti portatili](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

Quando tutti i gruppi di utenti sono stati popolati in base a questi requisiti aziendali, la gerarchia dei gruppi dovrebbe essere simile alla seguente:

![Visualizzazione della gerarchia dei gruppi](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Questa gerarchia consente di applicare i criteri dell'organizzazione in modo appropriato.

### Gruppi di dispositivi
È anche possibile creare gruppi simili per i dispositivi, come illustrato di seguito, a partire da un gruppo esteso che includa tutti i dispositivi di proprietà dei dipendenti, per lo scenario BYOD:

![Finestra di dialogo Crea gruppo](/intune/media/Intune_Planning_Groups_Device_General_small.png)

Assicurarsi di selezionare **Tutti i dispositivi (computer e dispositivi mobili)** in modo che il gruppo includerà tutti i dispositivi BYO:

![Definire la pagina dei criteri di appartenenza](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

Verificare i dati e fare clic su **Fine** per creare il gruppo BYOD.

![Finestra di dialogo Crea gruppo](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

Continuare a creare gruppi di dispositivi, fino a quando non si avrà una gerarchia di gruppi di dispositivi simile alla gerarchia dei gruppi di utenti. A questo punto il nodo del gruppo nella console di Intune dovrebbe essere simile al seguente:

![Visualizzazione della gerarchia dei gruppi di Intune](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## Gerarchie di gruppi e convenzioni di denominazione
Per semplificare la gestione dei criteri è consigliabile assegnare a ogni criterio un nome in base allo scopo, alla piattaforma e all'ambito a cui viene applicato. Questo standard di denominazione deve seguire la struttura dei gruppi creati in preparazione per l'applicazione dei criteri.

Ad esempio, per un criterio Android che viene applicato a tutti i dispositivi mobili Android aziendali a livello dell'area degli Stati Uniti, il criterio può essere denominato **CO_US_Mob_Android_General**.

![Creare criteri per Android](/intune/media/Intune_planning_policy_android_small.png)

Questa modalità di assegnazione di nomi ai criteri consentirà di identificare rapidamente i criteri e il relativo scopo e ambito previsto dal nodo dei criteri della console, come illustrato di seguito:

![Elenco dei criteri di Intune](/intune/media/Intune_planning_policy_view_small.png)

## Passaggi successivi
[Creare i gruppi](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


