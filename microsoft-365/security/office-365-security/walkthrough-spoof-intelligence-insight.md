---
title: Zarządzanie fałszywymi nadawcami przy użyciu zasad ochrony przed fałszerami i wglądu w fałsz
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak używać zasad ochrony przed fałszerami oraz informacji o fałszerce, aby zezwalać na wykrytych sfałszowanych nadawców lub blokować je.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: f433c93d9bba13822cf84ff8740f86d95cf2befe
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471346"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Zarządzanie fałszywymi nadawcami przy użyciu zasad ochrony przed fałszerami i informacjami o fałszerce w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> W tym artykule opisano starsze, zamieniane środowisko zarządzania fałszywymi nadawcami (zasady ochrony przed  fałszerami na stronie Zasady ochrony przed **spamem**). Aby uzyskać więcej informacji o nowym środowisko (na karcie **Fałszowanie** na liście zezwalań/zablokowanych dzierżaw), zobacz Szczegółowe informacje dotyczące fałszowania [w u usługi EOP](learn-about-spoof-intelligence.md).

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online przychodzące wiadomości e-mail są automatycznie chronione przed fałszowaniem przez usługę EOP od października 2018 r. Firma EOP **korzysta z ochrony** przed wyłudzaniem informacji fałszerczych w organizacji. Aby uzyskać więcej informacji, zobacz [Ochrona przed fałszerko-fałszergami w uciekaniu poczty eOP](anti-spoofing-protection.md).

Domyślne (i **tylko) zasady** ochrony przed fałszerami pomagają zagwarantować, że sfałszowane wiadomości e-mail wysyłane przez legalnych nadawców nie będą na bieżąco z filtrami spamu usługi EOP, chroniąc użytkowników przed spamem i atakami wyłudzania informacji. Przy użyciu szczegółowych informacji o  analizie fałsz można także szybko ustalić, którzy nadawcy zewnętrzni na pewno wysyłają nieuwierzytane wiadomości e-mail (wiadomości z domen, które nie przechodzą testów SPF, DKIM lub DMARC).

