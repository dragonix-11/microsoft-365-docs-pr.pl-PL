---
title: Ustaw datę wygaśnięcia wiadomości e-mail zaszyfrowanych przy użyciu zaawansowanego szyfrowania wiadomości usługi Microsoft Purview
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
description: Zaawansowane szyfrowanie wiadomości usługi Microsoft Purview umożliwia rozszerzenie zabezpieczeń poczty e-mail przez ustawienie daty wygaśnięcia wiadomości e-mail za pośrednictwem niestandardowego szablonu markowego.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 78855ae8906367293b69406ba74246619b5af465
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015567"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>Ustaw datę wygaśnięcia wiadomości e-mail zaszyfrowanych przy użyciu zaawansowanego szyfrowania wiadomości usługi Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview jest zawarte w [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (cennik pracowników organizacji non-profit), Office 365 Enterprise E5 (cennik personelu organizacji non-profit) i Office 365 Education A5. dodatek Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit) lub dodatek Office 365 Advanced Compliance SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit) lub jednostki SKU Office 365.

Jeśli Twoja organizacja ma subskrypcję, która nie obejmuje zaawansowanego szyfrowania komunikatów w usłudze Microsoft Purview, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit) lub dodatek Office 365 Advanced Compliance jednostki SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik pracowników organizacji non-profit) lub jednostek SKU Office 365.

Możesz użyć wygaśnięcia wiadomości w wiadomościach e-mail wysyłanych przez użytkowników do adresatów zewnętrznych, którzy korzystają z portalu OME, aby uzyskać dostęp do zaszyfrowanych wiadomości e-mail. Wymuszasz, aby adresaci używali portalu OME do wyświetlania zaszyfrowanych wiadomości e-mail wysyłanych przez organizację i odpowiadania na nie przy użyciu niestandardowego szablonu oznaczonego marką, który określa datę wygaśnięcia w programie PowerShell.

Jako administrator globalny Office 365, gdy zastosujesz firmową markę w celu dostosowania wyglądu wiadomości e-mail organizacji, możesz również określić wygaśnięcie tych wiadomości e-mail. Zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview umożliwia tworzenie wielu szablonów dla zaszyfrowanych wiadomości e-mail pochodzących z Organizacji. Za pomocą szablonu możesz kontrolować, jak długo adresaci mają dostęp do poczty wysyłanej przez użytkowników.

Gdy użytkownik końcowy otrzyma wiadomość e-mail z ustawioną datą wygaśnięcia, użytkownik zobaczy datę wygaśnięcia w wiadomości e-mail otoki. Jeśli użytkownik spróbuje otworzyć wygasłą wiadomość e-mail, w portalu OME zostanie wyświetlony błąd.

Daty wygaśnięcia wiadomości e-mail można ustawić tylko dla adresatów zewnętrznych.

Dzięki zaawansowanemu szyfrowaniu komunikatów usługi Microsoft Purview za każdym razem, gdy stosujesz znakowanie niestandardowe, Office 365 stosuje otokę do wiadomości e-mail, która pasuje do reguły przepływu poczty, do której stosujesz szablon. Ponadto możesz użyć wygaśnięcia tylko wtedy, gdy używasz znakowania niestandardowego.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Tworzenie niestandardowego szablonu znakowania w celu wymuszenia wygaśnięcia poczty przy użyciu programu PowerShell

1. [Połączenie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) przy użyciu konta z uprawnieniami administratora globalnego w organizacji.

2. Uruchom polecenie cmdlet New-OMEConfiguration.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Gdzie:

- `Identity` to nazwa szablonu niestandardowego.

- `ExternalMailExpiryInDays` określa liczbę dni, przez które adresaci mogą przechowywać pocztę przed jej wygaśnięciem. Można użyć dowolnej wartości z zakresu od 1 do 730 dni.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Więcej informacji na temat zaawansowanego szyfrowania komunikatów w usłudze Microsoft Purview

- [Zaawansowane szyfrowanie komunikatów](ome-advanced-message-encryption.md)

- [Odwołaj wiadomości e-mail zaszyfrowane przy użyciu zaawansowanego szyfrowania wiadomości usługi Microsoft Purview](revoke-ome-encrypted-mail.md)

- [Opis zasad komunikatów i usługi zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
