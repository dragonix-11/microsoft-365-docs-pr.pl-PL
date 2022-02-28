---
title: Project zakończenia obsługi programu Project Server 2013 — przewodnik
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: Wsparcie techniczne dla Project Server 2013 kończy się 11 kwietnia 2023 r. Ten artykuł jest przewodnikiem po uaktualnieniu do Project Online lub nowszej wersji programu Project Server lokalnie.
ms.openlocfilehash: 5a9ae38e819dfdb8f9cc2ca3719dccea2d33fa3e
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2021
ms.locfileid: "62990523"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Project dotyczące zakończenia pomocy technicznej dla programu Project Server 2013

Project 11 kwietnia 2023 r. zakończy się wsparcie techniczne **dla programu Server 2013**. Jeśli obecnie używasz programu Project Server 2013, pamiętaj, że aplikacja Project 2013 ma również te same daty zakończenia obsługi.

## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Niemal wszystkie produkty firmy Microsoft mają cykl życia pomocy technicznej, w trakcie którego są one dostępne nowe funkcje, poprawki i aktualizacje zabezpieczeń. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Po Project 11 kwietnia 2023 r. po zakończeniu świadczenia pomocy technicznej dla programu Project Server 2013 firma Microsoft nie będzie już zapewniać:

- pomoc techniczną w zakresie mogącego wystąpić problemów;

- Poprawki błędów dotyczące wykrytych problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dotyczące wykrytych luk, które mogą na narażenie serwera na naruszenie bezpieczeństwa.

- Aktualizacje stref czasowych.

Instalacja programu Project Server 2013 będzie nadal działać po tym dniu. Jednak z powodu zmian wymienionych wcześniej zdecydowanie zalecamy możliwie jak najszybciej migrację z programu Project Server 2013.

## <a name="what-are-my-options"></a>Jakie są moje opcje?

Dostępne są następujące opcje migracji:

- Migrowanie do Project Online

- Migrowanie do nowszej lokalnej wersji programu Project Server (najlepiej Project Server Subscription Edition)

|Dlaczego warto migrować do programu Project Server 2019?|Dlaczego warto migrować do Project Online?|
|---|---|
|Reguły biznesowe ograniczają moje możliwości prowadzenia firmy w chmurze.  <br/><br/>  Potrzebuję kontroli nad aktualizacjami środowiska.|Mam użytkowników mobilnych lub zdalnych.<br/><br/>  Koszty migracji serwerów lokalnych są istotnymi problemami (sprzęt, oprogramowanie, czas i nakład pracy związanej z wdrożeniem itp.). <br/><br/>  Koszty utrzymania środowiska po migracji mogą stanowić problem (na przykład aktualizacje automatyczne, gwarantowany czas beza dostępności itp.).|

> [!NOTE]
> Project Server nie obsługuje konfiguracji hybrydowej, ponieważ program Project Server i Project Online nie mogą udostępniać tej samej puli zasobów.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>Ważne zagadnienia dotyczące migracji z programu Project Server 2013

Plan migracji z programu Project Server 2013 można rozważyć następujące kwestie:

