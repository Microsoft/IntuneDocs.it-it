---
title: Introduzione ai criteri in Microsoft Intune - Azure | Microsoft Docs
description: Creare criteri per la protezione dei dati aziendali e la gestione dei dispositivi che gli utenti finali usano per accedere alle risorse aziendali. Assegnare quindi i criteri ai gruppi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271525"
---
# <a name="get-started-with-creating-policies"></a>Introduzione alla creazione di criteri

I criteri di Intune sono un ottimo modo per registrare i dispositivi e assicurarsi che siano conformi ai criteri aziendali. I criteri di conformità sono utili per gestire tipi di dispositivi specializzati, ad esempio chioschi multimediali di proprietà dell'azienda, ma anche dispositivi personali (BYOD), tablet e dispositivi senza utente associato.

![Dashboard di conformità con pochi dati](/intune/media/generic-compliance-dashboard.png)

I dispositivi mobili possono essere gestiti tramite criteri di conformità, ad esempio per:

* Regolamentare il numero di dispositivi registrati da un utente in Intune
* Gestire le impostazioni dei dispositivi, ad esempio la crittografia a livello di dispositivo, la lunghezza delle password e l'uso della fotocamera
* Distribuire app, profili di posta elettronica, profili VPN e altro
* Valutare i criteri a livello del dispositivo per i criteri di conformità di sicurezza

I criteri di conformità vengono creati per ogni piattaforma, ad esempio iOS, Android, Windows e altre. Per questo esercizio usare iOS. I criteri seguenti sono disponibili per i dispositivi iOS:

* Configurazione di PIN o password
* Crittografia dispositivo
* Dispositivo Jailbroken
* Profilo di posta elettronica
* Versione minima del sistema operativo
* Versione massima del sistema operativo

## <a name="create-a-policy"></a>Creare un criterio

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
4. Immettere **Nome**  e **Descrizione** per il criterio. 
5. Selezionare **iOS** per **Piattaforma**.
6. In **Impostazioni** selezionare **Sicurezza del sistema** e quindi impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Richiedi**. 

    È anche possibile impostare altre regole, ad esempio: 
    - **Lunghezza minima password**
    - **Tipo di password richiesto**
    - **Numero di caratteri non alfanumerici nella password**
    
    Dopo aver completato la configurazione dei criteri selezionare **OK**.
  
7. Tornare a **Crea criterio** e selezionare **Crea**. Questo passaggio crea i criteri e li elenca in **Conformità del dispositivo** > **Criteri**.
8. Selezionare il nuovo criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
Scegliere Gruppi selezionati per visualizzare i gruppi di sicurezza di Azure AD esistenti. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

Per garantire la conformità con i nuovi criteri aziendali, dopo alcuni minuti, il dispositivo registrato richiede una password aggiornata. È possibile verificare manualmente la disponibilità dell'aggiornamento nell'**app Portale aziendale per iOS**. Aprire l'app Portale aziendale, selezionare il nome del dispositivo e quindi selezionare **Sincronizza**.

> [!NOTE]
> Possono essere richieste fino a otto ore per l'applicazione dei nuovi criteri per un gruppo di dispositivi dinamico a tutti i dispositivi nel gruppo.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione alla registrazione dei dispositivi](get-started-enroll.md): illustra l'esperienza di registrazione tramite la registrazione completa di un dispositivo iOS.

## <a name="learn-more"></a>Altre informazioni

* [Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)
* [Modi comuni per usare i criteri di accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
