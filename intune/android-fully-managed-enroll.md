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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dff37794d6c58094749821748dcc96a4f36e28a
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071616"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti (anteprima)

I dispositivi Android Enterprise completamente gestiti sono dispositivi di proprietà aziendale associati a un utente singolo e usati esclusivamente per lavoro e non per uso personale. Gli amministratori possono gestire interamente tali dispositivi e applicare controlli di criteri non disponibili nei profili di lavoro, ad esempio:
- Consentire l'installazione di app solo da Google Play gestito.
- Bloccare la disinstallazione di app gestite.
- Impedire agli utenti di ripristinare le impostazioni predefinite dei dispositivi e così via.

Intune facilita la distribuzione di app e impostazioni nei dispositivi Android Enterprise, inclusi i dispositivi Android Enterprise completamente gestiti. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

## <a name="technical-requirements"></a>Requisiti tecnici

Per gestire dispositivi Android Enterprise completamente gestiti, è necessario un tenant autonomo di Intune. La gestione di dispositivi completamente gestiti non è disponibile in modalità ibrida (con connessione a Configuration Manager) o nella console di gestione legacy di Silverlight.

Per essere gestiti come dispositivi Android Enterprise completamente gestiti, i dispositivi devono soddisfare i requisiti seguenti:

- Sistema operativo Android versione 5.1 e successive.
- I dispositivi devono eseguire una build di Android dotata di connettività Google Mobile Services (GMS). I dispositivi devono includere GMS e devono essere in grado di connettersi a GMS.

Se i requisiti precedenti vengono soddisfatti, non esistono limitazioni relative al produttore o all'OEM del dispositivo.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurare la gestione di dispositivi Android Enterprise completamente gestiti

Per configurare la gestione di dispositivi Android Enterprise completamente gestiti, seguire questa procedura:

1. Per preparare la gestione dei dispositivi mobili, è necessario [impostare l'autorità per la gestione dei dispositivi mobili (MDM) su **Microsoft Intune**](mdm-authority-set.md). Questa opzione viene impostata una sola volta, ovvero quando si configura per la prima volta Intune per la gestione dei dispositivi mobili.
2. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
3. [Abilitare i dispositivi utente di proprietà aziendale](#enable-corporate-owned-user-devices)
4. [Registrare i dispositivi completamente gestiti](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Abilitare i dispositivi utente di proprietà aziendale

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Dispositivi utente completamente gestiti di proprietà aziendale (anteprima)** .
2. In **Consenti agli utenti di registrare dispositivi utente di proprietà aziendale** scegliere **Sì**.

> [!NOTE]
> Se sono stati definiti criteri di accesso condizionale di Azure AD che usano il controllo *Richiedi che i dispositivi siano contrassegnati come conformi* e si applicano a **Tutte le app cloud**, **Android** e **Browser**, è necessario escludere l'app cloud **Microsoft Intune** da questi criteri. Ciò è necessario poiché i processi di installazione di Android usano una scheda di Chrome per autenticare gli utenti durante la registrazione. Per altre informazioni, vedere [Documentazione di accesso condizionale di Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Se impostata su **Sì**, questa impostazione rende disponibile per il tenant di Intune un token di registrazione (una stringa casuale) e un codice a matrice. Questo token di registrazione singola è valido per tutti gli utenti e non scade. A seconda del sistema operativo Android e della versione del dispositivo, per registrare il dispositivo in modalità tutto schermo è possibile usare il token o il codice a matrice.

## <a name="enroll-the-fully-managed-devices"></a>Registrare i dispositivi completamente gestiti
È ora possibile [registrare i dispositivi completamente gestiti](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Considerazioni su questa funzionalità di anteprima
Questa anteprima pubblica include un set di funzionalità di base per il set di soluzioni Android Enterprise completamente gestite. È possibile inviare commenti sull'esperienza d'uso delle funzionalità di anteprima tramite uno qualsiasi dei canali di comunicazione correnti con il team, ad esempio [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853).

Per i dispositivi Android Enterprise completamente gestiti, questa anteprima supporta le funzionalità seguenti:
- Registrazione del dispositivo tramite NFC, token, codice a matrice e Zero Touch
- Configurazione del dispositivo per gruppi utenti
- Distribuzione e configurazione di app per gruppi utenti


Quando si usano queste funzionalità di anteprima, tenere presente quanto segue:
- Le funzionalità di anteprima non sono consigliate per distribuzioni cruciali o di produzione. 
- Le funzionalità di anteprima vengono implementate per gli standard di produzione di Microsoft Intune. Non tutte le funzionalità di Intune, tuttavia, sono disponibili per l'uso con dispositivi utente Android Enterprise completamente gestiti. Le funzionalità di anteprima sono chiaramente contrassegnate da "(anteprima)" nella console di Intune. 
- Le funzionalità di anteprima sono completamente supportate tramite i canali di supporto di Intune abituali.
- La registrazione di dispositivi Android Enterprise completamente gestiti tramite la registrazione per dispositivi mobili Samsung Knox non è supportata nella versione di anteprima. 
- L'uso dell'app Portale aziendale Intune non è supportato nei dispositivi Android Enterprise completamente gestiti. 
- Alcune funzionalità di Intune, ad esempio l'accesso condizionale, i criteri di protezione delle app e la distribuzione dei certificati non sono supportati in anteprima. 
- L'uso di gruppi di dispositivi come destinazione di un profilo o di un'app non è supportato in anteprima. L'uso come destinazione è supportato solo per gruppi utenti. 
- Non è presente un'interfaccia utente di prima classe per la configurazione di posta elettronica, Wi-Fi o VPN. Per configurare le impostazioni di configurazione delle app supportate, usare i criteri di configurazione delle app.

## <a name="next-steps"></a>Passaggi successivi
- [Aggiungere criteri di configurazione dei dispositivi Android Enterprise completamente gestiti](device-restrictions-android-for-work.md#device-owner-only)
- [Configurare criteri di configurazione delle app per dispositivi Android Enterprise completamente gestiti](app-configuration-policies-use-android.md)

