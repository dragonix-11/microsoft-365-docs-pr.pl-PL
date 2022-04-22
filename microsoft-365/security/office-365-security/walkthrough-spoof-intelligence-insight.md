---
title: Zarządzanie fałszywymi nadawcami przy użyciu zasad analizy fałszowania i fałszowania szczegółowych informacji wywiadowczych
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
description: Administratorzy mogą dowiedzieć się, jak używać zasad analizy fałszowania i analizy fałszowania, aby zezwalać na wykryte sfałszowane nadawcy lub blokować ich blokowanie.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 59f52e7fe10030283601aad86a1aa49ed91255ab
ms.sourcegitcommit: 363bdc517bd2564c6420cf21f352e97079f950e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2022
ms.locfileid: "65031828"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Zarządzanie sfałszowanymi nadawcami przy użyciu zasad analizy fałszowania i fałszowania analizy w ramach EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> W tym artykule opisano starsze, sfałszowane środowisko zarządzania nadawcą, które jest zastępowane ( **zasady analizy podróbek** na stronie **Zasady ochrony przed spamem** ). Aby uzyskać więcej informacji o nowym środowisku (na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców), zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach operacji EOP](learn-about-spoof-intelligence.md)).

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych przychodzące wiadomości e-mail są automatycznie chronione przed fałszowaniem przez EOP od października 2018 r. W ramach ogólnej ochrony organizacji przed wyłudzaniem informacji EOP używa **analizy fałszowania** . Aby uzyskać więcej informacji, zobacz [Ochrona przed fałszowaniem w ramach EOP](anti-spoofing-protection.md).

Domyślne (i jedyne) **zasady analizy podróbek** pomagają zagwarantować, że sfałszowana wiadomość e-mail wysłana przez legalnych nadawców nie zostanie wplątana w filtry spamu EOP, chroniąc jednocześnie użytkowników przed atakami spamu lub wyłudzania informacji. Możesz również użyć **analizy fałszowania,** aby szybko określić, którzy zewnętrzni nadawcy legalnie wysyłają Ci nieuwierzytelnioną wiadomość e-mail (wiadomości z domen, które nie przechodzą testów SPF, DKIM lub DMARC).

Analizą fałszowania można zarządzać w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online  skrzynki pocztowe).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby zmodyfikować zasady analizy fałszowania lub włączyć lub wyłączyć analizę fałszowania, musisz być członkiem 
    -   **Zarządzanie organizacją**
    -   **Administrator zabezpieczeń** <u>i</u> **konfiguracja tylko do wyświetlania** lub **zarządzanie organizacją tylko do wyświetlania**.
  - Aby uzyskać dostęp tylko do odczytu do zasad analizy fałszowania, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Opcje analizy fałszowania zostały opisane w temacie [Spoof settings in anti-phishing policies (Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings)).

- Ustawienia analizy fałszowania można włączać, wyłączać i konfigurować w zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać instrukcje oparte na subskrypcji, zobacz jeden z następujących tematów:

  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

- Aby zapoznać się z naszymi zalecanymi ustawieniami analizy podróbek, zobacz [Ustawienia zasad ochrony przed wyłudzaniem informacji](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) w usłudze EOP.

## <a name="manage-spoofed-senders"></a>Zarządzanie sfałszowanymi nadawcami

Istnieją dwa sposoby zezwalania na fałszowanie nadawców i blokowania ich:

- [Korzystanie z zasad analizy fałszowania](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Korzystanie ze szczegółowych informacji na temat fałszowania analizy](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Zarządzanie fałszywymi nadawcami w zasadach analizy fałszowania

> [!IMPORTANT]
> W tym artykule opisano starsze, sfałszowane środowisko zarządzania nadawcą, które jest zastępowane ( **zasady analizy podróbek** na stronie **Zasady ochrony przed spamem** ). Aby uzyskać więcej informacji o nowym środowisku (na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców), zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach operacji EOP](learn-about-spoof-intelligence.md)).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz pozycję **Zasady analizy fałszowania** , klikając nazwę.

   :::image type="content" source="../../media/anti-spam-settings-spoof-intelligence-policy.png" alt-text="Opcja wybrania zasad analizy fałszowania" lightbox="../../media/anti-spam-settings-spoof-intelligence-policy.png":::

