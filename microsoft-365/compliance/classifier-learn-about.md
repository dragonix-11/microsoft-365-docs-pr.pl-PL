---
title: Dowiedz się więcej o przeszkolnych klasyfikatorach
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Klasyfikatorzy przeszkoliwczy mogą rozpoznawać różne typy zawartości do oznaczania etykiet lub stosowania zasad, dając im próbki dodatnie i ujemne do oglądu.
ms.openlocfilehash: 50d20c3a40b21696c06064b548d7766684fb12a0
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015423"
---
# <a name="learn-about-trainable-classifiers"></a>Dowiedz się więcej o przeszkolnych klasyfikatorach

Klasyfikowanie i oznaczanie zawartości w celu ochrony i właściwej obsługi jest punktem wyjścia w dyscyplinie ochrony informacji. Microsoft 365 są trzy sposoby klasyfikowania zawartości.

## <a name="manually"></a>Ręcznie

Klasyfikacja ręczna wymaga ludzkich decyzji i działań. Użytkownicy i administratorzy stosują ich do zawartości w przypadku jej napotkania. Możesz użyć istniejących etykiet i typów informacji poufnych lub użyć utworzonych niestandardowych.  Następnie możesz chronić zawartość i zarządzać jej rozsyłaniem.

## <a name="automated-pattern-matching"></a>Automatyczne dopasowywanie wzorców

Ta kategoria mechanizmów klasyfikacji obejmuje znajdowanie zawartości przez:

