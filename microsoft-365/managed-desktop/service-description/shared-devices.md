---
title: Urządzenia udostępnione
description: Jak i kiedy używać trybu urządzenia udostępnionego
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 3682087e47db062240b001e8631f73ae8cbc1cda
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015419"
---
# <a name="shared-devices"></a>Urządzenia udostępnione

Microsoft Managed Desktop umożliwia zarejestrowanie urządzeń w "trybie urządzenia udostępnionego", podobnie jak w trybie urządzenia udostępnionego oferowanym przez [Microsoft Intune.](/mem/intune/configuration/shared-user-device-settings)

Urządzenia w tym trybie są zoptymalizowane pod kątem sytuacji, w których użytkownicy nie są powiązani z jednym biurkiem i często zmieniają urządzenia. Mogą to być na przykład pracownicy pierwszej linii (na przykład pracownicy bankowi lub pracownicy, którzy się w nim znajduje). W tym trybie możesz zastosować dowolne profile Microsoft Managed Desktop do [](profiles.md) urządzeń. W przypadku urządzeń zarejestrowanych w tym trybie występują pewne istotne różnice:

- [Przestrzeń dyskowa](#device-storage) urządzeń jest zoptymalizowana dla użytkowników udostępnionych.
- [Nieaktywne konta](#deletion-of-inactive-accounts) są usuwane.
- [Konta gości](#guest-accounts) nie są domyślnie obsługiwane.
- [Microsoft 365 Aplikacje na](#microsoft-365-apps-for-enterprise) urządzenia współużytkowane są zoptymalizowane pod kątem licencjonowania przedsiębiorstwa.

Ponieważ dokonasz wyboru korzystania z trybu urządzenia udostępnionego w punkcie rejestracji w programie Microsoft Managed Desktop, jeśli chcesz później wyjść z tego trybu, musisz go ponownie derejestrować i zarejestrować.

## <a name="when-to-use-shared-device-mode"></a>Kiedy używać trybu urządzenia udostępnionego

W każdej sytuacji, w której użytkownicy często zmieniają urządzenia.

Na przykład informacje bankowe mogą być w jednej lokalizacji służącej do zarządzania wpłatymi, ale przesuną się na back office, aby pomóc klientom z kredytem hipotecznym. W każdej z tych lokalizacji urządzenie działa w różnych aplikacjach i jest zoptymalizowane pod kątem tych zadań, chociaż jest używane przez wiele osób.

Pracownicy osobowi zazwyczaj poruszają się między pomieszczeniami i biurami w interakcji z pacjentami. Mogą zalogować się na stacji roboczej w biurze, ale połączyć się ze swoim pulpitem zdalnym i zrobić notatki, a następnie powtórzyć ten proces w innym pomieszczeniu z innym pacjentem.

## <a name="when-not-to-use-shared-device-mode"></a>Kiedy nie używać trybu urządzenia udostępnionego

Tryb urządzenia udostępnionego nie jest dobrym wyborem w takich sytuacjach:

- Gdy pliki użytkownika muszą być przechowywane lokalnie, a nie w chmurze
- Jeśli środowisko użytkownika musi być inne dla różnych użytkowników urządzenia
- Jeśli zestaw aplikacji wymaga znacznie poszczególnych użytkowników

## <a name="enroll-new-devices-in-shared-device-mode"></a>Rejestrowanie nowych urządzeń w trybie urządzenia udostępnionego

Niezależnie od tego, czy Rejestracja jest przez Ciebie czy partnera, możesz zdecydować się na użycie trybu urządzenia udostępnionego.

Jeśli rejestrujesz urządzenia samodzielnie, wykonaj czynności opisane w tece Rejestrowanie nowych urządzeń [samodzielnie, a](../get-started/register-devices-self.md) następnie dodaj je do grupy Nowoczesne urządzenia w miejscu pracy **— Tryb urządzenia udostępnionego** .

> [!WARNING]
> Nie próbuj konwertować żadnych istniejących Microsoft Managed Desktop na tryb urządzenia udostępnione, po prostu dodając je do tej grupy. Stosowane zasady mogą potencjalnie powodować trwałe OneDrive plików.

Jeśli masz partnera, który zarejestruje urządzenia, wykonaj czynności opisane w krokach rejestrowania urządzeń przez partnerów [, ale](../get-started/register-devices-partner.md) dołącz pole **-Shared** do tagu grupy, jak pokazano w poniższej tabeli:

| Profil urządzenia | Tag grupy rozwiązania Autopilot (tryb standardowy) | Tag grupy (tryb urządzenia udostępnionego) |
| ----- | ----- | ----- |
| Poufne dane | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Użytkownik zasilania | Microsoft365Managed_PowerUser | Nieobsługiwane |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

## <a name="consequences-of-shared-device-mode"></a>Konsekwencje trybu współużytkowania urządzenia

### <a name="device-storage"></a>Pamięć urządzenia

Użytkownicy urządzeń udostępnionych muszą mieć kopię zapasową swoich danych w chmurze, aby można było obserwować je na innych urządzeniach. Po zarejestrowaniu urządzeń w trybie urządzenia udostępnionego włącz funkcje plików na OneDrive oraz przekierowywania znanego [folderu](/onedrive/redirect-known-folders).[](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) Ta metoda minimalizuje wpływ każdego profilu użytkownika na magazyn urządzenia. Urządzenia w trybie urządzenia udostępnionego automatycznie usuwają profile użytkowników, jeśli wolne miejsce na dysku jest poniżej 25%. Ta aktywność jest zaplanowana na północ w godzinach lokalnych na urządzeniu, chyba że ilość miejsca do magazynowania zostanie bardzo ograniczona.

Microsoft Managed Desktop tych operacji jest używany program CSP [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows), dlatego należy się upewnić, że nie należy korzystać z tych zasad CSP samodzielnie.

> [!IMPORTANT]
> Szkolenie użytkowników, że po pobraniu dużego pliku powinni potwierdzić, że przed wylogowanium widzą oni zieloną ikonę czeku. Jeśli jego konto zostanie usunięte w ramach operacji oczyszczania i plik nie zostanie całkowicie przekazany OneDrive, plik zostanie trwale utracony.

### <a name="deletion-of-inactive-accounts"></a>Usuwanie nieaktywnych kont

Tryb urządzenia udostępnionego usuwa wszelkie konta, na które nie było zalogowanych dłużej niż 30 dni.

### <a name="guest-accounts"></a>Konta gości

Urządzenia w trybie urządzenia udostępnionego zezwalają tylko na konta przyłączone do domeny. Jeśli potrzebujesz kont gościa na urządzeniu, możesz złożyć wniosek o [](../working-with-managed-desktop/admin-support.md) zmianę i poprosić o ich włączoną obsługę.

### <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje usługi Microsoft 365 dla przedsiębiorstw

[Aplikacje Microsoft 365 dla przedsiębiorstw](/microsoft-365/managed-desktop/get-started/m365-apps) zwykle pozwala podanemu użytkownikowi zainstalować te aplikacje tylko na pięciu urządzeniach jednocześnie. W trybie współużytkowania urządzeń aplikacje nie są wliczane do limitu, więc mogą z nich korzystać podczas roamingu między urządzeniami. Wdrażanie i aktualizacje Aplikacje Microsoft 365 dla przedsiębiorstw działają normalnie.

### <a name="device-profiles"></a>Profile urządzeń

W trybie urządzenia udostępnionego możesz mieć tylko jeden [profil](profiles.md) urządzenia na danym urządzeniu. Ponadto profil urządzenia użytkownika w programie Power nie jest obecnie obsługiwany w trybie urządzenia udostępnionego.

### <a name="apps-and-policies-assigned-to-users"></a>Aplikacje i zasady przypisane do użytkowników

Na urządzeniach udostępnionych do grup urządzeń, a nie do grup użytkowników, należy przypisać wszystkie aplikacje lub *zasady, które* zarządzasz samodzielnie. Przypisywanie do grup urządzeń zapewnia, że każdy użytkownik ma bardziej spójne środowisko. Wyjątkiem jest [Portal firmy](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Ograniczenia trybu urządzenia udostępnionego

### <a name="windows-hello"></a>Windows Hello

Windows Hello korzysta z emulacji kart inteligentnych do bezpiecznego buforowania pinów [użytkowników,](/windows/security/identity-protection/hello-for-business/hello-faq) minimalizując liczbę uwierzytelnień użytkowników. Jednak Windows tylko 10 kart inteligentnych jednocześnie na danym urządzeniu. Gdy 11. użytkownik się pojawi po raz pierwszy, jedno z istniejących kont utraci kartę inteligentną. Będzie mógł się zalogować, ale numer PIN nie będzie buforowany.

### <a name="universal-print"></a>Drukowanie uniwersalne

Gdy narzędzie Drukowanie uniwersalne instaluje drukarkę dla jednego użytkownika na urządzeniu udostępnionym, która jest dostępna dla wszystkich użytkowników tego urządzenia. Użytkownicy korzystający z udostępnionych urządzeń nie mogą odizolować drukarek od innych użytkowników.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Ograniczenia trybu współużytkowania urządzenia w publicznej wersji Preview

### <a name="primary-user"></a>Użytkownik główny

Każde Microsoft Intune ma głównego użytkownika, który jest przypisywany po skonfigurowaniu urządzenia przez funkcję Autopilot. Jednak w przypadku współużytknia urządzeń usługa Intune wymaga usunięcia podstawowego użytkownika.

> [!IMPORTANT]
> Gdy tryb urządzenia udostępnionego jest w publicznej wersji zapoznawczej, pamiętaj o usunięciu użytkownika podstawowego, korzystając z następujących kroków: zaloguj się do centrum administracyjnego usługi Microsoft Endpoint Manager, > wybierz pozycję **UrządzeniaWszystkie** urządzenia, wybierz urządzenie, a następnie wybierz pozycję **PropertiesRemove**> **primary user** (Usuń użytkownika podstawowego) i usuń wymienionego tam użytkownika.

### <a name="deploying-apps-with-company-portal"></a>Wdrażanie aplikacji za pomocą aplikacji Portal firmy

Niektóre aplikacje prawdopodobnie nie muszą być obecne na wszystkich urządzeniach, więc możesz preferować, aby użytkownicy instalują te aplikacje tylko wtedy, gdy ich potrzebują, z usługi [Portal firmy](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Managed Desktop domyślnie wyłącza Portal firmy dla urządzeń w trybie urządzenia udostępnionego. Jeśli chcesz włączyć Portal firmy, możesz złożyć [żądanie zmiany](../working-with-managed-desktop/admin-support.md). Należy jednak pamiętać o pewnych ograniczeniach tej funkcji w tej publicznej wersji zapoznawczej:

- Aby udostępnić aplikację użytkownikom w usłudze Portal firmy, przypisz grupę użytkowników do tej aplikacji w usłudze Intune, [a](/mem/intune/apps/apps-deploy) następnie dodaj poszczególnych użytkowników do tej grupy użytkowników.
- Urządzenia nie mogą mieć [podstawowego użytkownika](#primary-user).
- Aby odinstalować aplikację, która została zainstalowana przez Portal firmy, musisz odinstalować tę aplikację od wszystkich użytkowników na tym urządzeniu.

> [!CAUTION]
> Portal firmy nie obsługuje aplikacji przypisanych do grup urządzeń, jeśli są dostępne.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Ponowne rozsuniecie Aplikacje Microsoft 365 dla przedsiębiorstw

Jeśli podczas publicznej wersji zapoznawczej należy ponownie Aplikacje Microsoft 365, użytkownicy muszą skontaktować się z lokalnym personelem pomocy technicznej, aby poprosić agenta o zainstalowanie pakietu Aplikacje Microsoft 365 dla przedsiębiorstw na tym urządzeniu.

### <a name="microsoft-teams"></a>Microsoft Teams

Gdy użytkownik Teams aplikacji po raz pierwszy, zostanie wyświetlony monit o zaktualizowanie aplikacji, zanim będzie mógł jej używać. Gdy zezwalają na aktualizację, Teams się w tle.
