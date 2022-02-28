---
title: 'Wdrożenie usługi Microsoft SharePoint Syntex: wprowadzenie'
description: Dowiedz się, jak używać i wdrażać SharePoint Syntex twojej organizacji, aby pomóc Ci w rozwiązywaniu problemów biznesowych.
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 172c0a681bc8e7c7867e4bcba1c75f94cfc12e60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986311"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Wdrożenie usługi Microsoft SharePoint Syntex: wprowadzenie

Inteligentne usługi zawartości dostępne w programie SharePoint Syntex się z trzema częściami:

- **Zrozumienie zawartości:** Twórz modele bez użycia kodu AI, aby klasyfikować i wyodrębniać informacje z zawartości w celu automatycznego stosowania metadanych w celu odnajdowania wiedzy i ponownego użycia. Dowiedz się więcej o [zrozumieniu zawartości](document-understanding-overview.md).
- **Przetwarzanie zawartości:** Automatyzuj przechwytywanie, wprowadzanie i kategoryzowanie zawartości, aby usprawnić procesy związane z zawartością przy użyciu Power Automate. Dowiedz się więcej o [przetwarzaniu zawartości](form-processing-overview.md).
- **Zgodność zawartości:** Kontrolowanie zawartości i zarządzanie zawartością w celu zwiększenia bezpieczeństwa i zarządzania dzięki integracji z Microsoft Information Protection.

Dzięki nowym usługom i możliwościom AI możesz tworzyć aplikacje do zrozumienia zawartości i klasyfikacji bezpośrednio do przepływu zarządzania zawartością przy użyciu SharePoint Syntex. Istnieją dwa różne sposoby zrozumienia zawartości. Używany typ modelu jest oparty na formacie pliku i przypadku użycia.

| Przetwarzanie formularza | Opis dokumentu |
|:-------|:-------|
| Utworzono z biblioteki dokumentów. | Utworzony w centrum zawartości, część SharePoint Syntex. |
| Model utworzony w konstruktorze AI. | Model utworzony w interfejsie natywnym. |
| Formaty plików pół strukturalne. | Formaty plików bez struktury. |
| Ustawiany klasyfikator tabeli. | Przeszkolny klasyfikator z opcjonalnymi wyodrębniaczami. |
| Ograniczone do jednej biblioteki. | Można stosować je do wielu bibliotek. |
| Szkolenie dotyczące formatu PDF, JPG i PNG o łącznej wartości 50 MB/500 pp. | Szkolenie dotyczące 5–10 plików PDF, Office e-mail, w tym przykładów ujemnych. |

