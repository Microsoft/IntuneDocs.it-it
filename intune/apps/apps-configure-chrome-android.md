---
title: Configurare Google Chrome per dispositivi Android con Intune
titleSuffix: Microsoft Intune
description: Usare i criteri di configurazione di Intune con Google Chrome per dispositivi Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c02ea34417073091e2f2841b363edfb9966ce558
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205905"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Configurare Google Chrome per dispositivi Android con Intune 

È possibile usare criteri di configurazione di Intune per configurare Google Chrome per dispositivi Android. È possibile applicare automaticamente le impostazioni per l'app. È ad esempio possibile impostare segnalibri e URL specifici da bloccare o consentire.

## <a name="prerequisites"></a>Prerequisiti

- Il dispositivo Android Enterprise dell'utente deve essere registrato in Intune. Per altre informazioni, vedere [Configurare la registrazione dei dispositivi con profilo di lavoro Android Enterprise](~/enrollment/android-work-profile-enroll.md).
- Google Chrome viene aggiunto come app Google Play gestita. Per altre informazioni su Google Play gestito, vedere [Connettere l'account di Intune all'account di Google Play gestito](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Aggiungere l'app Google Chrome a Intune

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi** e quindi aggiungere l'app **Google Play gestito**.
3. Passare a Google Play gestito, eseguire una ricerca con **Google Chrome** e approvare.

    ![Cercare e approvare Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Assegnare Google Chrome a un gruppo utenti come tipo di app necessaria. Quando il dispositivo viene registrato in Intune, Google Chrome viene distribuito automaticamente.

Per altre informazioni sull'aggiunta di un'app Google Play gestita a Intune, vedere [App Google Play Store gestite](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-app-configuration-for-managed-ae-devices"></a>Aggiungere la configurazione dell'app per i dispositivi Android Enterprise gestiti

1. Dall'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Criteri di configurazione dell'app** > **Aggiungi** > **Dispositivi gestiti**.
2. Impostare i dettagli seguenti:
    - **Nome** - Nome del profilo che viene visualizzato nel portale di Azure.
    - **Descrizione** - Descrizione del profilo che viene visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**: questo valore è impostato su **Dispositivi gestiti**.
    - **Piattaforma**: selezionare **Android**.

    ![Aggiungere criteri di configurazione di Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Fare clic su **App associata** per visualizzare il riquadro delle **app associate**. Trovare e selezionare **Google Chrome**. Questo elenco contiene le [app Google Play gestite che sono state approvate e sincronizzate con Intune](~/apps/apps-add-android-for-work.md).

    ![Selezionare Google Chrome in App associata](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Fare clic su **Impostazioni di configurazione**, selezionare **Usa progettazione configurazione** e quindi fare clic su **Aggiungi** per selezionare le chiavi di configurazione.

    ![Aggiungere Usa progettazione configurazione](~/apps/media/apps-configure-chrome-android/configuration.png)

    Di seguito è riportato un esempio di impostazioni di uso frequente:
    - **Block access to a list of URLs** (Blocca accesso a un elenco di URL): `["*"]`
    - **Allow access to a list of URLs** (Consenti accesso a un elenco di URL): `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Segnalibri gestiti**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Incognito mode availability** (Disponibilità modalità in incognito): `Incognito mode disabled`

    Dopo l'aggiunta tramite Progettazione configurazione, le impostazioni di configurazione vengono elencate in una tabella. 

    ![Impostazioni comuni](~/apps/media/apps-configure-chrome-android/common-settings.png)

    Le impostazioni indicate sopra creano segnalibri e bloccano l'accesso a tutti gli URL ad eccezione di `baidu.com`, `yahoo.com`, `chromium.org` e `chrome://`.

5. Fare clic su **OK** e su **Aggiungi**  per aggiungere i criteri di configurazione a Intune.
6. Assegnare i criteri di configurazione a un gruppo utenti. Per altre informazioni, vedere [Assegnare app ai gruppi con Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Verificare le impostazioni del dispositivo

Dopo la registrazione del dispositivo Android con Android Enterprise, l'app Google Chrome gestita con l'icona della cartella verrà distribuita automaticamente.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Avviare Google Chrome. Si vedrà che le impostazioni sono state applicate.

   Segnalibri:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   URL bloccato:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   URL consentito:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Scheda in incognito:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Risoluzione dei problemi

1. Monitorare nel portale di Intune lo stato della distribuzione dei criteri.

    ![Monitorare lo stato della distribuzione dei criteri](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Avviare Google Chrome e visitare la pagina **chrome://policy**. È possibile verificare se le impostazioni vengono applicate.

    ![Verificare che le impostazioni vengano applicate](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Informazioni aggiuntive

- [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](~/app-configuration-policies-use-android.md)
- [Elenco dei criteri di Chrome Enterprise](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sui dispositivi Android Enterprise completamente gestiti, vedere [Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti](~/enrollment/android-fully-managed-enroll.md).
