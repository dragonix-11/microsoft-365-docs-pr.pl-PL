---
title: Prywatność dla programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Mechanizmy kontroli prywatności, jak skonfigurować ustawienia zasad, które mają wpływ na prywatność, oraz informacje o danych diagnostycznych zbieranych w programie Microsoft Defender for Endpoint na komputerze Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, privacy, diagnostic
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c49a6ff1440c7a3eee2e26eef90fb928e68458d1
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013903"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-macos"></a>Prywatność dla programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Firma Microsoft dokłada wszelkich starań, aby zapewnić Ci informacje i mechanizmy kontroli potrzebne do wyboru sposobu gromadzenia i używania danych podczas korzystania z programu Microsoft Defender for Endpoint w systemie macOS.

W tym temacie opisano mechanizmy kontroli prywatności dostępne w ramach produktu, sposób zarządzania tymi kontrolkami za pomocą ustawień zasad i więcej szczegółowych informacji na temat zbieranych zdarzeń danych.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-macos"></a>Omówienie kontroli prywatności w programie Microsoft Defender for Endpoint w systemie macOS

W tej sekcji opisano mechanizmy kontroli prywatności dla różnych typów danych zbieranych przez program Microsoft Defender for Endpoint w systemie macOS.

### <a name="diagnostic-data"></a>Dane diagnostyczne

Dane diagnostyczne służą do zabezpieczania i aktualnego działania programu Microsoft Defender for Endpoint, wykrywania, diagnozowania i rozwiązywania problemów oraz do ulepszeń produktu.

Niektóre dane diagnostyczne są wymagane, zaś inne dane diagnostyczne — opcjonalne. Dajemy Ci możliwość wyboru, czy wysyłać nam wymagane lub opcjonalne dane diagnostyczne przy użyciu mechanizmów ochrony prywatności, takich jak ustawienia zasad dla organizacji.

Istnieją dwa poziomy danych diagnostycznych dla oprogramowania klienckiego Programu Microsoft Defender dla punktu końcowego, które można wybrać:

- **Wymagane**: Minimalne dane niezbędne do zapewnienia, że program Microsoft Defender for Endpoint jest bezpieczny, aktualny i działa zgodnie z oczekiwaniami na urządzeniu, na które jest zainstalowany.

- **Opcjonalnie**: Dodatkowe dane, które ułatwiają firmie Microsoft w zakresie ulepszeń produktów i zapewniają rozszerzone informacje w celu wykrywania, diagnozowania i rozwiązywania problemów.

Domyślnie do firmy Microsoft są wysyłane tylko wymagane dane diagnostyczne.

### <a name="cloud-delivered-protection-data"></a>Dane ochrony dostarczone w chmurze

Ochrona dostarczana w chmurze służy do zapewnienia zwiększonej i szybszej ochrony za pomocą dostępu do najnowszych danych ochrony w chmurze.

Włączenie usługi ochrony w chmurze jest opcjonalne, jednak jest zdecydowanie zalecane, ponieważ zapewnia ważną ochronę przed złośliwym oprogramowaniem na punktach końcowych i w całej sieci.

### <a name="sample-data"></a>Dane przykładowe

Przykładowe dane są używane w celu zwiększenia możliwości ochrony produktu przez wysyłanie podejrzanych próbek od firmy Microsoft w celu ich analizy. Włączenie automatycznego przesyłania próbek jest opcjonalne.

Gdy ta funkcja jest włączona i zbierany przykład może zawierać informacje osobiste, użytkownik jest monitowany o zgodę.

## <a name="manage-privacy-controls-with-policy-settings"></a>Zarządzanie mechanizmami ochrony prywatności za pomocą ustawień zasad

Jeśli jesteś administratorem IT, możesz chcieć skonfigurować te kontrolki na poziomie przedsiębiorstwa.

Zasady zachowania poufności informacji dotyczące różnych typów danych opisane w poprzedniej sekcji opisano szczegółowo w sekcji Ustawianie preferencji programu [Microsoft Defender dla punktu końcowego w systemie macOS](mac-preferences.md).

