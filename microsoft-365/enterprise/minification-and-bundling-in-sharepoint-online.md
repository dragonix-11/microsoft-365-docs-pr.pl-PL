---
title: Minifikacja i tworzenie pakietów w u SharePoint Online
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
description: Dowiedz się, jak za pomocą technik zminifikowania i tworzenie pakietów oraz programu Web Essentials zmniejszyć liczbę żądań HTTP i czas ładowania stron w u SharePoint Online.
ms.openlocfilehash: fabf690f523cabf67fe775bbd1a10251a477f633
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014683"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minifikacja i tworzenie pakietów w u SharePoint Online

W tym artykule opisano, jak za pomocą technik minifikacji i tworzenie pakietów oraz programu Web Essentials zmniejszyć liczbę żądań HTTP i skrócić czas ładowania stron w umacie SharePoint Online.
  
Podczas dostosowywania witryny sieci Web możesz dodać dużą liczbę dodatkowych plików do serwera w celu obsługi dostosowania. Dodanie dodatkowego kodu JavaScript, arkusza CSS i obrazów zwiększa liczbę żądań HTTP do serwera, co z kolei powoduje zwiększenie czasu wyświetlania strony internetowej. Jeśli masz wiele plików tego samego typu, możesz utworzyć z nich pakiet, aby przyspieszyć ich pobieranie.
  
W przypadku plików JavaScript i CSS możesz również użyć podejścia nazywanego minifikacją, które pozwala zmniejszyć całkowity rozmiar plików przez usunięcie odstępów i innych znaków, które nie są potrzebne.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Zminifikowanie i tworzenie pakietów plików JavaScript i CSS za pomocą oprogramowania Web Essentials

Do programowania w pakiecie plików CSS i JavaScript możesz używać oprogramowania innych firm, takiego jak Web Essentials.
  
> [!IMPORTANT]
> Web Essentials to projekt społecznościowy typu Open Source innej firmy. To oprogramowanie jest rozszerzeniem oprogramowania do wersji Visual Studio 2012 i Visual Studio 2013 i nie jest obsługiwane przez firmę Microsoft. Aby pobrać oprogramowanie Web Essentials, odwiedź witrynę internetową pod witrynie [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).
  
Web Essentials oferuje dwie formy pakietów:
  
- .bundle: dla plików CSS i JavaScript
- sprite: dotyczy obrazów (dostępne tylko w programie Visual Studio 2013)

Składników Web Essentials możesz używać, jeśli masz istniejącą funkcję z pewnymi elementami marki, do których odwołują się w obrębie niestandardowej strony wzorcowej, takimi jak:
  
![Zrzut ekranu przedstawiający element marki na niestandardowej stronie wzorcowej.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Aby utworzyć pakiet TE000127218 i CSS w programie Web Essentials
  
1. W Visual Studio w Eksploratorze rozwiązań zaznacz pliki, które chcesz dołączyć do pakietu.
2. Kliknij prawym przyciskiem myszy zaznaczone pliki, a następnie z menu kontekstowego wybierz polecenie **Web Essentials** \> **Create JavaScript bundle file** . Przykład:

    ![Zrzut ekranu przedstawiający opcje menu Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Wyświetlanie wyników tworzenie pakietów plików JavaScript i CSS

Podczas tworzenia pakietu JavaScript i CSS oprogramowanie Web Essentials tworzy plik XML nazywany plikiem przepisu, który identyfikuje pliki JavaScript i CSS, a także niektóre inne informacje o konfiguracji:
  
![Zrzut ekranu przedstawiający plik z przepisami JavaScript i CSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Ponadto, jeśli flaga mifikacji w przepisie na tworzenie pakietu ma wartość "true", pliki są zmniejszane i powiązane ze sobą. Oznacza to, że utworzono nowe, zminifikowane wersje plików JavaScript, do których można odwoływać się na stronie wzorcowej.
  
![Zrzut ekranu przedstawiający flagę minify ustawioną na wartość True (Prawda).](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Podczas ładowania strony z witryny sieci Web można za pomocą narzędzi deweloperskiej przeglądarki internetowej, takich jak program Internet Explorer 11, sprawdzić liczbę żądań wysłanych do serwera i czas ładowania każdego pliku.
  
Na poniższej ilustracji przedstawiono wynik ładowania plików JavaScript i CSS przed zminifikacją.
  
![Zrzut ekranu przedstawiający pobranie 80 elementów.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Po opakowaniu razem plików CSS i JavaScript liczba żądań została upuszczona do 74, a czas pobierania poszczególnych plików był tylko nieznacznie dłuższy niż w przypadku oryginalnych plików:
  
![Zrzut ekranu przedstawiający pobranie 74 elementów.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Po pakietów plik pakietu JavaScript został znacznie zmniejszony z 815 KB do 365 KB:
  
![Zrzut ekranu przedstawiający zmniejszony rozmiar pobierania.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Tworzenie pakietów obrazów przez utworzenie grafika obrazów

Podobnie jak w przypadku programowania plików JavaScript i CSS można połączyć wiele małych ikon i innych typowych obrazów w większy arkusz, a następnie za pomocą arkusza CSS odsłonić poszczególne obrazy. Zamiast pobierania poszczególnych obrazów przeglądarka internetowa użytkownika raz pobiera arkusz plików, a następnie buforuje go na komputerze lokalnym. Zwiększa to wydajność ładowania stron przez zmniejszenie liczby pobrań i odebrań do serwera sieci Web.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Aby utworzyć sprite obrazu w programie Web Essentials**
  
1. W Visual Studio w Eksploratorze rozwiązań zaznacz pliki, które chcesz dołączyć do pakietu.
2. Kliknij prawym przyciskiem myszy zaznaczone pliki, a następnie z menu kontekstowego wybierz pozycję **Web Essentials** \> **Create image sprite** . Przykład:

    ![Zrzut ekranu przedstawiający sposób tworzenia grafika obrazu.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Wybierz lokalizację zapisu pliku sprite. Plik sprite jest plikiem XML, który opisuje ustawienia i pliki obiektu. Na poniższych ilustracjach przedstawiono przykładowy plik PNG obiektu i odpowiadający mu plik XML sprite.

    ![Zrzut ekranu przedstawiający plik sprite.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Zrzut ekranu przedstawiający plik XML obiektu.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
