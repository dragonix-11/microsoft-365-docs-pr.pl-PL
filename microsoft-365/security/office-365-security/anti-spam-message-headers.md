---
title: Nagłówki wiadomości chroniących przed spamem
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
description: Administratorzy mogą dowiedzieć się więcej o polach nagłówka, które są dodawane do komunikatów przez Exchange Online Protection (EOP). Te pola nagłówka zawierają informacje o komunikacie i sposobie jego przetwarzania.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 592a583b572c134dd4ecd33dd18f392f6e9b36ce
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493070"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>Nagłówki wiadomości antyspamowych w usłudze Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

We wszystkich organizacjach platformy Microsoft 365 Exchange Online Protection (EOP) skanuje wszystkie przychodzące wiadomości pod kątem spamu, złośliwego oprogramowania i innych zagrożeń. Wyniki tych skanów są dodawane do następujących pól nagłówka w komunikatach:

- **X-Forefront-Antispam-Report**: zawiera informacje o komunikacie i sposobie jego przetwarzania.

- **X-Microsoft-Antispam**: zawiera dodatkowe informacje na temat poczty zbiorczej i wyłudzania informacji.

- **Wyniki uwierzytelniania**: zawiera informacje o wynikach SPF, DKIM i DMARC (uwierzytelnianie za pośrednictwem poczty e-mail).

W tym artykule opisano, co jest dostępne w tych polach nagłówka.

