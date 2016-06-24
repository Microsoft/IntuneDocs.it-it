---
# required metadata

title: Ritirare i dispositivi | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ritirare i dispositivi dalla gestione di Intune

Indipendentemente dal fatto che un dispositivo sia personale o aziendale, arriva un momento in cui è necessario rimuoverlo dalla gestione in Intune. Il ritiro del dispositivo è un'operazione relativamente semplice: è possibile eseguire una cancellazione selettiva o una cancellazione completa.
## Cancellare i dati e le app dai dispositivi
Sia la cancellazione selettiva sia quella completa rimuovono il dispositivo dalla gestione di Intune rimuovendo i relativi criteri e il portale aziendale. Il dispositivo non dispone quindi più delle credenziali necessarie per accedere alle risorse aziendali, ad esempio Microsoft SharePoint, posta elettronica o Office 365.

La [cancellazione selettiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) è l'azione da preferire nel caso di dipendenti che hanno registrato i propri dispositivi in Intune perché non influisce sui dati personali presenti nel dispositivo. In questo caso vengono infatti rimossi solo i dati aziendali.

Per i dispositivi di proprietà dell'azienda, è possibile usare anche la [cancellazione completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), che reimposta il dispositivo alle impostazioni di fabbrica.

## Revocare l'accesso alla rete aziendale
Nel caso di disattivazione di un dispositivo perché un dipendente lascia l'azienda e ha trascurato di restituire l'hardware di proprietà dell'azienda, è anche possibile [bloccare il dispositivo in modalità remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md). In tal modo si impedirà un uso improprio dell'hardware e delle informazioni aziendali anche se si dovrà registrare il dispositivo come perdita.

È anche opportuno revocare la licenza nell'account utente Intune del dipendente in modo da liberarla e assegnarla a un nuovo account utente.

## Ritirare l'hardware
In alcuni casi è il dispositivo stesso ad aver raggiunto il termine della vita utile. In tali casi è opportuno [ripristinare le impostazioni di fabbrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) del dispositivo con una cancellazione completa per rimuovere tutti i dati e rimuoverlo da Intune prima di smaltirlo in conformità ai criteri aziendali.

### Vedere anche
[Proteggere i dati con la cancellazione selettiva o completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)


<!--HONumber=May16_HO1-->


