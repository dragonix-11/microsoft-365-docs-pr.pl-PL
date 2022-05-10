---
title: Dowiedz się więcej o zasadach przechowywania & etykiet, aby automatycznie przechowywać lub usuwać zawartość
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się więcej o zasadach przechowywania i etykietach przechowywania, które ułatwiają zachowanie potrzebnych elementów i usuwanie tego, czego nie potrzebujesz.
ms.openlocfilehash: 6fd2f56d6876b6a3832e869767880890486551db
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286929"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>Dowiedz się więcej o zasadach przechowywania i etykietach przechowywania

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*


[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Jeśli widzisz komunikaty dotyczące zasad przechowywania w Teams lub masz pytania dotyczące etykiet przechowywania w aplikacjach, skontaktuj się z działem IT, aby uzyskać informacje o sposobie ich konfigurowania. W międzyczasie pomocne mogą być następujące artykuły:
>
> - [Teams komunikatów dotyczących zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)
> - [Stosowanie etykiet przechowywania do plików w SharePoint lub OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df)
>
> Informacje na tej stronie są przeznaczone dla administratorów IT, którzy mogą tworzyć zasady przechowywania i etykiety przechowywania ze względu na zgodność.

W przypadku większości organizacji ilość i złożoność ich danych rośnie codziennie — poczta e-mail, dokumenty, wiadomości błyskawiczne i nie tylko. Efektywne zarządzanie informacjami lub zarządzanie nimi jest ważne, ponieważ należy:

- **Proaktywnie przestrzegaj przepisów branżowych i zasad wewnętrznych** , które wymagają zachowania zawartości przez minimalny okres czasu — na przykład ustawa o Sarbanes-Oxley może wymagać przechowywania niektórych typów treści przez siedem lat.

- **Zmniejsz ryzyko w przypadku sporu sądowego lub naruszenia zabezpieczeń** , trwale usuwając starą zawartość, której nie musisz już przechowywać.

- **Pomóż organizacji efektywnie udostępniać wiedzę i być bardziej zwinnym** , zapewniając, że użytkownicy pracują tylko z zawartością, która jest dla nich aktualna i istotna.

Skonfigurowane ustawienia przechowywania mogą pomóc w osiągnięciu tych celów. Zarządzanie zawartością często wymaga dwóch akcji:

| Akcja| Celu |
|:-----|:-----|
|Zachowywanie zawartości | Zapobiegaj trwałemu usuwaniu i pozostawaj dostępny dla zbierania elektronicznych materiałów dowodowych |
|Usuwanie zawartości | Trwałe usuwanie zawartości z organizacji|

Za pomocą tych dwóch akcji przechowywania można skonfigurować ustawienia przechowywania dla następujących wyników:

- Zachowaj tylko: zachowaj zawartość na zawsze lub przez określony czas.
- Tylko do usuwania: trwale usuń zawartość po określonym czasie.
- Zachowaj, a następnie usuń: Zachowaj zawartość przez określony czas, a następnie trwale ją usuń.

Te ustawienia przechowywania działają z zawartością, która pozwala zaoszczędzić dodatkowe obciążenia związane z tworzeniem i konfigurowaniem dodatkowego magazynu, gdy konieczne jest zachowanie zawartości ze względu na zgodność. Ponadto nie trzeba implementować dostosowanych procesów do kopiowania i synchronizowania tych danych.

Skorzystaj z poniższych sekcji, aby dowiedzieć się więcej o tym, jak działają zasady przechowywania i etykiety przechowywania, kiedy z nich korzystać i jak wzajemnie się uzupełniają. Jeśli jednak wszystko jest gotowe do rozpoczęcia i wdrożenia ustawień przechowywania w niektórych typowych scenariuszach, zobacz [Wprowadzenie z zarządzaniem cyklem życia danych](get-started-with-data-lifecycle-management.md).

## <a name="how-retention-settings-work-with-content-in-place"></a>Jak działają ustawienia przechowywania z zawartością w miejscu

Jeśli zawartość ma przypisane ustawienia przechowywania, ta zawartość pozostaje w pierwotnej lokalizacji. W większości przypadków ludzie nadal pracują ze swoimi dokumentami lub pocztą tak, jakby nic się nie zmieniło. Jeśli jednak edytują lub usuwają zawartość uwzględnioną w zasadach przechowywania, kopia zawartości zostanie automatycznie zachowana.

- W przypadku witryn SharePoint i OneDrive: kopia jest przechowywana w bibliotece **archiwum zachowywania**.

- W przypadku Exchange skrzynek pocztowych: kopia jest przechowywana w folderze **Elementy możliwe do odzyskania**.

- W przypadku komunikatów Teams i Yammer: kopia jest przechowywana w ukrytym folderze o nazwie **SubstrateHolds** jako podfolder w folderze **elementów do odzyskania** Exchange.

> [!NOTE]
> Ponieważ biblioteka archiwizacyjna jest uwzględniona w limitach przydziału magazynu lokacji, może być konieczne zwiększenie magazynu w przypadku używania ustawień przechowywania dla grup SharePoint i Microsoft 365.
>
Te bezpieczne lokalizacje i zachowana zawartość nie są widoczne dla większości osób. W większości przypadków użytkownicy nie muszą nawet wiedzieć, że ich zawartość podlega ustawieniu przechowywania.

Aby uzyskać bardziej szczegółowe informacje o sposobie działania ustawień przechowywania dla różnych obciążeń, zobacz następujące artykuły:

- [Dowiedz się więcej na temat przechowywania SharePoint i OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md)
- [Dowiedz się więcej na temat przechowywania Yammer](retention-policies-yammer.md)
- [Dowiedz się więcej na temat przechowywania Exchange](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Zasady przechowywania i etykiety przechowywania

Aby przypisać ustawienia przechowywania do zawartości, użyj **zasad przechowywania** i **etykiet przechowywania z zasadami etykiet**. Możesz użyć tylko jednej z tych metod lub połączyć je.

Użyj zasad przechowywania, aby przypisać te same ustawienia przechowywania zawartości na poziomie lokacji lub skrzynki pocztowej, i użyj etykiety przechowywania, aby przypisać ustawienia przechowywania na poziomie elementu (folder, dokument, poczta e-mail).

Jeśli na przykład wszystkie dokumenty w witrynie SharePoint powinny być przechowywane przez 5 lat, bardziej wydajne jest stosowanie zasad przechowywania niż stosowanie tej samej etykiety przechowywania do wszystkich dokumentów w tej lokacji. Jeśli jednak niektóre dokumenty w tej witrynie powinny być przechowywane przez 5 lat, a inne przechowywane przez 10 lat, zasady przechowywania nie będą w stanie tego zrobić. Jeśli musisz określić ustawienia przechowywania na poziomie elementu, użyj etykiet przechowywania.

W przeciwieństwie do zasad przechowywania ustawienia przechowywania z etykiet przechowywania są przenoszone z zawartością, jeśli została przeniesiona do innej lokalizacji w ramach dzierżawy Microsoft 365. Ponadto etykiety przechowywania mają następujące możliwości, których zasady przechowywania nie obsługują:

- Opcje uruchamiania okresu przechowywania od momentu, gdy zawartość została oznaczona etykietą lub na podstawie zdarzenia, oprócz wieku zawartości lub ostatniej modyfikacji.

- Użyj [klasyfikatorów z możliwością trenowania](classifier-learn-about.md) , aby zidentyfikować zawartość do etykiety.

- Zastosuj etykietę domyślną dla dokumentów SharePoint.

- Obsługa [przeglądu dyspozycji](./disposition.md) w celu przejrzenia zawartości przed jej trwałym usunięciem.

- Oznacz zawartość jako [rekord](records-management.md#records) jako część ustawień etykiety i zawsze masz [dowód dyspozycji](disposition.md#disposition-of-records) , gdy zawartość zostanie usunięta po zakończeniu okresu przechowywania.

### <a name="retention-policies"></a>Zasady przechowywania

Zasady przechowywania mogą być stosowane do następujących lokalizacji:

- Exchange e-mail
- witryna SharePoint
- konta OneDrive
- Grupy Microsoft 365
- Skype dla firm
- Exchange folderów publicznych
- komunikaty kanału Teams
- Teams czaty
- Teams wiadomości z kanału prywatnego
- Yammer komunikaty społeczności
- Yammer komunikaty użytkowników

> [!NOTE]
> Teams komunikaty [kanałów zawierają teraz kanały udostępnione](/MicrosoftTeams/shared-channels) (obecnie w wersji zapoznawczej), a także kanały standardowe.

Można bardzo efektywnie zastosować pojedyncze zasady do wielu lokalizacji lub do określonych lokalizacji lub użytkowników.

Na początku okresu przechowywania można wybrać, kiedy zawartość została utworzona lub obsługiwana tylko dla plików i SharePoint, OneDrive i Grupy Microsoft 365 lokalizacji, kiedy zawartość została ostatnio zmodyfikowana.

Elementy dziedziczą ustawienia przechowywania z kontenera określonego w zasadach przechowywania. Jeśli zostaną one następnie przeniesione poza ten kontener, gdy zasady są skonfigurowane do przechowywania zawartości, kopia tego elementu zostanie zachowana w zabezpieczonej lokalizacji obciążenia. Jednak ustawienia przechowywania nie są przenoszone z zawartością w nowej lokalizacji. Jeśli jest to wymagane, użyj etykiet przechowywania zamiast zasad przechowywania.

### <a name="retention-labels"></a>Etykiety przechowywania

Użyj etykiet przechowywania dla różnych typów zawartości, które wymagają różnych ustawień przechowywania. Przykład:

- Formularze podatkowe, które muszą być przechowywane przez minimalny okres czasu.

- Materiały prasowe, które muszą zostać trwale usunięte po osiągnięciu określonego wieku.

- Badania konkurencyjne, które muszą zostać zachowane przez określony okres, a następnie trwale usunięte.

- Wizy służbowe, które muszą być oznaczone jako rekord, aby nie mogły być edytowane ani usuwane.

We wszystkich tych przypadkach etykiety przechowywania umożliwiają stosowanie ustawień przechowywania dla kontroli ładu na poziomie elementu (dokumentu lub poczty e-mail).

Etykiety przechowywania umożliwiają:

- **Umożliwianie osobom w organizacji ręcznego stosowania etykiety przechowywania** do zawartości w grupach Outlook i Outlook w sieci Web, OneDrive, SharePoint i Microsoft 365. Użytkownicy często najlepiej wiedzą, z jakim typem zawartości pracują, aby mogli ją sklasyfikować i zastosować odpowiednie ustawienia przechowywania.

- **Zastosuj etykiety przechowywania do zawartości automatycznie**, jeśli są one zgodne z określonymi warunkami, które obejmują załączniki w chmurze, które są udostępniane w wiadomościach e-mail lub Teams lub gdy zawartość zawiera:
  - Określone typy informacji poufnych.
  - Określone słowa kluczowe, które pasują do utworzonego zapytania.
  - Dopasowanie wzorca klasyfikatora z możliwością trenowania.

- **Rozpocznij okres przechowywania od momentu, gdy zawartość została oznaczona etykietą** dla dokumentów w witrynach SharePoint i kontach OneDrive oraz dla elementów poczty e-mail.

- **Rozpocznij okres przechowywania, gdy wystąpi zdarzenie**, na przykład pracownicy opuszczają organizację lub wygasają umowy.

- **Zastosuj domyślną etykietę przechowywania do biblioteki dokumentów, folderu lub dokumentu ustawionego** w SharePoint, aby wszystkie dokumenty przechowywane w tej lokalizacji dziedziczyć domyślną etykietę przechowywania.

- **Oznacz elementy jako rekord jako** część strategii [zarządzania rekordami](records-management.md) . Gdy zawartość oznaczona etykietą pozostanie w Microsoft 365, zostaną nałożone dalsze ograniczenia dotyczące zawartości, która może być potrzebna ze względów prawnych. Aby uzyskać więcej informacji, zobacz [Porównanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

Etykiety przechowywania, w przeciwieństwie do [etykiet poufności](sensitivity-labels.md), nie są utrwalane, jeśli zawartość jest przenoszona poza Microsoft 365.

#### <a name="classifying-content-without-applying-any-actions"></a>Klasyfikowanie zawartości bez stosowania żadnych akcji

Mimo że głównym celem etykiet przechowywania jest przechowywanie lub usuwanie zawartości, można również używać etykiet przechowywania bez włączania żadnych akcji przechowywania lub innych. W takim przypadku można użyć etykiety przechowywania po prostu jako etykiety tekstowej, bez wymuszania żadnych akcji.

Na przykład można utworzyć i zastosować etykietę przechowywania o nazwie "Przejrzyj później" bez akcji, a następnie użyć tej etykiety, aby znaleźć tę zawartość później.

![Ustawienia etykiet do klasyfikowania tylko.](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Używanie etykiety przechowywania jako warunku w zasadach DLP

Etykietę przechowywania można określić jako warunek w zasadach ochrony przed utratą danych (DLP) usługi Microsoft Purview dla dokumentów w SharePoint. Na przykład skonfiguruj zasady DLP, aby zapobiec udostępnianiu dokumentów poza organizacją, jeśli zastosowano do nich określoną etykietę przechowywania.

Aby uzyskać więcej informacji, zobacz [Używanie etykiety przechowywania jako warunku w zasadach DLP](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Etykiety przechowywania i zasady, które je stosują

Po opublikowaniu etykiet przechowywania są one uwzględniane w **zasadach etykiet przechowywania** , które umożliwiają administratorom i użytkownikom stosowanie ich do zawartości. Jak pokazano na poniższym diagramie:

1. Pojedyncza etykieta przechowywania może być uwzględniona w wielu zasadach etykiet przechowywania.

2. Zasady etykiet przechowywania określają lokalizacje, w których mają zostać opublikowane etykiety przechowywania. Ta sama lokalizacja może być uwzględniona w wielu zasadach etykiet przechowywania.

![Sposób dodawania etykiet przechowywania do zasad etykiet określających lokalizacje.](../media/retention-labels-and-policies.png)

Można również utworzyć co najmniej jedną **zasadę automatycznego stosowania etykiet przechowywania**, z których każda ma pojedynczą etykietę przechowywania. W przypadku tych zasad etykieta przechowywania jest automatycznie stosowana po spełnieniu warunków określonych w zasadach.

#### <a name="retention-label-policies-and-locations"></a>Zasady i lokalizacje etykiet przechowywania

Etykiety przechowywania mogą być publikowane w różnych lokalizacjach, w zależności od tego, co robi etykieta przechowywania.

| Jeśli etykieta przechowywania jest... | Następnie można zastosować zasady etykiety do... |
|:-----|:-----|
|Opublikowane dla administratorów i użytkowników końcowych  |Exchange, SharePoint, OneDrive, Grupy Microsoft 365  |
|Automatycznie stosowane na podstawie poufnych typów informacji lub klasyfikatorów z możliwością trenowania  |Exchange, SharePoint, OneDrive  |
|Automatycznie stosowane na podstawie słów kluczowych lub zapytania  |Exchange, SharePoint, OneDrive, Grupy Microsoft 365  |
|Automatyczne stosowanie do załączników w chmurze  |SharePoint, OneDrive, Grupy Microsoft 365  |

Exchange wiadomości z folderów publicznych, Skype, Teams i Yammer nie obsługują etykiet przechowywania. Aby zachować i usunąć zawartość z tych lokalizacji, zamiast tego użyj zasad przechowywania.

#### <a name="only-one-retention-label-at-a-time"></a>Tylko jedna etykieta przechowywania naraz

Wiadomość e-mail lub dokument może mieć jednocześnie zastosowaną tylko jedną etykietę przechowywania. Etykietę przechowywania można zastosować [ręcznie](create-apply-retention-labels.md#manually-apply-retention-labels) przez użytkownika końcowego lub administratora lub automatycznie przy użyciu dowolnej z następujących metod:

- [Zasady automatycznego stosowania etykiet](apply-retention-labels-automatically.md)
- [Model interpretacji dokumentów dla SharePoint Syntex](../contentunderstanding/apply-a-retention-label-to-a-model.md)
- [Etykieta domyślna dla SharePoint](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) lub [Outlook](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)
- [reguły Outlook](create-apply-retention-labels.md#automatically-applying-a-retention-label-to-email-by-using-rules)

W przypadku standardowych etykiet przechowywania (nie oznaczają one elementów jako [rekordu lub rekordu regulacyjnego](records-management.md#records)):

- Administratorzy i użytkownicy końcowi mogą ręcznie zmieniać lub usuwać istniejącą etykietę przechowywania stosowaną do zawartości.

- Gdy zawartość ma już zastosowaną etykietę przechowywania, istniejąca etykieta nie zostanie automatycznie usunięta ani zastąpiona inną etykietą przechowywania jednym możliwym wyjątkiem: istniejąca etykieta została zastosowana jako etykieta domyślna. Jeśli używasz etykiety domyślnej, istnieją pewne scenariusze, w których można ją zastąpić inną etykietą domyślną lub automatycznie usunąć.

  Aby uzyskać więcej informacji na temat zachowania etykiety, gdy jest stosowana przy użyciu etykiety domyślnej:

  - Etykieta domyślna dla SharePoint: [zachowanie etykiety podczas używania etykiety domyślnej dla SharePoint](create-apply-retention-labels.md#label-behavior-when-you-use-a-default-label-for-sharepoint)
  - Etykieta domyślna dla Outlook: [stosowanie domyślnej etykiety przechowywania do folderu Outlook](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)

- Jeśli istnieje wiele zasad automatycznego stosowania etykiet, które mogą stosować etykietę przechowywania, a zawartość spełnia warunki wielu zasad, zostanie zastosowana etykieta przechowywania najstarszych zasad automatycznego stosowania etykiet (według daty utworzenia).

Gdy etykiety przechowywania oznaczają elementy jako rekord lub rekord regulacyjny, etykiety te nigdy nie są automatycznie zmieniane. Tylko administratorzy kontenera mogą ręcznie zmieniać lub usuwać etykiety przechowywania, które oznaczają elementy jako rekord, ale nie rekordy regulacyjne. Aby uzyskać więcej informacji, zobacz [Porównanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

#### <a name="monitoring-retention-labels"></a>Monitorowanie etykiet przechowywania

W portalu zgodności usługi Microsoft Purview wybierz pozycję **Klasyfikacja danych** i stronę **Przegląd** , aby monitorować sposób użycia etykiet przechowywania w dzierżawie i identyfikować lokalizację elementów oznaczonych etykietami. Aby uzyskać więcej informacji, w tym ważne wymagania wstępne, zobacz [Informacje o klasyfikacji danych](data-classification-overview.md).

Następnie możesz przejść do szczegółów przy użyciu [Eksploratora zawartości](data-classification-content-explorer.md) i [Eksploratora działań](data-classification-activity-explorer.md).

> [!TIP]
>Rozważ użycie niektórych innych szczegółowych informacji o klasyfikacji danych, takich jak klasyfikatory z możliwością trenowania i typy informacji poufnych, aby ułatwić zidentyfikowanie zawartości, która może być konieczna do zachowania lub usunięcia lub zarządzania jako rekordy.

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Wyszukiwanie zawartości przy użyciu funkcji wyszukiwania zawartości w celu znalezienia całej zawartości z określoną etykietą przechowywania

Po zastosowaniu etykiet przechowywania do zawartości, przez użytkowników lub automatycznie stosowane, można użyć wyszukiwania zawartości, aby znaleźć wszystkie elementy, które mają określonej etykiety przechowywania stosowane.

Podczas tworzenia wyszukiwania zawartości wybierz warunek **Etykieta przechowywania** , a następnie wprowadź pełną nazwę etykiety przechowywania lub część nazwy etykiety i użyj symbolu wieloznacznego. Aby uzyskać więcej informacji, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

![Warunek etykiety przechowywania.](../media/retention-label-condition.png)

## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Porównanie możliwości zasad przechowywania i etykiet przechowywania

Poniższa tabela ułatwia określenie, czy należy używać zasad przechowywania, czy etykiety przechowywania w oparciu o możliwości.

|Możliwości|Zasady przechowywania |Etykieta przechowywania|
|:-----|:-----|:-----|:-----|
|Ustawienia przechowywania, które mogą być zachowywane, a następnie usuwane, tylko do zachowania lub tylko do usuwania |Tak |Tak |
|Obsługiwane obciążenia: <br />- Exchange <br />- SharePoint <br />- OneDrive <br />— grupy Microsoft 365 <br />- Skype dla firm <br />- Teams<br />- Yammer|<br /> Tak <br /> Tak <br /> Tak <br /> Tak <br /> Tak <br /> Tak <br /> Tak | <br /> Tak, z wyjątkiem folderów publicznych <br /> Tak <br /> Tak <br /> Tak <br /> Nie <br /> Nie <br /> Nie |
|Przechowywanie stosowane automatycznie | Tak | Tak |
|Przechowywanie stosowane na podstawie warunków <br /> — poufne typy informacji, KQL zapytań i słów kluczowych, klasyfikatory z możliwością trenowania, załączniki w chmurze| Nie | Tak |
|Przechowywanie zastosowane ręcznie | Nie | Tak |
|Interakcja użytkownika końcowego | Nie | Tak |
|Utrwala się, jeśli zawartość jest przenoszona | Nie | Tak, w ramach dzierżawy Microsoft 365 |
|Deklarowanie elementu jako rekordu| Nie | Tak |
|Rozpoczynanie okresu przechowywania po oznaczeniu etykietą lub na podstawie zdarzenia | Nie | Tak |
|Przegląd dyspozycji | Nie| Tak |
|Dowód dyspozycji przez maksymalnie 7 lat | Nie |Tak, jeśli używasz przeglądu dyspozycji lub element jest oznaczony jako rekord|
|Inspekcja działań administratora| Tak | Tak|
|Akcje przechowywania inspekcji| Nie | Tak <sup>\*</sup> |
|Identyfikowanie elementów podlegających przechowywaniu: <br /> — Wyszukiwanie zawartości <br /> — Strona klasyfikacji danych, eksplorator zawartości, eksplorator działań | <br /> Nie <br /> Nie | <br /> Tak <br /> Tak|

**Przypisie:**

<sup>\*</sup>W przypadku etykiet przechowywania, które nie oznaczają zawartości jako rekordu lub rekordu regulacyjnego, zdarzenia inspekcji są ograniczone do sytuacji, gdy element w SharePoint lub OneDrive ma etykietę zastosowaną, zmienioną lub usuniętą. Aby uzyskać szczegółowe informacje dotyczące inspekcji etykiet przechowywania, zobacz sekcję [Auditing retention actions (Akcje przechowywania inspekcji)](#auditing-retention-actions) na tej stronie.

### <a name="combining-retention-policies-and-retention-labels"></a>Łączenie zasad przechowywania i etykiet przechowywania

Nie musisz wybierać między używaniem tylko zasad przechowywania a etykietami przechowywania. Obie metody mogą być używane razem i w rzeczywistości, uzupełniając się nawzajem w celu bardziej kompleksowego rozwiązania.

Poniższe przykłady to tylko niektóre ze sposobów łączenia zasad przechowywania i etykiet przechowywania dla tej samej lokalizacji.

Aby uzyskać więcej informacji na temat sposobu współdziałania zasad przechowywania i etykiet przechowywania oraz sposobu określania ich połączonego wyniku, zobacz sekcję na tej stronie, w której [wyjaśniono zasady przechowywania i pierwszeństwo](#the-principles-of-retention-or-what-takes-precedence).

**Przykład zastąpienia automatycznego usuwania przez użytkowników**

Scenariusz: domyślnie zawartość na kontach OneDrive użytkowników jest automatycznie usuwana po pięciu latach, ale użytkownicy muszą mieć możliwość zastąpienia tej zawartości dla określonych dokumentów.

1. Tworzysz i konfigurujesz zasady przechowywania, które automatycznie usuwają zawartość pięć lat po jej ostatniej modyfikacji, i stosujesz zasady do wszystkich kont OneDrive.

2. Tworzysz i konfigurujesz etykietę przechowywania, która przechowuje zawartość na zawsze i dodaje ją do zasad etykiet publikowanych na wszystkich kontach OneDrive. Użytkownikom wyjaśniono, jak ręcznie zastosować tę etykietę do określonych dokumentów, które powinny zostać wykluczone z automatycznego usuwania, jeśli nie zostaną zmodyfikowane po pięciu latach.

**Przykład dłuższego przechowywania elementów**

Scenariusz: domyślnie elementy SharePoint są automatycznie zachowywane, a następnie usuwane po pięciu latach, ale dokumenty w określonych bibliotekach muszą być przechowywane przez dziesięć lat.

1. Tworzysz i konfigurujesz zasady przechowywania, które automatycznie przechowują, a następnie usuwają zawartość po pięciu latach oraz stosują zasady do wszystkich wystąpień SharePoint i Grupy Microsoft 365.

2. Tworzysz i konfigurujesz etykietę przechowywania, która automatycznie zachowuje zawartość przez dziesięć lat. Tę etykietę można opublikować dla SharePoint administratorów witryny, aby mogli zastosować ją jako etykietę domyślną, która ma być dziedziczona przez wszystkie elementy w określonych bibliotekach dokumentów.

**Przykład usuwania elementów w krótszym okresie**

Scenariusz: domyślnie wiadomości e-mail nie są zachowywane, ale są automatycznie usuwane po dziesięciu latach. Jednak wiadomości e-mail związane z określonym projektem, który ma nazwę kodu wstępnej wersji, muszą zostać automatycznie usunięte po roku.

1. Tworzysz i konfigurujesz zasady przechowywania, które automatycznie usuwają zawartość po dziesięciu latach, i stosujesz zasady do wszystkich Exchange adresatów.

2. Tworzysz i konfigurujesz etykietę przechowywania, która automatycznie usuwa zawartość po roku. Opcje stosowania tej etykiety do odpowiednich wiadomości e-mail obejmują:
    - Tworzysz zasady automatycznego etykietowania, które identyfikują zawartość przy użyciu nazwy kodu projektu jako słowa kluczowego, i stosujesz zasady do wszystkich adresatów Exchange
    - Publikujesz etykietę i instruujesz użytkowników biorących udział w projekcie, jak utworzyć regułę automatyczną w Outlook, która stosuje tę etykietę
    - Należy opublikować etykietę i poinstruować użytkowników, aby utworzyli folder w Outlook dla wszystkich wiadomości e-mail związanych z projektem i zastosowali opublikowaną etykietę do folderu, a następnie utworzyli regułę Outlook, aby przenieść wszystkie wiadomości e-mail związane z projektem do tego folderu

## <a name="how-long-it-takes-for-retention-settings-to-apply"></a>Jak długo trwa stosowanie ustawień przechowywania

Po przesłaniu zasad przechowywania dla obciążeń i zasad etykiet w celu automatycznego zastosowania etykiety przechowywania zezwalaj na zastosowanie ustawień przechowywania do zawartości przez maksymalnie 7 dni:

- [Jak długo trwa obowiązywanie zasad przechowywania](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- [Jak długo trwa obowiązywanie etykiet przechowywania](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect)

Podobnie po opublikowaniu etykiet etykiety przechowywania można wyświetlić do 7 dni w aplikacjach:

- [Gdy etykiety przechowywania staną się dostępne do zastosowania](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply)

Często zasady będą obowiązywać, a etykiety będą widoczne szybciej niż 7 dni. Jednak w przypadku wielu potencjalnych zmiennych, które mogą mieć wpływ na ten proces, najlepiej zaplanować go na maksymalnie 7 dni.

## <a name="adaptive-or-static-policy-scopes-for-retention"></a>Zakresy zasad adaptacyjnych lub statycznych na potrzeby przechowywania

Podczas tworzenia zasad przechowywania lub zasad etykiet przechowywania należy wybrać opcję adaptacyjną i statyczną, aby zdefiniować zakres zasad.

- **Zakres adaptacyjny** używa określonego zapytania, więc członkostwo nie jest statyczne, ale dynamiczne, uruchamiając codziennie atrybuty lub właściwości określone dla wybranych lokalizacji. Można użyć wielu zakresów adaptacyjnych z jednymi zasadami.

    Przykład: Wiadomości e-mail i dokumenty OneDrive dla kadry kierowniczej wymagają dłuższego okresu przechowywania niż użytkownicy standardowi. Tworzysz zasady przechowywania z zakresem adaptacyjnym, który używa tytułu zadania atrybutu Azure AD "Executive", a następnie wybiera lokalizacje Exchange poczty e-mail i kont OneDrive dla zasad. Nie ma potrzeby określania adresów e-mail ani adresów URL OneDrive dla tych użytkowników, ponieważ zakres adaptacyjny automatycznie pobiera te wartości. W przypadku nowych menedżerów nie trzeba ponownie konfigurować zasad przechowywania, ponieważ ci nowi użytkownicy z odpowiednimi wartościami dla poczty e-mail i OneDrive są automatycznie odbierane.

- **Zakres statyczny** nie używa zapytań i ma ograniczoną konfigurację, ponieważ może mieć zastosowanie do wszystkich wystąpień określonej lokalizacji lub używać dołączania i wykluczeń dla określonych wystąpień dla danej lokalizacji. Te trzy opcje są czasami określane jako odpowiednio "org-wide", "includes" i "excludes".

    Przykład: Wiadomości e-mail i dokumenty OneDrive dla kadry kierowniczej wymagają dłuższego okresu przechowywania niż użytkownicy standardowi. Tworzysz zasady przechowywania z zakresem statycznym, który wybiera lokalizacje Exchange poczty e-mail i kont OneDrive dla zasad. W Exchange lokalizacji poczty e-mail możesz zidentyfikować grupę zawierającą tylko kierownictwo, dlatego należy określić tę grupę dla zasad przechowywania, a członkostwo w grupie z odpowiednimi adresami e-mail jest pobierane po utworzeniu zasad. W przypadku lokalizacji kont OneDrive należy zidentyfikować, a następnie określić poszczególne adresy URL OneDrive dla każdego kierownictwa. W przypadku nowych menedżerów należy ponownie skonfigurować zasady przechowywania, aby dodać nowe adresy e-mail i adresy URL OneDrive. Należy również zaktualizować adresy URL OneDrive w każdej chwili, gdy nastąpi zmiana nazwy UPN kierownictwa.

    OneDrive adresy URL są szczególnie trudne do niezawodnego określenia, ponieważ domyślnie te adresy URL nie są tworzone, dopóki użytkownik nie uzyskuje dostępu do OneDrive po raz pierwszy. A jeśli nazwa UPN użytkownika zmieni się, o czym możesz nie wiedzieć, jego adres URL OneDrive zostanie automatycznie zmieniony.

Zalety korzystania z zakresów adaptacyjnych:

- Brak limitów [liczby elementów na zasady](retention-limits.md#maximum-number-of-items-per-policy). Mimo że zasady adaptacyjne nadal podlegają [maksymalnej liczbie zasad na ograniczenia dzierżawy](retention-limits.md#maximum-number-of-policies-per-tenant) , bardziej elastyczna konfiguracja prawdopodobnie spowoduje znacznie mniejszą liczbę zasad.

- Bardziej zaawansowane określanie wymagań dotyczących przechowywania. Na przykład można przypisać różne ustawienia przechowywania do użytkowników zgodnie z ich lokalizacją geograficzną przy użyciu istniejących atrybutów Azure AD bez konieczności tworzenia i utrzymywania grup administracyjnych w tym celu.

- Członkostwo oparte na zapytaniach zapewnia odporność na zmiany biznesowe, które mogą nie być niezawodnie odzwierciedlone w członkostwie w grupach lub procesach zewnętrznych, które opierają się na komunikacji między działami.

- Pojedyncze zasady przechowywania mogą obejmować lokalizacje zarówno dla Microsoft Teams, jak i Yammer, natomiast w przypadku używania zakresu statycznego te lokalizacje wymagają własnych zasad przechowywania.

- Do nieaktywnych skrzynek pocztowych można zastosować określone ustawienia przechowywania. Ta konfiguracja nie jest możliwa w przypadku zakresu statycznego, ponieważ w momencie przypisywania zasad zakresy statyczne nie obsługują konkretnego dołączania adresatów z nieaktywnymi skrzynkami pocztowymi.

Zalety używania zakresów statycznych:

- Prostsza konfiguracja, jeśli chcesz, aby wszystkie wystąpienia były automatycznie wybierane dla obciążenia.

    W przypadku opcji "includes" i "excludes" ten wybór może być początkowo prostszą konfiguracją, jeśli liczba wystąpień, które należy określić, jest niska i nie ulega zmianie. Jednak gdy liczba wystąpień zaczyna rosnąć i w organizacji występują częste zmiany wymagające ponownej konfiguracji zasad, zakresy adaptacyjne mogą być prostsze do skonfigurowania i znacznie łatwiejsze w obsłudze.

- **Lokalizacje folderów publicznych** **Skype dla firm** i Exchange nie obsługują zakresów adaptacyjnych. W przypadku tych lokalizacji należy użyć zakresu statycznego.

Aby uzyskać informacje o konfiguracji, zobacz [Konfigurowanie zakresów adaptacyjnych](retention-settings.md#configuration-information-for-adaptive-scopes).

Aby obejrzeć zarejestrowane seminarium internetowe (wymaga rejestracji), odwiedź [stronę Szczegółowe informacje na temat zakresów adaptacyjnych](https://mipc.eventbuilder.com/event/45703).

> [!IMPORTANT]
> Obecnie zakresy adaptacyjne nie obsługują [blokady zachowania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania](#use-preservation-lock-to-restrict-changes-to-policies).

## <a name="policy-lookup"></a>Wyszukiwanie zasad

Można skonfigurować wiele zasad przechowywania dla lokalizacji Microsoft 365, a także wiele zasad etykiet przechowywania publikowanych lub automatycznie stosowanych. Aby znaleźć zasady przechowywania przypisane do określonych użytkowników, witryn i grup Microsoft 365, użyj wyszukiwania **zasad** z rozwiązań do **zarządzania cyklem życia danych** lub **zarządzania rekordami** w portalu zgodności usługi Microsoft Purview.

Przykład:

![Wyszukiwanie zasad w celu znalezienia zasad przechowywania przypisanych do określonych użytkowników, witryn i grup Microsoft 365 ](../media/policy-lookup.png)

Musisz określić dokładny adres e-mail użytkownika, dokładny adres URL witryny lub dokładny adres e-mail grupy Microsoft 365. Na przykład nie można używać symboli wieloznacznych ani częściowych dopasowań.

Opcja dla witryn obejmuje konta OneDrive. Aby uzyskać informacje na temat określania adresu URL konta OneDrive użytkownika, zobacz [Pobieranie listy wszystkich adresów URL OneDrive użytkownika w organizacji](/onedrive/list-onedrive-urls).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Zasady przechowywania lub co ma pierwszeństwo?

W przeciwieństwie do etykiet przechowywania można zastosować więcej niż jedną zasadę przechowywania do tej samej zawartości. Każda zasada przechowywania może spowodować zachowanie akcji i usunięcie akcji. Ponadto ten element może również podlegać tym akcjom z etykiety przechowywania.

W tym scenariuszu, gdy elementy mogą podlegać wielu ustawień przechowywania, które mogą kolidować ze sobą, co ma pierwszeństwo, aby określić wynik?

Wynikiem nie jest to, które pojedyncze zasady przechowywania lub pojedyncza etykieta przechowywania wygrywa, ale czas przechowywania elementu (jeśli ma to zastosowanie) i kiedy element zostanie usunięty (jeśli ma to zastosowanie). Te dwie akcje są obliczane niezależnie od siebie, od wszystkich ustawień przechowywania zastosowanych do elementu.

Na przykład element może podlegać jednej zasadom przechowywania, które są skonfigurowane pod kątem akcji tylko do usuwania, oraz innym zasadom przechowywania, które są skonfigurowane do przechowywania, a następnie usuwania. W związku z tym ten element ma tylko jedną akcję zachowywania, ale dwie akcje usuwania. Akcje przechowywania i usuwania mogą być ze sobą w konflikcie, a dwie akcje usuwania mogą mieć datę powodującą konflikt. Zasady przechowywania wyjaśniają wynik.

Na wysokim poziomie można mieć pewność, że przechowywanie ma zawsze pierwszeństwo przed trwałym usunięciem i wygrywa najdłuższy okres przechowywania. Te dwie proste reguły zawsze decydują o tym, jak długo element zostanie zachowany.

Istnieje jeszcze kilka czynników, które określają, kiedy element zostanie trwale usunięty, co obejmuje akcję usuwania z etykiety przechowywania, która zawsze ma pierwszeństwo przed akcją usuwania z zasad przechowywania.

Użyj następującego przepływu, aby zrozumieć wyniki przechowywania i usuwania dla pojedynczego elementu, w którym każdy poziom działa jako tie-breaker dla konfliktów, od góry do dołu. Jeśli wynik jest określany przez pierwszy poziom, ponieważ nie ma dalszych konfliktów, nie ma potrzeby, aby przejść do następnego poziomu itd.

> [!IMPORTANT]
> Jeśli używasz etykiet przechowywania: Przed zastosowaniem zasad w celu określenia wyniku wielu ustawień przechowywania dla tego samego elementu upewnij się, że wiesz, [która etykieta przechowywania jest stosowana](#only-one-retention-label-at-a-time).

![Diagram zasad przechowywania.](../media/principles-of-retention.png)

Przed bardziej szczegółowym objaśnieniem każdej zasady należy zrozumieć różnicę między okresem przechowywania elementu a określonym okresem przechowywania w zasadach przechowywania lub etykiecie przechowywania. Dzieje się tak dlatego, że chociaż domyślną konfiguracją jest rozpoczęcie okresu przechowywania po utworzeniu elementu, tak aby koniec okresu przechowywania został ustalony dla elementu, pliki obsługują również konfigurację, aby rozpocząć okres przechowywania od momentu ostatniej modyfikacji pliku. W przypadku tej alternatywnej konfiguracji za każdym razem, gdy plik jest modyfikowany, rozpoczyna się okres przechowywania, co wydłuża koniec okresu przechowywania elementu. Etykiety przechowywania obsługują również uruchamianie okresu przechowywania po oznaczeniu i na początku zdarzenia.

Aby zastosować zasady w działaniu z serią pytań Tak i Nie, możesz również użyć [schematu blokowego przechowywania](retention-flowchart.md).

Wyjaśnienie czterech różnych zasad:

1. **Przechowywanie wygrywa nad usunięciem.** Zawartość nie zostanie trwale usunięta, jeśli ma również ustawienia przechowywania, aby ją zachować. Chociaż ta zasada zapewnia zachowanie zawartości ze względu na zgodność, proces usuwania może być nadal inicjowany (inicjowany przez użytkownika lub inicjowany przez system), a w związku z tym może usunąć zawartość z głównego widoku użytkowników. Jednak trwałe usunięcie jest zawieszone. Aby uzyskać więcej informacji na temat sposobu i miejsca przechowywania zawartości, użyj następujących linków dla każdego obciążenia:

    - [Jak działa przechowywanie SharePoint i OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)
    - [Jak przechowywanie działa z Microsoft Teams](retention-policies-teams.md#how-retention-works-with-microsoft-teams)
    - [Jak przechowywanie działa z Yammer](retention-policies-yammer.md#how-retention-works-with-yammer)
    - [Jak działa przechowywanie dla Exchange](retention-policies-exchange.md#how-retention-works-for-exchange)

    **Przykład dla tej pierwszej zasady**: wiadomość e-mail podlega zasadom przechowywania dla Exchange, który jest skonfigurowany do usuwania elementów trzy lata po ich utworzeniu, a także ma zastosowaną etykietę przechowywania, która jest skonfigurowana do przechowywania elementów pięć lat po ich utworzeniu.

    Wiadomość e-mail jest przechowywana przez pięć lat, ponieważ ta akcja przechowywania ma pierwszeństwo przed usunięciem. Wiadomość e-mail zostanie trwale usunięta pod koniec pięciu lat z powodu akcji usuwania, która została zawieszona, gdy akcja przechowywania obowiązywała.

2. **Wygrywa najdłuższy okres przechowywania.** Jeśli zawartość podlega wielu ustawień przechowywania, które zachowują zawartość przez różne okresy, zawartość będzie przechowywana do końca najdłuższego okresu przechowywania elementu.

    > [!NOTE]
    > Istnieje możliwość okresu przechowywania wynoszącego 5 lat w zasadach przechowywania lub wygranych etykietach w okresie przechowywania wynoszącym 7 lat w zasadach przechowywania lub etykiecie, ponieważ okres 5 lat jest skonfigurowany do uruchamiania na podstawie czasu ostatniej modyfikacji pliku, a okres 7 lat jest skonfigurowany tak, aby rozpoczynał się od momentu utworzenia pliku.

    **Przykład dla tej drugiej zasady**: Dokumenty w witrynie SharePoint marketingu podlegają dwóm zasadom przechowywania. Pierwsze zasady przechowywania są skonfigurowane dla wszystkich witryn SharePoint do przechowywania elementów przez pięć lat po ich utworzeniu. Drugie zasady przechowywania są skonfigurowane dla określonych witryn SharePoint do przechowywania elementów przez dziesięć lat po ich utworzeniu.

    Dokumenty w tej witrynie SharePoint marketingu są przechowywane przez dziesięć lat, ponieważ jest to najdłuższy okres przechowywania elementu.

3. **Jawne zwycięstwo nad niejawnym usuwaniem.** Gdy konflikty są teraz rozwiązywane na potrzeby przechowywania, pozostają tylko konflikty usuwania:

    1. Etykieta przechowywania (jednak została zastosowana) zapewnia jawne przechowywanie w porównaniu z zasadami przechowywania, ponieważ ustawienia przechowywania są stosowane do pojedynczego elementu, a nie nie niejawnie przypisywane z kontenera. Oznacza to, że akcja usuwania z etykiety przechowywania ma zawsze pierwszeństwo przed akcją usuwania z dowolnych zasad przechowywania.

        **Przykład dla tej trzeciej zasady (etykiety)**: dokument podlega dwóm zasadom przechowywania, które mają odpowiednio akcję usuwania wynoszącą pięć i dziesięć lat, a także etykietę przechowywania, która ma akcję usuwania wynoszącą siedem lat.

        Dokument jest trwale usuwany po siedmiu latach, ponieważ pierwszeństwo ma akcja usuwania z etykiety przechowywania.

    2. Jeśli masz tylko zasady przechowywania: jeśli zasady przechowywania dla lokalizacji korzystają z zakresu adaptacyjnego lub zakresu statycznego obejmującego określone wystąpienia (na przykład określonych użytkowników Exchange wiadomości e-mail), zasady przechowywania mają pierwszeństwo przed zakresem statycznym skonfigurowanym dla wszystkich wystąpień dla tej samej lokalizacji.

        Zakres statyczny skonfigurowany dla wszystkich wystąpień dla lokalizacji jest czasami określany jako "zasady dla całej organizacji". Na przykład **Exchange wiadomości e-mail** i domyślne ustawienie **Wszyscy adresaci**. Możesz też **SharePoint witryny** i domyślne ustawienie **Wszystkie witryny**. Jeśli zasady przechowywania nie są w całej organizacji, ale zostały skonfigurowane z zakresem adaptacyjnym lub zakresem statycznym obejmującym określone wystąpienia, mają one równe pierwszeństwo na tym poziomie.

        **Przykład 1 dla tej trzeciej zasady (zasad)**: Wiadomość e-mail podlega dwóm zasadom przechowywania. Pierwsze zasady przechowywania są nieskopowe i usuwają elementy po dziesięciu latach. Drugie zasady przechowywania są ograniczone do określonych skrzynek pocztowych i usuwają elementy po pięciu latach.

        Wiadomość e-mail jest trwale usuwana po pięciu latach, ponieważ akcja usuwania z zasad przechowywania o określonym zakresie ma pierwszeństwo przed zasadami przechowywania w całej organizacji.

        **Przykład 2 dla tej trzeciej zasady (zasad)**: Dokument na koncie OneDrive użytkownika podlega dwóm zasadom przechowywania. Pierwsze zasady przechowywania mają zakres obejmujący konto OneDrive tego użytkownika i mają akcję usuwania po 10 latach. Drugie zasady przechowywania mają zakres obejmujący konto OneDrive tego użytkownika i mają akcję usuwania po siedmiu latach.

        Gdy ten dokument zostanie trwale usunięty, nie można określić na tym poziomie, ponieważ obie zasady przechowywania mają zakres obejmujący określone wystąpienia.

4. **Wygrywa najkrótszy okres usuwania.** Dotyczy określenia, kiedy elementy zostaną usunięte z zasad przechowywania i nie można rozpoznać wyniku z poprzedniego poziomu: zawartość jest trwale usuwana na końcu najkrótszego okresu przechowywania elementu.

    > [!NOTE]
    > Istnieje możliwość, że zasady przechowywania z okresem przechowywania wynoszącym 7 lat wygrywają zasady przechowywania wynoszące 5 lat, ponieważ pierwsze zasady są skonfigurowane do uruchamiania okresu przechowywania na podstawie czasu utworzenia pliku, a drugie zasady przechowywania od momentu ostatniej modyfikacji pliku.

    **Przykład dla tej czwartej zasady**: dokument na koncie OneDrive użytkownika podlega dwóm zasadom przechowywania. Pierwsze zasady przechowywania mają zakres obejmujący konto OneDrive tego użytkownika i mają akcję usuwania wynoszącą 10 lat po utworzeniu pliku. Drugie zasady przechowywania mają zakres obejmujący konto OneDrive tego użytkownika i mają akcję usuwania wynoszącą siedem lat po utworzeniu pliku.

    Ten dokument zostanie trwale usunięty po siedmiu latach, ponieważ jest to najkrótszy okres przechowywania elementu z tych dwóch zasad przechowywania w zakresie.

Przedmioty podlegające blokadzie zbierania elektronicznych materiałów dowodowych również podlegają pierwszej zasadzie przechowywania; Nie można ich trwale usunąć za pomocą żadnych zasad przechowywania ani etykiet przechowywania. Po zwolnieniu tej blokady zasady przechowywania nadal mają do nich zastosowanie. Mogą one na przykład podlegać niewygasłemu okresowi przechowywania lub akcji usuwania.

### <a name="principles-of-retention-examples-that-combine-retain-and-delete-actions"></a>Przykłady zasad przechowywania, które łączą akcje zachowywania i usuwania

Poniższe przykłady są bardziej złożone, aby zilustrować zasady przechowywania, gdy są łączone różne akcje zachowywania i usuwania. Aby ułatwić stosowanie przykładów, wszystkie zasady przechowywania i etykiety używają domyślnego ustawienia uruchamiania okresu przechowywania po utworzeniu elementu, aby koniec okresu przechowywania był taki sam dla elementu.

1. Element ma następujące ustawienia przechowywania:

    - Zasady przechowywania dla usuwania tylko po pięciu latach
    - Zasady przechowywania, które są zachowywane przez trzy lata, a następnie usuwane
    - Etykieta przechowywania, która zachowuje tylko przez siedem lat

    **Wynik**: Element jest przechowywany przez siedem lat, ponieważ przechowywanie ma pierwszeństwo przed usunięciem, a siedem lat jest najdłuższym okresem przechowywania dla elementu. Po zakończeniu tego okresu przechowywania element zostanie trwale usunięty z powodu akcji usuwania z zasad przechowywania.

    Mimo że dwie zasady przechowywania mają różne daty dla akcji usuwania, najwcześniej element, który można trwale usunąć, znajduje się na końcu najdłuższego okresu przechowywania, który jest dłuższy niż obie daty usunięcia.

2. Element ma następujące ustawienia przechowywania:

    - Zasady przechowywania w całej organizacji, które usuwają tylko po dziesięciu latach
    - Zasady przechowywania o określonym zakresie z określonymi wystąpieniami, które są zachowywane przez pięć lat, a następnie usuwane
    - Etykieta przechowywania, która zachowuje się przez trzy lata, a następnie usuwa

    **Wynik**: Element jest zachowywany przez pięć lat, ponieważ jest to najdłuższy okres przechowywania elementu. Na koniec tego okresu przechowywania element jest trwale usuwany z powodu akcji usuwania wynoszącej trzy lata z etykiety przechowywania. Usunięcie z etykiet przechowywania ma pierwszeństwo przed usunięciem ze wszystkich zasad przechowywania. W tym przykładzie wszystkie konflikty są rozwiązywane przez trzeci poziom.

## <a name="use-preservation-lock-to-restrict-changes-to-policies"></a>Używanie blokady zachowywania w celu ograniczenia zmian zasad

Niektóre organizacje mogą wymagać przestrzegania zasad zdefiniowanych przez organy regulacyjne, takie jak reguła 17a-4 Komisji Papierów Wartościowych i Exchange Komisji (SEC), która wymaga, aby po włączeniu zasad przechowywania nie można jej wyłączyć ani zmniejszyć.

Blokada zachowania zapewnia, że organizacja może spełnić takie wymagania prawne, ponieważ blokuje zasady przechowywania lub zasady etykiet przechowywania, dzięki czemu nikt — w tym administrator — nie może wyłączyć zasad, usunąć zasad ani uczynić ich mniej restrykcyjnymi.

Blokadę zachowania stosuje się po utworzeniu zasad przechowywania lub zasad etykiet przechowywania. Aby uzyskać więcej informacji i instrukcji, zobacz [Use Preservation Lock to restrict changes to retention policies and retention label policies (Używanie blokady zachowania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania](retention-preservation-lock.md)).

## <a name="releasing-a-policy-for-retention"></a>Publikowanie zasad przechowywania

Jeśli zasady przechowywania nie mają blokady zachowania, możesz usunąć zasady w dowolnym momencie, co skutecznie wyłącza ustawienia przechowywania dla zasad przechowywania, a etykiety przechowywania nie mogą być już stosowane z zasad etykiet przechowywania. Wszystkie wcześniej zastosowane etykiety przechowywania pozostają ze skonfigurowanymi ustawieniami przechowywania, a dla tych etykiet można zaktualizować okres przechowywania, gdy nie jest on oparty na tym, kiedy elementy zostały oznaczone etykietą.

Można również zachować zasady, ale zmienić stan lokalizacji na wyłączony lub wyłączyć zasady. Inną opcją jest ponowne skonfigurowanie zasad, tak aby nie zawierały już określonych użytkowników, witryn, grup itd.

Dodatkowe informacje dotyczące określonych lokalizacji:

- **SharePoint witryn i kont OneDrive:**

    Po wydaniu zasad przechowywania dla witryn SharePoint i kont OneDrive każda zawartość, która podlega przechowywaniu z zasad, będzie przechowywana przez 30 dni, aby zapobiec przypadkowej utracie danych. W tym 30-dniowym okresie prolongaty usunięte pliki są nadal zachowywane (pliki są nadal dodawane do biblioteki archiwum zachowywania), ale zadanie czasomierza, które okresowo czyści bibliotekę archiwum konserwacji, jest zawieszone dla tych plików, dzięki czemu można je przywrócić w razie potrzeby.

    Wyjątkiem od tego 30-dniowego okresu prolongaty jest aktualizacja zasad w celu wykluczenia co najmniej jednej lokacji dla SharePoint lub kont dla OneDrive. W tym przypadku zadanie czasomierza usuwa pliki dla tych lokalizacji w bibliotece archiwizowania zachowania bez 30-dniowego opóźnienia.

    Aby uzyskać więcej informacji na temat biblioteki Archiwum zachowywania, zobacz [Jak działa przechowywanie dla SharePoint i OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

    Ze względu na zachowanie w okresie prolongaty, jeśli ponownie włączysz zasady lub zmienisz stan lokalizacji z powrotem na w ciągu 30 dni, zasady zostaną wznowione bez trwałej utraty danych w tym czasie.

- **Exchange wiadomości e-mail i Grupy Microsoft 365**

  Po wydaniu zasad przechowywania dla skrzynek pocztowych, które są [nieaktywne](inactive-mailboxes-in-office-365.md) w momencie wydania zasad:

  - Jeśli zasady przechowywania są jawnie stosowane do skrzynki pocztowej, ustawienia przechowywania nie są już stosowane. Bez zastosowania ustawień przechowywania nieaktywna skrzynka pocztowa kwalifikuje się do automatycznego usuwania w zwykły sposób.

    Jawne zasady przechowywania wymagają zakresu zasad adaptacyjnych lub zakresu zasad statycznych z konfiguracją dołączania, która określa aktywną skrzynkę pocztową w momencie stosowania zasad, a później stała się nieaktywna

  - Jeśli zasady przechowywania są niejawnie stosowane do skrzynki pocztowej, a skonfigurowana akcja przechowywania ma zostać zachowana, zasady przechowywania będą nadal stosowane, a nieaktywna skrzynka pocztowa nigdy nie kwalifikuje się do automatycznego usunięcia. Gdy akcja zachowywania nie ma już zastosowania z powodu wygaśnięcia okresu przechowywania, administrator Exchange może teraz [ręcznie usunąć nieaktywną skrzynkę pocztową](delete-an-inactive-mailbox.md)

    Zasady niejawnego przechowywania wymagają statycznego zakresu zasad z konfiguracją **Wszyscy adresaci** (dla Exchange poczty e-mail) lub **Wszystkie grupy** (dla Grupy Microsoft 365).

    Aby uzyskać więcej informacji na temat nieaktywnych skrzynek pocztowych z zastosowanymi zasadami przechowywania, zobacz [Nieaktywne skrzynki pocztowe i przechowywanie Microsoft 365](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-microsoft-365-retention).

## <a name="auditing-retention-configuration-and-actions"></a>Inspekcja konfiguracji przechowywania i akcji

Po [włączeniu inspekcji](turn-audit-log-search-on-or-off.md) zdarzenia inspekcji na potrzeby przechowywania są obsługiwane zarówno w przypadku konfiguracji administracyjnej (zasad przechowywania i etykiet przechowywania) jak i akcji przechowywania (tylko etykiety przechowywania).

### <a name="auditing-retention-configuration"></a>Inspekcja konfiguracji przechowywania

Konfiguracja administratora dla zasad przechowywania i etykiet przechowywania jest rejestrowana jako zdarzenia inspekcji podczas tworzenia, ponownego konfigurowania lub usuwania zasad przechowywania lub etykiet.

Aby uzyskać pełną listę zdarzeń inspekcji, zobacz [Działania dotyczące zasad przechowywania i etykiet przechowywania](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="auditing-retention-actions"></a>Inspekcja akcji przechowywania

Akcje przechowywania rejestrowane jako zdarzenia inspekcji są dostępne tylko dla etykiet przechowywania, a nie dla zasad przechowywania:

- Po zastosowaniu, zmianie lub usunięciu etykiety przechowywania z elementu w SharePoint lub OneDrive:
  - W **obszarze Działania dotyczące plików i stron** wybierz pozycję **Zmieniono etykietę przechowywania dla pliku**

- Gdy element oznaczony etykietą w SharePoint jest oznaczony jako rekord i jest odblokowany lub zablokowany przez użytkownika:
  - W **obszarze Działania dotyczące plików i stron** wybierz pozycję **Zmieniono stan rekordu na odblokowany** i **zmieniono stan rekordu na zablokowany**

- Gdy etykieta przechowywania, która oznacza zawartość jako rekord lub rekord regulacyjny, jest stosowana do elementu w Exchange:
  - Z **Exchange działań skrzynki pocztowej** wybierz pozycję **Wiadomość oznaczona etykietą jako rekord**

- Gdy element oznaczony etykietą w SharePoint, OneDrive lub Exchange jest oznaczony jako rekord lub rekord regulacyjny i jest trwale usuwany:
  - W **obszarze Działania dotyczące plików i stron** wybierz pozycję **Usunięty plik oznaczony jako rekord**

- Gdy recenzent dyspozycji podejmuje akcję dla elementu, który osiągnął koniec okresu przechowywania:
  - Z **obszaru Działania przeglądu dyspozycji** wybierz pozycję **Zatwierdzone usuwanie**, **Przedłużony okres przechowywania**, **Ponownie oznakowany element** lub **Dodano recenzentów**

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Polecenia cmdlet programu PowerShell dla zasad przechowywania i etykiet przechowywania

Aby użyć poleceń cmdlet przechowywania, należy najpierw [nawiązać połączenie z programem PowerShell Office 365 Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell). Następnie użyj dowolnego z następujących poleceń cmdlet:

- [Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)

- [New-ComplianceTag](/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag)

- [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](/powershell/module/exchange/get-compliancetagstorage)

- [Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig)

- [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/set-recordreviewnotificationtemplateconfig)

- [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancerule)

- [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule)

## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Kiedy używać zasad przechowywania i etykiet przechowywania lub blokad zbierania elektronicznych materiałów dowodowych

Mimo że ustawienia przechowywania i [blokady tworzone z przypadkiem zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md) mogą uniemożliwić trwałe usunięcie danych, są one przeznaczone dla różnych scenariuszy. Aby ułatwić zrozumienie różnic i podjęcie decyzji, której użyć, skorzystaj z następujących wskazówek:

- Ustawienia przechowywania określone w zasadach przechowywania i etykietach przechowywania są przeznaczone dla długoterminowej strategii zarządzania cyklem życia danych w celu przechowywania lub usuwania danych w celu spełnienia wymagań dotyczących zgodności. Zakres jest zwykle szeroki, a głównym celem jest lokalizacja i zawartość, a nie poszczególni użytkownicy. Można skonfigurować początek i koniec okresu przechowywania z opcją automatycznego usuwania zawartości bez dodatkowej interwencji administratora.

- Blokady dla przypadków zbierania elektronicznych materiałów dowodowych (eDiscovery (Standard) lub eDiscovery (Premium) są przeznaczone na ograniczony czas trwania w celu zachowania danych na potrzeby dochodzenia prawnego. Zakres jest specyficzny dla zawartości będącej własnością zidentyfikowanych użytkowników. Rozpoczęcie i zakończenie okresu przechowywania nie jest konfigurowalne, ale zależy od poszczególnych akcji administratora bez opcji automatycznego usuwania zawartości po wydaniu blokady.

Podsumowanie, aby porównać przechowywanie z blokadami:

|Kwestie do rozważenia|Przechowywania |Blokady zbierania elektronicznych materiałów dowodowych|
|:-----|:-----|:-----|:-----|
|Potrzeby biznesowe: |Zgodność |Prawnych |
|Zakres czasu: |Długoterminowe |Krótkoterminowych |
|Ostrości: |Szeroka, oparta na zawartości |Specyficzne, oparte na użytkownikach |
|Można skonfigurować datę rozpoczęcia i zakończenia: |Tak |Nie |
|Usuwanie zawartości: |Tak (opcjonalnie) |Nie |
|Koszty administracyjne: |Niskie |High (Wysoki) |

Jeśli zawartość podlega zarówno ustawieniu przechowywania, jak i przechowywaniu zbierania elektronicznych materiałów dowodowych, zachowanie zawartości dla blokady zbierania elektronicznych materiałów dowodowych zawsze ma pierwszeństwo. W ten sposób [zasady przechowywania](#the-principles-of-retention-or-what-takes-precedence) rozszerzają się o blokadę zbierania elektronicznych materiałów dowodowych, ponieważ przechowują dane, dopóki administrator ręcznie nie zwolni blokady. Jednak pomimo tego pierwszeństwa nie używaj funkcji zbierania elektronicznych materiałów dowodowych do długoterminowego zarządzania cyklem życia danych. Jeśli obawiasz się automatycznego usuwania danych, możesz skonfigurować ustawienia przechowywania, aby zachować elementy na zawsze, lub użyć [przeglądu dyspozycji](disposition.md#disposition-reviews) z etykietami przechowywania.

Jeśli używasz starszych narzędzi zbierania elektronicznych materiałów dowodowych do zachowania danych, zobacz następujące zasoby:

- Exchange:
  - [Blokada miejscowa i blokada postępowania sądowego](/exchange/security-and-compliance/in-place-and-litigation-holds)
  - [Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej Exchange Online](./identify-a-hold-on-an-exchange-online-mailbox.md)

- SharePoint i OneDrive:
  - [Dodawanie zawartości do sprawy i umieszczanie źródeł w blokadzie w Centrum zbierania elektronicznych materiałów dowodowych](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Używanie zasad przechowywania i etykiet przechowywania zamiast starszych funkcji

Jeśli chcesz proaktywnie przechowywać lub usuwać zawartość w Microsoft 365 na potrzeby zarządzania cyklem życia danych, zalecamy użycie zasad przechowywania i etykiet przechowywania zamiast następujących starszych funkcji.

Jeśli obecnie używasz tych starszych funkcji, będą one nadal działać równolegle z zasadami przechowywania Microsoft 365 i etykietami przechowywania. Zalecamy jednak, aby w przyszłości używać zasad przechowywania Microsoft 365 i etykiet przechowywania, aby korzystać z jednego rozwiązania do zarządzania przechowywaniem i usuwaniem zawartości w wielu obciążeniach w Microsoft 365.

**Starsze funkcje z Exchange Online:**

- [Tagi przechowywania i zasady przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies), znane również jako [zarządzanie rekordami obsługi komunikatów (MRM) (](/exchange/security-and-compliance/messaging-records-management/messaging-records-management) tylko usuwanie)

  Jeśli jednak używasz następujących funkcji mrm, pamiętaj, że nie są one obecnie obsługiwane przez zasady przechowywania Microsoft 365:

  - Zasady archiwum dla [archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) umożliwiające automatyczne przenoszenie wiadomości e-mail z podstawowej skrzynki pocztowej użytkownika do ich archiwum skrzynki pocztowej po określonym czasie. Zasady archiwum (z dowolnymi ustawieniami) mogą być używane w połączeniu z zasadami przechowywania Microsoft 365, które mają zastosowanie do podstawowej i archiwum skrzynki pocztowej użytkownika.

  - Zasady przechowywania stosowane przez administratora do określonych folderów w skrzynce pocztowej. Zasady przechowywania Microsoft 365 mają zastosowanie do wszystkich folderów w skrzynce pocztowej. Jednak administrator może skonfigurować różne ustawienia przechowywania przy użyciu etykiet przechowywania, które użytkownik może zastosować do folderów w Outlook jako [domyślną etykietę przechowywania](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder).

- [Wstrzymanie postępowania sądowego](create-a-litigation-hold.md) (tylko przechowywanie)

   Mimo że blokady postępowań sądowych są nadal obsługiwane, zalecamy użycie odpowiednio Microsoft 365 przechowywania lub zbierania elektronicznych materiałów dowodowych[.](#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds)

**Starsze funkcje SharePoint i OneDrive:**

- [Zasady usuwania dokumentów](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (tylko usuwanie)

- [Konfigurowanie zarządzania rekordami w miejscu](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (tylko przechowywanie)

- [Używanie zasad do zamykania i usuwania lokacji](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (tylko usunięcie)

- [Zasady zarządzania informacjami](intro-to-info-mgmt-policies.md) (tylko usuwanie)

Jeśli skonfigurowano SharePoint lokacje pod kątem zasad typów zawartości lub zasad zarządzania informacjami w celu zachowania zawartości listy lub biblioteki, zasady te są ignorowane podczas obowiązywania zasad przechowywania.

## <a name="related-information"></a>Informacje pokrewne

- [Limity usługi SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Limity i specyfikacje dla Microsoft Teams](/microsoftteams/limits-specifications-teams) 
- [Zasoby ułatwiające spełnienie wymagań prawnych dotyczących zarządzania cyklem życia danych i zarządzania rekordami](retention-regulatory-requirements.md)

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Zobacz [Wprowadzenie z zarządzaniem cyklem życia danych](get-started-with-data-lifecycle-management.md). Ten artykuł zawiera informacje o subskrypcjach, uprawnieniach i łączach do kompleksowych wskazówek dotyczących konfiguracji scenariuszy przechowywania.
