---
title: Pełne omówienie bezpiecznych linków dla Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
f1_keywords:
- "197503"
ms.date: 09/08/2021
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- ZVO160
- ZXL160
- ZPP160
- ZWD160
ms.assetid: dd6a1fef-ec4a-4cf4-a25a-bb591c5811e3
description: Dowiedz się więcej o ochronie bezpiecznych łączy w Ochrona usługi Office 365 w usłudze Defender, aby chronić organizację przed wyłudzaniem informacji i innymi atakami korzystającymi ze złośliwych adresów URL. Odnajdywanie bezpiecznych linków w usłudze Teams i wyświetlanie grafiki komunikatów bezpiecznych linków.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b3eb2ee76beb106d26d5b7b65d13c7aa0a0d5c1e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487054"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Bezpieczne linki w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Jeśli używasz Outlook.com, Microsoft 365 Family lub Microsoft 365 Personal i szukasz informacji o bezpiecznych linkach w programie Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Bezpieczne linki to funkcja w [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md), która zapewnia skanowanie adresów URL i ponowne zapisywanie przychodzących wiadomości e-mail w przepływie poczty oraz weryfikację adresów URL i linków w wiadomościach e-mail i innych lokalizacjach. Skanowanie bezpiecznych linków odbywa się oprócz zwykłych wiadomości [e-mail w ramach ochrony przed spamem](anti-spam-protection.md) i [złośliwym oprogramowaniem](anti-malware-protection.md) w przychodzących wiadomościach e-mail w Exchange Online Protection (EOP). Skanowanie bezpiecznych linków może pomóc chronić organizację przed złośliwymi linkami używanymi podczas wyłudzania informacji i innych ataków.

Obejrzyj ten krótki film wideo na temat ochrony przed złośliwymi linkami za pomocą bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGzjb]

Ochrona bezpiecznych łączy jest dostępna w następujących lokalizacjach:

