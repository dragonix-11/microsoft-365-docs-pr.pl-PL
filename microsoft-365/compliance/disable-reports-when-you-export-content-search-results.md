---
title: Wyłączanie raportów podczas eksportowania wyników przeszukiwania zawartości
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
description: Edytuj rejestr Windows na komputerze lokalnym, aby wyłączyć raporty podczas eksportowania wyników przeszukiwania zawartości z witryny Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: bafdab1586b28239ddba7cf251704111731f2239
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973513"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Wyłączanie raportów podczas eksportowania wyników przeszukiwania zawartości

Narzędzie eDiscovery Export tool to export the content search in the Centrum zgodności platformy Microsoft 365 (Eksportowanie zbierania elektronicznych materiałów dowodowych) powoduje automatyczne utworzenie i wyeksportowanie dwóch raportów zawierających dodatkowe informacje na temat eksportowaną zawartości. Te raporty to plik Results.csv oraz plik Manifest.xml (aby uzyskać szczegółowe [opisy](#frequently-asked-questions-about-disabling-export-reports) tych raportów, zobacz sekcję Często zadawane pytania na temat wyłączania raportów eksportu w tym temacie). Ponieważ te pliki mogą być bardzo duże, możesz przyspieszyć czas pobierania i zaoszczędzić miejsce na dysku, uniemożliwiając ich eksportowanie. Możesz to zrobić, zmieniając rejestr Windows na komputerze, na który są eksportowane wyniki wyszukiwania. Jeśli chcesz dołączyć raporty w późniejszym czasie, możesz edytować ustawienie rejestru. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Tworzenie ustawień rejestru w celu wyłączenia raportów eksportu

Wykonaj poniższe czynności na komputerze, na który chcesz wyeksportować wyniki wyszukiwania zawartości.
  
1. Zamknij narzędzie eDiscovery Export tool, jeśli jest otwarte.
    
2. Wykonaj jedną lub obie z poniższych czynności, zależnie od tego, który raport eksportu chcesz wyłączyć.
    
    - **Results.csv**
    
      Zapisz poniższy tekst w Windows rejestru, używając sufiksu nazwy pliku reg, na przykład DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Zapisz poniższy tekst w pliku rejestru programu Windows, używając sufiksu nazwy pliku reg, na przykład DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. W Windows kliknij lub kliknij dwukrotnie plik reg utworzony w poprzednich krokach.
    
4. W oknie Kontrola dostępu użytkownika kliknij przycisk **Tak** , aby edytor rejestru wprowadzić zmiany. 
    
5. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący, że ustawienie zostało pomyślnie dodane do rejestru.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Edytowanie ustawień rejestru w celu ponownego włączenia raportów eksportu

Jeśli wyłączono raporty programu Results.csv i Manifest.xml przez utworzenie plików reg w poprzedniej procedurze, można edytować te pliki w celu ponownego włączenia raportu, tak aby został wyeksportowany z wynikami wyszukiwania. Ponownie wykonaj na komputerze następującą procedurę, która ma być wyeksportowana do wyników przeszukiwania zawartości.
  
1. Zamknij narzędzie eDiscovery Export tool, jeśli jest otwarte.
    
2. Edytuj jeden lub oba pliki reg edycji utworzone w poprzedniej procedurze.
    
    - **Results.csv**
    
        Otwórz plik DisableResultsCsv.reg w programie Notatnik zmień `False` `True`wartość na , a następnie zapisz plik. Na przykład po zakończeniu edytowania pliku wygląda on następująco:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Otwórz plik DisableManifestXml.reg w programie Notatnik, `False` `True`zmień wartość na , a następnie zapisz plik. Na przykład po zakończeniu edytowania pliku wygląda on następująco:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. W Windows kliknij lub kliknij dwukrotnie plik reg, który był edytowany w poprzednim kroku.
    
4. W oknie Kontrola dostępu użytkownika kliknij przycisk **Tak** , aby edytor rejestru wprowadzić zmiany. 
    
5. Po wyświetleniu monitu o kontynuowanie kliknij przycisk **Tak**.
    
    Edytor rejestru wyświetla komunikat informujący, że ustawienie zostało pomyślnie dodane do rejestru.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Często zadawane pytania dotyczące wyłączania raportów eksportu

 **Co to są raporty Results.csv i Manifest.xml?**
  
Pliki Results.csv i Manifest.xml zawierają dodatkowe informacje o eksportowanych elementach.
  
- **Results.csv** Dokument Excel zawierający informacje o każdym pobieraniu elementu jako wyniku wyszukiwania. W przypadku wiadomości e-mail dziennik wyników zawiera informacje o każdej wiadomości, w tym: 
    
  - Lokalizacja wiadomości w źródłowej skrzynce pocztowej (w tym to, czy wiadomość znajduje się w podstawowej, czy archiwaowej skrzynce pocztowej).
    
  - Data wysłania lub odebrania wiadomości.
    
  - Wiersz Temat wiadomości.
    
  - Nadawca i adresaci wiadomości.
    
  - Informacja o tym, czy wiadomość jest zduplikowana, jeśli włączono duplikowanie podczas eksportowania wyników wyszukiwania. Zduplikowane wiadomości będą mieć wartość w kolumnie **Element elementu nadrzędnego** , która identyfikuje wiadomość jako duplikat. Wartość w kolumnie **Element nadrzędny itemId** jest taka sama jak wartość w kolumnie **Item DocumentId** wiadomości, która została wyeksportowana. 
    
    W przypadku dokumentów poszczególnych SharePoint i OneDrive dla Firm dziennik wyników zawiera informacje o każdym dokumencie, takie jak:
    
  - Adres URL dokumentu.
    
  - Adres URL zbioru witryn, w którym znajduje się dokument.
    
  - Data ostatniej modyfikacji dokumentu.
    
  - Nazwa dokumentu (która znajduje się w kolumnie Temat w dzienniku wyników).
    
- **Manifest.xml** Plik manifestu (w formacie XML), który zawiera informacje o każdym z elementów uwzględnionych w wynikach wyszukiwania. Informacje w tym raporcie są takie same jak w raporcie Results.csv, ale są w formacie określonym przez model EDRM (Electronic Discovery Reference Model). Aby uzyskać więcej informacji na temat usługi EDRM, przejdź na stronie [https://www.edrm.net](https://www.edrm.net).
    
 **Kiedy należy wyłączyć eksportowanie tych raportów?**
  
Zależy to od konkretnych potrzeb. Wiele organizacji nie wymaga dodatkowych informacji o wynikach wyszukiwania i nie potrzebuje tych raportów.
  
 **Na jakim komputerze muszę to zrobić?**
  
 Musisz zmienić ustawienie rejestru na dowolnym komputerze lokalnym, na który jest uruchamiane narzędzie eDiscovery Export Tool. 
  
 **Czy po zmianie tego ustawienia muszę ponownie uruchomić komputer?**
  
Nie, nie musisz ponownie uruchamiać komputera. Jeśli jednak narzędzie eDiscovery Export tool jest uruchomione, należy je zamknąć i ponownie uruchomić po zmianie ustawienia rejestru.
  
 **Czy istniejący klucz rejestru jest edytowany, czy też jest tworzony nowy klucz?**
  
Nowy klucz rejestru jest tworzony po pierwszym uruchomieniu pliku reg utworzonego w procedurze w tym temacie. Następnie ustawienie jest edytowane po każdej zmianie i po ponownej uruchomieniu pliku reg edit.
