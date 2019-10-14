---
title: Criteri di conformità dei dispositivi per i dispositivi Jamf
titleSuffix: Microsoft Intune
description: Usare i criteri di conformità di Microsoft Intune con l'accesso condizionale di Azure Active Directory per proteggere i dispositivi gestiti tramite Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 74ee1eaf0581c4500830514fa9ad272f0de09d3b
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71813989"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Imporre la conformità nei computer Mac gestiti con Jamf Pro

Quando si [integra Jamf Pro con Intune](conditional-access-integrate-jamf.md) è possibile usare i criteri di accesso condizionale per applicare la conformità nei dispositivi Mac con i requisiti dell'organizzazione.  Questo articolo illustra le attività seguenti:  

- Creare criteri di accesso condizionale.
- Configurare Jamf Pro per distribuire l'app Portale aziendale Intune ai dispositivi gestiti con Jamf.
- Configurare i dispositivi per la registrazione con Azure AD quando l'utente del dispositivo accede all'app Portale aziendale avviata dall'app self-service Jamf. La registrazione del dispositivo definisce un'identità in Azure AD che consente la valutazione del dispositivo da parte dei criteri di accesso condizionale, per l'accesso alle risorse aziendali.  
 
Le procedure descritte in questo articolo richiedono l'accesso alle console di Intune e di Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Impostare i criteri di conformità dei dispositivi in Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionare **Conformità del dispositivo** > **Criteri**. 
2. Se si usa un criterio creato in precedenza, selezionare il criterio nella console e quindi andare al passaggio successivo di questa procedura.  
   
   Selezionare **Crea criterio** e quindi specificare i dettagli per un criterio con *Piattaforma* impostata su **macOS**. Configurare *Impostazioni* e *Azioni per la non conformità* in modo da soddisfare i requisiti dell'organizzazione, quindi selezionare **Crea** per salvare il criterio.

3. Nel riquadro *Panoramica* dei criteri selezionare **Assegnazioni**. Usare le opzioni disponibili per configurare quali utenti e gruppi di sicurezza di Azure Active Directory (Azure AD) ricevono questo criterio. L'integrazione di Jamf con Intune non supporta i criteri di conformità che fanno riferimento a gruppi di dispositivi. 

4. Quando si seleziona **Salva** i criteri vengono distribuiti agli utenti.  

I criteri distribuiti sono destinati ai dispositivi usati dagli utenti assegnati. Questi dispositivi vengono valutati per la conformità. I dispositivi conformi vengono contrassegnati come tali in base all'impostazione "*Richiedi che i dispositivi siano contrassegnati come conformi*" in Azure AD.  

> [!NOTE]
> Per la conformità ai requisiti, Intune richiede la crittografia del disco completa.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuire l'app Portale aziendale per macOS in Jamf Pro

Creare criteri in Jamf Pro per distribuire il Portale aziendale Intune. Questi criteri distribuiscono l'app portale aziendale in modo che sia disponibile in Jamf Self Service. Creare i criteri prima di creare in Jamf Pro i criteri che consentono agli utenti di registrare dispositivi con Azure AD.  

Per completare la procedura seguente è necessario accedere a un dispositivo macOS e al portale di Jamf Pro. 

### <a name="to-deploy-the-company-portal-app"></a>Per distribuire l'app Portale aziendale  

1. In un dispositivo macOS scaricare (ma non installare) la versione corrente dell'[app Portale aziendale per macOS](https://go.microsoft.com/fwlink/?linkid=862280). È necessaria solo una copia dell'app, per poterla caricare in Jamf Pro.  

2. Aprire Jamf Pro e passare a **Gestione computer** > **Pacchetti**.

3. Creare un nuovo pacchetto con l'app Portale aziendale per macOS e quindi selezionare **Salva**.

4. Aprire **Computer** > **Criteri** e quindi selezionare **Nuovo**.

