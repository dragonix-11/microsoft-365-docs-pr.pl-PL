---
title: Podczas przenoszenia danych i po tym procesie
ms.author: andyber
author: andybergen
manager: scotv
ms.date: 09/22/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
ms.localizationpriority: medium
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Przenoszenie danych to operacje zaplecza, które występują, gdy firma Microsoft przenosi usługi i skojarzone dane dla dzierżawy do nowego obszaru geograficznego centrum danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e9b4a7e7be30920853318adf4015541b077b6cc1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099152"
---
# <a name="during-and-after-your-data-move"></a>Podczas przenoszenia danych i po tym procesie

Przenoszenie danych to operacja zaplecza o minimalnym wpływie na użytkowników końcowych. Nie jest wymagana żadna akcja, gdy firma Microsoft przenosi każdą usługę i skojarzone dane dla dzierżawy do nowego obszaru geograficznego centrum danych. Przesyłanie i walidacja danych odbywa się z wyprzedzeniem w tle przy minimalnym wpływie na użytkowników.
  
> [!NOTE]
> Ruchy są wykonywane w różnym czasie dla każdej usługi. W związku z tym w innym czasie zobaczysz opisaną ograniczoną funkcjonalność dla każdej usługi. 
  
Obejrzyj centrum wiadomości Microsoft 365, aby uzyskać potwierdzenie po zakończeniu przenoszenia poszczególnych Exchange Online, SharePoint Online i Teams czatu. Jak pokazano w poniższej tabeli, ukończenie podstawowych danych klientów magazynowanych do nowego obszaru geograficznego centrum danych może potrwać do 24 miesięcy od zakończenia okresu rejestracji.   

| Klienci z krajem rejestracji | Wszystkie ruchy ukończone przez |
|:-----|:-----|
|Australia, Nowa Zelandia, Fidżi  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Japonia  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Indie  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Kanada  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Korea Południowa  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Zjednoczone Królestwo  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Francja  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Zjednoczone Emiraty Arabskie  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Republika Południowej Afryki  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Szwajcaria, Liechtenstein  <br/> |piątek, 1 lipca 2022 r.  <br/> |
|Norwegia  <br/> |1 listopada 2022 r.  <br/> |
|Niemcy  <br/> |1 maja 2023 r.  <br/> |
|Brazylia  <br/> |czwartek, 1 czerwca 2023 r.  <br/> |
|Szwecja  <br/> |1 czerwca 2024 r.  <br/> |

## <a name="exchange-online"></a>Exchange Online

Ponieważ przeniesienie każdego użytkownika do nowego obszaru geograficznego centrum danych dla jednej dzierżawy wymaga czasu, niektórzy użytkownicy nadal będą znajdować się w starym obszarze geograficznym centrum danych podczas przenoszenia, podczas gdy inni będą w nowym obszarze geograficznym centrum danych. Oznacza to, że niektóre funkcje, które obejmują dostęp do wielu skrzynek pocztowych, mogą nie działać w pełni w okresie procesu przenoszenia, który może trwać kilka tygodni. Te funkcje zostały opisane w poniższych sekcjach.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Otwieranie folderu udostępnionego w Outlook web access

Niektórzy użytkownicy otwierają udostępniony folder poczty z innej skrzynki pocztowej (do której użytkownik ma uprawnienia do odczytu lub zapisu) w programie Outlook Web Access przy użyciu funkcji "Folder udostępniony". W poniższej tabeli opisano sposób działania dostępu do folderów udostępnionych podczas przenoszenia skrzynki pocztowej. Pamiętaj, że użytkownicy z pełnymi uprawnieniami do udostępnionej skrzynki pocztowej mogą otworzyć skrzynkę pocztową przy użyciu Outlook web access podczas przenoszenia. 
  
| Konfiguracja | Opis |
|:-----|:-----|
|Użytkownik ma uprawnienie folderu skrzynki pocztowej do innej skrzynki pocztowej  <br/> |Potencjalnie ograniczone.  <br/> Jeśli użytkownik A i skrzynka pocztowa B nie są w tym samym obszarze geograficznym podczas przenoszenia dzierżawy, użytkownik A nie może otworzyć folderu skrzynki pocztowej B w Outlook dostępu do sieci Web, jeśli użytkownik A ma uprawnienia tylko do określonego folderu w skrzynce pocztowej B.  <br/> Aby dodać folder udostępniony, kliknij prawym przyciskiem myszy nazwę użytkownika w panelu nawigacyjnym po lewej stronie i wybierz pozycję **Dodaj folder udostępniony**.  <br/> |
|Użytkownik z pełnym uprawnieniem skrzynki pocztowej do innej skrzynki pocztowej  <br/> |W pełni obsługiwane.  <br/> Jeśli użytkownik A ma uprawnienie "Pełny dostęp" do skrzynki pocztowej B, użytkownik A może kliknąć folder udostępniony w lewym panelu nawigacyjnym w Outlook Web Access, aby otworzyć okno z wyświetloną skrzynką pocztową B.  Użytkownik może otworzyć udostępnioną skrzynkę pocztową przy użyciu Outlook web access podczas przenoszenia bez żadnego negatywnego wpływu. Ograniczenie dotyczy tylko udostępniania na poziomie folderu w skrzynce pocztowej.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Po przeniesieniu SharePoint Online dane dla następujących usług również są przenoszone:
  
