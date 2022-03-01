---
title: Krok nr 1. Twoja Microsoft 365 dla dzierżaw w przedsiębiorstwie
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Wdrażaj i zarządzaj jednym lub wieloma Microsoft 365 dzierżawami z opcjami dla lokalizacji wielolokalizacji i przenoszenia.
ms.openlocfilehash: 305d7683413d5682c0dddda418e87de0a0a682b7
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027141"
---
# <a name="step-1-your-microsoft-365-for-enterprise-tenants"></a>Krok nr 1. Twoja Microsoft 365 dla dzierżaw w przedsiębiorstwie

Jedną z pierwszych decyzji dotyczących dzierżawy jest to, ilu ich jest. Każda Microsoft 365 jest odrębna, unikatowa i odrębna od wszystkich Microsoft 365 dzierżaw. Odpowiadająca jej dzierżawa usługi Azure AD jest również odrębna, unikatowa i odrębna od wszystkich Microsoft 365 dzierżaw.

## <a name="single-tenant"></a>Jedna dzierżawa
Posiadanie jednej dzierżawy upraszcza wiele aspektów korzystania z usługi Microsoft 365. Jedna dzierżawa oznacza pojedynczą dzierżawę usługi Azure AD z pojedynczym zestawem kont, grup i zasad. Uprawnienia i udostępnianie zasobów w organizacji można wykonać za pośrednictwem tego centralnego dostawcy tożsamości.

Jedna dzierżawa oferuje użytkownikom najbardziej rozbudowane i uproszczone funkcje współpracy oraz zwiększające produktywność.

Oto przykład przedstawiający domyślną lokalizację i dzierżawę usługi Azure AD dzierżawy Microsoft 365 dzierżawy.

![Jedna dzierżawa usługi Microsoft 365 Azure AD.](../media/tenant-management-overview/tenant-management-example-tenant.png)

## <a name="multiple-tenants"></a>Wiele dzierżaw

Istnieje wiele powodów, dla których Twoja organizacja może mieć wiele dzierżaw:

- Izolacji administracyjnej
- Scentralizowany system IT
- Decyzje historyczne
- Fuzje, pozyskiwanie lub zdobywanie danych
- Przejrzyste wyeksregowanie marki dla organizacji współmianingowych
- Dzierżawy przedprodukcji, testowania lub piaskownicy

Oto przykład organizacji, która ma dwie dzierżawy (dzierżawę A i dzierżawę B) w tym samym domyślnym geolokalizacji centrum danych. Każda dzierżawa jest osobną dzierżawą usługi Azure AD.

![Wiele Microsoft 365 dzierżawców z własną dzierżawą usługi Azure AD.](../media/tenant-management-overview/tenant-management-example-multi-tenant.png)

Jeśli masz wiele dzierżaw, istnieją ograniczenia i dodatkowe zagadnienia związane z zarządzaniem nimi i świadczeniem usług użytkownikom.

### <a name="inter-tenant-collaboration"></a>Współpraca w ramach dzierżawy

Jeśli chcesz, aby użytkownicy współpracowali wydajniej w różnych dzierżawach usługi Microsoft 365 w bezpieczny sposób, opcje współpracy w ramach kilku dzierżaw obejmują korzystanie z centralnej lokalizacji dla plików i konwersacji, udostępnianie kalendarzy, korzystanie z wiadomości błyskawicznych, połączeń audio/wideo w celu komunikacji oraz zabezpieczanie dostępu do zasobów i aplikacji.

Aby uzyskać więcej informacji, Microsoft 365 [współpracę w ramach wielu dzierżaw](../enterprise/microsoft-365-inter-tenant-collaboration.md).

### <a name="cross-tenant-mailbox-migration-preview"></a>Migracja skrzynek pocztowych między dzierżawami (wersja Preview)

Przed rozpoczęciem migracji skrzynek pocztowych między dzierżawami (w wersji Preview) podczas przenoszenia skrzynek pocztowych usługi Exchange Online między dzierżawami należy całkowicie usunąć skrzynkę pocztową użytkownika z bieżącej dzierżawy (dzierżawy źródłowej) do dzierżawy lokalnej, Exchange Online następnie do nowej dzierżawy (dzierżawy docelowej). Dzięki nowej funkcji migracji skrzynek pocztowych między dzierżawami administratorzy dzierżawy zarówno w dzierżawie źródłowej, jak i docelowej mogą przenosić skrzynki pocztowe między dzierżawami z minimalnymi zależnościami infrastruktury w ich systemach lokalnych. W ten sposób usuniesz konieczność przenoszenia się ze skrzynek pocztowych i do skrzynek pocztowych.

