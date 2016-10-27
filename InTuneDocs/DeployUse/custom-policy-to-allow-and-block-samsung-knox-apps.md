---
title: App consentite e bloccate per KNOX | Microsoft Intune
description: Personalizzare il profilo per creare un elenco di app consentite e bloccate per KNOX.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7679d624ba22b2a062ef2534a642e38a5f57fde
ms.openlocfilehash: 273627573f58e1bde4fd19c548ce87639f25ca4b



---
# Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX

Seguire le procedure riportate in questo argomento per creare un criterio Microsoft Intune personalizzato allo scopo di creare uno degli elementi seguenti:

- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Le app presenti in questo elenco sono bloccate e non possono essere eseguite, anche se al momento dell'applicazione del criterio erano già state installate .
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. È possibile installare soltanto le app elencate. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX.

## Per creare un elenco di app consentite o bloccate

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Criteri** &gt; **Criteri di configurazione** &gt; **Aggiungi**.
2. Nella finestra di dialogo **Crea un nuovo criterio** espandere **Android**, scegliere **Configurazione personalizzata** e quindi **Crea criterio**.
3. Fornire un nome e una descrizione del criterio (facoltativa) e quindi, nella sezione **Impostazioni URI OMA**, scegliere **Aggiungi**.
4. Nella finestra di dialogo **Aggiungi o modifica impostazione URI OMA** indicare quanto segue. Per un elenco di app bloccate sul dispositivo, specificare le informazioni seguenti:
    
    - **Nome dell'impostazione.** Immettere **PreventStartPackages**.
    - **Descrizione dell'impostazione.** Immettere una descrizione (facoltativa), ad esempio 'Elenco delle app bloccate'.
    -   **Tipo di dati.** Scegliere **Stringa** dall'elenco a discesa.
    -   **URI OMA.** Immettere **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valore.** Immettere l'elenco dei nomi di pacchetti che si vuole consentire. Come delimitatore è possibile usare **; : ,** o **|**. (Esempio: pacchetto1;pacchetto2;)

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


## Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** selezionare uno o più gruppi a cui si vuole distribuire il criterio e quindi fare clic su **Aggiungi** &gt; **OK**.

 
Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.

### Vedere anche
[Impostazioni dei criteri di Android e Samsung KNOX in Microsoft Intune](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


