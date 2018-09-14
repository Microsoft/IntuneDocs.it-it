---
title: Configurare le impostazioni di Identity Protection in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere un profilo di dispositivo per impostare Windows Hello for Business nei dispositivi Windows 10 in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43318006"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Configurare le impostazioni di Identity Protection in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I profili di Identity Protection controllano come viene eseguito il provisioning di Windows Hello for Business e come quest'ultimo viene configurato nei dispositivi Windows 10 gestiti. Creare il profilo per configurare:  
* La disponibilità di Windows Hello for Business per dispositivi e utenti.
* I requisiti di aggiunta dei dispositivi.
* I movimenti che gli utenti possono e non possono usare per accedere ai propri dispositivi.  

 È possibile assegnare questo profilo a utenti e gruppi di dispositivi selezionati oppure a tutti gli utenti e a tutti i dispositivi. I gruppi ricevano il profilo di Identity Protection quando accedono a Intune.    

Usare le informazioni di questo articolo per creare profili di Identity Protection. In seguito [assegnare il profilo](device-profile-assign.md) ai gruppi di utenti e dispositivi.

Questa funzionalità si applica ai dispositivi che eseguono:  
- Windows 10 e versioni successive
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Creare un profilo del dispositivo contenente le impostazioni di Identity Protection

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Inserire un **Nome** e una **Descrizione** per il profilo di Identity Protection.
5. Dall'elenco a discesa **Piattaforma** selezionare **Windows 10 e versioni successive**. Windows Hello for Business è supportato solo nei dispositivi che eseguono Windows 10 e versioni successive.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Identity Protection**.
7. Nel riquadro Windows Hello for Business scegliere tra le impostazioni di configurazione seguenti:
    * Disabilitato. Selezionare questa impostazione se non si vuole usare Windows Hello for Business. Tutte le altre impostazioni nella schermata risultano non disponibili.
    * Abilitata. Selezionare questa impostazione se si vuole configurare le impostazioni di Windows Hello for Business.  

8. Se si seleziona **Abilitato** nel passaggio precedente, configurare le impostazioni obbligatorie che verranno applicate ai dispositivi di destinazione Windows 10 e Windows 10 Mobile registrati e agli utenti relativi.

> [!NOTE]
> Quando si assegnano i profili di Identity Protection solo agli utenti, per impostazione predefinita il contesto del dispositivo è **Non configurato**.  

   - **Lunghezza minima del PIN**/**Lunghezza massima del PIN**. Configura i dispositivi in modo che usino i valori massimo e minimo specificati per la lunghezza del PIN per garantire l'accesso protetto. La lunghezza del PIN predefinita è 6 caratteri, ma è possibile applicare una lunghezza minima di 4 caratteri. La lunghezza massima del PIN è 127 caratteri.  

   - **Lettere minuscole nel PIN**/**Lettere maiuscole nel PIN**/**Caratteri speciali nel PIN**. Per applicare un PIN più complesso, richiedere l'utilizzo di lettere maiuscole, lettere minuscole e caratteri speciali nel PIN. Scegliere tra:

     - **Consentito**. Gli utenti possono usare il tipo di carattere specificato nel proprio PIN, ma non è obbligatorio.

     - **Obbligatorio**. Gli utenti devono includere almeno uno dei tipi di carattere specificati nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.

     - **Non consentito** (impostazione predefinita). Gli utenti non devono usare questi tipi di carattere nel PIN. Questo comportamento si verifica anche se l'impostazione non è configurata.<br>I caratteri speciali includono: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Scadenza PIN (giorni)**. Si consiglia di specificare un periodo di scadenza dopo il quale gli utenti finali devono modificare il PIN. L'impostazione predefinita è 41 giorni.

   - **Ricorda cronologia PIN**. Limita il riutilizzo di PIN usati in precedenza. Per impostazione predefinita, non è possibile riutilizzare gli ultimi 5 PIN.  
   - **Enable PIN recovery** (Abilita ripristino PIN): consente all'utente di modificare il PIN con il servizio di ripristino PIN di Windows Hello for Business. 
       - **Abilita**. Il servizio cloud esegue la crittografia di un segreto del ripristino PIN da archiviare nel dispositivo. L'utente può modificare il PIN, se necessario.  
       - **Non configurato** (impostazione predefinita). Non viene creato né archiviato alcun segreto del ripristino del PIN. Se l'utente dimentica il PIN, l'unico modo per ottenere un nuovo PIN consiste nell'eliminare quello esistente e crearne uno nuovo. L'utente dovrà ripetere la registrazione per tutti i servizi cui accedeva con il vecchio PIN.  
   
   - **Usa un modulo TPM (Trusted Platform Module)**. Un chip TPM (Trusted Platform Module) fornisce un livello aggiuntivo di sicurezza dei dati. Scegliere uno dei valori seguenti:  
     - **Abilita**. Solo i dispositivi con un modulo TPM accessibile possono eseguire il provisioning di Windows Hello for Business.
     - **Non configurato**. Tutti i dispositivi possono eseguire il provisioning di Windows Hello for Business, anche quando non esiste alcun modulo TPM utilizzabile. I dispositivi tentano per prima cosa di usare un modulo TPM, ma se non ve ne sono disponibili, i dispositivi possono usare la crittografia software.  

   - **Consenti autenticazione biometrica**. Abilita l'autenticazione biometrica, ad esempio il riconoscimento facciale o delle impronte digitali, come alternativa a un PIN di Windows Hello for Business. Gli utenti devono comunque configurare un PIN aziendale in caso di errore dell'autenticazione biometrica. Scegliere tra:

     - **Abilita**. Windows Hello for Business consente l'autenticazione biometrica.
     - **Non configurato** (impostazione predefinita). Windows Hello for Business impedisce l'autenticazione biometrica per tutti i tipi di account.

   - **Usa anti-spoofing avanzato, se disponibile**. Consente di configurare se usare le funzionalità di anti-spoofing di Windows Hello nei dispositivi che lo supportano, ad esempio il rilevamento di una fotografia di un viso invece di un viso reale.
       - **Abilita**. Windows richiede a tutti gli utenti di usare la funzionalità di anti-spoofing per il riconoscimento facciale, se supportata.  
       - **Non configurato** (impostazione predefinita). Windows rispetta le configurazioni di anti-spoofing del dispositivo.

   - **Certificate for on-premise resources** (Certificato per le risorse locali). 
       - **Abilita**. Consente a Windows Hello for Business di usare i certificati per l'autenticazione a risorse locali.
       - **Non configurato** (impostazione predefinita). Impedisce a Windows Hello for Business di usare i certificati per l'autenticazione a risorse locali.  
9. Fare clic su **OK** per salvare il profilo.  

Il profilo viene creato e visualizzato nell'elenco **Configurazione del dispositivo - Profili**. Per proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
