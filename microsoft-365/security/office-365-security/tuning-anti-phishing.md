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
description: Administratorzy mogą dowiedzieć się, dlaczego i jak wyłudzać informacje w Microsoft 365 oraz co zrobić, aby zapobiec wyłudzaniu informacji w przyszłości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7c39d3f4b3ee6fb98cadcd5518a81710402c1cb3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647760"
---
# <a name="tune-anti-phishing-protection"></a>Dostosowywanie ochrony przed wyłudzaniem informacji

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Chociaż Microsoft 365 oferuje różne funkcje ochrony przed wyłudzaniem informacji, które są domyślnie włączone, możliwe jest, że niektóre wiadomości wyłudzające informacje mogą nadal przechodzić do skrzynek pocztowych. W tym temacie opisano, co można zrobić, aby dowiedzieć się, dlaczego dotarła wiadomość wyłudzająca informacje i co możesz zrobić, aby dostosować ustawienia ochrony przed wyłudzaniem informacji w organizacji Microsoft 365 _bez przypadkowego pogorszenia sytuacji_.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Najpierw: zajmij się wszelkimi kontami, których zabezpieczenia zostały naruszone, i upewnij się, że blokujesz dostęp do kolejnych wiadomości wyłudzających informacje

Jeśli w wyniku wiadomości wyłudzającej informacje konto odbiorcy zostało naruszone, wykonaj kroki opisane [w temacie Odpowiadanie na naruszone konto e-mail w Microsoft 365](responding-to-a-compromised-email-account.md).

Jeśli Twoja subskrypcja obejmuje Ochrona usługi Office 365 w usłudze Microsoft Defender, możesz użyć [Office 365 Threat Intelligence](office-365-ti.md), aby zidentyfikować innych użytkowników, którzy również otrzymali wiadomość wyłudzającą informacje. Dostępne są dodatkowe opcje blokowania wiadomości wyłudzających informacje:

- [linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md)

- [Sejf załączników w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-attachments-policies.md)

- [Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md). Pamiętaj, że możesz tymczasowo zwiększyć **progi zaawansowanego wyłudzania informacji w zasadach** od **standardowego** do **agresywnego**, **bardziej agresywnego** lub **najbardziej agresywnego**.

Sprawdź, czy te funkcje Ochrona usługi Office 365 w usłudze Defender są włączone.

## <a name="report-the-phishing-message-to-microsoft"></a>Zgłoś wiadomość wyłudzającą informacje firmie Microsoft

Raportowanie wiadomości wyłudzających informacje jest pomocne w dostrajaniu filtrów, które są używane do ochrony wszystkich klientów w Microsoft 365. Aby uzyskać instrukcje, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Sprawdzanie nagłówków komunikatów

Możesz sprawdzić nagłówki wiadomości wyłudzającej informacje, aby sprawdzić, czy istnieje coś, co możesz zrobić samodzielnie, aby zapobiec przepływaniu większej liczby wiadomości wyłudzających informacje. Innymi słowy, badanie nagłówków komunikatów może pomóc w zidentyfikowaniu ustawień w organizacji, które były odpowiedzialne za zezwolenie na wyłudzanie wiadomości.

