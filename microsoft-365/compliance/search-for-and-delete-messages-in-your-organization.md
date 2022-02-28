---
title: Wyszukiwanie i usuwanie wiadomości e-mail w organizacji
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
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: Funkcja wyszukiwania i przeczyszczania w Centrum zgodności platformy Microsoft 365 umożliwia wyszukiwanie i usuwanie wiadomości e-mail ze wszystkich skrzynek pocztowych w organizacji.
ms.openlocfilehash: 33c65cb61be14d72631fd3a272b68f2dad2ffea6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988050"
---
# <a name="search-for-and-delete-email-messages"></a>Wyszukiwanie i usuwanie wiadomości e-mail

**Ten artykuł jest dla administratorów. Czy próbujesz znaleźć w skrzynce pocztowej elementy, które chcesz usunąć? Zobacz [Znajdowanie wiadomości lub elementu za pomocą wyszukiwania błyskawicznego](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

Za pomocą funkcji Wyszukiwanie zawartości można wyszukiwać i usuwać wiadomości e-mail ze wszystkich skrzynek pocztowych w organizacji. Może to ułatwić znajdowanie i usuwanie potencjalnie niebezpiecznych lub niebezpiecznych wiadomości e-mail, takich jak:

- Wiadomości zawierające niebezpieczne załączniki lub wirusy

- Wiadomości wyłudzdzce informacje

- Wiadomości zawierające poufne dane

> [!CAUTION]
> Wyszukiwanie i przeczyszczanie to zaawansowana funkcja, która umożliwia wszystkim osobom z przypisanymi niezbędnymi uprawnieniami usuwanie wiadomości e-mail ze skrzynek pocztowych w organizacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Przepływ pracy wyszukiwania i przeczyszczania opisany w tym artykule nie powoduje usunięcia wiadomości czatu ani innej zawartości z Microsoft Teams. Jeśli wyszukiwanie zawartości, które tworzysz w kroku 2, zwraca elementy z Microsoft Teams, elementy te nie zostaną usunięte podczas przeczyszczania elementów w kroku 3.

- Aby utworzyć i uruchomić wyszukiwanie zawartości, musisz być członkiem grupy ról Menedżer zbierania  elektronicznych materiałów dowodowych lub mieć przypisaną rolę Wyszukiwanie zgodności w  Centrum zgodności platformy Microsoft 365. Aby usuwać wiadomości, musisz być członkiem grupy ról Zarządzanie  organizacją lub mieć przypisaną rolę Wyszukiwania i [przeczyszczania](assign-ediscovery-permissions.md) w centrum zgodności Aby uzyskać informacje na temat dodawania użytkowników do grupy ról, zobacz Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych.

  > [!NOTE]
  > Grupa **ról Zarządzanie organizacją** istnieje zarówno w Exchange Online, jak i w Centrum zgodności platformy Microsoft 365. Są to osobne grupy ról, które nadawają różne uprawnienia. Jako członek zespołu zarządzania **organizacją w firmie** Exchange Online nie udziela wymaganych uprawnień do usuwania wiadomości e-mail. Jeśli nie masz przypisanej roli Wyszukiwania i  przeczyszczania w centrum zgodności (bezpośrednio lub za pośrednictwem grupy ról, takiej jak Zarządzanie **organizacją), otrzymasz** błąd w kroku 3 po uruchomieniu polecenia cmdlet **New-ComplianceSearchAction** z komunikatem "Nie można odnaleźć parametru, który jest zgodny z nazwą parametru "Purge"".

- Aby usuwać wiadomości, & w Centrum zgodności, należy użyć programu PowerShell w centrum zabezpieczeń. Zobacz [Krok 1](#step-1-connect-to-security--compliance-center-powershell) , aby uzyskać instrukcje dotyczące nawiązywania połączenia.

- Jednocześnie można usunąć maksymalnie 10 elementów na skrzynkę pocztową. Funkcja wyszukiwania i usuwania wiadomości jest w zamierzony sposób narzędziem do reagowania na zdarzenia, dlatego ten limit pomaga szybko usuwać wiadomości ze skrzynek pocztowych. Ta funkcja nie jest przeznaczona do oczyszczania skrzynek pocztowych użytkowników.

- Maksymalna liczba skrzynek pocztowych w przeszukiwaniu zawartości, których można użyć do usuwania elementów przez wykonanie akcji wyszukiwania i przeczyszczania, wynosi 50 000. Jeśli wyszukiwanie (w ramach wyszukiwania w kroku [2](#step-2-create-a-content-search-to-find-the-message-to-delete) ) spowoduje przeszukanie więcej niż 50 000 skrzynek pocztowych, akcja przeczyszczania (tworzyć w kroku 3) nie powiedzie się. Wyszukiwanie w więcej niż 50 000 skrzynek pocztowych w jednym wyszukiwaniu może się zazwyczaj odbywać po skonfigurowaniu wyszukiwania tak, aby uwzględniała wszystkie skrzynki pocztowe w organizacji. To ograniczenie obowiązuje nawet wtedy, gdy mniej niż 50 000 skrzynek pocztowych zawiera elementy zgodne z zapytaniem wyszukiwania. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać wskazówki dotyczące używania filtrów uprawnień wyszukiwania do wyszukiwania i przeczyszczania elementów z ponad 50 000 skrzynek pocztowych.

- Procedura w tym artykule dotyczy tylko usuwania elementów ze skrzynek Exchange Online i folderów publicznych. Nie można go używać do usuwania zawartości z witryn SharePoint ani OneDrive dla Firm internetowych.

- Za pomocą procedur  podanych w tym artykule nie można usuwać elementów Advanced eDiscovery e-mail z zestawu recenzji w przypadku Advanced eDiscovery przypadku. Jest tak, ponieważ elementy w zestawie recenzji są przechowywane w lokalizacji usługi Azure Storage, a nie w usłudze na żywo. Oznacza to, że nie zostaną one zwrócone przez wyszukiwanie zawartości, które tworzysz w kroku 1. Aby usunąć elementy z zestawu recenzji, należy usunąć Advanced eDiscovery przypadku, która zawiera zestaw recenzji. Aby uzyskać więcej informacji, [zobacz Zamykanie lub usuwanie Advanced eDiscovery przypadku](close-or-delete-case.md).

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Krok 1. Połączenie do centrum zabezpieczeń & w programie PowerShell

Pierwszym krokiem jest połączenie się z programem PowerShell & zabezpieczeń w organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do programu PowerShell & centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>Krok 2. Tworzenie wyszukiwania zawartości w celu znalezienia wiadomości do usunięcia

Drugim krokiem jest utworzenie i uruchomienie wyszukiwania zawartości w celu znalezienia wiadomości, którą chcesz usunąć ze skrzynek pocztowych w Twojej organizacji. Możesz utworzyć wyszukiwanie za pomocą narzędzia Centrum zgodności platformy Microsoft 365 lub uruchamiając polecenia cmdlet **New-ComplianceSearch** i **Start-ComplianceSearch** w programie PowerShell pod & zabezpieczeń i zgodności. Wiadomości zgodne z zapytaniem w tym wyszukiwaniu zostaną usunięte, uruchamiając polecenie **New-ComplianceSearchAction -Purge** w [kroku 3](#step-3-delete-the-message). Aby uzyskać informacje na temat tworzenia zapytań wyszukiwania i konfigurowania ich zawartości, zobacz następujące tematy:

- [Wyszukiwanie zawartości w programie Office 365](content-search.md)

- [Zapytania słów kluczowych dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md)

- [Wyszukiwanie nowych zgodności](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> Lokalizacje zawartości, które są przeszukiwane w przeszukiwaniu zawartości, który został przez Ciebie utworzyć w tym kroku, nie mogą obejmować SharePoint ani OneDrive dla Firm witryn. Wyszukiwanie zawartości może obejmować tylko skrzynki pocztowe i foldery publiczne, które będą używane do wiadomości e-mail. Jeśli wyszukiwanie zawartości obejmuje witryny, po uruchomieniu polecenia cmdlet **New-ComplianceSearchAction** w kroku 3 zostanie wyświetlony komunikat o błędzie.

### <a name="tips-for-finding-messages-to-remove"></a>Wskazówki znajdowania wiadomości do usunięcia

Celem zapytania wyszukiwania jest zawężenie wyników wyszukiwania tylko do wiadomości, które chcesz usunąć. Oto kilka porad:

- Jeśli znasz dokładną frazę lub tekst użyty w wierszu tematu wiadomości, użyj właściwości **Temat** w zapytaniu wyszukiwania.

- Jeśli znasz dokładną datę (lub zakres dat) wiadomości, uwzględnij w zapytaniu wyszukiwania właściwość Otrzymano.

- Jeśli wiesz, kto wysłał wiadomość, uwzględnij właściwość **Od** w zapytaniu wyszukiwania.

- Wyświetl podgląd wyników wyszukiwania, aby sprawdzić, czy wyszukiwanie zwróciło tylko wiadomość (lub wiadomości), które chcesz usunąć.

- Statystyka szacowanego wyszukiwania (wyświetlana w okienku szczegółów wyszukiwania w Centrum zgodności platformy Microsoft 365 lub za pomocą polecenia cmdlet [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)) pozwala uzyskać całkowitą liczbę wyników.

Oto dwa przykłady zapytań wyszukiwania podejrzanych wiadomości e-mail.

- To zapytanie zwraca wiadomości otrzymane przez użytkowników między 13 kwietnia 2016 a 14 kwietnia 2016 r., które zawierają wyrazy "akcja" i "wymagane" w wierszu tematu.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- To zapytanie zwraca wiadomości wysłane przez firmę chatsuwloginsset12345@outlook.com zawierające dokładną frazę "Zaktualizuj informacje o koncie" w wierszu tematu.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

Oto przykład użycia zapytania do tworzenia i rozpoczynania wyszukiwania, uruchamiając polecenia cmdlet **New-ComplianceSearch** i **Start-ComplianceSearch** w celu przeszukiwania wszystkich skrzynek pocztowych w organizacji:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>Krok 3. Usunięcie wiadomości

Po utworzeniu i dopracowaniu wyszukiwania zawartości w celu zwrócenia wiadomości, które chcesz usunąć, ostatnim krokiem jest uruchomienie polecenia **New-ComplianceSearchAction -Purge** w programie PowerShell zabezpieczeń & zgodności w celu usunięcia wiadomości. Możesz delikatnie lub trwale usunąć wiadomość. Programowo usunięta wiadomość jest przenoszony do folderu Elementy do odzyskania użytkownika i zachowywana do momentu wygaśnięcia okresu przechowywania elementów usuniętych. Usunięte wiadomości są oznaczane do trwałego usunięcia ze skrzynki pocztowej i zostaną trwale usunięte, gdy następnym razem skrzynka pocztowa zostanie przetworzona przez asystenta folderów zarządzanych. Jeśli dla skrzynki pocztowej włączono odzyskiwanie pojedynczych elementów, elementy usunięte z usuniętymi elementami zostaną trwale usunięte po wygaśnięciu okresu przechowywania elementów usuniętych. Jeśli skrzynka pocztowa znajduje się w posiadaniu, usunięte wiadomości są zachowywane do momentu wygaśnięcia czasu trwania przechowywania elementu lub do czasu usunięcia go ze skrzynki pocztowej.

> [!NOTE]
> Jak wspomniano wcześniej, elementy Microsoft Teams, które są zwracane przez przeszukiwanie zawartości, nie są usuwane po uruchomieniu polecenia **New-ComplianceSearchAction -Purge**.

Aby uruchomić następujące polecenia w celu usunięcia wiadomości, upewnij się, że masz połączenie z programem [PowerShell centrum zabezpieczeń & zgodności](/powershell/exchange/connect-to-scc-powershell).

### <a name="soft-delete-messages"></a>Miękkie usuwanie wiadomości

W poniższym przykładzie polecenie "miękkie" usuwa wyniki wyszukiwania zwrócone przez wyszukiwanie zawartości o nazwie "Usuwanie wiadomości wyłudzającej informacje".

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>Trudne usuwanie wiadomości

Aby trudno usunąć elementy zwrócone przez wyszukiwanie zawartości "Usuń wiadomość wyłudzającą informacje", należy uruchomić to polecenie:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

Po uruchomieniu poprzednich poleceń w celu "miękkiego" lub trudnego usunięcia wiadomości wyszukiwanie określone przez parametr  *SearchName*  jest wyszukiwaniem zawartości utworzonym w kroku 1.

Aby uzyskać więcej informacji, [zobacz New-ComplianceSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Więcej informacji

- **Jak można uzyskać stan operacji wyszukiwania i usuwania?**

  Uruchamianie akcji **Get-ComplianceSearchAction** w celu uzyskania stanu operacji usuwania. Obiekt tworzony po uruchomieniu polecenia cmdlet **New-ComplianceSearchAction** ma nazwę przy użyciu tego formatu:  `<name of Content Search>_Purge`.

- **Co się dzieje po usunięciu wiadomości?**

  Wiadomość usunięta za pomocą tego  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` polecenia jest przenoszony do folderu Przeczyszczania i użytkownik nie może uzyskać do niej dostępu. Po zakończeniu przenoszenia wiadomości do folderu Przeczyszczania jest ona zachowywana przez czas przechowywania elementów usuniętych, jeśli dla skrzynki pocztowej włączono odzyskiwanie pojedynczych elementów. (W Microsoft 365 odzyskiwania pojedynczych elementów jest domyślnie włączone podczas tworzenia nowej skrzynki pocztowej). Po wygaśnięciu okresu przechowywania elementów usuniętych wiadomość jest oznaczana do trwałego usunięcia i zostanie usunięta z programu Microsoft 365 następnym razem, gdy skrzynka pocztowa zostanie przetworzona przez asystenta folderów zarządzanych.

  W przypadku użycia tego `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` polecenia wiadomości są przenoszone do folderu Usunięcia w folderze Elementy do odzyskania użytkownika. Nie jest ona od razu czyszczona z Microsoft 365. Użytkownik może odzyskać wiadomości w folderze Elementy usunięte na czas trwania na podstawie okresu przechowywania elementów usuniętych skonfigurowanego dla skrzynki pocztowej. Gdy ten okres przechowywania wygaśnie (lub jeśli użytkownik oczyści wiadomość przed jej wygaśnięciem), wiadomość zostanie przeniesiona do folderu przeczyszczania i użytkownik nie będzie już miał do niej dostępu. Po w folderze przeczyszczania wiadomość jest zachowywana na czas trwania na podstawie okresu przechowywania elementów usuniętych skonfigurowanego dla skrzynki pocztowej, jeśli dla skrzynki pocztowej włączono odzyskiwanie pojedynczych elementów. (W Microsoft 365 odzyskiwania pojedynczych elementów jest domyślnie włączone podczas tworzenia nowej skrzynki pocztowej). Po wygaśnięciu okresu przechowywania elementów usuniętych wiadomość jest oznaczana do trwałego usunięcia i zostanie usunięta z programu Microsoft 365 przy następnym przetwarzaniu skrzynki pocztowej przez asystenta folderów zarządzanych.

- **Co zrobić, jeśli trzeba usunąć wiadomość z ponad 50 000 skrzynek pocztowych?**

  Jak wspomniano wcześniej, można przeprowadzić wyszukiwanie i przeczyszczanie maksymalnie 50 000 skrzynek pocztowych (nawet jeśli mniej niż 50 000 zawiera elementy zgodne z zapytaniem wyszukiwania). Jeśli musisz wykonać wyszukiwanie i przeczyścić więcej niż 50 000 skrzynek pocztowych, rozważ utworzenie filtrów uprawnień wyszukiwania tymczasowego w celu zmniejszenia liczby skrzynek pocztowych, które zostaną przeszukane do mniej niż 50 000 skrzynek pocztowych. Jeśli na przykład Twoja organizacja zawiera skrzynki pocztowe w różnych wydziałach, stanach lub krajach, możesz utworzyć filtr uprawnień wyszukiwania w skrzynce pocztowej na podstawie jednej z tych właściwości skrzynki pocztowej, aby przeszukać podzbiór skrzynek pocztowych w organizacji. Po utworzeniu filtru uprawnień wyszukiwania należy utworzyć wyszukiwanie (opisane w kroku 1), a następnie usunąć wiadomość (opisane w kroku 3). Następnie możesz edytować filtr, aby wyszukać i przeczyścić wiadomości w innym zestawie skrzynek pocztowych. Aby uzyskać więcej informacji na temat tworzenia filtrów uprawnień wyszukiwania, zobacz [Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości](permissions-filtering-for-content-search.md).

- **Czy elementy nieindeksowane uwzględnione w wynikach wyszukiwania zostaną usunięte?**

  Nie, polecenie "New-ComplianceSearchAction -Purge" nie powoduje usunięcia elementów nieindeksowanych.

- **Co się stanie, jeśli wiadomość zostanie usunięta ze skrzynki pocztowej, która została umieszczona w In-Place hold lub postępowaniem sądowym albo do której przypisano Microsoft 365 przechowywania?**

  Po przeczyszczeniu i przesunięciu wiadomości do folderu przeczyszczania wiadomość jest zachowywana do momentu wygaśnięcia czasu trwania przechowywania. Jeśli czas trwania zawieszonego połączenia jest nieograniczony, elementy są zachowywane do momentu usunięcia zawieszonego połączenia lub zmiany czasu trwania zawieszonego.

- **Dlaczego przepływ pracy wyszukiwania i usuwania jest podzielony na różne grupy ról Centrum zabezpieczeń i zgodności?**

  Jak wyjaśniono wcześniej, osoba musi być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych lub mieć przypisaną rolę zarządzania wyszukiwaniem zgodności do przeszukiwania skrzynek pocztowych. Aby usunąć wiadomości, osoba musi być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania Wyszukiwaniem i przeczyszczanie. Umożliwia to kontrolowanie, kto może przeszukiwać skrzynki pocztowe w organizacji i kto może usuwać wiadomości.
