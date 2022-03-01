---
title: Informacje o domyślnych etykietach i zasadach dotyczących etykiet Microsoft Information Protection
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
description: Zapoznaj się z domyślnymi etykietami i zasadami ochrony Microsoft Information Protection klasyfikowania i ochrony poufnej zawartości.
ms.openlocfilehash: a0634a8f67e28d84334cfadd4be7d9694084af6c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032099"
---
# <a name="default-labels-and-policies-for-microsoft-information-protection"></a>Domyślne etykiety i zasady dla Microsoft Information Protection

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Uprawnieni klienci mogą aktywować etykiety i zasady domyślne dla klientów Microsoft Information Protection (MIP): 

- Etykiety wrażliwości i zasady wrażliwości
- Automatyczne etykiety po stronie klienta
- Automatyczne etykiety po stronie serwisowej
- Zasady ochrony przed utratą danych (DLP) dotyczące Teams i urządzeń

Te konfiguracje domyślne ułatwiają szybkie uruchamianie się dzięki Microsoft Information Protection z Microsoft 365 zgodnością. Możesz ich używać bez zmian, wprowadzać tylko kilka zmian lub w pełni je dostosowywać, aby lepiej odpowiadały potrzebom biznesowym. 

Uprawnienia obejmują klientów, którzy mają bezpłatny okres próbny do Microsoft 365 [zgodności](compliance-easy-trials.md) z przepisami, i niektórzy klienci, którzy już mają Microsoft 365 E5 planu:

- **Nowi klienci**: Jeśli przez mniej niż 30 dni Microsoft 365, dzierżawa może aktywować wszystkie wymienione na liście konfiguracje domyślne. Zawsze możesz je wyłączyć, usunąć lub edytować.

- **Istniejący klienci**: Jeśli masz Microsoft 365 zgodności przez ponad 30 dni, możesz aktywować konfiguracje domyślne, jeśli nie skonfigurowano jeszcze odpowiednika:

    | Konfiguracja domyślna| Odpowiednik |
    |:-----|:-----|
    |Etykiety wrażliwości i zasady wrażliwości | Opublikowane etykiety wrażliwości |
    |Automatyczne etykiety po stronie klienta | Co najmniej jedna etykieta wrażliwości skonfigurowana do automatycznego stosowania (lub polecania użytkownikom) w Office aplikacjach|
    |Automatyczne etykiety po stronie serwisowej | Co najmniej jedna z włączonych zasad automatycznego oznaczania etykiet|
    |DLP dla Teams | Co najmniej jedna zasada ochrony przed dlp dla Teams|
    |DLP dla urządzeń | Co najmniej jedna zasada ochrony przed dlp dla urządzeń|

## <a name="activate-the-default-labels-and-policies"></a>Aktywowanie domyślnych etykiet i zasad

Aby uzyskać te wstępnie skonfigurowane etykiety i zasady: 

1. Z poziomu [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) wybierz **pozycję** **SolutionsInformation** >  Protection
    
    Jeśli nie widzisz tej opcji od razu, najpierw wybierz pozycję **Pokaż wszystko** w okienku nawigacji. 
    
2. Jeśli masz uprawnienia do Microsoft Information Protection etykiet i zasad domyślnych, zostaną wyświetlony następujące informacje, w których możesz aktywować etykiety i zasady domyślne. Przykład:
    
    :::image type="content" alt-text="Microsoft Information Protection, aby uzyskać wstępnie skonfigurowane etykiety i zasady." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Jeśli nie widzisz tych informacji z opcją aktywacji, oznacza to, że obecnie nie kwalifikujesz się do automatycznego tworzenia etykiet i zasad wrażliwości. Możesz spróbować ponownie później sprawdzić, czy ten stan uległ zmianie, lub użyć informacji o ustawieniach, które są poniżej, aby ręcznie utworzyć te same etykiety i zasady.

