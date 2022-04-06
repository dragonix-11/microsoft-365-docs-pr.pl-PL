---
title: Konfigurowanie możliwości Microsoft Threat Experts i zarządzanie nimi za pośrednictwem Microsoft 365 Defender
description: Subskrybowanie ekspertów ds. zagrożeń firmy Microsoft za pośrednictwem Microsoft 365 Defender w celu konfigurowania i używania ich w codziennych operacjach zabezpieczeń i administrowaniu zabezpieczeniami.
keywords: Microsoft Threat Experts, zarządzana usługa wyszukiwania zagrożeń, MTE, zarządzana usługa wyszukiwania zagrożeń firmy Microsoft
search.product: Windows 10
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-maave
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: cd8f7e65c409138d6404a734b098e70e6d419cbb
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667279"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Konfigurowanie możliwości Microsoft Threat Experts i zarządzanie nimi za pośrednictwem Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!IMPORTANT]
> Przed zastosowaniem należy omówić wymagania dotyczące uprawnień dla usługi Microsoft Threat Experts — Targeted Attack Notifications managed threat hunting service z dostawcą usług technicznych firmy Microsoft i zespołem kont.

Aby otrzymywać powiadomienia o atakach ukierunkowanych, konieczne będzie wdrożenie Microsoft 365 Defender z zarejestrowanymi urządzeniami. Następnie prześlij aplikację za pośrednictwem portalu M365, aby uzyskać Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych.

Skontaktuj się z zespołem ds. konta lub przedstawicielem firmy Microsoft, aby zasubskrybować Microsoft Threat Experts — Eksperci na żądanie. Usługa Experts on Demand umożliwia skonsultowanie się z naszymi ekspertami w dziedzinie zagrożeń, aby dowiedzieć się, jak chronić organizację przed odpowiednimi wykryciami i przeciwnikami.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Ubiegaj się o Microsoft Threat Experts — docelowa usługa powiadomień o atakach

Jeśli masz już Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft 365 Defender, możesz ubiegać się o Microsoft Threat Experts — ukierunkowane powiadomienia o ataku za pośrednictwem ich Microsoft 365 Defender portalu.  Powiadomienia o ukierunkowanych atakach zapewniają specjalny wgląd i analizę, aby ułatwić identyfikację najbardziej krytycznych zagrożeń dla organizacji, dzięki czemu możesz szybko na nie reagować.

1. W okienku nawigacji przejdź do **obszaru Ustawienia > Punkty końcowe > Funkcje ogólne > zaawansowane > Microsoft Threat Experts — powiadomienia o atakach docelowych**.

2. Wybierz pozycję **Zastosuj**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Strona ustawień Microsoft Threat Experts w portalu Microsoft 365 Defender" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Wprowadź imię i nazwisko i adres e-mail, aby firma Microsoft mogła skontaktować się z Tobą w kwestii Twojej aplikacji.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Strona aplikacji Microsoft Threat Experts w portalu Microsoft 365 Defender" lightbox="../../media/mte/mte-apply.png":::
  
