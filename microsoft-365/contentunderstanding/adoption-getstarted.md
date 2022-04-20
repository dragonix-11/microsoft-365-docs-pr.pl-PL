---
title: Wprowadzenie wdrażania SharePoint Syntex firmy Microsoft
description: Dowiedz się, jak używać i implementować SharePoint Syntex w organizacji, aby usprawnić procesy biznesowe.
ms.author: chucked
author: chuckedmonson
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
ms.openlocfilehash: 9b11c5077551aad666d565b0f3c077b3e43dc78e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937834"
---
# <a name="get-started-driving-adoption-of-microsoft-sharepoint-syntex"></a>Wprowadzenie wdrażania SharePoint Syntex firmy Microsoft

Inteligentne usługi zawartości dostępne w SharePoint Syntex mają trzy części:

- **Opis zawartości:** Tworzenie modeli sztucznej inteligencji bez kodu w celu klasyfikowania i wyodrębniania informacji z zawartości w celu automatycznego stosowania metadanych do odnajdywania i ponownego używania wiedzy. Dowiedz się więcej o [zrozumieniu zawartości](document-understanding-overview.md).
- **Przetwarzanie zawartości:** Automatyzuj przechwytywanie, pozyskiwanie i kategoryzowanie zawartości oraz usprawnij procesy zorientowane na zawartość przy użyciu Power Automate. Dowiedz się więcej o [przetwarzaniu zawartości](form-processing-overview.md).
- **Zgodność zawartości:** Kontrolowanie zawartości i zarządzanie nią w celu poprawy zabezpieczeń i ładu dzięki integracji z usługą Microsoft Purview Information Protection.

Nowe usługi i możliwości sztucznej inteligencji umożliwiają tworzenie aplikacji do analizy zawartości i klasyfikacji bezpośrednio w przepływie zarządzania zawartością przy użyciu SharePoint Syntex. Istnieją dwa różne sposoby zrozumienia zawartości. Używany typ modelu jest oparty na formacie pliku i przypadku użycia.

| Przetwarzanie formularzy | Omówienie dokumentu |
|:-------|:-------|
| Utworzono na podstawie biblioteki dokumentów. | Utworzona w centrum zawartości, część SharePoint Syntex. |
| Model utworzony w konstruktorze sztucznej inteligencji. | Model utworzony w interfejsie natywnym. |
| Służy do częściowo ustrukturyzowanych formatów plików. | Służy do formatów plików bez struktury. |
| Klasyfikator settable. | Klasyfikator trainable z opcjonalnymi wyodrębniaczami. |
| Ograniczone do jednej biblioteki. | Można zastosować do wielu bibliotek. |
| Trenuj w formacie PDF, JPG, PNG, łącznie 50 MB/500 pp. | Wytrenuj pliki PDF, Office lub e-mail 5–10, w tym negatywne przykłady. |

