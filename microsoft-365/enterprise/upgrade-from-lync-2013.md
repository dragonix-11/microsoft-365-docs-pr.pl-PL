---
title: Uaktualnianie z programu Lync Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Znajdź informacje i zasoby na temat uaktualniania programu Lync Server 2013. Pomoc techniczna kończy się 11 kwietnia 2023 r.
ms.openlocfilehash: 6d6d3baed383e85a1e97d37726ff7f1eb355e98c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009680"
---
# <a name="upgrading-from-lync-server-2013"></a>Uaktualnianie z programu Lync Server 2013

**11 kwietnia 2023** r. zakończy się wsparcie techniczne dla programu Microsoft Lync Server 2013. Ten artykuł zawiera zasoby pomocne w uaktualnieniu istniejącego wdrożenia programu Lync Server do Microsoft Teams lub Skype dla firm lokalnego.

## <a name="what-is-end-of-support"></a>Co oznacza *zakończenie wsparcia technicznego*?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskają nowe funkcje, poprawki, poprawki zabezpieczeń i tak dalej. Po zakończeniu wsparcia technicznego produkt nie przestanie działać, ale firma Microsoft już nie udostępnia:

- pomoc techniczną w zakresie mogącego wystąpić problemów;

- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.

- Aktualizacje stref czasowych.

Oznacza to, że nie będą dostępne żadne dalsze aktualizacje, poprawki ani poprawki dla tego produktu (w tym poprawki zabezpieczeń/poprawki). Pomoc techniczna firmy Microsoft całkowicie przesunięła swoje działania na rzecz obsługi najnowszych wersji.

## <a name="plan-ahead"></a>Planowanie z wyprzedzeniem

Sprawdź daty zakończenia obsługi w [witrynie Cyklu życia produktu](/lifecycle/products/lync-server-2013). Planuj uaktualnienia i migracje, pamiętasz o tych datach. Pamiętaj, że produkt *nie przestanie działać w* dniu na liście. Jednak ponieważ po tym dniu instalacja nie będzie już poprawiana, należy zaplanować płynne przejście do następnej wersji produktu. W poniższej tabeli wymieniono dostępne opcje.

|Zakończenie produktu pomocy technicznej|Obsługiwane|Zalecane|
|---|---|---|
|Lync Server 2013|Uaktualnianie do Skype dla firm Server 2015 lub 2019|Uaktualnianie do Microsoft Teams

## <a name="whats-next"></a>Co dalej?

Zalecamy uaktualnienie do Microsoft Teams. Microsoft Teams możliwości programu Lync Server, łącząc czat, spotkania, połączenia, współpracę, integrację z aplikacją i przechowywanie plików w jednym interfejsie. Teams usprawnić sposób pracy użytkowników, zwiększyć zadowolenie użytkowników i przyspieszyć przyspieszanie wyników biznesowych. Stale rozszerzamy możliwości Teams komunikacji i współpracy na nowe sposoby, łamania barier organizacyjnych i geograficznych oraz zwiększamy wydajność procesu i podejmowania decyzji.

Jeśli nie możesz uaktualnić do programu Microsoft Teams, możesz uaktualnić go do wersji Skype dla firm Server 2015 lub 2019. Kluczową kwestią podczas planowania jest zakończenie obsługi obu tych produktów 14 października 2025 r. Aby uzyskać więcej informacji, zobacz następujące strony cyklu życia pomocy technicznej:

- [Skype dla firm Server 2015 r. informacje o cyklu życia pomocy technicznej](/lifecycle/products/skype-for-business-server-2015)
- [Skype dla firm Server 2019 r. informacje o cyklu życia pomocy technicznej](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Uaktualnianie do Microsoft Teams

Mamy szczegółowe wskazówki dotyczące uaktualniania do Microsoft Teams z wdrożenia lokalnego. Najpierw przyjrzyjmy się kilku kluczowym wymaganiami technicznymi. Konieczne będzie ustanowienie łączności hybrydowej, która umożliwi przeniesienie użytkowników do Teams. [Planowanie łączności hybrydowej](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) zawiera omówienie konfigurowania środowiska hybrydowego. Mimo że artykuł dotyczy wyłącznie Skype dla firm, wszystkie pojęcia dotyczą również programu Lync Server 2013. Zobacz [sekcję wymagań dotyczących wersji serwera](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) , aby uzyskać szczegółowe informacje dotyczące programu Lync Server 2013.

Musisz również upewnić się, że Twoje wdrożenie programu Lync Server 2013 jest w pełni aktualne. Publikujemy listę wszystkich najnowszych aktualizacji dla programu [Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164), jednak następująca aktualizacja jest wymaganie wstępnego uaktualnienia do programu Microsoft Teams:

- Skumulowana aktualizacja [5.0.8308.1149 dla programu Lync Server 2013](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043), składniki podstawowe z września 2021 r.: ta aktualizacja zastępuje protokół uwierzytelniania OAuth `Move-CSUser` dla polecenia cmdlet, które jest używane do przenoszenia użytkowników lokalnych do programu Microsoft Teams.

Mimo że środowisko użytkownika w programie Microsoft Teams znacznie bardziej rozbudowane i lepsze niż program Lync, znacznie się różni. W związku z tym konieczne będzie również przygotowanie organizacji i użytkowników w celu zapewnienia szybkiego przyjęcia nowych Microsoft Teams. Dostępnych jest wiele informacji na temat sposobu przygotowania organizacji, planowania uaktualnienia do programu Teams i zapewnienia pomyślnego uaktualnienia.

**Zalecamy rozpoczęcie pracy w [](/MicrosoftTeams/upgrade-skype-teams)** naszym portalu Teams, w którym znajdują się informacje techniczne, zasoby szkoleniowe, linki do sesji Ignite, dostępne zasoby pomocy, analizy przypadków i nie tylko.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Zrzut ekranu przedstawiający Teams uaktualniania":::

### <a name="upgrade-to-skype-for-business-server"></a>Uaktualnianie do Skype dla firm Server

Ścieżka dostępu do Skype dla firm Server się różnić w zależności od wersji wybranej do uaktualnienia. Skype dla firm Server 2015 obsługuje uaktualnienie w miejscu z programu Lync Server 2013. Z drugiej strony, aby uaktualnić program do wersji Skype dla firm Server 2019, należy najpierw wprowadzić program Skype dla firm Server 2019 do instalacji programu Lync Server 2013, dodając jeden lub więcej nowych serwerów, a następnie przenieść operacje na nowo dodane serwery 2019.

Jedną z ważnych kwestii, które należy wziąć pod uwagę, jest to, że bieżąca faza pomocy technicznej dla każdego produktu: program Skype dla firm 2019 jest wsparciem głównym, a program Skype dla firm 2015 jest obecnie wsparciem rozszerzonym.  Dlatego zalecamy uaktualnienie do wersji Skype dla firm Server 2019. Aby dowiedzieć się więcej o różnicy między wsparciem głównym i wsparciem rozszerzonym, zobacz [Stałe zasady cyklu życia](/lifecycle/policies/fixed).

Szczegółowe informacje na temat poszczególnych scenariuszy uaktualniania można znaleźć w poniższych zasobach.

- [Uaktualnianie do Skype dla firm Server 2019 r.](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Uaktualnianie do wersji Skype dla firm Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
