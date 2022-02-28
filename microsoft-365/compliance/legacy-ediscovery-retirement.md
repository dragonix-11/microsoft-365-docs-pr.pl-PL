---
title: Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place zbierania elektronicznych materiałów dowodowych i In-Place i odpowiadające im polecenia cmdlet programu PowerShell w programie Exchange Online zostaną wycofane w pierwszej połowie 2020 r. W Search-Mailbox i 1.0 Advanced eDiscovery polecenia cmdlet i polecenia cmdlet w wersji 1.0 również zostaną wycofane.
ms.openlocfilehash: f778a31580bb908205c707c1f613f49bd6a576d1
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990502"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Wycofanie starszych narzędzi zbierania elektronicznych materiałów dowodowych

> [!IMPORTANT]
> Funkcje starszych narzędzi zbierania elektronicznych materiałów dowodowych opisane w tym artykule zostały usunięte z usługi Microsoft 365 lub są nadal dostępne, ale nie są już obsługiwane. Wszystkie funkcje, które są nadal dostępne, mogą zostać usunięte bez powiadomienia. Jeśli nadal używasz dowolnego z tych starszych narzędzi, rozważ  migrowanie do narzędzi zbierania elektronicznych materiałów dowodowych w p Centrum zgodności platformy Microsoft 365 lub innych rozwiązań alternatywnych opisanych w tym artykule.

Firma Microsoft przez lata zapewniała narzędzia zbierania elektronicznych materiałów dowodowych, które umożliwiają wyszukiwanie, wyświetlanie podglądu i eksportowanie zawartości wiadomości e-mail z usługi Exchange Online. Jednak te narzędzia nie oferują już skutecznego wyszukiwania zawartości innej niż Exchange w innych usługach firmy Microsoft 365, takich jak usługi SharePoint Online i Microsoft 365 Grupy. Aby rozwiązać ten temat, firma Microsoft oferuje inne narzędzia do zbierania elektronicznych materiałów dowodowych, które ułatwiają wyszukiwanie wielu różnych Microsoft 365 zawartości. Ponadto ciężko pracowaliśmy nad dodaniem najbardziej aktualnych i zaawansowanych funkcji zbierania elektronicznych materiałów dowodowych w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">p Centrum zgodności platformy Microsoft 365</a>. Dzięki temu organizacje mogą odpowiadać na żądania prawne, wewnętrzne i inne dokumenty na zawartość w wielu różnych Microsoft 365, w tym w Exchange Online.

W wyniku tej nowej i ulepszonej funkcji zbierania elektronicznych materiałów dowodowych w programie Centrum zgodności platformy Microsoft 365 wycofujemy następujące funkcje i funkcje związane z zbierania elektronicznych materiałów dowodowych związane z wyszukiwaniem zawartości wiadomości e-mail w programach Exchange Online i Microsoft 365:

- [Zbierania elektronicznych materiałów dowodowych](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) w miejscu i [zbierania elektronicznych materiałów dowodowych](/exchange/security-and-compliance/create-or-remove-in-place-holds) w Exchange administracyjnego.

- Polecenia cmdlet programu Exchange Online PowerShell, które obsługują In-Place zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych In-Place (te polecenia cmdlet są zbiorczo identyfikowane jako polecenia cmdlet **-MailboxSearch*). Obejmuje to następujące polecenia cmdlet:

  - [Nowe wyszukiwanie skrzynek pocztowych](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Polecenia cmdlet [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) i [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) będą dostępne po wycofaniu innych cmdlet z witryny ****-MailboxSearch***, dzięki czemu będą one pomocne podczas przechodzenia do innych narzędzi zbierania elektronicznych materiałów dowodowych i przytrzymaj. Jednak po określonej dacie (cytowanej poniżej) pomoc techniczna firmy Microsoft nie będzie już obsługiwać tych dwóch cmdlet.

- Polecenie [cmdlet Search-Mailbox](/powershell/module/exchange/search-mailbox) w programie Exchange Online PowerShell.

- Następujące operacje w interfejsie API Exchange Web Services:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Office 365 Advanced eDiscovery wersji 1.0](./overview-ediscovery-20.md), która jest pierwszą wersją pakietu Advanced eDiscovery dostępną za pośrednictwem podstawowej sprawy zbierania elektronicznych materiałów dowodowych w ramach Centrum zgodności platformy Microsoft 365. Wycofanie wersji Advanced eDiscovery 1.0 nie wpływa na Twoją możliwość tworzenia podstawowych spraw zbierania elektronicznych materiałów dowodowych i zarządzania nimi.

