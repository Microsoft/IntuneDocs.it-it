---
title: Retire devices (Ritirare i dispositivi)
description: Intune supporta sia la cancellazione selettiva sia quella completa per ritirare il dispositivo dalla gestione di Intune rimuovendo i relativi criteri e il portale aziendale.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 493b5bfce7ab9b78f5f7c48d0d18524d1b191f1f
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="retire-devices-from-intune-management"></a>Ritirare i dispositivi dalla gestione di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Indipendentemente dal fatto che un dispositivo sia personale o di proprietà dell'azienda, arriva un momento in cui è necessario rimuoverlo dalla gestione in Intune.

I dispositivi non vengono mai rimosse da Intune senza l'intervento dell'utente, anche se i dispositivi non sono stati connessi al servizio Intune per un periodo di tempo.

Potrebbe essere necessario ritirare un dispositivo per diversi motivi:

-   L'utente lascia la società in modo pianificato (abbandono "gestito")
-   L'utente lascia la società improvvisamente (licenziamento, dimissioni e così via)
-   Il dispositivo viene perso
-   Il dispositivo viene riutilizzato (passaggio a un altro utente, riutilizzo per altri scopi e così via)

Per un dispositivo gestito come dispositivo mobile è possibile eseguire una cancellazione selettiva o una cancellazione completa oppure è possibile bloccare il dispositivo e reimpostarne la password. Cancellando il dispositivo, la sottoscrizione dell'utente viene liberata per l'aggiunta di un altro dispositivo. È anche possibile ritirare i PC gestiti con il software client di Intune.

## <a name="wipe-data-and-apps-from-devices"></a>Cancellare i dati e le app dai dispositivi
Sia la cancellazione selettiva che quella completa rimuovono il dispositivo dalla gestione di Intune rimuovendo i relativi criteri e il portale aziendale. Di conseguenza, il dispositivo non dispone più delle credenziali necessarie per accedere alle risorse aziendali come Microsoft SharePoint, la posta elettronica o Office 365.

La [cancellazione selettiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) è l'azione da preferire nel caso di dipendenti che hanno registrato i propri dispositivi in Intune perché non influisce sui dati personali presenti nel dispositivo. In questo caso vengono infatti rimossi solo i dati aziendali.

Per i dispositivi da ridestinare, è possibile usare anche la [cancellazione completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), che reimposta il dispositivo alle impostazioni di fabbrica.

### <a name="removing-user-licenses-and-managed-devices"></a>Rimozione di licenze utente e dispositivi gestiti
Quando si rimuove una licenza utente, viene annullata la registrazione dei dispositivi registrati dell'utente. È consigliabile usare la cancellazione selettiva per rimuovere i dati aziendali dai dispositivi gestiti prima di rimuovere la licenza di Intune per un utente. Dopo aver rimosso la licenza utente, il dispositivo non può essere la destinazione di azioni remote.

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Per eliminare i dispositivi nel portale di Azure Active Directory

1.  Accedere con le credenziali dell'organizzazione al sito Web [http://aka.ms/accessaad](http://aka.ms/accessaad) o [https://portal.office.com](https://portal.office.com) e quindi scegliere **Interfacce di amministrazione** &gt; **Azure AD**.

2.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si dispone di un account a pagamento, non verrà richiesta una carta di credito o un altro tipo di pagamento. Scegliere il collegamento **Register your free Azure Active Directory** (Registra una sottoscrizione Azure Active Directory gratuita).

4.  Scegliere **Active Directory** e quindi l'organizzazione.

5.  Scegliere la scheda **Utenti**.

6.  Scegliere l'utente di cui si vogliono eliminare i dispositivi.

7.  Scegliere **Dispositivi**.

8.  Scegliere i dispositivi appropriati e quindi scegliere **Elimina dispositivo**. Il dispositivo verrà eliminato alla successiva sincronizzazione con Active Directory, che avviene, in genere, entro quattro ore. Dopo la sincronizzazione, il dispositivo viene rimosso dalla gestione. Il dispositivo viene scalato dal limite di dispositivi associato all'utente.

## <a name="retire-managed-computers"></a>Ritirare i computer gestiti
I computer gestiti dal software client di Intune possono essere rimossi dalla gestione dalla console di amministrazione di Intune. L'operazione disinstalla anche il software client ed elimina i criteri di Intune dal computer. Vedere le informazioni sul [ritiro dei computer gestiti con il software client di Intune](retire-a-windows-pc-with-microsoft-intune.md).

## <a name="block-access-a-device"></a>Bloccare l'accesso a un dispositivo
Se un dispositivo viene smarrito o quando è necessario ritirare un dispositivo perché un dipendente lascia l'azienda senza restituire hardware di proprietà di quest'ultima, è anche possibile [reimpostare il passcode e bloccare in remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) il dispositivo. In tal modo si impedirà un uso improprio delle informazioni aziendali anche se si dovrà registrare il dispositivo come perdita.

È anche opportuno revocare la licenza nell'account utente Intune del dipendente in modo da liberarla e assegnarla a un nuovo account utente.

## <a name="retire-hardware"></a>Ritirare l'hardware
In alcuni casi è il dispositivo stesso ad aver raggiunto il termine della vita utile. In tali casi è opportuno [ripristinare le impostazioni di fabbrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) del dispositivo con una cancellazione completa per rimuovere tutti i dati e rimuoverlo da Intune prima di smaltirlo in conformità ai criteri aziendali.

### <a name="see-also"></a>Vedere anche
[Proteggere i dati con la cancellazione selettiva o completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)

