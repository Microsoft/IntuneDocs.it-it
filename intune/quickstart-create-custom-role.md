---
title: 'Guida introduttiva: creare e assegnare un ruolo personalizzato in Intune'
description: 'Guida introduttiva: creare e assegnare un ruolo personalizzato per un servizio di gestione dispositivi remoti.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6cf4e365f4e68920ea5d24dc3ce2e1bd5eb9f817
ms.sourcegitcommit: 9af102e1232d9a568a7901783c30ba9905e64d99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477129"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Guida introduttiva: Creare e assegnare un ruolo personalizzato

In questa guida introduttiva di Intune si creerà un ruolo personalizzato con autorizzazioni specifiche per un reparto di operazioni di sicurezza. Quindi, si assegnerà il ruolo a un gruppo di operatori. Esistono diversi ruoli predefiniti che è possibile utilizzare sin da subito. Ma creando ruoli personalizzati come questo, è possibile esercitare un controllo di accesso preciso su tutti gli elementi del sistema di gestione dei dispositivi mobili.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Per completare questa guida introduttiva, è necessario [creare un gruppo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="create-a-custom-role"></a>Creare un ruolo personalizzato

Quando si crea un ruolo personalizzato, è possibile impostare le autorizzazioni per un'ampia gamma di azioni. Per il ruolo operazioni di sicurezza, verranno impostate alcune autorizzazioni di lettura in modo che l'operatore possa esaminare le configurazioni e i criteri di un dispositivo.

1. In Intune scegliere **Ruoli** > **Tutti i ruoli** > **Aggiungi**.
![Browser](media/quickstart-create-custom-role/add-custom-role.png)
2. In **Aggiungi ruolo personalizzato**, nella casella **Nome**, immettere *Operazioni di sicurezza*.
3. Nella casella **Descrizione** immettere *Questo ruolo consente un operatore della sicurezza di monitorare la configurazione del dispositivo e le informazioni di conformità.*
4. Scegliere **Configura** > **Identificatori dei dispositivi aziendali** > **Sì** accanto a **Lettura** > **OK**.
![Browser](media/quickstart-create-custom-role/corp-device-id-read.png)
5. Scegliere **Tutti i criteri di conformità del dispositivo** > **Sì** accanto a **Lettura** > **OK**.
6. Scegliere **Device configurations (Configurazioni dispositivo)** > **Sì** accanto a **Lettura** > **OK**.
7. Scegliere **Organizzazione** > **Sì** accanto a **Lettura** > **OK**.
8. Scegliere **OK** > **Crea**.

## <a name="assign-the-role-to-a-group"></a>Assegnare il ruolo a un gruppo

Prima che l'operatore della sicurezza possa usare le nuove autorizzazioni, è indispensabile assegnare il ruolo a un gruppo che contenga l'utente di sicurezza.

1. In Intune scegliere **Ruoli** > **Tutti i ruoli** > **Security operations** (Operazioni di sicurezza).
2. In **Ruoli di Intune** scegliere **Assegnazioni** > **Assegna**.
3. Nella casella **Nome dell'assegnazione** immettere *Sec ops*.
4. Scegliere **Membri (gruppi)** > **Aggiungi**.
5. Scegliere il gruppo **Contoso Testers**.
6. Scegliere **Seleziona** > **OK**.
7. Scegliere **Ambito (gruppi)** > **Selezionare i gruppi da includere** > **Contoso Testers**.
8. Scegliere **Seleziona** > **OK** > **OK**.

A questo punto tutti i membri del gruppo fanno parte del ruolo *Operazioni di sicurezza* e possono accedere alle seguenti informazioni su un dispositivo: identificatori dei dispositivi aziendali, criteri di conformità dei dispositivi, configurazioni dei dispositivi e informazioni sull'organizzazione.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se non si desidera usare più il nuovo ruolo personalizzato, è possibile eliminarlo. Scegliere **Ruoli** > **Tutti i ruoli** > scegliere i puntini di sospensione accanto al ruolo > **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato creato un ruolo operazioni di sicurezza personalizzato e il ruolo è stato assegnato a un gruppo. Per altre informazioni sui ruoli in Intune, vedere [Controllo degli accessi in base al ruolo (RBAC) con Microsoft Intune](role-based-access-control.md)

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Creare un profilo di posta elettronica del dispositivo per iOS](quickstart-email-profile.md)
