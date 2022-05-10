---
title: Dowiedz się więcej o domyślnych etykietach i zasadach ochrony danych
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
description: Dowiedz się więcej o domyślnych etykietach i zasadach usługi Microsoft Purview Information Protection do klasyfikowania i ochrony poufnej zawartości.
ms.openlocfilehash: 486286780eaa3a2deedb2c3df837a93814280f39
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286455"
---
# <a name="default-labels-and-policies-to-protect-your-data"></a>Domyślne etykiety i zasady ochrony danych

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Uprawnieni klienci mogą aktywować domyślne etykiety i zasady dla usługi Microsoft Purview Information Protection: 

- Etykiety poufności i zasady etykiet poufności
- Automatyczne etykietowanie po stronie klienta
- Automatyczne etykietowanie po stronie usługi
- Zasady ochrony przed utratą danych (DLP) dla Teams i urządzeń

Te domyślne konfiguracje ułatwiają szybkie rozpoczęcie pracy z usługą Microsoft Purview Information Protection dla Microsoft 365. Można ich używać w taki sam sposób, jak jest, wprowadzić tylko kilka zmian lub w pełni dostosować je do własnych wymagań biznesowych. 

Uprawnienia obejmują klientów, którzy mają [bezpłatną wersję próbną dla usługi Microsoft Purview](compliance-easy-trials.md), oraz niektórych klientów, którzy mają już plan Microsoft 365 E5:

- **Nowi klienci**: jeśli masz usługę Microsoft Purview przez mniej niż 30 dni, dzierżawa może aktywować wszystkie wymienione konfiguracje domyślne. Zawsze można je wyłączyć, usunąć lub edytować.

- **Istniejący klienci**: jeśli masz usługę Microsoft Purview przez ponad 30 dni, możesz aktywować konfiguracje domyślne, jeśli jeszcze nie skonfigurowano odpowiednika:

    | Konfiguracja domyślna| Równoważne |
    |:-----|:-----|
    |Etykiety poufności i zasady etykiet poufności | Opublikowane etykiety poufności |
    |Automatyczne etykietowanie po stronie klienta | Co najmniej jedna etykieta poufności skonfigurowana do automatycznego stosowania (lub zalecenia dla użytkowników) w aplikacjach Office|
    |Automatyczne etykietowanie po stronie usługi | Co najmniej jedna włączona zasada automatycznego etykietowania|
    |DLP dla Teams | Co najmniej jedna zasada DLP dla Teams|
    |DLP dla urządzeń | Co najmniej jedna zasada DLP dla urządzeń|

## <a name="activate-the-default-labels-and-policies"></a>Aktywowanie domyślnych etykiet i zasad

Aby uzyskać te wstępnie skonfigurowane etykiety i zasady: 

