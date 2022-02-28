---
title: Subskrypcje, licencje, konta i dzierżawy w usługach chmurowych firmy Microsoft
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: Opis relacji między organizacjami, subskrypcjami, licencjami, kontami użytkowników i dzierżawami w różnych ofertach chmury firmy Microsoft.
ms.openlocfilehash: c8f6fca0a5c9ce56c3565612e0de9b40d6e0254c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986640"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Subskrypcje, licencje, konta i dzierżawy w usługach chmurowych firmy Microsoft

Firma Microsoft zapewnia hierarchię organizacji, subskrypcji, licencji i kont użytkowników w celu spójnego korzystania z tożsamości i rozliczeń w swoich ofertach chmurowych:
  
- Microsoft 365 i Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Elementy hierarchii

Oto elementy hierarchii:
  
### <a name="organization"></a>Organizacja

Organizacja reprezentuje podmiot biznesowy korzystający z oferty firmy Microsoft w chmurze, zwykle identyfikowanych przez co najmniej jedną nazwę domeny publicznego systemu nazw domen (DNS), taką jak contoso.com. Organizacja jest kontenerem dla subskrypcji.
  
### <a name="subscriptions"></a>Subskrypcje

Subskrypcja to umowa z firmą Microsoft na korzystanie z co najmniej jednej platformy lub usług w chmurze firmy Microsoft, za które naliczane są opłaty na podstawie opłaty licencyjnej na użytkownika lub użycia zasobów w chmurze. 

- Usługi chmurowe oparte na oprogramowaniu jako usłudze (SaaS) firmy Microsoft (Microsoft 365 i usłudze Dynamics 365) naliczają opłaty za licencje na użytkownika. 
- Usługa PaaS (Platform as a Service) i usługa (Infrastructure as a Service) firmy Microsoft (IaaS) w chmurze (Azure) są naliczane w zależności od zużycia zasobów w chmurze.
 
Możesz również użyć subskrypcji próbnej, ale wygasa ona po upływie określonego czasu lub opłat za użycie. Możesz przekonwertować subskrypcję wersji próbnej na subskrypcję płatną.
  
Organizacje mogą mieć wiele subskrypcji dla ofert firmy Microsoft w chmurze. Rysunek 1 przedstawia pojedynczą organizację, która ma wiele Microsoft 365 subskrypcji usługi Dynamics 365 i wiele subskrypcji platformy Azure.

**Rysunek 1. Przykład wielu subskrypcji dla organizacji**

