---
title: Registrazione in blocco per Windows 10
description: Creare un pacchetto di registrazione in blocco per Microsoft Intune
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0053e37a-f26e-452f-9524-5039a635b52e
ms.reviewer: damionw
ms.custom: intune-classic
ms.openlocfilehash: ab52ba70403da5192cd3539dfd6d1e64bd79268c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Registrazione in blocco per dispositivi Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

L'amministratore può aggiungere un numero elevato di nuovi dispositivi Windows ad Azure Active Directory e Intune. Per eseguire la registrazione in blocco dei dispositivi per il tenant di Azure AD, è necessario creare un pacchetto di provisioning con l'Applicazione immagine e configurazione di Windows. Quando si applica il pacchetto di provisioning ai dispositivi aziendali, questi vengono aggiunti al tenant di Azure AD e vengono registrati per la gestione di Intune. Una volta applicato il pacchetto, gli utenti di Azure AD possono eseguire l'accesso.

Gli utenti di Azure AD sono utenti standard di questi dispositivi e devono conformarsi a criteri di Intune assegnati e applicazioni obbligatorie. Al momento non sono supportati scenari self-service o con il portale aziendale.

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Prerequisiti per la registrazione in blocco di dispositivi Windows

Per la registrazione in blocco per dispositivi Windows, è necessario quanto segue:

- Dispositivi che eseguano Windows 10 Creators Update o versione successiva
- [Registrazione automatica di Windows](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Creare un pacchetto di provisioning

1. Scaricare [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22) (Applicazione immagine e configurazione di Windows) da Windows Store.
![Screenshot e descrizione dallo Store dell'app Applicazione immagine e configurazione di Windows](../media/bulk-enroll-store.png)

2. Aprire l'**Applicazione immagine e configurazione di Windows** e selezionare **Provision desktop devices** (Esegui provisioning dispositivi desktop).
![Schermata della selezione del provisioning dei dispositivi desktop nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-select.png)

3. Si apre la finestra **New project** (Nuovo progetto) dove è necessario specificare quanto segue:
  - **Name** (Nome): il nome del progetto
  - **Project folder** (Cartella progetto): la cartella in cui verrà salvato il nuovo progetto
  - **Description** (Descrizione): una descrizione facoltativa del progetto ![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-name.png)

4.  Specificare un nome univoco per i dispositivi. I nomi possono includere un numero di serie (%%NUMERO DI SERIE%%) o un set di caratteri casuali. Facoltativamente, è anche possibile immettere un codice Product Key, se si vuole aggiornare l'edizione di Windows, configurare il dispositivo per la condivisione e rimuovere software pre-installato.<BR>
![Screenshot della finestra in cui specificare nome, cartella di progetto e descrizione nell'app Progettazione configurazione di Windows](../media/bulk-enroll-device.png)

5.  Facoltativamente, è possibile configurare la rete Wi-Fi alla quale i dispositivi si connettono quando vengono avviati per la prima volta.  Se questa non viene configurata, quando il dispositivo viene avviato per la prima volta è necessaria una connessione di rete cablata.
![Schermata di abilitazione Wi-Fi inclusi SSID di rete e opzioni del tipo di rete nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-network.png)

6.  Selezionare **Enroll in Azure AD** (Registra in Azure AD), immettere una data per **Bulk Token Expiry** (Scadenza token in blocco) e selezionare **Get Bulk Token** (Ottieni token in blocco).
![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-account.png)

7. Specificare le credenziali di Azure AD per ottenere un token in blocco.
![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-cred.png)

8.  Fare clic su **Next** (Avanti) quando **Bulk Token** (Token in blocco) viene recuperato correttamente.

9. Facoltativamente, è possibile selezionare **Add applications** (Aggiungi applicazioni) e **Add certificates** (Aggiungi certificati). Verrà eseguito il provisioning di tali applicazioni e certificati nel dispositivo.

10. Facoltativamente, è possibile proteggere il pacchetto di provisioning con una password.  Scegliere **Crea**.
![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-create.png)

## <a name="provision-devices"></a>Eseguire il provisioning dei dispositivi

1. Accedere al pacchetto di provisioning nel percorso specificato in **Project folder** (Cartella progetto) nell'app.

2. Scegliere la modalità di applicazione del pacchetto di provisioning nel dispositivo.  Un pacchetto di provisioning può essere applicato a un dispositivo in uno dei modi seguenti:
 - Archiviare il pacchetto di provisioning in un'unità USB, inserire l'unità USB nel dispositivo di cui eseguire la registrazione in blocco e applicare il pacchetto durante l'installazione iniziale
 - Archiviare il pacchetto di provisioning in una cartella di rete e applicarlo nel dispositivo di cui si vuole eseguire la registrazione in blocco dopo l'installazione iniziale

 Per istruzioni dettagliate sull'applicazione di un pacchetto di provisioning, vedere [Apply a provisioning package](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package) (Applicare un pacchetto di provisioning).

3. Dopo aver applicato il pacchetto, il dispositivo verrà riavviato automaticamente in 1 minuto.
 ![Screenshot della schermata in cui specificare nome, cartella di progetto e descrizione nell'Applicazione immagine e configurazione di Windows](../media/bulk-enroll-add.png)

4. Al riavvio del dispositivo, questo si connette ad Azure Active Directory e viene registrato in Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Risoluzione dei problemi relativi alla registrazione in blocco di Windows

Il provisioning deve essere usato su nuovi dispositivi Windows. Gli errori di provisioning potrebbero richiedere un ripristino delle impostazioni predefinite del dispositivo o il ripristino dall'immagine di avvio. Gli esempi seguenti descrivono alcuni dei motivi per cui si verificano errori di provisioning:

- Un pacchetto di provisioning che tenta di aggiungere un dominio di Active Directory o un tenant di Azure Active Directory che non crea un account locale potrebbe rendere il dispositivo non raggiungibile, se il processo di aggiunta al dominio ha esito negativo a causa della mancanza di connettività di rete.
- Gli script eseguiti dal pacchetto di provisioning vengono eseguiti nel contesto di sistema e possono apportare modifiche arbitrarie al file system e alle configurazioni del dispositivo. Uno script dannoso o errato potrebbe compromettere lo stato del dispositivo al punto che questo possa essere ripristinato solo recuperandone l'immagine o ripristinandone le impostazioni predefinite.