5. Usare il payload **Generale** per configurare le impostazioni per i criteri. Specificare le impostazioni seguenti:
   - Attivazione: selezionare **Enrollment Complete** (Completamento registrazione) e **Recurring Check-in** (Check in ricorrente)
   - Frequenza di esecuzione: selezionare **Once per computer** (Una volta per computer)

6. Selezionare il payload **Pacchetti** e fare clic su **Configura**.

7. Fare clic su **Aggiungi** per selezionare il pacchetto con l'app Portale aziendale.

8. Selezionare **Installa** dal menu di scelta rapida **Azione**.
9. Configurare le impostazioni del pacchetto.

10. Selezionare la scheda **Ambito** per specificare in quali computer verrà installata l'app Portale aziendale. Selezionare **Salva**. I criteri verranno eseguiti nei dispositivi inclusi nell'ambito la volta successiva che il trigger selezionato viene attivato nel computer e vengono soddisfatti i criteri presenti nel payload **Generale**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Creare in Jamf Pro i criteri per la registrazione dei dispositivi in Azure Active Directory da parte degli utenti  

Dopo aver [distribuito l'app Portale aziendale](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) per macOS tramite Jamf Pro Self Service, è possibile creare i criteri di Jamf Pro che registrano un dispositivo dell'utente con Azure AD. 

Per la registrazione del dispositivo è necessario che un utente del dispositivo selezioni manualmente l'app Portale aziendale Intune dall'interno di Jamf Self Service. È consigliabile [contattare gli utenti finali](../fundamentals/end-user-educate.md) tramite posta elettronica, notifiche Jamf Pro o qualsiasi altro metodo usato dall'organizzazione e di richiedere loro di completare questa operazione per registrare i dispositivi. 

> [!WARNING]
> Se l'app Portale aziendale viene avviata manualmente, ad esempio dalle cartelle Applicazioni o Download, il dispositivo non viene registrato. Se l'utente del dispositivo avvia manualmente l'app Portale aziendale, viene visualizzato l'avviso **'AccountNotOnboarded'** .

### <a name="to-create-the-registration-policy"></a>Per creare i criteri di registrazione  

1. In Jamf Pro passare a **Computer** > **Criteri** e creare nuovi criteri per la registrazione del dispositivo.

2. Configurare il payload **Microsoft Intune Integration** (Integrazione Microsoft Intune), incluse le impostazioni di attivazione e frequenza di esecuzione.

3. Selezionare la scheda **Ambito** e includere i criteri nell'ambito di tutti i dispositivi di destinazione.

4. Selezionare la scheda **Self Service** per rendere i criteri disponibili in Jamf Self Service. Includere i criteri nella categoria **Conformità del dispositivo**. Fare clic su **Save**.

## <a name="validate-intune-and-jamf-integration"></a>Convalidare l'integrazione di Intune e Jamf  

Usare la console Jamf Pro per verificare che le comunicazioni tra Jamf Pro e Microsoft Intune funzionino correttamente. 

- In Jamf Pro passare a **Settings** (Impostazioni) > **Global Management** (Gestione globale) > **Microsoft Intune Integration** (Integrazione con Microsoft Intune), quindi selezionare **Test**. 

    Nella console un messaggio indica l'esito positivo o negativo della connessione.  

Se il test della connessione dalla console Jamf Pro ha esito negativo, esaminare la configurazione di Jamf. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Rimozione di un dispositivo gestito da Jamf da Intune

È possibile rimuovere un dispositivo gestito da Jamf dalla console di Intune selezionando **Elimina** nella vista **Tutti i dispositivi**. L'eliminazione in blocco dei dispositivi può essere abilitata selezionando più dispositivi e facendo clic su **Elimina**.

Ottenere informazioni su come [rimuovere un dispositivo gestito da Jamf nella documentazione di Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Per altre informazioni, è anche possibile registrare un ticket di supporto presso il [supporto Jamf](https://www.jamf.com/support/). 

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introduzione all'accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
