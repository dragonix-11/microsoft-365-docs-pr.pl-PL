---
title: opcje migracji SharePoint 2007 r. do rozważenia
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Ten artykuł zawiera informacje dla użytkowników korzystających z programu SharePoint Server 2007, aby ułatwić im planowanie uaktualnienia.
ms.openlocfilehash: 044bfce8ea64233950fa291c72896f36531d206e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090756"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>opcje migracji SharePoint 2007 r. do rozważenia

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft SharePoint 2007 i SharePoint Server 2007 osiągnęły koniec wsparcia. Nadszedł czas na uaktualnienie! Ten artykuł zawiera informacje o opcjach migracji.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Typowe strategie uaktualniania dla SharePoint

Istnieje wiele metod uaktualniania środowiska serwera SharePoint. Jeśli masz farmę Microsoft Office SharePoint Server 2007, oto kilka przykładów metod uaktualniania:
  
- Dołączanie bazy danych
    
- Uaktualnianie równoległe
    
- Uaktualnienie w miejscu
    
- Uaktualnianie hybrydowe (w miejscu z odłączonymi bazami danych / oddzielnym dołączaniem bazy danych)
    
- SharePoint hybrydy (łączenie w trybie online z lokalnymi SharePoint)
    
- Ręczne przenoszenie danych między zbiorami witryn lub bibliotekami
    
