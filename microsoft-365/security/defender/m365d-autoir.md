---
title: Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender
description: Uzyskaj przegląd zautomatyzowanych możliwości badania i reagowania, nazywanych także samooceną, w programie Microsoft 365 Defender
keywords: zautomatyzowane, badania, alert, wyzwalacz, akcja, działania naprawcze, samoocena
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 180599007a47fe9cfa9ae68d6647f7494dd2f410
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314269"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Jeśli Twoja organizacja używa programu [Microsoft 365 Defender](microsoft-365-defender.md), zespół operacji zabezpieczeń otrzymuje w portalu programu Microsoft 365 Defender alert po wykryciu złośliwego lub podejrzanego działania lub artefaktu. Mając do czynienia z pozornie nigdy niekończeniem przepływem zagrożeń, które mogą się pojawiać, zespoły zabezpieczeń często wyzwanie związane z rozwiązywaniem problemu związanego z dużą ilością alertów. Na szczęście Microsoft 365 Defender funkcje automatycznego badania i odpowiedzi (AIR), które mogą ułatwić zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze reagowanie na zagrożenia.

Ten artykuł zawiera omówienie funkcji AIR oraz linki do następnych kroków i dodatkowych zasobów.

> [!TIP]
> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).

## <a name="how-automated-investigation-and-self-healing-works"></a>Jak działa automatyczne badania i samoocena

W związku z wyzwoleniem alertów zabezpieczeń zespół operacyjny zabezpieczeń musi przyjrzeć się tym alertom i podjąć odpowiednie kroki w celu ochrony organizacji. Ustalanie priorytetów i badanie alertów może być bardzo czasochłonne, szczególnie wtedy, gdy w trakcie badania są nadal przychodzi nowe alerty. Zespoły ds. operacji zabezpieczeń mogą być przytłoczone dużą ilości zagrożeń, które muszą monitorować i chronić przed. Automatyczne badania i odpowiedzi z własnymi możliwościami w zakresie Microsoft 365 Defender mogą pomóc.

Obejrzyj poniższy klip wideo, aby dowiedzieć się, jak działa samodzielna praca: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

W Microsoft 365 Defender, automatyczne badanie i reagowanie dzięki możliwościom samooceny na różnych urządzeniach, w wiadomościach e-mail & zawartości i tożsamości.
 
