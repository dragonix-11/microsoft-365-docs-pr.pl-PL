---
title: Wycofano starsze narzędzia zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place eDiscovery i In-Place Hold (oraz odpowiednie polecenia cmdlet programu PowerShell) w Exchange Online zostaną wycofane w pierwszej połowie 2020 r. Polecenie cmdlet Search-Mailbox i microsoft Purview eDiscovery (Premium) w wersji 1.0 są również wycofywane w tym samym okresie.
ms.openlocfilehash: 367b020a5804ac120f226962ea48a49b73dd70e6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094487"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> Funkcjonalność starszych narzędzi zbierania elektronicznych materiałów dowodowych opisanych w tym artykule została usunięta z usługi Microsoft 365 lub nadal jest dostępna, ale nie jest już obsługiwana. Wszystkie funkcje, które są nadal dostępne, mogą zostać usunięte bez powiadomienia. Jeśli nadal używasz żadnego z tych starszych narzędzi, rozważ migrację do narzędzi zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview lub jednej z alternatyw opisanych w tym artykule.

Przez lata firma Microsoft udostępniała narzędzia zbierania elektronicznych materiałów dowodowych, które umożliwiają wyszukiwanie, wyświetlanie podglądu i eksportowanie zawartości wiadomości e-mail z Exchange Online. Jednak te narzędzia nie oferują już skutecznego sposobu wyszukiwania zawartości bez Exchange w innych usługach Microsoft 365, takich jak SharePoint Online i Grupy Microsoft 365. Aby rozwiązać ten problem, firma Microsoft oferuje inne narzędzia zbierania elektronicznych materiałów dowodowych, które ułatwiają wyszukiwanie szerokiej gamy zawartości Microsoft 365. Ciężko pracowaliśmy nad uwzględnieniem najbardziej aktualnych i zaawansowanych funkcji zbierania elektronicznych materiałów dowodowych w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a>. Dzięki temu organizacje mogą odpowiadać na żądania prawne, wewnętrzne i inne żądania dokumentów dotyczące zawartości w wielu usługach Microsoft 365, w tym Exchange Online.

W wyniku tej nowej i ulepszonej funkcji zbierania elektronicznych materiałów dowodowych w portalu zgodności wycofujemy następujące funkcje i funkcje związane zbierania elektronicznych materiałów dowodowych związane z wyszukiwaniem zawartości wiadomości e-mail w Exchange Online i Microsoft 365:

- [W miejscu eDiscovery](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) i [In-Place Holds](/exchange/security-and-compliance/create-or-remove-in-place-holds) w centrum administracyjnym Exchange.

- Polecenia cmdlet programu PowerShell Exchange Online obsługujące In-Place eDiscovery i In-Place Holds (te polecenia cmdlet są wspólnie identyfikowane jako polecenia cmdlet **-MailboxSearch*). Obejmuje to następujące polecenia cmdlet:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Polecenia cmdlet [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) i [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) będą dostępne po tym, jak inne polecenia cmdlet ****-MailboxSearch*** zostaną wycofane, aby ułatwić przejście na inne narzędzia do zbierania elektronicznych materiałów dowodowych i przechowywania. Jednak po określonej dacie (przytoczonej poniżej) pomoc techniczna firmy Microsoft nie będzie już obsługiwać tych dwóch poleceń cmdlet.

- Polecenie cmdlet [Search-Mailbox](/powershell/module/exchange/search-mailbox) w programie Exchange Online programu PowerShell.

- Następujące operacje w interfejsie API usług sieci Web Exchange:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Microsoft Purview eDiscovery (Premium) v1.0](./overview-ediscovery-20.md), czyli pierwsza wersja zbierania elektronicznych materiałów dowodowych (Premium), do której uzyskuje się dostęp za pośrednictwem sprawy zbierania elektronicznych materiałów dowodowych usługi Microsoft Purview (Standard) w portalu zgodności. Wycofanie z funkcji zbierania elektronicznych materiałów dowodowych (Premium) w wersji 1.0 nie ma wpływu na możliwość tworzenia przypadków zbierania elektronicznych materiałów dowodowych (standardowych) i zarządzania nimi.

