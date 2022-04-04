---
title: Nagłówki wiadomości w celu ochrony przed spamem
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 2e3fcfc5-5604-4b88-ac0a-c5c45c03f1db
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się więcej o polach nagłówka dodawanych do wiadomości przez Exchange Online Protection (EOP). Te pola nagłówka zawierają informacje na temat wiadomości i sposobu jej przetwarzania.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 33cebd8cfd0d61b09a5d4976baec9708082c8ca3
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679439"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>Nagłówki wiadomości w programie Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

We wszystkich Microsoft 365 firmowych program Exchange Online Protection (EOP) skanuje wszystkie przychodzące wiadomości w poszukiwaniu spamu, złośliwego oprogramowania i innych zagrożeń. Wyniki tych skanów są dodawane do następujących pól nagłówka w wiadomościach:

- **X-Forefront-Antispam-Report**: zawiera informacje na temat wiadomości i sposobu jej przetwarzania.

- **X-Microsoft-Antispam**: Zawiera dodatkowe informacje dotyczące poczty masowej i wyłudzania informacji.

- **Uwierzytelnianie-wyniki**: zawiera informacje o wynikach SPF, DKIM i DMARC (uwierzytelniania poczty e-mail).

W tym artykule opisano, co jest dostępne w tych polach nagłówka.

