---
title: Criteri di conformità dei dispositivi per i dispositivi Jamf
titleSuffix: Microsoft Intune
description: Usare i criteri di conformità di Microsoft Intune con l'accesso condizionale di Azure Active Directory per proteggere i dispositivi gestiti tramite Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3542d86429293531a22678e14520e59cd9de9dc6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721539"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Imporre la conformità nei computer Mac gestiti con Jamf Pro

Si applica a: Intune nel portale di Azure

È possibile usare Azure Active Directory e i criteri di accesso condizionale di Microsoft Intune per verificare che gli utenti finali siano conformi ai requisiti dell'organizzazione. È possibile applicare questi criteri anche a computer Mac [gestiti con Jamf Pro](conditional-access-integrate-jamf.md). A questo scopo, è necessario l'accesso a entrambe le console di Intune e Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Impostare i criteri di conformità dei dispositivi in Intune

1. Aprire Microsoft Azure e quindi passare a **Intune** > **Conformità del dispositivo** > **Criteri**. È possibile creare criteri specifici per macOS, tra cui scegliere una serie di azioni, ad esempio inviare messaggi di posta elettronica di avviso, per gli utenti e i gruppi non conformi.
2. Selezionare i criteri > Assegnazioni. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere Gruppi selezionati per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vogliono applicare questi criteri > scegliere Salva per distribuire i criteri agli utenti.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui sono assegnati i criteri vengono valutati per verificarne la conformità e contrassegnati come conformi per l'impostazione "Richiedi che i dispositivi siano contrassegnati come conformi" in Azure Active Directory.

> [!Note]
> Per la conformità ai requisiti, Intune richiede la crittografia del disco completa.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuire l'app Portale aziendale per macOS in Jamf Pro

È necessario distribuire l'app Portale aziendale per macOS in Jamf Pro come installazione in background seguendo questa procedura:

1. In un dispositivo macOS scaricare la versione corrente dell'[app Portale aziendale per macOS](https://go.microsoft.com/fwlink/?linkid=862280). Non installarla. È necessaria una copia dell'app da caricare in Jamf Pro.
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
> Prima di passare alla procedura successiva, è necessario [distribuire l'app Portale aziendale](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) per macOS.  

Gli utenti finali devono avviare l'app Portale aziendale tramite Jamf Self Service in modo da registrare il dispositivo con Azure AD come dispositivo gestito da Jamf Pro. Questa operazione richiede l'azione degli utenti finali. Si consiglia di [contattare l'utente finale](../fundamentals/end-user-educate.md) tramite posta elettronica, notifiche di Jamf Pro o altri metodi di notifica per richiedere di fare clic sul pulsante in Jamf Self Service.

> [!WARNING]
> Per iniziare la registrazione del dispositivo, l'app Portale aziendale deve essere avviata da Jamf Self Service. <br><br>Se l'app Portale aziendale viene avviata manualmente, ad esempio dalle cartelle Applicazioni o Download, il dispositivo non viene registrato. Se l'utente finale avvia manualmente il portale aziendale, viene visualizzato l'avviso 'AccountNotOnboarded'.

1. In Jamf Pro passare a **Computer** > **Criteri** e creare nuovi criteri per la registrazione del dispositivo.
2. Configurare il payload **Microsoft Intune Integration** (Integrazione Microsoft Intune), incluse le impostazioni di attivazione e frequenza di esecuzione.
3. Fare clic sulla scheda **Ambito** e includere nell'ambito dei criteri tutti i dispositivi di destinazione.
4. Fare clic sulla scheda **Self Service** per rendere i criteri disponibili in Jamf Self Service. Includere i criteri nella categoria **Conformità del dispositivo**. Fare clic su **Save**.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Rimozione di un dispositivo gestito da Jamf da Intune

È possibile rimuovere un dispositivo gestito da Jamf dalla console di Intune selezionando **Elimina** nella vista **Tutti i dispositivi**. L'eliminazione in blocco dei dispositivi può essere abilitata selezionando più dispositivi e facendo clic su **Elimina**.

Ottenere informazioni su come [rimuovere un dispositivo gestito da Jamf nella documentazione di Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Per altre informazioni, è anche possibile registrare un ticket di supporto presso il [supporto Jamf](https://www.jamf.com/support/). 

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introduzione all'accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)