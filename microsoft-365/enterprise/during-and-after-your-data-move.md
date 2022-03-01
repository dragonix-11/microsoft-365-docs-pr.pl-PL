---
title: Podczas przenoszenia danych i po tym czasie
ms.author: andyber
author: andybergen
manager: laurawi
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
description: Przeniesienie danych to operacje back-end, które występują w przypadku, gdy firma Microsoft przenosi usługi i skojarzone z nią dane dzierżawy do nowego geolokalizacji centrum danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1fcb62897f1feabe0ca8c447c51e61c7d752138c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997821"
---
# <a name="during-and-after-your-data-move"></a>Podczas przenoszenia danych i po tym czasie

Przeniesienie danych to operacja back-end, która ma minimalny wpływ na użytkowników końcowych. Podczas gdy firma Microsoft przenosi wszystkie usługi i skojarzone z nią dane dzierżawy do nowej lokalizacji geograficznej centrum danych, nie jest wymagane żadne działanie. Transfer danych i weryfikacja występują wcześniej w tle z minimalnym skutkiem dla użytkowników.
  
> [!NOTE]
> Przeniesienie występuje w różnych momentach dla każdej usługi. W efekcie w innym czasie będzie dostępna opisana ograniczona funkcjonalność poszczególnych usług. 
  
Po potwierdzeniu Microsoft 365 wiadomości w Centrum wiadomości dla poszczególnych Exchange Online, SharePoint Online i Teams zakończyć usługę czatu. Jak pokazano w poniższej tabeli, ukończenie podstawowych danych klienta w spoczynku może potrwać do 24 miesięcy od zakończenia okresu rejestracji.   

| Klienci z kraju rejestracji w układzie | Wszystkie przeniesienie ukończone do |
|:-----|:-----|
|Australia, Nowa Zelandia, Fidżi  <br/> |1 lipca 2022 r.  <br/> |
|Japonia  <br/> |1 lipca 2022 r.  <br/> |
|Indie  <br/> |1 lipca 2022 r.  <br/> |
|Kanada  <br/> |1 lipca 2022 r.  <br/> |
|Korea Południowa  <br/> |1 lipca 2022 r.  <br/> |
|Zjednoczone Królestwo  <br/> |1 lipca 2022 r.  <br/> |
|Francja  <br/> |1 lipca 2022 r.  <br/> |
|Zjednoczone Emiraty Arabskie  <br/> |1 lipca 2022 r.  <br/> |
|Republika Południowej Afryki  <br/> |1 lipca 2022 r.  <br/> |
|Szwajcaria, Liechtenstein  <br/> |1 lipca 2022 r.  <br/> |
|Norwegia  <br/> |1 listopada 2022 r.  <br/> |
|Niemcy  <br/> |1 maja 2023 r.  <br/> |
|Brazylia  <br/> |1 czerwca 2023 r.  <br/> |
|Szwecja  <br/> |1 czerwca 2024 r.  <br/> |

## <a name="exchange-online"></a>Exchange Online

Ponieważ przeniesienie poszczególnych użytkowników do nowego geolokalizacji centrum danych dla jednej dzierżawy zajmuje trochę czasu, niektórzy użytkownicy nadal będą w starej lokalizacji geograficznej centrum danych, a inni w nowej lokalizacji geograficznej centrum danych. Oznacza to, że niektóre funkcje, które wymagają uzyskiwania dostępu do wielu skrzynek pocztowych, mogą nie działać w pełni w okresie procesu przenoszenia, który może obejmować ostatnie tygodnie. Te funkcje opisano w poniższych sekcjach.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Otwieranie folderu udostępnionego w programie Outlook Web Access

Niektórzy użytkownicy otwierają udostępniony folder poczty z innej skrzynki pocztowej (do których użytkownik ma uprawnienia do odczytu lub zapisu) w programie Outlook Web Access za pomocą funkcji "Folder udostępniony". W poniższej tabeli opisano sposób działania dostępu do folderów udostępnionych podczas przenoszenia skrzynki pocztowej. Pamiętaj, że użytkownicy z pełnymi uprawnieniami do udostępnionej skrzynki pocztowej mogą ją otwierać przy użyciu programu Outlook Web Access podczas przenoszenia. 
  
| Konfiguracja | Opis |
|:-----|:-----|
|Użytkownik ma uprawnienie folderu skrzynki pocztowej do innej skrzynki pocztowej  <br/> |Potencjalnie ograniczone.  <br/> Jeśli podczas przenoszenia dzierżawy użytkownik A i skrzynka pocztowa B nie mają tego samego geolokalizacji, użytkownik A nie może otworzyć folderu Skrzynka pocztowa B w programie Outlook Web Access, jeśli użytkownik A ma uprawnienia tylko do określonego folderu w skrzynce pocztowej B.  <br/> Aby dodać folder udostępniony, kliknij prawym przyciskiem myszy nazwę użytkownika w lewym panelu nawigacyjnym i wybierz pozycję **Dodaj folder udostępniony**.  <br/> |
|Użytkownik z pełnymi uprawnieniami do skrzynki pocztowej innej skrzynki pocztowej  <br/> |W pełni obsługiwane.  <br/> Jeśli użytkownik A ma uprawnienie "Pełny dostęp" do skrzynki pocztowej B, użytkownik A może kliknąć folder udostępniony w lewym panelu nawigacyjnym w programie Outlook Web Access, aby otworzyć okno zawierające skrzynkę pocztową B.  Użytkownik może podczas przenoszenia otworzyć udostępnioną skrzynkę pocztową przy Outlook Web Access bez negatywnego wpływu na to. To ograniczenie dotyczy tylko udostępniania na poziomie folderu w skrzynce pocztowej.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Gdy SharePoint Online jest przenoszony, dane dla następujących usług również są przenoszone:
  
