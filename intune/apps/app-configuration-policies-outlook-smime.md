---
title: Configurare S/MIME con Outlook per iOS in Microsoft Intune
description: Informazioni su S/MIME con Outlook per iOS in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9572f4accb1be232d4667d99b98beff90d81379
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000415"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Configurare S/MIME con Outlook per iOS

Secure/Multipurpose Internet Mail Extensions (S/MIME) offre un livello aggiuntivo di sicurezza per i messaggi di posta elettronica inviati da e verso un account di Exchange ActiveSync (EAS). [Microsoft Outlook](https://aka.ms/omsmime) può usare il protocollo S/MIME per consentire agli utenti di crittografare sia i messaggi in uscita sia gli allegati, assicurando così che solo il destinatario previsto possa leggere e accedere al contenuto del messaggio quando si usano account di Office 365. Gli utenti possono anche firmare digitalmente un messaggio in modo che i destinatari possano verificare l'identità del mittente e confermare che il messaggio non è stato manomesso. Questa funzionalità è possibile tramite l'uso di certificati. Per altre informazioni, vedere [Informazioni su S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> Questa funzionalità è stata posticipata, ma verrà presto rilasciata.

> [!NOTE]
> In questo argomento viene descritto come distribuire certificati radice trusted tramite [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Microsoft Endpoint Manager è una singola piattaforma integrata per la gestione di tutti gli endpoint. L'interfaccia di amministrazione di Microsoft Endpoint Manager si integra con System Center Configuration Manager e Microsoft Intune.

## <a name="about-message-encryption"></a>Crittografia dei messaggi
Gli utenti possono inviare messaggi crittografati a persone sia all'interno sia all'esterno dell'organizzazione se dispongono della parte pubblica dei certificati di crittografia. Le chiavi private associate ai certificati di crittografia devono essere sempre protette dal destinatario del messaggio crittografato. La chiave privata del certificato di crittografia viene usata dal destinatario per decrittografare il messaggio.

I messaggi crittografati possono essere letti solo dai destinatari che dispongono del certificato corrispondente a quello usato per crittografare il messaggio. Se si tenta di inviare un messaggio crittografato a destinatari che non hanno il certificato di crittografia, l'app richiederà di rimuovere questi destinatari prima di inviare il messaggio di posta elettronica.

## <a name="about-digital-signatures"></a>Firme digitali
Un messaggio con firma digitale assicura al destinatario che il messaggio non è stato manomesso e che l'identità del mittente è autentica. I destinatari possono verificare la firma digitale solo se usano un client di posta elettronica che supporta S/MIME.

## <a name="prerequisites"></a>Prerequisiti
- Outlook per iOS supporta S/MIME solo in account di Office 365.
- È necessario configurare S/MIME per Office 365. Per altre informazioni, vedere [How to configure S/MIME in Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516) (Come configurare S/MIME in Office 365).
- È necessario disporre di un'autorità di certificazione che possa emettere certificati utilizzabili per la firma e la crittografia.
- Distribuire i certificati radice trusted tramite Endpoint Manager. Per altre informazioni, vedere [Creare profili di certificati attendibili](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- I certificati di crittografia devono essere importati in Endpoint Manager. Per altre informazioni, vedere [Configurare e usare i certificati PKCS importati con Intune](~/protect/certificates-imported-pfx-configure.md).
- Installare e configurare il connettore dei certificati PFX per Microsoft Intune. Per altre informazioni, vedere [Scaricare, installare e configurare il connettore di certificati PFX per Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- I dispositivi devono essere registrati in MDM perché ricevano automaticamente certificati radice trusted e S/MIME da Endpoint Manager.

> [!IMPORTANT]
> Per poter usare certificati di crittografia S/MIME con Outlook per iOS, è necessario scaricare e installare il connettore dei certificati PFX aggiornato (versione 6.1911.11.0 o successiva) per Microsoft Intune.

## <a name="smime-support-in-outlook-for-ios"></a>Supporto S/MIME in Outlook per iOS
Outlook per iOS supporta la firma e la crittografia S/MIME dei messaggi usando i certificati. Molti clienti dispongono di certificati di firma e crittografia distinti anziché avere un solo certificato che supporta sia la firma sia la crittografia. I certificati di firma sono in genere univoci nei dispositivi registrati di un singolo utente, mentre i certificati di crittografia sono condivisi tra i dispositivi registrati di un singolo utente. Può succedere spesso che gli utenti usino S/MIME per anni e abbiano certificati di crittografia diversi man mano che si rinnovano. Le cronologie dei certificati di crittografia, incluse le relative chiavi private, devono essere presenti nel dispositivo dell'utente, in modo che sia possibile leggere il messaggio di posta elettronica che in passato potrebbe essere stato crittografato con uno di questi certificati. È anche possibile avere un solo certificato che supporta sia la firma sia la crittografia.

Outlook per iOS supporta due modi per fornire i certificati ai dispositivi in modo che possano essere usati per S/MIME:

- **Gli utenti** possono inviare i certificati S/MIME a se stessi e installarli dagli allegati in Outlook per iOS nei dispositivi mobili.
- Gli **amministratori** possono importare le cronologie dei certificati di crittografia da qualsiasi autorità di certificazione in Endpoint Manager. Endpoint Manager distribuirà quindi automaticamente tali certificati a tutti i dispositivi registrati dall'utente. Per i certificati di firma viene solitamente usato Simple Certificate Enrollment Protocol (SCEP). Con SCEP, la chiave privata viene generata e archiviata nel dispositivo registrato e viene fornito un certificato univoco a ogni dispositivo registrato da un utente, che può essere usato per il non ripudio. Gli amministratori importano le cronologie dei certificati di crittografia per gli utenti in Endpoint Manager, che quindi fornisce tutti i certificati di crittografia dell'utente ai dispositivi che l'utente registra. Infine, Endpoint Manager supporta le credenziali derivate per i clienti che richiedono supporto per lo standard NIST 800-157. In iOS viene usato il Portale aziendale per recuperare i certificati di firma e di crittografia da Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Configurazione di S/MIME per Outlook per iOS in Endpoint Manager
Per configurare S/MIME per Outlook per iOS in Endpoint Manager, inclusa la distribuzione automatica dei certificati S/MIME che Outlook per iOS può usare, seguire questa procedura:

### <a name="add-the-microsoft-outlook-app"></a>Aggiungere l'app Microsoft Outlook
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Aggiungere l'app Microsoft Outlook per iOS dall'App Store in Endpoint Manager oppure sincronizzare Outlook per iOS dal Volume Purchase Program di Apple. Per altre informazioni, vedere [Aggiungere app dello Store iOS a Microsoft Intune](~/apps/store-apps-ios.md) oppure [Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Creare i criteri di configurazione S/MIME di Outlook per iOS

I passaggi seguenti consentono di creare e configurare i criteri S/MIME di Outlook per iOS in Endpoint Manager. Con queste impostazioni i certificati di firma e crittografia vengono forniti automaticamente.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionare **App** > **Criteri di configurazione dell'app** > **Aggiungi**.<br>
Verrà visualizzato il riquadro **Aggiungi i criteri di configurazione**.
2. Immettere il **Nome** e la **Descrizione** del criterio di configurazione.
3. Selezionare **Dispositivi gestiti** per **Tipo di registrazione del dispositivo**.
4. Per **Piattaforma** selezionare **iOS/iPadOS**.
5. Fare clic su **Selezionare l'app necessaria** per trovare e associare l'app Microsoft Outlook per iOS aggiunta in precedenza. 
6. Fare clic su **Impostazioni di configurazione** per aggiungere le impostazioni di configurazione. 
    - Selezionare **Usa progettazione configurazione** accanto a **Formato delle impostazioni di configurazione** e accettare le impostazioni predefinite. Per altre informazioni, vedere [Impostazioni di configurazione di Microsoft Outlook](~/apps/app-configuration-policies-outlook.md).
7. Fare clic su **S/MIME** per visualizzare le **Impostazioni di S/MIME per Outlook**.
8. Impostare **Abilita S/MIME** su **Sì**.
9. Impostare **Distribuisci certificati S/MIME da Intune** su **Sì**.
10. In **Certificati di firma** scegliere una delle opzioni seguenti accanto a **Tipo di profilo di certificato**:
    - **SCEP**: crea un certificato univoco per il dispositivo e per l'utente che può essere usato da Microsoft Outlook per la firma. Per informazioni correlate, vedere [Configurare l'infrastruttura per il supporto di SCEP con Intune](~/protect/certificates-scep-configure.md) e [Creare un profilo certificato SCEP](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **Certificati PKCS importati**: usa un certificato univoco per l'utente, che può essere tuttavia condiviso tra dispositivi ed è stato importato in Endpoint Manager dall'amministratore per conto dell'utente. Il certificato viene fornito a tutti i dispositivi registrati da un utente. Endpoint Manager sceglierà automaticamente il certificato importato che supporta la firma e lo fornirà al dispositivo corrispondente all'utente registrato.
    - **Credenziali derivate**: usa un certificato già disponibile nel dispositivo che può essere usato per la firma. Il certificato deve essere recuperato nel dispositivo usando i flussi delle credenziali derivate in Intune.
11. In **Certificati di crittografia** scegliere una delle opzioni seguenti accanto a **Tipo di profilo di certificato**:
    - **Certificati PKCS importati**: fornisce tutti i certificati di crittografia che sono stati importati in Endpoint Manager dall'amministratore in qualsiasi dispositivo registrato dall'utente e Endpoint Manager sceglierà automaticamente il certificato o i certificati importati che supportano la crittografia per fornire i certificati al dispositivo corrispondente all'utente registrato.
    - **Credenziali derivate**: usa un certificato già disponibile nel dispositivo che può essere usato per la firma. Il certificato deve essere recuperato nel dispositivo usando i flussi delle credenziali derivate in Intune.
12. Accanto a **Notifiche per l'utente finale** scegliere di inviare una notifica agli utenti finali selezionando **Portale aziendale** o **Posta elettronica** per recuperare i certificati S/MIME per Outlook per iOS.

    In iOS gli utenti devono usare l'app Portale aziendale per recuperare i certificati S/MIME. Tramite la sezione Notifiche in Portale aziendale, una notifica push e/o un messaggio di posta elettronica, Endpoint Manager informerà l'utente della necessità di avviare il Portale aziendale per recuperare i certificati S/MIME. Selezionando una delle notifiche, l'utente visualizzerà una pagina di destinazione contenente informazioni sullo stato del recupero dei certificati. Dopo aver recuperato i certificati, l'utente può usare S/MIME in Microsoft Outlook per iOS per firmare e crittografare i messaggi di posta elettronica.
    
    Le notifiche all'utente finale includono le opzioni seguenti:
       - **Portale aziendale**: se questa opzione è selezionata, gli utenti riceveranno una notifica push nel dispositivo, che aprirà la pagina di destinazione in Portale aziendale in cui verranno recuperati i certificati S/MIME.
        - **Posta elettronica**: invia un messaggio di posta elettronica all'utente finale per informarlo che è necessario avviare il Portale aziendale per recuperare i certificati S/MIME. Se l'utente sta usando il dispositivo iOS registrato quando fa clic sul collegamento nel messaggio di posta elettronica, sarà reindirizzato al Portale aziendale per recuperare i certificati.
    
13. Selezionare **Assegnazioni** per assegnare i criteri di configurazione dell'app ai gruppi di Azure AD. Per altre informazioni, vedere [Assegnare app ai gruppi con Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni, vedere [Criteri di configurazione delle app per Microsoft Intune](app-configuration-policies-overview.md).
