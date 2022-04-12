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
description: Zarządzanie urządzeniami z systemem iOS w usłudze Basic Mobility and Security.
ms.openlocfilehash: 99aa909bf9adab1464ad3858cfac4a04cc541609
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781166"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Utwórz certyfikat APN dla urządzeń z systemem iOS

Aby zarządzać urządzeniami z systemem iOS, takimi jak iPady i iPhone w usłudze Basic Mobility and Security, utwórz certyfikat usługi APNs.

1. Zaloguj się do Microsoft 365 przy użyciu konta administratora globalnego.

2. W przeglądarce wpisz <https://protection.office.com/>.

3. Wybierz pozycję **Ochrona przed utratą** \> danych **Zarządzanie urządzeniami** i wybierz pozycję **Certyfikat APNs dla urządzeń z systemem iOS**.

4. Na stronie Apple Push Notification Certificate Ustawienia wybierz pozycję **Dalej**.

5. Wybierz pozycję Pobierz plik CSR i zapisz żądanie podpisania certyfikatu w dowolnym miejscu na komputerze, który zapamiętasz. Wybierz pozycję **Dalej**.

6. Na stronie Tworzenie certyfikatu usługi APNs:

    1. Wybierz pozycję Portal APNS firmy Apple, aby otworzyć portal Apple Push Certificates Portal.

    2. Zaloguj się przy użyciu identyfikatora Apple ID.

       > [!IMPORTANT]
       > Użyj firmowego identyfikatora Apple ID skojarzonego z kontem e-mail, które pozostanie w Twojej organizacji, nawet jeśli użytkownik, który zarządza kontem, opuści konto. Zapisz ten identyfikator, ponieważ musisz użyć tego samego identyfikatora, gdy nadszedł czas na odnowienie certyfikatu.

    3. Wybierz **pozycję Utwórz certyfikat** i zaakceptuj warunki użytkowania.

    4. Przejdź do żądania podpisania certyfikatu pobranego na komputer z Microsoft 365 i wybierz **pozycję Upload**.

       Pobierz na komputer certyfikat apns utworzony przez portal certyfikatów wypychania apple.

       > [!TIP]
       > Jeśli masz problemy z pobraniem certyfikatu, odśwież przeglądarkę.

7. Wstecz do Microsoft 365, a następnie wybierz przycisk **Dalej**, aby przejść do strony **certyfikatu Upload APNS**.

8. Przejdź do certyfikatu APN pobranego z portalu apple push certificates.

9. Wybierz **Zakończ**.

Aby ukończyć konfigurację, wróć do **ustawień** Zarządzanie **urządzeniami** \> **w** \> centrum zabezpieczeń usługi Security & Compliance Center\>.
