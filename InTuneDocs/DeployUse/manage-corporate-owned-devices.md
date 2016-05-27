---
# required metadata

title: Gestire i dispositivi di proprietà dell'azienda con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi di proprietà dell'azienda con Microsoft Intune
I dispositivi di proprietà dell'organizzazione o dell'azienda possono essere introdotti nella gestione in diversi modi, a seconda del dispositivo e di come è stato acquistato.

## Dispositivi iOS di proprietà dell'azienda
Questi metodi di registrazione sono adatti per gli scenari CYOD (Choose Your Own Device) in cui l'organizzazione acquista i dispositivi per gli utenti ma vuole mantenere la gestione dei dispositivi. Se l'organizzazione ha acquistato dispositivi iOS, è possibile preconfigurare la registrazione in modo che la gestione dei dispositivi sia possibile fin dalla prima volta che questi ultimi vengono accesi dai rispettivi utenti. Intune supporta la registrazione tramite il [programma di registrazione dispositivi di Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) o tramite lo strumento Apple Configurator in esecuzione in un computer Mac per la registrazione [diretta](ios-direct-enrollment-in-microsoft-intune.md) o con [Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Registrare i dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Manager di registrazione dispositivi
Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un unico account utente, detto manager di registrazione dispositivi. Dopo la creazione, un account manager di registrazione dispositivi può essere usato da un gestore per registrare più dei cinque dispositivi standard consentiti per impostazione predefinita agli utenti normali. La registrazione di dispositivi con un manager di registrazione dispositivi funziona solo per i dispositivi non usati da un utente specifico. Questi dispositivi sono ideali per app POS o utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse della società.

[Registrare i dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Specificare i dispositivi aziendali tramite IMEI (International Mobile Equipment Identity)
I numeri IMEI (International Mobile Equipment Identity) univoci costituiscono una proprietà di dispositivo diffusa per molti produttori di dispositivi mobili. Gli amministratori Intune possono importare numeri IMEI per i dispositivi di proprietà della società. Quando il dispositivo passa alla gestione con Intune, può essere contrassegnato come dispositivo di proprietà dell'azienda ed essere soggetto a criteri appropriati.

[Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)


<!--HONumber=May16_HO1-->


