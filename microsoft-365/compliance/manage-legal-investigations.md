---
title: Zarządzanie dochodzeniami prawnie w Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Spraw zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365, aby zarządzać dochodzeniami prawnie organizacji.
ms.openlocfilehash: fc4e89645ef1912c33ab89ec190c87dc9c8a8965
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985107"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Zarządzanie dochodzeniami prawnie w Microsoft 365

Organizacje mają wiele powodów, dla których należy reagować na postępowania prawne obejmujące określonych kierowników lub innych pracowników w organizacji. Może to obejmować szybkie znajdowanie i zachowywanie dalszych informacji specyficznych dla badania w wiadomościach e-mail, dokumentach, konwersacjach za pomocą wiadomości błyskawicznych i innych lokalizacjach zawartości używanych przez osoby w ich zadaniach służbowych. Te i wiele innych podobnych czynności można wykonywać za pomocą narzędzi do zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń i zgodności.
  
**Chcesz wiedzieć, jak firma Microsoft zarządza badaniami zbierania elektronicznych materiałów dowodowych?** Oto oficjalny dokument techniczny[](https://go.microsoft.com/fwlink/?linkid=852161), który możesz pobrać, który opisuje sposób, w jaki używamy tych samych narzędzi wyszukiwania i analizy do zarządzania naszym wewnętrznym przepływem pracy zbierania elektronicznych materiałów dowodowych.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Zarządzanie dochodzeniami prawnie za pomocą spraw zbierania elektronicznych materiałów dowodowych

Sprawy zbierania elektronicznych materiałów dowodowych pozwalają kontrolować, kto może tworzyć sprawy zbierania elektronicznych materiałów dowodowych, uzyskać do nich dostęp i zarządzać nimi w organizacji. Za pomocą spraw można dodawać członków i kontrolować, jakie typy akcji mogą wykonywać, stosować lokalizacje zawartości związane z danym sądem, a także przeszukiwać w lokalizacjach wstrzymywanych zawartość, która może odpowiadać na dane sprawy. Następnie możesz również wyeksportować i pobrać te wyniki do dalszego badania przez recenzentów zewnętrznych.
  
- [Zarządzaj przepływem pracy zbierania](./get-started-core-ediscovery.md) elektronicznych materiałów dowodowych, tworząc i używając spraw zbierania elektronicznych materiałów dowodowych dla każdego dochodzenia prawnego, które musi podjąć Twoja organizacja.

- [Przypisywanie uprawnień zbierania elektronicznych](assign-ediscovery-permissions.md) materiałów dowodowych w celu kontrolowania, kto może tworzyć sprawy zbierania elektronicznych materiałów dowodowych i zarządzać nimi w Organizacji.

- [Skonfiguruj granice zgodności w celu](set-up-compliance-boundaries.md) kontrolowania lokalizacji zawartości użytkowników, które mogą wyszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych.

- [Wyszukaj zawartość w](search-for-content.md) swojej organizacji.

### <a name="use-scripts-for-advanced-scenarios"></a>Używanie skryptów w zaawansowanych scenariuszach

Podobnie jak w poprzedniej sekcji, która zawierała listę skryptów dla scenariuszy wyszukiwania zawartości, utworzono również kilka skryptów programu PowerShell centrum zabezpieczeń i zgodności usługi &, które ułatwiają zarządzanie sprawami zbierania elektronicznych materiałów dowodowych.
  
- [Utwórz raport zbierania elektronicznych materiałów](create-a-report-on-holds-in-ediscovery-cases.md) dowodowych zawierający informacje o wszystkich zbieraniach elektronicznych materiałów dowodowych skojarzonych ze sprawami zbierania elektronicznych materiałów dowodowych w organizacji.

- [Dodaj skrzynki pocztowe i OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) lokalizacji na listę użytkowników do przechowywania zbierania elektronicznych materiałów dowodowych.
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>Zarządzanie dochodzeniami prawnie za pomocą Advanced eDiscovery w programie Microsoft 365

Rozwiązanie Advanced eDiscovery w programie Microsoft 365 na podstawie istniejących funkcji zbierania elektronicznych materiałów dowodowych i analizy w Office 365. To nowe rozwiązanie, nazywane *Advanced eDiscovery*, zapewnia szczegółowe przepływy pracy do zachowywania, zbierania, przeglądania, analizowania i eksportowania zawartości, która odpowiada wewnętrznym i zewnętrznym analizom Twojej organizacji. Umożliwia także zespołom prawnym zarządzanie całym przepływem pracy z powiadomieniem o zerowym zrzeka się w celu skomunikowania się z opiekunami zaangażowanymi w sprawę.

Advanced eDiscovery subskrypcji E5 dla Twojej organizacji Microsoft 365 lub Office 365 E5. Aby uzyskać więcej informacji na temat licencjonowania, [zobacz Konfigurowanie Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Oto krótki przegląd wbudowanego przepływu pracy w aplikacji Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz [Zarządzanie przepływem Advanced eDiscovery przepływu pracy](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow).

- [Utwórz sprawę,](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) aby rozpocząć.

- [Zarządzaj przechowywaniami](managing-custodians.md) przez dodanie ich do sprawy i umieszczenie zawartości w ich skrzynkach pocztowych, OneDrive Microsoft Teams kontach i dodawanie do nich elementów, do których są członkami.

- [Zarządzaj komunikacją](managing-custodian-communications.md) z użytkownikami, automatyzując proces powiadamiania o zmowie prawnej.

- [Indeksowanie danych adresowanych](processing-data-for-case.md) i naprawianie błędów indeksowania w celu efektywnego zbierania danych na własne badania.

- [Zbierz dane](collecting-data-for-ediscovery.md) dotyczące sprawy i dodaj je do [zestawu recenzji do](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) dalszego badania.

- [Wyświetlanie](view-documents-in-review-set.md) dokumentów, [danych](review-set-search.md) zapytań i [tagowanie](tagging-documents.md) elementów w zestawie recenzji.

- [Analizowanie danych dotyczących sprawy](analyzing-data-in-review-set.md) za pomocą zaawansowanych narzędzi do analizy.

- [Eksportuj dane sprawy do](exporting-data-ediscover20.md) przejrzenia przez doradcę zewnętrznego.

- [Zarządzanie długo działających zadań w](managing-jobs-ediscovery20.md) programie Advanced eDiscovery.