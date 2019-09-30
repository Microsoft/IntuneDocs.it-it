---
title: Eseguire la migrazione dell'accesso condizionale al portale di Azure
titleSuffix: Microsoft Intune
description: Riassegnare i criteri di accesso condizionale creati in precedenza nel portale di Intune classico al portale di Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36e7b8468e4ee9d1f6be71a82d18f066bd7568d4
ms.sourcegitcommit: 9110124a481160039d476cf0374a4fa0464a8509
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256207"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Riassegnare i criteri di accesso condizionale dal portale di Intune classico al portale di Azure

Con il nuovo portale di Azure, l'accesso condizionale offre supporto per più criteri per applicazione, insieme ad altre possibilità di personalizzazione. Se in precedenza sono stati creati criteri di accesso condizionale nel portale di Intune classico, è possibile eseguirne la migrazione al portale di Azure. 

## <a name="before-you-begin"></a>Prima di iniziare

Quando si è pronti per passare al portale di Azure, seguire la procedura descritta in questo argomento per riassegnare i criteri di accesso condizionale creati in precedenza nel portale di Intune classico:

- Raccogliere i criteri di accesso condizionale creati in precedenza, in modo che siano note le impostazioni da riassegnare in un secondo momento.

- Seguire i passaggi illustrati in questo argomento per ricreare tali criteri nel portale di Azure.

- Disabilitare i criteri condizionali nel portale classico di Intune dopo avere verificato che i nuovi criteri funzionino come previsto nel portale di Azure.
<br /><br />
  - **Prima di disabilitare** i criteri di accesso condizionale nel portale di Intune classico, pianificare come spostare gli utenti nei criteri nuovi. È possibile seguire due approcci:
<br /><br />
    - **Usare lo stesso gruppo di inclusione per applicare i criteri creati nel portale di Azure e creare un nuovo gruppo di esenzione da usare con i criteri applicati dal portale di Intune classico**.
      - Spostare progressivamente alcuni utenti nel gruppo di esenzione specificato nel portale classico. Ciò impedisce che vengano applicati i criteri assegnati dal portale di Intune classico. Oltre ai criteri del portale di Intune classico, vengono anche applicati i criteri creati e assegnati allo stesso gruppo di utenti nel portale di Azure. 
<br /><br />
    - **Creare un nuovo gruppo a cui assegnare i criteri di accesso condizionale nel portale di Azure**. Se si sceglie questo approccio, è necessario eseguire le operazioni seguenti:
      - Rimuovere gradualmente gli utenti dai gruppi di sicurezza che hanno criteri di accesso condizionale assegnati nel portale di Intune classico.
      - Dopo aver verificato che i nuovi criteri funzionano per tali utenti, è possibile disabilitare i criteri nel portale di Intune classico. 
<br /><br />
- Se le impostazioni dei criteri di accesso condizionale erano state configurate per usare Exchange ActiveSync (EAS) nel portale di Intune classico, vedere le [istruzioni in questo argomento](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) per **riassegnare le impostazioni dei criteri di accesso condizionale EAS nel portale di Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Per verificare i criteri di accesso condizionale basati sui dispositivi nel portale di Intune classico

