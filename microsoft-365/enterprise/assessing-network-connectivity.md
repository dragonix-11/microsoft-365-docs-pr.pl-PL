---
title: Ocena łączności sieciowej na platformie Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 została zaprojektowana w celu umożliwienia klientom na całym świecie nawiązywania połączenia z usługą przy użyciu połączenia internetowego. W miarę rozwoju usługi bezpieczeństwo, wydajność i niezawodność Microsoft 365 są ulepszane w oparciu o klientów korzystających z Internetu w celu nawiązania połączenia z usługą.
ms.openlocfilehash: 88664966a7451f342a140feb2ff31186cfc3c818
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099438"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Ocena łączności sieciowej na platformie Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 została zaprojektowana w celu umożliwienia klientom na całym świecie nawiązywania połączenia z usługą przy użyciu połączenia internetowego. W miarę rozwoju usługi bezpieczeństwo, wydajność i niezawodność Microsoft 365 są ulepszane w oparciu o klientów korzystających z Internetu w celu nawiązania połączenia z usługą.
  
Klienci planujący korzystanie z Microsoft 365 powinni ocenić istniejące i prognozowane potrzeby w zakresie łączności z Internetem w ramach projektu wdrażania. W przypadku wdrożeń klasy korporacyjnej niezawodna łączność z Internetem o odpowiednim rozmiarze jest kluczowym elementem korzystania z Microsoft 365 funkcji i scenariuszy.
  
Oceny sieci mogą być wykonywane przez wiele różnych osób i organizacji w zależności od rozmiaru i preferencji. Zakres sieci oceny może się również różnić w zależności od tego, gdzie jesteś w procesie wdrażania. Aby lepiej zrozumieć, czego potrzeba do przeprowadzenia oceny sieci, opracowaliśmy przewodnik oceny sieci, który pomoże Ci zrozumieć dostępne opcje. Ta ocena określi, jakie kroki i zasoby należy dodać do projektu wdrożenia, aby umożliwić pomyślne wdrożenie Microsoft 365.
  
Kompleksowa ocena sieci zapewni możliwe rozwiązania problemów związanych z projektowaniem sieci wraz ze szczegółami implementacji. Niektóre oceny sieci pokazują, że optymalna łączność sieciowa z Microsoft 365 może zostać dostosowana do drobnych zmian konfiguracji lub projektu istniejącej infrastruktury sieci i ruchu wychodzącego z Internetu.

