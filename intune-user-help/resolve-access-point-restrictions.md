---
title: Risolvere le limitazioni dei punti di accesso impostate in Intune
description: Esaminare i 3 messaggi comuni relativi ai criteri di restrizione dei punti di accesso di Intune e scoprire come risolverli
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: a6f5fb0ae4ab5f4f5cafbba6122c0b42e4591c4b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745142"
---
# <a name="resolve-access-point-restrictions"></a>Risolvere le limitazioni dei punti di accesso

Le organizzazioni possono limitare le posizioni da cui i dispositivi accedono ai dati aziendali.
Per configurare queste *limitazioni dei punti di accesso*, esse specificano e impostano percorsi di rete approvati.  

Quando si tenta di connettersi a una rete non riconosciuta o non approvata, si potrebbero ricevere uno o più dei messaggi seguenti:

* Le limitazioni del punto di accesso non sono state configurate.
* Non si è connessi a una rete approvata.
* Si è verificato un errore e non è stato possibile applicare le limitazioni del punto di accesso.

 Nelle tabelle riportate di seguito viene elencato ogni messaggio, il suo significato e viene spiegato come accedere nuovamente alle risorse di lavoro.

## <a name="access-point-restrictions-not-set-up"></a>Le limitazioni del punto di accesso non sono state configurate  
| Messaggio del Portale aziendale | Significato del messaggio | Operazione da eseguire                                                               
|------------------------|--------------------------|--------------------------|
| **Le limitazioni del punto di accesso non sono state configurate - Le limitazioni ai punti di accesso sono attive e devono essere configurate.** | La società ha applicato limitazioni ai punti di accesso nel dispositivo. Questa impostazione richiede che l'app Portale aziendale verifichi alcune impostazioni di rete nel dispositivo. | Toccare **Risolvi** L'app Portale aziendale verificherà la presenza di una connessione a una rete aziendale approvata. |

## <a name="not-connected-to-an-approved-network"></a>Non si è connessi a una rete approvata  

| Messaggio del Portale aziendale | Significato del messaggio | Operazione da eseguire                                                                   
|------------------------|-----------------------------------|--------------------------|
| **Il dispositivo non è connesso a una rete approvata - Connessione a una rete wireless approvata.** | Si è connessi a una rete che non è stata approvata per l'accesso aziendale. Finché si resterà connessi a questa rete, non sarà possibile accedere alla posta elettronica di lavoro, alle app e alle altre risorse aziendali protette. | Connettersi a una rete aziendale approvata. Toccare **Risolvi** per riprovare. |

## <a name="restrictions-couldnt-be-enforced"></a>Non è stato possibile applicare le limitazioni  

| Messaggio del Portale aziendale | Significato del messaggio | Operazione da eseguire                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Non è stato possibile applicare le limitazioni dei punti di accesso - Il Portale aziendale ha rilevato un errore.** | Intune non è in grado di stabilire se si sia connessi a una rete approvata. Questo errore potrebbe essere dovuto a una connettività di rete non adeguata, alla batteria in esaurimento, alla modalità di risparmio batteria o a un errore del Portale aziendale. | Verificare di avere una buona ricezione di rete. Disattivare la modalità di risparmio batteria e verificare che la batteria abbia una durata residua di almeno il 30%. Toccare **Risolvi** per riprovare. 

Serve ancora assistenza? È consigliabile contattare il supporto tecnico dell'azienda. Per informazioni di contatto specifiche, visitare il [sito Web del Portale aziendale](https://portal.manage.microsoft.com/#HelpDeskDialog).
