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
description: Znajdź informacje i zasoby do uaktualnienia z programu Lync Server 2013. Pomoc techniczna kończy się 11 kwietnia 2023 r.
ms.openlocfilehash: 925b53d751cd559ce3ccdf28d823531021611551
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129146"
---
# <a name="upgrading-from-lync-server-2013"></a>Uaktualnianie z programu Lync Server 2013

Program Microsoft Lync Server 2013 zakończy wsparcie **11 kwietnia 2023 r**. Ten artykuł zawiera zasoby ułatwiające uaktualnienie istniejącego wdrożenia programu Lync Server do Microsoft Teams lub Skype dla firm lokalnie.

## <a name="what-is-end-of-support"></a>Co to jest *koniec wsparcia*?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, podczas którego otrzymują nowe funkcje, poprawki błędów, poprawki zabezpieczeń itd. Po dacie zakończenia wsparcia produkt nie przestaje działać, ale firma Microsoft nie zapewnia już następujących elementów:

- Pomoc techniczna dotycząca problemów, które mogą wystąpić.

- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.

- Aktualizacje stref czasowych.

Oznacza to, że nie będzie żadnych dalszych aktualizacji, poprawek ani poprawek dla produktu (w tym poprawek/poprawek zabezpieczeń). pomoc techniczna firmy Microsoft w pełni przesunie wysiłki na rzecz wsparcia do nowszych wersji.

## <a name="plan-ahead"></a>Planować

Sprawdź daty zakończenia pomocy technicznej w [witrynie cyklu życia produktu](/lifecycle/products/microsoft-lync-server-2013). Zaplanuj uaktualnienia lub migracje z myślą o tych datach. Pamiętaj, że produkt *nie przestanie działać* w podanym dniu. Ponieważ jednak instalacja nie będzie już poprawiana po tej dacie, należy zaplanować płynne przejście do następnej wersji produktu. Poniższa tabela zawiera listę dostępnych opcji.

|Koniec produktu pomocy technicznej|Obsługiwane|Zalecane|
|---|---|---|
|Lync Server 2013|Uaktualnianie do Skype dla firm Server 2015 lub 2019 r.|Uaktualnianie do Microsoft Teams

## <a name="whats-next"></a>Co dalej?

Zalecamy uaktualnienie do Microsoft Teams. Microsoft Teams rozszerza możliwości programu Lync Server, łącząc czat, spotkania, rozmowy, współpracę, integrację aplikacji i magazyn plików w jeden interfejs. Teams pomaga usprawnić sposób wykonywania zadań przez użytkowników, poprawiając zadowolenie użytkowników i przyspieszając wyniki biznesowe. Nieustannie rozszerzamy możliwości Teams, aby umożliwić komunikowanie się i współpracę na nowe sposoby, usuwanie barier organizacyjnych i geograficznych oraz zwiększanie wydajności procesu i podejmowania decyzji.

Jeśli nie możesz uaktualnić do Microsoft Teams, możesz przeprowadzić uaktualnienie do wersji Skype dla firm Server 2015 lub 2019. Kluczową kwestią dotyczącą planowania jest to, że oba te produkty zakończą wsparcie 14 października 2025 r. Aby uzyskać więcej informacji, zobacz następujące strony cyklu życia pomocy technicznej:

- [informacje o cyklu życia pomocy technicznej Skype dla firm Server 2015 r.](/lifecycle/products/skype-for-business-server-2015)
- [informacje o cyklu życia pomocy technicznej Skype dla firm Server 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Uaktualnianie do Microsoft Teams

Dysponujemy szczegółowymi wskazówkami dotyczącymi uaktualniania do Microsoft Teams z wdrożenia lokalnego. Najpierw omówimy niektóre kluczowe wymagania techniczne. Należy ustanowić łączność hybrydową, co umożliwi przenoszenie użytkowników do Teams. [Planowanie łączności hybrydowej](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) zapewnia omówienie konfigurowania środowiska hybrydowego. Mimo że artykuł koncentruje się na Skype dla firm, wszystkie pojęcia dotyczą również programu Lync Server 2013. Zobacz sekcję [Wymagania dotyczące wersji serwera](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) , aby uzyskać szczegółowe informacje dotyczące programu Lync Server 2013.

Należy również upewnić się, że wdrożenie programu Lync Server 2013 jest w pełni aktualne. Publikujemy [listę wszystkich najnowszych aktualizacji programu Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) Jednak następująca aktualizacja jest wymaganiem wstępnym uaktualnienia do Microsoft Teams:

- [Aktualizacja zbiorcza 5.0.8308.1149 z września 2021 r. dla programu Lync Server 2013, Podstawowe składniki](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043): ta aktualizacja zastępuje uwierzytelnianie identyfikatora na żywo protokołem uwierzytelniania OAuth dla `Move-CSUser` polecenia cmdlet, który jest używany do przenoszenia użytkowników lokalnych do Microsoft Teams.

Mimo że środowisko użytkownika w Microsoft Teams jest znacznie bogatsze i lepsze od programu Lync, jest również znacznie inne. W związku z tym należy również przygotować organizację i użytkowników, aby zapewnić szybkie wdrożenie Microsoft Teams. Mamy do dyspozycji wiele informacji na temat przygotowywania organizacji, planowania uaktualniania do Teams i zapewnienia pomyślnego wdrożenia.

**Zalecamy rozpoczęcie pracy w naszym [portalu uaktualniania Teams](/MicrosoftTeams/upgrade-skype-teams)**, w którym można znaleźć informacje techniczne, zasoby szkoleniowe, linki do sesji konferencji Ignite, dostępne zasoby pomocy, analizy przypadku i inne.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Zrzut ekranu przedstawiający portal uaktualniania Teams":::

### <a name="upgrade-to-skype-for-business-server"></a>Uaktualnianie do Skype dla firm Server

Ścieżka do Skype dla firm Server będzie się różnić w zależności od wersji, do którą chcesz uaktualnić. Skype dla firm Server 2015 r. obsługuje uaktualnienie w miejscu z programu Lync Server 2013. Z drugiej strony, aby przeprowadzić uaktualnienie do wersji Skype dla firm Server 2019 r., należy najpierw wprowadzić Skype dla firm Server 2019 r. do instalacji programu Lync Server 2013 poprzez dodanie co najmniej jednego nowego serwera, a następnie przenieść operacje na nowo dodane serwery 2019.

Jedną z ważnych kwestii, które należy wziąć pod uwagę, jest to, że obecna faza wsparcia dla każdego produktu: Skype dla firm 2019 r. jest objęta wsparciem głównym, a Skype dla firm 2015 r. jest obecnie objęta wsparciem rozszerzonym.  Dlatego zalecamy uaktualnienie do Skype dla firm Server 2019 roku. Aby dowiedzieć się więcej na temat różnicy między wsparciem głównym i rozszerzonym, zobacz [Zasady stałego cyklu życia](/lifecycle/policies/fixed).

Zobacz następujące zasoby, aby uzyskać szczegółowe informacje o każdym scenariuszu uaktualniania.

- [Uaktualnianie do Skype dla firm Server 2019 r.](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Uaktualnianie do Skype dla firm Server 2015 r.](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
