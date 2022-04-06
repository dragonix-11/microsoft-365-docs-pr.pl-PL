---
title: Monitorowanie wycieków danych osobistych
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
description: Dowiedz się więcej o trzech narzędziach, których można używać do monitorowania wycieków danych osobistych.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4024640173d6cbbf6817d3fa2b1c24cb7264833c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470862"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Monitorowanie wycieków danych osobistych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Istnieje wiele narzędzi, których można używać do monitorowania używania i transportu danych osobowych. W tym temacie opisano trzy dobrze dobrane narzędzia.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image1.png" alt-text="Narzędzia do monitorowania wykorzystania i transportu danych osobistych" lightbox="../../media/Monitor-for-leaks-of-personal-data-image1.png":::

Na ilustracji:

- Zacznij od raportów Microsoft 365 ochrony przed utratą danych w celu monitorowania danych osobowych w sieciach SharePoint Online, OneDrive dla Firm i wiadomościach e-mail podczas przesyłania. Raporty te zawierają najwyższy poziom szczegółów monitorowania danych osobowych. Raporty te nie zawierają jednak wszystkich usług w programie Office 365.

- Następnie użyj zasad alertów i dziennika inspekcji, aby monitorować aktywność w różnych usługach. Skonfiguruj monitorowanie bieżące lub przeszukaj dziennik inspekcji w celu zbadania zdarzenia. Dziennik inspekcji działa w różnych usługach — Sway, Power BI, zbierania elektronicznych materiałów dowodowych, Dynamics 365, Power Automate, Microsoft Teams, Działania administratorów, OneDrive dla Firm, SharePoint Online, poczta w trakcie przesyłania i skrzynki pocztowe w miejscu spoczynku. Skype konwersacji są uwzględniane w skrzynkach pocztowych w spoczynku.

- Ponadto używaj oprogramowania Microsoft Defender for Cloud Apps do monitorowania plików z poufnymi danymi w innych dostawcach SaaS. Wkrótce będzie można używać typów informacji poufnych i ujednoliconych etykiet na platformie Azure Information Protection i Office z Defender dla Chmury Apps. Możesz skonfigurować zasady, które będą stosowane do wszystkich Twoich aplikacji SaaS lub określonych aplikacji (takich jak Box). Defender dla Chmury aplikacje nie wykrywają plików w aplikacji Exchange Online, w tym plików dołączonych do wiadomości e-mail.

## <a name="data-loss-prevention-reports"></a>Raporty dotyczące ochrony przed utratą danych

Po utworzeniu zasad ochrony przed utratą danych (DLP, Data Loss Prevention), musisz upewnić się, że działają one zgodnie z twoimi zamiarami, i pomóc Ci w zachowania zgodności. Dzięki raportom ochrony przed zasadami DLP w programie Office 365 możesz szybko wyświetlać liczbę spotkań zasad DLP, zastępować lub wyników fałszywie dodatnich; sprawdzać, czy są one trendowane w górę, czy w dół w czasie; filtrować raport na różne sposoby i wyświetlać więcej szczegółów, wybierając punkt na wykresie.

Raporty funkcji DLP mogą być w ten sposób:

- Skoncentruj się na określonych okresach czasu i poznaj przyczyny kolekcji i trendów.
- Odnajdowanie procesów biznesowych naruszających zasady ochrony przed firmami.
- Zrozumienie jakiegokolwiek wpływu biznesowego zasad DLP.
- Wyświetl justowanie przesłane przez użytkowników, gdy rozpoznają poradę o zasadach, zastępując zasady lub zgłaszając wynik fałszywie dodatni.
- Sprawdź zgodność z określonymi zasadami DLP, wyświetlając wszystkie dopasowania dla tych zasad.
- W okienku szczegółów można wyświetlić listę plików z danymi poufnymi, które są zgodnie z zasadami ochrony przed dlp.

