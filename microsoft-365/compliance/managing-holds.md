---
title: Zarządzanie blokadami w ramach zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/27/2022
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
ms.openlocfilehash: f7c47afe74c4d48036160d0fbb0c9717f884bc46
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629448"
---
# <a name="manage-holds-in-ediscovery-premium"></a>Zarządzanie blokadami w ramach zbierania elektronicznych materiałów dowodowych (Premium)

Możesz użyć przypadku Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium), aby utworzyć blokady, aby zachować zawartość, która może być istotna dla Twojego przypadku. Korzystając z funkcji archiwizacji zbierania elektronicznych materiałów dowodowych (Premium), można umieścić blokady na opiekunach i ich źródłach danych. Ponadto możesz wstrzymać skrzynki pocztowe i witryny OneDrive dla Firm. Możesz również umieścić blokadę w skrzynce pocztowej grupy, witrynie programu SharePoint i witrynie OneDrive dla Firm dla grupy platformy Microsoft 365. Podobnie możesz wstrzymać skrzynkę pocztową i witrynę skojarzoną z usługą Microsoft Teams. W przypadku wstrzymania lokalizacji zawartości zawartość jest przechowywana do momentu zwolnienia opiekuna, usunięcia określonej lokalizacji danych lub całkowitego usunięcia zasad blokady.

## <a name="manage-custodian-based-holds"></a>Zarządzanie blokadami opartymi na opiekunach

W niektórych przypadkach możesz mieć zestaw opiekunów, których zidentyfikowano i którzy zdecydowali się zachować swoje dane w trakcie sprawy. W przypadku zbierania elektronicznych materiałów dowodowych (Premium), gdy opiekunowie zostaną zatrzymani, użytkownik i wybrane źródła danych zostaną automatycznie dodane do zasad blokady opiekuna.

Aby wyświetlić zasady blokady opiekuna:

1. W portal zgodności Microsoft Purview kliknij pozycję **eDiscovery > Advanced**, aby wyświetlić listę przypadków w organizacji.

2. Przejdź do karty **Źródła** , aby dodać opiekunów w twojej sprawie. Aby dowiedzieć się, jak dodać i umieścić opiekunów w zawieszeniu w sprawie zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Dodawanie opiekunów do sprawy](add-custodians-to-case.md). Jeśli dodano już opiekunów i zawiesiliśmy ich, przejdź do kroku 3.

3. Przejdź do karty **Blokady** i kliknij pozycję **KustoszHold\<HoldId>**.

