---
title: Criteri di Microsoft Intune per consentire o bloccare le app per Samsung Knox
titleSuffix: ''
description: Creare un profilo personalizzato per consentire e bloccare le app per dispositivi Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8486e121e6497eefdd2d098c2421f2f3b53b8a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734349"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Usare criteri personalizzati in Microsoft Intune per consentire e bloccare le app per dispositivi Samsung Knox Standard 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Seguire la procedura riportata in questo articolo per creare criteri Microsoft Intune personalizzati allo scopo di creare uno degli elementi seguenti:

- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Le app presenti in questo elenco sono bloccate e non possono essere eseguite, anche se al momento dell'applicazione del criterio erano già state installate .
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. È possibile installare soltanto le app elencate. Non sarà possibile installare altre app dallo Store.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creare un elenco di app consentite o bloccate

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
2. Nell'elenco del riquadro dei profili scegliere **Crea profilo**.
3. Nel riquadro **Crea profilo** immettere **Nome** e **Descrizione** (facoltativa) per il profilo di dispositivo.
2. Scegliere la **Piattaforma** **Android** e il **Tipo di profilo** **Personalizzato**.
3. Fare clic su **Impostazioni**.
3. Nel riquadro **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
4. Nella finestra di dialogo **Aggiungi o modifica impostazione URI OMA** specificare le impostazioni seguenti:

   Per un elenco di app la cui esecuzione è bloccata nel dispositivo:

   - **Nome**: immettere **PreventStartPackages**.
   - **Descrizione**: immettere una descrizione (facoltativa), ad esempio "Elenco delle app bloccate".
   - **Tipo di dati**: scegliere **Stringa** dall'elenco a discesa.
   - **URI OMA**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   - **Valore**: immettere l'elenco dei nomi di pacchetti di app che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|** . (Esempio: pacchetto1;pacchetto2;)

   Per un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store, escludendo tutte le altre app, specificare le informazioni seguenti:
   - **Nome**: immettere **AllowInstallPackages**.
   - **Descrizione**: immettere una descrizione (facoltativa), ad esempio "Elenco delle app che gli utenti possono installare da Google Play".
   - **Tipo di dati**: scegliere **Stringa** dall'elenco a discesa.
   - **URI OMA**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Valore**: immettere l'elenco dei nomi di pacchetti di app che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|** . (Esempio: pacchetto1;pacchetto2;)

4. Fare clic su **OK** e nel riquadro **Crea profilo** scegliere **Crea**.

>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

Alla successiva verifica del dispositivo assegnato verranno applicate le impostazioni dell'applicazione.


<!---## Assign the custom profile--->