Oto dwie przykładowe dzierżawy i ich skrzynki pocztowe przed migracją skrzynek pocztowych między dzierżawami.

![Wiele Microsoft 365 dzierżaw i ich skrzynek pocztowych.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-before.png)

Na poniższej ilustracji dwie oddzielne dzierżawy mają własne domeny i zestaw skrzynek Exchange pocztowych.

Oto dzierżawa docelowa (dzierżawa A) po migracji skrzynek pocztowych między dzierżawami.

![Dzierżawa docelowa po migracji skrzynek pocztowych między dzierżawami.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-after.png)

Na poniższej ilustracji jedna dzierżawa ma zarówno domeny, jak i oba zestawy skrzynek Exchange pocztowych.

Aby uzyskać więcej informacji, zobacz [Migracja skrzynek pocztowych między dzierżawami](../enterprise/cross-tenant-mailbox-migration.md).

### <a name="tenant-to-tenant-migrations"></a>Migracje z dzierżawy do dzierżawy

Istnieje kilka metod architektury dla fuzji, nabyć, klientów i innych scenariuszy, które mogą doprowadzić do przeprowadzenia migracji istniejącej Microsoft 365 dzierżawy do nowej dzierżawy. 

Aby uzyskać szczegółowe wskazówki, [Microsoft 365 migrację z dzierżawy do dzierżawy](../enterprise/microsoft-365-tenant-to-tenant-migrations.md).

## <a name="multi-geo-for-a-tenant"></a>Multi-Geo dla dzierżawy

Za pomocą usługi Microsoft 365 Multi-Geo możesz zapewniać i przechowywać dane w spoczynku w innych lokalizacjach geolokalizacji centrum danych wybranych w celu spełnienia wymagań dotyczących przechowywania danych, a jednocześnie odblokować globalne udostępnianie pracownikom nowoczesnego środowiska zwiększającego produktywność.

W środowisku z wieloma lokalizacjami geograficznymi dzierżawa usługi Microsoft 365 składa się z domyślnej lub centralnej lokalizacji, w której pierwotnie utworzono subskrypcję usługi Microsoft 365 oraz jedną lub więcej lokalizacji satelitarnych. W dzierżawie wielowymiarowej informacje o lokalizacjach geograficznych, grupach i informacjach o użytkownikach są mastered w globalnej dzierżawie usługi Azure AD. Ponieważ informacje o dzierżawie są centralnie opanujone i synchronizowane z każdą lokalizacją geograficzną, funkcje współpracy obejmujące wszystkie osoby z Twojej firmy są udostępniane w różnych lokalizacjach.

Oto przykład organizacji, która ma swoją domyślną lokalizację w Europie i lokalizację satelitarną w Ameryce Północnej. Obie lokalizacje współużytkuje tę samą globalną dzierżawę usługi Azure AD dla jednej Microsoft 365 dzierżawy.

![Przykład dzierżawy wielowymiarowej Microsoft 365 danych.](../media/tenant-management-overview/tenant-management-example-multi-geo.png)

