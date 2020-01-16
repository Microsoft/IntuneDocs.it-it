---
title: Criteri di Microsoft Intune per consentire o bloccare le app per Samsung Knox
titleSuffix: ''
description: Creare un profilo personalizzato per consentire e bloccare le app per dispositivi Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207078"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Usare criteri personalizzati in Microsoft Intune per consentire e bloccare le app per dispositivi Samsung Knox Standard 

Seguire la procedura riportata in questo articolo per creare criteri Microsoft Intune personalizzati allo scopo di creare uno degli elementi seguenti:

- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Le app presenti in questo elenco sono bloccate e non possono essere eseguite, anche se al momento dell'applicazione del criterio erano già state installate .
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. È possibile installare soltanto le app elencate. Non sarà possibile installare altre app dallo Store.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creare un elenco di app consentite o bloccate

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Un nome di profilo valido, ad esempio, è **profilo personalizzato di Windows Phone**.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **Piattaforma**: Selezionare **Android**.
    - **Tipo di profilo**: selezionare **personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    Per un elenco di app la cui esecuzione è bloccata nel dispositivo:

    - **Nome**: Immettere **PreventStartPackages**.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuare il profilo. Ad esempio, immettere **l'elenco delle app che non sono in esecuzione**.
    - **OMA-URI (maiuscole/minuscole)**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
    - **Tipo di dati**: selezionare **stringa**.
    - **Valore**: Immettere l'elenco dei nomi di pacchetti che si vuole consentire. Come delimitatore è possibile usare `;`, `:` o `|`. Immettere ad esempio `package1;package2;`.

   Per un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store, escludendo tutte le altre app, specificare le informazioni seguenti:

    - **Nome**: Immettere **AllowInstallPackages**.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuare il profilo. Ad esempio, immettere un **elenco di app che gli utenti possono installare da Google Play**.
    - **OMA-URI (maiuscole/minuscole)**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
    - **Tipo di dati**: selezionare **stringa**.
    - **Valore**: Immettere l'elenco dei nomi di pacchetti che si vuole consentire. Come delimitatore è possibile usare `;`, `:` o `|`. Immettere ad esempio `package1;package2;`.

5. Selezionare **OK** per salvare le modifiche.
6. Al termine, selezionare **OK** > **Crea** per creare il profilo di Intune. Una volta completata l'operazione, il profilo viene visualizzato nell'elenco **Dispositivi - Profili di configurazione**.

>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

Alla successiva verifica del dispositivo assegnato vengono applicate le impostazioni dell'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
