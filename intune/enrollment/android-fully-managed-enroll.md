---
title: Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android Enterprise completamente gestiti in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8397dea1dca97122aac6716ee3d51295b913538
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885945"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Configurare la registrazione in Intune di dispositivi Android Enterprise completamente gestiti 

I dispositivi Android Enterprise completamente gestiti sono dispositivi di proprietà aziendale associati a un utente singolo e usati esclusivamente per lavoro e non per uso personale. Gli amministratori possono gestire interamente tali dispositivi e applicare controlli di criteri non disponibili nei profili di lavoro, ad esempio:
- Consentire l'installazione di app solo da Google Play gestito.
- Bloccare la disinstallazione di app gestite.
- Impedire agli utenti di ripristinare le impostazioni predefinite dei dispositivi e così via.

Intune facilita la distribuzione di app e impostazioni nei dispositivi Android Enterprise, inclusi i dispositivi Android Enterprise completamente gestiti. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

## <a name="technical-requirements"></a>Requisiti tecnici

Per gestire dispositivi Android Enterprise completamente gestiti, è necessario un tenant autonomo di Intune. La gestione di dispositivi completamente gestiti non è disponibile nella console di gestione legacy di Silverlight.

Per essere gestiti come dispositivi Android Enterprise completamente gestiti, i dispositivi devono soddisfare i requisiti seguenti:

- Sistema operativo Android versione 6.0 e successive.
- I dispositivi devono eseguire una build di Android dotata di connettività Google Mobile Services (GMS). I dispositivi devono includere GMS e devono essere in grado di connettersi a GMS.

Se i requisiti precedenti vengono soddisfatti, non esistono limitazioni relative al produttore o all'OEM del dispositivo.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurare la gestione di dispositivi Android Enterprise completamente gestiti

Per configurare la gestione di dispositivi Android Enterprise completamente gestiti, seguire questa procedura:

1. Per preparare la gestione dei dispositivi mobili, è necessario [impostare l'autorità per la gestione dei dispositivi mobili (MDM) su **Microsoft Intune**](../fundamentals/mdm-authority-set.md). Questa opzione viene impostata una sola volta, ovvero quando si configura per la prima volta Intune per la gestione dei dispositivi mobili.
2. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
3. [Abilitare i dispositivi utente di proprietà aziendale](#enable-corporate-owned-user-devices)
4. [Registrare i dispositivi completamente gestiti](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Abilitare i dispositivi utente di proprietà aziendale

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e scegliere **Dispositivi** > **Android** > **Registrazione Android**  > **Dispositivi utente completamente gestiti di proprietà aziendale**.
2. In **Consenti agli utenti di registrare dispositivi utente di proprietà aziendale** scegliere **Sì**.

> [!NOTE]
> Se sono stati definiti criteri di accesso condizionale di Azure AD che usano il controllo *Richiedi che i dispositivi siano contrassegnati come conformi* e si applicano a **Tutte le app cloud**, **Android** e **Browser**, è necessario escludere l'app cloud **Microsoft Intune** da questi criteri. Ciò è necessario poiché i processi di installazione di Android usano una scheda di Chrome per autenticare gli utenti durante la registrazione. Per altre informazioni, vedere [Documentazione di accesso condizionale di Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Se impostata su **Sì**, questa impostazione rende disponibile per il tenant di Intune un token di registrazione (una stringa casuale) e un codice a matrice. Questo token di registrazione singola è valido per tutti gli utenti e non scade. A seconda del sistema operativo Android e della versione del dispositivo, per registrare il dispositivo è possibile usare il token o il codice a matrice.

## <a name="enroll-the-fully-managed-devices"></a>Registrare i dispositivi completamente gestiti
È ora possibile [registrare i dispositivi completamente gestiti](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>Passaggi successivi
- [Aggiungere criteri di configurazione dei dispositivi Android Enterprise completamente gestiti](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Configurare criteri di configurazione delle app per dispositivi Android Enterprise completamente gestiti](../apps/app-configuration-policies-use-android.md)

