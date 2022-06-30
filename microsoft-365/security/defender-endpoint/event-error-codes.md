---
title: Przeglądanie zdarzeń i błędów przy użyciu Podgląd zdarzeń
description: Uzyskaj opisy i dalsze kroki rozwiązywania problemów (jeśli to konieczne) dla wszystkich zdarzeń zgłoszonych przez usługę Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: rozwiązywanie problemów, podgląd zdarzeń, podsumowanie dziennika, kod błędu, niepowodzenie, usługa Ochrona punktu końcowego w usłudze Microsoft Defender, nie można uruchomić, nie można uruchomić, nie można uruchomić
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
ms.openlocfilehash: a598361851593fc84a06e9c4a1ef94e3ed6e1fba
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554296"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Przeglądanie zdarzeń i błędów przy użyciu Podgląd zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- Podgląd zdarzeń
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Identyfikatory zdarzeń można przejrzeć w [Podgląd zdarzeń](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) na poszczególnych urządzeniach.

Jeśli na przykład urządzenia nie są wyświetlane na **liście Urządzenia**, może być konieczne wyszukanie identyfikatorów zdarzeń na urządzeniach. Następnie możesz użyć tej tabeli do określenia dalszych kroków rozwiązywania problemów.

**Otwórz Podgląd zdarzeń i znajdź dziennik zdarzeń usługi Ochrona punktu końcowego w usłudze Microsoft Defender:**

1. Kliknij **przycisk Start** w menu systemu Windows, wpisz **Podgląd zdarzeń**, a następnie naciśnij **klawisz Enter**.

2. Na liście dzienników w obszarze **Podsumowanie dziennika** przewiń do pozycji **Microsoft-Windows-SENSE/Operational**. Kliknij dwukrotnie element, aby otworzyć dziennik.

   Dostęp do dziennika można również uzyskać, rozwijając **pozycję Dzienniki** \> aplikacji i usług **Microsoft** \> **Windows** \> **SENSE** i klikając pozycję **Operacje**.

   > [!NOTE]
   > SENSE to nazwa wewnętrzna używana do odwoływania się do czujnika behawioralnego, który obsługuje Ochrona punktu końcowego w usłudze Microsoft Defender.

