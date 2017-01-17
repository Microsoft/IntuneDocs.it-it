---
title: 'Limitare l&quot;accesso alla posta elettronica: scenari di esempio | Documentazione Microsoft'
description: "Alcuni scenari di esempio e informazioni su come è possibile implementarli con l&quot;accesso condizionale."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2d6ead1495a64e4e215c49b14064e390065a06de


---

# <a name="restrict-access-to-email-with-microsoft-intune-example-scenarios"></a>Limitare l'accesso alla posta elettronica con Microsoft Intune: scenari di esempio

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>Scenario 1: Impedire agli utenti di usare dispositivi non conformi per accedere a Exchange Online
### <a name="scenario-requirements"></a>Requisiti dello scenario
- L'accesso a Exchange Online per tutti gli utenti nel gruppo di sicurezza di Azure Active Directory **Contabilità** deve essere bloccato se il dispositivo non è conforme ai criteri di conformità distribuiti.
- Se nel gruppo esistono utenti i cui dispositivi non sono supportati da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], è necessario che l'accesso a Exchange Online da parte di questi dispositivi sia bloccato.
- Gli utenti nel gruppo di sicurezza di Azure Active Directory **Finanza** devono essere esclusi dai criteri, anche se sono inclusi nel gruppo di sicurezza **Contabilità**.

A tale scopo, configurare i criteri di accesso condizionale per Exchange Online con le impostazioni seguenti:

- Scegliere **Abilitare i criteri di accesso condizionale**.

- Scegliere le piattaforme a cui si vuole consentire l'accesso da app con l'autenticazione moderna.
- Per le app di Exchange ActiveSync, scegliere **Blocca i dispositivi non conformi sulle piattaforme supportate da Microsoft Intune** e **Blocca tutti gli altri dispositivi sulle piattaforme non supportate da Microsoft Intune**.
-   Nella sezione **Gruppi di destinazione** in **Gruppi di sicurezza selezionati** scegliere il gruppo di utenti **Contabilità**.

-   Nella sezione **Gruppo di esenzione** in **Gruppi di sicurezza selezionati** scegliere il gruppo di utenti **Finanza**.


Il flusso seguente viene usato nello scenario per decidere quali dispositivi possono accedere a Exchange Online:

![Flusso di accesso dei dispositivi](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>Scenario 2: Tutti i dispositivi iOS che accedono a Exchange locale devono essere gestiti da Intune
### <a name="scenario-requirements"></a>Requisiti dello scenario
- Solo ai dispositivi che eseguono iOS deve essere consentito l'accesso a Exchange locale.
- I dispositivi devono inoltre essere registrati in Intune e soddisfare le regole dei criteri di conformità prima di poter essere usati per accedere a Exchange.

A tale scopo, configurare i criteri di accesso condizionale seguenti per Exchange locale con queste impostazioni:

-   Scegliere l'opzione **Bloccare l'accesso delle app di posta elettronica a Exchange locale se il dispositivo non è conforme o non è registrato in Microsoft Intune**. Scegliendo questa opzione, si abilitano i criteri di accesso condizionale, che richiedono che tutti i dispositivi debbano essere registrati in Microsoft Intune e debbano soddisfare le regole dei criteri di conformità prima di accedere a Exchange.

-   Per le impostazioni di Exchange Active Sync, creare:

  -   Un'eccezione della piattaforma che consente l'accesso a Exchange ai dispositivi che eseguono iOS.   

  -   Una regola predefinita che specifica che quando un dispositivo non è coperto dalla regola di eccezione della piattaforma, non deve accedere a Exchange. Questa regola consente di accertarsi che ai dispositivi che non eseguono iOS sia impedito l'accesso a Exchange.

Usare il flusso seguente per decidere quali dispositivi possono accedere a Exchange:

![Flusso di accesso dei dispositivi](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>Scenario 3: I dispositivi Android non possono accedere a Exchange locale
### <a name="scenario-requirements"></a>Requisiti dello scenario
- A tutti i dispositivi Android deve essere impedito l'accesso a Exchange.
- Tutti gli altri dispositivi supportati possono accedere a Exchange perché sono gestiti da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

A tale scopo, configurare i criteri di accesso condizionale per Exchange locale con le impostazioni seguenti:

-   Scegliere l'opzione **Bloccare l'accesso delle app di posta elettronica a Exchange locale se il dispositivo non è conforme o non è registrato in Microsoft Intune**. Se si sceglie questa opzione, tutti i dispositivi devono essere registrati in Intune e devono soddisfare le regole dei criteri di conformità.

- Per le impostazioni di Exchange Active Sync, creare:
  -   Un'eccezione della piattaforma che blocca l'accesso a Exchange ai dispositivi che eseguono Android. Questa regola consente di accertarsi che per accedere a Exchange non vengano usati i dispositivi Android.

  -   Una regola predefinita che specifica che se un dispositivo non è coperto da altre regole, deve disporre dell'accesso a Exchange. Questa regola predefinita garantisce che i dispositivi che eseguono piattaforme diverse da Android, ma supportati da Microsoft Intune possano essere usati per accedere a Exchange. Devono tuttavia essere registrati in Intune e soddisfare le regole dei criteri di conformità.

Usare il flusso seguente per decidere quali dispositivi possono accedere a Exchange:

![Flusso di accesso dei dispositivi](./media/ConditionalAccess8-4.png)



<!--HONumber=Dec16_HO2-->


