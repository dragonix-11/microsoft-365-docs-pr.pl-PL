---
title: Omówienie strony Dzierżawy w Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zapoznaj się ze stroną Dzierżawy.
ms.openlocfilehash: 0f25f8bb02c6957598b2b328bc7832c429ca1e7a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128379"
---
# <a name="overview-of-the-tenants-page-in-microsoft-365-lighthouse"></a>Omówienie strony Dzierżawy w Microsoft 365 Lighthouse

Microsoft 365 Lighthouse umożliwia zarządzanie kontami dzierżaw, wybierając pozycję **Dzierżawy** w okienku nawigacji po lewej stronie, aby otworzyć stronę Dzierżawy. Strona Dzierżawy zawiera listę wszystkich dzierżaw. Możesz wybrać dzierżawę, aby wyświetlić szczegółowe informacje, w tym szczegóły kontaktu i stan wdrożenia.

Strona Dzierżawy zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane dzierżawy do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Zarządzaj tagami:** Wybierz, aby dodać, edytować lub usunąć tag.
- **Przypisz tagi:** Wybierz, aby przypisać tag do dzierżawy.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określoną dzierżawę na liście.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Zrzut ekranu przedstawiający stronę Dzierżawa.":::

## <a name="tenant-list"></a>Lista dzierżaw

Lista dzierżaw zawiera szczegółowe informacje na temat różnych dzierżaw, z których masz umowę, w tym ich stan dołączania do usługi Lighthouse dzierżawy. Lista dzierżaw umożliwia również tagowanie dzierżaw w celu zapewnienia różnych filtrów w całej usłudze Lighthouse oraz przechodzenie do szczegółów, aby dowiedzieć się więcej o danej dzierżawie i stanie jej planu wdrożenia.

Gdy dzierżawcy spełnią [wymagania dotyczące dołączania do usługi Lighthouse](m365-lighthouse-requirements.md), jego stan będzie wyświetlany jako **Aktywny** na liście dzierżaw.

Lista dzierżaw umożliwia:

- Automatycznie sortuj dzierżawy według aktywnych, nieaktywnych i niekwalifikujących się.
- Wyeksportuj listę dzierżaw.
- Przypisywanie tagów i zarządzanie nimi.
- Wyszukaj dzierżawy według nazwy.
- Filtruj dzierżawy według stanu, delegowanego uprawnienia administracyjnego (DAP) i tagów.

Aby uaktywnić dzierżawę lub wyświetlić tagi i zarządzać nimi, wybierz trzy kropki (więcej akcji) obok nazwy dzierżawy. Poszczególne dzierżawy można wyświetlić, wybierając nazwę dzierżawy lub wybierając jeden z tagów przypisanych do dzierżawy.

Aby uzyskać informacje na temat dodawania dzierżaw, zobacz [Dodawanie wielu dzierżaw i zarządzanie nimi na koncie Centrum partnerskiego](/partner-center/multi-tenant-account).

## <a name="tenant-status"></a>Stan dzierżawy