Aby uzyskać więcej informacji, zobacz [Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

## <a name="moving-core-data-to-a-new-datacenter-geo"></a>Przenoszenie podstawowych danych do nowego geolokalizacji centrum danych

Firma Microsoft nadal otwiera nowe lokalizacje geograficzne centrum danych dla Microsoft 365 danych. Te nowe lokalizacje geograficzne centrum danych dodają wydajność i oblicz zasoby, aby wspierać nasze bieżące zapotrzebowanie klientów i wzrost użycia. Ponadto nowe lokalizacje geolokalizacji centrum danych oferują lokalizację przechowywania danych w lokalizacji geograficznej na podstawowe dane klientów.

Otwarcie nowego geolokalizacji centrum danych nie ma wpływu na Ciebie i Twoje podstawowe dane przechowywane w istniejącej już lokalizacji geograficznej centrum danych, ale firma Microsoft umożliwia żądanie wczesnej migracji podstawowych danych klienta Twojej organizacji w spoczynku do nowego geolokalizacji centrum danych.

Oto przykład, w którym dzierżawa Microsoft 365 została przeniesiona z geolokalizacji centrum danych Unii Europejskiej do lokalizacji na terenie Zjednoczonego Królestwa.

![Przykład przenoszenia dzierżawy Microsoft 365 między geolokalizacji centrum danych.](../media/tenant-management-overview/tenant-management-example-tenant-move.png)

Aby uzyskać więcej informacji, zobacz [Przenoszenie podstawowych danych do nowych Microsoft 365 lokalizacji geograficznych centrum danych](../enterprise/moving-data-to-new-datacenter-geos.md).

## <a name="products-and-licenses-for-a-tenant"></a>Produkty i licencje dla dzierżawy

Dzierżawa Microsoft 365 zostanie utworzona podczas zakupu pierwszego produktu, na przykład Microsoft 365 E3. Wraz z produktem są również licencje, które są obciążone miesięczną lub roczną opłatą. Następnie administrator przypisuje dostępną licencję z jednego z produktów do konta użytkownika bezpośrednio lub za pośrednictwem członkostwa w grupie. W zależności od potrzeb biznesowych Twojej organizacji możesz mieć zestaw produktów z własną pulą licencji. 

Określanie zestawu produktów i liczby licencji dla każdego z nich wymaga planowania:

- Upewnij się, że masz wystarczającą ilość licencji dla kont użytkowników, które wymagają zaawansowanych funkcji.
- Zapobiegaj utracie licencji lub zbyt wielu nieprzypisanych licencji w zależności od zmian personelu w organizacji.


## <a name="results-of-step-1"></a>Wyniki kroku 1

W przypadku Microsoft 365 dla dzierżaw w przedsiębiorstwie ustalisz:

- Ilu dzierżaw potrzebujesz.
- Dla każdej dzierżawy, które produkty i licencje muszą zostać kupione.
- Czy dzierżawa musi mieć wiele lokalizacji geograficznych, aby spełnić wymagania dotyczące przechowywania danych.
- Czy musisz skonfigurować współpracę w ramach dzierżawy?
- Czy konieczne jest przeprowadzenie migracji jednej dzierżawy do innej dzierżawy?
- Czy musisz przenieść podstawowe dane z jednego geolokalizacji centrum danych do nowego.

Oto przykład nowej dzierżawy.

![Przykład nowej dzierżawy.](../media/tenant-management-overview/tenant-management-tenant-build-step1.png)

Na poniższej ilustracji dzierżawa ma:

- Domyślna lokalizacja odpowiadająca lokalizacji geograficznej Microsoft 365 danych.
- Zestaw produktów i licencji.
- Zestaw aplikacji biurowych w chmurze, z których niektóre są specyficzne dla produktów.
- Dzierżawa usługi Azure AD zawierająca konta administratora globalnego i początkową nazwę domeny DNS.

W kolejnych krokach tego rozwiązania będziemy tworzyć tę liczbę.

## <a name="ongoing-maintenance-for-tenants"></a>Bieżąca konserwacja dzierżaw

Na bieżąco może być konieczne:

- Dodaj nową dzierżawę.
- Dodaj nowe produkty do dzierżawy z początkową liczbą licencji.
- Zmień zestaw licencji dla produktu w dzierżawie, aby dostosować go do zmieniających się wymagań personelu.
- Przenieś podstawowe dane z dzierżawy do nowej lokalizacji geograficznej centrum danych.
- Dodaj multi-Geo na potrzeby wymagań dotyczących przechowywania danych.
- Konfigurowanie współpracy w ramach dzierżawy.

## <a name="next-step"></a>Następny krok

[![Krok 2. Zoptymalizuj dzierżawę pod kątem sieci pod kątem dostępu.](../media/tenant-management-overview/tenant-management-step-grid-networking.png)](tenant-management-networking.md)

Kontynuuj korzystanie [z sieci,](tenant-management-networking.md) aby zapewniać pracownikom optymalną sieć do Microsoft 365 w chmurze.
