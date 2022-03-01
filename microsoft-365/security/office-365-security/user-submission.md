---
title: Ustawienia wiadomości zgłoszone przez użytkownika
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak skonfigurować skrzynkę pocztową do zbierania spamu i wiadomości e-mail wyłudzających informacje zgłaszanych przez użytkowników.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96ec8a32a04768431597c965473974965b2de608
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63020855"
---
# <a name="user-reported-message-settings"></a>Ustawienia wiadomości zgłoszone przez użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z Exchange Online można określić skrzynkę pocztową do odbierania wiadomości zgłaszanych przez użytkowników jako złośliwe. Gdy użytkownicy zgłaszają wiadomości przy użyciu różnych opcji raportowania, za pomocą tej skrzynki pocztowej można przechwytywać wiadomości (wysyłać je tylko do niestandardowej skrzynki pocztowej) lub odbierać kopie wiadomości (wysyłanych do niestandardowej skrzynki pocztowej i firmy Microsoft). Ta funkcja działa z następującymi opcjami raportowania wiadomości:

- [The Report Message add-in](enable-the-report-message-add-in.md)
- [The Report Phishing add-in](enable-the-report-phish-add-in.md)
- [Narzędzia do raportowania innych firm](#third-party-reporting-tools)

Dostarczanie użytkownikom zgłoszonych wiadomości do niestandardowej skrzynki pocztowej, a nie bezpośrednio do firmy Microsoft, umożliwia administratorom selektywne i ręczne zgłaszanie wiadomości do firmy Microsoft przy użyciu przesyłania [administratora](admin-submission.md). Te ustawienia były wcześniej nazywane zasadami przesyłania użytkowników.

  > [!NOTE]
  > Jeśli raportowanie zostało [wyłączone w programie Outlook w sieci Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), włączenie zgłoszonych przez użytkowników wiadomości w tym miejscu zastąpi to ustawienie i umożliwi użytkownikom raportowanie wiadomości w programie Outlook w sieci Web sieci.

## <a name="custom-mailbox-prerequisites"></a>Wymagania wstępne dotyczące niestandardowej skrzynki pocztowej

Użyj następujących artykułów, aby skonfigurować wymagane wymagania wstępne, aby wiadomości zgłoszone przez użytkownika trafiały do Twojej niestandardowej skrzynki pocztowej:

- Pomiń filtrowanie spamu w niestandardowej skrzynce pocztowej, tworząc regułę przepływu poczty programu Exchange w celu ustawienia poziomu ufności spamu. Zobacz [Tworzenie reguły przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) , która ustawia wartość SCL wiadomości w celu ustawienia SCL na **Pomijanie filtrowania spamu**.

- [](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) Utwórz zasady ochrony przed złośliwym oprogramowaniem, które obejmują niestandardową skrzynkę pocztową, w której bezgodzinne automatyczne przeczyszczanie (ZAP) złośliwego oprogramowania jest **wyłączone (** \> sekcja Ustawienia ochrony Włącz automatyczne przeczyszczanie bez godzin dla złośliwego oprogramowania nie jest zaznaczona).

- Utwórz zasady ochrony przed  [spamem](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies), które obejmują niestandardową skrzynkę pocztową, w której są wyłączone wartości ZAP dla spamu i ZAP dla wyłudzania **informacji (** \> nie jest zaznaczona sekcja Automatyczne przeczyszczanie zerowej godziny Włączono automatyczne przeczyszczanie bez godzin).

Jeśli masz program Microsoft Defender dla systemu Office 365, skonfiguruj też następujące ustawienia, aby nasze zaawansowane filtrowanie nie miało wpływu na komunikaty raportowania dla użytkowników:

- [Utwórz zasady usługi Sejf](set-up-safe-links-policies.md), które obejmują niestandardową skrzynkę pocztową, w której skanowanie łączy Sejf jest wyłączone (wybierz akcję dla nieznanych, potencjalnie złośliwych adresów **URL** w sekcji Wiadomości, sekcja \> **Wyłączone**).

- [Tworzenie zasad Sejf załączników](set-up-safe-attachments-policies.md), które obejmują niestandardową skrzynkę pocztową, w której skanowanie załączników Sejf jest wyłączone (**Sejf Załączniki** : odpowiedź z nieznanym złośliwym oprogramowaniem, sekcja \> **Wyłączone**).

Po zweryfikowaniu, że skrzynka pocztowa spełnia wszystkie odpowiednie wymagania wstępne, możesz skonfigurować skrzynkę pocztową przesłań użytkowników za pomocą procedur  procedury z tego artykułu.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Przesyłanie użytkowników**, użyj .<https://security.microsoft.com/reportsubmission>

- Aby zmodyfikować konfigurację przesyłania użytkowników, musisz być członkiem jednej z następujących grup ról:

  - **Zarządzanie organizacją** lub **administrator zabezpieczeń** w [witrynie Uprawnienia w Microsoft 365 Defender sieci.](permissions-microsoft-365-security-center.md)

- Potrzebujesz dostępu do programu Exchange Online PowerShell. Jeśli konto, które próbujesz użyć, nie ma dostępu do programu Exchange Online PowerShell, po określeniu skrzynki pocztowej przesyłania zostanie wyświetlony komunikat o błędzie, który wygląda następująco:

  > Określanie adresu e-mail w domenie

  Aby uzyskać więcej informacji na temat włączania lub wyłączania dostępu do programu Exchange Online PowerShell, zobacz następujące tematy:

  - [Włączanie lub wyłączanie dostępu do programu Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Reguły dostępu klienta w programie Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Konfigurowanie skrzynki Microsoft 365 Defender przesyłania użytkowników za pomocą portalu poczty e-mail

1. W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do **sekcji Zasady i &** \>  \> Zasady zagrożeń, które użytkownik zgłosił ustawienia wiadomości w **sekcji Inne**. Aby przejść bezpośrednio do **strony Przesyłanie użytkowników**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Przesyłanie użytkowników to**, co widzisz, zależy od tego, czy ustawienie przycisku Komunikat raportu Outlook firmy **Microsoft** **jest** wyłączone, czy **Wł.**:

   - **Przycisk włączoną** \>  ![](../../media/scc-toggle-on.png)wiadomość raportu programu Microsoft Outlook.: Zaznacz tę opcję, jeśli używasz dodatku Wiadomość raportu, dodatku Wyłudzanie informacji raportu lub wbudowanego raportowania w programie Outlook w sieci Web, a następnie skonfiguruj następujące ustawienia:
     - **Wyślij zgłoszone wiadomości do**: Wybierz jedną z następujących opcji:
       - **Microsoft**: Skrzynka pocztowa użytkownika przesyłania nie jest używana (wszystkie zgłoszone wiadomości trafiają do firmy Microsoft).
       - **Skrzynka pocztowa firmy Microsoft i mojej organizacji**: W wyświetlonym oknie wprowadź adres e-mail istniejącej skrzynki Exchange Online pocztowej. Grupy dystrybucyjne są niedozwolone. Zgłoszenia użytkowników zostaną przejestrowane zarówno do firmy Microsoft w celu analizy, jak i do niestandardowej skrzynki pocztowej analizowanych przez administratora lub zespół operacyjny zabezpieczeń.
       - **Skrzynka pocztowa mojej organizacji**: W wyświetlonym oknie wprowadź adres e-mail istniejącej skrzynki Exchange Online pocztowej. Grupy dystrybucyjne są niedozwolone. Użyj tej opcji, jeśli chcesz, aby komunikat był najpierw przekierowyny tylko do administratora lub zespołu operacji zabezpieczeń do analizy. Wiadomości nie będą wysyłane do firmy Microsoft, chyba że administrator sam je przekaże.

          > [!IMPORTANT]
          > Organizacje rządowe Stanów Zjednoczonych (GCC, GCC High i DoD) mogą konfigurować skrzynkę **pocztową mojej organizacji**. Pozostałe dwie opcje są wyłączone.
          >
          > Jeśli organizacje są skonfigurowane do wysyłania tylko do niestandardowych skrzynek pocztowych, zgłoszone wiadomości nie będą wysyłane do ponownego wysłania, a wyniki w portalu Wiadomości zgłoszone przez użytkowników będą zawsze puste.

       Niezależnie od wartości wybranej dla **opcji Wyślij zgłoszone wiadomości** do dostępne są następujące ustawienia:

       - **Umożliwianie użytkownikom wyboru, czy chcą raportować swoje wiadomości do firmy Microsoft**
       - **Wybierz opcje raportowania dostępne dla użytkowników** w sekcji: Wybierz co najmniej jedną z następujących opcji:
         - **Zapytaj mnie przed wysłaniem wiadomości**
         - **Zawsze zgłoś wiadomość**
         - **Nigdy nie zgłoś wiadomości**

          > [!CAUTION]
          > Jeśli wyłączono raportowanie wiadomości-śmieci w programie [Outlook w sieci Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) przy użyciu zasad skrzynki pocztowej programu Outlook w sieci Web, ale dowolne z poprzednich ustawień zostało skonfigurowane w celu zgłaszania wiadomości do firmy Microsoft, użytkownicy będą mogli raportować wiadomości do firmy Microsoft w programie Outlook w sieci Web przy użyciu dodatku Wiadomość raportu lub dodatku wyłudzania informacji raportów .

     Pozostaw **przełącznik Opcji Outlook** ![](../../media/scc-toggle-on.png) wiadomości raportu firmy Microsoft wł. w celu umożliwienia użytkownikom końcowych zgłaszania wiadomości fałszywie dodatnich z portalu kwarantanny.

     - **Sekcja Środowisko raportowania użytkowników**
       - **Karta Przed** raportowaniem: W  polach  Tytuł i Treść wiadomości wprowadź tekst opisu wyświetlany użytkownikom przed zgłoszeniem wiadomości za pomocą dodatku Wiadomość raportu lub dodatku Wyłudzanie informacji raportu. Za pomocą zmiennej %type% możesz uwzględnić typ przesyłania (wiadomość-śmieć, a nie wiadomość-śmieć, wyłud itp.).
       - **Po raportowaniu**: W polach Tytuł  i Komunikat potwierdzenia wprowadź tekst opisu wyświetlany użytkownikom po zrzucie raportu za pomocą dodatku Wiadomość raportu lub dodatku Wyłudzanie informacji raportu. Aby uwzględnić typ przesyłania, możesz użyć zmiennej %type%.
       - **Wyświetlanie tylko wtedy, gdy użytkownik zgłasza** wyłudzanie informacji: Zaznacz tę opcję, jeśli chcesz, aby wiadomość była wyświetlana tylko w przypadku zgłoszenia jej jako wiadomości wyłudzającej informacje. W innym przypadku będą wyświetlane zaznaczone wiadomości dla każdego rodzaju raportu.

       Jak pokazano na stronie, jeśli wybierzesz opcję, która wysyła zgłoszone wiadomości do firmy Microsoft, do powiadomienia zostanie również dodany następujący tekst:

          > Twoja wiadomość e-mail zostanie przesłana do firmy Microsoft w stanie, w stanie, w ile jest, do analizy. Niektóre wiadomości e-mail mogą zawierać informacje osobiste lub poufne.

   - Wyłącz przełącznik Komunikat raportu programu **Microsoft Outlook** \>  ![.](../../media/scc-toggle-off.png): Zaznacz tę opcję, jeśli korzystasz z narzędzi do raportowania innych firm, a nie z dodatku Wiadomość raportu, dodatku Wyłudzanie raportów lub wbudowanego raportowania w programie Outlook w sieci Web, a następnie skonfiguruj następujące ustawienia:
     - Zaznacz **pole wyboru Użyj tej niestandardowej skrzynki pocztowej do odbierania zgłoszonych przez użytkowników przesyłania**. W wyświetlonym oknie wprowadź adres e-mail istniejącej skrzynki Exchange Online pocztowej, która może odbierać wiadomości e-mail.

   - **Przycisk Outlook raportu firmy Microsoft**: Włącz tę funkcję, jeśli chcesz, aby użytkownicy końcowi zgłaszali wiadomości z kwarantanny.

   Po zakończeniu kliknij pozycję **Potwierdź**. Aby wyczyścić te wartości, kliknij pozycję **Przywróć.**

## <a name="third-party-reporting-tools"></a>Narzędzia do raportowania innych firm

Narzędzia do raportowania wiadomości innych firm można skonfigurować w celu wysyłania zgłoszonych wiadomości do niestandardowej skrzynki pocztowej. Można to zrobić, ustawiając dla przycisku Komunikat raportu Outlook firmy **Microsoft** ustawienie Wyłączone i  ustawiając skrzynkę  pocztową mojej organizacji na Office 365 skrzynkę pocztową.

Jedynym wymaganiem jest to, że oryginalna wiadomość jest dołączona jako . EML lub . Załącznik MSG (nie skompresowany) w wiadomości wysyłanej do niestandardowej skrzynki pocztowej (nie tylko przesyłaj dalej oryginalną wiadomość do niestandardowej skrzynki pocztowej).

Wymagania dotyczące formatowania wiadomości opisano w następnej sekcji. Formatowanie jest opcjonalne, ale jeśli nie jest zgodne z  zalecanym formatem, raporty zawsze będą przesyłane jako wyłudzy.

## <a name="message-submission-format"></a>Format przesyłania wiadomości

Aby prawidłowo zidentyfikować oryginalne dołączone wiadomości, wiadomości wysyłane do niestandardowej skrzynki pocztowej wymagają określonego formatowania. Jeśli wiadomości nie mają tego formatu, oryginalne dołączone wiadomości są zawsze identyfikowane jako materiały służące do wyłudzania informacji.

Jeśli chcesz określić zgłoszoną przyczynę oryginalnych załączonych wiadomości, wiadomości wysyłane do niestandardowej skrzynki pocztowej (nie modyfikuj załączników) muszą zaczynać się od jednego z następujących prefiksów w temacie (tytuł koperty):

- 1| lub Wiadomości-śmieci:
- 2| lub Niebędące śmieciem
- 3| lub wyłudzanie informacji

Przykład:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Obie te wiadomości są zgłaszane jako wiadomości niebędące śmieciem na podstawie tematu.
- Reszta jest ignorowana.


Wiadomości, które nie są zgodne z tym formatem, nie będą prawidłowo wyświetlane w portalu Materiały.
