---
title: "Gestire i dispositivi di proprietà dell&quot;azienda | Microsoft Intune"
description: "Registrare i dispositivi di proprietà dell&quot;azienda in diversi modi, in base al tipo di dispositivo, alla modalità di acquisto e alle esigenze dell&quot;organizzazione."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 7577cbab528d88635e8551bf8de1ffd49becaa84


---

# <a name="enroll-corporateowned-devices-by-using-intune"></a>Registrare i dispositivi di proprietà dell'azienda con Intune

È possibile registrare i dispositivi di proprietà dell'organizzazione o dell'azienda in Intune in diversi modi a seconda del tipo di dispositivo, della modalità di acquisto e delle esigenze dell'organizzazione. È anche possibile installare l'app Portale aziendale per registrare e gestire i dispositivi di proprietà dell'azienda, come negli scenari BYOD (Bring Your Own Device).

## <a name="enroll-corporateowned-ios-devices"></a>Registrare i dispositivi iOS di proprietà dell'azienda

I metodi di registrazione dei dispositivi di proprietà dell'azienda sono un'ottima scelta per gli scenari CYOD (Choose Your Own Device). In un ambiente CYOD l'organizzazione paga il dispositivo scelto dall'utente e lo gestisce.

Se l'organizzazione offre agli utenti una scelta di dispositivi iOS, è possibile preconfigurare la registrazione in modo che il dispositivo venga gestito con Intune sin dalla prima accensione. Intune supporta la registrazione tramite il [programma di registrazione dispositivi di Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) o tramite lo strumento Apple Configurator in esecuzione in un computer Mac per la registrazione [diretta](ios-direct-enrollment-in-microsoft-intune.md) o con [Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Informazioni su come [registrare i dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Creare un account del manager di registrazione dispositivi

È possibile creare un account del manager di registrazione dispositivi in Intune per un singolo utente per gestire un numero elevato di dispositivi mobili per l'organizzazione. Dopo aver creato un account del manager di registrazione dispositivi, un account manager designato può registrare un numero maggiore dei quindici dispositivi registrabili da un utente standard.

È possibile usare un account del manager di registrazione dispositivi per registrare solo i dispositivi che non sono usati da un singolo utente specifico. Questi tipi di dispositivi sono ideali per app POS o di utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse aziendali.

Informazioni su come [registrare i dispositivi di proprietà dell'azienda con un account del manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporateowned-windows-10-enterprise-devices"></a>Registrare dispositivi Windows 10 Enterprise di proprietà dell'azienda

Se si usa Azure Active Directory Premium o Microsoft Enterprise Mobility Suite all'interno dell'organizzazione, è possibile [registrare i dispositivi Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Quando un utente aggiunge un account aziendale o dell'istituto di istruzione in un dispositivo, il dispositivo viene automaticamente contrassegnato come "di proprietà dell'azienda".

## <a name="import-imei-numbers"></a>Importare i numeri IMEI

Molti produttori di dispositivi mobili usano un numero univoco noto come IMEI (International Mobile Equipment Identity) nei loro dispositivi. È possibile importare i numeri IMEI per i dispositivi di proprietà dell'organizzazione. Quando il dispositivo passa alla gestione con Intune, viene contrassegnato come dispositivo di proprietà dell'azienda.

Informazioni su come [contrassegnare i dispositivi di proprietà dell'azienda usando i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporateowned"></a>Identificare un dispositivo come di proprietà dell'azienda

In un elenco di dispositivi il valore per **Proprietà** è **Aziendale**. Un dispositivo di proprietà dell'azienda ha una di queste caratteristiche:

 - Il dispositivo è stato [registrato con un account del manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
 - Il dispositivo è stato registrato tramite il servizio [DEP di Apple](ios-device-enrollment-program-in-microsoft-intune.md) o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md).
 - Il produttore del dispositivo ha [predichiarato il dispositivo usando i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).
 - Il dispositivo è registrato in [Azure Active Directory o Enterprise Mobility Suite come dispositivo Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview).



<!--HONumber=Nov16_HO2-->