4. Na stronie wysuwanej można wykonywać akcje, takie jak stosowanie zapytania do blokady opartej na opiekunie. Aby uzyskać więcej informacji na temat tworzenia zapytania blokady i używania [warunków, zobacz Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Zarządzanie blokadami bez opieki

Podczas tworzenia blokady dostępne są następujące opcje określania zakresu zawartości przechowywanej w określonych lokalizacjach zawartości:

- Tworzysz nieskończoną blokadę, w której cała zawartość jest wstrzymana. Alternatywnie można utworzyć blokadę opartą na zapytaniach, w której wstrzymana jest tylko zawartość zgodna z zapytaniem wyszukiwania.
  
- Można określić zakres dat do przechowywania tylko zawartości, która została wysłana, odebrana lub utworzona w tym zakresie dat. Alternatywnie możesz przechowywać całą zawartość niezależnie od tego, kiedy została wysłana, odebrana lub utworzona.

Aby utworzyć blokadę bez nadzoru w przypadku zbierania elektronicznych materiałów dowodowych (Premium):

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> kliknij pozycję **eDiscovery > Advanced** , aby wyświetlić listę przypadków w organizacji.
  
2. Kliknij przycisk **Otwórz** obok przypadku, w którym chcesz utworzyć blokady.
  
3. Na stronie głównej sprawy kliknij kartę **Blokady** .
  
4. Na karcie **Blokady** kliknij pozycję **Utwórz**.
  
5. Na stronie **Nazwa blokady podaj** nazwę blokady. Nazwa blokady musi być unikatowa w organizacji.

6. (Opcjonalnie) W polu **Opis** dodaj opis blokady.
  
7. Kliknij **Dalej**.
  
8. Wybierz lokalizacje zawartości, które chcesz umieścić w blokadzie. Skrzynki pocztowe, witryny i foldery publiczne można wstrzymać.

   1. **Poczta e-mail programu Exchange** — kliknij pozycję **Wybierz użytkowników, grupy lub zespoły,** a następnie kliknij ponownie pozycję **Wybierz użytkowników, grupy lub zespoły,** aby określić skrzynki pocztowe do wstrzymania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne (aby zatrzymać skrzynki pocztowe członków grupy), aby zostać wstrzymane. Możesz również umieścić blokadę w skojarzonej skrzynce pocztowej dla grupy platformy Microsoft 365 lub zespołu firmy Microsoft. Zaznacz pole wyboru użytkownik, grupa, zespół, kliknij pozycję **Wybierz**, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Po kliknięciu **przycisku Wybierz użytkowników, grupy lub zespoły w** celu określenia skrzynek pocztowych, które mają zostać wstrzymane, wyświetlany selektor skrzynki pocztowej jest pusty. Jest to z założenia w celu zwiększenia wydajności. Aby dodać osoby do tej listy, wpisz nazwę (co najmniej 3 znaki) w polu wyszukiwania.

   1. **Witryny programu SharePoint** — kliknij pozycję **Wybierz witryny,** a następnie kliknij ponownie pozycję **Wybierz witryny**, aby określić witryny programu SharePoint i OneDrive dla Firm, które mają zostać wstrzymane. Wpisz adres URL każdej witryny, która ma zostać wstrzymana. Możesz również dodać adres URL witryny programu SharePoint dla grupy platformy Microsoft 365 lub zespołu firmy Microsoft. Kliknij **pozycję Wybierz**, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Adres URL konta usługi OneDrive użytkownika zawiera jego główną nazwę użytkownika (UPN) (na przykład `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). W rzadkich przypadkach, gdy nazwa UPN danej osoby zostanie zmieniona, jej adres URL usługi OneDrive również zmieni się, aby włączyć nową nazwę UPN. Jeśli konto użytkownika w usłudze OneDrive jest częścią blokady bez nadzoru i jego nazwa UPN została zmieniona, musisz zaktualizować blokadę i wskazać nowy adres URL usługi OneDrive. Aby uzyskać więcej informacji, zobacz [Jak zmiany nazwy UPN wpływają na adres URL usługi OneDrive](/onedrive/upn-changes).

   1. **Foldery publiczne programu Exchange** — przenieś przełącznik do pozycji Wszystkie, aby wstrzymać wszystkie foldery publiczne w organizacji Exchange Online. Nie można wybrać określonych folderów publicznych do wstrzymania. Pozostaw przełącznik ustawiony na **Brak** , jeśli nie chcesz zatrzymywać folderów publicznych.

9. Po zakończeniu dodawania lokalizacji zawartości do blokady kliknij przycisk **Dalej**.
  
10. Aby utworzyć blokadę opartą na zapytaniach z warunkami, wykonaj następujące czynności. W przeciwnym razie po prostu kliknij przycisk **Dalej**.

    - W polu **Słowa kluczowe** wpisz zapytanie wyszukiwania w polu, aby tylko zawartość spełniająca kryteria wyszukiwania została wstrzymana. Można określić słowa kluczowe, właściwości komunikatu lub właściwości dokumentu, takie jak nazwy plików. Można również użyć bardziej złożonych zapytań, które używają operatora logicznego, takiego jak AND, OR lub NOT. Jeśli pole słowa kluczowego pozostanie puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie wstrzymana.

    - Kliknij  **pozycję Dodaj** warunki, aby dodać co najmniej jeden warunk, aby zawęzić zapytanie wyszukiwania dla blokady. Każdy warunek dodaje klauzulę do zapytania wyszukiwania KQL, które jest tworzone i uruchamiane podczas tworzenia blokady. Można na przykład określić zakres dat, aby dokumenty poczty e-mail lub witryny utworzone w zakresie dat zostały wstrzymane. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operatora AND. Oznacza to, że elementy muszą spełniać zarówno zapytanie słowa kluczowego, jak i warunek, który ma zostać wstrzymany.

     Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania i używania warunków, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Po skonfigurowaniu blokady opartej na zapytaniach kliknij przycisk **Dalej**.

12. Przejrzyj ustawienia, a następnie kliknij pozycję **Utwórz tę blokadę**.

> [!NOTE]
> Podczas tworzenia blokady opartej na zapytaniach cała zawartość z wybranych lokalizacji jest początkowo wstrzymana. Po uruchomieniu zadania czasomierza w programie Exchange lub SharePoint każda zawartość niezgodna z określonym zapytaniem zostanie wyczyszczona z blokady. Gdy liczba znaków we wszystkich zapytaniach w jednej lokalizacji przekroczy 10 000 znaków, cała lokalizacja zostanie wstrzymana. 

> [!NOTE]
> Jeśli adres SMTP użytkownika zmieni się po wstrzymaniu skrzynki pocztowej użytkownika, skrzynka pocztowa pozostanie wstrzymana. Aby użyć nowego adresu SMTP do przechowywania, utwórz nowe blokady.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Umieszczanie blokady w aplikacjach Microsoft Teams i grupach Office 365

Usługa Microsoft Teams jest oparta na grupach Office 365. W związku z tym umieszczenie ich w blokadzie zbierania elektronicznych materiałów dowodowych (Premium) jest podobne.

- **Jak mogę mapować dodatkową witrynę Grupy Microsoft 365 lub Microsoft Teams na opiekuna? A co z umieszczeniem blokady bez nadzoru na Grupy Microsoft 365 i Microsoft Teams?** Usługa Microsoft Teams jest oparta na Grupy Microsoft 365. W związku z tym umieszczenie ich w zawieszeniu w przypadku zbierania elektronicznych materiałów dowodowych jest podobne. Podczas umieszczania aplikacji Grupy Microsoft 365 i microsoft teams należy pamiętać o następujących kwestiach.

  - Aby umieścić zawartość znajdującą się w Grupy Microsoft 365 i usłudze Microsoft Teams, należy określić skrzynkę pocztową i witrynę programu SharePoint skojarzoną z grupą lub zespołem.
  
  - Uruchom polecenie cmdlet **Get-UnifiedGroup** w Exchange Online, aby wyświetlić właściwości grupy platformy Microsoft 365 lub zespołu firmy Microsoft. Jest to dobry sposób na uzyskanie adresu URL witryny skojarzonej z grupą platformy Microsoft 365 lub zespołem firmy Microsoft. Na przykład następujące polecenie wyświetla wybrane właściwości grupy platformy Microsoft 365 o nazwie Senior Leadership Team:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Aby uruchomić polecenie cmdlet Get-UnifiedGroup, musisz mieć przypisaną rolę adresatów View-Only w Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

  - Po przeszukaniu skrzynki pocztowej użytkownika nie będą wyszukiwane żadne grupy platformy Microsoft 365 lub zespół firmy Microsoft, do których należy użytkownik. Podobnie w przypadku umieszczenia blokady grupy platformy Microsoft 365 lub zespołu firmy Microsoft tylko skrzynka pocztowa grupy i witryna grupy są wstrzymane; skrzynki pocztowe i witryny OneDrive dla Firm członków grupy nie zostaną wstrzymane, chyba że jawnie dodasz ich jako opiekunów lub umieścisz ich źródła danych w blokadzie. W związku z tym, jeśli konieczne jest wstrzymanie grupy platformy Microsoft 365 lub zespołu firmy Microsoft dla określonego opiekuna, rozważ mapowanie witryny grupy i skrzynki pocztowej grupy na opiekuna (zobacz Zarządzanie opiekunami w zakresie zbierania elektronicznych materiałów dowodowych (Premium)). Jeśli grupa platformy Microsoft 365 lub zespół firmy Microsoft nie można przypisać jednemu opiekunowi, rozważ dodanie źródła do blokady bez nadzoru.
  - Aby uzyskać listę członków grupy platformy Microsoft 365 lub zespołu firmy Microsoft, możesz wyświetlić właściwości na stronie [**Grupy**](https://go.microsoft.com/fwlink/p/?linkid=2052855) **główne** >  w Centrum administracyjne platformy Microsoft 365. Alternatywnie możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Aby uruchomić polecenie cmdlet **Get-UnifiedGroupLinks**, musisz mieć przypisaną rolę adresatów View-Only w Exchange Online lub być członkiem grupy ról przypisanej do roli adresatów View-Only.

  - Konwersacje kanału, które są częścią kanału usługi Microsoft Teams, są przechowywane w skrzynce pocztowej skojarzonej z zespołem. Podobnie pliki udostępniane przez członków zespołu w kanale są przechowywane w witrynie programu SharePoint zespołu. W związku z tym należy wstrzymać skrzynkę pocztową zespołu firmy Microsoft i witrynę programu SharePoint, aby zachować konwersacje i pliki w kanale.
  
  - Alternatywnie konwersacje, które są częścią listy czatów w usłudze Microsoft Teams, są przechowywane w skrzynce pocztowej użytkownika, który uczestniczy w czacie.  Pliki, które użytkownik udostępnia w konwersacjach czatu, są przechowywane w witrynie OneDrive dla Firm użytkownika, który udostępnia plik. W związku z tym należy umieścić skrzynki pocztowe poszczególnych użytkowników i witryny OneDrive dla Firm wstrzymane, aby zachować konwersacje i pliki na liście czatów.
  
  - Każdy kanał zespołu lub zespołu firmy Microsoft zawiera witrynę typu wiki do tworzenia notatek i współpracy. Zawartość witryny typu wiki jest automatycznie zapisywana w pliku w formacie mht. Ten plik jest przechowywany w bibliotece dokumentów usługi Teams Wiki Data w witrynie programu SharePoint zespołu. Zawartość witryny typu wiki można wstrzymać, umieszczając witrynę programu SharePoint zespołu.

    > [!NOTE]
    > 22 czerwca 2017 r. wydano możliwość przechowywania zawartości witryny typu wiki dla zespołu firmy Microsoft lub kanału zespołu (po wstrzymaniu witryny programu SharePoint zespołu). Jeśli witryna zespołu jest wstrzymana, zawartość witryny typu wiki zostanie zachowana począwszy od tego dnia. Jeśli jednak witryna zespołu jest wstrzymana, a zawartość witryny typu wiki została usunięta przed 22 czerwca 2017 r., zawartość witryny typu wiki nie została zachowana.
