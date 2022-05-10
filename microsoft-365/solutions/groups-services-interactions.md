---
title: Grupuje interakcje usług
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Grupuje interakcje usług
ms.openlocfilehash: 64de83690edb96e3bf7a889309c262a92f8e8193
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286346"
---
# <a name="groups-services-interactions"></a>Grupuje interakcje usług

Grupy Microsoft 365 udostępnia wspólną sieć szkieletową dla kilku usług i obciążeń na platformie Microsoft 365 w celu zapewnienia użytkownikom końcowym połączonego środowiska. Zasadniczo istnieje grupa Microsoft 365, która zapewnia:

- Sposób zarządzania członkostwem (Azure AD)
- Miejsce do obsługi wiadomości i konwersacji (Exchange skrzynki pocztowej, Microsoft Teams, Yammer)
- Miejsce przechowywania plików (SharePoint)
- Kalendarz do planowania (Exchange)
- Notes do przechwytywania notatek (OneNote)

W momencie tworzenia grupy aprowizowano również kilka innych zasobów, jednak nie są one widoczne, dopóki nie będą dostępne po raz pierwszy z usługi:

- Tablica do zarządzania zadaniami grupy (Planner)
- Obszar roboczy do raportowania (Power BI)
- Obszar udostępnionych filmów wideo (Microsoft Stream)
- Obszar dla formularzy udostępnionych (Formularze)

W Microsoft 365 inne usługi mogą wchodzić w interakcje z grupami Microsoft 365, aby zapewnić dodatkowe funkcje i możliwości grupowania członków.
Przykłady tego obejmują:

- Power Apps dla aplikacji
- Power Automate dla przepływów pracy
- Project w sieci Web i plan zarządzania projektami opartymi na kaskadach
- Teams konwersacji opartych na kanałach
- Yammer dla interesujących społeczności

## <a name="user-interactions-with-groups"></a>Interakcje użytkowników z grupami

Grupy Microsoft 365 mogą być tworzone i zarządzane z różnych interfejsów, zarówno przez administratorów, jak i użytkowników końcowych. 

### <a name="administrative-experiences"></a>Środowiska administracyjne

Administratorzy mogą tworzyć grupy Microsoft 365 i zarządzać nimi z kilku centrów administracyjnych obciążeń, interfejsów wiersza polecenia, które obsługują skrypty, a także niestandardowych aplikacji współdziałających z interfejs Graph API. Jedynym wyjątkiem jest Yammer grup — które muszą zostać utworzone z poziomu interfejsu internetowego Yammer.

**Ustawienia pokrewne**

W różnych interfejsach administracyjnych, które mogą zarządzać ustawieniami grupy, istnieje kilka nakładających się elementów, o których należy pamiętać.

**Centrum administracyjne platformy Microsoft 365**

W Centrum administracyjne platformy Microsoft 365 dostęp gościa do grup jest domyślnie włączony, podobnie jak możliwość zezwalania właścicielom na dodawanie gości. Nie ma żadnych dodatkowych kontrolek na poziomie organizacji dostępnych dla grup z tego centrum administracyjnego.

**centrum administracyjne Azure AD**

Centrum administracyjne Azure AD oferuje kontrolki dotyczące tego, czy użytkownicy mogą tworzyć grupy, czy przypisywać właścicieli w witrynie Azure Portals, a także ustawienia zasad wygasania i nazewnictwa.

Centrum administracyjne udostępnia również kilka środków kontroli zaproszeń gości, które wykraczają poza Centrum administracyjne platformy Microsoft 365, takie jak możliwość ograniczenia, czy właściciele nie mogą również zapraszać gości

**SharePoint**

SharePoint witryny są tworzone przy użyciu grup zabezpieczeń Właściciel, Członek i Odwiedzający, a pierwsze dwie są zgodne z ich odpowiednikami grupy Microsoft 365. Chociaż członkostwo w witrynach SharePoint Online jest zwykle zarządzane przez skojarzoną grupę Microsoft 365, nie jest to relacja dwukierunkowa. Wszelkie zmiany członkostwa na poziomie grupy Microsoft 365 są odzwierciedlane w SharePoint, jednak jeśli członkostwo zostanie zmienione w grupie SharePoint, nie zostanie to odzwierciedlone w grupie Microsoft 365.

