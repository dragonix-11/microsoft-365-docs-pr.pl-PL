---
title: Stosowanie usługi Zarządzanie prawami do informacji (IRM) do listy lub biblioteki
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 7/2/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1
ms.collection:
- M365-security-compliance
- SPO_Content
description: Za pomocą usługi Zarządzanie prawami do informacji (IRM) można kontrolować i chronić pliki pobierane z list lub bibliotek.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4dfa7360dd178e5943402fcb834236d7d0bf9a08
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988036"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Stosowanie usługi Zarządzanie prawami do informacji (IRM) do listy lub biblioteki

Za pomocą usługi Zarządzanie prawami do informacji (IRM) można kontrolować i chronić pliki pobierane z list lub bibliotek. Ta funkcja jest obsługiwana tylko w globalnej chmurze firmy Microsoft. Usługa IRM nie jest obsługiwana SharePoint listach i bibliotekach w chmurach narodowych.
  
## <a name="administrator-preparations-before-applying-irm"></a>Przygotowanie administratora przed zastosowaniem usługi IRM

- Usługa Azure Rights Management (Azure RMS) z usługi Azure Information Protection i Usługi Active Directory Rights Management jej lokalne odpowiedniki (AD RMS) obsługują usługę Zarządzanie prawami do informacji w witrynach. Nie są wymagane osobne ani dodatkowe instalacje.

- Przed zastosowaniem usługi IRM do listy lub biblioteki należy włączyć funkcję IRM dla witryny. Do włączenia usługi IRM są potrzebne uprawnienia administratora.

- Aby zastosować usługę IRM do listy lub biblioteki, musisz mieć uprawnienia administratora dla tej listy lub biblioteki.

- Jeśli korzystasz z usługi SharePoint Online, podczas pobierania większych plików chronionych za pomocą usługi IRM użytkownicy mogą mieć limity czasu. Aby uniknąć limitów czasu, zastosuj Office IRM w programach pakietu Office i przechowuj większe pliki w bibliotece usługi SharePoint, w SharePoint która nie korzysta z usługi IRM.

> [!NOTE]
> Jeśli korzystasz z programu SharePoint Server 2013, administrator serwera musi zainstalować pliki na wszystkich frontonych serwerach sieci Web dla każdego typu plików, który mają być chronić osoby w organizacji za pomocą usługi IRM.
  
## <a name="apply-irm-to-a-list-or-library"></a>Stosowanie usługi IRM do listy lub biblioteki
<a name="__toc256598179"> </a>

