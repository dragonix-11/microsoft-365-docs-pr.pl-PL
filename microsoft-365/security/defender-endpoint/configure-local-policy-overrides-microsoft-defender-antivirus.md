---
title: Konfigurowanie zastępowania lokalnego Program antywirusowy Microsoft Defender ustawień
description: Włącz lub wyłącz możliwość lokalnego zmieniania ustawień przez użytkowników w programie Microsoft Defender AV.
keywords: zastępowanie lokalne, zasady lokalne, zasady grupy, gpo, blokowanie, scalanie, listy
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: ec916b008ddb3e0669111efe2bd493c709327296
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997359"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie Program antywirusowy Microsoft Defender zasad


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Domyślnie ustawienia Program antywirusowy Microsoft Defender, które są wdrożone za pośrednictwem obiektu zasady grupy na punkty końcowe w Sieci, uniemożliwiają użytkownikom lokalną zmianę ustawień. W niektórych przypadkach można to zmienić.

Na przykład może być konieczne zezwolić określonym grupom użytkowników (na przykład na na przykład na dostęp do zabezpieczeń i na dostęp do zagrożeń) na dalszą kontrolę nad poszczególnymi ustawieniami dla poszczególnych punktów końcowych, z których korzystają.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Konfigurowanie zastępowania lokalnego Program antywirusowy Microsoft Defender ustawień

Ustawieniem domyślnym tych zasad jest **Wyłączone**.

Jeśli użytkownik ma ustawioną **wartość Włączone**, użytkownicy korzystający z punktów końcowych mogą wprowadzać zmiany w skojarzonym ustawieniu z aplikacją Zabezpieczenia Windows, ustawieniami lokalnymi programu [zasady grupy](microsoft-defender-security-center-antivirus.md) i poleceniami cmdlet programu PowerShell (jeśli to konieczne).

W poniższej tabeli wymieniono każde z ustawień zasad zastępowania oraz instrukcje konfiguracji skojarzonej funkcji lub ustawienia.

Aby skonfigurować te ustawienia:

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki** >  **Program antywirusowy Microsoft Defender** a następnie pozycję **Lokalizacja** określona w tabeli ustawień (w tym artykule).

4. Kliknij dwukrotnie ustawienie **zasad określone** w poniższej tabeli i ustaw odpowiednią konfigurację. Kliknij **przycisk OK** i powtórz te czynności dla innych ustawień.

5. Wdeksuj zasady grupy Obiekt w zwykły sposób.

## <a name="table-of-settings"></a>Tabela ustawień

<br/><br/>

| Lokalizacja | Ustawienie | Artykuł |
|---|---|---|---|
| MAPY |Konfigurowanie zastępowania ustawień lokalnych na poziomie raportowania w aplikacji Microsoft MAPS|[Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Kwarantanna|Konfigurowanie zastępowania ustawień lokalnych w celu usunięcia elementów z folderu kwarantanny|[Konfigurowanie działań naprawczych dla skanów](configure-remediation-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych pod celu monitorowania aktywności plików i programów na komputerze|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu monitorowania przychodzącej i wychodzącej aktywności plików | [Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu skanowania wszystkich pobranych plików i załączników|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu włączeń monitorowania zachowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastępowania ustawień lokalnych w celu włączoną ochronę w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender i monitorowanie](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Działania naprawcze|Konfigurowanie zastępowania ustawień lokalnych na czas dnia w celu uruchomienia zaplanowanego pełnego skanowania w celu ukończenia działań naprawczych|[Konfigurowanie działań naprawczych dla skanów](configure-remediation-microsoft-defender-antivirus.md) |
| Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla maksymalnego procentu użycia procesora|[Konfigurowanie i uruchamianie skanów](run-scan-microsoft-defender-antivirus.md) |
| Skanowanie|Konfigurowanie zastępowania ustawień lokalnych na dzień skanowania harmonogramu|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla zaplanowanego szybkiego skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowanie|Konfigurowanie zastępowania ustawień lokalnych dla zaplanowanego czasu skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowanie|Konfigurowanie zastępowania lokalnego typu skanowania na czas zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Konfigurowanie scalania list korygowania i wykluczeń zdefiniowanych lokalnie i globalnie

Możesz również skonfigurować łączenie lub scalanie list zdefiniowanych lokalnie z listami zdefiniowanymi globalnie. To ustawienie dotyczy list [wykluczeń](configure-exclusions-microsoft-defender-antivirus.md), [określonych list środków zaradczych](configure-remediation-microsoft-defender-antivirus.md) i [zmniejszenia powierzchni ataków](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Domyślnie listy skonfigurowane w lokalnych zasadach grupy i aplikacji Zabezpieczenia Windows są scalane z listami zdefiniowanymi przez odpowiedni obiekt programu zasady grupy wdrożony w sieci. W przypadku konfliktów lista zdefiniowana globalnie ma pierwszeństwo.

Możesz wyłączyć to ustawienie, aby mieć pewność, że będą używane tylko listy zdefiniowane globalnie (na przykład listy z dowolnego wdrożonego gpos).

### <a name="use-group-policy-to-disable-local-list-merging"></a>Wyłączanie scalania list lokalnych za pomocą funkcji zasady grupy

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender**.

4. Kliknij dwukrotnie **pozycję Konfiguruj zachowanie scalania administratora lokalnego dla list** i ustaw dla opcji wartość **Wyłączone**. Kliknij przycisk **OK**.

> [!NOTE]
> Jeśli wyłączysz scalanie listy lokalnej, zastąpi ono kontrolowane ustawienia dostępu do folderu. Zastępuje ono także wszelkie chronione foldery i dozwolone aplikacje ustawione przez administratora lokalnego. Aby uzyskać więcej informacji na temat ustawień kontrolowanego dostępu do folderu, zobacz [Zezwalanie na dostęp](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security) do zablokowanej aplikacji Zabezpieczenia Windows.

## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurowanie interakcji użytkownika końcowego z Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
