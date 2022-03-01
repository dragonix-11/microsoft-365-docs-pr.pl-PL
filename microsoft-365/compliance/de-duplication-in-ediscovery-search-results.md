---
title: De-duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/21/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5af334b6-a15d-4f73-97f8-1423457d9f6b
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak wyeliminować zduplikowane wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych w celu wyeksportowania tylko jednej kopii wiadomości e-mail.
ms.openlocfilehash: d09a0e09166928627be01d623963146cfd416bd2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032114"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>De-duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych

W tym artykule opisano działanie duplikowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych i wyjaśniono ograniczenia algorytmu de duplikowania.
  
W przypadku korzystania z narzędzi zbierania elektronicznych materiałów dowodowych w celu wyeksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych można dezduplikować eksportowane wyniki. Co to oznacza? Gdy włączysz duplikowanie (domyślnie de duplikowanie nie jest włączone), jest eksportowana tylko jedna kopia wiadomości e-mail, mimo że w przeszukanych skrzynkach pocztowych mogło znaleźć się wiele wystąpień tej samej wiadomości. Duplikowanie pomaga zaoszczędzić czas, zmniejszając liczbę elementów do przejrzenia i przeanalizowania po wyeksportowaniu wyników wyszukiwania. Należy jednak zrozumieć, jak działa duplikowanie i pamiętać, że algorytm ma ograniczenia, które mogą powodować oznaczenie unikatowego elementu jako duplikatu w trakcie procesu eksportowania.
  
## <a name="how-duplicate-messages-are-identified"></a>Jak są identyfikowane zduplikowane wiadomości

Narzędzia zbierania elektronicznych materiałów dowodowych używają kombinacji następujących właściwości poczty e-mail w celu określenia, czy wiadomość jest duplikatem:
  
- **InternetMessageId** — ta właściwość określa identyfikator wiadomości e-mail w Internecie, który jest unikatowy identyfikator globalny, który odwołuje się do określonej wersji określonej wiadomości. Ten identyfikator jest generowany przez program kliencki poczty e-mail nadawcy lub hostujący system poczty e-mail, który wysyła wiadomość. Jeśli użytkownik wyśle wiadomość do więcej niż jednego adresata, identyfikator wiadomości internetowej będzie taki sam dla każdego wystąpienia wiadomości. Kolejne poprawki oryginalnej wiadomości otrzymają inny identyfikator wiadomości. 

- **KonwersacjeTopic** — ta właściwość określa temat wątku konwersacji w wiadomości. Wartość właściwości **ConversationTopic** to ciąg opisujący ogólny temat konwersacji. Konwersacja składa się z wiadomości początkowej i wszystkich wiadomości wysłanych w odpowiedzi na wiadomość początkową. Wiadomości w tej samej konwersacji mają tę samą wartość właściwości **ConversationTopic** . Wartość tej właściwości to zazwyczaj wiersz Temat z początkowej wiadomości, która zaimkowała konwersację. 

- **BodyTagInfo** — to wewnętrzna Exchange magazynu danych. Wartość tej właściwości jest obliczana przez sprawdzenie różnych atrybutów w treści wiadomości. Ta właściwość służy do identyfikowania różnic w treści wiadomości. 

W trakcie procesu eksportowania zbierania elektronicznych materiałów dowodowych te trzy właściwości są porównywane dla każdej wiadomości, która jest spełniająca kryteria wyszukiwania. Jeśli te właściwości są identyczne dla dwóch (lub większej liczby) wiadomości, te wiadomości zostaną określone jako duplikaty, w wyniku czego tylko jedna kopia wiadomości zostanie wyeksportowana, jeśli włączono duplikowanie. Eksportowana wiadomość jest znana jako "element źródłowy". Informacje o zduplikowanych wiadomościach są zawarte **w raportach** Results.csvi **Manifest.xml** , które są zawarte w eksportowanych wynikach wyszukiwania. W pliku **Results.csv** zduplikowana wiadomość jest identyfikowana przez posiadanie wartości w kolumnie Duplikuj **do** elementu. Wartość w tej kolumnie odpowiada wartości w kolumnie Tożsamość elementu  dla eksportowanej wiadomości. 
  
Na poniższej ilustracji przedstawiono sposób wyświetlania zduplikowanych wiadomości **w** raportachResults.csv **Manifest.xmleksportowanych** z wynikami wyszukiwania. Te raporty nie zawierają wcześniej opisanych właściwości poczty e-mail, które są używane w algorytmie de duplikowania. Zamiast tego raporty zawierają właściwość **Tożsamość** elementu, która jest przypisywana do elementów przez Exchange magazyn. 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv (przeglądany w programie Excel)
  
