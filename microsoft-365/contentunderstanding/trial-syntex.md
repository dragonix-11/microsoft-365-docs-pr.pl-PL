---
title: Uruchom wersję próbną usługi Microsoft SharePoint Syntex
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
description: Dowiedz się, jak zaplanować i uruchomić próbny program pilotażowy dla SharePoint Syntex organizacji.
ms.openlocfilehash: 74b44c14140f26e0744aac73fd948e58d9d33e24
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983314"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Uruchom wersję próbną usługi Microsoft SharePoint Syntex

W tym artykule opisano, jak skonfigurować i uruchomić próbny program pilotażowy w celu SharePoint Syntex w organizacji. Zaleca również najlepsze rozwiązania dotyczące wersji próbnej.

## <a name="sign-up-for-a-trial"></a>Zarejestruj się w celu rejestracji w wersji próbnej

Wersja próbna SharePoint Syntex dostępu 300 użytkownikom przez 30 dni.

> [!NOTE]
> W wersji próbnej uwzględniono maksymalnie 300 użytkowników, aby zapewnić automatyczne dodawanie 1 miliona punktów aplikacji AI Builder. Aby uzyskać sukces wersji próbnej, nie trzeba uwzględniać 300 użytkowników.

Wersję próbną można pobrać z jednego z następujących źródeł:

