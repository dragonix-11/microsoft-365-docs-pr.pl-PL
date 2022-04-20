---
title: Szacowane i rzeczywiste wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Dowiedz się, dlaczego szacowane i rzeczywiste wyniki wyszukiwania mogą się różnić w przypadku wyszukiwań uruchamianych za pomocą narzędzi zbierania elektronicznych materiałów dowodowych w Office 365.
ms.openlocfilehash: b1e4ba4938e418d8364dfb06b24b6f7a58d6a463
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64938164"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Różnice między szacowanymi i rzeczywistymi wynikami wyszukiwania zbierania elektronicznych materiałów dowodowych

Ten artykuł dotyczy wyszukiwań, które można uruchomić przy użyciu jednego z następujących Microsoft 365 narzędzi zbierania elektronicznych materiałów dowodowych: 

- Wyszukiwanie zawartości
- eDiscovery (Standardowa)

Po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych używane narzędzie zwróci oszacowanie liczby elementów (i ich całkowitego rozmiaru) zgodnych z kryteriami wyszukiwania. Na przykład po uruchomieniu wyszukiwania w portalu zgodności usługi Microsoft Purview szacowane wyniki wyszukiwania są wyświetlane na stronie wysuwanej dla wybranego wyszukiwania.
  
![Szacowanie wyników wyświetlanych na stronie wysuwanego wyszukiwania.](../media/EstimatedSearchResults1.png)
  
Jest to takie samo oszacowanie całkowitego rozmiaru i liczby elementów wyświetlanych w narzędziu eksportu zbierania elektronicznych materiałów dowodowych podczas eksportowania wyników na komputer lokalny oraz w raporcie Podsumowanie eksportu pobranym z wynikami wyszukiwania.
  
**Szacowane wyniki w narzędziu eDiscovery Export**

