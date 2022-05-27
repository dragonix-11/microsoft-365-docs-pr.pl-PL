---
title: Uruchamianie wersji próbnej usługi Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- Adopt
- admindeeplinkMAC
search.appverid: ''
ms.localizationpriority: medium
description: Dowiedz się, jak planować, tworzyć i uruchamiać pilotażowy program próbny dla SharePoint Syntex w organizacji.
ms.openlocfilehash: ccbf1208d5c655171825b5a96f3a78b25ea3bbf2
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754449"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Uruchamianie wersji próbnej usługi Microsoft SharePoint Syntex

W tym artykule opisano sposób konfigurowania i uruchamiania próbnego programu pilotażowego w celu wdrożenia SharePoint Syntex w organizacji. Zaleca również najlepsze rozwiązania dotyczące wersji próbnej.

## <a name="sign-up-for-a-trial"></a>Tworzenie konta na potrzeby wersji próbnej

Wersja próbna SharePoint Syntex daje dostęp do 300 użytkowników przez 30 dni.

> [!NOTE]
> Do 300 użytkowników jest uwzględnionych w wersji próbnej w celu zapewnienia automatycznego dodania 1 miliona środków narzędzia AI Builder. Aby próba próbna zakończyła się pomyślnie, nie trzeba uwzględniać 300 użytkowników.

Wersję próbną można uzyskać z jednego z następujących źródeł:

