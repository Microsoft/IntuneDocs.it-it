---
title: Registrazione in blocco per Windows 10
titleSuffix: Microsoft Intune
description: Creare un pacchetto di registrazione in blocco per Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: spshumwa
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cbdd99dfb7b42677048b4f214e7de537db0edda
ms.sourcegitcommit: 5db0769274d788a1218dca3ad90d8649927becb4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925831"
---
# <a name="bulk-enrollment-for-windows-devices"></a>Registrazione in blocco per dispositivi Windows

L'amministratore può aggiungere un numero elevato di nuovi dispositivi Windows ad Azure Active Directory e Intune. Per eseguire la registrazione in blocco dei dispositivi per il tenant di Azure AD, è necessario creare un pacchetto di provisioning con l'Applicazione immagine e configurazione di Windows. Quando si applica il pacchetto di provisioning ai dispositivi aziendali, questi vengono aggiunti al tenant di Azure AD e vengono registrati per la gestione di Intune. Una volta applicato il pacchetto, gli utenti di Azure AD possono eseguire l'accesso.

Gli utenti di Azure AD sono utenti standard di questi dispositivi e devono conformarsi a criteri di Intune assegnati e applicazioni obbligatorie. I dispositivi Windows registrati in Intune tramite la registrazione in blocco di Windows possono usare l'app Portale aziendale per installare le app disponibili. 

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Prerequisiti per la registrazione in blocco di dispositivi Windows

- Dispositivi che eseguano Windows 10 Creators Update (build 1703) o versione successiva
- [Registrazione automatica di Windows](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Creare un pacchetto di provisioning

1. Scaricare [Progettazione configurazione di Windows](https://www.microsoft.com/store/apps/9nblggh4tx22) da Microsoft Store.
   ![Screenshot dallo Store dell'app Progettazione configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-store.png)

2. Aprire l'**Applicazione immagine e configurazione di Windows** e selezionare **Provision desktop devices** (Esegui provisioning dispositivi desktop).
   ![Schermata della selezione del provisioning dei dispositivi desktop nell'Applicazione immagine e configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-select.png)

3. Si apre la finestra **Nuovo progetto** in cui è necessario specificare le informazioni seguenti:
   - **Name** (Nome): il nome del progetto
   - **Cartella di progetto**: percorso di salvataggio per il progetto
   - **Description** (Descrizione): una descrizione facoltativa del progetto ![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-name.png)

4. Specificare un nome univoco per i dispositivi. I nomi possono includere un numero di serie (%NUMERO DI SERIE%) o un set di caratteri casuali. Facoltativamente, è anche possibile immettere un codice Product Key, se si vuole aggiornare l'edizione di Windows, configurare il dispositivo per la condivisione e rimuovere software pre-installato.
   
   ![Screenshot della schermata in cui specificare nome e codice Product Key nell'app Progettazione configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-device.png)

5. Facoltativamente, è possibile configurare la rete Wi-Fi alla quale i dispositivi si connettono quando vengono avviati per la prima volta.  Se i dispositivi di rete non sono configurati, quando il dispositivo viene avviato per la prima volta è necessaria una connessione di rete cablata.
   ![Schermata di abilitazione Wi-Fi inclusi SSID di rete e opzioni del tipo di rete nell'Applicazione immagine e configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-network.png)

6. Selezionare **Enroll in Azure AD** (Registra in Azure AD), immettere una data per **Bulk Token Expiry** (Scadenza token in blocco) e selezionare **Get Bulk Token** (Ottieni token in blocco).
   ![Screenshot della schermata di gestione degli account nell'app Progettazione configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-account.png)

7. Specificare le credenziali di Azure AD per ottenere un token in blocco.
   ![Screenshot della schermata di accesso all'app Progettazione configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-cred.png)

8. Fare clic su **Next** (Avanti) quando **Bulk Token** (Token in blocco) viene recuperato correttamente.

9. Facoltativamente, è possibile selezionare **Add applications** (Aggiungi applicazioni) e **Add certificates** (Aggiungi certificati). Verrà eseguito il provisioning di tali applicazioni e certificati nel dispositivo.

10. Facoltativamente, è possibile proteggere il pacchetto di provisioning con una password.  Scegliere **Crea**.
    ![Screenshot della protezione del pacchetto nell'app Progettazione configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-create.png)

## <a name="provision-devices"></a>Eseguire il provisioning dei dispositivi

1. Accedere al pacchetto di provisioning nel percorso specificato in **Project folder** (Cartella progetto) nell'app.

2. Scegliere la modalità di applicazione del pacchetto di provisioning nel dispositivo.  Un pacchetto di provisioning può essere applicato a un dispositivo in uno dei modi seguenti:
   - Archiviare il pacchetto di provisioning in un'unità USB, inserire l'unità USB nel dispositivo di cui eseguire la registrazione in blocco e applicare il pacchetto durante l'installazione iniziale
   - Archiviare il pacchetto di provisioning in una cartella di rete e applicarlo dopo l'installazione iniziale

   Per istruzioni dettagliate sull'applicazione di un pacchetto di provisioning, vedere [Apply a provisioning package](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package) (Applicare un pacchetto di provisioning).

3. Dopo aver applicato il pacchetto, il dispositivo verrà riavviato automaticamente in un minuto.
   ![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](./media/windows-bulk-enroll/bulk-enroll-add.png)

4. Al riavvio del dispositivo, questo si connette ad Azure Active Directory e viene registrato in Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Risoluzione dei problemi relativi alla registrazione in blocco di Windows

### <a name="provisioning-issues"></a>Problemi di provisioning
Il provisioning deve essere usato su nuovi dispositivi Windows. La correzione degli errori di provisioning potrebbe richiedere una cancellazione del dispositivo o il ripristino dall'immagine di avvio. Gli esempi seguenti descrivono alcuni dei motivi per cui si verificano errori di provisioning:

- Un pacchetto di provisioning che tenta di aggiungere un dominio di Active Directory o un tenant di Azure Active Directory che non crea un account locale potrebbe rendere il dispositivo non raggiungibile, se il processo di aggiunta al dominio ha esito negativo a causa della mancanza di connettività di rete.
- Gli script eseguiti dal pacchetto di provisioning vengono eseguiti nel contesto del sistema. Gli script possono apportare modifiche arbitrarie al file system e alle configurazioni del dispositivo. Uno script dannoso o errato potrebbe compromettere lo stato del dispositivo al punto che questo possa essere ripristinato solo recuperandone l'immagine o cancellandolo.

È possibile verificare l'esito positivo o negativo delle impostazioni nel pacchetto nel registro amministrativo **Provisioning-Diagnostics-Provider** nel Visualizzatore eventi.

### <a name="bulk-enrollment-with-wi-fi"></a>Registrazione in blocco con Wi-Fi 

Quando non si usa una rete aperta, è necessario usare [certificati a livello di dispositivo](../protect/certificates-configure.md) per avviare le connessioni. Non è possibile usare i certificati destinati agli utenti per l'accesso alla rete di dispositivi registrati in blocco. 

### <a name="conditional-access"></a>Accesso condizionale
L'accesso condizionale non è disponibile per i dispositivi Windows registrati con la registrazione in blocco.
