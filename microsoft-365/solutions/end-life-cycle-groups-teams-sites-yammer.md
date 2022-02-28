---
title: Zakończenie opcji cyklu życia grup, zespołów i Yammer
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
description: Zakończenie opcji cyklu życia grup, zespołów i Yammer.
ms.openlocfilehash: 883af3878bd0bc68aa539fc1cc36b66c4f1cfe9e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985119"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Zakończenie opcji cyklu życia grup, zespołów i Yammer

Microsoft 365 grupy i Microsoft Teams z wieloma usługami połączonymi. Po usunięciu grupy lub zespołu większość informacji w usługach połączonych również jest usuwana. W tym artykule opisano opcje zachowywania informacji przez przeniesienie ich poza grupę lub zespół przed usunięciem.

Często spotykaną praktyką w przypadku grup lub zespołów, które nie są już wymagane, jest przenoszenie plików poza zespół i archiwizowanie ich w innej lokalizacji, na przykład w SharePoint dokumentów. Taka procedura jest oparta na starszym stylu pracy, w którym informacje są przechowywane w plikach i folderach, a komunikacja jest prowadzona za pośrednictwem poczty e-mail.

W poniższej tabeli przedstawiono usługi skojarzone z grupami i zespołami oraz kluczowe typy zawartości w każdej z nich:

|Usługa|Typy zawartości|
|:------|:---------------|
|Teams|Konwersacje na kanale, pliki w kanałach|
|Formularze|Struktura i wyniki ankiety|
|OneNote|Notes|
|Outlook|Poczta i kalendarz|
|Planner|Project o stanie i o zadaniu|
|Power Automate|Przepływy pracy|
|Power BI|Dane, raporty i pulpity nawigacyjne|
|Project w sieci Web|plany Project-|
|Plan rozwoju|Plany|
|SharePoint|Pliki, listy i dane Teams wiki kanału|
|Stream|Filmy|
|Yammer|Konwersacje|

Podczas usuwania grupy lub zespołu większość skojarzonych zasobów również jest usuwana. Wyjątki obejmują:

- Klipy wideo w uścisieniu pozostaną i będą własnością osoby, która je przesłała/nagrała
- Przepływy Power Automate pozostają własnością osoby, która je utworzyła.
- Project i dane planu w Project sieci Web pozostają na dyskach CDS i można je przywrócić oddzielnie.

Grupy i zespoły pozostają w stanie "miękkiego usunięcia" przez 30 dni i można je przywrócić w dowolnym momencie. Jednak po upływie tych 30 dni i wszystkich skojarzonych zasobów, takich jak usługi i zawartość, zostaną wyczyszone ze środowiska Microsoft 365. Każda zawartość chroniona przez zasady przechowywania pozostaje dostępna w ramach wyszukiwań zbierania elektronicznych materiałów dowodowych.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Zagadnienia dotyczące cyklu życia usług połączonych grupami

Istnieją trzy kluczowe obszary, które właściciele zespołu i grupy oraz administratorzy IT muszą rozważyć podczas usuwania grupy lub zespołu.

**Content (Zawartość)**

Czy po zakończeniu pracy zespołu zawartość musi zostać zachowana? Czy wystarczy opierać się na możliwościach przechowywania Microsoft 365, czy też niektóre treści w aplikacjach i usługach, które nie oferują przechowywania? Czy zawartość musi być zachowana do celów zarządzania rekordami, archiwizacji lub do użytku w przyszłości i do celów referencyjnych?

Aby uniknąć potencjalnej utraty danych, należy zadać te pytania, zanim zespół zostanie zarchiwizowany lub usunięty.

**Usługi**

Czy zawartość musi pozostać w bieżącej formie roboczej? Czy na przykład raport Power BI będzie nadal dostępny? Czy wyniki formularza muszą być dostępne w wizualnym widoku podsumowania? Czy listy w programie SharePoint z których są połączone, czy osadzone w dowolnym miejscu?

Te pytania muszą zostać zadane przed usunięciem grupy źródłowej, ponieważ eksportowanie zawartości może nie być wystarczające.

**Goście**