### <a name="user-experiences"></a>Środowiska użytkownika

Użytkownicy końcowi mogą tworzyć grupy z kilku usług w ramach Microsoft 365, a w innych mogą udostępniać tylko grupie.

Następujące usługi umożliwiają tworzenie grup przez użytkowników końcowych:

- Outlook
- Planner
- Project dla sieci Web
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Ograniczenie tworzenia grupy

Typowym podejściem do kontrolowania rozrostu zespołów jest ograniczenie możliwości ich tworzenia przez użytkowników. Można to zrobić tylko przez ograniczenie tworzenia grup. Ma to wpływ na możliwość tworzenia grup z innych usług, jeśli może to być konieczne dla użytkownika końcowego. Grupy Microsoft 365 nie obsługuje możliwości ograniczania tworzenia grup z niektórych aplikacji lub usług przy jednoczesnym umożliwieniu ich innym.

Środowisko ograniczenia tworzenia grupy różni się w zależności od aplikacji i usług:

|Aplikacja lub usługa|Doświadczenie|
|---|---|
|Outlook|**Nowa opcja grupy** zostanie usunięta ze strony Nowe menu na stronie osób|
|Planner|**Nowy plan** wyjaśnia, że tworzenie grupy zostało wyłączone i oferuje dodanie planu do istniejącej grupy|
|Project dla sieci Web i planu działania|**Menu Tworzenie grupy** wyjaśnia, że tworzenie grupy jest ograniczone i sugeruje użycie istniejącej grupy.|
|SharePoint|Nadal można utworzyć witrynę zespołu, która nie jest połączona z grupą.|
|Stream|Opcja **Grupa** nie jest wyświetlana w **menu Utwórz**.|
|Teams|Użytkownik nie może utworzyć zespołu z nową grupą, ale nadal może utworzyć zespół, który korzysta z istniejącej grupy.<br><br>**Przycisk Utwórz zespół** zostanie zastąpiony opcją **Utwórz zespół z grupy**.|
|Yammer|**Opcja Utwórz grupę** zostanie usunięta z głównego obszaru nawigacji Grupy/Społeczności.|

## <a name="services-interactions-with-groups"></a>Interakcje usług z grupami

Zobacz plakat Grupy w Microsoft 365, aby uzyskać informacje na temat różnych typów grup, sposobu ich tworzenia i zarządzania oraz kilku zaleceń dotyczących ładu.

