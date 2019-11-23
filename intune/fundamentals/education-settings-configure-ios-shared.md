---
title: Impostazioni del dispositivo condiviso Intune per l'app Classroom iOS
titleSuffix: Microsoft Intune
description: Informazioni sulle impostazioni di Intune che è possibile usare per controllare le impostazioni per l'app Classroom nei dispositivi iOS.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86b61f628dc559bf0520dbe16ef58644bd360269
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188457"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>Configurare le impostazioni relative all'istruzione di Intune per i dispositivi iPad condivisi

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

> [!NOTE]
> Intune attualmente non supporta la configurazione dell'app per le classi. Questo articolo è applicabile solo per gli utenti con profili di formazione iOS esistenti in Intune.

Intune supporta l'app Classroom iOS, progettata per consentire ai docenti di gestire l'insegnamento e controllare i dispositivi degli studenti in aula. Per l'app Classroom, Apple offre anche la possibilità di configurare i dispositivi iPad degli studenti in modo che un singolo dispositivo possa essere condiviso da più studenti. In questo documento viene spiegato come raggiungere questo obiettivo con Intune.

Per informazioni sulla configurazione dei dispositivi iPad (1:1) dedicati per l'uso dell'app Classroom, vedere [How to configure Intune settings for the iOS Classroom app](education-settings-configure-ios.md) (Come configurare le impostazioni di Intune per l'app Classroom iOS).

## <a name="before-you-start"></a>Prima di iniziare

I prerequisiti per usare le funzionalità degli iPad condivisi sono:

- Impostare [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) e [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617).
- Nell'ambito dell'impostazione di Apple School Manager, configurare gli [ID Apple gestiti](http://help.apple.com/schoolmanager/#/tes78b477c81) per gli studenti. [Altre informazioni sugli ID Apple gestiti](https://support.apple.com/HT205918).
- Creare un profilo di registrazione per i numeri di serie di dispositivi sincronizzati da Apple School Manager.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Passaggio 1: Importare i dati dell'istituto di istruzione in Azure Active Directory

Usare Microsoft School Data Sync (SDS) per importare i record dell'istituto di istruzione da un sistema SIS (Student Information System) esistente in Azure Active Directory (Azure AD).
SDS sincronizza le informazioni dal sistema SIS e le archivia in Azure AD. Azure AD è un sistema di gestione di Microsoft che consente di organizzare utenti e dispositivi. È quindi possibile usare questi dati per gestire studenti e classi. [Altre informazioni su come distribuire SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Come importare i dati con SDS

È possibile importare informazioni in SDS in uno dei modi seguenti:

- [File CSV](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1): esportare e compilare manualmente file con valori delimitati da virgole (CSV)
- [API PowerSchool](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f): provider SIS che semplifica la sincronizzazione con Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab): formato CSV utilizzabile per l'esportazione e la conversione per la sincronizzazione con Azure AD

### <a name="find-out-more"></a>Altre informazioni

- [Altre informazioni sull'esperienza completa di sincronizzazione dei dati dell'istituto di istruzione locali in Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Altre informazioni su Microsoft School Data Sync](https://sds.microsoft.com/)
- [Altre informazioni sulle licenze in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Passaggio 2: Creare e assegnare un profilo Istruzione per iOS in Intune

### <a name="configure-general-settings"></a>Configurare le impostazioni generali

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
5. Nel riquadro dei profili scegliere **Crea profilo**.
6. Nel riquadro **Crea profilo** immettere **Nome** e **Descrizione** per il profilo Istruzione per iOS.
7. Dall'elenco a discesa **Piattaforma** scegliere **iOS**.
8. Dall'elenco a discesa dei tipi di **profilo** scegliere **Istruzione**.
9. Scegliere **Impostazioni** > **Configura**.

Sono quindi necessari i certificati per stabilire una relazione di trust tra gli iPad dei docenti e quelli degli studenti. I certificati vengono usati per autenticare automaticamente le connessioni tra i dispositivi senza dover immettere nomi utente e password.

>[!Important]
>I certificati usati per docenti e studenti devono essere rilasciati da Autorità di certificazione (CA) diverse. È necessario creare due nuove CA subordinate connesse all'infrastruttura di certificati esistente: una per i docenti e una per gli studenti.

I profili di formazione iOS supportano solo i certificati PFX. I certificati SCEP non sono supportati.

I certificati creati devono supportare l'autenticazione server oltre all'autenticazione utente.

### <a name="configure-teacher-certificates"></a>Configurare i certificati per i docenti

Nel riquadro **Istruzione** scegliere **Certificati per docenti**.

#### <a name="configure-teacher-root-certificate"></a>Configurare il certificato radice per i docenti

In **Certificato radice per docenti** scegliere il pulsante Sfoglia per selezionare il certificato radice per docenti con estensione cer (DER o codifica Base64) oppure P7B (con o senza catena completa).

#### <a name="configure-teacher-pkcs12-certificate"></a>Configurare il certificato PKCS#12 per i docenti

In **Certificato PKCS#12 per docenti** configurare i valori seguenti:

- **Formato nome soggetto**: Intune aggiunge automaticamente il prefisso **leader** al nome comune del certificato per il certificato per i docenti e il prefisso **member** per il certificato per gli studenti.
- **Autorità di certificazione**: un'autorità di certificazione globale eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata.
- **Nome dell'autorità di certificazione**: immettere il nome dell'autorità di certificazione.
- **Nome modello di certificato**: immettere il nome di un modello di certificato aggiunto a una CA emittente.
- **Soglia di rinnovo (%)** : specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
- **Periodo di validità del certificato**: specificare la quantità di tempo rimanente prima della scadenza del certificato. È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Il valore deve anche essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.

Al termine della configurazione dei certificati dei docenti, scegliere **OK**.

### <a name="configure-student-certificates"></a>Configurare i certificati per gli studenti

1. Nel riquadro **Istruzione** scegliere **Certificati per studenti**.
2. Nel riquadro **Certificati per studenti** scegliere **iPad condiviso** dall'elenco **Tipo di certificati per il dispositivo di studenti**.

#### <a name="configure-student-root-certificate"></a>Configurare il certificato radice per gli studenti

In **Certificato radice del dispositivo** scegliere il pulsante Sfoglia per selezionare il certificato radice per studenti con estensione cer (DER o codifica Base64) oppure P7B (con o senza catena completa).

#### <a name="configure-device-pkcs12-certificate"></a>Configurare il certificato PKCS#12 per il dispositivo

In **Certificato PKCS#12 per studenti** configurare i valori seguenti:

- **Formato nome soggetto**: Intune aggiunge automaticamente il prefisso leader al nome comune del certificato per il certificato per i docenti e il prefisso member per il certificato per gli studenti.
- **Autorità di certificazione**: un'autorità di certificazione globale eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata.
- **Nome dell'autorità di certificazione**: immettere il nome dell'autorità di certificazione.
- **Nome modello certificato**: immettere il nome di un modello di certificato aggiunto a una CA emittente.
- **Soglia di rinnovo (%)** : specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
- **Periodo di validità del certificato**: specificare la quantità di tempo rimanente prima della scadenza del certificato. È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Il valore deve anche essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.

Al termine della configurazione dei certificati, scegliere **OK**.

### <a name="complete-certificate-setup"></a>Completare l'installazione di certificati

1. Nel riquadro **Istruzione** scegliere **OK**.
2. Nel riquadro **Crea profilo** scegliere **Crea**.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.

## <a name="step-3---create-a-device-category"></a>Passaggio 3: Creare una categoria di dispositivi

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Registrazione del dispositivo**.
4. Nel riquadro **Registrazione del dispositivo - Panoramica** scegliere **Categorie di dispositivi**.
5. Nel riquadro **Registrazione del dispositivo - Categoria di dispositivi** scegliere **Crea**.
6. Nel riquadro **Crea una categoria di dispositivi** immettere un **Nome** e una **Descrizione** per la categoria.
7. Nel riquadro **Crea una categoria di dispositivi** scegliere **Crea**.

La categoria di dispositivi viene creata nel riquadro **Registrazione - Categoria di dispositivi**.

## <a name="step-4--create-a-dynamic-group"></a>Passaggio 4: Creare un gruppo dinamico

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Gruppi**.
4. Nel riquadro **Utenti e gruppi - Tutti i gruppi** scegliere **Nuovo gruppo**.
5. Nel riquadro **Gruppo** scegliere un **Tipo di gruppo** e immettere **Nome** e **Descrizione** per il gruppo.
6. Dall'elenco a discesa **Tipo di appartenenza** scegliere **Dispositivo dinamico**.
7. Scegliere **Membri dispositivo dinamico** per creare le regole di appartenenza.
8. Nel riquadro **Regole di appartenenza dinamica**:
1. Selezionare **deviceCategory** dall'elenco a discesa **Aggiungi dispositivi dove**.
2. Scegliere **Uguale a**.
3. Immettere la categoria del dispositivo creato nella casella di testo vuota.
9. Nel riquadro **Regole di appartenenza dinamica** scegliere **Aggiungi query**.
10. Nel riquadro **Gruppo** scegliere **Crea**.

Il gruppo dinamico viene creato nel riquadro **Utenti e gruppi - Tutti i gruppi**.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>Passaggio 5: Assegnare un dispositivo a una categoria (Carrelli)

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Dispositivi**.
4. Nel riquadro **Dispositivi** scegliere **Tutti i dispositivi**.
5. Scegliere un dispositivo nel riquadro **Dispositivi - Tutti i dispositivi**.
6. Nel riquadro dei dispositivi scegliere **Proprietà**.
7. Nel riquadro delle proprietà del dispositivo immettere la categoria del dispositivo nella casella di testo **Categoria del dispositivo**.
8. Nel riquadro del dispositivo scegliere **Salva**.

Il dispositivo è ora associato alla categoria del dispositivo. Ripetere questo processo per tutti i dispositivi che si intende associare alla categoria del dispositivo creata.

## <a name="step-6--create-classroom-profiles"></a>Passaggio 6: Creare profili di classe

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Profili del carrello**.
5. Nel riquadro dei profili scegliere **Crea profilo**.
6. Nel riquadro **Crea l'associazione** immettere un **Nome** e una **Descrizione**.
7. Scegliere **Seleziona classi** > **Configura** per associare i gruppi al profilo del carrello.
8. Scegliere le classi da includere nel profilo del carrello e quindi scegliere **Selezione**. 
9. Scegliere **Seleziona carrelli** > **Configura** per associare i gruppi al profilo del carrello.
10. Scegliere i gruppi da includere nel profilo del carrello e quindi scegliere **Selezione**.
11. Nel riquadro **Crea l'associazione** scegliere **Salva** per salvare il profilo del carrello.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>Passaggio 7: Assegnare il profilo del carrello alle classi

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
4. Nel riquadro **Configurazione del dispositivo** scegliere **Monitoraggio** > **Stato assegnazione**.
5. Nel riquadro **Stato assegnazione** selezionare il **Profilo del carrello** creato.
6. Nel riquadro **Profili del carrello** scegliere **Assegnazioni** e quindi in **Includi** scegliere **Selezionare i gruppi da includere**.
7. Selezionare le classi da specificare come destinazione del profilo del carrello (non selezionare un gruppo) e quindi scegliere **Selezione**. 
8. Al termine, scegliere **Salva**.

L'assegnazione viene completata e Intune distribuisce il profilo Classroom ai dispositivi di destinazione in base all'assegnazione della classe.

## <a name="next-steps"></a>Passaggi successivi

Ora gli studenti possono condividere i dispositivi e prendere qualsiasi iPad in una classe, accedere con un PIN e avere il dispositivo personalizzato con il proprio contenuto. Per altre informazioni sugli iPad condivisi, vedere il [sito Web di Apple](https://www.apple.com/education/it/).
