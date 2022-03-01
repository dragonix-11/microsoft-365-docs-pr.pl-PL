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
ms.openlocfilehash: e87e88b63bf44c7ea4154fa24c05c0e8e252a446
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006536"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Obsługa dwu bajtowych informacji o wersji zestawu znaków

 Microsoft 365 informacji obsługuje teraz języki zestawu znaków dwu bajtowych dla:

- Chiński (uproszczony)
- Chiński (tradycyjny)
- Korean
- Japanese

Ta obsługa jest dostępna dla typów informacji poufnych i słowników słów kluczowych i będzie odzwierciedlana w zapobieganiu utracie danych (w przypadku usług Exchange Online, SharePoint Online, OneDrive dla Firm i Teams), Zgodności komunikacji, Autoodzysowaniu w aplikacjach pakietu Office i usłudze Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Znane problemy

- Jeśli plik tekstowy dołączony do wiadomości e-mail jest w formacie UTF-8 bez znacznika kolejności bajtów, wiadomość e-mail nie jest wykrywana przez zasady zgodności komunikacji.

- Zasady zgodności komunikacji nie mogą wykryć wartości, jeśli dla warunku zasad zostanie wprowadzone zdanie: "Wiadomość zawiera dowolny z tych wyrazów". Jeśli tekst określony w zasadach jest napisany jako wyraz, można go wykryć. jeśli jednak zostanie on napisany w środku zdania, nie zostanie wykryty.

- Zasady zgodności komunikacji, które określają słowniki jako informacje o typie, nie Teams prywatnych czatów i czatów na kanałach.

- Na tym etapie zgodności z komunikacją nie są obsługiwane następujące warunki (planujemy rozwiązanie tych problemów w przyszłości): 
  - "Wiadomość zawiera dowolny z tych słów"
  - "Wiadomość nie zawiera żadnego z tych wyrazów"
  - "Załącznik zawiera dowolny z tych wyrazów"
  - "Załącznik zawiera dowolny z tych wyrazów"

Zamiast tego zalecamy utworzenie niestandardowego typu informacji poufnych (SIT) przy użyciu słownika słów kluczowych, który wykryje wzorce w wiadomościach i załącznikach, a także użycie tej niestandardowej funkcji SIT jako warunku zasad zgodności komunikacji.
