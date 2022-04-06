---
title: Szczegółowe informacje na pulpicie nawigacyjnym — Zarządzanie zagrożeniami i lukami
description: Pulpit Zarządzanie zagrożeniami i lukami może ułatwić secopom i administratorom zabezpieczeń zająć się zagrożeniami bezpieczeństwa i zwiększyć odporność ich organizacji na zagrożenia bezpieczeństwa.
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender-tvm, Ochrona punktu końcowego w usłudze Microsoft Defender-tvm, zagrożenia & zarządzanie lukami w zabezpieczeniach, Zarządzanie zagrożeniami i lukami, informacje o ryzyku związane z & zarządzanie lukami w zabezpieczeniach, konfiguracja zabezpieczeń, wynik bezpiecznego zabezpieczenia firmy Microsoft dla urządzeń, wynik ochrony przed zagrożeniami
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
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 76eedd78e6bc6a95450a50c04d4f85b0de46db8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472490"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>Szczegółowe informacje na pulpicie nawigacyjnym — Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Zagrożenie i zarządzanie lukami w zabezpieczeniach to składnik usługi Defender for Endpoint, który zapewnia administratorom zabezpieczeń i zespołom operacji zabezpieczeń unikatową wartość, w tym:

- Analizy w czasie rzeczywistym wykrywanie i reagowanie w punktach końcowych (EDR) skorelowane z lukami w punktach końcowych
- Nieocenieniowy kontekst luki w zabezpieczeniach urządzenia podczas badania zdarzeń
- Wbudowane procesy rozwiązywania problemów za pośrednictwem Microsoft Intune i Microsoft Endpoint Configuration Manager

Funkcja Zarządzanie zagrożeniami i lukami portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">w celu</a>:

- Wyświetl ocenę ekspozycji i bezpiecznego wyniku działania firmy Microsoft dla urządzeń, a także najważniejsze zalecenia dotyczące zabezpieczeń, luki w zabezpieczeniach, działania naprawcze i ujawnione urządzenia
- Skoreluj EDR z lukami w punktach końcowych i przetwarzaj je
- Wybieranie opcji rozwiązywania problemów w celu  informacje o zadaniach rozwiązywania problemów i śledzenia ich
- Wybieranie opcji wyjątków i śledzenie aktywnych wyjątków

> [!NOTE]
> Urządzenia, które nie są aktywne w ciągu ostatnich 30 dni, nie są wniesiene do danych, które odzwierciedlają Zarządzanie zagrożeniami i lukami organizacji oraz wynik bezpiecznego dostępu do urządzeń firmy Microsoft.

Obejrzyj ten klip wideo, aby szybko o tym, co znajduje się na Zarządzanie zagrożeniami i lukami nawigacyjnym.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>Zagrożenia i zarządzanie lukami w zabezpieczeniach nawigacyjny

:::image type="content" source="../../media/tvmdashboard.png" alt-text="Pulpit nawigacyjny zarządzania zagrożeniami i lukami w zabezpieczeniach dla urządzeń" lightbox="../../media/tvmdashboard.png":::

<br>

****

