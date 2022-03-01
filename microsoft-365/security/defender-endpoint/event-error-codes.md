---
title: Przeglądanie zdarzeń i błędów przy użyciu Podglądu zdarzeń
description: Uzyskaj opisy i dalsze kroki rozwiązywania problemów (jeśli to konieczne) dla wszystkich zdarzeń zgłoszonych przez usługę Microsoft Defender for Endpoint.
keywords: rozwiązywanie problemów, przeglądarka zdarzeń, podsumowanie dziennika, kod błędu, niepowodzenie, usługa Microsoft Defender for Endpoint, nie można uruchomić, przerwano, nie można uruchomić
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 05/21/2018
ms.technology: mde
ms.openlocfilehash: a09f034ac35aa3380ea834eafc149eaad9a7cb3d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62996732"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Przeglądanie zdarzeń i błędów przy użyciu Podglądu zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- Podgląd zdarzeń
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Identyfikatory zdarzeń można przeglądać w [Podglądzie zdarzeń](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) na poszczególnych urządzeniach.

Jeśli na przykład urządzenia nie są wyświetlane na liście **Urządzenia, może** być konieczne poszukanie identyfikatorów zdarzeń na tych urządzeniach. Następnie możesz użyć tej tabeli do określenia dalszych kroków rozwiązywania problemów.

**Otwórz podgląd zdarzeń i znajdź dziennik zdarzeń usługi Microsoft Defender for Endpoint:**

1. Kliknij **przycisk Start** w menu Windows, wpisz **podgląd zdarzeń** i naciśnij klawisz **Enter**.

2. Na liście dzienników w obszarze **Podsumowanie** dziennika przewijaj w dół, aż zobaczysz **Windows-SENSE/Operational firmy Microsoft**. Kliknij dwukrotnie element, aby otworzyć dziennik.

   Dostęp do dziennika można również uzyskać, rozwijając pozycję **Dzienniki** \> aplikacji i usług, Windows **pozycję** **Operacyjne firmy** **Microsoft** \>  \>.

   > [!NOTE]
   > SENSE to wewnętrzna nazwa używana do obsługi czujnika zachowania, który służy do obsługi programu Microsoft Defender for Endpoint.

