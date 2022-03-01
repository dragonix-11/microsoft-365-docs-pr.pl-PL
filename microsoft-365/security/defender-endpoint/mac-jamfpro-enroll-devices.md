---
title: Zarejestruj program Microsoft Defender dla punktu końcowego na urządzeniach z systemem macOS do usługi Jamf Pro
description: Zarejestruj program Microsoft Defender dla punktu końcowego na urządzeniach z systemem macOS do usługi Jamf Pro
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ab3db2e2b64261ae00008aef448a214cd235bda9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011313"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Zarejestruj program Microsoft Defender dla punktu końcowego na urządzeniach z systemem macOS do usługi Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>Zarejestruj urządzenia z systemem macOS

Istnieje wiele metod zarejestrowania się w programie JamF.

W tym artykule podano dwie metody:

- [Metoda 1. Zaproszenia do rejestracji](#enrollment-method-1-enrollment-invitations)
- [Metoda 2. Rejestracja w przedsprzedażu](#enrollment-method-2-prestage-enrollments)

Aby uzyskać pełną listę, zobacz [Informacje o rejestracji komputera](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html).

## <a name="enrollment-method-1-enrollment-invitations"></a>Metoda rejestracji 1: Zaproszenia do rejestracji

1. Na pulpicie nawigacyjnym Pro Jamf przejdź do **strony Zaproszenia do rejestracji**.

    ![Obraz ustawień konfiguracji1.](images/a347307458d6a9bbfa88df7dbe15398f.png)

2. Wybierz **pozycję + Nowy**.

    ![Automatycznie wygenerowano zbliżnie logo Description (Opis).](images/b6c7ad56d50f497c38fc14c1e315456c.png)

3. W **obszarze Określ adresatów dla zaproszenia** > w obszarze Adresy  e-mail wprowadź adresy e-mail adresatów.

    ![Obraz ustawień konfiguracji2.](images/718b9d609f9f77c8b13ba88c4c0abe5d.png)

    ![Obraz ustawień konfiguracji3.](images/ae3597247b6bc7c5347cf56ab1e820c0.png)

    Na przykład: janedoe@contoso.com

    ![Obraz ustawień konfiguracji4.](images/4922c0fcdde4c7f73242b13bf5e35c19.png)

4. Skonfiguruj wiadomość dla zaproszenia.

    ![Obraz ustawień konfiguracji5.](images/ce580aec080512d44a37ff8e82e5c2ac.png)

    ![Obraz ustawień konfiguracji6.](images/5856b765a6ce677caacb130ca36b1a62.png)

    ![Obraz ustawień konfiguracji7.](images/3ced5383a6be788486d89d407d042f28.png)

    ![Obraz ustawień konfiguracji8.](images/54be9c6ed5b24cebe628dc3cd9ca4089.png)

## <a name="enrollment-method-2-prestage-enrollments"></a>Metoda rejestracji 2: rejestracja w przedsprzedażu

1. Na pulpicie nawigacyjnym usługi Jamf Pro przejdź do strony **Rejestracja w przedsprzedażu**.

    ![Obraz ustawień konfiguracji9.](images/6fd0cb2bbb0e60a623829c91fd0826ab.png)

2. Postępuj zgodnie z instrukcjami [w tece Rejestracja na komputerze w przedsprzedażu](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Zarejestruj urządzenie z systemem macOS

1. Wybierz **pozycję Kontynuuj** i zainstaluj certyfikat urzędu certyfikacji w **oknie Preferencje** systemowe.

    ![Obraz: Jamf Pro enrollment1.](images/jamfpro-ca-certificate.png)

2. Po zainstalowaniu certyfikatu urzędu certyfikacji wróć do okna przeglądarki i wybierz pozycję **Kontynuuj** i zainstaluj profil MDM.

    ![Obraz: Jamf Pro enrollment2.](images/jamfpro-install-mdm-profile.png)

3. Wybierz **pozycję Zezwalaj** , aby pobierać pliki z jamf.

    ![Obraz jamf Pro rejestracji3.](images/jamfpro-download.png)

4. Wybierz **pozycję Kontynuuj** , aby kontynuować instalację profilu MDM.

    ![Obraz jamf Pro rejestracji4.](images/jamfpro-install-mdm.png)

5. Wybierz **pozycję Kontynuuj** , aby zainstalować profil MDM.

    ![Obraz: Jamf Pro enrollment5.](images/jamfpro-mdm-unverified.png)

6. Wybierz **pozycję Kontynuuj**  , aby ukończyć konfigurację.

    ![Obraz: Jamf Pro enrollment6.](images/jamfpro-mdm-profile.png)
