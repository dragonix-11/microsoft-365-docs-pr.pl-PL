---
title: Filtrowanie danych podczas importowania plików PST
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 26af16df-34cd-4f4a-b893-bc1d2e74039e
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Dowiedz się, jak filtrować dane przy użyciu inteligentnej funkcji importowania w usłudze importowania Microsoft 365 importowania podczas importowania plików PST do Microsoft 365.
ms.openlocfilehash: 593ce847803fdc3529fbe9276721e6bb8cf79069
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990498"
---
# <a name="filter-data-when-importing-pst-files"></a>Filtrowanie danych podczas importowania plików PST

Nowa funkcja inteligentnego importowania w usłudze importowania Microsoft 365 umożliwia filtrowanie elementów w plikach PST, które w rzeczywistości są importowane do docelowych skrzynek pocztowych. Oto jak to działa:
  
- Po utworzeniu i przesłaniu zadania importu pliku PST pliki PST są przekazywane do obszaru magazynu platformy Azure w chmurze firmy Microsoft.
  
- Microsoft 365 dane w plikach PST są analizowane w bezpieczny sposób przez zidentyfikowanie wieku elementów skrzynki pocztowej i poszczególnych typów wiadomości zawartych w plikach PST.
  
- Po zakończeniu analizy i przygotowaniu danych do zaimportowania możesz zaimportować wszystkie dane w plikach PST w stanie, w jakim są, lub przyciąć zaimportowane dane, ustawiając filtry sterujące tym, które dane są importowane. Możesz na przykład wybrać jedną z opcji:
  
  - Importowanie tylko elementów o określonym wieku.
  
  - Importowanie wybranych typów wiadomości.
  
  - Wyklucz wiadomości wysłane lub odebrane przez konkretne osoby.
  
- Po skonfigurowaniu ustawień filtru zaimportuj Microsoft 365 tylko dane spełniające kryteria filtrowania do docelowych skrzynek pocztowych określonych w zadaniu importu.
  
Na poniższej ilustracji przedstawiono proces inteligentnego importowania i wyróżnione są zadania wykonywane przez użytkowników oraz zadania wykonywane przez Office 365.
  