Tak jak w przypadku wszystkich nowych ustawień zasad, należy je dokładnie przetestować w ograniczonym, kontrolowanym środowisku, aby przed zaimplementowaniem ustawień zasad w organizacji zapewnić odpowiedni efekt dla skonfigurowanych ustawień.

## <a name="diagnostic-data-events"></a>Zdarzenia danych diagnostycznych

W tej sekcji opisano, co jest uznawane za wymagane dane diagnostyczne, a także co jest uważane za opcjonalne dane diagnostyczne, oraz opisano zdarzenia i pola, które są zbierane.

### <a name="data-fields-that-are-common-for-all-events"></a>Pola danych wspólne dla wszystkich zdarzeń

Istnieje kilka informacji o wydarzeniach wspólnych dla wszystkich zdarzeń niezależnie od kategorii lub podtypu danych.

Poniższe pola są uznawane za typowe dla wszystkich zdarzeń:

|Pole|Opis|
|---|---|
|platforma|Klasyfikacja ogólnie platformy, na której działa aplikacja. Umożliwia firmie Microsoft zidentyfikowanie platform, na których może wystąpić problem, aby można było go poprawnie określić priorytetowo.|
|machine_guid|Unikatowy identyfikator skojarzony z urządzeniem. Umożliwia firmie Microsoft zidentyfikowanie, czy problemy wpływają na wybór zestawu instalacji oraz na ilu użytkowników to wpływa.|
|sense_guid|Unikatowy identyfikator skojarzony z urządzeniem. Umożliwia firmie Microsoft zidentyfikowanie, czy problemy wpływają na wybór zestawu instalacji oraz na ilu użytkowników to wpływa.|
|org_id|Unikatowy identyfikator skojarzony z przedsiębiorstwem, do którego należy urządzenie. Umożliwia firmie Microsoft zidentyfikowanie, czy problemy wpływają na wybór zestawu przedsiębiorstw i na ile przedsiębiorstw ma to wpływ.|
|nazwa hosta|Nazwa urządzenia lokalnego (bez sufiksu DNS). Umożliwia firmie Microsoft zidentyfikowanie, czy problemy wpływają na wybór zestawu instalacji oraz na ilu użytkowników to wpływa.|
|product_guid|Unikatowy identyfikator produktu. Umożliwia firmie Microsoft odróżnienie problemów w różnych odmianach produktu.|
|app_version|Wersja programu Microsoft Defender for Endpoint w aplikacji macOS. Umożliwia firmie Microsoft zidentyfikowanie wersji produktu, w których występuje problem, aby można było go poprawnie określić priorytetowo.|
|sig_version|Wersja bazy danych analizy zabezpieczeń. Umożliwia firmie Microsoft określenie, które wersje analizy zabezpieczeń pokazują problem, dzięki czemu można je poprawnie określić priorytetowo.|
|supported_compressions|Lista algorytmów kompresji obsługiwanych przez aplikację, na przykład `['gzip']`. Umożliwia firmie Microsoft zrozumienie, jakiego typu kompresji można używać podczas komunikowania się z aplikacją.|
|release_ring|Pierścień, z który jest skojarzone urządzenie (na przykład Niejawny program testów szybkich, Niejawny program testów wolnych, Wersja produkcyjna). Umożliwia firmie Microsoft zidentyfikowanie, w którym pierścieniu wydania może wystąpić problem, dzięki czemu można go poprawnie określić priorytet.|

### <a name="required-diagnostic-data"></a>Wymagane dane diagnostyczne

**Wymagane dane diagnostyczne** to minimalne dane potrzebne, aby zapewnić, że program Microsoft Defender for Endpoint jest bezpieczny, aktualny i działa zgodnie z oczekiwaniami na urządzeniu, na które jest zainstalowany.

