---
title: Advanced Audit in Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-audit
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Zaawansowana inspekcja Microsoft 365 zapewnia nowe funkcje inspekcji, które pomagają organizacji w badaniach prawnych i zgodności.
ms.openlocfilehash: 4a378071a59d2462cff1af5b87f9ab99d1e1337f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032119"
---
# <a name="advanced-audit-in-microsoft-365"></a>Advanced Audit in Microsoft 365

Funkcja [inspekcji w programie](search-the-audit-log-in-security-and-compliance.md) Microsoft 365 zapewnia organizacjom wgląd w wiele typów działań pod kontrolą w wielu różnych usługach w różnych Microsoft 365. Zaawansowana inspekcja ułatwia organizacjom przeprowadzanie analiz prawnych i zgodności, zwiększając liczbę działań w dzienniku inspekcji wymaganym do przeprowadzenia badania, zapewniając dostęp do ważnych zdarzeń (za pomocą przeszukiwania dziennika inspekcji w p programie Centrum zgodności platformy Microsoft 365 i interfejsu API działań zarządzania programu Office 365), które pomagają w określeniu zakresu naruszenia bezpieczeństwa i szybszego dostępu aby Office 365 interfejs API działań zarządzania.

> [!NOTE]
> Inspekcja zaawansowana jest dostępna dla organizacji z subskrypcją usługi Office 365 E5/A5/G5 lub Microsoft 365 Enterprise E5/A5/G5. Użytkownikom należy przypisać licencje na funkcje zgodności Microsoft 365 E5/A5/G5 lub Zbierania elektronicznych materiałów dowodowych E5/A5/G5 i dodatki inspekcji na funkcje zaawansowanej inspekcji, takie jak długoterminowe przechowywanie dzienników inspekcji i generowanie zdarzeń inspekcji zaawansowanej w przypadku badań. Aby uzyskać więcej informacji na temat licencjonowania, zobacz:<br/>- [Zaawansowane wymagania dotyczące licencjonowania inspekcji](auditing-solutions-overview.md#licensing-requirements)<br/>- [Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

W tym artykule opisano funkcje zaawansowanej inspekcji i przedstawiono sposób skonfigurowania użytkowników do inspekcji zaawansowanej.

## <a name="long-term-retention-of-audit-logs"></a>Długoterminowe przechowywanie dzienników inspekcji

W ramach inspekcji zaawansowanej Exchange, SharePoint i Azure Active Directory rekordy inspekcji przez jeden rok. Jest **Exchange**, **SharePoint** lub **AzureActiveDirectory** dla właściwości **Workload** (co wskazuje usługę, w której wystąpiło działanie) przez jeden rok, przy użyciu domyślnych zasad przechowywania dziennika inspekcji. Zachowywanie rekordów inspekcji przez dłuższy czas może być pomocne w przypadku toczyjących się dochodzeniach prawnych lub dotyczących zgodności. Aby uzyskać więcej informacji, zobacz sekcję "Domyślne zasady przechowywania dziennika inspekcji" w tece [Zarządzanie zasadami przechowywania dziennika inspekcji](audit-log-retention-policies.md#default-audit-log-retention-policy).

Poza możliwościami przechowywania w ramach jednego roku w ramach inspekcji zaawansowanej opublikowano również możliwość przechowywania dzienników inspekcji przez 10 lat. 10-letnia przechowywanie dzienników inspekcji ułatwia obsługę długo prowadzonych badań oraz reagowanie na zobowiązania prawne, prawne i wewnętrzne.

> [!NOTE]
> Zachowywanie dzienników inspekcji przez 10 lat będzie wymagać dodatkowej licencji na użytkownika. Po przypisaniu tej licencji do użytkownika i skonfigurowaniu dla tego użytkownika odpowiednich 10-letniego zasad przechowywania dziennika inspekcji dzienniki inspekcji objęte tym zasadami zaczną być zachowywane przez 10-letni okres. Te zasady nie są wstecz aktywowane i nie mogą zachowywać dzienników inspekcji wygenerowanych przed utworzeniami 10-letniego dziennika inspekcji. Aby uzyskać więcej informacji, zobacz sekcję [Często zadawane pytania dotyczące inspekcji](#faqs-for-advanced-audit) zaawansowanej w tym artykule.

### <a name="audit-log-retention-policies"></a>Zasady przechowywania dziennika inspekcji

Wszystkie rekordy inspekcji wygenerowane w innych usługach, które nie są objęte domyślnymi zasadami przechowywania dziennika inspekcji (opisanymi w poprzedniej sekcji), są zachowywane przez 90 dni. Można jednak utworzyć niestandardowe zasady przechowywania dziennika inspekcji, aby przechowywać inne rekordy inspekcji przez dłuższy czas do 10 lat. Można utworzyć zasady zachowywania rekordów inspekcji na podstawie co najmniej jednego z następujących kryteriów:

- Usługa Microsoft 365, w której mają miejsce działania pod kontrolą.

- Określone działania pod kontrolą.

- Użytkownik, który wykonuje działania inspekcji.

Możesz także określić, jak długo mają być zachowywane rekordy inspekcji zgodne z zasadami i poziom priorytetu, dzięki czemu określone zasady będą mieć priorytet nad innymi zasadami. Należy również pamiętać Azure Active Directory, że wszelkie niestandardowe zasady przechowywania dziennika inspekcji mają pierwszeństwo przed domyślnymi zasadami przechowywania inspekcji, jeśli trzeba zachować rekordy inspekcji przez okres krótszy niż rok (lub przez 10 lat) dla niektórych lub wszystkich użytkowników w organizacji. SharePoint Exchange Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami przechowywania dziennika inspekcji](audit-log-retention-policies.md).

## <a name="advanced-audit-events"></a>Zaawansowane zdarzenia inspekcji

Zaawansowana inspekcja ułatwia organizacjom prowadzenie analiz prawnych i zgodności przez zapewnianie dostępu do ważnych zdarzeń, takich jak uzyskiwanie dostępu do elementów poczty, odpowiadanie na elementy poczty i przesyłanie ich dalej oraz kiedy i co użytkownik wyszukiwał w usługach Exchange Online i SharePoint Online. Zdarzenia te mogą pomóc w zbadaniu możliwych naruszeń zabezpieczeń i określeniu zakresu naruszenia. Oprócz tych zdarzeń w usługach Exchange i SharePoint istnieją zdarzenia w innych usługach Microsoft 365, które są uznawane za ważne zdarzenia i wymagają przypisania użytkownikom odpowiedniej licencji inspekcji [zaawansowanej](auditing-solutions-overview.md#licensing-requirements). Użytkownicy muszą mieć przypisaną licencję zaawansowanej inspekcji, aby dzienniki inspekcji były generowane podczas wykonywania tych zdarzeń.

W ramach inspekcji zaawansowanej są następujące zdarzenia:

- [MailItemsAccessed](#mailitemsaccessed)

- [Wyślij](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [Inne zdarzenia inspekcji zaawansowanej w programie Microsoft 365](#other-advanced-audit-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

Zdarzenie MailItemsAccessed jest akcją inspekcji skrzynki pocztowej i jest wyzwalane, gdy dane poczty są uzyskiwane przez protokoły poczty i klientów poczty. To zdarzenie może pomóc w zidentyfikowaniu naruszeń danych i określeniu zakresu wiadomości, które mogą być naruszone. Jeśli atakujący uzyskał dostęp do wiadomości e-mail, zostanie wyzwolona akcja MailItemsAccessed, nawet jeśli nie ma jawnego sygnału, że wiadomości zostały odczytane (to oznacza, że w rekordzie inspekcji jest rejestrowany typ dostępu, taki jak powiązanie lub synchronizacja).

Zdarzenie MailItemsAccessed zastępuje zdarzenie MessageBind w rejestrowaniu inspekcji skrzynki pocztowej w programie Exchange Online i udostępnia następujące ulepszenia:

- Ustawienie MessageBind można konfigurować tylko dla typu logowania użytkownika AuditAdmin. nie dotyczyło działań pełnomocnika ani właściciela. MailItemsAccessed dotyczy wszystkich typów logowania.

- Tekst MessageBind obejmuje tylko dostęp klienta poczty. Nie dotyczyło to działań synchronizacji. Zdarzenia MailItemsAccessed są wyzwalane przez zarówno powiązanie, jak i synchronizowanie typów dostępu.

- Działania funkcji MessageBind wyzwoliły tworzenie wielu rekordów inspekcji, gdy uzyskano dostęp do tej samej wiadomości e-mail, w wyniku czego inspekcja spowodowała "szum". Natomiast zdarzenia MailItemsAccessed są agregowane w mniej rekordów inspekcji.

Aby uzyskać informacje na temat rekordów inspekcji dla działań w programie MailItemsAccessed, zobacz Badanie naruszonych kont za pomocą inspekcji [zaawansowanej](mailitemsaccessed-forensics-investigations.md).

Aby wyszukać rekordy inspekcji typu MailItemsAccessed, możesz wyszukać działanie Dostępne elementy  skrzynki pocztowej na liście rozwijanej działań skrzynki pocztowej programu **Exchange** w narzędziu do przeszukiwania dziennika inspekcji w Centrum zgodności platformy Microsoft 365.[](search-the-audit-log-in-security-and-compliance.md)

![Wyszukiwanie akcji MailItemsAccessed w narzędziu do przeszukiwania dziennika inspekcji.](../media/AdvAudit_MailItemsAccessed.png)

W programie Exchange Online PowerShell można także uruchomić polecenia [Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) lub [Search-MailboxAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-mailboxauditlog).

### <a name="send"></a>Wyślij

Zdarzenie Send jest również akcją inspekcji skrzynki pocztowej i jest wyzwalane, gdy użytkownik wykonuje jedną z następujących akcji:

- Wysyła wiadomość e-mail

- Odpowiedzi na wiadomość e-mail

- Przesyłanie dalej wiadomości e-mail

Wsady mogą używać zdarzenia Wyślij do identyfikowania wiadomości e-mail wysłanych z naruszonego konta. Rekord inspekcji dla zdarzenia Send zawiera informacje o wiadomości, takie jak czas wysłania wiadomości, identyfikator InternetMessage, wiersz tematu i czy wiadomość zawierała załączniki. Te informacje inspekcji mogą ułatwić współpracownikom zidentyfikowanie informacji o wiadomościach e-mail wysyłanych z naruszonego konta lub wysyłanych przez atakującego. Ponadto słowy mogą używać narzędzia zbierania elektronicznych materiałów dowodowych usługi Microsoft 365 do wyszukiwania wiadomości (za pomocą wiersza tematu lub identyfikatora wiadomości) w celu zidentyfikowania adresatów, do których wysłano wiadomość, oraz rzeczywistej zawartości wysłanej wiadomości.

Aby wyszukać pole Wyślij rekordy inspekcji, możesz wyszukać działanie Wysłano  wiadomość na liście rozwijanej działania skrzynki pocztowej programu **Exchange** w narzędziu przeszukiwania [](search-the-audit-log-in-security-and-compliance.md) dziennika inspekcji w Centrum zgodności platformy Microsoft 365.

![Wyszukiwanie akcji wysłanych wiadomości w narzędziu do przeszukiwania dziennika inspekcji.](../media/AdvAudit_SentMessage.png)

W programie Exchange Online PowerShell można również uruchomić polecenia [wysyłania -Operations search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) lub [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog).

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

Zdarzenie SearchQueryInitiatedExchange jest wyzwalane, gdy osoba Outlook wyszukuje elementy w skrzynce pocztowej. Zdarzenia są wyzwalane podczas wyszukiwania w następujących Outlook środowiskach:

- Outlook (klient klasyczny)

- Outlook w sieci Web (OWA)

- Outlook dla systemu iOS

- Outlook dla systemu Android

- Aplikacja Poczta dla Windows 10

W celu ustalenia, czy atakujący, który mógł naruszyć konto w skrzynce pocztowej lub próbował uzyskać dostęp do poufnych informacji, może użyć zdarzenia SearchQueryInitiatedExchange. Rekord inspekcji zdarzenia SearchQueryInitiatedExchange zawiera informacje, takie jak rzeczywisty tekst zapytania wyszukiwania. Rekord inspekcji wskazuje również środowisko Outlook, w którym zostało przeprowadzone wyszukiwanie. Patrząc na zapytania wyszukiwania przeprowadzone przez atakującego, może on lepiej zrozumieć cel wyszukiwanych danych e-mail.

Aby wyszukać rekordy inspekcji SearchQueryInitiatedExchange, możesz wyszukać działanie wyszukiwania wykonanej  poczty e-mail na liście  rozwijanej Działania wyszukiwania w narzędziu przeszukiwania dziennika inspekcji w Centrum zgodności.[](search-the-audit-log-in-security-and-compliance.md)

![Wyszukiwanie działań wyszukiwania wykonanej poczty e-mail w narzędziu do przeszukiwania dziennika inspekcji.](../media/AdvAudit_SearchExchange.png)

Można również uruchomić zapytanie [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online PowerShell.

> [!NOTE]
> Aby wyszukać to zdarzenie w dzienniku inspekcji, należy włączyć funkcję SearchQueryInitiatedExchange. Aby uzyskać instrukcje, [zobacz Konfigurowanie inspekcji zaawansowanej](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

Podobnie jak w przypadku wyszukiwania elementów skrzynki pocztowej zdarzenie SearchQueryInitiatedSharePoint jest wyzwalane, gdy osoba wyszukuje elementy w SharePoint. Zdarzenia są wyzwalane podczas wyszukiwania na stronie głównej lub domyślnej następujących typów witryn SharePoint witryny:

- Witryny domowe

- Witryny do komunikacji

- Witryny centrum

- Witryny skojarzone z witrynami Microsoft Teams

Wsady mogą użyć zdarzenia SearchQueryInitiatedSharePoint w celu określenia, czy atakujący próbował znaleźć (i być może uzyskał dostęp) informacje poufne w SharePoint. Rekord inspekcji dla zdarzenia SearchQueryInitiatedSharePoint zawiera również rzeczywisty tekst zapytania wyszukiwania. Rekord inspekcji wskazuje również typ przeszukanej SharePoint witryny. Patrząc na zapytania wyszukiwania przeprowadzone przez atakującego, może on lepiej zrozumieć cel i zakres wyszukiwanych danych.

Aby wyszukać rekordy inspekcji searchQueryInitiatedSharePoint, możesz **wyszukać** działanie wyszukiwania Wykonane SharePoint na liście rozwijanej Działania wyszukiwania w narzędziu  przeszukiwania dziennika inspekcji w Centrum zgodności.[](search-the-audit-log-in-security-and-compliance.md)

![Wyszukiwanie wykonane SharePoint w narzędziu do przeszukiwania dziennika inspekcji.](../media/AdvAudit_SearchSharePoint.png)

Możesz również uruchomić zapytanie [Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online PowerShell.

> [!NOTE]
> Aby wyszukać to zdarzenie w dzienniku inspekcji, należy włączyć rejestrowanie dla zapytania SearchQueryInitiatedSharePoint. Aby uzyskać instrukcje, [zobacz Konfigurowanie inspekcji zaawansowanej](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="other-advanced-audit-events-in-microsoft-365"></a>Inne zdarzenia inspekcji zaawansowanej w programie Microsoft 365

Oprócz zdarzeń w usługach Exchange Online i SharePoint Online istnieją zdarzenia w innych usługach Microsoft 365, które są rejestrowane, gdy użytkownikom zostanie przypisane odpowiednie licencjonowanie zaawansowanej inspekcji. Poniższe Microsoft 365 zapewniają zdarzenia inspekcji zaawansowanej. Wybierz odpowiedni link, aby przejść do artykułu, który identyfikuje i opisuje te zdarzenia.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Dostęp o wysokiej przepustowości do interfejsu API Office 365 zarządzania

Organizacje, które mają dostęp do dzienników inspekcji za pośrednictwem interfejsu API działań zarządzania Office 365 zarządzania zostały ograniczone przez ograniczenie limitów na poziomie wydawcy. Oznacza to, że w przypadku wydawcy, który wyciąga dane w imieniu wielu klientów, limit ten został udostępniony przez wszystkich tych klientów.

Wraz z wydaniem inspekcji zaawansowanej przenosimy się z limitu na poziomie wydawcy do limitu na poziomie dzierżawy. W efekcie każda organizacja otrzyma swój własny, w pełni przydzielony przydział przepustowości na dostęp do danych inspekcji. Przepustowość nie jest statycznym, wstępnie zdefiniowanym limitem, ale jest modelowana na kombinacji czynników, takich jak liczba stanowisk w organizacji i że organizacje E5/A5/G5 uzyskają więcej przepustowości niż organizacje inne niż E5/A5/G5.

Wszystkie organizacje wstępnie mają przypisany plan bazowy 2000 wniosków na minutę. Ten limit zostanie dynamicznie zwiększany w zależności od liczby miejsc w organizacji i subskrypcji licencjonowania. Organizacje E5/A5/G5 uzyskają przepustowość o około dwa razy większą przepustowość niż organizacje inne niż E5/A5/G5. Zostaną także limity maksymalnej przepustowości w celu ochrony kondycji usługi.

Aby uzyskać więcej informacji, zobacz sekcję "Ograniczanie interfejsu API" w te [Office 365 informacji dotyczących interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-advanced-audit"></a>Często zadawane pytania dotyczące inspekcji zaawansowanej

**Czy każdy użytkownik potrzebuje licencji E5/A5/G5, aby korzystać z zalet inspekcji zaawansowanej?**

Aby można było korzystać z zaawansowanych funkcji inspekcji na poziomie użytkownika, należy przypisać użytkownikowi licencję E5/A5/G5. Istnieją pewne funkcje, które będą sprawdzać, czy jest dostępna odpowiednia licencja w celu udostępnienia funkcji dla użytkownika. Jeśli na przykład próbujesz zachować rekordy inspekcji dla użytkownika, który nie przypisał odpowiedniej licencji dłużej niż 90 dni, system zwróci komunikat o błędzie.

**Moja organizacja ma subskrypcję E5/A5/G5. Czy muszę cokolwiek robić, aby uzyskać dostęp do rekordów inspekcji w przypadku zdarzeń zaawansowanej inspekcji?**

W przypadku kwalifikujących się klientów i użytkowników, którzy mają przypisaną odpowiednią licencję E5/A5/G5, nie trzeba nic zrobić, aby uzyskać dostęp do zdarzeń zaawansowanej inspekcji, z wyjątkiem zdarzeń SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint (jak opisano wcześniej w tym artykule). Po przypisaniu tych licencji zdarzenia inspekcji zaawansowanej będą generowane tylko dla użytkowników z licencjami E5/A5/G5.

**Czy nowe zdarzenia w ramach inspekcji zaawansowanej są dostępne w interfejsie API Office 365 zarządzania?**

Tak. Dopóki rekordy inspekcji zostaną wygenerowane dla użytkowników z odpowiednią licencją, będzie można uzyskać do nich dostęp za pomocą interfejsu API działań zarządzania Office 365 zarządzaniem.

**Co stanie się z danymi dziennika inspekcji mojej organizacji, jeśli utworzyę 10-latowe zasady przechowywania dziennika inspekcji, gdy funkcja zostanie opublikowana w ogólno dostępnej wersji, ale przed dostępnością wymaganej licencji dodatku?**

Wszelkie dane dziennika inspekcji objęte 10-rokiem zasady przechowywania dziennika inspekcji utworzone po zwolnieniu funkcji w ogólną dostępność w ostatnim kwartale 2020 r. będą przechowywane przez 10 lat. Obejmuje to 10-latowe zasady przechowywania dziennika inspekcji, które utworzono przed wydano wymaganą licencją dodatku w celu zakupu w marcu 2021 r. Jednak ponieważ jest teraz dostępna 10-letnia licencja przechowywania dziennika inspekcji — Dodaj, musisz kupić i przypisać te licencje dodatków wszystkim użytkownikom, których dane inspekcji są objęte 10-letnią zasadą przechowywania inspekcji.
