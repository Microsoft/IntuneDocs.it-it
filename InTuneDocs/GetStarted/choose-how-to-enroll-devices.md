---
# required metadata

title: Scegliere come registrare i dispositivi mobili | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Scegliere come registrare i dispositivi mobili

La registrazione dei dispositivi mobili è il processo che consente la gestione di smartphone, tablet e PC da parte di Microsoft Intune. L'amministratore ha il compito di determinare qual è il modo migliore per registrare i dispositivi in base ai seguenti elementi:

 -  Proprietà (dispositivi personali e di proprietà della società)
 -  Utilizzo (condiviso o personale)
 -  Piattaforma (iOS, Android, Windows Phone, PC Windows, PC Mac)

Le risposte alle domande seguenti consentono di determinare il metodo di registrazione migliore per i dispositivi gestiti.

## **I dipendenti portano al lavoro i propri dispositivi o usano quelli dell'organizzazione?**

  **Dispositivi di proprietà dell'utente**, nota anche come registrazione BYOD (Bring your own device), consente agli utenti di registrare i propri dispositivi per accedere alle risorse aziendali come posta elettronica, app aziendali, dati aziendali e supporto. **Dispositivi di proprietà della società** (COD) vengono forniti dall'organizzazione ai propri dipendenti per soddisfare un'esigenza aziendale.
  > [!div class="button"]   [Registrazione BYOD >](#byod-device-enrollment)   [Registrazione COD >](cod-device-enrollment)

### Registrazione dispositivo BYOD

Con la registrazione BYOD è necessario che gli utenti installino l'app Portale aziendale nei propri dispositivi. Gli utenti possono quindi avviare l'app ed eseguire la registrazione specificando le credenziali aziendali o dell'istituto di istruzione. Se Intune trova una licenza per tali credenziali, il dispositivo viene aggiunto alla console di amministrazione di Intune e riceve i criteri di Intune, concedendo l'accesso alle risorse della società.

**Selezionare il tipo di dispositivo:**

> [!div class="op_single_selector"]
- [Configurare la gestione per Android con Microsoft Intune](..deploy-use/set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](..deploy-use/set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Impostare la gestione di Windows Phone con Microsoft Intune](..deploy-use/set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurare la gestione dei dispositivi Windows con Microsoft Intune](..deploy-use/set-up-windows-device-management-with-microsoft-intune.md)


### Registrazione dispositivo COD

I dispositivi di proprietà della società possono essere registrati per il supporto di un utente dedicato o condivisi.  **Dispositivi condivisi**: questi dispositivi non hanno un singolo utente e non sono in genere configurati per accedere alla posta elettronica. Gli esempi includono i dispositivi in modalità tutto schermo oppure orientati alle attività prelevati da un pool in base alle esigenze e quindi restituiti. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi. **Dispositivi dedicati**: i dispositivi rilasciati a singoli utenti devono essere registrati come risorse della società consentendo allo stesso tempo agli utenti di accedere alla posta elettronica e ai dati come se fossero dispositivi personalizzati. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi.

## **I dispositivi di proprietà della società sono condivisi o sono usati da utenti dedicati?**

> [!div class="button"] [Condivisi >](#Shared-company-owned-devices)   [Dedicati >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)


### Dispositivi condivisi di proprietà della società

Questi dispositivi non hanno un singolo utente e non sono in genere configurati per accedere alla posta elettronica. Gli esempi includono i dispositivi in modalità tutto schermo oppure orientati alle attività prelevati da un pool in base alle esigenze e quindi restituiti. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi.

  - **Dispositivi Windows e Android**: un *manager di registrazione dispositivi* è un account di Intune che può essere usato per registrare molti dispositivi condivisi con l'app del portale aziendale.
  > [!div class="button"]   [Windows >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#shared-ios-device-enrollment)

### Registrazione dei dispositivi iOS condivisi

Il metodo di registrazione preferito per i dispositivi iOS condivisi di proprietà della società dipende dalla modalità in cui i dispositivi sono stati acquistati e gestiti:

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con quel profilo
  - **Apple Configurator in un computer Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione. Se non si vuole riportare i dispositivi alle impostazioni di fabbrica, usare la registrazione diretta.
  - **Nessuna delle precedenti**: se non è possibile o non si vuole usare i metodi di registrazione DEP o Apple Configurator di Apple, usare il manager di registrazione dispositivi di Intune.

  **Scegliere:**
    > [!div class="button"]      [Registrazione DEP >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Mac >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Registrazione diretta >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)  

  > [!div class="button"]     [Registrazione DEM >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Singoli utenti**: i dispositivi di proprietà della società rilasciati a singoli utenti devono essere registrati come risorse aziendali consentendo allo stesso tempo agli utenti di accedere alla posta elettronica e ai dati come se fossero dispositivi personali. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi.

  - **Dispositivi Windows e Android**: importando i numeri di identità internazionale apparecchiature mobili (IMEI) dei dispositivi di proprietà della società è possibile contrassegnarli come dispositivi di proprietà della società in Intune. Gli utenti possono quindi registrare i propri dispositivi come dispositivo personali installando il portale aziendale per accedere a risorse aziendali come posta elettronica, applicazioni e dati.
  > [!div class="button"]   [Tag con IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **Dispositivi iOS**: i dispositivi iOS condivisi possono essere gestiti in tre modi.  **Come si registrano i dispositivi iOS condivisi?**

    - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione in base al profilo.
    > [!div class="button"]     [Registrazione DEP](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione.

    Se non si vuole riportare i dispositivi alle impostazioni di fabbrica, usare la registrazione diretta.
    Usare la registrazione di Assistente configurazione per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli.
    > [!div class="button"] [Registrazione con Assistente configurazione iOS >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"] [Registrazione diretta iOS >](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Nessuna delle precedenti**: se non è possibile o non si vuole usare i metodi di registrazione DEP o Apple Configurator di Apple, importando i numeri di identità internazionale apparecchiature mobili (IMEI) dei dispositivi di proprietà della società è possibile contrassegnarli come dispositivi di proprietà della società in Intune. Gli utenti possono quindi registrare i propri dispositivi come dispositivo personali installando il portale aziendale per accedere a risorse aziendali come posta elettronica, applicazioni e dati. > [!div class="button"][Contrassegnare i dispositivi con numeri IMEI](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO2-->


