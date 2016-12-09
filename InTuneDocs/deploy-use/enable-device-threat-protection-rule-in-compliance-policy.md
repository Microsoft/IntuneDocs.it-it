---
title: "Abilitare la regola di protezione del dispositivo nei criteri di conformità | Microsoft Intune"
description: "Abilitare la regola di protezione dalle minacce per i dispositivi mobili nei criteri di conformità del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: efddf7645d0548c842ae8aa3b1ca5222023913b5


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità
Intune con la protezione dalle minacce per i dispositivi mobili Lookout offre la possibilità di rilevare le minacce per dispositivi mobili ed eseguire una valutazione dei rischi nel dispositivo. È possibile creare una regola dei criteri di conformità che includa la valutazione dei rischi per determinare se il dispositivo è conforme. È quindi possibile usare i criteri di accesso condizionale per consentire o bloccare l'accesso a Exchange, SharePoint e altri servizi in base alla conformità del dispositivo.

Per fare in modo che il rilevamento delle minacce del dispositivo Lookout influenzi i criteri di conformità per il dispositivo:

* È necessario abilitare la regola **Protezione dalle minacce per il dispositivo** nei criteri di conformità.

* La pagina **Stato di Lookout** nella **console di amministrazione di Intune** deve indicare **Attivo**. Vedere l'argomento [Abilitare la connessione a Lookout MTP nella console di amministrazione Intune](enable-lookout-mtp-connection-in-intune.md) per altri dettagli e istruzioni su come attivare l'integrazione di Lookout.


Prima di creare la regola di protezione dalle minacce per il dispositivo nei criteri di conformità, è consigliabile [configurare la sottoscrizione con la protezione dalle minacce per il dispositivo di Lookout](set-up-your-subscription-with-lookout-mtp.md), [abilitare la connessione a Lookout in Intune](enable-lookout-mtp-connection-in-intune.md) e [configurare l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md). La regola di conformità viene applicata solo dopo il completamento della configurazione.

Per abilitare la regola di protezione dalle minacce per il dispositivo, è possibile usare criteri di conformità esistenti o crearne di nuovi.

Nell'ambito della configurazione della protezione dalle minacce per il dispositivo di Lookout, nella [console di Lookout](https://aad.lookout.com) è stato creato un criterio per la classificazione delle varie minacce in base ai livelli alto, medio e basso. Nei criteri di conformità di Intune si userà il livello di minaccia per impostare il livello di minaccia massimo consentito.

Nella pagina **Criteri di conformità** della **console di amministrazione di Intune** passare a **Integrità del dispositivo** e abilitare la regola **Protezione dalle minacce per il dispositivo** tramite l'opzione di alternanza. Selezionare quindi il livello di minaccia massimo consentito tra uno dei seguenti:
* **Nessuno (protetto)**: questo è il livello più sicuro e  indica che il dispositivo non può avere minacce.  Se viene trovato un livello di minaccia, il dispositivo viene valutato come non conforme.  
* **Bassa**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
* **Media**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
* **Alta**: questo è il livello meno sicuro. Fondamentalmente consente tutti i livelli di minaccia ed è utile se si usa questa soluzione esclusivamente per la creazione di report.

![screenshot che mostra l'impostazione della regola di protezione dalle minacce per il dispositivo ](../media/mtp/mtp-compliance-policy-rule.png)

![screenshot che mostra l'opzione del livello di minaccia per l'impostazione della regola di protezione dalle minacce per il dispositivo](../media/mtp/mtp-compliance-policy-setting.png)

Se si creano criteri di accesso condizionale per Office 365 e altri servizi, viene presa in considerazione la valutazione di conformità precedente e per i dispositivi non conformi viene bloccato l'accesso alle risorse aziendali fino alla risoluzione della condizione di minaccia.

È possibile visualizzare lo stato di conformità di un dispositivo nella pagina **Tutti i dispositivi** della **console di amministrazione di Intune**.

![screenshot della pagina dei dispositivi nella console di amministrazione Intune che mostra lo stato di conformità di un dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Passaggi successivi
* Creare criteri di accesso condizionale
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange locale](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


