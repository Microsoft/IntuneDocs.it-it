---
title: Registro modifiche per il data warehouse di Intune
titlesuffix: Microsoft Intune
description: Questo argomento presenta un elenco di modifiche per l'API data warehouse di Microsoft Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/21/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7d69c602471e8508744f2a00008294cbd335204
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358259"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro modifiche per l'API data warehouse di Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Tenersi aggiornati con il data warehouse di Intune.

## <a name="1903"></a>1903
_Data di rilascio: marzo 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>Modifiche v1.0 reflection al beta
Quando si V1.0 è stata introdotta in 1808, differenziavano alcune differenze significative dalla versione beta API. Nel 1903 tali modifiche si rifletteranno nella versione beta dell'API. Se si dispone di importanti report che utilizzano la versione beta dell'API, è fortemente consigliabile passare tali report a V1.0 per evitare modifiche di rilievo. Consultare [le informazioni sulla versione API](reports-api-url.md) per altre informazioni sulle versioni di API Data Warehouse e la compatibilità. 

## <a name="1902"></a>1902 
_Data di rilascio: febbraio 2019_

### <a name="power-bi-compliance-app"></a>App di conformità di Power BI 

Accedere al Data Warehouse di Intune in Power BI Online usando il [conformità di Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) app. Con questa app di Power BI, è ora possibile accedere e condividere i report creati in precedenza senza alcuna configurazione e senza uscire dal web browser. 

> [!NOTE]
> Esistono due filtri aggiuntivi, che è possibile applicare all'app di conformità di Intune.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Aggiungere filtri aggiuntivi per l'app di conformità di Intune
1. Aprire il [conformità di Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) app nel browser web.
2. Fare clic su **dispositivi Non conformi** e selezionare **Non conforme** nel **complianceStatus** filtro. 
3. Fare clic su **dispositivi sconosciuti** e selezionare **non è ancora disponibile** nel **complianceStatus** filtro. 

## <a name="1812"></a>1812 
_Data di rilascio: dicembre 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Raccolta di attività di registrazione rilasciata nella versione 1.0 

La raccolta di attività di registrazione è ora disponibile nella versione 1.0. È possibile usare questa raccolta per conoscere le tendenze e il volume degli errori di registrazione nell'ambiente. Per altre informazioni, vedere [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) ed [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Data di rilascio: agosto 2018_

### <a name="v10-collections"></a>Raccolte v1.0  

È ora possibile usare la versione v1.0 del data warehouse di Intune, impostando il parametro di query `api-version=v1.0`. Gli aggiornamenti alle raccolte nel data warehouse sono additivi per progettazione e non causano interruzioni per gli scenari esistenti.

### <a name="enrollment-activities-collection-released-to-beta"></a>Raccolta di attività di registrazione rilasciata in versione beta

La nuova raccolta `Enrollment Activities` è stata rilasciata in versione beta. È possibile usare questa raccolta per comprendere come procede la registrazione visualizzando gli errori più comuni. 


## <a name="1805"></a>1805
_Data di rilascio: maggio 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Correzione del conteggio dei dispositivi nella raccolta **Dispositivi** 

È stata apportata una correzione alla raccolta **Dispositivi** che può ridurre il conteggio totale dei dispositivi filtrati tramite l'attributo `isDeleted`. Questa riduzione è il risultato della correzione e non si tratta di un errore. Per altre informazioni sulla raccolta **Dispositivi**, vedere le [informazioni di riferimento per le entità dispositivo](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Ultimo aggiornamento: gennaio 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autenticazione OAuth del data warehouse di Intune <!-- 1867540 -->

È possibile configurare un'applicazione con Azure Active Directory (Azure AD) ed eseguirne l'autenticazione nel data warehouse di Intune. Per altre informazioni, vedere [Autenticazione OAuth del data warehouse di Intune](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Requisiti delle credenziali di Azure AD e Intune <!-- 2077525 -->

- Non è più necessario assegnare una licenza di Intune all'utente quando accede al data warehouse di Intune (inclusa l'API).
- Il nome del ruolo Intune è stato modificato da **Report** a **Data warehouse di Intune**. 

    Per altre informazioni, vedere [Requisiti delle credenziali di Azure AD e Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Opzioni di query OData <!-- 2077711 -->

È possibile usare <code>$select</code> come parametro di query OData. La versione corrente supporta i seguenti parametri di query OData: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> e <code>$top</code>. Per altre informazioni, vedere [Opzioni di query OData](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nuove entità nel modello di dati del data warehouse <!-- 2077804 -->

 - È stata aggiunta l'entità [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md). **MobileAppDeviceUserInstallStatus** rappresenta lo stato di installazione di un'app per dispositivi mobili per un determinato dispositivo e utente.
 - È stata aggiunta l'entità [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate). L'entità **MobileAppInstallState** rappresenta lo stato di installazione per un'applicazione per dispositivi mobili dopo l'assegnazione a un gruppo che contiene dispositivi, utenti o entrambi. 

## <a name="1710"></a>1710
_Ultimo aggiornamento: novembre 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Una nuova raccolta di entità denominata Current User è limitata ai dati degli utenti attualmente attivi <!-- 1544273 -->

La raccolta di entità **Users** contiene tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione. In questi record sono inclusi gli stati utente registrati nel periodo di raccolta dei dati, anche se l'utente è stato rimosso. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

La nuova raccolta di entità **Current User**, invece, contiene solo gli utenti che non sono stati rimossi. La raccolta di entità **Current User**, quindi, è limitata agli utenti attualmente attivi. Per informazioni sulla raccolta di entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Ultimo aggiornamento: ottobre 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune <!-- 1187917 -->

Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato. Per altre informazioni, vedere [Associazione utente-dispositivo](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nuove entità nel modello di dati del data warehouse <!-- 1479526 --><!-- -->

 - È stata aggiunta l'entità [**UserDeviceAssociation**](reports-ref-user-device.md). L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione. Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi.  
 - Aggiunta l'entità [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md). **IntuneManagementExtension** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni, quali stato di installazione e versione.

## <a name="next-steps"></a>Passaggi successivi
 - Informazioni sulle [novità di Intune ogni settimana](whats-new.md), oltre a indicazioni su modifiche previste, avvisi importanti sul servizio e informazioni sulle versioni precedenti.
 - Leggere il [blog di Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
