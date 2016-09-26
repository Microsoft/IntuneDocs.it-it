---
title: Limitare l'accesso con la protezione dalle minacce per dispositivi mobili | Microsoft Intune
description: Limitare l'accesso alle risorse aziendali in base al rischio per dispositivi, rete e applicazioni.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 61480eb11cc8f4b6b336e48a50c2fe1b5fcd3fac
ms.openlocfilehash: c05dfc8154cd13b74f42b4f63262613be8956d87


---

# Limitare l'accesso alle risorse aziendali in base al rischio per dispositivi, rete e applicazioni
È possibile controllare l'accesso dai dispositivi mobili alle risorse aziendali, in base alla valutazione dei rischi condotta da Lookout, una soluzione di protezione dalle minacce per dispositivi mobili (MTP, Mobile Threat Protection) integrata in Microsoft Intune. Il rischio si basa su dati di telemetria raccolti dal servizio Lookout MTP dai dispositivi per le vulnerabilità del sistema operativo, le app dannose installate e i profili di rete. In base alla valutazione dei rischi è quindi possibile configurare criteri di accesso condizionale in Intune e consentire o bloccare i dispositivi determinati come non conformi in seguito al rilevamento di minacce in tali dispositivi.  Questa soluzione è attualmente supportata solo per i dispositivi **Android** che eseguono la versione **4.1 e successive** e sono registrati in Microsoft Intune.  
## Quale problema risolve questa soluzione?
Le aziende e le organizzazioni hanno l'esigenza di proteggere i dati sensibili da minacce emergenti che includono minacce fisiche, minacce basate su app e sulla rete, oltre a vulnerabilità del sistema operativo.

Tradizionalmente, le aziende e le organizzazioni hanno adottato una posizione attiva per la protezione dei PC da attacchi dannosi. L'area dei dispositivi mobili è relativamente nuova e spesso senza protezione. Sebbene le piattaforme mobili includano la protezione predefinita del sistema operativo grazie a tecniche come l'isolamento delle app e store online controllati per le app dei consumatori, queste piattaforme continuano a essere vulnerabili ad attacchi sofisticati. Dato che i dispositivi mobili sono sempre più spesso usati dai dipendenti per il lavoro e devono avere accesso a informazioni che possono essere sensibili e preziose, questi dispositivi devono essere protetti da un'ampia gamma di attacchi sofisticati.

Intune offre la possibilità di controllare l'accesso alle risorse e ai dati aziendali in base alla valutazione dei rischi offerta da soluzioni MTP come Lookout.

## In che modo la protezione dalle minacce per dispositivi mobili di Intune e Lookout può tutelare le risorse aziendali?
L'app Lookout per dispositivi mobili (Lookout for Work), eseguita nei dispositivi mobili, consente di acquisire dati di telemetria per il file system, lo stack di rete, il dispositivo e le applicazioni (se disponibili) e di inviarli al servizio cloud Lookout MTP per il calcolo del livello di rischio aggregato del dispositivo per le minacce per dispositivi mobili. È anche possibile modificare la classificazione del livello di rischio per le minacce nella console di MTP in base alle proprie esigenze.  
I criteri di conformità in Intune includono ora una nuova regola per la protezione dalle minacce per dispositivi mobili di Lookout, basata sulla valutazione dei rischi di Lookout MTP. Quando questa regola è abilitata, Microsoft Intune valuta la conformità del dispositivo in base ai criteri abilitati.

Se il dispositivo risulta non conforme ai criteri, è possibile bloccare l'accesso a risorse come Exchange Online e SharePoint Online tramite criteri di accesso condizionale. In seguito al blocco dell'accesso, gli utenti ricevono istruzioni per la risoluzione del problema e per ottenere l'accesso alle risorse aziendali. Questa procedura dettagliata viene avviata tramite l'app Lookout for Work.

## Scenari di esempio
Questi sono alcuni degli scenari comuni:
### Minacce da app dannose:
Quando nel dispositivo vengono rilevate app dannose come malware, è possibile bloccare il dispositivo per impedire:
* La connessione alla posta elettronica aziendale prima di risolvere la condizione di minaccia.
* La sincronizzazione di file aziendali tramite l'app OneDrive per il lavoro.
* L'accesso ad applicazioni cruciali per l'azienda.

**Accesso bloccato quando vengono rilevate app dannose:**
![diagramma che mostra i criteri di accesso condizionale che bloccano l'accesso quando il dispositivo viene determinato come non conforme a causa della presenza di app dannose](../media/mtp/malicious-apps-blocked.png)

**Il dispositivo viene sbloccato e può accedere alle risorse aziendali quando la condizione di minaccia è risolta:**

![diagramma che mostra i criteri di accesso condizionale che concedono l'accesso quando il dispositivo risulta conforme dopo la correzione](../media/mtp/malicious-apps-unblocked.png)
### Minacce per la rete:
Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle e limitare l'accesso a reti Wi-Fi in base al livello di rischio del dispositivo.

**Accesso alla rete tramite Wi-Fi bloccato:**
![diagramma che mostra l'accesso condizionale che blocca l'accesso tramite Wi-Fi in presenza di minacce di rete](../media/mtp/network-wifi-blocked.png)

**Accesso concesso dopo la risoluzione:**

![diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia](../media/mtp/network-wifi-unblocked.png)
### Minacce per la rete (che impediscono l'accesso a SharePoint Online):

Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Accesso bloccato a SharePoint Online in base alle minacce di rete rilevate nel dispositivo:**

![Diagramma che mostra l'accesso condizionale che blocca l'accesso del dispositivo a SharePoint Online in base al rilevamento di minacce](../media/mtp/network-spo-blocked.png)


**Accesso concesso dopo la risoluzione:**

![Diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia per la rete](../media/mtp/network-spo-unblocked.png)

## Passaggi successivi
Ecco i passaggi principali per l'implementazione di questa soluzione:
1.  [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md)
2.  [Abilitare la connessione a Lookout MTP nella console di amministrazione Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Configurare e distribuire l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)
4.  [Configurare i criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Risolvere i problemi di integrazione di Lookout](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration.md)



<!--HONumber=Sep16_HO2-->