![Przykładowa organizacja z wieloma subskrypcjami dla ofert chmurowych firmy Microsoft.](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Licencje

W przypadku usług w chmurze SaaS firmy Microsoft licencja umożliwia określonemu kontu użytkownika korzystanie z usług oferowanych w chmurze. W ramach subskrypcji jest pobierana stała opłata miesięczna. Administratorzy przypiszą licencje do poszczególnych kont użytkowników w subskrypcji. Na przykład na rysunku 2 firma Contoso Corporation ma subskrypcję usługi Microsoft 365 E5 na 100 licencji, dzięki której maksymalnie 100 pojedynczych kont użytkowników może korzystać z Microsoft 365 E5 funkcji i usług.
  
**Rysunek 2. Licencje w ramach subskrypcji organizacji opartej na modelu SaaS**

![Przykład wielu licencji w ramach subskrypcji opartych na modelu SaaS firmy Microsoft w chmurze.](../media/Subscriptions/Subscriptions-Fig2.png)

>[!Note]
>Najlepszym rozwiązaniem w zakresie zabezpieczeń jest korzystanie z oddzielnych kont użytkowników, do których przypisano konkretne role dla funkcji administracyjnych. Te dedykowane konta administratora nie muszą mieć przypisanej licencji dla usług w chmurze, których administrują. Na przykład do SharePoint administratora nie musi być przypisana licencja usługi Microsoft 365 licencji.
>

W przypadku usług w chmurze opartych na usłudze Azure PaaS licencje na oprogramowanie są wbudowane w ceny usługi.
  
W przypadku maszyn wirtualnych opartych na platformie Azure IaaS mogą być wymagane dodatkowe licencje na używanie oprogramowania lub aplikacji zainstalowanej na obrazie maszyny wirtualnej. Niektóre obrazy maszyn wirtualnych mają zainstalowane licencjonowane wersje oprogramowania, a koszt jest uwzględniany w stawce minutowej dla serwera. Przykładowe obrazy maszyn wirtualnych dla SQL Server 2014 i SQL Server 2016. 
  
Niektóre obrazy maszyn wirtualnych mają zainstalowane wersje próbne aplikacji i wymagają dodatkowych licencji aplikacji na używanie poza okresem próbnym. Na przykład obraz maszyny wirtualnej wersji próbnej programu SharePoint Server 2016 zawiera preinstalowany SharePoint Server 2016 w wersji próbnej. Aby nadal korzystać SharePoint Server 2016 po dacie wygaśnięcia wersji próbnej, musisz kupić licencję programu SharePoint Server 2016 i licencje klientów firmy Microsoft. Opłaty te nie są związane z subskrypcją platformy Azure, a minutowa opłata za uruchomienie maszyny wirtualnej nadal ma zastosowanie.
  
### <a name="user-accounts"></a>Konta użytkowników

Konta użytkowników we wszystkich ofertach firmy Microsoft w chmurze są przechowywane w dzierżawie usługi Azure Active Directory (Azure AD), która zawiera konta użytkowników i grupy. Dzierżawę usługi Azure AD można synchronizować z istniejącymi Usługi domenowe w usłudze Active Directory (AD DS) przy użyciu usługi Azure AD Połączenie, usługi Windows opartej na serwerze. Jest to nazywane synchronizacją katalogów.
  
Rysunek 3 przedstawia przykład wielu subskrypcji organizacji korzystających ze wspólnej dzierżawy usługi Azure AD, która zawiera konta organizacji.
  
**Rysunek 3. Wiele subskrypcji organizacji, które korzystają z tej samej dzierżawy usługi Azure AD**

![Przykładowa organizacja z wieloma subskrypcjami korzystającymi z tej samej dzierżawy usługi Azure AD.](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Dzierżawcy

W przypadku usług w chmurze SaaS dzierżawa jest lokalizacją regionalną, która mieści serwery oferujące usługi w chmurze. Na przykład firma Contoso Corporation wybrała region europejski, aby hostować swoje subskrypcje usług Microsoft 365, EMS i Dynamics 365 dla 15 000 pracowników w ich siedzibie w Paryżu.
  
Usługi Azure PaaS i obciążenia maszyny wirtualnej hostowane w usłudze Azure IaaS mogą posiadać subskrypcję we wszystkich centrach danych platformy Azure na całym świecie. Podczas tworzenia aplikacji lub usługi Azure PaaS bądź elementu obciążenia IaaS określasz centrum danych platformy Azure, nazywane lokalizacją.
  
Dzierżawa usługi Azure AD to konkretne wystąpienie usługi Azure AD zawierające konta i grupy. Płatne lub próbne subskrypcje usługi Microsoft 365 dynamics 365 zawierają bezpłatną dzierżawę usługi Azure AD. Ta dzierżawa usługi Azure AD nie obejmuje innych usług platformy Azure i nie jest taka sama jak wersja próbna lub płatna subskrypcja usługi Azure.
  
### <a name="summary-of-the-hierarchy"></a>Podsumowanie hierarchii

Oto krótkie podsumowanie:
  
- Organizacja może mieć wiele subskrypcji
    
  - Subskrypcja może mieć wiele licencji
    
  - Licencje można przypisywać do kont poszczególnych użytkowników
    
  - Konta użytkowników są przechowywane w dzierżawie usługi Azure AD
    
Oto przykład relacji między organizacjami, subskrypcjami, licencjami i kontami użytkowników:
  
- Organizacja identyfikowana za pomocą nazwy domeny publicznej.
    
  - Subskrypcja Microsoft 365 E3 z licencjami użytkowników.
    
    Subskrypcja Microsoft 365 E5 z licencjami użytkowników.
    
    Subskrypcja usługi Dynamics 365 z licencjami użytkowników.
    
    Wiele subskrypcji platformy Azure.
    
  - Konta użytkowników organizacji we wspólnej dzierżawie usługi Azure AD.
    
Wiele subskrypcji chmurze firmy Microsoft może korzystać z tej samej dzierżawy usługi Azure AD, która działa jako wspólny dostawca tożsamości. Centralna dzierżawa usługi Azure AD, która zawiera zsynchronizowane konta Lokalnego konta usługi AD DS udostępnia w chmurze tożsamość jako usługę (IDaaS) dla Twojej organizacji. 
  
**Rysunek 4. Zsynchronizowanie kont lokalnych i IDaaS organizacji**

![Identity as a Service (IaaS) IDaaS dla organizacji.](../media/Subscriptions/Subscriptions-Fig4.png)
  
Rysunek 4 przedstawia sposób używania typowej dzierżawy usługi Azure AD przez oferty chmury SaaS firmy Microsoft, aplikacje Azure PaaS i maszyny wirtualne w usłudze Azure IaaS, które korzystają z usług domenowych Azure AD. Usługa Azure AD Połączenie synchronizuje lokalne lassy AD DS z dzierżawą usługi Azure AD.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Łączenie subskrypcji dla wielu ofert chmury firmy Microsoft

W poniższej tabeli opisano, jak można połączyć wiele ofert firmy Microsoft w chmurze w oparciu o już posiadaną subskrypcję jednego typu oferty chmury (etykiety przechodzące w dół pierwszej kolumny) i dodanie subskrypcji innej oferty chmury (przechodzącej przez kolumny).
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |0  <br/> |Subskrypcję platformy Azure można dodać do organizacji z portalu Azure Portal.  <br/> |Subskrypcję usługi Dynamics 365 można dodać do organizacji z centrum administracyjne platformy Microsoft 365.  <br/> |
|**Azure** <br/> |Dodajesz subskrypcję Microsoft 365 organizacji.  <br/> |0  <br/> |Dodajesz subskrypcję usługi Dynamics 365 do swojej organizacji.  <br/> |
|**Dynamics 365** <br/> |Dodajesz subskrypcję Microsoft 365 organizacji.  <br/> |Subskrypcję platformy Azure można dodać do organizacji z portalu Azure Portal.  <br/> |0  <br/> |
   
Łatwym sposobem dodawania subskrypcji do organizacji na usługi oparte na modelu Microsoft SaaS jest dostęp za pośrednictwem centrum administracyjnego:
  
1. Zaloguj się do centrum centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) za pomocą konta administratora **użytkownika** lub administratora **globalnego**.
    
2. W lewej części strony głównej **centrum administracyjnego** kliknij pozycję **Rozliczenia, a** następnie **Zakup usług**.
    
3. Na stronie **Zakup usług** kup nowe subskrypcje.
    
Centrum administracyjne przypisuje organizację i dzierżawę usługi Azure AD Twojej subskrypcji usługi Microsoft 365 do nowych subskrypcji usług opartych na modelu SaaS w chmurze.
  
Aby dodać subskrypcję platformy Azure z taką samą organizacją i dzierżawą usługi Azure AD co Twoja Microsoft 365 subskrypcji:
  
1. Zaloguj się do portalu Azure Portal ([https://portal.azure.com](https://portal.azure.com)) przy użyciu Microsoft 365 **usługi Azure AD DC lub** **konta administratora globalnego**.
    
2. W lewym okienku nawigacji kliknij pozycję **Subskrypcje**, a następnie kliknij pozycję **Dodaj**.
    
3. Na stronie **Dodawanie subskrypcji** wybierz ofertę i uzupełnij informacje o płatności oraz umowę.
    
Jeśli subskrypcje usługi Azure i Microsoft 365 zostały zakupione oddzielnie i chcesz uzyskać dostęp do dzierżawy usługi Azure AD usługi Microsoft 365 z subskrypcji platformy Azure, zobacz instrukcje w tece Dodawanie istniejącej subskrypcji platformy Azure do Azure Active Directory [dzierżawy](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) usługi.
 
## <a name="see-also"></a>Zobacz też

[Ilustracje przedstawiające architektów przedsiębiorstwa w chmurze firmy Microsoft](../solutions/cloud-architecture-models.md)
  
[Modele architektoniczne SharePoint, Exchange, Skype dla firm i Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Rozwiązania hybrydowe](hybrid-solutions.md)

## <a name="next-step"></a>Następny krok

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)
