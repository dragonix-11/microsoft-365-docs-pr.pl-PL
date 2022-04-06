---
title: Ochrona przed zagrożeniami w programach Ochrona usługi Office 365 w usłudze Microsoft Defender, anti-malware, anti-phishing, anti-spam, linki Sejf, załączniki Sejf, automatyczne przeczyszczanie zerowej godziny (ZAP), konfiguracja zabezpieczeń MDO
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
description: Administratorzy mogą dowiedzieć się więcej o ochronie przed Microsoft 365 i skonfigurować sposób używania jej w organizacji.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e5a0be5171a2de07792cd259dc6547046d7c1630
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507192"
---
# <a name="protect-against-threats"></a>Ochrona przed zagrożeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Oto przewodnik Szybki start, który dzieli konfigurację Ochrona usługi Office 365 w usłudze Defender na fragmenty. Jeśli dopiero zaczynasz korzystać z funkcji ochrony przed zagrożeniami w programie Office 365, nie wiesz, od czego zacząć, lub jeśli najlepiej się *uczysz, użyj* tych wskazówek jako listy kontrolnej i punktu wyjścia.

> [!IMPORTANT]
> **Początkowe zalecane ustawienia są dostępne dla** każdego rodzaju zasad, jednak dostępnych jest wiele opcji i możesz dostosować je do potrzeb konkretnej organizacji. Zezwalaj około 30 minut na sposób pracy zasad lub zmian przez centrum danych.
>
> Aby pominąć ręczną konfigurację większości zasad w programie Ochrona usługi Office 365 w usłudze Defender, można użyć wstępnie ustawionych zasad zabezpieczeń na poziomie Standardowy lub Ścisłe. Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w uchcie eOP i programie Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md).

## <a name="requirements"></a>Wymagania

### <a name="subscriptions"></a>Subskrypcje

Funkcje ochrony przed zagrożeniami *są zawarte we* wszystkich subskrypcjach produktów firmy Microsoft Office 365, jednak niektóre subskrypcje mają zaawansowane funkcje. W poniższej tabeli wymieniono funkcje ochrony zawarte w tym artykule oraz minimalne wymagania dotyczące subskrypcji.

> [!TIP]
> Zwróć uwagę, że oprócz wskazówek, jak włączyć *inspekcję, wykonać* kroki w celu uruchomienia ochrony przed złośliwym oprogramowaniem, ochrony przed wyłudzaniem informacji i ochrony przed spamem, które są oznaczone jako część Office 365 Exchange Online Protection (**EOP**). Może to wydawać się nieparzyste Ochrona usługi Office 365 w usłudze Defender artykułu, dopóki nie pamiętasz (**Ochrona usługi Office 365 w usłudze Defender**) zawiera i tworzysz program EOP.

