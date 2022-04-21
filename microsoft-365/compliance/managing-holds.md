---
title: Zarządzanie blokadami zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dowiedz się, jak umieszczać blokady na opiekunach i ich źródłach danych, aby zachować odpowiednią zawartość w przypadku zbierania elektronicznych materiałów dowodowych (Premium).
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: 6ec8e31fddba430a7a148eea5c8b07eb35872641
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996773"
---
# <a name="manage-holds-in-ediscovery-premium"></a>Zarządzanie blokadami zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz użyć sprawy zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium), aby utworzyć blokady w celu zachowania zawartości, która może być istotna dla Twojej sprawy. Korzystając z funkcji archiwizacji zbierania elektronicznych materiałów dowodowych (Premium), można umieścić blokady na opiekunach i ich źródłach danych. Ponadto możesz wstrzymać skrzynki pocztowe i witryny OneDrive dla Firm. Możesz również umieścić blokadę w skrzynce pocztowej grupy, SharePoint lokacji i witrynie OneDrive dla Firm dla grupy Microsoft 365. Podobnie możesz umieścić blokadę w skrzynce pocztowej i witrynie skojarzonej z Microsoft Teams. W przypadku wstrzymania lokalizacji zawartości zawartość jest przechowywana do momentu zwolnienia opiekuna, usunięcia określonej lokalizacji danych lub całkowitego usunięcia zasad blokady.

## <a name="manage-custodian-based-holds"></a>Zarządzanie blokadami opartymi na opiekunach

W niektórych przypadkach możesz mieć zestaw opiekunów, których zidentyfikowano i którzy zdecydowali się zachować swoje dane w trakcie sprawy. W przypadku zbierania elektronicznych materiałów dowodowych (Premium), gdy opiekunowie zostaną zatrzymani, użytkownik i wybrane źródła danych zostaną automatycznie dodane do zasad blokady opiekuna.

Aby wyświetlić zasady blokady opiekuna:

1. W portalu zgodności usługi Microsoft Purview kliknij pozycję **eDiscovery > Advanced** , aby wyświetlić listę przypadków w organizacji.

2. Przejdź do karty **Źródła** , aby dodać opiekunów w twojej sprawie. Aby dowiedzieć się, jak dodać i umieścić opiekunów w zawieszeniu w sprawie zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Dodawanie opiekunów do sprawy](add-custodians-to-case.md). Jeśli dodano już opiekunów i zawiesiliśmy ich, przejdź do kroku 3.

3. Przejdź do karty **Blokady** i kliknij pozycję **KustoszHold\<HoldId>**.