1. W [portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **SolutionsInformation**  >  protection
    
    Jeśli ta opcja nie zostanie od razu wyświetlona, najpierw wybierz pozycję **Pokaż wszystko** w okienku nawigacji. 
    
2. Jeśli kwalifikujesz się do programu Microsoft Purview Information Protection domyślnych etykiet i zasad, zostaną wyświetlone następujące informacje, w których można aktywować domyślne etykiety i zasady. Przykład:
    
    :::image type="content" alt-text="Usługa Microsoft Purview Information Protection aktywację wstępnie skonfigurowanych etykiet i zasad." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Jeśli te informacje nie są wyświetlane z opcją aktywacji, obecnie nie kwalifikujesz się do automatycznego tworzenia etykiet poufności i zasad. Możesz spróbować sprawdzić później, czy ten stan uległ zmianie, lub użyć poniższych informacji o ustawieniach, aby ręcznie utworzyć te same etykiety i zasady.

3. Teraz włącz etykiety poufności dla SharePoint i OneDrive. Ten krok jest wymaganiem wstępnym do używania etykiet poufności w zasadach Office dla sieci web i automatycznego etykietowania dla SharePoint i OneDrive.
   
    Użyj następującego baneru w górnej części karty **Information Protection Przegląd**, a następnie wybierz pozycję **Włącz teraz**. Jeśli nie widzisz tego transparentu, etykiety poufności dla SharePoint i OneDrive zostały już włączone dla dzierżawy.
    
    ![Włącz etykiety poufności dla baneru SharePoint i OneDrive.](../media/turn-on-mip-labels.png)
    
    Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Włączanie etykiet poufności dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Domyślne etykiety poufności

Jeśli nie masz opublikowanych etykiet poufności, utworzymy dla Ciebie następujące etykiety:


|Nazwa etykiety|Opis etykiety dla użytkowników|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Personal|Dane inne niż biznesowe tylko do użytku osobistego.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Publiczny|Dane biznesowe, które są specjalnie przygotowane i zatwierdzone do użytku publicznego.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Ogólne|Dane biznesowe, które nie są przeznaczone do użytku publicznego. W razie potrzeby można to jednak udostępnić partnerom zewnętrznym. Przykłady obejmują wewnętrzny katalog telefoniczny firmy, wykresy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Ogólne <br /> \ Każdy (nieograniczony)|Dane organizacji, które nie są przeznaczone do użytku publicznego, ale w razie potrzeby mogą być udostępniane partnerom zewnętrznym. Przykłady obejmują konwersacje klientów, które nie zawierają poufnych informacji ani opublikowanych materiałów marketingowych.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Ogólne <br /> \ Wszyscy pracownicy (nieograniczone)|Dane organizacji, które nie są przeznaczone do użytku publicznego. Jeśli chcesz udostępnić tę zawartość partnerom zewnętrznym, potwierdź innym właścicielom danych, że można udostępnić tę zawartość, a następnie zmień etykietę na Ogólne \ Każda (nieograniczona) . Przykłady obejmują wewnętrzny katalog telefoniczny firmy, wykresy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Poufne|Poufne dane biznesowe, które mogą spowodować szkody w firmie, jeśli są udostępniane nieautoryzowanym osobom. Przykłady obejmują kontrakty, raporty zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.|**Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: Nie<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Poufne <br /> \ Każdy (nieograniczony)|Poufne dane, które nie muszą być szyfrowane. Użyj tej opcji z ostrożnością i odpowiednim uzasadnieniem biznesowym.|Ta etykieta jest wybrana do [automatycznego etykietowania po stronie klienta](#client-side-auto-labeling) i [automatycznego etykietowania po stronie usługi](#service-side-auto-labeling).<br /><br /> **Zakres**: plik, adres e-mail <br /><br />**Oznaczanie zawartości**: stopka: sklasyfikowana jako poufna<br /><br />**Automatyczne etykietowanie**: zaleca się stosowanie etykiety przez użytkowników <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Poufne <br /> \ Wszyscy pracownicy|Poufne dane, które wymagają ochrony, co umożliwia wszystkim pracownikom pełne uprawnienia. Właściciele danych mogą śledzić i odwoływać zawartość.|Ta etykieta jest wybrana do [automatycznego etykietowania po stronie klienta](#client-side-auto-labeling) i [automatycznego etykietowania po stronie usługi](#service-side-auto-labeling).<br /><br /> **Zakres**: plik, adres e-mail <br /><br />**Szyfrowanie**: Wszyscy użytkownicy i grupy w organizacji: Co-Author<br /><br />**Oznaczanie zawartości**: stopka: sklasyfikowana jako poufna<br /><br />**Automatyczne etykietowanie**: zaleca się stosowanie etykiety przez użytkowników <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak |
|Poufne <br /> \ Zaufane osoby|Poufne dane, które mogą być udostępniane zaufanym osobom w organizacji i poza nią. Te osoby mogą również ponownie udostępniać dane w razie potrzeby.|**Zakres**: plik, adres e-mail <br /><br />**Szyfrowanie**: zezwalaj użytkownikom na przypisywanie uprawnień: <br /> - Encrypt-Only dla Outlook <br />— monituj użytkowników w programach Word, PowerPoint i Excel<br /><br />**Oznaczanie zawartości**: stopka: sklasyfikowana jako poufna<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Wysoce poufne|Bardzo poufne dane biznesowe, które mogłyby spowodować uszkodzenie firmy, gdyby zostały udostępnione nieautoryzowanym osobom. Przykłady obejmują informacje o pracownikach i klientach, hasła, kod źródłowy i wstępnie ogłoszone raporty finansowe.|**Zakres**: plik, adres e-mail <br /><br />**Znakowanie zawartości**: Znak wodny: WYSOCE POUFNE<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Wysoce poufne <br /> \ Wszyscy pracownicy|Wysoce poufne dane, które umożliwiają wszystkim pracownikom wyświetlanie, edytowanie i odpowiadanie na uprawnienia do tej zawartości. Właściciele danych mogą śledzić i odwoływać zawartość.|**Zakres**: plik, adres e-mail <br /><br />**Szyfrowanie**: Wszyscy użytkownicy i grupy w organizacji: Co-Author<br /><br />**Oznaczanie zawartości**: stopka: sklasyfikowana jako wysoce poufna<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|
|Wysoce poufne <br /> \ Określone osoby |Wysoce poufne dane, które wymagają ochrony i mogą być wyświetlane tylko przez określone osoby i z wybranym poziomem uprawnień.|**Zakres**: plik, adres e-mail <br /><br />**Szyfrowanie**: zezwalaj użytkownikom na przypisywanie uprawnień: <br />— Nie przekazuj dalej dla Outlook <br />— monituj użytkowników w programach Word, PowerPoint i Excel<br /><br />**Oznaczanie zawartości**: stopka: sklasyfikowana jako wysoce poufna<br /><br />**Automatyczne etykietowanie**: Nie <br /><br />**Ustawienia grupy**: Nie<br /><br />**Ustawienia witryny**: Nie <br /><br />**Automatyczne etykietowanie kolumn bazy danych**: Brak|

> [!NOTE]
> Nazwy etykiet i opisy są automatycznie dostępne dla następujących ustawień regionalnych: angielski usa, chiński uproszczony i tradycyjny, francuski, niemiecki, włoski, japoński, koreański, portugalski brazylijski, rosyjski i hiszpański.
> 
> Jeśli potrzebujesz dodatkowych języków, możesz określić tłumaczenia [przy użyciu programu PowerShell](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages).

Aby uzyskać więcej informacji na temat tych ustawień konfiguracji i możliwości etykiet poufności, zobacz [Co mogą zrobić etykiety poufności](sensitivity-labels.md#what-sensitivity-labels-can-do).

Jeśli chcesz edytować te domyślne etykiety poufności, zobacz [Tworzenie i konfigurowanie etykiet poufności](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Domyślne zasady etykiet poufności

Domyślne zasady etykiet poufności umożliwiają użytkownikom rozpoczęcie etykietowania dokumentów i wiadomości e-mail etykietami poufności. Ma następującą konfigurację:

- Publikowanie etykiet domyślnych dla wszystkich użytkowników w dzierżawie
- Etykieta domyślna **generalall** \  **employees (unrestricted)** dla nieoznaczonych dokumentów i wiadomości e-mail
- Użytkownicy muszą uzasadnić usunięcie etykiety lub obniżenie jej klasyfikacji

Aby uzyskać więcej informacji na temat tych ustawień zasad i innych dostępnych ustawień zasad, zobacz [Co mogą zrobić zasady etykiet](sensitivity-labels.md#what-label-policies-can-do).

Jeśli chcesz edytować te domyślne ustawienia zasad, zobacz [Publikowanie etykiet poufności, tworząc zasady etykiet](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Jeśli używasz tych etykiet w aplikacjach Office w Windows, macOS, iOS i Android, użytkownicy widzą nowe etykiety w ciągu czterech godzin, a w ciągu jednej godziny dla programu Word, Excel i PowerPoint w sieci Web podczas odświeżania przeglądarki. Może jednak być konieczne zezwolenie na replikację zmian do wszystkich aplikacji i usług przez maksymalnie 24 godziny.

## <a name="client-side-auto-labeling"></a>Automatyczne etykietowanie po stronie klienta

Domyślna konfiguracja automatycznego etykietowania po stronie klienta automatycznie zaleca użytkownikom stosowanie etykiety poufności w przypadku wykrycia numerów kart kredytowych w dokumentach lub wiadomościach e-mail, z którymi pracują. Jako zalecenie, a nie automatycznie stosowane, ta konfiguracja służy jako dobry pierwszy krok do wyróżniania zawartości i wprowadza użytkowników do praktyki etykietowania dokumentów i wiadomości e-mail.

Automatyczne etykietowanie po stronie klienta działa tylko w przypadku dokumentów i wiadomości e-mail używanych przez aplikacje Office Word, Excel, PowerPoint i Outlook. 

Domyślne automatyczne etykietowanie po stronie klienta ma następującą konfigurację: 

- Jeśli w dokumencie lub wiadomości e-mail znajduje się od 1 do 9 wystąpień numerów kart kredytowych, zaleca się, aby użytkownik zastosował etykietę poufności **ConfidentialAnyone** \  **(nieograniczone)** 

- Jeśli w dokumencie lub wiadomości e-mail znajduje się co najmniej 10 wystąpień numerów kart kredytowych, zaleca się, aby użytkownik zastosował etykietę poufności **PoufneWszystki** \  **pracownicy** 

> [!NOTE]
> Jeśli wykryliśmy, że masz opublikowane własne etykiety poufności, zostanie wyświetlony monit o wybranie jednej z własnych etykiet do automatycznego etykietowania i skonfigurowanie ich dla Ciebie.

Jeśli chcesz edytować konfigurację automatycznego etykietowania po stronie klienta, zobacz [How to configure auto-labeling for Office apps (Jak skonfigurować automatyczne etykietowanie dla aplikacji Office](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)).

## <a name="service-side-auto-labeling"></a>Automatyczne etykietowanie po stronie usługi 

Automatyczne etykietowanie po stronie usługi ułatwia etykietowanie poufnych dokumentów magazynowanych i wiadomości e-mail przesyłanych. Domyślne zasady automatycznego etykietowania po stronie usługi tworzą zasady w trybie symulacji dla dokumentów przechowywanych we wszystkich witrynach SharePoint lub OneDrive oraz wszystkich wiadomości e-mail wysyłanych za pośrednictwem Exchange Online. W trybie symulacji elementy nie są oznaczane etykietami, dopóki zasady nie zostaną włączone. Tryb symulacji umożliwia wyświetlenie podglądu elementów, które zostaną oznaczone etykietą po włączeniu zasad, dzięki czemu masz pewność co do funkcji etykietowania przed wdrożeniem zasad w dzierżawie na potrzeby rzeczywistego etykietowania. 

Domyślne automatyczne etykietowanie po stronie usługi ma następującą konfigurację: 

- Jeśli w dokumencie znajduje się od 1 do 9 wystąpień numerów kart kredytowych, zastosuj etykietę poufności **ConfidentialAnyone** \  **(bez ograniczeń)**

- Jeśli w dokumencie lub wiadomości e-mail znajduje się co najmniej 10 wystąpień numerów kart kredytowych, zaleca się, aby użytkownik zastosował etykietę poufności **PoufneWszystki** \  **pracownicy** 

> [!NOTE]
> Jeśli wykryliśmy, że masz opublikowane własne etykiety poufności, zostanie wyświetlony monit o wybranie jednej z własnych etykiet dla zasad automatycznego etykietowania.

Po zakończeniu symulacji przejrzyj wyniki i jeśli są one zadowalające, włącz zasady.

Aby uzyskać więcej informacji na temat trybu symulacji, zobacz [Dowiedz się więcej o trybie symulacji](apply-sensitivity-label-automatically.md#learn-about-simulation-mode).

Jeśli chcesz edytować zasady automatycznego etykietowania po stronie usługi, zobacz [Jak skonfigurować zasady automatycznego etykietowania dla SharePoint, OneDrive i Exchange](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>DLP dla Teams

Domyślne zasady DLP dla Teams wykrywają obecność numerów kart kredytowych we wszystkich Teams czatach i komunikatach kanałów. Po wykryciu tych poufnych informacji administratorzy otrzymają powiadomienie o alertach o niskiej ważności.

Te zasady są dyskretne dla użytkowników bez widocznej wskazówki dotyczącej zasad i nie są blokowane żadne komunikaty, ale administratorzy będą mieć rekordy poufnych informacji udostępnionych w tych komunikatach. W razie potrzeby możesz edytować ustawienia, aby zmienić tę konfigurację domyślną.

Aby wyświetlić wyniki tych zasad, użyj [Eksploratora działań DLP](dlp-learn-about-dlp.md#dlp-activity-explorer).

Jeśli chcesz edytować zasady DLP, zobacz [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>DLP dla urządzeń

Domyślne zasady DLP dla urządzeń wykrywają obecność numerów kart kredytowych na urządzeniach Windows 10, które zostały dołączone do usługi Microsoft Purview. Następnie przeprowadza inspekcję (nie blokuje) następujących akcji: 

- Upload do domen usług w chmurze lub dostęp przez niedozwolone przeglądarki

- Kopiowanie do schowka, portu USB lub udziału sieciowego 

- Dostęp przez niedozwolone aplikacje 

- Drukowania 

- Kopiowanie lub przenoszenie przy użyciu niedozwolonej aplikacji Bluetooth 

- Usługi pulpitu zdalnego 

Jeśli zawartość zawiera co najmniej 10 wystąpień kart kredytowych, a co najmniej jedno z wymienionych działań zostanie wykryte, do administratorów zostanie wysłane powiadomienie o alertie o średniej ważności.

Te zasady są dyskretne dla użytkowników bez widocznej wskazówki dotyczącej zasad i nie są blokowane żadne akcje, ale administratorzy będą mieć rekordy wszystkich podejrzanych działań. W razie potrzeby możesz edytować te ustawienia, aby zmienić tę konfigurację domyślną.

Aby wyświetlić wyniki tych zasad, użyj [Eksploratora działań DLP](dlp-learn-about-dlp.md#dlp-activity-explorer).

Jeśli chcesz edytować zasady DLP, zobacz [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Dodatkowe materiały

Aby dowiedzieć się więcej o etykietach poufności, zapobieganiu utracie danych i wszystkich możliwościach dostępnych w usłudze Microsoft Purview Information Protection, zobacz następujące zasoby:

- [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Ochrona danych za pomocą usługi Microsoft Purview](information-protection.md)
