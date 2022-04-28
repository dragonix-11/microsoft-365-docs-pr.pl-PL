---
title: Sieć dla firmy Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Zapoznaj się z infrastrukturą sieciową firmy Contoso i sposobem, w jaki firma wykorzystuje technologię SD-WAN w celu uzyskania optymalnej wydajności sieci w celu Microsoft 365 dla usług w chmurze dla przedsiębiorstw.
ms.openlocfilehash: f8450b63bed68de414c0ea585b6f5e199c87ad90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093948"
---
# <a name="networking-for-the-contoso-corporation"></a>Sieć dla firmy Contoso Corporation

Aby wdrożyć infrastrukturę uwzględniającą chmurę, firma Contoso opracowała fundamentalną zmianę w sposobie przenoszenia ruchu sieciowego do usług w chmurze. Zamiast wewnętrznego modelu piasty i szprych, który koncentruje łączność sieciową i ruch na następnym poziomie hierarchii pakietu Office, mapowali lokalizacje użytkowników na lokalne połączenia internetowe i lokalne z najbliższą lokalizacją sieci Microsoft 365 w Internecie.

## <a name="networking-infrastructure"></a>Infrastruktura sieciowa

Są to elementy sieci, które łączą biura firmy Contoso na całym świecie:

- Sieć WAN multiprotocol Label Switching (MPLS)

  Sieć MPLS WAN łączy siedzibę w Paryżu z biurami regionalnymi i regionalnymi z biurami satelitarnymi w konfiguracji szprychy i koncentratora. Sieć umożliwia użytkownikom dostęp do serwerów lokalnych, które tworzą aplikacje biznesowe w siedzibie głównej w Paryżu. Kieruje również każdy ogólny ruch internetowy do biura w Paryżu, gdzie urządzenia zabezpieczeń sieci szorują żądania. W każdym biurze routery dostarczają ruch do hostów przewodowych lub punktów dostępu bezprzewodowego w podsieciach, które korzystają z prywatnej przestrzeni adresowej IP.

- Lokalny bezpośredni dostęp do Internetu dla ruchu Microsoft 365

  Każdy urząd ma zdefiniowane programowo urządzenie WAN (SD-WAN), które ma co najmniej jeden lokalny internetowy obwód sieciowy usługodawcy internetowego z własną łącznością internetową za pośrednictwem serwera proxy. Jest to zwykle implementowane jako link sieci WAN do lokalnego usługodawcy internetowego, który udostępnia również publiczne adresy IP i lokalny serwer DNS.

- Obecność w Internecie

  Firma Contoso jest właścicielem nazwy domeny publicznej contosocom\.. Publiczna witryna internetowa firmy Contoso do zamawiania produktów to zestaw serwerów w połączonym z Internetem centrum danych w kampusie w Paryżu. Firma Contoso używa zakresu publicznych adresów IP /24 w Internecie.

Rysunek 1 przedstawia infrastrukturę sieciową firmy Contoso i jej połączenia z Internetem.

