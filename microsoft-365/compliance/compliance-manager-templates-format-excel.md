---
title: Formatowanie danych szablonu oceny w aplikacji Excel Menedżera zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak pracować z danymi Excel szablonów ocen w menedżerze zgodności firmy Microsoft.
ms.openlocfilehash: 899dd42401bb4c7acceb1db5bfe5816b383ae16b
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2021
ms.locfileid: "62988650"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-compliance-manager"></a>Formatowanie danych szablonu oceny w aplikacji Excel Menedżera zgodności firmy Microsoft

Podczas [tworzenia](compliance-manager-templates-create.md), [modyfikowania](compliance-manager-templates-modify.md) lub rozszerzania szablonów ocen w Menedżerze zgodności będziesz pracować z Excel kalkulacyjnymi, które używają określonego formatu i schematu.[](compliance-manager-templates-extend.md) Aby pliki zostały poprawnie zaimportowane, muszą być one poprawnie zaimportowane.

## <a name="download-example-spreadsheet"></a>Pobierz przykładowy arkusz kalkulacyjny

Aby wyświetlić przykładowy arkusz kalkulacyjny, [pobierz plik przykładowy](https://go.microsoft.com/fwlink/?linkid=2124865). Możesz go użyć w celu utworzenia własnego pliku.

Jeśli zamierzasz zmodyfikować istniejący szablon, zacznij od wyświetlenia szczegółów szablonu w Menedżerze zgodności i pobrania jego Excel pliku.

## <a name="spreadsheet-format"></a>Format arkusza kalkulacyjnego

Arkusz Excel zawiera cztery karty, z których trzy są wymagane:

1. [Szablon](#template-tab) (wymagany)
2. [ControlFamily](#controlfamily-tab) (wymagany)
3. [Akcje](#actions-tab) (wymagane)
4. [Wymiary](#dimensions-tab) (opcjonalnie)

Podczas wypełniania arkusza kalkulacyjnego danymi szablonu arkusz kalkulacyjny musi zawierać karty w kolejności podanej **powyżej**, w przeciwnym razie dane nie będą pomyślnie zaimportowane do szablonu.

### <a name="template-tab"></a>Karta Szablon

Karta **Szablon** jest wymagana. Informacje na tej karcie zawierają metadane dotyczące szablonu. Istnieją cztery kolumny wymagane. Kolumny muszą zachować kolejność w arkuszu Excel zgodnie z poniższymi instrukcjami. Możesz dodać własną kolumnę **po tych** czterech kolumnach, aby zapewnić własne wymiary. W takim przypadku dodaj je do **karty** Wymiary.

- **tytuł**: jest to tytuł szablonu, który musi być unikatowy. Nie można jej udostępnić innym szablonom w Menedżerze zgodności, w tym Własnym szablonom ani szablonowi Menedżera zgodności.

- **produkt**: jest to wymiar wymagany. Schowaj produkt skojarzony z szablonem.

- **certyfikacja**: jest to rozporządzenie, z których korzystasz w szablonie.

- **inScopeServices**: Są to usługi w obrębie produktu, których adresy do oceny (na przykład jeśli wymieniono usługę Office 365 jako produkt, Microsoft Teams może to być usługa w zakresie). Możesz wyświetlić listę wielu usług oddzielonych dwoma średnikami.

> [!NOTE]
> Po zaimportowaniu arkusza kalkulacyjnego  w celu  utworzenia lub dostosowania szablonu nie będzie można edytować danych wstawianych w komórkach produktu i komórek certyfikacji. Ponadto grupa nie może zawierać dwóch ocen, które mają taką samą **kombinację produktu i certyfikacji** . Możesz mieć wiele szablonów z taką samą kombinacją produktu/certyfikacji.

### <a name="controlfamily-tab"></a>ControlFamily tab

**Wymagana jest karta ControlFamily**.  Na tej karcie są wymagane kolumny, które muszą być zgodne z kolejnością podaną w przykładowym arkuszu kalkulacyjnym:

- **nazwa_** kontrolki: jest to nazwa kontrolki na podstawie certyfikatu, standardu lub przepisów, które zwykle są pewnego rodzaju identyfikatorami. Nazwy kontrolek muszą być unikatowe w szablonie. W arkuszu kalkulacyjnym nie można mieć wielu kontrolek o takiej samej nazwie.

- **controlFamily**: Podaj wyraz lub frazę kontrolkiFamily, która identyfikuje grupę kontrolek. KontrolkaFamily nie musi być unikatowa; może być wymieniony w arkuszu kalkulacyjnym więcej niż raz. Ta sama kontrolkaFamily może być również wymieniona w wielu szablonach, chociaż nie mają żadnej relacji między sobą. Każda kontrolkaFamily musi zostać zamapowana na co najmniej jedną kontrolkę.

- **controlTitle**: Podaj tytuł kontrolki. Nazwa kontrolki jest kodem referencyjnym, jednak tytuł jest tekstem sformatowanym zazwyczaj w przepisy.

- **controlDescription**: Podaj opis kontrolki.

- **controlActionTitle**: To pole odnosi kontrolkę do jednej lub większej liczby akcji wymienionych przez jej actionTitle. Możesz dodać wiele akcji, oddzielając je dwoma średnikami bez odstępów między nimi. Każda kontrolka, która zostanie wyświetlona na liście, musi zawierać co najmniej jedną istniejącą akcję,  która może zostać zdefiniowana na karcie Akcje tego samego arkusza kalkulacyjnego, zostać utworzona w innym szablonie lub utworzona przez firmę Microsoft. Różne kontrolki mogą odwoływać się do tej samej akcji.

### <a name="actions-tab"></a>Karta Akcje

Karta **Akcje** jest wymagana.  Oznacza on działania ulepszeń zarządzane przez Twoją organizację, a nie działania firmy Microsoft, które już istnieją w Menedżerze zgodności. Kolumny wymagane dla tej karty, które muszą być zgodne z kolejnością podaną w przykładowym arkuszu kalkulacyjnym, są następujące:

- **actionTitle**: To jest tytuł akcji i jest wymagane pole. Zapewniany tytuł musi być unikatowy. **Ważne**: jeśli odwołujesz się do akcji, która już istnieje (na przykład w innym szablonie), i zmodyfikujesz dowolny z jej elementów w kolejnych kolumnach, zmiany te będą propagowane do tej samej akcji w innych szablonach.

- **implementationType (Typ** implementacji): W tym wymaganym polu wpisz jeden z trzech poniższych typów implementacji:
- **Operacyjne** — działania wdrażane przez osoby i procesy w celu ochrony poufności, integralności oraz dostępności systemów organizacyjnych, zasobów, danych i pracowników (na przykład: informacje i szkolenia dotyczące bezpieczeństwa)
- Techniczne **— działania** zakończone przy użyciu technologii i mechanizmów zawartych w sprzęcie, oprogramowaniu lub składnikach oprogramowania układowego systemu informacyjnego w celu ochrony poufności, integralności oraz dostępności systemów i danych organizacyjnych (na przykład: uwierzytelnianie wieloskładnikowe)
- **Dokumentacja** — działania wdrażane w ramach dokumentowanych zasad i procedur ustanawiania i definiowania kontroli wymaganych do ochrony poufności, integralności oraz dostępności systemów organizacyjnych, zasobów, danych i pracowników (na przykład: zasady zabezpieczeń informacji)

- **actionScore**: W tym wymaganym polu podaj wartość wyniku liczbowego akcji. Wartość musi być liczbą całościową z zakresu od 1 do 99. Nie może mieć wartości 0, null ani pustej. Im wyższa liczba, tym większa wartość w celu poprawy poziomu zgodności z przepisami. Na poniższym obrazie przedstawiono, jak steruje wyniki Menedżera zgodności:

  ![Menedżer zgodności kontroluje wartości punktowe.](../media/compliance-score-action-scoring.png "Menedżer zgodności kontroluje wartości punktowe")

- **actionDescriptionTitle**: Jest to tytuł opisu i jest wymagany. Ten tytuł opisu pozwala na korzystanie z tej samej akcji w wielu szablonach i naniesienie innego opisu w każdym szablonie.  To pole ułatwia wyjaśnienie, do jakiego szablonu odwołuje się opis. W większości przypadków w tym polu można umieścić nazwę szablonu, który tworzysz.

- **actionDescription**: Podaj opis akcji. Możesz zastosować formatowanie, takie jak pogrubienie tekstu i hiperlinki. To jest pole wymagane.

- **cel wymiar-akcja**: to pole opcjonalne. W przypadku jego dojęć nagłówek musi zawierać prefiks "wymiar-". Wszelkie wymiary, które uwzględnisz w tym miejscu, będą używane jako filtry w Menedżerze zgodności i będą widoczne na stronie szczegółów akcji udoskonalania w Menedżerze zgodności.

### <a name="dimensions-tab"></a>Karta Wymiary

Karta **Wymiary jest** opcjonalna. Jeśli jednak odwołujesz się do wymiaru w innym miejscu, musisz go tutaj określić, jeśli nie istnieje w szablonie, który został już utworzony lub w szablonie firmy Microsoft. Kolumny dla tej karty są wymienione poniżej:

- **dimensionKey**: list as "product", "certifications", "action purpose" (Cel akcji)
- **dimensionValue**: examples: Office 365, HIPPA, Preventative, Detective

Podczas eksportowania istniejącego szablonu eksportowany arkusz kalkulacyjny będzie **zawierał kartę** Wymiary, która zawiera listę wszystkich wymiarów używanych w szablonie.
