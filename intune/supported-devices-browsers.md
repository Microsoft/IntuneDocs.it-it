---
title: Dispositivi supportati in Microsoft Intune
description: Questo articolo elenca le piattaforme di dispositivi e i browser supportati per la gestione dei dispositivi in Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6c9cc3a6a84c48da36b0219743012a15b72e6810
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="supported-devices-and-browsers"></a>Dispositivi e browser supportati

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Questo articolo è rivolto agli amministratori di sistema responsabili della gestione dei dispositivi nell'organizzazione. Per informazioni sull'installazione di Intune sul telefono, vedere [Uso di dispositivi gestiti per lo svolgimento del lavoro](/intune-user-help/company-portal-frequently-asked-questions).

Prima di iniziare la configurazione di Microsoft Intune, esaminare i requisiti seguenti:

- [Dispositivi e computer supportati](#intune-supported-devices)
- [Elenco di Web browser supportati che usano Intune](#intune-supported-web-browsers)

È anche consigliabile acquisire familiarità con l'[uso della larghezza di banda di rete in Intune](network-bandwidth-use.md) ([portale classico](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Dispositivi supportati da Intune

È possibile gestire i dispositivi seguenti con Gestione dei dispositivi mobili di Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Dispositivi Samsung KNOX Standard supportati

L'app Portale aziendale tenta l'attivazione Samsung KNOX durante la registrazione MDM solo se il dispositivo da attivare è presente nell'[elenco dei dispositivi KNOX supportati](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Ciò consente di evitare errori di attivazione KNOX che impediscono la registrazione MDM. I dispositivi che non supportano l'attivazione Samsung KNOX vengono registrati come dispositivi Android standard. Tra i dispositivi Samsung, non tutti hanno un numero di modello che supporta KNOX. Verificare la compatibilità KNOX presso il rivenditore del dispositivo prima dell'acquisto e della distribuzione di dispositivi Samsung.

I modelli Samsung presenti nell'elenco seguente non supportano KNOX e vengono registrati come dispositivi Android nativi dall'app Portale aziendale per Android.

| **Nome dispositivo** | **Numeri modello dispositivo** |
| --- | --- |
| Galaxy A3 | SM-A300G<br>SM-A310Y<br>SM-A320FL |
| Galaxy A5 | SM-A500G |
| Galaxy Alpha | SM-G850M |
| Galaxy Avant | SM-G386T |
| Galaxy C9/C9 Pro | SM-C900F |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime | SM-G530M |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M<br>SM-J320W8 |
| Galaxy J5 | SM-J500G |
| Galaxy J7 | SM-J710F |
| Galaxy J7 Prime | SM-J727T1 |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 5 | SM-N920G<br>SM-N920I<br>SM-N920W8 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy NotePRO 12.2&quot; | SM-P902 |
| Galaxy On5 | SM-G570MSM-G570Y |
| Galaxy On7 | SM-G600FY<br>SM-G610M<br>SM-G610Y |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Active | GT-I9295 |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W<br>SM-G900M |
| Galaxy S5 Neo | SM-G903M |
| Galaxy S6 Edge | 404SCSM-G925I<br>SM-G928G |
| Galaxy Tab A 7.0&quot; | SM-T280SM-T285 |
| Galaxy Tab A 9.7&quot; | SM-P555M |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

Intune non può essere usato per gestire sistemi operativi Windows Server.

### <a name="windows-pc-software-client"></a>Client software PC Windows

Un [client software Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) può essere distribuito e installato nei PC di Windows come metodo alternativo di registrazione. Questa funzionalità è disponibile solo nel portale classico di Intune. È possibile usare il client software di Intune per gestire PC con Windows 7 e versioni successive, ad eccezione dell'edizione Windows 10 Home.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Web browser supportati da Intune

Per le svariate attività amministrative è necessario usare uno dei siti Web di amministrazione seguenti.

- [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portale di Azure](https://portal.azure.com/)

Per questi portali sono supportati i browser seguenti:
- Microsoft Edge (versione più recente)
- Microsoft Internet Explorer 11
- Safari (versione più recente, solo Mac)
- Chrome (versione più recente)
- Firefox (versione più recente)

### <a name="intune-classic-portal"></a>Portale classico di Intune

Le funzionalità esclusivamente classiche di Intune, come il client software per PC di Intune e l'integrazione con i partner Mobile Threat Defense sono disponibili solo nel portale classico di Intune (https://manage.microsoft.com). Per il portale classico di Intune è richiesto il supporto di un browser Silverlight.

La console di Intune è supportata dai browser Silverlight seguenti:
- Internet Explorer 10 o versione successiva
- Google Chrome (versioni precedenti alla versione 42)
- Mozilla Firefox con Silverlight abilitato [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Microsoft Edge e i browser per dispositivi mobili non sono supportati per il portale classico di Intune perché non supportano [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Solo gli utenti con autorizzazioni di amministratore del servizio o di amministratore tenant con il ruolo Amministratore globale possono accedere al portale. Per accedere alla console di amministrazione, è necessario che l'account abbia una licenza per l'uso di Intune e lo stato di accesso **Consentito**.
