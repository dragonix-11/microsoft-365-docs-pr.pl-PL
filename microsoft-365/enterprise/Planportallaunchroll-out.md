---
title: Planowanie planu wdrożenia uruchamiania portalu w usłudze SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule opisano sposób planowania uruchamiania portalu w usłudze SharePoint Online oraz czynności, które należy wykonać w celu pomyślnego uruchomienia
ms.openlocfilehash: 088416537317a6728e1c5533767badf309de7634
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097475"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planowanie planu wdrożenia uruchamiania portalu w usłudze SharePoint Online

Portal to witryna SharePoint w intranecie z wieloma widzami witryn, którzy korzystają z zawartości w witrynie. Duże organizacje mogą mieć kilka portali. Na przykład portal firmy i portal hr. Zazwyczaj portale mają stosunkowo niewiele osób, które tworzą i tworzą witrynę oraz jej zawartość. Większość odwiedzających portal tylko odczytuje i zużywa zawartość.

W tym artykule opisano, jak zaplanować wdrożenie i plan wdrożenia w celu SharePoint Online. Zapewnia również podejścia do naśladowania, ponieważ tradycyjne testowanie obciążenia nie jest dozwolone w usłudze SharePoint Online. SharePoint Online to usługa w chmurze, a możliwości ładowania, kondycja i ogólny saldo obciążenia w usłudze są zarządzane przez firmę Microsoft.

Aby ułatwić tworzenie pomyślnego portalu, postępuj zgodnie z podstawowymi zasadami, praktykami i zaleceniami opisanymi w [temacie Tworzenie, uruchamianie i utrzymywanie dobrej kondycji portalu](/sharepoint/portal-health)

Podejście do wdrażania zostało wyróżnione poniżej.

## <a name="portal-launch-scheduler"></a>Harmonogram uruchamiania portalu

Harmonogram uruchamiania portalu umożliwia udostępnienie portalu użytkownikom w organizacji w zaplanowanych fazach. Dowiedz się więcej: 

![Ikona kalendarza.](../media/calendar.png) [Harmonogram uruchamiania portalu](/microsoft-365/enterprise/portallaunchscheduler)

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Omówienie planowania pojemności w usłudze SharePoint Online

Aby efektywnie korzystać z pojemności i radzić sobie z nieoczekiwanym wzrostem, w każdej farmie mamy automatyzację, która śledzi pewne scenariusze użycia. Chociaż dokładny wzrost jest nieprzewidywalny dla jednej dzierżawy w jednej farmie, zagregowana suma żądań jest przewidywalna w czasie. Identyfikując trendy wzrostu w usłudze SharePoint Online, możemy zaplanować przyszłą ekspansję. Aby uzyskać więcej informacji na temat [planowania pojemności i testowania obciążenia SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md).

Kluczową częścią pomyślnego uruchomienia jest podejście "wave" lub "phased roll-out" opisane poniżej.

## <a name="can-i-load-test-sharepoint-online"></a>Czy mogę ładować test SharePoint online?

SharePoint Online jest udostępnionym środowiskiem wielodostępnym, które jest zrównoważone między farmami, a skala jest dostosowywana w bieżącej wersji. Testowanie obciążenia środowiska, takiego jak SharePoint Online, którego ciągłe zmiany skalowania nie tylko dają nieoczekiwane wyniki, ale nie są dozwolone.