4. Przeczytaj [oświadczenie o ochronie prywatności](https://privacy.microsoft.com/en-us/privacystatement), a następnie wybierz pozycję **Prześlij** po zakończeniu. Po zatwierdzeniu aplikacji otrzymasz powitalną wiadomość e-mail.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Potwierdzenie aplikacji Microsoft Threat Experts w portalu Microsoft 365 Defender" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Po otrzymaniu powitalnej wiadomości e-mail automatycznie zaczniesz otrzymywać powiadomienia o ukierunkowanych atakach.

6. Stan możesz zweryfikować, odwiedzając stronę **Ustawienia > Endpoints > General > Advanced features (Punkty końcowe ogólne > zaawansowane).** Po zatwierdzeniu przełącznik **Microsoft Threat Experts — powiadomienie o ataku docelowym** będzie widoczny **i włączony.**

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Gdzie zobaczysz powiadomienia o ukierunkowanym ataku z Microsoft Threat Experts

Możesz otrzymywać powiadomienia o ataku ukierunkowanym z Microsoft Threat Experts za pośrednictwem następujących nośników:

- Strona **zdarzeń** portalu Microsoft 365 Defender
- Pulpit nawigacyjny **alertów** portalu Microsoft 365 Defender
- Interfejs [API](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) alertów OData i [interfejs API REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Tabela DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) w obszarze Zaawansowane wyszukiwanie zagrożeń
- Skrzynka odbiorcza, jeśli zdecydujesz się na wysyłanie do Ciebie ukierunkowanych powiadomień o atakach za pośrednictwem poczty e-mail. Zobacz [Tworzenie reguły powiadomień e-mail](#create-an-email-notification-rule) poniżej.

### <a name="create-an-email-notification-rule"></a>Tworzenie reguły powiadomień e-mail

Możesz utworzyć reguły wysyłania powiadomień e-mail dla adresatów powiadomień. Aby uzyskać szczegółowe informacje, zobacz  [Konfigurowanie powiadomień o alertach](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) w celu tworzenia, edytowania, usuwania lub rozwiązywania problemów z powiadomieniami e-mail.

## <a name="view-targeted-attack-notifications"></a>Wyświetlanie powiadomień o ukierunkowanych atakach

Po skonfigurowaniu systemu do odbierania powiadomień e-mail rozpoczniesz otrzymywanie powiadomienia o ataku ukierunkowanym z Microsoft Threat Experts w wiadomości e-mail.

1. Wybierz link w wiadomości e-mail, aby przejść do odpowiedniego kontekstu alertu na **pulpicie nawigacyjnym z tagiem Eksperci od zagrożeń**.

2. Na stronie **Alerty** wybierz ten sam temat alertu co ten, który został wyświetlony w wiadomości e-mail, aby wyświetlić dalsze szczegóły.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Subskrybowanie Microsoft Threat Experts — eksperci na żądanie

Jeśli jesteś już klientem Ochrona punktu końcowego w usłudze Microsoft Defender, możesz skontaktować się z przedstawicielem firmy Microsoft, aby zasubskrybować Microsoft Threat Experts — Eksperci na żądanie.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Skontaktuj się z ekspertem ds. zagrożeń firmy Microsoft w sprawie podejrzanych działań związanych z cyberbezpieczeństwem w organizacji

Możesz skontaktować się z Microsoft Threat Experts z poziomu portalu Microsoft 365 Defender. Eksperci mogą pomóc w zrozumieniu złożonych zagrożeń i ukierunkowanych powiadomień o atakach. Skontaktuj się z ekspertami, aby uzyskać więcej informacji na temat alertów i zdarzeń, lub porady dotyczące obsługi naruszenia zabezpieczeń. Uzyskaj wgląd w kontekst analizy zagrożeń opisany przez pulpit nawigacyjny portalu.

> [!NOTE]
>
> - Zapytania dotyczące alertów związane z dostosowanymi danymi analizy zagrożeń w organizacji nie są obecnie obsługiwane. Aby uzyskać szczegółowe informacje, skontaktuj się z zespołem ds. operacji zabezpieczeń lub reagowania na zdarzenia.
> - Musisz mieć **uprawnienie Zarządzaj ustawieniami zabezpieczeń w centrum zabezpieczeń** w portalu Microsoft 365 Defender, aby przesłać zapytanie za pośrednictwem formularza **Consult a threat expert (Skonsultuj się z ekspertem** ds. zagrożeń).

1. Przejdź do strony portalu związanej z informacjami, które chcesz zbadać: na przykład **Urządzenie**, **Alert** lub **Incydent**. Przed wysłaniem żądania zbadania upewnij się, że strona portalu powiązana z zapytaniem jest widoczna.

2. Z górnego menu wybierz pozycję **? Skontaktuj się z ekspertem ds. zagrożeń**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Microsoft Threat Experts Eksperci na żądanie z menu w portalu Microsoft 365 Defender" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Zostanie otwarty ekran wysuwany.

    Nagłówek wskazuje, czy korzystasz z subskrypcji wersji próbnej, czy pełnej Microsoft Threat Experts — subskrypcja eksperci na żądanie.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Ekran subskrypcji wersji próbnej Microsoft Threat Experts Experts on Demand w portalu Microsoft 365 Defender" lightbox="../../media/mte/mte-trial.png":::

    Pole **Temat badania** zostanie już wypełnione linkiem do odpowiedniej strony żądania.

3. W następnym polu podaj wystarczającą ilość informacji, aby nadać Microsoft Threat Experts kontekst wystarczająco dużo, aby rozpocząć badanie.

4. Wprowadź adres e-mail, którego chcesz użyć, aby odpowiadać Microsoft Threat Experts.

> [!NOTE]
> Jeśli chcesz śledzić stan spraw eksperci na żądanie za pośrednictwem Centrum usług firmy Microsoft, skontaktuj się z menedżerem konta technicznego.

Obejrzyj to wideo, aby zapoznać się z krótkim omówieniem Centrum usług firmy Microsoft.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Przykładowe tematy badania

### <a name="alert-information"></a>Informacje o alertach

- Widzieliśmy nowy rodzaj alertu dla living-off-the-land binarnych. Możemy podać identyfikator alertu. Czy możesz powiedzieć nam więcej o tym alercie i o tym, jak możemy go dokładniej zbadać?
- Zaobserwowaliśmy dwa podobne ataki, które próbują wykonać złośliwe skrypty programu PowerShell, ale generują różne alerty. Jednym z nich jest "Podejrzany wiersz polecenia programu PowerShell", a drugi to "Wykryto złośliwy plik na podstawie wskazania dostarczonego przez usługę O365". Jaka jest różnica?
- Dzisiaj otrzymaliśmy nietypowy alert o nietypowej liczbie nieudanych logowań z urządzenia użytkownika o wysokim profilu. Nie możemy znaleźć żadnych dalszych dowodów na te próby. Jak Microsoft 365 Defender zobaczyć te próby? Jakiego typu logowania są monitorowane?
- Czy możesz podać więcej kontekstu lub szczegółowych informacji na temat alertu "Zaobserwowano podejrzane zachowanie narzędzia systemowego"?
- Zaobserwowano alert o nazwie "Tworzenie reguły przekazywania/przekierowania". Uważam, że działalność jest łagodna. Czy możesz mi powiedzieć, dlaczego otrzymałem alert?

### <a name="possible-machine-compromise"></a>Możliwe naruszenie zabezpieczeń maszyny

- Czy możesz wyjaśnić, dlaczego na wielu urządzeniach w naszej organizacji jest wyświetlany komunikat lub alert dotyczący "zaobserwowanego nieznanego procesu"? Doceniamy wszelkie dane wejściowe, aby wyjaśnić, czy ten komunikat lub alert jest związany ze złośliwym działaniem.
- Czy możesz pomóc w zweryfikowaniu możliwego kompromisu w następującym systemie, pochodzącym z zeszłego tygodnia? Działa podobnie jak poprzednie wykrywanie złośliwego oprogramowania w tym samym systemie sześć miesięcy temu.

### <a name="threat-intelligence-details"></a>Szczegóły analizy zagrożeń

- Wykryliśmy wiadomość e-mail wyłudzającą informacje, która dostarczyła użytkownikowi złośliwy dokument programu Word. Dokument spowodował serię podejrzanych zdarzeń, które wyzwoliły wiele alertów dla określonej rodziny złośliwego oprogramowania. Czy masz jakieś informacje na temat tego złośliwego oprogramowania? Jeśli tak, czy możesz wysłać nam link?
- Niedawno zobaczyliśmy wpis w blogu o zagrożeniu, które jest skierowane do naszej branży. Czy możesz pomóc nam zrozumieć, jaką ochronę zapewnia Microsoft 365 Defender przed tym aktorem zagrożeń?
- Ostatnio zaobserwowaliśmy kampanię wyłudzania informacji prowadzoną przeciwko naszej organizacji. Czy możesz nam powiedzieć, czy było to skierowane specjalnie do naszej firmy, czy do pionu?

### <a name="microsoft-threat-experts-alert-communications"></a>komunikacja alertów Microsoft Threat Experts

- Czy twój zespół reagowania na zdarzenia może pomóc nam w rozwiązaniu otrzymanego powiadomienia o ataku?
- Otrzymaliśmy to ukierunkowane powiadomienie o ataku od Microsoft Threat Experts. Nie mamy własnego zespołu reagowania na zdarzenia. Co możemy teraz zrobić i jak możemy powstrzymać zdarzenie?
- Otrzymaliśmy powiadomienie o ataku ukierunkowanym od Microsoft Threat Experts. Jakie dane można nam podać, które możemy przekazać naszemu zespołowi reagowania na zdarzenia?

> [!NOTE]
> Microsoft Threat Experts jest zarządzaną usługą wyszukiwania zagrożeń, a nie usługą reagowania na zdarzenia. Możesz jednak skontaktować się z własnym zespołem reagowania na zdarzenia, aby rozwiązać problemy wymagające reakcji na zdarzenia. Jeśli nie masz własnego zespołu ds. reagowania na zdarzenia i chcesz uzyskać pomoc firmy Microsoft, możesz skontaktować się z zespołem CSS Cybersecurity Incident Response Team (CIRT). Mogą otworzyć bilet, aby pomóc w rozwiązaniu twojego zapytania.

## <a name="scenario"></a>Scenariusz

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Otrzymywanie raportu postępu dotyczącego zapytania dotyczącego wyszukiwania zagrożeń zarządzanych

Odpowiedź od Microsoft Threat Experts będzie się różnić w zależności od zapytania. Zazwyczaj otrzymasz jedną z następujących odpowiedzi:

- Aby kontynuować dochodzenie, potrzebne są dodatkowe informacje
- Plik lub kilka przykładów plików jest potrzebnych do określenia kontekstu technicznego
- Badanie wymaga więcej czasu
- Wstępne informacje wystarczyły, aby zakończyć dochodzenie

Jeśli ekspert zażąda więcej informacji lub przykładów plików, kluczowe jest szybkie reagowanie, aby kontynuować dochodzenie.

## <a name="see-also"></a>Zobacz też

- [Przegląd ekspertów ds. zagrożeń firmy Microsoft](microsoft-threat-experts.md)