3. Na wyświetlonym wysuwu **zasad analizy fałszowania** należy dokonać jednego z następujących wyborów:
   - **Pokaż nadawców, których już przeglądałem**
   - **Przejrzyj nowych nadawców**

4. Na wyświetlonym menu wysuwowym **Zdecyduj, czy ci nadawcy mogą podszywać się pod użytkowników** , wybierz jedną z następujących kart:
   - **Twoje domeny**: nadawcy podszywają się pod użytkowników w domenach wewnętrznych.
   - **Domeny zewnętrzne: nadawcy** podszywają się pod użytkowników w domenach zewnętrznych.

5. Kliknij ikonę ![Rozwiń.](../../media/scc-expand-icon.png) w kolumnie **Dozwolone fałszowanie?** i wykonaj jedną z następujących opcji:
   - **Tak**: zezwalaj na sfałszowanego nadawcę.
   - **Nie**: Oznacz wiadomość jako sfałszowaną. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

   :::image type="content" source="../../media/spoof-allow-block-flyout.png" alt-text="Wysuwane fałszowanie nadawców i to, czy nadawca może podszywać się pod nadawcę" lightbox="../../media/spoof-allow-block-flyout.png":::

   Widoczne kolumny i wartości zostały wyjaśnione na następującej liście:

   - **Sfałszowany użytkownik**: konto użytkownika, które jest sfałszowane. Jest to nadawca wiadomości z adresu Od (znanego `5322.From` również jako adres), który jest wyświetlany w klientach poczty e-mail. Ważność tego adresu nie jest sprawdzana przez SPF.
     - Na **karcie Twoje domeny** wartość zawiera pojedynczy adres e-mail lub jeśli źródłowy serwer poczty e-mail podszywa się pod wiele kont użytkowników, zawiera **więcej niż jeden**.
     - Na **karcie Domeny zewnętrzne** wartość zawiera domenę sfałszowanego użytkownika, a nie pełny adres e-mail.

   - **Infrastruktura wysyłania**: domena znaleziona w odwrotnym wyszukiwaniu DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail. Jeśli źródłowy adres IP nie ma rekordu PTR, infrastruktura wysyłania jest identyfikowana jako \<source IP\>/24 (na przykład 192.168.100.100/24).

     Aby uzyskać więcej informacji na temat źródeł wiadomości i nadawców wiadomości, zobacz [Omówienie standardów wiadomości e-mail](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **Liczba komunikatów**: liczba komunikatów z infrastruktury wysyłania do organizacji, które zawierają określonego sfałszowanego nadawcę lub nadawcę w ciągu ostatnich 30 dni.

   - **Liczba skarg użytkowników**: Skargi złożone przez użytkowników wobec tego nadawcy w ciągu ostatnich 30 dni. Skargi są zwykle w formie przesyłania wiadomości-śmieci do firmy Microsoft.

   - **Wynik uwierzytelniania**: Jedna z następujących wartości:
      - **Przekazano**: nadawca przeszedł testy uwierzytelniania poczty e-mail nadawcy (SPF lub DKIM).
      - **Niepowodzenie**: nadawca nie może sprawdzić uwierzytelniania nadawcy EOP.
      - **Nieznany**: wynik tych testów nie jest znany.

   - **Ostatnio widziany**: ostatnia data odebrania komunikatu z infrastruktury wysyłania zawierającej sfałszowanego użytkownika.

   - **Dozwolone do fałszowania?**: Wyświetlane tutaj wartości to:
     - **Tak**: Wiadomości z kombinacji sfałszowanego użytkownika i infrastruktury wysyłania są dozwolone i nie są traktowane jako sfałszowane wiadomości e-mail.
     - **Nie**: Komunikaty z kombinacji sfałszowanego użytkownika i infrastruktury wysyłania są oznaczone jako sfałszowane. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to **Przenieś wiadomość do folderu Wiadomości-śmieci**). Aby uzyskać więcej informacji, zobacz następną sekcję.

     - **Niektórzy użytkownicy** (tylko karta **Twoje domeny** ): infrastruktura wysyłania podszywa się pod wielu użytkowników, w przypadku których niektórzy sfałszowali użytkownicy są dozwoloni, a inni nie. Użyj karty **Szczegółowe** , aby wyświetlić określone adresy.

6. Po zakończeniu kliknij przycisk **Zapisz**.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Zarządzanie fałszowaniem nadawców przy użyciu programu PowerShell

