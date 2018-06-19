---
title: Impostazioni di Windows Information Protection in Microsoft Intune
titleSuffix: ''
description: Informazioni sulle impostazioni di Microsoft Intune che è possibile usare per gestire Windows Information Protection.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ec649134d4c3d28c99863aa3f04d2a89d4e029f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31033131"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Come configurare Windows Information Protection in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Con l'aumento dei dispositivi personali nell'organizzazione, aumenta anche il rischio di perdita accidentale dei dati tramite app e servizi, ad esempio posta elettronica, social media e cloud pubblico, non controllati dall'organizzazione. È il caso, ad esempio, di un dipendente che invia le immagini di progettazione più recenti dall'account di posta elettronica personale, copia e incolla le informazioni su un prodotto in un tweet o salva il report di una vendita in corso nell'area di archiviazione nel cloud pubblico.

**Windows Information Protection** offre protezione da questa potenziale perdita di dati senza interferire con l'esperienza del dipendente. Consente inoltre di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti portano a lavoro senza richiedere modifiche per l'ambiente o altre app.

Questi criteri di Intune gestiscono l'elenco di app protette da Windows Information Protection, i percorsi di rete aziendali, il livello di protezione e le impostazioni di crittografia.

>[!NOTE]
> Per usare l'app Portale aziendale di Windows 10 con Windows Information Protection è necessario aggiungere l'app con la modalità **Esente** di Windows Information Protection. 

### <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere:
-  [Proteggere i dati aziendali con Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Creare criteri di Windows Information Protection (WIP) usando la console classica per Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Creare criteri di Windows Information Protection (WIP) con il software MDM usando il portale di Azure per Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Creare criteri di Windows Information Protection (WIP) con il software MAM usando il portale di Azure per Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
