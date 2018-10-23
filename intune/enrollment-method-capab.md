---
title: Funzionalità di Intune per metodo di registrazione per i dispositivi Windows
titlesuffix: Microsoft Intune
description: Vedere le funzionalità supportate da ogni metodo di registrazione per i dispositivi Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c9e440aef7f434cbe675506fd6f22a9bd26b2c31
ms.sourcegitcommit: 528d2bc70bfd25803a2d9f0fe9372c8a5f5e7dad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446821"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Funzionalità per metodo di registrazione per i dispositivi Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune consente di gestire i dispositivi e le app del personale, nonché la modalità di accesso ai dati dell'organizzazione da parte del personale stesso. È necessario che i dispositivi siano registrati nel servizio Intune. Esistono diversi metodi per registrare i dispositivi del personale. Ogni metodo presenta procedure consigliate e funzionalità diverse, come illustrato nelle tabelle seguenti.

## <a name="best-practices-by-enrollment-method"></a>Procedure consigliate per metodo di registrazione
| **Procedure consigliate** | **[Aggiunto ad Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Aggiunto ad Azure AD con Autopilot](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **Oggetto Criteri di gruppo** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Usato comunemente in EDU|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|I dispositivi possono essere condivisi|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|I dispositivi personali devono accedere alle risorse aziendali|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|
|Manutenzione automatica delle app|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Procedure consigliate per metodo di registrazione

| **Funzionalità** | **[Aggiunto ad Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Aggiunto ad Azure AD con Autopilot](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **Oggetto Criteri di gruppo** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Accesso condizionale                                      |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|L'utente viene associato al dispositivo                    |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Richiede Azure AD Premium                               |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|
|Il dispositivo può accedere alle risorse protette da autorità di certificazione             |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Gli utenti non possono essere amministratori dei propri dispositivi               |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilità di configurare l'esperienza di installazione del dispositivo        |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilità di registrare i dispositivi senza intervento dell'utente      |![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|
|Possibilità di eseguire gli script di PowerShell                       |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Supporta la registrazione automatica dopo l'aggiunta a un dominio AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|
|Supporta la registrazione automatica dopo l'aggiunta ad Azure AD ibrido|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|
|Supporta la registrazione automatica dopo l'aggiunta ad Azure AD       |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Passaggi successivi

[Opzioni di registrazione](enrollment-options.md)