> [!IMPORTANT]
> W tym artykule opisano starsze, sfałszowane środowisko zarządzania nadawcą, które jest zastępowane ( **zasady analizy podróbek** na stronie **Zasady ochrony przed spamem** ). Aby uzyskać więcej informacji o nowym środowisku (na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców), zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach operacji EOP](learn-about-spoof-intelligence.md)).

Aby wyświetlić dozwolonych i zablokowanych nadawców w analizie fałszowania, użyj następującej składni:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Ten przykład zwraca szczegółowe informacje o wszystkich nadawcach, którzy mogą podszywać się pod użytkowników w domenach.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Aby skonfigurować dozwolonych i zablokowanych nadawców w analizie fałszowania, wykonaj następujące kroki:

1. Przechwyć bieżącą listę wykrytych sfałszowanych nadawców, zapisując dane wyjściowe polecenia cmdlet **Get-PhishFilterPolicy** w pliku CSV, uruchamiając następujące polecenie:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Edytuj plik CSV, aby dodać lub zmodyfikować następujące wartości:
   - **Nadawca** (domena w rekordzie PTR serwera źródłowego lub adres IP/24)
   - **SpoofedUser**: jedna z następujących wartości:
     - Wewnętrzny adres e-mail użytkownika.
     - Domena poczty e-mail użytkownika zewnętrznego.
     - Pusta wartość wskazująca, że chcesz zablokować lub zezwolić na wszystkie sfałszowane wiadomości od określonego **nadawcy**, niezależnie od sfałszowanego adresu e-mail.
   - **AllowedToSpoof** (Tak lub Nie)
   - **SpoofType** (wewnętrzny lub zewnętrzny)

   Zapisz plik, odczytaj plik i zapisz zawartość jako zmienną o nazwie `$UpdateSpoofedSenders` , uruchamiając następujące polecenie:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Użyj zmiennej `$UpdateSpoofedSenders` , aby skonfigurować zasady analizy fałszowania, uruchamiając następujące polecenie:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Zarządzanie sfałszowanymi nadawcami w szczegółowych informacjach na temat fałszowania danych wywiadowczych

> [!IMPORTANT]
> W tym artykule opisano starsze, sfałszowane środowisko zarządzania nadawcą, które jest zastępowane ( **zasady analizy podróbek** na stronie **Zasady ochrony przed spamem** ). Aby uzyskać więcej informacji o nowym środowisku (na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców), zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach operacji EOP](learn-about-spoof-intelligence.md)).

1. W Centrum zgodności & zabezpieczeń przejdź do **pulpitu nawigacyjnego** **zarządzania zagrożeniami**\>.

2. W **wierszu Szczegółowe informacje** poszukaj jednego z następujących elementów:

   - **Prawdopodobnie sfałszowane domeny w ciągu ostatnich siedmiu dni**: ta analiza wskazuje, że analiza fałszowania jest włączona (jest domyślnie włączona).
   - **Włącz ochronę przed fałszowaniem**: ta analiza wskazuje, że inteligencja fałszowania jest wyłączona, a kliknięcie szczegółowych informacji umożliwia włączenie analizy podróbek.

