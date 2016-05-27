---
# required metadata

title: Nomi di dominio per Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Nomi di dominio di Microsoft Intune

Prima di configurare Microsoft Intune, leggere questo argomento e i requisiti indicati nelle [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Quando l'organizzazione si iscrive a un servizio basato su cloud di Microsoft come Intune, si riceve un nome di dominio iniziale simile al seguente: **contoso.onmicrosoft.com**. In questo esempio, **contoso** è il nome scelto al momento dell'iscrizione e **onmicrosoft.com** è il suffisso assegnato agli account che si aggiungono alla sottoscrizione. Dopo aver completato la procedura di iscrizione, è possibile modificare il nome di dominio. Tuttavia, l'amministratore globale può aggiungere anche nomi di dominio personalizzati per l'organizzazione da usare con i servizi, oppure rimuovere i domini aggiunti in precedenza.

Per impostazione predefinita, quando si usa il dominio onmicrosoft, ogni utente importato riceve il suffisso **onmicrosoft.com** come nome entità utente (UPN).

Per usare un nome di dominio di cui si è proprietari anziché quello assegnato al momento dell'iscrizione, è possibile aggiungere il nome di dominio ad Azure Active Directory. Dopo che il dominio è stato aggiunto ed è stato verificato che si è i proprietari, è possibile creare account e gruppi che includono il nome di dominio modificando i record risorsa DNS nel provider del servizio di hosting DNS. Per semplificare la gestione degli account utente, quando si pianifica l'uso di un dominio personalizzato, configurare un nome di dominio personalizzato nella sottoscrizione prima di iniziare a sincronizzare gli utenti di Active Directory locale.

La configurazione dei nomi di dominio e dei record di risorse DNS per Intune è identica a quella degli altri tenant Azure Active Directory. Per leggere le istruzioni vedere [Aggiungere un nome di dominio personalizzato ad Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

### Vedere anche
[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO1-->


