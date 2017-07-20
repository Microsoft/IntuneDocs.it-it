---
title: Introduzione ai criteri
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 232ec25c34df5e71f70737ca5f0f8a2ef12a05f0
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-policies"></a>Introduzione ai criteri

Uno degli obiettivi principali dell'introduzione a Intune è la registrazione dei dispositivi per assicurarsi che siano conformi con i criteri aziendali. I criteri di conformità non solo consentono di gestire tipi di dispositivi specializzati, ad esempio chioschi multimediali di proprietà dell'azienda, ma anche dispositivi personali (BYOD), tablet e dispositivi senza utente associato.

![Dashboard di conformità con pochi dati](/intune/media/generic-compliance-dashboard.png)

I criteri di conformità offrono le funzionalità di gestione seguenti per i dispositivi mobili seguenti:

* Regolare il numero di dispositivi registrati da ogni utente
* Gestire le impostazioni dei dispositivi, ad esempio la crittografia a livello di dispositivo, la lunghezza delle password, l'uso della fotocamera e così via
* Distribuire app, profili di posta elettronica, profili VPN e così via.
* Valutare i criteri a livello del dispositivo per i criteri di conformità di sicurezza

I criteri di conformità vengono creati separatamente per ogni piattaforma. In questa esercitazione vengono illustrati i criteri per iOS. I criteri seguenti sono disponibili per i dispositivi iOS:

* Configurazione di PIN o password
* Crittografia dispositivo
* Dispositivo Jailbroken
* Profilo di posta elettronica
* Versione minima del sistema operativo
* Versione massima del sistema operativo

__Come si creano i criteri?__

1. Accedere al [portale di Azure](https://portal.azure.com).
2. In **Cerca risorse** cercare **Intune**.
3. Selezionare **Conformità del dispositivo**.
4. Nel pannello **Conformità del dispositivo** selezionare **Criteri**.
5. Selezionare **Crea criteri**, quindi specificare i dettagli, ad esempio **Nome** e **Descrizione**. Scegliere **iOS** come **Piattaforma**.
6. In **Impostazioni** selezionare **Sicurezza del sistema**, quindi impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Richiedi**. È possibile impostare anche altre regole, ad esempio **Lunghezza minima password**, **Tipo di password richiesto** e **Numero di caratteri non alfanumerici nella password**. Dopo aver terminato l'impostazione dei criteri, selezionare **OK**.
7. Tornare al pannello **Crea criteri**, quindi selezionare **Crea**.
8. Dopo aver creato i criteri, selezionare **Assegnazioni** per assegnarli al gruppo di test. Selezionare il gruppo di test che include l'utente di test e assegnare i criteri al gruppo facendo clic su **Salva**.
9. Attendere qualche minuto. Il dispositivo registrato dovrebbe richiedere di aggiornare la password per garantire la conformità ai criteri aziendali. È possibile verificare questa operazione anche manualmente nell'**app Portale aziendale per iOS** toccando il nome del dispositivo e il pulsante **Sincronizza**.
