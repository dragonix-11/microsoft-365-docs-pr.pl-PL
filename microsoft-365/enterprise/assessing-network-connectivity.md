---
title: Ocenianie Microsoft 365 sieciowej
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Microsoft 365 celu umożliwienia klientom z całego świata łączenia się z usługami za pośrednictwem połączenia internetowego. Wraz z rozwojem usługi zabezpieczenia, wydajność i niezawodność usługi Microsoft 365 są ulepszane w zależności od klientów korzystających z Internetu w celu nawiązania połączenia z usługą.
ms.openlocfilehash: 2f982bbce4786c69034560276e5aceebaa575a00
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985457"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Ocenianie Microsoft 365 sieciowej

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 celu umożliwienia klientom z całego świata łączenia się z usługami za pośrednictwem połączenia internetowego. Wraz z rozwojem usługi zabezpieczenia, wydajność i niezawodność usługi Microsoft 365 są ulepszane w zależności od klientów korzystających z Internetu w celu nawiązania połączenia z usługą.
  
Klienci, którzy planują korzystać Microsoft 365 powinni w ramach projektu wdrożenia ocenić swoje istniejące i prognozowane potrzeby dotyczące łączności internetowej. W przypadku wdrożeń klasy korporacyjnej niezawodna i mająca odpowiedni rozmiar łączność internetowa jest kluczowym elementem Microsoft 365 funkcji i scenariuszy.
  
Oceny sieci mogą być wykonywane przez wiele różnych osób i organizacji w zależności od rozmiaru i preferencji użytkownika. Zakres sieciowy oceny również może się różnić w zależności od tego, na którym miejscu procesu wdrażania jesteś. Aby ułatwić Ci lepsze zrozumienie czynności, jakie należy wykonać w celu przeprowadzenia oceny sieci, omyłowaliśmy przewodnik dotyczący oceny sieci, który pomoże Ci poznać dostępne opcje. Ta ocena określa czynności i zasoby, które należy dodać do projektu wdrożenia, aby umożliwić Pomyślne wdrożenie Microsoft 365.
  
W ramach kompleksowej oceny sieci możliwe będzie rozwiązanie problemów związanych z projektem sieci oraz szczegóły implementacji. Niektóre oceny sieci pokazują, że optymalna łączność sieciowa z siecią Microsoft 365 może mieścić się dzięki drobnym zmianom w konfiguracji lub projekcie istniejącej infrastruktury ruchu wychodzącego do sieci i Internetu.

