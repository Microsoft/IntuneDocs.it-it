---
title: Classificare i dispositivi con il mapping del gruppo di dispositivi | Microsoft Intune
description: "Usare il mapping del gruppo di dispositivi di Microsoft Intune per raggruppare i dispositivi in categorie specifiche in modo da renderne più facile la gestione."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 727d28cff074124b5401f6c2931f87df3a9d2d23
ms.openlocfilehash: 7b1c6f0e380c03d048686462682fc1cee85b7cfa


---

# Classificare i dispositivi con il mapping del gruppo di dispositivi in Microsoft Intune
Usare il **mapping del gruppo di dispositivi** di Microsoft Intune per raggruppare i dispositivi in categorie specifiche in modo da renderne più facile la gestione. 

Il mapping del gruppo di dispositivi usa il flusso di lavoro seguente:
1. Creare gruppi di dispositivi in Intune per ogni categoria che si vuole usare.
2. Configurare le regole del mapping del gruppo di dispositivi corrispondente alla categoria selezionata per il gruppo di dispositivi precedentemente creato.
3. Quando gli utenti finali registrano il loro dispositivo, devono scegliere una categoria tra quelle configurate. Dopo la selezione della categoria, il loro dispositivo verrà automaticamente aggiunto al corrispondente gruppo di dispositivi creato.
4. È possibile quindi usare i gruppi di dispositivi quando si distribuiscono i criteri e le app.

Alcuni esempi di categorie:
* Personal
* Dispositivo POS
* Dispositivo di prova
* Vendite
* Contabilità
* Manager

È possibile configurare tutte le categorie desiderate.

## Come configurare il mapping dei gruppi di dispositivi
1. Per ogni categoria di dispositivi da usare, creare un gruppo di dispositivi Intune. Per informazioni su come creare gruppi, vedere [Create groups to manage users and devices with Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md) (Creare gruppi per gestire utenti e dispositivi con Microsoft Intune).
2. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
3. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili**, quindi scegliere **Mapping del gruppo di dispositivi**.
4. Nella pagina **Mapping del gruppo di dispositivi** attivare il mapping del gruppo dei dispositivi.
5. Scegliere **Aggiungi** per creare una nuova regola di mapping.
6. Nella finestra di dialogo **Aggiungi una regola di mapping del gruppo di dispositivi** inserire il nome della categoria da creare e nell'elenco a discesa scegliere la raccolta di dispositivi a cui si vuole eseguire il mapping della categoria. Al termine, scegliere **Aggiungi**.
7. Dopo aver completato l'aggiunta di categorie e gruppi, scegliere **Salva**.

Da questo momento agli utenti che registrano i loro dispositivi viene visualizzato un elenco delle categorie configurate. Dopo aver scelto una categoria e completato la registrazione, il loro dispositivo viene aggiunto al gruppo di dispositivi corrispondente alla categoria selezionata.

### Vedere anche
[Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Aug16_HO5-->


