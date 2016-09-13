---
title: Ritirare i dispositivi | Microsoft Intune
description: Intune supporta sia la cancellazione selettiva sia quella completa per ritirare il dispositivo dalla gestione di Intune rimuovendo i relativi criteri e il portale aziendale.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: 29d13dcbc367c18d64f9522fa9a3b962226feebb


---

# Ritirare i dispositivi dalla gestione di Intune

Indipendentemente dal fatto che un dispositivo sia personale o aziendale, arriva un momento in cui è necessario rimuoverlo dalla gestione in Intune. Può essere necessario ritirare un dispositivo per diversi motivi:

-   L'utente lascia la società in modo pianificato (abbandono "gestito")
-   L'utente lascia la società improvvisamente (licenziamento, dimissioni e così via)
-   Il dispositivo viene perso
-   Il dispositivo viene riutilizzato (passaggio a un altro utente, riutilizzo per altri scopi e così via)

È possibile eseguire una cancellazione selettiva o una cancellazione completa nei dispositivi gestiti come dispositivi mobili oppure è possibile bloccare un dispositivo e reimpostarne la password. Cancellando il dispositivo, la sottoscrizione dell'utente viene liberata per l'aggiunta di un altro dispositivo. È inoltre possibile ritirare i PC gestiti con il software client di Intune.

## Cancellare i dati e le app dai dispositivi
Sia la cancellazione selettiva sia quella completa rimuovono il dispositivo dalla gestione di Intune rimuovendo i relativi criteri e il portale aziendale. Il dispositivo non dispone quindi più delle credenziali necessarie per accedere alle risorse aziendali, ad esempio Microsoft SharePoint, posta elettronica o Office 365.

La [cancellazione selettiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) è l'azione da preferire nel caso di dipendenti che hanno registrato i propri dispositivi in Intune perché non influisce sui dati personali presenti nel dispositivo. In questo caso vengono infatti rimossi solo i dati aziendali.

Per i dispositivi da ridestinare, è possibile usare anche la [cancellazione completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), che reimposta il dispositivo alle impostazioni di fabbrica.

## Per eliminare i dispositivi nel portale di Azure Active Directory

1.  Accedere con le credenziali dell'organizzazione a [http://aka.ms/accessaad](http://aka.ms/accessaad) o [https://portal.office.com](https://portal.office.com), quindi scegliere **Interfacce di amministrazione** &gt; **Azure AD**.

2.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si dispone di un account a pagamento, questa operazione non richiede l'uso di una carta di credito né un pagamento. Fare clic sul collegamento per l'abbonamento relativo alla **registrazione gratuita di Azure Active Directory**.

4.  Selezionare **Active Directory** e quindi l'organizzazione.

5.  Selezionare la scheda **Utenti** .

6.  Selezionare l'utente di cui si desidera eliminare i dispositivi.

7.  Scegliere **Dispositivi**.

8.  Selezionare i dispositivi appropriati e scegliere **Elimina dispositivo**. Il dispositivo verrà eliminato alla successiva sincronizzazione con Active Directory, che avviene, in genere, entro 4 ore. Dopo la sincronizzazione, il dispositivo viene rimosso dalla gestione. Il dispositivo viene scalato dal limite di dispositivi associato all'utente.

## Ritirare i computer gestiti
I computer gestiti con il software client di Intune possono essere rimossi dalla gestione usando la console di amministrazione di Intune. Viene disinstallato anche il software client e vengono eliminati i criteri di Intune dal computer. Vedere le informazioni sul [ritiro dei computer gestiti con il software client di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Bloccare l'accesso a un dispositivo
Nel caso di un dispositivo smarrito o quando è necessario ritirare un dispositivo perché un dipendente lascia l'azienda senza restituire un hardware di proprietà dell'azienda, è anche possibile [reimpostare il passcode e bloccare in remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) il dispositivo. In tal modo si impedirà un uso improprio delle informazioni aziendali anche se si dovrà registrare il dispositivo come perdita.

È anche opportuno revocare la licenza nell'account utente Intune del dipendente in modo da liberarla e assegnarla a un nuovo account utente.

## Ritirare l'hardware
In alcuni casi è il dispositivo stesso ad aver raggiunto il termine della vita utile. In tali casi è opportuno [ripristinare le impostazioni di fabbrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) del dispositivo con una cancellazione completa per rimuovere tutti i dati e rimuoverlo da Intune prima di smaltirlo in conformità ai criteri aziendali.

### Vedere anche
[Proteggere i dati con la cancellazione selettiva o completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->


