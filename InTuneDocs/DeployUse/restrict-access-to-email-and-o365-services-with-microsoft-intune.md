---
# required metadata

title: Limitare l'accesso alla posta elettronica e ai servizi di Office 365 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Limitare l'accesso alla posta elettronica e ai servizi di Office 365 con Microsoft Intune
È possibile limitare l'accesso alla posta elettronica aziendale e ai servizi di Office 365 con l'accesso condizionale di Intune. L'accesso condizionale di Intune consente di assicurarsi che l'accesso alla posta elettronica aziendale e ai servizi di Office 365 sia limitato ai dispositivi conformi alle regole definite.
## Come funziona l'accesso condizionale?
Le impostazioni dei criteri di conformità vengono usate per valutare la conformità del dispositivo. I criteri di accesso condizionale usano la versione di valutazione per limitare o consentire l'accesso a un servizio specifico. Quando i criteri di accesso condizionale vengono usati in combinazione con i criteri di conformità, solo i dispositivi conformi possono accedere al servizio.

Tenere presente che l'utente che usa il dispositivo deve inoltre disporre di criteri di conformità distribuiti, in modo che venga valutata la conformità del dispositivo.
Se nessun criterio di conformità viene distribuito all'utente, il dispositivo viene considerato conforme e non vengono applicate restrizioni di accesso.

Se i dispositivi non soddisfano le condizioni definite nei criteri, l'utente finale viene guidato nel processo di registrazione del dispositivo e di risoluzione del problema che impedisce la conformità del dispositivo.

Un flusso di accesso condizionale tipico:

![Immagine che illustra gli aspetti tenuti in considerazione per determinare se a un dispositivo è consentito o meno l'accesso a un servizio](./media/ConditionalAccess4.png)

## Come configurare l'accesso condizionale?
Usare l'accesso condizionale per gestire l'accesso a Microsoft **Exchange locale**, **Exchange Online**, **Exchange Online dedicato**, **SharePoint Online** e **Skype for Business Online**.

Per impostare l'accesso condizionale, configurare i criteri di conformità del dispositivo e i criteri di accesso condizionale.

I criteri di conformità includono impostazioni quali passcode e crittografia e la specifica se un dispositivo è jailbroken. Per poter essere considerato conforme, il dispositivo deve soddisfare le regole seguenti.

È possibile impostare criteri di accesso condizionale per limitare l'accesso in base a:
- Stato di conformità del dispositivo.
- Piattaforma in esecuzione nel dispositivo.
- Tipo di app usate per accedere ai servizi.

A differenza degli altri criteri di Intune, i criteri di accesso condizionale non vengono distribuiti. Dopo aver configurato i criteri e aver selezionato gli utenti che devono disporre di criteri, questi vengono applicati a tutti gli utenti destinatari. Per poter accedere alle risorse, un utente di destinazione in un criterio deve usare solo dispositivi conformi.


## Passaggi successivi
1. [Informazioni sui criteri di conformità del dispositivo e sul relativo funzionamento ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Creare i criteri di conformità](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Creare criteri di accesso condizionale per:
> [!div class="op_single_selector"]
  - [Creare criteri di accesso condizionale per Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per Exchange locale](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per il nuovo ambiente Exchange Online dedicato](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per l'ambiente legacy Exchange Online dedicato](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


