---
title: Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Możesz zmienić domyślny rozmiar plików PST pobranych na komputer podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: 135c83f734e0687c8d477ab434d0aa539224f39a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100836"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W przypadku korzystania z narzędzia eDiscovery Export do eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych z różnych narzędzi microsoft eDiscovery domyślny rozmiar pliku PST, który można wyeksportować, wynosi 10 GB. Jeśli chcesz zmienić ten rozmiar domyślny, możesz edytować rejestr Windows na komputerze używanym do eksportowania wyników wyszukiwania. Jednym z powodów, aby to zrobić, jest to, aby plik PST mógł zmieścić się na nośniku wymiennym, takim dvd, dysk kompaktowy lub dysk USB. 
  
> [!NOTE]
> Narzędzie eksportu zbierania elektronicznych materiałów dowodowych służy do eksportowania wyników wyszukiwania w przypadku korzystania z narzędzia do wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Tworzenie ustawienia rejestru w celu zmiany rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

Wykonaj poniższą procedurę na komputerze, którego użyjesz do wyeksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych.
  
1. Zamknij narzędzie eksportu zbierania elektronicznych materiałów dowodowych, jeśli jest otwarte. 
    
2. Zapisz następujący tekst w pliku rejestru okna przy użyciu sufiksu nazwy pliku reg; na przykład PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    W powyższym przykładzie  `PstSizeLimitInBytes` wartość jest ustawiona na 1 073 741 824 bajtów lub około 1 GB. Poniżej przedstawiono kilka innych przykładowych wartości dla  `PstSizeLimitInBytes` tego ustawienia. 
    
    |**Rozmiar w GB (ok.)**|**Rozmiar w bajtach**|
    |:-----|:-----|
    |0,7 GB (700 MB)  <br/> |751619277  <br/> |
    |2 GB  <br/> |2147483648  <br/> |
    |4 GB  <br/> |4294967296  <br/> |
    |8 GB  <br/> |8589934592  <br/> |
   
3. `PstSizeLimitInBytes` Zmień wartość na żądany maksymalny rozmiar pliku PST podczas eksportowania wyników wyszukiwania, a następnie zapisz plik. 
    
4. W Eksploratorze Windows kliknij lub kliknij dwukrotnie plik reg utworzony w poprzednich krokach.
    
5. W oknie Użytkownik Access Control kliknij przycisk **Tak**, aby zezwolić Edytorowi rejestru na wprowadzenie zmian. 
    
6. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący o pomyślnym dodaniu ustawienia do rejestru.
    
7. Możesz powtórzyć kroki 3–6, aby zmienić wartość  `PstSizeLimitInBytes` ustawienia rejestru. 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Często zadawane pytania dotyczące zmiany domyślnego rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

 **Dlaczego domyślny rozmiar to 10 GB?**
  
Domyślny rozmiar 10 GB był oparty na opiniach klientów; 10 GB to dobra równowaga między optymalną ilością zawartości w jednym PST i minimalną szansą na uszkodzenie pliku.
  
 **Czy należy zwiększyć lub zmniejszyć domyślny rozmiar plików PST?**
  
Klienci zwykle zmniejszają limit rozmiaru, dzięki czemu wyniki wyszukiwania będą pasować do nośników wymiennych, które mogą fizycznie wysyłać do innych lokalizacji w organizacji. Nie zalecamy zwiększania rozmiaru domyślnego, ponieważ pliki PST większe niż 10 GB mogą mieć problemy z uszkodzeniem.
  
 **Na jakim komputerze muszę to zrobić?**
  
Należy zmienić ustawienie rejestru na dowolnym komputerze lokalnym, na którego uruchomiono narzędzie eksportu elektronicznego zbierania elektronicznych materiałów dowodowych.
  
 **Czy po zmianie tego ustawienia należy ponownie uruchomić komputer?**
  
Nie, nie musisz ponownie uruchamiać komputera. Jeśli jednak narzędzie eksportu elektronicznego zbierania elektronicznych materiałów dowodowych jest uruchomione, musisz je zamknąć i ponownie uruchomić po zmianie tego ustawienia.
  
 **Czy istniejący klucz rejestru jest edytowany, czy jest tworzony nowy klucz?**
  
Nowy klucz rejestru jest tworzony przy pierwszym uruchomieniu pliku reg utworzonego w tej procedurze. Następnie ustawienie jest edytowane przy każdej zmianie i ponownym uruchomieniu pliku edycji reg.