- OneDrive dla Firm
    
- Microsoft 365 wideo
    
- Office w przeglądarce
    
- Aplikacje usługi Microsoft 365 dla przedsiębiorstw
    
- Visio Pro dla Microsoft 365
    
Po zakończeniu przenoszenia danych SharePoint Online możesz zobaczyć niektóre z poniższych efektów.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 usług wideo

- Przenoszenie danych do klipu wideo trwa dłużej niż przeniesienie pozostałej zawartości w aplikacji SharePoint Online.
    
- Po SharePoint zawartości online będzie dostępny ramy czasowe, w których nie będzie można odtwarzać klipów wideo.
    
- Usuwamy transkodowane kopie z poprzedniego centrum danych i ponownie je transkoduje w nowym centrum danych.
    
### <a name="search"></a>Wyszukiwanie

W trakcie przenoszenia twoich danych SharePoint Online przeprowadzamy migrację Indeksu wyszukiwania i ustawień wyszukiwania do nowej lokalizacji. Dopóki **nie ukończymy** przenoszenia Twoich danych SharePoint Online, będziemy nadal obsługiwać Twoich użytkowników z indeksu w oryginalnej lokalizacji. Po przeniesieniu danych z usługi SharePoint online wyszukiwanie automatycznie rozpocznie przeszukiwanie zawartości w nowej lokalizacji. Od tego momentu i dalej będziemy obsługiwać Twoich użytkowników z migrowanego indeksu. Zmiany zawartości, które wystąpiły po migracji, nie są uwzględniane w migrowanym indeksie, dopóki przeszukiwanie ich nie odbierze. Większość klientów nie zauważyć, że wyniki są mniej świeże od razu po zakończeniu przenoszenia danych usługi SharePoint Online, ale niektórzy klienci mogą mieć ograniczoną freshness w pierwszych 24–48 godzinach 
  
Dotyczy to następujących funkcji wyszukiwania:
  
- Wyniki wyszukiwania i składniki Web Part: Wyniki nie zawierają zmian, które wystąpiły po migracji, dopóki przeszukiwanie ich nie odbierze. 
    
- Delve: Delve nie uwzględnia zmian, które wystąpiły po migracji, dopóki przeszukiwanie ich nie odbierze.
    
- Raporty popularności i wyszukiwania dla witryny: Liczba raportów usługi Excel w nowej lokalizacji obejmuje tylko liczby z migrowanych raportów użycia, które zostały uruchomione po zakończeniu przenoszenia danych usługi SharePoint Online. Wszelkie zliczenia po pośrednim okresie są utracone i nie można ich odzyskać. Okres ten zwykle wynosi kilka dni. Dla niektórych klientów mogą wystąpić krótsze lub dłuższe straty.
    
- Portal wideo: Statystyki wyświetlania w portalu wideo zależą od statystyk raportów Excel, w związku z tym liczba wyświetleń oraz statystyki w portalu wideo są utracone w tym samym czasie co w przypadku raportów Excel wideo.
    
- Zbierania elektronicznych materiałów dowodowych: Elementy, które zmieniły się podczas migracji, nie są wyświetlane, dopóki przeszukiwanie nie przechowa tych zmian.
    
- Ochrona przed utratą danych (DLP): Zasady nie są wymuszane na elementach, które zmieniają się, dopóki przeszukiwanie nie przechowa tych zmian.

W ramach migracji region domyślny zmieni się i cała nowa zawartość będzie przechowywana w miejscu w nowym regionie domyślnym. Istniejąca zawartość będzie poruszać się w tle bez wpływu na Ciebie przez maksymalnie 90 dni od pierwszej zmiany w lokalizacji danych usługi SharePoint Online w centrum administracyjnym.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Karta Pliki

Po zakończeniu migracji karta Pliki może zająć więcej czasu (do 7 sekund) całkowitego załadowania, gdy użytkownik próbuje jej użyć po raz pierwszy. 

### <a name="read-only-period"></a>Okres tylko do odczytu

Teams czatów przenosi każdy wątek z osobna.  Podczas przenoszenia wątek jest blokowany w stanie tylko do odczytu, który trwa kilka sekund na wątek.  Wątki pozostają dostępne podczas migracji.

## <a name="skype-for-business"></a>Skype dla firm

Skype dla firm są już niedostępne.  [Skype dla firm online zostaną wycofane](/lifecycle/announcements/skype-for-business-online-retirement) 31 lipca 2021 r. Po tym czasie usługa nie będzie już dostępna. 
  
## <a name="related-topics"></a>Tematy pokrewne 
 
[Jak zażądać przeniesienia danych](request-your-data-move.md)
    
[Ogólne często zadawane pytania dotyczące przenoszenia danych](data-move-faq.yml)
  
[Nowe lokalizacje geograficzne centrum danych dla Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Usługi platformy Azure według regionów](https://azure.microsoft.com/regions/)
