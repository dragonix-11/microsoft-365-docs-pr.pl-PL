---
title: Monitorowanie pod kątem wycieków danych osobowych
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MET150
description: Dowiedz się więcej o trzech narzędziach, których można użyć do monitorowania wycieków danych osobowych.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b16e96e85d6ee154912535ecf0bac4ac5ba6fac
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947764"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Monitorowanie pod kątem wycieków danych osobowych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Istnieje wiele narzędzi, których można użyć do monitorowania wykorzystania i transportu danych osobowych. W tym temacie opisano trzy narzędzia, które działają dobrze.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image1.png" alt-text="Narzędzia do monitorowania wykorzystania i transportu danych osobowych" lightbox="../../media/Monitor-for-leaks-of-personal-data-image1.png":::

Na ilustracji:

- Zacznij od raportów ochrony przed utratą danych w usłudze Microsoft Purview na potrzeby monitorowania danych osobowych w usłudze SharePoint Online, OneDrive dla Firm i wiadomości e-mail przesyłane. Raporty te zapewniają najwyższy poziom szczegółowości monitorowania danych osobowych. Jednak te raporty nie obejmują wszystkich usług w Office 365.

- Następnie użyj zasad alertów i dziennika inspekcji, aby monitorować aktywność między usługami. Skonfiguruj bieżące monitorowanie lub przeszukaj dziennik inspekcji w celu zbadania zdarzenia. Dziennik inspekcji działa w usługach — Sway, Power BI, eDiscovery, Dynamics 365, Power Automate, Microsoft Teams, Aktywność administratora, OneDrive dla Firm, SharePoint Online, poczta przesyłana i skrzynki pocztowe magazynowane. Skype konwersacje są uwzględniane w skrzynkach pocztowych magazynowanych.

- Na koniec użyj Microsoft Defender for Cloud Apps do monitorowania plików z poufnymi danymi u innych dostawców SaaS. Wkrótce będzie można korzystać z poufnych typów informacji i ujednoliconych etykiet w usłudze Azure Information Protection i Office za pomocą usługi Defender dla Chmury Apps. Możesz skonfigurować zasady, które mają zastosowanie do wszystkich aplikacji SaaS lub określonych aplikacji (takich jak Box). Defender dla Chmury Apps nie odnajduje plików w Exchange Online, w tym plików dołączonych do poczty e-mail.

## <a name="data-loss-prevention-reports"></a>Raporty dotyczące zapobiegania utracie danych

Po utworzeniu zasad ochrony przed utratą danych (DLP) należy sprawdzić, czy działają one zgodnie z oczekiwaniami i pomagają zachować zgodność. Dzięki raportom DLP w Office 365 można szybko wyświetlić liczbę dopasowań, przesłoń lub wyników fałszywie dodatnich zasad DLP; sprawdzić, czy są one trendy w górę lub w dół w czasie; filtrować raport na różne sposoby i wyświetlać więcej szczegółów, wybierając punkt w wierszu na grafie.

Raporty DLP umożliwiają:

- Skoncentruj się na określonych okresach i poznaj przyczyny wzrostów i trendów.
- Odnajdywanie procesów biznesowych naruszających zasady DLP organizacji.
- Informacje o wpływie zasad DLP na działalność biznesową.
- Wyświetl uzasadnienia przesłane przez użytkowników, gdy rozwiążą poradę dotyczącą zasad, przesłaniając zasady lub zgłaszając wynik fałszywie dodatni.
- Sprawdź zgodność z określonymi zasadami DLP, wyświetlając wszystkie dopasowania dla tych zasad.
- Wyświetl listę plików z poufnymi danymi zgodnymi z zasadami DLP w okienku szczegółów.

Ponadto możesz użyć raportów DLP, aby dostosować zasady DLP podczas uruchamiania ich w trybie testowym.

Raporty DLP znajdują się w portalu zgodności usługi Microsoft Purview. Przejdź do sekcji **Raporty** \> **dotyczące danych organizacji** , aby znaleźć **dopasowania zasad DLP**, **zdarzenia DLP** i **raporty fałszywie dodatnie DLP i przesłaniają raporty** .

Aby uzyskać więcej informacji, zobacz [Wyświetlanie raportów dotyczących zapobiegania utracie danych](../../compliance/view-the-dlp-reports.md).

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image2.png" alt-text="Raport przedstawiający dopasowania zasad DLP" lightbox="../../media/Monitor-for-leaks-of-personal-data-image2.png":::

## <a name="audit-log-and-alert-policies"></a>Dziennik inspekcji i zasady alertów

Dziennik inspekcji zawiera zdarzenia z Exchange Online, SharePoint Online, OneDrive dla Firm, Azure Active Directory, Microsoft Teams, Power BI, Sway i innych Usług.

Portal Microsoft 365 Defender i portal zgodności usługi Microsoft Purview udostępniają dwa sposoby monitorowania i raportowania w dzienniku inspekcji:

