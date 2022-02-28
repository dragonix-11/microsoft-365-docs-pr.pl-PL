---
title: Ustawianie daty wygaśnięcia zaszyfrowanej wiadomości e-mail przez Zaawansowane szyfrowanie wiadomości usługi Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Użyj Zaawansowane szyfrowanie wiadomości usługi Office 365, aby zwiększyć bezpieczeństwo poczty e-mail, ustawiając datę wygaśnięcia w wiadomościach e-mail za pomocą niestandardowego, markowego szablonu.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1213ecf48ee9bd2e04accdd13aaf3ecd74d3faba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983166"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>Ustawianie daty wygaśnięcia zaszyfrowanej wiadomości e-mail przez Zaawansowane szyfrowanie wiadomości usługi Office 365

Zaawansowane szyfrowanie wiadomości usługi Office 365 jest zawarta w usługach [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5 i Microsoft 365 E5 (Nonprofit Staff Pricing), Office 365 Enterprise E5 (Nonprofit Staff Pricing) i Office 365 Education A5. Jeśli Twoja organizacja ma subskrypcję, która nie zawiera subskrypcji usługi Zaawansowane szyfrowanie wiadomości usługi Office 365, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing) lub dodatek jednostki SKU usługi Office 365 Advanced Compliance dla produktów Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing) lub Office 365 jednostki SKU.

Funkcji wygasania wiadomości e-mail wysyłanych przez użytkowników do adresatów zewnętrznych, którzy korzystają z portalu OME w celu uzyskiwania dostępu do zaszyfrowanych wiadomości e-mail. Wymuszasz, aby adresaci używali portalu OME do wyświetlania zaszyfrowanych wiadomości e-mail wysłanych przez Twoją organizację i odpowiadania na nie przy użyciu niestandardowego, markowego szablonu, który określa datę wygaśnięcia w Windows PowerShell.

Jeśli jesteś Office 365 globalnym, gdy zastosujemy markę firmy w celu dostosowania wyglądu wiadomości e-mail organizacji, możesz także określić datę wygaśnięcia tych wiadomości e-mail. Dzięki Zaawansowane szyfrowanie wiadomości usługi Office 365 możesz utworzyć wiele szablonów zaszyfrowanych wiadomości e-mail pochodzących z Twojej organizacji. Za pomocą szablonu możesz określić, jak długo adresaci mają dostęp do poczty wysyłanej przez użytkowników.

Gdy użytkownik końcowy otrzyma wiadomość e-mail z ustawioną datą wygaśnięcia, w wiadomości e-mail zawijaowej będzie ona widzieć datę wygaśnięcia. Jeśli użytkownik spróbuje otworzyć wygasłą pocztę, w portalu OME zostanie wyświetlony komunikat o błędzie.

Daty wygaśnięcia wiadomości e-mail można ustawić tylko dla adresatów zewnętrznych.

Przy Zaawansowane szyfrowanie wiadomości usługi Office 365, gdy tylko zastosujemy znakowanie niestandardowe, etykieta Office 365 do wiadomości e-mail, która pasuje do reguły przepływu poczty, do której stosujesz szablon. Ponadto z wygasania można korzystać tylko w przypadku użycia niestandardowych  brandingów.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Tworzenie niestandardowego szablonu  brandingu w celu wymusania wygaśnięcia poczty przy użyciu programu PowerShell

1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) przy użyciu konta z uprawnieniami administratora globalnego w Twojej organizacji.

2. Uruchom New-OMEConfiguration cmdlet.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Gdzie:

- `Identity` to nazwa szablonu niestandardowego.

- `ExternalMailExpiryInDays` określa liczbę dni, przez które adresaci mogą przechowywać pocztę przed jej wygaśnięciem. Możesz użyć dowolnej wartości od 1 do 730 dni.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Więcej informacji na temat Zaawansowane szyfrowanie wiadomości usługi Office 365

- [Zaawansowane szyfrowanie wiadomości usługi Office 365](ome-advanced-message-encryption.md)

- [Odwołaj wiadomości e-mail zaszyfrowane za pomocą Zaawansowane szyfrowanie wiadomości usługi Office 365](revoke-ome-encrypted-mail.md)

- [Opis usługi zgodności i zasad dotyczących wiadomości](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)