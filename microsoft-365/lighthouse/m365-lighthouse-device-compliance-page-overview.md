---
title: Omówienie strony Zgodność urządzeń w Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zapoznaj się ze stroną Zgodność urządzeń.
ms.openlocfilehash: 1d00df09231863dd2d7d110dbf9d3c2600f464dc
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017837"
---
# <a name="overview-of-the-device-compliance-page-in-microsoft-365-lighthouse"></a>Omówienie strony Zgodność urządzeń w Microsoft 365 Lighthouse

Microsoft 365 Lighthouse umożliwia wyświetlanie szczegółowych informacji i informacji związanych ze zgodnością Intune urządzeniami dla wszystkich dzierżaw klientów, wybierając pozycję **Urządzenia** w okienku nawigacji po lewej stronie, aby otworzyć stronę Zgodność urządzenia. Na tej stronie można uzyskać przegląd stanu zgodności między dzierżawami, wyświetlić listę urządzeń dla każdej dzierżawy i uzyskać raporty o stanie dotyczące zasad i ustawień zgodności.

## <a name="overview-tab"></a>Karta Przegląd  
  
Na karcie Przegląd możesz wyświetlać stan zgodności urządzeń w dzierżawach, wyświetlać comiesięczne trendy zgodności urządzeń i śledzić, czy urządzenia mają przypisane zasady zgodności. Możesz również zobaczyć, ile dzierżaw nie ma żadnych wymagań dotyczących zgodności urządzeń wymuszanych przy użyciu zasad dostępu warunkowego. Możesz wybrać pozycję **Wyświetl więcej** , aby wyświetlić więcej szczegółów.

Aby uzyskać szczegółowe informacje o zgodności urządzeń dla określonej dzierżawy klienta, wybierz wartość w dowolnej kolumnie stanu dla tej dzierżawy. Spowoduje to otwarcie karty Urządzenia, aby można było wyświetlić szczegóły zgodności urządzeń dla wybranej dzierżawy.

Aby wyeksportować dane zgodności urządzeń do pliku wartości rozdzielanych Excel przecinkami (.csv), wybierz pozycję **Eksportuj**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Przegląd." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Karta Urządzenia

Na karcie Urządzenia na kolorowym pasku adnotacji liczbowej jest wyświetlana całkowita liczba urządzeń we wszystkich dzierżawach klientów, które mają następujące stany zgodności: Zgodne, Niezgodne, W okresie prolongaty i Nie oceniono. Aby uzyskać więcej informacji na temat różnych stanów zgodności, zobacz [Monitorowanie zasad zgodności urządzeń Intune](/mem/intune/protect/compliance-policy-monitor).

Aby sprawdzić, które dzierżawy mają urządzenia o określonym stanie zgodności, wybierz ten stan na pasku count-annotation, aby odfiltrować listę. Aby wyświetlić stan zgodności urządzeń dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Wybierz dowolną nazwę urządzenia na liście, aby wyświetlić więcej szczegółów dotyczących bieżącego stanu zgodności tego urządzenia. Możesz zsynchronizować lub ponownie uruchomić urządzenie lub wybrać pozycję **Wyświetl urządzenie w Microsoft Endpoint Manager**, jeśli chcesz rozwiązać problemy lub podjąć dalsze działania.

> [!NOTE]
> Po ponownym uruchomieniu urządzenia właściciel urządzenia nie jest automatycznie powiadamiany i może utracić niezapisaną pracę. Z tego powodu może być konieczne powiadomienie właściciela urządzenia przed ponownym uruchomieniem urządzenia.

Karta Urządzenia zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane zgodności urządzeń do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane zgodności urządzeń.
- **Synchronizacji:** Wybierz co najmniej jedno urządzenie z listy ze stanem Niezgodne, W okresie prolongaty lub Nie oceniono, a następnie wybierz tę opcję, aby wymusić na tych urządzeniach zaewidencjonowanie przy użyciu Intune i natychmiastowe odebranie wszelkich zasad, które zostały do nich przypisane.
- **Ponownie uruchomić:** Wybierz z listy co najmniej jedno urządzenie ze stanem Niezgodne, W okresie prolongaty lub Nie oceniono, a następnie wybierz tę opcję, aby ponownie uruchomić te urządzenia.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone urządzenie na liście.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Urządzenia." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Karta Zasady

Na karcie Zasady możesz wyświetlić zasady zgodności urządzeń w dzierżawach i porównać dwie lub trzy zasady tego samego typu platformy przy użyciu opcji **Porównaj** .

Aby wyświetlić zasady dotyczące urządzeń na określonej platformie, użyj menu rozwijanego **systemu operacyjnego** , aby odfiltrować listę. Aby wyświetlić zasady dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Wybierz dowolną nazwę zasad na liście, aby wyświetlić więcej szczegółów dotyczących tych zasad. Jeśli musisz podjąć akcję lub wyświetlić dodatkowe informacje, wybierz pozycję **Wyświetl te zasady w Microsoft Endpoint Manager**.

Karta Zasady zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane zasad zgodności urządzeń do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane zasad zgodności urządzeń.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone zasady zgodności urządzeń na liście.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Zasady." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>karta Ustawienia

Karta Ustawienia zawiera zagregowany raport o niezgodnych ustawieniach na urządzeniach dzierżawy. 

Aby wyświetlić niezgodne ustawienia dla urządzeń na określonej platformie, użyj menu rozwijanego **Platforma** , aby odfiltrować listę. Aby wyświetlić niezgodne ustawienia dla co najmniej jednej konkretnej dzierżawy klienta, użyj menu rozwijanego **Dzierżawy** , aby odfiltrować listę.

Wybierz dowolną niezgodną nazwę ustawienia na liście, aby otworzyć okienko, w którym można wyświetlić listę dzierżaw, które mają urządzenia z tym konkretnym niezgodnym ustawieniem. W tym miejscu możesz przejść do szczegółów, wybierając dowolną dzierżawę z listy, aby wyświetlić informacje o urządzeniach w tej dzierżawie, które mają określone niezgodne ustawienie. Możesz również zsynchronizować lub ponownie uruchomić urządzenie lub wybrać pozycję **Wyświetl urządzenie w Microsoft Endpoint Manager**, jeśli chcesz rozwiązać problemy lub podjąć dalsze działania.

Karta Ustawienia zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować niezgodne dane ustawień do pliku wartości rozdzielanych przecinkami Excel (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne niezgodne dane ustawień.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określone niezgodne ustawienie na liście.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Ustawienia." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie strony Windows 365 (komputery w chmurze) w Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