> [!NOTE]
> Funkcja zbierania elektronicznych materiałów dowodowych jest wy wycofana tylko w opartej na chmurze Microsoft 365 i Office 365. Funkcja zbierania elektronicznych materiałów dowodowych w lokalnych wersjach Exchange i SharePoint będzie nadal obsługiwana do odwołania.

Poniższe sekcje w tym artykule zawierają wskazówki dotyczące poszczególnych wycofanych funkcji. Te informacje, w tym osie czasu i alternatywne narzędzia, których można używać zamiast wycofanych narzędzi.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place zbierania elektronicznych materiałów dowodowych i In-Place w centrum administracyjnym usługi Exchange w programie 

Zgodnie z pierwotnym ogłoszeniem z 1 lipca 2017 r. funkcja zbierania elektronicznych materiałów dowodowych In-Place & w centrum administracyjnym usługi Exchange zostanie wycofana. Strona In-Place zbierania elektronicznych materiałów dowodowych & w Aplikacji EAC umożliwiała przeszukiwanie, hold i eksportowanie zawartości z witryny Exchange Online. In-Place zbierania elektronicznych materiałów dowodowych możesz również skopiować wyniki wyszukiwania do skrzynki pocztowej zbierania elektronicznych materiałów dowodowych, aby Ty i inni menedżerowie zbierania elektronicznych materiałów dowodowych mogli przejrzeć zawartość i udostępnić ją na żądanie prawne, prawne i publiczne.

Ponieważ wszystkie te funkcje (z wyjątkiem kopiowania wyników wyszukiwania do skrzynki pocztowej odnajdowania) są teraz dostępne w narzędziach wyszukiwania zawartości, zbierania elektronicznych materiałów dowodowych i aplikacji Advanced eDiscovery w programie [Centrum zgodności platformy Microsoft 365](./microsoft-365-compliance-center.md) (z większą funkcjonalnością, niezawodnością i obsługą wielu Microsoft 365 usługi) zalecamy jak najszybciej rozpocząć korzystanie z tych narzędzi. Aby ułatwić ci przejście do tych innych narzędzi zbierania elektronicznych materiałów dowodowych, w poniższej tabeli wymieniono narzędzia, których można używać zamiast funkcji zbierania elektronicznych materiałów dowodowych In-Place i In-Place hold.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których to dotyczy

- Office 365 i Microsoft 365 Enterprise organizacji

- Office 365 i Microsoft 365 Education organizacji

- Office 365 i Microsoft 365 rządowych. Dotyczy to GCC, GCC High i DoD

- Office 365 Germany

### <a name="timeline-for-retirement"></a>Oś czasu dla wycofania

- 1 lipca 2020 r.: Nie będzie można tworzyć nowych wyszukiwań i blokady, ale nadal można uruchamiać, edytować i usuwać istniejące wyszukiwania na własne ryzyko. Pomoc techniczna Microsoft nie będzie już In-Place zbierania elektronicznych materiałów dowodowych & eAC.

