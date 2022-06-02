---
title: Optymalizowanie i poprawianie zasad zabezpieczeń za pomocą analizatora konfiguracji
description: Kroki optymalizowania i poprawiania zasad zabezpieczeń za pomocą analizatora konfiguracji. Analizator konfiguracji to centralna lokalizacja i pojedyncze okienko szkła do administrowania i wyświetlania zasad zabezpieczeń poczty e-mail skonfigurowanych w dzierżawie.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: dcb40c0abd619291da2f05fdfa362c03f853181e
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842546"
---
# <a name="optimize-and-correct-security-policies-with-configuration-analyzer"></a>Optymalizowanie i poprawianie zasad zabezpieczeń za pomocą analizatora konfiguracji

Analizator konfiguracji to centralna lokalizacja i pojedyncze okienko szkła do administrowania i wyświetlania zasad zabezpieczeń poczty e-mail skonfigurowanych w dzierżawie. Możesz przeprowadzić bezpośrednie porównanie ustawień z naszymi zalecanymi ustawieniami standardowymi i ścisłymi, zastosować zalecenia i wyświetlić historyczne zmiany, które wpłynęły na Twoją postawę.

## <a name="what-youll-need"></a>Co będzie potrzebne
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1
- Wystarczające uprawnienia (rola administratora zabezpieczeń)
- 5 minut na wykonanie poniższych kroków.

## <a name="compare-settings-and-apply-recommendations"></a>Porównanie ustawień i stosowanie zaleceń
1. Przejdź do obszaru [https://security.microsoft.com/configurationAnalyzer](https://security.microsoft.com/configurationAnalyzer).
1. Wybierz **pozycję Rekomendacje standardowe** lub **Zalecenia ścisłe** z górnego menu w oparciu o porównanie równoległe, które chcesz utworzyć.
1. Rekomendacje zmiany zasad zostaną wyświetlone. (Jeśli dotyczy)
1. Następnie możesz wybrać zalecenie, zanotować zalecaną akcję, zasady, do których ma zastosowanie zalecenie, nazwę ustawienia & bieżącej konfiguracji itp.
1. Po wybraniu rekomendacji możesz nacisnąć **pozycję Zastosuj zalecenie** , a następnie **przycisk OK** w wyświetlonym komunikacie potwierdzenia.
1. Jeśli chcesz ręcznie edytować zasady lub potwierdzić ustawienia bezpośrednio w ramach zasad, możesz nacisnąć przycisk **Wyświetl zasady** zamiast **pozycji Zastosuj zalecenie** , które załaduje nową kartę i ułatwi ci bezpośrednie wprowadzenie do odpowiednich zasad.

## <a name="view-historical-configuration-changes"></a>Wyświetlanie historycznych zmian konfiguracji

W **analizatorze konfiguracji** możesz wybrać pozycję **Analiza dryfu konfiguracji i historia** z górnego paska menu.

Na stronie, która zostanie załadowana, zostaną wyświetlone modyfikacje zasad zabezpieczeń w przedziale czasu wybranym przez filtry wraz z danymi o zmianie oraz w przypadku zwiększenia lub zmniejszenia ogólnej postawy.

Aby dowiedzieć się więcej o analizatorze konfiguracji, zobacz [Analizator konfiguracji dla zasad zabezpieczeń — Office 365 | Microsoft Docs](../../office-365-security/configuration-analyzer-for-security-policies.md).