3. Zdarzenia zarejestrowane przez usługę pojawią się w dzienniku. W poniższej tabeli przedstawiono listę zdarzeń zarejestrowanych przez usługę.

   <br>

   ****

   |Identyfikator zdarzenia|Komunikat|Opis|Akcja|
   |---|---|---|---|
   |1|Usługa Microsoft Defender for Endpoint service started (wersja `variable`).|Występuje podczas uruchamiania systemu, zamykania i w trakcie dołączania.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |2|Program Microsoft Defender for Endpoint service shutdown.|Występuje w przypadku zamknięcia lub wyłączenia urządzenia.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |3|Nie można uruchomić usługi Microsoft Defender for Endpoint. Kod błędu: `variable`.|Usługa nie uruchomić się.|Przejrzyj inne wiadomości, aby ustalić możliwą przyczynę i kroki rozwiązywania problemów.|
   |4|Usługa Microsoft Defender for Endpoint skontaktowała się z serwerem pod adresem `variable`.|Zmienna = adres URL usługi Defender dla serwerów przetwarzania punktu końcowego. <p> Ten adres URL będzie taki, jak w przypadku aktywności w zaporze lub sieci.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |5|Program Microsoft Defender for Endpoint service nie może nawiązać połączenia z serwerem w `variable`.|Zmienna = adres URL usługi Defender dla serwerów przetwarzania punktu końcowego. <p> Usługa nie może skontaktować się z zewnętrznymi serwerami przetwarzania pod tym adresem URL.|Sprawdź połączenie z adresem URL. Zobacz [Konfigurowanie łączności z internetem i serwerem proxy](configure-proxy-internet.md).|
   |6|Usługa Microsoft Defender for Endpoint nie jest wnoowana i nie znaleziono parametrów dołączania.|Urządzenie nie zostało poprawnie podłączone i nie będzie podlegało portalowi.|Rozpoczęcie musi zostać uruchomione przed uruchomieniem usługi. <p> Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |7|Nie można odczytać parametrów dołączania do usługi Microsoft Defender for Endpoint. Niepowodzenie: `variable`.|Zmienna = szczegółowy opis błędu. Urządzenie nie zostało poprawnie podłączone i nie będzie podlegało portalowi.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |8|Usługa Microsoft Defender for Endpoint nie wyczyściła swojej konfiguracji. Kod błędu: `variable`.|**Podczas dołączania:** Podczas dołączania usługi nie można wyczyścić jej konfiguracji. Proces dołączania jest kontynuowany. <p> **Podczas wystartowania:** Podczas wynoszania nie można wyczyścić konfiguracji usługi. Proces wywłasania został ukończony, ale usługa nadal działa.|**Dołączanie:** Nie jest wymagane żadne działanie. <p> **Wyniesienie:** Uruchom ponownie system. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |9|Zmiana typu uruchomienia usługi Microsoft Defender for Endpoint nie powiodła się. Kod błędu: `variable`.|**Podczas dołączania:** Urządzenie nie zostało poprawnie podłączone i nie będzie podlegało portalowi. <p>**Podczas wystartowania:** Nie można zmienić typu uruchomienia usługi. Proces wywłasania jest kontynuowany. |Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |10|Usługa Microsoft Defender for Endpoint nie może zachowywać informacji o dołączaniu. Kod błędu: `variable`.|Urządzenie nie zostało poprawnie podłączone i nie będzie podlegało portalowi.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |11|Ukończono dołączanie lub ponowne dołączanie usługi Defender dla punktu końcowego.|Urządzenie zostało prawidłowo podłączone.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania. <p> Może mi potrwać kilka godzin, aby urządzenie pojawiło się w portalu.|
   |12|Program Microsoft Defender for Endpoint nie zastosuje konfiguracji domyślnej.|Usługa nie mogła zastosować konfiguracji domyślnej.|Ten błąd powinien zostać rozwiązany po krótkim czasie.|
   |13|Obliczony identyfikator urządzenia programu Microsoft Defender dla punktu końcowego: `variable`.|Normalny proces operacyjny.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |15|Program Microsoft Defender for Endpoint nie może uruchomić kanału poleceń z adresem URL: `variable`.|Zmienna = adres URL usługi Defender dla serwerów przetwarzania punktu końcowego. <p> Usługa nie może skontaktować się z zewnętrznymi serwerami przetwarzania pod tym adresem URL.|Sprawdź połączenie z adresem URL. Zobacz [Konfigurowanie łączności z internetem i serwerem proxy](configure-proxy-internet.md).|
   |17|Nie można zmienić lokalizacji usługi połączonych usług user experiences i telemetrii programu Microsoft Defender dla punktu końcowego. Kod błędu: `variable`.|Wystąpił błąd w usłudze Windows telemetrii.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)>upewnij się, że usługa danych diagnostycznych jest włączona. <p> Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |18|OOBE (Windows Welcome) został ukończony.|Usługa zostanie uruchomić dopiero po zakończeniu instalacji Windows aktualizacji.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |19|OOBE (Windows Welcome) nie zostało jeszcze ukończone.|Usługa zostanie uruchomić dopiero po zakończeniu instalacji Windows aktualizacji.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania. <p> Jeśli po ponownym uruchomieniu systemu ten błąd będzie nadal występował, upewnij się, Windows wszystkie aktualizacje są w pełni zainstalowane.|
   |20|Nie można zaczekać na ukończenie pracy Windows OOBE (Zapraszamy). Kod błędu: `variable`.|Błąd wewnętrzny.|Jeśli po ponownym uruchomieniu systemu ten błąd będzie nadal występował, upewnij się, Windows wszystkie aktualizacje są w pełni zainstalowane.|
   |25|Nie można zresetować stanu kondycji usługi Microsoft Defender for Endpoint w rejestrze. Kod błędu: `variable`.|Urządzenie nie zostało poprawnie podłączone. Zostanie ona zarejestrowana w portalu, ale usługa może nie być zarejestrowana w programie SCCM lub w rejestrze.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |26|Nie można ustawić stanu dołączania w rejestrze usługi Microsoft Defender for Endpoint. Kod błędu: `variable`.|Urządzenie nie zostało poprawnie podłączone. <p> Zostanie ona zarejestrowana w portalu, ale usługa może nie być zarejestrowana w programie SCCM lub w rejestrze.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |27|Usługa Microsoft Defender for Endpoint nie powiodła się włączyć tryb sense aware w Program antywirusowy Microsoft Defender. Proces dołączania nie powiódł się. Kod błędu: `variable`.|Jeśli na Program antywirusowy Microsoft Defender inny produkt ochrony przed złośliwym kodem w czasie rzeczywistym zostanie wpisanie specjalnego stanu pasywnego, a urządzenie podlega programowi Defender for Endpoint.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md). <p> Upewnij się, że ochrona przed złośliwym oprogramowaniem w czasie rzeczywistym działa prawidłowo.|
   |28|Rejestracja usług Microsoft Defender dla połączonych punktów końcowych i usług telemetrii nie powiodła się. Kod błędu: `variable`.|Wystąpił błąd w usłudze Windows telemetrii.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |29|Nie można odczytać parametrów wynoszowania. Typ błędu: %1, Kod błędu: %2, Opis: %3|To zdarzenie występuje, gdy system nie może odczytać parametrów wystartowania.|Upewnij się, że urządzenie ma dostęp do Internetu, a następnie ponownie uruchom cały proces wywęzienia. Upewnij się, że pakiet wywęszania nie wygasł.|
   |30|Program Microsoft Defender for Endpoint service nie może wyłączyć trybu sense aware w Program antywirusowy Microsoft Defender. Kod błędu: `variable`.|Jeśli na Program antywirusowy Microsoft Defender inny produkt ochrony przed złośliwym kodem w czasie rzeczywistym zostanie wpisanie specjalnego stanu pasywnego, a urządzenie podlega programowi Defender for Endpoint.|Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md). <p> Upewnij się, że ochrona przed złośliwym oprogramowaniem w czasie rzeczywistym działa prawidłowo.|
   |31|Nie można wyrejestrować usług Microsoft Defender for Endpoint Connected User Experiences i Telemetria. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii Windows podczas dołączania. Proces wywłasania jest kontynuowany.|[Sprawdź, czy nie występują błędy w usłudze Windows telemetrii](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|Usługa Microsoft Defender dla punktu końcowego nie żądała zatrzymania się po zakończeniu procesu wynoszania. Kod błędu: %1|Wystąpił błąd podczas wystartowania.|Uruchom ponownie urządzenie.|
   |33|Usługa Microsoft Defender for Endpoint nie może zachowywać identyfikatora GUID SENSE. Kod błędu: `variable`.|Do identyfikator unikatowy urządzenia, które podlega portalowi, jest używana identyfikator unikatowy. <p> Jeśli identyfikator nie zostanie utrwalony, to samo urządzenie może zostać wyświetlone dwukrotnie w portalu.|Sprawdź uprawnienia rejestru na urządzeniu, aby upewnić się, że usługa może zaktualizować rejestr.|
   |34|Nie można dodać samej usługi Microsoft Defender dla punktu końcowego jako zależności od usługi połączonych usług user experiences i telemetrii, co powoduje niepowodzenie procesu dołączania. Kod błędu: `variable`.|Wystąpił błąd w usłudze Windows telemetrii.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Sprawdź, czy ustawienia dotyczące dołączania i skrypty zostały poprawnie wdrożone. Spróbuj ponownie uruchomić pakiety konfiguracji. <p> Zobacz [Urządzenia Windows 10 urządzenia](configure-endpoints.md).|
   |35|Nie można usunąć samej usługi Microsoft Defender dla punktu końcowego jako zależności od usługi połączonych usług user experiences i telemetrii. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii Windows podczas wywłasniania. Proces wywłasania jest kontynuowany.|Sprawdź, czy nie ma błędów w Windows danych diagnostycznych.|
   |36|Rejestracja usługi Microsoft Defender for Endpoint Connected User Experiences i telemetrii zakończyła się pomyślnie. Kod ukończenia: `variable`.|Rejestracja usługi Defender dla punktu końcowego w usłudze połączonych usług i telemetrii została ukończona pomyślnie.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |37|Program Microsoft Defender dla punktu końcowego Moduł nie będzie już przekraczać przydziału. Moduł: %1, Przydział: {%2} {%3}, Procent użycia przydziału: %4.|Urządzenie niemal użyło przydzielonego przydziału w bieżącym 24-godzinnym oknie. To nie będzie już ograniczenie.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |38|Połączenie sieciowe jest identyfikowane jako niskie. Program Microsoft Defender for Endpoint będzie co %1 min kontaktował się z serwerem. Połączenie taryfowe: %2, dostępny Internet: %3, dostępna bezpłatna sieć: %4.|Urządzenie korzysta z sieci taryfowej/płatnej i będzie rzadziej kontaktuje się z serwerem.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |39|Połączenie sieciowe jest identyfikowane jako normalne. Program Microsoft Defender for Endpoint będzie co %1 min kontaktował się z serwerem. Połączenie taryfowe: %2, dostępny Internet: %3, dostępna bezpłatna sieć: %4.|Urządzenie nie korzysta z połączenia taryfowego/płatnego i będzie kontaktować się z serwerem w zwykły sposób.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |40|Stan baterii jest identyfikowany jako niski. Program Microsoft Defender for Endpoint będzie co %1 min kontaktował się z serwerem. Stan baterii: %2.|Urządzenie ma niski poziom naładowania baterii i będzie rzadziej kontaktować się z serwerem.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |41|Stan baterii jest identyfikowany jako normalny. Program Microsoft Defender for Endpoint będzie co %1 min kontaktował się z serwerem. Stan baterii: %2.|Urządzenie nie ma niskiego poziomu naładowania baterii i będzie kontaktować się z serwerem w zwykły sposób.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |42|Nie można wykonać akcji składnika programu Microsoft Defender for Endpoint. Składnik: %1, akcja: %2, typ wyjątku: %3, komunikat o wyjątku: %4|Błąd wewnętrzny. Nie można uruchomić usługi.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |43|Nie można wykonać akcji składnika programu Microsoft Defender for Endpoint. Składnik: %1, akcja: %2, typ wyjątku: %3, błąd wyjątku: %4, komunikat o wyjątku: %5|Błąd wewnętrzny. Nie można uruchomić usługi.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |44|Ukończono wyniesienie usługi Defender for Endpoint.|Usługa została wyłączona.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |45|Nie można zarejestrować i uruchomić sesji śledzenia zdarzeń [%1]. Kod błędu: %2|Wystąpił błąd podczas uruchamiania usługi podczas tworzenia sesji ETW. Powodowało to błąd uruchomienia usługi.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |46|Nie można zarejestrować i uruchomić sesji śledzenia zdarzeń [%1] z powodu braku zasobów. Kod błędu: %2. Jest to najprawdopodobniej spowodowane zbyt wieloma aktywnymi sesjami śledzenia zdarzeń. Usługa spróbuje ponownie za 1 minutę.|Wystąpił błąd podczas uruchamiania usługi podczas tworzenia sesji ETW z powodu braku zasobów. Usługa została uruchomiona i jest uruchomiona, ale nie będzie zgłaszać żadnego zdarzenia czujnika do momentu rozpoczęcia sesji ETW.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania. Usługa co minutę spróbuje uruchomić sesję.|
   |47|Pomyślnie zarejestrowano i uruchomiliśmy sesję śledzenia zdarzeń — odzyskaną po poprzednich nieudanych próbach.|To zdarzenie następuje po poprzednim zdarzeniu po pomyślnym rozpoczęciu sesji ETW.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |48|Nie można dodać dostawcy [%1] do sesji śledzenia zdarzeń [%2]. Kod błędu: %3. Oznacza to, że zdarzenia od tego dostawcy nie zostaną zgłoszone.|Nie można dodać dostawcy do sesji ETW. W wyniku tego zdarzenia dostawcy nie są zgłaszane.|Sprawdź kod błędu. Jeśli błąd nadal występuje, skontaktuj się z pomocą techniczną.|
   |49|Odebrano i zignorowano polecenie nieprawidłowej konfiguracji chmury. Wersja: %1, stan: %2, kod błędu: %3, komunikat: %4|Odebrano nieprawidłowy plik konfiguracji z usługi w chmurze, który został zignorowany.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |50|Pomyślnie zastosowano nową konfigurację chmury. Wersja: %1.|Pomyślnie zastosowano nową konfigurację z usługi w chmurze.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |51|Nie można zastosować nowej konfiguracji chmury, wersja: %1. Pomyślnie zastosowano ostatnią znaną dobrą konfigurację, wersję %2.|Odebrano plik złej konfiguracji z usługi w chmurze. Pomyślnie zastosowano ostatnią znaną dobrą konfigurację.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |52|Nie można zastosować nowej konfiguracji chmury, wersja: %1. Nie można też zastosować ostatniej znanej dobrej konfiguracji, w wersji %2. Pomyślnie zastosowano konfigurację domyślną.|Odebrano plik złej konfiguracji z usługi w chmurze. Nie można zastosować ostatniej znanej dobrej konfiguracji i zastosowano konfigurację domyślną.|Usługa podejmie próbę pobrania nowego pliku konfiguracji w ciągu 5 minut. Jeśli nie widzisz zdarzenia nr 50 , skontaktuj się z pomocą techniczną.|
   |53|Konfiguracja chmury załadowana z magazynu trwałego, wersja: %1.|Konfiguracja została załadowana z trwałego magazynu podczas uruchamiania usługi.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |55|Nie można utworzyć autologowania bezpiecznego etW. Kod błędu: %1|Nie można utworzyć bezpiecznego loglogii ETW.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |56|Nie można usunąć autologii Secure ETW. Kod błędu: %1|Nie można usunąć bezpiecznej sesji ETW przy wynoszceniu.|Skontaktuj się z pomocą techniczną.|
   |57|Przechwytywanie migawki komputera na potrzeby rozwiązywania problemów.|Trwa zbieranie pakietu badania, nazywanego także pakietem forensics.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |59|Polecenie Początkowe: %1|Uruchamianie polecenia odpowiedzi.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |60|Nie można uruchomić polecenia %1, błąd: %2.|Nie można wykonać polecenia odpowiedzi.|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |61|Parametry polecenia zbierania danych są nieprawidłowe: SasUri: %1, compressionLevel: %2.|Nie można odczytać ani  analizowania argumentów poleceń zbierania danych (nieprawidłowe argumenty).|Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |62|Nie można uruchomić usługi połączonych użytkowników i telemetrii. Kod błędu: %1|Uruchomienie usługi Połączone środowisko użytkownika i telemetria (diagtrack) nie powiodło się. Z tego komputera nie będą wysyłane telemetrii innych niż program Microsoft Defender for Endpoint.|Więcej wskazówek dotyczących rozwiązywania problemów można uzyskać w dzienniku zdarzeń: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Aktualizowanie typu uruchomienia usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3, kod wyjścia: %4|Zaktualizowano typ uruchomienia usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |64|Uruchamianie zatrzymało usługę zewnętrzną. Nazwa: %1, kod wyjścia: %2|Uruchamianie usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |65|Nie można załadować minifiltru składnika Zdarzenia zabezpieczeń firmy Microsoft. Kod błędu: %1|Nie można załadować MsSecFlt.sys minifiltru systemu plików.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |66|Aktualizacja zasad: Tryb opóźnienia — %1|Zasady częstotliwości połączeń C&C zostały zaktualizowane.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |68|Typ uruchomienia usługi jest nieoczekiwany. Nazwa usługi: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3|Nieoczekiwany typ uruchomienia usługi zewnętrznej.|Naprawianie typu uruchomienia usługi zewnętrznej.|
   |69|Usługa została zatrzymana. Nazwa usługi: %1|Usługa zewnętrzna jest zatrzymywana.|Uruchom usługę zewnętrzną.|
   |70|Aktualizacja zasad: Zezwalaj na przykładową kolekcję — %1|Przykładowe zasady kolekcji zostały zaktualizowane.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |71|Udało się uruchomić polecenie: %1|Polecenie zostało pomyślnie wykonane.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |72|Próbowano wysłać pierwszy pełny raport profilu komputera. Kod wyniku: %1|Tylko informacje.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |73|Sense starting for platform: %1|Tylko informacje.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |74|Tag urządzenia w rejestrze przekracza limit długości. Nazwa tagu: %2. Limit długości: %1.|Tag urządzenia przekracza limit długości.|Użyj krótszego tagu urządzenia.|
   |81|Nie można utworzyć programu Microsoft Defender dla autologii punktu końcowego ETW. Kod błędu: %1|Nie można utworzyć sesji ETW.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |82|Nie można usunąć programu Microsoft Defender dla autologii etw punktu końcowego. Kod błędu: %1|Nie można usunąć sesji ETW.|Skontaktuj się z pomocą techniczną.|
   |84|Ustaw Program antywirusowy Windows Defender tryb uruchamiania. Wymuszanie trybu pasywnego: %1, kod wyniku: %2.|Ustawianie trybu uruchamiania defender (aktywny lub pasywny).|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |85|Nie można uruchomić wykonywalnego programu Microsoft Defender for Endpoint. Kod błędu: %1|Oznaczone gwiazdką wykonywalny plik wykonywalny SenseIR nie powiódł się.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |86|Uruchamianie ponownie zatrzymało usługę zewnętrzną, która powinna być w górę. Nazwa: %1, kod wyjścia: %2|Ponownie uruchamiam usługę zewnętrzną.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |87|Nie można uruchomić usługi zewnętrznej. Nazwa: %1|Nie można uruchomić usługi zewnętrznej.|Skontaktuj się z pomocą techniczną.|
   |88|Ponownie aktualizowanie typu usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3, kod wyjścia: %4|Zaktualizowano typ uruchomienia usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |89|Nie można zaktualizować typu uruchomienia usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3|Nie można zaktualizować typu uruchomienia usługi zewnętrznej.|Skontaktuj się z pomocą techniczną.|
   |90|Nie można skonfigurować monitora środowiska uruchomieniowego systemu System Guard w celu nawiązania połączenia z usługą w chmurze w regionie geograficznym %1. Kod błędu: %2|Monitor środowiska uruchomieniowego System Guard nie wysyła danych o zakaście do usługi w chmurze.|Sprawdź uprawnienia ścieżki rejestru: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Jeśli nie zauważyć żadnych problemów, skontaktuj się z pomocą techniczną.|
   |91|Nie można usunąć informacji o regionie geograficznym monitora środowiska uruchomieniowego systemu Windows Guard. Kod błędu: %1|Monitor środowiska uruchomieniowego System Guard nie wysyła danych o zakaście do usługi w chmurze.|Sprawdź uprawnienia ścieżki rejestru: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Jeśli nie zauważyć żadnych problemów, skontaktuj się z pomocą techniczną.|
   |92|Zatrzymywanie wysyłania przydziału cyberprzedażeń czujnika z powodu przekroczenia przydziału danych. Wznowi wysyłanie po przekro czasie przydziału. Maska województwa: %1|Przekroczenie limitu ograniczania.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |93|Wznawianie wysyłania danych cyberprzestępczości z czujnika. Maska województwa: %1|Wznów cyberprzesłanie danych.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |94|Program Microsoft Defender for Endpoint wykonywalny został uruchomiony|Plik wykonywalny SenseCE został uruchomiony.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |95|Program Microsoft Defender for Endpoint wykonywalny został zakończony|Plik wykonywalny SenseCE został zakończony.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |96|Program Microsoft Defender for Endpoint Init zadzwonił. Kod wyniku: %2|Plik wykonywalny SenseCE nazywa się inicjowaniem mce.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |97|Występują problemy z łącznością z chmurą w scenariuszu zasad DLP|Występują problemy z łącznością sieciową, które wpływają na przepływ klasyfikacji DLP.|Sprawdź łączność sieciową.|
   |98|Przywrócono łączność z chmurą dla scenariusza DLP|Łączność z siecią została przywrócona, a przepływ klasyfikacji DLP może być kontynuowany.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |99|W sense napotkał następujący błąd podczas komunikowania się z serwerem: (%1). Wynik: (%2)|Wystąpił błąd komunikacji.|Aby uzyskać więcej szczegółowych informacji, zapoznaj się z poniższymi zdarzeniami w dzienniku zdarzeń.|
   |100|Nie można uruchomić pliku wykonywalnego programu Microsoft Defender for Endpoint. Kod błędu: %1|Nie można uruchomić pliku wykonywalnego SenseCE.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |102|Uruchomiony wykonywalny plik wykonywalny usługi Microsoft Defender for Endpoint Network Detection and Response|Plik wykonywalny sensendr został uruchomiony.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |103|Zakończono wykonywalny plik wykonywalny usługi Microsoft Defender for Endpoint Network Detection i Odpowiedzi|Plik wykonywalny sensendr został zakończony.|Normalne powiadomienie operacyjne; nie są wymagane żadne działania.|
   |

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Zobacz też
- [Urządzenia Windows 10 urządzeniach](configure-endpoints.md)
- [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md)
- [Rozwiązywanie problemów z usługą Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
- [Omówienie analizatora klientów](overview-client-analyzer.md)
- [Pobieranie i uruchamianie analizatora klienta](download-client-analyzer.md)
- [Opis raportu w formacie HTML analizatora](analyzer-report.md)