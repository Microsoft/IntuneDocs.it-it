---
title: "Gestire i dispositivi di proprietà dell&quot;azienda | Documentazione Microsoft"
description: "Registrare i dispositivi di proprietà dell&quot;azienda in diversi modi, in base al tipo di dispositivo, alla modalità di acquisto e alle esigenze dell&quot;organizzazione."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: ae077d80e05b33d625285d796917f4f6c153ca3f


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>Registrare i dispositivi di proprietà dell'azienda con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile registrare i dispositivi di proprietà dell'organizzazione o dell'azienda in Intune in diversi modi a seconda del tipo di dispositivo, della modalità di acquisto e delle esigenze dell'organizzazione. È anche possibile installare l'app Portale aziendale per registrare e gestire i dispositivi di proprietà dell'azienda, come negli scenari BYOD (Bring Your Own Device).

Per impostazione predefinita, i dispositivi di tutte le piattaforme sono autorizzati alla registrazione in Intune. Per impedire la registrazione dei dispositivi, accedere al [portale di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore. Scegliere **Amministrazione** > **Gestione dei dispositivi mobili** > **Regole di registrazione** e deselezionare le caselle di controllo applicabili per le piattaforme da bloccare.

## <a name="enroll-corporate-owned-ios-devices"></a>Registrare i dispositivi iOS di proprietà dell'azienda

I metodi di registrazione dei dispositivi di proprietà dell'azienda sono un'ottima scelta per gli scenari CYOD (Choose Your Own Device). In un ambiente CYOD l'organizzazione paga il dispositivo scelto dall'utente e lo gestisce.

Se l'organizzazione offre agli utenti una scelta di dispositivi iOS, è possibile preconfigurare la registrazione in modo che il dispositivo venga gestito con Intune sin dalla prima accensione. Intune supporta la registrazione tramite il [programma di registrazione dispositivi di Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) o tramite lo strumento Apple Configurator in esecuzione in un computer Mac per la registrazione [diretta](ios-direct-enrollment-in-microsoft-intune.md) o con [Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Informazioni su come [registrare i dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Creare un account del manager di registrazione dispositivi

È possibile creare un account del manager di registrazione dispositivi in Intune per un singolo utente per gestire un numero elevato di dispositivi mobili per l'organizzazione. Dopo aver creato un account del manager di registrazione dispositivi, un account manager designato può registrare un numero maggiore dei quindici dispositivi registrabili da un utente standard.

È possibile usare un account del manager di registrazione dispositivi per registrare solo i dispositivi che non sono usati da un singolo utente specifico. Questi tipi di dispositivi sono ideali per app POS o di utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse aziendali.

Informazioni su come [registrare i dispositivi di proprietà dell'azienda con un account del manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>Registrare dispositivi Windows 10 Enterprise di proprietà dell'azienda

Se si usa Azure Active Directory Premium o Microsoft Enterprise Mobility Suite all'interno dell'organizzazione, è possibile [registrare i dispositivi Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Quando un utente aggiunge un account aziendale o dell'istituto di istruzione in un dispositivo, il dispositivo viene automaticamente contrassegnato come "di proprietà dell'azienda".

## <a name="import-imei-numbers"></a>Importare i numeri IMEI

Molti produttori di dispositivi mobili usano un numero univoco noto come IMEI (International Mobile Equipment Identity) nei loro dispositivi. È possibile importare i numeri IMEI per i dispositivi di proprietà dell'organizzazione. Quando il dispositivo passa alla gestione con Intune, viene contrassegnato come dispositivo di proprietà dell'azienda.

Informazioni su come [contrassegnare i dispositivi di proprietà dell'azienda usando i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporate-owned"></a>Identificare un dispositivo come di proprietà dell'azienda

Un dispositivo viene identificato come "aziendale" in Intune in presenza di una di queste condizioni:

 - Il dispositivo è stato [registrato con un account del manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (tutte le piattaforme).
 - Il dispositivo è stato registrato tramite il servizio [DEP di Apple](ios-device-enrollment-program-in-microsoft-intune.md) o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) (solo per iOS).
 - Il produttore del dispositivo ha [predichiarato il dispositivo usando i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (tutte le piattaforme con numeri IMEI).
 - Il dispositivo è registrato in [Azure Active Directory o Enterprise Mobility Suite come dispositivo Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) (solo per Windows 10).

Quando un dispositivo è contrassegnato come aziendale, verrà visualizzata l'indicazione **Aziendale** nella colonna **Proprietà** per il record del dispositivo nella console di amministrazione. 



<!--HONumber=Jan17_HO5-->


