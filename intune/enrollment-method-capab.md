---
title: Funzionalità di Intune per i metodi di registrazione dei dispositivi Windows
titleSuffix: Microsoft Intune
description: Funzionalità per ogni metodo di registrazione dei dispositivi Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd1dbb3280fbbb93423796b18f6dd85a50a41f11
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567543"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funzionalità di Intune per i metodi di registrazione dei dispositivi Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Esistono diversi metodi per registrare i dispositivi del personale in Intune. Ogni metodo presenta procedure consigliate e funzionalità diverse, come illustrato nelle tabelle seguenti.

## <a name="best-practices-by-enrollment-method"></a>Procedure consigliate per metodo di registrazione
| **Procedure consigliate** | **[Aggiunto ad Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Aggiunto ad Azure AD con Autopilot (modalità definita dall'utente)](enrollment-autopilot.md)** |**[Aggiunto ad Azure AD con Autopilot (modalità di distribuzione automatica)](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[Oggetto Criteri di gruppo](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-gestione](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Usato comunemente in EDU|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|I dispositivi possono essere condivisi|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|I dispositivi personali devono accedere alle risorse aziendali|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Manutenzione automatica delle app|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Procedure consigliate per metodo di registrazione

| **Funzionalità** | **[Aggiunto ad Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Aggiunto ad Azure AD con Autopilot (modalità definita dall'utente)](enrollment-autopilot.md)** |**[Aggiunto ad Azure AD con Autopilot (modalità di distribuzione automatica)](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[Oggetto Criteri di gruppo](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-gestione](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Accesso condizionale                                      |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|L'utente viene associato al dispositivo                    |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Richiede Azure AD Premium                               |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Il dispositivo può accedere alle risorse protette da autorità di certificazione             |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Gli utenti non possono essere amministratori dei propri dispositivi               |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilità di configurare l'esperienza di installazione del dispositivo        |![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilità di registrare i dispositivi senza intervento dell'utente      |![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Possibilità di eseguire gli script di PowerShell                       |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Supporta la registrazione automatica dopo l'aggiunta a un dominio AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Supporta la registrazione automatica dopo l'aggiunta ad Azure AD ibrido|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|
|Supporta la registrazione automatica dopo l'aggiunta ad Azure AD       |![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![Segno di spunta](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Passaggi successivi

[Configurare la registrazione per Windows ](windows-enroll.md)