![Inteligentny proces importowania w programie Office 365.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>Tworzenie zadania importu pliku PST

- W procedurach w tym temacie założono, że zadanie importu pliku PST utworzono w usłudze importowania Office 365 przy użyciu przekazywania sieciowego lub wysyłki dysków. Aby uzyskać instrukcje krok po kroku, zobacz jeden z następujących tematów:
    
  - [Użyj przekazywania sieciowego, aby zaimportować pliki PST do Office 365](use-network-upload-to-import-pst-files.md)
    
  - [Użyj wysyłki dysków, aby zaimportować pliki PST do Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Po utworzeniu zadania importu przy użyciu przekazywania sieciowego stan zadania importu na stronie Importowanie w Centrum zgodności usługi & ma ustawioną wartość Analiza w **toku, co** oznacza, że program Microsoft 365 analizuje dane w przekazanych plikach PST. Kliknij **pozycję Refreshrefresh**![ (Odświeżrefresh).](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) w celu zaktualizowania stanu zadania importu. 
    
- W przypadku zadań importu wysyłki dysków dane będą analizowane przez usługę Microsoft 365 po otrzymaniu dysku twardego przez pracowników centrum danych firmy Microsoft i przesłaniu plików PST do obszaru magazynu platformy Azure dla organizacji.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Filtrowanie danych importowanych do skrzynek pocztowych

Po utworzeniu zadania importu pliku PST wykonaj poniższe czynności, aby przefiltrować dane przed ich zaimportowaniem w celu Office 365.
  
1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń konta administratora w organizacji.
    
2. W lewym okienku okna Centrum zgodności platformy Microsoft 365 pozycję **Importowanie zarządzania informacjami**\>.
    
    Zadania importu dla organizacji są wyświetlane na karcie **Importowanie**. Wartość **Ukończona analiza** w kolumnie **Stan** wskazuje zadania importu, które zostały przeanalizowane przez Microsoft 365 i są gotowe do zaimportowania.
    
    ![Stan ukończenia analizy wskazuje Microsoft 365 dane w plikach PST zostały już przeanalizowane.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Wybierz zadanie importu, które chcesz ukończyć, a następnie kliknij pozycję **Importuj, Office 365**.
  
    Zostanie wyświetlona wysuwana strona z informacjami o plikach PST i innymi informacjami na temat zadania importu.

4. Kliknij **pozycję Importuj do Office 365**.
    
    Zostanie **wyświetlona strona Filtrowanie** danych. Zawiera szczegółowe informacje o danych w plikach PST na zadanie importu, w tym informacje o wieku danych. 
    
    ![Strona Filtrowanie danych zawiera szczegółowe informacje o danych dotyczące plików PST na temat zadania importu.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. W zależności od tego, czy chcesz przyciąć dane, które są importowane do Microsoft 365, w obszarze Czy chcesz filtrować dane **?** wykonaj jedną z następujących czynności:
  
    a. Kliknij **przycisk Tak, chcę filtrować dane przed zaimportowaniem** , aby przyciąć zaimportowane dane, a następnie kliknij przycisk **Dalej**.
  
    Strona **Importowanie danych do Office 365** stronie jest wyświetlana ze szczegółowymi informacjami o danych z analiz, które Microsoft 365 przeprowadzić. 
  
    ![Microsoft 365 szczegółowe informacje o danych z analiz plików PST.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Na wykresie na tej stronie pokazano ilość danych, które zostaną zaimportowane. Na wykresie są wyświetlane informacje o poszczególnych typach wiadomości znalezionych w plikach PST. Możesz umieścić kursor na każdym pasku, aby wyświetlić konkretne informacje dotyczące tego typu wiadomości. Istnieje również lista rozwijana z różnymi wartościami wieku na podstawie analizy plików PST. Po wybraniu wieku z listy rozwijanej wykres zostanie zaktualizowany, aby pokazać, ile danych zostanie zaimportowanych dla wybranego wieku. 
  
    b. Aby skonfigurować filtry dodatku w celu zmniejszenia ilości importowanych danych, kliknij pozycję **Więcej opcji filtrowania**.
  
    ![Skonfiguruj filtry na stronie Więcej opcji, aby przyciąć importowane dane.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Filtry te można skonfigurować:
  
      - **Wiek** — wybierz wiek, aby importowane zostały tylko elementy, które są nowsze niż określony wiek. Zobacz [sekcję Więcej informacji](#more-information), aby uzyskać opis sposobu Microsoft 365 zasobników wiekowych dla **filtru** Wiek. 
  
      - **Typ** — w tej sekcji przedstawiono wszystkie typy wiadomości, które zostały znalezione w plikach PST dla zadania importu. Możesz usunąć zaznaczenie pola wyboru obok typu wiadomości, który chcesz wykluczyć. Nie można wykluczyć typu wiadomości Inne. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać listę elementów skrzynki pocztowej zawartych w kategorii Inne.
  
      - **Użytkownicy** — możesz wykluczyć wiadomości wysłane lub odebrane przez konkretne osoby. Aby wykluczyć osoby wyświetlane w polu Od, Do lub DW: wiadomości, kliknij pozycję Wyklucz użytkowników obok tego typu  adresata. Wpisz adres e-mail (adres SMTP) osoby i kliknij **ikonę DodajNaw**![.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) w celu dodania ich do listy wykluczonych użytkowników dla tego typu adresata,  a następnie kliknij przycisk Zapisz, aby zapisać listę wykluczonych użytkowników. 
  
        > [!NOTE]
        > Microsoft 365 nie wyświetla szczegółowych informacji o danych wynikających z ustawienia **filtru** Osoby. Jeśli jednak ustawisz ten filtr tak, aby wykluczyć wiadomości wysłane lub odebrane przez określone osoby, te wiadomości zostaną wykluczone podczas rzeczywistego procesu importowania. 
  
    c. Kliknij **przycisk Zastosuj** na **wysuwana** strona Więcej opcji filtrowania, aby zapisać ustawienia filtru. 
  
    Szczegółowe informacje o danych na stronie  Importowanie danych do Office 365 są aktualizowane na podstawie ustawień filtru, łącznie z łączną ilością danych, które zostaną zaimportowane na podstawie ustawień filtru. Widoczne jest również podsumowanie ustawień filtru. Możesz kliknąć pozycję **Edytuj** obok filtru, aby w razie potrzeby zmienić to ustawienie. 
  
    ![Szczegółowe informacje o danych są aktualizowane na podstawie ustawień filtru.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. Kliknij **Dalej**.
  
    Zostanie wyświetlona strona stanu z widocznymi ustawieniami filtru. Ponownie możesz edytować dowolne ustawienia filtru.
  
    e. Kliknij **pozycję Importuj dane** , aby rozpocząć importowanie. Zostanie wyświetlona całkowita ilość danych, które zostaną zaimportowane. 
  
    Lub
  
    a. Kliknij **przycisk Nie, chcę zaimportować wszystkie** dane z plików PST, aby je Office 365, a następnie kliknij przycisk **Dalej**.
  
    b. Na **stronie Importowanie danych do Office 365** kliknij pozycję **Importuj dane**, aby rozpocząć importowanie. Zostanie wyświetlona całkowita ilość danych, które zostaną zaimportowane. 
  
6. Na karcie **Importowanie** kliknij pozycję **Odśwież** ![odśwież](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png). Stan zadania importu jest wyświetlany w **kolumnie Stan** .
  
7. Kliknij zadanie importu, aby wyświetlić bardziej szczegółowe informacje, takie jak stan każdego pliku PST i skonfigurowane ustawienia filtru.

## <a name="more-information"></a>Więcej informacji

- Jak Microsoft 365 określić odstępy dla filtru wieku? Gdy program Microsoft 365 analizuje plik PST, analizuje wysłany lub odebrany znacznik czasu każdego elementu (jeśli dla elementu zaznaczono zarówno wysłaną, jak i otrzymaną sygnaturę czasową, zaznaczona jest najstarsza data). Następnie Microsoft 365 i porównuje wartość roku dla tej sygnatury czasowej z bieżącą datą w celu określenia wieku pozycji. Te wieki są następnie używane jako wartości na liście rozwijanej **filtru** Wiek. Jeśli na przykład plik PST zawiera wiadomości z lat 2016, 2015 i 2014, to w filtrze Wiek będą wartości **1** rok, **2** lata **i 3 lata**.
  
- W poniższej tabeli wymieniono typy wiadomości zawarte w kategorii  Inne w filtrze  Typ na stronie Wysuwana więcej opcji (zobacz krok 5b w poprzedniej procedurze). Obecnie nie można wykluczyć elementów z kategorii "Inne" podczas importowania punktów PST do Office 365. 
  
    |**Identyfikator klasy wiadomości**|**Elementy skrzynki pocztowej, które korzystają z tej klasy wiadomości**|
    |:-----|:-----|
    |IPM. Działanie  <br/> |Pozycje dziennika  <br/> |
    |IPM. Dokument  <br/> |Dokumenty i pliki (nie są dołączone do wiadomości e-mail)  <br/> |
    |IPM. Plik  <br/> |(taki sam jak IPM. Dokument)  <br/> |
    |IPM. Note.IMC.Notification  <br/> |Raporty wysyłane przez internetową pocztę Połączenie, która jest bramą Exchange Server do Internetu  <br/> |
    |IPM. Note.Microsoft.Fax  <br/> |Faksy  <br/> |
    |IPM. Note.Rules.Oof.Template.Microsoft  <br/> |Automatyczne wiadomości z biura  <br/> |
    |IPM. Note.Rules.ReplyTemplate.Microsoft  <br/> |Odpowiedzi wysłane przez regułę skrzynki odbiorczej  <br/> |
    |IPM. OLE. Zajęcia  <br/> |Wyjątki dla serii cyklicznej  <br/> |
    |IPM. Odwołaj.Raport  <br/> |Raporty dotyczące odwoływania wiadomości  <br/> |
    |IPM. Zdalny  <br/> |Zdalne wiadomości e-mail  <br/> |
    |IPM. Raport  <br/> |Raporty o stanie elementów  <br/> |
