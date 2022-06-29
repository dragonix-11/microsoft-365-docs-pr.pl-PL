---
title: Konfigurowanie funkcji usługi Microsoft Threat Experts i zarządzanie nimi
ms.reviewer: ''
description: Zarejestruj się w firmie Microsoft Threats Experts, aby skonfigurować i używać jej w codziennych operacjach zabezpieczeń i administrowaniu zabezpieczeniami oraz zarządzać nimi.
keywords: Microsoft Threat Experts, zarządzana usługa wyszukiwania zagrożeń, MTE, zarządzana usługa wyszukiwania zagrożeń firmy Microsoft
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7661619ccb60bb55020a8e241c341b11fe45abd1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487350"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>Konfigurowanie funkcji usługi Microsoft Threat Experts i zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!NOTE]
> Przed zastosowaniem do usługi Microsoft Threat Experts — Targeted Attack Notification zarządzanej usługi wyszukiwania zagrożeń omów wymagania dotyczące uprawnień z dostawcą usług technicznych firmy Microsoft i zespołem ds. konta.

Upewnij się, że usługa Defender for Endpoint została wdrożona w środowisku z zarejestrowanymi urządzeniami, a nie tylko w konfiguracji laboratorium.

Jeśli jesteś klientem usługi Defender for Endpoint, musisz ubiegać się o **Microsoft Threat Experts — docelowe powiadomienia o atakach**, aby uzyskać specjalne szczegółowe informacje i analizy ułatwiające zidentyfikowanie najbardziej krytycznych zagrożeń, dzięki czemu możesz szybko na nie reagować. Skontaktuj się z zespołem ds. konta lub przedstawicielem firmy Microsoft, aby zasubskrybować **Microsoft Threat Experts — eksperci na żądanie**, aby skonsultować się z naszymi ekspertami ds. zagrożeń w sprawie odpowiednich wykryć i przeciwników.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Ubiegaj się o Microsoft Threat Experts — docelowa usługa powiadomień o atakach

Jeśli jesteś już klientem usługi Defender for Endpoint, możesz złożyć wniosek za pośrednictwem portalu Microsoft 365 Defender.

1. W okienku nawigacji przejdź do pozycji **Ustawienia > Ogólne > Funkcje zaawansowane > Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych**.

2. Kliknij przycisk **Zastosuj**.

   :::image type="content" source="images/mte-collaboratewithmte.png" alt-text="Ustawienia Microsoft Threat Experts" lightbox="images/mte-collaboratewithmte.png":::

3. Wprowadź imię i nazwisko i adres e-mail, aby firma Microsoft mogła wrócić do Ciebie w aplikacji.

   :::image type="content" source="images/mte-apply.png" alt-text="Pole Nazwa na stronie aplikacji Microsoft Threat Experts" lightbox="images/mte-apply.png":::

