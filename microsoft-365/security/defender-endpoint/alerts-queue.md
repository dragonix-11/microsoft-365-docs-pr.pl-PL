---
title: Wyświetlanie i organizowanie kolejki alertów programu Microsoft Defender dla punktu końcowego
description: Dowiedz się, jak działają kolejki alertów programu Microsoft Defender dla punktu końcowego oraz jak sortować i filtrować listy alertów.
keywords: alerty, kolejki, alerty w kolejce, sortowanie, porządek, filtrowanie, zarządzanie alertami, nowy, w toku, rozwiązany, najnowszy, czas w kolejce, ważność, okres, alerty ekspertów ds. zagrożeń firmy Microsoft
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: b4606eb25f2cea9c18db8c13beba0e107d0e7950
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62973980"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Wyświetlanie i organizowanie kolejki alertów programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

W **kolejce alertów** jest wyświetlona lista alertów oflagowanych przez urządzenia w Twojej sieci. Domyślnie w widoku pogruponym w kolejce są wyświetlane alerty z ostatnich 30 dni. Najnowsze alerty są wyświetlane u góry listy, co ułatwia wyświetlanie najnowszych alertów w pierwszej kolejności.

> [!NOTE]
> Kolejka alertów jest znacznie zmniejszona dzięki zautomatyzowanym narzędziom do badania i rozwiązywania problemów, dzięki czemu eksperci w zakresie operacji zabezpieczeń mogą skoncentrować się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. Jeśli alert zawiera obsługiwaną jednostkę do automatycznego badania (na przykład pliku) na urządzeniu z obsługiwanym systemem operacyjnym dla tego urządzenia, można uruchomić automatyczne badanie i rozwiązywanie problemów. Aby uzyskać więcej informacji na temat zautomatyzowanych badań, zobacz [Omówienie zautomatyzowanych badań](automated-investigations.md).

Istnieje kilka opcji, które można wybrać, aby dostosować widok kolejki alertów.

W górnym okienku nawigacji możesz:

- Wybieranie widoku grupowego lub widoku listy
- Dostosowywanie kolumn w celu dodania lub usunięcia kolumn
- Wybieranie elementów do pokazania na stronie
- Nawigowanie między stronami
- Stosowanie filtrów

![Obraz kolejki alertów.](images/alerts-queue-list.png)

## <a name="sort-filter-and-group-the-alerts-queue"></a>Sortowanie, filtrowanie i grupowanie alertów w kolejce

Aby ograniczyć listę alertów i uzyskać bardziej skoncentrowany widok alertów, możesz zastosować następujące filtry.

### <a name="severity"></a>Ważność

Ważność alertu|Opis
---|---
High (Wysoki) <br> (Czerwony)|Alerty często spotykane z zaawansowanymi trwałymi zagrożeniami (MZ). Alerty te oznaczają duże ryzyko ze względu na poważne szkody, które mogą one spowodować na urządzeniach. Przykłady: działania związane z narzędziami do kradzieży poświadczeń, działania oprogramowania wymuszającego okup nieskojarzone z żadnymi grupami, manipulowanie czujnikiem zabezpieczeń lub złośliwą aktywnością osoby adversary.
Średni <br> (Orange)|Alerty wykrywanie i reagowanie w punktach końcowych dotyczące zachowań po naruszeniu zabezpieczeń, które mogą stanowić część zaawansowanego zagrożenia trwałego (MZ). Należą do nich obserwowane zachowania typowe dla etapów ataków, nietypowych zmian rejestru, wykonywania podejrzanych plików i tak dalej. Niektóre z nich mogą być częścią wewnętrznych testów zabezpieczeń, ale wymagają badania, ponieważ mogą być także częścią zaawansowanego ataku.
Niska <br> (Żółty)|Alerty dotyczące zagrożeń związanych z rozpowszechnionym złośliwym oprogramowaniem. Na przykład narzędzia do łamania zabezpieczeń, narzędzia do łamania innych niż złośliwe oprogramowanie, takie jak uruchamianie poleceń eksploracji, czyszczenie dzienników itp., które często nie wskazują zaawansowanego zagrożenia skierowanego do organizacji. Może to być również na przykład wyizolowane narzędzie testowane przez użytkownika w organizacji.
Informacyjne <br> (Szary)|Alerty, które nie mogą być uznawane za niebezpieczne dla sieci, ale mogą zwiększyć świadomość bezpieczeństwa organizacji w sprawie potencjalnych problemów z zabezpieczeniami.

