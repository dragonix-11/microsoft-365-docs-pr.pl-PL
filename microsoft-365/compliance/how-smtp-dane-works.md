---
title: Jak działa uwierzytelnianie oparte na systemie DNS SMTP nazwanych jednostek (DANE) do zabezpieczania komunikacji za pośrednictwem poczty e-mail
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
description: Dowiedz się, jak usługa SMTP uwierzytelniania nazwanych obiektów (DANE) na podstawie systemu DNS działa w celu zabezpieczania komunikacji e-mail między serwerami poczty.
ms.openlocfilehash: 32c39859d9bfdf292fd9c7a315a0ee1ee08eae2e
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009721"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Jak działa uwierzytelnianie oparte na systemie DNS SMTP dla nazwanych jednostek (DANE)

Protokół SMTP to główny protokół używany do przesyłania wiadomości między serwerami poczty i domyślnie nie jest bezpieczny. Protokół Transport Layer Security (TLS) został wprowadzony kilka lat temu w celu obsługi zaszyfrowanej transmisji wiadomości przez SMTP. Jest on często stosowany skojarzeń, a nie jako wymaganie, pozostawiając ruch poczty e-mail w przejrzystej tekście, narażona na punkt przecięcia przez fikcyjne szybkowanie. Ponadto protokół SMTP określa adresy IP serwerów docelowych za pośrednictwem publicznej infrastruktury DNS, która jest podatna na spoofing i ataki typu Man-in-the-Middle (MITM). W związku z tym utworzono wiele nowych standardów w celu zwiększenia bezpieczeństwa wysyłania i odbierania wiadomości e-mail. Jednym z nich jest uwierzytelnianie oparte na systemie DNS dla nazwanych obiektów (DANE).
  
Dane dla protokołu [SMTP RFC 7672](https://tools.ietf.org/html/rfc7672) korzysta z informacji o obecności rekordu TLSA (Transport Layer Security Authentication) w rekordzie DNS domeny ustawionym do zasygnalizować domenę, a jej serwery poczty obsługują DANE. Jeśli nie ma rekordu TLSA, rozpoznawanie DNS przepływu poczty e-mail będzie działać jak zwykle, bez konieczności przeprowadzania jakichkolwiek testów danych. Rekord TLSA bezpiecznie sygnalizuje obsługę usługi TLS i publikuje zasady DANE dla domeny. Dlatego wysyłanie serwerów poczty może pomyślnie uwierzytelnić wiarygodne serwery poczty odbieranej przy użyciu danych SMTP. Dzięki temu można ją bezbłędnie obniżyć i ataki MITM. Dane są zależne bezpośrednio od rekordu DNSSEC, który działa przez cyfrowe podpisywanie rekordów dla odnośników DNS za pomocą kryptografii klucza publicznego. Testy DNSSEC występują w przypadku rekurenujących rozpoznawania nazw DNS, czyli serwerów DNS, które wysyłają zapytania DNS dla klientów. Dzięki rekordowi DNSSEC rekordy DNS nie są modyfikowane i są autentyczne.  

Gdy rekord MX, rekordy A/AAAA i rekordy zasobów pokrewne w rekordzie DNSSEC domeny zostaną zwrócone do rekurentywnego rozpoznawania nazw DNS jako DNSSEC authentic, serwer poczty wysyłającej poprosi o rekord TLSA odpowiadający wpisom hosta MX. Jeśli rekord TLSA jest rekordem, który został sprawdzony jako autentyczny przy użyciu innego sprawdzania DNSSEC, rekurencyjna funkcji rozpoznawania nazw DNS zwróci rekord TLSA na wysyłający serwer poczty. 

Po otrzymaniu uwierzytelniania rekordu TLSA serwer wysyłający pocztę nawiązał połączenie SMTP z hostem MX skojarzonym z tym autentycznym rekordem TLSA. Wysyłający serwer poczty spróbuje skonfigurować usługę TLS i porównać certyfikat TLS serwera z danymi w rekordzie TLSA, aby sprawdzić, czy docelowy serwer poczty połączony z nadawcą jest legalnym serwerem poczty odbieranej. W przypadku powodzenia uwierzytelniania komunikat zostanie przesłany (przy użyciu protokołu TLS). Jeśli uwierzytelnianie zakończy się niepowodzeniem lub protokół TLS nie jest obsługiwany przez serwer docelowy, usługa Exchange Online ponownie spróbuje cały proces sprawdzania poprawności, począwszy od zapytania DNS dla tej samej domeny docelowej po 15 minutach, a potem 15 minut po tym czasie, a następnie co godzinę przez następne 24 godziny. Jeśli po 24 godzinach ponownego ponowienia uwierzytelnianie nadal się nie powiedzie, wiadomość wygaśnie, a do nadawcy zostanie wygenerowany raport o błędzie ze szczegółami błędów. 

## <a name="what-are-the-components-of-dane"></a>Co to są składniki danych?

### <a name="tlsa-resource-record"></a>Rekord zasobu TLSA

Rekord TLS Authentication (TLSA) służy do skojarzenia certyfikatu X.509 serwera lub wartości klucza publicznego z nazwą domeny, która zawiera ten rekord. Rekordy TLSA mogą być zaufane tylko wtedy, gdy w domenie włączono funkcję DNSSEC. Jeśli hostowanie domeny jest przez Ciebie hostowane za pomocą dostawcy dns, może to być ustawienie dostępne podczas konfigurowania domeny z nim. Aby dowiedzieć się więcej o podpisywaniu strefy DNSSEC, odwiedź ten link: [Omówienie zabezpieczeń DNSSEC | Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)). 
  