> [!TIP]
> W tym artykule opisano działanie automatycznego badania i odpowiedzi. Aby skonfigurować te funkcje, zobacz [Konfigurowanie funkcji automatycznego badania i odpowiedzi w programie Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Twój własny wirtualny analityk

Imagine w zespole operacji zabezpieczeń warstwy 1 lub 2 wirtualnego analityka. Wirtualny analityk naśladuje idealne kroki, jakie mogą podjąć operacje zabezpieczeń w celu zbadania i rozwiązania problemów związanych z zagrożeniami. Wirtualny analityk może pracować przez całą 7 dni w tygodniu, bez ograniczeń, a także brać udział w istotnych badaniach i rozwiązywaniu zagrożeń. Taki wirtualny analityk może znacznie skrócić czas reakcji, aby twój zespół operacji zabezpieczeń mógł uwolnić się od innych ważnych zagrożeń lub projektów strategicznych. Jeśli ten scenariusz brzmi jak science fiction, to nie wszystko! Taki wirtualny analityk jest częścią pakietu Microsoft 365 Defender, a jego nazwa to *zautomatyzowane badanie i odpowiedź*.

Automatyczne badanie i reagowanie umożliwia Twojemu zespołowi operacyjnemu ds. zabezpieczeń znaczne zwiększenie możliwości organizacji w zakresie postępowania z alertami zabezpieczeń i zdarzeniami. Dzięki zautomatyzowanym testom i odpowiedziom możesz zmniejszyć koszty związane z działaniami analizy i odpowiedzi oraz w pełni korzystać z pakietu ochrony przed zagrożeniami. Funkcje automatycznego badania i reagowania pomagają zespołowi ds. bezpieczeństwa:

1. Określanie, czy zagrożenie wymaga działania.
2. Podejmowanie (lub polecanie) wszelkich niezbędnych działań naprawczych.
3. Określanie, czy i jakie inne badania powinny zostać prowadzone.
4. W razie potrzeby powtórz tę procedurę dla innych alertów.

## <a name="the-automated-investigation-process"></a>Proces zautomatyzowanego badania

Alert tworzy zdarzenie, które może rozpocząć zautomatyzowane badanie. Zautomatyzowane badanie powoduje werdykt każdego dowodu. Werdykty mogą być:
- *Złośliwy*
- *Podejrzane* 
- *Nie znaleziono zagrożeń* 

Działania naprawcze dotyczące złośliwych lub podejrzanych obiektów są identyfikowane. Przykłady działań naprawczych są następujące:

- Wysyłanie pliku do kwarantanny
- Zatrzymywanie procesu
- Odizolowanie urządzenia
- Blokowanie adresu URL 
- Inne akcje

Aby uzyskać więcej informacji, zobacz Działania [naprawcze w programie Microsoft 365 Defender](m365d-remediation-actions.md).

W zależności [od tego,](m365d-configure-auto-investigation-response.md) jak są skonfigurowane funkcje automatycznego badania i reakcji dla organizacji, działania naprawcze są podejmowane automatycznie lub tylko po zatwierdzeniu ich przez zespół operacyjny ds. zabezpieczeń. Wszystkie akcje, zarówno oczekujące, jak i ukończone, są wyświetlane w [Centrum akcji](m365d-action-center.md).

Gdy jest uruchomione badanie, wszelkie inne powiązane alerty, które się pojawią, są dodawane do badania do momentu jego zakończenia. Jeśli obiekt, którego dotyczy problem, jest widoczny w innym miejscu, automatyczne badanie rozszerza zakres, tak aby uwzględnić tę jednostkę, i proces badania jest powtarzany. 

W Microsoft 365 Defender każdym zautomatyzowanym śledztwu skorelowane są sygnały w usługach Microsoft Defender for Identity, Microsoft Defender for Endpoint i Microsoft Defender for Office 365, jak podsumowano w poniższej tabeli: 

|Jednostki |Usługi ochrony przed zagrożeniami  |
|:---------|:---------|
|Urządzenia (nazywane również punktami końcowymi lub komputerami) |[Defender for Endpoint](../defender-endpoint/automated-investigations.md) |      
|Lokalni użytkownicy usługi Active Directory, zachowanie jednostki i działania     |[Defender for Identity](/azure-advanced-threat-protection/what-is-atp) |      
|Zawartość wiadomości e-mail (wiadomości e-mail, które mogą zawierać pliki i adresy URL)     |[Defender for Office 365](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Nie każdy alert powoduje uruchomienie zautomatyzowanego badania, a nie wszystkie wyniki badania powodują automatyczne działania naprawcze. Zależy to od konfiguracji automatycznego badania i odpowiedzi dla organizacji. Zobacz [Konfigurowanie funkcji automatycznego badania i odpowiedzi](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Wyświetlanie listy badań

Aby wyświetlić badania, przejdź do **strony Zdarzenia** . Wybierz zdarzenie, a następnie wybierz **kartę Badania** . Aby dowiedzieć się więcej, [zobacz Szczegóły i wyniki automatycznego badania](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Szkolenie dla analityków zabezpieczeń

Skorzystaj z tego modułu szkoleniowego firmy Microsoft Learn, aby dowiedzieć się, Microsoft 365 Defender w celu samodzielnej obsługi badania i reagowania na incydenty.

|Szkolenie:|Automatyzowanie samodzielnej pracy za pomocą Microsoft 365 Defender|
|---|---|
|![Zautomatyzuj samodzielną samodzielnie Microsoft 365 Defender ikonę szkolenia.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender korzysta ze swojej sieci WI w celu zautomatyzowania działań naprawczych w przypadku zdarzeń, co ułatwia zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze rozwiązywanie problemów. <p> 11 min – 5 jednostek |

> [!div class="nextstepaction"]
> [Rozpoczynanie >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Następne kroki

- [Zobacz wymagania wstępne dotyczące automatycznego badania i odpowiedzi](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Konfigurowanie automatycznego badania i reagowania na nie w organizacji](m365d-configure-auto-investigation-response.md)
- [Dowiedz się więcej o Centrum akcji](m365d-action-center.md)
