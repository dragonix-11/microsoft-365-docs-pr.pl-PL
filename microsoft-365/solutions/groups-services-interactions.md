---
title: Interakcje usług grup
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
description: Interakcje usług grup
ms.openlocfilehash: 226c1588c0275c3349d0fd996dd68f5748f11cd6
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005212"
---
# <a name="groups-services-interactions"></a>Interakcje usług grup

Microsoft 365 Groups to materiał wspólny dla kilku usług i obciążeń na platformie Microsoft 365, aby zapewnić połączone środowisko dla użytkowników końcowych. Podstawową zasadą jest Microsoft 365, która zapewnia:

- Sposób zarządzania członkostwem (Azure AD)
- Miejsce do wysyłania wiadomości i konwersacji (skrzynka Exchange, Microsoft Teams, Yammer)
- Miejsce, w którym mają być przechowywane pliki (SharePoint)
- Kalendarz do planowania (Exchange)
- Notes do przechwytywania notatek (OneNote)

W momencie tworzenia grupy kilka innych zasobów jest również aprowizowanych, jednak nie są one widoczne, dopóki nie zostaną po raz pierwszy dostępne z usługi:

- Tablica do zarządzania zadaniami grupy (Planner)
- Obszar roboczy raportowania (Power BI)
- Obszar udostępnianych klipów wideo (Microsoft Stream)
- Obszar formularzy udostępnionych (formularzy)

W Microsoft 365 inne usługi mogą wchodzić w interakcje z grupami usługi Microsoft 365, aby zapewnić dodatkowe funkcje i możliwości członkom grupy.
Oto przykłady:

- Power Apps aplikacji
- Power Automate przepływów pracy
- Project sieci Web i Przewodnik po zarządzaniu projektami opartymi na kaskadach
- Teams konwersacji opartych na kanałach
- Yammer dla interesującej ich społeczności

## <a name="user-interactions-with-groups"></a>Interakcje użytkowników z grupami

Microsoft 365 grupy mogą być tworzone i zarządzane z różnych interfejsów, zarówno przez administratorów, jak i użytkowników końcowych. 

### <a name="administrative-experiences"></a>Środowisko administracyjne

Administratorzy mogą tworzyć grupy usługi Microsoft 365 i zarządzać nimi z kilku centrów aadministracyjnym obciążenia pracą, interfejsów wiersza polecenia, które obsługują skrypty, a także niestandardowych aplikacji współdziałających z interfejsem API Graph. Jedynym wyjątkiem są grupy Yammer, które muszą zostać utworzone z poziomu Yammer sieci Web.

**Powiązane ustawienia**

W różnych interfejsach administracyjnych, które mogą zarządzać ustawieniami grupy, istnieje kilka nakładań, o których należy pamiętać.

**Centrum administracyjne platformy Microsoft 365**

W centrum administracyjne platformy Microsoft 365 dostęp gości do grup jest domyślnie włączony, podobnie jak możliwość zezwalania właścicielom na dodawanie gości. Dla grup z tego centrum administracyjnego nie są dostępne dodatkowe kontrolki na poziomie organizacji.

**Centrum administracyjne usługi Azure AD**

Centrum administracyjne usługi Azure AD oferuje kontrolę nad tym, czy użytkownicy mogą tworzyć grupy, czy przypisywać właścicieli w portalach Azure Portale Azure, a także ustawienia zasad wygasania i nazewnictwa.

Centrum administracyjne udostępnia również kilka miar kontroli zaproszeń gości wykraczających poza zakres centrum administracyjne platformy Microsoft 365, na przykład możliwość ograniczenia możliwości zapraszania gości przez osoby niebędących właścicielami.

**SharePoint**

