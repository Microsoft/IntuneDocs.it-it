---
# required metadata

title: Prepararsi alla registrazione dei dispositivi in Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Prepararsi alla registrazione dei dispositivi in Microsoft Intune
Per consentire ai dipendenti di registrare i dispositivi mobili, compresi telefoni Android, iOS e Windows Phone e computer Windows, con Intune è necessario abilitare la registrazione dei dispositivi. Per consentire la registrazione è necessario impostare un'autorità di gestione dei dispositivi mobili, configurare il portale aziendale di Intune, assegnare le licenze e abilitare la registrazione per la piattaforma del dispositivo.

## <a name="BKMK_Set_MDM_Authority"></a>Impostare l'autorità di gestione dei dispositivi mobili
Questa autorità definisce il servizio di gestione con le autorizzazioni per la gestione di un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune. Se Configuration Manager è impostato come autorità di gestione, non è possibile usare altri servizi per la gestione dei dispositivi mobili.

>[!IMPORTANT]
> Valutare attentamente se gestire i dispositivi mobili usando solo Intune (servizio online) o System Center Configuration Manager con Intune (soluzione software locale in combinazione con un servizio online). Dopo l'impostazione, l'autorità di gestione del dispositivo mobile non può essere modificata.



1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; ** Gestione dei dispositivi mobili**.

2.  Nell'elenco **Attività** fare clic su **Imposta autorità di gestione dei dispositivi mobili**. Verrà visualizzata la finestra di dialogo **Imposta autorità MDM** .

    ![Finestra di dialogo Imposta autorità MDM](../media/intune-mdm-authority.png)

3.  Intune richiede di confermare che si vuole usare Intune come autorità di gestione dei dispositivi mobili. Selezionare la casella e quindi fare clic su **Sì** per usare Microsoft Intune per la gestione dei dispositivi mobili.

## Configurare il portale aziendale di Intune e assegnare licenze
Il portale aziendale di Intune consente agli utenti di accedere alle risorse aziendali, ad esempio alle applicazioni, trovare le informazioni di supporto tecnico e registrare i dispositivi o annullarne la registrazione. Prima di registrare i dispositivi è necessario [configurare il portale aziendale](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7). È necessario anche [assegnare licenze utente](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4) per consentire l'accesso a Intune.

## Impostare la gestione dei dispositivi
Dopo aver impostato l'autorità MDM, è necessario impostare la gestione dei dispositivi per i sistemi operativi che l'organizzazione vuole supportare. I passaggi necessari per configurare la gestione dei dispositivi variano a seconda del sistema operativo. Ad esempio, il sistema operativo Android non richiede di eseguire alcuna operazione nella console di amministrazione di Intune. Windows e iOS invece richiedono una relazione di trust tra i dispositivi e Intune per consentire la gestione.

> [!div class="op_single_selector"]
- [Configurare la gestione per Android con Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Impostare la gestione di Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurare la gestione dei dispositivi Windows con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

È inoltre possibile:
 - Usare [l'account manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) per registrare più dispositivi
 - [Specificare i dispositivi di proprietà dell'azienda con i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) per registrare i dispositivi e i criteri di destinazione


<!--HONumber=May16_HO1-->