Aby uzyskać pełniejszą porównanie możliwości, zobacz [Różnica między zrozumieniem dokumentu a modelami przetwarzania formularzy](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identyfikowanie pilotażowych scenariuszy biznesowych w celu optymalizacji

Aby przygotować się do korzystania SharePoint Syntex w organizacji, musisz najpierw zrozumieć scenariusze, w których będą one przydatne. Ten "why" pomaga określić, jaki model będzie potrzebny, oraz jak określić strukturę organizacji na podstawie tego, gdzie zostanie zastosowany model. Oto kilka scenariuszy, w których opis dokumentu może pomóc Twojej organizacji:

- **Przetwarzanie zawartości:** Przetwarzaj umowy, zestawienia pracy i inne dokumenty podobne do formularzy. Wywłasz formularze, przeszkolij model w zakresie zrozumienia i mapowania pól, a następnie uruchom formularze w celu automatycznego zbierania danych. Aby uzyskać więcej informacji, zobacz [Omówienie przetwarzania formularzy](form-processing-overview.md).
- **Analiza faktury:** Wyciągaj odpowiednie dane z faktur i upewnij się, że są one zgodne z zasadami lub są odpowiednio przetwarzane.

Zastanów się nad sposobami, które SharePoint Syntex twojej organizacji:

- Automatyzowanie procesów biznesowych
- Poprawa dokładności wyszukiwania
- Zarządzanie ryzykiem zgodności

Zastanawiając się nad scenariuszami biznesowymi do rozważenia, zadaj sobie następujące pytania:

- Czy to rozwiąże rzeczywisty problem?
- Czy będzie on powszechnie używany, czy będzie miał szeroki wpływ?
- Czy można go uzyskać?
- Czy możesz mierzyć sukces?

Określanie priorytetów scenariuszy na podstawie wpływu i łatwości wdrożenia. Nadaj obszarowi początkowej koncentracji scenariusze o wyższym wpływie, które można również łatwo zaimplementować. Określanie priorytetów scenariuszy o niższym wpływie, które trudno wdrożyć.

Skorzystaj z [przykładowych scenariuszy i używaj przypadków,](adoption-scenarios.md) aby wyświetlać pomysły dotyczące sposobu SharePoint Syntex w organizacji.

## <a name="identify-roles--responsibilities"></a>Określanie ról & obowiązków

Określ, kto w Twojej organizacji będzie tworzyć modele i zarządzać nimi. Mogą w to uczestniczyć następujące role.

| SharePoint/Administrator wiedzy | Administrator platformy Power Platform | Menedżer wiedzy | Właściciel modelu |
|:-------|:-------|:-------|:-------|
| AAD rola| AAD rola | AAD rola | Mistrzowie |
| Konfigurowanie przetwarzania formularza | Konfigurowanie środowiska dataverse do przetwarzania formularzy | Zbieranie przypadków użycia | Zbieranie spraw użycia biznesowego |
| Zarządzanie centrami zawartości i uprawnieniami| Kupowanie i przydzielanie środków AIB | Ustanawianie najlepszych rozwiązań i przeglądanie analizy modelu | Tworzenie i stosowanie modeli |

Menedżer wiedzy, właściciel procesu biznesowego i właściciel modelu zawartości tworzą przykładowe modele i wdrożenie mistrza w organizacji.
Inni, którzy mogą być zaangażowani: administrator zgodności, menedżerowie taksonomii.

Gdzie będą tworzyć i stosować modele? Czy istnieją istniejące procesy lub repozytoria, które można by usprawnić?

- Przetwarzanie formularza: Zdecyduj, które witryny otrzymają akcję przetwarzania formularza.
- Opis dokumentu: Możesz utworzyć wiele centrów zawartości dla różnych obszarów biznesowych.

## <a name="strategic-positioning"></a>Pozycjonowanie strategiczne

We współpracy z uczestnikami projektu upewnij się, że są one zgodne ze strategią korzystania z programu SharePoint Syntex. Zbadaj tę pozycję i udostępnij następujące zasoby pomocne w tym zakresie:

- Wyniki biznesowe:
  - Potencjalne wyniki obrachunkowe
  - Potencjalnie elastyczna możliwość zwrotu z projektu
  - Szablon wyników biznesowych
- Uczestników projektu/sponsora Exec, buy-in/alignment
  - Business case decks
  - Modele finansowe
  - Gotowość firmy — kultura

## <a name="identify-stakeholders"></a>Identyfikowanie uczestników projektu

Zidentyfikuj uczestników projektu.

|Rola |Obowiązki |Department |
|:-------|:-------|:--------|
| Sponsorzy z kierownictwa   | Komunikowanie firmy z wartościami i wizją wysokiego poziomu   |  Kierownictwo   |
| Project potencjalnych klienta | Nadzór nad całym procesem uruchamiania i realizacji | Project zarządzania danymi |
| Administratorzy wiedzy| Tworzenie centrów zawartości i zarządzanie nimi | Dział IT lub inny dział|
| Menedżerowie zawartości i właściciele modeli| Zbieranie przypadków użycia oraz tworzenie i stosowanie modeli | Dowolny dział|
| Mistrzowie | Pomoc w pomoc w zarządzaniu niechętną obsługą niechęć | Dowolny dział (personel) |
| Administrator dzierżawy | Konfigurowanie ustawień na poziomie dzierżawy | Dział IT|
| Administrator platformy Power Platform| Konfigurowanie środowiska dataverse | Dział IT|

> [!NOTE]
> Mimo że zalecamy, aby wszystkie te role zostały spełnione w trakcie Twojego realizacji, może się okazać, że nie wymagasz od nich wszystkich, aby rozpocząć pracę nad wskazanym rozwiązaniem.

## <a name="readiness-checklist"></a>Lista kontrolna gotowości

Aby przygotować się do wdrożenia SharePoint Syntex, musisz:

![Gotowość do zrozumienia zawartości.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planowanie stanu końcowego
    - Opis modeli dokumentów to znaczenie, a nie koniec.
    - Zaplanuj wykorzystanie wartości wyodrębniowanych metadanych za pomocą:
      - Wyszukiwanie
      - Filtrowanie i wyświetlanie formatowania
      - Zgodność
      - Automatyzacja
2. Identyfikowanie
    - Zrozumienie istniejącej architektury informacji i używania funkcji zarządzania zawartością.
    - Czy jakieś istniejące typy zawartości dobrze się kandydują do modeli?
    - Jakie istniejące procesy można ulepszyć za pomocą metadanych?
3. Design
    - Zaprojektuj swoje podejście do architektury informacji, zarządzanych metadanych i typów zawartości.
    - Zaprojektuj proces definiowania, tworzenia i zarządzania.

## <a name="engage-your-organization"></a>Angażowanie organizacji

1. Zidentyfikuj schoweki, potwierdź scenariusze i opracuj plan projektu.
1. Konfigurowanie ustawień i stosowanie licencji.
1. Rozpocznij świadomość i szkolenia — Zwerybuj mistrzów.
1. Rozsyłaj je etapami.  
1. Zbierz opinie i iteracyjnie.
1. Wraz ze wzrostem użycia planu dla wszystkich środków na korzystanie z aplikacji AI Builder w razie potrzeby.

## <a name="see-also"></a>Zobacz też

[Scenariusze i przypadki użycia na SharePoint Syntex](adoption-scenarios.md)

[Zarządzanie umowami przy użyciu Microsoft 365 rozwiązania](solution-manage-contracts-in-microsoft-365.md)
