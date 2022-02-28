---
title: Dostosowywanie ochrony przed wyłudzaniem informacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- MET150
description: Administratorzy mogą dowiedzieć się, dlaczego i jak wygląda wiadomość wyłudzająca informacje, która została przez nie Microsoft 365, i co należy zrobić, aby uniknąć kolejnych wiadomości wyłudzających informacje w przyszłości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 299488a7ed8a891d870efb3ace618178c36552f1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988354"
---
# <a name="tune-anti-phishing-protection"></a>Dostosowywanie ochrony przed wyłudzaniem informacji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Mimo Microsoft 365 są dostępne różne funkcje ochrony przed wyłudzaniem informacji, które są domyślnie włączone, istnieje możliwość, że niektóre wiadomości wyłudzące informacje mogą być nadal dostępne w Twoich skrzynkach pocztowych. W tym temacie opisano, co można zrobić, aby dowiedzieć się, dlaczego wiadomość wyłudzająca informacje została za pośrednictwem jej pośrednictwa, i co można zrobić, aby dostosować ustawienia ochrony przed wyłudzaniem informacji w organizacji, Microsoft 365 co _gorsza._

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Przede wszystkim: należy zająć się naruszonymi kontami i zablokować dostęp do kolejnych wiadomości wyłudzających informacje.

Jeśli konto adresata zostało naruszone w wyniku wiadomości służącej do wyłudzania informacji, postępuj zgodnie z instrukcjami w tece Odpowiadanie na naruszone konto e-mail w [programie Microsoft 365](responding-to-a-compromised-email-account.md).

Jeśli Twoja subskrypcja obejmuje program Microsoft Defender for Office 365, możesz użyć analizy zagrożeń [](office-365-ti.md) Office 365 do identyfikowania innych użytkowników, którzy również otrzymali wiadomość wyłudzającą informacje. Masz dodatkowe opcje blokowania wiadomości wyłudzających informacje:

- [Sejf linków w programie Microsoft Defender dla Office 365](set-up-safe-links-policies.md)

- [Sejf załączników w programie Microsoft Defender dla Office 365](set-up-safe-attachments-policies.md)

- [Zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md). Zwróć uwagę, że w zasadach można tymczasowo  zwiększyć progi zaawansowanej wyłudzania informacji z wartości Standardowe na wartości Agresywne **, Bardziej** agresywne lub **Najbardziej agresywne**.

Sprawdź, czy te funkcje Office 365 włączone.

## <a name="report-the-phishing-message-to-microsoft"></a>Zgłaszanie wiadomości wyłudzającej informacje do firmy Microsoft

