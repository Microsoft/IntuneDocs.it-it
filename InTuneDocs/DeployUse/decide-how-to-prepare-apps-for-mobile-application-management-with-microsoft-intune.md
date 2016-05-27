---
# required metadata

title: Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune
È possibile consentire alle app di usare i criteri di gestione delle applicazioni mobili tramite lo strumento di wrapping delle app di Intune o Intune App SDK. In questo articolo vengono fornite informazioni su questi due metodi e su quando usarli.

## Strumento di wrapping delle app di Intune
Lo strumento di wrapping delle app viene usato principalmente per le app line-of-business (LOB) interne. Lo strumento è un'applicazione della riga di comando che crea un wrapper per l'app, consentendo quindi all'app di essere gestita dai criteri di gestione delle applicazioni mobili di Intune. Non è necessario il codice sorgente per usare lo strumento, ma sono necessarie le credenziali di firma.  Per altre informazioni sulle credenziali di firma, vedere il [blog di Intune](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx). Per la documentazione dello strumento per la disposizione testo per app, vedere gli articolo relativi allo [strumento per la disposizione testo per app Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e allo [strumento per la disposizione testo per app iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)..

Lo strumento di wrapping delle app non supporta le app nell'App o Play Store né le funzionalità che richiedono un'integrazione del tempo di sviluppo (vedere la tabella di confronto delle funzionalità seguente).

È consigliabile usare lo strumento di wrapping delle app, anziché l'SDK, se l'app è già stato scritta o se il codice sorgente non è disponibile.

## Intune App SDK
App SDK è progettato principalmente per i clienti che hanno le app nell'App o Play Store e che vogliono poter gestire le app con Intune. Tuttavia, qualsiasi app può sfruttare l'integrazione dell'SDK, anche se si tratta di un'app LOB.

Per integrare l'SDK, è necessario accedere al codice sorgente dell'app. Per istruzioni sull'integrazione dell'SDK, vedere [Microsoft Intune App SDK](https://msdn.microsoft.com/library/mt627769.aspx)..

## Confronto delle funzionalità
Questa tabella elenca le impostazioni che è possibile usare per App SDK e per lo strumento di wrapping delle app.

> [!NOTE]
> Lo strumento per la disposizione testo per app può essere usato con la versione autonoma di Intune o Intune con Configuration Manager.

|Funzionalità|App SDK|Strumento di wrapping delle app|
|-----------|---------------------|-----------|
|Limitare il contenuto Web per la visualizzazione in Managed Browser dell'azienda|X|X|
|Impedire backup in Android, iTunes o iCloud|X|X|
|Consenti all'app di trasferire i dati ad altre app|X|X|
|Consenti all'app di ricevere i dati da altre app|X|X|
|Limita le operazioni taglia, copia e incolla con le altre app|X|X|
|Richiedi PIN semplice per l'accesso|X|X|
|Sostituire il PIN dell'app predefinita con il PIN di Intune|X||
|Specificare il numero di tentativi prima della reimpostazione del PIN|X|X|
|Richiedere l'impronta digitale anziché il PIN (solo iOS)<br></br>**Nota:** disponibile solo in ambienti MAM.|X||
|Richiedi credenziali aziendali per l'accesso|X|X|
|Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted|X|X|
|Crittografa dati app|X|X|
|Ricontrollare i requisiti di accesso dopo un numero di minuti specificato|X|X|
|Specificare il periodo di prova offline|X|X|
|Bloccare l'acquisizione schermo (solo Android)|X|X|
|Cancellazione completa|X|X|
|Cancellazione selettiva <br></br>**Nota:** per iOS, quando viene rimosso il profilo di gestione, viene rimossa anche l'app.|X||
|Impedire "Salva con nome" |X||
|Supportare più identità|X||

### Vedere anche
[Strumento per la disposizione testo per app Adroid](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Strumento per la disposizione testo per app iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Usare l'SDK per abilitare le app per la gestione delle applicazioni per dispositivi mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->