Gdy goście są zapraszani do zespołu, w skoroszycie organizacji goszowej jest tworzone konto Azure Active Directory przed dodaniem ich do zespołu. Po usunięciu zespołu goście nie są usuwani z Azure Active Directory. Mimo że goście nie mogą uzyskać dostępu do grup, witryn, zespołów ani zawartości, które nie zostały im udostępnione, nadal mogą korzystać z funkcji w obrębie usługi Microsoft Teams takich jak rozpoczynanie czatów, połączeń głosowych i wideo oraz korzystanie z aplikacji.

Właściciel zespołu lub grupy może zaprosić kogoś spoza organizacji, aby stał się Azure Active Directory w zespole, dodając go do zespołu. Właściciel zespołu nie może jednak usunąć gościa z Azure Active Directory. Usuwanie kont może wykonać tylko administrator globalny lub administrator użytkownika.

Ważne jest, aby przeglądać gości i sprawdzać, czy należy ich usuwać Azure Active Directory usunięcia zespołu. W katalogu może być prawidłowa sprawa, w której goście mogą pozostać w katalogu, na przykład jako członek innych zespołów lub używając innych usług firmy Microsoft 365 lub Azure.

## <a name="teams"></a>Teams

Teams określonej zawartości głównie w formie konwersacji.

Konwersacji w kanałach nie można kopiować ani przenosić przy użyciu natywnych funkcji Microsoft Teams kanałów. Można je jednak eksportować przy użyciu interfejsu API Graph API.

