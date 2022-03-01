---
title: SharePoint migracji do 2007 r. do rozważenia
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Ten artykuł zawiera informacje dla użytkowników korzystających z programu SharePoint Server 2007, które ułatwiają im zaplanowanie uaktualnienia.
ms.openlocfilehash: 9c1c4c90443b632b490ac7a510394f367f688fca
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019256"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint migracji do 2007 r. do rozważenia

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Firmy Microsoft SharePoint 2007 i SharePoint Server 2007 zakończyły wsparcie techniczne. Czas na uaktualnienie! Ten artykuł zawiera informacje o dostępnych opcjach migracji.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Typowe strategie uaktualniania dla SharePoint

Istnieje wiele metod uaktualniania środowiska programu SharePoint Server. Jeśli masz farmę programu Microsoft Office SharePoint Server 2007, oto kilka przykładów metod uaktualniania:
  
- Dołączanie baz danych
    
- Uaktualnianie obok siebie
    
- Uaktualnianie w miejscu
    
- Uaktualnianie hybrydowe (w miejscu z odłączanymi bazami danych / osobne dołączanie baz danych)
    
- SharePoint hybrydowe (łączenie w trybie online z lokalnym SharePoint)
    
- Ręczne przenoszenie danych między zbiorami witryn lub bibliotekami
    