W szczególności należy sprawdzić pole nagłówka **X-Forefront-Antispam-Report** w nagłówkach wiadomości pod kątem oznak pominięcia filtrowania pod kątem spamu lub wyłudzania informacji w wartości Werdykt filtrowania spamu (SFV). Komunikaty pomijające filtrowanie będą miały wpis o `SCL:-1`wartości , co oznacza, że jedno z ustawień zezwala na tę wiadomość przez zastąpienie spamu lub werdyktów wyłudzających informacje, które zostały określone przez usługę. Aby uzyskać więcej informacji na temat pobierania nagłówków wiadomości i pełnej listy wszystkich dostępnych nagłówków wiadomości antyspamowych i anty-phishingowych, zobacz [Nagłówki wiadomości antyspamowych w Microsoft 365](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Najlepsze rozwiązania dotyczące zachowania ochrony

- Co miesiąc uruchom polecenie [Wskaźnik](../defender/microsoft-secure-score.md) bezpieczeństwa, aby ocenić ustawienia zabezpieczeń organizacji.

- W przypadku komunikatów, które są poddawane kwarantannie przez pomyłkę lub komunikatów, które są dozwolone, zalecamy wyszukanie tych [komunikatów w Eksploratorze zagrożeń i wykrywaniu w czasie rzeczywistym](threat-explorer.md). Możesz wyszukiwać według nadawcy, adresata lub identyfikatora wiadomości. Po zlokalizowaniu wiadomości przejdź do szczegółów, klikając temat. W przypadku komunikatu poddanej kwarantannie sprawdź, co to jest "technologia wykrywania", aby można było zastąpić odpowiednią metodę. Aby uzyskać dozwolony komunikat, sprawdź, które zasady zezwalają na komunikat.

- Wiadomości e-mail od sfałszowanych nadawców (adres od wiadomości nie jest zgodny ze źródłem wiadomości) jest klasyfikowany jako wyłudzanie informacji w Ochrona usługi Office 365 w usłudze Defender. Czasami fałszowanie jest łagodne, a czasami użytkownicy nie chcą, aby wiadomości od określonego sfałszowanego nadawcy były poddawane kwarantannie. Aby zminimalizować wpływ na użytkowników, okresowo przeglądaj [szczegółowe informacje na temat fałszowania,](learn-about-spoof-intelligence.md) kartę **Fałszowanie** na [liście dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) oraz [raport Wykrywanie fałszowania](view-email-security-reports.md#spoof-detections-report). Po przejrzeniu dozwolonych i zablokowanych sfałszowanych nadawców i wykonaniu wszelkich niezbędnych zastąpień możesz mieć pewność, że [skonfigurujesz analizę fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings) w celu **kwarantanny** podejrzanych wiadomości zamiast dostarczać je do folderu Wiadomości-śmieci użytkownika.

- Powyższy krok można powtórzyć dla pozycji Personifikacja (domena lub użytkownik) w Ochrona usługi Office 365 w usłudze Microsoft Defender. Raport personifikacji znajduje się w obszarze **Pulpit nawigacyjny** \> **zarządzania zagrożeniami** \> **Szczegółowe informacje**.

- Okresowo przeglądaj [raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report).

- Niektórzy klienci niechcący zezwalają na wyłudzanie informacji, umieszczając własne domeny na liście Zezwalaj nadawcy lub Zezwalaj na domenę w zasadach ochrony przed spamem. Mimo że ta konfiguracja umożliwi korzystanie z pewnych legalnych komunikatów, będzie również zezwalać na złośliwe wiadomości, które normalnie byłyby blokowane przez filtry spamu i/lub wyłudzania informacji. Zamiast zezwalać na domenę, należy rozwiązać podstawowy problem.

  Najlepszym sposobem radzenia sobie z legalnymi wiadomościami, które są blokowane przez Microsoft 365 (wyniki fałszywie dodatnie), które obejmują nadawców w domenie, jest pełne i całkowite skonfigurowanie rekordów SPF, DKIM i DMARC w systemie DNS dla _wszystkich_ domen poczty e-mail:

  - Sprawdź, czy rekord SPF identyfikuje _wszystkie_ źródła wiadomości e-mail dla nadawców w domenie (nie zapomnij o usługach innych firm!).

  - Użyj twardych błędów (\-wszystkie), aby upewnić się, że nieautoryzowani nadawcy są odrzucane przez skonfigurowane systemy poczty e-mail. Możesz użyć [analizy fałszowania,](learn-about-spoof-intelligence.md) aby ułatwić identyfikowanie nadawców korzystających z twojej domeny, aby można było dołączyć autoryzowanych nadawców innych firm do rekordu SPF.

  Aby uzyskać instrukcje dotyczące konfiguracji, zobacz:

  - [Konfigurowanie platformy SPF w celu zapobiegania spoofingowi](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Sprawdzanie poprawności wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej za pomocą funkcji DKIM](use-dkim-to-validate-outbound-email.md)

  - [Sprawdzanie poprawności poczty e-mail przy użyciu usługi DMARC](use-dmarc-to-validate-email.md)

- Jeśli to możliwe, zalecamy dostarczenie wiadomości e-mail dla domeny bezpośrednio do Microsoft 365. Innymi słowy, wskaż rekord MX domeny Microsoft 365, aby Microsoft 365. Exchange Online Protection (EOP) jest w stanie zapewnić najlepszą ochronę użytkownikom chmury, gdy ich poczta jest dostarczana bezpośrednio do Microsoft 365. Jeśli przed operacją EOP należy użyć systemu higieny poczty e-mail innej firmy, użyj funkcji filtrowania rozszerzonego dla łączników. Aby uzyskać instrukcje, zobacz [Rozszerzone filtrowanie łączników w Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Użytkownicy powinni używać [dodatku Komunikat raportu](enable-the-report-message-add-in.md) lub [dodatku Wyłudzanie informacji raportów,](enable-the-report-phish-add-in.md) aby zgłaszać komunikaty firmie Microsoft, co może wytrenować nasz system. Administratorzy powinni również korzystać z możliwości [przesyłania przez administratora](admin-submission.md) .

- Uwierzytelnianie wieloskładnikowe (MFA) to dobry sposób zapobiegania naruszonym kontom. Należy zdecydowanie rozważyć włączenie uwierzytelniania wieloskładnikowego dla wszystkich użytkowników. W przypadku podejścia etapowego rozpocznij od włączenia uwierzytelniania wieloskładnikowego dla najbardziej wrażliwych użytkowników (administratorów, kadry kierowniczej itp.) przed włączeniem uwierzytelniania wieloskładnikowego dla wszystkich. Aby uzyskać instrukcje, zobacz [Konfigurowanie uwierzytelniania wieloskładnikowego](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Reguły przekazywania do adresatów zewnętrznych są często używane przez osoby atakujące do wyodrębniania danych. Aby znaleźć reguły przekazywania dalej do adresatów zewnętrznych, skorzystaj z informacji o **regułach przekazywania przejrzyj skrzynkę pocztową** w usłudze [Microsoft Secure Score](../defender/microsoft-secure-score.md) . Aby uzyskać więcej informacji, zobacz [Mitigating Client External Forwarding Rules with Secure Score (Ograniczanie reguł przekazywania zewnętrznego klienta przy użyciu wskaźnika bezpieczeństwa](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score)).
