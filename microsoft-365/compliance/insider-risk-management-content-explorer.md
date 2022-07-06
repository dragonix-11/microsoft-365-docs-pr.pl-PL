---
title: Insider risk management Eksplorator zawartości
description: Dowiedz się więcej na temat zarządzania ryzykiem wewnętrznym Eksplorator zawartości w usłudze Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: c193325608feef3bc8114b50af9d5e5832eb9d66
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642552"
---
# <a name="insider-risk-management-content-explorer"></a>Insider risk management Eksplorator zawartości

**Eksplorator zawartości** zarządzania ryzykiem wewnętrznym umożliwia użytkownikom przypisanym do roli *badaczy zarządzania ryzykiem niejawnym* sprawdzanie kontekstu i szczegółów zawartości skojarzonej z działaniem w alertach. Dane sprawy w Eksploratorze zawartości są odświeżane codziennie w celu uwzględnienia nowych działań. W przypadku wszystkich alertów potwierdzonych w danym przypadku kopie danych i plików komunikatów są archiwizowane jako migawka w czasie elementów przy zachowaniu oryginalnych plików i komunikatów w źródłach magazynu. W razie potrzeby pliki danych przypadku mogą być eksportowane jako przenośny plik dokumentu (PDF) lub w oryginalnym formacie pliku.

W przypadku nowych przypadków wypełnienie zawartości w Eksploratorze zawartości zwykle trwa około godziny. W przypadku dużych ilości zawartości utworzenie migawki może potrwać dłużej. Jeśli zawartość jest nadal ładowana w Eksploratorze zawartości, zostanie wyświetlony wskaźnik postępu, który wyświetla procent ukończenia.

W niektórych przypadkach dane skojarzone ze sprawą mogą nie być dostępne jako migawka do przeglądu w Eksploratorze zawartości. Taka sytuacja może wystąpić, gdy dane sprawy zostały usunięte lub przeniesione, lub gdy wystąpi tymczasowy błąd podczas przetwarzania danych sprawy. W takiej sytuacji wybierz pozycję **Wyświetl pliki** na pasku ostrzegawczym, aby wyświetlić nazwy plików, ścieżkę pliku i przyczynę niepowodzenia dla każdego pliku. W razie potrzeby te informacje można wyeksportować do pliku .csv (wartości rozdzielone przecinkami).

Jeśli zawartość zawiera uprawnienia do zarządzania prawami do informacji, te uprawnienia są zachowywane dla skopiowanej zawartości, a użytkownicy *przypisani do roli Badacze zarządzania ryzykiem wewnętrznym* będą potrzebować tych uprawnień i praw, jeśli będą musieli otworzyć i wyświetlić pliki. Do każdego pliku i komunikatu jest automatycznie przypisywany unikatowy identyfikator pliku w przypadku zarządzania ryzykiem wewnętrznym do celów zarządzania. Dokumenty skojarzone z działaniami wskaźnika urządzenia nie są uwzględniane w Eksploratorze zawartości.

> [!NOTE]
> Eksplorator zawartości obejmuje działania użytkowników związane z plikami usługi Microsoft 365, takie jak aktywność użytkowników w programach SharePoint, Exchange, Microsoft Teams i OneDrive dla Firm.

## <a name="column-options"></a>Opcje kolumn

Aby ułatwić analitykom ryzyka i badaczom przeglądanie przechwyconych danych i komunikatów oraz przeglądanie kontekstu sprawy, w Eksploratorze zawartości znajduje się kilka narzędzi do filtrowania i sortowania. W przypadku sortowania podstawowego kolumny **klasy Date** i **File** obsługują sortowanie przy użyciu tytułów kolumn w okienku kolejki zawartości. Inne kolumny kolejki są dostępne do dodania do widoku, aby zapewnić różne tabele przestawne dla plików i komunikatów.

Aby dodać lub usunąć nagłówki kolumn dla kolejki zawartości, użyj kontrolki **Edytuj kolumny** i wybierz z następujących opcji kolumn. Te kolumny są mapowane na typowe warunki właściwości poczty e-mail i dokumentu obsługiwane w Eksploratorze zawartości i wymienione w dalszej części tego artykułu.