Aby uzyskać informacje na temat wyświetlania nagłówka wiadomości e-mail w różnych klientach poczty e-mail, zobacz [Wyświetlanie nagłówków wiadomości internetowych w programie Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Zawartość nagłówka wiadomości można skopiować i wkleić do narzędzia [Analizator nagłówka](https://mha.azurewebsites.net/) wiadomości. To narzędzie ułatwia analizowanie nagłówków i formatowanie ich w bardziej czytelnym formacie.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Pola nagłówków wiadomości X-Forefront-Antispam-Report

Po wyczyszczeniu informacji z nagłówka wiadomości znajdź nagłówek **X-Forefront-Antispam-Report** . Ten nagłówek będzie zawierał wiele par pól i wartości rozdzielonych średnikami (;). Przykład:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

Poszczególne pola i wartości są opisane w poniższej tabeli.

> [!NOTE]
> Nagłówek **X-Forefront-Antispam-Report** zawiera wiele różnych pól i wartości. Pola, które nie są opisane w tabeli, są używane wyłącznie przez zespół ochrony przed spamem firmy Microsoft do celów diagnostycznych.

|Pole|Opis|
|---|---|
|`ARC`|Protokół `ARC` ma następujące pola: <ul><li>`AAR`: rejestruje zawartość nagłówka **Authentication-results (Wyniki** uwierzytelniania) z rekordów DMARC.</li><li>`AMS`: zawiera podpisy kryptograficzne wiadomości.</li><li>`AS`: zawiera podpisy kryptograficzne nagłówków wiadomości. To pole zawiera tag sprawdzania poprawności `"cv="`łańcucha o nazwie , który uwzględnia wynik sprawdzania poprawności łańcucha jako **brak, przejście** **lub niepowodzenie****.**</li></ul>|
|`CAT:`|Kategoria zasad ochrony zastosowana do wiadomości: <ul><li>`BULK`: Zbiorczo</li><li>`DIMP`: Personifikacja domeny</li><li>`GIMP`: [Personifikacja oparta na analizie skrzynki pocztowej](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` lub `HPHISH` : Zaufana wyłudzanie informacji</li><li>`HSPM`: Duża pewność, że spam</li><li>`MALW`: Złośliwe oprogramowanie</li><li>`PHSH`: Wyłudzanie informacji</li><li>`SPM`: Spam</li><li>`SPOOF`: Fałszowanie</li><li>`UIMP`: Personifikacja użytkownika</li><li>`AMP`: ochrona przed złośliwym oprogramowaniem</li><li>`SAP`: Sejf załączników</li><li>`OSPM`: Spam wychodzący</li></ul> <p> Wiadomość przychodzący może być oflagowana przez wiele rodzajów ochrony i wiele skanów wykrywania. Zasady mają różne priorytety, a zasady o najwyższym priorytecie są stosowane w pierwszej kolejności. Aby uzyskać więcej informacji, zobacz [Jakie zasady mają](how-policies-and-protections-are-combined.md) zastosowanie, gdy na Twojej wiadomości e-mail są uruchamiane wiele metod ochrony i wykrywanie.|
|`CIP:[IP address]`|Adres IP, z którego jest nawiązywany połączenie. Możesz użyć tego adresu IP na liście adresów IP Allow List (Lista zablokowanych adresów IP) lub IP Block List (Lista zablokowanych adresów IP). Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).|
|`CTRY`|Kraj źródłowy określony na podstawie adresu IP łączącego, który może nie być taki sam jak źródłowy wysyłający adres IP.|
|`H:[helostring]`|Ciąg HELO lub EHLO łączącego serwera poczty e-mail.|
|`IPV:CAL`|Wiadomość pominięta w filtrowaniu spamu, ponieważ źródłowy adres IP został podany na liście adresów IP ze zezwalaniem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|Nie znaleziono adresu IP na żadnej liście reputacji IP.|
|`LANG`|Język, w którym została napisana wiadomość, określony w kodzie kraju (na przykład w ru_RU rosyjskim).|
|`PTR:[ReverseDNS]`|Rekord PTR źródłowego adresu IP (nazywany też odwrotnym odnośnikem DNS).|
|`SCL`|Poziom ufności filtru spamu dla wiadomości. Wyższa wartość oznacza, że wiadomość jest bardziej prawdopodobna jako spam. Aby uzyskać więcej informacji, zobacz [Poziom ufności filtru spamu](spam-confidence-levels.md).|
|`SFTY`|Wiadomość została zidentyfikowany jako wyłudzanie informacji i będzie również oznaczona jedną z następujących wartości: <ul><li>9.19: Personifikacja domeny. Domena wysyłająca próbuje [personifikować chronioną domenę](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Nazwa porada dotycząca bezpieczeństwa personifikacji domeny jest dodawana do wiadomości (jeśli jest włączona).</li><li>9.20: Personifikacja użytkownika. Wysyłający użytkownik próbuje podszyć się pod użytkownika w organizacji adresata lub chronionego użytkownika [](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) określonego w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla systemu Office 365. Nazwa porada dotycząca bezpieczeństwa personifikacji użytkownika jest dodawana do wiadomości (jeśli jest włączona).</li></ul>|
|`SFV:BLK`|Filtrowanie zostało pominięte, a wiadomość została zablokowana, ponieważ została wysłana z adresu z listy zablokowanych nadawców użytkownika. <p> Aby uzyskać więcej informacji o tym, jak administratorzy mogą zarządzać listą zablokowanych nadawców użytkownika, zobacz Konfigurowanie ustawień wiadomości-śmieci w [Exchange Online skrzynkach pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|Filtrowanie spamu oznaczało wiadomość jako niebędącą spamem, a wiadomość została wysłana do zamierzonych adresatów.|
|`SFV:SFE`|Filtrowanie zostało pominięte i wiadomość została dozwolona, ponieważ została wysłana z adresu na liście Sejf nadawców użytkownika. <p> Aby uzyskać więcej informacji o tym, jak administratorzy mogą zarządzać listą nadawców Sejf użytkowników, zobacz Konfigurowanie ustawień wiadomości-śmieci w [Exchange Online skrzynkach pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|Wiadomość pominięta w filtrowaniu spamu została dostarczona do skrzynki odbiorczej, ponieważ nadawca został na liście dozwolonych nadawców lub na liście dozwolonych domen w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|Wiadomość została oznaczona jako spam, ponieważ dopasowała nadawcę do listy zablokowanych nadawców lub zablokowanych domen w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|Podobnie jak w przypadku sfv:sku w wiadomości pominięto filtrowanie spamu z innego powodu (na przykład wiadomość e-mail wewnątrz organizacji w dzierżawie).|
|`SFV:SKN`|Wiadomość została oznaczona jako wiadomość niebędąca spamem przed rozpoczęciem przetwarzania przez filtrowanie spamu. Na przykład wiadomość została oznaczona jako SCL -1 lub Pomijanie **filtrowania spamu** przez regułę przepływu poczty.|
|`SFV:SKQ`|Wiadomość została wydana z kwarantanny i została wysłana do zamierzonych adresatów.|
|`SFV:SKS`|Wiadomość została oznaczona jako spam przed przetworzeniem przez filtrowanie spamu. Na przykład wiadomość została oznaczona jako SCL od 5 do 9 przez regułę przepływu poczty.|
|`SFV:SPM`|Wiadomość została oznaczona jako spam przez filtrowanie spamu.|
|`SRV:BULK`|Wiadomość została zidentyfikowany jako zbiorcza poczta e-mail za pomocą filtrowania spamu i progu ilości skarg zbiorczych. Gdy _parametr MarkAsSpamBulkMail_ `On` jest (domyślnie jest włączona), zbiorcza wiadomość e-mail jest oznaczona jako spam (SCL 6). Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|Wiadomość została dopasowana do ustawienia Zaawansowanego filtru spamu (ASF). Aby wyświetlić wartość nagłówka X dla każdego ustawienia asf, zobacz Zaawansowane ustawienia filtru [spamu (ASF).](advanced-spam-filtering-asf-options.md)|

## <a name="x-microsoft-antispam-message-header-fields"></a>Pola nagłówka wiadomości X-Microsoft-Antispam

W poniższej tabeli opisano przydatne pola w nagłówku wiadomości **X-Microsoft-Antispam** . Inne pola w tym nagłówku są używane wyłącznie przez zespół ochrony przed spamem firmy Microsoft do celów diagnostycznych.

|Pole|Opis|
|---|---|
|`BCL`|Zbiorczy poziom skarg (BCL) wiadomości. Wyższa wartość BCL wskazuje, że wiadomości masowej wysyłki z większą prawdopodobieństwem generują skargi (przez co są tym bardziej prawdopodobne, że są spamem). Aby uzyskać więcej informacji, zobacz [Zbiorczy poziom skarg (BCL).](bulk-complaint-level-values.md)|

## <a name="authentication-results-message-header"></a>Nagłówek wiadomości wyników uwierzytelniania

Wyniki sprawdzania uwierzytelniania poczty **e-mail** pod adresem SPF, DKIM i DMARC są rejestrowane (oznaczane sygnaturą) w nagłówku wiadomości przychodzących wyników uwierzytelniania.

Na poniższej liście opisano tekst, który jest dodawany do nagłówka **Authentication-Results** (Wyniki uwierzytelniania) dla każdego typu sprawdzania uwierzytelniania wiadomości e-mail:

- Spf ma następującą składnię:

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Przykład:

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- W funkcji DKIM jest używana następująca składnia:

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Przykład:

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- W funkcji DMARC jest używana następująca składnia:

  ```text
  dmarc=<pass|fail|bestguesspass|none> action=<permerror|temperror|oreject|pct.quarantine|pct.reject> header.from=<domain>
  ```

  Przykład:

  ```text
  dmarc=pass action=none header.from=contoso.com
  dmarc=bestguesspass action=none header.from=contoso.com
  dmarc=fail action=none header.from=contoso.com
  dmarc=fail action=oreject header.from=contoso.com
  ```

### <a name="authentication-results-message-header-fields"></a>Pola nagłówków wiadomości w wynikach uwierzytelniania

W poniższej tabeli opisano pola i możliwe wartości dla każdego sprawdzania uwierzytelniania poczty e-mail.

|Pole|Opis|
|---|---|
|`action`|Oznacza działanie wykonane przez filtr spamu na podstawie wyników sprawdzenia DMARC. Przykład: <ul><li>**oreject** lub **o.reject**: oznacza "odrzuć". W tym Microsoft 365 ta akcja jest używana, gdy odbiera wiadomość, która kończy się niepowodzeniem sprawdzania DMARC z domeny, której rekord TXT DMARC ma zasady p=reject. Zamiast usuwać lub odrzucać wiadomość, Microsoft 365 oznacza wiadomość jako spam. Aby uzyskać więcej informacji o tym, dlaczego Microsoft 365 w ten sposób, zobacz Jak Microsoft 365 poczty przychodzącej, która kończy się [niepowodzeniem DMARC](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.quarantine**: Wskazuje, że wiadomości nieukońcowe będą dostarczane jako mniej niż 100% wiadomości nieukońcowych. Oznacza to, że wiadomość nie powiodła się DMARC i zasady zostały ustawione do kwarantanny, ale pole pct nie zostało ustawione na 100%, a system losowo nie określał, aby zastosować akcję DMARC zgodnie z zasadami określonej domeny.</li><li>**pct.reject**: Oznacza, że nieukończyty DMARC zostanie dostarczony w procentach krótszych niż 100% wiadomości. Oznacza to, że wiadomość nie powiodła się DMARC i zasady zostały ustawione na odrzucenie, ale pole pct nie zostało ustawione na 100%, a system losowo nie określał, aby zastosować akcję DMARC zgodnie z zasadami określonej domeny.</li><li>**Permerror**: Podczas oceny DMARC wystąpił błąd trwały, na przykład napotkanie niepoprawnie utworzonego rekordu TXT DMARC w systemie DNS. Próba ponownego przesłania tej wiadomości prawdopodobnie nie zakończy się innym wynikiem. W celu rozwiązania problemu może być konieczne skontaktowanie się z właścicielem domeny.</li><li>**błąd**: Wystąpił tymczasowy błąd podczas oceny DMARC. Możesz mieć możliwość zażądania, aby nadawca ponownie wysłał wiadomość później, aby poprawnie przetworzyć wiadomość e-mail.</li></ul>|
|`compauth`|Wynik uwierzytelniania złożonego. Używany przez Microsoft 365 do łączenia wielu typów uwierzytelniania, takich jak SPF, DKIM, DMARC lub dowolnej innej części wiadomości w celu określenia, czy wiadomość jest uwierzytelniona. Używa domeny From (Od) jako podstawy oceny.|
|`dkim`|W tym artykule opisano wyniki sprawdzenia przez DKIM wiadomości. Możliwe wartości: <ul><li>**pass** (pomyślnie): wskazuje, czy wiadomość została przekazana przez DKIM.</li><li>**niepowodzenie (powód)**: wskazuje, że kontrola DKIM wiadomości nie powiodła się i dlaczego. Na przykład jeśli wiadomość nie została podpisana lub podpis nie został zweryfikowany.</li><li>**brak**. Wskazuje, że wiadomość nie została podpisana. Może to oznaczać, że domena ma rekord DKIM lub że rekord DKIM nie jest szacowany jako wynik, tylko że ta wiadomość nie została podpisana.</li></ul>|
|`dmarc`|W tym artykule opisano wyniki sprawdzenia wiadomości przez DMARC. Możliwe wartości: <ul><li>**pass**: wskazuje, że DMARC sprawdza pomyślnie wiadomość.</li><li>**niepowodzenie**: Oznacza, że sprawdzenie DMARC wiadomości nie powiodło się.</li><li>**bestguesspass**: Wskazuje, że dla domeny nie istnieje żaden rekord DMARC TXT, ale jeśli istniał, oznacza to, że dMARC sprawdza, czy wiadomość zostałaby przekazana.</li><li>**brak**: wskazuje, że dla domeny wysyłającej w systemie DNS nie istnieje żaden rekord TXT DMARC.|
|`header.d`|Domena zidentyfikowany w podpisie DKIM, jeśli jest w podpisie. Jest to domena, do która jest ponawiana kwerenda dla klucza publicznego.|
|`header.from`|Domena adresu w nagłówku `5322.From` wiadomości e-mail (ta nazwa jest również znana jako adres Od lub nadawca P2). Adresat zobacz adres Od w klientach poczty e-mail.|
|`reason`|Przyczyna, dla których uwierzytelnienie złożone zakończyło się niepowodzeniem lub pomyślnie. Wartość jest 3-cyfrowym kodem. Przykład: <ul><li>**000**: W komunikacie nie powiodło się uwierzytelnianie jawne (`compauth=fail`). Na przykład wiadomość odebrana jako DMARC nie powiodła się wraz z akcją kwarantanny lub odrzuceniem.</li><li>**001**: W komunikacie nie powiodło się uwierzytelnianie niejawne (`compauth=fail`). Oznacza to, że w domenie wysyłającej nie zostały opublikowane rekordy uwierzytelniania wiadomości e-mail lub , jeśli tak, miały one słabsze zasady awarii (mechanizm SPF "miękkie niepowodzenie" lub neutralność, zasady DMARC z `p=none`).</li><li>**002**: Organizacja ma zasady dotyczące pary nadawca/domena, za pomocą których nie można wysyłać sfałszowanych wiadomości e-mail. To ustawienie jest ustawiane ręcznie przez administratora.</li><li>**010**: Wiadomość nie powiodła się DMARC z akcją odrzucenia lub kwarantanny, a domena wysyłająca jest jedną z zaakceptowanych domen organizacji (jest to część samoobsługi lub spoofingu wewnątrz organizacji).</li><li>**1xx** lub **7xx**: Wiadomość przeszła uwierzytelnianie (`compauth=pass`). Ostatnie dwie cyfry to wewnętrzne kody używane przez Microsoft 365.</li><li>**2xx**: Komunikat z uwierzytelnianiem niejawnym (soft-passed`compauth=softpass`). Ostatnie dwie cyfry to wewnętrzne kody używane przez Microsoft 365.</li><li>**3xx**: Komunikat nie został sprawdzony pod kątem uwierzytelniania złożonego (`compauth=none`).</li><li>**4xx** lub **9xx**: Komunikat ominął uwierzytelnianie złożone (`compauth=none`). Ostatnie dwie cyfry to wewnętrzne kody używane przez Microsoft 365.</li><li>**6xx**: Wiadomość nie powiodła się niejawnego uwierzytelniania wiadomości e-mail, a domena wysyłająca jest jedną z zaakceptowanych domen organizacji (jest to część fałszowania w organizacji lub samoobsługi wewnątrz organizacji).</li></ul>|
|`smtp.mailfrom`|Domena adresu `5321.MailFrom` (znana również jako adres MAIL FROM, nadawca P1 lub nadawca koperty). Jest to adres e-mail, który jest używany na przykład w raportach o niedo dostarczeniu (nazywanych również raportami o niedo dostarczeniach lub wiadomościami bounce).|
|`spf`|W tym artykule opisano wyniki sprawdzenia SPF dla wiadomości. Możliwe wartości: <ul><li>`pass (IP address)`: Sprawdzanie SPF dla wiadomości przekazano i zawiera adres IP nadawcy. Klient jest uprawniony do wysyłania lub przekazywania wiadomości e-mail w imieniu domeny nadawcy.</li><li>`fail (IP address)`: Sprawdzanie SPF dla wiadomości nie powiodło się i zawiera adres IP nadawcy. Jest to czasami nazywane _trudnym niepowodzeniem_.</li><li>`softfail (reason)`: Rekord SPF wyznaczył hosta jako niedozwolonego do wysyłania, ale jest w przejściu.</li><li>`neutral`: Rekord SPF wyraźnie stwierdza, że nie skonserduje, czy adres IP nie jest autoryzowany do wysyłania.</li><li>`none`: Domena nie ma rekordu SPF lub rekord SPF nie jest szacowany jako wynik.</li><li>`temperror`: Wystąpił tymczasowy błąd. Na przykład błąd DNS. To samo sprawdzanie może się powieść w późniejszym czasie.</li><li>`permerror`: Wystąpił błąd trwały. Na przykład domena ma rekord SPF o źle sformatowanym formacie.</li></ul>|
