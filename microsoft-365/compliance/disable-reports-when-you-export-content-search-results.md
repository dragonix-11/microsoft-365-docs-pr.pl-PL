---
title: Wyłączanie raportów podczas eksportowania wyników wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: c9b0ff0c-282b-4a44-b43f-cfc5b96557f9
ms.custom:
- seo-marvel-apr2020
description: Edytuj rejestr Windows na komputerze lokalnym, aby wyłączyć raporty podczas eksportowania wyników wyszukiwania zawartości z portalu zgodności usługi Microsoft Purview.
ms.openlocfilehash: 5cd6816807af1b6da4fc8c41e7cdde7bc7f07d66
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000097"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Wyłączanie raportów podczas eksportowania wyników wyszukiwania zawartości

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W przypadku korzystania z narzędzia eDiscovery Export w celu wyeksportowania wyników wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview narzędzie automatycznie tworzy i eksportuje dwa raporty zawierające dodatkowe informacje o wyeksportowanej zawartości. Te raporty to plik Results.csv i plik Manifest.xml (zobacz sekcję [Często zadawane pytania dotyczące wyłączania raportów eksportu](#frequently-asked-questions-about-disabling-export-reports) w tym temacie, aby uzyskać szczegółowe opisy tych raportów). Ponieważ te pliki mogą być bardzo duże, możesz przyspieszyć czas pobierania i zaoszczędzić miejsce na dysku, uniemożliwiając eksportowanie tych plików. Można to zrobić, zmieniając rejestr Windows na komputerze używanym do eksportowania wyników wyszukiwania. Jeśli chcesz uwzględnić raporty w późniejszym czasie, możesz edytować ustawienie rejestru. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Tworzenie ustawień rejestru w celu wyłączenia raportów eksportu

Wykonaj poniższą procedurę na komputerze, którego użyjesz do wyeksportowania wyników wyszukiwania zawartości.
  
1. Zamknij narzędzie eksportu zbierania elektronicznych materiałów dowodowych, jeśli jest otwarte.
    
2. W zależności od tego, który raport eksportu chcesz wyłączyć, wykonaj jedną lub obie poniższe czynności.
    
    - **Results.csv**
    
      Zapisz następujący tekst w pliku rejestru Windows przy użyciu sufiksu nazwy pliku reg, na przykład DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Zapisz następujący tekst w pliku rejestru Windows przy użyciu sufiksu nazwy pliku reg, na przykład DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. W Eksploratorze Windows kliknij lub kliknij dwukrotnie plik reg utworzony w poprzednich krokach.
    
4. W oknie Użytkownik Access Control kliknij przycisk **Tak**, aby zezwolić Edytorowi rejestru na wprowadzenie zmian. 
    
5. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący o pomyślnym dodaniu ustawienia do rejestru.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Edytowanie ustawień rejestru w celu ponownego włączenia raportów eksportu

Jeśli wyłączysz Results.csv i Manifest.xml raporty, tworząc pliki reg w poprzedniej procedurze, możesz edytować te pliki, aby ponownie włączyć raport, tak aby był eksportowany z wynikami wyszukiwania. Ponownie wykonaj poniższą procedurę na komputerze, którego użyjesz do wyeksportowania wyników wyszukiwania zawartości.
  
1. Zamknij narzędzie eksportu zbierania elektronicznych materiałów dowodowych, jeśli jest otwarte.
    
2. Edytuj jeden lub oba pliki edycji reg utworzone w poprzedniej procedurze.
    
    - **Results.csv**
    
        Otwórz plik DisableResultsCsv.reg w Notatnik, zmień wartość `False` na `True`, a następnie zapisz plik. Na przykład po edytowaniu pliku wygląda on następująco:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Otwórz plik DisableManifestXml.reg w Notatnik, zmień wartość `False` na `True`, a następnie zapisz plik. Na przykład po edytowaniu pliku wygląda on następująco:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. W Eksploratorze Windows kliknij lub kliknij dwukrotnie plik reg edytowany w poprzednim kroku.
    
4. W oknie Użytkownik Access Control kliknij przycisk **Tak**, aby zezwolić Edytorowi rejestru na wprowadzenie zmian. 
    
5. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący o pomyślnym dodaniu ustawienia do rejestru.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Często zadawane pytania dotyczące wyłączania raportów eksportu

 **Jakie są raporty Results.csv i Manifest.xml?**
  
Pliki Results.csv i Manifest.xml zawierają dodatkowe informacje o wyeksportowanej zawartości.
  
- **Results.csv** Dokument Excel zawierający informacje o każdym elemencie, który jest pobierany w wyniku wyszukiwania. W przypadku poczty e-mail dziennik wyników zawiera informacje o każdej wiadomości, w tym: 
    
  - Lokalizacja wiadomości w źródłowej skrzynce pocztowej (w tym, czy wiadomość znajduje się w podstawowej, czy archiwum skrzynki pocztowej).
    
  - Data wysłania lub odebrania wiadomości.
    
  - Wiersz tematu z wiadomości.
    
  - Nadawca i adresaci wiadomości.
    
  - Czy komunikat jest zduplikowanym komunikatem, jeśli włączono anulowanie duplikowania podczas eksportowania wyników wyszukiwania. Zduplikowane komunikaty będą miały wartość w kolumnie **Element nadrzędny** , która identyfikuje komunikat jako duplikat. Wartość w kolumnie **Parent ItemId** jest taka sama jak wartość w kolumnie **DocumentId elementu** w wyeksportowanym komunikacie. 
    
    W przypadku dokumentów z witryn SharePoint i OneDrive dla Firm dziennik wyników zawiera informacje o każdym dokumencie, w tym:
    
  - Adres URL dokumentu.
    
  - Adres URL zbioru witryn, w którym znajduje się dokument.
    
  - Data ostatniej modyfikacji dokumentu.
    
  - Nazwa dokumentu (który znajduje się w kolumnie Podmiot w dzienniku wyników).
    
- **Manifest.xml** Plik manifestu (w formacie XML), który zawiera informacje o każdym elemencie uwzględnionym w wynikach wyszukiwania. Informacje zawarte w tym raporcie są takie same jak raport Results.csv, ale mają format określony przez model referencyjny odnajdywania elektronicznego (EDRM). Aby uzyskać więcej informacji na temat EDRM, przejdź do .[https://www.edrm.net](https://www.edrm.net)
    
 **Kiedy należy wyłączyć eksportowanie tych raportów?**
  
Zależy to od konkretnych potrzeb. Wiele organizacji nie wymaga dodatkowych informacji o wynikach wyszukiwania i nie potrzebuje tych raportów.
  
 **Na jakim komputerze muszę to zrobić?**
  
 Musisz zmienić ustawienie rejestru na dowolnym komputerze lokalnym, na którego uruchomiono narzędzie eksportu zbierania elektronicznych materiałów dowodowych. 
  
 **Czy po zmianie tego ustawienia należy ponownie uruchomić komputer?**
  
Nie, nie musisz ponownie uruchamiać komputera. Jeśli jednak narzędzie eksportu zbierania elektronicznych materiałów dowodowych jest uruchomione, musisz je zamknąć, a następnie ponownie uruchomić po zmianie ustawienia rejestru.
  
 **Czy istniejący klucz rejestru jest edytowany, czy jest tworzony nowy klucz?**
  
Nowy klucz rejestru jest tworzony przy pierwszym uruchomieniu pliku reg utworzonego w procedurze w tym temacie. Następnie ustawienie jest edytowane przy każdej zmianie i ponownym uruchomieniu pliku edycji reg.
