---
title: Accesso condizionale basato su app a Office 365 | Microsoft Intune
description: "Informazioni su come l&quot;accesso condizionale per la gestione delle app per dispositivi mobili può essere usato per controllare le app che hanno accesso ai servizi di Office 365."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# Creare un criterio che consenta solo alle app per dispositivi mobili che supportano i criteri di gestione delle app per dispositivi mobili di Intune di accedere ai servizi di Office 365
I [criteri di gestione delle app per dispositivi mobili di Intune](protect-apps-and-data-with-microsoft-intune.md) consentono di proteggere i dati aziendali sui dispositivi registrati per la gestione in Intune. I criteri di gestione delle app per dispositivi mobili possono essere usati anche nei **dispositivi di proprietà dei dipendenti non registrati per la gestione in Intune**.  In questo caso, anche se il dispositivo non viene gestito, è comunque necessario assicurarsi che i dati e le risorse aziendali siano protetti. Usando l'accesso condizionale per la gestione delle app per dispositivi mobili è possibile creare un criterio che consenta solo alle app per dispositivi mobili che supportano i criteri di gestione delle app per dispositivi mobili di Intune di accedere a servizi di Office 365 come Exchange Online.

Ad esempio, consentendo solo all'**app di Microsoft Outlook** di accedere a Exchange Online è possibile **bloccare le app di posta elettronica predefinite in iOS e Android** che non hanno la protezione dei dati dei criteri di gestione delle app per dispositivi mobili di Intune per ricevere la posta elettronica da **Exchange Online**.

## Prerequisiti
**Prima** di configurare i criteri di accesso condizionale per la gestione delle app per dispositivi mobili è necessario avere un **abbonamento Enterprise Mobility + Security o un abbonamento Azure Active Directory Premium** e gli utenti devono avere la licenza per EMS o Azure AD. Per altre informazioni dettagliate, vedere la [pagina dei prezzi di Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) o la [pagina dei prezzi di Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## App supportate
**Exchange Online**
* Microsoft Outlook per Android e iOS

## Sovrapposizione con altri metodi di accesso condizionale e autenticazione
### Accesso condizionale per la gestione delle app per dispositivi mobili con autenticazione basata su certificato di Azure Active Directory

L'accesso condizionale per la gestione delle app per dispositivi mobili non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.
### Accesso condizionale per la gestione delle app per dispositivi mobili con accesso condizionale basato sulla conformità del dispositivo  

È possibile configurare l'[accesso condizionale basato sulla conformità del dispositivo](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**accesso condizionale per il dispositivo**) nella [console di amministrazione di Intune](https://manage.microsoft.com) o nella [console di gestione di Azure AD Premium] (https://manage.windowsazure.com). L'accesso condizionale per il dispositivo richiede che gli utenti si connettano a Exchange Online solo tramite dispositivi gestiti in Intune conformi ai criteri di conformità dei dispositivi di Intune o tramite PC aggiunti a un dominio.  Se un utente appartiene a uno o più gruppi di sicurezza che soddisfano i criteri di accesso condizionale per la gestione delle app per dispositivi mobili e per il dispositivo, l'utente deve soddisfare uno dei due requisiti:
* L'app usata per accedere al servizio è un'app per dispositivi mobili supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili e nel dispositivo su cui viene eseguita l'app è installato il **programma di autenticazione iOS (per i dispositivi iOS)** o l'**app Portale aziendale (per i dispositivi Android)**.
* Il dispositivo usato per accedere al servizio è **gestito da Intune e conforme** ai criteri di conformità del dispositivo di Intune oppure è un **PC aggiunto a un dominio**.  Di seguito sono riportati alcuni esempi per illustrare quanto descritto:
  * Se un utente tenta di connettersi da un'**app di posta elettronica iOS nativa**, verrà richiesto di usare un **dispositivo gestito e conforme** poiché l'app nativa non è supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili.
  * Se un utente tenta di connettersi da un **PC Windows Home**, verranno applicati i **criteri di accesso condizionale per il dispositivo** che richiedono che l'utente usi un PC aggiunto a un dominio.


## Cosa accade quando viene usata un'app con accesso condizionale per le gestione delle app per dispositivi mobili
L'accesso condizionale per le gestione delle app per dispositivi mobili verifica l'identità dell'applicazione approvata tramite un'app broker che deve essere presente nel dispositivo:
*  In **iOS** l'app broker è l'**app Azure Authenticator**.
* In **Android** l'app broker è l'**app Portale aziendale di Intune**. 

Agli utenti finali che accedono per la prima volta a un'app supportata dall'accesso condizionale per la gestione delle app per dispositivi mobili, come OneDrive o Outlook, viene chiesto di installare l'app broker e di registrare il dispositivo in Azure AD. La registrazione del dispositivo in Azure AD (in precedenza chiamata Aggiunta all'area di lavoro) crea un record del dispositivo e un certificato con cui vengono rilasciati i token.  Questa operazione **non** corrisponde alla **registrazione MDM**. Non vengono applicati profili o criteri di gestione e non è disponibile un inventario delle app del dispositivo.  Il processo di installazione dell'app broker e di registrazione del dispositivo verrà eseguito solo al primo utilizzo di un'app gestita.


## Passaggi successivi
[Create an Exchange Online Policy for MAM apps (Creare un criterio di Exchange Online per le app di gestione delle app per dispositivi mobili)](mam-ca-for-exchange-online.md)

[Block apps that do not have modern authentication (Bloccare le app che non usano l'autenticazione moderna)](block-apps-with-no-modern-authentication.md)

### Vedere anche

[Proteggere i dati delle app usando i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


