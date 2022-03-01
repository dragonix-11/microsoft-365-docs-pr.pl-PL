---
title: Tworzenie i stosowanie zasad zarządzania informacjami
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 8ccac9e4-3a50-49fa-a95b-d186032a6ee3
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak skonfigurować zasady zarządzania informacjami w celu kontrolowania, jak długo informacje są przechowywane i śledzenia, kto korzysta z tych informacji.
ms.openlocfilehash: f8a4400e890e02ecd7ac57011770ff4a23a1a5e1
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013827"
---
# <a name="create-and-apply-information-management-policies"></a>Tworzenie i stosowanie zasad zarządzania informacjami

Zasady zarządzania informacjami umożliwiają organizacji kontrolowanie, jak długo zawartość jest zachowywana, inspekcja działań użytkowników z zawartością oraz dodawanie kodów kreskowych lub etykiet do dokumentów. Zasady mogą ułatwić egzekwowanie zgodności z przepisami prawnymi i rządowymi lub wewnętrznymi procesami biznesowymi. Jako administrator możesz skonfigurować zasady sterujące tym, jak śledzić dokumenty i jak długo mają być zachowywane dokumenty.

Zasady zarządzania informacjami można tworzyć w trzech różnych miejscach hierarchii witryn, od najszerszej do najwęższych:

- Tworzenie zasad w celu używania wielu typów zawartości w zbiorze witryn.
- Tworzenie zasad dla typu zawartości witryny.
- Tworzenie zasad dla listy lub biblioteki.

Aby uzyskać więcej informacji, [zobacz Wprowadzenie do zasad zarządzania informacjami](intro-to-info-mgmt-policies.md).

## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Tworzenie zasad dla wielu typów zawartości w zbiorze witryn
<a name="__toc261001590"> </a>

Aby mieć pewność, że zasady informacyjne będą stosowane do wszystkich dokumentów określonego typu w zbiorze witryn, rozważ utworzenie zasad na poziomie zbioru witryn, a następnie ich stosowanie do typów zawartości. Są one nazywane zasadami zbioru witryn.

