---
title: Urządzenia udostępnione
description: Jak i kiedy używać trybu urządzenia udostępnionego
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: ad9cb5e69585f0c014050b51b719e539111cf9fa
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687190"
---
# <a name="shared-devices"></a>Urządzenia udostępnione

Microsoft Managed Desktop umożliwia rejestrowanie urządzeń w "trybie urządzenia udostępnionego", podobnie jak w przypadku trybu urządzenia udostępnionego oferowanego przez [Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

Urządzenia w tym trybie są zoptymalizowane pod kątem sytuacji, w których użytkownicy nie są powiązani z pojedynczym biurkiem i często zmieniają urządzenia. Na przykład pracownicy pierwszej linii, tacy jak kasjerzy bankowi lub personel pielęgniarski. W tym trybie można zastosować [dowolny z profilów](profiles.md) Microsoft Managed Desktop do urządzeń. Urządzenia zarejestrowane w tym trybie mają pewne istotne różnice:

- [Magazyn urządzeń](#device-storage) jest zoptymalizowany pod kątem użytkowników udostępnionych.
- [Nieaktywne konta](#deletion-of-inactive-accounts) są usuwane.
- [Konta gościa](#guest-accounts) nie są domyślnie obsługiwane.
- [Microsoft 365 Aplikacje](#microsoft-365-apps-for-enterprise) do licencjonowania przedsiębiorstwa są zoptymalizowane pod kątem urządzeń udostępnionych.

Ponieważ wybierasz tryb urządzenia udostępnionego w punkcie rejestracji w Microsoft Managed Desktop, jeśli chcesz później zmienić tryb, musisz go ponownie zarejestrować i zarejestrować.

## <a name="when-to-use-shared-device-mode"></a>Kiedy używać trybu urządzenia udostępnionego

Każda sytuacja, w której użytkownicy często zmieniają urządzenia.

Na przykład kasjerzy bankowi mogą znajdować się w jednej lokalizacji zarządzającej depozytami, ale przenieść się do zaplecza, aby pomóc klientom z kredytem hipotecznym. W każdej z tych lokalizacji urządzenie uruchamia różne aplikacje i jest zoptymalizowane pod kątem tych zadań, chociaż jest używane przez wiele osób.

Personel pielęgniarski zazwyczaj przemieszcza się między pokojami i biurami podczas interakcji z pacjentami. Mogą zalogować się do stacji roboczej w biurze, ale połączyć się ze swoim pulpitem zdalnym i robić notatki i powtarzać ten proces w innym pomieszczeniu z innym pacjentem.

## <a name="when-not-to-use-shared-device-mode"></a>Kiedy nie używać trybu urządzenia udostępnionego

Tryb urządzenia udostępnionego nie jest dobrym wyborem w takich sytuacjach:

- Gdy pliki użytkownika muszą być przechowywane lokalnie, a nie w chmurze
- Jeśli środowisko użytkownika musi być inne dla różnych użytkowników na urządzeniu
- Jeśli zestaw aplikacji, których potrzebuje każdy użytkownik, znacznie się różni

## <a name="register-new-devices-in-shared-device-mode"></a>Rejestrowanie nowych urządzeń w trybie urządzenia udostępnionego

Począwszy od 2203 r., niezależnie od tego, czy ty lub partner obsługujesz rejestrację urządzeń, możesz użyć profilu [trybu samodzielnego wdrażania rozwiązania Windows Autopilot](/mem/autopilot/self-deploying) w Microsoft Managed Desktop.

Jeśli samodzielnie rejestrujesz urządzenia, musisz zaimportować nowe urządzenia do bloku Windows Urządzenia rozwiązania Autopilot.

**Aby zaimportować nowe urządzenia do bloku urządzenia rozwiązania Windows Autopilot:**

1. Zbierz [skrót sprzętu](../get-started/manual-registration.md#obtain-the-hardware-hash) dla nowych urządzeń, do które chcesz przypisać profil trybu samodzielnego wdrażania rozwiązania Windows Autopilot.
2. Przejdź do [portalu Microsoft Endpoint Manager](https://endpoint.microsoft.com).
2. Wybierz pozycję **Urządzenia** z menu nawigacji po lewej stronie.
3. W sekcji **Według platformy** wybierz pozycję **Windows**. Następnie wybierz pozycję **Windows Rejestracja**.
4. W sekcji **Windows Autopilot Deployment Program** wybierz pozycję **Urządzenia**.
5. [Zaimportuj](../get-started/manual-registration.md#register-devices-by-using-the-admin-portal) plik .CSV zawierający wszystkie skróty sprzętowe zebrane w kroku 1.
6. Po przekazaniu Windows urządzeń z rozwiązaniem Autopilot należy edytować atrybut tagu grupy zaimportowanych urządzeń, aby Microsoft Managed Desktop mogli je zarejestrować przy użyciu profilu trybu samodzielnego wdrażania rozwiązania Windows Autopilot. Poniżej przedstawiono atrybuty tagów grupy. Musisz dołączyć **element -Shared** do tagu grupy, jak pokazano w poniższej tabeli:

| Profil urządzenia | Tag grupy rozwiązania Autopilot (tryb standardowy) | Tag grupy (tryb urządzenia udostępnionego) |
| ----- | ----- | ----- |
| Dane poufne | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Użytkownik usługi Power | Microsoft365Managed_PowerUser | Nieobsługiwane |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

> [!WARNING]
> Nie próbuj edytować atrybutu karty grupy, dołączając **polecenie -Shared** do urządzeń wcześniej zaimportowanych do rozwiązania Windows Autopilot. Urządzenia już zaimportowane do rozwiązania Windows Autopilot przy użyciu jednego z tagów grupy Microsoft Managed Desktop, począwszy od *Microsoft365Managed_*, ale bez początkowego dołączania **elementu -Shared**, są już częścią innej grupy Azure Active Directory. Ta grupa Azure Active Directory nie ma przypisanego profilu trybu samodzielnego wdrażania rozwiązania Windows Autopilot. Jeśli konieczne jest ponowne przeznaczenie istniejącego urządzenia jako urządzenia udostępnionego, należy usunąć i ponownie zarejestrować urządzenie w rozwiązaniu Windows Autopilot.

Jeśli masz urządzenia zarejestrowane przez partnera, wykonaj kroki opisane w temacie [Rejestracja partnera](../get-started/partner-registration.md), ale dołącz **ciąg -Shared** do tagu grupy, jak pokazano w powyższej tabeli.

## <a name="consequences-of-shared-device-mode"></a>Konsekwencje trybu urządzenia udostępnionego

### <a name="device-storage"></a>Magazyn urządzeń

Użytkownicy urządzeń udostępnionych muszą mieć kopie zapasowe danych w chmurze, aby mogli śledzić je na innych urządzeniach. Po zarejestrowaniu urządzeń w trybie urządzenia udostępnionego należy włączyć funkcje przekierowania [plików na żądanie](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) i [znanych folderów](/onedrive/redirect-known-folders) OneDrive. Takie podejście minimalizuje wpływ każdego profilu użytkownika na magazyn urządzeń. Urządzenia w trybie urządzenia udostępnionego automatycznie usuwają profile użytkowników, jeśli wolne miejsce na dysku spadnie poniżej 25%. To działanie jest zaplanowane na północ w czasie lokalnym urządzenia, chyba że magazyn stanie się krytycznie ograniczony.

Microsoft Managed Desktop używa dostawcy CSP [sharedPC](/mem/intune/configuration/shared-user-device-settings-windows) do wykonywania tych operacji, więc upewnij się, że nie używasz tych dostawców CSP samodzielnie.

> [!IMPORTANT]
> Wytrenuj użytkowników, że po pobraniu dużego pliku przed wylogowaniem powinni potwierdzić, że widzą zieloną ikonę wyboru w pliku. Jeśli ich konto zostanie usunięte w ramach operacji oczyszczania, a plik nie zostanie całkowicie przekazany w OneDrive, plik zostanie trwale utracony.

### <a name="deletion-of-inactive-accounts"></a>Usuwanie nieaktywnych kont

Tryb urządzenia udostępnionego usuwa wszystkie konta, które nie zostały zalogowane przez więcej niż 30 dni.

### <a name="guest-accounts"></a>Konta gościa

Urządzenia w trybie urządzenia udostępnionego zezwalają tylko na konta przyłączone do domeny. Jeśli potrzebujesz kont gościa na urządzeniu, możesz złożyć [żądanie zmiany](../working-with-managed-desktop/admin-support.md) , aby zażądać ich włączenia.

### <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje usługi Microsoft 365 dla przedsiębiorstw

[Aplikacje Microsoft 365 dla przedsiębiorstw](/microsoft-365/managed-desktop/get-started/m365-apps) zwykle umożliwia danemu użytkownikowi instalowanie tych aplikacji tylko na pięciu urządzeniach w tym samym czasie. W trybie urządzenia udostępnionego aplikacje nie są wliczane do limitu, więc mogą z nich korzystać podczas roamingu między urządzeniami. Wdrażanie i aktualizacje Aplikacje Microsoft 365 dla przedsiębiorstw działają jak zwykle.

### <a name="device-profiles"></a>Profile urządzeń

W trybie urządzenia udostępnionego można mieć tylko jeden [profil urządzenia](profiles.md) na danym urządzeniu. Ponadto profil urządzenia użytkownika usługi Power nie jest obecnie obsługiwany w trybie urządzenia udostępnionego.

### <a name="apps-and-policies-assigned-to-users"></a>Aplikacje i zasady przypisane do użytkowników

Na urządzeniach udostępnionych należy przypisać wszystkie aplikacje lub zasady, którymi zarządzasz samodzielnie, do *grup urządzeń*, a nie do grup użytkowników. Przypisanie do grup urządzeń gwarantuje, że każdy użytkownik ma bardziej spójne środowisko. Wyjątek jest [Portal firmy](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Ograniczenia trybu urządzenia udostępnionego

### <a name="windows-hello"></a>Windows Hello

Windows Hello używa emulacji kart inteligentnych do [bezpiecznego buforowania numerów PIN użytkowników](/windows/security/identity-protection/hello-for-business/hello-faq), minimalizując liczbę uwierzytelnień użytkowników. Jednak Windows zezwala tylko na 10 kart inteligentnych jednocześnie na danym urządzeniu. Gdy 11 użytkownik zaloguje się po raz pierwszy, jedno z istniejących kont utraci kartę inteligentną. Będą mogli się zalogować, ale ich numer PIN nie zostanie zapisany w pamięci podręcznej.

### <a name="universal-print"></a>Drukowanie uniwersalne

Gdy drukowanie uniwersalne instaluje drukarkę dla jednego użytkownika na urządzeniu udostępnionym, drukarka staje się dostępna dla wszystkich użytkowników tego urządzenia. Nie ma możliwości izolowania drukarek między użytkownikami na urządzeniach udostępnionych.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Ograniczenia trybu urządzenia udostępnionego w publicznej wersji zapoznawczej

### <a name="primary-user"></a>Użytkownik podstawowy

Każde urządzenie Microsoft Intune ma użytkownika podstawowego, który jest przypisywany, gdy urządzenie jest skonfigurowane przez rozwiązanie Autopilot. Jednak gdy urządzenia są współużytkowane, Intune wymaga usunięcia użytkownika podstawowego.

> [!IMPORTANT]
> Jeśli tryb urządzenia udostępnionego jest w publicznej wersji zapoznawczej, usuń użytkownika podstawowego, wykonując następujące kroki: zaloguj się do centrum administracyjnego Microsoft Endpoint Manager, wybierz pozycję **UrządzeniaWszystkie**> urządzenia, wybierz urządzenie, a następnie wybierz pozycję **WłaściwościUsuń**> użytkownika podstawowego i usuń wymienionego tam użytkownika.

### <a name="deploying-apps-with-company-portal"></a>Wdrażanie aplikacji za pomocą Portal firmy

Niektóre aplikacje prawdopodobnie nie muszą być obecne na wszystkich urządzeniach, więc możesz chcieć, aby użytkownicy instalowali te aplikacje tylko wtedy, gdy ich potrzebują z [Portal firmy](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Managed Desktop domyślnie wyłącza Portal firmy dla urządzeń w trybie urządzenia udostępnionego. Jeśli chcesz włączyć Portal firmy, możesz złożyć [żądanie zmiany](../working-with-managed-desktop/admin-support.md). Należy jednak pamiętać o pewnych ograniczeniach tej funkcji w tej publicznej wersji zapoznawczej:

- Aby udostępnić aplikację użytkownikom w Portal firmy, [przypisz grupę użytkowników](/mem/intune/apps/apps-deploy) do tej aplikacji w Intune, a następnie dodaj każdego użytkownika do tej grupy użytkowników.
- Urządzenia nie mogą mieć [użytkownika podstawowego](#primary-user).
- Aby odinstalować aplikację zainstalowaną przez użytkownika za pośrednictwem Portal firmy, należy odinstalować aplikację od wszystkich użytkowników na tym urządzeniu.

> [!CAUTION]
> Portal firmy nie obsługuje aplikacji przypisanych do grup urządzeń jako dostępne.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Ponowne wdrażanie Aplikacje Microsoft 365 dla Enterprise

W publicznej wersji zapoznawczej, jeśli Aplikacje Microsoft 365 muszą zostać ponownie wdrożone, użytkownicy muszą skontaktować się z lokalnym personelem pomocy technicznej, aby zażądać podniesienia poziomu agenta i ponownej instalacji Aplikacje Microsoft 365 dla przedsiębiorstw na tym urządzeniu.

### <a name="microsoft-teams"></a>Microsoft Teams

Gdy użytkownik uruchomi Teams po raz pierwszy, zostanie wyświetlony monit o zaktualizowanie aplikacji, zanim będzie mógł z niej korzystać. Po zezwoleniu na aktualizację Teams będzie aktualizowana w tle.