- **Wiadomości e-mail**: Chociaż nie ma domyślnych zasad zabezpieczeń bezpiecznych łączy, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę bezpiecznych łączy wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach bezpiecznych łączy). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)). Można również utworzyć zasady bezpiecznych łączy, które mają zastosowanie do określonych użytkowników, grup lub domen. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

  Aby uzyskać więcej informacji na temat ochrony bezpiecznych łączy dla wiadomości e-mail, zobacz sekcję [Ustawienia bezpiecznych łączy dla wiadomości e-mail](#safe-links-settings-for-email-messages) w dalszej części tego artykułu.
  
  > [!NOTE]
  > Bezpieczne linki nie działają w folderach publicznych z włączoną obsługą poczty.
  >
  > Bezpieczne linki obsługują tylko formaty HTTP(S) i FTP.

- **Microsoft Teams**: ochrona bezpiecznych linków dla linków w konwersacjach w usłudze Teams, czatach grupowych lub kanałach jest również kontrolowana przez zasady bezpiecznych linków.

  Aby uzyskać więcej informacji na temat ochrony bezpiecznych łączy w usłudze Teams, zobacz [sekcję Ustawienia bezpiecznych linków dla usługi Microsoft Teams](#safe-links-settings-for-microsoft-teams) w dalszej części tego artykułu.

  > [!NOTE]
  > Obecnie ochrona bezpiecznych linków dla usługi Microsoft Teams nie jest dostępna w usłudze Microsoft 365 GCC High lub Microsoft 365 DoD.

- **aplikacje Office 365**: ochrona bezpiecznych linków dla aplikacji Office 365 jest dostępna w obsługiwanych aplikacjach klasycznych, mobilnych i internetowych. Ochronę bezpiecznych łączy **można skonfigurować** dla aplikacji Office 365 w ustawieniu globalnym **, które wykraczają poza** zasady bezpiecznych łączy. Aby uzyskać instrukcje, zobacz [Konfigurowanie ustawień globalnych ustawień bezpiecznych łączy w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md).

  Ochrona bezpiecznych linków dla aplikacji Office 365 jest stosowana do wszystkich użytkowników w organizacji, którzy mają licencję na Ochrona usługi Office 365 w usłudze Defender, niezależnie od tego, czy użytkownicy są uwzględnieni w aktywnych zasadach bezpiecznych linków.

  Aby uzyskać więcej informacji na temat ochrony bezpiecznych łączy w aplikacjach Office 365, zobacz sekcję [Ustawienia bezpiecznych łączy dla aplikacji Office 365](#safe-links-settings-for-office-365-apps) w dalszej części tego artykułu.

Ten artykuł zawiera szczegółowe opisy następujących typów ustawień bezpiecznych łączy:

- **Ustawienia zasad bezpiecznych łączy**: te ustawienia mają zastosowanie tylko do użytkowników uwzględnionych w określonych zasadach, a ustawienia mogą się różnić między zasadami. Te ustawienia obejmują:

  - [Ustawienia bezpiecznych łączy dla wiadomości e-mail](#safe-links-settings-for-email-messages)
  - [Ustawienia bezpiecznych linków dla usługi Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [Listy "Nie przepisuj ponownie następujących adresów URL" w zasadach bezpiecznych linków](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Globalne ustawienia bezpiecznych łączy**: te ustawienia są konfigurowane globalnie, a nie w zasadach bezpiecznych łączy. Te ustawienia obejmują:

  - [Ustawienia bezpiecznych linków dla aplikacji Office 365](#safe-links-settings-for-office-365-apps)
  - [Lista "Blokuj następujące adresy URL" dla bezpiecznych linków](#block-the-following-urls-list-for-safe-links)

W poniższej tabeli opisano scenariusze dotyczące bezpiecznych linków w usłudze Microsoft 365 i organizacjach Office 365, które obejmują Ochrona usługi Office 365 w usłudze Defender (należy pamiętać, że brak licencji nigdy nie stanowi problemu w przykładach).

|Scenariusz|Result (Wynik)|
|---|---|
|Jean jest członkiem działu marketingu. Ochrona bezpiecznych łączy dla aplikacji Office 365 jest włączona w ustawieniach globalnych bezpiecznych linków, a zasady bezpiecznych łączy, które mają zastosowanie do członków działu marketingu, istnieją. Jean otwiera prezentację programu PowerPoint w wiadomości e-mail, a następnie klika adres URL w prezentacji.|Jean jest chroniony przez bezpieczne linki. <p> Jean jest uwzględniony w zasadach bezpiecznych linków, a ochrona bezpiecznych linków dla aplikacji Office 365 jest włączona. <p> Aby uzyskać więcej informacji na temat wymagań dotyczących ochrony bezpiecznych łączy w aplikacjach Office 365, zobacz sekcję [Ustawienia bezpiecznych łączy dla aplikacji Office 365](#safe-links-settings-for-office-365-apps) w dalszej części tego artykułu.|
|Organizacja Microsoft 365 E5 Chrisa nie ma skonfigurowanych zasad bezpiecznych linków. Chris otrzymuje wiadomość e-mail od zewnętrznego nadawcy zawierającego adres URL do złośliwej witryny internetowej, którą ostatecznie klika.|Chris nie jest chroniony przez bezpieczne linki. <p> Administrator musi utworzyć co najmniej jedną zasadę bezpiecznych łączy dla każdego, aby uzyskać ochronę bezpiecznych łączy w przychodzących wiadomościach e-mail. Chris musi zostać uwzględniony w warunkach zasad, aby uzyskać ochronę bezpiecznych linków.|
|W organizacji pata żaden administrator nie utworzył żadnych zasad bezpiecznych linków, ale ochrona bezpiecznych łączy dla aplikacji Office 365 jest włączona. Pat otwiera dokument programu Word i klika adres URL w pliku.|Pat nie jest chroniony przez bezpieczne linki. <p> Mimo że ochrona bezpiecznych łączy dla aplikacji Office 365 jest włączona globalnie, pat nie jest uwzględniony w żadnych aktywnych zasadach bezpiecznych linków, więc nie można zastosować ochrony.|
|W organizacji `https://tailspintoys.com` Lee jest skonfigurowany na liście **Blokuj następujące adresy URL** w ustawieniach globalnych bezpiecznych linków. Zasady bezpiecznych łączy, w tym Lee, już istnieją. Lee otrzymuje wiadomość e-mail zawierającą adres URL `https://tailspintoys.com/aboutus/trythispage`. Lee klika adres URL.|Adres URL może zostać automatycznie zablokowany dla lee; to zależy od wpisu adresu URL na liście i klienta poczty e-mail Lee używane. Aby uzyskać więcej informacji, zobacz [sekcję "Blokuj następujące adresy URL" dla bezpiecznych linków](#block-the-following-urls-list-for-safe-links) w dalszej części tego artykułu.|
|Jamie i Julia pracują dla contoso.com. Dawno temu administratorzy skonfigurowali zasady bezpiecznych łączy, które mają zastosowanie zarówno do Jamiego, jak i Julii. Jamie wysyła wiadomość e-mail do Julii, nie wiedząc, że wiadomość e-mail zawiera złośliwy adres URL.|Julia jest chroniona przez bezpieczne linki **, jeśli** zasady bezpiecznych linków, które mają do niej zastosowanie, są skonfigurowane do stosowania do wiadomości między adresatami wewnętrznymi. Aby uzyskać więcej informacji, zobacz sekcję [Ustawienia bezpiecznych łączy dla wiadomości e-mail](#safe-links-settings-for-email-messages) w dalszej części tego artykułu.|

## <a name="safe-links-settings-for-email-messages"></a>Ustawienia bezpiecznych łączy dla wiadomości e-mail

Usługa Safe Links skanuje przychodzące wiadomości e-mail pod kątem znanych złośliwych hiperlinków. Zeskanowane adresy URL są ponownie zapisywane przy użyciu prefiksu standardowego adresu URL firmy Microsoft: `https://nam01.safelinks.protection.outlook.com`. Po ponownym napisaniu linku jest on analizowany pod kątem potencjalnie złośliwej zawartości.

Po ponownym zapisaniu adresu URL w bezpiecznych linkach adres URL pozostaje ponownie zapisywany, nawet jeśli wiadomość jest _przekazywana ręcznie_ lub odpowiadana (zarówno adresatom wewnętrznym, jak i zewnętrznym). Dodatkowe linki, które są dodawane do wiadomości przesłanej dalej lub przekazanej do wiadomości, nie są ponownie zapisywane. Jednak w przypadku _automatycznego_ przesyłania dalej według reguł skrzynki odbiorczej lub przekazywania SMTP adres URL nie zostanie ponownie zapisany w wiadomości przeznaczonej dla końcowego adresata, chyba że adresat jest również chroniony bezpiecznymi _linkami_ lub adres URL został już przepisany w poprzedniej komunikacji. Dopóki bezpieczne linki są włączone, adresy URL są nadal skanowane przed dostarczeniem, niezależnie od tego, czy zostały one przepisane, czy nie. Nieopakowane adresy URL będą również nadal sprawdzane przez wywołanie interfejsu API po stronie klienta do bezpiecznych linków w momencie kliknięcia w programie Outlook for Desktop w wersji 16.0.12513 lub nowszej.

Ustawienia zasad bezpiecznych łączy, które mają zastosowanie do wiadomości e-mail, są opisane na następującej liście:

- **Włączone: Bezpieczne linki sprawdzają listę znanych, złośliwych linków, gdy użytkownicy klikają linki w wiadomościach e-mail**: Włącza lub wyłącza skanowanie bezpiecznych linków w wiadomościach e-mail. Zalecana wartość jest zaznaczona (włączona) i powoduje wykonanie następujących akcji:
  - Skanowanie bezpiecznych łączy jest włączone w programie Outlook (C2R) w systemie Windows.
  - Adresy URL są ponownie zapisywane, a użytkownicy są kierowani przez ochronę bezpiecznych linków po kliknięciu adresów URL w komunikatach.
  - Po kliknięciu adresy URL są sprawdzane pod kątem listy znanych złośliwych adresów URL i [listy "Blokuj następujące adresy URL"](#block-the-following-urls-list-for-safe-links).
  - Adresy URL, które nie mają prawidłowej reputacji, są detonowane asynchronicznie w tle.

  Następujące ustawienia są dostępne tylko wtedy, gdy skanowanie bezpiecznych linków jest włączone w wiadomościach e-mail:

  - **Stosowanie bezpiecznych linków do wiadomości e-mail wysyłanych w organizacji**: włącza lub wyłącza skanowanie bezpiecznych łączy w wiadomościach wysyłanych między nadawcami wewnętrznymi i odbiorcami wewnętrznymi w tej samej organizacji Exchange Online. Zalecana wartość jest zaznaczona (włączone).

  - **Zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**: umożliwia skanowanie linków w czasie rzeczywistym, w tym linków w wiadomościach e-mail wskazujących na zawartość do pobrania. Zalecana wartość jest zaznaczona (włączone).

  - **Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL**:
    - Wybrane (włączone): komunikaty zawierające adresy URL są przechowywane do momentu zakończenia skanowania. Komunikaty są dostarczane dopiero po potwierdzeniu, że adresy URL są bezpieczne. Jest to zalecana wartość.
    - Nie wybrano (wyłączone): jeśli skanowanie adresu URL nie może zakończyć się, i tak dostarczyć komunikat.

  - **Nie należy ponownie pisać adresów URL, sprawdzaj tylko za pośrednictwem interfejsu API SafeLinks**: jeśli to ustawienie jest włączone, nie ma zawijania adresów URL. Bezpieczne linki są wywoływane wyłącznie za pośrednictwem interfejsów API w momencie kliknięcia adresu URL przez klientów programu Outlook, którzy ją obsługują. Wartość zalecana jest wyłączona.

- **Śledzenie kliknięć użytkownika**: włącza lub wyłącza przechowywanie bezpiecznych linków, klikając dane dla adresów URL klikniętych w wiadomościach e-mail. Zalecaną wartością jest pozostawienie wybranego ustawienia (śledzenie kliknięć użytkownika).

  Śledzenie kliknięć adresów URL dla linków w wiadomościach e-mail wysyłanych między nadawcami wewnętrznymi i odbiorcami wewnętrznymi nie jest obecnie obsługiwane.

- **Zezwalaj użytkownikom na klikanie oryginalnego adresu URL**: umożliwia lub blokuje użytkownikom klikanie [przez stronę ostrzeżenia](#warning-pages-from-safe-links) do oryginalnego adresu URL. Wartość zalecana jest wyłączona.

- **Wyświetlanie znakowania organizacji na stronach powiadomień i ostrzeżeń**: ta opcja pokazuje znakowanie organizacji na stronach ostrzegawczych. Znakowanie pomaga użytkownikom identyfikować uzasadnione ostrzeżenia, ponieważ domyślne strony ostrzegawcze firmy Microsoft są często używane przez osoby atakujące. Aby uzyskać więcej informacji na temat niestandardowego znakowania, zobacz [Dostosowywanie motywu platformy Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md).

  Aby uzyskać więcej informacji na temat zalecanych wartości dla standardowych i ścisłych ustawień zasad zasad bezpiecznych łączy, zobacz [Ustawienia zasad bezpiecznych łączy](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **Filtry adresatów**: należy określić warunki i wyjątki adresatów, które określają, do kogo mają zastosowanie zasady. Możesz użyć tych właściwości w przypadku warunków i wyjątków:
  - **Adresat jest**
  - **Domena adresata jest**
  - **Odbiorca jest członkiem**

  Warunek lub wyjątek można użyć tylko raz, ale warunek lub wyjątek może zawierać wiele wartości. Wiele wartości tego samego warunku lub wyjątku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki lub wyjątki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

  > [!IMPORTANT]
  > Wiele różnych warunków lub wyjątków nie są addytywne; są inkluzywne. Zasady są stosowane _tylko_ do tych adresatów, którzy pasują do _wszystkich_ filtrów określonych adresatów. Na przykład należy skonfigurować warunek filtru adresata w zasadach z następującymi wartościami:
  >
  > - Adresatem jest: romain@contoso.com
  > - Odbiorca jest członkiem: Kierownictwo
  >
  > Zasady są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, zasady nie są do niego stosowane.
  >
  > Podobnie, jeśli używasz tego samego filtru adresata co wyjątek od zasad, zasady nie są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, polityka nadal ma do niego zastosowanie.

- **Priorytet**: jeśli tworzysz wiele zasad, możesz określić kolejność ich stosowania. Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

  Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Jak działają bezpieczne linki w wiadomościach e-mail

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony bezpiecznych linków na adresach URL w wiadomościach e-mail:

1. Wszystkie wiadomości e-mail przechodzą przez operacje EOP, gdzie filtry protokołu internetowego (IP) i koperty, ochrona przed złośliwym oprogramowaniem oparte na podpisie, filtry chroniące przed spamem i złośliwym oprogramowaniem przed dostarczeniem wiadomości do skrzynki pocztowej adresata.

2. Użytkownik otwiera wiadomość w swojej skrzynce pocztowej i klika adres URL w wiadomości.

3. Bezpieczne linki natychmiast sprawdzają adres URL przed otwarciem witryny internetowej:

   - Jeśli adres URL zostanie uwzględniony na liście **Blokuj następujące adresy URL** , zostanie otwarte [ostrzeżenie o zablokowanym adresie URL](#blocked-url-warning) .

   - Jeśli adres URL wskazuje witrynę internetową, która została określona jako złośliwa, zostanie otwarta [złośliwa strona ostrzeżenia witryny internetowej](#malicious-website-warning) (lub inna strona ostrzeżenia).

   - Jeśli adres URL wskazuje na plik do pobrania, a ustawienie **Zastosuj adres URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących na pliki** jest włączone w zasadach, które mają zastosowanie do użytkownika, plik do pobrania jest sprawdzany.

   - Jeśli adres URL zostanie uznany za bezpieczny, zostanie otwarta witryna internetowa.

## <a name="safe-links-settings-for-microsoft-teams"></a>Ustawienia bezpiecznych linków dla usługi Microsoft Teams

Ochronę bezpiecznych łączy dla usługi Microsoft Teams można włączyć lub wyłączyć w zasadach bezpiecznych łączy. W szczególności należy użyć **ustawienia Wybierz akcję dla nieznanych lub potencjalnie złośliwych adresów URL w usłudze Microsoft Teams** . Zalecana wartość to **Włączone**.

> [!NOTE]
> Po włączeniu lub wyłączeniu ochrony bezpiecznych linków dla usługi Teams może upłynąć do 24 godzin, aż zmiana zostanie wprowadzona.
>
> Obecnie ochrona bezpiecznych linków dla usługi Microsoft Teams nie jest dostępna w usłudze Microsoft 365 GCC High lub Microsoft 365 DoD.

Następujące ustawienia zasad bezpiecznych linków, które mają zastosowanie do linków w wiadomościach e-mail, dotyczą również linków w usłudze Teams:

- **Stosowanie skanowania adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**
- **Nie śledź kliknięć użytkownika**
- **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL**

Te ustawienia zostały wcześniej wyjaśnione w [obszarze Ustawienia bezpiecznych linków dla wiadomości e-mail](#safe-links-settings-for-email-messages).

Po włączeniu ochrony bezpiecznych linków dla usługi Microsoft Teams adresy URL w usłudze Teams są sprawdzane pod kątem listy znanych złośliwych linków, gdy chroniony użytkownik kliknie link (ochrona przed kliknięciem). Adresy URL nie są ponownie zapisywane. Jeśli link zostanie uznany za złośliwy, użytkownicy będą mieli następujące środowiska:

- Jeśli link został kliknięty w konwersacji w usłudze Teams, czacie grupowym lub w kanałach, strona ostrzeżenia, jak pokazano na poniższym zrzucie ekranu, pojawi się w domyślnej przeglądarce internetowej.
- Jeśli link został kliknięty na przypiętej karcie, strona ostrzeżenia zostanie wyświetlona w interfejsie usługi Teams na tej karcie. Opcja otwarcia linku w przeglądarce internetowej jest wyłączona ze względów bezpieczeństwa.
- W zależności od tego, jak skonfigurowano ustawienie **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL** w zasadach, użytkownik będzie lub nie będzie mógł kliknąć oryginalnego adresu URL (**kontynuuj mimo to (niezalecane)** na zrzucie ekranu. Zalecamy włączenie ustawienia **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL** , aby użytkownicy nie mogli klikać oryginalnego adresu URL.

Jeśli użytkownik, który wysłał link, nie jest uwzględniony w zasadach bezpiecznych linków, w których włączono ochronę aplikacji Teams, użytkownik może kliknąć oryginalny adres URL na swoim komputerze lub urządzeniu.

:::image type="content" source="../../media/tp-safe-links-for-teams-malicious.png" alt-text="Strona Bezpieczne linki dla usługi Teams zgłasza złośliwy link" lightbox="../../media/tp-safe-links-for-teams-malicious.png":::

Kliknięcie przycisku **Wróć** na stronie ostrzeżenia spowoduje powrót użytkownika do oryginalnego kontekstu lub lokalizacji adresu URL. Jednak ponowne kliknięcie oryginalnego linku spowoduje ponowne przeskanowanie adresu URL w bezpiecznych linkach, aby strona ostrzeżenia pojawiła się ponownie.

### <a name="how-safe-links-works-in-teams"></a>Jak działają bezpieczne linki w usłudze Teams

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony bezpiecznych linków dla adresów URL w usłudze Microsoft Teams:

1. Użytkownik uruchamia aplikację Teams.

2. Platforma Microsoft 365 sprawdza, czy organizacja użytkownika obejmuje Ochrona usługi Office 365 w usłudze Microsoft Defender i czy użytkownik jest uwzględniony w aktywnych zasadach bezpiecznych linków, w których włączono ochronę aplikacji Microsoft Teams.

3. Adresy URL są weryfikowane w momencie kliknięcia użytkownika w czatach, czatach grupowych, kanałach i kartach.

## <a name="safe-links-settings-for-office-365-apps"></a>Ustawienia bezpiecznych linków dla aplikacji Office 365

Ochrona bezpiecznych linków dla aplikacji Office 365 sprawdza linki w dokumentach pakietu Office, a nie linki w wiadomościach e-mail (ale może sprawdzać linki w dołączonych dokumentach pakietu Office w wiadomościach e-mail po otwarciu dokumentu).

Ochrona bezpiecznych łączy dla aplikacji Office 365 ma następujące wymagania klienta:

- Aplikacje Microsoft 365 lub Microsoft 365 Business Premium.
  - Bieżące wersje programów Word, Excel i PowerPoint w systemach Windows, Mac lub w przeglądarce internetowej.
  - Aplikacje pakietu Office na urządzeniach z systemem iOS lub Android.
  - Program Visio w systemie Windows.
  - Program OneNote w przeglądarce internetowej.
  - Program Outlook dla systemu Windows podczas otwierania zapisanych plików EML lub MSG.

- Office 365 aplikacje są skonfigurowane do korzystania z nowoczesnego uwierzytelniania. Aby uzyskać więcej informacji, zobacz [Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich pakietu Office 2013, Office 2016 i Office 2019](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Użytkownicy są zalogowani przy użyciu kont służbowych. Aby uzyskać więcej informacji, zobacz [Logowanie do pakietu Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Ochronę bezpiecznych łączy można skonfigurować dla aplikacji Office 365 w ustawieniach globalnych bezpiecznych łączy, a nie w zasadach bezpiecznych łączy. Ochrona jest stosowana do wszystkich użytkowników w organizacji, którzy mają licencję na Ochrona usługi Office 365 w usłudze Defender, niezależnie od tego, czy użytkownicy są uwzględnieni w aktywnych zasadach bezpiecznych linków.

Następujące ustawienia bezpiecznych linków są dostępne dla aplikacji Office 365:

- **aplikacje Office 365**: włącza lub wyłącza skanowanie bezpiecznych łączy w obsługiwanych aplikacjach Office 365. Wartość domyślna i zalecana to **Włączone**.

- **Nie śledź, gdy użytkownicy klikną pozycję Bezpieczne linki**: włącza lub wyłącza przechowywanie bezpiecznych linków, klikając dane dla adresów URL klikniętych w wersjach klasycznych Word, Excel, PowerPoint i Visio. Zalecana wartość to **Wyłączone**, co oznacza, że kliknięcia użytkownika są śledzone.

- **Nie zezwalaj użytkownikom na klikanie bezpiecznych linków do oryginalnego adresu URL**: umożliwia lub blokuje użytkownikom klikanie [strony z ostrzeżeniem](#warning-pages-from-safe-links) do oryginalnego adresu URL w wersjach klasycznych Word, Excel, PowerPoint i Visio. Wartość domyślna i zalecana to **Włączone**.

Aby skonfigurować ustawienia bezpiecznych łączy dla aplikacji Office 365, zobacz [Konfigurowanie ochrony bezpiecznych łączy dla aplikacji Office 365](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Aby uzyskać więcej informacji na temat zalecanych wartości ustawień zasad standardowych i ścisłych, zobacz [Ustawienia globalne dla bezpiecznych linków](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Jak działają bezpieczne linki w aplikacjach Office 365

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony bezpiecznych linków dla adresów URL w aplikacjach Office 365. Obsługiwane aplikacje Office 365 opisano w poprzedniej sekcji.

1. Użytkownik loguje się przy użyciu konta służbowego w organizacji obejmującej Aplikacje Microsoft 365 lub Microsoft 365 Business Premium.

2. Użytkownik otwiera i klika link do dokumentu pakietu Office w obsługiwanej aplikacji pakietu Office.

3. Bezpieczne linki natychmiast sprawdzają adres URL przed otwarciem docelowej witryny internetowej:

   - Jeśli adres URL znajduje się na liście, która pomija skanowanie bezpiecznych linków (lista **Blokuj następujące adresy URL** ) zostanie otwarta [zablokowana strona ostrzeżenia adresu URL](#blocked-url-warning) .

   - Jeśli adres URL wskazuje witrynę internetową, która została określona jako złośliwa, zostanie otwarta [złośliwa strona ostrzeżenia witryny internetowej](#malicious-website-warning) (lub inna strona ostrzeżenia).

   - Jeśli adres URL wskazuje na plik do pobrania, a zasady bezpiecznych łączy, które mają zastosowanie do użytkownika, są skonfigurowane do skanowania linków do zawartości do pobrania (**zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**), plik do pobrania jest sprawdzany.

   - Jeśli adres URL zostanie uznany za bezpieczny, użytkownik zostanie przekierowany do witryny internetowej.

   - Jeśli skanowanie bezpiecznych łączy nie jest w stanie ukończyć, ochrona bezpiecznych łączy nie jest wyzwalana. W przypadku klientów klasycznych pakietu Office użytkownik zostanie ostrzeżony przed przejściem do docelowej witryny internetowej.

> [!NOTE]
> Na początku każdej sesji może upłynąć kilka sekund, aby sprawdzić, czy użytkownik ma włączone bezpieczne linki dla pakietu Office.

## <a name="block-the-following-urls-list-for-safe-links"></a>Lista "Blokuj następujące adresy URL" dla bezpiecznych linków

> [!NOTE]
> Teraz możesz zarządzać wpisami bloku adresu URL na [liście dozwolonych/zablokowanych dzierżaw](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). Lista "Blokuj następujące adresy URL" jest w trakcie wycofywania. Spróbujemy przeprowadzić migrację istniejących wpisów z listy "Blokuj następujące adresy URL", aby zablokować wpisy adresów URL na liście dozwolonych/zablokowanych dzierżaw. Komunikaty zawierające zablokowany adres URL zostaną poddane kwarantannie.

Lista **Blokuj następujące adresy URL** definiuje łącza, które są zawsze blokowane przez skanowanie bezpiecznych łączy w następujących lokalizacjach:

- Wiadomości e-mail.
- Dokumenty w aplikacjach Office 365 w systemach Windows i Mac.
- Dokumenty w pakiecie Office dla systemów iOS i Android.

Gdy użytkownik w aktywnych zasadach bezpiecznych łączy kliknie zablokowany link w obsługiwanej aplikacji, zostanie przekierowany do strony [ostrzeżenia Zablokowany adres URL](#blocked-url-warning) .

Listę adresów URL można skonfigurować w ustawieniach globalnych bezpiecznych linków. Aby uzyskać instrukcje, zobacz [Konfigurowanie listy "Blokuj następujące adresy URL"](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal).

**Uwagi**:

- Aby uzyskać prawdziwie uniwersalną listę adresów URL, które są blokowane wszędzie, zobacz [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).
- Limity listy **Blokuj następujące adresy URL** :
  - Maksymalna liczba wpisów wynosi 500.
  - Maksymalna długość wpisu to 128 znaków.
  - Wszystkie wpisy nie mogą przekraczać 10 000 znaków.
- Nie dołączaj ukośnika (`/`) na końcu adresu URL. Na przykład użyj polecenia `https://www.contoso.com`, a nie `https://www.contoso.com/`.
- Adres URL tylko do domeny (na przykład `contoso.com` lub `tailspintoys.com`) zablokuje dowolny adres URL zawierający domenę.
- Możesz zablokować poddomenę bez blokowania pełnej domeny. Na przykład `toys.contoso.com*` blokuje dowolny adres URL zawierający poddomenę, ale nie blokuje adresów URL zawierających pełną domenę `contoso.com`.
- Możesz dołączyć maksymalnie trzy symbole wieloznaczne (`*`) na wpis adresu URL.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Składnia wpisu dla listy "Blokuj następujące adresy URL"

Przykłady wartości, które można wprowadzić i ich wyników, opisano w poniższej tabeli:

|Value|Result (Wynik)|
|---|---|
|`contoso.com` <p> lub <p> `*contoso.com*`|Blokuje domenę, poddomeny i ścieżki. Na przykład `https://www.contoso.com`, `https://sub.contoso.com`, i `https://contoso.com/abc` są blokowane.|
|`https://contoso.com/a`|Bloki `https://contoso.com/a` , ale nie dodatkowe ścieżki podrzędne, takie jak `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Bloki `https://contoso.com/a` i dodatkowe ścieżki podrzędne, takie jak `https://contoso.com/a/b`.|
|`https://toys.contoso.com*`|Blokuje poddomenę (`toys` w tym przykładzie), ale zezwala na kliknięcia innych adresów URL domeny (np `https://contoso.com` . lub `https://home.contoso.com`).|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Listy "Nie przepisuj ponownie następujących adresów URL" w zasadach bezpiecznych linków

> [!NOTE]
> Celem listy "Nie przepisuj ponownie następujących adresów URL" jest pominięcie zawijania bezpiecznych łączy określonych adresów URL. Zamiast korzystać z tej listy, można teraz [tworzyć wpisy dozwolonych adresów URL na liście dozwolonych/zablokowanych dzierżaw](allow-block-urls.md#create-allow-url-entries).

Każda zasada bezpiecznych łączy zawiera listę **Nie przepisuj ponownie następujących adresów URL** , których można użyć do określenia adresów URL, które nie są ponownie zapisywane przez skanowanie bezpiecznych linków. Innymi słowy, lista umożliwia użytkownikom uwzględnionym w zasadach dostęp do określonych adresów URL, które w przeciwnym razie zostałyby zablokowane przez bezpieczne linki. Różne listy można skonfigurować w różnych zasadach bezpiecznych łączy. Przetwarzanie zasad zostaje zatrzymane po zastosowaniu do użytkownika pierwszych zasad (prawdopodobnie o najwyższym priorytecie). Dlatego tylko jeden **nie należy ponownie pisać poniższej listy adresów URL** jest stosowany do użytkownika, który jest uwzględniony w wielu aktywnych zasad bezpiecznych linków.

Aby dodać wpisy do listy w nowych lub istniejących zasadach bezpiecznych łączy, zobacz [Tworzenie zasad bezpiecznych łączy](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) lub [Modyfikowanie zasad bezpiecznych łączy](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Uwagi**:

- Następujący klienci nie rozpoznają listy **Nie przepisuj ponownie następujących adresów URL** w zasadach bezpiecznych łączy. Użytkownikom uwzględnionym w zasadach można zablokować dostęp do adresów URL na podstawie wyników skanowania bezpiecznych łączy w tych klientach:
  - Microsoft Teams
  - Aplikacje internetowe pakietu Office

  Aby uzyskać prawdziwie uniwersalną listę adresów URL dozwolonych wszędzie, zobacz [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md). Należy jednak pamiętać, że dodane adresy URL nie zostaną wykluczone z ponownego pisania bezpiecznych linków, ponieważ należy to zrobić w zasadach bezpiecznych łączy.

- Rozważ dodanie często używanych wewnętrznych adresów URL do listy, aby ulepszyć środowisko użytkownika. Jeśli na przykład masz usługi lokalne, takie jak Skype dla firm lub SharePoint, możesz dodać te adresy URL, aby wykluczyć je ze skanowania.
- Jeśli w zasadach bezpiecznych łączy nie zapisano już **ponownie następujących wpisów adresów URL** , zapoznaj się z listami i dodaj symbole wieloznaczne zgodnie z wymaganiami. Na przykład lista zawiera wpis podobny `https://contoso.com/a` do tego, a później decydujesz się na uwzględnienie ścieżek podrzędnych, takich jak `https://contoso.com/a/b`. Zamiast dodawać nowy wpis, dodaj symbol wieloznaczny do istniejącego wpisu, aby stał się `https://contoso.com/a/*`.
- Możesz dołączyć maksymalnie trzy symbole wieloznaczne (`*`) na wpis adresu URL. Symbole wieloznaczne jawnie zawierają prefiksy lub poddomeny. Na przykład wpis `contoso.com` nie jest taki sam jak `*.contoso.com/*`, ponieważ `*.contoso.com/*` umożliwia użytkownikom odwiedzanie domen podrzędnych i ścieżek w określonej domenie.
- Jeśli adres URL używa automatycznego przekierowania dla protokołu HTTP do protokołu HTTPS (na przykład przekierowania 302 dla `http://www.contoso.com` polecenia do `https://www.contoso.com`), i spróbujesz wprowadzić zarówno wpisy HTTP, jak i HTTPS dla tego samego adresu URL na liście, możesz zauważyć, że drugi wpis adresu URL zastępuje pierwszy wpis adresu URL. To zachowanie nie występuje, jeśli wersje HTTP i HTTPS adresu URL są całkowicie oddzielone.
- Nie należy określać http:// ani https:// (czyli contoso.com), aby wykluczyć wersje HTTP i HTTPS.
- `*.contoso.com`**nie** obejmuje contoso.com, więc należy wykluczyć zarówno w celu objęcia określonej domeny, jak i wszystkich domen podrzędnych.
- `contoso.com/*` obejmuje **tylko** contoso.com, więc nie ma potrzeby wykluczania obu `contoso.com` i `contoso.com/*`; wystarczy `contoso.com/*` .
- Aby wykluczyć wszystkie iteracje domeny, potrzebne są dwa wpisy wykluczeń; `contoso.com/*` i `*.contoso.com/*`. Są one łączone w celu wykluczenia zarówno protokołu HTTP, jak i HTTPS, domeny głównej contoso.com i wszystkich domen podrzędnych, a także dowolnej lub nie kończącej się części (na przykład omówione są zarówno contoso.com, jak i contoso.com/vdir1).

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Składnia wpisu dla listy "Nie przepisuj ponownie następujących adresów URL"

Przykłady wartości, które można wprowadzić i ich wyników, opisano w poniższej tabeli:

|Value|Result (Wynik)|
|---|---|
|`contoso.com`|Zezwala na dostęp do `https://contoso.com` domen podrzędnych lub ścieżek, ale nie do nich.|
|`*.contoso.com/*`|Zezwala na dostęp do domeny, poddomen i ścieżek (na przykład , `https://www.contoso.com``https://www.contoso.com`, , `https://maps.contoso.com`lub `https://www.contoso.com/a`). <p> Ten wpis jest z natury lepszy niż `*contoso.com*`, ponieważ nie zezwala na potencjalnie fałszywe witryny, takie jak `https://www.falsecontoso.com` lub `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Zezwala na dostęp do `https://contoso.com/a`ścieżek podrzędnych, takich jak , `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Umożliwia dostęp do `https://contoso.com/a` ścieżek podrzędnych i takich jak `https://contoso.com/a/b`|

## <a name="warning-pages-from-safe-links"></a>Strony ostrzegawcze z bezpiecznych linków

Ta sekcja zawiera przykłady różnych stron ostrzegawczych, które są wyzwalane przez ochronę bezpiecznych łączy po kliknięciu adresu URL.

Należy pamiętać, że zaktualizowano kilka stron ostrzegawczych. Jeśli nie widzisz jeszcze zaktualizowanych stron, wkrótce to zrobisz. Zaktualizowane strony zawierają nowy schemat kolorów, więcej szczegółów i możliwość kontynuowania pracy z witryną pomimo danego ostrzeżenia i zaleceń.

### <a name="scan-in-progress-notification"></a>Skanowanie w toku — powiadomienie

Klikniętego adresu URL jest skanowany przez bezpieczne linki. Może być konieczne odczekanie kilku chwil przed ponownym wypróbowaniem linku.

:::image type="content" source="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png" alt-text="Powiadomienie o skanowaniu linku" lightbox="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png":::

Oryginalna strona powiadomień wyglądała następująco:

:::image type="content" source="../../media/04368763-763f-43d6-94a4-a48291d36893.png" alt-text="Link jest skanowany— powiadomienie" lightbox="../../media/04368763-763f-43d6-94a4-a48291d36893.png":::

### <a name="suspicious-message-warning"></a>Ostrzeżenie o podejrzanym komunikacie

Klikniętego adresu URL w wiadomości e-mail, która jest podobna do innych podejrzanych wiadomości. Zalecamy dwukrotne sprawdzenie wiadomości e-mail przed przejściem do witryny.

:::image type="content" source="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png" alt-text="Kliknięcie linku z ostrzeżenia o podejrzanym komunikacie" lightbox="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png":::

### <a name="phishing-attempt-warning"></a>Ostrzeżenie o próbie wyłudzania informacji

Klikniętego adresu URL w wiadomości e-mail, która została zidentyfikowana jako atak phishingowy. W związku z tym wszystkie adresy URL w wiadomości e-mail są blokowane. Zalecamy, aby nie przechodzić do witryny.

:::image type="content" source="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png" alt-text="Ostrzeżenie informujące o kliknięciu linku z wiadomości wyłudzającej informacje" lightbox="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png":::

### <a name="malicious-website-warning"></a>Ostrzeżenie o złośliwej witrynie internetowej

Kliknięty adres URL wskazuje witrynę, która została zidentyfikowana jako złośliwa. Zalecamy, aby nie przechodzić do witryny.

:::image type="content" source="../../media/058883c8-23f0-4672-9c1c-66b084796177.png" alt-text="Ostrzeżenie informujące o tym, że witryna internetowa jest klasyfikowana jako złośliwa" lightbox="../../media/058883c8-23f0-4672-9c1c-66b084796177.png":::

Oryginalna strona ostrzeżenia wyglądała następująco:

:::image type="content" source="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png" alt-text="Oryginalne ostrzeżenie informujące o tym, że witryna internetowa jest sklasyfikowana jako złośliwa" lightbox="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png":::

### <a name="blocked-url-warning"></a>Ostrzeżenie o zablokowanym adresie URL

Kliknięty adres URL został ręcznie zablokowany przez administratora w organizacji (lista **Blokuj następujące adresy URL** w ustawieniach globalnych bezpiecznych linków). Link nie został zeskanowany przez bezpieczne linki, ponieważ został ręcznie zablokowany.

Istnieje kilka powodów, dla których administrator ręcznie blokuje określone adresy URL. Jeśli uważasz, że witryna nie powinna być zablokowana, skontaktuj się z administratorem.

:::image type="content" source="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png" alt-text="Ostrzeżenie informujące, że witryna internetowa została zablokowana przez administratora" lightbox="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png":::

Oryginalna strona ostrzeżenia wyglądała następująco:

:::image type="content" source="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png" alt-text="Oryginalne ostrzeżenie informujące o tym, że witryna internetowa została zablokowana według zasad adresów URL organizacji" lightbox="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png":::

### <a name="error-warning"></a>Ostrzeżenie o błędzie

Wystąpił jakiś błąd i nie można otworzyć adresu URL.

:::image type="content" source="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png" alt-text="Nie można załadować ostrzeżenia informującego o stronie, do którą próbujesz uzyskać dostęp" lightbox="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png":::

Oryginalna strona ostrzeżenia wyglądała następująco:

:::image type="content" source="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png" alt-text="Ostrzeżenie informujące o tym, że nie można załadować strony internetowej" lightbox="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png":::
