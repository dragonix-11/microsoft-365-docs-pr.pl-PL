---
title: Używanie współdziałania Microsoft OneDrive Edukacja Tools
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
description: Twórz i ocenij zadania, twórz zawartość kursu i dopracuj jej zawartość oraz współpracuj nad plikami w czasie rzeczywistym za pomocą nowej aplikacji do współdziałania narzędzi programu Microsoft OneDrive Edukacja Tools.
ms.openlocfilehash: 68622305e6a277b44538d4a05ee42a6b680749f3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021233"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Integracja Microsoft OneDrive LTI z systemami Canvas

Integracja Microsoft OneDrive LTI z usługą Canvas jest procesem dwuetapowym. Pierwszy krok umożliwia korzystanie Microsoft OneDrive Canvas, a drugi krok umożliwia Microsoft OneDrive LTI w ramach kursów programu Canvas.

## <a name="recommended-browser-settings"></a>Zalecane ustawienia przeglądarki

- Pliki cookie powinny być włączone dla Microsoft OneDrive.
- Wyskakujące okienka nie powinny być blokowane przez Microsoft OneDrive.

> [!NOTE]
> - W trybie incognito przeglądarki Chrome pliki cookie nie są domyślnie włączone i należy je włączyć.
> - Microsoft OneDrive lti działa w trybie prywatnym w Microsoft Edge przeglądarce. Upewnij się, że pliki cookie nie zostały zablokowane (które są domyślnie włączone).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Włączanie Microsoft OneDrive LTI w płótnie

> [!IMPORTANT]
> Osoba, która wykonuje tę integrację, powinna być administratorem systemu Canvas i administratorem Microsoft 365 dzierżawy.

1. Logowanie się do <a href="https://onedrivelti.microsoft.com/admin" target="_blank">portalu Microsoft OneDrive LTI</a>
1. Wybierz przycisk **Zgoda administratora** i zaakceptuj te uprawnienia.

> [!CAUTION]
> Jeśli ten krok nie zostanie wykonany, poniższy krok spowoduje błąd i nie będzie można go wykonać przez godzinę, gdy błąd wystąpi.

3. Wybierz przycisk **Create new LTI Tenant (Utwórz nową dzierżawę LTI** ). Na stronie LtI Registration (Rejestracja LTI) wybierz z listy rozwijanej pozycję **Canvas** i wprowadź podstawowy adres URL wystąpienia canvas.

> [!NOTE]
> Jeśli wystąpienie kanwy to na przykład https://contoso.test.instructure.com](https://contoso.test.instructure.com), należy wprowadzić pełny adres URL.

:::image type="content" source="media/OneDrive-LTI-07.png" alt-text="Strona administracji dzierżawy LTI z polem rozwijaym do wyboru platformy lti dla klientów konsumenckich i pola tekstowego adresu URL.":::

4. Skopiuj JSON, wybierając przycisk **Kopiuj** (ikonę po prawej stronie, która pokazuje dwie strony na siebie). Zostanie on użyty do wygenerowania klucza w płótnie.

:::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Obraz przedstawiający przycisk Kopiuj, który skopiuje wyświetlany tekst JSON i udostępni go dla generowania klucza w kanwie.":::

5. Zaloguj się jako administrator do wystąpienia kanwy i wybierz pozycję **Klucze** dewelopera z menu w lewej części strony. Z listy rozwijanej utwórz klucz dewelopera, wybierając klawisz **LTI** z listy rozwijanej w prawym górnym rogu strony.

:::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Zrzut ekranu przedstawiający pasek nawigacyjny po lewej stronie z wybranymi klawiszami dewelopera oraz wpis klucza LTI wybrany z listy rozwijanej po prawej stronie.":::