- [Strona produktu SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com)
    1. Zaloguj się do [Centrum administracyjnego usługi Microsoft 365](https://admin.microsoft.com).
    2. Przejdź do **obszaru Usługi**<a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**zakupu rozliczeń**</a> > .
    3. Przewiń w dół do sekcji **Dodatki** .
    4. Na kafelku SharePoint Syntex wybierz pozycję **Szczegóły**.
    5. Wybierz pozycję **Rozpocznij bezpłatną wersję próbną**.
    6. Aby potwierdzić wersję próbną, wykonaj pozostałe kroki kreatora.

Aby aktywować wersję próbną, musisz być administratorem globalnym lub administratorem rozliczeń Microsoft 365.

### <a name="who-should-be-involved-in-a-trial"></a>KtoTo powinny być zaangażowane w proces

|Rola|Działanie|
|---|---|
|Microsoft 365 administrator globalny lub administrator rozliczeń|Aktywowanie wersji próbnej i przypisywanie licencji|
|Microsoft 365 administrator globalny lub administrator SharePoint|Konfigurowanie SharePoint Syntex i tworzenie centrów zawartości|
|Użytkownicy biznesowi|Tworzenie i testowanie modelu|

### <a name="before-you-activate-a-trial"></a>Przed aktywowaniem wersji próbnej

Aby pomyślnie zaplanować SharePoint Syntex wersji próbnej, należy wziąć pod uwagę następujące czynniki:

- Najbardziej znaczące testy są wykonywane w scenariuszach i danych w świecie rzeczywistym.
- Możesz aktywować SharePoint Syntex wersji próbnej tylko raz na dzierżawę.

Dzierżawa testowa lub demonstracyjna może służyć jako "suchy przebieg" do przechodzenia przez kroki aktywacji i kontrolki administracyjne. Ale prawdopodobnie najlepiej jest ocenić model oparty na dzierżawie produkcyjnej.

Aby zmaksymalizować wartość wersji próbnej dzierżawy produkcyjnej, planowanie i zaangażowanie biznesowe są niezbędne. Należy zaangażować co najmniej jeden obszar biznesowy, aby zidentyfikować od trzech do sześciu przypadków użycia, które mogą być potencjalnie rozwiązane przez SharePoint Syntex. Te przypadki użycia powinny:

- Uwzględnij scenariusze, które można rozwiązać za pomocą przetwarzania formularzy lub modelu interpretacji dokumentów.
- Mieć jasną wiedzę na temat celu wyodrębnionych metadanych; na przykład wyświetl formatowanie lub automatyzację przy użyciu Power Automate. Podczas gdy SharePoint Syntex koncentruje się na klasyfikowaniu dokumentów i wyodrębnianiu metadanych, wartość do oszacowania jest tym, co umożliwia to metadane.
- Być oparte na zdefiniowanym zestawie danych; na przykład określone witryny lub biblioteki SharePoint. Typowym błędem SharePoint Syntex jest to, że modele ogólnego przeznaczenia mogą być stosowane w całej zawartości organizacji. Dokładniejszym widokiem jest to, że modele są tworzone w celu ułatwienia rozwiązywania określonych problemów biznesowych w lokalizacjach docelowych.

Wszystkie te przypadki użycia mogą nie być dobrym rozwiązaniem dla SharePoint Syntex. Celem wysokiej jakości wersji próbnej nie jest udowodnienie, że SharePoint Syntex będzie pasować do wszystkich scenariuszy. Zamiast tego wersja próbna powinna pomóc lepiej zrozumieć wartość produktu.

W każdym z planowanych przypadków użycia zidentyfikuj użytkowników, którzy są ekspertami w zakresie powiązanej zawartości lub procesu. Tworzenie modeli SharePoint Syntex koncentruje się na ekspertach w dziedzinie zawartości, a nie na specjalistach IT lub zasobach deweloperskich.

## <a name="activate-a-trial"></a>Aktywowanie wersji próbnej

Podczas inicjowania wersji próbnej należy wykonać następujące czynności:

- Przypisz licencje odpowiednim użytkownikom.
- Wykonaj [dodatkową konfigurację SharePoint Syntex](set-up-content-understanding.md).
  - Możesz utworzyć [więcej centrów zawartości](create-a-content-center.md).

Po aktywowaniu wersji próbnej można tworzyć modele i przetwarzać pliki. Zobacz [wskazówki dotyczące tworzenia modelu](create-a-content-center.md).

## <a name="during-a-trial"></a>Podczas okresu próbnego

Okresy próbne są ograniczone, dlatego najlepiej skupić się początkowo na tym, czy modele SharePoint Syntex mogą klasyfikować dokumenty i wyodrębniać metadane dla zdefiniowanych przypadków użycia. Po zakończeniu okresu próbnego możesz ocenić, w jaki sposób można wykorzystać metadane.

## <a name="after-a-trial"></a>Po zakończeniu okresu próbnego

Na podstawie wyniku próby możesz zdecydować, czy kontynuować produkcyjne korzystanie z SharePoint Syntex.

### <a name="proceed-to-production-use"></a>Przejdź do użycia w środowisku produkcyjnym

Aby zapewnić ciągłość działania usługi, należy kupić wymaganą liczbę [licencji](syntex-licensing.md) i przypisać te licencje użytkownikom. Użytkownicy wersji próbnej, którzy nie mają pełnej licencji po zakończeniu okresu próbnego, nie będą mogli w pełni korzystać z SharePoint Syntex.

Może być konieczne oszacowanie przewidywanego użycia przetwarzania formularzy i zaplanowanie oczekiwanej liczby środków narzędzia AI Builder. Aby uzyskać pomoc, zobacz [Szacowanie pojemności narzędzia AI Builder, która jest odpowiednia dla Ciebie](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Nie kontynuuj używania w środowisku produkcyjnym

Jeśli licencje nie są kupowane po wersji próbnej:

- Nie będzie można tworzyć nowych modeli.
- Biblioteki, w których uruchomiono modele, nie będą już automatycznie klasyfikować plików ani wyodrębniać modeli.
- Nie będzie to miało wpływu na żadne wcześniej sklasyfikowane pliki ani wyodrębnione metadane.
- Centra zawartości i wszystkie modele interpretacji dokumentów nie zostaną automatycznie usunięte. Pozostaną one dostępne do użycia, jeśli zdecydujesz się na zakup licencji w przyszłości.
- Modele przetwarzania formularzy będą przechowywane w wystąpieniu usługi Dataverse (wcześniej o nazwie Common Data Service (CDS) domyślnego środowiska platformy Power Platform. Mogą one być używane w przypadku przyszłych licencji na SharePoint Syntex lub z możliwościami narzędzia AI Builder na platformie Power Platform.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie wdrażanie SharePoint Syntex](adoption-getstarted.md)
