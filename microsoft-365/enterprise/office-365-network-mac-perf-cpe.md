---
title: Microsoft 365 przekierowywu przekierowywów sieci
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
description: Microsoft 365 przekierowywu przekierowywów sieci
ms.openlocfilehash: f35257520385f8d4287c9a0839cd1e4e0e6b0aa3
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996410"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 przekierowywu przekierowywów sieci

Przeszlikowanie sieci to funkcja, która integruje różne aplikacje sieci Microsoft 365 z rozwiązaniami sieci zdefiniowanymi programowo (SD-WAN) innych firm w celu optymalizowania i ulepszania łączności sieciowej z punktami końcowymi usług firmy Microsoft. Zoptymalizowana łączność SD-WAN może spowodować poprawę wydajności i możliwości użytkownika.

## <a name="overview"></a>Omówienie

Przekierowywczana sieć zapewnia dwukierunkowy kanał udostępniania danych między firmą Microsoft a twoim rozwiązaniem SD-WAN. W przypadku każdej skonfigurowanej lokalizacji biura i obwodu internetowego firma Microsoft okresowo udostępnia opinie rozwiązania SD-WAN na temat jakości wybranych aplikacji pakietu Microsoft 365 dla ruchu sieciowego skojarzonego z każdym konkretnym obwodem internetowym. Korzystając z tej opinii, rozwiązanie SD-WAN może następnie podjąć inteligentne akcje odzyskiwania, przekierowywjąc Microsoft 365 ruchu aplikacji za pomocą alternatywnych dostępnych linków. 

Obniżenie jakości usługi w ścieżce określonego obwodu internetowego, na przykład zwiększone opóźnienie lub wysoka utrata pakietów, jest trudne do wykrycia w sposób ciągły. Pogorszenie tej wydajności może zaszkodzić procesom obsługi aplikacji takich jak Exchange Online, SharePoint, OneDrive i Microsoft Teams. Typowe symptomy to powolne wyszukiwanie Exchange zawartości, wysoki czas przesyłania podczas interakcji z bibliotekami SharePoint lub OneDrive dokumentów albo niska jakość połączeń lub spotkań w Microsoft Teams.

Mechanizm przesyłania opinii i odzyskiwania w obrębie przekierowywowanego routingu sieciowego ma na celu dynamiczne wykrywanie takich problemów w czasie rzeczywistym i informuje wdrożone rozwiązanie SD-WAN o podjęciu automatycznych działań odzyskiwania.

Kanał udostępniania danych jest również używany do okresowego odbierania danych na poziomie sieci z rozwiązania SD-WAN, w tym informacji o konfiguracji i statystyk użycia skojarzonych z urządzeniem i podłączonymi obwodami. Nie są zbierane ani przechowywane żadne informacje osobiste. Wszystkie zebrane informacje są agregowane w lokalizacjach biura i obwodach internetowych. Te informacje mogą pomóc firmie Microsoft w bardziej efektywnym i efektywnym rozwiązywaniu zgłoszonych problemów z Microsoft 365 usługami i aplikacjami.

>[!NOTE]
>Microsoft 365 przekierowywaną sieć obsługuje dzierżawców w chmurze komercyjnej WW, ale nie obsługuje chmur GCC moderate, GCC High, DoD, Germany lub China.

## <a name="requirements"></a>Wymagania

### <a name="integrated-sd-wan-solutions"></a>Zintegrowane rozwiązania SD-WAN

Firma Microsoft współpracuje z różnymi partnerami, aby umożliwić integrację z przekierowywowym Microsoft 365 przekierowywowym siecią. Aktualnie włączone rozwiązania są następujące:

| Device Maker | Nazwa rozwiązania | Minimalna wersja |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Topologia sieci

Informed network routing currently identifies traffic associated with a specific office location and Internet circuit based on the public IP address used to send network traffic to Microsoft. 

Jeśli nie istnieje co najmniej jeden obwód sieciowy zapewniający bezpośredni dostęp do Internetu w lokalizacji gałęzi, przekierowywiona usługa przekierowywu sieci może nie dostarczyć istotnej wartości.

### <a name="application-usage"></a>Użycie aplikacji

Dane dotyczące działania aplikacji (odzwierciedlane za pomocą metryk jakości sieci) są zbierane w ramach użycia określonych aplikacji klienckich firmy Microsoft. Exchange metryki odzwierciedlają użycie Outlook klienta sieci Outlook oraz niektóre Outlook Web App użycia. SharePoint i OneDrive odzwierciedlają użycie poszczególnych SharePoint końcowych dzierżawy, niezależnie od aplikacji klienckiej. Teams metryki odzwierciedlają użycie klienta Teams klasycznego. Podczas oceny kondycji obwodu sieciowego nie jest rozważany inny ruch aplikacji.

## <a name="enabling-informed-network-routing"></a>Włączanie przekierowywowania przekierowywów w