Do zarządzania analizą spoof intelligence można używać w portalu usługi Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online  skrzynki pocztowe).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby zmodyfikować zasady ochrony przed fałszerami albo włączyć lub wyłączyć analizę fałszowania,  musisz być członkiem grup ról Zarządzanie organizacją lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do zasad ochrony przed fałszerami, musisz być członkiem  grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Opcje ochrony przed fałszerami są opisane w tece Ustawienia [fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

- W zasadach ochrony przed wyłudzaniem informacji można włączać, wyłączać i konfigurować ustawienia ochrony przed fałszerami. Aby uzyskać instrukcje dotyczące subskrypcji, zobacz jeden z następujących tematów:

  - [Skonfiguruj zasady ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md).
  - [Skonfiguruj zasady ochrony przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

- Aby uzyskać informacje o naszych zalecanych ustawieniach ochrony przed fałszerami, zobacz Ustawienia zasad ochrony przed wyłudzaniem informacji [eOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Zarządzanie fałszywymi nadawcami

Istnieją dwa sposoby zezwalania na spoofed nadawców i blokowania ich:

- [Korzystanie z zasad ochrony przed fałszerami](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Korzystanie z szczegółowych informacji o analizie fałszowania](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Zarządzanie fałszywymi nadawcami w zasadach ochrony przed fałszerami

> [!IMPORTANT]
> W tym artykule opisano starsze, zamieniane środowisko zarządzania fałszywymi nadawcami (zasady ochrony przed  fałszerami na stronie Zasady ochrony przed **spamem**). Aby uzyskać więcej informacji o nowym środowisko (na karcie **Fałszowanie** na liście zezwalań/zablokowanych dzierżaw), zobacz Szczegółowe informacje dotyczące fałszowania [w u usługi EOP](learn-about-spoof-intelligence.md).

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz pozycję Zasady **ochrony przed fałszerami** , klikając nazwę.

   :::image type="content" source="../../media/anti-spam-settings-spoof-intelligence-policy.png" alt-text="Opcja wyboru zasad ochrony przed fałszerami" lightbox="../../media/anti-spam-settings-spoof-intelligence-policy.png":::

3. W **wyświetlonym wysuwanych zasadach** ochrony przed fałszerami zaznacz jedną z następujących opcji:
   - **Pokaż nadawców, którzy już przejrzeli**
   - **Przeglądanie nowych nadawców**

4. Na **wysuwanych oknach** Zdecyduj, czy ci nadawcy mogą fałszować wyświetlanych użytkowników wybierz jedną z następujących kart:
   - **Twoje domeny**: Nadawcy podszywając się pod użytkowników w domenach wewnętrznych.
   - **Domeny zewnętrzne**: Nadawcy podszywając się pod użytkowników w domenach zewnętrznych.

5. Kliknij ikonę ![Rozwiń.](../../media/scc-expand-icon.png) w kolumnie **Może fałszować?** i zaznacz jedną z następujących opcji:
   - **Tak**: zezwalaj na fałszywy nadawcę.
   - **Nie**: oznacz wiadomość jako fałszywą. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

   :::image type="content" source="../../media/spoof-allow-block-flyout.png" alt-text="Wysuwają się informacje o fałszywych nadawcach oraz o tym, czy nadawca może fałszować" lightbox="../../media/spoof-allow-block-flyout.png":::

   Kolumny i wartości, które widzisz, zostały objaśnione na poniższej liście:

   - **Fałszywy użytkownik**: sfałszowane konto użytkownika. Jest to nadawca wiadomości w adresie Od wyświetlanym `5322.From` w klientach poczty e-mail. Ważność tego adresu nie jest sprawdzana przez SPF.
     - Wartość na **karcie Domeny** zawiera jeden adres e-mail lub, jeśli źródłowy serwer poczty e-mail fałszuje wiele kont użytkowników, zawiera **więcej niż jeden adres**.
     - Na karcie **Domeny zewnętrzne** wartość zawiera domenę fałszywego użytkownika, a nie pełny adres e-mail.

   - **Infrastruktura wysyłania**: domena znaleziona w rekordzie wyszukiwania odwrotnego DNS (PTR) adresu IP źródłowego serwera poczty e-mail. Jeśli źródłowy adres IP nie ma rekordu PTR, \<source IP\>wówczas infrastruktura wysyłania jest identyfikowana jako /24 (na przykład 192.168.100.100/24).

     Aby uzyskać więcej informacji o źródłach wiadomości i nadawcach wiadomości, zobacz [Omówienie standardów wiadomości e-mail](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **# wiadomości**: liczba wiadomości z infrastruktury wysyłania do Organizacji, które zawierają określonego sfałszowane nadawcę lub nadawców w ciągu ostatnich 30 dni.

   - **# skarg użytkowników**: Skargi złożone przez użytkowników wobec tego nadawcy w ciągu ostatnich 30 dni. Skargi zazwyczaj mają postać przesyłania wiadomości-śmieci do firmy Microsoft.

   - **Wynik uwierzytelniania**: Jedna z następujących wartości:
      - **Minął**: Nadawca przeszedł testy uwierzytelniania poczty e-mail (SPF lub DKIM).
      - **Niepowodzenie**: Nadawca nie sprawdza uwierzytelniania nadawcy usługi EOP.
      - **Nieznany**: wynik tych testów nie jest znany.

   - **Ostatnio widziane**: Data ostatniej daty, kiedy wiadomość została odebrana z infrastruktury wysyłania zawierającej fałszywego użytkownika.

   - **Może fałszować?**: Wartości, które widzisz poniżej, to:
     - **Tak**: Wiadomości z połączenia sfałszowanej infrastruktury użytkownika i infrastruktury wysyłania są dozwolone i nie są traktowane jako sfałszowane wiadomości e-mail.
     - **Nie**: Wiadomości z połączenia spoofed użytkownika i infrastruktury wysyłania są oznaczane jako fałszywe. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to Przenoszenie wiadomości **do folderu Wiadomości-śmieci**). Aby uzyskać więcej informacji, zobacz następną sekcję.

     - **Niektórzy użytkownicy** (**tylko karta Domeny** ): Infrastruktura wysyłania fałszuje wielu użytkowników, gdzie niektórzy fałszywi użytkownicy są dozwolone, a inni nie. Użyj karty **Szczegóły** , aby wyświetlić określone adresy.

6. Po zakończeniu kliknij przycisk **Zapisz**.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Zarządzanie fałszywymi nadawcami za pomocą programu PowerShell

> [!IMPORTANT]
> W tym artykule opisano starsze, zamieniane środowisko zarządzania fałszywymi nadawcami (zasady ochrony przed  fałszerami na stronie Zasady ochrony przed **spamem**). Aby uzyskać więcej informacji o nowym środowisko (na karcie **Fałszowanie** na liście zezwalań/zablokowanych dzierżaw), zobacz Szczegółowe informacje dotyczące fałszowania [w u usługi EOP](learn-about-spoof-intelligence.md).

Aby wyświetlać dozwolonych i zablokowanych nadawców w analizie fałszowania, użyj następującej składni:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Ten przykład zwraca szczegółowe informacje o wszystkich nadawcach, którzy mogą fałszować użytkowników w Twoich domenach.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Aby skonfigurować dozwolonych i zablokowanych nadawców w analizie fałszowania, wykonaj następujące czynności:

1. Przechwyć bieżącą listę wykrytych fałszywych nadawców, zapisując wynik polecenia cmdlet **Get-PhishFilterPolicy** w pliku CSV, uruchamiając następujące polecenie:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Edytuj plik CSV, aby dodać lub zmodyfikować następujące wartości:
   - **Nadawca** (domena w rekordzie PTR serwera źródłowego lub adres IP/24)
   - **SpoofedUser**: Jedna z następujących wartości:
     - Adres e-mail użytkownika wewnętrznego.
     - Domena poczty e-mail użytkownika zewnętrznego.
     - Pusta wartość wskazująca, że chcesz zablokować lub zezwolić na wszystkie sfałszowane wiadomości od określonego nadawcy **, niezależnie** od tego, czy adres e-mail jest sfałszowany.
   - **AllowedToSpoof** (Tak lub Nie)
   - **SpoofType** (wewnętrzny lub zewnętrzny)

   Zapisz plik, przeczytaj go i zapisz `$UpdateSpoofedSenders` zawartość jako zmienną o nazwie, uruchamiając następujące polecenie:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Za pomocą zmiennej `$UpdateSpoofedSenders` skonfiguruj zasady ochrony przed fałszerami, uruchamiając następujące polecenie:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Zarządzanie fałszywymi nadawcami w szczegółowych informacjach o analizie fałszerów

> [!IMPORTANT]
> W tym artykule opisano starsze, zamieniane środowisko zarządzania fałszywymi nadawcami (zasady ochrony przed  fałszerami na stronie Zasady ochrony przed **spamem**). Aby uzyskać więcej informacji o nowym środowisko (na karcie **Fałszowanie** na liście zezwalań/zablokowanych dzierżaw), zobacz Szczegółowe informacje dotyczące fałszowania [w u usługi EOP](learn-about-spoof-intelligence.md).

1. W Centrum zabezpieczeń & zgodności przejdź do strony **Pulpit nawigacyjny zarządzania zagrożeniami**\>.

2. W **Szczegółowe informacje** wiersza poszukaj jednego z następujących elementów:

   - **Prawdopodobnie fałszowane domeny w** ciągu ostatnich siedmiu dni: Ta informacja wskazuje, że analiza fałszerska jest włączona (jest domyślnie włączona).
   - **Włącz ochronę przed fałszerami**: Ta informacja wskazuje, że analiza przed fałszerami jest wyłączona, a kliknięcie tej informacji umożliwia włączenie ochrony przed fałszerami.

3. Szczegółowe informacje na pulpicie nawigacyjnym są podane w ten sposób:

   :::image type="content" source="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png" alt-text="Analiza fałszowania" lightbox="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png":::

   Ten wgląd ma dwa tryby:

   - **Tryb analizy**: Jeśli funkcja fałszowania informacji jest włączona, możesz zobaczyć, na ile wiadomości w ciągu ostatnich siedmiu dni wpłynieliśmy na funkcje analizy fałszowania.
   - **Co zrobić, jeśli** tryb: Jeśli analiza fałszywa jest wyłączona, w szczegółowych informacjach można sprawdzić, na ile wiadomości w ciągu ostatnich siedmiu dni wpłyniełyby nasze funkcje analizy fałszowania.

   W obu tych sposób sfałszowane domeny wyświetlane w szczegółowych informacjach są podzielone na dwie **kategorie: Podejrzane** domeny i Nieza **podejrzanych domen**.

   - **Podejrzane domeny**:
     - Zaufana fałszowanie **:** Na podstawie historycznych wzorców wysyłania i oceny reputacji domen mamy pewność, że domeny podszywają się pod inne domeny, a wiadomości z tych domen najprawdopodobniej są złośliwe.
     - **Umiarkowane** zaufanie: Na podstawie historycznych wzorców wysyłania i oceny reputacji domen mamy umiarkowaną pewność, że domeny podszywają się pod inne domeny i że wiadomości wysyłane z tych domen są zgodne z prawem. Wyniki fałszywie dodatnie są bardziej prawdopodobne w tej kategorii niż błędy ufności.
   - **Podejrzane domeny**: Domena nie sprawdza jawnego uwierzytelniania poczty e-mail [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md). Jednak ta domena przeszła niejawne testy uwierzytelniania wiadomości e-mail ([uwierzytelnianie złożone](email-validation-and-authentication.md#composite-authentication)). W wyniku tego nie zostały podjęte żadne działania zapobiegające podszywce się nad wiadomością.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Wyświetlanie szczegółowych informacji o podejrzanych i niesuspipijących domenach

1. Na stronie Spoof intelligence insight (Analiza fałszowania) kliknij pozycję **Suspicious domains** (Podejrzane domeny) lub **Non-suspicious domains** (Podejrzane domeny), aby przejść do strony **Spoof intelligence insight (Analiza fałszowania** ). Strona **Spoof Intelligence insight (** Analiza fałszu) zawiera następujące informacje:

   - **Spoofed domain** (Fałszowana domena): domena fałszywego użytkownika wyświetlana w polu **Od w** klientach poczty e-mail. Ten adres jest również nazywany adresem `5322.From` .
   - **Infrastruktura**: ta infrastruktura jest również znana _jako infrastruktura wysyłania_. Domena znaleziona w odwrotnym odnośniku DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail. Jeśli źródłowy adres IP nie ma rekordu PTR, \<source IP\>wówczas infrastruktura wysyłania jest identyfikowana jako /24 (na przykład 192.168.100.100/24).
   - **Liczba wiadomości**: Liczba wiadomości z infrastruktury wysyłania do Organizacji, które zawierają określoną sfałszowaną domenę w ciągu ostatnich 7 dni.
   - **Ostatnio widziane**: Ostatnia data, kiedy wiadomość została odebrana z infrastruktury wysyłania zawierającej fałszywą domenę.
   - **Fałsz typ**: Ta wartość to **Zewnętrzna**.
   - **Może fałszować?**: Wartości, które widzisz poniżej, to:
     - **Tak**: Wiadomości z połączenia domeny sfałszowanej domeny użytkownika i infrastruktury wysyłania są dozwolone i nie są traktowane jako sfałszowane wiadomości e-mail.
     - **Nie**: Wiadomości z połączenia domeny użytkownika o sfałszowanej domenie i infrastruktury wysyłania są oznaczane jako fałszywe. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to Przenoszenie wiadomości **do folderu Wiadomości-śmieci**).

2. Wybierz element z listy, aby wyświetlić szczegóły pary domena/infrastruktura wysyłania w wysuwanych informacjach. Informacje te obejmują:
   - Dlaczego go przygotowaliśmy.
   - Co należy zrobić.
   - Podsumowanie domeny.
   - WhoIs data about the sender.
   - Podobne wiadomości, które zobaczyliśmy w Twojej dzierżawie od tego samego nadawcy.

   W tym miejscu możesz również dodać lub usunąć parę infrastruktury domen/wysyłania z listy Dozwolonych **do fałszowania** nadawców listy dozwolonych. Wystarczy odpowiednio ustawić przełącznik.

   :::image type="content" source="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png" alt-text="Domena w okienku szczegółów informacji dotyczących fałszowania informacji" lightbox="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png":::

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy skonfigurowano analizę fałszowania nadawców, którzy są dozwolone i nie mogą fałszować, należy wykonać dowolną z następujących czynności:

- **Współpraca za & e-mail** \> **Zasady & reguł** \> **Zasady zagrożeń** \> **Ochrona przed spamem**  \>  \>   \> w sekcji Zasady zasady ochrony przed fałszerami zaznacz pole wyboru Pokaż nadawców,  którzy już przejrzeli, wybierz kartę Twoje domeny  lub domeny zewnętrzne i sprawdź dla nadawcy wartość Dozwolone do fałszowania?

- W programie PowerShell uruchom następujące polecenia, aby wyświetlić nadawców, którzy mają prawo i nie mogą podszywać się:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- W programie PowerShell uruchom następujące polecenie, aby wyeksportować listę wszystkich sfałszowanych nadawców do pliku CSV:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
