---
title: Ochrona przed zagrożeniami w Ochrona usługi Office 365 w usłudze Microsoft Defender, ochrona przed złośliwym oprogramowaniem, ochrona przed wyłudzaniem informacji, ochrona przed spamem, linki Sejf, załączniki Sejf, automatyczne przeczyszczanie (ZAP), konfiguracja zabezpieczeń MDO
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
ms.date: 06/22/2021
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się więcej o ochronie przed zagrożeniami w Microsoft 365 i skonfigurować sposób jej używania w organizacji.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d067035d5eaf3c7a4febac6feeab0c56cd707728
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941440"
---
# <a name="protect-against-threats"></a>Ochrona przed zagrożeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Oto przewodnik szybkiego startu, który dzieli konfigurację Ochrona usługi Office 365 w usłudze Defender na fragmenty. Jeśli dopiero zaczynasz korzystać z funkcji ochrony przed zagrożeniami w Office 365, nie wiesz, od czego zacząć lub jeśli najlepiej się z *tego* nauczysz, skorzystaj z tych wskazówek jako listy kontrolnej i punktu początkowego.

> [!IMPORTANT]
> **Początkowe zalecane ustawienia są uwzględniane dla każdego rodzaju zasad, jednak dostępnych jest wiele opcji i można dostosować ustawienia zgodnie z potrzebami określonej organizacji**. Zaczekaj około 30 minut na pracę zasad lub zmian w centrum danych.
>
> Aby pominąć ręczną konfigurację większości zasad w Ochrona usługi Office 365 w usłudze Defender, możesz użyć wstępnie ustawionych zasad zabezpieczeń na poziomie standardowym lub ścisłym. Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

## <a name="requirements"></a>Wymagania

### <a name="subscriptions"></a>Subskrypcji

Funkcje ochrony przed zagrożeniami są dostępne we *wszystkich* subskrypcjach firmy Microsoft lub Office 365; jednak niektóre subskrypcje mają zaawansowane funkcje. W poniższej tabeli wymieniono funkcje ochrony zawarte w tym artykule wraz z minimalnymi wymaganiami dotyczącymi subskrypcji.

> [!TIP]
> Zwróć uwagę, że poza kierunkami włączania inspekcji należy rozpocząć *działania* chroniące przed złośliwym oprogramowaniem, wyłudzaniem informacji i antyspamowe, które są oznaczone jako część Office 365 Exchange Online Protection (**EOP**). To może wydawać się dziwne w artykule Ochrona usługi Office 365 w usłudze Defender, dopóki nie pamiętasz (**Ochrona usługi Office 365 w usłudze Defender**) zawiera i opiera się na EOP.

