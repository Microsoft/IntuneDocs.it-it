---
title: Impostare restrizioni di registrazione in Microsoft Intune
titlesuffix: ''
description: Limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99c69d08bb11ed097e2262938d254074169492c3
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Gli amministratori di Intune sono in grado di creare e gestire restrizioni di registrazione che definiscono i tipi e il numero di dispositivi che possono essere registrati per la gestione con Intune. È possibile creare più restrizioni e applicarle a gruppi utenti diversi. È anche possibile impostare l'[ordine di priorità](#change-enrollment-restriction-priority) delle diverse restrizioni.

>[!NOTE]
>Le restrizioni di registrazione non sono una funzionalità di sicurezza. I dispositivi compromessi possano dare risultati non previsti. Queste restrizioni sono una barriera di massimo sforzo per gli utenti legittimi.

>[!NOTE]
>Le funzionalità menzionate in questo articolo per le restrizioni e l'impostazione dell'ordine di priorità per la registrazione dei dispositivi con applicazione ai gruppi sono in corso di distribuzione tra i clienti di Intune. Fino al termine della distribuzione, le funzionalità per gruppi e priorità potrebbero non essere accessibili.

Le restrizioni di registrazione specifiche che è possibile creare includono:

- Numero massimo di dispositivi registrati.
- Piattaforme per dispositivi che possono registrare:
  - Android.
  - Android for Work.
  - iOS.
  - macOS.
  - Windows.
- Versione del sistema operativo della piattaforma per iOS, Android, Android for Work e Windows. (È possibile usare solo le versioni di Windows 10. Lasciare questo campo vuoto se è consentito Windows 8.1.)
  - Versione minima.
  - Versione massima.
- Limitare i dispositivi personali (solo iOS, Android, Android for Work e macOS).

## <a name="default-restrictions"></a>Restrizioni predefinite

Per il tipo e il numero massimo di dispositivi vengono applicate automaticamente restrizioni predefinite che possono essere modificate. Le restrizioni predefinite si applicano a tutte le registrazioni, con e senza utente. È possibile sostituire queste impostazioni predefinite tramite la creazione di nuove restrizioni con priorità più alta.

## <a name="create-a-restriction"></a>Creare una restrizione

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. Selezionare **Crea restrizione**.
5. Assegnare un nome e una descrizione alla restrizione.
6. Scegliere un **Tipo di restrizione** e quindi selezionare **Crea**.
7. Per le restrizioni relative al numero di dispositivi selezionare **Limite di dispositivi** per impostare il numero massimo di dispositivi che un utente è autorizzato a registrare.
8. Per le restrizioni relative ai tipi di dispositivo, selezionare **Piattaforme** e su **Configurazioni della piattaforma** per consentire o bloccare varie versioni di diverse piattaforme.
9. Selezionare **Assegnazioni** > **+ Seleziona i gruppi**.
10. In **Selezionare i gruppi** selezionare uno o più gruppi e quindi scegliere **Seleziona**. La restrizione si applica solo ai gruppi a cui è assegnata. La restrizione ha effetto solo se viene assegnata ad almeno un gruppo.
11. Selezionare **Salva**.
12. La nuova restrizione viene creata con una priorità di livello immediatamente superiore a quello dell'impostazione predefinita. È possibile [modificare la priorità](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Impostare le restrizioni sul tipo di dispositivi

È possibile modificare le impostazioni relative al tipo di dispositivo tramite la procedura seguente:

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **Restrizioni sul tipo di dispositivi** scegliere la restrizione che si vuole impostare.
5. Sotto il nome della restrizione (**Tutti gli utenti** per la restrizione predefinita) selezionare **Piattaforme**. Scegliere **Consenti** o **Blocca** per ogni piattaforma elencata.
6. Selezionare **Salva**.
7. Sotto il nome della restrizione (**Tutti gli utenti** per la restrizione predefinita) selezionare **Configurazioni della piattaforma**. Selezionare quindi le **Versioni** minima e massima per le piattaforme elencate. Versioni supportate:
    - Android e Android for Work supportano major.minor.rev.build.
    - iOS supporta il formato di versione maggiore.minore.revisione.
    - Windows supporta il formato maggiore.minore.revisione.build solo per Windows 10.
  Le versioni del sistema operativo non si applicano ai dispositivi Apple registrati in Device Enrollment Program, Apple School Manager o nell'app Apple Configurator.
8. Specificare **Consenti** o **Blocca** per i dispositivi **di proprietà personale** per ogni piattaforma elencata.
    ![Area di lavoro delle restrizioni relative ai dispositivi con la configurazione dei dispositivi di proprietà personale visualizzate per le configurazioni delle piattaforme predefinite](media/device-restrictions-platform-configurations.png)
9. Selezionare **Salva**.


>[!NOTE]
>- Anche se si bloccano i dispositivi personali Android per la registrazione, i dispositivi di proprietà personale con Android for Work possono ancora essere registrati.
>- Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.
>- Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi

È possibile modificare le impostazioni relative al numero di dispositivi tramite la procedura seguente:

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **Restrizione sul limite di dispositivi** scegliere la restrizione che si vuole impostare.
5. Selezionare **Limite di dispositivi** e quindi nell'elenco a discesa selezionare il numero massimo di dispositivi che un utente può registrare.
    ![Pannello delle restrizioni sul limite di dispositivi con le restrizioni sul limite del dispositivo](./media/device-restrictions-limit.png)
6. Selezionare **Salva**.


Verrà visualizzata una notifica che informa gli utenti quando raggiungono il limite di dispositivi registrati. Ad esempio, in iOS la notifica è simile alla seguente:

![notifica iOS per il limite di dispositivi](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Modificare la priorità delle restrizioni di registrazione

La priorità viene usata se un utente appartiene a più gruppi a cui sono assegnate restrizioni. Gli utenti sono soggetti solo alla restrizione con priorità più alta assegnata a un gruppo di cui fanno parte. Si supponga ad esempio che Joe appartenga al gruppo A, a cui sono assegnate restrizioni con priorità 5, e anche al gruppo B, a cui sono assegnate restrizioni con priorità 2. Joe è soggetto solo alle restrizioni con priorità 2.

Quando si crea una restrizione, questa viene aggiunta all'elenco al livello immediatamente superiore a quello dell'impostazione predefinita.

La registrazione di dispositivi prevede restrizioni predefinite sia per il tipo che per il numero di dispositivi. Queste due restrizioni si applicano a tutti gli utenti, a meno che non vengano sostituite da restrizioni con priorità più alta.

È possibile modificare la priorità di tutte le restrizioni non predefinite.

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. Passare il puntatore del mouse sulla restrizione nell'elenco delle priorità.
5. Usando i tre punti verticali, trascinare la priorità nella posizione voluta nell'elenco.