![Szacowane wyniki w narzędziu eksportu zbierania elektronicznych materiałów dowodowych.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Szacowane wyniki w raporcie podsumowania eksportu**

![Szacowane wyniki wyszukiwania są uwzględniane w raporcie Podsumowanie eksportu.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Jak jednak zauważysz na poprzednim zrzucie ekranu raportu Podsumowanie eksportu, rozmiar i liczba pobranych wyników wyszukiwania są inne niż rozmiar i liczba szacowanych wyników wyszukiwania.
  
![Różnica między szacowanym i pobranym wynikiem wyszukiwania.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Oto kilka przyczyn tych różnic:
  
- **Sposób szacowania wyników**. Oszacowanie wyników wyszukiwania polega tylko na tym, że oszacowanie (a nie rzeczywista liczba) elementów spełniających kryteria zapytania wyszukiwania. Aby skompilować oszacowanie elementów Exchange, lista identyfikatorów komunikatów spełniających kryteria wyszukiwania jest żądana z bazy danych Exchange przez używane narzędzie zbierania elektronicznych materiałów dowodowych. Jednak po wyeksportowaniu wyników wyszukiwania wyszukiwanie jest uruchamiane ponownie, a rzeczywiste komunikaty są pobierane z bazy danych Exchange. Dlatego te różnice mogą wynikać ze sposobu określania szacowanej liczby elementów i rzeczywistej liczby elementów.

- **Zmiany zachodzą między godziną szacowania i eksportowania wyników wyszukiwania**. Podczas eksportowania wyników wyszukiwania wyszukiwanie jest ponownie uruchamiane w celu zebrania najnowszych elementów w indeksie wyszukiwania spełniających kryteria wyszukiwania. Istnieje możliwość utworzenia, wysłania lub odebrania dodatkowych elementów spełniających kryteria wyszukiwania w czasie między zebraniami szacowanych wyników wyszukiwania a wyeksportowaniem wyników wyszukiwania. Istnieje również możliwość, że elementy znajdujące się w indeksie wyszukiwania, gdy wyniki wyszukiwania zostały oszacowane, nie są już dostępne, ponieważ zostały usunięte z lokalizacji zawartości przed wyeksportowaniem wyników wyszukiwania. Jednym ze sposobów rozwiązania tego problemu jest określenie zakresu dat dla wyszukiwania zbierania elektronicznych materiałów dowodowych. Innym sposobem jest wstrzymanie lokalizacji zawartości, aby elementy były zachowywane i nie mogły być czyszczone.

   Poniżej przedstawiono inne problemy, które mogą spowodować różnice między szacowanymi i wyeksportowanymi wynikami wyszukiwania:

  - Zwiększenie liczby elementów podczas korzystania z zapytania daty. Zazwyczaj przyczyną są następujące dwie rzeczy:

  - Przechowywanie wersji w SharePoint. Jeśli dokument zostanie usunięty z witryny, która jest wstrzymana, a wersja dokumentu jest włączona, wszystkie wersje usuniętego dokumentu zostaną zachowane.

  - Elementy kalendarza. Akceptowanie i odrzucanie komunikatów oraz cykliczne spotkania będą automatycznie kontynuować tworzenie nowych elementów w tle ze starymi datami.

  - W przypadku blokad może wystąpić sytuacja, w której ten sam element jest zachowywany w podstawowej skrzynce pocztowej użytkownika i w jego archiwum skrzynki pocztowej. Może się to zdarzyć, gdy użytkownik ręcznie przeniesie element do swojego archiwum.

  - Chociaż rzadko, nawet w przypadku zastosowania blokady, konserwacja wbudowanych elementów kalendarza (które nie są edytowalne przez użytkownika, ale są uwzględniane w wielu wynikach wyszukiwania) może być od czasu do czasu usuwana. To okresowe usuwanie elementów kalendarza spowoduje mniejszą liczbę eksportowanych elementów.

- **Elementy bez certyfikatu**. Elementy, które nie są wymagane do wyszukiwania, mogą powodować różnice między szacowanymi i rzeczywistymi wynikami wyszukiwania. Podczas eksportowania wyników wyszukiwania można dołączyć elementy niewymierne. Jeśli podczas eksportowania wyników wyszukiwania zostaną uwzględnione elementy niezaimportowane, może być więcej elementów, które są eksportowane. Spowoduje to różnicę między szacowanym i wyeksportowanym wynikiem wyszukiwania.

    W przypadku korzystania z narzędzia do wyszukiwania zawartości podczas eksportowania wyników wyszukiwania można dołączyć elementy niewymierne. Liczba niezainicjowanych elementów zwracanych przez wyszukiwanie jest wyświetlana na stronie wysuwanej wraz z innymi szacowanymi wynikami wyszukiwania. Wszystkie niezaimportowane elementy również zostaną uwzględnione w całkowitym rozmiarze szacowanych wyników wyszukiwania. Podczas eksportowania wyników wyszukiwania można dołączyć lub nie dołączyć elementów niewykładowanych. Sposób konfigurowania tych opcji może spowodować różnice między szacowanymi i rzeczywistymi wynikami wyszukiwania, które są pobierane.

- **Eksportowanie wyników wyszukiwania zawartości zawierającego wszystkie lokalizacje zawartości**. Jeśli wyszukiwanie, z których eksportujesz wyniki, było wyszukiwaniem wszystkich lokalizacji zawartości w organizacji, zostaną wyeksportowane tylko niezainicjowane elementy z lokalizacji zawartości zawierające elementy zgodne z kryteriami wyszukiwania. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki wyszukiwania, żadne niezainicjowane elementy w tej skrzynce pocztowej lub witrynie nie zostaną wyeksportowane. Jednak niezainicjowane elementy ze wszystkich lokalizacji zawartości (nawet te, które nie zawierają elementów zgodnych z zapytaniem wyszukiwania) zostaną uwzględnione w szacowanych wynikach wyszukiwania.

    Alternatywnie, jeśli wyszukiwanie, które eksportujesz wyniki z uwzględnionych lokalizacji zawartości, zostaną wyeksportowane nieweksportowane elementy (które nie są wykluczone przez kryteria wyszukiwania) ze wszystkich lokalizacji zawartości określonych w wyszukiwaniu. W tym przypadku szacowana liczba nieweksportowanych elementów i liczba wyeksportowanych elementów bez certyfikatu powinny być takie same.

    Przyczyną nieeksportowania niezaimportowanych elementów z każdej lokalizacji w organizacji jest to, że może to zwiększyć prawdopodobieństwo wystąpienia błędów eksportu i zwiększyć czas potrzebny na wyeksportowanie i pobranie wyników wyszukiwania.

- **Elementy niezaimportowane w SharePoint i OneDrive nie są uwzględniane w szacunkach wyszukiwania**. Elementy bez certyfikatu z witryn SharePoint i kont OneDrive dla Firm nie są uwzględniane w szacowanych wynikach wyszukiwania. Dzieje się tak, ponieważ indeks SharePoint nie zawiera danych dla elementów niewyświetlonych. W szacowaniu wyszukiwania są uwzględniane tylko elementy niezaimportowane ze skrzynek pocztowych. Jeśli jednak podczas eksportowania wyników wyszukiwania zostaną uwzględnione elementy niezawłaszczone, uwzględnione zostaną elementy niezawłaszczone w SharePoint i OneDrive, co zwiększy liczbę faktycznie wyeksportowanych elementów. Spowoduje to różnice między szacowanymi wynikami (które nie obejmują elementów niezaimportowanych w witrynach SharePoint i OneDrive) a rzeczywistymi pobranymi elementami. Reguła dotycząca eksportowania niezainicjowanych elementów tylko z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami wyszukiwania, nadal ma zastosowanie w tej sytuacji.

- **Wersje dokumentów w SharePoint i OneDrive**. Podczas wyszukiwania SharePoint witryn i kont OneDrive wiele wersji dokumentu nie jest uwzględnianych w liczbie szacowanych wyników wyszukiwania. Masz jednak możliwość uwzględnienia wszystkich wersji dokumentów podczas eksportowania wyników wyszukiwania. Jeśli podczas eksportowania wyników wyszukiwania uwzględnisz wersje dokumentów, liczba rzeczywista (i całkowity rozmiar) wyeksportowanych elementów zostanie zwiększona.

- **SharePoint folderów**. Jeśli foldery w SharePoint pasują do zapytania wyszukiwania, na przykład wyszukiwanie według daty, oszacowanie wyszukiwania będzie zawierać liczbę folderów z zakresem dat ostatniej modyfikacji (ale nie elementów w tych folderach). Podczas eksportowania wyników wyszukiwania elementy w folderze są eksportowane, ale rzeczywisty folder nie jest eksportowany. W rezultacie liczba wyeksportowanych elementów będzie większa niż liczba szacowanych wyników wyszukiwania. Jeśli folder jest pusty, liczba wyeksportowanych rzeczywistych wyników wyszukiwania zostanie zmniejszona o jeden element, ponieważ rzeczywisty folder nie jest eksportowany.

   > [!NOTE]
   > Podczas uruchamiania wyszukiwania opartego na zapytaniach można wykluczyć foldery SharePoint, dodając następujący warunek do zapytania: `NOT(ContentType:folder)`.

- **SharePoint list**. Jeśli nazwa listy SharePoint jest zgodna z zapytaniem wyszukiwania, oszacowanie wyszukiwania będzie zawierać liczbę wszystkich elementów na liście. Podczas eksportowania wyników wyszukiwania lista (i elementy listy) jest eksportowana jako pojedynczy plik CSV. Spowoduje to zmniejszenie rzeczywistej liczby faktycznie wyeksportowanych elementów. Jeśli lista zawiera załączniki, załączniki zostaną wyeksportowane jako oddzielne dokumenty, co zwiększy również liczbę wyeksportowanych elementów.

   > [!NOTE]
   > Podczas uruchamiania wyszukiwania opartego na zapytaniach można wykluczyć listy SharePoint, dodając następujący warunek do zapytania: `NOT(ContentType:list)`.

- **Nieprzetworzone formaty plików a wyeksportowane formaty plików**. W przypadku Exchange elementów szacowany rozmiar wyników wyszukiwania jest obliczany przy użyciu nieprzetworzonych Exchange rozmiarów komunikatów. Jednak wiadomości e-mail są eksportowane w pliku PST lub jako pojedyncze wiadomości (sformatowane jako pliki EML). Obie te opcje eksportu używają innego formatu pliku niż nieprzetworzone komunikaty Exchange, co powoduje, że całkowity wyeksportowany rozmiar pliku jest inny niż szacowany rozmiar pliku.

- **De-duplikowanie elementów Exchange podczas eksportowania**. W przypadku Exchange elementów anulowanie duplikowania zmniejsza liczbę eksportowanych elementów. Podczas eksportowania można anulować duplikowanie wyników wyszukiwania. W przypadku Exchange wiadomości oznacza to, że eksportowane jest tylko jedno wystąpienie wiadomości, nawet jeśli ta wiadomość może znajdować się w wielu skrzynkach pocztowych. Szacowane wyniki wyszukiwania obejmują każde wystąpienie komunikatu. Jeśli więc wybierzesz opcję anulowania duplikowania podczas eksportowania wyników wyszukiwania, rzeczywista liczba eksportowanych elementów może być znacznie mniejsza niż szacowana liczba elementów.

Raport wyników wyszukiwania (plik Results.csv) zawiera wpis dla każdej zduplikowanej wiadomości i identyfikuje źródłową skrzynkę pocztową, w której znajduje się zduplikowana wiadomość. Pomaga to zidentyfikować wszystkie skrzynki pocztowe zawierające zduplikowaną wiadomość.

> [!NOTE]
> Jeśli nie wybierzesz opcji **Dołącz elementy, które są zaszyfrowane lub mają nierozpoznany format** podczas eksportowania wyników wyszukiwania lub pobierania raportów, raporty o błędach indeksu są pobierane, ale nie mają żadnych wpisów. Nie oznacza to, że nie ma żadnych błędów indeksowania. Oznacza to po prostu, że niezaimportowane elementy nie zostały uwzględnione w eksporcie.
