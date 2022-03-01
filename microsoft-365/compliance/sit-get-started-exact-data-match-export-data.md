---
title: Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak wyeksportować dane źródłowe, aby uzyskać dokładne dopasowanie danych na podstawie typu informacji poufnych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8253ff73d53100c986a2bd8580830703c9f4b363
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014742"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych


Tabela danych poufnych to plik tekstowy zawierający wiersze wartości, z którymi będzie porównywana zawartość w dokumentach w celu zidentyfikowania poufnych danych. Te wartości mogą umożliwiać identyfikację danych osobowych, rekordów produktów lub innych poufnych danych w postaci tekstowej, które chcesz wykryć w zawartości i podjąć działania zabezpieczające.

Po wyeksportowaniu danych w jednym z obsługiwanych formatów możesz przystąpić do utworzenia schematu EDM.

## <a name="defining-your-edm-sensitive-type"></a>Definiowanie typu poufnego w programie EDM

Podczas definiowania typu poufnego informacji w programie EDM jedną z najważniejszych decyzji jest to, które pola będą polami podstawowymi. Pola podstawowe muszą być zgodne ze wzorcem wykrywalnym i zostać zdefiniowane jako pola (kolumny) można wyszukiwać w schemacie EDM. Pola pomocnicze nie muszą być zgodne ze wzorcem, ponieważ będą porównywane ze wszystkimi otaczającymi je tekstami i polami podstawowymi.

Poniższe reguły ułatwiają podjęcie decyzji o tym, których kolumn należy użyć jako pól podstawowych:

- Jeśli trzeba wykryć poufne dane na podstawie obecności jednej wartości pasującej do pola w tabeli danych poufnych, niezależnie od obecności innych otaczających ją danych poufnych, ta kolumna musi być zdefiniowana jako element podstawowy dla typu danych EDM. 
- Jeśli w zawartości jest wykrywanych wiele kombinacji różnych pól w tabeli danych poufnych, należy zidentyfikować kolumny wspólne dla większości takich kombinacji i wyznaczyć je jako elementy podstawowe oraz kombinacje innych pól na elementy pomocnicze.
- Jeśli kolumna, której chcesz użyć jako pola podstawowego, nie działa zgodnie z wykrywalnym wzorcem, tak jak dowolny ciąg tekstowy lub jest zgodna z wykrywalnymi wzorcami, które byłyby tam obecne w dużej części dokumentów lub wiadomości e-mail, spróbuj wybrać inne lepiej ustrukturyzowane kolumny jako elementy podstawowe.

`full name`Jeśli na przykład masz kolumny , `date of birth`, `account number`i , `Social Security Number`nawet jeśli imiona i nazwiska to kolumny wspólne dla różnych kombinacji danych, które chcesz wykryć, takie ciągi nie są łatwa do zidentyfikowania wzorców i ich zdefiniowanie jako typu informacji poufnych może być trudne. Wynika to z tego, że niektóre nazwy mogą nie zaczynać się od wielkich liter, mogą zostać utworzone za pomocą dwóch, trzech lub większej liczby wyrazów, a nawet zawierać cyfry lub inne znaki niekońcowe. Daty urodzenia można łatwiej zidentyfikować, ale ponieważ każda wiadomość e-mail i większość dokumentów będzie zawierać co najmniej jedną datę, również nie jest dobrym kandydatem. Numery PESEL i konta to dobre kandydaty do użycia jako pole podstawowe.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Zapisywanie poufnych danych w .csv, tsv lub rozdzielanych potokami

1. Zidentyfikuj informacje poufne, których chcesz użyć. Wyeksportuj dane do aplikacji, na przykład Microsoft Excel, i zapisz plik w pliku tekstowym. Plik można zapisać w formacie .csv (wartości rozdzielane przecinkami), tsv (wartości rozdzielane tabulatorami) lub w formacie | potokowym. Format tsv jest zalecany w przypadkach, gdy wartości danych mogą zawierać przecinki, na przykład adresy pocztowe.
Plik danych może zawierać maksymalnie:
   - Maksymalnie 100 milionów wierszy poufnych danych
   - Maksymalnie 32 kolumny (pola) na źródło danych
   - Maksymalnie 5 kolumn (pól) oznaczonych jako można wyszukiwać

2. Nadaj poufne dane w pliku .csv lub tsv tak, aby pierwszy wiersz zawierał nazwy pól używanych na podstawie klasyfikacji opartej na układzie EDM. Plik może zawierać nazwy pól, takie jak "ssn", "dataurodze", "imię", "nazwisko". Nazwy nagłówków kolumn nie mogą zawierać spacji ani podkreśleń. Na przykładowy plik .csv, który został przez nas wybrany w tym artykule, nosi nazwę *PatientRecords.csv, a* jego kolumny to między innymi *PATIENTID*, *MRN*, *LastName*, *FirstName*, *SSN*.

3. Zwróć uwagę na format pól danych poufnych. W szczególności pola, które mogą zawierać przecinki w swojej zawartości, na przykład adres, który zawiera wartość "Szczecin,WA", zostaną rozsyłane jako dwa oddzielne pola podczas analizy, jeśli zostanie .csv format ulicy. Aby tego uniknąć, należy użyć formatu tsv lub otoczyć przecinek zawierający wartości cudzysłowami podwójnymi w tabeli danych poufnych. Jeśli przecinek zawierający również wartości zawiera spacje, musisz utworzyć niestandardowy sit odpowiadający odpowiadającemu mu formatowi. Na przykład funkcja SIT wykrywa ciąg wielosłowny zawierający przecinki i spacje.

## <a name="next-step"></a>Następny krok

- [Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do dokładnych typów informacji poufnych opartych na danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