- FastTrack uaktualnianie kreatora do Microsoft 365 ([SharePoint w zakresie wdrażania online](https://aka.ms/spoguidance))
    
- Interfejs API migracji do usługi SharePoint Online (SPO) w programie Microsoft 365
    
Jaka jest najlepsza dla Ciebie?
  
Twoja wiedza na temat tego, co robi farma i do czego jest używana, stanowi taktyczną siłę w zakresie uaktualnienia. Sposób korzystania z farmy SharePoint pomoże Ci wybrać jedną z dostępnych opcji.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 jest również stopniowo uaktualnianie, które nie zostało tu objęte. Aby wyświetlić listę artykułów dotyczących uaktualniania poszczególnych kroków, zobacz przewodnik po zakończeniu SharePoint [Server 2007 — przewodnik](sharepoint-2007-end-of-support.md). 
  
Pamiętaj, aby sprawdzić [wymagania dotyczące cyklu życia i](https://support.microsoft.com/lifecycle/search) systemu produktu SharePoint, do których uaktualniasz. Jest to potrzebne, aby wiedzieć, kiedy będzie konieczne następne uaktualnienie (na przykład jeśli zatrzymasz się na starszym produkcie, takim jak SharePoint Server 2010, aby zaplanować kolejne uaktualnienia, upewnij się, że znasz datę zakończenia wsparcia technicznego) i aby mieć pewność, że masz sprzęt, który obsługuje Twój plan. 
  
Jeśli planujesz przejście niektórych lub wszystkich witryn usługi SharePoint do usługi Microsoft 365 w chmurze, na tym etapie należy dodać zakładkę do linku do opisów usług [Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Opisy usług będą potrzebne, aby dowiedzieć się więcej SharePoint online i ich różnic w poszczególnych funkcjach niż w lokalnym SharePoint Server. Uaktualnij farmy Microsoft Office SharePoint Server 2007. Jeśli twoja instalacja ma uszkodzone witryny, napraw je przed uaktualnieniem.
  
## <a name="a-note-about-managing-risk"></a>Uwaga na temat zarządzania ryzykiem

Metody takie jak "metoda obok siebie" są ważne w schemacie logiki uaktualnienia. Podczas uaktualniania obok siebie utrzymujesz swoją farmę programu Microsoft Office SharePoint Server 2007, ale tworzysz farmę następnej wersji (SharePoint Server 2010) na nowym sprzęcie. Pomaga to na trzy sposoby:
  
1. Masz miejsce na wykonywanie kopii zapasowych baz danych programu Microsoft Office SharePoint Server 2007 w celu ich oddzielnego uaktualnienia za pomocą dołączania baz danych.
    
2. Jeśli ustalisz, że tylko kilka krytycznych bibliotek dokumentów i innych informacji jest w użyciu w farmie programu Microsoft Office SharePoint Server 2007, możesz ręcznie przenieść dane z programu Microsoft Office SharePoint Server 2007 do programu SharePoint  Server 2010 lub przejmij do następnej wersji tylko konkretne witryny i sieci Web (co może ułatwić Ci pracę).
    
3. Tym mniej będziesz bezpośrednio robisz na farmie serwerów programu Microsoft Office SharePoint Server 2007, tym bezpieczniejsze są dane, które ta farma zawiera podczas uaktualniania.
    
Metody takie In-Place uaktualnianie będą działać bezpośrednio na farmie programu Microsoft Office SharePoint Server 2007, zapewniając mniej łatwych opcji porzucenia ścieżki i rozpoczęcia jej ponownie w dziewiczym środowisku. Na tyle, na ile to możliwe, należy tworzyć zabezpieczenia (na przykład tworzyć i testować kopie zapasowe pierwotnego środowiska). Jeśli na przykład Twoja farma programu Microsoft Office SharePoint Server 2007 jest wirtualna i zostanie zduplikowana w celu tworzenia kopii zapasowej i przywracania, to należy utworzyć kopię zapasową najbardziej aktualnych baz danych przed oknem usługi dla uaktualnienia i przywrócić je. Świadomość, że masz możliwość przywracania kopii zapasowych baz danych, nie tylko zapewni Ci opcję awaryjną, ale także spokój ducha.
  
> [!TIP]
> W przypadku usług [Microsoft Office SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)), [SharePoint Server 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) i [SharePoint Server 2016](/SharePoint/upgrade-and-update/best-practices-for-upgrade) istnieją dokumenty najlepszych rozwiązań. Możesz również wyszukiwać partnerów firmy [Microsoft](https://partnercenter.microsoft.com/pcv/search), którzy mają doświadczenie w uaktualnień lub Microsoft 365 migracji. 
  
## <a name="make-your-plan"></a>Planowanie

Jeśli musisz uaktualnić plan, a w tym przypadku jednowymiarowy nie jest odpowiedni dla wszystkich. Twój plan może być tak prosty, jak: "Utwórz subskrypcję usługi Microsoft 365 w u rejestratorze SharePoint Online, zarejestruj domenę i przekieruj użytkowników, aby tam zapisywali swoje pliki". I może nie tak być. Ta decyzja należy do Ciebie i jest ona naprawdę potrzebna Dla Ciebie i Twoich użytkowników.
  
> [!NOTE]
> Uruchamianie oprogramowania, którego cykl życia został zakończony, jest ryzykowne. Produkty bez pomocy technicznej nie są poprawiane w przypadku ich problemów. Oznacza to również, że w przypadku pojawiania się nowych zagrożeń bezpieczeństwa nie będą pojawiać się poprawki zabezpieczeń ani poprawki, ponieważ produkty o zakończeniu cyklu życia nie są już obsługiwane. Unikaj takich sytuacji. 
  
### <a name="first-know-your-farm"></a>Po pierwsze, poznaj swoją farmę

Podejmowanie decyzji podczas uaktualniania powinno być oparte na tym, co farma robi dla organizacji. Jakie potrzeby spełnia? Jaka jest jej rola? Każda farma w Twojej firmie może mieć inną rolę. Niektóre farmy SharePoint być *krytyczne*, niektóre mogą być archiwami plików w celu zachowania bezpieczeństwa. Jeśli natomiast farma wypełnia jednocześnie wiele ról, może być konieczne wiedzieć, jakie zbiory witryn, sieci Web, a nawet biblioteki dokumentów są dostępne, wszelkie dostosowania i jak ważne są te zbiory witryn. Analizowanie danych na tym poziomie może wydawać się pracą, ale opanowanie domeny przed jej uaktualnieniem lub migracją pozwala zaoszczędzić czas i energię. Gdy już poznasz wszystkie ruchome elementy i najważniejsze elementy, będziesz wiedzieć, co jest niezapomniane i co można zostawić za sobą. Ta wiedza w przyszłości będzie tylko dla Ciebie korzyścią. 
  
Co zatem jest najważniejsze dla użytkowników w farmie programu SharePoint Server?
  
- Wbudowane funkcje SharePoint funkcji
    
- Duży corpus danych (na przykład archiwum plików)
    
- Dostępność
    
- Krytyczne aplikacje, składników Web Part lub dokumenty na farmie (farma o znaczeniu krytycznym)
    
- Spełnione standardy zgodności
    
- Dostosowania
    
Jeśli na farmie usługi SharePoint jest uruchamiana coś istotnego dla Twojej firmy, na przykład działa ona jak duży katalog najważniejszych danych dotyczących wymagań usług klienckich, możesz zaznaczyć pole wyboru obok "Krytyczne aplikacje", ale także "Dostępność", czyli na Twoją firmę będzie mieć wpływ, jeśli przez jakiś czas nie będzie można używać programu SharePoint. Podobnie możesz sprawdzać "Dostosowania", ponieważ krytyczne usługi oferowanych przez farmę są oparte na niestandardowym kodzie, definicjach witryn lub wielu dostosowanych ze sobą dostosowaniach.
  
Jeśli program SharePoint spełnił te potrzeby bez angażowania użytkownika za pośrednictwem korzystania z wbudowanych funkcji oprogramowania i ogólnie go aktualizował oraz przeprowadzał normalne administrowanie i konserwację, użytkownik mógł wybrać "Wbudowane oprogramowanie SharePoint" — może to być również powód pracy przy starszej wersji programu SharePoint. Oznacza to, że po zakończeniu obsługi programu Microsoft Office SharePoint Server 2007 ta już działa i uaktualnianie nie było konieczne.
  
Po utworzeniu listy punktowanej należy utworzyć kryteria dla uaktualnienia. Innymi słowy, każde uaktualnienie musi spełniać ten pasek, aby można było je rozważyć. W ten sposób możesz wykluczyć metody, które obecnie nie są odpowiednie do Twoich potrzeb.
  
### <a name="a-simple-sample-plan"></a>Prosty przykładowy plan

Ścieżka uaktualnienia SharePoint może wymagać szerszego porozumienia z kierownictwem i innymi administratorami. SharePoint administratorzy serwerów często współpracują Microsoft SQL Server administratorami, pracują z zespołami sieci i zabezpieczeń oraz nie tylko. Jeśli uczestników projektu jest wielu, może być konieczne kompilowanie lub dostosowywanie planu uaktualniania i migracji. Jeśli na przykład przeprowadzasz migrację danych, tak aby część firmy korzysta z usługi SharePoint Online w programie Microsoft 365, prawdopodobnie trzeba będzie przeprowadzić dostosowywanie lub testowanie wydajności w sieci. Zespoły, których to dotyczy, powinny zostać poinformowane z wyprzedzeniem.
  
W moim prostym przykładzie pokażę propozycję SharePoint administratora, a następnie wypisuję plan, na który zgodzili się wszyscy uczestnicy projektu. W celu zachowania przejrzystości dokumentuj uzgodnienia i decyzje.
  
Plan jest rozpoczynany po szczegółowej analizie farmy i stanowi próbę zidentyfikowania roli farmy, problemów i innych ważnych informacji, które doprowadzą do zawężenia opcji uaktualnienia. Następnie administrator usługi składa propozycję uaktualnienia, SharePoint uczestnicy projektu uzgadniają plan działania.
  
Moja "najważniejsze" lista punktowana:
  
- Dostępność, wbudowane funkcje do SharePoint zgodności i standardy zgodności.
    
- Większość danych znajduje się w trzech zbiorach witryn z jednym obszarem roboczym spotkania używanym przez zespół deweloperów i używanym w wielu strefach czasowych na całym świecie.
    
- Istnieje 17 innych witryn, które są powszechnie używane.
    
- Dwie biblioteki dokumentów (Obszar roboczy spotkania i Dokumenty w głównym zbiorze witryn) są największe (ponad 8000 dokumentów każda). Mamy dużą liczbę zarchiwizowane dokumenty i listę z załącznikami arkuszy kalkulacyjnych.
    
- Istnieje 14 list bibliotek z poufnymi danymi, które MUSZĄ zachować zgodność.
    
- MUSIMY mieć możliwość tworzenia blokady i z odnajdowania elektronicznego w każdym miejscu.
    
- Niektóre z tych danych MUSZĄ pozostać lokalne ze względu na reguły InfoSec.
    
 **Dostępne są opcje uaktualnienia i migracji:**
  
| Tak | Nie |
|:-----|:-----|
|Uaktualnianie baz danych za pomocą dołączania baz danych  <br/> |Uaktualnianie w miejscu  <br/> |
|Uaktualnianie za pomocą farm obok siebie  <br/> |Uaktualnianie hybrydowe  <br/> |
|Interfejs API migracji do usługi SPO Microsoft 365 sieci Web (w przypadku danych witryn osobistych)  <br/> |SharePoint hybrydowe (jeszcze nie jest potrzebne)  <br/> |
|Niektóre ręczne migracje danych do usługi SharePoint Online w przypadku krytycznych danych  <br/> |FastTrack uaktualnianie kreatora do Microsoft 365  <br/> |
   
 **Mój zaproponowany plan:**
  
Uaktualnienie lokalne, z wersjami programu SharePoint obok siebie (niektóre zwirtualizowane), aby można było najpierw uaktualnić bazy danych. Miń od SharePoint 2007 do SharePoint 2010. Administratorzy i twórcy testujemy farmy wynikowe. Użytkownicy testuje farmy wynikowe. W tym czasie rozwiąż wszelkie problemy zatrzymania pokazu. Również uaktualnienie baz danych programu SharePoint 2010 do wersji 2013 SharePoint 2013. Przetestuj. Test użytkownika/pilotaż. W tym czasie rozwiąż wszelkie problemy zatrzymania pokazu.
  
- Zastanów się, czy wyszukiwanie hybrydowe federowane z spo spełnia Twoje potrzeby.
    
- Rozważ [FastTrack,](https://fasttrack.microsoft.com) jeśli chcesz uaktualnić usługę do usługi SharePoint online. 
    
- Określ, czy jakieś zbiory witryn można załadować do Microsoft 365 subskrypcji. (Microsoft 365 spełnia wiele [standardów zgodności](/compliance/regulatory/offering-home). Microsoft 365 ma [możliwość zbierania elektronicznych materiałów dowodowych](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) i [zbierania elektronicznych](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) materiałów dowodowych za pośrednictwem Centrum zgodności). 
    
W przeciwnym razie kontynuuj uaktualnianie do programu SharePoint Server 2016.
  
> [!NOTE]
> Po rekomendacjach wykonanych przez administratorów planujących uaktualnienie i przed rzeczywistym procesem są prowadzone konwersacje z innymi uczestnikami projektu, od których zależy uaktualnienie. Na przykład czasami działania ekonomiczne wymuszają na administratorach zmianę planów. Niezależnie od ostatecznej decyzji, przed terminem należy udokumentować uzgodniony plan. Może on wyglądać podobnie do tego: 
  
 **Mój plan akcji:**
  
Lokalnie korzystamy ze środowiska wirtualnego do tworzenia domyślnych SharePoint Server 2010 i 2013. SharePoint Server 2016 zostanie zbudowany na nowym sprzęcie, który spełnia wymagania systemowe w roku 2016. Dołączymy bazy danych, aby uaktualnić bazy danych z programu SharePoint 2007 do wszystkich wersji między tym i SharePoint Server 2016. Obecnie w środowisku programu SharePoint Server 2016 są ponownie tworzone i testowane podstawowe dostosowania, jeśli funkcje natywne nie spełniają jeszcze naszych potrzeb. Jeśli nam się powiedzie, będziemy mieć farmę lokalną na nowym sprzęcie z uaktualnionymi bazami danych i mniejszą liczbą dostosowań. Dołączymy uaktualnione bazy danych zawartości do nowych zbiorów witryn w programie SharePoint Server 2013, przetestujemy, przetestujemy użytkownika/pilotaż, a następnie przeniesiemy system DNS do nowego środowiska programu SharePoint Server 2016 do użytku na żywo.
  
- Obecnie nie będziemy rozważać federacji hybrydowej między SharePoint Server 2016 i SharePoint Online.
    
- Około 35% naszych witryn można przekształcć w nowe witryny usługi Spo z domenami, które są bardzo ważnymi domenami, lub ostatecznie mogą stać się OneDrive dla Firm magazynami. Poszukamy innych możliwości konwertowania witryn lub przekieruj nowe witryny do usług SPO.
    
- Część tej części migracji będzie ręczna poprzez przeciąganie i upuszczanie w witrynach OneDrive dla Firm, a jeszcze inne za pomocą interfejsu API migracji.
    
Bardziej szczegółowe instrukcje lub linki do konkretnych wskazówek uaktualnienia powinny być zgodne z planem. Nie należy likwidować komputera z programem MOSS 2007, a środowiska wirtualne powinny być zachowywane w celu porównania. jednak uaktualnienie zostanie ukończone, gdy użytkownicy zostaną przekierowani do programu SharePoint Server 2016.
  
Często główną rolę w wybieraniu metody ma całkowity koszt uaktualnienia i czas realizacji (więcej informacji na ten temat znajdziesz w artykule Przewodnik po migracji do usługi SharePoint). Jednak planowanie z wyprzedzeniem w dużym stopniu ułatwi ustalanie oczekiwań, roztropne wybieranie i ustalanie ram, jak będzie wyglądać sukces.
  
## <a name="related-links"></a>Linki pokrewne

[Zasoby pomocne w uaktualnieniu serwerów i klientów programu Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Zasady cyklu życia firmy Microsoft i wyszukiwanie cyklu życia](https://support.microsoft.com/lifecycle)
  
[Wyszukiwanie partnerów firmy Microsoft, którzy mogą pomóc w uaktualnieniu lub migracji](https://partnercenter.microsoft.com/pcv/search)