Aby uzyskać bardziej kompletne porównanie możliwości, zobacz [Różnice między interpretacją dokumentów a modelami przetwarzania formularzy](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identyfikowanie pilotażowych scenariuszy biznesowych do optymalizacji

Aby przygotować się do korzystania z SharePoint Syntex w organizacji, musisz najpierw zrozumieć scenariusze, w których będzie ona przydatna. Element "why" pomaga określić, jaki model będzie potrzebny i jak utworzyć strukturę organizacji w zależności od tego, gdzie model zostanie zastosowany. Oto kilka scenariuszy, w których zrozumienie dokumentów może pomóc twojej organizacji:

- **Przetwarzanie zawartości:** Przetwarzaj kontrakty, instrukcje pracy i inne dokumenty podobne do formularza. Wprowadź formularze, wytrenuj model, aby zrozumieć i zamapować pola, a następnie uruchom formularze, aby automatycznie zbierać dane. Aby uzyskać więcej informacji, zobacz [Omówienie przetwarzania formularzy](form-processing-overview.md).
- **Analiza faktur:** Wyjmij odpowiednie szczegóły z faktur i upewnij się, że są one zgodne z zasadami lub są odpowiednio przetwarzane.

Zastanów się, w jaki sposób SharePoint Syntex może pomóc Twojej organizacji:

- Automatyzowanie procesów biznesowych
- Zwiększanie dokładności wyszukiwania
- Zarządzanie ryzykiem zgodności

Podczas myślenia o tym, które scenariusze biznesowe należy wziąć pod uwagę, zadaj sobie następujące pytania:

- Czy rozwiązuje prawdziwy problem?
- Czy będzie szeroko stosowany, czy będzie miał szeroki wpływ?
- Czy jest to możliwe do uzyskania?
- Czy można zmierzyć sukces?

Określanie priorytetów scenariuszy na podstawie wpływu i łatwości implementacji. Oceń początkowy obszar koncentracji uwagi na scenariuszach o większym wpływie, które można również łatwo zaimplementować. Usuwanie priorytetów scenariuszy o niższym wpływie, które są trudne do zaimplementowania.

Skorzystaj z [przykładowych scenariuszy i przypadków użycia](adoption-scenarios.md), aby wyświetlić pomysły dotyczące sposobu używania SharePoint Syntex w organizacji.

## <a name="identify-roles--responsibilities"></a>Identyfikowanie ról & obowiązków

Określ, kto w organizacji będzie kompilować modele i zarządzać nimi. Mogą być zaangażowane następujące role.

| SharePoint/administrator wiedzy | Administrator platformy Power | Menedżer wiedzy | Właściciel modelu |
|:-------|:-------|:-------|:-------|
| rola AAD| rola AAD | rola AAD | Mistrzów |
| Konfigurowanie przetwarzania formularzy | Konfigurowanie środowiska Dataverse na potrzeby przetwarzania formularzy | Zbieranie przypadków użycia | Zbieranie przypadków użycia biznesowego |
| Zarządzanie centrami zawartości i uprawnieniami| Kupowanie i przydzielanie środków AIB | Ustanawianie najlepszych rozwiązań i przeglądanie analizy modelu | Tworzenie i stosowanie modeli |

Menedżer wiedzy, właściciel procesu biznesowego i właściciel modelu zawartości tworzą przykładowe modeleiee w organizacji.
Inne osoby, które mogą być zaangażowane: administrator zgodności, menedżerowie taksonomii.

Gdzie będą kompilować i stosować modele? Czy istnieją istniejące procesy lub repozytoria, które można ulepszyć?

- Przetwarzanie formularzy: zdecyduj, które lokacje otrzymają akcję przetwarzania formularzy.
- Omówienie dokumentów: możesz utworzyć wiele centrów zawartości dla różnych obszarów biznesowych.

## <a name="strategic-positioning"></a>Pozycjonowanie strategiczne

Współpracuj z osobami biorącymi udział w projekcie, aby upewnić się, że są one zgodne ze strategią używania SharePoint Syntex. Przeprowadź badania i podaj następujące zasoby, które pomogą w tym pozycjonowaniu:

- Wyniki biznesowe:
  - Potencjalne wyniki fiskalne
  - Potencjalne wyniki elastyczności
  - Szablon wyników biznesowych
- Udziałowcy/Exec sponsor buy-in/alignment
  - Prezentacje przypadków biznesowych
  - Modele finansowe
  - Gotowość firmy — kultura

## <a name="identify-stakeholders"></a>Identyfikowanie uczestników projektu

Zidentyfikuj uczestników projektu.

|Rola |Obowiązki |Department |
|:-------|:-------|:--------|
| Sponsorzy wykonawczy   | Przekazywanie firmie wizji i wartości wysokiego poziomu   |  Kierownictwo kadry kierowniczej   |
| Project potencjalnych klientach | Nadzorowanie całego procesu uruchamiania i wdrażania | zarządzanie Project |
| Administratorzy wiedzy| Tworzenie centrów zawartości i zarządzanie nimi | DZIAŁ IT lub inny dział|
| Menedżerowie zawartości i właściciele modeli| Zbieranie przypadków użycia i tworzenie i stosowanie modeli | Dowolny dział|
| Mistrzów | Pomoc w ewangelizacji i zarządzaniu obsługą zastrzeżeń | Dowolny dział (personel) |
| Administrator dzierżawy | Konfigurowanie ustawień na poziomie dzierżawy | Dział IT|
| Administrator platformy Power Platform| Konfigurowanie środowiska Dataverse | Dział IT|

> [!NOTE]
> Mimo że zalecamy spełnienie każdej z tych ról w całym wdrożeniu, może się okazać, że nie wymagasz od nich wszystkich rozpoczęcia pracy z zidentyfikowanym rozwiązaniem.

## <a name="readiness-checklist"></a>Lista kontrolna gotowości

Aby przygotować się do zaimplementowania SharePoint Syntex, należy wykonać następujące czynności:

![Gotowość do zrozumienia zawartości.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planowanie stanu końcowego
    - Modele rozumienia dokumentów to środki, a nie koniec.
    - Zaplanuj wykorzystanie wartości wyodrębnionych metadanych za pomocą:
      - Szukaj
      - Filtrowanie i formatowanie widoku
      - Zgodność
      - Automatyzacji
2. Identyfikacji
    - Omówienie istniejącej architektury informacji i użycia funkcji zarządzania zawartością.
    - Czy istniejące typy zawartości są dobrymi kandydatami do modeli?
    - Jakie istniejące procesy zostałyby ulepszone przez metadane?
3. Design
    - Projektowanie podejścia do architektury informacji, zarządzanych metadanych i typów zawartości.
    - Projektowanie procesu definicji, tworzenia i zarządzania.

## <a name="engage-your-organization"></a>Angażowanie organizacji

1. Identyfikowanie posiadaczy udziałów, potwierdzanie scenariuszy i opracowywanie planu projektu.
1. Skonfiguruj ustawienia i zastosuj licencje.
1. Rozpocznij świadomość i szkolenie — Rekrutuj mistrzów.
1. Wdrażanie etapami.  
1. Zbierz opinie i iteruj.
1. Wraz ze wzrostem użycia planowanie wszelkich środków narzędzia AI Builder w razie potrzeby.

## <a name="see-also"></a>Zobacz też

[Scenariusze i przypadki użycia dla SharePoint Syntex](adoption-scenarios.md)

[Zarządzanie kontraktami przy użyciu rozwiązania Microsoft 365](solution-manage-contracts-in-microsoft-365.md)
