---
title: 'Guida introduttiva: creare e assegnare un ruolo personalizzato in Intune'
description: 'Guida introduttiva: creare e assegnare un ruolo personalizzato per un servizio di gestione dispositivi remoti.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 66426e9e22c2624b9828440906e3b1b947f4b60a
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581668"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Guida introduttiva: creare e assegnare un ruolo personalizzato

In questa guida introduttiva di Intune si creerà un ruolo personalizzato con autorizzazioni specifiche per un reparto di operazioni di sicurezza. Quindi, si assegnerà il ruolo a un gruppo di operatori. Esistono diversi ruoli predefiniti che è possibile utilizzare sin da subito. Ma creando ruoli personalizzati come questo, è possibile esercitare un controllo di accesso preciso su tutti gli elementi del sistema di gestione dei dispositivi mobili.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Per completare questa guida introduttiva, è necessario [creare un gruppo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.

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

1. In Intune scegliere **Ruoli** > **Tutti i ruoli** > **Remote device helpdesk** (Helpdesk dispositivo remoto).
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

In questa guida introduttiva è stato creato un ruolo operazioni di sicurezza personalizzato e il ruolo è stato assegnato a un gruppo. È possibile ottenere altre informazioni sui problemi di sicurezza nell'articolo seguente.

> [!div class="nextstepaction"]
> [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md)