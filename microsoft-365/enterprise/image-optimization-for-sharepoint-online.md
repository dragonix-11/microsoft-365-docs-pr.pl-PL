---
title: Optymalizacja obrazu dla SharePoint klasycznych witryn publikowania w trybie online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak za pomocą odwzorowań i obiektów towych zwiększyć wydajność obrazu w SharePoint klasycznych witryn publikowania online.
ms.openlocfilehash: fe3c698dda06559bf6e104650b6b8bb8d81172fa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988403"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Optymalizacja obrazu dla SharePoint klasycznych witryn publikowania w trybie online

Szybkość ładowania strony internetowej zależy od łącznego rozmiaru wszystkich składników wymaganych do renderowania strony, w tym obrazów, kodu HTML, kodu JavaScript i arkuszy CSS. Obrazy są doskonałym sposobem na uaekscyjnianie witryny, ale ich rozmiar może mieć wpływ na wydajność. Dzięki optymalizacji obrazów za pomocą kompresji i zmiany rozmiaru oraz używaniu grafik można zrównoważyć efekty bardzo dużych obrazów. Za SharePoint odwzorowań obrazu można przekazać jeden duży obraz i wyświetlić jego sekcje, aby można było go ponownie używać zamiast ponownego ładowania.

>[!NOTE]
>Ten temat dotyczy klasycznych SharePoint publikowania w trybie online, a nie nowoczesnych witryn portalu. Aby uzyskać informacje na temat optymalizacji obrazów w SharePoint nowoczesnych witrynach portalu online, zobacz Optymalizowanie obrazów w SharePoint [nowoczesnych stron portalu w trybie online](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Używanie sprites w celu przyspieszenia ładowania obrazów

![Zrzut ekranu przedstawiający spcommon.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Grafika obrazów zawiera wiele mniejszych obrazów. Za pomocą arkuszy CSS wybierasz część złożonego obrazu do wyświetlania w konkretnej części strony z pozycjonowaniem bezwzględnym. Po prostu zamiast ładować wiele obrazów przenosisz jeden obraz na stronie i wyświetlasz tylko jego niewielki fragment w małym oknie, w którym użytkownikowi końcoweowi jest wyświetlany wymagany fragment obrazu. SharePoint Online używa sprites do wyświetlania różnych ikon w pliku spcommon.png pliku.

Czego dotyczy ten zakres:
- Kompresja obrazu
- Optymalizacja obrazu
- SharePoint odwzorowań obrazu
   
Może to zwiększyć wydajność, ponieważ zamiast kilku obrazów zostanie pobrana tylko jedna, a następnie buforowany i ponownie użyty. Nawet jeśli obraz nie pozostaje w pamięci podręcznej, posiadanie jednego obrazu zamiast wielu obrazów powoduje zmniejszenie całkowitej liczby żądań HTTP do serwera, co skraca czas ładowania strony. Jest to w ist. forma tworzenie pakietów obrazów. Ta technika jest bardzo przydatna, gdy obrazy nie zmieniają się zbyt często, na przykład ikony, jak pokazano w powyższym SharePoint przykładzie. Możesz to łatwo osiągnąć w programie Microsoft Visual Studio za pomocą web [essentials](https://vswebessentials.com/), zewnętrznego projektu społecznościowego open source. Aby uzyskać więcej informacji, zobacz [Mifikowanie i tworzenie pakietów w u SharePoint Online](./minification-and-bundling-in-sharepoint-online.md).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Używanie kompresji i optymalizacji obrazów w celu przyspieszenia ładowania strony

Kompresja i optymalizacja obrazów to zmniejszenie rozmiaru pliku obrazów, których używasz w witrynie. Często najlepszą metodą zmniejszenia rozmiaru obrazu jest zmiana jego rozmiaru do maksymalnych wymiarów, w których będzie on przeglądany w witrynie. Nie ma sensu posiadanie obrazu o rozmiarze większym niż ten, który będzie kiedykolwiek przeglądany. Upewnienie się, że obrazy mają odpowiednie wymiary za pomocą edytora obrazów, to szybki i łatwy sposób na zmniejszenie rozmiaru strony.
  
Gdy obrazy mają odpowiedni rozmiar, następnym krokiem jest zoptymalizowanie ich kompresji. Dostępne są różne narzędzia do kompresji i optymalizacji, w tym Galeria fotografii i narzędzia innych firm. Kluczem do kompresji jest jak najwięcej zmniejszenie rozmiaru pliku bez utraty jakości widocznej dla użytkowników końcowych. Pamiętaj, aby przetestować skompresowane pliki na ekranie o wysokiej rozdzielczości, aby zapewnić, że nadal będą dobrze wyglądać.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Przyspieszanie pobierania stron za pomocą SharePoint odwzorowań obrazów

Odwzorowania obrazów to funkcja dostępna w SharePoint Online, która pozwala na korzystanie z różnych wersji obrazów na podstawie wstępnie zdefiniowanych wymiarów obrazów. Jest to szczególnie ważne, gdy zawartość obrazu jest generowana przez użytkownika lub wymiary obrazu, takie jak szerokość i wysokość, są ustalone przez styl CSS w witrynie. Nawet jeśli obraz jest naprawiony przez styl CSS, nadal jest ładowany obraz w pełnej rozdzielczości. W takim przypadku rozmiar pliku można zmniejszyć za pomocą odwzorowań obrazu.
  
> [!NOTE]
> Odwzorowania są dostępne tylko dla SharePoint włączono publikowanie. Publikowanie można włączyć w obszarze Ustawienia \> witryny Ustawienia \> Zarządzanie funkcjami witryny w SharePoint \> publikowania na serwerze. Inaczej ta opcja nie będzie wyświetlana.
  
Zmiana rozmiaru odwzorowania obrazu działa przez określenie najmniejszego rozmiaru (szerokości lub wysokości), a następnie zmiany rozmiaru obrazu w taki sposób, aby rozmiar drugiego wymiaru był automatycznie zmieniany według zablokowanego współczynnika proporcji. Domyślnie obraz zostanie przycięty od środka według pozostałych wymiarów. Jeśli na przykład zdefiniowano odwzorowanie o szerokości 100 pikseli i wysokości 50 pikseli, a oryginalny obraz ma 1000 pikseli szerokości i 800 pikseli wysokości, zostanie on zmieniony tak, aby wymiar 800 pikseli miał teraz 50 pikseli, a wymiar 1000 pikseli (teraz 62,5 piksela) zostanie przycięty od środka obrazu.
  
Kroki są stosunkowo proste, ale aby obrazy używać odwzorowań, odwzorowania muszą się znaleźć w witrynie SharePoint, zanim dodasz obrazy. Ponadto musisz mieć włączone funkcje infrastruktury publikowania w SharePoint server (na poziomie zbioru witryn) i publikowania na SharePoint server (na poziomie witryny).
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Dodawanie odwzorowania obrazu w celu przyspieszenia ładowania strony
  
1. Upewnij się, że konto użytkownika wykonującego tę procedurę ma co najmniej uprawnienia do projektowania witryny najwyższego poziomu w zbiorze witryn oraz czy witryna jest publikowana na stronie internetowej.

2. W przeglądarce internetowej przejdź do witryny najwyższego poziomu w zbiorze witryn publikowania.

3. Wybierz **ikonę Ustawienia**.

4. Na **stronie Ustawienia** w sekcji Wygląd i sposób pracy zobaczysz wbudowane  odwzorowania obrazu.

    Możesz użyć odwzorowań poza polem lub wybrać pozycję Odwzorowania obrazu **, aby utworzyć** nowe odwzorowania.

    ![Zrzut ekranu przedstawiający odwzorowanie obrazu.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Na **stronie Odwzorowania obrazów** wybierz pozycję **Dodaj nowy element**.

    ![Zrzut ekranu przedstawiający pozycję Dodaj nowy element.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Na **stronie Nowe odwzorowanie** obrazu w **polu Nazwa wprowadź** nazwę odwzorowania.

7. W **polach** **tekstowych** Szerokość i Wysokość wprowadź szerokość i wysokość odwzorowania (w pikselach), a następnie wybierz pozycję **Zapisz**.

    ![Zrzut ekranu przedstawiający nazwę odwzorowania obrazu.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Niestandardowe przycinanie za pomocą odwzorowań obrazu

Domyślnie odwzorowanie obrazu jest generowane od środka obrazu. Odwzorowanie obrazu dla pojedynczych obrazów można dostosować, przycinając fragment obrazu, którego chcesz użyć. Obrazy można przycinać indywidualnie dla każdego odwzorowania. Przycinanie obrazów przyspiesza ładowanie strony, SharePoint pamięci podręcznej obiektów blob firmy SharePoint tworzenia wersji obrazu dla każdego odwzorowania. Zmniejsza to obciążenie serwera, ponieważ rozmiar obrazu jest zmieniany tylko raz, a następnie jest gotowy do wielokrotnego odczytu dla użytkowników końcowych. Aby uzyskać więcej informacji na temat przycinania odwzorowania obrazu, zobacz [Przycinanie odwzorowania obrazu](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