> [!NOTE]
> Wycofywana funkcja zbierania elektronicznych materiałów dowodowych ma zastosowanie tylko do opartych na chmurze wersji Microsoft 365 i Office 365. Funkcje zbierania elektronicznych materiałów dowodowych w lokalnych wersjach Exchange i SharePoint będą nadal obsługiwane do odwołania.

Poniższe sekcje w tym artykule zawierają wskazówki dotyczące wycofywania każdej funkcji. Te informacje obejmują osie czasu i narzędzia alternatywne, których można użyć zamiast wycofanego narzędzia.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery i In-Place Holds w centrum administracyjnym Exchange 

Zgodnie z pierwotnym ogłoszeniem z 1 lipca 2017 r. funkcja In-Place eDiscovery & Hold w centrum administracyjnym Exchange (EAC) jest wycofywana. Strona In-Place eDiscovery & Holds w usłudze EAC umożliwia wyszukiwanie, archiwizowanie i eksportowanie zawartości z Exchange Online. In-Place zbierania elektronicznych materiałów dowodowych umożliwia również kopiowanie wyników wyszukiwania do skrzynki pocztowej odnajdywania, aby ty lub inni menedżerowie zbierania elektronicznych materiałów dowodowych mogli przeglądać zawartość i udostępniać je na potrzeby żądań prawnych, regulacyjnych i publicznych.

Ponieważ wszystkie te możliwości (z wyjątkiem kopiowania wyników wyszukiwania do skrzynki pocztowej odnajdywania) są teraz dostępne w narzędziach wyszukiwania zawartości, zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych (Premium) w [portalu zgodności](./microsoft-365-compliance-center.md) (z ulepszoną funkcjonalnością, niezawodnością i obsługą szerokiej gamy usług Microsoft 365), zalecamy jak najszybsze rozpoczęcie korzystania z tych narzędzi. Aby ułatwić przejście do innych narzędzi zbierania elektronicznych materiałów dowodowych, poniższa tabela zawiera listę narzędzi, których można użyć zamiast In-Place eDiscovery i In-Place Hold.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których dotyczy problem

- organizacje Office 365 i Microsoft 365 Enterprise

- organizacje Office 365 i Microsoft 365 Education

- Office 365 i Microsoft 365 organizacji rządowych; obejmuje to GCC, GCC High i DoD

- Office 365 Niemcy

### <a name="timeline-for-retirement"></a>Oś czasu wycofania

- 1 lipca 2020 r.: Nie będzie można tworzyć nowych wyszukiwań i blokad, ale nadal możesz uruchamiać, edytować i usuwać istniejące wyszukiwania na własne ryzyko. pomoc techniczna firmy Microsoft nie będzie już In-Place zbierania elektronicznych materiałów dowodowych & blokad w eac.

- 1 października 2020 r.: funkcja In-Place eDiscovery & Holds w usłudze EAC zostanie umieszczona w trybie tylko do odczytu. Oznacza to, że będziesz mieć możliwość usunięcia tylko istniejących wyszukiwań i blokad.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, których można użyć do zastąpienia istniejących funkcji, które są wycofywane.

