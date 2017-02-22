---
title: "Che cos&quot;è l&quot;accesso condizionale? | Anteprima di Intune in Azure | Documentazione Microsoft"
description: 'Anteprima di Intune in Azure: informazioni su come definire le condizioni che utenti e dispositivi devono soddisfare per accedere alle risorse aziendali nell&quot;anteprima di Microsoft Intune in Azure.'
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 41931f64db969c82f79e007c4be9e68b7caf4ce9
ms.openlocfilehash: 20696fb2dc0126aa224e779738cedb4f95f666e8


---

# <a name="what-is-conditional-access"></a>Che cos'è l'accesso condizionale?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Questo argomento descrive l'accesso condizionale applicato a Enterprise Mobility + Security e, a seguire, le funzionalità di accesso condizionale in Intune.

L'accesso condizionale da Enterprise Mobility + Security (EMS) offre la potenza di Azure Active Directory Premium e Microsoft Intune per fornire il controllo necessario per proteggere i dati aziendali, offrendo agli utenti un'esperienza che consenta di lavorare al meglio da qualsiasi dispositivo.

Con l'accesso condizionale è possibile definire le condizioni che limitano l'accesso ai dati aziendali in base alla posizione, al dispositivo, allo stato dell'utente e alla sensibilità dell'applicazione.

Dalla prospettiva del dispositivo, Intune e Azure Active Directory collaborano per assicurarsi che solo dispositivi gestiti e conformi abbiano accesso alla posta elettronica e ai servizi di Office 365. Ad esempio, è possibile impostare un criterio in Azure Active Directory per consentire l'accesso ai servizi di Office 365 solo ai computer che appartengono a un dominio o ai dispositivi mobili registrati in un'applicazione di gestione di dispositivi mobili come Intune. Per impostare un profilo di conformità del dispositivo che valuta lo stato di conformità del dispositivo, è possibile usare Intune. Lo stato di conformità viene segnalato ad Azure Active Directory che lo usa per l'applicazione dei criteri in Azure Active Directory quando l'utente tenta di accedere alle risorse aziendali. Per informazioni sulla conformità dei dispositivi in Intune, vedere [Che cos'è la conformità dei dispositivi?](/intune-azure/set-device-compliance/what-is-device-compliance)

L'accesso condizionale per le applicazioni cloud, ad esempio Exchange Online, può essere configurato tramite Azure Active Directory. Per altre informazioni, vedere questo [articolo](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal).

## <a name="on-premises-conditional-access-in-intune"></a>Accesso condizionale locale in Intune

L'accesso condizionale in Intune può essere usato per consentire o bloccare l'accesso a **Exchange locale** in base alla gestione e alla registrazione dei dispositivi.

Le impostazioni del profilo di conformità del dispositivo vengono usate per valutare la conformità del dispositivo. L'accesso condizionale usa la valutazione per consentire o bloccare l'accesso a Exchange locale. Quando l'accesso condizionale viene usato in combinazione con il profilo di conformità dei dispositivi, possono accedere a Exchange locale solo i dispositivi conformi. È possibile configurare le impostazioni avanzate di accesso condizionale per un controllo più granulare, ad esempio: consentire o bloccare determinate piattaforme o bloccare immediatamente i dispositivi non gestiti da Intune.

Il profilo di conformità del dispositivo e l'accesso condizionale vengono assegnati all'utente. Di qualsiasi dispositivo usato dall'utente per accedere a Exchange locale viene verificata la conformità. Tenere presente che l'utente che usa il dispositivo deve disporre di un profilo di conformità assegnato, in modo che venga valutata la conformità del dispositivo. Se all'utente non viene distribuito alcun criterio di conformità, il dispositivo viene considerato conforme e non vengono applicate restrizioni di accesso.

Se i dispositivi non soddisfano le condizioni imposte, l'utente viene guidato nel processo di registrazione del dispositivo e di risoluzione del problema che rende il dispositivo non conforme.

## <a name="next-steps"></a>Passaggi successivi

[How to create a conditional access policy for Exchange on-premises](create-conditional-access-policy-for-exchange-on-premises.md) (Come creare criteri di accesso condizionale per Exchange locale)

[How to configure conditional access in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal) (Come configurare l'accesso condizionale in Azure Active Directory)



<!--HONumber=Feb17_HO1-->


