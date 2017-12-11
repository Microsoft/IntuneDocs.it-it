---
title: "Applicare criteri di conformità a dispositivi gestiti da Jamf"
titlesuffix: Azure portal
description: "Usare i criteri di conformità per proteggere i dispositivi gestiti da Jamf."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06cc4d70b30ec92946baefbc020aa4cda28b0c88
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
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

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuire l'app Portale aziendale per macOS in Jamf Pro

Esistono due modi per distribuire l'app Portale aziendale per macOS in Jamf Pro:

- Rendere disponibile la distribuzione dell'app Portale aziendale in Jamf Self-Service oppure
- Come installazione in background in modo che gli utenti eseguano la procedura seguente:

1. In un dispositivo macOS scaricare la versione corrente dell'[app Portale aziendale per macOS](https://go.microsoft.com/fwlink/?linkid=862280).
2. Aprire Jamf Pro e quindi passare a **Gestione computer** > **Pacchetti**.
3. Creare un nuovo pacchetto con l'app Portale aziendale per macOS e quindi fare clic su **Salva**.
4. Aprire **Computer** > **Criteri** e quindi selezionare **Nuovo**.
5. Usare il payload **Generale** per configurare le impostazioni per i criteri. Specificare le impostazioni seguenti: 
   - Attivazione: selezionare **Enrollment Complete** (Completamento registrazione) e **Recurring Check-in** (Check in ricorrente)
   - Frequenza di esecuzione: selezionare **Once per computer** (Una volta per computer)
6. Selezionare il payload **Pacchetti** e fare clic su **Configura**.
7. Fare clic su **Aggiungi** per selezionare il pacchetto con l'app Portale aziendale.
8. Scegliere **Installa** dal menu di scelta rapida **Azione**.
9. Configurare le impostazioni del pacchetto.
10. Fare clic sulla scheda **Ambito** per specificare in quali computer dovrà essere installata l'app Portale aziendale. Fare clic su **Save**. I dispositivi inclusi nell'ambito verranno eseguiti dai criteri la volta successiva in cui il trigger selezionato viene attivato nel computer e soddisfa i criteri presenti nel payload **Generale**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Creare in Jamf Pro i criteri per la registrazione dei dispositivi in Azure Active Directory da parte degli utenti

> [!NOTE]
> Prima di passare alla procedura successiva, è necessario [distribuire l'app Portale aziendale](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) per macOS.  

Gli utenti finali devono avviare l'app Portale aziendale tramite Jamf Self Service in modo da registrare il dispositivo con Azure AD come dispositivo gestito da Jamf Pro. Questa operazione richiede l'azione degli utenti finali. Si consiglia di [contattare l'utente finale](end-user-educate.md) tramite posta elettronica, notifiche di Jamf Pro o altri metodi di notifica per richiedere di fare clic sul pulsante in Jamf Self Service.

> [!WARNING]
> Per iniziare la registrazione del dispositivo, l'app Portale aziendale deve essere avviata da Jamf Self Service. <br><br>Se l'app Portale aziendale viene avviata manualmente, ad esempio dalle cartelle Applicazioni o Download, il dispositivo non viene registrato. Se l'utente finale avvia manualmente il portale aziendale, viene visualizzato l'avviso 'AccountNotOnboarded'.

1. In Jamf Pro passare a **Computer** > **Criteri** e creare nuovi criteri per la registrazione del dispositivo.
2. Configurare il payload **Microsoft Intune Integration** (Integrazione Microsoft Intune), incluse le impostazioni di attivazione e frequenza di esecuzione. Impostare la priorità su **Dopo**.
3. Fare clic sulla scheda **Ambito** e includere nell'ambito dei criteri tutti i dispositivi di destinazione.
4. Fare clic sulla scheda **Self Service** per rendere i criteri disponibili in Jamf Self Service. Includere i criteri nella categoria **Conformità del dispositivo**. Fare clic su **Save**.

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Get started with conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started) (Introduzione all'accesso condizionale in Azure Active Directory)