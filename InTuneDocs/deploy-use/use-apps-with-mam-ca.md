---
title: Uso di app con l&quot;accesso condizionale MAM | Documentazione Microsoft
description: "Informazioni su come l&quot;accesso condizionale per la gestione delle app per dispositivi mobili può essere usato per controllare le app che hanno accesso ai servizi di Office 365."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 22746475bf50f8e4775c81e6833428c7f2ef9eba


---
# <a name="what-to-expect-when-using-an-app-with-mam-ca"></a>Cosa accade quando viene usata un'app con accesso condizionale per le gestione delle app per dispositivi mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

L'accesso condizionale per le gestione delle app per dispositivi mobili verifica l'identità dell'applicazione approvata tramite un'app broker che deve essere presente nel dispositivo:
*  In **iOS** l'app broker è l'**app Azure Authenticator**.
* In **Android** l'app broker è l'**app Portale aziendale di Intune**. 

Agli utenti finali che accedono per la prima volta a un'app supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili, come OneDrive o Outlook, viene chiesto di installare l'app broker e di registrare il dispositivo in Azure AD. La registrazione del dispositivo in Azure AD (in precedenza chiamata Aggiunta all'area di lavoro) crea un record del dispositivo e un certificato con cui vengono rilasciati i token.  Questa operazione **non** corrisponde alla **registrazione MDM**. Non vengono applicati profili o criteri di gestione e non è disponibile un inventario delle app del dispositivo.  Il processo di installazione dell'app broker e di registrazione del dispositivo verrà eseguito solo al primo utilizzo di un'app gestita.

L'elenco seguente include le proprietà che derivano direttamente dal dispositivo:

* alternativeSecurityIds (identificazione personale del certificato di Azure Active Directory e hash della chiave pubblica)
* deviceOSType
* deviceOSVersion
* displayName

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Per rimuovere un dispositivo dalla registrazione in Azure AD
La registrazione del dispositivo può essere rimossa tramite la console di amministrazione di Azure AD, in genere da un amministratore IT.  Questa operazione può essere eseguita anche dall'utente finale nel dispositivo stesso.

* **Console di amministrazione di Azure AD**: nella console di amministrazione** di Azure AD eliminare il dispositivo che si vuole rimuovere.
* **Dispositivo iOS**: aprire l'app Azure Authenticator, scorrere verso sinistra fino all'account e scegliere di annullare la registrazione.  
* **Dispositivo Android**: disinstallare l'app Portale aziendale o rimuovere l'account da **Impostazioni di sistema**.



## <a name="mam-ca-with-conditional-access-based-on-device-compliance"></a>Accesso condizionale per la gestione delle app per dispositivi mobili con accesso condizionale basato sulla conformità del dispositivo  

È possibile configurare l'[accesso condizionale basato sulla conformità del dispositivo](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**accesso condizionale per il dispositivo**) nella [console di amministrazione di Intune](https://manage.microsoft.com) o nella [console di gestione di Azure AD Premium] (https://manage.windowsazure.com). L'accesso condizionale per il dispositivo richiede che gli utenti si connettano a Exchange Online solo tramite dispositivi gestiti in Intune conformi ai criteri di conformità dei dispositivi di Intune o tramite PC aggiunti a un dominio.  Se un utente appartiene a uno o più gruppi di sicurezza che soddisfano i criteri di accesso condizionale per la gestione delle app per dispositivi mobili e per il dispositivo, l'utente deve soddisfare uno dei due requisiti:
* L'app usata per accedere al servizio è un'app per dispositivi mobili supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili e nel dispositivo su cui viene eseguita l'app è installato il **programma di autenticazione iOS (per i dispositivi iOS)** o l'**app Portale aziendale (per i dispositivi Android)**.
* Il dispositivo usato per accedere al servizio è **gestito da Intune e conforme** ai criteri di conformità del dispositivo di Intune oppure è un **PC aggiunto a un dominio**.  Di seguito sono riportati alcuni esempi per illustrare quanto descritto:
  * Se un utente tenta di connettersi da un'**app di posta elettronica iOS nativa**, verrà richiesto di usare un **dispositivo gestito e conforme** poiché l'app nativa non è supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili.
  * Se un utente tenta di connettersi da un **PC Windows Home**, verranno applicati i **criteri di accesso condizionale per il dispositivo** che richiedono che l'utente usi un PC aggiunto a un dominio.




## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di Exchange Online per le app di gestione delle app per dispositivi mobili](mam-ca-for-exchange-online.md)

[Bloccare le app che non usano l'autenticazione moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


