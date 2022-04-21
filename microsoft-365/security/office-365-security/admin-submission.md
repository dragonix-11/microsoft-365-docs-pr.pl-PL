---
title: Zarządzanie przesyłaniem
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak używać portalu Przesyłania w portalu Microsoft 365 Defender do przesyłania podejrzanych wiadomości e-mail, podejrzanych wiadomości phishingowych, spamu i innych potencjalnie szkodliwych wiadomości, adresów URL i załączników wiadomości e-mail do firmy Microsoft w celu ponownego skanowania.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a21c9e6655c01e2d2229e957f79b2342895ac4e4
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971974"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Przesyłanie do firmy Microsoft podejrzanych wiadomości spamowych, adresów URL i plików przy użyciu portalu Przesyłania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

W Microsoft 365 organizacjach ze skrzynkami pocztowymi Exchange Online administratorzy mogą przesyłać wiadomości e-mail, adresy URL i załączniki do firmy Microsoft za pomocą portalu Przesyłania w portalu Microsoft 365 Defender w celu przesyłania wiadomości e-mail, adresów URL i załączników do firmy Microsoft w celu skanowania.

Po przesłaniu wiadomości e-mail do analizy otrzymasz:

- **Sprawdzanie uwierzytelniania za pomocą poczty e-mail**: szczegółowe informacje na temat tego, czy uwierzytelnianie poczty e-mail zostało zakończone pomyślnie, czy też nie powiodło się, gdy zostało dostarczone.
- **Trafienia zasad**: informacje o zasadach, które mogły zezwalać na przychodzące wiadomości e-mail lub blokować je w dzierżawie, zastępując nasze werdykty dotyczące filtru usługi.
- **Reputacja ładunku/detonacja**: aktualne badanie wszelkich adresów URL i załączników w wiadomości.
- **Analiza równiarki**: przejrzyj wyniki wykonywane przez klasyfikatorów ludzkich w celu potwierdzenia, czy komunikaty są złośliwe.

> [!IMPORTANT]
> Analiza reputacji ładunku/detonacji i równiarki nie jest wykonywana we wszystkich dzierżawach. Dostęp informacji poza organizację jest blokowany, gdy dane nie powinny opuszczać granicy dzierżawy w celach zgodności.

Aby uzyskać inne sposoby przesyłania wiadomości e-mail, adresów URL i załączników do firmy Microsoft, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com/>. Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