Niektóre oceny wskazują, że łączność sieciowa z Microsoft 365 będzie wymagać dodatkowych inwestycji w składniki sieci. Na przykład sieci przedsiębiorstwa obejmujące biura oddziałów i wiele regionów geograficznych mogą wymagać inwestycji w rozwiązania SD-WAN lub zoptymalizowaną infrastrukturę routingu w celu obsługi łączności internetowej z Microsoft 365. Czasami ocena wskazuje, że na łączność sieciową z Microsoft 365 mają wpływ wymagania dotyczące regulacji lub wydajności w scenariuszach takich jak [jakość multimediów Skype dla firm Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Te dodatkowe wymagania mogą prowadzić do inwestycji w infrastrukturę łączności internetowej, optymalizację routingu i wyspecjalizowaną łączność bezpośrednią.

Niektóre zasoby ułatwiające ocenę sieci:

- Zobacz [Microsoft 365 omówienie łączności sieciowej](microsoft-365-networking-overview.md), aby uzyskać informacje koncepcyjne na temat sieci Microsoft 365.
- Zobacz [Microsoft 365 Zasady łączności sieciowej](./microsoft-365-network-connectivity-principles.md), aby poznać zasady łączności dotyczące bezpiecznego zarządzania ruchem Microsoft 365 i uzyskiwania najlepszej możliwej wydajności.
- Utwórz konto [Microsoft FastTrack](https://www.microsoft.com/fasttrack), aby uzyskać pomoc z przewodnikiem w zakresie planowania, projektowania i wdrażania Microsoft 365. 
- Zapoznaj się z sekcją [Microsoft 365 test łączności](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) poniżej, aby uruchomić podstawowe testy łączności, które zawierają konkretne wskazówki dotyczące ulepszeń łączności sieciowej, które można wprowadzić między daną lokalizacją użytkownika a Microsoft 365.

> [!NOTE]
> Autoryzacja firmy Microsoft jest wymagana do używania usługi ExpressRoute dla Office 365. Firma Microsoft przegląda każde żądanie klienta i autoryzuje usługę ExpressRoute tylko w celu Office 365 użycia, gdy wymaganie prawne klienta nakazuje bezpośrednią łączność. Jeśli masz takie wymagania, podaj fragment tekstu i link internetowy do rozporządzenia, które interpretujesz jako oznacza, że w [usłudze ExpressRoute](https://aka.ms/O365ERReview) jest wymagana bezpośrednia łączność, aby formularz żądania Office 365 mógł rozpocząć przegląd firmy Microsoft. Nieautoryzowane subskrypcje próbujące utworzyć filtry tras dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709).
  
Kluczowe kwestie, które należy wziąć pod uwagę podczas planowania oceny sieci dla Microsoft 365:
  
- Microsoft 365 jest bezpieczną, niezawodną usługą o wysokiej wydajności działającą przez publiczny Internet. Nadal inwestujemy w ulepszanie tych aspektów usługi. Wszystkie usługi Microsoft 365 są dostępne za pośrednictwem łączności internetowej.

- Stale optymalizujemy podstawowe aspekty Microsoft 365, takie jak dostępność, globalny zasięg i wydajność łączności internetowej. Na przykład wiele usług Microsoft 365 korzysta z rozszerzającego się zestawu węzłów brzegowych dostępnych z Internetu. Ta sieć brzegowa oferuje najlepszą bliskość i wydajność połączeń przesyłanych przez Internet.

- Rozważając korzystanie z Microsoft 365 dla dowolnej z uwzględnionych usług, takich jak Teams lub Skype dla firm funkcji głosowych, wideo lub spotkań online, klienci powinni ukończyć kompleksową ocenę sieci i spełnić wymagania dotyczące łączności przy użyciu [Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Jeśli oceniasz Microsoft 365 i nie masz pewności, od czego zacząć od oceny sieci lub znalazłeś wyzwania związane z projektowaniem sieci, które potrzebujesz pomocy w pokonaniu, skontaktuj się z zespołem ds. konta Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Test łączności Microsoft 365

[Test łączności Microsoft 365](https://aka.ms/netonboard) jest narzędziem do oceny sieci koncepcji (POC), które uruchamia podstawowe testy łączności względem dzierżawy Microsoft 365 i udostępnia konkretne zalecenia dotyczące projektowania sieci w celu uzyskania optymalnej wydajności Microsoft 365. Narzędzie wyróżnia typowe opcje projektowania obwodu sieci dużych przedsiębiorstw, które są przydatne do przeglądania internetu, ale mają wpływ na wydajność dużych aplikacji SaaS, takich jak Microsoft 365.

Narzędzie do dołączania sieci wykonuje następujące czynności:

- Wykrywa lokalizację lub można określić lokalizację do przetestowania
- Sprawdza lokalizację ruchu wychodzącego sieci
- Testuje ścieżkę sieciową do najbliższej bramy usługi Microsoft 365
- Udostępnia zaawansowane testy przy użyciu aplikacji Windows 10 do pobrania, która udostępnia zalecenia dotyczące projektowania sieci obwodowej związane z serwerami proxy, zaporami i usługą DNS. Narzędzie uruchamia również testy wydajności dla usług Skype dla firm Online, Microsoft Teams, SharePoint Online i Exchange Online.

Narzędzie ma dwa składniki: interfejs użytkownika oparty na przeglądarce, który zbiera podstawowe informacje o łączności, oraz aplikację do pobrania Windows 10, która uruchamia zaawansowane testy i zwraca dodatkowe dane oceny.

Narzędzie oparte na przeglądarce wyświetla następujące informacje:

- Karta Wyniki i wpływ
  - Lokalizacja na mapie używanych drzwi wejściowych usługi
  - Lokalizacja na mapie innych drzwi frontowych usługi, które zapewniłyby optymalną łączność
  - Względna wydajność w porównaniu z innymi Microsoft 365 klientów w pobliżu
- Karta Szczegóły i rozwiązania
  - Lokalizacja użytkownika według miasta i kraju
  - Lokalizacja ruchu wychodzącego sieci według miasta, stanu i kraju
  - Odległość ruchu wychodzącego od użytkownika do sieci
  - Microsoft 365 Exchange Online lokalizacji drzwi wejściowych usługi
  - Optymalne Microsoft 365 Exchange Online drzwi wejściowe usługi dla lokalizacji użytkownika
  - Klienci w twojej dzielnicy metra z lepszą wydajnością

Aplikacja do pobrania testów zaawansowanych zawiera następujące dodatkowe informacje:

- Karta Szczegóły i rozwiązania (dołączona)
  - Brama domyślna użytkownika
  - Kliencki serwer DNS
  - Rekursywny program rozpoznawania nazw DNS klienta
  - serwer DNS Exchange Online
  - serwer DNS usługi SharePoint Online
  - Identyfikacja serwera proxy
  - Sprawdzanie łączności z nośnikami
  - Utrata pakietów jakości multimediów
  - Opóźnienie jakości multimediów
  - Trema jakości multimediów
  - Zmiana kolejności pakietów dotyczących jakości multimediów
- Testy łączności z wieloma punktami końcowymi specyficznymi dla funkcji
- Diagnostyka ścieżki sieciowej obejmująca dane tracert i opóźnienia dla usług Exchange Online, SharePoint Online i Teams

Możesz przeczytać o teście łączności Microsoft 365 i przekazać opinię na blogu [Zaktualizowano test łączności Microsoft 365 z nowymi zaleceniami dotyczącymi projektowania sieci](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130). Informacje o przyszłych aktualizacjach tego narzędzia i innych Microsoft 365 aktualizacji sieci zostaną opublikowane na blogu [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking).
  
Oto krótki link, którego można użyć do powrotu: [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>Tematy pokrewne

[Omówienie łączności sieciowej Microsoft 365](microsoft-365-networking-overview.md)

[zasady łączności sieciowej Microsoft 365](./microsoft-365-network-connectivity-principles.md)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Usługa Office 365 — usługa sieci Web adresów IP i adresów URL](microsoft-365-ip-web-service.md)

[Microsoft 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)