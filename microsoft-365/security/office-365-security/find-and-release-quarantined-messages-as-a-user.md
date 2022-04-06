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
description: Użytkownicy mogą dowiedzieć się, jak wyświetlać wiadomości poddane kwarantannie i zarządzać nimi w Exchange Online Protection (EOP), które powinny zostać do nich dostarczone.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 35aa801d0d981f68de5c62a1928e1f85d82ee95d
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682400"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Znajdowanie i wypuszczenie wiadomości poddanych kwarantannie jako użytkownik w u kontie EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online kwarantanna zawiera potencjalnie niebezpieczne lub niechciane wiadomości. Aby uzyskać więcej informacji, zobacz [Kwarantanna w uchcie eOP](quarantine-email-messages.md).

Jako zwykły użytkownik (nie administrator) domyślne funkcje dostępne  dla Ciebie jako adresata poddaną kwarantannie wiadomości są opisane w poniższej tabeli:

|Powód kwarantanny|Widok|Wydanie|Usuń|
|---|:---:|:---:|:---:|
|**Zasady ochrony przed spamem**||||
|Zbiorcze|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Spam|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Duża pewność, że spam|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Wyłudzanie informacji|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Wyłudzanie informacji o wysokiej pewności||||
|**Zasady ochrony przed wyłudzaniem informacji**||||
|Ochrona przed fałszerami w UOP|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Personifikacja ochrony użytkownika w programie Defender dla Office 365|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Personifikowana ochrona domeny w uchcie Defender dla Office 365|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Ochrona skrzynki pocztowej w uchcie Defender dla Office 365|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|**Zasady ochrony przed złośliwym oprogramowaniem**||||
|Wiadomości e-mail z załącznikami poddanymi kwarantannie jako złośliwe oprogramowanie.||||
|**Sejf załączników w programie Defender dla Office 365**||||
|Sejf załączników, które poddasz wiadomościom e-mail ze złośliwymi załącznikami jako złośliwe oprogramowanie.||||
|Sejf załączników do SharePoint, OneDrive i Microsoft Teams, które poddasz kwarantannie złośliwe pliki jako złośliwe oprogramowanie.||||
|**Reguły przepływu poczty (reguły transportu)**||||
|Reguły przepływu poczty e-mail służące do kwarantanny wiadomości e-mail.||||

_Zasady kwarantanny_ określają, co użytkownicy mogą robić w kwarantannie wiadomości na podstawie przyczyny kwarantanny wiadomości w [obsługiwanych funkcjach](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). Domyślne zasady kwarantanny wymuszają funkcje historyczne zgodnie z opisem w poprzedniej tabeli. Administratorzy mogą tworzyć i stosować niestandardowe zasady kwarantanny definiujące mniej restrykcyjne lub bardziej restrykcyjne funkcje dla użytkowników korzystających z obsługiwanych funkcji. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

W portalu poczty usługi Microsoft 365 Defender można wyświetlać wiadomości poddane kwarantannie i zarządzać nimi lub (jeśli administrator schował tę pozycję) powiadomieniami kwarantanny z zasad kwarantanny.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć Microsoft 365 Defender, przejdź do .<https://security.microsoft.com> Aby przejść bezpośrednio do strony **kwarantanny**, użyj .<https://security.microsoft.com/quarantine>

- Administratorzy mogą określić, jak długo wiadomości są przechowywane w kwarantannie, zanim zostaną trwale usunięte w zasadach ochrony przed spamem. Wiadomości, które wygasły z kwarantanny, nie można ich użyć. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

- Domyślnie wiadomości poddane kwarantannie w celu wyłudzania informacji o dużej pewności, złośliwego oprogramowania lub reguł przepływu poczty są dostępne tylko dla administratorów i nie są widoczne dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zarządzanie poddatymi wiadomościami i plikami jako administrator w u usługi EOP](manage-quarantined-messages-and-files.md).

## <a name="view-your-quarantined-messages"></a>Wyświetlanie wiadomości poddanych kwarantannie

> [!NOTE]
> Możliwość wyświetlania poddanych kwarantannie wiadomości jest kontrolowana przez zasady kwarantanny, które dotyczą typu wiadomości poddanych kwarantannie (które mogą być domyślnymi zasadami kwarantanny z powodu [kwarantanny](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)).[](quarantine-policies.md)

1. W portalu Microsoft 365 Defender pod adresem  <https://security.microsoft.com>, przejdź do tematu Przeglądanie **& poczty e-mail** \> **.**\> Aby przejść bezpośrednio do strony **kwarantanny**, użyj .<https://security.microsoft.com/quarantine>

2. Na stronie **Kwarantanna** możesz posortować wyniki, klikając dostępny nagłówek kolumny. Kliknij **pozycję Dostosuj kolumny**  , aby zmienić wyświetlane kolumny. Wartości domyślne są oznaczone gwiazdką (<sup>\*</sup>):

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

   Po zakończeniu kliknij przycisk **Zastosuj**.

