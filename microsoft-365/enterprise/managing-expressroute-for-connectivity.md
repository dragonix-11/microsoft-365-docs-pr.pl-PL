---
title: Zarządzanie łącznością sieciową za Office 365 ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Dowiedz się, jak zarządzać usługą ExpressRoute dla Office 365, w tym o wspólnych obszarach konfigurowania, takich jak filtrowanie prefiksu, zabezpieczenia i zgodność.
ms.openlocfilehash: bffe82249a9d8a531ee85525f9db0eb38a344d50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985480"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Zarządzanie łącznością sieciową za Office 365 ExpressRoute

Usługa ExpressRoute dla usługi Office 365 oferuje alternatywną ścieżkę routingu, która umożliwia dotarcie do wielu Office 365 internetowych bez konieczności kierowania całego ruchu do Internetu. Mimo że połączenie internetowe z usługą Office 365 jest nadal potrzebne, określone trasy do Twojej sieci anonsowane przez firmę Microsoft za pośrednictwem BGP sprawiają, że bezpośredni obwód usługi ExpressRoute jest preferowany, chyba że w Twojej sieci istnieją inne konfiguracje. Trzy typowe obszary, które możesz chcieć skonfigurować do zarządzania tym routingiem, to filtrowanie prefiksów, zabezpieczenia i zgodność.
  
> [!NOTE]
> Firma Microsoft zmieniła sposób rerecenzowania domeny routingu komunikacji równorzędnej firmy Microsoft dla usługi Azure ExpressRoute. Począwszy od 31 lipca 2017 r., wszyscy klienci usługi Azure ExpressRoute mogą włączyć komunikacji równorzędnej firmy Microsoft bezpośrednio z konsoli administracyjnej platformy Azure lub za pomocą programu PowerShell. Po włączeniu komunikacji równorzędnej firmy Microsoft dowolny klient może tworzyć filtry trasy w celu odbierania ogłoszeń trasy BGP dla aplikacji Dynamics 365 Customer Engagement (wcześniej znanych jako CRM Online). Klienci potrzebujący usługi Azure ExpressRoute dla usługi Office 365 muszą uzyskać recenzję od firmy Microsoft, aby mogą tworzyć filtry trasy dla Office 365. Skontaktuj się ze swoim zespołem kont Microsoft, aby dowiedzieć się, jak zażądać recenzji w celu włączenia Office 365 ExpressRoute. Nieautoryzowane subskrypcje próbujące utworzyć filtry trasy dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrowanie prefiksów

Firma Microsoft zaleca, aby klienci akceptowali wszystkie trasy BGP w sposób anonsowany przez firmę Microsoft , czyli trasy podane przechodzą rygorystyczny proces recenzji i weryfikacji, usuwający wszelkie korzyści w celu dodania kontroli. ExpressRoute natywnie oferuje zalecane mechanizmy kontroli, takie jak własność prefiksu IP, integralność i skalę — bez filtrowania trasy przychodzącej po stronie klienta.
  
