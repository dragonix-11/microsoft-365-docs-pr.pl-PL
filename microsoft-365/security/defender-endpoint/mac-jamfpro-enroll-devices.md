---
title: Zarejestruj Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach z systemem macOS do aplikacji Jamf Pro
description: Zarejestruj Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach z systemem macOS do aplikacji Jamf Pro
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, wdrażanie, dezinstalacja, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6189b61826cd56e2a8652032998c3b2df8f980ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468682"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Zarejestruj Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach z systemem macOS do aplikacji Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

   :::image type="content" source="images/a347307458d6a9bbfa88df7dbe15398f.png" alt-text="Ustawienia konfiguracji1" lightbox="images/a347307458d6a9bbfa88df7dbe15398f.png":::

2. Wybierz **pozycję + Nowy**.

   :::image type="content" source="images/b6c7ad56d50f497c38fc14c1e315456c.png" alt-text="Automatyczne wygenerowanie opisu logo" lightbox="images/b6c7ad56d50f497c38fc14c1e315456c.png":::

3. W **obszarze Określ adresatów dla zaproszenia** > w obszarze Adresy  e-mail wprowadź adresy e-mail adresatów.

    :::image type="content" source="images/718b9d609f9f77c8b13ba88c4c0abe5d.png" alt-text="Ustawienia konfiguracji2" lightbox="images/718b9d609f9f77c8b13ba88c4c0abe5d.png":::

    :::image type="content" source="images/ae3597247b6bc7c5347cf56ab1e820c0.png" alt-text="Ustawienia konfiguracji3" lightbox="images/ae3597247b6bc7c5347cf56ab1e820c0.png":::

    Na przykład: janedoe@contoso.com

    :::image type="content" source="images/4922c0fcdde4c7f73242b13bf5e35c19.png" alt-text="Ustawienia konfiguracji4" lightbox="images/4922c0fcdde4c7f73242b13bf5e35c19.png":::

4. Skonfiguruj wiadomość dla zaproszenia.

   :::image type="content" source="images/ce580aec080512d44a37ff8e82e5c2ac.png" alt-text="Ustawienia konfiguracji5" lightbox="images/ce580aec080512d44a37ff8e82e5c2ac.png":::

   :::image type="content" source="images/5856b765a6ce677caacb130ca36b1a62.png" alt-text="Ustawienia konfiguracji6" lightbox="images/5856b765a6ce677caacb130ca36b1a62.png":::

   :::image type="content" source="images/3ced5383a6be788486d89d407d042f28.png" alt-text="Ustawienia konfiguracji7" lightbox="images/3ced5383a6be788486d89d407d042f28.png":::

   :::image type="content" source="images/54be9c6ed5b24cebe628dc3cd9ca4089.png" alt-text="Ustawienia konfiguracji8" lightbox="images/54be9c6ed5b24cebe628dc3cd9ca4089.png":::

## <a name="enrollment-method-2-prestage-enrollments"></a>Metoda rejestracji 2: rejestracja w przedsprzedażu

1. Na pulpicie nawigacyjnym usługi Jamf Pro przejdź do strony **Rejestracja w przedsprzedażu**.

   :::image type="content" source="images/6fd0cb2bbb0e60a623829c91fd0826ab.png" alt-text="Ustawienia konfiguracji9" lightbox="images/6fd0cb2bbb0e60a623829c91fd0826ab.png":::

2. Postępuj zgodnie z instrukcjami [w tece Rejestracja na komputerze w przedsprzedażu](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Zarejestruj urządzenie z systemem macOS

1. Wybierz **pozycję Kontynuuj** i zainstaluj certyfikat urzędu certyfikacji w **oknie Preferencje** systemowe.

   :::image type="content" source="images/jamfpro-ca-certificate.png" alt-text="The Jamf Pro enrollment1" lightbox="images/jamfpro-ca-certificate.png":::

2. Po zainstalowaniu certyfikatu urzędu certyfikacji wróć do okna przeglądarki i wybierz pozycję **Kontynuuj** i zainstaluj profil MDM.

   :::image type="content" source="images/jamfpro-install-mdm-profile.png" alt-text="Rejestracja do Pro Jamf" lightbox="images/jamfpro-install-mdm-profile.png":::

3. Wybierz **pozycję Zezwalaj** , aby pobierać pliki z jamf.

   :::image type="content" source="images/jamfpro-download.png" alt-text="The Jamf Pro enrollment3" lightbox="images/jamfpro-download.png":::

4. Wybierz **pozycję Kontynuuj** , aby kontynuować instalację profilu MDM.

   :::image type="content" source="images/jamfpro-install-mdm.png" alt-text="Rejestracja do Pro Jamf" lightbox="images/jamfpro-install-mdm.png":::

5. Wybierz **pozycję Kontynuuj** , aby zainstalować profil MDM.

   :::image type="content" source="images/jamfpro-mdm-unverified.png" alt-text="Rejestracja do Pro Jamf" lightbox="images/jamfpro-mdm-unverified.png":::

6. Wybierz **pozycję Kontynuuj**  , aby ukończyć konfigurację.

   :::image type="content" source="images/jamfpro-mdm-profile.png" alt-text="The Jamf Pro enrollment6" lightbox="images/jamfpro-mdm-profile.png":::