Włączenie przeszłego routingu sieci wymaga wykonania wielu kroków, z których niektóre należy wykonać w interfejsie konfiguracji rozwiązania SD-WAN. Aby uzyskać wskazówki dotyczące inicjowania procesu włączania przeszłego routingu sieci w ramach rozwiązania SD-WAN przed przystąpieniem do konfiguracji w sieci centrum administracyjne platformy Microsoft 365, skontaktuj się z dostawcą rozwiązań SD-WAN.

Gdy wszystko będzie gotowe do włączenia przekierowywowania przeszłej sieci w centrum centrum administracyjne platformy Microsoft 365, upewnij **się, że** masz odpowiednie uprawnienia administratora użytkownika lub **administratora globalnego**.

>[!IMPORTANT]
>Aby udzielić wymaganej zgody aplikacji na poziomie dzierżawy na uzyskanie dostępu do wybranego rozwiązania SD-WAN w celu uzyskania dostępu do kanału udostępniania danych przekierowywu sieciowego, administrator globalny musi wykonać następujące czynności.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Krok 1. Otwórz opcje konfiguracji rozwiązania SD-WAN

W [okienku centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/) pozycję **Kondycja > Łączność sieciowa** w okienku nawigacji po lewej stronie.

Ta sekcja centrum administracyjnego zawiera zagregowane metryki łączności sieciowej dla Organizacji oraz wskazówki dotyczące sposobu poprawy łączności. Aby [uzyskać dodatkowe informacje](office-365-network-mac-perf-overview.md) na temat tych funkcji dostępnych w centrum administracyjnym, zobacz Łączność sieciowa w centrum administracyjnym usługi Administracja Microsoft 365 Center.

Wybierz **Ustawienia > SD-WAN,** aby otworzyć okienko konfiguracji przekierowywu przekierowywu sieci. Pozostałe opcje wyświetlane w obszarze **Ustawienia** mają zastosowanie do ogólnych wskazówek dotyczących łączności sieciowej w centrum administracyjnym i nie są wymagane do włączania przekierowywu przekierowywów w przeszytą sieć.

W okienku konfiguracji wybierz **pozycję Dodaj rozwiązanie SD-WAN**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Krok 2. Wybieranie rozwiązania SD-WAN i lokalizacji przechowywania danych