3. Teraz włącz etykiety wrażliwości dla SharePoint i OneDrive. Ten krok stanowi wymaganie wstępne dotyczące korzystania z etykiet wrażliwości Office dla sieci web a zasad automatycznego oznaczania etykiet SharePoint i OneDrive.
   
    Użyj następującego transparentu u góry karty **Omówienie ochrony informacji** i wybierz **pozycję Włącz teraz**. Jeśli nie widzisz tego transparentu, etykiety wrażliwości dla SharePoint i OneDrive zostały już włączone dla Twojej dzierżawy.
    
    ![Włącz etykiety wrażliwości dla SharePoint i OneDrive transparentu.](../media/turn-on-mip-labels.png)
    
    Aby uzyskać więcej informacji na temat tej funkcji, zobacz Włączanie etykiet wrażliwości [dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Domyślne etykiety wrażliwości

Jeśli nie masz opublikowanych etykiet wrażliwości, utworzymy dla Ciebie następujące etykiety:


|Nazwa etykiety|Opis etykiet dla użytkowników|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Personal|Dane inne niż służbowe, tylko do użytku osobistego.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Publiczne|Dane biznesowe specjalnie przygotowane i zatwierdzone do użycia publicznego.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Ogólne|Dane biznesowe przeznaczone do użycia publicznego. W razie potrzeby można jednak udostępnić te dane partnerom zewnętrznym. Przykłady obejmują wewnętrzny katalog telefoniczny firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Ogólne <br /> \ Każdy (nieograniczone)|Dane organizacji, które nie są przeznaczone do użytku publicznego, ale w razie potrzeby mogą być udostępniane partnerom zewnętrznym. Przykłady obejmują konwersacje z klientami, które nie zawierają informacji poufnych ani nie opublikowano materiałów marketingowych.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Ogólne <br /> \ Wszyscy pracownicy (nieograniczone)|Dane organizacji przeznaczone do użycia publicznego. Jeśli chcesz udostępnić tę zawartość partnerom zewnętrznym, potwierdź innym właścicielom danych, że udostępnianie jest możliwe, a następnie zmień etykietę na Ogólne \ Każdy (nieograniczone). Przykłady obejmują wewnętrzny katalog telefoniczny firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Poufne|Poufne dane biznesowe, które mogą powodować szkody w firmie w przypadku ich współużytkenia z nieautoryzowanymi osobami. Mogą to być na przykład umowy, raporty zabezpieczeń, podsumowania prognoz i dane dotyczące kont sprzedaży.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Poufne <br /> \ Każdy (nieograniczone)|Poufne dane, których nie trzeba zaszyfrować. Tej opcji należy używać z należytą ostrożność i odpowiednim uzasadnieniem biznesowym.|Ta etykieta jest [zaznaczona do automatycznego oznaczania](#client-side-auto-labeling) po stronie klienta i do [automatycznego oznaczania po stronie serwisowej](#service-side-auto-labeling).<br /><br /> **Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Stopka: Klasyfikowane jako poufne<br /><br />**Automatyczne oznaczanie etykiet**: zaleca się użytkownikom stosowanie etykiety <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Poufne <br /> \ Wszyscy pracownicy|Poufne dane, które wymagają ochrony, co pozwala wszystkim pracownikom na pełne uprawnienia. Właściciele danych mogą śledzić i cofać zawartość.|Ta etykieta jest [zaznaczona do automatycznego oznaczania](#client-side-auto-labeling) po stronie klienta i do [automatycznego oznaczania po stronie serwisowej](#service-side-auto-labeling).<br /><br /> **Zakres**: Plik, Poczta e-mail <br /><br />**Szyfrowanie**: wszyscy użytkownicy i grupy w organizacji: Co-Author<br /><br />**Oznaczanie zawartości**: Stopka: Klasyfikowane jako poufne<br /><br />**Automatyczne oznaczanie etykiet**: zaleca się użytkownikom stosowanie etykiety <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak |
|Poufne <br /> \ Zaufane osoby|Poufne dane, które mogą być udostępniane zaufanym osobom w organizacji i poza nią. Te osoby mogą również w razie potrzeby ponownie udostępnić dane.|**Zakres**: Plik, Poczta e-mail <br /><br />**Szyfrowanie**: umożliwianie użytkownikom przypisywania uprawnień: <br /> — Encrypt-Only dla Outlook <br />— Monituj użytkowników w programie Word, PowerPoint i Excel<br /><br />**Oznaczanie zawartości**: Stopka: Klasyfikowane jako poufne<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Wysoce poufne|Bardzo poufne dane biznesowe, które mogą uszkodzić firmę w przypadku ich współużytkenia z nieautoryzowanymi osobami. Mogą to być na przykład informacje o pracownikach i klientach, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|**Zakres**: Plik, Poczta e-mail <br /><br />**Oznaczanie zawartości**: Znak wodny: WYSOCE POUFNE<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Wysoce poufne <br /> \ Wszyscy pracownicy|Wysoce poufne dane, które umożliwiają wszystkim pracownikom wyświetlanie, edytowanie i odpowiadanie na tę zawartość. Właściciele danych mogą śledzić i cofać zawartość.|**Zakres**: Plik, Poczta e-mail <br /><br />**Szyfrowanie**: wszyscy użytkownicy i grupy w organizacji: Co-Author<br /><br />**Oznaczanie zawartości**: Stopka: Sklasyfikowane jako wysoce poufne<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|
|Wysoce poufne <br /> \ Określone osoby |Wysoce poufne dane, które wymagają ochrony i mogą być przeglądane tylko przez określone przez Ciebie osoby z dowolnym poziomem uprawnień.|**Zakres**: Plik, Poczta e-mail <br /><br />**Szyfrowanie**: umożliwianie użytkownikom przypisywania uprawnień: <br />- Nie przesyłaj dalej dla Outlook <br />— Monituj użytkowników w programie Word, PowerPoint i Excel<br /><br />**Oznaczanie zawartości**: Stopka: Sklasyfikowane jako wysoce poufne<br /><br />**Automatyczne oznaczanie etykiet**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne oznaczanie kolumn bazy danych**: Brak|

> [!NOTE]
> Nazwy etykiet i opisy są automatycznie dostępne dla następujących lokalizacji: angielski (USA), chiński uproszczony i tradycyjny, francuski, niemiecki, włoski, japoński, koreański, portugalski (Brazylia), rosyjski i hiszpański.
> 
> Jeśli potrzebujesz dodatkowych języków, możesz określić swoje tłumaczenia za [pomocą programu PowerShell](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages).

Aby uzyskać więcej informacji o tych ustawieniach konfiguracji i o tym, jakie są opcje etykiet wrażliwości, zobacz [Jakie są opcje etykiet wrażliwości](sensitivity-labels.md#what-sensitivity-labels-can-do).

Jeśli musisz edytować te domyślne etykiety wrażliwości, zobacz [Tworzenie i konfigurowanie etykiet wrażliwości](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Domyślne zasady etykiet wrażliwości

Domyślne zasady etykiet wrażliwości udostępniają użytkownikom etykiety w celu rozpoczęcia oznaczania ich dokumentów i wiadomości e-mail etykietami wrażliwości. Ma on następującą konfigurację:

- Publikowanie etykiet domyślnych dla wszystkich użytkowników w dzierżawie
- Domyślna **etykieta OgólneWszystkie** \  **pracownicy (nieograniczone) dla** nieokreślonych dokumentów i wiadomości e-mail
- Użytkownicy muszą podać uzasadnienie, aby usunąć etykietę lub obniżyć jej klasyfikację

Aby uzyskać więcej informacji na temat tych ustawień zasad i innych dostępnych ustawień zasad, zobacz Jakie [zasady etykiet można wykonać](sensitivity-labels.md#what-label-policies-can-do).

Jeśli musisz edytować te domyślne ustawienia zasad, zobacz [Publikowanie etykiet wrażliwości przez utworzenie zasad etykiet](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Gdy używasz tych etykiet w aplikacjach Office w systemach Windows, macOS, iOS i Android, użytkownicy widzą nowe etykiety w ciągu czterech godzin i w ciągu jednej godziny dla programów Word, Excel i PowerPoint w sieci Web po odświeżeniu przeglądarki. Jednak może być konieczne do 24 godzin, aby zmiany replikowały się we wszystkich aplikacjach i usługach.

## <a name="client-side-auto-labeling"></a>Automatyczne etykiety po stronie klienta

Domyślna konfiguracja automatycznego oznaczania po stronie klienta automatycznie zaleca użytkownikom stosowanie etykiet wrażliwości po wykryciu numerów kart kredytowych w dokumentach lub wiadomościach e-mail, z których pracują. Ta konfiguracja służy jako dobry pierwszy krok do wyróżnienia informacji dotyczących zawartości, a nie do automatycznego zastosowania tej konfiguracji i wprowadza użytkowników do praktyki oznaczania etykietami dokumentów i wiadomości e-mail.

Automatyczne etykiety po stronie klienta są dostępne tylko w przypadku dokumentów i wiadomości e-mail, z których korzystają aplikacje Office Word, Excel, PowerPoint i Outlook. 

Domyślne automatyczne oznaczanie po stronie klienta ma następującą konfigurację: 

- Jeśli dokument lub wiadomość e-mail zawiera 1–9 wystąpień numerów kart kredytowych, zaleca się, aby użytkownik stosowanie etykiety poufności **ConfidentialAnyone** \  **(nieograniczone)** 

- Jeśli istnieje co najmniej 10 wystąpień numerów kart kredytowych znalezionych w dokumencie lub wiadomości e-mail, poleć użytkownikowi stosowanie etykiety poufności **ConfidentialAll** \  **Employees** 

> [!NOTE]
> Jeśli wykryliśmy, że masz opublikowane własne etykiety wrażliwości, zostanie wyświetlony monit o wybranie jednej z Twoich etykiet do automatycznego oznaczania etykiet i skonfigurowanie ich dla Ciebie.

Jeśli chcesz edytować konfigurację automatycznego oznaczania po stronie klienta, zobacz Jak skonfigurować automatyczne etykiety [dla Office aplikacji](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps).

## <a name="service-side-auto-labeling"></a>Automatyczne etykiety po stronie serwisowej 

Automatyczne etykiety po stronie usługi pomagają oznaczać poufne dokumenty w miejscu spoczynku i wiadomości e-mail podczas ich przesyłania. Domyślne zasady automatycznego oznaczania po stronie usługi tworzą zasady w trybie symulacyjnej dla dokumentów przechowywanych we wszystkich witrynach programu SharePoint lub OneDrive oraz wszystkich wiadomości e-mail wysyłanych za pośrednictwem Exchange Online. W trybie symulacyjnej elementy są tak naprawdę oznaczane dopiero po włączeniu zasad. Tryb symulowania pozwala wyświetlić podgląd elementów, które będą miały etykiety po włączeniu zasad, dzięki czemu masz pewność co do funkcji etykiet przed wdrożeniem zasad w dzierżawie w celu wykorzystania rzeczywistych etykiet. 

Domyślne automatyczne oznaczanie po stronie usługi ma następującą konfigurację: 

- Jeśli dokument zawiera 1–9 wystąpień numerów kart kredytowych, zastosuj etykietę poufności **ConfidentialAnyone** \  **(nieograniczone)**

- Jeśli istnieje co najmniej 10 wystąpień numerów kart kredytowych znalezionych w dokumencie lub wiadomości e-mail, poleć użytkownikowi stosowanie etykiety poufności **ConfidentialAll** \  **Employees** 

> [!NOTE]
> Jeśli wykryliśmy, że masz opublikowane własne etykiety wrażliwości, zostanie wyświetlony monit o wybranie jednej z Twoich etykiet do zasad automatycznego oznaczania etykiet.

Po zakończeniu symulowania przejrzyj wyniki i, jeśli są one zadowolone, włącz zasady.

Aby uzyskać więcej informacji na temat trybu symulacyjnego, zobacz [Informacje o trybie symulacyjnej](apply-sensitivity-label-automatically.md#learn-about-simulation-mode).

Jeśli chcesz edytować zasady automatycznego oznaczania po stronie usługi, zobacz Jak skonfigurować zasady automatycznego oznaczania etykiet dla SharePoint[, OneDrive i Exchange](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>DLP dla Teams

Domyślne zasady DLP dla Teams wykrywają obecność numerów kart kredytowych we wszystkich Teams czatach i wiadomościach kanałów. Po wykryciu tych poufnych informacji administratorzy otrzymają powiadomienie o alertach o niskim poziomie ważności.

Te zasady są dyskretne dla użytkowników, którzy nie są widoczni ani nie mają zablokowanych wiadomości, ale administratorzy będą dzielić się informacjami poufnymi w tych wiadomościach. W razie potrzeby możesz edytować ustawienia, aby zmienić tę konfigurację domyślną.

Aby wyświetlić wyniki tych zasad, użyj Eksploratora aktywności [funkcji DLP](dlp-learn-about-dlp.md#dlp-activity-explorer).

Jeśli chcesz edytować zasady DLP, zobacz [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>DLP dla urządzeń

Domyślne zasady DLP dla urządzeń wykrywają obecność numerów kart kredytowych na Windows 10, które zostały włączone w celu zapewnienia zgodności Microsoft 365 zabezpieczeń. Następnie przeprowadza inspekcje (nie blokuje) następujących działań: 

- Upload do domen usług w chmurze lub do uzyskiwania do nich dostępu za pomocą odblokowanych przeglądarek

- Kopiowanie do schowka, usb lub do udziału sieciowego 

- Uzyskiwanie dostępu przez aplikacje niedozwolone 

- Drukowanie 

- Kopiowanie lub przenoszenie przy użyciu niedozwolonej Bluetooth aplikacji 

- Usługi pulpitu zdalnego 

Jeśli zawartość zawiera co najmniej 10 wystąpień kart kredytowych i co najmniej jedno z wymienionych działań zostanie wykryte, do administratorów zostanie wysłane powiadomienie o alertach o średniej ważności.

Te zasady są dyskretne dla użytkowników, którzy nie są widoczni ani nie mają zablokowanych akcji, ale administratorzy będą chować wszystkie podejrzane działania. W razie potrzeby możesz edytować te ustawienia, aby zmienić tę konfigurację domyślną.

Aby wyświetlić wyniki tych zasad, użyj Eksploratora aktywności [funkcji DLP](dlp-learn-about-dlp.md#dlp-activity-explorer).

Jeśli chcesz edytować zasady DLP, zobacz [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Dodatkowe materiały

Aby dowiedzieć się więcej o etykietach wrażliwości, ochronie przed utratą danych i wszystkich możliwościach dostępnych w Microsoft Information Protection, zobacz następujące zasoby:

- [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Microsoft Information Protection w programie Microsoft 365](information-protection.md)