Ponadto przy użyciu raportów funkcji DLP można precyzyjnie dostosować zasady DLP podczas uruchamiania ich w trybie testowania.

Raporty DLP znajdują się w Centrum zgodności platformy Microsoft 365. Przejdź do **sekcji Raporty** \> **Danych organizacyjnych**, aby znaleźć dopasowania zasad DLP, zdarzenia **DLP** oraz raporty o wynikach fałszywie dodatnich i zastępować zasad **DLP**.

Aby uzyskać więcej informacji, [zobacz Wyświetlanie raportów w celu ochrony przed utratą danych](../../compliance/view-the-dlp-reports.md).

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image2.png" alt-text="Raport przedstawiający dopasowania zasad DLP" lightbox="../../media/Monitor-for-leaks-of-personal-data-image2.png":::

## <a name="audit-log-and-alert-policies"></a>Dziennik inspekcji i zasady alertów

Dziennik inspekcji zawiera zdarzenia z usług Exchange Online, SharePoint Online, OneDrive dla Firm, Azure Active Directory, Microsoft Teams, Power BI, Sway i innych usługi.

Portal Microsoft 365 Defender i raporty Centrum zgodności platformy Microsoft 365 dwa sposoby monitorowania i tworzenia raportów w dzienniku inspekcji:

- Konfigurowanie zasad alertów, wyświetlanie alertów i monitorowanie trendów — korzystanie z zasad alertów i narzędzi pulpitu nawigacyjnego alertów w portalu alertów Microsoft 365 Defender sieci Centrum zgodności platformy Microsoft 365.
- Przeszukiwanie dziennika inspekcji bezpośrednio: Wyszukaj wszystkie zdarzenia w określonym przedziale dat. Możesz również filtrować wyniki według określonych kryteriów, takich jak użytkownik, który wykonał akcję, akcję lub obiekt docelowy.

Dzięki tym narzędziom zespoły ds. zgodności z informacjami i zabezpieczeń mogą aktywnie przeglądać działania wykonywane przez użytkowników końcowych i administratorów w różnych usługach. Automatyczne alerty można skonfigurować tak, aby wysyłać powiadomienia e-mail, gdy w określonych zbiorach witryn wystąpią określone działania — na przykład gdy zawartość jest udostępniana z witryn nazywanych informacjami związanymi z RODO. Umożliwia to tym zespołom obserwowanie użytkowników w celu zapewnienia, że są stosowane firmowe zasady zabezpieczeń, lub zapewnienie dodatkowego szkolenia.

Zespoły ds. zabezpieczeń informacji mogą również przeszukiwać dziennik inspekcji w celu zbadania podejrzewanych naruszeń danych i określenia zarówno głównej przyczyny, jak i zakresu naruszenia. Ta wbudowana funkcja ułatwia zachowanie zgodności z artykułem 33 i 34 RODO, który wymaga powiadomienia urzędu nadzorczygo RODO i podmiotom danych o naruszeniu danych w danym okresie. Wpisy dziennika inspekcji są przechowywane tylko przez 90 dni w ramach usługi — jest to często zalecane i wiele organizacji wymaga, aby te dzienniki były przechowywane przez dłuższy czas.

Dostępne są rozwiązania, które subskrybują ujednolicone dzienniki inspekcji za pomocą interfejsu API działań zarządzania firmy Microsoft i mogą w razie potrzeby przechowywać wpisy dziennika oraz zapewniać zaawansowane pulpity nawigacyjne i alerty. Przykładem jest pakiet [Microsoft Operations Management Suite (OMS).](/azure/operations-management-suite/oms-solution-office-365)

Więcej informacji na temat zasad alertów i przeszukiwania dziennika inspekcji:

