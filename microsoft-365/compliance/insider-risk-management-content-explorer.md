---
title: Eksplorator zawartości zarządzania ryzykiem w niejawnym programie testów
description: Informacje o Eksploratorze zawartości zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: d60726b7fbf68ecbeb8af2d40c4c18e2bb9aaa7c
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2021
ms.locfileid: "62988655"
---
# <a name="insider-risk-management-content-explorer"></a>Eksplorator zawartości zarządzania ryzykiem w niejawnym programie testów

Eksplorator zawartości zarządzania ryzykiem  w ramach niejawnego programu testów  umożliwia użytkownikom z przypisaną rolą grupy poszukań zarządzania ryzykiem w ramach niejawnego programu testów analizy kontekstu i szczegółów zawartości skojarzonej z działaniem w alertach. Dane dotyczące sprawy w Eksploratorze zawartości są odświeżane codziennie w celu dołączyć nowe działania. W przypadku wszystkich alertów, które są potwierdzone sprawą, kopie danych i plików wiadomości są archiwizowane jako migawka czasu elementów przy zachowaniu oryginalnych plików i wiadomości w źródłach pamięci. W razie potrzeby pliki danych sprawy mogą zostać wyeksportowane jako pdf lub w oryginalnym formacie pliku.

W przypadku nowych spraw wypełnianie zawartości w Eksploratorze zawartości trwa zwykle około godziny. W przypadku przypadków z dużą ilością zawartości utworzenie migawki może trwać dłużej. Jeśli zawartość jest nadal ładowana w Eksploratorze zawartości, zostanie wyświetlony wskaźnik postępu z wartością procentową ukończenia.

W niektórych przypadkach dane skojarzone ze sprawą mogą nie być dostępne jako migawka do przejrzenia w Eksploratorze zawartości. Taka sytuacja może wystąpić, gdy dane sprawy zostały usunięte lub przeniesione, lub gdy podczas przetwarzania danych sprawy występuje tymczasowy błąd. W takiej sytuacji wybierz pozycję Wyświetl  pliki na pasku ostrzegawczym, aby wyświetlić nazwy plików, ścieżkę i przyczynę niepowodzenia każdego pliku. W razie potrzeby te informacje można wyeksportować do .csv pliku danych (wartości rozdzielane przecinkami).

Jeśli zawartość obejmuje uprawnienia usługi Zarządzanie prawami do informacji, są one zachowywane dla kopiowanej zawartości, a użytkownicy z przypisaną  rolą Grupy użytkowników zarządzania ryzykiem w niejawnym programie testów będą potrzebowali tych uprawnień i praw, jeśli będą musieli otwierać i wyświetlać pliki. Do każdego pliku i wiadomości jest automatycznie przypisywany unikatowy identyfikator pliku w przypadku zarządzania ryzykiem w niejawnym programie testów na potrzeby zarządzania. Dokumenty skojarzone ze wskaźnikami urządzeń nie są uwzględniane w Eksploratorze zawartości.

> [!NOTE]
> Eksplorator zawartości uwzględnia działania użytkownika związane z Microsoft 365 usługami, takie jak aktywność użytkowników na SharePoint, Exchange, Microsoft Teams i OneDrive dla Firm.

## <a name="column-options"></a>Opcje kolumn

W Eksploratorze zawartości jest dostępnych kilka narzędzi do filtrowania i sortowania, aby ułatwić analitykom ryzyka i chętym przejrzenie przechwyconych danych i wiadomości oraz przejrzenie kontekstu w związku z sprawą. W przypadku podstawowego sortowania **kolumny klasy** **Data i Plik** obsługują sortowanie przy użyciu tytułów kolumn w okienku kolejki zawartości. Inne kolumny kolejki są dostępne do dodania do widoku w celu zapewnienia różnych widoków przestawnych plików i wiadomości.

Aby dodać lub usunąć nagłówki kolumn dla kolejki zawartości, użyj kontrolki Edytuj **kolumny** i wybierz jedną z poniższych opcji kolumn. Te kolumny są mapowane na typowe, e-mail i warunki właściwości dokumentu obsługiwane w Eksploratorze zawartości i wymienione w dalszej części tego artykułu.

