---
title: Registrare dispositivi Windows con il programma Windows AutoPilot Deployment
description: Informazioni su come registrare nuovi dispositivi Windows 10 con il programma Windows AutoPilot Deployment.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 736eda24e355024e2abadd57206c0f0423e6d4b4
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>Registrare dispositivi Windows con il programma Windows AutoPilot Deployment
Il programma Windows AutoPilot Deployment semplifica il provisioning dei dispositivi. Oggi, la compilazione e la gestione di immagini del sistema operativo personalizzate richiedono molto tempo. Allo stesso modo, l'applicazione di queste immagini personalizzate del sistema operativo ai nuovi dispositivi per prepararli per l'uso prima della consegna agli utenti finali richiede molto tempo. Con Microsoft Intune e AutoPilot è possibile assegnare i nuovi dispositivi agli utenti finali senza la necessità di compilare, gestire e applicare le immagini del sistema operativo personalizzate ai dispositivi. Quando si usa Intune per gestire i dispositivi AutoPilot, è possibile gestire criteri, profili, applicazioni, e così via, sui dispositivi dopo che sono stati registrati. Per una panoramica di vantaggi, scenari e prerequisiti, vedere [Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot) (Panoramica di Windows AutoPilot).

## <a name="prerequisites"></a>Prerequisiti
- [I dispositivi devono essere registrati per l'organizzazione](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot#registering-devices-to-your-organization)
- [La registrazione automatica di Windows deve essere abilitata](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- È necessario avere una [sottoscrizione di Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Sincronizzare i dispositivi
Sincronizzare i dispositivi registrati in Intune in modo da poterli configurare.

1. Accedere ad [Azure](https://portal.azure.com/).
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
4. Nel pannello **Registrazione Windows** nella sezione **Programma Windows AutoPilot Deployment**  scegliere **Dispositivi**.
5. Fare clic su **Sincronizza** per importare i dispositivi registrati. Viene visualizzato un messaggio che informa che è in corso la sincronizzazione.
6. Aggiornare la vista per visualizzare i nuovi dispositivi. Il processo potrebbe richiedere alcuni minuti, a seconda di quanti dispositivi sono in corso di sincronizzazione.  

## <a name="create-an-autopilot-deployment-profile"></a>Creare un profilo di distribuzione AutoPilot
I profili di distribuzione AutoPilot vengono usati per configurare i dispositivi AutoPilot.
1. Accedere ad [Azure](https://portal.azure.com/). 
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
4. Nel pannello **Registrazione Windows** nella sezione **Programma Windows AutoPilot Deployment**  scegliere **Profili di distribuzione**.
5. Fare clic su **Crea profilo** e scegliere un nome e una descrizione facoltativa. 
6. Per **Tipo di join** selezionare **Aggiunto ad Azure AD**.
7. In **Configurazione guidata** configurare le opzioni seguenti e quindi fare clic su **OK**: 
   - **Impostazioni privacy**: scegliere se visualizzare le impostazioni di privacy per gli utenti. 
   - **Contratto di licenza con l'utente finale**: scegliere se visualizzare il contratto di licenza per gli utenti.
   - **Tipo di account utente**: scegliere se il tipo di account utente è un utente **Amministratore** o **Standard**.

     > [!Note]    
     > Questa impostazione non si applica agli account Amministratore globale o Amministratore società. Questi account non possono essere utenti standard perché hanno accesso a tutte le funzionalità amministrative di Azure AD.
8. Fare clic su **Crea** per creare il profilo. Il profilo di distribuzione AutoPilot è ora disponibile per l'assegnazione ai dispositivi.
     
> [!Note]    
> Con tutti i profili di distribuzione AutoPilot vengono configurate le impostazioni seguenti:
> - Ignorare Cortana, OneDrive e pagine di configurazione di registrazione OEM
> - Configurazione automatica per l'azienda o l'istituto di istruzione
> - Esperienza di accesso con il marchio aziendale o dell'istituto di istruzione    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Avvisi per dispositivi non assegnati per Windows AutoPilot <!-- 163236 -->
È possibile visualizzare un avviso per i dispositivi Windows AutoPilot non assegnati per verificare il numero di dispositivi dal programma AutoPilot che non hanno profili distribuzione AutoPilot assegnati. Usare le informazioni contenute nell'avviso per creare profili e assegnarli ai dispositivi non assegnati. Quando si sceglie l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e informazioni dettagliate su di essi. 
1. Accedere ad [Azure](https://portal.azure.com/). 
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
4. Scegliere **Panoramica** per visualizzare l'avviso. Fare clic sull'avviso per visualizzare un elenco di dispositivi AutoPilot.  

## <a name="assign-an-autopilot-deployment-profile"></a>Assegnare un profilo di distribuzione AutoPilot
Dopo aver creato i profili di distribuzione AutoPilot è possibile assegnarli ai dispositivi selezionati.

1. Accedere ad [Azure](https://portal.azure.com/). 
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
4. Nel pannello **Registrazione Windows** nella sezione **Programma Windows AutoPilot Deployment**  scegliere **Dispositivi**.
5. Scegliere i dispositivi a cui si vuole assegnare il profilo di distribuzione. È possibile filtrare la colonna **Stato** per trovare facilmente i dispositivi senza un profilo assegnato. 
6. Fare clic su **Assegna profilo**, selezionare il profilo di distribuzione AutoPilot e quindi fare clic su **Assegna**. Viene visualizzato un messaggio che informa che è in corso l'assegnazione.
7. Aggiornare la vista per vedere che il profilo è stato assegnato ai dispositivi. Il processo potrebbe richiedere alcuni minuti, a seconda di quanti dispositivi sono stati selezionati. 

> [!Note]
> Il nuovo profilo viene assegnato al dispositivo. Il profilo non verrà tuttavia applicato ai dispositivi già registrati in Intune finché non saranno state completate la reimpostazione e la nuova registrazione.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Assegnare un profilo di distribuzione AutoPilot diverso
Dopo aver assegnato un profilo di distribuzione AutoPilot a un dispositivo, se si decide di assegnare un profilo diverso è possibile assegnare il nuovo profilo al dispositivo.  

## <a name="edit-an-autopilot-deployment-profile"></a>Modificare un profilo di distribuzione AutoPilot 
Dopo aver creato un profilo di distribuzione AutoPilot, è possibile modificare alcune parti del profilo di distribuzione.   
1. Accedere ad [Azure](https://portal.azure.com/). 
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Registrazione del dispositivo**.
4. Nel pannello **Registrazione Windows** nella sezione **Programma Windows AutoPilot Deployment**  scegliere **Profili di distribuzione**. 
5. Selezionare il profilo da modificare. 
6. Fare clic su **Proprietà** a sinistra per modificare il nome o la descrizione del profilo di distribuzione. Fare clic su **Salva** dopo aver apportato le modifiche. 
7. Fare clic su **Impostazioni** per apportare modifiche alle impostazioni della configurazione guidata. Fare clic su **Salva** dopo aver apportato le modifiche. 

> [!NOTE]
> Il profilo aggiornato viene assegnato ai dispositivi. Il profilo aggiornato non verrà tuttavia applicato a un dispositivo già registrato in Intune finché non saranno state completate la reimpostazione e la nuova registrazione del dispositivo. 

## <a name="using-autopilot-in-other-portals"></a>Uso di AutoPilot in altri portali
Se non si è interessati alla gestione di dispositivi mobili, è possibile usare AutoPilot, ad esempio, in Microsoft Store per le aziende. Benché sia possibile l'uso di altri portali, è consigliabile usare solo Intune per gestire le distribuzioni AutoPilot. Se si usa Intune e un altro portale, Intune non è in grado di:
- Visualizzare le modifiche apportate ai profili creati in Intune ma modificati in un altro portale
- Sincronizzare i profili creati in un altro portale
- Visualizzare le modifiche apportate alle assegnazioni dei profili eseguite in un altro portale
- Sincronizzare le assegnazioni dei profili eseguite in un altro portale

## <a name="next-steps"></a>Passaggi successivi
Dopo aver configurato Windows AutoPilot per i dispositivi Windows 10 registrati, scoprire come gestire i dispositivi. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.com/intune/device-management)