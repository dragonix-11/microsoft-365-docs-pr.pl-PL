---
title: Konfigurowanie Program antywirusowy Microsoft Defender z zasady grupy
description: Dowiedz się, jak za pomocą zasady grupy konfigurować i zarządzać Program antywirusowy Microsoft Defender punktami końcowymi w programie Microsoft Defender for Endpoint.
keywords: zasady grupy, grupa zasad grupy, konfiguracja, ustawienia
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/04/2022
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 3659f0f532b14babd256f3310c4e7da8dde67e3c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032090"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie zasady grupy zarządzanie plikami Program antywirusowy Microsoft Defender i zarządzanie nimi zasady grupy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Za [pomocą zasady grupy do](/windows/win32/srvnodes/group-policy) konfigurowania i zarządzania Program antywirusowy Microsoft Defender punktami końcowymi.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy

Poniższej procedury można na ogół używać do konfigurowania lub zmieniania Program antywirusowy Microsoft Defender zasad grupy:

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy obiekt zasady grupy(GPO), który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender**\>.

5. Rozwiń sekcję (podaną  w tym temacie jako Lokalizacja) zawierającą ustawienie, które chcesz skonfigurować, kliknij dwukrotnie to ustawienie, aby je otworzyć, i dokonaj zmian w konfiguracji.

