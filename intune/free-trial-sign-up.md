---
title: Iscriversi per una valutazione gratuita di 30 giorni
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: come effettuare l&quot;iscrizione a Intune in Azure.'
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3be43e12abc1cf90da3584450ddd56ab63bdfac1
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune per l'anteprima del portale di Azure

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Questo articolo descrive la procedura di iscrizione a una versione di valutazione di Intune autonomo per l'anteprima del portale di Azure. <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. Visitare la pagina di [iscrizione a Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) e compilare il modulo per richiedere una sottoscrizione di valutazione.

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![Immagine della pagina di iscrizione](./media/1-clicking-try.png)

 > [!TIP]
> Se per la maggior parte delle operazioni IT e degli utenti viene usata una lingua diversa dalla propria, è necessario selezionare la lingua in **Where's your company located?** (Dov'è situata la tua azienda?).

2. Al termine del processo di iscrizione, l'utente riceverà un messaggio con le nuove informazioni sull'account. <br/> ![Immagine delle informazioni sull'account](./media/2-end-of-sign-up-process.png) <br/>A questo punto, se si fa clic su **You're ready to go** (Sei pronto per procedere), si verrà indirizzati all'interfaccia di amministrazione di Office 365, in cui è possibile aggiungere utenti all'ambiente di test. <br/><br/>Tuttavia, se si desidera accedere direttamente al portale di anteprima di Intune in Azure, aprire una nuova finestra del browser e digitare **https://portal.azure.com** nella barra degli indirizzi. Verrà visualizzata la pagina di accesso ad Azure in cui è possibile accedere tramite le credenziali assegnate. Usare questo indirizzo per accedere alla versione di valutazione di Intune. <br/> ![Immagine della pagina di accesso al portale di Azure](./media/azure-portal-signin.png)

Al primo accesso all'anteprima di Intune in Azure, Intune potrebbe non essere visibile nel dashboard di Azure. Per aggiungere il servizio Intune al dashboard di Azure:
1. Scegliere **Altri servizi >** nell'elenco dei servizi di Azure a sinistra del dashboard e immettere **Intune** nella casella di ricerca.
2. Scegliere **Intune** nell'elenco e selezionare la stella per aggiungere il servizio all'elenco dei servizi.<br/> ![Immagine della selezione di Intune dall'elenco dei servizi](./media/azure-add-intune1.png)
3. Scegliere quindi **Intune** nell'elenco dei servizi per aprire il dashboard di Intune.

Quando si esegue l'iscrizione per una versione di valutazione, all'indirizzo di posta elettronica specificato in fase di iscrizione verrà anche inviato un messaggio contenente le informazioni sul proprio account. Questo messaggio conferma che la versione di valutazione è attiva.


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>Esperienze diverse per l'amministrazione
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Per l'anteprima di Intune in Azure verranno usati tre portali:
- Il dashboard di Intune in Azure ([portal.azure.com](https://portal.azure.com)) in cui è possibile esplorare le [funzionalità di Intune nel portale di Azure](what-is-intune.md).
- L'interfaccia di amministrazione di Office 365 ([portal.office.com](https://portal.office.com)) in cui è possibile aggiungere e gestire gli utenti se non si usa Azure Active Directory a tale scopo. È anche possibile gestire altri aspetti del proprio account, incluse la fatturazione e il supporto tecnico.
- La console di amministrazione di Intune classica ([manage.microsoft.com](https://manage.microsoft.com)) in cui è possibile esplorare le funzionalità che non sono ancora state aggiunte ad Azure.

In genere le operazioni vengono eseguite nel dashboard di Intune, illustrato di seguito. Questa console consente infatti di impostare e gestire i gruppi, i criteri, i dispositivi e le app.

È possibile passare alla console di amministrazione di Intune classico dal dashboard scegliendo il riquadro **Apri il portale classico di Intune**.

Per tornare all'anteprima di Intune in Azure, immettere https://portal.azure.com nella barra degli indirizzi del browser e quindi scegliere di nuovo **Intune** nell'elenco dei servizi.

 ![Immagine del dashboard di Intune](./media/intune-azure-dashboard.png)


Per aggiungere e gestire gli utenti e per altri aspetti dell'account, inclusi la fatturazione e il supporto, viene tuttavia usata l'interfaccia di amministrazione di Office 365, illustrata di seguito.

![Immagine dell'interfaccia di amministrazione di Office 365](./media/office-admin-center.png)

Per passare dall'interfaccia di amministrazione di Office 365 al dashboard di Intune, immettere https://portal.azure.com nella barra degli indirizzi del browser. Scegliere **Intune** nell'elenco dei servizi.

Per tornare all'interfaccia di amministrazione di Office 365 da Intune, immettere https://portal.office.com nella barra degli indirizzi del browser. Se è già stato effettuato l'accesso in Intune, si passerà direttamente all'interfaccia di amministrazione di Office 365.

## <a name="next-steps"></a>Passaggi successivi

### <a name="intune-azure-preview"></a>Anteprima di Intune in Azure
Altre informazioni sull'[anteprima di Intune nel portale di Azure](what-is-intune.md)
### <a name="classic-intune"></a>Intune classico
Scenario di valutazione: [Valutare la gestione dei dispositivi mobili in Microsoft Intune](https://docs.microsoft.com/intune-classic/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>Integrazione con altri prodotti
Per altre informazioni sull'uso degli account utente di Azure Active Directory con Intune, vedere:
- [Identity requirements](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview) (Requisiti di identità)
- [Determinare i requisiti di sincronizzazione delle directory](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Determinare i requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Altre informazioni sull'uso di [Intune con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

