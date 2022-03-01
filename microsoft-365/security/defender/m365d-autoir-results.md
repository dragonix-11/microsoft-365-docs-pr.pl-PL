---
title: Szczegóły i wyniki zautomatyzowanego badania
description: Wyświetlanie wyników i kluczowych wyników automatycznego badania w programie Microsoft 365 Defender
keywords: zautomatyzowane, badania, wyniki, analizowanie, szczegóły, działania naprawcze, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: e38de9e864fa063e3e56dc99c1d9c671b6409023
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033002"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Szczegóły i wyniki zautomatyzowanego badania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Dzięki Microsoft 365 Defender [po zakończeniu](m365d-autoir.md) automatycznego badania szczegóły dotyczące tego badania są dostępne zarówno w trakcie, jak i po nim. Jeśli [masz niezbędne uprawnienia](m365d-action-center.md#required-permissions-for-action-center-tasks), możesz wyświetlić te szczegóły w widoku szczegółów badania, który udostępnia aktualny stan i możliwość zatwierdzania wszystkich oczekujących akcji. 

## <a name="new-unified-investigation-page"></a>(NOWY) Strona ujednoliconego badania

Strona badania została ostatnio zaktualizowana w celu dołączania informacji z różnych urządzeń, poczty e-mail i zawartości współpracy. Nowa, ujednolicona strona badania definiuje wspólny język i zapewnia ujednolicone środowisko dla automatycznego badania w programie [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) i [Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md). Aby uzyskać dostęp do ujednoliconej strony badania, wybierz link na żółtym banerze, który będzie wyświetlony na:

- Dowolna strona badania w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Centrum Office 365 zabezpieczeń & zgodności</a>
- Dowolna strona badania w Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))
- Wszelkie zdarzenia i działania Centrum akcji w portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender zdarzeń</a>

## <a name="open-the-investigation-details-view"></a>Otwieranie widoku szczegółów badania

Widok szczegółów badania można otworzyć przy użyciu jednej z następujących metod:

- [Zaznaczanie elementu w Centrum akcji](#select-an-item-in-the-action-center)
- [Wybieranie badania na stronie szczegółów zdarzenia](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Zaznaczanie elementu w Centrum akcji

Ulepszone Centrum [akcji](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) łączy działania naprawcze na [](m365d-remediation-actions.md) różnych urządzeniach, wiadomości e-mail & zawartości współpracy i tożsamości. Wymienione działania obejmują działania naprawcze, które zostały wykonane automatycznie lub ręcznie. W Centrum akcji możesz wyświetlić akcje oczekujące na zatwierdzenie oraz akcje, które zostały już zatwierdzone lub ukończone. Możesz również przejść do szczegółowych informacji, takich jak strona badania.

> [!TIP]
> Musisz mieć pewne [uprawnienia do](m365d-action-center.md#required-permissions-for-action-center-tasks) zatwierdzania, odrzucania lub cofania akcji.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

3. Wybierz element **na karcie Oczekiwanie** lub Historia. Zostanie otwarte okienko wysuwu.

4. Przejrzyj informacje w okienku wysuwu, a następnie zrób tak:
   - Wybierz **pozycję Otwórz stronę badania,** aby wyświetlić więcej szczegółów dotyczących badania.
   - Wybierz **pozycję Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz **pozycję Odrzuć** , aby zapobiec podejmowanej akcji oczekującej.
   - Wybierz **pozycję Przejdź wyszukiwania,** aby przejść do wyszukiwania [zaawansowanego](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Otwieranie badania ze strony szczegółów zdarzenia

Strona ze szczegółami zdarzenia umożliwia wyświetlenie szczegółowych informacji o zdarzeniu, w tym alertów wyzwalanych w związku z informacjami o wszelkich urządzeniach, kontach użytkowników lub skrzynkach pocztowych, których dotyczy problem.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Zdarzenia & AlertyIncidentyfikaci** > . 

3. Zaznacz element na liście, a następnie wybierz pozycję **Otwórz stronę zdarzenia**.

4. Wybierz **kartę Badania** , a następnie wybierz badanie z listy. Zostanie otwarte okienko wysuwu.

5. Wybierz **pozycję Otwórz stronę badania**. 

Oto przykład.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Przykład strony badania." lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Szczegóły badania

Widok szczegółów badania umożliwia wyświetlanie przeszłych, bieżących i oczekujących działań związanych z badaniem. Oto przykład.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Przykład szczegółów badania." lightbox="../../media/mtp-air-investdetails.png":::

W widoku Szczegóły badania możesz wyświetlić informacje  na kartach Wykres **badania,** Alerty **, Urządzenia****,** **Tożsamości****, Ustalenia** **klucza,** Encje **, Dziennik** i Akcje oczekujące opisane w poniższej tabeli.

> [!NOTE]
> Konkretne karty, które widzisz na stronie szczegółów badania, zależą od tego, co obejmuje Twoja subskrypcja. Jeśli na przykład Twoja subskrypcja nie zawiera programu Microsoft Defender for Office 365 Plan 2, nie zobaczysz karty **Skrzynki** pocztowe.

| Tab | Opis |
|:--------|:--------|
| **Wykres badania** | Zapewnia wizualną reprezentację badania. Przedstawia znalezione jednostki i wyświetla znalezione zagrożenia oraz alerty oraz informacje o tym, czy jakieś działania oczekują na zatwierdzenie.<br/>Możesz wybrać element na wykresie, aby wyświetlić więcej szczegółów. Na przykład **wybranie ikony Dowód** przenosi do karty Dowód, gdzie  można zobaczyć wykryte jednostki i ich werdykty. |
| **Alerty** | Wyświetla alerty skojarzone z badaniem. Alerty mogą pochodzić z funkcji ochrony przed zagrożeniami na urządzeniu użytkownika, w Office aplikacji Microsoft Defender dla aplikacji w chmurze i innych Microsoft 365 Defender funkcje.|
| **Urządzenia** | Zawiera listę urządzeń uwzględnionych w śledztwie wraz z ich poziomem rozwiązywania problemów. (Poziomy rozwiązywania problemów odpowiadają [poziomowi automatyzacji grup urządzeń](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)). |
| **Skrzynki pocztowe** |Zawiera listę skrzynek pocztowych, na które mają wpływ wykryte zagrożenia.  |
| **Użytkownicy**  | Lista kont użytkowników, na które mają wpływ wykryte zagrożenia. |
| **Dowód** | Lista dowodów podniesionych w wyniku alertów lub badań. Zawiera werdykty (*złośliwe**, podejrzane**, nieznane* lub *nie* odnalezione zagrożeń) oraz stan rozwiązywania problemów. |
| **Jednostki** | Zawiera szczegółowe informacje na temat każdej analizowanej jednostki, w tym werdykt dla każdego typu encji (*złośliwe**, podejrzane* lub Nie znaleziono *zagrożeń*).|
|**Dziennik** | Udostępnia chronologiczny, szczegółowy widok wszystkich akcji badania, które zostały wykonane po wyzwoleniu alertu.|
| **Historia oczekujących akcji** | Lista elementów wymagających zatwierdzenia w celu kontynuowania. Przejdź do Centrum akcji (), aby[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) zatwierdzić oczekujące akcje. |

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
- [Dowiedz się więcej o działaniach naprawczych](m365d-remediation-actions.md)
