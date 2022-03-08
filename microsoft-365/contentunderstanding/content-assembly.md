---
title: Tworzenie dokumentów przy użyciu zestawu zawartości w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak automatycznie tworzyć dokumenty i inną zawartość przy użyciu zestawu zawartości w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: f2e8c601e8a7242524cb323d099975f6600cce05
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318889"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Tworzenie dokumentów przy użyciu zestawu zawartości w aplikacji Microsoft SharePoint Syntex

Przy użyciu tego SharePoint Syntex można automatycznie generować standardowe powtarzające się dokumenty biznesowe, takie jak umowy, oświadczenia o pracy, umowy serwisowe, listy zgody, informacje o sprzedaży i korespondencja. Korzystając z zestawu zawartości w programie SharePoint Syntex, możesz zrobić to wszystko szybciej, spójniej i mniej podatnie na błędy.

Dzięki zestawowi zawartości możesz użyć istniejącego dokumentu, aby utworzyć nowoczesny *szablon, a* następnie użyć tego szablonu do automatycznego generowania nowej zawartości przy użyciu list SharePoint lub danych wejściowych użytkownika jako źródła danych.

> [!NOTE]
> Aby uzyskać dostęp do funkcji zestawu SharePoint Syntex i korzystać z tych możliwości, musisz być licencjonowanym użytkownikiem. Ponadto musisz mieć uprawnienia do zarządzania listami SharePoint listami.

## <a name="create-a-modern-template"></a>Tworzenie nowoczesnego szablonu

Wykonaj poniższe czynności, aby utworzyć nowoczesny szablon.

1. W bibliotece dokumentów programu SharePoint wybierz pozycję **NowyTworzenie** >  **nowoczesnego szablonu**. 
 
   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z wyróżniona opcją Utwórz nowoczesny szablon.](../media/content-understanding/content-assembly-create-template-1.png)

