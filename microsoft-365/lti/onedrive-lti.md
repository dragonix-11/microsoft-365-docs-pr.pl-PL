---
title: Integracja Microsoft OneDrive LTI z kanwą
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Twórz i oceniaj przypisania, twórz i kuratoruj zawartość kursu oraz współpracuj nad plikami w czasie rzeczywistym przy użyciu nowej aplikacji Microsoft OneDrive Edukacja Tools Interoperability App for Canvas.
ms.openlocfilehash: 8a4e3a1fc1b1d19bed093d5e72bf66e1afb2f591
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285571"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Integracja Microsoft OneDrive LTI z kanwą

Ten artykuł jest przeznaczony dla edukacyjnych administratorów IT, którzy muszą skonfigurować Microsoft OneDrive LTI for Canvas.

Aby uzyskać instrukcje dla nauczycieli dotyczące korzystania z OneDrive LTI w kanwie, zobacz [Korzystanie z Microsoft OneDrive z usługą LMS](https://support.microsoft.com/topic/use-microsoft-onedrive-with-your-lms-c2ddeb48-f695-4267-94f2-14f7ff1b7bdd).

Integracja Microsoft OneDrive LTI z kanwą to proces dwuetapowy. Pierwszy krok umożliwia Microsoft OneDrive w kanwie, a drugi sprawia, że Microsoft OneDrive LTI jest dostępny w ramach kursów kanwy.

## <a name="recommended-browser-settings"></a>Zalecane ustawienia przeglądarki

- Pliki cookie powinny być włączone dla Microsoft OneDrive.
- Wyskakujące okienka nie powinny być blokowane dla Microsoft OneDrive.

> [!NOTE]
>
> - Pliki cookie nie są domyślnie włączone w trybie incognito przeglądarki Chrome i muszą być włączone.
> - Microsoft OneDrive LTI działa w trybie prywatnym w przeglądarce Microsoft Edge. Upewnij się, że nie zablokowano plików cookie (które są domyślnie włączone).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Włączanie Microsoft OneDrive LTI na kanwie

> [!IMPORTANT]
> Osoba, która wykonuje tę integrację, powinna być administratorem aplikacji Canvas i administratorem dzierżawy Microsoft 365.

1. Zaloguj się do <a href="https://onedrivelti.microsoft.com/admin" target="_blank">portalu rejestracji Microsoft OneDrive LTI</a>
2. Wybierz przycisk **Zgoda administratora** i zaakceptuj uprawnienia.

   > [!CAUTION]
   > Jeśli ten krok nie zostanie wykonany, poniższy krok spowoduje wyświetlenie błędu i nie będzie można wykonać tego kroku przez godzinę po wystąpieniu błędu.

3. Wybierz przycisk **Utwórz nową dzierżawę LTI** . Na stronie Rejestracja LTI wybierz pozycję **Kanwa** na liście rozwijanej i wprowadź podstawowy adres URL wystąpienia kanwy.

   > [!NOTE]
   > Jeśli na przykład `https://contoso.test.instructure.com`wystąpienie kanwy to , należy wprowadzić pełny adres URL.

   :::image type="content" source="media/OneDrive-LTI-07.png" alt-text="Strona administrowania dzierżawą LTI z polem listy rozwijanej umożliwiającym wybranie platformy konsumenta LTI i pola tekstowego adresu URL.":::

4. Skopiuj kod JSON, wybierając przycisk **Kopiuj** (ikona po prawej stronie, która pokazuje dwie strony na górze). Zostanie on użyty do wygenerowania klucza w kanwie.

   :::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Obraz przedstawiający przycisk kopiowania, który skopiuje wyświetlany tekst JSON i udostępni go do generowania kluczy w kanwie.":::

5. Zaloguj się do wystąpienia kanwy jako administrator i wybierz pozycję **Klucze deweloperów** z menu po lewej stronie. Z listy rozwijanej utwórz klucz dewelopera, wybierając pozycję **KLUCZ LTI** z listy rozwijanej w prawym górnym rogu strony.

   :::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Zrzut ekranu przedstawiający lewy pasek nawigacyjny z wybranymi kluczami deweloperów oraz wpis klucza LTI wybrany z listy rozwijanej po prawej stronie.":::

6. Na stronie Konfigurowanie na liście rozwijanej **Metoda** wybierz pozycję **Wklej kod JSON** jako metodę i wklej tekst JSON skopiowany w kroku 4 w wyświetlonym polu tekstowym.

    > [!TIP]
    > **Krok opcjonalny:** Jeśli nauczyciele w twojej szkole chcą samodzielnie kontrolować, które linki pojawiają się w nawigacji kursów, możesz zmodyfikować ``default`` parametr w skopiowanym formacie JSON. Parametr ``default`` jest ustawiany ``enabled`` automatycznie, jednak zmiana parametru ``default`` ``disabled`` umożliwia nauczycielom wybór nawigacji po kursach.
    >
    > Aby uzyskać więcej informacji na temat sposobu modyfikowania linków nawigacyjnych kursów przez nauczycieli, zobacz [Jak mogę zarządzanie linkami nawigacji po kursach?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Zapisz klucz i stanie się on dostępny na kanwie w stanie **Wyłączone** . Włącz **klucz i** skopiuj klucz podany w kolumnie **Szczegóły** do użycia w następnym kroku.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Strona Kanwa z kluczem ustawionym w stanie wyłączenia. Należy ją włączyć, a klucz będzie musiał zostać skopiowany z kolumny szczegółów na tej stronie.":::

8. Wróć do portalu rejestracji Microsoft OneDrive LTI i wklej klucz w polu **Identyfikator klienta kanwy**. Wybierz pozycję **Dalej** , gdy wszystko będzie gotowe.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Strona rejestracji dzierżawy LTI, na której jest wyświetlany tekst JSON i pole tekstowe, do którego należy skopiować klucz.":::

9. Przejrzyj i zapisz zmiany. Po pomyślnej rejestracji zostanie wyświetlony komunikat.

10. Szczegóły rejestracji można również przejrzeć, wybierając przycisk **Wyświetl dzierżawy LTI** na stronie głównej.

Przyszłe wersje mogą wymagać dodatkowej zgody administratora. W takich przypadkach należy powtórzyć tylko kroki 1 i 2.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Włączanie Microsoft OneDrive LTI na kursach kanwy

Administrator kanwy może włączyć Microsoft OneDrive LTI dla wszystkich kursów. Jeśli Microsoft OneDrive LTI jest potrzebne w określonym kursie (a nie we wszystkich kursach), nauczyciel kursu musi wykonać te same kroki w ustawieniach kursu.

1. Zaloguj się jako administrator i przejdź do sekcji **Ustawienia**.
2. Przejdź do sekcji **Aplikacje** i wybierz przycisk **Wyświetl konfiguracje aplikacji** .
3. Wybierz przycisk **Dodaj aplikację** .
4. Na liście rozwijanej **Typ konfiguracji** wybierz **opcję Według identyfikatora klienta** .
5. Wklej wartość klucza dewelopera wygenerowanego wcześniej w polu **Identyfikator klienta** i wybierz przycisk **Prześlij** .

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Strona dodawania aplikacji z opcją Według identyfikatora klienta w menu rozwijanego Typ konfiguracji.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Współpraca Ustawienia dla Microsoft OneDrive LTI na kursach kanwy

> [!NOTE]
> Aby współpraca działała dla nauczycieli i uczniów, nie należy włączać ustawienia współpracy. Aby upewnić się, że ustawienie nie jest włączone, wykonaj poniższe kroki.

1. Zaloguj się jako administrator i przejdź do sekcji **Ustawienia**.
1. Przejdź do sekcji **Opcje funkcji** , a następnie przejdź do sekcji **Kurs** .
1. Ustaw funkcję **Narzędzia do współpracy zewnętrznej** , aby nie była włączona.

> [!NOTE]
> Współpraca może być przypisana do poszczególnych uczniów i grup uczniów. Przypisywanie do poszczególnych uczniów działa domyślnie. Aby móc przypisać współpracę do grupy uczniów, wykonaj następujące kroki:

1. Zaloguj się jako administrator i przejdź do sekcji **Klucze deweloperów** .
1. Znajdź klucz z wartością 170000000000710 i ustaw go na **wartość Włączone**.