- [Zasady alertów w programie Microsoft 365](../../compliance/alert-policies.md)
- [Wyszukiwanie działań użytkowników i administratorów w dzienniku inspekcji w programie Office 365](../../compliance/search-the-audit-log-in-security-and-compliance.md) (wprowadzenie)
- [Włączanie lub wyłączanie przeszukiwania dziennika inspekcji](../../compliance/turn-audit-log-search-on-or-off.md)
- [Przeszukaj dziennik inspekcji](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (polecenie cmdlet)
- [Szczegółowe właściwości w dzienniku inspekcji](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps pomaga w odnajdywaniu innych aplikacji SaaS w użytku w twoich sieciach oraz danych poufnych wysyłanych do i z tych aplikacji.

Microsoft Defender for Cloud Apps to kompleksowy program zapewniający szczegółową widoczność, szczegółową kontrolę i ulepszoną ochronę przed zagrożeniami dla aplikacji w chmurze. Identyfikuje ona ponad 15 000 aplikacji w chmurze w Twojej sieci ze wszystkich urządzeń i udostępnia ocenianie ryzyka oraz bieżącą ocenę ryzyka i analizy. Nie są wymagani żadni agenci: z Twoich zapór i serwerów proxy są zbierane informacje, aby zapewnić Ci pełną widoczność i kontekst użycia chmury i cienia IT.

Aby lepiej zrozumieć środowisko chmury, funkcja Defender dla Chmury aplikacje bada szczegółowe informacje na temat wszystkich działań, plików i kont dla aplikacji zarządzanych i zweryfikowanych. Możesz uzyskać szczegółowe informacje na poziomie pliku i dowiedzieć się, gdzie są przemieszczane dane w aplikacjach w chmurze.

Na przykład na poniższej ilustracji przedstawiono dwie zasady dotyczące aplikacji Defender dla Chmury, które mogą pomóc w zakresie RODO.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image3.png" alt-text="Zasady Defender dla Chmury aplikacji" lightbox="../../media/Monitor-for-leaks-of-personal-data-image3.png":::

Pierwsze alerty zasad są alertowane, gdy pliki z wstępnie zdefiniowanym atrybutem PII lub wyrażeniem niestandardowym są udostępniane poza organizacją z określonych aplikacji SaaS.

Druga zasada blokuje pobieranie plików na dowolne urządzenie niezakierowane. Wybierasz atrybuty w plikach do wyszukiwania i aplikacje SaaS, których mają dotyczyć zasady.

Te typy atrybutów zostaną wkrótce Defender dla Chmury aplikacje:

- Typy informacji poufnych
- Ujednolicone etykiety w usługach Microsoft 365 i Azure Information Protection

### <a name="defender-for-cloud-apps-dashboard"></a>Defender dla Chmury pulpit nawigacyjny aplikacji

Jeśli korzystanie z aplikacji Pakietu Office nie zostało jeszcze przez Ciebie Defender dla Chmury, zacznij od jego uruchamiania. Aby uzyskać dostęp Defender dla Chmury aplikacji: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Pamiętaj o włączeniu ustawienia "Automatycznie skanuj pliki pod Information Protection klasyfikacji usługi Azure" (w ustawieniach ogólnych) podczas rozpoczynania pracy z aplikacjami pakietu Defender dla Chmury lub przed przypisaniem etykiet. Po zakończeniu konfiguracji Defender dla Chmury ponownie skanuje istniejące pliki, dopóki nie zostaną zmodyfikowane.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image4.png" alt-text="Pulpit nawigacyjny z informacjami o alertach" lightbox="../../media/Monitor-for-leaks-of-personal-data-image4.png":::

Więcej informacji:

- [Wdrażanie Defender dla Chmury aplikacji](/cloud-app-security/getting-started-with-cloud-app-security)
- [Więcej informacji na temat Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Blokowanie pobierania poufnych informacji przy użyciu Microsoft Defender for Cloud Apps proxy](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Przykładowe zasady dotyczące plików i aktywności w celu wykrywania udostępniania danych osobistych

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Wykrywanie udostępniania plików zawierających dane pii — numer karty kredytowej

Alert, gdy plik zawierający numer karty kredytowej jest udostępniany za pomocą zatwierdzonej aplikacji w chmurze.

|Kontrolka|Ustawienia|
|---|---|
|Typ zasad|Zasady dotyczące plików|
|Szablon zasad|Brak szablonu|
|Ważność zasad|High (Wysoki)|
|Kategoria|DLP|
|Ustawienia filtru|Poziom dostępu = Publiczny (Internet), Publiczny, Zewnętrzny <p> App = \<select apps\> (użyj tego ustawienia, jeśli chcesz ograniczyć monitorowanie do określonych aplikacji SaaS)|
|Zastosuj do|Wszystkie pliki, wszyscy właściciele|
|Inspekcja zawartości|Pliki zgodne z wyrażeniem w prezentacji: Wszystkie kraje: Finanse: numer karty kredytowej <p> Nie wymagaj istotnego kontekstu: niezaznaczone (to ustawienie będzie zgodne ze słowami kluczowymi, jak również regex) <p> Zawiera pliki o co najmniej 1 dopasowaniach <p> Unmask the last 4 characters of the violation: checked|
|Alerty|Tworzenie alertu dla każdego pasującego pliku: zaznaczone <p> Dzienny limit alertów: 1000 <p> Wybierz alert jako wiadomość e-mail: zaznaczone <p> Do: infosec@contoso.com|
|Nadzór|Microsoft OneDrive dla Firm <p> Zamieć prywatne: zaznacz pole wyboru Usuń użytkowników zewnętrznych <p> Wszystkie inne ustawienia: niezaznaczone <p> Microsoft Office SharePoint Online <p> Zamieć prywatne: zaznacz pole wyboru Usuń użytkowników zewnętrznych <p> Wszystkie inne ustawienia: niezaznaczone|

Podobne zasady:

- Wykrywanie udostępniania plików zawierających dane PII — adres e-mail
- Wykrywanie udostępniania plików zawierających dane PII — numer paszportu

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Wykrywanie danych klienta lub kadr w uścisce lub OneDrive dla Firm

Alert, gdy plik oznaczony jako Dane klienta lub Dane HR zostanie przekazany do OneDrive dla Firm lub Box.

Uwagi:

- Monitorowanie pola wymaga skonfigurowania łącznika przy użyciu zestawu SDK łącznika interfejsu API.
- Te zasady wymagają funkcji, które są obecnie w prywatnej wersji Preview.

|Kontrolka|Ustawienia|
|---|---|
|Typ zasad|Zasady aktywności|
|Szablon zasad|Brak szablonu|
|Ważność zasad|High (Wysoki)|
|Kategoria|Udostępnianie kontroli|
|Działanie w dniu|Pojedyncza aktywność|
|Ustawienia filtru|Typ działania = Upload pliku <p> App = Microsoft OneDrive dla Firm i Box <p> Etykieta klasyfikacji (obecnie w prywatnej wersji zapoznawczej): usługa Azure Information Protection = Dane klienta, Dział kadr — Dane płac, Kadry — Dane pracowników|
|Alerty|Tworzenie alertu: zaznaczone <p> Dzienny limit alertów: 1000 <p> Wybierz alert jako wiadomość e-mail: zaznaczone <p> Do: infosec@contoso.com|
|Nadzór|Wszystkie aplikacje <p> Umieść użytkownika w kwarantannie: sprawdź <p> Wszystkie inne ustawienia: niezaznaczone <p> Usługa Office 365 <p> Umieść użytkownika w kwarantannie: sprawdź <p> Wszystkie inne ustawienia: niezaznaczone|

Podobne zasady:

- Wykrywanie dużych ilości pobieranych danych klienta lub danych HR — ostrzegaj, gdy jeden użytkownik wykryje, że duża liczba plików zawierających dane klienta lub dane HR zostanie pobrana przez jednego użytkownika w krótkim czasie.
- Wykrywanie udostępniania danych klientów i kadr — alerty w przypadku udostępniania plików zawierających dane klienta lub kadr.
