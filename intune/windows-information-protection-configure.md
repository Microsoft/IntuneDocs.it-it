---
title: Configurare Windows Information Protection - Intune
titleSuffix: Intune on Azure
description: "Informazioni sulle impostazioni di Intune che è possibile usare per gestire Windows Information Protection.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f233672c-7d9b-4554-af1f-92c001a1a3c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ac59456dd2bc59a0a50eeab4e483dea2033c0fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Come configurare Windows Information Protection in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Con l'aumento dei dispositivi personali nell'organizzazione, aumenta anche il rischio di perdita accidentale dei dati tramite app e servizi, ad esempio posta elettronica, social media e cloud pubblico, non controllati dall'organizzazione. È il caso, ad esempio, di un dipendente che invia le immagini di progettazione più recenti dall'account di posta elettronica personale, copia e incolla le informazioni su un prodotto in un tweet o salva il report di una vendita in corso nell'area di archiviazione nel cloud pubblico.

**Windows Information Protection** offre protezione da questa potenziale perdita di dati senza interferire con l'esperienza del dipendente. Consente inoltre di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti portano a lavoro senza richiedere modifiche per l'ambiente o altre app.

Questi criteri di Intune gestiscono l'elenco di app protette da Windows Information Protection, i percorsi di rete aziendali, il livello di protezione e le impostazioni di crittografia.

>[!NOTE]
> Per usare l'app Portale aziendale di Windows 10 con Windows Information Protection è necessario aggiungere l'app con la modalità **Esente** di Windows Information Protection. 

### <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere [Protect your enterprise data using Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip) (Proteggere i dati aziendali tramite Windows Information Protection).