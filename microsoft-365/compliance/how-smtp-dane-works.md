---
title: Jak działa uwierzytelnianie oparte na usłudze DNS SMTP dla jednostek nazwanych (DANE) w celu zabezpieczenia komunikacji za pośrednictwem poczty e-mail
f1.keywords:
- NOCSH
ms.author: v-mathavale
author: v-mathavale
manager: dansimp
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak oparte na usłudze SMTP uwierzytelnianie dns jednostek nazwanych (DANE) działa w celu zabezpieczenia komunikacji poczty e-mail między serwerami poczty.
ms.openlocfilehash: b5f9337457556dda53b5b2f982480a4c2501fcc9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782858"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Jak działa uwierzytelnianie oparte na usłudze DNS SMTP dla jednostek nazwanych (DANE)

Protokół SMTP jest głównym protokołem używanym do przesyłania komunikatów między serwerami poczty i domyślnie nie jest bezpieczny. Protokół Transport Layer Security (TLS) został wprowadzony wiele lat temu w celu obsługi szyfrowanej transmisji komunikatów za pośrednictwem protokołu SMTP. Jest to powszechnie używane oportunistycznie, a nie jako wymóg, pozostawiając dużo ruchu poczty e-mail w postaci zwykłego tekstu, podatne na przechwycenie przez nikczemnych aktorów. Ponadto protokół SMTP określa adresy IP serwerów docelowych za pośrednictwem publicznej infrastruktury DNS, która jest podatna na fałszowanie i ataki typu man-in-the-middle (MITM). Doprowadziło to do utworzenia wielu nowych standardów w celu zwiększenia bezpieczeństwa wysyłania i odbierania wiadomości e-mail. Jednym z nich jest uwierzytelnianie nazwane jednostek (DANE) oparte na systemie DNS.

DANE for SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) używa obecności rekordu TLSA (Transport Layer Security Authentication) w rekordzie DNS domeny, aby zasygnalizować domenę, a jej serwery poczty obsługują DANE. Jeśli nie ma rekordu TLSA, rozpoznawanie nazw DNS dla przepływu poczty będzie działać jak zwykle bez próby sprawdzenia DANE. Rekord TLSA bezpiecznie sygnalizuje obsługę protokołu TLS i publikuje zasady DANE dla domeny. Dlatego wysyłanie serwerów poczty może pomyślnie uwierzytelnić prawidłowe serwery poczty odbiorczej przy użyciu protokołu SMTP DANE. Dzięki temu jest odporny na ataki z powodu obniżenia poziomu i mitm. Dane ma bezpośrednie zależności od serwera DNSSEC, który działa poprzez cyfrowe podpisywanie rekordów odnośników DNS przy użyciu kryptografii klucza publicznego. Testy DNSSEC są wykonywane dla cyklicznych rozpoznawania nazw DNS, serwerów DNS, które tworzą zapytania DNS dla klientów. Serwer DNSSEC zapewnia, że rekordy DNS nie są modyfikowane i są autentyczne.

Gdy rekordy zasobów MX, A/AAAA i DNSSEC dla domeny zostaną zwrócone do rekursywnego rozpoznawania nazw DNS jako uwierzytelnianie DNSSEC, serwer poczty wysyłającej poprosi o rekord TLSA odpowiadający wpisowi lub wpisom hosta MX. Jeśli rekord TLSA jest obecny i sprawdzony jako autentyczny przy użyciu innego sprawdzania DNSSEC, cykliczny program rozpoznawania nazw DNS zwróci rekord TLSA do serwera poczty wysyłającej.

