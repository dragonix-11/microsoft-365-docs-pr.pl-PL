---
title: Wyszukiwanie zagrożeń w Eksploratorze zagrożeń dla Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Użyj Eksploratora zagrożeń lub wykrywania w czasie rzeczywistym w portalu Microsoft 365 Defender, aby efektywnie badać zagrożenia i reagować na nie.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bcbacc886c57257e5c4b067b278c7736ae403390
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945522"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Wyszukiwanie zagrożeń w Eksploratorze zagrożeń dla Ochrona usługi Office 365 w usłudze Microsoft Defender

W tym artykule:

- [Przewodnik po Eksploratorze zagrożeń](#threat-explorer-walk-through)
- [Badanie poczty e-mail](#email-investigation)
- [Korygowanie wiadomości e-mail](#email-remediation)
- [Ulepszenia środowiska wyszukiwania zagrożeń](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Jest to część **serii 3 artykułów** dotyczących **Eksploratora zagrożeń (Eksplorator),** **zabezpieczeń poczty e-mail** oraz **wykrywania Eksploratora i czasu rzeczywistego** (takich jak różnice między narzędziami i uprawnienia wymagane do ich obsługi). Pozostałe dwa artykuły z tej serii to [Zabezpieczenia poczty e-mail z Eksploratorem zagrożeń](email-security-in-microsoft-defender.md) i [Eksploratorem zagrożeń oraz wykrywanie w czasie rzeczywistym](real-time-detections.md).


**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli Twoja organizacja ma [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) i masz [uprawnienia](#required-licenses-and-permissions), możesz użyć **Eksploratora** lub **wykrywania w czasie rzeczywistym do wykrywania** i korygowania zagrożeń.

W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Poczta e-mail & współpracy**, a następnie wybierz pozycję **Eksplorator** lub **Wykrywanie w czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj polecenia <https://security.microsoft.com/threatexplorer> lub <https://security.microsoft.com/realtimereports>.

Za pomocą tych narzędzi możesz:

- Zobacz złośliwe oprogramowanie wykryte przez funkcje zabezpieczeń Microsoft 365
- Wyświetl adres URL wyłudzania informacji i kliknij dane werdyktu
- Uruchamianie zautomatyzowanego badania i procesu odpowiedzi z widoku w Eksploratorze
- Badanie złośliwych wiadomości e-mail i nie tylko

Aby uzyskać więcej informacji, zobacz [Zabezpieczenia poczty e-mail w Eksploratorze zagrożeń](email-security-in-microsoft-defender.md).

## <a name="threat-explorer-walk-through"></a>Przewodnik po Eksploratorze zagrożeń

W Ochrona usługi Office 365 w usłudze Microsoft Defender istnieją dwa plany subskrypcji — plan 1 i plan 2. Ręcznie obsługiwane narzędzia do wyszukiwania zagrożeń istnieją w obu planach, pod różnymi nazwami i z różnymi możliwościami.

Ochrona usługi Office 365 w usłudze Defender plan 1 używa *wykrywania w czasie rzeczywistym*, który jest podzbiorem narzędzia do wyszukiwania *zagrożeń* (nazywanego również *Eksploratorem*) w planie 2. W tej serii artykułów większość przykładów została utworzona przy użyciu pełnego Eksploratora zagrożeń. Administratorzy powinni przetestować wszelkie kroki wykrywania w czasie rzeczywistym, aby sprawdzić, gdzie mają zastosowanie.

Po przejściu do **Eksploratora** domyślnie pojawisz się na stronie **Złośliwe oprogramowanie** , ale użyjesz listy rozwijanej **Widok** , aby zapoznać się z opcjami. Jeśli polujesz na Phish lub zagłębiasz się w kampanię zagrożeń, wybierz te poglądy.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="Lista rozwijana Widok w Eksploratorze zagrożeń" lightbox="../../media/view-drop-down.png":::

Gdy osoba operacji zabezpieczeń (Sec Ops) wybierze dane, które chce zobaczyć, czy zakres jest wąski, taki jak **przesyłanie użytkowników**, czy szerszy widok, taki jak **Wszystkie wiadomości e-mail**, może użyć przycisku **Nadawca** do dalszego filtrowania. Pamiętaj, aby wybrać pozycję Odśwież, aby ukończyć akcje filtrowania.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="Przycisk Nadawca w Eksploratorze zagrożeń" lightbox="../../media/sender-drop-down.png":::


Uściślanie fokusu w Eksploratorze lub wykrywaniu w czasie rzeczywistym można traktować w warstwach. Pierwszy z nich to **Widok**. Drugi można traktować jako *przefiltrowany fokus*. Na przykład możesz odtworzyć kroki, które zostały opisane w znalezieniu zagrożenia, rejestrując swoje decyzje w następujący sposób: Aby znaleźć problem w Eksploratorze, **wybrałem widok złośliwego oprogramowania z fokusem filtru adresata**. Ułatwia to śledzenie kroków.

> [!TIP]
> Jeśli usługa Sec Ops używa **tagów** do oznaczania kont, które uważają za obiekty docelowe o wysokiej wartości, może dokonać wyborów, takich jak *Widok phish, z fokusem filtru Tagi (uwzględnij zakres dat, jeśli jest używany)*. Spowoduje to wyświetleniem wszelkich prób wyłudzania informacji skierowanych do celów użytkowników o wysokiej wartości w przedziale czasu (na przykład daty, w których niektóre ataki wyłudzania informacji mają wiele miejsca dla swojej branży).

Uściślenia można wprowadzić w zakresach dat przy użyciu kontrolek zakresu dat. Tutaj możesz zobaczyć Eksploratora w widoku **złośliwego oprogramowania** z fokusem filtru **technologii wykrywania** . Ale jest to przycisk **Filtr zaawansowany** , który pozwala zespołom Sec Ops kopać głęboko.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="Filtr Zaawansowane w Eksploratorze zagrożeń" lightbox="../../media/advanced-filter.png":::

Kliknięcie **filtru Zaawansowane** powoduje wyświetlenie panelu, który umożliwia łowcom usługi Sec Ops samodzielne tworzenie zapytań, umożliwiając im dołączanie lub wykluczanie informacji potrzebnych do wyświetlenia. Zarówno wykres, jak i tabela na stronie Eksploratora będą odzwierciedlać ich wyniki.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="Wyniki zapytania" lightbox="../../media/threat-explorer-chart-table.png":::

Użyj przycisku **Opcje kolumny** , aby uzyskać informacje na temat tabeli, które byłyby najbardziej przydatne:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="Wyróżniony przycisk Opcje kolumny" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="Dostępne opcje w kolumnach" lightbox="../../media/column-options.png":::

W tym samym pliku mien sprawdź opcje wyświetlania. Różni odbiorcy będą dobrze reagować na różne prezentacje tych samych danych. Dla niektórych osób przeglądających mapa **Źródła poczty e-mail** może pokazać, że zagrożenie jest powszechne lub dyskretniejsze szybciej niż opcja **wyświetlania kampanii** tuż obok niej. Operacje sec mogą korzystać z tych wyświetlaczy, aby jak najlepiej tworzyć punkty, które podkreślają potrzebę zabezpieczeń i ochrony, lub do późniejszego porównania, aby zademonstrować skuteczność swoich działań.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="Mapa Źródła wiadomości e-mail" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="Opcje wyświetlania kampanii" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>Badanie poczty e-mail

Gdy zobaczysz podejrzaną wiadomość e-mail, kliknij nazwę, aby rozwinąć wysuwany po prawej stronie. W tym miejscu baner, który umożliwia usłudze Sec Ops wyświetlanie [strony jednostki poczty e-mail](mdo-email-entity-page.md) , jest dostępny.

Strona jednostki poczty e-mail łączy zawartość, którą można znaleźć w obszarze **Szczegóły**, **Załączniki**, **Urządzenia**, ale zawiera bardziej zorganizowane dane. Obejmuje to takie elementy jak wyniki DMARC, wyświetlanie nagłówka wiadomości e-mail w postaci zwykłego tekstu z opcją kopiowania, informacje o werdyktach dotyczące załączników, które zostały bezpiecznie zdetonowane, oraz pliki, z których te detonacje zostały usunięte (mogą zawierać adresy IP, z których nawiązano kontakt, oraz zrzuty ekranu stron lub plików). Adresy URL i ich werdykty są również wymienione z podobnymi szczegółami.

Po osiągnięciu tego etapu strona jednostki poczty e-mail będzie krytyczna dla ostatniego kroku — *korygowania*.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="Strona jednostki poczty e-mail" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> Aby dowiedzieć się więcej o bogatej stronie jednostki poczty e-mail (widocznej poniżej na karcie **Analiza** ), w tym o wynikach detonowanych załączników, ustaleniach dotyczących uwzględnionych adresów URL i bezpiecznej wersji zapoznawczej poczty e-mail, kliknij [tutaj](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="Karta Analiza strony jednostki poczty e-mail" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>Korygowanie wiadomości e-mail

Gdy osoba Sec Ops określi, że wiadomość e-mail jest zagrożeniem, następnym krokiem wykrywania Eksploratora lub Wykrywanie w czasie rzeczywistym jest rozwiązanie problemu z zagrożeniem i jego korygowanie. Można to zrobić, wracając do Eksploratora zagrożeń, zaznaczając pole wyboru dla wiadomości e-mail problemu i używając przycisku **Akcje** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="Przycisk Akcje w Eksploratorze zagrożeń" lightbox="../../media/threat-explorer-email-actions-button.png":::

W tym miejscu analityk może podjąć działania, takie jak zgłaszanie wiadomości e-mail jako spamu, wyłudzania informacji lub złośliwego oprogramowania, kontaktowanie się z adresatami lub dalsze badania, które mogą obejmować wyzwalanie podręczników zautomatyzowanego badania i odpowiedzi (lub air) (jeśli masz plan 2). Możesz też zgłosić wiadomość e-mail jako czystą.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="Lista rozwijana Akcje" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>Ulepszenia środowiska wyszukiwania zagrożeń

### <a name="alert-id"></a>Identyfikator alertu

Podczas przechodzenia z alertu do Eksploratora zagrożeń **widok** będzie filtrowany według **identyfikatora alertu**. Dotyczy to również wykrywania w czasie rzeczywistym. Wyświetlane są komunikaty dotyczące określonego alertu i suma wiadomości e-mail (liczba). Będzie można sprawdzić, czy komunikat był częścią alertu, a także przejść od tej wiadomości do powiązanego alertu.

Na koniec identyfikator alertu jest uwzględniony w adresie URL, na przykład: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtr identyfikatora alertu" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Identyfikator alertu w wysuwnym elemencie szczegółów" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Rozszerzanie przechowywania danych Eksploratora (i wykrywania w czasie rzeczywistym) i limitu wyszukiwania dla dzierżaw wersji próbnej

W ramach tej zmiany analitycy będą mogli wyszukiwać i filtrować dane wiadomości e-mail w ciągu 30 dni (zwiększono z siedmiu dni) w Eksploratorze zagrożeń i wykrywaniu w czasie rzeczywistym Office dla dzierżaw usługi Defender dla dzierżaw wersji próbnej P1 i P2 w usłudze Defender. Nie ma to wpływu na dzierżawy produkcyjne zarówno dla klientów P1, jak i P2 E5, gdzie domyślne przechowywanie wynosi już 30 dni.

### <a name="updated-export-limit"></a>Zaktualizowany limit eksportu

Liczba rekordów wiadomości e-mail, które można wyeksportować z Eksploratora zagrożeń, wynosi teraz 200 000 (było to 9990). Zestaw kolumn, które można wyeksportować, nie ulega zmianie.

### <a name="tags-in-threat-explorer"></a>Tagi w Eksploratorze zagrożeń

> [!NOTE]
> Funkcja tagów użytkownika jest dostępna w wersji zapoznawczej i może nie być dostępna dla wszystkich użytkowników. Ponadto podglądy mogą ulec zmianie. Aby uzyskać informacje na temat harmonogramu wydania, zapoznaj się z planem Microsoft 365.

Tagi użytkowników identyfikują określone grupy użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby uzyskać więcej informacji na temat tagów, w tym licencjonowania i konfiguracji, zobacz [Tagi użytkowników](user-tags.md).

W Eksploratorze zagrożeń możesz zobaczyć informacje o tagach użytkowników w następujących środowiskach.

#### <a name="email-grid-view"></a>Widok siatki poczty e-mail

Gdy analitycy zobaczą kolumnę **Tagi** w siatce wiadomości e-mail, widzą wszystkie tagi, które zostały zastosowane do skrzynek pocztowych nadawcy lub adresata. Domyślnie tagi systemowe, takie jak *konta priorytetowe* , są wyświetlane jako pierwsze.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Filtruj tagi w widoku siatki poczty e-mail" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrowanie

Tagi mogą być używane jako filtry. Poluj tylko na konta priorytetowe lub w ten sposób używaj konkretnych scenariuszy tagów użytkowników. Można również wykluczyć wyniki, które mają określone tagi. Połącz tagi z innymi filtrami i zakresami dat, aby zawęzić zakres badania.

[![Filtruj tagi.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="Tagi, które nie zostały przefiltrowane" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>Wysuwany szczegół wiadomości e-mail

Aby wyświetlić pojedyncze tagi dla nadawcy i odbiorcy, wybierz wiadomość e-mail, aby otworzyć wysuwaną wiadomość. Na karcie Podsumowanie tagi **nadawcy** i adresata są wyświetlane oddzielnie. Informacje o poszczególnych tagach dla nadawcy i odbiorcy można wyeksportować jako dane CSV.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Tagi Szczegóły wiadomości e-mail" lightbox="../../media/tags-flyout.png":::

Informacje o tagach są również wyświetlane w wysuwanym kliknięciu adresu URL. Aby go wyświetlić, przejdź do widoku Phish lub All Email > **adresy URL** lub karty **Kliknięcia adresu URL** . Wybierz wysuwany indywidualny adres URL, aby wyświetlić dodatkowe szczegóły dotyczące kliknięć tego adresu URL, w tym wszystkie tagi skojarzone z tym kliknięciem.

### <a name="updated-timeline-view"></a>Zaktualizowany widok osi czasu

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="Tagi adresu URL" lightbox="../../media/tags-urls.png":::
>
Dowiedz się więcej, oglądając [ten film wideo](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Rozszerzone możliwości

### <a name="top-targeted-users"></a>Najważniejsi użytkownicy docelowi

Najważniejsze rodziny złośliwego oprogramowania pokazują **najpopularniejszych użytkowników docelowych** w sekcji Złośliwe oprogramowanie. Najważniejsi użytkownicy docelowi zostaną rozszerzoni o widoki Phish i Wszystkie widoki poczty e-mail. Analitycy będą mogli zobaczyć pięciu pierwszych użytkowników docelowych wraz z liczbą prób dla każdego użytkownika w każdym widoku.

Osoby wykonujące operacje zabezpieczeń mogą wyeksportować listę docelowych użytkowników do limitu 3000 wraz z liczbą podjętych prób na potrzeby analizy w trybie offline dla każdego widoku poczty e-mail. Ponadto wybranie liczby prób (na przykład 13 prób na poniższej ilustracji) spowoduje otwarcie filtrowanego widoku w Eksploratorze zagrożeń, aby zobaczyć więcej szczegółów dotyczących wiadomości e-mail i zagrożeń dla tego użytkownika.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="Użytkownicy najczęściej" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>reguły transportu Exchange

Zespół ds. operacji zabezpieczeń będzie mógł zobaczyć wszystkie reguły transportu Exchange (lub reguły przepływu poczty) zastosowane do wiadomości w widoku siatki poczty e-mail. Wybierz **opcje Kolumna** w siatce, a następnie **dodaj Exchange regułę transportu** z opcji kolumny. Opcja reguł transportu Exchange jest również widoczna w wysuwu **Szczegóły** w wiadomości e-mail.

Zostaną wyświetlone nazwy i identyfikatory GUID reguł transportu stosowanych do komunikatu. Analitycy będą mogli wyszukiwać komunikaty przy użyciu nazwy reguły transportu. Jest to wyszukiwanie CONTAINS, co oznacza, że możesz również wykonywać wyszukiwania częściowe.

> [!IMPORTANT]
> Exchange wyszukiwanie reguł transportu i dostępność nazw zależą od określonej roli przypisanej Do Ciebie. Aby wyświetlić nazwy reguł transportu i wyszukać, musisz mieć jedną z następujących ról lub uprawnień. Jednak nawet bez poniższych ról lub uprawnień analityk może zobaczyć etykietę reguły transportu i informacje o identyfikatorze GUID w szczegółach wiadomości e-mail. Nie ma to wpływu na inne środowiska wyświetlania rekordów w siatkach poczty e-mail, wysuwanych wiadomości e-mail, filtrach i eksportie.
>
> - Tylko Exchange Online — zapobieganie utracie danych: wszystkie
> - Tylko Exchange Online — O365SupportViewConfig: Wszystkie
> - Microsoft Azure Active Directory lub Exchange Online — administrator zabezpieczeń: wszystkie
> - Azure Active Directory lub Exchange Online — czytelnik zabezpieczeń: wszystkie
> - Tylko Exchange Online — reguły transportu: wszystkie
> - Tylko Exchange Online — konfiguracja View-Only: wszystkie
>
> W siatce poczty e-mail, wysuwu Szczegóły i wyeksportowanym woluminie CSV wartości ETR są prezentowane z nazwą/identyfikatorem GUID, jak pokazano poniżej.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Reguły w Exchange Transport" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Łączniki przychodzące

Łączniki to zbiór instrukcji, które dostosowują sposób przepływu poczty e-mail do i z organizacji Microsoft 365 lub Office 365. Umożliwiają one stosowanie wszelkich ograniczeń zabezpieczeń lub mechanizmów kontroli. W Eksploratorze zagrożeń możesz wyświetlić łączniki powiązane z wiadomością e-mail i wyszukać wiadomości e-mail przy użyciu nazw łączników.

Wyszukiwanie łączników to zapytanie CONTAINS, co oznacza, że częściowe wyszukiwanie słów kluczowych może działać:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Szczegóły łącznika" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Aby używać Eksploratora lub wykrywania w czasie rzeczywistym, musisz mieć [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md).

- Eksplorator jest uwzględniony w planie Ochrona usługi Office 365 w usłudze Defender 2.
- Raport wykrywania w czasie rzeczywistym jest uwzględniony w planie Ochrona usługi Office 365 w usłudze Defender 1.
- Zaplanuj przypisywanie licencji dla wszystkich użytkowników, którzy powinni być chronieni przez Ochrona usługi Office 365 w usłudze Defender. Eksplorator i wykrywanie w czasie rzeczywistym pokazują dane wykrywania dla licencjonowanych użytkowników.

Aby wyświetlić i użyć Eksploratora lub wykrywania w czasie rzeczywistym, musisz mieć następujące uprawnienia:

- W portalu Microsoft 365 Defender:
  - Zarządzanie organizacją
  - Administrator zabezpieczeń (można to przypisać w centrum administracyjnym Azure Active Directory (<https://aad.portal.azure.com>)
  - Czytelnik zabezpieczeń
- W Exchange Online:
  - Zarządzanie organizacją
  - zarządzanie organizacją View-Only
  - adresaci View-Only
  - Zarządzanie zgodnością

Aby dowiedzieć się więcej o rolach i uprawnieniach, zobacz następujące zasoby:

- [Uprawnienia w portalu usługi Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online programu PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Więcej informacji

- [Znajdowanie i badanie dostarczonej złośliwej wiadomości e-mail](investigate-malicious-email-that-was-delivered.md)
- [Wyświetlanie złośliwych plików wykrytych w usłudze SharePoint Online, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Omówienie widoków w Eksploratorze zagrożeń (i wykrywaniu w czasie rzeczywistym)](threat-explorer-views.md)
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
- [Zautomatyzowane badanie i reagowanie w usłudze Microsoft Threat Protection](automated-investigation-response-office.md)
- [Badanie wiadomości e-mail za pomocą strony jednostki poczty e-mail](mdo-email-entity-page.md)
