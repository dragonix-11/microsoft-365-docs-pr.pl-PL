---
title: Strony logowania w szkoleniu z symulacji ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak tworzyć strony logowania i zarządzać nimi w przypadku symulowanych ataków wyłudzania informacji w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2.
ms.technology: mdo
ms.openlocfilehash: 5ecbdddfff4d528c1af8e20cf4d3831d3250eacc
ms.sourcegitcommit: 03543c27c33427ac7f11af4c04fff35a181a2524
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66609290"
---
# <a name="login-pages-in-attack-simulation-training"></a>Strony logowania w szkoleniu z symulacji ataków

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Podczas trenowania symulacji ataków w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2 strony logowania są wyświetlane użytkownikom w symulacjach korzystających z **zbioru poświadczeń** i **linku w** [technikach inżynierii społecznej](attack-simulation-training.md#select-a-social-engineering-technique) załączników.

Aby wyświetlić dostępne strony logowania, otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do karty \> Biblioteka **zawartości Symulacja** **symulacji symulacji** \> ataków & **współpracy** \> pocztą e-mail, a następnie wybierz pozycję **Strony logowania**. Aby przejść bezpośrednio do karty **Biblioteka zawartości symulacji** , na której można wybrać pozycję **Strony logowania**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Strony logowania** mają dwie karty:

- **Globalne strony logowania**: zawiera wbudowane, nie modyfikowalne strony logowania. Istnieją cztery wbudowane strony logowania zlokalizowane w ponad 12 językach:
  - **Strona logowania w usłudze GitHub**
  - **Strona logowania linkedin**
  - **Strona logowania firmy Microsoft**
  - **Strona logowania bez marki**

- **Strony logowania dzierżawy**: zawiera utworzone niestandardowe strony logowania.

Dla każdej strony logowania są wyświetlane następujące informacje:

- **Nazwa**
- **Język**
- **Źródło**: W przypadku wbudowanych stron logowania wartość to **Globalna**. W przypadku niestandardowych stron logowania wartość to **Dzierżawa**.
- **Stan**: **Gotowe** lub **wersje robocze**.
- **Utworzone przez**: w przypadku wbudowanych stron logowania wartość to **Microsoft**. W przypadku niestandardowych stron logowania wartość to nazwa UPN użytkownika, który utworzył stronę logowania.
- **Ostatnia modyfikacja**

Aby znaleźć stronę logowania na liście, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia nazwy strony logowania.

Kliknij ikonę ![Filtruj.](../../media/m365-cc-sc-filter-icon.png) **Filtruj** , aby filtrować strony logowania według **języka** lub **stanu**.

Aby usunąć co najmniej jedną wyświetlaną kolumnę, kliknij pozycję Dostosuj ikonę ![kolumn.](../../media/m365-cc-sc-customize-icon.png) **Dostosowywanie kolumn**.

Po wybraniu strony logowania z listy zostanie wyświetlone okno wysuwane szczegóły z następującymi informacjami:

- ![Ikona edycji.](../../media/m365-cc-sc-edit-icon.png) **Edycja** jest dostępna tylko na niestandardowych stronach logowania na karcie **Strony logowania dzierżawy** .
- ![Oznacz jako ikonę domyślną.](../../media/m365-cc-sc-set-as-default-icon.png) **Oznacz jako domyślny** , aby ta strona logowania była domyślnym wyborem w obszarze **Zbieranie poświadczeń** lub **Łącze w** [ładunkach załączników](attack-simulation-training-payloads.md) lub [automatyzacjach ładunków](attack-simulation-training-payload-automations.md). Jeśli strona logowania jest już domyślna, ![oznacz jako ikonę domyślną.](../../media/m365-cc-sc-set-as-default-icon.png) **Oznacz jako domyślne** jest niedostępne.
- Karta **Podgląd**: wyświetl stronę logowania, gdy użytkownicy ją zobaczą. **Linki strony 1** i **strony 2** są dostępne w dolnej części strony dla dwustronicowych stron logowania.
- Karta **Szczegóły**: wyświetl szczegóły dotyczące strony logowania:
  - **Opis**
  - **Stan**: **Gotowe** lub **wersje robocze**.
  - **Źródło strony logowania**: w przypadku wbudowanych stron logowania wartość to **Globalna**. W przypadku niestandardowych stron logowania wartość to **Dzierżawa**.
  - **Zmodyfikowane przez**
  - **Język**
  - **Ostatnia modyfikacja**

## <a name="create-login-pages"></a>Tworzenie stron logowania

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do karty \> Biblioteka **zawartości symulacji**  \> & **poczty e-mail**\>, a następnie wybierz pozycję **Strony logowania**. Aby przejść bezpośrednio do karty **Biblioteka zawartości symulacji** , na której można wybrać pozycję **Strony logowania**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.
Niestandardowe strony logowania można tworzyć w następujących lokalizacjach:

   Kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową,** aby uruchomić kreatora tworzenia strony logowania użytkownika końcowego.

   > [!NOTE]
   > Ikona ![Utwórz nową.](../../media/m365-cc-sc-create-icon.png) **Tworzenie nowych** jest również dostępne podczas kroku wyboru ładunku podczas tworzenia symulacji. Aby uzyskać więcej informacji, zobacz [Simulate a phishing attack with Attack simulation training in Ochrona usługi Office 365 w usłudze Defender (Symulowanie ataku wyłudzania informacji przy użyciu trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md)).
   >
   > W dowolnym momencie kreatora tworzenia można kliknąć przycisk **Zapisz i zamknąć** , aby zapisać postęp i kontynuować konfigurowanie strony logowania później. Możesz wybrać miejsce, w którym zostało przerwane, wybierając stronę logowania na karcie **Strony logowania dzierżawy** na **stronach logowania**, a następnie klikając ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**. Częściowo ukończona strona logowania będzie mieć wartość **Stan** **— wersja robocza**.

2. Na **stronie Definiowanie szczegółów logowania** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową nazwę.
   - **Opis**: wprowadź opcjonalny opis.

   Po zakończeniu kliknij przycisk **Dalej**.

3. Na **stronie Konfigurowanie logowania** skonfiguruj następujące ustawienia:

   - **Wybierz język**: Dostępne wartości to: **chiński (uproszczony),** **chiński (tradycyjny),** **angielski**, **francuski**, **niemiecki**, **włoski**, **japoński**, **koreański**, **portugalski**, **rosyjski**, **hiszpański** i **holenderski**.

   - **Ustaw tę domyślną stronę logowania**: jeśli wybierzesz tę opcję, strona logowania będzie domyślnym wyborem w obszarze **Zbieranie poświadczeń** lub **Link w** [ładunkach załączników](attack-simulation-training-payloads.md) lub [automatyzacjach ładunków](attack-simulation-training-payload-automations.md).

   - **Utwórz dwustronicowe logowanie**: jeśli nie wybierzesz tej opcji, strona logowania to jedna strona. Jeśli wybierzesz tę opcję, zostaną wyświetlone karty **Strona 1** i **Strona 2** , aby skonfigurować je oddzielnie.

     - Na karcie **Tekst** możesz utworzyć stronę logowania za pomocą edytora tekstów sformatowanych.

       - Użyj kontrolki **Tag dynamiczny** , aby dostosować stronę logowania, wstawiając dostępne tagi:
         - **Wstaw nazwę użytkownika**: wartość dodana w treści komunikatu to `${userName}`.
         - **Wstaw wiadomość e-mail**: wartość dodana w treści wiadomości to `${emailAddress}`.
         - **Wstaw datę**: wartość dodana w treści komunikatu to `${date|MM/dd/yyyy|offset}`.

       - Użyj kontrolki **Użyj z domyślnej** , aby wybrać wbudowaną stronę logowania, aby rozpocząć od szablonu.

       - Kontrolka **Przycisk Dodaj dalej** jest dostępna tylko na **stronie 1** z dwustronicowymi identyfikatorami logowania. Domyślny tekst na przycisku to **Dalej** , ale można go zmienić.

       - Kontrolka **Dodaj przycisk naruszenia** zabezpieczeń dostępna na jednostronicowych logowaniach lub na **stronie 2** logowania dwustronicowego. Domyślny tekst na przycisku to **Prześlij**, ale możesz go zmienić.

     - Na karcie **Kod** można bezpośrednio wyświetlać i modyfikować kod HTML. Formatowanie i inne kontrolki, takie jak **tag dynamiczny** i **Użyj od domyślnego** lub **Dodaj przycisk naruszenia zabezpieczeń** , nie są dostępne.

   - Użyj przycisku **Podgląd strony logowania** w górnej części strony, aby przejrzeć stronę logowania.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na **stronie Przeglądanie logowania** możesz przejrzeć szczegóły strony logowania.

   W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

5. Na **utworzonej stronie Nowa strona \<Name\> logowania** możesz użyć linków, aby utworzyć nową stronę logowania, uruchomić symulację lub wyświetlić wszystkie strony logowania.

   Po zakończeniu kliknij pozycję **Gotowe**.

Na karcie **Strony logowania dzierżawy** na **stronach logowania** utworzona strona logowania jest teraz wyświetlana.

## <a name="modify-login-pages"></a>Modyfikowanie stron logowania

Na karcie **Globalne strony logowania** nie można modyfikować wbudowanych stron logowania. Niestandardowe strony logowania można modyfikować tylko na karcie **Strony logowania dzierżawy** .

Aby zmodyfikować istniejącą niestandardową stronę logowania na karcie **Strony logowania dzierżawy** , wykonaj jedną z następujących czynności:

- Wybierz stronę logowania z listy, klikając pole wyboru. Kliknij ikonę Edytuj ![.](../../media/m365-cc-sc-edit-icon.png) **Wyświetlona ikona edycji** .
- Kliknij **pozycję ⋮** (**Akcje**) między wartościami **Nazwa** i **Język** na stronie logowania na liście, a następnie wybierz pozycję Edytuj ikonę ![.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.
- Wybierz stronę logowania z listy, klikając nazwę. W wyświetlonym wysuwu szczegółów kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.

Zostanie otwarty kreator strony logowania z ustawieniami i wartościami wybranej strony logowania. Kroki są takie same, jak opisano w sekcji [Tworzenie stron logowania](#create-login-pages) .

## <a name="copy-login-pages"></a>Kopiowanie stron logowania

Aby skopiować istniejącą stronę logowania na **stronach logowania dzierżawy** lub na kartach **Globalne strony logowania** , wykonaj jedną z następujących czynności:

- Wybierz stronę logowania z listy, klikając pole wyboru, a następnie kliknij ikonę ![Utwórz kopię.](../../media/m365-cc-sc-edit-icon.png) **Utwórz wyświetloną ikonę kopiowania** .
- Kliknij **pozycję ⋮** (**Akcje**) między wartościami **Nazwa** i **Język** na stronie logowania na liście, a następnie wybierz pozycję ![Utwórz ikonę kopiowania.](../../media/m365-cc-sc-edit-icon.png) **Utwórz kopię**.

Zostanie otwarty kreator strony logowania z ustawieniami i wartościami wybranej strony logowania. Kroki są takie same, jak opisano w sekcji [Tworzenie stron logowania](#create-login-pages) .

> [!NOTE]
> Podczas kopiowania wbudowanej strony logowania na karcie **Globalne strony logowania** należy zmienić wartość **Nazwa** . Ten krok gwarantuje zapisanie kopii jako niestandardowej strony logowania na karcie **Strony logowania dzierżawy** .
>
> Kontrolka **Użyj z domyślnej** na **stronie Konfigurowanie logowania** w kreatorze strony logowania umożliwia skopiowanie zawartości wbudowanej strony logowania.

## <a name="remove-login-pages"></a>Usuwanie stron logowania

Nie można usunąć wbudowanych stron logowania z karty **Globalne strony logowania** . Niestandardowe strony logowania można usuwać tylko na karcie **Strony logowania dzierżawy** .

Aby usunąć istniejącą niestandardową stronę logowania na karcie **Strony logowania dzierżawy** , wykonaj jedną z następujących czynności:

- Wybierz stronę logowania z listy, klikając pole wyboru, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Ikona usuwania** , która zostanie wyświetlona.
- Kliknij **pozycję ⋮** (**Akcje**) między wartościami **Nazwa** i **Język** na stronie logowania na liście, a następnie wybierz pozycję Usuń ikonę ![.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

## <a name="make-a-login-page-the-default"></a>Ustaw domyślną stronę logowania

Domyślna strona logowania to domyślny wybór używany w obszarze **Zbieranie poświadczeń** lub **Link w** [ładunkach załączników](attack-simulation-training-payloads.md) lub [automatyzacjach ładunków](attack-simulation-training-payload-automations.md).

Aby ustawić domyślną stronę logowania na **stronach logowania dzierżawy** lub globalnych **stronach logowania** , wykonaj jedną z następujących czynności:

- Wybierz stronę logowania z listy, klikając pole wyboru. Kliknij ikonę ![Oznacz jako domyślną.](../../media/m365-cc-sc-set-as-default-icon.png) **Oznacz jako wyświetloną ikonę domyślną** .
- Kliknij **pozycję ⋮** (**Akcje**) między wartościami **Nazwa** i **Język** na stronie logowania na liście, a następnie wybierz pozycję ![Oznacz jako ikonę domyślną.](../../media/m365-cc-sc-set-as-default-icon.png) **Oznacz jako domyślne**.
- Wybierz stronę logowania z listy, klikając nazwę. W wyświetlonym wysuwu szczegółów kliknij pozycję ![Oznacz jako ikonę domyślną.](../../media/m365-cc-sc-set-as-default-icon.png) **Oznacz jako domyślne**.
- Wybierz pozycję **Ustaw domyślną stronę logowania** na **stronie Konfigurowanie logowania** w kreatorze podczas [tworzenia lub modyfikowania strony logowania](#create-login-pages).

> [!NOTE]
> Poprzednie procedury nie są dostępne, jeśli strona logowania jest już domyślna.
>
> Domyślna strona logowania jest również oznaczona na liście, chociaż może być konieczne rozszerzenie kolumny **Nazwa** , aby ją wyświetlić:
>
> ![Domyślna strona logowania oznaczona na liście stron logowania w trenowaniu symulacji ataku.](../../media/attack-sim-training-login-pages-default.png)

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

[Tworzenie symulacji ataku wyłudzania informacji](attack-simulation-training.md)

[Automatyzacje symulacji na potrzeby trenowania symulacji ataków](attack-simulation-training-simulation-automations.md)
