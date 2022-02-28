---
title: Scenariusze i przypadki użycia dla usługi Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
description: Znajdź scenariusze dotyczące używania SharePoint Syntex twojej organizacji.
ms.openlocfilehash: 16688f08183e55c8e2f52cdbcd50919dff680c1b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984962"
---
# <a name="scenarios-and-use-cases-for-microsoft-sharepoint-syntex"></a>Scenariusze i przypadki użycia dla usługi Microsoft SharePoint Syntex

W poniższych przykładowych scenariuszach możesz wyświetlać pomysły dotyczące sposobu używania SharePoint Syntex organizacji.

- [Scenariusz: Śledzenie danych z faktur przy użyciu przetwarzania formularza](adoption-scenarios.md#scenario-track-data-from-invoices-with-form-processing)
- [Scenariusz: śledzenie informacji z umów przy użyciu zrozumienia dokumentu](adoption-scenarios.md#scenario-track-information-from-contracts-with-document-understanding)
- [Scenariusz: Unikaj ryzyka związanego z zarządzaniem rekordami, procesami zarządzania dokumentami i zgodnością opartymi na SharePoint Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex)
- [Scenariusz: przechwytywanie informacji z dokumentów, które wcześniej były niedostępne](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Scenariusz: Ulepszanie przetwarzania danych w celu zapewnienia szczegółowych informacji i analizy](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Scenariusz: Automatyzowanie przetwarzania zamówienia](adoption-scenarios.md#scenario-automate-order-processing)
- [Scenariusz: uprość proces odnawiania wiz](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-data-from-invoices-with-form-processing"></a>Scenariusz: Śledzenie danych z faktur przy użyciu przetwarzania formularza

Na przykład możesz skonfigurować proces za pomocą funkcji SharePoint Syntex i Power Automate do śledzenia i monitorowania faktur.

1. Skonfiguruj bibliotekę do przechowywania dokumentów z fakturami.
1. Szkolenie modelu w zakresie rozpoznawania pól w dokumentach.
1. Wyodrębnianie pól, które mają być śledzone, do listy.
1. Skonfiguruj przepływ w celu powiadamiania Cię o określonych zdarzeniach, takich jak:
    - Zostanie dodana nowa faktura.
    - Faktura miej już termin płatności.
    - Faktura jest wyższa niż wartość zatwierdzeń automatycznych.

![Monitoruj faktury za pomocą SharePoint Syntex i Power Automate.](../media/content-understanding/process-invoices-flow.png)

Automatyzowanie tego scenariusza umożliwia:

- Oszczędzaj czas i pieniądze, automatycznie wyodrębniając dane z faktur zamiast robić to ręcznie.
- Ogranicz potencjalne błędy i zapewnij lepszą zgodność za pomocą przepływów pracy, aby sprawdzać faktury i powiadamiać Cię o wszelkich problemach.

## <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Scenariusz: śledzenie informacji z umów przy użyciu zrozumienia dokumentu

Możesz też skonfigurować proces identyfikowania umów z innymi firmami lub osobami, które Twoja firma ma z sobą. Skonfiguruj model wyodrębniania kluczowych informacji z tych umów, takich jak nazwa klienta, opłaty, daty lub inne ważne informacje, a następnie dodaj te informacje do biblioteki jako pola, które możesz szybko wyświetlić. Zastosuj etykietę przechowywania w bibliotece dokumentów, aby upewnić się, że nie będzie można usunąć umów przed określonym czasem w celu zapewnienia zgodności z przepisami biznesowymi.

1. Zacznij od centrum zawartości i utwórz nowy model rozumienia dokumentów dla umów.
1. Upload przykładowe dokumenty na przykłady dodatnie i ujemne, a następnie uruchom szkolenie w celu identyfikowania dokumentów kontraktowych i przeglądania wyników.
1. Przeszkoli wyodrębniacz w identyfikowaniu pól w umowach, takich jak nazwa klienta, opłata i data, a następnie przetestuj wyodrębniacz.
1. Po zakończeniu modelu zastosuj go do biblioteki, w której możesz przekazywać umowy.
1. Zastosuj etykietę przechowywania do pola daty, aby umowy zostały zachowane w bibliotece przez wymagany czas.

![Śledzenie i monitorowanie umów za pomocą SharePoint Syntex etykiet przechowywania.](../media/content-understanding/process-contracts-flow.png)

Automatyzowanie tego scenariusza umożliwia:

- Oszczędzaj czas i pieniądze, automatycznie wyodrębniając dane z umów, zamiast robić to ręcznie.
- Zapewnij lepszą zgodność, stosując etykiety przechowywania, aby zapewnić odpowiednie zachowanie umów.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex"></a>Scenariusz: Unikaj ryzyka związanego z zarządzaniem rekordami, procesami zarządzania dokumentami i zgodnością opartymi na SharePoint Syntex

Zmniejszenie ryzyka jest częstym celem dla większości firm. Mogą być potrzebne:

- Lepszy sposób na zapewnianie/wymuszanie zarządzania informacjami w całej dzierżawie.
- Aby ulepszyć system klasyfikacji dokumentów, wiadomości e-mail i innych form komunikacji uznawanych za "rekordy" w projektach.
- Aby sprawdzić pokwitowania, umowy i tak dalej, w celu zapewnienia zgodności z zasadami firmy.
- Aby zapewnić, że projekty będą zawierały całą dokumentację wymaganą do zachowania zgodności z przepisami.

Skonfiguruj pewne procesy zachowania zgodności z przepisami SharePoint Syntex w celu przechwytywania i odpowiedniego klasyfikowania, inspekcji oraz oflagowania dokumentów i formularzy, które wymagają lepszego zarządzania. Możesz polegać na SharePoint Syntex klasyfikowania zawartości, zamiast polegać na tagach ręcznie przez użytkowników końcowych lub na zespole zgodności na potrzeby ręcznego stosowania reguł zarządzania i archiwizacji. Możesz również włączyć uproszczone wyszukiwanie, zarządzać woluminami danych, stosować zasady zarządzania rekordami i przechowywania, zapewnić zgodność z przepisami i najlepsze rozwiązania w zakresie archiwizacji i przeczyszczania.

Automatyzowanie tego scenariusza pozwala zapewnić bezpieczeństwo:

- Zgodność jest zwiększana, a ryzyko jest zmniejszone.
- Taksonomia i zarządzanie rekordami są stale i dokładnie stosowane.
- Głośność zawartości jest kontrolowana.
- Pracownicy mogą łatwo odnajdować odpowiednie informacje w odpowiednim kontekście.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scenariusz: przechwytywanie informacji z dokumentów, które wcześniej były niedostępne

Większość organizacji ma duże repozytoria dokumentów prawnych, zasad, umów, dokumentów hr i wytycznych dotyczących zarządzania. Moje te magazyny danych są dostępne w celu wyodrębnienia cennych informacji, takich jak projekty, szybki, motywy, osoby, obszary geograficzne itp.

Na przykład dyrektor kadr musi szybko uzyskać dostęp do wszystkich dokumentów HR , w tym życiorysów, zasad kadrowych i innych formularzy. Chcą także szybko identyfikować niezbędne informacje z życiorysów i innych dokumentów związanych z kadrami bez konieczności ręcznego przeszukiania tych dokumentów. Poszukują rozwiązania, które pozwoli im szybko znaleźć potrzebne informacje bez konieczności ręcznego szukania tysięcy życiorysów, zasad dotyczących kadr i innej dokumentacji, które mogą być rozsiane po wielu witrynach.

Automatyzowanie tego scenariusza umożliwia:

- Odblokowywanie wiedzy z zawartości cyfrowej.
- Klasyfikowanie zasad kadrowych, życiorysów, dokumentów sprzedaży, planów technicznych, planów kont i wyodrębnianie informacji.
- Szybko znajdź właściwe informacje lub dokument, którego szukasz.
- Uzyskaj błyskawiczny dostęp do najnowszych informacji.
- Skracanie czasu wyszukiwania.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Scenariusz: Ulepszanie przetwarzania danych w celu zapewnienia szczegółowych informacji i analizy

Na przykład firma farmaceutyczne może użyć funkcji SharePoint Syntex informacji z dokumentów FDA w celu odpowiedzenia na pytania, które mają jej liderzy. Ułatwienia dostępu do odpowiedzi mogą skrócić czas potrzebny na tworzenie tych odpowiedzi i zwiększyć dostępność danych w celu wygenerowania bardziej precyzyjnych odpowiedzi na pytania kierownictwa.

Menedżer projektu musi na przykład szybko udzielić odpowiedzi na pytania dotyczące produktu od kierownictwa. Muszą one znaleźć informacje i metryki związane z zapytaniami na jednym skonsolidowanym pulpicie nawigacyjnym. Szuka rozwiązania wyodrębnianego z etykiet produktów, etykiet produktów i innych materiałów, a także generuje skonsolidowany raport, którego mogą użyć podczas raportowania do zespołu kierownictwa.

Automatyzowanie tego scenariusza umożliwia:

- Skracanie czasu w celu uzyskania odpowiedzi.
- Zwiększanie dostępności danych.
- Udzielaj bardziej precyzyjnych odpowiedzi.

## <a name="scenario-automate-order-processing"></a>Scenariusz: Automatyzowanie przetwarzania zamówienia

Dzięki SharePoint Syntex możesz skrócić czas ręcznego przetwarzania zamówień klientów. Możesz na przykład przekazać zamówienia z faksu, wiadomości e-mail lub papieru do usługi SharePoint przy użyciu przetwarzania OCR, a następnie wyodrębnić metadane z tych zamówień, aby zrealizować je przy użyciu zautomatyzowanych procesów.

Na przykład menedżer łańcucha dostaw chce ograniczyć liczbę błędów spowodowanych ręcznym wprowadzaniem danych. Chcą uniknąć ręcznego przeglądania i wprowadzania danych przychodzących zamówień klientów (papierowych, faksów lub poczty e-mail), aby ograniczyć liczbę błędów przychodzących do ich systemów biznesowych. Chcą uzyskać rozwiązanie, które stosuje technologie AI i uczenia maszynowego do sprawdzania poprawności informacji o przychodzących zamówieniach, wyodrębniania podstawowych danych i automatycznego wypychania ich do systemu ERP w celu realizacji zamówienia i uzgadniania.

Automatyzując ten scenariusz, możesz upewnić się, że:

- Zwiększa się dokładność zamówień i wysyłki.
- Zmniejszyć opłaty lub opłaty związane z błędami związanym z zamówieniem lub wysyłką.
- Zmniejsza się opóźnienia w fakturowaniu lub płatnościach.
- Koszty personelu są zmniejszane.

## <a name="scenario-simplify-visa-renewal-process"></a>Scenariusz: uprość proces odnawiania wiz

SharePoint Syntex może ułatwić automatyzowanie przypomnień i odnawiania kluczowych informacji o umowie. Na przykład dyrektor kadr musi zadbać o to, aby wiza pracowników było aktualne i/lub odnowiona na czas. Chcą zapewnić im prosty i intuicyjny proces aktualizacji usługi Visas. Potrzebne jest rozwiązanie, które wyodrębnia daty odnowienia z umów i automatycznie wysyła pracownikom przypomnienia, gdy zbliża się data odnowienia.

Automatyzując ten scenariusz, możesz upewnić się, że:

- Poziomy braku zgodności są ograniczane.
- Liczba przypomnień ręcznych zostanie zmniejszona.
- Liczba stawek za niezgodność z przepisami jest ograniczona.

## <a name="see-also"></a>Zobacz też

[Wdrożenie usługi Microsoft SharePoint Syntex: wprowadzenie](adoption-getstarted.md)