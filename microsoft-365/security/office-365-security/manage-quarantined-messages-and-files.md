---
title: Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak wyświetlać wiadomości poddanych kwarantannie i zarządzać nimi dla wszystkich użytkowników usługi Exchange Online Protection (EOP). Administratorzy w organizacjach z Ochrona usługi Office 365 w usłudze Microsoft Defender mogą również zarządzać plikami poddanymi kwarantannie w usługach SharePoint Online, OneDrive dla Firm i Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 449886f6272c81f9947fd3e7ea869e565326578f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469652"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomościom w kwarantannie usługi EOP](quarantine-email-messages.md).

Administratorzy mogą wyświetlać, zwalniać i usuwać wszystkie typy wiadomości poddanych kwarantannie wszystkim użytkownikom. Administratorzy mogą również raportować wyniki fałszywie dodatnie firmie Microsoft.

Domyślnie tylko administratorzy mogą zarządzać wiadomościami poddanymi kwarantannie jako złośliwe oprogramowanie, wyłudzaniem dużej pewności lub ze względu na reguły przepływu poczty (nazywane także regułami transportu). Jednak administratorzy _mogą używać zasad_ kwarantanny w celu określenia, co użytkownicy mogą robić w kwarantannie wiadomości w zależności od tego, dlaczego wiadomość została poddana kwarantannie (dla obsługiwanych funkcji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

Administratorzy w organizacjach Ochrona usługi Office 365 w usłudze Microsoft Defender mogą również zarządzać plikami poddanymi kwarantannie przez administratorów Sejf Załączniki wiadomości SharePoint[, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

W portalu usługi Microsoft 365 Defender lub programie PowerShell (Exchange Online PowerShell dla organizacji z skrzynkami pocztowymi w programie Exchange Online i zarządzaniu nimi; autonomiczny program Power Microsoft 365 Shell usługi EOP dla organizacji bez Exchange Online skrzynki pocztowe).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć Microsoft 365 Defender, przejdź do .<https://security.microsoft.com> Aby przejść bezpośrednio do strony **kwarantanny**, użyj .<https://security.microsoft.com/quarantine>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby podjąć działania dotyczące wiadomości poddanych kwarantannie wszystkim użytkownikom, musisz być członkiem grup ról Zarządzanie **organizacją,** **Administrator** zabezpieczeń lub **Administrator kwarantanny**<sup>\*</sup> . Aby przesłać wiadomości do firmy Microsoft, musisz być członkiem grupy ról **Administrator** zabezpieczeń.
  - Aby dostęp do wiadomości poddanych kwarantannie dla wszystkich użytkowników był tylko do odczytu, musisz być członkiem grup  ról Czytelnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.
  - <sup>\*</sup>Członkowie grupy ról **Administrator** kwarantanny w rolach współpracy poczty **e-mail &** w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) muszą być także członkami grupy ról Zarządzanie wiadomościami w  programie [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups), aby wykonać procedury kwarantanny w programie Exchange Online PowerShell.

- Poddaj je kwarantannie wiadomości są zachowywane przez domyślny okres w zależności od tego, dlaczego zostały poddane kwarantannie. Po wygaśnięciu okresu przechowywania wiadomości są automatycznie usuwane i nie można ich odzyskać. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomościom w kwarantannie usługi EOP i Ochrona usługi Office 365 w usłudze Defender](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Zarządzanie wiadomościami Microsoft 365 Defender-mail poddanych kwarantannie za pomocą portalu zarządzania wiadomościami e-mail poddanymi kwarantannie

### <a name="view-quarantined-email"></a>Wyświetlanie poddanych kwarantannie wiadomości e-mail

1. W portalu Microsoft 365 Defender pod adresem  <https://security.microsoft.com>, przejdź do tematu Przeglądanie **& poczty e-mail** \> **.**\> Aby przejść bezpośrednio do strony **kwarantanny**, użyj .<https://security.microsoft.com/quarantine>

2. Na stronie **Kwarantanna** sprawdź, **czy jest** zaznaczona karta Poczta e-mail.

3. Wyniki możesz posortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny**  , aby zmienić wyświetlane kolumny. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

   - **Odebrano czas**<sup>\*</sup>
   - **Temat**<sup>\*</sup>
   - **Nadawca**<sup>\*</sup>
   - **Powód kwarantanny**<sup>\*</sup>
   - **Stan wersji**<sup>\*</sup>
   - **Typ zasad**<sup>\*</sup>
   - **Wygasa**<sup>\*</sup>
   - **Adresat**
   - **Identyfikator wiadomości**
   - **Nazwa zasad**
   - **Rozmiar wiadomości**
   - **Kierunek poczty**
   - **Tag adresata**

   Po zakończeniu kliknij przycisk **Zastosuj**.

4. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym **wysuwanych filtrach** są dostępne następujące filtry:
   - **Identyfikator wiadomości**: unikatowy identyfikator globalny wiadomości.

     Na przykład śledzenie wiadomości zostało [](message-trace-scc.md) użyte do wyszukiwania wiadomości wysłanej do użytkownika w organizacji i użytkownik ustali, że wiadomość została poddana kwarantannie, a nie dostarczona. Pamiętaj, aby uwzględnić pełną wartość identyfikatora wiadomości, która może zawierać nawiasy kwadratowe (\<\>). Na przykład: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adres nadawcy**
   - **Adres adresata**
   - **Temat**
   - **Godzina odebrana**: Wprowadź czas **rozpoczęcia i** **czas zakończenia** (datę).
   - **Wygasa:** Filtruj wiadomości według tego, kiedy wygasną z kwarantanny:
     - **Dzisiaj**
     - **Następne 2 dni**
     - **Następne 7 dni**
     - **Niestandardowe**: Wprowadź czas **rozpoczęcia i** **czas zakończenia** (datę).
   - **Tag adresata**
   - **Powód kwarantanny**:
     - **Reguła transportu** (reguła przepływu poczty e-mail)
     - **Zbiorcze**
     - **Spam**
     - **Złośliwe oprogramowanie**: Zasady ochrony przed złośliwym oprogramowaniem w usługach EOP Sejf załączników w programie Ochrona usługi Office 365 w usłudze Defender. Wartość **Typ zasad** wskazuje, która funkcja została użyta.
     - **Wyłudzanie** informacji: Werdykt filtru spamu był w kwarantannie przed wyłudzaniem informacji lub wyłudzaniem informacji w kwarantannie (ustawienia [spoof settings](set-up-anti-phishing-policies.md#spoof-settings) lub [impersonation protection](set-up-anti-phishing-policies).
     - **Wyłudzanie informacji o wysokiej pewności**
   - **Adresat**: **Wszyscy użytkownicy lub** **Tylko ja**. Użytkownicy końcowi mogą zarządzać tylko w kwarantannie wysyłanymi do nich wiadomościami.
   - **Stan wersji**: Dowolna z następujących wartości:
     - **Przegląd potrzeb**
     - **Zatwierdzono**
     - **Odmówiono**
     - **Zażądano wydania**
     - **Wydano**
   - **Typ zasad**: Filtrowanie wiadomości według typu zasad:
     - **Zasady ochrony przed złośliwym oprogramowaniem**
     - **Sejf załączników**
     - **Zasady ochrony przed wyłudzaniem informacji**
     - **Zasady ochrony przed spamem**
     - **Reguła transportu** (reguła przepływu poczty e-mail)

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić filtry, kliknij ikonę ![Wyczyść filtry.](../../media/m365-cc-sc-clear-filters-icon.png) **Wyczyść filtry**.

5. Użyj pola **Wyszukaj** i odpowiadającej mu wartości, aby znaleźć określone wiadomości. Symbole wieloznaczne nie są obsługiwane. Możesz wyszukiwać według następujących wartości:
   - Adres e-mail nadawcy
   - Temat. Użyj całego tematu wiadomości. W wyszukiwaniu nie jest wróżniana wielkość liter.

   Po wprowadzeniu kryteriów wyszukiwania naciśnij klawisz ENTER, aby przefiltrować wyniki.

Po odnalezieniu określonej wiadomości poddanej kwarantannie zaznacz ją, aby wyświetlić szczegółowe informacje i podjąć w związku z tym działanie (na przykład wyświetlanie, zwalnianie, pobieranie lub usuwanie wiadomości).

#### <a name="view-quarantined-message-details"></a>Wyświetlanie szczegółów wiadomości poddanych kwarantannie

Po wybraniu z listy wiadomości poddanej kwarantannie w wysuwanych szczegółach są dostępne następujące informacje.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Wysuw szczegółów wiadomości poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout.png":::

- **Identyfikator wiadomości**: unikatowy identyfikator globalny wiadomości. Dostępne w **polu nagłówka Identyfikatora** wiadomości w nagłówku wiadomości.
- **Adres nadawcy**
- **Otrzymano**: data/godzina otrzymania wiadomości.
- **Temat**
- **Przyczyna kwarantanny**: pokazuje, czy wiadomość została zidentyfikowany jako **spam****,** masowa, **phish**, dopasowana do reguły przepływu **poczty (reguła** transportu) lub została zidentyfikowana jako zawierająca **złośliwe oprogramowanie**.
- **Typ zasad**
- **Nazwa zasad**
- **Liczba adresatów**
- **Adresaci**: Jeśli wiadomość zawiera wielu adresatów, należy kliknąć pozycję Podgląd  wiadomości lub Wyświetl  nagłówek wiadomości, aby wyświetlić pełną listę adresatów.
- **Tag adresata**: Aby uzyskać więcej informacji, zobacz [Tagi użytkowników w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](user-tags.md).
- **Wygasa:** Data/godzina, kiedy wiadomość zostanie automatycznie i trwale usunięta z kwarantanny.
- **Opublikowano dla**: Wszystkie adresy e-mail (jeśli są), na które została wydana wiadomość.
- **Jeszcze nie opublikowano** dla: Wszystkie adresy e-mail (jeśli są), na które wiadomość nie została jeszcze wydana.

Aby podjąć działanie w związku z wiadomością, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach, ale zmienić obecnie poddaną kwarantannie wiadomość, użyj strzałek w górę i w dół u góry wysuwanych.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Strzałki w górę i w dół w wysuwanych szczegółach wiadomości poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Działania w przypadku poddanych kwarantannie wiadomości e-mail

Po wybraniu poddaną kwarantannie wiadomości z listy w wysuwanych szczegółach są dostępne następujące akcje:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="The Available actions in the details flyout of a quarantined message" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png) **Zwolnij wiadomość e-mail**<sup>\*</sup>: W wyświetlonym okienku wysuwu skonfiguruj następujące opcje:
  - **Dodaj nadawcę do listy zezwalań w Twojej** organizacji: wybierz tę opcję, aby zapobiec kwarantannie wiadomości od tego nadawcy.
  - Wybierz jedną z następujących opcji:
    - **Upuszczanie dla wszystkich adresatów**
    - **Zwolnij na określonych adresatów**: Wybierz adresatów w **wyświetlonym polu** Adresaci
  - **Wysłać kopię tej wiadomości do** innych adresatów: Zaznacz tę opcję i wprowadź adresy e-mail adresatów w **wyświetlonym polu Adresaci** .

    > [!NOTE]
    > Aby wysłać kopię wiadomości do innych adresatów, należy także zwolnić wiadomość co najmniej jednego z oryginalnych adresatów (wybierz pozycję Zwolnij  dla wszystkich adresatów lub Zwolnij dla określonych **adresatów**).

  - **Prześlij wiadomość do firmy Microsoft**, aby poprawić wykrywanie (wynik fałszywie dodatni): Ta opcja jest domyślnie zaznaczona i zgłasza firmie Microsoft błędnie poddany kwarantannie komunikat jako wynik fałszywie dodatni. Jeśli wiadomość została poddana kwarantannie jako spam, zbiorcza, wyłudzająca informacje lub zawierająca złośliwe oprogramowanie, jest również raportowana zespołowi Microsoft Do analizy spamu. W zależności od wyników ich analizy reguły filtrowania spamu dla całej usługi mogą zostać dostosowane, aby umożliwić przesłanie wiadomości.

  - **Zezwalaj na wiadomości w** ten sposób: Ta opcja jest domyślnie wyłączona (![Przełącznik wyłączony](../../media/scc-toggle-off.png)). Włącz (Włącz![)](../../media/scc-toggle-on.png) , aby tymczasowo uniemożliwić poddaj kwarantannie wiadomości z podobnymi adresami URL, załącznikami i innymi właściwościami. Po włączeniu tej opcji dostępne są następujące opcje:
    - **Usuń po**: wybierz, jak długo wiadomości mają być wyświetlane w ten sposób. Wybierz **od 1 dnia** **do 30 dni**. Wartość domyślna to 30.
    - **Uwaga opcjonalna**: Wprowadź użyteczny opis zezwalania.

  Po zakończeniu kliknij pozycję **Komunikat o wydaniu**.

  Uwagi dotyczące zwalniania wiadomości:

  - Nie możesz zwolnić wiadomości do tego samego adresata więcej niż raz.
  - Na liście potencjalnych adresatów pojawią się tylko adresaci, którzy nie otrzymali wiadomości.
  - Tylko członkowie **grupy ról** Administratorzy zabezpieczeń mogą widzieć wiadomości i używać ich w celu ulepszania wykrywania **(** wyników fałszywie dodatnich) i Zezwalaj na wiadomości **tego rodzaju.** 

- ![Ikona udostępniania wiadomości e-mail.](../../media/m365-cc-sc-share-email-icon.png) **Udostępnianie wiadomości** e-mail: W wyświetlonym wysuwaniu dodaj co najmniej jednego adresata, aby otrzymać kopię wiadomości. Po zakończeniu kliknij pozycję **Udostępnij**.

Po kliknięciu ikony Więcej akcji są ![dostępne następujące akcje.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji**:

- ![Wyświetl ikonę nagłówków wiadomości.](../../media/m365-cc-sc-view-message-headers-icon.png) **Wyświetlanie nagłówków wiadomości**: Wybierz ten link, aby wyświetlić tekst nagłówka wiadomości. Zostanie **wyświetlone okno wysuwu** nagłówka wiadomości z następującymi linkami:
  - **Kopiowanie nagłówka wiadomości**: kliknij ten link, aby skopiować nagłówek wiadomości (wszystkie pola nagłówka) do Schowka.
  - **Analizator nagłówka wiadomości firmy Microsoft**: aby szczegółowo przeanalizować pola i wartości nagłówka, kliknij ten link, aby przejść do Analizatora nagłówka wiadomości. Wklej nagłówek wiadomości w sekcji Wstaw  nagłówek wiadomości, który chcesz przeanalizować (naciśnij klawisze CTRL+V lub kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej), a** następnie kliknij pozycję **Analizuj nagłówki**.

- ![Ikona podglądu wiadomości.](../../media/m365-cc-sc-preview-message-icon.png) **Podgląd wiadomości**: W wyświetlonym wysuwanych oknach wybierz jedną z następujących kart:
  - **Źródło**: wyświetla wersję HTML treści wiadomości z wyłączonymi wszystkimi linkami.
  - **Zwykły tekst**: wyświetla treść wiadomości w formacie zwykłego tekstu.

- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: Po kliknięciu przycisku **Tak** w wyświetlonym komunikacie ostrzegawczym wiadomość zostanie natychmiast usunięta, a wiadomość nie zostanie wysłana do oryginalnych adresatów.

- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobierz wiadomość e-mail**: W wyświetlonym wysuwanym czacie wybierz pozycję Rozumiem zagrożenia związane z pobieraniem tej  **wiadomości, a** następnie kliknij przycisk Pobierz, aby zapisać kopię lokalną wiadomości w formacie eml.

- ![Ikona Blokowania nadawcy.](../../media/m365-cc-sc-block-sender-icon.png) **Blokowanie nadawcy**: Dodaj nadawcę do listy zablokowanych nadawców w **skrzynce pocztowej** . Aby uzyskać więcej informacji, zobacz [Blokowanie nadawcy poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Ikona Prześlij tylko.](../../media/m365-cc-sc-create-icon.png) **Tylko przesyłanie**: raportuje wiadomość do firmy Microsoft w celu analizy. W wyświetlonym wysuwu wybierz następujące opcje:
  - **Wybierz typ przesyłania**: Adres **e-mail** (domyślny), **Adres URL** lub **Plik**.
  - **Dodaj identyfikator wiadomości sieciowej lub przekaż plik wiadomości e-mail**: Wybierz jedną z następujących opcji:
    - **Dodawanie identyfikatora wiadomości sieciowej poczty e-mail** (domyślnie z odpowiednią wartością w polu)
    - Upload plik wiadomości e-mail **(msg lub eml)**: Kliknij przycisk Przeglądaj  pliki, aby znaleźć i wybrać plik wiadomości msg lub eml do przesłania.
  - **Wybierz adresata, który miał problem**: Wybierz co najmniej jednego oryginalnego adresata wiadomości, aby przeanalizować zastosowane do nich zasady.
  - **Wybierz przyczynę przesyłania do firmy Microsoft**: Wybierz jedną z następujących opcji:
    - **Nie powinno być blokowane (wynik fałszywie dodatni)** (ustawienie domyślne): Dostępne są następujące opcje:
      - **Zezwalaj na wiadomości w** ten sposób: Ta opcja jest domyślnie wyłączona (![Przełącznik wyłączony](../../media/scc-toggle-off.png)). Włącz (Włącz![)](../../media/scc-toggle-on.png) , aby tymczasowo uniemożliwić poddaj kwarantannie wiadomości z podobnymi adresami URL, załącznikami i innymi właściwościami. Po włączeniu tej opcji dostępne są następujące opcje:
        - **Usuń po**: wybierz, jak długo wiadomości mają być wyświetlane w ten sposób. Wybierz **od 1 dnia** **do 30 dni**. Wartość domyślna to 30.
        - **Uwaga opcjonalna**: Wprowadź użyteczny opis zezwalania.
    - **Powinna zostać zablokowana (wynik fałszywie ujemny)**.

  Po zakończeniu kliknij pozycję **Prześlij**.

<sup>\*</sup> Ta opcja nie jest dostępna w przypadku wiadomości, które zostały już wydane (wartość **stanu** Wydana została **wydana**).

Jeśli nie zwolnisz lub nie usuniesz wiadomości, zostanie ona usunięta po upływie domyślnego okresu przechowywania kwarantanny (jak pokazano w **kolumnie Wygasa** ).

> [!NOTE]
> Na urządzeniach przenośnych tekst opisu nie jest dostępny na ikonach akcji.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Szczegóły wiadomości poddanej kwarantannie z wyróżnieniami dostępnych akcji" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Ikony w kolejności i odpowiadające im opisy są podsumowywane w poniższej tabeli:
>
> |Ikona|Opis|
> |---:|---|
> |![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png)|**Wiadomość e-mail o wersji**|
> |![Ikona udostępniania wiadomości e-mail.](../../media/m365-cc-sc-share-email-icon.png)|**Udostępnianie wiadomości e-mail**|
> |![Wyświetl ikonę nagłówków wiadomości.](../../media/m365-cc-sc-view-message-headers-icon.png)|**Wyświetlanie nagłówków wiadomości**|
> |![Ikona podglądu wiadomości.](../../media/m365-cc-sc-preview-message-icon.png)|**Podgląd wiadomości**|
> |![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png)|**Usuwanie z kwarantanny**|
> |![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png)|**Pobieranie wiadomości e-mail**|
> |![Ikona Blokowania nadawcy.](../../media/m365-cc-sc-block-sender-icon.png)|**Blokowanie nadawcy**|
> |![Ikona Prześlij tylko.](../../media/m365-cc-sc-create-icon.png)|**Tylko przesyłanie**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Działanie w przypadku wielu poddanych kwarantannie wiadomości e-mail

Po zaznaczeniu wielu poddanych kwarantannie wiadomości na liście (maksymalnie 100) przez kliknięcie pustego obszaru z lewej strony pierwszej kolumny zostanie wyświetlona lista rozwijana Akcje zbiorcze, na której możesz podjąć następujące czynności:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Lista rozwijana Akcje zbiorcze dla wiadomości w kwarantannie" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png) **Release messages**: Releases messages to all recipients. W wyświetlonym wysuwzie możesz wybrać następujące opcje, które są takie same jak w przypadku zwolnienia jednej wiadomości:
  - **Dodawanie nadawcy do listy zezwalań w organizacji**
  - **Wysyłanie kopii tej wiadomości do innych adresatów**
  - **Prześlij wiadomość do firmy Microsoft w celu ulepszenia wykrywania (wynik fałszywie dodatni)**
  - **Zezwalaj na wiadomości w ten sposób**:
    - **Usuwanie po**: **od 1 dnia do** **30 dni**
    - **Uwaga opcjonalna**

  Po zakończeniu kliknij pozycję **Komunikat o wydaniu**.

  > [!NOTE]
  > Rozważmy następujący scenariusz: wysyłanie john@gmail.com wiadomości do faith@contoso.com i john@subsidiary.contoso.com. W usłudze Gmail ta wiadomość jest rozsyłana do dwóch kopii, które są kierowane do kwarantanny jako próby wyłudzenia informacji przez firmę Microsoft. Administrator wydaje oba te komunikaty do admin@contoso.com. Zostanie dostarczona pierwsza opublikowana wiadomość, która dotrze do skrzynki pocztowej administratora. Druga wydana wiadomość jest identyfikowana jako zduplikowana dostarczanie i jest pomijana. Wiadomości są identyfikowane jako duplikaty, jeśli mają ten sam identyfikator wiadomości i czas jego odsyłki.

- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuwanie wiadomości**: Po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeń wiadomości są natychmiast usuwane z kwarantanny, a nie wysyłane do oryginalnych adresatów.
- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobieranie wiadomości**
- ![Ikona Prześlij tylko.](../../media/m365-cc-sc-create-icon.png) **Tylko przesyłanie**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Zarządzanie plikami poddanymi kwarantannie w portalu Microsoft 365 Defender w programie Ochrona usługi Office 365 w usłudze Defender

> [!NOTE]
> Procedury dotyczące plików poddanych kwarantannie w tej sekcji są dostępne tylko dla subskrybentów Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 lub Plan 2.

W organizacjach Ochrona usługi Office 365 w usłudze Defender, administratorzy mogą zarządzać plikami poddanymi kwarantannie przez użytkownika Sejf Załączniki do SharePoint, OneDrive i Microsoft Teams. Aby włączyć ochronę tych plików, zobacz [Włączanie załączników Sejf załączników wiadomości SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Wyświetlanie plików poddanych kwarantannie

1. W portalu Microsoft 365 Defender pod adresem  <https://security.microsoft.com>, przejdź do tematu Przeglądanie **& poczty e-mail** \> **.**\> Aby przejść bezpośrednio do strony **kwarantanny**, użyj .<https://security.microsoft.com/quarantine>

2. Na stronie **Kwarantanna** wybierz **kartę Pliki** **(karta** Domyślna jest poczta e-mail).

3. Wyniki możesz posortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby zmienić wyświetlane kolumny. Kolumny domyślne są oznaczone gwiazdką (<sup>\*</sup>):
   - **Użytkownik**<sup>\*</sup>
   - **Lokalizacja**<sup>\*</sup>
   - **Nazwa pliku załącznika**<sup>\*</sup>
   - **Adres URL pliku**<sup>\*</sup>
   - **Rozmiar pliku**
   - **Stan wersji**<sup>\*</sup>
   - **Wygasa**<sup>\*</sup>
   - **Wykryty przez**
   - **Zmodyfikowane przez czas**

   Po zakończeniu kliknij przycisk **Zastosuj lub** **Anuluj**.

4. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym **wysuwanych filtrach** są dostępne następujące filtry:
   - **Godzina odebrana**: **Godzina rozpoczęcia** **i Godzina zakończenia** (data).
   - **Wygasa:** **Godzina rozpoczęcia i** **Godzina zakończenia** (data).
   - **Przyczyna kwarantanny**: Jedyną dostępną wartością jest złośliwe **oprogramowanie**.
   - **Typ zasad**

   Po zakończeniu kliknij przycisk **Zastosuj lub** **Anuluj**.

Po odnalezieniu określonego pliku poddanego kwarantannie wybierz go, aby wyświetlić szczegółowe informacje i podjąć w związku z nim działanie (na przykład wyświetlanie, zwalnianie, pobieranie lub usuwanie pliku).

#### <a name="view-quarantined-file-details"></a>Wyświetlanie szczegółów pliku poddanego kwarantannie

Po wybraniu z listy pliku poddanego kwarantannie w wysuwanych szczegółach są dostępne następujące informacje:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Wysuw szczegółów pliku poddanego kwarantannie" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Nazwa pliku**
- **Adres URL** pliku: adres URL, który definiuje lokalizację pliku (na przykład w aplikacji SharePoint online).
- **Wykrywana złośliwa zawartość w** Data/godzina kwarantanny pliku.
- **Wygasa:** Data usunięcia pliku z kwarantanny.
- **Wykryty przez**
- **Wydane?**
- **Nazwa złośliwego oprogramowania**
- **Identyfikator dokumentu**: identyfikator unikatowy dokumentu.
- **Rozmiar pliku**: W kilobajtach (KB).
- **Organizacja** Unikatowy identyfikator organizacji.
- **Ostatnia modyfikacja**
- **Zmodyfikowane przez**: Użytkownik, który ostatnio zmodyfikował plik.
- **Wartość 256-bitowego algorytmu bezpiecznego skrótu (SHA-256**): tej wartości skrótu można użyć do identyfikowania pliku w innych magazynach reputacji lub w innych lokalizacjach w Twoim środowisku.

Aby podjąć działanie na pliku, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach i zmienić plik poddany kwarantannie, użyj strzałek w górę i w dół u góry wysuwanych.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Strzałki w górę i w dół w wysuwanych szczegółach plików poddanych kwarantannie" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Działanie w przypadku plików poddanych kwarantannie

Po wybraniu z listy pliku poddanego kwarantannie w wysuwanych szczegółach są dostępne następujące akcje:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Akcje w wysuwanych szczegółach pliku poddanego kwarantannie" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Ikona zwolnij plik.](../../media/m365-cc-sc-check-mark-icon.png) **Plik wydania**<sup>\*</sup>: W wyświetlonym okienku wysuwu włącz lub wyłącz pliki raportów do analizy dla firmy **Microsoft**, a następnie kliknij pozycję **Zwolnij**.
- ![Ikona zwolnij plik.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Ikona pobierz plik.](../../media/m365-cc-sc-download-icon.png) **Pobierz plik**: W wyświetlonym wysuwaniu wybierz pozycję Rozumiem zagrożenia związane z pobieraniem tego **pliku, a** następnie kliknij pozycję  Pobierz, aby zapisać lokalną kopię pliku.
- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: Po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeń plik zostanie natychmiast usunięty.
- ![Ikona Blokowania nadawcy.](../../media/m365-cc-sc-block-sender-icon.png) **Blokowanie nadawcy**: Dodaj nadawcę do listy zablokowanych nadawców w **skrzynce pocztowej** . Aby uzyskać więcej informacji, zobacz [Blokowanie nadawcy poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Ta opcja nie jest dostępna w przypadku plików, które zostały już wydane (wartość **stanu** Wydana została **wydana**).

Jeśli nie zwolnisz lub nie usuniesz pliku, zostanie on usunięty po wygaśnięciu domyślnego okresu przechowywania kwarantanny (jak pokazano w **kolumnie Wygasa** ).

#### <a name="take-action-on-multiple-quarantined-files"></a>Działanie w przypadku wielu plików poddanych kwarantannie

Po zaznaczeniu wielu poddanych kwarantannie plików na liście (maksymalnie 100) przez kliknięcie pustego obszaru z lewej strony kolumny Temat zostanie wyświetlona lista rozwijana Akcje zbiorcze, na której możesz podjąć następujące czynności: 

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Lista rozwijana Akcje zbiorcze dla plików w kwarantannie" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Ikona zwolnij plik.](../../media/m365-cc-sc-check-mark-icon.png) **Plik wydania**: W wyświetlonym okienku wysuwu włącz lub wyłącz pliki raportów do analizy dla firmy **Microsoft**, a następnie kliknij pozycję **Zwolnij**.
- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: Po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeń plik zostanie natychmiast usunięty.
- ![Ikona pobierz plik.](../../media/m365-cc-sc-download-icon.png) **Pobierz plik**: W wyświetlonym wysuwaniu wybierz pozycję Rozumiem zagrożenia związane z pobieraniem tego **pliku, a** następnie kliknij pozycję  Pobierz, aby zapisać lokalną kopię pliku.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Wyświetlanie Exchange Online i plików poddanych kwarantannie za pomocą programu PowerShell lub autonomicznego programu PowerShell usługi EOP

Polecenia cmdlet, których używasz do wyświetlania wiadomości i plików w kwarantannie oraz zarządzania nimi, są opisane na poniższej liście:

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): To polecenie cmdlet jest tylko dla wiadomości, a nie do kwarantanny plików z usługi Sejf Załączniki dla plików SharePoint, OneDrive i Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

[Wiadomości poddane kwarantannie — często zadawane pytania](quarantine-faq.yml)