Zgłaszanie wiadomości wyłudzających informacje jest pomocne przy dostosowywaniu filtrów używanych do ochrony wszystkich klientów w Microsoft 365. Aby uzyskać instrukcje, [zobacz Zgłaszanie wiadomości i plików firmie Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Sprawdzanie nagłówków wiadomości

Możesz sprawdzić nagłówki wiadomości wyłudzającej informacje, aby sprawdzić, czy istnieje coś, co możesz zrobić samodzielnie, aby uniemożliwić dostęp do kolejnych wiadomości wyłudzających informacje. Innymi słowy, można rozsyłać nagłówki wiadomości, aby pomóc w zidentyfikowaniu ustawień w twojej organizacji, które były odpowiedzialnymi za zezwolenie na wiadomości służące do wyłudzania informacji.

W szczególności należy sprawdzić pole **nagłówka X-Forefront-Antispam-Report** w nagłówkach wiadomości pod aby sprawdzić oznaczenia pominiętego filtrowania spamu lub wyłudzania informacji w wartości SfV (Spam Filtering Verdict). Wiadomości pomijające filtrowanie `SCL:-1`będą miały wpis o treści , co oznacza, że jedno z ustawień dopuszczało tę wiadomość, zastępując werdykty spamu lub próby wyłudzenia informacji określone przez usługę. Aby uzyskać więcej informacji na temat sposobu uzyskania nagłówków wiadomości oraz pełnej listy wszystkich dostępnych nagłówków wiadomości ochrony przed spamem i ochrony przed wyłudzaniem informacji, zobacz Nagłówki wiadomości przed [spamem](anti-spam-message-headers.md) w programie Microsoft 365.

## <a name="best-practices-to-stay-protected"></a>Najlepsze rozwiązania dotyczące ochrony

- Comiesięczne uruchamianie [bezpiecznego wyniku](../defender/microsoft-secure-score.md) w celu oceny ustawień zabezpieczeń organizacji.

- W przypadku wiadomości, które są przez pomyłkę poddawane kwarantannie lub dozwolonych przez nie, zalecamy wyszukanie ich w Eksploratorze zagrożeń i wykryciu ich [w czasie rzeczywistym](threat-explorer.md). Możesz wyszukiwać według nadawcy, adresata lub identyfikatora wiadomości. Po odnalezieniu wiadomości przejdź do szczegółów, klikając temat. W przypadku wiadomości poddanej kwarantannie sprawdź, co to jest technologia wykrywania, aby zastąpić ją odpowiednią metodą. W przypadku dozwolonej wiadomości sprawdź, jakie zasady zezwoliły na wiadomość.

- Wiadomości e-mail od sfałszowanych nadawców (adres od wiadomości nie jest zgodne ze źródłem wiadomości) jest klasyfikowany w uchcie Defender for Office 365. Czasami fałszowanie jest szemrane, a użytkownicy nie chcą, aby wiadomości od określonego sfałszowanego nadawcy podlegały kwarantannie. Aby zminimalizować wpływ na użytkowników, należy okresowo przeglądać szczegółowe informacje dotyczące fałszowania [,](learn-about-spoof-intelligence.md) kartę **Fałsz** w obszarze Listy zezwalania [/](tenant-allow-block-list.md)blokowania dzierżawy oraz raport wykrywanie [fałszu](view-email-security-reports.md#spoof-detections-report). Po przejrzeniu dozwolonych i zablokowanych nadawców, którzy są fałszywi, i w razie potrzeby zastępujesz wiadomości, możesz mieć pewność, że skonfigurujesz podejrzaną inteligencję w zasadach ochrony przed wyłudzaniem informacji w celu kwarantanny podejrzanych wiadomości zamiast dostarczania ich do folderu [wiadomości-śmieci](set-up-anti-phishing-policies.md#spoof-settings) użytkownika.

- Możesz powtórzyć powyższy krok dla personifikacji (domeny lub użytkownika) w programie Microsoft Defender dla Office 365. Raport personifikacji znajduje się w obszarze Pulpit **nawigacyjny** \> **zarządzania zagrożeniami** \> **Szczegółowe informacje**.

- Należy okresowo [przeglądać raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report).

- Niektórzy klienci przypadkowo zezwalają na wiadomości wyłudzujące informacje, umieszczając własne domeny na liście Zezwalaj nadawcy lub Zezwalaj na domenę w zasadach ochrony przed spamem. Ta konfiguracja umożliwia dostęp do niektórych normalnych wiadomości, ale umożliwia także blokowanie złośliwych wiadomości, które normalnie byłyby blokowane przez filtry spamu i(lub) wyłudzania informacji. Zamiast zezwalać na dostęp do domeny, musisz rozwiązać problem źródłowy.

  Najlepszym sposobem na zajmowanie się uzasadnionymi wiadomościami zablokowanymi przez program Microsoft 365 (wynik fałszywie dodatni) oznaczających nadawców w Twojej domenie jest pełne i pełne skonfigurowanie rekordów SPF, DKIM i DMARC w systemie DNS dla  wszystkich domen poczty e-mail:

  - Sprawdź, czy rekord SPF identyfikuje wszystkie  źródła poczty e-mail dla nadawców w Twojej domenie (pamiętaj o usługach innych firm).

  - Zadbaj o to,\- aby nieautoryzowani nadawcy (wszyscy) nieautoryzowani nadawcy są odrzucani przez skonfigurowane w tym celu systemy poczty e-mail. Przy użyciu szczegółowych informacji [](learn-about-spoof-intelligence.md) o analizie fałszerzy możesz pomóc w zidentyfikowaniu nadawców korzystających z Twojej domeny, dzięki czemu w rekordzie SPF możesz dołączyć autoryzowanych nadawców z innych firm.

  Aby uzyskać instrukcje dotyczące konfiguracji, zobacz:

  - [Konfigurowanie spf w celu zapobiegania fałszerszem](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny niestandardowej](use-dkim-to-validate-outbound-email.md)

  - [Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail](use-dmarc-to-validate-email.md)

- Jeśli to możliwe, zalecamy dostarczanie wiadomości e-mail z domeny bezpośrednio do Microsoft 365. Innymi słowy wskaż rekord MX Microsoft 365 domeny, aby Microsoft 365. Exchange Online Protection (EOP) może zapewnić najlepszą ochronę dla użytkowników chmury, gdy ich poczta jest dostarczana bezpośrednio do Microsoft 365. Jeśli przed usługą EOP musisz użyć systemu poczty e-mail innej firmy, użyj funkcji rozszerzonego filtrowania dla łączników. Aby uzyskać instrukcje, [zobacz Ulepszone filtrowanie łączników w programie Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Użytkownicy powinni korzystać z [dodatku Report Message](enable-the-report-message-add-in.md) (Wiadomość raportu) lub dodatku Do wyłudzania informacji ( [Report Phishing),](enable-the-report-phish-add-in.md) aby raportować wiadomości do firmy Microsoft, co może pomóc w przeszkolić nasz system. Administratorzy powinni również korzystać z możliwości [przesyłania przez administratora](admin-submission.md) .

- Uwierzytelnianie wieloskładnikowe to dobry sposób na zapobieganie naruszonym kontom. Zdecydowanie należy rozważyć włączenie uwierzytelniania MFA dla wszystkich użytkowników. Aby uzyskać podejście etapowe, zacznij od włączenia uwierzytelniania wieloskładnikowego dla najbardziej poufnych użytkowników (administratorów, kierowników itp.), zanim włączysz uwierzytelniania MFA dla wszystkich użytkowników. Aby uzyskać instrukcje, [zobacz Konfigurowanie uwierzytelniania wieloskładnikowego](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Reguły przesyłania dalej do adresatów zewnętrznych są często używane przez atakujących w celu wyodrębniania danych. Aby znaleźć **reguły przesyłania dalej do** adresatów zewnętrznych, skorzystaj z informacji dotyczących reguł przesyłania dalej skrzynek pocztowych w wynikach bezpiecznego programu [Microsoft](../defender/microsoft-secure-score.md) . Aby uzyskać więcej informacji, zobacz [Ograniczanie reguł przekazywania zewnętrznego klienta przy użyciu bezpiecznego wyniku](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
