---
title: App consentite e bloccate per KNOX
description: Personalizzare il profilo per creare un elenco di app consentite e bloccate per KNOX.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ee5279c91eeaa2d75044a156ebe9c4b100bd8047
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX Standard

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Seguire le procedure riportate in questo argomento per creare un criterio Microsoft Intune personalizzato allo scopo di creare uno degli elementi seguenti:

- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Le app presenti in questo elenco sono bloccate e non possono essere eseguite, anche se al momento dell'applicazione del criterio erano già state installate .
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. È possibile installare soltanto le app elencate. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX Standard.

## <a name="to-create-an-allowed-or-blocked-app-list"></a>Per creare un elenco di app consentite o bloccate

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Criteri** &gt; **Criteri di configurazione** &gt; **Aggiungi**.
2. Nella finestra di dialogo **Crea un nuovo criterio** espandere **Android**, scegliere **Configurazione personalizzata** e quindi **Crea criterio**.
3. Fornire un nome e una descrizione del criterio (facoltativa) e quindi, nella sezione **Impostazioni URI OMA**, scegliere **Aggiungi**.
4. Nella finestra di dialogo **Aggiungi o modifica impostazione URI OMA** indicare quanto segue. Per un elenco di app bloccate sul dispositivo, specificare le informazioni seguenti:
    
    - **Nome dell'impostazione.** Immettere **PreventStartPackages**.
    - **Descrizione dell'impostazione.** Immettere una descrizione (facoltativa), ad esempio 'Elenco delle app bloccate'.
    -   **Tipo di dati.** Scegliere **Stringa** dall'elenco a discesa.
    -   **URI OMA.** Immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valore.** Immettere l'elenco dei nomi di pacchetti di app che si vuole bloccare. Come delimitatore è possibile usare **; : ,** o **|**. (Esempio: pacchetto1;pacchetto2;)

    Per un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store, escludendo tutte le altre app, specificare le informazioni seguenti:

    - **Nome dell'impostazione.** Immettere **AllowInstallPackages**.
    - **Descrizione dell'impostazione.** Immettere una descrizione (facoltativa), ad esempio 'Elenco delle app che gli utenti possono installare da Google Play.'
    - **Tipo di dati.** Scegliere **Stringa** dall'elenco a discesa.
    - **URI OMA.** Immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Valore.** Immettere l'elenco dei nomi di pacchetti che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|**. (Esempio: pacchetto1;pacchetto2;)

4. Fare clic su **OK** e quindi su **Salva criterio**. 

>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

Alla successiva verifica del dispositivo assegnato verranno applicate le impostazioni dell'applicazione.


## <a name="deploy-the-policy"></a>Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** selezionare uno o più gruppi a cui si vuole distribuire il criterio e quindi fare clic su **Aggiungi** &gt; **OK**.

 
Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.

### <a name="see-also"></a>Vedere anche
[Impostazioni dei criteri di Android e Samsung KNOX in Microsoft Intune](android-policy-settings-in-microsoft-intune.md)
