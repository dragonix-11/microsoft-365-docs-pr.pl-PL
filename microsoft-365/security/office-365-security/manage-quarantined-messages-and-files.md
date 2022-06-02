---
title: Zarządzaj wiadomościami i plikami poddanymi kwarantannie jako administrator
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
description: Administratorzy mogą dowiedzieć się, jak wyświetlać komunikaty poddane kwarantannie i zarządzać nimi dla wszystkich użytkowników w Exchange Online Protection (EOP). Administratorzy w organizacjach z Ochrona usługi Office 365 w usłudze Microsoft Defender mogą również zarządzać plikami poddanymi kwarantannie w usłudze SharePoint Online, OneDrive dla Firm i Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3bd239231cc49684f8b07fb73f33265c9463bad4
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839804"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w ramach EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Kwarantanna wiadomości e-mail w EOP](quarantine-email-messages.md).

Administratorzy mogą wyświetlać, zwalniać i usuwać wszystkie typy komunikatów objętych kwarantanną dla wszystkich użytkowników. Administratorzy mogą również zgłaszać firmie Microsoft wyniki fałszywie dodatnie.

Domyślnie tylko administratorzy mogą zarządzać wiadomościami, które zostały poddane kwarantannie jako złośliwe oprogramowanie, wyłudzanie informacji o wysokim poziomie zaufania lub w wyniku reguł przepływu poczty (nazywanych również regułami transportu). Administratorzy mogą jednak używać _zasad kwarantanny_ , aby określić, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie w oparciu o przyczynę kwarantanny komunikatu (w przypadku obsługiwanych funkcji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

Administratorzy w organizacjach z Ochrona usługi Office 365 w usłudze Microsoft Defender mogą również zarządzać plikami, które zostały poddane kwarantannie przez [załączniki Sejf dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Komunikaty poddane kwarantannie można wyświetlać i zarządzać nimi w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe).

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak zarządzać komunikatami poddanymi kwarantannie jako administrator. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGGPF]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć portal Microsoft 365 Defender, przejdź do strony <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Kwarantanna** , użyj polecenia <https://security.microsoft.com/quarantine>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby podjąć działania w przypadku komunikatów poddanych kwarantannie dla wszystkich użytkowników, musisz być członkiem grup ról **Zarządzanie organizacją**, **Administrator zabezpieczeń** lub **Administrator**<sup>\*</sup> kwarantanny. Aby przesłać komunikaty do firmy Microsoft, musisz być członkiem grupy ról **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do komunikatów objętych kwarantanną dla wszystkich użytkowników, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.
  - <sup>\*</sup>Członkowie grupy ról **Administrator kwarantanny** w rolach **współpracy & poczty e-mail** w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) muszą również być członkami grupy ról **Zarządzanie higieną** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups), aby wykonywać procedury kwarantanny w programie Exchange Online programie PowerShell.