<table>
<thead>
<tr class="header">
<th>Funkcje</th>
<th>Narzędzie alternatywne</th>
<th>Komentarze</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Wyszukiwanie, eksportowanie i archiwizowanie do celów prawnych</td>
<td>Przypadki zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) w portalu zgodności </td>
<td><p>Korzystanie z możliwości przypadków zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) zapewnia równoważność funkcjonalną do In-Place zbierania elektronicznych materiałów dowodowych i In-Place blokad. Obejmuje to następujące elementy:</p>
<ul>
<li>
<p>Wyszukiwanie jest skalowane do milionów lokalizacji</p>
</li>
<li>
<p>Większa niezawodność wyszukiwania, eksportowania i umieszczania zawartości w zawieszeniu</p>
</li>
<li>
<p>Wyszukiwanie zawartości w Exchange Online, SharePoint Online, OneDrive dla Firm, Skype dla firm, Microsoft Teams, grupach Yammer, Grupy Microsoft 365 i innej zawartości przechowywanej w aplikacjach Office 365</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Przechowywanie do celów przechowywania</td>
<td>Zasady przechowywania w portalu zgodności</td>
<td><p>Zasady przechowywania umożliwiają zachowanie zawartości i, w razie potrzeby, usunięcie jej po upływie okresu przechowywania. Inne możliwości obejmują:</p>
<ul>
<li>
<p>Stosowanie zasad do całej organizacji </p>
</li><li>
<p>Stosowanie zasad do określonych lokalizacji zawartości, takich jak Exchange Online, SharePoint Online, OneDrive dla Firm, Skype dla firm, Microsoft Teams i grupy Office 365</p></li>
<li>
<p>Stosowanie zasad do określonych użytkowników</p></li></ul>
<p>Aby uzyskać więcej informacji, zobacz <a href="/microsoft-365/compliance/retention-policies"> Informacje o zasadach przechowywania i etykietach przechowywania</a>.</td>
</tr>
<tr class="odd">
<td>Kopiowanie wyników wyszukiwania wiadomości e-mail do skrzynki pocztowej odnajdywania w celu sprawdzenia</td><td>Zestawy przeglądów w systemie zbierania elektronicznych materiałów dowodowych (Premium) w wersji 2.0</td>
<td><p>Przeglądanie zawartości w Microsoft 365 nigdy nie było łatwiejsze. Zestawy przeglądów mają wiele doskonałych możliwości, które ułatwiają skrócenie czasu i ilości danych potrzebnych do przeglądu, w tym:</p>
<ul>
<li><p>Wykonywanie szybkich zapytań wyszukiwania i filtrowanie zawartości w zestawie przeglądów</p></li>
<li><p>Analizowanie zawartości w zestawie przeglądów; obejmuje to wątki wiadomości e-mail, wykrywanie niemal duplikatów, analizę motywów i kodowanie predykcyjne</p></li>
<li><p>Taguj dokumenty w zestawie do przeglądu</p></li>
<li><p>Tagowanie sugestii ułatwiających identyfikację zawartości uprawnień klienta adwokata</p></li></ul>
<p>Aby uzyskać więcej informacji, zobacz <a href="/microsoft-365/compliance/overview-ediscovery-20">Omówienie rozwiązania zbierania elektronicznych materiałów dowodowych (Premium) w Microsoft 365</a>.</p>
<p>
<p>Możesz też wyeksportować wyniki wyszukiwania do plików PST, a następnie użyć usługi Microsoft 365 Import do zaimportowania pst do skrzynki pocztowej odnajdywania. Aby uzyskać instrukcje krok po kroku, zobacz <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">Używanie przekazywania sieci do importowania plików PST do Office 365</a>.
</tr>
<tr class=even>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby udzielić osobie dostępu do poczty e-mail innego użytkownika (na przykład gdy pracownik opuszcza organizację i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, przypisz użytkownikowi uprawnienia niezbędne do uzyskania dostępu do źródłowej skrzynki pocztowej.</td>
  
  </tr>
<tr class="odd">
<td>Przywracanie elementów z folderu Elementy możliwe do odzyskania</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>W skrzynkach pocztowych można przywrócić trwale usunięte elementy (nazywane również elementami <i>nietrwałymi</i> ), o ile usunięty okres przechowywania elementu nie wygasł. Aby uzyskać więcej informacji, zobacz <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">Folder Elementy do odzyskania w Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>Często zadawane pytania dotyczące In-Place zbierania elektronicznych materiałów dowodowych i blokad In-Place

**Używam funkcji kopiowania wyników wyszukiwania In-Place eDiscovery & Holds w eac do kopiowania wyników wyszukiwania do skrzynki pocztowej odnajdywania do przeglądu przez prawników. Jakie opcje mam teraz?**

Obecnie istnieją dwa sposoby replikacji tej funkcji. Pierwszym z nich jest użycie [zestawów przeglądów w systemie eDiscovery (Premium) w wersji 2.0](./view-documents-in-review-set.md). Zestawy przeglądów mają wiele takich samych możliwości, jakie można zobaczyć w tradycyjnym narzędziu do przeglądu, takich jak szybkie wyszukiwanie dokumentów, tagowanie, wątki wiadomości e-mail, niemal zduplikowane grupowanie, analiza motywów i kodowanie predykcyjne. Jeśli nadal chcesz używać skrzynek pocztowych odnajdywania do przeglądu, drugą opcją jest wyeksportowanie wyników wyszukiwania do plików PST, a następnie zaimportowanie plików PST do skrzynki pocztowej odnajdywania przy użyciu [funkcji importowania PST](use-network-upload-to-import-pst-files.md) w Centrum zgodności firmy Microsoft.

**Jak mogę kontrolować lokalizacje zawartości (takie jak skrzynki pocztowe lub witryny), które mogą być wyszukiwane przez menedżera zbierania elektronicznych materiałów dowodowych przy użyciu nowych narzędzi?**

Portal zgodności używa również [granic zgodności](set-up-compliance-boundaries.md) do kontrolowania lokalizacji zawartości, które może przeszukiwać menedżer zbierania elektronicznych materiałów dowodowych. Granice zgodności są przydatne w jednostkach rządowych, które muszą pozostać w granicach agencji lub w korporacjach wielonarodowych wymaganych do poszanowania zarządców geograficznych.

**Jak mogę przenieść bieżące wyszukiwania i blokady do portalu zgodności usługi Microsoft Purview?**

Za pomocą programu PowerShell można migrować In-Place wyszukiwania zbierania elektronicznych materiałów dowodowych i blokad z usługi EAC. Aby uzyskać [instrukcje, zobacz Migrate searches and holds from the EAC to the compliance portal (Migrowanie wyszukiwań i blokad z eac do portalu zgodności](./migrate-legacy-ediscovery-searches-and-holds.md)).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch polecenia cmdlet

Zgodnie z pierwotnym zawiadomieniem ogłoszonym 1 lipca 2017 r. w centrum administracyjnym Exchange funkcje In-Place eDiscovery & Hold i odpowiednie **\*polecenia cmdlet -MailboxSearch** są wycofywane. Te polecenia cmdlet zapewniają użytkownikom możliwość wyszukiwania, przechowywania i eksportowania zawartości skrzynki pocztowej na potrzeby żądań prawnych, regulacyjnych i publicznych.

Ponieważ te możliwości są teraz dostępne w [<span class="underline">portalu zgodności</span>](./microsoft-365-compliance-center.md) i programie PowerShell Office 365 Security & Compliance Center z lepszą wydajnością i skalowalnością, należy użyć tych ulepszonych poleceń cmdlet. Te polecenia cmdlet obejmują [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) i [<span class="underline">\*-ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których dotyczy problem

- organizacje Office 365 i Microsoft 365 Enterprise

- organizacje Office 365 i Microsoft 365 Education

- Office 365 i Microsoft 365 organizacji rządowych; obejmuje to GCC, GCC High i DoD

- Office 365 Niemcy

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Nie będzie można używać polecenia **New-MailboxSearch** do tworzenia nowych In-Place wyszukiwania zbierania elektronicznych materiałów dowodowych i In-Place Blokady, ale nadal możesz używać poleceń cmdlet do uruchamiania, edytowania i usuwania istniejących wyszukiwań i blokad na własne ryzyko. pomoc techniczna firmy Microsoft nie będzie już udzielać pomocy dla tego typu wyszukiwań i blokad.

- 1 października 2020 r.: Jak wspomniano wcześniej, funkcja In-Place eDiscovery & Holds w eac zostanie umieszczona w trybie tylko do odczytu. Oznacza to również, że nie będzie można używać poleceń cmdlet **New-MailboxSearch**, **Start-MailboxSearch** ani **Set-MailboxSearch** . Będzie można pobierać i usuwać tylko istniejące wyszukiwania i blokady.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, których można użyć do zastąpienia istniejących funkcji, które są wycofywane.

<table>
<thead>
<tr class="header">
<th>Funkcje</th>
<th>Narzędzia alternatywne</th>
<th>Komentarze</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Wyszukiwanie i eksportowanie</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Polecenia cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić wyszukiwanie i eksportowanie zawartości. Możesz utworzyć nowe wyszukiwanie i wyświetlić oszacowanie wyszukiwania przy użyciu poleceń cmdlet <strong>New-</strong>, <strong>Get-i Start-ComplianceSearch</strong>. <strong></strong> Następnie możesz użyć polecenia cmdlet <strong>New-ComplianceSearchAction</strong> , aby wyeksportować wyniki wyszukiwania. Nadal będziesz musiał użyć narzędzia eDiscovery (Standard) w portalu zgodności, aby pobrać te wyniki wyszukiwania na komputer lokalny.</p>
<p>
<p><strong>Uwaga:</strong> Jeśli użyjesz tych poleceń cmdlet do tworzenia wyszukiwań, które nie są skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa), te wyszukiwania będą znajdować się na stronie <strong>wyszukiwania zawartości</strong> w portalu zgodności.</p></td>
</tr>
<tr class="even">
<td>Przechowuj zawartość w skrzynce pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Blokady w portalu zgodności muszą być skojarzone z elementem ComplianceCase. Najpierw utwórz przypadek zgodności, a następnie utwórz argument CaseHoldPolicy i CaseHoldRule.</p>
<p><strong>Uwaga:</strong> Utworzenie obiektu CaseHoldPolicy bez utworzenia elementu CaseHoldRule spowoduje, że blokada będzie niedziałać do momentu utworzenia i skojarzenia elementu CaseHoldRule z zasadą CaseHoldPolicy. Aby uzyskać więcej informacji, zobacz dokumentację polecenia cmdlet.</p></td>
</tr>
<tr class="odd">
<td>Kopiowanie wyników wyszukiwania do skrzynki pocztowej odnajdywania</td>
<td>Brak</td>
<td>Nie ma bezpośredniego zastąpienia tej funkcji, ponieważ nie zapewnia ona dostępu do wszystkich usług Microsoft 365. Aby uzyskać alternatywne rozwiązania, zobacz poniższe często zadawane pytania.</td>
</tr>
  <tr class=even>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby udzielić osobie dostępu do poczty e-mail innego użytkownika (na przykład gdy pracownik opuszcza organizację i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, wystarczy przypisać użytkownikowi uprawnienia dostępu do źródłowej skrzynki pocztowej.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>Często zadawane pytania dotyczące poleceń cmdlet ***-MailboxSearch**

**Usługa Copy Search służy do eksportowania wiadomości e-mail lub wiadomości błyskawicznych do celów innych zbierania elektronicznych materiałów dowodowych i dochodzeń prawnych. Jakie inne opcje mamy po wycofaniu tych poleceń cmdlet?**

[<span class="underline">Interfejsy API Graph firmy Microsoft</span>](https://developer.microsoft.com/en-us/graph) udostępniają szereg metod wyodrębniania danych na potrzeby analizy i innych celów, które są znacznie bardziej odporne i skalowalne niż przy użyciu **\*poleceń cmdlet -MailboxSearch**.

**Jak mogę przeprowadzić migrację wyszukiwań i blokad do portalu zgodności?**

Istnieje możliwość migracji In-Place wyszukiwania zbierania elektronicznych materiałów dowodowych i archiwizacji z centrum administracyjnego Exchange przy użyciu skryptu programu PowerShell. Aby uzyskać więcej informacji, zobacz [Migrate legacy eDiscovery searches and holds to the compliance portal (Migrowanie starszych wyszukiwań elektronicznych zbierania elektronicznych materiałów dowodowych i archiwizacji do portalu zgodności](migrate-legacy-eDiscovery-searches-and-holds.md)).

**Czy po wycofaniu poleceń cmdlet nadal będę mógł usuwać lub pobierać wyszukiwania?**

Tak, mimo że usuwamy możliwość tworzenia i modyfikowania wyszukiwań, nadal będzie można używać funkcji **Get-MailboxSearch** i **Remove-MailboxSearch** do odwołania. Jednak użycie tych poleceń cmdlet będzie na własne ryzyko po upływie dat wycofania i pomoc techniczna firmy Microsoft nie będzie już w stanie udzielić pomocy.

## <a name="search-mailbox-cmdlet"></a>polecenie cmdlet Search-Mailbox

Polecenie cmdlet **Search-Mailbox** w programie Exchange Online programu PowerShell jest wycofywane zgodnie z pierwotnym ogłoszeniem w ostrzeżeniu w danych wyjściowych polecenia cmdlet rozpoczynających się w 2018 r. Polecenie cmdlet **Search-Mailbox** było pierwotnie używane do przeszukiwania skrzynki pocztowej użytkownika i przeczyszczania złośliwej zawartości. Zalecamy rozpoczęcie korzystania z poleceń cmdlet **New-ComplianceSearch** i **New-ComplianceSearchAction** w programie Office 365 Security & Compliance Center PowerShell w celu wyszukiwania i przeczyszczania zawartości. W przypadku wbudowanego środowiska zabezpieczeń [<span class="underline">funkcje zabezpieczeń Microsoft 365</span>](../security/index.yml) zapewniają niezawodną ochronę przed zagrożeniami w przypadku poczty e-mail i wielu innych usługi firmy Microsoft.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których dotyczy problem

- organizacje Office 365 i Microsoft 365 Enterprise

- organizacje Office 365 i Microsoft 365 Education

- Office 365 i Microsoft 365 organizacji rządowych; obejmuje to GCC, GCC High i DoD

- Office 365 Niemcy

### <a name="timeline"></a>Oś czasu

-  1 lipca 2020 r.: polecenie cmdlet **Search-Mailbox** nie będzie już dostępne i pomoc techniczna firmy Microsoft nie będzie już udzielać pomocy.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, których można użyć do zastąpienia istniejących funkcji, które są wycofywane.

<table>
<thead>
<tr class="header">
<th>Funkcje</th>
<th>Narzędzia alternatywne</th>
<th>Komentarze</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Wyszukiwanie skrzynki pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Polecenia cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić wyszukiwanie i eksportowanie zawartości. Możesz utworzyć nowe wyszukiwanie i wyświetlić oszacowanie wyszukiwania przy użyciu poleceń cmdlet <strong>New-</strong>, <strong>Get-i Start-ComplianceSearch</strong>. <strong></strong> Następnie możesz użyć polecenia <strong>New-ComplianceSearchAction -Export</strong> , aby wyeksportować wyniki wyszukiwania. Nadal będziesz musiał użyć narzędzia eDiscovery (Standard) w portalu zgodności, aby pobrać te wyniki wyszukiwania na komputer lokalny.</p></p>
</td>
</tr>
<tr class="even">
<td>Usuwanie zbiorczej poczty e-mail ze skrzynki pocztowej</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Konfigurowanie zasad archiwum i usuwania dla skrzynek pocztowych</span></a></p>
<p></p></td>
<td><p>Administratorzy mogą utworzyć zasady archiwizacji i usuwania, które automatycznie przenosi elementy do skrzynki pocztowej archiwum użytkownika i automatycznie usuwa elementy ze skrzynki pocztowej.</p>
</td>
</tr>
<tr class="even">
<td>Kopiowanie wyników wyszukiwania do skrzynki pocztowej odnajdywania</td>
<td> </td>
<td>Nie ma bezpośredniego zastąpienia tej funkcji, ponieważ nie zapewnia ona dostępu do wszystkich usług Microsoft 365. Zapoznaj się z często zadawanymi pytaniami w sekcji <strong>*-MailboxSearch cmdlets (Polecenia cmdlet *-MailboxSearch</strong> ) , aby uzyskać alternatywne rozwiązania. </td>
</tr>
<tr class=odd>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby udzielić osobie dostępu do poczty e-mail innego użytkownika (na przykład gdy pracownik opuszcza organizację i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, wystarczy przypisać użytkownikowi uprawnienie dostępu do źródłowej skrzynki pocztowej.</td>
</tr>
<tr class=even>
  <td>Przeczyszczanie wiadomości ze skrzynki pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Polecenia cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić wyszukiwanie i przeczyszczanie zawartości. Możesz utworzyć i uruchomić wyszukiwanie za pomocą poleceń cmdlet <strong>New-ComplianceSearch</strong> i <strong>New-ComplianceSearch</strong> , a następnie przeczyścić zawartość za pomocą polecenia <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> . Aby uzyskać więcej informacji, zobacz <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">Wyszukiwanie i usuwanie komunikatów</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Przeczyszczanie wiadomości ze skrzynki pocztowej</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
<td>Aby przeczyścić wiadomości ze skrzynki pocztowej, przypisz uprawnienia administratora w celu uzyskania dostępu do skrzynki pocztowej pracownika. Komunikaty można usuwać i odtwarzać zgodnie z potrzebami, korzystając z wbudowanych funkcji wyszukiwania i wyświetlania w Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange operacje interfejsu API usług sieci Web

Te operacje w interfejsie API usług sieci Web Exchange są używane przez funkcję In-Place eDiscovery & Holds w centrum administracyjnym Exchange i odpowiednie **\*polecenia cmdlet -MailboxSearch** w programie Exchange Online programu PowerShell. Zostaną one również wycofane w ramach wycofywania innych starszych narzędzi zbierania elektronicznych materiałów dowodowych.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których dotyczy problem

- organizacje Office 365 i Microsoft 365 Enterprise

- organizacje Office 365 i Microsoft 365 Education

- Office 365 i Microsoft 365 organizacji rządowych; obejmuje to GCC, GCC High i DoD

- Office 365 Niemcy

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Operacje GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes i GetHoldOnMailboxes nie będą już dostępne, a pomoc techniczna firmy Microsoft nie będą już udzielać pomocy.

## <a name="ediscovery-premium-v10"></a>eDiscovery (Premium) v1.0

eDiscovery (Premium) v1.0, czyli wersja eDiscovery (Premium) dostępna w przypadku zbierania elektronicznych materiałów dowodowych (Standardowa), klikając pozycję **Przełącz się do eDiscovery (Premium)**, jest wycofywana. Jego funkcjonalność została zastąpiona nowym [rozwiązaniem zbierania elektronicznych materiałów dowodowych (Premium)](./ediscovery.md) w portalu zgodności.

Aby ustalić, czy organizacja korzysta z funkcji zbierania elektronicznych materiałów dowodowych (Premium) w wersji 1.0:

1. Przejdź do portalu zgodności, wybierz pozycję **eDiscoveryCore** >  i otwórz przypadek zbierania elektronicznych materiałów dowodowych (Standard).<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. Jeśli zostanie **wyświetlony przycisk Przełącz do zbierania elektronicznych materiałów dowodowych (Premium**), kliknięcie go spowoduje przejście do wersji 1.0 zbierania elektronicznych materiałów dowodowych (Premium), która jest wycofywana. Nie będzie to miało wpływu na możliwość tworzenia przypadków zbierania elektronicznych materiałów dowodowych (standard) i zarządzania nimi. Wycofywana jest tylko możliwość dodawania i analizowania danych przypadków w systemie zbierania elektronicznych materiałów dowodowych (Premium) w wersji 1.0 (przez **kliknięcie pozycji Przełącz do zbierania elektronicznych materiałów dowodowych (Premium)**).

Nowe rozwiązanie zbierania elektronicznych materiałów dowodowych (Premium) w Microsoft 365 (znane również jako *eDiscovery (Premium) w wersji 2.0*) zapewnia wszystkie możliwości oryginalnego rozwiązania, ale teraz obejmuje oparte na opiekunach podejście do identyfikowania zawartości w innych Microsoft 365  usługi, zbieranie tej zawartości, a następnie dodawanie jej do zestawu przeglądów, w którym recenzenci mogą korzystać z funkcji szybkiego wyszukiwania, tagowania i analizy, aby pomóc w usuwaniu odpowiednich dokumentów. Funkcja zbierania elektronicznych materiałów dowodowych (Premium) obejmuje teraz ulepszone przetwarzanie i natywnych osób przeglądających zarówno dla typów plików firmy Microsoft, jak i innych firm. Pełna lista typów plików znajduje się [tutaj](./supported-filetypes-ediscovery20.md), a obsługiwane pola metadanych znajdują [się tutaj](./document-metadata-fields-in-advanced-ediscovery.md). Ponadto nowe rozwiązanie do zbierania elektronicznych materiałów dowodowych (Premium) zapewnia zaawansowaną funkcję zarządzania, która umożliwia stosowanie blokad do zawartości w różnych usługach, powiadamianie użytkowników o blokadach i śledzenie odpowiedzi opiekuna, a wszystko to w przypadku zbierania elektronicznych materiałów dowodowych (Premium).

Aby uzyskać dostęp do funkcji zbierania elektronicznych materiałów dowodowych (Premium) w wersji 2.0:

Przejdź do portalu zgodności, wybierz pozycję **eDiscoveryAdvanced** >  i otwórz przypadek zbierania elektronicznych materiałów dowodowych (Standard).<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

W tej chwili zalecamy rozpoczęcie przenoszenia przepływu pracy zbierania elektronicznych materiałów dowodowych do nowej funkcji zbierania elektronicznych materiałów dowodowych (Premium). W razie potrzeby możesz zarchiwizować przypadki zbierania elektronicznych materiałów dowodowych (Premium) 1.0, eksportując zawartość i przechowując ją w trybie offline. Mimo że w istniejących przypadkach do 31 grudnia 2020 r. będziesz mieć dostęp do usługi eDiscovery (Premium) w wersji 1.0, pomoc techniczna firmy Microsoft nie zapewni wsparcia po 1 października 2020 r. Aby uzyskać więcej informacji, zobacz następującą oś czasu.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których dotyczy problem

- organizacje Office 365 i Microsoft 365 Enterprise

- organizacje Office 365 i Microsoft 365 Education

- Office 365 i Microsoft 365 organizacji rządowych; obejmuje to GCC, GCC High i DoD

- Office 365 Niemcy

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Nie będzie można tworzyć nowych przypadków zbierania elektronicznych materiałów dowodowych (Premium) w wersji 1.0.

- 1 października 2020 r.: Nie będzie można dodawać nowych danych (Przygotowanie wyników wyszukiwania dla zbierania elektronicznych materiałów dowodowych (Premium)) do żadnych przypadków. Będziesz mieć możliwość dalszej pracy z danymi w istniejących przypadkach na własne ryzyko. pomoc techniczna firmy Microsoft nie będzie już udzielać pomocy. 

- 31 grudnia 2020 r.: Nie będziesz mieć dostępu do spraw zbierania elektronicznych materiałów dowodowych (Premium) w wersji 1.0.

### <a name="alternative-tools"></a>Narzędzia alternatywne

[Rozwiązanie zbierania elektronicznych materiałów dowodowych (Premium)](./overview-ediscovery-20.md) w portalu zgodności.
