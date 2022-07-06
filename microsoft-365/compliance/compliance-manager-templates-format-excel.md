---
title: Formatowanie danych szablonu oceny w programie Excel dla programu Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
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
description: Dowiedz się, jak pracować z danymi programu Excel na potrzeby szablonów oceny w programie Microsoft Purview Compliance Manager.
ms.openlocfilehash: 6c94d79fec8ff59419854c34755a7402f841cfe8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631232"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-purview-compliance-manager"></a>Formatowanie danych szablonu oceny w programie Excel dla programu Microsoft Purview Compliance Manager

Podczas [tworzenia](compliance-manager-templates-create.md), [modyfikowania](compliance-manager-templates-modify.md) lub [rozszerzania](compliance-manager-templates-extend.md) szablonów oceny w Menedżerze zgodności będziesz pracować z arkuszami kalkulacyjnymi programu Excel, które używają określonego formatu i schematu. Aby pliki zostały prawidłowo zaimportowane, należy przestrzegać tych specyfikacji.

## <a name="download-example-spreadsheet"></a>Pobierz przykładowy arkusz kalkulacyjny

Aby wyświetlić przykładowy arkusz kalkulacyjny, [pobierz przykładowy plik](https://go.microsoft.com/fwlink/?linkid=2124865). Można go użyć do odwołania do utworzenia własnego pliku.

Jeśli planujesz zmodyfikować istniejący szablon, zacznij od wyświetlenia szczegółów szablonu w Menedżerze zgodności i pobrania pliku programu Excel.

## <a name="spreadsheet-format"></a>Format arkusza kalkulacyjnego

Arkusz kalkulacyjny programu Excel zawiera cztery karty, z których trzy są wymagane:

1. [Szablon](#template-tab) (wymagany)
2. [ControlFamily](#controlfamily-tab) (wymagane)
3. [Akcje](#actions-tab) (wymagane)
4. [Wymiary](#dimensions-tab) (opcjonalnie)

Podczas wypełniania arkusza kalkulacyjnego danymi szablonu arkusz **kalkulacyjny musi zawierać karty w powyższej kolejności, w** przeciwnym razie dane nie zostaną pomyślnie zaimportowane do szablonu.

### <a name="template-tab"></a>Karta Szablon

Karta **Szablon** jest wymagana. Informacje na tej karcie zawierają metadane dotyczące szablonu. Istnieją cztery wymagane kolumny. Kolumny muszą zachować kolejność w arkuszu programu Excel zgodnie z poniższą listą. Możesz dodać własną kolumnę **po** czterech kolumnach, aby zapewnić własne wymiary. Jeśli to zrobisz, dodaj je do karty **Wymiary** .

- **title**: jest to tytuł szablonu, który musi być unikatowy. Nie może udostępnić nazwy innemu szablonowi w Menedżerze zgodności, w tym własnym szablonom lub szablonowi menedżera zgodności.

- **produkt**: jest to wymagany wymiar. Wyświetl listę produktów skojarzonych z szablonem.

- **certyfikacja**: jest to rozporządzenie używane dla szablonu.

- **inScopeServices**: są to usługi w ramach produktu, które są adresowane przez tę ocenę (na przykład jeśli wymieniono Office 365 jako produkt, usługa Microsoft Teams może być usługą w zakresie). Możesz wyświetlić listę wielu usług rozdzielonych dwoma średnikami.

> [!NOTE]
> Danych wstawionych do komórek **produktu** i **certyfikacji** nie można edytować po zaimportowaniu arkusza kalkulacyjnego w celu utworzenia lub dostosowania szablonu. Ponadto grupa nie może zawierać dwóch ocen, które mają tę samą kombinację **produktu/certyfikacji** . Możesz mieć wiele szablonów z tą samą kombinacją produktu/certyfikacji.

### <a name="controlfamily-tab"></a>Karta ControlFamily

Karta **ControlFamily** jest wymagana.  Wymagane kolumny na tej karcie, które muszą być zgodne z kolejnością określoną w przykładowym arkuszu kalkulacyjnym, to:

- **controlName**: jest to nazwa kontrolki z certyfikacji, standardu lub regulacji, która jest zazwyczaj pewnego typu identyfikatorem. Nazwy kontrolek muszą być unikatowe w szablonie. W arkuszu kalkulacyjnym nie można mieć wielu kontrolek o tej samej nazwie.

- **controlFamily**: podaj wyraz lub frazę dla kontrolkiFamily, która identyfikuje szeroką grupę kontrolek. Element controlFamily nie musi być unikatowy; Można go wyświetlić więcej niż raz w arkuszu kalkulacyjnym. Tę samą kontrolkęFamily można również wyświetlić w wielu szablonach, chociaż nie mają one ze sobą żadnego związku. Każda kontrolkaFamilia musi być zamapowana na co najmniej jedną kontrolkę.

- **controlTitle**: podaj tytuł kontrolki. Podczas gdy controlName jest kodem referencyjnym, tytuł jest formatem tekstu sformatowanego, zwykle widocznym w przepisach.

- **controlDescription**: podaj opis kontrolki.

- **controlActionTitle**: to pole wiąże kontrolkę z co najmniej jedną akcją wymienioną przez element actionTitle. Możesz dodać wiele akcji, oddzielając je dwoma średnikami bez odstępu między nimi. Każda lista formantów musi zawierać co najmniej jedną istniejącą akcję, a akcję można zdefiniować na karcie **Akcje** tego samego arkusza kalkulacyjnego, znajdować się w innym szablonie lub zostać utworzona przez firmę Microsoft. Różne kontrolki mogą odwoływać się do tej samej akcji.

### <a name="actions-tab"></a>Karta Akcje

Karta **Akcje** jest wymagana.  Określa on akcje poprawy zarządzane przez organizację, a nie działania firmy Microsoft, które już istnieją w Menedżerze zgodności. Wymagane kolumny dla tej karty, które muszą być zgodne z kolejnością określoną w przykładowym arkuszu kalkulacyjnym, to:

- **actionTitle**: jest to tytuł akcji i jest to pole wymagane. Podany tytuł musi być unikatowy. **Ważne**: jeśli odwołujesz się do akcji, która już istnieje (na przykład w innym szablonie) i zmodyfikujesz dowolny z jej elementów w kolejnych kolumnach, zmiany te zostaną propagowane do tej samej akcji w innych szablonach.

- **implementationType**: W tym wymaganym polu wpisz jeden z następujących trzech typów implementacji: 
  1) **Operacje** — akcje implementowane przez osoby i procesy w celu ochrony poufności, integralności i dostępności systemów organizacyjnych, zasobów, danych i personelu (na przykład: świadomość zabezpieczeń i szkolenia).      
  2) **Techniczne** — akcje wykonywane przy użyciu technologii i mechanizmów zawartych w składnikach sprzętu, oprogramowania lub oprogramowania układowego systemu informacyjnego w celu ochrony poufności, integralności i dostępności systemów organizacyjnych i danych (na przykład: uwierzytelnianie wieloskładnikowe).
  3) **Dokumentacja** — akcje implementowane za pomocą udokumentowanych zasad i procedur ustanawiających i definiujących mechanizmy kontroli wymagane do ochrony poufności, integralności i dostępności systemów organizacyjnych, zasobów, danych i personelu (na przykład: zasady zabezpieczeń informacji).

- **actionScore**: w tym wymaganym polu podaj wartość wyniku liczbowego dla akcji. Wartość musi być liczbą całkowitą w zakresie od 1 do 99; Nie może to być wartość 0, null ani pusta. Im wyższa liczba, tym większa jej wartość w kierunku poprawy stanu zgodności. Na poniższej ilustracji pokazano, jak menedżer zgodności ocenia kontrolki:

  ![Menedżer zgodności kontroluje wartości punktów.](../media/compliance-score-action-scoring.png "Menedżer zgodności kontroluje wartości punktów")

- **actionDescriptionTitle**: jest to tytuł opisu i jest wymagany. Ten tytuł opisu umożliwia wykonanie tej samej akcji w wielu szablonach i wyświetlenie innego opisu w każdym szablonie.  To pole ułatwia wyjaśnienie szablonu, do którego odwołuje się opis. W większości przypadków można umieścić nazwę szablonu, który tworzysz w tym polu.

- **actionDescription**: podaj opis akcji. Można zastosować formatowanie, takie jak pogrubiony tekst i hiperlinki. Jest to pole wymagane.

- **dimension-Action Purpose**: jest to pole opcjonalne. Jeśli ją uwzględnisz, nagłówek musi zawierać prefiks "dimension-". Wszystkie wymiary uwzględnione w tym miejscu będą używane jako filtry w Menedżerze zgodności i wyświetlane na stronie szczegółów akcji poprawy w Menedżerze zgodności.

### <a name="dimensions-tab"></a>Karta Wymiary

Karta **Wymiary** jest opcjonalna. Jeśli jednak odwołujesz się do wymiaru w innym miejscu, musisz określić go tutaj, jeśli nie istnieje on w utworzonym szablonie lub w szablonie firmy Microsoft. Poniżej wymieniono kolumny dla tej karty:

- **dimensionKey**: lista "product", "certifications", "action purpose"
- **dimensionValue**: przykłady: Office 365, HIPPA, Profilaktyczne, Detektyw

Podczas eksportowania istniejącego szablonu wyeksportowany arkusz kalkulacyjny będzie miał kartę **Wymiary** , która zawiera listę wszystkich wymiarów używanych w szablonie.
