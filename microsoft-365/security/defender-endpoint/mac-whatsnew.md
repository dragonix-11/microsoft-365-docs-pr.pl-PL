---
title: Co nowego w programie Microsoft Defender dla punktu końcowego na komputerze Mac
description: Dowiedz się więcej o głównych zmianach dotyczących poprzednich wersji programu Microsoft Defender dla punktu końcowego na komputerze Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
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
ms.openlocfilehash: 10ecf1f3906e7968328729257feea9c272562ffb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322635"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Co nowego w programie Microsoft Defender dla punktu końcowego na komputerze Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Ta wersja dodaje obsługę systemu macOS 12.3. Począwszy od wersji 12.3 w systemie macOS, [firma Apple usuwa język Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Domyślnie w systemie macOS nie będzie preinstalowana wersja w języku Python. **WYMAGANE DZIAŁANIE**: 
  - Użytkownicy muszą zaktualizować program Microsoft Defender for Endpoint dla komputerów Mac do wersji 101.59.50 (lub nowszej) przed zaktualizowaniem swoich urządzeń do systemu macOS Monterey 12.3 (lub nowszego). Ta minimalna wersja 101.59.50 jest wymagane do wyeliminowania problemów związanych z programem Python z programem Microsoft Defender for Endpoint dla komputerów Mac w systemie macOS Monterey.
  - W przypadku wdrożeń zdalnych istniejące konfiguracje usługi MDM muszą zostać zaktualizowane do programu Microsoft Defender dla punktu końcowego dla komputerów Mac w wersji 101.59.50 (lub nowszej). Wypychanie za pośrednictwem usługi MDM starszej wersji programu Microsoft Defender dla punktu końcowego dla komputerów Mac do systemu macOS Monterey 12.3 (lub nowszego) spowoduje niepowodzenie instalacji.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Narzędzie wiersza polecenia obsługuje teraz przywracanie plików poddanych kwarantannie do lokalizacji innej niż ta, w której plik został pierwotnie wykryty. Można to zrobić za pośrednictwem .`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`
- Rozszerzona kontrola urządzenia do obsługi urządzeń połączonych za pośrednictwem urządzenia 3
- Ulepszono obsługę zasad sterowania urządzeniami zawierających nieprawidłowe identyfikatory dostawców i identyfikatory produktów. Przed tą wersją, jeśli zasady zawierały jeden lub więcej nieprawidłowych identyfikatorów, cała zasada została zignorowana. Począwszy od tej wersji zignorowane są tylko nieprawidłowe części zasad. Problemy z zasadami są rozwiązane za pośrednictwem `mdatp device-control removable-media policy list`.
- Poprawki błędów

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Poprawki błędów

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Nazwa aplikacji została zmieniona z "Microsoft Defender ATP" na "Microsoft Defender". Użytkownicy końcowi będą obserwować następujące zmiany:
  - Ścieżka instalacji aplikacji została zmieniona z `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app`na .
  - W ramach obsługi użytkownika wystąpienia "Microsoft Defender ATP" zostały zastąpione przez program "Microsoft Defender"