6. [Wdeksuj zaktualizowanych zasad grupy tak jak zwykle](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>zasady grupy i zasoby

W poniższej tabeli wymieniono często zasady grupy ustawienia dostępne w programie Windows 10.

> [!TIP]
> Pobierz arkusz zasady grupy kalkulacyjny, który zawiera listę ustawień zasad dla komputera i konfiguracji użytkowników, które są zawarte w plikach szablonów administracyjnych dostarczanych z usługą Windows. Podczas edytowania plików w oknie zasady grupy kalkulacyjnych można konfigurować zasady grupy arkusza kalkulacyjnego. <br/><br/> Oto najnowsze wersje:
> - [zasady grupy Ustawienia arkusza kalkulacyjnego z aktualizacją z Windows 10 maja 2020 r. (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [zasady grupy Ustawienia arkusza kalkulacyjnego z Windows z 11 października 2021 r. (21h2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Lokalizacja|Ustawienie|Artykuł|
|---|---|---|
|Interfejs klienta|Włączanie trybu bezgłowego interfejsu użytkownika|[Uniemożliwianie użytkownikom oglądania interfejsu Program antywirusowy Microsoft Defender interakcji z nim](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|Interfejs klienta|Wyświetlanie dodatkowego tekstu klientom, gdy trzeba wykonać akcję|[Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Interfejs klienta|Pomiń wszystkie powiadomienia|[Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Interfejs klienta|Pomija powiadomienia o ponownym uruchomieniu|[Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia rozszerzeń|[Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia ścieżek|[Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia procesów|[Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wyłączanie automatycznego wykluczeń|[Konfigurowanie i weryfikowanie wykluczeń w Program antywirusowy Microsoft Defender skanowaniach](configure-exclusions-microsoft-defender-antivirus.md)|
|MAPY|Konfigurowanie funkcji blokowania na pierwszy rzut oka|[Włączanie bloku na pierwszy rzut oka](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|MAPY|Dołączanie do aplikacji Microsoft MAPS|[Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)|
|MAPY|Wysyłanie próbek plików w razie potrzeby dalszej analizy|[Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)|
|MAPY|Konfigurowanie zastępowania ustawień lokalnych na poziomie raportowania w aplikacji Microsoft MAPS|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Konfigurowanie rozszerzonego sprawdzania w chmurze|[Konfigurowanie limitu czasu blokowania chmury](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Wybieranie poziomu ochrony w chmurze|[Określanie poziomu ochrony w chmurze](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|System inspekcji sieci|Określanie dodatkowych zestawów definicji dla inspekcji ruchu sieciowego| Nie używane (przestarzałe) |
|System inspekcji sieci|Włączanie wycofania definicji| Nie używane (przestarzałe)|
|System inspekcji sieci|Włączanie rozpoznawania protokołów| Nie używane (przestarzałe)|
|Kwarantanna|Konfigurowanie zastępowania ustawień lokalnych w celu usunięcia elementów z folderu kwarantanny|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Kwarantanna|Konfigurowanie usuwania elementów z folderu kwarantanny|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych pod celu monitorowania aktywności plików i programów na komputerze|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu monitorowania przychodzącej i wychodzącej aktywności plików|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu skanowania wszystkich pobranych plików i załączników|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu włączeń monitorowania zachowania|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu włączoną ochronę w czasie rzeczywistym|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Definiowanie maksymalnego rozmiaru pobranych plików i załączników do skanowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Monitorowanie aktywności dotyczącej plików i programów na komputerze|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Skanowanie wszystkich pobranych plików i załączników|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Wyłączanie ochrony w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie monitorowania zachowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie skanowania w czasie rzeczywistym po włączeniu ochrony w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie powiadomień o nieprzetworzonej głośności zapisu|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie monitorowania przychodzącej i wychodzącej aktywności dotyczącej plików i programów|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Działania naprawcze|Konfigurowanie zastępowania ustawień lokalnych na czas dnia w celu uruchomienia zaplanowanego pełnego skanowania w celu ukończenia działań naprawczych|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Działania naprawcze|Określanie dnia tygodnia, w który ma zostać uruchomione zaplanowane pełne skanowanie w celu ukończenia działań naprawczych|[Konfigurowanie zaplanowanych Program antywirusowy Microsoft Defender skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Działania naprawcze|Określanie czasu zaplanowanego pełnego skanowania w celu ukończenia działań naprawczych|[Konfigurowanie zaplanowanych Program antywirusowy Microsoft Defender skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Raportowanie|Wyłączanie rozszerzonych powiadomień|[Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
|Katalog główny|Wyłączanie Program antywirusowy Microsoft Defender|Nie używane. Jeśli używasz lub planujesz używać produktu antywirusowego innego niż firmy Microsoft, zobacz zgodność [Program antywirusowy Microsoft Defender z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md).|
|Katalog główny|Definiowanie adresów w celu obejścia serwera proxy|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Katalog główny|Definiowanie autokonfigurowania serwera proxy (pac) dla łączenia się z siecią|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Katalog główny|Definiowanie serwera proxy na celu nawiązywania połączenia z siecią|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Katalog główny|Konfigurowanie zachowania lokalnej korespondencji seryjnej administratora dla list|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Katalog główny|Zezwalanie usłudze ochrony przed złośliwym oprogramowaniem na uruchamianie się z normalnym priorytetem|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Katalog główny|Zezwalaj na to, aby usługa ochrony przed złośliwym oprogramowaniem nadal działała zawsze|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Katalog główny|Wyłączanie rutynowych działań naprawczych|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Katalog główny|Randomizowanie zaplanowanych czasów zadań|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Zezwalaj użytkownikom na wstrzymywanie skanowania|[Uniemożliwianie użytkownikom oglądania interfejsu](prevent-end-user-interaction-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender interakcji z nim (nie jest obsługiwane w Windows 10)|
|Skanowanie|Sprawdzanie, czy są dostępne najnowsze definicje wirusów i oprogramowania szpiegującego przed uruchomieniem zaplanowanego skanowania|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Skanowanie|Definiowanie liczby dni, po których należy wymusić skanowanie pochwytowe|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie pełnego skanowania|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie szybkiego skanowania|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla maksymalnego procentu użycia procesora|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowanie|Konfigurowanie zastępowania ustawień lokalnych na dzień skanowania harmonogramu|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla zaplanowanego szybkiego skanowania|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla zaplanowanego czasu skanowania|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowanie|Konfigurowanie zastępowania lokalnego typu skanowania na czas zaplanowanego skanowania|[Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowanie|Tworzenie punktu przywracania systemu|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie usuwania elementów z folderu historii skanowania|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie heuristics|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie skanowania wiadomości e-mail|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Włączanie skanowania punktowego|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Uruchamianie pełnego skanowania na zamapowanych dyskach sieciowych|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Skanowanie plików archiwum|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Skanowanie plików sieciowych|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Skanowanie spakowanych plików wykonywalnych|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Skanowanie | Skanowanie skryptów | [Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Zobacz też [Defender/AllowScriptKanning](/windows/client-management/mdm/policy-csp-defender).|
|Skanowanie|Skanowanie dysków wymiennych|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie maksymalnej głębokości skanowania plików archiwum|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie maksymalnego procentu użycia procesora podczas skanowania|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie maksymalnego rozmiaru skanowanych plików archiwum|[Konfigurowanie opcji skanowania w programie Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie dnia tygodnia do uruchomienia zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie interwału do uruchamiania szybkich skanów w ciągu dnia|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie typu skanowania do użycia w zaplanowanym skanie|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie czasu dziennego szybkiego skanowania|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Określanie czasu dnia do uruchomienia zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowanie|Rozpoczynanie zaplanowanego skanowania tylko wtedy, gdy komputer jest wł., ale nie jest w użyciu|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń z usługi Microsoft Update|[Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń w przypadku pracy z baterii|[Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalanie na wyłączanie raportów opartych na definicjach w aplikacji Microsoft MAPS|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń w czasie rzeczywistym na podstawie raportów do mapy Microsoft MAPS|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Sprawdzanie, czy podczas uruchamiania nie są dostępne najnowsze definicje wirusów i oprogramowania szpiegującego|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie udziałów plików na celu pobierania aktualizacji analizy zabezpieczeń|[Zarządzanie Program antywirusowy Microsoft Defender i aktualizacjami analizy zabezpieczeń](manage-protection-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie liczby dni, po których jest wymagana aktualizacja analizy zabezpieczeń|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie liczby dni, po których definicje oprogramowania szpiegującego są uznawane za aktualne|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie liczby dni, po których definicje wirusów są uznawane za aktualne|[Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie kolejności źródeł pobierania aktualizacji analizy zabezpieczeń|[Zarządzanie Program antywirusowy Microsoft Defender i aktualizacjami analizy zabezpieczeń](manage-protection-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Inicjowanie aktualizacji analizy zabezpieczeń przy uruchamianiu|[Zarządzanie aktualizacjami wymuszonmi opartymi na wydarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określanie dnia tygodnia, w który mają być sprawdzane aktualizacje analizy zabezpieczeń|[Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określanie interwału sprawdzania aktualizacji analizy zabezpieczeń|[Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określanie czasu sprawdzania aktualizacji analizy zabezpieczeń|[Zarządzanie tym, kiedy mają być pobierane i stosowane aktualizacje ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Włączanie skanowania po aktualizacji analizy zabezpieczeń|[Konfigurowanie zaplanowanych skanów dla Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Zagrożenia|Określanie poziomów alertów o zagrożeniach, na których domyślne działania nie powinny być podejmowane podczas wykrywania|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|
|Zagrożenia|Określanie zagrożeń, w przypadku których nie należy stosować akcji domyślnej w przypadku wykrycia|[Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender skanowania](configure-remediation-microsoft-defender-antivirus.md)|


## <a name="see-also"></a>Zobacz też

- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
