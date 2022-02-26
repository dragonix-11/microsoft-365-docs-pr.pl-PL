---
title: Udostępnione skrzynki pocztowe — informacje
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Udostępnione skrzynki pocztowe są używane, gdy wiele osób potrzebuje dostępu do tej samej skrzynki pocztowej. Dowiedz się, co należy wiedzieć przed utworzeniem udostępnionej skrzynki pocztowej.
ms.openlocfilehash: 2fbf07fbe71ccb42411f5808aa923d7179d2f13d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "62973816"
---
# <a name="about-shared-mailboxes"></a>Udostępnione skrzynki pocztowe — informacje

Udostępnione skrzynki pocztowe są używane, gdy wiele osób potrzebuje dostępu do tej samej skrzynki pocztowej, na przykład do informacji firmowej, adresu e-mail pomocy technicznej, recepcji lub w przypadku innej funkcji, którą może pełnić wiele osób.

Użytkownicy mający uprawnienia do skrzynki pocztowej grupy mogą wysyłać wiadomości e-mail z adresu tej skrzynki pocztowej lub w jej imieniu, jeśli administrator udzielił użytkownikom odpowiednich uprawnień. Jest to szczególnie przydatne w przypadku skrzynek pocztowych pomocy i obsługi technicznej, ponieważ użytkownicy mogą wysyłać wiadomości e-mail jako „Pomoc techniczna firmy Contoso” lub „Recepcja w budynku A”.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed [utworzeniem udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) należy poznać kilka rzeczy:

- **Licencje:** W udostępnionej skrzynce pocztowej można przechować maksymalnie 50 GB danych bez przypisywania do niego licencji. Aby móc przechować więcej danych w skrzynce pocztowej, należy przypisać do niej licencję. Aby uzyskać więcej szczegółowych informacji na temat licencjonowania udostępnionej skrzynki pocztowej, zobacz [Exchange Online limity](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Po osiągnięciu limitu miejsca do magazynowania w udostępnionej skrzynce pocztowej będzie można przez pewien czas odbierać pocztę e-mail, ale nie będzie można wysyłać nowych wiadomości. Po tym czasie odbieranie poczty e-mail zostanie również zatrzymane. Osoby wysyłające wiadomości e-mail do takiej skrzynki pocztowej będą otrzymywały powiadomienie o niedostarczeniu.

- **Uprawnienia użytkowników:** Musisz nadać użytkownikom uprawnienia (członkostwo) do korzystania z udostępnionej skrzynki pocztowej. Tylko osoby z organizacji mogą korzystać z udostępnionej skrzynki pocztowej.

- **Użytkownicy zewnętrzni:** Osobom spoza firmy (na przykład osobom z kontem Gmail) nie można udzielić dostępu do udostępnionej skrzynki pocztowej. Jeśli chcesz to zrobić, lepszym rozwiązaniem może być utworzenie grupy dla programu Outlook. Aby dowiedzieć się więcej, [zobacz Tworzenie grupy Microsoft 365 w centrum administracyjnym](../create-groups/create-groups.md).

- **Używanie z usługą Outlook:** oprócz korzystania z programu Outlook w sieci Web z przeglądarki w celu uzyskiwania dostępu do udostępnionych skrzynek pocztowych możesz też używać aplikacji Outlook dla systemu iOS lub aplikacji Outlook dla systemu Android. Aby dowiedzieć się więcej, [zobacz Dodawanie udostępnionej skrzynki pocztowej do Outlook urządzenia przenośnego](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). Innym rozwiązaniem jest utworzenie grupy dla udostępnionej skrzynki pocztowej. Aby dowiedzieć się więcej, zobacz [Porównanie grup](../create-groups/compare-groups.md).

- **Szyfrowanie:** Nie można szyfrować wiadomości e-mail wysyłanych z udostępnionej skrzynki pocztowej. Jest tak, ponieważ udostępniona skrzynka pocztowa nie ma własnego kontekstu zabezpieczeń (nazwy użytkownika/hasła), więc nie można jej przypisać do klucza. Jeśli do grupy należy więcej niż jedna osoba, która wysyła/odbiera wiadomości e-mail zaszyfrowane za pomocą własnych kluczy, inni członkowie mogą nie być w stanie odczytać tych wiadomości, a inni nie, w zależności od klucza publicznego, który został zaszyfrowany.

- **Konwersja skrzynki pocztowej:** Skrzynki pocztowe użytkowników można konwertować na udostępnione skrzynki pocztowe. Zobacz [Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md).

- **Role administratorów:** Użytkownicy z administratorem globalnym lub administratorami Exchange mogą tworzyć udostępnione skrzynki pocztowe.

- **Wymagania dotyczące subskrypcji:** Aby utworzyć udostępnioną skrzynkę pocztową, musisz zasubskrybować plan usługi Microsoft 365 dla firm, który obejmuje pocztę e-mail (usługę Exchange Online poczty). Subskrypcja Aplikacje Microsoft 365 dla firm nie obejmuje poczty e-mail. Microsoft 365 Business Standard e-mail.

- **Logowanie:** Udostępniona skrzynka pocztowa nie jest przeznaczona do bezpośredniego logowania przez skojarzone z nią konto użytkownika. Zawsze należy zablokować logowanie do konta udostępnionej skrzynki pocztowej i zachować je zablokowane.

- **Zbyt wielu użytkowników:** Jeśli jednocześnie wielu wyznaczonych użytkowników uzyskuje dostęp do udostępnionej skrzynki pocztowej (zalecane jest nie więcej niż 25), mogą sporadycznie nie nawiązać połączenia z tą skrzynką pocztową lub występują niespójności, takie jak zduplikowane wiadomości w skrzynce nadawczej. W takim przypadku możesz rozważyć zmniejszenie liczby użytkowników lub użycie innego obciążenia pracą, takiego jak grupa Microsoft 365 lub folder publiczny.

- **Usuwanie wiadomości:** Niestety, nie można uniemożliwić usuwania wiadomości z udostępnionej skrzynki pocztowej. Jedynym sposobem na to jest utworzenie grupy Microsoft 365 zamiast udostępnionej skrzynki pocztowej. Grupa w programie Outlook przypomina udostępnioną skrzynkę pocztową. Aby uzyskać ich porównanie, zobacz [Porównanie grup](../create-groups/compare-groups.md). Aby dowiedzieć się więcej o grupach, zobacz [Dowiedz się więcej o grupach](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Multi-Geo** W środowisku wielokierunkowym udostępnione skrzynki pocztowe muszą być licencjonowane w taki sam sposób jak w przypadku skrzynki pocztowej użytkownika. Zwróć uwagę, że inspekcja skrzynek pocztowych między lokalizacjami geograficznymi nie jest obsługiwana. Jeśli na przykład użytkownikowi przypisano uprawnienia dostępu do udostępnionej skrzynki pocztowej w innej lokalizacji geograficznej, akcje skrzynki pocztowej wykonywane przez tego użytkownika nie są rejestrowane w dzienniku inspekcji skrzynki pocztowej udostępnionej skrzynki pocztowej. 


> [!NOTE]
> Aby uzyskać dostęp do udostępnionej skrzynki pocztowej, użytkownik musi mieć licencję usługi Exchange Online, ale udostępniona skrzynka pocztowa nie wymaga osobnej licencji. Każda udostępniona skrzynka pocztowa ma odpowiednie konto użytkownika. Zwróć uwagę, że podczas tworzenia udostępnionej skrzynki pocztowej nie poproszono Cię o podanie hasła? Konto ma hasło, ale jest generowane przez system (nieznany). Nie należy logować się do udostępnionej skrzynki pocztowej przy użyciu tego konta. Bez licencji rozmiar udostępnionych skrzynek pocztowych jest ograniczony do 50 GB. Aby zwiększyć limit rozmiaru do 100 GB, udostępniona skrzynka pocztowa musi mieć przypisaną licencję Exchange Online Plan 2. Licencja Exchange Online Plan 1 z licencją dodatku Exchange Online — archiwum spowoduje tylko zwiększenie rozmiaru archiwaowej skrzynki pocztowej. Umożliwi to również automatyczne rozszerzanie archiwizacji w celu dodatkowej pojemności archiwum. Podobnie, jeśli chcesz umieścić udostępnioną skrzynkę pocztową w związku z postępowaniem sądowym, udostępniona skrzynka pocztowa musi mieć licencję programu Exchange Online Plan 2 lub licencję planu Exchange Online Plan 1 z licencją dodatku Exchange Online — archiwum. Jeśli chcesz zastosować zaawansowane funkcje, takie jak usługa Microsoft Defender Office 365, Advanced eDiscovery lub automatyczne zasady przechowywania, udostępniona skrzynka pocztowa musi być licencjonowana na te funkcje.

## <a name="related-content"></a>Zawartość pokrewna

[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