Po otrzymaniu autentycznego rekordu TLSA serwer poczty wysyłającej ustanawia połączenie SMTP z hostem MX skojarzonym z autentycznym rekordem TLSA. Serwer poczty wysyłającej spróbuje skonfigurować protokół TLS i porównać certyfikat TLS serwera z danymi w rekordzie TLSA, aby sprawdzić, czy docelowy serwer poczty połączony z nadawcą jest legalnym serwerem poczty odbiorczej. Komunikat zostanie przesłany (przy użyciu protokołu TLS), jeśli uwierzytelnianie zakończy się pomyślnie. W przypadku niepowodzenia uwierzytelniania lub jeśli protokół TLS nie jest obsługiwany przez serwer docelowy, Exchange Online ponawia próbę wykonania całego procesu weryfikacji, rozpoczynając od zapytania DNS dla tej samej domeny docelowej ponownie po 15 minutach, a następnie 15 minut po tym, a następnie co godzinę przez następne 24 godziny. Jeśli uwierzytelnianie nadal kończy się niepowodzeniem po 24 godzinach ponawiania próby, komunikat wygaśnie, a do nadawcy zostanie wygenerowany identyfikator NDR ze szczegółami błędu.

## <a name="what-are-the-components-of-dane"></a>Jakie są składniki dane?

### <a name="tlsa-resource-record"></a>Rekord zasobu TLSA

Rekord uwierzytelniania TLS (TLSA) służy do kojarzenia certyfikatu X.509 serwera lub wartości klucza publicznego z nazwą domeny zawierającą rekord. Rekordy TLSA można ufać tylko wtedy, gdy serwer DNSSEC jest włączony w twojej domenie. Jeśli używasz dostawcy DNS do hostowania domeny, może to być ustawienie oferowane podczas konfigurowania domeny z nimi. Aby dowiedzieć się więcej na temat podpisywania stref DNSSEC, odwiedź ten link: [Omówienie | DNSSEC Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)).

Przykładowy rekord TLSA:

:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Przykładowy rekord TLSA" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Istnieją cztery konfigurowalne pola unikatowe dla typu rekordu TLSA:

**Pole użycia certyfikatu**: określa, w jaki sposób serwer poczty e-mail wysyłającej powinien zweryfikować certyfikat docelowego serwera poczty e-mail.

|Value|Akronim|Opis|
|---|---|---|
|01<sup></sup>|PKIX-TA|Używany certyfikat to publiczny urząd certyfikacji zakotwiczony w zaufaniu z łańcucha zaufania X.509.|
|11<sup></sup>|PKIX-EE|Sprawdzony certyfikat jest serwerem docelowym; Testy DNSSEC muszą zweryfikować jego autentyczność.|
|2|DANE-TA|Użyj klucza prywatnego serwera z drzewa X.509, który musi zostać zweryfikowany przez kotwicę zaufania w łańcuchu zaufania. Rekord TLSA określa kotwicę zaufania, która ma być używana do weryfikowania certyfikatów protokołu TLS dla domeny.|
|3|DANE-EE|Pasuje tylko do certyfikatu serwera docelowego.|

<sup>1</sup> Exchange Online jest zgodne ze wskazówkami implementacji RFC, których wartości pola użycia certyfikatu 0 lub 1 nie powinny być używane, gdy dane dane są implementowane za pomocą protokołu SMTP. Gdy do Exchange Online zostanie zwrócony rekord TLSA z wartością pola Użycie certyfikatu o wartości 0 lub 1, Exchange Online będzie traktować go jako niezdatny do użycia. Jeśli wszystkie rekordy TLSA zostaną uznane za bezużyteczne, Exchange Online podczas wysyłania wiadomości e-mail nie wykona kroków weryfikacji DANYCH dla wartości 0 lub 1. Zamiast tego ze względu na obecność rekordu TLSA Exchange Online wymusi użycie protokołu TLS do wysyłania wiadomości e-mail, wysyłania wiadomości e-mail, jeśli docelowy serwer poczty e-mail obsługuje protokół TLS, lub upuszczenia wiadomości e-mail i wygenerowania protokołu NDR, jeśli docelowy serwer poczty e-mail nie obsługuje protokołu TLS.

