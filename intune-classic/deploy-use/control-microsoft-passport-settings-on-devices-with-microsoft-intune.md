---
title: Controllare le impostazioni di Windows Hello for Business nei dispositivi
description: Informazioni sull'integrazione tra Intune e Windows Hello for Business, un metodo di accesso alternativo che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7c4ac0b79e30283b90612c77acf1462a25bb6093
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="control-windows-hello-for-business-settings-on-devices-with-microsoft-intune"></a>Controllare le impostazioni di Windows Hello for Business nei dispositivi con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune si integra con Windows Hello for Business (precedentemente noto come Microsoft Passport for Work), un metodo di accesso alternativo che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.

Hello for Business consente di eseguire l'accesso usando un *movimento dell'utente* invece di una password. Un movimento dell'utente può essere un PIN semplice, l'autenticazione biometrica come Windows Hello o un dispositivo esterno come un lettore di impronte digitali.

Intune si integra con Hello for Business in due modi:

-   È possibile usare i criteri di Intune per controllare i movimenti che gli utenti possono usare o meno per l'accesso.

-   È possibile archiviare i certificati di autenticazione nel provider di archiviazione chiavi (KSP) di Windows Hello for Business. Per altre informazioni, vedere [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune).

> [!IMPORTANT]
> Nelle versioni di Windows 10 Desktop e Mobile precedenti all'aggiornamento dell'anniversario era possibile impostare due diversi PIN da usare per l'autenticazione alle risorse:
- Il **PIN dispositivo** che poteva essere usato per sbloccare il dispositivo e connetterlo alle risorse cloud.
- Il **PIN per lavoro** che veniva usato per accedere alle risorse di Azure AD nei dispositivi personali dell'utente (BYOD).

>Nell'aggiornamento dell'anniversario questi due PIN sono stati uniti in un unico PIN dispositivo.
Eventuali criteri di configurazione di Intune impostati per controllare il PIN del dispositivo ed eventuali criteri di Windows Hello for Business configurati, ora impostano questo nuovo valore di PIN.
Se entrambi i tipi di criteri sono stati impostati per controllare il PIN, i criteri di Windows Hello for Business verranno applicati ai dispositivi Windows 10 Desktop e Mobile.
Per assicurarsi che i conflitti dei criteri vengano risolti e che i criteri dei PIN vengano applicati correttamente, aggiornare i criteri di Windows Hello for Business in modo che corrispondano alle impostazioni nei criteri di configurazione e chiedere agli utenti di sincronizzare i propri dispositivi nell'app Portale aziendale.



## <a name="create-a-windows-hello-for-business-policy"></a>Creare un criterio di Windows Hello for Business

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows** &gt; **Windows Hello for Business** per aprire la pagina Windows Hello for Business.

    ![Pagina Windows Hello for Business](../media/passport.png)

2.  Scegliere una delle impostazioni seguenti:
    - **Disabilita Windows Hello for Business nei dispositivi registrati**. Selezionare questa impostazione se non si vuole usare Windows Hello for Business. Tutte le altre impostazioni nella schermata risultano non disponibili.
    - **Abilita Windows Hello for Business nei dispositivi registrati**. Selezionare questa impostazione se si vuole configurare le impostazioni di Windows Hello for Business.
    - **Non configurato**. Selezionare questa impostazione se non si vuole usare Intune per controllare le impostazioni di Windows Hello for Business. Eventuali impostazioni di Windows Hello for Business presenti nei dispositivi Windows 10 non verranno modificate. Tutte le altre impostazioni nella schermata risultano non disponibili.
3.  Se si seleziona **Abilita Windows Hello for Business nei dispositivi registrati**, configurare le impostazioni obbligatorie che verranno applicate a tutti i dispositivi Windows 10 e Windows 10 Mobile registrati.
4.  Al termine, scegliere **Salva**.


## <a name="settings-for-the-windows-hello-for-business-policy"></a>Impostazioni per il criterio di Windows Hello for Business

- **Usa un modulo TPM (Trusted Platform Module)**. Un chip TPM (Trusted Platform Module) fornisce un livello aggiuntivo di sicurezza dei dati.<br>Scegliere uno dei valori seguenti:
    - **Obbligatorio** (impostazione predefinita). Solo i dispositivi con un modulo TPM accessibile possono eseguire il provisioning di Windows Hello for Business.
    - **Preferito**. I dispositivi provano a usare prima un modulo TPM. Se non è disponibile, possono usare la crittografia software.
- **Richiedi lunghezza minima del PIN**/**Richiedi lunghezza massima del PIN**. Configura i dispositivi in modo che usino i valori massimo e minimo specificati per la lunghezza del PIN per garantire l'accesso protetto. La lunghezza del PIN predefinita è 6 caratteri, ma è possibile applicare una lunghezza minima di 4 caratteri. La lunghezza massima del PIN è 127 caratteri.
- **Richiedi lettere minuscole nel PIN**/**Richiedi lettere maiuscole nel PIN**/**Caratteri speciali nel PIN**. Per applicare un PIN più complesso, richiedere l'utilizzo di lettere maiuscole, lettere minuscole e caratteri speciali nel PIN. È possibile scegliere tra:
    - **Consentito**. Gli utenti possono usare il tipo di carattere specificato nel proprio PIN, ma non è obbligatorio.
    - **Obbligatorio**. Gli utenti devono includere almeno uno dei tipi di carattere specificati nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.
    - **Non consentito** (impostazione predefinita). Gli utenti non devono usare questi tipi di carattere nel PIN. Se l'opzione non è configurata, questa è l'impostazione predefinita.<br>I caratteri speciali includono: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **Scadenza PIN (giorni)**. Si consiglia di specificare un periodo di scadenza dopo il quale gli utenti finali devono modificare il PIN. L'impostazione predefinita è 41 giorni.
- **Ricorda cronologia PIN**. Limita il riutilizzo di PIN usati in precedenza. Per impostazione predefinita, non è possibile riutilizzare gli ultimi 5 PIN.
- **Consenti autenticazione biometrica**. Abilita l'autenticazione biometrica, ad esempio il riconoscimento facciale o delle impronte digitali, come alternativa a un PIN di Windows Hello for Business. Gli utenti devono comunque configurare un PIN aziendale in caso di errore dell'autenticazione biometrica. È possibile scegliere tra:
    - **Sì**. Windows Hello for Business consente l'autenticazione biometrica.
    - **No**. Windows Hello for Business impedisce l'autenticazione biometrica per tutti i tipi di account.
- **Usa anti-spoofing avanzato, se disponibile**. Consente di configurare se usare le funzionalità di anti-spoofing di Windows Hello nei dispositivi che lo supportano, ad esempio il rilevamento di una fotografia di un viso invece di un viso reale.<br>Se impostato su **Sì**, Windows richiede a tutti gli utenti di usare la funzionalità di anti-spoofing per le caratteristiche del viso, se supportata.
- **Usare l'accesso tramite telefono**. Se questa opzione è impostata su **Sì**, gli utenti possono usare Passport remoto come dispositivo portatile complementare per l'autenticazione del computer desktop. Il computer desktop deve essere aggiunto ad Azure Active Directory e il dispositivo complementare deve essere configurato con un PIN di Windows Hello for Business.

## <a name="further-information"></a>Altre informazioni
Per altre informazioni su Microsoft Passport, vedere [la guida](https://technet.microsoft.com/library/mt589441.aspx) nella documentazione di Windows 10.