- Rozwiązano problem, gdy niektóre aplikacje VPN nie mogły się połączyć z powodu filtru zawartości sieci, który jest rozpowszechniany z programem Microsoft Defender for Endpoint dla komputerów Mac
- Rozwiązano problem wykryty w systemie macOS 12.2 beta 2, w którym nie można otworzyć pakietu instalacyjnego z powodu zmiany systemu operacyjnego uniemożliwiającego instalowanie pakietów o określonych cechach. Mimo że ta zmiana systemu operacyjnego nie jest uwzględniona w ostatecznej wersji systemu macOS 12.2, prawdopodobnie zostanie ona ponownie włączona w przyszłej wersji systemu macOS. W związku z tym zachęcamy wszystkich administratorów przedsiębiorstwa do odświeżenia pakietu Microsoft Defender for Endpoint w ich konsoli zarządzania do tej wersji produktu (lub nowszej).
- Rozwiązano problem spotykany na niektórych urządzeniach M1, na których produkt utknął z nieprawidłowymi definicjami złośliwych kodów i nie mógł pomyślnie zaktualizować do zestawu roboczej definicji.
- `mdatp health` Rozszerzono dane wyjściowe o `full_disk_access_enabled` dodatkowy atrybut, który może zostać użyty w celu określenia, czy pełny dostęp na dysku został przyznany wszystkim składnikom programu Microsoft Defender for Endpoint dla komputerów Mac.
- Ulepszenia wydajności & poprawki błędów

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- System macOS 10.14 (Mojave) nie jest już obsługiwany
- Po zakończeniu zarządzania ustawieniem produktu przez administratora za pośrednictwem usługi MDM przywracana jest wartość, która była wcześniej zarządzana (wartość skonfigurowana lokalnie przez użytkownika końcowego lub, jeśli nie została jawnie określona żadna wartość lokalna, wartość domyślna używana przez produkt). Przed tą zmianą po zatrzymaniu zarządzania ustawieniem jego zarządzana wartość była nadal używana przez produkt.
- Ulepszenia wydajności & poprawki błędów

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Dodano nowy przełącznik do narzędzia wiersza polecenia w celu kontrolowania, czy archiwa są skanowane podczas skanowania na żądanie. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config scan-archives --value [enabled/disabled]`. Domyślnie jest ustawiona wartość `enabled`.
- Poprawki błędów

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Poprawka dla zawieszania się systemu podczas zamykania systemu w systemie macOS Mojave i macOS Catalina

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Kompilacja kandydata dla systemu macOS 12 (Monterey)
- Poprawki błędów

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Dodano nowe przełączniki do narzędzia wiersza polecenia:
  - Kontroluj stopień równoległości w skanach na żądanie. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Domyślnie stosowany jest stopień równoległości `2` .
  - Kontroluj, czy skanuje po włączeniu aktualizacji analizy zabezpieczeń, czy też jest wyłączony. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config scan-after-definition-update --value [enabled/disabled]`. Domyślnie jest ustawiona wartość `enabled`.
- Zmiana poziomu dziennika produktu wymaga teraz podwyższenia
- Ulepszenia wydajności & poprawki błędów

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Natywne wsparcie techniczne mikroukładu M1
- Ulepszenia wydajności & poprawki błędów

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Poprawki błędów

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Poprawki błędów

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Kontrola urządzeń dla systemu macOS](mac-device-control-overview.md) jest teraz ogólnie dostępne
- Rozwiązano problem, gdy nie można rozpocząć szybkiego skanowania z menu stanu w systemie macOS 11 (Big Sur)
- Inne poprawki błędów

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Rozwiązano problem, w którym współbieżny dostęp do keychain z usługi Microsoft Defender for Endpoint i innych aplikacji może powodować uszkodzenie keychain.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Począwszy od tej wersji, zagrożenia wykryte podczas skanów antywirusowych na żądanie wywoływanych przez klienta wiersza polecenia są automatycznie korygowane. Zagrożenia wykryte podczas skanów wyzwalanych za pośrednictwem interfejsu użytkownika nadal wymagają ręcznego działania.
- `mdatp diagnostic real-time-protection-statistics` Teraz obsługuje dwa dodatkowe przełączniki:
  - `--sort`: sortuje dane wyjściowe w kolejności malejącej według łącznej liczby zeskanowanych plików.
  - `--top N`: wyświetla najważniejsze wyniki N (działa tylko wtedy, gdy `--sort` jest również określona)
