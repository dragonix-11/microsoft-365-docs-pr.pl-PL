---
title: Dowiedz się więcej na temat przechowywania SharePoint i OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak działa przechowywanie SharePoint i OneDrive.
ms.openlocfilehash: a553945fdb0b0034d8f3182164749b06badfe503
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013826"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>Dowiedz się więcej na temat przechowywania SharePoint i OneDrive

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Informacje zawarte w tym artykule uzupełnia informacje [dotyczące przechowywania,](retention.md) ponieważ zawierają informacje specyficzne dla SharePoint i OneDrive.

W przypadku innych obciążeń, zobacz:

- [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md)
- [Informacje na temat przechowywania danych dla Yammer](retention-policies-yammer.md)
- [Dowiedz się więcej na temat przechowywania Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co obejmuje przechowywanie i usuwanie

Wszystkie pliki przechowywane w SharePoint lub OneDrive można zachować, stosując zasady przechowywania lub etykiety przechowywania. 

Można usunąć następujące pliki:

- W przypadku korzystania z zasad przechowywania: Wszystkie pliki w bibliotekach dokumentów, które zawierają wszystkie automatycznie utworzone w SharePoint dokumentów, takie jak **Zasoby witryny**.
    
- W przypadku korzystania z etykiet przechowywania: Wszystkie pliki we wszystkich bibliotekach dokumentów i wszystkie pliki na poziomie głównym, które nie są w folderze.
    
> [!TIP]
> Jeśli używasz zapytania [z zasadami automatycznego](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties) stosowania do etykiety przechowywania, możesz wykluczyć określone biblioteki dokumentów, używając następującego wpisu: `NOT(DocumentLink:"<URL to document library>")`

Elementy listy nie są obsługiwane przez zasady przechowywania, ale są obsługiwane przez etykiety przechowywania z wyjątkiem elementów na listach systemowych. Są to ukryte listy używane przez firmę SharePoint do zarządzania systemem i obejmują katalog stron wzorcowych, wykaz rozwiązań i źródła danych. Etykiety przechowywania stosowane do obsługiwanych elementów listy są zawsze zachowywane zgodnie z ustawieniami przechowywania, ale nie są usuwane, jeśli są ukryte przed wyszukiwaniem.

Po zastosowaniu etykiety przechowywania do obsługiwanego elementu listy, który ma załącznik dokumentu:
- W przypadku standardowej etykiety przechowywania (nie deklaruje elementu jako rekordu):
    - Załącznik dokumentu nie dziedziczy automatycznie ustawień przechowywania etykiety, ale można go o etykiecie ustawić niezależnie.
- W przypadku etykiety przechowywania deklarowania elementu jako rekordu: 
    - Załącznik dokumentu automatycznie dziedziczy ustawienia przechowywania po etykiecie, jeśli dokument nie jest jeszcze oznaczony etykietą.

Ustawienia przechowywania na podstawie zasad przechowywania i etykiet przechowywania nie dotyczą struktur porządkowania, które zawierają biblioteki, listy i foldery.

W przypadku zasad przechowywania i automatycznego stosowania zasad etykiet: SharePoint witryn muszą być indeksowane, aby ustawienia przechowywania, które mają zostać zastosowane. Jeśli jednak elementy w SharePoint dokumentów są skonfigurowane tak, aby nie były wyświetlane w wynikach wyszukiwania, ta konfiguracja nie powoduje wykluczenia plików z ustawień przechowywania.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Jak działa przechowywanie w SharePoint i OneDrive

Aby przechowywać zawartość, która ma zostać zachowana, można SharePoint a OneDrive utworzyć bibliotekę Hold zachowywania, jeśli nie istnieje dla witryny. Biblioteka Hold (Przechowywanie) nie jest przeznaczona do interakcyjnego korzystania, ale zamiast tego automatycznie przechowuje pliki, gdy jest to konieczne ze względu na zgodność z przepisami. Działa to w następujący sposób:

Gdy użytkownik zmieni lub usunie element, który podlega przechowywaniem, jest sprawdzana, czy zawartość została zmieniona od momentu zastosowania ustawień przechowywania. Jeśli jest to pierwsza zmiana od momentu zastosowania ustawień przechowywania, zawartość jest kopiowana do biblioteki Zachowywanie, co pozwala użytkownikowi zmienić lub usunąć oryginalną zawartość.

Zadanie czasomierza okresowo działa w bibliotece Hold(Hold) zachowywania. W przypadku zawartości, która była przez ponad 30 dni w bibliotece zachowywania, to zadanie porównuje zawartość ze wszystkimi zapytaniami używanymi przez ustawienia przechowywania dla tej zawartości. Zawartość, która jest starsza niż skonfigurowany okres przechowywania, jest następnie usuwana z biblioteki Zachowywanie i z oryginalnej lokalizacji, jeśli nadal tam jest. To zadanie czasomierza jest uruchamiane co siedem dni, co oznacza, że usunięcie zawartości z biblioteki hold zachowywania może potrwać co najmniej 30 dni.

To zachowanie w przypadku kopiowania plików do biblioteki wstrzymywania ma zastosowanie do zawartości, która istnieje po zastosowaniu ustawień przechowywania. Ponadto w przypadku zasad przechowywania każda nowa zawartość, która została utworzona lub dodana do witryny po jej dodaniu do zasad, będzie zachowywana w bibliotece Hold (Przechowywanie). Jednak nowa zawartość nie jest kopiowana do biblioteki Zachowywanie podczas pierwszej edycji, tylko po jej usunięciu. Aby zachować wszystkie wersje [pliku, należy](#how-retention-works-with-document-versions) włączona przechowywania wersji dla oryginalnej witryny.
  
Użytkownicy widzą komunikat o błędzie, jeśli próbują usunąć bibliotekę, listę, folder lub witrynę, które podlegają zatrzymaniu. Mogą oni usunąć folder, jeśli najpierw przesuną lub usuną wszystkie pliki w folderze, które podlegają przechowywania.

Użytkownicy mogą również zobaczyć komunikat o błędzie, jeśli w dowolnej z poniższych sytuacji spróbują usunąć element oznaczony etykietą. Element nie zostanie skopiowany do biblioteki Zachowywanie, ale pozostanie w pierwotnej lokalizacji:

- Ustawienie zarządzania rekordami, które umożliwia użytkownikom usuwanie elementów oznaczonych etykietą, jest wyłączone.
    
    Aby sprawdzić lub zmienić to ustawienie, przejdź do rozwiązania  do zarządzania rekordami w Centrum zgodności platformy Microsoft 365 > **Zarządzanie** >  >  >  rekordamiUzyskania zarządzaniaRekordami Etykiety rekordówNalepki **elementów**. Istnieją osobne ustawienia dla SharePoint i OneDrive.
    
    Ewentualnie, jeśli nie masz dostępu do rozwiązania do zarządzania rekordami, możesz użyć polecenia *AllowFilesWithKeepLabelToBeDeletedSPO* i *AllowFilesWithKeepLabelToBeDeletedODB* z usługi [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) i [Set-PnPTenant](/powershell/module/sharepoint-pnp/set-pnptenant).

- Etykieta przechowywania oznacza elementy jako rekord i jest [on zablokowany](record-versioning.md).
    
    Tylko po odblokowaniu rekordu kopia ostatniej wersji jest przechowywana w bibliotece Hold (Przechowywanie).

- Etykieta przechowywania oznacza elementy jako rekord [wymogów](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) prawnych, co zawsze uniemożliwia edycję lub usunięcie elementu.

Po przypisaniu ustawień przechowywania do zawartości na koncie programu OneDrive lub w witrynie programu SharePoint ścieżki, jakie może trwać ta zawartość, zależą od tego, czy ustawienia przechowywania mają być zachowywane, usuwane, zachowywane tylko, czy tylko usunięte.

Zachowanie i usunięcie ustawień przechowywania:

![Diagram cyklu życia zawartości w SharePoint i OneDrive.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Jeśli zawartość zostanie zmodyfikowana lub** usunięta w okresie przechowywania, w bibliotece zasad zachowywania będzie tworzona kopia oryginalnej zawartości, jaka istniała podczas przypisywania ustawień przechowywania. Zadanie czasomierza identyfikuje elementy, których okres przechowywania wygasł. Te elementy są przenoszone do Kosza drugiego poziomu, gdzie są trwale usuwane po 93 dniach. Kosz drugiego poziomu nie jest widoczny dla użytkowników końcowych (jest tylko Kosz pierwszego poziomu), ale administratorzy zbiorów witryn mogą wyświetlać i przywracać w tym miejscu zawartość.

    > [!NOTE]
    > Aby zapobiec przypadkowej utracie danych, nie usuwamy już trwale zawartości z biblioteki Zbierania. Zamiast tego trwale usuwamy tylko zawartość z Kosza, więc cała zawartość z biblioteki Wstrzymanie zachowywania przechodzi teraz przez Kosz drugiego poziomu.
    
2. **Jeśli zawartość nie zostanie zmodyfikowana ani** usunięta w trakcie okresu przechowywania, zadanie czasomierza przeniesie tę zawartość do Kosza pierwszego poziomu na koniec okresu przechowywania. Jeśli użytkownik usunie z tego Kosza zawartość lub opróżni go (nazywany też czyszczeniem), dokument zostanie przeniesiony do Kosza drugiego poziomu. 93-dniowy okres przechowywania obejmuje zarówno Kosz pierwszego, jak i drugiego poziomu. Po 93 dniach dokument jest trwale usuwany z miejsca, w którym się znajduje, w Koszu pierwszego lub drugiego poziomu. Kosz nie jest indeksowany i dlatego nie jest dostępny do wyszukiwania. W wyniku tego wyszukiwanie zbierania elektronicznych materiałów dowodowych nie może znaleźć żadnej zawartości Kosza, na której ma zostać zawieszone.

> [!NOTE]
> Ze względu na pierwszą zasadę przechowywania trwałe usuwanie jest zawsze [zawieszone, jeśli](retention.md#the-principles-of-retention-or-what-takes-precedence) ten sam element musi zostać zachowany ze względu na inne zasady przechowywania lub etykietę przechowywania albo jest on w ramach zbierania elektronicznych materiałów dowodowych ze względów prawnych lub badawczych.

Jeśli ustawienia przechowywania są dostępne tylko do zachowania lub tylko do usuwania, ścieżki zawartości są odmianami zachowania i usuwania:

### <a name="content-paths-for-retain-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania z zachowaniem tylko

1.  Jeśli zawartość zostanie zmodyfikowana lub usunięta w okresie przechowywania: W bibliotece zachowanej jest tworzona kopia oryginalnego dokumentu, która jest zachowywana do końca okresu przechowywania, po tym, jak kopia w bibliotece hold(a) przechowywania jest przenoszony do Kosza drugiego poziomu i jest trwale usuwana po 93 dniach.

2. **Jeśli zawartość nie została zmodyfikowana ani usunięta** w trakcie okresu przechowywania: Nic się nie dzieje przed i po okresie przechowywania; dokument pozostanie w pierwotnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania tylko do usuwania

1. **Jeśli zawartość zostanie usunięta** w skonfigurowanym okresie: Dokument zostanie przeniesiony do Kosza pierwszego poziomu. Jeśli użytkownik usunie z tego kosza dokument lub opróżni go, dokument zostanie przeniesiony do Kosza drugiego poziomu. 93-dniowy okres przechowywania obejmuje zarówno Kosz pierwszego, jak i Drugiego Poziomu. Po 93 dniach dokument jest trwale usuwany z miejsca, w którym się znajduje, w Koszu pierwszego lub drugiego poziomu. Jeśli zawartość jest modyfikowana w trakcie skonfigurowanego okresu, po upływie skonfigurowanego okresu jest następująca ta sama ścieżka usuwania.

2. **Jeśli zawartość nie zostanie** usunięta w trakcie skonfigurowanego okresu: Na koniec skonfigurowanego okresu w zasadach przechowywania dokument jest przenoszony do Kosza pierwszego poziomu. Jeśli użytkownik usunie z tego kosza dokument lub opróżni go (nazywany też czyszczeniem), dokument zostanie przeniesiony do Kosza drugiego poziomu. 93-dniowy okres przechowywania obejmuje zarówno Kosz pierwszego, jak i Drugiego Poziomu. Po 93 dniach dokument jest trwale usuwany z miejsca, w którym się znajduje, w Koszu pierwszego lub drugiego poziomu. Kosz nie jest indeksowany i dlatego nie jest dostępny do wyszukiwania. W wyniku tego wyszukiwanie zbierania elektronicznych materiałów dowodowych nie może znaleźć żadnej zawartości Kosza, na której ma zostać zawieszone.

## <a name="how-retention-works-with-cloud-attachments"></a>Jak działa przechowywanie w przypadku załączników w chmurze

Załączniki w chmurze są osadzonymi linkami do plików, które są współużytkowane przez użytkowników i można je zachowywać i usuwać, gdy użytkownicy Outlook wiadomości e-mail Teams wiadomościach. Gdy [etykieta przechowywania jest automatycznie](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments) stosowana do załączników w chmurze, etykieta przechowywania jest stosowana do kopii pliku udostępnionego, która jest przechowywana w bibliotece hold.zachowywania.

W tym scenariuszu zalecamy skonfigurowanie ustawienia etykiety w celu rozpoczęcia okresu przechowywania na podstawie etykiety elementu. Jeśli skonfigurujesz okres przechowywania na podstawie daty utworzenia lub ostatniej modyfikacji elementu, data ta jest tworzona z pierwotnego pliku w momencie udostępniania. Jeśli czas rozpoczęcia przechowywania zostanie skonfigurowany tak, aby był modyfikowany po ostatniej modyfikacji, to ustawienie nie będzie mieć wpływu na tę kopię w bibliotece Hold (Przechowywanie).

Jeśli jednak oryginalny plik zostanie zmodyfikowany, a następnie udostępniony ponownie, nowa kopia pliku w nowej wersji zostanie zapisana i oznaczona etykietą w bibliotece Hold (Przechowywanie).

Jeśli oryginalny plik zostanie ponownie udostępniony, ale nie zmodyfikowany, data kopii w bibliotece Zachowywanie zostanie zaktualizowana z etykietą. Ta akcja powoduje zresetowanie początku okresu przechowywania i dlatego zalecamy skonfigurowanie początku okresu przechowywania na podstawie etykiety elementu.

Ponieważ etykieta przechowywania nie jest stosowana do oryginalnego pliku, użytkownik nigdy nie jest modyfikowany ani usuwany. Oznaczony plik pozostaje w bibliotece Zachowywanie do momentu, aż zadanie czasomierza zidentyfikuje, że jego okres przechowywania wygasł. Jeśli ustawienia przechowywania są skonfigurowane do usuwania elementów, plik jest następnie przenoszony do Kosza drugiego poziomu, gdzie jest trwale usuwany po 93 dniach:

![Jak działa przechowywanie załączników w chmurze przechowywanych w SharePoint i OneDrive](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

Kopia przechowywana w bibliotece Zachowywanie jest zazwyczaj tworzona w ciągu godziny od udostępnianego załącznika w chmurze.

## <a name="how-retention-works-with-onenote-content"></a>Jak działa przechowywanie OneNote zawartości

Po zastosowaniu zasad przechowywania do lokalizacji zawierającej zawartość programu OneNote lub etykiety przechowywania do folderu usługi OneNote w tle inne strony i sekcje programu OneNote to pojedyncze pliki dziedziczące ustawienia przechowywania. Oznacza to, że każda sekcja na stronie zostanie indywidualnie zachowana i usunięta zgodnie z ustawieniami przechowywania, które określisz.

Ustawienia przechowywania określone przez użytkownika mają wpływ tylko na strony i sekcje. Na przykład dla każdego notesu **jest na przykład** data Zmodyfikowano, ale nie jest ona używana przez Microsoft 365 przechowywania.

## <a name="how-retention-works-with-document-versions"></a>Jak działa przechowywanie w wersjach dokumentów

Versioning is a feature of all document lists and libraries in SharePoint and OneDrive. Domyślnie przechowywania wersji zachowuje co najmniej 500 wersji głównych, chociaż można zwiększyć ten limit. Aby uzyskać więcej informacji, [zobacz Włączanie i konfigurowanie obsługi](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) wersji dla listy lub biblioteki oraz Jak [działa wersja na listach i w bibliotekach](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247).
  
Jeśli dokument z wersjami podlega ustawień przechowywania w celu zachowania tej zawartości, wersje, które są kopiowane do biblioteki holdu zachowania, istnieją jako osobny element. Jeśli na koniec okresu przechowywania skonfigurowano usuwanie ustawień przechowywania:

- Jeśli okres przechowywania jest oparty na czasie tworzenia zawartości, każda wersja ma tę samą datę wygaśnięcia co oryginalny dokument. Jednocześnie wygasa oryginalny dokument i jego wersje.

- Jeśli okres przechowywania jest oparty na dacie ostatniej modyfikacji zawartości, każda wersja ma własną datę wygaśnięcia, zależnie od tego, kiedy oryginalny dokument został zmodyfikowany w celu utworzenia tej wersji. Oryginalny dokument i jego wersje wygasają niezależnie od siebie.

Gdy akcja przechowywania ma na celu usunięcie dokumentu, wszystkie wersje, które nie znajdują się w bibliotece Przechowywanie, są usuwane jednocześnie zgodnie z bieżącą wersją.

W przypadku elementów podlegających zasadom przechowywania (lub zbierania elektronicznych materiałów dowodowych) limity przechowywania wersji biblioteki dokumentów są ignorowane do momentu osiągnięciu okresu przechowywania dokumentu (lub do czasu zbierania elektronicznych materiałów dowodowych). W tym scenariuszu stare wersje nie są automatycznie czyszowane i użytkownicy nie mogą usuwać wersji.

Nie dzieje się tak w przypadku etykiet przechowywania, gdy zawartość nie podlega zasadom przechowywania (ani holdowi zbierania elektronicznych materiałów dowodowych). Zamiast tego są uwzględniane limity dotyczące wersji, dzięki czemu starsze wersje są automatycznie usuwane w celu uwzględnienia nowych wersji, ale użytkownicy nadal nie mogą usuwać wersji.

## <a name="when-a-user-leaves-the-organization"></a>Kiedy użytkownik odchodzi z organizacji

**SharePoint**:

Odejmowanie od organizacji użytkownika nie wpływa na zawartość utworzoną przez tego użytkownika, ponieważ SharePoint jest uważane za środowisko współpracy, w przeciwieństwie do skrzynki pocztowej lub konta OneDrive użytkownika.

**OneDrive**:

Jeśli użytkownik opuści organizację, wszelkie pliki, które podlegają zasadom przechowywania lub mają etykietę przechowywania, pozostaną objęte ustawieniami przechowywania przez czas trwania okresu przechowywania określonego w zasadach lub etykiecie. W tym czasie cały dostęp do udostępniania będzie nadal działać, a zawartość będzie nadal wykrywana przez przeszukiwanie zawartości i zbierania elektronicznych materiałów dowodowych. 

Gdy okres przechowywania wygasa, a ustawienia przechowywania zawierały akcję usuwania, zawartość jest przesułączona do Kosza zbioru witryn i nie jest dostępna dla nikogo poza administratorem.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli nie wiesz, jak konfigurować przechowywanie w aplikacji Microsoft 365, zobacz [Wprowadzenie do zarządzania informacjami](get-started-with-information-governance.md).

Jeśli możesz już skonfigurować zasady przechowywania lub etykiety przechowywania dla aplikacji Exchange, zobacz następujące instrukcje:
- [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md)
- [Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)