---
title: Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
description: Dowiedz się więcej o najważniejszych zmianach w poprzednich wersjach Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach Mac.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d36d05a4abe36ffe63e53eb8e164e248755de0ec
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665915"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1016169-20122022161690"></a>101.61.69 (20.122022.16169.0)

- Poprawki błędów

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Ta wersja zawiera aktualizację zabezpieczeń dla [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Ta wersja dodaje obsługę systemu macOS 12.3. Począwszy od systemu macOS 12.3, [firma Apple usuwa język Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Nie będzie domyślnie wstępnie zainstalowanej wersji języka Python w systemie macOS. **WYMAGANA AKCJA**: 
  - Użytkownicy muszą zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac do wersji 101.59.50 (lub nowszej) przed zaktualizowaniem swoich urządzeń do systemu macOS Monterey 12.3 (lub nowszego). Ta minimalna wersja 101.59.50 jest wymaganiem wstępnym wyeliminowania problemów związanych z językiem Python z Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac w systemie macOS Monterey.
  - W przypadku wdrożeń zdalnych istniejące konfiguracje mdm muszą zostać zaktualizowane w celu Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac w wersji 101.59.50 (lub nowszej). Wypychanie za pośrednictwem rozwiązania MDM starszej Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac do systemu macOS Monterey 12.3 (lub nowszego) spowoduje niepowodzenie instalacji.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Narzędzie wiersza polecenia obsługuje teraz przywracanie plików poddanych kwarantannie do lokalizacji innej niż ta, w której plik został pierwotnie wykryty. Można to zrobić za pośrednictwem programu `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Rozszerzona kontrola urządzenia do obsługi urządzeń połączonych za pośrednictwem rozwiązania Thunderbolt 3
- Ulepszono obsługę zasad kontroli urządzeń zawierających nieprawidłowe identyfikatory dostawców i identyfikatory produktów. Przed tą wersją, jeśli zasady zawierały co najmniej jeden nieprawidłowy identyfikator, całe zasady zostały zignorowane. Począwszy od tej wersji, ignorowane są tylko nieprawidłowe części zasad. Problemy z zasadami są wyświetlane za pośrednictwem `mdatp device-control removable-media policy list`programu .
- Poprawki błędów

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Poprawki błędów

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Nazwa aplikacji została zmieniona z "Microsoft Defender ATP" na "Microsoft Defender". Użytkownicy końcowi będą obserwować następujące zmiany:
  - Ścieżka instalacji aplikacji została zmieniona z `/Application/Microsoft Defender ATP.app` na `/Applications/Microsoft Defender.app`.
  - W środowisku użytkownika wystąpienia "Microsoft Defender ATP" zostały zastąpione ciągiem "Microsoft Defender"
- Rozwiązano problem polegający na tym, że niektóre aplikacje sieci VPN nie mogły nawiązać połączenia z powodu filtru zawartości sieciowej dystrybuowanego za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac
- Rozwiązano problem wykryty w systemie macOS 12.2 beta 2, w którym nie można otworzyć pakietu instalacyjnego z powodu zmiany systemu operacyjnego ,która uniemożliwia instalowanie pakietów o pewnych cechach. Chociaż wydaje się, że ta zmiana systemu operacyjnego nie jest uwzględniona w ostatecznej wersji systemu macOS 12.2, prawdopodobnie zostanie ona ponownie wprowadzona w przyszłej wersji systemu macOS. W związku z tym zachęcamy wszystkich administratorów przedsiębiorstwa do odświeżenia pakietu Ochrona punktu końcowego w usłudze Microsoft Defender w konsoli zarządzania do tej wersji produktu (lub nowszej wersji).
- Rozwiązano problem występujący na niektórych urządzeniach M1, na których produkt został zablokowany z nieprawidłowymi definicjami ochrony przed złośliwym kodem i nie mógł pomyślnie zaktualizować do działającego zestawu definicji.
- `mdatp health`Dane wyjściowe zostały rozszerzone o dodatkowy atrybut o nazwie `full_disk_access_enabled` , którego można użyć do określenia, czy udzielono pełnego dostępu do dysku wszystkim składnikom Ochrona punktu końcowego w usłudze Microsoft Defender dla komputerów Mac.
- Ulepszenia wydajności & poprawek błędów

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- System macOS 10.14 (Mojave) nie jest już obsługiwany
- Gdy ustawienie produktu przestanie być zarządzane przez administratora za pośrednictwem rozwiązania MDM, przywraca teraz wartość, którą miał przed zarządzaniem (wartość skonfigurowana lokalnie przez użytkownika końcowego lub, jeśli nie została jawnie podana taka wartość lokalna, wartość domyślna używana przez produkt). Przed tą zmianą, po zatrzymaniu zarządzania ustawieniem, jego wartość zarządzana utrwaliła się i była nadal używana przez produkt.
- Ulepszenia wydajności & poprawek błędów

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Dodano nowy przełącznik do narzędzia wiersza polecenia, aby kontrolować, czy archiwa są skanowane podczas skanowania na żądanie. Można to skonfigurować za pomocą programu `mdatp config scan-archives --value [enabled/disabled]`. Domyślnie jest to ustawienie na wartość `enabled`.
- Poprawki błędów

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Poprawka dotycząca zamrożenia systemu występującego podczas zamykania systemu macOS Mojave i macOS Catalina

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Kompilacja kandydata dla systemu macOS 12 (Monterey)
- Poprawki błędów

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Dodano nowe przełączniki do narzędzia wiersza polecenia:
  - Kontrolowanie stopnia równoległości skanowania na żądanie. Można to skonfigurować za pomocą programu `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Domyślnie używany jest stopień równoległości `2` .
  - Określ, czy skanowanie po włączeniu lub wyłączeniu aktualizacji analizy zabezpieczeń. Można to skonfigurować za pomocą programu `mdatp config scan-after-definition-update --value [enabled/disabled]`. Domyślnie jest to ustawienie na wartość `enabled`.
- Zmiana poziomu dziennika produktu wymaga teraz podniesienia uprawnień
- Ulepszenia wydajności & poprawek błędów

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Obsługa natywnych mikroukładów M1
- Ulepszenia wydajności & poprawek błędów

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Poprawki błędów

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Poprawki błędów

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Kontrola urządzenia dla systemu macOS](mac-device-control-overview.md) jest teraz ogólnie dostępna
- Rozwiązano problem polegający na tym, że nie można było uruchomić szybkiego skanowania z menu stanu w systemie macOS 11 (Big Sur)
- Inne poprawki błędów

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Rozwiązano problem polegający na tym, że współbieżny dostęp do łańcucha kluczy z Ochrona punktu końcowego w usłudze Microsoft Defender i innych aplikacji może prowadzić do uszkodzenia łańcucha kluczy.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Począwszy od tej wersji, zagrożenia wykryte podczas skanowania antywirusowego na żądanie wyzwalane za pośrednictwem klienta wiersza polecenia są automatycznie korygowane. Zagrożenia wykryte podczas skanowania wyzwalane za pośrednictwem interfejsu użytkownika nadal wymagają akcji ręcznej.
- `mdatp diagnostic real-time-protection-statistics` Teraz obsługuje dwa dodatkowe przełączniki:
  - `--sort`: sortuje dane wyjściowe malejąco według całkowitej liczby skanowanych plików
  - `--top N`: wyświetla pierwsze wyniki N (działa tylko wtedy, gdy `--sort` jest również określona)
- Ulepszenia wydajności (szczególnie w przypadku użycia usługi YARN) & poprawek błędów

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Poprawka umożliwiająca uwzględnienie wygaśnięcia certyfikatu firmy Apple dla systemu macOS Catalina i wcześniejszych. Ta poprawka przywraca funkcje zarządzania lukami w zabezpieczeniach & zagrożeń (TVM).

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS jest teraz dostępna w wersji zapoznawczej dla klientów rządowych USA. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA](gov.md).
- Ulepszenia wydajności (szczególnie w sytuacji, gdy jest używana aplikacja symulatora XCode) & poprawki błędów.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Dodano nową opcję do narzędzia wiersza polecenia, aby wyświetlić informacje o ostatnim skanowaniu na żądanie. Aby wyświetlić informacje o ostatnim skanowaniu na żądanie, uruchom polecenie `mdatp health --details antivirus`
- Ulepszenia wydajności & poprawek błędów

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> Stara składnia narzędzia wiersza polecenia została wycofana z tej wersji. Aby uzyskać informacje na temat nowej składni, zobacz [Zasoby](mac-resources.md#configuring-from-the-command-line).

- Dodano nowy przełącznik wiersza polecenia, aby wyłączyć rozszerzenie sieci: `mdatp system-extension network-filter disable`. To polecenie może być przydatne do rozwiązywania problemów z siecią, które mogą być związane z Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
- Ulepszenia wydajności & poprawek błędów

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Poprawki błędów

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Zwiększono niezawodność agenta podczas uruchamiania w systemie macOS 11 Big Sur
- Dodano nowy przełącznik wiersza polecenia (`--ignore-exclusions`) w celu ignorowania wykluczeń av podczas skanowania niestandardowego (`mdatp scan custom`)
- Ulepszenia wydajności & poprawek błędów

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Usunięto warunki, gdy Ochrona punktu końcowego w usłudze Microsoft Defender wyzwalała usterkę systemu macOS 11 (Big Sur), która objawia się paniką jądra
- Naprawiono wyciek pamięci w rozszerzeniu systemu zabezpieczeń punktu końcowego podczas uruchamiania na komputerze mac 11 (Big Sur)
- Poprawki błędów

## <a name="1011072"></a>101.10.72

- Poprawki błędów

## <a name="1010961"></a>101.09.61

- Dodano nową preferencję zarządzaną [dotyczącą wyłączania opcji wysyłania opinii](mac-preferences.md#show--hide-option-to-send-feedback)
- Ikona menu stanu pokazuje teraz stan dobrej kondycji, gdy ustawienia produktu są zarządzane. Wcześniej ikona menu stanu wyświetlała stan ostrzeżenia lub błędu, mimo że ustawienia produktu były zarządzane przez administratora
- Ulepszenia wydajności & poprawek błędów

## <a name="1010950"></a>101.09.50

- Ta wersja produktu została zweryfikowana w systemie macOS Big Sur 11 beta 9

- Nowa składnia narzędzia wiersza `mdatp` polecenia jest teraz domyślna. Aby uzyskać więcej informacji na temat nowej składni, zobacz [Zasoby dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Stara składnia narzędzia wiersza polecenia zostanie usunięta z produktu **1 stycznia 2021** r.

- Rozszerzono `mdatp diagnostic create` o nowy parametr (`--path [directory]`), który umożliwia zapisywanie dzienników diagnostycznych w innym katalogu
- Ulepszenia wydajności & poprawek błędów

## <a name="1010949"></a>101.09.49

- Ulepszenia interfejsu użytkownika w celu odróżnienia wykluczeń zarządzanych przez administratora IT od wykluczeń zdefiniowanych przez użytkownika lokalnego
- Ulepszone wykorzystanie procesora CPU podczas skanowania na żądanie
- Ulepszenia wydajności & poprawek błędów

## <a name="1010723"></a>101.07.23

- Dodano nowe pola do danych wyjściowych sprawdzania `mdatp --health` stanu trybu pasywnego i identyfikatora grupy EDR

  > [!NOTE]
  > `mdatp --health` zostaną zastąpione `mdatp health` w przyszłej aktualizacji produktu.

- Usunięto usterkę polegającą na tym, że automatyczne przesyłanie przykładów nie było oznaczone jako zarządzane w interfejsie użytkownika
- Dodano nowe ustawienia kontroli przechowywania elementów w historii skanowania antywirusowego. Teraz możesz [określić liczbę dni przechowywania elementów w historii skanowania](mac-preferences.md#antivirus-scan-history-retention-in-days) i [określić maksymalną liczbę elementów w historii skanowania](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Poprawki błędów

## <a name="1010663"></a>101.06.63

- Rozwiązano problem regresji wydajności wprowadzonej w wersji `101.05.17`. Regresja została wprowadzona wraz z poprawką eliminującą panikę jądra obserwowaną przez niektórych klientów podczas uzyskiwania dostępu do udziałów SMB. Przywróciliśmy tę zmianę kodu i badamy alternatywne sposoby eliminowania panik jądra.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Pracujemy nad nową i ulepszoną składnią narzędzia wiersza `mdatp` polecenia. Nowa składnia jest obecnie domyślna w kanałach szybkiej i powolnej aktualizacji niejawnych testerów. Zachęcamy do zapoznania się z tą nową składnią.
>
> Będziemy nadal obsługiwać starą składnię równolegle z nową składnią i zapewnimy większą komunikację wokół planu wycofania starej składni w nadchodzących miesiącach.

- Rozwiązano problem błędu jądra, który czasami występował podczas uzyskiwania dostępu do udziałów plików SMB
- Ulepszenia wydajności & poprawek błędów

## <a name="1010516"></a>101.05.16

- Ulepszenia logiki szybkiego skanowania w celu znacznego zmniejszenia liczby skanowanych plików
- Dodano [obsługę autouzupełniania](mac-resources.md#how-to-enable-autocompletion) dla narzędzia wiersza polecenia
- Poprawki błędów

## <a name="1010312"></a>101.03.12

- Ulepszenia wydajności & poprawek błędów

## <a name="1010154"></a>101.01.54

- Ulepszenia dotyczące zgodności z maszyną czasomierza
- Ulepszenia ułatwień dostępu
- Ulepszenia wydajności & poprawek błędów

## <a name="1010031"></a>101.00.31

- Ulepszone [środowisko dołączania produktów dla użytkowników Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)
- [Wykluczenia programu antywirusowego obsługują teraz symbole wieloznaczne](mac-exclusions.md#supported-exclusion-types)
- Dodano możliwość wyzwalania skanowania antywirusowego z menu kontekstowego systemu macOS. Teraz możesz kliknąć prawym przyciskiem myszy plik lub folder w programie Finder i wybrać pozycję **Skanuj przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender**
- Zmiany na starszą wersję produktu w miejscu są teraz jawnie niedozwolone przez instalatora. Jeśli chcesz obniżyć poziom, najpierw odinstaluj istniejącą wersję i ponownie skonfiguruj urządzenie
- Inne ulepszenia wydajności & poprawki błędów

## <a name="1009027"></a>100.90.27

- Teraz możesz [ustawić kanał aktualizacji](mac-updates.md#set-the-channel-name) dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS, który różni się od kanału aktualizacji dla całego systemu
- Ikona nowego produktu
- Inne ulepszenia środowiska użytkownika
- Poprawki błędów

## <a name="1008692"></a>100.86.92

- Ulepszenia dotyczące zgodności z maszyną czasomierza
- Rozwiązano problem polegający na tym, że produkt czasami nie czyścił wszystkich plików podczas `/Library/Application Support/Microsoft/Defender` dezinstalacji
- Zmniejszono wykorzystanie procesora CPU produktu, gdy produkty firmy Microsoft są aktualizowane za pośrednictwem usługi Microsoft AutoUpdate
- Inne ulepszenia wydajności & poprawki błędów

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> Aby zapewnić najbardziej pełną ochronę urządzeń z systemem macOS i zgodną z zatrzymaniem przez firmę Apple dostarczania natywnych aktualizacji zabezpieczeń systemu macOS do wersji systemu operacyjnego starszych niż [bieżące — 2], wdrożenie i aktualizacje protokołu MDATP dla komputerów Mac nie będą już obsługiwane w systemie macOS Sierra [10.12]. Aktualizacje i ulepszenia protokołu MDATP dla komputerów Mac zostaną dostarczone do urządzeń z uruchomionymi wersjami Catalina [10.15], Mojave [10.14] i High Sierra [10.13].
>
> Jeśli masz już protokół MDATP dla komputerów Mac wdrożony na urządzeniach Sierra [10.12], uaktualnij go do najnowszej wersji systemu macOS, aby wyeliminować ryzyko utraty ochrony.

- Ulepszenia wydajności & poprawek błędów

## <a name="1008373"></a>100.83.73

- Dodano więcej kontrolek dla administratorów IT dotyczących [zarządzania wykluczeniami](mac-preferences.md#exclusion-merge-policy), [zarządzania ustawieniami typu zagrożenia](mac-preferences.md#threat-type-settings-merge-policy) i [niedozwolonych akcji zagrożeń](mac-preferences.md#disallowed-threat-actions)
- Jeśli na urządzeniu nie włączono dostępu do pełnego dysku, w menu stanu zostanie wyświetlone ostrzeżenie
- Ulepszenia wydajności & poprawek błędów

## <a name="1008260"></a>100.82.60

- Rozwiązano problem polegający na tym, że nie można uruchomić produktu po aktualizacji definicji.

## <a name="1008042"></a>100.80.42

- Poprawki błędów

## <a name="1007942"></a>100.79.42

- Rozwiązano problem polegający na tym, że Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac czasami zakłócał czasomierz
- Dodano nowy przełącznik do narzędzia wiersza polecenia w celu przetestowania łączności z usługą zaplecza

  ```bash
  mdatp connectivity test
  ```

- Dodano możliwość wyświetlania pełnej historii zagrożeń w interfejsie użytkownika (dostęp można uzyskać z widoku **historia ochrony** )
- Ulepszenia wydajności & poprawek błędów

## <a name="1007215"></a>100.72.15

- Poprawki błędów

## <a name="1007099"></a>100.70.99

- Rozwiązano problem, który wpływa na możliwość uaktualnienia niektórych użytkowników do systemu macOS Catalina po włączeniu ochrony w czasie rzeczywistym. Ten sporadyczny problem był spowodowany przez Ochrona punktu końcowego w usłudze Microsoft Defender blokowanie plików w pakiecie uaktualniania Catalina podczas skanowania ich pod kątem zagrożeń, co doprowadziło do błędów w sekwencji uaktualniania.

## <a name="1006899"></a>100.68.99

- Dodano możliwość skonfigurowania funkcji antywirusowej do uruchamiania w [trybie pasywnym](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Ulepszenia wydajności & poprawek błędów

## <a name="1006528"></a>100.65.28

- Dodano obsługę systemu macOS Catalina

  > [!CAUTION]
  > System macOS 10.15 (Catalina) zawiera nowe ulepszenia zabezpieczeń i prywatności. Począwszy od tej wersji, domyślnie aplikacje nie mogą uzyskać dostępu do niektórych lokalizacji na dysku (takich jak Dokumenty, Pliki do pobrania, Pulpit itp.) bez wyraźnej zgody. W przypadku braku tej zgody Ochrona punktu końcowego w usłudze Microsoft Defender nie jest w stanie w pełni chronić urządzenia.
  >
  > Mechanizm udzielania tej zgody zależy od sposobu wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender:
  >
  > - Aby zapoznać się z wdrożeniami ręcznymi, zobacz zaktualizowane instrukcje w temacie [Wdrażanie ręczne](mac-install-manually.md#how-to-allow-full-disk-access) .
  > - W przypadku wdrożeń zarządzanych zobacz zaktualizowane instrukcje w tematach [wdrażania opartego na narzędziu JAMF](mac-install-with-jamf.md) i [Microsoft Intune.](mac-install-with-intune.md#create-system-configuration-profiles)

- Ulepszenia wydajności & poprawek błędów
