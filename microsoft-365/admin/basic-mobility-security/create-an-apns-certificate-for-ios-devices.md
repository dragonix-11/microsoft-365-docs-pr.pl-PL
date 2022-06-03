---
title: Utwórz certyfikat APN dla urządzeń z systemem iOS
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
description: Aby zarządzać urządzeniami iOS, takimi jak iPady i iPhone w usłudze Basic Mobility and Security, rozpocznij od utworzenia certyfikatu usługi APNs.
ms.openlocfilehash: 10d2e8412cfecf3627c7520123592b371bf01fdb
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863527"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Utwórz certyfikat APN dla urządzeń z systemem iOS

Aby zarządzać urządzeniami iOS, takimi jak iPady i iPhone w usłudze Basic Mobility and Security, utwórz certyfikat usługi APNs.

1. Zaloguj się do Microsoft 365 przy użyciu konta administratora globalnego.

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://portal.office.com/adminportal/home?#/MifoDevices) i wybierz pozycję **Certyfikat usługi APNs dla iOS**.

1. Na stronie Apple Push Notification Certificate Ustawienia wybierz pozycję **Dalej**.

1. Wybierz pozycję Pobierz plik CSR i zapisz żądanie podpisania certyfikatu w dowolnym miejscu na komputerze, który zapamiętasz. Wybierz pozycję **Dalej**.

1. Na stronie Tworzenie certyfikatu usługi APNs:

    1. Wybierz pozycję Portal APNS firmy Apple, aby otworzyć portal Apple Push Certificates Portal.

    2. Zaloguj się przy użyciu identyfikatora Apple ID.

       > [!IMPORTANT]
       > Użyj firmowego identyfikatora Apple ID skojarzonego z kontem e-mail, które pozostanie w Twojej organizacji, nawet jeśli użytkownik, który zarządza kontem, opuści konto. Zapisz ten identyfikator, ponieważ musisz użyć tego samego identyfikatora, gdy nadszedł czas na odnowienie certyfikatu.

    3. Wybierz **pozycję Utwórz certyfikat** i zaakceptuj warunki użytkowania.

    4. Przejdź do żądania podpisania certyfikatu pobranego na komputer z Microsoft 365 i wybierz pozycję **Przekaż**.

       Pobierz na komputer certyfikat apns utworzony przez portal certyfikatów wypychania apple.

       > [!TIP]
       > Jeśli masz problemy z pobraniem certyfikatu, odśwież przeglądarkę.

1. Wstecz do Microsoft 365, a następnie wybierz przycisk **Dalej**, aby przejść do strony **Przekazywanie certyfikatu APNS**.

1. Przejdź do certyfikatu APN pobranego z portalu apple push certificates.

1. Wybierz **Zakończ**.

Aby ukończyć konfigurację, wróć do **ustawień** Zarządzanie **urządzeniami** \> **w** \> centrum zabezpieczeń usługi Security & Compliance Center\>.
