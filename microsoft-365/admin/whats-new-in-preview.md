---
title: Co nowego w Centrum administracyjne platformy Microsoft 365?
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- MET150
- MOE150
- FRP150
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
- admindeeplinkMAC
description: Centrum administracyjne platformy Microsoft 365 — informacje o funkcjach, które zostały dodane w tym miesiącu.
ms.openlocfilehash: 198832f09f6b219579f128b7104ecf3ae2fa3446
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679357"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Co nowego w Centrum administracyjne platformy Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Niektóre informacje zawarte w tym artykule mogą nie dotyczyć Office 365 obsługiwanych przez firmę 21Vianet.

::: moniker-end

Ciągle dodajemy nowe funkcje do [Centrum administracyjne platformy Microsoft 365](Omówienie Centrum administracyjne platformy Microsoft 365](admin-overview/admin-center-overview.md), naprawiamy problemy, o których się dowiadujemy, i wprowadzamy zmiany na podstawie Opinii. Niektóre funkcje są wdrażane z różnymi prędkościami dla naszych klientów. Jeśli nie widzisz jeszcze funkcji, [spróbuj dodać siebie do docelowej wersji](manage/release-options-in-office-365.md).

A jeśli chcesz wiedzieć, co nowego w innych usługach w chmurze firmy Microsoft:

- [Co nowego w Azure Active Directory](/azure/active-directory/fundamentals/whats-new)
- [Co nowego w centrum administracyjnym Exchange](/Exchange/whats-new)
- [Co nowego w Microsoft Intune](/mem/intune/fundamentals/whats-new)
- [Co nowego w portal zgodności Microsoft Purview](/Office365/SecurityCompliance/whats-new)
- [Co nowego w usłudze Microsoft 365 Defender](../security/mtp/whats-new.md)
- [Co nowego w centrum administracyjnym SharePoint](/sharepoint/what-s-new-in-admin-center)
- [aktualizacje Office](/OfficeUpdates/)
- [Jak sprawdzić kondycję wersji Windows](/windows/deployment/update/check-release-health)

## <a name="may-2022"></a>Maj 2022 r.

### <a name="role-based-access-controls-rbac"></a>Kontrola dostępu oparta na rolach (RBAC)

W Centrum administracyjne platformy Microsoft 365 istnieją cztery nowe role do zarządzania niestandardowymi atrybutami zabezpieczeń. Te role są dostępne dla wszystkich użytkowników w Centrum administracyjne platformy Microsoft 365 w obszarze **Role**.

- **Administrator przypisań atrybutów**   Przypisz niestandardowe klucze atrybutów zabezpieczeń i wartości do obsługiwanych obiektów Azure AD.

- **Czytelnik przypisań atrybutów**   Odczytuje niestandardowe klucze atrybutów zabezpieczeń i wartości dla obsługiwanych obiektów Azure AD.

- **Administrator definicji atrybutów**   Definiowanie definicji niestandardowych atrybutów zabezpieczeń i zarządzanie nimi.

- **Czytelnik definicji atrybutów**   Odczytuje definicję niestandardowych atrybutów zabezpieczeń.

Istnieje również nowa rola, która umożliwia administratorom dostęp potrzebny tylko do zarządzania wizytami wirtualnymi.

- **Administrator wizyt wirtualnych**   Zarządzaj informacjami i metrykami wizyt wirtualnych oraz udostępniaj je z centrów administracyjnych lub aplikacji Wizyty wirtualne.

Aby uzyskać więcej informacji na temat tych ról, zobacz [Azure AD role wbudowane](/azure/active-directory/roles/permissions-reference).

### <a name="quick-assist"></a>Szybka pomoc

Przenieśliśmy Szybka pomoc do sklepu Windows Store, aby zwiększyć wydajność i bezpieczeństwo aplikacji. Aplikacja Windows Szybka pomoc umożliwia Tobie i użytkownikom końcowym odbieranie lub udzielanie pomocy komputerowej za pośrednictwem połączenia zdalnego.