3. Szczegółowe informacje na pulpicie nawigacyjnym zawierają następujące informacje:

   :::image type="content" source="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png" alt-text="Szczegółowe informacje na temat fałszowania danych wywiadowczych" lightbox="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png":::

   Ten wgląd w szczegółowe informacje ma dwa tryby:

   - **Tryb szczegółowych informacji**: jeśli włączono analizę fałszowania, szczegółowe informacje pokazują, ile komunikatów zostało dotkniętych przez nasze możliwości analizy fałszowania w ciągu ostatnich siedmiu dni.
   - **Co zrobić, jeśli tryb**: Jeśli analiza fałszowania jest wyłączona, szczegółowe informacje pokazują, ile wiadomości *miałoby* wpływ na nasze możliwości analizy fałszowania w ciągu ostatnich siedmiu dni.

   Tak czy inaczej, sfałszowane domeny wyświetlane w analizie są podzielone na dwie kategorie: **podejrzane domeny** i **domeny niepodejrzane**.

   - **Podejrzane domeny**:
     - **Fałszerstwo o wysokim poziomie zaufania**: na podstawie historycznych wzorców wysyłania i oceny reputacji domen jesteśmy bardzo pewni, że domeny podszywają się, a komunikaty z tych domen są bardziej narażone na złośliwość.
     - **Umiarkowane fałszowanie zaufania**: Na podstawie historycznych wzorców wysyłania i oceny reputacji domen jesteśmy umiarkowanie pewni, że domeny podchodą i że komunikaty wysyłane z tych domen są uzasadnione. Wyniki fałszywie dodatnie są bardziej prawdopodobne w tej kategorii niż fałszowanie o wysokim poziomie ufności.
   - **Domeny niepodejrzane**: domena nie powiodła się jawne uwierzytelnianie poczty e-mail sprawdza [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md). Jednak domena przeszła nasze niejawne testy uwierzytelniania poczty e-mail ([uwierzytelnianie złożone](email-validation-and-authentication.md#composite-authentication)). W związku z tym nie podjęto żadnych działań chroniących przed fałszowaniem wiadomości.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Wyświetlanie szczegółowych informacji o podejrzanych i niepomyślnych domenach

1. Na stronie Szczegółowe informacje o fałszowaniu analizy kliknij pozycję **Podejrzane domeny** lub **domeny niepodejrzane** , aby przejść do strony **Szczegółowe informacje o fałszowaniu analizy** . Strona **Spoof Intelligence insight (Szczegółowe informacje dotyczące analizy fałszowania** ) zawiera następujące informacje:

   - **Domena sfałszowana**: domena sfałszowanego użytkownika wyświetlana w polu **Od** w klientach poczty e-mail. Ten adres jest również znany jako `5322.From` adres.
   - **Infrastruktura**: znana również jako _infrastruktura wysyłająca_. Domena znaleziona w odwrotnym wyszukiwaniu DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail. Jeśli źródłowy adres IP nie ma rekordu PTR, infrastruktura wysyłania jest identyfikowana jako \<source IP\>/24 (na przykład 192.168.100.100/24).
   - **Liczba komunikatów**: liczba komunikatów z infrastruktury wysyłania do organizacji, które zawierają określoną sfałszowaną domenę w ciągu ostatnich 7 dni.
   - **Ostatnio widziano**: ostatnia data odebrania komunikatu z infrastruktury wysyłania zawierającej sfałszowaną domenę.
   - **Typ fałszowania**: ta wartość to **External**.
   - **Dozwolone do fałszowania?**: Wyświetlane tutaj wartości to:
     - **Tak**: Wiadomości z kombinacji sfałszowanej domeny użytkownika i infrastruktury wysyłania są dozwolone i nie są traktowane jako sfałszowane wiadomości e-mail.
     - **Nie**: Komunikaty z kombinacji sfałszowanej domeny użytkownika i infrastruktury wysyłania są oznaczone jako sfałszowane. Akcja jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to **Przenieś wiadomość do folderu Wiadomości-śmieci**).

2. Wybierz element z listy, aby wyświetlić szczegóły dotyczące pary domeny/wysyłania infrastruktury w wysuwnym oknie. Informacje te obejmują:
   - Dlaczego to złapaliśmy.
   - Co musisz zrobić.
   - Podsumowanie domeny.
   - WhoIs data about the sender (WhoIs data about the sender).
   - Podobne komunikaty, które widzieliśmy w twojej dzierżawie od tego samego nadawcy.

   W tym miejscu możesz również dodać lub usunąć parę infrastruktury domeny/wysyłania z listy dozwolonych **do fałszowania** nadawcy. Wystarczy odpowiednio ustawić przełącznik.

   :::image type="content" source="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png" alt-text="Domena w okienku Szczegóły analizy fałszowania" lightbox="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png":::

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy skonfigurowano analizę fałszowania z nadawcami, którzy są dozwoloni i nie mogą podszywać się, wykonaj dowolne z następujących kroków:

- Współpraca \> **& poczty e-mail** **Zasady & Reguły** \> **Zasady zagrożeń** \> **Ochrona przed spamem** w sekcji \> **Zasady** Zasady dotyczące fałszowania **zasad** \> analizy wybierz pozycję **Pokaż nadawców, których już przeglądałem**\>, wybierz kartę **Twoje domeny** lub **domeny zewnętrzne** i sprawdź wartość **Dozwolone do fałszowania dla** nadawcy.

- W programie PowerShell uruchom następujące polecenia, aby wyświetlić nadawców, którzy są dozwolone i nie mogą podszywać się pod:

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