- 1 października 2020 r.: Funkcje In-Place eDiscovery & w Aplikacji EAC zostaną umieszczone w trybie tylko do odczytu. Oznacza to, że będzie można tylko usuwać istniejące wyszukiwania i blokady.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, za pomocą których można zastąpić obecnie wycofane funkcje.

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
<td>Wyszukiwanie, eksportowanie i przechowywania w celach prawnych</td>
<td>Podstawowe sprawy zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 </td>
<td><p>Korzystanie z funkcji podstawowych spraw zbierania elektronicznych materiałów dowodowych zapewnia funkcjonalny zestaw funkcji zbierania elektronicznych materiałów dowodowych In-Place zbierania elektronicznych materiałów dowodowych In-Place funkcją zbierania elektronicznych materiałów dowodowych. Obejmuje to następujące elementy:</p>
<ul>
<li>
<p>Skalowanie wyszukiwania do milionów lokalizacji</p>
</li>
<li>
<p>Większa niezawodność wyszukiwania, eksportowania i umieszczania zawartości w hold.</p>
</li>
<li>
<p>Wyszukiwanie zawartości w usługach Exchange Online, SharePoint Online, OneDrive dla Firm, Skype dla firm, Microsoft Teams, Yammer, Microsoft 365 Groups i inna zawartość przechowywana w Office 365 aplikacjach</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Wstrzymywanie w celu przechowywania</td>
<td>Zasady przechowywania w Centrum zgodności platformy Microsoft 365</td>
<td><p>Przy użyciu zasad przechowywania można zachować zawartość i, w razie potrzeby, usunąć ją po wygaśnięciu okresu przechowywania. Inne możliwości są następujące:</p>
<ul>
<li>
<p>Stosowanie zasad do całej organizacji </p>
</li><li>
<p>Stosowanie zasad do określonych lokalizacji zawartości, takich jak Exchange Online, SharePoint Online, OneDrive dla Firm, Skype dla firm, Microsoft Teams i Office 365 Groups</p></li>
<li>
<p>Stosowanie zasad do konkretnych użytkowników</p></li></ul>
<p>Aby uzyskać więcej informacji, zobacz <a href="/microsoft-365/compliance/retention-policies"> Informacje o zasadach przechowywania i etykietach przechowywania</a>.</td>
</tr>
<tr class="odd">
<td>Kopiowanie wyników wyszukiwania wiadomości e-mail do skrzynki pocztowej odnajdowania w celu przejrzenia</td><td>Przeglądanie zestawów w Advanced eDiscovery 2.0</td>
<td><p>Przeglądanie zawartości w programie Microsoft 365 jeszcze nigdy nie było łatwiejsze. Zestawy recenzji mają wiele doskonałych funkcji, które pomagają skrócić czas i ilość danych potrzebnych do przejrzenia, między innymi:</p>
<ul>
<li><p>Wykonywanie szybkich zapytań wyszukiwania i filtrowanie zawartości w zestawie recenzji</p></li>
<li><p>Analizowanie zawartości w zestawie recenzji; obejmuje to wątki wiadomości e-mail, wykrywanie niemal duplikatów, analizę motywów i podpowidanie kodu</p></li>
<li><p>Oznaczanie dokumentów w zestawie recenzji</p></li>
<li><p>Sugestie dotyczące otagowania w celu pomoc w zidentyfikowaniu zawartości dotyczącej uprawnień klienta</p></li></ul>
<p>Aby uzyskać więcej informacji, zobacz <a href="/microsoft-365/compliance/overview-ediscovery-20">Omówienie Advanced eDiscovery w programie Microsoft 365</a>.</p>
<p>
<p>Możesz również wyeksportować wyniki wyszukiwania do plików PST, a następnie użyć Microsoft 365 Importowanie usługi w celu zaimportowania plików PST do skrzynki pocztowej odnajdowania. Aby uzyskać instrukcje krok po kroku, zobacz Importowanie plików PST do importowania plików <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">PST za pomocą przekazywania Office 365</a>.
</tr>
<tr class=even>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby nadać innej osobie dostęp do poczty e-mail innego użytkownika (na przykład gdy pracownik odchodzi z organizacji i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, wystarczy przypisać użytkownikowi uprawnienia konieczne do uzyskania dostępu do źródłowej skrzynki pocztowej.</td>
  
  </tr>
<tr class="odd">
<td>Przywracanie elementów z folderu Elementy do odzyskania</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>W skrzynkach pocztowych możesz przywrócić elementy trwale usunięte (<i></i>nazywane także elementami "miękkiego usunięcia"), o ile nie wygasł okres przechowywania elementów usuniętych dla elementu. Aby uzyskać więcej informacji, zobacz <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">Folder Elementy do odzyskania w folderze Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>Często zadawane pytania dotyczące zbierania In-Place eDiscovery i In-Place blokady

**Korzystam z funkcji kopiowania wyników wyszukiwania funkcji zbierania elektronicznych In-Place eDiscovery &, aby skopiować wyniki wyszukiwania do skrzynki pocztowej zbierania elektronicznych materiałów dowodowych w celu ich przejrzenia przez pełnomocników. Jakie opcje mam teraz?**

Istnieją dwa sposoby replikowania tej funkcji już dziś. Pierwszym z nich jest użycie [zestawów recenzji w Advanced eDiscovery 2.0](./view-documents-in-review-set.md). Zestawy recenzji mają wiele takich samych możliwości, jak w przypadku tradycyjnych narzędzi do rerecenzowania, takich jak szybkie wyszukiwanie dokumentów, tagowanie, wątkowanie wiadomości e-mail, niemal zduplikowane grupowanie, analiza motywów i podpowidanie kodu. Jeśli nadal chcesz przeglądać skrzynki pocztowe z odnajdowaniami, drugą opcją jest wyeksportowanie wyników wyszukiwania do plików PST, a następnie zaimportowanie plików PST do skrzynki pocztowej odnajdowania przy użyciu funkcji importowania [pliku PST](use-network-upload-to-import-pst-files.md) w Centrum zgodności firmy Microsoft.

**Jak kontrolować, w których lokalizacjach zawartości (takich jak skrzynki pocztowe lub witryny) menedżer zbierania elektronicznych materiałów dowodowych może wyszukiwać za pomocą nowych narzędzi?**

Ponadto Centrum zgodności platformy Microsoft 365 korzysta z granic [zgodności w](set-up-compliance-boundaries.md) celu kontrolowania, które lokalizacje zawartości może wyszukiwać Menedżer zbierania elektronicznych materiałów dowodowych. Granice zgodności są przydatne w jednostkach rządowych, które muszą pozostać w granicach agencji lub wielonarodowych przedsiębiorstw wymaganych do przestrzegania tablic geograficznych.

**Jak przenieść bieżące wyszukiwania i blokady do Centrum zgodności platformy Microsoft 365?**

Za pomocą programu PowerShell można przeprowadzić migrację In-Place zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych w Chmurze programu PowerShell. Aby uzyskać instrukcje, zobacz [Migrowanie wyszukiwań i blokady z aplikacji EAC do programu Centrum zgodności platformy Microsoft 365](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlet

Zgodnie z pierwotnym powiadomieniem z 1 lipca 2017 r. w centrum administracyjnym usługi Exchange In-Place funkcje zbierania elektronicznych materiałów dowodowych & **\*** i odpowiadające im polecenia cmdlet wyszukiwania skrzynek pocztowych są wyginane. Te polecenia cmdlet zapewniają użytkownikom możliwość przeszukiwania, przechowywania i eksportowania zawartości skrzynek pocztowych na żądanie prawne, prawne i publiczne.

Ponieważ te funkcje są teraz dostępne w programie [<span class="underline">PowerShell</span>](./microsoft-365-compliance-center.md) centrum zabezpieczeń Centrum zgodności platformy Microsoft 365 i Office 365 Security & o lepszej wydajności i skalowalności, należy używać tych ulepszonych poleceń cmdlet. Te polecenia cmdlet to[<span class="underline">\*: -ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) [<span class="underline">i\* -ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których to dotyczy

- Office 365 i Microsoft 365 Enterprise organizacji

- Office 365 i Microsoft 365 Education organizacji

- Office 365 i Microsoft 365 rządowych. Dotyczy to GCC, GCC High i DoD

- Office 365 Germany

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Nie będzie można używać wyszukiwania nowych skrzynek pocztowych  do tworzenia nowych wyszukiwań zbierania elektronicznych materiałów dowodowych usługi In-Place i zbierania elektronicznych materiałów dowodowych In-Place, ale nadal można używać polecenia cmdlet do uruchamiania, edytowania i usuwania istniejących wyszukiwań oraz blokady na własne ryzyko. Pomoc techniczna firmy Microsoft nie będzie już zapewniać pomocy przy tego typu wyszukiwaniach i blokadych.

- 1 października 2020 r.: Jak wspomniano wcześniej, funkcja zbierania elektronicznych materiałów dowodowych In-Place & w AAC zostanie umieszczona w trybie tylko do odczytu. Oznacza to również, że nie będzie można używać polecenia cmdlet **New-MailboxSearch**, **Start-MailboxSearch** ani **Set-MailboxSearch** . Będzie można tylko wyszukiwać i usuwać istniejące wyszukiwania i blokady.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, za pomocą których można zastąpić obecnie wycofane funkcje.

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
<td><p>Polecenia cmdlet cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić wyszukiwanie i eksportowanie zawartości. Możesz utworzyć nowe wyszukiwanie i wyświetlić oszacowanie za pomocą polecenia cmdlet <strong>New-</strong>, <strong>Get-</strong>, <strong>i Start-ComplianceSearch</strong> . Następnie możesz użyć polecenia cmdlet <strong>New-ComplianceSearchAction</strong> w celu wyeksportowania wyników wyszukiwania. Nadal musisz korzystać z podstawowego narzędzia zbierania elektronicznych materiałów dowodowych w aplikacji Centrum zgodności platformy Microsoft 365, aby pobrać te wyniki wyszukiwania na komputer lokalny.</p>
<p>
<p><strong>Uwaga:</strong> Jeśli za pomocą tych funkcji cmdlet utworzysz wyszukiwania, które nie są skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych, te wyszukiwania będą się znajdowały <strong></strong> na stronie Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365.</p></td>
</tr>
<tr class="even">
<td>Wstrzymywanie zawartości w skrzynce pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Musi być skojarzona Centrum zgodności platformy Microsoft 365 z literami ComplianceCase. Najpierw utwórz sprawę zgodności, a następnie utwórz zasady CaseHoldPolicy i caseHoldRule.</p>
<p><strong>Uwaga:</strong> Utworzenie usługi CaseHoldPolicy bez tworzenia utworzonego ustawienia CaseHoldRule będzie renderować niedziałaną wstrzymać do czasu utworzenia i skojarzenia caseHoldRule z caseHoldPolicy. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją polecenia cmdlet.</p></td>
</tr>
<tr class="odd">
<td>Kopiowanie wyników wyszukiwania do skrzynki pocztowej odnajdowania</td>
<td>Brak</td>
<td>Nie istnieje bezpośrednia zamiana tej funkcji, ponieważ nie zapewnia ona dostępu do wszystkich Microsoft 365 usług. Aby uzyskać alternatywne rozwiązania, zobacz poniższe często zadawane pytania.</td>
</tr>
  <tr class=even>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby nadać innej osobie dostęp do poczty e-mail innego użytkownika (na przykład gdy pracownik odchodzi z organizacji i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, wystarczy przypisać użytkownikowi uprawnienia dostępu do źródłowej skrzynki pocztowej.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>Często zadawane pytania dotyczące ***-MailboxSearch** — polecenia cmdlet

**Używamy funkcji kopiowania wyszukiwania do eksportowania wiadomości e-mail lub wiadomości błyskawicznych na potrzeby innego zbierania elektronicznych materiałów dowodowych i dochodzenia prawnego. Jakie inne opcje są dostępne po wycofaniu tych polecenia cmdlet?**

Interfejsy [<span class="underline">API</span>](https://developer.microsoft.com/en-us/graph) **\*** platformy Microsoft Graph zapewniają wiele metod wyodrębniania danych do analizy i do innych celów, które są o wiele bardziej elastyczne i skalowalne niż polecenia cmdlet -MailboxSearch.

**Jak przeprowadzić migrację wyszukiwań i blokady do Centrum zgodności platformy Microsoft 365?**

Za pomocą skryptu programu PowerShell można przeprowadzić migrację In-Place zbierania elektronicznych materiałów dowodowych i blokady z centrum administracyjnego programu Exchange. Aby uzyskać więcej informacji, zobacz [Migrowanie starszych](migrate-legacy-eDiscovery-searches-and-holds.md) wyszukiwań i funkcji zbierania elektronicznych materiałów dowodowych do Centrum zgodności platformy Microsoft 365.

**Czy po wycofaniu tych polecenia cmdlet nadal będzie można usuwać lub pobierać wyszukiwania?**

Tak, chociaż usuwamy możliwość tworzenia i modyfikowania wyszukiwań, nadal będzie można używać funkcji **Get-MailboxSearch** i **Remove-MailboxSearch** , aż do odwołania. Jednak korzystanie z tych cmdlet będzie na własne ryzyko po wycofaniem i pomoc techniczna firmy Microsoft nie będzie już mogła udzielać pomocy.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

Polecenie cmdlet **Search-Mailbox** w programie Exchange Online PowerShell zostało wycofane, jak pierwotnie ogłoszono w ostrzeżeń w wyniku polecenia cmdlet rozpoczynającego się w 2018 r. Polecenie **cmdlet Search-Mailbox** zostało pierwotnie użyte do przeszukiwania skrzynki pocztowej użytkownika i przeczyszczania złośliwej zawartości. Zalecamy rozpoczęcie korzystania z poleceń cmdlet **New-ComplianceSearch** i **New-ComplianceSearchAction** w programie PowerShell w Office 365 Security & Compliance Center w celu wyszukiwania i przeczyszczania zawartości. W celu zapewnienia wbudowanego środowiska zabezpieczeń funkcje zabezpieczeń aplikacji Microsoft 365 [<span class="underline">zapewniają</span>](../security/index.yml) niezawodność ochrony przed zagrożeniami dla poczty e-mail i wielu innych usługi firmy Microsoft.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których to dotyczy

- Office 365 i Microsoft 365 Enterprise organizacji

- Office 365 i Microsoft 365 Education organizacji

- Office 365 i Microsoft 365 rządowych. Dotyczy to GCC, GCC High i DoD

- Office 365 Germany

### <a name="timeline"></a>Oś czasu

-  1 lipca 2020 r.: Polecenie cmdlet **Search-Mailbox** nie będzie już dostępne i pomoc techniczna firmy Microsoft nie będzie już zapewniać pomocy.

### <a name="alternative-tools"></a>Narzędzia alternatywne

W poniższej tabeli opisano inne narzędzia, za pomocą których można zastąpić obecnie wycofane funkcje.

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
<td>Wyszukiwanie w skrzynce pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Polecenia cmdlet cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić wyszukiwanie i eksportowanie zawartości. Możesz utworzyć nowe wyszukiwanie i wyświetlić oszacowanie za pomocą polecenia cmdlet <strong>New-</strong>, <strong>Get-</strong>, <strong>i Start-ComplianceSearch</strong> . Następnie możesz użyć polecenia <strong>New-ComplianceSearchAction -Export</strong> w celu wyeksportowania wyników wyszukiwania. Nadal musisz korzystać z podstawowego narzędzia zbierania elektronicznych materiałów dowodowych w aplikacji Centrum zgodności platformy Microsoft 365, aby pobrać te wyniki wyszukiwania na komputer lokalny.</p></p>
</td>
</tr>
<tr class="even">
<td>Usuwanie zbiorczej poczty e-mail ze skrzynki pocztowej</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Konfigurowanie zasad archiwizacji i usuwania dla skrzynek pocztowych</span></a></p>
<p></p></td>
<td><p>Administratorzy mogą utworzyć zasady archiwizacji i usuwania, które automatycznie przesuną elementy do archiwalnej skrzynki pocztowej użytkownika i automatycznie usuwają elementy ze skrzynki pocztowej.</p>
</td>
</tr>
<tr class="even">
<td>Kopiowanie wyników wyszukiwania do skrzynki pocztowej odnajdowania</td>
<td> </td>
<td>Nie istnieje bezpośrednia zamiana tej funkcji, ponieważ nie zapewnia ona dostępu do wszystkich Microsoft 365 usług. Zobacz często zadawane pytania w sekcji <strong>polecenia cmdlet *-MailboxSearch</strong> , aby uzyskać alternatywne rozwiązania. </td>
</tr>
<tr class=odd>
  <td>Kopiowanie wiadomości z jednej skrzynki pocztowej do innej skrzynki pocztowej</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
  <td>Aby nadać innej osobie dostęp do poczty e-mail innego użytkownika (na przykład gdy pracownik odchodzi z organizacji i musisz udzielić innej osobie dostępu do poczty e-mail byłego pracownika), zalecamy przypisanie tej osobie uprawnień dostępu do skrzynki pocztowej byłego pracownika. Dlatego zamiast kopiować elementy skrzynki pocztowej do innej skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej, wystarczy przypisać użytkownikowi uprawnienia dostępu do źródłowej skrzynki pocztowej.</td>
</tr>
<tr class=even>
  <td>Przeczyszczanie wiadomości ze skrzynki pocztowej</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Polecenia cmdlet ComplianceSearch i ComplianceSearchAction współpracują ze sobą, aby ułatwić przeszukiwanie i przeczyszczanie zawartości. Możesz utworzyć i uruchomić wyszukiwanie za pomocą poleceń cmdlet <strong>New-ComplianceSearch</strong> i <strong>New-ComplianceSearch</strong> , a następnie przeczyścić zawartość, używając polecenia <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> . Aby uzyskać więcej informacji, <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">zobacz Wyszukiwanie i usuwanie wiadomości</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Przeczyszczanie wiadomości ze skrzynki pocztowej</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Przypisywanie uprawnień do skrzynki pocztowej</a></td>
<td>Aby przeczyścić wiadomości ze skrzynki pocztowej, przypisz uprawnienia administratora do uzyskiwania dostępu do skrzynki pocztowej pracownika. Wiadomości można usuwać i odzyskiwać zgodnie z potrzebami, korzystając z wbudowanych funkcji wyszukiwania i wyświetlania w programie Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange operacji interfejsu API usług sieci Web

Operacje wykonywane w interfejsie API usług sieci Web usługi In-Place Exchange są używane przez funkcję zbierania elektronicznych materiałów dowodowych & w centrum administracyjnym programu Exchange **\*** i odpowiadające im polecenia cmdlet -MailboxSearch w programie Exchange Online PowerShell. Zostaną one również wycofane w ramach wycofywania innych starszych narzędzi zbierania elektronicznych materiałów dowodowych.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których to dotyczy

- Office 365 i Microsoft 365 Enterprise organizacji

- Office 365 i Microsoft 365 Education organizacji

- Office 365 i Microsoft 365 rządowych. Dotyczy to GCC, GCC High i DoD

- Office 365 Germany

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Operacje GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes i GetHoldOnMailboxes nie będą już dostępne, a pomoc techniczna firmy Microsoft nie będzie już udzielać pomocy.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery 1.0

Advanced eDiscovery wersji 1.0, która jest wersją pakietu Advanced eDiscovery dostępną w podstawowej sprawie zbierania elektronicznych materiałów dowodowych przez kliknięcie pozycji Przełącz do programu **Advanced eDiscovery**, jest wylogowydawana. Jego funkcje zostały zastąpione przez nowe Advanced eDiscovery [w](./ediscovery.md) programie Centrum zgodności platformy Microsoft 365.

Aby ustalić, czy Twoja organizacja Advanced eDiscovery wersji 1.0:

1. Przejdź do centrum Centrum zgodności platformy Microsoft 365, wybierz **pozycję eDiscoveryCore** >  i otwórz podstawową sprawę zbierania elektronicznych materiałów dowodowych.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. Jeśli zobaczysz przycisk **Przełącz do Advanced eDiscovery**, kliknięcie go spowoduje przejście do wersji 1.0 pakietu Advanced eDiscovery, która jest wye żeby z nich z nich Advanced eDiscovery. Nie wpływa to na możliwość tworzenia spraw i zarządzania nimi w przypadku podstawowych zbierania elektronicznych materiałów dowodowych. Tylko możliwość dodawania i analizowania danych dotyczących Advanced eDiscovery w wersji 1.0 (przez kliknięcie pozycji Przełącz do **Advanced eDiscovery**) jest wylogowydawana.

Nowe rozwiązanie Advanced eDiscovery w programie Microsoft 365 (znane również jako *Advanced eDiscovery w wersji 2.0*) oferuje wszystkie funkcje oryginalnego rozwiązania, ale teraz zawiera oparte na wyekschiwistycznej podejście do identyfikowania zawartości w innych Microsoft 365  usługi, zbierając tę zawartość, a następnie dodając ją do zestawu recenzji, gdzie recenzentzy mogą korzystać z funkcji szybkiego wyszukiwania, tagowania i analizy, co pomaga w oznaczaniu odpowiednich dokumentów. Advanced eDiscovery teraz ulepszone przetwarzanie i natywne przeglądarki zarówno dla typów plików firmy Microsoft, jak i plików innych niż firmy Microsoft, tutaj znajduje się [](./supported-filetypes-ediscovery20.md) pełna lista typów plików, a znajdują się tutaj obsługiwane pola [metadanych](./document-metadata-fields-in-advanced-ediscovery.md). Nowe rozwiązanie Advanced eDiscovery udostępnia też zaawansowaną funkcję zarządzania funkcją przechowawczy, która umożliwia stosowanie blokady do zawartości w różnych usługach, powiadamianie użytkowników o blokadych oraz śledzenie odpowiedzi w związku z Advanced eDiscovery przypadku.

Aby uzyskać Advanced eDiscovery wersji 2.0:

Przejdź do centrum Centrum zgodności platformy Microsoft 365, wybierz **pozycję eDiscoveryAdvanced** >  i otwórz podstawową sprawę zbierania elektronicznych materiałów dowodowych.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

W tym momencie zalecamy rozpoczęcie przejścia przepływu pracy zbierania elektronicznych materiałów dowodowych do nowej Advanced eDiscovery e-mail. W razie potrzeby można zarchiwizować pliki w Advanced eDiscovery 1.0, eksportując zawartość i przechowując ją w trybie offline. Mimo że nadal będzie można uzyskać dostęp do wersji Advanced eDiscovery 1.0 w istniejących przypadkach do 31 grudnia 2020 r., pomoc techniczna firmy Microsoft nie będzie zapewniać pomocy technicznej po 1 października 2020 r. Aby uzyskać więcej informacji, zobacz następującą oś czasu.

### <a name="scope-of-affected-organizations"></a>Zakres organizacji, których to dotyczy

- Office 365 i Microsoft 365 Enterprise organizacji

- Office 365 i Microsoft 365 Education organizacji

- Office 365 i Microsoft 365 rządowych. Dotyczy to GCC, GCC High i DoD

- Office 365 Germany

### <a name="timeline"></a>Oś czasu

- 1 lipca 2020 r.: Nie będzie można tworzyć nowych Advanced eDiscovery w wersji 1.0.

- 1 października 2020 r.: Nie będzie można dodawać nowych danych (Przygotowywanie wyników wyszukiwania do Advanced eDiscovery) w żadnych przypadkach. Możesz kontynuować pracę z danymi w istniejących przypadkach na własne ryzyko. Pomoc techniczna firmy Microsoft nie będzie już udzielać pomocy. 

- 31 grudnia 2020 r.: Nie będzie można uzyskać dostępu do Advanced eDiscovery w wersji 1.0.

### <a name="alternative-tools"></a>Narzędzia alternatywne

To [Advanced eDiscovery rozwiązanie](./overview-ediscovery-20.md) w Centrum zgodności platformy Microsoft 365.