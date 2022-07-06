---
title: Stosowanie usługi IRM do listy lub biblioteki
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
description: Zarządzanie prawami do informacji (IRM) ułatwia kontrolowanie i ochronę plików pobieranych z list lub bibliotek.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf677fc81a20b7e86d9b66505dd8968c0a31272b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633130"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Stosowanie usługi Information Rights Management (IRM) do listy lub biblioteki

Zarządzanie prawami do informacji (IRM) ułatwia kontrolowanie i ochronę plików pobieranych z list lub bibliotek. Ta funkcja jest obsługiwana tylko w chmurze globalnej firmy Microsoft. Usługa IRM nie jest obsługiwana w przypadku list i bibliotek programu SharePoint we wdrożeniach chmury krajowej.
  
## <a name="administrator-preparations-before-applying-irm"></a>Przygotowania administratora przed zastosowaniem usługi IRM

- Usługa Azure Rights Management (Azure RMS) z usługi Azure Information Protection i odpowiednik lokalnej usługi Active Directory Rights Management Services (AD RMS) obsługują zarządzanie prawami do informacji dla witryn. Nie są wymagane żadne oddzielne ani dodatkowe instalacje.

- Przed zastosowaniem usługi IRM do listy lub biblioteki należy włączyć usługę IRM dla swojej witryny. Aby włączyć usługę IRM, potrzebne będą uprawnienia administratora.

- Aby zastosować usługę IRM do listy lub biblioteki, musisz mieć uprawnienia administratora do tej listy lub biblioteki.

- Jeśli używasz usługi SharePoint Online, użytkownicy mogą mieć przekroczenia limitu czasu podczas pobierania większych plików chronionych przez usługę IRM. Aby uniknąć przekroczenia limitu czasu, użyj programów pakietu Office, aby zastosować ochronę usługi IRM i przechowywać większe pliki w bibliotece programu SharePoint, która nie korzysta z usługi IRM.

> [!NOTE]
> Jeśli używasz programu SharePoint Server 2013, administrator serwera musi zainstalować funkcje ochrony na wszystkich serwerach sieci Web frontonu dla każdego typu pliku, który osoby w organizacji chcą chronić przy użyciu usługi IRM.
  
## <a name="apply-irm-to-a-list-or-library"></a>Stosowanie usługi IRM do listy lub biblioteki
<a name="__toc256598179"> </a>