4. Przeczytaj [oświadczenie o ochronie prywatności](https://privacy.microsoft.com/privacystatement), a następnie kliknij pozycję **Prześlij** po zakończeniu. Po zatwierdzeniu aplikacji otrzymasz powitalną wiadomość e-mail.

   :::image type="content" source="images/mte-applicationconfirmation.png" alt-text="Komunikat z potwierdzeniem aplikacji Microsoft Threat Experts" lightbox="images/mte-applicationconfirmation.png":::

Po zaakceptowaniu otrzymasz powitalną wiadomość e-mail i zobaczysz zmianę przycisku **Zastosuj** na przełącznik "włączony". Jeśli chcesz wyjąć się z usługi Targeted Attack Notifications, przesuń przełącznik "off" i kliknij pozycję **Zapisz preferencje** w dolnej części strony.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Gdzie zobaczysz powiadomienia o ukierunkowanym ataku z Microsoft Threat Experts

Możesz otrzymywać powiadomienia o ataku docelowym z Microsoft Threat Experts za pośrednictwem następującego nośnika:

- Strona **Zdarzenia** portalu usługi Defender for Endpoint
- Pulpit nawigacyjny alertów portalu usługi Defender dla punktów **końcowych**
- Interfejs [API](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) alertów OData i [interfejs API REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Tabela DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) w obszarze Zaawansowane wyszukiwanie zagrożeń
- Wiadomość e-mail, jeśli zdecydujesz się ją skonfigurować

Aby otrzymywać powiadomienia o atakach ukierunkowanych za pośrednictwem poczty e-mail, utwórz regułę powiadomień e-mail.

### <a name="create-an-email-notification-rule"></a>Tworzenie reguły powiadomień e-mail

Możesz utworzyć reguły wysyłania powiadomień e-mail dla adresatów powiadomień. Aby uzyskać szczegółowe informacje, zobacz  [Konfigurowanie powiadomień o alertach](configure-email-notifications.md) w celu tworzenia, edytowania, usuwania lub rozwiązywania problemów z powiadomieniami e-mail.

## <a name="view-the-targeted-attack-notification"></a>Wyświetlanie powiadomienia o ataku ukierunkowanym

Po skonfigurowaniu systemu do odbierania powiadomień e-mail rozpoczniesz otrzymywanie powiadomienia o ataku ukierunkowanym z Microsoft Threat Experts w wiadomości e-mail.

1. Kliknij link w wiadomości e-mail, aby przejść do odpowiedniego kontekstu alertu na **pulpicie nawigacyjnym z tagiem Eksperci od zagrożeń**.

2. Na pulpicie nawigacyjnym wybierz ten sam temat alertu, który został uzyskany z wiadomości e-mail, aby wyświetlić szczegóły.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Subskrybowanie Microsoft Threat Experts — eksperci na żądanie

Jest ona dostępna jako usługa subskrypcji. Jeśli jesteś już klientem usługi Defender for Endpoint, możesz skontaktować się z przedstawicielem firmy Microsoft, aby zasubskrybować usługę Microsoft Threat Experts — Eksperci na żądanie.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Skontaktuj się z ekspertem ds. zagrożeń firmy Microsoft w sprawie podejrzanych działań związanych z cyberbezpieczeństwem w organizacji

Możesz nawiązać współpracę z Microsoft Threat Experts, którzy mogą być zaangażowani bezpośrednio z poziomu portalu Microsoft 365 Defender w celu ich odpowiedzi. Eksperci udostępniają szczegółowe informacje, aby lepiej zrozumieć złożone zagrożenia, otrzymywane powiadomienia o ukierunkowanych atakach lub jeśli potrzebujesz więcej informacji o alertach, potencjalnie naruszonym urządzeniu lub kontekście analizy zagrożeń widocznym na pulpicie nawigacyjnym portalu.

> [!NOTE]
>
> - Zapytania dotyczące alertów związane z dostosowanymi danymi analizy zagrożeń w organizacji nie są obecnie obsługiwane. Aby uzyskać szczegółowe informacje, skontaktuj się z zespołem ds. operacji zabezpieczeń lub zespołu reagowania na zdarzenia.
> - Musisz mieć **uprawnienie Zarządzaj ustawieniami zabezpieczeń** w portalu Microsoft 365 Defender, aby móc przesłać zapytanie "Skonsultuj się z ekspertem od zagrożeń".

1. Przejdź do strony portalu z odpowiednimi informacjami, które chcesz zbadać, na przykład stroną **Incydent** . Przed wysłaniem żądania zbadania upewnij się, że strona odpowiedniego alertu lub urządzenia jest widoczna.

2. W prawym górnym menu kliknij przycisk **?** . Następnie wybierz pozycję **Skonsultuj się z ekspertem ds. zagrożeń**.

    :::image type="content" source="images/mte-eod-menu.png" alt-text="Element menu eksperci Microsoft Threat Experts na żądanie" lightbox="images/mte-eod-menu.png":::

    Zostanie otwarty ekran wysuwany. Na poniższym ekranie przedstawiono, kiedy korzystasz z subskrypcji wersji próbnej.

    :::image type="content" source="images/mte-eod.png" alt-text="Strona eksperci Microsoft Threat Experts na żądanie" lightbox="images/mte-eod.png":::

    Na poniższym ekranie przedstawiono, kiedy korzystasz z pełnej Microsoft Threat Experts — subskrypcja Eksperci na żądanie.

    :::image type="content" source="images/mte-eod-fullsubscription.png" alt-text="Pełna strona subskrypcji Microsoft Threat Experts Experts on Demand" lightbox="images/mte-eod-fullsubscription.png":::

    Pole **Temat zapytania** jest wstępnie wypełnione linkiem do odpowiedniej strony żądania badania. Na przykład link do strony zdarzenia, alertu lub szczegółów urządzenia, na którą byłeś podczas żądania.

3. W następnym polu podaj wystarczającą ilość informacji, aby nadać Microsoft Threat Experts kontekst wystarczająco dużo, aby rozpocząć badanie.

4. Wprowadź adres e-mail, którego chcesz użyć, aby odpowiadać Microsoft Threat Experts.

> [!NOTE]
> Jeśli chcesz śledzić stan swoich spraw eksperci na żądanie za pośrednictwem Centrum usług firmy Microsoft, skontaktuj się z Menedżerem konta sukcesu klienta.

Obejrzyj to wideo, aby zapoznać się z krótkim omówieniem Centrum usług firmy Microsoft.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>Przykładowe tematy badania, które można znaleźć w Microsoft Threat Experts — Eksperci na żądanie

### <a name="alert-information"></a>Informacje o alertach

- Widzimy nowy typ alertu dla danych binarnych typu living-off-the-land: [AlertID]. Czy możesz nam powiedzieć coś więcej o tym alercie i o tym, jak możemy dokładniej zbadać ten alert?
- Zaobserwowaliśmy dwa podobne ataki, które próbują wykonywać złośliwe skrypty programu PowerShell, ale generują różne alerty. Jednym z nich jest "Podejrzany wiersz polecenia programu PowerShell", a drugi to "Wykryto złośliwy plik na podstawie wskazania dostarczonego przez usługę O365". Jaka jest różnica?
- Otrzymuję dziś nieparzysty alert dotyczący nietypowej liczby nieudanych logowań z urządzenia użytkownika o wysokim profilu. Nie mogę znaleźć żadnych dalszych dowodów na te próby logowania. Jak usługa Defender dla punktu końcowego może zobaczyć te próby? Jakiego typu logowania są monitorowane?
- Można podać więcej kontekstu lub szczegółowych informacji na temat tego alertu: "Zaobserwowano podejrzane zachowanie narzędzia systemowego".

### <a name="possible-machine-compromise"></a>Możliwe naruszenie zabezpieczeń maszyny

- Czy możesz pomóc odpowiedzieć, dlaczego widzimy "Zaobserwowano nieznany proces?" Ten komunikat lub alert jest często wyświetlany na wielu urządzeniach. Doceniamy wszelkie dane wejściowe, aby wyjaśnić, czy ten komunikat lub alert jest związany ze złośliwym działaniem.
- Czy możesz pomóc w zweryfikowaniu ewentualnego naruszenia zabezpieczeń w następującym systemie w dniu [data] z podobnymi zachowaniami jak poprzednie wykrywanie złośliwego oprogramowania w tym samym systemie w ciągu [miesiąca]?

### <a name="threat-intelligence-details"></a>Szczegóły analizy zagrożeń

- Wykryliśmy wiadomość e-mail wyłudzającą informacje, która dostarczyła użytkownikowi złośliwy dokument programu Word. Złośliwy dokument programu Word spowodował serię podejrzanych zdarzeń, które wyzwoliły wiele alertów usługi Defender for Endpoint dotyczących złośliwego oprogramowania [nazwa złośliwego oprogramowania]. Czy masz jakieś informacje na temat tego złośliwego oprogramowania? Jeśli tak, możesz wysłać mi link?
- Niedawno widziałem [social media odniesienia, na przykład Twitter lub blog] post o zagrożeniu, które jest skierowane do mojej branży. Czy możesz pomóc mi zrozumieć, jaką ochronę zapewnia usługa Defender for Endpoint przed tym aktorem zagrożeń?

### <a name="microsoft-threat-experts-alert-communications"></a>komunikacja alertów Microsoft Threat Experts

- Czy twój zespół reagowania na zdarzenia może pomóc nam w rozwiązaniu otrzymanego powiadomienia o ataku?
- Otrzymałem to ukierunkowane powiadomienie o ataku z Microsoft Threat Experts. Nie mamy własnego zespołu reagowania na zdarzenia. Co możemy teraz zrobić i jak możemy powstrzymać zdarzenie?
- Otrzymałem powiadomienie o ataku ukierunkowanym od Microsoft Threat Experts. Jakie dane można nam podać, które możemy przekazać naszemu zespołowi reagowania na zdarzenia?

  > [!NOTE]
  > Microsoft Threat Experts jest zarządzaną usługą wyszukiwania zagrożeń cybernetycznych, a nie usługą reagowania na zdarzenia. Możesz jednak skontaktować się z własnym zespołem reagowania na zdarzenia, aby rozwiązać problemy wymagające reakcji na zdarzenia. Jeśli nie masz własnego zespołu ds. reagowania na zdarzenia i chcesz uzyskać pomoc firmy Microsoft, możesz skontaktować się z zespołem CSS Cybersecurity Incident Response Team (CIRT). Mogą otworzyć bilet, aby pomóc w rozwiązaniu twojego zapytania.

## <a name="scenario"></a>Scenariusz

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Otrzymywanie raportu postępu dotyczącego zapytania dotyczącego wyszukiwania zagrożeń zarządzanych

Odpowiedź od Microsoft Threat Experts różni się w zależności od zapytania. W ciągu dwóch dni przekażą Do Ciebie raport o postępach dotyczący zapytania **eksperta ds. zagrożeń w** celu przekazania stanu badania z następujących kategorii:

- Aby kontynuować dochodzenie, potrzebne są dodatkowe informacje
- Plik lub kilka przykładów plików jest potrzebnych do określenia kontekstu technicznego
- Badanie wymaga więcej czasu
- Wstępne informacje wystarczyły, aby zakończyć dochodzenie

Ważne jest, aby szybko zareagować, aby utrzymać dochodzenie w ruchu.

## <a name="related-topic"></a>Temat pokrewny

- [Przegląd ekspertów ds. zagrożeń firmy Microsoft](microsoft-threat-experts.md)
- [Microsoft Threat Experts na platformie Microsoft 365 — omówienie](/microsoft-365/security/mtp/microsoft-threat-experts)