- Uaktualnienie kreatora FastTrack do Microsoft 365 ([doradca wdrażania usługi SharePoint Online](https://aka.ms/spoguidance))
    
- Interfejs API migracji do usługi SharePoint Online (SPO) w Microsoft 365
    
Co działa najlepiej dla Ciebie?
  
Twoja wiedza na temat tego, co robi twoja farma i do której służy, jest siłą taktyczną, jeśli chodzi o uaktualnienie. Sposób, w jaki użytkownicy korzystają z farmy SharePoint, pomoże Ci wybrać spośród twoich opcji.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 ma również stopniowe uaktualnienie nieobjęte tutaj. Aby wyświetlić listę artykułów dotyczących uaktualniania specyficznych dla poszczególnych kroków, zobacz [plan zakończenia pomocy technicznej programu SharePoint Server 2007](sharepoint-2007-end-of-support.md). 
  
Pamiętaj, aby sprawdzić [cykl życia produktu](https://support.microsoft.com/lifecycle/search) i wymagania systemowe niezależnie od wersji SharePoint, do której się uaktualniasz. Dzięki temu będziesz wiedzieć, kiedy będzie konieczne następne uaktualnienie (na przykład jeśli wstrzymasz działanie starszego produktu, takiego jak SharePoint Server 2010, aby zaplanować więcej uaktualnień, upewnij się, że znasz datę zakończenia wsparcia technicznego) i upewnij się, że masz sprzęt, który obsługuje twój plan. 
  
Jeśli planujesz przeniesienie niektórych lub wszystkich witryn SharePoint do Microsoft 365 w chmurze, nadszedł czas, aby dodać do zakładki link do [Microsoft 365 i Office 365 opisów usług](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Aby dowiedzieć się więcej na temat funkcji usługi SharePoint Online i ich różnic między lokalnymi SharePoint Server, potrzebne są opisy usługi. Uaktualnij farmy funkcjonalne Microsoft Office SharePoint Server 2007. Jeśli instalacja ma uszkodzone lokacje, popraw je przed uaktualnieniem.
  
## <a name="a-note-about-managing-risk"></a>Uwaga dotycząca zarządzania ryzykiem

Metody takie jak "side-by-side" są ważne w schemacie logiki uaktualniania. Podczas uaktualniania należy zachować farmę Microsoft Office SharePoint Server 2007, ale na nowym sprzęcie utworzysz farmę w następnej wersji (SharePoint Server 2010). Pomaga to na trzy sposoby:
  
1. Istnieje miejsce do wykonywania kopii zapasowych baz danych Microsoft Office SharePoint Server 2007 w celu ich oddzielnego uaktualnienia przy użyciu dołączania bazy danych.
    
2. Jeśli ustalisz, że w farmie Microsoft Office SharePoint Server 2007 jest używanych tylko kilka bibliotek dokumentów krytycznych i inne informacje, możesz ręcznie przenieść dane z serwera Microsoft Office SharePoint Server 2007 do SharePoint  Serwer 2010 lub przeprowadź tylko określone witryny i sieci Web do następnej wersji (co może ułatwić zadanie).
    
3. Tym mniej robisz dla farmy serwerów Microsoft Office SharePoint Server 2007, bezpośrednio, tym bezpieczniejsze są dane, które farma zawiera podczas uaktualniania.
    
Metody takie jak In-Place uaktualnienia będą działać bezpośrednio w farmie Microsoft Office SharePoint Server 2007, co daje mniej łatwych opcji porzucenia ścieżki i rozpoczęcia od nowa dziewiczego środowiska. W miarę możliwości należy utworzyć pewne środki bezpieczeństwa (takie jak tworzenie i testowanie kopii zapasowych oryginalnego środowiska). Jeśli na przykład farma Microsoft Office SharePoint Server 2007 jest wirtualna i jest zduplikowana na potrzeby tworzenia kopii zapasowych i przywracania, utwórz kopię zapasową i przywróć większość bieżących baz danych przed oknem usługi w celu uaktualnienia. Wiedząc, że masz możliwość przywrócenia kopii zapasowych bazy danych, nie tylko zapewni ci to bezpieczeństwo awaryjne, ale także zapewni ci spokój.
  
> [!TIP]
> Istnieją dokumenty dotyczące najlepszych rozwiązań dotyczących uaktualniania [serwerów Microsoft Office SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)), [SharePoint Server 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) i [SharePoint Server 2016](/SharePoint/upgrade-and-update/best-practices-for-upgrade). Możesz również wyszukać [partnerów firmy Microsoft](https://partnercenter.microsoft.com/pcv/search), którzy mają doświadczenie z uaktualnieniami lub migracjami Microsoft 365. 
  
## <a name="make-your-plan"></a>Utwórz plan

Jeśli musisz przeprowadzić uaktualnienie, potrzebujesz planu, a jeden rozmiar nie pasuje do wszystkich w tych przypadkach. Plan może być tak prosty jak "Tworzenie subskrypcji Microsoft 365 przy użyciu usługi SharePoint Online, rejestrowanie domeny i przekierowywanie osób w celu zapisania tam plików". I może nie być. Ta decyzja należy do Ciebie i zależy od tego, czego naprawdę potrzebujesz Ty i Twoi użytkownicy.
  
> [!NOTE]
> Uruchamianie oprogramowania, którego cykl życia się zakończył, jest ryzykowne. Produkty, które nie są obsługiwane, nie są już poprawiane po znalezieniu problemów. Oznacza to również, że w przypadku wystąpienia nowych zagrożeń bezpieczeństwa nie będzie żadnych poprawek ani poprawek zabezpieczeń, ponieważ produkty z końcem cyklu życia nie są już obsługiwane. Proszę uniknąć tej sytuacji! 
  
### <a name="first-know-your-farm"></a>Najpierw poznaj swoją farmę

Podczas uaktualniania podejmowanie decyzji powinno być oparte na tym, co farma robi dla twojej organizacji. Jakie potrzeby spełnia? Jaka jest jej rola? Każda farma w firmie może mieć inną rolę. Niektóre farmy SharePoint mogą mieć *krytyczne znaczenie*, niektóre mogą być archiwami plików — w celu zapewnienia bezpieczeństwa. Jeśli farma wypełnia wiele ról jednocześnie, może być konieczne określenie, jakie są zbiory witryn, sieci Web, a nawet biblioteki dokumentów, jakie są dostosowania i jak ważne są. Analizowanie danych na tym poziomie może wydawać się dużo pracy, ale pozwala zaoszczędzić czas i nakład pracy na opanowanie domeny przed uaktualnieniem lub migracją. Gdy poznasz wszystkie ruchome części i najważniejsze bity, będziesz również wiedzieć, co przerosło i możesz zostawić. Ta wiedza przyniesie korzyści tylko w przyszłości. 
  
Co mówią użytkownicy, jest najważniejsze w farmie serwera SharePoint?
  
- Wbudowane funkcje SharePoint
    
- Duży korpus danych (na przykład archiwum plików)
    
- Dostępność
    
- Krytyczne aplikacje, składniki Web Part lub dokumenty w farmie (farma o krytycznym znaczeniu)
    
- Standardy zgodności zostały spełnione
    
- Dostosowania
    
Jeśli uruchomisz coś istotnego dla swojej firmy z farmy SharePoint, załóżmy, że działa ona jak duży katalog krytycznych danych dotyczących wymagań dotyczących usługi klienta, możesz umieścić znacznik obok pozycji "Aplikacje krytyczne", ale także "Dostępność" — oznacza to, że twoja firma będzie miała wpływ, jeśli nie będzie można przez jakiś czas korzystać z SharePoint. Podobnie możesz sprawdzić opcję "Dostosowania", ponieważ usługi krytyczne, które oferuje twoja farma, są oparte na kodzie niestandardowym, definicjach witryn lub wielu dostosowaniach, które współpracują ze sobą.
  
Jeśli SharePoint spełniać te potrzeby bez twojego zaangażowania poza korzystaniem z wbudowanych elementów oprogramowania, a ty ogólnie aktualizujesz je i przeprowadzasz normalną administrację i konserwację, być może wybrałeś "wbudowaną SharePoint" - może to być również powód, dla którego siedzisz w starszej wersji SharePoint. Innymi słowy, to już robi to, czego potrzebujesz i nie trzeba było uaktualniać do tej pory, na Microsoft Office SharePoint Server 2007 koniec wsparcia.
  
Gdy punktujesz te elementy, tworzysz kryteria uaktualnienia. Innymi słowy, każde uaktualnienie musiałoby spełniać ten pasek, aby był brany pod uwagę. Dzięki temu można wykluczyć metody, które obecnie nie pasują do Twoich potrzeb.
  
### <a name="a-simple-sample-plan"></a>Prosty przykładowy plan

Może być konieczne szersze porozumienie z kierownictwem i innymi administratorami w sprawie ścieżki, którą wykona SharePoint uaktualnienia. SharePoint Administratorzy serwera często współpracują z administratorami Microsoft SQL Server, współpracują z zespołami ds. sieci i zabezpieczeń i nie tylko. W przypadku wielu uczestników projektu może być konieczne utworzenie umowy dotyczącej planu uaktualniania i migracji lub dostosowanie go. Jeśli na przykład zmigrujesz dane tak, aby część firmy używa usługi SharePoint Online w Microsoft 365, prawdopodobnie konieczne będzie dostrajanie wydajności lub testowanie w sieci. Zespoły, których dotyczy problem, powinny być powiadamiane z wyprzedzeniem.
  
W moim prostym przykładzie przedstawiam propozycję administratora SharePoint, a następnie wyświetlam listę planów uzgodnionych przez wszystkie zainteresowane strony. Aby uzyskać jasność, udokumentowaj swoje umowy i decyzje.
  
Plan rozpoczyna się po szczegółowej analizie farmy i próbuje zidentyfikować rolę farmy, punkty bólu i inne ważne informacje, które doprowadzą do zawężenia niektórych opcji uaktualniania. Następnie administrator SharePoint składa propozycję uaktualnienia, a uczestnicy projektu uzgadniają plan działania.
  
Moja "najważniejsza" lista punktowana:
  
- Dostępność, funkcje wbudowane w SharePoint i standardy zgodności.
    
- Większość danych znajduje się w trzech zbiorach witryn, a jeden obszar roboczy spotkania jest używany przez zespół deweloperów, który jest ważny i intensywnie używany w wielu strefach czasowych na całym świecie.
    
- Istnieje 17 innych witryn, które są powszechnie używane.
    
- Dwie biblioteki dokumentów (obszar roboczy spotkania i dokumenty w głównym zbiorze witryn) są największe (po ponad 8000 dokumentów). Mamy dużą liczbę zarchiwizowanych dokumentów i list z załącznikami arkuszy kalkulacyjnych.
    
- Istnieje 14 list bibliotek, które mają poufne dane, które muszą pozostać w zgodności.
    
- Musimy mieć możliwość przeprowadzania blokad i e-odnajdywania, gdziekolwiek się udamy.
    
- Niektóre z tych danych muszą pozostać w środowisku lokalnym ze względu na reguły programu InfoSec.
    
 **Moje opcje uaktualniania i migracji:**
  
| Tak | Nie |
|:-----|:-----|
|Uaktualnianie baz danych za pomocą dołączania bazy danych  <br/> |Uaktualnienie w miejscu  <br/> |
|Uaktualnianie z farmami obok siebie  <br/> |Uaktualnianie hybrydowe  <br/> |
|Interfejs API migracji do adresu SPO w Microsoft 365 (w przypadku danych witryny osobistej)  <br/> |SharePoint hybrydowe (jeszcze nie potrzebne)  <br/> |
|Niektóre ręczne migracje danych do usługi SharePoint Online w przypadku danych krytycznych  <br/> |Uaktualnienie kreatora FastTrack do Microsoft 365  <br/> |
   
 **Mój proponowany plan:**
  
Uaktualnij środowisko lokalne z wersjami SharePoint obok siebie, niektóre zwirtualizowane, abyśmy mogli najpierw uaktualnić bazy danych. Przejdź z SharePoint 2007 r. do SharePoint 2010 r. Administratorzy i deweloperzy testują wynikowe farmy. Użytkownicy testują wynikowe farmy. W tym czasie rozwiązano wszelkie problemy z zatrzymywaniem pokazów. Ponownie, obok siebie, uaktualnij bazy danych SharePoint 2010 do SharePoint 2013. Test. Test użytkownika/pilotaż. W tym czasie rozwiązano wszelkie problemy z zatrzymywaniem pokazów.
  
- Zastanów się, czy federacyjna hybryda wyszukiwania ze spo spełnia Twoje potrzeby.
    
- Rozważ [FastTrack pomoc](https://fasttrack.microsoft.com), jeśli chcesz przeprowadzić uaktualnienie do usługi SharePoint Online. 
    
- Ustal, czy jakiekolwiek zbiory witryn mogą być odciążane do subskrypcji Microsoft 365. (Microsoft 365 spełnia wiele [standardów zgodności](/compliance/regulatory/offering-home). Microsoft 365 ma [elektroniczne dowody](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) i [może wykonywać](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) blokady za pośrednictwem Centrum zgodności). 
    
W przeciwnym razie kontynuuj uaktualnienie równoległe do SharePoint Server 2016.
  
> [!NOTE]
> Między zaleceniami administratorów planującym uaktualnienie a rzeczywistym procesem są konwersacje, które odbywają się z innymi uczestnikami projektu, na których opiera się uaktualnienie. Na przykład czasami ekonomia zmusza administratorów do zmiany planów. Niezależnie od ostatecznej decyzji należy udokumentować, jaki jest uzgodniony plan, idąc dalej. Może to wyglądać mniej więcej tak: 
  
 **Mój plan działania:**
  
Lokalnie używamy środowiska wirtualnego do tworzenia domyślnych SharePoint Server 2010 i 2013. SharePoint Server 2016 zostanie utworzony na nowym sprzęcie, który spełnia wymagania systemowe na rok 2016. Wykonamy dołączanie baz danych w celu uaktualnienia baz danych z SharePoint 2007 r. do wszystkich wersji między nim a serwerem SharePoint Server 2016. Podstawowe dostosowania są obecnie ponownie tworzone i testowane w środowisku SharePoint Server 2016, jeśli funkcje natywne nie spełniają jeszcze naszych potrzeb. Jeśli się powiedzie, będziemy mieć lokalną farmę na nowym sprzęcie z uaktualnianą bazą danych i mniejszą liczbą dostosowań. Uaktualnione bazy danych zawartości zostaną dołączone do nowych zbiorów witryn w programie SharePoint Server 2013, test, test użytkownika/pilotaż, a następnie wykonamy rozszerzenie DNS do nowego środowiska SharePoint Server 2016 na żywo.
  
- Nie będziemy teraz uwzględniać federacyjnej hybrydy między serwerem SharePoint Server 2016 i SharePoint Online.
    
- Szacuje się, że 35% naszych witryn można przekształcić w nowe witryny SPO z domenami próżności lub ostatecznie stać się OneDrive dla Firm magazynu. Szukasz innych możliwości konwertowania witryn lub kierowania nowych witryn do sieci SPO.
    
- Część tej części migracji będzie wykonywana ręcznie przez przeciąganie i upuszczanie do OneDrive dla Firm witryn osobistych, a niektóre według interfejsu API migracji.
    
Bardziej szczegółowe kroki lub kilka linków do konkretnych kierunków uaktualniania powinny być zgodne z planem. Komputer MOSS 2007 nie powinien zostać zlikwidowany, a środowiska wirtualne powinny być utrzymywane w celu porównania; Jednak uaktualnienie zostanie ukończone po przekierowaniu użytkowników do SharePoint Server 2016.
  
Często głównymi czynnikami w wyborze metody są całkowity koszt uaktualnienia i koszt w czasie (więcej informacji na ten temat można znaleźć w artykule SharePoint Migration Roadmap (Plan migracji SharePoint). Jednak planowanie z wyprzedzeniem będzie korzystne w ustalaniu oczekiwań, mądrym wyborze i określaniu, jak będzie wyglądał sukces.
  
## <a name="related-links"></a>Linki pokrewne

[Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Wyszukiwanie zasad cyklu życia i cyklu życia firmy Microsoft](https://support.microsoft.com/lifecycle)
  
[Wyszukaj partnerów firmy Microsoft, którzy mogą pomóc w uaktualnianiu lub migracji](https://partnercenter.microsoft.com/pcv/search)
