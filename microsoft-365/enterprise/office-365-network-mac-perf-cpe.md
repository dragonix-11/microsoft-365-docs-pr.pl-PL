---
title: Microsoft 365 routingu sieci
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
description: Microsoft 365 routingu sieci
ms.openlocfilehash: fc946b3a1de057605b89bcadeb4e5b7269aebcb0
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622482"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 routingu sieci

Świadomy routing sieciowy to funkcja, która integruje różne aplikacje Microsoft 365 z rozwiązaniami sieci zdefiniowanej programowo (SD-WAN) innych firm w celu optymalizacji i poprawy łączności sieciowej z punktami końcowymi usługi firmy Microsoft. Zoptymalizowana łączność SD-WAN może spowodować poprawę środowiska i wydajności użytkowników.

## <a name="overview"></a>Omówienie

Usługa routingu sieciowego zapewnia dwukierunkowy kanał udostępniania danych między firmą Microsoft a rozwiązaniem SD-WAN. W przypadku każdej skonfigurowanej lokalizacji w biurze i obwodu internetowego firma Microsoft okresowo dzieli się opiniami z rozwiązaniem SD-WAN na temat jakości wybranych Microsoft 365 środowisk aplikacji dla ruchu sieciowego skojarzonego z każdym konkretnym obwodem internetowym. Korzystając z tej opinii, rozwiązanie SD-WAN może następnie podjąć akcje odzyskiwania inteligentnego przez routing ruchu aplikacji Microsoft 365 za pośrednictwem alternatywnych dostępnych linków. 

Obniżenie jakości usług w ścieżce określonego obwodu internetowego, takie jak zwiększone opóźnienie lub duża utrata pakietów, jest trudne do wykrycia w sposób ciągły. Te degradacje mogą być szkodliwe dla środowisk użytkownika dla aplikacji, takich jak Exchange Online, SharePoint, OneDrive i Microsoft Teams. Typowe objawy to powolne wyszukiwanie zawartości Exchange, wysokie czasy transferu podczas interakcji z bibliotekami dokumentów SharePoint lub OneDrive albo niska jakość wywołań lub spotkań w Microsoft Teams.

Mechanizm przekazywania opinii i odzyskiwania w ramach routingu świadomej sieci ma na celu dynamiczne wykrywanie takich problemów niemal w czasie rzeczywistym i informuje wdrożone rozwiązanie SD-WAN o podjęciu automatycznych akcji odzyskiwania.

Kanał udostępniania danych jest również używany do okresowego odbierania danych optycznych na poziomie sieci z rozwiązania SD-WAN, w tym informacji o konfiguracji i statystyk użycia skojarzonych z urządzeniem i dołączonymi obwodami. Żadne dane osobowe nie są zbierane ani przechowywane. Wszystkie zebrane informacje są agregowane do lokalizacji biura i połączonych obwodów internetowych. Te informacje mogą pomóc firmie Microsoft w wydajniejszym i efektywniejszym rozwiązywaniu zgłoszonych problemów z korzystaniem z usług i aplikacji Microsoft 365.

>[!NOTE]
>Microsoft 365 usługa routingu sieciowego obsługuje dzierżawy w chmurze komercyjnej platformy WW, ale nie w chmurach GCC Moderate, GCC High, DoD, Germany lub China.

## <a name="requirements"></a>Wymagania

### <a name="integrated-sd-wan-solutions"></a>Zintegrowane rozwiązania SD-WAN

Firma Microsoft współpracuje z różnymi partnerami, aby umożliwić integrację z Microsoft 365 routingiem sieci. Obecnie włączone rozwiązania obejmują następujące elementy:

| Device Maker | Nazwa rozwiązania | Minimalna wersja |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Topologia sieci

Świadomy routing sieciowy obecnie identyfikuje ruch skojarzony z określoną lokalizacją biura i obwodem internetowym na podstawie publicznego adresu IP używanego do wysyłania ruchu sieciowego do firmy Microsoft. 

W przypadku, gdy nie ma co najmniej jednego obwodu sieciowego zapewniającego bezpośredni dostęp do Internetu w lokalizacji gałęzi, routing sieciowy z informacją może nie zapewniać znaczącej wartości.

### <a name="application-usage"></a>Użycie aplikacji

Dane środowiska aplikacji (odzwierciedlone za pośrednictwem metryk jakości sieci) są zbierane poprzez użycie określonych aplikacji klienckich firmy Microsoft. Exchange metryki odzwierciedlają użycie klienta Outlook i niektóre Outlook Web App użycia. Metryki SharePoint i OneDrive odzwierciedlają użycie punktów końcowych SharePoint specyficznych dla dzierżawy, niezależnie od aplikacji klienckiej. Teams metryki odzwierciedlają użycie klienta Teams desktop. Inny ruch aplikacji nie jest brany pod uwagę podczas oceny kondycji obwodu sieciowego.