- **Uzyskiwanie pomocy od dostawcy rozwiązań firmy Microsoft** — uaktualnienie programu Project Server 2013 może stanowić wyzwanie. Wymaga ona wiele przygotowań i planowania. Może to być szczególnie trudne, jeśli nie jesteś osobą, która pierwotnie schowała program Project Server 2013. Dostawcy rozwiązań firmy Microsoft są dostępni, niezależnie od tego, czy zamierzasz przeprowadzić migrację do programu Project Server Subscription Edition, czy Project Online. Wyszukaj dostawcę rozwiązań w Centrum [dostawców rozwiązań firmy Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Czas i cierpliwość —** planowanie uaktualnienia, jego wykonanie i testowanie będzie wymagać wiele czasu i wysiłku, szczególnie w przypadku uaktualnienia do programu Project Server Subscription Edition. W przypadku migracji z programu Project Server 2013 do programu Project Server Subscription Edition należy najpierw przeprowadzić migrację do programu Project Server 2016, sprawdzić dane, a następnie do programu Project Server Subscription Edition. Warto sprawdzić u dostawcy rozwiązań firmy Microsoft ramy czasowe i szacowany koszt, jaki może okazać się pomocny.

## <a name="migrate-to-project-online"></a>Migrowanie do Project Online

Jeśli zdecydujesz się na migrację z programu Project Server 2013 do programu Project Online, możesz wykonać następujące czynności, aby ręcznie przeprowadzić migrację danych planu projektu:

1. Zapisz plany projektu z programu Project Server 2013 w formacie mpp.

2. Przy użyciu Project Professional 2016, Project Professional 2019 lub klienta klasycznego programu Project Online otwórz każdy plik mpp, a następnie zapisz go i opublikuj w Project Online.

Konfigurację pliku można utworzyć ręcznie PWA w programie Project Online (na przykład ponownie utworzyć wszystkie wymagane pola niestandardowe lub kalendarze przedsiębiorstwa). Dostawcy rozwiązań firmy Microsoft mogą również pomóc w tym procesie.

Kluczowe zasoby:

|Zasób|Opis|
|---|---|
|[Wprowadzenie do usługi Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Jak skonfigurować i używać Project Online|
|[Opis usługi Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informacje o różnych dostępnych Project Online planach|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrowanie do nowszej lokalnej wersji programu Project Server

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można uzyskać dzięki migracji do Project Online. Rozumiemy jednak, że niektóre organizacje muszą przechowywać dane projektu lokalnie. Jeśli zdecydujesz się przechowywać dane projektu lokalnie, możesz przeprowadzić migrację środowiska programu Project Server 2013 do programu Project Server 2016, Project Server 2019 lub Project Server Subscription Edition.

Jeśli nie możesz przeprowadzić migracji do programu Project Online, zalecamy przeprowadzenie migracji do programu Project Server Subscription Edition, który zawiera większość kluczowych funkcji z poprzednich wersji programu Project Server. Jego środowisko jest najbardziej zbliżone do funkcji dostępnych w programach Project Online, chociaż niektóre funkcje są dostępne tylko w Project Online. Weź pod uwagę następujące dodatkowe czynniki:

- Project Server Subscription Edition wprowadza model ciągłej aktualizacji, który eliminuje konieczność wprowadzania nowych wersji głównych programu Project Server w przyszłości.
- Wsparcie Project Server 2016 i 2019 r. zakończy się 14 lipca 2026 r. Jeśli przeprowadzasz migrację do jednej z tych wersji, musisz zaplanować kolejne uaktualnienie w ciągu trzech lat. Aby uzyskać więcej informacji, zobacz strony cyklu życia pomocy technicznej zarówno [dla roku 2016](/lifecycle/products/project-server-2016) , jak [i 2019](/lifecycle/products/project-server-2019).

Po ukończeniu każdej migracji upewnij się, że migracja danych została ukończona pomyślnie.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>Jak przeprowadzić migrację do programu Project Server Subscription Edition?

Różnice w architekturze wersji Project Server 2013 i Project Server Subscription Edition uniemożliwiają bezpośrednią ścieżkę migracji. W związku z tym należy najpierw przeprowadzić migrację danych programu Project Server 2013 do programu Project Server 2016, a następnie do programu Project Server Subscription Edition. 

1. Migrowanie do Project Server 2016.

2. Migrowanie z Project Server 2016 do Project Server Subscription Edition.

Po ukończeniu każdej migracji upewnij się, że migracja danych została ukończona pomyślnie.

### <a name="step-1-migrate-to-project-server-2016"></a>Krok 1. Migrowanie do Project Server 2016

Aby uzyskać pełne informacje na temat uaktualniania programu Project Server 2013 do wersji Project Server 2016, zobacz [Uaktualnianie do Project Server 2016](/project/upgrade-to-project-server-2016).

Kluczowe zasoby:

- [Omówienie procesu uaktualniania Project Server 2016](/project/upgrade-to-project-server-2016): Ogólne omówienie uaktualniania programu Project Server 2013 do wersji Project Server 2016.
- [Planowanie uaktualnienia do wersji Project Server 2016](/project/plan-for-upgrade-to-project-server-2016): Przyjrzyj się kwestii dotyczących planowania podczas uaktualniania programu Project Server 2013 do wersji Project Server 2016 z wymaganiami systemowymi.
- [Uaktualnianie do Project Server 2016](/project/upgrading-to-project-server-2016): Zobacz szczegółowe instrukcje dotyczące procesu uaktualniania.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>Krok 2. Migrowanie do programu Project Server Subscription Edition

Po zakończeniu migracji do programu Project Server 2016 i sprawdzeniu, czy migracja danych została ukończona pomyślnie, następnym krokiem jest przeprowadzenie migracji do programu Project Server Subscription Edition.

Aby uzyskać więcej informacji, [zobacz Uaktualnianie do Project Server Subscription Edition](/project/upgrade-project-server-subscription-edition).

Kluczowe zasoby:

- [Omówienie procesu uaktualniania programu Project Server Subscription Edition](/project/overview-project-server-subscription-edition-upgrade-process): Dowiedz się, co należy zrobić, aby uaktualnić program Project Server 2013 do wersji Project Server 2016.
- [Planowanie uaktualnienia do programu Project Server Subscription Edition](/Project/plan-upgrade-project-server-subscription-edition): Przyjrzyj się kwestiiom planowania, które należy rozważyć podczas uaktualniania programu Project Server 2013 do wersji Project Server 2016.
- [Uaktualnianie do Project Server Subscription Edition](/project/how-to-upgrade-project-server-subscription-edition): Zobacz szczegółowe instrukcje dotyczące procesu uaktualniania.


