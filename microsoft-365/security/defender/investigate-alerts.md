---
title: Badanie alertów w programie Microsoft 365 Defender
description: Badanie alertów widzianych na różnych urządzeniach, użytkownikach i skrzynkach pocztowych.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
ms.prod: m365-security
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: cfa39ca38046c131de2531b4ad6446626895090f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015388"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Badanie alertów w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Alerty są podstawą wszystkich zdarzeń i wskazują na wystąpienie złośliwych lub podejrzanych zdarzeń w Twoim środowisku. Alerty są zazwyczaj częścią szerszego ataku i zawierają wskazówki dotyczące zdarzenia.

W Microsoft 365 Defender powiązanych ze sobą alertów są agregowane w celu [formowania zdarzeń](incidents-overview.md). Zdarzenia zawsze zapewniają szerszy kontekst ataków, jednak analizowanie alertów może być przydatne, gdy jest wymagana bardziej dogłębna analiza. 

**Kolejka alertów** zawiera bieżący zestaw alertów. Do kolejki alertów można dostać się z menu Zdarzenia **& alerty > alerty** na pasku Szybkie uruchamianie Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">w witrynie.</a>

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Przykład kolejki alertów w portalu Microsoft 365 Defender wiadomości.":::

Alerty z różnych rozwiązań zabezpieczeń firmy Microsoft, takich jak Microsoft Defender for Endpoint, Microsoft Defender for Office 365 i Microsoft 365 Defender są wyświetlane tutaj.

Domyślnie w kolejce alertów w portalu Microsoft 365 Defender są wyświetlane nowe alerty w toku z ostatnich 30 dni. Najnowszy alert znajduje się u góry listy, więc jest on najpierw wyświetlony. 

W domyślnej kolejce alertów możesz wybrać  pozycję Filtruj, aby wyświetlić okienko **Filtr**, w którym możesz określić podzestaw alertów. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Example of the filters pane for the alerts queue in the Microsoft 365 Defender portal.":::

Alerty można filtrować według tych kryteriów:

- Ważność
- Stan
- Źródła usług
- Jednostki (mają wpływ środki trwałe)
- Stan zautomatyzowanego badania

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Role wymagane dla usługi Defender dla Office 365 alertów

Aby uzyskać dostęp do usługi Microsoft Defender na potrzeby alertów, musisz mieć dowolną z następujących Office 365 alertów:

- W Azure Active Directory globalnej usługi Azure AD:

   - Administrator globalny

   - Administrator zabezpieczeń

   - Operator zabezpieczeń

   - Czytnik globalny

   - Czytnik zabezpieczeń

- Office 365 ról & zabezpieczeń i zgodności

   - Administrator zgodności

   - Zarządzanie organizacją 

- Rola [niestandardowa](custom-roles.md)

## <a name="analyze-an-alert"></a>Analizowanie alertu

Aby wyświetlić stronę alertu głównego, wybierz nazwę alertu. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Przykład strony szczegółów alertu w portalu Microsoft 365 Defender sieci Web.":::

Możesz również wybrać akcję **Otwórz stronę alertu głównego** w **okienku Zarządzanie alertami** .

Strona alertu składa się z tych sekcji: 

- Alert, który jest łańcuchem zdarzeń i alertów związanych z tym alertem w porządku chronologicznym
- Szczegóły podsumowania

Na stronie alertu możesz wybrać wielokropek (**...**) obok dowolnej jednostki, aby wyświetlić dostępne akcje, takie jak otwarcie strony alertu lub połączenie alertu z innym zdarzeniem.

### <a name="alert-sources"></a>Źródła alertów

Microsoft 365 Defender alerty mogą pochodzić z rozwiązań, takich jak Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps oraz dodatek do zarządzania aplikacjami dla programu Microsoft Defender dla aplikacji w chmurze. Możesz zauważyć alerty ze wstępnie wpisanym znakiem. W poniższej tabeli podajemy wskazówki, które ułatwiają zrozumienie mapowania źródeł alertów na podstawie znaku, który przed alertem został wpisowany.

> [!NOTE]
> - Wstępnie określone identyfikatory GUID są specyficzne tylko dla ujednoliconych funkcji, takich jak ujednolicona kolejka alertów, strona ujednoliconych alertów, ujednolicone badanie i ujednolicone zdarzenie.
> - Znak, który wstępnie został wpisowany, nie zmienia identyfikatora GUID alertu. Jedyną zmianą identyfikatora GUID jest składnik, który go zawiera.

| Źródło alertu | Znak ze znakiem przedimka |
| :---|:--- |
| Usługa Microsoft Defender dla Office 365 | `fa{GUID}` <br> Przykład: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Ochrona punktu końcowego w usłudze Microsoft Defender | `da` lub niestandardowe `ed` alerty wykrywania <br> |
| Microsoft Defender for Identity | `aa{GUID}` <br> Przykład: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Usługa Microsoft Defender dla aplikacji w chmurze |`ca{GUID}` <br> Przykład: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analizowanie zasobów, których dotyczy problem

Sekcja **Akcje wykonane** zawiera listę zasobów, których dotyczy problem, takich jak skrzynki pocztowe, urządzenia i użytkownicy, których dotyczy ten alert. 

Możesz również wybrać pozycję **Wyświetl w Centrum akcji,** aby wyświetlić **kartę** Historia Centrum  akcji w portalu Microsoft 365 Defender akcji. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Śledzenie roli alertu w historii alertu

