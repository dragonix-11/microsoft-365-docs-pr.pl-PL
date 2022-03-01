---
title: Test package guidelines
description: Przejrzyj wytyczne dotyczące pakietu testowego
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 0b5e69a245b21f4f6985eb54ca865b602059cba8
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016028"
---
# <a name="test-package-guidelines"></a>Test package guidelines

## <a name="1-script-referencing"></a>1. Odwołanie do skryptu

Podczas przekazywania pliku .zip do portalu rozpakuje się cała jego zawartość do folderu głównego. Nie musisz pisać żadnego kodu, aby wykonać tę początkową operację rozpakowania. Możesz też odwołać się do dowolnego pliku w pliku .zip, używając ścieżki względem przekazanego pliku zip.

W poniższym przykładzie pokażemy, jak można odwoływać się do danych binralnych/skryptów z pola wprowadzania na karcie Zadania. Tekst w kolorze niebieskim powinien zostać wprowadzony w polu Ścieżka **skryptu** **bez cudzysłowów.**

Ważne jest, aby przed przekazaniem pliku zip wiedzieć, jaka jest jego zawartość. Często podczas spakowania folderu na komputerze lokalnym jest tworzyć folder główny pod plikiem zip. W tym przypadku odwołania będą wyświetlane jako pogrubione **poniżej:**

**Contoso_App_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 — **"Contoso_App_Folder/ScriptX.ps1"**
- Script.ps1 - **"Contoso_App_Folder/folder1/script.ps1"**

W innych momentach plik zip może zawierać Twoje pliki lub zawartość bezpośrednio pod nim (na przykład nie ma folderu drugiego poziomu):

**Zip_file_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 — **"ScriptX.ps1"**
- Script.ps1 - **"folder1/script.ps1"**

## <a name="2-script-execution"></a>2. Wykonywanie skryptów

**Testy podczas pracy w pudełku:** Pakiet aplikacji musi zawierać co najmniej trzy skrypty programu PowerShell. Te skrypty będą wykonywać nienadzorowane instalowanie, uruchamianie i zamykanie aplikacji oraz jej zależności. Każdy skrypt powinien obsługiwać sprawdzanie własnych wymagań wstępnych, sprawdzanie poprawności własnych sukcesów i oczyszczanie po sobie (w razie potrzeby).

**Testy funkcjonalności:** Pakiet aplikacji musi zawierać co najmniej jeden skrypt programu PowerShell. Jeśli podano więcej niż jeden skrypt, skrypty są uruchamiane w sekwencji przekazywania, a niepowodzenie w określonym skrypcie zatrzyma wykonywanie kolejnych skryptów.

### <a name="script-requirements"></a> Wymagania dotyczące skryptu

- PowerShell w wersji 5.1+
- Nienadzorowane wykonywanie
- Kod zwrotu błędu
- Sprawdź poprawność sukcesu
- Rejestrowanie do określonego folderu dziennika dla skryptu

Aby pomyślnie wykonać w potoku testowym, każdy skrypt musi zostać uruchomiony bez nadzoru (bez monitów użytkowników).

> [!NOTE]
> W przypadku wystąpienia błędu podczas wykonywania skrypty powinny zwracać wartość "0" po pomyślnym ukończeniu oraz kod błędu niezerowego.

Każdy skrypt powinien sprawdzić, czy pomyślnie go uruchomiono. Na przykład skrypt instalacji powinien sprawdzić, czy istnieją w systemie pewne binarnie i/lub klucze rejestru po zakończeniu wykonywania pliku binarnego instalatora. Ten proces sprawdza się w rozsądnym stopniu, co do tego, czy instalacja powiodła się.

Sprawdzanie poprawności jest niezbędne do poprawnego diagnozowania błędów podczas uruchamiania testu. Jeśli na przykład skrypt nie może pomyślnie zainstalować aplikacji i nie można go uruchomić.

> [!IMPORTANT]
> **Należy unikać następujących czynności:** Skrypty nie powinny ponownie uruchamiać komputera. Jeśli jest konieczne ponowne uruchomienie, określ to podczas przekazywania skryptów.

## <a name="3-log-collection"></a>3. Zbieranie dziennika

Każdy skrypt powinien wytworzyć wszystkie generowane przez niego dzienniki do folderu o nazwie `logs`. Wszystkie foldery w katalogu o nazwie `logs` zostaną skopiowane i przedstawione do pobrania na `Test Results` stronie.

Na przykład skrypt instalacji (który może się znaleźć w katalogu aplikacji **/skryptów/install** ) może wyrejestrować swoje dzienniki do pliku: **logs/install.log**, tak aby ostateczny dziennik znajdował się na stronie: **Apps/scripts/install/logs/install.log**

System pobierze plik wraz `install.log` `logs` z innymi plikami z innych folderów i zs sortuje go do pobrania.

## <a name="4-application-binaries"></a>4. Binaries aplikacji

Każdy plik zip powinien zawierał wszystkie pliki binarne i zależności.

Te pliki binarne powinny zawierać wszystko, co niezbędne do zainstalowania aplikacji (na przykład instalatora aplikacji). Jeśli aplikacja ma zależność od jakichkolwiek platform, takich jak .NET Core/Standard lub .NET Framework, te struktury powinny być zawarte w pliku i prawidłowo odwoływać się do nich we podanych skryptach.

> [!NOTE]
> Przekazany plik zip nie może mieć w nazwie żadnych spacji ani znaków specjalnych

## <a name="5-applicationtest-rules"></a>5. Reguły aplikacji/testu

Aby Twoje aplikacje/testy działały poprawnie w ramach infrastruktury bazy testowej, muszą być zgodne z regułami opisanymi w zasadach [aplikacji/testowania ](rules.md). 

## <a name="next-steps"></a>Następne kroki

Przejść do następnego artykułu, aby wyświetlić niektóre **często zadawane pytania (często zadawane pytania)**
> [!div class="nextstepaction"]
> [Następny krok](faq.md)