3. Zdarzenia zarejestrowane przez usługę będą wyświetlane w dzienniku. Zapoznaj się z poniższą tabelą, aby uzyskać listę zdarzeń zarejestrowanych przez usługę.

   <br>

   ****

   |Identyfikator zdarzenia|Komunikat|Opis|Akcja|
   |---|---|---|---|
   |1|Ochrona punktu końcowego w usłudze Microsoft Defender uruchomiono usługę (wersja `variable`).|Występuje podczas uruchamiania, zamykania i dołączania systemu.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |2|Ochrona punktu końcowego w usłudze Microsoft Defender zamknięcie usługi.|Występuje, gdy urządzenie jest wyłączone lub odłączone.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |3|Ochrona punktu końcowego w usłudze Microsoft Defender nie można uruchomić usługi. Kod błędu: `variable`.|Usługa nie została uruchomiona.|Przejrzyj inne komunikaty, aby określić możliwą przyczynę i kroki rozwiązywania problemów.|
   |4|Ochrona punktu końcowego w usłudze Microsoft Defender usługa skontaktowała się z serwerem pod adresem `variable`.|Zmienna = adres URL serwerów przetwarzania punktu końcowego w usłudze Defender. <p> Ten adres URL będzie zgodny z adresem widocznym w działaniu zapory lub sieci.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |5|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może nawiązać połączenia z serwerem pod adresem `variable`.|Zmienna = adres URL serwerów przetwarzania punktu końcowego w usłudze Defender. <p> Usługa nie może skontaktować się z zewnętrznymi serwerami przetwarzania pod tym adresem URL.|Sprawdź połączenie z adresem URL. Zobacz [Konfigurowanie serwera proxy i łączności z Internetem](configure-proxy-internet.md).|
   |6|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie jest dołączona i nie znaleziono żadnych parametrów dołączania.|Urządzenie nie zostało prawidłowo dołączone i nie będzie raportować do portalu.|Przed uruchomieniem usługi należy uruchomić dołączanie. <p> Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |7|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może odczytać parametrów dołączania. Błąd: `variable`.|Zmienna = szczegółowy opis błędu. Urządzenie nie zostało prawidłowo dołączone i nie będzie raportować do portalu.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |8|usługa Ochrona punktu końcowego w usłudze Microsoft Defender nie może wyczyścić konfiguracji. Kod błędu: `variable`.|**Podczas dołączania:** Usługa nie mogła wyczyścić konfiguracji podczas dołączania. Proces dołączania jest kontynuowany. <p> **Podczas odłączania:** Usługa nie mogła wyczyścić konfiguracji podczas odłączania. Proces odłączania zakończył się, ale usługa nadal działa.|**Dołączania:** Nie jest wymagana żadna akcja. <p> **Odłączanie:** Uruchom ponownie system. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |9|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może zmienić typu początkowego. Kod błędu: `variable`.|**Podczas dołączania:** Urządzenie nie zostało prawidłowo dołączone i nie będzie raportować do portalu. <p>**Podczas odłączania:** Nie można zmienić typu uruchomienia usługi. Proces odłączania jest kontynuowany. |Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |10|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może utrwalić informacji o dołączaniu. Kod błędu: `variable`.|Urządzenie nie zostało prawidłowo dołączone i nie będzie raportować do portalu.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |11|Ukończono dołączanie lub ponowne dołączanie usługi Defender for Endpoint.|Urządzenie zostało prawidłowo dołączone.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja. <p> Wyświetlenie urządzenia w portalu może potrwać kilka godzin.|
   |12|Ochrona punktu końcowego w usłudze Microsoft Defender nie można zastosować konfiguracji domyślnej.|Usługa nie może zastosować konfiguracji domyślnej.|Ten błąd powinien zostać rozwiązany po krótkim czasie.|
   |13|Ochrona punktu końcowego w usłudze Microsoft Defender obliczony identyfikator urządzenia: `variable`.|Normalny proces operacyjny.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |15|Ochrona punktu końcowego w usłudze Microsoft Defender nie można uruchomić kanału poleceń z adresem URL: `variable`.|Zmienna = adres URL serwerów przetwarzania punktu końcowego w usłudze Defender. <p> Usługa nie może skontaktować się z zewnętrznymi serwerami przetwarzania pod tym adresem URL.|Sprawdź połączenie z adresem URL. Zobacz [Konfigurowanie serwera proxy i łączności z Internetem](configure-proxy-internet.md).|
   |17|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może zmienić lokalizacji usługi Środowisko i telemetria połączonego użytkownika. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii systemu Windows.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)" >Upewnij się, że usługa danych diagnostycznych jest włączona. <p> Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |18|Środowisko OOBE (Windows Welcome) zostało ukończone.|Usługa zostanie uruchomiona dopiero po zakończeniu instalacji aktualizacji systemu Windows.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |19|Funkcja OOBE (Windows Welcome) nie została jeszcze ukończona.|Usługa zostanie uruchomiona dopiero po zakończeniu instalacji aktualizacji systemu Windows.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja. <p> Jeśli ten błąd będzie się powtarzać po ponownym uruchomieniu systemu, upewnij się, że wszystkie aktualizacje systemu Windows są w pełni zainstalowane.|
   |20|Nie można czekać na ukończenie funkcji OOBE (Windows Welcome). Kod błędu: `variable`.|Błąd wewnętrzny.|Jeśli ten błąd będzie się powtarzać po ponownym uruchomieniu systemu, upewnij się, że wszystkie aktualizacje systemu Windows są w pełni zainstalowane.|
   |25|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może zresetować stanu kondycji w rejestrze. Kod błędu: `variable`.|Urządzenie nie zostało prawidłowo dołączone. Będzie raportować do portalu, jednak usługa może nie być wyświetlana jako zarejestrowana w programie SCCM lub rejestrze.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |26|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może ustawić stanu dołączania w rejestrze. Kod błędu: `variable`.|Urządzenie nie zostało prawidłowo dołączone. <p> Będzie raportować do portalu, jednak usługa może nie być wyświetlana jako zarejestrowana w programie SCCM lub rejestrze.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |27|usługa Ochrona punktu końcowego w usłudze Microsoft Defender nie może włączyć trybu rozpoznawania sense w programie antywirusowym Microsoft Defender. Proces dołączania nie powiódł się. Kod błędu: `variable`.|Zwykle program antywirusowy Microsoft Defender będzie miał specjalny stan pasywny, jeśli inny produkt chroniący przed złośliwym kodem w czasie rzeczywistym działa prawidłowo na urządzeniu, a urządzenie jest raportowane do usługi Defender for Endpoint.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md). <p> Upewnij się, że ochrona przed złośliwym kodem w czasie rzeczywistym działa prawidłowo.|
   |28|Ochrona punktu końcowego w usłudze Microsoft Defender rejestracja usługi Connected User Experiences and Telemetry nie powiodła się. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii systemu Windows.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |29|Nie można odczytać parametrów odłączania. Typ błędu: %1, kod błędu: %2, opis: %3|To zdarzenie występuje, gdy system nie może odczytać parametrów odłączania.|Upewnij się, że urządzenie ma dostęp do Internetu, a następnie uruchom ponownie cały proces odłączania. Upewnij się, że pakiet odłączania nie wygasł.|
   |30|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może wyłączyć trybu rozpoznawania sense w programie antywirusowym Microsoft Defender. Kod błędu: `variable`.|Zwykle program antywirusowy Microsoft Defender będzie miał specjalny stan pasywny, jeśli inny produkt chroniący przed złośliwym kodem w czasie rzeczywistym działa prawidłowo na urządzeniu, a urządzenie jest raportowane do usługi Defender for Endpoint.|Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md). <p> Upewnij się, że ochrona przed złośliwym kodem w czasie rzeczywistym działa prawidłowo.|
   |31|Ochrona punktu końcowego w usłudze Microsoft Defender nie można wyrejestrowyć połączonych środowisk użytkownika i usługi telemetrii. Kod błędu: `variable`.|Wystąpił błąd z usługą telemetrii systemu Windows podczas dołączania. Proces odłączania jest kontynuowany.|[Sprawdź błędy w usłudze telemetrii systemu Windows](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|usługa Ochrona punktu końcowego w usłudze Microsoft Defender nie może zażądać zatrzymania się po zakończeniu procesu dołączania. Kod błędu: %1|Wystąpił błąd podczas odłączania.|Uruchom ponownie urządzenie.|
   |33|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie może utrwalić identyfikatora GUID SENSE. Kod błędu: `variable`.|Unikatowy identyfikator jest używany do reprezentowania każdego urządzenia, które raportuje do portalu. <p> Jeśli identyfikator nie utrwali się, to samo urządzenie może pojawić się dwa razy w portalu.|Sprawdź uprawnienia rejestru na urządzeniu, aby upewnić się, że usługa może zaktualizować rejestr.|
   |34|Ochrona punktu końcowego w usłudze Microsoft Defender usługa nie mogła dodać się jako zależność od usługi Środowiska i telemetria połączonego użytkownika, co spowodowało niepowodzenie procesu dołączania. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii systemu Windows.|[Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Sprawdź, czy ustawienia dołączania i skrypty zostały prawidłowo wdrożone. Spróbuj ponownie wdrożyć pakiety konfiguracji. <p> Zobacz [Dołączanie urządzeń Windows 10](configure-endpoints.md).|
   |35|usługa Ochrona punktu końcowego w usłudze Microsoft Defender nie mogła usunąć siebie jako zależności od usługi Środowiska i telemetria połączonego użytkownika. Kod błędu: `variable`.|Wystąpił błąd w usłudze telemetrii systemu Windows podczas odłączania. Proces odłączania jest kontynuowany.|Sprawdź, czy występują błędy w usłudze danych diagnostycznych systemu Windows.|
   |36|Ochrona punktu końcowego w usłudze Microsoft Defender rejestracja usługi Connected User Experiences and Telemetry zakończyła się pomyślnie. Kod ukończenia: `variable`.|Pomyślnie ukończono rejestrowanie usługi Defender for Endpoint w usłudze Connected User Experiences and Telemetry.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |37|Ochrona punktu końcowego w usłudze Microsoft Defender moduł przekroczy swój limit przydziału. Moduł: %1, przydział: {%2} {%3}, procent wykorzystania przydziału: %4.|Urządzenie niemal wykorzystało przydzielony przydział bieżącego okna 24-godzinnego. To ma być ograniczane.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |38|Połączenie sieciowe jest identyfikowane jako niskie. Ochrona punktu końcowego w usłudze Microsoft Defender skontaktuje się z serwerem co %1 minutę. Połączenie taryfowe: %2, dostępny internet: %3, dostępna bezpłatna sieć: %4.|Urządzenie korzysta z sieci taryfowej/płatnej i rzadziej kontaktuje się z serwerem.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |39|Połączenie sieciowe jest identyfikowane jako normalne. Ochrona punktu końcowego w usłudze Microsoft Defender skontaktuje się z serwerem co %1 minutę. Połączenie taryfowe: %2, dostępny internet: %3, dostępna bezpłatna sieć: %4.|Urządzenie nie korzysta z połączenia taryfowego/płatnego i skontaktuje się z serwerem jak zwykle.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |40|Stan baterii jest identyfikowany jako niski. Ochrona punktu końcowego w usłudze Microsoft Defender skontaktuje się z serwerem co %1 minutę. Stan baterii: %2.|Urządzenie ma niski poziom baterii i rzadziej kontaktuje się z serwerem.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |41|Stan baterii jest identyfikowany jako normalny. Ochrona punktu końcowego w usłudze Microsoft Defender skontaktuje się z serwerem co %1 minutę. Stan baterii: %2.|Urządzenie nie ma niskiego poziomu baterii i skontaktuje się z serwerem jak zwykle.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |42|Ochrona punktu końcowego w usłudze Microsoft Defender składnik nie może wykonać akcji. Składnik: %1, akcja: %2, typ wyjątku: %3, komunikat o wyjątku: %4|Błąd wewnętrzny. Nie można uruchomić usługi.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |43|Ochrona punktu końcowego w usłudze Microsoft Defender składnik nie może wykonać akcji. Składnik: %1, akcja: %2, typ wyjątku: %3, błąd wyjątku: %4, komunikat o wyjątku: %5|Błąd wewnętrzny. Nie można uruchomić usługi.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |44|Zakończono odłączanie usługi Defender for Endpoint.|Usługa została odłączona.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |45|Nie można zarejestrować i uruchomić sesji śledzenia zdarzeń [%1]. Kod błędu: %2|Wystąpił błąd podczas uruchamiania usługi podczas tworzenia sesji ETW. Spowodowało to niepowodzenie uruchamiania usługi.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |46|Nie można zarejestrować i uruchomić sesji śledzenia zdarzeń [%1] z powodu braku zasobów. Kod błędu: %2. Jest to najprawdopodobniej spowodowane zbyt dużą liczbą aktywnych sesji śledzenia zdarzeń. Usługa ponowi próbę w ciągu 1 minuty.|Wystąpił błąd podczas uruchamiania usługi podczas tworzenia sesji ETW z powodu braku zasobów. Usługa została uruchomiona i jest uruchomiona, ale nie będzie zgłaszać żadnego zdarzenia czujnika do czasu rozpoczęcia sesji ETW.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja. Usługa będzie próbować uruchamiać sesję co minutę.|
   |47|Pomyślnie zarejestrowano i uruchomiono sesję śledzenia zdarzeń — odzyskaną po poprzednich nieudanych próbach.|To zdarzenie jest następstwem poprzedniego zdarzenia po pomyślnym rozpoczęciu sesji ETW.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |48|Nie można dodać dostawcy [%1] do sesji śledzenia zdarzeń [%2]. Kod błędu: %3. Oznacza to, że zdarzenia od tego dostawcy nie będą zgłaszane.|Nie można dodać dostawcy do sesji ETW. W związku z tym zdarzenia dostawcy nie są zgłaszane.|Sprawdź kod błędu. Jeśli błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |49|Odebrano i zignorowano nieprawidłowe polecenie konfiguracji chmury. Wersja: %1, stan: %2, kod błędu: %3, komunikat: %4|Odebrano nieprawidłowy plik konfiguracji z usługi w chmurze, który został zignorowany.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |50|Nowa konfiguracja chmury została pomyślnie zastosowana. Wersja: %1.|Pomyślnie zastosowano nową konfigurację z usługi w chmurze.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |51|Nie można zastosować nowej konfiguracji chmury, wersja: %1. Pomyślnie zastosowaliśmy ostatnią znaną dobrą konfigurację w wersji %2.|Odebrano nieprawidłowy plik konfiguracji z usługi w chmurze. Ostatnia znana dobra konfiguracja została pomyślnie zastosowana.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |52|Nie można zastosować nowej konfiguracji chmury, wersja: %1. Nie można również zastosować ostatniej znanej dobrej konfiguracji w wersji %2. Pomyślnie zastosowaliśmy konfigurację domyślną.|Odebrano nieprawidłowy plik konfiguracji z usługi w chmurze. Nie można zastosować ostatniej znanej dobrej konfiguracji i zastosowano konfigurację domyślną.|Usługa podejmie próbę pobrania nowego pliku konfiguracji w ciągu 5 minut. Jeśli nie widzisz zdarzenia nr 50 — skontaktuj się z pomocą techniczną.|
   |53|Konfiguracja chmury załadowana z magazynu trwałego, wersja: %1.|Konfiguracja została załadowana z magazynu trwałego podczas uruchamiania usługi.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |54| Stan globalny (według wzorca) został zmieniony. Stan: %1, wzorzec: %2 | Jeśli stan = 0: reguła raportowania danych cybernetycznych osiągnęła zdefiniowany limit przydziału ograniczenia i nie wyśle więcej danych, dopóki limit przydziału nie wygaśnie. Jeśli stan = 1: limit przydziału ograniczenia wygasł, a reguła wznowi wysyłanie danych. | Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja. |
   |55|Nie można utworzyć automatycznego rejestrowania secure ETW. Kod błędu: %1|Nie można utworzyć bezpiecznego rejestratora ETW.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |56|Nie można usunąć automatycznego rejestrowania secure ETW. Kod błędu: %1|Nie można usunąć bezpiecznej sesji ETW podczas odłączania.|Skontaktuj się z pomocą techniczną.|
   |57|Przechwytywanie migawki maszyny na potrzeby rozwiązywania problemów.|Zbierany jest pakiet dochodzeniowy, znany również jako pakiet kryminalistyczny.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |59|Uruchamianie polecenia: %1|Uruchamianie wykonywania polecenia odpowiedzi.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |60|Nie można uruchomić polecenia %1, błąd: %2.|Nie można wykonać polecenia odpowiedzi.|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |61|Parametry polecenia zbierania danych są nieprawidłowe: SasUri: %1, compressionLevel: %2.|Nie można odczytać lub przeanalizować argumentów polecenia zbierania danych (nieprawidłowe argumenty).|Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |62|Nie można uruchomić usługi Środowiska i telemetria połączonego użytkownika. Kod błędu: %1|Nie można uruchomić usługi środowiska i telemetrii połączonego użytkownika (diagtrack). Dane telemetryczne inne niż Ochrona punktu końcowego w usłudze Microsoft Defender nie będą wysyłane z tej maszyny.|Poszukaj więcej wskazówek dotyczących rozwiązywania problemów w dzienniku zdarzeń: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Aktualizowanie typu początkowego usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3, kod zakończenia: %4|Zaktualizowano typ rozpoczęcia usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |64|Uruchamianie zatrzymanej usługi zewnętrznej. Nazwa: %1, kod zakończenia: %2|Uruchamianie usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |65|Nie można załadować sterownika minifiltru składnika zdarzeń zabezpieczeń firmy Microsoft. Kod błędu: %1|Nie można załadować MsSecFlt.sys minifiltru systemu plików.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |66|Aktualizacja zasad: tryb opóźnienia — %1|Zaktualizowano zasady częstotliwości połączeń C&C.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |68|Typ rozpoczęcia usługi jest nieoczekiwany. Nazwa usługi: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3|Nieoczekiwany typ uruchomienia usługi zewnętrznej.|Napraw typ rozpoczęcia usługi zewnętrznej.|
   |69|Usługa jest zatrzymana. Nazwa usługi: %1|Usługa zewnętrzna jest zatrzymana.|Uruchom usługę zewnętrzną.|
   |70|Aktualizacja zasad: Zezwalaj na zbieranie przykładów — %1|Zasady zbierania przykładów zostały zaktualizowane.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |71|Pomyślnie uruchomiono polecenie: %1|Polecenie zostało wykonane pomyślnie.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |72|Podjęto próbę wysłania pierwszego pełnego raportu profilu komputera. Kod wyniku: %1|Tylko informacje.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |73|Sense starting for platform: %1|Tylko informacje.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |74|Tag urządzenia w rejestrze przekracza limit długości. Nazwa tagu: %2. Limit długości: %1.|Tag urządzenia przekracza limit długości.|Użyj krótszego tagu urządzenia.|
   |81|Nie można utworzyć automatycznego rejestrowania Ochrona punktu końcowego w usłudze Microsoft Defender ETW. Kod błędu: %1|Nie można utworzyć sesji ETW.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |82|Nie można usunąć Ochrona punktu końcowego w usłudze Microsoft Defender autologgera ETW. Kod błędu: %1|Nie można usunąć sesji ETW.|Skontaktuj się z pomocą techniczną.|
   |84|Ustaw Program antywirusowy Windows Defender tryb uruchamiania. Wymuś tryb pasywny: %1, kod wyniku: %2.|Ustaw tryb działania usługi Defender (aktywny lub pasywny).|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |85|Nie można wyzwolić Ochrona punktu końcowego w usłudze Microsoft Defender pliku wykonywalnego. Kod błędu: %1|Wystąpił błąd wykonywalny SenseIR.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |86|Uruchomienie ponownie zatrzymał usługę zewnętrzną, która powinna być w górę. Nazwa: %1, kod zakończenia: %2|Ponowne uruchomienie usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |87|Nie można uruchomić usługi zewnętrznej. Nazwa: %1|Nie można uruchomić usługi zewnętrznej.|Skontaktuj się z pomocą techniczną.|
   |88|Ponowne aktualizowanie typu początkowego usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3, kod zakończenia: %4|Zaktualizowano typ rozpoczęcia usługi zewnętrznej.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |89|Nie można zaktualizować typu początkowego usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3|Nie można zaktualizować typu początkowego usługi zewnętrznej.|Skontaktuj się z pomocą techniczną.|
   |90|Nie można skonfigurować monitora środowiska uruchomieniowego funkcji System Guard w celu nawiązania połączenia z usługą w chmurze w regionie geograficznym %1. Kod błędu: %2|System Guard Runtime Monitor nie wysyła danych zaświadczania do usługi w chmurze.|Sprawdź uprawnienia w ścieżce rejestrowania: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Jeśli nie wykryto żadnych problemów, skontaktuj się z pomocą techniczną.|
   |91|Nie można usunąć informacji o regionie geograficznym monitora środowiska uruchomieniowego funkcji System Guard. Kod błędu: %1|System Guard Runtime Monitor nie wysyła danych zaświadczania do usługi w chmurze.|Sprawdź uprawnienia w ścieżce rejestrowania: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Jeśli nie wykryto żadnych problemów, skontaktuj się z pomocą techniczną.|
   |92|Zatrzymywanie wysyłania limitu przydziału danych cybernetycznych czujnika z powodu przekroczenia limitu przydziału danych. Wznowi wysyłanie po upływie okresu przydziału. Maska stanu: %1|Przekrocz limit ograniczania przepustowości.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |93|Wznawianie wysyłania danych cybernetycznych czujników. Maska stanu: %1|Wznawianie przesyłania danych cybernetycznych.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |94|Ochrona punktu końcowego w usłudze Microsoft Defender uruchomiono plik wykonywalny|Uruchomiono plik wykonywalny SenseCE.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |95|Ochrona punktu końcowego w usłudze Microsoft Defender plik wykonywalny został zakończony|Plik wykonywalny SenseCE został zakończony.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |96|Ochrona punktu końcowego w usłudze Microsoft Defender init zadzwonił. Kod wyniku: %2|Plik wykonywalny SenseCE nazwał inicjowanie MCE.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |97|Występują problemy z łącznością z chmurą w scenariuszu DLP|Występują problemy z łącznością sieciową, które mają wpływ na przepływ klasyfikacji DLP.|Sprawdź łączność sieciową.|
   |98|Przywrócono łączność z chmurą w scenariuszu DLP|Łączność z siecią została przywrócona i przepływ klasyfikacji DLP może być kontynuowany.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |99|Podczas komunikacji z serwerem sense napotkało następujący błąd: (%1). Wynik: (%2)|Wystąpił błąd komunikacji.|Aby uzyskać więcej informacji, sprawdź następujące zdarzenia w dzienniku zdarzeń.|
   |100|Ochrona punktu końcowego w usłudze Microsoft Defender nie można uruchomić pliku wykonywalnego. Kod błędu: %1|Nie można uruchomić pliku wykonywalnego SenseCE.|Uruchom ponownie urządzenie. Jeśli ten błąd będzie się powtarzać, skontaktuj się z pomocą techniczną.|
   |102|Ochrona punktu końcowego w usłudze Microsoft Defender uruchomiono plik wykonywalny wykrywania sieci i odpowiedzi|Uruchomiono plik wykonywalny SenseNdr.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |103|Ochrona punktu końcowego w usłudze Microsoft Defender funkcja wykonywalna wykrywania sieci i reagowania została zakończona|Plik wykonywalny SenseNdr został zakończony.|Normalne powiadomienie operacyjne; nie jest wymagana żadna akcja.|
   |

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Zobacz też
- [Dołączanie urządzeń Windows 10](configure-endpoints.md)
- [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md)
- [Rozwiązywanie problemów z Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
- [Omówienie funkcji analizatora klienta](overview-client-analyzer.md)
- [Pobierz i uruchom analizator klienta](download-client-analyzer.md)
- [Zrozumienie raportu HTML analizatora](analyzer-report.md)
