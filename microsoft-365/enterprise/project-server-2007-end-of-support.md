---
title: Project dotyczące zakończenia pomocy technicznej dla programu Project Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 10 października 2017 r. zakończono obsługę Project Server 2007, Project Portfolio Server i Project 2007. Skorzystaj z tego artykułu, aby już teraz zaplanować uaktualnienie.
ms.openlocfilehash: c492c7154006a139589cff1c768dd77c13804c07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983947"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project dotyczące zakończenia pomocy technicznej dla programu Project Server 2007

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W 2017 roku zakończono pomoc techniczną dla Office i aplikacji w 2007 r. i należy rozważyć plany migracji. Jeśli obecnie używasz programu Project Server 2007 i produktów pokrewnych, zwróć uwagę na następujące daty zakończenia wsparcia technicznego:
  
|**Produkt**|**Data zakończenia pomocy technicznej**|
|:-----|:-----|
|Project Server 2007  <br/> |10 października 2017 r.  <br/> |
|Project Portfolio Server 2007  <br/> |10 października 2017 r.  <br/> |
|Project 2007 Standard  <br/> |10 października 2017 r.  <br/> |
|Project 2007 Professional  <br/> |10 października 2017 r.  <br/> |
   
Aby uzyskać więcej informacji na temat Office 2007, zobacz Uaktualnianie serwerów i produktów klienckich do wersji [Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskać nowe funkcje, poprawki błędów, poprawki zabezpieczeń i tak dalej. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Ponieważ Project Server 2007 zakończył obsługę 10 października 2017 r., firma Microsoft nie udostępnia już:
  
- pomoc techniczną w zakresie mogącego wystąpić problemów;
    
- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
    
- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.
    
- Aktualizacje stref czasowych.
    
Instalacja programu Project Server 2007 będzie nadal działać po upływie tego terminu. Jednak z powodu zmian wymienionych wcześniej zdecydowanie zalecamy przeprowadzenie migracji z programu Project Server 2007 tak szybko, jak to możliwe.
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Jeśli korzystasz z programu Project Server 2007, zapoznaj się z dostępnymi opcjami migracji:
  
- Migrowanie do Project Online
    
- Migrowanie do nowszej lokalnej wersji programu Project Server (najlepiej Project Server 2016)
    
|**Dlaczego warto migrować do Project Online**|**Dlaczego warto migrować do Project Server 2016**|
|:-----|:-----|
| Mam użytkowników urządzeń przenośnych.  <br/> <br/>Koszty migracji są istotnym problemem (sprzęt, oprogramowanie, godziny i nakład pracy związanej z wdrożeniem). <br/><br/>  Głównym problemem po migracji są koszty utrzymania mojego środowiska (na przykład aktualizacje automatyczne, gwarantowany czas bezadysekwny itp.).  <br/> | Reguły biznesowe ograniczają moje możliwości prowadzenia firmy w chmurze.<br/><br/>  Potrzebuję kontroli nad aktualizacjami środowiska.  |
   
> [!NOTE]
> Aby uzyskać więcej informacji na temat możliwości przechodzenia z serwerów programu Office 2007, zobacz Zasoby pomocne przy uaktualnieniu serwerów i klientów programu [Office 2007](upgrade-from-office-2007-servers-and-products.md). Zwróć uwagę Project że program Project nie obsługuje konfiguracji hybrydowej, ponieważ program Project Server i Project Online nie mogą udostępniać tej samej puli zasobów. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Ważne zagadnienia związane z migracją z programu Project Server 2007

Plan migracji z programu Project Server 2007 można rozważyć następujące kwestie:
  
- **Uzyskiwanie pomocy od partnera firmy Microsoft** — uaktualnienie programu Project Server 2007 może być trudne i wymaga wiele przygotowań i planowania. Może to być szczególnie trudne, jeśli nie jesteś osobą, która s konfiguracji programu Project Server 2007. Na szczęście mogą Ci pomóc partnerzy firmy Microsoft, niezależnie od tego, czy zamierzasz przeprowadzić migrację do programu Project Server 2016, czy do Project Online. Wyszukaj partnera firmy Microsoft, który pomoże Ci w migracji w Centrum [partnerskim firmy Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Wyszukaj termin Gold *Project zarządzanie* portfelem, aby wyświetlić listę wszystkich partnerów firmy Microsoft, którzy mają doświadczenie w Project. 
    
- **Planowanie dostosowań —** wiele dostosowań w środowisku programu Project Server 2007 może nie działać podczas migracji do programu Project Server 2016 lub Project Online. Istnieją istotne różnice w architekturze Project Server między wersjami. Obsługiwane są również wymagane systemy operacyjne, serwery baz danych i obsługiwane przeglądarki sieci Web klienta. Zaplanuj, jak przetestować lub odbudować dostosowania w nowym środowisku. Planowanie pozwala także zastanowić się, czy wszystkie dostosowania są nadal potrzebne. Aby uzyskać więcej informacji, zobacz Tworzenie planu bieżących dostosowań podczas [uaktualniania do SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Czas i cierpliwość —** planowanie uaktualnienia, jego wykonanie i testowanie wymaga czasu i wysiłku, szczególnie w przypadku uaktualnienia do Project Server 2016. Na przykład w przypadku migracji z programu Project Server 2007 do programu Project Server 2016 należy najpierw przeprowadzić migrację do programu Project Server 2010, sprawdzić dane, a następnie wykonać te same kroki podczas migracji do każdej kolejnej wersji. Warto sprawdzić u partnera firmy Microsoft, ile będzie czekać i jakie będzie kosztować.
    
## <a name="migrate-to-project-online"></a>Migrowanie do Project Online

W przypadku migracji z programu Project Server 2007 do programu Project Online możesz wykonać następujące czynności w celu przeprowadzenia ręcznej migracji danych planu projektu:
  
1. Zapisz plany projektu z programu Project Server 2003 w formacie mpp.
    
2. W Project Professional 2013, Project Professional 2016 lub kliencie Project Online, otwórz każdy plik mpp, a następnie zapisz go i opublikuj w Project Online.
    
Konfigurację aplikacji Microsoft Project Web App (PWA) można utworzyć ręcznie Project Online. Możesz na przykład ponownie utworzyć wszystkie potrzebne pola niestandardowe lub kalendarze przedsiębiorstwa. Partnerzy firmy Microsoft mogą również pomóc w tym procesie.
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Wprowadzenie do usługi Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Jak skonfigurować i używać Project Online <br/> |
|[Project Online opisy usług](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Informacje na temat poszczególnych Project Online, które są dla Ciebie dostępne <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrowanie do nowszej lokalnej wersji programu Project Server

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można uzyskać dzięki migracji do Project Online. Rozumiemy jednak, że niektóre organizacje muszą przechowywać dane projektu w środowisku lokalnym. Jeśli zdecydujesz się przechowywać dane projektu lokalnie, możesz przeprowadzić migrację środowiska programu Project Server 2007 do programu Project Server 2010, Project Server 2013 lub Project Server 2016.
  
Jeśli nie możesz przeprowadzić migracji do Project Online, zalecamy przeprowadzenie migracji do Project Server 2016. Project Server 2016 zawiera wszystkie funkcje poprzednich wersji programu Project Server. Jego środowisko jest najbardziej zbliżone do funkcji dostępnych w Project Online, chociaż niektóre funkcje są dostępne tylko w Project Online.
  
Po każdej migracji należy sprawdzić, czy dane zostały pomyślnie zmigrowane.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Jak przeprowadzić migrację do Project Server 2016?

Różnice w architekturze Project Server 2007 i Project Server 2016 mogą uniemożliwiać bezpośrednią ścieżkę migracji. Dlatego musisz przeprowadzić migrację danych programu Project Server 2007 do każdej kolejnej wersji programu Project Server, aż dotrzesz do Project Server 2016.
  
Wykonaj poniższe czynności, aby Project Server 2016:
  
1. Migrowanie z Project Server 2007 do programu Project Server 2010.
    
2. Migrowanie z programu Project Serve 2010 do programu Project Server 2013.
    
3. Migrowanie z Project Server 2013 do programu Project Server 2016.
    
Po każdej migracji upewnij się, że dane zostały pomyślnie zmigrowane.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Krok 1. Migrowanie z Project Server 2007 do Project Server 2010

Aby uzyskać pełny opis uaktualniania programu Project Server 2007 do programu Project Server 2010, zobacz Uaktualnianie do [programu Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Project o uaktualnieniu do programu Project Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |High-level view of what you need to upgrade from Project Server 2007 to Project Server 2010 <br/> |
|[Planowanie uaktualnienia do programu Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Zagadnienia dotyczące planowania podczas uaktualniania programu Project Server 2007 do programu Project Server 2010, w tym wymagania systemowe  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Jak uaktualnić?

Aby uzyskać szczegółowe informacje, [zobacz Uaktualnianie do Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Należy jednak pamiętać, że istnieją dwie różne metody uaktualniania:
  
- **Uaktualnianie przez dołączanie baz danych:** Ta metoda uaktualnia tylko zawartość środowiska, a nie ustawienia konfiguracyjne. Jest ona wymagana w przypadku uaktualniania z programu Office Project Server 2007 wdrożonego na sprzęcie, który obsługuje tylko 32-bitowy system operacyjny serwera. Istnieją dwie metody uaktualniania przez dołączanie baz danych:
    
  - Pełne uaktualnianie przez dołączanie baz **danych —** migruje dane projektu przechowywane w bazach danych programu Office Project Server 2007 oraz dane witryny aplikacji Microsoft Project Web App przechowywane w bazie danych SharePoint zawartości.
    
  - **Podstawowe uaktualnianie *przez dołączanie baz danych*** — migruje tylko dane projektu przechowywane w bazach danych programu Project Server.
    
- **Uaktualnianie w miejscu**: Dane konfiguracji farmy i całej zawartości farmy są uaktualniane na istniejącym sprzęcie w ustalonej kolejności. Po rozpoczęciu procesu uaktualniania instalator przenosi całą farmę w tryb offline. Witryny sieci Web i Microsoft Project są niedostępne do czasu uaktualnienia, a następnie instalator ponownie uruchomi serwer. Po rozpoczęciu uaktualniania w miejscu nie można wstrzymać uaktualniania ani wrócić do poprzedniej wersji. Najlepiej jest wykonać obraz lustrzany środowiska produkcyjnego i uaktualnić go w miejscu do tego środowiska, a nie do środowiska produkcyjnego. 
    
Dodatkowe zasoby:
  
- [SuperFlow dla programu Microsoft Project Server 2010 Upgrade](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Migracja z Project Server 2007 do programu Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Zagadnienia związane z uaktualnianiem Project Web App składniki Web Part](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project Sdk (Software Development Kit)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>Krok 2. Migrowanie do Project Server 2013

Po pomyślnym zweryfikowaniu, że dane zostały pomyślnie zmigrowane, następnym krokiem jest przeprowadzenie migracji do programu Project Server 2013.
  
Aby uzyskać pełny opis tego, co należy zrobić, aby uaktualnić system z programu Project Server 2010 do programu Project Server 2013, zobacz Uaktualnianie do [programu Project Server 2013](/project/upgrade-to-project-server-2016). 
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Omówienie procesu uaktualniania do Project Server 2013](/project/upgrade-to-project-server-2016) <br/> |Omówienie uaktualniania programu Project Server 2010 do programu Project Server 2013  <br/> |
|[Planowanie uaktualnienia do programu Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |Zagadnienia dotyczące planowania podczas uaktualniania programu Project Server 2010 do programu Project Server 2013, w tym wymagania systemowe <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Co należy wiedzieć o uaktualnianiu do tej wersji

[Co nowego w uaktualnieniu do Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) zawiera opis istotnych zmian w uaktualnieniu do tej wersji. Najpowszechniejszymi z nich są: 
  
- Nie można uaktualnić w miejscu do programu Project Server 2013. Dołączanie baz danych jest jedyną metodą obsługiwaną podczas uaktualniania z programu Project Server 2010 do Project Server 2013.
    
- Proces uaktualniania nie tylko przekonwertuje dane programu Project Server 2010 na format programu Project Server 2013, ale również skonsoliduje cztery bazy danych programu Project Server 2010 w jedną Project Web App danych.
    
- W wersjach 2013 zarówno SharePoint Server, jak i Project Server zmieniły się na uwierzytelnianie oparte na oświadczeniach. Jeśli korzystasz z uwierzytelniania klasycznego, musisz wziąć pod uwagę ten czynnik podczas uaktualniania. Aby uzyskać więcej informacji, zobacz Migrowanie z uwierzytelniania w trybie klasycznym do uwierzytelniania opartego na oświadczeniach w [programie SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
Dodatkowe zasoby:
  
- [Omówienie procesu uaktualniania do programu Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Uaktualnianie baz danych i Project Web App witryn (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Microsoft Project procesu uaktualniania do serwera](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Wielka konsolidacja baz danych, Project z programu Server 2010 do 2013 w 8 łatwych krokach](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Krok 3. Migrowanie do Project Server 2016

Po sprawdzeniu, czy dane zostały pomyślnie zmigrowane, następnym krokiem jest przeprowadzenie migracji do Project Server 2016.
  
Aby uzyskać pełny opis tego, co należy zrobić, aby uaktualnić system z programu Project Server 2013 do wersji Project Server 2016, zobacz [Uaktualnianie do Project Server 2016](//project/upgrading-to-project-server-2016).
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Omówienie procesu Project Server 2016 uaktualniania](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Omówienie uaktualniania programu Project Server 2013 do wersji Project Server 2016 <br/> |
|[Planowanie uaktualnienia do Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Zagadnienia dotyczące planowania podczas uaktualniania programu Project Server 2013 do wersji Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Co należy wiedzieć o uaktualnianiu do tej wersji

[Co należy wiedzieć o uaktualnieniu Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) informuje o kilku istotnych zmianach dotyczących uaktualniania dla tej wersji, takich jak:
  
- Podczas tworzenia środowiska programu Project Server 2016, do którego będą migrowane dane z programu Project Server 2013, pliki instalacyjne programu Project Server 2016 są zawarte w programie SharePoint Server 2016. Aby uzyskać więcej informacji, zobacz [Wdrażanie Project Server 2016](/project/deploy-project-server-2016).
    
- Plany zasobów są przestarzałe w programie Project Server 2016. Plany Project Server 2013 zostaną poddane migracji do zasób w programie Project Server 2016 i w programie Project Online. Aby [uzyskać więcej informacji, zobacz Omówienie: angażowanie](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) zasobów. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrowanie z programu Portfolio Server 2007

Project Portfolio Server 2007 został użyty z Project Server 2007 do strategii, priorytetu i optymalizacji portfela. Po tej wersji nie utworzono Project programu Portfolio Server. Funkcje zarządzania portfelem są jednak dostępne w Project Server 2016 i Premium wersji Project Online. Danych z programu Project Portfolio Server 2007 także nie można migrować. Dane, takie jak czynniki biznesowe, należy ponownie utworzyć.
  
Inne zasoby:
  
- [Project Online opisy usług:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) zobacz funkcje zarządzania portfelem zawarte w Project Server 2016 i Project Online Premium.
    
- [Microsoft Office Project migracji do programu Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Tematy pokrewne

[SharePoint dotyczące zakończenia pomocy technicznej dla programu SharePoint Server 2007 Przewodnik](sharepoint-2007-end-of-support.md)
  
[Zasoby pomocne w uaktualnieniu serwerów i klientów programu Office 2007](upgrade-from-office-2007-servers-and-products.md)