2. Wybierz istniejący dokument programu Word, na podstawie którego chcesz utworzyć nowoczesny szablon, a następnie wybierz pozycję **Otwórz**. 
 
   ![Zrzut ekranu przedstawiający stronę przekazywania, na której wybierasz dokument.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > Obecnie do tworzenia szablonów można przekazywać tylko dokumenty programu Word (.docx rozszerzenia). Upload programu Word z lokalnego magazynu lub pulpitu.

3. Po przesłaniu dokumentu dokument zostanie wyświetlony w studio szablonów, w którym możesz przekonwertować dokument na szablon.
 
   ![Zrzut ekranu przedstawiający dokument w przeglądarce szablonów.](../media/content-understanding/content-assembly-create-template-3.png)

4. W lewym górnym rogu studio szablonów wybierz nazwę szablonu. Domyślna nazwa to nazwa dokumentu użytego do utworzenia szablonu. Jeśli chcesz zmienić nazwę szablonu, wybierz nazwę domyślną lub ikonę ołówka obok nazwy, wpisz nową nazwę, a następnie naciśnij klawisz **Enter**.
 
   ![Zrzut ekranu przedstawiający przeglądarkę szablonów z nazwą dokumentu do wybrania w celu zmiany nazwy.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Tworzenie symboli zastępczych dla całego tekstu dynamicznego w dokumencie, które użytkownicy mogą chcieć zmieniać z jednego dokumentu na inny. Można na przykład utworzyć symbol zastępczy dla danych wejściowych, takich jak nazwa firmy, nazwa klienta, adres, numer telefonu lub data.

    Aby utworzyć symbol zastępczy, zaznacz tekst (na przykład datę). Zostanie **otwarty panel Wszystkie** symbole zastępcze, w którym nadasz symbolowi zastępczeowi odpowiednią nazwę i wybierzesz typ danych wejściowych, które chcesz skojarzyć z symbolem zastępczym.
 
   ![Zrzut ekranu przedstawiający przeglądarkę szablonów z wyróżnione polem i panelem Wszystkie symbole zastępcze.](../media/content-understanding/content-assembly-create-template-4a.png)

   Obecnie użytkownicy mogą wypełnić symbol zastępczy na dwa sposoby:

   - [Wprowadzanie tekstu lub wybieranie daty](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Wybieranie jednej z opcji w kolumnie listy lub biblioteki](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Kojarzenie symbolu zastępczego przez wprowadzenie tekstu lub wybranie daty 

W **panelu Wszystkie symbole** zastępcze:

1. W **polu Nazwa** wprowadź odpowiednią nazwę symbolu zastępczego.

   ![Zrzut ekranu przedstawiający przeglądarkę szablonów z panelem Wszystkie symbole zastępcze służące do ręcznego wprowadzania danych.](../media/content-understanding/content-assembly-create-template-5.png)

2. W sekcji **Jak autorzy wypełnić ten symbol zastępczy** wybierz pozycję **Wprowadź tekst lub wybierz datę**.

3. W **polu Typ informacji** wybierz typ danych, który chcesz skojarzyć z symbolem zastępczym. Obecnie dostępnych jest sześć **opcji: Pojedynczy** wiersz **tekstu, Wiele** wierszy **tekstu, Liczba**, Data **i** **godzina, Wiadomość** e-mail i **Hiperlink**.

4. Wybierz opcję **Dodaj**.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Kojarzenie symbolu zastępczego przez wybranie jednej z opcji w kolumnie listy lub biblioteki

W **panelu Wszystkie symbole** zastępcze:

1. W **polu Nazwa** wprowadź odpowiednią nazwę symbolu zastępczego.

   ![Zrzut ekranu przedstawiający przeglądarkę szablonów z panelem Wszystkie symbole zastępcze do wprowadzania danych z SharePoint szablonu.](../media/content-understanding/content-assembly-create-template-6.png)

2. W sekcji **Jak autorzy wypełnili ten** symbol zastępczy wybierz pozycję Wybierz z opcji do wyboru w kolumnie listy lub biblioteki, **a** następnie wybierz pozycję **Wybierz**.

3. Na **stronie Wybierz listę do dodawania kolumny źródłowej** wybierz listę, której chcesz użyć, a następnie wybierz pozycję **Dalej**.

   ![Zrzut ekranu przedstawiający stronę Wybierz listę do dodawania kolumny źródłowej z listami.](../media/content-understanding/content-assembly-create-template-7.png)

4. Na **stronie Wybierz kolumnę źródłową** z istniejącej listy wybierz nazwę kolumny, którą chcesz skojarzyć z symbolem zastępczym, a następnie wybierz pozycję **Zapisz**. 

   ![Zrzut ekranu przedstawiający kolumnę Wybierz źródło na stronie istniejącej listy z nazwami kolumn.](../media/content-understanding/content-assembly-create-template-8.png)

    Jeśli chcesz ponownie wyświetlić oryginalną stronę list, wybierz pozycję Przejdź do **(** nazwa listy) linku u dołu listy.

5. Gdy to zrobisz, zobaczysz, że pole listy zostało skojarzone z symbolem zastępczym.

   ![Zrzut ekranu przedstawiający panel Wszystkie symbole zastępcze z polem listy skojarzonym z symbolem zastępczym.](../media/content-understanding/content-assembly-create-template-9.png)

6. Jeśli chcesz, aby użytkownicy mogli ręcznie dodawać dane wejściowe, oprócz wybierania z listy, wybierz pozycję Zezwalaj autorom **na dodawanie nowych opcji**. W tym przypadku domyślnym typem danych ręcznych jest *Pojedynczy wiersz tekstu*. Również wartości wprowadzane przez autorów będą używane tylko do wygenerowania dokumentu. Nie zostaną one dodane do SharePoint wiadomości.
 
Można utworzyć tyle symboli zastępczych, ile potrzeba. Po zapisaniu szablonu jako wersji roboczej lub opublikowaniu go możesz go opublikować.

   - **Zapisywanie wersji** roboczej — umożliwia zapisanie szablonu jako wersji roboczej i późniejsze uzyskanie do niego dostępu. Zapisane wersje robocze można wyświetlać, edytować lub publikować w sekcji **Nowoczesne szablony**,  >  wybierając **menu NowaEdytuj Nowy** w bibliotece dokumentów. 
   - **Publikuj** — publikuje szablon, który ma być używany przez innych użytkowników w organizacji do tworzenia dokumentów. W sekcji Nowoczesne szablony możesz wyświetlać, edytować lub cofać publikacje  szablonów, wybierając **menu NowaEdytowa**  >  Nowa z biblioteki dokumentów. 

## <a name="edit-a-modern-template"></a>Edytowanie nowoczesnego szablonu

Jeśli chcesz edytować istniejący szablon albo usunąć lub cofnąć jego publikację, wykonaj poniższe czynności.

1. W bibliotece dokumentów programu SharePoint wybierz menu **NowaEdytuj** >  Nowy. 
 
   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z wyróżniona opcją menu Edytuj nowy.](../media/content-understanding/content-assembly-edit-template-1.png)

2. W **panelu menu Edytuj nowy** w sekcji **Nowoczesne szablony** wybierz opublikowany lub wersja robocza szablonu, który chcesz edytować.
 
   ![Zrzut ekranu przedstawiający panel menu Edytuj nowy z wyświetloną sekcją Nowoczesne szablony.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Aby edytować opublikowany szablon lub szablon wersji roboczej:

   - W **przypadku szablonu Opublikowane** wybierz  **pozycjęEdyt,**  aby otworzyć studio szablonów, w którym możesz edytować opublikowany szablon. Możesz również usunąć lub cofnąć publikację szablonu. 
 
      ![Zrzut ekranu przedstawiający sekcję Nowoczesne szablony przedstawiającą opublikowane szablony.](../media/content-understanding/content-assembly-edit-published.png)

   - W **przypadku szablonu wersji** roboczej wybierz  **pozycjęEdyt** , aby otworzyć studio szablonów, w którym możesz edytować projekt szablonu. Możesz również usunąć lub opublikować szablon.
 
      ![Zrzut ekranu przedstawiający sekcję Nowoczesne szablony z wyświetloną wersjami roboczą szablonów.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Tworzenie dokumentu na podstawie nowoczesnego szablonu

Możesz użyć opublikowanego *nowoczesnego* szablonu, aby szybko tworzyć podobne dokumenty bez konieczności rozpoczynania od podstaw. Aby utworzyć dokument przy użyciu opublikowanego szablonu, wykonaj następujące czynności:

1. W bibliotece dokumentów programu SharePoint wybierz pozycję **Nowy**, a następnie wybierz nowoczesny szablon, którego chcesz użyć.
 
   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z opcjami nowoczesnego szablonu w menu Nowy.](../media/content-understanding/content-assembly-create-document-1.png)

2. Szablon zostanie otwarty w studio szablonów.

3. W **panelu Tworzenie dokumentu na podstawie szablonu** wprowadź odpowiednie informacje, a następnie wybierz pozycję **Utwórz dokument**.

   ![Zrzut ekranu przedstawiający bibliotekę dokumentów z panelem Tworzenie dokumentu na podstawie szablonu.](../media/content-understanding/content-assembly-create-document-2.png)

   Aby skrócić czas i ograniczyć nakład pracy związany z wypełnianiem wartości symboli zastępczych, SharePoint Syntex funkcje:

      - Sugestie, które ułatwiają wybieranie wartości podczas wybierania wartości z listy.
      - Autowypełnianie wartości zastępczych, jeśli mogą jednoznacznie identyfikować rekord dla symboli zastępczych skojarzonych z tą samą listą.

> [!NOTE]
> - Obecnie tworzenie szablonu Microsoft Word obsługiwane .docx (rozszerzenie projektu). Przed przekazaniem dokumentu upewnij się, że w dokumencie programu Word nie jest **włączone śledzenie zmian** ani komentarze. Jeśli dokument zawiera symbole zastępcze tekstu dla obrazów, upewnij się, że nie są one zawinięte. Obecnie nie obsługujemy **kontrolek zawartości w** programie Word. Jeśli chcesz utworzyć szablon na podstawie dokumentu programu Word z kontrolkami zawartości, usuń je przed utworzeniem nowoczesnego szablonu.
>- Szablon i dokument są skojarzone z jedną biblioteką dokumentów. Aby użyć szablonu w innej bibliotece dokumentów, należy ponownie utworzyć szablon w tej bibliotece dokumentów.
>- Przekazany dokument użyty do utworzenia nowoczesnego szablonu zostanie zapisany jako oddzielna kopia i umieszczona w katalogu /forms biblioteki dokumentów. Nie ma to wpływu na oryginalny plik na dysku.
>- Symbole zastępcze można tworzyć tylko dla tekstu. Obecnie obrazy, grafiki smartart, tabele i listy punktorów nie są obsługiwane.
>- Po utworzeniu dokumentu na podstawie szablonu nie jest on skojarzony z szablonem.



 