| **Opcja Kolumny** | **Opis** |
|:------------------|:----------------|
| **Autor** | Pole autora z Office, które pozostaje zachowywane w przypadku skopiowania dokumentu. Jeśli na przykład użytkownik utworzy dokument i prześle go w wiadomości e-mail do innej osoby, która następnie przekaże go do SharePoint, dokument zachowa oryginalny autor. |
| **UDW** | Użytkownicy są dostępni w wiadomościach e-mail w polu wiadomości UDW. |
| **DW** | Użytkownicy są dostępni w wiadomościach e-mail w polu wiadomości DW. |
| **Ścieżka złożona** | Czytelna ścieżka dla człowieka, która opisuje źródło elementu. |
| **Identyfikator konwersacji** | Identyfikator konwersacji z wiadomości. |
| **Indeks konwersacji** | Indeks konwersacji z wiadomości. |
| **Godzina utworzenia** | Godzina utworzenia pliku lub wiadomości e-mail. |
| **Data (UTC)** | W przypadku wiadomości e-mail jest to data, w która wiadomość została odebrana przez adresata lub wysłana przez nadawcę. W przypadku dokumentów jest to data ostatniej modyfikacji dokumentu. Data jest w skoordynowanym czasie uniwersalnym (UTC).|
| **Motyw dominanty** | Motyw dominanty obliczony na podstawie analizy. |
| **Identyfikator zestawu wiadomości e-mail** | Identyfikator grupy dla wszystkich wiadomości w tym samym zestawie wiadomości e-mail. |
| **Identyfikator rodziny** | Identyfikator rodzinny grupuje razem wszystkie elementy; w przypadku wiadomości e-mail ta kolumna zawiera wiadomość i wszystkie załączniki. w przypadku dokumentów ta kolumna zawiera dokument i wszystkie elementy osadzone. |
| **Klasa pliku** | W przypadku zawartości SharePoint i OneDrive: **Dokument**; w przypadku zawartości z Exchange: Wiadomość **e-mail** lub **załącznik**. |
| **Identyfikator pliku** | Unikatowy identyfikator dokumentu w ramach sprawy. |
| **Ikona typu pliku** | Rozszerzenie pliku; na przykład docx, one, pptx lub xlsx. To pole ma tę samą właściwość co właściwość witryny FileExtension (Rozszerzenie Pliku). |
| **Identyfikator** | Identyfikator GUID pliku. |
| **Niezmienialny identyfikator** | Niezmienialny identyfikator przechowywany w programie Office 365. |
| **Typ inkluzywny** | Typ inkluzywny obliczany dla analiz: **0** – nie inkluzywny; **1** — włącznie; **2** — minus włącznie; **3** — kopie włącznie. |
| **Ostatnia modyfikacja** | Data ostatniej zmiany dokumentu. |
| **Oznaczone jako reprezentatywne** | Jeden dokument z każdego zestawu dokładnych duplikatów jest oznaczony jako przedstawicieli. |
| **Typ wiadomości** | Typ wiadomości e-mail, która ma być wyszukiwana. Możliwe wartości: kontakty, dokumenty, poczta e-mail, dane zewnętrzne, faksy, wiadomości błyskawiczne, dzienniki, spotkania, aplikacja Microsoft Teams (zwraca elementy z czatów, spotkań i połączeń w programie Microsoft Teams), notatki, wpisy, kanały informacyjne RSS, zadania, poczta głosowa |
| **Uczestnicy** | Lista wszystkich uczestników wiadomości; Na przykład Nadawca, Do, DW, UDW. |
| **Identyfikator przestawny** | Identyfikator tabeli przestawnej. |
| **Odebrano** | Data, do dnia, w który wiadomość e-mail została odebrana przez adresata. To pole ma tę samą właściwość co właściwość Otrzymano pocztę e-mail. |
| **Adresaci** | Wszystkie pola adresatów w wiadomości e-mail. Te pola to Do, DW i UDW. |
| **Identyfikator przedstawiciela** | Identyfikator numeryczny każdego zestawu dokładnych duplikatów. |
| **Nadawca** | Nadawca wiadomości e-mail. |
| **Nadawca/Autor** | W przypadku wiadomości e-mail osoba, która wysłała wiadomość. W przypadku dokumentów osoba cytowana w polu autora może Office dokumenty. Możesz wpisać więcej niż jedno imię i nazwisko, oddzielając je przecinkami. Dwie lub więcej wartości jest logicznie połączonych operatorem LUB. |
| **Typy informacji poufnych** | Typy informacji poufnych zidentyfikowane w zawartości. |
| **Etykiety wrażliwości** | Etykiety wrażliwości zastosowane do zawartości. |
| **Wysłano** | Data wysłania wiadomości e-mail przez nadawcę. To pole ma tę samą właściwość, co właściwość Wysłane wiadomości e-mail. |
| **Rozmiar** | Zarówno w przypadku wiadomości e-mail, jak i dokumentów, rozmiar elementu (w bajtach). |
| **Temat** | Tekst w wierszu tematu wiadomości e-mail. |
| **Temat/tytuł** | W przypadku wiadomości e-mail tekst w wierszu tematu wiadomości. W przypadku dokumentów jest to tytuł dokumentu. Jak wyjaśniono wcześniej, właściwość Tytuł to metadane określone w Microsoft Office dokumenty. Możesz wpisać nazwę więcej niż jednego tematu/tytułu, oddzielając ją przecinkami. Dwie lub więcej wartości jest logicznie połączonych operatorem LUB. |
| **Lista motywów** | Lista motywy obliczona na podstawie analizy. |
| **Tytuł** | Tytuł dokumentu. Właściwość Title to metadane określone w Office dokumenty. Ta nazwa różni się od nazwy pliku dokumentu. |
| **Do** | Adresat wiadomości e-mail w polu Do. |

