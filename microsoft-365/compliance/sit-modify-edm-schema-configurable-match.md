---
title: Modyfikowanie schematu dokładnego dopasowania danych w celu używania konfigurowalnego dopasowania
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak zmodyfikować schemat edm w celu używania konfigurowalnego dopasowania.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf11e60f3fce46926d297c97a44c7d494942d556
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009705"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Modyfikowanie schematu dokładnego dopasowania danych w celu używania konfigurowalnego dopasowania

Klasyfikacja oparta na danych (EDM, Exact Data Match) umożliwia tworzenie niestandardowych typów informacji poufnych, które odwołują się do dokładnych wartości w bazie danych informacji poufnych. Jeśli chcesz zezwolić na warianty dokładnego ciągu znaków, możesz użyć konfigurowalnego dopasowania, aby określić, Microsoft 365 ignorować literę, a niektóre ograniczniki.

> [!IMPORTANT]
> Ta procedura służy do modyfikowania istniejącego schematu i pliku danych EDM.

1. **OdinstalujEdmUploadAgent.exe** z komputera, z Microsoft 365 na potrzeby przekazywania plików danych i schematu EDM.

2. Pobierz odpowiedni **plikEdmUploadAgent.exe** twojej subskrypcji, korzystając z poniższych linków:
    - [Komercyjna + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) — większość klientów komercyjnych powinna używać tej
    - [GCC-wysoka —](https://go.microsoft.com/fwlink/?linkid=2137521) ta rozwiązanie jest przeznaczone specjalnie dla subskrybentów chmury o wysokim poziomie zabezpieczeń
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) — jest to przeznaczone specjalnie dla klientów w chmurze Działu Obrony Stanów Zjednoczonych

3. Autoryzuj agenta Upload usługi EDM, otwórz okno wiersza polecenia (jako administrator) i uruchom następujące polecenie:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Jeśli nie masz bieżącej kopii istniejącego schematu, musisz pobrać kopię istniejącego schematu. Uruchom to polecenie:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Dostosuj schemat, aby w każdej kolumnie używane są "caseInsensitive" i / lub "ignorowaneDelimiters".  Wartość domyślna dla ciągu "caseInsensitive" to "false", a dla "ignorowanychDelimiters" jest to pusty ciąg.

    > [!NOTE]
    > Źródłowy niestandardowy typ informacji poufnych lub wbudowany typ informacji poufnych używany do wykrywania ogólnego wzorca regex musi obsługiwać wykrywanie odmian danych wejściowych wymienionych zignorowanychDelimiters. Na przykład wbudowany amerykański numer PESEL (SSN) o typie informacji poufnych może wykrywać odmiany danych, które zawierają kreski, spacje lub brak odstępów między pogrupowanych numerami, które zawierają nazwę SSN. W efekcie jedynymi ogranicznikami, które należy uwzględnić w ignorowanych plikach EDM dla danych SSN, są: kreska i spacja.

    Oto przykładowy schemat, który symulowa dopasowanie bez uwzględniania wielkości liter przez utworzenie dodatkowych kolumn potrzebnych do rozpoznawania odmian wielkości liter w poufnych danych.

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
               <Field name="PolicyNumber" searchable="true" />
               <Field name="PolicyNumberLowerCase" searchable="true" />
               <Field name="PolicyNumberUpperCase" searchable="true" />
               <Field name="PolicyNumberCapitalLetters" searchable="true" />
      </DataStore>
    </EdmSchema>
    ```

    W powyższym przykładzie odmiany `PolicyNumber` oryginalnej kolumny nie będą już potrzebne, jeśli obie `caseInsensitive` zostaną `ignoredDelimiters` dodane.

    Aby zaktualizować ten schemat w celu używania flag i przez program EDM `caseInsensitive` `ignoredDelimiters` , można je skonfigurować jako zgodne.  Wygląda to następująco:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    Flaga `ignoredDelimiters` obsługuje dowolny znak niealalnumeryczny. Oto kilka przykładów:
    - \.
    - \-
    - \/
    - \_
    - \*
    - \^
    - \#
    - \!
    - \?
    - \[
    - \]
    - \{
    - \}
    - \\
    - \~
    - \;

    Flaga `ignoredDelimiters` nie obsługuje:
    - znaki 0-9
    - A–Z
    - a-z
    - \"
    - \,

6. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > Jeśli w Twojej organizacji klucz klienta został Microsoft 365 na poziomie dzierżawy (publiczna wersja [Zapoznawcza),](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) funkcja dokładnego dopasowania danych automatycznie użyje funkcji szyfrowania. Ta usługa jest dostępna tylko dla licencjonowanych dzierżawców usługi E5 w chmurze komercyjnej.

7. Zaktualizuj schemat, uruchamiając następujące polecenie:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. W razie potrzeby zaktualizuj plik danych, aby dopasować go do nowej wersji schematu.

    > [!TIP]
    > Opcjonalnie można uruchomić sprawdzanie poprawności pliku csv przed jego przekazaniem, uruchamiając program:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > Aby uzyskać więcej informacji na temat EdmUploadAgent.exe parametrów, uruchom
    >
    > `EdmUploadAgent.exe /?`

9. Otwórz okno wiersza polecenia (jako administrator) i uruchom następujące polecenie, aby skrótować i przekazać poufne dane:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>Artykuły pokrewne

- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Definicje typu jednostki informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Niestandardowe typy informacji poufnych](./sensitive-information-type-learn-about.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Usługa Microsoft Defender dla aplikacji w chmurze](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