W przykładowym rekordzie TLSA pole Użycie certyfikatu jest ustawione na wartość "3", więc dane skojarzenia certyfikatu ("abc123... xyz789') będzie dopasowywany tylko do certyfikatu serwera docelowego.

**Pole selektora**: wskazuje, które części certyfikatu serwera docelowego powinny być sprawdzane.

|Value|Akronim|Opis|
|---|---|---|
|0|Cert|Użyj pełnego certyfikatu.|
|1|SPKI (informacje o kluczu publicznym podmiotu)|Użyj klucza publicznego certyfikatu i algorytmu, za pomocą którego jest identyfikowany klucz publiczny do użycia.|

W przykładowym rekordzie TLSA pole selektora jest ustawione na wartość "1", więc dane skojarzenia certyfikatów zostaną dopasowane przy użyciu klucza publicznego certyfikatu serwera docelowego i algorytmu, z którym jest identyfikowany klucz publiczny do użycia.

**Pasujące pole typu**: wskazuje format, w jakim certyfikat będzie reprezentowany w rekordzie TLSA.

|Value|Akronim|Opis|
|---|---|---|
|0|Pełne|Dane w rekordzie TSLA są pełnym certyfikatem lub infrastrukturą SPKI.|
|1|SHA-256|Dane w rekordzie TSLA są skrótem SHA-256 certyfikatu lub infrastruktury SPKI.|
|2|SHA-512|Dane w rekordzie TSLA są skrótem SHA-512 certyfikatu lub infrastruktury SPKI.|

W przykładowym rekordzie TLSA pole Typ dopasowania jest ustawione na wartość "1", więc dane skojarzenia certyfikatów są skrótem SHA-256 informacji o kluczu publicznym podmiotu z certyfikatu serwera docelowego

**Dane skojarzenia certyfikatów**: określa dane certyfikatu używane do dopasowywania do certyfikatu serwera docelowego. Te dane zależą od wartości Pola selektora i pasującej wartości typu.

W przykładowym rekordzie TLSA dane skojarzenia certyfikatów są ustawione na "abc123.. xyz789'. Ponieważ wartość Pola selektora w przykładzie jest ustawiona na wartość "1", będzie odwoływać się do klucza publicznego certyfikatu serwera docelowego i algorytmu, który jest identyfikowany do użycia z nim. A ponieważ wartość pola Typ dopasowania w przykładzie jest ustawiona na wartość "1", będzie odwoływać się do skrótu SHA-256 informacji o kluczu publicznym podmiotu z certyfikatu serwera docelowego.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Jak Exchange Online klienci mogą korzystać z ruchu wychodzącego SMTP DANE?

Jako klient Exchange Online nie musisz nic robić, aby skonfigurować to rozszerzone zabezpieczenia poczty e-mail dla wychodzącej poczty e-mail. Jest to coś, co zostało utworzone dla Ciebie i jest domyślnie włączone dla wszystkich klientów Exchange Online i jest używane, gdy domena docelowa anonsuje obsługę dane. Aby czerpać korzyści z wysyłania wiadomości e-mail z testami DNSSEC i DANE, przekaż partnerom biznesowym, z którymi wymieniasz wiadomości e-mail, które muszą zaimplementować usługi DNSSEC i DANE, aby mogli odbierać wiadomości e-mail przy użyciu tych standardów.

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Jak Exchange Online klienci mogą korzystać z ruchu przychodzącego SMTP DANE?

Obecnie dane SMTP dla ruchu przychodzącego nie są obsługiwane w przypadku Exchange Online. Oczekuje się, że wsparcie zostanie wydane pod koniec 2022 r.

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Jaka jest zalecana konfiguracja rekordu TLSA?

Zgodnie ze wskazówkami dotyczącymi implementacji RFC dla SMTP DANE zaleca się utworzenie rekordu TLSA składającego się z pola Użycie certyfikatu ustawionego na 3, pola Selektor ustawionego na 1 i pola Typ dopasowania ustawionego na 1.

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online Flow poczty za pomocą protokołu SMTP DANE

Proces przepływu poczty dla Exchange Online za pomocą protokołu SMTP DANE, pokazany na poniższym wykresie przepływowym, weryfikuje zabezpieczenia domeny i rekordu zasobów za pośrednictwem protokołu DNSSEC, obsługę protokołu TLS na docelowym serwerze poczty oraz że certyfikat docelowego serwera poczty jest zgodny z oczekiwaniami na podstawie skojarzonego rekordu TLSA.

Istnieją tylko dwa scenariusze, w których błąd SMTP DANE spowoduje zablokowanie wiadomości e-mail:

- Domena docelowa zasygnalizowała obsługę protokołu DNSSEC, ale co najmniej jeden rekord został zwrócony jako nieautentyczny.

- Wszystkie rekordy MX dla domeny docelowej mają rekordy TLSA i żaden z certyfikatów serwera docelowego nie jest zgodny z oczekiwanymi danymi rekordu TSLA lub połączenie TLS nie jest obsługiwane przez serwer docelowy.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange przepływu poczty online za pomocą protokołu SMTP DANE" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Powiązane technologie

|Technologia|Dodatkowe informacje|
|---|---|
|**Agent transferu poczty — ścisłe zabezpieczenia transportu (MTA-STS)** pomagają udaremnić ataki typu "downgrade" i "Man-in-the-Middle", zapewniając mechanizm ustawiania zasad domeny, które określają, czy docelowy serwer poczty e-mail obsługuje protokół TLS i co zrobić, gdy nie można wynegocjować protokołu TLS, na przykład zatrzymać transmisję.|Więcej informacji na temat nadchodzącej pomocy technicznej Exchange Online dla ruchu przychodzącego i wychodzącego MTA-STS zostanie opublikowanych jeszcze w tym roku. <br/><br/> [Exchange Online wiadomości transportowe z konferencji Microsoft Ignite 2020 — Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699) <br/><br/> [rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)|
|**Struktura zasad nadawcy (SPF)** używa informacji o adresach IP, aby upewnić się, że docelowe systemy poczty e-mail ufają komunikatom wysłanym z domeny niestandardowej.|[Jak struktura zasad nadawcy (SPF) zapobiega fałszowaniu — Office 365 — Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)|
|**Usługa DomainKeys Identified Mail (DKIM)** używa informacji o certyfikacie X.509, aby upewnić się, że docelowe systemy poczty e-mail ufają komunikatom wysyłanym wychodzącym z domeny niestandardowej.|[Jak używać programu DKIM do obsługi poczty e-mail w domenie niestandardowej — Office 365 — Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)|
|**Oparte na domenie uwierzytelnianie komunikatów, raportowanie i zgodność (DMARC)** współdziała z platformą zasad nadawcy i identyfikowaną pocztą domainKeys w celu uwierzytelniania nadawców poczty i zapewnienia, że docelowe systemy poczty e-mail ufają wiadomościom wysyłanym z twojej domeny.|[Sprawdzanie poprawności poczty e-mail, konfigurowanie kroków — Office 365 — Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)|

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Rozwiązywanie problemów z wysyłaniem wiadomości e-mail przy użyciu protokołu SMTP DANE

Obecnie istnieją cztery kody błędów dane podczas wysyłania wiadomości e-mail z Exchange Online. Firma Microsoft aktywnie aktualizuje tę listę kodów błędów. Błędy będą widoczne w następujących elementach:

1. Portal centrum administracyjnego Exchange za pośrednictwem widoku Szczegóły śledzenia komunikatów.
2. Serwery NDR generowane, gdy komunikat nie jest wysyłany z powodu błędu DANE lub DNSSEC.
3. Narzędzie analizatora łączności zdalnej [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|Kod NDR|Opis|
|---|---|
|5.7.321|starttls-not-supported: Docelowy serwer poczty musi obsługiwać protokół TLS do odbierania poczty.|
|5.7.322|certyfikat wygasł: certyfikat docelowego serwera poczty wygasł.|
|5.7.323|tlsa-invalid: Nie można zweryfikować danych DANE w domenie.|
|5.7.324|dnssec-invalid: domena docelowa zwróciła nieprawidłowe rekordy DNSSEC.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Rozwiązywanie problemów z programem starttls-not-supported w wersji 5.7.321

Zwykle oznacza to problem z docelowym serwerem poczty. Po otrzymaniu komunikatu:

1. Sprawdź, czy docelowy adres e-mail został wprowadzony poprawnie.
2. Ostrzec docelowego administratora poczty e-mail o tym kodzie błędu, aby mógł określić, czy serwer docelowy jest poprawnie skonfigurowany do odbierania komunikatów przy użyciu protokołu TLS.
3. Spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości w portalu centrum administracyjnego Exchange.

### <a name="troubleshooting-57322-certificate-expired"></a>Rozwiązywanie problemów z wygaśnięciem certyfikatu w wersji 5.7.322

Prawidłowy certyfikat X.509, który nie wygasł, musi zostać przedstawiony na serwerze poczty e-mail wysyłającej. Certyfikaty X.509 muszą być odnawiane po ich wygaśnięciu, często co rok. Po otrzymaniu komunikatu:

1. Wyślij alert do docelowego administratora poczty e-mail, który otrzymał ten kod błędu, i podaj ciąg kodu błędu.
2. Zaczekaj na odnowienie certyfikatu serwera docelowego i zaktualizowanie rekordu TLSA w celu odwołania się do nowego certyfikatu. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości w portalu centrum administracyjnego Exchange.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Rozwiązywanie problemów z błędem tlsa 5.7.323

Ten kod błędu jest związany z błędną konfiguracją rekordu TLSA i może być generowany tylko po zwróceniu rekordu TLSA uwierzytelniania DNSSEC. Istnieje wiele scenariuszy podczas walidacji DANE, które występują po zwróceniu rekordu, co może spowodować wygenerowanie kodu. Firma Microsoft aktywnie pracuje nad scenariuszami objętymi tym kodem błędu, aby każdy scenariusz miał określony kod. Obecnie co najmniej jeden z tych scenariuszy może spowodować wygenerowanie kodu błędu:

1. Certyfikat docelowego serwera poczty nie jest zgodny z oczekiwaniami dla autentycznego rekordu TLSA.
2. Autentyczny rekord TLSA jest nieprawidłowo skonfigurowany.
3. Domena docelowa jest atakowana.
4. Dowolny inny błąd DANE.

Po otrzymaniu komunikatu:

1. Wyślij alert do docelowego administratora poczty e-mail o otrzymaniu tego kodu błędu i podaj mu ciąg kodu błędu.
2. Zaczekaj czas na sprawdzenie przez docelowego administratora poczty e-mail konfiguracji danych i ważności certyfikatu serwera poczty e-mail. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości w portalu centrum administracyjnego Exchange.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Rozwiązywanie problemów z błędem dnssec 5.7.324

Ten kod błędu jest generowany, gdy domena docelowa wskazała, że jest ona autentyczna w usłudze DNSSEC, ale Exchange Online nie mogła zweryfikować jej jako dnssec-authentic.

Po otrzymaniu komunikatu:

1. Wyślij alert do docelowego administratora poczty e-mail o otrzymaniu tego kodu błędu i podaj mu ciąg kodu błędu.
2. Zaczekaj czas, aby docelowy administrator poczty e-mail przejrzał konfigurację DNSSEC swojej domeny. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości w portalu centrum administracyjnego Exchange.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Rozwiązywanie problemów z odbieraniem wiadomości e-mail za pomocą protokołu SMTP DANE

Obecnie istnieją dwie metody, których administrator domeny odbierającego może użyć do weryfikowania i rozwiązywania problemów z konfiguracją DNSSEC i DANE w celu otrzymywania wiadomości e-mail od Exchange Online przy użyciu tych standardów.

1. Wdrażanie protokołu SMTP TLS-RPT (Transport Layer Security Reporting) wprowadzonego w [dokumencie RFC8460](https://datatracker.ietf.org/doc/html/rfc8460)
2. Korzystanie z narzędzia Analizator łączności zdalnej [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) to mechanizm raportowania dla nadawców, który udostępnia administratorom domeny docelowej szczegółowe informacje o sukcesach i niepowodzeniach usług DANE i MTA-STS w tych domenach docelowych. Aby otrzymywać raporty TLS-RPT, należy dodać tylko rekord TXT w rekordach DNS domeny, który zawiera adres e-mail lub identyfikator URI, do którego chcesz wysłać raporty. Exchange Online będzie wysyłać raporty TLS-RPT w formacie JSON.

Przykładowy rekord:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Przykładowy rekord" lightbox="../media/compliance-trial/example-record.png":::

Drugą metodą jest użycie analizatora łączności zdalnej [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), który może wykonywać te same testy DNSSEC i DANE względem konfiguracji DNS, które Exchange Online będą wykonywane podczas wysyłania wiadomości e-mail poza usługą. Jest to najbardziej bezpośredni sposób rozwiązywania problemów z błędami w konfiguracji w celu otrzymywania wiadomości e-mail od Exchange Online przy użyciu tych standardów.

Podczas rozwiązywania problemów mogą zostać wygenerowane poniższe kody błędów:

|Kod NDR|Opis|
|---|---|
|4/5.7.321|starttls-not-supported: Docelowy serwer poczty musi obsługiwać protokół TLS do odbierania poczty.|
|4/5.7.322|certyfikat wygasł: certyfikat docelowego serwera poczty wygasł.|
|4/5.7.323|tlsa-invalid: Nie można zweryfikować danych DANE w domenie.|
|4/5.7.324|dnssec-invalid: domena docelowa zwróciła nieprawidłowe rekordy DNSSEC.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Rozwiązywanie problemów z programem starttls-not-supported w wersji 5.7.321

> [!NOTE]
> Te kroki dotyczą rozwiązywania problemów z otrzymywaniem wiadomości e-mail od administratorów poczty e-mail od Exchange Online przy użyciu protokołu SMTP DANE.

Zwykle oznacza to problem z docelowym serwerem poczty. Serwer poczty, z którym jest testowany analizator łączności zdalnej. Ogólnie istnieją dwa scenariusze, które generują ten kod:

1. Docelowy serwer poczty w ogóle nie obsługuje bezpiecznej komunikacji i musi być używana zwykła, nieszyfrowana komunikacja.
2. Serwer docelowy jest niepoprawnie skonfigurowany i ignoruje polecenie STARTTLS.

Po otrzymaniu komunikatu:

1. Sprawdź adres e-mail.
2. Znajdź adres IP skojarzony z instrukcją błędu, aby zidentyfikować serwer poczty, z który jest skojarzona instrukcja.
3. Sprawdź ustawienie serwera poczty, aby upewnić się, że jest on skonfigurowany do nasłuchiwania ruchu SMTP (zazwyczaj porty 25 i 587).
4. Zaczekaj kilka minut, a następnie spróbuj ponownie wykonać test za pomocą narzędzia Analizator łączności zdalnej.
5. Jeśli nadal nie powiedzie się, spróbuj usunąć rekord TLSA i ponownie uruchomić test za pomocą narzędzia Analizator łączności zdalnej.
6. Jeśli nie ma żadnych błędów, może to oznaczać, że serwer poczty, którego używasz do odbierania poczty, nie obsługuje protokołu STARTTLS i może być konieczne uaktualnienie do serwera, który ma być używany do używania danych DANE.

### <a name="troubleshooting-57322-certificate-expired"></a>Rozwiązywanie problemów z wygaśnięciem certyfikatu w wersji 5.7.322

> [!NOTE]
> Te kroki dotyczą rozwiązywania problemów z otrzymywaniem wiadomości e-mail od administratorów poczty e-mail od Exchange Online przy użyciu protokołu SMTP DANE.

Prawidłowy certyfikat X.509, który nie wygasł, musi zostać przedstawiony na serwerze poczty e-mail wysyłającej. Certyfikaty X.509 muszą być odnawiane po ich wygaśnięciu, często co rok. Po otrzymaniu komunikatu:

1. Sprawdź adres IP skojarzony z instrukcją błędu, aby zidentyfikować serwer poczty, z który jest skojarzony. Znajdź wygasły certyfikat na zidentyfikowanym serwerze poczty e-mail.
2. Zaloguj się do witryny internetowej dostawcy certyfikatów.
3. Wybierz wygasły certyfikat i postępuj zgodnie z instrukcjami, aby odnowić i zapłacić za odnowienie.
4. Po zweryfikowaniu zakupu przez dostawcę możesz pobrać nowy certyfikat.
5. Zainstaluj odnowiony certyfikat na skojarzonym serwerze poczty.
6. Zaktualizuj rekord TLSA skojarzony z serwerem poczty przy użyciu danych nowego certyfikatu.
7. Po odczekaniu odpowiedniego czasu ponów próbę testu za pomocą narzędzia Analizator łączności zdalnej.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Rozwiązywanie problemów z błędem tlsa 5.7.323

> [!NOTE]
> Te kroki dotyczą rozwiązywania problemów z otrzymywaniem wiadomości e-mail od administratorów poczty e-mail od Exchange Online przy użyciu protokołu SMTP DANE.

Ten kod błędu jest związany z błędną konfiguracją rekordu TLSA i może być generowany tylko po zwróceniu rekordu TSLA uwierzytelniania DNSSEC. Jednak podczas walidacji DANE występuje wiele scenariuszy, które występują po zwróceniu rekordu, co może spowodować wygenerowanie kodu. Firma Microsoft aktywnie pracuje nad scenariuszami objętymi tym kodem błędu, aby każdy scenariusz miał określony kod. Obecnie co najmniej jeden z tych scenariuszy może spowodować wygenerowanie kodu błędu:

1. Autentyczny rekord TLSA jest nieprawidłowo skonfigurowany.
2. Certyfikat nie jest jeszcze ważny/skonfigurowany dla przyszłego przedziału czasu.
3. Domena docelowa jest atakowana.
4. Dowolny inny błąd DANE.

Po otrzymaniu komunikatu:

1. Sprawdź adres IP skojarzony z instrukcją błędu, aby zidentyfikować serwer poczty, z który jest skojarzony.
2. Zidentyfikuj rekord TLSA skojarzony z zidentyfikowanym serwerem poczty.
3. Sprawdź konfigurację rekordu TLSA, aby upewnić się, że sygnalizuje nadawcy, że wykonuje preferowane kontrole DANE i że poprawne dane certyfikatu zostały uwzględnione w rekordzie TLSA.
    1. Jeśli musisz wprowadzić jakiekolwiek aktualizacje rekordu pod kątem rozbieżności, poczekaj kilka minut, a następnie ponownie uruchom test za pomocą narzędzia Analizator łączności zdalnej.
4. Znajdź certyfikat na zidentyfikowanym serwerze poczty.
5. Sprawdź przedział czasu, dla którego certyfikat jest prawidłowy. Jeśli jest ustawiona na rozpoczęcie ważności w przyszłości, należy ją odnowić dla bieżącej daty.
    1. Zaloguj się do witryny internetowej dostawcy certyfikatów.
    2. Wybierz wygasły certyfikat i postępuj zgodnie z instrukcjami, aby odnowić i zapłacić za odnowienie.
    3. Po zweryfikowaniu zakupu przez dostawcę możesz pobrać nowy certyfikat.
    4. Zainstaluj odnowiony certyfikat na skojarzonym serwerze poczty.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Rozwiązywanie problemów z błędem dnssec 5.7.324

> [!NOTE]
> Te kroki dotyczą rozwiązywania problemów z otrzymywaniem wiadomości e-mail od administratorów poczty e-mail od Exchange Online przy użyciu protokołu SMTP DANE.

Ten kod błędu jest generowany, gdy domena docelowa wskazuje, że jest autentyczna w usłudze DNSSEC, ale Exchange Online nie może zweryfikować jej jako dnssec-authentic. Ta sekcja nie będzie kompleksowa do rozwiązywania problemów z protokołem DNSSEC i koncentruje się na scenariuszach, w których domeny wcześniej przeszły uwierzytelnianie DNSSEC, ale nie teraz.

Po otrzymaniu komunikatu:

1. Jeśli używasz dostawcy DNS, na przykład GoDaddy, ostrzegaj dostawcę DNS o błędzie, aby mógł pracować nad zmianą rozwiązywania problemów i konfiguracji.
2. Jeśli zarządzasz własną infrastrukturą DNSSEC, istnieje wiele błędów konfiguracji DNSSEC, które mogą generować ten komunikat o błędzie. Niektóre typowe problemy dotyczące sprawdzania, czy strefa wcześniej przekazywała uwierzytelnianie DNSSEC:
    1. Przerwany łańcuch zaufania, gdy strefa nadrzędna zawiera zestaw rekordów DS wskazujących coś, co nie istnieje w strefie podrzędnej. Powoduje to, że strefa podrzędna jest oznaczona jako fałszywa przez walidację rozpoznawania.
        - Rozwiąż problem, przeglądając identyfikatory kluczy RRSIG domen podrzędnych i upewniając się, że są one zgodne z identyfikatorami kluczy w rekordach DS opublikowanych w strefie nadrzędnej.
    2. Rekord zasobu RRSIG dla domeny nie jest prawidłowy, wygasł lub jego okres ważności nie został rozpoczęty.
        - Rozwiąż problem, generując nowe podpisy dla domeny przy użyciu prawidłowych przedziałów czasu.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Czy jako klient Exchange Online mogę zrezygnować z używania protokołu DNSSEC i/lub DANE?

Jesteśmy przekonani, że serwery DNSSEC i DANE znacząco zwiększą pozycję bezpieczeństwa naszej usługi i przyniosą korzyści wszystkim naszym klientom. W ciągu ostatniego roku pilnie pracowaliśmy nad zmniejszeniem ryzyka i ważności potencjalnego wpływu tego wdrożenia na klientów M365. Będziemy aktywnie monitorować i śledzić wdrożenie, aby zapewnić zminimalizowanie negatywnego wpływu w miarę jego wdrażania. Z tego powodu wyjątki na poziomie dzierżawy lub rezygnacja nie będą dostępne.
Jeśli wystąpią problemy związane z włączaniem serwera DNSSEC i/lub DANE, różne metody badania błędów zanotowane w tym dokumencie pomogą Ci zidentyfikować źródło błędu. W większości przypadków problem dotyczy zewnętrznej strony docelowej i musisz przekazać tym partnerom biznesowym, że muszą prawidłowo skonfigurować serwery DNSSEC i DANE, aby otrzymywać wiadomości e-mail od Exchange Online przy użyciu tych standardów.

### <a name="how-does-dnssec-relate-to-dane"></a>Jak usługa DNSSEC odnosi się do danych DANE?

Serwer DNSSEC dodaje warstwę zaufania do rozpoznawania nazw DNS, wykorzystując infrastrukturę kluczy publicznych, aby upewnić się, że rekordy zwrócone w odpowiedzi na zapytanie DNS są autentyczne. DANE zapewnia, że serwer poczty odbierającego jest wiarygodnym i oczekiwanym serwerem poczty dla autentycznego rekordu MX.

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Jaka jest różnica między usługą MTA-STS i DANE dla protokołu SMTP?

Dane i MTA-STS służą do tego samego celu, ale dane wymagają protokołu DNSSEC do uwierzytelniania DNS, podczas gdy usługa MTA-STS korzysta z urzędów certyfikacji.

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Dlaczego oportunistyczny protokół TLS nie jest wystarczający?

Oportunistyczny protokół TLS szyfruje komunikację między dwoma punktami końcowymi, jeśli obie strony wyrażą zgodę na jej obsługę. Jednak nawet jeśli protokół TLS szyfruje transmisję, domena może zostać sfałszowana podczas rozpoznawania nazw DNS w taki sposób, że wskazuje punkt końcowy złośliwego aktora zamiast rzeczywistego punktu końcowego dla domeny. Jest to luka w zabezpieczeniach poczty e-mail, którą rozwiązuje implementacja usługi MTA-STS i/lub SMTP DANE za pomocą protokołu DNSSEC.

### <a name="why-isnt-dnssec-sufficient"></a>Dlaczego serwer DNSSEC nie jest wystarczający?

Serwer DNSSEC nie jest w pełni odporny na ataki typu Man-in-the-Middle i obniża poziom (od protokołu TLS do zwykłego tekstu) w scenariuszach przepływu poczty. Dodanie usług MTA-STS i DANE wraz z serwerem DNSSEC zapewnia kompleksową metodę zabezpieczeń, aby udaremnić ataki MITM i downgrade.

## <a name="additional-links"></a>Dodatkowe linki

[Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Omówienie | DNSSEC Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Sprawdzanie poprawności poczty e-mail, konfigurowanie kroków — Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Jak używać usługi DKIM do obsługi poczty e-mail w domenie niestandardowej — Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Jak struktura zasad nadawcy (SPF) zapobiega fałszowaniu — Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online wiadomości transportowe z konferencji Microsoft Ignite 2020 — Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)
