---
title: Opcje zakończenia cyklu życia dla grup, zespołów i Yammer
ms.reviewer: mmclean
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
description: Opcje zakończenia cyklu życia dla grup, zespołów i Yammer.
ms.openlocfilehash: f7774498047f74c27b21e45ed86b284a42325bb0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973932"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Opcje zakończenia cyklu życia dla grup, zespołów i Yammer

Grupy Microsoft 365 i Microsoft Teams współpracują z wieloma połączonymi usługami. Po usunięciu grupy lub zespołu większość informacji w połączonych usługach również zostanie usunięta. W tym artykule opisano opcje przechowywania informacji przez przeniesienie ich poza grupę lub zespół przed usunięciem.

Typowym rozwiązaniem dla grup lub zespołów, które nie są już wymagane, jest przeniesienie plików z zespołu i zarchiwizowanie ich w innej lokalizacji, takiej jak biblioteka dokumentów SharePoint. Ta praktyka opiera się na starszym stylu pracy, w którym informacje są przechowywane w plikach i folderach, a komunikacja jest prowadzona za pośrednictwem poczty e-mail.

W poniższej tabeli przedstawiono usługi skojarzone z grupami i zespołami oraz kluczowe typy zawartości znajdujące się w każdej z nich:

|Usługa|Typy zawartości|
|:------|:---------------|
|Teams|Konwersacje kanałów, pliki w kanałach|
|Formularzy|Struktura i wyniki ankiety|
|OneNote|Notebook|
|Outlook|Poczta i kalendarz|
|Planner|Project informacje o stanie i zadaniu|
|Power Automate|Przepływy pracy|
|Power BI|Dane, raporty i pulpity nawigacyjne|
|Project w Internecie|plany Project|
|Plan rozwoju|Planów|
|SharePoint|Pliki, listy, Teams dane typu wiki kanału|
|Stream|Filmy|
|Yammer|Rozmowy|

Podczas usuwania grupy lub zespołu większość skojarzonych zasobów również jest usuwana. Wyjątki obejmują:

- Filmy wideo w usłudze Stream pozostają własnością osoby, która je przesłała/nagrała
- Przepływy w Power Automate pozostają własnością osoby, która je utworzyła.
- Project i dane planów w Project w internecie pozostają w usłudze CDS i można je przywrócić oddzielnie.

Grupy i zespoły pozostają w stanie usuwania nietrwałego przez 30 dni i można je przywrócić w dowolnym momencie. Jednak po upływie 30 dni i wszystkie skojarzone zasoby, takie jak usługi i zawartość, są czyszczone ze środowiska Microsoft 365. Każda zawartość chroniona przez zasady przechowywania pozostaje dostępna za pośrednictwem wyszukiwań zbierania elektronicznych materiałów dowodowych.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Zagadnienia dotyczące zakończenia cyklu życia dla usług połączonych z grupą

Istnieją trzy kluczowe obszary, które właściciele zespołów i grup oraz administratorzy IT muszą wziąć pod uwagę podczas usuwania grupy lub zespołu.

**Content (Zawartość)**

Czy zawartość musi zostać zachowana po tym, jak zespołu już nie ma? Czy wystarczy polegać na możliwościach przechowywania Microsoft 365, czy też część zawartości w aplikacjach i usługach, które nie oferują przechowywania? Czy zawartość musi być przechowywana do celów zarządzania rekordami, archiwizacji lub przyszłego użycia i odwoływania się do nich?

Aby uniknąć potencjalnej utraty danych, należy zadać te pytania, zanim jakikolwiek zespół zostanie zarchiwizowany lub usunięty.

**Usług**

Czy zawartość musi pozostać w bieżącej formie roboczej? Czy na przykład raport Power BI musi być nadal dostępny? Czy wyniki formularza muszą być dostępne w widoku podsumowania wizualizacji? Czy listy w SharePoint są połączone lub osadzone w dowolnym miejscu?

Te pytania należy zadać przed usunięciem grupy bazowej, ponieważ eksportowanie zawartości może nie być wystarczające.

**Zatrzymali**