- Konfigurowanie zasad alertów, wyświetlanie alertów i monitorowanie trendów — użyj zasad alertów i narzędzi pulpitu nawigacyjnego alertów w portalu Microsoft 365 Defender lub portalu zgodności usługi Microsoft Purview.
- Przeszukaj dziennik inspekcji bezpośrednio: wyszukaj wszystkie zdarzenia w określonej dacie. Możesz też filtrować wyniki na podstawie określonych kryteriów, takich jak użytkownik, który wykonał akcję, akcja lub obiekt docelowy.

Zespoły ds. zgodności z informacjami i zabezpieczeń mogą używać tych narzędzi do proaktywnego przeglądania działań wykonywanych zarówno przez użytkowników końcowych, jak i administratorów w różnych usługach. Alerty automatyczne można skonfigurować do wysyłania powiadomień e-mail w przypadku niektórych działań wykonywanych w określonych zbiorach witryn — na przykład gdy zawartość jest udostępniana z witryn, o których wiadomo, że zawierają informacje związane z RODO. Dzięki temu zespoły mogą śledzić użytkowników, aby zapewnić przestrzeganie firmowych zasad zabezpieczeń lub zapewnić dodatkowe szkolenia.

Zespoły ds. zabezpieczeń informacji mogą również przeszukiwać dziennik inspekcji w celu zbadania podejrzanych naruszeń danych i określenia zarówno głównej przyczyny, jak i zakresu naruszenia. Ta wbudowana funkcja ułatwia zgodność z art. Wpisy dziennika inspekcji są przechowywane tylko przez 90 dni w usłudze — jest to często zalecane, a wiele organizacji wymaga przechowywania tych dzienników przez dłuższy czas.

Dostępne są rozwiązania, które subskrybują ujednolicone dzienniki inspekcji za pośrednictwem interfejsu API działania zarządzania firmy Microsoft i mogą przechowywać wpisy dziennika w razie potrzeby oraz udostępniać zaawansowane pulpity nawigacyjne i alerty. Jednym z przykładów jest [pakiet Microsoft Operations Management Suite (OMS).](/azure/operations-management-suite/oms-solution-office-365)

Więcej informacji o zasadach alertów i przeszukiwaniu dziennika inspekcji:

