---
title: Obsługa usługi Microsoft Purview dla informacji o wersji zestawu znaków dwubajtowych
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
ms.openlocfilehash: 593e1db04c5e4dc56bc4cc1a7fd11d907d4fe09d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622430"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Obsługa informacji o wersji podwójnego zestawu znaków bajtów

 Usługa Microsoft 365 Information Protection obsługuje teraz języki podwójnego zestawu znaków bajtów dla:

- Chiński (uproszczony)
- Chiński (tradycyjny)
- Korean
- Japanese

Ta obsługa jest dostępna dla typów informacji poufnych i słowników słów kluczowych i zostanie odzwierciedlona w Ochrona przed utratą danych w Microsoft Purview (dla Exchange Online, SharePoint Online, OneDrive dla Firm i Teams), Zgodność z komunikacją, Automatyczne etykietowanie w aplikacje pakietu Office i Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Znane problemy

- Jeśli plik tekstowy dołączony do wiadomości e-mail ma format UTF-8 bez znaku kolejności bajtów (BOM), wiadomość e-mail nie jest wykrywana przez zasady zgodności komunikacji.

- Zasady zgodności komunikacji nie mogą wykrywać wartości, jeśli wprowadzono zdanie dla warunku zasad: "Komunikat zawiera dowolne z tych słów". Jeśli tekst określony w zasadach jest napisany jako słowo, można go wykryć; Jeśli jednak zostanie on zapisany w środku zdania, nie zostanie wykryty.

- Zasady zgodności komunikacji określające słowniki jako informacje o typie nie wykrywają prywatnych czatów i czatów kanałowych usługi Teams.

- Następujące warunki nie są na tym etapie obsługiwane w przypadku zgodności z komunikacją (planujemy rozwiązać te problemy w przyszłości): 
  - "Wiadomość zawiera dowolne z tych słów"
  - "Wiadomość nie zawiera żadnego z tych słów"
  - "Załącznik zawiera dowolne z tych słów"
  - "Załącznik zawiera dowolne z tych słów"

- Zasady ochrony przed utratą danych są wymuszane na urządzeniach z systemem macOS (wersja zapoznawcza) z systemem Catalina 10.15 lub nowszym, z wyjątkiem wymienionych poniżej warunków dla języków wschodnioazjatyckich, w tym języka japońskiego.
  - Nie są wykrywane liczby o pełnej szerokości, takie jak użycie wbudowanego szablonu, takiego jak numer konta bankowego Japonii
  - Liczby bez ograniczników nie są wykrywane
  - Słowa kluczowe oddzielone przestrzenią o połowie szerokości nie są wykrywane dla typu informacji poufnych. Na przykład: wyraz japoński jest ustawiony na typ informacji poufnych, a słownik nie jest wykrywany, jeśli znajduje się w zdaniu
  - Słowa zawierające zarówno angielski, jak i japoński (東京2020) nie są wykrywane

Zamiast tego zalecamy utworzenie niestandardowego typu informacji poufnych (SIT) ze słownikiem słów kluczowych, który wykrywa wzorce w komunikatach i załącznikach, oraz używanie tego niestandardowego interfejsu SIT jako warunku zasad zgodności z komunikacją.
