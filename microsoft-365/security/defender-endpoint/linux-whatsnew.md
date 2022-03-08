---
title: Co nowego w programie Microsoft Defender dla punktu końcowego w systemie Linux
description: Lista głównych zmian dla programu Microsoft Defender dla punktu końcowego w systemie Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, whatsnew, release
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
ms.openlocfilehash: 58ba49a49b41d80bacb31efa780530e44a146fc1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326765"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Co nowego w programie Microsoft Defender dla punktu końcowego w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="1015880-30122012158800"></a>101.58.80 (30.122012.15880.0)

- Narzędzie wiersza polecenia obsługuje teraz przywracanie plików poddanych kwarantannie do lokalizacji innej niż ta, w której plik został pierwotnie wykryty. Można to zrobić za pośrednictwem .`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`
- Poprawki błędów

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- Usunięto awarię produktu w wersji 101.53.02, która wpływała na wielu klientów

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Dodano funkcję wykrywania wrażliwych jarsów log4j w użyciu przez aplikacje Java. Komputer jest okresowo sprawdzany pod celu uruchomienia procesów języka Java z załadowanym słoikami log4j. Informacje są raportowane w zapleczam programu Microsoft Defender for Endpoint i są udostępniane w obszarze Zarządzania lukami w zabezpieczeniach portalu.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- Dodano nowy przełącznik do narzędzia wiersza polecenia w celu kontrolowania, czy archiwa są skanowane podczas skanowania na żądanie. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config scan-archives --value [enabled/disabled]`. Domyślnie jest ustawiona wartość `enabled`.
- Poprawki błędów

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- Począwszy od tej wersji wprowadzamy obsługę programu Microsoft Defender for Endpoint w następujących systemach: 
  - R NAT.6.7-6.10 i CentOS6.7-6.10.
  - Amazon Linux 2
  - Fedora 33 lub wyższa
- Poprawki błędów


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Dodano nowe przełączniki do narzędzia wiersza polecenia:
  - Kontroluj stopień równoległości w skanach na żądanie. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Domyślnie stosowany jest stopień równoległości `2` .
  - Kontroluj, czy skanuje po włączeniu aktualizacji analizy zabezpieczeń, czy też jest wyłączony. Tę możliwość można skonfigurować za pośrednictwem usługi `mdatp config scan-after-definition-update --value [enabled/disabled]`. Domyślnie jest ustawiona wartość `enabled`.
- Zmiana poziomu dziennika produktu wymaga teraz podwyższenia
- Poprawki błędów

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- Począwszy od tej wersji, zagrożenia wykryte podczas skanów antywirusowych na żądanie wywoływanych przez klienta wiersza polecenia są automatycznie korygowane. Zagrożenia wykryte podczas skanów wyzwalanych za pośrednictwem interfejsu użytkownika nadal wymagają ręcznego działania.
- `mdatp diagnostic real-time-protection-statistics` Teraz obsługuje dwa dodatkowe przełączniki:
  - `--sort`: sortuje dane wyjściowe w kolejności malejącej według łącznej liczby zeskanowanych plików.
  - `--top N`: wyświetla najważniejsze wyniki N (działa tylko wtedy, gdy `--sort` jest również określona)
- Ulepszenia wydajności & poprawki błędów

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Program Microsoft Defender for Endpoint dla systemu Linux jest teraz dostępny w wersji preview dla klientów z rządem Stanów Zjednoczonych. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych](gov.md).
- Rozwiązano problem, gdy użycie programu Microsoft Defender dla punktu końcowego w systemie Linux w systemach z PLIKAMI NIM BYŁO prowadzące do zawieszania się systemu operacyjnego
- Ulepszenia wydajności & innych poprawek błędów

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Ulepszenia wydajności & poprawki błędów

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Ulepszenie wydajności w sytuacji, gdy do listy wykluczeń oprogramowania antywirusowego jest dodawany cały punkt instalacji. Przed tą wersją działania dotyczące plików pochodzące z punktu instalacji nadal były przetwarzane przez produkt. Począwszy od tej wersji aktywność plików dla wykluczonych punktów instalacji jest pomijana, co prowadzi do lepszej wydajności produktu
- Dodano nową opcję do narzędzia wiersza polecenia w celu wyświetlania informacji o ostatnim skanie na żądanie. Aby wyświetlić informacje dotyczące ostatniego skanowania na żądanie, uruchom `mdatp health --details antivirus`
- Inne ulepszenia wydajności & poprawek błędów

## <a name="1011853"></a>101.18.53

- EDR dla Systemu Linux jest [teraz ogólnie dostępne](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Dodano nowy przełącznik wiersza polecenia (`--ignore-exclusions`), który umożliwia ignorowanie wykluczeń audio/wideo podczas skanowania niestandardowego (`mdatp scan custom`)
- Rozszerzona `mdatp diagnostic create` o nowy parametr (`--path [directory]`), który umożliwia zapisanie dzienników diagnostycznych w innym katalogu
- Ulepszenia wydajności & poprawki błędów

## <a name="1011299"></a>101.12.99

- Ulepszenia wydajności & poprawki błędów

## <a name="1010476"></a>101.04.76

- Poprawki błędów

## <a name="1010348"></a>101.03.48

- Poprawki błędów

## <a name="1010255"></a>101.02.55

- Rozwiązano problem, gdy produkt czasami nie rozpoczyna się po ponownym uruchomieniu / uaktualnieniu
- Rozwiązano problem, gdy ustawienia serwera proxy nie są zachowywane podczas uaktualnień produktu

## <a name="1010075"></a>101.00.75

- Dodano obsługę następujących typów systemów plików: `ecryptfs`, `fuse`, `fuseblk`, `jfs`, `nfs`, `overlay``ramfs`, `reiserfs`, `udf`i`vfat`
- Nowa składnia [narzędzia wiersza polecenia](linux-resources.md#configure-from-the-command-line).
- Ulepszenia wydajności & poprawki błędów

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Podczas uaktualniania zainstalowanego pakietu z wersji produktu wcześniejszej niż 100.90.70 aktualizacja może nie powieść się w przypadku dystrybucji opartych na systemie Red Hat i SLES. Wynika to z istotnej zmiany ścieżki pliku. Rozwiązaniem tymczasowym jest usunięcie starszego pakietu, a następnie zainstalowanie nowszego. Ten problem nie występuje w nowszej wersji.

- [Wykluczenia oprogramowania antywirusowego obsługują teraz symbole wieloznaczne](linux-exclusions.md#supported-exclusion-types)
- Dodano możliwość [rozwiązywania problemów z wydajnością](linux-support-perf.md) za pomocą `mdatp` narzędzia wiersza polecenia
- Ulepszenia usprawnień w zakresie instalowania pakietu
- Ulepszenia wydajności & poprawki błędów