W polach listy rozwijanej wybierz wdrożone rozwiązanie SD-WAN oraz lokalizację, w której mają być przechowywane dane skojarzone z przekierowywczaną siecią. Dodatkowe informacje [można znaleźć](#data-storage) w sekcji dotyczącej przechowywania danych.

Wybierz pozycję **Dalej**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Krok 3. Zaakceptowanie warunków udostępniania danych

Dokładnie przeczytaj i upewnij się, że dostarczone warunki są skojarzone z udostępnianiem danych między firmą Microsoft a wybranym przez Twoje rozwiązanie SD-WAN, a następnie zaznacz wskazane pole wyboru.

Wybierz pozycję **Dalej**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Krok 4. Udzielanie uprawnień do rozwiązania SD-WAN

Ten krok zainicjuje żądanie przyznawania uprawnień za pomocą usługi Azure Active Directory (Azure AD). Zostaniesz żądany o udzielenie uprawnień na poziomie dzierżawy, które umożliwiają wybranemu rozwiązaniu SD-WAN dostęp do przeszłyego magazynu danych routingu sieciowego i informacji o kondycji usługi skojarzonej z Dzierżawą. Ta akcja wymaga **uprawnień administratora dc usługi Azure AD** lub **uprawnień roli** administratora globalnego.

Wybierz link **Nadaj uprawnienia do tej aplikacji** i postępuj zgodnie z żądaniami usługi Azure AD.

Po zakończeniu udzielania uprawnień wybierz pozycję **Dalej**.

### <a name="step-5-confirm-your-configuration-settings"></a>Krok 5. Potwierdzanie ustawień konfiguracji

Ostatnim krokiem umożliwiającym przekierowywowanie przeszytej sieci dla dzierżawy jest strona potwierdzenia z wyświetlonymi ustawieniami. 

Dla dzierżawy jest teraz włączony przekierowywowyny przekierowywowy usługi przeszłej sieci.

Wybierz **pozycję Gotowe** , a następnie zamknij okienko konfiguracji rozwiązania SD-WAN.

## <a name="configuring-informed-network-routing"></a>Konfigurowanie przekierowywu przeszłej sieci

W ramach rozwiązania SD-WAN wykonasz większą część konfiguracji przekierowywowania informed sieci, na przykład skonfigurujesz sposób kierowania ruchu w zwykłych okolicznościach i alternatywne ścieżki, które powinny być używane w przypadku wykrycia problemów. Aby uzyskać szczegółowe informacje na temat tych kroków konfiguracji, skonsultuj się z dostawcą rozwiązań SD-WAN.

Każda lokalizacja biura musi zostać skonfigurowana w centrum centrum administracyjne platformy Microsoft 365, aby przekierowywowany przekierowyw sieciowy poprawnie identyfikował ruch skojarzony z obwodami sieciowym zapewniającymi łączność z tymi lokalizacjami.

Office lokalizacji mogą być wykrywane automatycznie w ramach ciągłego zbioru telemetrii sieciowej firmy Microsoft. W wyniku tego niektóre lokalizacje mogą być wstępnie wypełnione w centrum administracyjnym dzierżawy. 

Jeśli te lokalizacje są dokładne, wystarczy włączyć funkcję przekierowywowania sieci dla każdej odpowiedniej lokalizacji i skonfigurować obwody internetowe i ich publiczne adresy IP. 

Jeśli lokalizacje wykrywane automatycznie nie są dokładne lub w dzierżawie nie ma wstępnie wypełnionych lokalizacji, musisz dodać lub edytować lokalizacje ręcznie, aby odzwierciedlić dokładną topologię Twojej organizacji.

### <a name="updating-locations"></a>Aktualizowanie lokalizacji

Lokalizacje dzierżawy można znaleźć na **karcie** Lokalizacje. Lokalizacje można edytować bezpośrednio na liście lub aktualizować przy użyciu pliku CSV.

Upewnij się, że na tej liście znajduje się każda lokalizacja biura, w której chcesz włączyć przekierowywowy w sieci.

>[!NOTE]
>Kolumny na liście Lokalizacje **dotyczące** pobranych próbek i inne informacje związane z ocenami nie są związane z funkcją przekierowywowania przekierowywów sieci przekierowywczych.

### <a name="enabling-a-location-for-informed-network-routing"></a>Włączanie lokalizacji dla przekierowywu przekierowywów w przeszytą sieć

1. Z listy **Lokalizacje** wybierz **pozycję Edytuj z** menu szybkich akcji, aby otworzyć okienko konfiguracji lokalizacji.

2. Wybierz **pozycję Microsoft 365 przekierowywuj przekierowywową sieć w tej lokalizacji**.

3. Dodaj wszystkie obwody sieciowe zapewniające łączność z Internetem do tej lokalizacji biura w sekcji Egress adresów **IP w tej sekcji lokalizacji biura**. Upewnij się, że każdy obwód jest skojarzony z unikatowymi publicznymi podsiecimi adresów IP reprezentującmi ruch sieciowy.

4. Wybierz **pozycję Zapisz** , aby zapisać zmiany.

## <a name="disabling-informed-network-routing"></a>Wyłączanie przekierowywu sieci przekierowywowej

Funkcja przekierowywowania przeszłej sieci może zostać wyłączona dla całej dzierżawy przez zresetowanie ustawień rozwiązania SD-WAN. Mimo że spowoduje to zatrzymanie przetwarzania wszystkich danych w ramach usługi Microsoft 365, należy również wyłączyć przekierowywowywną sieć w centrum administracyjnym.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Krok 1. Otwórz opcje konfiguracji rozwiązania SD-WAN

W [okienku centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/) **pozycję Kondycja > Łączność sieciowa** w okienku nawigacji po lewej stronie.

Wybierz **Ustawienia > SD-WAN,** aby otworzyć okienko konfiguracji przekierowywu przekierowywu sieci.

Okienko konfiguracji zawiera podsumowanie obecnie skonfigurowanego rozwiązania SD-WAN.

### <a name="step-2-reset-your-configuration"></a>Krok 2. Resetowanie konfiguracji

W okienku konfiguracji wybierz pozycję **Resetuj ustawienia rozwiązania SD-WAN**.

Ustawienia zostały zresetowane i przekierowywowany przekierowyw sieci został wyłączony. Tę funkcję można włączyć ponownie w dowolnym momencie, korzystając z procedury opisanej w tece [Włączanie przekierowywani na bieżąco przekierowywaną przez przekierowywaną sieć](#enabling-informed-network-routing).

## <a name="data-storage"></a>Przechowywanie danych

Dane wymieniane między firmą Microsoft a dostawcą rozwiązań SD-WAN są przechowywane w lokalizacji przechowywania danych wybranej podczas początkowego włączania przekierowywowania przekierowywów sieciowych o przeszlifowanych danych. Opcje lokalizacji przechowywania danych reprezentują obszary geograficzne Microsoft Azure regionów, w których dane są przechowywane.

Dane są przechowywane w tej lokalizacji przez maksymalnie 30 dni. Po wyłączeniu wszystkie pozostałe dane są usuwane w tym 30-dniowym oknie przechowywania.

Dane w tej lokalizacji są wymieniane z wybranym rozwiązaniem SD-WAN, a lokalizacja skonfigurowanego rozwiązania SD-WAN może nie być w tym samym regionie. Klienci powinni współpracować z dostawcą rozwiązań SD-WAN, aby ocenić wymagania dotyczące lokalizacji przechowywania danych przed wdrożeniem produkcyjnym.

## <a name="related-topics"></a>Tematy pokrewne

[Łączność sieciowa w centrum administracyjne platformy Microsoft 365](office-365-network-mac-perf-overview.md)

[Microsoft 365 lokalizacji łączności sieciowej](office-365-network-mac-location-services.md)
