---
title: Zarządzanie kontami priorytetów i monitorowanie ich
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
description: Monitorowanie nieudanych i opóźnionych wiadomości e-mail wysyłanych na lub z kont o wysokim wpływie na działalność.
ms.openlocfilehash: b8762885cc54859cf927653abb14858c0094ea12
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987794"
---
# <a name="manage-and-monitor-priority-accounts"></a>Zarządzanie kontami priorytetów i monitorowanie ich

W każdej Microsoft 365 organizacji istnieją osoby, które są istotne, na przykład kierownicy, liderzy, menedżerowie lub inni użytkownicy, którzy mają dostęp do informacji poufnych, zastrzeżonych lub o wysokim priorytecie.

Aby ułatwić chronienie tych kont w organizacji, możesz teraz wyznaczyć określonych użytkowników jako konta priorytetowe i korzystać z funkcji specyficznych dla aplikacji, które zapewniają im dodatkową ochronę. W przyszłości więcej aplikacji i funkcji będzie obsługiwać konta o priorytecie, a na początek ogłosiliśmy dwie **możliwości:** priorytetową ochronę konta i premium monitorowanie przepływu **poczty**.

- **Priorytetowa ochrona konta** — usługa Microsoft Defender for Office 365 (wcześniej Office 365 Advanced Threat Protection) obsługuje konta priorytetów jako tagi, których można używać w filtrach alertów, raportów i badań. Aby uzyskać więcej informacji, zobacz [Tagi użytkownika w programie Microsoft Defender dla Office 365](../../security/office-365-security/user-tags.md).

  Naturalne pytanie brzmi: "Czy nie wszyscy użytkownicy są priorytetami? Dlaczego nie wyznaczyć wszystkich użytkowników jako kont priorytetowych?" Tak, wszyscy użytkownicy mają priorytet, ale ochrona konta o priorytecie zapewnia następujące dodatkowe korzyści:

  - **Dodatkowa heuristics**: Nasza analiza przepływu poczty e-mail w centrach danych firmy Microsoft wskazuje, że wzorce przepływu poczty dla kadry kierowniczej w firmie różnią się od średnich pracowników. Priorytetowa ochrona konta zapewnia dodatkowe heuristics, które są specjalnie dostosowane do kadry kierowniczej w firmie, co nie byłoby korzystne dla zwykłego pracownika.
  - **Dodatkowa widoczność raportów**: W efekcie w alertach, raportach i badaniach są już dostępne informacje dotyczące wszystkich użytkowników (lub wszystkich użytkowników, których to dotyczy). Tag kont priorytetu jako filtr umożliwia kierowanie konkretnie twoich badań.

- **Premium monitorowanie poczty Flow** - Prawidłowe przepływy poczty mogą być krytyczne dla sukcesu biznesowego, a opóźnienia lub niepowodzenia dostarczenia mogą mieć negatywny wpływ na działalność firmy. Możesz wybrać próg dla wiadomości e-mail nieudanych lub opóźnionych, otrzymywać alerty po jego przekroczeniu oraz wyświetlać raport o problemach z pocztą e-mail dla kont priorytetowych. Aby uzyskać więcej informacji, zapoznaj się z raportem Problemy z pocztą e-mail dla kont priorytetowych [w nowoczesnym Centrum arytmii](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Aby uzyskać najważniejsze wskazówki dotyczące zabezpieczeń w przypadku kont priorytetowych, zobacz [Zalecenia dotyczące zabezpieczeń dla kont priorytetowych](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Funkcja **ochrony konta Priority (Priorytet)** opisana w tym temacie jest dostępna tylko dla organizacji, które spełniają następujące wymagania:

- Program Microsoft Defender dla Office 365 Plan 2, łącznie z Office 365 E3, Office 365 E5, Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5.

Funkcja **Premium monitorowanie poczty Flow**, opisana w tym temacie, jest dostępna tylko dla organizacji, które spełniają następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji co najmniej 5000 licencji jednego z następujących produktów lub ich kombinacji: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Na przykład organizacja może mieć 3000 Office 365 E3 licencji i 2500 Microsoft 365 E5, co łącznie 5500 licencji z kwalifikujących się produktów.
- Twoja organizacja musi mieć co najmniej 50 aktywnych użytkowników co najmniej 50 miesięcznie dla co najmniej jednego podstawowego obciążenia pracą— usługi Teams, usługi One Drive dla Firm, usługi SharePoint Online, aplikacji Exchange Online i Office firm.

> [!NOTE]
> Możesz monitorować maksymalnie 250 kont priorytetowych.

Podczas stosowania ochrony konta priorytetowego do skrzynki pocztowej należy również stosować ochronę konta priorytetu do użytkowników, którzy mają dostęp do skrzynki pocztowej (na przykład dyrektor generalny i asystent dyrektora generalnego, który zarządza kalendarzem dyrektora generalnego).

### <a name="add-priority-accounts-from-the-setup-page"></a>Dodawanie kont priorytetowych na stronie Konfiguracja

Dodaj konta o priorytecie na **stronie Konfiguracja**.

1. Przejdź do centrum administracyjne platformy Microsoft 365 stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **strony** **KonfiguracjaUporządkowanie** >  wiedzy i wybierz pozycję **Wyświetl** w **obszarze Monitoruj najważniejsze konta**.

3. Wybierz **Wprowadzenie** lub **Zarządzaj**.

4. Na stronie **Add Priority accounts (Dodawanie** kont priorytetów) w polu wyszukiwania wpisz nazwę lub adres e-mail osoby, którą chcesz dodać do listy kont priorytetów. Możesz również ustawić próg poczty e-mail dla nieudanych lub opóźnionych wiadomości e-mail i uzyskać tygodniowy raport o problemach dotyczących kont priorytetowych.

5. Wybierz użytkownika i wybierz pozycję **Zapisz**.

Możesz również dodać konta o priorytecie ze strony Aktywni użytkownicy.

### <a name="add-priority-accounts-from-active-users-page"></a>Dodawanie kont priorytetowych na stronie Aktywni użytkownicy

Dodaj konta o priorytecie na stronie Aktywni użytkownicy.

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **strony** **UżytkownicyAktywowanie** >  użytkowników i wybierz trzy kropki (więcej akcji) u góry strony. Wybierz **pozycję Zarządzaj kontami priorytetów**.

3. Wybierz **pozycję Dodaj** konta i na stronie **Dodawanie** kont priorytetowych w polu wyszukiwania wpisz imię i nazwisko osoby, którą chcesz dodać do listy kont priorytetów.

4. Wybierz użytkownika i wybierz pozycję **Zapisz**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Usuwanie użytkownika z listy kont priorytetów

1. Przejdź do centrum administracyjne platformy Microsoft 365 stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **strony** **KonfiguracjaUporządkowanie** >  wiedzy i wybierz pozycję **Wyświetl** w **obszarze Monitoruj najważniejsze konta**.

3. Na stronie **Monitoruj większość kont** wybierz pozycję **Konta o priorytecie** w **obszarze Zarządzaj tą funkcją**.

4. Na stronie **Konta priorytetowe** wybierz z listy użytkowników, których chcesz usunąć, a następnie wybierz pozycję **Usuń konta**.

## <a name="related-topics"></a>Tematy pokrewne

[Korzystanie z kont priorytetowych w programie Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
