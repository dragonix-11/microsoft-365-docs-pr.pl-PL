---
title: Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
description: Lista najważniejszych zmian dotyczących Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, whatsnew, release
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
ms.openlocfilehash: 385b139390192d172b3bbbcbefd5efc2b793d4ab
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173502"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

## <a name="1016577-30122032165770"></a>101.65.77 (30.122032.16577.0)

- Ulepszono pole w programie `conflicting_applications` , `mdatp health` aby wyświetlić tylko najnowsze 10 procesów, a także uwzględnić nazwy procesów. Ułatwia to określenie, które procesy mogą być w konflikcie z Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Linux.
- Poprawki błędów

## <a name="1016274-30122022162740"></a>101.62.74 (30.122022.16274.0)

- Rozwiązano problem polegający na tym, że produkt niepoprawnie blokował dostęp do plików o rozmiarze większym niż 2 GB podczas uruchamiania w starszych wersjach jądra
- Poprawki błędów

## <a name="1016093-30122012160930"></a>101.60.93 (30.122012.16093.0)

- Ta wersja zawiera aktualizację zabezpieczeń dla [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1016005-30122012160050"></a>101.60.05 (30.122012.16005.0)

- Dodano obsługę jądra w wersji 2.6.32-754.43.1.el6.x86_64 dla RHEL 6.10
- Poprawki błędów

## <a name="1015880-30122012158800"></a>101.58.80 (30.122012.15880.0)

- Narzędzie wiersza polecenia obsługuje teraz przywracanie plików poddanych kwarantannie do lokalizacji innej niż ta, w której plik został pierwotnie wykryty. Można to zrobić za pośrednictwem programu `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Począwszy od tej wersji, ochronę sieci dla systemu Linux można ocenić na żądanie
- Poprawki błędów

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- Naprawiono awarię produktu wprowadzona w wersji 101.53.02, która wpłynęła na wielu klientów

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Dodano możliwość wykrywania zagrożonych plików jar log4j używanych przez aplikacje Java. Maszyna jest okresowo sprawdzana pod kątem uruchamiania procesów Java z załadowanymi plikami jar log4j. Informacje są zgłaszane do zaplecza Ochrona punktu końcowego w usłudze Microsoft Defender i są widoczne w obszarze Zarządzanie lukami w zabezpieczeniach w portalu.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- Dodano nowy przełącznik do narzędzia wiersza polecenia, aby kontrolować, czy archiwa są skanowane podczas skanowania na żądanie. Można to skonfigurować za pomocą programu `mdatp config scan-archives --value [enabled/disabled]`. Domyślnie jest to ustawienie na wartość `enabled`.
- Poprawki błędów

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- Począwszy od tej wersji, oferujemy obsługę Ochrona punktu końcowego w usłudze Microsoft Defender do następujących dystrybucji: 
  - Wersje RHEL6.7-6.10 i CentOS6.7-6.10.
  - Amazon Linux 2
  - Fedora 33 lub nowsza
- Poprawki błędów


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Dodano nowe przełączniki do narzędzia wiersza polecenia:
  - Kontrolowanie stopnia równoległości skanowania na żądanie. Można to skonfigurować za pomocą programu `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Domyślnie używany jest stopień równoległości `2` .
  - Określ, czy skanowanie po włączeniu lub wyłączeniu aktualizacji analizy zabezpieczeń. Można to skonfigurować za pomocą programu `mdatp config scan-after-definition-update --value [enabled/disabled]`. Domyślnie jest to ustawienie na wartość `enabled`.
- Zmiana poziomu dziennika produktu wymaga teraz podniesienia uprawnień
- Poprawki błędów

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- Począwszy od tej wersji, zagrożenia wykryte podczas skanowania antywirusowego na żądanie wyzwalane za pośrednictwem klienta wiersza polecenia są automatycznie korygowane. Zagrożenia wykryte podczas skanowania wyzwalane za pośrednictwem interfejsu użytkownika nadal wymagają akcji ręcznej.
- `mdatp diagnostic real-time-protection-statistics` Teraz obsługuje dwa dodatkowe przełączniki:
  - `--sort`: sortuje dane wyjściowe malejąco według całkowitej liczby skanowanych plików
  - `--top N`: wyświetla pierwsze wyniki N (działa tylko wtedy, gdy `--sort` jest również określona)
- Ulepszenia wydajności & poprawek błędów

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux jest teraz dostępna w wersji zapoznawczej dla klientów rządowych USA. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA](gov.md).
- Rozwiązano problem polegający na tym, że użycie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux w systemach z systemami plików FUSE doprowadziło do zawieszenia systemu operacyjnego
- Ulepszenia wydajności & innych poprawek błędów

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Ulepszenia wydajności & poprawek błędów

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Poprawa wydajności w sytuacji, gdy cały punkt instalacji jest dodawany do listy wykluczeń programu antywirusowego. Przed tą wersją działanie pliku pochodzące z punktu instalacji było nadal przetwarzane przez produkt. Począwszy od tej wersji, działanie pliku dla wykluczonych punktów instalacji jest pomijane, co prowadzi do lepszej wydajności produktu
- Dodano nową opcję do narzędzia wiersza polecenia, aby wyświetlić informacje o ostatnim skanowaniu na żądanie. Aby wyświetlić informacje o ostatnim skanowaniu na żądanie, uruchom polecenie `mdatp health --details antivirus`
- Inne ulepszenia wydajności & poprawki błędów