SharePoint witryny są tworzone przy użyciu grup zabezpieczeń Właściciel, Członek i Odwiedzający, a pierwsze dwa odpowiadające ich odpowiednikom w grupie Microsoft 365 grupy. Członkostwo w witrynach SharePoint Online jest zazwyczaj zarządzane przez skojarzoną Microsoft 365, ale nie jest to relacja dwukierunkowa. Wszelkie zmiany członkostwa na poziomie grupy Microsoft 365 są odzwierciedlane w programie SharePoint, jednak zmiana członkostwa w grupie SharePoint nie jest odzwierciedlana w grupie Microsoft 365.

### <a name="user-experiences"></a>Środowisko użytkownika

Użytkownicy końcowi mogą tworzyć grupy z kilku usług w ramach usługi Microsoft 365, a w innych tylko grupie.

Następujące usługi umożliwiają tworzenie grup według użytkowników końcowych:

- Outlook
- Planner
- Project dla sieci Web
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Ograniczenie tworzenia grup

Wspólnym podejściem do kontrolowania sprawnowego działania zespołów jest ograniczenie liczby użytkowników, którzy mogą je tworzyć. Można to zrobić tylko przez ograniczenie tworzenia grup. Ma to wpływ na możliwość tworzenia grup z innych usług, które mogą być konieczne dla użytkownika końcowego. Microsoft 365 grupy nie obsługują możliwości ograniczenia tworzenia grup z niektórych aplikacji lub usług, zezwalając jednocześnie na to innym.

Środowisko ograniczeń tworzenia grup różni się w zależności od aplikacji i usług:

|Aplikacja lub usługa|Środowisko|
|---|---|
|Outlook|**Opcja Nowa grupa** zostanie usunięta z menu Nowy na stronie osoby|
|Planner|**W nowym planie** wyjaśniono, że tworzenie grup zostało wyłączone, i oferuje dodanie planu do istniejącej grupy.|
|Project sieci Web i przewodnik|**Menu Utwórz** grupę wyjaśnia, że tworzenie grup jest ograniczone i sugeruje użycie istniejącej grupy.|
|SharePoint|Nadal można utworzyć witrynę zespołu, która nie jest połączona z grupą.|
|Stream|**Opcja** Grupuj nie jest wyświetlana w **menu Utwórz**.|
|Teams|Użytkownik nie może utworzyć zespołu z nową grupą, ale nadal może utworzyć zespół, który korzysta z istniejącej grupy.<br><br>**Przycisk Utwórz zespół** zostanie zastąpiony przyciskiem Utwórz **zespół z grupy**.|
|Yammer|**Opcja Utwórz grupę** jest usuwana z nawigacji głównej grupy/społeczności.|

## <a name="services-interactions-with-groups"></a>Interakcje usług z grupami

Zobacz plakat Grupy w programie Microsoft 365, aby uzyskać informacje na temat różnych typów grup, sposobu ich tworzenia i zarządzania nimi oraz kilku zaleceń dotyczących zarządzania.

