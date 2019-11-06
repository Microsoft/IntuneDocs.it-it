---
title: Messaggi dell'app Portale aziendale visualizzati dagli utenti nei dispositivi
titleSuffix: Microsoft Intune
description: Informazioni sui diversi messaggi che possono vedere gli utenti finali nell'app Portale aziendale.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57467d3d073666c1c22ac0a412f68a258d5b3d75
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414079"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Consentire agli utenti finali di comprendere i messaggi dell'app Portale aziendale

> [!NOTE]
> Le informazioni seguenti si applicano solo ai dispositivi Android 6.0 e versioni successive e iOS 10 e versioni successive.

Informazioni sui diversi messaggi dell'app che possono vedere gli utenti finali nell'app Portale aziendale. Questi messaggi vengono in genere visualizzati in diversi momenti durante il processo di registrazione. Informazioni su dove vengono visualizzati i messaggi, il significato dei messaggi e cosa accade se gli utenti negano l'accesso. Scoprire anche come spiegare in modo ottimale i messaggi agli utenti.

- __Allow Company Portal to make and manage phone calls? (Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?)__
- __Allow Company Portal to access photos, media, and files on your device?__ (Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?)

> [!NOTE]
> Microsoft non vende per alcun motivo a terze parti i dati raccolti dal servizio.

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?

### <a name="where-it-appears"></a>Dove viene visualizzato

Il testo del messaggio **Allow Company Portal to make and manage phone calls?** (Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?) viene visualizzato quando gli utenti toccano **Registra** nell'app Portale aziendale durante la registrazione del dispositivo.

### <a name="what-it-means"></a>Che cosa significa

Accettando questa richiesta, gli utenti acconsentono all'invio del numero di telefono e del codice IMEI del proprio dispositivo al servizio Intune. Questi valori verranno visualizzati nella pagina __Hardware__ della console di amministrazione.