Dowiedz się więcej: [Planowanie pojemności i testowanie obciążenia SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optymalizowanie stron zgodnie z zalecanymi wytycznymi

Strony z wdrożenia lokalnego nie powinny być po prostu przenoszone, ponieważ znajdują się w usłudze SharePoint Online bez przeglądania ich zgodnie z zalecanymi wytycznymi dotyczącymi usługi SharePoint Online. Najlepszym rozwiązaniem jest zawsze optymalizowanie dowolnej strony głównej dla dowolnej witryny lub portalu w SharePoint, ponieważ jest to miejsce, w którym większość użytkowników w organizacji będzie uzyskiwać dostęp jako punkt początkowy dla witryn.

Należy rozważyć kilka podstawowych czynników:

- Wdrożenia lokalne mogą używać tradycyjnych pamięci podręcznych po stronie serwera, takich jak pamięć podręczna obiektów, pamięć podręczna danych wyjściowych i pamięć podręczna obiektów blob. Różnice topologii w chmurze niekoniecznie są dostępne, ponieważ różnice w skali sprawiają, że są mniej opłacalne.
- Wszystkie strony / funkcje / dostosowania używane do użycia w chmurze powinny być zoptymalizowane pod kątem większych opóźnień i rozproszonych lokalizacji użytkowników, tak aby użytkownicy w różnych obszarach lub regionach mieli bardziej spójne środowisko. Chmura oferuje optymalizacje, takie jak content delivery networks (CDN) w celu zoptymalizowania pod kątem rozproszonej bazy użytkowników i nowoczesnych SharePoint, ostatnie znane dobre (LKG) jest używane przez nasze nieczynne składniki internetowe (OOTB).

**Co robić**:

- Dla wszystkich stron witryny w usłudze SharePoint Online użyj [narzędzia diagnostyki strony](./page-diagnostics-for-spo.md), które jest rozszerzeniem Chromium, które pomaga w analizowaniu i dostarczaniu wskazówek. Może być ona używana przez właścicieli witryn, redaktorów, administratorów i deweloperów, ponieważ została zaprojektowana jako punkt wyjścia do analizy i optymalizacji.
- Deweloperzy powinni również używać narzędzi programistycznych, takich jak narzędzie deweloperskie przeglądarki F12 i CTRL-F12 w przeglądarce na nowoczesnych stronach. [Program Fiddler](https://www.telerik.com/download/fiddler) może również służyć do przeglądania wagi rozmiaru (rozmiaru strony w megabajtach) strony oraz liczby wywołań i elementów wpływających na ogólne obciążenie strony.

Ta sekcja była krótkim podsumowaniem optymalizacji stron.  Aby dowiedzieć się więcej, zobacz  [: Tworzenie, uruchamianie i utrzymywanie portalu w dobrej kondycji](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Postępuj zgodnie z podejściem do wdrażania stopniowego/stopniowego

Tradycyjne podejście do uruchamiania witryn nie umożliwi weryfikacji, czy dostosowania, źródła zewnętrzne, usługi lub procesy zostały przetestowane w odpowiedniej skali. Takie podejście nie oznacza, że uruchomienie może potrwać miesiące, ale jest zalecane przez co najmniej kilka dni w zależności od rozmiaru organizacji. W związku z tym po planie wdrożenia falowego możesz wstrzymać i rozwiązać problemy przed przejściem do następnej fazy, a tym samym zmniejszyć potencjalną liczbę użytkowników, na których wystąpiły jakiekolwiek problemy. SharePoint jako usługa skaluje pojemność na podstawie użycia i przewidywanego użycia, a mimo że nie musimy powiadamiać nas o uruchomieniu, należy postępować zgodnie z wytycznymi, aby zapewnić powodzenie.

Jak pokazano na poniższej ilustracji, często liczba zaproszonych użytkowników jest znacznie wyższa niż liczba użytkowników faktycznie korzystających z witryny. Na tym obrazie przedstawiono strategię dotyczącą sposobu wdrażania wydania. Ta metoda pomaga zidentyfikować sposoby ulepszania witryny SharePoint, zanim większość użytkowników ją zobaczy.

![Graph przedstawiających zaproszonych i aktywnych użytkowników.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)

W fazie pilotażowej dobrze jest otrzymywać opinie od użytkowników, którym organizacja ufa i wie, że będą zaangażowani. W ten sposób można ocenić, jak system jest używany i jak działa.

Podczas każdej z tych fal zbierz opinie użytkowników dotyczące funkcji i wydajności podczas każdej fali wdrażania. Zbieranie opinii ma tę zaletę, że powoli wprowadza system i wprowadza ulepszenia, ponieważ system staje się bardziej używany. Dzięki temu możemy również reagować na zwiększone obciążenie, ponieważ witryna jest wdrażana dla większej liczby użytkowników i w połączeniu z przestrzeganiem wytycznych dotyczących optymalizacji stron zapewnia pozytywne środowisko dla użytkowników.

**Co robić**:

- Zdecyduj o czasie każdej fazy i upewnij się, że masz możliwość awaryjnego/wstrzymania, jeśli musisz wprowadzić korekty przed kontynuowaniem
- Zaplanuj pierwszą grupę użytkowników, których chcesz włączyć, aby upewnić się, że otrzymasz opinię, której potrzebujesz, aby przejść do przodu.  Jeśli to możliwe, wybierz aktywną grupę użytkowników, którzy będą przekazywać opinie w odpowiednim czasie
- Podczas planowania każdej fali spróbuj rozpocząć od małej bazy użytkowników (mniej niż 5000 użytkowników). Zwiększ rozmiary grup w miarę wykonywania każdej fali. Dzięki utworzeniu podejścia rozłożonego pozwala na łatwiejsze wstrzymywanie możliwości w razie potrzeby.
