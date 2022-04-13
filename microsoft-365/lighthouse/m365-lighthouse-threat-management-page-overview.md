---
title: Omówienie strony zarządzania zagrożeniami Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zapoznaj się ze stroną Zarządzanie zagrożeniami.
ms.openlocfilehash: 94e71d648dac3a285ecef81b4dae29305cf7e98c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823173"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>Omówienie strony zarządzania zagrożeniami Microsoft 365 Lighthouse 

**Dotyczy:**

- Windows 10

Program antywirusowy Microsoft Defender chroni dzierżawców, użytkowników i urządzenia przed zagrożeniami oprogramowania, w tym wirusami, złośliwym oprogramowaniem i programami szpiegującymi. Jest to niezawodna, ciągła ochrona wbudowana w Windows 10 i dołączona do Microsoft 365 Business Premium i Microsoft365E3&nbsp;&nbsp;.  
  
Aby uzyskać dostęp do strony Zarządzanie zagrożeniami w Microsoft 365 Lighthouse, wybierz pozycję **Zarządzanie zagrożeniami** w okienku nawigacji po lewej stronie, aby wyświetlić stan zabezpieczeń dzierżaw klientów przed zagrożeniami. Zobaczysz dzierżawy, użytkowników i urządzenia, które wymagają uwagi i zaleceń, które pomogą Ci zmniejszyć ryzyko.  
  
## <a name="overview-tab"></a>Karta Przegląd  
  
Na karcie Przegląd na stronie Zarządzanie zagrożeniami możesz monitorować stan oprogramowania antywirusowego we wszystkich dzierżawach, aby zidentyfikować obszary wymagające uwagi.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Przegląd.":::

## <a name="threats-tab"></a>Karta Zagrożenia

Na karcie Zagrożenia na stronie Zarządzanie zagrożeniami można zobaczyć zagrożenia aktywne, zminimalizowane, rozwiązane i dozwolone we wszystkich dzierżawach. Możesz również korygować wiele zagrożeń w tym samym czasie we wszystkich dzierżawach, filtrując i przechodząc do szczegółów każdego zagrożenia, aby dowiedzieć się, które urządzenia, użytkownicy lub dzierżawcy mają wpływ.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Zrzut ekranu przedstawiający domyślną stronę punktu odniesienia.":::
  
Zagrożenia można filtrować według:

- Stan zagrożenia
- Ważność zagrożenia
- Typ zagrożenia
- Zakres dat

W poniższej tabeli wymieniono różne stany zagrożenia i ich definicję:<br><br>

| Stan zagrożenia | Definicja |
|---|---|
| Aktywny | Zagrożenie jest aktywne na urządzeniu. |
| Brak stanu | Stan zagrożenia jest niedostępny. Uruchom pełne skanowanie na urządzeniu, aby Program antywirusowy Microsoft Defender ponownie wykryć zagrożenie. |
| Akcja nie powiodła się | Urządzenie nie jest zagrożone. Akcja nie powiodła się, ale potencjalne zagrożenie zostało zatrzymane i nie jest aktywne na urządzeniu. Uruchom pełne skanowanie na urządzeniu. |
| Wymagane czynności ręczne | Zagrożenie zostało zatrzymane, ale wymaga ręcznego wykonania kroku, takiego jak pełne skanowanie lub ponowne uruchomienie urządzenia. |
| Wymagane pełne skanowanie | Wymagane jest pełne skanowanie urządzenia. |
| Wymagane ponowne uruchomienie | Wymagane jest ponowne uruchomienie urządzenia. |
| Korygowane z błędami niekrytywowymi | Zagrożenie zostało skorygowane i nie są potrzebne żadne dalsze działania. |
| Kwarantannie | Zagrożenie zostało poddane kwarantannie. Nie są potrzebne żadne dalsze akcje. |
| Usunięte | Zagrożenie zostało pomyślnie usunięte z urządzenia. Nie są potrzebne żadne dalsze akcje. |
| Czyszczone | Program antywirusowy Microsoft Defender odzyskał i zdezynfekował pliki. Nie są potrzebne żadne dalsze akcje. |
| Dozwolone | Administrator może pozostać na urządzeniu. | 

## <a name="antivirus-protection-tab"></a>Karta Ochrona antywirusowa

Karta Ochrona antywirusowa na stronie Zarządzanie zagrożeniami pokazuje urządzenia we wszystkich dzierżawach i ich stan ochrony Program antywirusowy Microsoft Defender. Możesz ocenić stan i podjąć działania dla co najmniej jednego urządzenia, które może być narażone. Możesz również wybrać urządzenie, aby wyświetlić więcej informacji, takich jak Omówienie urządzenia, Bieżące zagrożenia i Stan akcji urządzenia.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Program antywirusowy.":::

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse punktów odniesienia](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
