---
title: Ogólne często zadawane pytania dotyczące przenoszenia danych
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: ITPro
ms.topic: faq
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Znajdź odpowiedzi na często zadawane pytania dotyczące przenoszenia danych podstawowych do nowego obszaru geograficznego Office 365 centrum danych.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3164612238010e72eb02510e1264cca528b80f38
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874322"
---
# <a name="data-move-general-faq"></a>Ogólne często zadawane pytania dotyczące przenoszenia danych

Poniżej przedstawiono odpowiedzi na ogólne pytania dotyczące przenoszenia podstawowych danych klientów magazynowanych do nowego obszaru geograficznego centrum danych.

### <a name="what-customers-are-eligible-to-request-a-move"></a>Co klienci kwalifikują się do żądania przeniesienia?
<details><summary>Kliknij, aby rozwinąć</summary>

Istniejący Microsoft 365 klienci komercyjni, którzy wybrali kraj kwalifikujący się do nowego obszaru geograficznego centrum danych, będą mogli zażądać przeniesienia. Program istnieje tylko w przypadku dzierżaw z kwalifikującym się kodem kraju przypisanym do dzierżawy Microsoft 365 w celu migracji podstawowych danych klientów magazynowanych dla kwalifikujących się obciążeń do odpowiedniego obszaru geograficznego Microsoft 365 centrum danych. Zobacz [Jak zażądać przeniesienia danych](request-your-data-move.md) , aby potwierdzić kwalifikowalność kraju.

</details>

### <a name="how-do-we-define-core-customer-data"></a>Jak zdefiniować podstawowe dane klienta?
<details><summary>Kliknij, aby rozwinąć</summary>

