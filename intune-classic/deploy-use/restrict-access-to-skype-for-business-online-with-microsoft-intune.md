---
title: Proteggere Skype for Business Online | Microsoft Docs
description: Proteggere e controllare l&quot;accesso a Skype for Business Online con accesso condizionale.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 46dc5bc7d7b4107b87a41aa8a454453d591d0ef9
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="protect-access-to-skype-for-business-online-with-microsoft-intune"></a>Proteggere l'accesso a Skype for Business Online con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile usare i criteri di accesso condizionale per **Skype for Business Online** per controllare l'accesso a Skype for Business Online.
L'accesso condizionale è costituito da due componenti:
- Criteri di conformità che il dispositivo deve soddisfare per essere considerato conforme.
- Criteri di accesso condizionale in cui si specificano le condizioni che il dispositivo deve soddisfare per poter accedere al servizio.
Per altre informazioni sul funzionamento dell'accesso condizionale, leggere l'articolo [Proteggere l'accesso alla posta elettronica e ai servizi O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Quando un utente di destinazione tenta di usare Skype for Business Online sul proprio dispositivo, si verifica quanto segue:

![Immagine che illustra gli aspetti considerati per determinare se a un dispositivo è consentito o meno l'accesso a Skype for Business Online](../media/ConditionalAccess_SkypeforBusiness.png)

**Prima** di configurare i criteri di accesso condizionale per Skype for Business Online è necessario:
- Avere una **sottoscrizione di Skype for Business Online** e assegnare la licenza di Skype for Business agli utenti.
- Avere una **sottoscrizione di Enterprise Mobility + Security (EMS)** o una **sottoscrizione di Azure Active Directory Premium (Azure AD)** e gli utenti devono essere licenziatari di EMS o Azure AD. Per altre informazioni dettagliate, vedere i [prezzi di Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o i [prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-   [Abilitare l'autenticazione moderna](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) per Skype for Business Online.
-  Tutti gli utenti devono usare **Skype for Business Online**. Se si ha una distribuzione con Skype for Business Online e Skype for Business locale, i criteri di accesso condizionale non verranno applicati agli utenti.

Il dispositivo che necessita dell'accesso a Skype for Business Online deve:

-   Essere un dispositivo **Android** o **iOS**.

-   Essere **registrato** in Intune.

-   Essere **conforme** ai criteri di conformità di Intune distribuiti.


Lo stato del dispositivo viene archiviato in Azure Active Directory, che consente o blocca l'accesso in base alle condizioni specificate.

Se non viene soddisfatta una condizione, quando l'utente esegue l'accesso viene visualizzato uno dei messaggi seguenti:

-   Se il dispositivo non è registrato con Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente le istruzioni su come installare l'app Portale aziendale ed eseguire la registrazione.

-   Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale o all'app Portale aziendale di Intune dove sono disponibili informazioni sul problema e su come risolverlo.

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Configurare i criteri di accesso condizionale per Skype for Business Online

### <a name="step-1-configure-azure-active-directory-security-groups"></a>Passaggio 1: Configurare i gruppi di sicurezza di Azure Active Directory
Prima di iniziare configurare i gruppi di sicurezza di Azure Active Directory per i criteri di accesso condizionale. È possibile configurare questi gruppi nel **centro di amministrazione di Office 365**. Questi gruppi verranno usati per destinare o escludere gli utenti dai criteri. Per poter accedere alle risorse, un utente di destinazione nel criterio deve usare solo dispositivi conformi.

È possibile specificare due tipi di gruppo da usare per i criteri di Skype for Business:

-   **Gruppi di destinazione**: contiene i gruppi di utenti per i quali si applicano i criteri.

-   **Gruppi di esenzione**: contiene i gruppi di utenti esclusi dai criteri.

Se un utente si trova in entrambi i gruppi, sarà esentato dai criteri.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Passaggio 2: Configurare e distribuire i criteri di conformità
[Creare](create-a-device-compliance-policy-in-microsoft-intune.md) e [distribuire](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) i criteri di conformità a tutti i dispositivi interessati dai criteri, ossia tutti i dispositivi usati dagli utenti nei **Gruppi di destinazione**.

> [!NOTE]
> Mentre i criteri di conformità vengono distribuiti nei gruppi di Intune, i criteri di accesso condizionale sono destinati ai gruppi di sicurezza di Azure Active Directory.


> [!IMPORTANT]
> Se i criteri di conformità non sono stati distribuiti, i dispositivi verranno considerati conformi.

Quando si è pronti, continuare con il **Passaggio 3**.

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Passaggio 3: Configurare i criteri di Skype for Business Online
A questo punto, configurare i criteri in modo che solo i dispositivi gestiti e conformi possano accedere a Skype for Business Online. Questi criteri verranno archiviati in Azure Active Directory.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** > **Accesso condizionale** > **Criteri di Skype for Business Online**.

  ![Schermata della pagine dei criteri di accesso condizionale per Skype for Business Online](./media/conditional_access_SFBPolicy.png)

2.  Scegliere **Abilitare i criteri di accesso condizionale**.

3.  In **Accesso all'applicazione** è possibile scegliere di applicare i criteri di accesso condizionale a:

    -   **iOS**

    -   **Android**

4.  In **Gruppi di destinazione** scegliere **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory ai quali verranno applicati i criteri. È possibile scegliere di applicare questa opzione a tutti gli utenti o solo a un gruppo di utenti selezionato.

5.  Facoltativamente, in **Gruppi esentati** scegliere **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory esentati da questi criteri.

6.  Al termine dell'operazione scegliere **Salva**.

L'accesso condizionale per Skype for Business Online è stato configurato. Non è necessario distribuire i criteri di accesso condizionale perché diventano immediatamente effettivi.


## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorare i criteri di conformità e di accesso condizionale
Nell'area di lavoro **Gruppi** è possibile visualizzare lo stato dell'accesso condizionale per i dispositivi.

Scegliere un gruppo qualsiasi di dispositivi mobili e quindi nella scheda **Dispositivi** scegliere uno dei **filtri** seguenti:

* **Dispositivi non registrati con AAD**: si tratta dei dispositivi che non possono accedere a Skype for Business Online.

* **Dispositivi non conformi**: si tratta dei dispositivi che non possono accedere a Skype for Business Online.

* **Dispositivi conformi e registrati con AAD**: si tratta dei dispositivi che possono accedere a Skype for Business Online.

