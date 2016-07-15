---
title: Eseguire la migrazione a Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: 20394c243b9355cd3f4e30f170dfd00d10e1153f


---

# Eseguire la migrazione a Intune


La migrazione a Intune dalla soluzione di gestione della mobilità aziendale esistente può rappresentare l'ultimo passaggio della sequenza generale della procedura seguente:

![Passaggi della migrazione per Intune](./media/migrate-intune-steps.png)

## Notificare gli utenti

Una volta che la distribuzione pilota di Intune soddisfa i requisiti, comunicare agli utenti la migrazione imminente a Intune dei loro dispositivi. Messaggi di posta elettronica, istruzioni e [poster](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) consentono di creare aspettative e offrire dettagli di registrazione sui passaggi che gli utenti devono eseguire per mantenere una connettività ininterrotta alle risorse aziendali e alle applicazioni. Assicurarsi che il team di assistenza sia pronto ad aiutare gli utenti durante il processo di migrazione.

## Modificare la soluzione di gestione della mobilità aziendale esistente

A seconda di come si prevede di gestire i criteri di accesso condizionale tra la soluzione di gestione della mobilità aziendale esistente e Intune, potrebbe essere necessario disabilitare i criteri di accesso condizionale esistenti. Sarà necessario disabilitare i criteri di accesso condizionale esistenti OPPURE escludere dall'ambito dei criteri di accesso condizionale gli utenti o i dispositivi di cui si sta per eseguire la migrazione a Intune.  Evitare che sia Intune che la soluzione di gestione della mobilità aziendale esistente applichino criteri di accesso condizionale agli stessi utenti o dispositivi.

## Abilitare i criteri di accesso condizionale di Intune (facoltativo)

Se si è deciso di applicare immediatamente i criteri di accesso condizionale senza un periodo di tolleranza per la migrazione dei dispositivi, abilitare i criteri di accesso condizionale in Intune in questo passaggio.  Assicurarsi che questa decisione venga comunicata chiaramente agli utenti e al team di supporto tecnico.  Se i dispositivi non sono registrati in Intune e non sono conformi ai criteri di Intune, gli utenti non saranno in grado di accedere alle risorse aziendali finché non si saranno registrati in Intune e finché i dispositivi non saranno conformi ai criteri di Intune.

## Annullamento della registrazione dei dispositivi alla soluzione di gestione della mobilità aziendale esistente

Prima della registrazione in Intune, è necessario annullare la registrazione dei dispositivi alla soluzione di gestione di mobilità aziendale esistente. Per garantire l'esperienza utente più soddisfacente, è consigliabile consentire agli utenti di eseguire personalmente l'annullamento della registrazione.  Assicurarsi di seguire le indicazioni per l'annullamento della registrazione specificate dal provider della soluzione per garantire la rimozione corretta di utenti e dispositivi dalla piattaforma con un'interruzione delle attività più breve possibile per gli utenti finali.

## Registrazione dei dispositivi in Intune

Gli utenti per i quali è pianificata la migrazione devono registrarsi immediatamente in Intune per riottenere o evitare di perdere l'accesso alle risorse aziendali, alla posta elettronica e alle applicazioni. Se l'accesso condizionale è configurato e gli utenti tentano di connettersi alla posta elettronica prima di registrarsi in Intune, l'accesso verrà bloccato e gli utenti riceveranno un messaggio di posta elettronica di registrazione. Questo messaggio di posta elettronica contiene le istruzioni per la registrazione del dispositivo in Intune.  In alternativa, gli utenti possono registrarsi in Intune tramite l'app del portale aziendale di Intune o in modo nativo tramite il sistema operativo in Windows 8.1 e Windows 10 Mobile. Fare riferimento a [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md) per altre indicazioni sulla procedura di registrazione a seconda della piattaforma.

## Configurare l'accesso condizionale di Intune (facoltativo)

Se si è stabilito un periodo di tolleranza per l'applicazione dell'accesso condizionale, fare in modo che i criteri di accesso condizionale in Intune vengano applicati a partire dalla fine del periodo di tolleranza comunicato agli utenti finali. Questo richiederà che da quel momento tutti i dispositivi soddisfino immediatamente i requisiti dei criteri di accesso condizionale di Intune.

## Registrare i dispositivi e gli utenti rimanenti

Ora che l'accesso condizionale è abilitato, per ottenere l'accesso alle risorse aziendali tutti gli utenti devono registrarsi in Intune e soddisfare i criteri di conformità dell'organizzazione. Se la migrazione degli utenti è stata eseguita durante una registrazione in più fasi anziché contemporaneamente, ripetere i passaggi precedenti fino a quando tutti i dispositivi e tutti gli utenti non sono stati registrati e non sono passati alla gestione con Intune.

## Ritirare la soluzione di gestione della mobilità aziendale precedente

Dopo aver eseguito la migrazione di tutti gli utenti e di tutti i dispositivi a Intune e dopo averne verificato l'esito positivo, è possibile ritirare la soluzione di gestione della mobilità aziendale precedente e/o annullare la sottoscrizione del servizio. Assicurarsi di seguire le indicazioni del provider della soluzione per garantire la corretta rimozione di eventuali requisiti di infrastruttura non necessari e l'annullamento di tutte le sottoscrizioni e di tutte le licenze.

## Risorse aggiuntive sulla migrazione

Se è necessario maggiore supporto per la migrazione a Intune, sono disponibili diverse opzioni di assistenza da parte di esperti in grado di garantire una migrazione priva di problemi:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft Consulting Services](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Supporto tecnico e non tecnico di Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Forum su Microsoft Intune in TechNet](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## Scaricare una copia di questa guida

Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).



<!--HONumber=Jul16_HO2-->


