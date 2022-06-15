---
title: Dowiedz się więcej o klasyfikatorach z możliwością szkolenia
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
description: Klasyfikatory z możliwością trenowania mogą rozpoznawać różne typy zawartości do etykietowania lub aplikacji zasad, dając jej pozytywne i negatywne próbki do obejrzenia.
ms.openlocfilehash: 955e94aad0c7c4c20a020a76ebf4b4ffc1871d9a
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078815"
---
# <a name="learn-about-trainable-classifiers"></a>Dowiedz się więcej o klasyfikatorach z możliwością szkolenia

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Klasyfikowanie i etykietowanie zawartości, aby można było ją odpowiednio chronić i obsługiwać, jest miejscem początkowym dla dziedziny ochrony informacji. Microsoft 365 ma trzy sposoby klasyfikowania zawartości.

## <a name="manually"></a>Ręcznie

Klasyfikacja ręczna wymaga ludzkiego osądu i działania. Użytkownicy i administratorzy stosują je do zawartości w miarę jej występowania. Możesz użyć wcześniej istniejących etykiet i typów informacji poufnych lub użyć niestandardowych utworzonych.  Następnie możesz chronić zawartość i zarządzać jej dyspozycją.

## <a name="automated-pattern-matching"></a>Automatyczne dopasowywanie wzorców

Ta kategoria mechanizmów klasyfikacji obejmuje znajdowanie zawartości według:

- Słowa kluczowe lub wartości metadanych (język zapytań słów kluczowych).
- Używanie wcześniej zidentyfikowanych wzorców informacji poufnych, takich jak zabezpieczenia społeczne, karty kredytowe lub numery kont bankowych [(definicje jednostek typu informacje poufne).](sensitive-information-type-entity-definitions.md)
- Rozpoznawanie elementu, ponieważ jest to odmiana szablonu [(drukowanie palcem dokumentu).](document-fingerprinting.md)
- Przy użyciu obecności dokładnych ciągów [dokładne dopasowanie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Etykiety poufności i przechowywania można następnie automatycznie stosować, aby udostępnić zawartość do użycia w [artykule Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md) i [automatycznych zasadach stosowania etykiet przechowywania](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Klasyfikatorów

Ta metoda klasyfikacji jest odpowiednia dla zawartości, która nie jest łatwo identyfikowana za pomocą metod ręcznego lub zautomatyzowanego dopasowywania wzorców. Ta metoda klasyfikacji polega bardziej na używaniu klasyfikatora do identyfikowania elementu na podstawie tego, czym jest element, a nie elementów znajdujących się w elemencie (dopasowywanie wzorca). Klasyfikator dowie się, jak zidentyfikować typ zawartości, przeglądając setki przykładów zawartości, którą chcesz sklasyfikować.

> [!NOTE]
> W wersji zapoznawczej — klasyfikatory z możliwością trenowania można wyświetlić w Eksploratorze zawartości, rozwijając pozycję **Klasyfikatory klasyfikujące możliwość** trenowania w panelu filtrów. Klasyfikatory z możliwością trenowania automatycznie wyświetlają liczbę zdarzeń znalezionych w SharePoint, Teams i OneDrive bez konieczności etykietowania.
> Jeśli nie chcesz korzystać z tej funkcji, musisz wysłać żądanie z pomoc techniczna firmy Microsoft, aby wyłączyć klasyfikację out-of-the-box. Spowoduje to wyłączenie skanowania poufnej i oznaczonej zawartości przed utworzeniem zasad etykietowania.

### <a name="where-you-can-use-classifiers"></a>Gdzie można używać klasyfikatorów

Klasyfikatory są dostępne do użycia jako warunek [Office automatycznego etykietowania z etykietami poufności](apply-sensitivity-label-automatically.md), [automatycznego stosowania zasad etykiet przechowywania na podstawie warunku](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) i [zgodności z komunikacją](communication-compliance.md). 

Etykiety poufności mogą używać klasyfikatorów jako warunków. Zobacz [Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Klasyfikatory działają tylko z elementami, które nie są szyfrowane.

## <a name="types-of-classifiers"></a>Typy klasyfikatorów

- **wstępnie wytrenowane klasyfikatory** — firma Microsoft utworzyła i wstępnie wytrenowała wiele klasyfikatorów, których można zacząć używać bez ich trenowania. Te klasyfikatory będą wyświetlane ze stanem `Ready to use`.
- **niestandardowe klasyfikatory trenowalne** — jeśli masz wymagania klasyfikacji wykraczające poza to, co obejmują wstępnie wytrenowane klasyfikatory, możesz utworzyć i wytrenować własne klasyfikatory.

### <a name="pre-trained-classifiers"></a>Wstępnie wytrenowane klasyfikatory

Microsoft 365 zawiera wiele wstępnie wytrenowanych klasyfikatorów:

- **Adult, Racy i Gory**: wykrywa obrazy tych typów. Obrazy muszą mieć rozmiar od 50 kilobajtów (KB) do 4 megabajtów (MB) i być większe niż 50 x 50 pikseli w wymiarach wysokości x szerokości. Skanowanie i wykrywanie są obsługiwane w przypadku Exchange Online wiadomości e-mail oraz Microsoft Teams kanałów i czatów. Wykrywa zawartość w plikach jpeg, .png, .gif i .bmp.

- **Umowy**: Wykrywa zawartość związaną z umowami prawnymi, takimi jak umowy o zachowaniu poufności, oświadczenia o pracy, umowy pożyczki i dzierżawy, umowy o pracę i umowy o zachowaniu konkurencji. Wykrywa zawartość w plikach .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Życiorysy**: wykrywa dokumenty, .pdf, rtf, .txt elementy, które są tekstowymi kontami osobistymi, edukacyjnymi, zawodowymi, doświadczeniami służbowymi i innymi danymi identyfikacyjnymi wnioskodawcy

- **Kod źródłowy**: wykrywa elementy zawierające zestaw instrukcji i instrukcji napisanych w 25 najlepszych używanych językach programowania komputerowego na GitHub: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Wykrywa zawartość w plikach .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . RData, .rds, .rb, .scala, .sc, .sh, .swift files.

- **Skargi klientów**: klasyfikator skarg klientów wykrywa opinie i skargi dotyczące produktów lub usług organizacji. Ten klasyfikator może pomóc w spełnieniu wymagań regulacyjnych dotyczących wykrywania i klasyfikowania skarg, takich jak wymagania Consumer Financial Protection Bureau i Food and Drug Administration. W przypadku zgodności z usługą Communications wykrywa zawartość w plikach msg i eml. W pozostałych usługach Microsoft Purview Information Protection wykrywa zawartość w plikach .docx, .pdf, .txt, rtf, .jpg, jpeg, .png, .gif, .bmp, .svg.

- **Dyskryminacja**: Wykrywa jawny dyskryminujący język i jest wrażliwy na dyskryminujący język wobec społeczności Afroamerykańskich/Czarnych w porównaniu z innymi społecznościami.

- **Finanse**: wykrywa zawartość w kategoriach finansów korporacyjnych, księgowości, gospodarki, bankowości i inwestycji. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, xltx, .xltm, .xlt, .xlt, .xlam, .xla files.

- **Molestowanie**: Wykrywa określoną kategorię obraźliwych elementów tekstowych języka związanych z obraźliwym zachowaniem skierowanym do jednej lub wielu osób na podstawie następujących cech: rasa, pochodzenie etniczne, religia, pochodzenie narodowe, płeć, orientacja seksualna, wiek, niepełnosprawność. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp, svg.

- **Opieka zdrowotna**: Wykrywa zawartość w aspektach administracji medycznej i opieki zdrowotnej, takich jak usługi medyczne, diagnozy, leczenie, roszczenia itp. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, xltx, .xltm, .xlt, .xlt, .xlam, .xla files.

- **Kadr**: Wykrywa zawartość w kategoriach związanych z zasobami ludzkimi rekrutacji, rozmowy kwalifikacyjnej, zatrudniania, szkolenia, oceny, ostrzeżenia i zakończenia. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, xltx, .xltm, .xlt, .xlt, .xlam, .xla files.

- **Adres IP**: wykrywa zawartość kategorii związanych z własnością intelektualną, takich jak wpisy tajne i podobne informacje poufne. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, xltx, .xltm, .xlt, .xlt, .xlam, .xla files.

- **IT**: Wykrywa zawartość w kategoriach technologii informatycznych i cyberbezpieczeństwa, takich jak ustawienia sieci, zabezpieczenia informacji, sprzęt i oprogramowanie. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, xltx, .xltm, .xlt, .xlt, .xlam, .xla files.

- **Sprawy prawne**: Wykrywa treści w kategoriach prawnych, takich jak spory sądowe, proces prawny, obowiązek prawny, terminologia prawna, prawo i ustawodawstwo. Wykrywa zawartość w plikach .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Zaopatrzenie**: Wykrywa zawartość w kategoriach licytacji, ofert, zakupów i płacenia za dostawę towarów i usług. Wykrywa zawartość w plikach .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Wulgaryzmy**: wykrywa określoną kategorię obraźliwych elementów tekstowych języka, które zawierają wyrażenia, które zawstydzają większość ludzi.

- **Życiorysy**: wykrywa dokumenty, .pdf, rtf, .txt elementy, które są tekstowymi kontami osobistymi, edukacyjnymi, zawodowymi, doświadczeniami służbowymi i innymi danymi identyfikacyjnymi wnioskodawcy

- **Kod źródłowy**: wykrywa elementy zawierające zestaw instrukcji i instrukcji napisanych w 25 najlepszych używanych językach programowania komputerowego na GitHub: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script.

    > [!NOTE]
    > Kod źródłowy jest wytrenowany do wykrywania, kiedy większość tekstu to kod źródłowy. Nie wykrywa tekstu kodu źródłowego, który jest przeplatany zwykłym tekstem.

- **Podatek**: Wykrywa zawartość relacji podatkowych, takich jak planowanie podatkowe, formularze podatkowe, zgłoszenia podatkowe, przepisy podatkowe. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla files.

- **Zagrożenie**: wykrywa określoną kategorię obraźliwych elementów tekstowych języka związanych z groźbami popełnienia przemocy lub wyrządzenia fizycznej krzywdy lub szkody osobie lub mienia.
- **Wulgaryzmy**: wykrywa określoną kategorię obraźliwych elementów tekstowych języka, które zawierają wyrażenia, które zawstydzają większość ludzi. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp, svg.
- **Podatek**: Wykrywa zawartość relacji podatkowych, takich jak planowanie podatkowe, formularze podatkowe, zgłoszenia podatkowe, przepisy podatkowe. Wykrywa zawartość w .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla files.
- **Zagrożenie**: wykrywa określoną kategorię obraźliwych elementów tekstowych języka związanych z groźbami popełnienia przemocy lub wyrządzenia fizycznej krzywdy lub szkody osobie lub mienia. Wykrywa zawartość w plikach msg, .docx, .pdf, .txt, rtf, jpeg, .jpg, .png, .gif, .bmp, svg.

Są one wyświetlane w widoku **klasyfikatorów klasyfikujących** **portal zgodności Microsoft Purview** >  **Data** >  ze stanem `Ready to use`.

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Należy pamiętać, że wbudowane klasyfikatory trenowalne i globalne nie zawierają wyczerpującej ani pełnej listy terminów ani języków w tych obszarach. Ponadto standardy językowe i kulturowe stale się zmieniają, a w świetle tych realiów firma Microsoft zastrzega sobie prawo do aktualizowania tych klasyfikatorów według własnego uznania. Klasyfikatory mogą pomóc twojej organizacji w wykrywaniu tych obszarów, ale klasyfikatory nie są przeznaczone do zapewniania organizacji jedynego sposobu wykrywania lub rozwiązywania problemów z używaniem takiego języka. Twoja organizacja, a nie firma Microsoft ani jej podmioty zależne, pozostaje odpowiedzialna za wszystkie decyzje związane z monitorowaniem, skanowaniem, blokowaniem, usuwaniem i przechowywaniem dowolnej zawartości zidentyfikowanej przez wstępnie wytrenowanego klasyfikatora, w tym zgodności z lokalną prywatnością i innymi obowiązującymi przepisami. Firma Microsoft zachęca do konsultacji z radcą prawnym przed wdrożeniem i użyciem.

Nasze klasyfikatory zagrożeń, wulgaryzmów, molestowania i dyskryminacji mogą skanować zawartość w następujących językach:

- Arabski
- Chiński (uproszczony)
- Chiński (tradycyjny)
- Dutch
- English
- French
- German
- Italian
- Korean
- Japanese
- Portugalski
- Spanish

Wszystkie inne są angielski tylko w tej chwili.

### <a name="custom-classifiers"></a>Klasyfikatory niestandardowe

Gdy wstępnie wytrenowane klasyfikatory nie spełniają Twoich potrzeb, możesz utworzyć i wytrenować własne klasyfikatory. Tworzenie własnych aplikacji wymaga większej ilości pracy, ale będą one znacznie lepiej dostosowane do potrzeb organizacji.

Możesz rozpocząć tworzenie niestandardowego klasyfikatora trenowalnego, podając przykłady, które zdecydowanie należą do tej kategorii. Po przetłuczeniu tych przykładów można przetestować je, nadając mu kombinację zarówno zgodnych, jak i niezgodnych przykładów. Klasyfikator następnie prognozuje, czy dany element należy do kategorii, którą tworzysz. Następnie potwierdzasz jego wyniki, sortując wartości prawdziwie dodatnie, prawdziwie ujemne, fałszywie dodatnie i fałszywie ujemne, aby zwiększyć dokładność przewidywań. 

Po opublikowaniu klasyfikatora sortuje on elementy w lokalizacjach takich jak SharePoint Online, Exchange i OneDrive oraz klasyfikuje zawartość. Po opublikowaniu klasyfikatora możesz kontynuować trenowanie go przy użyciu procesu opinii, który jest podobny do początkowego procesu trenowania.

Można na przykład utworzyć klasyfikatory z możliwością trenowania dla następujących elementów:

- Dokumenty prawne — takie jak uprawnienie klienta adwokata, zestawy zamykające, instrukcja pracy
- Strategiczne dokumenty biznesowe — takie jak informacje prasowe, fuzja i nabycie, transakcje, plany biznesowe lub marketingowe, własność intelektualna, patenty, dokumenty projektowe
- Informacje o cenach — na przykład faktury, oferty cenowe, zamówienia pracy, dokumenty dotyczące ustalania stawek
- Informacje finansowe — takie jak inwestycje organizacyjne, wyniki kwartalne lub roczne

#### <a name="process-flow-for-creating-custom-classifiers"></a>Przepływ procesu tworzenia niestandardowych klasyfikatorów

Tworzenie i publikowanie klasyfikatora do użycia w rozwiązaniach zgodności, takich jak zasady przechowywania i nadzór komunikacyjny, jest zgodne z tym przepływem. Aby uzyskać więcej szczegółów na temat tworzenia niestandardowego klasyfikatora trenowalnego, zobacz [Tworzenie klasyfikatora niestandardowego](classifier-get-started-with.md).

![klasyfikator niestandardowy przepływu procesów.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Ponowne trenowanie klasyfikatorów

Możesz pomóc zwiększyć dokładność wszystkich niestandardowych klasyfikatorów trenowalnych i przekazując im opinię na temat dokładności klasyfikacji, którą wykonują. Jest to nazywane ponownym trenowaniem i jest zgodne z tym przepływem pracy.

> [!NOTE]
> Wstępnie wytrenowanych klasyfikatorów nie można ponownie wytrenować.

![przepływ pracy ponownego trenowania klasyfikatora.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Zobacz też

- [Etykiety przechowywania](retention.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Drukowanie palcem dokumentu](document-fingerprinting.md)
- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
