---
title: Scoprire a quanti utenti viene destinato un criterio
titlesuffix: Microsoft Intune
description: Scoprire a quanti utenti viene destinato un criterio
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38e8a2e2-2329-11e8-b467-0ed5f89f718b
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a69f4c4e5f80c77259656cac7650ca58c51b2407
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185765"
---
# <a name="evaluate-how-many-users-are-targeted-by-a-policy"></a>Calcolare a quanti utenti viene destinato un criterio
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile usare il pulsante **Valuta** per scoprire a quanti utenti viene destinato un criterio di configurazione o un criterio di configurazione del dispositivo. Questa funzione calcola solo gli utenti e non i dispositivi.

1.  In [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Conformità del dispositivo** o **Configurazione del dispositivo** e quindi **Criteri**.
2.  Selezionare uno dei criteri o crearne uno nuovo e quindi scegliere **Assegnazioni**.
3.  Scegliere **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti a cui viene destinato il criterio.

Se il pulsante **Valuta** è disattivato, verificare che il criterio sia stato assegnato a uno o più gruppi.