Przykładowy rekord TLSA:
  
:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Przykładowy rekord TLSA" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Istnieją cztery pola, które można skonfigurować jako unikatowe dla typu rekordu TLSA: 

**Pole użycie certyfikatu**: określa sposób, w jaki wysyłający serwer poczty e-mail powinien zweryfikować certyfikat docelowego serwera poczty e-mail.

|Value  |Akronim  |Opis |
|---------|---------|---------|
|01<sup></sup>     |PKIX-TA          |Używany certyfikat to publiczny urząd certyfikacji zakotwiczenia zaufania z łańcucha zaufania X.509.          |
|11<sup></sup>     |PKIX-EE         |Certyfikat jest sprawdzany jako serwer docelowy. Testy DNSSEC muszą zweryfikować autentyczność.          |
|2     |DANE-TA         |Użyj klucza prywatnego serwera z drzewa X.509, który musi być weryfikowany przez kotwicę zaufania w łańcuchu zaufania. Rekord TLSA określa kotwicę zaufania, która ma być używana do sprawdzania poprawności certyfikatów TLS dla domeny.         |
|3     |DANE-EE         |Są zgodne tylko z certyfikatem serwera docelowego.           |

<sup>1</sup> Exchange Online zgodnie z wytycznymi implementacji protokołu RFC, że wartości pola użycia certyfikatu 0 lub 1 nie powinny być używane podczas implementacji danych za pomocą protokołu SMTP.   Jeśli do usługi Exchange Online zostanie zwrócony rekord TLSA z polem Użycie certyfikatu o wartości 0 lub 1, Exchange Online nie nadaje się do użytku. Jeśli wszystkie rekordy TLSA nie będą Exchange Online, podczas wysyłania wiadomości e-mail nie będzie można wykonać procedury sprawdzania poprawności danych dla 0 lub 1. Ze względu na obecność rekordu TLSA program Exchange Online wymusi użycie usługi TLS do wysyłania wiadomości e-mail, wysyłania wiadomości e-mail, jeśli docelowy serwer poczty e-mail obsługuje TLS, lub upuszczanie wiadomości e-mail i generowanie raportów o niedostarczeniu, jeśli docelowy serwer poczty e-mail nie obsługuje usługi TLS.     

W przykładowym rekordzie TLSA pole Użycie certyfikatu ma wartość "3", więc dane skojarzenia certyfikatów ('abc123... xyz789') zostanie dopasowana tylko do certyfikatu serwera docelowego.

**Pole Selektor**: Wskazuje, które części certyfikatu serwera docelowego powinny być sprawdzane. 

|Value  |Akronim  |Opis  |
|---------|---------|---------|
|0     |Cert         |Użyj pełnego certyfikatu.         |
|1     |SPKI (informacje o kluczu publicznym tematu)          |Użyj klucza publicznego certyfikatu i algorytmu, dla którego ten klucz publiczny jest identyfikowany.          |

