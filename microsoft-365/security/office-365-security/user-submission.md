---
title: Ustawienia komunikatów zgłoszonych przez użytkownika
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
description: Administratorzy mogą dowiedzieć się, jak skonfigurować skrzynkę pocztową do zbierania wiadomości e-mail dotyczących spamu i wyłudzania informacji zgłaszanych przez użytkowników.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a2e57c5dbfb8738eb9e554a3207679bfd48c6f60
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970917"
---
# <a name="user-reported-message-settings"></a>Ustawienia komunikatów zgłoszonych przez użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji z Exchange Online skrzynkami pocztowymi można określić skrzynkę pocztową do odbierania wiadomości zgłaszanych przez użytkowników jako złośliwe lub złośliwe. Gdy użytkownicy zgłaszają wiadomości przy użyciu różnych opcji raportowania, możesz użyć tej skrzynki pocztowej do przechwytywania wiadomości (wysyłać tylko do niestandardowej skrzynki pocztowej) lub odbierać kopie wiadomości (wysyłać do niestandardowej skrzynki pocztowej i firmy Microsoft). Ta funkcja działa z następującymi opcjami raportowania komunikatów:

- [Dodatek Komunikat raportu](enable-the-report-message-add-in.md)
- [Dodatek Raport wyłudzający informacje](enable-the-report-phish-add-in.md)
- [Narzędzia do raportowania innych firm](#third-party-reporting-tools)

Dostarczanie wiadomości zgłoszonych przez użytkownika do niestandardowej skrzynki pocztowej zamiast bezpośrednio do firmy Microsoft umożliwia administratorom selektywne i ręczne zgłaszanie wiadomości do firmy Microsoft przy użyciu [przesyłania przez administratora](admin-submission.md). Te ustawienia były wcześniej nazywane zasadami przesyłania użytkowników.

  > [!NOTE]
  > Jeśli raportowanie zostało [wyłączone w Outlook w sieci Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), włączenie w tym miejscu komunikatów zgłoszonych przez użytkownika spowoduje zastąpienie tego ustawienia i umożliwi użytkownikom ponowne zgłaszanie komunikatów w Outlook w sieci Web.

## <a name="custom-mailbox-prerequisites"></a>Wymagania wstępne niestandardowej skrzynki pocztowej

Poniższe artykuły umożliwiają skonfigurowanie wymaganych wymagań wstępnych, aby wiadomości zgłaszane przez użytkownika przechodziły do niestandardowej skrzynki pocztowej:

- Pomiń filtrowanie spamu w niestandardowej skrzynce pocztowej, tworząc regułę przepływu poczty exchange, aby ustawić poziom ufności spamu. Zobacz [Używanie umowy EAC do tworzenia reguły przepływu poczty, która ustawia listę SCL wiadomości](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) , aby ustawić listę SCL na **wartość Pomijanie filtrowania spamu**.

- [Utwórz zasady ochrony przed złośliwym oprogramowaniem](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies), które obejmują niestandardową skrzynkę pocztową, w której jest wyłączone automatyczne przeczyszczanie o wartości zero godzin (ZAP) dla złośliwego oprogramowania (sekcja \>**Ustawienia ochrony** **Włącz automatyczne przeczyszczanie bez godzin dla złośliwego oprogramowania** nie jest zaznaczona).

- [Utwórz zasady ochrony przed spamem](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) , które obejmują niestandardową skrzynkę pocztową, w której zap dla spamu i zap dla wyłudzania informacji są wyłączone (**zero godzin auto przeczyszczania** sekcja \> **Włączone zero godzin auto przeczyszczania (ZAP)** nie jest zaznaczone).

Jeśli masz Ochrona usługi Office 365 w usłudze Microsoft Defender, należy również skonfigurować następujące ustawienia, aby nasze zaawansowane filtrowanie nie miało wpływu na użytkowników zgłaszających komunikaty:

- [Utwórz zasady Sejf Links zawierające niestandardową](set-up-safe-links-policies.md) skrzynkę pocztową, w której skanowanie Sejf Łącza jest wyłączone (**wybierz akcję dla nieznanych potencjalnie złośliwych adresów URL w** sekcji \> Wiadomości **Wyłączone**).

- [Utwórz zasady załączników Sejf](set-up-safe-attachments-policies.md), które zawierają niestandardową skrzynkę pocztową, w której skanowanie Sejf Załączniki jest wyłączone (**Sejf Załączniki — nieznane złośliwe oprogramowanie — sekcja** \> **Wyłączona**).

Po upewnieniu się, że skrzynka pocztowa spełnia wszystkie odpowiednie wymagania wstępne, możesz użyć procedur w tym artykule, aby skonfigurować skrzynkę pocztową przesyłania użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Przesyłanie użytkowników** , użyj polecenia <https://security.microsoft.com/userSubmissionsReportMessage>.

- Aby zmodyfikować konfigurację przesyłania użytkowników, musisz być członkiem jednej z następujących grup ról:

  - **Zarządzanie organizacją** lub **administrator zabezpieczeń** w obszarze [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Potrzebujesz dostępu do Exchange Online programu PowerShell. Jeśli konto, którego próbujesz użyć, nie ma dostępu do Exchange Online programu PowerShell, podczas określania skrzynki pocztowej przesyłania zostanie wyświetlony komunikat o błędzie, który wygląda następująco:

  > Określanie adresu e-mail w domenie

  Aby uzyskać więcej informacji na temat włączania lub wyłączania dostępu do programu Exchange Online programu PowerShell, zobacz następujące tematy:

  - [Włączanie lub wyłączanie dostępu do Exchange Online programu PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Reguły dostępu klienta w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Konfigurowanie skrzynki pocztowej przesyłania użytkowników przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady & reguły** \> **zasad** \> zagrożeń **Ustawienia komunikatów zgłoszonych przez użytkownika** w sekcji **Inne**. Aby przejść bezpośrednio do strony **Przesyłanie użytkowników** , użyj polecenia <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Na stronie **Przesyłanie użytkowników** to, co widzisz, zależy od tego, czy ustawienie **przycisku Komunikat raportu firmy Microsoft Outlook** jest **wyłączone**, czy **włączone**:

   - Przycisk \> **Komunikat raportu firmy Microsoft Outlook** **włączony**![](../../media/scc-toggle-on.png): wybierz tę opcję, jeśli używasz dodatku Komunikat raportu, dodatku Wyłudzanie informacji o raportach lub wbudowanego raportowania w Outlook w sieci Web, a następnie skonfiguruj następujące ustawienia:
     - **Wyślij zgłoszone komunikaty do**: Wybierz jedną z następujących opcji:
       - **Microsoft**: Skrzynka pocztowa przesyłania przez użytkownika nie jest używana (wszystkie zgłoszone wiadomości trafiają do firmy Microsoft).
       - **Skrzynka pocztowa firmy Microsoft i mojej organizacji**: w wyświetlonym polu wprowadź adres e-mail istniejącej skrzynki pocztowej Exchange Online. Grupy dystrybucyjne są niedozwolone. Przesłania użytkowników zostaną przesłane zarówno do firmy Microsoft w celu analizy, jak i do niestandardowej skrzynki pocztowej dla administratora lub zespołu ds. operacji zabezpieczeń w celu przeanalizowania.
       - **Skrzynka pocztowa mojej organizacji**: w wyświetlonym polu wprowadź adres e-mail istniejącej skrzynki pocztowej Exchange Online. Grupy dystrybucyjne są niedozwolone. Użyj tej opcji, jeśli chcesz, aby komunikat najpierw został przesłany do administratora lub zespołu ds. operacji zabezpieczeń. Komunikaty nie zostaną przekazane do firmy Microsoft, chyba że administrator przekaże je samodzielnie.

          > [!IMPORTANT]
          > Organizacje rządowe Stanów Zjednoczonych (GCC, GCC High i DoD) mogą konfigurować tylko **skrzynkę pocztową mojej organizacji**. Pozostałe dwie opcje są wyłączone.
          >
          > Jeśli organizacje są skonfigurowane do wysyłania tylko do niestandardowej skrzynki pocztowej, zgłoszone wiadomości nie zostaną wysłane do ponownego przeskanowania, a wyniki w portalu wiadomości zgłoszonych przez użytkownika będą zawsze puste.

       Niezależnie od wartości wybranej dla opcji **Wyślij zgłoszone komunikaty do** są dostępne następujące ustawienia:

       - **Pozwól użytkownikom wybrać, czy chcą zgłosić wiadomość do firmy Microsoft**
       - **Wybierz opcje raportowania dostępne dla użytkowników** : Wybierz co najmniej jedną z następujących opcji:
         - **Zapytaj mnie przed wysłaniem wiadomości**
         - **Zawsze zgłaszaj komunikat**
         - **Nigdy nie zgłaszaj komunikatu**

          > [!CAUTION]
          > Jeśli [w Outlook w sieci Web wyłączono raportowanie wiadomości-śmieci](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) przy użyciu zasad Outlook w sieci Web skrzynki pocztowej, ale skonfigurowano dowolne z poprzednich ustawień do raportowania wiadomości do firmy Microsoft, użytkownicy będą mogli zgłaszać wiadomości do firmy Microsoft w Outlook w sieci Web przy użyciu dodatku Komunikat raportu lub dodatku Wyłudzanie informacji raportów .

     Pozostaw ustawienie ![**przycisku Komunikat raportu firmy Microsoft Outlook** **Włącz,**](../../media/scc-toggle-on.png) aby umożliwić użytkownikom końcowym zgłaszanie fałszywie dodatnich komunikatów z portalu kwarantanny.

     - **Sekcja środowiska raportowania użytkowników**
       - **Karta Przed raportowaniem** : W polach **Tytuł** i **Treść komunikatu** wprowadź opisowy tekst widoczny przez użytkowników przed zgłoszeniem komunikatu przy użyciu dodatku Komunikat raportu lub dodatku Wyłudzanie informacji o raporcie. Zmienna %type% umożliwia uwzględnienie typu przesyłania (śmieci, nie śmieci, phish itp.).
       - **Po karcie raportowania** : w polach **Tytuł** i **potwierdzenie wprowadź** opisowy tekst wyświetlany przez użytkowników po zgłoszeniu wiadomości przy użyciu dodatku Komunikat raportu lub dodatku Wyłudzanie informacji o raporcie. Możesz użyć zmiennej %type% do uwzględnienia typu przesyłania.
       - **Wyświetlane tylko wtedy, gdy użytkownik zgłasza wyłudzanie informacji**: sprawdź tę opcję, jeśli chcesz wyświetlić wiadomość tylko wtedy, gdy wiadomość e-mail zostanie zgłoszona jako phish. Jeśli nie, zaznaczone komunikaty będą wyświetlane dla dowolnego rodzaju raportu.

       Jak pokazano na stronie, jeśli wybierzesz opcję, która wysyła zgłoszone komunikaty do firmy Microsoft, do powiadomienia zostanie również dodany następujący tekst:

          > Wiadomość e-mail zostanie przesłana w stanie rzeczywistym do firmy Microsoft w celu analizy. Niektóre wiadomości e-mail mogą zawierać informacje osobiste lub poufne.

   - Przycisk \> **Komunikat raportu firmy Microsoft Outlook** **Wyłączanie** ![przełącznika.](../../media/scc-toggle-off.png) Wybierz tę opcję, jeśli używasz narzędzi do raportowania innych firm zamiast dodatku Komunikat raportu, dodatku Wyłudzanie informacji o raportach lub wbudowanego raportowania w Outlook w sieci Web, a następnie skonfiguruj następujące ustawienia:
     - Wybierz pozycję **Użyj tej niestandardowej skrzynki pocztowej, aby odbierać zgłoszenia zgłaszane przez użytkownika**. W wyświetlonym polu wprowadź adres e-mail istniejącej skrzynki pocztowej Exchange Online, która może odbierać wiadomości e-mail.

   - **Przycisk komunikatu raportu kwarantanny**: włącz tę funkcję, jeśli chcesz zezwolić użytkownikom końcowym na zgłaszanie komunikatów z kwarantanny.

3. Po zakończeniu kliknij przycisk **Potwierdź**. Aby wyczyścić te wartości, kliknij przycisk **Przywróć**.

## <a name="third-party-reporting-tools"></a>Narzędzia do raportowania innych firm

Możesz skonfigurować narzędzia do raportowania wiadomości innych firm, aby wysyłać zgłoszone wiadomości do niestandardowej skrzynki pocztowej. W tym celu należy **ustawić ustawienie przycisku Komunikat raportu firmy Microsoft Outlook** na **Wartość Wyłączone** i ustawić **skrzynkę pocztową mojej organizacji** na wybraną Office 365 skrzynkę pocztową.

Jedynym wymaganiem jest uwzględnienie oryginalnego komunikatu jako . EML lub . Załącznik msg (nieskompresowany) w wiadomości wysyłanej do niestandardowej skrzynki pocztowej (nie przekazuj oryginalnej wiadomości do niestandardowej skrzynki pocztowej). 

 > [!NOTE]
 > Jeśli w wiadomości e-mail znajduje się wiele załączników wiadomości e-mail, przesłanie zostanie odrzucone. Obsługujemy tylko wiadomości e-mail z jednym załącznikiem wiadomości e-mail.

Wymagania dotyczące formatowania komunikatów zostały opisane w następnej sekcji. Formatowanie jest opcjonalne, ale jeśli nie jest zgodne z określonym formatem, raporty będą zawsze przesyłane jako phish.

## <a name="message-submission-format"></a>Format przesyłania wiadomości

Aby poprawnie zidentyfikować oryginalne dołączone wiadomości, wiadomości wysyłane do niestandardowej skrzynki pocztowej wymagają określonego formatowania. Jeśli wiadomości nie używają tego formatu, oryginalne dołączone komunikaty są zawsze identyfikowane jako przesłania wyłudzające informacje.

Jeśli chcesz określić zgłoszoną przyczynę oryginalnych dołączonych wiadomości, wiadomości wysyłane do niestandardowej skrzynki pocztowej (nie modyfikują załącznika) muszą zaczynać się od jednego z następujących prefiksów w temacie (tytuł koperty):

- 1| lub Śmieci:
- 2| lub Nie śmieci:
- 3| lub wyłudzanie informacji:

Przykład:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Oba te komunikaty są zgłaszane jako nie-śmieci na podstawie tematu.
- Reszta jest ignorowana.

Komunikaty, które nie są zgodne z tym formatem, nie będą wyświetlane poprawnie w portalu Przesłane.
