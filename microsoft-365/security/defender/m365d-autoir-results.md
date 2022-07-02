---
title: Szczegóły i wyniki zautomatyzowanego badania
description: Wyświetlanie wyników i kluczowych ustaleń zautomatyzowanego badania w Microsoft 365 Defender
keywords: zautomatyzowane, badanie, wyniki, analiza, szczegóły, korygowanie, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
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
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: cc53717feed347019540ffcb8c85687a6c28537f
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607482"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Szczegóły i wyniki zautomatyzowanego badania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

W przypadku Microsoft 365 Defender, gdy [uruchamiane jest zautomatyzowane badanie](m365d-autoir.md), szczegółowe informacje o tym badaniu są dostępne zarówno w trakcie, jak i po zautomatyzowanym procesie badania. Jeśli masz niezbędne uprawnienia, możesz wyświetlić te szczegóły w widoku [szczegółów](m365d-action-center.md#required-permissions-for-action-center-tasks) badania, który zapewnia aktualny stan i możliwość zatwierdzania wszelkich oczekujących akcji. 

## <a name="new-unified-investigation-page"></a>(NOWY) Strona ujednoliconego badania

Strona badania została niedawno zaktualizowana w celu uwzględnienia informacji na urządzeniach, w wiadomościach e-mail i zawartości współpracy. Nowa, ujednolicona strona badania definiuje wspólny język i zapewnia ujednolicone środowisko do automatycznego badania w [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) i [Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/defender-for-office-365.md). Aby uzyskać dostęp do ujednoliconej strony badania, wybierz link na żółtym banerze, który zobaczysz na stronie:

- Dowolna strona badania w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Centrum zgodności & zabezpieczeń Office 365</a>
- Dowolna strona badania w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))
- Dowolne środowisko zdarzenia lub centrum akcji w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>

## <a name="open-the-investigation-details-view"></a>Otwieranie widoku szczegółów badania

Widok szczegółów badania można otworzyć przy użyciu jednej z następujących metod:

- [Wybieranie elementu w centrum akcji](#select-an-item-in-the-action-center)
- [Wybieranie badania na stronie szczegółów zdarzenia](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Wybieranie elementu w centrum akcji

Ulepszone [centrum akcji](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) łączy [akcje korygowania](m365d-remediation-actions.md) na urządzeniach, pocztę e-mail & zawartość współpracy i tożsamości. Wymienione akcje obejmują akcje korygowania, które zostały wykonane automatycznie lub ręcznie. W Centrum akcji można wyświetlać akcje oczekujące na zatwierdzenie i akcje, które zostały już zatwierdzone lub ukończone. Możesz również przejść do dodatkowych szczegółów, takich jak strona badania.

> [!TIP]
> Musisz mieć [pewne uprawnienia](m365d-action-center.md#required-permissions-for-action-center-tasks) do zatwierdzania, odrzucania lub cofania akcji.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

3. Na karcie **Oczekujące** lub **Historia** wybierz element. Zostanie otwarte okienko wysuwane.

4. Przejrzyj informacje w okienku wysuwanego, a następnie wykonaj jedną z następujących czynności:
   - Wybierz **pozycję Otwórz stronę badania** , aby wyświetlić więcej szczegółów na temat badania.
   - Wybierz pozycję **Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz pozycję **Odrzuć** , aby zapobiec podjęciu oczekującej akcji.
   - Wybierz pozycję **Go hunt** ,aby przejść do [pozycji Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Otwieranie badania ze strony szczegółów zdarzenia

Użyj strony szczegółów zdarzenia, aby wyświetlić szczegółowe informacje o zdarzeniu, w tym alerty, które zostały wyzwolone informacje o wszystkich urządzeniach, kontach użytkowników lub skrzynkach pocztowych, których dotyczy problem.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Incydenty & alerty** > **Zdarzenia**. 

3. Wybierz element z listy, a następnie wybierz pozycję **Otwórz stronę zdarzenia**.

4. Wybierz kartę **Badania** , a następnie wybierz badanie na liście. Zostanie otwarte okienko wysuwane.

5. Wybierz pozycję **Otwórz stronę badania**. 

Oto przykład.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Strona badania w portalu Microsoft 365 Defender" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Szczegóły badania

Użyj widoku szczegółów badania, aby zobaczyć wcześniejsze, bieżące i oczekujące działania dotyczące badania. Oto przykład.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Strona szczegółów badania w portalu Microsoft 365 Defender" lightbox="../../media/mtp-air-investdetails.png":::

W widoku Szczegóły badania można wyświetlić informacje na kartach **Wykres badania**, **Alerty**, **Urządzenia**, **Tożsamości**, **Kluczowe wyniki, Jednostki**, **Dziennik** i **Oczekujące akcje** opisane w poniższej tabeli. 

> [!NOTE]
> Konkretne karty widoczne na stronie szczegółów badania zależą od subskrypcji. Jeśli na przykład subskrypcja nie zawiera Ochrona usługi Office 365 w usłudze Microsoft Defender planu 2, nie będzie widoczna karta **Skrzynki pocztowe**.

| Zakładka | Opis |
|:--------|:--------|
| **Wykres badania** | Zapewnia wizualną reprezentację badania. Przedstawia jednostki i wyświetla listę znalezionych zagrożeń wraz z alertami i informacją, czy jakiekolwiek akcje oczekują na zatwierdzenie.<br/>Możesz wybrać element na grafie, aby wyświetlić więcej szczegółów. Na przykład wybranie **ikony Dowody** spowoduje przejście do karty **Dowody** , gdzie można zobaczyć wykryte jednostki i ich werdykty. |
| **Alerty** | Wyświetla listę alertów skojarzonych z badaniem. Alerty mogą pochodzić z funkcji ochrony przed zagrożeniami na urządzeniu użytkownika, w aplikacjach pakietu Office, Microsoft Defender for Cloud Apps i innych funkcjach Microsoft 365 Defender. <br> <br> Pamiętaj, że jeśli widzisz *nieobsługiwany typ alertu*, oznacza to, że funkcje zautomatyzowanego badania nie mogą odebrać tego alertu w celu uruchomienia zautomatyzowanego badania. Można jednak [zbadać te alerty ręcznie](investigate-incidents.md#alerts).
| **Urządzeń** | Wyświetla listę urządzeń uwzględnionych w badaniu wraz z ich poziomem korygowania. (Poziomy korygowania odpowiadają [poziomowi automatyzacji dla grup urządzeń](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)). |
| **Skrzynek pocztowych** |Wyświetla listę skrzynek pocztowych, na które mają wpływ wykryte zagrożenia.  |
| **Użytkownicy**  | Wyświetla listę kont użytkowników, na które mają wpływ wykryte zagrożenia. |
| **Dowody** | Wyświetla listę dowodów zgłoszonych przez alerty lub dochodzenia. Zawiera werdykty (*złośliwe*, *podejrzane*, *nieznane* lub *nie znaleziono zagrożeń*) i stan korygowania. |
| **Podmioty** | Zawiera szczegółowe informacje o każdej analizowanej jednostce, w tym werdykt dla każdego typu jednostki (*Złośliwe*, *Podejrzane* lub *Nie znaleziono zagrożeń*).|
|**Dziennika** | Udostępnia chronologiczny, szczegółowy widok wszystkich akcji badania wykonanych po wyzwoleniu alertu.|
| **Historia oczekujących akcji** | Wyświetla listę elementów, które wymagają zatwierdzenia, aby kontynuować. Przejdź do centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), aby zatwierdzić oczekujące akcje. |

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
- [Dowiedz się więcej o akcjach korygowania](m365d-remediation-actions.md)