6. Na stronie Konfigurowanie z listy rozwijanej **Method** (Metoda) wybierz pozycję **Paste JSON (Wklej JSON** ) jako metodę i wklej tekst JSON skopiowany w kroku 4 w wyświetlonym polu tekstowym.

    > [!TIP]
    > **Krok opcjonalny:** Jeśli nauczyciele w Twojej szkole chcą kontrolować, które linki są wyświetlane w nawigacji po kursach, ``default`` możesz zmodyfikować parametr w skopiowanym JSON. Parametr ``default`` jest ustawiany automatycznie ``enabled`` , jednak zmiana tego parametru umożliwia ``default`` ``disabled`` nauczycielom wybieranie nawigacji po własnych kursach.
    >
    > Aby uzyskać więcej informacji na temat sposobu, w jaki nauczyciele mogą modyfikować linki nawigacji po kursie, zobacz Jak [zarządzać linkami nawigacji po kursach?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Zapisz klucz, a stanie się on dostępny w obszarze Canvas w **stanie Wyłączony** . Włącz **i skopiuj klawisz** podany w kolumnie **Szczegóły** , który ma zostać użyty w następnym kroku.

:::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Strona Kanwa z klawiszem ustawionym w stanie wyłączenia. Klucz musi być włączony, a klucz musi zostać skopiowany z kolumny szczegóły na tej stronie.":::

8. Wróć do portalu Microsoft OneDrive lti Registration (Rejestracja LTI) i wklej klucz w polu **Identyfikator klienta systemu Canvas**. Gdy **wszystko** będzie gotowe, wybierz pozycję Dalej.

:::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Strona rejestracji dzierżawy LTI z tekstem JSON i polem tekstowym, do którego należy skopiować klucz.":::

9. Przejrzyj i zapisz zmiany. Po pomyślnej rejestracji zostanie wyświetlony komunikat.
10. Szczegóły rejestracji można również przejrzeć, wybierając przycisk Wyświetl dzierżawy **LTI** na stronie głównej.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Włączanie Microsoft OneDrive LTI na kursach Canvas

Administrator systemu Canvas może włączyć Microsoft OneDrive LTI dla wszystkich kursów. Jeśli Microsoft OneDrive ltI jest potrzebna w ramach określonego kursu (a nie wszystkich kursów), nauczyciel musi wykonać te same kroki w ramach ustawień kursu.

1. Zaloguj się jako administrator i przejdź **do sekcji Ustawienia** konta.
2. Przejdź do sekcji **Aplikacje** i wybierz przycisk **Wyświetl konfiguracje** aplikacji.
3. Wybierz przycisk **Dodaj aplikację** .
4. Z listy **rozwijanej Typ** konfiguracji wybierz opcję **Według identyfikatora** klienta.
5. Wklej wartość klucza dewelopera wygenerowanego wcześniej w polu **Identyfikator klienta** i wybierz **przycisk** Prześlij.

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Strona dodawanie aplikacji z opcją Według identyfikatora klienta w menu rozwijaym Typ konfiguracji.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Collaboration Ustawienia for Microsoft OneDrive LTI in Canvas Courses

> [!NOTE]
> Aby współpracować z nauczycielami i uczniami, nie należy włączać ustawienia współpracy. Aby upewnić się, że to ustawienie nie jest włączone, wykonaj poniższe czynności.

1. Zaloguj się jako administrator i przejdź **do sekcji Ustawienia** administratorów.
1. Przejdź do **sekcji Opcje funkcji** , a następnie przejdź do **sekcji Kurs** .
1. Ustaw, **aby funkcja narzędzia Współpraca zewnętrzna** nie była włączona.

> [!NOTE]
> Współpracę można przypisywać poszczególnym uczniom i grupom uczniów. Domyślnie przypisz do poszczególnych uczniów. Aby przypisać współpracę do grupy uczniów, wykonaj następujące czynności:

1. Zaloguj się jako administrator i przejdź do sekcji **Klucze dewelopera** .
1. Znajdź klucz z wartością 170000000000710 i ustaw dla niego wartość **Wł**.