W przykładowym rekordzie TLSA pole Selektor ma wartość "1", więc dane skojarzenia certyfikatu zostaną dopasowane przy użyciu klucza publicznego certyfikatu serwera docelowego oraz algorytmu, z którym ten klucz publiczny jest identyfikowany.

**Pasujące pole typu**. Wskazuje format certyfikatu, który będzie reprezentowany w rekordzie TLSA. 

|Value  |Akronim  |Opis  |
|---------|---------|---------|
|0     |Pełne         |Dane w rekordzie TSLA to pełny certyfikat lub dodatek SPKI.          |
|1     |SHA-256         |Dane w rekordzie TSLA to skrót SHA-256 certyfikatu lub pliku SPKI.          |
|2     |SHA-512         |Dane w rekordzie TSLA to skrót SHA-512 certyfikatu lub pliku SPKI.         |

W przykładowym rekordzie TLSA pole Pasujące typ jest ustawione na wartość "1", więc dane skojarzenia certyfikatu to skrót SHA-256 tematu informacji o kluczu publicznym z certyfikatu serwera docelowego.

**Dane skojarzenia** certyfikatów. Określa dane certyfikatu, które są używane do dopasowywania do certyfikatu serwera docelowego. Te dane zależą od wartości pole selektora i wartości pasującego typu.

W przykładowym rekordzie TLSA dane skojarzenia certyfikatu są ustawione na wartość "abc123... xyz789'. Wartość Pole selektora w tym przykładzie ma wartość "1", dlatego odwołuje się ona do klucza publicznego certyfikatu serwera docelowego i algorytmu, który zostanie użyty z tym certyfikatem. Ponieważ w tym przykładzie wartość pola Typ dopasowania jest ustawiona na "1", odwołuje się ona do skrótu SHA-256 tematu informacji o kluczu publicznym z certyfikatu serwera docelowego.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Jak klienci Exchange Online korzystający z ruchu wychodzącego SMTP DANE?

Jako Exchange Online poczty wychodzącej nie musisz nic robić, aby skonfigurować to rozszerzone zabezpieczenia poczty e-mail dla poczty wychodzącej. Jest to coś, co dla Ciebie sbudowaliśmy i jest domyślnie włączone dla wszystkich klientów usługi Exchange Online i jest używane, gdy domena docelowa ogłasza obsługę danych. Aby ponownie wykorzystać zalety wysyłania wiadomości e-mail za pomocą testów DNSSEC i DANE, porozumiew się z partnerami biznesowymi, z którymi wymieniasz wiadomości e-mail, i przekaż im, że muszą oni zaimplementować ustawienia DNSSEC i Dane w celu otrzymywania wiadomości e-mail za pomocą tych standardów. 

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Jak klienci Exchange Online korzystający z ruchu przychodzącego SMTP DANE?

Obecnie dane serwera SMTP ruchu przychodzącego nie są obsługiwane w Exchange Online. Oczekuje się, że pomoc techniczna zostanie wydana pod koniec 2022 r. 

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Jaka jest zalecana konfiguracja rekordu TLSA?

Per RFC implementation guidance for SMTP DANE, a TLSA record composed of the Certificate Usage field set to 3, the Selector field set to 1, and the Matching Type field set to 1 is recommended. 

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online mail Flow dane SMTP 

Proces przepływu poczty e-mail dla programu Exchange Online z danemi SMTP przedstawiony na poniższym wykresie blokowym sprawdza poprawność zabezpieczeń rekordów domeny i zasobu za pośrednictwem rekordu DNSSEC, obsługi protokołu TLS na docelowym serwerze poczty e-mail oraz czy certyfikat docelowego serwera poczty jest taki, jaki jest oczekiwany, na podstawie skojarzonego z nim rekordu TLSA. 

Istnieją tylko dwa scenariusze, w których niepowodzenie danych SMTP spowoduje zablokowanie wiadomości e-mail:

- W domenie docelowej jest sygnalizowana obsługa protokołu DNSSEC, ale co najmniej jeden rekord został zwrócony jako nieuwierzyta. 