3. Aby filtrować wyniki, kliknij pozycję **Filtruj**. W wyświetlonym **wysuwanych filtrach** są dostępne następujące filtry:
   - **Identyfikator wiadomości**: unikatowy identyfikator globalny wiadomości.
   - **Adres nadawcy**
   - **Adres adresata**
   - **Temat**
   - **Godzina odebrana**: Wprowadź czas **rozpoczęcia i** **czas zakończenia** (datę).
   - **Wygasa:** Filtruj wiadomości według tego, kiedy wygasną z kwarantanny:
     - **Dzisiaj**
     - **Następne 2 dni**
     - **Następne 7 dni**
     - **Niestandardowe**: Wprowadź czas **rozpoczęcia i** **czas zakończenia** (datę).
   - **Powód kwarantanny**:
     - **Zbiorcze**
     - **Spam**
     - **Wyłudzanie** informacji: Werdykt filtru spamu **był w** kwarantannie przed wyłudzaniem informacji lub ochrony przed wyłudzaniem informacji ([ustawienia spoof lub](set-up-anti-phishing-policies.md#spoof-settings) [ochrona przed personifikacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Wyłudzanie informacji o wysokiej pewności**
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

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić filtry, kliknij ikonę ![Wyczyść filtry.](../../media/m365-cc-sc-clear-filters-icon.png) **Wyczyść filtry**.

4. Użyj **pola** wyszukaj i odpowiadającej mu wartości, aby znaleźć określone wiadomości. Symbole wieloznaczne nie są obsługiwane. Możesz wyszukiwać według następujących wartości:
   - Identyfikator wiadomości
   - Adres e-mail nadawcy
   - Adres e-mail adresata
   - Temat. Użyj całego tematu wiadomości. W wyszukiwaniu nie jest wróżniana wielkość liter.
   - Nazwa zasad. Użyj całej nazwy zasad. W wyszukiwaniu nie jest wróżniana wielkość liter.

   Po wprowadzeniu kryteriów wyszukiwania naciśnij klawisz ENTER, aby przefiltrować wyniki.

Po odnalezieniu określonej wiadomości poddanej kwarantannie zaznacz ją, aby wyświetlić szczegółowe informacje i podjąć w związku z tym działanie (na przykład wyświetlanie, zwalnianie, pobieranie lub usuwanie wiadomości).

### <a name="view-quarantined-message-details"></a>Wyświetlanie szczegółów wiadomości poddanych kwarantannie

Po wybraniu z listy wiadomości poddanej kwarantannie w wysuwanych szczegółach są dostępne następujące informacje.

![Wysuw szczegółów wiadomości poddanej kwarantannie.](../../media/quarantine-user-message-details.png)

Po zaznaczeniu wiadomości e-mail na liście w wysuwanych okienku Szczegóły są **wyświetlane następujące szczegóły** wiadomości:

- **Identyfikator wiadomości**: unikatowy identyfikator globalny wiadomości.
- **Adres nadawcy**
- **Otrzymano**: data/godzina otrzymania wiadomości.
- **Temat**
- **Powód kwarantanny**
- **Typ zasad**: Typ zasad. Na przykład zasady **ochrony przed spamem**.
- **Liczba adresatów**
- **Adresaci**: Jeśli wiadomość zawiera wielu adresatów, należy kliknąć pozycję Podgląd  wiadomości lub Wyświetl  nagłówek wiadomości, aby wyświetlić pełną listę adresatów.
- **Wygasa:** Data/godzina, kiedy wiadomość zostanie automatycznie i trwale usunięta z kwarantanny.

Aby podjąć działanie w związku z wiadomością, zobacz następną sekcję.

> [!NOTE]
> Aby pozostać w wysuwanych szczegółach, ale zmienić obecnie poddaną kwarantannie wiadomość, użyj strzałek w górę i w dół u góry wysuwanych.
>
> ![Strzałki w górę i w dół w wysuwanych szczegółach wiadomości poddanej kwarantannie.](../../media/quarantine-message-details-flyout-up-down-arrows.png)

### <a name="take-action-on-quarantined-email"></a>Działania w przypadku poddanych kwarantannie wiadomości e-mail

> [!NOTE]
> Możliwość wykonywania działań w przypadku wiadomości poddanych kwarantannie jest kontrolowana przez [](quarantine-policies.md) zasady kwarantanny, które dotyczą typu wiadomości poddanych kwarantannie (które mogą być domyślnymi zasadami kwarantanny z powodu [kwarantanny](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)). W tej sekcji opisano wszystkie dostępne akcje.

Po wybraniu poddaną kwarantannie wiadomości z listy w wysuwanych szczegółach są dostępne następujące akcje:

![Dostępne akcje w wysuwanych szczegółach wiadomości poddanej kwarantannie.](../../media/quarantine-user-message-details-flyout-actions.png)

- ![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png) **Zwolnij wiadomość e-mail**<sup>\*</sup>: Dostarcza wiadomość do skrzynki odbiorczej.

- ![Wyświetl ikonę nagłówków wiadomości.](../../media/m365-cc-sc-eye-icon.png) **Wyświetlanie nagłówków wiadomości**: Wybierz ten link, aby wyświetlić tekst nagłówka wiadomości. Zostanie **wyświetlone okno wysuwu** nagłówka wiadomości z następującymi linkami:
- **Kopiowanie nagłówka wiadomości**: kliknij ten link, aby skopiować nagłówek wiadomości (wszystkie pola nagłówka) do Schowka.
- **Analizator nagłówka wiadomości firmy Microsoft**: aby szczegółowo przeanalizować pola i wartości nagłówka, kliknij ten link, aby przejść do Analizatora nagłówka wiadomości. Wklej nagłówek wiadomości w sekcji Wstaw  nagłówek wiadomości, który chcesz przeanalizować (naciśnij klawisze CTRL+V lub kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej), a** następnie kliknij pozycję **Analizuj nagłówki**.

Po kliknięciu ikony Więcej akcji są ![dostępne następujące akcje.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji**:

- ![Ikona podglądu wiadomości.](../../media/m365-cc-sc-eye-icon.png) **Podgląd wiadomości**: W wyświetlonym wysuwanych oknach wybierz jedną z następujących kart:
  - **Źródło**: wyświetla wersję HTML treści wiadomości z wyłączonymi wszystkimi linkami.
  - **Zwykły tekst**: wyświetla treść wiadomości w formacie zwykłego tekstu.

- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuń z kwarantanny**: Po kliknięciu przycisku **Tak** w wyświetlonym komunikacie ostrzegawczym wiadomość zostanie natychmiast usunięta bez wysłania do oryginalnych adresatów.

- ![Ikona pobierania wiadomości e-mail.](../../media/m365-cc-sc-download-icon.png) **Pobierz wiadomość e-mail**: W wyświetlonym wysuwanym czacie wybierz pozycję Rozumiem zagrożenia związane z pobieraniem tej  **wiadomości, a** następnie kliknij przycisk Pobierz, aby zapisać kopię lokalną wiadomości w formacie eml.

- ![Ikona Blokowania nadawcy.](../../media/m365-cc-sc-block-sender-icon.png) **Blokowanie nadawcy**: Dodaj nadawcę do listy zablokowanych nadawców w **skrzynce pocztowej** . Aby uzyskać więcej informacji, zobacz [Blokowanie nadawcy poczty](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Ta opcja nie jest dostępna w przypadku wiadomości, które zostały już wydane (wartość **stanu** Wydana została **wydana**).

Jeśli nie zwolnisz lub nie usuniesz wiadomości, zostanie ona usunięta po upływie domyślnego okresu przechowywania kwarantanny (jak pokazano w **kolumnie Wygasa** ).

> [!NOTE]
> Na urządzeniach przenośnych tekst opisu nie jest dostępny na ikonach akcji.
>
> ![Szczegóły wiadomości poddanej kwarantannie z wyróżniona dostępnymi akcjami.](../../media/quarantine-user-message-details-flyout-mobile-actions.png)
>
> Ikony w kolejności i odpowiadające im opisy są podsumowywane w poniższej tabeli:
>
> |Ikona|Opis|
> |---:|---|
> |![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png)|**Wiadomość e-mail o wersji**|
> |![Wyświetl ikonę nagłówków wiadomości.](../../media/m365-cc-sc-eye-icon.png)|**Wyświetlanie nagłówków wiadomości**|
> |![Ikona podglądu wiadomości.](../../media/m365-cc-sc-eye-icon.png)|**Podgląd wiadomości**|
> |![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png)|**Usuwanie z kwarantanny**|
> |![Ikona Blokowania nadawcy.](../../media/m365-cc-sc-block-sender-icon.png)|**Blokowanie nadawcy**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Działanie w przypadku wielu poddanych kwarantannie wiadomości e-mail

Po zaznaczeniu wielu poddanych kwarantannie wiadomości na liście (maksymalnie 100) przez kliknięcie pustego obszaru z lewej strony pierwszej kolumny zostanie wyświetlona lista rozwijana Akcje zbiorcze, na której możesz podjąć następujące czynności:

![Lista rozwijana akcji zbiorczych dla wiadomości poddanych kwarantannie.](../../media/quarantine-user-message-bulk-actions.png)

- ![Ikona zwolnienia wiadomości e-mail.](../../media/m365-cc-sc-check-mark-icon.png) **Release messages**: Delivers the messages to your Inbox.
- ![Ikona Usuń z kwarantanny.](../../media/m365-cc-sc-delete-icon.png) **Usuwanie wiadomości**: Po kliknięciu przycisku **Tak** w wyświetlonym ostrzeżeń wiadomości są natychmiast usuwane z kwarantanny, a nie wysyłane do oryginalnych adresatów.
