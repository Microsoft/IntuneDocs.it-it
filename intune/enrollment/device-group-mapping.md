---
title: Raggruppare i dispositivi in categorie in Intune
titleSuffix: Microsoft Intune
description: Informazioni sul raggruppamento dei dispositivi in categorie per una gestione più semplice.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 114637478ffecd2cb88176d1d2304706665a3c22
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723203"
---
# <a name="categorize-devices-into-groups"></a>Raggruppare i dispositivi in categorie

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Per semplificare la gestione dei dispositivi, è possibile usare le categorie di dispositivi di Microsoft Intune per aggiungere automaticamente i dispositivi a gruppi basati su categorie definite dall'utente.

Le categorie dei dispositivi usano il flusso di lavoro seguente:
1. Creare categorie che gli utenti possano scegliere quando registrano i dispositivi.
2. Quando gli utenti registrano il loro dispositivo iOS e Android, devono scegliere una categoria nell'elenco delle categorie configurate. Per assegnare una categoria a un dispositivo Windows, gli utenti devono utilizzare il sito Web Portale aziendale.
3. È quindi possibile distribuire app e criteri a tali gruppi.

È possibile creare qualsiasi categoria di dispositivi desiderata. Ad esempio:
- Dispositivo POS
- Dispositivo di prova
- Vendite
- Contabilità
- Manager

## <a name="how-to-configure-device-categories"></a>Come configurare le categorie di dispositivi

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Passaggio 1: Creare categorie di dispositivi nel pannello Intune del portale di Azure
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo**.
2. Nel pannello **Registrazione del dispositivo** scegliere **Categorie di dispositivi**.
3. Nella pagina **Categorie di dispositivi** scegliere **Crea** per aggiungere una nuova categoria.
4. Nel pannello **Crea categoria di dispositivi** immettere un **Nome** per la nuova categoria e una **Descrizione** facoltativa.
5. Al termine, selezionare **Crea**. È possibile visualizzare la nuova categoria nell'elenco delle categorie.

Il nome della categoria di dispositivi verrà usato per la creazione dei gruppi di sicurezza di Azure Active Directory (Azure AD) nel passaggio 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Passaggio 2: Creare i gruppi di sicurezza di Azure Active Directory
In questo passaggio verranno creati gruppi dinamici nel portale di Azure, basati sulla categoria di dispositivi e sul nome della categoria di dispositivi.

Per continuare, vedere [Uso degli attributi per creare regole avanzate](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) nella documentazione di Azure Active Directory.

Usare le informazioni in questa sezione per creare un gruppo di dispositivi con una regola avanzata usando l'attributo **deviceCategory**. Ad esempio (**device.deviceCategory - eq** "*nome della categoria di dispositivi ottenuto dal portale di Azure*".

Dopo aver configurato i gruppi di dispositivi, e dopo che gli utenti hanno registrato i loro dispositivi, viene visualizzato un elenco delle categorie configurate. Dopo che gli utenti hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Visualizzare le categorie di dispositivi gestiti

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Dispositivi**.

2. In **Gestisci** selezionare **Tutti i dispositivi**.

3. Nell'elenco dei dispositivi esaminare la colonna **Categoria del dispositivo**.

Se la colonna **Categoria del dispositivo** non è visualizzata, selezionare **Colonne**. Scegliere una **Categoria del dispositivo** dall'elenco e quindi selezionare **Applica**.

### <a name="change-the-category-of-a-device"></a>Cambiare la categoria di un dispositivo

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Dispositivi**.
2. Nel pannello **Dispositivi** trovare la sezione **Gestisci** e scegliere **Tutti i dispositivi**.
3. Nell'elenco dei dispositivi scegliere il dispositivo desiderato. Quindi, nel pannello delle proprietà del dispositivo trovare la sezione **Gestisci** e scegliere **Proprietà**.
4. Nel pannello successivo è possibile modificare la **categoria del dispositivo** selezionato in uno dei nomi di categoria configurati in precedenza.

## <a name="after-you-configure-device-groups"></a>Dopo la configurazione dei gruppi di dispositivi

Quando gli utenti registrano il loro dispositivo iOS e Android devono scegliere una categoria nell'elenco delle categorie configurate. Dopo che hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di dispositivi di Intune o al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

Gli utenti in Windows devono usare il sito Web Portale aziendale per selezionare una categoria.

Indipendentemente dalla piattaforma, gli utenti possono sempre passare a portal.manage.microsoft.com dopo la registrazione del dispositivo. Richiedere all'utente di accedere al sito Web Portale aziendale e passare a **Dispositivi personali**. L'utente potrà scegliere un dispositivo registrato elencato nella pagina e quindi selezionare una categoria.

Dopo la scelta della categoria, il dispositivo viene automaticamente aggiunto al gruppo corrispondente creato. Se un dispositivo è già registrato prima che vengano configurate le categorie, l'utente visualizza una notifica sul dispositivo nel sito Web Portale aziendale. Ciò comunica all'utente di selezionare una categoria la volta successiva che accede all'app Portale aziendale su iOS o Android.

## <a name="further-information"></a>Altre informazioni
- È possibile modificare una categoria di dispositivo nel portale di Azure, ma è necessario aggiornare manualmente i gruppi di sicurezza di Azure AD che fanno riferimento a questa categoria.

- Se si elimina una categoria, per i dispositivi a essa assegnati viene visualizzato il nome di categoria **Non assegnati**.
