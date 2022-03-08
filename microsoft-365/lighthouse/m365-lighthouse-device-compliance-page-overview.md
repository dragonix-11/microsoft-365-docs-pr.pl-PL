---
title: omówienie Microsoft 365 Lighthouse zgodności urządzenia
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się więcej o stronie Zgodność urządzenia.
ms.openlocfilehash: 76cb914b878b3da8236e91ddda538cb13fa3aa8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317601"
---
# <a name="microsoft-365-lighthouse-device-compliance-page-overview"></a>omówienie Microsoft 365 Lighthouse zgodności urządzenia

Microsoft 365 Lighthouse umożliwia wyświetlanie szczegółowych informacji dotyczących zgodności urządzeń z usługą Intune dla wszystkich dzierżaw klientów, wybierając pozycję Urządzenia w lewym okienku  nawigacji, aby otworzyć stronę Zgodność urządzenia. Na tej stronie możesz uzyskać przegląd stanu zgodności w dzierżawach, wyświetlić listę urządzeń dla poszczególnych dzierżaw i uzyskać raporty o stanie dotyczące zasad i ustawień zgodności.

## <a name="overview-tab"></a>Karta Omówienie  
  
Na karcie Omówienie możesz wyświetlić stan zgodności urządzeń w dzierżawach, miesięczne trendy zgodności urządzeń i śledzić, czy do urządzeń są przypisane zasady zgodności. Możesz również sprawdzić, w ilu dzierżawach nie są wymuszane żadne wymagania dotyczące zgodności urządzeń przy użyciu zasad dostępu warunkowego. Możesz wybrać pozycję **Wyświetl więcej,** aby wyświetlić więcej szczegółów.

Aby uzyskać szczegółowe informacje o zgodności urządzeń dla określonej dzierżawy klienta, wybierz wartość w dowolnej z kolumn stanu dla tej dzierżawy. Spowoduje to otwarcie karty Urządzenia, aby można było wyświetlić szczegóły dotyczące zgodności urządzeń dla wybranej dzierżawy.

Aby wyeksportować dane zgodności urządzenia do pliku Excel wartości rozdzielanych przecinkami (.csv), wybierz pozycję **Eksportuj**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Przegląd." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Karta Urządzenia

Na karcie Urządzenia kolorowy pasek adnotacji z adnotacjami zawiera łączną liczbę urządzeń we wszystkich dzierżawach klientów, które mają następujące stany zgodności: Zgodne, Niezgodne, W okresie prolongaty i Nieoceniowa. Aby uzyskać więcej informacji o różnych stanach zgodności, zobacz [Monitorowanie zasad zgodności urządzeń w usłudze Intune](/mem/intune/protect/compliance-policy-monitor).

Aby sprawdzić, które dzierżawy mają urządzenia o określonym stanie zgodności, wybierz ten stan na pasku adnotacji, aby przefiltrować listę. Aby wyświetlić stan zgodności urządzeń dla jednej lub większej liczby dzierżaw klientów, użyj menu rozwijanego  Dzierżawy, aby przefiltrować listę.

Wybierz dowolną nazwę urządzenia na liście, aby wyświetlić więcej szczegółowych informacji o bieżącym stanie zgodności tego urządzenia. Możesz zsynchronizować lub ponownie uruchomić urządzenie albo wybrać pozycję Wyświetl urządzenie w aplikacji **Microsoft Endpoint Manager**, jeśli chcesz rozwiązać problem lub podjąć dalsze działania.

> [!NOTE]
> Po ponownym uruchomieniu urządzenia właściciel urządzenia nie jest automatycznie powiadamiany i może utracić niezapisaną pracę. Z tego powodu możesz chcieć powiadomić właściciela urządzenia przed ponownym uruchomieniem urządzenia.

Karta Urządzenia zawiera również następujące opcje:

- **Eksportowanie:** Wybierz, aby wyeksportować dane zgodności urządzenia do Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane dotyczące zgodności urządzenia.
- **Synchronizacja:** Wybierz jedno lub więcej urządzeń z listy o stanie Niezgodne, W okresie prolongaty lub Nieoceniowane, a następnie wybierz tę opcję, aby wymusić, aby te urządzenia zaewidencjonowały się w usłudze Intune i natychmiast otrzymać wszystkie przypisane do nich zasady.
- **Uruchom ponownie:** Wybierz jedno lub więcej urządzeń z listy o stanie Niezgodne, W okresie prolongaty lub Nieoceniowane, a następnie wybierz tę opcję, aby ponownie uruchomić te urządzenia.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć określone urządzenie na liście.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Urządzenia." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Karta Zasady

Na karcie Zasady możesz wyświetlić zasady zgodności urządzeń w dzierżawach i porównać dwie lub trzy zasady tego samego typu platformy przy użyciu opcji **Porównaj** .

Aby zobaczyć zasady dotyczące urządzeń na określonej platformie, użyj menu rozwijanego **systemu operacyjnego** , aby przefiltrować listę. Aby wyświetlić zasady dla jednej lub większej liczby konkretnych dzierżaw klientów, użyj menu  rozwijanego Dzierżawy, aby przefiltrować listę.

Wybierz dowolną nazwę zasad na liście, aby wyświetlić więcej szczegółów dotyczących tych zasad. Jeśli chcesz podjąć działanie lub wyświetlić dodatkowe informacje, wybierz pozycję **Wyświetl te zasady w programie Microsoft Endpoint Manager**.

Karta Zasady zawiera również następujące opcje:

- **Eksportowanie:** Wybierz, aby wyeksportować dane zasad zgodności urządzenia Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane zasad zgodności urządzenia.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć określone zasady zgodności urządzenia na liście.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Zasady." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Ustawienia karcie

Karta Ustawienia udostępnia zagregowany raport o niezgodnych ustawieniach na urządzeniach dzierżawcy. 

Aby wyświetlić niezgodne ustawienia urządzeń na określonej platformie, użyj menu rozwijanego Platforma, aby przefiltrować listę. Aby wyświetlić niezgodne ustawienia dla jednej lub większej liczby dzierżaw klientów, użyj menu rozwijanego Dzierżawy, aby przefiltrować listę.

Wybierz dowolną z niezgodnych nazw ustawień na liście, aby otworzyć okienko, w którym możesz wyświetlić listę dzierżaw, które mają urządzenia z tym określonym ustawieniem niezgodnym. W tym miejscu możesz dodatkowo przejść do szczegółów, wybierając z listy dowolną dzierżawę, aby wyświetlić informacje o urządzeniach w ramach tej dzierżawy, które mają określone niezgodne ustawienie. Możesz również zsynchronizować lub ponownie uruchomić urządzenie albo wybrać pozycję Wyświetl urządzenie w aplikacji **Microsoft Endpoint Manager**, jeśli chcesz rozwiązać problem lub podjąć dalsze działania.

Karta Ustawienia zawiera również następujące opcje:

- **Eksportowanie:** Wybierz opcję eksportowania niezgodnych danych ustawień do Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze niezgodne dane ustawień.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć określone niezgodne ustawienie na liście.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Ustawienia zaawansowanej." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Zawartość pokrewna

[omówienie Windows usługi Windows 365 (komputery w chmurze)](m365-lighthouse-win365-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
