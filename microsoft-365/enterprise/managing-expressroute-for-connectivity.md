---
title: Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak zarządzać usługą ExpressRoute dla Office 365, w tym typowymi obszarami konfigurowania, takimi jak filtrowanie prefiksów, zabezpieczenia i zgodność.
ms.openlocfilehash: 493a7c0ca14d05a2b84763b9e9485f828574a930
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753875"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365

Usługa ExpressRoute dla Office 365 oferuje alternatywną ścieżkę routingu umożliwiającą dotarcie do wielu usług Office 365 bez konieczności ruchu wychodzącego do Internetu. Mimo że połączenie internetowe z Office 365 jest nadal potrzebne, określone trasy anonsowane przez firmę Microsoft za pośrednictwem protokołu BGP do sieci sprawiają, że bezpośredni obwód usługi ExpressRoute jest preferowany, chyba że istnieją inne konfiguracje w sieci. Trzy typowe obszary, które można skonfigurować do zarządzania tym routingiem, obejmują filtrowanie prefiksów, zabezpieczenia i zgodność.
  
> [!NOTE]
> Firma Microsoft zmieniła sposób przeglądania domeny routingu komunikacji równorzędnej firmy Microsoft dla usługi Azure ExpressRoute. Od 31 lipca 2017 r. wszyscy klienci usługi Azure ExpressRoute mogą włączyć komunikację równorzędne firmy Microsoft bezpośrednio z poziomu konsoli administracyjnej platformy Azure lub programu PowerShell. Po włączeniu komunikacji równorzędnej firmy Microsoft każdy klient może utworzyć filtry tras w celu otrzymywania anonsów tras protokołu BGP dla aplikacji usługi Dynamics 365 Customer Engagement (wcześniej znanych jako CRM Online). Klienci, którzy potrzebują usługi Azure ExpressRoute dla Office 365, muszą uzyskać recenzję od firmy Microsoft, zanim będą mogli tworzyć filtry tras dla Office 365. Skontaktuj się z zespołem ds. konta Microsoft, aby dowiedzieć się, jak zażądać przeglądu w celu włączenia Office 365 expressroute. Nieautoryzowane subskrypcje próbujące utworzyć filtry tras dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrowanie prefiksów

Firma Microsoft zaleca, aby klienci akceptowali wszystkie trasy protokołu BGP zgodnie z reklamą firmy Microsoft, a podane trasy przechodzą rygorystyczny proces przeglądu i weryfikacji, usuwając wszelkie korzyści wynikające z dodatkowej kontroli. Usługa ExpressRoute natywnie oferuje zalecane kontrolki, takie jak własność prefiksu IP, integralność i skalowanie — bez filtrowania tras przychodzących po stronie klienta.
  
