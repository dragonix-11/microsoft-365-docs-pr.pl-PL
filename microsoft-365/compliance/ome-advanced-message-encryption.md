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
ms.openlocfilehash: a4b970c005b49067e59254ff549200a9118f6cd4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632162"
---
# <a name="advanced-message-encryption"></a>Zaawansowane szyfrowanie komunikatów

Zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview jest zawarte w [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (cennik pracowników organizacji non-profit), Office 365 Enterprise E5 (cennik personelu organizacji non-profit) i Office 365 Education A5. Jeśli Twoja organizacja ma subskrypcję, która nie obejmuje zaawansowanego szyfrowania komunikatów w usłudze Microsoft Purview, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik personelu organizacji non-profit) lub dodatek Office 365 Advanced Compliance jednostki SKU dla Microsoft 365 E3, Microsoft 365 E3 (cennik pracowników organizacji non-profit), jednostek SKU Office 365 lub Information Protection Microsoft 365 E5/A5  i dodatku jednostki SKU ładu dla Microsoft 365 A3/E3.

Zaawansowane szyfrowanie komunikatów pomaga klientom spełnić wymagania dotyczące zgodności, które wymagają bardziej elastycznej kontroli nad adresatami zewnętrznymi i ich dostępu do zaszyfrowanych wiadomości e-mail. Dzięki zaawansowanemu szyfrowaniu komunikatów w Office 365 możesz kontrolować poufne wiadomości e-mail udostępniane poza organizacją przy użyciu zasad automatycznych i śledzić te działania za pośrednictwem zaszyfrowanych dzienników dostępu portalu wiadomości. Te zasady można skonfigurować w celu identyfikowania poufnych typów informacji, takich jak identyfikatory pii, finansowe lub identyfikatory kondycji, lub można użyć słów kluczowych w celu zwiększenia ochrony. Po skonfigurowaniu zasad należy sparować zasady z niestandardowymi szablonami wiadomości e-mail z marką, a następnie dodać datę wygaśnięcia, aby uzyskać dodatkową kontrolę nad wiadomościami e-mail, które pasują do zasad. Ponadto administratorzy mogą dodatkowo kontrolować zaszyfrowane wiadomości e-mail dostępne zewnętrznie za pośrednictwem bezpiecznego portalu internetowego, cofając dostęp do poczty w dowolnym momencie.

Możesz odwołać i ustawić tylko datę wygaśnięcia wiadomości e-mail wysyłanych do adresatów zewnętrznych.

## <a name="get-started-with-microsoft-purview-advanced-message-encryption"></a>Wprowadzenie do zaawansowanego szyfrowania komunikatów w usłudze Microsoft Purview

W poniższych artykułach opisano sposób konfigurowania i używania zaawansowanego szyfrowania komunikatów.

Twoja organizacja musi mieć subskrypcję obejmującą zaawansowane szyfrowanie komunikatów usługi Microsoft Purview. Aby uzyskać szczegółowe informacje na temat obsługiwanych subskrypcji, zobacz [opis zasad komunikatów i usługi zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Jeśli nie skonfigurowano jeszcze Office 365 szyfrowania [komunikatów, zobacz Konfigurowanie nowych funkcji szyfrowania komunikatów Office 365](set-up-new-message-encryption-capabilities.md).

W przypadku zaawansowanego szyfrowania komunikatów nie ograniczasz się do jednego szablonu znakowania. Zamiast tego można tworzyć i używać wielu szablonów znakowania. Dodanie niestandardowego znakowania umożliwia również śledzenie odwołania zaszyfrowanych komunikatów. Aby uzyskać informacje, zobacz [Dodawanie marki organizacji do zaszyfrowanych komunikatów](add-your-organization-brand-to-encrypted-messages.md). W przypadku korzystania z niestandardowego znakowania adresaci zewnętrzni otrzymują wiadomość e-mail z powiadomieniem zawierającym link do portalu OME. Reguła przepływu poczty określa szablon znakowania używany przez wiadomość e-mail z powiadomieniem i portal OME. Dzięki temu bezpieczna zawartość nie jest wysyłana poza organizację.

Komunikaty można odwoływać tylko i stosować daty wygaśnięcia do komunikatów odbierane przez użytkowników za pośrednictwem portalu. Innymi słowy, wiadomość e-mail z zastosowanym niestandardowym szablonem znakowania. Aby uzyskać więcej informacji i przykład, zobacz wskazówki w [temacie Upewnij się, że wszyscy adresaci zewnętrzni używają portalu OME do odczytywania zaszyfrowanej poczty](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Ustaw datę wygaśnięcia wiadomości e-mail zaszyfrowanej przez zaawansowane szyfrowanie komunikatów usługi Microsoft Purview](ome-advanced-expiration.md). Kontrolowanie poufnych wiadomości e-mail udostępnianych poza organizacją przy użyciu automatycznych zasad, które zwiększają ochronę przez wygaśnięcie dostępu za pośrednictwem bezpiecznego portalu internetowego do zaszyfrowanych wiadomości e-mail.

[Odwołaj wiadomość e-mail zaszyfrowaną przez zaawansowane szyfrowanie komunikatów usługi Microsoft Purview](revoke-ome-encrypted-mail.md). Kontrolowanie poufnych wiadomości e-mail udostępnianych poza organizacją i zwiększanie ochrony przez odwołanie dostępu za pośrednictwem bezpiecznego portalu internetowego do zaszyfrowanych wiadomości e-mail.

[Dziennik aktywności zaszyfrowanego portalu komunikatów firmy Microsoft Purview — zaawansowane szyfrowanie komunikatów](ome-message-access-logs.md). Monitorowanie poufnych wiadomości e-mail udostępnianych poza organizacją w zaszyfrowanym portalu wiadomości.
