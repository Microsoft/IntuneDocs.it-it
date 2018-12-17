---
title: Impostare restrizioni di registrazione in Microsoft Intune
titlesuffix: ''
description: Limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e6f816ae0eb025addfaa0c5f7ec7d16005f6b040
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112953"
---
# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Gli amministratori di Intune sono in grado di creare e gestire restrizioni di registrazione che definiscono i tipi e il numero di dispositivi che possono essere registrati per la gestione con Intune. È possibile creare più restrizioni e applicarle a gruppi utenti diversi. È anche possibile impostare l'[ordine di priorità](#change-enrollment-restriction-priority) delle diverse restrizioni.

>[!NOTE]
>Le restrizioni di registrazione non sono una funzionalità di sicurezza. I dispositivi compromessi possano dare risultati non previsti. Queste restrizioni sono una barriera di massimo sforzo per gli utenti legittimi.

Le restrizioni di registrazione specifiche che è possibile creare includono:

- Numero massimo di dispositivi registrati.
- Piattaforme per dispositivi che possono registrare:
  - Android
  - Profilo di lavoro Android
  - iOS
  - macOS
  - Windows
- Versione del sistema operativo della piattaforma per iOS, Android, profilo di lavoro Android e Windows. (È possibile usare solo le versioni di Windows 10. Lasciare questo campo vuoto se è consentito Windows 8.1.)
  - Versione minima.
  - Versione massima.
- Limitare i dispositivi personali (solo iOS, Android, profilo di lavoro Android, macOS e Windows).

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

È possibile modificare le impostazioni relative al tipo di dispositivo tramite la procedura seguente. Queste restrizioni non influiscono sui dispositivi già registrati. I dispositivi registrati con l'[agente del computer di Intune](manage-windows-pcs-with-microsoft-intune.md) non possono essere bloccati con questa funzionalità.

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **Restrizioni sul tipo di dispositivi** > scegliere la restrizione che si vuole impostare > **Proprietà** > **Seleziona le piattaforme**. Scegliere **Consenti** o **Blocca** per ogni piattaforma elencata.
    ![Acquisizione schermo per consentire o bloccare una piattaforma](media/enrollment-restrictions-set/platform-allow-block.png)
5. Scegliere **OK**.
6. Scegliere **Configura piattaforme**.
    ![Acquisizione schermo per la configurazione di piattaforme](media/enrollment-restrictions-set/configure-platforms.png)
7. Selezionare le **Versioni** minima e massima per le piattaforme elencate. I formati delle versioni supportate includono:
    - Il profilo di lavoro Android supporta il formato maggiore.minore.revisione.build.
    - iOS supporta il formato di versione maggiore.minore.revisione. Le versioni del sistema operativo non si applicano ai dispositivi Apple registrati in Device Enrollment Program, Apple School Manager o nell'app Apple Configurator.
    - Windows supporta il formato maggiore.minore.revisione.build solo per Windows 10.
8. Scegliere **Consenti** o **Blocca** per i dispositivi **di proprietà personale** per ogni piattaforma elencata.
9. Scegliere **OK**.

### <a name="blocking-personal-android-devices"></a>Blocco dei dispositivi Android personali
- Anche se si blocca la registrazione dei dispositivi personali Android, i dispositivi personali del profilo di lavoro Android possono ancora essere registrati.
- Per impostazione predefinita, le impostazioni dei dispositivi del profilo di lavoro Android corrispondono alle impostazioni dei dispositivi Android. Dopo la modifica delle impostazioni del profilo di lavoro Android questa corrispondenza andrà persa.
- Se si blocca la registrazione dei dispositivi del profilo di lavoro Android personali, solo i dispositivi Android aziendali possono essere registrati come profilo di lavoro Android.

### <a name="blocking-personal-windows-devices"></a>Blocco dei dispositivi Windows personali
Se si blocca la registrazione dei dispositivi Windows personali, Intune verifica che ogni nuova richiesta di registrazione Windows sia stata autorizzata come registrazione aziendale. Le registrazioni non autorizzate verranno bloccate.

I metodi seguenti si qualificano per essere autorizzati come registrazione aziendale Windows:
 - L'utente che esegue la registrazione usa un [account del manager di registrazione dispositivi]( device-enrollment-manager-enroll.md).
- Il dispositivo viene registrato tramite [Windows AutoPilot](enrollment-autopilot.md).
- Il dispositivo viene registrato con Windows Autopilot ma non è un'opzione solo registrazione al software MDM dalle impostazioni di Windows.
- Il numero IMEI del dispositivo è indicato in **Registrazione del dispositivo** > **[Identificatori dei dispositivi aziendali](corporate-identifiers-add.md)**. (Funzionalità non supportata per Windows Phone 8.1.)
- Il dispositivo viene registrato tramite un [pacchetto di provisioning in blocco](windows-bulk-enroll.md).
- Il dispositivo viene registrato tramite la [registrazione automatica da SCCM per la co-gestione](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
Le registrazioni seguenti sono contrassegnate come aziendali da Intune, ma dal momento che non offrono all'amministratore di Intune il controllo per ogni dispositivo, verranno bloccate:
 - La [registrazione automatica al software MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con l'[aggiunta ad Azure Active Directory durante la configurazione di Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- La [registrazione automatica al software MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [aggiunta ad Azure Active Directory dalle impostazioni di Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Verranno bloccati anche i seguenti metodi di registrazione personale:
- La [registrazione automatica al software MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [aggiunta dell'account aziendale dalle impostazioni di Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Solo l'[opzione di registrazione MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) dalle impostazioni di Windows.

\* Questi elementi non verranno bloccati se la registrazione avviene con Autopilot.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi

È possibile modificare le impostazioni relative al numero di dispositivi tramite la procedura seguente:

1. Accedere al portale di Azure.
2. Selezionare **Altri servizi**, cercare **Intune** e quindi scegliere **Intune**.
3. Selezionare **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **Restrizione sul limite di dispositivi** scegliere la restrizione che si vuole impostare.
5. Selezionare **Limite di dispositivi** e quindi nell'elenco a discesa selezionare il numero massimo di dispositivi che un utente può registrare.
    ![Pannello delle restrizioni sul limite di dispositivi con le restrizioni sul limite del dispositivo](./media/device-restrictions-limit.png)
6. Selezionare **Salva**.


Durante le registrazioni BYOD viene visualizzata una notifica che informa gli utenti quando raggiungono il limite di dispositivi registrati. Ad esempio, in iOS la notifica è simile alla seguente:

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