Po zaproszeniu gości do zespołu konto gościa jest tworzone w Azure Active Directory organizacji hosta przed dodaniem ich do zespołu. Po usunięciu zespołu goście nie są usuwane z Azure Active Directory. Chociaż goście nie mogą uzyskiwać dostępu do grup, witryn, zespołów ani zawartości, które nie zostały im udostępnione, nadal mogą potencjalnie korzystać z funkcji w ramach Microsoft Teams, takich jak uruchamianie czatów, połączeń głosowych i wideo oraz korzystanie z aplikacji.

Właściciel zespołu lub grupy może zaprosić osobę spoza organizacji do zostania gościem w Azure Active Directory, dodając ją do zespołu. Właściciel zespołu nie może jednak usunąć gościa z Azure Active Directory. Usuwanie kont może być wykonywane tylko przez administratora globalnego lub administratora użytkownika.

Ważne jest, aby przeprowadzać przeglądy gości i zrozumieć, czy goście muszą zostać usunięci z Azure Active Directory po usunięciu zespołu. Goście mogą pozostać w katalogu, na przykład być członkiem innych zespołów lub korzystać z innych Microsoft 365 lub usług platformy Azure.

## <a name="teams"></a>Teams

Teams zawartość jest głównie w formie konwersacji.

Konwersacji w kanałach nie można kopiować ani przenosić przy użyciu natywnej funkcji Microsoft Teams. Można je jednak wyeksportować przy użyciu interfejs Graph API.