| **Opcja Kolumna** | **Opis** |
|:------------------|:----------------|
| **Autor** | Pole autora z dokumentów pakietu Office, które jest utrwalane w przypadku skopiowania dokumentu. Jeśli na przykład użytkownik utworzy dokument i wyśle go pocztą e-mail do innej osoby, która następnie przekaże go do programu SharePoint, dokument będzie nadal zachowywać pierwotnego autora. |
| **Udw** | Dostępne dla wiadomości e-mail, użytkowników w polu wiadomości Bcc. |
| **Cc** | Dostępne dla wiadomości e-mail, użytkowników w polu Wiadomości DW. |
| **Ścieżka złożona** | Ścieżka czytelna dla człowieka opisująca źródło elementu. |
| **Identyfikator konwersacji** | Identyfikator konwersacji z wiadomości. |
| **Indeks konwersacji** | Indeks konwersacji z wiadomości. |
| **Czas utworzenia** | Czas utworzenia pliku lub wiadomości e-mail. |
| **Data (UTC)** | W przypadku wiadomości e-mail data odebrania wiadomości przez adresata lub wysłania przez nadawcę. W przypadku dokumentów data ostatniej modyfikacji dokumentu. Data jest wyrażona w uniwersalnym czasie koordynowanym (UTC).|
| **Motyw dominujący** | Motyw dominujący obliczony na potrzeby analizy. |
| **Identyfikator zestawu wiadomości e-mail** | Identyfikator grupy dla wszystkich wiadomości w tym samym zestawie poczty e-mail. |
| **Identyfikator rodziny** | Identyfikator rodziny grupuje wszystkie elementy; w przypadku wiadomości e-mail ta kolumna zawiera wiadomość i wszystkie załączniki; W przypadku dokumentów ta kolumna zawiera dokument i wszystkie elementy osadzone. |
| **Klasa plików** | W przypadku zawartości z programu SharePoint i usługi OneDrive: **Dokument**; dla zawartości z programu Exchange: **adres e-mail** lub **załącznik**. |
| **Identyfikator pliku** | Identyfikator dokumentu jest unikatowy w przypadku. |
| **Ikona typu pliku** | Rozszerzenie pliku; na przykład docx, one, pptx lub xlsx. To pole jest tą samą właściwością co właściwość witryny FileExtension. |
| **ID** | Identyfikator GUID pliku. |
| **Niezmienny identyfikator** | Niezmienny identyfikator przechowywany w Office 365. |
| **Typ inkluzywny** | Typ inkluzywny obliczany na potrzeby analizy: **0** — nie inkluzywny; **1** — inkluzywne; **2** — włącznie minus; **3** — kopiowanie inkluzywne. |
| **Ostatnia modyfikacja** | Data ostatniej zmiany dokumentu. |
| **Oznaczony jako reprezentatywny** | Jeden dokument z każdego zestawu dokładnych duplikatów jest oznaczony jako przedstawiciele. |
| **Rodzaj komunikatu** | Typ wiadomości e-mail do wyszukania. Możliwe wartości: kontakty, dokumenty, poczta e-mail, dane zewnętrzne, faksy, wiadomości błyskawiczne, dzienniki, spotkania, zespoły microsoft (zwraca elementy z czatów, spotkań i połączeń w usłudze Microsoft Teams), notatki, posty, kanały informacyjne RSS, zadania, poczta głosowa |
| **Uczestników** | Lista wszystkich uczestników wiadomości; na przykład Sender, To, Cc, Bcc. |
| **Identyfikator tabeli przestawnej** | Identyfikator tabeli przestawnej. |
| **Otrzymał** | Data odebrania wiadomości e-mail przez adresata. To pole jest tą samą właściwością co właściwość Odebrana wiadomość e-mail. |
| **Adresatów** | Wszystkie pola adresatów w wiadomości e-mail. Te pola to To, Cc i Bcc. |
| **Identyfikator przedstawiciela** | Identyfikator liczbowy każdego zestawu dokładnych duplikatów. |
| **Nadawcy** | Nadawca wiadomości e-mail. |
| **Nadawca/autor** | W przypadku wiadomości e-mail osoba, która wysłała wiadomość. W przypadku dokumentów osoba cytowana w polu autora z dokumentów pakietu Office. Możesz wpisać więcej niż jedną nazwę rozdzieloną przecinkami. Co najmniej dwie wartości są logicznie połączone przez operator OR. |
| **Typy informacji poufnych** | Typy informacji poufnych zidentyfikowane w zawartości. |
| **Etykiety wrażliwości** | Etykiety poufności zastosowane do zawartości. |
| **Wysłane** | Data wysłania wiadomości e-mail przez nadawcę. To pole jest tą samą właściwością co właściwość Wysłane wiadomości e-mail. |
| **Rozmiar** | W przypadku poczty e-mail i dokumentów rozmiar elementu (w bajtach). |
| **Temat** | Tekst w wierszu tematu wiadomości e-mail. |
| **Temat/tytuł** | W przypadku wiadomości e-mail tekst w wierszu tematu wiadomości. W przypadku dokumentów tytuł dokumentu. Jak wyjaśniono wcześniej, właściwość Title jest metadanymi określonymi w dokumentach pakietu Microsoft Office. Możesz wpisać nazwę więcej niż jednego tematu/tytułu rozdzielonego przecinkami. Co najmniej dwie wartości są logicznie połączone przez operator OR. |
| **Lista motywów** | Lista motywów obliczana na potrzeby analizy. |
| **Tytuł** | Tytuł dokumentu. Właściwość Title to metadane określone w dokumentach pakietu Office. Różni się od nazwy pliku dokumentu. |
| **Do** | Adresat wiadomości e-mail w polu Do. |

