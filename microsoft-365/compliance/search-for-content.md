---
title: Szukaj zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: Użyj narzędzia Do zbierania elektronicznych materiałów dowodowych wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview, aby szybko znaleźć wiadomości e-mail w skrzynkach pocztowych Exchange, dokumentach w witrynach SharePoint i lokalizacjach OneDrive oraz konwersacje dotyczące wiadomości błyskawicznych w Skype dla firm.
ms.openlocfilehash: 4efe2f4b4735005c10fd59e618bb6ecc8be51ec0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993660"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Wyszukiwanie zawartości przy użyciu narzędzia do wyszukiwania zawartości

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj narzędzia do wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview, aby szybko znaleźć wiadomości e-mail w Exchange skrzynkach pocztowych, dokumentach w witrynach SharePoint i lokalizacjach OneDrive oraz w konwersacjach wiadomości błyskawicznych w Skype dla firm. Narzędzie do wyszukiwania zawartości umożliwia wyszukiwanie wiadomości e-mail, dokumentów i konwersacji wiadomości błyskawicznych w narzędziach do współpracy, takich jak Microsoft Teams i Grupy Microsoft 365.
  
## <a name="search-for-content"></a>Szukaj zawartości

Pierwszym krokiem jest rozpoczęcie korzystania z narzędzia wyszukiwania zawartości do wybierania lokalizacji zawartości do wyszukiwania i konfigurowania zapytania słowa kluczowego w celu wyszukiwania określonych elementów. Możesz też po prostu pozostawić zapytanie puste i zwrócić wszystkie elementy w lokalizacjach docelowych.
  
- [Tworzenie i uruchamianie](content-search.md) wyszukiwania zawartości

- [Tworzenie zapytań wyszukiwania i używanie warunków](keyword-queries-and-search-conditions.md) do zawężenia wyszukiwania

- [Dokumentacja funkcji](content-search-reference.md) wyszukiwania zawartości

- [Skonfiguruj filtrowanie uprawnień wyszukiwania](permissions-filtering-for-content-search.md) , aby menedżer zbierania elektronicznych materiałów dowodowych mógł przeszukiwać tylko podzbiór skrzynek pocztowych lub witryn w organizacji

- [Wyszukiwanie w chmurowych skrzynkach pocztowych](search-cloud-based-mailboxes-for-on-premises-users.md) użytkowników lokalnych w Microsoft 365

- [Wyświetl statystyki słów kluczowych](view-keyword-statistics-for-content-search.md) dla wyników wyszukiwania, a następnie w razie potrzeby uściślij zapytanie

- [Wyszukaj dane innych firm zaimportowane](use-content-search-to-search-third-party-data-that-was-imported.md) do Microsoft 365

- [Zachowaj adresatów programu Bcc](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) , aby można było ich wyszukać

## <a name="perform-actions-on-content-you-find"></a>Wykonywanie akcji dotyczących zawartości, którą znajdziesz

Po uruchomieniu wyszukiwania i uściślaniu go w razie potrzeby następnym krokiem jest zrobienie czegoś z wynikami zwróconymi przez wyszukiwanie. Możesz wyeksportować i pobrać wyniki na komputer lokalny lub w przypadku ataku poczty e-mail na organizację możesz usunąć wyniki wyszukiwania ze skrzynek pocztowych użytkowników.
  
- [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md) i pobieranie ich na komputer lokalny

- [Wyszukiwanie i usuwanie wiadomości e-mail](search-for-and-delete-messages-in-your-organization.md), takich jak wiadomości z zawartością wirusa, niebezpieczne załączniki lub wiadomości wyłudzające informacje

- [Eksportowanie raportu](export-a-content-search-report.md) o wynikach wyszukiwania zawartości bez eksportowania rzeczywistych wyników

## <a name="learn-more-about-content-search"></a>Dowiedz się więcej o wyszukiwaniu zawartości

Wyszukiwanie zawartości jest łatwe w użyciu, ale jest również zaawansowanym narzędziem. Za kulisami dzieje się wiele. Więcej informacji na ten temat i zrozumienie jego zachowania i ograniczeń, tym bardziej pomyślne będziesz używać go do celów wyszukiwania i badania w organizacji. Dowiedz się więcej o:
  
- [Limity wyszukiwania zawartości](limits-for-content-search.md), takie jak maksymalna liczba wyszukiwań, które można uruchomić w tym samym czasie, oraz maksymalna liczba lokalizacji zawartości, które można uwzględnić w jednym wyszukiwaniu

- [Szacowane i rzeczywiste wyniki wyszukiwania](differences-between-estimated-and-actual-ediscovery-search-results.md) oraz przyczyny, dla których mogą występować różnice między nimi podczas eksportowania i pobierania wyników wyszukiwania

- [Częściowo indeksowane elementy w Exchange i SharePoint](partially-indexed-items-in-content-search.md) oraz sposób ich dołączania lub wykluczania podczas eksportowania i pobierania wyników wyszukiwania

- [Badanie częściowo indeksowanych elementów](investigating-partially-indexed-items-in-ediscovery.md) i określanie narażenia organizacji na nie

- [De-duplikowanie w wynikach wyszukiwania](de-duplication-in-ediscovery-search-results.md) , które można włączyć podczas eksportowania wiadomości e-mail, które są wynikami wyszukiwania

## <a name="use-scripts-for-advanced-scenarios"></a>Używanie skryptów w scenariuszach zaawansowanych

Czasami trzeba wykonywać bardziej zaawansowane, złożone i powtarzalne zadania wyszukiwania zawartości. W takich przypadkach korzystanie z poleceń w programie PowerShell Centrum zgodności & zabezpieczeń jest łatwiejsze i szybsze. Aby ułatwić to, utworzyliśmy szereg skryptów programu PowerShell Centrum zgodności & zabezpieczeń, które ułatwiają wykonywanie złożonych zadań związanych z wyszukiwaniem zawartości.

- [Wyszukaj określone skrzynki pocztowe i foldery lokacji (nazywane](use-content-search-for-targeted-collections.md)  *docelową* kolekcją), gdy masz pewność, że elementy reagujące na przypadek znajdują się w tym folderze

- [Wyszukaj listę użytkowników w skrzynce pocztowej i lokalizacji OneDrive](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md)

- [Tworzenie, raportowanie i usuwanie wielu wyszukiwań w](create-report-on-and-delete-multiple-content-searches.md) celu szybkiego i wydajnego identyfikowania i usuwania danych wyszukiwania

- [Sklonuj wyszukiwanie zawartości](clone-a-content-search.md) i szybko porównaj wyniki różnych zapytań wyszukiwania słów kluczowych uruchamianych w tych samych lokalizacjach zawartości; lub użyj skryptu, aby zaoszczędzić czas, nie mając konieczności ponownego wprowadzania dużej liczby lokalizacji zawartości podczas tworzenia nowego wyszukiwania
