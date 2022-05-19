---
title: Pełne omówienie linków Sejf dla Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Dowiedz się więcej o ochronie linków Sejf w Ochrona usługi Office 365 w usłudze Defender, aby chronić organizację przed wyłudzaniem informacji i innymi atakami korzystającymi ze złośliwych adresów URL. Odnajdywanie linków Teams Sejf i wyświetlanie grafiki komunikatów Sejf Links.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0aef211b91ef406926720f8c50e4af457d07eaab
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535113"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Jeśli używasz witryny Outlook.com, Microsoft 365 Family lub Microsoft 365 Personal i szukasz informacji o bezpiecznych linkach w Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Links to funkcja w [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md), która umożliwia skanowanie i ponowne zapisywanie adresów URL przychodzących wiadomości e-mail w przepływie poczty oraz weryfikację adresów URL i linków w wiadomościach e-mail i innych lokalizacjach. Sejf Skanowanie linków odbywa się oprócz zwykłych wiadomości [e-mail](anti-spam-protection.md) dla ruchu [przychodzącego i chroniącego przed spamem i chroniącego przed złośliwym oprogramowaniem](anti-malware-protection.md) w Exchange Online Protection (EOP). Sejf Skanowanie linków może pomóc chronić organizację przed złośliwymi linkami używanymi podczas wyłudzania informacji i innych ataków.

Sejf Ochrona linków jest dostępna w następujących lokalizacjach:

