---
title: Planowanie planu uruchomienia portalu w witrynie SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: W tym artykule opisano, jak zaplanować uruchomienie portalu w aplikacji SharePoint Online oraz jakie czynności należy wykonać w celu pomyślnego uruchomienia
ms.openlocfilehash: c31a77f516aad7a58d908f47ee09dac353872283
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569508"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planowanie planu uruchomienia portalu w witrynie SharePoint Online

Portal to witryna sieci SharePoint intranecie z wieloma osobami przeglądający witrynę, które konsumują jej zawartość. Duże organizacje mogą mieć wiele portali. Może to być na przykład portal firmy i portal hr. Zazwyczaj portale mają stosunkowo niewiele osób, które tworzą i tworzą witrynę oraz jej zawartość. Większość osób odwiedzających portal jedynie odczytuje zawartość i zużyje jej.

W tym artykule opisano, jak zaplanować wdrożenie i plan wdrażania w celu wdrożenia SharePoint online. Udostępnia również metody do śledzenia, ponieważ tradycyjne testowanie obciążenia nie jest dozwolone w przypadku SharePoint Online. SharePoint Online to usługa w chmurze, a firma Microsoft zarządza możliwościami ładowania, kondycją i ogólną równoważością obciążenia w usłudze.

Aby pomóc w tworzeniu udanego portalu, postępuj zgodnie z podstawowymi zasadami, ćwiczeniami i zaleceniami szczegółowymi w tworzenie [, uruchamianie i prowadzenie zdrowego portalu](/sharepoint/portal-health)

Poniżej przedstawiono podejście do wdrażania.

## <a name="portal-launch-scheduler"></a>Harmonogram uruchamiania portalu

Użyj harmonogramu uruchamiania portalu, aby zwolnić portal użytkownikom w Twojej organizacji w fazach planowanych. Dowiedz się więcej: 

![Ikona kalendarza.](../media/calendar.png) [Harmonogram uruchamiania portalu](/microsoft-365/enterprise/portallaunchscheduler)

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Omówienie planowania pojemności w u SharePoint Online

W celu efektywnego wykorzystania wydajności i radzenia sobie z nieoczekiwanym wzrostem w dowolnej farmie używamy automatyzacji, która śledzi pewne scenariusze użycia. Chociaż dokładny wzrost jest nieprzewidywalny dla dowolnej dzierżawy w jednej farmie, zagregowana suma żądań jest przewidywalna w czasie. Identyfikując trendy wzrostu w usługach SharePoint Online, możemy zaplanować przyszłą rozszerzeń. Aby uzyskać więcej informacji na temat [planowania pojemności i testowania obciążenia w SharePoint online](capacity-planning-and-load-testing-sharepoint-online.md).

Kluczową częścią udanego wprowadzenia na rynek jest analiza etapu realizacji (etapowa lub etapowa realizacji) szczegółowo poniżej.

## <a name="can-i-load-test-sharepoint-online"></a>Czy mogę załadować test SharePoint Online?

SharePoint Online to wielodostępne środowisko współużytkowane, które jest zrównoważone w farmach, a skala jest dostosowywana na bieżąco. Testowanie obciążenia środowiska, takiego jak aplikacja SharePoint Online, którego skala zmienia się w sposób ciągły nie tylko daje nieoczekiwane wyniki, ale jest niedozwolona.

