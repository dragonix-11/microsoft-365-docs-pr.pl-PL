---
title: Zarządzaj kontami priorytetowymi i je monitoruj
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
description: Monitorowanie nieudanych i opóźnionych wiadomości e-mail wysyłanych do lub z kont, które mają duży wpływ na działalność.
ms.openlocfilehash: edf2c2b1994e1647c4df9b639386cc43dc312c80
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465871"
---
# <a name="manage-and-monitor-priority-accounts-in-microsoft-365"></a>Zarządzanie kontami priorytetów i monitorowanie ich w Microsoft 365

W każdej organizacji Microsoft 365 istnieją osoby, które są niezbędne, takie jak kadra kierownicza, liderzy, menedżerowie lub inni użytkownicy, którzy mają dostęp do poufnych, zastrzeżonych lub o wysokim priorytecie informacji.

Aby ułatwić organizacji ochronę tych kont, możesz teraz wyznaczyć określonych użytkowników jako konta priorytetowe i korzystać z funkcji specyficznych dla aplikacji, które zapewniają im dodatkową ochronę. W przyszłości więcej aplikacji i funkcji będzie obsługiwać konta priorytetowe, a na początek ogłosiliśmy dwie możliwości: **ochronę konta priorytetowego** i **monitorowanie przepływu poczty w warstwie Premium**.

- **Priorytetowa ochrona konta** — Ochrona usługi Office 365 w usłudze Microsoft Defender (dawniej Office 365 Advanced Threat Protection) obsługuje konta o priorytecie jako tagi, które mogą być używane w filtrach w alertach, raportach i badaniach. Aby uzyskać więcej informacji, zapoznaj się z [tematem Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender](../../security/office-365-security/user-tags.md).

  Naturalne pytanie brzmi: "Czy nie wszyscy użytkownicy mają priorytet? Dlaczego nie wyznaczyć wszystkich użytkowników jako kont priorytetowych?" Tak, wszyscy użytkownicy mają priorytet, ale priorytetowa ochrona konta oferuje następujące dodatkowe korzyści:

  - **Dodatkowa heurystyka**: Nasza analiza przepływu poczty w centrach danych firmy Microsoft wskazuje, że wzorce przepływu poczty dla kierownictwa firmy różnią się od przeciętnego pracownika. Priorytetowa ochrona konta oferuje dodatkowe heurystyki, które są specjalnie dostosowane do kierownictwa firmy, które nie byłyby korzystne dla zwykłego pracownika.
  - **Dodatkowy wgląd w raporty**: w efekcie informacje dla wszystkich użytkowników (lub wszystkich użytkowników, których dotyczy problem) są już dostępne w alertach, raportach i badaniach. Tag kont priorytetowych jako filtr umożliwia ukierunkowanie badań.

- **Premium Monitorowanie Flow poczty** — przepływ poczty w dobrej kondycji może mieć kluczowe znaczenie dla sukcesu biznesowego, a opóźnienia lub niepowodzenia dostarczania mogą mieć negatywny wpływ na firmę. Możesz wybrać próg dla nieudanych lub opóźnionych wiadomości e-mail, otrzymywać alerty po przekroczeniu tego progu i wyświetlać raport o problemach z pocztą e-mail dla kont priorytetowych. Aby uzyskać więcej informacji, zapoznaj się z [tematem Problemy z pocztą e-mail dla raportów dotyczących kont priorytetowych w nowoczesnej usłudze EAC](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Aby zapoznać się z najlepszymi rozwiązaniami w zakresie zabezpieczeń dla kont priorytetowych, zobacz [Zalecenia dotyczące zabezpieczeń dla kont priorytetowych](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Funkcja **ochrony konta priorytetowego** opisana w tym temacie jest dostępna tylko dla organizacji spełniających następujące wymagania:

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2, w tym Office 365 E3, Office 365 E5, Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5.

Funkcja **monitorowania Premium Mail Flow opisana** w tym temacie jest dostępna tylko dla organizacji spełniających następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji wynoszącą co najmniej 5000 z jednego z następujących produktów lub kombinację następujących produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Na przykład organizacja może mieć 3000 licencji Office 365 E3 i 2500 Microsoft 365 E5, co daje łącznie 5500 licencji z kwalifikujących się produktów.
- Organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla co najmniej jednego podstawowego obciążenia — Teams, one drive dla firm, SharePoint Online, Exchange Online i Office aplikacji.

> [!NOTE]
> Możesz monitorować maksymalnie 250 kont priorytetów.

Gdy stosujesz ochronę konta priorytetowego do skrzynki pocztowej, należy również zastosować ochronę konta priorytetowego do użytkowników, którzy mają dostęp do skrzynki pocztowej (na przykład dyrektor generalny i asystent wykonawczy dyrektora generalnego, który zarządza kalendarzem dyrektora generalnego).

### <a name="add-priority-accounts-from-the-setup-page"></a>Dodawanie kont priorytetów ze strony Konfiguracja

Dodaj konta o **priorytecie ze strony Konfiguracja**.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **obszaru** **SetupOrganizational knowledge (Konfiguracja** > ) I wybierz pozycję **Wyświetl** w obszarze **Monitorowanie najważniejszych kont**.

3. Wybierz **pozycję Wprowadzenie** lub **Zarządzaj**.

4. Na stronie **Dodawanie kont priorytetowych** w polu wyszukiwania wpisz nazwę lub adres e-mail osoby, którą chcesz dodać do listy kont priorytetowych. Możesz również ustawić próg poczty e-mail dla wiadomości e-mail zakończonych niepowodzeniem lub opóźnionych wiadomości e-mail i uzyskać cotygodniowy raport o problemach dotyczących kont priorytetowych.

5. Wybierz użytkownika i wybierz pozycję **Zapisz**.

Możesz również dodać konta o priorytecie ze strony Aktywni użytkownicy.

### <a name="add-priority-accounts-from-active-users-page"></a>Dodawanie kont o priorytecie ze strony Aktywni użytkownicy

Dodaj konta o priorytecie ze strony Aktywni użytkownicy.

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do pozycji **UżytkownicyAktywni**  >  użytkownicy i wybierz trzy kropki (więcej akcji) w górnej części strony. Wybierz pozycję **Zarządzaj kontami priorytetów**.

3. Wybierz pozycję **Dodaj konta**, a następnie na stronie **Dodawanie kont priorytetowych** w polu wyszukiwania wpisz nazwę osoby, którą chcesz dodać do listy kont priorytetów.

4. Wybierz użytkownika i wybierz pozycję **Zapisz**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Usuwanie użytkownika z listy kont priorytetów

1. Przejdź do Centrum administracyjne platformy Microsoft 365 pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **obszaru** **SetupOrganizational knowledge (Konfiguracja** > ) I wybierz pozycję **Wyświetl** w obszarze **Monitorowanie najważniejszych kont**.

3. Na stronie **Monitorowanie większości kont** wybierz pozycję **Konta priorytetowe** w obszarze **Zarządzanie tą funkcją**.

4. Na stronie **Konta priorytetowe** wybierz użytkownika lub użytkowników, których chcesz usunąć z listy, a następnie wybierz pozycję **Usuń konta**.

## <a name="related-topics"></a>Tematy pokrewne

[Używanie kont priorytetowych w Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