Ponadto jeśli zasady przechowywania są stosowane do Teams, konwersacje są zachowywane i dostępne za pośrednictwem wyszukiwań zbierania elektronicznych materiałów dowodowych. Korzystając z zbierania elektronicznych materiałów dowodowych (Premium), możesz [zrekonstruować Teams konwersację na czacie](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Archiwizowanie zespołu

[Zaletą archiwizacji zespołu](/microsoftteams/archive-or-delete-a-team) jest to, że zapewnia on pełny dostęp do zespołu w takim samym stanie, w jakim był. Użytkownicy nadal mogą przeglądać konwersacje kanału i otwierać pliki, nawet jeśli nie są aktywne. Ponadto zespoły mogą być niearchiwizowane, jeśli istnieje potrzeba kontynuowania pracy nad nimi (na przykład jeśli projekt zostanie rozszerzony).

Gdy zespół jest archiwizowany przez właściciela, jest on ustawiony na tylko do odczytu dla członków zarówno dla zawartości w zespole, jak i w przypadku wybrania skojarzonej witryny SharePoint. Celem tej akcji jest zapewnienie, że konwersacje w kanałach zostaną zachowane w istniejącym stanie wraz z zawartością opartą na SharePoint, taką jak pliki i witryny typu wiki.

W witrynie SharePoint nie ma widocznych zmian. Nie można jednak wprowadzać żadnych zmian w żadnych plikach lub listach, ponieważ uprawnienia SharePoint dla grupy Microsoft 365 są ustawione na **odwiedzających witrynę**. Obejmuje to notes OneNote dla zespołu, który jest przechowywany w bibliotece zasobów witryny w SharePoint lokacji.

Gdy zespół zostanie zarchiwizowany, podstawowa grupa Microsoft 365 nadal podlega zasadom wygasania (jeśli została ustawiona) i jako taka właściciel musi kontynuować odnawianie zespołu.

Mimo że konwersacje na kanale zespołu i zawartość witryny SharePoint są ustawione na tylko do odczytu, to samo nie jest stosowane do innych skojarzonych usług:

- Zasobniki i zadania planisty można nadal tworzyć, modyfikować i usuwać.
- Formularze nadal mogą otrzymywać zgłoszenia.
- Skrzynka pocztowa Outlook nadal może odbierać wiadomości e-mail.
- Power BI pulpitów nawigacyjnych, raportów i danych można nadal modyfikować.
- Projekty i plany nadal można edytować w Project w Internecie.
- Filmy wideo można nadal przekazywać, modyfikować i usuwać w usłudze Stream.
- Przepływy w Power Automate można nadal tworzyć, modyfikować, usuwać i nadal będą uruchamiane. (Jeśli jest to wymagane do opublikowania komunikatu w kanale zarchiwizowanego zespołu, nie powiedzie się).

## <a name="forms"></a>Formularzy

Chociaż formularz można przenieść z pojedynczego konta do grupy, nie można go przenieść ani skopiować z jednej grupy do innej. Istnieją trzy opcje dostępne dla formularza po usunięciu zespołu.

**Duplikuj formularz**

Formularze mogą być [udostępniane jako szablony](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), co umożliwia innym użytkownikom kopiowanie ich na własne konto lub do grupy. Nie zachowuje to danych z przesłanych wyników; strukturę formularzy, taką jak pytania i ustawienia.

**Eksportowanie wyników do arkusza kalkulacyjnego**

Jeśli dane odpowiedzi formularza muszą zostać zachowane, można to osiągnąć, [eksportując wyniki do arkusza kalkulacyjnego Excel](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Spowoduje to tylko wyeksportowanie pytań i odpowiedzi jako danych — nie obejmuje ono wykresów utworzonych przez formularze.

**Usuwanie formularza**

Usunięcie grupy spowoduje również usunięcie wszystkich skojarzonych formularzy, ale członkowie grupy mogą [je bezpośrednio usunąć](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) bez bycia właścicielem grupy. Jest to jednak krok ręczny, który nie zapewnia żadnych dodatkowych korzyści.

## <a name="onenote"></a>OneNote

Notes OneNote zawarty w grupie jest przechowywany w bibliotece zasobów witryny w skojarzonej SharePoint lokacji. Chociaż pliki notesu mogą być czasami rozłożone na wiele pojedynczych plików, nie można ich kopiować i otwierać niezależnie. Zamiast tego zawartość notesu OneNote musi zostać przeniesiona lub wyeksportowana przy użyciu OneNote 2016.

**Przenoszenie stron i sekcji do innego notesu**

[Pojedyncze przenoszenie stron lub sekcji do innego notesu](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) zapewnia właścicielom możliwość czyszczenia danych i wykonywania tylko tych czynności, które należy zachować.

**Eksportowanie całego notesu jako pakietu**

Jeśli cały notes musi zostać zachowany z istniejącą strukturą, można go [wyeksportować jako plik pakietu OneNote](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309), a następnie zaimportować go do nowej lokalizacji. Zamiast tego może służyć jako metoda do przechowywania zawartości w jednym pliku, a nie w istniejącej strukturze wielu plików.

**Drukowanie w formacie PDF**

W scenariuszach, w których część zawartości notesu musi być przechowywana tylko w celach informacyjnych lub jako rekordy, poszczególne strony mogą być [drukowane w formacie PDF i przechowywane w innym miejscu](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Skrzynka pocztowa i kalendarz

Nie jest niczym niezwykłym, że skrzynka pocztowa skojarzona z grupą jest używana, mimo że wiele konwersacji mogło być prowadzonych w kanałach zespołu. Skrzynka pocztowa przechowuje tylko wiadomości e-mail, które zostały wysłane bezpośrednio do niej i nie zawierają wiadomości e-mail, które zostały wysłane bezpośrednio do kanałów.

W niektórych przypadkach wiadomości e-mail przechowywane w skrzynce pocztowej mogą być powiadomieniami o spotkaniach, aktualizacjach zadań plannera i innych komunikatach generowanych przez aplikację lub system. Ważne jest, aby zawartość skrzynki pocztowej została przejrzana w celu ustalenia, czy zawartość powinna zostać zachowana, czy usunięta.

Jeśli zasady przechowywania są stosowane w Exchange, wiadomości e-mail i elementy kalendarza są zachowywane i dostępne za pośrednictwem wyszukiwań zbierania elektronicznych materiałów dowodowych.

**Eksportowanie poczty i kalendarza**

Członkowie zespołu lub grupy mogą [eksportować zawartość skrzynki pocztowej i kalendarza do pliku Outlook Data / Personal Storage (PST](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91)). Ten plik może być następnie przechowywany w innym miejscu lub zawartość może zostać zaimportowana do innej skrzynki pocztowej. Ten pierwszy nie jest zalecany, ponieważ nie można przeszukiwać zawartości pliku PST bez otwarcia go w Outlook, a sam plik może z czasem ulec uszkodzeniu.

**Migracja zawartości wykonywana przez it**

Administratorzy mogą używać narzędzi innych firm do migrowania zawartości poczty e-mail i kalendarza między skrzynkami pocztowymi bez żadnej interwencji użytkownika. Jedną z potencjalnych lokalizacji magazynu może być udostępniona skrzynka pocztowa utworzona wyłącznie w celu "archiwizacji" zawartości skrzynki pocztowej grupy.

## <a name="planner"></a>Planner

Każda grupa lub zespół może mieć wiele planów. Ważne jest, aby podczas procesu poza wejściem na pokład upewnić się, że wymagania dotyczące przechowywania są spełnione dla każdego planu. Podobnie jak w przypadku innych usług, istnieje kilka podejść do zawartości wbudowanej w planistę.

**Eksportowanie planu do arkusza kalkulacyjnego**

Jeśli jest on wymagany tylko do przechowywania kopii planu do celów przechowywania rekordów, najprostszym podejściem jest [wyeksportowanie planu do arkusza kalkulacyjnego Excel](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Jest to akcja jednokierunkowa — nie ma możliwości importowania planów z arkusza kalkulacyjnego.

> [!IMPORTANT]
> Eksportowanie planu do Excel będzie zawierać większość informacji w ramach planu, ale nie będzie zawierać komentarzy, linków ani plików.

**Kopiowanie i przenoszenie zadań do innego planu**

Podczas gdy kopiowanie lub przenoszenie zadań do innego planu wydaje się rozwiązaniem, poszczególne zadania można [kopiować lub przenosić tylko między planami](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) w tej samej grupie. Nie spowoduje to tworzenia kopii zapasowej danych, jeśli grupa skojarzona z planem zostanie usunięta.

**Kopiowanie całego planu**

Istnieje również możliwość [skopiowania całego planu](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Nie można wykonać kopiowania do istniejącej grupy. Skopiowanie planu spowoduje utworzenie nowej grupy. Ponadto kopiowanie całego planu nie będzie zawierać komentarzy, przypisań, linków, załączników ani dat.

## <a name="power-automate"></a>Power Automate

Przepływy utworzone w Power Automate i skojarzone z grupą lub zespołem nie należą do grupy. Są one własnością twórcy i są jedynie udostępniane innym użytkownikom i grupom. W związku z tym nie ma to wpływu na usunięcie grupy lub zespołu.

**Zmienianie własności przepływu**

Jeśli przepływ musi nadal działać, właściciele mogą dodawać innych użytkowników lub Microsoft 365 grupy jako właścicieli.

**Eksportowanie przepływu**

Jeśli przepływ nie musi kontynuować działania, ale musi zostać zachowany w celu potencjalnego użycia w przyszłości, można go [wyeksportować jako plik i zaimportować](https://flow.microsoft.com/blog/import-export-bap-packages/) ponownie później.

## <a name="power-bi"></a>Power BI

Power BI dane i obszary robocze mogą działać niezależnie od grup i zespołów i podobnie jak inne obciążenia oferują różne sposoby wdrażania.

**Kopiowanie raportów do innego obszaru roboczego**

Jeśli raport jest potrzebny po usunięciu grupy lub zespołu, można go [skopiować z istniejącego obszaru roboczego do innego obszaru roboczego w ramach Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Eksportowanie danych z pulpitu nawigacyjnego lub raportu**

Zamiast tego, jeśli raport nie musi już być aktywny, ale dane muszą zostać zachowane, można go [wyeksportować do Excel](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Projekty i plany utworzone w Project dla sieci Web są skojarzone z grupami Microsoft 365 i mają podejścia do dołączania podobne do Power BI.

**Przypisywanie projektu do innej grupy**

Jeśli projekt musi zostać zachowany w stanie funkcjonalnym poza okresem istnienia grupy lub zespołu, może zostać [przypisany do innej grupy Microsoft 365](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Można to zrobić przy użyciu Centrum administracyjnego usługi Dynamics 365.

**Eksportowanie danych z projektu lub planu działania**

Za pomocą Centrum administracyjnego usługi Dynamics 365 można [wyeksportować dane użytkowników z projektu](/project-for-the-web/export-user-data-from-project-for-the-web) do arkusza kalkulacyjnego. Dane można również wyeksportować do pliku Project (. MPP) i formaty plików XML przy użyciu programu PowerShell.

## <a name="sharepoint"></a>SharePoint

Wszystkie pliki w kanałach zespołu są przechowywane w SharePoint lokacji skojarzonej grupy. W niektórych przypadkach zawartość inna niż dokumenty może istnieć w SharePoint, takich jak listy lub strony.

Pliki są zwykle przechowywane w trzech lokalizacjach podstawowych w SharePoint lokacji:

- Strony — biblioteka stron witryny
- Obrazy używane na stronach — biblioteka zasobów witryny
- Pliki w kanałach — biblioteka dokumentów
- Strony typu wiki — biblioteka danych typu wiki Teams

Jeśli witryna ma co najmniej jedną podwitrynę, proces wejścia na pokład będzie musiał zostać powtórzony dla każdej podwitryny. Jeśli zespół zawiera kanały prywatne lub udostępnione, istnieje oddzielna witryna SharePoint dla każdego kanału.

Ważne jest, aby podczas usuwania plików z grupy lub zespołu wziąć pod uwagę, że mogą one być udostępniane użytkownikom, którzy nie są członkami grupy lub zespołu. Możesz przekazać im zbliżającą się zmianę.

**Pobieranie plików**

Pliki przechowywane w SharePoint w jednej z bibliotek wymienionych powyżej można [pobrać na komputer lokalny](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Przenoszenie plików**

Ponadto pliki można [przenosić do innej lokalizacji w ramach SharePoint, na przykład biblioteki w innej lokacji](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Eksportuj listę**

Dane przechowywane na listach SharePoint można [wyeksportować do arkusza kalkulacyjnego Excel](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) i ponownie zaimportować do listy w innej witrynie.

Alternatywnie narzędzie innej firmy może służyć do migrowania listy między lokacjami w celu zachowania funkcji, widoków listy, formatowania i innych atrybutów.

**"Eksportowanie" plików typu wiki**

Zawartość witryny typu wiki w kanałach zespołu jest przechowywana w pliku w formacie HTML w dedykowanej bibliotece skojarzonej witryny SharePoint. Nie można ich łatwo wyeksportować i zaimportować do innej witryny typu wiki kanału, ale można je przekonwertować na plik HTML i otworzyć jako stronę internetową.

## <a name="microsoft-stream"></a>Microsoft Stream

Podobnie jak Power Automate, filmy wideo w usłudze Stream skojarzone z grupą lub zespołem nie są w rzeczywistości własnością grupy i nie są usuwane po usunięciu grupy. Filmy wideo w usłudze Stream należą do osoby, która przekazała lub utworzyła film wideo, nawet jeśli dodają użytkowników lub grupy jako właścicieli. Spotkania zarejestrowane w kanale Teams należą do osoby, która rozpoczęła nagrywanie.

**Dodawanie innych właścicieli**

Ponieważ wideo jest zachowywane w usłudze Stream po usunięciu grupy, pierwotny właściciel może [udostępnić wideo innym użytkownikom i grupom, nawet dodając je jako właścicieli](/stream/portal-edit-video).

**Pobieranie wideo**

W scenariuszach, w których film wideo nie musi być przechowywany w usłudze Stream lub musi być przechowywany w innej lokalizacji, takiej jak system zarządzania rekordami, właściciel może [pobrać go lokalnie](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

W przeciwieństwie do konwersacji w Microsoft Teams Yammer oferuje zarówno użytkownikom, jak i administratorom opcje przenoszenia lub eksportowania konwersacji.

**Przenoszenie konwersacji do innej grupy lub społeczności**

Konwersacje mogą być przenoszone do innej grupy Yammer przez dowolnego użytkownika, a nie tylko przez właścicieli lub administratorów. Jest to możliwe zarówno w [klasycznym Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872), jak i [w nowych](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) interfejsach Yammer.

**Eksportowanie danych sieciowych**

Yammer administratorzy sieci [eksportują dane sieciowe](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Spowoduje to jednak wyeksportowanie wszystkich konwersacji dla całej sieci. Wynikowe eksportowanie powoduje wyświetlenie identyfikatora grupy. Konwersacje można filtrować na podstawie tego identyfikatora.

## <a name="related-topics"></a>Tematy pokrewne

[Usuwanie byłego pracownika i zabezpieczanie danych](/microsoft-365/admin/add-users/remove-former-employee)