- [Zasady alertów w Microsoft 365](../../compliance/alert-policies.md)
- [Wyszukaj w dzienniku inspekcji aktywność użytkownika i administratora w Office 365](../../compliance/search-the-audit-log-in-security-and-compliance.md) (wprowadzenie)
- [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md)
- [Przeszukaj dziennik inspekcji](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (polecenie cmdlet)
- [Szczegółowe właściwości w dzienniku inspekcji](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps ułatwia odnajdywanie innych aplikacji SaaS używanych w sieciach oraz poufnych danych wysyłanych do i z tych aplikacji.

Microsoft Defender for Cloud Apps to kompleksowa usługa zapewniająca głęboką widoczność, szczegółowe mechanizmy kontroli i rozszerzoną ochronę przed zagrożeniami dla aplikacji w chmurze. Identyfikuje ponad 15 000 aplikacji w chmurze w sieci ze wszystkich urządzeń i zapewnia ocenę ryzyka oraz bieżącą ocenę ryzyka i analizę. Brak wymaganych agentów: informacje są zbierane z zapór i serwerów proxy w celu uzyskania pełnego wglądu i kontekstu dla użycia chmury i w tle it.

Aby lepiej zrozumieć środowisko chmury, funkcja badania aplikacji Defender dla Chmury zapewnia szczegółowy wgląd we wszystkie działania, pliki i konta dla zaakceptowanych i zarządzanych aplikacji. Możesz uzyskać szczegółowe informacje na temat poziomu plików i dowiedzieć się, gdzie dane przemieszczają się w aplikacjach w chmurze.

Na przykład poniższa ilustracja przedstawia dwie zasady Defender dla Chmury Aplikacje, które mogą pomóc w rodorze.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image3.png" alt-text="Zasady aplikacji Defender dla Chmury" lightbox="../../media/Monitor-for-leaks-of-personal-data-image3.png":::

Pierwsze alerty zasad, gdy pliki ze wstępnie zdefiniowanym atrybutem pii lub wyrażeniem niestandardowym, które wybierzesz, są udostępniane poza organizacją z wybranych aplikacji SaaS.

Drugie zasady blokują pobieranie plików na dowolne urządzenie niezarządzane. Wybierasz atrybuty w plikach do wyszukania oraz aplikacje SaaS, do których mają być stosowane zasady.

Te typy atrybutów wkrótce zostaną Defender dla Chmury Apps:

- Typy informacji poufnych
- Ujednolicone etykiety w Microsoft 365 i usłudze Azure Information Protection

### <a name="defender-for-cloud-apps-dashboard"></a>pulpit nawigacyjny aplikacji Defender dla Chmury

Jeśli jeszcze nie rozpoczęto korzystania z usługi Defender dla Chmury Apps, rozpocznij od jej uruchomienia. Aby uzyskać dostęp do aplikacji Defender dla Chmury: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Pamiętaj, aby włączyć opcję "Automatycznie skanuj pliki pod kątem etykiet klasyfikacji Information Protection platformy Azure" (w ustawieniach ogólnych) podczas rozpoczynania pracy z aplikacjami Defender dla Chmury lub przed przypisaniem etykiet. Po skonfigurowaniu usługa Defender dla Chmury Apps nie skanuje ponownie istniejących plików, dopóki nie zostaną zmodyfikowane.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image4.png" alt-text="Pulpit nawigacyjny przedstawiający informacje o alertach" lightbox="../../media/Monitor-for-leaks-of-personal-data-image4.png":::

Więcej informacji:

- [Wdrażanie aplikacji Defender dla Chmury](/cloud-app-security/getting-started-with-cloud-app-security)
- [Więcej informacji o Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Blokuj pobieranie poufnych informacji przy użyciu serwera proxy Microsoft Defender for Cloud Apps](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Przykładowe zasady dotyczące plików i działań do wykrywania udostępniania danych osobowych

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Wykrywanie udostępniania plików zawierających dane osobowe — numer karty kredytowej

Alert, gdy plik zawierający numer karty kredytowej jest udostępniany z zatwierdzonej aplikacji w chmurze.

|Kontroli|Ustawienia|
|---|---|
|Typ zasad|Zasady plików|
|Szablon zasad|Brak szablonu|
|Ważność zasad|High (Wysoki)|
|Kategoria|DLP|
|Ustawienia filtru|Poziom dostępu = Publiczny (Internet), Publiczny, Zewnętrzny <p> App = \<select apps\> (użyj tego ustawienia, jeśli chcesz ograniczyć monitorowanie do określonych aplikacji SaaS)|
|Zastosuj do|Wszystkie pliki, wszyscy właściciele|
|Inspekcja zawartości|Zawiera pliki zgodne z obecnym wyrażeniem: Wszystkie kraje: Finanse: Numer karty kredytowej <p> Nie wymagaj odpowiedniego kontekstu: niezaznaczone (to ustawienie będzie zgodne ze słowami kluczowymi i wyrażeniami regularnymi) <p> Zawiera pliki z co najmniej 1 dopasowaniem <p> Usuń maskowanie ostatnich 4 znaków naruszenia: zaznaczone|
|Alerty|Utwórz alert dla każdego pasującego pliku: zaznaczone <p> Dzienny limit alertów: 1000 <p> Wybierz alert jako wiadomość e-mail: zaznaczone <p> Do: infosec@contoso.com|
|Nadzór|Microsoft OneDrive dla Firm <p> Ustaw jako prywatny: zaznacz opcję Usuń użytkowników zewnętrznych <p> Wszystkie inne ustawienia: niezaznaczone <p> Microsoft Office SharePoint Online <p> Ustaw jako prywatny: zaznacz opcję Usuń użytkowników zewnętrznych <p> Wszystkie inne ustawienia: niezaznaczone|

Podobne zasady:

- Wykrywanie udostępniania plików zawierających identyfikator PII — adres e-mail
- Wykrywanie udostępniania plików zawierających identyfikator PII — numer paszportu

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Wykrywanie danych klienta lub działu kadr w usłudze Box lub OneDrive dla Firm

Alert po przekazaniu pliku z etykietą Dane klienta lub Dane działu kadr do OneDrive dla Firm lub Box.

Uwagi:

- Monitorowanie urządzenia Box wymaga skonfigurowania łącznika przy użyciu zestawu SDK łącznika interfejsu API.
- Te zasady wymagają możliwości, które są obecnie dostępne w prywatnej wersji zapoznawczej.

|Kontroli|Ustawienia|
|---|---|
|Typ zasad|Zasady działania|
|Szablon zasad|Brak szablonu|
|Ważność zasad|High (Wysoki)|
|Kategoria|Kontrola udostępniania|
|Działaj zgodnie z|Pojedyncze działanie|
|Ustawienia filtru|Typ działania = plik Upload <p> App = Microsoft OneDrive dla Firm i Box <p> Etykieta klasyfikacji (obecnie w prywatnej wersji zapoznawczej): azure Information Protection = dane klienta, zasoby ludzkie — dane wynagrodzeń, zasoby ludzkie — dane pracowników|
|Alerty|Tworzenie alertu: zaznaczone <p> Dzienny limit alertów: 1000 <p> Wybierz alert jako wiadomość e-mail: zaznaczone <p> Do: infosec@contoso.com|
|Nadzór|Wszystkie aplikacje <p> Umieść użytkownika w kwarantannie: sprawdź <p> Wszystkie inne ustawienia: niezaznaczone <p> Usługa Office 365 <p> Umieść użytkownika w kwarantannie: sprawdź <p> Wszystkie inne ustawienia: niezaznaczone|

Podobne zasady:

- Wykrywanie dużych pobrań danych klienta lub danych kadr — alert, gdy w krótkim czasie zostanie wykryta duża liczba plików zawierających dane klienta lub dane kadrowe pobieranych przez jednego użytkownika.
- Wykrywanie udostępniania danych klienta i działu kadr — alert, gdy pliki zawierające dane klienta lub działu kadr są udostępniane.