#### <a name="understanding-alert-severity"></a>Opis ważności alertów

Program antywirusowy Microsoft Defender (Microsoft Defender AV) i Defender for Endpoint alert severities are different because they represent different scopes.

Istotność Program antywirusowy Microsoft Defender zagrożenia oznacza bezwzględną ważność wykrytego zagrożenia (złośliwego oprogramowania) i jest przypisywana na podstawie potencjalnego ryzyka dla poszczególnych urządzeń, jeśli zostały zainfekowane.

Ważność alertu programu Defender dla punktu końcowego oznacza powagę wykrytego zachowania, rzeczywiste ryzyko dla urządzenia, ale, co ważniejsze, potencjalne ryzyko dla organizacji.

Na przykład:

- Ważność alertu programu Defender dla punktu końcowego o Program antywirusowy Microsoft Defender wykryła zagrożenie, które było całkowicie niemożliwe i nie infekowała urządzenia, jest kategoryzowana jako "informacyjna", ponieważ nie było żadnych rzeczywistych szkód.
- Alert o komercyjnym złośliwym oprogramowaniu został wykryty podczas wykonywania, ale zablokowany i naprawiony przez program Microsoft Defender AV, jest kategoryzowany jako "Niski", ponieważ mógł spowodować uszkodzenie poszczególnych urządzeń, ale nie stwarza zagrożenia organizacyjnego.
- Alert o wykryciu złośliwego oprogramowania podczas wykonywania, które może stanowić zagrożenie nie tylko dla pojedynczego urządzenia, ale również dla organizacji, niezależnie od tego, czy zostało później zablokowane, może zostać sklasyfikowane jako "Średni" lub "Wysoki".
- Podejrzane alerty o zachowaniu, które nie zostały zablokowane ani usunięte, zostaną sklasyfikowane jako "Niskie", "Średnie" lub "Wysokie" po uwzględnieniu tych samych kwestii zagrożenia organizacyjnego.

#### <a name="understanding-alert-categories"></a>Opis kategorii alertów

