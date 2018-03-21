---
title: Come includere i dispositivi in gruppi in Intune
titleSuffix: Microsoft Intune
description: "Informazioni sul raggruppamento dei dispositivi in categorie per una gestione più semplice."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d07b025881ea78299d617205ce5ba39bb92a1231
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>Raggruppamento dei dispositivi in categorie per una gestione più semplice

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le categorie di dispositivi di Microsoft Intune per aggiungere automaticamente i dispositivi ai gruppi sulla base di categorie specifiche, in modo da renderne più facile la gestione.

Le categorie dei dispositivi usano il flusso di lavoro seguente:
1. Creare categorie tra cui gli utenti possono scegliere quando registrano i dispositivi
2. Quando gli utenti finali registrano il loro dispositivo iOS e Android, devono scegliere una categoria nell'elenco delle categorie configurate. Per assegnare una categoria a un dispositivo Windows, gli utenti finali devono usare il sito Web Portale aziendale (vedere **Dopo la configurazione dei gruppi di dispositivi** in questo articolo per altri dettagli).
3. È quindi possibile distribuire app e criteri a tali gruppi.

È possibile creare qualsiasi categoria di dispositivi desiderata, ad esempio:
- Dispositivo POS
- Dispositivo di prova
- Vendite
- Contabilità
- Manager

## <a name="how-to-configure-device-categories"></a>Come configurare le categorie di dispositivi

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Passaggio 1: creare categorie di dispositivi nel pannello Intune del portale di Azure
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo**.
2. Nel pannello **Registrazione del dispositivo** scegliere **Categorie di dispositivi**.
3. Nella pagina **Categorie di dispositivi** scegliere **Crea** per aggiungere una nuova categoria.
4. Nel pannello **Crea categoria di dispositivi** immettere un **Nome** per la nuova categoria e una **Descrizione** facoltativa.
5. Al termine, fare clic su **Crea**. È possibile visualizzare la nuova categoria nell'elenco delle categorie.

Il nome della categoria di dispositivi verrà usato per la creazione dei gruppi di sicurezza di Azure Active Directory nel passaggio 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passaggio 2: creare i gruppi di sicurezza di Azure Active Directory
In questo passaggio verranno creati gruppi dinamici nel portale di Azure, basati sulla categoria dispositivi e sul nome della categoria dispositivi.

Per continuare, vedere l'articolo [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) nella documentazione di Azure Active Directory.

Usare le informazioni in questa sezione per creare un gruppo di dispositivi con una regola avanzata usando l'attributo **deviceCategory**. Ad esempio, (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

Dopo aver configurato i gruppi di dispositivi, e dopo che gli utenti hanno registrato i loro dispositivi, viene visualizzato un elenco delle categorie configurate. Dopo che gli utenti hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Come visualizzare le categorie di dispositivi gestiti

1.  Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Dispositivi**.

2.  In **Gestisci** fare clic su **Tutti i dispositivi**.

3.  Nell'elenco dei dispositivi esaminare la colonna **Categoria del dispositivo**.

Se la colonna **Categoria de dispositivo** non viene visualizzata, fare clic su **Colonne**, scegliere **Categoria del dispositivo** dall'elenco e quindi fare clic su **Applica**.

### <a name="to-change-the-category-of-a-device"></a>Per cambiare la categoria di un dispositivo

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Dispositivi**.
2. Nel pannello **Dispositivi** trovare la sezione **Gestisci** e scegliere **Tutti i dispositivi**.
3. Scegliere il dispositivo desiderato nell'elenco dei dispositivi, quindi nel pannello delle proprietà del dispositivo trovare la sezione **Gestisci** e scegliere **Proprietà**.
4. Nel pannello successivo è possibile modificare la **categoria del dispositivo** selezionato in uno dei nomi di categoria configurati in precedenza.

## <a name="after-you-configure-device-groups"></a>Dopo la configurazione dei gruppi di dispositivi

Quando gli utenti finali registrano il loro dispositivo iOS e Android, devono scegliere una categoria nell'elenco delle categorie configurate. Dopo che hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di dispositivi di Intune o al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

Gli utenti finali in Windows devono usare il sito Web Portale aziendale per selezionare una categoria.

Indipendentemente dalla piattaforma, gli utenti finali possono sempre passare a portal.manage.microsoft.com dopo la registrazione del dispositivo. Richiedere all'utente di accedere al sito Web del portale aziendale e passare a **Dispositivi personali**. L'utente potrà scegliere un dispositivo registrato elencato nella pagina e quindi selezionare una categoria.

Dopo la scelta della categoria, il dispositivo viene automaticamente aggiunto al gruppo corrispondente creato. Se un dispositivo è già registrato prima di configurare le categorie, l'utente finale vedrà una notifica sul dispositivo nel sito Web Portale aziendale che richiede di selezionare una categoria in occasione dell'accesso successivo all'app Portale aziendale su iOS e Android.

## <a name="further-information"></a>Altre informazioni
- È possibile modificare una categoria di dispositivo nel portale di Azure, ma è necessario aggiornare manualmente i gruppi di sicurezza di Azure Active Directory che fanno riferimento a questa categoria.

- Se si elimina una categoria, per i dispositivi a essa assegnati viene visualizzato il nome di categoria **Non assegnati**.
