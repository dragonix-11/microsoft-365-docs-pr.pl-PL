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
ms.openlocfilehash: a384440b64b84618831b8065bd40d89200ea47d0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971539"
---
# <a name="about-shared-mailboxes"></a>Udostępnione skrzynki pocztowe — informacje

Udostępnione skrzynki pocztowe są używane, gdy wiele osób potrzebuje dostępu do tej samej skrzynki pocztowej, na przykład do informacji firmowej, adresu e-mail pomocy technicznej, recepcji lub w przypadku innej funkcji, którą może pełnić wiele osób.

Użytkownicy mający uprawnienia do skrzynki pocztowej grupy mogą wysyłać wiadomości e-mail z adresu tej skrzynki pocztowej lub w jej imieniu, jeśli administrator udzielił użytkownikom odpowiednich uprawnień. Jest to szczególnie przydatne w przypadku skrzynek pocztowych pomocy i obsługi technicznej, ponieważ użytkownicy mogą wysyłać wiadomości e-mail jako „Pomoc techniczna firmy Contoso” lub „Recepcja w budynku A”.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed [utworzeniem udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) należy znać następujące kwestie:

- **Licencje:** Udostępniona skrzynka pocztowa może przechowywać do 50 GB danych bez przypisywania do niej licencji. Aby móc przechować więcej danych w skrzynce pocztowej, należy przypisać do niej licencję. Aby uzyskać więcej informacji na temat licencjonowania udostępnionej skrzynki pocztowej, zobacz [Exchange Online Limity](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Po osiągnięciu limitu miejsca do magazynowania w udostępnionej skrzynce pocztowej będzie można przez pewien czas odbierać pocztę e-mail, ale nie będzie można wysyłać nowych wiadomości. Po tym czasie odbieranie poczty e-mail zostanie również zatrzymane. Osoby wysyłające wiadomości e-mail do takiej skrzynki pocztowej będą otrzymywały powiadomienie o niedostarczeniu.

- **Uprawnienia użytkownika:** Musisz nadać użytkownikom uprawnienia (członkostwo) do korzystania z udostępnionej skrzynki pocztowej. Tylko osoby z organizacji mogą korzystać z udostępnionej skrzynki pocztowej.

- **Użytkownicy zewnętrzni:** Nie możesz udzielić osobom spoza firmy (takim jak osoby z kontem Gmail) dostępu do udostępnionej skrzynki pocztowej. Jeśli chcesz to zrobić, lepszym rozwiązaniem może być utworzenie grupy dla programu Outlook. Aby dowiedzieć się więcej, zobacz [Tworzenie grupy Microsoft 365 w centrum administracyjnym](../create-groups/create-groups.md).

- **Używanie z Outlook:** oprócz używania Outlook w sieci Web z przeglądarki do uzyskiwania dostępu do udostępnionych skrzynek pocztowych można również użyć Outlook dla aplikacji systemu iOS lub aplikacji Outlook dla systemu Android. Aby dowiedzieć się więcej, zobacz [Dodawanie udostępnionej skrzynki pocztowej do Outlook urządzenia przenośnego](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). Inną opcją jest utworzenie grupy dla udostępnionej skrzynki pocztowej. Aby dowiedzieć się więcej, zobacz [Porównanie grup](../create-groups/compare-groups.md).

- **Szyfrowania:** Nie można zaszyfrować wiadomości e-mail wysyłanych z udostępnionej skrzynki pocztowej. Dzieje się tak, ponieważ udostępniona skrzynka pocztowa nie ma własnego kontekstu zabezpieczeń (nazwy użytkownika/hasła), więc nie można jej przypisać do klucza. Jeśli więcej niż jedna osoba jest członkiem i wysyła/odbiera wiadomości e-mail zaszyfrowane przy użyciu własnych kluczy, inni członkowie mogą być w stanie odczytać wiadomość e-mail, a inni nie, w zależności od klucza publicznego, za pomocą którego wiadomość e-mail została zaszyfrowana.

- **Konwersja skrzynki pocztowej:** Skrzynki pocztowe użytkowników można konwertować na udostępnione skrzynki pocztowe. Zobacz [Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md).

- **Role administratora:** Użytkownicy z rolami administratora globalnego lub administratora Exchange mogą tworzyć udostępnione skrzynki pocztowe.

- **Wymagania dotyczące subskrypcji:** Aby utworzyć udostępnioną skrzynkę pocztową, musisz zasubskrybować Microsoft 365 dla planu biznesowego obejmującego pocztę e-mail (usługę Exchange Online). Subskrypcja Aplikacje Microsoft 365 dla firm nie zawiera poczty e-mail. Microsoft 365 Business Standard zawiera wiadomość e-mail.

- **Logowanie:** Udostępniona skrzynka pocztowa nie jest przeznaczona do bezpośredniego logowania przez skojarzone konto użytkownika. Zawsze należy blokować logowanie do udostępnionego konta skrzynki pocztowej i blokować je.

- **Zbyt wielu użytkowników:** Jeśli zbyt wielu wyznaczonych użytkowników jednocześnie uzyskuje dostęp do udostępnionej skrzynki pocztowej (zalecane jest nie więcej niż 25), mogą sporadycznie nie nawiązać połączenia z tą skrzynką pocztową lub występują niespójności, takie jak duplikowanie wiadomości w skrzynce wychodzącej. W takim przypadku można rozważyć zmniejszenie liczby użytkowników lub użycie innego obciążenia, takiego jak grupa Microsoft 365 lub folder publiczny.

- **Usuwanie komunikatu:** Niestety nie można uniemożliwić użytkownikom usuwania wiadomości w udostępnionej skrzynce pocztowej. Jedynym sposobem obejścia tego problemu jest [utworzenie grupy Microsoft 365](/microsoft-365/admin/create-groups/create-groups) zamiast udostępnionej skrzynki pocztowej. Grupa w Outlook jest jak udostępniona skrzynka pocztowa. Aby zapoznać się z porównaniem tych dwóch elementów, zobacz [Porównanie grup](../create-groups/compare-groups.md). Aby dowiedzieć się więcej o grupach, zobacz [Dowiedz się więcej o grupach Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Wiele obszarów geograficznych** W środowisku z wieloma lokalizacjami geograficznymi udostępnione skrzynki pocztowe muszą mieć licencję w taki sam sposób, w jaki jest licencjonowana skrzynka pocztowa użytkownika. Należy pamiętać, że inspekcja skrzynek pocztowych między obszarami geograficznymi nie jest obsługiwana. Jeśli na przykład użytkownik ma przypisane uprawnienia dostępu do udostępnionej skrzynki pocztowej w innej lokalizacji geograficznej, akcje skrzynki pocztowej wykonywane przez tego użytkownika nie są rejestrowane w dzienniku inspekcji skrzynki pocztowej udostępnionej skrzynki pocztowej. 


> [!NOTE]
> Aby uzyskać dostęp do udostępnionej skrzynki pocztowej, użytkownik musi mieć licencję Exchange Online, ale udostępniona skrzynka pocztowa nie wymaga oddzielnej licencji. Każda udostępniona skrzynka pocztowa ma odpowiednie konto użytkownika. Zwróć uwagę, że podczas tworzenia udostępnionej skrzynki pocztowej nie poproszono Cię o podanie hasła? Konto ma hasło, ale jest generowane przez system (nieznane). Nie należy używać konta do logowania się do udostępnionej skrzynki pocztowej. Bez licencji udostępnione skrzynki pocztowe są ograniczone do 50 GB. Aby zwiększyć limit rozmiaru do 100 GB, udostępnionej skrzynce pocztowej należy przypisać licencję Exchange Online plan 2. Licencja Exchange Online plan 1 z licencją dodatku Exchange Online — archiwum tylko zwiększy rozmiar skrzynki pocztowej archiwum. Umożliwi to również automatyczne rozszerzanie archiwizacji w celu zwiększenia pojemności magazynu archiwum. Podobnie, jeśli chcesz wstrzymać udostępnioną skrzynkę pocztową, udostępniona skrzynka pocztowa musi mieć licencję Exchange Online plan 2 lub licencję Exchange Online plan 1 z licencją dodatku Exchange Online — archiwum. Jeśli chcesz zastosować zaawansowane funkcje, takie jak Ochrona usługi Office 365 w usłudze Microsoft Defender, eDiscovery (Premium) lub zasady automatycznego przechowywania, udostępniona skrzynka pocztowa musi mieć licencję na te funkcje.

## <a name="related-content"></a>Zawartość pokrewna

[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
