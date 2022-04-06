---
title: Rozwiązywanie problemów ze złośliwymi wiadomościami e-mail dostarczonymi w Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Działania naprawcze w przypadku zagrożeń
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 49cd5f532f41fd05090592136e28ca2462a9efd6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681177"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Remediate malicious email delivered in Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

Działania naprawcze oznaczają podejmowanie określonych działań w celu ochrony przed zagrożeniami. Złośliwe wiadomości e-mail wysyłane do organizacji mogą być czyszczone przez system, przez automatyczne przeczyszczenie bezgodzinne (ZAP) lub przez zespoły zabezpieczeń w ramach działań naprawczych, takich jak przenoszenie do skrzynki odbiorczej *, przechodzenie* do wiadomości-śmieci *, przechodzenie* do elementów usuniętych *,* niechciane usunięcie lub usuwanie *twarde.* Usługa Microsoft Defender dla Office 365 Plan 2/E5 umożliwia zespołom zabezpieczeń korygowanie zagrożeń w wiadomościach e-mail i funkcjach współpracy za pośrednictwem ręcznego i automatycznego badania.

> [!NOTE]
> Aby zaradić w złośliwych wiadomościach  e-mail, zespoły zabezpieczeń muszą mieć przypisaną rolę wyszukiwania i przeczyszczania. Przypisywanie ról odbywa się [za pośrednictwem uprawnień w portalu Microsoft 365 Defender zadań](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem

Administratorzy mogą podjąć wymagane działania w związku z wiadomościami e-mail, ale aby te działania zostały  zatwierdzone, muszą mieć przypisaną do nich rolę Wyszukiwania i  przeczyszczania w uprawnieniach współpracy poczty e-mail & w portalu Microsoft 365 Defender. Bez *dodania roli Wyszukaj i* przeczyszczania jej do jednej z grup ról nie będą oni mogli wykonać akcji.

## <a name="manual-and-automated-remediation"></a>Ręczne i automatyczne rozwiązywanie problemów

*Ręczne szukanie* odbywa się, gdy zespoły zabezpieczeń ręcznie identyfikują zagrożenia za pomocą funkcji wyszukiwania i filtrowania w Eksploratorze. Ręczne rozwiązywanie problemów z pocztą e-mail może zostać wyzwolone za pośrednictwem dowolnego widoku poczty e-mail *(Złośliwe* *oprogramowanie,* Wyłudzy lub Wszystkie wiadomości e-mail *) po* zidentyfikowaniu zestawu wiadomości e-mail, które wymagają rozwiązania.

> [!div class="mx-imgBorder"]
> [![Ręczne wyszukiwania w Office 365 w Eksploratorze zagrożeń według daty.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Za pomocą Eksploratora zespoły ds. zabezpieczeń mogą wybierać wiadomości e-mail na kilka sposobów:

- Ręczne wybieranie wiadomości e-mail: Korzystanie z filtrów w różnych widokach. Zaznacz maksymalnie 100 wiadomości e-mail, które chcesz rozwiązać.

- Zaznaczenie zapytania: umożliwia zaznaczenie całego zapytania za pomocą przycisku **zaznacz wszystko** u góry. To samo zapytanie jest również wyświetlane w szczegółach przesyłania poczty w Centrum akcji.

- Wybór zapytania z wyłączeniem: Czasami zespoły ds. operacji zabezpieczeń mogą chcieć rozwiązać ten proces, zaznaczając całe zapytanie i wykluczając określone wiadomości e-mail z zapytania ręcznie. W tym celu administrator może użyć pola wyboru Zaznacz  wszystko i przewinąć w dół, aby ręcznie wykluczyć wiadomości e-mail. Kwerenda może zawierać maksymalnie 1000 wiadomości e-mail. Maksymalna liczba wykluczeń to 100.

Po wybraniu wiadomości e-mail za pomocą Eksploratora możesz rozpocząć działania naprawcze, podejmowanie bezpośrednich działań lub kolejkowanie wiadomości e-mail dla akcji:

- Bezpośrednie zatwierdzanie: Gdy akcje, takie jak przechodzenie do skrzynki odbiorczej *, przechodzenie* do wiadomości-śmieci *,* przechodzenie do elementów usuniętych *,* niechyłne usunięcie lub usuwanie bezpośrednie, są wybierane przez pracowników zabezpieczeń, którzy mają odpowiednie uprawnienia, a następnie są wykonywane następne kroki rozwiązywania problemów, a następnie rozpoczyna się proces rozwiązywania problemów w celu wykonania wybranej akcji. Tymczasowe wysuwanie pokazuje działania naprawcze w toku.

- Zatwierdzanie dwuetapowe: Administratorzy, którzy nie mają odpowiednich uprawnień lub muszą zaczekać na wykonanie akcji, mogą wykonać akcję "Dodaj do działań naprawczych". W takim przypadku kierowane wiadomości e-mail są dodawane do kontenera rozwiązywania problemów. Zatwierdzenie jest wymagane przed wykonaniem działań naprawczych.

**Automatyczne akcje do badania i odpowiedzi** są wyzwalane przez alerty lub zespoły operacji zabezpieczeń z Eksploratora. Mogą to być zalecane działania naprawcze, które muszą zostać zatwierdzone przez zespół operacyjny ds. zabezpieczeń. Te akcje są uwzględniane na karcie **Akcja** w automatycznym śledztwie.

> [!div class="mx-imgBorder"]
> [![Poczta z złośliwym oprogramowaniem na stronie "Zamapowana" przedstawiająca czas wykonywania za pomocą zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

W Centrum akcji są wyświetlane wszystkie działania naprawcze (bezpośrednie lub dwuetapowe), które utworzono w Eksploratorze, oraz zatwierdzone działania pochodzące z automatycznego badania. Dostęp do nich można uzyskać za pośrednictwem lewego panelu **nawigacyjnego w centrum** \> **akcji Recenzja**.

> [!div class="mx-imgBorder"]
> [![Centrum akcji z listą zagrożeń według dat i ważności.](../../media/tp-RemediationArticle4.png)](../../media/tp-RemediationArticle4.png#lightbox)

Centrum akcji zawiera wszystkie działania naprawcze z ostatnich 30 dni. Akcje wykonane za pomocą Eksploratora są wyświetlane według nazwy udostępnianej przez zespół operacji zabezpieczeń podczas tworzenia środków zaradczych. Akcje wykonane w ramach zautomatyzowanych badań mają tytuły, które zaczynają się od powiązanego alertu, który wyzwolił badanie, na przykład "Zap klaster poczty e-mail... ".

Otwórz dowolny element rozwiązywania problemów, aby wyświetlić dotyczące go szczegóły, w tym jego nazwę, datę utworzenia, opis, zagrożenia i stan. Pokazano też dwie poniższe karty.

- **Karta Przesyłanie** poczty: Wyświetla liczbę wiadomości e-mail przesłanych za pomocą Eksploratora zagrożeń lub zautomatyzowanych badań, które mają zostać rozwiązane. Takie wiadomości e-mail mogą mieć możliwość akcji lub nie.

  > [!div class="mx-imgBorder"]
  > [![Centrum akcji z zagrożeniami, które nie mogą być akcjami ani działaniem.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

  - **Z akcją**: Wiadomości e-mail w następujących lokalizacjach skrzynek pocztowych w chmurze można przenosić i używać do tego celu:
    - Skrzynka odbiorcza
    - Wiadomości-śmieci
    - Usunięto folder
    - Folder "miękkiego usunięcia"

      > [!NOTE]
      > Obecnie tylko użytkownik z dostępem do skrzynki pocztowej może odzyskać elementy z folderu "miękkiego usunięcia".

  - **Brak akcji: W działaniach** naprawczych nie można przenosić ani używać wiadomości e-mail w następujących lokalizacjach:
    - Kwarantanna
    - Trudno usunąć folder
    - Lokalnie/zewnętrznie
    - Niepowodzenie/upuszczenie

  Podejrzane wiadomości można kategoryzować jako nieusuwalne lub nienadzysalne. W większości przypadków wiadomości, których nie można naprawić, łączą w sobie całkowitą liczbę przesłanych wiadomości. Jednak w rzadkich przypadkach może się to nie pookazać prawdziwe. Może się tak zdarzyć z powodu opóźnień systemu, limitów czasu lub wiadomości wygasłych. Wiadomości wygasają w zależności od okresu przechowywania Eksploratora dla organizacji.

  Jeśli po upływie okresu przechowywania w Eksploratorze organizacji nie są naprawiane stare wiadomości, zaleca się ponawianie prób usuwania elementów, jeśli zobaczysz niespójności liczb. W przypadku opóźnień systemu aktualizacje środków zaradczych są zwykle odświeżane w ciągu kilku godzin.

  Jeśli okres przechowywania poczty e-mail organizacji w Eksploratorze wynosi 30 dni i działania naprawcze będą obejmować wiadomości e-mail, które będą się powtarzać 29–30 dni, ich liczba nie zawsze się dodaje. Być może wiadomości e-mail przesuną się już poza okres przechowywania.

  Jeśli działania naprawcze zatrzymają się na jakiś czas w stanie "W toku", prawdopodobnie jest to spowodowane opóźnieniami systemu. Rozwiązywanie problemów może potrwać nawet kilka godzin. Mogą być liczone odmiany przesyłania poczty, ponieważ niektóre wiadomości e-mail mogły nie zostać uwzględnione w zapytaniu na początku rozwiązywania problemów z powodu opóźnień systemu. Warto ponowić próbę działania naprawczego w takich przypadkach.

  > [!NOTE]
  > Aby uzyskać najlepsze wyniki, działania naprawcze należy stosować w partiach nie więcej niż 50 000.

  W trakcie rozwiązywania problemów są naprawiane tylko wiadomości e-mail, które można naprawić. Nie można rozwiązać problemów z wiadomościami e-mail przez system poczty e-mail usługi Office 365 e-mail, ponieważ nie są one przechowywane w skrzynkach pocztowych w chmurze.

  W razie potrzeby administratorzy mogą podjąć działania na wiadomościach e-mail w kwarantannie, ale w razie potrzeby wygasną one poza kwarantanną, jeśli nie zostaną ręcznie wyczyszone. Domyślnie wiadomości e-mail poddane kwarantannie z powodu złośliwej zawartości nie są dostępne dla użytkowników, więc personel zabezpieczeń nie musi nic zrobić, aby usunąć zagrożenia w kwarantannie. Jeśli wiadomości e-mail są lokalne lub zewnętrzne, można skontaktować się z użytkownikiem w celu ich rozwiązania. Administratorzy mogą też usuwać wiadomości przy użyciu osobnych narzędzi serwera/zabezpieczeń poczty e-mail. Te wiadomości *e-mail* można zidentyfikować, stosując w Eksploratorze lokalizację dostarczania = filtr zewnętrzny. W przypadku nieudanych lub upuszczanych wiadomości e-mail lub wiadomości e-mail niedostępnych dla użytkowników nie będzie żadnych wiadomości e-mail, których nie będzie można zmniejszyć, ponieważ te wiadomości e-mail nie trafią do skrzynki pocztowej.

  Na poniższej ilustracji przedstawiono wygląd przesyłania w Centrum akcji. Działania naprawcze mogą zawierać wiele elementów przesyłania. Jeśli wiele akcji zostanie zatwierdzonych w ramach jednego zautomatyzowanego badania, każda akcja grupowania poczty e-mail lub poczty e-mail jest wyświetlana w ramach tych samych działań naprawczych, co inne przesyłanie.

  > [!div class="mx-imgBorder"]
  > [![Zap email cluster flyout panel.](../../media/tp-RemediationArticle6.png)](../../media/tp-RemediationArticle6.png#lightbox)

  Wybierz element przesyłania poczty, aby wyświetlić szczegóły dotyczące tych działań naprawczych, takie jak zapytanie (gdy działania naprawcze są wyzwolone przez zautomatyzowane badania lub eksploratora przez wybranie zapytania) oraz czas rozpoczęcia i zakończenia działań naprawczych. Jest w nim również wyświetlana lista komunikatów, które zostały przesłane w celu rozwiązania problemów. Gdy wiadomości wychodzą poza okres przechowywania w Eksploratorze, wiadomości znikają z tej listy. Na liście są również wyświetlane poszczególne wiadomości, których rozwiązywanie można rozwiązać.

- **Dzienniki akcji**: Na tej karcie są wyświetlane wiadomości, których działania zostały rozwiązane, w tym zatwierdzone daty, administrator, który zatwierdził akcję, działanie, stan i liczby.

  Stan może być:

  - **Uruchomione**: Zostanie wyzwolona remediacja.
    - **W kolejce**: Działania naprawcze są w kolejce w celu złagodzenia wpływu wiadomości e-mail.
    - **W toku**: Ograniczanie jest w toku.
    - **Ukończone**: Ograniczanie wpływu na wszystkie wiadomości e-mail, które można naprawić, zostały ukończone pomyślnie lub niektóre błędy.
    - **Niepowodzenie**: Żadne działania naprawcze nie zakończyły się pomyślnie.

  Ponieważ można działać tylko w przypadku wiadomości e-mail, które można naprawić, oczyszczanie każdej wiadomości e-mail zakończyło się powodzeniem lub nie powiodło się. Na temat łącznej liczby wiadomości e-mail, które można naprawić, raportowane są skuteczne i nieudane środki zaradcze.

  - **Sukces**: udało się wykonać odpowiednie działanie w przypadku wiadomości e-mail, które można naprawić. Na przykład: Administrator chce usunąć wiadomości e-mail ze skrzynek pocztowych, więc administrator podejmuje akcję "miękkiego usunięcia" wiadomości e-mail. Jeśli po zakończeniu akcji w oryginalnym folderze nie zostanie odnaleziona wiadomość e-mail, która można rozwiązać, będzie ona pokazywana jako pomyślna.

  - **Niepowodzenie**: Żądane działanie dotyczące wiadomości e-mail, które można naprawić, nie powiodło się. Na przykład: Administrator chce usunąć wiadomości e-mail ze skrzynek pocztowych, więc administrator podejmuje akcję "miękkiego usunięcia" wiadomości e-mail. Jeśli po zakończeniu akcji w skrzynce pocztowej nadal znajdziesz adres e-mail, który można naprawić, stan będzie pokazywany jako nieudany.
  
  - **Już w miejscu docelowym**: Żądane działanie zostało już wykonane na wiadomości e-mail LUB w lokalizacji docelowej już istniała wiadomość e-mail. Przykład: Wiadomość e-mail została niechbędnie usunięta przez administratora za pośrednictwem Eksploratora w pierwszym dniu. Następnie podobne wiadomości e-mail są wyświetlane w dniu 2, który znowu jest niechcący usunięty przez administratora. Podczas zaznaczania tych wiadomości e-mail administrator odbiera od dnia odebranie niektórych wiadomości e-mail, które zostały już "miękkie". Teraz te wiadomości e-mail nie będą już podejmowane w związku z tym, będą wyświetlane jako "już w miejscu docelowym", ponieważ nie zostały w związku z nimi wykonane żadne działania, ponieważ istniały w lokalizacji docelowej.

  - **Nowy**: Kolumna *docelowa Już istnieje* w dzienniku akcji została dodana. Ta funkcja korzysta z najnowszej lokalizacji dostarczania w Eksploratorze zagrożeń do zasygnalizować, jeśli poczta została już rozwiązana. *Już w miejscu docelowym* pomoże zespołom zabezpieczeń zrozumieć łączną liczbę wiadomości, które nadal muszą zostać rozwiązane.

Akcje mogą być podejmowane tylko w przypadku wiadomości w folderach Skrzynka odbiorcza, Wiadomości-śmieci, Usunięte i Niechciane usunięte w Eksploratorze zagrożeń. Oto przykład działania nowej kolumny. W *przypadku wiadomości obecnych* w Skrzynce odbiorczej następuje niechybne usunięcie, a następnie wiadomość zostanie obsłużona zgodnie z zasadami. Przy następnym wykonaniu "miękkiego usunięcia", ten komunikat zostanie wyświetlony pod kolumną "Już w miejscu docelowym" i zasygnalizuje, że nie trzeba ponownie się do niego zaadresować.

Wybierz dowolny element w dzienniku akcji, aby wyświetlić szczegóły dotyczące rozwiązywania problemów. Jeśli szczegóły mówią "pomyślnie" lub "nie znaleziono w skrzynce pocztowej", oznacza to, że ten element został już usunięty ze skrzynki pocztowej. Czasami podczas rozwiązywania problemów występuje błąd systemu. W takich przypadkach warto ponownie wykonać działania naprawcze.

W przypadku rozwiązywania problemów z dużymi partiami poczty e-mail wyeksportuj za pośrednictwem przesyłania poczty wiadomości wysłanych w celu ich rozwiązania oraz wiadomości, które zostały rozwiązane za pośrednictwem dzienników akcji. Limit eksportu został zwiększony do 100 000 rekordów.

Działania naprawcze w celu zmniejszenia zagrożeń, rozwiązania podejrzanych wiadomości e-mail i zapewnienia bezpieczeństwa organizacji.