Wymagane dane diagnostyczne pomagają w identyfikowaniu problemów z usługą Microsoft Defender dla punktu końcowego, które mogą być związane z konfiguracją urządzenia lub oprogramowania. Może na przykład pomóc w ustaleniu, czy funkcja programu Microsoft Defender dla punktu końcowego najczęściej ulega awarii w konkretnej wersji systemu operacyjnego, przy użyciu nowo wprowadzonych funkcji lub gdy pewne funkcje programu Microsoft Defender dla punktu końcowego są wyłączone. Wymagane dane diagnostyczne pomagają firmie Microsoft szybciej wykrywać, diagnozować i naprawiać te problemy w celu zmniejszenia wpływu na użytkowników lub organizacje.

#### <a name="software-setup-and-inventory-data-events"></a>Konfiguracja oprogramowania i zdarzenia danych zapasów

**Instalacja/odinstalowywanie programu Microsoft Defender for Endpoint**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|correlation_id|Unikatowy identyfikator skojarzony z instalacją.|
|Wersja|Wersja pakietu.|
|ważność|Ważność wiadomości (na przykład Informacje).|
|kod|Kod opisujący operację.|
|tekst|Dodatkowe informacje skojarzone z instalacją produktu.|

**Konfiguracja programu Microsoft Defender dla punktu końcowego**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|antivirus_engine.enable_real_time_protection|Czy ochrona w czasie rzeczywistym jest włączona na urządzeniu, czy nie.|
|antivirus_engine.strona_pasywna|Czy na urządzeniu włączono tryb pasywny, czy nie.|
|cloud_service.enabled|Czy ochrona w chmurze jest włączona na urządzeniu.|
|cloud_service.limit czasu|Przekieruj czas, w którym aplikacja komunikuje się z chmurą programu Microsoft Defender for Endpoint.|
|cloud_service.heartbeat_interval|Interwał między kolejnymi pulsami wysyłanymi przez produkt do chmury.|
|cloud_service.service_uri|URI używany do komunikowania się z chmurą.|
|cloud_service.diagnostic_level|Poziom diagnostyczny urządzenia (wymagany, opcjonalny).|
|cloud_service.automatic_sample_submission|Czy automatyczne przesyłanie próbek jest włączone, czy nie.|
|cloud_service.automatic_definition_update_enabled|Czy automatyczne aktualizowanie definicji jest włączone, czy nie.|
|edr.early_preview|Czy urządzenie ma być uruchamiane w EDR wersji Preview.|
|edr.group_id|Identyfikator grupy używany przez składnik wykrywania i odpowiedzi.|
|edr.tags|Tagi zdefiniowane przez użytkownika.|
|funkcje.\[ opcjonalna nazwa funkcji\]|Lista funkcji wersji Preview wraz z tym, czy są włączone, czy nie.|

#### <a name="product-and-service-usage-data-events"></a>Zdarzenia danych dotyczące użycia produktów i usług

**Raport aktualizacji analizy zabezpieczeń**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|from_version|Oryginalna wersja analizy zabezpieczeń.|
|to_version|Nowa wersja analizy zabezpieczeń.|
|stan|Stan aktualizacji oznaczający sukces lub niepowodzenie.|
|using_proxy|Czy aktualizacja została wykonana przez serwer proxy.|
|błąd|Kod błędu, jeśli aktualizacja nie powiodła się.|
|Przyczyna|Komunikat o błędzie, jeśli zaktualizowano dane.|

#### <a name="product-and-service-performance-data-events-for-required-diagnostic-data"></a>Zdarzenia danych o wydajności produktów i usług dla wymaganych danych diagnostycznych

**Nieoczekiwane zamknięcie aplikacji (awaria)**:

Zbiera informacje o systemie i stanie aplikacji, gdy aplikacja nieoczekiwanie kończy działanie.

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|v1_crash_count|Liczba awarii procesu aparatu V1 co godzinę na komputerze klienckim|
|v2_crash_count|Liczba awarii procesu aparatu V2 co godzinę na komputerze klienckim|
|EDR_crash_count|Liczba awarii EDR co godzinę na komputerze klienckim|