Jeśli potrzebujesz dodatkowej weryfikacji własności tras w publicznej komunikacji równorzędnej usługi ExpressRoute, możesz sprawdzić anonsowane trasy pod kątem listy wszystkich prefiksów adresów IP IPv4 i IPv6 [reprezentujących publiczne zakresy adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Te zakresy obejmują całą przestrzeń adresową firmy Microsoft i zmieniają się rzadko, zapewniając niezawodny zestaw zakresów do filtrowania, który zapewnia również dodatkową ochronę klientom, którzy obawiają się wycieków tras innych niż należące do firmy Microsoft do ich środowiska. Jeśli nastąpi zmiana, zostanie ona wprowadzona 1 dnia miesiąca, a numer wersji w sekcji **szczegółów** strony zmieni się za każdym razem, gdy plik zostanie zaktualizowany.
  
Istnieje wiele powodów, aby uniknąć używania [adresów URL Office 365 i zakresów adresów IP do generowania list filtrów prefiksów](./urls-and-ip-address-ranges.md). W tym następujące elementy:
  
- Prefiksy Office 365 IP często ulegają wielu zmianom.

- Adresy URL i zakresy adresów IP Office 365 są przeznaczone do zarządzania listami dozwolonych zapory i infrastrukturą serwera proxy, a nie routingiem.

- Zakresy adresów URL i IP Office 365 nie obejmują innych usługi firmy Microsoft, które mogą znajdować się w zakresie połączeń usługi ExpressRoute.

|**Opcja**|**Złożoności**|**Zmienianie kontrolki**|
|:-----|:-----|:-----|
|Akceptowanie wszystkich tras firmy Microsoft  <br/> |**Niskie:** Klient korzysta z mechanizmów kontroli firmy Microsoft, aby upewnić się, że wszystkie trasy są właściwie własnością.  <br/> |Brak  <br/> |
|Filtrowanie supersieci należących do firmy Microsoft  <br/> |**Średni:** Klient implementuje podsumowane listy filtrów prefiksów, aby zezwalać tylko na trasy należące do firmy Microsoft.  <br/> |Klienci muszą upewnić się, że rzadkie aktualizacje są odzwierciedlane w filtrach tras.  <br/> |
|Filtrowanie Office 365 zakresów adresów IP  <br/> [!CAUTION] Not-Recommended |**Wysokiej:** Klient filtruje trasy na podstawie zdefiniowanych prefiksów adresów IP Office 365.  <br/> |Klienci muszą zaimplementować niezawodny proces zarządzania zmianami dla miesięcznych aktualizacji.  <br/> [!CAUTION] To rozwiązanie wymaga znaczących zmian. Zmiany, które nie zostaną zaimplementowane w czasie, prawdopodobnie spowodują awarię usługi.   |

Nawiązywanie połączenia z Office 365 przy użyciu usługi Azure ExpressRoute jest oparte na anonsach protokołu BGP określonych podsieci IP reprezentujących sieci, w których są wdrażane punkty końcowe Office 365. Ze względu na globalny charakter Office 365 i liczbę usług, które składają się na Office 365, klienci często muszą zarządzać reklamami, które akceptują w swojej sieci. Jeśli interesuje Cię liczba prefiksów anonsowanych w środowisku, funkcja [społeczności protokołu BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) umożliwia filtrowanie anonsów do określonego zestawu usług Office 365. Ta funkcja jest teraz dostępna w wersji zapoznawczej.
  
Niezależnie od sposobu zarządzania anonsami tras protokołu BGP pochodzącymi od firmy Microsoft, nie uzyskasz żadnej specjalnej ekspozycji na usługi Office 365 w porównaniu z nawiązywaniem połączenia z Office 365 tylko za pośrednictwem obwodu internetowego. Firma Microsoft utrzymuje te same poziomy zabezpieczeń, zgodności i wydajności niezależnie od typu obwodu używanego przez klienta do nawiązywania połączenia z Office 365.
  
### <a name="security"></a>Bezpieczeństwo

Firma Microsoft zaleca utrzymywanie własnych kontroli obwodowych sieci i zabezpieczeń dla połączeń komunikacji równorzędnej usługi ExpressRoute i komunikacji równorzędnej firmy Microsoft, która obejmuje połączenia z usługami Office 365 i z nich. W przypadku żądań sieciowych przesyłanych wychodzących z sieci do sieci firmy Microsoft i przychodzących z sieci firmy Microsoft do sieci należy stosować mechanizmy zabezpieczeń.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Ruch wychodzący od klienta do firmy Microsoft
  
Gdy komputery łączą się z Office 365, łączą się z tym samym zestawem punktów końcowych, niezależnie od tego, czy połączenie jest nawiązywane za pośrednictwem Internetu, czy obwodu usługi ExpressRoute. Niezależnie od używanego obwodu firma Microsoft zaleca traktowanie usług Office 365 jako bardziej zaufanych niż ogólne internetowe miejsca docelowe. Wychodzące mechanizmy kontroli zabezpieczeń powinny koncentrować się na portach i protokołach, aby ograniczyć narażenie i zminimalizować bieżącą konserwację. Wymagane informacje o porcie są dostępne w artykule dotyczącym [punktów końcowych Office 365](./urls-and-ip-address-ranges.md).
  
W przypadku dodatkowych kontrolek można użyć filtrowania na poziomie nazwy FQDN w infrastrukturze serwera proxy, aby ograniczyć lub sprawdzić niektóre lub wszystkie żądania sieciowe przeznaczone dla Internetu lub Office 365. Utrzymywanie listy nazw FQDN w miarę publikowania funkcji i rozwijanie ofert Office 365 wymaga bardziej niezawodnego zarządzania zmianami i śledzenia zmian w [opublikowanych punktach końcowych Office 365](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> Firma Microsoft zaleca, aby nie polegać wyłącznie na prefiksach adresów IP w celu zarządzania zabezpieczeniami ruchu wychodzącego w celu Office 365.

|**Opcja**|**Złożoności**|**Zmienianie kontrolki**|
|:-----|:-----|:-----|
|Brak ograniczeń  <br/> |**Niskie:** Klient zezwala na nieograniczony dostęp wychodzący do firmy Microsoft.  <br/> |Brak  <br/> |
|Ograniczenia portów  <br/> |**Niskie:** Klient ogranicza dostęp wychodzący do firmy Microsoft przez oczekiwane porty.  <br/> |Rzadkie.  <br/> |
|Ograniczenia nazwY FQDN  <br/> |**Wysokiej:** Klient ogranicza dostęp wychodzący do Office 365 na podstawie opublikowanych nazw FQDN.  <br/> |Zmiany miesięczne.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Przychodzący z firmy Microsoft do klienta
  
Istnieje kilka opcjonalnych scenariuszy, które wymagają od firmy Microsoft inicjowania połączeń z siecią.
  
- Usługi ADFS podczas walidacji haseł na potrzeby logowania.

- [Exchange Server wdrożenia hybrydowe](/exchange/exchange-hybrid).

- Wyślij wiadomość e-mail z dzierżawy Exchange Online do hosta lokalnego.

- SharePoint Poczta online wysłana z usługi SharePoint Online do hosta lokalnego.

- [SharePoint federacyjnego wyszukiwania hybrydowego](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint hybrydowy bcs](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype dla firm federacji hybrydowej](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) i/lub [Skype dla firm](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype dla firm łącznik chmury](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Firma Microsoft zaleca zaakceptowanie tych połączeń za pośrednictwem obwodu internetowego zamiast obwodu usługi ExpressRoute w celu zmniejszenia złożoności. Jeśli wymagania dotyczące zgodności lub wydajności wymagają zaakceptowania tych połączeń przychodzących za pośrednictwem obwodu usługi ExpressRoute, zalecane jest użycie zapory lub zwrotnego serwera proxy w celu określenia zakresu akceptowanych połączeń. Punkty końcowe Office 365 umożliwiają ustalenie odpowiednich nazw FQDN i [prefiksów adresów](./urls-and-ip-address-ranges.md) IP.
  
### <a name="compliance"></a>Zgodność

Nie polegamy na ścieżce routingu używanej dla żadnej z naszych kontrolek zgodności. Niezależnie od tego, czy łączysz się z usługami Office 365 za pośrednictwem usługi ExpressRoute, czy obwodu internetowego, nasze mechanizmy kontroli zgodności nie ulegną zmianie. Należy przejrzeć różne poziomy certyfikacji zgodności i zabezpieczeń dla Office 365, aby ustalić najlepszy wybór w celu spełnienia potrzeb organizacji.
  
Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Sieci dostarczania zawartości](content-delivery-networks.md)
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)