- Aby przesłać komunikaty i pliki do firmy Microsoft, musisz mieć jedną z następujących ról:
  - **Administrator zabezpieczeń** lub **czytelnik zabezpieczeń** w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

    Należy pamiętać, że jedna z tych ról jest wymagana do [wyświetlenia przesyłania użytkowników do niestandardowej skrzynki pocztowej](#view-user-submissions-to-microsoft) zgodnie z opisem w dalszej części tego artykułu.

- Administratorzy mogą przesyłać wiadomości w ciągu 30 dni, jeśli są nadal dostępne w skrzynce pocztowej i nie są usuwane przez użytkownika lub innego administratora.

- Przesyłanie przez administratora jest ograniczane według następujących stawek:
  - Maksymalna liczba przesłanych zgłoszeń w dowolnym okresie 15 minut: 150 przesłanych
  - Te same zgłoszenia w 24-godzinnym okresie: 3 przesłania
  - Te same zgłoszenia w okresie 15 minut: 1 przesyłanie

- Aby uzyskać więcej informacji na temat sposobu przesyłania wiadomości i plików do firmy Microsoft, zobacz [Raport wiadomości i pliki do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Zgłaszanie podejrzanej zawartości firmie Microsoft

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Przesłane** w **akcji & przesłanych.** \> Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** sprawdź, czy wybrano kartę **Wiadomości e-mail**, **Załączniki lub adresy URL wiadomości e-mail** na podstawie typu zawartości, którą chcesz zgłosić, a następnie kliknij ikonę  ![Prześlij do firmy Microsoft w celu analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Użyj wysuwanego **polecenia Prześlij do firmy Microsoft w celu analizy** , który wygląda na przesłany odpowiedni typ zawartości (wiadomość e-mail, adres URL lub załącznik wiadomości e-mail), zgodnie z opisem w poniższych sekcjach.

   > [!NOTE]
   > Przesyłanie plików i adresów URL nie jest dostępne w chmurach, które nie zezwalają na opuszczenie środowiska przez dane. Możliwość wybrania pozycji Plik lub adres URL zostanie wyszarzone.

### <a name="notify-users-from-within-the-portal"></a>Powiadamianie użytkowników z poziomu portalu

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Przesłane** w witrynie Email & collaboration **Submissions (Przesyłanie** **w ramach współpracy** \> & poczty e-mail). Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** wybierz kartę **Komunikaty zgłaszane przez użytkownika** , a następnie wybierz komunikat, który chcesz oznaczyć i powiadomić.

3. Wybierz listę rozwijaną **Oznacz jako i powiadom** , a następnie wybierz pozycję **Nie znaleziono** \> zagrożeń **wyłudzających informacje** lub **wiadomości-śmieci**.

   :::image type="content" source="../../media/unified-submission-user-reported-message.png" alt-text="Strona Przesłane" lightbox="../../media/unified-submission-user-reported-message.png":::

Zgłoszona wiadomość zostanie oznaczona jako fałszywie dodatnia lub fałszywie ujemna. Powiadomienie e-mail jest wysyłane automatycznie z poziomu portalu do użytkownika, który zgłosił wiadomość.

### <a name="submit-a-questionable-email-to-microsoft"></a>Przesyłanie wątpliwej wiadomości e-mail do firmy Microsoft

1. W polu **Wybierz typ przesyłania** sprawdź, czy na liście rozwijanej **wybrano pozycję Poczta e-mail** .

2. W sekcji **Dodawanie identyfikatora komunikatu sieciowego lub przekazywanie pliku wiadomości e-mail** użyj jednej z następujących opcji:
   - **Dodaj identyfikator wiadomości sieciowej poczty e-mail**: jest to wartość identyfikatora GUID dostępna w nagłówku **X-MS-Exchange-Organization-Network-Message-Id** w wiadomości lub w nagłówku **X-MS-Office365-Filtering-Correlation-Id** w komunikatach poddanych kwarantannie.
   - **Upload pliku e-mail (msg lub .eml)**: kliknij przycisk **Przeglądaj pliki**. W otwartym oknie dialogowym znajdź i wybierz plik .eml lub msg, a następnie kliknij przycisk **Otwórz**.

3. W polu **Wybierz adresata, który miał problem** , określ adresata, dla któremu chcesz uruchomić sprawdzanie zasad. Sprawdzanie zasad określi, czy wiadomość e-mail pominąła skanowanie z powodu zasad użytkownika lub organizacji.

4. W sekcji **Wybieranie przyczyny przesłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - **Powinna zostać zablokowana (fałszywie ujemna)**: W **wyświetlonej sekcji Wiadomość e-mail powinna zostać sklasyfikowana jako** jedna z następujących wartości (jeśli nie masz pewności, użyj najlepszej oceny):
     - **Phish**
     - **Złośliwego oprogramowania**
     - **Spam**

5. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-flyout-email.png" alt-text="Proces przesyłania nowego adresu URL" lightbox="../../media/submission-flyout-email.png":::

### <a name="send-a-suspect-url-to-microsoft"></a>Wysyłanie podejrzanego adresu URL do firmy Microsoft

1. W polu **Wybierz typ przesyłania** wybierz pozycję **Adres URL** z listy rozwijanej.

2. W wyświetlonym polu **adresu URL** wprowadź pełny adres URL (na przykład `https://www.fabrikam.com/marketing.html`).

3. W sekcji **Wybieranie przyczyny przesłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - **Powinna zostać zablokowana (fałszywie ujemna)**: W **wyświetlonej sekcji Ten adres URL powinien zostać sklasyfikowany jako** jedna z następujących wartości (jeśli nie masz pewności, użyj najlepszej oceny):
     - **Phish**
     - **Złośliwego oprogramowania**

4. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-url-flyout.png" alt-text="Proces przesyłania nowej wiadomości e-mail" lightbox="../../media/submission-url-flyout.png":::

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Przesyłanie podejrzanego załącznika wiadomości e-mail do firmy Microsoft

1. W polu **Wybierz typ przesyłania** wybierz pozycję **Załącznik wiadomości e-mail** z listy rozwijanej.

2. W wyświetlonej sekcji **Plik** kliknij pozycję **Przeglądaj pliki**. W otwartym oknie dialogowym znajdź i wybierz plik, a następnie kliknij przycisk **Otwórz**.

3. W sekcji **Wybieranie przyczyny przesłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - **Powinna zostać zablokowana (fałszywie ujemna)**: W **wyświetlonej sekcji Ten plik powinien zostać sklasyfikowany jako** jedna z następujących wartości (jeśli nie masz pewności, użyj najlepszej oceny):
     - **Phish**
     - **Złośliwego oprogramowania**

4. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-file-flyout.png" alt-text="Proces przesyłania nowego załącznika" lightbox="../../media/submission-file-flyout.png":::

> [!NOTE]
> Jeśli filtrowanie złośliwego oprogramowania zastąpiło załączniki wiadomości plikiem alertu o złośliwym oprogramowaniu Text.txt, należy przesłać oryginalny komunikat z kwarantanny zawierającej oryginalne załączniki. Aby uzyskać więcej informacji na temat kwarantanny i sposobu wydawania komunikatów ze złośliwym oprogramowaniem fałszywie dodatnim, zobacz [Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator](manage-quarantined-messages-and-files.md).

## <a name="view-admin-submissions-to-microsoft"></a>Wyświetlanie przesyłania przez administratora do firmy Microsoft

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Przesłane** w **akcji & przesłanych.** \> Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** sprawdź, czy wybrano kartę **Wiadomości e-mail**, **Adres URL** lub **Załącznik wiadomości e-mail** .

   - Wpisy można sortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby wyświetlić maksymalnie siedem kolumn. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):
     - **Nazwa przesyłania**<sup>\*</sup>
     - **Nadawcy**<sup>\*</sup>
     - **Odbiorcy**
     - **Data przesłania**<sup>\*</sup>
     - **Powód przesłania**<sup>\*</sup>
     - **Stan**<sup>\*</sup>
     - **Wynik**<sup>\*</sup>
     - **Filtrowanie werdyktu**
     - **Przyczyna dostarczania/blokowania**
     - **Identyfikator przesyłania**
     - **Identyfikator komunikatu sieci/identyfikator obiektu**
     - **Kierunek**
     - **Adres IP nadawcy**
     - **Poziom zgodności zbiorczej (BCL)**
     - **Destination (Miejsce docelowe)**
     - **Akcja zasad**
     - **Przesłane przez**
     - **Symulacja phish**
     - **Tagi**<sup>\*</sup>
     - **Zezwalaj**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/admin-submission-customize-columns.png" alt-text="Opcje nowej kolumny Dostosowywanie dla przesyłania przez administratora" lightbox="../../media/admin-submission-customize-columns.png":::

   - Aby filtrować wpisy, kliknij pozycję **Filtruj**. Dostępne filtry to:
     - **Przesłana data**: **data rozpoczęcia** i **data zakończenia**.
     - **Identyfikator przesyłania**: wartość identyfikatora GUID przypisana do każdego przesłania.
     - **Identyfikator komunikatu sieci**
     - **Nadawcy**
     - **Odbiorcy**
     - **Nazwa**
     - **Przesłane przez**
     - **Powód przesłania**
     - **Stan**
     - **Tagi**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/admin-submission-filters.png" alt-text="Opcje nowego filtru dla przesłanych przez administratorów" lightbox="../../media/admin-submission-filters.png":::

   - Aby pogrupować wpisy, kliknij pozycję **Grupuj** i wybierz jedną z następujących wartości z listy rozwijanej:
     - **Brak**
     - **Type**
     - **Powodu**
     - **Stan**
     - **Result (Wynik)**
     - **Tagi**

   - Aby wyeksportować wpisy, kliknij pozycję **Eksportuj**. W wyświetlonym oknie dialogowym zapisz plik .csv.

### <a name="admin-submission-result-details"></a>Szczegóły wyników przesyłania przez administratora

Komunikaty przesyłane w przesłanych przez administratorów plikach są przeglądane, a wyniki wyświetlane w wysuwnym oknie wysuwnym szczegółów przesyłania:

- Jeśli wystąpił błąd w uwierzytelnianiu wiadomości e-mail nadawcy w czasie dostarczania.
- Informacje na temat wskazówek dotyczących zasad, które mogły wpłynąć na werdykt wiadomości lub go pominąć.
- Bieżące wyniki detonacji, aby sprawdzić, czy adresy URL lub pliki zawarte w wiadomości były złośliwe.
- Opinie od równiarki.

Jeśli znaleziono przesłonięcia, wynik powinien być dostępny w ciągu kilku minut. Jeśli nie wystąpił problem podczas uwierzytelniania lub dostarczania wiadomości e-mail, przesłonięcie nie miało wpływu, opinie od równiarki mogą potrwać nawet jeden dzień.

## <a name="view-user-submissions-to-microsoft"></a>Wyświetlanie przesyłania użytkowników do firmy Microsoft

Jeśli wdrożono [dodatek Komunikat raportu](enable-the-report-message-add-in.md), [dodatek wyłudzanie informacji o raportach](enable-the-report-phish-add-in.md) lub osoby korzystające z [wbudowanego raportowania w Outlook w sieci Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), możesz zobaczyć, co użytkownicy zgłaszają na karcie **Komunikat zgłoszony przez użytkownika**.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Przesłane** w **akcji & przesłanych.** \> Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** wybierz kartę **Komunikaty zgłaszane przez użytkownika** .

   - Wpisy można sortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby wyświetlić opcje. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

     - **Temat wiadomości e-mail**<sup>\*</sup>
     - **Zgłoszone przez**<sup>\*</sup>
     - **Data zgłoszenia**<sup>\*</sup>
     - **Nadawcy**<sup>\*</sup>
     - **Zgłoszona przyczyna**<sup>\*</sup>
     - **Wynik**<sup>\*</sup>
     - **Identyfikator zgłoszonych komunikatów**
     - **Identyfikator komunikatu sieci**
     - **Adres IP nadawcy**
     - **Raportowane z**
     - **Symulacja phish**
     - **Przekonwertowane na przesyłanie przez administratora**
     - **Tagi**<sup>\*</sup>
     - **Oznaczone jako**<sup>\*</sup>
     - **Oznaczone przez**
     - **Data oznaczona**

     Po zakończeniu kliknij przycisk **Zastosuj**.

   - Aby filtrować wpisy, kliknij pozycję **Filtruj**. Dostępne filtry to:
     - **Data zgłoszenia**: **data rozpoczęcia** i **data zakończenia**.
     - **Zgłoszone przez**
     - **Temat wiadomości e-mail**
     - **Identyfikator zgłoszonych komunikatów**
     - **Identyfikator komunikatu sieci**
     - **Nadawcy**
     - **Zgłoszony powód**: **Nie śmieci**, **Phish** lub **Spam**
     - **Zgłoszone z**: **dodatek firmy Microsoft** lub **dodatek innej firmy**
     - **Symulacja phish**: **Tak** lub **Nie**
     - **Przekonwertowane na przesyłanie przez administratora**: **Tak** lub **Nie**
     - **Tagi**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/admin-submission-reported-messages.png" alt-text="Opcje nowego filtru dla przesyłanych przez użytkowników" lightbox="../../media/admin-submission-reported-messages.png":::

   - Aby pogrupować wpisy, kliknij pozycję **Grupuj** i wybierz jedną z następujących wartości z listy rozwijanej:
     - **Brak**
     - **Powodu**
     - **Nadawcy**
     - **Zgłoszone przez**
     - **Result (Wynik)**
     - **Raportowane z**
     - **Symulacja phish**
     - **Przekonwertowane na przesyłanie przez administratora**
     - **Tagi**

   - Aby wyeksportować wpisy, kliknij pozycję **Eksportuj**. W wyświetlonym oknie dialogowym zapisz plik .csv.

> [!NOTE]
> Jeśli organizacje są skonfigurowane do wysyłania wiadomości zgłoszonych przez użytkownika tylko do niestandardowej skrzynki pocztowej, zgłoszone wiadomości nie zostaną wysłane do ponownego przeskanowania, a wyniki w **wiadomościach zgłoszonych przez użytkownika** będą zawsze puste.

### <a name="undo-user-submissions"></a>Cofanie przesyłania przez użytkownika

Gdy użytkownik prześle podejrzaną wiadomość e-mail do niestandardowej skrzynki pocztowej, użytkownik i administrator nie będą mogli cofnąć przesyłania. Jeśli użytkownik chce odzyskać wiadomość e-mail, będzie on dostępny do odzyskania w folderach Elementy usunięte lub Wiadomości-śmieci.

### <a name="converting-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Konwertowanie wiadomości zgłoszonych przez użytkownika z niestandardowej skrzynki pocztowej na przesyłanie przez administratora

Jeśli niestandardowa skrzynka pocztowa została skonfigurowana do przechwytywania wiadomości zgłoszonych przez użytkowników bez wysyłania wiadomości do firmy Microsoft, możesz znaleźć i wysłać określone wiadomości do firmy Microsoft w celu analizy.

Na karcie **Komunikaty zgłaszane przez użytkownika** wybierz komunikat z listy, kliknij pozycję **Prześlij do firmy Microsoft do analizy**, a następnie wybierz jedną z następujących wartości z listy rozwijanej:

- **Raport jest czysty**
- **Zgłaszanie wyłudzania informacji**
- **Zgłaszanie złośliwego oprogramowania**
- **Zgłaszanie spamu**
- **Badanie wyzwalacza**

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/admin-submission-main-action-button.png" alt-text="Przycisk Nowe opcje na przycisku Akcja" lightbox="../../media/admin-submission-main-action-button.png":::