Dowiedz się więcej: Planowanie [pojemności i testowanie obciążenia w SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optymalizowanie stron przez stosowanie się do zalecanych wytycznych

Strony z wdrożenia lokalnego nie powinny być po prostu przenoszone w trybie online, ponieważ znajdują się SharePoint Online, bez ich przeglądania w oparciu o zalecane wskazówki dotyczące usługi SharePoint Online. Najlepszym rozwiązaniem jest zawsze zoptymalizowanie dowolnej strony głównej pod kątem dowolnej witryny lub portalu w programie SharePoint, ponieważ większość użytkowników w organizacji uzyskuje dostęp jako punkt wyjścia dla witryn.

Należy wziąć pod uwagę kilka podstawowych czynników:

- Wdrożenia lokalne mogą używać tradycyjnych pamięci podręcznych po stronie serwera, takich jak pamięć podręczna obiektów, pamięć podręczna danych wyjściowych i pamięć podręczna obiektów blob. W przypadku różnic w topologii w chmurze te opcje nie muszą być dostępne, ponieważ dzięki tym różnicom skala jest mniej rentowna.
- Wszelkie strony/funkcje/dostosowania używane do użycia w chmurze powinny być zoptymalizowane pod kątem większych opóźnień i rozproszonych lokalizacji użytkowników, tak aby użytkownicy w różnych obszarach lub regionach mieli spójnsze środowisko. Chmura oferuje optymalizacje, takie jak sieci dostarczania zawartości (CDN) w celu optymalizacji pod kątem rozproszonej bazy użytkowników i dla nowoczesnego SharePoint, ostatnie znane dobre (LKG) jest używane przez nasze prywatne (OOTB) składników Web Part.

**Co należy zrobić**:

- Dla wszystkich stron witryny w aplikacji SharePoint Online użyj narzędzia Diagnostyka [stron, które](./page-diagnostics-for-spo.md) jest rozszerzeniem Chromium pomaga w analizowaniu i dostarczaniu wskazówek. Mogą z niego korzystać właściciele, redaktorzy, administratorzy i deweloperzy witryny, ponieważ służy on jako punkt wyjścia do analizy i optymalizacji.
- Deweloperzy powinni również korzystać z narzędzi programisty, takich jak F12 browser developer tool i CTRL-F12 w przeglądarce na nowoczesnych stronach. [Za pomocą fiddlera](https://www.telerik.com/download/fiddler) można także przeglądać rozmiar strony (rozmiar strony w megabajtach) oraz liczbę połączeń i elementów wywłaścić na ogólne obciążenie strony.

Ta sekcja zawierała krótkie podsumowanie dotyczące optymalizowania stron.  Aby dowiedzieć się więcej, zobacz:  [Tworzenie, uruchamianie i prowadzenie prawidłowego portalu](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Postępuj zgodnie z etapami /etapami — etapami

Tradycyjne wielkie podejście do uruchamiania witryny nie pozwala na weryfikację, że dostosowania, źródła zewnętrzne, usługi lub procesy zostały przetestowane we właściwej skali. Ta metoda nie oznacza, że wprowadzenie usługi zajmie kilka miesięcy, ale jest zalecane w ciągu co najmniej kilku dni w zależności od rozmiaru organizacji. Zatem postępowanie zgodnie z planem etapu realizacji umożliwia wstrzymywanie i rozwiązywanie problemów przed przystąpieniem do następnej fazy, przez co pozwala obniżyć potencjalną liczbę użytkowników, na które mogą mieć wpływ wszelkie problemy. SharePoint jako usługi skaluje Twoją wydajność na podstawie użycia i przewidywanego użycia. Mimo że nie potrzebujemy Cię do powiadamiania nas o uruchomieniu, należy postępować zgodnie z wytycznymi, aby zapewnić sukces.

Jak pokazano na poniższej ilustracji, zaproszone osoby często są znacznie większe niż te, które korzystają z witryny. Ten obraz przedstawia strategię rozsyłania wersji. Ta metoda pomaga w identyfikowaniu sposobów ulepszania witryny SharePoint, zanim większość użytkowników będzie ją widzieć.

![Graph się z zaproszonymi i aktywnymi użytkownikami.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)

W fazie pilotażowej warto uzyskać opinie od użytkowników, których organizacja ufa i wie, że będzie zaangażowani. Dzięki temu można sprawdzić, jak jest używany system i jak działa.

Podczas każdej z tych fal zbieraj opinie użytkowników dotyczące funkcji i wydajności podczas każdego procesu wdrażania. Zbieranie opinii ma tę zaletę, że wolno wprowadzamy system i wprowadzamy ulepszenia, gdy system staje się coraz bardziej skorzystaje. Dzięki temu możemy reagować na zwiększone obciążenie, ponieważ witryna jest wyeksagowana u większej liczby użytkowników i w połączeniu z wytycznymi dotyczącymi optymalizacji stron zapewnia pozytywne środowisko pracy użytkowników.

**Co należy zrobić**:

- Wybierz chronometraż poszczególnych faz i upewnij się, że masz nieprzewidzianą/wstrzymaną możliwość, jeśli przed kontynuowaniem konieczne będzie dostosowanie
- Zaplanuj pierwszą grupę użytkowników, dla których chcesz włączyć tę funkcję, aby mieć pewność, że będziesz otrzymywać opinie, które trzeba będzie przesyłać.  Jeśli to możliwe, wybierz aktywną grupę użytkowników, którzy będą na czas dostarczać opinie
- Podczas planowania poszczególnych fal spróbuj zacząć od małej bazy użytkowników (mniej niż 5000 użytkowników). Zwiększaj rozmiary grup podczas pracy nad każdymi falami. Utworzenie metody schodkowania pozwala na łatwiejsze wstrzymywanie szans wstrzymywania w razie potrzeby.
