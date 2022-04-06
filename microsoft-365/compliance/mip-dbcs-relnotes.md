---
title: Microsoft 365 zgodności dla dwu bajtowych informacji o wersji zestawu znaków
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Informacje o wersji dotyczące obsługi zestawów znaków dwu bajtowych.
ms.openlocfilehash: 2de0e67c78ac558f4bdc2648790e49fad86e3178
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595064"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Obsługa dwu bajtowych informacji o wersji zestawu znaków

 Microsoft 365 Information Protection obsługuje teraz języki zestawu znaków dwu bajtowych dla:

- Chiński (uproszczony)
- Chiński (tradycyjny)
- Korean
- Japanese

Ta obsługa jest dostępna dla typów informacji poufnych i słowników słów kluczowych i będzie odzwierciedlana w zapobieganie utracie danych (w przypadku usług Exchange Online, SharePoint Online, OneDrive dla Firm i Teams), Zgodności z komunikacją, Automatyczne etykiety w aplikacjach pakietu Office oraz Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Znane problemy

- Jeśli plik tekstowy dołączony do wiadomości e-mail jest w formacie UTF-8 bez znacznika kolejności bajtowej, wiadomość e-mail nie jest wykrywana przez zasady zgodności komunikacji.

- Zasady zgodności komunikacji nie mogą wykrywać wartości, jeśli wprowadzono zdanie dla warunku zasad: "Wiadomość zawiera dowolny z tych wyrazów". Jeśli tekst określony w zasadach jest napisany jako wyraz, można go wykryć. jednak jeśli zostanie on napisany w środku zdania, nie zostanie wykryty.

- Zasady zgodności komunikacji określające słowniki jako informacje o typie nie wykryją Teams prywatnych czatów i czatów kanałów.

- Na tym etapie zgodności z komunikacją nie są obsługiwane następujące warunki (planujemy rozwiązanie tych problemów w przyszłości): 
  - "Wiadomość zawiera dowolny z tych słów"
  - "Wiadomość nie zawiera żadnego z tych wyrazów"
  - "Załącznik zawiera dowolny z tych wyrazów"
  - "Załącznik zawiera dowolny z tych wyrazów"

- Zasady ochrony przed utratą danych można wymusić na urządzeniach z systemem macOS (wersja Preview) z systemem Catalina 10.15 lub wyższymi wersjami, z wyjątkiem wymienionych poniżej warunków dla języków wschodnioazjatyckich, w tym dla języka japońskiego.
  - Numery o pełnej szerokości nie są wykrywane, na przykład użycie wbudowanego szablonu, takiego jak japoński numer konta bankowego
  - Nie są wykrywane liczby bez ograniczników
  - Słowa kluczowe rozdzielone połówkową szerokością nie są wykrywane w przypadku poufnego typu informacji. Na przykład: Dla wyrazu japońskiego ustawiono typ informacji poufnych, a słownik nie jest wykrywany, jeśli został on w zdaniu
  - Nie są wykrywane wyrazy zawierające zarówno wyrazy angielskie, jak i japońskie (ode mnie2020).

Zamiast tego zalecamy utworzenie niestandardowego typu informacji poufnych (SIT) przy użyciu słownika słów kluczowych, który wykryje wzorce w wiadomościach i załącznikach, a także użycie tej niestandardowej funkcji SIT jako warunku zasad zgodności komunikacji.