- Wszystkie rekordy MX dla domeny docelowej mają rekordy TLSA i żaden z certyfikatów serwera docelowego nie jest zgodne z oczekiwaniami co do danych rekordu TSLA lub połączenie TLS nie jest obsługiwane przez serwer docelowy.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange przepływ poczty e-mail online przy użyciu danych SMTP" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Technologie pokrewne 

|Technologia  |Dodatkowe informacje  |
|---------|---------|
|Agent transferu poczty — ścisłe zabezpieczenia transportu **(MTA-STS)** pomagają obniżyć wersję i ataki typu Man-in-the-Middle przez udostępnienie mechanizmu ustawiania zasad domeny określających, czy docelowy serwer poczty e-mail obsługuje TLS, i co zrobić, gdy nie można wynegocjować TLS, na przykład zatrzymać przesyłanie.     |Więcej informacji o Exchange Online dla przychodzących i wychodzących mtA-STS zostanie opublikowane później w tym roku.     [Exchange Online wiadomości na temat transportu z konferencji Microsoft Ignite 2020 — informacje techniczne Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)<br /><br />[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461) |
|**Spf (Sender Policy Framework) używa** informacji IP, aby zapewnić, że docelowe systemy poczty e-mail będą ufać wiadomościom wysyłanym z Twojej domeny niestandardowej.    |   [Jak spf (Sender Policy Framework) zapobiega spoofingowi — Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)      |
|**DKIM (DomainKeys Identified Mail)** używa informacji certyfikatu X.509 w celu zapewnienia, że docelowe systemy poczty e-mail zaufają wiadomościom wychodzącym z Twojej domeny niestandardowej.      | [Jak używać funkcji DKIM do obsługi poczty e-mail w domenie niestandardowej — Office 365 - Dokumenty Microsoft](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)        |
|**DMARC (Domain-based Message Authentication, Reporting, and Conformance)** działa z platformą zasad nadawców i identyfikowaną pocztą domenową w celu uwierzytelniania nadawców poczty i upewnienia się, że docelowe systemy poczty e-mail zaufają wiadomościom wysyłanym z Twojej domeny.      |  [Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail, kroków konfigurowania — Office 365 - Dokumenty Microsoft](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)       |

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Rozwiązywanie problemów z wysyłaniem wiadomości e-mail przy użyciu danych SMTP