W historii alertu są wyświetlane wszystkie zasoby lub jednostki powiązane z alertem w widoku drzewa procesu. Alert w tytule to alert, który znajduje się na stronie wybranego alertu po raz pierwszy. Zasoby w historii alertu można rozwijać i klikać. Zapewniają one dodatkowe informacje i przyspieszają reakcję, umożliwiając ci działanie bezpośrednio w kontekście strony alertów. 

> [!NOTE]
> Sekcja artykułu alertu może zawierać więcej niż jeden alert, a dodatkowe alerty dotyczące tego samego drzewa wykonywania pojawiają się przed wybranym alertem lub po nim.

### <a name="view-more-alert-information-on-the-details-page"></a>Wyświetlanie dodatkowych informacji alertów na stronie szczegółów

Strona szczegółów zawiera szczegóły wybranego alertu wraz ze szczegółami i działaniami z nim związanych. Jeśli w wątku alertu wybierzesz dowolny z zasobów lub jednostek, których dotyczy problem, strona szczegółów zmieni się, aby udostępnić informacje kontekstowe i akcje dla wybranego obiektu.

Po wybraniu encji, która ma być zainteresowana, strona szczegółów zmienia się, aby wyświetlić informacje o wybranym typie encji, informacje historyczne, gdy jest dostępna, oraz opcje działania na tej encji bezpośrednio ze strony alertu.

## <a name="manage-alerts"></a>Zarządzanie alertami

Aby zarządzać alertem, wybierz alert w kolejce alertów w jego wierszu, aby wyświetlić **okienko Zarządzanie alertami** . Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Przykład okienka podsumowania dla alertu w portalu Microsoft 365 Defender wiadomości.":::

Okienko **zarządzanie alertami** umożliwia wyświetlanie i określanie:

- Stan alertu (Nowy, Rozwiązany, W toku).
- Konto użytkownika, do których przypisano alert.
- Klasyfikacja alertu (nie ustawiono, alert Prawda, alert fałsz).
- Dla klasyfikacji jako prawdziwego alertu typ zagrożenia dla alertu w polu **Wyznaczanie** .
- Komentarz alertu.

> [!NOTE]
> Jednym ze sposobów zarządzania alertami dzięki użyciu tagów. Funkcja otagowania dla programu Microsoft Defender Office 365 jest stopniowo wdawana i jest obecnie w wersji Zapoznawczej. <br>
> Obecnie zmodyfikowane nazwy tagów są stosowane tylko do alertów *utworzonych po* aktualizacji. Alerty wygenerowane przed modyfikacją nie będą odzwierciedlać zaktualizowanej nazwy tagu. 

W tym okienku możesz również wykonać następujące dodatkowe czynności: 

- Otwarcie strony alertu głównego
- Skonsultuj się z ekspertem ds. zagrożeń firmy Microsoft
- Wyświetl przesyłanie
- Link do innego zdarzenia
- Wyświetlanie alertu na osi czasu
- Tworzenie reguły reguły reguły reguły

Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-actions.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-actions.png" alt-text="Przykładowe akcje dotyczące alertu w Microsoft 365 Defender w programie":::

Lista dodatkowych akcji zależy od typu alertu.

## <a name="resolve-an-alert"></a>Rozwiązywanie alertu

Po zakończeniu analizowania alertu, który można rozwiązać, przejdź do okienka **Zarządzanie alertem** i oznacz stan jako Rozwiązany i sklasyfikuj go jako **alert** o wartości Fałsz lub **Prawda**. Dla prawdziwych alertów określ typ zagrożenia dla alertu w polu **Wyznaczanie** .

Klasyfikowanie alertów i określanie ich określania ułatwia dostosowywanie Microsoft 365 Defender w celu zapewnienia bardziej prawdziwych alertów i mniej fałszywych alertów.

## <a name="use-power-automate-to-triage-alerts"></a>Używanie Power Automate do ujednania alertów

Nowoczesne zespoły ds. zabezpieczeń (SecOps) wymagają automatyzacji, aby efektywnie pracować. Aby skupić się na chłoowaniu i badaniu rzeczywistych zagrożeń, zespoły secopsów używają Power Automate do sprawdzania listy alertów i eliminowania tych, które nie są zagrożeniami.  

### <a name="criteria-for-resolving-alerts"></a>Kryteria rozwiązywania alertów

- Włączona wiadomość o biurze dla użytkownika

- Użytkownik nie jest otagowany jako użytkownik o wysokim poziomie ryzyka

Jeśli oba te oznaczenia są prawdziwe, program SecOps oznacza alert jako legalną podróż i rozwiązuje go. Po rozpoznaniu alertu Microsoft Teams powiadomienie jest publikowane w tym programie.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Połączenie Power Automate do programu Microsoft Defender dla aplikacji w chmurze

Aby utworzyć automatyzację, potrzebujesz tokenu API, aby można było połączyć Power Automate usługą Microsoft Defender dla aplikacji w chmurze.

1. Kliknij **Ustawienia**, wybierz pozycję **Rozszerzenia zabezpieczeń**, a następnie kliknij pozycję **Dodaj token** na karcie **Tokeny API**.

2. Podaj nazwę tokenu, a następnie kliknij pozycję **Generuj**. Zapisz token, ponieważ będzie potrzebny później.

### <a name="create-an-automated-flow"></a>Tworzenie zautomatyzowanego przepływu

Aby uzyskać szczegółowy opis procesu krok po kroku, zobacz klip wideo [tutaj](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

W tym klipie wideo opisano również, jak połączyć zasilanie z programem Defender dla aplikacji w chmurze.

## <a name="next-steps"></a>Następne kroki

W razie potrzeby w przypadku zdarzeń w trakcie procesu kontynuuj [badanie](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
