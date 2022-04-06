---
title: Zarządzanie przesłaniami
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
description: Administratorzy mogą dowiedzieć się, jak za pomocą portalu Przesyłanie w portalu Microsoft 365 Defender przesyłać podejrzane wiadomości e-mail, podejrzewane wiadomości wyłudzające informacje, spam i inne potencjalnie niebezpieczne wiadomości, adresy URL i załączniki wiadomości e-mail do firmy Microsoft w celu ponownego skanowania.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 34d608a6ea114fff8005069f3dc2ddc79c4be45e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682642"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Korzystanie z portalu Przesyłanie w celu przesyłania podejrzanych wiadomości-śmieci, wyłudków, adresów URL i plików do firmy Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)


W Microsoft 365 organizacji ze skrzynkami pocztowymi usługi Exchange Online administratorzy mogą za pomocą portalu Przesyłanie w portalu Microsoft 365 Defender wysyłać wiadomości e-mail, adresy URL i załączniki do firmy Microsoft w celu skanowania.

Gdy przesyłasz wiadomość e-mail do analizy, otrzymasz:

- **Sprawdzanie uwierzytelniania wiadomości e-mail**: Szczegóły dotyczące tego, czy uwierzytelnianie poczty e-mail zakończyło się pomyślnie, czy nie po jego dostarczyć.
- **Trafienia zasad**: Informacje o wszelkich zasadach, które mogły zezwolić lub zablokować przychodzącą pocztę e-mail w dzierżawie, zastępując nasze werdykty filtru usługi.
- **Reputacja/detonacja** ładowania: Aktualne informacje o adresach URL i załącznikach w wiadomości.
- **Analiza gradera**: przejrzyj wykonane przez ocenionych przez ludzkich klasyfikatorów, aby sprawdzić, czy wiadomości są złośliwe.

> [!IMPORTANT]
> Analiza reputacji/detonacji obciążenia i oceny nie jest wykonywana we wszystkich dzierżawach. Dostęp do informacji poza organizację jest blokowany, gdy dane nie powinny opuszczać granicy dzierżawy w celu zachowania zgodności z przepisami.

Aby uzyskać inne sposoby przesyłania wiadomości e-mail, adresów URL i załączników do firmy Microsoft, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com/>. Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

