---
title: Che cosa avviene se si annulla la registrazione del dispositivo Windows? | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6e3f61fc84458525ae2ff62887d64baea9542
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505954"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>Che cosa avviene se si annulla la registrazione del dispositivo Windows da Intune?

Usare i collegamenti sul lato destro della pagina in **Contenuto di questo articolo** per trovare informazioni sul tipo di dispositivo in uso.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

- Il dispositivo non è più visualizzato nel portale aziendale e non è più possibile installare app dal portale stesso.

- Il software client Intune, se è installato, verrà rimosso dal computer.

- Il software Intune Endpoint Protection verrà rimosso dal computer. Se nel computer è installato altro software di protezione da virus, ma tale software è disabilitato, sarà possibile abilitarlo di nuovo dopo aver rimosso Intune Endpoint Protection. Controllare il computer dopo che è stato rimosso dal portale aziendale.

    > [!IMPORTANT]
    > Se l'altro software di protezione da virus non viene riabilitato o non sono installati altri software di protezione da virus, il computer potrebbe essere vulnerabile a virus e malware.

- Non sono più valide le impostazioni che sono state modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera.

- Il computer non riceve più aggiornamenti software automatici o aggiornamenti del software antivirus dal servizio Intune. Ma, a seconda della configurazione, il computer potrebbe continuare a ricevere aggiornamenti da Windows Server Update Services, Windows Update o Microsoft Update.

Inoltre, per Windows 8.1:

- Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

- Alcune app di posta elettronica, ad esempio Windows Mail, non possono più accedere alla posta elettronica aziendale archiviata nel dispositivo.

- Potrebbe non essere possibile connettersi alla rete aziendale usando una connessione Wi-Fi o una rete privata virtuale.

- Dal dispositivo potrebbe non essere più possibile accedere ad alcune risorse aziendali, ad esempio condivisioni di file o siti Web interni.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile e Windows Phone 8.1

- L'app Portale aziendale viene disinstallata dal dispositivo. Ciò significa che il dispositivo non è più visualizzato nel portale aziendale e che non è più possibile installare app dall'app Portale aziendale o dal sito Web del portale aziendale.

- Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

- Non saranno più valide le impostazioni modificate nel dispositivo quando questo è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

    > [!IMPORTANT]
    > L'unica eccezione è costituita dai criteri di crittografia, che saranno ancora validi. Se i criteri aziendali richiedevano la crittografia del telefono Windows Phone, l'unico modo per decrittografare il telefono è di reimpostarlo tramite il menu **Impostazioni**.

## <a name="windows-rt-running-windows-81"></a>Windows RT che esegue Windows 8.1

- L'app Portale aziendale viene disinstallata dal dispositivo. Ciò significa che il dispositivo non è più visualizzato nel portale aziendale e che non è possibile installare app dal portale stesso.

- Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

- Non saranno più valide le impostazioni modificate nel dispositivo quando questo è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

- Potrebbe non essere più possibile connettersi alla rete aziendale usando una connessione Wi-Fi o una rete privata virtuale.

- Dal dispositivo potrebbe non essere più possibile accedere ad alcune risorse aziendali, ad esempio condivisioni di file o siti Web interni.

- Alcune app di posta elettronica, ad esempio Windows Mail, non possono più accedere alla posta elettronica aziendale archiviata nel dispositivo.

Quando si rimuove il dispositivo Windows RT, si verifica quanto segue:

- L'app Portale aziendale viene disinstallata dal dispositivo. Ciò significa che il dispositivo non è più visualizzato nel portale aziendale e che non è possibile installare app dal portale stesso.

- Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

- Non saranno più valide le impostazioni modificate nel dispositivo quando questo è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

Per eventuali domande, contattare il supporto tecnico dell'azienda. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
