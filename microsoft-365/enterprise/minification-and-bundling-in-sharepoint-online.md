---
title: Minification and bundling in SharePoint Online (Minification and bundling in SharePoint Online )Minification and bundling in SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Dowiedz się, jak używać technik minimalizowania i łączenia z usługą Web Essentials w celu zmniejszenia liczby żądań HTTP oraz czasu potrzebnego na załadowanie stron w usłudze SharePoint Online.
ms.openlocfilehash: b02cf095b1d7f05a82df1cf98a590ff762453f8a
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637632"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minification and bundling in SharePoint Online (Minification and bundling in SharePoint Online )Minification and bundling in SharePoint Online

W tym artykule opisano sposób używania technik minimalizowania i łączenia z usługą Web Essentials w celu zmniejszenia liczby żądań HTTP i skrócenia czasu ładowania stron w usłudze SharePoint Online.
  
Po dostosowaniu witryny internetowej można dodać do serwera dużą liczbę dodatkowych plików w celu obsługi dostosowywania. Dodanie dodatkowych skryptów JavaScript, CSS i obrazów zwiększa liczbę żądań HTTP do serwera, co z kolei zwiększa czas potrzebny na wyświetlenie strony internetowej. Jeśli masz wiele plików tego samego typu, możesz spakować te pliki, aby przyspieszyć pobieranie tych plików.
  
W przypadku plików JavaScript i CSS można również użyć podejścia o nazwie minification, w którym można zmniejszyć całkowity rozmiar plików przez usunięcie białych znaków i innych znaków, które nie są konieczne.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minification and bundling JavaScript and CSS files with Web Essentials

Do tworzenia pakietów plików CSS i JavaScript można używać oprogramowania innych firm, takiego jak Web Essentials.
  
> [!IMPORTANT]
> Web Essentials to projekt oparty na społeczności innej firmy, typu open source. Oprogramowanie jest rozszerzeniem do Visual Studio 2012 i Visual Studio 2013 i nie jest obsługiwane przez firmę Microsoft. Aby pobrać program Web Essentials, odwiedź witrynę internetową [web essentials 2012](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebEssentials2012).
  
Usługa Web Essentials oferuje dwie formy tworzenia pakietów:
 
- .bundle: dla plików CSS i JavaScript
- .sprite: dla obrazów (dostępne tylko w Visual Studio 2013)

Usługi Web Essentials można użyć, jeśli masz istniejącą funkcję z niektórymi elementami znakowania, do których odwołuje się strona wzorca niestandardowego, na przykład:
  
![Zrzut ekranu przedstawiający element marki na niestandardowej stronie wzorcowej.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Aby utworzyć pakiet TE000127218 i CSS w usłudze Web Essentials
  
1. W Visual Studio w Eksplorator rozwiązań wybierz pliki, które chcesz uwzględnić w pakiecie.
2. Kliknij prawym przyciskiem myszy wybrane pliki, a następnie wybierz pozycję **Web Essentials** \> **Utwórz plik pakietu JavaScript** z menu kontekstowego. Przykład:

    ![Zrzut ekranu przedstawiający opcje menu Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Wyświetlanie wyników tworzenia pakietów plików JavaScript i CSS

Podczas tworzenia pakietu JavaScript i CSS usługa Web Essentials tworzy plik XML o nazwie plik przepisu, który identyfikuje pliki JavaScript i CSS, a także inne informacje o konfiguracji:
  
![Zrzut ekranu przedstawiający plik przepisów języka JavaScript i CSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Ponadto jeśli flaga minify jest ustawiona na wartość true w przepisie pakietowym, pliki zostaną zmniejszone i połączone ze sobą. Oznacza to, że utworzono nowe, zmifikowane wersje plików JavaScript, do których można odwoływać się na stronie wzorcowej.
  
![Zrzut ekranu przedstawiający flagę minify ustawioną na true.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Po załadowaniu strony z witryny internetowej możesz użyć narzędzi deweloperskich z przeglądarki internetowej, takich jak Internet Explorer 11, aby wyświetlić liczbę żądań wysłanych do serwera i czas ładowania każdego pliku.
  
Poniższa ilustracja jest wynikiem ładowania plików JavaScript i CSS przed minyfikacją.
  
![Zrzut ekranu przedstawiający 80 pobranych elementów.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Po połączeniu plików CSS i JavaScript liczba żądań spadła do 74, a każdy plik trwał tylko nieco dłużej niż oryginalne pliki do pobrania indywidualnie:
  
![Zrzut ekranu przedstawiający pobrane 74 elementy.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Po utworzeniu pakietu plik pakietu JavaScript został znacznie zmniejszony z 815 KB do 365 KB:
  
![Zrzut ekranu przedstawiający zmniejszony rozmiar pobierania.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Łączenie obrazów przez utworzenie sprite obrazu

Podobnie jak w przypadku pakietów plików JavaScript i CSS, możesz połączyć wiele małych ikon i innych typowych obrazów w większy arkusz sprite, a następnie użyć css do ujawnienia poszczególnych obrazów. Zamiast pobierać poszczególne obrazy, przeglądarka internetowa użytkownika pobiera arkusz sprite raz, a następnie buforuje go na komputerze lokalnym. Zwiększa to wydajność ładowania stron przez zmniejszenie liczby pobrań i rund na serwer internetowy.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Aby utworzyć sprite obrazu w składniku Web Essentials**
  
1. W Visual Studio w Eksplorator rozwiązań wybierz pliki, które chcesz uwzględnić w pakiecie.
2. Kliknij prawym przyciskiem myszy wybrane pliki, a następnie wybierz pozycję **Web Essentials** \> **Utwórz sprite obrazu** z menu kontekstowego. Przykład:

    ![Zrzut ekranu przedstawiający sposób tworzenia sprite obrazu.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Wybierz lokalizację, aby zapisać plik sprite. Plik sprite to plik XML opisujący ustawienia i pliki w sprite. Poniższe dane przedstawiają przykład pliku PNG sprite i odpowiadającego mu pliku XML sprite.

    ![Zrzut ekranu przedstawiający plik sprite.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Zrzut ekranu przedstawiający plik XML sprite.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