![Sieć firmy Contoso.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Rysunek 1. Sieć firmy Contoso**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Korzystanie z sieci SD-WAN w celu uzyskania optymalnej łączności sieciowej z firmą Microsoft

Firma Contoso przestrzegała [Microsoft 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md) w celu:

- Identyfikowanie i rozróżnianie ruchu sieciowego Microsoft 365
- Egress połączeń sieciowych lokalnie
- Unikanie sieciowych spinek do włosów
- Pomijanie zduplikowanych sieciowych urządzeń zabezpieczeń

Istnieją trzy kategorie ruchu sieciowego dla Microsoft 365: *Optymalizuj*, *Zezwalaj* i *Domyślne*. Optymalizacja i zezwalanie na ruch to zaufany ruch sieciowy, który jest szyfrowany i zabezpieczony w punktach końcowych i jest przeznaczony dla sieci Microsoft 365.

Firma Contoso zdecydowała się na:

- Użyj bezpośredniego ruchu wychodzącego z Internetu, aby zoptymalizować i zezwolić na ruch kategorii oraz przekazać cały domyślny ruch kategorii do centralnego połączenia internetowego z siedzibą w Paryżu.

- Wdrażanie urządzeń SD-WAN w każdym biurze jako prosty sposób na przestrzeganie tych zasad i osiągnięcie optymalnej wydajności sieci dla Microsoft 365 usług opartych na chmurze.

  Urządzenia SD-WAN mają port LAN dla lokalnej sieci biurowej i wiele portów sieci WAN. Jeden port sieci WAN łączy się z siecią MPLS. Inny łączy się z lokalnym obwodem usługodawcy sieciowego. Urządzenie SD-WAN kieruje opcję Optymalizuj i zezwalaj na ruch sieciowy kategorii za pośrednictwem linku usługodawcy internetowego.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Infrastruktura aplikacji biznesowych firmy Contoso

Firma Contoso jest architektem infrastruktury intranetu aplikacji biznesowych i serwera w następujących celach:

- Biura satelitarne używają lokalnych serwerów buforowania do przechowywania często używanych dokumentów i wewnętrznych witryn internetowych.
- Centra regionalne używają regionalnych serwerów aplikacji dla biur regionalnych i satelitarnych. Te serwery synchronizują się z serwerami w siedzibie głównej w Paryżu.
- Centra danych kampusu w Paryżu zawierają scentralizowane serwery aplikacji, które obsługują całą organizację.

Rysunek 2 przedstawia procent pojemności ruchu sieciowego używany podczas uzyskiwania dostępu do serwerów w intranecie firmy Contoso.

![Infrastruktura firmy Contoso dla aplikacji wewnętrznych.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Rysunek 2. Infrastruktura firmy Contoso dla aplikacji wewnętrznych**

W przypadku biur centrów satelitarnych lub regionalnych 60 procent zasobów potrzebnych pracownikom może być obsługiwanych przez serwery satelitarne i regionalne. Dodatkowe 40 procent żądań zasobów musi przejść przez link sieci WAN do kampusu w Paryżu.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Analiza sieci i przygotowanie do Microsoft 365 dla przedsiębiorstw

Pomyślne wdrożenie Microsoft 365 dla usług dla przedsiębiorstw przez użytkowników firmy Contoso zależy od wysokiej dostępności i wydajnej łączności z Internetem lub bezpośrednio z usługami w chmurze firmy Microsoft. Firma Contoso podjęła następujące kroki, aby zaplanować i zaimplementować zoptymalizowaną łączność z Microsoft 365 dla usług w chmurze dla przedsiębiorstw:

1. Tworzenie diagramu sieci WAN firmy w celu pomocy w planowaniu

   Aby rozpocząć planowanie sieci, firma Contoso utworzyła diagram przedstawiający lokalizacje biura, istniejącą łączność sieciową, istniejące urządzenia obwodowe sieci i klasy usług, które są zarządzane w sieci. Korzystali z tego diagramu dla każdego kolejnego kroku planowania i implementacji łączności sieciowej.

2. Tworzenie planu dla Microsoft 365 dla łączności sieciowej przedsiębiorstwa

   Firma Contoso użyła [Microsoft 365 zasad łączności sieciowej i przykładowych](microsoft-365-network-connectivity-principles.md) referencyjnych architektur sieci do zidentyfikowania sieci SD-WAN jako preferowanej topologii łączności Microsoft 365.

3. Analizowanie wykorzystania połączenia internetowego i przepustowości MPLS-WAN w każdym biurze i zwiększanie przepustowości w razie potrzeby

   Przeanalizowano bieżące użycie każdego biura, a obwody zostały zwiększone, dzięki czemu przewidywany ruch oparty na chmurze Microsoft 365 będzie działać ze średnią nieużywaną pojemnością wynoszącą 20 procent.

4. Optymalizowanie wydajności usług sieciowych firmy Microsoft

   Firma Contoso określiła zestaw punktów końcowych Office 365, Intune i azure oraz skonfigurowanych zapór, urządzeń zabezpieczeń i innych systemów w ścieżce internetowej w celu uzyskania optymalnej wydajności. Punkty końcowe dla Office 365 Optymalizuj i Zezwalaj na ruch kategorii zostały skonfigurowane na urządzeniach SD-WAN na potrzeby routingu przez obwód usługodawcy internetowego.

5. Konfigurowanie wewnętrznego systemu DNS

   System DNS musi działać i być wyszukiwany lokalnie pod kątem ruchu Microsoft 365.

6. Weryfikowanie sieciowego punktu końcowego i łączności portów

   Firma Contoso uruchomiła narzędzia testowe łączności sieciowej firmy Microsoft, aby zweryfikować łączność dla Microsoft 365 dla usług w chmurze dla przedsiębiorstw.

7. Optymalizowanie komputerów pracowników pod kątem łączności sieciowej

   Poszczególne komputery zostały sprawdzone, aby upewnić się, że zainstalowano najnowsze aktualizacje systemu operacyjnego i że monitorowanie zabezpieczeń punktu końcowego było aktywne na wszystkich klientach.

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso [wykorzystuje swoje usługi lokalna usługa Active Directory Domain Services w chmurze](contoso-identity.md) dla pracowników i federuje uwierzytelnianie dla klientów i partnerów biznesowych.

## <a name="see-also"></a>Zobacz też

[Plan sieciowy dla Microsoft 365](networking-roadmap-microsoft-365.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki po laboratorium testowym](m365-enterprise-test-lab-guides.md)