[![Obraz kciuka dla infografiki grup.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf)

[PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx)

Poniższa tabela zawiera omówienie interakcji Grupy Microsoft 365 z różnymi usługami:

|Rezultat|Funkcje|Czy usługa istnieje bez grupy?|Czy usługa może utworzyć grupę?|Czy usunięcie wystąpienia powoduje usunięcie grupy?|
|---|---|---|---|---|
|Azure AD|Członkostwo, kontrolki grupy, goście|Tak|Tak|Tak|
|Exchange|Kalendarz, skrzynka pocztowa|Tak|Tak|Tak|
|Formularzy|Formularza|Tak|Nie|Nie|
|OneNote|Notebook|Tak|Nie|Nie|
|Planner|Tablica zadań|Nie|Tak|Tak|
|aplikacja Power Apps|Aplikacja|Tak|Nie|Nie|
|Power Automate|Przepływu pracy|Tak|Nie|Nie|
|Power BI (klasyczny)|Workspace|Nie|Tak|Tak|
|Power BI (nowy)|Workspace|Tak|Nie|Tak|
|Project dla sieci Web|plan Project|Tak|Tak|Nie|
|Plan rozwoju|Plan rozwoju|Tak|Tak|Nie|
|SharePoint|Witryny|Tak|Tak|Tak|
|Stream|Kanał, wideo|Tak|Tak|Tak|
|Teams|Zespołu|Nie|Tak|Tak|
|Yammer|Grupa|Tak|Tak|Tak|

Chociaż powyższa tabela zawiera ogólne omówienie interakcji grupowych z usługami Microsoft 365, istnieje kilka niuansów i zawiłości, które należy zrozumieć. W poniższych sekcjach bardziej szczegółowo przedstawiono konkretne obciążenia i ich interakcje z grupami.

## <a name="azure-ad"></a>Azure AD

Azure AD zapewnia podstawowe możliwości zarządzania tożsamościami w Microsoft 365.

**Najważniejsze funkcje udostępniane grupom**

- Członkostwo w grupie
- Zasady nazewnictwa
- Zasady wygasania
- Zatrzymali
- Ograniczenie tworzenia grupy

**Czy Azure AD można utworzyć grupę?**

Tak, Grupy Microsoft 365 można utworzyć z Azure AD za pośrednictwem administracyjnego portalu internetowego, programu PowerShell lub interfejs Graph API.

**Czy Azure AD istnieje bez grupy?**

Tak, Azure AD wykonuje dużą liczbę usług, które nie mają związku z Grupy Microsoft 365. Każda grupa Microsoft 365 jest reprezentowana jako obiekt w Azure AD.

**Czy istnieje wiele wystąpień Azure AD na grupę?**

Nie, istnieje tylko jedno wystąpienie Azure AD.

**Czy Azure AD można skojarzyć z wieloma grupami?**

Tak, ponieważ Azure AD jest podstawową platformą, która zapewnia usługę członkostwa w grupie.

**Czy skojarzenie Azure AD z grupą może ulec zmianie?**

Nie, Azure AD jest podstawową platformą, na której istnieją grupy.

**Czy usunięcie wystąpienia powoduje usunięcie grupy?**

Usunięcie grupy w Azure AD spowoduje usunięcie odpowiednich usług i zawartości skojarzonych z grupą.

## <a name="teams"></a>Teams

Teams to obszar roboczy skoncentrowany na czatach, który ma na celu usprawnienie współpracy przez zapewnienie pojedynczego interfejsu do interakcji z różnymi usługami firmy Microsoft i innych firm.

Domyślnie po utworzeniu zespołu skrzynka pocztowa i kalendarz skojarzone z grupą Microsoft 365 są ukryte zarówno przed globalną listą adresów w Exchange, jak i Outlook. Może to zostać zastąpione ręcznie przez administratora, jeśli użytkownik chce używać zarówno Outlook, jak i Teams w tej samej grupie Microsoft 365.

**Najważniejsze funkcje udostępniane grupom**

- Rozmowy
- Karty & kanałów
- Spotkania

**Czy Teams można utworzyć grupę?**

Tak, utworzenie nowego zespołu spowoduje utworzenie nowej grupy Microsoft 365. Istnieje również możliwość utworzenia zespołu dla istniejącej grupy, która obecnie jej nie ma.

**Czy zespoły istnieją bez grupy?**

Nie, nie jest możliwe, aby zespół istniał bez grupy.

**Czy na grupę może być wiele zespołów?**

Nie, relacja między zespołem a grupą wynosi 1:1.

**Czy zespół może być skojarzony z wieloma grupami?**

Nie, sam zespół może być skojarzony tylko z jedną grupą.

**Czy skojarzenie zespołu z grupą może ulec zmianie?**

Nie, zespół może być skojarzony tylko z grupą, z którą był pierwotnie skojarzony.

**Czy usunięcie grupy przez zespół jest usuwane?**

Tak, usunięcie zespołu w Microsoft Teams spowoduje usunięcie grupy, usług skojarzonych z grupą i zawartości.

## <a name="exchange"></a>Exchange

Exchange Online udostępnia komunikaty, kalendarz, kontakt i skojarzone funkcje. W kontekście grupy jest skojarzony tylko jeden zasób — w przeciwieństwie do całego wystąpienia usługi.

**Najważniejsze funkcje udostępniane grupom**

- Skrzynka pocztowa i kalendarz
- Możliwość wysłania wiadomości e-mail do wszystkich członków grupy
- Storage konwersacji kanału Teams na potrzeby zbierania elektronicznych materiałów dowodowych, komentarze planisty

**Czy Exchange można utworzyć grupę?**

Tak, można utworzyć grupę z centrum administracyjnego Exchange Online, a także z poziomu Outlook. Można również konwertować listy dystrybucyjne Exchange na grupy Microsoft 365.

**Czy Exchange istnieje bez grupy?**

Tak, Exchange Online udostępnia kilka usług, w tym udostępnione skrzynki pocztowe i kalendarze, bez skojarzenia grupy.

**Czy istnieje wiele wystąpień Exchange skrzynek pocztowych lub kalendarzy na grupę?**

Nie, dla grupy może istnieć tylko jedna Exchange Online skrzynki pocztowej i kalendarza.

**Czy Exchange skrzynki pocztowe i kalendarze mogą być skojarzone z wieloma grupami?**

Nie, skrzynka pocztowa i kalendarz mają relację 1:1 z grupą. Istnieje możliwość udostępnienia skrzynki pocztowej innym użytkownikom lub grupom, jednak nie ustanawia to żadnej formy skojarzenia usługi.

**Czy skojarzenie Exchange skrzynki pocztowej lub kalendarza z grupą może ulec zmianie?**

Nie, nie można zmienić skrzynki pocztowej i kalendarza na inną grupę. Jednak zawartość może zostać przeniesiona z jednej skrzynki pocztowej do innej w ramach Outlook lub przy użyciu narzędzia innej firmy.

**Czy usunięcie skrzynki pocztowej powoduje usunięcie grupy?**

Tak, usunięcie skrzynki pocztowej w Exchange spowoduje usunięcie grupy, a także usług i zawartości skojarzonych z grupą.

## <a name="forms"></a>Formularzy

Formularze udostępniają internetowe ankiety i quizy.

**Najważniejsze funkcje udostępniane grupom**

- Własność formularzy

**Czy formularze mogą utworzyć grupę?**

Nie. Formularze nie mogą utworzyć grupy.

**Czy formularze istnieją bez grupy?**

Tak, ankiety i quizy można tworzyć bezpośrednio na koncie użytkownika końcowego.

**Czy może istnieć wiele formularzy na grupę?**

Tak, z grupą może być skojarzonych wiele formularzy.

**Czy formularze mogą być skojarzone z wieloma grupami?**

Nie, formularz można skojarzyć tylko z jedną grupą.

**Czy skojarzenie formularza z grupą może ulec zmianie?**

Nie, po skojarzeniu formularza z grupą (utworzoną bezpośrednio w obrębie lub z przeniesieniem własności od jednostki) nie można go przenieść do innej grupy.

**Czy usunięcie formularza powoduje usunięcie grupy?**

Nie, nie można usunąć grupy z interfejsu Formularze, tylko z pojedynczych formularzy.

## <a name="onenote"></a>OneNote

OneNote jest aplikacją do notesu cyfrowego. Notes OneNote utworzony z grupą jest plikiem w skojarzonej SharePoint lokacji, a nie w usłudze połączonej z grupą.

**Najważniejsze funkcje udostępniane grupom**

- Notes udostępniony (przechowywany w bibliotece SharePoint skojarzonej z grupą)

**Czy można OneNote utworzyć grupę?**

Nie, aplikacja OneNote nie może utworzyć grupy.

**Czy OneNote notesy istnieją bez grupy?**

Tak, notesy można tworzyć bezpośrednio w OneDrive lub w innych lokalizacjach udostępnionych.

**Czy może istnieć wiele notesów OneNote na grupę?**

Tak, notes jest tworzony domyślnie i można dodawać inne, jednak dowolny link do OneNote z usług skojarzonych z grupą zawsze będzie przechodził do notesu domyślnego.

**Czy notes OneNote może być skojarzony z wieloma grupami?**

Nie, notes jest przechowywany w skojarzonej z grupą SharePoint bibliotece lokacji i połączony z różnych interfejsów. Można go jednak udostępniać innym grupom w taki sam sposób, w jaki można go udostępniać osobom fizycznym.

**Czy skojarzenie notesu z grupą może ulec zmianie?**

Nie, sam notes jest skojarzony z grupą i może być bezpośrednio dostępny z innych usług połączonych z grupą, jednak zawartość można przenieść z jednego notesu do innego w aplikacji OneNote.

**Czy usunięcie notesu powoduje usunięcie grupy?**

Nie, jeśli jednak notes OneNote zostanie usunięty, w niektórych usługach skojarzonych z grupą mogą występować przerwane linki.

## <a name="planner"></a>Planner

Planner to uproszczona usługa zarządzania zadaniami grupowymi.

**Najważniejsze funkcje udostępniane grupom**

- Tablica do zarządzania zadaniami grupy

**Czy planista może utworzyć grupę?**

Tak, utworzenie planu spowoduje utworzenie nowej grupy.

**Czy tablica Planner istnieje bez grupy?**

Nie, plan musi być skojarzony z grupą.

**Czy może istnieć wiele planów na grupę?**

Tak, może istnieć wiele planów na grupę.

**Czy plan może być skojarzony z wieloma grupami?**

Nie, plan opiera się wyłącznie na członkostwie w grupie w celu określenia dostępu.

**Czy skojarzenie planu z grupą może ulec zmianie?**

Nie, jednak skopiowanie planu powoduje utworzenie nowej grupy.

> [!NOTE]
> Grupa utworzona przez inną aplikację nie zostanie automatycznie wyświetlona w programie Planner dla użytkownika. Aby uzyskać dostęp do tablicy, należy otworzyć ją z innego interfejsu opartego na grupie, takiego jak Outlook.

**Czy usunięcie planu powoduje usunięcie grupy?**

Tak, usunięcie planu spowoduje usunięcie usług i zawartości skojarzonych z grupą i grupą.

## <a name="power-apps"></a>Power Apps

Power Apps udostępnia kanwę do tworzenia aplikacji bez kodu.

**Najważniejsze funkcje udostępniane grupom**

- Aplikacje mogą być udostępniane grupie do uruchomienia i modyfikacji

**Czy Power Apps można utworzyć grupę?**

Nie, Power Apps nie może utworzyć grupy Microsoft 365.

**Czy Power Apps istnieć bez grupy?**

Tak, aplikacje można tworzyć w ramach Power Apps i znajdować się na koncie twórców do momentu udostępnienia lub opublikowania.

**Czy może istnieć wiele aplikacji na grupę?**

Tak, może istnieć wiele aplikacji udostępnionych grupie.

**Czy aplikacje mogą być skojarzone z wieloma grupami?**

Tak, aplikacja może być udostępniana wielu grupom.

**Czy skojarzenie aplikacji z grupą może ulec zmianie?**

Tak, ponieważ skojarzenie między Power Apps a grupą Microsoft 365 jest udostępniane tylko — aplikacja nadal znajduje się u twórcy.

> [!IMPORTANT]
> [Grupy muszą być włączone w zabezpieczeniach, aby można było udostępniać im aplikacje](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Czy usunięcie aplikacji powoduje usunięcie grupy?**

Nie, aplikacje nie są połączone z grupą inną niż udostępniona im.

## <a name="power-automate"></a>Power Automate

Power Automate (wcześniej znana jako Microsoft Flow) udostępnia przepływy pracy i usługi automatyzacji.

**Najważniejsze funkcje udostępniane grupom**

- Przepływy pracy można udostępniać grupie, która ma zostać uruchomiona i zmodyfikowana.

**Czy można Power Automate utworzyć grupę?**

Nie, Power Automate nie może utworzyć grupy Microsoft 365 w kontekście skojarzenia z grupą.

Istnieje jednak możliwość utworzenia przepływu, który wykonuje różne operacje, takie jak tworzenie Azure AD grupy zabezpieczeń lub aktualizowanie członkostwa w grupie Microsoft 365.

**Czy przepływy istnieją bez grupy?**

Tak, przepływy można tworzyć w ramach Power Automate i znajdować się na koncie twórców do momentu udostępnienia lub opublikowania.

**Czy może istnieć wiele przepływów na grupę?**

Tak, może istnieć wiele przepływów współużytkowanych z grupą.

**Czy przepływ może być skojarzony z wieloma grupami?**

Tak, przepływ można udostępnić wielu grupom.

**Czy skojarzenie przepływu z grupą może ulec zmianie?**

Tak, ponieważ skojarzenie między Power Automate a grupą Microsoft 365 jest udostępniane tylko — przepływ nadal znajduje się u twórcy.

**Czy usunięcie przepływu powoduje usunięcie grupy?**

Nie, podobnie jak Power Apps, przepływy nie są połączone z grupą inną niż udostępniona im.

## <a name="power-bi-classic"></a>Power BI (klasyczny)

Power BI udostępnia interaktywne pulpity nawigacyjne i raporty oparte na danych.

**Najważniejsze funkcje udostępniane grupom**

- Raportowanie danych

**Czy można Power BI utworzyć grupę?**

Tak, utworzenie klasycznego obszaru roboczego spowoduje utworzenie grupy Microsoft 365.

**Czy Power BI klasyczny obszar roboczy istnieje bez grupy?**

Nie, [klasyczny obszar roboczy w Power BI musi być skojarzony z grupą](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Czy może istnieć wiele Power BI obszarów roboczych na grupę?**

Nie, relacja między klasycznym obszarem roboczym a grupą wynosi 1:1.

**Czy obszar roboczy może być skojarzony z wieloma grupami?**

Technicznie nie, podczas tworzenia klasycznego obszaru roboczego z grupą zawartość może być udostępniana poza grupą użytkownikom i grupom zabezpieczeń.

**Czy skojarzenie obszaru roboczego z grupą może ulec zmianie?**

Nie, klasyczny obszar roboczy jest skojarzony z grupą, ale zawartość można przenieść z jednego obszaru roboczego do innego w interfejsie Power BI lub przez eksportowanie zawartości lokalnie.

**Czy usunięcie obszaru roboczego powoduje usunięcie grupy?**

Tak, usunięcie obszaru roboczego w Power BI spowoduje usunięcie usług i zawartości skojarzonych z grupą i grupą.

## <a name="power-bi-new"></a>Power BI (nowy)

Power BI udostępnia interaktywne pulpity nawigacyjne i raporty oparte na danych.

Podczas tworzenia nowego obszaru roboczego w Power BI nie tworzy grupy Microsoft 365, utworzenie grupy za pomocą innych środków powoduje utworzenie nowego (nie klasycznego) obszaru roboczego w Power BI.

**Najważniejsze funkcje udostępniane grupom**

- Raportowanie danych

**Czy można Power BI utworzyć grupę?**

Nie, nie można utworzyć grupy Microsoft 365 z nowego interfejsu Power BI.

**Czy nowy obszar roboczy Power BI istnieje bez grupy?**

Tak, istnieje możliwość tworzenia raportów i obszarów roboczych w Power BI, które nie są skojarzone z grupami Microsoft 365.

**Czy może istnieć wiele obszarów roboczych na grupę?**

Tak, [wiele obszarów roboczych utworzonych przez Power BI można udostępnić jednej grupie](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Czy obszar roboczy może być skojarzony z wieloma grupami?**

Nie, obszar roboczy utworzony przez Power BI może być skojarzony tylko z jedną grupą.

**Czy skojarzenie obszaru roboczego z grupą może ulec zmianie?**

Tak i nie. Obszar roboczy utworzony przez Power BI może być skojarzony tylko z jedną grupą jednocześnie, ale może zmienić skojarzenie w dowolnym momencie. Obszar roboczy utworzony w Power BI przez grupę jest trwale skojarzony z tą grupą.

**Czy usunięcie obszaru roboczego powoduje usunięcie grupy?**

Tak, usunięcie obszaru roboczego w Power BI spowoduje usunięcie usług i zawartości skojarzonych z grupą i grupą.

## <a name="project-for-the-web"></a>Project dla sieci Web

Project dla sieci Web oferuje możliwość tworzenia planów projektów, wykresów Gantta i planów.
Najważniejsze funkcje udostępniane grupom.

- plany Project

**Czy Project sieci Web może utworzyć grupę?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z Project dla sieci Web.

**Czy projekty istnieją bez grupy?**

Tak, projekty mogą istnieć bez skojarzenia z grupą Microsoft 365, jednak przypisanie zadań wymaga skojarzenia grupy.

**Czy może istnieć wiele projektów na grupę?**

Tak, istnieje możliwość połączenia wielu projektów w jednej grupie.

**Czy projekt może być skojarzony z wieloma grupami?**

Nie, projekt może być skojarzony tylko z jedną grupą.

**Czy skojarzenie projektu z grupą może ulec zmianie?**

Nie, po ustanowieniu skojarzenia z grupą nie można jej zmienić.

**Czy usunięcie projektu powoduje usunięcie grupy?**

Nie, usunięcie projektu w Project sieci Web nie spowoduje usunięcia grupy.

## <a name="roadmap"></a>Plan rozwoju

Plan działania umożliwia tworzenie planów projektu z Project dla sieci Web i Project Online.

**Najważniejsze funkcje udostępniane grupom**

- Project harmonogramy

**Czy plan działania może utworzyć grupę?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z planu działania.

**Czy plan działania istnieje bez grupy?**

Tak, harmonogramy mogą istnieć bez skojarzenia z grupą Microsoft 365, jednak udostępnienie planu działania wymaga skojarzenia grupy.

**Czy na grupę może istnieć wiele planów?**

Tak, istnieje możliwość połączenia wielu planów z jedną grupą.

**Czy plan działania może być skojarzony z wieloma grupami?**

Nie, plan działania może być skojarzony tylko z jedną grupą.

**Czy skojarzenie harmonogramu z grupą może ulec zmianie?**

Nie, po ustanowieniu skojarzenia z grupą nie można jej zmienić.

**Czy usunięcie planu działania powoduje usunięcie grupy?**

Nie, usunięcie harmonogramu nie spowoduje usunięcia grupy.

## <a name="sharepoint"></a>SharePoint

SharePoint jest internetową platformą do zarządzania zawartością, która udostępnia między innymi usługi magazynu dla kilku usług Microsoft 365.

**Najważniejsze funkcje udostępniane grupom**

- Biblioteka dokumentów
- Biblioteka do przechowywania notesu OneNote
- Storage plików typu wiki Teams

**Czy można SharePoint utworzyć grupę?**

Tak, utworzenie witryny zespołu w SharePoint spowoduje utworzenie domyślnie grupy Microsoft 365. Istnieje również możliwość utworzenia grupy i opcjonalnie zespołu dla istniejącej witryny.

**Czy SharePoint lokacje istnieją bez grupy?**

Tak, SharePoint oferuje kilka usług i witryn niezwiązanych z grupami, takich jak witryny komunikacji i centrum. 

**Czy może istnieć wiele lokacji na grupę?**

Nie, może istnieć tylko jedna lokacja na grupę. Kanały prywatne i udostępnione w Teams używają dodatkowych witryn, które nie są połączone z grupą.

**Czy witryny mogą być skojarzone z wieloma grupami?**

Technicznie nie, ale gdy witryna jest tworzona z grupą, zawartość może być udostępniana innym grupom.

**Czy skojarzenie witryny z grupą może ulec zmianie?**

Nie, sama witryna jest skojarzona z grupą, jednak zawartość może zostać przeniesiona z jednej witryny do innej w interfejsie SharePoint, przez eksportowanie zawartości lokalnie lub za pomocą narzędzia innej firmy.

**Czy usunięcie witryny powoduje usunięcie grupy?**

Tak, usunięcie witryny w SharePoint spowoduje usunięcie usług i zawartości skojarzonych z grupą i grupą.

## <a name="stream"></a>Stream

Microsoft Stream jest platformą do hostingu i udostępniania wideo.

**Najważniejsze funkcje udostępniane grupom**

- Magazyn wideo
- Teams nagrywanie spotkania
- Kanały wideo

**Czy usługa Stream może utworzyć grupę?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z poziomu usługi Stream.

**Czy usługa Stream istnieje bez grupy?**

Tak, kanały wideo i filmy wideo mogą istnieć w usłudze Stream bez skojarzeniu z grupą.

**Czy na grupę może istnieć wiele filmów wideo i kanałów?**

Tak, w każdej grupie może istnieć wiele filmów wideo i kanałów.

**Czy wideo lub kanał można skojarzyć z wieloma grupami?**

Tak, podczas tworzenia wideo lub kanału z grupą można go udostępniać innym grupom.

**Czy jej skojarzenie z grupą może ulec zmianie?**

Tak i nie; Filmy wideo w usłudze Stream są własnością oryginalnego modułu przekazującego lub rejestratora spotkań, dlatego można je skojarzyć z dowolną grupą, jednak kanały wideo mogą być skojarzone tylko z grupą, w ramach których zostały pierwotnie utworzone.

**Czy usunięcie klipów wideo lub kanałów powoduje usunięcie grupy?**

Nie, usunięcie filmów wideo lub kanałów nie powoduje usunięcia grupy. Jednak usunięcie samej grupy w usłudze Stream spowoduje usunięcie usług i zawartości skojarzonych z grupą, z wyjątkiem rzeczywistych filmów wideo.

## <a name="yammer"></a>Yammer

Yammer to platforma społecznościowa dla przedsiębiorstw, która ma na celu wspieranie zaangażowania społeczności w organizacjach i między nimi.

Utworzenie społeczności (wcześniej znanej jako "grupa") w Yammer tworzy skrzynkę pocztową, ale obecnie nie jest ona używana.

Grupy Microsoft 365 skojarzonej z Yammer nie można używać z zespołem w Microsoft Teams.

**Najważniejsze funkcje udostępniane grupom**

- Obszar konwersacji

**Czy można Yammer utworzyć grupę Microsoft 365?**

Tak, utworzenie nowej grupy w Yammer spowoduje utworzenie nowej grupy Microsoft 365, jeśli platformy są połączone, a użytkownik może utworzyć grupę.

Nie można utworzyć grupy Yammer ze skojarzoną grupą Microsoft 365 w żadnym interfejsie lub usłudze innej niż Yammer.

**Czy grupa Yammer istnieje bez grupy Microsoft 365?**

Tak, istnieje możliwość utworzenia grupy Yammer bez grupy Microsoft 365.

Jeśli platforma Yammer nie jest połączona z grupami Microsoft 365 lub użytkownicy nie mogą tworzyć grupy Microsoft 365, Yammer grupy są tworzone bez skojarzenia grupy Microsoft 365.

**Czy może istnieć wiele grup Yammer na grupę Microsoft 365?**

Nie, relacja między grupą Yammer a grupą Microsoft 365 wynosi 1:1.

**Czy grupa Yammer może być skojarzona z wieloma grupami Microsoft 365?**

Nie, grupa Yammer może być skojarzona tylko z jedną grupą Microsoft 365. Istnieje możliwość udostępniania lub przenoszenia wpisów do innych grup Yammer.

**Czy skojarzenie grupy Yammer z grupą Microsoft 365 może ulec zmianie?**

Nie, grupa Yammer może być skojarzona tylko z grupą Microsoft 365, z którą była pierwotnie skojarzona.

**Czy usunięcie grupy Yammer powoduje usunięcie grupy Microsoft 365?**

Tak, usunięcie grupy w Yammer spowoduje usunięcie powiązanych usług i zawartości powiązanych z grupą i grupą firmy Microsoft.

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)
