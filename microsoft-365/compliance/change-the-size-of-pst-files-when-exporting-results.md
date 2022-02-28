---
title: Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 10/12/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 04e9de2d-765b-457b-a98a-d0f60bfb13f2
description: Możesz zmienić domyślny rozmiar plików PST pobieranych na komputer podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: b0376a423827df855af83375ddfae0e9803fd933
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983561"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

W przypadku korzystania z narzędzia eDiscovery Export w celu wyeksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych z różnych narzędzi zbierania elektronicznych materiałów dowodowych firmy Microsoft domyślny rozmiar pliku PST, który można wyeksportować, wynosi 10 GB. Jeśli chcesz zmienić ten rozmiar domyślny, możesz edytować rejestr Windows na komputerze, którego używasz do eksportowania wyników wyszukiwania. Jednym z powodów jest to, że plik PST może zmieścić się na nośniku wymiennym, takim jak dysk DVD, dysk CD lub dysk USB. 
  
> [!NOTE]
> Narzędzie Eksport zbierania elektronicznych materiałów dowodowych służy do eksportowania wyników wyszukiwania podczas korzystania z narzędzia Przeszukiwanie zawartości w aplikacji Centrum zgodności platformy Microsoft 365.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Tworzenie ustawienia rejestru w celu zmiany rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

Wykonaj następującą procedurę na komputerze, na który chcesz wyeksportować wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych.
  
1. Zamknij narzędzie eDiscovery Export tool, jeśli jest otwarte. 
    
2. Zapisz poniższy tekst w pliku rejestru Window, używając sufiksu nazwy pliku reg. Na przykład PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    W powyższym przykładzie  `PstSizeLimitInBytes` ustawiono wartość 1 073 741 824 bajtów lub około 1 GB. Oto inne przykładowe wartości tego  `PstSizeLimitInBytes` ustawienia. 
    
    |**Rozmiar w GB (przybliżony)**|**Rozmiar w bajtach**|
    |:-----|:-----|
    |0,7 GB (700 MB)  <br/> |751619277  <br/> |
    |2 GB  <br/> |2147483648  <br/> |
    |4 GB  <br/> |4294967296  <br/> |
    |8 GB  <br/> |8589934592  <br/> |
   
3. Podczas eksportowania `PstSizeLimitInBytes` wyników wyszukiwania zmień żądany maksymalny rozmiar pliku PST, a następnie zapisz ten plik. 
    
4. W Windows kliknij lub kliknij dwukrotnie plik reg utworzony w poprzednich krokach.
    
5. W oknie Kontrola dostępu użytkownika kliknij przycisk **Tak** , aby edytor rejestru wprowadzić zmiany. 
    
6. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący, że ustawienie zostało pomyślnie dodane do rejestru.
    
7. Możesz powtórzyć kroki od 3 do 6, aby zmienić wartość  `PstSizeLimitInBytes` ustawienia rejestru. 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Często zadawane pytania dotyczące zmieniania domyślnego rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

 **Dlaczego jest domyślny rozmiar 10 GB?**
  
Domyślny rozmiar 10 GB był oparty na opiniach klientów. 10 GB to dobre saldo między optymalną ilością zawartości w pojedynczym pliku PST a minimalną możliwością uszkodzenia pliku.
  
 **Czy należy zwiększyć lub zmniejszyć domyślny rozmiar plików PST?**
  
Klienci zwykle zmniejszają limit rozmiaru tak, aby wyniki wyszukiwania zmieściły się na nośniku wymiennym, który mogą fizycznie wysłać do innych lokalizacji w organizacji. Nie zalecamy zwiększania domyślnego rozmiaru plików, ponieważ mogą wystąpić problemy z uszkodzeniami plików PST o rozmiarze ponad 10 GB.
  
 **Na jakim komputerze muszę to zrobić?**
  
Należy zmienić ustawienie rejestru na dowolnym komputerze lokalnym, na których jest uruchamiane narzędzie eDiscovery Export Tool.
  
 **Czy po zmianie tego ustawienia muszę ponownie uruchomić komputer?**
  
Nie, nie musisz ponownie uruchamiać komputera. Jeśli jednak narzędzie eDiscovery Export tool jest uruchomione, po zmianie tego ustawienia musisz je zamknąć i ponownie uruchomić.
  
 **Czy istniejący klucz rejestru jest edytowany, czy też jest tworzony nowy klucz?**
  
Nowy klucz rejestru jest tworzony po pierwszym uruchomieniu pliku reg utworzonego w tej procedurze. Ustawienie jest wówczas edytowane po każdej zmianie i ponownej edycji pliku reg.
