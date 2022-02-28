---
title: Project zakończenia obsługi technicznej dla programu Project Server 2010 — przewodnik
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
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
description: Wsparcie techniczne dla Project Server 2010 kończy się 13 kwietnia 2021 r. Ten artykuł jest przewodnikiem po uaktualnieniu do Project Online lub nowszej wersji programu Project Server lokalnie.
ms.openlocfilehash: 9d04df22af0a0614270907f4ad4026324b026211
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988442"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project dotyczące zakończenia pomocy technicznej dla programu Project Server 2010

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Project 13 kwietnia 2021 r. zakończy się wsparcie techniczne dla **programu Server 2010**. Ta data została przedłużona od poprzedniej daty zakończenia obsługi, 13 października 2020 r. Jeśli obecnie używasz programu Project Server 2010, pamiętaj, że te powiązane produkty mają następujące daty zakończenia obsługi:

|Rezultat |Data zakończenia pomocy technicznej|
|---|---|
|Project 2010 Standard|13 października 2020 r.|
|Project 2010 Professional|13 października 2020 r.|

Aby uzyskać więcej informacji na temat zakończenia wsparcia technicznego, zobacz [Uaktualnianie serwerów i produktów Office 2010](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Niemal wszystkie produkty firmy Microsoft mają cykl życia pomocy technicznej, w trakcie którego są one dostępne nowe funkcje, poprawki i aktualizacje zabezpieczeń. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Po Project 13 kwietnia 2021 r. program Project Server 2010 nie będzie już zapewniał:

- pomoc techniczną w zakresie mogącego wystąpić problemów;

- Poprawki błędów dotyczące wykrytych problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dotyczące wykrytych luk, które mogą na narażenie serwera na naruszenie bezpieczeństwa.

- Aktualizacje stref czasowych.

Instalacja programu Project Server 2010 będzie nadal działać po upływie tego terminu. Jednak z powodu zmian wymienionych wcześniej zdecydowanie zalecamy możliwie jak najszybciej migrację z programu Project Server 2010.

## <a name="what-are-my-options"></a>Jakie są moje opcje?

Dostępne są następujące opcje migracji:

- Migrowanie do Project Online

- Migrowanie do nowszej lokalnej wersji programu Project Server (najlepiej Project Server 2019)

Oto dwa sposoby uniknięcia zakończenia obsługi programu Project Server 2010.

![Project uaktualnianie do programu Server 2010.](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Dlaczego warto migrować do programu Project Server 2019?|Dlaczego warto migrować do Project Online?|
|---|---|
|Reguły biznesowe ograniczają moje możliwości prowadzenia firmy w chmurze.  <br/><br/>  Potrzebuję kontroli nad aktualizacjami środowiska.|Mam użytkowników mobilnych lub zdalnych.<br/><br/>  Koszty migracji serwerów lokalnych są istotnymi problemami (sprzęt, oprogramowanie, czas i nakład pracy związanej z wdrożeniem itp.). <br/><br/>  Koszty utrzymania środowiska po migracji mogą stanowić problem (na przykład aktualizacje automatyczne, gwarantowany czas beza dostępności itp.).|

> [!NOTE]
> Aby uzyskać więcej informacji na temat opcji migracji, zobacz Zasoby pomocne przy uaktualnieniu z serwerów i klientów Office [2010](upgrade-from-office-2010-servers-and-products.md). Zwróć uwagę Project że program Project nie obsługuje konfiguracji hybrydowej, ponieważ program Project Server i Project Online nie mogą korzystać z tej samej puli zasobów.

### <a name="what-are-my-options-for-project-client"></a>Jakie mam opcje dla Project klienta?

Jeśli korzystasz z programu Project Professional 2010 lub Project Standard 2010, masz następujące opcje:

- Przechodzenie do nowszej wersji Project Professional lub Project Standard
- Przechodzenie do rozwiązania online, takiego Project Online lub Project dla sieci Web

#### <a name="move-to-a-newer-version-of-project-client"></a>Przechodzenie do nowszej wersji Project klienta

W przypadku migracji z programu Project Standard 2010 możesz przejść do nowszej wersji programu Project Standard (Project Standard 2016 lub Project Standard 2019). Zalecamy przejście do najnowszej wersji, aby korzystać z najnowszych funkcji. Migracja do mniej aktualnej wersji (Project Standard 2016) oznacza również, że trzeba będzie ponownie przeprowadzić migrację wcześniej.

Podobnie w przypadku migracji z programu Project Professional 2010 możesz przejść do nowszej wersji (w wersji Project Professional 2019 lub Project Professional 2016). Ponownie przejdź do najnowszej wersji, jeśli to możliwe. Jeśli łączysz się Project Professional z programem Project Server, migruj do wersji programu Project Professional, która łączy się z używaną wersją programu Project Server.

Project Professional 2010 można również przeprowadzić migrację do klienta Project Online desktop, który jest opartą na subskrypcji wersją programu Project Professional 2019. Jest on dołączony do Project (plan 3) i Project (plan 5) subskrypcji.

#### <a name="move-to-an-online-solution"></a>Przechodzenie do rozwiązania online

Możesz również przeprowadzić migrację z Project Professional 2010 lub Project Standard 2010 do opartego na subskrypcji rozwiązania online opartego na Project subskrypcji. Zarówno Project (plan 3), jak i Plan 5 Project Online i najnowszą ofertę chmury, Project [dla sieci Web](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Obie te funkcje oferują nowe funkcje i korzyści, które warto poznać.

Aby uzyskać więcej informacji na temat funkcji i licencji, [Microsoft Project opis usługi](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Ważne zagadnienia dotyczące migracji z programu Project Server 2010

Plan migracji z programu Project Server 2010 można rozważyć następujące kwestie:

- **Uzyskiwanie pomocy od dostawcy rozwiązań firmy Microsoft** — uaktualnienie programu Project Server 2010 może stanowić wyzwanie. Wymaga ona wiele przygotowań i planowania. Może to być szczególnie trudne, jeśli nie jesteś osobą, która pierwotnie schowała program Project Server 2010. Dostawcy rozwiązań firmy Microsoft są dostępni, niezależnie od tego, czy planujesz migrację do programu Project Server 2019, czy do programu Project Online. Wyszukaj dostawcę rozwiązań w Centrum [dostawców rozwiązań firmy Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Planowanie dostosowań —** dostosowania w środowisku programu Project Server 2010 mogą nie działać podczas migracji do programu Project Server 2019 lub Project Online. Istnieją istotne różnice w architekturze Project Server między wersjami. Różnią się również wymagane systemy operacyjne, serwery baz danych i przeglądarki sieci Web, które działają z wersjami. Zaplanuj, jak przetestować lub odbudować dostosowania w nowym środowisku. Skorzystaj z tej możliwości, aby określić, czy określone dostosowania są nadal potrzebne. Aby uzyskać więcej informacji, zobacz Tworzenie planu bieżących dostosowań podczas [uaktualniania do SharePoint 2013](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Czas i cierpliwość —** planowanie, wykonywanie i testowanie uaktualnienia będzie wymagać wiele czasu i wysiłku, szczególnie w przypadku uaktualnienia do programu Project Server 2019. W przypadku migracji z programu Project Server 2010 do programu Project Server 2019 należy najpierw przeprowadzić migrację do programu Project Server 2013, sprawdzić dane, a następnie przeprowadzić migrację do programu Project Server 2016, a następnie do programu Project Server 2019. Warto sprawdzić u dostawcy rozwiązań firmy Microsoft ramy czasowe i szacowany koszt, jaki może okazać się pomocny.

## <a name="migrate-to-project-online"></a>Migrowanie do Project Online

Jeśli zdecydujesz się na migrację z programu Project Server 2010 do programu Project Online, możesz wykonać następujące czynności, aby ręcznie przeprowadzić migrację danych planu projektu:

1. Zapisz plany projektu z programu Project Server 2010 w formacie mpp.

2. Przy użyciu Project Professional 2016, Project Professional 2019 lub klienta klasycznego programu Project Online otwórz każdy plik mpp, a następnie zapisz go i opublikuj w Project Online.

Konfigurację pliku można utworzyć ręcznie PWA w programie Project Online (na przykład ponownie utworzyć wszystkie wymagane pola niestandardowe lub kalendarze przedsiębiorstwa). Dostawcy rozwiązań firmy Microsoft mogą również pomóc w tym procesie.

Kluczowe zasoby:

|Zasób|Opis|
|---|---|
|[Wprowadzenie do usługi Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Jak skonfigurować i używać Project Online|
|[Opis usługi Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informacje o różnych dostępnych Project Online planach|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrowanie do nowszej lokalnej wersji programu Project Server

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można uzyskać dzięki migracji do Project Online. Rozumiemy jednak, że niektóre organizacje muszą przechowywać dane projektu lokalnie. Jeśli zdecydujesz się przechowywać dane projektu lokalnie, możesz przeprowadzić migrację środowiska programu Project Server 2010 do programu Project Server 2013, Project Server 2016 lub Project Server 2019.

Jeśli nie możesz przeprowadzić migracji do programu Project Online, zalecamy przeprowadzenie migracji do programu Project Server 2019. Project Server 2019 zawiera większość kluczowych funkcji w poprzednich wersjach programu Project Server. Jego środowisko jest najbardziej zbliżone do funkcji dostępnych w programach Project Online, chociaż niektóre funkcje są dostępne tylko w Project Online.

Po ukończeniu każdej migracji upewnij się, że migracja danych została ukończona pomyślnie.

> [!NOTE]
> Jeśli masz ograniczone rozwiązanie lokalne i rozważasz tylko  migrowanie do programu Project Server 2013, migruj tę wersję tylko na kilka lat. Data zakończenia świadczenia pomocy technicznej dla programu Project Server 2013 z dodatkiem Service Pack 2 13 października 2023 r. Aby uzyskać więcej informacji na temat dat zakończenia wsparcia technicznego, zobacz [Zasady cyklu życia produktów firmy Microsoft](/lifecycle/).

### <a name="how-do-i-migrate-to-project-server-2019"></a>Jak przeprowadzić migrację do programu Project Server 2019?

Różnice w architekturze między programami Project Server 2010 i Project Server 2019 uniemożliwiają bezpośrednią ścieżkę migracji. Dlatego konieczne będzie migrowanie danych z programu Project Server 2010 do każdej kolejnej wersji programu Project Server, aż dotrzesz do Project Server 2019. Kroki uaktualniania do Project Server 2010 do Project Server 2019:

1. Migrowanie do Project Server 2013.

2. Migrowanie z Project Serve 2013 do Project Server 2016.

3. Migrowanie Project Server 2016 do Project Server 2019.

Po ukończeniu każdej migracji upewnij się, że migracja danych została ukończona pomyślnie.

### <a name="step-1-migrate-to-project-server-2013"></a>Krok 1. Migrowanie do Project Server 2013

Aby uzyskać pełne informacje na temat uaktualniania programu Project Server 2010 do programu Project Server 2013, zobacz [Uaktualnianie do programu Project Server 2013](/project/upgrade-to-project-server-2016).

Kluczowe zasoby:

- [Omówienie procesu uaktualniania do Project Server 2013](/project/upgrade-to-project-server-2016)

  Uzyskaj ogólne omówienie uaktualniania programu Project Server 2010 do programu Project Server 2013.
- [Planowanie uaktualnienia do programu Project Server 2013](/project/plan-for-upgrade-to-project-server-2016)

  Przyjrzyj się kwestii dotyczących planowania podczas uaktualniania programu Project Server 2010 do programu Project Server 2013, w tym wymagań systemowych.

- [W tym artykule Co nowego w uaktualnieniu Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) os.:

  - Nie można uaktualnić w miejscu do programu Project Server 2013. Dołączanie baz danych jest jedynym obsługiwanym sposobem uaktualnienia z programu Project Server 2010 do Project Server 2013.

  - Proces uaktualniania nie tylko przekonwertuje dane programu Project Server 2010 na format programu Project Server 2013, ale również skonsoliduje cztery bazy danych programu Project Server 2010 w jedną Project Web App danych.

  - W SharePoint Server 2013 i Project Server 2013 uwierzytelnianie oparte na oświadczeniach było oparte na oświadczeniach z poprzedniej wersji. Jeśli korzystasz z uwierzytelniania klasycznego, musisz rozważyć to podczas uaktualniania. Aby uzyskać więcej informacji, zobacz Migrowanie z uwierzytelniania w trybie klasycznym do uwierzytelniania opartego na oświadczeniach w [programie SharePoint 2013](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

Kluczowe zasoby:

- [Omówienie procesu uaktualniania do programu Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)

- [Uaktualnianie baz danych i Project Web App witryn (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Microsoft Project procesu uaktualniania do serwera](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [Wielka konsolidacja baz danych, Project z programu Server 2010 do 2013 w 8 łatwych krokach](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>Krok 2. Migrowanie do Project Server 2016

Po zakończeniu migracji do programu Project Server 2013 i sprawdzeniu, czy migracja danych została pomyślnie ukończona, następnym krokiem jest przeprowadzenie migracji do programu Project Server 2016.

Aby uzyskać więcej informacji, [zobacz Uaktualnianie do Project Server 2016](/Project/upgrade-to-project-server-2016).

Kluczowe zasoby:

- [Omówienie procesu Project Server 2016 uaktualniania](/Project/overview-of-the-project-server-2016-upgrade-process)

  Dowiedz się, co należy zrobić, aby uaktualnić system Project Server 2013 do wersji Project Server 2016.

- [Planowanie uaktualnienia do Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  Przyjrzyj się kwestii planowania, które należy uwzględnić podczas uaktualniania programu Project Server 2013 do wersji Project Server 2016.

[Ważne informacje o uaktualnianiu do Project Server 2016 obejmują](/project/plan-for-upgrade-to-project-server-2016#thingknow) ważne zmiany dotyczące uaktualniania do tej wersji, takie jak:

- Podczas tworzenia środowiska Project Server 2016 należy pamiętać, że pliki Project Server 2016 są zawarte w programie SharePoint Server 2016. Aby uzyskać więcej informacji, zobacz [Wdrażanie Project Server 2016](/project/deploy-project-server-2016).

- Plany zasobów są przestarzałe w programie Project Server 2016. Plany Project Server 2013 zostaną poddane migracji do zasób w programie Project Server 2016 i w programie Project Online. Aby [uzyskać więcej informacji, zobacz Omówienie: angażowanie](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) zasobów.

### <a name="step-3-migrate-to-project-server-2019"></a>Krok 3. Migrowanie do Project Server 2019

Po zakończeniu migracji do programu Project Server 2016 i sprawdzeniu, czy migracja danych została ukończona pomyślnie, następnym krokiem jest przeprowadzenie migracji danych do programu Project Server 2019.

Aby dowiedzieć się, co należy zrobić, aby uaktualnić system z programu Project Server 2016 do programu Project Server 2019, zobacz Uaktualnianie do [programu Project Server 2019](/Project/upgrade-to-project-server-2016).

Kluczowe zasoby:

- [Omówienie procesu uaktualniania do Project Server 2019](/project/overview-of-the-project-server-2019-upgrade-process)

  Uzyskaj wiedzę na temat uaktualniania programu Project Server 2013 do wersji Project Server 2016.

- [Planowanie uaktualnienia do programu Project Server 2019](/project/plan-for-upgrade-to-project-server-2019)

  Przyjrzyj się rozważaniom w kwestii planowania uaktualnienia programu Project Server 2016 do Project Server 2019.

- [Co należy wiedzieć o uaktualnieniu do Project Server 2019](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>Zapoznaj się z ważnymi zmianami, które należy wprowadzić podczas uaktualniania do tej wersji:

  - Proces uaktualniania spowoduje przeprowadzenie migracji danych z bazy danych Project Server 2016 do bazy danych SharePoint Server 2019 zawartości.  Project Server 2019 nie będzie już tworzyć własnej bazy danych programu Project Server w farmie SharePoint Server.

  - Po uaktualnieniu należy pamiętać o kilku zmianach wprowadzonych w Project Web App.  Aby uzyskać szczegółowe informacje, [zobacz Co nowego w programie Project Server 2019](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**Inne zasoby**:

- [Project Online opisy](/office365/servicedescriptions/project-online-service-description/project-online-service-description) usług: zobacz funkcje zarządzania portfelem zawarte w Project Server 2016 i Project Online Premium.

- [Microsoft Office Project migracji do programu Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Podsumowanie opcji dla klientów Office 2010 i serwerów oraz Windows 7

Aby uzyskać wizualne podsumowanie opcji uaktualnienia, migracji i przenoszenia do chmury dla klientów i serwerów programu Office 2010 oraz systemu Windows 7, zobacz koniec plakatu pomocy [technicznej](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Zakończenie obsługi klientów i Office 2010 i serwerów oraz Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Ten plakat przedstawia różne sposoby, które można podjąć, aby uniknąć zakończenia obsługi produktów klienckich i serwerowych programu Office 2010 oraz programu Windows 7, z wyróżnione preferowanymi ścieżkami i obsługą Microsoft 365 Enterprise opcji.

Możesz również pobrać [ten plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) i wydrukować go w formacie letter, legal lub tabloid (11 x 17).

## <a name="related-topics"></a>Tematy pokrewne

[Uaktualnianie z SharePoint 2010 r.](upgrade-from-sharepoint-2010.md)

[Uaktualnianie serwerów i klientów Office 2010](upgrade-from-office-2010-servers-and-products.md)