- Strona [SharePoint Syntex produktu](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com)
    1. Zaloguj się do [Centrum administracyjnego usługi Microsoft 365](https://admin.microsoft.com).
    2. Przejdź do **usługi** <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**BillingPurchase**</a> >  Services.
    3. Przewiń w dół **do sekcji Dodatki** .
    4. Na kafelku SharePoint Syntex wybierz pozycję **Szczegóły**.
    5. Wybierz **pozycję Uzyskaj bezpłatną wersję próbną**.
    6. Aby potwierdzić wersję próbną, wykonaj pozostałe kroki kreatora.

Aby aktywować wersję próbną, Microsoft 365 administratorem globalnym lub administratorem rozliczeń.

### <a name="who-should-be-involved-in-a-trial"></a>KtoTo uczestniczyć w próbie

|Rola|Działanie|
|---|---|
|Microsoft 365 administrator globalny lub administrator rozliczeń|Aktywowanie wersji próbnej i przypisywanie licencji|
|Microsoft 365 administrator globalny lub SharePoint administrator|Konfigurowanie SharePoint Syntex i tworzenie centrów zawartości|
|Użytkownicy biznesowi|Model tworzenia i testowania|

### <a name="before-you-activate-a-trial"></a>Przed aktywowaniem wersji próbnej

Aby pomyślnie zaplanować SharePoint Syntex próbną, weź pod uwagę następujące czynniki:

- Najbardziej znaczące testy są ukończone w "świecie rzeczywistym" w scenariuszach i danych.
- Wersję próbną można aktywować tylko SharePoint Syntex dzierżawy.

Dzierżawy testowej lub demonstracyjnej można użyć jako "suchej wersji" do ominięcia kroków aktywacji i kontroli administracyjnej. Jednak prawdopodobnie najlepszym rozwiązaniem jest oszacowanie modelu na podstawie dzierżawy produkcyjnej.

Aby zmaksymalizować wartość wersji próbnej w dzierżawie produkcyjnej, niezbędne jest planowanie i angażowanie firmy. Należy zaangażuć co najmniej jeden obszar biznesowy w celu zidentyfikowania spraw użycia trzech do sześciu, które potencjalnie mogą zostać rozwiązane przez SharePoint Syntex. Te przypadki użycia powinny:

- Dołącz scenariusze, które mogą zostać rozwiązane przez model przetwarzania formularzy lub dokumentu opisowego.
- jednoznacznie zrozumieć przeznaczenie dowolnych wyodrębnianych metadanych; można na przykład wyświetlać formatowanie lub automatyzację za pomocą Power Automate. Chociaż SharePoint Syntex się na klasyfikowaniu dokumentów i wyodrębniania metadanych, wartość, jaką należy określić, to tym, co umożliwiają te metadane.
- Być oparte na zdefiniowanym zestawie danych; na przykład konkretne SharePoint lub bibliotek. Często myli się SharePoint Syntex jest to, że modele ogólnego przeznaczenia można stosować we wszystkich zawartość organizacji. Dokładniejszy widok to modele, które ułatwiają rozwiązywanie określonych problemów biznesowych w określonych lokalizacjach.

Wszystkie te przypadki mogą nie być odpowiednie dla SharePoint Syntex. Celem próby jakości nie jest udowodnienie, że SharePoint Syntex pasuje do wszystkich scenariuszy. Zamiast tego wersja próbna powinna lepiej zrozumieć wartość produktu.

W przypadku każdego z planowanych przypadków użycia określ użytkowników, którzy są ekspertami w poszczególnych sprawach związanych z powiązaną zawartością lub procesem. Tworzenie modeli SharePoint Syntex jest koncentrowały się na ekspertach w dziedzinie treści, a nie na informatykach i zasobach deweloperowych.

## <a name="activate-a-trial"></a>Aktywowanie wersji próbnej

Podczas inicjowania okresu próbnego należy:

- Przypisywanie licencji odpowiednim użytkownikom.
- Wykonaj [dodatkową konfigurację SharePoint Syntex](set-up-content-understanding.md).
  - Możesz utworzyć dodatkowe [centra zawartości](create-a-content-center.md).

Po aktywowaniu wersji próbnej możesz tworzyć modele i pliki procesów. Zobacz [wskazówki dotyczące tworzenia modelu](create-a-content-center.md).

## <a name="during-a-trial"></a>W trakcie okresu próbnego

Okresy próbne są ograniczone, dlatego na początku warto się skupić na tym, czy modele SharePoint Syntex klasyfikować dokumenty i wyodrębniać metadane dla określonych przypadków użycia. Po upływie okresu próbnego można oszacować, jak można wykorzystać metadane.

## <a name="after-a-trial"></a>Po upływie okresu próbnego

Na podstawie wyniku okresu próbnego możesz zdecydować, czy przystąpić do używania produkcyjnego SharePoint Syntex.

### <a name="proceed-to-production-use"></a>Kontynuowanie użytkowania produkcyjnego

Aby zapewnić ciągłość działania usługi, należy zakupić wymaganą liczbę licencji i przypisać je użytkownikom. Użytkownicy wersji próbnej, którzy nie mają pełnej licencji po zakończeniu okresu próbnego, nie będą mogli w pełni korzystać z SharePoint Syntex.

Może być konieczne oszacowanie przewidywanego użycia przetwarzania i planowania formularzy na oczekiwaną ilość środków na korzystanie z aplikacji Builder aplikacji AI. Aby uzyskać pomoc, [zobacz Szacowanie pojemności aplikacji AI Builder odpowiedniego dla Ciebie](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Nie kontynuuj używania produkcji

Jeśli nie zakupisz licencji po wersji próbnej:

- Nie będzie można tworzyć nowych modeli.
- Biblioteki, które były modelami, nie będą już automatycznie klasyfikować plików ani wyodrębniać modeli.
- Nie będzie to mieć wpływu na żadne wcześniej sklasyfikowane pliki ani wyodrębnione metadane.
- Centra zawartości i wszelkie modele opisowe dokumentów nie zostaną automatycznie usunięte. Pozostaną one dostępne do użytku, jeśli zdecydujesz się na zakup licencji w przyszłości.
- Modele przetwarzania formularzy będą przechowywane w wystąpieniu funkcji Dataverse (wcześniej o nazwie Common Data Service [CDS]) domyślnego środowiska platformy Power Platform. Mogą one być używane w przyszłości w celu licencjonowania oprogramowania SharePoint Syntex za pomocą funkcji AI Builder na platformie Power.

## <a name="see-also"></a>Zobacz też

[Wdrożenie usługi Microsoft SharePoint Syntex: wprowadzenie](adoption-getstarted.md)
