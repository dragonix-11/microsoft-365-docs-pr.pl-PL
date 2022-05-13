---
title: Zaawansowane szyfrowanie komunikatów
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Zaawansowane szyfrowanie komunikatów pomaga organizacjom spełnić swoje obowiązki w zakresie zgodności, umożliwiając administratorom wykonywanie jeszcze większej liczby chronionych komunikatów.
ms.openlocfilehash: 077a17921c456ddff30e7490611dd4e78aaa5232
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393291"
---
# <a name="advanced-message-encryption"></a>Zaawansowane szyfrowanie komunikatów

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview zaawansowane szyfrowanie komunikatów jest zawarte w [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (cennik pracowników organizacji non-profit), Office 365 Enterprise E5 (Pracownicy organizacji non-profit) Cennik) i Office 365 Education A5. Jeśli Twoja organizacja ma subskrypcję, która nie obejmuje Microsoft Purview zaawansowanego szyfrowania komunikatów, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit), lub dodatek Office 365 Advanced Compliance SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit), jednostki SKU Office 365 lub Microsoft 365 E5/A5 dodatek Information Protection i jednostki SKU ładu dla Microsoft 365 A3/E3.

Zaawansowane szyfrowanie komunikatów pomaga klientom spełnić wymagania dotyczące zgodności, które wymagają bardziej elastycznej kontroli nad adresatami zewnętrznymi i ich dostępu do zaszyfrowanych wiadomości e-mail. Dzięki zaawansowanemu szyfrowaniu komunikatów w Office 365 możesz kontrolować poufne wiadomości e-mail udostępniane poza organizacją przy użyciu zasad automatycznych i śledzić te działania za pośrednictwem zaszyfrowanych dzienników dostępu portalu wiadomości. Te zasady można skonfigurować w celu identyfikowania poufnych typów informacji, takich jak identyfikatory pii, finansowe lub identyfikatory kondycji, lub można użyć słów kluczowych w celu zwiększenia ochrony. Po skonfigurowaniu zasad należy sparować zasady z niestandardowymi szablonami wiadomości e-mail z marką, a następnie dodać datę wygaśnięcia, aby uzyskać dodatkową kontrolę nad wiadomościami e-mail, które pasują do zasad. Ponadto administratorzy mogą dodatkowo kontrolować zaszyfrowane wiadomości e-mail dostępne zewnętrznie za pośrednictwem bezpiecznego portalu internetowego, cofając dostęp do poczty w dowolnym momencie.

Możesz odwołać i ustawić tylko datę wygaśnięcia wiadomości e-mail wysyłanych do adresatów zewnętrznych.

## <a name="get-started-with-microsoft-purview-advanced-message-encryption"></a>Wprowadzenie z zaawansowanym szyfrowaniem komunikatów Microsoft Purview

W poniższych artykułach opisano sposób konfigurowania i używania zaawansowanego szyfrowania komunikatów.

Twoja organizacja musi mieć subskrypcję obejmującą Microsoft Purview zaawansowane szyfrowanie komunikatów. Aby uzyskać szczegółowe informacje na temat obsługiwanych subskrypcji, zobacz [opis zasad komunikatów i usługi zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Jeśli nie skonfigurowano jeszcze Office 365 szyfrowania [komunikatów, zobacz Konfigurowanie nowych funkcji szyfrowania komunikatów Office 365](set-up-new-message-encryption-capabilities.md).

W przypadku zaawansowanego szyfrowania komunikatów nie ograniczasz się do jednego szablonu znakowania. Zamiast tego można tworzyć i używać wielu szablonów znakowania. Dodanie niestandardowego znakowania umożliwia również śledzenie odwołania zaszyfrowanych komunikatów. Aby uzyskać informacje, zobacz [Dodawanie marki organizacji do zaszyfrowanych komunikatów](add-your-organization-brand-to-encrypted-messages.md). W przypadku korzystania z niestandardowego znakowania adresaci zewnętrzni otrzymują wiadomość e-mail z powiadomieniem zawierającym link do portalu OME. Reguła przepływu poczty określa szablon znakowania używany przez wiadomość e-mail z powiadomieniem i portal OME. Dzięki temu bezpieczna zawartość nie jest wysyłana poza organizację.

Komunikaty można odwoływać tylko i stosować daty wygaśnięcia do komunikatów odbierane przez użytkowników za pośrednictwem portalu. Innymi słowy, wiadomość e-mail z zastosowanym niestandardowym szablonem znakowania. Aby uzyskać więcej informacji i przykład, zobacz wskazówki w [temacie Upewnij się, że wszyscy adresaci zewnętrzni używają portalu OME do odczytywania zaszyfrowanej poczty](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Ustaw datę wygaśnięcia wiadomości e-mail zaszyfrowanej przez Microsoft Purview zaawansowane szyfrowanie komunikatów](ome-advanced-expiration.md). Kontrolowanie poufnych wiadomości e-mail udostępnianych poza organizacją przy użyciu automatycznych zasad, które zwiększają ochronę przez wygaśnięcie dostępu za pośrednictwem bezpiecznego portalu internetowego do zaszyfrowanych wiadomości e-mail.

[Odwołaj wiadomość e-mail zaszyfrowaną przez Microsoft Purview zaawansowane szyfrowanie komunikatów](revoke-ome-encrypted-mail.md). Kontrolowanie poufnych wiadomości e-mail udostępnianych poza organizacją i zwiększanie ochrony przez odwołanie dostępu za pośrednictwem bezpiecznego portalu internetowego do zaszyfrowanych wiadomości e-mail.

[Dziennik aktywności zaszyfrowanego portalu wiadomości za pomocą Microsoft Purview zaawansowanego szyfrowania komunikatów](ome-message-access-logs.md). Monitorowanie poufnych wiadomości e-mail udostępnianych poza organizacją w zaszyfrowanym portalu wiadomości.