- Słowa kluczowe lub wartości metadanych (język zapytania słów kluczowych).
- Stosowanie wcześniej zidentyfikowanych wzorców informacji poufnych, takich jak ubezpieczenia, kart kredytowych lub numerów kont bankowych (definicje jednostek typu informacji [poufnych)](sensitive-information-type-entity-definitions.md).
- Rozpoznanie elementu, ponieważ jest odmianą szablonu [(drukowanie palcem w dokumencie).](document-fingerprinting.md)
- Używanie dokładnego dopasowania [ciągów do danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Etykiety wrażliwości i przechowywania mogą być następnie automatycznie stosowane w celu udostępnień zawartości do użycia [](dlp-learn-about-dlp.md) w sekcji Informacje na temat ochrony przed utratą danych i automatycznego stosowania zasad przechowywania [etykiet przechowywania](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Klasyfikatory

Ta metoda klasyfikacji nadaje się dobrze do zawartości, która nie jest łatwo identyfikowana za pomocą metod ręcznego lub automatycznego dopasowywania wzorców. Ta metoda klasyfikacji polega bardziej na identyfikacji elementu za pomocą klasyfikatora na podstawie tego, co to jest, a nie według elementów, które się w nim znajdują (dopasowywanie wzorca). Klasyfikator uczy się, jak zidentyfikować typ zawartości, patrząc na setki przykładów zawartości, która Cię interesuje, klasyfikowanie.

> [!NOTE]
> W wersji zapoznawczej — klasyfikatory przeszkolne można wyświetlać w Eksploratorze zawartości, rozwijając klasyfikatorów przeszkolnych **w** panelu filtrów. Klasyfikatorzy przeszkoni będą automatycznie wyświetlać liczbę zdarzeń znalezionych w SharePoint, Teams i OneDrive, bez konieczności oznaczania etykiet.
> Jeśli nie chcesz korzystać z tej funkcji, musisz złożyć żądanie do pomocy technicznej firmy Microsoft w celu wyłączenia klasyfikacji "poza polem". Spowoduje to wyłączenie skanowania zawartości poufnej i oznaczonej etykietą przed utworzeniem zasad tworzenia etykiet.

### <a name="where-you-can-use-classifiers"></a>Gdzie można używać klasyfikatorów

Klasyfikatory są dostępne do użycia jako warunek Office [](apply-sensitivity-label-automatically.md)etykiet wrażliwości, automatyczne stosowanie zasad etykiet przechowywania na podstawie warunku [](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) i zgodności [komunikacji](communication-compliance.md). 

Etykiety wrażliwości mogą używać klasyfikatorów jako warunków ( zobacz [Automatyczne stosowanie etykiet wrażliwości do zawartości](apply-sensitivity-label-automatically.md)).

> [!IMPORTANT]
> Klasyfikatory działają tylko w przypadku elementów, które nie są szyfrowane.

## <a name="types-of-classifiers"></a>Typy klasyfikatorów

- **Wstępnie przeszkolone klasyfikatory** — firma Microsoft utworzyła i wstępnie przeszkoliła wiele klasyfikatorów, z których możesz zacząć korzystać bez szkolenia. Te klasyfikatory będą wyświetlane ze stanem `Ready to use`.
- **Niestandardowe klasyfikatory** przeszkolone — jeśli klasyfikacja wykracza poza zakres, który obejmuje wstępnie przeszkolone klasyfikatory, możesz tworzyć i przeszkolenie swoich klasyfikatorów.

### <a name="pre-trained-classifiers"></a>Wstępnie przeszkolone klasyfikatory

Microsoft 365 zawiera wiele wstępnie przeszkolonych klasyfikatorów:

> [!CAUTION]
> Wyszkodziliśmy wstępnie  przeszkolonych klasyfikatorów w języku obraźliwym, ponieważ został w nim wyszkolonych duża liczba wyników fałszywie dodatnich. Nie należy go używać, a jeśli obecnie z niego korzystasz, należy z niego przenieść procesy biznesowe. Zamiast tego zalecamy  **używanie wstępnie** przeszkolonych klasyfikatorów pod preszkową podpowiadanie **zagrożenia,** profanowania i molestowania.

- **Życiorysy**: wykrywa pliki docx, .pdf, rtf, .txt elementy, które są kontami tekstowych osobistych, edukacji, kwalifikacji zawodowych, doświadczenia zawodowego kandydata i innych danych osobowych
- Kod **źródłowy: wykrywa** elementy zawierające zestaw instrukcji i instrukcji napisanych w 25 najlepszych używanych językach programowania komputerowego w serwisie GitHub: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Wykrywa zawartość w msg, as, h, c, cs, cc, cpp, hpp, cxx. hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, pod, .php, .phar, .php4, .pyc, . R, r, rda, . RData, rds, rb, .scala, sc, sh, .swift.

> [!NOTE]
> Kod źródłowy jest przeszkolony w celu wykrywania, kiedy zbiorcza część tekstu jest kodem źródłowym. Nie wykrywa tekstu kodu źródłowego przeplatanego zwykłego tekstu.

- **Umowy**: Wykrywa zawartość związaną z umowami prawnie, takimi jak umowy o nie ujawnianiu informacji, oświadczenia o pracy, umowy pożyczki i dzierżawy, umowy o zatrudnieniu i umowy, które nie konkurowają ze sobą. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg i eml.
- **Język** dyskryminujący: wykrywa jawny język dyskryminujący i jest poufny na dyskryminujący język dla społeczności amerykańskich/czarnych w porównaniu z innymi społecznościami.
- **Finanse**. Wykrywa zawartość w kategoriach finansów korporacyjnych, księgowości, banku i inwestycji. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsm, .xls, .csv, xltx, xltm, xltt, xlam, xla.
- **Molestowanie**: Wykrywa określoną kategorię obraźliwych elementów tekstowych w języku powiązanych z obraźliwym zachowaniem kierowanym do jednej lub wielu osób ze względu na następujące cechy: rasa, płeć, płeć, orientacja erocyjna, wiek, niepełnosprawność. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp i svg.
- **Służba zdrowia**: Wykrywa zawartość w aspektach administrowania medycznego i opieki zdrowotnej, takich jak usługi medyczne, diagnozy, leczenia, roszczenia itp. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsm, .xls, .csv, xltx, xltm, xltt, xlam, xla.
- **Kadry**: Wykrywa zawartość w kategoriach związanych z zasobami ludzkimi, które są powiązane z tematem, które mogą być schowanie, rozmawianie na rozmowę kwalifikacyjną, zatrudnienie, szkolenia, ocenianie, ostrzeżenie i zakończenie. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsm, .xls, .csv, xltx, xltm, xltt, xlam, xla.
- **ADRES IP**: Wykrywa zawartość kategorii związanych z własnością intelektualną, takich jak tajemnice handlowe i podobne poufne informacje. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsm, .xls, .csv, xltx, xltm, xltt, xlam, xla.
- **IT**: Wykrywa zawartość w kategoriach technologii informacyjnych i na przykład ustawień sieci, zabezpieczeń informacji, sprzętu i oprogramowania. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsm, .xls, .csv, xltx, xltm, xltt, xlam, xla.
- **Sprawy prawne**. Wykrywa zawartość kategorii związanych ze sprawami prawnymi, takimi jak procesy sądowe, procesy, zobowiązania prawne, terminologia prawnymi, prawo i prawo. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg i eml.
- **Zaopatrzenie**. Wykrywa zawartość kategorii cytowanych, cytowanych, zakupów oraz płacenia za dostawy produktów i usług. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .xlsx, xlsm, xlsb, .xls, .csv, xltx, xltm, xlt, xlam i xla.
- **Profanity**: wykrywa konkretną kategorię obraźliwych elementów tekstowych w językach, które zawierają wyrażenia kłopotliwe dla większości osób. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp i svg.
- **Podatek**: Wykrywa zawartość relacyjną o podatku, taką jak planowanie podatkowe, formularze podatkowe, zgłaszanie podatków, przepisy podatkowe. Wykrywa zawartość w plikach .docx, docm, .doc, dotx, dotm, dot, .pdf, rtf, .txt, one, msg, eml, .pptx, pptm, .ppt, potx, potm, pot, ppsx, ppsx, ppsm, pps, ppam, ppa, .xlsx, xlsm, xlsb, .xls, .csv, xltx, xltm, xltm, xlam, xla.
- **Zagrożenie**: Wykrywa konkretną kategorię obraźliwych elementów tekstowych w językach związanych z zagrożeniami, które mogą dotyczyć przemocy lub wyczynów wyszkodzeniom fizycznym bądź szkodom w osobie bądź mieniu. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp i svg.

Są one wyświetlane w **Centrum zgodności platformy Microsoft 365** >  **KlasyfikacjaDanychTrainable** >  **klasyfikatorów** ze stanem `Ready to use`.

![klasyfikatory wstępnie przeszkolone.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Należy pamiętać, że klasyfikatory obraźliwego języka, molestowania, wulgarności, przemocy i zagrożeń działają tylko z tekstem, który można wyszukać, i nie jest to pełna lista terminów lub języka we wszystkich tych obszarach. Ponadto standardy językowe i kulturowe stale się zmieniają i w związku z tymi uwarunkowaniami firma Microsoft zastrzega sobie prawo do według własnego uznania do aktualizowania tych klasyfikatorów. Klasyfikatory mogą pomóc Twojej organizacji w wykrywaniu tych obszarów, natomiast klasyfikatory nie są przeznaczone wyłącznie do wykrywania takiego języka lub adresowania go. Twoja organizacja, a nie firma Microsoft ani jej przedstawicielscy, ponosi odpowiedzialność za wszystkie decyzje związane z monitorowaniem, skanowaniem, blokowaniem, usuwaniem i przechowywaniem wszelkiej zawartości wskazanej przez wstępnie przeszkolonych klasyfikatorów, w tym za zgodność z lokalną prywatnością i innymi obowiązującymi przepisami prawa. Firma Microsoft zachęca do konsultowania się z doradcą prawnym przed wdrożeniem i użyciem.

Wstępnie przeszkolone klasyfikatory mogą skanować zawartość w tych językach:

• Chiński (uproszczony) • angielski • francuski • niemiecki • włoski • japoński • portugalski • hiszpański

### <a name="custom-classifiers"></a>Klasyfikatory niestandardowe

Gdy wstępnie przeszkolone klasyfikatory nie spełniają Twoich potrzeb, możesz tworzyć i szkolenie swoich klasyfikatorów. Utworzenie własnej organizacji wymaga znacznie więcej pracy, ale będą one lepiej dostosowane do potrzeb Twojej organizacji.

Aby utworzyć niestandardowego, przeszkoliwnego klasyfikatora, zacznij od podawania przykładów, które z pewnością należy do danej kategorii. Gdy przetwarza te przykłady, można je przetestować, podając zarówno pasujące, jak i niepasujący przykłady. Następnie klasyfikator podpowiada, czy dany element należy do kategorii, która się znajduje. Następnie należy potwierdzić wyniki, sortując prawdziwe wartości dodatnie, prawdziwe wartości ujemne, wyniki fałszywie dodatnie i wyniki fałszywie ujemne, aby zwiększyć dokładność jego prognoz. 

Po opublikowaniu klasyfikator sortuje elementy w lokalizacjach, takich jak SharePoint Online, Exchange i OneDrive klasyfikuje zawartość. Po opublikowaniu klasyfikatora możesz nadal przeszkolić go przy użyciu procesu opinii podobnego do procesu początkowego szkolenia.

Możesz na przykład utworzyć klasyfikatorów przeszkolnych dla:

- Dokumenty prawne — takie jak uprawnienie klienta obsługi prawnej, dokumenty zamykające, oświadczenie o pracy
- Strategiczne dokumenty biznesowe — takie jak informacje prasowe, fuzje i pozyskiwanie, transakcje, plany biznesowe lub marketingowe, własność intelektualna, patenty, dokumenty projektowe
- Informacje o cenach — na przykład faktury, oferty cenowe, zlecenia robocze, dokumenty do przeniesienia
- Informacje finansowe — na przykład inwestycje w organizacji, wyniki kwartalne lub roczne

#### <a name="process-flow-for-creating-custom-classifiers"></a>Przepływ procesu tworzenia niestandardowych klasyfikatorów

Tym przepływem jest tworzenie i publikowanie klasyfikatora do użytku w rozwiązaniach zgodności, takich jak zasady przechowywania i nadzór nad komunikacją. Aby uzyskać więcej szczegółowych informacji na temat tworzenia niestandardowego, przeszkotnego klasyfikatora, zobacz [Tworzenie niestandardowego klasyfikatora](classifier-get-started-with.md).

![Niestandardowy klasyfikator przepływu procesu.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Ponowne szkolenie klasyfikatorów

Możesz pomóc w zwiększaniu dokładności wszystkich niestandardowych przeszkolnych klasyfikatorów oraz udostępniając im opinie na temat dokładności klasyfikacji, która jest przez nich klasyfikowana. To tak zwane ponowne szkolenie i następuje po tym przepływie pracy.

> [!NOTE]
> Wstępnie przeszkolonych klasyfikatorów nie można ponownie przeszkolić.

![Klasyfikator ponowne szkolenie przepływu pracy.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Zobacz też

- [Etykiety przechowywania](retention.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Drukowanie palcem w dokumencie](document-fingerprinting.md)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