Aby uzyskać informacje o sposobie wyświetlania nagłówka wiadomości e-mail w różnych klientach poczty e-mail, zobacz [Wyświetlanie nagłówków wiadomości internetowych w programie Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Zawartość nagłówka komunikatu można skopiować i wkleić do narzędzia [Analizator nagłówka wiadomości](https://mha.azurewebsites.net/) . To narzędzie pomaga przeanalizować nagłówki i umieścić je w bardziej czytelnym formacie.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Pola nagłówka komunikatu X-Forefront-Antispam-Report

Po wyświetleniu informacji nagłówka komunikatu znajdź nagłówek **X-Forefront-Antispam-Report** . W tym nagłówku będzie wiele par pól i wartości rozdzielonych średnikami (;). Przykład:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

Poszczególne pola i wartości są opisane w poniższej tabeli.

> [!NOTE]
> Nagłówek **X-Forefront-Antispam-Report** zawiera wiele różnych pól i wartości. Pola, które nie są opisane w tabeli, są używane wyłącznie przez zespół ds. ochrony przed spamem firmy Microsoft do celów diagnostycznych.

|Pole|Opis|
|---|---|
|`ARC`|Protokół `ARC` zawiera następujące pola: <ul><li>`AAR`: rejestruje zawartość **nagłówka Authentication-results** z DMARC.</li><li>`AMS`: zawiera sygnatury kryptograficzne komunikatu.</li><li>`AS`: zawiera sygnatury kryptograficzne nagłówków wiadomości. To pole zawiera tag weryfikacji łańcucha o nazwie `"cv="`, który zawiera wynik weryfikacji łańcucha jako **brak**, **przekazywanie** lub **niepowodzenie**.</li></ul>|
|`CAT:`|Kategoria zasad ochrony zastosowana do komunikatu: <ul><li>`BULK`: Zbiorczo</li><li>`DIMP`: Personifikacja domeny</li><li>`GIMP`: [Personifikacja oparta na analizie skrzynki pocztowej](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` lub `HPHISH`: Wyłudzanie informacji o wysokim poziomie ufności</li><li>`HSPM`: Spam o wysokim poziomie ufności</li><li>`MALW`: Złośliwe oprogramowanie</li><li>`PHSH`: wyłudzanie informacji</li><li>`SPM`: Spam</li><li>`SPOOF`: Fałszowanie</li><li>`UIMP`: Personifikacja użytkownika</li><li>`AMP`: Ochrona przed złośliwym oprogramowaniem</li><li>`SAP`: Bezpieczne załączniki</li><li>`OSPM`: Spam wychodzący</li></ul> <p> Komunikat przychodzący może być oflagowany przez wiele form ochrony i wiele skanów wykrywania. Zasady mają różne priorytety, a zasady o najwyższym priorytecie są stosowane jako pierwsze. Aby uzyskać więcej informacji, zobacz [Jakie zasady mają zastosowanie w przypadku uruchamiania wielu metod ochrony i skanowania wykrywania w wiadomości e-mail](how-policies-and-protections-are-combined.md).|
|`CIP:[IP address]`|Łączący się adres IP. Tego adresu IP można użyć na liście dozwolonych adresów IP lub na liście zablokowanych adresów IP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).|
|`CTRY`|Kraj źródłowy określony przez łączący się adres IP, który może nie być taki sam jak adres IP wysyłający dane źródłowe.|
|`H:[helostring]`|Ciąg HELO lub EHLO łączącego się serwera poczty e-mail.|
|`IPV:CAL`|Komunikat pominął filtrowanie spamu, ponieważ źródłowy adres IP znajduje się na liście dozwolonych adresów IP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|Nie odnaleziono adresu IP na żadnej liście reputacji adresów IP.|
|`LANG`|Język, w którym wiadomość została napisana, zgodnie z kodem kraju (na przykład ru_RU dla języka rosyjskiego).|
|`PTR:[ReverseDNS]`|Rekord PTR (znany również jako odwrotne wyszukiwanie DNS) źródłowego adresu IP.|
|`SCL`|Poziom ufności spamu (SCL) wiadomości. Wyższa wartość wskazuje, że wiadomość jest bardziej prawdopodobna jako spam. Aby uzyskać więcej informacji, zobacz [Poziom ufności spamu (SCL).](spam-confidence-levels.md)|
|`SFTY`|Wiadomość została zidentyfikowana jako wyłudzająca informacje i zostanie również oznaczona jedną z następujących wartości: <ul><li>9.19: Personifikacja domeny. Domena wysyłająca próbuje [personifikować chronioną domenę](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Wskazówka dotycząca bezpieczeństwa personifikacji domeny jest dodawana do komunikatu (jeśli jest włączona).</li><li>9.20: Personifikacja użytkownika. Wysyłający użytkownik próbuje personifikować użytkownika w organizacji odbiorcy lub [chronionego użytkownika określonego w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) w Ochrona usługi Office 365 w usłudze Microsoft Defender. Wskazówka dotycząca bezpieczeństwa dotycząca personifikacji użytkowników jest dodawana do komunikatu (jeśli jest włączona).</li><li>9.25: Pierwsza porada bezpieczeństwa kontaktu. Ta wartość _może wskazywać_ na podejrzaną lub wyłudzającą informacje. Aby uzyskać więcej informacji, zobacz [Porada dotycząca bezpieczeństwa pierwszego kontaktu](set-up-anti-phishing-policies.md#first-contact-safety-tip).</li></ul>|
|`SFV:BLK`|Filtrowanie zostało pominięte, a komunikat został zablokowany, ponieważ został wysłany z adresu na liście zablokowanych nadawców użytkownika. <p> Aby uzyskać więcej informacji o tym, jak administratorzy mogą zarządzać listą zablokowanych nadawców użytkownika, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|Filtrowanie spamu oznaczało wiadomość jako niespamową, a wiadomość została wysłana do zamierzonych adresatów.|
|`SFV:SFE`|Filtrowanie zostało pominięte, a komunikat był dozwolony, ponieważ został wysłany z adresu na liście bezpiecznych nadawców użytkownika. <p> Aby uzyskać więcej informacji o tym, jak administratorzy mogą zarządzać listą bezpiecznych nadawców użytkownika, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|Wiadomość pominąła filtrowanie spamu i została dostarczona do skrzynki odbiorczej, ponieważ nadawca znajdował się na liście dozwolonych nadawców lub na liście dozwolonych domen w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|Wiadomość została oznaczona jako spam, ponieważ pasowała do nadawcy na liście zablokowanych nadawców lub zablokowanych domen w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|Podobnie jak w przypadku protokołu SFV:SKN, komunikat pominął filtrowanie spamu z innego powodu (na przykład wewnątrz organizacji wiadomości e-mail w ramach dzierżawy).|
|`SFV:SKN`|Wiadomość została oznaczona jako niespamowana przed przetworzeniem przez filtrowanie spamu. Na przykład wiadomość została oznaczona jako SCL -1 lub **Pomiń filtrowanie spamu** według reguły przepływu poczty.|
|`SFV:SKQ`|Wiadomość została zwolniona z kwarantanny i została wysłana do zamierzonych adresatów.|
|`SFV:SKS`|Wiadomość została oznaczona jako spam przed przetworzeniem przez filtrowanie spamu. Na przykład wiadomość została oznaczona jako SCL od 5 do 9 przez regułę przepływu poczty.|
|`SFV:SPM`|Wiadomość została oznaczona jako spam przez filtrowanie spamu.|
|`SRV:BULK`|Wiadomość została zidentyfikowana jako zbiorcza wiadomość e-mail przez filtrowanie spamu i próg poziomu skarg zbiorczych (BCL). Gdy parametr _MarkAsSpamBulkMail_ jest `On` (domyślnie włączony), zbiorcza wiadomość e-mail jest oznaczona jako spam (SCL 6). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|Wiadomość była zgodna z ustawieniem zaawansowanego filtru spamu (ASF). Aby wyświetlić wartość nagłówka X dla każdego ustawienia asf, zobacz [Ustawienia zaawansowanego filtru spamu (ASF).](advanced-spam-filtering-asf-options.md)|

## <a name="x-microsoft-antispam-message-header-fields"></a>Pola nagłówka komunikatu X-Microsoft-Antispam

W poniższej tabeli opisano przydatne pola w nagłówku komunikatu **X-Microsoft-Antispam** . Inne pola w tym nagłówku są używane wyłącznie przez zespół ds. ochrony przed spamem firmy Microsoft do celów diagnostycznych.

|Pole|Opis|
|---|---|
|`BCL`|Poziom skargi zbiorczej (BCL) komunikatu. Wyższa lista BCL wskazuje, że wiadomość e-mail zbiorcza jest bardziej skłonna do generowania skarg (i dlatego jest bardziej prawdopodobna jako spam). Aby uzyskać więcej informacji, zobacz [Poziom skarg zbiorczych (BCL).](bulk-complaint-level-values.md)|

## <a name="authentication-results-message-header"></a>Nagłówek komunikatu authentication-results

Wyniki kontroli uwierzytelniania poczty e-mail dla SPF, DKIM i DMARC są rejestrowane (ostemplowane) w nagłówku **komunikatu Authentication-results** w komunikatach przychodzących.

Na poniższej liście opisano tekst dodany do nagłówka Authentication-Results dla każdego typu sprawdzania uwierzytelniania poczty **e-mail** :

- SPF używa następującej składni:

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Przykład:

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- Usługa DKIM używa następującej składni:

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Przykład:

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- Usługa DMARC używa następującej składni:

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

### <a name="authentication-results-message-header-fields"></a>Pola nagłówka komunikatu authentication-results

W poniższej tabeli opisano pola i możliwe wartości dla każdego sprawdzania uwierzytelniania poczty e-mail.

|Pole|Opis|
|---|---|
|`action`|Wskazuje akcję podjętą przez filtr spamu na podstawie wyników sprawdzania DMARC. Przykład: <ul><li>**oreject** lub **o.reject**: skrót od zastąpienia odrzuć. W takim przypadku usługa Microsoft 365 używa tej akcji, gdy otrzymuje komunikat, który kończy się niepowodzeniem sprawdzania DMARC z domeny, której rekord DMARC TXT ma zasady p=reject. Zamiast usuwać lub odrzucać wiadomość, platforma Microsoft 365 oznacza wiadomość jako spam. Aby uzyskać więcej informacji na temat tego, dlaczego platforma Microsoft 365 jest skonfigurowana w ten sposób, zobacz [Jak platforma Microsoft 365 obsługuje przychodzące wiadomości e-mail, które kończy się niepowodzeniem DMARC](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.quarantine**: wskazuje, że procent mniejszy niż 100% komunikatów, które nie przechodzą DMARC, i tak zostanie dostarczony. Oznacza to, że komunikat nie powiodł się DMARC, a zasady zostały ustawione na kwarantannę, ale pole pct nie zostało ustawione na 100%, a system losowo postanowił nie stosować akcji DMARC zgodnie z zasadami określonej domeny.</li><li>**pct.reject**: wskazuje, że procent mniejszy niż 100% komunikatów, które nie przechodzą DMARC, i tak zostanie dostarczony. Oznacza to, że komunikat nie powiodł się DMARC i zasady zostały ustawione na odrzucenie, ale pole pct nie zostało ustawione na 100%, a system losowo postanowił nie stosować akcji DMARC zgodnie z zasadami określonej domeny.</li><li>**permerror**: Podczas oceny DMARC wystąpił trwały błąd, taki jak napotkanie niepoprawnie utworzonego rekordu TXT DMARC w systemie DNS. Próba ponownego przesłania tej wiadomości prawdopodobnie nie zakończy się innym wynikiem. Zamiast tego może być konieczne skontaktowanie się z właścicielem domeny w celu rozwiązania problemu.</li><li>**temperror**: Wystąpił tymczasowy błąd podczas oceny DMARC. Możesz zażądać, aby nadawca ponownie wysłał wiadomość później, aby prawidłowo przetworzyć wiadomość e-mail.</li></ul>|
|`compauth`|Wynik uwierzytelniania złożonego. Używany przez platformę Microsoft 365 do łączenia wielu typów uwierzytelniania, takich jak SPF, DKIM, DMARC, lub dowolnej innej części komunikatu w celu ustalenia, czy komunikat jest uwierzytelniony. Używa domeny From: jako podstawy oceny.|
|`dkim`|Opisuje wyniki sprawdzania DKIM dla komunikatu. Możliwe wartości obejmują: <ul><li>**pass**: wskazuje sprawdzanie DKIM dla przekazanego komunikatu.</li><li>**fail (reason)**: wskazuje sprawdzanie DKIM dla komunikatu nie powiodło się i dlaczego. Jeśli na przykład wiadomość nie została podpisana lub podpis nie został zweryfikowany.</li><li>**brak**: wskazuje, że komunikat nie został podpisany. Może to oznaczać, że domena ma rekord DKIM lub rekord DKIM nie daje wyniku, tylko że ten komunikat nie został podpisany.</li></ul>|
|`dmarc`|Opisuje wyniki sprawdzania DMARC dla komunikatu. Możliwe wartości obejmują: <ul><li>**pass**: wskazuje sprawdzanie DMARC dla przekazanego komunikatu.</li><li>**niepowodzenie**: wskazuje, że sprawdzanie DMARC dla komunikatu nie powiodło się.</li><li>**bestguesspass**: wskazuje, że nie istnieje rekord DMARC TXT dla domeny, ale gdyby istniał, sprawdzanie DMARC dla komunikatu zostałoby zakończone.</li><li>**brak**: wskazuje, że dla domeny wysyłającej w systemie DNS nie istnieje żaden rekord TXT DMARC.|
|`header.d`|Domena zidentyfikowana w sygnaturze DKIM, jeśli istnieje. Jest to domena, która jest pytana o klucz publiczny.|
|`header.from`|Domena `5322.From` adresu w nagłówku wiadomości e-mail (znana również jako nadawca z adresu lub P2). Adresat widzi adres od w klientach poczty e-mail.|
|`reason`|Przyczyna przekazania lub niepowodzenia uwierzytelniania złożonego. Wartość jest kodem 3-cyfrowym. Przykład: <ul><li>**000**: Komunikat nie może jawnie uwierzytelnić (`compauth=fail`). Na przykład komunikat otrzymał błąd DMARC z akcją kwarantanny lub odrzucenia.</li><li>**001**: Niejawne uwierzytelnianie (`compauth=fail`) nie powiodło się. Oznacza to, że domena wysyłająca nie ma opublikowanych rekordów uwierzytelniania poczty e-mail lub jeśli tak się stało, miała słabsze zasady błędów (SPF soft fail or neutral, DMARC policy of `p=none`).</li><li>**002**: Organizacja ma zasady dla pary nadawca/domena, które jawnie nie mogą wysyłać sfałszowanych wiadomości e-mail. To ustawienie jest ustawiane ręcznie przez administratora.</li><li>**010**: Komunikat nie powiodł się DMARC z akcją odrzucenia lub kwarantanny, a domena wysyłająca jest jedną z akceptowanych domen organizacji (jest to część samoobsługowego lub wewnątrz organizacji, fałszowanie).</li><li>**1xx** lub **7xx**: komunikat przeszedł uwierzytelnianie (`compauth=pass`). Ostatnie dwie cyfry to kody wewnętrzne używane przez platformę Microsoft 365.</li><li>**2xx**: niejawne uwierzytelnianie przekazywane przez komunikat (`compauth=softpass`). Ostatnie dwie cyfry to kody wewnętrzne używane przez platformę Microsoft 365.</li><li>**3xx**: Komunikat nie został sprawdzony pod kątem uwierzytelniania złożonego (`compauth=none`).</li><li>**4xx** lub **9xx**: komunikat pominął uwierzytelnianie złożone (`compauth=none`). Ostatnie dwie cyfry to kody wewnętrzne używane przez platformę Microsoft 365.</li><li>**6xx**: Niejawne uwierzytelnianie poczty e-mail nie powiodło się, a domena wysyłania jest jedną z akceptowanych domen organizacji (jest to część samoobsługowego lub wewnątrz organizacji).</li></ul>|
|`smtp.mailfrom`|Domena adresu (znana `5321.MailFrom` również jako adres MAIL FROM, nadawca P1 lub nadawca koperty). Jest to adres e-mail używany do raportów o braku dostarczania (znanych również jako serwery NDR lub wiadomości odbić).|
|`spf`|Opisuje wyniki sprawdzania SPF dla komunikatu. Możliwe wartości obejmują: <ul><li>`pass (IP address)`: Sprawdzanie SPF dla przekazanej wiadomości i zawiera adres IP nadawcy. Klient ma uprawnienia do wysyłania lub przekazywania wiadomości e-mail w imieniu domeny nadawcy.</li><li>`fail (IP address)`: Sprawdzanie SPF komunikatu nie powiodło się i zawiera adres IP nadawcy. Jest to czasami nazywane _twardym niepowodzeniem_.</li><li>`softfail (reason)`: Rekord SPF wyznaczył hosta jako niedozwolony do wysyłania, ale jest w stanie przejściowym.</li><li>`neutral`: Rekord SPF jawnie stwierdza, że nie potwierdza, czy adres IP jest autoryzowany do wysyłania.</li><li>`none`: Domena nie ma rekordu SPF lub rekord SPF nie daje wyniku.</li><li>`temperror`: Wystąpił tymczasowy błąd. Na przykład błąd DNS. To samo sprawdzenie później może zakończyć się pomyślnie.</li><li>`permerror`: Wystąpił trwały błąd. Na przykład domena ma nieprawidłowo sformatowany rekord SPF.</li></ul>|