![Zarządzanie prawami do informacji Ustawienia.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Przejdź do listy lub biblioteki, dla której chcesz skonfigurować usługę IRM.

2. Na wstążce wybierz kartę **Biblioteka**, a następnie wybierz pozycję Biblioteka **Ustawienia**. (Jeśli pracujesz z listą, wybierz **kartę** Lista, a następnie wybierz pozycję **Lista Ustawienia**).
    
    ![SharePoint biblioteki Ustawienia na Wstążce.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. W **obszarze Uprawnienia i zarządzanie** wybierz pozycję **Zarządzanie prawami do informacji**. Jeśli link Zarządzanie prawami do informacji nie jest widoczny, może to oznaczać, że w witrynie nie włączono usługi IRM. Skontaktuj się z administratorem serwera, aby sprawdzić, czy możesz włączyć funkcję IRM dla swojej witryny. Link **Zarządzanie prawami do informacji** nie jest wyświetlany w przypadku bibliotek obrazów.

4. Na stronie **Ustawienia** zarządzanie prawami do informacji zaznacz pole wyboru Ogranicz uprawnienia do  dokumentów w tej bibliotece podczas pobierania, aby zastosować ograniczone uprawnienia do dokumentów pobieranych z tej listy lub biblioteki przez użytkowników.

5. W **polu Utwórz tytuł zasad uprawnień** wprowadź opisową nazwę zasad. Użyj nazwy, która ułatwia identyfikowanie tych zasad na pomocą innych zasad. Możesz na przykład użyć funkcji **Poufne informacje firmowe** , aby zastosować ograniczone uprawnienia do listy lub biblioteki zawierającej poufne dokumenty firmowe.

6. W **polu Dodaj opis zasad** uprawnień wpisz opis, który będzie wyświetlany osobom, które używają tej listy lub biblioteki, wyjaśniacy sposób obsługi dokumentów na tej liście lub w tej bibliotece. Możesz na przykład wpisać **Omówić** zawartość tego dokumentu tylko z innymi pracownikami, jeśli chcesz ograniczyć dostęp do informacji w tych dokumentach pracownikom wewnętrznym. 

7. Aby zastosować dodatkowe ograniczenia do dokumentów na tej liście lub w tej bibliotece, wybierz pozycję **Pokaż opcje** i wykonaj dowolną z następujących czynności:

|**W tym celu:**|**W tym celu:**|
|:-----|:-----|
|Zezwalanie innym osobom na drukowanie dokumentów z tej listy lub biblioteki|Zaznacz pole **wyboru Zezwalaj użytkownikom na drukowanie** .|
|Zezwalaj osobom z co najmniej uprawnieniem Wyświetlanie elementów na uruchamianie w dokumencie kodu lub makr osadzonych.|Zaznacz pole **wyboru Zezwalaj użytkownikom na uruchamianie skryptu** i czytnika zawartości ekranu w pobranych dokumentach. Jeśli wybierzesz tę opcję, użytkownicy będą mogli uruchamiać kod w celu wyodrębnienia zawartości dokumentu.           |
|Zaznacz tę opcję, jeśli chcesz ograniczyć dostęp do zawartości do określonego czasu. Jeśli wybierzesz tę opcję, licencje osób na wydawanie licencji na dostęp do zawartości wygasną po upływie określonej liczby dni i będzie wymagane powrót na serwer w celu zweryfikowania swoich poświadczeń i pobrania nowej kopii.|Zaznacz pole wyboru Po pobraniu prawa dostępu do dokumentu wygasną po upływie następującej liczby dni **(1–365** ), a następnie określ liczbę dni, przez które chcesz wyświetlać dokument.|
| Uniemożliwianie osobom przekazywania do tej listy lub biblioteki dokumentów, które nie obsługują usługi IRM. Jeśli wybierzesz tę opcję, inne osoby nie będą mogły przekazywać plików następujących typów: Typy plików, które nie mają odpowiednich plików usługi IRM, są zainstalowane na wszystkich frontoowych serwerach sieci Web. Typy plików, które SharePoint Server 2010 nie mogą odszyfrowywać. Typy plików, które są chronione za pomocą usługi IRM w innym programie.|Zaznacz pole **wyboru Nie zezwalaj użytkownikom na przekazywanie dokumentów, które nie obsługują usługi IRM** .|
|Usuń ograniczone uprawnienia z tej listy lub biblioteki w określonym dniu.|Zaznacz pole **wyboru Zatrzymaj ograniczanie dostępu do biblioteki** w, a następnie wybierz datę.|
|Steruj interwałem buforowania poświadczeń dla programu licencjonowanego do otwierania dokumentu.|Zaznacz pole **wyboru Użytkownicy muszą zweryfikować** swoje poświadczenia za pomocą tego interwału (dni), a następnie wprowadzić interwał poświadczeń buforowania w liczbie dni.|
|Zezwalaj na ochronę grupy, aby użytkownicy mogą udostępniać dane członkom tej samej grupy.|Wybierz **pozycję Zezwalaj na ochronę** grupy i wprowadź nazwę grupy do udostępniania.|

8. Po zakończeniu wybierania odpowiednich opcji wybierz przycisk **OK**.
  
## <a name="what-is-information-rights-management"></a>Co to jest zarządzanie prawami do informacji?
<a name="__toc256598175"> </a>

Zarządzanie prawami do informacji (IRM, Information Rights Management) pozwala ograniczyć czynności, jakie użytkownicy mogą podjąć na plikach pobranych z list lub bibliotek. Za pomocą usługi IRM pliki pobrane są szyfrowane i ograniczane zestawy użytkowników i programów, które mogą odszyfrowywać te pliki. Ponadto usługi IRM mogą ograniczać prawa użytkowników, którym wolno odczytywać pliki, tak aby nie mogli takich czynności jak drukowanie kopii plików lub kopiowanie z nich tekstu.
  
Usługi IRM można używać na listach i w bibliotekach, aby ograniczyć rozpowszechnianie poufnej zawartości. Jeśli na przykład tworzysz bibliotekę dokumentów w celu udostępniania informacji o nadchodzących produktach wybranym przedstawicielom marketingowym, możesz użyć usługi IRM, aby uniemożliwić tym osobom udostępnianie tej zawartości innym pracownikom w firmie.
  
W witrynie można zastosować usługę IRM do całej listy lub biblioteki, a nie do poszczególnych plików. Ułatwia to zapewnienie spójnego poziomu ochrony dla całego zestawu dokumentów lub plików. Dzięki temu usługi IRM mogą ułatwić organizacji egzekwowanie zasad firmowych dotyczących rozpowszechniania i używania informacji poufnych i zastrzeżonych.
  
> [!NOTE]
> Informacje na tej stronie dotyczące usługi Zarządzanie prawami do informacji (Information Rights Management) nie zawierają żadnych postanowień odwołująjących się do "Zarządzania prawami do informacji" w żadnych umowach licencyjnych na postanowienia licencyjne dotyczące programu Microsoft SharePoint Server 2013 i SharePoint Server 2016. 
  
### <a name="how-irm-can-help-protect-content"></a>Jak za pomocą usługi IRM można chronić zawartość
<a name="__toc256598176"> </a>

Ochrona zawartości z ograniczeniami za przez usługi IRM jest pomocna w następujących sposobach:
  
- Pomaga zapobiec kopiowaniu, modyfikowaniu, drukowaniu, faksowania, kopiowaniu i wklejania zawartości przez upoważnioną przeglądarkę w celu nieautoryzowanego użycia.
    
- Pomaga zapobiec kopiowaniu zawartości przez autoryzowaną przeglądarkę przy użyciu funkcji Print Screen w aplikacji Microsoft Windows
    
- Pomaga zapobiec wyświetlaniu zawartości przez nieautoryzowaną przeglądarkę, jeśli zostanie ona wysłana w wiadomości e-mail po pobraniu jej z serwera.
    
- Ograniczanie dostępu do zawartości do określonego okresu, po upływie którego użytkownicy muszą potwierdzić swoje poświadczenia i ponownie pobrać zawartość.
    
- Ułatwia egzekwowanie zasad firmowych dotyczących rozpowszechniania i używania zawartości w organizacji
    
### <a name="how-irm-cannot-help-protect-content"></a>Jak ochrona zawartości za pomocą usługi IRM
<a name="__toc256598177"> </a>

Usługi IRM nie mogą chronić zawartości objętej ograniczeniami przez:
  
- Wymazywania, kradzieży, przechwytywania lub transmisji za pomocą złośliwych programów, takich jak konie trojańskie, rejestratory naciśnięć klawiszy i programy szpiegujące określonego typu
    
- Utrata lub uszkodzenie spowodowane działaniem wirusów komputerowych
    
- Ręczne kopiowanie lub ponowne wpisywanie zawartości z ekranu
    
- Cyfrowe lub filmowe fotografie zawartości wyświetlanej na ekranie
    
- Kopiowanie za pomocą programów do przechwytywania zawartości ekranu innych firm
    
- Kopiowanie metadanych zawartości (wartości kolumn) przy użyciu programów do przechwytywania zawartości ekranu innych firm lub akcji kopiowania i wklejania
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Jak działa usługi IRM dla list i bibliotek
<a name="__toc256598178"> </a>

Ochrona usługi IRM jest stosowana do plików na poziomie listy lub biblioteki. Jeśli funkcja IRM jest włączona dla biblioteki, zarządzanie prawami dostępu dotyczy wszystkich plików w tej bibliotece. Jeśli funkcja IRM jest włączona dla listy, zarządzanie prawami dostępu dotyczy tylko plików, które są dołączone do elementów listy, a nie rzeczywistych elementów listy.
  
Gdy osoby pobierają pliki z listy lub biblioteki z obsługą usługi IRM, pliki są szyfrowane, dzięki czemu mogą je wyświetlać tylko uprawnione osoby. Każdy plik zarządzania prawami dostępu zawiera również licencję wydawania, która nakłada ograniczenia na osoby, które przeglądają plik. Typowe ograniczenia obejmują tworzenie pliku tylko do odczytu, wyłączanie kopiowania tekstu, uniemożliwianie zapisywania kopii lokalnej i uniemożliwianie drukowania pliku. Programy klienckie, które mogą odczytywać typy plików obsługiwane przez usługę IRM, używają licencji wydawania w ramach pliku zarządzanego prawami do wymuszenia tych ograniczeń. W ten sposób plik zarządzany prawami dostępu zachowuje swoją ochronę nawet po pobraniu go z serwera.
  
Typy ograniczeń stosowane do pliku pobieranego z listy lub biblioteki są oparte na uprawnieniach poszczególnych użytkowników w witrynie zawierającej ten plik. W poniższej tabeli wyjaśniono, jak uprawnienia witryn odpowiadają uprawnieniam usługi IRM.
  
|**Uprawnienia**|**Uprawnienia usługi IRM**|
|:-----|:-----|
|Zarządzanie uprawnieniami, zarządzanie witryną sieci Web|**Pełna kontrola** (zgodnie z definicją w programie klienckim): To uprawnienie na ogół pozwala użytkownikowi odczytywać, edytować, kopiować, zapisywać i modyfikować uprawnienia zawartości zarządzanej prawami.|
|Edytowanie elementów, zarządzanie listami, dodawanie i dostosowywanie stron|**Edytowanie**, **kopiowanie** i zapisywanie **Ustawienia: Użytkownik** może wydrukować plik tylko wtedy, gdy  na stronie Zarządzanie prawami do informacji dla listy lub biblioteki jest zaznaczone pole wyboru Zezwalaj użytkownikom na drukowanie dokumentów.|
|Wyświetlanie elementów|**Odczyt**: Użytkownik może odczytać dokument, ale nie może kopiować ani modyfikować jego zawartości. Użytkownik może drukować tylko wtedy,  gdy pole wyboru Zezwalaj użytkownikom na drukowanie dokumentów jest zaznaczone na stronie Zarządzanie prawami do informacji Ustawienia dla listy lub biblioteki.|
|Inne|Żadne inne uprawnienia nie są bezpośrednio związane z uprawnieniami usługi IRM.|
   
Po włączeniu usługi IRM dla listy lub biblioteki w programie SharePoint Server 2013 można chronić tylko typy plików na tej liście lub w bibliotece, dla których zainstalowano dane na wszystkich frontonych serwerach sieci Web. A is a program that controls the encryption and decryption of rights-managed files of a specific file format. SharePoint zawiera pliki dla następujących typów plików:
  
- Microsoft Office formularzy programu InfoPath
    
- Formaty plików 97–2003 dla następujących Microsoft Office programów: Word, Excel i PowerPoint
    
- Formaty Office Open XML dla następujących Microsoft Office programów: Word, Excel i PowerPoint
    
- Format XPS (XML Paper Specification)
    
Jeśli Twoja organizacja planuje korzystanie z usługi IRM w celu ochrony innych typów plików oprócz wymienionych powyżej, administrator serwera musi zainstalować pliki w celu użycia tych dodatkowych formatów plików.
  

