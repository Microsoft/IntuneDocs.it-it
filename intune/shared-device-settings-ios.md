---
title: Personalizzare la schermata di blocco nei dispositivi iOS con Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Informazioni sulle impostazioni di Microsoft Intune che consentono di visualizzare informazioni nella schermata di blocco dei dispositivi iOS tramite le impostazioni di configurazione dei dispositivi condivisi per iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203077"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Aggiungere messaggi personalizzati alla schermata di blocco e alla finestra di accesso nei dispositivi iOS con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Microsoft Intune che consentono di visualizzare informazioni nella schermata di blocco e nella finestra di accesso. 

Usare queste impostazioni per visualizzare un messaggio o un testo personalizzato nella finestra di accesso e nella schermata di blocco. È ad esempio possibile immettere il messaggio "In caso di ritrovamento, restituire a" e informazioni sul tag asset.

Queste impostazioni supportano dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **Nome** e una **Descrizione** per il profilo.
4. In **Piattaforma** selezionare **iOS**. In **Tipo di profilo** selezionare **Funzionalità del dispositivo**.
5. In **Impostazioni** selezionare **Messaggio della schermata di blocco (solo con supervisione)**. Configurare le seguenti impostazioni:

    - **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Immettere ad esempio `123xyz`.

        Il testo immesso viene visualizzato nella finestra di accesso e nella schermata di blocco di accesso del dispositivo.

    - **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. In questo campo è possibile immettere qualsiasi testo. Ad esempio, `If found, call Contoso at ...`.

    Per aggiungere informazioni specifiche del dispositivo in questi campi è anche possibile usare token di dispositivo. Per visualizzare, ad esempio, il numero di serie, immettere `Serial Number: {{serialnumber}}`. Nella schermata di blocco il testo è simile a `Serial Number 123456789ABC`. Quando si immettono le variabili, assicurarsi di usare le parentesi graffe `{{ }}`. I [token di configurazione delle app](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includono un elenco delle variabili che è possibile usare. È anche possibile usare `deviceName` o qualsiasi altro valore specifico del dispositivo.

6. Al termine, selezionare **OK** > **OK** > **Crea**. Il profilo viene visualizzato nell'elenco.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