Niektóre oceny wskażą łączność sieciową z siecią Microsoft 365 będzie wymagać dodatkowych inwestycji w składniki sieciowe. Na przykład sieci przedsiębiorstw obejmujące oddziały i wiele regionów geograficznych mogą wymagać inwestycji w rozwiązania SD-WAN lub zoptymalizowaną infrastrukturę routingu w celu obsługi łączności internetowej z siecią Microsoft 365. Czasami ocena może wskazywać, że na łączność sieciową Microsoft 365 mają wpływ przepisy lub wymagania dotyczące wydajności w takich scenariuszach, jak jakość multimediów Skype dla firm [online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Te dodatkowe wymagania mogą doprowadzić do inwestycji w infrastrukturę łączności internetowej, optymalizację routingu i wyspecjalizowaną łączność bezpośrednią.

Niektóre zasoby pomocne w ocenie sieci:

- Aby [Microsoft 365 na temat łączności sieciowej](microsoft-365-networking-overview.md), zobacz omówienie Microsoft 365 sieci.
- Zobacz [Microsoft 365 łączności sieciowej](./microsoft-365-network-connectivity-principles.md), aby zrozumieć zasady łączności w celu bezpiecznego zarządzania Microsoft 365 siecią i uzyskiwania najlepszej możliwej wydajności.
- Zarejestruj się w [microsoft FastTrack](https://www.microsoft.com/fasttrack), aby uzyskać pomoc ze przewodnikiem Microsoft 365 planowania, projektowania i wdrażania. 
- Zobacz [sekcję Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) testową łączności, aby uruchomić testy łączności podstawowej, które zawierają szczegółowe wskazówki dotyczące ulepszeń łączności sieciowej, które mogą być wprowadzone między określoną lokalizacją użytkownika a Microsoft 365.

> [!NOTE]
> Autoryzacja firmy Microsoft jest wymagana do używania usługi ExpressRoute dla Office 365. Firma Microsoft przegląda każde żądanie klienta i autoryzuje usługę ExpressRoute Office 365 na potrzeby użycia tylko wtedy, gdy wymagane jest regule prawne klienta wymagane przez łączność bezpośrednią. W przypadku takich wymagań należy udostępnić fragment tekstu i link do sieci Web do interpretowanego przez Ciebie rozporządzenia, aby oznaczać, że wymagana jest bezpośrednia łączność w uwitrynie [ExpressRoute dla systemu Office 365 Formularz](https://aka.ms/O365ERReview) żądania w celu rozpoczęcia przeglądu firmy Microsoft. Nieautoryzowane subskrypcje próbujące utworzyć filtry trasy dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709).
  
Najważniejsze kwestie do rozważenia podczas planowania oceny sieci na Microsoft 365:
  
- Microsoft 365 to bezpieczna, niezawodna i o wysokiej wydajności usługa, która działa za pośrednictwem publicznego Internetu. Będziemy nadal inwestować w celu ulepszania tych aspektów usługi. Wszystkie Microsoft 365 są dostępne za pośrednictwem łączności internetowej.

- Stale optymalizujemy podstawowe aspekty Microsoft 365, takie jak dostępność, zasięg globalny i wydajność, pod względem łączności opartej na Internecie. Na przykład wiele usług Microsoft 365 korzysta z rozszerzających się węzłów brzegowych zwróconych w stronę Internetu. Ta sieć brzegowa oferuje najlepsze zbliżeń i wydajności dla połączeń pochodzących z Internetu.

- Rozważając użycie usługi Microsoft 365 do jakichkolwiek dostępnych usług, takich jak funkcje komunikacji głosowej, wideo lub spotkań usługi Teams lub Skype dla firm Online, klienci powinni dokończyć ocenę sieci i spełniać wymagania dotyczące łączności przy użyciu usługi [Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Jeśli oceniasz Microsoft 365 i nie masz pewności, od czego zacząć ocenę sieci, lub znalazłeś wyzwania związane z projektem sieci, których rozwiązania potrzebujesz do rozwiązania, skontaktuj się ze swoim zespołem konta Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Test Microsoft 365 połączenia

Test [Microsoft 365](https://aka.ms/netonboard) jest narzędziem do oceny sieci (POC, Proof of Concept) dla sieci, które sprawdza podstawową łączność względem Twojej dzierżawy usługi Microsoft 365 i udostępnia konkretne zalecenia dotyczące projektu sieci w celu uzyskania optymalnej Microsoft 365 wydajności. Narzędzie wyróżnia typowe wybory projektu obwodu sieci dużych przedsiębiorstwa, które przydają się do przeglądania Internetu, ale wpływają na wydajność dużych aplikacji SaaS, takich jak Microsoft 365.

Narzędzie do dołączania do sieci obsługuje następujące czynności:

- Wykrywa lokalizację lub możesz określić lokalizację do przetestowania.
- Sprawdza lokalizację Twojego ruchu wychodzącego do sieci.
- Sprawdza ścieżkę sieciową do najbliższej Microsoft 365 serwisowej z przodu.
- Udostępnia zaawansowane testy przy użyciu aplikacji sieci Windows 10 do pobrania, która przedstawia zalecenia dotyczące projektu sieci obwodowej dotyczące serwerów proxy, zapór i systemu DNS. Narzędzie to również uruchamia testy wydajności pod Skype dla firm Online, Microsoft Teams, SharePoint Online i Exchange Online.

Narzędzie ma dwa składniki: oparty na przeglądarce interfejs użytkownika, który zbiera podstawowe informacje dotyczące łączności, oraz aplikację do Windows 10 do pobrania, która uruchamia testy zaawansowane i zwraca dodatkowe dane testów.

W narzędziu opartym na przeglądarce są wyświetlane następujące informacje:

- Karta Wyniki i wpływ
  - Położenie na mapie drzwi frontu wejściowego użytkowania w usłudze
  - Położenie na mapie innych drzwi przedniego usługi, które zapewniłyby optymalną łączność
  - Względna wydajność w porównaniu z innymi Microsoft 365 w pobliżu
- Karta Szczegóły i rozwiązania
  - Lokalizacja użytkownika według miasta i kraju
  - Lokalizacja ruchu wychodzącego sieciowego według miasta, stanu i kraju
  - Użytkownik do sieciowej odległości ruchu wychodzącego
  - Microsoft 365 Exchange Online serwisowej na drzwiach przednich
  - Optymalne Microsoft 365 Exchange Online serwisowych drzwi z przodu w celu zapewnienia lokalizacji użytkownika
  - Klienci w Twoim regionie metra o lepszej wydajności

Aplikacja Test zaawansowany do pobrania udostępnia następujące dodatkowe informacje:

- Karta Szczegóły i rozwiązania (dołączana)
  - Brama domyślna użytkownika
  - Serwer DNS klienta
  - Rekurencyjna rozpoznawanie nazw DNS klienta
  - Exchange Online serwera DNS
  - SharePoint DNS online
  - Identyfikacja serwera proxy
  - Sprawdzanie łączności multimediów
  - Utrata pakietów jakości multimediów
  - Opóźnienie jakości multimediów
  - Zakłóceń jakości multimediów
  - Zmiana kolejności pakietów jakości multimediów
- Testy łączności z wieloma punktami końcowymi specyficznych dla funkcji
- Diagnostyka ścieżek sieciowych, która zawiera dane śledzenia i opóźnień dla Exchange Online, SharePoint Online i Teams internetowych

Możesz przeczytać o teście łączności Microsoft 365 i przekazać opinię w wpisie w blogu [PoC updated Microsoft 365 test](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) łączności z nowymi zaleceniami projektu sieci. Informacje o przyszłych aktualizacjach tego narzędzia i innych Microsoft 365 sieciowych zostaną opublikowane w blogu Office 365 [sieciowym](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking).
  
Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>Tematy pokrewne

[Microsoft 365 na temat łączności sieciowej](microsoft-365-networking-overview.md)

[Microsoft 365 dotyczące łączności sieciowej](./microsoft-365-network-connectivity-principles.md)

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Office 365 adresu IP i usługi sieci Web adresu URL](microsoft-365-ip-web-service.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)