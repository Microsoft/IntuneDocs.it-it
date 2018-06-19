---
title: Impostazioni di Intune per l'app Classroom iOS
titleSuffix: Microsoft Intune
description: Informazioni sulle impostazioni di Intune che è possibile usare per controllare le impostazioni per l'app Classroom nei dispositivi iOS.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/9/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ff30ef609cf2ad742b55d80f418919bf4ab144a
ms.sourcegitcommit: d40bfb6af66f2ce7026c0151ace98ec23f1cf76e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "33927441"
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Come configurare le impostazioni di Intune per l'app Classroom iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]
>[!NOTE]
>Le impostazioni di Intune per l'app Classroom sono ora obsolete in Intune. Questo articolo è applicabile solo per gli utenti con profili di formazione esistenti in Intune.

## <a name="introduction"></a>Introduzione
[Classroom](https://itunes.apple.com/app/id1085319084) è un'app progettata per consentire ai docenti di gestire l'insegnamento e di controllare i dispositivi degli studenti in aula. Ad esempio, l'app consente ai docenti di:

- Aprire app nei dispositivi degli studenti
- Bloccare e sbloccare lo schermo dell'iPad
- Visualizzare lo schermo dell'iPad di uno studente
- Impostare gli iPad degli studenti su un segnalibro o il capitolo di un libro
- Visualizzare lo schermo dell'iPad di uno studente su una TV Apple

Per configurare Classroom nel dispositivo, sarà necessario creare e configurare un profilo del dispositivo Istruzione per iOS in Intune.

## <a name="before-you-start"></a>Prima di iniziare

Tenere presenti le considerazioni seguenti prima di iniziare a configurare le impostazioni:

- Sia gli iPad dei docenti che quelli degli studenti devono essere registrati in Intune.
- Assicurarsi di aver installato l'app [Classroom Apple](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) nel dispositivo del docente. È possibile installare l'app manualmente o usare la [gestione delle app in Intune](app-management.md).
- È necessario configurare i certificati per autenticare le connessioni tra i dispositivi di docenti e studenti (vedere il passaggio 2, Creare e assegnare un profilo Istruzione per iOS in Intune).
- Gli iPad di docenti e studenti devono trovarsi nella stessa rete Wi-Fi e avere abilitato Bluetooth.
- L'app Classroom può essere eseguita su iPad con supervisione che eseguono iOS 9.3 o versione successiva.
- In questa versione, Intune supporta la gestione di scenari 1:1 in cui ogni studente ha un iPad proprio dedicato.


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

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
5.  Nel riquadro dei profili scegliere **Crea profilo**.
6.  Nel riquadro **Crea profilo** immettere **Nome** e **Descrizione** per il profilo Istruzione per iOS.
7.  Dall'elenco a discesa **Piattaforma** scegliere **iOS**.
8.  Dall'elenco a discesa dei tipi di **profilo** scegliere **Istruzione**.
9.  Scegliere **Impostazioni** > **Configura**.


Nella sezione successiva si creeranno i certificati per stabilire una relazione di trust tra gli iPad dei docenti e quelli degli studenti. I certificati vengono usati per autenticare automaticamente le connessioni tra i dispositivi senza dover immettere nomi utente e password.

>[!IMPORTANT]
>I certificati usati per docenti e studenti devono essere rilasciati da Autorità di certificazione (CA) diverse. È necessario creare due nuove CA subordinate connesse all'infrastruttura di certificati esistente: una per i docenti e una per gli studenti.

I profili di formazione iOS supportano solo i certificati PFX. I certificati SCEP non sono supportati.

I certificati creati devono supportare l'autenticazione server e l'autenticazione utente.

### <a name="configure-teacher-certificates"></a>Configurare i certificati per i docenti

Nel riquadro **Istruzione** scegliere **Certificati per docenti**.

#### <a name="configure-teacher-root-certificate"></a>Configurare il certificato radice per i docenti

In **Certificato radice per docenti** scegliere il pulsante Sfoglia. Selezionare il certificato radice con:
- Estensione cer (con codifica DER o Base 64) 
- Estensione P7B (con o senza catena completa)

#### <a name="configure-teacher-pkcs12-certificate"></a>Configurare il certificato PKCS#12 per i docenti

In **Certificato PKCS#12 per docenti** configurare i valori seguenti:

- **Formato nome soggetto**: Intune aggiunge automaticamente il prefisso **leader** ai nomi comuni dei certificati per i docenti. Ai nomi comuni dei certificati per gli studenti viene aggiunto il prefisso **member**.
- **Autorità di certificazione**: un'autorità di certificazione globale eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. 
- **Nome dell'autorità di certificazione**: immettere il nome dell'autorità di certificazione.
- **Nome modello certificato**: immettere il nome di un modello di certificato aggiunto a una CA emittente. 
- **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
- **Periodo di validità del certificato**: specificare la quantità di tempo rimanente prima della scadenza del certificato.
È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Il valore deve anche essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.

Al termine della configurazione dei certificati, scegliere **OK**.

### <a name="configure-student-certificates"></a>Configurare i certificati per gli studenti

1.  Nel riquadro **Istruzione** scegliere **Certificati per studenti**.
2.  Nella riquadro **Certificati per studenti** scegliere **1:1** nell'elenco **Tipo di certificati per il dispositivo di studenti**.

#### <a name="configure-student-root-certificate"></a>Configurare il certificato radice per gli studenti

In **Certificato radice per studenti** scegliere il pulsante Sfoglia. Selezionare il certificato radice con:
- Estensione cer (con codifica DER o Base 64) 
- Estensione P7B (con o senza catena completa)

#### <a name="configure-student-pkcs12-certificate"></a>Configurare il certificato PKCS#12 per gli studenti

In **Certificato PKCS#12 per studenti** configurare i valori seguenti:

- **Formato nome soggetto**: Intune aggiunge automaticamente il prefisso **leader** ai nomi comuni dei certificati per i docenti. Ai nomi comuni dei certificati per gli studenti viene aggiunto il prefisso **member**.
- **Autorità di certificazione**: un'autorità di certificazione globale eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. 
- **Nome dell'autorità di certificazione**: immettere il nome dell'autorità di certificazione.
- **Nome modello certificato**: immettere il nome di un modello di certificato aggiunto a una CA emittente. 
- **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
- **Periodo di validità del certificato**: specificare la quantità di tempo rimanente prima della scadenza del certificato.
È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Il valore deve anche essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.

Al termine della configurazione dei certificati, scegliere **OK**.

## <a name="finish-up"></a>Terminare

1.  Nel riquadro **Istruzione** scegliere OK.
2.  Nel riquadro **Crea profilo** scegliere **Crea**.
    
Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.

Assegnare il profilo ai dispositivi degli studenti nei gruppi di classi creati durante la sincronizzazione dei dati dell'istituto di istruzione con Azure AD (vedere [Come assegnare i profili di dispositivo](device-profile-assign.md)).

## <a name="next-steps"></a>Passaggi successivi

A questo punto, i docenti che usano l'app Classroom avranno il controllo completo sui dispositivi degli studenti.

Per altre informazioni sull'app Classroom, vedere [Aiuto Classroom](https://help.apple.com/classroom/ipad/2.0/) nel sito Web di Apple.

Se si vogliono configurare i dispositivi iPad condivisi per studenti, vedere [How to configure Intune education settings for shared iPad devices](education-settings-configure-ios-shared.md) (Come configurare le impostazioni di formazione di Intune per i dispositivi iPad condivisi).