## <a name="filtering"></a>Filtrowanie

Możesz użyć co najmniej jednego filtru, aby zawęzić zakres wyszukiwania i zwrócić bardziej wyrafinowany zestaw wyników. Aby ustawić filtr, wybierz pozycję **Filtry** w górnej części kolejki zawartości. Wiele filtrów zawiera dodatkowe opcje filtrowania, które ułatwiają zawężenie wyników zwracanych przez filtr. Na przykład filtr *Data* zawiera kontrolki umożliwiające skonfigurowanie *daty rozpoczęcia* i *daty zakończenia* dla filtru **Data** . Wybierz co najmniej jeden element filtru z następujących kategorii:

### <a name="common-filters"></a>Typowe filtry

| **Filtrowanie** | **Opis** |
|:---------------------|:----------------|
| **Data (UTC)** | W przypadku wiadomości e-mail data odebrania wiadomości przez adresata lub wysłania przez nadawcę. W przypadku dokumentów data ostatniej modyfikacji dokumentu. |
| **Nadawca/autor** | W przypadku wiadomości e-mail osoba, która wysłała wiadomość. W przypadku dokumentów osoba cytowana w polu *Autor* z dokumentów pakietu Office. Możesz wpisać więcej niż jedną nazwę rozdzieloną przecinkami. |
| **Źródło** | Lokalizacja dokumentu w organizacji. Na przykład określona lokalizacja witryny programu SharePoint. |
| **Temat/tytuł** | W przypadku wiadomości e-mail tekst w wierszu tematu wiadomości. W przypadku dokumentów tytuł dokumentu. Właściwość Title w dokumentach to metadane określone w dokumentach pakietu Microsoft Office. Możesz wpisać nazwę więcej niż jednego tematu/tytułu rozdzielonego przecinkami. Co najmniej dwie wartości są logicznie połączone przez operator OR. |

### <a name="email-filters"></a>Filtry poczty e-mail

| **Filtrowanie** | **Opis** |
|:---------------------|:----------------|
| **Udw** | Pole Bcc wiadomości e-mail. |
| **Cc** | Pole DW wiadomości e-mail. |
| **Ma załącznik** | Wskazuje, czy wiadomość ma załącznik. Wartości są wyświetlane jako **true** lub **false**. |
| **Jest załącznik wiadomości e-mail** | Jeśli dokument jest załącznikiem, wartość jest wyświetlana jako **Tak**. |
| **Jest dokumentem osadzonym** | Jeśli dokument jest osadzony w wiadomości e-mail, wartość jest wyświetlana jako **Tak**. |
| **Jest załącznik w tekście** | Jeśli dokument jest wbudowanym załącznikiem w wiadomości e-mail, wartość jest wyświetlana jako **Tak**. |
| **Uczestników** | Wszystkie pola osób w wiadomości e-mail. Te pola to From, To, Cc i Bcc. |
| **Otrzymał** | Data odebrania wiadomości e-mail przez adresata. |
| **Domeny adresatów** | Lista wszystkich domen adresatów wiadomości. |
| **Adresatów** | Adresaci wiadomości e-mail. |
| **Nadawcy** | Pole nadawcy (od) dla typów komunikatów.  Format to **DisplayName \<SmtpAddress>**. |
| **Domena nadawcy** | Domena nadawcy. |
| **Do** | Pole Do wiadomości e-mail. |
| **Unikatowy w zestawie poczty e-mail** | Fałsz, jeśli w zestawie poczty e-mail znajduje się duplikat załącznika. |

## <a name="document-filters"></a>Filtry dokumentów

| **Filtry** | **Opis** |
|:---------------------|:----------------|
| **Etykiety zgodności** | Etykiety zgodności stosowane w Office 365. |
| **Czas utworzenia (UTC)** | Data i godzina utworzenia pliku lub wiadomości e-mail. Data i godzina znajdują się w uniwersalnym czasie koordynowanym (UTC). |
| **Data ostatniej modyfikacji (UTC)** | Data ostatniej zmiany dokumentu. Data i godzina znajdują się w uniwersalnym czasie koordynowanym (UTC). |
| **Formatem** | Typ rozszerzenia pliku. |
| **Zdarzenia działania użytkownika** | Działanie dla elementów związanych z określoną aktywnością użytkownika w danym przypadku.  Na przykład po wybraniu linku do elementu "Eksploruj zawartość" dla działania na stronie **Aktywność użytkownika** przypadku ten filtr służy do wyświetlania elementów związanych z tym działaniem. |
| **Produkt roboczy** | Typ produktu roboczego dla dokumentu. Na przykład adnotacje lub tagi w dokumencie. |
