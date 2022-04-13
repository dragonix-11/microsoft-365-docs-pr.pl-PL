---
title: Rekordy systemu nazw domen zewnętrznych dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: Lista referencyjna zewnętrznych rekordów systemu nazw domen do użycia podczas planowania wdrożenia Office 365.
ms.openlocfilehash: 47a8bfe283041ad0350cfdf1db0b9e97bfa18b60
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824833"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Rekordy systemu nazw domen zewnętrznych dla Office 365

![Domeny.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Chcesz wyświetlić niestandardową listę rekordów DNS dla organizacji Office 365?** Informacje [potrzebne do utworzenia Office 365 rekordów DNS](../admin/get-help-with-domains/information-for-dns-records.md) dla domeny można znaleźć w Office 365.

**Potrzebujesz pomocy krok po kroku, aby dodać te rekordy na hoście DNS domeny, takim jak GoDaddy lub eNom?** [Znajdź linki do instrukcji krok po kroku dla wielu popularnych hostów DNS](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Trzymać się używać listy referencyjnej dla własnego wdrożenia niestandardowego?** Poniższa lista powinna być używana jako odwołanie do niestandardowego wdrożenia Office 365. Musisz wybrać, które rekordy dotyczą Twojej organizacji, i wypełnić odpowiednie wartości.

**Wstecz do** [planowania sieci i dostrajania wydajności dla Office 365](./network-planning-and-performance.md).

Często rekordy SPF i MX są najtrudniejsze do ustalenia. Na końcu tego artykułu zaktualizowaliśmy wskazówki dotyczące rekordów SPF. Ważne jest, aby pamiętać, że _możesz mieć tylko jeden rekord SPF dla swojej domeny_. Możesz mieć wiele rekordów MX; Może to jednak powodować problemy z dostarczaniem poczty. Posiadanie pojedynczego rekordu MX, który kieruje pocztę e-mail do jednego systemu poczty, usuwa wiele potencjalnych problemów.

Poniższe sekcje są zorganizowane według usługi w Office 365. Aby wyświetlić niestandardową listę Office 365 rekordów DNS dla domeny, zaloguj się do Office 365 i [zbierz informacje potrzebne do utworzenia Office 365 rekordów DNS](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).

## <a name="external-dns-records-required-for-office-365-core-services"></a>Zewnętrzne rekordy DNS wymagane dla Office 365 (usługi podstawowe)
<a name="BKMK_ReqdCore"> </a>

Rekord TXT jest potrzebny, aby udowodnić, że jesteś właścicielem domeny i jest wymagany dla wszystkich klientów.

Rekord CNAME jest wymagany tylko dla klientów korzystających z [Office 365 obsługiwanych przez firmę 21Vianet](/microsoft-365/admin/services-in-china/services-in-china). Zapewnia to, że Office 365 może kierować stacje robocze do uwierzytelniania przy użyciu odpowiedniej platformy tożsamości.

|Rekord DNS|Celu|Wartość do użycia|Dotyczy|
|---|---|---|---|
|**TXT** <br/> **(Weryfikacja domeny)**|Używane przez Office 365 do sprawdzania tylko, czy jesteś właścicielem domeny. Nie ma to wpływu na nic innego.|**Host:** @ (lub, dla niektórych dostawców hostingu DNS, nazwa domeny) <br/> **Wartość TXT:** _ciąg tekstowy dostarczony przez_ Office 365 <br/> **Kreator konfiguracji domeny** Office 365 zawiera wartości używane do utworzenia tego rekordu.|Wszyscy klienci|
|**CNAME** <br/> **(Pakiet)**|Używane przez Office 365 do kierowania uwierzytelniania do właściwej platformy tożsamości. [Więcej informacji](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Należy pamiętać**, że ten CNAME dotyczy tylko Office 365 obsługiwanych przez firmę 21Vianet. Jeśli Office 365 nie jest obsługiwany przez firmę 21Vianet, użytkownicy w domenie niestandardowej otrzymają błąd "*domena niestandardowa* nie jest w naszym systemie" i nie będą mogli aktywować licencji Office 365. [Więcej informacji](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Alias:** msoid <br/> **Cel:** clientconfig.partner.microsoftonline-p.net.cn| Tylko klienci 21Vianet|

## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Zewnętrzne rekordy DNS wymagane dla poczty e-mail w Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Wiadomość e-mail w Office 365 wymaga kilku różnych rekordów. Trzy rekordy podstawowe, których powinni używać wszyscy klienci, to rekordy wykrywania automatycznego, MX i SPF.

- **Rekord wykrywania automatycznego** umożliwia komputerom klienckim automatyczne znajdowanie Exchange i prawidłowe konfigurowanie klienta.

- **Rekord MX** informuje inne systemy poczty, gdzie wysyłać wiadomości e-mail dla twojej domeny. **Uwaga:** Po zmianie adresu e-mail na Office 365 przez zaktualizowanie rekordu MX domeny wszystkie wiadomości e-mail wysyłane do tej domeny zaczną przychodzić do Office 365.
Czy chcesz po prostu przełączyć kilka adresów e-mail na Office 365? Możesz [pilotować Office 365 z kilkoma adresami e-mail w domenie niestandardowej](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **Rekord TXT dla SPF** jest używany przez systemy poczty e-mail adresata do sprawdzania, czy serwer wysyłający wiadomość e-mail jest zatwierdzany. Pomaga to zapobiegać problemom, takim jak fałszowanie wiadomości e-mail i wyłudzanie informacji. Zobacz [zewnętrzne rekordy DNS wymagane dla SPF](external-domain-name-system-records.md#BKMK_SPFrecords) w tym artykule, aby dowiedzieć się, co należy uwzględnić w rekordzie.

Klienci poczty e-mail korzystający z Exchange Federation będą również potrzebować dodatkowego rekordu CNAME i TXT wymienionego w dolnej części tabeli.

|Rekord DNS|Celu|Wartość do użycia|
|---|---|---|
|**CNAME** <br/> **(Exchange Online)**|Ułatwia Outlook klientom łatwe łączenie się z usługą Exchange Online przy użyciu usługi wykrywania automatycznego. Wykrywanie automatyczne automatycznie znajduje prawidłowy host Exchange Server i konfiguruje Outlook dla użytkowników.|**Alias:** Automatycznego wykrywania <br/> **Wartość docelowa:** autodiscover.outlook.com|
|**MX** <br/> **(Exchange Online)**|Wysyła pocztę przychodzącą dla domeny do usługi Exchange Online w Office 365. <br/> **Uwaga:** Po wysłaniu wiadomości e-mail do Exchange Online należy usunąć rekordy MX wskazujące stary system. |**Domeny:** Na przykład contoso.com <br/> **Docelowy serwer poczty e-mail:**\<MX token\>. mail.protection.outlook.com <br/> **Wartość czasu wygaśnięcia (TTL):** 3600 <br/> **Preferencja/priorytet:** Niższe niż jakiekolwiek inne rekordy MX (dzięki temu poczta jest dostarczana do Exchange Online) — na przykład 1 lub "niska" <br/> Znajdź swoje, \<MX token\> wykonując następujące kroki: <br/> Zaloguj się do Office 365, przejdź do Office 365 domen administratora\>. <br/> W kolumnie Akcja dla domeny wybierz pozycję Rozwiąż problemy. <br/> W sekcji Rekordy MX wybierz pozycję Co mogę naprawić? <br/> Postępuj zgodnie z instrukcjami na tej stronie, aby zaktualizować rekord MX. <br/> [Co to jest priorytet rekordu MX?](../admin/setup/domains-faq.yml)|
|**SPF (TXT)** <br/> **(Exchange Online)**|Pomaga uniemożliwić innym osobom wysyłanie spamu lub innych złośliwych wiadomości e-mail przy użyciu twojej domeny. Rekordy platformy zasad nadawcy (SPF) działają, identyfikując serwery autoryzowane do wysyłania wiadomości e-mail z domeny.|[Zewnętrzne rekordy DNS wymagane dla SPF](external-domain-name-system-records.md#BKMK_SPFrecords)|
|**TXT** <br/> **(federacja Exchange)**|Służy do Exchange federacji wdrożenia hybrydowego.|**Rekord TXT 1:** Na przykład contoso.com i skojarzony niestandardowy, odporny na domenę tekst skrótu (na przykład Y96nu89138789315669824) <br/> **Rekord TXT 2:** Na przykład exchangedelegation.contoso.com i skojarzony niestandardowy, odporny na domenę tekst skrótu (na przykład Y3259071352452626169)|
|**CNAME** <br/> **(federacja Exchange)**|Ułatwia Outlook klientom łatwe nawiązywanie połączenia z usługą Exchange Online przy użyciu usługi wykrywania automatycznego, gdy firma korzysta z federacji Exchange. Funkcja wykrywania automatycznego automatycznie znajduje prawidłowy host Exchange Server i konfiguruje Outlook dla użytkowników.|**Alias:** Na przykład Autodiscover.service.contoso.com <br/> **Wartość docelowa:** autodiscover.outlook.com|

## <a name="external-dns-records-required-for-skype-for-business-online"></a>Zewnętrzne rekordy DNS wymagane dla usługi Skype dla firm Online
<a name="BKMK_ReqdCore"> </a>

Istnieją konkretne kroki, które należy wykonać, gdy używasz [Office 365 adresów URL i zakresów adresów IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO), aby upewnić się, że sieć jest prawidłowo skonfigurowana.

> [!NOTE]
> Te rekordy DNS mają również zastosowanie do Teams, zwłaszcza w scenariuszu Teams hybrydowego i Skype dla firm, w którym mogą wystąpić pewne problemy z federacją.

|Rekord DNS|Celu|Wartość do użycia|
|---|---|---|
|**SRV** <br/> **(Skype dla firm Online)**|Umożliwia domenie Office 365 udostępnianie funkcji wiadomości błyskawicznych klientom zewnętrznym przez włączenie federacji SIP. Przeczytaj więcej na temat [Office 365 adresów URL i zakresów adresów IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).|**Usługa:** sipfederationtls <br/> **Protokół:** TCP <br/> **Priorytet:** 100 <br/> **Waga:** 1 <br/> **Port:** 5061 <br/> **Cel:** sipfed.online.lync.com <br/> **Uwaga:** Jeśli zapora lub serwer proxy blokuje wyszukiwania SRV w zewnętrznym systemie DNS, należy dodać ten rekord do wewnętrznego rekordu DNS. |
|**SRV** <br/> **(Skype dla firm Online)**|Używane przez Skype dla firm do koordynowania przepływu informacji między klientami programu Lync.|**Usługa:** sip <br/> **Protokół:** TLS <br/> **Priorytet:** 100 <br/> **Waga:** 1 <br/> **Port:** 443 <br/> **Cel:** sipdir.online.lync.com|
|**CNAME** <br/> **(Skype dla firm Online)**|Używany przez klienta programu Lync do znajdowania usługi Skype dla firm Online i logowania.|**Alias:** sip <br/> **Cel:** sipdir.online.lync.com <br/> Aby uzyskać więcej informacji, zobacz [Office 365 adresów URL i zakresów adresów IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).|
|**CNAME** <br/> **(Skype dla firm Online)**|Używany przez klienta mobilnego programu Lync do znajdowania usługi Skype dla firm Online i logowania.|**Alias:** lyncdiscover <br/> **Cel:** webdir.online.lync.com|

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Zewnętrzne rekordy DNS wymagane do Office 365 pojedynczego Sign-On
<a name="BKMK_ReqdCore"> </a>

|Rekord DNS|Celu|Wartość do użycia|
|---|---|---|
|**Host (A)**|Używany do logowania jednokrotnego. Zapewnia punkt końcowy dla użytkowników lokalnych (i użytkowników lokalnych, jeśli chcesz), aby połączyć się z serwerami proxy serwera federacyjnego Active Directory Federation Services (AD FS) lub wirtualnym adresem IP (VIP) z równoważeniem obciążenia.|**Docelowego:** Na przykład sts.contoso.com|

## <a name="external-dns-records-required-for-spf"></a>Zewnętrzne rekordy DNS wymagane dla SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> Mechanizm SPF ułatwia zapobieganie podszywaniu się, ale istnieją techniki podszywania się, przed którymi mechanizm SPF nie chroni. Aby się przed tym chronić, po skonfigurowaniu SPF należy również skonfigurować DKIM i DMARC dla Office 365. Aby rozpocząć, zobacz [Używanie modułu DKIM do weryfikowania wychodzących wiadomości e-mail wysłanych z domeny w Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Następnie zobacz [Używanie usługi DMARC do weryfikowania poczty e-mail w Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).

Rekordy SPF to rekordy TXT, które uniemożliwiają innym osobom wysyłanie spamu lub innych złośliwych wiadomości e-mail przy użyciu twojej domeny. Rekordy platformy zasad nadawcy (SPF) działają, identyfikując serwery autoryzowane do wysyłania wiadomości e-mail z domeny.

Możesz mieć tylko jeden rekord SPF (tj. rekord TXT definiujący SPF) dla domeny. Ten pojedynczy rekord może mieć kilka różnych inkluzywek, ale łączna liczba wyszukiwań DNS, które powodują, że wynik nie może być większy niż 10 (pomaga to zapobiegać atakom typu "odmowa usługi"). Zapoznaj się z tabelą i innymi przykładami poniżej, aby ułatwić tworzenie lub aktualizowanie odpowiednich wartości rekordów SPF dla środowiska.

### <a name="structure-of-an-spf-record"></a>Struktura rekordu SPF

Wszystkie rekordy SPF zawierają trzy części: deklarację, że jest to rekord SPF, domeny i adresy IP, które powinny wysyłać wiadomości e-mail, oraz regułę wymuszania. Wszystkie trzy elementy są potrzebne w prawidłowym rekordzie SPF. Oto przykład wspólnego rekordu SPF dla Office 365, gdy używasz tylko Exchange Online wiadomości e-mail:

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

System poczty e-mail, który odbiera wiadomość e-mail z domeny, analizuje rekord SPF i jeśli serwer poczty e-mail, który wysłał wiadomość, był serwerem Office 365, wiadomość jest akceptowana. Jeśli serwer, który wysłał wiadomość, był starym systemem poczty lub złośliwym systemem w Internecie, na przykład sprawdzanie SPF może zakończyć się niepowodzeniem i wiadomość nie zostanie dostarczona. Takie testy pomagają zapobiegać fałszowaniu i wyłudzaniu informacji.

### <a name="choose-the-spf-record-structure-you-need"></a>Wybierz potrzebną strukturę rekordów SPF

W przypadku scenariuszy, w których nie używasz tylko Exchange Online poczty e-mail dla Office 365 (na przykład w przypadku korzystania z poczty e-mail pochodzącej również z usługi SharePoint Online), użyj poniższej tabeli, aby określić, co należy uwzględnić w wartości rekordu.

> [!NOTE]
> Jeśli masz skomplikowany scenariusz obejmujący na przykład serwery poczty e-mail brzegowej do zarządzania ruchem poczty e-mail przez zaporę, będziesz mieć bardziej szczegółowy rekord SPF do skonfigurowania. Dowiedz się, jak [skonfigurować rekordy SPF w Office 365, aby zapobiec fałszowaniu](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby dowiedzieć się więcej o tym, jak SPF współpracuje z Office 365, przeczytaj [artykuł How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing (How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing (How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing (How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing (How Office 365 uses Sender Policy Framework (SPF) to help](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md)

|Numer|Jeśli używasz...|Celu|Dodaj te elementy:|
|---|---|---|---|
|1|Wszystkie systemy poczty e-mail (wymagane)|Wszystkie rekordy SPF zaczynają się od tej wartości|v=spf1|
|2|Exchange Online (wspólne)|Użyj tylko z Exchange Online|include:spf.protection.outlook.com|
|3|System poczty e-mail innych firm (rzadziej używany)||Obejmują:\<email system like mail.contoso.com\>|
|4|Lokalny system poczty (rzadziej używany)|Użyj, jeśli używasz Exchange Online Protection lub Exchange Online plus inny system poczty|ip4:\<0.0.0.0\> <br/> ip6:\< : : \> <br/> Obejmują:\<mail.contoso.com\> <br/> Wartością w nawiasach kwadratowych (\<\>) powinny być inne systemy poczty, które będą wysyłać wiadomości e-mail dla twojej domeny.|
|5|Wszystkie systemy poczty e-mail (wymagane)||-all|

### <a name="example-adding-to-an-existing-spf-record"></a>Przykład: dodawanie do istniejącego rekordu SPF
<a name="bkmk_addtospf"> </a>

Jeśli masz już rekord SPF, musisz dodać lub zaktualizować wartości dla Office 365. Załóżmy na przykład, że istniejący rekord SPF dla contoso.com jest następujący:

``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Teraz aktualizujesz rekord SPF dla Office 365. Będziesz edytować bieżący rekord, aby mieć rekord SPF zawierający potrzebne wartości. W przypadku Office 365 "spf.protection.outlook.com".

Poprawne:

``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Niepoprawne:

``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Więcej przykładów typowych wartości SPF
<a name="bkmk_addtospf"> </a>

Jeśli używasz pełnego pakietu Office 365 i wysyłasz marketingowe wiadomości e-mail w Twoim imieniu za pomocą narzędzia MailChimp, rekord SPF w contoso.com może wyglądać następująco, który używa wierszy 1, 3 i 5 z powyższej tabeli. Pamiętaj, że wiersze 1 i 5 są wymagane.

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Alternatywnie, jeśli masz Exchange Konfiguracja hybrydowa, w której poczta e-mail będzie wysyłana zarówno z Office 365, jak i z lokalnego systemu poczty, rekord SPF w contoso.com może wyglądać następująco:

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Oto kilka typowych przykładów, które mogą pomóc w dostosowaniu istniejącego rekordu SPF po dodaniu domeny do Office 365 wiadomości e-mail. Jeśli masz skomplikowany scenariusz obejmujący na przykład serwery poczty e-mail brzegowej do zarządzania ruchem poczty e-mail przez zaporę, będziesz mieć bardziej szczegółowy rekord SPF do skonfigurowania. Dowiedz się, jak [skonfigurować rekordy SPF w Office 365, aby zapobiec fałszowaniu](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Oto krótki link, za pomocą którego możesz wrócić: <https://aka.ms/o365edns>