Jeśli wymagasz dodatkowej weryfikacji własności ścieżki w publicznej komunikacji równorzędnej usługi ExpressRoute, możesz sprawdzić ogłaszane trasy względem listy wszystkich prefiksów IP protokołu IPv4 i IPv6 reprezentujących zakresy publicznych adresów [IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Te zakresy pokrywają całą przestrzeń adresów firmy Microsoft i zmieniają się rzadko, oferując niezawodny zestaw zakresów do filtrowania, co zapewnia również dodatkową ochronę dla klientów, którzy martwią się o trasy nienależących do firmy Microsoft wyciekają do ich środowiska. W przypadku zmiany zostanie ona wana pierwszego dnia miesiąca, a numer wersji w sekcji szczegóły na stronie będzie zmieniany za każdym razem,  gdy plik zostanie zaktualizowany.
  
Istnieje kilka powodów, dla których należy unikać używania zakresów adresów IP Office 365 URL i [IP](./urls-and-ip-address-ranges.md) do generowania list filtrowania prefiksu. Są to między innymi następujące elementy:
  
- Prefiksy OFFICE 365 IP są często zmieniane.

- Adresy Office 365 i zakresy adresów IP są przeznaczone do zarządzania listami zezwalań zapory i infrastrukturą serwera proxy, a nie do routingu.

- Zakresy Office 365 URL i IP nie obejmują innych usługi firmy Microsoft, które mogą być w zakresie połączeń usługi ExpressRoute.

|**Opcja**|**Złożoność**|**Kontrolka zmiany**|
|:-----|:-----|:-----|
|Akceptuj wszystkie trasy firmy Microsoft  <br/> |**Niska:** Klient korzysta z kontrolek firmy Microsoft, aby zapewnić prawidłowe własność wszystkich tras.  <br/> |Brak  <br/> |
|Filtrowanie supersieci należących do firmy Microsoft  <br/> |**Średni:** Klient implementuje zsumowane listy filtrowania prefiksów, aby umożliwić tylko trasy będące własnością firmy Microsoft.  <br/> |Klienci muszą upewnić się, że rzadko aktualne aktualizacje są odzwierciedlane w filtrach tras.  <br/> |
|Filtrowanie Office 365 zakresów adresów IP  <br/> [!CAUTION] Not-Recommended |**Wysoka:** Klient filtruje trasy na podstawie zdefiniowanych Office 365 IP.  <br/> |Klienci muszą zaimplementować niezawodny proces zarządzania zmianami na potrzeby comiesięcznych aktualizacji.  <br/> [!CAUTION] To rozwiązanie wymaga od nas znacznych, wywłaszanych zmian. Zmiany nie zaimplementowane w terminie prawdopodobnie będą skutkować zmianami w usłudze.   |

Nawiązywanie połączenia Office 365 przy użyciu usługi Azure ExpressRoute jest oparte na anonsach BGP określonych podsieci IP reprezentujących sieci, w których Office 365 punkty końcowe są wdrażane. Ze względu na globalny charakter usługi Office 365 oraz liczbę usług, które się Office 365, klienci często muszą zarządzać anonsami, które akceptują w swoich sieciach. Jeśli martwi Cię liczba prefiksów ogłaszanych w środowisku, funkcja społeczności [BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) umożliwia filtrowanie reklam do określonego zestawu Office 365 usług. Ta funkcja jest teraz w wersji Preview.
  
Niezależnie od tego, jak zarządzasz anonsami tras BGP pochodzących od firmy Microsoft, nie uzyskasz żadnego specjalnego dostępu do usług Office 365 w porównaniu z nawiązywanie połączenia z usługą Office 365 tylko za pomocą obwodu internetowego. Firma Microsoft zapewnia taki sam poziom zabezpieczeń, zgodności i wydajności niezależnie od typu obwodu używanego przez klienta do łączenia się z Office 365.
  
### <a name="security"></a>Bezpieczeństwo

Firma Microsoft zaleca, aby utrzymywać własne mechanizmy kontroli obwodu zabezpieczeń i sieci dla połączeń przechodzących do i z publicznej komunikacji równorzędnej usługi ExpressRoute oraz komunikacji równorzędnej firmy Microsoft, które obejmują połączenia z Office 365 połączeń. Mechanizmy kontroli zabezpieczeń powinny być stosować w przypadku żądań sieciowych wychodzących z Twojej sieci do sieci firmy Microsoft oraz przychodzących z sieci firmy Microsoft do Twojej sieci.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Połączenia wychodzące od klienta do firmy Microsoft
  
Gdy komputery nawiąają połączenie Office 365, łączą się z tym samym zestawem punktów końcowych niezależnie od tego, czy połączenie jest nawiązywane za pośrednictwem obwodu internetowego, czy za pośrednictwem obwodu usługi ExpressRoute. Niezależnie od używanego obwodu firma Microsoft zaleca, aby traktować usługi sieci Office 365 jako bardziej zaufane niż ogólne miejsca docelowe Internetu. Mechanizmy kontroli zabezpieczeń połączeń wychodzących powinny być skoncentrowane na portach i protokołach w celu zmniejszenia ekspozycji i zminimalizowania stałej konserwacji. Wymagane informacje o portach są dostępne w [artykule Office 365 informacji o punktach końcowych](./urls-and-ip-address-ranges.md).
  
Aby uzyskać dodatkowe kontrolki, możesz użyć filtrowania na poziomie FQDN w obrębie swojej infrastruktury serwerów proxy, aby ograniczać lub sprawdzać niektóre lub wszystkie żądania przeznaczone dla Internetu lub Office 365. Utrzymywanie listy plików FQN w czasie, gdy funkcje są publikowane i Office 365 ofert wymaga bardziej zaawansowanego zarządzania zmianami i śledzenia zmian w opublikowanych Office 365 [końcowych](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> Firma Microsoft zaleca, aby nie polegać wyłącznie na prefiksach IP w celu zarządzania zabezpieczeniami połączeń wychodzących w Office 365.

|**Opcja**|**Złożoność**|**Kontrolka zmiany**|
|:-----|:-----|:-----|
|Bez ograniczeń  <br/> |**Niska:** Klient zezwala na nieograniczony dostęp wychodzący do firmy Microsoft.  <br/> |Brak  <br/> |
|Ograniczenia portów  <br/> |**Niska:** Klient ogranicza dostęp połączeń wychodzących do firmy Microsoft przez oczekiwane porty.  <br/> |Rzadko.  <br/> |
|Ograniczenia FQDN  <br/> |**Wysoka:** Klient ogranicza dostęp połączeń wychodzących do Office 365 na podstawie opublikowanych fQDn.  <br/> |Comiesięczne zmiany.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Połączenia przychodzące od firmy Microsoft do klienta
  
Istnieje kilka opcjonalnych scenariuszy, które wymagają, aby firma Microsoft zainicjowała połączenia z Twoją siecią.
  
- Usługi ADFS podczas sprawdzania poprawności hasła logowania.

- [Exchange Server wdrożeń hybrydowych](/exchange/exchange-hybrid).

- Poczta z dzierżawy Exchange Online do hosta lokalnego.

- SharePoint poczty online z usługi SharePoint Online do hosta lokalnego.

- [SharePoint wyszukiwania hybrydowego feder służącego do wyszukiwania hybrydowego](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint usług łączności biznesowej.](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution)

- [Skype dla firm hybrydowe](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) i/[lub Skype dla firm federacyjną](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype dla firm Łącznik chmury](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Firma Microsoft zaleca, aby akceptować te połączenia za pośrednictwem obwodu internetowego, a nie obwodu usługi ExpressRoute, w celu zmniejszenia złożoności. Jeśli Twoje potrzeby w zakresie zgodności lub wydajności muszą być akceptowane przez te połączenia przychodzące za pośrednictwem obwodu usługi ExpressRoute, zalecane jest użycie zapory lub zwrotnego serwera proxy w celu określić zakres akceptowanych połączeń. Za pomocą tych [Office 365 końcowych](./urls-and-ip-address-ranges.md) możesz ustalić odpowiednie nazwy FQDN i prefiksy IP.
  
### <a name="compliance"></a>Zgodność

Nie polegamy na ścieżce routingu, którą używasz na podstawie żadnej z naszych kontroli zgodności. Niezależnie od tego, czy łączysz się Office 365 usługami za pomocą obwodu usługi ExpressRoute, czy za pomocą obwodu internetowego, nasze mechanizmy kontroli zgodności nie zmienią się. Należy zapoznać się z różnymi poziomami certyfikatów zabezpieczeń i zgodności Office 365, aby ustalić najlepszą możliwość spełniania potrzeb Twojej organizacji.
  
Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Sieci dostarczania zawartości](content-delivery-networks.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Szkolenia dotyczące usługi Azure ExpressRoute Office 365 usługi Azure ExpressRoute](https://channel9.msdn.com/series/aer)