|Obszar|Opis|
|---|---|
|**Wybrane grupy urządzeń (#/#)**|Filtruj Zarządzanie zagrożeniami i lukami, które chcesz wyświetlić na pulpicie nawigacyjnym, i na kartach według grup urządzeń. To, co wybierzesz w filtrze, dotyczy Zarządzanie zagrożeniami i lukami stron.|
|[**Wynik ekspozycji**](tvm-exposure-score.md)|Sprawdź bieżący stan zagrożenia i luki w zabezpieczeniach urządzenia w Twojej organizacji. Na ocenę ekspozycji w organizacji wpływa kilka czynników: wady wykryte na Twoich urządzeniach, prawdopodobieństwo naruszenia zabezpieczeń Twoich urządzeń, wartość urządzeń w Organizacji i właściwe alerty wykryte na Twoich urządzeniach. Celem jest zmniejszenie oceny ekspozycji w organizacji, aby zapewnić większe bezpieczeństwo. Aby zmniejszyć wynik, należy rozwiązać związane z tym problemy z konfiguracją zabezpieczeń wymienione w zaleceniach dotyczących zabezpieczeń.|
|[**Microsoft Secure Score dla urządzeń**](tvm-microsoft-secure-score-devices.md)|Sprawdź, jak działa system operacyjny, aplikacje, sieć, konta i mechanizmy kontroli zabezpieczeń Twojej organizacji. Celem jest rozwiązywanie związanych z tym problemów z konfiguracją zabezpieczeń, aby zwiększyć wynik dla urządzeń. Wybranie pasków spowoduje wybranie strony **zalecenia zabezpieczeń** .|
|**Rozkład ekspozycji na urządzenie**|Sprawdź, ile urządzeń jest ujawnionych na podstawie ich poziomu ekspozycji. Wybierz sekcję na wykresie pierścieniowym, aby przejść do strony  listy Urządzenia i wyświetlić nazwy urządzeń, poziom ekspozycji, poziom ryzyka i inne szczegóły, takie jak domena, platforma systemu operacyjnego, stan kondycji urządzenia i jego znaczniki.|
|**Najważniejsze zalecenia dotyczące zabezpieczeń**|Zapoznaj się z posortowaną zaleceniami o zabezpieczeniach, które są sortowane i priorytetyzowane na podstawie ryzyka i pilności twojej organizacji, jakie są jej wymagane. Wybierz **pozycję Pokaż więcej** , aby wyświetlić pozostałe zalecenia dotyczące zabezpieczeń na liście. Wybierz **pozycję Pokaż wyjątki** dla listy zaleceń, dla których występuje wyjątek.|
|**Oprogramowanie, które jest najbardziej narażone na zagrożenia**|Uzyskaj wgląd w stan oprogramowania organizacji w czasie rzeczywistym dzięki sklasyfikowanej w stosie liście narażonych na oprogramowanie zainstalowanych na urządzeniach sieciowych i wpływie tych czynników na wynik działania organizacji. Wybierz element, aby uzyskać szczegółowe informacje, lub pozycję **Pokaż więcej** , aby wyświetlić pozostałą część listy oprogramowania, która jest podatna na stronie **Spis** oprogramowania.|
|**Najważniejsze działania naprawcze**|Śledzenie działań naprawczych generowanych na podstawie zaleceń dotyczących zabezpieczeń. Możesz wybrać każdy element na liście, aby wyświetlić szczegóły na stronie Działania naprawcze, lub wybrać pozycję Pokaż  więcej, aby wyświetlić pozostałe działania naprawcze i aktywne wyjątki.|
|**Najlepiej widoczne urządzenia**|Wyświetlaj dostępne nazwy urządzeń i ich poziom ekspozycji. Wybierz nazwę urządzenia z listy, aby przejść do strony urządzenia, na której możesz wyświetlać alerty, zagrożenia, zdarzenia, zalecenia dotyczące zabezpieczeń, zainstalowane oprogramowanie oraz wykryć luki w zabezpieczeniach związane z dostępnymi urządzeniami. Wybierz **pozycję Pokaż więcej** , aby wyświetlić pozostałą część listy dostępnych urządzeń. Z listy urządzeń możesz zarządzać tagami, inicjować zautomatyzowane badania, rozpoczynać sesję odpowiedzi na żywo, zbierać pakiet badania, uruchamiać skanowanie antywirusowe, ograniczać wykonywanie aplikacji i izolować urządzenie.|
|

Aby uzyskać więcej informacji na temat ikon używanych w całym portalu, zobacz Ochrona punktu końcowego w usłudze Microsoft Defender [ikony](portal-overview.md#microsoft-defender-for-endpoint-icons).

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Wynik ekspozycji](tvm-exposure-score.md)
- [Microsoft Secure Score dla urządzeń](tvm-microsoft-secure-score-devices.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
- [Spis oprogramowania](tvm-software-inventory.md)
- [Oś czasu zdarzenia](threat-and-vuln-mgt-event-timeline.md)