|Typ ochrony|Wymaganie subskrypcji|
|---|---|
|Rejestrowanie inspekcji (do celów raportowania)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Ochrona przed złośliwym oprogramowaniem|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Ochrona przed wyłudzaniem informacji|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Ochrona przed spamem|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Ochrona przed złośliwymi adresami URL i plikami w wiadomościach e-mail i dokumentach Office (linki Sejf i załączniki Sejf)|[Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Role i uprawnienia

Aby skonfigurować zasady Ochrona usługi Office 365 w usłudze Defender, musisz mieć przypisaną odpowiednią rolę. Zapoznaj się z poniższą tabelą, aby zapoznać się z rolami, które mogą wykonywać te akcje.

|Rola lub grupa ról|Gdzie dowiedzieć się więcej|
|---|---|
|administrator globalny|[Informacje o rolach administratora Microsoft 365](../../admin/add-users/about-admin-roles.md)|
|Administrator zabezpieczeń|[Wbudowane role usługi Azure AD](/azure/active-directory/roles/permissions-reference#security-administrator)
|zarządzanie organizacją Exchange Online|[Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo)|

Aby dowiedzieć się więcej, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Włączanie rejestrowania inspekcji na potrzeby raportowania i badania

- Rozpocznij rejestrowanie inspekcji wcześnie. Inspekcja musi być **włączona** , aby wykonać niektóre z poniższych kroków. Rejestrowanie inspekcji jest dostępne w subskrypcjach, które obejmują [Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Aby można było wyświetlać dane w raportach ochrony przed zagrożeniami, [raportach zabezpieczeń poczty e-mail](view-email-security-reports.md) i [Eksploratorze](threat-explorer.md), rejestrowanie inspekcji musi być *włączone*. Aby dowiedzieć się więcej, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Część 1 — Ochrona przed złośliwym oprogramowaniem w ramach EOP

Aby uzyskać więcej informacji na temat zalecanych ustawień ochrony przed złośliwym oprogramowaniem, zobacz [Ustawienia zasad ochrony przed złośliwym oprogramowaniem EOP](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Otwórz stronę **Ochrona przed złośliwym oprogramowaniem** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/antimalwarev2>.

2. Na stronie **Ochrona przed złośliwym oprogramowaniem** wybierz zasady o nazwie **Domyślne (domyślne),** klikając nazwę.

3. W wyświetlonym wysuwu szczegółów zasad kliknij pozycję **Edytuj ustawienia ochrony**, a następnie skonfiguruj następujące ustawienia:
   - Sekcja **Ustawień ochrony**:
     - **Włącz filtr typowych załączników**: Wybierz (włącz). Kliknij **pozycję Dostosuj typy plików** , aby dodać więcej typów plików.
     - **Włącz automatyczne przeczyszczanie bez godziny dla złośliwego oprogramowania**: sprawdź, czy to ustawienie jest zaznaczone. Aby uzyskać więcej informacji na temat zap dla złośliwego oprogramowania, zobacz [Zero godzin auto przeczyszczania (ZAP) dla złośliwego oprogramowania](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware).
   - **Zasady kwarantanny**: pozostaw wybraną wartość domyślną AdminOnlyAccessPolicy. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
   - Sekcja **powiadomień**: sprawdź, czy nie wybrano żadnych ustawień powiadomień.

   Po zakończeniu kliknij przycisk **Zapisz**.

4. Po powrocie do wysuwanego szczegółów zasad kliknij przycisk **Zamknij**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed złośliwym oprogramowaniem, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w usłudze EOP](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Część 2 — Ochrona przed wyłudzaniem informacji w ramach EOP i Ochrona usługi Office 365 w usłudze Defender

[Ochrona przed wyłudzaniem informacji](anti-phishing-protection.md) jest dostępna w subskrypcjach obejmujących [operacje EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Zaawansowana ochrona przed wyłudzaniem informacji jest dostępna w [Ochrona usługi Office 365 w usłudze Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Aby uzyskać więcej informacji na temat zalecanych ustawień zasad ochrony przed wyłudzaniem informacji, zobacz [Ustawienia zasad ochrony przed wyłudzaniem informacji](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) i [Ustawienia zasad ochrony przed wyłudzaniem informacji w usłudze Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

W poniższej procedurze opisano sposób konfigurowania domyślnych zasad ochrony przed wyłudzaniem informacji. Ustawienia dostępne tylko w Ochrona usługi Office 365 w usłudze Defender są wyraźnie oznaczone.

1. Otwórz stronę **Ochrona przed wyłudzaniem informacji** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** wybierz zasady o nazwie **Office365 AntiPhish Default (domyślnie),** klikając nazwę.

3. W wyświetlonym oknie wysuwowym szczegółów zasad skonfiguruj następujące ustawienia:
   - **Próg wyłudzania informacji & sekcji ochrony** : Kliknij pozycję **Edytuj ustawienia ochrony** i skonfiguruj następujące ustawienia w otwierającym się wysuwie:
     - **Próg wiadomości e-mail wyłudzającej informacje**: wybierz **pozycję 2 — agresywne** (standardowe) lub **3 — bardziej agresywne** (ścisłe).<sup>\*</sup>
     - Sekcja <sup>\*</sup> **personifikacji**: Skonfiguruj następujące wartości:
       - Wybierz pozycję **Włącz użytkowników do ochrony**, kliknij wyświetlony link **Zarządzaj nadawcami (nn** ), a następnie dodaj wewnętrznych i zewnętrznych nadawców w celu ochrony przed personifikacją, takimi jak członkowie zarządu organizacji, dyrektor generalny, dyrektor finansowy i inni starsi liderzy.
       - Wybierz pozycję **Włącz domeny do ochrony**, a następnie skonfiguruj następujące wyświetlane ustawienia:
         - Wybierz **pozycję Dołącz domeny, których jestem właścicielem** , aby chronić wewnętrznych nadawców w zaakceptowanych domenach (widocznych przez kliknięcie pozycji **Wyświetl moje domeny**) przed personifikacją.
         - Aby chronić nadawców w innych domenach, wybierz pozycję **Dołącz domeny niestandardowe**, kliknij wyświetlony link **Zarządzaj domenami niestandardowymi (nn** ), a następnie dodaj inne domeny w celu ochrony przed personifikacją.
     - Sekcja <sup>\*</sup> **Dodawanie zaufanych nadawców i domen**: kliknij pozycję **Zarządzaj (nn) zaufanymi nadawcami i domenami**, aby skonfigurować wyjątki domeny nadawcy i nadawcy do ochrony przed personifikacją w razie potrzeby.
     - Ustawienia <sup>\*</sup> analizy skrzynki pocztowej: sprawdź, czy **wybrano opcje Włącz analizę skrzynki pocztowej** i **Włącz analizę pod kątem ochrony przed personifikacją** .
     - Sekcja **Fałszowanie**: sprawdź, czy **wybrano opcję Włącz analizę fałszowania**.

     Po zakończeniu kliknij przycisk **Zapisz**.

   - Sekcja **Akcje**: Kliknij pozycję **Edytuj akcje** i skonfiguruj następujące ustawienia w wyświetlonym wysuwie:
     - Sekcja **Akcje komunikatu**: Skonfiguruj następujące ustawienia:
       - **Jeśli komunikat zostanie wykryty jako personifikowany użytkownik**<sup>\*</sup>: wybierz pozycję **Kwarantanna komunikatu**. Zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym [wybierzesz zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed personifikacją użytkowników.
       - **Jeśli komunikat zostanie wykryty jako domena personifikowana**: wybierz pozycję **Kwarantanna komunikatu**.<sup>\*</sup> Zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym [wybierzesz zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed personifikacją domeny.
       - **Jeśli analiza skrzynki pocztowej wykryje personifikowanego użytkownika**<sup>\*</sup>: wybierz pozycję **Przenieś wiadomość do folderów Wiadomości-śmieci adresatów** (Standardowa) lub **Kwarantanna wiadomości** (ścisła). Jeśli **wybierzesz pozycję Kwarantanna wiadomości**, zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz [zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do wiadomości, które zostały poddane kwarantannie przez ochronę przed analizą skrzynki pocztowej.
       - **Jeśli wiadomość zostanie wykryta jako sfałszowana**: wybierz pozycję **Przenieś wiadomość do folderów wiadomości-śmieci adresatów** (Standardowa) lub **Kwarantanna wiadomości** (ścisła).  Jeśli **wybierzesz pozycję Kwarantanna komunikatu**, zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz [zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed fałszowaniem danych wywiadowczych.
     - **Wskazówki dotyczące bezpieczeństwa & sekcji wskaźników** : Skonfiguruj następujące ustawienia:
       - **Pokaż pierwszy kontakt porada dotycząca bezpieczeństwa**: Wybierz (włącz).
       - Pokaż porada dotycząca bezpieczeństwa <sup>\*</sup>**personifikacji użytkownika**: Wybierz (włącz).
       - Pokaż porada dotycząca bezpieczeństwa <sup>\*</sup>**personifikacji domeny**: Wybierz (włącz).
       - **Pokaż nietypowe znaki personifikacji użytkownika porada dotycząca bezpieczeństwa**<sup>\*</sup>: Wybierz (włącz).
       - **Pokaż (?) dla nieuwierzytelnionych nadawców pod kątem fałszowania**: Wybierz (włącz).
       - **Pokaż tag "via"**: wybierz pozycję (włącz).

     Po zakończeniu kliknij przycisk **Zapisz**.

   <sup>\*</sup>To ustawienie jest dostępne tylko w Ochrona usługi Office 365 w usłudze Defender.

4. Kliknij **przycisk Zapisz** , a następnie kliknij przycisk **Zamknij**

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed wyłudzaniem informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md) i [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Część 3 — Ochrona przed spamem w ramach EOP

Aby uzyskać więcej informacji na temat zalecanych ustawień ochrony przed spamem, zobacz [Ustawienia zasad ochrony przed spamem w usłudze EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Otwórz stronę **Zasady ochrony przed spamem** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady o nazwie **Zasady ruchu przychodzącego ochrony przed spamem (domyślne),** klikając nazwę.

3. W wyświetlonym oknie wysuwowym szczegółów zasad skonfiguruj następujące ustawienia:
   - **Próg zbiorczej poczty e-mail & sekcji właściwości spamu** : kliknij pozycję **Edytuj próg spamu i właściwości**. W wyświetlonym wysuwie skonfiguruj następujące ustawienia:
     - **Próg zbiorczej poczty e-mail**: ustaw tę wartość na wartość 5 (ścisła) lub 6 (standardowa).
     - Pozostaw inne ustawienia na wartościach domyślnych (**Wyłączone** lub **Brak**).

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja Akcje** : kliknij pozycję **Edytuj akcje**. W wyświetlonym wysuwie skonfiguruj następujące ustawienia:
     - Sekcja **akcji komunikatu**:
       - **Spam**: sprawdź, czy wybrano **opcję Przenieś wiadomość do folderu Wiadomości-śmieci** (Standardowa) lub wybierz **pozycję Wiadomość kwarantanny** (ścisła).
       - **Spam o wysokim poziomie ufności**: wybierz **pozycję Wiadomość kwarantanny**.
       - **Wyłudzanie informacji**: wybierz **pozycję Komunikat kwarantanny**.
       - **Wyłudzanie informacji o wysokim poziomie ufności**: sprawdź, czy **wybrano komunikaty kwarantanny** .
       - **Zbiorczo**: sprawdź, czy wybrano **opcję Przenieś wiadomość do folderu Wiadomości-śmieci** (Standardowa) lub wybierz **pozycję Komunikat kwarantanny** (ścisły).

       Dla każdej akcji, w której **wybrano komunikat kwarantanny**, zostanie wyświetlone pole **Wyboru zasad kwarantanny** , w którym [wybierzesz zasady kwarantanny](quarantine-policies.md) , które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed spamem.

     - **Zachowaj spam w kwarantannie przez tyle dni**: sprawdź wartość **30** dni.
     - **Włącz wskazówki dotyczące bezpieczeństwa spamu**: sprawdź, czy to ustawienie jest zaznaczone (włączone).
     - **Włącz automatyczne przeczyszczanie o zerowej godzinie (ZAP)**: sprawdź, czy to ustawienie jest zaznaczone (włączone).
       - **Włącz dla wiadomości wyłudzających informacje**: sprawdź, czy to ustawienie jest zaznaczone (włączone). Aby uzyskać więcej informacji, zobacz [Zero-hour auto przeczyszczanie (ZAP) w celu wyłudzania informacji](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Włącz dla wiadomości niepożądanych**: sprawdź, czy to ustawienie jest zaznaczone (włączone). Aby uzyskać więcej informacji, zobacz [Zero-hour auto przeczyszczanie (ZAP) pod kątem spamu](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam).

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja Dozwolonych i zablokowanych nadawców i domen** : Przejrzyj lub edytuj dozwolonych nadawców i dozwolone domeny zgodnie z opisem w [temacie Tworzenie zablokowanych list nadawców w ramach EOP](create-block-sender-lists-in-office-365.md) lub [Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md).

     Po zakończeniu kliknij przycisk **Zapisz**.

4. Po wprowadzeniu wszystkich zmian kliknij przycisk **Zamknij**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed spamem, zobacz [Konfigurowanie zasad ochrony przed spamem w usłudze EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Część 4 — Ochrona przed złośliwymi adresami URL i plikami (linki Sejf i załączniki Sejf w Ochrona usługi Office 365 w usłudze Defender)

Ochrona przed złośliwymi adresami URL i plikami jest dostępna w subskrypcjach zawierających [Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Jest on konfigurowany za pomocą zasad [Sejf Załączniki](safe-attachments.md) i [linki Sejf](safe-links.md).

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>zasady załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat zalecanych ustawień dla załączników Sejf, zobacz .[ Sejf ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Otwórz stronę **załączników Sejf** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** kliknij pozycję **Ustawienia globalne**, a następnie skonfiguruj następujące ustawienia w wyświetlonym wysuwie:
   - **Włącz Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive i Microsoft Teams**: włącz to ustawienie (![Włącz).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **Przed włączeniem Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams sprawdź, czy rejestrowanie inspekcji jest włączone w organizacji**. Ta akcja jest zwykle wykonywana przez osobę, która ma przypisaną rolę Dzienniki inspekcji w Exchange Online. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

   - **Włącz Sejf Dokumenty dla klientów Office**: włącz to ustawienie (![Włącz](../../media/scc-toggle-on.png)). Należy pamiętać, że ta funkcja jest dostępna i zrozumiała tylko w przypadku wymaganych typów licencji. Aby uzyskać więcej informacji, zobacz [Sejf Documents in Microsoft 365 E5 (Dokumenty Sejf w Microsoft 365 E5](safe-docs.md)).
   - **Zezwalaj użytkownikom na klikanie widoku chronionego, nawet jeśli Sejf Dokumenty zidentyfikowały plik jako złośliwy**: Sprawdź, czy to ustawienie jest wyłączone (![Przełącz wyłączone).](../../media/scc-toggle-off.png)

   Po zakończeniu kliknij pozycję **Zapisz**

3. Po powrocie na stronę **załączników Sejf** kliknij pozycję Utwórz ikonę![.](../../media/m365-cc-sc-create-icon.png)

4. W **kreatorze tworzenia zasad tworzenia załączników Sejf**, który zostanie otwarty, skonfiguruj następujące ustawienia:
   - **Nadaj nazwę stronie zasad** :
     - **Nazwa**: wprowadź coś unikatowego i opisowego.
     - **Opis**: wprowadź opcjonalny opis.
   - **Strona Użytkownicy i domeny** : ponieważ są to pierwsze zasady i prawdopodobnie chcesz zmaksymalizować zasięg, rozważ wprowadzenie [zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w polu **Domeny** . W przeciwnym razie możesz użyć pól **Użytkownicy** i **grupy** , aby uzyskać bardziej szczegółową kontrolę. Wyjątki można określić, wybierając pozycję **Wyklucz tych użytkowników, grupy i domeny** oraz wprowadzając wartości.
   - **strona Ustawienia**:
     - **Sejf Odpowiedzi na nieznane złośliwe oprogramowanie załączników**: wybierz pozycję **Blokuj**.
     - **Zasady kwarantanny**: wartość domyślna jest pusta, co oznacza, że są używane zasady AdminOnlyAccessPolicy. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
     - **Przekierowywanie załącznika z wykrytymi załącznikami** : **Włącz przekierowanie**: włącz to ustawienie (wybierz) i wprowadź adres e-mail w celu odbierania wykrytych wiadomości.
     - **Zastosuj odpowiedź wykrywania Sejf Załączniki, jeśli skanowanie nie może zostać ukończone (przekroczenie limitu czasu lub błędy)**: Sprawdź, czy to ustawienie jest zaznaczone.

5. Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

6. (Zalecane) Jako administrator globalny lub administrator usługi SharePoint Online uruchom polecenie cmdlet **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** z parametrem _DisallowInfectedFileDownload_ ustawionym na `$true` w SharePoint Online PowerShell.
   - `$true` blokuje wszystkie akcje (z wyjątkiem usuwania) dla wykrytych plików. Użytkownicy nie mogą otwierać, przenosić, kopiować ani udostępniać wykrytych plików.
   - `$false` blokuje wszystkie akcje z wyjątkiem usuwania i pobierania. Użytkownicy mogą zaakceptować ryzyko i pobrać wykryty plik.

7. Zaczekaj do 30 minut na rozłożenie zmian na wszystkie Microsoft 365 centrów danych.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad załączników Sejf i ustawień globalnych dla załączników Sejf, zobacz następujące tematy:

- [Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-attachments-policies.md)
- [Włączanie bezpiecznych załączników dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Bezpieczne dokumenty w usłudze Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>zasady linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat zalecanych ustawień dla linków Sejf, zobacz [ustawienia linków Sejf](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Otwórz stronę **łącza Sejf** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/safelinksv2>.

2. Na stronie **łącza Sejf** kliknij pozycję **Ustawienia globalne**, a następnie skonfiguruj następujące ustawienia w wyświetlonym wysuwie:
   - **Ustawienia, które mają zastosowanie do zawartości w sekcji obsługiwane aplikacje Office 365**:
     - **Użyj linków Sejf w aplikacjach Office 365**: sprawdź, czy to ustawienie jest włączone (![Włącz](../../media/scc-toggle-on.png)).
     - **Nie śledź, kiedy użytkownicy klikają linki chronione w aplikacjach Office 365**: wyłącz to ustawienie (![Przełącz wyłączone).](../../media/scc-toggle-off.png)
     - **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL w aplikacjach Office 365**: Sprawdź, czy to ustawienie jest włączone (![Przełącz włączone).](../../media/scc-toggle-on.png)

   Po zakończeniu kliknij pozycję **Zapisz**

3. Po powrocie na stronę **Sejf Linki** kliknij pozycję Utwórz ikonę![.](../../media/m365-cc-sc-create-icon.png)

4. W **kreatorze tworzenia zasad linków Sejf**, który zostanie otwarty, skonfiguruj następujące ustawienia:
   - **Nadaj nazwę stronie zasad** :
     - **Nazwa**: wprowadź coś unikatowego i opisowego.
     - **Opis**: wprowadź opcjonalny opis.
   - **Strona Użytkownicy i domeny** : ponieważ są to pierwsze zasady i prawdopodobnie chcesz zmaksymalizować zasięg, rozważ wprowadzenie [zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w polu **Domeny** . W przeciwnym razie możesz użyć pól **Użytkownicy** i **grupy** , aby uzyskać bardziej szczegółową kontrolę. Wyjątki można określić, wybierając pozycję **Wyklucz tych użytkowników, grupy i domeny** oraz wprowadzając wartości.
   - **Adres URL & kliknij stronę ustawień ochrony** :
     - **Akcja dotycząca potencjalnie złośliwych adresów URL w sekcji Wiadomości e-mail** :
       - **Włączone: Sejf Linki sprawdzają listę znanych, złośliwych linków, gdy użytkownicy klikają linki w wiadomości e-mail**: wybierz jego ustawienie (włącz).
       - **Zastosuj Sejf Łącza do wiadomości e-mail wysyłanych w organizacji**: wybierz to ustawienie (włącz).
       - **Zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**: wybierz to ustawienie (włącz).
       - **Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL**: wybierz to ustawienie (włącz).
       - **Nie należy ponownie pisać adresów URL, sprawdzaj tylko za pośrednictwem interfejsu API linków Sejf**: Sprawdź, czy to ustawienie nie jest zaznaczone (wyłącz).
     - **Nie należy ponownie pisać następujących adresów URL w wiadomości e-mail**: Nie mamy konkretnych zaleceń dotyczących tego ustawienia. Aby uzyskać więcej informacji, zobacz [artykuł "Nie przepisuj ponownie następujących adresów URL" list w zasadach linków Sejf](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).
     - **Akcja dotycząca potencjalnie złośliwych adresów URL w sekcji Microsoft Teams**:
       - ***Włączone: Sejf Linki sprawdzają listę znanych, złośliwych linków, gdy użytkownicy klikają linki w Microsoft Teams**: wybierz to ustawienie (włącz).
     - **Kliknij sekcję ustawień ochrony** :
       - **Śledzenie kliknięć użytkownika**: sprawdź, czy to ustawienie jest zaznaczone (włączone).
       - **Zezwalaj użytkownikom na klikanie oryginalnego adresu URL**: wyłącz to ustawienie (nie zaznaczono).
       - **Wyświetlanie znakowania organizacji na stronach powiadomień i ostrzeżeń**: wybranie tego ustawienia (włączenie go) ma znaczenie dopiero po wykonaniu instrukcji w [temacie Dostosowywanie motywu Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md) w celu przekazania logo firmy.
   - Strona **powiadomień**:
     - **Jak chcesz powiadomić użytkowników?** sekcja: Opcjonalnie możesz wybrać pozycję **Użyj niestandardowego tekstu powiadomienia** , aby wprowadzić dostosowany tekst powiadomienia do użycia. Możesz również wybrać pozycję **Użyj Microsoft Translator do automatycznej lokalizacji**, aby przetłumaczyć niestandardowy tekst powiadomienia na język użytkownika. W przeciwnym razie pozostaw **zaznaczony domyślny tekst powiadomienia** .

5. Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad łączy Sejf i ustawień globalnych dla linków Sejf, zobacz następujące tematy:

- [Konfigurowanie zasad linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md)
- [Konfigurowanie ustawień globalnych dla linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Teraz skonfiguruj alerty dla wykrytych plików w usłudze SharePoint Online lub OneDrive dla Firm

Aby otrzymywać powiadomienia, gdy plik w usłudze SharePoint Online lub OneDrive dla Firm został zidentyfikowany jako złośliwy, możesz skonfigurować alert zgodnie z opisem w tej sekcji.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Zasady** & **zasad** \> & **współpracy** \> & poczty e-mail.

2. Na stronie **Zasady alertów** kliknij pozycję **Nowe zasady alertów**.

3. Zostanie otwarty kreator **nowych zasad alertów** . Na stronie **Nazwa** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową i opisową nazwę. Na przykład można wpisać złośliwe pliki w bibliotekach.
   - **Opis**: wprowadź opcjonalny opis.
   - **Ważność**: wybierz pozycję **Niski**, **Średni** lub **Wysoki**.
   - **Kategoria**: wybierz pozycję **Zarządzanie zagrożeniami**.

   Po zakończeniu kliknij przycisk **Dalej**

4. Na stronie **Tworzenie ustawień alertu** skonfiguruj następujące ustawienia:
   - **Na czym chcesz otrzymywać alerty?** sekcja: **Działanie to** \> **Wykryte złośliwe oprogramowanie w pliku**.
   - **Jak chcesz, aby alert został wyzwolony** , sekcja: Weryfikowanie **za każdym razem, gdy działanie jest zgodne z regułą** .

   Po zakończeniu kliknij przycisk **Dalej**

5. Na stronie **Ustawianie adresatów** skonfiguruj następujące ustawienia:
   - **Wysyłanie powiadomień e-mail**: sprawdź, czy to ustawienie jest zaznaczone.
   - **Adresaci wiadomości e-mail**: wybierz co najmniej jednego administratora globalnego, administratora zabezpieczeń lub czytelników zabezpieczeń, którzy powinni otrzymywać powiadomienia po wykryciu złośliwego pliku.
   - **Dzienny limit powiadomień**: sprawdź, czy nie wybrano **żadnego limitu** .

   Po zakończeniu kliknij przycisk **Dalej**

6. Na stronie **Przeglądanie ustawień przejrzyj** ustawienia, sprawdź opcję **Tak, włącz ją od razu** , a następnie kliknij przycisk **Zakończ**

Aby dowiedzieć się więcej na temat zasad alertów, zobacz [Zasady alertów w portalu zgodności usługi Microsoft Purview](../../compliance/alert-policies.md).

> [!NOTE]
> Po zakończeniu konfigurowania użyj tych linków, aby rozpocząć badania obciążeń:
>
> - [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
> - [Zarządzanie plikami poddanymi kwarantannie w Ochrona usługi Office 365 w usłudze Defender za pomocą portalu Microsoft 365 Defender](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [Co zrobić, gdy złośliwy plik zostanie znaleziony w usłudze SharePoint Online, OneDrive lub Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Zadania po instalacji i następne kroki

Po skonfigurowaniu funkcji ochrony przed zagrożeniami należy monitorować działanie tych funkcji. Przejrzyj i zrewiduj zasady tak, aby robiły to, czego potrzebujesz. Ponadto należy zapoznać się z nowymi funkcjami i aktualizacjami usług, które mogą dodać wartość.

|Co robić|Zasoby, aby dowiedzieć się więcej|
|---|---|
|Zobacz, jak funkcje ochrony przed zagrożeniami działają w Organizacji, wyświetlając raporty|[Raporty zabezpieczeń poczty e-mail](view-email-security-reports.md) <p> [Raporty dla Ochrona usługi Office 365 w usłudze Microsoft Defender](view-reports-for-mdo.md) <p> [Eksplorator zagrożeń](threat-explorer.md)|
|Okresowe przeglądanie i poprawianie zasad ochrony przed zagrożeniami w razie potrzeby|[Wskaźnik bezpieczeństwa](../defender/microsoft-secure-score.md) <p> [Microsoft 365 funkcje badania zagrożeń i reagowania na nie](./office-365-ti.md)|
|Obejrzyj nowe funkcje i aktualizacje usługi|[Opcje wersji standardowej i docelowej](../../admin/manage/release-options-in-office-365.md) <p> [Centrum wiadomości](../../admin/manage/message-center.md) <p> [Plan działania usługi Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Opisy usług](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