- Komunikaty poddane kwarantannie są zachowywane przez domyślny okres w zależności od tego, dlaczego zostały poddane kwarantannie. Po upływie okresu przechowywania komunikaty są automatycznie usuwane i nie można ich odzyskać. Aby uzyskać więcej informacji, zobacz [Kwarantanna wiadomości e-mail w EOP i Ochrona usługi Office 365 w usłudze Defender](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Zarządzanie wiadomościami e-mail z kwarantanną przy użyciu portalu Microsoft 365 Defender

### <a name="view-quarantined-email"></a>Wyświetlanie wiadomości e-mail z kwarantanną

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Poczta e-mail & współpracy** \> **Przeglądanie** \> **kwarantanny**. Aby przejść bezpośrednio do strony **Kwarantanna** , użyj polecenia <https://security.microsoft.com/quarantine>.

2. Na stronie **Kwarantanna** sprawdź, czy **wybrano kartę Poczta e-mail** .

3. Wyniki można posortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny**  , aby zmienić wyświetlane kolumny. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

   - **Odebrany czas**<sup>\*</sup>
   - **Temat**<sup>\*</sup>
   - **Nadawcy**<sup>\*</sup>
   - **Przyczyna kwarantanny**<sup>\*</sup>
   - **Stan wydania**<sup>\*</sup>
   - **Typ zasad**<sup>\*</sup>
   - **Wygasa**<sup>\*</sup>
   - **Odbiorcy**
   - **Identyfikator komunikatu**
   - **Nazwa zasad**
   - **Rozmiar komunikatu**
   - **Kierunek wysyłki**
   - **Tag adresata**

   Po zakończeniu kliknij przycisk **Zastosuj**.

4. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym wysuwu Filtry są dostępne następujące **filtry** :
   - **Identyfikator komunikatu**: unikatowy globalnie identyfikator komunikatu.

     Na przykład użyto [śledzenia komunikatów](message-trace-scc.md) , aby wyszukać komunikat, który został wysłany do użytkownika w organizacji, i ustalić, że wiadomość została poddana kwarantannie, a nie dostarczona. Pamiętaj, aby uwzględnić pełną wartość identyfikatora komunikatu, która może zawierać nawiasy kątowe (\<\>). Przykład: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adres nadawcy**
   - **Adres odbiorcy**
   - **Temat**
   - **Odebrana godzina**: wprowadź **godzinę rozpoczęcia** i **godzinę zakończenia** (datę).
   - Wygasa: filtruj **komunikaty** według tego, kiedy wygasną po kwarantannie:
     - **Dziś**
     - **Następne 2 dni**
     - **Następne 7 dni**
     - **Niestandardowe**: wprowadź **godzinę rozpoczęcia** i **godzinę zakończenia** (data).
   - **Tag adresata**
   - **Przyczyna kwarantanny**:
     - **Reguła transportu** (reguła przepływu poczty)
     - **Zbiorczego**
     - **Spam**
     - **Złośliwe oprogramowanie**: zasady ochrony przed złośliwym oprogramowaniem w zasadach EOP lub Sejf Attachments w Ochrona usługi Office 365 w usłudze Defender. Wartość **Typ zasad** wskazuje, która funkcja została użyta.
     - **Wyłudzanie** informacji: Werdykt filtru spamu polegał na tym, że ochrona przed **wyłudzaniem** informacji lub ochrona przed wyłudzaniem informacji poddała wiadomość kwarantannie ([ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) lub [ochrona przed personifikacją](set-up-anti-phishing-policies).
     - **Wyłudzanie informacji o dużej pewności**
   - **Adresat**: **Wszyscy użytkownicy** lub **tylko ja**. Użytkownicy końcowi mogą zarządzać tylko wysłanymi do nich komunikatami objętymi kwarantanną.
   - **Stan wydania**: Dowolna z następujących wartości:
     - **Przegląd potrzeb**
     - **Zatwierdzone**
     - **Odmowa dostępu**
     - **Zażądano wydania**
     - **Wydany**
   - **Typ zasad**: filtruj komunikaty według typu zasad:
     - **Zasady ochrony przed złośliwym oprogramowaniem**
     - **zasady załączników Sejf**
     - **Zasady ochrony przed wyłudzaniem informacji**
     - **Zasady ochrony przed spamem**
     - **Reguła transportu** (reguła przepływu poczty)

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić filtry, kliknij ikonę ![Wyczyść filtry.](../../media/m365-cc-sc-clear-filters-icon.png) **Wyczyść filtry**.

5. Użyj pola **Wyszukiwania** i odpowiedniej wartości, aby znaleźć określone komunikaty. Symbole wieloznaczne nie są obsługiwane. Możesz wyszukiwać następujące wartości:
   - Adres e-mail nadawcy
   - Temat. Użyj całego tematu wiadomości. Wyszukiwanie nie uwzględnia wielkości liter.

   Po wprowadzeniu kryteriów wyszukiwania naciśnij klawisz ENTER, aby odfiltrować wyniki.

Po znalezieniu określonego komunikatu poddanej kwarantannie wybierz komunikat, aby wyświetlić szczegółowe informacje na jego temat i podjąć działania w tej sprawie (na przykład wyświetl, zwolnij, pobierz lub usuń komunikat).

#### <a name="view-quarantined-message-details"></a>Wyświetlanie szczegółów komunikatu poddanej kwarantannie

Po wybraniu komunikatu poddanej kwarantannie z listy następujące informacje są dostępne w wyświetlonym wysuwaniu szczegółów.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Wysuwane szczegóły komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout.png":::

- **Identyfikator komunikatu**: unikatowy identyfikator globalny komunikatu. Dostępne w polu nagłówek **Message-ID** w nagłówku wiadomości.
- **Adres nadawcy**
- **Odebrano**: data/godzina odebrania komunikatu.
- **Temat**
- **Przyczyna kwarantanny**: pokazuje, czy wiadomość została zidentyfikowana jako **spam**, **zbiorcza**, **phish**, dopasowana do reguły przepływu poczty (**reguła transportu**) lub została zidentyfikowana jako zawierająca **złośliwe oprogramowanie**.
- **Typ zasad**
- **Nazwa zasad**
- **Liczba adresatów**
- **Adresaci**: jeśli wiadomość zawiera wielu adresatów, musisz kliknąć **pozycję Podgląd wiadomości** lub **Wyświetl nagłówek wiadomości** , aby wyświetlić pełną listę adresatów.
- **Tag adresata**: Aby uzyskać więcej informacji, zobacz [Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender](user-tags.md).
- **Wygasa**: data/godzina automatycznego i trwałego usunięcia komunikatu z kwarantanny.
- **Wydano dla**: Wszystkie adresy e-mail (jeśli istnieją), na które wiadomość została wydana.
- **Nie została jeszcze wydana na** adres: wszystkie adresy e-mail (jeśli istnieją), na które wiadomość nie została jeszcze wydana.

Aby wykonać akcję w komunikacie, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach, ale zmienić wyświetlany komunikat w kwarantannie, użyj strzałek w górę i w dół w górnej części wysuwanego elementu.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Strzałki w górę i w dół w wysuwanym oknie szczegółów komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Podjęcie akcji w wiadomości e-mail poddanej kwarantannie

Po wybraniu komunikatu poddanej kwarantannie z listy w wysuwanym oknie szczegółów są dostępne następujące akcje:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="Dostępne akcje w wysuwanym oknie wysuwanym szczegółów komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Ikona wiadomości e-mail wydania.](../../media/m365-cc-sc-check-mark-icon.png) **Wiadomość e-mail**<sup>\*</sup> o wersji: W wyświetlonym okienku wysuwu skonfiguruj następujące opcje:
  - **Dodaj nadawcę do listy dozwolonych organizacji**: wybierz tę opcję, aby zapobiec kwarantannie komunikatów od nadawcy.
  - Wybierz jedną z następujących opcji:
    - **Wydanie dla wszystkich adresatów**
    - **Zwolnij dla określonych adresatów**: wybierz adresatów w **wyświetlonym polu Adresaci**
  - **Wyślij kopię tej wiadomości do innych adresatów**: wybierz tę opcję i wprowadź adresy e-mail **adresatów w wyświetlonym polu Adresaci** .

    > [!NOTE]
    > Aby wysłać kopię wiadomości do innych adresatów, należy również wydać komunikat co najmniej jednego z oryginalnych adresatów (wybierz pozycję **Zwolnij dla wszystkich adresatów** lub **Zwolnij dla określonych adresatów**).

  - **Prześlij wiadomość do firmy Microsoft, aby ulepszyć wykrywanie (fałszywie dodatnie):** ta opcja jest domyślnie wybrana i zgłasza błędną wiadomość do firmy Microsoft jako fałszywie dodatnią. Jeśli wiadomość została poddana kwarantannie jako spam, zbiorcze, wyłudzanie informacji lub zawierające złośliwe oprogramowanie, wiadomość zostanie również zgłoszona do zespołu ds. analizy spamu firmy Microsoft. W zależności od wyników ich analizy reguły filtru spamu w całej usłudze mogą zostać dostosowane, aby umożliwić wysyłanie wiadomości.

  - **Zezwalaj na takie komunikaty**: ta opcja jest domyślnie wyłączona (![Przełącz wyłączone).](../../media/scc-toggle-off.png) Włącz (![Włącz),](../../media/scc-toggle-on.png) aby tymczasowo uniemożliwić kwarantannie komunikaty z podobnymi adresami URL, załącznikami i innymi właściwościami. Po włączeniu tej opcji dostępne są następujące opcje:
    - **Usuń po**: wybierz, jak długo chcesz zezwalać na takie komunikaty. Wybierz od **1 dnia** do **30 dni**. Wartość domyślna to 30.
    - **Opcjonalna uwaga**: wprowadź przydatny opis zezwalania.

  Po zakończeniu kliknij pozycję **Komunikat o wersji**.

  Uwagi dotyczące wydawania komunikatów:

  - Nie można zwolnić wiadomości do tego samego adresata więcej niż raz.
  - Na liście potencjalnych adresatów pojawią się tylko adresaci, którzy nie otrzymali wiadomości.
  - Tylko członkowie grupy ról **Administratorzy zabezpieczeń** mogą wyświetlać **i używać funkcji Prześlij wiadomość do firmy Microsoft w celu ulepszenia wykrywania (fałszywie dodatniego)** i **zezwalania na komunikaty, takie jak te** opcje.

- ![Ikona udostępniania wiadomości e-mail.](../../media/m365-cc-sc-share-email-icon.png) **Udostępnij wiadomość e-mail**: w wyświetlonym wysuwie dodaj co najmniej jednego adresata, aby otrzymać kopię wiadomości. Po zakończeniu kliknij pozycję **Udostępnij**.

Następujące akcje są dostępne po kliknięciu ![ikony Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji**:

- ![Wyświetl ikonę nagłówków komunikatów.](../../media/m365-cc-sc-view-message-headers-icon.png) **Wyświetl nagłówki wiadomości**: wybierz ten link, aby wyświetlić tekst nagłówka wiadomości. Wyświetlony **zostanie wysuwany nagłówek komunikatu** z następującymi linkami:
  - **Skopiuj nagłówek wiadomości**: kliknij ten link, aby skopiować nagłówek wiadomości (wszystkie pola nagłówka) do schowka.
  - **Analizator nagłówków komunikatów firmy Microsoft**: aby dokładnie przeanalizować pola nagłówka i wartości, kliknij ten link, aby przejść do analizatora nagłówków komunikatów. Wklej nagłówek komunikatu do **sekcji Wstawianie nagłówka komunikatu, który chcesz przeanalizować** (CTRL+V lub kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**), a następnie kliknij pozycję **Analizuj nagłówki**.

- ![Ikona podglądu wiadomości.](../../media/m365-cc-sc-preview-message-icon.png) **Komunikat w wersji zapoznawczej**: W wyświetlonym wysuwie wybierz jedną z następujących kart:
  - **Źródło**: pokazuje wersję HTML treści komunikatu z wyłączonymi wszystkimi linkami.
  - **Zwykły tekst**: pokazuje treść wiadomości w postaci zwykłego tekstu.

- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu komunikat zostanie natychmiast usunięty bez wysyłania do oryginalnych adresatów.

- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobierz wiadomość e-mail**: w wyświetlonym wysuwie wybierz **pozycję Rozumiem ryzyko związane z pobraniem tej wiadomości**, a następnie kliknij pozycję **Pobierz** , aby zapisać lokalną kopię wiadomości w formacie eml.

- ![Ikona blokuj nadawcę.](../../media/m365-cc-sc-block-sender-icon.png) **Blokuj nadawcę**: dodaj nadawcę do listy zablokowanych nadawców w **skrzynce** pocztowej. Aby uzyskać więcej informacji, zobacz [Blokuj nadawcę poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Ikona przesyłania tylko.](../../media/m365-cc-sc-create-icon.png) **Prześlij tylko**: raportuje komunikat do firmy Microsoft w celu analizy. W wyświetlonym wysuwie wybierz następujące opcje:
  - **Wybierz typ przesyłania**: **Adres e-mail** (domyślny), **adres URL** lub **plik**.
  - **Dodaj identyfikator komunikatu sieciowego lub przekaż plik wiadomości e-mail**: Wybierz jedną z następujących opcji:
    - **Dodaj identyfikator wiadomości e-mail sieciowej** (wartość domyślna z odpowiednią wartością w polu)
    - **Przekaż plik e-mail (msg lub eml)**: kliknij pozycję **Przeglądaj pliki** , aby znaleźć i wybierz plik komunikatu msg lub .eml do przesłania.
  - **Wybierz adresata, który miał problem**: wybierz jednego (preferowanego) lub więcej oryginalnych adresatów wiadomości, aby przeanalizować zasady, które zostały do nich zastosowane.
  - **Wybierz powód przesyłania do firmy Microsoft**: wybierz jedną z następujących opcji:
    - **Nie powinno być blokowane (wynik fałszywie dodatni)** (wartość domyślna): Dostępne są następujące opcje:
      - **Zezwalaj na takie komunikaty**: ta opcja jest domyślnie wyłączona (![Przełącz wyłączone).](../../media/scc-toggle-off.png) Włącz (![Włącz),](../../media/scc-toggle-on.png) aby tymczasowo uniemożliwić kwarantannie komunikaty z podobnymi adresami URL, załącznikami i innymi właściwościami. Po włączeniu tej opcji dostępne są następujące opcje:
        - **Usuń po**: wybierz, jak długo chcesz zezwalać na takie komunikaty. Wybierz od **1 dnia** do **30 dni**. Wartość domyślna to 30.
        - **Opcjonalna uwaga**: wprowadź przydatny opis zezwalania.
    - **Powinna być zablokowana (fałszywie ujemna)**.

  Po zakończeniu kliknij pozycję **Prześlij**.

<sup>\*</sup> Ta opcja nie jest dostępna w przypadku komunikatów, które zostały już wydane (wartość **Stan wydania** to **Wydano**).

Jeśli nie wydasz lub nie usuniesz komunikatu, zostanie on usunięty po wygaśnięciu domyślnego okresu przechowywania kwarantanny (jak pokazano w kolumnie **Wygasa** ).

> [!NOTE]
> Na urządzeniu przenośnym tekst opisu nie jest dostępny na ikonach akcji.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Szczegóły komunikatu poddanego kwarantannie z wyróżnionymi dostępnymi akcjami" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Ikony w kolejności i odpowiadające im opisy są podsumowane w poniższej tabeli:
>
> |Ikonę|Opis|
> |---:|---|
> |![Ikona wiadomości e-mail wydania.](../../media/m365-cc-sc-check-mark-icon.png)|**Wiadomość e-mail o wersji**|
> |![Ikona udostępniania wiadomości e-mail.](../../media/m365-cc-sc-share-email-icon.png)|**Udostępnianie wiadomości e-mail**|
> |![Wyświetl ikonę nagłówków komunikatów.](../../media/m365-cc-sc-view-message-headers-icon.png)|**Wyświetlanie nagłówków komunikatów**|
> |![Ikona podglądu wiadomości.](../../media/m365-cc-sc-preview-message-icon.png)|**Komunikat w wersji zapoznawczej**|
> |![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png)|**Usuwanie z kwarantanny**|
> |![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png)|**Pobieranie wiadomości e-mail**|
> |![Ikona blokuj nadawcę.](../../media/m365-cc-sc-block-sender-icon.png)|**Blokuj nadawcę**|
> |![Ikona przesyłania tylko.](../../media/m365-cc-sc-create-icon.png)|**Tylko przesyłanie**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Podjęcie akcji w przypadku wielu wiadomości e-mail z kwarantanną

Po wybraniu wielu komunikatów poddanych kwarantannie na liście (maksymalnie 100), klikając pusty obszar po lewej stronie pierwszej kolumny, zostanie wyświetlona lista rozwijana **Akcje zbiorcze** , na której można wykonać następujące akcje:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Lista rozwijana akcji zbiorczych dla komunikatów w kwarantannie" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Ikona wiadomości e-mail wydania.](../../media/m365-cc-sc-check-mark-icon.png) **Komunikaty o wersji**: zwalnia komunikaty do wszystkich adresatów. W wyświetlonym wysuwie możesz wybrać następujące opcje, które są takie same jak w przypadku wydania pojedynczego komunikatu:
  - **Dodawanie nadawcy do listy dozwolonych w organizacji**
  - **Wysyłanie kopii tej wiadomości do innych adresatów**
  - **Prześlij wiadomość do firmy Microsoft, aby ulepszyć wykrywanie (fałszywie dodatnie)**
  - **Zezwalaj na takie komunikaty**:
    - **Usuń po**: **od 1 dnia** do **30 dni**
    - **Uwaga opcjonalna**

  Po zakończeniu kliknij pozycję **Komunikat o wersji**.

  > [!NOTE]
  > Rozważmy następujący scenariusz: john@gmail.com wysyła komunikat do faith@contoso.com i john@subsidiary.contoso.com. Gmail przekształca tę wiadomość w dwie kopie, które są kierowane do kwarantanny jako wyłudzanie informacji w firmie Microsoft. Administrator wydaje oba te komunikaty do admin@contoso.com. Pierwsza wydana wiadomość, która dociera do skrzynki pocztowej administratora, jest dostarczana. Drugi wydany komunikat jest identyfikowany jako zduplikowane dostarczanie i jest pomijany. Komunikaty są identyfikowane jako duplikaty, jeśli mają ten sam identyfikator komunikatu i czas odebrania.

- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń komunikaty**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu komunikaty zostaną natychmiast usunięte z kwarantanny bez wysyłania do oryginalnych adresatów.
- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobieranie komunikatów**
- ![Ikona przesyłania tylko.](../../media/m365-cc-sc-create-icon.png) **Tylko przesyłanie**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Zarządzanie plikami poddanymi kwarantannie w Ochrona usługi Office 365 w usłudze Defender za pomocą portalu Microsoft 365 Defender

> [!NOTE]
> Procedury dotyczące plików poddanych kwarantannie w tej sekcji są dostępne tylko dla subskrybentów Ochrona usługi Office 365 w usłudze Microsoft Defender planu 1 lub planu 2.

W organizacjach z Ochrona usługi Office 365 w usłudze Defender administratorzy mogą zarządzać plikami, które zostały poddane kwarantannie przez załączniki Sejf dla SharePoint, OneDrive i Microsoft Teams. Aby włączyć ochronę tych plików, zobacz [Włączanie Sejf załączników dla SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Wyświetlanie plików poddanych kwarantannie

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Poczta e-mail & współpracy** \> **Przeglądanie** \> **kwarantanny**. Aby przejść bezpośrednio do strony **Kwarantanna** , użyj polecenia <https://security.microsoft.com/quarantine>.

2. Na stronie **Kwarantanna** wybierz kartę **Pliki** (**Poczta e-mail** jest domyślną kartą).

3. Wyniki można posortować, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny** , aby zmienić wyświetlane kolumny. Kolumny domyślne są oznaczone gwiazdką (<sup>\*</sup>):
   - **Użytkownika**<sup>\*</sup>
   - **Lokalizacji**<sup>\*</sup>
   - **Nazwa pliku załącznika**<sup>\*</sup>
   - **Adres URL pliku**<sup>\*</sup>
   - **Rozmiar pliku**
   - **Stan wydania**<sup>\*</sup>
   - **Wygasa**<sup>\*</sup>
   - **Wykryte przez**
   - **Zmodyfikowane według czasu**

   Po zakończeniu kliknij przycisk **Zastosuj** lub **Anuluj**.

4. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym wysuwu Filtry są dostępne następujące **filtry** :
   - **Odebrana godzina**: **godzina rozpoczęcia** i **godzina zakończenia** (data).
   - **Wygasa**: **godzina rozpoczęcia** i **godzina zakończenia** (data).
   - **Przyczyna kwarantanny**: Jedyną dostępną wartością jest **złośliwe oprogramowanie**.
   - **Typ zasad**

   Po zakończeniu kliknij przycisk **Zastosuj** lub **Anuluj**.

Po znalezieniu określonego pliku poddanej kwarantannie wybierz plik, aby wyświetlić szczegółowe informacje na jego temat i podjąć działania w jego sprawie (na przykład wyświetl, zwolnij, pobierz lub usuń plik).

#### <a name="view-quarantined-file-details"></a>Wyświetlanie szczegółów pliku poddanej kwarantannie

Po wybraniu pliku poddanej kwarantannie z listy następujące informacje są dostępne w wyświetlonym wysuwanym oknie szczegółów:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Wysuwane szczegóły pliku poddanej kwarantannie" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Nazwa pliku**
- **Adres URL pliku**: adres URL definiujący lokalizację pliku (na przykład w usłudze SharePoint Online).
- **Wykryto złośliwą zawartość** Data/godzina kwarantanny pliku.
- **Wygasa**: data usunięcia pliku z kwarantanny.
- **Wykryte przez**
- **Wydany?**
- **Nazwa złośliwego oprogramowania**
- **Identyfikator dokumentu**: unikatowy identyfikator dokumentu.
- **Rozmiar pliku**: w kilobajtach (KB).
- **Organizacji** Unikatowy identyfikator organizacji.
- **Ostatnia modyfikacja**
- **Zmodyfikowane przez**: użytkownik, który ostatnio zmodyfikował plik.
- **Wartość 256-bitowego algorytmu bezpiecznego skrótu (SHA-256**): możesz użyć tej wartości skrótu, aby zidentyfikować plik w innych magazynach reputacji lub w innych lokalizacjach w środowisku.

Aby wykonać akcję w pliku, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach, ale zmienić plik poddawany kwarantannie, użyj strzałek w górę i w dół w górnej części wysuwanego elementu.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Strzałki w górę i w dół w wysuwanych szczegółach plików poddanych kwarantannie" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Podjęcie akcji w plikach poddanych kwarantannie

Po wybraniu pliku poddanej kwarantannie z listy w wysuwanym okienku szczegółów są dostępne następujące akcje:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Akcje w wysuwanym okienku szczegółów pliku poddanej kwarantannie" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Ikona pliku wydania.](../../media/m365-cc-sc-check-mark-icon.png) **Plik**<sup>\*</sup> wydania: w wyświetlonym okienku wysuwania włącz lub wyłącz **pliki raportów dla firmy Microsoft do analizy**, a następnie kliknij pozycję **Zwolnij**.
- ![Ikona pliku wydania.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Ikona pobierania pliku.](../../media/m365-cc-sc-download-icon.png) **Pobierz plik**: w wyświetlonym wysuwie wybierz **pozycję Rozumiem ryzyko związane z pobraniem tego pliku**, a następnie kliknij pozycję **Pobierz** , aby zapisać lokalną kopię pliku.
- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu plik zostanie natychmiast usunięty.
- ![Ikona blokuj nadawcę.](../../media/m365-cc-sc-block-sender-icon.png) **Blokuj nadawcę**: dodaj nadawcę do listy zablokowanych nadawców w **skrzynce** pocztowej. Aby uzyskać więcej informacji, zobacz [Blokuj nadawcę poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Ta opcja nie jest dostępna dla plików, które zostały już wydane (wartość **Stan wydania** to **Wydano**).

Jeśli nie wydasz lub nie usuniesz pliku, zostanie on usunięty po wygaśnięciu domyślnego okresu przechowywania kwarantanny (jak pokazano w kolumnie **Wygasa** ).

#### <a name="take-action-on-multiple-quarantined-files"></a>Podjęcie akcji w przypadku wielu plików poddanych kwarantannie

Po wybraniu wielu plików poddanych kwarantannie na liście (maksymalnie 100), klikając pusty obszar po lewej stronie kolumny **Temat** , zostanie wyświetlona lista rozwijana **Akcje zbiorcze** , na której można wykonać następujące akcje:

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Lista rozwijana akcji zbiorczych dla plików w kwarantannie" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Ikona pliku wydania.](../../media/m365-cc-sc-check-mark-icon.png) **Plik wydania**: w wyświetlonym okienku wysuwania włącz lub wyłącz **pliki raportów dla firmy Microsoft do analizy**, a następnie kliknij pozycję **Zwolnij**.
- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu plik zostanie natychmiast usunięty.
- ![Ikona pobierania pliku.](../../media/m365-cc-sc-download-icon.png) **Pobierz plik**: w wyświetlonym wysuwie wybierz **pozycję Rozumiem ryzyko związane z pobraniem tego pliku**, a następnie kliknij pozycję **Pobierz** , aby zapisać lokalną kopię pliku.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Używanie Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP do wyświetlania komunikatów i plików objętych kwarantanną oraz zarządzania nimi

Polecenia cmdlet używane do wyświetlania komunikatów i plików w kwarantannie oraz zarządzania nimi są opisane na następującej liście:

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): należy pamiętać, że to polecenie cmdlet dotyczy tylko komunikatów, a nie plików objętych kwarantanną z załączników Sejf dla SharePoint, OneDrive i Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

[Komunikaty poddane kwarantannie — często zadawane pytania](quarantine-faq.yml)
