---
title: Znajdowanie i zwalnianie wiadomości poddanych kwarantannie jako użytkownik
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Consumer/IW
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Użytkownicy mogą dowiedzieć się, jak wyświetlać komunikaty poddane kwarantannie i zarządzać nimi w Exchange Online Protection (EOP), które powinny zostać im dostarczone.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc3e53283f59d7a750e05d56718d389f48e6a9d9
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840021"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Znajdowanie i zwalnianie komunikatów poddanych kwarantannie jako użytkownik w ramach EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Kwarantanna w operacji EOP](quarantine-email-messages.md).

Jako zwykły użytkownik (nie administrator) **domyślne** możliwości dostępne dla Ciebie jako odbiorca wiadomości poddanej kwarantannie są opisane w poniższej tabeli:

|Przyczyna kwarantanny|Widok|Wydanie|Usuń|
|---|:---:|:---:|:---:|
|**Zasady ochrony przed spamem**||||
|Zbiorczego|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Spam|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Spam o wysokim poziomie ufności|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Wyłudzanie informacji|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Wyłudzanie informacji o dużej pewności||||
|**Zasady ochrony przed wyłudzaniem informacji**||||
|Fałszowanie ochrony inteligencji w ramach EOP|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Personifikowana ochrona użytkownika w Ochrona usługi Office 365 w usłudze Defender|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Ochrona domeny personifikowana w Ochrona usługi Office 365 w usłudze Defender|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Ochrona inteligencji skrzynki pocztowej w Ochrona usługi Office 365 w usłudze Defender|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|**Zasady ochrony przed złośliwym oprogramowaniem**||||
|Wiadomości e-mail z załącznikami, które zostały poddane kwarantannie jako złośliwe oprogramowanie.||||
|**Bezpieczne załączniki w usłudze Defender dla Office 365**||||
|Sejf zasady załączników, które poddają wiadomości e-mail kwarantannie ze złośliwymi załącznikami jako złośliwym oprogramowaniem.||||
|Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams, które poddają kwarantannie złośliwe pliki jako złośliwe oprogramowanie.||||
|**Reguły przepływu poczty e-mail (reguły transportu)**||||
|Reguły przepływu poczty, które poddają kwarantannie wiadomości e-mail.||||

_Zasady kwarantanny_ definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie w oparciu o przyczynę kwarantanny komunikatu w [obsługiwanych funkcjach](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). Domyślne zasady kwarantanny wymuszają możliwości historyczne zgodnie z opisem w poprzedniej tabeli. Administratorzy mogą tworzyć i stosować niestandardowe zasady kwarantanny, które definiują mniej restrykcyjne lub bardziej restrykcyjne możliwości dla użytkowników w obsługiwanych funkcjach. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

Komunikaty poddane kwarantannie można wyświetlać i zarządzać nimi w portalu Microsoft 365 Defender lub (jeśli administrator skonfigurował tę konfigurację) powiadomienia o kwarantannie z zasad kwarantanny.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć portal Microsoft 365 Defender, przejdź do strony <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Kwarantanna** , użyj polecenia <https://security.microsoft.com/quarantine>.

- Administratorzy mogą skonfigurować, jak długo wiadomości są przechowywane w kwarantannie, zanim zostaną trwale usunięte w zasadach ochrony przed spamem. Komunikaty, które wygasły z kwarantanny, są nieodwracalne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

- Domyślnie wiadomości poddane kwarantannie w celu wyłudzania informacji o wysokim poziomie zaufania, złośliwego oprogramowania lub reguł przepływu poczty są dostępne tylko dla administratorów i nie są widoczne dla użytkowników. Aby uzyskać więcej informacji, zobacz [Manage quarantined messages and files as an admin in EOP (Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w ramach EOP](manage-quarantined-messages-and-files.md)).

## <a name="view-your-quarantined-messages"></a>Wyświetlanie komunikatów poddanych kwarantannie

