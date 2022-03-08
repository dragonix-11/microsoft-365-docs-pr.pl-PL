---
title: Omówienie Microsoft 365 Lighthouse dzierżaw
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się więcej o stronie Dzierżawy.
ms.openlocfilehash: 23f151664455c35bb2fcc191d774ead00927e830
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329995"
---
# <a name="microsoft-365-lighthouse-tenants-page-overview"></a>Omówienie Microsoft 365 Lighthouse dzierżaw

Microsoft 365 Lighthouse umożliwia zarządzanie kontami dzierżawy, wybierając pozycję **Dzierżawy** w lewym okienku nawigacji, aby otworzyć stronę Dzierżawy. Strona Dzierżawy zawiera listę wszystkich Twoich dzierżaw. Możesz wybrać dzierżawę, aby wyświetlić szczegółowe informacje, takie jak szczegóły kontaktu i stan wdrożenia.

Na stronie Dzierżawy znajdują się również następujące opcje:

- **Eksportowanie:** Zaznacz, aby wyeksportować dane dzierżawy Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Zarządzanie tagami:** Wybierz, aby dodać, edytować lub usunąć tag.
- **Przypisz tagi:** Wybierz, aby przypisać tag do dzierżawy.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć konkretną dzierżawę na liście.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Zrzut ekranu przedstawiający stronę Dzierżawa.":::

## <a name="tenant-list"></a>Lista dzierżaw

Lista dzierżaw udostępnia szczegółowe informacje o różnych dzierżawach, z których masz umowę, w tym o stanie dołączania do latarni lighthouse dzierżawy. Lista dzierżaw umożliwia również oznaczanie dzierżaw w celu zapewnienia różnych filtrów w latarni morskiej i przechodzenie do szczegółów, aby dowiedzieć się więcej o danej dzierżawie i stanie jej planu wdrażania.

Gdy dzierżawcy spełnią wymagania dotyczące dołączania do latarni [lighthouse](m365-lighthouse-requirements.md), jej stan będzie miał status **Aktywny na liście** dzierżawy.

Lista dzierżaw umożliwia:

- Automatyczne sortowanie dzierżaw według aktywnych, nieaktywnych i nieuklasyfikujących.
- Wyeksportuj listę dzierżaw.
- Przypisywanie tagów i zarządzanie nimi.
- Wyszukaj dzierżawy według nazwy.
- Filtruj dzierżawy według stanu, delegowanego uprawnienia administracyjnego (DAP) i tagów.

Aby dezaktywować dzierżawę lub wyświetlić tagi i zarządzać nimi, wybierz trzy kropki (więcej akcji) obok nazwy dzierżawy. Możesz wyświetlić poszczególnych dzierżaw, wybierając nazwę dzierżawy lub wybierając jeden z tagów przypisanych do dzierżawy.

## <a name="tenant-status"></a>Stan dzierżawy

W poniższej tabeli przedstawiono różne statusy i ich znaczenie.<br><br>

| Stan                                   | Opis                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Aktywny                                   | Rozpoczęto dołączanie do dzierżawy i przepływ danych.                                                           |
| Nieaktywny                                 | Dzierżawa została wyłączona na żądanie usługi MSP i nie jest już zarządzana w latarni morskiej.           |
| W trakcie procesu                               | Dzierżawa została wykryta, ale nie została w pełni wyedytowana.                                                              |
| Nieuprawniany — nie jest jeszcze skonfigurować protokołu DAP lub GDAP    | Partner musi mieć delegowane (DAP) lub poziome uprawnienia administratora (GDAP) delegowane na poziomie dzierżawy. |
| Nieukwalifikowana — brakuje wymaganej licencji | Dzierżawa nie ma wymaganej licencji.                                                               |
| Bez uprawnienia — przekroczono liczbę użytkowników         | Dzierżawa ma więcej użytkowników niż jest dozwolonych.                                                                     |
| Nieukwalifikowane — sprawdzenie geolokalizacji nie powiodło się            | Partner i klient muszą znajdować się w tej samej lokalizacji geograficznej.                                       |

Po dezaktywowania dzierżawy nie możesz podjąć żadnych działań w tej dzierżawie do czasu zakończenia procesu dezaktywowania. Dezaktywacja może potrwać do 48 godzin. W przypadku podjęcia decyzji o ponownej aktywacji dzierżawy może upłynieć do 48 godzin, aż dane ponownie się pojawią.

## <a name="tenant-tags"></a>Tagi dzierżawy

