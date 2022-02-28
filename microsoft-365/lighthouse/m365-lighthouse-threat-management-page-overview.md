---
title: Microsoft 365 Lighthouse zarządzania zagrożeniami — omówienie
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się więcej o stronie Zarządzanie zagrożeniami.
ms.openlocfilehash: 6eb5ed0c37295a7683b2eb16068f96f912aefb91
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984448"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>Microsoft 365 Lighthouse zarządzania zagrożeniami — omówienie 

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

**Dotyczy:**

- Windows 10

Program antywirusowy Microsoft Defender chroni dzierżawców, użytkowników i urządzenia przed zagrożeniami oprogramowania, w tym wirusami, złośliwym oprogramowaniem i programami szpiegującymi. Jest to niezawodna, niezawodna ochrona wbudowana w Windows 10 i dołączona do aplikacji Microsoft 365 Business Premium i Microsoft365E3&nbsp;&nbsp;.  
  
Aby uzyskać dostęp do strony Zarządzanie zagrożeniami w programie Microsoft 365 Lighthouse,  wybierz pozycję Zarządzanie zagrożeniami w okienku nawigacji po lewej stronie w celu wyświetlenia informacji o stanie zabezpieczeń dzierżaw klientów przed zagrożeniami. Zobaczysz dzierżawy, użytkowników i urządzenia wymagające Twojej uwagi i rekomendacji, które pomogą zmniejszyć ryzyko.  
  
## <a name="overview-tab"></a>Karta Omówienie  
  
Na karcie Omówienie na stronie Zarządzanie zagrożeniami możesz monitorować stan oprogramowania antywirusowego we wszystkich dzierżawach, aby zidentyfikować obszary, na które należy zwrócić uwagę.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Przegląd.>.":::

## <a name="threats-tab"></a>Karta Zagrożenia

Na karcie Zagrożenia na stronie Zarządzanie zagrożeniami widać zagrożenia Aktywne, Zminimalizowane, Rozwiązane i Dozwolone we wszystkich dzierżawach. Możesz również rozwiązać wiele zagrożeń jednocześnie we wszystkich dzierżawach, filtrując i uwzględniając wszystkie zagrożenia, aby dowiedzieć się, których urządzeń, użytkowników lub dzierżaw dotyczy problem.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Zrzut ekranu przedstawiający stronę Domyślny plan bazowy.>.":::
  
Możesz filtrować zagrożenia, korzystając z tych filtrów:

- Stan zagrożenia
- Zagrożenia zagrożenia
- Typ zagrożenia
- Zakres dat

W poniższej tabeli wymieniono różne statusy zagrożeń i ich definicje:<br><br>

| Stan zagrożenia | Definicja |
|--|--|
| Aktywny | Zagrożenie jest aktywne na urządzeniu. |
| Brak stanu | Stan zagrożeń jest niedostępny. Uruchom pełne skanowanie na urządzeniu, aby Program antywirusowy Microsoft Defender ponownie wychylić zagrożenie. |
| Akcja nie powiodła się | Urządzenie nie jest zagrożenia. Akcja zakończyła się niepowodzeniem, ale potencjalne zagrożenie zostało zatrzymane i nie jest aktywne na urządzeniu. Uruchom pełne skanowanie na urządzeniu. |
| Wymagane ręczne kroki | Zagrożenie zostało zatrzymane, ale wymaga ręcznego ukończenia kroku, na przykład pełnego skanowania lub ponownego uruchomienia urządzenia. |
| Wymagane pełne skanowanie | Wymagane jest pełne skanowanie urządzenia. |
| Wymagane ponowne uruchomienie | Wymagane jest ponowne uruchomienie urządzenia. |
| Działania naprawcze w przypadku niepowodzeń niekrytyczych | Zagrożenie zostało usunięte i nie są wymagane żadne dalsze działania. |
| Kwarantanna | Zagrożenie zostało poddane kwarantannie. Nie są wymagane żadne dalsze działania. |
| Usunięto | Zagrożenie zostało pomyślnie usunięte z urządzenia. Nie są wymagane żadne dalsze działania. |
| Wyczyszczone | Program antywirusowy Microsoft Defender odzyskane i odzyskane pliki. Nie są wymagane żadne dalsze działania. |
| Dozwolone | Administrator zezwolił na pozostanie na urządzeniu. | 

## <a name="antivirus-protection-tab"></a>Karta Ochrona antywirusowa

Karta Ochrona antywirusowa na stronie Zarządzanie zagrożeniami zawiera urządzenia dla wszystkich dzierżawców i ich Program antywirusowy Microsoft Defender stan ochrony. Możesz ocenić stan i podjąć działania dotyczące jednego lub większej liczby urządzeń, które mogą być narażone na zagrożenia. Możesz także wybrać urządzenie, aby wyświetlić więcej informacji, takich jak Przegląd urządzenia, Bieżące zagrożenia i Stan akcji urządzenia.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Oprogramowanie antywirusowe.":::

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse bazowych](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
