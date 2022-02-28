---
title: Omówienie Microsoft 365 Lighthouse Windows usługi Microsoft 365 Lighthouse Windows 365 (komputery w chmurze)
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) korzystających z Microsoft 365 Lighthouse, dowiedz się więcej o Windows usługi Windows 365 (na komputerach w chmurze).
ms.openlocfilehash: a0d828a382000502f6700d585624b967a740ff36
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983794"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>Omówienie Windows usługi Windows 365 (Komputery w chmurze)  

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).
  
Windows 365 to usługa oparta na chmurze, która pozwala administratorom programu Microsoft Endpoint Manager (MEM) zapewniać obsługę komputerów w chmurze i zarządzanie nimi dla użytkowników, którzy mają licencję usługi Windows 365. Windows 365 jest w pełni zintegrowana z MEM do zarządzania urządzeniami, a Microsoft 365 Lighthouse na potrzeby zarządzania komputerami w chmurze partnerów we wszystkich dzierżawach klientów.

Aby uzyskać więcej informacji o Windows 365, zobacz Co [to jest Windows 365?](/windows-365/overview) Aby uzyskać listę wymagań Windows 365, zobacz [Wymagania dotyczące Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Aby zarządzać nimi w usłudze Lighthouse, musisz przejść do [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) w celu zapewnienia obsługi komputerów w chmurze dla poszczególnych dzierżawców. Nie można zapewniać obsługi z poziomu latarni morskiej.

Po zapewnienia obsługi administracyjnej komputerów w chmurze dla dzierżawy klienta karta Windows 365 na stronie głównej usługi Microsoft 365 udostępnia krótki alert na komputerach w chmurze potrzebny do działania, na przykład liczbę komputerów w chmurze, na których nie powiodło się inicjowanie obsługi administracyjnej, oraz awarie połączenia lokalnego połączenia sieciowego. Aby uzyskać szczegółowy stan, wybierz przycisk na karcie programu Windows 365 (lub wybierz pozycję **Windows 365** w lewym okienku nawigacji), aby otworzyć stronę Windows 365. Na tej stronie możesz uzyskać przegląd stanu komputerów w chmurze przypisanych do dzierżaw klientów, wyświetlić listę wszystkich komputerów w chmurze, które zarządzasz, oraz dzierżaw, do których są przypisane, oraz wyświetlić lokalne połączenia sieciowe między dzierżawami klientów i usługą Azure Active Directory (Azure AD) oraz ich stan.

## <a name="overview-tab"></a>Karta Omówienie

Na karcie Przegląd kolorowy pasek adnotacji z adnotacjami zawiera łączną liczbę komputerów w chmurze lub lokalnych połączeń sieciowych we wszystkich dzierżawach klientów o następujących stanie: Nieudane połączenia sieciowe, Nie aprowizowane, Inicjowanie obsługi administracyjnej nie powiodło się i Wkrótce zostanie zatrzymane udostępnianie administracyjne.

Poniżej paska adnotacji można zobaczyć zestawienie stanu komputerów w chmurze dla poszczególnych dzierżaw klientów. Aby sprawdzić, które dzierżawy mają komputery w chmurze o określonym stanie, wybierz ten stan na pasku adnotacji, aby przefiltrować listę. Aby wyświetlić statusy komputerów w chmurze dla jednej lub większej liczby dzierżaw klientów, użyj menu  rozwijanego Dzierżawy, aby przefiltrować listę.

Aby uzyskać szczegółowe informacje o stanie określonej dzierżawy klienta, wybierz wartość w dowolnej z kolumn stanu dla tej dzierżawy. W zależności od kolumny, w której znajduje się  ta wartość, zostanie otwarta karta  Lokalne połączenia sieciowe lub Wszystkie komputery w chmurze, aby wyświetlić więcej informacji.

Karta Omówienie zawiera również następujące opcje:

- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane z komputera w chmurze.
- **Eksportowanie:** Zaznacz, aby wyeksportować dane z komputera w chmurze Excel pliku z wartościami oddzielaymi .csv przecinkami.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć konkretny komputer w chmurze na liście.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Windows 365 — Omówienie.":::

## <a name="all-cloud-pcs-tab"></a>Karta Wszystkie komputery w chmurze

Na karcie Wszystkie komputery w chmurze na kolorowym pasku adnotacji jest wyświetlana łączna liczba komputerów w chmurze we wszystkich dzierżawach klientów o następujących stanie: Inicjowanie obsługi administracyjnej, Nieudostępniane inicjowanie obsługi administracyjnej, Inicjowanie obsługi administracyjnej nie powiodło się i Udostępnianie obsługi administracyjnej wkrótce.

Możesz wyświetlić wszystkie komputery w chmurze i ich stan inicjowania obsługi na liście poniżej paska adnotacji. Podano następujące informacje:

- **Nazwa komputera w chmurze:** Nazwa przypisana do komputera w chmurze.
- **Dzierżawa:** Dzierżawa klienta, w której aprowizowana była usługa Cloud PC.
- **Nazwa urządzenia:** Nazwa urządzenia Intune — identyfikator unikatowy dla komputera w chmurze.
- **typ komputera:** Typ komputera w chmurze zgodnie ze standardowymi jednostkami SKU.
- **Stan:** Stan obsługi administracyjnej komputera w chmurze.
- **Użytkownik:** Użytkownik, dla którego inicjowanie obsługi administracyjnej lub próbowano zapewnienia obsługi komputera w chmurze.

Aby sprawdzić, które dzierżawy mają komputery w chmurze z określonym stanem inicjowania obsługi, wybierz ten stan na pasku adnotacji, aby przefiltrować listę. Aby wyświetlić stan inicjowania obsługi komputera w chmurze dla jednej lub większej liczby dzierżaw klientów, użyj menu  rozwijanego Dzierżawy, aby przefiltrować listę.

Wybierz z listy dowolny komputer w chmurze, aby wyświetlić więcej szczegółów. Jeśli musisz podjąć działania na komputerze w chmurze, istnieją opcje wyświetlania zasad inicjowania obsługi administracyjnej dzierżawy i szczegółów urządzeń w Microsoft Endpoint Manager.

Karta Wszystkie komputery w chmurze zawiera również następujące opcje:

- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane z komputera w chmurze.
- **Eksportowanie:** Zaznacz, aby wyeksportować dane z komputera w chmurze Excel pliku z wartościami oddzielaymi .csv przecinkami.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć konkretny komputer w chmurze na liście.
- **Spróbuj ponownie inicjowanie obsługi administracyjnej:** Wybierz z listy 1–20 komputerów w chmurze o stanie Inicjowanie obsługi administracyjnej nie powiodło **się, a** następnie wybierz tę opcję, aby ponowić próbę inicjowania obsługi administracyjnej dla tych komputerów w chmurze.

Aby wyświetlić pełną listę stanu inicjowania obsługi komputera w chmurze i ich znaczenie, zobacz Omówienie zarządzania [](/windows-365/enterprise/device-management-overview#column-details) urządzeniami dla komputerów w chmurze w bibliotece dokumentacji usługi Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Windows 365 All Cloud PCs (Wszystkie komputery w chmurze).":::

## <a name="on-premises-network-connections-tab"></a>Lokalna karta połączeń sieciowych

Na karcie Lokalne połączenia sieciowe kolorowy pasek adnotacji z adnotacjami zawiera łączną liczbę lokalnych połączeń sieciowych we wszystkich dzierżawach klientów o następujących stanie: Połączenia pomyślne i Połączenia nieudane.

Na liście poniżej paska adnotacji można wyświetlić wszystkie lokalne połączenia sieciowe i ich stan połączenia.

Aby wyświetlić połączenia z określonym stanem inicjowania obsługi, wybierz ten stan na pasku adnotacji z adnotacjami, aby przefiltrować listę. Aby wyświetlić stan połączenia dla jednej lub większej liczby dzierżaw klientów, użyj menu rozwijanego  Dzierżawy, aby przefiltrować listę.

Jeśli musisz podjąć działania lub rozwiązać problemy z połączeniem na liście, wybierz pozycję **Wyświetl szczegóły połączenia** w Microsoft Endpoint Manager.

Karta Lokalne połączenia sieciowe zawiera również następujące opcje:

- **Odświeżanie:** Zaznacz, aby pobrać najnowsze dane połączenia.
- **Eksportowanie:** Zaznacz, aby wyeksportować dane połączenia Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone połączenie.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/on-prem-network-connections-tab.png" alt-text="Zrzut ekranu przedstawiający Windows lokalnych połączeń sieciowych usługi 365.":::

## <a name="related-content"></a>Zawartość pokrewna

[Co to jest Windows 365?](/windows-365/overview) (artykuł)\
[Windows zarządzanie urządzeniami w usłudze 365 dla komputerów](/windows-365/enterprise/device-management-overview) w chmurze (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)