![Wyświetlanie informacji o zduplikowanych elementach w Results.csv raportu.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml (przeglądany w programie Excel)
  
![Wyświetlanie informacji o zduplikowanych elementach w Manifest.xml raportu.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
Ponadto w raportach eksportu są uwzględniane inne właściwości zduplikowanych wiadomości. Dotyczy to skrzynki pocztowej, w których znajduje się zduplikowana wiadomość, niezależnie od tego, czy wiadomość została wysłana do grupy dystrybucyjnej, i czy wiadomość została przesłana do innego użytkownika, czy do innego użytkownika.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Ograniczenia algorytmu de duplikowania

Istnieją pewne znane ograniczenia algorytmu deplikacji, które mogą powodować oznaczanie unikatowych elementów jako duplikatów. Ważne jest zrozumienie tych ograniczeń, aby można było zdecydować, czy użyć opcjonalnej funkcji de duplikowania.
  
W jednej sytuacji funkcja deplikacji może omyłowo zidentyfikować wiadomość jako duplikat, a nie wyeksportować go (ale nadal cytować jako duplikat w raportach eksportu). Są to wiadomości, które są edytowane, ale nie są wysyłane przez użytkownika. Załóżmy na przykład, że użytkownik zaznaczy wiadomość w programie Outlook, skopiuje jej treść, a następnie wklei ją do nowej wiadomości. Następnie użytkownik zmieni jedną z kopii, usuwając lub dodając załącznik albo zmieniając wiersz tematu lub treść. Jeśli te dwa wiadomości są zgodne z zapytaniem wyszukiwania zbierania elektronicznych materiałów dowodowych, tylko jedna z nich zostanie wyeksportowana, jeśli funkcja deplikacji jest włączona podczas eksportowania wyników wyszukiwania. Mimo że zmieniono oryginalną wiadomość lub skopiowaną wiadomość, żadne ze zmienionych wiadomości nie zostały wysłane, a zatem wartości właściwości **InternetMessageId**, **ConversationTopic** i **BodyTagInfo** nie zostały zaktualizowane. Jednak jak wyjaśniono wcześniej, obie wiadomości będą wyświetlane w raportach eksportu. 
  
Unikatowe wiadomości można również oznaczać jako duplikaty po włączeniu funkcji ochrony strony podczas kopiowania w czasie pisania, na przykład w przypadku skrzynki pocztowej ze względu na to, że jest ona włączona w związku z postępowaniem sądowym lub In-Place sądowym. Funkcja Kopiowania w zapisywaniu kopiuje oryginalną wiadomość (i zapisuje ją w folderze Wersje folderu Elementy do odzyskania użytkownika) przed zapisaniem poprawki w oryginalnym elementie. W tym przypadku poprawiona kopia i oryginalna wiadomość (w folderze Elementy do odzyskania) mogą być traktowane jako zduplikowane wiadomości i dlatego tylko jedna z nich zostałaby wyeksportowana.
  
> [!IMPORTANT]
> Jeśli ograniczenia algorytmu deplikacji mogą mieć wpływ na jakość wyników wyszukiwania, nie należy włączać de duplikowania podczas eksportowania elementów. Jeśli sytuacja opisana w tej sekcji jest mało prawdopodobna w wynikach wyszukiwania i chcesz zmniejszyć liczbę elementów, które najprawdopodobniej są duplikatami, rozważ włączenie odduplikowania. 
  
## <a name="more-information"></a>Więcej informacji

- Informacje zawarte w tym artykule mają zastosowanie w przypadku eksportowania wyników wyszukiwania za pomocą jednego z następujących narzędzi zbierania elektronicznych materiałów dowodowych:

  - Wyszukiwanie zawartości w Centrum zgodności w Office 365

  - In-Place zbierania elektronicznych materiałów dowodowych w programie Exchange Online

  - Centrum zbierania elektronicznych materiałów dowodowych w u SharePoint Online

- Aby uzyskać więcej informacji na temat eksportowania wyników wyszukiwania, zobacz:

  - [Eksportowanie wyszukiwania zawartości](export-search-results.md)

  - [Eksportowanie raportu przeszukiwania zawartości](export-a-content-search-report.md)

  - [Eksportowanie In-Place wyszukiwania zbierania elektronicznych materiałów dowodowych do pliku PST](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - [Eksportowanie zawartości i tworzenie raportów w Centrum zbierania elektronicznych materiałów dowodowych](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