[![Obraz kciuka dla infografiki na temat grup.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf)

[PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx)

W poniższej tabeli przedstawiono omówienie interakcji grup Microsoft 365 z różnymi usługami:

|Rezultat|Funkcje|Czy usługa istnieje bez grupy?|Czy usługa może utworzyć grupę?|Czy usunięcie wystąpienia powoduje usunięcie grupy?|
|---|---|---|---|---|
|Azure AD|Członkostwo, kontrolki grupy, goście|Tak|Tak|Tak|
|Exchange|Kalendarz, skrzynka pocztowa|Tak|Tak|Tak|
|Formularze|Formularz|Tak|Nie|Nie|
|OneNote|Notes|Tak|Nie|Nie|
|Planner|Tablica zadań|Nie|Tak|Tak|
|Power Apps aplikacji|Aplikacja|Tak|Nie|Nie|
|Power Automate|Przepływ pracy|Tak|Nie|Nie|
|Power BI (klasyczny)|Workspace|Nie|Tak|Tak|
|Power BI (nowy)|Workspace|Tak|Nie|Tak|
|Project dla sieci Web|Project plan|Tak|Tak|Nie|
|Plan rozwoju|Plan rozwoju|Tak|Tak|Nie|
|SharePoint|Witryna|Tak|Tak|Tak|
|Stream|Kanał, wideo|Tak|Tak|Tak|
|Teams|Zespół|Nie|Tak|Tak|
|Yammer|Grupa|Tak|Tak|Tak|

Mimo że powyższej tabeli przedstawiono ogólne omówienie interakcji grup z Microsoft 365, istnieje kilka uciążliwości i macierzy, które należy zrozumieć. W poniższych sekcjach bardziej szczegółowo opatrzymy określone obciążenia pracą i ich interakcje z grupami.

## <a name="azure-ad"></a>Azure AD

Usługa Azure AD zapewnia podstawowe funkcje zarządzania tożsamościami w Microsoft 365.

**Najważniejsze funkcje dostępne dla grup**

- Członkostwo w grupie
- Zasady nazewnictwa
- Zasady wygasania
- Goście
- Ograniczenie tworzenia grup

**Czy usługa Azure AD może utworzyć grupę?**

Tak, Microsoft 365 w usłudze Azure AD można tworzyć za pośrednictwem portalu sieci Web administracji, programu PowerShell lub Graph API.

**Czy usługa Azure AD istnieje bez grupy?**

Tak, usługa Azure AD wykonuje wiele usług, które nie są związane z Microsoft 365 grupami. Każda Microsoft 365 jest reprezentowana jako obiekt w usłudze Azure AD.

**Czy istnieje wiele wystąpień usługi Azure AD na grupę?**

Nie, istnieje tylko jedno wystąpienie usługi Azure AD.

**Czy usługa Azure AD może być skojarzona z wieloma grupami?**

Tak, ponieważ usługa Azure AD jest platformą podstawową, która zapewnia usługę członkostwa w grupie.

**Czy skojarzenie usługi Azure AD ze zmianą grupy może się zmienić?**

Nie, usługa Azure AD jest podstawową platformą, na której istnieją grupy.

**Czy usunięcie wystąpienia powoduje usunięcie grupy?**

Usunięcie grupy w usłudze Azure AD spowoduje usunięcie powiązanych z grupą usług i zawartości.

## <a name="teams"></a>Teams

Teams to centrum rozmów ukierunkowane na ulepszanie współpracy dzięki możliwości korzystania z różnych usług firmy Microsoft i innych firm.

Domyślnie po utworzeniu zespołu skrzynka pocztowa i kalendarz skojarzone z grupą Microsoft 365 są ukryte zarówno na globalnej liście adresowej w programie Exchange, jak i na Outlook. To może zostać ręcznie zastąpione przez administratora, jeśli użytkownik chce używać zarówno programu Outlook, jak i Teams tej samej Microsoft 365 grupy.

**Najważniejsze funkcje dostępne dla grup**

- Konwersacje
- Kanały & karty
- Spotkania

**Czy Teams utworzyć grupę?**

Tak, utworzenie nowego zespołu spowoduje utworzenie nowej grupy Microsoft 365 zespołu. Można również utworzyć zespół dla istniejącej grupy, która obecnie go nie ma.

**Czy zespoły istnieją bez grupy?**

Nie, nie jest możliwe, aby zespół istniał bez grupy.

**Czy w grupie może być wiele zespołów?**

Nie, relacja między zespołem a grupą to 1:1.

**Czy zespół może być skojarzony z wieloma grupami?**

Nie, zespół może być skojarzony tylko z jedną grupą.

**Czy zespół może skojarzenia ze zmianą grupy?**

Nie, zespół może być skojarzony tylko z grupą, z którą był pierwotnie skojarzony.

**Czy usunięcie zespołu powoduje usunięcie grupy?**

Tak, usunięcie zespołu w programie Microsoft Teams spowoduje usunięcie grupy, usług skojarzonych z grupą i zawartości.

## <a name="exchange"></a>Exchange

Exchange Online udostępnia funkcje wiadomości, kalendarza, kontaktów i skojarzonych funkcji. W kontekście grupy jest skojarzony tylko jeden zasób — w odróżnieniu od całego wystąpienia usługi.

**Najważniejsze funkcje dostępne dla grup**

- Skrzynka pocztowa i kalendarz
- Możliwość wysyłania wiadomości e-mail do wszystkich członków grupy
- Storage konwersacji Teams na potrzeby zbierania elektronicznych materiałów dowodowych, komentarzy aplikacji Planner

**Czy Exchange utworzyć grupę?**

Tak, grupę można utworzyć w centrum administracyjnym usługi Exchange Online, a także w Outlook. Można również konwertować listy Exchange na grupy Microsoft 365 grupy.

**Czy Exchange istnieje bez grupy?**

Tak, Exchange Online zapewnia kilka usług, w tym udostępnione skrzynki pocztowe i kalendarze, bez skojarzenia grup.

**Czy istnieje wiele wystąpień skrzynek Exchange lub kalendarzy w grupie?**

Nie, grupa może mieć tylko jedną skrzynkę Exchange Online i kalendarz.

**Czy Exchange i kalendarze mogą być skojarzone z wieloma grupami?**

Nie, skrzynka pocztowa i kalendarz mają relację 1:1 z grupą. Skrzynkę pocztową można udostępnić innym użytkownikom lub grupom, ale nie powoduje to utworzenia żadnej formy skojarzenia usług.

**Czy Exchange skrzynki pocztowej lub kalendarza ze zmianą grupy?**

Nie, nie można zmienić skrzynki pocztowej i kalendarza na inną grupę. Jednak zawartość można przenosić z jednej skrzynki pocztowej do drugiej w obrębie Outlook lub za pomocą narzędzia innej firmy.

**Czy usunięcie skrzynki pocztowej powoduje usunięcie grupy?**

Tak, usunięcie skrzynki pocztowej w programie Exchange spowoduje usunięcie grupy, a także usług i zawartości skojarzonych z grupą.

## <a name="forms"></a>Formularze

Formularze — ankiety i testy oparte na sieci Web.

**Najważniejsze funkcje udostępniane grupom**

- Własność formularzy

**Czy formularze mogą utworzyć grupę?**

Nie, formularze nie mogą tworzyć grup.

**Czy formularze nie istnieją w grupie?**

Tak, ankiety i testy można tworzyć bezpośrednio na koncie użytkownika końcowego.

**Czy można utworzyć wiele formularzy na grupę?**

Tak, z grupą może być skojarzonych wiele formularzy.

**Czy formularze mogą być skojarzone z wieloma grupami?**

Nie, formularz może być skojarzony tylko z jedną grupą.

**Czy formularz może skojarzenia ze zmianą grupy?**

Nie, gdy formularz jest skojarzony z grupą (utworzoną bezpośrednio w obrębie firmy lub właścicielem przeniesionym od osoby), nie może zostać przeniesiony do innej grupy.

**Czy usunięcie formularza powoduje usunięcie grupy?**

Nie, nie można usunąć grupy z interfejsu formularzy, tylko pojedyncze formularze.

## <a name="onenote"></a>OneNote

OneNote to aplikacja notesu cyfrowego. Notes OneNote utworzony za pomocą grupy to plik w skojarzonej SharePoint sieci Web, a nie w usłudze połączonej z grupą.

**Najważniejsze funkcje udostępniane grupom**

- Notes udostępniony (przechowywany w bibliotece SharePoint grupy)

**Czy OneNote utworzyć grupę?**

Nie, aplikacja OneNote nie może utworzyć grupy.

**Czy OneNote notesy istnieją bez grupy?**

Tak, notesy można tworzyć bezpośrednio w OneDrive lub w innych lokalizacjach udostępnionych.

**Czy można utworzyć wiele OneNote w grupie?**

Tak, notes jest tworzony domyślnie i można dodawać inne osoby, jednak każdy link do notesu OneNote z usług skojarzonych z grupą zawsze jest przekierowywał do notesu domyślnego.

**Czy notes OneNote być skojarzony z wieloma grupami?**

Nie, notes jest przechowywany w skojarzonej z SharePoint bibliotece witryny i połączony z różnymi interfejsami. Można ją jednak udostępniać innym grupom w taki sam sposób jak inne osoby.

**Czy notes może być skojarzenia ze zmianą grupy?**

Nie, sam notes jest skojarzony z grupą i można uzyskać do niego dostęp bezpośrednio z innych usług połączonych z grupą, jednak zawartość można przenosić między notesami w aplikacji OneNote grupy.

**Czy usunięcie notesu powoduje usunięcie grupy?**

Nie, jeśli jednak OneNote notes zostanie usunięty, niektóre usługi skojarzone z grupą mogą zawierać przerwane linki.

## <a name="planner"></a>Planner

Planner to usługa uproszczonego zarządzania zadaniami grupy.

**Najważniejsze funkcje udostępniane grupom**

- Tablica do zarządzania zadaniami grupy

**Czy program Planner może utworzyć grupę?**

Tak, utworzenie planu spowoduje utworzenie nowej grupy.

**Czy tablica aplikacji Planner istnieje bez grupy?**

Nie, plan musi być skojarzony z grupą.

**Czy można utworzyć wiele planów na grupę?**

Tak, można utworzyć wiele planów na grupę.

**Czy plan może być skojarzony z wieloma grupami?**

Nie, do określenia dostępu do planu należy wyłącznie członkostwo w grupie.

**Czy plan może być skojarzenia ze zmianą grupy?**

Nie, jednak skopiowanie planu powoduje utworzenie nowej grupy.

> [!NOTE]
> Grupa utworzona przez dowolną inną aplikację nie będzie automatycznie pokazywana użytkownikowi w aplikacji Planner. Aby uzyskać dostęp do tablicy, musi ona najpierw otworzyć ją z innego interfejsu opartego na grupie, takiego jak Outlook.

**Czy usunięcie planu powoduje usunięcie grupy?**

Tak, usunięcie planu spowoduje usunięcie usług i zawartości skojarzonych z grupą.

## <a name="power-apps"></a>Power Apps

Power Apps udostępnia kanwę do tworzenia aplikacji bez kodu.

**Najważniejsze funkcje dostępne dla grup**

- Aplikacje można udostępniać grupie, aby można je było uruchamiać i modyfikować

**Czy Power Apps utworzyć grupę?**

Nie, Power Apps nie można utworzyć Microsoft 365 grupy.

**Czy Power Apps istnieje bez grupy?**

Tak, aplikacje można tworzyć w Power Apps i korzystać z konta twórców do czasu ich udostępnień lub opublikowania.

**Czy w grupie może być wiele aplikacji?**

Tak, grupa może być udostępniana w wielu aplikacjach.

**Czy aplikacje mogą być skojarzone z wieloma grupami?**

Tak, aplikację można udostępnić wielu grupom.

**Czy skojarzenie aplikacji ze zmianą grupy?**

Tak, ponieważ skojarzenie między Power Apps a grupą osób Microsoft 365 udostępnia tylko — aplikacja nadal znajduje się u autora.

> [!IMPORTANT]
> [Grupy muszą mieć włączone zabezpieczenia, aby można było im udostępniać aplikacje](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Czy usunięcie aplikacji powoduje usunięcie grupy?**

Nie, aplikacje nie są połączone z grupą inną niż udostępniane im.

## <a name="power-automate"></a>Power Automate

Power Automate (wcześniej znany jako Microsoft Flow) dostarcza przepływy pracy i usługi automatyzacji.

**Najważniejsze funkcje udostępniane grupom**

- Przepływy pracy można udostępniać grupie, aby można je było uruchamiać i modyfikować.

**Czy Power Automate utworzyć grupę?**

Nie, Power Automate nie można utworzyć grupy Microsoft 365 w kontekście skojarzonym z nią.

Można jednak utworzyć przepływ wykonujący różne operacje, takie jak tworzenie grupy zabezpieczeń usługi Azure AD lub aktualizowanie członkostwa w Microsoft 365 grupy.

**Czy przepływy istnieją bez grupy?**

Tak, przepływy można tworzyć w Power Automate i korzystać z konta twórców do czasu jego udostępnień lub opublikowania.

**Czy na grupę może być wiele przepływów?**

Tak, może być wiele przepływów udostępnianych grupie.

**Czy przepływ może być skojarzony z wieloma grupami?**

Tak, przepływ można udostępnić wielu grupom.

**Czy skojarzenie przepływu ze zmianą grupy?**

Tak, ponieważ skojarzenie między Power Automate a grupą Microsoft 365 współużytkuje tylko grupę — przepływ nadal istnieje wraz z twórcą.

**Czy usunięcie przepływu powoduje usunięcie grupy?**

Nie, tak Power Apps przepływy nie są połączone z grupą inną niż udostępniane im.

## <a name="power-bi-classic"></a>Power BI (klasyczny)

Power BI udostępnia interakcyjne pulpity nawigacyjne i raporty oparte na danych.

**Najważniejsze funkcje udostępniane grupom**

- Raportowanie danych

**Czy Power BI utworzyć grupę?**

Tak, utworzenie klasycznego obszaru roboczego spowoduje utworzenie Microsoft 365 grupy.

**Czy klasyczny Power BI nie istnieje w grupie?**

Nie, [klasyczny obszar roboczy w Power BI musi być skojarzony z grupą](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Czy w grupie można Power BI obszarów roboczych?**

Nie, relacja między klasycznym obszarem roboczym a grupą jest 1:1.

**Czy obszar roboczy może być skojarzony z wieloma grupami?**

Nie z technicznego punktu widzenia podczas tworzenia klasycznego obszaru roboczego razem z grupą można udostępnić zawartość poza grupą użytkownikom i grupom zabezpieczeń.

**Czy można skojarzenie obszaru roboczego ze zmianą grupy?**

Nie, klasyczny obszar roboczy jest skojarzony z grupą, jednak zawartość można przenosić z jednego obszaru roboczego do innego w interfejsie programu Power BI lub eksportować zawartość lokalnie.

**Czy usunięcie obszaru roboczego powoduje usunięcie grupy?**

Tak, usunięcie obszaru roboczego w programie Power BI spowoduje usunięcie usług i zawartości skojarzonych z grupą.

## <a name="power-bi-new"></a>Power BI (nowy)

Power BI udostępnia interakcyjne pulpity nawigacyjne i raporty oparte na danych.

Podczas tworzenia nowego obszaru roboczego w programie Power BI nie można utworzyć grupy programu Microsoft 365, natomiast utworzenie grupy w inny sposób powoduje utworzenie nowego (nie klasycznego) obszaru roboczego w Power BI.

**Najważniejsze funkcje udostępniane grupom**

- Raportowanie danych

**Czy Power BI utworzyć grupę?**

Nie, nie można utworzyć grupy Microsoft 365 z nowego interfejsu Power BI sieci.

**Czy nowy obszar Power BI nie istnieje w grupie?**

Tak, można tworzyć raporty i obszary robocze w Power BI, które nie są skojarzone Microsoft 365 grupy.

**Czy grupa może mieć wiele obszarów roboczych?**

Tak, [wiele obszarów roboczych utworzonych przez Power BI można udostępnić jednej grupie](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Czy obszar roboczy może być skojarzony z wieloma grupami?**

Nie, obszar roboczy utworzony przez Power BI może być skojarzony tylko z jedną grupą.

**Czy skojarzenie obszaru roboczego ze zmianą grupy może się zmienić?**

Tak i nie. Obszar roboczy utworzony za Power BI może być skojarzony tylko z jedną grupą jednocześnie, ale w dowolnym momencie można zmienić skojarzenie. Obszar roboczy utworzony w Power BI grupy jest trwale skojarzony z tą grupą.

**Czy usunięcie obszaru roboczego powoduje usunięcie grupy?**

Tak, usunięcie obszaru roboczego w programie Power BI spowoduje usunięcie usług i zawartości skojarzonych z grupą.

## <a name="project-for-the-web"></a>Project dla sieci Web

Project sieci Web oferuje możliwość tworzenia planów projektów, wykresów Gantta i przewodników.
Najważniejsze funkcje dostępne dla grup.

- plany Project-

**Czy Project dla sieci Web utworzyć grupę?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z Project sieci Web.

**Czy projekty istnieją bez grupy?**

Tak, projekty mogą istnieć bez kojarzenia z Microsoft 365, jednak przypisanie zadań wymaga skojarzenia grupy.

**Czy w ramach grupy może być wiele projektów?**

Tak, można połączyć wiele projektów w jednej grupie.

**Czy można skojarzyć projekt z wieloma grupami?**

Nie, projekt może być skojarzony tylko z jedną grupą.

**Czy projekt może być skojarzenia ze zmianą grupy?**

Nie, po skojarzenia z grupą nie można go zmienić.

**Czy usunięcie projektu powoduje usunięcie grupy?**

Nie, usunięcie projektu w aplikacji Project sieci Web nie spowoduje usunięcia grupy.

## <a name="roadmap"></a>Plan rozwoju

Przewodnik umożliwia tworzenie przewodników po projektach przy Project sieci Web i aplikacji Project Online.

**Najważniejsze funkcje dostępne dla grup**

- Project przewodników

**Czy przewodnik może utworzyć grupę?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z planu.

**Czy przewodnik istnieje bez grupy?**

Tak, przewodnik może istnieć bez kojarzenia Microsoft 365 grupy, ale udostępnianie planu wymaga skojarzenia grupy.

**Czy można utworzyć wiele przewodników na grupę?**

Tak, można połączyć wiele przewodników z jedną grupą.

**Czy plan może być skojarzony z wieloma grupami?**

Nie, plan może być skojarzony tylko z jedną grupą.

**Czy skojarzenie planu ze zmianą grupy?**

Nie, po skojarzenia z grupą nie można go zmienić.

**Czy usunięcie planu powoduje usunięcie grupy?**

Nie, usunięcie planu nie spowoduje usunięcia grupy.

## <a name="sharepoint"></a>SharePoint

SharePoint to oparta na sieci Web platforma do zarządzania zawartością, która oferuje między innymi usługi magazynowania dla wielu Microsoft 365 zawartości.

**Najważniejsze funkcje dostępne dla grup**

- Biblioteka dokumentów
- Biblioteka do przechowywania OneNote notesu
- Storage plików Teams wiki

**Czy SharePoint utworzyć grupę?**

Tak, utworzenie witryny zespołu w programie SharePoint domyślnie spowoduje utworzenie Microsoft 365 zespołu. Można także utworzyć grupę oraz, opcjonalnie, zespół dla istniejącej witryny.

**Czy SharePoint istnieją bez grupy?**

Tak, SharePoint oferuje kilka niegrupowych usług i witryn, takich jak witryny komunikacji i centrum. 

**Czy na grupę może być wiele witryn?**

Nie, dla jednej grupy może być dostępna tylko jedna witryna. Kanały prywatne Teams korzystają z dodatkowych witryn, które nie są połączone z grupą.

**Czy witryny mogą być skojarzone z wieloma grupami?**

Nie z technicznego punktu widzenia, ale gdy witryna jest tworzona wraz z grupą, zawartość można udostępniać innym grupom.

**Czy można skojarzenie witryny ze zmianą grupy?**

Nie, witryna jest skojarzona z grupą, jednak zawartość można przenosić między witrynami w obrębie interfejsu programu SharePoint, eksportować zawartość lokalnie lub za pomocą narzędzia innej firmy.

**Czy usunięcie witryny powoduje usunięcie grupy?**

Tak, usunięcie witryny w programie SharePoint spowoduje usunięcie usług i zawartości skojarzonych z grupą.

## <a name="stream"></a>Stream

Microsoft Stream to platforma do udostępniania i hostingu wideo.

**Najważniejsze funkcje dostępne dla grup**

- Magazyn wideo
- Teams nagrania ze spotkania
- Kanały wideo

**Czy można utworzyć grupę za pomocą strumienia?**

Tak, można utworzyć nową grupę Microsoft 365 bezpośrednio z streamu.

**Czy stream istnieje bez grupy?**

Tak, kanały wideo i klipy wideo mogą istnieć w u gdybym programie Stream nie była skojarzona z grupą.

**Czy w grupie może być wiele klipów wideo i kanałów?**

Tak, każda grupa może mieć wiele klipów wideo i kanałów.

**Czy klip wideo lub kanał może być skojarzony z wieloma grupami?**

Tak, podczas tworzenia klipu wideo lub kanału w grupie można udostępnić go innym grupom.

**Czy jego skojarzenie ze zmianą grupy?**

Tak i nie; Klipy wideo w u rejestratorze strumieni są własnością pierwotnego uploadera lub rejestratora spotkań, więc mogą być skojarzone z dowolną grupą, jednak kanały wideo mogą być skojarzone tylko z grupą, w której zostały pierwotnie utworzone.

**Czy usunięcie klipów wideo lub kanałów powoduje usunięcie grupy?**

Nie, usunięcie klipów wideo lub kanałów nie powoduje usunięcia grupy. Jednak usunięcie samej grupy w u programie Stream spowoduje usunięcie powiązanych z grupą usług i zawartości, z wyjątkiem rzeczywistych klipów wideo.

## <a name="yammer"></a>Yammer

Yammer to platforma społecznościowa dla przedsiębiorstw zaprojektowana w celu pielęgnowania zaangażowania społeczności w ramach organizacji i między nimi.

Utworzenie społeczności (wcześniej nazywanej "grupą") w programie Yammer powoduje utworzenie skrzynki pocztowej, ale obecnie nie jest ona używana.

Grupy Microsoft 365 skojarzonej z zespołem Yammer nie można używać z zespołem w Microsoft Teams.

**Najważniejsze funkcje dostępne dla grup**

- Obszar konwersacji

**Czy Yammer utworzyć Microsoft 365 grupy?**

Tak, utworzenie nowej grupy w Yammer spowoduje utworzenie nowej grupy Microsoft 365, o ile platformy są połączone, a użytkownik może utworzyć grupę.

Grupy Yammer ze skojarzoną Microsoft 365 nie można utworzyć w interfejsie ani w innej usłudze niż Yammer interfejsu.

**Czy grupa Yammer istnieje bez grupy Microsoft 365 grupy?**

Tak, można utworzyć grupę Yammer bez grupy Microsoft 365 grupy.

Jeśli platforma Yammer nie jest połączona z grupami Microsoft 365 lub użytkownicy nie mają możliwości tworzenia grupy Microsoft 365, grupy Yammer są tworzone bez skojarzenia Microsoft 365 grupy.

**Czy w grupie może Yammer grup Microsoft 365 grupy?**

Nie, relacja między grupą Yammer a grupą Microsoft 365 to 1:1.

**Czy grupa Yammer może być skojarzona z Microsoft 365 grupami?**

Nie, grupa Yammer może być skojarzona tylko z jedną Microsoft 365 grupy. Wpisy mogą być udostępniane innym grupom lub przenoszone do Yammer grupy.

**Czy skojarzenie grupy Yammer z Microsoft 365 grupę?**

Nie, grupa Yammer może być skojarzona tylko z Microsoft 365, z którą była pierwotnie skojarzona.

**Czy usunięcie grupy Yammer powoduje usunięcie Microsoft 365 grupy?**

Tak, usunięcie grupy w programie Yammer spowoduje usunięcie powiązanych usług i zawartości skojarzonych z grupą Microsoft.

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)
