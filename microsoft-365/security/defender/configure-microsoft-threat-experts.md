---
title: Konfigurowanie funkcji i zarządzanie Microsoft Threat Experts za pośrednictwem Microsoft 365 Defender
description: Zasubskrybuj ekspertów ds. zagrożeń firmy Microsoft za Microsoft 365 Defender, aby konfigurować i używać go oraz zarządzać nimi w codziennych działaniach związanych z zabezpieczeniami i administrowaniem zabezpieczeniami.
keywords: Microsoft Threat Experts, zarządzana służba chłoniania zagrożeń, MTE, firma Microsoft zarządzała usługą chowania
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
ms.openlocfilehash: 8a8de691ff08b50b56c34ed9e779cc97d48c5fcd
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755838"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Konfigurowanie funkcji i zarządzanie Microsoft Threat Experts za pośrednictwem Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!IMPORTANT]
> Przed zastosowaniem, upewnij się, że zostały omówione wymagania dotyczące uprawnień do programu Microsoft Threat Experts — powiadomienia o atakach kierowanej pod zarządzaniem usługą chłoniania zagrożeń z dostawcą pomocy technicznej firmy Microsoft i zespołem konta.

Aby otrzymywać powiadomienia o atakach ukierunkowanych, musisz wdrożyć Microsoft 365 Defender z zarejestrowanymi urządzeniami. Następnie prześlij aplikację za pośrednictwem portalu M365 dla Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych.

Skontaktuj się ze swoim zespołem ds. klientów lub przedstawicielem firmy Microsoft, aby zasubskrybować usługę Microsoft Threat Experts — Experts on Demand. Ekspertów na żądanie pozwala konsultować się z naszymi ekspertami ds. zagrożeń, jak chronić twoją organizację przed odpowiednimi wykryciami i adwersjami.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Zastosuj do Microsoft Threat Experts — usługa powiadomień o atakach ukierunkowanych

Jeśli masz już program Microsoft Defender for Endpoint i Microsoft 365 Defender, możesz złożyć wniosek o Microsoft Threat Experts — powiadomienia o atakach kierowane za pośrednictwem ich Microsoft 365 Defender sieci Web.  Powiadomienia o atakach ukierunkowanych przyznają Ci specjalne informacje i analizy, które ułatwiają identyfikowanie najważniejszych zagrożeń dla organizacji, dzięki czemu możesz szybko na nie reagować.

1. W okienku nawigacji przejdź do Ustawienia > **punktów końcowych > Ogólne > zaawansowane funkcje > Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych**.

2. Wybierz **pozycję Zastosuj**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Strona Microsoft Threat Experts ustawień w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Wprowadź swoje imię i nazwisko (nazwę) oraz adres e-mail, aby firma Microsoft skontaktowały się z Tobą w sprawie Twojej aplikacji.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Strona Microsoft Threat Experts aplikacji w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mte/mte-apply.png":::
  