|Typ ochrony|Wymaganie subskrypcji|
|---|---|
|Rejestrowanie inspekcji (na potrzeby raportowania)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Ochrona przed złośliwym oprogramowaniem|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Ochrona przed wyłudzaniem informacji|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Ochrona przed spamem|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Ochrona przed złośliwymi adresami URL i plikami w wiadomościach e-mail Office dokumentach (linki Sejf i załączniki Sejf wiadomości)|[Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Role i uprawnienia

Aby skonfigurować Ochrona usługi Office 365 w usłudze Defender, musisz mieć przypisaną odpowiednią rolę. W poniższej tabeli znajdziesz role, które mogą wykonać te czynności.

|Rola lub grupa ról|Gdzie można dowiedzieć się więcej|
|---|---|
|administrator globalny|[Informacje Microsoft 365 administratorów](../../admin/add-users/about-admin-roles.md)|
|Administrator zabezpieczeń|[Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference#security-administrator)
|Exchange Online zarządzanie organizacją|[Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo)|

Aby dowiedzieć się więcej, zobacz [Uprawnienia w portalu Microsoft 365 Defender witryny](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Włączanie rejestrowania inspekcji dla raportowania i badania

- Rozpocznij rejestrowanie inspekcji wcześniej. Aby można było wykonać niektóre z poniższych **czynności,** inspekcja musi być wł. Rejestrowanie inspekcji jest dostępne w subskrypcjach, które zawierają [Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Aby można było wyświetlać dane w raportach ochrony przed zagrożeniami [,](view-email-security-reports.md) raportach zabezpieczeń poczty e-mail i Eksploratorze [, rejestrowanie](threat-explorer.md) inspekcji musi być *włączone*. Aby dowiedzieć się więcej, zobacz [Włączanie lub wyłączanie wyszukiwania w dzienniku inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Część 1. Ochrona przed złośliwym oprogramowaniem w uterjomej eOP

Aby uzyskać więcej informacji na temat zalecanych ustawień ochrony przed złośliwym oprogramowaniem, zobacz Ustawienia zasad ochrony przed złośliwym oprogramowaniem [eOP](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Otwórz stronę **ochrony przed złośliwym oprogramowaniem** w portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/antimalwarev2>.

2. Na stronie **ochrona przed złośliwym oprogramowaniem** wybierz zasady o nazwie **Domyślne (domyślne),** klikając nazwę.

3. W oknie wysuwu szczegółów zasad, które zostanie otwarte, kliknij pozycję **Edytuj ustawienia ochrony**, a następnie skonfiguruj następujące ustawienia:
   - **Sekcja Ustawienia** ochrony:
     - **Włącz wspólny filtr załączników**: Wybierz (włącz). Kliknij **pozycję Dostosuj typy plików,** aby dodać więcej typów plików.
     - **Włączanie automatycznego przeczyszczania w godzinach pracy w poszukiwaniu złośliwego** oprogramowania: sprawdź, czy to ustawienie jest zaznaczone. Aby uzyskać więcej informacji na temat programu ZAP w przypadku złośliwego oprogramowania, zobacz [Automatyczne przeczyszczanie bezgodzinne (ZAP) w przypadku złośliwego oprogramowania](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware).
   - **Zasady kwarantanny**: pozostaw zaznaczoną wartość domyślną AdminOnlyAccessPolicy. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
   - **Sekcja** powiadomień: Upewnij się, że żadne z ustawień powiadomień nie jest zaznaczone.

   Po zakończeniu kliknij przycisk **Zapisz**.

4. Na wysuwanych szczegółach zasad kliknij pozycję **Zamknij**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed złośliwym oprogramowaniem, zobacz Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem [w uciekaniu usługi EOP](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Część 2. Ochrona przed wyłudzaniem informacji w UOS i Ochrona usługi Office 365 w usłudze Defender

[Ochrona przed wyłudzaniem informacji](anti-phishing-protection.md) jest dostępna w subskrypcjach, które zawierają [usługę EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Zaawansowana ochrona przed wyłudzaniem informacji jest [dostępna w Ochrona usługi Office 365 w usłudze Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Aby uzyskać więcej informacji na temat zalecanych ustawień zasad ochrony przed wyłudzaniem informacji, zobacz Ustawienia zasad ochrony przed wyłudzaniem informacji [eOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) i Ustawienia zasad ochrony przed wyłudzaniem informacji w [programie Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

Poniżej opisano procedurę konfigurowania domyślnych zasad ochrony przed wyłudzaniem informacji. Ustawienia, które są dostępne tylko w Ochrona usługi Office 365 w usłudze Defender są wyraźnie oznaczone.

1. Otwórz stronę **ochrony przed wyłudzaniem** informacji w portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem** informacji wybierz zasady o nazwie **Office365 AntiPhish Default (domyślne** ), klikając nazwę.

3. W wyświetlonym wysuwanych szczegółach zasad skonfiguruj następujące ustawienia:
   - **Próg wyłudzania & ochrony** : Kliknij **pozycję Edytuj ustawienia ochrony** i skonfiguruj następujące ustawienia w otwieranych wysuwanych menu:
     - **Próg wiadomości e-mail**<sup>\*</sup> wyłudzających informacje: Wybierz **wartość 2 — Agresywna** (standardowa) lub **3 – Bardziej** rygorystyczna (rygorystyczna).
     - **Sekcja Personifikacja**<sup>\*</sup>: Skonfiguruj następujące wartości:
       - Wybierz pozycję Włącz ochronę **użytkowników, kliknij** wyświetlony link Zarządzaj **(nn** ), a następnie dodaj wewnętrznych i zewnętrznych nadawców w celu ochrony przed personifikacji, na przykład członków zarządu organizacji, dyrektora generalnego, dyrektora generalnego i innych wyższego kierownictwa.
       - Wybierz **pozycję Włącz ochronę domen**, a następnie skonfiguruj wyświetlone następujące ustawienia:
         - Wybierz **pozycję Uwzględnij domeny, których jestem** właścicielem, aby chronić wewnętrznych nadawców w zaakceptowanych domenach (widoczne po kliknięciu pozycji **Wyświetl moje** domeny) przed personifikacji.
         - Aby chronić nadawców w innych domenach **, wybierz** pozycję Uwzględnij domeny niestandardowe, kliknij link Zarządzaj **domenami niestandardowymi (nn** ), który zostanie wyświetlony, a następnie dodaj inne domeny w celu ochrony przed personifikacji.
     - **Dodawanie sekcji zaufanych**<sup>\*</sup> nadawców i domen: Kliknij pozycję Zarządzaj **(nn)** zaufanymi nadawcami i domenami, aby w razie potrzeby skonfigurować wyjątki nadawcy i domeny nadawcy na potrzeby ochrony personifikacji.
     - Ustawienia analizy skrzynki pocztowej <sup>\*</sup>: Upewnij się **, że** zaznaczono opcję Włącz analizę skrzynek pocztowych i **Włącz analizę dla ochrony personifikacji** .
     - **Sekcja Fałsz** : Sprawdź, czy **jest zaznaczona opcja Włącz analizę fałszowania** .

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja** Akcje: Kliknij **pozycję Edytuj akcje** i skonfiguruj następujące ustawienia w oknie wysuwu, które zostanie otwarte:
     - **Sekcja Akcje** wiadomości: Konfigurowanie następujących ustawień:
       - **Jeśli wiadomość zostanie wykryta jako personifikowany użytkownik**<sup>\*</sup>: Wybierz **pozycję Poddaj wiadomość kwarantannie**. W **miejscu, w którym wybierzesz** zasady kwarantanny [](quarantine-policies.md) dotyczące wiadomości poddanych kwarantannie przez ochronę personifikacji użytkownika, zostanie wyświetlone okno Zastosuj zasady kwarantanny.
       - **Jeśli wiadomość zostanie wykryta jako spersonifikowana domena**<sup>\*</sup>: Wybierz **pozycję Poddaj wiadomość kwarantannie**. Zostanie **wyświetlone okno Zastosuj zasady kwarantanny**, w którym [](quarantine-policies.md) wybierzesz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę personifikacji domeny.
       - **Jeśli w analizie**<sup>\*</sup> skrzynki pocztowej zostanie wykryty personifikowany użytkownik: wybierz pozycję Przenieś wiadomość do folderów wiadomości-śmieci **adresatów** (standardowe) lub Poddaj ją kwarantannie **(Ścisłe** ). Jeśli wybierzesz pozycję  **Poddaj** wiadomość kwarantannie, pojawi się pole Zastosuj zasady [](quarantine-policies.md) kwarantanny w miejscu, w którym wybierzesz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę skrzynki pocztowej.
       - **Jeśli wiadomość zostanie wykryta jako** fałszywa: Wybierz pozycję Przenieś wiadomość do folderów wiadomości-śmieci **adresatów** (standardowe) lub Poddaj ją kwarantannie **(ścisłe** ).  Jeśli wybierzesz pozycję  **Poddaj** kwarantannie wiadomość, zostanie wyświetlone okno Zastosuj zasady [](quarantine-policies.md) kwarantanny w miejscu, w którym wybierzesz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę przed fałszerami.
     - **Porady dotyczące & wskaźników** : Konfigurowanie następujących ustawień:
       - **Pokaż pierwszy kontakt porada dotycząca bezpieczeństwa**: Wybierz (włącz).
       - **Pokaż identyfikator personifikacji porada dotycząca bezpieczeństwa**<sup>\*</sup>: Wybierz (włącz).
       - **Pokaż domenę personifikacji porada dotycząca bezpieczeństwa**<sup>\*</sup>: Wybierz (włącz).
       - **Pokaż nietypowe znaki personifikacji użytkownika porada dotycząca bezpieczeństwa**<sup>\*</sup>: Wybierz (włącz).
       - **Pokaż (?) dla nieuwierzytanych nadawców w celu fałszowania**: Wybierz (włącz).
       - **Pokaż tag "za pośrednictwem"**: Wybierz (włącz).

     Po zakończeniu kliknij przycisk **Zapisz**.

   <sup>\*</sup>To ustawienie jest dostępne tylko w programie Ochrona usługi Office 365 w usłudze Defender.

4. Kliknij **przycisk Zapisz,** a następnie kliknij przycisk **Zamknij.**

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed wyłudzaniem informacji, zobacz Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi [EOP](configure-anti-phishing-policies-eop.md) i Konfigurowanie zasad ochrony przed wyłudzaniem informacji w [programie Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Część 3. Ochrona przed spamem w uciekaniu poczty eop

Aby uzyskać więcej informacji na temat zalecanych ustawień ochrony przed spamem, zobacz Ustawienia zasad ochrony [przed spamem W UA.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

1. Otwórz stronę **Zasady ochrony przed spamem** w portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady o nazwie Zasady przychodzące ochrony przed **spamem (** domyślne), klikając nazwę.

3. W wyświetlonym wysuwanych szczegółach zasad skonfiguruj następujące ustawienia:
   - **Próg masowej & właściwości spamu** : Kliknij **pozycję Edytuj próg i właściwości spamu**. W wyświetlonym wysuwu skonfiguruj następujące ustawienia:
     - **Próg masowej poczty** e-mail: Ustaw tę wartość na 5 (Ścisłe) lub 6 (Standardowe).
     - Pozostaw inne ustawienia na ich wartościach domyślnych (**Wyłączone** lub **Brak**).

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja** Akcje: Kliknij **pozycję Edytuj akcje**. W wyświetlonym wysuwu skonfiguruj następujące ustawienia:
     - **Sekcja Akcje** wiadomości:
       - **Spam**: sprawdź, **czy jest zaznaczona opcja Przenieś wiadomość do folderu Wiadomości-śmieci** (standardowy) lub wybierz pozycję **Poddaj wiadomość kwarantannie** (ścisłe).
       - **Duża pewność, że spam**: Wybierz pozycję **Poddaj wiadomość kwarantannie**.
       - **Wyłudzanie** informacji: Wybierz **pozycję Poddaj wiadomość kwarantannie**.
       - **Wyłudzanie dużej pewności**: sprawdź **, czy jest zaznaczona opcja Sprawdź, czy jest zaznaczona opcja Poddaj** wiadomości kwarantannie.
       - **Zbiorcze**: sprawdź, **czy jest zaznaczona opcja Przenieś wiadomość do folderu Wiadomości-śmieci** (standardowy) lub wybierz pozycję **Kwarantanna wiadomości** (ścisłe).

       W przypadku każdej akcji, w której wybierzesz pozycję  Poddaj wiadomość kwarantannie **, pojawi** się pole Wybierz zasady kwarantanny w miejscu, w którym wybierzesz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę przed spamem.[](quarantine-policies.md)

     - **Zachowywanie spamu w kwarantannie przez tę wiele dni**: Sprawdź wartość **30** dni.
     - **Włącz porady dotyczące bezpieczeństwa przed** spamem: sprawdź, czy to ustawienie jest zaznaczone (włączone).
     - **Włączanie automatycznego przeczyszczania bez godzin:** sprawdź, czy to ustawienie jest zaznaczone (włączone).
       - **Włącz dla wiadomości wyłudzających informacje**: sprawdź, czy to ustawienie jest zaznaczone (włączone). Aby uzyskać więcej informacji, zobacz [Automatyczne przeczyszczanie bez godzin (ZAP) w celu wyłudzania informacji](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Włącz dla wiadomości-śmieci**: sprawdź, czy to ustawienie jest zaznaczone (włączone). Aby uzyskać więcej informacji, zobacz [Automatyczne przeczyszczanie bez godzin (ZAP) w przypadku spamu](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam).

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja dozwolonych i zablokowanych** nadawców i domen: Przejrzyj lub edytuj dozwolonych nadawców i dozwolone domeny zgodnie z opisem w artykule Tworzenie list zablokowanych nadawców w uchęcie [EOP](create-block-sender-lists-in-office-365.md) lub Tworzenie list bezpiecznych nadawców w [uchcie usługi EOP](create-safe-sender-lists-in-office-365.md).

     Po zakończeniu kliknij przycisk **Zapisz**.

4. Po wprowadzeniu wszystkich zmian kliknij przycisk **Zamknij**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad ochrony przed spamem, zobacz [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Część 4. Ochrona przed złośliwymi adresami URL i plikami (linki Sejf i załączniki Sejf w folderze Ochrona usługi Office 365 w usłudze Defender)

Ochrona przed złośliwymi adresami URL i plikami po kliknięciu jest dostępna w subskrypcjach zawierających [Ochrona usługi Office 365 w usłudze Microsoft Defender.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) Te zasady są ustawiane za [pomocą Sejf załączników](safe-attachments.md) [i Sejf linków](safe-links.md).

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Sejf załączników w aplikacji Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat zalecanych ustawień dla załączników Sejf, zobacz .[ Sejf ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Otwórz stronę **Sejf załączników** w portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** kliknij pozycję **Ustawienia** globalne, a następnie skonfiguruj następujące ustawienia w wyświetlonym wysuwanych oknie wysuwanych:
   - **Włącz Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive i Microsoft Teams**: Włącz to ustawienie (![włącz).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **Przed włączeniem załączników Sejf dla aplikacji SharePoint,** OneDrive i Microsoft Teams upewnij się, że rejestrowanie inspekcji jest włączone w organizacji. Ta akcja jest zazwyczaj wykonywana przez osobę, która ma rolę Dzienniki inspekcji przypisaną do Exchange Online. Aby uzyskać więcej informacji, zobacz Włączanie lub wyłączanie wyszukiwania w [dzienniku inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

   - **Włącz Sejf dokumenty dla Office klientów**: Włącz to ustawienie (![Włącz](../../media/scc-toggle-on.png)). Zwróć uwagę, że ta funkcja jest dostępna i znacząca tylko w przypadku wymaganych typów licencji. Aby uzyskać więcej informacji, [zobacz Sejf Dokumenty w programie Microsoft 365 E5](safe-docs.md).
   - **Zezwalaj użytkownikom na** klikanie w widoku chronionym, Sejf plik został oznaczony jako złośliwy: Sprawdź, czy to ustawienie jest wyłączone (![przełącznik wyłączony](../../media/scc-toggle-off.png)).

   Po zakończeniu kliknij przycisk **Zapisz.**

3. Z powrotem na **Sejf Załączniki** kliknij ikonę ![Utwórz](../../media/m365-cc-sc-create-icon.png).

4. W **kreatorze Sejf Załączniki** skonfiguruj następujące ustawienia:
   - **Nadaj nazwę stronie** zasad:
     - **Nazwa**: Wprowadź coś unikatowego i opisowego.
     - **Opis**. Wprowadź opcjonalny opis.
   - **Strona Użytkownicy i domeny**: ponieważ są to Twoje pierwsze zasady i prawdopodobnie chcesz zmaksymalizować zasięg, rozważ wprowadzenie zaakceptowanych [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) domen w **polu** Domeny. W przeciwnym razie możesz użyć pól **Użytkownicy** i  Grupy, aby uzyskać bardziej szczegółową kontrolę. Możesz określić wyjątki, wybierając pozycję **Wyklucz tych użytkowników, grupy i domeny i** wprowadzając wartości.
   - **Ustawienia** stronie:
     - **Sejf załączników odpowiedź z nieznanym złośliwym oprogramowaniem**: Wybierz **pozycję Zablokuj**.
     - **Zasady kwarantanny**: wartość domyślna jest pusta, co oznacza, że są używane zasady AdminOnlyAccessPolicy. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
     - **Przekieruj załączniki** **z** wykrytymi załącznikami: Włącz przekierowywanie. Włącz (wybierz) i wprowadź adres e-mail, aby otrzymywać wykryte wiadomości.
     - **Stosowanie odpowiedzi Sejf wykrywania** załączników, jeśli skanowanie nie jest ukończone (limit czasu lub błędy): Sprawdź, czy to ustawienie jest zaznaczone.

5. Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

6. (Zalecane) Jako administrator globalny lub administrator usługi SharePoint Online uruchom polecenie cmdlet **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** z parametrem _DisallowInfectedFileDownload_ `$true` ustawionym w programie SharePoint Online PowerShell.
   - `$true` blokuje wszystkie akcje (z wyjątkiem usuwania) dla wykrytych plików. Inne osoby nie mogą otwierać, przenosić, kopiować ani udostępniać wykrytych plików.
   - `$false` blokuje wszystkie akcje z wyjątkiem przycisków Usuń i Pobierz. Inne osoby mogą zaakceptować to ryzyko i pobrać wykryty plik.

7. Maksymalnie 30 minut na rozpowszechnienie zmian na Microsoft 365 danych.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania Sejf zasad załączników i ustawień globalnych dotyczących załączników Sejf, zobacz następujące tematy:

- [Konfigurowanie zasad Sejf załączników w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-attachments-policies.md)
- [Włącz załączniki Sejf załączników wiadomości SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Bezpieczne dokumenty w usłudze Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Sejf linków w aplikacji Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat zalecanych ustawień linków Sejf, zobacz Sejf [ustawienia linków](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Otwórz stronę **Sejf w** portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/safelinksv2>.

2. Na stronie **Sejf połączeń kliknij** pozycję **Ustawienia** globalne, a następnie skonfiguruj następujące ustawienia w wyświetlonym wysuwu:
   - **Ustawienia, które dotyczą zawartości w sekcji obsługiwane Office 365 aplikacji**:
     - **Używanie Sejf w aplikacjach Office 365:** Sprawdź, czy to ustawienie jest włączone (![włączoną](../../media/scc-toggle-on.png)).
     - **Nie śledź, kiedy użytkownicy klikają chronione linki w Office 365 aplikacjach**: Wyłącz to ustawienie (![Wyłącz).](../../media/scc-toggle-off.png)
     - **Nie pozwól użytkownikom na klikanie w** aplikacjach pakietu Office 365, aby przejść do pierwotnego adresu URL. Sprawdź, czy to ustawienie jest włączone (![włączoną](../../media/scc-toggle-on.png)).

   Po zakończeniu kliknij przycisk **Zapisz.**

3. Na stronie **Sejf kliknij** ikonę ![Utwórz](../../media/m365-cc-sc-create-icon.png).

4. W **kreatorze Sejf** tworzenie łączy konfiguruj następujące ustawienia:
   - **Nadaj nazwę stronie** zasad:
     - **Nazwa**: Wprowadź coś unikatowego i opisowego.
     - **Opis**. Wprowadź opcjonalny opis.
   - **Strona Użytkownicy i domeny**: ponieważ są to Twoje pierwsze zasady i prawdopodobnie chcesz zmaksymalizować zasięg, rozważ wprowadzenie zaakceptowanych [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) domen w **polu** Domeny. W przeciwnym razie możesz użyć pól **Użytkownicy** i  Grupy, aby uzyskać bardziej szczegółową kontrolę. Możesz określić wyjątki, wybierając pozycję **Wyklucz tych użytkowników, grupy i domeny i** wprowadzając wartości.
   - **Adres URL & stronie ustawień ochrony** :
     - **Akcja na potencjalnie złośliwych adresach URL w sekcji Wiadomości e-mail** :
       - **Wł.: Sejf sprawdza** listę znanych, złośliwych linków, gdy użytkownicy klikają linki w wiadomości e-mail: Wybierz jego ustawienie (włącz).
       - **Stosowanie Sejf do wiadomości e-mail wysyłanych** w organizacji: Wybierz to ustawienie (włącz).
       - **Stosowanie skanowania w czasie rzeczywistym podejrzanych linków i linków, które** wskazują pliki: Wybierz to ustawienie (włącz).
       - **Przed dostarczeniem wiadomości poczekaj**, aż skanowanie adresów URL zostanie ukończone: wybierz to ustawienie (włącz).
       - **Nie redaguj adresów URL, sprawdzaj** tylko za pośrednictwem interfejsu API Sejf Link: Sprawdź, czy to ustawienie nie jest zaznaczone (wyłącz tę opcję).
     - **Nie przepisuj w wiadomości e-mail** następujących adresów URL: Nie mamy konkretnych zaleceń dla tego ustawienia. Aby uzyskać więcej informacji, zobacz [listy "Nie](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) robisz ponownie następujących adresów URL" w zasadach dotyczących Sejf URL.
     - **Akcja w przypadku potencjalnie złośliwych adresów URL w Microsoft Teams** adresach URL:
       - ***Wł.: Sejf** sprawdza listę znanych, złośliwych linków, gdy użytkownicy klikają linki w aplikacji Microsoft Teams: Wybierz to ustawienie (włącz).
     - **Kliknij sekcję ustawień** ochrony:
       - **Śledź kliknięcia użytkowników**: Sprawdź, czy to ustawienie jest zaznaczone (włączone).
       - **Pozwól użytkownikom na kliknięcie pierwotnego adresu URL**: Wyłącz to ustawienie (nie zaznaczone).
       - Wyświetlanie **brandingu organizacji** na stronach powiadomień i ostrzeżeń: Zaznaczenie tego ustawienia (włączenie go) jest istotne dopiero po zakończeniu instrukcje w temacie [](../../admin/setup/customize-your-organization-theme.md) Dostosowywanie motywu Microsoft 365 organizacji w celu przekazania logo firmy.
   - **Strona** powiadomienia:
     - **Jak chcesz powiadomić użytkowników?** sekcja: Opcjonalnie możesz wybrać pozycję Użyj **niestandardowego tekstu powiadomień** , aby wprowadzić niestandardowy tekst powiadomienia. Aby przetłumaczyć niestandardowy tekst powiadomienia na język użytkownika **Microsoft Translator** użyć funkcji automatycznego tłumaczenia niestandardowego tekstu powiadomień. W przeciwnym razie **pozostaw zaznaczoną opcję Użyj domyślnego tekstu** powiadomień.

5. Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania Sejf linków i ustawień globalnych linków do witryn Sejf, zobacz następujące tematy:

- [Konfigurowanie zasad Sejf linków w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md)
- [Konfigurowanie ustawień globalnych linków Sejf w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Teraz możesz skonfigurować alerty dotyczące wykrytych plików w SharePoint Online lub OneDrive dla Firm

Aby otrzymywać powiadomienia, gdy plik w u SharePoint Online lub OneDrive dla Firm został zidentyfikowany jako złośliwy, możesz skonfigurować alert w sposób opisany w tej sekcji.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do tematu Zasady **&-mail** \> **i zasad & alertów**\>.

2. Na stronie **Zasady alertów** kliknij pozycję **Nowe zasady alertów**.

3. Zostanie **otwarty kreator Nowych zasad** alertów. Na **stronie Nazwa** skonfiguruj następujące ustawienia:
   - **Nazwa**: Wprowadź unikatową i opisową nazwę. Możesz na przykład wpisać złośliwe pliki w bibliotekach.
   - **Opis**. Wprowadź opcjonalny opis.
   - **Ważność**: Wybierz **pozycję Niski**, **Średni** lub **Wysoki**.
   - **Kategoria**: Wybierz **pozycję Zarządzanie zagrożeniami**.

   Po zakończeniu kliknij przycisk **Dalej.**

4. Na stronie **Tworzenie ustawień alertów** skonfiguruj następujące ustawienia:
   - **Czego chcesz ostrzegać?** sekcja: **Aktywność jest wykrywana** \> **w pliku w złośliwym oprogramowaniu**.
   - **Jak chcesz wyzwolić sekcję alertu** : Sprawdź **za każdym** razem, gdy działanie jest zaznaczone.

   Po zakończeniu kliknij przycisk **Dalej.**

5. Na stronie **Ustawianie adresatów** skonfiguruj następujące ustawienia:
   - **Wysyłanie powiadomień e-mail**: Sprawdź, czy to ustawienie jest zaznaczone.
   - **Adresaci wiadomości e-mail**: wybierz co najmniej jednego administratora globalnego, administratora zabezpieczeń lub czytelnika zabezpieczeń, którzy powinni otrzymać powiadomienie po wykryciu złośliwego pliku.
   - **Dzienny limit powiadomień**: Sprawdź **, czy nie wybrano limitu** .

   Po zakończeniu kliknij przycisk **Dalej.**

6. Na **stronie Przeglądanie ustawień przejrzyj** ustawienia, sprawdź, czy jest zaznaczona opcja **Tak,** włącz ją od razu, a następnie kliknij przycisk **Zakończ.**

Aby dowiedzieć się więcej o zasadach alertów, zobacz [Zasady alertów w Centrum zgodności platformy Microsoft 365](../../compliance/alert-policies.md).

> [!NOTE]
> Po zakończeniu konfigurowania możesz rozpocząć badania obciążenia pracą, korzystając z poniższych linków:
>
> - [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
> - [Zarządzanie plikami poddanymi kwarantannie w portalu Microsoft 365 Defender w programie Ochrona usługi Office 365 w usłudze Defender](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [Co należy zrobić w przypadku, gdy złośliwy plik zostanie znaleziony w SharePoint Online, OneDrive lub Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Zadania po instalacji i kolejne kroki

Po skonfigurowaniu funkcji ochrony przed zagrożeniami pamiętaj o tym, aby monitorować ich działanie. Przejrzyj i zrecenzuj zasady, tak aby robisz to, czego potrzebujesz. Ponadto obserwuj nowe funkcje i aktualizacje usług, które mogą być dla nas wartością dodaną.

|Co należy zrobić|Zasoby, aby dowiedzieć się więcej|
|---|---|
|Wyświetlanie raportów w celu wyświetlenia informacji o tym, jak działają funkcje ochrony przed zagrożeniami w organizacji|[Raporty zabezpieczeń poczty e-mail](view-email-security-reports.md) <p> [Raporty dla Ochrona usługi Office 365 w usłudze Microsoft Defender](view-reports-for-mdo.md) <p> [Eksplorator zagrożeń](threat-explorer.md)|
|Okresowe przeglądanie i poprawianie zasad ochrony przed zagrożeniami zgodnie z potrzebami|[Secure Score](../defender/microsoft-secure-score.md) <p> [Microsoft 365 analizy zagrożeń i funkcji reakcji](./office-365-ti.md)|
|Obserwowanie nowych funkcji i aktualizacji usługi|[Opcje wydania standardowego i kierowanego](../../admin/manage/release-options-in-office-365.md) <p> [Centrum wiadomości](../../admin/manage/message-center.md) <p> [Plan działania usługi Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Opisy usług](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
