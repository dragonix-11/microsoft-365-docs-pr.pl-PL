---
title: Zarządzanie dochodzeniami prawnymi w usłudze Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: Użyj przypadków zbierania elektronicznych materiałów dowodowych w portal zgodności Microsoft Purview, aby zarządzać badaniem prawnym organizacji.
ms.openlocfilehash: 9db3a1e9ad831c74c9468121eaa0800875c74e5a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623810"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Zarządzanie dochodzeniami prawnymi w usłudze Microsoft 365

Organizacje mają wiele powodów, aby odpowiedzieć na sprawę prawną z udziałem niektórych menedżerów lub innych pracowników w organizacji. Może to obejmować szybkie znajdowanie i przechowywanie dalszych informacji specyficznych dla badania w wiadomościach e-mail, dokumentach, konwersacjach wiadomości błyskawicznych i innych lokalizacjach zawartości używanych przez osoby w codziennych zadaniach służbowych. Te i wiele innych podobnych działań można wykonywać przy użyciu narzędzi do zbierania elektronicznych elektronicznych materiałów dowodowych w centrum zabezpieczeń i zgodności.
  
**Chcesz wiedzieć, jak firma Microsoft zarządza badaniami zbierania elektronicznych materiałów dowodowych?** Oto [oficjalny dokument techniczny](https://go.microsoft.com/fwlink/?linkid=852161) , który można pobrać, który wyjaśnia, w jaki sposób używamy tych samych narzędzi do wyszukiwania i badania, aby zarządzać naszym wewnętrznym przepływem pracy zbierania elektronicznych materiałów dowodowych.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Zarządzanie dochodzeniami prawnymi w sprawach zbierania elektronicznych materiałów dowodowych

Przypadki zbierania elektronicznych materiałów dowodowych umożliwiają kontrolowanie, kto może tworzyć i zarządzać przypadkami zbierania elektronicznych materiałów dowodowych w organizacji oraz zarządzać nimi. Przypadki użycia umożliwiają dodawanie członków i kontrolowanie typów akcji, które mogą wykonywać, umieszczanie lokalizacji zawartości istotnych dla sprawy prawnej, a także używanie narzędzia wyszukiwania zawartości do wyszukiwania lokalizacji w miejscu wstrzymania pod kątem zawartości, która może odpowiadać twojej sprawie. Następnie możesz również wyeksportować i pobrać te wyniki w celu dalszego zbadania przez zewnętrznych recenzentów.
  
- [Zarządzaj przepływem pracy zbierania elektronicznych elektronicznych](./get-started-core-ediscovery.md) materiałów dowodowych, tworząc i używając spraw zbierania elektronicznych materiałów dowodowych dla każdego badania prawnego, które musi przeprowadzić organizacja.

- [Przypisz uprawnienia zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md) , aby kontrolować, kto może tworzyć przypadki zbierania elektronicznych materiałów dowodowych i zarządzać nimi w organizacji.

- [Skonfiguruj granice zgodności](set-up-compliance-boundaries.md) , aby kontrolować lokalizacje zawartości użytkownika, które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych.

- [Wyszukaj zawartość](search-for-content.md) w organizacji.

### <a name="use-scripts-for-advanced-scenarios"></a>Używanie skryptów w scenariuszach zaawansowanych

Podobnie jak w poprzedniej sekcji zawierającej skrypty dla scenariuszy wyszukiwania zawartości, utworzyliśmy również niektóre skrypty programu PowerShell dotyczące zabezpieczeń & zgodności, aby ułatwić zarządzanie przypadkami zbierania elektronicznych materiałów dowodowych.
  
- [Utwórz raport zbierania elektronicznych](create-a-report-on-holds-in-ediscovery-cases.md) materiałów dowodowych zawierający informacje o wszystkich blokadach skojarzonych z przypadkami zbierania elektronicznych materiałów dowodowych w organizacji.

- [Dodaj skrzynki pocztowe i lokalizacje usługi OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) dla listy użytkowników do blokady zbierania elektronicznych materiałów dowodowych.
  
## <a name="manage-legal-investigations-with-the-ediscovery-premium-solution-in-microsoft-365"></a>Zarządzanie badaniami prawnymi za pomocą rozwiązania zbierania elektronicznych materiałów dowodowych (Premium) na platformie Microsoft 365

Rozwiązanie Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) na platformie Microsoft 365 bazuje na istniejących funkcjach zbierania elektronicznych materiałów dowodowych i analiz w Office 365. To nowe rozwiązanie o nazwie *eDiscovery (Premium) zapewnia kompleksowy* przepływ pracy do przechowywania, zbierania, przeglądania, analizowania i eksportowania zawartości, która reaguje na wewnętrzne i zewnętrzne badania organizacji. Umożliwia również zespołom prawnym zarządzanie całym przepływem pracy powiadomień o blokadzie prawnej w celu komunikowania się z opiekunami zaangażowanymi w sprawę.

Funkcja zbierania elektronicznych materiałów dowodowych (Premium) wymaga subskrypcji E5 dla organizacji platformy Microsoft 365 lub Office 365. Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Konfigurowanie zbierania elektronicznych materiałów dowodowych (Premium).](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)

Oto krótkie omówienie wbudowanego przepływu pracy w usłudze eDiscovery (Premium). Aby uzyskać więcej informacji, zobacz [Zarządzanie przepływem pracy zbierania elektronicznych materiałów dowodowych (Premium](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)).

- [Utwórz przypadek,](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) aby rozpocząć pracę.

- [Zarządzaj opiekunami](managing-custodians.md) , dodając ich do sprawy i wstrzymując zawartość w skrzynce pocztowej, na koncie usługi OneDrive i w usłudze Microsoft Teams, do której należą.

- [Zarządzaj komunikacją](managing-custodian-communications.md) z opiekunami, automatyzując proces powiadamiania o blokadzie prawnej.

- [Indeksowanie danych opiekuna](processing-data-for-case.md) i naprawianie błędów indeksowania, dzięki czemu można skutecznie zbierać dane na potrzeby badań.

- [Zbierz dane](collecting-data-for-ediscovery.md) dla sprawy i [dodaj je do zestawu przeglądów w celu dalszego](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) zbadania.

- [Wyświetlanie](view-documents-in-review-set.md) dokumentów, [danych zapytań](review-set-search.md) i [elementów tagów](tagging-documents.md) w zestawie przeglądów.

- [Analizowanie danych przypadków](analyzing-data-in-review-set.md) przy użyciu zaawansowanych narzędzi analitycznych.

- [Eksportowanie danych sprawy](exporting-data-ediscover20.md) do przeglądu przez zewnętrznego doradcę.

- [Zarządzanie długotrwałymi zadaniami](managing-jobs-ediscovery20.md) w usłudze eDiscovery (Premium).