Ponownie zdefiniowaliśmy kategorie alertów w celu dostosowania ich do [](https://attack.mitre.org/tactics/enterprise/) taktyki ataków w przedsiębiorstwie w macierzy [MITRE ATT&CK](https://attack.mitre.org/). Nowe nazwy kategorii są stosowane do wszystkich nowych alertów. Istniejące alerty zachowają nazwy poprzednich kategorii.

W poniższej tabeli wymieniono bieżące kategorie oraz sposób ich mapowania na poprzednie kategorie.

|Nowa kategoria|Nazwa kategorii interfejsu API|Wykryto aktywność lub składnik zagrożeń|
|---|---|---|
|Kolekcja|Kolekcja|Lokalizowanie i zbieranie danych na ich przykłady.|
|Polecenie i kontrolka|CommandAndControl|Nawiązywanie połączenia z infrastrukturą sieciową kontrolowaną przez atakującego w celu przekazywania danych lub odbierania poleceń.|
|Dostęp poświadczeń|CredentialAccess|Uzyskiwanie prawidłowych poświadczeń w celu rozszerzenia kontroli nad urządzeniami i innymi zasobami w sieci.|
|Obrona|DefenseEvasion|Unikaj kontroli zabezpieczeń, na przykład wyłączając aplikacje zabezpieczające, usuwając programy i uruchamiając programy typu rootkit.|
|Odnajdowanie|Odnajdowanie|Zbieranie informacji o ważnych urządzeniach i zasobach, takich jak komputery administratora, kontrolery domen i serwery plików.|
|Wykonywanie|Wykonywanie|Uruchamianie narzędzi dla atakujących i złośliwego kodu, w tym RAT i backdoorów.|
|Ex przeocły|Ex przeocły|Wyodrębnianie danych z sieci do zewnętrznej lokalizacji sterowanej przez atakującego.|
|Exploit|Exploit|Wykorzystywanie kodu i możliwej aktywności wykorzystywania.|
|Dostęp wstępny|InitialAccess|Uzyskiwanie początkowego dostępu do sieci docelowej zwykle wymaga odgadnięcia hasła, wykorzystania lub wyłudzania informacji e-mail.|
|Ruch lateralny|LateralMovement|Przechodzenie między urządzeniami w sieci docelowej w celu osiągnięcia krytycznych zasobów lub uzyskanie utrwaloności sieci.|
|Złośliwe oprogramowanie|Złośliwe oprogramowanie|Backdoors, trojański i inne rodzaje złośliwego kodu.|
|Persistence|Persistence|Tworzenie punktów rozszerzalności automatycznego (ASEPs) w celu pozostania aktywni i ponownego uruchomienia systemu po jego ponownym uruchomieniu.|
|Eskalacji uprawnień|PrivilegeEscalation|Uzyskiwanie wyższych poziomów uprawnień dla kodu przez uruchomienie go w kontekście procesu lub konta z uprawnieniami.|
|Oprogramowanie wymuszające okup|Oprogramowanie wymuszające okup|Złośliwe oprogramowanie, które szyfruje pliki i rozszerza płatności, aby przywrócić dostęp.|
|Podejrzane działania|Podejrzane Działania|Nietypowe działania, które mogą być działaniami złośliwego oprogramowania lub częścią ataków.|
|Niechciane oprogramowanie|UnwantedSoftware|aplikacje o niskiej reputacji, które wpływają na produktywność i środowisko użytkownika; jako potencjalnie niechciane aplikacje (PUA).|

### <a name="status"></a>Stan

Możesz ograniczyć listę alertów na podstawie ich statusu.

### <a name="investigation-state"></a>Stan badania

Odpowiada stanowi automatycznego badania.

### <a name="category"></a>Kategoria

Możesz filtrować kolejkę, aby wyświetlić określone typy złośliwych działań.

### <a name="assigned-to"></a>Przypisane do

Możesz wybrać wyświetlanie alertów przypisanych do Ciebie lub automatyzacji.

### <a name="detection-source"></a>Źródło wykrywania

Wybierz źródło, które wyzwoliło wykrywanie alertu. Microsoft Threat Experts w wersji Preview mogą teraz filtrować i wyświetlać wykrywanie nowych służb chłonianych zarządzanych przez ekspertów ds. zagrożeń.

> [!NOTE]
> Filtr oprogramowania antywirusowego będzie wyświetlany tylko wtedy, gdy urządzenia Program antywirusowy Microsoft Defender jako domyślny produkt ochrony przed złośliwym kodem w czasie rzeczywistym.

|Źródło wykrywania|Wartość interfejsu API|
|---|---|
|Czujniki innych firm|ThirdPartySensors|
|Oprogramowanie antywirusowe|WindowsDefenderAv|
|Zautomatyzowane badanie|AutomatedInvestigation|
|Wykrywanie niestandardowe|CustomDetection|
|Niestandardowy zestaw ti|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Program Microsoft Defender dla Office 365|OfficeATP|
|Microsoft Threat Experts|ThreatExperts|
|SmartScreen|WindowsDefender SmartScreen|

### <a name="os-platform"></a>Platforma systemu operacyjnego

Ogranicz widok kolejki alertów, wybierając platformę systemu operacyjnego, która cię interesuje.

### <a name="device-group"></a>Grupa Urządzenia

Jeśli chcesz sprawdzić określone grupy urządzeń, możesz je wybrać, aby ograniczyć widok kolejki alertów.

### <a name="associated-threat"></a>Skojarzone zagrożenie

Użyj tego filtru, aby skoncentrować się na alertach związanych z wysokimi zagrożeniami w profilu. Pełną listę zagrożeń o wysokim profilu można wyświetlić w [analizie zagrożeń](threat-analytics.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie alertami programu Microsoft Defender dla punktów końcowych](manage-alerts.md)
- [Badanie alertów programu Microsoft Defender dla punktów końcowych](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-files.md)
- [Badanie urządzeń na liście programu Microsoft Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem programu Microsoft Defender dla punktu końcowego](investigate-domain.md)
- [Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego](investigate-user.md)
