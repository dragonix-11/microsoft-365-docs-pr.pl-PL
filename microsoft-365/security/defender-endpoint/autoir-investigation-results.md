---
title: Wyświetlanie szczegółów i wyników automatycznego badania
description: Podczas zautomatyzowanego badania i po jego zakończeniu można wyświetlać wyniki i kluczowe wyniki
keywords: zautomatyzowane, badania, wyniki, analizowanie, szczegóły, działania naprawcze, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
ms.openlocfilehash: 294722f3f79172e06752c5318bfef21dfc640eed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327633"
---
# <a name="view-the-details-and-results-of-an-automated-investigation"></a>Wyświetlanie szczegółów i wyników automatycznego badania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Dzięki programowi Microsoft Defender for Endpoint [po zakończeniu](automated-investigations.md) zautomatyzowanego badania szczegóły dotyczące tego badania są dostępne zarówno w trakcie, jak i po nim. Jeśli masz odpowiednie uprawnienia, możesz wyświetlić te szczegóły w widoku szczegółów badania. Widok szczegółów badania udostępnia aktualny stan i możliwość zatwierdzania wszystkich oczekujących akcji.

## <a name="new-unified-investigation-page"></a>(NOWOŚĆ!) Strona ujednoliconego badania

Strona badania została ostatnio zaktualizowana w celu dołączania informacji z różnych urządzeń, poczty e-mail i zawartości współpracy. Nowa, ujednolicona strona badania definiuje wspólny język i zapewnia ujednolicone środowisko dla automatycznego badania w programie [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) i [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp).

> [!TIP]
> Aby dowiedzieć się więcej o tym, co się zmienia, zobacz [(NOWY!) Ujednolicona strona badania](/microsoft-365/security/mtp/mtp-autoir-results).

## <a name="open-the-investigation-details-view"></a>Otwieranie widoku szczegółów badania

Widok szczegółów badania można otworzyć przy użyciu jednej z następujących metod:

- [Zaznaczanie elementu w Centrum akcji](#select-an-item-in-the-action-center)
- [Wybieranie badania na stronie szczegółów zdarzenia](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Zaznaczanie elementu w Centrum akcji

Ulepszone Centrum [akcji zapewnia](auto-investigation-action-center.md) [ze sobą akcje](manage-auto-investigation.md#remediation-actions) naprawcze na różnych urządzeniach, wiadomości e-mail & zawartość współpracy i tożsamości. Wymienione działania obejmują działania naprawcze, które zostały wykonane automatycznie lub ręcznie. W Centrum akcji możesz wyświetlić akcje oczekujące na zatwierdzenie oraz akcje, które zostały już zatwierdzone lub ukończone. Możesz również przejść do szczegółowych informacji, takich jak strona badania.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Wybierz element **na karcie Oczekiwanie** lub Historia. Zostanie otwarte okienko wysuwu.
4. Przejrzyj informacje w okienku wysuwu, a następnie zrób tak:
   - Wybierz **pozycję Otwórz stronę badania,** aby wyświetlić więcej szczegółów dotyczących badania.
   - Wybierz **pozycję Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz **pozycję Odrzuć** , aby zapobiec podejmowanej akcji oczekującej.
   - Wybierz **pozycję Przejdź wyszukiwania,** aby przejść do wyszukiwania [zaawansowanego](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Otwieranie badania ze strony szczegółów zdarzenia

Strona ze szczegółami zdarzenia umożliwia wyświetlenie szczegółowych informacji o zdarzeniu, w tym alertów wyzwalanych w związku z informacjami o wszelkich urządzeniach, kontach użytkowników lub skrzynkach pocztowych, których dotyczy problem.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Zdarzenia i & alerty** \> **Zdarzenia**.
3. Zaznacz element na liście, a następnie wybierz pozycję **Otwórz stronę zdarzenia**.
4. Wybierz **kartę Badania** , a następnie wybierz badanie z listy. Zostanie otwarte okienko wysuwu.
5. Wybierz **pozycję Otwórz stronę badania**.

## <a name="investigation-details"></a>Szczegóły badania

Widok szczegółów badania umożliwia wyświetlanie przeszłych, bieżących i oczekujących działań związanych z badaniem. Widok szczegółów badania przypomina poniższy obraz:

W widoku Szczegóły badania możesz wyświetlić informacje  na kartach Wykres **badania,** Alerty **, Urządzenia****,** **Tożsamości****, Ustalenia** **klucza,** Encje **, Dziennik** i Akcje oczekujące opisane w poniższej tabeli.

> [!NOTE]
> Konkretne karty, które widzisz na stronie szczegółów badania, zależą od tego, co obejmuje Twoja subskrypcja. Jeśli na przykład Twoja subskrypcja nie zawiera programu Microsoft Defender for Office 365 Plan 2, nie zobaczysz karty **Skrzynki** pocztowe.

|Tab|Opis|
|---|---|
|**Wykres badania**|Zapewnia wizualną reprezentację badania. Przedstawia znalezione jednostki i wyświetla znalezione zagrożenia oraz alerty oraz informacje o tym, czy jakieś działania oczekują na zatwierdzenie. <p> Możesz wybrać element na wykresie, aby wyświetlić więcej szczegółów. Na przykład **wybranie ikony Dowód** przenosi do karty Dowód, gdzie  można zobaczyć wykryte jednostki i ich werdykty.|
|**Alerty**|Wyświetla alerty skojarzone z badaniem. Alerty mogą pochodzić z funkcji ochrony przed zagrożeniami na urządzeniu użytkownika, w aplikacjach usługi Office, usłudze Defender dla aplikacji w chmurze i Microsoft 365 Defender funkcje.|
|**Urządzenia**|Zawiera listę urządzeń uwzględnionych w śledztwie wraz z ich poziomem rozwiązywania problemów. (Poziomy rozwiązywania problemów odpowiadają [poziomowi automatyzacji grup urządzeń](automation-levels.md)).|
|**Skrzynki pocztowe**|Zawiera listę skrzynek pocztowych, na które mają wpływ wykryte zagrożenia.|
|**Użytkownicy**|Lista kont użytkowników, na które mają wpływ wykryte zagrożenia.|
|**Dowód**|Lista dowodów podniesionych przez alerty/badania. Zawiera werdykty (*złośliwe**, podejrzane* lub Nie odnaleziono *zagrożeń*) i stan działań naprawczych.|
|**Jednostki**|Zawiera szczegółowe informacje na temat każdej analizowanej jednostki, w tym werdykt dla każdego typu encji (*złośliwe**, podejrzane* lub Nie znaleziono *zagrożeń*).|
|**Dziennik**|Udostępnia chronologiczny, szczegółowy widok wszystkich akcji badania, które zostały wykonane po wyzwoleniu alertu.|
|**Oczekujące akcje**|Lista elementów wymagających zatwierdzenia w celu kontynuowania. Przejdź do Centrum akcji (), aby<https://security.microsoft.com/action-center> zatwierdzić oczekujące akcje.|

## <a name="see-also"></a>Zobacz też

- [Przeglądanie działań naprawczych w przypadku zautomatyzowanego badania](manage-auto-investigation.md)
- [Wyświetlanie i organizowanie kolejki zdarzenia punktu końcowego programu Microsoft Defender](view-incidents-queue.md)
