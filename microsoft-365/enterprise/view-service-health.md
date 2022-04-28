---
title: Jak sprawdzić kondycję usługi Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Przed wywołaniem pomocy technicznej wyświetl stan kondycji usług Microsoft 365, aby sprawdzić, czy wystąpiła aktywna przerwa w działaniu usługi.
ms.openlocfilehash: 3155d9a26fd2b34eb4f5bc820e906d35f1f7fdff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090214"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Jak sprawdzić kondycję usługi Microsoft 365

[![Etykieta informująca, że centrum administracyjne zmienia się, a więcej informacji na ten temat możesz znaleźć w witrynie aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Kondycję usługi firmy Microsoft, w tym usług w chmurze Office w sieci Web, Yammer, Microsoft Dynamics CRM i zarządzania urządzeniami przenośnymi, można wyświetlić na stronie **Kondycja usługi** [ Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

Jeśli nie możesz zalogować się do centrum administracyjnego, możesz użyć [strony stanu usługi](https://status.office365.com) , aby sprawdzić, czy występują znane problemy uniemożliwiające zalogowanie się do dzierżawy.  Zarejestruj się również, aby śledzić nas na [@MSFT365status](https://twitter.com/MSFT365Status) na Twitterze, aby zobaczyć informacje na temat niektórych wydarzeń.

## <a name="how-to-check-service-health"></a>Jak sprawdzić kondycję usługi

1. Przejdź do Centrum administracyjne platformy Microsoft 365 pod adresem [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)i zaloguj się przy użyciu konta administratora.

    > [!NOTE]
    > Osoby, do których przypisano rolę administratora globalnego lub administratora pomocy technicznej usługi, mogą wyświetlać kondycję usługi. Aby umożliwić administratorom programu Exchange, programu SharePoint i programu Skype dla firm wyświetlanie kondycji usługi, należy do nich również przypisać rolę administratora usługi. Aby uzyskać więcej informacji na temat ról, które mogą wyświetlać kondycję usługi, zobacz [Informacje o rolach administratora](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Aby wyświetlić kondycję usługi, w obszarze nawigacji po lewej stronie centrum administracyjnego przejdź do pozycji **Kondycja** >  **Kondycja usługi** lub wybierz kartę **Kondycja usługi** na **pulpicie nawigacyjnym Narzędzia główne**. Karta pulpitu nawigacyjnego wskazuje, czy występuje aktywny problem z usługą i linki do szczegółowej strony **Kondycja usługi**.

3. Na stronie **Kondycja usługi** stan kondycji każdej usługi w chmurze jest wyświetlany w formacie tabeli.

   ![Wyświetlanie bieżących problemów w usłudze Service Health.](../media/shd-landing-page.png)

Karta **Wszystkie usługi** (widok domyślny) zawiera wszystkie usługi, ich bieżący stan kondycji oraz wszystkie aktywne zdarzenia lub porady. Ikona i stan w kolumnie **Kondycja** wskazują stan każdej usługi.

Jeśli istnieje aktywne zdarzenie lub porada dotycząca usługi, zostaną one wymienione bezpośrednio pod nazwą usługi w tabeli zagnieżdżonej. Zagnieżdżoną tabelę można zwinąć, aby ukryć zdarzenia lub porady w tym widoku, klikając ikonę pagonu po lewej stronie nazwy usługi.

Aby odfiltrować widok, aby wyświetlić tylko wszystkie aktywne zdarzenia, wybierz kartę **Incydenty** w górnej części strony. Wybranie karty **Porady** spowoduje wyświetlenie tylko wszystkich aktywnych opublikowanych porad.

Karta **Historia** zawiera wszystkie zdarzenia i porady, które zostały rozwiązane w ciągu ostatnich siedmiu lub 30 dni.

Jeśli masz problem z usługą Microsoft 365 i nie widzisz jej na stronie **Kondycja usługi**, poinformuj nas o tym, wybierając **pozycję Zgłoś problem** i wykonując krótki formularz. Przyjrzymy się powiązanym danym i raportom z innych organizacji, aby zobaczyć, jak powszechny jest problem i czy pochodzi on z naszej usługi. Jeśli tak się stało, dodamy go jako nowe zdarzenie lub poradę na stronie **Kondycja usługi**, gdzie można śledzić jego rozwiązanie. Na stronie **Zgłaszane problemy** zostaną wyświetlone wszystkie problemy zgłoszone przez dzierżawę z tego formularza i stan.

Aby dostosować widok usług wyświetlanych na **pulpicie** nawigacyjnym, wybierz pozycję **PreferencjeWyślij** >  widok i wyczyść pola wyboru dla usług, które chcesz odfiltrować z widoku pulpitu nawigacyjnego Kondycja usługi. Upewnij się, że pole wyboru jest zaznaczone dla każdej usługi, którą chcesz monitorować.

Aby zarejestrować się w celu otrzymywania powiadomień e-mail o nowych zdarzeniach, które mają wpływ na dzierżawę i zmiany stanu aktywnego zdarzenia, wybierz pozycję **PreferencjeAmail** > , kliknij pozycję **Wyślij mi powiadomienia o kondycji usługi w wiadomości e-mail**, a następnie określ:

- Maksymalnie dwa adresy e-mail.
- Czy chcesz otrzymywać powiadomienia o zdarzeniach lub poradach
- Usługi, dla których chcesz powiadomić

Możesz również subskrybować powiadomienia e-mail dotyczące poszczególnych zdarzeń zamiast każdego zdarzenia dla usługi. W tym celu wybierz aktywny problem, dla których chcesz otrzymywać aktualizacje powiadomień e-mail, wybierz pozycję **Zarządzaj powiadomieniami dla tego problemu**, a następnie określ:

- Maksymalnie dwa adresy e-mail.

> [!NOTE]
> Każdy administrator może mieć ustawione preferencje, a powyższy limit dwóch adresów e-mail jest ustawiony na konto administratora.

> [!TIP]
> Możesz również użyć [aplikacji Administracja Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=627216) na urządzeniu przenośnym, aby wyświetlić Kondycja usługi, co jest doskonałym sposobem na bieżąco z powiadomieniami wypychanym.

### <a name="view-details-of-posted-service-health"></a>Wyświetlanie szczegółów opublikowanej kondycji usługi

W widoku **Wszystkie usługi** wybierz tytuł problemu, aby wyświetlić stronę szczegółów problemu, która zawiera więcej informacji o problemie, w tym kanał informacyjny wszystkich komunikatów opublikowanych podczas pracy nad rozwiązaniem.

[![Zrzut ekranu przedstawiający poradnik usługi.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

W podsumowaniu porady lub zdarzenia podane są następujące informacje:

- **Tytuł** — podsumowanie problemu.
- **ID** — identyfikator liczbowy problemu.
- **Usługa** — nazwa usługi, którego dotyczy problem.
- **Ostatnia aktualizacja** — czas ostatniej aktualizacji komunikatu o kondycji usługi.
- **Szacowany czas rozpoczęcia** — szacowany czas rozpoczęcia problemu.
- **Stan** — jak ten problem wpływa na usługę.
- **Wpływ na użytkownika** — krótki opis wpływu tego problemu na użytkownika końcowego.
- Wszystkie aktualizacje — często publikujemy **komunikaty informujące** o postępie stosowania rozwiązania.

![Zrzut ekranu przedstawiający szczegóły problemu.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Tłumaczenie szczegółów kondycji usługi

Tłumaczenie maszynowe służy do automatycznego wyświetlania komunikatów w preferowanym języku. Aby uzyskać więcej informacji na temat ustawiania języka, przeczytaj [artykuł Tłumaczenie języka dla pulpitu nawigacyjnego Kondycja usługi](lang-service-health.md).

### <a name="definitions"></a>Definicje

W większości przypadków usługi będą wyświetlane jako w dobrej kondycji bez dodatkowych informacji. Bieżący problem z usługą, jest określony jako porada lub zdarzenie i jest wyświetlony jego bieżący stan.

> [!TIP]
> Zdarzenia planowanej konserwacji nie są wyświetlane na stronie Kondycja usługi. Możesz śledzić zdarzenia planowanej konserwacji, obserwując na bieżąco **Centrum wiadomości**. Za pomocą filtru wyświetl wiadomości z kategorii Planowanie na wypadek zmiany, aby dowiedzieć się, kiedy zmiana zostanie wprowadzona, jakie będą jej efekty i jak się do niej przygotować. Aby uzyskać więcej informacji, zobacz [Centrum komunikatów w Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).

### <a name="incidents-and-advisories"></a>Zdarzenia i porady

| Ikonę | Opis |
|:-----|:-----|
|![Ikona informacji na potrzeby doradztwa.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Jeśli dla usługi jest wyświetlona porada, wiemy o problemie zakłócającym pracę niektórych użytkowników, ale usługa jest mimo to dostępna. W poradzie jest często podane obejście problemu. Problem może być sporadyczny lub mieć ograniczony zakres i wpływ na użytkowników.  <br/> |
|![Ikona wykrzyknego punktu zdarzenia.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Jeśli dla usługi jest wyświetlone aktywne zdarzenie, występuje problem krytyczny i usługa lub główna funkcja usługi jest niedostępna. Na przykład użytkownicy mogą nie mieć możliwości wysyłania i odbierania wiadomości e-mail lub zalogowania się. Zdarzenia będą miały zauważalny wpływ na użytkowników. Gdy zdarzenie jest w toku, będziemy udostępniać aktualizacje dotyczące badania, podjętych prób złagodzenia wpływu i potwierdzenia rozwiązania na pulpicie nawigacyjnym kondycji usługi.  <br/> |

### <a name="status-definitions"></a>Definicje stanów

| Stan | Definicja |
|:-----|:-----|
|**Badanie** | Wiemy o potencjalnym problemie i zbieramy dodatkowe informacje na temat bieżącej sytuacji i zakresu jej wpływu. |
|**Obniżenie wydajności usługi** | Potwierdziliśmy występowanie problemu, który może zakłócać korzystanie z usługi lub funkcji. Ten status może być wyświetlany, jeśli na przykład usługa działa wolniej niż zwykle, występują sporadyczne przerwy w świadczeniu usługi lub określona funkcja nie działa. |
|**Przerwa w świadczeniu usługi** | Ten status zostanie wyświetlony, jeśli ustalimy, że problem uniemożliwia użytkownikom uzyskanie dostępu do usługi. W tym przypadku problem jest istotny i może być spójnie odtworzony. |
|**Przywracanie usługi** | Przyczyna problemu została zidentyfikowana, wiemy, jaką akcję naprawczą należy podjąć, i jesteśmy w trakcie procesu przywracania stanu dobrej kondycji usługi. |
|**Przedłużone odzyskiwanie usługi** | Ten stan oznacza, że akcja naprawcza trwa, aby przywrócić usługę dla większości użytkowników, ale usunięcie problemu względem wszystkich systemów zajmie trochę czasu. Ten stan może być również widoczny, jeśli wprowadziliśmy tymczasową poprawkę w celu zmniejszenia wpływu, gdy czekamy na zastosowanie trwałej poprawki. |
|**Wstrzymano badanie problemu** | Ten stan zostanie wyświetlony, jeśli wynikiem naszego szczegółowego badania potencjalnego problemu jest prośba o dodatkowe informacje od klientów, aby można było przeprowadzić dalsze badania. Jeśli konieczne jest działanie z Twojej strony, powiadomimy Cię, jakie dane lub dzienniki są nam potrzebne. |
|**Usługa została przywrócona** | Potwierdziliśmy, że akcja naprawcza rozwiązała podstawowy problem i przywrócono stan dobrej kondycji usługi. Aby dowiedzieć się, na czym polegał problem, wyświetl szczegóły problemu. |
|**Wynik fałszywie dodatni** | Po szczegółowym badaniu potwierdziliśmy, że usługa jest w dobrej kondycji i działa zgodnie z projektem. Nie zaobserwowano żadnego wpływu na usługę ani nie zaobserwowano przyczyny zdarzenia pochodzącego poza usługę. Zdarzenia i porady o tym stanie są wyświetlane w widoku historii do momentu ich wygaśnięcia (po upływie okresu określonego w ostatnim wpisie dla tego zdarzenia). |
|**Opublikowany raport po zdarzeniu** | Opublikowaliśmy raport po zdarzeniu dla określonego problemu, który zawiera informacje o głównej przyczynie, i następne kroki, aby upewnić się, że podobny problem nie wystąpi ponownie. |

### <a name="message-post-types"></a>Typy wpisów komunikatów

| Wpisać | Definicja |
|:-----|:-----|
|**Szybka aktualizacja** | Krótkie i częste aktualizacje przyrostowe dla zdarzeń o szerokim wpływie, dostępne dla wszystkich klientów. |
|**Dodatkowe szczegóły** | Te dodatkowe wpisy zapewnią bogatsze szczegóły techniczne i rozwiązywania problemów, aby zapewnić lepszy wgląd w obsługę zdarzeń. Jest to dostępne dla dzierżaw, które spełniają te same wymagania opisane w [Exchange Online monitorowania](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements), |

### <a name="history"></a>Historia

Kondycja usługi umożliwia zapoznanie się z bieżącym stanem kondycji i wyświetlenie historii wszelkich porad dotyczących usług i zdarzeń, które wpłynęły na dzierżawę w ciągu ostatnich 30 dni. Aby wyświetlić poprzednią kondycję wszystkich usług, wybierz pozycję Widok **historii** .

Aby uzyskać więcej informacji na temat naszego zaangażowania w czas pracy, zobacz [Transparent operations from Microsoft 365 (Operacje przezroczyste z Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)).

## <a name="related-topics"></a>Tematy pokrewne

- [Raporty aktywności w Centrum administracyjne platformy Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [Preferencje centrum komunikatów](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Jak sprawdzić kondycję wersji Windows w centrum administracyjnym](/windows/deployment/update/check-release-health)