4. Przeczytaj zasady [zachowania poufności informacji](https://privacy.microsoft.com/en-us/privacystatement), a **następnie po wybraniu** przycisku Prześlij wybierz pozycję Prześlij. Po zatwierdzeniu aplikacji otrzymasz powitaną wiadomość e-mail.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Potwierdzenie Microsoft Threat Experts aplikacji w portalu Microsoft 365 Defender adresowej" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Gdy otrzymasz powitaną wiadomość e-mail, automatycznie zaczniesz otrzymywać powiadomienia o ukierunkowanych atakach.

6. Możesz zweryfikować swój status, odwiedzając Ustawienia > **punktów końcowych > ogólne > funkcje zaawansowane**. Po zatwierdzeniu przełącznik **powiadomienia o Microsoft Threat Experts —** ukierunkowany atak będzie widoczny i **włączony**.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Miejsce, w którym są wyświetlane powiadomienia o atakach ukierunkowanych z aplikacji Microsoft Threat Experts

Możesz otrzymywać powiadomienia o atakach ukierunkowanych od Microsoft Threat Experts za pośrednictwem następujących mediów:

- Strona Microsoft 365 Defender zdarzenia w **portalu**
- Pulpit Microsoft 365 Defender alertów **w portalu**
- Interfejs API alertów [](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) OData i [interfejs API rest](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) table in Advanced hunting
- Skrzynka odbiorcza, jeśli zdecydujesz się na wysyłanie do Ciebie za pośrednictwem poczty e-mail powiadomień o atakach ukierunkowanych. Zobacz [Tworzenie reguły powiadomienia e-mail](#create-an-email-notification-rule) poniżej.

### <a name="create-an-email-notification-rule"></a>Tworzenie reguły powiadomienia e-mail

Możesz utworzyć reguły w celu wysyłania powiadomień e-mail do adresatów powiadomień. Aby uzyskać szczegółowe informacje, zobacz  [Konfigurowanie powiadomień alertów](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) w celu tworzenia, edytowania, usuwania i rozwiązywania problemów z powiadomieniami e-mail.

## <a name="view-targeted-attack-notifications"></a>Wyświetlanie powiadomień o atakach ukierunkowanych

Po skonfigurowaniu systemu do odbierania wiadomości e-mail z powiadomieniem o Microsoft Threat Experts e-mail zaczniesz otrzymywać powiadomienia o ukierunkowanych atakach od innych osób.

1. Wybierz link w wiadomości e-mail, aby przejść do odpowiedniego kontekstu alertu na pulpicie nawigacyjnym oznaczonym **ekspertami** ds. zagrożeń.

2. Na stronie **Alerty** wybierz ten sam temat alertu, który został odebrany w wiadomości e-mail, aby wyświetlić więcej szczegółów.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Subskrybuj Microsoft Threat Experts — Eksperci na żądanie

Jeśli jesteś już klientem programu Microsoft Defender for Endpoint, możesz skontaktować się z przedstawicielem firmy Microsoft w celu zasubskrybowania usługi Microsoft Threat Experts — Experts on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Skonsultuj się z ekspertem ds. zagrożeń firmy Microsoft w sprawie podejrzanych działań chłonianych w Twojej organizacji

Możesz skontaktować się Microsoft Threat Experts z wewnątrz Microsoft 365 Defender adresowej. Eksperci mogą ułatwić zrozumienie złożonych zagrożeń i powiadomień o atakach ukierunkowanych. Nawiązyj kontakt z ekspertami, aby uzyskać szczegółowe informacje na temat alertów i zdarzeń lub porady dotyczące postępowania z naruszeniami zabezpieczeń. Uzyskaj wgląd w kontekst analizy zagrożeń opisany na pulpicie nawigacyjnym portalu.

> [!NOTE]
>
> - Zapytania alertów dotyczące dostosowanych danych analizy zagrożeń twojej organizacji nie są obecnie obsługiwane. Aby uzyskać szczegółowe informacje, skonsultuj się ze swoim zespołem ds. zabezpieczeń lub reagowania na incydenty.
> - Aby przesłać zapytanie za  pomocą formularza Skonsultuj się z ekspertem ds. zagrożeń, musisz mieć uprawnienie Zarządzanie  ustawieniami zabezpieczeń w centrum zabezpieczeń w portalu Microsoft 365 Defender.

1. Przejdź do strony portalu powiązanej z informacjami, które chcesz zbadać, na przykład **Urządzenie,** **Alert** lub **Zdarzenie**. Przed wysłaniem żądania badania upewnij się, że strona portalu powiązana z Twoim zapytaniem jest w widoku.

2. Z górnego menu wybierz pozycję **? Skonsultuj się z ekspertem ds. zagrożeń**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="The Microsoft Threat Experts Experts on Demand from the menu in the Microsoft 365 Defender portal" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Zostanie otwarty wysuwny ekran.

    Nagłówek wskaże, czy masz subskrypcję wersji próbnej, czy pełną Microsoft Threat Experts — Subskrypcję ekspertów na żądanie.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Ekran Microsoft Threat Experts subskrypcji wersji próbnej usługi Microsoft Threat Experts Experts on Demand w portalu Microsoft 365 Defender w wersji próbnej" lightbox="../../media/mte/mte-trial.png":::

    Pole **Temat badania** zostanie już wypełnione linkiem do odpowiedniej strony dla twojego żądania.

3. W następnym polu podaj wystarczającą ilość informacji, aby Microsoft Threat Experts kontekst do rozpoczęcia badania.

4. Wprowadź adres e-mail, z który chcesz się korespondować Microsoft Threat Experts.

> [!NOTE]
> Jeśli chcesz śledzić stan spraw ekspertów na żądanie za pośrednictwem centrum Usług Microsoft, strzygow się z menedżerem ds. klientów technicznych.

Ten klip wideo zawiera krótkie omówienie Centrum usług firmy Microsoft.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Przykładowe tematy badania

### <a name="alert-information"></a>Informacje alertu

- Został nam ostrzegany nowy typ alertu o nieużywanym pliku binarnym. Możemy udostępnić identyfikator alertu. Czy możesz nam powiedzieć więcej na temat tego alertu i w jaki sposób możemy go dokładniej zbadać?
- Zauważyliśmy dwie podobne ataki, w których obie próbowały wykonywać złośliwe skrypty programu PowerShell, ale generować inne alerty. Jeden z nich to "wiersz polecenia programu PowerShell", a drugi to "Wykryto złośliwy plik na podstawie wskazania dostarczonego przez usługę O365". Jaka jest różnica?
- Dzisiaj otrzymaliśmy nietypowy alert o nieprawidłowej liczbie nieudanych logowania z urządzenia wysokiego profilu użytkownika. Nie ma dodatkowych dowodów na te próby. Jak Microsoft 365 Defender zobaczyć te próby? Jakie typy logowania są monitorowane?
- Czy możesz dać więcej kontekstu lub więcej informacji na temat alertu "Obserwowane podejrzane zachowanie przez narzędzie systemowe"?
- Został obserwowany alert o tytule "Tworzenie reguły przesyłania dalej/przekierowywania". Sądzę, że to działanie jest wytęźliwe. Czy możesz mi powiedzieć, dlaczego otrzymałem alert?

### <a name="possible-machine-compromise"></a>Możliwe złamanie komputera

- Czy możesz pomóc w wyjaśnić, dlaczego na wielu urządzeniach w naszej organizacji jest wyświetlany komunikat lub alert o "Nieznanym procesie obserwowanym"? Dziękujemy za wszelkie dane wejściowe w celu wyjaśnienia, czy te wiadomości lub alerty są związane ze złośliwą aktywnością.
- Czy możesz pomóc w weryfikacji możliwego naruszenia zabezpieczeń systemu z ostatniego tygodnia? Zachowuje się podobnie jak w przypadku poprzedniego wykrywania złośliwego oprogramowania w tym samym systemie sześć miesięcy temu.

### <a name="threat-intelligence-details"></a>Szczegóły analizy zagrożeń

- Wykryliśmy wiadomość e-mail wyłudzającą informacje, która dostarczyć użytkownikowi złośliwy dokument programu Word. Dokument spowodował serię podejrzanych zdarzeń, w wyniku których wyzwoliło wiele alertów dla konkretnej rodziny złośliwego oprogramowania. Czy masz jakieś informacje o tym złośliwym oprogramowaniu? Jeśli tak, czy możesz wysłać nam link?
- Ostatnio pojawił się wpis w blogu o zagrożeń, które mają na celu kierowanie branży. Czy możesz pomóc nam zrozumieć, jaką ochronę Microsoft 365 Defender przed tym aktorem zagrożeń?
- Ostatnio obserwowaliśmy kampanię wyłudzania informacji prowadzonej wobec naszej organizacji. Czy możesz nas poinformować, czy dotyczy to konkretnie naszej firmy, czy pionowej?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft Threat Experts alertów użytkownika

- Czy Twój zespół reagowania na incydenty może pomóc nam w odpowiedzi na powiadomienie o docelowym ataków, które dostaliśmy?
- Otrzymaliśmy to powiadomienie o atakach ukierunkowanych od firmy Microsoft Threat Experts. Nie mamy własnego zespołu reagowania na incydenty. Co możemy teraz zrobić i jak możemy się z nim pomylić?
- Otrzymaliśmy powiadomienie o ukierunkowanych atakach od firmy Microsoft Threat Experts. Jakie dane możesz nam przekazać, które możemy przekazać naszemu zespołowi reagowania na incydenty?

> [!NOTE]
> Microsoft Threat Experts jest zarządzaną usługą chłoniania zagrożeń, a nie usługą reagowania na incydenty. Możesz jednak współpracować ze swoim zespołem reagowania na incydenty w celu rozwiązania problemów wymagających reakcji na incydent. Jeśli nie masz własnego zespołu reagowania na incydenty i potrzebujesz pomocy firmy Microsoft, możesz zaangażować się w zespół odpowiedzi css na zdarzenia (CIRT, CSS Incident Response Team). Mogą oni utworzyć bilet, aby pomóc w zaadresować Twoje zapytanie.

## <a name="scenario"></a>Scenariusz

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Otrzymywanie raportu o postępie w śledztwie zarządzanym

Odpowiedź od Microsoft Threat Experts będzie się różnić w zależności od zapytania. Zazwyczaj otrzymujesz jedną z następujących odpowiedzi:

- Więcej informacji jest potrzebnych do kontynuowania badania
- Do określenia kontekstu technicznego potrzebny jest plik lub kilka przykładów plików
- Badanie wymaga więcej czasu
- Początkowe informacje wystarczyły do prowadzonego badania

Jeśli ekspert prosi o dodatkowe informacje lub próbki plików, niezwykle ważne jest szybkie reagowanie w celu prowadzonego badania.

## <a name="see-also"></a>Zobacz też

- [Microsoft Threat Experts omówienie](microsoft-threat-experts.md)
