---
title: Come usare le categorie di dispositivi in Intune
titleSuffix: Azure portal
description: Informazioni su come usare le categorie di dispositivi che gli utenti possono scegliere quando registrano i dispositivi in Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00becba338f9a64e341b0b6d220b1a4ace3b40a9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="map-device-groups"></a>Mappare gruppi di dispositivi


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le categorie di dispositivi di Microsoft Intune per aggiungere automaticamente i dispositivi ai gruppi sulla base di categorie specifiche, in modo da renderne più facile la gestione.

Le categorie dei dispositivi usano il flusso di lavoro seguente:
1. Creare categorie che gli utenti scelgono quando registrano i dispositivi
3. Quando gli utenti finali registrano il loro dispositivo iOS e Android, devono scegliere una categoria nell'elenco delle categorie configurate. Per assegnare una categoria a un dispositivo Windows, gli utenti finali devono usare il sito Web Portale aziendale (vedere **Dopo la configurazione dei gruppi di dispositivi** in questo argomento per altri dettagli).
4. È quindi possibile distribuire app e criteri a tali gruppi.

È possibile creare qualsiasi categoria di dispositivi desiderata, ad esempio:
- Dispositivo POS
- Dispositivo di prova
- Vendite
- Contabilità
- Manager

## <a name="how-to-configure-device-categories"></a>Come configurare le categorie di dispositivi

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Passaggio 1: creare categorie di dispositivi nel pannello Intune del portale di Azure
1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
3. Nel pannello **Registrazione del dispositivo** scegliere **Categorie di dispositivi**.
4. Nella pagina **Categorie di dispositivi** scegliere **Crea** per aggiungere una nuova categoria.
5. Nel pannello successivo immettere un **Nome** per la nuova categoria e una **Descrizione** facoltativa.
6. Al termine, fare clic su **Crea**. La categoria appena creata verrà visualizzata nell'elenco delle categorie.

Il nome della categoria di dispositivi verrà usato per la creazione dei gruppi di sicurezza di Azure Active Directory nel passaggio 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passaggio 2: creare i gruppi di sicurezza di Azure Active Directory
In questo passaggio verranno creati gruppi dinamici nel portale di Azure, basati sulla categoria dispositivi e sul nome della categoria dispositivi.

Per continuare, vedere l'argomento [Utilizzo degli attributi per creare regole avanzate](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) nella documentazione di Azure Active Directory. 

Usare le informazioni in questa sezione per creare un gruppo di dispositivi con una regola avanzata usando l'attributo **deviceCategory**. Ad esempio (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

Dopo aver configurato i gruppi di dispositivi, e dopo che gli utenti hanno registrato i loro dispositivi, viene visualizzato un elenco delle categorie configurate. Dopo che gli utenti hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Come visualizzare le categorie di dispositivi gestiti

1.  Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune del portale di Azure scegliere **Dispositivi e gruppi**.

3.  In **Gestisci** fare clic su **Tutti i dispositivi**.

4.  Nell'elenco dei dispositivi esaminare la colonna **Categoria**.

Se la colonna **Categoria** non viene visualizzata, fare clic su **Colonne**, scegliere **Categoria** dall'elenco e quindi fare clic su **Applica**.

### <a name="to-change-the-category-of-a-device"></a>Per cambiare la categoria di un dispositivo

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi e gruppi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Gestisci** > **Tutti i dispositivi**.
5. Scegliere il dispositivo desiderato nell'elenco dei dispositivi, quindi, nel pannello delle proprietà del dispositivo, scegliere **Gestisci** > **Proprietà**.
6. Nel pannello successivo è possibile modificare la **categoria del dispositivo** selezionato in uno dei nomi di categoria configurati in precedenza.

## <a name="after-you-configure-device-groups"></a>Dopo la configurazione dei gruppi di dispositivi

Quando gli utenti finali registrano il loro dispositivo iOS e Android, devono scegliere una categoria nell'elenco delle categorie configurate. Dopo che hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di dispositivi di Intune o al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

Per assegnare una categoria a un dispositivo Windows, gli utenti finali devono usare il sito Web Portale aziendale (portal.manage.microsoft.com) dopo aver registrato il dispositivo. In un dispositivo Windows, accedere al sito Web e passare a **Menu** > **Dispositivi personali**. Scegliere un dispositivo registrato elencato nella pagina e quindi selezionare una categoria. 

Dopo la scelta della categoria, il dispositivo viene automaticamente aggiunto al gruppo corrispondente creato. Se un dispositivo è già registrato prima di configurare le categorie, l'utente finale vedrà una notifica sul dispositivo nel sito Web Portale aziendale che richiede di selezionare una categoria in occasione dell'accesso successivo all'app Portale aziendale su iOS e Android.

## <a name="further-information"></a>Altre informazioni
- È possibile modificare una categoria di dispositivo nel portale di Azure, ma in questo caso, è necessario aggiornare manualmente i gruppi di sicurezza di Azure Active Directory che fanno riferimento a questa categoria.

- Se si elimina una categoria, per tutti i dispositivi a essa assegnati verrà visualizzato il nome di categoria **Non assegnati**.