- OneDrive dla Firm
    
- usługi wideo Microsoft 365
    
- Office w przeglądarce
    
- Aplikacje usługi Microsoft 365 dla przedsiębiorstw
    
- Visio Pro dla Microsoft 365
    
Po zakończeniu przenoszenia danych usługi SharePoint Online mogą zostać wyświetlone niektóre z następujących efektów.
  
### <a name="microsoft-365-video-services"></a>usługi wideo Microsoft 365

- Przenoszenie danych wideo trwa dłużej niż przenoszenie pozostałej części zawartości w usłudze SharePoint Online.
    
- Po przeniesieniu zawartości SharePoint Online nastąpi czas, gdy nie będzie można odtwarzać filmów wideo.
    
- Usuwamy transkodowane kopie z poprzedniego centrum danych i transkodujemy je ponownie w nowym centrum danych.
    
### <a name="search"></a>Szukaj

W trakcie przenoszenia danych usługi SharePoint Online przeprowadzamy migrację indeksu wyszukiwania i ustawień wyszukiwania do nowej lokalizacji. Dopóki nie **zakończymy** przenoszenia danych usługi SharePoint Online, nadal będziemy obsługiwać użytkowników z indeksu w oryginalnej lokalizacji. W nowej lokalizacji wyszukiwanie automatycznie rozpoczyna przeszukiwanie zawartości po zakończeniu przenoszenia danych usługi SharePoint Online. Od tego momentu i dalej będziemy obsługiwać użytkowników z zmigrowanego indeksu. Zmiany zawartości, które wystąpiły po migracji, nie są uwzględniane w migrowanym indeksie, dopóki przeszukiwanie nie zostanie pobrane. Większość klientów nie zauważa, że wyniki są mniej świeże zaraz po zakończeniu przenoszenia danych SharePoint Online, ale niektórzy klienci mogą doświadczyć mniejszej świeżości w ciągu pierwszych 24–48 godzin 
  
Dotyczy to następujących funkcji wyszukiwania:
  
- Wyniki wyszukiwania i składniki Web Part wyszukiwania: wyniki nie zawierają zmian, które wystąpiły po migracji, dopóki przeszukiwanie nie zostanie pobrane. 
    
- Delve: Delve nie zawiera zmian, które wystąpiły po migracji, dopóki przeszukiwanie nie zostanie pobrane.
    
- Raporty dotyczące popularności i wyszukiwania dla witryny: liczba raportów Excel w nowej lokalizacji obejmuje tylko zmigrowane liczby i liczby raportów użycia, które zostały uruchomione po zakończeniu przenoszenia danych usługi SharePoint Online. Wszelkie liczby z okresu przejściowego są tracone i nie można ich odzyskać. Ten okres zazwyczaj trwa kilka dni. Niektórzy klienci mogą doświadczać krótszych lub dłuższych strat.
    
- Portal wideo: wyświetlanie liczby i statystyk dla portalu wideo zależy od statystyk Excel Raporty, dlatego liczba wyświetleń i statystyki portalu wideo są tracone w tym samym okresie co w przypadku raportów Excel.
    
- eDiscovery: Elementy, które uległy zmianie podczas migracji, nie są wyświetlane, dopóki przeszukiwanie nie odbierze zmian.
    
- Ochrona przed utratą danych (DLP): zasady nie są wymuszane dla elementów, które zmieniają się, dopóki przeszukiwanie nie pobierze zmian.

W ramach migracji domyślny region ulegnie zmianie i cała nowa zawartość będzie przechowywana w nowym regionie domyślnym. Istniejąca zawartość będzie przenoszona w tle bez wpływu na Ciebie przez maksymalnie 90 dni po pierwszej zmianie lokalizacji danych usługi SharePoint Online w centrum administracyjnym.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Karta Pliki

Po zakończeniu migracji na karcie Pliki może upłynąć dodatkowy czas (do 7 sekund), aby w pełni załadować, gdy użytkownik po raz pierwszy spróbuje go użyć. 

### <a name="read-only-period"></a>Okres tylko do odczytu

Teams usług czatu przenosi każdy wątek indywidualnie.  Wątek jest zablokowany w stanie tylko do odczytu podczas przenoszenia, co trwa kilka sekund na wątek.  Wątki pozostają dostępne podczas migracji.

## <a name="skype-for-business"></a>Skype dla firm

Skype dla firm ruchy nie są już dostępne.  [Skype dla firm Online zostanie wycofana](/lifecycle/announcements/skype-for-business-online-retirement) 31 lipca 2021 r. Po tym czasie usługa nie będzie już dostępna. 
  
## <a name="related-topics"></a>Tematy pokrewne 
 
[Jak zażądać przeniesienia danych](request-your-data-move.md)
    
[Ogólne często zadawane pytania dotyczące przenoszenia danych](data-move-faq.yml)
  
[Nowe lokalizacje geograficzne centrum danych dla Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Usługi platformy Azure według regionów](https://azure.microsoft.com/regions/)
