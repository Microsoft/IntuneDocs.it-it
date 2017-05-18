---
title: Proteggere Dynamics CRM Online | Microsoft Docs
description: Proteggere e controllare l&quot;accesso a Dynamics CRM Online con l&quot;accesso condizionale.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 6740e6f5894f6dfd7788d90cc8f445e0a63821a9
ms.lasthandoff: 04/14/2017


---

# <a name="protect-access-to-dynamics-crm-online-with-intune"></a>Proteggere l'accesso a Dynamics CRM Online con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile controllare l'accesso a Microsoft Dynamics CRM Online dai dispositivi iOS e Android usando l'accesso condizionale di Microsoft Intune.  L'accesso condizionale di Intune è costituito da due componenti:
* [Criteri di conformità](introduction-to-device-compliance-policies-in-microsoft-intune.md) che il dispositivo deve soddisfare per essere considerato conforme.
* [Criteri di accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) in cui si specificano le condizioni che il dispositivo deve soddisfare per poter accedere al servizio.

Per altre informazioni sul funzionamento dell'accesso condizionale, leggere l'articolo [Proteggere l'accesso alla posta elettronica, a Office 365 e ad altri servizi](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!IMPORTANT]
> Per distribuire l'accesso condizionale è necessario disporre di sottoscrizioni di Intune e Azure Active Directory Premium. È inoltre necessario che gli utenti dispongano delle licenze di entrambi i prodotti. La **sottoscrizione di Enterprise Mobility + Security (EMS)** include sottoscrizioni di Intune e Azure Active Directory Premium. Per altre informazioni, vedere la [pagina dei prezzi di Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing). Se non si dispone della sottoscrizione di EMS, è possibile ottenere una sottoscrizione per Azure Active Directory Premium. Vedere la [pagina dei prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

Quando un utente di destinazione tenta di usare l'app Dynamics CRM sul proprio dispositivo, si verifica quanto segue:

![Immagine che illustra gli aspetti tenuti in considerazione per determinare se un dispositivo può accedere o meno a un servizio](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Il dispositivo che deve accedere a Dynamics CRM Online deve essere:
* Un dispositivo **Android** o **iOS**.
* **Registrato** con Intune.
* **Conforme** ai criteri di conformità di Intune distribuiti.

Lo stato del dispositivo viene archiviato in Azure Active Directory, che consente o blocca l'accesso in base alle condizioni specificate.

Se non viene soddisfatta una condizione, quando l'utente esegue l'accesso viene visualizzato uno dei messaggi seguenti:
* Se il dispositivo non è registrato con Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente le istruzioni su come installare l'app Portale aziendale ed eseguire la registrazione.
* Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di Microsoft Intune o all'app del portale aziendale in cui sono disponibili informazioni sul problema e su come risolverlo.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Configurare l'accesso condizionale per Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Passaggio 1: Configurare i gruppi di sicurezza di Active Directory

Prima di iniziare configurare i gruppi di sicurezza di Azure Active Directory per i criteri di accesso condizionale. È possibile configurare questi gruppi nel **centro di amministrazione di Office 365**. I gruppi vengono usati per definire gli utenti come destinazione dei criteri o per esentarli da questi ultimi. Per poter accedere alle risorse, un utente di destinazione in un criterio deve usare solo dispositivi conformi.

È possibile specificare due tipi di gruppo da usare per i criteri di Dynamics CRM:
* **Gruppi di destinazione**. Contiene i gruppi di utenti per i quali si applicano i criteri.
* **Gruppi di esenzione**. Contiene i gruppi di utenti esclusi dai criteri.

Se un utente si trova in entrambi i gruppi, sarà esentato dai criteri.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Passaggio 2: Configurare e distribuire i criteri di conformità
[Creare](create-a-device-compliance-policy-in-microsoft-intune.md) criteri di conformità e [distribuirli](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) a tutti i dispositivi interessati dai criteri stessi. In altri termini, tutti i dispositivi usati dagli utenti inclusi nei Gruppi di destinazione.

> [!NOTE]
> Mentre i criteri di conformità vengono distribuiti nei gruppi di Intune, i criteri di accesso condizionale sono destinati ai gruppi di sicurezza di Azure Active Directory.

> [!IMPORTANT]
> Se i criteri di conformità non sono stati distribuiti, i dispositivi verranno considerati conformi.

Quando si è pronti, continuare con il Passaggio 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Passaggio 3: Configurare i criteri di Dynamics CRM
A questo punto, configurare i criteri in modo che solo i dispositivi gestiti e conformi possano accedere a Dynamics CRM. Questi criteri verranno archiviati in Azure Active Directory.

1.  Nella console di amministrazione di Intune scegliere **Criteri > Accesso condizionale > Criteri di Dynamics CRM Online**.

  ![Schermata della pagina dei criteri di accesso condizionale per Dynamics CRM Online](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Scegliere il criterio **Abilita criteri di accesso condizionale**.
3.  In **Accesso all'applicazione** è possibile scegliere di applicare i criteri di accesso condizionale a:
  * **iOS**
  * **Android**
4.  In **Gruppi di destinazione** scegliere **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory ai quali verranno applicati i criteri. È possibile scegliere di applicare questa opzione a tutti gli utenti o solo a un gruppo di utenti selezionato.
5.    Facoltativamente, in **Gruppi esentati** scegliere **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory esentati da questi criteri.
6.    Al termine, scegliere **Salva**.

L'accesso condizionale per Dynamics CRM è stato configurato. Non è necessario distribuire i criteri di accesso condizionale perché diventano immediatamente effettivi.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorare i criteri di conformità e di accesso condizionale

Nell'area di lavoro **Gruppi** è possibile visualizzare lo stato dell'accesso condizionale per i dispositivi.

Scegliere un gruppo qualsiasi di dispositivi mobili e quindi nella scheda **Dispositivi** scegliere uno dei **filtri** seguenti:
* **Dispositivi non registrati con AAD**. Questi dispositivi non possono accedere a Dynamics CRM.
* **Dispositivi non conformi**. Questi dispositivi non possono accedere a Dynamics CRM.
* **Dispositivi conformi e registrati con AAD**. Questi dispositivi possono accedere a Dynamics CRM.

##  <a name="next-steps"></a>Passaggi successivi
* [Proteggere l'accesso a Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

* [Proteggere l'accesso a Exchange locale](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
* [Proteggere l'accesso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

* [Proteggere l'accesso a Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)