## <a name="enabling-informed-network-routing"></a>Włączanie świadomego routingu sieci

Włączenie świadomego routingu sieciowego wymaga wielu kroków, z których niektóre należy wykonać w interfejsie konfiguracji rozwiązania SD-WAN. Skontaktuj się z dostawcą rozwiązania SD-WAN, aby uzyskać wskazówki dotyczące sposobu inicjowania procesu włączania świadomego routingu sieciowego w rozwiązaniu SD-WAN przed kontynuowaniem konfiguracji w Centrum administracyjne platformy Microsoft 365.

Gdy wszystko będzie gotowe do włączenia świadomego routingu sieciowego w Centrum administracyjne platformy Microsoft 365, upewnij się, że masz wymagane uprawnienia **administratora użytkownika** lub **administratora globalnego**.

>[!IMPORTANT]
>Aby udzielić odpowiedniej zgody aplikacji na poziomie dzierżawy dla wybranego rozwiązania SD-WAN w celu uzyskania dostępu do kanału udostępniania danych routingu sieciowego, należy wykonać następujące kroki jako administrator globalny.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Krok 1. Otwieranie opcji konfiguracji rozwiązania SD-WAN

W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/) wybierz pozycję **Kondycja > Łączność sieciowa** w okienku nawigacji po lewej stronie.

Ta sekcja centrum administracyjnego zawiera zagregowane metryki łączności sieciowej dla organizacji oraz wskazówki dotyczące sposobu poprawy łączności. Aby uzyskać dodatkowe informacje na temat tych funkcji dostępnych [w centrum administracyjnym, zobacz Łączność sieciowa w centrum Administracja Microsoft 365](office-365-network-mac-perf-overview.md).

Wybierz **Ustawienia > rozwiązanie SD-WAN**, aby otworzyć okienko konfiguracji routingu sieciowego. Inne opcje, które są wyświetlane w **obszarze Ustawienia**, mają zastosowanie do ogólnych wskazówek dotyczących łączności sieciowej w centrum administracyjnym i nie są wymagane do włączenia świadomego routingu sieciowego.

W okienku konfiguracji wybierz pozycję **Dodaj rozwiązanie SD-WAN**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Krok 2. Wybieranie rozwiązania SD-WAN i lokalizacji magazynu danych