W poniższej tabeli przedstawiono różne stany i ich znaczenie. Aby uzyskać informacje na temat rozwiązywania problemów ze stanami dzierżawy klienta, zobacz [Rozwiązywanie problemów z komunikatami o błędach i problemami w Microsoft 365 Lighthouse: dołączanie dzierżawy klienta](m365-lighthouse-troubleshoot.md#customer-tenant-onboarding).<br><br>

| Stan                                   | Opis                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Aktywny                                   | Rozpoczęto dołączanie dzierżawy i przepływ danych.                                                           |
| Nieaktywne                                 | Dzierżawa została odłączona na żądanie MSP i nie jest już zarządzana w Lighthouse.           |
| W toku                               | Dzierżawa została odnaleziona, ale nie jest w pełni dołączona.                                                              |
| Niekwalifikowalne — nie skonfigurowano protokołu DAP lub GDAP    | Partner musi mieć delegowane uprawnienia administratora (DAP) lub uprawnienia administratora delegowania szczegółowego (GDAP) skonfigurowane w dzierżawie. |
| Niekwalifikowalne — brak wymaganej licencji | Dzierżawa nie ma wymaganej licencji.                                                               |
| Niekwalifikowalne — przekroczono liczbę użytkowników         | Dzierżawa ma więcej użytkowników niż jest to dozwolone.                                                                     |
| Niekwalifikowalne — sprawdzanie geograficzne nie powiodło się            | Partner i klient muszą znajdować się w tej samej lokalizacji geograficznej.                                       |

Po uaktywnieniu dzierżawy nie można wykonać akcji w dzierżawie do czasu zakończenia procesu inaktywacji. Wykonanie nieaktywnego działania może potrwać do 48 godzin. Jeśli zdecydujesz się ponownie uaktywnić dzierżawę, ponowne pojawienie się danych może potrwać do 48 godzin.

## <a name="tenant-tags"></a>Tagi dzierżawy

Aby ułatwić organizowanie dzierżaw i łatwe filtrowanie istniejących widoków, możesz tworzyć i przypisywać tagi do dzierżaw. Aby dowiedzieć się więcej, zobacz [Zarządzanie listą dzierżaw w Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Możesz utworzyć maksymalnie 30 tagów w całej dzierżawie.

## <a name="tenant-details-page"></a>Strona szczegółów dzierżawy

Aby wyświetlić szczegółowe informacje o dzierżawie, wybierz dzierżawę z listy dzierżaw. Strona szczegółów dzierżawy zawiera informacje kontaktowe i stan planu wdrożenia.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Zrzut ekranu przedstawiający stronę szczegółów dzierżawy.":::

### <a name="overview-tab"></a>Karta Przegląd

Na karcie Przegląd możesz wyświetlić omówienie dzierżawy, informacje kontaktowe i użycie usługi Microsoft 365.

#### <a name="tenant-overview-card"></a>Karta przeglądu dzierżawy

Karta Przegląd dzierżawy zawiera informacje o dzierżawie z konta Microsoft 365.<br><br>

| Informacje o dzierżawie    | Opis|
|-----------------------|------------------|
| Headquarters    | Gdzie znajduje się dzierżawa.|
| Przemysłu    |Branża organizacji.|
| Stronie internetowej    |Witryna internetowa organizacji. To pole można edytować, jeśli nie podano żadnych danych.|
| Domena klienta    |Domena organizacji.|
| Łączna liczba użytkowników    |Liczba użytkowników przypisanych do dzierżawy. Możesz wybrać ten numer, aby otworzyć stronę Użytkownicy dla tej dzierżawy.|
| Łączna liczba urządzeń|Liczba urządzeń zarejestrowanych w dzierżawie. Możesz wybrać ten numer, aby otworzyć stronę Urządzenia dla tej dzierżawy.|

#### <a name="contacts-card"></a>Karta Kontakty

Karta Kontakty umożliwia wprowadzanie informacji dotyczących kluczowych kontaktów w zarządzanych dzierżawach, takich jak:

- Name (Nazwa)
- Tytuł
- Phone
- Poczta e-mail
- Uwagi

Sekcja Notatki to pole tekstowe, którego można użyć do rejestrowania kluczowych informacji dla dzierżawy, takich jak preferencje zaangażowania, lokalizacja, strefa czasowa i szczegóły dotyczące ich roli w organizacji.

Aby edytować szczegóły lub usunąć istniejący kontakt, wybierz z listy nazwę kontaktu. W okienku **Edytowanie kontaktu edytuj** lub usuń kontakt. Aby dodać kolejny kontakt, wybierz pozycję **+Dodaj kontakt**.

#### <a name="microsoft-365-usage-card"></a>karta użycia Microsoft 365

Usługa Lighthouse zapewnia wgląd w użycie usług Microsoft 365, w tym liczbę użytkowników w ramach dzierżawy, którzy są licencjonowani i aktywnie korzystają z każdej usługi. Active wskazuje liczbę użytkowników lub urządzeń, którzy zalogowali się do usługi co najmniej raz w ciągu ostatnich 28 dni. Zmiana wskazuje na zmianę aktywnych użytkowników i urządzeń od ostatniego miesiąca.

Karta Microsoft 365 Użycie zawiera dwie sekcje:

- **usługi z obsługą Microsoft 365 Lighthouse:** usługi, które można zarządzać w portalu lighthouse.
- **Dodatkowe usługi Microsoft 365:** usługi, które są zawarte w pakiecie Microsoft 365, ale nie mogą być obecnie zarządzane w portalu Microsoft 365 Lighthouse.

### <a name="deployment-plans-tab"></a>Karta Plany wdrożenia

Karta Plany wdrażania zawiera stan planu wdrożenia dzierżawy. Kroki wdrażania na liście są oparte na linii bazowej zastosowanej do dzierżawy. Aby wyświetlić szczegóły kroku wdrożenia, wybierz krok wdrożenia z listy.

Karta Plany wdrażania zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane kroku wdrożenia do pliku wartości rozdzielanych przecinkami Excel (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane kroków wdrażania.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określony krok wdrożenia na liście.

## <a name="related-content"></a>Zawartość pokrewna

[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)\
[Zarządzanie listą dzierżaw w Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (artykuł)\
[Omówienie wdrażania standardowych konfiguracji dzierżawy za pomocą Microsoft 365 Lighthouse planów bazowych](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artykuł)\
[Wdrażanie Microsoft 365 Lighthouse punktów odniesienia](m365-lighthouse-deploy-baselines.md) (artykuł)
