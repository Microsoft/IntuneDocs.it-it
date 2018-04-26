---
title: Integrazione del controllo di accesso alla rete con Microsoft Intune - Azure | Microsoft Docs
description: Le soluzioni di controllo di accesso alla rete (NAC, Network Access Control) consentono di verificare che i dispositivi siano registrati in Intune e che siano conformi. NAC include alcuni comportamenti e funziona con l'accesso condizionale. Vedere i passaggi per l'onboarding e ottenere un elenco di soluzioni partner.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf796afcfc42f2cdf778713f4dceadb2597a12e2
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integrazione del controllo di accesso alla rete (NAC) con Intune

Intune si integra con i partner di controllo di accesso alla rete per consentire alle organizzazioni di proteggere i dati aziendali quando i dispositivi provano ad accedere alle risorse locali.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Protezione delle risorse aziendali con le soluzioni di Intune e NAC

Le soluzioni NAC controllano lo stato di registrazione e conformità del dispositivo con Intune e consentono di prendere decisioni relative al controllo dell'accesso. Se il dispositivo non è registrato oppure è registrato ma non è conforme ai criteri di conformità dei dispositivi Intune, deve essere reindirizzato a Intune per la registrazione e/o per un controllo di conformità.

### <a name="example"></a>Esempio

Se il dispositivo è registrato e conforme con Intune, la soluzione NAC dovrebbe consentire al dispositivo di accedere alle risorse aziendali. Ad esempio, agli utenti può essere consentito o negato l'accesso quando provano a usare una connessione WiFi aziendale o risorse VPN.

## <a name="feature-behaviors"></a>Comportamenti delle funzionalità

I dispositivi che stanno eseguendo la sincronizzazione con Intune non possono passare dallo stato **Conforme** / **Non conforme** allo stato **Not Synched** (Non sincronizzato) o **Sconosciuto**. Lo stato **Sconosciuto** è riservato ai dispositivi appena registrati dei quali non è ancora stata valutata la conformità.

Per i dispositivi a cui viene impedito l'accesso alle risorse, il servizio che blocca l'accesso deve reindirizzare tutti gli utenti al [portale di gestione](https://portal.manage.microsoft.com) per determinare i motivi per cui il dispositivo è bloccato.  Se gli utenti visitano questa pagina, viene rivalutata la conformità dei loro dispositivi in modo sincrono.

## <a name="nac-and-conditional-access"></a>NAC e accesso condizionale

NAC interagisce con l'accesso condizionale per le decisioni relative al controllo di accesso. Per altre informazioni, vedere [Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Funzionamento dell'integrazione NAC

L'elenco seguente è una panoramica del funzionamento dell'integrazione di NAC con Intune. I primi tre passaggi, da 1 a 3, illustrano il processo di onboarding. Dopo aver integrato la soluzione NAC con Intune, seguire i passaggi da 4 a 9 che descrivono l'intera operazione.

![Funzionamento di NAC con Intune](./media/ca-intune-common-ways-2.png)

1. Registrare la soluzione partner NAC con Azure Active Directory (AAD) e concedere le autorizzazioni delegate all'API NAC di Intune.
2. Configurare la soluzione partner NAC con le impostazioni appropriate, incluso l'URL di individuazione di Intune.
3. Configurare la soluzione partner NAC per l'autenticazione del certificato.
4. L'utente si connette al punto di accesso WiFi aziendale o esegue una richiesta di connessione VPN.
5. La soluzione partner NAC inoltra le informazioni sul dispositivo a Intune e chiede a Intune lo stato di conformità e la registrazione del dispositivo.
6. Se il dispositivo non è conforme o non è registrato, la soluzione partner NAC indica all'utente di registrare o risolvere la conformità del dispositivo.
7. Il dispositivo prova di nuovo a verificare la conformità e/o lo stato di registrazione.
8. Dopo che il dispositivo è registrato e conforme, la soluzione partner NAC Ottiene lo stato da Intune.
9. La connessione viene stabilita correttamente e consente al dispositivo di accedere alle risorse aziendali.

## <a name="next-steps"></a>Passaggi successivi

- [Integrate Cisco ISE with Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html) (Integrare ISE Cisco con Intune)
- [Integrate Citrix NetScaler with Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) (Integrare Citrix NetScaler con Intune)
- [Integrate HP Aruba Clear Pass with Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757) (Integrare HP Aruba Clear Pass con Intune)
- [Integrare Squadra security Removable Media Manager (secRMM) con Intune](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)