> [!NOTE]
> Możliwość wyświetlania komunikatów poddanych kwarantannie jest kontrolowana przez [zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do typu komunikatu poddanego kwarantannie (co może być [domyślną zasadą kwarantanny z powodu kwarantanny](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Poczta e-mail & współpracy** \> **Przeglądanie** \> **kwarantanny**. Aby przejść bezpośrednio do strony **Kwarantanna** , użyj polecenia <https://security.microsoft.com/quarantine>.

2. Na stronie **Kwarantanna** możesz posortować wyniki, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny**  , aby zmienić wyświetlane kolumny. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

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

   Po zakończeniu kliknij przycisk **Zastosuj**.

3. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym wysuwu Filtry są dostępne następujące **filtry** :
   - **Identyfikator komunikatu**: unikatowy globalnie identyfikator komunikatu.
   - **Adres nadawcy**
   - **Adres odbiorcy**
   - **Temat**
   - **Odebrana godzina**: wprowadź **godzinę rozpoczęcia** i **godzinę zakończenia** (datę).
   - Wygasa: filtruj **komunikaty** według tego, kiedy wygasną po kwarantannie:
     - **Dziś**
     - **Następne 2 dni**
     - **Następne 7 dni**
     - **Niestandardowe**: wprowadź **godzinę rozpoczęcia** i **godzinę zakończenia** (data).
   - **Przyczyna kwarantanny**:
     - **Zbiorczego**
     - **Spam**
     - **Wyłudzanie** informacji: werdykt filtru spamu polegał na tym, że ochrona przed **wyłudzaniem** informacji lub ochrona przed wyłudzaniem informacji została poddana kwarantannie ([ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) lub [ochrona przed personifikacją](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Wyłudzanie informacji o dużej pewności**
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

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić filtry, kliknij ikonę ![Wyczyść filtry.](../../media/m365-cc-sc-clear-filters-icon.png) **Wyczyść filtry**.

4. Użyj pola **wyszukiwania** i odpowiedniej wartości, aby znaleźć określone komunikaty. Symbole wieloznaczne nie są obsługiwane. Możesz wyszukiwać następujące wartości:
   - Identyfikator komunikatu
   - Adres e-mail nadawcy
   - Adres e-mail adresata
   - Temat. Użyj całego tematu wiadomości. Wyszukiwanie nie uwzględnia wielkości liter.
   - Nazwa zasad. Użyj całej nazwy zasad. Wyszukiwanie nie uwzględnia wielkości liter.

   Po wprowadzeniu kryteriów wyszukiwania naciśnij klawisz ENTER, aby odfiltrować wyniki.

Po znalezieniu określonego komunikatu poddanej kwarantannie wybierz komunikat, aby wyświetlić szczegółowe informacje na jego temat i podjąć działania w tej sprawie (na przykład wyświetl, zwolnij, pobierz lub usuń komunikat).

### <a name="view-quarantined-message-details"></a>Wyświetlanie szczegółów komunikatu poddanej kwarantannie

Po wybraniu komunikatu poddanej kwarantannie z listy następujące informacje są dostępne w wyświetlonym wysuwaniu szczegółów.

:::image type="content" source="../../media/quarantine-user-message-details.png" alt-text="Wysuwane szczegóły komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-user-message-details.png":::

Po wybraniu wiadomości e-mail z listy w okienku wysuwanym **Szczegóły** zostaną wyświetlone następujące szczegóły komunikatu:

- **Identyfikator komunikatu**: unikatowy identyfikator globalny komunikatu.
- **Adres nadawcy**
- **Odebrano**: data/godzina odebrania komunikatu.
- **Temat**
- **Przyczyna kwarantanny**
- **Typ zasad**: typ zasad. Na przykład **zasady ochrony przed spamem**.
- **Liczba adresatów**
- **Adresaci**: jeśli wiadomość zawiera wielu adresatów, musisz kliknąć **pozycję Podgląd wiadomości** lub **Wyświetl nagłówek wiadomości** , aby wyświetlić pełną listę adresatów.
- **Wygasa**: data/godzina automatycznego i trwałego usunięcia komunikatu z kwarantanny.

Aby wykonać akcję w komunikacie, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach, ale zmienić wyświetlany komunikat w kwarantannie, użyj strzałek w górę i w dół w górnej części wysuwanego elementu.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Strzałki w górę i w dół w wysuwanym oknie szczegółów komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Podjęcie akcji w wiadomości e-mail poddanej kwarantannie

> [!NOTE]
> Możliwość podjęcia akcji w przypadku komunikatów poddanych kwarantannie jest kontrolowana przez [zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do typu komunikatu poddanego kwarantannie (co może być [domyślną zasadą kwarantanny ze względu na kwarantannę](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)). W tej sekcji opisano wszystkie dostępne akcje.

Po wybraniu komunikatu poddanej kwarantannie z listy w wysuwanym oknie szczegółów są dostępne następujące akcje:

:::image type="content" source="../../media/quarantine-user-message-details-flyout-actions.png" alt-text="Dostępne akcje w wysuwanym oknie wysuwanym szczegółów komunikatu poddanej kwarantannie" lightbox="../../media/quarantine-user-message-details-flyout-actions.png":::

- ![Ikona wiadomości e-mail wydania.](../../media/m365-cc-sc-check-mark-icon.png) **Wiadomość e-mail**<sup>\*</sup> o wersji: dostarcza wiadomość do skrzynki odbiorczej.

- ![Wyświetl ikonę nagłówków komunikatów.](../../media/m365-cc-sc-eye-icon.png) **Wyświetl nagłówki wiadomości**: wybierz ten link, aby wyświetlić tekst nagłówka wiadomości. Wyświetlony **zostanie wysuwany nagłówek komunikatu** z następującymi linkami:
- **Skopiuj nagłówek wiadomości**: kliknij ten link, aby skopiować nagłówek wiadomości (wszystkie pola nagłówka) do schowka.
- **Analizator nagłówków komunikatów firmy Microsoft**: aby dokładnie przeanalizować pola nagłówka i wartości, kliknij ten link, aby przejść do analizatora nagłówków komunikatów. Wklej nagłówek komunikatu do **sekcji Wstawianie nagłówka komunikatu, który chcesz przeanalizować** (CTRL+V lub kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**), a następnie kliknij pozycję **Analizuj nagłówki**.

Następujące akcje są dostępne po kliknięciu ![ikony Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji**:

- ![Ikona podglądu wiadomości.](../../media/m365-cc-sc-eye-icon.png) **Komunikat w wersji zapoznawczej**: W wyświetlonym wysuwie wybierz jedną z następujących kart:
  - **Źródło**: pokazuje wersję HTML treści komunikatu z wyłączonymi wszystkimi linkami.
  - **Zwykły tekst**: pokazuje treść wiadomości w postaci zwykłego tekstu.

- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu komunikat zostanie natychmiast usunięty bez wysyłania do oryginalnych adresatów.

- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobierz wiadomość e-mail**: w wyświetlonym wysuwie wybierz **pozycję Rozumiem ryzyko związane z pobraniem tej wiadomości**, a następnie kliknij pozycję **Pobierz** , aby zapisać lokalną kopię wiadomości w formacie eml.

- ![Ikona blokuj nadawcę.](../../media/m365-cc-sc-block-sender-icon.png) **Blokuj nadawcę**: dodaj nadawcę do listy zablokowanych nadawców w **skrzynce** pocztowej. Aby uzyskać więcej informacji, zobacz [Blokuj nadawcę poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Ta opcja nie jest dostępna w przypadku komunikatów, które zostały już wydane (wartość **Stan wydania** to **Wydano**).

Jeśli nie wydasz lub nie usuniesz komunikatu, zostanie on usunięty po wygaśnięciu domyślnego okresu przechowywania kwarantanny (jak pokazano w kolumnie **Wygasa** ).

> [!NOTE]
> Na urządzeniu przenośnym tekst opisu nie jest dostępny na ikonach akcji.
>
> :::image type="content" source="../../media/quarantine-user-message-details-flyout-mobile-actions.png" alt-text="Szczegóły komunikatu poddanej kwarantannie z wyróżnionymi dostępnymi akcjami" lightbox="../../media/quarantine-user-message-details-flyout-mobile-actions.png":::

>
> Ikony w kolejności i odpowiadające im opisy są podsumowane w poniższej tabeli:
>
> |Ikonę|Opis|
> |---:|---|
> |![Ikona wiadomości e-mail wydania.](../../media/m365-cc-sc-check-mark-icon.png)|**Wiadomość e-mail o wersji**|
> |![Wyświetl ikonę nagłówków komunikatów.](../../media/m365-cc-sc-eye-icon.png)|**Wyświetlanie nagłówków komunikatów**|
> |![Ikona podglądu wiadomości.](../../media/m365-cc-sc-eye-icon.png)|**Komunikat w wersji zapoznawczej**|
> |![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png)|**Usuwanie z kwarantanny**|
> |![Ikona blokuj nadawcę.](../../media/m365-cc-sc-block-sender-icon.png)|**Blokuj nadawcę**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Podjęcie akcji w przypadku wielu wiadomości e-mail z kwarantanną

Po wybraniu wielu komunikatów poddanych kwarantannie na liście (maksymalnie 100), klikając pusty obszar po lewej stronie pierwszej kolumny, zostanie wyświetlona lista rozwijana **Akcje zbiorcze** , na której można wykonać następujące akcje:

:::image type="content" source="../../media/quarantine-user-message-bulk-actions.png" alt-text="Lista rozwijana akcji zbiorczych dla komunikatów w kwarantannie" lightbox="../../media/quarantine-user-message-bulk-actions.png":::

- ![Ikona komunikatów o wersji.](../../media/m365-cc-sc-check-mark-icon.png) **Komunikaty o wersji**: dostarcza komunikaty do skrzynki odbiorczej.
- ![Usuń z ikony kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń komunikaty**: po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeniu komunikaty zostaną natychmiast usunięte z kwarantanny bez wysyłania do oryginalnych adresatów.