Aby ułatwić organizowanie dzierżaw i łatwo filtrować istniejące widoki, możesz tworzyć tagi i przypisywać je do dzierżaw. Aby dowiedzieć się więcej, zobacz [Zarządzanie listą dzierżaw](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Możesz utworzyć do 30 tagów we wszystkich dzierżawach.

## <a name="tenant-details-page"></a>Strona szczegółów dzierżawy

Aby wyświetlić szczegółowe informacje o dzierżawie, wybierz dzierżawę z listy dzierżaw. Strona szczegółów dzierżawy zawiera informacje kontaktowe i stan planu wdrażania.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Zrzut ekranu przedstawiający stronę Szczegóły dzierżawy.":::

### <a name="overview-tab"></a>Karta Omówienie

Na karcie Omówienie możesz wyświetlić omówienie dzierżawy, informacje kontaktowe Microsoft 365 użycia usługi.

#### <a name="tenant-overview-card"></a>Karta przegląd dzierżawy

Karta Przegląd dzierżawy zawiera informacje o dzierżawie z jej Microsoft 365 dzierżawy.<br><br>

| Informacje o dzierżawie    | Opis|
|-----------------------|------------------|
| Headquarters    | Miejsce, w którym znajduje się dzierżawa.|
| Branża    |Branżę firmy.|
| Witryna internetowa    |Witryna internetowa organizacji. Możesz edytować to pole, jeśli nie podano żadnych danych.|
| Domena klienta    |Domena organizacji.|
| Łączna liczba użytkowników    |Liczba użytkowników przypisanych w dzierżawie. Możesz wybrać ten numer, aby otworzyć stronę Użytkownicy dla tej dzierżawy.|
| Łączna liczba urządzeń|Liczba urządzeń zarejestrowanych w dzierżawie. Możesz wybrać ten numer, aby otworzyć stronę Urządzenia dla tej dzierżawy.|

#### <a name="contacts-card"></a>Wizytówka

Karta Kontakty umożliwia wprowadzanie informacji dotyczących kluczowych kontaktów w obrębie zarządzanych dzierżaw, takich jak:

- Name (Nazwa)
- Tytuł
- Phone
- Poczta e-mail
- Uwagi

Sekcja Notatki to pole tekstowe, za pomocą których można rejestrować kluczowe informacje o dzierżawie, takie jak preferencje zaangażowania, lokalizacja, strefa czasowa i szczegóły dotyczące jej roli w organizacji.

Aby edytować szczegóły lub usunąć istniejący kontakt, wybierz jego nazwę z listy. W **okienku Edytowanie** kontaktu edytuj lub usuń kontakt. Aby dodać kolejny kontakt, wybierz pozycję **+Dodaj kontakt**.

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 karty użycia

Lighthouse dostarcza szczegółowych informacji o Microsoft 365 usługach, w tym o tym, ilu użytkowników w ramach dzierżawy jest licencjonowanych i aktywnie korzysta z poszczególnych usług. Aktywny wskazuje liczbę użytkowników lub urządzeń, które zalogowały się do usługi co najmniej raz w ciągu ostatnich 28 dni. Zmiana oznacza zmianę w aktywnych użytkownikach i urządzeniach od ostatniego miesiąca.

Karta Microsoft 365 zawiera dwie sekcje:

- **Microsoft 365 Lighthouse usługami z włączoną obsługą:** Usługi, które można zarządzać w portalu lighthouse.
- **Dodatkowe Microsoft 365 usługi:** Usługi zawarte w pakiecie Microsoft 365, ale obecnie nie można nimi zarządzać w portalu Microsoft 365 Lighthouse.

### <a name="deployment-plans-tab"></a>Karta Plany wdrażania

Karta Plany wdrażania zawiera informacje o stanie planu wdrażania dzierżawy. Kroki wdrażania na liście są oparte na planie bazowym zastosowanym do dzierżawy. Aby wyświetlić szczegóły etapu wdrożenia, wybierz krok wdrożenia z listy.

Karta Plany wdrażania zawiera również następujące opcje:

- **Eksportowanie:** Wybierz, aby wyeksportować dane o krokach wdrożenia Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane o krokach wdrożenia.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć określony krok wdrożenia na liście.

## <a name="related-content"></a>Zawartość pokrewna

[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Zarządzanie listą dzierżaw](m365-lighthouse-manage-tenant-list.md) (artykuł)\
[Omówienie wdrażania standardowych konfiguracji dzierżawy](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) przy użyciu planu bazowego (artykuł)\
[Wdrażanie Microsoft 365 Lighthouse bazowych](m365-lighthouse-deploy-baselines.md) (artykuł)