1. Passare al [portale di Intune classico](https://manage.microsoft.com) e accedere con le proprie credenziali.

2. Scegliere **Criteri** dal menu a sinistra.

3. Scegliere **Accesso condizionale** e quindi selezionare il servizio cloud Microsoft (ad esempio Exchange Online o SharePoint Online) per cui sono stati creati i criteri di accesso condizionale.

4. Prendere nota delle impostazioni di accesso condizionale e farvi riferimento durante la creazione degli stessi criteri di accesso condizionale nel portale di Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Interazione dei criteri di accesso condizionale basati sul dispositivo e basati sull'app

Il pannello **Protezione app di Intune**  nel portale di Azure consente agli amministratori di impostare regole condizionali basate su app, in modo che solo le app che supportano i criteri di protezione delle app di Intune possano accedere alle risorse aziendali. È possibile scegliere di sovrapporre questi criteri di accesso condizionale basati su app usando i criteri di accesso condizionale basati su dispositivo. È possibile combinare i criteri condizionali basati su dispositivo e app (AND logico) oppure specificare uno o l'altro tipo di criteri (OR logico). Se i requisiti dei criteri di accesso condizionale prevedono di:

- Richiedere un dispositivo conforme **E** usare l'app approvata.
  - È necessario impostare i criteri di accesso condizionale tramite il [pannello Accesso condizionale di Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e il [pannello Protezione app di Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Richiedere un dispositivo conforme **O** usare l'app approvata.
  - È necessario impostare i criteri di accesso condizionale tramite il [portale di Intune classico](https://manage.microsoft.com) e il [pannello Protezione app di Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Questo argomento include screenshot che confrontano l'esperienza utente con il portale di Intune classico e con il portale di Azure.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Riassegnare i criteri di accesso condizionale basati su dispositivo di Intune

1. Passare al pannello [Accesso condizionale](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) nel portale di Azure e accedere con le proprie credenziali.

2. Scegliere **Nuovo criterio**.

3. Specificare un nome per il criterio.

4. Scegliere **Utenti e gruppi** nella sezione **Assegnazioni** per assegnare i nuovi criteri di accesso condizionale.

    ![Immagine che confronta l'interfaccia utente per i gruppi di utenti tra i portali di Intune e di Azure](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > La selezione eseguita per il portale di Azure deve corrispondere alla selezione eseguita per il portale classico. Ad esempio, se sono selezionati tutti gli utenti nel portale di Intune classico, selezionare **Tutti gli utenti** nel portale di Azure. Inoltre, se è stata scelta l'opzione **Gruppi esenti** nel portale di Intune classico, escludere tali gruppi anche nel portale di Azure.

5. Dopo aver scelto il gruppo, fare clic su **Seleziona** e quindi su **Fine**.

6. Scegliere **App cloud** nella sezione **Assegnazioni**.

7. Nel pannello **App cloud**, scegliere **Seleziona app**.

8. Scegliere l'app a cui si vuole applicare i nuovi criteri di accesso condizionale e fare clic su **Seleziona**.

9. Fare clic su **Fine**.

    ![Immagine del confronto dell'interfaccia utente per le app cloud tra i portali di Intune e di Azure](./media/reassign-ca-3.png)

    > [!TIP] 
    > Se si hanno più app con gli stessi criteri, valutare la possibilità di consolidarli in un singolo set di criteri nel portale di Azure.

10. Scegliere **Condizioni** nella sezione **Assegnazioni**.

11. Nel pannello **Condizioni** scegliere **Piattaforme dei dispositivi** e quindi scegliere le piattaforme dei dispositivi applicabili.

12. Dopo aver scelto le piattaforme dei dispositivi, fare clic su **Fine** due volte.

    ![Immagine che confronta l'interfaccia utente della piattaforma dei dispositivi con i portali di Intune e di Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Se sono state scelte singole piattaforme nel portale di Intune classico, scegliere le singole piattaforme nel portale di Azure.

    > [!NOTE] 
    > È possibile specificare le opzioni di aggiunta al dominio o di conformità per Windows in un secondo momento.

13. Scegliere **Condizioni** nella sezione **Assegnazioni**.

14. Nel pannello **Condizioni** scegliere **App client** e quindi scegliere l'app client applicabile.

15. Dopo aver scelto l'app client, fare clic su **Fine** due volte.

    ![Immagine che confronta l'interfaccia utente delle app client tra i portali di Intune e di Azure](./media/reassign-ca-6.png)

16. Se sono state scelte le impostazioni del browser nel portale di Intune classico, selezionare **Browser** e **App per dispositivi mobili e client desktop** nel portale di Azure. Nel caso in cui non siano state scelte le impostazioni del browser nel portale di Intune classico, scegliere solo **App per dispositivi mobili e client desktop**. 

17. Scegliere **Concedi** nella sezione **Controlli di accesso**.

18. Scegliere **Richiedi che i dispositivi siano contrassegnati come conformi** in **Concedi controlli di accesso** e quindi fare clic su **Seleziona**.

19. In presenza di criteri che richiedono che i dispositivi Windows siano aggiunti a un dominio e se sono anche consentiti i dispositivi Windows conformi e registrati in Intune, scegliere **Richiedi dispositivo aggiunto a un dominio** e **Richiedi che i dispositivi siano contrassegnati come conformi** insieme a **Richiedi uno dei controlli selezionati**.

20. Se i dispositivi Windows conformi e registrati in Intune non sono consentiti, escludere i criteri Windows dai criteri correnti. Creare quindi criteri separati con **Piattaforma dei dispositivi** impostata su **Windows**, includere le altre condizioni come specificato precedentemente e scegliere **Richiedi dispositivo aggiunto a un dominio** nella sezione **Concedi controlli di accesso**.

21. Attivare l'opzione **Abilita criteri** nel pannello **Nuovo** dei criteri di accesso condizionale e quindi fare clic su **Crea**.

    ![Confrontare l'interfaccia utente dei criteri di accesso condizionale tra Intune e Azure](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Riassegnare i criteri di accesso condizionale basati su dispositivo di Intune per i client EAS

Se sono state configurate le impostazioni di Exchange ActiveSync come parte dei criteri di Exchange Online nel portale di Intune classico, è necessario creare un secondo set di criteri di accesso condizionale nel portale di Azure.

1. Passare al pannello [Accesso condizionale](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) nel portale di Azure e accedere con le proprie credenziali.

2. Scegliere **Nuovo criterio**.

3. Specificare un nome per il criterio.

4. Scegliere **Utenti e gruppi** nella sezione **Assegnazioni** per assegnare i nuovi criteri di accesso condizionale.

    ![Immagine del confronto dell'interfaccia utente per i gruppi di utenti tra i portali di Intune e di Azure](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > La selezione effettuata per il portale di Azure deve corrispondere alla selezione effettuata per il portale di Azure. Ad esempio, se sono selezionati tutti gli utenti nel portale di Intune classico, selezionare **Tutti gli utenti** nel portale di Azure. Inoltre, se è stata scelta l'opzione **Gruppi esenti** nel portale di Intune classico, escludere tali gruppi anche nel portale di Azure.

5. Dopo aver scelto il gruppo, fare clic su **Seleziona** e quindi su **Fine**.

6. Scegliere **App cloud** nella sezione **Assegnazioni**.

7. Nel pannello **App cloud**, fare clic su **Seleziona app** e scegliere **Exchange Online**. Fare quindi clic su **Seleziona** e su **Fine**.

    ![Immagine del confronto dell'interfaccia utente per le app cloud tra i portali di Intune e di Azure](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > I criteri di accesso condizionale per i client EAS non possono includere altre app cloud.

8. Nel pannello **Condizioni** scegliere **App client** e quindi scegliere l'app client applicabile. Se si è scelto di bloccare i client che non sono supportati da Intune, usare l'opzione **Applica i criteri solo alle piattaforme supportate**.

    ![Immagine del confronto dell'interfaccia utente delle app client tra i portali di Intune e di Azure](./media/reassign-ca-15.png)

9. Dopo aver scelto l'app client, fare clic su **Fine** due volte.

10. Scegliere **Concedi** nella sezione **Controlli di accesso**.

11. Scegliere **Richiedi che i dispositivi siano contrassegnati come conformi** in **Concedi controlli di accesso** e quindi fare clic su **Seleziona**.

    ![Immagine che confronta l'interfaccia utente per la concessione dell'accesso tra i portali di Intune e di Azure](./media/reassign-ca-16.png)

12. Attivare l'opzione **Abilita criteri** nel pannello **Nuovo** dei criteri di accesso condizionale e quindi fare clic su **Crea**.

    ![Confronto dell'interfaccia utente di abilitazione dei criteri di accesso condizionale tra Intune e Azure](./media/reassign-ca-17.png)

> [!NOTE]
> Se si configurano **Piattaforme del dispositivo**, quando si tenta di salvare i criteri verrà visualizzato l'errore "La configurazione dei criteri non è supportata". Exchange ActiveSync non riesce a identificare la piattaforma in uso dal dispositivo che esegue la connessione. Pertanto, la configurazione di piattaforme del dispositivo specifiche non è supportata per la creazione di criteri per i dispositivi Exchange ActiveSync.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Disabilitare i criteri di accesso condizionale nel portale di Intune classico

Dopo aver riassegnato i criteri di accesso condizionale nel portale di Azure, è importante disabilitare gradualmente i criteri di accesso condizionale creati in precedenza nel portale di Intune classico. Inoltre, potrebbe essere necessario usare lo stesso gruppo di sicurezza per applicare i criteri di accesso condizionale creati nel portale di Azure.

> [!NOTE]
> Prima di disabilitare i criteri di accesso condizionale nel portale di Intune classico, vedere la sezione [Prima di iniziare](#before-you-begin) all'inizio di questo argomento.

### <a name="to-disable-the-conditional-access-policies"></a>Per disabilitare i criteri di accesso condizionale

Poiché la gestione di dispositivi mobili è stata rimossa dal portale di Intune classico, è stato aggiunto il collegamento seguente per visualizzare/disabilitare questi criteri classici:

https://portal.azure.com/?microsoft_aad_iam_classicPolicyDontHide=true#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/ClassicPolicies

## <a name="see-also"></a>Vedere anche

- [Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
- [Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
