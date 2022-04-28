---
title: plan zakończenia wsparcia dla serwera Project Server 2007
ms.author: efrene
author: efrene
manager: scotv
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
description: 10 października 2017 r. zakończono wsparcie dla Project Server 2007, Project Portfolio Server i Project 2007 r. Użyj tego artykułu, aby zaplanować uaktualnienie teraz.
ms.openlocfilehash: 1c46a0c422a0eb66b4991589a0996092c40f5fba
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090192"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>plan zakończenia wsparcia dla serwera Project Server 2007

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Obsługa serwerów i aplikacji Office 2007 została zakończona w 2017 r. i należy rozważyć plany migracji. Jeśli obecnie używasz programu Project Server 2007 i powiązanych produktów, zwróć uwagę na następujące daty zakończenia pomocy technicznej:
  
|**Produkt**|**Data zakończenia wsparcia technicznego**|
|:-----|:-----|
|Project Server 2007  <br/> |10 października 2017 r.  <br/> |
|Project Portfolio Server 2007  <br/> |10 października 2017 r.  <br/> |
|Project 2007 Standard  <br/> |10 października 2017 r.  <br/> |
|Project 2007 r. Professional  <br/> |10 października 2017 r.  <br/> |
   
Aby uzyskać więcej informacji na temat serwerów Office 2007 osiągających wycofanie, zobacz [Uaktualnianie z serwerów Office 2007 i produktów klienckich](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, podczas którego otrzymują nowe funkcje, poprawki błędów, poprawki zabezpieczeń itd. Ten cykl życia zazwyczaj trwa 10 lat od początkowej wersji produktu. Koniec tego cyklu życia jest określany jako koniec wsparcia technicznego produktu. Ponieważ Project Server 2007 osiągnął koniec wsparcia 10 października 2017 r., firma Microsoft nie zapewnia już:
  
- Pomoc techniczna dotycząca problemów, które mogą wystąpić.
    
- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
    
- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.
    
- Aktualizacje stref czasowych.
    
Instalacja programu Project Server 2007 będzie kontynuowana po tej dacie. Jednak ze względu na wymienione wcześniej zmiany zdecydowanie zalecamy migrację z serwera Project Server 2007 tak szybko, jak to możliwe.
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Jeśli używasz programu Project Server 2007, musisz zapoznać się z opcjami migracji, które są następujące:
  
- Migrowanie do Project Online
    
- Migrowanie do nowszej lokalnej wersji serwera Project Server (najlepiej Project Server 2016)
    
|**Dlaczego wolałbym przeprowadzić migrację do Project Online**|**Dlaczego wolałbym przeprowadzić migrację do Project Server 2016**|
|:-----|:-----|
| Mam użytkowników mobilnych.  <br/> <br/>Koszty migracji są istotnym problemem (sprzęt, oprogramowanie, godziny i nakład pracy do zaimplementowania). <br/><br/>  Po migracji koszty utrzymania środowiska są głównym problemem (na przykład aktualizacje automatyczne, gwarantowany czas pracy itd.).  <br/> | Reguły biznesowe uniemożliwiają mi prowadzenie działalności w chmurze.<br/><br/>  Potrzebuję kontroli nad aktualizacjami środowiska.  |
   
> [!NOTE]
> Aby uzyskać więcej informacji na temat opcji przenoszenia z serwerów Office 2007, zobacz [Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md). Należy pamiętać, że Project Server nie obsługuje konfiguracji hybrydowej, ponieważ Project Server i Project Online nie mogą współużytkować tej samej puli zasobów. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Ważne zagadnienia podczas migracji z programu Project Server 2007

Podczas planowania migracji z programu Project Server 2007 należy wziąć pod uwagę następujące kwestie:
  
- **Uzyskaj pomoc od partnera firmy Microsoft** — uaktualnienie z Project Server 2007 może być trudne i wymaga dużego przygotowania i planowania. Może to być szczególnie trudne, jeśli nie jesteś osobą, która pierwotnie skonfigurowała Project Server 2007. Na szczęście są partnerzy firmy Microsoft, którzy mogą pomóc, niezależnie od tego, czy planujesz migrację do Project Server 2016, czy do Project Online. Wyszukaj partnera firmy Microsoft, który pomoże Ci w migracji w [Centrum partnerskim firmy Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Wyszukaj termin *Gold Project and Portfolio Management*, aby wyświetlić listę wszystkich partnerów firmy Microsoft, którzy mają doświadczenie w Project. 
    
- **Planowanie dostosowań** — wiele dostosowań wprowadzonych w środowisku Project Server 2007 może nie działać podczas migracji do Project Server 2016 lub Project Online. Istnieją znaczne różnice w architekturze serwera Project między wersjami. Wymagane systemy operacyjne, serwery baz danych i obsługiwane przeglądarki sieci Web klienta również różnią się. Planowanie sposobu testowania lub ponownego kompilowania dostosowań dla nowego środowiska. Planowanie zapewnia również dobrą okazję do rozważenia, czy każde dostosowanie jest nadal potrzebne. Aby uzyskać więcej informacji, zobacz [Create a plan for current customizations during upgrade to SharePoint 2013 (Tworzenie planu dla bieżących dostosowań podczas uaktualniania do SharePoint 2013 r.).](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013) 
    
- **Czas i cierpliwość** — planowanie, wykonywanie i testowanie uaktualniania zajmie trochę czasu i wysiłku, zwłaszcza w przypadku uaktualnienia do Project Server 2016. Na przykład w przypadku migracji z serwera Project Server 2007 do Project Server 2016 należy najpierw przeprowadzić migrację do serwera Project Server 2010, sprawdzić dane, a następnie wykonać to samo podczas migracji do każdej kolejnej wersji. Możesz skontaktować się z partnerem firmy Microsoft, aby uzyskać oszacowanie czasu i kosztów.
    
## <a name="migrate-to-project-online"></a>Migrowanie do Project Online

Jeśli zdecydujesz się przeprowadzić migrację z programu Project Server 2007 do Project Online, możesz wykonać następujące czynności, aby ręcznie przeprowadzić migrację danych planu projektu:
  
1. Zapisz plany projektu z serwera Project Server 2003 w formacie mpp.
    
2. W Project Professional 2013 r. Project Professional 2016 lub Project Online Desktop Client otwórz każdy plik mpp, a następnie zapisz go i opublikuj w Project Online.
    
Konfigurację Microsoft Project Web App (PWA) można ręcznie utworzyć w Project Online. Na przykład utwórz ponownie wszystkie wymagane pola niestandardowe lub kalendarze przedsiębiorstwa. Partnerzy firmy Microsoft mogą również pomóc w tym procesie.
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Wprowadzenie do usługi Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Jak skonfigurować i użyć Project Online <br/> |
|[Opisy usługi Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Informacje o różnych planach Project Online, które są dostępne dla Ciebie <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrowanie do nowszej lokalnej wersji serwera Project Server

Jesteśmy przekonani, że uzyskujesz najlepszą wartość i środowisko użytkownika, migrując do Project Online. Rozumiemy jednak również, że niektóre organizacje muszą przechowywać dane projektu w środowisku lokalnym. Jeśli zdecydujesz się zachować lokalne dane projektu, możesz przeprowadzić migrację środowiska Project Server 2007 do Project Server 2010, Project Server 2013 lub Project Server 2016.
  
Jeśli nie możesz przeprowadzić migracji do Project Online, zalecamy przeprowadzenie migracji do Project Server 2016. Project Server 2016 zawiera wszystkie funkcje poprzednich wersji programu Project Server. Najbardziej pasuje do środowiska dostępnego w Project Online, chociaż niektóre funkcje są dostępne tylko w Project Online.
  
Po każdej migracji należy sprawdzić, czy dane zostały pomyślnie zmigrowane.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Jak mogę migrować do Project Server 2016?

Różnice w architekturze między programem Project Server 2007 i Project Server 2016 uniemożliwiają bezpośrednią ścieżkę migracji. Dlatego należy przeprowadzić migrację danych Project Server 2007 do każdej kolejnej wersji serwera Project, dopóki nie osiągniesz Project Server 2016.
  
Wykonaj następujące kroki, aby Project Server 2016:
  
1. Migrowanie z programu Project Server 2007 do Project Server 2010.
    
2. Migrowanie z usługi Project Serve 2010 do serwera Project Server 2013.
    
3. Migrowanie z programu Project Server 2013 do Project Server 2016.
    
Po każdej migracji upewnij się, że dane zostały pomyślnie zmigrowane.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Krok 1. Migracja z Project Server 2007 do Project Server 2010

Aby uzyskać kompleksowy opis czynności, które należy wykonać w celu uaktualnienia z Project Server 2007 do Project Server 2010, zobacz [Uaktualnianie do Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Project Server 2010 upgrade overview (Omówienie uaktualniania programu Project Server 2010)](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |Ogólny widok tego, co należy zrobić, aby przeprowadzić uaktualnienie z Project Server 2007 do Project Server 2010 <br/> |
|[Planowanie uaktualnienia do serwera Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Zagadnienia dotyczące planowania podczas uaktualniania z Project Server 2007 do Project Server 2010, w tym wymagania systemowe  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Jak mogę uaktualnienie?

Aby uzyskać szczegółowe informacje, zobacz [Uaktualnianie do Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Należy jednak pamiętać, że istnieją dwie różne metody, których można użyć do uaktualnienia:
  
- **Uaktualnienie dołączania bazy danych:** Ta metoda uaktualnia tylko zawartość środowiska, a nie ustawienia konfiguracji. Jest to wymagane, jeśli uaktualniasz program z Office Project Server 2007 wdrożony na sprzęcie, który obsługuje tylko 32-bitowy system operacyjny serwera. Istnieją dwa typy metod uaktualniania dołączania bazy danych:
    
  - ***Pełne uaktualnienie* dołączania bazy danych** — migruje dane projektu przechowywane w bazach danych programu Office Project Server 2007 oraz Microsoft Project danych witryny aplikacji internetowej przechowywanych w bazie danych zawartości SharePoint.
    
  - ***Uaktualnianie rdzeni* dołączania bazy danych** — migruje tylko dane projektu przechowywane w bazach danych serwera Project.
    
- **Uaktualnienie w miejscu**: dane konfiguracji farmy i całej zawartości w farmie są uaktualnione na istniejącym sprzęcie w stałej kolejności. Po rozpoczęciu procesu uaktualniania konfiguracja przenosi całą farmę w tryb offline. Witryny sieci Web i witryny Microsoft Project web app są niedostępne do czasu zakończenia uaktualnienia, a następnie instalator ponownie uruchamia serwer. Po rozpoczęciu uaktualnienia w miejscu nie można wstrzymać uaktualnienia ani wycofać poprzedniej wersji. Najlepiej utworzyć dublowany obraz środowiska produkcyjnego i przeprowadzić uaktualnienie w miejscu do tego środowiska, a nie w środowisku produkcyjnym. 
    
Dodatkowe zasoby:
  
- [SuperFlow dla uaktualnienia Microsoft Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Migracja z programu Project Server 2007 do Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Zagadnienia dotyczące uaktualniania Project Web App składniki Web Part](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [zestaw Project Software Development Kit (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>Krok 2. Migrowanie do serwera Project Server 2013

Po sprawdzeniu, czy dane zostały pomyślnie zmigrowane, następnym krokiem jest migracja do Project Server 2013.
  
Aby uzyskać kompleksowy opis czynności niezbędnych do uaktualnienia z Project Server 2010 do Project Server 2013, zobacz [Uaktualnianie do Project Server 2013](/project/upgrade-to-project-server-2016). 
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Omówienie procesu uaktualniania serwera Project Server 2013](/project/upgrade-to-project-server-2016) <br/> |Omówienie czynności, które należy zrobić, aby przeprowadzić uaktualnienie z programu Project Server 2010 do Project Server 2013  <br/> |
|[Planowanie uaktualnienia do Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |Zagadnienia dotyczące planowania podczas uaktualniania z Project Server 2010 do Project Server 2013, w tym wymagania systemowe <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Co należy wiedzieć o uaktualnianiu do tej wersji

[Co nowego w uaktualnieniu programu Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) opisano ważne zmiany dotyczące uaktualniania dla tej wersji. Najbardziej godne uwagi są: 
  
- Nie ma uaktualnienia w miejscu do Project Server 2013. Metoda dołączania bazy danych jest jedyną obsługiwaną metodą uaktualniania z Project Server 2010 do Project Server 2013.
    
- Proces uaktualniania nie tylko przekonwertuje dane Project Server 2010 na format Project Server 2013, ale także skonsoliduje cztery bazy danych Project Server 2010 w pojedynczą bazę danych Project Web App.
    
- W wersjach 2013 zarówno serwer SharePoint, jak i serwer Project zostały zmienione na uwierzytelnianie oparte na oświadczeniach. Jeśli używasz uwierzytelniania klasycznego, musisz wziąć pod uwagę ten czynnik w przypadku uaktualnienia. Aby uzyskać więcej informacji, zobacz [Migrowanie z trybu klasycznego do uwierzytelniania opartego na oświadczeniach w SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) r.
    
Dodatkowe zasoby:
  
- [Omówienie procesu uaktualniania do Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Uaktualnianie baz danych i Project Web App zbiorów witryn (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Diagram procesu uaktualniania serwera Microsoft Project](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Wielka konsolidacja bazy danych, migracja Project Server 2010 do 2013 w 8 prostych krokach](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Krok 3. Migrowanie do Project Server 2016

Po sprawdzeniu, czy dane zostały pomyślnie zmigrowane, następnym krokiem jest migracja do Project Server 2016.
  
Aby uzyskać kompleksowy opis czynności niezbędnych do uaktualnienia z Project Server 2013 do Project Server 2016, zobacz [Uaktualnianie do Project Server 2016](//project/upgrading-to-project-server-2016).
  
Kluczowe zasoby:
  
|**Zasób**|**Opis**|
|:-----|:-----|
|[Omówienie procesu uaktualniania Project Server 2016](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Omówienie czynności, które należy zrobić, aby przeprowadzić uaktualnienie z programu Project Server 2013 do Project Server 2016 <br/> |
|[Planowanie uaktualnienia do Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Zagadnienia dotyczące planowania uaktualniania z programu Project Server 2013 do Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Co należy wiedzieć o uaktualnianiu do tej wersji

[Informacje, które należy wiedzieć o uaktualnieniu Project Server 2016](/project/plan-for-upgrade-to-project-server-2016), informują o istotnych zmianach dotyczących uaktualniania tej wersji, w tym:
  
- Podczas tworzenia środowiska Project Server 2016, do którego zostaną zmigrowane dane Project Server 2013, pliki instalacyjne Project Server 2016 zostaną uwzględnione w programie SharePoint Server 2016. Aby uzyskać więcej informacji, zobacz [Wdrażanie Project Server 2016](/project/deploy-project-server-2016).
    
- Plany zasobów są przestarzałe w Project Server 2016. Plany zasobów serwera Project Server 2013 zostaną zmigrowane do usługi Resource Engagements w Project Server 2016 i w Project Online. Aby uzyskać więcej informacji, zobacz [Omówienie: Zakontraktowanie zasobów](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrowanie z programu Portfolio Server 2007

Project Portfolio Server 2007 był używany z serwerem Project Server 2007 na potrzeby strategii portfela, priorytetyzacji i optymalizacji. Po tej wersji nie utworzono żadnych dodatkowych wersji programu Project Portfolio Server. Jednak funkcje zarządzania portfelem są dostępne w Project Server 2016 i Premium wersji Project Online. Nie można jednak migrować danych z serwera Project Portfolio Server 2007. Dane, takie jak czynniki biznesowe, będą musiały zostać ponownie utworzone.
  
Inne zasoby:
  
- [Project Online Opisy usług:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) zobacz funkcje zarządzania portfelem dołączone do Project Server 2016 i Project Online Premium.
    
- [przewodnik migracji programu Microsoft Office Project Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Tematy pokrewne

[SharePoint Server 2007 — plan pomocy technicznej](sharepoint-2007-end-of-support.md)
  
[Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)
