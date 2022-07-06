---
title: Modyfikowanie schematu dokładnego dopasowania danych w celu użycia konfigurowalnego dopasowania
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
description: Dowiedz się, jak zmodyfikować schemat edm w celu użycia konfigurowalnego dopasowania.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a90f81136bf6aa78aa11d732deca19ecd1d59b9c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622068"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Modyfikowanie schematu dokładnego dopasowania danych w celu użycia konfigurowalnego dopasowania

Klasyfikacja oparta na dokładnym dopasowaniu danych (EDM) umożliwia tworzenie niestandardowych typów informacji poufnych odwołujących się do dokładnych wartości w bazie danych informacji poufnych. Jeśli chcesz zezwolić na warianty dokładnego ciągu, możesz użyć *konfigurowalnego dopasowania* , aby poinformować usługę Microsoft Purview o ignorowaniu wielkości liter i niektórych ograniczników.

> [!IMPORTANT]
> Ta procedura służy do modyfikowania istniejącego schematu i pliku danych EDM.

1. Odinstaluj **EdmUploadAgent.exe** z komputera używanego do nawiązywania połączenia z usługą Microsoft 365 na potrzeby przekazywania schematu i pliku danych EDM.

2. Pobierz odpowiedni plik **EdmUploadAgent.exe** dla subskrypcji, korzystając z poniższych linków:
    - [Komercyjne i GCC](https://go.microsoft.com/fwlink/?linkid=2088639) — większość klientów komercyjnych powinna z tego korzystać
    - [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) — jest to przeznaczone specjalnie dla subskrybentów chmury dla instytucji rządowych o wysokim poziomie zabezpieczeń
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) — jest to przeznaczone specjalnie dla klientów w chmurze departamentu obrony Stany Zjednoczone

3. Autoryzuj agenta przekazywania EDM, otwórz okno wiersza polecenia (jako administrator) i uruchom następujące polecenie:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Jeśli nie masz bieżącej kopii istniejącego schematu, musisz pobrać kopię istniejącego schematu, uruchom następujące polecenie:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Dostosuj schemat tak, aby każda kolumna wykorzystywała "caseInsensitive" i /lub "ignoredDelimiters".  Wartość domyślna "caseInsensitive" to "false", a dla "ignoredDelimiters" jest pustym ciągiem.

    > [!NOTE]
    > Podstawowy niestandardowy typ informacji poufnych lub wbudowany typ informacji poufnych używany do wykrywania ogólnego wzorca regex musi obsługiwać wykrywanie danych wejściowych odmian wymienionych z ignorowanymiDelimiterami. Na przykład wbudowany typ informacji poufnych numeru ubezpieczenia społecznego (SSN) w SSN może wykrywać odmiany danych, które obejmują kreski, spacje lub brak spacji między zgrupowanymi numerami, które tworzą nazwę SSN. W związku z tym jedynymi ogranicznikami, które są istotne do uwzględnienia w ignorowanychdelimiterach EDM dla danych SSN, są: kreska i spacja.

    Oto przykładowy schemat, który symuluje dopasowanie bez uwzględniania wielkości liter, tworząc dodatkowe kolumny potrzebne do rozpoznawania odmian wielkości liter w danych poufnych.

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

    W powyższym przykładzie odmiany oryginalnej `PolicyNumber` kolumny nie będą już potrzebne, jeśli oba `caseInsensitive` `ignoredDelimiters` i zostaną dodane.

    Aby zaktualizować ten schemat tak, aby program EDM używał konfigurowalnego dopasowania, `caseInsensitive` użyj flag i `ignoredDelimiters` .  Oto jak to wygląda:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    Flaga `ignoredDelimiters` obsługuje dowolny znak inny niż alfanumeryczny. Oto kilka przykładów:
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
    - znaki 0–9
    - A-Z
    - a-z
    - \"
    - \,

6. [Połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > Jeśli Twoja organizacja skonfigurowała [klucz klienta dla platformy Microsoft 365 na poziomie dzierżawy (publiczna wersja zapoznawcza),](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) dokładne dopasowanie danych automatycznie użyje jej funkcji szyfrowania. Jest to dostępne tylko dla dzierżaw licencjonowanych E5 w chmurze komercyjnej.

7. Zaktualizuj schemat, uruchamiając następujące polecenie:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. W razie potrzeby zaktualizuj plik danych, aby był zgodny z nową wersją schematu.

    > [!TIP]
    > Opcjonalnie możesz uruchomić walidację pliku csv przed przekazaniem, uruchamiając polecenie:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > Aby uzyskać więcej informacji na temat wszystkich EdmUploadAgent.exe obsługiwanych parametrów, uruchom polecenie
    >
    > `EdmUploadAgent.exe /?`

9. Otwórz okno wiersza polecenia (jako administrator) i uruchom następujące polecenie, aby utworzyć skrót i przekazać poufne dane:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>Powiązane artykuły:

- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Niestandardowe typy informacji poufnych](./sensitive-information-type-learn-about.md)
- [Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