Dzięki nowej aplikacji ze sklepu Szybka pomoc Store powinna nastąpić znacząca poprawa czasu generowania kodu dostępu i zmniejszenie liczby błędów aplikacji.

Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z komputerem za pośrednictwem połączenia zdalnego](https://support.microsoft.com/windows/solve-pc-problems-over-a-remote-connection-b077e31a-16f4-2529-1a47-21f6a9040bf3) i [Instalowanie Szybka pomoc](https://support.microsoft.com/windows/install-quick-assist-c17479b7-a49d-4d12-938c-dbfb97c88bca)

## <a name="april-2022"></a>Kwiecień 2022 r.

### <a name="nps-sentiment-insights"></a>Szczegółowe informacje tonacji serwera NPS

Analizy ankiet nps to pulpit nawigacyjny oparty na sztucznej inteligencji dostępny w Centrum administracyjne platformy Microsoft 365.

W centrum administracyjnym przejdź do obszaru Informacje o **ankietach nps opinii o** >  **produktach** **kondycji** > .

Ta funkcja ułatwia administratorom, takim jak Ty, uzyskanie praktycznych szczegółowych informacji pochodzących z ankiet nps firmy Microsoft, na które użytkownicy odpowiedzieli. Dowiedz się więcej na [stronie Microsoft product NPS feedback and insights for your organization (Opinie i szczegółowe informacje dotyczące serwera NPS produktów firmy Microsoft dla Twojej organizacji](manage/manage-feedback-product-insights.md)).

Na podstawie Twoich opinii wprowadzamy nową funkcję, która identyfikuje tonację dla każdej opinii nps dosłownej, dzięki czemu możesz dowiedzieć się, co użytkownicy czują w odniesieniu do Microsoft 365 produktów. Etykiety tonacji, takie jak **Pozytywne**, **Negatywne** i **Inne** , są przypisywane do opinii dosłownej nps.

:::image type="content" source="../media/product-feedback-nps-verbatims.png" alt-text="Zrzut ekranu: Pulpit nawigacyjny opinii o produkcie na karcie Analizy ankiet nps":::

Dzięki funkcji tonacji na pulpicie nawigacyjnym analizy ankiet nps będziesz mieć możliwość:

- Wizualizuj trend tonacji w ciągu ostatnich 12 miesięcy na podstawie opinii nps dosłownej.

- Zidentyfikuj tonację na aplikację i platformę.

Dostępne są trzy opinie:

:::image type="content" source="../media/sentiment-examples.png" alt-text="Zrzut ekranu: Przykłady tonacji i opisy":::

Aby zapewnić lepsze środowisko korzystania z pulpitu nawigacyjnego analizy ankiet nps, zalecamy sprawdzenie następujących elementów:

- Zachęć użytkowników do przesyłania opinii.

- Upewnij się [, że zasady ankiet w produktach](https://config.office.com) są włączone.

- Zwiększanie możliwości diagnozowania przez włączenie [Raportowanie błędów systemu Windows](/windows/win32/wer/windows-error-reporting).

> [!NOTE]
> Jeśli jesteś klientem korporacyjnym i chcesz dołączyć do naszych sesji projektowych, wyślij do nas wiadomość e-mail: prosight@microsoft.com

### <a name="microsoft-365-admin-center-search"></a>wyszukiwanie Centrum administracyjne platformy Microsoft 365

Teraz możesz wyświetlić wszystkie wyniki wyszukiwania na osobnej stronie przeglądarki, wyszukując w wyszukiwanie globalne i wybierając pozycję **Enter**.

Dzięki naszej nowej osobnej stronie wyników wyszukiwania możesz zapoznać się z bardziej kompleksową listą wyników i łatwo wrócić do strony przeglądarki, aby uzyskać bardziej wydajne środowisko wyszukiwania.

:::image type="content" source="../media/whats-new-search-page.png" alt-text="Zrzut ekranu: Nowa strona wyszukiwania w przeglądarce Centrum administracyjne platformy Microsoft 365":::

### <a name="search-in-distribution-lists-to-add-priority-accounts"></a>Wyszukiwanie na listach dystrybucyjnych w celu dodania kont priorytetowych

Wcześniej można było tagować tylko konta priorytetowe, wyszukując je przy użyciu imienia i nazwiska, adresu e-mail lub stanowiska. Dzięki tej aktualizacji możesz teraz wyszukiwać osoby, które mają zostać dodane do kont priorytetowych na liście dystrybucyjnej. Umożliwia to zbiorcze dodawanie osób w wydajny sposób i skraca czas potrzebny do oznaczania poszczególnych osób w organizacji.

:::image type="content" source="../media/search-by-distribution-list-priority-accounts.png" alt-text="Zrzut ekranu: wyszukiwanie kont priorytetów do dodania przy użyciu listy dystrybucyjnej":::

- W ramach jednej akcji można oznaczyć maksymalnie 50 użytkowników z listy dystrybucyjnej jako konta priorytetowe.

- Dodatkowe informacje o użytkowniku, takie jak dział i stanowisko, zostały wprowadzone na stronie Konta priorytetowe.

- Konta użytkowników można tagować tylko na listach dystrybucyjnych, a nie na samej liście. Użytkownicy, którzy zostali już otagowaniu, nie będą widoczni w wyszukiwaniu listy dystrybucyjnej.

## <a name="march-2022"></a>Marzec 2022 r.

### <a name="microsoft-365-lighthouse-ga"></a>Microsoft 365 Lighthouse ogólna dostępność

Małe i średnie firmy często polegają na zaufanych partnerach IT w celu zarządzania środowiskami IT. Ułatwiamy partnerom zabezpieczanie klientów na dużą skalę przy użyciu ogólnej dostępności [Microsoft 365 Lighthouse](https://aka.ms/March1SMBPartnerBlog)— wielodostępnego portalu administracyjnego dla dostawców usług zarządzanych. Microsoft 365 Lighthouse zapewnia klientom pełne środowisko dzięki umożliwieniu partnerom szybkiego identyfikowania zagrożeń, nietypowych logowań i alertów dotyczących zgodności urządzeń, aby zapewnić im bezpieczeństwo.

:::image type="content" source="../media/lighthouse.png" alt-text="Zrzut ekranu: pulpit nawigacyjny Microsoft 365 Lighthouse":::

Microsoft 365 Lighthouse jest tylko usługą partnera IT i jest dostępna dla partnerów, którzy są zarejestrowani w programie Dostawca rozwiązań w chmurze (CSP) i zarządzają klientami, którzy mają do 1000 licencjonowanych użytkowników z Microsoft 365 Business Premium, Microsoft 365 E3 lub Microsoft Defender dla Firm (w wersji zapoznawczej) subskrypcji. Jeśli jesteś zarejestrowanym partnerem IT w programie Microsoft CSP, Microsoft 365 Lighthouse jest dostępny bezpłatnie dla Organizacji i został zaprojektowany, aby pomóc Twojej firmie w skalowaniu i rozwoju. Aby uzyskać więcej informacji, zapoznaj się z [biblioteką pomocy Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md).

Aby rozpocząć korzystanie z Microsoft 365 Lighthouse, zobacz [Tworzenie konta w celu Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-sign-up.md). Aby dowiedzieć się więcej na temat Microsoft 365 Lighthouse, usługi Defender dla Firm i Microsoft 365 Business Premium, [dołącz do nas w naszej serii seminariów internetowych partnerów](https://aka.ms/M365MDBSeries).

## <a name="february-2022"></a>Luty 2022 r.

### <a name="net-promoter-score-nps-survey-insights"></a>Szczegółowe informacje o badaniu net promoter score (NPS)

Teraz możesz wyświetlać dane ankiety nps i szczegółowe informacje od użytkowników w Centrum administracyjne platformy Microsoft 365. Dzięki tej nowej funkcji możesz uzyskać praktyczne szczegółowe informacje z odpowiedzi na ankiety nps od użytkowników końcowych i osiągnąć większą radość użytkowników końcowych, rozwiązując wszelkie problemy i problemy.

W centrum administracyjnym przejdź do obszaru Informacje o **ankietach nps opinii o** >  **produktach** **kondycji** > .

:::image type="content" source="../media/feedback-whatsnew.png" alt-text="Zrzut ekranu: wyświetlanie strony opinii w Centrum administracyjne platformy Microsoft 365":::

Zidentyfikowaliśmy typowe motywy z opinii użytkowników. Następnie użyliśmy technik modeli uczenia maszynowego do trenowania zestawów danych i automatycznego organizowania opinii w najważniejsze tematy.

Dostępnych jest dziewięć tematów. Zwróć uwagę na więcej tematów w przyszłych aktualizacjach.

:::image type="content" source="../media/feedback-nine-topics.png" alt-text="Zrzut ekranu: pokazano 9 nowych tematów opinii":::

Pulpit nawigacyjny analizy ankiet nps zawiera również te trzy nowe raporty i tabele przestawne:

- Miesięczny wolumen trendu nps serwera NPS w ciągu ostatnich 12 miesięcy
- Umiejętność identyfikowania pasywnych, promotorów i przeciwników
- Wolumin NPS na platformę i aplikację

Aby zapewnić lepsze środowisko korzystania z pulpitu nawigacyjnego analizy ankiet nps:

- Zachęcanie użytkowników końcowych do przesyłania opinii
- Potwierdź, że zasady ankiet w produktach są włączone
- Ulepsz diagnozę, włączając Raportowanie błędów systemu Windows

Dowiedz się więcej na [stronie Microsoft product NPS feedback and insights for your organization (Opinie i szczegółowe informacje dotyczące serwera NPS produktów firmy Microsoft dla Twojej organizacji](manage/manage-feedback-product-insights.md)).  

> [!NOTE]
> Jeśli chcesz dołączyć do naszych sesji projektowych, wyślij do nas wiadomość e-mail: prosight@microsoft.com

### <a name="microsoft-365-admin-center-video-training"></a>Centrum administracyjne platformy Microsoft 365 trenowanie wideo

Zaktualizowaliśmy nasze Centrum administracyjne platformy Microsoft 365 szkolenia wideo. Przejdź do strony [biblioteki wideo Administracja training,](admin-video-library.yml) aby dowiedzieć się, jak skonfigurować Microsoft 365 i zarządzać nimi dla swojej firmy.

:::image type="content" source="../media/admin-library-vid-training.png" alt-text="Zrzut ekranu: Wyświetlanie biblioteki trenowania wideo centrum administracyjnego":::

## <a name="july-2021"></a>Lipiec 2021

### <a name="microsoft-365-admin-center-search"></a>wyszukiwanie Centrum administracyjne platformy Microsoft 365

Teraz możesz wyszukiwać identyfikatory zdarzeń w <a href="https://go.microsoft.com/fwlink/p/?linkid=2091030" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Możesz dowiedzieć się więcej o bieżących zdarzeniach za pośrednictwem mediów społecznościowych, publikacji branżowych lub od innych administratorów. Teraz możesz przejść do centrum administracyjnego, aby wyszukać więcej szczegółów dotyczących zdarzenia i zrozumieć wpływ na organizację. Po prostu wyszukaj identyfikator zdarzenia w centrum administracyjnym.

:::image type="content" source="../media/incident-id.png" alt-text="Zrzut ekranu: Wyszukiwanie identyfikatora zdarzenia w centrum administracyjnym":::

### <a name="support-ticket-insight-for-premier-organizations"></a>Szczegółowe informacje o biletach pomocy technicznej dla organizacji Premier

Dodaliśmy 2 grafy o nazwie **Trend woluminu** i **Trend woluminu według produktu** , aby uzyskać wizualne szczegółowe informacje o woluminie pomocy technicznej.

Wykres liniowy na karcie **Trend woluminu** wyróżnia trend, jeśli liczba przypadków pomocy technicznej rośnie lub maleje w organizacji z miesiąca na miesiąc. Możesz zatrzymać kursor na wykresie, aby sprawdzić liczbę przypadków pomocy technicznej utworzonych w każdym miesiącu.

:::image type="content" source="../media/SuppInsight-voltrnd.PNG" alt-text="Zrzut ekranu: Graph, który wyróżnia trend, jeśli liczba przypadków pomocy technicznej rośnie lub maleje w organizacji z miesiąca na miesiąc":::

Wykres **Trend wolumenu według produktu** przedstawia 3 najlepsze produkty każdego miesiąca z najwyższymi przypadkami pomocy technicznej. Włączyliśmy filtrowanie w tabeli i teraz możesz filtrować wyniki według **produktów**, **ważności** i **daty**.

:::image type="content" source="../media/SuppInsight-voltrndproduct.PNG" alt-text="Zrzut ekranu: Graph przedstawia 3 najlepsze produkty każdego miesiąca z najwyższymi przypadkami pomocy technicznej":::

Dodaliśmy również 2 nowe pola **, Ważność** i **Data zamknięcia** w tabeli **Wyświetl żądanie usługi** , aby uzyskać więcej informacji na temat biletów.

:::image type="content" source="../media/SuppInsight-date-sev.PNG" alt-text="Zrzut ekranu: Tabela przedstawiająca sortowanie biletów pomocy technicznej według ważności i daty.":::

Aby wyewidencjonować te aktualizacje w <a href="https://go.microsoft.com/fwlink/p/?linkid=2166757" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, przejdź do obszaru Support **View Service requests** in left navigation okienko (Wyświetl żądania usługi **pomocy technicznej** > ) w okienku nawigacji po lewej stronie.

## <a name="june-2021"></a>Czerwiec 2021

### <a name="microsoft-365-admin-center-search"></a>wyszukiwanie Centrum administracyjne platformy Microsoft 365

Dodaliśmy kilka nowych kategorii do funkcji wyszukiwania.

- Teraz możesz wyszukiwać role administratora Microsoft 365 w wyszukiwanie globalne i szybko wyświetlać przypisania ról i zarządzać nimi z dowolnej strony. Na przykład wyszukaj **administratora Intune**.

- Teraz możesz znaleźć uproszczone środowiska konfiguracji za pośrednictwem wyszukiwanie globalne. Może to pomóc Tobie i Twojej drużynie szybko rozpocząć korzystanie z nowych funkcji. Na przykład wyszukaj **ustawienie hasła, które nigdy nie wygaśnie**.

Aby dowiedzieć się więcej na temat wyszukiwania w centrum administracyjnym, zobacz [Wyszukiwanie w Centrum administracyjne platformy Microsoft 365](manage/search-in-the-mac.md).
