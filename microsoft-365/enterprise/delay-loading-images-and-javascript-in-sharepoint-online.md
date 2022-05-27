---
title: Opóźnienie ładowania obrazów i języka JavaScript w usłudze SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
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
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Dowiedz się, jak skrócić czas ładowania stron usługi SharePoint Online przy użyciu języka JavaScript w celu opóźnienia ładowania obrazów i innych niż istotne skrypty JavaScript.
ms.openlocfilehash: 8252e169e36dc6976a7be0b4815915ee72283eff
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754737"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Opóźnienie ładowania obrazów i języka JavaScript w usłudze SharePoint Online

W tym artykule opisano sposób skrócenia czasu ładowania stron usługi SharePoint Online przy użyciu języka JavaScript w celu opóźnienia ładowania obrazów, a także oczekiwania na załadowanie nieistotnego kodu JavaScript do momentu załadowania strony.
  
Obrazy mogą negatywnie wpływać na szybkość ładowania stron w SharePoint Online. Domyślnie większość nowoczesnych przeglądarek internetowych pobiera obrazy wstępnie podczas ładowania strony HTML. Może to spowodować niepotrzebne spowolnienie ładowania strony, jeśli obrazy nie są widoczne na ekranie, dopóki użytkownik nie przewinie w dół. Obrazy mogą zablokować przeglądarce możliwość ładowania widocznej części strony. Aby obejść ten problem, możesz użyć języka JavaScript, aby najpierw pominąć ładowanie obrazów. Ponadto ładowanie nieistotnego kodu JavaScript może spowolnić czas pobierania na stronach SharePoint. W tym temacie opisano niektóre metody, których można użyć w celu skrócenia czasu ładowania stron za pomocą języka JavaScript w usłudze SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Skrócenie czasu ładowania strony przez opóźnienie ładowania obrazów na stronach SharePoint Online przy użyciu języka JavaScript

Za pomocą języka JavaScript można uniemożliwić przeglądarce internetowej wstępne pobieranie obrazów. Przyspiesza to ogólne renderowanie dokumentów. W tym celu należy usunąć wartość atrybutu src z tagu \<img\> i zastąpić ją ścieżką do pliku w atrybucie danych, takim jak: data-src. Przykład:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Przy użyciu tej metody przeglądarka nie pobiera obrazów natychmiast. Jeśli obraz znajduje się już w okienku widoków, język JavaScript nakazuje przeglądarce pobranie adresu URL z atrybutu danych i wstawienie go jako wartości atrybutu src. Obraz ładuje się tylko w miarę przewijania użytkownika i jest wyświetlany.
  
Aby to wszystko się stało, musisz użyć języka JavaScript.
  
W pliku tekstowym zdefiniuj funkcję **isElementInViewport(),** aby sprawdzić, czy element znajduje się w części przeglądarki, która jest widoczna dla użytkownika.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

Następnie użyj polecenia **isElementInViewport()** w funkcji **loadItemsInView(** ). Funkcja **loadItemsInView()** załaduje wszystkie obrazy, które mają wartość atrybutu data-src, jeśli znajdują się w części przeglądarki, która jest widoczna dla użytkownika. Dodaj następującą funkcję do pliku tekstowego:
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

Na koniec **wywołaj funkcję loadItemsInView()** z poziomu **pliku window.onscroll(),** jak pokazano w poniższym przykładzie. Dzięki temu wszystkie obrazy znajdujące się w okienku widoków są ładowane zgodnie z potrzebami użytkownika, ale nie wcześniej. Dodaj następujące elementy do pliku tekstowego:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

W przypadku SharePoint Online należy dołączyć następującą funkcję do zdarzenia przewijania w tagu obszaru roboczego \<div\> #s4. Dzieje się tak, ponieważ zdarzenia okna są zastępowane w celu zapewnienia, że wstążka pozostanie dołączona do górnej części strony.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Zapisz plik tekstowy jako plik JavaScript z rozszerzeniem .js, na przykład delayLoadImages.js.
  
Po zakończeniu pisania delayLoadImages.js możesz dodać zawartość pliku do strony wzorcowej w usłudze SharePoint Online. Można to zrobić, dodając link skryptu do nagłówka na stronie wzorcowej. Po umieszczeniu go na stronie wzorcowej język JavaScript zostanie zastosowany do wszystkich stron w witrynie SharePoint Online korzystających z tego układu strony wzorcowej. Alternatywnie, jeśli zamierzasz używać tego tylko na jednej stronie witryny, użyj składnika Web Part edytora skryptów, aby osadzić skrypt JavaScript na stronie. Aby uzyskać więcej informacji, zobacz następujące tematy:
  
- [Instrukcje: stosowanie strony wzorcowej do witryny w SharePoint 2013 r.](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [Instrukcje: tworzenie układu strony w SharePoint 2013 r.](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Przykład: odwoływanie się do pliku delayLoadImages.js Języka JavaScript ze strony wzorcowej w usłudze SharePoint Online
  
Aby to działało, należy również odwołać się do trybu jQuery na stronie wzorcowej. W poniższym przykładzie na początkowym załadowaniu strony widać, że załadowano tylko jeden obraz, ale na stronie jest ich jeszcze kilka.
  
![Zrzut ekranu przedstawiający jeden obraz załadowany na stronie.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Na poniższym zrzucie ekranu przedstawiono pozostałe obrazy pobrane po przewinięciem do widoku.
  
![Zrzut ekranu przedstawiający kilka obrazów załadowanych na stronie.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Opóźnienie ładowania obrazów przy użyciu języka JavaScript może być efektywną techniką zwiększania wydajności; Jeśli jednak technika zostanie zastosowana w publicznej witrynie internetowej, wyszukiwarki nie będą mogły przeszukiwać obrazów w taki sam sposób, w jaki przeszukiwałyby regularnie sformułowany obraz. Może to mieć wpływ na klasyfikacje aparatów wyszukiwania, ponieważ metadane na samym obrazie nie są tak naprawdę dostępne, dopóki strona nie zostanie załadowana. Przeszukiwarki aparatu wyszukiwania odczytują tylko kod HTML i w związku z tym nie będą widzieć obrazów jako zawartości na stronie. Obrazy są jednym z czynników używanych do klasyfikacji stron w wynikach wyszukiwania. Jednym ze sposobów obejścia tego celu jest użycie tekstu wprowadzającego dla obrazów.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>przykład kodu GitHub: wstrzykiwanie kodu JavaScript w celu zwiększenia wydajności

Nie przegap przykładu artykułu i kodu w [języku JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) podanym w GitHub.
  
## <a name="see-also"></a>Zobacz też

[Obsługiwane przeglądarki w Office 2013 r. i Aplikacje Microsoft 365 dla przedsiębiorstw](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Instrukcje: stosowanie strony wzorcowej do witryny w SharePoint 2013 r.](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[Instrukcje: tworzenie układu strony w SharePoint 2013 r.](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)