W polach rozwijanych wybierz wdrożone rozwiązanie SD-WAN oraz lokalizację, w której mają być przechowywane dane skojarzone z routingiem sieciowym. Aby uzyskać dodatkowe informacje, zobacz sekcję [magazyn danych](#data-storage) .

Wybierz pozycję **Dalej**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Krok 3. Akceptowanie warunków udostępniania danych

Uważnie przeczytaj i potwierdź podane terminy skojarzone z udostępnianiem danych między firmą Microsoft a wybranym rozwiązaniem SD-WAN, a następnie zaznacz wskazane pole wyboru.

Wybierz pozycję **Dalej**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Krok 4. Udzielanie uprawnień do rozwiązania SD-WAN

Ten krok spowoduje zainicjowanie żądania udzielenia uprawnień za pomocą Azure Active Directory (Azure AD). Zostanie wyświetlony wniosek o przyznanie uprawnień na poziomie dzierżawy, które zezwalają wybranemu rozwiązaniu SD-WAN na dostęp do magazynu danych routingu sieciowego oraz informacji o kondycji usługi skojarzonych z dzierżawą. Ta akcja wymaga **Azure AD uprawnień administratora kontrolera domeny** lub roli **administratora globalnego**.

Wybierz link **Nadaj uprawnienia tej aplikacji** i postępuj zgodnie z Azure AD żądaniami.

Po zakończeniu udzielania uprawnień wybierz pozycję **Dalej**.

### <a name="step-5-confirm-your-configuration-settings"></a>Krok 5. Potwierdzanie ustawień konfiguracji

Ostatnim krokiem włączania świadomego routingu sieciowego dla dzierżawy jest strona potwierdzenia, która wyświetla podane ustawienia. 

Świadomy routing sieci jest teraz włączony dla dzierżawy.

Wybierz pozycję **Gotowe** , a następnie zamknij okienko konfiguracji rozwiązania SD-WAN.

## <a name="configuring-informed-network-routing"></a>Konfigurowanie routingu świadomej sieci

Wykonasz dużą część konfiguracji dla świadomego routingu sieciowego w ramach rozwiązania SD-WAN, na przykład konfigurując sposób kierowania ruchu w normalnych warunkach i alternatywne ścieżki, które powinny być używane w przypadku wykrycia problemów. Aby uzyskać szczegółowe informacje na temat tych kroków konfiguracji, skontaktuj się z dostawcą rozwiązań SD-WAN.

Każda lokalizacja biura musi być skonfigurowana w Centrum administracyjne platformy Microsoft 365, aby usługa routingu sieciowego mogła prawidłowo identyfikować ruch skojarzony z obwodami sieciowymi zapewniającymi łączność z tymi lokalizacjami.

Office lokalizacje mogą być automatycznie wykrywane w ramach trwającej kolekcji danych telemetrycznych sieci firmy Microsoft. W związku z tym niektóre lokalizacje mogą być wstępnie wypełnione w centrum administracyjnym dzierżawy. 

Jeśli te lokalizacje są dokładne, wystarczy włączyć funkcję świadomego routingu sieciowego dla każdej żądanej lokalizacji i skonfigurować obwody internetowe i ich publiczne adresy IP. 

Jeśli automatycznie wykryte lokalizacje nie są dokładne lub w dzierżawie nie ma wstępnie wypełnionych lokalizacji, musisz dodać lub edytować lokalizacje ręcznie, aby odzwierciedlić dokładną topologię organizacji.

### <a name="updating-locations"></a>Aktualizowanie lokalizacji

Lokalizacje dzierżawy można znaleźć na **karcie Lokalizacje** . Lokalizacje mogą być edytowane bezpośrednio na liście lub aktualizowane przy użyciu pliku CSV.

Upewnij się, że na tej liście znajduje się każda lokalizacja biura, w której chcesz włączyć routing sieciowej.

>[!NOTE]
>Kolumny na liście **Lokalizacje** dla zebranych przykładów i inne informacje związane z oceną nie są związane z funkcją świadomego routingu sieciowego.

### <a name="enabling-a-location-for-informed-network-routing"></a>Włączanie lokalizacji dla świadomego routingu sieciowego

1. Na liście **Lokalizacje** wybierz pozycję **Edytuj** z menu Szybkich akcji, aby otworzyć okienko konfiguracji lokalizacji.

2. Wybierz pozycję **Użyj Microsoft 365 świadomego routingu sieci w tej lokalizacji**.

3. Dodaj wszystkie obwody sieciowe zapewniające łączność z Internetem do tej lokalizacji biura w **Egress zakresach adresów IP w tej sekcji lokalizacji biura**. Upewnij się, że każdy obwód jest skojarzony z unikatowymi podsieciami publicznego adresu IP reprezentującymi ruch sieciowy.

4. Wybierz pozycję **Zapisz** , aby zapisać zmiany.

## <a name="disabling-informed-network-routing"></a>Wyłączanie routingu sieci z informacją

Świadoma funkcja routingu sieciowego może zostać wyłączona dla całej dzierżawy przez zresetowanie ustawień rozwiązania SD-WAN. Mimo że spowoduje to zatrzymanie całego przetwarzania danych w Microsoft 365, należy również wyłączyć routing sieci z informacją w centrum administracyjnym.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Krok 1. Otwieranie opcji konfiguracji rozwiązania SD-WAN

W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/) wybierz pozycję **Kondycja > Łączność sieciowa** w okienku nawigacji po lewej stronie.

Wybierz **Ustawienia > rozwiązanie SD-WAN**, aby otworzyć okienko konfiguracji routingu sieciowego.

W okienku konfiguracji przedstawiono podsumowanie aktualnie skonfigurowanego rozwiązania SD-WAN.

### <a name="step-2-reset-your-configuration"></a>Krok 2. Resetowanie konfiguracji

W okienku konfiguracji wybierz pozycję **Resetuj ustawienia rozwiązania SD-WAN**.

Ustawienia zostały zresetowane i poinformowano, że routing sieci został wyłączony. Można go ponownie włączyć w dowolnym momencie, wykonując kroki opisane w [temacie Włączanie routingu świadomej sieci](#enabling-informed-network-routing).

## <a name="data-storage"></a>Magazyn danych

Dane wymieniane między firmą Microsoft a dostawcą rozwiązań SD-WAN są przechowywane w lokalizacji magazynu danych wybranej podczas początkowego włączania świadomego routingu sieciowego. Opcje lokalizacji magazynu danych reprezentują obszary geograficzne zawierające Microsoft Azure regionów, w których są przechowywane dane.

Dane są przechowywane w tej lokalizacji przez maksymalnie 30 dni. Po wyłączeniu wszystkie pozostałe dane zostaną usunięte w tym 30-dniowym oknie przechowywania.

Dane w tej lokalizacji są wymieniane z wybranym rozwiązaniem SD-WAN, a lokalizacja skonfigurowanego rozwiązania SD-WAN może nie znajdować się w tym samym regionie. Klienci powinni współpracować ze swoim dostawcą rozwiązań SD-WAN, aby ocenić wszelkie wymagania dotyczące lokalizacji magazynu danych przed wdrożeniem produkcyjnym.

## <a name="related-topics"></a>Tematy pokrewne

[Łączność sieciowa w Centrum administracyjne platformy Microsoft 365](office-365-network-mac-perf-overview.md)

[usługi lokalizacji łączności sieciowej Microsoft 365](office-365-network-mac-location-services.md)
