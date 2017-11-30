---
title: "Applicare criteri di conformità a dispositivi gestiti da Jamf"
titlesuffix: Azure portal
description: "Usare i criteri di conformità per proteggere i dispositivi gestiti da Jamf."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dd84812a7e7dcf83f01c8d4d2b613706f7700775
ms.sourcegitcommit: b2a6678a0e9617f94ee8c65e7981211483b30ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Imporre la conformità nei computer Mac gestiti con Jamf Pro

|Si applica a: Intune nel Portale di Azure |
|--|
|Serve documentazione su Intune nel portale classico? [Fare clic qui](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Attualmente in anteprima privata|
|--|
|Le funzionalità descritte in questo argomento sono disponibili solo ai clienti attualmente registrati per l'anteprima privata. Questo messaggio verrò rimosso dopo il rilascio per tutti i clienti.|
| |

È possibile usare Azure Active Directory e i criteri di accesso condizionale di Microsoft Intune per verificare che gli utenti finali siano conformi ai requisiti dell'organizzazione. È possibile applicare questi criteri anche a computer Mac [gestiti con Jamf Pro](conditional-access-integrate-jamf.md). A questo scopo, è necessario l'accesso a entrambe le console di Intune e Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Impostare i criteri di conformità dei dispositivi in Intune

1. Aprire Microsoft Azure e quindi passare a **Intune** > **Conformità del dispositivo** > **Criteri**. È possibile creare criteri specifici per macOS, tra cui scegliere una serie di azioni (ad esempio, inviare messaggi di posta elettronica di avviso) per gli utenti e i gruppi non conformi.
2. Cercare i gruppi desiderati e applicare ad essi i criteri.

## <a name="require-the-company-portal-app-for-macos"></a>Richiedere l'app Portale aziendale per macOS

1. In un dispositivo macOS passare a https://aka.ms/macoscompanyportal per scaricare la versione corrente dell'app Portale aziendale per macOS.
2. Aprire Jamf Pro e quindi passare a **Gestione computer** > **Pacchetti**.
3. Creare un nuovo pacchetto con l'app Portale aziendale per macOS e quindi fare clic su **Salva**.
4. Aprire **Computer** > **Criteri** e quindi selezionare **Nuovo**.
5. Usare il payload **Generale** per configurare le impostazioni relative ai criteri, tra cui il trigger e la frequenza di esecuzione.
6. Selezionare il payload **Pacchetti** e fare clic su **Configura**.
7. Fare clic su **Aggiungi** per selezionare il pacchetto con l'app Portale aziendale.
8. Scegliere **Installa** dal menu di scelta rapida **Azione**.
9. Configurare le impostazioni del pacchetto.
10. Fare clic sulla scheda **Ambito** per specificare in quali computer dovrà essere installata l'app Portale aziendale. Fare clic su **Save**. I dispositivi inclusi nell'ambito verranno eseguiti dai criteri la volta successiva in cui il trigger selezionato viene attivato nel computer e soddisfa i criteri presenti nel payload **Generale**.

## <a name="direct-your-users-to-register-jamf-pro-managed-devices-with-azure-active-directory"></a>Indicare agli utenti di registrare i dispositivi gestiti da Jamf Pro con Azure Active Directory

> [!NOTE]
> Prima di passare alla procedura successiva, è necessario [distribuire l'app Portale aziendale](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) per macOS.  

Gli utenti finali devono avviare l'app Portale aziendale tramite Jamf Self Service in modo da registrare il dispositivo con Azure AD come dispositivo gestito da Jamf Pro.

1. In Jamf Pro passare a **Computer** > **Criteri** e creare nuovi criteri per la registrazione del dispositivo.
2. Configurare il payload **Accesso condizionale**, incluse le impostazioni relative al trigger e alla frequenza di esecuzione. Impostare la priorità su **Dopo**.
3. Fare clic sulla scheda **Ambito** e includere nell'ambito dei criteri tutti i dispositivi di destinazione.
4. Fare clic sulla scheda **Self Service** per rendere i criteri disponibili in Jamf Self Service. Includere i criteri nella categoria **Conformità del dispositivo**. Fare clic su **Save**.

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Get started with conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started) (Introduzione all'accesso condizionale in Azure Active Directory)