## <a name="1011853"></a>101.18.53

- EDR dla systemu Linux jest teraz [ogólnie dostępna](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Dodano nowy przełącznik wiersza polecenia (`--ignore-exclusions`) w celu ignorowania wykluczeń av podczas skanowania niestandardowego (`mdatp scan custom`)
- Rozszerzono `mdatp diagnostic create` o nowy parametr (`--path [directory]`), który umożliwia zapisywanie dzienników diagnostycznych w innym katalogu
- Ulepszenia wydajności & poprawek błędów

## <a name="1011299"></a>101.12.99

- Ulepszenia wydajności & poprawek błędów

## <a name="1010476"></a>101.04.76

- Poprawki błędów

## <a name="1010348"></a>101.03.48

- Poprawki błędów

## <a name="1010255"></a>101.02.55

- Rozwiązano problem polegający na tym, że produkt czasami nie uruchamiał się po ponownym uruchomieniu/uaktualnieniu
- Rozwiązano problem polegający na tym, że ustawienia serwera proxy nie były utrwalane w ramach uaktualnień produktów

## <a name="1010075"></a>101.00.75

- Dodano obsługę następujących typów systemów plików: , , , , , `nfs``overlay`, `ramfs`, `reiserfs`, `udf`i `jfs``fuseblk``fuse``ecryptfs``vfat`
- Nowa składnia [narzędzia wiersza polecenia](linux-resources.md#configure-from-the-command-line).
- Ulepszenia wydajności & poprawek błędów

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Podczas uaktualniania zainstalowanego pakietu z wersji produktu starszej niż 100.90.70 aktualizacja może zakończyć się niepowodzeniem w dystrybucjach opartych na systemie Red Hat i SLES. Jest to spowodowane istotną zmianą ścieżki pliku. Rozwiązaniem tymczasowym jest usunięcie starszego pakietu, a następnie zainstalowanie nowszego. Ten problem nie istnieje w nowszych wersjach.

- [Wykluczenia programu antywirusowego obsługują teraz symbole wieloznaczne](linux-exclusions.md#supported-exclusion-types)
- Dodano możliwość [rozwiązywania problemów z wydajnością](linux-support-perf.md) za pomocą narzędzia wiersza `mdatp` polecenia
- Ulepszenia w celu zwiększenia niezawodności instalacji pakietu
- Ulepszenia wydajności & poprawek błędów