- Ulepszenia wydajności (zwłaszcza w przypadku korzystania z funkcji ZAOSTR.&) i poprawek błędów

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Poprawka, aby zmieścić się w wygaśnięciu certyfikatu firmy Apple dla systemu macOS Catalina i starszych wersji. Ta poprawka przywraca & zarządzania lukami w zabezpieczeniach.

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Program Microsoft Defender for Endpoint w systemie macOS jest teraz dostępny w wersji preview dla klientów z wersjami dla instytucji rządowych Stanów Zjednoczonych. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych](gov.md).
- Ulepszenia wydajności (w szczególności w sytuacji, gdy jest używana aplikacja kod XCode) & poprawki błędów.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Dodano nową opcję do narzędzia wiersza polecenia w celu wyświetlania informacji o ostatnim skanie na żądanie. Aby wyświetlić informacje dotyczące ostatniego skanowania na żądanie, uruchom `mdatp health --details antivirus`
- Ulepszenia wydajności & poprawki błędów

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> W tym wydaniu stara składnia narzędzia wiersza polecenia została wycofana. Aby uzyskać informacje na temat nowej składni, zobacz [Zasoby](mac-resources.md#configuring-from-the-command-line).

- Dodano nowy przełącznik wiersza polecenia, aby wyłączyć rozszerzenie sieci: `mdatp system-extension network-filter disable`. To polecenie może być przydatne do rozwiązywania problemów z siecią, które mogą być związane z programem Microsoft Defender for Endpoint na komputerze Mac
- Ulepszenia wydajności & poprawki błędów

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Poprawki błędów

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Ulepszono niezawodność agenta podczas pracy w systemie macOS 11 Big Sur
- Dodano nowy przełącznik wiersza polecenia (`--ignore-exclusions`), który umożliwia ignorowanie wykluczeń audio/wideo podczas skanowania niestandardowego (`mdatp scan custom`)
- Ulepszenia wydajności & poprawki błędów

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Usunięto warunki, gdy program Microsoft Defender dla punktu końcowego wyzwalał błąd macOS 11 (Big Sur), który pojawia się w paniki kernelu
- Usunięto wyciek pamięci w rozszerzeniu systemu zabezpieczeń punktu końcowego podczas uruchamiania na komputerze Mac 11 (Big Sur)
- Poprawki błędów

## <a name="1011072"></a>101.10.72

- Poprawki błędów

## <a name="1010961"></a>101.09.61

- Dodano nową zarządzaną [preferencję wyłączania opcji wysyłania opinii](mac-preferences.md#show--hide-option-to-send-feedback)
- Ikona menu stanu pokazuje teraz stan dobrej kondycji w przypadku zarządzania ustawieniami produktu. Wcześniej ikona menu statusu wyświetlała ostrzeżenie lub stan błędu, mimo że ustawieniami produktu zarządzał administrator
- Ulepszenia wydajności & poprawki błędów

## <a name="1010950"></a>101.09.50

- Ta wersja produktu została zweryfikowana w systemie macOS Big Sur 11 beta 9

- Nowa składnia narzędzia `mdatp` wiersza polecenia jest teraz składnią domyślną. Aby uzyskać więcej informacji na temat nowej składni, zobacz [Zasoby dotyczące programu Microsoft Defender dla punktu końcowego w systemie macOS.](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Stara składnia narzędzia wiersza polecenia zostanie usunięta z produktu **1 stycznia 2021 r**.

- Rozszerzona `mdatp diagnostic create` o nowy parametr (`--path [directory]`), który umożliwia zapisanie dzienników diagnostycznych w innym katalogu
- Ulepszenia wydajności & poprawki błędów

## <a name="1010949"></a>101.09.49

- Ulepszenia interfejsu użytkownika odróżniają wykluczenia zarządzane przez administratora IT od wykluczeń zdefiniowanych przez użytkownika lokalnego
- Ulepszone wykorzystanie procesora podczas skanów na żądanie
- Ulepszenia wydajności & poprawki błędów

## <a name="1010723"></a>101.07.23

- Dodano nowe pola do wyniku w `mdatp --health` celu sprawdzenia stanu trybu pasywnego i identyfikatora EDR grupy

  > [!NOTE]
  > `mdatp --health` zostaną zastąpione w `mdatp health` przyszłej aktualizacji produktu.

- Usunięto błąd, gdy automatyczne przesyłanie próbek nie zostało oznaczone jako zarządzane w interfejsie użytkownika
- Dodano nowe ustawienia kontrolowania przechowywania elementów w historii skanowania oprogramowania antywirusowego. Teraz możesz [określić liczbę dni przechowywania](mac-preferences.md#antivirus-scan-history-retention-in-days) elementów w historii skanowania i określić maksymalną liczbę elementów [w historii skanowania.](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Poprawki błędów

## <a name="1010663"></a>101.06.63

- Rozwiązano regresję wydajności wprowadzono w wersji `101.05.17`. Regresja została wprowadzona razem z poprawką w celu wyeliminowania paniki kernelów obserwowanych przez niektórych klientów podczas uzyskiwania dostępu do udziałów SMB. Przywróciliśmy tę zmianę kodu i pracujemy nad alternatywnymi sposobami usunięcia jądrowych panik.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Pracujemy nad nową i rozszerzoną składnią narzędzia `mdatp` wiersza polecenia. Nowa składnia jest obecnie domyślną składnią w kanałach aktualizacji Niejawny program testów szybkie i Wolne aktualizacje w niejawnym programie testów. Zachęcamy do fałszowanie się tą nową składnią.
>
> Będziemy nadal obsługiwać starą składnię równolegle z nową składnią i zapewnimy więcej komunikacji dotyczącej planu deprecationu dla starej składni w nadchodzących miesiącach.

- Rozwiązano problem paniki z kernelmi, która czasami występowała podczas uzyskiwania dostępu do udziałów plików SMB
- Ulepszenia wydajności & poprawki błędów

## <a name="1010516"></a>101.05.16

- Ulepszenia logiki szybkiego skanowania w celu znacznego zmniejszenia liczby zeskanowanych plików
- [Dodano obsługę autouzupełniania](mac-resources.md#how-to-enable-autocompletion) dla narzędzia wiersza polecenia
- Poprawki błędów

## <a name="1010312"></a>101.03.12

- Ulepszenia wydajności & poprawki błędów

## <a name="1010154"></a>101.01.54

- Ulepszenia dotyczące zgodności z time machine
- Ulepszenia ułatwień dostępu
- Ulepszenia wydajności & poprawki błędów

## <a name="1010031"></a>101.00.31

- Ulepszone [środowisko dołączania produktu dla użytkowników usługi Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)
- [Wykluczenia oprogramowania antywirusowego obsługują teraz symbole wieloznaczne](mac-exclusions.md#supported-exclusion-types)
- Dodano możliwość wyzwalania skanów antywirusowych z menu kontekstowego systemu macOS. Teraz możesz kliknąć prawym przyciskiem myszy plik lub folder w programie Finder i wybrać polecenie **Skanuj za pomocą programu Microsoft Defender w celu wybrania punktu końcowego**
- Zmiany na starszą wersję produktu w miejscu są teraz jawnie niedozwolone przez instalatora. Jeśli chcesz zmienić wersję na starszą, najpierw odinstaluj istniejącą wersję i ponownie skonfiguruj swoje urządzenie
- Inne ulepszenia wydajności & poprawek błędów

## <a name="1009027"></a>100.90.27

- Teraz możesz ustawić [kanał aktualizacji dla programu](mac-updates.md#set-the-channel-name) Microsoft Defender dla punktu końcowego w systemie macOS, który różni się od kanału aktualizacji dla całego systemu
- Ikona nowego produktu
- Inne ulepszenia w zakresie obsługi użytkowników
- Poprawki błędów

## <a name="1008692"></a>100.86.92

- Ulepszenia dotyczące zgodności z time machine
- Rozwiązano problem, gdy produkt czasami nie `/Library/Application Support/Microsoft/Defender` czyścił wszystkich plików podczas dezinstalacji
- Zmniejszenie użycia procesora w produkcie w przypadku aktualizowania produktów firmy Microsoft za pomocą programu Microsoft AutoUpdate
- Inne ulepszenia wydajności & poprawek błędów

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> Aby zapewnić pełną ochronę urządzeń z systemem macOS i wyrównanie do zatrzymania przez Apple dostarczania natywnych aktualizacji zabezpieczeń systemu macOS dla wersji systemu operacyjnego starszych niż [current - 2], wdrażanie i aktualizacje MDATP dla komputerów Mac nie będą już obsługiwane w systemie macOS Sierra [10.12]. Usługi MDATP dla komputerów Mac będą dostarczane do urządzeń z wersjami Catalina [10.15], Mojave [10.14] i High Sierra [10.13].
>
> Jeśli masz już program MDATP dla komputerów Mac wdrożony na urządzeniach z systemem Sierra [10.12], uaktualnij system do najnowszej wersji systemu macOS, aby wyeliminować ryzyko utraty ochrony.

- Ulepszenia wydajności & poprawki błędów

## <a name="1008373"></a>100.83.73

- Dodano więcej kontrolek dla administratorów IT dotyczących zarządzania wykluczeniami[, zarządzania](mac-preferences.md#threat-type-settings-merge-policy) ustawieniami typu zagrożeń i [niedozwolonej akcji zagrożeń](mac-preferences.md#disallowed-threat-actions) [](mac-preferences.md#exclusion-merge-policy)
- Gdy na urządzeniu nie włączono pełnego dostępu do dysku, w menu stanu jest teraz wyświetlane ostrzeżenie
- Ulepszenia wydajności & poprawki błędów

## <a name="1008260"></a>100.82.60

- Rozwiązano problem, gdy produkt nie może rozpocząć się po aktualizacji definicji.

## <a name="1008042"></a>100.80.42

- Poprawki błędów

## <a name="1007942"></a>100.79.42

- Rozwiązano problem, gdy program Microsoft Defender dla punktu końcowego na komputerze Mac czasami zakłócał program Time Machine
- Dodano nowy przełącznik do narzędzia wiersza polecenia w celu przetestowania łączności z usługą zaplecza

  ```bash
  mdatp connectivity test
  ```

- Dodano możliwość wyświetlania pełnej historii zagrożeń w interfejsie użytkownika (dostęp do niej można uzyskać z **poziomu widoku Historia** ochrony)
- Ulepszenia wydajności & poprawki błędów

## <a name="1007215"></a>100.72.15

- Poprawki błędów

## <a name="1007099"></a>100.70.99

- Rozwiązano problem, który wpływa na możliwość uaktualnienia niektórych użytkowników do systemu macOS Catalina po włączeniu ochrony w czasie rzeczywistym. Ten sporadyczne problem został spowodowany przez program Microsoft Defender for Endpoint blokujący pliki w pakiecie uaktualniania Catalina podczas skanowania ich w celu skanowania ich w celu ochrony przed zagrożeniami, co powodowało błędy w sekwencji uaktualniania.

## <a name="1006899"></a>100.68.99

- Dodano możliwość konfigurowania funkcji oprogramowania antywirusowego do działania w [trybie pasywnym](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Ulepszenia wydajności & poprawki błędów

## <a name="1006528"></a>100.65.28

- Dodano obsługę systemu macOS Catalina

  > [!CAUTION]
  > System macOS 10.15 (Catalina) zawiera nowe udoskonalenia zabezpieczeń i prywatności. Począwszy od tej wersji aplikacje nie mogą domyślnie uzyskać dostępu do określonych lokalizacji na dysku (takich jak Dokumenty, Pliki do pobrania, Pulpit itp.) bez wyraźnej zgody. W przypadku braku tej zgody usługa Microsoft Defender for Endpoint nie może w pełni chronić Twojego urządzenia.
  >
  > Mechanizm udzielania tej zgody zależy od sposobu wdrożenia programu Microsoft Defender dla punktu końcowego:
  >
  > - Zaktualizowane instrukcje znajdziesz w temacie Wdrażanie [ręczne](mac-install-manually.md#how-to-allow-full-disk-access) .
  > - Aby uzyskać informacje na temat wdrożeń zarządzanych, zobacz zaktualizowane instrukcje w tematach wdrażania opartych na technologii [JAMF](mac-install-with-jamf.md) [Microsoft Intune na temat wdrażania opartego na usługach](mac-install-with-intune.md#create-system-configuration-profiles).

- Ulepszenia wydajności & poprawki błędów