Ponadto jeśli do programu są stosowane zasady przechowywania Teams konwersacje są zachowywane i dostępne za pośrednictwem wyszukiwań zbierania elektronicznych materiałów dowodowych. Za pomocą zaawansowanego zbierania elektronicznych materiałów dowodowych możesz [odtworzyć konwersację Teams na czacie](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Archiwizowanie zespołu

Zaletą [archiwizacji zespołu jest](/microsoftteams/archive-or-delete-a-team) to, że zapewnia on pełny dostęp do zespołu w taki sposób, w który był. Użytkownicy nadal mogą przeglądać konwersacje w kanale i otwierać pliki, nawet jeśli nie są aktywni. Ponadto zespoły mogą mieć niezaarchiwowane, jeśli istnieje potrzeba kontynuowania pracy nad nimi (na przykład w przypadku przedłużenia projektu).

W przypadku archiwizowania zespołu przez właściciela jest ustawiane ustawienie tylko do odczytu dla członków zarówno dla zawartości w zespole, jak i dla skojarzonej SharePoint zespołu. Celem tej akcji jest zagwarantowanie, że konwersacje w kanałach będą zachowywane w istniejącym stanie, podobnie jak SharePoint zawartości opartej na wiadomościach, takiej jak pliki i strony typu wiki.

W SharePoint witryny nie ma żadnych widocznych zmian. Jednak nie można wprowadzać żadnych zmian w żadnych plikach ani na listach, ponieważ dla grupy SharePoint dla grupy Microsoft 365 jest ustawiona wartość **Odwiedzający witrynę**. Obejmuje to OneNote zespołu, który jest przechowywany w bibliotece Elementy zawartości witryny w obrębie SharePoint witryny.

W przypadku zarchiwizowania zespołu grupa Microsoft 365 nadal podlega zasadom wygasania (jeśli została ustawiona), a zatem właściciel musi nadal odnawiać zespół.

Konwersacje zespołu i zawartość SharePoint są ustawione jako tylko do odczytu, ale nie są stosowane do innych skojarzonych usług:

- Zasobniki i zadania programu Planner nadal można tworzyć, modyfikować i usuwać.
- Formularze nadal mogą odbierać przesłania.
- Skrzynka Outlook nadal może odbierać wiadomości e-mail.
- Power BI, raporty i dane nadal można modyfikować.
- Projekty i plany nadal można edytować w Project sieci Web.
- Klipy wideo nadal można przesyłać, modyfikować i usuwać w uścisce Stream.
- Przepływy Power Automate nadal można tworzyć, modyfikować, usuwać i nadal działać. (Nie będą jednak w stanie opublikować wiadomości w kanale zarchiwizowanego zespołu).

## <a name="forms"></a>Formularze

Mimo że formularz można przenieść z pojedynczego konta do grupy, nie można go przenosić ani kopiować z jednej grupy do drugiej. Po usunięciu zespołu dostępne są trzy opcje formularza.

**Duplikowanie formularza**

Formularze można [udostępniać jako szablony](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), dzięki czemu inni użytkownicy mogą je kopiować na własne konto lub do grupy. Nie spowoduje to zachowania danych z przesyłania wyników; tylko struktura formularza, taka jak pytania i ustawienia.

**Eksportowanie wyników do arkusza kalkulacyjnego**

Jeśli dane odpowiedzi na formularz muszą zostać zachowane, można to uzyskać, eksportując wyniki do arkusza kalkulacyjnego Excel [kalkulacyjnym](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Spowoduje to wyeksportowanie pytań i ich odpowiedzi jako danych — nie obejmuje to schematów utworzonych przez formularze.

**Usuwanie formularza**

Usunięcie grupy spowoduje również usunięcie wszystkich skojarzonych formularzy, a członkowie grupy mogą je usuwać bezpośrednio[](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0), nie będąc właścicielem grupy. Jest to jednak etap ręczny, który nie zapewnia żadnych dodatkowych korzyści.

## <a name="onenote"></a>OneNote

Notes OneNote grupy jest przechowywany w bibliotece Zasoby witryny w skojarzonej SharePoint witryny. Pliki notesów czasami można rozłożyć na wiele pojedynczych plików, ale nie można ich kopiować ani otwierać niezależnie. Zamiast tego zawartość notesu OneNote zostać przeniesiona lub wyeksportowana przy użyciu programu OneNote 2016.

**Przenoszenie stron i sekcji do innego notesu**

[Pojedyncze przenoszenie stron lub sekcji](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) do innego notesu daje właścicielom możliwość oczyszczenia ich danych i podjęcia tylko tego, co należy zachować.

**Eksportowanie całego notesu jako pakietu**

Jeśli cały notes musi zostać zachowany przy użyciu jego istniejącej struktury, można go wyeksportować jako plik pakietu OneNote[, a](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) następnie zaimportować do nowej lokalizacji. Zamiast istniejącej struktury wielu plików można użyć jej jako metody zachowania zawartości w jednym pliku.

**Drukowanie w formacie PDF**

W scenariuszach, w których część zawartości notesu musi zostać zachowana tylko w celu odwołania lub jako rekordy, pojedyncze strony mogą być drukowane do formatu PDF i przechowywane [w innym miejscu](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Skrzynka pocztowa i kalendarz

Nie jest rzadkością, w związku z tym, że skrzynka pocztowa skojarzona z grupą może być używana, mimo że w kanałach zespołu może być prowadzonych wiele konwersacji. Skrzynka pocztowa przechowuje tylko wiadomości e-mail, do których bezpośrednio wysłano wiadomość e-mail, i nie zawiera wiadomości e-mail wysłanych bezpośrednio do kanałów.

W niektórych przypadkach wiadomości e-mail przechowywane w skrzynce pocztowej mogą być powiadomieniami o spotkaniach, aktualizacjach zadań usługi Planner i innych wiadomościach generowanych przez aplikację lub system. ważne jest, aby zawartość skrzynki pocztowej była przeglądana w celu określenia, czy zawartość powinna zostać zachowana, czy usunięta.

Jeśli zasady przechowywania są stosowane w programie Exchange, wiadomości e-mail i elementy kalendarza są zachowywane i dostępne w ramach wyszukiwań zbierania elektronicznych materiałów dowodowych.

**Eksportowanie poczty i kalendarza**

Członkowie zespołu lub grupy mogą eksportować zawartość skrzynki pocztowej i kalendarza do pliku danych Outlook [/Osobiste Storage (PST](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91)). Ten plik można następnie przechowywać w innym miejscu lub można zaimportować zawartość do innej skrzynki pocztowej. Nie zaleca się wyszukiwania zawartości pliku PST bez otwarcia go w programie Outlook, a sam plik może z czasem ulec uszkodzeniu.

**Migracja zawartości wykonywana przez it**

Administratorzy mogą używać narzędzi innych firm do migrowania poczty e-mail i zawartości kalendarza między skrzynkami pocztowymi bez interwencji użytkownika. Jedną z potencjalnych lokalizacji przechowywania może być udostępniona skrzynka pocztowa utworzona tylko po to, aby służyła jako "archiwum" zawartości skrzynki pocztowej grupy.

## <a name="planner"></a>Planner

Każda grupa lub zespół może mieć wiele planów. Podczas procesu wynoszania należy zadbać o to, aby w poszczególnych planach zostały spełnione wymagania przechowywania. Podobnie jak w przypadku innych usług, zawartość poza tablicą jest podejrzeń do usługi Planner na kilka sposobów.

**Eksportowanie planu do arkusza kalkulacyjnego**

Jeśli przechowywanie kopii planu jest wymagane tylko w celu przechowywania dokumentacji, najprostszym rozwiązaniem jest wyeksportowanie planu do arkusza kalkulacyjnego Excel [danych](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Jest to akcja jednokierunkowa — nie ma opcji importowania planów z arkusza kalkulacyjnego.

> [!IMPORTANT]
> Eksportowanie planu do programu Excel będzie zawierać większość informacji w ramach planu, ale nie będzie zawierać komentarzy, linków ani plików.

**Kopiowanie i przenoszenie zadań do innego planu**

Kopiowanie lub przenoszenie zadań do innego planu wydaje się rozwiązaniem, jednak pojedyncze zadania można kopiować lub przenosić tylko między planami [w](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) obrębie tej samej grupy. Nie spowoduje to zapasowej kopii danych, jeśli grupa skojarzona z planem zostanie usunięta.

**Kopiowanie całego planu**

Można też skopiować [cały plan](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Nie można kopiować danych do istniejącej grupy. Skopiowanie planu spowoduje utworzenie nowej grupy. Ponadto kopiowanie całego planu nie będzie zawierać komentarzy, zadań, linków, załączników ani dat.

## <a name="power-automate"></a>Power Automate

Przepływy utworzone Power Automate skojarzone z grupą lub zespołem nie należą do grupy. Są one własnością autora i są udostępniane jedynie innym użytkownikom i grupom. W związku z tym nie będzie to mieć wpływu na usunięcie grupy lub zespołu.

**Zmienianie własności przepływu**

Jeśli przepływ będzie wymagał dalszego działania, dowolny właściciel może dodać innych użytkowników lub Microsoft 365 jako właścicieli.

**Eksportowanie przepływu**

Jeśli przepływ nie wymaga dalszej pracy, ale musi zostać zachowany, aby można go było użyć w przyszłości, można wyeksportować go jako plik i zaimportować ponownie później.[](https://flow.microsoft.com/blog/import-export-bap-packages/)

## <a name="power-bi"></a>Power BI

Power BI danych i obszarów roboczych mogą działać niezależnie od grup i zespołów, podobnie jak inne obciążenia pracą oferują różne sposoby pracy poza pracą.

**Kopiowanie raportów do innego obszaru roboczego**

Jeśli potrzebujesz tego raportu po usunięciu grupy lub zespołu, możesz go skopiować z istniejącego obszaru roboczego do innego obszaru roboczego w [obrębie Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Eksportowanie danych z pulpitu nawigacyjnego lub raportu**

Jeśli raport nie musi już być aktywny, ale dane muszą zostać zachowane, można je wyeksportować do [Excel.](/power-bi/visuals/power-bi-visualization-export-data)

## <a name="project"></a>Project

Projekty i plany utworzone w aplikacji Project dla sieci Web są skojarzone z grupami usługi Microsoft 365 i mają metody wytyczania tak jak Power BI.

**Przypisywanie projektu do innej grupy**

Jeśli projekt wymaga zachowywania w stanie funkcjonalnym poza okresem życia grupy lub zespołu, można przypisać go do innej Microsoft 365 [grupy](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Można to zrobić przy użyciu Centrum administracyjnego usługi Dynamics 365.

**Eksportowanie danych z projektu lub planu**

Za pomocą Centrum administracyjnego usługi Dynamics 365 można eksportować dane użytkowników z [projektu](/project-for-the-web/export-user-data-from-project-for-the-web) do arkusza kalkulacyjnego. Dane można również wyeksportować do Project pliku (. formaty plików MPP) i XML przy użyciu programu PowerShell.

## <a name="sharepoint"></a>SharePoint

Wszystkie pliki w kanałach zespołu są przechowywane w SharePoint witryny skojarzonej grupy. W niektórych przypadkach w dokumentach może istnieć zawartość inna SharePoint, na przykład listy lub strony.

Pliki są zazwyczaj przechowywane w trzech głównych lokalizacjach w SharePoint lokalizacji:

- Strony — biblioteka stron witryny
- Obrazy używane na stronach — biblioteka Zasoby witryny
- Pliki w kanałach — biblioteka dokumentów
- Strony typu wiki — Teams danych typu wiki

Jeśli witryna ma jedną lub więcej podwitryn, proces wynoszania należy powtórzyć dla każdej z podwitryn. Jeśli zespół zawiera kanały prywatne, dla każdego SharePoint istnieje osobna witryna.

Podczas usuwania plików z grupy lub zespołu należy pamiętać, że mogą one być udostępniane użytkownikom, którzy nie są członkami grupy lub zespołu. Możesz także zakomunikować im zbliżającą się zmianę.

**Pobieranie plików**

Pliki przechowywane w SharePoint w jednej z wymienionych powyżej bibliotek można [pobrać na komputer lokalny](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Przenoszenie plików**

Ponadto pliki można przenosić do innej lokalizacji w [SharePoint, na przykład do biblioteki w innej witrynie](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Eksportowanie listy**

Dane przechowywane w SharePoint można wyeksportować do arkusza kalkulacyjnego programu [Excel](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) i zaimportować ponownie do listy w innej witrynie.

Ewentualnie można użyć narzędzia innej firmy do przeprowadzenia migracji listy między witrynami w celu zachowania funkcji, widoków list, formatowania i innych atrybutów.

**"Eksportowanie" plików typu wiki**

Zawartość stron typu wiki w kanałach zespołu jest przechowywana w pliku w formacie HTML w dedykowanej bibliotece skojarzonej SharePoint zespołu. Nie można ich łatwo wyeksportować i zaimportować do witryny typu wiki innego kanału, ale można przekonwertować na plik HTML i otworzyć jako stronę sieci Web.

## <a name="microsoft-stream"></a>Microsoft Stream

Podobnie Power Automate wideo w układzie Stream skojarzone z grupą lub zespołem nie są w rzeczywistości własnością tej grupy i nie są usuwane po jej usunięciu. Klipy wideo w udatku Stream są własnością osoby, która przesłała lub utworzyła klip wideo, nawet jeśli dodaje użytkowników lub grupy jako właścicieli. Spotkania nagrywane w kanale Teams należą do osoby, która rozpoczęła nagrywanie.

**Dodawanie innych właścicieli**

Ponieważ po usunięciu grupy klip wideo jest zachowywany w użytą grupę, pierwotny właściciel może udostępnić go innym użytkownikom i grupom, nawet dodając ich [jako właścicieli](/stream/portal-edit-video).

**Pobierz klip wideo**

W scenariuszach, w których klip wideo nie musi być zachowany w układzie Strumieniowym lub musi być przechowywany w lokalizacji alternatywnej, takiej jak system zarządzania rekordami, właściciel może pobrać [go lokalnie](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

W przeciwieństwie do konwersacji Microsoft Teams, Yammer przenoszenie lub eksportowanie konwersacji oferuje zarówno użytkownikom, jak i administratorom opcje przenoszenia i eksportowania.

**Przenoszenie konwersacji do innej grupy lub społeczności**

Konwersacje mogą być przenoszone do Yammer grupy przez dowolnego użytkownika, nie tylko właścicieli i administratorów. Jest to możliwe zarówno w [klasycznej wersji Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872), jak i w [nowych Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) interfejsach użytkownika.

**Eksportowanie danych sieciowych**

Yammer sieci [eksportuje dane sieciowe](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Spowoduje to jednak wyeksportowanie wszystkich konwersacji dla całej sieci. Wynikowy eksport wyświetla identyfikator grupy. Konwersacje można filtrować na podstawie tego identyfikatora.

## <a name="related-topics"></a>Tematy pokrewne

[Usuwanie byłego pracownika i zabezpieczanie danych](/microsoft-365/admin/add-users/remove-former-employee)
