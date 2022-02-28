---
title: Sieci firmy Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Zrozumienie infrastruktury sieciowej firmy Contoso i sposobu, w jaki firma korzysta z technologii SD-WAN w celu zapewnienia optymalnej wydajności sieci w Microsoft 365 dla usług w chmurze przedsiębiorstwa.
ms.openlocfilehash: 94c9c43e35f0f1a3d973529aa2b107cffe608693
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985048"
---
# <a name="networking-for-the-contoso-corporation"></a>Sieci firmy Contoso Corporation

W celu przyjęcia infrastruktury chmurowej firma Contoso opracowała podstawową zmianę sposobu ruchu sieciowego do usług w chmurze. Zamiast wewnętrznego modelu hub-and-wrysłowy, w którym skupiono się na łączności sieciowej i ruchu na następnym poziomie hierarchii biura, zamapowane są one na lokalny internetowy ruch wychodzący i połączenia lokalne z najbliższą lokalizacją sieciową Microsoft 365 w Internecie.

## <a name="networking-infrastructure"></a>Infrastruktura sieci

Są to elementy sieci, które łączyją biura firmy Contoso na całym świecie:

- Sieć WAN multiprotocol Label Switching (MPLS)

  Sieć MPLS WAN łączy siedzibę główną Paryża z oddziałami regionalnymi i oddziałami regionalnymi w konfiguracji rozsyłanej na urządzeniach satelitarnych i w centrum. Sieć umożliwia użytkownikom dostęp do serwerów lokalnych, które składa się z aplikacji biznesowych w siedzibie głównej w Paryżu. Ponadto przekierowywuje on dowolny ogólny ruch internetowy do biura w Paryżu, gdzie urządzenia zabezpieczeń sieciowych przesuwają żądania. W każdym biurze routery dostarczają ruch do hostów przewodowych lub punktów dostępu bezprzewodowego w podsieci, w których jest wykorzystanie prywatnej przestrzeni adresów IP.

- Lokalny bezpośredni dostęp do Internetu dla Microsoft 365 ruchu

  Każde biuro ma urządzenie w sieci WAN (SD-WAN) zdefiniowane programowo, które ma co najmniej jeden lokalny obwód sieciowy u dostawcy internetowego z własną łącznością internetową za pośrednictwem serwera proxy. Jest to zwykle zaimplementowane jako link sieci WAN do lokalnego dostawcy usług internetowych, który również udostępnia publiczne adresy IP i lokalny serwer DNS.

- Obecność w Internecie

  Contoso jest właścicielem nazwy domeny publicznej contosocom\.. Publiczna witryna sieci Web Firmy Contoso do zamawiania produktów to zestaw serwerów w centrum danych połączonym z Internetem w paryżu campus. Firma Contoso używa publicznego zakresu adresów IP /24 w Internecie.

Rysunek 1 przedstawia infrastrukturę sieciową firmy Contoso i jej połączenia z Internetem.

