---
title: Omówienie Microsoft 365 Lighthouse Windows 365 (Komputery w chmurze)
f1.keywords: CSH
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się więcej o stronie Windows 365 (Cloud PC).
ms.openlocfilehash: fa910e3de992aa3f3f76090f76a473a96aebc8fb
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387116"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>Omówienie Windows 365 (Komputery w chmurze)  
  
Windows 365 to usługa oparta na chmurze, która pozwala administratorom programu Microsoft Endpoint Manager (MEM) zapewniać obsługę komputerów w chmurze i zarządzać nimi dla użytkowników, którzy mają licencję usługi Windows 365. Windows 365 jest w pełni zintegrowana z MEM do zarządzania urządzeniami oraz Microsoft 365 Lighthouse na potrzeby zarządzania komputerami w chmurze partnerów we wszystkich dzierżawach klientów.

Aby uzyskać więcej informacji o Windows 365, zobacz Co [to jest Windows 365?](/windows-365/overview) Aby uzyskać listę wymagań Windows 365, [zobacz Wymagania dotyczące Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Aby zarządzać nimi w usłudze Lighthouse, musisz przejść do [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) w celu zapewnienia obsługi komputerów w chmurze dla poszczególnych dzierżawców. Nie można zapewniać obsługi z poziomu latarni morskiej.

Po zapewnienia obsługi administracyjnej komputerów w chmurze dla dzierżawy klienta karta Windows 365 na stronie głównej usługi Microsoft 365 udostępnia krótki alert dotyczący komputerów w chmurze potrzebny do działania, na przykład liczba komputerów z chmurą, których nie można było aprowizować, oraz awarie połączenia sieciowego platformy Azure. Aby uzyskać szczegółowy stan, wybierz przycisk na karcie Windows 365 (lub wybierz pozycję Windows 365 w lewym okienku  nawigacji), aby otworzyć Windows 365 stronę. Na tej stronie możesz uzyskać przegląd stanu komputerów w chmurze przypisanych do dzierżaw klientów, wyświetlić listę wszystkich komputerów w chmurze, które zarządzasz, oraz dzierżaw, do których są przypisani, oraz wyświetlić połączenia sieciowe platformy Azure między dzierżawami klientów i usługą Azure Active Directory (Azure AD) oraz ich stan.

## <a name="overview-tab"></a>Karta Omówienie

Na karcie Przegląd kolorowy pasek adnotacji z adnotacjami zawiera łączną liczbę komputerów w chmurze lub połączeń sieciowych platformy Azure we wszystkich dzierżawach klientów o następujących stanie: Nieudane połączenia sieciowe, Bez obsługi administracyjnej, Inicjowanie obsługi administracyjnej nie powiodło się i Wkrótce zostanie zatrzymane udostępnianie administracyjne.

Poniżej paska adnotacji można zobaczyć zestawienie stanu komputerów w chmurze dla poszczególnych dzierżaw klientów. Aby sprawdzić, które dzierżawy mają komputery w chmurze o określonym stanie, wybierz ten stan na pasku adnotacji, aby przefiltrować listę. Aby wyświetlić statusy komputerów w chmurze dla jednej lub większej liczby dzierżaw klientów, użyj menu  rozwijanego Dzierżawy, aby przefiltrować listę.

Aby uzyskać szczegółowe informacje o stanie określonej dzierżawy klienta, wybierz wartość w dowolnej z kolumn stanu dla tej dzierżawy. W zależności od kolumny, w której znajduje się ta wartość, zostanie  otwarta karta **Połączenia sieciowe platformy Azure** lub Wszystkie komputery w chmurze, aby wyświetlić więcej informacji.

Karta Omówienie zawiera również następujące opcje:

- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane z komputera w chmurze.
- **Eksportowanie:** Zaznacz, aby wyeksportować dane z komputera w chmurze Excel pliku z wartościami oddzielaymi .csv przecinkami.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć konkretny komputer w chmurze na liście.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Windows 365 Przegląd." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Karta Wszystkie komputery w chmurze

Na karcie Wszystkie komputery w chmurze na kolorowym pasku adnotacji jest wyświetlana łączna liczba komputerów w chmurze we wszystkich dzierżawach klientów o następujących stanie: Inicjowanie obsługi administracyjnej, Nieudostępniane inicjowanie obsługi administracyjnej, Inicjowanie obsługi administracyjnej nie powiodło się i Udostępnianie obsługi administracyjnej wkrótce.

Możesz wyświetlić wszystkie komputery w chmurze i ich stan inicjowania obsługi na liście poniżej paska adnotacji. Podano następujące informacje:

- **Nazwa komputera w chmurze:** Nazwa przypisana do komputera w chmurze.
- **Dzierżawa:** Dzierżawa klienta, w której aprowizowana była usługa Cloud PC.
- **Nazwa urządzenia:** Intune — nazwa identyfikator unikatowy dla komputera w chmurze.
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

Aby wyświetlić pełną listę stanu inicjowania obsługi komputera w chmurze i ich znaczenie, zobacz Omówienie zarządzania [](/windows-365/enterprise/device-management-overview#column-details) urządzeniami dla komputerów w chmurze w bibliotece Windows 365 dokumentacji.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Windows 365 Wszystkie komputery w chmurze." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Karta Połączenia sieciowe platformy Azure

Na karcie Połączenia sieciowe platformy Azure na kolorowym pasku adnotacji jest wyświetlana łączna liczba połączeń sieciowych platformy Azure we wszystkich dzierżawach klientów o następujących stanie: Pomyślne połączenia i Połączenia nieudane.

Na liście poniżej paska adnotacji można wyświetlić wszystkie połączenia sieciowe platformy Azure i ich stan połączenia.

Aby wyświetlić połączenia z określonym stanem inicjowania obsługi, wybierz ten stan na pasku adnotacji z adnotacjami, aby przefiltrować listę. Aby wyświetlić stan połączenia dla jednej lub większej liczby dzierżaw klientów, użyj menu rozwijanego  Dzierżawy, aby przefiltrować listę.

Jeśli musisz podjąć działania lub rozwiązać problemy z połączeniem na liście, wybierz pozycję **Wyświetl szczegóły połączenia** w Microsoft Endpoint Manager.

Karta Połączenia sieciowe platformy Azure zawiera również następujące opcje:

- **Odświeżanie:** Zaznacz, aby pobrać najnowsze dane połączenia.
- **Eksportowanie:** Zaznacz, aby wyeksportować dane połączenia Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone połączenie.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Połączenia sieciowe platformy Azure." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Zawartość pokrewna

[Co to jest Windows 365?](/windows-365/overview) (artykuł)\
[Windows 365 omówienie zarządzania urządzeniami na komputerach w](/windows-365/enterprise/device-management-overview) chmurze (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)