**Statystyka rozszerzenia kernelu**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|Wersja|Wersja programu Microsoft Defender for Endpoint w systemie macOS.|
|instance_id|Unikatowy identyfikator wygenerowany podczas uruchamiania rozszerzenia kernelu.|
|trace_level|Śledzenie poziomu rozszerzenia kernelu.|
|podsystem|Podsystem używany do ochrony w czasie rzeczywistym.|
|ipc.connects|Liczba żądań połączeń otrzymywanych przez rozszerzenie kernel.|
|ipc.rejects|Liczba żądań połączeń odrzuconych przez rozszerzenie kernel.|
|ipc.connected|Czy istnieje aktywne połączenie z rozszerzeniem kernel.|

#### <a name="support-data"></a>Dane pomocy technicznej

**Dzienniki diagnostyczne**:

Dzienniki diagnostyczne są zbierane tylko za zgodą użytkownika w ramach funkcji przesyłania opinii. W dziennikach pomocy technicznej są zbierane następujące pliki:

- Wszystkie pliki w *folderze /Biblioteki/Logs/Microsoft/mdatp/*
- Podzbiór plików *w folderze /Biblioteki/Application Support/Microsoft/Defender/* , które są tworzone i używane przez program Microsoft Defender for Endpoint w systemie macOS
- Podzbiór plików *w folderze /Library/Managed Preferences* , które są używane przez program Microsoft Defender for Endpoint w systemie macOS
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>Opcjonalne dane diagnostyczne

**Opcjonalne dane diagnostyczne to** dodatkowe dane, które pomagają firmie Microsoft ulepszać produkty i dostarczać rozszerzone informacje w celu wykrywania, diagnozowania i rozwiązywania problemów.

Jeśli zdecydujesz się wysłać nam opcjonalne dane diagnostyczne, wymagane dane diagnostyczne również zostaną dołączone.

Przykładami opcjonalnych danych diagnostycznych są dane zbierane przez firmę Microsoft dotyczące konfiguracji produktu (na przykład liczba wykluczeń określonych na urządzeniu) i wydajność produktu (zagregowane miary dotyczące wydajności składników produktu).

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>Konfigurowanie oprogramowania i zdarzenia danych dotyczących zapasów dla opcjonalnych danych diagnostycznych

**Konfiguracja programu Microsoft Defender dla punktu końcowego**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|connection_retry_timeout|Podczas komunikacji z chmurą ponownie wyekstrybuje połączenie.|
|file_hash_cache_maximum|Rozmiar pamięci podręcznej produktu.|
|crash_upload_daily_limit|Limit dziennych dzienników awarii.|
|antivirus_engine.exclusions[].is_directory|Czy wyłączenie skanowania jest katalogiem, czy nie.|
|antivirus_engine.exclusions[].path|Ścieżka wykluczona z skanowania.|
|antivirus_engine.exclusions[].extension|Rozszerzenie wykluczone z skanowania.|
|antivirus_engine.exclusions[].name|Nazwa pliku wykluczonego z skanowania.|
|antivirus_engine.scan_cache_maximum|Rozmiar pamięci podręcznej produktu.|
|antivirus_engine.maximum_scan_threads|Maksymalna liczba wątków używanych do skanowania.|
|antivirus_engine.threat_restoration_time|Przekierowywają czas, zanim plik przywrócony z kwarantanny będzie ponownie wykrywany.|
|antivirus_engine.threat_type_settings|Konfiguracja obsługi różnych typów zagrożeń przez produkt.|
|filesystem_scanner.full_scan_directory|Pełny katalog skanowania.|
|filesystem_scanner.quick_scan_directories|Lista katalogów używanych podczas szybkiego skanowania.|
|edr.latency_mode|Tryb opóźnienia używany przez składnik wykrywania i odpowiedzi.|
|edr.proxy_address|Adres serwera proxy używany przez składnik wykrywania i odpowiedzi.|

**Konfiguracja usługi Microsoft Auto-Update**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|how_to_check|Określa sposób sprawdzenia aktualizacji produktu (na przykład automatyczny lub ręczny).|
|channel_name|Zaktualizuj kanał skojarzony z urządzeniem.|
|manifest_server|Serwer używany do pobierania aktualizacji.|
|update_cache|Lokalizacja pamięci podręcznej używanej do przechowywania aktualizacji.|

### <a name="product-and-service-usage"></a>Użycie produktów i usług

#### <a name="diagnostic-log-upload-started-report"></a>Raport rozpoczętego przekazywania dziennika diagnostycznego

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|sha256|Identyfikator SHA256 dziennika pomocy technicznej.|
|rozmiar|Rozmiar dziennika pomocy technicznej.|
|original_path|Ścieżka do dziennika pomocy technicznej (zawsze w obszarze */Biblioteki/Application Support/Microsoft/Defender/wdavdiag/*).|
|format|Format dziennika pomocy technicznej.|
|metadane|Informacje o zawartości dziennika pomocy technicznej.|

#### <a name="diagnostic-log-upload-completed-report"></a>Ukończony raport przekazywania dziennika diagnostycznego

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|request_id|Identyfikator korelacji wniosku o przekazanie dziennika pomocy technicznej.|
|sha256|Identyfikator SHA256 dziennika pomocy technicznej.|
|blob_sas_uri|URI używany przez aplikację do przekazywania dziennika pomocy technicznej.|

#### <a name="product-and-service-performance-data-events-for-product-and-service-usage"></a>Zdarzenia danych o wydajności produktów i usług dotyczące użycia produktów i usług

**Nieoczekiwane zamknięcie aplikacji (awaria)**:

Niespodziewane zakończenie działania aplikacji oraz stan aplikacji w momencie takiego zdarzenia.

**Statystyka rozszerzenia kernelu**:

Zbierane są dane z następujących pól:

|Pole|Opis|
|---|---|
|pkt_ack_timeout|Poniższe właściwości to zagregowane wartości liczbowe reprezentujące liczbę zdarzeń, które miały miejsce od momentu uruchomienia rozszerzenia kernela.|
|pkt_ack_conn_timeout||
|ipc.ack_pkts||
|ipc.nack_pkts||
|ipc.send.ack_no_conn||
|ipc.send.nack_no_conn||
|ipc.send.ack_no_qsq||
|ipc.send.nack_no_qsq||
|ipc.ack.no_space||
|ipc.ack.timeout||
|ipc.ack.ackd_fast||
|ipc.ack.ackd||
|ipc.recv.bad_pkt_len||
|ipc.recv.bad_reply_len||
|ipc.recv.no_waiter||
|ipc.recv.copy_failed||
|ipc.kauth.vnode.mask||
|ipc.kauth.vnode.read||
|ipc.kauth.vnode.write||
|ipc.kauth.vnode.exec||
|ipc.kauth.vnode.del||
|ipc.kauth.vnode.read_attr||
|ipc.kauth.vnode.write_attr||
|ipc.kauth.vnode.read_ex_attr||
|ipc.kauth.vnode.write_ex_attr||
|ipc.kauth.vnode.read_sec||
|ipc.kauth.vnode.write_sec||
|ipc.kauth.vnode.take_own||
|ipc.kauth.vnode.link||
|ipc.kauth.vnode.create||
|ipc.kauth.vnode.move||
|ipc.kauth.vnode.mount||
|ipc.kauth.vnode.denied||
|ipc.kauth.vnode.ackd_before_deadline||
|ipc.kauth.vnode.missed_deadline||
|ipc.kauth.file_op.mask||
|ipc.kauth_file_op.open||
|ipc.kauth.file_op.close||
|ipc.kauth.file_op.close_modified||
|ipc.kauth.file_op.move||
|ipc.kauth.file_op.link||
|ipc.kauth.file_op.exec||
|ipc.kauth.file_op.remove||
|ipc.kauth.file_op.unmount||
|ipc.kauth.file_op.fork||
|ipc.kauth.file_op.create||

## <a name="resources"></a>Zasoby

- [Prywatność w firmie Microsoft](https://privacy.microsoft.com/)