![Ustawienia zarządzania prawami do informacji.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Przejdź do listy lub biblioteki, dla której chcesz skonfigurować usługę IRM.

2. Na wstążce wybierz kartę **Biblioteka** , a następnie wybierz pozycję **Ustawienia biblioteki**. (Jeśli pracujesz na liście, wybierz kartę **Lista** , a następnie wybierz pozycję **Ustawienia listy**).
    
    ![Przyciski Ustawienia biblioteki programu SharePoint na wstążce.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. W obszarze **Uprawnienia i zarządzanie** wybierz pozycję **Zarządzanie prawami do informacji**. Jeśli link zarządzanie prawami do informacji nie jest wyświetlany, usługa IRM może nie być włączona dla twojej witryny. Skontaktuj się z administratorem serwera, aby sprawdzić, czy można włączyć usługę IRM dla swojej witryny. Link **do usługi Information Rights Management** nie jest wyświetlany dla bibliotek obrazów.

4. Na stronie **Ustawienia zarządzania prawami do informacji** zaznacz pole wyboru **Ogranicz uprawnienia do dokumentów w tej bibliotece podczas pobierania** , aby zastosować ograniczone uprawnienia do dokumentów pobieranych przez użytkowników z tej listy lub biblioteki.

5. W polu **Tworzenie tytułu zasad uprawnień** wprowadź opisową nazwę zasad. Użyj nazwy, która pomaga zidentyfikować te zasady na podstawie innych zasad. Na przykład użyj pozycji **Poufne firmy** , aby zastosować ograniczone uprawnienia do listy lub biblioteki zawierającej poufne dokumenty firmowe.

6. W polu **Dodawanie opisu zasad uprawnień** wpisz opis, który będzie widoczny dla osób korzystających z tej listy lub biblioteki, który wyjaśnia, jak powinny obsługiwać dokumenty na tej liście lub w bibliotece. Na przykład możesz wpisać **Artykułuj zawartość tego dokumentu tylko z innymi pracownikami** , jeśli chcesz ograniczyć dostęp do informacji zawartych w tych dokumentach do pracowników wewnętrznych. 

7. Aby zastosować dodatkowe ograniczenia do dokumentów na tej liście lub w bibliotece, wybierz pozycję **Pokaż opcje** i wykonaj dowolne z następujących czynności:

|**W tym celu:**|**Wykonaj następujące czynności:**|
|:-----|:-----|
|Zezwalaj użytkownikom na drukowanie dokumentów z tej listy lub biblioteki|Zaznacz pole wyboru **Zezwalaj widzom na drukowanie** .|
|Zezwalaj osobom z co najmniej uprawnieniem Wyświetl elementy na uruchamianie osadzonego kodu lub makr w dokumencie.|Zaznacz pole wyboru **Zezwalaj widzom na uruchamianie skryptu i czytnika zawartości ekranu, aby działało w pobranych dokumentach** . Jeśli wybierzesz tę opcję, użytkownicy mogą uruchomić kod, aby wyodrębnić zawartość dokumentu.           |
|Wybierz tę opcję, jeśli chcesz ograniczyć dostęp do zawartości do określonego okresu. Jeśli wybierzesz tę opcję, licencje wystawiane przez osoby w celu uzyskania dostępu do zawartości wygasną po określonej liczbie dni, a użytkownicy będą musieli wrócić na serwer, aby zweryfikować swoje poświadczenia i pobrać nową kopię.|Zaznacz pole wyboru **Po pobraniu prawa dostępu do dokumentu wygasną po tej liczbie dni (1–365),** a następnie określ liczbę dni, dla których dokument ma być wyświetlany.|
| Uniemożliwiaj użytkownikom przekazywanie dokumentów, które nie obsługują usługi IRM, do tej listy lub biblioteki. Jeśli wybierzesz tę opcję, użytkownicy nie będą mogli przekazać żadnego z następujących typów plików: typy plików, które nie mają zainstalowanych odpowiednich funkcji ochrony IRM na wszystkich serwerach sieci Web frontonu. Typy plików, których program SharePoint Server 2010 nie może odszyfrować. Typy plików, które są chronione przez usługę IRM w innym programie.|Zaznacz pole wyboru **Nie zezwalaj użytkownikom na przekazywanie dokumentów, które nie obsługują usługi IRM** .|
|Usuń ograniczone uprawnienia z tej listy lub biblioteki w określonym dniu.|Zaznacz pole wyboru **Zatrzymaj ograniczanie dostępu do biblioteki** , a następnie wybierz odpowiednią datę.|
|Kontroluj interwał buforowania poświadczeń dla programu, który ma licencję na otwieranie dokumentu.|Zaznacz pole wyboru **Użytkownicy muszą zweryfikować swoje poświadczenia przy użyciu tego interwału (dni),** a następnie wprowadź interwał buforowania poświadczeń w ciągu kilku dni.|
|Zezwalaj na ochronę grup, aby użytkownicy mogli udostępniać je członkom tej samej grupy.|Wybierz pozycję **Zezwalaj na ochronę grupy** i wprowadź nazwę grupy do udostępniania.|

8. Po wybraniu odpowiednich opcji wybierz przycisk **OK**.
  
## <a name="what-is-information-rights-management"></a>Co to jest zarządzanie prawami do informacji?
<a name="__toc256598175"> </a>

Zarządzanie prawami do informacji (IRM) umożliwia ograniczenie akcji, które użytkownicy mogą wykonywać w przypadku plików pobranych z list lub bibliotek. Usługa IRM szyfruje pobrane pliki i ogranicza zestaw użytkowników i programów, które mogą odszyfrować te pliki. Usługa IRM może również ograniczyć prawa użytkowników, którzy mogą odczytywać pliki, aby nie mogli wykonywać akcji, takich jak drukowanie kopii plików lub kopiowanie z nich tekstu.
  
Można użyć usługi IRM na listach lub bibliotekach, aby ograniczyć rozpowszechnianie poufnej zawartości. Jeśli na przykład tworzysz bibliotekę dokumentów w celu udostępniania informacji o nadchodzących produktach wybranym przedstawicielom marketingu, możesz użyć usługi IRM, aby uniemożliwić tym osobom udostępnianie tej zawartości innym pracownikom w firmie.
  
W witrynie stosuje się usługę IRM do całej listy lub biblioteki, a nie do poszczególnych plików. Ułatwia to zapewnienie spójnego poziomu ochrony całego zestawu dokumentów lub plików. Usługa IRM może zatem pomóc twojej organizacji w egzekwowaniu zasad firmowych regulujących stosowanie i rozpowszechnianie informacji poufnych lub zastrzeżonych.
  
> [!NOTE]
> Informacje na tej stronie dotyczące usługi Information Rights Management zasłaniają wszelkie postanowienia odwołujące się do "Zarządzanie prawami do informacji" w dowolnych umowach licencyjnych programu Microsoft SharePoint Server 2013 i SharePoint Server 2016. 
  
### <a name="how-irm-can-help-protect-content"></a>Jak usługa IRM może pomóc w ochronie zawartości
<a name="__toc256598176"> </a>

Usługa IRM pomaga chronić zawartość z ograniczeniami w następujący sposób:
  
- Zapobiega kopiowaniu, modyfikowaniu, drukowaniu, faksowaniu lub kopiowaniu i wklejaniu zawartości przez autoryzowanego widza w celu nieautoryzowanego użycia
    
- Zapobiega kopiowaniu zawartości przez autoryzowanego widza przy użyciu funkcji Print Screen w systemie Microsoft Windows
    
- Zapobiega wyświetlaniu zawartości przez nieautoryzowanego widza, jeśli jest ona wysyłana pocztą e-mail po pobraniu jej z serwera
    
- Ogranicza dostęp do zawartości do określonego okresu, po którym użytkownicy muszą potwierdzić swoje poświadczenia i ponownie pobrać zawartość
    
- Pomaga wymusić zasady firmowe, które regulują używanie i rozpowszechnianie zawartości w organizacji
    
### <a name="how-irm-cannot-help-protect-content"></a>Jak usługa IRM nie może pomóc w ochronie zawartości
<a name="__toc256598177"> </a>

Usługa IRM nie może chronić zawartości z ograniczeniami przed następującymi elementami:
  
- Usuwanie, kradzież, przechwytywanie lub transmisja przez złośliwe programy, takie jak konie trojańskie, rejestratory naciśnięcia klawiszy i niektóre typy programów szpiegujących
    
- Utrata lub uszkodzenie z powodu działań wirusów komputerowych
    
- Ręczne kopiowanie lub ponowne wpisywanie zawartości z ekranu na ekranie
    
- Fotografia cyfrowa lub filmowa zawartości wyświetlanej na ekranie
    
- Kopiowanie za pomocą programów przechwytywania ekranu innych firm
    
- Kopiowanie metadanych zawartości (wartości kolumn) za pomocą programów przechwytywania ekranu innych firm lub akcji kopiowania i wklejania
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Jak działa usługa IRM dla list i bibliotek
<a name="__toc256598178"> </a>

Ochrona za pomocą usługi IRM jest stosowana do plików na poziomie listy lub biblioteki. Gdy usługa IRM jest włączona dla biblioteki, zarządzanie prawami ma zastosowanie do wszystkich plików w tej bibliotece. Gdy usługa IRM jest włączona dla listy, zarządzanie prawami ma zastosowanie tylko do plików dołączonych do elementów listy, a nie do rzeczywistych elementów listy.
  
Gdy użytkownicy pobierają pliki z listy lub biblioteki z obsługą usługi IRM, pliki są szyfrowane, aby tylko autoryzowane osoby mogły je wyświetlać. Każdy plik zarządzany przez prawa zawiera również licencję wystawiania, która nakłada ograniczenia na osoby, które wyświetlają plik. Typowe ograniczenia obejmują tworzenie pliku tylko do odczytu, wyłączanie kopiowania tekstu, uniemożliwianie użytkownikom zapisywania lokalnej kopii i uniemożliwianie użytkownikom drukowania pliku. Programy klienckie, które mogą odczytywać typy plików obsługiwane przez usługę IRM, używają licencji wystawiania w pliku zarządzanym przez prawa, aby wymusić te ograniczenia. W ten sposób plik zarządzany prawami zachowuje ochronę nawet po pobraniu go z serwera.
  
Typy ograniczeń, które są stosowane do pliku po pobraniu z listy lub biblioteki, są oparte na uprawnieniach poszczególnych użytkowników w witrynie zawierającej plik. W poniższej tabeli wyjaśniono, w jaki sposób uprawnienia w lokacjach odpowiadają uprawnieniom IRM.
  
|**Uprawnienia**|**Uprawnienia usługi IRM**|
|:-----|:-----|
|Zarządzanie uprawnieniami, zarządzanie witryną sieci Web|**Pełna kontrola** (zgodnie z definicją programu klienckiego): to uprawnienie zwykle umożliwia użytkownikowi odczytywanie, edytowanie, kopiowanie, zapisywanie i modyfikowanie uprawnień do zawartości zarządzanej prawami.|
|Edytowanie elementów, zarządzanie listami, dodawanie i dostosowywanie stron|**Edytuj**, **kopiuj** i **zapisz**: użytkownik może wydrukować plik tylko wtedy, gdy pole wyboru **Zezwalaj użytkownikom na drukowanie dokumentów** jest zaznaczone na stronie Ustawienia zarządzania prawami do informacji dla listy lub biblioteki.|
|Wyświetl elementy|**Przeczytaj**: Użytkownik może odczytać dokument, ale nie może skopiować ani zmodyfikować jego zawartości. Użytkownik może drukować tylko wtedy, gdy pole wyboru **Zezwalaj użytkownikom na drukowanie dokumentów** jest zaznaczone na stronie Ustawienia zarządzania prawami do informacji dla listy lub biblioteki.|
|Inne|Żadne inne uprawnienia nie odpowiadają bezpośrednio uprawnieniom usługi IRM.|
   
Po włączeniu usługi IRM dla listy lub biblioteki w programie SharePoint Server 2013 można chronić tylko typy plików na tej liście lub w bibliotece, dla których ochrona jest zainstalowana na wszystkich serwerach sieci Web frontonu. Ochrona to program, który kontroluje szyfrowanie i odszyfrowywanie plików zarządzanych prawami w określonym formacie pliku. Program SharePoint zawiera funkcje ochrony dla następujących typów plików:
  
- Formularze programu Microsoft Office InfoPath
    
- Formaty plików 97-2003 dla następujących programów pakietu Microsoft Office: Word, Excel i PowerPoint
    
- Formaty Open XML pakietu Office dla następujących programów pakietu Microsoft Office: Word, Excel i PowerPoint
    
- Format specyfikacji papieru XML (XPS)
    
Jeśli organizacja planuje używać usługi IRM do ochrony innych typów plików oprócz tych wymienionych powyżej, administrator serwera musi zainstalować funkcje ochrony dla tych dodatkowych formatów plików.
  

