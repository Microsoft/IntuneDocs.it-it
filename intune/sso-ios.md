---
title: Configurare Microsoft Intune per l'accesso Single Sign-On al dispositivo iOS
titlesuffix: ''
description: Informazioni su come configurare Microsoft Intune per l'accesso Single Sign-On al dispositivo iOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b9afd14fd3ba4e464f0bf09c228290ef2f19eac3
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>Configurare Microsoft Intune per l'accesso Single Sign-On al dispositivo iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La maggior parte delle app line-of-business (LOB) richiedono un certo livello di autenticazione utente per il supporto della sicurezza. In molti casi viene richiesto all'utente di digitare le stesse credenziali più volte e ciò può essere frustrante per gli utenti. Per migliorare l'esperienza utente, gli sviluppatori possono creare app che usano Single Sign-On, riducendo così il numero di volte in cui un utente deve fornire le credenziali.

Per sfruttare i vantaggi della funzionalità Single Sign-On per i dispositivi iOS, è necessario che siano soddisfatte le condizioni seguenti:

- Un'app sviluppata in modo da cercare l'archivio delle credenziali utente nel payload Single Sign-On nel dispositivo iOS.
- Intune configurato per l'accesso Single Sign-On al dispositivo iOS.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Per configurare Intune per l'accesso Single Sign-On al dispositivo iOS


1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
5. Nel riquadro dei profili scegliere **Crea profilo**.
6. Specificare un nome e una descrizione e configurare le impostazioni seguenti:
   - **Piattaforma**: scegliere **iOS**.
   - **Tipo di profilo**: scegliere **Funzionalità del dispositivo**.
7. Nel riquadro **Funzionalità del dispositivo** scegliere **Single Sign On**.

   ![Riquadro Single Sign-On](./media/sso-blade.png)

8. Fare riferimento alla tabella di riepilogo seguente per la compilazione dei campi nel riquadro **Single Sign-On**. Per informazioni dettagliate, vedere le sezioni dopo la tabella.

   |Campo  |Note|
   |---------|---------|
   |**Attributo nome utente da AAD**|Attributo esaminato da Intune per ogni utente in AAD e usato per popolare il campo corrispondente (ad esempio UPN) prima di generare il payload XML che viene installato nel dispositivo.|
   |**Area di autenticazione**|Parte del dominio dell'URL.|
   |**Prefissi di URL che useranno l'accesso Single Sign-On**|Tutti gli URL all'interno dell'organizzazione che richiedono l'autenticazione Single Sign-On per gli utenti|
   |**App che useranno l'accesso Single Sign-On**|App nel dispositivo dell'utente finale che usano il payload Single Sign-On.|
   |**Certificato di rinnovo delle credenziali**|Se si usano i certificati per l'autenticazione, selezionare il certificato SCEP o PFX che viene distribuito all'utente come certificato di autenticazione.|

Le sezioni seguenti contengono informazioni dettagliate su ognuno dei campi relativi a Single Sign-On.

### <a name="username-attribute-from-aad-and-realm"></a>Attributo nome utente da AAD e Area di autenticazione

- Se si seleziona **Nome dell'entità utente** per questo campo, l'analisi viene eseguita nel modo seguente:

   ![Attributo nome utente](media/User-name-attribute.png)

   È anche possibile scegliere di sovrascrivere l'area di autenticazione con il testo digitato nella casella di testo **Area di autenticazione**.

   Ad esempio, Contoso potrebbe avere varie aree secondarie, ad esempio Europa, Asia e America del Nord. Potrebbe richiedere l'uso del payload SSO agli utenti in Asia e l'UPN dell'app in formato *username@asia.contoso.com*. In questo caso, se si seleziona **Nome dell'entità utente**, per impostazione predefinita l'area di autenticazione per ogni utente viene recuperata da AAD è potrebbe essere semplicemente *contoso.com*. Specificatamente per gli utenti nell'area Asia è quindi possibile creare questo payload e sovrascrivere l'area di autenticazione con il valore *asia.contoso.com*. L'UPN dell'utente finale diventa ora *username@asia.contoso.com* e non *username@contoso.com*.

- Se si seleziona **ID dispositivo**, Intune seleziona automaticamente l'ID dispositivo di Intune.

   Per impostazione predefinita, le app devono usare solo l'ID del dispositivo. Se l'app usa l'area di autenticazione oltre all'ID del dispositivo, tuttavia, è possibile digitare l'area di autenticazione nella casella di testo **Area di autenticazione**.

   > [!NOTE]
   > Per impostazione predefinita, mantenere vuoto il campo dell'area di autenticazione se si usa l'ID del dispositivo.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>Prefissi di URL che useranno l'accesso Single Sign-On

Digitare gli eventuali URL esistenti all'interno dell'organizzazione che richiedono l'autenticazione utente.

Ad esempio, quando un utente si connette a uno di questi siti, il dispositivo iOS usa le credenziali Single Sign-On e l'utente non deve immettere credenziali aggiuntive. Tuttavia, se è abilitata l'autenticazione a più fattori, gli utenti devono immettere la seconda autenticazione.

> [!NOTE]
> Questi URL devono essere nomi di dominio completi formattati in modo appropriato. Apple richiede che siano nel formato `http://<yourURL.domain>`

I criteri di corrispondenza per gli URL devono iniziare con `http://` o `https://`. Viene eseguita una semplice corrispondenza di stringhe, quindi il prefisso URL `http://www.contoso.com/` non corrisponde a `http://www.contoso.com:80/`. Con iOS 9.0 o versioni successive, tuttavia, è possibile usare un singolo carattere jolly \* per specificare tutti i valori corrispondenti. Ad esempio, `http://*.contoso.com/` corrisponde sia a `http://store.contoso.com/` che a `http://www.contoso.com`.
I criteri `http://.com` e `https://.com` corrispondono rispettivamente a tutti gli URL HTTP e HTTPS.

### <a name="apps-that-will-use-single-sign-on"></a>App che useranno l'accesso Single Sign-On

Indicare le app nel dispositivo dell'utente finale che possono usare il payload Single Sign-On.

La matrice `AppIdentifierMatches` deve contenere stringhe corrispondenti agli ID dei bundle dell'app. Queste stringhe potrebbero essere corrispondenze esatte (ad esempio: `com.contoso.myapp`) o specificare una corrispondenza di prefisso per l'ID del bundle usando il carattere jolly \*. Il carattere jolly deve essere visualizzato dopo un punto (.) e può comparire una sola volta alla fine della stringa (ad esempio: `com.contoso.*`). Quando si include un carattere jolly, viene concesso all'account l'accesso a qualsiasi app il cui ID di bundle inizia con il prefisso.

Il campo **Nome app** viene usato per aggiungere un nome descrittivo per facilitare l'identificazione dell'ID del bundle.

### <a name="credential-renewal-certificate"></a>Certificato di rinnovo delle credenziali

Se si autenticano gli utenti finali con i certificati (non password), usare questo campo per selezionare il certificato SCEP o PFX distribuito all'utente come certificato di autenticazione. In genere, si tratta dello stesso certificato distribuito all'utente per altri profili, ad esempio VPN, Wi-Fi o posta elettronica.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla configurazione delle funzionalità dei dispositivi, vedere [Come configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune](device-features-configure.md).