- **Wiadomości e-mail**: Mimo że nie ma domyślnych zasad Sejf Łącza, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę Sejf Łącza wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Łączy). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)). Można również utworzyć zasady linków Sejf, które mają zastosowanie do określonych użytkowników, grup lub domen. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

  Aby uzyskać więcej informacji na temat ochrony Sejf Linki dla wiadomości e-mail, zobacz sekcję [ustawienia linków Sejf dla wiadomości e-mail](#safe-links-settings-for-email-messages) w dalszej części tego artykułu.
  
  > [!NOTE]
  > Sejf Łącza nie działają w folderach publicznych z włączoną obsługą poczty.
  >
  > Sejf Links obsługuje tylko formaty HTTP(S) i FTP.

- **Microsoft Teams**: ochrona linków Sejf linków w Teams konwersacjach, czatach grupowych lub kanałach jest również kontrolowana przez zasady linków Sejf.

  Aby uzyskać więcej informacji na temat ochrony linków Sejf w Teams, zobacz sekcję [ustawienia linków Sejf dla Microsoft Teams](#safe-links-settings-for-microsoft-teams) w dalszej części tego artykułu.

- **aplikacje Office 365**: ochrona linków Sejf dla aplikacji Office 365 jest dostępna w obsługiwanych aplikacjach klasycznych, mobilnych i internetowych. Ochronę łączy Sejf dla aplikacji Office 365 **można skonfigurować** w ustawieniu globalnym **, które wykraczają poza** zasady linków Sejf. Aby uzyskać instrukcje, zobacz [Konfigurowanie ustawień globalnych dla ustawień linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md).

  Sejf Ochrona linków dla aplikacji Office 365 jest stosowana do wszystkich użytkowników w organizacji, którzy mają licencję na Ochrona usługi Office 365 w usłudze Defender, niezależnie od tego, czy użytkownicy są uwzględnieni w aktywnych zasadach linków Sejf.

  Aby uzyskać więcej informacji na temat ochrony linków Sejf w aplikacjach Office 365, zobacz sekcję [ustawienia linków Sejf dla aplikacji Office 365](#safe-links-settings-for-office-365-apps) w dalszej części tego artykułu.

Ten artykuł zawiera szczegółowe opisy następujących typów ustawień linków Sejf:

- **Ustawienia w zasadach linków Sejf**: te ustawienia mają zastosowanie tylko do użytkowników uwzględnionych w określonych zasadach, a ustawienia mogą się różnić między zasadami. Te ustawienia obejmują:

  - [ustawienia linków Sejf dla wiadomości e-mail](#safe-links-settings-for-email-messages)
  - [ustawienia linków Sejf dla Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [Listy "Nie należy ponownie pisać następujących adresów URL" w zasadach linków Sejf](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Ustawienia łączy Sejf** globalnych: te ustawienia są konfigurowane globalnie, a nie w zasadach linków Sejf. Te ustawienia obejmują:

  - [ustawienia linków Sejf dla aplikacji Office 365](#safe-links-settings-for-office-365-apps)
  - [Lista "Blokuj następujące adresy URL" dla linków Sejf](#block-the-following-urls-list-for-safe-links)

W poniższej tabeli opisano scenariusze dotyczące linków Sejf w organizacjach Microsoft 365 i Office 365, które obejmują Ochrona usługi Office 365 w usłudze Defender (należy pamiętać, że brak licencji nigdy nie stanowi problemu w przykładach).

|Scenariusz|Result (Wynik)|
|---|---|
|Jean jest członkiem działu marketingu. Sejf Ochrona linków dla aplikacji Office 365 jest włączona w ustawieniach globalnych linków Sejf, a zasady linków Sejf, które mają zastosowanie do członków działu marketingu, istnieją. Jean otwiera prezentację PowerPoint w wiadomości e-mail, a następnie klika adres URL w prezentacji.|Jean jest chroniony przez Sejf Links. <p> Jean jest uwzględniony w zasadach linków Sejf, a ochrona linków Sejf dla aplikacji Office 365 jest włączona. <p> Aby uzyskać więcej informacji na temat wymagań dotyczących ochrony linków Sejf w aplikacjach Office 365, zobacz sekcję [ustawienia linków Sejf dla aplikacji Office 365](#safe-links-settings-for-office-365-apps) w dalszej części tego artykułu.|
|Organizacja Microsoft 365 E5 Chrisa nie ma skonfigurowanych zasad linków Sejf. Chris otrzymuje wiadomość e-mail od zewnętrznego nadawcy zawierającego adres URL do złośliwej witryny internetowej, którą ostatecznie klika.|Chris nie jest chroniony przez Sejf Links. <p> Administrator musi utworzyć co najmniej jedną zasadę linków Sejf, aby każda osoba miała dostęp do ochrony Sejf Łącza w przychodzących wiadomościach e-mail. Chris musi zostać uwzględniony w warunkach zasad, aby uzyskać ochronę Sejf Linki.|
|W organizacji pata żaden administrator nie utworzył żadnych zasad linków Sejf, ale ochrona linków Sejf dla aplikacji Office 365 jest włączona. Pat otwiera dokument programu Word i klika adres URL w pliku.|Pat nie jest chroniony przez linki Sejf. <p> Mimo że ochrona linków Sejf dla aplikacji Office 365 jest włączona globalnie, pat nie jest uwzględniony w żadnych aktywnych zasadach Sejf Łącza, więc nie można zastosować ochrony.|
|W organizacji `https://tailspintoys.com` Lee jest skonfigurowany na liście **Blokuj następujące adresy URL** w ustawieniach globalnych dla linków Sejf. Zasady linków Sejf, w tym Lee, już istnieją. Lee otrzymuje wiadomość e-mail zawierającą adres URL `https://tailspintoys.com/aboutus/trythispage`. Lee klika adres URL.|Adres URL może zostać automatycznie zablokowany dla lee; to zależy od wpisu adresu URL na liście i klienta poczty e-mail Lee używane. Aby uzyskać więcej informacji, zobacz [sekcję "Blokuj następujące adresy URL", aby uzyskać Sejf Linki](#block-the-following-urls-list-for-safe-links) w dalszej części tego artykułu.|
|Jamie i Julia pracują dla contoso.com. Dawno temu administratorzy skonfigurowali zasady Sejf Linki, które mają zastosowanie zarówno do Jamiego, jak i Julii. Jamie wysyła wiadomość e-mail do Julii, nie wiedząc, że wiadomość e-mail zawiera złośliwy adres URL.|Julia jest chroniona przez Sejf Links **, jeśli** zasady linków Sejf, które mają do niej zastosowanie, są skonfigurowane do stosowania do wiadomości między odbiorcami wewnętrznymi. Aby uzyskać więcej informacji, zobacz sekcję [ustawienia linków Sejf dla wiadomości e-mail](#safe-links-settings-for-email-messages) w dalszej części tego artykułu.|

## <a name="safe-links-settings-for-email-messages"></a>ustawienia linków Sejf dla wiadomości e-mail

Sejf Linki skanują przychodzące wiadomości e-mail pod kątem znanych złośliwych hiperłączy. Zeskanowane adresy URL są ponownie zapisywane przy użyciu prefiksu standardowego adresu URL firmy Microsoft: `https://nam01.safelinks.protection.outlook.com`. Po ponownym napisaniu linku jest on analizowany pod kątem potencjalnie złośliwej zawartości.

Po ponownym zapisaniu adresu URL przez Sejf Links adres URL pozostaje ponownie zapisywany, nawet jeśli wiadomość jest _przekazywana ręcznie_ lub odpowiadana (zarówno adresatom wewnętrznym, jak i zewnętrznym). Dodatkowe linki, które są dodawane do wiadomości przesłanej dalej lub przekazanej do wiadomości, nie są ponownie zapisywane. Jednak w przypadku _automatycznego_ przesyłania dalej według reguł skrzynki odbiorczej lub przekazywania SMTP adres URL nie zostanie ponownie zapisany w wiadomości przeznaczonej dla końcowego adresata, _chyba że_ adresat jest również chroniony przez Sejf Links lub adres URL został już przepisany w poprzedniej komunikacji. Dopóki Sejf łącza są włączone, adresy URL są nadal skanowane przed dostarczeniem, niezależnie od tego, czy zostały one przepisane, czy nie. Nieopakowane adresy URL będą nadal sprawdzane przez wywołanie interfejsu API po stronie klienta w celu Sejf Łącza w momencie kliknięcia w Outlook dla programu Desktop w wersji 16.0.12513 lub nowszej.

Ustawienia w zasadach linków Sejf, które mają zastosowanie do wiadomości e-mail, są opisane na następującej liście:

- **On: Sejf Links checks a list of known, malicious links when users click links in email: Enables or disables Sejf Links scanning in email messages .On: Sejf Links checks a list of known, malicious links when users click links in email: Enables or disables Sejf Links scanning in email messages (Włączone: Sejf Linki sprawdzają listę znanych złośliwych linków, gdy użytkownicy klikają linki w wiadomościach e-mail**: włącza lub wyłącza skanowanie linków Zalecana wartość jest zaznaczona (włączona) i powoduje wykonanie następujących akcji:
  - skanowanie linków Sejf jest włączone w Outlook (C2R) na Windows.
  - Adresy URL są ponownie zapisywane, a użytkownicy są kierowani przez ochronę Sejf Linki po kliknięciu adresów URL w komunikatach.
  - Po kliknięciu adresy URL są sprawdzane pod kątem listy znanych złośliwych adresów URL i [listy "Blokuj następujące adresy URL"](#block-the-following-urls-list-for-safe-links).
  - Adresy URL, które nie mają prawidłowej reputacji, są detonowane asynchronicznie w tle.

  Następujące ustawienia są dostępne tylko wtedy, gdy skanowanie linków Sejf jest włączone w wiadomościach e-mail:

  - **Zastosuj Sejf Łącza do wiadomości e-mail wysyłanych w organizacji**: włącza lub wyłącza skanowanie Sejf Linków w wiadomościach wysyłanych między nadawcami wewnętrznymi i odbiorcami wewnętrznymi w tej samej organizacji Exchange Online. Zalecana wartość jest zaznaczona (włączone).

  - **Zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**: umożliwia skanowanie linków w czasie rzeczywistym, w tym linków w wiadomościach e-mail wskazujących na zawartość do pobrania. Zalecana wartość jest zaznaczona (włączone).

  - **Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL**:
    - Wybrane (włączone): komunikaty zawierające adresy URL są przechowywane do momentu zakończenia skanowania. Komunikaty są dostarczane dopiero po potwierdzeniu, że adresy URL są bezpieczne. Jest to zalecana wartość.
    - Nie wybrano (wyłączone): jeśli skanowanie adresu URL nie może zakończyć się, i tak dostarczyć komunikat.

  - **Nie należy ponownie pisać adresów URL, sprawdzaj tylko za pośrednictwem interfejsu API SafeLinks**: jeśli to ustawienie jest włączone, nie ma zawijania adresów URL. Sejf Łącza są wywoływane wyłącznie za pośrednictwem interfejsów API w momencie kliknięcia adresu URL przez Outlook klientów, którzy go obsługują. Wartość zalecana jest wyłączona.

- **Śledzenie kliknięć użytkownika**: włącza lub wyłącza przechowywanie Sejf Łącza klikają dane dla adresów URL klikniętych w wiadomościach e-mail. Zalecaną wartością jest pozostawienie wybranego ustawienia (śledzenie kliknięć użytkownika).

  Śledzenie kliknięć adresów URL dla linków w wiadomościach e-mail wysyłanych między nadawcami wewnętrznymi i odbiorcami wewnętrznymi nie jest obecnie obsługiwane.

- **Zezwalaj użytkownikom na klikanie oryginalnego adresu URL**: umożliwia lub blokuje użytkownikom klikanie [przez stronę ostrzeżenia](#warning-pages-from-safe-links) do oryginalnego adresu URL. Wartość zalecana jest wyłączona.

- **Wyświetlanie znakowania organizacji na stronach powiadomień i ostrzeżeń**: ta opcja pokazuje znakowanie organizacji na stronach ostrzegawczych. Znakowanie pomaga użytkownikom identyfikować uzasadnione ostrzeżenia, ponieważ domyślne strony ostrzegawcze firmy Microsoft są często używane przez osoby atakujące. Aby uzyskać więcej informacji na temat niestandardowego znakowania, zobacz [Dostosowywanie motywu Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md).

  Aby uzyskać więcej informacji o zalecanych wartościach standardowych i ścisłych ustawień zasad dla zasad Sejf Łącza, zobacz [Sejf Ustawienia zasad łączy](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **Filtry adresatów**: należy określić warunki i wyjątki adresatów, które określają, do kogo mają zastosowanie zasady. Możesz użyć tych właściwości w przypadku warunków i wyjątków:
  - **Adresat jest**
  - **Domena adresata jest**
  - **Odbiorca jest członkiem**

  Warunek lub wyjątek można użyć tylko raz, ale warunek lub wyjątek może zawierać wiele wartości. Wiele wartości tego samego warunku lub wyjątku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki lub wyjątki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

- **Priorytet**: jeśli tworzysz wiele zasad, możesz określić kolejność ich stosowania. Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

  Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Jak działają linki Sejf w wiadomościach e-mail

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony linków Sejf na adresach URL w wiadomościach e-mail:

1. Wszystkie wiadomości e-mail przechodzą przez operacje EOP, gdzie filtry protokołu internetowego (IP) i koperty, ochrona przed złośliwym oprogramowaniem oparte na podpisie, filtry chroniące przed spamem i złośliwym oprogramowaniem przed dostarczeniem wiadomości do skrzynki pocztowej adresata.

2. Użytkownik otwiera wiadomość w swojej skrzynce pocztowej i klika adres URL w wiadomości.

3. Sejf Linki natychmiast sprawdzają adres URL przed otwarciem witryny internetowej:

   - Jeśli adres URL zostanie uwzględniony na liście **Blokuj następujące adresy URL** , zostanie otwarte [ostrzeżenie o zablokowanym adresie URL](#blocked-url-warning) .

   - Jeśli adres URL wskazuje witrynę internetową, która została określona jako złośliwa, zostanie otwarta [złośliwa strona ostrzeżenia witryny internetowej](#malicious-website-warning) (lub inna strona ostrzeżenia).

   - Jeśli adres URL wskazuje na plik do pobrania, a ustawienie **Zastosuj adres URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących na pliki** jest włączone w zasadach, które mają zastosowanie do użytkownika, plik do pobrania jest sprawdzany.

   - Jeśli adres URL zostanie uznany za bezpieczny, zostanie otwarta witryna internetowa.

## <a name="safe-links-settings-for-microsoft-teams"></a>ustawienia linków Sejf dla Microsoft Teams

Ochronę Sejf Łącza dla Microsoft Teams można włączyć lub wyłączyć w zasadach linków Sejf. W szczególności należy użyć **ustawienia Wybierz akcję dla nieznanych lub potencjalnie złośliwych adresów URL w Microsoft Teams**. Zalecana wartość to **Włączone**.

> [!NOTE]
> Po włączeniu lub wyłączeniu ochrony Sejf Łącza dla Teams może upłynąć do 24 godzin, aż zmiana zostanie wprowadzona.

Następujące ustawienia w zasadach linków Sejf, które mają zastosowanie do linków w wiadomościach e-mail, dotyczą również linków w Teams:

- **Stosowanie skanowania adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**
- **Nie śledź kliknięć użytkownika**
- **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL**

Te ustawienia zostały wcześniej wyjaśnione w [ustawieniach linków Sejf dla wiadomości e-mail](#safe-links-settings-for-email-messages).

Po włączeniu ochrony Sejf Łącza dla Microsoft Teams adresy URL w Teams są sprawdzane pod kątem listy znanych złośliwych linków, gdy chroniony użytkownik kliknie link (ochrona przed kliknięciem). Adresy URL nie są ponownie zapisywane. Jeśli link zostanie uznany za złośliwy, użytkownicy będą mieli następujące środowiska:

- Jeśli link został kliknięty w Teams konwersacji, czatu grupowego lub kanałów, strona ostrzeżenia, jak pokazano na poniższym zrzucie ekranu, pojawi się w domyślnej przeglądarce internetowej.
- Jeśli link został kliknięty na przypiętej karcie, strona ostrzeżenia zostanie wyświetlona w interfejsie Teams na tej karcie. Opcja otwarcia linku w przeglądarce internetowej jest wyłączona ze względów bezpieczeństwa.
- W zależności od tego, jak skonfigurowano ustawienie **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL** w zasadach, użytkownik będzie lub nie będzie mógł kliknąć oryginalnego adresu URL (**kontynuuj mimo to (niezalecane)** na zrzucie ekranu. Zalecamy włączenie ustawienia **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL** , aby użytkownicy nie mogli klikać oryginalnego adresu URL.

Jeśli użytkownik, który wysłał link, nie jest uwzględniony w zasadach linków Sejf, w których włączono ochronę Teams, użytkownik może kliknąć oryginalny adres URL na swoim komputerze lub urządzeniu.

:::image type="content" source="../../media/tp-safe-links-for-teams-malicious.png" alt-text="Linki Sejf do strony Teams zgłaszania złośliwego linku" lightbox="../../media/tp-safe-links-for-teams-malicious.png":::

Kliknięcie przycisku **Wróć** na stronie ostrzeżenia spowoduje powrót użytkownika do oryginalnego kontekstu lub lokalizacji adresu URL. Jednak ponowne kliknięcie oryginalnego linku spowoduje ponowne przeskanowanie adresu URL Sejf Links, aby strona ostrzeżenia pojawiła się ponownie.

### <a name="how-safe-links-works-in-teams"></a>Jak działają linki Sejf w Teams

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony linków Sejf dla adresów URL w Microsoft Teams:

1. Użytkownik uruchamia aplikację Teams.

2. Microsoft 365 sprawdza, czy organizacja użytkownika obejmuje Ochrona usługi Office 365 w usłudze Microsoft Defender i czy użytkownik jest uwzględniony w aktywnych zasadach linków Sejf, w których włączono ochronę Microsoft Teams.

3. Adresy URL są weryfikowane w momencie kliknięcia użytkownika w czatach, czatach grupowych, kanałach i kartach.

## <a name="safe-links-settings-for-office-365-apps"></a>ustawienia linków Sejf dla aplikacji Office 365

Sejf Ochrona linków dla aplikacji Office 365 sprawdza linki w dokumentach Office, a nie linki w wiadomościach e-mail (ale może sprawdzać linki w dołączonych dokumentach Office w wiadomościach e-mail po otwarciu dokumentu).

Ochrona linków Sejf dla aplikacji Office 365 ma następujące wymagania klienta:

- Aplikacje Microsoft 365 lub Microsoft 365 Business Premium.
  - Bieżące wersje programu Word, Excel i PowerPoint na Windows, Mac lub w przeglądarce internetowej.
  - Office aplikacje na urządzeniach iOS lub Android.
  - Visio na Windows.
  - OneNote w przeglądarce internetowej.
  - Outlook dla Windows podczas otwierania zapisanych plików EML lub MSG.

- Office 365 aplikacje są skonfigurowane do korzystania z nowoczesnego uwierzytelniania. Aby uzyskać więcej informacji, zobacz [Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013, Office 2016 i Office 2019](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Użytkownicy są zalogowani przy użyciu kont służbowych. Aby uzyskać więcej informacji, zobacz [Logowanie się do Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Ochronę łączy Sejf dla aplikacji Office 365 należy skonfigurować w ustawieniach globalnych linków Sejf, a nie w zasadach Sejf Łącza. Ochrona jest stosowana do wszystkich użytkowników w organizacji, którzy mają licencję na Ochrona usługi Office 365 w usłudze Defender, niezależnie od tego, czy użytkownicy są uwzględnieni w aktywnych zasadach linków Sejf.

Następujące ustawienia linków Sejf są dostępne dla aplikacji Office 365:

- **aplikacje Office 365**: włącza lub wyłącza skanowanie linków Sejf w obsługiwanych aplikacjach Office 365. Wartość domyślna i zalecana to **Włączone**.

- **Nie śledź, gdy użytkownicy klikają Sejf Łącza**: włącza lub wyłącza przechowywanie Sejf Łącza klikają dane dla adresów URL klikniętych w wersjach klasycznych Programu Word, Excel, PowerPoint i Visio. Zalecana wartość to **Wyłączone**, co oznacza, że kliknięcia użytkownika są śledzone.

- **Nie zezwalaj użytkownikom na klikanie bezpiecznych linków do oryginalnego adresu URL**: umożliwia lub blokuje użytkownikom klikanie [strony ostrzeżenia](#warning-pages-from-safe-links) do oryginalnego adresu URL w wersjach klasycznych Word, Excel, PowerPoint i Visio. Wartość domyślna i zalecana to **Włączone**.

Aby skonfigurować ustawienia linków Sejf dla aplikacji Office 365, zobacz [Konfigurowanie ochrony linków Sejf dla aplikacji Office 365](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Aby uzyskać więcej informacji na temat zalecanych wartości dla standardowych i ścisłych ustawień zasad, zobacz [Ustawienia globalne dla linków Sejf](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Jak działają linki Sejf w aplikacjach Office 365

Na wysokim poziomie poniżej przedstawiono sposób działania ochrony Sejf Linków dla adresów URL w aplikacjach Office 365. Obsługiwane aplikacje Office 365 opisano w poprzedniej sekcji.

1. Użytkownik loguje się przy użyciu konta służbowego w organizacji obejmującej Aplikacje Microsoft 365 lub Microsoft 365 Business Premium.

2. Użytkownik otwiera i klika link do dokumentu Office w obsługiwanym aplikacja pakietu Office.

3. Sejf Linki natychmiast sprawdzają adres URL przed otwarciem docelowej witryny internetowej:

   - Jeśli adres URL znajduje się na liście, która pomija skanowanie linków Sejf (lista **Blokuj następujące adresy URL**) zostanie otwarta [zablokowana strona ostrzeżenia adresu URL](#blocked-url-warning).

   - Jeśli adres URL wskazuje witrynę internetową, która została określona jako złośliwa, zostanie otwarta [złośliwa strona ostrzeżenia witryny internetowej](#malicious-website-warning) (lub inna strona ostrzeżenia).

   - Jeśli adres URL wskazuje na plik do pobrania, a zasady linków Sejf, które mają zastosowanie do użytkownika, są skonfigurowane do skanowania linków do zawartości do pobrania (**zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**), plik do pobrania jest sprawdzany.

   - Jeśli adres URL zostanie uznany za bezpieczny, użytkownik zostanie przekierowany do witryny internetowej.

   - Jeśli skanowanie linków Sejf nie jest w stanie ukończyć, ochrona Sejf Łącza nie zostanie wyzwolona. W Office klientów klasycznych użytkownik zostanie ostrzeżony przed przejściem do docelowej witryny internetowej.

> [!NOTE]
> Może upłynąć kilka sekund na początku każdej sesji, aby sprawdzić, czy użytkownik ma Sejf Łącza dla Office włączone.

## <a name="block-the-following-urls-list-for-safe-links"></a>Lista "Blokuj następujące adresy URL" dla linków Sejf

Lista **Blokuj następujące adresy URL** definiuje łącza, które są zawsze blokowane przez skanowanie linków Sejf w następujących lokalizacjach:

- Wiadomości e-mail.
- Dokumenty w aplikacjach Office 365 na komputerach Windows i Mac.
- Dokumenty w Office dla iOS i Android.

Gdy użytkownik w aktywnych zasadach Sejf Łącza kliknie zablokowany link w obsługiwanej aplikacji, zostanie przekierowany do strony [ostrzeżenia Zablokowany adres URL](#blocked-url-warning).

Listę adresów URL można skonfigurować w ustawieniach globalnych dla linków Sejf. Aby uzyskać instrukcje, zobacz [Konfigurowanie listy "Blokuj następujące adresy URL"](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal).

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

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Listy "Nie należy ponownie pisać następujących adresów URL" w zasadach linków Sejf

> [!NOTE]
> Jeśli Twoja organizacja korzysta z zasad Sejf Links, **listy Nie przepisuj ponownie następujących adresów URL** są jedyną obsługiwaną metodą testów wyłudzania informacji innych firm.

Każda zasada Sejf Łącza zawiera listę **Nie przepisuj ponownie następujących adresów URL**, których można użyć do określenia adresów URL, które nie są ponownie zapisywane przez skanowanie linków Sejf. Innymi słowy, lista umożliwia użytkownikom uwzględnionym w zasadach dostęp do określonych adresów URL, które w przeciwnym razie zostałyby zablokowane przez Sejf Łącza. Różne listy można skonfigurować w różnych zasadach linków Sejf. Przetwarzanie zasad zostaje zatrzymane po zastosowaniu do użytkownika pierwszych zasad (prawdopodobnie o najwyższym priorytecie). Dlatego do użytkownika, który jest uwzględniony w wielu aktywnych zasadach linków Sejf linków, jest stosowana tylko jedna lista Nie **przepisuj ponownie następujących adresów URL**.

Aby dodać wpisy do listy w nowych lub istniejących zasadach łączy Sejf, zobacz [Tworzenie zasad łączy Sejf](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) lub [Modyfikowanie zasad łączy Sejf](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Uwagi**:

- Następujący klienci nie rozpoznają listy **Nie przepisuj ponownie następujących adresów URL** w zasadach Sejf Łącza. Użytkownikom uwzględnionym w zasadach można zablokować dostęp do adresów URL na podstawie wyników skanowania linków Sejf w tych klientach:
  - Microsoft Teams
  - Office aplikacje internetowe

  Aby uzyskać prawdziwie uniwersalną listę adresów URL dozwolonych wszędzie, zobacz [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md). Należy jednak pamiętać, że dodane adresy URL nie zostaną wykluczone z ponownego zapisywania linków Sejf, ponieważ należy to zrobić w zasadach Sejf Łącza.

- Rozważ dodanie często używanych wewnętrznych adresów URL do listy, aby ulepszyć środowisko użytkownika. Jeśli na przykład masz usługi lokalne, takie jak Skype dla firm lub SharePoint, możesz dodać te adresy URL, aby wykluczyć je ze skanowania.
- Jeśli w zasadach Sejf Łącza nie zostały już **ponownie zapisane następujące wpisy adresów URL**, zapoznaj się z listami i dodaj symbole wieloznaczne zgodnie z wymaganiami. Na przykład lista zawiera wpis podobny `https://contoso.com/a` do tego, a później decydujesz się na uwzględnienie ścieżek podrzędnych, takich jak `https://contoso.com/a/b`. Zamiast dodawać nowy wpis, dodaj symbol wieloznaczny do istniejącego wpisu, aby stał się `https://contoso.com/a/*`.
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

## <a name="warning-pages-from-safe-links"></a>Strony ostrzeżenia z linków Sejf

Ta sekcja zawiera przykłady różnych stron ostrzegawczych wyzwalanych przez ochronę Sejf Łącza po kliknięciu adresu URL.

Należy pamiętać, że zaktualizowano kilka stron ostrzegawczych. Jeśli nie widzisz jeszcze zaktualizowanych stron, wkrótce to zrobisz. Zaktualizowane strony zawierają nowy schemat kolorów, więcej szczegółów i możliwość kontynuowania pracy z witryną pomimo danego ostrzeżenia i zaleceń.

### <a name="scan-in-progress-notification"></a>Skanowanie w toku — powiadomienie

Klikniętego adresu URL jest skanowany przez Sejf Łącza. Może być konieczne odczekanie kilku chwil przed ponownym wypróbowaniem linku.

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

Kliknięty adres URL został ręcznie zablokowany przez administratora w organizacji (lista **Blokuj następujące adresy URL** w ustawieniach globalnych dla linków Sejf). Link nie został zeskanowany przez Sejf Links, ponieważ został ręcznie zablokowany.

Istnieje kilka powodów, dla których administrator ręcznie blokuje określone adresy URL. Jeśli uważasz, że witryna nie powinna być zablokowana, skontaktuj się z administratorem.

:::image type="content" source="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png" alt-text="Ostrzeżenie informujące, że witryna internetowa została zablokowana przez administratora" lightbox="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png":::

Oryginalna strona ostrzeżenia wyglądała następująco:

:::image type="content" source="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png" alt-text="Oryginalne ostrzeżenie informujące o tym, że witryna internetowa została zablokowana według zasad adresów URL organizacji" lightbox="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png":::

### <a name="error-warning"></a>Ostrzeżenie o błędzie

Wystąpił jakiś błąd i nie można otworzyć adresu URL.

:::image type="content" source="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png" alt-text="Nie można załadować ostrzeżenia informującego o stronie, do którą próbujesz uzyskać dostęp" lightbox="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png":::

Oryginalna strona ostrzeżenia wyglądała następująco:

:::image type="content" source="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png" alt-text="Ostrzeżenie informujące o tym, że nie można załadować strony internetowej" lightbox="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png":::
