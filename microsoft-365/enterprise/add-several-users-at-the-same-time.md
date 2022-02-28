---
title: Dodawanie kilku użytkowników jednocześnie do usługi Microsoft 365 — Pomoc dla administratorów
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
- admindeeplinkMAC
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
description: 'Dowiedz się, jak dodać wielu użytkowników do listy Microsoft 365 dla firm z listy w arkuszu kalkulacyjnym lub innym pliku w formacie CSV. Obejrzyj klip wideo w serwisie YouTube, w który wyjaśniono, jak dodawać konta do Microsoft 365. Po zakończeniu tego procesu każdy użytkownik z kontem będzie miał skrzynkę pocztową Microsoft 365 pocztowej. '
ms.openlocfilehash: d9152ba8dfef21faeaba6f981c23359eb114b653
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985631"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a>Dodawanie kilku użytkowników jednocześnie do usługi Microsoft 365 — Pomoc dla administratorów

Każda osoba w Twoim zespole potrzebuje konta użytkownika, aby mieć możliwość logowania się i uzyskiwania dostępu Microsoft 365 usług, takich jak poczta e-mail Office. Jeśli jest wiele takich osób, możesz dodać ich konta jednocześnie z arkusza kalkulacyjnego programu Excel lub innego pliku zapisanego w formacie CSV. [Nie masz pewności, co to jest format CSV](add-several-users-at-the-same-time.md#not-sure-what-csv-format-is)?
  
> [!NOTE]
> Jeśli nie korzystasz z nowego centrum administracyjnego usługi Microsoft 365, możesz je włączyć, klikając przełącznik **Wypróbuj nowe centrum administracyjne** w górnej części strony głównej.

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a>Dodawanie wielu użytkowników w centrum administracyjne platformy Microsoft 365

1. Zaloguj się Microsoft 365 za pomocą konta służbowego.

2. W centrum administracyjnym wybierz pozycję **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**użytkownicy użytkownicy**</a>.

3. Wybierz **pozycję Dodaj wielu użytkowników**.

4. W panelu **Importuj wielu użytkowników** możesz opcjonalnie pobrać przykładowy plik CSV wypełniony danymi przykładowymi lub bez nich.

    Arkusz kalkulacyjny musi zawierać takie **same** nagłówki kolumn, jak arkusz przykładowy (Nazwa użytkownika, Imię itd.). Jeśli używasz szablonu, otwórz go w narzędziu do edycji tekstu, na przykład Notatnik, i rozważ pozostawienie tylko wszystkich danych w wierszu 1 i wprowadzenie danych tylko w wierszach 2 i poniżej.

    Twój arkusz kalkulacyjny musi także zawierać wartości dla nazwy użytkownika (na przykład jan@contoso.com) i nazwy wyświetlanej (na przykład Jan Michalski) każdego użytkownika.

  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Wprowadź ścieżkę pliku w polu lub wybierz przycisk **Przeglądaj**, aby przeglądać w poszukiwaniu lokalizacji pliku CSV, a następnie wybierz pozycję **Weryfikuj**.
  
    Jeśli występują problemy dotyczące pliku, zostaną one wyświetlone w panelu. Możesz także pobrać plik dziennika.

6. W oknie dialogowym **Ustawianie opcji użytkownika** możesz ustawić stan logowania i wybrać licencję produktu, która zostanie przypisana do wszystkich użytkowników.

7. W oknie dialogowym **Wyświetlanie wyników** możesz wybrać opcję wysłania wyników do siebie lub do innych użytkowników (hasła będą w formacie zwykłego tekstu), a także możesz sprawdzić, ilu użytkowników zostało utworzonych i czy trzeba zakupić dodatkowe licencje w celu ich przypisania do niektórych nowych użytkowników.

## <a name="next-steps"></a>Następne kroki

- Teraz te osoby mają już konta, muszą pobrać i zainstalować lub ponownie zainstalować program [Microsoft 365 lub Office 2016 na komputerze PC lub Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Każda osoba w Twoim zespole może zainstalować Microsoft 365 na maksymalnie 5 komputerach PC lub Mac.

- Każda osoba może również [](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) skonfigurować aplikacje Office i pocztę e-mail na urządzeniu przenośnym na maksymalnie 5 tabletach i 5 telefonach, takich jak telefony iPhone, tablety iPad oraz telefony i tablety z systemem Android. Dzięki temu te osoby mogą edytować pliki pakietu Office z dowolnego miejsca.

    Zobacz [Konfigurowanie Microsoft 365 dla](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) firm, aby uzyskać pełną listę kroków konfiguracji.

## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a>Więcej informacji na temat dodawania użytkowników do Microsoft 365

### <a name="not-sure-what-csv-format-is"></a>Nie masz pewności, co to jest format CSV?

Plik CSV jest plikiem z wartościami oddzielanymi przecinkami. Taki plik można utworzyć i edytować za pomocą dowolnego edytora tekstu lub programu do obsługi arkuszy kalkulacyjnych, takiego jak program Excel.
  
Na początek możesz pobrać [ten przykładowy arkusz kalkulacyjny](https://www.microsoft.com/download/details.aspx?id=45485). Pamiętaj, Microsoft 365 nagłówki kolumn w pierwszym wierszu, więc nie zamieniaj ich na nic innego. 
  
Zapisz plik pod nową nazwą i określ dla niego format CSV.
  
![Obraz, w jaki sposób zapisać plik w formacie Excel formacie CSV.](../media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Podczas zapisywania pliku prawdopodobnie zostanie wyświetlony monit informujący, że niektóre funkcje w skoroszycie zostaną utracone w razie zapisania pliku w formacie CSV. To normalne. Kliknij przycisk **Tak**, aby kontynuować.
  
![Obraz monitu, który może zostać wyświetlony Excel z pytaniem, czy naprawdę chcesz zapisać plik jako format CSV.](../media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Porady dotyczące formatowania arkusza kalkulacyjnego

- **Czy potrzebne są takie same nagłówki kolumn, jak w przykładowym arkuszu kalkulacyjnym?** Tak. Przykładowy arkusz kalkulacyjny zawiera nagłówki kolumn w pierwszym wierszu. Te nagłówki są wymagane. Dla każdego użytkownika, którego chcesz dodać do Microsoft 365, utwórz wiersz pod nagłówkiem. Jeśli dodasz, zmienisz lub usuniesz dowolny nagłówek kolumny, Microsoft 365 może nie być w stanie utworzyć użytkowników na stronie z informacji w pliku.

- **Co zrobić, jeśli nie mam wszystkich informacji wymaganych dla każdego użytkownika?** Nazwa użytkownika i nazwa wyświetlana są wymagane i nie można dodać nowego użytkownika bez tych informacji. Jeśli nie masz innych informacji, na przykład numeru faksu, możesz użyć spacji i przecinka, aby wskazać, że to pole ma pozostać puste.

- **Jak mały lub jak duży może być arkusz kalkulacyjny?** Arkusz kalkulacyjny musi zawierać co najmniej dwa wiersze. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.

- **Jakich języków można używać?** Podczas tworzenia arkusza kalkulacyjnego etykiety kolumn danych użytkownika można wprowadzać w dowolnym języku i za pomocą dowolnych znaków, nie można jednak zmieniać kolejności etykiet przedstawionej w przykładzie. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.

- **Co zrobić, gdy dodaję użytkowników z różnych krajów i regionów?** Utwórz osobny arkusz kalkulacyjny dla każdego obszaru. Dla każdego arkusza kalkulacyjnego musisz wykonać kroki kreatora Zbiorcze dodawanie użytkowników, nadając jedną lokalizację wszystkim użytkownikom zawartym w pliku, z którym pracujesz.

- **Czy istnieje limit liczby znaków, których można użyć?** Poniższa tabela zawiera etykiety kolumn danych użytkowników i maksymalną liczbę znaków dla każdej z nich w przykładowym arkuszu kalkulacyjnym.

|**Etykieta kolumny danych użytkownika**|**Maksymalna liczba znaków**|
|:-----|:-----|
|Nazwa użytkownika (wymagane)  <br/> |79, w tym znak @, w formacie name@domain\<extension\>. Alias użytkownika nie może mieć więcej niż 50 znaków, a nazwa domeny nie może mieć więcej, niż 48 znaków.  <br/> |
|Imię  <br/> |64  <br/> |
|Nazwisko  <br/> |64  <br/> |
|Nazwa wyświetlana (wymagane)  <br/> |256  <br/> |
|Stanowisko  <br/> |64  <br/> |
|Dział  <br/> |64  <br/> |
|Numer biura  <br/> |128  <br/> |
|Tel. w biurze  <br/> |64  <br/> |
|Telefon komórkowy  <br/> |64  <br/> |
|Faks  <br/> |64  <br/> |
|Adres  <br/> |1023  <br/> |
|Miasto  <br/> |128  <br/> |
|Województwo  <br/> |128  <br/> |
|Kod pocztowy  <br/> |40  <br/> |
|Kraj lub region  <br/> |128  <br/> |

### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a>Nadal masz problemy podczas dodawania użytkowników do Microsoft 365?

- **Sprawdź dokładnie, czy arkusz kalkulacyjny został poprawnie sformatowany.** Sprawdź, czy nagłówki kolumn są zgodne z nagłówkami w pliku przykładowym. Upewnij się, że zostały spełnione reguły dotyczące liczby znaków i że każde pole jest oddzielone przecinkiem.

- **Jeśli nowi użytkownicy nie są od razu widziani Microsoft 365, poczekaj kilka minut.** Może minąć trochę czasu, aby zmiany trafiły między wszystkimi usługami w Microsoft 365. 

## <a name="related-articles"></a>Artykuły pokrewne

[Dodawanie użytkowników pojedynczo lub zbiorczo do Microsoft 365](/office365/admin/add-users/add-users)