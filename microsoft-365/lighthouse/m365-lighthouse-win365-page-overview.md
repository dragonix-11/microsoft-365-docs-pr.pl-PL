---
title: Omówienie strony Windows 365 (komputery w chmurze) w Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zapoznaj się ze stroną Windows 365 (komputery w chmurze).
ms.openlocfilehash: 325fe39c144227052c966b81a8a2109a07fb0cf2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100286"
---
# <a name="overview-of-the-windows-365-cloud-pcs-page-in-microsoft-365-lighthouse"></a>Omówienie strony Windows 365 (komputery w chmurze) w Microsoft 365 Lighthouse  
  
Windows 365 to usługa oparta na chmurze, która umożliwia administratorom Microsoft Endpoint Manager (MEM) aprowizowanie komputerów w chmurze i zarządzanie nimi dla użytkowników, którzy mają licencję Windows 365. Windows 365 jest w pełni zintegrowana z rozwiązaniem MEM do zarządzania urządzeniami oraz z Microsoft 365 Lighthouse do zarządzania przez partnerów komputerami w chmurze we wszystkich dzierżawach klientów.

Aby uzyskać więcej informacji na temat Windows 365, zobacz [Co to jest Windows 365?](/windows-365/overview) Aby uzyskać listę wymagań Windows 365, zobacz [Wymagania dotyczące Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Przed rozpoczęciem zarządzania nimi w usłudze Lighthouse musisz przejść do usługi [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) , aby aprowizować komputery w chmurze dla każdej dzierżawy klienta. Nie można aprowizować z poziomu usługi Lighthouse.

Po zainicjowaniu obsługi administracyjnej komputerów w chmurze dla dzierżawy klienta karta Windows 365 na stronie głównej Microsoft 365 zawiera krótki alert dotyczący komputerów w chmurze wymagających akcji, takich jak liczba komputerów w chmurze, których nie można aprowizować, i błędy połączeń sieciowych platformy Azure. Aby uzyskać szczegółowy stan, wybierz przycisk na karcie Windows 365 (lub wybierz **pozycję Windows 365** w okienku nawigacji po lewej stronie), aby otworzyć stronę Windows 365. Na tej stronie można uzyskać przegląd stanu komputerów w chmurze przypisanych do dzierżaw klientów, wyświetlić listę wszystkich zarządzanych komputerów w chmurze i dzierżaw, do których są przypisani, oraz wyświetlić połączenia sieciowe platformy Azure między dzierżawami klientów i Azure Active Directory (Azure AD) oraz ich stan.

## <a name="overview-tab"></a>Karta Przegląd

Na karcie Przegląd kolorowy pasek z adnotacją liczbową wyświetla całkowitą liczbę komputerów w chmurze lub połączeń sieciowych platformy Azure we wszystkich dzierżawach klientów, które mają następujące stany: Nieudane połączenia sieciowe, Nie zainicjowano obsługi administracyjnej, Aprowizowanie nie powiodło się i wkrótce anulowano aprowizację.

Na liście poniżej paska adnotacji można zobaczyć podział stanów komputerów w chmurze dla każdej dzierżawy klienta. Aby sprawdzić, które dzierżawy mają komputery w chmurze o określonym stanie, wybierz ten stan na pasku zliczanie adnotacji, aby odfiltrować listę. Aby wyświetlić stan komputera w chmurze dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Aby uzyskać szczegółowe informacje o stanie dla określonej dzierżawy klienta, wybierz wartość w dowolnej kolumnie stanu dla tej dzierżawy. W zależności od kolumny, w której znajduje się wartość, otworzy się karta **Połączenia sieciowe platformy Azure** lub **Wszystkie komputery w chmurze** i wyświetli więcej informacji.

Karta Przegląd zawiera również następujące opcje:

- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane komputera w chmurze.
- **Eksportu:** Wybierz, aby wyeksportować dane komputera w chmurze do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określony komputer w chmurze na liście.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Przegląd Windows 365." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Karta Wszystkie komputery w chmurze

Na karcie Wszystkie komputery w chmurze na kolorowym pasku adnotacji liczbowej jest wyświetlana całkowita liczba komputerów w chmurze we wszystkich dzierżawach klientów, które mają następujące stany: Aprowizowano, Nie zainicjowano obsługi administracyjnej, aprowizowanie nie powiodło się i wkrótce anulowano aprowizację.

Wszystkie komputery w chmurze i ich stan aprowizacji można wyświetlić na liście poniżej paska adnotacji. Podano następujące informacje:

- **Nazwa komputera w chmurze:** Nazwa przypisana do komputera w chmurze.
- **Użytkownika:** Użytkownik, dla którego aprowizowano lub próbowano aprowizować komputer w chmurze.
- **Nazwa urządzenia:** Intune nazwę urządzenia — unikatowy identyfikator komputera w chmurze.
- **Dzierżawy:** Dzierżawa klienta, w której aprowizowane jest komputer w chmurze.
- **Stan:** Stan aprowizacji komputera w chmurze.
- **Typ licencji:** Enterprise lub Business.
- **Specyfikacje:** Konfiguracja sprzętu komputera w chmurze.

Aby sprawdzić, które dzierżawy mają komputery w chmurze o określonym stanie aprowizacji, wybierz ten stan na pasku count-annotation, aby odfiltrować listę. Aby wyświetlić stan aprowizacji komputera w chmurze dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Wybierz dowolny komputer z chmurą na liście, aby wyświetlić więcej szczegółów i wykonać akcje zarządzania, takie jak:
- **Ponownie uruchomić:** Wybierz, aby ponownie uruchomić urządzenie. 
- **Ponowne aprowizowanie:** Wybierz, aby zresetować urządzenie. Zasady aprowizacji można również wyświetlić w linku Microsoft Endpoint Manager.
- **Zmienić nazwę:** Wybierz, aby zmienić nazwę urządzenia przypisanego do użytkownika.

Karta Wszystkie komputery w chmurze zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane komputera w chmurze do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane komputera w chmurze.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określony komputer w chmurze na liście.

Aby wyświetlić pełną listę stanów aprowizacji komputerów w chmurze i ich znaczenie, zobacz [Omówienie zarządzania urządzeniami dla komputerów w chmurze](/windows-365/enterprise/device-management-overview#column-details) w bibliotece dokumentacji Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Windows 365 Wszystkie komputery w chmurze." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Karta Połączenia sieciowe platformy Azure

Na karcie Połączenia sieciowe platformy Azure na kolorowym pasku adnotacji liczbowej jest wyświetlana całkowita liczba połączeń sieciowych platformy Azure we wszystkich dzierżawach klientów, którzy mają Windows 365 Enterprise komputery w chmurze i mogą mieć następujące stany: Pomyślne połączenia i Nieudane połączenia.

Na liście poniżej paska zliczanie adnotacji można wyświetlić wszystkie połączenia sieciowe platformy Azure i ich stan połączenia.

Aby wyświetlić połączenia z określonym stanem aprowizacji, wybierz ten stan na pasku zliczanie adnotacji, aby filtrować listę. Aby wyświetlić stan połączenia dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Jeśli musisz podjąć działania lub rozwiązać problemy z połączeniem na liście, wybierz pozycję **Wyświetl szczegóły połączenia w Microsoft Endpoint Manager**.

Karta Połączenia sieciowe platformy Azure zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane połączenia do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane połączenia.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone połączenie.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Połączenia sieciowe platformy Azure." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Zawartość pokrewna

[Co to jest Windows 365?](/windows-365/overview) (artykuł)\
[Windows 365 omówienie zarządzania urządzeniami dla komputerów w chmurze](/windows-365/enterprise/device-management-overview) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)