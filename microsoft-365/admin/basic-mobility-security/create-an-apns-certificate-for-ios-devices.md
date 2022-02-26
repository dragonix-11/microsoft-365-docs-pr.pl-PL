---
title: Tworzenie certyfikatu usługi APN dla urządzeń z systemem iOS
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
description: Zarządzaj urządzeniami z systemem iOS w pakietach Basic Mobility and Security.
ms.openlocfilehash: f2539ac1c27bd63c13766e197fc12fafc3906f07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973647"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Tworzenie certyfikatu usługi APN dla urządzeń z systemem iOS

Aby zarządzać urządzeniami z systemem iOS, takimi jak tablety iPad i telefony iPhone w pakietach Basic Mobility and Security, utwórz certyfikat usługi APN.

1. Zaloguj się Microsoft 365 konta administratora globalnego.

2. Wpisz tekst w przeglądarce <https://protection.office.com/>.

3. Wybierz  **pozycję Zapobieganie utracie**  **danychZarządzajanie** > i wybierz pozycję Certyfikat **usługi APN dla urządzeń z systemem iOS**.

4. Na stronie certyfikatu powiadomień push firmy Apple Ustawienia wybierz  **pozycjęNext**.

5. Wybierz pozycję Pobierz plik CSR i zapisz żądanie podpisania certyfikatu w miejscu na komputerze, które zapamiętasz. Wybierz   **pozycjęNastępny**.

6. Na stronie Tworzenie certyfikatu usługi APN:

    1. Wybierz pozycję Portal Apple APNS, aby otworzyć portal certyfikatów Push firmy Apple.

    2. Zaloguj się przy użyciu identyfikatora Apple ID.

       > [!IMPORTANT]
       > Użyj firmowego identyfikatora Apple skojarzonego z kontem e-mail, który pozostanie w Twojej organizacji, nawet jeśli opuści go użytkownik, który nim zarządza. Zapisz ten identyfikator, ponieważ będzie konieczne użycie tego samego identyfikatora przy odnawianiu certyfikatu.

    3. Wybierz   **pozycjęTwoz certyfikat i**  zaakceptuj warunki użytkowania.

    4. Przejdź do żądania podpisania certyfikatu, które zostało pobrane na komputer z witryny Microsoft 365, a następnie wybierz pozycję **Upload**.

       Pobierz na komputer certyfikat usługi APN utworzony w portalu certyfikatów Push firmy Apple.

       > [!TIP]
       > Jeśli masz problem z pobraniem certyfikatu, odśwież przeglądarkę.

7. Wróć do Microsoft 365 i wybierz pozycję **Dalej** , aby przejść do Upload   **certyfikatu APNS** .

8. Przejdź do certyfikatu usługi APN pobranego z portalu certyfikatów Push firmy Apple.

9. Wybierz   **pozycjęFinisz**.

Aby ukończyć konfigurację, wróć do Centrum & zgodności i > **zabezpieczeńNarządz**  **** >> zarządzanie  **urządzeniami.**
