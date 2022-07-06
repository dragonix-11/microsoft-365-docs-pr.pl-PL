---
title: Omówienie szyfrowania podwójnego klucza i często zadawane pytania
description: Często zadawane pytania dotyczące szyfrowania podwójnym kluczem.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: c42104ccb74aba71b143d1ee31b0ed5893d9396f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641839"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Często zadawane pytania dotyczące podwójnego szyfrowania kluczy

Masz pytanie dotyczące sposobu działania funkcji podwójnego szyfrowania kluczy? Sprawdź odpowiedź tutaj.

## <a name="what-is-double-key-encryption-dke"></a>Co to jest szyfrowanie podwójnym kluczem (DKE)?

Szyfrowanie podwójnym kluczem umożliwia klientom ochronę wysoce poufnych danych w celu spełnienia wyspecjalizowanych wymagań. Ułatwia to zachowanie pełnej kontroli nad kluczami szyfrowania. Używa dwóch kluczy do ochrony danych; jeden klucz w kontrolce i drugi klucz przechowywany bezpiecznie na platformie Microsoft Azure. Wyświetlanie danych chronionych za pomocą szyfrowania podwójnym kluczem wymaga dostępu do obu kluczy. Ponieważ firma Microsoft może uzyskać dostęp tylko do jednego z tych kluczy, chronione dane pozostają niedostępne dla firmy Microsoft, zapewniając pełną kontrolę nad prywatnością i bezpieczeństwem danych.  

Możesz hostować usługę szyfrowania podwójnym kluczem używaną do żądania klucza w wybranej lokalizacji (lokalny serwer zarządzania kluczami lub w chmurze). Usługa jest utrzymywana tak, jak w przypadku każdej innej aplikacji. Szyfrowanie podwójnym kluczem umożliwia kontrolowanie dostępu do usługi podwójnego szyfrowania kluczy. Możesz przechowywać wysoce poufne dane lokalnie lub przenieść je do chmury. Możesz mieć pewność, że uniemożliwisz dostęp innym firmom, ponieważ zachowujesz pełną kontrolę nad kluczem. Podwójne szyfrowanie kluczy umożliwia przechowywanie danych i klucza w tej samej lokalizacji.

DKE pomaga spełnić wymagania prawne w kilku przepisach i standardach, takich jak ogólne rozporządzenie o ochronie danych (RODO), ustawy o przenośności i odpowiedzialności ubezpieczeń zdrowotnych (HIPAA), gramm-Leach-Bliley Act (GLBA), rosyjskiej ustawy o lokalizacji danych – prawo federalne nr. 242-FZ, australijska federalna ustawa o ochronie prywatności z 1988 r. i nowozelandzka ustawa o ochronie prywatności z 1993 r.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Czy mogę używać szyfrowania podwójnym kluczem z wbudowanym etykietowaniem poufności pakietu Microsoft Office?

Aby chronić dokumenty za pomocą szyfrowania podwójnym kluczem, należy użyć klienta ujednoliconego etykietowania usługi Azure Information Protection. Obecnie nie można używać wbudowanego etykietowania poufności pakietu Microsoft Office.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Jakiego Aplikacje Microsoft 365 mogę użyć z funkcją DKE?

Etykiety DKE umożliwiają ochronę dokumentów przy użyciu klasycznych wersji programów Word, Excel i PowerPoint w systemie Windows. Upewnij się, że używasz programu *.12711 lub nowszego (wersje klasyczne programów Word, PowerPoint i Excel) w systemie Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Czym różni się szyfrowanie podwójnego klucza od istniejącego rozwiązania do przechowywania własnego klucza (HYOK)?

Funkcja podwójnego szyfrowania kluczy szyfruje dane za pomocą dwóch kluczy. Klucz szyfrowania znajduje się w twojej kontroli, a drugi klucz jest przechowywany na platformie Microsoft Azure, co umożliwia przenoszenie zaszyfrowanych danych do chmury. Funkcja HYOK chroni zawartość tylko jednym kluczem, a klucz jest zawsze lokalny.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Czy dokumenty z podwójnym kluczem szyfrowane mogą być udostępniane zewnętrznie?

Dokumenty z podwójnym kluczem szyfrowane można udostępniać użytkownikom w osobnej dzierżawie, o ile użytkownicy:

- Uzyskaj wymagane uprawnienie dostępu do klucza w usłudze podwójnego szyfrowania kluczy.

- Uzyskaj wymagane uprawnienie dostępu do klucza na platformie Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Co się dzieje z dokumentami chronionymi za pomocą funkcji HYOK?

Wdrożenie szyfrowania podwójnego klucza nie wpłynie na istniejącą konfigurację rozwiązania HYOK. Zalecamy jednak rozpoczęcie korzystania z szyfrowania podwójnym kluczem równolegle z funkcją HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Czy mogę uruchomić szyfrowanie podwójnym kluczem w środowisku innym niż microsoft air-gapped?

Usługa DKE nie obsługuje tych środowisk, ponieważ usługa wymaga dostępu do platformy Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Gdzie można przechowywać dokumenty zaszyfrowane podwójnym kluczem?

Dokumenty z podwójnym kluczem szyfrowane można przechowywać lokalnie lub w chmurze. W chmurze możesz przenieść zaszyfrowaną zawartość do usługi SharePoint Online i OneDrive dla Firm. Ponieważ firma Microsoft nie ma dostępu do Twojego klucza prywatnego, zaszyfrowane dane pozostają nieprzejrzysty dla firmy Microsoft. Oznacza to również, że nie można wyświetlać zaszyfrowanych dokumentów online w usłudze Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>W jakich regionach i językach jest dostępne podwójne szyfrowanie kluczy? Czy szyfrowanie podwójnym kluczem jest dostępne na całym świecie?

Etykiety DKE są zlokalizowane w tych samych językach, co inne etykiety poufności w Microsoft Purview Information Protection. Szyfrowanie podwójnym kluczem jest dostępne na całym świecie.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Czy można przekonwertować etykietę inną niż DKE na etykietę DKE?

L.p. Nie można dodać funkcji DKE do etykiety po jej utworzeniu. Zamiast tego należy wybrać opcję **Użyj szyfrowania podwójnym kluczem** i podać adres URL usługi Double Key Encryption podczas tworzenia etykiety.

## <a name="how-do-i-roll-my-dke-keys"></a>Jak mogę rzutować klucze DKE?

Aby uzyskać instrukcje dotyczące stopniowania (nazywanego również rotacją lub ponownym kluczem) klucza przechowywanego na platformie Azure, zobacz [Operacje dla klucza dzierżawy usługi Azure Information Protection](/azure/information-protection/operations-customer-managed-tenant-key).

Zobacz [Ustawienia dzierżawy i klucza](double-key-encryption.md#tenant-and-key-settings) , aby uzyskać informacje na temat tworzenia nowego klucza dla usługi DKE.

Podczas tworzenia klucza należy skonfigurować nazwę i identyfikator GUID. Następnie, jeśli obrócisz klucz, zachowasz stary rekord z nazwą i identyfikatorem GUID, ale dodasz nowy rekord o tej samej nazwie, ale z innym identyfikatorem GUID. Nowy klucz zostanie ustawiony jako aktywny, dzięki czemu interfejs API klucza publicznego zacznie zwracać go do nowego szyfrowania. Oba klucze są dostępne do odszyfrowywania, dzięki czemu można odszyfrować nową zawartość i starą zawartość.
