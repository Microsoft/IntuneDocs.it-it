---
title: Classificare i dispositivi con il mapping del gruppo di dispositivi | Documentazione Microsoft
description: "Usare il mapping del gruppo di dispositivi di Microsoft Intune per raggruppare i dispositivi in categorie specifiche in modo da renderne più facile la gestione."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 28af253b0a0fe174478961810a26b45d8ac3d959

---

# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>Classificare i dispositivi con il mapping del gruppo di dispositivi in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare il **mapping del gruppo di dispositivi** di Microsoft Intune per aggiungere automaticamente i dispositivi ai gruppi sulla base di categorie specifiche, in modo da renderne più facile la gestione. 

Il mapping del gruppo di dispositivi usa il flusso di lavoro seguente:
1. Creare categorie che gli utenti scelgono quando registrano i dispositivi
2. È possibile creare gruppi o usare gruppi di dispositivi esistenti per ogni categoria che si vuole usare. A seconda della versione di Intune in uso, si tratterà di gruppi di Intune o di gruppi di sicurezza di Azure Active Directory.
2. Configurare le regole per il mapping della categoria scelta al gruppo di dispositivi creato in precedenza.
3. Quando gli utenti finali registrano il loro dispositivo, devono scegliere una categoria nell'elenco delle categorie configurate. Dopo la scelta della categoria, il loro dispositivo viene automaticamente aggiunto al gruppo corrispondente creato. Se un dispositivo è già registrato, quando l'utente torna ad accedere all'app Portale aziendale gli verrà richiesto di selezionare una categoria.
4. È quindi possibile distribuire app e criteri a tali gruppi.

È possibile creare qualsiasi categoria di dispositivi desiderata, ad esempio:
* Dispositivo POS
* Dispositivo di prova
* Vendite
* Contabilità
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Informazioni importanti su una modifica nella gestione dei gruppi per Intune

Sulla base del feedback ricevuto dagli utenti, è in corso l'unificazione delle modalità d'uso del raggruppamento e dell'assegnazione in Enterprise Mobility e Security. Per tale motivo, presto i gruppi di Intune verranno convertiti in gruppi di sicurezza basati su Azure Active Directory. Dopo questa modifica la creazione di gruppi non avverrà più con Intune. I gruppi verranno creati nel portale di Azure. Questa modifica verrà introdotta in modo graduale. Per informazioni dettagliate sulla modifica e sulle fasi previste, vedere [questo argomento](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>Quale delle procedure di questo argomento usare per configurare il mapping dei gruppi di dispositivi?

A causa dell'implementazione graduale dei gruppi di sicurezza basati su Azure Active Directory, per identificare la procedura da eseguire è necessario aprire l'area di lavoro **Gruppi** della [console di amministrazione di Intune](https://manage.microsoft.com):

-  Se viene visualizzato un collegamento al portale di Azure, i gruppi di Intune non sono più in uso. Seguire la procedura [Come configurare il mapping dei gruppi di dispositivi per i gruppi di Azure Active Directory](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups) di seguito.
-  Se non viene visualizzato un collegamento al portale di Azure, i gruppi di Intune sono ancora in uso. Seguire la procedura [Come configurare il mapping dei gruppi di dispositivi per i gruppi di Intune](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups) di seguito.

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>Come configurare il mapping dei gruppi di dispositivi per i gruppi di Intune
1. Per ogni categoria di dispositivi da usare, creare un gruppo di dispositivi Intune o identificare un gruppo esistente. Per informazioni su come creare gruppi, vedere [Create groups to manage users and devices with Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md) (Creare gruppi per gestire utenti e dispositivi con Microsoft Intune).
2. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
3. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili**, quindi scegliere **Mapping del gruppo di dispositivi**.
4. Nella pagina **Mapping del gruppo di dispositivi** attivare il mapping del gruppo dei dispositivi.
5. Scegliere **Aggiungi** per creare una nuova regola di mapping.
6. Nella finestra di dialogo **Aggiungi una regola di mapping del gruppo di dispositivi** inserire il nome della categoria da creare e nell'elenco a discesa scegliere la raccolta di dispositivi a cui si vuole eseguire il mapping della categoria. Al termine, scegliere **Aggiungi**.
7. Dopo aver completato l'aggiunta di categorie e gruppi, scegliere **Salva**.



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>Come configurare il mapping dei gruppi di dispositivi per i gruppi di Azure Active Directory

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>Passaggio 1: creare categorie di dispositivi nella console di amministrazione di Intune
1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
3. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili**, quindi scegliere **Categorie di dispositivi**.
4. Nella pagina **Categorie di dispositivi** un elenco consente di configurare le categorie di dispositivi: 
- È possibile immettere un nome e fare clic su **Aggiungi** per aggiungerlo come nuova categoria di dispositivi.
- È anche possibile selezionare una categoria ed eliminarla scegliendo **Elimina**.

Il nome della categoria di dispositivi verrà usato per la creazione dei gruppi di sicurezza di Azure Active Directory nel passaggio 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passaggio 2: creare i gruppi di sicurezza di Azure Active Directory

In questo passaggio verranno creati gruppi dinamici nel portale di Azure, basati sulla categoria dispositivi e sul nome della categoria dispositivi.

Per continuare, vedere l'argomento [Utilizzo degli attributi per creare regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) nella documentazione di Azure Active Directory.
Usare le informazioni in questo argomento per creare un gruppo di dispositivi con una regola avanzata usando l'attributo **deviceCategory**.
Ad esempio (**device.deviceCategory - eq** "<*nome della categoria di dispositivi ottenuto dalla console di amministrazione di Intune*>")


## <a name="after-you-configure-device-groups"></a>Dopo la configurazione dei gruppi di dispositivi

Quando gli utenti registrano i loro dispositivi visualizzano un elenco delle categorie configurate. Dopo che hanno scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di dispositivi di Intune o al gruppo di sicurezza di Active Directory corrispondente alla categoria selezionata.

### <a name="see-also"></a>Vedere anche
[Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


