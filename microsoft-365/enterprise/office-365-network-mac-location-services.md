---
title: Microsoft 365 lokalizacji łączności sieciowej
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
description: Microsoft 365 lokalizacji łączności sieciowej
ms.openlocfilehash: 6150102471b03fbc83be09b503a6969ca6615a87
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996411"
---
# <a name="microsoft-365-network-connectivity-location-services"></a>Microsoft 365 lokalizacji łączności sieciowej

W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> teraz przedstawiono zalecenia dotyczące **Szczegółowe informacje** wydajności i sieci, czyli metryki wydajności na żywo zbierane z twojej Microsoft 365 dzierżawy. Te metryki mogą być przeglądane tylko przez użytkowników administracyjnych w Twojej dzierżawie. Łączność sieciowa organizacji jest zaprojektowana dla procesów z różnych lokalizacji biurowych za pośrednictwem lokalizacji ruchu wychodzącego do Internetu. Microsoft 365 klienta używa tej trasy, a następnie przez Internet do serwerów frontonie usług firmy Microsoft. Identyfikowanie lokalizacji biur jest kluczem do pokazywania tych szczegółowych informacji sieciowych.

## <a name="location-in-network-measurements"></a>Lokalizacja w pomiarach sieci

Administrator organizacji może wybrać lokalizację do uwzględnionia w pomiarach sieciowych używanych przez tę funkcję. Umożliwia to automatyczne odnajdowanie miasta, w którym znajduje się poszczególne biura. Informacje o lokalizacji nie są dokładne i są podzielone na 300 m i podzielone na kategorie według miast. W momencie przechwytywania lokalizacji na urządzeniu Windows na pasku narzędzi będzie wyświetlana ikona Lokalizacja w użyciu. Administratorzy mogą chcieć powiadomić użytkowników o wyglądzie tej ikony. W przypadku tego przetwarzania lokalizacja jest traktowana jak lokalizacja biura organizacji, a nie lokalizacja osoby lub urządzenia. Szczegółowe informacje o sieci można wyświetlać w tych lokalizacjach biurowych. Aby uzyskać większą dokładność zaleceń, możesz wprowadzić określone adresy lokalizacji biura. Szczegółowe informacje o sieci zostaną zagregowane z tych lokalizacji. Office lokalizacji nie mogą być agregowane bardziej niż 300 metrów.

## <a name="location-in-the-microsoft-365-admin-center"></a>Lokalizacja w centrum Administracja Microsoft 365 sieci Administracja Microsoft 365.

W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 Bing</a> map są używane do pokazywania lokalizacji biur organizacji. Kontrolki pokazują również topologię obwodu sieci dla wybranej lokalizacji biura. Gdy administrator dodaje określone szczegóły adresu dla lokalizacji biura, za Mapy Bing są też sugerowane adresy w celu ułatwienia wprowadzania danych.

## <a name="terms-of-use"></a>Regulamin użytkowania

Każda zawartość dostarczana za pośrednictwem Mapy Bing, w tym kody  geokodów, może być używana tylko w obrębie produktu, za pośrednictwem którego jest dostarczana zawartość. Korzystanie przez klienta z funkcji usług <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> centrum administracyjne platformy Microsoft 365 lokalizacji, obsługiwanej przez firmę Mapy Bing, podlega regulaminom użytkowania usługi _Mapy Bing End-User_ <https://go.microsoft.com/?linkid=9710837> dostępnym na stronie i Oświadczeniu o ochronie prywatności firmy [Microsoft](https://go.microsoft.com/fwlink/?LinkID=248686).

Ta funkcja, dostępna za pośrednictwem Mapy Bing, jest również obsługiwana przez firmę **TomTom**. Więcej informacji o produktach i usługach firmy TomTom można znaleźć w .[https://www.tomtom.com/legal](https://www.tomtom.com/legal)

## <a name="related-topics"></a>Tematy pokrewne

[Łączność sieciowa w Administracja Microsoft 365 center](office-365-network-mac-perf-overview.md)

[Microsoft 365 informacji o wydajności sieci](office-365-network-mac-perf-insights.md)

[Microsoft 365 oceny sieci](office-365-network-mac-perf-score.md)

[Microsoft 365 test łączności w centrum administracyjne platformy Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)
