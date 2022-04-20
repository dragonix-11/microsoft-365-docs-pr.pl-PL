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
description: Użyj funkcji wyszukiwania i przeczyszczania w portalu zgodności usługi Microsoft Purview, aby wyszukać i usunąć wiadomość e-mail ze wszystkich skrzynek pocztowych w organizacji.
ms.openlocfilehash: 23eeff8078dbd7ab65b0bddb9684aa81d65aab94
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936252"
---
# <a name="search-for-and-delete-email-messages"></a>Wyszukaj i usuń wiadomości e-mail

**Ten artykuł jest przeznaczony dla administratorów. Czy próbujesz znaleźć elementy w skrzynce pocztowej, które chcesz usunąć? Zobacz [Znajdowanie wiadomości lub elementu za pomocą wyszukiwania błyskawicznego](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

Funkcja wyszukiwania zawartości umożliwia wyszukiwanie i usuwanie wiadomości e-mail ze wszystkich skrzynek pocztowych w organizacji. Może to pomóc w znalezieniu i usunięciu potencjalnie szkodliwych wiadomości e-mail lub wiadomości e-mail wysokiego ryzyka, takich jak:

- Wiadomości zawierające niebezpieczne załączniki lub wirusy

- Wiadomości wyłudzające informacje

- Komunikaty zawierające dane poufne

> [!TIP]
> Jeśli Twoja organizacja ma subskrypcję planu Ochrona usługi Office 365 w usłudze Defender 2, zalecamy skorzystanie z procedury opisanej w artykule [Korygowanie złośliwych wiadomości e-mail dostarczonych w Office 365](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365), zamiast postępować zgodnie z procedurą opisaną w tym artykule.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Przepływ pracy wyszukiwania i przeczyszczania opisany w tym artykule nie usuwa wiadomości czatu ani innej zawartości z Microsoft Teams. Jeśli wyszukiwanie zawartości utworzone w kroku 2 zwraca elementy z Microsoft Teams, te elementy nie zostaną usunięte podczas przeczyszczania elementów w kroku 3. Aby wyszukać i usunąć wiadomości czatu, zobacz [Wyszukiwanie i przeczyszczanie wiadomości czatu w Teams](search-and-delete-Teams-chat-messages.md).

- Aby utworzyć i uruchomić wyszukiwanie zawartości, musisz być członkiem grupy ról **menedżera zbierania elektronicznych materiałów dowodowych** lub mieć przypisaną rolę **Wyszukiwanie zgodności** w portalu zgodności usługi Microsoft Purview. Aby usunąć komunikaty, musisz być członkiem grupy ról **Zarządzanie organizacją** lub mieć przypisaną rolę **Wyszukaj i przeczyszczanie** w centrum zgodności Aby uzyskać informacje o dodawaniu użytkowników do grupy ról, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

  > [!NOTE]
  > Grupa ról **Zarządzanie organizacją** istnieje zarówno w Exchange Online, jak i w portalu zgodności. Są to oddzielne grupy ról, które dają różne uprawnienia. Bycie członkiem **zarządzania organizacją** w Exchange Online nie udziela wymaganych uprawnień do usuwania wiadomości e-mail. Jeśli nie masz przypisanej roli **Wyszukaj i przeczyszczanie** w centrum zgodności (bezpośrednio lub za pośrednictwem grupy ról, takiej jak **Zarządzanie organizacją**), po uruchomieniu polecenia cmdlet **New-ComplianceSearchAction** w kroku 3 zostanie wyświetlony komunikat "Nie można odnaleźć parametru zgodnego z nazwą parametru "Przeczyszczanie".

- Aby usunąć komunikaty, musisz użyć programu PowerShell Centrum zgodności & zabezpieczeń. Aby uzyskać instrukcje dotyczące nawiązywania połączenia, zobacz [Krok 1](#step-1-connect-to-security--compliance-center-powershell) .

- Jednocześnie można usunąć maksymalnie 10 elementów na skrzynkę pocztową. Ponieważ możliwość wyszukiwania i usuwania wiadomości ma być narzędziem reagowania na zdarzenia, ten limit pomaga zapewnić szybkie usunięcie wiadomości ze skrzynek pocztowych. Ta funkcja nie jest przeznaczona do czyszczenia skrzynek pocztowych użytkowników.

- Maksymalna liczba skrzynek pocztowych w wyszukiwaniu zawartości, których można użyć do usunięcia elementów, wykonując akcję wyszukiwania i przeczyszczania, wynosi 50 000. Jeśli wyszukiwanie (utworzone w [kroku 2](#step-2-create-a-content-search-to-find-the-message-to-delete) wyszukuje ponad 50 000 skrzynek pocztowych), akcja przeczyszczania (utworzona w kroku 3) zakończy się niepowodzeniem. Wyszukiwanie ponad 50 000 skrzynek pocztowych w jednym wyszukiwaniu może zazwyczaj nastąpić podczas konfigurowania wyszukiwania tak, aby uwzględniało wszystkie skrzynki pocztowe w organizacji. To ograniczenie nadal ma zastosowanie nawet wtedy, gdy mniej niż 50 000 skrzynek pocztowych zawiera elementy zgodne z zapytaniem wyszukiwania. Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać wskazówki dotyczące używania filtrów uprawnień wyszukiwania do wyszukiwania i przeczyszczania elementów z ponad 50 000 skrzynek pocztowych.

- Procedura opisana w tym artykule może służyć tylko do usuwania elementów w Exchange Online skrzynkach pocztowych i folderach publicznych. Nie można jej używać do usuwania zawartości z witryn SharePoint lub OneDrive dla Firm.

- Nie można usunąć elementów wiadomości e-mail w zestawie przeglądów w przypadku zbierania elektronicznych materiałów dowodowych (Premium), korzystając z procedur opisanych w tym artykule. Dzieje się tak dlatego, że elementy w zestawie przeglądów są przechowywane w lokalizacji Storage platformy Azure, a nie w usłudze na żywo. Oznacza to, że nie zostaną one zwrócone przez wyszukiwanie zawartości utworzone w kroku 1. Aby usunąć elementy w zestawie przeglądów, należy usunąć przypadek zbierania elektronicznych materiałów dowodowych (Premium), który zawiera zestaw przeglądów. Aby uzyskać więcej informacji, zobacz [Zamykanie lub usuwanie sprawy zbierania elektronicznych materiałów dowodowych (Premium](close-or-delete-case.md)).

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Krok 1. Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń

Pierwszym krokiem jest nawiązanie połączenia z programem PowerShell Centrum zgodności usługi Security & dla Twojej organizacji. Aby uzyskać instrukcje krok po kroku, zobacz [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>Krok 2. Tworzenie wyszukiwania zawartości w celu znalezienia komunikatu do usunięcia

Drugim krokiem jest utworzenie i uruchomienie wyszukiwania zawartości w celu znalezienia wiadomości, którą chcesz usunąć ze skrzynek pocztowych w organizacji. Wyszukiwanie można utworzyć przy użyciu portalu zgodności lub uruchamiając polecenia cmdlet **New-ComplianceSearch** i **Start-ComplianceSearch** w programie PowerShell Security & Compliance. Komunikaty zgodne z zapytaniem dla tego wyszukiwania zostaną usunięte przez uruchomienie polecenia **New-ComplianceSearchAction -Purge** w [kroku 3](#step-3-delete-the-message). Aby uzyskać informacje na temat tworzenia wyszukiwania zawartości i konfigurowania zapytań wyszukiwania, zobacz następujące tematy:

- [Wyszukiwanie zawartości w Office 365](content-search.md)

- [Zapytania słów kluczowych dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md)

- [New-ComplianceSearch](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> Lokalizacje zawartości, które są przeszukiwane w wyszukiwaniu zawartości utworzonym w tym kroku, nie mogą zawierać witryn SharePoint ani OneDrive dla Firm. W wyszukiwaniu zawartości można dołączyć tylko skrzynki pocztowe i foldery publiczne, które będą używane do wiadomości e-mail. Jeśli wyszukiwanie zawartości zawiera witryny, po uruchomieniu polecenia cmdlet **New-ComplianceSearchAction** w kroku 3 zostanie wyświetlony błąd.

### <a name="tips-for-finding-messages-to-remove"></a>Wskazówki do znajdowania komunikatów do usunięcia

Celem zapytania wyszukiwania jest zawężenie wyników wyszukiwania tylko do wiadomości lub komunikatów, które chcesz usunąć. Oto kilka wskazówek:

- Jeśli znasz dokładny tekst lub frazę używaną w wierszu tematu wiadomości, użyj właściwości **Podmiot** w zapytaniu wyszukiwania.

- Jeśli wiesz, że dokładna data (lub zakres dat) komunikatu, uwzględnij właściwość **Odebrano** w zapytaniu wyszukiwania.

- Jeśli wiesz, kto wysłał komunikat, uwzględnij właściwość **From** w zapytaniu wyszukiwania.

- Wyświetl podgląd wyników wyszukiwania, aby sprawdzić, czy wyszukiwanie zwróciło tylko komunikat (lub komunikaty), które chcesz usunąć.

- Użyj statystyk szacowania wyszukiwania (wyświetlanych w okienku szczegółów wyszukiwania w portalu zgodności lub za pomocą polecenia cmdlet [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch) ), aby uzyskać łączną liczbę wyników.

Poniżej przedstawiono dwa przykłady zapytań w celu znalezienia podejrzanych wiadomości e-mail.

- To zapytanie zwraca komunikaty odebrane przez użytkowników w okresie od 13 kwietnia 2016 r. do 14 kwietnia 2016 r. i zawierające wyrazy "action" i "required" w wierszu tematu.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- To zapytanie zwraca komunikaty wysyłane przez chatsuwloginsset12345@outlook.com i zawierające dokładną frazę "Aktualizuj informacje o koncie" w wierszu tematu.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

Oto przykład użycia zapytania do utworzenia i rozpoczęcia wyszukiwania przez uruchomienie poleceń cmdlet **New-ComplianceSearch** i **Start-ComplianceSearch** w celu wyszukania wszystkich skrzynek pocztowych w organizacji:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>Krok 3. Usuwanie komunikatu

Po utworzeniu i uściśleniu wyszukiwania zawartości w celu zwrócenia komunikatów, które chcesz usunąć, ostatnim krokiem jest uruchomienie polecenia **New-ComplianceSearchAction -Purge** w programie PowerShell Security & Compliance w celu usunięcia komunikatu. Komunikat można usunąć nietrwale lub na stałe. Komunikat o usunięciu nietrwałym jest przenoszony do folderu Elementy możliwe do odzyskania użytkownika i przechowywany do momentu wygaśnięcia okresu przechowywania usuniętego elementu. Wiadomości usunięte na stałe są oznaczone do trwałego usunięcia ze skrzynki pocztowej i zostaną trwale usunięte przy następnym przetworzeniu skrzynki pocztowej przez Asystenta folderów zarządzanych. Jeśli odzyskiwanie pojedynczego elementu jest włączone dla skrzynki pocztowej, usunięte elementy zostaną trwale usunięte po upływie okresu przechowywania usuniętego elementu. Jeśli skrzynka pocztowa zostanie wstrzymana, usunięte wiadomości zostaną zachowane do czasu wygaśnięcia czasu przechowywania elementu lub do momentu usunięcia blokady ze skrzynki pocztowej.

> [!NOTE]
> Jak wspomniano wcześniej, elementy z Microsoft Teams zwracane przez wyszukiwanie zawartości nie są usuwane po uruchomieniu polecenia **New-ComplianceSearchAction -Purge**.

Aby uruchomić następujące polecenia w celu usunięcia komunikatów, upewnij się, że masz [połączenie z programem PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

### <a name="soft-delete-messages"></a>Komunikaty usuwania nietrwałego

W poniższym przykładzie polecenie nietrwale usuwa wyniki wyszukiwania zwrócone przez wyszukiwanie zawartości o nazwie "Usuń wiadomość wyłudzającą informacje".

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>Komunikaty o twardym usunięciu

Aby usunąć elementy zwrócone przez wyszukiwanie zawartości "Usuń wiadomość wyłudzającą informacje", należy uruchomić następujące polecenie:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

Po uruchomieniu poprzednich poleceń w celu usunięcia komunikatów nietrwałych lub twardych wyszukiwanie określone przez parametr  *SearchName*  to wyszukiwanie zawartości utworzone w kroku 1.

Aby uzyskać więcej informacji, zobacz [New-ComplianceSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Więcej informacji

- **Jak uzyskać stan operacji wyszukiwania i usuwania?**

  Uruchom polecenie **Get-ComplianceSearchAction** , aby uzyskać stan operacji usuwania. Obiekt tworzony podczas uruchamiania polecenia cmdlet **New-ComplianceSearchAction** nosi nazwę przy użyciu następującego formatu:  `<name of Content Search>_Purge`.

- **Co się stanie po usunięciu komunikatu?**

  Komunikat usunięty za pomocą  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` polecenia jest przenoszony do folderu Przeczyszczanie i użytkownik nie może uzyskać do nich dostępu. Po przeniesieniu wiadomości do folderu Przeczyszczanie wiadomość jest zachowywana przez czas przechowywania usuniętego elementu, jeśli dla skrzynki pocztowej włączono odzyskiwanie pojedynczego elementu. (W Microsoft 365 odzyskiwanie pojedynczego elementu jest domyślnie włączone podczas tworzenia nowej skrzynki pocztowej). Po upływie okresu przechowywania usuniętego elementu wiadomość zostanie oznaczona do trwałego usunięcia i zostanie usunięta z Microsoft 365 następnym razem, gdy skrzynka pocztowa zostanie przetworzona przez asystenta folderu zarządzanego.

  Jeśli użyjesz `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` polecenia, komunikaty zostaną przeniesione do folderu Usuwanie w folderze Elementy możliwe do odzyskania użytkownika. Nie jest natychmiast czyszczony z Microsoft 365. Użytkownik może odzyskać komunikaty w folderze Elementy usunięte na czas trwania na podstawie okresu przechowywania usuniętego elementu skonfigurowanego dla skrzynki pocztowej. Po upływie tego okresu przechowywania (lub jeśli użytkownik przeczyści komunikat przed jego wygaśnięciem), komunikat zostanie przeniesiony do folderu Przeczyszczanie i użytkownik nie będzie już mógł uzyskać do niego dostępu. W folderze Przeczyszczanie wiadomość jest przechowywana przez cały czas na podstawie okresu przechowywania usuniętego elementu skonfigurowanego dla skrzynki pocztowej, jeśli dla skrzynki pocztowej włączono odzyskiwanie pojedynczych elementów. (W Microsoft 365 odzyskiwanie pojedynczego elementu jest domyślnie włączone podczas tworzenia nowej skrzynki pocztowej). Po upływie okresu przechowywania usuniętego elementu wiadomość zostanie oznaczona do trwałego usunięcia i zostanie usunięta z Microsoft 365 następnym razem, gdy skrzynka pocztowa zostanie przetworzona przez asystenta folderu zarządzanego.

- **Co zrobić, jeśli musisz usunąć wiadomość z ponad 50 000 skrzynek pocztowych?**

  Jak wspomniano wcześniej, można wykonać operację wyszukiwania i przeczyszczania na maksymalnie 50 000 skrzynek pocztowych (nawet jeśli mniej niż 50 000 zawiera elementy zgodne z zapytaniem wyszukiwania). Jeśli musisz wykonać operację wyszukiwania i przeczyszczania na ponad 50 000 skrzynek pocztowych, rozważ utworzenie tymczasowych filtrów uprawnień wyszukiwania, które zmniejszą liczbę skrzynek pocztowych, które będą przeszukiwane do mniej niż 50 000 skrzynek pocztowych. Jeśli na przykład organizacja zawiera skrzynki pocztowe w różnych działach, stanach lub krajach, możesz utworzyć filtr uprawnień wyszukiwania skrzynki pocztowej na podstawie jednej z tych właściwości skrzynki pocztowej, aby wyszukać podzbiór skrzynek pocztowych w organizacji. Po utworzeniu filtru uprawnień wyszukiwania należy utworzyć wyszukiwanie (opisane w kroku 1), a następnie usunąć komunikat (opisany w kroku 3). Następnie możesz edytować filtr, aby wyszukiwać i czyścić wiadomości w innym zestawie skrzynek pocztowych. Aby uzyskać więcej informacji na temat tworzenia filtrów uprawnień wyszukiwania, zobacz [Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości](permissions-filtering-for-content-search.md).

- **Czy elementy niezainicjowane uwzględnione w wynikach wyszukiwania zostaną usunięte?**

  Nie, polecenie "New-ComplianceSearchAction -Purge" nie usuwa elementów bez certyfikatu.

- **Co się stanie, jeśli wiadomość zostanie usunięta ze skrzynki pocztowej, która została umieszczona w In-Place wstrzymania lub blokady postępowania sądowego lub została przypisana do zasad przechowywania Microsoft 365?**

  Po usunięciu komunikatu i przeniesieniu go do folderu Przeczyszczanie komunikat zostanie zachowany do czasu wygaśnięcia czasu przechowywania. Jeśli czas przechowywania jest nieograniczony, elementy są zachowywane do momentu usunięcia blokady lub zmiany czasu trwania blokady.

- **Dlaczego przepływ pracy wyszukiwania i usuwania jest podzielony między różne grupy ról centrum zabezpieczeń i zgodności?**

  Jak wyjaśniono wcześniej, osoba musi być członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych lub mieć przypisaną rolę zarządzania wyszukiwaniem zgodności do przeszukiwania skrzynek pocztowych. Aby usunąć komunikaty, osoba musi być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania wyszukiwaniem i przeczyszczaniem. Dzięki temu można kontrolować, kto może przeszukiwać skrzynki pocztowe w organizacji i kto może usuwać wiadomości.
