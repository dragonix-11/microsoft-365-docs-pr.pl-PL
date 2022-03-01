---
title: Ładowanie danych nie Microsoft 365 do zestawu recenzji
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak zaimportować dane Microsoft 365 do zestawu recenzji do analizy w przypadku Advanced eDiscovery przypadku.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39f91846e42bb2403c2b1faf7fd98ff3e7759182
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010413"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Ładowanie danych nie Microsoft 365 do zestawu recenzji

Nie wszystkie dokumenty, które należy analizować w programie Advanced eDiscovery znajdują się w Microsoft 365. Dzięki funkcji importowania Microsoft 365 danych w programie Advanced eDiscovery możesz przekazywać dokumenty, które nie znajdują się w tym Microsoft 365 do zestawu recenzji. W tym artykule pokazano, jak wprowadzić dokumenty niezwiązy Microsoft 365 do Advanced eDiscovery analizy.

## <a name="requirements-to-upload-non-office-365-content"></a>Wymagania dotyczące przekazywania zawartości Office 365 zawartości

Aby korzystać z funkcji przekazywania niezwiązywistej Microsoft 365 opisanej w tym artykule, wymagane są następujące elementy:

- Wszystkim opiekunom, którym chcesz skojarzyć zawartość niezwiązywoną Microsoft 365, należy przypisać odpowiednią licencję. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- Istniejąca Advanced eDiscovery przypadku.

- Aby można było przekazywać i skojarzyć dane, które nie Microsoft 365 do sprawy, należy je dodać do sprawy.

- Dane inne Microsoft 365 muszą być typami plików obsługiwanymi przez Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz [Obsługiwane typy plików Advanced eDiscovery](supported-filetypes-ediscovery20.md).

- Wszystkie pliki przekazane do zestawu recenzji muszą znajdować się w folderach, w których każdy folder jest skojarzony z określoną skojarzoną skojarzoną z nim skojarzoną z określoną folderem. Nazwy tych folderów muszą mieć następujący format nazewnictwa: nazwa *alias@domainname*. Ta alias@domainname musi być aliasem Microsoft 365 domeny i aliasem użytkownika. Możesz zebrać wszystkie foldery alias@domainname w folderze głównym. Folder główny może zawierać tylko foldery alias@domainname foldery. Luźne pliki w folderze głównym nie są obsługiwane.

   Struktura folderów dla danych innych niż Microsoft 365, które chcesz przekazać, będzie podobna do poniższego przykładu:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Jeśli abraham.mcmahon@contoso.com, jewell.gordon@contoso.com i staci.gonzalez@contoso.com to adresy SMTP adresatów w tym przypadku.

   ![Nie Microsoft 365 struktury folderów przekazywania danych.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- Konto przypisane do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych (i dodane jako administrator zbierania elektronicznych materiałów dowodowych).

- Narzędzie AzCopy w wersji 8.1 zainstalowane na komputerze, który ma dostęp do struktury Microsoft 365 zawartości. Aby zainstalować aplikację AzCopy, zobacz [Przenoszenie danych za pomocą programu AzCopy w wersji 8.1 na Windows](/previous-versions/azure/storage/storage-use-azcopy). Pamiętaj, aby zainstalować narzędzie AzCopy w lokalizacji domyślnej **: %ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**. Należy użyć programu AzCopy w wersji 8.1. Inne wersje programu AzCopy mogą nie działać podczas ładowania danych innych niż Microsoft 365 w programie Advanced eDiscovery.


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>Upload zawartości, która nie Microsoft 365, do Advanced eDiscovery

1. Jako administrator zbierania elektronicznych materiałów dowodowych lub menedżer zbierania elektronicznych materiałów dowodowych otwórz Advanced eDiscovery i przejdź do sprawy, do Microsoft 365 dane, które nie zostaną przekazane.  

2. Kliknij **pozycję Zestawy** recenzji, a następnie wybierz zestaw recenzji, aby przekazać do Microsoft 365 dane bez recenzji.  Jeśli nie masz zestawu recenzji, możesz go utworzyć. 
 
3. Otwórz zestaw recenzji, klikając go lub zaznaczając i klikając pozycję **Otwórz zestaw recenzji**.

4. W zestawie recenzji **kliknij pozycję Zarządzaj** zestawem recenzji (strzałka w dół zaraz  za opcją Akcje), a następnie kliknij opcję Dane Office 365 **inne**.

5. Kliknij **Upload,** aby uruchomić kreatora importu danych.

   ![Upload plików.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   Pierwszy krok kreatora tworzy bezpieczną lokalizację przekazywania plików Storage platformy Azure podaną przez firmę Microsoft.  Po zakończeniu przygotowywania przycisk Następne **: Upload pliki** stanie się aktywny.

   ![Inne niż Microsoft 365 Importowanie: Przygotowywanie.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Kliknij **przycisk Dalej: Upload pliki**.

6. Na **stronie Upload plików** wykonaj następujące czynności:

   ![Inne niż Microsoft 365 Importowanie: Upload pliki.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. W **polu Ścieżka do lokalizacji** plików sprawdź lub wpisz lokalizację folderu głównego, w którym są przechowywane dane, które nie Microsoft 365 przekazać. Na przykład dla lokalizacji plików przykładowych pokazanych w sekcji Przed rozpoczęciem wpisz **%USERPROFILE\Downloads\no365**. Podanie odpowiedniej lokalizacji zapewnia, że polecenie AzCopy wyświetlane w polu pod ścieżką jest poprawnie aktualizowane.

   b. Kliknij **pozycję Kopiuj do schowka** , aby skopiować polecenie wyświetlane w polu.

7. Uruchom wiersz Windows polecenia, wklej polecenie skopiowane w poprzednim kroku, a następnie naciśnij klawisz **Enter**, aby uruchomić polecenie AzCopy.  Po uruchomieniu polecenia pliki, które nie Microsoft 365, zostaną przekazane do lokalizacji usługi Azure Storage przygotowanej w kroku 4.

   ![Inne niż Microsoft 365 import: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Jak wspomniano wcześniej, należy użyć programu AzCopy w wersji 8.1, aby pomyślnie użyć polecenia podanego na Upload **plikach**. Jeśli podane polecenie AzCopy nie powiedzie się, zobacz Rozwiązywanie [problemów z azCopy w programie Advanced eDiscovery](troubleshooting-azcopy.md).

8. Wróć do menu Centrum zgodności platformy Microsoft 365 i kliknij przycisk **Dalej: Przetwarzaj pliki** w kreatorze.  Inicjuje to przetwarzanie, wyodrębnianie tekstu i indeksowanie plików innych niż Microsoft 365, które zostały przekazane do lokalizacji usługi Azure Storage danych.  

9. Śledź postęp przetwarzania plików na stronie Proces plików  lub na karcie Zadania, wyświetlając zadanie o nazwie Dodawanie danych innych niż Microsoft 365 do **zestawu recenzji**.  Po zakończeniu zadania nowe pliki będą dostępne w zestawie recenzji.

   ![Inne niż Microsoft 365 Importowanie: przetwarzaj pliki.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. Po zakończeniu przetwarzania możesz zamknąć kreatora.
