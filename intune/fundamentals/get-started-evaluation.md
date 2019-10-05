---
title: Che cosa può fare Microsoft Intune per la mia azienda
titleSuffix: ''
description: Problemi aziendali comuni che Microsoft Intune contribuisce a risolvere.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 845eb22522895e04f6ec4f46eda7a817e27a830c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726531"
---
# <a name="what-can-intune-do-for-my-company"></a>Che cosa può fare Intune per la mia azienda?
Microsoft Intune è un servizio di gestione della mobilità aziendale (EMM) basato su cloud che consente alla forza lavoro di essere produttiva, garantendo al tempo stesso la protezione dei dati aziendali.

Con Intune, è possibile:

- Gestire i dispositivi mobili usati dalla forza lavoro per accedere ai dati aziendali.
- Gestire le app per dispositivi mobili usate dalla forza lavoro.
- Proteggere le informazioni aziendali grazie alla possibilità di controllare le modalità di accesso e condivisione dei dati da parte della forza lavoro.
- Assicurarsi che i dispositivi e le app siano conformi ai requisiti di sicurezza aziendali.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemi aziendali comuni che Intune contribuisce a risolvere

* [Proteggere dati e messaggi di posta elettronica a livello locale in modo da consentire l'accesso dai dispositivi mobili](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteggere dati e messaggi di posta elettronica di Office 365 in modo da consentire l'accesso sicuro dai dispositivi mobili](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Rilasciare telefoni di proprietà dell'azienda alla forza lavoro](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Offrire un programma BYOD (Bring Your Own Device) o per un dispositivo personale a tutti i dipendenti](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Abilitare i dipendenti per l'accesso protetto a Office 365 da un chiosco pubblico non gestito](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuire tablet condivisi con limitazioni d'uso ai dipendenti](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Guida introduttiva

Affrontare la gestione dei dispositivi mobili può essere difficile inizialmente. Sono molte le decisioni da prendere per conto della propria azienda. Gli argomenti di avvio rapido seguenti consentono di iniziare ad usare Intune e svolgere alcune attività comuni impiegando una quantità minima di tempo.

È possibile seguire l'ordine previsto degli argomenti di **avvio rapido** facendo riferimento al sommario nella parte sinistra della pagina.

- [Provare Intune gratuitamente](free-trial-sign-up.md) - Creare una sottoscrizione gratuita per provare Intune in un ambiente di test.    
- [Creare un utente](quickstart-create-user.md) - Aggiungere un utente a Intune per consentirgli di accedere alle risorse aziendali dai dispositivi mobili.
- [Creare un gruppo](quickstart-create-group.md) - Organizzare gli utenti in gruppi per semplificare la gestione dei criteri e delle app a cui possono accedere.
- [Configurare la registrazione automatica](../enrollment/quickstart-setup-auto-enrollment.md) - Configurare Intune per registrare automaticamente i dispositivi quando utenti specifici eseguono l'accesso a dispositivi Windows 10.
- [Registrare il dispositivo](../enrollment/quickstart-enroll-windows-device.md) - Assumere il ruolo di un utente di Intune e registrare il dispositivo in Intune. Tornare quindi a Intune e verificare che il dispositivo sia registrato correttamente.
- [Creare un criterio di conformità del dispositivo](../protect/quickstart-set-password-length-android.md): creare un criterio di conformità del dispositivo e assegnare un gruppo al criterio.
- [Inviare notifiche ai dispositivi non conformi](../protect/quickstart-send-notification.md) - Inviare una notifica di posta elettronica ai membri della forza lavoro con dispositivi non conformi creando e assegnando un criterio di conformità.
- [Aggiungere e assegnare un'app](../apps/quickstart-add-assign-app.md): aggiungere e assegnare un'app client alla forza lavoro della società.
- [Creare e assegnare un criterio di protezione delle app](../apps/quickstart-create-assign-app-policy.md): creare e assegnare un criterio di protezione delle app a un'app client nel dispositivo dell'utente finale.
- [Creare e assegnare un ruolo personalizzato](create-custom-role.md) - Creare e assegnare un ruolo personalizzato con autorizzazioni specifiche per un reparto di operazioni di sicurezza. 
- [Creare un profilo di posta elettronica del dispositivo per iOS](../configuration/quickstart-email-profile.md) - Creare un profilo di posta elettronica del dispositivo per i dispositivi iOS.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, è necessario avere un account amministratore e un tenant per Intune attivato. Creare una sottoscrizione gratuita per [provare Intune gratuitamente](free-trial-sign-up.md) in un ambiente di test. I sottoscrittori correnti possono anche completare queste attività nel tenant live. Questi articoli introduttivi partono dal presupposto che vengano usati dispositivi di test.

Per poter completare tutte le attività dell'introduzione, è anche necessario essere amministratore globale dell'organizzazione.

## <a name="intune-architecture"></a>Architettura di Intune

Intune è il componente di Enterprise Mobility + Security (EMS) che gestisce dispositivi e app per dispositivi mobili. Intune è integrato con altri componenti EMS come Azure Active Directory (Azure AD) per il controllo delle identità e degli accessi e Azure Information Protection per la protezione dei dati. Quando viene usato con Office 365, consente alla forza lavoro di essere produttiva con tutti i dispositivi, garantendo al tempo stesso la protezione delle informazioni dell'organizzazione.

![Diagramma dell'architettura di alto livello per Microsoft Intune](./media/get-started-evaluation/intunearchitecture.svg)

## <a name="next-steps"></a>Passaggi successivi

[Introduzione all'utilizzo di Azure](tutorial-walkthrough-intune-portal.md): fornisce informazioni sull'anatomia del portale di Azure e spiega come apportare modifiche alla pagina visualizzata.

## <a name="learn-more"></a>Altre informazioni

- [Informazioni su Intune](what-is-intune.md)
- [Introduzione al portale di Azure](what-is-intune.md)
- [Cicli di vita del dispositivo e dell'app](device-lifecycle.md)