---
title: Criteri di Intune per consentire o bloccare le app per Samsung KNOX
titleSuffix: Intune on Azure
description: Creare un profilo personalizzato per consentire e bloccare app per dispositivi Samsung KNOX Standard."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8245bb3fa8f08e719df903a70f079f4fdf534ca5
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX Standard in Microsoft Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]Seguire le procedure riportate in questo argomento per creare un criterio Microsoft Intune personalizzato allo scopo di creare uno degli elementi seguenti:

- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Le app presenti in questo elenco sono bloccate e non possono essere eseguite, anche se al momento dell'applicazione del criterio erano già state installate .
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. È possibile installare soltanto le app elencate. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creare un elenco di app consentite o bloccate

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
2. Nell'elenco del pannello dei profili scegliere **Crea profilo**.
3. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** (facoltativa) per questo profilo di dispositivo.
2. Scegliere un **Tipo di piattaforma** di **Android**e un tipo di profilo **personalizzato**.
3. Fare clic su **Impostazioni**.
3. Nel pannello **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
4. Nella finestra di dialogo **Aggiungi o modifica impostazione URI OMA** specificare quanto segue:

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>Per un elenco di app la cui esecuzione è bloccata nel dispositivo:

- **Nome**: immettere **PreventStartPackages**.
- **Descrizione**: immettere una descrizione (facoltativa), ad esempio "Elenco delle app bloccate".
-   **Tipo di dati**: scegliere **Stringa** dall'elenco a discesa.
-   **URI OMA**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
-   **Valore**: immettere l'elenco dei nomi di pacchetti di app che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|**. (Esempio: pacchetto1;pacchetto2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>Per un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store, escludendo tutte le altre app, specificare le informazioni seguenti:
- **Nome**: immettere **AllowInstallPackages**.
- **Descrizione**: immettere una descrizione (facoltativa), ad esempio "Elenco delle app che gli utenti possono installare da Google Play".
- **Tipo di dati**: scegliere **Stringa** dall'elenco a discesa.
- **URI OMA**: immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
- **Valore**: immettere l'elenco dei nomi di pacchetti di app che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|**. (Esempio: pacchetto1;pacchetto2;)

4. Fare clic su **OK**, quindi nel pannello **Crea profilo** scegliere **Crea**.

>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

Alla successiva verifica del dispositivo assegnato verranno applicate le impostazioni dell'applicazione.


<!---## Assign the custom profile--->