## <a name="filtering"></a>Filtrowanie

Możesz użyć jednego lub kilku filtrów, aby zawęzić zakres wyszukiwania i zwrócić bardziej dopracowany zestaw wyników. Aby ustawić filtr, wybierz **pozycję Filtry** w górnej części kolejki zawartości. Wiele filtrów zawiera dodatkowe opcje filtrowania, które ułatwiają zawężenie wyników zwróconych przez filtr. Na przykład filtr *Data zawiera kontrolki* służące do konfigurowania *daty rozpoczęcia* i daty *zakończenia* dla **filtru** Data. Wybierz co najmniej jeden element filtru z następujących kategorii:

### <a name="common-filters"></a>Typowe filtry

| **Filtr** | **Opis** |
|:---------------------|:----------------|
| **Data (UTC)** | W przypadku wiadomości e-mail jest to data, w która wiadomość została odebrana przez adresata lub wysłana przez nadawcę. W przypadku dokumentów jest to data ostatniej modyfikacji dokumentu. |
| **Nadawca/Autor** | W przypadku wiadomości e-mail osoba, która wysłała wiadomość. W przypadku dokumentów cytowana osoba w polu *Autor* Office dokumenty. Możesz wpisać więcej niż jedno imię i nazwisko, oddzielając je przecinkami. |
| **Źródło** | Lokalizacja dokumentu w organizacji. Może to być na przykład SharePoint lokalizacji witryny. |
| **Temat/tytuł** | W przypadku wiadomości e-mail tekst w wierszu tematu wiadomości. W przypadku dokumentów jest to tytuł dokumentu. Właściwość Tytuł w dokumentach to metadane określone w Microsoft Office dokumenty. Możesz wpisać nazwę więcej niż jednego tematu/tytułu, oddzielając ją przecinkami. Dwie lub więcej wartości jest logicznie połączonych operatorem LUB. |

### <a name="email-filters"></a>Filtry wiadomości e-mail

| **Filtr** | **Opis** |
|:---------------------|:----------------|
| **UDW** | Pole UDW wiadomości e-mail. |
| **DW** | Pole DW wiadomości e-mail. |
| **Ma załącznik** | Wskazuje, czy wiadomość ma załącznik. Wartości są wyświetlane jako **prawda lub** **fałsz**. |
| **Załącznik wiadomości e-mail** | Jeśli dokument jest załącznikiem, ta wartość jest wymieniona jako **Tak**. |
| **Jest osadzony dokument** | Jeśli dokument jest osadzony w wiadomości e-mail, ta wartość jest wymieniona jako **Tak**. |
| **Znajduje się w tekście załącznika** | Jeśli dokument jest dołączonym w tekście wiadomości e-mail, ta wartość jest wymieniona jako **Tak**. |
| **Uczestnicy** | Wszystkie pola osób w wiadomości e-mail. Te pola to Od, Do, DW i UDW. |
| **Odebrano** | Data, do dnia, w który wiadomość e-mail została odebrana przez adresata. |
| **Domeny adresatów** | Lista wszystkich domen adresatów wiadomości. |
| **Adresaci** | Adresaci wiadomości e-mail. |
| **Nadawca** | Pole Nadawca (Od) dla typów wiadomości.  Format to **DisplayName \<SmtpAddress>**. |
| **Domena nadawcy** | Domena nadawcy. |
| **Do** | Pole Do wiadomości e-mail. |
| **Unikatowe w zestawie wiadomości e-mail** | Fałsz, jeśli w zestawie wiadomości e-mail znajduje się duplikat załącznika. |

## <a name="document-filters"></a>Filtry dokumentów

| **Filtry** | **Opis** |
|:---------------------|:----------------|
| **Etykiety zgodności** | Etykiety zgodności zastosowane w Office 365. |
| **Czas utworzenia (UTC)** | Data i godzina utworzenia pliku lub wiadomości e-mail. Data i godzina są dostępne we skoordynowanym czasie uniwersalnym (UTC). |
| **Data ostatniej modyfikacji (UTC)** | Data ostatniej zmiany dokumentu. Data i godzina są dostępne we skoordynowanym czasie uniwersalnym (UTC). |
| **Rozszerzenie pliku** | Typ rozszerzenia pliku. |
| **Zdarzenia aktywności użytkowników** | Działanie dotyczące elementów związanych z określoną aktywnością użytkownika w danym przypadku.  Na przykład po wybraniu linku do "Eksploruj zawartość" dla działania na stronie  Działania użytkownika w przypadku, ten filtr jest używany do wyświetlania elementów związanych z tym działaniem. |
| **Produkt służbowy** | Typ produktu służbowego dla dokumentu. Na przykład adnotacje lub tagi w dokumencie. |