> [!NOTE]
> **The Company Portal app never makes or manages phone calls!** (L'app Portale aziendale non effettua o gestisce mai chiamate telefoniche.) Il testo del messaggio è controllato da Google e non può essere modificato.

Per visualizzare la pagina **Hardware**, è necessario passare a **Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi**. Selezionare il dispositivo dell'utente e passare a **Visualizza proprietà** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso

Se gli utenti negano l'accesso, possono continuare a usare l'app Portale aziendale e registrare il proprio dispositivo. Tuttavia, il numero di telefono e il codice IMEI del dispositivo non verranno visualizzati nella pagina __Hardware__ della console di amministrazione. La seconda volta che gli utenti accedono all'app Portale aziendale dopo aver negato l'accesso, nel messaggio viene visualizzata la casella di controllo **Non visualizzare più questo messaggio** che è possibile selezionare per evitare di visualizzare di nuovo il messaggio.

Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio viene visualizzato all'accesso successivo all'app Portale aziendale dopo la registrazione.

Se gli utenti decidono di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.

### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti

Suggerire agli utenti di consultare l'articolo [Registrare il dispositivo Android in Intune](/intune-user-help/enroll-device-android-company-portal) per ottenere altre informazioni.

## <a name="allow-company-portal-to-access-your-contacts"></a>Consentire a Portale aziendale di accedere ai contatti?

### <a name="where-it-appears"></a>Dove viene visualizzato

Il messaggio **Allow Company Portal to access your contacts?** (Consentire a Portale aziendale di accedere ai contatti?) viene visualizzato quando l'utente tocca **Registra** nell'app Portale aziendale durante la registrazione del dispositivo.

### <a name="what-it-means"></a>Che cosa significa

Accettando questa richiesta, gli utenti consentono a Intune di creare il proprio account aziendale e gestire l'identità di Azure Active Directory registrata per l'utente nel dispositivo.

> [!NOTE]
> **Microsoft never accesses your contacts!** (Microsoft non accede mai ai contatti dell'utente.) Il testo del messaggio è controllato da Google e non può essere modificato.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso

Se gli utenti negano l'accesso, il dispositivo non verrà registrato in Intune e non può essere gestito. La seconda volta che gli utenti accedono all'app Portale aziendale dopo aver negato l'accesso, nel messaggio viene visualizzata la casella di controllo **Non visualizzare più questo messaggio** che è possibile selezionare per evitare di visualizzare di nuovo il messaggio.

Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato all'accesso successivo all'app Portale aziendale dopo la registrazione.

Se gli utenti decidono di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.

### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti

Suggerire agli utenti di consultare l'articolo [Registrare il dispositivo Android in Intune](/intune-user-help/enroll-device-android-company-portal) per ottenere altre informazioni.  

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

### <a name="where-it-appears"></a>Dove viene visualizzato

Il messaggio **Allow Company Portal to access photos, media, and files on your device?** (Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?) viene visualizzato quando gli utenti toccano **Invia dati** per inviare i log all'amministratore IT.

### <a name="what-it-means"></a>Che cosa significa

Accettando questa richiesta, gli utenti consentono al dispositivo di scrivere i log di dati nella scheda SD e viene anche abilitato lo spostamento dei log tramite un cavo USB.   

> [!NOTE]
> **The Company Portal app never accesses users' photos, media, and files!** (L'app Portale aziendale non accede mai a foto, elementi multimediali e file degli utenti.) Il testo del messaggio è controllato da Google e non può essere modificato.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso

Se gli utenti negano l'accesso, possono comunque inviare i log di dati tramite posta elettronica, ma questi non vengono copiati nella scheda SD del dispositivo.

Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio. Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo tentativo di invio dei log. Tuttavia, se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Archiviazione** e quindi attivare l'autorizzazione.


### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti

Suggerire agli utenti di consultare l'articolo [Inviare i log all'amministratore IT tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>È necessario che il supporto aziendale garantisca l'accesso alle risorse aziendali

### <a name="where-it-appears"></a>Dove viene visualizzato

Se l'app Portale aziendale non è stata aggiunta all'elenco **App consentite** o **Escludi le app** e un utente tenta di accedere, l'accesso avrà esito negativo. Verrà visualizzato il messaggio seguente:

> **È necessario che il supporto aziendale garantisca l'accesso alle risorse aziendali**  
> L'azienda usa i criteri di Windows Information Protection per proteggere il dispositivo. Il supporto aziendale dovrà assicurarsi di consentire all'app Portale aziendale di accedere a queste risorse.

### <a name="what-it-means"></a>Che cosa significa

Aggiungere il Portale aziendale all'elenco **App consentite** o **Escludi le app** tra i criteri di protezione delle app di Windows Information Protection (WIP). Per altre informazioni, vedere [Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](../apps/windows-information-protection-policy-create.md).

## <a name="approve-a-ios-company-app-line-of-business-app-on-your-ios-device"></a>Approvare un'app aziendale iOS (app line-of-business) nel dispositivo iOS 

### <a name="where-it-appears"></a>Dove viene visualizzato

Le app iOS sviluppate dall'organizzazione e non disponibili nell'App Store non sono considerate attendibili dal dispositivo per impostazione predefinita. Quando si installa un'app di questo tipo usando il portale aziendale e la si avvia, viene visualizzato il messaggio seguente:

![Messaggio dell'app iOS - Sviluppatore interno non attendibile](./media/end-user-company-portal-messages/end-user-company-portal-messages-01.png)

### <a name="what-it-means"></a>Che cosa significa

Questo messaggio indica che è necessario modificare le impostazioni del dispositivo iOS per approvare e installare un'app sviluppata dall'azienda nel dispositivo iOS.

Quando si installa un'app di questo tipo usando il portale aziendale e la si avvia, seguire questa procedura per approvare l'app dopo il download:

1. Dopo l'avvio di un'app aziendale (app line-of-business app) installata, viene visualizzato il messaggio "Sviluppatore interno non attendibile". <br>
   Premere **CANC**.
2. Passare a **Impostazioni** > **Generale** > **Gestione dei dispositivi**.

   ![Interfaccia utente del dispositivo iOS - Gestione dei dispositivi](./media/end-user-company-portal-messages/end-user-company-portal-messages-02.png)

3. Selezionare **Gestione profilo** > **App aziendale**.
4. Selezionare il nome dello sviluppatore.
5. Selezionare **Considera attendibile _nome sviluppatore_** .
6. Confermare l'app selezionando **Considera attendibile** nel messaggio popup di installazione dell'app.

   ![Interfaccia utente del dispositivo iOS - Messaggio di attendibilità dell'app](./media/end-user-company-portal-messages/end-user-company-portal-messages-03.png)

    Ora dovrebbe essere possibile avviare e usare l'app aziendale.


## <a name="see-also"></a>Vedere anche
[Informazioni sull'uso di Intune per gli utenti finali](end-user-educate.md)
