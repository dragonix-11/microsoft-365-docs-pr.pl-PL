---
title: Strona jednostki Ochrona usługi Office 365 w usłudze Microsoft Defender wiadomości e-mail
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 04/01/2022
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Ochrona usługi Office 365 w usłudze Microsoft Defender klienci E5 i P1 i P2 mogą teraz uzyskać 360-stopniowy widok każdej wiadomości e-mail ze stroną jednostki poczty e-mail.
ms.openlocfilehash: 79863916cab3b859a0b24de9dc5eb9b4f324a3f9
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648772"
---
# <a name="the-email-entity-page"></a>Strona jednostki Poczta e-mail

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**W tym artykule:**
- [Docieranie do strony jednostki poczty e-mail](#reach-the-email-entity-page)
- [Odczytywanie strony jednostki poczty e-mail](#read-the-email-entity-page)
- [Korzystanie z kart strony jednostki poczty e-mail](#use-email-entity-page-tabs)
- [Nowość na stronie jednostki poczty e-mail](#new-to-the-email-entity-page)

Administratorzy Ochrona usługi Office 365 w usłudze Microsoft Defender E5 i Defender for Office P1 i P2 mają 360-stopniowy widok poczty e-mail przy użyciu **strony jednostki Poczta e-mail**. Ta strona przejdź do wiadomości e-mail została utworzona w celu ulepszenia informacji dostarczanych w [eksploratorze zagrożeń "szczegóły e-mail" wysuwane](threat-explorer-views.md).

## <a name="reach-the-email-entity-page"></a>Docieranie do strony jednostki poczty e-mail

Strona jednostki poczty e-mail jest dostępna w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> **Eksplorator** współpracy \> **& poczty e-mail**. Aby przejść bezpośrednio do strony **Eksploratora** , użyj polecenia <https://security.microsoft.com/threatexplorer>.

W **Eksploratorze** wybierz temat badanej wiadomości e-mail. W górnej części wysuwanej wiadomości e-mail zostanie wyświetlony złoty pasek. To zaproszenie na nową stronę z napisem "Wypróbuj naszą nową stronę jednostki poczty e-mail ze wzbogaconymi danymi...". Wybierz, aby wyświetlić nową stronę.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Złoty baner ze słowami *Wypróbuj naszą nową stronę jednostki poczty e-mail ze wzbogaconymi danymi*, aby przejść do nowego środowiska" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Grafika strony jednostki poczty e-mail, która koncentruje się na nagłówkach, które zobaczysz" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> Uprawnienia wymagane do wyświetlania i używania tej strony są takie same jak w przypadku wyświetlania **Eksploratora**. Administrator musi być członkiem administratora globalnego lub czytelnika globalnego, administratora zabezpieczeń lub czytelnika zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>Odczytywanie strony jednostki poczty e-mail

Struktura została zaprojektowana tak, aby była łatwa do odczytania i nawigowania w skrócie. Różne karty w górnej części strony umożliwiają bardziej szczegółowe zbadanie. Oto jak działa układ:

1. Najbardziej wymagane pola znajdują się po lewej stronie wysuwanego okienka. Te szczegóły są "lepkie", co oznacza, że są zakotwiczone w lewo bez względu na kartę, do której przechodzisz w pozostałej części wysuwanego.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Grafika strony jednostki poczty e-mail z wyróżnioną lewą stroną" lightbox="../../media/email-entities-3-left-panel.png":::

2. W prawym górnym rogu znajdują się akcje, które można wykonać w wiadomości e-mail. Wszystkie akcje, które można wykonać za pośrednictwem **Eksploratora** , będą również dostępne za pośrednictwem strony jednostki poczty e-mail.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Grafika strony jednostki poczty e-mail z wyróżnioną prawą stroną" lightbox="../../media/email-entities-5-preview.png":::

3. Dokładniejszą analizę można wykonać, sortując resztę strony. Sprawdź szczegóły wykrywania poczty e-mail, stan uwierzytelniania poczty e-mail i nagłówek. Ten obszar powinien być wyszukiwany w zależności od przypadku, ale informacje na tych kartach są dostępne dla każdej wiadomości e-mail.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Główny panel strony, który zawiera nagłówek wiadomości e-mail i stan uwierzytelniania" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>Korzystanie z kart strony jednostki poczty e-mail

Karty w górnej części strony jednostki umożliwiają efektywne badanie poczty e-mail.

1. **Oś czasu**: widok osi czasu dla wiadomości e-mail (na osi czasu **Eksploratora** ) przedstawia oryginalne dostarczanie do zdarzeń po dostarczeniu, które mają miejsce w wiadomości e-mail. W przypadku wiadomości e-mail, które nie mają żadnych akcji po dostarczeniu, widok pokazuje oryginalny wiersz dostarczania w widoku osi czasu. Zdarzenia takie jak: Automatyczne przeczyszczanie zerogodzin (ZAP), Korygowanie, kliknięcia adresu URL, et cetera, ze źródeł takich jak system, administrator i użytkownik, są wyświetlane tutaj w kolejności, w jakiej wystąpiły.
2. **Analiza**: Analiza pokazuje pola, które ułatwiają administratorom szczegółowe analizowanie wiadomości e-mail. W przypadkach, gdy administratorzy muszą dowiedzieć się więcej na temat wykrywania, nadawcy/odbiorcy i szczegółów uwierzytelniania poczty e-mail, powinni użyć karty Analiza. Linki do załączników i adresów URL znajdują się również na tej stronie w obszarze "Jednostki pokrewne". Zarówno załączniki, jak i zidentyfikowane zagrożenia są numerowane w tym miejscu, a kliknięcie spowoduje, że przejdziesz bezpośrednio do stron załączników i adresów URL. Ta karta zawiera również opcję Wyświetl nagłówek, aby *wyświetlić nagłówek wiadomości e-mail*. Administratorzy mogą porównać wszystkie szczegóły z nagłówków wiadomości e-mail obok informacji w panelu głównym, aby uzyskać przejrzystość.
3. **Załączniki**: sprawdza załączniki znalezione w wiadomości e-mail z innymi szczegółami dotyczącymi załączników. Liczba wyświetlanych załączników jest obecnie ograniczona do 10. Zwróć uwagę, że szczegóły detonacji załączników uznanych za złośliwe są również wyświetlane tutaj.
4. **Adresy URL**: ta karta zawiera listę adresów URL znalezionych w wiadomości e-mail z innymi szczegółami dotyczącymi adresów URL. Liczba adresów URL jest obecnie ograniczona do 10, ale te 10 jest priorytetem, aby najpierw wyświetlić *złośliwe adresy URL*. Priorytetyzacja pozwala zaoszczędzić czas i odgadnąć pracę. Adresy URL, które zostały uznane za złośliwe i zdetonowane, zostaną również wyświetlone tutaj.
5. **Podobne wiadomości e-mail**: ta karta zawiera listę wszystkich wiadomości e-mail podobnych do kombinacji *identyfikatora wiadomości sieciowej i adresata* specyficznej dla tej wiadomości e-mail. Podobieństwo jest oparte tylko na *treści komunikatu*. Ustalenia dokonane w wiadomościach e-mail w celu kategoryzowania ich jako "podobnych" nie obejmują uwzględnienia *załączników*.

## <a name="new-to-the-email-entity-page"></a>Nowość na stronie jednostki poczty e-mail

Istnieją nowe możliwości dostępne na tej stronie jednostki poczty e-mail. Oto lista.

### <a name="email-preview-for-cloud-mailboxes"></a>Podgląd wiadomości e-mail dla skrzynek pocztowych w chmurze

Administratorzy mogą wyświetlać podgląd wiadomości e-mail w skrzynkach pocztowych w chmurze, ***jeśli*** wiadomości e-mail są nadal obecne w chmurze. W przypadku usunięcia nietrwałego (przez administratora lub użytkownika) lub zap (do kwarantanny) wiadomości e-mail nie są już obecne w lokalizacji chmury. W takim przypadku administratorzy nie będą mogli wyświetlać podglądu tych konkretnych wiadomości e-mail. Wiadomości e-mail, które zostały porzucone lub gdzie dostarczanie nie powiodło się, nigdy nie dotarły do skrzynki pocztowej. W związku z tym administratorzy nie będą mogli wyświetlać podglądu tych wiadomości e-mail.

> [!WARNING]
> Podgląd wiadomości e-mail wymaga specjalnej roli o nazwie **Wersja zapoznawcza**. Tę rolę można dodać w portalu Microsoft 365 Defender zgodnie z opisem w [temacie Role współpracy & poczty e-mail w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). Może być konieczne utworzenie nowej grupy ról **współpracy & poczty e-mail** i dodanie roli **w wersji zapoznawczej** do nowej grupy ról lub dodanie roli **w wersji zapoznawczej** do grupy ról, która umożliwia administratorom w organizacji pracę w **Eksploratorze**.

### <a name="detonation-details"></a>Szczegóły detonacji

Te szczegóły są specyficzne dla załączników i adresów URL wiadomości e-mail. Użytkownicy mogą zobaczyć te szczegóły, przechodząc do Eksploratora i stosując filtr *technologii wykrywania* ustawiony do detonacji pliku lub detonacji adresu URL. Wiadomości e-mail filtrowane pod kątem detonacji plików będą zawierać złośliwy plik ze szczegółami detonacji, a te filtrowane pod kątem adresów URL zawierają złośliwy adres URL i szczegóły jego detonacji.

Użytkownicy zobaczą wzbogacone szczegóły detonacji dla znanych złośliwych załączników lub adresów URL znalezionych w ich wiadomościach e-mail, które zostały zdetonowane dla określonej dzierżawy. Będzie on zawierać łańcuch detonacji, podsumowanie detonacji, zrzut ekranu i szczegóły obserwowanego zachowania, aby pomóc klientom zrozumieć, dlaczego załącznik lub adres URL został uznany za złośliwy i zdetonowany.

1. *Łańcuch detonacji*. Detonacja pojedynczego pliku lub adresu URL może wywołać wiele detonacji. Łańcuch detonacji śledzi ścieżkę detonacji, w tym oryginalny złośliwy plik lub adres URL, który spowodował werdykt, oraz wszystkie inne pliki lub adresy URL dotknięte detonacją. Te adresy URL lub dołączone pliki mogą nie być bezpośrednio obecne w wiadomości e-mail, ale uwzględnienie tej analizy jest ważne dla określenia, dlaczego plik lub adres URL został uznany za złośliwy.  

    > [!NOTE]
    > Może to wskazywać tylko element najwyższego poziomu, jeśli żadna z połączonych z nim jednostek nie była problematyczna lub została zdetonowana.

1. *Podsumowanie detonacji* zawiera podstawowe podsumowanie detonacji, takie jak *czas analizy*, czas, kiedy nastąpiła detonacja, system operacyjny i aplikacja, system operacyjny i aplikacja, w której doszło do detonacji, rozmiar pliku i przyczyna werdyktu.
1. *Zrzuty ekranu* pokazują zrzuty ekranu przechwycone podczas detonacji. Podczas detonacji może być wiele zrzutów ekranu. Nie są przechwytywane żadne zrzuty ekranu dla
    - Pliki typu kontenera, takie jak .zip lub .rar.
    - Jeśli adres URL zostanie otwarty w linku, który bezpośrednio pobierze plik. Jednak pobrany plik zostanie wyświetlony w łańcuchu detonacji.
1. *Szczegóły zachowania* to eksport, który pokazuje szczegóły zachowania, takie jak dokładne zdarzenia, które miały miejsce podczas detonacji, oraz obserwowane elementy zawierające adresy URL, adresy IP, domeny i pliki znalezione podczas detonacji (i mogą być problematyczne lub niegroźne). Należy pamiętać, że nie ma żadnych szczegółów zachowania dla:
    - Pliki kontenera, takie jak .zip lub .rar, które przechowują inne pliki.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Podsumowanie detonacji przedstawiające łańcuch, podsumowanie, szczegóły detonacji i zrzut ekranu pod nagłówkiem *Analiza szczegółowa*" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Inne innowacje

*Tagi*: są to tagi stosowane do użytkowników. Jeśli użytkownik jest adresatem, administratorzy zobaczą tag *adresata* . Podobnie, jeśli użytkownik jest nadawcą, *tagiem nadawcy* . Będzie ona wyświetlana po lewej stronie strony jednostek poczty e-mail (w części opisanej jako *lepka* , a zatem zakotwiczona na stronie).

*Najnowsza lokalizacja dostarczania*: najnowsza lokalizacja dostarczania to lokalizacja, w której wiadomość e-mail wylądowała po zakończeniu akcji systemowych, takich jak ZAP, lub akcji administratora, takich jak Przenoszenie do usuniętych elementów. Najnowsza lokalizacja dostarczania nie jest przeznaczona do informowania administratorów o *bieżącej* lokalizacji komunikatu. Jeśli na przykład użytkownik usunie komunikat lub przeniesie go do archiwum, lokalizacja dostarczania nie zostanie zaktualizowana. Jeśli jednak wykonano akcję systemową i zaktualizowano lokalizację (np. zap powodującą przeniesienie wiadomości e-mail do kwarantanny), spowoduje to zaktualizowanie najnowszej lokalizacji dostarczania do kwarantanny.

*Szczegóły wiadomości e-mail*: szczegóły wymagane do dokładniejszego zrozumienia poczty e-mail dostępnej na karcie *Analiza* .

- *Exchange reguł transportu (znanych również jako reguły przepływu poczty lub etrów)*: te reguły są stosowane do wiadomości w warstwie transportu i mają pierwszeństwo przed werdyktami phish i spamu. Reguły przepływu poczty są tworzone i modyfikowane w centrum administracyjnym Exchange pod adresem <https://admin.exchange.microsoft.com/#/transportrules>, ale jeśli reguła przepływu poczty ma zastosowanie do wiadomości, nazwa reguły i identyfikator GUID będą wyświetlane tutaj. Cenne informacje do celów śledzenia.

- *Przesłonięcia podstawowe: Źródło*: Przesłonięcia podstawowe i źródło odnoszą się do ustawienia dzierżawy lub użytkownika, które miało wpływ na dostarczanie wiadomości e-mail, przesłaniając lokalizację dostarczania podaną przez system (zgodnie z technologią zagrożeń i wykrywania). Na przykład może to być wiadomość e-mail zablokowana z powodu reguły transportu skonfigurowanej przez dzierżawę lub wiadomości e-mail dozwolonej z powodu ustawienia użytkownika końcowego dla Sejf nadawców. 

- *Wszystkie przesłonięcia*: Wszystkie przesłonięcia odnoszą się do listy przesłoń (ustawień dzierżawy lub użytkownika), które zostały zastosowane w wiadomości e-mail, co mogło lub nie miało wpływu na dostarczanie wiadomości e-mail. Jeśli na przykład do wiadomości e-mail zostanie zastosowana reguła transportu skonfigurowana przez dzierżawę, a także ustawienie zasad skonfigurowane przez dzierżawę (na przykład z listy Blokuj zezwalanie na dzierżawę), obie zostaną wyświetlone w tym polu. Pole przesłonięcia podstawowego można sprawdzić, aby określić ustawienie, które miało wpływ na dostarczanie wiadomości e-mail. 

- *Poziom skarg zbiorczych (BCL)*: poziom skarg zbiorczych (BCL) komunikatu. Wyższa lista BCL wskazuje, że wiadomość e-mail zbiorcza jest bardziej skłonna do generowania skarg (naturalny wynik, jeśli wiadomość e-mail może być spamem).

- *Poziom zaufania do spamu (SCL)* : poziom ufności spamu (SCL) wiadomości. Wyższa wartość wskazuje, że wiadomość jest bardziej prawdopodobna jako spam.

- *Typ klienta*: wskazuje typ klienta, z którego wysłano wiadomość e-mail, na przykład REST.

- *Przekazywanie*: w przypadku scenariuszy z automatycznym przekierowywaniem wskazuje użytkownika przekazującego, a także typ przekazywania, taki jak etr lub przekazywanie SMTP. 

- *Lista dystrybucyjna*: pokazuje listę dystrybucyjną, jeśli odbiorca otrzymał wiadomość e-mail jako członek listy. Pokazuje listę dystrybucji najwyższego poziomu, jeśli istnieją zagnieżdżone listy dystrybucyjne.  

- *Do, DW*: wskazuje adresy, które są wymienione w polach Do, DW wiadomości e-mail. Informacje w tych polach są ograniczone do 5000 znaków. 

- *Nazwa domeny*: jest nazwą domeny nadawcy.

- *Właściciel domeny*: określa właściciela domeny wysyłającej.

- *Lokalizacja domeny*: określa lokalizację domeny wysyłającej.

- *Data utworzenia domeny*: określa datę utworzenia domeny wysyłającej. Nowo utworzona domena jest czymś, co można zachować ostrożność, jeśli inne sygnały wskazują na podejrzane zachowanie.

*Uwierzytelnianie poczty e-mail*: Metody uwierzytelniania poczty e-mail używane przez Microsoft 365 obejmują SPF, DKIM i DMARC.

- Struktura zasad nadawcy (**SPF**): opisuje wyniki sprawdzania SPF dla komunikatu. Możliwe wartości mogą być następujące:
  - Pass (adres IP): sprawdzanie SPF dla przekazanej wiadomości i zawiera adres IP nadawcy. Klient ma uprawnienia do wysyłania lub przekazywania wiadomości e-mail w imieniu domeny nadawcy.
  - Niepowodzenie (adres IP): sprawdzanie SPF komunikatu nie powiodło się i zawiera adres IP nadawcy. Jest to czasami nazywane twardym niepowodzeniem.
  - Softfail (przyczyna): Rekord SPF wyznaczył hosta jako niedozwolony do wysyłania, ale jest w okresie przejściowym.
  - Neutralny: rekord SPF jawnie stwierdza, że nie potwierdza, czy adres IP jest autoryzowany do wysyłania.
  - Brak: domena nie ma rekordu SPF lub rekord SPF nie daje wyniku.
  - Temperror: Wystąpił tymczasowy błąd. Na przykład błąd DNS. To samo sprawdzenie później może zakończyć się pomyślnie.
  - Permerror: Wystąpił trwały błąd. Na przykład domena ma nieprawidłowo sformatowany rekord SPF.

- DomainKeys Identified Mail (**DKIM**):
  - Pass: wskazuje sprawdzanie DKIM dla przekazanego komunikatu.
  - Niepowodzenie (przyczyna): wskazuje sprawdzanie DKIM dla komunikatu nie powiodło się i dlaczego. Jeśli na przykład wiadomość nie została podpisana lub podpis nie został zweryfikowany.
  - Brak: wskazuje, że komunikat nie został podpisany. Może to oznaczać, że domena ma rekord DKIM lub rekord DKIM nie daje wyniku, tylko że ten komunikat nie został podpisany.

- Uwierzytelnianie, raportowanie i zgodność komunikatów oparte na domenie (**DMARC**):
  - Pass: wskazuje sprawdzanie DMARC dla przekazanego komunikatu.
  - Niepowodzenie: wskazuje, że sprawdzanie DMARC dla komunikatu nie powiodło się.
  - Bestguesspass: wskazuje, że nie istnieje rekord DMARC TXT dla domeny, ale gdyby istniał, sprawdzanie DMARC dla komunikatu zostałoby zakończone.
  - Brak: wskazuje, że dla domeny wysyłającej w systemie DNS nie istnieje żaden rekord TXT DMARC.

*Uwierzytelnianie złożone*: jest to wartość używana przez Microsoft 365 do łączenia uwierzytelniania poczty e-mail, takiego jak SPF, DKIM i DMARC, w celu ustalenia, czy komunikat jest autentyczny. Używa domeny *Od:* poczty jako podstawy oceny.

### <a name="email-summary-panel"></a>Panel podsumowania wiadomości e-mail

Panel podsumowania wiadomości e-mail to podsumowany widok pełnej strony jednostki poczty e-mail. Zawiera on ustandaryzowane szczegóły dotyczące wiadomości e-mail (np. wykrycia), a także informacje specyficzne dla kontekstu (np. dotyczące metadanych kwarantanny lub przesyłania). Panel podsumowania wiadomości e-mail zastępuje tradycyjne wysuwane elementy Wykrywanie w czasie rzeczywistym, Eksplorator zagrożeń, Przesyłanie i Raportowanie.

> [!div class="mx-imgBorder"]
> ![Otwórz link jednostki poczty e-mail.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Aby wyświetlić wszystkie składniki, kliknij link **Otwórz jednostkę poczty e-mail** , aby otworzyć pełną stronę jednostki poczty e-mail.  

Panel podsumowania wiadomości e-mail jest podzielony na następujące sekcje:  

- *Szczegóły dostarczania*: zawiera informacje o zagrożeniach i odpowiednim poziomie ufności, technologiach wykrywania oraz oryginalnej i najnowszej lokalizacji dostarczania.

- *Szczegóły wiadomości e-mail*: zawiera informacje o właściwościach wiadomości e-mail, takich jak nazwa nadawcy, adres nadawcy, czas odebrania, szczegóły uwierzytelniania i inne inne szczegóły.

- *Adresy URL*: domyślnie zobaczysz 3 adresy URL i odpowiadające im zagrożenia. Zawsze możesz kliknąć pozycję **Wyświetl wszystkie adresy URL,** aby rozwinąć i wyświetlić wszystkie adresy URL i wyeksportować je.  

- *Załączniki*: domyślnie zobaczysz 3 załączniki. Zawsze możesz kliknąć pozycję **Wyświetl wszystkie załączniki** , aby rozwinąć i wyświetlić wszystkie załączniki. 

Oprócz powyższych sekcji zobaczysz również sekcje specyficzne dla kilku środowisk zintegrowanych z panelem podsumowania: 

- Zgłoszenia: 

    - *Szczegóły przesyłania*: zawiera informacje o konkretnych przesłanych, takich jak:
        - Data przesłania
        - Temat
        - Typ przesyłania
        - Powód przesłania
        - Identyfikator przesyłania
        - Przesłane przez

    - *Szczegóły wyniku*: Przesyłane komunikaty są przeglądane. Możesz zobaczyć wynik przesłania, a także wszelkie zalecane następne kroki.

- Kwarantanny:  

    - *Szczegóły kwarantanny*: zawiera szczegóły specyficzne dla kwarantanny. Aby uzyskać więcej informacji, zobacz [Zarządzanie komunikatami poddanymi kwarantannie](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Wygasa: data/godzina automatycznego i trwałego usunięcia komunikatu z kwarantanny.
        - Wydano dla: Wszystkie adresy e-mail (jeśli istnieją), na które wiadomość została wydana.
        - Nie została jeszcze wydana na adres: wszystkie adresy e-mail (jeśli istnieją), na które wiadomość nie została jeszcze wydana.

    - *Akcje kwarantanny*: Aby uzyskać więcej informacji na temat różnych akcji kwarantanny, zobacz [Zarządzanie komunikatami poddanymi kwarantannie](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
