---
title: Aggiungere l'accesso Single Sign-On per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune, creare, configurare, consentire o abilitare i dispositivi iOS per l'uso dell'accesso Single Sign-On (SSO) invece della password per l'autenticazione con le risorse e i dati dell'organizzazione. Per usare l'accesso SSO, creare un profilo di configurazione del dispositivo e immettere il nome UPN, l'ID dispositivo, le app usate e un certificato per l'autenticazione dell'utente e del dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992010"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Usare l'accesso Single Sign-On con un dispositivo iOS in Microsoft Intune

La maggior parte delle app line-of-business (LOB) richiedono un certo livello di autenticazione utente per il supporto della sicurezza. In molti casi, l'autenticazione richiede di immettere le stesse credenziali più volte e ciò può essere frustrante per gli utenti. Per migliorare l'esperienza utente, gli sviluppatori possono creare app che usano l'accesso Single Sign-On (SSO), riducendo così il numero di volte in cui l'utente deve immettere le credenziali.

Questo articolo illustra come attivare l'accesso Single Sign-On per i dispositivi iOS tramite un profilo di configurazione del dispositivo in Microsoft Intune.

## <a name="before-you-begin"></a>Prima di iniziare

Assicurarsi di avere nel dispositivo iOS un'app che cerchi l'archivio delle credenziali utente nel payload Single Sign-On.

## <a name="create-the-sso-profile"></a>Creare il profilo SSO

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Scegliere **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `ios sso profile`.
    - **Descrizione**: immettere una descrizione con termini chiave che consentano di individuare il profilo nell'elenco.
    - **Piattaforma**: scegliere **iOS**.
    - **Tipo di profilo**: scegliere **Funzionalità del dispositivo**.

4. Scegliere **Single Sign-On**.

    ![Riquadro Single Sign-On](./media/sso-blade.png)

5. Immettere le impostazioni seguenti: 

    - **Attributo nome utente da AAD**: Intune cerca questo attributo per ogni utente in Azure AD e quindi popola il campo corrispondente (ad esempio UPN) prima di generare il payload XML da installare nel dispositivo. Le opzioni disponibili sono:
    
        - **Nome entità utente**: l'UPN viene analizzato nel modo seguente:

            ![Attributo nome utente](media/User-name-attribute.png)

            È anche possibile sovrascrivere l'area di autenticazione con il testo immesso nella casella di testo **Area di autenticazione**.

            Ad esempio, Contoso potrebbe avere varie aree secondarie, ad esempio Europa, Asia e America del Nord. Potrebbe richiedere l'uso del payload SSO agli utenti in Asia e l'app potrebbe richiedere il formato `username@asia.contoso.com` per l'UPN. In questo caso, se si seleziona **Nome entità utente**, per impostazione predefinita l'area di autenticazione per ogni utente viene recuperata da Azure AD e può corrispondere semplicemente a *contoso.com*. Specificatamente per gli utenti nell'area Asia è quindi possibile creare questo payload e sovrascrivere l'area di autenticazione con il valore *asia.contoso.com*. L'UPN dell'utente finale diventa ora username@asia.contoso.com anziché username@contoso.com.

        - **ID dispositivo Intune**: Intune seleziona automaticamente l'ID dispositivo di Intune. 

            Per impostazione predefinita, le app devono usare solo l'ID del dispositivo. Se l'app usa l'area di autenticazione *e* l'ID del dispositivo, tuttavia, è possibile digitare l'area di autenticazione nella casella di testo **Area di autenticazione**.

            > [!NOTE]
            > Per impostazione predefinita, mantenere vuoto il campo dell'area di autenticazione se si usa l'ID del dispositivo.

    - **Area di autenticazione**: parte del dominio dell'URL.
    
    - **Prefissi di URL che useranno l'accesso Single Sign-On**: **aggiungere** tutti gli URL dell'organizzazione che richiedono l'autenticazione Single Sign-On. 

        Quando un utente si connette a uno di questi siti, ad esempio, il dispositivo iOS usa le credenziali Single Sign-On. L'utente non deve immettere credenziali aggiuntive. Tuttavia, se è abilitata l'autenticazione a più fattori, gli utenti devono immettere la seconda autenticazione.

        > [!NOTE]
        > Questi URL devono essere nomi di dominio completi formattati in modo appropriato. Apple richiede che gli URL abbiano il formato `http://<yourURL.domain>`.

        I criteri di corrispondenza per gli URL devono iniziare con `http://` o `https://`. Viene eseguito un confronto di stringhe semplice e quindi il prefisso URL `http://www.contoso.com/` non corrisponde a `http://www.contoso.com:80/`. Con iOS 10.0 o versioni successive, tuttavia, è possibile immettere tutti i valori corrispondenti usando un solo carattere jolly \*. Ad esempio, `http://*.contoso.com/` corrisponde sia a `http://store.contoso.com/` che a `http://www.contoso.com`.

        I criteri `http://.com` e `https://.com` corrispondono rispettivamente a tutti gli URL HTTP e HTTPS.
    
    - **App che useranno l'accesso Single Sign-On**: **aggiungere** le app dei dispositivi degli utenti finali che potranno usare l'accesso Single Sign-On. 

        La matrice `AppIdentifierMatches` deve contenere stringhe corrispondenti agli ID dei bundle dell'app. Queste stringhe possono essere corrispondenze esatte (ad esempio: `com.contoso.myapp`). In alternativa, immettere una corrispondenza di prefisso per l'ID del bundle usando il carattere jolly \*. Il carattere jolly deve essere visualizzato dopo un punto (.) e può comparire una sola volta alla fine della stringa (ad esempio: `com.contoso.*`). Quando si include un carattere jolly, viene concesso all'account l'accesso a qualsiasi app il cui ID di bundle inizia con il prefisso.

        Usare **Nome app** per immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle.
    
    - **Certificato di rinnovo delle credenziali**: se per l'autenticazione si usano certificati (non password), selezionare il certificato SCEP o PFX distribuito all'utente come certificato di autenticazione. In genere, si tratta dello stesso certificato distribuito all'utente per altri profili, ad esempio VPN, Wi-Fi o posta elettronica.

6. Selezionare **OK** > **OK** > **Crea** per salvare le modifiche e creare il profilo. Dopo la creazione, il profilo viene visualizzato nell'elenco **Configurazione del dispositivo - Profili**. 

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla configurazione delle funzionalità dei dispositivi, vedere [Come configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune](device-features-configure.md).

[Assegnare il profilo](device-profile-assign.md) ai dispositivi iOS.
