---
title: Eksportuj dane źródłowe dla dokładnego typu informacji poufnych opartych na dopasowaniu danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak eksportować dane źródłowe pod kątem dokładnego typu informacji poufnych zgodnych z danymi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 913870afeef443c5b346172099b0cd47db13e52e
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760696"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Eksportuj dane źródłowe dla dokładnego typu informacji poufnych opartych na dopasowaniu danych


Tabela danych poufnych to plik tekstowy zawierający wiersze wartości, z którymi będziesz porównywać zawartość w dokumentach w celu identyfikowania poufnych danych. Te wartości mogą być danymi osobowymi, rekordami produktów lub innymi poufnymi danymi w postaci tekstowej, które chcesz wykryć w zawartości i podjąć działania ochronne.

Po wyeksportowaniu danych w jednym z obsługiwanych formatów możesz kontynuować tworzenie schematu EDM.

## <a name="defining-your-edm-sensitive-type"></a>Definiowanie typu wrażliwego na EDM

Podczas definiowania typu wrażliwego EDM jedną z najważniejszych decyzji jest to, które pola będą polami podstawowymi. Pola podstawowe muszą być zgodne z wykrywalnym wzorcem i definiowane jako pola (kolumny) z możliwością wyszukiwania w schemacie EDM. Pola pomocnicze nie muszą być zgodne z żadnym wzorcem, ponieważ zostaną porównane ze wszystkimi tekstami otaczającymi dopasowania do pól podstawowych.

Te reguły ułatwiają określenie kolumn, których należy używać jako pól podstawowych:

- Jeśli musisz wykryć poufne dane na podstawie obecności pojedynczej wartości pasującej do pola w poufnej tabeli danych, niezależnie od obecności innych poufnych danych otaczających tę kolumnę, ta kolumna musi być zdefiniowana jako podstawowy element dla typu EDM. 
- Jeśli wiele kombinacji różnych pól w poufnej tabeli danych musi zostać wykrytych w zawartości, zidentyfikuj kolumny, które są wspólne dla większości takich kombinacji, i określ je jako podstawowe elementy i kombinacje innych pól jako elementy pomocnicze.
- Jeśli kolumna, której chcesz użyć jako pola podstawowego, nie jest zgodna z wykrywalnym wzorcem, takim jak dowolny ciąg tekstowy lub jest zgodna z wykrywalnymi wzorcami, które byłyby obecne w dużej części dokumentów lub wiadomości e-mail, spróbuj wybrać inne lepiej ustrukturyzowane kolumny jako elementy podstawowe.

Jeśli na przykład masz kolumny `full name`, , `date of birth``account number`, i `Social Security Number`, nawet jeśli pierwszą i ostatnią nazwą są kolumny, które będą wspólne dla różnych kombinacji danych, które chcesz wykryć, takie ciągi nie są zgodne z łatwo rozpoznawalnymi wzorcami i mogą być trudne do zdefiniowania jako typ informacji poufnych. Dzieje się tak, ponieważ niektóre nazwy mogą nawet nie zaczynać się wielkimi literami, mogą być tworzone przez dwa, trzy lub więcej słów, a nawet mogą zawierać cyfry lub inne znaki nie alfabetyczne. Datę urodzenia można łatwiej zidentyfikować, ale ponieważ każda wiadomość e-mail i większość dokumentów będzie zawierać co najmniej jedną datę, nie jest również dobrym kandydatem. Numery ubezpieczenia społecznego i numery kont są dobrymi kandydatami do użycia jako pole podstawowe.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Zapisywanie poufnych danych w formacie .csv, tsv lub rozdzielanym potokami

1. Zidentyfikuj informacje poufne, których chcesz użyć. Wyeksportuj dane do aplikacji, takie jak Microsoft Excel, i zapisz plik w pliku tekstowym. Plik można zapisać w formacie .csv (wartości rozdzielane przecinkami), tsv (wartości rozdzielone tabulatorami) lub rozdzielanych potokami (|). Format tsv jest zalecany w przypadkach, gdy wartości danych mogą zawierać przecinki, takie jak adresy ulic.
Plik danych może zawierać maksymalnie:
   - Maksymalnie 100 milionów wierszy poufnych danych
   - Maksymalnie 32 kolumny (pola) na źródło danych
   - Maksymalnie 5 kolumn (pól) oznaczonych jako możliwe do wyszukiwania

2. Ustrukturyzuj dane poufne w pliku .csv lub tsv, tak aby pierwszy wiersz zawierał nazwy pól używanych do klasyfikacji opartej na rozwiązaniu EDM. W pliku mogą znajdować się nazwy pól, takie jak "ssn", "birthdate", "firstname", "lastname". Nazwy nagłówków kolumn nie mogą zawierać spacji ani podkreślenia. Przykładowy plik .csv używany w tym artykule nosi nazwę *PatientRecords.csv*, a jego kolumny to *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN* i inne.

3. Zwróć uwagę na format pól danych poufnych. W szczególności pola, które mogą zawierać przecinki w ich zawartości, na przykład adres ulicy zawierający wartość "Seattle,WA" zostanie przeanalizowany jako dwa oddzielne pola po przeanalizowaniu, jeśli wybrano format .csv. Aby tego uniknąć, użyj formatu tsv lub otoczył przecinek zawierający wartości podwójnym cudzysłowem w tabeli danych poufnych. Jeśli przecinki zawierające wartości zawierają również spacje, musisz utworzyć niestandardowy interfejs SIT zgodny z odpowiednim formatem. Na przykład sit, który wykrywa ciąg wielosłowny z przecinkami i spacjami w nim.

## <a name="next-step"></a>Następny krok

- [Twórz schemat dla dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