4. Na stronie wysuwanej możesz zobaczyć statystyki blokady dla zasad. Możesz również wykonywać akcje, takie jak stosowanie zapytania do blokady opartej na opiekunie. Aby uzyskać więcej informacji na temat tworzenia zapytania blokady i używania [warunków, zobacz Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Zarządzanie blokadami bez opieki

Podczas tworzenia blokady dostępne są następujące opcje określania zakresu zawartości przechowywanej w określonych lokalizacjach zawartości:

- Tworzysz nieskończoną blokadę, w której cała zawartość jest wstrzymana. Alternatywnie można utworzyć blokadę opartą na zapytaniach, w której wstrzymana jest tylko zawartość zgodna z zapytaniem wyszukiwania.
  
- Można określić zakres dat do przechowywania tylko zawartości, która została wysłana, odebrana lub utworzona w tym zakresie dat. Alternatywnie możesz przechowywać całą zawartość niezależnie od tego, kiedy została wysłana, odebrana lub utworzona.

Aby utworzyć blokadę bez nadzoru dla sprawy zbierania elektronicznych materiałów dowodowych (Premium):

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> kliknij pozycję **eDiscovery > Advanced** , aby wyświetlić listę przypadków w organizacji.
  
2. Kliknij przycisk **Otwórz** obok przypadku, w którym chcesz utworzyć blokady.
  
3. Na stronie głównej sprawy kliknij kartę **Blokady** .
  
4. Na karcie **Blokady** kliknij pozycję **Utwórz**.
  
5. Na stronie **Nazwa blokady podaj** nazwę blokady. Nazwa blokady musi być unikatowa w organizacji.

6. (Opcjonalnie) W polu **Opis** dodaj opis blokady.
  
7. Kliknij **Dalej**.
  
8. Wybierz lokalizacje zawartości, które chcesz umieścić w blokadzie. Skrzynki pocztowe, witryny i foldery publiczne można wstrzymać.

   1. **Exchange wiadomości e-mail** — kliknij pozycję **Wybierz użytkowników, grupy lub zespoły,** a następnie kliknij ponownie pozycję **Wybierz użytkowników, grupy lub zespoły,** aby określić skrzynki pocztowe do wstrzymania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne (aby zatrzymać skrzynki pocztowe członków grupy), aby zostać wstrzymane. Możesz również umieścić blokadę w skojarzonej skrzynce pocztowej dla grupy Microsoft 365 lub zespołu firmy Microsoft. Zaznacz pole wyboru użytkownik, grupa, zespół, kliknij pozycję **Wybierz**, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Po kliknięciu **przycisku Wybierz użytkowników, grupy lub zespoły w** celu określenia skrzynek pocztowych, które mają zostać wstrzymane, wyświetlany selektor skrzynki pocztowej jest pusty. Jest to z założenia w celu zwiększenia wydajności. Aby dodać osoby do tej listy, wpisz nazwę (co najmniej 3 znaki) w polu wyszukiwania.

   1. **SharePoint witryn** — kliknij pozycję **Wybierz witryny,** a następnie kliknij ponownie pozycję **Wybierz witryny**, aby określić witryny SharePoint i OneDrive dla Firm, które mają zostać wstrzymane. Wpisz adres URL każdej witryny, która ma zostać wstrzymana. Możesz również dodać adres URL witryny SharePoint dla grupy Microsoft 365 lub zespołu firmy Microsoft. Kliknij **pozycję Wybierz**, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Adres URL konta OneDrive użytkownika zawiera jego główną nazwę użytkownika (UPN) (na przykład `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). W rzadkich przypadkach, gdy nazwa UPN danej osoby zostanie zmieniona, jej adres URL OneDrive również zmieni się, aby włączyć nową nazwę UPN. Jeśli konto OneDrive użytkownika jest częścią blokady bez nadzoru, a jego nazwa UPN została zmieniona, musisz zaktualizować blokadę i wskazać nowy adres URL OneDrive. Aby uzyskać więcej informacji, zobacz [Jak zmiany nazwy UPN wpływają na adres URL OneDrive](/onedrive/upn-changes).

   1. **Exchange folderów publicznych** — przenieś przełącznik do pozycji Wszystkie, aby wstrzymać wszystkie foldery publiczne w organizacji Exchange Online. Nie można wybrać określonych folderów publicznych do wstrzymania. Pozostaw przełącznik ustawiony na **Brak** , jeśli nie chcesz zatrzymywać folderów publicznych.

9. Po zakończeniu dodawania lokalizacji zawartości do blokady kliknij przycisk **Dalej**.
  
10. Aby utworzyć blokadę opartą na zapytaniach z warunkami, wykonaj następujące czynności. W przeciwnym razie po prostu kliknij przycisk **Dalej**.

    - W polu **Słowa kluczowe** wpisz zapytanie wyszukiwania w polu, aby tylko zawartość spełniająca kryteria wyszukiwania została wstrzymana. Można określić słowa kluczowe, właściwości komunikatu lub właściwości dokumentu, takie jak nazwy plików. Można również użyć bardziej złożonych zapytań, które używają operatora logicznego, takiego jak AND, OR lub NOT. Jeśli pole słowa kluczowego pozostanie puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie wstrzymana.

    - Kliknij  **pozycję Dodaj** warunki, aby dodać co najmniej jeden warunk, aby zawęzić zapytanie wyszukiwania dla blokady. Każdy warunek dodaje klauzulę do zapytania wyszukiwania KQL, które jest tworzone i uruchamiane podczas tworzenia blokady. Można na przykład określić zakres dat, aby dokumenty poczty e-mail lub witryny utworzone w zakresie dat zostały wstrzymane. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operatora AND. Oznacza to, że elementy muszą spełniać zarówno zapytanie słowa kluczowego, jak i warunek, który ma zostać wstrzymany.

     Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania i używania warunków, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Po skonfigurowaniu blokady opartej na zapytaniach kliknij przycisk **Dalej**.

12. Przejrzyj ustawienia, a następnie kliknij pozycję **Utwórz tę blokadę**.

> [!NOTE]
> Podczas tworzenia blokady opartej na zapytaniach cała zawartość z wybranych lokalizacji jest początkowo wstrzymana. Następnie każda zawartość, która nie jest zgodna z określonym zapytaniem, jest usuwana z blokady co siedem do 14 dni. Jednak blokada oparta na zapytaniach nie wyczyści zawartości, jeśli do lokalizacji zawartości zostanie zastosowanych więcej niż pięć blokad dowolnego typu lub jeśli jakikolwiek element ma problemy z indeksowaniem.

> [!NOTE]
> Jeśli adres SMTP użytkownika zmieni się po wstrzymaniu skrzynki pocztowej użytkownika, skrzynka pocztowa pozostanie wstrzymana. Aby użyć nowego adresu SMTP do przechowywania, utwórz nowe blokady.

## <a name="view-hold-statistics"></a>Wyświetlanie statystyk archiwum

Po pewnym czasie informacje o nowym blokadzie są wyświetlane w okienku szczegółów na karcie **Blokady** dla wybranego blokady. Informacje te obejmują liczbę skrzynek pocztowych i witryn, które zostały wstrzymane, oraz statystyki dotyczące zawartości, która została wstrzymana, takie jak całkowita liczba i rozmiar elementów umieszczonych w blokadzie oraz czas ostatniego obliczenia statystyk blokady. Te statystyki przechowywania pomagają określić, ile zawartości jest związanych ze sprawą zbierania elektronicznych materiałów dowodowych.

Należy pamiętać o następujących kwestiach dotyczących statystyk archiwum:

- Całkowita liczba wstrzymanych elementów wskazuje liczbę elementów ze wszystkich źródeł zawartości, które są wstrzymane. Jeśli utworzono blokadę opartą na zapytaniach, ta statystyka wskazuje liczbę elementów zgodnych z zapytaniem.
  
- Liczba wstrzymanych elementów obejmuje również elementy bez certyfikatu znalezione w lokalizacjach zawartości. Jeśli utworzysz blokadę opartą na zapytaniach, wszystkie elementy niezawłaszczone w lokalizacjach zawartości zostaną wstrzymane. Obejmuje to elementy niezainicjowane, które nie spełniają kryteriów wyszukiwania blokady opartej na zapytaniach i elementów niewyświetlonych, które mogą wykraczać poza warunek zakresu dat. Różni się to od tego, co dzieje się po uruchomieniu wyszukiwania zawartości, w którym niezainicjowane elementy, które nie są zgodne z zapytaniem wyszukiwania lub są wykluczone przez warunek zakresu dat, nie są uwzględniane w wynikach wyszukiwania. Aby uzyskać więcej informacji na temat elementów niezaindeksowanych, zobacz [Częściowo zaindeksowane elementy w wyszukiwaniu zawartości w Office 365](partially-indexed-items-in-content-search.md).

- Najnowsze statystyki blokady można uzyskać, klikając pozycję Aktualizuj statystyki, aby ponownie uruchomić oszacowanie wyszukiwania, które oblicza bieżącą liczbę wstrzymanych elementów.

- W razie potrzeby kliknij przycisk Odśwież na pasku narzędzi, aby zaktualizować statystyki blokady w okienku szczegółów.

- Jest to normalne, że liczba wstrzymanych elementów rośnie wraz z upływem czasu, ponieważ użytkownicy, których skrzynka pocztowa lub witryna jest wstrzymana, zazwyczaj wysyłają lub odbierają nową wiadomość e-mail oraz tworzą nowe SharePoint i OneDrive dla Firm dokumentów.

- Jeśli witryna SharePoint lub konto OneDrive zostaną przeniesione do innego regionu w środowisku z wieloma obszarami geograficznymi, statystyki dla tej witryny nie zostaną uwzględnione w statystykach blokady. Jednak zawartość witryny nadal będzie wstrzymana. Ponadto jeśli witryna zostanie przeniesiona do innego regionu, adres URL wyświetlany w blokadzie nie zostanie zaktualizowany. Musisz edytować blokadę i zaktualizować adres URL.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Umieszczanie blokady w grupach Microsoft Teams i Office 365

Microsoft Teams jest oparta na grupach Office 365. W związku z tym umieszczenie ich w zakładzie zbierania elektronicznych materiałów dowodowych (Premium) jest podobne.

- **Jak mogę mapować dodatkową witrynę Grupy Microsoft 365 lub Microsoft Teams na opiekuna? A co z umieszczeniem niestosownie blokady na Grupy Microsoft 365 i Microsoft Teams?** Microsoft Teams jest oparta na Grupy Microsoft 365. W związku z tym umieszczenie ich w zawieszeniu w przypadku zbierania elektronicznych materiałów dowodowych jest podobne. Podczas umieszczania Grupy Microsoft 365 i Microsoft Teams wstrzymania należy pamiętać o następujących kwestiach.

  - Aby umieścić zawartość znajdującą się w Grupy Microsoft 365 i Microsoft Teams wstrzymana, należy określić skrzynkę pocztową i witrynę SharePoint skojarzoną z grupą lub zespołem.
  
  - Uruchom polecenie cmdlet **Get-UnifiedGroup** w Exchange Online, aby wyświetlić właściwości grupy Microsoft 365 lub zespołu firmy Microsoft. Jest to dobry sposób na uzyskanie adresu URL witryny skojarzonej z grupą Microsoft 365 lub zespołem firmy Microsoft. Na przykład następujące polecenie wyświetla wybrane właściwości grupy Microsoft 365 o nazwie Senior Leadership Team:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Aby uruchomić polecenie cmdlet Get-UnifiedGroup, musisz mieć przypisaną rolę adresatów View-Only w Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

  - Po przeszukaniu skrzynki pocztowej użytkownika nie będą wyszukiwane żadne Microsoft 365 Group lub Microsoft Team, do których należy użytkownik. Podobnie w przypadku umieszczenia blokady grupy Microsoft 365 lub zespołu firmy Microsoft tylko skrzynka pocztowa grupy i witryna grupy są zawieszone; skrzynki pocztowe i witryny OneDrive dla Firm członków grupy nie są wstrzymane, chyba że jawnie dodasz ich jako opiekunów lub umieścisz ich źródła danych. W związku z tym, jeśli konieczne jest wstrzymanie grupy Microsoft 365 lub zespołu firmy Microsoft dla określonego opiekuna, rozważ mapowanie witryny grupy i skrzynki pocztowej grupy na opiekuna (zobacz Managing Custodians in eDiscovery (Premium)). Jeśli grupa Microsoft 365 lub zespół firmy Microsoft nie można przypisać jednemu opiekunowi, rozważ dodanie źródła do blokady bez nadzoru.
  - Aby uzyskać listę członków grupy Microsoft 365 lub zespołu firmy Microsoft, możesz wyświetlić właściwości na stronie **Grupy główne** >  w Centrum administracyjne platformy Microsoft 365.[](https://go.microsoft.com/fwlink/p/?linkid=2052855) Alternatywnie możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Aby uruchomić polecenie cmdlet **Get-UnifiedGroupLinks**, musisz mieć przypisaną rolę adresatów View-Only w Exchange Online lub być członkiem grupy ról przypisanej do roli adresatów View-Only.

  - Konwersacje kanału będące częścią kanału Microsoft Teams są przechowywane w skrzynce pocztowej skojarzonej z zespołem. Podobnie pliki udostępniane przez członków zespołu w kanale są przechowywane w SharePoint lokacji zespołu. W związku z tym należy wstrzymać skrzynkę pocztową zespołu firmy Microsoft i witrynę SharePoint, aby zachować konwersacje i pliki w kanale.
  
  - Alternatywnie konwersacje, które są częścią listy czatów w Microsoft Teams, są przechowywane w skrzynce pocztowej użytkownika, który uczestniczy w czacie.  Pliki, które użytkownik udostępnia w konwersacjach czatu, są przechowywane w witrynie OneDrive dla Firm użytkownika, który udostępnia plik. W związku z tym należy umieścić skrzynki pocztowe poszczególnych użytkowników i witryny OneDrive dla Firm wstrzymane, aby zachować konwersacje i pliki na liście czatów.
  
  - Każdy kanał zespołu lub zespołu firmy Microsoft zawiera witrynę typu wiki do tworzenia notatek i współpracy. Zawartość witryny typu wiki jest automatycznie zapisywana w pliku w formacie mht. Ten plik jest przechowywany w bibliotece dokumentów Teams Wiki Data w witrynie SharePoint zespołu. Zawartość witryny typu wiki można wstrzymać, umieszczając witrynę SharePoint zespołu.

    > [!NOTE]
    > 22 czerwca 2017 r. wydano możliwość przechowywania zawartości witryny typu wiki dla zespołu firmy Microsoft lub kanału zespołu (gdy witryna SharePoint zespołu została wstrzymana). Jeśli witryna zespołu jest wstrzymana, zawartość witryny typu wiki zostanie zachowana począwszy od tego dnia. Jeśli jednak witryna zespołu jest wstrzymana, a zawartość witryny typu wiki została usunięta przed 22 czerwca 2017 r., zawartość witryny typu wiki nie została zachowana.