Podstawowe dane klienta to termin, który odnosi się do podzestawu danych klienta zdefiniowanego w [warunkach usług online firmy Microsoft](https://aka.ms/ost):

- Exchange Online zawartości skrzynki pocztowej (treść wiadomości e-mail, wpisy kalendarza i zawartość załączników wiadomości e-mail)
- SharePoint zawartość witryny online i pliki przechowywane w tej witrynie
- Pliki przekazane do OneDrive dla Firm

</details>

### <a name="what-is-in-scope-for-teams-migration"></a>Co jest w zakresie migracji Teams?
<details><summary>Kliknij, aby rozwinąć</summary>

Oprócz Exchange Online, SharePoint Online i OneDrive dla Firm; Firma Microsoft przeprowadzi migrację Teams danych do lokalnego centrum danych.

- Teams wiadomości czatu, w tym wiadomości prywatne i wiadomości kanału.
- Teams obrazów używanych w czatach.

Teams pliki są przechowywane w usłudze SharePoint Online, a pliki czatu Teams są przechowywane w OneDrive dla Firm. Poczta głosowa, kalendarz i kontakty są przechowywane w Exchange Online. W wielu przypadkach Exchange Online, SharePoint Online i OneDrive dla Firm są już używane przez klienta w lokalnym centrum danych geograficznych, a także są częścią programu migracji Microsoft 365 dla kwalifikujących się krajów klientów.

</details>

### <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>W jakim momencie migracja została ukończona, aby podstawowe dane klientów mojej dzierżawy były przechowywane w nowym obszarze geograficznym?
<details><summary>Kliknij, aby rozwinąć</summary>

Ze względu na współdzielone zależności między Exchange Online i SharePoint Online/OneDrive dla Firm nie można uznać żadnej migracji za ukończoną, dopóki obie usługi nie zostaną zmigrowane. Exchange Online i SharePoint Online/OneDrive dla Firm często migrowane w oddzielnych godzinach i niezależnie od siebie. Administratorzy dzierżawy klienta otrzymują potwierdzenie w Centrum komunikatów po zakończeniu każdej migracji usługi i mogą wyświetlać kartę lokalizacji danych w centrum Administracja w dowolnym momencie, aby potwierdzić podstawowe dane klienta w lokalizacji spoczynku dla każdej usługi.

</details>

### <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Jak upewnić się, że dane klientów są bezpieczne podczas przenoszenia i że nie wystąpi przestój?
<details><summary>Kliknij, aby rozwinąć</summary>

Przenoszenie danych to operacja usługi zaplecza o minimalnym wpływie na użytkowników końcowych. Funkcje, na które mogą mieć wpływ, są wyświetlane w obszarze [Podczas i po przeniesieniu danych](during-and-after-your-data-move.md). Przestrzegamy [umowy dotyczącej poziomu usług online firmy Microsoft (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) w celu zapewnienia dostępności, dlatego klienci nie muszą przygotowywać się do przenoszenia ani monitorować ich.

Wszystkie usługi Microsoft 365 działają w tych samych wersjach w centrach danych, dzięki czemu możesz mieć pewność spójnej funkcjonalności. Twoja usługa jest w pełni obsługiwana w całym procesie.

</details>

### <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Jaki jest wpływ posiadania różnych usług znajdujących się w różnych obszarach geograficznych?
<details><summary>Kliknij, aby rozwinąć</summary>

Niektóre usługi Microsoft 365 mogą znajdować się w różnych obszarach geograficznych dla niektórych istniejących klientów i klientów, którzy znajdują się w trakcie procesu przenoszenia. Nasze usługi działają niezależnie od siebie i nie ma to wpływu na środowisko użytkownika, jeśli tak jest. Jednak dla celów przechowywania danych migracja dzierżawy nie może zostać uznana za ukończoną, dopóki zarówno Exchange Online, jak i SharePoint Online/OneDrive dla Firm nie zostaną zmigrowane do tego samego obszaru geograficznego centrum danych.

</details>

### <a name="where-is-my-core-customer-data-located"></a>Gdzie znajdują się moje podstawowe dane klienta?
<details><summary>Kliknij, aby rozwinąć</summary>

Administratorzy dzierżawy klienta mogą wyświetlać kartę lokalizacji danych w centrum Administracja w dowolnym momencie, aby potwierdzić podstawowe dane klienta w lokalizacji spoczynku dla każdej usługi, w szczególności dla dzierżawy. Publikujemy również lokalizację obszarów geograficznych centrum danych, centrów danych i lokalizacji Office 365 danych klientów na [Microsoft 365 interaktywnych mapach centrów danych](https://office.com/datamaps) jako odwołanie do bieżących domyślnych podstawowych danych klienta w lokalizacjach spoczynku dla nowych dzierżaw. Lokalizację danych klientów magazynowanych można sprawdzić w sekcji Lokalizacja danych w profilu organizacji w Centrum administracyjne platformy Microsoft 365.

</details>

### <a name="when-will-i-be-able-to-request-a-move"></a>Kiedy będę mógł zażądać przeniesienia?
<details><summary>Kliknij, aby rozwinąć</summary>

Zapoznaj się ze stroną [Jak zażądać przeniesienia danych](request-your-data-move.md) dla obsługiwanych ram czasowych dla obszaru geograficznego centrum danych.

</details>

### <a name="how-can-i-request-to-be-moved"></a>Jak mogę poprosić o przeniesienie?
<details><summary>Kliknij, aby rozwinąć</summary>

Uprawnieni klienci zobaczą stronę w [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/). Aby uzyskać instrukcje dotyczące żądania przeniesienia [, zobacz Jak zażądać przeniesienia danych](request-your-data-move.md) .

</details>

### <a name="can-i-change-my-selection-after-requesting-a-move"></a>Czy mogę zmienić wybór po zażądaniu przeniesienia?
<details><summary>Kliknij, aby rozwinąć</summary>

Nie możemy usunąć Użytkownika z procesu po przesłaniu żądania.

</details>

### <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Co się stanie, jeśli nie zażądam przeniesienia przed upływem terminu?
<details><summary>Kliknij, aby rozwinąć</summary>

Nie możemy akceptować żądań migracji po otwartym okresie rejestracji.

</details>

### <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Co zrobić, jeśli chcę przenieść dane w celu uzyskania lepszej wydajności sieci?
<details><summary>Kliknij, aby rozwinąć</summary>

Fizyczna bliskość Microsoft 365 centrum danych nie gwarantuje lepszej wydajności sieci. Istnieje wiele czynników i składników, które wpływają na wydajność sieci między użytkownikiem końcowym a usługą Microsoft 365. Aby uzyskać więcej informacji na ten temat i dostrajanie wydajności, zobacz [Planowanie sieci i dostrajanie wydajności dla Microsoft 365](network-planning-and-performance.md).

</details>

### <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Czy wszystkie usługi przenoszą swoje dane tego samego dnia?
<details><summary>Kliknij, aby rozwinąć</summary>

Każda usługa jest przenoszona niezależnie i prawdopodobnie będzie przenosić swoje dane w różnym czasie.

</details>

### <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Czy mogę wybrać, kiedy chcę przenieść moje dane?
<details><summary>Kliknij, aby rozwinąć</summary>

Klienci nie mogą wybrać określonej daty, nie mogą opóźnić przenoszenia i nie możemy udostępnić określonej daty ani przedziału czasu przenoszenia.

</details>

### <a name="can-you-share-when-my-data-will-be-moved"></a>Czy możesz udostępnić dane, które zostaną przeniesione?
<details><summary>Kliknij, aby rozwinąć</summary>

Przenoszenie danych to operacja zaplecza o minimalnym wpływie na użytkowników końcowych. Złożoność, precyzja i skala, z jaką musimy wykonywać przenoszenie danych w środowisku obsługiwanym globalnie i zautomatyzowanym, uniemożliwia udostępnianie danych, gdy oczekuje się, że przeniesienie danych zostanie ukończone dla dzierżawy lub dowolnej innej pojedynczej dzierżawy. Po zakończeniu przenoszenia danych klienci otrzymają jedno potwierdzenie w Centrum komunikatów na uczestniczącą usługę.

</details>

### <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Co się stanie, jeśli użytkownicy uzyskują dostęp do usług podczas przenoszenia danych?
<details><summary>Kliknij, aby rozwinąć</summary>

Zobacz [Sekcję Podczas i po przeniesieniu danych](during-and-after-your-data-move.md) , aby uzyskać pełną listę funkcji, które mogą być ograniczone podczas przenoszenia części danych dla każdej usługi.

</details>

### <a name="how-do-i-know-the-move-is-complete"></a>Jak mogę wiedzieć, że przenoszenie zostało ukończone?
<details><summary>Kliknij, aby rozwinąć</summary>

Obejrzyj Microsoft 365 Centrum komunikatów, aby potwierdzić, że przenoszenie danych poszczególnych usług zostało ukończone. Po przeniesieniu danych każdej usługi opublikujemy powiadomienie o ukończeniu, dzięki czemu otrzymasz trzy powiadomienia o ukończeniu: po jednym dla Exchange Online, SharePoint Online i Skype dla firm Online. Możesz również zweryfikować lokalizację danych klientów magazynowanych za pośrednictwem sekcji Lokalizacja danych w obszarze Profil organizacji w Centrum administracyjne platformy Microsoft 365.

</details>

### <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Jestem klientem Microsoft 365 w jednym z nowych obszarów geograficznych centrum danych, ale po zarejestrowaniu się wybrałem inny kraj. Jak można przenieść do nowego obszaru geograficznego centrum danych?
<details><summary>Kliknij, aby rozwinąć</summary>

Nie można zmienić kraju rejestracji skojarzonego z dzierżawą. Zamiast tego należy utworzyć nową dzierżawę Microsoft 365 z nową subskrypcją i ręcznie przenieść użytkowników i dane do nowej dzierżawy.

</details>

### <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Co się stanie, jeśli będziemy w trakcie migracji danych poczty e-mail do Microsoft 365 podczas przenoszenia Exchange Online?
<details><summary>Kliknij, aby rozwinąć</summary>

Jest to bardzo typowy scenariusz i jest w pełni obsługiwany. Migracja chmury między obszarami geograficznymi centrum danych nie zakłóca żadnych migracji lokalnych do skrzynek pocztowych w chmurze.

</details>

### <a name="can-i-pilot-some-users"></a>Czy mogę pilotować niektórych użytkowników?
<details><summary>Kliknij, aby rozwinąć</summary>

Możesz utworzyć oddzielną dzierżawę wersji próbnej, aby przetestować łączność, ale dzierżawy wersji próbnej nie można w żaden sposób połączyć z istniejącą dzierżawą.

</details>

### <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Nie chcę czekać, aż firma Microsoft przeniesie moje dane. Czy mogę po prostu utworzyć nową dzierżawę i przenieść się?
<details><summary>Kliknij, aby rozwinąć</summary>

Tak, jednak proces nie będzie tak bezproblemowy, jak gdyby firma Microsoft wykonała przenoszenie danych.

Jeśli nowa dzierżawa zostanie utworzona po udostępnieniu nowego obszaru geograficznego centrum danych, nowa dzierżawa będzie hostowana w nowym obszarze geograficznym. Ta nowa dzierżawa jest całkowicie oddzielona od poprzedniej dzierżawy i będzie odpowiedzialna za przenoszenie wszystkich skrzynek pocztowych użytkownika, zawartości witryny, nazw domen i innych danych. Należy pamiętać, że nie można przenieść nazwy dzierżawy z jednej dzierżawy do innej. Zalecamy oczekiwanie na program przenoszenia dostarczony przez firmę Microsoft, ponieważ zajmiemy się przenoszeniem wszystkich ustawień, danych i subskrypcji dla użytkowników.

</details>

### <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Moje dane klientów zostały już przeniesione do nowego obszaru geograficznego centrum danych. Czy mogę wrócić?
<details><summary>Kliknij, aby rozwinąć</summary>

Nie, nie jest to możliwe. Nie można przenieść klientów, którzy zostali przeniesieniu do nowych geograficznych centrów danych. Jako klient w dowolnym obszarze geograficznym będziesz mieć taką samą jakość usług, wydajności i mechanizmów zabezpieczeń, jak wcześniej. [Microsoft 365 multi geo](https://aka.ms/multi-geo) jest dostępna dla niektórych klientów jako dodatek i umożliwia jednej dzierżawie tworzenie wielu obszarów geograficznych satelitarnych i przenoszenie danych użytkowników do tych obszarów geograficznych przy użyciu zobowiązań dotyczących rezydencji danych.

</details>

### <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Czy Microsoft 365 dzierżawy hostowane w nowych centrach danych będą dostępne dla użytkowników spoza kraju?
<details><summary>Kliknij, aby rozwinąć</summary>

Tak. Firma Microsoft utrzymuje dużą globalną sieć z publicznymi połączeniami internetowymi w ponad 130 lokalizacjach w 35 krajach na całym świecie z umowami komunikacji równorzędnej z ponad 2700 dostawcami usług internetowych. Użytkownicy będą mogli uzyskiwać dostęp do centrów danych z dowolnego miejsca w Internecie.

</details>

### <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Moja dzierżawa skonfigurowała dodatek Multi Geo. Czy nadal mogę zarejestrować się w dzierżawie w programie przenoszenia Microsoft 365? aby zmienić domyślną lokalizację geograficzną i przenieść dowolnego użytkownika, który nie jest w regionie satelitarnym, do nowego domyślnego obszaru geograficznego?
<details><summary>Kliknij, aby rozwinąć</summary>

Tak, dzierżawa kwalifikuje się do rejestracji, ale istnieją istotne zagadnienia, ponieważ przenoszenie na poziomie dzierżawy nie jest w pełni obsługiwane dla klientów, którzy skonfigurowali funkcję [Multi-Geo](https://aka.ms/multi-geo).

SharePoint Online i OneDrive dla Firm nie mogą migrować do nowego obszaru geograficznego centrum danych na poziomie dzierżawy za pośrednictwem tego programu. Administrator klienta może skonfigurować udziały OneDrive dla Firm, aby przenieść je do dowolnego dostępnego regionu przy użyciu funkcji Multi-Geo, ale nie można zmienić domyślnej lokalizacji dzierżawy po skonfigurowaniu wielu obszarów geograficznych dla dzierżawy.

W przypadku klientów, którzy zdecydują się na migrację — przeniesiemy wszystkie Exchange Online skrzynki pocztowe z bieżącego domyślnego obszaru geograficznego do nowego lokalnego obszaru geograficznego centrum danych i zaktualizujemy domyślny region Exchange Online. Nie będziemy przenosić żadnych skrzynek pocztowych EXO skonfigurowanych w regionach satelitów Multi Geo, aby nadal respektować miejsce przechowywania danych w regionie satelitarnym zgodnie z oczekiwaniami.  Teams migracje dzierżawy usługi czatu dla klientów z konfiguracją wielu obszarów geograficznych zachowują się podobnie do Exchange Online.

</details>

### <a name="i-have-public-folders-deployed-in-my-tenant-what-will-be-the-impact-on-public-folder-access-during-or-after-the-move"></a>Mam foldery publiczne wdrożone w mojej dzierżawie. Jaki będzie wpływ na dostęp do folderu publicznego podczas przenoszenia lub po niej?
<details><summary>Kliknij, aby rozwinąć</summary>

Nie ma to wpływu na użytkowników końcowych uzyskujących dostęp do folderów publicznych podczas przenoszenia folderów publicznych lub po nich. Jednak foldery publiczne mogą nie być dostępne do administrowania w narzędziu centrum Exchange Administracja, dopóki wszystkie skrzynki pocztowe folderów publicznych nie zostaną przeniesione w tym samym regionie. Aby uzyskać więcej informacji, zapoznaj się z [tym artykułem](https://aka.ms/pfxrf) .

</details>

### <a name="related-topics"></a>Tematy pokrewne

[Przenoszenie danych podstawowych do nowych obszarów geograficznych centrum danych Microsoft 365](moving-data-to-new-datacenter-geos.md)

[Jak zażądać przeniesienia danych](request-your-data-move.md)

[Microsoft 365 wielu obszarach geograficznych](https://aka.ms/multi-geo)

[Microsoft 365 interaktywnej mapy centrum danych](https://office.com/datamaps)

[obsługa Microsoft 365](../admin/get-help-support.md)

[Nowe lokalizacje geograficzne centrum danych dla Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)

[Usługi platformy Azure według regionów](https://azure.microsoft.com/regions/)
