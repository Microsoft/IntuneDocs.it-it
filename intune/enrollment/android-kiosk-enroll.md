---
title: Configurare la registrazione in Intune per dispositivi Android Enterprise dedicati
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android Enterprise dedicati in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc884850b70ff7621224c5b01a68d016f27504e
ms.sourcegitcommit: 5932da3ed8f52c7b0f0d71c1801f81c85952cf0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923382"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise supporta dispositivi in modalità tutto schermo di proprietà aziendale a uso singolo tramite un set di soluzioni per dispositivi dedicato. Questo tipo di dispositivi vengono usati per un singolo scopo, ad esempio la firma digitale, la stampa di biglietti o la gestione di inventari. Gli amministratori bloccano l'utilizzo di un dispositivo per un set limitato di app e collegamenti Web. Viene anche impedito agli utenti di aggiungere altre app o eseguire altre azioni sul dispositivo.

Intune consente di distribuire app e impostazioni in dispositivi Android Enterprise dedicati. Per informazioni dettagliate su Android Enterprise, vedere [Requisiti per Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

I dispositivi gestiti in questo modo vengono registrati in Intune senza un account utente e non sono associati ad alcun utente finale. Non sono progettati per le applicazioni o le app a uso personale che richiedono dati di account specifici dell'utente, ad esempio Outlook o Gmail.

## <a name="device-requirements"></a>Requisiti dei dispositivi

Per essere gestiti come dispositivi dedicati Android Enterprise, i dispositivi devono soddisfare i requisiti seguenti:

- Sistema operativo Android versione 5.1 e successive.
- I dispositivi devono eseguire una distribuzione di Android che include la connettività Google Mobile Services (GMS). I dispositivi devono includere GMS e devono essere in grado di connettersi a GMS.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Configurare la gestione di dispositivi dedicati Android Enterprise

Per configurare la gestione di dispositivi dedicati Android Enterprise, seguire questa procedura:

1. Per preparare la gestione dei dispositivi mobili è necessario [impostare l'autorità MDM (Mobile Device Management) su **Microsoft Intune**](../fundamentals/mdm-authority-set.md). Questa opzione viene impostata una sola volta, ovvero quando si configura per la prima volta Intune per la gestione dei dispositivi mobili.
2. [Connettere l'account del tenant di Intune all'account di Google Play gestito](connect-intune-android-enterprise.md).
3. [Creare un profilo di registrazione.](#create-an-enrollment-profile)
4. [Creare un gruppo di dispositivi](#create-a-device-group).
5. [Registrare i dispositivi dedicati](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Creare un profilo di registrazione

> [!NOTE]
> Se un token è scaduto, il profilo associato non verrà visualizzato in **Registrazione dispositivi** > **Registrazione Android** > **Dispositivi dedicati di proprietà aziendale**. Per visualizzare tutti i profili associati a token attivi e inattivi, fare clic su **Filtro** e selezionare le caselle per gli stati dei criteri "Attivo" e "Inattivo". 

Per poter registrare i dispositivi dedicati, è necessario creare un profilo di registrazione. Il profilo creato fornisce un token di registrazione (stringa casuale) e un codice a matrice (codice QR). A seconda del sistema operativo Android e della versione del dispositivo, per [registrare il dispositivo dedicato](#enroll-the-dedicated-devices) è possibile usare il token o un codice a matrice.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e scegliere **Registrazione dispositivi** > **Registrazione Android** > **Dispositivi dedicati di proprietà aziendale**.
2. Scegliere **Crea** e compilare i campi obbligatori.
    - **Nome**: digitare un nome che verrà usato per l'assegnazione del profilo al gruppo di dispositivi dinamico.
    - **Data di scadenza del token**: data in cui il token scade. Google impone un massimo di 90 giorni.
3. Scegliere **Crea** per salvare il profilo.

### <a name="create-a-device-group"></a>Creare un gruppo di dispositivi

È possibile assegnare le app e i criteri a gruppi di dispositivi assegnati o dinamici. Per configurare gruppi di dispositivi AAD dinamici per popolare automaticamente i dispositivi registrati con un profilo di registrazione specifico, seguire questa procedura:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e scegliere **Gruppi** > **Tutti i gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo** compilare i campi obbligatori come segue:
    - **Tipo di gruppo**: Sicurezza
    - **Nome gruppo**: digitare un nome intuitivo, ad esempio Factory 1
    - **Tipo di appartenenza**: Dispositivo dinamico
3. Scegliere **Aggiungi query dinamica**.
4. Nel pannello **Regole di appartenenza dinamica** compilare i campi come segue:
    - **Aggiungi regola di appartenenza dinamica**: Regola semplice
    - **Aggiungi dispositivi dove**: enrollmentProfileName
    - Nella casella centrale scegliere **Uguale a**.
    - Nell'ultimo campo immettere il nome del profilo di registrazione creato in precedenza.
    Per altre informazioni sulle regole di appartenenza dinamica, vedere [Regole di appartenenza dinamica per i gruppi in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Scegliere **Aggiungi query** > **Crea**.

### <a name="replace-or-remove-tokens"></a>Sostituire o rimuovere i token

- **Sostituisci il token**: è possibile generare un nuovo token o codice a matrice all'approssimarsi della scadenza usando Sostituisci il token.
- **Revoca il token**: è possibile far scadere immediatamente il token o il codice a matrice. Il token o codice a matrice non sarà più utilizzabile. È possibile usare questa opzione se:
  - il token o codice a matrice viene condiviso accidentalmente con un'entità non autorizzata
  - si completano tutte le registrazioni e il token o codice a matrice non è più necessario

La sostituzione o la revoca di un token o codice a matrice non avrà alcun effetto sui dispositivi già registrati.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e scegliere **Registrazione dispositivi** > **Registrazione Android** > **Dispositivi dedicati di proprietà aziendale**.
2. Scegliere il profilo che si vuole usare.
3. Scegliere **Token**.
4. Per sostituire il token, scegliere **Sostituisci il token**.
5. Per revocare il token, scegliere **Revoca il token**.

## <a name="enroll-the-dedicated-devices"></a>Registrare i dispositivi dedicati

È ora possibile [registrare i dispositivi dedicati](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Gestione delle app nei dispositivi dedicati Android Enterprise

Nei dispositivi dedicati Android Enterprise è possibile installare soltanto app con il tipo di assegnazione [impostato su Obbligatoria](../apps/apps-deploy.md#assign-an-app). Le app vengono installate da Google Play Store gestito allo stesso modo dei dispositivi con profilo di lavoro Android Enterprise.

Le app vengono aggiornate automaticamente sui dispositivi gestiti quando lo sviluppatore pubblica un aggiornamento in Google Play.

Per rimuovere un'app dai dispositivi dedicati Android Enterprise, è possibile eseguire una delle operazioni seguenti:
- Eliminare la distribuzione dell'app obbligatoria.
- Creare una distribuzione di disinstallazione per l'app.

## <a name="next-steps"></a>Passaggi successivi
- [Distribuire app Android](../apps/apps-deploy.md)
- [Aggiungere criteri di configurazione di Android](../configuration/device-profiles.md)