Obecnie dane mają cztery kody błędów podczas wysyłania wiadomości e-mail z Exchange Online. Firma Microsoft aktywnie aktualizuje tę listę kodów błędów. Błędy będą widoczne w:
1.  Centrum Exchange administracyjnego za pośrednictwem widoku Szczegóły śledzenia wiadomości.
2.  Raporty o niedo wysłaniu są generowane, gdy wiadomość nie jest wysyłana z powodu błędu DANE lub DNSSEC.
3.  Narzędzie Remote Connectivity Analyzer [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|Kod błędu NDR  |Opis  |
|---------|---------|
|5.7.321     |starttls-not-supported: Docelowy serwer poczty musi obsługiwać usługę TLS w celu odbierania poczty.          |
|5.7.322     |certyfikat wygasł: Certyfikat serwera poczty docelowej wygasł.          |
|5.7.323     |tlsa-invalid: Sprawdzanie poprawności danych w domenie nie powiodło się.          |
|5.7.324     |dnssec-invalid: Domena docelowa zwróciła nieprawidłowe rekordy DNSSEC.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Rozwiązywanie problemów z błędem 5.7.321 starttls — nie jest obsługiwane

Zazwyczaj oznacza to problem z docelowym serwerem poczty. Po otrzymaniu wiadomości:
1.  Sprawdź, czy docelowy adres e-mail został wprowadzony poprawnie.
2.  Ostrzegaj administratora docelowej poczty e-mail o otrzymaniu tego kodu błędu, aby mógł ustalić, czy serwer docelowy jest poprawnie skonfigurowany do odbierania wiadomości za pomocą usługi TLS. 
3.  Spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości w portalu Centrum administracyjne usługi Exchange.

### <a name="troubleshooting-57322-certificate-expired"></a>Rozwiązywanie problemów z certyfikatem 5.7.322, który wygasł

Wysyłający serwer poczty e-mail musi zaprezentować prawidłowy certyfikat X.509, który nie wygasł. Po wygaśnięciu certyfikatów X.509 należy odnowić je (zazwyczaj co rok). Po otrzymaniu wiadomości:

1.  Ostrzegaj administratora docelowej poczty e-mail o otrzymaniu tego kodu błędu i podaj ciąg kodu błędu.
2.  Zezwalaj na odnowienie certyfikatu serwera docelowego i zaktualizowanie rekordu TLSA w celu odwołania się do nowego certyfikatu. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości dla tej wiadomości w portalu centrum Exchange administracyjnego.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Rozwiązywanie problemów z błędem 5.7.323 tlsa

Ten kod błędu jest związany z błędną konfiguracją rekordu TLSA i można go wygenerować dopiero po zwróceniu rekordu TLSA o uwierzytelnieniu DNSSEC. Istnieje wiele scenariuszy podczas sprawdzania poprawności danych, które występują po zwróceniu rekordu, co może spowodować wygenerowanie kodu. Firma Microsoft aktywnie pracuje nad scenariuszami, które są objęte tym kodem błędu, dzięki czemu każdy scenariusz ma określony kod. Obecnie co najmniej jeden z tych scenariuszy może powodować generowanie kodu błędu:

1.  Certyfikat docelowego serwera poczty nie jest zgodne z oczekiwaniami w przypadku uwierzytelniania rekordu TLSA.
2.  Authentic TLSA record is misconfigured .
3.  Domena docelowa jest atakiem.
4.  Jakiekolwiek inne błędy danych.

Po otrzymaniu wiadomości:

1. Ostrzegaj administratora docelowej poczty e-mail o tym, że został otrzymany ten kod błędu, i podaj jego ciąg kodu błędu.
2. Zezwalaj docelowym administratorowi poczty e-mail na sprawdzenie ich konfiguracji danych i ważności certyfikatu serwera poczty e-mail. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości dla tej wiadomości w portalu centrum Exchange administracyjnego.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Rozwiązywanie problemów z błędem 5.7.324 dnssec-invalid

Ten kod błędu jest generowany, gdy domena docelowa wskazuje, że jest ona DNSSEC-authentic, Exchange Online nie mogła zweryfikować jej jako DNSSEC-authentic. 

Po otrzymaniu wiadomości:

1. Ostrzegaj administratora docelowej poczty e-mail o tym, że został otrzymany ten kod błędu, i podaj jego ciąg kodu błędu.
2. Miej czas na przejrzenie konfiguracji DNSSEC swojej domeny przez docelowego administratora poczty e-mail. Następnie spróbuj ponownie wysłać wiadomość e-mail i przejrzyj szczegóły śledzenia wiadomości dla tej wiadomości w portalu centrum Exchange administracyjnego.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Rozwiązywanie problemów z odbieraniem wiadomości e-mail za pomocą DANYCH SMTP

Obecnie istnieją dwie metody, za pomocą których administrator domeny odbieracej może sprawdzać poprawność konfiguracji DNSSEC i DANE i rozwiązywać problemy z tymi konfiguracjami, aby odbierać wiadomości e-mail z usługi Exchange Online za pomocą tych standardów. 

1. Przyjęcie protokołu SMTP TLS-RPT (Transport Layer Security Reporting), wprowadzonego w dokumencie [RFC8460](https://datatracker.ietf.org/doc/html/rfc8460) 
2. Używanie narzędzia Remote Connectivity Analyzer programu [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) to mechanizm raportowania dla nadawców, który dostarcza administratorom domen docelowych szczegółowych informacji o sukcesach i niepowodzeniach MTA-STS dla odpowiednich domen docelowych. Aby otrzymywać raporty TLS-RPT, wystarczy dodać rekord TXT w rekordach DNS swojej domeny, który zawiera adres e-mail lub adres URI, na który mają być wysyłane raporty. Exchange Online będą wysyłać raporty TLS-RPT w formacie JSON. 

Przykładowy rekord:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Przykładowy rekord" lightbox="../media/compliance-trial/example-record.png":::

Drugą metodą jest użycie analizatora łączności zdalnej firmy [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), który może sprawdzać dane w ten sam sposób pod względem konfiguracji DNS, która jest sprawdzana przez usługę Exchange Online podczas wysyłania poczty e-mail poza usługę. Jest to najbardziej bezpośredni sposób rozwiązywania problemów z błędami w konfiguracji w celu otrzymywania wiadomości e-mail od Exchange Online tych standardów. 

Podczas rozwiązywania problemów mogą zostać wygenerowane poniższe kody błędów:

|Kod błędu NDR  |Opis |
|---------|---------|
|4/5.7.321     |starttls-not-supported: Docelowy serwer poczty musi obsługiwać usługę TLS w celu odbierania poczty.          |
|4/5.7.322     |certyfikat wygasł: Certyfikat serwera poczty docelowej wygasł.          |
|4/5.7.323    |tlsa-invalid: Sprawdzanie poprawności danych w domenie nie powiodło się.         |
|4/5.7.324     |dnssec-invalid: Domena docelowa zwróciła nieprawidłowe rekordy DNSSEC.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Rozwiązywanie problemów z błędem 5.7.321 starttls — nie jest obsługiwane

> [!NOTE]
> Poniższe instrukcje są dostępne dla administratorów poczty e-mail w celu rozwiązywania problemów z odbieraniem wiadomości e-mail Exchange Online danych SMTP.

Zazwyczaj oznacza to problem z docelowym serwerem poczty. Serwer poczty, za pomocą którego Remote Connectivity Analyzer testuje nawiązywanie połączenia. Ten kod można wygenerować na ogół w dwóch scenariuszach: 

1.  Docelowy serwer poczty w ogóle nie obsługuje bezpiecznej komunikacji i musi być używana zwykła, nie zaszyfrowana komunikacja. 
2.  Serwer docelowy jest skonfigurowany nieprawidłowo i ignoruje polecenie STARTTLS.
    
Po otrzymaniu wiadomości:

1. Sprawdź adres e-mail.
2. Znajdź adres IP skojarzony z oświadczeniem o błędzie, aby zidentyfikować serwer poczty, z którym jest skojarzona instrukcja.
3. Sprawdź ustawienia serwera poczty, aby upewnić się, że jest on skonfigurowany do odsłuchiwać ruch SMTP (zazwyczaj porty 25 i 587).
4. Poczekaj kilka minut, a następnie ponów próbę za pomocą narzędzia Remote Connectivity Analyzer.
5. Jeśli to nadal nie powiedzie się, spróbuj usunąć rekord TLSA i ponownie uruchom test za pomocą narzędzia Remote Connectivity Analyzer.
6. Jeśli nie występują żadne błędy, może to wskazywać, że serwer poczty, za pomocą których odbierasz pocztę, nie obsługuje funkcji STARTTLS, i może być konieczne uaktualnienie do serwera, który obsługuje dane. 

### <a name="troubleshooting-57322-certificate-expired"></a>Rozwiązywanie problemów z certyfikatem 5.7.322, który wygasł

> [!NOTE]
> Poniższe instrukcje są dostępne dla administratorów poczty e-mail w celu rozwiązywania problemów z odbieraniem wiadomości e-mail Exchange Online danych SMTP.

Wysyłający serwer poczty e-mail musi zaprezentować prawidłowy certyfikat X.509, który nie wygasł. Po wygaśnięciu certyfikatów X.509 należy odnowić je (zazwyczaj co rok). Po otrzymaniu wiadomości:

1. Sprawdź adres IP skojarzony z oświadczeniem o błędzie, aby zidentyfikować serwer poczty, z którym jest skojarzony. Odszukaj wygasły certyfikat na wskazanym serwerze poczty e-mail.
2. Zaloguj się w witrynie internetowej dostawcy certyfikatu.
3. Wybierz wygasły certyfikat i postępuj zgodnie z instrukcjami, aby odnowić subskrypcję i zapłacić za odnowienie.
4. Po zweryfikowaniu zakupu przez dostawcę możesz pobrać nowy certyfikat.
5. Zainstaluj odnowiony certyfikat na skojarzonym z nim serwerze poczty.
6. Zaktualizuj rekord TLSA skojarzonego z serwerem poczty przy użyciu danych nowego certyfikatu. 
7. Po upływie odpowiedniego czasu ponów próbę za pomocą narzędzia Remote Connectivity Analyzer.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Rozwiązywanie problemów z błędem 5.7.323 tlsa

> [!NOTE]
> Poniższe instrukcje są dostępne dla administratorów poczty e-mail w celu rozwiązywania problemów z odbieraniem wiadomości e-mail Exchange Online danych SMTP.

Ten kod błędu jest związany z błędną konfiguracją rekordu TLSA i można go wygenerować dopiero po zwróceniu rekordu TSLA uwierzytelnienia DNSSEC. Istnieje jednak wiele scenariuszy podczas sprawdzania poprawności danych, które występują po zwróceniu rekordu, co może spowodować wygenerowanie kodu. Firma Microsoft aktywnie pracuje nad scenariuszami, które są objęte tym kodem błędu, dzięki czemu każdy scenariusz ma określony kod. Obecnie co najmniej jeden z tych scenariuszy może powodować generowanie kodu błędu:

1. Authentic TLSA record is misconfigured .
2. Certyfikat nie jest jeszcze prawidłowy/skonfigurowany dla przyszłego okna czasowego. 
3. Domena docelowa jest atakowana.
4. Jakiekolwiek inne błędy danych.

Po otrzymaniu wiadomości:

1. Sprawdź adres IP skojarzony z oświadczeniem o błędzie, aby zidentyfikować serwer poczty, z którym jest skojarzony. 
2. Zidentyfikuj rekord TLSA skojarzony z wskazanym serwerem poczty. 
3. Sprawdź konfigurację rekordu TLSA, aby upewnić się, że nadawca sygnalizuje nadawcę do przeprowadzenia preferowanych testów danych i że w rekordzie TLSA zostały uwzględnione poprawne dane certyfikatu. 
    1. Jeśli musisz wprowadzić jakiekolwiek aktualizacje rekordu w przypadku rozbieżności, poczekaj kilka minut, a następnie ponownie uruchomić test za pomocą narzędzia Remote Connectivity Analyzer. 
4. Znajdź certyfikat na wskazanym serwerze poczty.
5. Sprawdź okres, dla którego certyfikat jest prawidłowy. Jeśli okres ważności jest ustawiony na datę ważności w przyszłości, należy ją odnowić na bieżący dzień.
    1. Zaloguj się w witrynie internetowej dostawcy certyfikatu.
    2. Wybierz wygasły certyfikat i postępuj zgodnie z instrukcjami, aby odnowić subskrypcję i zapłacić za odnowienie.
    3. Po zweryfikowaniu zakupu przez dostawcę możesz pobrać nowy certyfikat.
    4. Zainstaluj odnowiony certyfikat na skojarzonym z nim serwerze poczty.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Rozwiązywanie problemów z błędem 5.7.324 dnssec-invalid

> [!NOTE]
> Poniższe instrukcje są dostępne dla administratorów poczty e-mail w celu rozwiązywania problemów z odbieraniem wiadomości e-mail Exchange Online danych SMTP.

Ten kod błędu jest generowany, gdy domena docelowa wskazuje, że jest ona DNSSEC-authentic, Exchange Online nie może zweryfikować jej jako DNSSEC-authentic. Ta sekcja nie będzie pełna w zakresie rozwiązywania problemów z rekordami DNSSEC i skupia się na scenariuszach, w których domeny wcześniej przeszła uwierzytelnianie DNSSEC, ale nie teraz. 

Po otrzymaniu wiadomości:

1. Jeśli korzystasz z dostawcy hostingu DNS, na przykład GoDaddy, poślij dostawcy hostingu DNS o błędzie, aby może on pracować nad rozwiązywaniem problemów i zmianami konfiguracji. 
2. Jeśli zarządzasz własną infrastrukturą DNSSEC, istnieje wiele błędów konfiguracji DNSSEC, które mogą powodować generowanie tego komunikatu o błędzie. Niektóre typowe problemy do sprawdzenia, czy strefa wcześniej mieła uwierzytelnianie DNSSEC:
    1. Przerwany łańcuch zaufania, gdy strefa nadrzędna zawiera zestaw rekordów DS, które wskazują na element, który nie istnieje w strefie podrzędnej. W wyniku tego strefa podrzędna jest oznaczana jako błędna przez sprawdzania poprawności nazw. 
        - Rozwiąż, przeglądając identyfikatory kluczy domen podrzędnych RRSIG i upewniając się, że są one zgodne z identyfikatorami kluczy w rekordach DS opublikowanych w strefie nadrzędnej. 
    2. Rekord zasobu RRSIG dla domeny jest nieprawidłowy, wygasł albo okres ważności nie rozpoczął się. 
        - Rozwiąż, generując nowe podpisy dla domeny przy użyciu prawidłowych czasów. 

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Czy jako Exchange Online mogę zrezygnować z używania danych i DNSSEC?

Zdecydowanie uważamy, że dane DNSSEC znacznie zwiększą pozycję zabezpieczeń naszej usługi i przysyłają korzyści wszystkim naszym klientom. W ciągu ostatniego roku pracowaliśmy bardzo wyraźnie nad zmniejszeniem ryzyka i istotności potencjalnego wpływu, jaki może to mieć to wdrożenie dla klientów korzystających z usługi M365. Będziemy aktywnie monitorować i śledzić wdrożenie, aby zapewnić zminimalizowanie negatywnego wpływu w czasie jego wdrażania. Z tego powodu wyjątki na poziomie dzierżawy lub rezygnacja nie będą dostępne.
W przypadku wystąpienia jakichkolwiek problemów związanych z włączeniem serwerów DNSSEC i(lub) DANE różne metody badania błędów zanotowania w tym dokumencie pomogą zidentyfikować źródło błędu. W większości przypadków problem dotyczy zewnętrznej strony docelowej i musisz zakomunikować tym partnerom biznesowym, że muszą oni poprawnie skonfigurować dnssec i dane, aby odbierać wiadomości e-mail od firmy Exchange Online z zastosowaniem tych standardów.

### <a name="how-does-dnssec-relate-to-dane"></a>Jak rekordy DNSSEC są powiązane z danem?

Rekord DNSSEC dodaje warstwę zaufania do rozpoznawania nazw DNS, wykorzystując infrastrukturę kluczy publicznych, aby zapewnić autentyczność rekordów zwróconych w odpowiedzi na zapytanie DNS. Dane zapewnia, że odbierający serwer poczty jest prawdziwym i oczekiwanym serwerem poczty dla uwierzytelniania rekordu MX. 

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Jaka jest różnica między usługami MTA-STS i DANE dla serwera SMTP?

Dane i PROTOKOŁY MTA-STS służą do tego samego celu, ale dane wymagają uwierzytelniania DNSSEC, podczas gdy mtA-STS korzysta z urzędów certyfikacji. 

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Dlaczego nie jest wystarczający operacyjny adres TLS?

Opportunistic TLS will encrypt communication between two endpoints if both agree to support it. Jednak nawet jeśli szyfrowanie TLS transmisji jest szyfrowane, podczas rozpoznawania nazw DNS domena może być sfałszowana, tak aby wskazujeła punkt końcowy złośliwego podmiotu (a nie rzeczywisty punkt końcowy domeny). Jest to przerwa w zabezpieczeniach poczty e-mail, która rozwiązano, implementując dane MTA-STS i/lub SMTP z rekordem DNSSEC.  

### <a name="why-isnt-dnssec-sufficient"></a>Dlaczego rekord DNSSEC nie jest wystarczający?

Rekord DNSSEC nie jest w pełni odporny na ataki typu Man-in-the-Middle i ataki na starszą wersję (z protokołu TLS w celu wyczyszczenia tekstu) w scenariuszach przepływu poczty e-mail. Dodanie usług MTA-STS i DANE oraz DNSSEC zapewnia pełną metodę zabezpieczeń, która umożliwia udaremnianie zarówno ataków MITM, jak i ataków na starszą wersję.

## <a name="additional-links"></a>Dodatkowe linki 

[Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Omówienie zabezpieczeń DNSSEC | Microsoft Docs ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail, kroków konfigurowania — Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Jak używać funkcji DKIM do poczty e-mail w domenie niestandardowej — Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Jak struktury zasad dotyczących nadawców (SPF) chronią przed fałszer Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online wiadomości na temat transportu z konferencji Microsoft Ignite 2020 — informacje techniczne Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)