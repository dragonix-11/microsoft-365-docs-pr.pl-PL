---
title: Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy
description: Dowiedz się, jak za pomocą zasady grupy konfigurować Program antywirusowy Microsoft Defender i zarządzać nimi w punktach końcowych w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: zasady grupy, obiekt zasad grupy, konfiguracja, ustawienia
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
ms.openlocfilehash: 53b24f0566b9b9d43ad725a832bb1e0fa8013923
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416381"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi przy użyciu ustawień zasady grupy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Za pomocą [zasady grupy](/windows/win32/srvnodes/group-policy) można konfigurować Program antywirusowy Microsoft Defender i zarządzać nimi w punktach końcowych.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy

Ogólnie rzecz biorąc, można użyć następującej procedury, aby skonfigurować lub zmienić ustawienia zasad grupy Program antywirusowy Microsoft Defender:

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender**.

5. Rozwiń sekcję (określaną jako **Lokalizacja** w tabeli w tym temacie), która zawiera ustawienie, które chcesz skonfigurować, kliknij dwukrotnie ustawienie, aby je otworzyć, i wprowadź zmiany konfiguracji.

6. [Wdróż zaktualizowany obiekt zasad grupy tak, jak zwykle](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>zasady grupy ustawienia i zasoby

W poniższej tabeli wymieniono często używane ustawienia zasady grupy dostępne w Windows 10.

> [!TIP]
> Pobierz arkusz kalkulacyjny dokumentacji zasady grupy, który zawiera listę ustawień zasad dla konfiguracji komputerów i użytkowników, które są zawarte w plikach szablonów administracyjnych dostarczonych dla Windows. Podczas edytowania zasady grupy Obiektów można skonfigurować odwołanie do arkusza kalkulacyjnego. <br/><br/> Oto najnowsze wersje:
> - [zasady grupy Ustawienia arkusz kalkulacyjny referencyjny dla aktualizacji Windows 10 maja 2020 r. (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [zasady grupy Ustawienia arkusz kalkulacyjny referencyjny dla Windows 11 aktualizacji z października 2021 r. (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Lokalizacja|Ustawienie|Artykułu|
|---|---|---|
|Interfejs klienta|Włączanie trybu bezgłowego interfejsu użytkownika|[Uniemożliwianie użytkownikom korzystania z interfejsu użytkownika Program antywirusowy Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|Interfejs klienta|Wyświetl dodatkowy tekst klientom, gdy będą musieli wykonać akcję|[Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Interfejs klienta|Pomiń wszystkie powiadomienia|[Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Interfejs klienta|Pomija powiadomienia o ponownym uruchomieniu|[Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia rozszerzeń|[Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia ścieżki|[Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wykluczenia procesów|[Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Wykluczenia|Wyłączanie automatycznych wykluczeń|[Konfigurowanie i weryfikowanie wykluczeń w skanowaniach Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|MAPY|Konfigurowanie funkcji "Blokuj od pierwszego wejrzenia"|[Włącz blok od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|MAPY|Dołącz do usługi Microsoft MAPS|[Włączanie ochrony dostarczanej w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)|
|MAPY|Wysyłanie przykładów plików, gdy wymagana jest dalsza analiza|[Włączanie ochrony dostarczanej w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)|
|MAPY|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby raportowania do usługi Microsoft MAPS|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Konfigurowanie rozszerzonego sprawdzania chmury|[Skonfiguruj limit czasu blokady chmury](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Wybieranie poziomu ochrony w chmurze|[Określanie poziomu ochrony dostarczanej w chmurze](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|System inspekcji sieci|Określanie dodatkowych zestawów definicji na potrzeby inspekcji ruchu sieci| Nieużywane (przestarzałe) |
|System inspekcji sieci|Włączanie wycofywania definicji| Nieużywane (przestarzałe)|
|System inspekcji sieci|Włączanie rozpoznawania protokołów| Nieużywane (przestarzałe)|
|Kwarantanna|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby usuwania elementów z folderu Kwarantanna|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Kwarantanna|Konfigurowanie usuwania elementów z folderu Kwarantanna|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie zastąpienia ustawień lokalnych na potrzeby monitorowania działania plików i programów na komputerze|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby monitorowania aktywności plików przychodzących i wychodzących|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby skanowania wszystkich pobranych plików i załączników|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby włączania monitorowania zachowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych w celu włączenia ochrony w czasie rzeczywistym|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Definiowanie maksymalnego rozmiaru pobranych plików i załączników do skanowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Monitorowanie aktywności plików i programów na komputerze|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Skanuj wszystkie pobrane pliki i załączniki|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Wyłączanie ochrony w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie monitorowania zachowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie skanowania procesów za każdym razem, gdy włączono ochronę w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Włączanie nieprzetworzonych powiadomień zapisu woluminu|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Ochrona w czasie rzeczywistym|Konfigurowanie monitorowania dla działań przychodzących i wychodzących plików i programów|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Korygowania|Konfigurowanie przesłonięcia ustawień lokalnych na czas dnia w celu uruchomienia zaplanowanego pełnego skanowania w celu ukończenia korygowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Korygowania|Określ dzień tygodnia, w którym ma zostać uruchomione zaplanowane pełne skanowanie w celu ukończenia korygowania|[Konfigurowanie zaplanowanych skanów Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Korygowania|Określ godzinę uruchomienia zaplanowanego pełnego skanowania w celu ukończenia korygowania|[Konfigurowanie zaplanowanych skanów Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Raportowanie|Wyłączanie powiadomień rozszerzonych|[Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
|Głównego|Wyłącz Program antywirusowy Microsoft Defender|Nieużywane. Jeśli używasz lub planujesz używać produktu antywirusowego innego niż Microsoft, zobacz [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md).|
|Głównego|Definiowanie adresów w celu obejścia serwera proxy|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Głównego|Definiowanie automatycznej konfiguracji serwera proxy (pac) na potrzeby nawiązywania połączenia z siecią|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Głównego|Definiowanie serwera proxy na potrzeby nawiązywania połączenia z siecią|[Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Głównego|Konfigurowanie zachowania scalania administratora lokalnego dla list|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Głównego|Zezwalaj na uruchamianie usługi ochrony przed złośliwym kodem z normalnym priorytetem|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Głównego|Zezwalaj na zawsze działającą usługę ochrony przed złośliwym kodem|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Głównego|Wyłączanie rutynowego korygowania|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Głównego|Losowe zaplanowanych godzin zadań|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Zezwalaj użytkownikom na wstrzymywanie skanowania|[Uniemożliwianie użytkownikom korzystania z interfejsu użytkownika Program antywirusowy Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md) (nieobsługiwane w Windows 10)|
|Skanowania|Przed uruchomieniem zaplanowanego skanowania sprawdź najnowsze definicje wirusów i programów szpiegujących|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Skanowania|Definiowanie liczby dni, po których jest wymuszane skanowanie nadrabianie zaległości|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowania|Włącz nadrabianie zaległości w pełnym skanowaniu|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowania|Włączanie szybkiego skanowania nadrabiania zaległości|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla maksymalnego procentu wykorzystania procesora CPU|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby zaplanowanego dnia skanowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla zaplanowanego czasu szybkiego skanowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla zaplanowanego czasu skanowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowania|Konfigurowanie przesłonięcia ustawienia lokalnego dla typu skanowania do użycia w przypadku zaplanowanego skanowania|[Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Skanowania|Tworzenie punktu przywracania systemu|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Skanowania|Włączanie usuwania elementów z folderu historii skanowania|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Skanowania|Włączanie heurystyki|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Skanowania|Włączanie skanowania poczty e-mail|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Włączanie skanowania punktów ponownej analizy|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Uruchamianie pełnego skanowania na zamapowanych dyskach sieciowych|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Skanowanie plików archiwum|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Skanowanie plików sieciowych|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Skanowanie spakowanych plików wykonywalnych|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Skanowania | Skanuj skrypty | [Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Zobacz również [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Skanowania|Skanowanie dysków wymiennych|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Określ maksymalną głębokość skanowania plików archiwum|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Określanie maksymalnego procentu wykorzystania procesora CPU podczas skanowania|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Określanie maksymalnego rozmiaru plików archiwum do skanowania|[Konfigurowanie opcji skanowania w Program antywirusowy Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Skanowania|Określ dzień tygodnia, w którym ma zostać uruchomione zaplanowane skanowanie|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Określanie interwału do uruchamiania szybkich skanów dziennie|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Określanie typu skanowania do użycia w przypadku zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Określanie czasu codziennego szybkiego skanowania|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Określanie godziny uruchomienia zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Skanowania|Uruchamianie zaplanowanego skanowania tylko wtedy, gdy komputer jest włączony, ale nie jest używany|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń z usługi Microsoft Update|[Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń podczas pracy z zasilaniem bateryjnym|[Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na powiadomienia, aby wyłączyć raporty oparte na definicjach w usłudze Microsoft MAPS|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zezwalaj na aktualizacje analizy zabezpieczeń w czasie rzeczywistym na podstawie raportów do usługi Microsoft MAPS|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Sprawdzanie najnowszych definicji wirusów i programów szpiegujących podczas uruchamiania|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie udziałów plików do pobierania aktualizacji analizy zabezpieczeń|[Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender ochrony i analizy zabezpieczeń](manage-protection-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zdefiniuj liczbę dni, po których wymagana jest aktualizacja analizy zabezpieczeń|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zdefiniuj liczbę dni, po których definicje programów szpiegujących zostaną uznane za nieaktualne|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Zdefiniuj liczbę dni, po których definicje wirusów zostaną uznane za nieaktualne|[Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Definiowanie kolejności źródeł pobierania aktualizacji analizy zabezpieczeń|[Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender ochrony i analizy zabezpieczeń](manage-protection-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Inicjowanie aktualizacji analizy zabezpieczeń podczas uruchamiania|[Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określ dzień tygodnia, w którym będą sprawdzane aktualizacje analizy zabezpieczeń|[Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określ interwał sprawdzania dostępności aktualizacji analizy zabezpieczeń|[Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Określanie czasu sprawdzania dostępności aktualizacji analizy zabezpieczeń|[Zarządzanie pobieraniem i stosowaniem aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Aktualizacje analizy zabezpieczeń|Włączanie skanowania po aktualizacji analizy zabezpieczeń|[Konfigurowanie zaplanowanych skanów pod kątem Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Zagrożeń|Określanie poziomów alertów o zagrożeniach, przy których nie należy wykonywać akcji domyślnej po wykryciu|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Zagrożeń|Określanie zagrożeń, dla których nie należy podejmować akcji domyślnej po wykryciu|[Konfigurowanie korygowania na potrzeby skanowania Program antywirusowy Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