- Aby przesłać wiadomości i pliki do firmy Microsoft, musisz mieć jedną z następujących ról:
  - **Administrator zabezpieczeń** lub **czytnik zabezpieczeń** w [portalu Microsoft 365 Defender sieci.](permissions-microsoft-365-security-center.md)
  
    Jedna z tych ról jest wymagana [do wyświetlania](#view-user-submissions-to-microsoft) przesyłania użytkowników do niestandardowej skrzynki pocztowej w sposób opisany w dalszej części tego artykułu.

- Administratorzy mogą przesyłać wiadomości w wieku do 30 dni, jeśli są nadal dostępne w skrzynce pocztowej i nie są czyszowane przez użytkownika ani innego administratora.

- Zgłoszenia administratorów są ograniczane zgodnie z następującymi stawkami:
  - Maksymalna liczba przesyłania w dowolnym okresie 15 minut: 150 przesyłania
  - Te same zgłoszenia w okresie 24-godzinnym: 3 zgłoszenia
  - Te same zgłoszenia w okresie 15 minut: 1 przesłanie
  
- Aby uzyskać więcej informacji o tym, jak użytkownicy mogą przesyłać wiadomości i pliki do firmy Microsoft, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Zgłaszanie podejrzanej zawartości firmie Microsoft

1. W portalu Microsoft 365 Defender pod stroną <https://security.microsoft.com>, przejdź do strony **Przesyłanie** w witrynie **Akcje & przesyłania** \> **.** Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na **stronie Materiały sprawdź**, czy wybrano kartę Adresy  e-mail lub adresy **URL** w zależności od typu zawartości, którą chcesz zgłosić, ![a następnie kliknij ikonę Prześlij do firmy Microsoft w celu analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Użyj **wysuwanej listy** wysuwanej Submit to Microsoft for analysis (Prześlij do firmy Microsoft w celu zgłoszenia odpowiedniego typu zawartości (wiadomości e-mail, adresu URL lub załącznika wiadomości e-mail) zgodnie z opisem w poniższych sekcjach.

   > [!NOTE]
   > Przesyłanie plików i adresów URL nie jest dostępne w chmurach, które nie zezwalają na opuszczenie środowiska przez dane. Możliwość wybrania opcji Plik lub Adres URL będzie wyszowana.

### <a name="notify-users-from-within-the-portal"></a>Powiadamianie użytkowników z poziomu portalu

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do strony **Przesyłanie w witrynie** e-mail **& Przesyłanie** \> **.** Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Materiały wybierz** kartę Użytkownik zgłosił **wiadomości** , a następnie wybierz wiadomość, którą chcesz oznaczyć i powiadomić.

3. Wybierz menu **rozwijane Oznacz jako i powiadom** , a następnie **wybierz pozycję** \> Nie znaleziono zagrożeń **wyłudzających informacje** lub **Wiadomości-śmieci**.

   :::image type="content" alt-text="Wysyłanie wiadomości z portalu." source="../../media/unified-submission-user-reported-message.png" lightbox="../../media/unified-submission-user-reported-message.png":::

Zgłoszony komunikat zostanie oznaczony jako wynik fałszywie dodatni lub ujemny. Powiadomienie e-mail jest wysyłane automatycznie z portalu do użytkownika, który zgłosił wiadomość.

### <a name="submit-a-questionable-email-to-microsoft"></a>Przesyłanie pytanie do firmy Microsoft w wiadomości e-mail

1. W polu **Wybierz typ przesyłania** sprawdź, czy na liście  rozwijanej wybrano pozycję Poczta e-mail.

2. W sekcji **Dodawanie identyfikatora wiadomości sieciowej lub przekazywanie pliku poczty e-mail** użyj jednej z następujących opcji:
   - Dodawanie identyfikatora wiadomości sieciowej poczty e-mail **: Jest** to wartość GUID, która jest dostępna w nagłówku **identyfikatora X-MS-Exchange-Organization-Network-Message-Id** w wiadomości lub w nagłówku **identyfikatora X-MS-Office365-Filtering-Correlation-Id** w wiadomościach poddanych kwarantannie.
   - **Upload plik poczty e-mail (msg lub eml)**: Kliknij **pozycję Przeglądaj pliki**. W otwartym oknie dialogowym znajdź i zaznacz plik eml lub msg, a następnie kliknij przycisk **Otwórz**.

3. W **polu Wybierz adresata** , który miał problem, określ adresata, dla kogo chcesz uruchomić sprawdzanie zasad. Sprawdzanie zasad określa, czy wiadomość e-mail nie jest skanowana ze względu na zasady użytkowników lub organizacji.

4. W **sekcji Wybierz przyczynę przesyłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - Powinna zostać zablokowana (wynik fałszywie ujemny **)**:  W wyświetlonej sekcji wiadomość e-mail powinna zostać skategoryzowana jako sekcja, wybierz jedną z następujących wartości (jeśli nie masz pewności, z jak najlepszej oceny:
     - **Phish**
     - **Złośliwe oprogramowanie**
     - **Spam**

5. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > ![Przykład nowego przesyłania adresu URL.](../../media/submission-flyout-email.png)

### <a name="send-a-suspect-url-to-microsoft"></a>Wysyłanie podejrzanego adresu URL do firmy Microsoft

1. W **polu Wybierz typ przesyłania** wybierz z listy rozwijanej pozycję **Adres URL** .

2. W **wyświetlonym** polu Adres URL wprowadź pełny adres URL (na przykład `https://www.fabrikam.com/marketing.html`).

3. W **sekcji Wybierz przyczynę przesyłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - Powinna zostać zablokowana (wynik fałszywie ujemny **)**: W wyświetlonej sekcji Ten adres **URL** powinien zostać skategoryzowany jako sekcja, która powinna być wyświetlana, wybierz jedną z następujących wartości (jeśli nie masz pewności, zachęć do tego z jak najlepszej oceny):
     - **Phish**
     - **Złośliwe oprogramowanie**

4. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > ![Przykład nowego przesłania wiadomości e-mail.](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Przesyłanie podejrzanego załącznika wiadomości e-mail do firmy Microsoft

1. W **polu Wybierz typ przesyłania** **wybierz z listy** rozwijanej pozycję Załącznik wiadomości e-mail.

2. W **wyświetlonej sekcji** Plik kliknij pozycję **Przeglądaj pliki**. W otwartym oknie dialogowym znajdź i zaznacz plik, a następnie kliknij przycisk **Otwórz**.

3. W **sekcji Wybierz przyczynę przesyłania do firmy Microsoft** wybierz jedną z następujących opcji:
   - **Nie powinno być blokowane (wynik fałszywie dodatni)**
   - Powinna zostać zablokowana (wynik fałszywie ujemny **)**:  W wyświetlonej sekcji Ten plik powinien zostać skategoryzowany jako sekcja, która powinna być widoczna, wybierz jedną z następujących wartości (jeśli nie masz pewności, z jak najlepszej oceny:
     - **Phish**
     - **Złośliwe oprogramowanie**

4. Po zakończeniu kliknij pozycję **Prześlij**.

    > [!div class="mx-imgBorder"]
    > ![Przykład nowego przesyłania załącznika.](../../media/submit-email-attachment-for-analysis.png)

> [!NOTE]
> Jeśli filtrowanie złośliwego oprogramowania zastąpiło załączniki wiadomości alertem o złośliwym Text.txt pliku, należy przesłać oryginalną wiadomość z kwarantanny zawierającej oryginalne załączniki. Aby uzyskać więcej informacji na temat kwarantanny i sposobu usuwania wiadomości z wynikami fałszywie dodatnimi złośliwego oprogramowania, zobacz Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako [administrator](manage-quarantined-messages-and-files.md).

## <a name="view-admin-submissions-to-microsoft"></a>Wyświetlanie przesyłania administratorów do firmy Microsoft

1. W portalu Microsoft 365 Defender pod stroną <https://security.microsoft.com>, przejdź do strony **Przesyłanie** w witrynie **Akcje & przesyłania** \> **.** Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Materiały sprawdź** , **czy jest** zaznaczona karta Załącznik wiadomości e-mail, **adresu URL** **lub wiadomości e-mail** .

   - Pozycje można sortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby wyświetlić maksymalnie siedem kolumn. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):
     - **Nazwa przesłania**<sup>\*</sup>
     - **Nadawca**<sup>\*</sup>
     - **Adresat**
     - **Data przesłana**<sup>\*</sup>
     - **Powód przesłania**<sup>\*</sup>
     - **Stan**<sup>\*</sup>
     - **Wynik**<sup>\*</sup>
     - **Werdykt filtru**
     - **Przyczyna dostarczenia/zablokowania**
     - **Identyfikator przesyłania**
     - **Identyfikator komunikatu sieciowego/identyfikator obiektu**
     - **Kierunek**
     - **Adres IP nadawcy**
     - **Poziom zgodności zbiorczej (BCL)**
     - **Destination (Miejsce docelowe)**
     - **Akcja zasad**
     - **Przesłane przez**
     - **Phish simulation**
     - **Tagi**<sup>\*</sup>
     - **Zezwalaj**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > ![Nowe opcje dostosowywania kolumn dla przesyłania administratorów.](../../media/submit-admin-submissios-customize-columns.png)

   - Aby filtrować pozycje, kliknij pozycję **Filtruj**. Dostępne filtry:
     - **Data przesłana**: **Data rozpoczęcia** **i Data zakończenia**.
     - **Identyfikator przesyłania**: wartość GUID przypisana do każdego przesłania.
     - **Identyfikator wiadomości sieciowej**
     - **Nadawca**
     - **Adresat**
     - **Nazwa**
     - **Przesłane przez**
     - **Powód przesłania**
     - **Stan**
     - **Tagi**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > ![Nowe opcje filtrowania dla przesyłania przez administratora.](../../media/submit-admin-submissions-view-filters.png)

   - Aby zgrupować pozycje, kliknij pozycję **Grupuj** i wybierz jedną z następujących wartości z listy rozwijanej:
     - **Brak**
     - **Type**
     - **Przyczyna**
     - **Stan**
     - **Result (Wynik)**
     - **Tagi**

   - Aby wyeksportować pozycje, kliknij pozycję **Eksportuj**. W wyświetlonym oknie dialogowym zapisz .csv pliku.

### <a name="admin-submission-result-details"></a>Szczegóły wyniku przesłania przez administratora

Wiadomości przesłane w przesłanych przez administratorów są przeglądane i wyświetlane w wysuwanych szczegółach przesyłania wyników:

- Jeśli wystąpił błąd w uwierzytelnianiu wiadomości e-mail nadawcy w czasie dostarczania.
- Informacje na temat wskazówek dotyczących zasad, które mogły wpłynąć na werdykt wiadomości lub go pominąć.
- Bieżące wyniki detonacji, aby sprawdzić, czy adresy URL lub pliki zawarte w wiadomości były złośliwe.
- Opinie graderów.

Jeśli wynik został znaleziony, wynik powinien być dostępny za kilka minut. Jeśli nie było problemu z uwierzytelnianiem lub dostarczaniem poczty e-mail, zastąpienie nie wpłynęło na to, może to potrwać nawet jeden dzień.

## <a name="view-user-submissions-to-microsoft"></a>Wyświetlanie przesyłania użytkowników do firmy Microsoft

Jeśli wdrożono dodatek Report [Message](enable-the-report-message-add-in.md) (Wiadomość raportu), dodatek Wyłudzanie informacji ([Report Phishing](enable-the-report-phish-add-in.md)) lub użytkownicy korzystają z wbudowanego raportowania w programie [Outlook w sieci Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), można sprawdzić, co raportują użytkownicy, na karcie  Komunikat zgłoszony przez użytkownika.

1. W portalu Microsoft 365 Defender pod stroną <https://security.microsoft.com>, przejdź do strony **Przesyłanie** w witrynie **Akcje & przesyłania** \> **.** Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Materiały** wybierz kartę **Użytkownik zgłosił wiadomości** .

   - Pozycje można sortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby wyświetlić opcje. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

     - **Temat wiadomości e-mail**<sup>\*</sup>
     - **Zgłoszone przez**<sup>\*</sup>
     - **Data zgłoszonej daty**<sup>\*</sup>
     - **Nadawca**<sup>\*</sup>
     - **Zgłoszona przyczyna**<sup>\*</sup>
     - **Wynik**<sup>\*</sup>
     - **Identyfikator zgłoszony wiadomości**
     - **Identyfikator wiadomości sieciowej**
     - **Adres IP nadawcy**
     - **Zgłoszone od**
     - **Phish simulation**
     - **Konwertowane na przesyłanie administratora**
     - **Tagi**<sup>\*</sup>
     - **Oznaczone jako**<sup>\*</sup>
     - **Oznaczone przez**
     - **Data oznaczona**

     Po zakończeniu kliknij przycisk **Zastosuj**.

   - Aby filtrować pozycje, kliknij pozycję **Filtruj**. Dostępne filtry:
     - **Data zgłoszone**: **Data rozpoczęcia i** **Data zakończenia**.
     - **Zgłoszone przez**
     - **Temat wiadomości e-mail**
     - **Identyfikator zgłoszony wiadomości**
     - **Identyfikator wiadomości sieciowej**
     - **Nadawca**
     - **Zgłoszono przyczynę**: **Wiadomość niebędąka** śmieciem, **wiadomością phish** lub **spamem**
     - **Zgłoszone przez**: **dodatek firmy Microsoft** lub dodatek **innej firmy**
     - **Phish simulation**: **Yes** or **No**
     - **Konwertowane na przesyłanie administratora**: **Tak** lub **Nie**
     - **Tagi**

     Po zakończeniu kliknij przycisk **Zastosuj**.

     > [!div class="mx-imgBorder"]
     > ![Nowe opcje filtrowania dla przesyłania użytkowników.](../../media/submit-user-submissions-view-filters.png)

   - Aby zgrupować pozycje, kliknij pozycję **Grupuj** i wybierz jedną z następujących wartości z listy rozwijanej:
     - **Brak**
     - **Przyczyna**
     - **Nadawca**
     - **Zgłoszone przez**
     - **Result (Wynik)**
     - **Zgłoszone od**
     - **Phish simulation**
     - **Konwertowane na przesyłanie administratora**
     - **Tagi**
   
   - Aby wyeksportować pozycje, kliknij pozycję **Eksportuj**. W wyświetlonym oknie dialogowym zapisz .csv pliku.

> [!NOTE]
> Jeśli organizacje są skonfigurowane do wysyłania wiadomości zgłoszonych przez użytkowników tylko do niestandardowej skrzynki pocztowej, zgłoszone wiadomości nie zostaną wysłane ponownie, a wyniki  w raportach użytkowników będą zawsze puste.

### <a name="undo-user-submissions"></a>Cofanie przesyłania użytkowników

Gdy użytkownik przesyła podejrzaną wiadomość e-mail do niestandardowej skrzynki pocztowej, użytkownik i administrator nie mogą cofnąć przesłania. Jeśli użytkownik chce odzyskać wiadomość e-mail, będzie ona dostępna do odzyskania w folderach Elementy usunięte lub Wiadomości-śmieci.

### <a name="converting-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Konwertowanie użytkownika zgłosił wiadomości z niestandardowej skrzynki pocztowej na przesyłanie administratora 

Jeśli skonfigurowano niestandardową skrzynkę pocztową w celu przechwycenia wiadomości zgłoszonych przez użytkowników bez wysyłania ich do firmy Microsoft, można znaleźć i wysłać określone wiadomości do firmy Microsoft w celu analizy.

Na karcie **Użytkownik zgłosił wiadomości** wybierz wiadomość z listy, kliknij pozycję Prześlij do firmy **Microsoft** w celu analizy, a następnie wybierz jedną z następujących wartości z listy rozwijanej:

- **Oczyszczanie raportu**
- **Zgłaszanie wyłudzania informacji**
- **Zgłaszanie złośliwego oprogramowania**
- **Zgłaszanie spamu**
- **Wyzwalanie badania**

> [!div class="mx-imgBorder"]
> ![Nowe opcje na przycisku Akcja.](../../media/admin-submission-main-action-button.png)
