---
title: Optymalizacja obrazów dla klasycznych witryn publikowania w usłudze SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Dowiedz się, jak używać odwzorowania i sprite'ów w celu zwiększenia wydajności obrazów w klasycznych witrynach publikowania SharePoint Online.
ms.openlocfilehash: 39d0e4c26339ecf70c922636f82dcef82dd4b13e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754427"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Optymalizacja obrazów dla klasycznych witryn publikowania w usłudze SharePoint Online

Szybkość ładowania strony internetowej zależy od łącznego rozmiaru wszystkich składników wymaganych do renderowania strony, w tym obrazów, HTML, JavaScript i CSS. Obrazy to doskonały sposób, aby witryna była bardziej atrakcyjna, ale ich rozmiar może mieć wpływ na wydajność. Optymalizując obrazy przy użyciu kompresji i zmiany rozmiaru oraz używając elementów sprite, możesz zrównoważyć skutki dużych obrazów. Przy użyciu SharePoint odwzorowania obrazów można przekazać jeden duży obraz i wyświetlić sekcje obrazu, co pozwoli na ponowne użycie, a nie ponowne załadowanie.

>[!NOTE]
>Ten temat dotyczy klasycznych witryn publikowania SharePoint Online, a nie nowoczesnych witryn portalu. Aby uzyskać informacje na temat optymalizacji obrazów w nowoczesnych witrynach portalu SharePoint Online, zobacz [Optymalizowanie obrazów na nowoczesnych stronach portalu SharePoint Online](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Przyspieszanie ładowania obrazów przy użyciu elementów sprite

![Zrzut ekranu przedstawiający polecenie spcommon.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Sprite obrazu zawiera wiele mniejszych obrazów. Przy użyciu css wybierz część obrazu złożonego do wyświetlenia w określonej części strony z położeniem bezwzględnym. Zasadniczo jeden obraz jest przenoszony wokół strony zamiast ładowania wielu obrazów i sprawia, że niewielka część tego obrazu jest widoczna przez małe okno, w którym wymagana część obrazu sprite jest wyświetlana użytkownikowi końcowemu. SharePoint Online używa elementów sprite do wyświetlania różnych ikon w pliku spcommon.png sprite.

Co jest tutaj omówione:
- Kompresja obrazu
- Optymalizacja obrazu
- SharePoint odwzorowania obrazów
   
Może to zwiększyć wydajność, ponieważ pobierasz tylko jeden obraz zamiast kilku, a następnie buforujesz i ponownie używasz tego obrazu. Nawet jeśli obraz nie pozostaje w pamięci podręcznej, mając jeden obraz zamiast wielu obrazów, ta metoda zmniejsza całkowitą liczbę żądań HTTP do serwera, co skróci czas ładowania strony. To jest naprawdę forma łączenia obrazów. Jest to przydatna technika, jeśli obrazy nie zmieniają się często, na przykład ikony, jak pokazano w przykładzie SharePoint podanym powyżej. Dowiesz się, jak za pomocą usługi [Web Essentials](https://vswebessentials.com/), projektu opartego na społeczności innej firmy, open source, łatwo to osiągnąć w Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz [Artykuł Minification and bundling in SharePoint Online (Minification and bundling in SharePoint Online](./minification-and-bundling-in-sharepoint-online.md)).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Przyspieszanie ładowania stron przy użyciu kompresji i optymalizacji obrazu

Kompresja i optymalizacja obrazu polega na zmniejszeniu rozmiaru pliku obrazów używanych w witrynie. Często najlepszą techniką zmniejszania rozmiaru obrazu jest zmiana rozmiaru obrazu do maksymalnych wymiarów, które będą wyświetlane w witrynie. Nie ma sensu mieć większego obrazu niż kiedykolwiek będzie wyświetlany. Upewnienie się, że obrazy mają prawidłowe wymiary przy użyciu edytora obrazów, jest szybkim i łatwym sposobem zmniejszenia rozmiaru strony.
  
Gdy obrazy mają odpowiedni rozmiar, następnym krokiem jest zoptymalizowanie kompresji tych obrazów. Dostępne są różne narzędzia do kompresji i optymalizacji, w tym galeria zdjęć i narzędzia innych firm. Kluczem do kompresji jest jak najbardziej zmniejszenie rozmiaru pliku bez utraty zauważalnej jakości dla użytkowników końcowych. Upewnij się, że skompresowane pliki są testowane na ekranie o wysokiej rozdzielczości, aby upewnić się, że nadal będą wyglądać dobrze.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Przyspieszanie pobierania stron przy użyciu odwzorowania obrazów SharePoint

Odwzorowania obrazów są funkcją w usłudze SharePoint Online, która umożliwia obsługę różnych wersji obrazów na podstawie wstępnie zdefiniowanych wymiarów obrazu. Jest to szczególnie ważne, gdy zawartość obrazu wygenerowana przez użytkownika lub wymiary obrazu, takie jak szerokość i wysokość, są naprawiane przez css w witrynie. Nawet jeśli obraz został naprawiony przez css, obraz w pełnej rozdzielczości jest nadal ładowany. W takim przypadku rozmiar pliku można zmniejszyć przy użyciu odwzorowania obrazów.
  
> [!NOTE]
> Odwzorowania są dostępne tylko dla SharePoint po włączeniu publikowania. Publikowanie można włączyć w obszarze Ustawienia \> Witryna Ustawienia \> Zarządzanie funkcjami \> lokacji SharePoint Publikowanie serwera. Opcja nie będzie wyświetlana w inny sposób.
  
Zmiana rozmiaru odwzorowania obrazu polega na utworzeniu najmniejszego zdefiniowanego wymiaru, szerokości lub wysokości, a następnie zmiana rozmiaru obrazu w taki sposób, aby drugi wymiar był automatycznie zmieniany na podstawie zablokowanego współczynnika proporcji. Domyślnie obraz zostanie przycięty ze środka przez pozostałe wymiary. Jeśli na przykład zdefiniujesz odwzorowanie o szerokości 100 pikseli i wysokości 50 pikseli, a oryginalny obraz ma 1000 pikseli szerokości i 800 pikseli wysokości, zostanie on zmieniony tak, aby wymiar 800 pikseli miał teraz rozmiar 50 pikseli, a wymiar 1000 pikseli (teraz 62,5 pikseli) został przycięty ze środka obrazu.
  
Kroki są stosunkowo proste, ale aby obrazy używały odwzorowania, odwzorowania muszą znajdować się w witrynie SharePoint przed dodaniem obrazów. Ponadto należy również włączyć funkcje infrastruktury publikowania serwera SharePoint (poziom zbioru witryn) i publikowania serwera SharePoint (poziom lokacji).
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Dodawanie odwzorowania obrazu w celu przyspieszenia ładowania stron
  
1. Sprawdź, czy konto użytkownika wykonujące tę procedurę ma co najmniej uprawnienia projektowania do witryny najwyższego poziomu zbioru witryn i czy witryna jest publikowana na stronie internetowej.

2. W przeglądarce internetowej przejdź do witryny najwyższego poziomu zbioru witryn publikowania.

3. Wybierz ikonę **Ustawienia**.

4. Na stronie **Ustawienia witryny** w sekcji **Look and Feel** zostaną wyświetlone wbudowane odwzorowania obrazów.

    Możesz użyć odwzorowania po wyjętej wersji lub wybrać pozycję **Odwzorowania obrazów** , aby utworzyć nowe.

    ![Zrzut ekranu przedstawiający odwzorowanie obrazu.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Na stronie **Odwzorowania obrazów** wybierz pozycję **Dodaj nowy element**.

    ![Zrzut ekranu przedstawiający dodawanie nowego elementu.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Na stronie **Odwzorowanie nowego obrazu** w polu **Nazwa** wprowadź nazwę odwzorowania.

7. W polach tekstowych **Szerokość** i **Wysokość** wprowadź szerokość i wysokość w pikselach odwzorowania, a następnie wybierz pozycję **Zapisz**.

    ![Zrzut ekranu przedstawiający nazwę odwzorowania obrazu.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Przycinanie niestandardowe z odwzorowaniami obrazów

Domyślnie odwzorowanie obrazu jest generowane na środku obrazu. Odwzorowanie obrazu dla poszczególnych obrazów można dostosować, przycinając część obrazu, która ma być używana. Obrazy można przycinać indywidualnie dla każdego odwzorowania. Przycinanie obrazów przyspiesza ładowanie stron przy użyciu pamięci podręcznej obiektów blob SharePoint w celu utworzenia wersji obrazu dla każdego odwzorowania. W ten sposób obciążenie serwera jest mniejsze, ponieważ rozmiar obrazu jest zmieniany tylko raz, a następnie jest gotowy do wielokrotnego obsługi dla użytkowników końcowych. Aby uzyskać więcej informacji na temat przycinania odwzorowania obrazu, zobacz [Przycinanie odwzorowania obrazu](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
