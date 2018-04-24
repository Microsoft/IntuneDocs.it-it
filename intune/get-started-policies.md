---
title: Introduzione ai criteri di Microsoft Intune
titlesuffix: ''
description: Creare criteri per la protezione dei dati aziendali e la gestione dei dispositivi che gli utenti finali usano per accedere alle risorse aziendali.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 661ef25085892e299e45156f27b3d9db959577d4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-creating-policies"></a>Introduzione alla creazione di criteri

Uno degli obiettivi principali quando si inizia a prendere confidenza con Intune è la registrazione dei dispositivi per assicurarsi che siano conformi ai criteri aziendali. I criteri di conformità non solo consentono di gestire tipi di dispositivi specializzati, ad esempio chioschi multimediali di proprietà dell'azienda, ma anche dispositivi personali (BYOD), tablet e dispositivi senza utente associato.

![Dashboard di conformità con pochi dati](/intune/media/generic-compliance-dashboard.png)

Gestire i dispositivi mobili nelle aree seguenti tramite criteri di conformità:

* Regolare il numero di dispositivi registrati da ogni utente
* Gestire le impostazioni dei dispositivi, ad esempio la crittografia a livello di dispositivo, la lunghezza delle password e l'uso della fotocamera
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

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Selezionare **Conformità del dispositivo**.
4. Nel riquadro **Conformità del dispositivo** selezionare **Criteri**.
5. Selezionare **Crea criteri**, quindi specificare i dettagli, ad esempio **Nome** e **Descrizione**. 
6. Scegliere **iOS** come **Piattaforma**.
6. In **Impostazioni** selezionare **Sicurezza del sistema**, quindi impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Richiedi**. È possibile impostare anche altre regole, ad esempio **Lunghezza minima password**, **Tipo di password richiesto** e **Numero di caratteri non alfanumerici nella password**. Dopo aver terminato l'impostazione dei criteri, selezionare **OK**.
7. Tornare al riquadro **Crea criterio** e quindi selezionare **Crea**.
8. Dopo aver creato i criteri, selezionare **Assegnazioni** per assegnarli al gruppo di test. Selezionare il gruppo di test che include l'utente di test e assegnare i criteri al gruppo facendo clic su **Salva**.
9. Attendere qualche minuto. Il dispositivo registrato dovrebbe richiedere di aggiornare la password per garantire la conformità ai criteri aziendali. È possibile verificare questa operazione anche manualmente nell'**app Portale aziendale per iOS** toccando il nome del dispositivo e il pulsante **Sincronizza**.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione alla registrazione dei dispositivi](get-started-enroll.md): illustra l'esperienza di registrazione tramite la registrazione completa di un dispositivo iOS.

## <a name="learn-more"></a>Altre informazioni

* [Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)
* [Modi comuni per usare i criteri di accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