1. Na stronie głównej zbioru **Ustawienia**![\> SharePoint 2016 Ustawienia na pasku tytułu.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Witryna Ustawienia**.

    W witrynie SharePoint połączonej z grupą kliknij pozycję Zawartość **Ustawienia****, a następnie** kliknij pozycję **Zawartość witryny Ustawienia**.

2. Na stronie Ustawienia w obszarze Szablony zasad typu zawartości **Administracja** \> zbiorem **witryn**.

   ![Link Szablon zasad typu zawartości na Ustawienia witryny.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Na stronie Zasady utwórz \> **.**

4. Wprowadź nazwę i opis zasad, a następnie wpisz krótką oświadczenie o zasadach objaśniace użytkownikom, do czego służy zasada.

5. Zobacz następną sekcję na temat tworzenia zasad dla typu zawartości witryny, aby dowiedzieć się, jak skonfigurować funkcje, które chcesz skojarzyć z zasadami.

6. Wybierz pozycję **OK**.

## <a name="create-a-policy-for-a-site-content-type"></a>Tworzenie zasad dla typu zawartości witryny
<a name="__create_a_policy"> </a>

Dodanie zasad zarządzania informacjami do typu zawartości ułatwia kojarzenie funkcji zasad z wieloma listami lub bibliotekami. Możesz dodać istniejące zasady zarządzania informacjami do typu zawartości lub utworzyć unikatowe zasady specyficzne dla poszczególnych typów zawartości.

 Zasady zarządzania informacjami można również dodać do typu zawartości specyficznego dla list. Ma to wpływ na stosowanie zasad tylko do elementów na tej liście, które mają typ zawartości.

1. Na stronie głównej zbioru **Ustawienia**![\> SharePoint 2016 Ustawienia na pasku tytułu.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Witryna Ustawienia**.

    W witrynie SharePoint połączonej z grupą kliknij pozycję Zawartość **Ustawienia****, a następnie** kliknij pozycję **Zawartość witryny Ustawienia**.

2. Na stronie Ustawienia w obszarze **Typy zawartości witryny Galerie** \> **Projektanta sieci Web**.

   ![Link Typy zawartości witryny na Ustawienia witryny.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)

3. Na stronie Typ zawartości Ustawienia wybierz typ zawartości, do którego chcesz dodać zasady.

4. Na stronie Typ zawartości witryny w obszarze **Ustawienia** \> **zasad zarządzania informacjami**.

5. Na stronie Edytowanie zasad wprowadź nazwę i opis zasad, a następnie wpisz krótki opis wyjaśniacy użytkownikom, do czego służy zasada.

6. W następnych sekcjach wybierz poszczególne funkcje zasad, które chcesz dodać do zasad zarządzania informacjami.

   ![Typy zasad zawartości.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)

7. Aby określić okres przechowywania dla dokumentów i elementów podlegających tym zasadom, wybierz pozycję Włącz **przechowywanie, a** następnie określ okres przechowywania i akcje, które mają być podejmowane po wygaśnięciu elementów.

   Aby określić okres przechowywania:

   1. Wybierz **pozycję Dodaj etap przechowywania dla rekordów**.

   2. Wybierz opcję okresu przechowywania, aby określić, kiedy dokumenty lub elementy mają wygasać. Wykonaj jedną z następujących czynności:
      - Aby ustawić datę wygaśnięcia na podstawie właściwości daty,  \> w obszarze Zdarzenie Ten etap jest oparty na właściwości daty elementu, **a** następnie wybierz akcję dokumentu lub elementu (na przykład Utworzono lub Zmodyfikowano) oraz przyrost czasu po tej akcji (na przykład liczba dni, miesięcy lub lat), kiedy element ma wygasnąć.
      - Aby określić wygaśnięcie niestandardowej formuły przechowywania, wybierz pozycję Ustaw przez **niestandardową formułę przechowywania zainstalowaną na tym serwerze**.

        > [!NOTE]
        > Ta opcja jest dostępna tylko wtedy, gdy administrator s skonfigurowanie formuły niestandardowej.

   3. Opcja **Uruchom przepływ pracy** jest dostępna tylko wtedy, gdy definiujesz zasady dla listy, biblioteki lub typu zawartości, z które już jest skojarzony przepływ pracy. Następnie będziesz mieć do wyboru przepływy pracy.

   4. W sekcji **Cykl** wybierz pozycję Powtórz akcję tego etapu **...**, a następnie określ, jak często akcja ma się powtarzać.

      > [!NOTE]
      >  Ta opcja jest dostępna tylko wtedy, gdy wybraną akcję można powtarzać. Nie można na przykład ustawić cyklu akcji **Usuń trwale**.

   5. Wybierz pozycję **OK**.

8. Aby włączyć inspekcję dokumentów i elementów podlegających tym zasadom, wybierz pozycję Włącz **inspekcję, a** następnie określ zdarzenia, które mają zostać objęte inspekcją.

   Aby włączyć inspekcję:

   1. Na stronie Edytowanie zasad w obszarze **Inspekcja** wybierz pozycję Włącz inspekcję **, a** następnie zaznacz pola wyboru obok zdarzeń, dla których chcesz zachować dziennik inspekcji.

   2. Aby monitować użytkowników o wstawienie tych kodów kreskowych do dokumentów, wybierz pozycję Monituj użytkowników o wstawienie kodu kreskowego **przed zapisaniem lub wydrukowaniem**.

   3. Wybierz **przycisk OK** , aby zastosować funkcję inspekcji do zasad.

   Funkcja zasad inspekcji umożliwia organizacjom tworzenie i analizowanie śladów inspekcji dokumentów oraz tworzenie list elementów, takich jak listy zadań, listy problemów, grupy dyskusyjne i kalendarze. Ta funkcja zasad udostępnia dziennik inspekcji, który rejestruje zdarzenia, na przykład gdy zawartość jest przeglądana, edytowana lub usuwana.

   Gdy inspekcja jest włączona w ramach zasad zarządzania informacjami, administratorzy mogą wyświetlać dane inspekcji w raportach użycia zasad opartych na programie Microsoft Excel oraz podsumowywane bieżącego użycia. Administratorzy mogą używać tych raportów do określania sposobu używania informacji w organizacji. Raporty te mogą również pomóc organizacjom zweryfikować i udokumentować zgodność z przepisami lub zbadać potencjalne problemy.

   Dziennik inspekcji rejestruje następujące informacje: nazwę zdarzenia, datę i godzina zdarzenia oraz nazwę systemu użytkownika, który wykonał działanie.

9. Jeśli kody kreskowe są włączone w ramach zasad, są one dodawane do właściwości dokumentu i wyświetlane w obszarze nagłówka dokumentu, do którego zastosowano kod kreskowy. Kody kreskowe, na przykład etykiety, można również ręcznie usuwać z dokumentu. Możesz określić, czy użytkownicy będą monitować o dołączanie kodu kreskowego podczas drukowania lub zapisywania elementu, czy kod kreskowy powinien zostać wstawiony ręcznie  za pomocą karty Wstawianie w programach wersji Office 2010.

   Aby włączyć kody kreskowe:

   1. Na stronie **Edytowanie zasad** w obszarze **Kody kreskowe** wybierz pozycję **Włącz kody kreskowe**.

   2. Aby monitować użytkowników o wstawienie tych kodów kreskowych do dokumentów, wybierz pozycję Monituj użytkowników o wstawienie kodu kreskowego **przed zapisaniem lub wydrukowaniem**.

   3. Wybierz **przycisk OK** , aby zastosować do zasad funkcję kodu kreskowego.

   Zasady kodów kreskowych generują standardowe kody kreskowe Kod 39. Każdy obraz kodu kreskowego zawiera tekst poniżej symbolu kodu kreskowego reprezentującego wartość kodu kreskowego. Dzięki temu dane z kodu kreskowego będą używane nawet wtedy, gdy skanowanie sprzętu jest niedostępne. Użytkownicy mogą ręcznie wpisać numer kodu kreskowego w polu wyszukiwania, aby zlokalizować element w witrynie.  <br/> |

10. Aby określić, że dokumenty objęte zasadami mają etykiety, wybierz pozycję Włącz **etykiety, a** następnie określ ustawienia etykiet.

    Aby włączyć etykiety:

    1. Aby użytkownicy dodali etykiety do dokumentu, wybierz pozycję Monituj użytkowników o wstawienie **etykiety przed zapisaniem lub wydrukowaniem**.

       > [!NOTE]
       > Jeśli chcesz, aby etykiety były opcjonalne, nie zaznaczaj tego pola wyboru.

    2. Aby uniemożliwić zmianę etykiety po jej wstawieniu, wybierz pozycję Zapobiegaj zmianom **etykiet po ich dodaniu**.

       To ustawienie zapobiega aktualizowaniu tekstu etykiety po wstawieniu etykiety do elementu w aplikacji klienckiej, takiej jak Word, Excel lub PowerPoint. Jeśli chcesz, aby etykieta była aktualizowana po aktualizacji właściwości tego dokumentu lub elementu, nie zaznaczaj tego pola wyboru.

    3. W polu Format etykiety wprowadź tekst etykiety, która ma być wyświetlana. Etykiety mogą zawierać maksymalnie 10 odwołań do kolumn, z których każda może zawierać do 255 znaków. Aby utworzyć format etykiety, wykonaj następujące czynności:
       - Wpisz nazwy kolumn, które chcesz uwzględnić na etykiecie, w kolejności, w jakiej mają się pojawić. Nazwy kolumn należy ująć w nawiasy klamrowe ({}), jak pokazano w przykładzie na stronie Edytowanie zasad.
       - Wpisz wyrazy, aby zidentyfikować kolumny poza nawiasami kwadratowymi, jak pokazano w przykładzie na stronie Edytowanie zasad.

    4. Aby dodać podział wiersza, wprowadź **\n** miejscu, w którym ma się pojawić podział wiersza.

    5. Wybierz odpowiedni rozmiar i styl czcionki i określ, czy etykieta ma być pozycjonowana w lewo, wyśrodkowana, czy bezpośrednio w dokumencie.

       Wybierz czcionkę i styl, które są dostępne na komputerach użytkowników. Rozmiar czcionki wpływa na to, ile tekstu można wyświetlić na etykiecie.

    6. Wprowadź wysokość i szerokość etykiety. Wysokość etykiety może mieć od 0,25 cala do 20 cali, a szerokość etykiety może mieć od 0,25 cala do 20 cali. Tekst etykiety jest zawsze wyśrodkowany w pionie w obrębie obrazu etykiety.

    7. Wybierz **pozycję Odśwież** , aby wyświetlić podgląd zawartości etykiety.

11. Wybierz pozycję **OK**.

## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Tworzenie zasad dla listy, biblioteki lub folderu (zasady przechowywania oparte na lokalizacji)
<a name="__create_a_policy"> </a>

Zasady przechowywania można zdefiniować tylko dla określonej listy, biblioteki lub folderu. Jeśli jednak utworzysz zasady przechowywania w ten sposób, nie będzie można ponownie używać tych zasad na innych listach, bibliotekach, folderach lub witrynach. Zasad zbioru witryn nie można stosować do zasad opartych na lokalizacji.

Jeśli chcesz zastosować jedną zasady przechowywania do wszystkich typów zawartości w jednej lokalizacji, najprawdopodobniej będziesz używać przechowywania opartego na lokalizacji. W większości innych przypadków warto sprawdzić, czy dla wszystkich typów zawartości zostały określone zasady przechowywania.

Każdy podfolder dziedziczy zasady przechowywania elementu nadrzędnego, chyba że zdecydujesz się przerwać dziedziczenie i zdefiniować nowe zasady przechowywania na poziomie elementu podrzędnego.

Jeśli chcesz zdefiniować zasady zarządzania informacjami inne niż przechowywanie na liście lub w bibliotece, musisz zdefiniować zasady zarządzania informacjami dla każdego indywidualnego typu zawartości listy skojarzonego z tą listą lub biblioteką.

Jeśli w dowolnym momencie zdecydujesz się przełączyć się z typu zawartości na zasady oparte na lokalizacji dla listy lub biblioteki, jako zasady oparte na lokalizacji będą używane tylko zasady przechowywania. Wszystkie inne zasady zarządzania (inspekcje, kody kreskowe i kody kreskowe) zostaną odziedziczone po skojarzonych typach zawartości.

Zasady oparte na lokalizacji można wyłączyć w zbiorze witryn przez dezaktywowanie funkcji Przechowywanie na podstawie biblioteki i folderu. Dzięki temu administratorzy zbioru witryn mogą mieć pewność, że ich zasady typów zawartości nie zostaną zastąpione przez zasady oparte na lokalizacji administratora listy.

Do zmiany ustawień zasad zarządzania informacjami dla listy lub biblioteki jest potrzebne co najmniej uprawnienie Zarządzanie listami.

1. Przejdź do listy lub biblioteki, dla której chcesz określić zasady zarządzania informacjami.

2. Na wstążce wybierz **kartę** Biblioteka lub **Lista** \> na karcie **Biblioteka Ustawienia** **lub Lista Ustawienia**.

   W SharePoint w trybie online kliknij pozycję **Ustawienia** a następnie kliknij **pozycję Ustawienia listy** lub **Ustawienia biblioteki**.

3. W **obszarze Ustawienia zasad zarządzania informacjami**\> **o uprawnieniach i zarządzaniu**.

   ![Link do zasad zarządzania informacjami na stronie ustawień biblioteki dokumentów.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Na stronie Ustawienia zasad zarządzania informacjami upewnij się, że źródło przechowywania listy lub biblioteki ma ustawioną wartość Biblioteka i foldery.

   Jeśli **typ zawartości jest** wyświetlany jako źródło, kliknij pozycję **Zmień** źródło, a następnie kliknij pozycję **Biblioteka i foldery**. Zostanie ostrzegany, że zasady przechowywania typów zawartości zostaną zignorowane. Wybierz pozycję **OK**.

5. Na stronie Edytowanie zasad w obszarze **Harmonogram** przechowywania oparty na bibliotece wprowadź krótki opis tworzyć zasady.

6. Wybierz **pozycję Dodaj etap przechowywania...**

   Pamiętaj, że w obszarze Rekordy możesz zdefiniować różne zasady przechowywania dla rekordów, wybierając opcję Definiuj różne etapy przechowywania rekordów.

7. W oknie dialogowym Właściwości etapu wybierz opcję okresu przechowywania, aby określić, kiedy dokumenty lub elementy mają wygasać. Wykonaj jeden z następujących kroków:

   - Aby ustawić datę wygaśnięcia na podstawie właściwości daty,  \> w obszarze Zdarzenie Ten etap jest oparty na właściwości daty elementu, **a** następnie wybierz akcję dokumentu lub elementu (na przykład Utworzono lub Zmodyfikowano) oraz przyrost czasu po tej akcji (na przykład liczba dni, miesięcy lub lat), kiedy element ma wygasnąć.

   - Aby określić wygaśnięcie niestandardowej formuły przechowywania, wybierz pozycję Ustaw przez **niestandardową formułę przechowywania zainstalowaną na tym serwerze**.

     > [!NOTE]
     >  Ta opcja jest dostępna tylko wtedy, gdy administrator s skonfigurowanie formuły niestandardowej.

   - W **obszarze** Akcja określ, co ma się stać, gdy dokument lub element wygaśnie. Aby włączyć określoną akcję dla dokumentu lub elementu (na przykład usunięcie), wybierz akcję z listy.

8. Opcja **Uruchom przepływ pracy** jest dostępna tylko wtedy, gdy definiujesz zasady dla listy, biblioteki lub typu zawartości, z które już jest skojarzony przepływ pracy. Następnie będziesz mieć do wyboru przepływy pracy.

9. W **obszarze** Cykl wybierz **pozycję Powtórz akcję tego etapu...** i wprowadź, jak często akcja ma się powtarzać.

   > [!NOTE]
   >  Ta opcja jest dostępna tylko wtedy, gdy wybraną akcję można powtarzać. Nie można na przykład ustawić cyklu akcji **Usuń trwale**.

10. Wybierz pozycję **OK**.

## <a name="apply-a-site-collection-policy-to-a-content-type"></a>Stosowanie zasad zbioru witryn do typu zawartości
<a name="__apply_a_site"> </a>

Jeśli zasady zarządzania informacjami zostały już utworzone dla witryny jako zasady zbioru witryn, możesz zastosować jedną z tych zasad do typu zawartości. Dzięki temu można zastosować te same zasady do wielu typów zawartości w zbiorze witryn, które nie mają tego samego nadrzędnego typu zawartości.

 Jeśli chcesz zastosować zasady do wielu typów zawartości w zbiorze witryn i masz Usługa przesyłania metadanych zarządzane, możesz opublikować zasady zarządzania informacjami w wielu zbiorach witryn za pomocą publikowania typów zawartości. Aby uzyskać więcej [informacji, zobacz sekcję Stosowanie zasad we wszystkich](#apply-a-policy-across-site-collections) zbiorach witryn.

1. Przejdź do listy lub biblioteki zawierającej typ zawartości, do którego chcesz zastosować zasady.

2. Na wstążce wybierz **kartę** Biblioteka lub **Lista** \> na karcie **Biblioteka Ustawienia** **lub Lista Ustawienia**.

   W SharePoint w trybie online kliknij pozycję **Ustawienia** a następnie kliknij **pozycję Ustawienia listy** lub **Ustawienia biblioteki**.

3. W **obszarze Ustawienia zasad zarządzania informacjami** \> **o uprawnieniach i zarządzaniu**.

   ![Link do zasad zarządzania informacjami na stronie ustawień biblioteki dokumentów.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Sprawdź, czy źródło zasad jest ustawione na **Typy** zawartości, a  następnie w obszarze Zasady typu zawartości wybierz typ zawartości, do którego chcesz zastosować zasady.

5. W **obszarze Określ zasady** \> **Użyj zasad zbioru** witryn wybierz z listy zasady, które chcesz zastosować.

   > [!NOTE]
   >  Jeśli opcja **Użyj zasad zbioru witryn** jest dostępna, dla tego zbioru witryn nie zdefiniowano żadnych zasad zbioru witryn.

6. Wybierz pozycję **OK**.

   Jeśli lista lub biblioteka, z którą pracujesz, obsługuje zarządzanie wieloma typami zawartości, w  obszarze Typy zawartości możesz wybrać typ zawartości, dla którego chcesz określić zasady zarządzania informacjami. Spowoduje to bezpośredni dostęp do kroku 5 powyżej.

## <a name="apply-a-policy-across-site-collections"></a>Stosowanie zasad w zbiorach witryn
<a name="__toc260646789"> </a>

Udostępniaj typy zawartości w zbiorach witryn za pomocą aplikacji usługi zarządzanych metadanych w celu skonfigurowania publikowania typów zawartości. Publikowanie typów zawartości ułatwia spójne zarządzanie zawartością i metadanymi w witrynach, ponieważ typy zawartości można tworzyć i aktualizować w sposób centralny, a aktualizacje można publikować w wielu subskrybowaniach zbiorów witryn lub aplikacji sieci Web.

## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Tworzenie szablonu na podstawie istniejących zasad do używania w różnych zbiorach witryn
<a name="__toc262125409"> </a>

Możesz zdefiniować zasady zarządzania informacjami, a następnie utworzyć na ich podstawie szablon, który będzie potrzebny dla wielu zbiorów witryn zgodnie z potrzebami. Tej metody można użyć, jeśli chcesz utworzyć kopię zapasową zasad dotyczących informacji, lub użyć jej jako alternatywnej metody publikowania typów zawartości w celu zastosowania jednej zasady we wszystkich zbiorach witryn. Utwórz szablon lub kopię zapasową zasad, eksportując zasady z jednego zbioru witryn, a następnie importując je do zapisanej lokalizacji lub do innego zbioru witryn.

> [!IMPORTANT]
> Jeśli używasz funkcji eksportowania/importowania jako sposobu tworzenia zestawu szablonów zasad, pamiętaj, że identyfikator unikatowy istnieje w pliku .xml zasad. Z tego powodu nie można zaimportować tych zasad do witryny więcej niż raz bez zmiany tych identyfikator unikatowy.

### <a name="export-a-policy"></a>Eksportowanie zasad
<a name="__toc260646790"> </a>

1. Na stronie głównej zbioru witryn wybierz pozycję **Ustawienia**![ Wszystkie Ustawienia, które zajęło miejsce witryny Ustawienia.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Witryna Ustawienia**.

   W witrynie SharePoint połączonej z grupą kliknij pozycję Zawartość **Ustawienia****, a następnie** kliknij pozycję **Zawartość witryny Ustawienia**.

2. Na stronie Ustawienia w obszarze Szablony zasad typu zawartości **Administracja** \> zbiorem **witryn**.

   ![Link Szablon zasad typu zawartości na Ustawienia witryny.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Wybierz zasady, które chcesz wyeksportować, \> przewiń do dolnego przycisku **Eksportuj**\>.

4. Po wyświetleniu monitu o zapisanie lub otwarcie pliku **wybierz pozycję Zapisz**, a następnie wybierz lokalizację zapisu pliku. Pamiętaj, aby wybrać lokalizację dostępną dla zbiorów witryn, które importują zasady.

5. Gdy zostanie wyświetlone okno dialogowe Pobieranie ukończone, wybierz pozycję **Zamknij**.

### <a name="import-a-policy-to-a-different-site-collection"></a>Importowanie zasad do innego zbioru witryn
<a name="__toc260646791"> </a>

Zaimportowanie zasad zarządzania informacjami umożliwia zastosowanie ich do wielu typów zawartości na poziomie witryny lub listy w obrębie dowolnego zbioru witryn. Korzyści wynikające z tego są dwa rodzaje zasad: nie trzeba ponownie definiować i stosować zasad do poszczególnych typów zawartości, a ponadto można łatwiej zarządzać modyfikacjami zasad, dokonując zmian w zasadach w jednym miejscu.

1. Na stronie głównej zbioru witryn, do którego chcesz zastosować zasady, wybierz pozycję **Ustawienia**![ Wszystkie koła zębate Ustawienia, które zajęły miejsce witryny Ustawienia.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Witryna Ustawienia**.

   W witrynie SharePoint połączonej z grupą kliknij pozycję Zawartość **Ustawienia****, a następnie** kliknij pozycję **Zawartość witryny Ustawienia**.

2. Na stronie Ustawienia w obszarze Szablony zasad typu zawartości **Administracja** \> zbiorem **witryn**.

3. Na stronie Zasady **Importuj** \> \> **przeglądaj** w celu znalezienia pliku XML dla zasad.

4. Wybierz plik XML, w którym zasady **zostały zapisane Otwórz**\>.

5. Na stronie Importowanie zasad zbioru witryn **Zaimportuj**\>, aby dodać zasady do zbioru witryn.

Zaimportowane zasady można teraz stosować do jednego lub wielu typów zawartości na poziomie witryny lub listy.

Zasady zarządzania informacjami umożliwiają organizacji kontrolowanie, jak długo zawartość jest zachowywana, inspekcja działań użytkowników z zawartością oraz dodawanie kodów kreskowych lub etykiet do dokumentów. Zasady mogą ułatwić egzekwowanie zgodności z przepisami prawnymi i rządowymi lub wewnętrznymi procesami biznesowymi. Jako administrator możesz skonfigurować zasady sterujące tym, jak śledzić dokumenty i jak długo mają być zachowywane dokumenty.

Zasady zarządzania informacjami można tworzyć w trzech różnych miejscach hierarchii witryn, od najszerszej do najwęższych:

- Tworzenie zasad w celu używania wielu typów zawartości w zbiorze witryn.
- Tworzenie zasad dla typu zawartości witryny.
- Tworzenie zasad dla listy lub biblioteki.

Aby uzyskać więcej informacji, [zobacz Wprowadzenie do zasad zarządzania informacjami](intro-to-info-mgmt-policies.md).