![Sieć Contoso.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Rysunek 1. Sieć Contoso**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Korzystanie z sieci SD-WAN w celu zapewnienia optymalnej łączności sieciowej z firmą Microsoft

Firma Contoso [przestrzegać Microsoft 365 dotyczących łączności sieciowej](microsoft-365-network-connectivity-principles.md) do:

- Identyfikowanie i rozróżnianie Microsoft 365 sieciowego
- Egress połączeń sieciowych lokalnie
- Unikaj spinek sieciowych
- Pomijanie zduplikowanych urządzeń zabezpieczeń sieciowych

Istnieją trzy kategorie ruchu sieciowego dla następujących Microsoft 365: *Optymalizuj*, *Zezwalaj* i *Domyślne*. Optymalizuj i zezwalaj na ruch jest zaufanym ruchem sieciowym, który jest zaszyfrowany i zabezpieczony w punktach końcowych i jest przeznaczony do Microsoft 365 sieci.

Firma Contoso zdecydowała się:

- Użyj bezpośredniego internetowego ruchu wychodzącego, aby zoptymalizować i zezwolić na ruch kategorii oraz aby przesyłać dalej cały domyślny ruch kategorii do centralnego połączenia internetowego opartego na Paryżu.

- Wdrażaj urządzenia SD-WAN w każdym biurze w prosty sposób zgodnie z tymi zasadami i osiągaj optymalną wydajność sieci dla Microsoft 365 usług opartych na chmurze.

  Urządzenia SD-WAN mają port LAN dla lokalnej sieci biura i wiele portów WAN. Jeden port WAN łączy się z siecią MPLS. Inny łączy się z lokalnym obwodem sieciowym. Urządzenie SD-WAN umożliwia trasę optymalizowania i zezwalania na ruch sieciowy kategorii za pośrednictwem linku internetowego.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Infrastruktura aplikacji biznesowych firmy Contoso

Firma Contoso zaprojektowała swoją infrastrukturę intranetową aplikacja LOB serwera na przykład w następujący sposób:

- Biura satelitarne korzystają z lokalnych serwerów buforowania do przechowywania często używanych dokumentów i wewnętrznych witryn sieci Web.
- Centra regionalne korzystają z serwerów aplikacji regionalnych dla biur regionalnych i satelitarnych. Te serwery są synchronizowane z serwerami w siedzibie głównej w Paryżu.
- Centra danych firmy Paris Campus zawierają scentralizowane serwery aplikacji, które obsługują całą organizację.

Rysunek 2 przedstawia wartość procentową pojemności ruchu sieciowego używaną podczas uzyskiwania dostępu do serwerów przez intranet firmy Contoso.

![Infrastruktura firmy Contoso dla aplikacji wewnętrznych.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Rysunek 2. Infrastruktura firmy Contoso dla aplikacji wewnętrznych**

W przypadku biur satelitarnych lub regionalnych 60% zasobów potrzebnych pracownikom może być obsługiwanych przez serwery biur satelitarnych i regionalnych centrów regionalnych. Dodatkowe 40 procent żądań zasobów musi zostać za pośrednictwem łącza WAN do uniwersytetu w Paryżu.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Analiza sieci i przygotowanie do Microsoft 365 przedsiębiorstwa

Pomyślne wdrożenie usługi Microsoft 365 dla przedsiębiorstw firmy Contoso zależy od wysokiej dostępnej i wydajnej łączności z Internetem lub bezpośrednio z usługami firmy Microsoft w chmurze. Firma Contoso zajęła się tym, aby zaplanować i zaimplementować zoptymalizowaną łączność z usługami Microsoft 365 w chmurze przedsiębiorstwa:

1. Tworzenie firmowego diagramu sieci WAN w celu pomocy w planowaniu

   Aby rozpocząć planowanie sieci, firma Contoso utworzyła diagram przedstawiający lokalizacje ich biur, istniejącą łączność sieciową, istniejące urządzenia obwodowe sieci oraz klasy usług zarządzane w sieci. Używali tego diagramu na każdym kolejnym etapie planowania i implementacji łączności sieciowej.

2. Tworzenie planu na Microsoft 365 dla łączności sieciowej w przedsiębiorstwie

   Firma Contoso użyła [zasad Microsoft 365](microsoft-365-network-connectivity-principles.md) łączności sieciowej i przykładowych referencyjnych architektur sieciowych do identyfikowania sieci SD-WAN jako ich preferowanej topologii dla Microsoft 365 sieci.

3. Analizowanie użycia połączenia internetowego i przepustowości MPLS-WAN w każdym biurze i zwiększanie przepustowości zgodnie z potrzebami

   Analizowane było bieżące użycie każdego biura, a obwody zostały zwiększone, dzięki czemu przewidywany ruch oparty na chmurze Microsoft 365 będzie działać przy średniej 20-procentowej nieużywanej pojemności.

4. Optymalizowanie wydajności usług sieciowych firmy Microsoft

   Firma Contoso określała zestaw punktów końcowych usług Office 365, Intune i Azure oraz skonfigurowano zapory, urządzenia zabezpieczeń i inne systemy na ścieżce internetowej w celu zapewnienia optymalnej wydajności. Punkty końcowe dla Office 365 Optymalizacja i Zezwalaj na ruch kategorii zostały skonfigurowane na urządzeniach SD-WAN na kątem routingu za pośrednictwem obwodu isp.

5. Konfigurowanie wewnętrznego systemu DNS

   System DNS musi być funkcjonalny i poszukiwany lokalnie pod Microsoft 365 ruchu.

6. Sprawdzanie poprawności punktu końcowego sieci i łączności portów

   Firma Contoso uruchomiła narzędzia testowe łączności sieciowej firmy Microsoft w celu weryfikacji łączności Microsoft 365 usług w chmurze przedsiębiorstwa.

7. Optymalizowanie komputerów pracowników pod kątem łączności sieciowej

   Poszczególne komputery zostały sprawdzone, aby upewnić się, że zainstalowano najnowsze aktualizacje systemu operacyjnego i że monitorowanie zabezpieczeń punktów końcowych było aktywne na wszystkich klientach.

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso [wykorzystująca](contoso-identity.md) swoje lokalne Usługi domenowe w usłudze Active Directory w chmurze na potrzeby pracowników i uwierzytelnianie federujące dla klientów i partnerów biznesowych.

## <a name="see-also"></a>Zobacz też

[Plan sieci dla sieci dla sieci Microsoft 365](networking-roadmap-microsoft-365.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)
